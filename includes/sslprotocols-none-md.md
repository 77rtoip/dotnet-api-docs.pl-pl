---
ms.openlocfilehash: 733bfb4740f3f274ba9ebb396749d313907d5fa6
ms.sourcegitcommit: f1d16425528e237257ca3b58eb49217a514849ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/24/2019
ms.locfileid: "63870372"
---
Począwszy od programu .NET Framework 4.7, ta metoda jest uwierzytelniany przy użyciu <xref:System.Security.Authentication.SslProtocols.None>, co pozwala systemu operacyjnego wybrać protokół używany i blokowanie protokoły, które nie są bezpieczne. W .NET Framework 4.6 (i .NET Framework 4.5 z zainstalowanymi najnowszymi poprawkami zabezpieczeń) dozwolonych wersji protokołów TLS/SSL są 1.2, 1.1 i 1.0 (o ile nie wyłączysz silnej kryptografii, edytując Rejestr Windows).
