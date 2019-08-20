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
# <a name="how-to-perform-streaming-transform-of-large-xml-documents-c"></a><span data-ttu-id="bc6ea-102">Nasıl yapılır: Büyük XML belgelerinin (C#) akış dönüşümünü gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="bc6ea-102">How to: Perform Streaming Transform of Large XML Documents (C#)</span></span>
<span data-ttu-id="bc6ea-103">Bazen büyük XML dosyalarını dönüştürmeniz ve uygulamanın bellek parmak izin tahmin edilebilir olması için uygulamanızı yazmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="bc6ea-103">Sometimes you have to transform large XML files, and write your application so that the memory footprint of the application is predictable.</span></span> <span data-ttu-id="bc6ea-104">Bir XML ağacını çok büyük bir XML dosyası ile doldurmayı denerseniz, bellek kullanımınız dosyanın boyutuyla (aşırı) orantılı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="bc6ea-104">If you try to populate an XML tree with a very large XML file, your memory usage will be proportional to the size of the file (that is, excessive).</span></span> <span data-ttu-id="bc6ea-105">Bu nedenle, bunun yerine bir akış tekniği kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="bc6ea-105">Therefore, you should use a streaming technique instead.</span></span>  
  
 <span data-ttu-id="bc6ea-106">Akış teknikleri en iyi şekilde, kaynak belgeyi yalnızca bir kez işleyebilmeniz ve öğeleri belge düzeninde işleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bc6ea-106">Streaming techniques are best applied in situations where you need to process the source document only once, and you can process the elements in document order.</span></span> <span data-ttu-id="bc6ea-107">Gibi belirli standart sorgu işleçleri <xref:System.Linq.Enumerable.OrderBy%2A>, kaynaklarını yineleyebilir, tüm verileri toplar, sıralar ve son olarak dizideki ilk öğeyi verir.</span><span class="sxs-lookup"><span data-stu-id="bc6ea-107">Certain standard query operators, such as <xref:System.Linq.Enumerable.OrderBy%2A>, iterate their source, collect all of the data, sort it, and then finally yield the first item in the sequence.</span></span> <span data-ttu-id="bc6ea-108">İlk öğeyi bırakmadan önce kaynağını üreten bir sorgu işleci kullanırsanız, uygulamanız için küçük bir bellek parmak izini saklayacağınızı unutmayın.</span><span class="sxs-lookup"><span data-stu-id="bc6ea-108">Note that if you use a query operator that materializes its source before yielding the first item, you will not retain a small memory footprint for your application.</span></span>  
  
 <span data-ttu-id="bc6ea-109">Şu şekilde açıklanan [tekniği kullanıyor olsanız da: Üst bilgi bilgilerine erişimi olan XML parçaları akışı (C#)](./how-to-stream-xml-fragments-with-access-to-header-information.md), dönüştürülmüş belgeyi içeren bir xml ağacını birleştirmek istiyorsanız, bellek kullanımı çok büyük olur.</span><span class="sxs-lookup"><span data-stu-id="bc6ea-109">Even if you use the technique described in [How to: Stream XML Fragments with Access to Header Information (C#)](./how-to-stream-xml-fragments-with-access-to-header-information.md), if you try to assemble an XML tree that contains the transformed document, memory usage will be too great.</span></span>  
  
 <span data-ttu-id="bc6ea-110">İki ana yaklaşım vardır.</span><span class="sxs-lookup"><span data-stu-id="bc6ea-110">There are two main approaches.</span></span> <span data-ttu-id="bc6ea-111">Bir yaklaşım, ertelenmiş işleme özelliklerini <xref:System.Xml.Linq.XStreamingElement>kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="bc6ea-111">One approach is to use the deferred processing characteristics of <xref:System.Xml.Linq.XStreamingElement>.</span></span> <span data-ttu-id="bc6ea-112">Başka bir yaklaşım ise oluşturmak <xref:System.Xml.XmlWriter>ve ' a öğeleri yazmak [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <xref:System.Xml.XmlWriter>için yeteneklerini kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="bc6ea-112">Another approach is to create an <xref:System.Xml.XmlWriter>, and use the capabilities of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] to write elements to an <xref:System.Xml.XmlWriter>.</span></span> <span data-ttu-id="bc6ea-113">Bu konuda her iki yaklaşım da gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="bc6ea-113">This topic demonstrates both approaches.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bc6ea-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="bc6ea-114">Example</span></span>  
 <span data-ttu-id="bc6ea-115">Aşağıdaki örnek [, nasıl yapılır: Üst bilgi bilgilerine (C#)](./how-to-stream-xml-fragments-with-access-to-header-information.md)erişimi olan XML parçalarını akışa ın.</span><span class="sxs-lookup"><span data-stu-id="bc6ea-115">The following example builds on the example in [How to: Stream XML Fragments with Access to Header Information (C#)](./how-to-stream-xml-fragments-with-access-to-header-information.md).</span></span>  
  
 <span data-ttu-id="bc6ea-116">Bu örnek, çıktıyı akışa <xref:System.Xml.Linq.XStreamingElement> almak için ertelenmiş yürütme yeteneklerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="bc6ea-116">This example uses the deferred execution capabilities of <xref:System.Xml.Linq.XStreamingElement> to stream the output.</span></span> <span data-ttu-id="bc6ea-117">Bu örnek, küçük bir bellek parmak izini koruyarak çok büyük bir belgeyi dönüştürebilir.</span><span class="sxs-lookup"><span data-stu-id="bc6ea-117">This example can transform a very large document while maintaining a small memory footprint.</span></span>  
  
 <span data-ttu-id="bc6ea-118">Özel eksenin (`StreamCustomerItem`) özellikle `Customer`, `Name`, ve `Item` öğelerinin bulunduğu bir belgeyi beklediğinden ve bu öğelerin aşağıdaki Source. xml belgesinde düzenlenebilmesini sağlayacak şekilde yazıldığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="bc6ea-118">Note that the custom axis (`StreamCustomerItem`) is specifically written so that it expects a document that has `Customer`, `Name`, and `Item` elements, and that those elements will be arranged as in the following Source.xml document.</span></span> <span data-ttu-id="bc6ea-119">Ancak, daha güçlü bir uygulama, geçersiz bir belgeyi ayrıştırmaya hazırlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="bc6ea-119">A more robust implementation, however, would be prepared to parse an invalid document.</span></span>  
  
 <span data-ttu-id="bc6ea-120">Kaynak. xml kaynak belgesi aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="bc6ea-120">The following is the source document, Source.xml:</span></span>  
  
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
  
 <span data-ttu-id="bc6ea-121">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="bc6ea-121">This code produces the following output:</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="bc6ea-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="bc6ea-122">Example</span></span>  
 <span data-ttu-id="bc6ea-123">Aşağıdaki örnek ayrıca [nasıl yapılır: Üst bilgi bilgilerine (C#)](./how-to-stream-xml-fragments-with-access-to-header-information.md)erişimi olan XML parçalarını akışa ın.</span><span class="sxs-lookup"><span data-stu-id="bc6ea-123">The following example also builds on the example in [How to: Stream XML Fragments with Access to Header Information (C#)](./how-to-stream-xml-fragments-with-access-to-header-information.md).</span></span>  
  
 <span data-ttu-id="bc6ea-124">Bu örnek, <xref:System.Xml.XmlWriter>öğesine öğeleri yazmak [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] için özelliğini kullanır.</span><span class="sxs-lookup"><span data-stu-id="bc6ea-124">This example uses the capability of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] to write elements to an <xref:System.Xml.XmlWriter>.</span></span> <span data-ttu-id="bc6ea-125">Bu örnek, küçük bir bellek parmak izini koruyarak çok büyük bir belgeyi dönüştürebilir.</span><span class="sxs-lookup"><span data-stu-id="bc6ea-125">This example can transform a very large document while maintaining a small memory footprint.</span></span>  
  
 <span data-ttu-id="bc6ea-126">Özel eksenin (`StreamCustomerItem`) özellikle `Customer`, `Name`, ve `Item` öğelerinin bulunduğu bir belgeyi beklediğinden ve bu öğelerin aşağıdaki Source. xml belgesinde düzenlenebilmesini sağlayacak şekilde yazıldığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="bc6ea-126">Note that the custom axis (`StreamCustomerItem`) is specifically written so that it expects a document that has `Customer`, `Name`, and `Item` elements, and that those elements will be arranged as in the following Source.xml document.</span></span> <span data-ttu-id="bc6ea-127">Ancak daha sağlam bir uygulama, kaynak belgeyi bir XSD ile doğrular ya da geçersiz bir belgeyi ayrıştırmaya hazırlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="bc6ea-127">A more robust implementation, however, would either validate the source document with an XSD, or would be prepared to parse an invalid document.</span></span>  
  
 <span data-ttu-id="bc6ea-128">Bu örnek, bu konudaki önceki örnekte olduğu gibi, Source. xml kaynak belgesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="bc6ea-128">This example uses the same source document, Source.xml, as the previous example in this topic.</span></span> <span data-ttu-id="bc6ea-129">Aynı zamanda tam olarak aynı çıktıyı da üretir.</span><span class="sxs-lookup"><span data-stu-id="bc6ea-129">It also produces exactly the same output.</span></span>  
  
 <span data-ttu-id="bc6ea-130">Akış <xref:System.Xml.Linq.XStreamingElement> XML 'sini akışa almak için kullanmak, bir <xref:System.Xml.XmlWriter>öğesine yazmak yerine tercih edilir.</span><span class="sxs-lookup"><span data-stu-id="bc6ea-130">Using <xref:System.Xml.Linq.XStreamingElement> for streaming the output XML is preferred over writing to an <xref:System.Xml.XmlWriter>.</span></span>  
  
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
  
 <span data-ttu-id="bc6ea-131">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="bc6ea-131">This code produces the following output:</span></span>  
  
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
  