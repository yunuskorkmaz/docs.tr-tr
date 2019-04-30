---
title: While Serializing2 boşluk koruma
ms.date: 07/20/2015
ms.assetid: 2d7abbd4-37f4-422b-89dd-0a694b5edc17
ms.openlocfilehash: a8903268f5ae1c2bc6c71a0998ba7d932f01e0ec
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61666124"
---
# <a name="preserving-white-space-while-serializing"></a>Serileştirirken Boşlukları Koruma
Bu konuda, bir XML ağacı serileştirilirken boşluk denetlemek nasıl açıklanmaktadır.  
  
 Sık karşılaşılan bir senaryodur girintili XML oku, herhangi bir boşluk metin düğümleri (diğer bir deyişle, beyaz boşluk olmayan koruma) olmadan bir bellek içi XML ağacı oluşturmak, bazı XML işlemleri ve XML girintilemeli kaydedin sağlamaktır. Biçimlendirme ile XML serileştirme, yalnızca önemli boşluk XML ağacındaki korunur. Varsayılan davranışı budur [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].  
  
 Başka bir yaygın bir senaryo, okuma ve değiştirme kasıtlı olarak girintili zaten XML sağlamaktır. Bu girinti herhangi bir şekilde değiştirmek istemeyebilirsiniz. Bunu yapmak için [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], yükleme veya XML Ayrıştırma ve XML serileştirme seçildiğinde biçimlendirmeyi devre dışı olduğunda bölünemez boşluğu koruyacak.  
  
## <a name="white-space-behavior-of-methods-that-serialize-xml-trees"></a>XML ağaçlarını serileştirme yöntemleri boşluk davranışını  
 Aşağıdaki yöntemleri <xref:System.Xml.Linq.XElement> ve <xref:System.Xml.Linq.XDocument> sınıfların serileştirmek bir XML ağacı. Bir dosyaya bir XML ağacı serileştirebilen bir <xref:System.IO.TextReader>, veya bir <xref:System.Xml.XmlReader>. `ToString` Yöntemi bir dizeye serileştirir.  
  
- <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>  
  
- <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>  
  
- [XElement.ToString()](xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType)
  
- [XDocument.ToString()](xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType)
  
 Yöntem değil izlerseniz <xref:System.Xml.Linq.SaveOptions> bağımsız değişken olarak, ardından yöntemi biçimlendirir (Girinti) serileştirilmiş XML. Bu durumda, XML ağacı Önemsiz tüm bölünemez boşluğu göz ardı edilir.  
  
 Yöntem alırsanız <xref:System.Xml.Linq.SaveOptions> bağımsız değişken olarak, ardından yöntemi olmayan biçimlendirme belirtebilirsiniz (Girinti) serileştirilmiş XML. Bu durumda, XML ağacındaki tüm boşluk korunur.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [(Visual Basic) XML ağaçlarını serileştirme](../../../../visual-basic/programming-guide/concepts/linq/serializing-xml-trees.md)
