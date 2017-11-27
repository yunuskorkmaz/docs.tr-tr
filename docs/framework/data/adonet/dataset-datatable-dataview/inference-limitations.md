---
title: "Çıkarım sınırlamaları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 78517994-5d57-44f8-9d20-38812977de09
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 98ea3d5fa4427b391ef06b3fc6ace9a05dfb819a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="inference-limitations"></a><span data-ttu-id="f7772-102">Çıkarım sınırlamaları</span><span class="sxs-lookup"><span data-stu-id="f7772-102">Inference Limitations</span></span>
<span data-ttu-id="f7772-103">Çıkarımını yapma işlemi bir <xref:System.Data.DataSet> XML Şeması, her bir belgenin XML öğeleri bağlı olarak farklı şemalarda sonuçlanabilir.</span><span class="sxs-lookup"><span data-stu-id="f7772-103">The process of inferring a <xref:System.Data.DataSet> schema from XML can result in different schemas depending on the XML elements in each document.</span></span> <span data-ttu-id="f7772-104">Örneğin, aşağıdaki XML belgelerini göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="f7772-104">For example, consider the following XML documents.</span></span>  
  
 <span data-ttu-id="f7772-105">Document1:</span><span class="sxs-lookup"><span data-stu-id="f7772-105">Document1:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
  <Element1>Text2</Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="f7772-106">Document2:</span><span class="sxs-lookup"><span data-stu-id="f7772-106">Document2:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="f7772-107">Çıkarma işlemi "Document1 için" üreten bir **DataSet** "Element1" yinelenen bir öğe olduğundan "DocumentElement" ve "Element1," adlı bir tablo adında.</span><span class="sxs-lookup"><span data-stu-id="f7772-107">For "Document1," the inference process produces a **DataSet** named "DocumentElement" and a table named "Element1," because "Element1" is a repeating element.</span></span>  
  
 <span data-ttu-id="f7772-108">**Veri kümesi:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="f7772-108">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="f7772-109">**Tablo:** Element1</span><span class="sxs-lookup"><span data-stu-id="f7772-109">**Table:** Element1</span></span>  
  
|<span data-ttu-id="f7772-110">Element1_Text</span><span class="sxs-lookup"><span data-stu-id="f7772-110">Element1_Text</span></span>|  
|--------------------|  
|<span data-ttu-id="f7772-111">Metin1</span><span class="sxs-lookup"><span data-stu-id="f7772-111">Text1</span></span>|  
|<span data-ttu-id="f7772-112">Metin2</span><span class="sxs-lookup"><span data-stu-id="f7772-112">Text2</span></span>|  
  
 <span data-ttu-id="f7772-113">Ancak, "Document2 için" çıkarım işlem üreten bir **DataSet** "NewDataSet" ve "DocumentElement." adlı bir tablo adında</span><span class="sxs-lookup"><span data-stu-id="f7772-113">However, for "Document2," the inference process produces a **DataSet** named "NewDataSet" and a table named "DocumentElement."</span></span> <span data-ttu-id="f7772-114">Özniteliklere ve hiçbir alt öğeler içerdiğinden "Element1" bir sütun olarak algılanır.</span><span class="sxs-lookup"><span data-stu-id="f7772-114">"Element1" is inferred as a column because it has no attributes and no child elements.</span></span>  
  
 <span data-ttu-id="f7772-115">**Veri kümesi:** NewDataSet</span><span class="sxs-lookup"><span data-stu-id="f7772-115">**DataSet:** NewDataSet</span></span>  
  
 <span data-ttu-id="f7772-116">**Tablo:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="f7772-116">**Table:** DocumentElement</span></span>  
  
|<span data-ttu-id="f7772-117">Element1</span><span class="sxs-lookup"><span data-stu-id="f7772-117">Element1</span></span>|  
|--------------|  
|<span data-ttu-id="f7772-118">Metin1</span><span class="sxs-lookup"><span data-stu-id="f7772-118">Text1</span></span>|  
  
 <span data-ttu-id="f7772-119">Bu iki XML belgeleri aynı şema üretmek için hedeflenen, ancak çıkarım işlemi her belgede bulunan öğeleri dayalı çok farklı sonuçlar üretir.</span><span class="sxs-lookup"><span data-stu-id="f7772-119">These two XML documents may have been intended to produce the same schema, but the inference process produces very different results based on the elements contained in each document.</span></span>  
  
 <span data-ttu-id="f7772-120">Bir XML belgesinden şema oluşturma sırasında oluşabilecek Tutarsızlıklardan kaçınmak için XML Şeması Tanım Dili (XSD) veya XML verileri azaltılmış (XDR) yüklenirken kullanarak bir şema açıkça belirtilmesi önerilir bir **DataSet** gelen XML.</span><span class="sxs-lookup"><span data-stu-id="f7772-120">To avoid the discrepancies that can occur when generating schema from an XML document, we recommend that you explicitly specify a schema using XML Schema definition language (XSD) or XML-Data Reduced (XDR) when loading a **DataSet** from XML.</span></span> <span data-ttu-id="f7772-121">Açıkça belirtme hakkında daha fazla bilgi için bir **DataSet** XML Şeması şemasıyla bkz [türetme DataSet ilişkisel yapısı XML Şeması'ndan (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md).</span><span class="sxs-lookup"><span data-stu-id="f7772-121">For more information about explicitly specifying a **DataSet** schema with XML Schema, see [Deriving DataSet Relational Structure from XML Schema (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7772-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f7772-122">See Also</span></span>  
 [<span data-ttu-id="f7772-123">Veri kümesi ilişkisel XML yapısından çıkarımını yapma</span><span class="sxs-lookup"><span data-stu-id="f7772-123">Inferring DataSet Relational Structure from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)  
 [<span data-ttu-id="f7772-124">Bir veri kümesini XML dosyası şuradan yükleniyor</span><span class="sxs-lookup"><span data-stu-id="f7772-124">Loading a DataSet from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)  
 [<span data-ttu-id="f7772-125">XML'den veri kümesi şema bilgileri yükleniyor</span><span class="sxs-lookup"><span data-stu-id="f7772-125">Loading DataSet Schema Information from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)  
 [<span data-ttu-id="f7772-126">Bir veri kümesini XML kullanma</span><span class="sxs-lookup"><span data-stu-id="f7772-126">Using XML in a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [<span data-ttu-id="f7772-127">Veri kümeleri, DataTable ve DataView</span><span class="sxs-lookup"><span data-stu-id="f7772-127">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="f7772-128">ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="f7772-128">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
