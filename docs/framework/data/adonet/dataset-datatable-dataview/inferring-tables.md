---
title: Tabloların Çıkarımını Yapma
ms.date: 03/30/2017
ms.assetid: 74a288d4-b8e9-4f1a-b2cd-10df92c1ed1f
ms.openlocfilehash: 4a3d7b239dbc405cf2acae967b5be401dc772e38
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91177559"
---
# <a name="inferring-tables"></a><span data-ttu-id="b2850-102">Tabloların Çıkarımını Yapma</span><span class="sxs-lookup"><span data-stu-id="b2850-102">Inferring Tables</span></span>

<span data-ttu-id="b2850-103">Bir XML belgesinden bir şemayı kullanırken <xref:System.Data.DataSet> , ADO.net ilk olarak tabloları temsil eden XML öğelerini belirler.</span><span class="sxs-lookup"><span data-stu-id="b2850-103">When inferring a schema for a <xref:System.Data.DataSet> from an XML document, ADO.NET first determines which XML elements represent tables.</span></span> <span data-ttu-id="b2850-104">Aşağıdaki XML yapıları **veri kümesi** şemasının bir tablosu ile sonuçlanır:</span><span class="sxs-lookup"><span data-stu-id="b2850-104">The following XML structures result in a table for the **DataSet** schema:</span></span>  
  
- <span data-ttu-id="b2850-105">Öznitelikleri olan öğeler</span><span class="sxs-lookup"><span data-stu-id="b2850-105">Elements with attributes</span></span>  
  
- <span data-ttu-id="b2850-106">Alt öğeleri olan öğeler</span><span class="sxs-lookup"><span data-stu-id="b2850-106">Elements with child elements</span></span>  
  
- <span data-ttu-id="b2850-107">Yinelenen öğeler</span><span class="sxs-lookup"><span data-stu-id="b2850-107">Repeating elements</span></span>  
  
## <a name="elements-with-attributes"></a><span data-ttu-id="b2850-108">Öznitelikleri olan öğeler</span><span class="sxs-lookup"><span data-stu-id="b2850-108">Elements with Attributes</span></span>  

 <span data-ttu-id="b2850-109">Üzerlerinde belirtilen öznitelikleri olan öğeler, çıkartılan tablolarla sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="b2850-109">Elements that have attributes specified in them result in inferred tables.</span></span> <span data-ttu-id="b2850-110">Örneğin, aşağıdaki XML 'i göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="b2850-110">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1"/>  
  <Element1 attr1="value2">Text1</Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="b2850-111">Çıkarım işlemi, "Element1" adlı bir tablo oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b2850-111">The inference process produces a table named "Element1."</span></span>  
  
 <span data-ttu-id="b2850-112">**Veri kümesi:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="b2850-112">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="b2850-113">**Tablo:** Element1</span><span class="sxs-lookup"><span data-stu-id="b2850-113">**Table:** Element1</span></span>  
  
|<span data-ttu-id="b2850-114">attr1</span><span class="sxs-lookup"><span data-stu-id="b2850-114">attr1</span></span>|<span data-ttu-id="b2850-115">Element1_Text</span><span class="sxs-lookup"><span data-stu-id="b2850-115">Element1_Text</span></span>|  
|-----------|--------------------|  
|<span data-ttu-id="b2850-116">value1</span><span class="sxs-lookup"><span data-stu-id="b2850-116">value1</span></span>||  
|<span data-ttu-id="b2850-117">value2</span><span class="sxs-lookup"><span data-stu-id="b2850-117">value2</span></span>|<span data-ttu-id="b2850-118">Text1</span><span class="sxs-lookup"><span data-stu-id="b2850-118">Text1</span></span>|  
  
## <a name="elements-with-child-elements"></a><span data-ttu-id="b2850-119">Alt öğeleri olan öğeler</span><span class="sxs-lookup"><span data-stu-id="b2850-119">Elements with Child Elements</span></span>  

 <span data-ttu-id="b2850-120">Alt öğeleri olan öğeler, çıkarılan tablolara neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="b2850-120">Elements that have child elements result in inferred tables.</span></span> <span data-ttu-id="b2850-121">Örneğin, aşağıdaki XML 'i göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="b2850-121">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>  
    <ChildElement1>Text1</ChildElement1>  
  </Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="b2850-122">Çıkarım işlemi, "Element1" adlı bir tablo oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b2850-122">The inference process produces a table named "Element1."</span></span>  
  
 <span data-ttu-id="b2850-123">**Veri kümesi:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="b2850-123">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="b2850-124">**Tablo:** Element1</span><span class="sxs-lookup"><span data-stu-id="b2850-124">**Table:** Element1</span></span>  
  
|<span data-ttu-id="b2850-125">ChildElement1</span><span class="sxs-lookup"><span data-stu-id="b2850-125">ChildElement1</span></span>|  
|-------------------|  
|<span data-ttu-id="b2850-126">Text1</span><span class="sxs-lookup"><span data-stu-id="b2850-126">Text1</span></span>|  
  
 <span data-ttu-id="b2850-127">Belge veya kök öğe, sütun olarak gösterilen öznitelikler veya alt öğeler içeriyorsa, çıkarılan bir tabloyla sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="b2850-127">The document, or root, element result in an inferred table if it has attributes or child elements that are inferred as columns.</span></span> <span data-ttu-id="b2850-128">Belge öğesinin hiç özniteliği yoksa ve sütun olarak çıkarsanmayacak alt öğe yoksa, öğe bir **veri kümesi**olarak algılanır.</span><span class="sxs-lookup"><span data-stu-id="b2850-128">If the document element has no attributes and no child elements that would be inferred as columns, the element is inferred as a **DataSet**.</span></span> <span data-ttu-id="b2850-129">Örneğin, aşağıdaki XML 'i göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="b2850-129">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
  <Element2>Text2</Element2>  
</DocumentElement>  
```  
  
 <span data-ttu-id="b2850-130">Çıkarım işlemi, "DocumentElement" adlı bir tablo oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b2850-130">The inference process produces a table named "DocumentElement."</span></span>  
  
 <span data-ttu-id="b2850-131">**Veri kümesi:** NewDataSet</span><span class="sxs-lookup"><span data-stu-id="b2850-131">**DataSet:** NewDataSet</span></span>  
  
 <span data-ttu-id="b2850-132">**Tablo:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="b2850-132">**Table:** DocumentElement</span></span>  
  
|<span data-ttu-id="b2850-133">Element1</span><span class="sxs-lookup"><span data-stu-id="b2850-133">Element1</span></span>|<span data-ttu-id="b2850-134">Element2</span><span class="sxs-lookup"><span data-stu-id="b2850-134">Element2</span></span>|  
|--------------|--------------|  
|<span data-ttu-id="b2850-135">Text1</span><span class="sxs-lookup"><span data-stu-id="b2850-135">Text1</span></span>|<span data-ttu-id="b2850-136">Metin2</span><span class="sxs-lookup"><span data-stu-id="b2850-136">Text2</span></span>|  
  
 <span data-ttu-id="b2850-137">Alternatif olarak, aşağıdaki XML 'i göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="b2850-137">Alternatively, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1" attr2="value2"/>  
</DocumentElement>  
```  
  
 <span data-ttu-id="b2850-138">Çıkarım işlemi, "Element1" adlı bir tablo içeren "DocumentElement" adlı bir **veri kümesi** oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b2850-138">The inference process produces a **DataSet** named "DocumentElement" that contains a table named "Element1."</span></span>  
  
 <span data-ttu-id="b2850-139">**Veri kümesi:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="b2850-139">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="b2850-140">**Tablo:** Element1</span><span class="sxs-lookup"><span data-stu-id="b2850-140">**Table:** Element1</span></span>  
  
|<span data-ttu-id="b2850-141">attr1</span><span class="sxs-lookup"><span data-stu-id="b2850-141">attr1</span></span>|<span data-ttu-id="b2850-142">attr2</span><span class="sxs-lookup"><span data-stu-id="b2850-142">attr2</span></span>|  
|-----------|-----------|  
|<span data-ttu-id="b2850-143">value1</span><span class="sxs-lookup"><span data-stu-id="b2850-143">value1</span></span>|<span data-ttu-id="b2850-144">value2</span><span class="sxs-lookup"><span data-stu-id="b2850-144">value2</span></span>|  
  
## <a name="repeating-elements"></a><span data-ttu-id="b2850-145">Yinelenen öğeler</span><span class="sxs-lookup"><span data-stu-id="b2850-145">Repeating Elements</span></span>  

 <span data-ttu-id="b2850-146">Yinelenen öğeler, ortaya çıkarılan tek bir tabloyla sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="b2850-146">Elements that repeat result in a single inferred table.</span></span> <span data-ttu-id="b2850-147">Örneğin, aşağıdaki XML 'i göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="b2850-147">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
  <Element1>Text2</Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="b2850-148">Çıkarım işlemi, "Element1" adlı bir tablo oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b2850-148">The inference process produces a table named "Element1."</span></span>  
  
 <span data-ttu-id="b2850-149">**Veri kümesi:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="b2850-149">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="b2850-150">**Tablo:** Element1</span><span class="sxs-lookup"><span data-stu-id="b2850-150">**Table:** Element1</span></span>  
  
|<span data-ttu-id="b2850-151">Element1_Text</span><span class="sxs-lookup"><span data-stu-id="b2850-151">Element1_Text</span></span>|  
|--------------------|  
|<span data-ttu-id="b2850-152">Text1</span><span class="sxs-lookup"><span data-stu-id="b2850-152">Text1</span></span>|  
|<span data-ttu-id="b2850-153">Metin2</span><span class="sxs-lookup"><span data-stu-id="b2850-153">Text2</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b2850-154">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b2850-154">See also</span></span>

- [<span data-ttu-id="b2850-155">XML’den DataSet İlişkisel Yapısını Çıkarma</span><span class="sxs-lookup"><span data-stu-id="b2850-155">Inferring DataSet Relational Structure from XML</span></span>](inferring-dataset-relational-structure-from-xml.md)
- [<span data-ttu-id="b2850-156">XML’den DataSet Yükleme</span><span class="sxs-lookup"><span data-stu-id="b2850-156">Loading a DataSet from XML</span></span>](loading-a-dataset-from-xml.md)
- [<span data-ttu-id="b2850-157">XML’den DataSet Schema Bilgilerini Yükleme</span><span class="sxs-lookup"><span data-stu-id="b2850-157">Loading DataSet Schema Information from XML</span></span>](loading-dataset-schema-information-from-xml.md)
- [<span data-ttu-id="b2850-158">DataSet içinde XML kullanma</span><span class="sxs-lookup"><span data-stu-id="b2850-158">Using XML in a DataSet</span></span>](using-xml-in-a-dataset.md)
- [<span data-ttu-id="b2850-159">DataSets, DataTables ve DataViews</span><span class="sxs-lookup"><span data-stu-id="b2850-159">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="b2850-160">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="b2850-160">ADO.NET Overview</span></span>](../ado-net-overview.md)
