---
title: Öğeleri, öznitelikleri ve bir XML Tree3 düğümler değiştirme
ms.date: 07/20/2015
ms.assetid: 0ed22e4e-4c6b-4eb1-b0eb-06685efd8c33
ms.openlocfilehash: a03045c9a4b7b0fb24bbe5c25211b9626cab9185
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33321275"
---
# <a name="modifying-elements-attributes-and-nodes-in-an-xml-tree"></a><span data-ttu-id="2233b-102">Öğeleri, öznitelikleri ve bir XML ağacında düğümlerin değiştirme</span><span class="sxs-lookup"><span data-stu-id="2233b-102">Modifying Elements, Attributes, and Nodes in an XML Tree</span></span>
<span data-ttu-id="2233b-103">Bir öğe, alt öğelerini veya özniteliklerini değiştirmek için kullanabileceğiniz özellikler ve yöntemler aşağıdaki tabloda özetlenmiştir.</span><span class="sxs-lookup"><span data-stu-id="2233b-103">The following table summarizes the methods and properties that you can use to modify an element, its child elements, or its attributes.</span></span>  
  
 <span data-ttu-id="2233b-104">Aşağıdaki yöntemlerden değiştirme bir <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="2233b-104">The following methods modify an <xref:System.Xml.Linq.XElement>.</span></span>  
  
|<span data-ttu-id="2233b-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="2233b-105">Method</span></span>|<span data-ttu-id="2233b-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2233b-106">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>|<span data-ttu-id="2233b-107">Bir öğenin ayrıştırılmış XML ile değiştirir.</span><span class="sxs-lookup"><span data-stu-id="2233b-107">Replaces an element with parsed XML.</span></span>|  
|<xref:System.Xml.Linq.XElement.RemoveAll%2A?displayProperty=nameWithType>|<span data-ttu-id="2233b-108">Bir öğenin tüm içeriğin (alt düğümleri ve öznitelikleri) kaldırır.</span><span class="sxs-lookup"><span data-stu-id="2233b-108">Removes all content (child nodes and attributes) of an element.</span></span>|  
|<xref:System.Xml.Linq.XElement.RemoveAttributes%2A?displayProperty=nameWithType>|<span data-ttu-id="2233b-109">Bir öğenin öznitelikleri kaldırır.</span><span class="sxs-lookup"><span data-stu-id="2233b-109">Removes the attributes of an element.</span></span>|  
|<xref:System.Xml.Linq.XElement.ReplaceAll%2A?displayProperty=nameWithType>|<span data-ttu-id="2233b-110">Bir öğenin tüm içeriğin (alt düğümleri ve öznitelikleri) yerini alır.</span><span class="sxs-lookup"><span data-stu-id="2233b-110">Replaces all content (child nodes and attributes) of an element.</span></span>|  
|<xref:System.Xml.Linq.XElement.ReplaceAttributes%2A?displayProperty=nameWithType>|<span data-ttu-id="2233b-111">Bir öğenin özniteliklerini değiştirir.</span><span class="sxs-lookup"><span data-stu-id="2233b-111">Replaces the attributes of an element.</span></span>|  
|<xref:System.Xml.Linq.XElement.SetAttributeValue%2A?displayProperty=nameWithType>|<span data-ttu-id="2233b-112">Özniteliğin değerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="2233b-112">Sets the value of an attribute.</span></span> <span data-ttu-id="2233b-113">Öznitelik yoksa oluşturur.</span><span class="sxs-lookup"><span data-stu-id="2233b-113">Creates the attribute if it doesn't exist.</span></span> <span data-ttu-id="2233b-114">Değer ayarlanmışsa `null`, öznitelik kaldırır.</span><span class="sxs-lookup"><span data-stu-id="2233b-114">If the value is set to `null`, removes the attribute.</span></span>|  
|<xref:System.Xml.Linq.XElement.SetElementValue%2A?displayProperty=nameWithType>|<span data-ttu-id="2233b-115">Bir alt öğenin değerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="2233b-115">Sets the value of a child element.</span></span> <span data-ttu-id="2233b-116">Yoksa öğesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="2233b-116">Creates the element if it doesn't exist.</span></span> <span data-ttu-id="2233b-117">Değer ayarlanmışsa `null`, öğeyi kaldırır.</span><span class="sxs-lookup"><span data-stu-id="2233b-117">If the value is set to `null`, removes the element.</span></span>|  
|<xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType>|<span data-ttu-id="2233b-118">Bir öğenin içeriğini (alt düğümler) belirtilen metinle değiştirir.</span><span class="sxs-lookup"><span data-stu-id="2233b-118">Replaces the content (child nodes) of an element with the specified text.</span></span>|  
|<xref:System.Xml.Linq.XElement.SetValue%2A?displayProperty=nameWithType>|<span data-ttu-id="2233b-119">Bir öğenin değerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="2233b-119">Sets the value of an element.</span></span>|  
  
 <span data-ttu-id="2233b-120">Aşağıdaki yöntemlerden değiştirme bir <xref:System.Xml.Linq.XAttribute>.</span><span class="sxs-lookup"><span data-stu-id="2233b-120">The following methods modify an <xref:System.Xml.Linq.XAttribute>.</span></span>  
  
|<span data-ttu-id="2233b-121">Yöntem</span><span class="sxs-lookup"><span data-stu-id="2233b-121">Method</span></span>|<span data-ttu-id="2233b-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2233b-122">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=nameWithType>|<span data-ttu-id="2233b-123">Özniteliğin değerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="2233b-123">Sets the value of an attribute.</span></span>|  
|<xref:System.Xml.Linq.XAttribute.SetValue%2A?displayProperty=nameWithType>|<span data-ttu-id="2233b-124">Özniteliğin değerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="2233b-124">Sets the value of an attribute.</span></span>|  
  
 <span data-ttu-id="2233b-125">Aşağıdaki yöntemlerden değiştirme bir <xref:System.Xml.Linq.XNode> (dahil olmak üzere bir <xref:System.Xml.Linq.XElement> veya <xref:System.Xml.Linq.XDocument>).</span><span class="sxs-lookup"><span data-stu-id="2233b-125">The following methods modify an <xref:System.Xml.Linq.XNode> (including an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument>).</span></span>  
  
|<span data-ttu-id="2233b-126">Yöntem</span><span class="sxs-lookup"><span data-stu-id="2233b-126">Method</span></span>|<span data-ttu-id="2233b-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2233b-127">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XNode.ReplaceWith%2A?displayProperty=nameWithType>|<span data-ttu-id="2233b-128">Bir düğüm yeni içerikle değiştirir.</span><span class="sxs-lookup"><span data-stu-id="2233b-128">Replaces a node with new content.</span></span>|  
  
 <span data-ttu-id="2233b-129">Aşağıdaki yöntemlerden değiştirme bir <xref:System.Xml.Linq.XContainer> (bir <xref:System.Xml.Linq.XElement> veya <xref:System.Xml.Linq.XDocument>).</span><span class="sxs-lookup"><span data-stu-id="2233b-129">The following methods modify an <xref:System.Xml.Linq.XContainer> (an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument>).</span></span>  
  
|<span data-ttu-id="2233b-130">Yöntem</span><span class="sxs-lookup"><span data-stu-id="2233b-130">Method</span></span>|<span data-ttu-id="2233b-131">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2233b-131">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XContainer.ReplaceNodes%2A?displayProperty=nameWithType>|<span data-ttu-id="2233b-132">Alt düğümler ile yeni içerik değiştirir.</span><span class="sxs-lookup"><span data-stu-id="2233b-132">Replaces the children nodes with new content.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2233b-133">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2233b-133">See Also</span></span>  
 [<span data-ttu-id="2233b-134">XML ağaçları (LINQ-XML) değiştirme (C#)</span><span class="sxs-lookup"><span data-stu-id="2233b-134">Modifying XML Trees (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)
