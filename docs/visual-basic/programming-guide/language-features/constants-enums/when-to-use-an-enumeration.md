---
title: Bir Numaralandırmanın Ne Zaman Kullanılacağı
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic]
ms.assetid: e6e47b5b-3ed9-452d-a481-9c3fed88519a
ms.openlocfilehash: ba69249e16b8c0ee06d57d06d192874a283b295e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403543"
---
# <a name="when-to-use-an-enumeration-visual-basic"></a>Bir Numaralandırmanın Ne Zaman Kullanılacağı (Visual Basic)
Numaralandırmalar ilgili sabitler kümesiyle çalışmanın kolay bir yolunu sunar. Bir sabit listesi veya `Enum` , bir değer kümesi için sembolik bir addır. Numaralandırmalar veri türleri olarak değerlendirilir ve bunları, değişkenler ve özelliklerle kullanılacak sabitler kümesi oluşturmak için kullanabilirsiniz.  
  
## <a name="when-to-use-an-enumeration"></a>Bir Numaralandırmanın Ne Zaman Kullanılacağı  
 Her bir yordam sınırlı bir değişken kümesini kabul ettiğinde, bir numaralandırma kullanmayı düşünün. Numaralandırmalar, özellikle anlamlı adlar kullanıldığında daha net ve daha okunabilir kod için yapılır.  
  
 Numaralandırmalar kullanmanın avantajları şunlardır:  
  
- Dışarı veya hatalı yazma numaralarının neden olduğu hataları azaltır.  
  
- Gelecekte değerlerin değiştirilmesini kolaylaştırır.  
  
- Kodu daha kolay okunabilir hale getirir, yani hataların buna katması daha az olabilir.  
  
- İleriye dönük uyumluluğu sağlar. Numaralandırmalar sayesinde, gelecekte birisi üye adlarına karşılık gelen değerleri değiştirirse kodunuzun başarısız olma olasılığı düşüktür.  
  
## <a name="naming-enumerations"></a>Sabit listeleri adlandırma  
 Numaralandırma üyeleri için bir adlandırma kuralı kullanın. Visual Basic bir numaralandırma üye adıyla karşılaştığında, başvurulan diğer tür kitaplıkları aynı adı içeriyorsa bir özel durum oluşabilir. Uygulamanızdan veya bileşeninizden değerleri tanımlayan benzersiz bir ön ek kullanın.  
  
 Bir numaralandırmanın üyesine başvuru yaparken, üye adını numaralandırma adıyla nitelemeniz veya daha sonra ifadesini kullanmanız gerekir `Imports` . Daha fazla bilgi için bkz. [numaralandırmalar ve ad niteliği](enumerations-and-name-qualification.md).  
  
## <a name="predefined-enumerations"></a>Önceden tanımlanmış numaralandırmalar  
 Visual Basic, `FirstDayOfWeek` kodunuzu kolaylaştırmak için ve gibi bir dizi önceden tanımlanmış sabit listesi sağlar `MsgBoxResult` . Bunların bir listesi için bkz. [sabitler ve numaralandırmalar](../../../language-reference/constants-and-enumerations.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: numaralandırma bildirme](how-to-declare-enumerations.md)
- [Nasıl yapılır: Bir Sabit Listesi Üyesine Başvurma](how-to-refer-to-an-enumeration-member.md)
- [Sabit Listeleri ve Ad Niteliği](enumerations-and-name-qualification.md)
- [Nasıl yapılır: Visual Basic'de Numaralandırma Yoluyla Yineleme Yapma](how-to-iterate-through-an-enumeration.md)
- [Nasıl yapılır: Bir Numaralandırma Değeriyle İlişkili Dizeyi Belirleme](how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [Enum Deyimi](../../../language-reference/statements/enum-statement.md)
- [Sabitler ve numaralandırmalar](../../../language-reference/constants-and-enumerations.md)
