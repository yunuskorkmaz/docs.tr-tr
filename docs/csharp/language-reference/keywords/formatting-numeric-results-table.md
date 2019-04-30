---
title: Sayısal sonuçlar tablosunu biçimlendirme - C# başvurusu
ms.custom: seodec18
description: C# standart sayısal biçim dizeleri hakkında bilgi edinin
ms.date: 09/20/2018
helpviewer_keywords:
- formatting [C#]
- numeric formatting [C#]
- String.Format method
ms.assetid: 120ba537-4448-4c62-8676-7a8fdd98f496
ms.openlocfilehash: 12fe89e3aa63e9d3d8c3f102fe5a01a5f2225375
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61661561"
---
# <a name="formatting-numeric-results-table-c-reference"></a>Biçimlendirme sayısal sonuçlar tablosunu (C# Başvurusu)

Aşağıdaki tablo, sayısal sonuçlarını biçimlendirme için desteklenen biçim belirticileri gösterir. Biçimlendirilmiş sonuç son sütunda "en-US" karşılık gelen <xref:System.Globalization.CultureInfo>.

|Biçim belirteci|Açıklama|Örnekler|Sonuç|  
|----------------------|-----------------|--------------|------------|  
|C ya da c|Para Birimi|`string s = $"{2.5:C}";`<br /><br /> `string s = $"{-2.5:C}";`|$2.50<br /><br /> ($2.50)|  
|D veya d|Ondalık|`string s = $"{25:D5}";`|00025|  
|E veya e|Üstel|`string s = $"{250000:E2}";`|2.50E + 005|  
|F veya f|Sabit nokta|`string s = $"{2.5:F2}";`<br /><br /> `string s = $"{2.5:F0}";`|2.50<br /><br /> 3|  
|G veya g|Genel|`string s = $"{2.5:G}";`|2,5|  
|N veya n|Numeric|`string s = $"{2500000:N}";`|2,500,000.00|  
|P ya da p|Yüzde|`string s = $"{0.25:P}";`|25.00%|  
|R veya r|Gidiş|`string s = $"{2.5:R}";`|2,5|  
|X ya da x|Onaltılık|`string s = $"{250:X}";`<br /><br /> `string s = $"{0xffff:X}";`|FA<br /><br /> FFFF|  

## <a name="remarks"></a>Açıklamalar

Bir biçim belirticisi bir biçim dizesi oluşturmak için kullanın. Biçim dizesi aşağıdaki şekildedir: `Axx`burada

- `A` Biçimlendirme sayısal değere uygulanmış türünü denetleyen biçim belirticisi ' dir.
- `xx` biçimlendirilmiş çıktı basamak sayısını etkiler. duyarlık belirticisi ' dir. Duyarlık belirticisi aralıkları 0 ile 99 değeri.

Ondalık ("D" veya "d") ve ("X" veya "x") onaltılı biçim belirticileri yalnızca integral türleri için desteklenir. Gidiş dönüş ("R" veya "r") biçim tanımlayıcısı sadece desteklenen <xref:System.Single>, <xref:System.Double>, ve <xref:System.Numerics.BigInteger> türleri.

Standart sayısal biçim dizeleri tarafından desteklenir:

- Bazı aşırı yüklemeleri `ToString` tüm sayısal türlerin yöntemi. Örneğin, bir sayısal biçim dizesi sağlayabilirsiniz <xref:System.Int32.ToString%28System.String%29?displayProperty=nameWithType> ve <xref:System.Int32.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> yöntemleri.

- .NET [bileşik biçimlendirme özelliği](../../../standard/base-types/composite-formatting.md), tarafından desteklenen <xref:System.String.Format%2A?displayProperty=nameWithType> örneğin bir yöntem.

- [İlişkilendirilmiş dizeler](../tokens/interpolated.md).

Daha fazla bilgi için [standart sayısal biçim dizeleri](../../../standard/base-types/standard-numeric-format-strings.md).

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [Türler için başvuru tabloları](reference-tables-for-types.md)
- [Biçimlendirme türleri](../../../standard/base-types/formatting-types.md)
- [Bileşik biçimlendirme](../../../standard/base-types/composite-formatting.md)
- [Dize ilişkilendirme](../tokens/interpolated.md)
- [string](string.md)
