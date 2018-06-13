---
title: Tabloları çıkarımını yapma
ms.date: 03/30/2017
ms.assetid: 74a288d4-b8e9-4f1a-b2cd-10df92c1ed1f
ms.openlocfilehash: b14cbc39b02136ac7f226faf2636a69ac072f529
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32757833"
---
# <a name="inferring-tables"></a><span data-ttu-id="4a255-102">Tabloları çıkarımını yapma</span><span class="sxs-lookup"><span data-stu-id="4a255-102">Inferring Tables</span></span>
<span data-ttu-id="4a255-103">İçin bir şema çıkarımını yapma olduğunda bir <xref:System.Data.DataSet> hangi XML öğeleri tabloları temsil eden önce bir XML belgesinden ADO.NET belirler.</span><span class="sxs-lookup"><span data-stu-id="4a255-103">When inferring a schema for a <xref:System.Data.DataSet> from an XML document, ADO.NET first determines which XML elements represent tables.</span></span> <span data-ttu-id="4a255-104">Bir tablo için aşağıdaki XML yapıları sonucunda **DataSet** şeması:</span><span class="sxs-lookup"><span data-stu-id="4a255-104">The following XML structures result in a table for the **DataSet** schema:</span></span>  
  
-   <span data-ttu-id="4a255-105">Öznitelikleri olan öğeleri</span><span class="sxs-lookup"><span data-stu-id="4a255-105">Elements with attributes</span></span>  
  
-   <span data-ttu-id="4a255-106">Alt öğelerin</span><span class="sxs-lookup"><span data-stu-id="4a255-106">Elements with child elements</span></span>  
  
-   <span data-ttu-id="4a255-107">Yinelenen öğeleri</span><span class="sxs-lookup"><span data-stu-id="4a255-107">Repeating elements</span></span>  
  
## <a name="elements-with-attributes"></a><span data-ttu-id="4a255-108">Öznitelikleri olan öğeleri</span><span class="sxs-lookup"><span data-stu-id="4a255-108">Elements with Attributes</span></span>  
 <span data-ttu-id="4a255-109">Bunları belirtilen öznitelikler neden olan öğenin tabloları sonuçlandı.</span><span class="sxs-lookup"><span data-stu-id="4a255-109">Elements that have attributes specified in them result in inferred tables.</span></span> <span data-ttu-id="4a255-110">Örneğin, aşağıdaki XML göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="4a255-110">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1"/>  
  <Element1 attr1="value2">Text1</Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="4a255-111">Çıkarma işlemi "Element1." adlı bir tablo oluşturur</span><span class="sxs-lookup"><span data-stu-id="4a255-111">The inference process produces a table named "Element1."</span></span>  
  
 <span data-ttu-id="4a255-112">**Veri kümesi:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="4a255-112">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="4a255-113">**Tablo:** Element1</span><span class="sxs-lookup"><span data-stu-id="4a255-113">**Table:** Element1</span></span>  
  
|<span data-ttu-id="4a255-114">attr1</span><span class="sxs-lookup"><span data-stu-id="4a255-114">attr1</span></span>|<span data-ttu-id="4a255-115">Element1_Text</span><span class="sxs-lookup"><span data-stu-id="4a255-115">Element1_Text</span></span>|  
|-----------|--------------------|  
|<span data-ttu-id="4a255-116">Değer1</span><span class="sxs-lookup"><span data-stu-id="4a255-116">value1</span></span>||  
|<span data-ttu-id="4a255-117">Value2</span><span class="sxs-lookup"><span data-stu-id="4a255-117">value2</span></span>|<span data-ttu-id="4a255-118">Metin1</span><span class="sxs-lookup"><span data-stu-id="4a255-118">Text1</span></span>|  
  
## <a name="elements-with-child-elements"></a><span data-ttu-id="4a255-119">Alt öğelerin</span><span class="sxs-lookup"><span data-stu-id="4a255-119">Elements with Child Elements</span></span>  
 <span data-ttu-id="4a255-120">Alt öğeler sonucu olan öğenin tabloları sonuçlandı.</span><span class="sxs-lookup"><span data-stu-id="4a255-120">Elements that have child elements result in inferred tables.</span></span> <span data-ttu-id="4a255-121">Örneğin, aşağıdaki XML göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="4a255-121">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>  
    <ChildElement1>Text1</ChildElement1>  
  </Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="4a255-122">Çıkarma işlemi "Element1." adlı bir tablo oluşturur</span><span class="sxs-lookup"><span data-stu-id="4a255-122">The inference process produces a table named "Element1."</span></span>  
  
 <span data-ttu-id="4a255-123">**Veri kümesi:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="4a255-123">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="4a255-124">**Tablo:** Element1</span><span class="sxs-lookup"><span data-stu-id="4a255-124">**Table:** Element1</span></span>  
  
|<span data-ttu-id="4a255-125">ChildElement1</span><span class="sxs-lookup"><span data-stu-id="4a255-125">ChildElement1</span></span>|  
|-------------------|  
|<span data-ttu-id="4a255-126">Metin1</span><span class="sxs-lookup"><span data-stu-id="4a255-126">Text1</span></span>|  
  
 <span data-ttu-id="4a255-127">Belge veya kök öğesi sonuç öznitelikleri ya da sütun olarak algılanır alt öğeleri varsa oluşturulursa bir tabloda.</span><span class="sxs-lookup"><span data-stu-id="4a255-127">The document, or root, element result in an inferred table if it has attributes or child elements that are inferred as columns.</span></span> <span data-ttu-id="4a255-128">Belge öğenin özniteliklere ve sütun olarak ortaya alt öğeleri varsa öğe olarak algılanır bir **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="4a255-128">If the document element has no attributes and no child elements that would be inferred as columns, the element is inferred as a **DataSet**.</span></span> <span data-ttu-id="4a255-129">Örneğin, aşağıdaki XML göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="4a255-129">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
  <Element2>Text2</Element2>  
</DocumentElement>  
```  
  
 <span data-ttu-id="4a255-130">Çıkarma işlemi "DocumentElement." adlı bir tablo oluşturur</span><span class="sxs-lookup"><span data-stu-id="4a255-130">The inference process produces a table named "DocumentElement."</span></span>  
  
 <span data-ttu-id="4a255-131">**Veri kümesi:** NewDataSet</span><span class="sxs-lookup"><span data-stu-id="4a255-131">**DataSet:** NewDataSet</span></span>  
  
 <span data-ttu-id="4a255-132">**Tablo:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="4a255-132">**Table:** DocumentElement</span></span>  
  
|<span data-ttu-id="4a255-133">Element1</span><span class="sxs-lookup"><span data-stu-id="4a255-133">Element1</span></span>|<span data-ttu-id="4a255-134">Element2</span><span class="sxs-lookup"><span data-stu-id="4a255-134">Element2</span></span>|  
|--------------|--------------|  
|<span data-ttu-id="4a255-135">Metin1</span><span class="sxs-lookup"><span data-stu-id="4a255-135">Text1</span></span>|<span data-ttu-id="4a255-136">Metin2</span><span class="sxs-lookup"><span data-stu-id="4a255-136">Text2</span></span>|  
  
 <span data-ttu-id="4a255-137">Alternatif olarak, aşağıdaki XML göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="4a255-137">Alternatively, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1" attr2="value2"/>  
</DocumentElement>  
```  
  
 <span data-ttu-id="4a255-138">Çıkarma işlemi üreten bir **DataSet** "" Element1."adlı bir tablo içeriyor DocumentElement" adlı</span><span class="sxs-lookup"><span data-stu-id="4a255-138">The inference process produces a **DataSet** named "DocumentElement" that contains a table named "Element1."</span></span>  
  
 <span data-ttu-id="4a255-139">**Veri kümesi:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="4a255-139">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="4a255-140">**Tablo:** Element1</span><span class="sxs-lookup"><span data-stu-id="4a255-140">**Table:** Element1</span></span>  
  
|<span data-ttu-id="4a255-141">attr1</span><span class="sxs-lookup"><span data-stu-id="4a255-141">attr1</span></span>|<span data-ttu-id="4a255-142">attr2</span><span class="sxs-lookup"><span data-stu-id="4a255-142">attr2</span></span>|  
|-----------|-----------|  
|<span data-ttu-id="4a255-143">Değer1</span><span class="sxs-lookup"><span data-stu-id="4a255-143">value1</span></span>|<span data-ttu-id="4a255-144">Value2</span><span class="sxs-lookup"><span data-stu-id="4a255-144">value2</span></span>|  
  
## <a name="repeating-elements"></a><span data-ttu-id="4a255-145">Yinelenen öğeleri</span><span class="sxs-lookup"><span data-stu-id="4a255-145">Repeating Elements</span></span>  
 <span data-ttu-id="4a255-146">Tek bir oluşturulursa tablo sonucunda yineleyin öğeleri.</span><span class="sxs-lookup"><span data-stu-id="4a255-146">Elements that repeat result in a single inferred table.</span></span> <span data-ttu-id="4a255-147">Örneğin, aşağıdaki XML göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="4a255-147">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
  <Element1>Text2</Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="4a255-148">Çıkarma işlemi "Element1." adlı bir tablo oluşturur</span><span class="sxs-lookup"><span data-stu-id="4a255-148">The inference process produces a table named "Element1."</span></span>  
  
 <span data-ttu-id="4a255-149">**Veri kümesi:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="4a255-149">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="4a255-150">**Tablo:** Element1</span><span class="sxs-lookup"><span data-stu-id="4a255-150">**Table:** Element1</span></span>  
  
|<span data-ttu-id="4a255-151">Element1_Text</span><span class="sxs-lookup"><span data-stu-id="4a255-151">Element1_Text</span></span>|  
|--------------------|  
|<span data-ttu-id="4a255-152">Metin1</span><span class="sxs-lookup"><span data-stu-id="4a255-152">Text1</span></span>|  
|<span data-ttu-id="4a255-153">Metin2</span><span class="sxs-lookup"><span data-stu-id="4a255-153">Text2</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4a255-154">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4a255-154">See Also</span></span>  
 [<span data-ttu-id="4a255-155">XML’den DataSet İlişkisel Yapısını Çıkarma</span><span class="sxs-lookup"><span data-stu-id="4a255-155">Inferring DataSet Relational Structure from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)  
 [<span data-ttu-id="4a255-156">XML’den DataSet Yükleme</span><span class="sxs-lookup"><span data-stu-id="4a255-156">Loading a DataSet from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)  
 [<span data-ttu-id="4a255-157">XML’den DataSet Schema Bilgilerini Yükleme</span><span class="sxs-lookup"><span data-stu-id="4a255-157">Loading DataSet Schema Information from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)  
 [<span data-ttu-id="4a255-158">DataSet içinde XML kullanma</span><span class="sxs-lookup"><span data-stu-id="4a255-158">Using XML in a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [<span data-ttu-id="4a255-159">DataSets, DataTables ve DataViews</span><span class="sxs-lookup"><span data-stu-id="4a255-159">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="4a255-160">ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="4a255-160">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
