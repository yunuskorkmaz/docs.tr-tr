---
title: (Visual Basic) XML ağacına öğe, öznitelik ve düğümleri ekleme
ms.date: 07/20/2015
ms.assetid: e243e694-c987-43aa-8b22-1e33dace582c
ms.openlocfilehash: 5b15a3a943425a7443ad0986d8d91973d0090ed3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54669347"
---
# <a name="adding-elements-attributes-and-nodes-to-an-xml-tree-visual-basic"></a><span data-ttu-id="0264e-102">(Visual Basic) XML ağacına öğe, öznitelik ve düğümleri ekleme</span><span class="sxs-lookup"><span data-stu-id="0264e-102">Adding Elements, Attributes, and Nodes to an XML Tree (Visual Basic)</span></span>
<span data-ttu-id="0264e-103">Varolan bir XML ağacına içeriği (öğe, öznitelik, yorumlar, işleme yönergeleri, metin ve CDATA) ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0264e-103">You can add content (elements, attributes, comments, processing instructions, text, and CDATA) to an existing XML tree.</span></span>  
  
## <a name="methods-for-adding-content"></a><span data-ttu-id="0264e-104">İçerik ekleme yöntemleri</span><span class="sxs-lookup"><span data-stu-id="0264e-104">Methods for Adding Content</span></span>  
 <span data-ttu-id="0264e-105">Aşağıdaki yöntemler alt içeriğin bir <xref:System.Xml.Linq.XElement> veya <xref:System.Xml.Linq.XDocument>:</span><span class="sxs-lookup"><span data-stu-id="0264e-105">The following methods add child content to an <xref:System.Xml.Linq.XElement> or an <xref:System.Xml.Linq.XDocument>:</span></span>  
  
|<span data-ttu-id="0264e-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="0264e-106">Method</span></span>|<span data-ttu-id="0264e-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0264e-107">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XContainer.Add%2A>|<span data-ttu-id="0264e-108">İçeriği, içerik alt sonunda ekler <xref:System.Xml.Linq.XContainer>.</span><span class="sxs-lookup"><span data-stu-id="0264e-108">Adds content at the end of the child content of the <xref:System.Xml.Linq.XContainer>.</span></span>|  
|<xref:System.Xml.Linq.XContainer.AddFirst%2A>|<span data-ttu-id="0264e-109">İçeriği, içerik alt başında ekler <xref:System.Xml.Linq.XContainer>.</span><span class="sxs-lookup"><span data-stu-id="0264e-109">Adds content at the beginning of the child content of the <xref:System.Xml.Linq.XContainer>.</span></span>|  
  
 <span data-ttu-id="0264e-110">Aşağıdaki yöntemlerden içerik eşdüzey düğümleri olarak eklemek bir <xref:System.Xml.Linq.XNode>.</span><span class="sxs-lookup"><span data-stu-id="0264e-110">The following methods add content as sibling nodes of an <xref:System.Xml.Linq.XNode>.</span></span> <span data-ttu-id="0264e-111">Eşdüzey içeriği için eklediğiniz en yaygın düğüm <xref:System.Xml.Linq.XElement>, geçerli eşdüzey içeriği gibi diğer düğümleri türlerine ekleyebilirsiniz ancak <xref:System.Xml.Linq.XText> veya <xref:System.Xml.Linq.XComment>.</span><span class="sxs-lookup"><span data-stu-id="0264e-111">The most common node to which you add sibling content is <xref:System.Xml.Linq.XElement>, although you can add valid sibling content to other types of nodes such as <xref:System.Xml.Linq.XText> or <xref:System.Xml.Linq.XComment>.</span></span>  
  
|<span data-ttu-id="0264e-112">Yöntem</span><span class="sxs-lookup"><span data-stu-id="0264e-112">Method</span></span>|<span data-ttu-id="0264e-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0264e-113">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XNode.AddAfterSelf%2A>|<span data-ttu-id="0264e-114">Sonra içerik ekler <xref:System.Xml.Linq.XNode>.</span><span class="sxs-lookup"><span data-stu-id="0264e-114">Adds content after the <xref:System.Xml.Linq.XNode>.</span></span>|  
|<xref:System.Xml.Linq.XNode.AddBeforeSelf%2A>|<span data-ttu-id="0264e-115">Önce içeriği ekler <xref:System.Xml.Linq.XNode>.</span><span class="sxs-lookup"><span data-stu-id="0264e-115">Adds content before the <xref:System.Xml.Linq.XNode>.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="0264e-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="0264e-116">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="0264e-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0264e-117">Description</span></span>  
 <span data-ttu-id="0264e-118">Aşağıdaki örnek, iki XML ağaçlarını oluşturur ve bir ağaçları değiştirir.</span><span class="sxs-lookup"><span data-stu-id="0264e-118">The following example creates two XML trees, and then modifies one of the trees.</span></span>  
  
### <a name="code"></a><span data-ttu-id="0264e-119">Kod</span><span class="sxs-lookup"><span data-stu-id="0264e-119">Code</span></span>  
  
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
  
### <a name="comments"></a><span data-ttu-id="0264e-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0264e-120">Comments</span></span>  
 <span data-ttu-id="0264e-121">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="0264e-121">This code produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0264e-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0264e-122">See also</span></span>
- [<span data-ttu-id="0264e-123">(LINQ to XML) XML ağaçlarını değiştirme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0264e-123">Modifying XML Trees (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)
