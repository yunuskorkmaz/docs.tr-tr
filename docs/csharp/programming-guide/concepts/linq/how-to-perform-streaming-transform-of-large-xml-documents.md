---
title: "Nasıl yapılır: akış dönüşümü büyük XML belgelerinin (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 5f16d1f8-5370-4b55-b0c8-e497df163037
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 1f3bc1876097474eae6f329711139a2f3797db97
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-perform-streaming-transform-of-large-xml-documents-c"></a><span data-ttu-id="b0ca1-102">Nasıl yapılır: akış dönüşümü büyük XML belgelerinin (C#)</span><span class="sxs-lookup"><span data-stu-id="b0ca1-102">How to: Perform Streaming Transform of Large XML Documents (C#)</span></span>
<span data-ttu-id="b0ca1-103">Bazen büyük XML dosyalarını dönüştürme ve uygulamanızı yazın, böylece uygulamanın bellek alanını tahmin edilebilir gerekir.</span><span class="sxs-lookup"><span data-stu-id="b0ca1-103">Sometimes you have to transform large XML files, and write your application so that the memory footprint of the application is predictable.</span></span> <span data-ttu-id="b0ca1-104">Bir XML ağaç içeren çok büyük bir XML dosyası doldurmak çalışırsanız, bellek kullanımı dosyasının boyutunu orantılı (diğer bir deyişle, aşırı).</span><span class="sxs-lookup"><span data-stu-id="b0ca1-104">If you try to populate an XML tree with a very large XML file, your memory usage will be proportional to the size of the file (that is, excessive).</span></span> <span data-ttu-id="b0ca1-105">Bu nedenle, bir akış teknik yerine kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="b0ca1-105">Therefore, you should use a streaming technique instead.</span></span>  
  
 <span data-ttu-id="b0ca1-106">Akış teknikleri en iyi kaynak belge yalnızca bir kez işlem gerekir ve belge sırayla öğeleri işleyebilmesi için durumlarda uygulanır.</span><span class="sxs-lookup"><span data-stu-id="b0ca1-106">Streaming techniques are best applied in situations where you need to process the source document only once, and you can process the elements in document order.</span></span> <span data-ttu-id="b0ca1-107">Belirli standart sorgu işleçleri gibi <xref:System.Linq.Enumerable.OrderBy%2A>kendi kaynak yinelemek, tüm verileri toplamak, sıralanmasını ve son olarak dizinin ilk öğesi verim.</span><span class="sxs-lookup"><span data-stu-id="b0ca1-107">Certain standard query operators, such as <xref:System.Linq.Enumerable.OrderBy%2A>, iterate their source, collect all of the data, sort it, and then finally yield the first item in the sequence.</span></span> <span data-ttu-id="b0ca1-108">İlk öğe sağlayan önce kaynağı gerçeğe bir sorgu işleci kullanırsanız, küçük bellek alanını'ı, uygulamanız için bulamayacaktır unutmayın.</span><span class="sxs-lookup"><span data-stu-id="b0ca1-108">Note that if you use a query operator that materializes its source before yielding the first item, you will not retain a small memory footprint for your application.</span></span>  
  
 <span data-ttu-id="b0ca1-109">Açıklanan tekniği kullansanız bile [nasıl yapılır: akışı XML parçaları üst bilgileri (C#) erişimi](../../../../csharp/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md), bellek kullanımı çok olacaktır dönüştürülmüş belgeyi içeren bir XML ağacı derlemek çalışırsanız.</span><span class="sxs-lookup"><span data-stu-id="b0ca1-109">Even if you use the technique described in [How to: Stream XML Fragments with Access to Header Information (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md), if you try to assemble an XML tree that contains the transformed document, memory usage will be too great.</span></span>  
  
 <span data-ttu-id="b0ca1-110">İki ana yaklaşım vardır.</span><span class="sxs-lookup"><span data-stu-id="b0ca1-110">There are two main approaches.</span></span> <span data-ttu-id="b0ca1-111">Bir yaklaşım ise ertelenmiş işleme özelliklerini kullanmak için <xref:System.Xml.Linq.XStreamingElement>.</span><span class="sxs-lookup"><span data-stu-id="b0ca1-111">One approach is to use the deferred processing characteristics of <xref:System.Xml.Linq.XStreamingElement>.</span></span> <span data-ttu-id="b0ca1-112">Başka bir yaklaşım oluşturmaktır bir <xref:System.Xml.XmlWriter>ve özelliklerini kullanma [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] öğelerine yazmak için bir <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="b0ca1-112">Another approach is to create an <xref:System.Xml.XmlWriter>, and use the capabilities of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] to write elements to an <xref:System.Xml.XmlWriter>.</span></span> <span data-ttu-id="b0ca1-113">Bu konu, her iki yaklaşımın gösterir.</span><span class="sxs-lookup"><span data-stu-id="b0ca1-113">This topic demonstrates both approaches.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b0ca1-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="b0ca1-114">Example</span></span>  
 <span data-ttu-id="b0ca1-115">Aşağıdaki örnek örnekte inşa edilmiştir [nasıl yapılır: akışı XML parçaları üst bilgileri (C#) erişimi](../../../../csharp/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md).</span><span class="sxs-lookup"><span data-stu-id="b0ca1-115">The following example builds on the example in [How to: Stream XML Fragments with Access to Header Information (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md).</span></span>  
  
 <span data-ttu-id="b0ca1-116">Bu örnek, ertelenmiş yürütme yeteneklerini kullanır <xref:System.Xml.Linq.XStreamingElement> çıkış akışı.</span><span class="sxs-lookup"><span data-stu-id="b0ca1-116">This example uses the deferred execution capabilities of <xref:System.Xml.Linq.XStreamingElement> to stream the output.</span></span> <span data-ttu-id="b0ca1-117">Bu örnek, bir küçük bellek alanını korurken çok büyük bir belge dönüştürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b0ca1-117">This example can transform a very large document while maintaining a small memory footprint.</span></span>  
  
 <span data-ttu-id="b0ca1-118">Unutmayın özel eksen (`StreamCustomerItem`) bir belge bekliyor böylece özel olarak yazılmış olan `Customer`, `Name`, ve `Item` öğeleri ve bu öğeleri aşağıdaki Source.xml belgeyi olduğu gibi düzenlenmiş.</span><span class="sxs-lookup"><span data-stu-id="b0ca1-118">Note that the custom axis (`StreamCustomerItem`) is specifically written so that it expects a document that has `Customer`, `Name`, and `Item` elements, and that those elements will be arranged as in the following Source.xml document.</span></span> <span data-ttu-id="b0ca1-119">Geçersiz bir belge ayrıştırılacak ancak, daha sağlam bir uygulama hazırlanması.</span><span class="sxs-lookup"><span data-stu-id="b0ca1-119">A more robust implementation, however, would be prepared to parse an invalid document.</span></span>  
  
 <span data-ttu-id="b0ca1-120">Kaynak belge Source.xml verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="b0ca1-120">The following is the source document, Source.xml:</span></span>  
  
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
  
 <span data-ttu-id="b0ca1-121">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="b0ca1-121">This code produces the following output:</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="b0ca1-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="b0ca1-122">Example</span></span>  
 <span data-ttu-id="b0ca1-123">Aşağıdaki örnekte de örnekte inşa edilmiştir [nasıl yapılır: akışı XML parçaları üst bilgileri (C#) erişimi](../../../../csharp/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md).</span><span class="sxs-lookup"><span data-stu-id="b0ca1-123">The following example also builds on the example in [How to: Stream XML Fragments with Access to Header Information (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md).</span></span>  
  
 <span data-ttu-id="b0ca1-124">Bu örnek yeteneğini kullanır [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] öğelerine yazmak için bir <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="b0ca1-124">This example uses the capability of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] to write elements to an <xref:System.Xml.XmlWriter>.</span></span> <span data-ttu-id="b0ca1-125">Bu örnek, bir küçük bellek alanını korurken çok büyük bir belge dönüştürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b0ca1-125">This example can transform a very large document while maintaining a small memory footprint.</span></span>  
  
 <span data-ttu-id="b0ca1-126">Unutmayın özel eksen (`StreamCustomerItem`) bir belge bekliyor böylece özel olarak yazılmış olan `Customer`, `Name`, ve `Item` öğeleri ve bu öğeleri aşağıdaki Source.xml belgeyi olduğu gibi düzenlenmiş.</span><span class="sxs-lookup"><span data-stu-id="b0ca1-126">Note that the custom axis (`StreamCustomerItem`) is specifically written so that it expects a document that has `Customer`, `Name`, and `Item` elements, and that those elements will be arranged as in the following Source.xml document.</span></span> <span data-ttu-id="b0ca1-127">Daha sağlam bir uygulama, ancak bir XSD kaynak belge ya da doğrulamak veya geçersiz bir belge ayrıştırmak hazır olacaktır.</span><span class="sxs-lookup"><span data-stu-id="b0ca1-127">A more robust implementation, however, would either validate the source document with an XSD, or would be prepared to parse an invalid document.</span></span>  
  
 <span data-ttu-id="b0ca1-128">Bu örnek aynı kaynak belge Source.xml, bu konunun önceki örnek olarak kullanır.</span><span class="sxs-lookup"><span data-stu-id="b0ca1-128">This example uses the same source document, Source.xml, as the previous example in this topic.</span></span> <span data-ttu-id="b0ca1-129">Ayrıca, tam olarak aynı çıkışı üretir.</span><span class="sxs-lookup"><span data-stu-id="b0ca1-129">It also produces exactly the same output.</span></span>  
  
 <span data-ttu-id="b0ca1-130">Kullanarak <xref:System.Xml.Linq.XStreamingElement> XML çıkış akış yazma üzerinden tercih edilir bir <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="b0ca1-130">Using <xref:System.Xml.Linq.XStreamingElement> for streaming the output XML is preferred over writing to an <xref:System.Xml.XmlWriter>.</span></span>  
  
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
  
 <span data-ttu-id="b0ca1-131">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="b0ca1-131">This code produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b0ca1-132">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b0ca1-132">See Also</span></span>  
 [<span data-ttu-id="b0ca1-133">Gelişmiş LINQ-XML programlama (C#)</span><span class="sxs-lookup"><span data-stu-id="b0ca1-133">Advanced LINQ to XML Programming (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
