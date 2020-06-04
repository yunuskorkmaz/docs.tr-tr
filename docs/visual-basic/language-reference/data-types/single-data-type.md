---
title: Single Veri Türü
ms.date: 07/20/2015
f1_keywords:
- vb.Single
helpviewer_keywords:
- Single data type
- F literal type character [Visual Basic]
- trailing zeros
- real numbers
- literal type characters [Visual Basic], F
- trailing 0 characters [Visual Basic]
- identifier type characters [Visual Basic], !
- single-precision numbers
- '! identifier type character'
- 0 characters [Visual Basic], trailing
- data types [Visual Basic], assigning
- floating-point numbers [Visual Basic], Single data type
- numbers [Visual Basic], real
- zeros, trailing
- numbers [Visual Basic], floating point
ms.assetid: 224a2795-4cd5-496c-8f7a-a4f05a06d45d
ms.openlocfilehash: ecb0f5f6416a2dd4ddd6888cb80ed3ac11ee58df
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84415537"
---
# <a name="single-data-type-visual-basic"></a>Single Veri Türü (Visual Basic)

, Negatif değerler için-3.4028235 E + 38 ila-1.401298 E-45 değerindeki ve pozitif değerler için 3.4028235 E + 38 ile 1.401298 E-45 arasında değişen, imzalanan IEEE 32-bit (4 baytlık) tek duyarlıklı kayan nokta sayılarını barındırır. Tek duyarlıklı sayılar gerçek bir sayının yaklaşık bir kısmını depolar.  
  
## <a name="remarks"></a>Açıklamalar  

 `Single`Tam veri genişliğini gerektirmeyen kayan nokta değerlerini içermesi için veri türünü kullanın `Double` . Bazı durumlarda, ortak dil çalışma zamanı `Single` değişkenlerinizi birbirine yakından paketlenebilir ve bellek tüketimini kaydedebilir.  
  
 Varsayılan değeri 0 ' `Single` dır.  
  
## <a name="programming-tips"></a>Programlama İpuçları  
  
- **Duyarlılık.** Kayan noktalı sayılarla çalışırken her zaman bellekte kesin bir gösterimine sahip olmadıkları göz önünde bulundurun. Bu, değer karşılaştırması ve işleç gibi belirli işlemlerden beklenmedik sonuçlara neden olabilir `Mod` . Daha fazla bilgi için bkz. [sorun giderme veri türleri](../../programming-guide/language-features/data-types/troubleshooting-data-types.md).  
  
- **Kan.** `Single`Widens veri türü `Double` . Bu, `Single` `Double` bir hatayla karşılaşmadan ' a dönüştürebileceğiniz anlamına gelir <xref:System.OverflowException?displayProperty=nameWithType> .  
  
- **Sondaki sıfırlar.** Kayan nokta veri türlerinde sondaki 0 karakterden oluşan iç temsili yok. Örneğin, 4,2000 ve 4,2 arasında ayrım yapmazlar. Sonuç olarak, kayan nokta değerlerini görüntülerken veya yazdırdığınızda sondaki 0 karakter görünmez.  
  
- **Tür karakterleri.** Değişmez değer türü karakterini `F` bir sabit değere eklemek, `Single` veri türüne zorlar. Tanımlayıcı türü karakteri `!` herhangi bir tanımlayıcıya eklemek bunu öğesine zorlar `Single` .  
  
- **Çerçeve türü.** .NET Framework karşılık gelen tür <xref:System.Single?displayProperty=nameWithType> yapısıdır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Single?displayProperty=nameWithType>
- [Veri türleri](index.md)
- [Decimal Veri Türü](decimal-data-type.md)
- [Double Veri Türü](double-data-type.md)
- [Tür Dönüştürme İşlevleri](../functions/type-conversion-functions.md)
- [Dönüştürme Özeti](../keywords/conversion-summary.md)
- [Veri Türlerinin Etkili Kullanımı](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)
- [Veri Türü Sorunlarını Giderme](../../programming-guide/language-features/data-types/troubleshooting-data-types.md)
