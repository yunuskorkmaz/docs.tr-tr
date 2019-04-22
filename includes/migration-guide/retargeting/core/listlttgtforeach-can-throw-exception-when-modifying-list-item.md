---
ms.openlocfilehash: 4e81087431091dfa4d5432d5ea5e2b665be2b130
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59774407"
---
### <a name="listtforeach-can-throw-exception-when-modifying-list-item"></a>Liste\<T >. ForEach liste öğesi değiştirirken özel durumu oluşturabilecek

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.5 sürümünden başlayarak, çağrı koleksiyonundaki bir öğe değiştirilirse bir <xref:System.Collections.Generic.List%601.ForEach(System.Action{%600})> numaralandırıcısı bir <xref:System.InvalidOperationException?displayProperty=name> özel durumu oluşturur. Daha önceden, bu bir özel durum oluşturmuyordu ancak yarış durumlarına neden olabiliyordu.|
|Öneri|İdeal olarak, bu hiçbir zaman güvenli bir işlem olmadığından kod, liste öğelerini listelerken, listeleri değiştirmeyecek şekilde düzeltilmelidir. Bununla birlikte, bir uygulama önceki davranışa dönmek için .NET Framework 4.0’ı hedefleyebilir.|
|Kapsam|Kenar|
|Sürüm|4,5|
|Tür|Yeniden Hedefleme|
|Etkilenen API’ler|<ul><li><xref:System.Collections.Generic.List%601.ForEach(System.Action{%600})?displayProperty=nameWithType></li></ul>|
