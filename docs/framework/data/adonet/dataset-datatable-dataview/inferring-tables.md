---
title: "Tabloları çıkarımını yapma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 74a288d4-b8e9-4f1a-b2cd-10df92c1ed1f
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 2c00dd11d4d93e5d3b0e2f1c3b75765056a10cab
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="inferring-tables"></a><span data-ttu-id="9919e-102">Tabloları çıkarımını yapma</span><span class="sxs-lookup"><span data-stu-id="9919e-102">Inferring Tables</span></span>
<span data-ttu-id="9919e-103">İçin bir şema çıkarımını yapma olduğunda bir <xref:System.Data.DataSet> hangi XML öğeleri tabloları temsil eden önce bir XML belgesinden ADO.NET belirler.</span><span class="sxs-lookup"><span data-stu-id="9919e-103">When inferring a schema for a <xref:System.Data.DataSet> from an XML document, ADO.NET first determines which XML elements represent tables.</span></span> <span data-ttu-id="9919e-104">Bir tablo için aşağıdaki XML yapıları sonucunda **DataSet** şeması:</span><span class="sxs-lookup"><span data-stu-id="9919e-104">The following XML structures result in a table for the **DataSet** schema:</span></span>  
  
-   <span data-ttu-id="9919e-105">Öznitelikleri olan öğeleri</span><span class="sxs-lookup"><span data-stu-id="9919e-105">Elements with attributes</span></span>  
  
-   <span data-ttu-id="9919e-106">Alt öğelerin</span><span class="sxs-lookup"><span data-stu-id="9919e-106">Elements with child elements</span></span>  
  
-   <span data-ttu-id="9919e-107">Yinelenen öğeleri</span><span class="sxs-lookup"><span data-stu-id="9919e-107">Repeating elements</span></span>  
  
## <a name="elements-with-attributes"></a><span data-ttu-id="9919e-108">Öznitelikleri olan öğeleri</span><span class="sxs-lookup"><span data-stu-id="9919e-108">Elements with Attributes</span></span>  
 <span data-ttu-id="9919e-109">Bunları belirtilen öznitelikler neden olan öğenin tabloları sonuçlandı.</span><span class="sxs-lookup"><span data-stu-id="9919e-109">Elements that have attributes specified in them result in inferred tables.</span></span> <span data-ttu-id="9919e-110">Örneğin, aşağıdaki XML göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="9919e-110">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1"/>  
  <Element1 attr1="value2">Text1</Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="9919e-111">Çıkarma işlemi "Element1." adlı bir tablo oluşturur</span><span class="sxs-lookup"><span data-stu-id="9919e-111">The inference process produces a table named "Element1."</span></span>  
  
 <span data-ttu-id="9919e-112">**Veri kümesi:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="9919e-112">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="9919e-113">**Tablo:** Element1</span><span class="sxs-lookup"><span data-stu-id="9919e-113">**Table:** Element1</span></span>  
  
|<span data-ttu-id="9919e-114">attr1</span><span class="sxs-lookup"><span data-stu-id="9919e-114">attr1</span></span>|<span data-ttu-id="9919e-115">Element1_Text</span><span class="sxs-lookup"><span data-stu-id="9919e-115">Element1_Text</span></span>|  
|-----------|--------------------|  
|<span data-ttu-id="9919e-116">Değer1</span><span class="sxs-lookup"><span data-stu-id="9919e-116">value1</span></span>||  
|<span data-ttu-id="9919e-117">Value2</span><span class="sxs-lookup"><span data-stu-id="9919e-117">value2</span></span>|<span data-ttu-id="9919e-118">Text1</span><span class="sxs-lookup"><span data-stu-id="9919e-118">Text1</span></span>|  
  
## <a name="elements-with-child-elements"></a><span data-ttu-id="9919e-119">Alt öğelerin</span><span class="sxs-lookup"><span data-stu-id="9919e-119">Elements with Child Elements</span></span>  
 <span data-ttu-id="9919e-120">Alt öğeler sonucu olan öğenin tabloları sonuçlandı.</span><span class="sxs-lookup"><span data-stu-id="9919e-120">Elements that have child elements result in inferred tables.</span></span> <span data-ttu-id="9919e-121">Örneğin, aşağıdaki XML göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="9919e-121">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>  
    <ChildElement1>Text1</ChildElement1>  
  </Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="9919e-122">Çıkarma işlemi "Element1." adlı bir tablo oluşturur</span><span class="sxs-lookup"><span data-stu-id="9919e-122">The inference process produces a table named "Element1."</span></span>  
  
 <span data-ttu-id="9919e-123">**Veri kümesi:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="9919e-123">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="9919e-124">**Tablo:** Element1</span><span class="sxs-lookup"><span data-stu-id="9919e-124">**Table:** Element1</span></span>  
  
|<span data-ttu-id="9919e-125">ChildElement1</span><span class="sxs-lookup"><span data-stu-id="9919e-125">ChildElement1</span></span>|  
|-------------------|  
|<span data-ttu-id="9919e-126">Text1</span><span class="sxs-lookup"><span data-stu-id="9919e-126">Text1</span></span>|  
  
 <span data-ttu-id="9919e-127">Belge veya kök öğesi sonuç öznitelikleri ya da sütun olarak algılanır alt öğeleri varsa oluşturulursa bir tabloda.</span><span class="sxs-lookup"><span data-stu-id="9919e-127">The document, or root, element result in an inferred table if it has attributes or child elements that are inferred as columns.</span></span> <span data-ttu-id="9919e-128">Belge öğenin özniteliklere ve sütun olarak ortaya alt öğeleri varsa öğe olarak algılanır bir **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="9919e-128">If the document element has no attributes and no child elements that would be inferred as columns, the element is inferred as a **DataSet**.</span></span> <span data-ttu-id="9919e-129">Örneğin, aşağıdaki XML göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="9919e-129">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
  <Element2>Text2</Element2>  
</DocumentElement>  
```  
  
 <span data-ttu-id="9919e-130">Çıkarma işlemi "DocumentElement." adlı bir tablo oluşturur</span><span class="sxs-lookup"><span data-stu-id="9919e-130">The inference process produces a table named "DocumentElement."</span></span>  
  
 <span data-ttu-id="9919e-131">**Veri kümesi:** NewDataSet</span><span class="sxs-lookup"><span data-stu-id="9919e-131">**DataSet:** NewDataSet</span></span>  
  
 <span data-ttu-id="9919e-132">**Tablo:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="9919e-132">**Table:** DocumentElement</span></span>  
  
|<span data-ttu-id="9919e-133">Element1</span><span class="sxs-lookup"><span data-stu-id="9919e-133">Element1</span></span>|<span data-ttu-id="9919e-134">Element2</span><span class="sxs-lookup"><span data-stu-id="9919e-134">Element2</span></span>|  
|--------------|--------------|  
|<span data-ttu-id="9919e-135">Text1</span><span class="sxs-lookup"><span data-stu-id="9919e-135">Text1</span></span>|<span data-ttu-id="9919e-136">Metin2</span><span class="sxs-lookup"><span data-stu-id="9919e-136">Text2</span></span>|  
  
 <span data-ttu-id="9919e-137">Alternatif olarak, aşağıdaki XML göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="9919e-137">Alternatively, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1" attr2="value2"/>  
</DocumentElement>  
```  
  
 <span data-ttu-id="9919e-138">Çıkarma işlemi üreten bir **DataSet** "" Element1."adlı bir tablo içeriyor DocumentElement" adlı</span><span class="sxs-lookup"><span data-stu-id="9919e-138">The inference process produces a **DataSet** named "DocumentElement" that contains a table named "Element1."</span></span>  
  
 <span data-ttu-id="9919e-139">**Veri kümesi:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="9919e-139">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="9919e-140">**Tablo:** Element1</span><span class="sxs-lookup"><span data-stu-id="9919e-140">**Table:** Element1</span></span>  
  
|<span data-ttu-id="9919e-141">attr1</span><span class="sxs-lookup"><span data-stu-id="9919e-141">attr1</span></span>|<span data-ttu-id="9919e-142">attr2</span><span class="sxs-lookup"><span data-stu-id="9919e-142">attr2</span></span>|  
|-----------|-----------|  
|<span data-ttu-id="9919e-143">Değer1</span><span class="sxs-lookup"><span data-stu-id="9919e-143">value1</span></span>|<span data-ttu-id="9919e-144">Value2</span><span class="sxs-lookup"><span data-stu-id="9919e-144">value2</span></span>|  
  
## <a name="repeating-elements"></a><span data-ttu-id="9919e-145">Yinelenen öğeleri</span><span class="sxs-lookup"><span data-stu-id="9919e-145">Repeating Elements</span></span>  
 <span data-ttu-id="9919e-146">Tek bir oluşturulursa tablo sonucunda yineleyin öğeleri.</span><span class="sxs-lookup"><span data-stu-id="9919e-146">Elements that repeat result in a single inferred table.</span></span> <span data-ttu-id="9919e-147">Örneğin, aşağıdaki XML göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="9919e-147">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
  <Element1>Text2</Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="9919e-148">Çıkarma işlemi "Element1." adlı bir tablo oluşturur</span><span class="sxs-lookup"><span data-stu-id="9919e-148">The inference process produces a table named "Element1."</span></span>  
  
 <span data-ttu-id="9919e-149">**Veri kümesi:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="9919e-149">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="9919e-150">**Tablo:** Element1</span><span class="sxs-lookup"><span data-stu-id="9919e-150">**Table:** Element1</span></span>  
  
|<span data-ttu-id="9919e-151">Element1_Text</span><span class="sxs-lookup"><span data-stu-id="9919e-151">Element1_Text</span></span>|  
|--------------------|  
|<span data-ttu-id="9919e-152">Text1</span><span class="sxs-lookup"><span data-stu-id="9919e-152">Text1</span></span>|  
|<span data-ttu-id="9919e-153">Metin2</span><span class="sxs-lookup"><span data-stu-id="9919e-153">Text2</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9919e-154">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9919e-154">See Also</span></span>  
 [<span data-ttu-id="9919e-155">XML’den DataSet İlişkisel Yapısını Çıkarma</span><span class="sxs-lookup"><span data-stu-id="9919e-155">Inferring DataSet Relational Structure from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)  
 [<span data-ttu-id="9919e-156">XML’den DataSet Yükleme</span><span class="sxs-lookup"><span data-stu-id="9919e-156">Loading a DataSet from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)  
 [<span data-ttu-id="9919e-157">XML’den DataSet Schema Bilgilerini Yükleme</span><span class="sxs-lookup"><span data-stu-id="9919e-157">Loading DataSet Schema Information from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)  
 [<span data-ttu-id="9919e-158">DataSet içinde XML kullanma</span><span class="sxs-lookup"><span data-stu-id="9919e-158">Using XML in a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [<span data-ttu-id="9919e-159">DataSets, DataTables ve DataViews</span><span class="sxs-lookup"><span data-stu-id="9919e-159">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="9919e-160">ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="9919e-160">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
