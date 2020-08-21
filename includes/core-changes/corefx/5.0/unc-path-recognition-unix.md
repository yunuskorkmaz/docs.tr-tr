---
ms.openlocfilehash: 0246f325a6274082b7fb0d5590cec7c80687ae85
ms.sourcegitcommit: ef86c24c418439b8bb5e3e7d64bbdbe5e11c3e9c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2020
ms.locfileid: "88720218"
---
### <a name="uri-recognition-of-unc-paths-on-unix"></a>UNIX üzerinde UNC yollarının URI tanıması

<xref:System.Uri>Sınıfı artık, `//` UNIX işletim sistemlerinde evrensel adlandırma KURALı (UNC) yolları olarak iki eğik çizgi () ile başlayan dizeleri tanır. Bu değişiklik, bu tür dizelerin davranışını tüm platformlarda tutarlı hale getirir.

#### <a name="change-description"></a>Açıklamayı Değiştir

.NET 'in önceki sürümlerinde, <xref:System.Uri> sınıfı iki eğik çizgi ile başlayan dizeleri tanır, örneğin, `//contoso` UNIX işletim sistemlerinde mutlak dosya yolları olarak. Ancak, Windows 'ta bu tür dizeler UNC yolları olarak tanınır.

.NET 5,0 ' den başlayarak, <xref:System.Uri> sınıfı, UNIX dahil olmak üzere tüm platformlarda UNC yolları olarak iki eğik çizgi ile başlayan dizeleri tanır. Ayrıca, Özellikler UNC semantiklerine göre davranır:

- <xref:System.Uri.IsUnc?displayProperty=nameWithType> döndürür `true` .
- Yoldaki ters eğik çizgiler eğik çizgiyle değiştirilmiştir. Örneğin, `//first\second` olur `//first/second` .
- <xref:System.Uri.LocalPath?displayProperty=nameWithType> karakter yüzdesi değil. Örneğin, `//first/\uFFF0` öğesine dönüştürülmez *not* `//first/%EF%BF%B0` .

#### <a name="version-introduced"></a>Sunulan sürüm

5.0

#### <a name="recommended-action"></a>Önerilen eylem

Geliştiricinin bölümünde herhangi bir eylem gerekmez.

#### <a name="category"></a>Kategori

Core .NET kitaplıkları

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Uri?displayProperty=fullName>

<!--

#### Affected APIs

- `T:System.Uri`

-->
