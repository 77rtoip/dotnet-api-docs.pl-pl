---
ms.openlocfilehash: 733bfb4740f3f274ba9ebb396749d313907d5fa6
ms.sourcegitcommit: f1d16425528e237257ca3b58eb49217a514849ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/24/2019
ms.locfileid: "63870372"
---
<span data-ttu-id="86df7-101">Począwszy od programu .NET Framework 4.7, ta metoda jest uwierzytelniany przy użyciu <xref:System.Security.Authentication.SslProtocols.None>, co pozwala systemu operacyjnego wybrać protokół używany i blokowanie protokoły, które nie są bezpieczne.</span><span class="sxs-lookup"><span data-stu-id="86df7-101">Starting with .NET Framework 4.7, this method authenticates using <xref:System.Security.Authentication.SslProtocols.None>, which allows the operating system to choose the best protocol to use, and to block protocols that are not secure.</span></span> <span data-ttu-id="86df7-102">W .NET Framework 4.6 (i .NET Framework 4.5 z zainstalowanymi najnowszymi poprawkami zabezpieczeń) dozwolonych wersji protokołów TLS/SSL są 1.2, 1.1 i 1.0 (o ile nie wyłączysz silnej kryptografii, edytując Rejestr Windows).</span><span class="sxs-lookup"><span data-stu-id="86df7-102">In .NET Framework 4.6 (and .NET Framework 4.5 with the latest security patches installed), the allowed TLS/SSL protocols versions are 1.2, 1.1, and 1.0 (unless you disable strong cryptography by editing the Windows Registry).</span></span>
