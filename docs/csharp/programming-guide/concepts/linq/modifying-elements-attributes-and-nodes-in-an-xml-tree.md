---
title: Öğe, öznitelik ve düğümleri bir XML Tree3 değiştirme
ms.date: 07/20/2015
ms.assetid: 0ed22e4e-4c6b-4eb1-b0eb-06685efd8c33
ms.openlocfilehash: 93a4d67129e22d0bbeef464c1d4d8758439edb7b
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66484237"
---
# <a name="modifying-elements-attributes-and-nodes-in-an-xml-tree"></a><span data-ttu-id="c35fb-102">XML Ağacındaki Öğe, Öznitelik ve Düğümleri Değiştirme</span><span class="sxs-lookup"><span data-stu-id="c35fb-102">Modifying Elements, Attributes, and Nodes in an XML Tree</span></span>
<span data-ttu-id="c35fb-103">Bir öğe, alt öğelerini ve özniteliklerini değiştirmek için kullanabileceğiniz özellikler ve yöntemler aşağıdaki tabloda özetlenmiştir.</span><span class="sxs-lookup"><span data-stu-id="c35fb-103">The following table summarizes the methods and properties that you can use to modify an element, its child elements, or its attributes.</span></span>  
  
 <span data-ttu-id="c35fb-104">Aşağıdaki yöntemlerden değiştirme bir <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="c35fb-104">The following methods modify an <xref:System.Xml.Linq.XElement>.</span></span>  
  
|<span data-ttu-id="c35fb-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="c35fb-105">Method</span></span>|<span data-ttu-id="c35fb-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c35fb-106">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>|<span data-ttu-id="c35fb-107">Bir öğe ayrıştırılmış XML ile değiştirir.</span><span class="sxs-lookup"><span data-stu-id="c35fb-107">Replaces an element with parsed XML.</span></span>|  
|<xref:System.Xml.Linq.XElement.RemoveAll%2A?displayProperty=nameWithType>|<span data-ttu-id="c35fb-108">Bir öğenin tüm içeriğin (alt düğümleri ve öznitelikleri) kaldırır.</span><span class="sxs-lookup"><span data-stu-id="c35fb-108">Removes all content (child nodes and attributes) of an element.</span></span>|  
|<xref:System.Xml.Linq.XElement.RemoveAttributes%2A?displayProperty=nameWithType>|<span data-ttu-id="c35fb-109">Bir öğenin öznitelikleri kaldırır.</span><span class="sxs-lookup"><span data-stu-id="c35fb-109">Removes the attributes of an element.</span></span>|  
|<xref:System.Xml.Linq.XElement.ReplaceAll%2A?displayProperty=nameWithType>|<span data-ttu-id="c35fb-110">Bir öğenin tüm içeriğin (alt düğümleri ve öznitelikleri) değiştirir.</span><span class="sxs-lookup"><span data-stu-id="c35fb-110">Replaces all content (child nodes and attributes) of an element.</span></span>|  
|<xref:System.Xml.Linq.XElement.ReplaceAttributes%2A?displayProperty=nameWithType>|<span data-ttu-id="c35fb-111">Bir öğenin öznitelikleri değiştirir.</span><span class="sxs-lookup"><span data-stu-id="c35fb-111">Replaces the attributes of an element.</span></span>|  
|<xref:System.Xml.Linq.XElement.SetAttributeValue%2A?displayProperty=nameWithType>|<span data-ttu-id="c35fb-112">Bir özniteliğin değerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="c35fb-112">Sets the value of an attribute.</span></span> <span data-ttu-id="c35fb-113">Öznitelik yoksa oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c35fb-113">Creates the attribute if it doesn't exist.</span></span> <span data-ttu-id="c35fb-114">Değer ayarlanmışsa `null`, öznitelik kaldırır.</span><span class="sxs-lookup"><span data-stu-id="c35fb-114">If the value is set to `null`, removes the attribute.</span></span>|  
|<xref:System.Xml.Linq.XElement.SetElementValue%2A?displayProperty=nameWithType>|<span data-ttu-id="c35fb-115">Bir alt öğenin değerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="c35fb-115">Sets the value of a child element.</span></span> <span data-ttu-id="c35fb-116">Öğe yoksa oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c35fb-116">Creates the element if it doesn't exist.</span></span> <span data-ttu-id="c35fb-117">Değer ayarlanmışsa `null`, öğeyi kaldırır.</span><span class="sxs-lookup"><span data-stu-id="c35fb-117">If the value is set to `null`, removes the element.</span></span>|  
|<xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType>|<span data-ttu-id="c35fb-118">Bir öğenin içeriğini (alt düğümleri) belirtilen metinle değiştirir.</span><span class="sxs-lookup"><span data-stu-id="c35fb-118">Replaces the content (child nodes) of an element with the specified text.</span></span>|  
|<xref:System.Xml.Linq.XElement.SetValue%2A?displayProperty=nameWithType>|<span data-ttu-id="c35fb-119">Bir öğenin değerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="c35fb-119">Sets the value of an element.</span></span>|  
  
 <span data-ttu-id="c35fb-120">Aşağıdaki yöntemlerden değiştirme bir <xref:System.Xml.Linq.XAttribute>.</span><span class="sxs-lookup"><span data-stu-id="c35fb-120">The following methods modify an <xref:System.Xml.Linq.XAttribute>.</span></span>  
  
|<span data-ttu-id="c35fb-121">Yöntem</span><span class="sxs-lookup"><span data-stu-id="c35fb-121">Method</span></span>|<span data-ttu-id="c35fb-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c35fb-122">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=nameWithType>|<span data-ttu-id="c35fb-123">Bir özniteliğin değerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="c35fb-123">Sets the value of an attribute.</span></span>|  
|<xref:System.Xml.Linq.XAttribute.SetValue%2A?displayProperty=nameWithType>|<span data-ttu-id="c35fb-124">Bir özniteliğin değerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="c35fb-124">Sets the value of an attribute.</span></span>|  
  
 <span data-ttu-id="c35fb-125">Aşağıdaki yöntemlerden değiştirme bir <xref:System.Xml.Linq.XNode> (dahil olmak üzere bir <xref:System.Xml.Linq.XElement> veya <xref:System.Xml.Linq.XDocument>).</span><span class="sxs-lookup"><span data-stu-id="c35fb-125">The following methods modify an <xref:System.Xml.Linq.XNode> (including an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument>).</span></span>  
  
|<span data-ttu-id="c35fb-126">Yöntem</span><span class="sxs-lookup"><span data-stu-id="c35fb-126">Method</span></span>|<span data-ttu-id="c35fb-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c35fb-127">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XNode.ReplaceWith%2A?displayProperty=nameWithType>|<span data-ttu-id="c35fb-128">Bir düğüm, yeni içerikle değiştirir.</span><span class="sxs-lookup"><span data-stu-id="c35fb-128">Replaces a node with new content.</span></span>|  
  
 <span data-ttu-id="c35fb-129">Aşağıdaki yöntemlerden değiştirme bir <xref:System.Xml.Linq.XContainer> (bir <xref:System.Xml.Linq.XElement> veya <xref:System.Xml.Linq.XDocument>).</span><span class="sxs-lookup"><span data-stu-id="c35fb-129">The following methods modify an <xref:System.Xml.Linq.XContainer> (an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument>).</span></span>  
  
|<span data-ttu-id="c35fb-130">Yöntem</span><span class="sxs-lookup"><span data-stu-id="c35fb-130">Method</span></span>|<span data-ttu-id="c35fb-131">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c35fb-131">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XContainer.ReplaceNodes%2A?displayProperty=nameWithType>|<span data-ttu-id="c35fb-132">Alt düğüm, yeni içerikle değiştirir.</span><span class="sxs-lookup"><span data-stu-id="c35fb-132">Replaces the children nodes with new content.</span></span>|  
