---
title: Sayısal sonuçlar tablosunu biçimlendirme- C# başvuru
description: Standart sayısal C# biçim dizeleri hakkında bilgi edinin
ms.date: 09/20/2018
helpviewer_keywords:
- formatting [C#]
- numeric formatting [C#]
- String.Format method
ms.assetid: 120ba537-4448-4c62-8676-7a8fdd98f496
ms.openlocfilehash: eb93f0a4f3c66e9f7b295366a77b9fb099fc3a1e
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713505"
---
# <a name="formatting-numeric-results-table-c-reference"></a>Sayısal sonuçlar tablosunu biçimlendirme (C# başvuru)

Aşağıdaki tabloda sayısal sonuçları biçimlendirmek için desteklenen biçim belirticileri gösterilmektedir. Son sütundaki biçimlendirilen sonuç, "en-US" <xref:System.Globalization.CultureInfo>karşılık gelir.

|Biçim belirteci|Açıklama|Örnekler|Sonuç|  
|----------------------|-----------------|--------------|------------|  
|C veya c|Para Birimi|`string s = $"{2.5:C}";`<br /><br /> `string s = $"{-2.5:C}";`|\\$2,50<br /><br /> (\\$2,50)|  
|D veya d|Ondalık|`string s = $"{25:D5}";`|00025|  
|E veya e|Üstel|`string s = $"{250000:E2}";`|2.50 e + 005|  
|F veya f|Sabit nokta|`string s = $"{2.5:F2}";`<br /><br /> `string s = $"{2.5:F0}";`|2.50<br /><br /> 3|  
|G veya g|Genel|`string s = $"{2.5:G}";`|2,5|  
|N veya n|Sayısal|`string s = $"{2500000:N}";`|2,500,000.00|  
|P veya p|Yüzde|`string s = $"{0.25:P}";`|%25|  
|R veya r|Gidiş|`string s = $"{2.5:R}";`|2,5|  
|X veya x|Onaltılık|`string s = $"{250:X}";`<br /><br /> `string s = $"{0xffff:X}";`|BELIRLEDIĞINIZ<br /><br /> 'DIR|  

## <a name="remarks"></a>Açıklamalar

Bir biçim dizesi oluşturmak için Biçim belirleyicisi kullanın. Biçim dizesi şu biçimdedir: `Axx`, burada

- `A`, sayısal değere uygulanan biçimlendirme türünü denetleyen biçim belirticisidir.
- `xx`, biçimlendirilen çıktıda basamak sayısını etkileyen duyarlık belirticisidir. Duyarlık belirticisinin değeri, 0 ile 99 aralığındadır.

Ondalık ("D" veya "d") ve onaltılı ("X" veya "x") biçim belirticileri yalnızca integral türler için desteklenir. Gidiş dönüş ("R" veya "r") Biçim belirleyicisi yalnızca <xref:System.Single>, <xref:System.Double>ve <xref:System.Numerics.BigInteger> türleri için desteklenir.

Standart sayısal biçim dizeleri şunları destekler:

- Tüm sayısal türlerde `ToString` yönteminin bazı aşırı yüklemeleri. Örneğin, <xref:System.Int32.ToString%28System.String%29?displayProperty=nameWithType> ve <xref:System.Int32.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> yöntemlerine bir sayısal biçim dizesi sağlayabilirsiniz.

- Örneğin <xref:System.String.Format%2A?displayProperty=nameWithType> yöntemi tarafından desteklenen .NET [Bileşik biçimlendirme özelliği](../../../standard/base-types/composite-formatting.md).

- [Enterpolasyonlu dizeler](../tokens/interpolated.md).

Daha fazla bilgi için bkz. [Standart sayısal biçim dizeleri](../../../standard/base-types/standard-numeric-format-strings.md).

## <a name="see-also"></a>Ayrıca bkz.

- [C#Başvurunun](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [Biçimlendirme türleri](../../../standard/base-types/formatting-types.md)
- [Bileşik biçimlendirme](../../../standard/base-types/composite-formatting.md)
- [Dize ilişkilendirme](../tokens/interpolated.md)
- [string](../builtin-types/reference-types.md)
