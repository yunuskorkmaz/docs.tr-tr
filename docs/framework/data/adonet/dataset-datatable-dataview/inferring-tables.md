---
title: Tabloların Çıkarımını Yapma
ms.date: 03/30/2017
ms.assetid: 74a288d4-b8e9-4f1a-b2cd-10df92c1ed1f
ms.openlocfilehash: 84cee828f2d3c918a12e449da5b01a3d72d86333
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70203522"
---
# <a name="inferring-tables"></a><span data-ttu-id="b5f76-102">Tabloların Çıkarımını Yapma</span><span class="sxs-lookup"><span data-stu-id="b5f76-102">Inferring Tables</span></span>
<span data-ttu-id="b5f76-103">Bir XML belgesinden bir <xref:System.Data.DataSet> şemayı kullanırken, ADO.net ilk olarak tabloları temsil eden XML öğelerini belirler.</span><span class="sxs-lookup"><span data-stu-id="b5f76-103">When inferring a schema for a <xref:System.Data.DataSet> from an XML document, ADO.NET first determines which XML elements represent tables.</span></span> <span data-ttu-id="b5f76-104">Aşağıdaki XML yapıları **veri kümesi** şemasının bir tablosu ile sonuçlanır:</span><span class="sxs-lookup"><span data-stu-id="b5f76-104">The following XML structures result in a table for the **DataSet** schema:</span></span>  
  
- <span data-ttu-id="b5f76-105">Öznitelikleri olan öğeler</span><span class="sxs-lookup"><span data-stu-id="b5f76-105">Elements with attributes</span></span>  
  
- <span data-ttu-id="b5f76-106">Alt öğeleri olan öğeler</span><span class="sxs-lookup"><span data-stu-id="b5f76-106">Elements with child elements</span></span>  
  
- <span data-ttu-id="b5f76-107">Yinelenen öğeler</span><span class="sxs-lookup"><span data-stu-id="b5f76-107">Repeating elements</span></span>  
  
## <a name="elements-with-attributes"></a><span data-ttu-id="b5f76-108">Öznitelikleri olan öğeler</span><span class="sxs-lookup"><span data-stu-id="b5f76-108">Elements with Attributes</span></span>  
 <span data-ttu-id="b5f76-109">Üzerlerinde belirtilen öznitelikleri olan öğeler, çıkartılan tablolarla sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="b5f76-109">Elements that have attributes specified in them result in inferred tables.</span></span> <span data-ttu-id="b5f76-110">Örneğin, aşağıdaki XML 'i göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="b5f76-110">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1"/>  
  <Element1 attr1="value2">Text1</Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="b5f76-111">Çıkarım işlemi, "Element1" adlı bir tablo oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b5f76-111">The inference process produces a table named "Element1."</span></span>  
  
 <span data-ttu-id="b5f76-112">**Veri kümesi** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="b5f76-112">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="b5f76-113">**Tablosundan** Element1</span><span class="sxs-lookup"><span data-stu-id="b5f76-113">**Table:** Element1</span></span>  
  
|<span data-ttu-id="b5f76-114">attr1</span><span class="sxs-lookup"><span data-stu-id="b5f76-114">attr1</span></span>|<span data-ttu-id="b5f76-115">Element1_Text</span><span class="sxs-lookup"><span data-stu-id="b5f76-115">Element1_Text</span></span>|  
|-----------|--------------------|  
|<span data-ttu-id="b5f76-116">value1</span><span class="sxs-lookup"><span data-stu-id="b5f76-116">value1</span></span>||  
|<span data-ttu-id="b5f76-117">value2</span><span class="sxs-lookup"><span data-stu-id="b5f76-117">value2</span></span>|<span data-ttu-id="b5f76-118">Text1</span><span class="sxs-lookup"><span data-stu-id="b5f76-118">Text1</span></span>|  
  
## <a name="elements-with-child-elements"></a><span data-ttu-id="b5f76-119">Alt öğeleri olan öğeler</span><span class="sxs-lookup"><span data-stu-id="b5f76-119">Elements with Child Elements</span></span>  
 <span data-ttu-id="b5f76-120">Alt öğeleri olan öğeler, çıkarılan tablolara neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="b5f76-120">Elements that have child elements result in inferred tables.</span></span> <span data-ttu-id="b5f76-121">Örneğin, aşağıdaki XML 'i göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="b5f76-121">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>  
    <ChildElement1>Text1</ChildElement1>  
  </Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="b5f76-122">Çıkarım işlemi, "Element1" adlı bir tablo oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b5f76-122">The inference process produces a table named "Element1."</span></span>  
  
 <span data-ttu-id="b5f76-123">**Veri kümesi** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="b5f76-123">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="b5f76-124">**Tablosundan** Element1</span><span class="sxs-lookup"><span data-stu-id="b5f76-124">**Table:** Element1</span></span>  
  
|<span data-ttu-id="b5f76-125">ChildElement1</span><span class="sxs-lookup"><span data-stu-id="b5f76-125">ChildElement1</span></span>|  
|-------------------|  
|<span data-ttu-id="b5f76-126">Text1</span><span class="sxs-lookup"><span data-stu-id="b5f76-126">Text1</span></span>|  
  
 <span data-ttu-id="b5f76-127">Belge veya kök öğe, sütun olarak gösterilen öznitelikler veya alt öğeler içeriyorsa, çıkarılan bir tabloyla sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="b5f76-127">The document, or root, element result in an inferred table if it has attributes or child elements that are inferred as columns.</span></span> <span data-ttu-id="b5f76-128">Belge öğesinin hiç özniteliği yoksa ve sütun olarak çıkarsanmayacak alt öğe yoksa, öğe bir **veri kümesi**olarak algılanır.</span><span class="sxs-lookup"><span data-stu-id="b5f76-128">If the document element has no attributes and no child elements that would be inferred as columns, the element is inferred as a **DataSet**.</span></span> <span data-ttu-id="b5f76-129">Örneğin, aşağıdaki XML 'i göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="b5f76-129">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
  <Element2>Text2</Element2>  
</DocumentElement>  
```  
  
 <span data-ttu-id="b5f76-130">Çıkarım işlemi, "DocumentElement" adlı bir tablo oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b5f76-130">The inference process produces a table named "DocumentElement."</span></span>  
  
 <span data-ttu-id="b5f76-131">**Veri kümesi** NewDataSet</span><span class="sxs-lookup"><span data-stu-id="b5f76-131">**DataSet:** NewDataSet</span></span>  
  
 <span data-ttu-id="b5f76-132">**Tablosundan** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="b5f76-132">**Table:** DocumentElement</span></span>  
  
|<span data-ttu-id="b5f76-133">Element1</span><span class="sxs-lookup"><span data-stu-id="b5f76-133">Element1</span></span>|<span data-ttu-id="b5f76-134">Element2</span><span class="sxs-lookup"><span data-stu-id="b5f76-134">Element2</span></span>|  
|--------------|--------------|  
|<span data-ttu-id="b5f76-135">Text1</span><span class="sxs-lookup"><span data-stu-id="b5f76-135">Text1</span></span>|<span data-ttu-id="b5f76-136">Metin2</span><span class="sxs-lookup"><span data-stu-id="b5f76-136">Text2</span></span>|  
  
 <span data-ttu-id="b5f76-137">Alternatif olarak, aşağıdaki XML 'i göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="b5f76-137">Alternatively, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1" attr2="value2"/>  
</DocumentElement>  
```  
  
 <span data-ttu-id="b5f76-138">Çıkarım işlemi, "Element1" adlı bir tablo içeren "DocumentElement" adlı bir **veri kümesi** oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b5f76-138">The inference process produces a **DataSet** named "DocumentElement" that contains a table named "Element1."</span></span>  
  
 <span data-ttu-id="b5f76-139">**Veri kümesi** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="b5f76-139">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="b5f76-140">**Tablosundan** Element1</span><span class="sxs-lookup"><span data-stu-id="b5f76-140">**Table:** Element1</span></span>  
  
|<span data-ttu-id="b5f76-141">attr1</span><span class="sxs-lookup"><span data-stu-id="b5f76-141">attr1</span></span>|<span data-ttu-id="b5f76-142">attr2</span><span class="sxs-lookup"><span data-stu-id="b5f76-142">attr2</span></span>|  
|-----------|-----------|  
|<span data-ttu-id="b5f76-143">value1</span><span class="sxs-lookup"><span data-stu-id="b5f76-143">value1</span></span>|<span data-ttu-id="b5f76-144">value2</span><span class="sxs-lookup"><span data-stu-id="b5f76-144">value2</span></span>|  
  
## <a name="repeating-elements"></a><span data-ttu-id="b5f76-145">Yinelenen öğeler</span><span class="sxs-lookup"><span data-stu-id="b5f76-145">Repeating Elements</span></span>  
 <span data-ttu-id="b5f76-146">Yinelenen öğeler, ortaya çıkarılan tek bir tabloyla sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="b5f76-146">Elements that repeat result in a single inferred table.</span></span> <span data-ttu-id="b5f76-147">Örneğin, aşağıdaki XML 'i göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="b5f76-147">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
  <Element1>Text2</Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="b5f76-148">Çıkarım işlemi, "Element1" adlı bir tablo oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b5f76-148">The inference process produces a table named "Element1."</span></span>  
  
 <span data-ttu-id="b5f76-149">**Veri kümesi** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="b5f76-149">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="b5f76-150">**Tablosundan** Element1</span><span class="sxs-lookup"><span data-stu-id="b5f76-150">**Table:** Element1</span></span>  
  
|<span data-ttu-id="b5f76-151">Element1_Text</span><span class="sxs-lookup"><span data-stu-id="b5f76-151">Element1_Text</span></span>|  
|--------------------|  
|<span data-ttu-id="b5f76-152">Text1</span><span class="sxs-lookup"><span data-stu-id="b5f76-152">Text1</span></span>|  
|<span data-ttu-id="b5f76-153">Metin2</span><span class="sxs-lookup"><span data-stu-id="b5f76-153">Text2</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b5f76-154">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b5f76-154">See also</span></span>

- [<span data-ttu-id="b5f76-155">XML’den DataSet İlişkisel Yapısını Çıkarma</span><span class="sxs-lookup"><span data-stu-id="b5f76-155">Inferring DataSet Relational Structure from XML</span></span>](inferring-dataset-relational-structure-from-xml.md)
- [<span data-ttu-id="b5f76-156">XML’den DataSet Yükleme</span><span class="sxs-lookup"><span data-stu-id="b5f76-156">Loading a DataSet from XML</span></span>](loading-a-dataset-from-xml.md)
- [<span data-ttu-id="b5f76-157">XML’den DataSet Schema Bilgilerini Yükleme</span><span class="sxs-lookup"><span data-stu-id="b5f76-157">Loading DataSet Schema Information from XML</span></span>](loading-dataset-schema-information-from-xml.md)
- [<span data-ttu-id="b5f76-158">DataSet içinde XML kullanma</span><span class="sxs-lookup"><span data-stu-id="b5f76-158">Using XML in a DataSet</span></span>](using-xml-in-a-dataset.md)
- [<span data-ttu-id="b5f76-159">DataSets, DataTables ve DataViews</span><span class="sxs-lookup"><span data-stu-id="b5f76-159">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="b5f76-160">ADO.NET yönetilen sağlayıcılar ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="b5f76-160">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
