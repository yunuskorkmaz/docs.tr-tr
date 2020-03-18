---
title: XElement Sınıfına Genel Bakış (C#)
ms.date: 07/20/2015
ms.assetid: 2b9f0cd8-a1d1-4037-accf-0f38a410fa11
ms.openlocfilehash: 6a93dd4bdaf16fddff800b08b0f3146ecb63f9b7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79167900"
---
# <a name="xelement-class-overview-c"></a>XElement Sınıfına Genel Bakış (C#)
Sınıf, <xref:System.Xml.Linq.XElement> .................................................................................................. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] Bir XML öğesini temsil eder. Bu sınıfı öğeleri oluşturmak için kullanabilirsiniz; öğenin içeriğini değiştirmek; alt öğeleri ekleme, değiştirme veya silme; bir öğeye öznitelikleri eklemek; veya metin biçiminde bir öğenin içeriğini serihale. <xref:System.Xml?displayProperty=nameWithType>Ayrıca, <xref:System.Xml.XmlReader>, , <xref:System.Xml.XmlWriter>, ve <xref:System.Xml.Xsl.XslCompiledTransform>.  
  
Bu <xref:System.Xml.Linq.XElement> konu, sınıf tarafından sağlanan işlevselliği açıklar.  
  
## <a name="constructing-xml-trees"></a>XML Ağaçlarının İnşası  
 XML ağaçları aşağıdakiler de dahil olmak üzere çeşitli şekillerde oluşturabilirsiniz:  
  
- Kod da bir XML ağacı oluşturabilirsiniz. Daha fazla bilgi için Bkz. [XML Ağaçları Oluşturma (C#)](./linq-to-xml-overview.md).  
  
- XML'i <xref:System.IO.TextReader>metin dosyaları veya Web adresi (URL) dahil olmak üzere çeşitli kaynaklardan ayrışdırabilirsiniz. Daha fazla bilgi için Bkz. [Ayrıştırma XML (C#)](./how-to-parse-a-string.md).  
  
- Ağacı doldurmak <xref:System.Xml.XmlReader> için bir kullanabilirsiniz. Daha fazla bilgi için bkz. <xref:System.Xml.Linq.XNode.ReadFrom%2A>.  
  
- Bir içeriğe içerik yazabilen <xref:System.Xml.XmlWriter>bir modülüz <xref:System.Xml.Linq.XContainer.CreateWriter%2A> varsa, bir yazar oluşturmak, yazarı modüle geçirmek ve ardından XML <xref:System.Xml.XmlWriter> ağacını doldurmak için yazılan içeriği kullanmak için yöntemi kullanabilirsiniz.  
  
 Ancak, bir XML ağacı oluşturmak için en yaygın yolu aşağıdaki gibidir:  
  
```csharp  
XElement contacts =  
    new XElement("Contacts",  
        new XElement("Contact",  
            new XElement("Name", "Patrick Hines"),
            new XElement("Phone", "206-555-0144"),  
            new XElement("Address",  
                new XElement("Street1", "123 Main St"),  
                new XElement("City", "Mercer Island"),  
                new XElement("State", "WA"),  
                new XElement("Postal", "68042")  
            )  
        )  
    );  
```  
  
 Bir XML ağacı oluşturmak için başka bir çok yaygın teknik aşağıdaki örnekte gösterildiği gibi, bir XML ağacı doldurmak için bir LINQ sorgusunun sonuçlarını kullanarak içerir:  
  
```csharp  
XElement srcTree = new XElement("Root",  
    new XElement("Element", 1),  
    new XElement("Element", 2),  
    new XElement("Element", 3),  
    new XElement("Element", 4),  
    new XElement("Element", 5)  
);  
XElement xmlTree = new XElement("Root",  
    new XElement("Child", 1),  
    new XElement("Child", 2),  
    from el in srcTree.Elements()  
    where (int)el > 2  
    select el  
);  
Console.WriteLine(xmlTree);  
```  
  
 Bu örnek, aşağıdaki çıktıyı üretir:  
  
```xml  
<Root>  
  <Child>1</Child>  
  <Child>2</Child>  
  <Element>3</Element>  
  <Element>4</Element>  
  <Element>5</Element>  
</Root>  
```  
  
## <a name="serializing-xml-trees"></a>XML Ağaçlarını Serileştirme  
 XML ağacını bir <xref:System.IO.File>, a <xref:System.IO.TextWriter>veya bir <xref:System.Xml.XmlWriter>.  
  
 Daha fazla bilgi için bkz: [Serializing XML Ağaçlar (C#)](./preserving-white-space-while-serializing.md).  
  
## <a name="retrieving-xml-data-via-axis-methods"></a>Eksen Yöntemleri ile XML Veri alma  
 Öznitelikleri, alt öğeleri, soyundan gelen öğeleri ve ata öğelerini almak için eksen yöntemlerini kullanabilirsiniz. LINQ sorguları eksen yöntemleri üzerinde çalışır ve bir XML ağacında gezinmek ve işlemek için birkaç esnek ve güçlü yol sağlar.  
  
 Daha fazla bilgi için [LinQ to XML Axes (C#)](./linq-to-xml-axes-overview.md)için bkz.  
  
## <a name="querying-xml-trees"></a>XML Ağaçlarını Sorgulama  
 Bir XML ağacından veri ayıklayan LINQ sorguları yazabilirsiniz.  
  
 Daha fazla bilgi için Bkz. [XML AğaçLarını Sorgula (C#)](./how-to-find-an-element-with-a-specific-attribute.md).  
  
## <a name="modifying-xml-trees"></a>XML Ağaçlarını Değiştirme  
 Bir öğeyi, içeriğini veya özniteliklerini değiştirme de dahil olmak üzere çeşitli şekillerde değiştirebilirsiniz. Bir öğeyi üst öğesinden de kaldırabilirsiniz.  
  
 Daha fazla bilgi için bkz: [XML Ağaçlarını Değiştirme (LINQ to XML) (C#)](./in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ - XML Programlamaya Genel Bakış (C#)](serializing-to-files-textwriters-and-xmlwriters.md)
