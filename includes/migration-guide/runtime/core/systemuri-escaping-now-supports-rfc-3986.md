---
ms.openlocfilehash: e7001fcfdf88fd9e710fbb702f2ed39d63b1e080
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496132"
---
### <a name="systemuri-escaping-now-supports-rfc-3986"></a>System. Uri kaçış artık RFC 3986 ' i desteklemektedir

#### <a name="details"></a>Ayrıntılar

.NET Framework 4,5 ' de, [RFC 3986](https://tools.ietf.org/html/rfc3986)' i desteklemek için URI kaçış değeri değişti. Belirli değişiklikler şunları içerir:<ul><li><xref:System.Uri.EscapeDataString(System.String)?displayProperty=fullName> RFC 3986 ' i temel alarak ayrılmış karakterleri çıkar.</li><li><xref:System.Uri.EscapeUriString(System.String)?displayProperty=fullName> ayrılmış karakterlerden kaçış yapmaz.</li><li><xref:System.Uri.UnescapeDataString(System.String)?displayProperty=fullName> geçersiz bir kaçış dizisiyle karşılaşırsa özel durum oluşturmaz.</li><li>Ayrılmamış kaçış karakterleri, kaçılmamış durumdadır.</li></ul>

#### <a name="suggestion"></a>Öneri

<ul><li>Uygulamaları <xref:System.Uri.UnescapeDataString(System.String)?displayProperty=fullName> , geçersiz bir kaçış sırası durumunda throw 'e dayanmayan olarak güncelleştirin. Bu tür diziler doğrudan hemen algılanmalıdır.</li><li>Benzer şekilde, kaçış ve kaçışsız URI ve veri dizelerinin .NET Framework 4,0 ve .NET Framework 4,5 ' den değişebildiğinden ve .NET sürümleri arasında doğrudan karşılaştırılmamalıdır. Bunun yerine, karşılaştırmalar yapılmadan önce bunların tek bir .NET sürümünde ayrıştırılıp normalleştirilmeleri gerekir.</li></ul>

| Name    | Değer       |
|:--------|:------------|
| Kapsam   |İkincil|
|Sürüm|4,5|
|Tür|Çalışma Zamanı|

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Uri.EscapeDataString(System.String)?displayProperty=nameWithType>
- <xref:System.Uri.EscapeUriString(System.String)?displayProperty=nameWithType>
- <xref:System.Uri.UnescapeDataString(System.String)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Uri.EscapeDataString(System.String)`
- `M:System.Uri.EscapeUriString(System.String)`
- `M:System.Uri.UnescapeDataString(System.String)`

-->
