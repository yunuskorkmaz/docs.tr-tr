---
title: XML ağacına öğe, öznitelik ve düğüm ekleme (C#)
description: Öğeler, öznitelikler, açıklamalar, işleme talimatları ve metin gibi içeriği varolan bir XML ağacına ekleme yöntemleri hakkında bilgi edinin.
ms.date: 07/20/2015
ms.assetid: db911e4f-40aa-499a-9500-a9763bb6df56
ms.openlocfilehash: 78a84401494e2d4280799632fa42dc95574e3e10
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/23/2020
ms.locfileid: "87105551"
---
# <a name="adding-elements-attributes-and-nodes-to-an-xml-tree-c"></a><span data-ttu-id="c12c9-103">XML ağacına öğe, öznitelik ve düğüm ekleme (C#)</span><span class="sxs-lookup"><span data-stu-id="c12c9-103">Adding Elements, Attributes, and Nodes to an XML Tree (C#)</span></span>
<span data-ttu-id="c12c9-104">Mevcut bir XML ağacına içerik (öğe, öznitelik, yorum, işleme yönergeleri, metin ve CDATA) ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c12c9-104">You can add content (elements, attributes, comments, processing instructions, text, and CDATA) to an existing XML tree.</span></span>  
  
## <a name="methods-for-adding-content"></a><span data-ttu-id="c12c9-105">Içerik ekleme yöntemleri</span><span class="sxs-lookup"><span data-stu-id="c12c9-105">Methods for Adding Content</span></span>  
 <span data-ttu-id="c12c9-106">Aşağıdaki yöntemler bir veya öğesine alt içerik ekler <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XDocument> :</span><span class="sxs-lookup"><span data-stu-id="c12c9-106">The following methods add child content to an <xref:System.Xml.Linq.XElement> or an <xref:System.Xml.Linq.XDocument>:</span></span>  
  
|<span data-ttu-id="c12c9-107">Yöntem</span><span class="sxs-lookup"><span data-stu-id="c12c9-107">Method</span></span>|<span data-ttu-id="c12c9-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c12c9-108">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XContainer.Add%2A>|<span data-ttu-id="c12c9-109">Öğesinin alt içeriğinin sonuna içerik ekler <xref:System.Xml.Linq.XContainer> .</span><span class="sxs-lookup"><span data-stu-id="c12c9-109">Adds content at the end of the child content of the <xref:System.Xml.Linq.XContainer>.</span></span>|  
|<xref:System.Xml.Linq.XContainer.AddFirst%2A>|<span data-ttu-id="c12c9-110">Öğesinin alt içeriğinin başlangıcına içerik ekler <xref:System.Xml.Linq.XContainer> .</span><span class="sxs-lookup"><span data-stu-id="c12c9-110">Adds content at the beginning of the child content of the <xref:System.Xml.Linq.XContainer>.</span></span>|  
  
 <span data-ttu-id="c12c9-111">Aşağıdaki yöntemler bir öğesinin eşdüzey düğümleri olarak içerik ekler <xref:System.Xml.Linq.XNode> .</span><span class="sxs-lookup"><span data-stu-id="c12c9-111">The following methods add content as sibling nodes of an <xref:System.Xml.Linq.XNode>.</span></span> <span data-ttu-id="c12c9-112">Eşdüzey içerik eklediğiniz en yaygın düğüm, <xref:System.Xml.Linq.XElement> veya gibi diğer düğüm türlerine geçerli eşdüzey içerik eklemenize olanak sağlar <xref:System.Xml.Linq.XText> <xref:System.Xml.Linq.XComment> .</span><span class="sxs-lookup"><span data-stu-id="c12c9-112">The most common node to which you add sibling content is <xref:System.Xml.Linq.XElement>, although you can add valid sibling content to other types of nodes such as <xref:System.Xml.Linq.XText> or <xref:System.Xml.Linq.XComment>.</span></span>  
  
|<span data-ttu-id="c12c9-113">Yöntem</span><span class="sxs-lookup"><span data-stu-id="c12c9-113">Method</span></span>|<span data-ttu-id="c12c9-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c12c9-114">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XNode.AddAfterSelf%2A>|<span data-ttu-id="c12c9-115">Öğesinden sonra içerik ekler <xref:System.Xml.Linq.XNode> .</span><span class="sxs-lookup"><span data-stu-id="c12c9-115">Adds content after the <xref:System.Xml.Linq.XNode>.</span></span>|  
|<xref:System.Xml.Linq.XNode.AddBeforeSelf%2A>|<span data-ttu-id="c12c9-116">Öğesinden önce içerik ekler <xref:System.Xml.Linq.XNode> .</span><span class="sxs-lookup"><span data-stu-id="c12c9-116">Adds content before the <xref:System.Xml.Linq.XNode>.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="c12c9-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="c12c9-117">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="c12c9-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c12c9-118">Description</span></span>  
 <span data-ttu-id="c12c9-119">Aşağıdaki örnek iki XML ağacı oluşturur ve sonra ağaçlardan birini değiştirir.</span><span class="sxs-lookup"><span data-stu-id="c12c9-119">The following example creates two XML trees, and then modifies one of the trees.</span></span>  
  
### <a name="code"></a><span data-ttu-id="c12c9-120">Kod</span><span class="sxs-lookup"><span data-stu-id="c12c9-120">Code</span></span>  
  
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
  
### <a name="comments"></a><span data-ttu-id="c12c9-121">Yorumlar</span><span class="sxs-lookup"><span data-stu-id="c12c9-121">Comments</span></span>  
 <span data-ttu-id="c12c9-122">Bu kod şu çıkışı oluşturur:</span><span class="sxs-lookup"><span data-stu-id="c12c9-122">This code produces the following output:</span></span>  
  
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
  