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
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: ae6f7827b7206544ff7547cc04f44b7cda34bef8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="inferring-tables"></a><span data-ttu-id="a77e9-102">Tabloları çıkarımını yapma</span><span class="sxs-lookup"><span data-stu-id="a77e9-102">Inferring Tables</span></span>
<span data-ttu-id="a77e9-103">İçin bir şema çıkarımını yapma olduğunda bir <xref:System.Data.DataSet> hangi XML öğeleri tabloları temsil eden önce bir XML belgesinden ADO.NET belirler.</span><span class="sxs-lookup"><span data-stu-id="a77e9-103">When inferring a schema for a <xref:System.Data.DataSet> from an XML document, ADO.NET first determines which XML elements represent tables.</span></span> <span data-ttu-id="a77e9-104">Bir tablo için aşağıdaki XML yapıları sonucunda **DataSet** şeması:</span><span class="sxs-lookup"><span data-stu-id="a77e9-104">The following XML structures result in a table for the **DataSet** schema:</span></span>  
  
-   <span data-ttu-id="a77e9-105">Öznitelikleri olan öğeleri</span><span class="sxs-lookup"><span data-stu-id="a77e9-105">Elements with attributes</span></span>  
  
-   <span data-ttu-id="a77e9-106">Alt öğelerin</span><span class="sxs-lookup"><span data-stu-id="a77e9-106">Elements with child elements</span></span>  
  
-   <span data-ttu-id="a77e9-107">Yinelenen öğeleri</span><span class="sxs-lookup"><span data-stu-id="a77e9-107">Repeating elements</span></span>  
  
## <a name="elements-with-attributes"></a><span data-ttu-id="a77e9-108">Öznitelikleri olan öğeleri</span><span class="sxs-lookup"><span data-stu-id="a77e9-108">Elements with Attributes</span></span>  
 <span data-ttu-id="a77e9-109">Bunları belirtilen öznitelikler neden olan öğenin tabloları sonuçlandı.</span><span class="sxs-lookup"><span data-stu-id="a77e9-109">Elements that have attributes specified in them result in inferred tables.</span></span> <span data-ttu-id="a77e9-110">Örneğin, aşağıdaki XML göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="a77e9-110">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1"/>  
  <Element1 attr1="value2">Text1</Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="a77e9-111">Çıkarma işlemi "Element1." adlı bir tablo oluşturur</span><span class="sxs-lookup"><span data-stu-id="a77e9-111">The inference process produces a table named "Element1."</span></span>  
  
 <span data-ttu-id="a77e9-112">**Veri kümesi:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="a77e9-112">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="a77e9-113">**Tablo:** Element1</span><span class="sxs-lookup"><span data-stu-id="a77e9-113">**Table:** Element1</span></span>  
  
|<span data-ttu-id="a77e9-114">attr1</span><span class="sxs-lookup"><span data-stu-id="a77e9-114">attr1</span></span>|<span data-ttu-id="a77e9-115">Element1_Text</span><span class="sxs-lookup"><span data-stu-id="a77e9-115">Element1_Text</span></span>|  
|-----------|--------------------|  
|<span data-ttu-id="a77e9-116">Değer1</span><span class="sxs-lookup"><span data-stu-id="a77e9-116">value1</span></span>||  
|<span data-ttu-id="a77e9-117">Value2</span><span class="sxs-lookup"><span data-stu-id="a77e9-117">value2</span></span>|<span data-ttu-id="a77e9-118">Metin1</span><span class="sxs-lookup"><span data-stu-id="a77e9-118">Text1</span></span>|  
  
## <a name="elements-with-child-elements"></a><span data-ttu-id="a77e9-119">Alt öğelerin</span><span class="sxs-lookup"><span data-stu-id="a77e9-119">Elements with Child Elements</span></span>  
 <span data-ttu-id="a77e9-120">Alt öğeler sonucu olan öğenin tabloları sonuçlandı.</span><span class="sxs-lookup"><span data-stu-id="a77e9-120">Elements that have child elements result in inferred tables.</span></span> <span data-ttu-id="a77e9-121">Örneğin, aşağıdaki XML göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="a77e9-121">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>  
    <ChildElement1>Text1</ChildElement1>  
  </Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="a77e9-122">Çıkarma işlemi "Element1." adlı bir tablo oluşturur</span><span class="sxs-lookup"><span data-stu-id="a77e9-122">The inference process produces a table named "Element1."</span></span>  
  
 <span data-ttu-id="a77e9-123">**Veri kümesi:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="a77e9-123">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="a77e9-124">**Tablo:** Element1</span><span class="sxs-lookup"><span data-stu-id="a77e9-124">**Table:** Element1</span></span>  
  
|<span data-ttu-id="a77e9-125">ChildElement1</span><span class="sxs-lookup"><span data-stu-id="a77e9-125">ChildElement1</span></span>|  
|-------------------|  
|<span data-ttu-id="a77e9-126">Metin1</span><span class="sxs-lookup"><span data-stu-id="a77e9-126">Text1</span></span>|  
  
 <span data-ttu-id="a77e9-127">Belge veya kök öğesi sonuç öznitelikleri ya da sütun olarak algılanır alt öğeleri varsa oluşturulursa bir tabloda.</span><span class="sxs-lookup"><span data-stu-id="a77e9-127">The document, or root, element result in an inferred table if it has attributes or child elements that are inferred as columns.</span></span> <span data-ttu-id="a77e9-128">Belge öğenin özniteliklere ve sütun olarak ortaya alt öğeleri varsa öğe olarak algılanır bir **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="a77e9-128">If the document element has no attributes and no child elements that would be inferred as columns, the element is inferred as a **DataSet**.</span></span> <span data-ttu-id="a77e9-129">Örneğin, aşağıdaki XML göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="a77e9-129">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
  <Element2>Text2</Element2>  
</DocumentElement>  
```  
  
 <span data-ttu-id="a77e9-130">Çıkarma işlemi "DocumentElement." adlı bir tablo oluşturur</span><span class="sxs-lookup"><span data-stu-id="a77e9-130">The inference process produces a table named "DocumentElement."</span></span>  
  
 <span data-ttu-id="a77e9-131">**Veri kümesi:** NewDataSet</span><span class="sxs-lookup"><span data-stu-id="a77e9-131">**DataSet:** NewDataSet</span></span>  
  
 <span data-ttu-id="a77e9-132">**Tablo:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="a77e9-132">**Table:** DocumentElement</span></span>  
  
|<span data-ttu-id="a77e9-133">Element1</span><span class="sxs-lookup"><span data-stu-id="a77e9-133">Element1</span></span>|<span data-ttu-id="a77e9-134">Element2</span><span class="sxs-lookup"><span data-stu-id="a77e9-134">Element2</span></span>|  
|--------------|--------------|  
|<span data-ttu-id="a77e9-135">Metin1</span><span class="sxs-lookup"><span data-stu-id="a77e9-135">Text1</span></span>|<span data-ttu-id="a77e9-136">Metin2</span><span class="sxs-lookup"><span data-stu-id="a77e9-136">Text2</span></span>|  
  
 <span data-ttu-id="a77e9-137">Alternatif olarak, aşağıdaki XML göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="a77e9-137">Alternatively, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1" attr2="value2"/>  
</DocumentElement>  
```  
  
 <span data-ttu-id="a77e9-138">Çıkarma işlemi üreten bir **DataSet** "" Element1."adlı bir tablo içeriyor DocumentElement" adlı</span><span class="sxs-lookup"><span data-stu-id="a77e9-138">The inference process produces a **DataSet** named "DocumentElement" that contains a table named "Element1."</span></span>  
  
 <span data-ttu-id="a77e9-139">**Veri kümesi:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="a77e9-139">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="a77e9-140">**Tablo:** Element1</span><span class="sxs-lookup"><span data-stu-id="a77e9-140">**Table:** Element1</span></span>  
  
|<span data-ttu-id="a77e9-141">attr1</span><span class="sxs-lookup"><span data-stu-id="a77e9-141">attr1</span></span>|<span data-ttu-id="a77e9-142">attr2</span><span class="sxs-lookup"><span data-stu-id="a77e9-142">attr2</span></span>|  
|-----------|-----------|  
|<span data-ttu-id="a77e9-143">Değer1</span><span class="sxs-lookup"><span data-stu-id="a77e9-143">value1</span></span>|<span data-ttu-id="a77e9-144">Value2</span><span class="sxs-lookup"><span data-stu-id="a77e9-144">value2</span></span>|  
  
## <a name="repeating-elements"></a><span data-ttu-id="a77e9-145">Yinelenen öğeleri</span><span class="sxs-lookup"><span data-stu-id="a77e9-145">Repeating Elements</span></span>  
 <span data-ttu-id="a77e9-146">Tek bir oluşturulursa tablo sonucunda yineleyin öğeleri.</span><span class="sxs-lookup"><span data-stu-id="a77e9-146">Elements that repeat result in a single inferred table.</span></span> <span data-ttu-id="a77e9-147">Örneğin, aşağıdaki XML göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="a77e9-147">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
  <Element1>Text2</Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="a77e9-148">Çıkarma işlemi "Element1." adlı bir tablo oluşturur</span><span class="sxs-lookup"><span data-stu-id="a77e9-148">The inference process produces a table named "Element1."</span></span>  
  
 <span data-ttu-id="a77e9-149">**Veri kümesi:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="a77e9-149">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="a77e9-150">**Tablo:** Element1</span><span class="sxs-lookup"><span data-stu-id="a77e9-150">**Table:** Element1</span></span>  
  
|<span data-ttu-id="a77e9-151">Element1_Text</span><span class="sxs-lookup"><span data-stu-id="a77e9-151">Element1_Text</span></span>|  
|--------------------|  
|<span data-ttu-id="a77e9-152">Metin1</span><span class="sxs-lookup"><span data-stu-id="a77e9-152">Text1</span></span>|  
|<span data-ttu-id="a77e9-153">Metin2</span><span class="sxs-lookup"><span data-stu-id="a77e9-153">Text2</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a77e9-154">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a77e9-154">See Also</span></span>  
 [<span data-ttu-id="a77e9-155">Veri kümesi ilişkisel XML yapısından çıkarımını yapma</span><span class="sxs-lookup"><span data-stu-id="a77e9-155">Inferring DataSet Relational Structure from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)  
 [<span data-ttu-id="a77e9-156">Bir veri kümesini XML dosyası şuradan yükleniyor</span><span class="sxs-lookup"><span data-stu-id="a77e9-156">Loading a DataSet from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)  
 [<span data-ttu-id="a77e9-157">XML'den veri kümesi şema bilgileri yükleniyor</span><span class="sxs-lookup"><span data-stu-id="a77e9-157">Loading DataSet Schema Information from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)  
 [<span data-ttu-id="a77e9-158">Bir veri kümesini XML kullanma</span><span class="sxs-lookup"><span data-stu-id="a77e9-158">Using XML in a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [<span data-ttu-id="a77e9-159">Veri kümeleri, DataTable ve DataView</span><span class="sxs-lookup"><span data-stu-id="a77e9-159">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="a77e9-160">ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="a77e9-160">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
