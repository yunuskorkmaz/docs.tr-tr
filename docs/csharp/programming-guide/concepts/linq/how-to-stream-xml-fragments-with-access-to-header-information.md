---
title: 'Nasıl yapılır: Stream üst bilgilere erişimle XML parçalarının (C#)'
ms.date: 07/20/2015
ms.assetid: 7f242770-b0c7-418d-894b-643215e1f8aa
ms.openlocfilehash: a7e590dcc70dcdb4ea7d5681d623c63f194e0d4e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54655575"
---
# <a name="how-to-stream-xml-fragments-with-access-to-header-information-c"></a><span data-ttu-id="60c84-102">Nasıl yapılır: Stream üst bilgilere erişimle XML parçalarının (C#)</span><span class="sxs-lookup"><span data-stu-id="60c84-102">How to: Stream XML Fragments with Access to Header Information (C#)</span></span>
<span data-ttu-id="60c84-103">Bazen büyük XML dosyaları okur ve bellek Ayak izi uygulamanın öngörülebilir böylece uygulamanız yazma gerekir.</span><span class="sxs-lookup"><span data-stu-id="60c84-103">Sometimes you have to read arbitrarily large XML files, and write your application so that the memory footprint of the application is predictable.</span></span> <span data-ttu-id="60c84-104">İle büyük bir XML dosyasını bir XML ağacı doldurma çalışırsanız, bellek kullanım için dosya boyutu orantılı — diğer bir deyişle, aşırı.</span><span class="sxs-lookup"><span data-stu-id="60c84-104">If you attempt to populate an XML tree with a large XML file, your memory usage will be proportional to the size of the file—that is, excessive.</span></span> <span data-ttu-id="60c84-105">Bu nedenle, bir akış teknik yerine kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="60c84-105">Therefore, you should use a streaming technique instead.</span></span>  
  
 <span data-ttu-id="60c84-106">Bir seçenektir kullanarak uygulamanızı yazmak için <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="60c84-106">One option is to write your application using <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="60c84-107">Ancak, kullanmak isteyebilirsiniz [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] XML ağacı sorgulanamıyor.</span><span class="sxs-lookup"><span data-stu-id="60c84-107">However, you might want to use [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] to query the XML tree.</span></span> <span data-ttu-id="60c84-108">Bu durumda, kendi özel eksen yöntemi yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="60c84-108">If this is the case, you can write your own custom axis method.</span></span> <span data-ttu-id="60c84-109">Daha fazla bilgi için [nasıl yapılır: LINQ to XML eksen yöntemi yazma (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-write-a-linq-to-xml-axis-method.md).</span><span class="sxs-lookup"><span data-stu-id="60c84-109">For more information, see [How to: Write a LINQ to XML Axis Method (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-write-a-linq-to-xml-axis-method.md).</span></span>  
  
 <span data-ttu-id="60c84-110">Kendi eksen yöntemi yazma için kullanan küçük bir yöntem yazmaktır. <xref:System.Xml.XmlReader> , olduğu ilgilenen düğümlerinden biri ulaşana dek düğümleri okumak için.</span><span class="sxs-lookup"><span data-stu-id="60c84-110">To write your own axis method, you write a small method that uses the <xref:System.Xml.XmlReader> to read nodes until it reaches one of the nodes in which you are interested.</span></span> <span data-ttu-id="60c84-111">Daha sonra yöntemi çağırır <xref:System.Xml.Linq.XNode.ReadFrom%2A>, hangi okur <xref:System.Xml.XmlReader> ve bir XML parçası başlatır.</span><span class="sxs-lookup"><span data-stu-id="60c84-111">The method then calls <xref:System.Xml.Linq.XNode.ReadFrom%2A>, which reads from the <xref:System.Xml.XmlReader> and instantiates an XML fragment.</span></span> <span data-ttu-id="60c84-112">Ardından her parçayı aracılığıyla ortaya çıkarır `yield return` özel eksen yönteminizi numaralandırma yöntemi.</span><span class="sxs-lookup"><span data-stu-id="60c84-112">It then yields each fragment through `yield return` to the method that is enumerating your custom axis method.</span></span> <span data-ttu-id="60c84-113">Ardından, özel eksen yöntemi LINQ sorguları da yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="60c84-113">You can then write LINQ queries on your custom axis method.</span></span>  
  
 <span data-ttu-id="60c84-114">Akış teknikleri, burada yalnızca bir kez kaynak belge işlemek gereken ve belge sırada öğeleri işleyebilir durumlarda en iyi şekilde uygulanır.</span><span class="sxs-lookup"><span data-stu-id="60c84-114">Streaming techniques are best applied in situations where you need to process the source document only once, and you can process the elements in document order.</span></span> <span data-ttu-id="60c84-115">Belirli standart sorgu işleçleri gibi <xref:System.Linq.Enumerable.OrderBy%2A>kaynağına yineleme, tüm verileri Topla, sıralanmasını ve son sıradaki ilk öğeyi yield.</span><span class="sxs-lookup"><span data-stu-id="60c84-115">Certain standard query operators, such as <xref:System.Linq.Enumerable.OrderBy%2A>, iterate their source, collect all of the data, sort it, and then finally yield the first item in the sequence.</span></span> <span data-ttu-id="60c84-116">İlk öğeyi oluşturan önce kaynağına gerçekleştiren bir sorgu işlecini kullanmak, bir küçük bellek Ayak izi korumaz unutmayın.</span><span class="sxs-lookup"><span data-stu-id="60c84-116">Note that if you use a query operator that materializes its source before yielding the first item, you will not retain a small memory footprint.</span></span>  
  
## <a name="example"></a><span data-ttu-id="60c84-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="60c84-117">Example</span></span>  
 <span data-ttu-id="60c84-118">Bazı durumlarda biraz daha fazla ilgi çekici sorun alır.</span><span class="sxs-lookup"><span data-stu-id="60c84-118">Sometimes the problem gets just a little more interesting.</span></span> <span data-ttu-id="60c84-119">Aşağıdaki XML belgesindeki özel eksen yönteminizi tüketicisinin her öğenin ait olduğu müşterinin adını bilmek de vardır.</span><span class="sxs-lookup"><span data-stu-id="60c84-119">In the following XML document, the consumer of your custom axis method also has to know the name of the customer that each item belongs to.</span></span>  
  
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
  
 <span data-ttu-id="60c84-120">Bu örnek alan için bu üst bilgi bilgileri izlemek, üst bilgi bilgileri kaydedin ve ardından üst bilgi bilgileri hem numaralandırma ayrıntı içeren küçük bir XML ağacı oluşturmak için bir yaklaşımdır.</span><span class="sxs-lookup"><span data-stu-id="60c84-120">The approach that this example takes is to also watch for this header information, save the header information, and then build a small XML tree that contains both the header information and the detail that you are enumerating.</span></span> <span data-ttu-id="60c84-121">Eksen yöntemi, ardından bu yeni, küçük XML ağacı verir.</span><span class="sxs-lookup"><span data-stu-id="60c84-121">The axis method then yields this new, small XML tree.</span></span> <span data-ttu-id="60c84-122">Sorgu, daha sonra ayrıntılı bilgilerin yanı sıra, üst bilgi bilgileri erişimi vardır.</span><span class="sxs-lookup"><span data-stu-id="60c84-122">The query then has access to the header information as well as the detail information.</span></span>  
  
 <span data-ttu-id="60c84-123">Bu yaklaşım, küçük bellek Ayak izi sahiptir.</span><span class="sxs-lookup"><span data-stu-id="60c84-123">This approach has a small memory footprint.</span></span> <span data-ttu-id="60c84-124">Her ayrıntı XML parçası veriyor gibi başvuru için önceki parça tutulur ve çöp toplama için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="60c84-124">As each detail XML fragment is yielded, no references are kept to the previous fragment, and it is available for garbage collection.</span></span> <span data-ttu-id="60c84-125">Bu teknik yığın üzerinde çok kısa süreli nesneleri oluşturur unutmayın.</span><span class="sxs-lookup"><span data-stu-id="60c84-125">Note that this technique creates many short lived objects on the heap.</span></span>  
  
 <span data-ttu-id="60c84-126">Aşağıdaki örnek, uygulamak ve URI tarafından belirtilen dosyaya XML parçalarının akışını bir özel eksen yöntemi kullanmak gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="60c84-126">The following example shows how to implement and use a custom axis method that streams XML fragments from the file specified by the URI.</span></span> <span data-ttu-id="60c84-127">Bu özel eksen özellikle sahip bir belge beklediği gibi yazılır `Customer`, `Name`, ve `Item` öğeleri ve bu öğeleri olduğu gibi yukarıdaki düzenlenmesini, `Source.xml` belge.</span><span class="sxs-lookup"><span data-stu-id="60c84-127">This custom axis is specifically written such that it expects a document that has `Customer`, `Name`, and `Item` elements, and that those elements will be arranged as in the above `Source.xml` document.</span></span> <span data-ttu-id="60c84-128">Bu basitleştirilmiş bir uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="60c84-128">It is a simplistic implementation.</span></span> <span data-ttu-id="60c84-129">Geçersiz bir belge ayrıştırmak için daha sağlam bir uygulama hazır.</span><span class="sxs-lookup"><span data-stu-id="60c84-129">A more robust implementation would be prepared to parse an invalid document.</span></span>  
  
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
    XElement xmlTree = new XElement("Root",  
        from el in StreamCustomerItem("Source.xml")  
        where (int)el.Element("Key") >= 3 && (int)el.Element("Key") <= 7  
        select new XElement("Item",  
            new XElement("Customer", (string)el.Parent.Element("Name")),  
            new XElement(el.Element("Key"))  
        )  
    );  
    Console.WriteLine(xmlTree);  
}  
```  
  
 <span data-ttu-id="60c84-130">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="60c84-130">This code produces the following output:</span></span>  
  
```xml  
<Root>  
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
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="60c84-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="60c84-131">See also</span></span>

- [<span data-ttu-id="60c84-132">Gelişmiş LINQ to XML programlama (C#)</span><span class="sxs-lookup"><span data-stu-id="60c84-132">Advanced LINQ to XML Programming (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
