---
title: Bir Numaralandırmanın Ne Zaman Kullanılacağı (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic]
ms.assetid: e6e47b5b-3ed9-452d-a481-9c3fed88519a
ms.openlocfilehash: e50057e114abae9fbf05c94ef0b60cf94b033a2b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33647316"
---
# <a name="when-to-use-an-enumeration-visual-basic"></a>Bir Numaralandırmanın Ne Zaman Kullanılacağı (Visual Basic)
Numaralandırmalar ilgili sabitleri kümeleriyle çalışmak için kolay bir yol sunar. Numaralandırma, bir ya da `Enum`, değer kümesi için bir simgesel ad. Numaralandırmalar veri türleri olarak kabul edilir ve değişkenleri ve özellikleri ile kullanım için sabitleri kümesi oluşturmak için kullanabilirsiniz.  
  
## <a name="when-to-use-an-enumeration"></a>Bir Numaralandırmanın Ne Zaman Kullanılacağı  
 Her bir yordam sınırlı sayıda değişkenleri kabul eder, numaralandırma kullanmayı düşünün. Özellikle anlamlı adları kullanıldığında numaralandırmalar NET ve daha okunabilir kodunu olun.  
  
 Numaralandırmalar kullanmanın avantajları şunlardır:  
  
-   Sırasını değiştirme veya numaraları yanlış yazmanız kaynaklanan hataları azaltır.  
  
-   Gelecekte değerlerini değiştirmek kolaylaştırır.  
  
-   Hataları içine şekilde işi olasılığını anlamına gelen kod okumak daha kolay hale getirir.  
  
-   İleriye dönük uyumluluk sağlar. Numaralandırmalar ile kodunuzu gelecekte birinin üyesi adlarına karşılık gelen değerleri değişirse başarısız daha az olasıdır.  
  
## <a name="naming-enumerations"></a>Numaralandırmalar adlandırma  
 Numaralandırma üyeleri için bir adlandırma kuralını kullanın. Visual Basic bir numaralandırma üye adı karşılaştığında, diğer başvurulan tür kitaplıklarının aynı ada sahip olması durumunda bir özel durum oluşturulabilir. Uygulama veya bileşenin değerleri tanımlayan benzersiz bir ön ekini kullanın.  
  
 Bir numaralandırma üyesi için söz konusu olduğunda, numaralandırma adıyla üye nitelemek veya desteklemeli kullanmak `Imports` deyimi. Daha fazla bilgi için bkz: [numaralandırmalar ve ad niteliği](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md).  
  
## <a name="predefined-enumerations"></a>Önceden tanımlanmış numaralandırmaları  
 Visual Basic sağlayan bir dizi önceden tanımlanmış numaralandırmalar gibi `FirstDayOfWeek` ve `MsgBoxResult`, kodunuzu kolaylaştırmak için. Bunların listesi için bkz: [sabitler ve numaralandırmalar](../../../../visual-basic/language-reference/constants-and-enumerations.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: bir numaralandırma bildirme](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)  
 [Nasıl yapılır: Bir Sabit Listesi Üyesine Başvurma](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)  
 [Sabit Listeleri ve Ad Niteliği](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)  
 [Nasıl yapılır: Visual Basic'de numaralandırma yoluyla yineleme](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)  
 [Nasıl yapılır: Bir Sabit Listesi Değeriyle İlişkili Dizeyi Belirleme](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)  
 [Enum Deyimi](../../../../visual-basic/language-reference/statements/enum-statement.md)  
 [Sabitler ve Sabit Listeleri](../../../../visual-basic/language-reference/constants-and-enumerations.md)
