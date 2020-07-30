---
title: XElement sınıfına genel bakış (C#)
description: XElement sınıfı, C# içindeki bir XML öğesini temsil eder. Bu, LINQ to XML temel sınıflardan biridir. XElement tarafından sunulan işlevsellik hakkında bilgi edinin.
ms.date: 07/20/2015
ms.assetid: 2b9f0cd8-a1d1-4037-accf-0f38a410fa11
ms.openlocfilehash: f76f51703de054443f47531294777b43a9c0b004
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302184"
---
# <a name="xelement-class-overview-c"></a>XElement sınıfına genel bakış (C#)
<xref:System.Xml.Linq.XElement>Sınıfı, içindeki temel sınıflardan biridir [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] . Bir XML öğesini temsil eder. Bu sınıfı, öğeler oluşturmak için kullanabilirsiniz; öğenin içeriğini değiştirme; alt öğeleri ekleyin, değiştirin veya silin; özniteliği bir öğeye ekleyin; veya metin biçimindeki bir öğenin içeriğini seri hale getirme. Ayrıca, ve gibi diğer sınıflarla da birlikte kullanabilirsiniz <xref:System.Xml?displayProperty=nameWithType> <xref:System.Xml.XmlReader> <xref:System.Xml.XmlWriter> <xref:System.Xml.Xsl.XslCompiledTransform> .  
  
Bu konu, sınıfının sunduğu işlevselliği açıklar <xref:System.Xml.Linq.XElement> .  
  
## <a name="constructing-xml-trees"></a>XML ağaçları oluşturma  
 Aşağıdakiler dahil olmak üzere çeşitli yollarla XML ağaçları oluşturabilirsiniz:  
  
- Kodda bir XML ağacı oluşturabilirsiniz. Daha fazla bilgi için bkz. [xml ağaçları oluşturma (C#)](./linq-to-xml-overview.md).  
  
- Bir <xref:System.IO.TextReader> metin dosyası veya bir Web adresi (URL) dahil olmak üzere çeşitli kaynaklardan XML ayrıştırabilirsiniz. Daha fazla bilgi için bkz. [XML 'ı ayrıştırma (C#)](./how-to-parse-a-string.md).  
  
- <xref:System.Xml.XmlReader>Ağacı doldurmak için kullanabilirsiniz. Daha fazla bilgi için bkz. <xref:System.Xml.Linq.XNode.ReadFrom%2A>.  
  
- İçine içerik yazabileceği bir modülünüzün varsa, bir <xref:System.Xml.XmlWriter> <xref:System.Xml.Linq.XContainer.CreateWriter%2A> yazıcı oluşturmak, yazıcıyı modüle geçirmek ve ardından <xref:System.Xml.XmlWriter> XML ağacını doldurmak için öğesine yazılan içeriği kullanmak için yöntemini kullanabilirsiniz.  
  
 Ancak, bir XML ağacı oluşturmanın en yaygın yolu aşağıdaki gibidir:  
  
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
  
 Bir XML ağacı oluşturmaya yönelik başka bir çok yaygın teknik, aşağıdaki örnekte gösterildiği gibi bir XML ağacını doldurmak için bir LINQ sorgusunun sonuçlarının kullanılmasını içerir:  
  
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
  
 Bu örnek aşağıdaki çıktıyı üretir:  
  
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
 XML ağacını bir <xref:System.IO.File> , a veya olarak seri hale getirebilirsiniz <xref:System.IO.TextWriter> <xref:System.Xml.XmlWriter> .  
  
 Daha fazla bilgi için bkz. [XML ağaçlarını serileştirme (C#)](./preserving-white-space-while-serializing.md).  
  
## <a name="retrieving-xml-data-via-axis-methods"></a>XML verilerini eksen yöntemleri aracılığıyla alma  
 Öznitelikleri, alt öğeleri, alt öğeleri ve üst öğeleri almak için eksen yöntemlerini kullanabilirsiniz. LINQ sorguları eksen yöntemleri üzerinde çalışır ve bir XML ağacı üzerinde gezinmek ve işlemek için çeşitli esnek ve güçlü yollar sunar.  
  
 Daha fazla bilgi için bkz. [LINQ to XML eksenleri (C#)](./linq-to-xml-axes-overview.md).  
  
## <a name="querying-xml-trees"></a>XML Ağaçlarını Sorgulama  
 XML ağacından veri çıkaran LINQ sorguları yazabilirsiniz.  
  
 Daha fazla bilgi için bkz. [XML ağaçlarını sorgulama (C#)](./how-to-find-an-element-with-a-specific-attribute.md).  
  
## <a name="modifying-xml-trees"></a>XML ağaçlarını değiştirme  
 Bir öğeyi, içeriğini veya özniteliklerini değiştirme gibi çeşitli yollarla değiştirebilirsiniz. Ayrıca bir öğeyi üst öğesinden da kaldırabilirsiniz.  
  
 Daha fazla bilgi için bkz. [XML ağaçlarını değiştirme (LINQ to XML) (C#)](./in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to XML programlamaya genel bakış (C#)](serializing-to-files-textwriters-and-xmlwriters.md)
