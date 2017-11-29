---
title: "DataTable şema tanımı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: efbcdda4-f5a9-421d-8be2-4c194c74552f
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: be5969bf8653512da27785479ac7feae1f6c09a1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="datatable-schema-definition"></a><span data-ttu-id="58179-102">DataTable şema tanımı</span><span class="sxs-lookup"><span data-stu-id="58179-102">DataTable Schema Definition</span></span>
<span data-ttu-id="58179-103">Sütunları ve kısıtlamalar tarafından kullanılacak şema veya bir tablonun yapısını temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="58179-103">The schema, or structure, of a table is represented by columns and constraints.</span></span> <span data-ttu-id="58179-104">Şemasını tanımlayan bir <xref:System.Data.DataTable> kullanarak <xref:System.Data.DataColumn> nesneleri yanı <xref:System.Data.ForeignKeyConstraint> ve <xref:System.Data.UniqueConstraint> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="58179-104">You define the schema of a <xref:System.Data.DataTable> using <xref:System.Data.DataColumn> objects as well as <xref:System.Data.ForeignKeyConstraint> and <xref:System.Data.UniqueConstraint> objects.</span></span> <span data-ttu-id="58179-105">Bir tablodaki sütun bir veri kaynağındaki sütunları eşlemek, ifadeler hesaplanan değerler içeren, otomatik olarak değerlerine artırın veya birincil anahtar değerlerini içeriyor.</span><span class="sxs-lookup"><span data-stu-id="58179-105">The columns in a table can map to columns in a data source, contain calculated values from expressions, automatically increment their values, or contain primary key values.</span></span>  
  
 <span data-ttu-id="58179-106">Sütunları, ilişkileri ve kısıtlamaları bir tabloda ada göre başvurular büyük/küçük harfe duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="58179-106">References by name to columns, relations, and constraints in a table are case-sensitive.</span></span> <span data-ttu-id="58179-107">Bu nedenle iki veya daha fazla sütun, ilişkileri veya kısıtlamaları aynı ada sahip, ancak bu durumda farklı bir tabloda bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="58179-107">Two or more columns, relations, or constraints can therefore exist in a table that have the same name, but that differ in case.</span></span> <span data-ttu-id="58179-108">Örneğin, sahip **Col1** ve **col1**.</span><span class="sxs-lookup"><span data-stu-id="58179-108">For example, you can have **Col1** and **col1**.</span></span> <span data-ttu-id="58179-109">İçinde durumda gibi ada göre sütunlardan biri için bir başvuru sütun adı durumunun tam olarak eşleşmelidir; Aksi takdirde özel durum oluşur.</span><span class="sxs-lookup"><span data-stu-id="58179-109">In such as case, a reference to one of the columns by name must match the case of the column name exactly; otherwise an exception is thrown.</span></span> <span data-ttu-id="58179-110">Örneğin, varsa tablonun **myTable** sütunları içeren **Col1** ve **col1**, başvuru **Col1** ada göre  **myTable.Columns["Col1"]**, ve **col1** olarak **myTable.Columns["col1"]**.</span><span class="sxs-lookup"><span data-stu-id="58179-110">For example, if the table **myTable** contains the columns **Col1** and **col1**, you would reference **Col1** by name as **myTable.Columns["Col1"]**, and **col1** as **myTable.Columns["col1"]**.</span></span> <span data-ttu-id="58179-111">Ya da sütun olarak başvuru girişimi **myTable.Columns["COL1"]** bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="58179-111">Attempting to reference either of the columns as **myTable.Columns["COL1"]** would generate an exception.</span></span>  
  
 <span data-ttu-id="58179-112">Yalnızca bir sütun, ilişki veya belirli bir ad ile kısıtlaması varsa büyük küçük harf duyarlılığı kuralı geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="58179-112">The case-sensitivity rule does not apply if only one column, relation, or constraint  with a particular name exists.</span></span> <span data-ttu-id="58179-113">Diğer bir deyişle, diğer hiçbir sütun, ilişki veya tablosundaki kısıtlama nesnesi bu belirli sütun, ilişki veya kısıtlama nesnesi adı eşleşirse, herhangi bir durumu kullanarak adıyla nesne başvurusundan ve hiçbir özel durum oluşur.</span><span class="sxs-lookup"><span data-stu-id="58179-113">That is, if no other column, relation, or constraint object in the table matches the name of that particular column, relation, or constraint object, you may reference the object by name using any case, and no exception is thrown.</span></span> <span data-ttu-id="58179-114">Örneğin, tablo yalnızca varsa **Col1**, kullanarak başvuru **my. Sütunlar ["COL1"]**.</span><span class="sxs-lookup"><span data-stu-id="58179-114">For example, if the table has only **Col1**, you can reference it using **my.Columns["COL1"]**.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="58179-115"><xref:System.Data.DataTable.CaseSensitive%2A> Özelliği **DataTable** bu davranışını etkilemez.</span><span class="sxs-lookup"><span data-stu-id="58179-115">The <xref:System.Data.DataTable.CaseSensitive%2A> property of the **DataTable** does not affect this behavior.</span></span> <span data-ttu-id="58179-116">**CaseSensitive** özelliği, bir tablo ve kısıtlamalar ve benzeri zorlamayı sıralama, filtreleme, aramayı etkiler veriler, ancak sütun, ilişkileri ve kısıtlamaları başvuruları uygulanır.</span><span class="sxs-lookup"><span data-stu-id="58179-116">The **CaseSensitive** property applies to the data in a table and affects sorting, searching, filtering, enforcing constraints, and so on, but not to references to the columns, relations, and constraints.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="58179-117">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="58179-117">In This Section</span></span>  
 [<span data-ttu-id="58179-118">DataTable tablosuna sütun ekleme</span><span class="sxs-lookup"><span data-stu-id="58179-118">Adding Columns to a DataTable</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/adding-columns-to-a-datatable.md)  
 <span data-ttu-id="58179-119">Kullanarak bir tablo sütunları tanımlamak açıklar **DataColumn** nesneleri.</span><span class="sxs-lookup"><span data-stu-id="58179-119">Describes how to define the columns of a table using **DataColumn** objects.</span></span>  
  
 [<span data-ttu-id="58179-120">İfade sütunları oluşturma</span><span class="sxs-lookup"><span data-stu-id="58179-120">Creating Expression Columns</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-expression-columns.md)  
 <span data-ttu-id="58179-121">Açıklar nasıl **ifade** bir sütunun özelliği, satırda başka sütunlardan değerlere göre değerleri hesaplamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="58179-121">Explains how the **Expression** property of a column can be used to calculate values based on the values from other columns in the row.</span></span>  
  
 [<span data-ttu-id="58179-122">AutoIncrement sütunlar oluşturma</span><span class="sxs-lookup"><span data-stu-id="58179-122">Creating AutoIncrement Columns</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-autoincrement-columns.md)  
 <span data-ttu-id="58179-123">Sayısal değerler, satır başına bir benzersiz sütun değeri sağlamak için otomatik olarak artırmak için bir sütun nasıl ayarlanabilir açıklar.</span><span class="sxs-lookup"><span data-stu-id="58179-123">Describes how a column can be set to automatically increment numerical values to ensure a unique column value per row.</span></span>  
  
 [<span data-ttu-id="58179-124">Birincil anahtarlar tanımlama</span><span class="sxs-lookup"><span data-stu-id="58179-124">Defining Primary Keys</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/defining-primary-keys.md)  
 <span data-ttu-id="58179-125">Bir veya daha fazla bir tablonun birincil anahtarı belirtmek açıklar **DataColumn** nesneleri.</span><span class="sxs-lookup"><span data-stu-id="58179-125">Describes how to specify the primary key of a table from one or more **DataColumn** objects.</span></span>  
  
 [<span data-ttu-id="58179-126">DataTable kısıtlamaları</span><span class="sxs-lookup"><span data-stu-id="58179-126">DataTable Constraints</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-constraints.md)  
 <span data-ttu-id="58179-127">Yabancı anahtar ve benzersiz kısıtlamalar sütunlar için bir tabloda nasıl tanımlanacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="58179-127">Describes how to define foreign key and unique constraints for columns in a table.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58179-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="58179-128">See Also</span></span>  
 [<span data-ttu-id="58179-129">DataTables</span><span class="sxs-lookup"><span data-stu-id="58179-129">DataTables</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 [<span data-ttu-id="58179-130">ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="58179-130">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
