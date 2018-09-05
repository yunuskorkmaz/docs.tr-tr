---
title: Tabloların çıkarımını yapma
ms.date: 03/30/2017
ms.assetid: 74a288d4-b8e9-4f1a-b2cd-10df92c1ed1f
ms.openlocfilehash: 38709f91e01c7f85d9e8482bdd49bc0892121f09
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43528178"
---
# <a name="inferring-tables"></a><span data-ttu-id="14175-102">Tabloların çıkarımını yapma</span><span class="sxs-lookup"><span data-stu-id="14175-102">Inferring Tables</span></span>
<span data-ttu-id="14175-103">İçin bir şema çıkarımını yapma sırasında bir <xref:System.Data.DataSet> tablolar XML öğeleri temsil eden önce bir XML belgesinden ADO.NET belirler.</span><span class="sxs-lookup"><span data-stu-id="14175-103">When inferring a schema for a <xref:System.Data.DataSet> from an XML document, ADO.NET first determines which XML elements represent tables.</span></span> <span data-ttu-id="14175-104">Aşağıdaki XML yapıları için bir tabloyu neden **veri kümesi** şema:</span><span class="sxs-lookup"><span data-stu-id="14175-104">The following XML structures result in a table for the **DataSet** schema:</span></span>  
  
-   <span data-ttu-id="14175-105">Öznitelikleri olan öğeleri</span><span class="sxs-lookup"><span data-stu-id="14175-105">Elements with attributes</span></span>  
  
-   <span data-ttu-id="14175-106">Alt öğelerini</span><span class="sxs-lookup"><span data-stu-id="14175-106">Elements with child elements</span></span>  
  
-   <span data-ttu-id="14175-107">Yinelenen öğeleri</span><span class="sxs-lookup"><span data-stu-id="14175-107">Repeating elements</span></span>  
  
## <a name="elements-with-attributes"></a><span data-ttu-id="14175-108">Öznitelikleri olan öğeleri</span><span class="sxs-lookup"><span data-stu-id="14175-108">Elements with Attributes</span></span>  
 <span data-ttu-id="14175-109">İçinde belirtilen öznitelikler neden olan öğeler tabloları sonuçlandı.</span><span class="sxs-lookup"><span data-stu-id="14175-109">Elements that have attributes specified in them result in inferred tables.</span></span> <span data-ttu-id="14175-110">Örneğin, aşağıdaki XML göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="14175-110">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1"/>  
  <Element1 attr1="value2">Text1</Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="14175-111">Çıkarma işlemi "Element1." adlı bir tablo oluşturur</span><span class="sxs-lookup"><span data-stu-id="14175-111">The inference process produces a table named "Element1."</span></span>  
  
 <span data-ttu-id="14175-112">**Veri kümesi:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="14175-112">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="14175-113">**Tablo:** Element1</span><span class="sxs-lookup"><span data-stu-id="14175-113">**Table:** Element1</span></span>  
  
|<span data-ttu-id="14175-114">attr1</span><span class="sxs-lookup"><span data-stu-id="14175-114">attr1</span></span>|<span data-ttu-id="14175-115">Element1_Text</span><span class="sxs-lookup"><span data-stu-id="14175-115">Element1_Text</span></span>|  
|-----------|--------------------|  
|<span data-ttu-id="14175-116">Değer1</span><span class="sxs-lookup"><span data-stu-id="14175-116">value1</span></span>||  
|<span data-ttu-id="14175-117">Value2</span><span class="sxs-lookup"><span data-stu-id="14175-117">value2</span></span>|<span data-ttu-id="14175-118">text1</span><span class="sxs-lookup"><span data-stu-id="14175-118">Text1</span></span>|  
  
## <a name="elements-with-child-elements"></a><span data-ttu-id="14175-119">Alt öğelerini</span><span class="sxs-lookup"><span data-stu-id="14175-119">Elements with Child Elements</span></span>  
 <span data-ttu-id="14175-120">Alt öğeleri sonucu olmayan öğeler tabloları sonuçlandı.</span><span class="sxs-lookup"><span data-stu-id="14175-120">Elements that have child elements result in inferred tables.</span></span> <span data-ttu-id="14175-121">Örneğin, aşağıdaki XML göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="14175-121">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>  
    <ChildElement1>Text1</ChildElement1>  
  </Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="14175-122">Çıkarma işlemi "Element1." adlı bir tablo oluşturur</span><span class="sxs-lookup"><span data-stu-id="14175-122">The inference process produces a table named "Element1."</span></span>  
  
 <span data-ttu-id="14175-123">**Veri kümesi:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="14175-123">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="14175-124">**Tablo:** Element1</span><span class="sxs-lookup"><span data-stu-id="14175-124">**Table:** Element1</span></span>  
  
|<span data-ttu-id="14175-125">ChildElement1</span><span class="sxs-lookup"><span data-stu-id="14175-125">ChildElement1</span></span>|  
|-------------------|  
|<span data-ttu-id="14175-126">text1</span><span class="sxs-lookup"><span data-stu-id="14175-126">Text1</span></span>|  
  
 <span data-ttu-id="14175-127">Belge veya kök öğe sonucu çıkarsanan tabloda öznitelikleri veya sütun olarak algılanır alt öğeleri varsa.</span><span class="sxs-lookup"><span data-stu-id="14175-127">The document, or root, element result in an inferred table if it has attributes or child elements that are inferred as columns.</span></span> <span data-ttu-id="14175-128">Belge öğesi özniteliklere ve sütun olarak çıkarılan hiçbir alt öğeleri varsa öğe olarak algılanır bir **veri kümesi**.</span><span class="sxs-lookup"><span data-stu-id="14175-128">If the document element has no attributes and no child elements that would be inferred as columns, the element is inferred as a **DataSet**.</span></span> <span data-ttu-id="14175-129">Örneğin, aşağıdaki XML göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="14175-129">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
  <Element2>Text2</Element2>  
</DocumentElement>  
```  
  
 <span data-ttu-id="14175-130">Çıkarma işlemi "DocumentElement." adlı bir tablo oluşturur</span><span class="sxs-lookup"><span data-stu-id="14175-130">The inference process produces a table named "DocumentElement."</span></span>  
  
 <span data-ttu-id="14175-131">**Veri kümesi:** NewDataSet</span><span class="sxs-lookup"><span data-stu-id="14175-131">**DataSet:** NewDataSet</span></span>  
  
 <span data-ttu-id="14175-132">**Tablo:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="14175-132">**Table:** DocumentElement</span></span>  
  
|<span data-ttu-id="14175-133">element1</span><span class="sxs-lookup"><span data-stu-id="14175-133">Element1</span></span>|<span data-ttu-id="14175-134">element2</span><span class="sxs-lookup"><span data-stu-id="14175-134">Element2</span></span>|  
|--------------|--------------|  
|<span data-ttu-id="14175-135">text1</span><span class="sxs-lookup"><span data-stu-id="14175-135">Text1</span></span>|<span data-ttu-id="14175-136">Text2</span><span class="sxs-lookup"><span data-stu-id="14175-136">Text2</span></span>|  
  
 <span data-ttu-id="14175-137">Alternatif olarak, aşağıdaki XML göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="14175-137">Alternatively, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1" attr2="value2"/>  
</DocumentElement>  
```  
  
 <span data-ttu-id="14175-138">Çıkarma işlemi ürettiği bir **veri kümesi** "" Element1."adlı bir tablo içeren DocumentElement" adlı</span><span class="sxs-lookup"><span data-stu-id="14175-138">The inference process produces a **DataSet** named "DocumentElement" that contains a table named "Element1."</span></span>  
  
 <span data-ttu-id="14175-139">**Veri kümesi:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="14175-139">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="14175-140">**Tablo:** Element1</span><span class="sxs-lookup"><span data-stu-id="14175-140">**Table:** Element1</span></span>  
  
|<span data-ttu-id="14175-141">attr1</span><span class="sxs-lookup"><span data-stu-id="14175-141">attr1</span></span>|<span data-ttu-id="14175-142">attr2</span><span class="sxs-lookup"><span data-stu-id="14175-142">attr2</span></span>|  
|-----------|-----------|  
|<span data-ttu-id="14175-143">Değer1</span><span class="sxs-lookup"><span data-stu-id="14175-143">value1</span></span>|<span data-ttu-id="14175-144">Value2</span><span class="sxs-lookup"><span data-stu-id="14175-144">value2</span></span>|  
  
## <a name="repeating-elements"></a><span data-ttu-id="14175-145">Yinelenen öğeleri</span><span class="sxs-lookup"><span data-stu-id="14175-145">Repeating Elements</span></span>  
 <span data-ttu-id="14175-146">Tek bir çıkarsanan tablosundaki sonuç yineleyin öğeleri.</span><span class="sxs-lookup"><span data-stu-id="14175-146">Elements that repeat result in a single inferred table.</span></span> <span data-ttu-id="14175-147">Örneğin, aşağıdaki XML göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="14175-147">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
  <Element1>Text2</Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="14175-148">Çıkarma işlemi "Element1." adlı bir tablo oluşturur</span><span class="sxs-lookup"><span data-stu-id="14175-148">The inference process produces a table named "Element1."</span></span>  
  
 <span data-ttu-id="14175-149">**Veri kümesi:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="14175-149">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="14175-150">**Tablo:** Element1</span><span class="sxs-lookup"><span data-stu-id="14175-150">**Table:** Element1</span></span>  
  
|<span data-ttu-id="14175-151">Element1_Text</span><span class="sxs-lookup"><span data-stu-id="14175-151">Element1_Text</span></span>|  
|--------------------|  
|<span data-ttu-id="14175-152">text1</span><span class="sxs-lookup"><span data-stu-id="14175-152">Text1</span></span>|  
|<span data-ttu-id="14175-153">Text2</span><span class="sxs-lookup"><span data-stu-id="14175-153">Text2</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="14175-154">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="14175-154">See Also</span></span>  
 [<span data-ttu-id="14175-155">XML’den DataSet İlişkisel Yapısını Çıkarma</span><span class="sxs-lookup"><span data-stu-id="14175-155">Inferring DataSet Relational Structure from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)  
 [<span data-ttu-id="14175-156">XML’den DataSet Yükleme</span><span class="sxs-lookup"><span data-stu-id="14175-156">Loading a DataSet from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)  
 [<span data-ttu-id="14175-157">XML’den DataSet Schema Bilgilerini Yükleme</span><span class="sxs-lookup"><span data-stu-id="14175-157">Loading DataSet Schema Information from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)  
 [<span data-ttu-id="14175-158">DataSet içinde XML kullanma</span><span class="sxs-lookup"><span data-stu-id="14175-158">Using XML in a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [<span data-ttu-id="14175-159">DataSets, DataTables ve DataViews</span><span class="sxs-lookup"><span data-stu-id="14175-159">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="14175-160">ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="14175-160">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
