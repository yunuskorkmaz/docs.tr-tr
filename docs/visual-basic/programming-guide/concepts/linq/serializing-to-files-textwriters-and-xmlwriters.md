---
title: Dosyaları, TextWriters ve XmlWriters3 seri hale getirme
ms.date: 07/20/2015
ms.assetid: 7a0c24df-79ef-41a0-87f5-e6cf79382da9
ms.openlocfilehash: ff877e3c800bd1409d796fb68d651175d3602e34
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33645323"
---
# <a name="serializing-to-files-textwriters-and-xmlwriters"></a>Dosyaları, TextWriters ve XmlWriters seri hale getirme
XML ağaçları serileştirebilen bir <xref:System.IO.File>, <xref:System.IO.TextWriter>, veya bir <xref:System.Xml.XmlWriter>.  
  
 Herhangi bir XML bileşeni serileştirebilen dahil olmak üzere <xref:System.Xml.Linq.XDocument> ve <xref:System.Xml.Linq.XElement>, kullanarak bir dizeye `ToString` yöntemi.  
  
 Bir dizeyi serileştirilirken biçimlendirme gizlemek istiyorsanız, kullanabileceğiniz <xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType> yöntemi.  
  
 Bir dosyaya serileştirilirken varsayılan (Girinti) sonuç XML belge biçimlendirmek için davranıştır. Girintisini zaman anlamsız boşluk XML ağacında korunmaz. Biçimlendirme ile seri hale getirmek için aşırı yararlanabilir mi aşağıdaki yöntemlerden birini kullanın <xref:System.Xml.Linq.SaveOptions> bağımsız değişken olarak:  
  
-   <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>  
  
-   <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>  
  
 Değil girinti ve önemsiz boşluk XML ağacında korumak için seçeneği istiyorsanız, alan aşırı yüklemeleri aşağıdaki yöntemlerden birini kullanın <xref:System.Xml.Linq.SaveOptions> bağımsız değişken olarak:  
  
-   <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>  
  
-   <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>  
  
 Örnekler için uygun başvuru konusuna bakın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Biçimlendiricisi XML ağaçları (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/serializing-xml-trees.md)
