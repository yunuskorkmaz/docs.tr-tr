---
description: 'Daha fazla bilgi edinin: tabloları erteleme'
title: Tabloların Çıkarımını Yapma
ms.date: 03/30/2017
ms.assetid: 74a288d4-b8e9-4f1a-b2cd-10df92c1ed1f
ms.openlocfilehash: 00a24cbfc44aea4279b0a115214ec26d3eac59ad
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99652165"
---
# <a name="inferring-tables"></a><span data-ttu-id="e4e6d-103">Tabloların Çıkarımını Yapma</span><span class="sxs-lookup"><span data-stu-id="e4e6d-103">Inferring Tables</span></span>

<span data-ttu-id="e4e6d-104">Bir XML belgesinden bir şemayı kullanırken <xref:System.Data.DataSet> , ADO.net ilk olarak tabloları temsil eden XML öğelerini belirler.</span><span class="sxs-lookup"><span data-stu-id="e4e6d-104">When inferring a schema for a <xref:System.Data.DataSet> from an XML document, ADO.NET first determines which XML elements represent tables.</span></span> <span data-ttu-id="e4e6d-105">Aşağıdaki XML yapıları **veri kümesi** şemasının bir tablosu ile sonuçlanır:</span><span class="sxs-lookup"><span data-stu-id="e4e6d-105">The following XML structures result in a table for the **DataSet** schema:</span></span>  
  
- <span data-ttu-id="e4e6d-106">Öznitelikleri olan öğeler</span><span class="sxs-lookup"><span data-stu-id="e4e6d-106">Elements with attributes</span></span>  
  
- <span data-ttu-id="e4e6d-107">Alt öğeleri olan öğeler</span><span class="sxs-lookup"><span data-stu-id="e4e6d-107">Elements with child elements</span></span>  
  
- <span data-ttu-id="e4e6d-108">Yinelenen öğeler</span><span class="sxs-lookup"><span data-stu-id="e4e6d-108">Repeating elements</span></span>  
  
## <a name="elements-with-attributes"></a><span data-ttu-id="e4e6d-109">Öznitelikleri olan öğeler</span><span class="sxs-lookup"><span data-stu-id="e4e6d-109">Elements with Attributes</span></span>  

 <span data-ttu-id="e4e6d-110">Üzerlerinde belirtilen öznitelikleri olan öğeler, çıkartılan tablolarla sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="e4e6d-110">Elements that have attributes specified in them result in inferred tables.</span></span> <span data-ttu-id="e4e6d-111">Örneğin, aşağıdaki XML 'i göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="e4e6d-111">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1"/>  
  <Element1 attr1="value2">Text1</Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="e4e6d-112">Çıkarım işlemi, "Element1" adlı bir tablo oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e4e6d-112">The inference process produces a table named "Element1."</span></span>  
  
 <span data-ttu-id="e4e6d-113">**Veri kümesi:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="e4e6d-113">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="e4e6d-114">**Tablo:** Element1</span><span class="sxs-lookup"><span data-stu-id="e4e6d-114">**Table:** Element1</span></span>  
  
|<span data-ttu-id="e4e6d-115">attr1</span><span class="sxs-lookup"><span data-stu-id="e4e6d-115">attr1</span></span>|<span data-ttu-id="e4e6d-116">Element1_Text</span><span class="sxs-lookup"><span data-stu-id="e4e6d-116">Element1_Text</span></span>|  
|-----------|--------------------|  
|<span data-ttu-id="e4e6d-117">value1</span><span class="sxs-lookup"><span data-stu-id="e4e6d-117">value1</span></span>||  
|<span data-ttu-id="e4e6d-118">value2</span><span class="sxs-lookup"><span data-stu-id="e4e6d-118">value2</span></span>|<span data-ttu-id="e4e6d-119">Text1</span><span class="sxs-lookup"><span data-stu-id="e4e6d-119">Text1</span></span>|  
  
## <a name="elements-with-child-elements"></a><span data-ttu-id="e4e6d-120">Alt öğeleri olan öğeler</span><span class="sxs-lookup"><span data-stu-id="e4e6d-120">Elements with Child Elements</span></span>  

 <span data-ttu-id="e4e6d-121">Alt öğeleri olan öğeler, çıkarılan tablolara neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="e4e6d-121">Elements that have child elements result in inferred tables.</span></span> <span data-ttu-id="e4e6d-122">Örneğin, aşağıdaki XML 'i göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="e4e6d-122">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>  
    <ChildElement1>Text1</ChildElement1>  
  </Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="e4e6d-123">Çıkarım işlemi, "Element1" adlı bir tablo oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e4e6d-123">The inference process produces a table named "Element1."</span></span>  
  
 <span data-ttu-id="e4e6d-124">**Veri kümesi:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="e4e6d-124">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="e4e6d-125">**Tablo:** Element1</span><span class="sxs-lookup"><span data-stu-id="e4e6d-125">**Table:** Element1</span></span>  
  
|<span data-ttu-id="e4e6d-126">ChildElement1</span><span class="sxs-lookup"><span data-stu-id="e4e6d-126">ChildElement1</span></span>|  
|-------------------|  
|<span data-ttu-id="e4e6d-127">Text1</span><span class="sxs-lookup"><span data-stu-id="e4e6d-127">Text1</span></span>|  
  
 <span data-ttu-id="e4e6d-128">Belge veya kök öğe, sütun olarak gösterilen öznitelikler veya alt öğeler içeriyorsa, çıkarılan bir tabloyla sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="e4e6d-128">The document, or root, element result in an inferred table if it has attributes or child elements that are inferred as columns.</span></span> <span data-ttu-id="e4e6d-129">Belge öğesinin hiç özniteliği yoksa ve sütun olarak çıkarsanmayacak alt öğe yoksa, öğe bir **veri kümesi** olarak algılanır.</span><span class="sxs-lookup"><span data-stu-id="e4e6d-129">If the document element has no attributes and no child elements that would be inferred as columns, the element is inferred as a **DataSet**.</span></span> <span data-ttu-id="e4e6d-130">Örneğin, aşağıdaki XML 'i göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="e4e6d-130">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
  <Element2>Text2</Element2>  
</DocumentElement>  
```  
  
 <span data-ttu-id="e4e6d-131">Çıkarım işlemi, "DocumentElement" adlı bir tablo oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e4e6d-131">The inference process produces a table named "DocumentElement."</span></span>  
  
 <span data-ttu-id="e4e6d-132">**Veri kümesi:** NewDataSet</span><span class="sxs-lookup"><span data-stu-id="e4e6d-132">**DataSet:** NewDataSet</span></span>  
  
 <span data-ttu-id="e4e6d-133">**Tablo:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="e4e6d-133">**Table:** DocumentElement</span></span>  
  
|<span data-ttu-id="e4e6d-134">Element1</span><span class="sxs-lookup"><span data-stu-id="e4e6d-134">Element1</span></span>|<span data-ttu-id="e4e6d-135">Element2</span><span class="sxs-lookup"><span data-stu-id="e4e6d-135">Element2</span></span>|  
|--------------|--------------|  
|<span data-ttu-id="e4e6d-136">Text1</span><span class="sxs-lookup"><span data-stu-id="e4e6d-136">Text1</span></span>|<span data-ttu-id="e4e6d-137">Metin2</span><span class="sxs-lookup"><span data-stu-id="e4e6d-137">Text2</span></span>|  
  
 <span data-ttu-id="e4e6d-138">Alternatif olarak, aşağıdaki XML 'i göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="e4e6d-138">Alternatively, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1" attr2="value2"/>  
</DocumentElement>  
```  
  
 <span data-ttu-id="e4e6d-139">Çıkarım işlemi, "Element1" adlı bir tablo içeren "DocumentElement" adlı bir **veri kümesi** oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e4e6d-139">The inference process produces a **DataSet** named "DocumentElement" that contains a table named "Element1."</span></span>  
  
 <span data-ttu-id="e4e6d-140">**Veri kümesi:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="e4e6d-140">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="e4e6d-141">**Tablo:** Element1</span><span class="sxs-lookup"><span data-stu-id="e4e6d-141">**Table:** Element1</span></span>  
  
|<span data-ttu-id="e4e6d-142">attr1</span><span class="sxs-lookup"><span data-stu-id="e4e6d-142">attr1</span></span>|<span data-ttu-id="e4e6d-143">attr2</span><span class="sxs-lookup"><span data-stu-id="e4e6d-143">attr2</span></span>|  
|-----------|-----------|  
|<span data-ttu-id="e4e6d-144">value1</span><span class="sxs-lookup"><span data-stu-id="e4e6d-144">value1</span></span>|<span data-ttu-id="e4e6d-145">value2</span><span class="sxs-lookup"><span data-stu-id="e4e6d-145">value2</span></span>|  
  
## <a name="repeating-elements"></a><span data-ttu-id="e4e6d-146">Yinelenen öğeler</span><span class="sxs-lookup"><span data-stu-id="e4e6d-146">Repeating Elements</span></span>  

 <span data-ttu-id="e4e6d-147">Yinelenen öğeler, ortaya çıkarılan tek bir tabloyla sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="e4e6d-147">Elements that repeat result in a single inferred table.</span></span> <span data-ttu-id="e4e6d-148">Örneğin, aşağıdaki XML 'i göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="e4e6d-148">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
  <Element1>Text2</Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="e4e6d-149">Çıkarım işlemi, "Element1" adlı bir tablo oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e4e6d-149">The inference process produces a table named "Element1."</span></span>  
  
 <span data-ttu-id="e4e6d-150">**Veri kümesi:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="e4e6d-150">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="e4e6d-151">**Tablo:** Element1</span><span class="sxs-lookup"><span data-stu-id="e4e6d-151">**Table:** Element1</span></span>  
  
|<span data-ttu-id="e4e6d-152">Element1_Text</span><span class="sxs-lookup"><span data-stu-id="e4e6d-152">Element1_Text</span></span>|  
|--------------------|  
|<span data-ttu-id="e4e6d-153">Text1</span><span class="sxs-lookup"><span data-stu-id="e4e6d-153">Text1</span></span>|  
|<span data-ttu-id="e4e6d-154">Metin2</span><span class="sxs-lookup"><span data-stu-id="e4e6d-154">Text2</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e4e6d-155">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e4e6d-155">See also</span></span>

- [<span data-ttu-id="e4e6d-156">XML’den DataSet İlişkisel Yapısını Çıkarma</span><span class="sxs-lookup"><span data-stu-id="e4e6d-156">Inferring DataSet Relational Structure from XML</span></span>](inferring-dataset-relational-structure-from-xml.md)
- [<span data-ttu-id="e4e6d-157">XML’den DataSet Yükleme</span><span class="sxs-lookup"><span data-stu-id="e4e6d-157">Loading a DataSet from XML</span></span>](loading-a-dataset-from-xml.md)
- [<span data-ttu-id="e4e6d-158">XML’den DataSet Schema Bilgilerini Yükleme</span><span class="sxs-lookup"><span data-stu-id="e4e6d-158">Loading DataSet Schema Information from XML</span></span>](loading-dataset-schema-information-from-xml.md)
- [<span data-ttu-id="e4e6d-159">DataSet içinde XML kullanma</span><span class="sxs-lookup"><span data-stu-id="e4e6d-159">Using XML in a DataSet</span></span>](using-xml-in-a-dataset.md)
- [<span data-ttu-id="e4e6d-160">DataSets, DataTables ve DataViews</span><span class="sxs-lookup"><span data-stu-id="e4e6d-160">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="e4e6d-161">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="e4e6d-161">ADO.NET Overview</span></span>](../ado-net-overview.md)
