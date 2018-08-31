---
title: Tabloların çıkarımını yapma
ms.date: 03/30/2017
ms.assetid: 74a288d4-b8e9-4f1a-b2cd-10df92c1ed1f
ms.openlocfilehash: 38709f91e01c7f85d9e8482bdd49bc0892121f09
ms.sourcegitcommit: a368166a51e5204c0224fbf5e46476e3ed122817
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/31/2018
ms.locfileid: "43332859"
---
# <a name="inferring-tables"></a><span data-ttu-id="b754b-102">Tabloların çıkarımını yapma</span><span class="sxs-lookup"><span data-stu-id="b754b-102">Inferring Tables</span></span>
<span data-ttu-id="b754b-103">İçin bir şema çıkarımını yapma sırasında bir <xref:System.Data.DataSet> tablolar XML öğeleri temsil eden önce bir XML belgesinden ADO.NET belirler.</span><span class="sxs-lookup"><span data-stu-id="b754b-103">When inferring a schema for a <xref:System.Data.DataSet> from an XML document, ADO.NET first determines which XML elements represent tables.</span></span> <span data-ttu-id="b754b-104">Aşağıdaki XML yapıları için bir tabloyu neden **veri kümesi** şema:</span><span class="sxs-lookup"><span data-stu-id="b754b-104">The following XML structures result in a table for the **DataSet** schema:</span></span>  
  
-   <span data-ttu-id="b754b-105">Öznitelikleri olan öğeleri</span><span class="sxs-lookup"><span data-stu-id="b754b-105">Elements with attributes</span></span>  
  
-   <span data-ttu-id="b754b-106">Alt öğelerini</span><span class="sxs-lookup"><span data-stu-id="b754b-106">Elements with child elements</span></span>  
  
-   <span data-ttu-id="b754b-107">Yinelenen öğeleri</span><span class="sxs-lookup"><span data-stu-id="b754b-107">Repeating elements</span></span>  
  
## <a name="elements-with-attributes"></a><span data-ttu-id="b754b-108">Öznitelikleri olan öğeleri</span><span class="sxs-lookup"><span data-stu-id="b754b-108">Elements with Attributes</span></span>  
 <span data-ttu-id="b754b-109">İçinde belirtilen öznitelikler neden olan öğeler tabloları sonuçlandı.</span><span class="sxs-lookup"><span data-stu-id="b754b-109">Elements that have attributes specified in them result in inferred tables.</span></span> <span data-ttu-id="b754b-110">Örneğin, aşağıdaki XML göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="b754b-110">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1"/>  
  <Element1 attr1="value2">Text1</Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="b754b-111">Çıkarma işlemi "Element1." adlı bir tablo oluşturur</span><span class="sxs-lookup"><span data-stu-id="b754b-111">The inference process produces a table named "Element1."</span></span>  
  
 <span data-ttu-id="b754b-112">**Veri kümesi:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="b754b-112">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="b754b-113">**Tablo:** Element1</span><span class="sxs-lookup"><span data-stu-id="b754b-113">**Table:** Element1</span></span>  
  
|<span data-ttu-id="b754b-114">attr1</span><span class="sxs-lookup"><span data-stu-id="b754b-114">attr1</span></span>|<span data-ttu-id="b754b-115">Element1_Text</span><span class="sxs-lookup"><span data-stu-id="b754b-115">Element1_Text</span></span>|  
|-----------|--------------------|  
|<span data-ttu-id="b754b-116">Değer1</span><span class="sxs-lookup"><span data-stu-id="b754b-116">value1</span></span>||  
|<span data-ttu-id="b754b-117">Value2</span><span class="sxs-lookup"><span data-stu-id="b754b-117">value2</span></span>|<span data-ttu-id="b754b-118">text1</span><span class="sxs-lookup"><span data-stu-id="b754b-118">Text1</span></span>|  
  
## <a name="elements-with-child-elements"></a><span data-ttu-id="b754b-119">Alt öğelerini</span><span class="sxs-lookup"><span data-stu-id="b754b-119">Elements with Child Elements</span></span>  
 <span data-ttu-id="b754b-120">Alt öğeleri sonucu olmayan öğeler tabloları sonuçlandı.</span><span class="sxs-lookup"><span data-stu-id="b754b-120">Elements that have child elements result in inferred tables.</span></span> <span data-ttu-id="b754b-121">Örneğin, aşağıdaki XML göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="b754b-121">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>  
    <ChildElement1>Text1</ChildElement1>  
  </Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="b754b-122">Çıkarma işlemi "Element1." adlı bir tablo oluşturur</span><span class="sxs-lookup"><span data-stu-id="b754b-122">The inference process produces a table named "Element1."</span></span>  
  
 <span data-ttu-id="b754b-123">**Veri kümesi:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="b754b-123">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="b754b-124">**Tablo:** Element1</span><span class="sxs-lookup"><span data-stu-id="b754b-124">**Table:** Element1</span></span>  
  
|<span data-ttu-id="b754b-125">ChildElement1</span><span class="sxs-lookup"><span data-stu-id="b754b-125">ChildElement1</span></span>|  
|-------------------|  
|<span data-ttu-id="b754b-126">text1</span><span class="sxs-lookup"><span data-stu-id="b754b-126">Text1</span></span>|  
  
 <span data-ttu-id="b754b-127">Belge veya kök öğe sonucu çıkarsanan tabloda öznitelikleri veya sütun olarak algılanır alt öğeleri varsa.</span><span class="sxs-lookup"><span data-stu-id="b754b-127">The document, or root, element result in an inferred table if it has attributes or child elements that are inferred as columns.</span></span> <span data-ttu-id="b754b-128">Belge öğesi özniteliklere ve sütun olarak çıkarılan hiçbir alt öğeleri varsa öğe olarak algılanır bir **veri kümesi**.</span><span class="sxs-lookup"><span data-stu-id="b754b-128">If the document element has no attributes and no child elements that would be inferred as columns, the element is inferred as a **DataSet**.</span></span> <span data-ttu-id="b754b-129">Örneğin, aşağıdaki XML göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="b754b-129">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
  <Element2>Text2</Element2>  
</DocumentElement>  
```  
  
 <span data-ttu-id="b754b-130">Çıkarma işlemi "DocumentElement." adlı bir tablo oluşturur</span><span class="sxs-lookup"><span data-stu-id="b754b-130">The inference process produces a table named "DocumentElement."</span></span>  
  
 <span data-ttu-id="b754b-131">**Veri kümesi:** NewDataSet</span><span class="sxs-lookup"><span data-stu-id="b754b-131">**DataSet:** NewDataSet</span></span>  
  
 <span data-ttu-id="b754b-132">**Tablo:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="b754b-132">**Table:** DocumentElement</span></span>  
  
|<span data-ttu-id="b754b-133">element1</span><span class="sxs-lookup"><span data-stu-id="b754b-133">Element1</span></span>|<span data-ttu-id="b754b-134">element2</span><span class="sxs-lookup"><span data-stu-id="b754b-134">Element2</span></span>|  
|--------------|--------------|  
|<span data-ttu-id="b754b-135">text1</span><span class="sxs-lookup"><span data-stu-id="b754b-135">Text1</span></span>|<span data-ttu-id="b754b-136">Text2</span><span class="sxs-lookup"><span data-stu-id="b754b-136">Text2</span></span>|  
  
 <span data-ttu-id="b754b-137">Alternatif olarak, aşağıdaki XML göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="b754b-137">Alternatively, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1" attr2="value2"/>  
</DocumentElement>  
```  
  
 <span data-ttu-id="b754b-138">Çıkarma işlemi ürettiği bir **veri kümesi** "" Element1."adlı bir tablo içeren DocumentElement" adlı</span><span class="sxs-lookup"><span data-stu-id="b754b-138">The inference process produces a **DataSet** named "DocumentElement" that contains a table named "Element1."</span></span>  
  
 <span data-ttu-id="b754b-139">**Veri kümesi:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="b754b-139">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="b754b-140">**Tablo:** Element1</span><span class="sxs-lookup"><span data-stu-id="b754b-140">**Table:** Element1</span></span>  
  
|<span data-ttu-id="b754b-141">attr1</span><span class="sxs-lookup"><span data-stu-id="b754b-141">attr1</span></span>|<span data-ttu-id="b754b-142">attr2</span><span class="sxs-lookup"><span data-stu-id="b754b-142">attr2</span></span>|  
|-----------|-----------|  
|<span data-ttu-id="b754b-143">Değer1</span><span class="sxs-lookup"><span data-stu-id="b754b-143">value1</span></span>|<span data-ttu-id="b754b-144">Value2</span><span class="sxs-lookup"><span data-stu-id="b754b-144">value2</span></span>|  
  
## <a name="repeating-elements"></a><span data-ttu-id="b754b-145">Yinelenen öğeleri</span><span class="sxs-lookup"><span data-stu-id="b754b-145">Repeating Elements</span></span>  
 <span data-ttu-id="b754b-146">Tek bir çıkarsanan tablosundaki sonuç yineleyin öğeleri.</span><span class="sxs-lookup"><span data-stu-id="b754b-146">Elements that repeat result in a single inferred table.</span></span> <span data-ttu-id="b754b-147">Örneğin, aşağıdaki XML göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="b754b-147">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
  <Element1>Text2</Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="b754b-148">Çıkarma işlemi "Element1." adlı bir tablo oluşturur</span><span class="sxs-lookup"><span data-stu-id="b754b-148">The inference process produces a table named "Element1."</span></span>  
  
 <span data-ttu-id="b754b-149">**Veri kümesi:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="b754b-149">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="b754b-150">**Tablo:** Element1</span><span class="sxs-lookup"><span data-stu-id="b754b-150">**Table:** Element1</span></span>  
  
|<span data-ttu-id="b754b-151">Element1_Text</span><span class="sxs-lookup"><span data-stu-id="b754b-151">Element1_Text</span></span>|  
|--------------------|  
|<span data-ttu-id="b754b-152">text1</span><span class="sxs-lookup"><span data-stu-id="b754b-152">Text1</span></span>|  
|<span data-ttu-id="b754b-153">Text2</span><span class="sxs-lookup"><span data-stu-id="b754b-153">Text2</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b754b-154">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b754b-154">See Also</span></span>  
 [<span data-ttu-id="b754b-155">XML’den DataSet İlişkisel Yapısını Çıkarma</span><span class="sxs-lookup"><span data-stu-id="b754b-155">Inferring DataSet Relational Structure from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)  
 [<span data-ttu-id="b754b-156">XML’den DataSet Yükleme</span><span class="sxs-lookup"><span data-stu-id="b754b-156">Loading a DataSet from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)  
 [<span data-ttu-id="b754b-157">XML’den DataSet Schema Bilgilerini Yükleme</span><span class="sxs-lookup"><span data-stu-id="b754b-157">Loading DataSet Schema Information from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)  
 [<span data-ttu-id="b754b-158">DataSet içinde XML kullanma</span><span class="sxs-lookup"><span data-stu-id="b754b-158">Using XML in a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [<span data-ttu-id="b754b-159">DataSets, DataTables ve DataViews</span><span class="sxs-lookup"><span data-stu-id="b754b-159">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="b754b-160">ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="b754b-160">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
