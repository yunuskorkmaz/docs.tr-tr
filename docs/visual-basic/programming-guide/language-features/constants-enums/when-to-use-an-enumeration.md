---
title: Bir Numaralandırmanın Ne Zaman Kullanılacağı
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic]
ms.assetid: e6e47b5b-3ed9-452d-a481-9c3fed88519a
ms.openlocfilehash: 5daae8d487ddfe079a54e305e59e32e8ded8f65e
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353956"
---
# <a name="when-to-use-an-enumeration-visual-basic"></a>Bir Numaralandırmanın Ne Zaman Kullanılacağı (Visual Basic)
Numaralandırmalar ilgili sabitler kümesiyle çalışmanın kolay bir yolunu sunar. Bir sabit listesi veya `Enum`, bir değerler kümesi için sembolik bir addır. Numaralandırmalar veri türleri olarak değerlendirilir ve bunları, değişkenler ve özelliklerle kullanılacak sabitler kümesi oluşturmak için kullanabilirsiniz.  
  
## <a name="when-to-use-an-enumeration"></a>Bir Numaralandırmanın Ne Zaman Kullanılacağı  
 Her bir yordam sınırlı bir değişken kümesini kabul ettiğinde, bir numaralandırma kullanmayı düşünün. Numaralandırmalar, özellikle anlamlı adlar kullanıldığında daha net ve daha okunabilir kod için yapılır.  
  
 Numaralandırmalar kullanmanın avantajları şunlardır:  
  
- Dışarı veya hatalı yazma numaralarının neden olduğu hataları azaltır.  
  
- Gelecekte değerlerin değiştirilmesini kolaylaştırır.  
  
- Kodu daha kolay okunabilir hale getirir, yani hataların buna katması daha az olabilir.  
  
- İleriye dönük uyumluluğu sağlar. Numaralandırmalar sayesinde, gelecekte birisi üye adlarına karşılık gelen değerleri değiştirirse kodunuzun başarısız olma olasılığı düşüktür.  
  
## <a name="naming-enumerations"></a>Sabit listeleri adlandırma  
 Numaralandırma üyeleri için bir adlandırma kuralı kullanın. Visual Basic bir numaralandırma üye adıyla karşılaştığında, başvurulan diğer tür kitaplıkları aynı adı içeriyorsa bir özel durum oluşabilir. Uygulamanızdan veya bileşeninizden değerleri tanımlayan benzersiz bir ön ek kullanın.  
  
 Bir numaralandırmanın üyesine başvuru yaparken, üye adını numaralandırma adıyla nitelemeniz veya `Imports` ifadesini kullanmanız gerekir. Daha fazla bilgi için bkz. [numaralandırmalar ve ad niteliği](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md).  
  
## <a name="predefined-enumerations"></a>Önceden tanımlanmış numaralandırmalar  
 Visual Basic, kodunuzu kolaylaştırmak için `FirstDayOfWeek` ve `MsgBoxResult`gibi önceden tanımlanmış bir dizi numaralandırma sağlar. Bunların bir listesi için bkz. [sabitler ve numaralandırmalar](../../../../visual-basic/language-reference/constants-and-enumerations.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: numaralandırma bildirme](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)
- [Nasıl yapılır: Bir Sabit Listesi Üyesine Başvurma](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)
- [Sabit Listeleri ve Ad Niteliği](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)
- [Nasıl yapılır: Visual Basic bir numaralandırmada yineleme yapma](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)
- [Nasıl yapılır: Bir Sabit Listesi Değeriyle İlişkili Dizeyi Belirleme](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [Enum Deyimi](../../../../visual-basic/language-reference/statements/enum-statement.md)
- [Sabitler ve Sabit Listeleri](../../../../visual-basic/language-reference/constants-and-enumerations.md)
