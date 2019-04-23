---
ms.openlocfilehash: 1654d58651bf14b0e7c21de2afa827634b7db858
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59235900"
---
### <a name="systemuri-escaping-now-supports-rfc-3986"></a>System.Uri kaçış artık RFC 3986 destekler

|   |   |
|---|---|
|Ayrıntılar|URI kaçış desteklemek için .NET Framework 4.5 içinde değiştirilmemiş [RFC 3986](https://tools.ietf.org/html/rfc3986). Özel değişiklikler şunlardır:<ul><li><xref:System.Uri.EscapeDataString(System.String)?displayProperty=name> kaçış karakterleri RFC 3986'ya dayalı ayrılmış karakterleri kaçırır.</li><li><xref:System.Uri.EscapeUriString(System.String)?displayProperty=name> ayrılmış karakterleri kaçırmaz.</li><li><xref:System.Uri.UnescapeDataString(System.String)?displayProperty=name> Geçersiz bir kaçış dizisi ile karşılaşırsa, bir özel durum oluşturmaz.</li><li>Ayrılmamış kaçış karakterleri, kaçılmamış durumdadır.</li></ul>|
|Öneri|<ul><li>Dayanan olmayan uygulamaları güncelleştirme <xref:System.Uri.UnescapeDataString(System.String)?displayProperty=name> söz konusu olduğunda geçersiz kaçış dizisi oluşturmak için. Tür dizilerini doğrudan artık algılanabilmesi gerekir.</li><li>Benzer şekilde, Escaped ve Atlanmayan URI ve veri dizeleri .NET Framework 4.0 ve .NET Framework 4.5 değişebilir ve .NET sürümleri arasında doğrudan karşılaştırılmalıdır değil bekler. Bunun yerine, ayrıştırılır ve tüm karşılaştırmalar yapılmadan önce tek bir .NET sürümde normalleştirilmiş.</li></ul>|
|Kapsam|İkincil|
|Sürüm|4,5|
|Tür|Çalışma zamanı|
|Etkilenen API’ler|<ul><li><xref:System.Uri.EscapeDataString(System.String)?displayProperty=nameWithType></li><li><xref:System.Uri.EscapeUriString(System.String)?displayProperty=nameWithType></li><li><xref:System.Uri.UnescapeDataString(System.String)?displayProperty=nameWithType></li></ul>|
