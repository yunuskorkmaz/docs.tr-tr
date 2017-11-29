---
title: "Öğeleri, öznitelikleri ve bir XML Tree1 düğümler değiştirme"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 865cf54e-f8ac-4871-863b-a3e6fc61a4b9
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 1c769885d958abeaa92e19ef0b20d695fbcc4b96
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="modifying-elements-attributes-and-nodes-in-an-xml-tree"></a><span data-ttu-id="bb6a4-102">Öğeleri, öznitelikleri ve bir XML ağacında düğümlerin değiştirme</span><span class="sxs-lookup"><span data-stu-id="bb6a4-102">Modifying Elements, Attributes, and Nodes in an XML Tree</span></span>
<span data-ttu-id="bb6a4-103">Bir öğe, alt öğelerini veya özniteliklerini değiştirmek için kullanabileceğiniz özellikler ve yöntemler aşağıdaki tabloda özetlenmiştir.</span><span class="sxs-lookup"><span data-stu-id="bb6a4-103">The following table summarizes the methods and properties that you can use to modify an element, its child elements, or its attributes.</span></span>  
  
 <span data-ttu-id="bb6a4-104">Aşağıdaki yöntemlerden değiştirme bir <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="bb6a4-104">The following methods modify an <xref:System.Xml.Linq.XElement>.</span></span>  
  
|<span data-ttu-id="bb6a4-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="bb6a4-105">Method</span></span>|<span data-ttu-id="bb6a4-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bb6a4-106">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>|<span data-ttu-id="bb6a4-107">Bir öğenin ayrıştırılmış XML ile değiştirir.</span><span class="sxs-lookup"><span data-stu-id="bb6a4-107">Replaces an element with parsed XML.</span></span>|  
|<xref:System.Xml.Linq.XElement.RemoveAll%2A?displayProperty=nameWithType>|<span data-ttu-id="bb6a4-108">Bir öğenin tüm içeriğin (alt düğümleri ve öznitelikleri) kaldırır.</span><span class="sxs-lookup"><span data-stu-id="bb6a4-108">Removes all content (child nodes and attributes) of an element.</span></span>|  
|<xref:System.Xml.Linq.XElement.RemoveAttributes%2A?displayProperty=nameWithType>|<span data-ttu-id="bb6a4-109">Bir öğenin öznitelikleri kaldırır.</span><span class="sxs-lookup"><span data-stu-id="bb6a4-109">Removes the attributes of an element.</span></span>|  
|<xref:System.Xml.Linq.XElement.ReplaceAll%2A?displayProperty=nameWithType>|<span data-ttu-id="bb6a4-110">Bir öğenin tüm içeriğin (alt düğümleri ve öznitelikleri) yerini alır.</span><span class="sxs-lookup"><span data-stu-id="bb6a4-110">Replaces all content (child nodes and attributes) of an element.</span></span>|  
|<xref:System.Xml.Linq.XElement.ReplaceAttributes%2A?displayProperty=nameWithType>|<span data-ttu-id="bb6a4-111">Bir öğenin özniteliklerini değiştirir.</span><span class="sxs-lookup"><span data-stu-id="bb6a4-111">Replaces the attributes of an element.</span></span>|  
|<xref:System.Xml.Linq.XElement.SetAttributeValue%2A?displayProperty=nameWithType>|<span data-ttu-id="bb6a4-112">Özniteliğin değerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="bb6a4-112">Sets the value of an attribute.</span></span> <span data-ttu-id="bb6a4-113">Öznitelik yoksa oluşturur.</span><span class="sxs-lookup"><span data-stu-id="bb6a4-113">Creates the attribute if it doesn't exist.</span></span> <span data-ttu-id="bb6a4-114">Değer ayarlanmışsa `null`, öznitelik kaldırır.</span><span class="sxs-lookup"><span data-stu-id="bb6a4-114">If the value is set to `null`, removes the attribute.</span></span>|  
|<xref:System.Xml.Linq.XElement.SetElementValue%2A?displayProperty=nameWithType>|<span data-ttu-id="bb6a4-115">Bir alt öğenin değerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="bb6a4-115">Sets the value of a child element.</span></span> <span data-ttu-id="bb6a4-116">Yoksa öğesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="bb6a4-116">Creates the element if it doesn't exist.</span></span> <span data-ttu-id="bb6a4-117">Değer ayarlanmışsa `null`, öğeyi kaldırır.</span><span class="sxs-lookup"><span data-stu-id="bb6a4-117">If the value is set to `null`, removes the element.</span></span>|  
|<xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType>|<span data-ttu-id="bb6a4-118">Bir öğenin içeriğini (alt düğümler) belirtilen metinle değiştirir.</span><span class="sxs-lookup"><span data-stu-id="bb6a4-118">Replaces the content (child nodes) of an element with the specified text.</span></span>|  
|<xref:System.Xml.Linq.XElement.SetValue%2A?displayProperty=nameWithType>|<span data-ttu-id="bb6a4-119">Bir öğenin değerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="bb6a4-119">Sets the value of an element.</span></span>|  
  
 <span data-ttu-id="bb6a4-120">Aşağıdaki yöntemlerden değiştirme bir <xref:System.Xml.Linq.XAttribute>.</span><span class="sxs-lookup"><span data-stu-id="bb6a4-120">The following methods modify an <xref:System.Xml.Linq.XAttribute>.</span></span>  
  
|<span data-ttu-id="bb6a4-121">Yöntem</span><span class="sxs-lookup"><span data-stu-id="bb6a4-121">Method</span></span>|<span data-ttu-id="bb6a4-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bb6a4-122">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=nameWithType>|<span data-ttu-id="bb6a4-123">Özniteliğin değerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="bb6a4-123">Sets the value of an attribute.</span></span>|  
|<xref:System.Xml.Linq.XAttribute.SetValue%2A?displayProperty=nameWithType>|<span data-ttu-id="bb6a4-124">Özniteliğin değerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="bb6a4-124">Sets the value of an attribute.</span></span>|  
  
 <span data-ttu-id="bb6a4-125">Aşağıdaki yöntemlerden değiştirme bir <xref:System.Xml.Linq.XNode> (dahil olmak üzere bir <xref:System.Xml.Linq.XElement> veya <xref:System.Xml.Linq.XDocument>).</span><span class="sxs-lookup"><span data-stu-id="bb6a4-125">The following methods modify an <xref:System.Xml.Linq.XNode> (including an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument>).</span></span>  
  
|<span data-ttu-id="bb6a4-126">Yöntem</span><span class="sxs-lookup"><span data-stu-id="bb6a4-126">Method</span></span>|<span data-ttu-id="bb6a4-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bb6a4-127">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XNode.ReplaceWith%2A?displayProperty=nameWithType>|<span data-ttu-id="bb6a4-128">Bir düğüm yeni içerikle değiştirir.</span><span class="sxs-lookup"><span data-stu-id="bb6a4-128">Replaces a node with new content.</span></span>|  
  
 <span data-ttu-id="bb6a4-129">Aşağıdaki yöntemlerden değiştirme bir <xref:System.Xml.Linq.XContainer> (bir <xref:System.Xml.Linq.XElement> veya <xref:System.Xml.Linq.XDocument>).</span><span class="sxs-lookup"><span data-stu-id="bb6a4-129">The following methods modify an <xref:System.Xml.Linq.XContainer> (an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument>).</span></span>  
  
|<span data-ttu-id="bb6a4-130">Yöntem</span><span class="sxs-lookup"><span data-stu-id="bb6a4-130">Method</span></span>|<span data-ttu-id="bb6a4-131">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bb6a4-131">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XContainer.ReplaceNodes%2A?displayProperty=nameWithType>|<span data-ttu-id="bb6a4-132">Alt düğümler ile yeni içerik değiştirir.</span><span class="sxs-lookup"><span data-stu-id="bb6a4-132">Replaces the children nodes with new content.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bb6a4-133">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="bb6a4-133">See Also</span></span>  
 [<span data-ttu-id="bb6a4-134">XML ağaçları (LINQ-XML) değiştirme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bb6a4-134">Modifying XML Trees (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)
