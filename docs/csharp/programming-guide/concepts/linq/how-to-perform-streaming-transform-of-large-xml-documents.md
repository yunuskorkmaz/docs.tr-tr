---
title: Büyük XML belgelerinin akış dönüşümü nasıl yapılır (C#)
ms.date: 07/20/2015
ms.assetid: 5f16d1f8-5370-4b55-b0c8-e497df163037
ms.openlocfilehash: 9eb2e832f798e550ef3b534b0c9a0e3416378b43
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79169110"
---
# <a name="how-to-perform-streaming-transform-of-large-xml-documents-c"></a>Büyük XML belgelerinin akış dönüşümü nasıl yapılır (C#)
Bazen büyük XML dosyalarını dönüştürmeniz ve uygulamanın bellek ayak izinin öngörülebilir olması için uygulamanızı yazmanız gerekir. Bir XML ağacını çok büyük bir XML dosyasıyla doldurmaya çalışırsanız, bellek kullanımınız dosyanın boyutuyla orantılı olacaktır (diğer bir şekilde aşırı). Bu nedenle, bunun yerine bir akış tekniği kullanmanız gerekir.  
  
 Akış teknikleri en iyi kaynak belgeyi yalnızca bir kez işlemeniz gereken durumlarda uygulanır ve öğeleri belge sırasına göre işleyebilirsiniz. Kaynaklarını yineleyin, <xref:System.Linq.Enumerable.OrderBy%2A>tüm verileri toplar, sıralar ve ardından son olarak dizideki ilk öğeyi verir. İlk öğeyi vermeden önce kaynağını somutlaştıran bir sorgu işleci kullanırsanız, uygulamanız için küçük bir bellek ayak izini saklamayacağınızı unutmayın.  
  
[Üstbilgi bilgilerine (C#) erişebilen XML parçalarının akışı nda](./how-to-stream-xml-fragments-with-access-to-header-information.md)açıklanan tekniği kullansanız bile, dönüştürülmüş belgeyi içeren bir XML ağacını birleştirmeye çalışırsanız, bellek kullanımı çok büyük olacaktır.
  
 İki ana yaklaşım vardır. Bir yaklaşım ertelenmiş işleme özelliklerini <xref:System.Xml.Linq.XStreamingElement>kullanmaktır. Başka bir yaklaşım, <xref:System.Xml.XmlWriter>bir oluşturmak ve [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] bir <xref:System.Xml.XmlWriter>. Bu konu her iki yaklaşımı da gösterir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, [üstbilgi bilgilerine (C#) erişebilen XML parçalarının nasıl aktarılabildiğini](./how-to-stream-xml-fragments-with-access-to-header-information.md)örnekte oluşturur.
  
 Bu örnek, çıktıakışı <xref:System.Xml.Linq.XStreamingElement> için ertelenmiş yürütme yeteneklerini kullanır. Bu örnek, küçük bir bellek ayak izini korurken çok büyük bir belgeyi dönüştürebilir.  
  
 Özel eksenin (`StreamCustomerItem`) özel olarak yazıldığına, böylece `Customer` `Name`, `Item` , ve öğeleri olan bir belge beklediğini ve bu öğelerin aşağıdaki Source.xml belgesinde olduğu gibi düzenleneceğini unutmayın. Ancak daha sağlam bir uygulama, geçersiz bir belgeyi ayrıştırmaya hazır olacak.  
  
 Kaynak belge, Source.xml aşağıdaki gibidir:  
  
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
Aşağıdaki örnek, [üstbilgi bilgilerine (C#) erişebilen XML parçalarının nasıl aktarılabildiğini](./how-to-stream-xml-fragments-with-access-to-header-information.md)de örnekte oluşturur.
  
 Bu örnek, bir [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <xref:System.Xml.XmlWriter>öğeye öğe yazma özelliğini kullanır. Bu örnek, küçük bir bellek ayak izini korurken çok büyük bir belgeyi dönüştürebilir.  
  
 Özel eksenin (`StreamCustomerItem`) özel olarak yazıldığına, böylece `Customer` `Name`, `Item` , ve öğeleri olan bir belge beklediğini ve bu öğelerin aşağıdaki Source.xml belgesinde olduğu gibi düzenleneceğini unutmayın. Ancak daha sağlam bir uygulama, kaynak belgeyi xsd ile doğrular veya geçersiz bir belgeyi ayrıştırmaya hazır olur.  
  
 Bu örnek, bu konuda önceki örnek olarak aynı kaynak belge, Source.xml kullanır. Aynı zamanda tam olarak aynı çıktıüretir.  
  
 Çıkış <xref:System.Xml.Linq.XStreamingElement> xml akışı için kullanarak bir <xref:System.Xml.XmlWriter>.  
  
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
  