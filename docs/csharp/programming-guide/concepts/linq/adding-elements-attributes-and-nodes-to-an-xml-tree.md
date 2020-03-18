---
title: XML Ağacına Öğeler, Öznitelikler ve Düğümler Ekleme (C#)
ms.date: 07/20/2015
ms.assetid: db911e4f-40aa-499a-9500-a9763bb6df56
ms.openlocfilehash: 20d8d9d9c592f5f570d7c94298dcee41763c1f1f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79169581"
---
# <a name="adding-elements-attributes-and-nodes-to-an-xml-tree-c"></a><span data-ttu-id="53cb3-102">XML Ağacına Öğeler, Öznitelikler ve Düğümler Ekleme (C#)</span><span class="sxs-lookup"><span data-stu-id="53cb3-102">Adding Elements, Attributes, and Nodes to an XML Tree (C#)</span></span>
<span data-ttu-id="53cb3-103">Varolan bir XML ağacına içerik (öğeler, öznitelikler, yorumlar, işleme yönergeleri, metin ve CDATA) ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="53cb3-103">You can add content (elements, attributes, comments, processing instructions, text, and CDATA) to an existing XML tree.</span></span>  
  
## <a name="methods-for-adding-content"></a><span data-ttu-id="53cb3-104">İçerik Ekleme Yöntemleri</span><span class="sxs-lookup"><span data-stu-id="53cb3-104">Methods for Adding Content</span></span>  
 <span data-ttu-id="53cb3-105">Aşağıdaki yöntemler, bir veya <xref:System.Xml.Linq.XElement> bir <xref:System.Xml.Linq.XDocument>alt içerik eklemek:</span><span class="sxs-lookup"><span data-stu-id="53cb3-105">The following methods add child content to an <xref:System.Xml.Linq.XElement> or an <xref:System.Xml.Linq.XDocument>:</span></span>  
  
|<span data-ttu-id="53cb3-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="53cb3-106">Method</span></span>|<span data-ttu-id="53cb3-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="53cb3-107">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XContainer.Add%2A>|<span data-ttu-id="53cb3-108">Alt içeriğin sonuna içerik <xref:System.Xml.Linq.XContainer>ekler.</span><span class="sxs-lookup"><span data-stu-id="53cb3-108">Adds content at the end of the child content of the <xref:System.Xml.Linq.XContainer>.</span></span>|  
|<xref:System.Xml.Linq.XContainer.AddFirst%2A>|<span data-ttu-id="53cb3-109">Alt içeriğin başında içerik <xref:System.Xml.Linq.XContainer>ekler.</span><span class="sxs-lookup"><span data-stu-id="53cb3-109">Adds content at the beginning of the child content of the <xref:System.Xml.Linq.XContainer>.</span></span>|  
  
 <span data-ttu-id="53cb3-110">Aşağıdaki yöntemler, bir <xref:System.Xml.Linq.XNode>.</span><span class="sxs-lookup"><span data-stu-id="53cb3-110">The following methods add content as sibling nodes of an <xref:System.Xml.Linq.XNode>.</span></span> <span data-ttu-id="53cb3-111">Kardeş içerik eklediğiniz en yaygın <xref:System.Xml.Linq.XElement>düğüm, geçerli kardeş içeriği eklemekle birlikte diğer düğüm <xref:System.Xml.Linq.XText> türlerine veya <xref:System.Xml.Linq.XComment>.</span><span class="sxs-lookup"><span data-stu-id="53cb3-111">The most common node to which you add sibling content is <xref:System.Xml.Linq.XElement>, although you can add valid sibling content to other types of nodes such as <xref:System.Xml.Linq.XText> or <xref:System.Xml.Linq.XComment>.</span></span>  
  
|<span data-ttu-id="53cb3-112">Yöntem</span><span class="sxs-lookup"><span data-stu-id="53cb3-112">Method</span></span>|<span data-ttu-id="53cb3-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="53cb3-113">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XNode.AddAfterSelf%2A>|<span data-ttu-id="53cb3-114">Sonra içerik <xref:System.Xml.Linq.XNode>ekler.</span><span class="sxs-lookup"><span data-stu-id="53cb3-114">Adds content after the <xref:System.Xml.Linq.XNode>.</span></span>|  
|<xref:System.Xml.Linq.XNode.AddBeforeSelf%2A>|<span data-ttu-id="53cb3-115">Önce içerik <xref:System.Xml.Linq.XNode>ekler.</span><span class="sxs-lookup"><span data-stu-id="53cb3-115">Adds content before the <xref:System.Xml.Linq.XNode>.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="53cb3-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="53cb3-116">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="53cb3-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="53cb3-117">Description</span></span>  
 <span data-ttu-id="53cb3-118">Aşağıdaki örnek, iki XML ağacı oluşturur ve ağaçlardan birini değiştirir.</span><span class="sxs-lookup"><span data-stu-id="53cb3-118">The following example creates two XML trees, and then modifies one of the trees.</span></span>  
  
### <a name="code"></a><span data-ttu-id="53cb3-119">Kod</span><span class="sxs-lookup"><span data-stu-id="53cb3-119">Code</span></span>  
  
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
  
### <a name="comments"></a><span data-ttu-id="53cb3-120">Yorumlar</span><span class="sxs-lookup"><span data-stu-id="53cb3-120">Comments</span></span>  
 <span data-ttu-id="53cb3-121">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="53cb3-121">This code produces the following output:</span></span>  
  
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
  