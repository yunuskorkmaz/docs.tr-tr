---
title: DataSet’e DataTable Ekleme
description: DataTable nesneleri oluşturma ve bunları ADO.NET içinde mevcut bir veri kümesine ekleme hakkında bilgi edinmek için bu örnek koda bakın.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 556d29a3-8fc9-4e38-b3ee-c188f7e7b155
ms.openlocfilehash: 6a5e3a89870b3959a6ac042b93414694e8a6cc1c
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91164902"
---
# <a name="adding-a-datatable-to-a-dataset"></a><span data-ttu-id="c32b7-103">DataSet’e DataTable Ekleme</span><span class="sxs-lookup"><span data-stu-id="c32b7-103">Adding a DataTable to a DataSet</span></span>

<span data-ttu-id="c32b7-104">ADO.NET, <xref:System.Data.DataTable> nesneleri oluşturmanızı ve bunları var olan bir nesneye eklemenizi sağlar <xref:System.Data.DataSet> .</span><span class="sxs-lookup"><span data-stu-id="c32b7-104">ADO.NET enables you to create <xref:System.Data.DataTable> objects and add them to an existing <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="c32b7-105"><xref:System.Data.DataTable>Ve özelliklerini kullanarak bir için kısıtlama bilgileri ayarlayabilirsiniz <xref:System.Data.DataTable.PrimaryKey%2A> <xref:System.Data.DataColumn.Unique%2A> .</span><span class="sxs-lookup"><span data-stu-id="c32b7-105">You can set constraint information for a <xref:System.Data.DataTable> by using the <xref:System.Data.DataTable.PrimaryKey%2A> and <xref:System.Data.DataColumn.Unique%2A> properties.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c32b7-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="c32b7-106">Example</span></span>  

 <span data-ttu-id="c32b7-107">Aşağıdaki örnek bir oluşturur <xref:System.Data.DataSet> , öğesine yeni bir <xref:System.Data.DataTable> nesnesi ekler <xref:System.Data.DataSet> ve ardından <xref:System.Data.DataColumn> tabloya üç nesne ekler.</span><span class="sxs-lookup"><span data-stu-id="c32b7-107">The following example constructs a <xref:System.Data.DataSet>, adds a new <xref:System.Data.DataTable> object to the <xref:System.Data.DataSet>, and then adds three <xref:System.Data.DataColumn> objects to the table.</span></span> <span data-ttu-id="c32b7-108">Son olarak, kod bir sütunu birincil anahtar sütunu olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="c32b7-108">Finally, the code sets one column as the primary key column.</span></span>  
  
 [!code-csharp[DataWorks Data.DataTableAdd#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks Data.DataTableAdd/CS/source.cs#1)]
 [!code-vb[DataWorks Data.DataTableAdd#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks Data.DataTableAdd/VB/source.vb#1)]  
  
## <a name="case-sensitivity"></a><span data-ttu-id="c32b7-109">Büyük/küçük harf duyarlılığı</span><span class="sxs-lookup"><span data-stu-id="c32b7-109">Case Sensitivity</span></span>  

 <span data-ttu-id="c32b7-110">İki veya daha fazla tablo veya aynı ada sahip, ancak büyük küçük harfe sahip ilişkiler bir içinde bulunabilir <xref:System.Data.DataSet> .</span><span class="sxs-lookup"><span data-stu-id="c32b7-110">Two or more tables or relations with the same name, but different casing, can exist in a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="c32b7-111">Bu gibi durumlarda, tabloya ve ilişkilerde ada göre başvurular büyük/küçük harfe duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="c32b7-111">In such cases, references by name to tables and relations are case sensitive.</span></span> <span data-ttu-id="c32b7-112">Örneğin, <xref:System.Data.DataSet> **veri kümesi** **Table1** ve **Table1**tabloları Içeriyorsa, **Table1** adına ad **DataSet. Tables ["Table1"]** ve **Table1** as **DataSet. Tables ["Table1"]** olarak başvurabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c32b7-112">For example, if the <xref:System.Data.DataSet> **dataSet** contains tables **Table1** and **table1**, you would reference **Table1** by name as **dataSet.Tables["Table1"]**, and **table1** as **dataSet.Tables["table1"]**.</span></span> <span data-ttu-id="c32b7-113">Veri kümesi olarak tablolardan birine başvurulmaya çalışılıyor **. tablolar ["Table1"]** bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c32b7-113">Attempting to reference either of the tables as **dataSet.Tables["TABLE1"]** would generate an exception.</span></span>  
  
 <span data-ttu-id="c32b7-114">Yalnızca bir tablo veya ilişki belirli bir ada sahipse, büyük/küçük harf duyarlılığı davranışı uygulanmaz.</span><span class="sxs-lookup"><span data-stu-id="c32b7-114">The case-sensitivity behavior does not apply if only one table or relation has a particular name.</span></span> <span data-ttu-id="c32b7-115">Örneğin, <xref:System.Data.DataSet> yalnızca **Table1**ise, **DataSet. Tables ["Table1"]** kullanarak buna başvurabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c32b7-115">For example, if the <xref:System.Data.DataSet> has only **Table1**, you can reference it using **dataSet.Tables["TABLE1"]**.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c32b7-116"><xref:System.Data.DataSet.CaseSensitive%2A>Öğesinin özelliği <xref:System.Data.DataSet> Bu davranışı etkilemez.</span><span class="sxs-lookup"><span data-stu-id="c32b7-116">The <xref:System.Data.DataSet.CaseSensitive%2A> property of the <xref:System.Data.DataSet> does not affect this behavior.</span></span> <span data-ttu-id="c32b7-117"><xref:System.Data.DataSet.CaseSensitive%2A>Özelliği, içindeki veriler için geçerlidir <xref:System.Data.DataSet> ve sıralamayı, aramayı, filtrelemeyi, kısıtlamaları zorunlu tutmayı ve benzerlerini etkiler.</span><span class="sxs-lookup"><span data-stu-id="c32b7-117">The <xref:System.Data.DataSet.CaseSensitive%2A> property applies to the data in the <xref:System.Data.DataSet> and affects sorting, searching, filtering, enforcing constraints, and so on.</span></span>  
  
## <a name="namespace-support"></a><span data-ttu-id="c32b7-118">Ad alanı desteği</span><span class="sxs-lookup"><span data-stu-id="c32b7-118">Namespace Support</span></span>  

 <span data-ttu-id="c32b7-119">2,0 'den önceki ADO.NET sürümlerinde, farklı ad boşluklarında olsalar bile, iki tablo aynı ada sahip olamaz.</span><span class="sxs-lookup"><span data-stu-id="c32b7-119">In versions of ADO.NET earlier than 2.0, two tables could not have the same name, even if they were in different namespaces.</span></span> <span data-ttu-id="c32b7-120">Bu sınırlama, ADO.NET 2,0 ' de kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="c32b7-120">This limitation was removed in ADO.NET 2.0.</span></span> <span data-ttu-id="c32b7-121"><xref:System.Data.DataSet>, Aynı <xref:System.Data.DataTable.TableName%2A> özellik değerine sahip ancak farklı özellik değerlerine sahip iki tablo içerebilir <xref:System.Data.DataTable.Namespace%2A> .</span><span class="sxs-lookup"><span data-stu-id="c32b7-121">A <xref:System.Data.DataSet> can contain two tables that have the same <xref:System.Data.DataTable.TableName%2A> property value but different <xref:System.Data.DataTable.Namespace%2A> property values.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c32b7-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c32b7-122">See also</span></span>

- [<span data-ttu-id="c32b7-123">DataSets, DataTables ve DataViews</span><span class="sxs-lookup"><span data-stu-id="c32b7-123">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="c32b7-124">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="c32b7-124">ADO.NET Overview</span></span>](../ado-net-overview.md)
