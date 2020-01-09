---
title: XElement sınıfına genel bakışC#()
ms.date: 07/20/2015
ms.assetid: 2b9f0cd8-a1d1-4037-accf-0f38a410fa11
ms.openlocfilehash: d77c725b3c786b8a8fa2b0eeab4bc4b30f298218
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/03/2020
ms.locfileid: "75635476"
---
# <a name="xelement-class-overview-c"></a>XElement sınıfına genel bakışC#()
<xref:System.Xml.Linq.XElement> sınıfı, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]temel sınıflardan biridir. Bir XML öğesini temsil eder. Bu sınıfı, öğeler oluşturmak için kullanabilirsiniz; öğenin içeriğini değiştirme; alt öğeleri ekleyin, değiştirin veya silin; özniteliği bir öğeye ekleyin; veya metin biçimindeki bir öğenin içeriğini seri hale getirme. Ayrıca, <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>ve <xref:System.Xml.Xsl.XslCompiledTransform>gibi <xref:System.Xml?displayProperty=nameWithType>diğer sınıflarla da birlikte kullanabilirsiniz.  
  
Bu konu, <xref:System.Xml.Linq.XElement> sınıfı tarafından sunulan işlevleri açıklamaktadır.  
  
## <a name="constructing-xml-trees"></a>XML ağaçları oluşturma  
 Aşağıdakiler dahil olmak üzere çeşitli yollarla XML ağaçları oluşturabilirsiniz:  
  
- Kodda bir XML ağacı oluşturabilirsiniz. Daha fazla bilgi için bkz. [xml ağaçları oluşturmaC#()](./linq-to-xml-overview.md).  
  
- <xref:System.IO.TextReader>, metin dosyaları veya Web adresi (URL) dahil olmak üzere çeşitli kaynaklardan XML ayrıştırılabilir. Daha fazla bilgi için bkz. [XML (C#) ayrıştırma](./how-to-parse-a-string.md).  
  
- Ağacı doldurmak için bir <xref:System.Xml.XmlReader> kullanabilirsiniz. Daha fazla bilgi için bkz. <xref:System.Xml.Linq.XNode.ReadFrom%2A>.  
  
- Bir <xref:System.Xml.XmlWriter>içerik yazabilmesi için bir modülünüzün varsa, bir yazıcı oluşturmak, yazıcıyı modüle geçirmek ve sonra da XML ağacını doldurmak için <xref:System.Xml.XmlWriter> yazılan içeriği kullanmak için <xref:System.Xml.Linq.XContainer.CreateWriter%2A> yöntemini kullanabilirsiniz.  
  
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
 XML ağacını bir <xref:System.IO.File>, <xref:System.IO.TextWriter>veya <xref:System.Xml.XmlWriter>seri hale getirebilirsiniz.  
  
 Daha fazla bilgi için bkz. [XML ağaçlarını serileştirmeC#()](./preserving-white-space-while-serializing.md).  
  
## <a name="retrieving-xml-data-via-axis-methods"></a>XML verilerini eksen yöntemleri aracılığıyla alma  
 Öznitelikleri, alt öğeleri, alt öğeleri ve üst öğeleri almak için eksen yöntemlerini kullanabilirsiniz. LINQ sorguları eksen yöntemleri üzerinde çalışır ve bir XML ağacı üzerinde gezinmek ve işlemek için çeşitli esnek ve güçlü yollar sunar.  
  
 Daha fazla bilgi için bkz. [LINQ to XML eksenleriC#()](./linq-to-xml-axes-overview.md).  
  
## <a name="querying-xml-trees"></a>XML Ağaçlarını Sorgulama  
 XML ağacından veri çıkaran LINQ sorguları yazabilirsiniz.  
  
 Daha fazla bilgi için bkz. [XML ağaçlarını sorgulamaC#()](./how-to-find-an-element-with-a-specific-attribute.md).  
  
## <a name="modifying-xml-trees"></a>XML ağaçlarını değiştirme  
 Bir öğeyi, içeriğini veya özniteliklerini değiştirme gibi çeşitli yollarla değiştirebilirsiniz. Ayrıca bir öğeyi üst öğesinden da kaldırabilirsiniz.  
  
 Daha fazla bilgi için bkz. [XML ağaçlarını değiştirme (LINQ to XML)C#()](./in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to XML programlamaya genel bakışC#()](serializing-to-files-textwriters-and-xmlwriters.md)
