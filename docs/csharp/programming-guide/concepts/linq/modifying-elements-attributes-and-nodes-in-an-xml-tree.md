---
title: XML Ağacındaki Öğe, Öznitelik ve Düğümleri Değiştirme
description: Bir öğeyi, alt düğümlerini veya özniteliklerini değiştirmek için kullanabileceğiniz yöntemler ve özellikler hakkında bilgi edinin.
ms.date: 07/20/2015
ms.assetid: 0ed22e4e-4c6b-4eb1-b0eb-06685efd8c33
ms.openlocfilehash: bfff882dc57a4f6f4b228563ac923122097d88d0
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303172"
---
# <a name="modifying-elements-attributes-and-nodes-in-an-xml-tree"></a><span data-ttu-id="d9296-103">XML Ağacındaki Öğe, Öznitelik ve Düğümleri Değiştirme</span><span class="sxs-lookup"><span data-stu-id="d9296-103">Modifying Elements, Attributes, and Nodes in an XML Tree</span></span>
<span data-ttu-id="d9296-104">Aşağıdaki tabloda bir öğe, alt öğeleri veya özniteliklerini değiştirmek için kullanabileceğiniz yöntemler ve Özellikler özetlenmektedir.</span><span class="sxs-lookup"><span data-stu-id="d9296-104">The following table summarizes the methods and properties that you can use to modify an element, its child elements, or its attributes.</span></span>  
  
 <span data-ttu-id="d9296-105">Aşağıdaki yöntemler bir değiştirir <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="d9296-105">The following methods modify an <xref:System.Xml.Linq.XElement>.</span></span>  
  
|<span data-ttu-id="d9296-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="d9296-106">Method</span></span>|<span data-ttu-id="d9296-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d9296-107">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>|<span data-ttu-id="d9296-108">Bir öğeyi ayrıştırılmış XML ile değiştirir.</span><span class="sxs-lookup"><span data-stu-id="d9296-108">Replaces an element with parsed XML.</span></span>|  
|<xref:System.Xml.Linq.XElement.RemoveAll%2A?displayProperty=nameWithType>|<span data-ttu-id="d9296-109">Bir öğenin tüm içeriğini (alt düğümleri ve öznitelikleri) kaldırır.</span><span class="sxs-lookup"><span data-stu-id="d9296-109">Removes all content (child nodes and attributes) of an element.</span></span>|  
|<xref:System.Xml.Linq.XElement.RemoveAttributes%2A?displayProperty=nameWithType>|<span data-ttu-id="d9296-110">Bir öğenin özniteliklerini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="d9296-110">Removes the attributes of an element.</span></span>|  
|<xref:System.Xml.Linq.XElement.ReplaceAll%2A?displayProperty=nameWithType>|<span data-ttu-id="d9296-111">Bir öğenin tüm içeriğini (alt düğümleri ve öznitelikleri) değiştirir.</span><span class="sxs-lookup"><span data-stu-id="d9296-111">Replaces all content (child nodes and attributes) of an element.</span></span>|  
|<xref:System.Xml.Linq.XElement.ReplaceAttributes%2A?displayProperty=nameWithType>|<span data-ttu-id="d9296-112">Bir öğenin özniteliklerini değiştirir.</span><span class="sxs-lookup"><span data-stu-id="d9296-112">Replaces the attributes of an element.</span></span>|  
|<xref:System.Xml.Linq.XElement.SetAttributeValue%2A?displayProperty=nameWithType>|<span data-ttu-id="d9296-113">Bir özniteliğin değerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="d9296-113">Sets the value of an attribute.</span></span> <span data-ttu-id="d9296-114">Mevcut değilse özniteliği oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d9296-114">Creates the attribute if it doesn't exist.</span></span> <span data-ttu-id="d9296-115">Değer olarak ayarlanırsa `null` , özniteliğini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="d9296-115">If the value is set to `null`, removes the attribute.</span></span>|  
|<xref:System.Xml.Linq.XElement.SetElementValue%2A?displayProperty=nameWithType>|<span data-ttu-id="d9296-116">Bir alt öğenin değerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="d9296-116">Sets the value of a child element.</span></span> <span data-ttu-id="d9296-117">Yoksa, öğesini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d9296-117">Creates the element if it doesn't exist.</span></span> <span data-ttu-id="d9296-118">Değer olarak ayarlanırsa `null` , öğesini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="d9296-118">If the value is set to `null`, removes the element.</span></span>|  
|<xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType>|<span data-ttu-id="d9296-119">Bir öğenin içeriğini (alt düğümleri) belirtilen metinle değiştirir.</span><span class="sxs-lookup"><span data-stu-id="d9296-119">Replaces the content (child nodes) of an element with the specified text.</span></span>|  
|<xref:System.Xml.Linq.XElement.SetValue%2A?displayProperty=nameWithType>|<span data-ttu-id="d9296-120">Bir öğenin değerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="d9296-120">Sets the value of an element.</span></span>|  
  
 <span data-ttu-id="d9296-121">Aşağıdaki yöntemler bir değiştirir <xref:System.Xml.Linq.XAttribute> .</span><span class="sxs-lookup"><span data-stu-id="d9296-121">The following methods modify an <xref:System.Xml.Linq.XAttribute>.</span></span>  
  
|<span data-ttu-id="d9296-122">Yöntem</span><span class="sxs-lookup"><span data-stu-id="d9296-122">Method</span></span>|<span data-ttu-id="d9296-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d9296-123">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=nameWithType>|<span data-ttu-id="d9296-124">Bir özniteliğin değerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="d9296-124">Sets the value of an attribute.</span></span>|  
|<xref:System.Xml.Linq.XAttribute.SetValue%2A?displayProperty=nameWithType>|<span data-ttu-id="d9296-125">Bir özniteliğin değerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="d9296-125">Sets the value of an attribute.</span></span>|  
  
 <span data-ttu-id="d9296-126">Aşağıdaki yöntemler bir ' i <xref:System.Xml.Linq.XNode> (veya dahil <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XDocument> ) değiştirir.</span><span class="sxs-lookup"><span data-stu-id="d9296-126">The following methods modify an <xref:System.Xml.Linq.XNode> (including an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument>).</span></span>  
  
|<span data-ttu-id="d9296-127">Yöntem</span><span class="sxs-lookup"><span data-stu-id="d9296-127">Method</span></span>|<span data-ttu-id="d9296-128">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d9296-128">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XNode.ReplaceWith%2A?displayProperty=nameWithType>|<span data-ttu-id="d9296-129">Bir düğümü yeni içerikle değiştirir.</span><span class="sxs-lookup"><span data-stu-id="d9296-129">Replaces a node with new content.</span></span>|  
  
 <span data-ttu-id="d9296-130">Aşağıdaki yöntemler bir <xref:System.Xml.Linq.XContainer> ( <xref:System.Xml.Linq.XElement> veya <xref:System.Xml.Linq.XDocument> ) değiştirir.</span><span class="sxs-lookup"><span data-stu-id="d9296-130">The following methods modify an <xref:System.Xml.Linq.XContainer> (an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument>).</span></span>  
  
|<span data-ttu-id="d9296-131">Yöntem</span><span class="sxs-lookup"><span data-stu-id="d9296-131">Method</span></span>|<span data-ttu-id="d9296-132">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d9296-132">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XContainer.ReplaceNodes%2A?displayProperty=nameWithType>|<span data-ttu-id="d9296-133">Alt düğümleri yeni içerikle değiştirir.</span><span class="sxs-lookup"><span data-stu-id="d9296-133">Replaces the children nodes with new content.</span></span>|  
