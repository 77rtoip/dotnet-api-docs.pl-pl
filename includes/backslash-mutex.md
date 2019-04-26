---
ms.openlocfilehash: c28e3f97e02079905d591a7f27dc8d68d603c0bf
ms.sourcegitcommit: f1d16425528e237257ca3b58eb49217a514849ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/24/2019
ms.locfileid: "63871558"
---
Ukośnik odwrotny (\\) to zastrzeżony znak w nazwie obiektu mutex. Nie należy używać ukośnika odwrotnego (\\) w nazwie obiektu mutex z wyjątkiem określonych z uwagi na temat używania muteksy w sesji serwera terminali. W przeciwnym razie <xref:System.IO.DirectoryNotFoundException> mogą zostać zgłoszone, nawet jeśli nazwę obiektu mutex reprezentuje istniejącego pliku.
