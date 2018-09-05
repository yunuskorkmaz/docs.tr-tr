---
title: (C#) XML ağacına öğe, öznitelik ve düğümleri ekleme
ms.date: 07/20/2015
ms.assetid: db911e4f-40aa-499a-9500-a9763bb6df56
ms.openlocfilehash: 1ebc300d74f8dbf0ec746a14f19b5cf0c7ffa51b
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43517065"
---
# <a name="adding-elements-attributes-and-nodes-to-an-xml-tree-c"></a><span data-ttu-id="9eef2-102">(C#) XML ağacına öğe, öznitelik ve düğümleri ekleme</span><span class="sxs-lookup"><span data-stu-id="9eef2-102">Adding Elements, Attributes, and Nodes to an XML Tree (C#)</span></span>
<span data-ttu-id="9eef2-103">Varolan bir XML ağacına içeriği (öğe, öznitelik, yorumlar, işleme yönergeleri, metin ve CDATA) ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9eef2-103">You can add content (elements, attributes, comments, processing instructions, text, and CDATA) to an existing XML tree.</span></span>  
  
## <a name="methods-for-adding-content"></a><span data-ttu-id="9eef2-104">İçerik ekleme yöntemleri</span><span class="sxs-lookup"><span data-stu-id="9eef2-104">Methods for Adding Content</span></span>  
 <span data-ttu-id="9eef2-105">Aşağıdaki yöntemler alt içeriğin bir <xref:System.Xml.Linq.XElement> veya <xref:System.Xml.Linq.XDocument>:</span><span class="sxs-lookup"><span data-stu-id="9eef2-105">The following methods add child content to an <xref:System.Xml.Linq.XElement> or an <xref:System.Xml.Linq.XDocument>:</span></span>  
  
|<span data-ttu-id="9eef2-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="9eef2-106">Method</span></span>|<span data-ttu-id="9eef2-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9eef2-107">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XContainer.Add%2A>|<span data-ttu-id="9eef2-108">İçeriği, içerik alt sonunda ekler <xref:System.Xml.Linq.XContainer>.</span><span class="sxs-lookup"><span data-stu-id="9eef2-108">Adds content at the end of the child content of the <xref:System.Xml.Linq.XContainer>.</span></span>|  
|<xref:System.Xml.Linq.XContainer.AddFirst%2A>|<span data-ttu-id="9eef2-109">İçeriği, içerik alt başında ekler <xref:System.Xml.Linq.XContainer>.</span><span class="sxs-lookup"><span data-stu-id="9eef2-109">Adds content at the beginning of the child content of the <xref:System.Xml.Linq.XContainer>.</span></span>|  
  
 <span data-ttu-id="9eef2-110">Aşağıdaki yöntemlerden içerik eşdüzey düğümleri olarak eklemek bir <xref:System.Xml.Linq.XNode>.</span><span class="sxs-lookup"><span data-stu-id="9eef2-110">The following methods add content as sibling nodes of an <xref:System.Xml.Linq.XNode>.</span></span> <span data-ttu-id="9eef2-111">Eşdüzey içeriği için eklediğiniz en yaygın düğüm <xref:System.Xml.Linq.XElement>, geçerli eşdüzey içeriği gibi diğer düğümleri türlerine ekleyebilirsiniz ancak <xref:System.Xml.Linq.XText> veya <xref:System.Xml.Linq.XComment>.</span><span class="sxs-lookup"><span data-stu-id="9eef2-111">The most common node to which you add sibling content is <xref:System.Xml.Linq.XElement>, although you can add valid sibling content to other types of nodes such as <xref:System.Xml.Linq.XText> or <xref:System.Xml.Linq.XComment>.</span></span>  
  
|<span data-ttu-id="9eef2-112">Yöntem</span><span class="sxs-lookup"><span data-stu-id="9eef2-112">Method</span></span>|<span data-ttu-id="9eef2-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9eef2-113">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XNode.AddAfterSelf%2A>|<span data-ttu-id="9eef2-114">Sonra içerik ekler <xref:System.Xml.Linq.XNode>.</span><span class="sxs-lookup"><span data-stu-id="9eef2-114">Adds content after the <xref:System.Xml.Linq.XNode>.</span></span>|  
|<xref:System.Xml.Linq.XNode.AddBeforeSelf%2A>|<span data-ttu-id="9eef2-115">Önce içeriği ekler <xref:System.Xml.Linq.XNode>.</span><span class="sxs-lookup"><span data-stu-id="9eef2-115">Adds content before the <xref:System.Xml.Linq.XNode>.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="9eef2-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="9eef2-116">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="9eef2-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9eef2-117">Description</span></span>  
 <span data-ttu-id="9eef2-118">Aşağıdaki örnek, iki XML ağaçlarını oluşturur ve bir ağaçları değiştirir.</span><span class="sxs-lookup"><span data-stu-id="9eef2-118">The following example creates two XML trees, and then modifies one of the trees.</span></span>  
  
### <a name="code"></a><span data-ttu-id="9eef2-119">Kod</span><span class="sxs-lookup"><span data-stu-id="9eef2-119">Code</span></span>  
  
```csharp  
XElement srcTree = new XElement("Root",   
    new XElement("Element1", 1),  
    new XElement("Element2", 2),  
    new XElement("Element3", 3),  
    new XElement("Element4", 4),  
    new XElement("Element5", 5)  
);  
XElement xmlTree = new XElement("Root",  
    new XElement("Child1", 1),  
    new XElement("Child2", 2),  
    new XElement("Child3", 3),  
    new XElement("Child4", 4),  
    new XElement("Child5", 5)  
);  
xmlTree.Add(new XElement("NewChild", "new content"));  
xmlTree.Add(  
    from el in srcTree.Elements()  
    where (int)el > 3  
    select el  
);  
// Even though Child9 does not exist in srcTree, the following statement will not  
// throw an exception, and nothing will be added to xmlTree.  
xmlTree.Add(srcTree.Element("Child9"));  
Console.WriteLine(xmlTree);  
```  
  
### <a name="comments"></a><span data-ttu-id="9eef2-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9eef2-120">Comments</span></span>  
 <span data-ttu-id="9eef2-121">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="9eef2-121">This code produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child1>1</Child1>  
  <Child2>2</Child2>  
  <Child3>3</Child3>  
  <Child4>4</Child4>  
  <Child5>5</Child5>  
  <NewChild>new content</NewChild>  
  <Element4>4</Element4>  
  <Element5>5</Element5>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="9eef2-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9eef2-122">See Also</span></span>

- [<span data-ttu-id="9eef2-123">(LINQ to XML) XML ağaçlarını değiştirme (C#)</span><span class="sxs-lookup"><span data-stu-id="9eef2-123">Modifying XML Trees (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)
