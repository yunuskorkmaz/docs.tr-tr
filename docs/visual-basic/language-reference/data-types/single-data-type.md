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
ms.openlocfilehash: 60a688c510f6e36dca5809566b37a388429e18c7
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343927"
---
# <a name="single-data-type-visual-basic"></a>Single Veri Türü (Visual Basic)

, Negatif değerler için-3.4028235 E + 38 ila-1.401298 E-45 değerindeki ve pozitif değerler için 3.4028235 E + 38 ile 1.401298 E-45 arasında değişen, imzalanan IEEE 32-bit (4 baytlık) tek duyarlıklı kayan nokta sayılarını barındırır. Tek duyarlıklı sayılar gerçek bir sayının yaklaşık bir kısmını depolar.  
  
## <a name="remarks"></a>Açıklamalar  

 `Double`tam veri genişliğini gerektirmeyen kayan nokta değerlerini içermesi için `Single` veri türünü kullanın. Bazı durumlarda, ortak dil çalışma zamanı `Single` değişkenlerinizi birbirine yakından paketlenebilir ve bellek tüketimini kaydedebilir.  
  
 `Single` varsayılan değeri 0 ' dır.  
  
## <a name="programming-tips"></a>Programlama İpuçları  
  
- **Duyarlılık.** Kayan noktalı sayılarla çalışırken her zaman bellekte kesin bir gösterimine sahip olmadıkları göz önünde bulundurun. Bu, değer karşılaştırması ve `Mod` işleci gibi belirli işlemlerden beklenmedik sonuçlara neden olabilir. Daha fazla bilgi için bkz. [sorun giderme veri türleri](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).  
  
- **Kan.** `Single` veri türü `Double`widens. Bu, bir <xref:System.OverflowException?displayProperty=nameWithType> hatasıyla karşılaşmadan `Single` `Double` dönüştürebileceğiniz anlamına gelir.  
  
- **Sondaki sıfırlar.** Kayan nokta veri türlerinde sondaki 0 karakterden oluşan iç temsili yok. Örneğin, 4,2000 ve 4,2 arasında ayrım yapmazlar. Sonuç olarak, kayan nokta değerlerini görüntülerken veya yazdırdığınızda sondaki 0 karakter görünmez.  
  
- **Tür karakterleri.** Değişmez değer türü karakter `F` bir sabit değere eklenmesi, `Single` veri türüne zorlar. Tanımlayıcı türü karakter `!` herhangi bir tanımlayıcıya eklemek bunu `Single`zorlar.  
  
- **Çerçeve türü.** .NET Framework karşılık gelen tür <xref:System.Single?displayProperty=nameWithType> yapısıdır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Single?displayProperty=nameWithType>
- [Veri Türleri](../../../visual-basic/language-reference/data-types/index.md)
- [Decimal Veri Türü](../../../visual-basic/language-reference/data-types/decimal-data-type.md)
- [Double Veri Türü](../../../visual-basic/language-reference/data-types/double-data-type.md)
- [Tür Dönüştürme İşlevleri](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Dönüştürme Özeti](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Veri Türlerinin Etkili Kullanımı](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
- [Veri Türü Sorunlarını Giderme](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
