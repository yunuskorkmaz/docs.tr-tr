---
title: 'Nasıl yapılır: akış parçalarını gelen XmlReader (C#)'
ms.date: 07/20/2015
ms.assetid: 4a8f0e45-768a-42e2-bc5f-68bdf0e0a726
ms.openlocfilehash: 8e2baed3ca32ea4273993fe5bed43fef768204ce
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33321070"
---
# <a name="how-to-stream-xml-fragments-from-an-xmlreader-c"></a><span data-ttu-id="1a90a-102">Nasıl yapılır: akış parçalarını gelen XmlReader (C#)</span><span class="sxs-lookup"><span data-stu-id="1a90a-102">How to: Stream XML Fragments from an XmlReader (C#)</span></span>
<span data-ttu-id="1a90a-103">Büyük XML dosyalarını işlemek varsa, XML ağacın tamamı belleğe yüklemek için uygun olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="1a90a-103">When you have to process large XML files, it might not be feasible to load the whole XML tree into memory.</span></span> <span data-ttu-id="1a90a-104">Bu konuda kullanarak parçaları akışı gösterilmektedir bir <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="1a90a-104">This topic shows how to stream fragments using an <xref:System.Xml.XmlReader>.</span></span>  
  
 <span data-ttu-id="1a90a-105">Kullanmak için en etkili yollarından biri, bir <xref:System.Xml.XmlReader> okumak için <xref:System.Xml.Linq.XElement> nesnedir kendi özel eksen yöntemi yazmak için.</span><span class="sxs-lookup"><span data-stu-id="1a90a-105">One of the most effective ways to use an <xref:System.Xml.XmlReader> to read <xref:System.Xml.Linq.XElement> objects is to write your own custom axis method.</span></span> <span data-ttu-id="1a90a-106">Bir eksen yöntemi bir koleksiyon gibi tipik döndürür <xref:System.Collections.Generic.IEnumerable%601> , <xref:System.Xml.Linq.XElement>, bu konuda örnekte gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="1a90a-106">An axis method typically returns a collection such as <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>, as shown in the example in this topic.</span></span> <span data-ttu-id="1a90a-107">Özel eksen yönteminde çağırarak XML parçası oluşturduktan sonra <xref:System.Xml.Linq.XNode.ReadFrom%2A> yöntemi kullanarak koleksiyon döndürmek `yield return`.</span><span class="sxs-lookup"><span data-stu-id="1a90a-107">In the custom axis method, after you create the XML fragment by calling the <xref:System.Xml.Linq.XNode.ReadFrom%2A> method, return the collection using `yield return`.</span></span> <span data-ttu-id="1a90a-108">Bu, özel eksen yönteminize ertelenmiş yürütme semantiği sağlar.</span><span class="sxs-lookup"><span data-stu-id="1a90a-108">This provides deferred execution semantics to your custom axis method.</span></span>  
  
 <span data-ttu-id="1a90a-109">Bir XML ağacından oluşturduğunuzda bir <xref:System.Xml.XmlReader> nesnesi <xref:System.Xml.XmlReader> bir öğede konumlandırılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="1a90a-109">When you create an XML tree from an <xref:System.Xml.XmlReader> object, the <xref:System.Xml.XmlReader> must be positioned on an element.</span></span> <span data-ttu-id="1a90a-110"><xref:System.Xml.Linq.XNode.ReadFrom%2A> Yöntemi öğenin kapatma etiketi okudu kadar döndürmez.</span><span class="sxs-lookup"><span data-stu-id="1a90a-110">The <xref:System.Xml.Linq.XNode.ReadFrom%2A> method does not return until it has read the close tag of the element.</span></span>  
  
 <span data-ttu-id="1a90a-111">Kısmi bir ağaç oluşturmak istiyorsanız, örneği oluşturmak bir <xref:System.Xml.XmlReader>, dönüştürmek istediğiniz düğüme okuyucu getirin bir <xref:System.Xml.Linq.XElement> ağacı ve ardından oluşturun <xref:System.Xml.Linq.XElement> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="1a90a-111">If you want to create a partial tree, you can instantiate an <xref:System.Xml.XmlReader>, position the reader on the node that you want to convert to an <xref:System.Xml.Linq.XElement> tree, and then create the <xref:System.Xml.Linq.XElement> object.</span></span>  
  
 <span data-ttu-id="1a90a-112">Konu [nasıl yapılır: akışı XML parçaları üst bilgileri (C#) erişimi](../../../../csharp/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md) bilgi ve daha karmaşık bir belge akış konusunda bir örnek içerir.</span><span class="sxs-lookup"><span data-stu-id="1a90a-112">The topic [How to: Stream XML Fragments with Access to Header Information (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md) contains information and an example on how to stream a more complex document.</span></span>  
  
 <span data-ttu-id="1a90a-113">Konu [nasıl yapılır: gerçekleştirmek akış dönüştürme, büyük XML belgeleri (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-perform-streaming-transform-of-large-xml-documents.md) küçük bellek alanını korurken son derece büyük XML belgelerini dönüştürmek için LINQ-XML kullanarak bir örnek içerir.</span><span class="sxs-lookup"><span data-stu-id="1a90a-113">The topic [How to: Perform Streaming Transform of Large XML Documents (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-perform-streaming-transform-of-large-xml-documents.md) contains an example of using LINQ to XML to transform extremely large XML documents while maintaining a small memory footprint.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1a90a-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="1a90a-114">Example</span></span>  
 <span data-ttu-id="1a90a-115">Bu örnek, bir özel eksen yöntemi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="1a90a-115">This example creates a custom axis method.</span></span> <span data-ttu-id="1a90a-116">Kullanarak sorgulama yapabilirsiniz bir [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgu.</span><span class="sxs-lookup"><span data-stu-id="1a90a-116">You can query it by using a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query.</span></span> <span data-ttu-id="1a90a-117">Özel eksen yöntemi `StreamRootChildDoc`, özellikle yinelenen olan bir belgeyi okumak için tasarlanmış bir yöntemle `Child` öğesi.</span><span class="sxs-lookup"><span data-stu-id="1a90a-117">The custom axis method, `StreamRootChildDoc`, is a method that is designed specifically to read a document that has a repeating `Child` element.</span></span>  
  
```csharp  
static IEnumerable<XElement> StreamRootChildDoc(StringReader stringReader)  
{  
    using (XmlReader reader = XmlReader.Create(stringReader))  
    {  
        reader.MoveToContent();  
        // Parse the file and display each of the nodes.  
        while (reader.Read())  
        {  
            switch (reader.NodeType)  
            {  
                case XmlNodeType.Element:  
                    if (reader.Name == "Child") {  
                        XElement el = XElement.ReadFrom(reader) as XElement;  
                        if (el != null)  
                            yield return el;  
                    }  
                    break;  
            }  
        }  
    }  
}  
  
static void Main(string[] args)  
{  
    string markup = @"<Root>  
      <Child Key=""01"">  
        <GrandChild>aaa</GrandChild>  
      </Child>  
      <Child Key=""02"">  
        <GrandChild>bbb</GrandChild>  
      </Child>  
      <Child Key=""03"">  
        <GrandChild>ccc</GrandChild>  
      </Child>  
    </Root>";  
  
    IEnumerable<string> grandChildData =  
        from el in StreamRootChildDoc(new StringReader(markup))  
        where (int)el.Attribute("Key") > 1  
        select (string)el.Element("GrandChild");  
  
    foreach (string str in grandChildData) {  
        Console.WriteLine(str);  
    }  
}  
```  
  
 <span data-ttu-id="1a90a-118">Bu örnek şu çıkışı üretir:</span><span class="sxs-lookup"><span data-stu-id="1a90a-118">This example produces the following output:</span></span>  
  
```  
bbb  
ccc  
```  
  
 <span data-ttu-id="1a90a-119">Bu örnekte, kaynak belge çok küçük.</span><span class="sxs-lookup"><span data-stu-id="1a90a-119">In this example, the source document is very small.</span></span> <span data-ttu-id="1a90a-120">Ancak, milyonlarca olsa bile `Child` öğeleri, bu örnekte küçük bellek alanını hala sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="1a90a-120">However, even if there were millions of `Child` elements, this example would still have a small memory footprint.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a90a-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1a90a-121">See Also</span></span>  
 [<span data-ttu-id="1a90a-122">XML Ayrıştırma (C#)</span><span class="sxs-lookup"><span data-stu-id="1a90a-122">Parsing XML (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/parsing-xml.md)
