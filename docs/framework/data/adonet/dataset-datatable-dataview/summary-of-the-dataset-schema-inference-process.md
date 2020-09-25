---
title: DataSet Şema Çıkarımı İşleminin Özeti
ms.date: 03/30/2017
ms.assetid: fd0891c8-d068-4e30-a76f-7c375f078bf7
ms.openlocfilehash: 8d517487b96aa7f204ea9f25d326500db7df413a
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91198515"
---
# <a name="summary-of-the-dataset-schema-inference-process"></a><span data-ttu-id="dc3cb-102">DataSet Şema Çıkarımı İşleminin Özeti</span><span class="sxs-lookup"><span data-stu-id="dc3cb-102">Summary of the DataSet Schema Inference Process</span></span>

<span data-ttu-id="dc3cb-103">Çıkarım işlemi ilk olarak XML belgesinden, hangi öğelerin tablo olarak gösterileceğini belirler.</span><span class="sxs-lookup"><span data-stu-id="dc3cb-103">The inference process first determines, from the XML document, which elements will be inferred as tables.</span></span> <span data-ttu-id="dc3cb-104">Kalan XML 'den, çıkarım işlemi bu tabloların sütunlarını belirler.</span><span class="sxs-lookup"><span data-stu-id="dc3cb-104">From the remaining XML, the inference process determines the columns for those tables.</span></span> <span data-ttu-id="dc3cb-105">İç içe tablolar için, çıkarım işlemi iç içe <xref:System.Data.DataRelation> ve <xref:System.Data.ForeignKeyConstraint> nesneler oluşturur.</span><span class="sxs-lookup"><span data-stu-id="dc3cb-105">For nested tables, the inference process generates nested <xref:System.Data.DataRelation> and <xref:System.Data.ForeignKeyConstraint> objects.</span></span>  
  
 <span data-ttu-id="dc3cb-106">Aşağıda, çıkarım kurallarının kısa bir özeti verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="dc3cb-106">The following is a brief summary of inference rules:</span></span>  
  
- <span data-ttu-id="dc3cb-107">Öznitelikleri olan öğeler tablo olarak algılanır.</span><span class="sxs-lookup"><span data-stu-id="dc3cb-107">Elements that have attributes are inferred as tables.</span></span>  
  
- <span data-ttu-id="dc3cb-108">Alt öğeleri olan öğeler tablo olarak algılanır.</span><span class="sxs-lookup"><span data-stu-id="dc3cb-108">Elements that have child elements are inferred as tables.</span></span>  
  
- <span data-ttu-id="dc3cb-109">Yinelenen öğeler tek bir tablo olarak algılanır.</span><span class="sxs-lookup"><span data-stu-id="dc3cb-109">Elements that repeat are inferred as a single table.</span></span>  
  
- <span data-ttu-id="dc3cb-110">Belge, veya kök, öğe bir özniteliğe sahip değilse ve sütun olarak çıkarsanmayacak alt öğe yoksa, bir olarak algılanır <xref:System.Data.DataSet> .</span><span class="sxs-lookup"><span data-stu-id="dc3cb-110">If the document, or root, element has no attributes, and no child elements that would be inferred as columns, it is inferred as a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="dc3cb-111">Aksi halde, belge öğesi tablo olarak algılanır.</span><span class="sxs-lookup"><span data-stu-id="dc3cb-111">Otherwise, the document element is inferred as a table.</span></span>  
  
- <span data-ttu-id="dc3cb-112">Öznitelikler sütun olarak algılanır.</span><span class="sxs-lookup"><span data-stu-id="dc3cb-112">Attributes are inferred as columns.</span></span>  
  
- <span data-ttu-id="dc3cb-113">Öznitelikleri veya alt öğeleri olmayan ve tekrarsız öğeler sütun olarak algılanır.</span><span class="sxs-lookup"><span data-stu-id="dc3cb-113">Elements that have no attributes or child elements, and that do not repeat, are inferred as columns.</span></span>  
  
- <span data-ttu-id="dc3cb-114">Tablo olarak da gösterilen diğer öğeler içinde iç içe geçmiş tablolar olarak gösterilen öğeler için, iki tablo arasında iç içe bir **DataRelation** oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="dc3cb-114">For elements that are inferred as nested tables within other elements that are also inferred as tables, a nested **DataRelation** is created between the two tables.</span></span> <span data-ttu-id="dc3cb-115">**TableName_Id** adlı yeni bir birincil anahtar sütunu her iki tabloya da eklenir ve **DataRelation**tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="dc3cb-115">A new, primary key column named **TableName_Id** is added to both tables and used by the **DataRelation**.</span></span> <span data-ttu-id="dc3cb-116">**TableName_Id** sütunu kullanılarak iki tablo arasında bir **ForeignKeyConstraint** oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="dc3cb-116">A **ForeignKeyConstraint** is created between the two tables using the **TableName_Id** column.</span></span>  
  
- <span data-ttu-id="dc3cb-117">Tablo olarak gösterilen ve metin içeren ancak hiç alt öğesi olmayan öğeler için, öğelerin her birinin metni için **TableName_Text** adlı yeni bir sütun oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="dc3cb-117">For elements that are inferred as tables and that contain text but have no child elements, a new column named **TableName_Text** is created for the text of each of the elements.</span></span> <span data-ttu-id="dc3cb-118">Bir öğe tablo olarak algılanır ve metin içeriyorsa, ancak alt öğeleri de varsa, metin yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="dc3cb-118">If an element is inferred as a table and has text, but also has child elements, the text is ignored.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc3cb-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dc3cb-119">See also</span></span>

- [<span data-ttu-id="dc3cb-120">XML’den DataSet İlişkisel Yapısını Çıkarma</span><span class="sxs-lookup"><span data-stu-id="dc3cb-120">Inferring DataSet Relational Structure from XML</span></span>](inferring-dataset-relational-structure-from-xml.md)
- [<span data-ttu-id="dc3cb-121">XML’den DataSet Yükleme</span><span class="sxs-lookup"><span data-stu-id="dc3cb-121">Loading a DataSet from XML</span></span>](loading-a-dataset-from-xml.md)
- [<span data-ttu-id="dc3cb-122">XML’den DataSet Schema Bilgilerini Yükleme</span><span class="sxs-lookup"><span data-stu-id="dc3cb-122">Loading DataSet Schema Information from XML</span></span>](loading-dataset-schema-information-from-xml.md)
- [<span data-ttu-id="dc3cb-123">DataSet içinde XML kullanma</span><span class="sxs-lookup"><span data-stu-id="dc3cb-123">Using XML in a DataSet</span></span>](using-xml-in-a-dataset.md)
- [<span data-ttu-id="dc3cb-124">DataSets, DataTables ve DataViews</span><span class="sxs-lookup"><span data-stu-id="dc3cb-124">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="dc3cb-125">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="dc3cb-125">ADO.NET Overview</span></span>](../ado-net-overview.md)
