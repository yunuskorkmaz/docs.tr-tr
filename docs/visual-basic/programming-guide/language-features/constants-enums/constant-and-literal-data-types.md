---
title: Sabit ve Değişmez Değerli Veri Türleri
ms.date: 07/20/2015
helpviewer_keywords:
- declaring constants [Visual Basic], literal data types
- data types [Visual Basic], declaring
- constants [Visual Basic], declaring
- explicit declarations
- literals [Visual Basic], coercing data type
- declarations [Visual Basic], data types
ms.assetid: 057206d2-3a5b-40b9-b3af-57446f9b52fa
ms.openlocfilehash: 8ebecddfab0724023c269e92c1fc5534f096bf1c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74333723"
---
# <a name="constant-and-literal-data-types-visual-basic"></a>Sabit ve Değişmez Değerli Veri Türleri (Visual Basic)
Değişmez değer, değişkenin değeri veya "Hello" dizesi gibi bir ifadenin sonucu yerine kendisini ifade eden bir değerdir. Sabit, bir sabit değerin yerini alan anlamlı bir addır ve değer değişebilir bir değişkenin aksine, bu değeri program genelinde tutar.  
  
 [Option Infer](../../../../visual-basic/language-reference/statements/option-infer-statement.md) `Off` ve [Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md) `On`, bir veri türü ile tüm sabitleri açıkça bildirmeniz gerekir. Aşağıdaki örnekte `MyByte` veri türü açıkça veri türü olarak `Byte`olarak bildirilmiştir:  
  
 [!code-vb[VbVbalrConstants#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConstants/VB/Class1.vb#1)]  
  
 `Option Infer` `On` veya `Option Strict` `Off`olduğunda, bir `As` yan tümcesiyle veri türü belirtmeden bir sabit bildirebilirsiniz. Derleyici, ifadenin türünden sabit türünü belirler. Sayısal tamsayı sabit değeri, `Integer` veri türüne varsayılan olarak ayarlanır. Kayan nokta numaraları için varsayılan veri türü `Double`ve anahtar sözcükler `True` ve `False` bir `Boolean` sabiti belirler.  
  
## <a name="literals-and-type-coercion"></a>Değişmez değerler ve tür zorlaması  
 Bazı durumlarda, bir sabit değeri belirli bir veri türüne zorlamak isteyebilirsiniz; Örneğin, `Decimal`türünde bir değişkene özellikle büyük bir integral sabit değeri atarken. Aşağıdaki örnek bir hata üretir:  
  
```vb  
Dim myDecimal as Decimal  
myDecimal = 100000000000000000000   ' This causes a compiler error.  
```  
  
 Hata, sabit değerinin gösteriminden kaynaklanmaktadır. `Decimal` veri türü bu büyüklükte bir değer tutabilir, ancak değişmez değer örtük olarak bir `Long`olarak temsil edilir; bu, olamaz.  
  
 Bir sabit değeri, belirli bir veri türüne iki şekilde dönüştürebilirsiniz: buna bir tür karakteri ekleyerek veya kapsayan karakterlerin içine yerleştirerek. Bir tür karakteri veya kapsayan karakterler, hiçbir türden boşluk veya karakter olmadan hemen önce ve/veya sabit değer içermelidir.  
  
 Önceki örneğin çalışmasını sağlamak için, `D` tür karakterini literal ekleyebilirsiniz, bu da `Decimal`olarak temsil edilmesine neden olur:  
  
 [!code-vb[VbVbalrConstants#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConstants/VB/Class1.vb#2)]  
  
 Aşağıdaki örnek, tür karakterlerinin ve kapsayan karakterlerin doğru kullanımını gösterir:  
  
 [!code-vb[VbVbalrConstants#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConstants/VB/Class1.vb#3)]  
  
 Aşağıdaki tabloda, Visual Basic ' de bulunan karakterlerin ve tür karakterlerinin gösterildiği gösterilmektedir.  
  
|Veri türü|Kapsayan karakter|Eklenen tür karakteri|  
|---|---|---|  
|`Boolean`|seçim|seçim|  
|`Byte`|seçim|seçim|  
|`Char`|"|Mş|  
|`Date`|#|seçim|  
|`Decimal`|seçim|D veya @|  
|`Double`|seçim|R veya #|  
|`Integer`|seçim|I veya%|  
|`Long`|seçim|L veya &|  
|`Short`|seçim|S|  
|`Single`|seçim|F veya!|  
|`String`|"|seçim|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Kullanıcı Tanımlı Sabitler](../../../../visual-basic/programming-guide/language-features/constants-enums/user-defined-constants.md)
- [Nasıl yapılır: Bir Sabit Bildirme](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-a-constant.md)
- [Sabitlere Genel Bakış](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)
- [Option Strict Deyimi](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [Option Explicit Deyimi](../../../../visual-basic/language-reference/statements/option-explicit-statement.md)
- [Sabit Listelerine Genel Bakış](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)
- [Nasıl yapılır: numaralandırma bildirme](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)
- [Sabit Listeleri ve Ad Niteliği](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)
- [Veri Türleri](../../../../visual-basic/language-reference/data-types/index.md)
- [Sabitler ve Sabit Listeleri](../../../../visual-basic/language-reference/constants-and-enumerations.md)
