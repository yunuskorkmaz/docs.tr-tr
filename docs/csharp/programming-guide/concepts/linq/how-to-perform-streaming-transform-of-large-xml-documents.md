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
# <a name="how-to-perform-streaming-transform-of-large-xml-documents-c"></a><span data-ttu-id="0f718-102">Büyük XML belgelerinin akış dönüşümü nasıl yapılır (C#)</span><span class="sxs-lookup"><span data-stu-id="0f718-102">How to perform streaming transform of large XML documents (C#)</span></span>
<span data-ttu-id="0f718-103">Bazen büyük XML dosyalarını dönüştürmeniz ve uygulamanın bellek ayak izinin öngörülebilir olması için uygulamanızı yazmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="0f718-103">Sometimes you have to transform large XML files, and write your application so that the memory footprint of the application is predictable.</span></span> <span data-ttu-id="0f718-104">Bir XML ağacını çok büyük bir XML dosyasıyla doldurmaya çalışırsanız, bellek kullanımınız dosyanın boyutuyla orantılı olacaktır (diğer bir şekilde aşırı).</span><span class="sxs-lookup"><span data-stu-id="0f718-104">If you try to populate an XML tree with a very large XML file, your memory usage will be proportional to the size of the file (that is, excessive).</span></span> <span data-ttu-id="0f718-105">Bu nedenle, bunun yerine bir akış tekniği kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="0f718-105">Therefore, you should use a streaming technique instead.</span></span>  
  
 <span data-ttu-id="0f718-106">Akış teknikleri en iyi kaynak belgeyi yalnızca bir kez işlemeniz gereken durumlarda uygulanır ve öğeleri belge sırasına göre işleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0f718-106">Streaming techniques are best applied in situations where you need to process the source document only once, and you can process the elements in document order.</span></span> <span data-ttu-id="0f718-107">Kaynaklarını yineleyin, <xref:System.Linq.Enumerable.OrderBy%2A>tüm verileri toplar, sıralar ve ardından son olarak dizideki ilk öğeyi verir.</span><span class="sxs-lookup"><span data-stu-id="0f718-107">Certain standard query operators, such as <xref:System.Linq.Enumerable.OrderBy%2A>, iterate their source, collect all of the data, sort it, and then finally yield the first item in the sequence.</span></span> <span data-ttu-id="0f718-108">İlk öğeyi vermeden önce kaynağını somutlaştıran bir sorgu işleci kullanırsanız, uygulamanız için küçük bir bellek ayak izini saklamayacağınızı unutmayın.</span><span class="sxs-lookup"><span data-stu-id="0f718-108">Note that if you use a query operator that materializes its source before yielding the first item, you will not retain a small memory footprint for your application.</span></span>  
  
<span data-ttu-id="0f718-109">[Üstbilgi bilgilerine (C#) erişebilen XML parçalarının akışı nda](./how-to-stream-xml-fragments-with-access-to-header-information.md)açıklanan tekniği kullansanız bile, dönüştürülmüş belgeyi içeren bir XML ağacını birleştirmeye çalışırsanız, bellek kullanımı çok büyük olacaktır.</span><span class="sxs-lookup"><span data-stu-id="0f718-109">Even if you use the technique described in [How to stream XML fragments with access to header information (C#)](./how-to-stream-xml-fragments-with-access-to-header-information.md), if you try to assemble an XML tree that contains the transformed document, memory usage will be too great.</span></span>
  
 <span data-ttu-id="0f718-110">İki ana yaklaşım vardır.</span><span class="sxs-lookup"><span data-stu-id="0f718-110">There are two main approaches.</span></span> <span data-ttu-id="0f718-111">Bir yaklaşım ertelenmiş işleme özelliklerini <xref:System.Xml.Linq.XStreamingElement>kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="0f718-111">One approach is to use the deferred processing characteristics of <xref:System.Xml.Linq.XStreamingElement>.</span></span> <span data-ttu-id="0f718-112">Başka bir yaklaşım, <xref:System.Xml.XmlWriter>bir oluşturmak ve [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] bir <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="0f718-112">Another approach is to create an <xref:System.Xml.XmlWriter>, and use the capabilities of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] to write elements to an <xref:System.Xml.XmlWriter>.</span></span> <span data-ttu-id="0f718-113">Bu konu her iki yaklaşımı da gösterir.</span><span class="sxs-lookup"><span data-stu-id="0f718-113">This topic demonstrates both approaches.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0f718-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="0f718-114">Example</span></span>  
 <span data-ttu-id="0f718-115">Aşağıdaki örnek, [üstbilgi bilgilerine (C#) erişebilen XML parçalarının nasıl aktarılabildiğini](./how-to-stream-xml-fragments-with-access-to-header-information.md)örnekte oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0f718-115">The following example builds on the example in [How to stream XML fragments with access to header information (C#)](./how-to-stream-xml-fragments-with-access-to-header-information.md).</span></span>
  
 <span data-ttu-id="0f718-116">Bu örnek, çıktıakışı <xref:System.Xml.Linq.XStreamingElement> için ertelenmiş yürütme yeteneklerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="0f718-116">This example uses the deferred execution capabilities of <xref:System.Xml.Linq.XStreamingElement> to stream the output.</span></span> <span data-ttu-id="0f718-117">Bu örnek, küçük bir bellek ayak izini korurken çok büyük bir belgeyi dönüştürebilir.</span><span class="sxs-lookup"><span data-stu-id="0f718-117">This example can transform a very large document while maintaining a small memory footprint.</span></span>  
  
 <span data-ttu-id="0f718-118">Özel eksenin (`StreamCustomerItem`) özel olarak yazıldığına, böylece `Customer` `Name`, `Item` , ve öğeleri olan bir belge beklediğini ve bu öğelerin aşağıdaki Source.xml belgesinde olduğu gibi düzenleneceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="0f718-118">Note that the custom axis (`StreamCustomerItem`) is specifically written so that it expects a document that has `Customer`, `Name`, and `Item` elements, and that those elements will be arranged as in the following Source.xml document.</span></span> <span data-ttu-id="0f718-119">Ancak daha sağlam bir uygulama, geçersiz bir belgeyi ayrıştırmaya hazır olacak.</span><span class="sxs-lookup"><span data-stu-id="0f718-119">A more robust implementation, however, would be prepared to parse an invalid document.</span></span>  
  
 <span data-ttu-id="0f718-120">Kaynak belge, Source.xml aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="0f718-120">The following is the source document, Source.xml:</span></span>  
  
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
  
 <span data-ttu-id="0f718-121">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="0f718-121">This code produces the following output:</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="0f718-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="0f718-122">Example</span></span>  
<span data-ttu-id="0f718-123">Aşağıdaki örnek, [üstbilgi bilgilerine (C#) erişebilen XML parçalarının nasıl aktarılabildiğini](./how-to-stream-xml-fragments-with-access-to-header-information.md)de örnekte oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0f718-123">The following example also builds on the example in [How to stream XML fragments with access to header information (C#)](./how-to-stream-xml-fragments-with-access-to-header-information.md).</span></span>
  
 <span data-ttu-id="0f718-124">Bu örnek, bir [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <xref:System.Xml.XmlWriter>öğeye öğe yazma özelliğini kullanır.</span><span class="sxs-lookup"><span data-stu-id="0f718-124">This example uses the capability of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] to write elements to an <xref:System.Xml.XmlWriter>.</span></span> <span data-ttu-id="0f718-125">Bu örnek, küçük bir bellek ayak izini korurken çok büyük bir belgeyi dönüştürebilir.</span><span class="sxs-lookup"><span data-stu-id="0f718-125">This example can transform a very large document while maintaining a small memory footprint.</span></span>  
  
 <span data-ttu-id="0f718-126">Özel eksenin (`StreamCustomerItem`) özel olarak yazıldığına, böylece `Customer` `Name`, `Item` , ve öğeleri olan bir belge beklediğini ve bu öğelerin aşağıdaki Source.xml belgesinde olduğu gibi düzenleneceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="0f718-126">Note that the custom axis (`StreamCustomerItem`) is specifically written so that it expects a document that has `Customer`, `Name`, and `Item` elements, and that those elements will be arranged as in the following Source.xml document.</span></span> <span data-ttu-id="0f718-127">Ancak daha sağlam bir uygulama, kaynak belgeyi xsd ile doğrular veya geçersiz bir belgeyi ayrıştırmaya hazır olur.</span><span class="sxs-lookup"><span data-stu-id="0f718-127">A more robust implementation, however, would either validate the source document with an XSD, or would be prepared to parse an invalid document.</span></span>  
  
 <span data-ttu-id="0f718-128">Bu örnek, bu konuda önceki örnek olarak aynı kaynak belge, Source.xml kullanır.</span><span class="sxs-lookup"><span data-stu-id="0f718-128">This example uses the same source document, Source.xml, as the previous example in this topic.</span></span> <span data-ttu-id="0f718-129">Aynı zamanda tam olarak aynı çıktıüretir.</span><span class="sxs-lookup"><span data-stu-id="0f718-129">It also produces exactly the same output.</span></span>  
  
 <span data-ttu-id="0f718-130">Çıkış <xref:System.Xml.Linq.XStreamingElement> xml akışı için kullanarak bir <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="0f718-130">Using <xref:System.Xml.Linq.XStreamingElement> for streaming the output XML is preferred over writing to an <xref:System.Xml.XmlWriter>.</span></span>  
  
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
  
 <span data-ttu-id="0f718-131">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="0f718-131">This code produces the following output:</span></span>  
  
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
  