---
ms.openlocfilehash: 903ac4ecb57e3a8e02a4f65ecfa6f9e77a552f45
ms.sourcegitcommit: f1d16425528e237257ca3b58eb49217a514849ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/24/2019
ms.locfileid: "63872203"
---
<span data-ttu-id="e5b28-101">Za pomocą opartego na znakach indeksowanie z <xref:System.Text.StringBuilder.Chars%2A> właściwość może być bardzo wolne działanie w następujących warunkach:</span><span class="sxs-lookup"><span data-stu-id="e5b28-101">Using character-based indexing with the <xref:System.Text.StringBuilder.Chars%2A> property can be extremely slow under the following conditions:</span></span>

- <span data-ttu-id="e5b28-102"><xref:System.Text.StringBuilder> Wystąpienia jest duży (na przykład składa się z dziesiątków tysięcy znaków).</span><span class="sxs-lookup"><span data-stu-id="e5b28-102">The <xref:System.Text.StringBuilder> instance is large (for example, it consists of several tens of thousands of characters).</span></span>
- <span data-ttu-id="e5b28-103"><xref:System.Text.StringBuilder> Jest "podzielonym."</span><span class="sxs-lookup"><span data-stu-id="e5b28-103">The <xref:System.Text.StringBuilder> is "chunky."</span></span> <span data-ttu-id="e5b28-104">Oznacza to, takich jak wielokrotne wywołania metody <xref:System.Text.StringBuilder.Append%2A?displayProperty=nameWithType> automatycznie zostały rozszerzone obiektu <xref:System.Text.StringBuilder.Capacity%2A?displayProperty=nameWithType> właściwość i przydzielone nowych fragmentów w pamięci do niego.</span><span class="sxs-lookup"><span data-stu-id="e5b28-104">That is, repeated calls to methods such as <xref:System.Text.StringBuilder.Append%2A?displayProperty=nameWithType> have automatically expanded the object's <xref:System.Text.StringBuilder.Capacity%2A?displayProperty=nameWithType> property and allocated new chunks of memory to it.</span></span>

<span data-ttu-id="e5b28-105">Jest znaczny wpływ na wydajność, ponieważ dostęp do każdego znaku opisano połączone całą listę fragmentach, aby znaleźć poprawne buforu na indeksowanie.</span><span class="sxs-lookup"><span data-stu-id="e5b28-105">Performance is severely impacted because each character access walks the entire linked list of chunks to find the correct buffer to index into.</span></span>

> [!NOTE]
>  <span data-ttu-id="e5b28-106">Nawet w przypadku dużych "podzielonym" <xref:System.Text.StringBuilder> obiektu przy użyciu <xref:System.Text.StringBuilder.Chars%2A> właściwość opartego na indeksie dostęp do jednej lub niewielkiej liczby znaków ma wpływ na wydajność niewielkie; zazwyczaj jest **0(n)** operacji.</span><span class="sxs-lookup"><span data-stu-id="e5b28-106">Even for a large "chunky" <xref:System.Text.StringBuilder> object, using the <xref:System.Text.StringBuilder.Chars%2A> property for index-based access to one or a small number of characters has a negligible performance impact; typically, it is an **0(n)** operation.</span></span> <span data-ttu-id="e5b28-107">Wpływ na wydajność znaczące występuje podczas iteracji znaków w <xref:System.Text.StringBuilder> obiektu, który jest **O(n^2)** operacji.</span><span class="sxs-lookup"><span data-stu-id="e5b28-107">The significant performance impact occurs when iterating the characters in the <xref:System.Text.StringBuilder> object, which is an **O(n^2)** operation.</span></span> 

<span data-ttu-id="e5b28-108">Jeśli napotkasz problemy z wydajnością, korzystając z opartego na znakach indeksowanie za pomocą <xref:System.Text.StringBuilder> obiektów, możesz użyć dowolnej z poniższych rozwiązań:</span><span class="sxs-lookup"><span data-stu-id="e5b28-108">If you encounter performance issues when using character-based indexing with <xref:System.Text.StringBuilder> objects, you can use any of the following workarounds:</span></span>

- <span data-ttu-id="e5b28-109">Konwertuj <xref:System.Text.StringBuilder> wystąpienia do <xref:System.String> przez wywołanie metody <xref:System.Text.StringBuilder.ToString%2A> metody, uzyskiwać dostęp do znaków w ciągu.</span><span class="sxs-lookup"><span data-stu-id="e5b28-109">Convert the <xref:System.Text.StringBuilder> instance to a <xref:System.String> by calling the <xref:System.Text.StringBuilder.ToString%2A> method, then access the characters in the string.</span></span>

- <span data-ttu-id="e5b28-110">Skopiuj zawartość istniejącego <xref:System.Text.StringBuilder> nowy obiekt wstępnie wielkości <xref:System.Text.StringBuilder> obiektu.</span><span class="sxs-lookup"><span data-stu-id="e5b28-110">Copy the contents of the existing <xref:System.Text.StringBuilder> object to a new pre-sized <xref:System.Text.StringBuilder> object.</span></span> <span data-ttu-id="e5b28-111">Zwiększa wydajność, ponieważ nowy <xref:System.Text.StringBuilder> obiekt nie jest podzielonym.</span><span class="sxs-lookup"><span data-stu-id="e5b28-111">Performance improves because the new <xref:System.Text.StringBuilder> object is not chunky.</span></span> <span data-ttu-id="e5b28-112">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="e5b28-112">For example:</span></span>

   ```csharp
   // sbOriginal is the existing StringBuilder object
   var sbNew = new StringBuilder(sbOriginal.ToString(), sbOriginal.Length);
   ```
   ```vb
   ' sbOriginal is the existing StringBuilder object
   Dim sbNew = New StringBuilder(sbOriginal.ToString(), sbOriginal.Length)
   ```
- <span data-ttu-id="e5b28-113">Ustaw początkową pojemność <xref:System.Text.StringBuilder> obiektu wartość, która jest w przybliżeniu równa maksymalny rozmiar oczekiwany przez wywołanie metody <xref:System.Text.StringBuilder.%23ctor(System.Int32)> konstruktora.</span><span class="sxs-lookup"><span data-stu-id="e5b28-113">Set the initial capacity of the <xref:System.Text.StringBuilder> object to a value that is approximately equal to its maximum expected size by calling the <xref:System.Text.StringBuilder.%23ctor(System.Int32)> constructor.</span></span> <span data-ttu-id="e5b28-114">Należy pamiętać, że to przydziela cały blok pamięci nawet wtedy, gdy <xref:System.Text.StringBuilder> rzadko osiąga limit maksymalnej pojemności.</span><span class="sxs-lookup"><span data-stu-id="e5b28-114">Note that this allocates the entire block of memory even if the <xref:System.Text.StringBuilder> rarely reaches its maximum capacity.</span></span>
