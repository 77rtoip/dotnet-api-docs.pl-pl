---
ms.openlocfilehash: 903ac4ecb57e3a8e02a4f65ecfa6f9e77a552f45
ms.sourcegitcommit: f1d16425528e237257ca3b58eb49217a514849ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/24/2019
ms.locfileid: "63872203"
---
Za pomocą opartego na znakach indeksowanie z <xref:System.Text.StringBuilder.Chars%2A> właściwość może być bardzo wolne działanie w następujących warunkach:

- <xref:System.Text.StringBuilder> Wystąpienia jest duży (na przykład składa się z dziesiątków tysięcy znaków).
- <xref:System.Text.StringBuilder> Jest "podzielonym." Oznacza to, takich jak wielokrotne wywołania metody <xref:System.Text.StringBuilder.Append%2A?displayProperty=nameWithType> automatycznie zostały rozszerzone obiektu <xref:System.Text.StringBuilder.Capacity%2A?displayProperty=nameWithType> właściwość i przydzielone nowych fragmentów w pamięci do niego.

Jest znaczny wpływ na wydajność, ponieważ dostęp do każdego znaku opisano połączone całą listę fragmentach, aby znaleźć poprawne buforu na indeksowanie.

> [!NOTE]
>  Nawet w przypadku dużych "podzielonym" <xref:System.Text.StringBuilder> obiektu przy użyciu <xref:System.Text.StringBuilder.Chars%2A> właściwość opartego na indeksie dostęp do jednej lub niewielkiej liczby znaków ma wpływ na wydajność niewielkie; zazwyczaj jest **0(n)** operacji. Wpływ na wydajność znaczące występuje podczas iteracji znaków w <xref:System.Text.StringBuilder> obiektu, który jest **O(n^2)** operacji. 

Jeśli napotkasz problemy z wydajnością, korzystając z opartego na znakach indeksowanie za pomocą <xref:System.Text.StringBuilder> obiektów, możesz użyć dowolnej z poniższych rozwiązań:

- Konwertuj <xref:System.Text.StringBuilder> wystąpienia do <xref:System.String> przez wywołanie metody <xref:System.Text.StringBuilder.ToString%2A> metody, uzyskiwać dostęp do znaków w ciągu.

- Skopiuj zawartość istniejącego <xref:System.Text.StringBuilder> nowy obiekt wstępnie wielkości <xref:System.Text.StringBuilder> obiektu. Zwiększa wydajność, ponieważ nowy <xref:System.Text.StringBuilder> obiekt nie jest podzielonym. Na przykład:

   ```csharp
   // sbOriginal is the existing StringBuilder object
   var sbNew = new StringBuilder(sbOriginal.ToString(), sbOriginal.Length);
   ```
   ```vb
   ' sbOriginal is the existing StringBuilder object
   Dim sbNew = New StringBuilder(sbOriginal.ToString(), sbOriginal.Length)
   ```
- Ustaw początkową pojemność <xref:System.Text.StringBuilder> obiektu wartość, która jest w przybliżeniu równa maksymalny rozmiar oczekiwany przez wywołanie metody <xref:System.Text.StringBuilder.%23ctor(System.Int32)> konstruktora. Należy pamiętać, że to przydziela cały blok pamięci nawet wtedy, gdy <xref:System.Text.StringBuilder> rzadko osiąga limit maksymalnej pojemności.
