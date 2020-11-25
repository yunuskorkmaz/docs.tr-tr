---
title: 'Son değişiklik: UNIX üzerinde UNC yollarının URI tanıması'
description: URI sınıfının artık UNIX üzerinde UNC yolları olarak iki eğik çizgi ile başlayan dizeleri tanıdığı çekirdek .NET kitaplıklarında .NET 5,0 son değişikliği hakkında bilgi edinin.
ms.date: 11/01/2020
ms.openlocfilehash: 0d5d9cd8dd869f24e94d15724e5e16eaddf6ed47
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95761386"
---
# <a name="uri-recognition-of-unc-paths-on-unix"></a>UNIX üzerinde UNC yollarının URI tanıması

<xref:System.Uri>Sınıfı artık, `//` UNIX işletim sistemlerinde evrensel adlandırma KURALı (UNC) yolları olarak iki eğik çizgi () ile başlayan dizeleri tanır. Bu değişiklik, bu tür dizelerin davranışını tüm platformlarda tutarlı hale getirir.

## <a name="change-description"></a>Açıklamayı Değiştir

.NET 'in önceki sürümlerinde, <xref:System.Uri> sınıfı iki eğik çizgi ile başlayan dizeleri (örneğin, `//contoso` UNIX işletim sistemlerinde mutlak dosya yolları) tanır. Ancak, Windows 'ta bu tür dizeler UNC yolları olarak tanınır.

.NET 5,0 ' den başlayarak, <xref:System.Uri> sınıfı, UNIX dahil olmak üzere tüm platformlarda UNC yolları olarak iki eğik çizgi ile başlayan dizeleri tanır. Ayrıca, Özellikler UNC semantiklerine göre davranır:

- <xref:System.Uri.IsUnc?displayProperty=nameWithType> döndürür `true` .
- Yoldaki ters eğik çizgiler eğik çizgiyle değiştirilmiştir. Örneğin, `//first\second` olur `//first/second` .
- <xref:System.Uri.LocalPath?displayProperty=nameWithType> karakter yüzdesi değil. Örneğin, `//first/\uFFF0` öğesine dönüştürülmez *not* `//first/%EF%BF%B0` .

## <a name="version-introduced"></a>Sunulan sürüm

5.0

## <a name="recommended-action"></a>Önerilen eylem

Geliştiricinin bölümünde herhangi bir eylem gerekmez.

## <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Uri?displayProperty=fullName>

<!--

#### Category

Core .NET libraries

### Affected APIs

- `T:System.Uri`

-->
