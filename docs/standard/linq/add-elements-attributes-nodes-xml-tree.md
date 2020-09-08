---
title: XML ağacına öğe, öznitelik ve düğüm ekleme-LINQ to XML
description: Bir XML ağacına içerik (öğe, öznitelik, açıklama, işleme yönergeleri, metin ve CDATA) eklemeyi öğrenin.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: db911e4f-40aa-499a-9500-a9763bb6df56
ms.openlocfilehash: 5225560a3f3c94dcb7d4c65e66accddcead84b70
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553558"
---
# <a name="add-elements-attributes-and-nodes-to-an-xml-tree-linq-to-xml"></a><span data-ttu-id="a2b8a-103">XML ağacına öğe, öznitelik ve düğüm ekleme (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="a2b8a-103">Add elements, attributes, and nodes to an XML tree (LINQ to XML)</span></span>

<span data-ttu-id="a2b8a-104">Bir XML ağacına içerik (öğeler, öznitelikler, açıklamalar, işleme yönergeleri, metin ve CDATA) ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a2b8a-104">You can add content (elements, attributes, comments, processing instructions, text, and CDATA) to an XML tree.</span></span>

## <a name="methods-for-adding-content"></a><span data-ttu-id="a2b8a-105">Içerik ekleme yöntemleri</span><span class="sxs-lookup"><span data-stu-id="a2b8a-105">Methods for Adding Content</span></span>

<span data-ttu-id="a2b8a-106">Aşağıdaki yöntemler bir veya öğesine alt içerik ekler <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XDocument> :</span><span class="sxs-lookup"><span data-stu-id="a2b8a-106">The following methods add child content to an <xref:System.Xml.Linq.XElement> or an <xref:System.Xml.Linq.XDocument>:</span></span>

|<span data-ttu-id="a2b8a-107">Yöntem</span><span class="sxs-lookup"><span data-stu-id="a2b8a-107">Method</span></span>|<span data-ttu-id="a2b8a-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a2b8a-108">Description</span></span>|
|------------|-----------------|
|<xref:System.Xml.Linq.XContainer.Add%2A>|<span data-ttu-id="a2b8a-109">Öğesinin alt içeriğinin sonuna içerik ekler <xref:System.Xml.Linq.XContainer> .</span><span class="sxs-lookup"><span data-stu-id="a2b8a-109">Adds content at the end of the child content of the <xref:System.Xml.Linq.XContainer>.</span></span>|
|<xref:System.Xml.Linq.XContainer.AddFirst%2A>|<span data-ttu-id="a2b8a-110">Öğesinin alt içeriğinin başlangıcına içerik ekler <xref:System.Xml.Linq.XContainer> .</span><span class="sxs-lookup"><span data-stu-id="a2b8a-110">Adds content at the beginning of the child content of the <xref:System.Xml.Linq.XContainer>.</span></span>|

<span data-ttu-id="a2b8a-111">Aşağıdaki yöntemler bir öğesinin eşdüzey düğümleri olarak içerik ekler <xref:System.Xml.Linq.XNode> .</span><span class="sxs-lookup"><span data-stu-id="a2b8a-111">The following methods add content as sibling nodes of an <xref:System.Xml.Linq.XNode>.</span></span> <span data-ttu-id="a2b8a-112">Eşdüzey içerik eklediğiniz en yaygın düğüm, <xref:System.Xml.Linq.XElement> veya gibi diğer düğüm türlerine geçerli eşdüzey içerik eklemenize olanak sağlar <xref:System.Xml.Linq.XText> <xref:System.Xml.Linq.XComment> .</span><span class="sxs-lookup"><span data-stu-id="a2b8a-112">The most common node to which you add sibling content is <xref:System.Xml.Linq.XElement>, although you can add valid sibling content to other types of nodes such as <xref:System.Xml.Linq.XText> or <xref:System.Xml.Linq.XComment>.</span></span>

|<span data-ttu-id="a2b8a-113">Yöntem</span><span class="sxs-lookup"><span data-stu-id="a2b8a-113">Method</span></span>|<span data-ttu-id="a2b8a-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a2b8a-114">Description</span></span>|
|------------|-----------------|
|<xref:System.Xml.Linq.XNode.AddAfterSelf%2A>|<span data-ttu-id="a2b8a-115">Öğesinden sonra içerik ekler <xref:System.Xml.Linq.XNode> .</span><span class="sxs-lookup"><span data-stu-id="a2b8a-115">Adds content after the <xref:System.Xml.Linq.XNode>.</span></span>|
|<xref:System.Xml.Linq.XNode.AddBeforeSelf%2A>|<span data-ttu-id="a2b8a-116">Öğesinden önce içerik ekler <xref:System.Xml.Linq.XNode> .</span><span class="sxs-lookup"><span data-stu-id="a2b8a-116">Adds content before the <xref:System.Xml.Linq.XNode>.</span></span>|

## <a name="example-create-two-xml-trees-and-modify-one-of-them"></a><span data-ttu-id="a2b8a-117">Örnek: iki XML ağacı oluşturma ve bunlardan birini değiştirme</span><span class="sxs-lookup"><span data-stu-id="a2b8a-117">Example: Create two XML trees and modify one of them</span></span>

<span data-ttu-id="a2b8a-118">Aşağıdaki örnek iki XML ağacı oluşturur ve bunlardan birini değiştirir.</span><span class="sxs-lookup"><span data-stu-id="a2b8a-118">The following example creates two XML trees, and then modifies one of them.</span></span>

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
// Even though Child9 doesn't exist in srcTree, the following statement won't
// throw an exception, and nothing will be added to xmlTree.
xmlTree.Add(srcTree.Element("Child9"));
Console.WriteLine(xmlTree);
```

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

' Even though Child9 doesn't exist in srcTree, the following statement
' won't throw an exception, and nothing will be added to xmlTree.
xmlTree.Add(srcTree.Element("Child9"))
Console.WriteLine(xmlTree)
```

<span data-ttu-id="a2b8a-119">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="a2b8a-119">This example produces the following output:</span></span>

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
