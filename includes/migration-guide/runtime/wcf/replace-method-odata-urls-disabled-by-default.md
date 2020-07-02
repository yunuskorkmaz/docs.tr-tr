---
ms.openlocfilehash: b2fcacdb02c411c4dcb12051bf0c6759faccdea2
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620664"
---
### <a name="the-replace-method-in-odata-urls-is-disabled-by-default"></a>OData URL 'Lerinde Replace yöntemi varsayılan olarak devre dışıdır

#### <a name="details"></a>Ayrıntılar

.NET Framework 4,5 ' den başlayarak OData URL 'Lerinde Replace yöntemi varsayılan olarak devre dışıdır. OData Replace devre dışı bırakıldığında (şimdi varsayılan olarak), Replace işlevleri de dahil olmak üzere tüm Kullanıcı istekleri başarısız olur.

#### <a name="suggestion"></a>Öneri

Replace yöntemi gerekliyse (Bu çok nadir bir durumdur), bir yapılandırma ayarları () aracılığıyla yeniden etkinleştirilebilir <xref:System.Data.Services.Configuration.DataServicesFeaturesSection.ReplaceFunction?displayProperty=fullName> . Ancak etkin bir Replace yöntemi güvenlik açıklarını açabilir ve yalnızca dikkatli bir inceleme sonrasında kullanılmalıdır.

| Name    | Değer       |
|:--------|:------------|
| Kapsam   |Edge|
|Sürüm|4,5|
|Tür|Çalışma Zamanı

#### <a name="affected-apis"></a>Etkilenen API’ler

-<xref:System.Data.Services.DataService%601?displayProperty=nameWithType></li></ul>|
