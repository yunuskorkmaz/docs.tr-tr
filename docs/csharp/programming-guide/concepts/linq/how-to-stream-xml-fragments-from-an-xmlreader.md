---
title: XML'den XML parçaları akışı nasıl yapılır (C#)
ms.date: 07/20/2015
ms.assetid: 4a8f0e45-768a-42e2-bc5f-68bdf0e0a726
ms.openlocfilehash: f7914d33622518f983a685dd2e844a25fd3ca15f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75714648"
---
# <a name="how-to-stream-xml-fragments-from-an-xmlreader-c"></a><span data-ttu-id="a8d5d-102">XML'den XML parçaları akışı nasıl yapılır (C#)</span><span class="sxs-lookup"><span data-stu-id="a8d5d-102">How to stream XML fragments from an XmlReader (C#)</span></span>

<span data-ttu-id="a8d5d-103">Büyük XML dosyalarını işlemek zorunda olduğunuzda, tüm XML ağacını belleğe yüklemek uygun olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="a8d5d-103">When you have to process large XML files, it might not be feasible to load the whole XML tree into memory.</span></span> <span data-ttu-id="a8d5d-104">Bu konu, bir <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="a8d5d-104">This topic shows how to stream fragments using an <xref:System.Xml.XmlReader>.</span></span>  
  
 <span data-ttu-id="a8d5d-105">Nesneleri okumak <xref:System.Xml.XmlReader> <xref:System.Xml.Linq.XElement> için bir kullanmak için en etkili yollarından biri kendi özel eksen yöntemi yazmaktır.</span><span class="sxs-lookup"><span data-stu-id="a8d5d-105">One of the most effective ways to use an <xref:System.Xml.XmlReader> to read <xref:System.Xml.Linq.XElement> objects is to write your own custom axis method.</span></span> <span data-ttu-id="a8d5d-106">Eksen yöntemi genellikle bu konudaki <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement>örnekte gösterildiği gibi bir koleksiyon döndürür.</span><span class="sxs-lookup"><span data-stu-id="a8d5d-106">An axis method typically returns a collection such as <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>, as shown in the example in this topic.</span></span> <span data-ttu-id="a8d5d-107">Özel eksen yönteminde, <xref:System.Xml.Linq.XNode.ReadFrom%2A> yöntemi çağırarak XML parçasını oluşturduktan sonra, koleksiyonu kullanarak döndürün. `yield return`</span><span class="sxs-lookup"><span data-stu-id="a8d5d-107">In the custom axis method, after you create the XML fragment by calling the <xref:System.Xml.Linq.XNode.ReadFrom%2A> method, return the collection using `yield return`.</span></span> <span data-ttu-id="a8d5d-108">Bu, özel eksen yönteminize ertelenmiş yürütme semantikleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="a8d5d-108">This provides deferred execution semantics to your custom axis method.</span></span>  
  
 <span data-ttu-id="a8d5d-109">Bir <xref:System.Xml.XmlReader> nesneden bir XML ağacı <xref:System.Xml.XmlReader> oluşturduğunuzda, bir öğe üzerinde konumlandırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="a8d5d-109">When you create an XML tree from an <xref:System.Xml.XmlReader> object, the <xref:System.Xml.XmlReader> must be positioned on an element.</span></span> <span data-ttu-id="a8d5d-110">Yöntem, <xref:System.Xml.Linq.XNode.ReadFrom%2A> öğenin yakın etiketini okuyana kadar geri dönmez.</span><span class="sxs-lookup"><span data-stu-id="a8d5d-110">The <xref:System.Xml.Linq.XNode.ReadFrom%2A> method does not return until it has read the close tag of the element.</span></span>  
  
 <span data-ttu-id="a8d5d-111">Kısmi bir <xref:System.Xml.XmlReader>ağaç oluşturmak istiyorsanız, okuyucuyu <xref:System.Xml.Linq.XElement> ağaca dönüştürmek istediğiniz düğümüzerinde anında konumlandırAbilir ve nesneyi oluşturabilirsiniz. <xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="a8d5d-111">If you want to create a partial tree, you can instantiate an <xref:System.Xml.XmlReader>, position the reader on the node that you want to convert to an <xref:System.Xml.Linq.XElement> tree, and then create the <xref:System.Xml.Linq.XElement> object.</span></span>  
  
<span data-ttu-id="a8d5d-112">[Üstbilgi bilgilerine (C#) erişebilen XML parçalarının nasıl aktarılabildiğini](./how-to-stream-xml-fragments-with-access-to-header-information.md) konu, bilgi ve daha karmaşık bir belgenin nasıl akışına ilişkin bir örnek içerir.</span><span class="sxs-lookup"><span data-stu-id="a8d5d-112">The topic [How to stream XML fragments with access to header information (C#)](./how-to-stream-xml-fragments-with-access-to-header-information.md) contains information and an example on how to stream a more complex document.</span></span>
  
 <span data-ttu-id="a8d5d-113">Büyük [XML belgelerinin akış dönüşümü (C#) nasıl yapılır](./how-to-perform-streaming-transform-of-large-xml-documents.md) konusu, küçük bir bellek ayak izini korurken son derece büyük XML belgelerini dönüştürmek için LINQ'dan XML'e dönüştürmenin bir örneğini içerir.</span><span class="sxs-lookup"><span data-stu-id="a8d5d-113">The topic [How to perform streaming transform of large XML documents (C#)](./how-to-perform-streaming-transform-of-large-xml-documents.md) contains an example of using LINQ to XML to transform extremely large XML documents while maintaining a small memory footprint.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a8d5d-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="a8d5d-114">Example</span></span>  
 <span data-ttu-id="a8d5d-115">Bu örnek, özel bir eksen yöntemi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a8d5d-115">This example creates a custom axis method.</span></span> <span data-ttu-id="a8d5d-116">Bir LINQ sorgusu kullanarak sorgulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a8d5d-116">You can query it by using a LINQ query.</span></span> <span data-ttu-id="a8d5d-117">Özel eksen yöntemi, `StreamRootChildDoc`yinelenen bir `Child` öğeye sahip bir belgeyi okumak için özel olarak tasarlanmış bir yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="a8d5d-117">The custom axis method, `StreamRootChildDoc`, is a method that is designed specifically to read a document that has a repeating `Child` element.</span></span>  
  
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
  
 <span data-ttu-id="a8d5d-118">Bu örnek, aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="a8d5d-118">This example produces the following output:</span></span>  
  
```output  
bbb  
ccc  
```  
  
 <span data-ttu-id="a8d5d-119">Bu örnekte, kaynak belge çok küçüktür.</span><span class="sxs-lookup"><span data-stu-id="a8d5d-119">In this example, the source document is very small.</span></span> <span data-ttu-id="a8d5d-120">Ancak, milyonlarca `Child` öğe olsa bile, bu örnek hala küçük bir bellek ayak izi olurdu.</span><span class="sxs-lookup"><span data-stu-id="a8d5d-120">However, even if there were millions of `Child` elements, this example would still have a small memory footprint.</span></span>  
