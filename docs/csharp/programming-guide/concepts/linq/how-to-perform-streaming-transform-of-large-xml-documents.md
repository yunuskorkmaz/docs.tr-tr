---
title: Büyük XML belgelerinin akış dönüşümünü gerçekleştirme (C#)
ms.date: 07/20/2015
ms.assetid: 5f16d1f8-5370-4b55-b0c8-e497df163037
ms.openlocfilehash: 86b74534635dcca7e8c7f94873abcb50ea7c4d2b
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75345821"
---
# <a name="how-to-perform-streaming-transform-of-large-xml-documents-c"></a>Büyük XML belgelerinin akış dönüşümünü gerçekleştirme (C#)
Bazen büyük XML dosyalarını dönüştürmeniz ve uygulamanın bellek parmak izin tahmin edilebilir olması için uygulamanızı yazmanız gerekir. Bir XML ağacını çok büyük bir XML dosyası ile doldurmayı denerseniz, bellek kullanımınız dosyanın boyutuyla (aşırı) orantılı olacaktır. Bu nedenle, bunun yerine bir akış tekniği kullanmanız gerekir.  
  
 Akış teknikleri en iyi şekilde, kaynak belgeyi yalnızca bir kez işleyebilmeniz ve öğeleri belge düzeninde işleyebilirsiniz. <xref:System.Linq.Enumerable.OrderBy%2A>gibi bazı standart sorgu işleçleri, kaynaklarını yineleyebilir, tüm verileri toplar, sıralar ve son olarak dizideki ilk öğeyi verir. İlk öğeyi bırakmadan önce kaynağını üreten bir sorgu işleci kullanırsanız, uygulamanız için küçük bir bellek parmak izini saklayacağınızı unutmayın.  
  
[Üst bilgi bilgilerine erişimi olan XML parçalarını akışaC#](./how-to-stream-xml-fragments-with-access-to-header-information.md)alma bölümünde açıklanan tekniği () kullansanız bile, dönüştürülmüş belgeyi içeren bir xml ağacını oluşturmayı denerseniz, bellek kullanımı çok büyük olur.
  
 İki ana yaklaşım vardır. Bir yaklaşım, <xref:System.Xml.Linq.XStreamingElement>ertelenmiş işleme özelliklerini kullanmaktır. Başka bir yaklaşım de <xref:System.Xml.XmlWriter>oluşturmak ve bir <xref:System.Xml.XmlWriter>öğeleri yazmak için [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] yeteneklerini kullanmaktır. Bu konuda her iki yaklaşım da gösterilmektedir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, [üst bilgi bilgilerine (C#) erişimi olan XML parçalarının nasıl akışa alınacağını gösteren](./how-to-stream-xml-fragments-with-access-to-header-information.md)örneği oluşturur.
  
 Bu örnek, çıktının akışı için <xref:System.Xml.Linq.XStreamingElement> ertelenmiş yürütme yeteneklerini kullanır. Bu örnek, küçük bir bellek parmak izini koruyarak çok büyük bir belgeyi dönüştürebilir.  
  
 Özel eksenin (`StreamCustomerItem`) özellikle `Customer`, `Name`ve `Item` öğelerine sahip bir belge beklediği ve bu öğelerin aşağıdaki Source. xml belgesinde düzenlenebilmesini sağlayacak şekilde yazıldığını unutmayın. Ancak, daha güçlü bir uygulama, geçersiz bir belgeyi ayrıştırmaya hazırlanmalıdır.  
  
 Kaynak. xml kaynak belgesi aşağıda verilmiştir:  
  
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
Aşağıdaki örnek, [üst bilgi bilgilerine (C#) erişimi olan XML parçalarının nasıl akışa alınacağını](./how-to-stream-xml-fragments-with-access-to-header-information.md)da örnek olarak oluşturur.
  
 Bu örnek, öğeleri bir <xref:System.Xml.XmlWriter>yazmak için [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] özelliğini kullanır. Bu örnek, küçük bir bellek parmak izini koruyarak çok büyük bir belgeyi dönüştürebilir.  
  
 Özel eksenin (`StreamCustomerItem`) özellikle `Customer`, `Name`ve `Item` öğelerine sahip bir belge beklediği ve bu öğelerin aşağıdaki Source. xml belgesinde düzenlenebilmesini sağlayacak şekilde yazıldığını unutmayın. Ancak daha sağlam bir uygulama, kaynak belgeyi bir XSD ile doğrular ya da geçersiz bir belgeyi ayrıştırmaya hazırlanmalıdır.  
  
 Bu örnek, bu konudaki önceki örnekte olduğu gibi, Source. xml kaynak belgesini kullanır. Aynı zamanda tam olarak aynı çıktıyı da üretir.  
  
 Çıkış XML 'sini akışa almak için <xref:System.Xml.Linq.XStreamingElement> kullanmak bir <xref:System.Xml.XmlWriter>yazmaya göre tercih edilir.  
  
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
  