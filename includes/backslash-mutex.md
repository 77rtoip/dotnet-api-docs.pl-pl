---
ms.openlocfilehash: c28e3f97e02079905d591a7f27dc8d68d603c0bf
ms.sourcegitcommit: 1bb00d2f4343e73ae8d58668f02297a3cf10a4c1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/15/2019
ms.locfileid: "63871558"
---
Ukośnik odwrotny (\\) to zastrzeżony znak w nazwie obiektu mutex. Nie należy używać ukośnika odwrotnego (\\) w nazwie obiektu mutex z wyjątkiem określonych z uwagi na temat używania muteksy w sesji serwera terminali. W przeciwnym razie <xref:System.IO.DirectoryNotFoundException> mogą zostać zgłoszone, nawet jeśli nazwę obiektu mutex reprezentuje istniejącego pliku.
