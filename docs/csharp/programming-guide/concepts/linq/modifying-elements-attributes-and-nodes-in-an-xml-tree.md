---
title: Öğe, öznitelik ve düğümleri bir XML Tree3 değiştirme
ms.date: 07/20/2015
ms.assetid: 0ed22e4e-4c6b-4eb1-b0eb-06685efd8c33
ms.openlocfilehash: 68195133a944f14f83bf6a33903152393205bfce
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54606249"
---
# <a name="modifying-elements-attributes-and-nodes-in-an-xml-tree"></a><span data-ttu-id="0738a-102">Öğe, öznitelik ve düğümleri bir XML ağacı değiştirme</span><span class="sxs-lookup"><span data-stu-id="0738a-102">Modifying Elements, Attributes, and Nodes in an XML Tree</span></span>
<span data-ttu-id="0738a-103">Bir öğe, alt öğelerini ve özniteliklerini değiştirmek için kullanabileceğiniz özellikler ve yöntemler aşağıdaki tabloda özetlenmiştir.</span><span class="sxs-lookup"><span data-stu-id="0738a-103">The following table summarizes the methods and properties that you can use to modify an element, its child elements, or its attributes.</span></span>  
  
 <span data-ttu-id="0738a-104">Aşağıdaki yöntemlerden değiştirme bir <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="0738a-104">The following methods modify an <xref:System.Xml.Linq.XElement>.</span></span>  
  
|<span data-ttu-id="0738a-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="0738a-105">Method</span></span>|<span data-ttu-id="0738a-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0738a-106">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>|<span data-ttu-id="0738a-107">Bir öğe ayrıştırılmış XML ile değiştirir.</span><span class="sxs-lookup"><span data-stu-id="0738a-107">Replaces an element with parsed XML.</span></span>|  
|<xref:System.Xml.Linq.XElement.RemoveAll%2A?displayProperty=nameWithType>|<span data-ttu-id="0738a-108">Bir öğenin tüm içeriğin (alt düğümleri ve öznitelikleri) kaldırır.</span><span class="sxs-lookup"><span data-stu-id="0738a-108">Removes all content (child nodes and attributes) of an element.</span></span>|  
|<xref:System.Xml.Linq.XElement.RemoveAttributes%2A?displayProperty=nameWithType>|<span data-ttu-id="0738a-109">Bir öğenin öznitelikleri kaldırır.</span><span class="sxs-lookup"><span data-stu-id="0738a-109">Removes the attributes of an element.</span></span>|  
|<xref:System.Xml.Linq.XElement.ReplaceAll%2A?displayProperty=nameWithType>|<span data-ttu-id="0738a-110">Bir öğenin tüm içeriğin (alt düğümleri ve öznitelikleri) değiştirir.</span><span class="sxs-lookup"><span data-stu-id="0738a-110">Replaces all content (child nodes and attributes) of an element.</span></span>|  
|<xref:System.Xml.Linq.XElement.ReplaceAttributes%2A?displayProperty=nameWithType>|<span data-ttu-id="0738a-111">Bir öğenin öznitelikleri değiştirir.</span><span class="sxs-lookup"><span data-stu-id="0738a-111">Replaces the attributes of an element.</span></span>|  
|<xref:System.Xml.Linq.XElement.SetAttributeValue%2A?displayProperty=nameWithType>|<span data-ttu-id="0738a-112">Bir özniteliğin değerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="0738a-112">Sets the value of an attribute.</span></span> <span data-ttu-id="0738a-113">Öznitelik yoksa oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0738a-113">Creates the attribute if it doesn't exist.</span></span> <span data-ttu-id="0738a-114">Değer ayarlanmışsa `null`, öznitelik kaldırır.</span><span class="sxs-lookup"><span data-stu-id="0738a-114">If the value is set to `null`, removes the attribute.</span></span>|  
|<xref:System.Xml.Linq.XElement.SetElementValue%2A?displayProperty=nameWithType>|<span data-ttu-id="0738a-115">Bir alt öğenin değerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="0738a-115">Sets the value of a child element.</span></span> <span data-ttu-id="0738a-116">Öğe yoksa oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0738a-116">Creates the element if it doesn't exist.</span></span> <span data-ttu-id="0738a-117">Değer ayarlanmışsa `null`, öğeyi kaldırır.</span><span class="sxs-lookup"><span data-stu-id="0738a-117">If the value is set to `null`, removes the element.</span></span>|  
|<xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType>|<span data-ttu-id="0738a-118">Bir öğenin içeriğini (alt düğümleri) belirtilen metinle değiştirir.</span><span class="sxs-lookup"><span data-stu-id="0738a-118">Replaces the content (child nodes) of an element with the specified text.</span></span>|  
|<xref:System.Xml.Linq.XElement.SetValue%2A?displayProperty=nameWithType>|<span data-ttu-id="0738a-119">Bir öğenin değerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="0738a-119">Sets the value of an element.</span></span>|  
  
 <span data-ttu-id="0738a-120">Aşağıdaki yöntemlerden değiştirme bir <xref:System.Xml.Linq.XAttribute>.</span><span class="sxs-lookup"><span data-stu-id="0738a-120">The following methods modify an <xref:System.Xml.Linq.XAttribute>.</span></span>  
  
|<span data-ttu-id="0738a-121">Yöntem</span><span class="sxs-lookup"><span data-stu-id="0738a-121">Method</span></span>|<span data-ttu-id="0738a-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0738a-122">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=nameWithType>|<span data-ttu-id="0738a-123">Bir özniteliğin değerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="0738a-123">Sets the value of an attribute.</span></span>|  
|<xref:System.Xml.Linq.XAttribute.SetValue%2A?displayProperty=nameWithType>|<span data-ttu-id="0738a-124">Bir özniteliğin değerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="0738a-124">Sets the value of an attribute.</span></span>|  
  
 <span data-ttu-id="0738a-125">Aşağıdaki yöntemlerden değiştirme bir <xref:System.Xml.Linq.XNode> (dahil olmak üzere bir <xref:System.Xml.Linq.XElement> veya <xref:System.Xml.Linq.XDocument>).</span><span class="sxs-lookup"><span data-stu-id="0738a-125">The following methods modify an <xref:System.Xml.Linq.XNode> (including an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument>).</span></span>  
  
|<span data-ttu-id="0738a-126">Yöntem</span><span class="sxs-lookup"><span data-stu-id="0738a-126">Method</span></span>|<span data-ttu-id="0738a-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0738a-127">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XNode.ReplaceWith%2A?displayProperty=nameWithType>|<span data-ttu-id="0738a-128">Bir düğüm, yeni içerikle değiştirir.</span><span class="sxs-lookup"><span data-stu-id="0738a-128">Replaces a node with new content.</span></span>|  
  
 <span data-ttu-id="0738a-129">Aşağıdaki yöntemlerden değiştirme bir <xref:System.Xml.Linq.XContainer> (bir <xref:System.Xml.Linq.XElement> veya <xref:System.Xml.Linq.XDocument>).</span><span class="sxs-lookup"><span data-stu-id="0738a-129">The following methods modify an <xref:System.Xml.Linq.XContainer> (an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument>).</span></span>  
  
|<span data-ttu-id="0738a-130">Yöntem</span><span class="sxs-lookup"><span data-stu-id="0738a-130">Method</span></span>|<span data-ttu-id="0738a-131">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0738a-131">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XContainer.ReplaceNodes%2A?displayProperty=nameWithType>|<span data-ttu-id="0738a-132">Alt düğüm, yeni içerikle değiştirir.</span><span class="sxs-lookup"><span data-stu-id="0738a-132">Replaces the children nodes with new content.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0738a-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0738a-133">See also</span></span>

- [<span data-ttu-id="0738a-134">(LINQ to XML) XML ağaçlarını değiştirme (C#)</span><span class="sxs-lookup"><span data-stu-id="0738a-134">Modifying XML Trees (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)
