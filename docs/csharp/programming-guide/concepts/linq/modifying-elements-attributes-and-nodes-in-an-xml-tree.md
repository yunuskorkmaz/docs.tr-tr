---
title: Öğe, öznitelik ve düğümleri bir XML Tree3 değiştirme
ms.date: 07/20/2015
ms.assetid: 0ed22e4e-4c6b-4eb1-b0eb-06685efd8c33
ms.openlocfilehash: 9567d0c6c5cd4853eeb2a86066cd1a805f20a031
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43777356"
---
# <a name="modifying-elements-attributes-and-nodes-in-an-xml-tree"></a><span data-ttu-id="ab2c0-102">Öğe, öznitelik ve düğümleri bir XML ağacı değiştirme</span><span class="sxs-lookup"><span data-stu-id="ab2c0-102">Modifying Elements, Attributes, and Nodes in an XML Tree</span></span>
<span data-ttu-id="ab2c0-103">Bir öğe, alt öğelerini ve özniteliklerini değiştirmek için kullanabileceğiniz özellikler ve yöntemler aşağıdaki tabloda özetlenmiştir.</span><span class="sxs-lookup"><span data-stu-id="ab2c0-103">The following table summarizes the methods and properties that you can use to modify an element, its child elements, or its attributes.</span></span>  
  
 <span data-ttu-id="ab2c0-104">Aşağıdaki yöntemlerden değiştirme bir <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="ab2c0-104">The following methods modify an <xref:System.Xml.Linq.XElement>.</span></span>  
  
|<span data-ttu-id="ab2c0-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="ab2c0-105">Method</span></span>|<span data-ttu-id="ab2c0-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ab2c0-106">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>|<span data-ttu-id="ab2c0-107">Bir öğe ayrıştırılmış XML ile değiştirir.</span><span class="sxs-lookup"><span data-stu-id="ab2c0-107">Replaces an element with parsed XML.</span></span>|  
|<xref:System.Xml.Linq.XElement.RemoveAll%2A?displayProperty=nameWithType>|<span data-ttu-id="ab2c0-108">Bir öğenin tüm içeriğin (alt düğümleri ve öznitelikleri) kaldırır.</span><span class="sxs-lookup"><span data-stu-id="ab2c0-108">Removes all content (child nodes and attributes) of an element.</span></span>|  
|<xref:System.Xml.Linq.XElement.RemoveAttributes%2A?displayProperty=nameWithType>|<span data-ttu-id="ab2c0-109">Bir öğenin öznitelikleri kaldırır.</span><span class="sxs-lookup"><span data-stu-id="ab2c0-109">Removes the attributes of an element.</span></span>|  
|<xref:System.Xml.Linq.XElement.ReplaceAll%2A?displayProperty=nameWithType>|<span data-ttu-id="ab2c0-110">Bir öğenin tüm içeriğin (alt düğümleri ve öznitelikleri) değiştirir.</span><span class="sxs-lookup"><span data-stu-id="ab2c0-110">Replaces all content (child nodes and attributes) of an element.</span></span>|  
|<xref:System.Xml.Linq.XElement.ReplaceAttributes%2A?displayProperty=nameWithType>|<span data-ttu-id="ab2c0-111">Bir öğenin öznitelikleri değiştirir.</span><span class="sxs-lookup"><span data-stu-id="ab2c0-111">Replaces the attributes of an element.</span></span>|  
|<xref:System.Xml.Linq.XElement.SetAttributeValue%2A?displayProperty=nameWithType>|<span data-ttu-id="ab2c0-112">Bir özniteliğin değerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="ab2c0-112">Sets the value of an attribute.</span></span> <span data-ttu-id="ab2c0-113">Öznitelik yoksa oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ab2c0-113">Creates the attribute if it doesn't exist.</span></span> <span data-ttu-id="ab2c0-114">Değer ayarlanmışsa `null`, öznitelik kaldırır.</span><span class="sxs-lookup"><span data-stu-id="ab2c0-114">If the value is set to `null`, removes the attribute.</span></span>|  
|<xref:System.Xml.Linq.XElement.SetElementValue%2A?displayProperty=nameWithType>|<span data-ttu-id="ab2c0-115">Bir alt öğenin değerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="ab2c0-115">Sets the value of a child element.</span></span> <span data-ttu-id="ab2c0-116">Öğe yoksa oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ab2c0-116">Creates the element if it doesn't exist.</span></span> <span data-ttu-id="ab2c0-117">Değer ayarlanmışsa `null`, öğeyi kaldırır.</span><span class="sxs-lookup"><span data-stu-id="ab2c0-117">If the value is set to `null`, removes the element.</span></span>|  
|<xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType>|<span data-ttu-id="ab2c0-118">Bir öğenin içeriğini (alt düğümleri) belirtilen metinle değiştirir.</span><span class="sxs-lookup"><span data-stu-id="ab2c0-118">Replaces the content (child nodes) of an element with the specified text.</span></span>|  
|<xref:System.Xml.Linq.XElement.SetValue%2A?displayProperty=nameWithType>|<span data-ttu-id="ab2c0-119">Bir öğenin değerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="ab2c0-119">Sets the value of an element.</span></span>|  
  
 <span data-ttu-id="ab2c0-120">Aşağıdaki yöntemlerden değiştirme bir <xref:System.Xml.Linq.XAttribute>.</span><span class="sxs-lookup"><span data-stu-id="ab2c0-120">The following methods modify an <xref:System.Xml.Linq.XAttribute>.</span></span>  
  
|<span data-ttu-id="ab2c0-121">Yöntem</span><span class="sxs-lookup"><span data-stu-id="ab2c0-121">Method</span></span>|<span data-ttu-id="ab2c0-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ab2c0-122">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=nameWithType>|<span data-ttu-id="ab2c0-123">Bir özniteliğin değerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="ab2c0-123">Sets the value of an attribute.</span></span>|  
|<xref:System.Xml.Linq.XAttribute.SetValue%2A?displayProperty=nameWithType>|<span data-ttu-id="ab2c0-124">Bir özniteliğin değerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="ab2c0-124">Sets the value of an attribute.</span></span>|  
  
 <span data-ttu-id="ab2c0-125">Aşağıdaki yöntemlerden değiştirme bir <xref:System.Xml.Linq.XNode> (dahil olmak üzere bir <xref:System.Xml.Linq.XElement> veya <xref:System.Xml.Linq.XDocument>).</span><span class="sxs-lookup"><span data-stu-id="ab2c0-125">The following methods modify an <xref:System.Xml.Linq.XNode> (including an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument>).</span></span>  
  
|<span data-ttu-id="ab2c0-126">Yöntem</span><span class="sxs-lookup"><span data-stu-id="ab2c0-126">Method</span></span>|<span data-ttu-id="ab2c0-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ab2c0-127">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XNode.ReplaceWith%2A?displayProperty=nameWithType>|<span data-ttu-id="ab2c0-128">Bir düğüm, yeni içerikle değiştirir.</span><span class="sxs-lookup"><span data-stu-id="ab2c0-128">Replaces a node with new content.</span></span>|  
  
 <span data-ttu-id="ab2c0-129">Aşağıdaki yöntemlerden değiştirme bir <xref:System.Xml.Linq.XContainer> (bir <xref:System.Xml.Linq.XElement> veya <xref:System.Xml.Linq.XDocument>).</span><span class="sxs-lookup"><span data-stu-id="ab2c0-129">The following methods modify an <xref:System.Xml.Linq.XContainer> (an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument>).</span></span>  
  
|<span data-ttu-id="ab2c0-130">Yöntem</span><span class="sxs-lookup"><span data-stu-id="ab2c0-130">Method</span></span>|<span data-ttu-id="ab2c0-131">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ab2c0-131">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XContainer.ReplaceNodes%2A?displayProperty=nameWithType>|<span data-ttu-id="ab2c0-132">Alt düğüm, yeni içerikle değiştirir.</span><span class="sxs-lookup"><span data-stu-id="ab2c0-132">Replaces the children nodes with new content.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ab2c0-133">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ab2c0-133">See Also</span></span>

- [<span data-ttu-id="ab2c0-134">(LINQ to XML) XML ağaçlarını değiştirme (C#)</span><span class="sxs-lookup"><span data-stu-id="ab2c0-134">Modifying XML Trees (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)
