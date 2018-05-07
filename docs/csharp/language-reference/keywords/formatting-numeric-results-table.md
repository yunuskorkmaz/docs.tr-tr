---
title: Sayısal Sonuçlar Tablosunu Biçimlendirme (C# Başvurusu)
ms.date: 07/20/2015
helpviewer_keywords:
- formatting [C#]
- numeric formatting [C#]
- String.Format method
- Console.Write method
ms.assetid: 120ba537-4448-4c62-8676-7a8fdd98f496
ms.openlocfilehash: cc215971d63a0ee61eb25ac45834a81fbbc50b96
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="formatting-numeric-results-table-c-reference"></a>Sayısal Sonuçlar Tablosunu Biçimlendirme (C# Başvurusu)
Sayısal sonuçlar kullanarak biçimlendirebilirsiniz <xref:System.String.Format%2A?displayProperty=nameWithType> yöntemi, ile <xref:System.Console.Write%2A?displayProperty=nameWithType> veya <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> çağrı yöntemleri `String.Format`, veya kullanarak [dize ilişkilendirme](../tokens/interpolated.md). Biçim biçim dizeleri kullanılarak belirtilir. Aşağıdaki tabloda, desteklenen standart biçim dizeleri içerir. Biçim dizesi aşağıdaki biçimdedir: `Axx`, burada `A` biçim belirteci olan ve `xx` duyarlık Belirleyicisi değil. Sayısal değer uygulanan biçimlendirme türü biçim belirteci denetler ve önemli basamak sayısını veya ondalık biçimlendirilmiş çıkış duyarlık Belirleyicisi denetler. Duyarlık Belirleyicisi aralığından 0 ile 99 değeri.  
  
 Standart ve özel biçimlendirme dizeleri hakkında daha fazla bilgi için bkz: [biçimlendirme türleri](../../../standard/base-types/formatting-types.md).
  
|Biçim belirticisi|Açıklama|Örnekler|Çıkış|  
|----------------------|-----------------|--------------|------------|  
|C veya c|Para Birimi|Console.Write ("{0:C}", 2.5);<br /><br /> Console.Write ("{0:C}",-2.5);|$2.50<br /><br /> ($2.50)|  
|D veya d|Ondalık|Console.Write ("{0:D5}", 25);|00025|  
|E veya e|Bilimsel|Console.Write ("{0:E}", 250000);|2.500000E + 005|  
|F veya f|Sabit nokta|Console.Write ("{0:F2}", 25);<br /><br /> Console.Write ("{0:F0}", 25);|25.00<br /><br /> 25|  
|G veya g|Genel|Console.Write ("{0:G}", 2.5);|2,5|  
|N veya n|Sayı|Console.Write ("{0:N}", 2500000);|2,500,000.00|  
|X veya x|Onaltılık|Console.Write ("{0:X}", 250);<br /><br /> Console.Write ("{0:X}", 0xffff);|FA<br /><br /> FFFF|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [Standart Sayısal Biçim Dizeleri](../../../standard/base-types/standard-numeric-format-strings.md)  
 [Türler için Başvuru Tabloları](../../../csharp/language-reference/keywords/reference-tables-for-types.md)  
 [string](../../../csharp/language-reference/keywords/string.md)
