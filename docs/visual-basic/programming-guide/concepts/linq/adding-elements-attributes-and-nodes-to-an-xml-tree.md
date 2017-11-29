---
title: "Bir XML ağacına (Visual Basic) öğeleri, öznitelikleri ve düğümler ekleme"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e243e694-c987-43aa-8b22-1e33dace582c
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 710397e2a2a200dc5129ed42ca34f25617a071c5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="adding-elements-attributes-and-nodes-to-an-xml-tree-visual-basic"></a><span data-ttu-id="31594-102">Bir XML ağacına (Visual Basic) öğeleri, öznitelikleri ve düğümler ekleme</span><span class="sxs-lookup"><span data-stu-id="31594-102">Adding Elements, Attributes, and Nodes to an XML Tree (Visual Basic)</span></span>
<span data-ttu-id="31594-103">Varolan bir XML ağacına içerik (öğeleri, öznitelikleri, yorumlar, işleme yönergeleri, metin ve CDATA) ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="31594-103">You can add content (elements, attributes, comments, processing instructions, text, and CDATA) to an existing XML tree.</span></span>  
  
## <a name="methods-for-adding-content"></a><span data-ttu-id="31594-104">İçerik ekleme yöntemleri</span><span class="sxs-lookup"><span data-stu-id="31594-104">Methods for Adding Content</span></span>  
 <span data-ttu-id="31594-105">Alt içerik için aşağıdaki yöntemleri ekleyin bir <xref:System.Xml.Linq.XElement> veya bir <xref:System.Xml.Linq.XDocument>:</span><span class="sxs-lookup"><span data-stu-id="31594-105">The following methods add child content to an <xref:System.Xml.Linq.XElement> or an <xref:System.Xml.Linq.XDocument>:</span></span>  
  
|<span data-ttu-id="31594-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="31594-106">Method</span></span>|<span data-ttu-id="31594-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="31594-107">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XContainer.Add%2A>|<span data-ttu-id="31594-108">İçeriği, içerik alt sonuna ekler <xref:System.Xml.Linq.XContainer>.</span><span class="sxs-lookup"><span data-stu-id="31594-108">Adds content at the end of the child content of the <xref:System.Xml.Linq.XContainer>.</span></span>|  
|<xref:System.Xml.Linq.XContainer.AddFirst%2A>|<span data-ttu-id="31594-109">Alt öğe içeriğini başında içeriği ekler <xref:System.Xml.Linq.XContainer>.</span><span class="sxs-lookup"><span data-stu-id="31594-109">Adds content at the beginning of the child content of the <xref:System.Xml.Linq.XContainer>.</span></span>|  
  
 <span data-ttu-id="31594-110">Aşağıdaki yöntemlerden içeriği eş düğümleri olarak eklemek bir <xref:System.Xml.Linq.XNode>.</span><span class="sxs-lookup"><span data-stu-id="31594-110">The following methods add content as sibling nodes of an <xref:System.Xml.Linq.XNode>.</span></span> <span data-ttu-id="31594-111">Eşdüzey içeriğin için eklediğiniz en yaygın düğüm <xref:System.Xml.Linq.XElement>, geçerli eşdüzey içeriği gibi diğer tür düğüm ekleyebilirsiniz, ancak <xref:System.Xml.Linq.XText> veya <xref:System.Xml.Linq.XComment>.</span><span class="sxs-lookup"><span data-stu-id="31594-111">The most common node to which you add sibling content is <xref:System.Xml.Linq.XElement>, although you can add valid sibling content to other types of nodes such as <xref:System.Xml.Linq.XText> or <xref:System.Xml.Linq.XComment>.</span></span>  
  
|<span data-ttu-id="31594-112">Yöntem</span><span class="sxs-lookup"><span data-stu-id="31594-112">Method</span></span>|<span data-ttu-id="31594-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="31594-113">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XNode.AddAfterSelf%2A>|<span data-ttu-id="31594-114">Sonra içerik ekler <xref:System.Xml.Linq.XNode>.</span><span class="sxs-lookup"><span data-stu-id="31594-114">Adds content after the <xref:System.Xml.Linq.XNode>.</span></span>|  
|<xref:System.Xml.Linq.XNode.AddBeforeSelf%2A>|<span data-ttu-id="31594-115">Önce içeriği ekler <xref:System.Xml.Linq.XNode>.</span><span class="sxs-lookup"><span data-stu-id="31594-115">Adds content before the <xref:System.Xml.Linq.XNode>.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="31594-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="31594-116">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="31594-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="31594-117">Description</span></span>  
 <span data-ttu-id="31594-118">Aşağıdaki örnekte, iki XML ağaçları oluşturur ve ağaçları birini değiştirir.</span><span class="sxs-lookup"><span data-stu-id="31594-118">The following example creates two XML trees, and then modifies one of the trees.</span></span>  
  
### <a name="code"></a><span data-ttu-id="31594-119">Kod</span><span class="sxs-lookup"><span data-stu-id="31594-119">Code</span></span>  
  
```vb  
Dim srcTree As XElement = _  
    <Root>  
        <Element1>1</Element1>  
        <Element2>2</Element2>  
        <Element3>3</Element3>  
        <Element4>4</Element4>  
        <Element5>5</Element5>  
    </Root>  
Dim xmlTree As XElement = _  
    <Root>  
        <Child1>1</Child1>  
        <Child2>2</Child2>  
        <Child3>3</Child3>  
        <Child4>4</Child4>  
        <Child5>5</Child5>  
    </Root>  
  
xmlTree.Add(<NewChild>new content</NewChild>)  
xmlTree.Add( _  
    From el In srcTree.Elements() _  
    Where CInt(el) > 3 _  
    Select el)  
  
' Even though Child9 does not exist in srcTree, the following statement  
' will not throw an exception, and nothing will be added to xmlTree.  
xmlTree.Add(srcTree.Element("Child9"))  
Console.WriteLine(xmlTree)  
```  
  
### <a name="comments"></a><span data-ttu-id="31594-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="31594-120">Comments</span></span>  
 <span data-ttu-id="31594-121">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="31594-121">This code produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="31594-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="31594-122">See Also</span></span>  
 [<span data-ttu-id="31594-123">XML ağaçları (LINQ-XML) değiştirme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="31594-123">Modifying XML Trees (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)
