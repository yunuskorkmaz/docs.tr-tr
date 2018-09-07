---
title: DataSet şema çıkarımı işleminin özeti
ms.date: 03/30/2017
ms.assetid: fd0891c8-d068-4e30-a76f-7c375f078bf7
ms.openlocfilehash: 1583d5232a3dd483bbe2a6fa0b1bc8a3ae6a659f
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44080505"
---
# <a name="summary-of-the-dataset-schema-inference-process"></a><span data-ttu-id="9a669-102">DataSet şema çıkarımı işleminin özeti</span><span class="sxs-lookup"><span data-stu-id="9a669-102">Summary of the DataSet Schema Inference Process</span></span>
<span data-ttu-id="9a669-103">Çıkarım işlemi önce hangi öğelerin tablo olarak çıkarılan XML belgesinden belirler.</span><span class="sxs-lookup"><span data-stu-id="9a669-103">The inference process first determines, from the XML document, which elements will be inferred as tables.</span></span> <span data-ttu-id="9a669-104">Kalan XML'den çıkarımı işleminin bu tablonun sütunlarını belirler.</span><span class="sxs-lookup"><span data-stu-id="9a669-104">From the remaining XML, the inference process determines the columns for those tables.</span></span> <span data-ttu-id="9a669-105">İç içe tablolar için çıkarım işlem oluşturur iç içe geçmiş <xref:System.Data.DataRelation> ve <xref:System.Data.ForeignKeyConstraint> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="9a669-105">For nested tables, the inference process generates nested <xref:System.Data.DataRelation> and <xref:System.Data.ForeignKeyConstraint> objects.</span></span>  
  
 <span data-ttu-id="9a669-106">Çıkarım kuralları kısa bir özeti aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="9a669-106">Following is a brief summary of inference rules:</span></span>  
  
-   <span data-ttu-id="9a669-107">Öznitelikleri olan öğeler, tablo olarak algılanır.</span><span class="sxs-lookup"><span data-stu-id="9a669-107">Elements that have attributes are inferred as tables.</span></span>  
  
-   <span data-ttu-id="9a669-108">Alt öğeleri olan öğeler, tablo olarak algılanır.</span><span class="sxs-lookup"><span data-stu-id="9a669-108">Elements that have child elements are inferred as tables.</span></span>  
  
-   <span data-ttu-id="9a669-109">Yinelenen öğeler tek bir tablo olarak algılanır.</span><span class="sxs-lookup"><span data-stu-id="9a669-109">Elements that repeat are inferred as a single table.</span></span>  
  
-   <span data-ttu-id="9a669-110">Belge veya kök öğe öznitelikleri ve sütun olarak çıkarılan hiçbir alt öğe varsa, olarak algılanır bir <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="9a669-110">If the document, or root, element has no attributes, and no child elements that would be inferred as columns, it is inferred as a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="9a669-111">Aksi takdirde, belge öğesi bir tablo olarak algılanır.</span><span class="sxs-lookup"><span data-stu-id="9a669-111">Otherwise, the document element is inferred as a table.</span></span>  
  
-   <span data-ttu-id="9a669-112">Öznitelikleri sütun olarak algılanır.</span><span class="sxs-lookup"><span data-stu-id="9a669-112">Attributes are inferred as columns.</span></span>  
  
-   <span data-ttu-id="9a669-113">Hiçbir öznitelik veya alt öğeleri olan ve bu tekrarlamayın, öğeleri, sütunlar olarak algılanır.</span><span class="sxs-lookup"><span data-stu-id="9a669-113">Elements that have no attributes or child elements, and that do not repeat, are inferred as columns.</span></span>  
  
-   <span data-ttu-id="9a669-114">Ayrıca ortaya çıkan diğer öğeleri içinde iç içe geçmiş tablo olarak algılanan öğeler için farklı tabloları, iç içe bir **DataRelation** iki tablo arasında oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="9a669-114">For elements that are inferred as nested tables within other elements that are also inferred as tables, a nested **DataRelation** is created between the two tables.</span></span> <span data-ttu-id="9a669-115">Adlı yeni, birincil bir anahtar sütunu **Tablename_ıd** her iki tabloya eklenen ve tarafından kullanılan **DataRelation**.</span><span class="sxs-lookup"><span data-stu-id="9a669-115">A new, primary key column named **TableName_Id** is added to both tables and used by the **DataRelation**.</span></span> <span data-ttu-id="9a669-116">A **ForeignKeyConstraint** kullanarak iki tablo arasında oluşturulan **Tablename_ıd** sütun.</span><span class="sxs-lookup"><span data-stu-id="9a669-116">A **ForeignKeyConstraint** is created between the two tables using the **TableName_Id** column.</span></span>  
  
-   <span data-ttu-id="9a669-117">Tablo olarak çıkarılan ve metin içeriyor ancak hiçbir alt öğeleri olan öğeler için yeni bir sütun adındaki **TableName_Text** metnini öğelerin her biri için oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="9a669-117">For elements that are inferred as tables and that contain text but have no child elements, a new column named **TableName_Text** is created for the text of each of the elements.</span></span> <span data-ttu-id="9a669-118">Tablo olarak algılanır ve metin ancak de alt öğeye sahip bir öğe, metin göz ardı edilir.</span><span class="sxs-lookup"><span data-stu-id="9a669-118">If an element is inferred as a table and has text, but also has child elements, the text is ignored.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a669-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9a669-119">See Also</span></span>  
 [<span data-ttu-id="9a669-120">XML’den DataSet İlişkisel Yapısını Çıkarma</span><span class="sxs-lookup"><span data-stu-id="9a669-120">Inferring DataSet Relational Structure from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)  
 [<span data-ttu-id="9a669-121">XML’den DataSet Yükleme</span><span class="sxs-lookup"><span data-stu-id="9a669-121">Loading a DataSet from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)  
 [<span data-ttu-id="9a669-122">XML’den DataSet Schema Bilgilerini Yükleme</span><span class="sxs-lookup"><span data-stu-id="9a669-122">Loading DataSet Schema Information from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)  
 [<span data-ttu-id="9a669-123">DataSet içinde XML kullanma</span><span class="sxs-lookup"><span data-stu-id="9a669-123">Using XML in a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [<span data-ttu-id="9a669-124">DataSets, DataTables ve DataViews</span><span class="sxs-lookup"><span data-stu-id="9a669-124">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="9a669-125">ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="9a669-125">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
