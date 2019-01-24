---
title: Bir Numaralandırmanın Ne Zaman Kullanılacağı (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic]
ms.assetid: e6e47b5b-3ed9-452d-a481-9c3fed88519a
ms.openlocfilehash: 826f8fffedb8c983423fbef0fbf1f4014d93be91
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54535027"
---
# <a name="when-to-use-an-enumeration-visual-basic"></a>Bir Numaralandırmanın Ne Zaman Kullanılacağı (Visual Basic)
Numaralandırmalar ilgili sabitlerinin kümeleriyle çalışmak için kolay bir yolunu sunar. Bir numaralandırma veya `Enum`, değerler için simgesel bir addır. Numaralandırmalar veri türleri olarak kabul edilir ve değişkenleri ve özellikleri ile kullanım için sabitler kümesini oluşturmak için kullanabilirsiniz.  
  
## <a name="when-to-use-an-enumeration"></a>Bir Numaralandırmanın Ne Zaman Kullanılacağı  
 Her bir yordam değişkenleri sınırlı sayıda kabul eder, bir numaralandırma kullanmayı düşünün. Özellikle anlamlı adlar kullanıldığında sabit listeleri için kodu daha anlaşılır ve daha okunabilir, olun.  
  
 Numaralandırmalar kullanmanın avantajları şunlardır:  
  
-   Sırasını değiştirme ya da sayı yanlış yazmanız kaynaklanan hataları azaltır.  
  
-   Değerleri gelecekte değiştirilmesini daha kolay hale getirir.  
  
-   Hataları içine şekilde katlamayı olasılığını yani kod okumak daha kolay hale getirir.  
  
-   İleriye dönük uyumluluk sağlar. Numaralandırmalar ile kodunuzu gelecekte birinin üyesi adlara karşılık gelen değerleri değişirse başarısız etkilenme olasılığı da düşer.  
  
## <a name="naming-enumerations"></a>Adlandırma sabit listeleri  
 Numaralandırma üyeleri için bir adlandırma kuralını kullanın. Visual Basic bir sabit listesi üye adı karşılaştığında, diğer başvurulan tür kitaplıkları aynı adı içeriyorsa bir özel durum. Uygulama veya bileşen değerleri tanımlayan benzersiz bir ön ekini kullanın.  
  
 Bir sabit listesi üyesi için söz konusu olduğunda, sabit listesi adı üye adıyla nitelemeniz veya desteklemeli kullanın `Imports` deyimi. Daha fazla bilgi için [numaralandırmalar ve ad niteliği](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md).  
  
## <a name="predefined-enumerations"></a>Önceden tanımlanmış sabit listeleri  
 Visual Basic sağlayan bir dizi önceden tanımlanmış sabit listeleri gibi `FirstDayOfWeek` ve `MsgBoxResult`, kodunuzu kolaylaştırmak için. Bunların bir listesi için bkz. [sabitler ve numaralandırmalar](../../../../visual-basic/language-reference/constants-and-enumerations.md).  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: Bir numaralandırma bildirme](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)
- [Nasıl yapılır: Bir numaralandırma üyesine başvurma](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)
- [Sabit Listeleri ve Ad Niteliği](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)
- [Nasıl yapılır: Visual Basic'de numaralandırma yoluyla yineleme yapma](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)
- [Nasıl yapılır: Bir numaralandırma değeriyle ilişkili dizeyi belirleme](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [Enum Deyimi](../../../../visual-basic/language-reference/statements/enum-statement.md)
- [Sabitler ve Sabit Listeleri](../../../../visual-basic/language-reference/constants-and-enumerations.md)
