---
title: "Nasıl yapılır: Stream xmlreader'dan XML parçalarının (C#)"
ms.date: 07/20/2015
ms.assetid: 4a8f0e45-768a-42e2-bc5f-68bdf0e0a726
ms.openlocfilehash: 6937a7160c83def3238c8d2fe3e2b83c996396fd
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66484911"
---
# <a name="how-to-stream-xml-fragments-from-an-xmlreader-c"></a><span data-ttu-id="7d28c-102">Nasıl yapılır: Stream xmlreader'dan XML parçalarının (C#)</span><span class="sxs-lookup"><span data-stu-id="7d28c-102">How to: Stream XML Fragments from an XmlReader (C#)</span></span>
<span data-ttu-id="7d28c-103">Büyük XML dosyalarını işlemek varsa, tüm XML ağacının belleğe yüklemek için uygun olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="7d28c-103">When you have to process large XML files, it might not be feasible to load the whole XML tree into memory.</span></span> <span data-ttu-id="7d28c-104">Bu konuda gösterir kullanarak parçalarının akışını yapma hakkında bir <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="7d28c-104">This topic shows how to stream fragments using an <xref:System.Xml.XmlReader>.</span></span>  
  
 <span data-ttu-id="7d28c-105">Kullanmak için en etkili yollarından biri bir <xref:System.Xml.XmlReader> okunacak <xref:System.Xml.Linq.XElement> nesneleri, kendi özel eksen yöntem yazmaktır.</span><span class="sxs-lookup"><span data-stu-id="7d28c-105">One of the most effective ways to use an <xref:System.Xml.XmlReader> to read <xref:System.Xml.Linq.XElement> objects is to write your own custom axis method.</span></span> <span data-ttu-id="7d28c-106">Eksen yöntemi genellikle bir koleksiyonu gibi döndürür <xref:System.Collections.Generic.IEnumerable%601> , <xref:System.Xml.Linq.XElement>, bu konudaki örnekte gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="7d28c-106">An axis method typically returns a collection such as <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>, as shown in the example in this topic.</span></span> <span data-ttu-id="7d28c-107">Özel eksen yöntemi çağırarak XML parçası oluşturduktan sonra <xref:System.Xml.Linq.XNode.ReadFrom%2A> yöntemini kullanarak koleksiyon döndürmek `yield return`.</span><span class="sxs-lookup"><span data-stu-id="7d28c-107">In the custom axis method, after you create the XML fragment by calling the <xref:System.Xml.Linq.XNode.ReadFrom%2A> method, return the collection using `yield return`.</span></span> <span data-ttu-id="7d28c-108">Bu özel eksen yönteminize ertelenmiş yürütme semantiği sağlar.</span><span class="sxs-lookup"><span data-stu-id="7d28c-108">This provides deferred execution semantics to your custom axis method.</span></span>  
  
 <span data-ttu-id="7d28c-109">XML ağacından oluşturduğunuzda bir <xref:System.Xml.XmlReader> nesnesi <xref:System.Xml.XmlReader> bir öğede konumlandırılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7d28c-109">When you create an XML tree from an <xref:System.Xml.XmlReader> object, the <xref:System.Xml.XmlReader> must be positioned on an element.</span></span> <span data-ttu-id="7d28c-110"><xref:System.Xml.Linq.XNode.ReadFrom%2A> Öğenin kapatma etiketi okudu kadar yöntemi döndürmez.</span><span class="sxs-lookup"><span data-stu-id="7d28c-110">The <xref:System.Xml.Linq.XNode.ReadFrom%2A> method does not return until it has read the close tag of the element.</span></span>  
  
 <span data-ttu-id="7d28c-111">Kısmi bir ağaç oluşturmak istiyorsanız, oluşturabileceğiniz bir <xref:System.Xml.XmlReader>, dönüştürmek istediğiniz düğüme okuyucu getirin bir <xref:System.Xml.Linq.XElement> ağaç ve oluşturup <xref:System.Xml.Linq.XElement> nesne.</span><span class="sxs-lookup"><span data-stu-id="7d28c-111">If you want to create a partial tree, you can instantiate an <xref:System.Xml.XmlReader>, position the reader on the node that you want to convert to an <xref:System.Xml.Linq.XElement> tree, and then create the <xref:System.Xml.Linq.XElement> object.</span></span>  
  
 <span data-ttu-id="7d28c-112">Konu [nasıl yapılır: Stream üst bilgilere erişimle XML parçalarının (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md) bilgileri ve daha karmaşık bir belge akışı konusunda bir örnek içerir.</span><span class="sxs-lookup"><span data-stu-id="7d28c-112">The topic [How to: Stream XML Fragments with Access to Header Information (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md) contains information and an example on how to stream a more complex document.</span></span>  
  
 <span data-ttu-id="7d28c-113">Konu [nasıl yapılır: Akış dönüştürme, büyük XML belgelerinin gerçekleştirin (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-perform-streaming-transform-of-large-xml-documents.md) küçük bellek ayak izini sürdürürken son derece büyük XML belgelerini dönüştürmek için LINQ to XML kullanarak bir örnek içerir.</span><span class="sxs-lookup"><span data-stu-id="7d28c-113">The topic [How to: Perform Streaming Transform of Large XML Documents (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-perform-streaming-transform-of-large-xml-documents.md) contains an example of using LINQ to XML to transform extremely large XML documents while maintaining a small memory footprint.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7d28c-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="7d28c-114">Example</span></span>  
 <span data-ttu-id="7d28c-115">Bu örnek bir özel eksen yöntemi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7d28c-115">This example creates a custom axis method.</span></span> <span data-ttu-id="7d28c-116">Kullanarak sorgulayabilirsiniz bir [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgu.</span><span class="sxs-lookup"><span data-stu-id="7d28c-116">You can query it by using a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query.</span></span> <span data-ttu-id="7d28c-117">Özel eksen yöntemi `StreamRootChildDoc`, özellikle yinelenen olan bir belgeyi okumak için tasarlanmış bir yöntem `Child` öğesi.</span><span class="sxs-lookup"><span data-stu-id="7d28c-117">The custom axis method, `StreamRootChildDoc`, is a method that is designed specifically to read a document that has a repeating `Child` element.</span></span>  
  
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
  
 <span data-ttu-id="7d28c-118">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="7d28c-118">This example produces the following output:</span></span>  
  
```  
bbb  
ccc  
```  
  
 <span data-ttu-id="7d28c-119">Bu örnekte, kaynak belge çok küçüktür.</span><span class="sxs-lookup"><span data-stu-id="7d28c-119">In this example, the source document is very small.</span></span> <span data-ttu-id="7d28c-120">Ancak, milyonlarca olsa bile `Child` öğeleri, bu örnekte küçük bellek Ayak izi yine de sahip.</span><span class="sxs-lookup"><span data-stu-id="7d28c-120">However, even if there were millions of `Child` elements, this example would still have a small memory footprint.</span></span>  
  