---
title: 'Nasıl yapılır: (C#) büyük XML belgelerinin akış dönüşümünü gerçekleştirme'
ms.date: 07/20/2015
ms.assetid: 5f16d1f8-5370-4b55-b0c8-e497df163037
ms.openlocfilehash: f837117bec2bac615e4cbd822c1110f648d32ce8
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43514079"
---
# <a name="how-to-perform-streaming-transform-of-large-xml-documents-c"></a>Nasıl yapılır: (C#) büyük XML belgelerinin akış dönüşümünü gerçekleştirme
Bazen büyük XML dosyalarını dönüştürme ve uygulamanızı yazın, böylece bellek Ayak izi uygulamanın öngörülebilir gerekir. Çok büyük bir XML dosyası ile XML ağacı doldurma denerseniz, bellek kullanımınızı orantılı dosya boyutunu (diğer bir deyişle, aşırı). Bu nedenle, bir akış teknik yerine kullanmanız gerekir.  
  
 Akış teknikleri, burada yalnızca bir kez kaynak belge işlemek gereken ve belge sırada öğeleri işleyebilir durumlarda en iyi şekilde uygulanır. Belirli standart sorgu işleçleri gibi <xref:System.Linq.Enumerable.OrderBy%2A>kaynağına yineleme, tüm verileri Topla, sıralanmasını ve son sıradaki ilk öğeyi yield. İlk öğeyi oluşturan önce kaynağına gerçekleştiren bir sorgu işlecini kullanmak, bir küçük bellek Ayak izi'ı uygulamanız için korumaz unutmayın.  
  
 Açıklanan tekniği kullanıyor olsanız bile [nasıl yapılır: üst bilgileri (C#) erişimi Stream parçalarını](../../../../csharp/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md), dönüştürülen belgeyi, bellek kullanımı çok olacaktır içeren bir XML ağacı derlemek deneyin.  
  
 İki temel yaklaşım vardır. Ertelenen işlem özelliklerini kullanmak için bir yaklaşım ise <xref:System.Xml.Linq.XStreamingElement>. Başka bir yaklaşım oluşturmaktır bir <xref:System.Xml.XmlWriter>ve yeteneklerini [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] öğelerine yazmak için bir <xref:System.Xml.XmlWriter>. Bu konuda, her iki yaklaşım gösterilmektedir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek örnekte geliştirir [nasıl yapılır: üst bilgileri (C#) erişimi Stream parçalarını](../../../../csharp/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md).  
  
 Bu örnekte ertelenmiş yürütme yeteneklerini <xref:System.Xml.Linq.XStreamingElement> çıkış akışı. Bu örnek, bir küçük bellek Ayak izi korurken çok büyük bir belge dönüştürebilirsiniz.  
  
 Unutmayın özel eksen (`StreamCustomerItem`) ve böylece bir belgeye bekliyor özellikle yazılmış olan `Customer`, `Name`, ve `Item` öğeleri ve öğeler aşağıdaki Source.xml belgeyi olduğu gibi düzenlenir. Geçersiz bir belge ayrıştırılacak ancak daha sağlam bir uygulama hazırlanması.  
  
 Kaynak belge Source.xml verilmiştir:  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>   
<Root>  
  <Customer>  
    <Name>A. Datum Corporation</Name>  
    <Item>  
      <Key>0001</Key>  
    </Item>  
    <Item>  
      <Key>0002</Key>  
    </Item>  
    <Item>  
      <Key>0003</Key>  
    </Item>  
    <Item>  
      <Key>0004</Key>  
    </Item>  
  </Customer>  
  <Customer>  
    <Name>Fabrikam, Inc.</Name>  
    <Item>  
      <Key>0005</Key>  
    </Item>  
    <Item>  
      <Key>0006</Key>  
    </Item>  
    <Item>  
      <Key>0007</Key>  
    </Item>  
    <Item>  
      <Key>0008</Key>  
    </Item>  
  </Customer>  
  <Customer>  
    <Name>Southridge Video</Name>  
    <Item>  
      <Key>0009</Key>  
    </Item>  
    <Item>  
      <Key>0010</Key>  
    </Item>  
  </Customer>  
</Root>  
```  
  
```csharp  
static IEnumerable<XElement> StreamCustomerItem(string uri)  
{  
    using (XmlReader reader = XmlReader.Create(uri))  
    {  
        XElement name = null;  
        XElement item = null;  
  
        reader.MoveToContent();  
  
        // Parse the file, save header information when encountered, and yield the  
        // Item XElement objects as they are created.  
  
        // loop through Customer elements  
        while (reader.Read())  
        {  
            if (reader.NodeType == XmlNodeType.Element  
                && reader.Name == "Customer")  
            {  
                // move to Name element  
                while (reader.Read())  
                {  
                    if (reader.NodeType == XmlNodeType.Element &&  
                        reader.Name == "Name")  
                    {  
                        name = XElement.ReadFrom(reader) as XElement;  
                        break;  
                    }  
                }  
  
                // loop through Item elements  
                while (reader.Read())  
                {  
                    if (reader.NodeType == XmlNodeType.EndElement)  
                        break;  
                    if (reader.NodeType == XmlNodeType.Element  
                        && reader.Name == "Item")  
                    {  
                        item = XElement.ReadFrom(reader) as XElement;  
                        if (item != null)  
                        {  
                            XElement tempRoot = new XElement("Root",  
                                new XElement(name)  
                            );  
                            tempRoot.Add(item);  
                            yield return item;  
                        }  
                    }  
                }  
            }  
        }  
    }  
}  
  
static void Main(string[] args)  
{  
    XStreamingElement root = new XStreamingElement("Root",  
        from el in StreamCustomerItem("Source.xml")  
        select new XElement("Item",  
            new XElement("Customer", (string)el.Parent.Element("Name")),  
            new XElement(el.Element("Key"))  
        )  
    );  
    root.Save("Test.xml");  
    Console.WriteLine(File.ReadAllText("Test.xml"));  
}  
```  
  
 Bu kod aşağıdaki çıktıyı üretir:  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<Root>  
  <Item>  
    <Customer>A. Datum Corporation</Customer>  
    <Key>0001</Key>  
  </Item>  
  <Item>  
    <Customer>A. Datum Corporation</Customer>  
    <Key>0002</Key>  
  </Item>  
  <Item>  
    <Customer>A. Datum Corporation</Customer>  
    <Key>0003</Key>  
  </Item>  
  <Item>  
    <Customer>A. Datum Corporation</Customer>  
    <Key>0004</Key>  
  </Item>  
  <Item>  
    <Customer>Fabrikam, Inc.</Customer>  
    <Key>0005</Key>  
  </Item>  
  <Item>  
    <Customer>Fabrikam, Inc.</Customer>  
    <Key>0006</Key>  
  </Item>  
  <Item>  
    <Customer>Fabrikam, Inc.</Customer>  
    <Key>0007</Key>  
  </Item>  
  <Item>  
    <Customer>Fabrikam, Inc.</Customer>  
    <Key>0008</Key>  
  </Item>  
  <Item>  
    <Customer>Southridge Video</Customer>  
    <Key>0009</Key>  
  </Item>  
  <Item>  
    <Customer>Southridge Video</Customer>  
    <Key>0010</Key>  
  </Item>  
</Root>  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte de geliştirir [nasıl yapılır: üst bilgileri (C#) erişimi Stream parçalarını](../../../../csharp/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md).  
  
 Bu örnekte yeteneğini [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] öğelerine yazmak için bir <xref:System.Xml.XmlWriter>. Bu örnek, bir küçük bellek Ayak izi korurken çok büyük bir belge dönüştürebilirsiniz.  
  
 Unutmayın özel eksen (`StreamCustomerItem`) ve böylece bir belgeye bekliyor özellikle yazılmış olan `Customer`, `Name`, ve `Item` öğeleri ve öğeler aşağıdaki Source.xml belgeyi olduğu gibi düzenlenir. Daha sağlam bir uygulama, ancak bir XSD kaynak belge ya da doğrulamak veya geçersiz bir belge ayrıştırmak hazır olacaktır.  
  
 Bu örnek aynı kaynak belge Source.xml, bu konuda önceki örnekteki gibi kullanır. Ayrıca, tam olarak aynı çıktı üretir.  
  
 Kullanarak <xref:System.Xml.Linq.XStreamingElement> çıkış XML akış yazmak üzerinden tercih edilir bir <xref:System.Xml.XmlWriter>.  
  
```csharp  
static IEnumerable<XElement> StreamCustomerItem(string uri)  
{  
    using (XmlReader reader = XmlReader.Create(uri))  
    {  
        XElement name = null;  
        XElement item = null;  
  
        reader.MoveToContent();  
  
        // Parse the file, save header information when encountered, and yield the  
        // Item XElement objects as they are created.  
  
        // loop through Customer elements  
        while (reader.Read())  
        {  
            if (reader.NodeType == XmlNodeType.Element  
                && reader.Name == "Customer")  
            {  
                // move to Name element  
                while (reader.Read())  
                {  
                    if (reader.NodeType == XmlNodeType.Element &&  
                        reader.Name == "Name")  
                    {  
                        name = XElement.ReadFrom(reader) as XElement;  
                        break;  
                    }  
                }  
  
                // loop through Item elements  
                while (reader.Read())  
                {  
                    if (reader.NodeType == XmlNodeType.EndElement)  
                        break;  
                    if (reader.NodeType == XmlNodeType.Element  
                        && reader.Name == "Item")  
                    {  
                        item = XElement.ReadFrom(reader) as XElement;  
                        if (item != null) {  
                            XElement tempRoot = new XElement("Root",  
                                new XElement(name)  
                            );  
                            tempRoot.Add(item);  
                            yield return item;  
                        }  
                    }  
                }  
            }  
        }  
    }  
}  
  
static void Main(string[] args)  
{  
    IEnumerable<XElement> srcTree =  
        from el in StreamCustomerItem("Source.xml")  
        select new XElement("Item",  
            new XElement("Customer", (string)el.Parent.Element("Name")),  
            new XElement(el.Element("Key"))  
        );  
    XmlWriterSettings xws = new XmlWriterSettings();  
    xws.OmitXmlDeclaration = true;  
    xws.Indent = true;  
    using (XmlWriter xw = XmlWriter.Create("Output.xml", xws)) {  
        xw.WriteStartElement("Root");  
        foreach (XElement el in srcTree)  
            el.WriteTo(xw);  
        xw.WriteEndElement();  
    }  
  
    string str = File.ReadAllText("Output.xml");  
    Console.WriteLine(str);  
}  
```  
  
 Bu kod aşağıdaki çıktıyı üretir:  
  
```xml  
<Root>  
  <Item>  
    <Customer>A. Datum Corporation</Customer>  
    <Key>0001</Key>  
  </Item>  
  <Item>  
    <Customer>A. Datum Corporation</Customer>  
    <Key>0002</Key>  
  </Item>  
  <Item>  
    <Customer>A. Datum Corporation</Customer>  
    <Key>0003</Key>  
  </Item>  
  <Item>  
    <Customer>A. Datum Corporation</Customer>  
    <Key>0004</Key>  
  </Item>  
  <Item>  
    <Customer>Fabrikam, Inc.</Customer>  
    <Key>0005</Key>  
  </Item>  
  <Item>  
    <Customer>Fabrikam, Inc.</Customer>  
    <Key>0006</Key>  
  </Item>  
  <Item>  
    <Customer>Fabrikam, Inc.</Customer>  
    <Key>0007</Key>  
  </Item>  
  <Item>  
    <Customer>Fabrikam, Inc.</Customer>  
    <Key>0008</Key>  
  </Item>  
  <Item>  
    <Customer>Southridge Video</Customer>  
    <Key>0009</Key>  
  </Item>  
  <Item>  
    <Customer>Southridge Video</Customer>  
    <Key>0010</Key>  
  </Item>  
</Root>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.

- [Gelişmiş LINQ to XML programlama (C#)](../../../../csharp/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
