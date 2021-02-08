---
description: 'Hakkında daha fazla bilgi edinin: Double veri türü (Visual Basic)'
title: Double Veri Türü
ms.date: 07/20/2015
f1_keywords:
- vb.Double
helpviewer_keywords:
- 'identifier type characters [Visual Basic], #'
- trailing zeros
- real numbers
- trailing 0 characters [Visual Basic]
- 0 characters [Visual Basic], trailing
- literal type characters [Visual Basic], R
- data types [Visual Basic], assigning
- Double data type [Visual Basic]
- '# identifier type character'
- double-precision numbers
- floating-point numbers [Visual Basic], Double data type
- R literal type character [Visual Basic]
- zeros, trailing
- Double data type
ms.assetid: 0c5670f7-fcb1-453a-bef1-374730cd38fd
ms.openlocfilehash: ae7b87b392038c67ba47e09d7ca995562bf06c1d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792225"
---
# <a name="double-data-type-visual-basic"></a>Double Veri Türü (Visual Basic)

Negatif değerler için-1.79769313486231570 E + 308 ile-4.94065645841246544 E-324 arasında ve pozitif değerler için 1.79769313486231570 E + 308 ile 4.94065645841246544 E-324 arasında yer alan imzalanmış IEEE 64-bit (8 baytlık) çift duyarlıklı kayan nokta sayılarını barındırır. Çift duyarlıklı sayılar gerçek bir sayının yaklaşık bir kısmını depolar.

## <a name="remarks"></a>Açıklamalar

`Double`Veri türü, bir sayı için en büyük ve en küçük olası magnitudes sağlar.

Varsayılan değeri 0 ' `Double` dır.

## <a name="programming-tips"></a>Programlama İpuçları

- **Duyarlılık.** Kayan noktalı sayılarla çalışırken her zaman bellekte kesin bir gösterimin olduğunu unutmayın. Bu, değer karşılaştırması ve işleç gibi belirli işlemlerden beklenmedik sonuçlara neden olabilir `Mod` . Daha fazla bilgi için bkz. [sorun giderme veri türleri](../../programming-guide/language-features/data-types/troubleshooting-data-types.md).

- **Sondaki sıfırlar.** Kayan nokta veri türlerinde sondaki sıfır karakteri iç temsili yok. Örneğin, 4,2000 ve 4,2 arasında ayrım yapmazlar. Sonuç olarak, kayan nokta değerlerini görüntülerken veya yazdırdığınızda sondaki sıfır karakter görünmez.

- **Tür karakterleri.** Değişmez değer türü karakterini `R` bir sabit değere eklemek, `Double` veri türüne zorlar. Örneğin, bir tamsayı değerinin arkasından `R` , değer bir olarak değiştirilir `Double` .

  ```vb
  ' Visual Basic expands the 4 in the statement Dim dub As Double = 4R to 4.0:
  Dim dub As Double = 4.0R
  ```

  Tanımlayıcı türü karakteri `#` herhangi bir tanımlayıcıya eklemek bunu öğesine zorlar `Double` . Aşağıdaki örnekte, değişkeni `num` şöyle yazılır `Double` :

  ```vb
  Dim num# = 3
  ```

- **Çerçeve türü.** .NET Framework karşılık gelen tür <xref:System.Double?displayProperty=nameWithType> yapısıdır.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Double?displayProperty=nameWithType>
- [Veri türleri](index.md)
- [Decimal Veri Türü](decimal-data-type.md)
- [Single Veri Türü](single-data-type.md)
- [Tür Dönüştürme İşlevleri](../functions/type-conversion-functions.md)
- [Dönüştürme Özeti](../keywords/conversion-summary.md)
- [Veri Türlerinin Etkili Kullanımı](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)
- [Veri Türü Sorunlarını Giderme](../../programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [Tür Karakterleri](../../programming-guide/language-features/data-types/type-characters.md)
