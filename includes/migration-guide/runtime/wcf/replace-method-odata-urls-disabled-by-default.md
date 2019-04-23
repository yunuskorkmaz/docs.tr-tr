---
ms.openlocfilehash: 6dc3669433804a4524c18d5a932f9879343ab508
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59805246"
---
### <a name="the-replace-method-in-odata-urls-is-disabled-by-default"></a>OData URL'lerinde Değiştir yöntemi varsayılan olarak devre dışıdır

|   |   |
|---|---|
|Ayrıntılar|OData URL'lerinde Değiştir yöntemi, .NET Framework 4. 5 ' başlayarak, varsayılan olarak devre dışıdır. OData Değiştir (şimdi varsayılan olarak) devre dışı bırakıldığında (Bu nadir) Değiştir işlevleri dahil olmak üzere herhangi bir kullanıcı isteğinin başarısız olur.|
|Öneri|Replace yöntemi gerekiyorsa (olduğu genel olmayan), yapılandırma ayarları aracılığıyla yeniden etkin olabilir (<xref:System.Data.Services.Configuration.DataServicesFeaturesSection.ReplaceFunction?displayProperty=name>). Ancak, bir etkin Değiştir yöntemi güvenlik açıklarını açabilirsiniz ve yalnızca inceledikten sonra kullanılmalıdır.|
|Kapsam|Kenar|
|Sürüm|4,5|
|Tür|Çalışma zamanı|
|Etkilenen API’ler|<ul><li><xref:System.Data.Services.DataService%601?displayProperty=nameWithType></li></ul>|
