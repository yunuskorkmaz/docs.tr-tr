---
title: Bir XmlReader 'dan XML parçalarını akışa alma (C#)
description: Bir XmlReader 'dan XML parçalarını akışa alma hakkında bilgi edinin. Bu yöntem, büyük XML dosyalarını işlemek için kullanılır.
ms.date: 07/20/2015
ms.assetid: 4a8f0e45-768a-42e2-bc5f-68bdf0e0a726
ms.openlocfilehash: e35322724712816180d48c1957719cf87079aedd
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87301027"
---
# <a name="how-to-stream-xml-fragments-from-an-xmlreader-c"></a><span data-ttu-id="92043-104">Bir XmlReader 'dan XML parçalarını akışa alma (C#)</span><span class="sxs-lookup"><span data-stu-id="92043-104">How to stream XML fragments from an XmlReader (C#)</span></span>

<span data-ttu-id="92043-105">Büyük XML dosyalarını işlemek zorunda olduğunuzda, tüm XML ağacının belleğe yüklenmesi mümkün olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="92043-105">When you have to process large XML files, it might not be feasible to load the whole XML tree into memory.</span></span> <span data-ttu-id="92043-106">Bu konuda, kullanarak parçaların nasıl akışının yapılacağı gösterilmektedir <xref:System.Xml.XmlReader> .</span><span class="sxs-lookup"><span data-stu-id="92043-106">This topic shows how to stream fragments using an <xref:System.Xml.XmlReader>.</span></span>  
  
 <span data-ttu-id="92043-107">Nesneleri okumak için kullanmanın en etkili yöntemlerinden biri <xref:System.Xml.XmlReader> <xref:System.Xml.Linq.XElement> kendi özel eksen yönteminizi yazmaktır.</span><span class="sxs-lookup"><span data-stu-id="92043-107">One of the most effective ways to use an <xref:System.Xml.XmlReader> to read <xref:System.Xml.Linq.XElement> objects is to write your own custom axis method.</span></span> <span data-ttu-id="92043-108">Bir Axis yöntemi <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement> , bu konudaki örnekte gösterildiği gibi genellikle gibi bir koleksiyon döndürür.</span><span class="sxs-lookup"><span data-stu-id="92043-108">An axis method typically returns a collection such as <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>, as shown in the example in this topic.</span></span> <span data-ttu-id="92043-109">Özel eksen yönteminde, yöntemini çağırarak XML parçasını oluşturduktan sonra <xref:System.Xml.Linq.XNode.ReadFrom%2A> , kullanarak koleksiyonu döndürün `yield return` .</span><span class="sxs-lookup"><span data-stu-id="92043-109">In the custom axis method, after you create the XML fragment by calling the <xref:System.Xml.Linq.XNode.ReadFrom%2A> method, return the collection using `yield return`.</span></span> <span data-ttu-id="92043-110">Bu, özel eksen yönteminiz için ertelenmiş yürütme semantiğini sağlar.</span><span class="sxs-lookup"><span data-stu-id="92043-110">This provides deferred execution semantics to your custom axis method.</span></span>  
  
 <span data-ttu-id="92043-111">Nesnesinden bir XML ağacı oluşturduğunuzda, <xref:System.Xml.XmlReader> <xref:System.Xml.XmlReader> öğesinin bir öğe üzerinde konumlandırılmış olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="92043-111">When you create an XML tree from an <xref:System.Xml.XmlReader> object, the <xref:System.Xml.XmlReader> must be positioned on an element.</span></span> <span data-ttu-id="92043-112"><xref:System.Xml.Linq.XNode.ReadFrom%2A>Yöntemi, öğenin kapanış etiketini okuuncaya kadar döndürmez.</span><span class="sxs-lookup"><span data-stu-id="92043-112">The <xref:System.Xml.Linq.XNode.ReadFrom%2A> method does not return until it has read the close tag of the element.</span></span>  
  
 <span data-ttu-id="92043-113">Kısmi bir ağaç oluşturmak isterseniz, bir <xref:System.Xml.XmlReader> ağaca dönüştürmek istediğiniz düğümde okuyucuyu konumlandırabilirsiniz <xref:System.Xml.Linq.XElement> ve sonra nesneyi oluşturabilirsiniz. Bu, bir ağacı oluşturabilir <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="92043-113">If you want to create a partial tree, you can instantiate an <xref:System.Xml.XmlReader>, position the reader on the node that you want to convert to an <xref:System.Xml.Linq.XElement> tree, and then create the <xref:System.Xml.Linq.XElement> object.</span></span>  
  
<span data-ttu-id="92043-114">[Başlık bilgilerine erişimi olan XML parçalarının nasıl akışının yapılacağı konusu (C#)](./how-to-stream-xml-fragments-with-access-to-header-information.md) , daha karmaşık bir belgeyi akışa alma hakkında bilgi ve bir örnek içerir.</span><span class="sxs-lookup"><span data-stu-id="92043-114">The topic [How to stream XML fragments with access to header information (C#)](./how-to-stream-xml-fragments-with-access-to-header-information.md) contains information and an example on how to stream a more complex document.</span></span>
  
 <span data-ttu-id="92043-115">[Büyük XML belgelerinin akış dönüşümünü gerçekleştirme konusu (C#)](./how-to-perform-streaming-transform-of-large-xml-documents.md) , küçük bir bellek parmak izini sağlarken çok büyük XML belgelerini dönüştürmek için LINQ to XML kullanma örneği içerir.</span><span class="sxs-lookup"><span data-stu-id="92043-115">The topic [How to perform streaming transform of large XML documents (C#)](./how-to-perform-streaming-transform-of-large-xml-documents.md) contains an example of using LINQ to XML to transform extremely large XML documents while maintaining a small memory footprint.</span></span>  
  
## <a name="example"></a><span data-ttu-id="92043-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="92043-116">Example</span></span>  
 <span data-ttu-id="92043-117">Bu örnek bir özel eksen yöntemi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="92043-117">This example creates a custom axis method.</span></span> <span data-ttu-id="92043-118">Bir LINQ sorgusu kullanarak bunu sorgulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="92043-118">You can query it by using a LINQ query.</span></span> <span data-ttu-id="92043-119">Özel eksen yöntemi, bir `StreamRootChildDoc` yinelenen öğesi olan bir belgeyi okumak için özel olarak tasarlanan bir yöntemdir `Child` .</span><span class="sxs-lookup"><span data-stu-id="92043-119">The custom axis method, `StreamRootChildDoc`, is a method that is designed specifically to read a document that has a repeating `Child` element.</span></span>  
  
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
  
 <span data-ttu-id="92043-120">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="92043-120">This example produces the following output:</span></span>  
  
```output  
bbb  
ccc  
```  
  
 <span data-ttu-id="92043-121">Bu örnekte, kaynak belge çok küçüktür.</span><span class="sxs-lookup"><span data-stu-id="92043-121">In this example, the source document is very small.</span></span> <span data-ttu-id="92043-122">Ancak milyonlarca öğe olsa bile `Child` , bu örnekte küçük bir bellek ayak izine sahip olmaya devam edersiniz.</span><span class="sxs-lookup"><span data-stu-id="92043-122">However, even if there were millions of `Child` elements, this example would still have a small memory footprint.</span></span>  
