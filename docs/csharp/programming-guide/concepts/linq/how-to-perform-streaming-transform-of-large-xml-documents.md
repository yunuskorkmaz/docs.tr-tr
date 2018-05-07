---
title: 'Nasıl yapılır: akış dönüşümü büyük XML belgelerinin (C#)'
ms.date: 07/20/2015
ms.assetid: 5f16d1f8-5370-4b55-b0c8-e497df163037
ms.openlocfilehash: 1a12e8c0ae98be37599b05e5d63469336247d915
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-perform-streaming-transform-of-large-xml-documents-c"></a>Nasıl yapılır: akış dönüşümü büyük XML belgelerinin (C#)
Bazen büyük XML dosyalarını dönüştürme ve uygulamanızı yazın, böylece uygulamanın bellek alanını tahmin edilebilir gerekir. Bir XML ağaç içeren çok büyük bir XML dosyası doldurmak çalışırsanız, bellek kullanımı dosyasının boyutunu orantılı (diğer bir deyişle, aşırı). Bu nedenle, bir akış teknik yerine kullanmanız gerekir.  
  
 Akış teknikleri en iyi kaynak belge yalnızca bir kez işlem gerekir ve belge sırayla öğeleri işleyebilmesi için durumlarda uygulanır. Belirli standart sorgu işleçleri gibi <xref:System.Linq.Enumerable.OrderBy%2A>kendi kaynak yinelemek, tüm verileri toplamak, sıralanmasını ve son olarak dizinin ilk öğesi verim. İlk öğe sağlayan önce kaynağı gerçeğe bir sorgu işleci kullanırsanız, küçük bellek alanını'ı, uygulamanız için bulamayacaktır unutmayın.  
  
 Açıklanan tekniği kullansanız bile [nasıl yapılır: akışı XML parçaları üst bilgileri (C#) erişimi](../../../../csharp/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md), bellek kullanımı çok olacaktır dönüştürülmüş belgeyi içeren bir XML ağacı derlemek çalışırsanız.  
  
 İki ana yaklaşım vardır. Bir yaklaşım ise ertelenmiş işleme özelliklerini kullanmak için <xref:System.Xml.Linq.XStreamingElement>. Başka bir yaklaşım oluşturmaktır bir <xref:System.Xml.XmlWriter>ve özelliklerini kullanma [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] öğelerine yazmak için bir <xref:System.Xml.XmlWriter>. Bu konu, her iki yaklaşımın gösterir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek örnekte inşa edilmiştir [nasıl yapılır: akışı XML parçaları üst bilgileri (C#) erişimi](../../../../csharp/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md).  
  
 Bu örnek, ertelenmiş yürütme yeteneklerini kullanır <xref:System.Xml.Linq.XStreamingElement> çıkış akışı. Bu örnek, bir küçük bellek alanını korurken çok büyük bir belge dönüştürebilirsiniz.  
  
 Unutmayın özel eksen (`StreamCustomerItem`) bir belge bekliyor böylece özel olarak yazılmış olan `Customer`, `Name`, ve `Item` öğeleri ve bu öğeleri aşağıdaki Source.xml belgeyi olduğu gibi düzenlenmiş. Geçersiz bir belge ayrıştırılacak ancak, daha sağlam bir uygulama hazırlanması.  
  
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
 Aşağıdaki örnekte de örnekte inşa edilmiştir [nasıl yapılır: akışı XML parçaları üst bilgileri (C#) erişimi](../../../../csharp/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md).  
  
 Bu örnek yeteneğini kullanır [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] öğelerine yazmak için bir <xref:System.Xml.XmlWriter>. Bu örnek, bir küçük bellek alanını korurken çok büyük bir belge dönüştürebilirsiniz.  
  
 Unutmayın özel eksen (`StreamCustomerItem`) bir belge bekliyor böylece özel olarak yazılmış olan `Customer`, `Name`, ve `Item` öğeleri ve bu öğeleri aşağıdaki Source.xml belgeyi olduğu gibi düzenlenmiş. Daha sağlam bir uygulama, ancak bir XSD kaynak belge ya da doğrulamak veya geçersiz bir belge ayrıştırmak hazır olacaktır.  
  
 Bu örnek aynı kaynak belge Source.xml, bu konunun önceki örnek olarak kullanır. Ayrıca, tam olarak aynı çıkışı üretir.  
  
 Kullanarak <xref:System.Xml.Linq.XStreamingElement> XML çıkış akış yazma üzerinden tercih edilir bir <xref:System.Xml.XmlWriter>.  
  
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
 [Gelişmiş LINQ-XML programlama (C#)](../../../../csharp/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
