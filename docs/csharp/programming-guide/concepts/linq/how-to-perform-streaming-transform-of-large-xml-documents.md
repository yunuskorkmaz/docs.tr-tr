---
title: 'Nasıl yapılır: Büyük XML belgelerinin (C#) akış dönüşümünü gerçekleştirme'
ms.date: 07/20/2015
ms.assetid: 5f16d1f8-5370-4b55-b0c8-e497df163037
ms.openlocfilehash: 3ddafc0e053a5dc18d024588e9f71081c8d6da14
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69593186"
---
# <a name="how-to-perform-streaming-transform-of-large-xml-documents-c"></a>Nasıl yapılır: Büyük XML belgelerinin (C#) akış dönüşümünü gerçekleştirme
Bazen büyük XML dosyalarını dönüştürmeniz ve uygulamanın bellek parmak izin tahmin edilebilir olması için uygulamanızı yazmanız gerekir. Bir XML ağacını çok büyük bir XML dosyası ile doldurmayı denerseniz, bellek kullanımınız dosyanın boyutuyla (aşırı) orantılı olacaktır. Bu nedenle, bunun yerine bir akış tekniği kullanmanız gerekir.  
  
 Akış teknikleri en iyi şekilde, kaynak belgeyi yalnızca bir kez işleyebilmeniz ve öğeleri belge düzeninde işleyebilirsiniz. Gibi belirli standart sorgu işleçleri <xref:System.Linq.Enumerable.OrderBy%2A>, kaynaklarını yineleyebilir, tüm verileri toplar, sıralar ve son olarak dizideki ilk öğeyi verir. İlk öğeyi bırakmadan önce kaynağını üreten bir sorgu işleci kullanırsanız, uygulamanız için küçük bir bellek parmak izini saklayacağınızı unutmayın.  
  
 Şu şekilde açıklanan [tekniği kullanıyor olsanız da: Üst bilgi bilgilerine erişimi olan XML parçaları akışı (C#)](./how-to-stream-xml-fragments-with-access-to-header-information.md), dönüştürülmüş belgeyi içeren bir xml ağacını birleştirmek istiyorsanız, bellek kullanımı çok büyük olur.  
  
 İki ana yaklaşım vardır. Bir yaklaşım, ertelenmiş işleme özelliklerini <xref:System.Xml.Linq.XStreamingElement>kullanmaktır. Başka bir yaklaşım ise oluşturmak <xref:System.Xml.XmlWriter>ve ' a öğeleri yazmak [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <xref:System.Xml.XmlWriter>için yeteneklerini kullanmaktır. Bu konuda her iki yaklaşım da gösterilmektedir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek [, nasıl yapılır: Üst bilgi bilgilerine (C#)](./how-to-stream-xml-fragments-with-access-to-header-information.md)erişimi olan XML parçalarını akışa ın.  
  
 Bu örnek, çıktıyı akışa <xref:System.Xml.Linq.XStreamingElement> almak için ertelenmiş yürütme yeteneklerini kullanır. Bu örnek, küçük bir bellek parmak izini koruyarak çok büyük bir belgeyi dönüştürebilir.  
  
 Özel eksenin (`StreamCustomerItem`) özellikle `Customer`, `Name`, ve `Item` öğelerinin bulunduğu bir belgeyi beklediğinden ve bu öğelerin aşağıdaki Source. xml belgesinde düzenlenebilmesini sağlayacak şekilde yazıldığını unutmayın. Ancak, daha güçlü bir uygulama, geçersiz bir belgeyi ayrıştırmaya hazırlanmalıdır.  
  
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
 Aşağıdaki örnek ayrıca [nasıl yapılır: Üst bilgi bilgilerine (C#)](./how-to-stream-xml-fragments-with-access-to-header-information.md)erişimi olan XML parçalarını akışa ın.  
  
 Bu örnek, <xref:System.Xml.XmlWriter>öğesine öğeleri yazmak [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] için özelliğini kullanır. Bu örnek, küçük bir bellek parmak izini koruyarak çok büyük bir belgeyi dönüştürebilir.  
  
 Özel eksenin (`StreamCustomerItem`) özellikle `Customer`, `Name`, ve `Item` öğelerinin bulunduğu bir belgeyi beklediğinden ve bu öğelerin aşağıdaki Source. xml belgesinde düzenlenebilmesini sağlayacak şekilde yazıldığını unutmayın. Ancak daha sağlam bir uygulama, kaynak belgeyi bir XSD ile doğrular ya da geçersiz bir belgeyi ayrıştırmaya hazırlanmalıdır.  
  
 Bu örnek, bu konudaki önceki örnekte olduğu gibi, Source. xml kaynak belgesini kullanır. Aynı zamanda tam olarak aynı çıktıyı da üretir.  
  
 Akış <xref:System.Xml.Linq.XStreamingElement> XML 'sini akışa almak için kullanmak, bir <xref:System.Xml.XmlWriter>öğesine yazmak yerine tercih edilir.  
  
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
  