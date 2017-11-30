---
title: "Öğeleri, öznitelikleri ve bir XML Tree3 düğümler değiştirme"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 0ed22e4e-4c6b-4eb1-b0eb-06685efd8c33
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: da3b31456bc86b547c5174143620f464dc42f35b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="modifying-elements-attributes-and-nodes-in-an-xml-tree"></a><span data-ttu-id="310cf-102">Öğeleri, öznitelikleri ve bir XML ağacında düğümlerin değiştirme</span><span class="sxs-lookup"><span data-stu-id="310cf-102">Modifying Elements, Attributes, and Nodes in an XML Tree</span></span>
<span data-ttu-id="310cf-103">Bir öğe, alt öğelerini veya özniteliklerini değiştirmek için kullanabileceğiniz özellikler ve yöntemler aşağıdaki tabloda özetlenmiştir.</span><span class="sxs-lookup"><span data-stu-id="310cf-103">The following table summarizes the methods and properties that you can use to modify an element, its child elements, or its attributes.</span></span>  
  
 <span data-ttu-id="310cf-104">Aşağıdaki yöntemlerden değiştirme bir <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="310cf-104">The following methods modify an <xref:System.Xml.Linq.XElement>.</span></span>  
  
|<span data-ttu-id="310cf-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="310cf-105">Method</span></span>|<span data-ttu-id="310cf-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="310cf-106">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>|<span data-ttu-id="310cf-107">Bir öğenin ayrıştırılmış XML ile değiştirir.</span><span class="sxs-lookup"><span data-stu-id="310cf-107">Replaces an element with parsed XML.</span></span>|  
|<xref:System.Xml.Linq.XElement.RemoveAll%2A?displayProperty=nameWithType>|<span data-ttu-id="310cf-108">Bir öğenin tüm içeriğin (alt düğümleri ve öznitelikleri) kaldırır.</span><span class="sxs-lookup"><span data-stu-id="310cf-108">Removes all content (child nodes and attributes) of an element.</span></span>|  
|<xref:System.Xml.Linq.XElement.RemoveAttributes%2A?displayProperty=nameWithType>|<span data-ttu-id="310cf-109">Bir öğenin öznitelikleri kaldırır.</span><span class="sxs-lookup"><span data-stu-id="310cf-109">Removes the attributes of an element.</span></span>|  
|<xref:System.Xml.Linq.XElement.ReplaceAll%2A?displayProperty=nameWithType>|<span data-ttu-id="310cf-110">Bir öğenin tüm içeriğin (alt düğümleri ve öznitelikleri) yerini alır.</span><span class="sxs-lookup"><span data-stu-id="310cf-110">Replaces all content (child nodes and attributes) of an element.</span></span>|  
|<xref:System.Xml.Linq.XElement.ReplaceAttributes%2A?displayProperty=nameWithType>|<span data-ttu-id="310cf-111">Bir öğenin özniteliklerini değiştirir.</span><span class="sxs-lookup"><span data-stu-id="310cf-111">Replaces the attributes of an element.</span></span>|  
|<xref:System.Xml.Linq.XElement.SetAttributeValue%2A?displayProperty=nameWithType>|<span data-ttu-id="310cf-112">Özniteliğin değerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="310cf-112">Sets the value of an attribute.</span></span> <span data-ttu-id="310cf-113">Öznitelik yoksa oluşturur.</span><span class="sxs-lookup"><span data-stu-id="310cf-113">Creates the attribute if it doesn't exist.</span></span> <span data-ttu-id="310cf-114">Değer ayarlanmışsa `null`, öznitelik kaldırır.</span><span class="sxs-lookup"><span data-stu-id="310cf-114">If the value is set to `null`, removes the attribute.</span></span>|  
|<xref:System.Xml.Linq.XElement.SetElementValue%2A?displayProperty=nameWithType>|<span data-ttu-id="310cf-115">Bir alt öğenin değerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="310cf-115">Sets the value of a child element.</span></span> <span data-ttu-id="310cf-116">Yoksa öğesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="310cf-116">Creates the element if it doesn't exist.</span></span> <span data-ttu-id="310cf-117">Değer ayarlanmışsa `null`, öğeyi kaldırır.</span><span class="sxs-lookup"><span data-stu-id="310cf-117">If the value is set to `null`, removes the element.</span></span>|  
|<xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType>|<span data-ttu-id="310cf-118">Bir öğenin içeriğini (alt düğümler) belirtilen metinle değiştirir.</span><span class="sxs-lookup"><span data-stu-id="310cf-118">Replaces the content (child nodes) of an element with the specified text.</span></span>|  
|<xref:System.Xml.Linq.XElement.SetValue%2A?displayProperty=nameWithType>|<span data-ttu-id="310cf-119">Bir öğenin değerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="310cf-119">Sets the value of an element.</span></span>|  
  
 <span data-ttu-id="310cf-120">Aşağıdaki yöntemlerden değiştirme bir <xref:System.Xml.Linq.XAttribute>.</span><span class="sxs-lookup"><span data-stu-id="310cf-120">The following methods modify an <xref:System.Xml.Linq.XAttribute>.</span></span>  
  
|<span data-ttu-id="310cf-121">Yöntem</span><span class="sxs-lookup"><span data-stu-id="310cf-121">Method</span></span>|<span data-ttu-id="310cf-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="310cf-122">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=nameWithType>|<span data-ttu-id="310cf-123">Özniteliğin değerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="310cf-123">Sets the value of an attribute.</span></span>|  
|<xref:System.Xml.Linq.XAttribute.SetValue%2A?displayProperty=nameWithType>|<span data-ttu-id="310cf-124">Özniteliğin değerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="310cf-124">Sets the value of an attribute.</span></span>|  
  
 <span data-ttu-id="310cf-125">Aşağıdaki yöntemlerden değiştirme bir <xref:System.Xml.Linq.XNode> (dahil olmak üzere bir <xref:System.Xml.Linq.XElement> veya <xref:System.Xml.Linq.XDocument>).</span><span class="sxs-lookup"><span data-stu-id="310cf-125">The following methods modify an <xref:System.Xml.Linq.XNode> (including an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument>).</span></span>  
  
|<span data-ttu-id="310cf-126">Yöntem</span><span class="sxs-lookup"><span data-stu-id="310cf-126">Method</span></span>|<span data-ttu-id="310cf-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="310cf-127">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XNode.ReplaceWith%2A?displayProperty=nameWithType>|<span data-ttu-id="310cf-128">Bir düğüm yeni içerikle değiştirir.</span><span class="sxs-lookup"><span data-stu-id="310cf-128">Replaces a node with new content.</span></span>|  
  
 <span data-ttu-id="310cf-129">Aşağıdaki yöntemlerden değiştirme bir <xref:System.Xml.Linq.XContainer> (bir <xref:System.Xml.Linq.XElement> veya <xref:System.Xml.Linq.XDocument>).</span><span class="sxs-lookup"><span data-stu-id="310cf-129">The following methods modify an <xref:System.Xml.Linq.XContainer> (an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument>).</span></span>  
  
|<span data-ttu-id="310cf-130">Yöntem</span><span class="sxs-lookup"><span data-stu-id="310cf-130">Method</span></span>|<span data-ttu-id="310cf-131">Açıklama</span><span class="sxs-lookup"><span data-stu-id="310cf-131">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XContainer.ReplaceNodes%2A?displayProperty=nameWithType>|<span data-ttu-id="310cf-132">Alt düğümler ile yeni içerik değiştirir.</span><span class="sxs-lookup"><span data-stu-id="310cf-132">Replaces the children nodes with new content.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="310cf-133">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="310cf-133">See Also</span></span>  
 [<span data-ttu-id="310cf-134">XML ağaçları (LINQ-XML) değiştirme (C#)</span><span class="sxs-lookup"><span data-stu-id="310cf-134">Modifying XML Trees (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)
