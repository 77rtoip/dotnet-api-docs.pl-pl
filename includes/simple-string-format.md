---
ms.openlocfilehash: 483f2c83f4d55aad694ba713c787972178b19e5e
ms.sourcegitcommit: f1d16425528e237257ca3b58eb49217a514849ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/24/2019
ms.locfileid: "63872450"
---

Jednak podczas wywoływania **String.Format** metody, nie jest konieczne skoncentrować się na określonego przeciążenia, które ma zostać wywołana. Zamiast tego należy wywołać metodę z [ciąg formatu złożonego](~/docs/standard/base-types/composite-formatting.md) zawierającego jeden lub więcej elementów formatu. Przypisz każdy element formatu indeksu liczbowego; Pierwszy indeks zaczyna się od 0. Oprócz ciąg początkowy wywołania metody powinna mieć dowolną liczbę dodatkowych argumentów, ponieważ zawiera ona wartości indeksu. Na przykład ciąg, którego elementy formatu miały indeksy od 0 do 1 powinny mieć argumentów 2; jeden z indeksami 0 do 5 powinna mieć 6 argumentów. Twój kompilator języka zostanie następnie rozpoznać wywołania metody do określonego przeciążenia **String.Format** metody.   
 
Aby uzyskać bardziej szczegółowe dokumentacją dotyczącą korzystania z **String.Format** metody, zobacz [rozpoczęcie korzystania z metody String.Format](#Starting) i [która metoda zostanie wywołana?](#FTaskList).    
