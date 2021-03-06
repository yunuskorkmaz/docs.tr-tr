---
title: 'Son değişiklik: ASCII olmayan karakterler içeren URI yolları UNIX üzerinde doğru şekilde ayrıştırır'
description: ASCII olmayan karakterler içeren mutlak URI yollarının artık UNIX platformlarında doğru şekilde ayrıştırdığına ilişkin temel .NET kitaplıklarında .NET 5 ' in son değişikliği hakkında bilgi edinin.
ms.date: 11/01/2020
ms.openlocfilehash: 50e9b4597a5ac0b73732a38ce662037292777a03
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2021
ms.locfileid: "102257420"
---
# <a name="uri-paths-with-non-ascii-characters-parse-correctly-on-unix"></a>ASCII olmayan karakterler içeren URI yolları UNIX üzerinde doğru şekilde ayrıştırır

<xref:System.Uri?displayProperty=fullName>Sınıfında, ASCII olmayan karakterler içeren mutlak URI yollarının UNIX platformlarında doğru şekilde ayrıştırdığına ilişkin bir hata düzeltildi.

## <a name="change-description"></a>Açıklamayı Değiştir

.NET 'in önceki sürümlerinde, ASCII olmayan karakterler içeren mutlak URI yolları UNIX platformlarında yanlış ayrıştırılır ve yolun kesimleri yinelenir. (Mutlak yollar "/" ile başlayan olanlardır.) Ayrıştırma sorunu .NET 5,0 için düzeltildi. .NET ' in önceki bir sürümünü .NET 5 veya sonraki bir sürümüne taşırsanız,, <xref:System.Uri.AbsoluteUri?displayProperty=nameWithType> <xref:System.Uri.ToString?displayProperty=nameWithType> ve diğer Üyeler tarafından oluşturulan farklı değerler alırsınız <xref:System.Uri> .

UNIX üzerinde çalıştırıldığında aşağıdaki kodun çıkışını göz önünde bulundurun.

```csharp
var myUri = new Uri("/üri");

Console.WriteLine($"AbsoluteUri: {myUri.AbsoluteUri}");
Console.WriteLine($"ToString: {myUri.ToString()}");
```

Önceki .NET sürümündeki çıkış:

```text
AbsoluteUri: /%C3%BCri/%C3%BCri
ToString: /üri/üri
```

.NET 5 veya sonraki bir sürümde çıkış:

```text
AbsoluteUri: /%C3%BCri
ToString: /üri
```

## <a name="version-introduced"></a>Sunulan sürüm

5.0

## <a name="recommended-action"></a>Önerilen eylem

Yinelenen yol segmentlerini bekleyen ve hesapları bekleyen bir kodunuz varsa, bu kodu kaldırabilirsiniz.

## <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Uri?displayProperty=fullName>

<!--

### Category

Core .NET libraries

### Affected APIs

- `T:System.Uri`

-->
