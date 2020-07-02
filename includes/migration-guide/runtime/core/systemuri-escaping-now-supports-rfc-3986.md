---
ms.openlocfilehash: 1d7dc808d5b514acc582675d6ccdbd5778314624
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620591"
---
### <a name="systemuri-escaping-now-supports-rfc-3986"></a>System. Uri kaçış artık RFC 3986 ' i desteklemektedir

#### <a name="details"></a>Ayrıntılar

.NET Framework 4,5 ' de, [RFC 3986](https://tools.ietf.org/html/rfc3986)' i desteklemek için URI kaçış değeri değişti. Belirli değişiklikler şunları içerir:<ul><li><xref:System.Uri.EscapeDataString(System.String)?displayProperty=fullName>RFC 3986 ' i temel alarak ayrılmış karakterleri çıkar.</li><li><xref:System.Uri.EscapeUriString(System.String)?displayProperty=fullName>ayrılmış karakterlerden kaçış yapmaz.</li><li><xref:System.Uri.UnescapeDataString(System.String)?displayProperty=fullName>geçersiz bir kaçış dizisiyle karşılaşırsa özel durum oluşturmaz.</li><li>Ayrılmamış kaçış karakterleri, kaçılmamış durumdadır.</li></ul>

#### <a name="suggestion"></a>Öneri

<ul><li>Uygulamaları <xref:System.Uri.UnescapeDataString(System.String)?displayProperty=fullName> , geçersiz bir kaçış sırası durumunda throw 'e dayanmayan olarak güncelleştirin. Bu tür diziler doğrudan hemen algılanmalıdır.</li><li>Benzer şekilde, kaçış ve kaçışsız URI ve veri dizelerinin .NET Framework 4,0 ve .NET Framework 4,5 ' den değişebildiğinden ve .NET sürümleri arasında doğrudan karşılaştırılmamalıdır. Bunun yerine, karşılaştırmalar yapılmadan önce bunların tek bir .NET sürümünde ayrıştırılıp normalleştirilmeleri gerekir.</li></ul>

| Name    | Değer       |
|:--------|:------------|
| Kapsam   |İkincil|
|Sürüm|4,5|
|Tür|Çalışma Zamanı

#### <a name="affected-apis"></a>Etkilenen API’ler

-<xref:System.Uri.EscapeDataString(System.String)?displayProperty=nameWithType></li><li><xref:System.Uri.EscapeUriString(System.String)?displayProperty=nameWithType></li><li><xref:System.Uri.UnescapeDataString(System.String)?displayProperty=nameWithType></li></ul>|
