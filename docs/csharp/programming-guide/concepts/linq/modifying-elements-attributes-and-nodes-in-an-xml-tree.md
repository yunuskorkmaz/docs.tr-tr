---
title: XML Ağacındaki Öğeleri, Öznitelikleri ve Düğümleri Değiştirme3
ms.date: 07/20/2015
ms.assetid: 0ed22e4e-4c6b-4eb1-b0eb-06685efd8c33
ms.openlocfilehash: 93a4d67129e22d0bbeef464c1d4d8758439edb7b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "66484237"
---
# <a name="modifying-elements-attributes-and-nodes-in-an-xml-tree"></a><span data-ttu-id="109a3-102">XML Ağacındaki Öğe, Öznitelik ve Düğümleri Değiştirme</span><span class="sxs-lookup"><span data-stu-id="109a3-102">Modifying Elements, Attributes, and Nodes in an XML Tree</span></span>
<span data-ttu-id="109a3-103">Aşağıdaki tablo, bir öğeyi, alt öğelerini veya özniteliklerini değiştirmek için kullanabileceğiniz yöntemleri ve özellikleri özetler.</span><span class="sxs-lookup"><span data-stu-id="109a3-103">The following table summarizes the methods and properties that you can use to modify an element, its child elements, or its attributes.</span></span>  
  
 <span data-ttu-id="109a3-104">Aşağıdaki yöntemler bir. <xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="109a3-104">The following methods modify an <xref:System.Xml.Linq.XElement>.</span></span>  
  
|<span data-ttu-id="109a3-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="109a3-105">Method</span></span>|<span data-ttu-id="109a3-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="109a3-106">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>|<span data-ttu-id="109a3-107">Bir öğeyi ayrışmış XML ile değiştirir.</span><span class="sxs-lookup"><span data-stu-id="109a3-107">Replaces an element with parsed XML.</span></span>|  
|<xref:System.Xml.Linq.XElement.RemoveAll%2A?displayProperty=nameWithType>|<span data-ttu-id="109a3-108">Bir öğenin tüm içeriğini (alt düğümleri ve öznitelikleri) kaldırır.</span><span class="sxs-lookup"><span data-stu-id="109a3-108">Removes all content (child nodes and attributes) of an element.</span></span>|  
|<xref:System.Xml.Linq.XElement.RemoveAttributes%2A?displayProperty=nameWithType>|<span data-ttu-id="109a3-109">Bir öğenin özniteliklerini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="109a3-109">Removes the attributes of an element.</span></span>|  
|<xref:System.Xml.Linq.XElement.ReplaceAll%2A?displayProperty=nameWithType>|<span data-ttu-id="109a3-110">Bir öğenin tüm içeriğini (alt düğümleri ve öznitelikleri) değiştirir.</span><span class="sxs-lookup"><span data-stu-id="109a3-110">Replaces all content (child nodes and attributes) of an element.</span></span>|  
|<xref:System.Xml.Linq.XElement.ReplaceAttributes%2A?displayProperty=nameWithType>|<span data-ttu-id="109a3-111">Bir öğenin özniteliklerini değiştirir.</span><span class="sxs-lookup"><span data-stu-id="109a3-111">Replaces the attributes of an element.</span></span>|  
|<xref:System.Xml.Linq.XElement.SetAttributeValue%2A?displayProperty=nameWithType>|<span data-ttu-id="109a3-112">Bir özniteliğin değerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="109a3-112">Sets the value of an attribute.</span></span> <span data-ttu-id="109a3-113">Yoksa öznitelik oluşturur.</span><span class="sxs-lookup"><span data-stu-id="109a3-113">Creates the attribute if it doesn't exist.</span></span> <span data-ttu-id="109a3-114">Değer `null`ayarlanmışsa, özniteliği kaldırır.</span><span class="sxs-lookup"><span data-stu-id="109a3-114">If the value is set to `null`, removes the attribute.</span></span>|  
|<xref:System.Xml.Linq.XElement.SetElementValue%2A?displayProperty=nameWithType>|<span data-ttu-id="109a3-115">Bir alt öğenin değerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="109a3-115">Sets the value of a child element.</span></span> <span data-ttu-id="109a3-116">Yoksa öğeyi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="109a3-116">Creates the element if it doesn't exist.</span></span> <span data-ttu-id="109a3-117">Değer `null`ayarlanmışsa, öğeyi kaldırır.</span><span class="sxs-lookup"><span data-stu-id="109a3-117">If the value is set to `null`, removes the element.</span></span>|  
|<xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType>|<span data-ttu-id="109a3-118">Bir öğenin içeriğini (alt düğümleri) belirtilen metinle değiştirir.</span><span class="sxs-lookup"><span data-stu-id="109a3-118">Replaces the content (child nodes) of an element with the specified text.</span></span>|  
|<xref:System.Xml.Linq.XElement.SetValue%2A?displayProperty=nameWithType>|<span data-ttu-id="109a3-119">Bir öğenin değerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="109a3-119">Sets the value of an element.</span></span>|  
  
 <span data-ttu-id="109a3-120">Aşağıdaki yöntemler bir. <xref:System.Xml.Linq.XAttribute></span><span class="sxs-lookup"><span data-stu-id="109a3-120">The following methods modify an <xref:System.Xml.Linq.XAttribute>.</span></span>  
  
|<span data-ttu-id="109a3-121">Yöntem</span><span class="sxs-lookup"><span data-stu-id="109a3-121">Method</span></span>|<span data-ttu-id="109a3-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="109a3-122">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=nameWithType>|<span data-ttu-id="109a3-123">Bir özniteliğin değerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="109a3-123">Sets the value of an attribute.</span></span>|  
|<xref:System.Xml.Linq.XAttribute.SetValue%2A?displayProperty=nameWithType>|<span data-ttu-id="109a3-124">Bir özniteliğin değerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="109a3-124">Sets the value of an attribute.</span></span>|  
  
 <span data-ttu-id="109a3-125">Aşağıdaki yöntemler bir <xref:System.Xml.Linq.XNode> (bir <xref:System.Xml.Linq.XElement> veya <xref:System.Xml.Linq.XDocument>dahil) değiştirmek.</span><span class="sxs-lookup"><span data-stu-id="109a3-125">The following methods modify an <xref:System.Xml.Linq.XNode> (including an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument>).</span></span>  
  
|<span data-ttu-id="109a3-126">Yöntem</span><span class="sxs-lookup"><span data-stu-id="109a3-126">Method</span></span>|<span data-ttu-id="109a3-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="109a3-127">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XNode.ReplaceWith%2A?displayProperty=nameWithType>|<span data-ttu-id="109a3-128">Düğümü yeni içerikle değiştirir.</span><span class="sxs-lookup"><span data-stu-id="109a3-128">Replaces a node with new content.</span></span>|  
  
 <span data-ttu-id="109a3-129">Aşağıdaki yöntemler bir <xref:System.Xml.Linq.XContainer> <xref:System.Xml.Linq.XElement> (bir <xref:System.Xml.Linq.XDocument>veya) değiştirmek.</span><span class="sxs-lookup"><span data-stu-id="109a3-129">The following methods modify an <xref:System.Xml.Linq.XContainer> (an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument>).</span></span>  
  
|<span data-ttu-id="109a3-130">Yöntem</span><span class="sxs-lookup"><span data-stu-id="109a3-130">Method</span></span>|<span data-ttu-id="109a3-131">Açıklama</span><span class="sxs-lookup"><span data-stu-id="109a3-131">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XContainer.ReplaceNodes%2A?displayProperty=nameWithType>|<span data-ttu-id="109a3-132">Çocuk düğümlerini yeni içerikle değiştirir.</span><span class="sxs-lookup"><span data-stu-id="109a3-132">Replaces the children nodes with new content.</span></span>|  
