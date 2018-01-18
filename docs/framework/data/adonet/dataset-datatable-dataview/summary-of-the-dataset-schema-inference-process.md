---
title: "Veri kümesi şemasını çıkarım işlem özeti"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fd0891c8-d068-4e30-a76f-7c375f078bf7
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 63ab866785f1fea66ed72fa17589a5be790fcdaa
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="summary-of-the-dataset-schema-inference-process"></a><span data-ttu-id="1b7ec-102">Veri kümesi şemasını çıkarım işlem özeti</span><span class="sxs-lookup"><span data-stu-id="1b7ec-102">Summary of the DataSet Schema Inference Process</span></span>
<span data-ttu-id="1b7ec-103">Çıkarım işlemi önce hangi öğelerin tabloları olarak çıkarımı yapılan XML belgesinden belirler.</span><span class="sxs-lookup"><span data-stu-id="1b7ec-103">The inference process first determines, from the XML document, which elements will be inferred as tables.</span></span> <span data-ttu-id="1b7ec-104">Kalan XML'den çıkarım işlemi bu tablo sütunlarını belirler.</span><span class="sxs-lookup"><span data-stu-id="1b7ec-104">From the remaining XML, the inference process determines the columns for those tables.</span></span> <span data-ttu-id="1b7ec-105">İç içe tablolar için çıkarım işlem oluşturur iç içe geçmiş <xref:System.Data.DataRelation> ve <xref:System.Data.ForeignKeyConstraint> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="1b7ec-105">For nested tables, the inference process generates nested <xref:System.Data.DataRelation> and <xref:System.Data.ForeignKeyConstraint> objects.</span></span>  
  
 <span data-ttu-id="1b7ec-106">Çıkarım kuralları kısa bir özeti aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="1b7ec-106">Following is a brief summary of inference rules:</span></span>  
  
-   <span data-ttu-id="1b7ec-107">Özniteliklere sahip öğeler tablo olarak algılanır.</span><span class="sxs-lookup"><span data-stu-id="1b7ec-107">Elements that have attributes are inferred as tables.</span></span>  
  
-   <span data-ttu-id="1b7ec-108">Alt öğeleri olan öğeler tablo olarak algılanır.</span><span class="sxs-lookup"><span data-stu-id="1b7ec-108">Elements that have child elements are inferred as tables.</span></span>  
  
-   <span data-ttu-id="1b7ec-109">Yinelenen öğeler tek bir tablo olarak algılanır.</span><span class="sxs-lookup"><span data-stu-id="1b7ec-109">Elements that repeat are inferred as a single table.</span></span>  
  
-   <span data-ttu-id="1b7ec-110">Belge ya da kök öğesi özniteliklere ve sütun olarak ortaya alt öğe varsa, olarak algılanır bir <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="1b7ec-110">If the document, or root, element has no attributes, and no child elements that would be inferred as columns, it is inferred as a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="1b7ec-111">Aksi takdirde, belge öğesi bir tablo olarak algılanır.</span><span class="sxs-lookup"><span data-stu-id="1b7ec-111">Otherwise, the document element is inferred as a table.</span></span>  
  
-   <span data-ttu-id="1b7ec-112">Öznitelikleri sütun olarak algılanır.</span><span class="sxs-lookup"><span data-stu-id="1b7ec-112">Attributes are inferred as columns.</span></span>  
  
-   <span data-ttu-id="1b7ec-113">Hiçbir öznitelik veya alt öğe varsa ve bu tekrarlamayın, öğeler sütun olarak algılanır.</span><span class="sxs-lookup"><span data-stu-id="1b7ec-113">Elements that have no attributes or child elements, and that do not repeat, are inferred as columns.</span></span>  
  
-   <span data-ttu-id="1b7ec-114">Ayrıca algılanır diğer öğeleri içinde iç içe tablo olarak algılanır öğelerin olarak tabloları, iç içe bir **DataRelation** iki tablo arasında oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="1b7ec-114">For elements that are inferred as nested tables within other elements that are also inferred as tables, a nested **DataRelation** is created between the two tables.</span></span> <span data-ttu-id="1b7ec-115">Adlı yeni, birincil bir anahtar sütunu **Tablename_ıd** her iki tabloyu eklenir ve tarafından kullanılan **DataRelation**.</span><span class="sxs-lookup"><span data-stu-id="1b7ec-115">A new, primary key column named **TableName_Id** is added to both tables and used by the **DataRelation**.</span></span> <span data-ttu-id="1b7ec-116">A **ForeignKeyConstraint** kullanarak iki tablo arasında oluşturulan **Tablename_ıd** sütun.</span><span class="sxs-lookup"><span data-stu-id="1b7ec-116">A **ForeignKeyConstraint** is created between the two tables using the **TableName_Id** column.</span></span>  
  
-   <span data-ttu-id="1b7ec-117">Tablo olarak çıkarımı yapılan ve metin içeriyor ancak hiçbir alt öğelere sahip öğeleri için yeni bir sütun adında **TableName_Text** metnini öğelerin her biri için oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="1b7ec-117">For elements that are inferred as tables and that contain text but have no child elements, a new column named **TableName_Text** is created for the text of each of the elements.</span></span> <span data-ttu-id="1b7ec-118">Bir tablo olarak algılanır ve metin varsa ancak de alt öğeye sahip bir öğe, metin göz ardı edilir.</span><span class="sxs-lookup"><span data-stu-id="1b7ec-118">If an element is inferred as a table and has text, but also has child elements, the text is ignored.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b7ec-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1b7ec-119">See Also</span></span>  
 [<span data-ttu-id="1b7ec-120">XML’den DataSet İlişkisel Yapısını Çıkarma</span><span class="sxs-lookup"><span data-stu-id="1b7ec-120">Inferring DataSet Relational Structure from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)  
 [<span data-ttu-id="1b7ec-121">XML’den DataSet Yükleme</span><span class="sxs-lookup"><span data-stu-id="1b7ec-121">Loading a DataSet from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)  
 [<span data-ttu-id="1b7ec-122">XML’den DataSet Schema Bilgilerini Yükleme</span><span class="sxs-lookup"><span data-stu-id="1b7ec-122">Loading DataSet Schema Information from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)  
 [<span data-ttu-id="1b7ec-123">DataSet içinde XML kullanma</span><span class="sxs-lookup"><span data-stu-id="1b7ec-123">Using XML in a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [<span data-ttu-id="1b7ec-124">DataSets, DataTables ve DataViews</span><span class="sxs-lookup"><span data-stu-id="1b7ec-124">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="1b7ec-125">ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="1b7ec-125">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
