---
title: XML Tree1 içinde öğeleri, öznitelikleri ve düğümleri değiştirme
ms.date: 07/20/2015
ms.assetid: 865cf54e-f8ac-4871-863b-a3e6fc61a4b9
ms.openlocfilehash: 002e87d58ad1a3730889225bf4b3e50448431f2d
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84360936"
---
# <a name="modifying-elements-attributes-and-nodes-in-an-xml-tree"></a><span data-ttu-id="b5245-102">XML Ağacındaki Öğe, Öznitelik ve Düğümleri Değiştirme</span><span class="sxs-lookup"><span data-stu-id="b5245-102">Modifying Elements, Attributes, and Nodes in an XML Tree</span></span>
<span data-ttu-id="b5245-103">Aşağıdaki tabloda bir öğe, alt öğeleri veya özniteliklerini değiştirmek için kullanabileceğiniz yöntemler ve Özellikler özetlenmektedir.</span><span class="sxs-lookup"><span data-stu-id="b5245-103">The following table summarizes the methods and properties that you can use to modify an element, its child elements, or its attributes.</span></span>  
  
 <span data-ttu-id="b5245-104">Aşağıdaki yöntemler bir değiştirir <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="b5245-104">The following methods modify an <xref:System.Xml.Linq.XElement>.</span></span>  
  
|<span data-ttu-id="b5245-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="b5245-105">Method</span></span>|<span data-ttu-id="b5245-106">Description</span><span class="sxs-lookup"><span data-stu-id="b5245-106">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>|<span data-ttu-id="b5245-107">Bir öğeyi ayrıştırılmış XML ile değiştirir.</span><span class="sxs-lookup"><span data-stu-id="b5245-107">Replaces an element with parsed XML.</span></span>|  
|<xref:System.Xml.Linq.XElement.RemoveAll%2A?displayProperty=nameWithType>|<span data-ttu-id="b5245-108">Bir öğenin tüm içeriğini (alt düğümleri ve öznitelikleri) kaldırır.</span><span class="sxs-lookup"><span data-stu-id="b5245-108">Removes all content (child nodes and attributes) of an element.</span></span>|  
|<xref:System.Xml.Linq.XElement.RemoveAttributes%2A?displayProperty=nameWithType>|<span data-ttu-id="b5245-109">Bir öğenin özniteliklerini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="b5245-109">Removes the attributes of an element.</span></span>|  
|<xref:System.Xml.Linq.XElement.ReplaceAll%2A?displayProperty=nameWithType>|<span data-ttu-id="b5245-110">Bir öğenin tüm içeriğini (alt düğümleri ve öznitelikleri) değiştirir.</span><span class="sxs-lookup"><span data-stu-id="b5245-110">Replaces all content (child nodes and attributes) of an element.</span></span>|  
|<xref:System.Xml.Linq.XElement.ReplaceAttributes%2A?displayProperty=nameWithType>|<span data-ttu-id="b5245-111">Bir öğenin özniteliklerini değiştirir.</span><span class="sxs-lookup"><span data-stu-id="b5245-111">Replaces the attributes of an element.</span></span>|  
|<xref:System.Xml.Linq.XElement.SetAttributeValue%2A?displayProperty=nameWithType>|<span data-ttu-id="b5245-112">Bir özniteliğin değerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="b5245-112">Sets the value of an attribute.</span></span> <span data-ttu-id="b5245-113">Mevcut değilse özniteliği oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b5245-113">Creates the attribute if it doesn't exist.</span></span> <span data-ttu-id="b5245-114">Değer olarak ayarlanırsa `null` , özniteliğini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="b5245-114">If the value is set to `null`, removes the attribute.</span></span>|  
|<xref:System.Xml.Linq.XElement.SetElementValue%2A?displayProperty=nameWithType>|<span data-ttu-id="b5245-115">Bir alt öğenin değerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="b5245-115">Sets the value of a child element.</span></span> <span data-ttu-id="b5245-116">Yoksa, öğesini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b5245-116">Creates the element if it doesn't exist.</span></span> <span data-ttu-id="b5245-117">Değer olarak ayarlanırsa `null` , öğesini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="b5245-117">If the value is set to `null`, removes the element.</span></span>|  
|<xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType>|<span data-ttu-id="b5245-118">Bir öğenin içeriğini (alt düğümleri) belirtilen metinle değiştirir.</span><span class="sxs-lookup"><span data-stu-id="b5245-118">Replaces the content (child nodes) of an element with the specified text.</span></span>|  
|<xref:System.Xml.Linq.XElement.SetValue%2A?displayProperty=nameWithType>|<span data-ttu-id="b5245-119">Bir öğenin değerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="b5245-119">Sets the value of an element.</span></span>|  
  
 <span data-ttu-id="b5245-120">Aşağıdaki yöntemler bir değiştirir <xref:System.Xml.Linq.XAttribute> .</span><span class="sxs-lookup"><span data-stu-id="b5245-120">The following methods modify an <xref:System.Xml.Linq.XAttribute>.</span></span>  
  
|<span data-ttu-id="b5245-121">Yöntem</span><span class="sxs-lookup"><span data-stu-id="b5245-121">Method</span></span>|<span data-ttu-id="b5245-122">Description</span><span class="sxs-lookup"><span data-stu-id="b5245-122">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=nameWithType>|<span data-ttu-id="b5245-123">Bir özniteliğin değerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="b5245-123">Sets the value of an attribute.</span></span>|  
|<xref:System.Xml.Linq.XAttribute.SetValue%2A?displayProperty=nameWithType>|<span data-ttu-id="b5245-124">Bir özniteliğin değerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="b5245-124">Sets the value of an attribute.</span></span>|  
  
 <span data-ttu-id="b5245-125">Aşağıdaki yöntemler bir ' i <xref:System.Xml.Linq.XNode> (veya dahil <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XDocument> ) değiştirir.</span><span class="sxs-lookup"><span data-stu-id="b5245-125">The following methods modify an <xref:System.Xml.Linq.XNode> (including an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument>).</span></span>  
  
|<span data-ttu-id="b5245-126">Yöntem</span><span class="sxs-lookup"><span data-stu-id="b5245-126">Method</span></span>|<span data-ttu-id="b5245-127">Description</span><span class="sxs-lookup"><span data-stu-id="b5245-127">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XNode.ReplaceWith%2A?displayProperty=nameWithType>|<span data-ttu-id="b5245-128">Bir düğümü yeni içerikle değiştirir.</span><span class="sxs-lookup"><span data-stu-id="b5245-128">Replaces a node with new content.</span></span>|  
  
 <span data-ttu-id="b5245-129">Aşağıdaki yöntemler bir <xref:System.Xml.Linq.XContainer> ( <xref:System.Xml.Linq.XElement> veya <xref:System.Xml.Linq.XDocument> ) değiştirir.</span><span class="sxs-lookup"><span data-stu-id="b5245-129">The following methods modify an <xref:System.Xml.Linq.XContainer> (an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument>).</span></span>  
  
|<span data-ttu-id="b5245-130">Yöntem</span><span class="sxs-lookup"><span data-stu-id="b5245-130">Method</span></span>|<span data-ttu-id="b5245-131">Description</span><span class="sxs-lookup"><span data-stu-id="b5245-131">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XContainer.ReplaceNodes%2A?displayProperty=nameWithType>|<span data-ttu-id="b5245-132">Alt düğümleri yeni içerikle değiştirir.</span><span class="sxs-lookup"><span data-stu-id="b5245-132">Replaces the children nodes with new content.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b5245-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b5245-133">See also</span></span>

- [<span data-ttu-id="b5245-134">XML ağaçlarını değiştirme (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b5245-134">Modifying XML Trees (LINQ to XML) (Visual Basic)</span></span>](modifying-xml-trees-linq-to-xml.md)
