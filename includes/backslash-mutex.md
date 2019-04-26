---
ms.openlocfilehash: c28e3f97e02079905d591a7f27dc8d68d603c0bf
ms.sourcegitcommit: f1d16425528e237257ca3b58eb49217a514849ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/24/2019
ms.locfileid: "63871558"
---
<span data-ttu-id="57d19-101">Ukośnik odwrotny (\\) to zastrzeżony znak w nazwie obiektu mutex.</span><span class="sxs-lookup"><span data-stu-id="57d19-101">The backslash (\\) is a reserved character in a mutex name.</span></span> <span data-ttu-id="57d19-102">Nie należy używać ukośnika odwrotnego (\\) w nazwie obiektu mutex z wyjątkiem określonych z uwagi na temat używania muteksy w sesji serwera terminali.</span><span class="sxs-lookup"><span data-stu-id="57d19-102">Don't use a backslash (\\) in a mutex name except as specified in the note on using mutexes in terminal server sessions.</span></span> <span data-ttu-id="57d19-103">W przeciwnym razie <xref:System.IO.DirectoryNotFoundException> mogą zostać zgłoszone, nawet jeśli nazwę obiektu mutex reprezentuje istniejącego pliku.</span><span class="sxs-lookup"><span data-stu-id="57d19-103">Otherwise, a <xref:System.IO.DirectoryNotFoundException> may be thrown, even though the name of the mutex represents an existing file.</span></span>
