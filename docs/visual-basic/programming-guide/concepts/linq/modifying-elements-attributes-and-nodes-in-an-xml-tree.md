---
title: Öğe, öznitelik ve düğümleri bir XML Tree1 değiştirme
ms.date: 07/20/2015
ms.assetid: 865cf54e-f8ac-4871-863b-a3e6fc61a4b9
ms.openlocfilehash: d548e6f5912437e5c5df27f55fcdb28990e92c8d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58814906"
---
# <a name="modifying-elements-attributes-and-nodes-in-an-xml-tree"></a><span data-ttu-id="5d8c7-102">XML Ağacındaki Öğe, Öznitelik ve Düğümleri Değiştirme</span><span class="sxs-lookup"><span data-stu-id="5d8c7-102">Modifying Elements, Attributes, and Nodes in an XML Tree</span></span>
<span data-ttu-id="5d8c7-103">Bir öğe, alt öğelerini ve özniteliklerini değiştirmek için kullanabileceğiniz özellikler ve yöntemler aşağıdaki tabloda özetlenmiştir.</span><span class="sxs-lookup"><span data-stu-id="5d8c7-103">The following table summarizes the methods and properties that you can use to modify an element, its child elements, or its attributes.</span></span>  
  
 <span data-ttu-id="5d8c7-104">Aşağıdaki yöntemlerden değiştirme bir <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="5d8c7-104">The following methods modify an <xref:System.Xml.Linq.XElement>.</span></span>  
  
|<span data-ttu-id="5d8c7-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="5d8c7-105">Method</span></span>|<span data-ttu-id="5d8c7-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5d8c7-106">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>|<span data-ttu-id="5d8c7-107">Bir öğe ayrıştırılmış XML ile değiştirir.</span><span class="sxs-lookup"><span data-stu-id="5d8c7-107">Replaces an element with parsed XML.</span></span>|  
|<xref:System.Xml.Linq.XElement.RemoveAll%2A?displayProperty=nameWithType>|<span data-ttu-id="5d8c7-108">Bir öğenin tüm içeriğin (alt düğümleri ve öznitelikleri) kaldırır.</span><span class="sxs-lookup"><span data-stu-id="5d8c7-108">Removes all content (child nodes and attributes) of an element.</span></span>|  
|<xref:System.Xml.Linq.XElement.RemoveAttributes%2A?displayProperty=nameWithType>|<span data-ttu-id="5d8c7-109">Bir öğenin öznitelikleri kaldırır.</span><span class="sxs-lookup"><span data-stu-id="5d8c7-109">Removes the attributes of an element.</span></span>|  
|<xref:System.Xml.Linq.XElement.ReplaceAll%2A?displayProperty=nameWithType>|<span data-ttu-id="5d8c7-110">Bir öğenin tüm içeriğin (alt düğümleri ve öznitelikleri) değiştirir.</span><span class="sxs-lookup"><span data-stu-id="5d8c7-110">Replaces all content (child nodes and attributes) of an element.</span></span>|  
|<xref:System.Xml.Linq.XElement.ReplaceAttributes%2A?displayProperty=nameWithType>|<span data-ttu-id="5d8c7-111">Bir öğenin öznitelikleri değiştirir.</span><span class="sxs-lookup"><span data-stu-id="5d8c7-111">Replaces the attributes of an element.</span></span>|  
|<xref:System.Xml.Linq.XElement.SetAttributeValue%2A?displayProperty=nameWithType>|<span data-ttu-id="5d8c7-112">Bir özniteliğin değerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="5d8c7-112">Sets the value of an attribute.</span></span> <span data-ttu-id="5d8c7-113">Öznitelik yoksa oluşturur.</span><span class="sxs-lookup"><span data-stu-id="5d8c7-113">Creates the attribute if it doesn't exist.</span></span> <span data-ttu-id="5d8c7-114">Değer ayarlanmışsa `null`, öznitelik kaldırır.</span><span class="sxs-lookup"><span data-stu-id="5d8c7-114">If the value is set to `null`, removes the attribute.</span></span>|  
|<xref:System.Xml.Linq.XElement.SetElementValue%2A?displayProperty=nameWithType>|<span data-ttu-id="5d8c7-115">Bir alt öğenin değerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="5d8c7-115">Sets the value of a child element.</span></span> <span data-ttu-id="5d8c7-116">Öğe yoksa oluşturur.</span><span class="sxs-lookup"><span data-stu-id="5d8c7-116">Creates the element if it doesn't exist.</span></span> <span data-ttu-id="5d8c7-117">Değer ayarlanmışsa `null`, öğeyi kaldırır.</span><span class="sxs-lookup"><span data-stu-id="5d8c7-117">If the value is set to `null`, removes the element.</span></span>|  
|<xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType>|<span data-ttu-id="5d8c7-118">Bir öğenin içeriğini (alt düğümleri) belirtilen metinle değiştirir.</span><span class="sxs-lookup"><span data-stu-id="5d8c7-118">Replaces the content (child nodes) of an element with the specified text.</span></span>|  
|<xref:System.Xml.Linq.XElement.SetValue%2A?displayProperty=nameWithType>|<span data-ttu-id="5d8c7-119">Bir öğenin değerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="5d8c7-119">Sets the value of an element.</span></span>|  
  
 <span data-ttu-id="5d8c7-120">Aşağıdaki yöntemlerden değiştirme bir <xref:System.Xml.Linq.XAttribute>.</span><span class="sxs-lookup"><span data-stu-id="5d8c7-120">The following methods modify an <xref:System.Xml.Linq.XAttribute>.</span></span>  
  
|<span data-ttu-id="5d8c7-121">Yöntem</span><span class="sxs-lookup"><span data-stu-id="5d8c7-121">Method</span></span>|<span data-ttu-id="5d8c7-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5d8c7-122">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=nameWithType>|<span data-ttu-id="5d8c7-123">Bir özniteliğin değerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="5d8c7-123">Sets the value of an attribute.</span></span>|  
|<xref:System.Xml.Linq.XAttribute.SetValue%2A?displayProperty=nameWithType>|<span data-ttu-id="5d8c7-124">Bir özniteliğin değerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="5d8c7-124">Sets the value of an attribute.</span></span>|  
  
 <span data-ttu-id="5d8c7-125">Aşağıdaki yöntemlerden değiştirme bir <xref:System.Xml.Linq.XNode> (dahil olmak üzere bir <xref:System.Xml.Linq.XElement> veya <xref:System.Xml.Linq.XDocument>).</span><span class="sxs-lookup"><span data-stu-id="5d8c7-125">The following methods modify an <xref:System.Xml.Linq.XNode> (including an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument>).</span></span>  
  
|<span data-ttu-id="5d8c7-126">Yöntem</span><span class="sxs-lookup"><span data-stu-id="5d8c7-126">Method</span></span>|<span data-ttu-id="5d8c7-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5d8c7-127">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XNode.ReplaceWith%2A?displayProperty=nameWithType>|<span data-ttu-id="5d8c7-128">Bir düğüm, yeni içerikle değiştirir.</span><span class="sxs-lookup"><span data-stu-id="5d8c7-128">Replaces a node with new content.</span></span>|  
  
 <span data-ttu-id="5d8c7-129">Aşağıdaki yöntemlerden değiştirme bir <xref:System.Xml.Linq.XContainer> (bir <xref:System.Xml.Linq.XElement> veya <xref:System.Xml.Linq.XDocument>).</span><span class="sxs-lookup"><span data-stu-id="5d8c7-129">The following methods modify an <xref:System.Xml.Linq.XContainer> (an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument>).</span></span>  
  
|<span data-ttu-id="5d8c7-130">Yöntem</span><span class="sxs-lookup"><span data-stu-id="5d8c7-130">Method</span></span>|<span data-ttu-id="5d8c7-131">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5d8c7-131">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XContainer.ReplaceNodes%2A?displayProperty=nameWithType>|<span data-ttu-id="5d8c7-132">Alt düğüm, yeni içerikle değiştirir.</span><span class="sxs-lookup"><span data-stu-id="5d8c7-132">Replaces the children nodes with new content.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5d8c7-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5d8c7-133">See also</span></span>

- [<span data-ttu-id="5d8c7-134">(LINQ to XML) XML ağaçlarını değiştirme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5d8c7-134">Modifying XML Trees (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)
