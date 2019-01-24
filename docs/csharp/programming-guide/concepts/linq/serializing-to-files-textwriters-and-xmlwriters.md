---
title: Dosya, TextWriters ve XmlWriters1 seri hale getirme
ms.date: 07/20/2015
ms.assetid: bd3ea6f7-895b-4ff4-a625-fe2bb55b1886
ms.openlocfilehash: 19371c0422c607171ccbea1235ea4348852d801c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54498823"
---
# <a name="serializing-to-files-textwriters-and-xmlwriters"></a>Dosya, TextWriters ve XmlWriters serileştirme
XML ağaçlarını serileştirebilen bir <xref:System.IO.File>, <xref:System.IO.TextWriter>, veya bir <xref:System.Xml.XmlWriter>.  
  
 Herhangi bir XML bileşeni serileştirebiliyorsa dahil olmak üzere <xref:System.Xml.Linq.XDocument> ve <xref:System.Xml.Linq.XElement>, kullanarak bir dizeye `ToString` yöntemi.  
  
 Bir dizeye serileştirilirken biçimlendirme gizlemek istiyorsanız, kullanabileceğiniz <xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType> yöntemi.  
  
 Bir dosyaya serileştirmek kullanırken varsayılan davranış (Girinti) elde edilen XML belgeyi Biçimlendir sağlamaktır. Girintisini zaman anlamsız boşluk XML ağacındaki korunmaz. Biçimlendirme ile seri hale getirmek için aşırı almaz aşağıdaki yöntemlerden birini kullanın: <xref:System.Xml.Linq.SaveOptions> bağımsız değişken olarak:  
  
-   <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>  
  
-   <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>  
  
 Seçeneği değil girinti ve XML ağacındaki Önemsiz bölünemez boşluğu koruyacak istiyorsanız, alan aşırı yüklemeler aşağıdaki yöntemlerden birini kullanın <xref:System.Xml.Linq.SaveOptions> bağımsız değişken olarak:  
  
-   <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>  
  
-   <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>  
  
 Örnekler için uygun bir başvuru konusuna bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Serileştirmek XML ağaçları (C#)](../../../../csharp/programming-guide/concepts/linq/serializing-xml-trees.md)
