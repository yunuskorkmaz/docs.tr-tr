---
title: "DataTable bir veri kümesine ekleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 556d29a3-8fc9-4e38-b3ee-c188f7e7b155
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 6b72727ac42691b510e52370c937fa40baf6c006
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="adding-a-datatable-to-a-dataset"></a><span data-ttu-id="1e523-102">DataTable bir veri kümesine ekleme</span><span class="sxs-lookup"><span data-stu-id="1e523-102">Adding a DataTable to a DataSet</span></span>
<span data-ttu-id="1e523-103">ADO.NET oluşturmanıza olanak sağlayan <xref:System.Data.DataTable> nesneleri ve var olan eklemesini <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="1e523-103">ADO.NET enables you to create <xref:System.Data.DataTable> objects and add them to an existing <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="1e523-104">Kısıtlama bilgi için ayarlayabileceğiniz bir <xref:System.Data.DataTable> kullanarak <xref:System.Data.DataTable.PrimaryKey%2A> ve <xref:System.Data.DataColumn.Unique%2A> özellikleri.</span><span class="sxs-lookup"><span data-stu-id="1e523-104">You can set constraint information for a <xref:System.Data.DataTable> by using the <xref:System.Data.DataTable.PrimaryKey%2A> and <xref:System.Data.DataColumn.Unique%2A> properties.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1e523-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="1e523-105">Example</span></span>  
 <span data-ttu-id="1e523-106">Aşağıdaki örnekte oluşturur bir <xref:System.Data.DataSet>, yeni bir ekler <xref:System.Data.DataTable> nesnesini <xref:System.Data.DataSet>ve üç ekler <xref:System.Data.DataColumn> tablosuna nesneleri.</span><span class="sxs-lookup"><span data-stu-id="1e523-106">The following example constructs a <xref:System.Data.DataSet>, adds a new <xref:System.Data.DataTable> object to the <xref:System.Data.DataSet>, and then adds three <xref:System.Data.DataColumn> objects to the table.</span></span> <span data-ttu-id="1e523-107">Son olarak, bu kod bir sütun birincil anahtar sütunu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="1e523-107">Finally, the code sets one column as the primary key column.</span></span>  
  
 [!code-csharp[DataWorks Data.DataTableAdd#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks Data.DataTableAdd/CS/source.cs#1)]
 [!code-vb[DataWorks Data.DataTableAdd#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks Data.DataTableAdd/VB/source.vb#1)]  
  
## <a name="case-sensitivity"></a><span data-ttu-id="1e523-108">Büyük/küçük harfe duyarlılık</span><span class="sxs-lookup"><span data-stu-id="1e523-108">Case Sensitivity</span></span>  
 <span data-ttu-id="1e523-109">İki veya daha fazla tablo veya aynı adlı ancak farklı büyük/küçük harf, ilişkileri içinde bulunabilir bir <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="1e523-109">Two or more tables or relations with the same name, but different casing, can exist in a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="1e523-110">Böyle durumlarda, tabloları ve ilişkileri ada göre başvuruları büyük küçük harf duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="1e523-110">In such cases, references by name to tables and relations are case sensitive.</span></span> <span data-ttu-id="1e523-111">Örneğin, varsa <xref:System.Data.DataSet> **dataSet** tabloları içeren **tablo1** ve **tablo1**, başvuru **tablo1** ada göre **dataSet.Tables["Table1"]**, ve **tablo1** olarak **dataSet.Tables["table1"]**.</span><span class="sxs-lookup"><span data-stu-id="1e523-111">For example, if the <xref:System.Data.DataSet> **dataSet** contains tables **Table1** and **table1**, you would reference **Table1** by name as **dataSet.Tables["Table1"]**, and **table1** as **dataSet.Tables["table1"]**.</span></span> <span data-ttu-id="1e523-112">Tablolardan birini başvuru girişimi **dataSet.Tables["TABLE1"]** bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="1e523-112">Attempting to reference either of the tables as **dataSet.Tables["TABLE1"]** would generate an exception.</span></span>  
  
 <span data-ttu-id="1e523-113">Bir tablo veya ilişki belirli bir ada sahip yalnızca büyük küçük harf duyarlılığı davranış geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="1e523-113">The case-sensitivity behavior does not apply if only one table or relation has a particular name.</span></span> <span data-ttu-id="1e523-114">Örneğin, varsa <xref:System.Data.DataSet> yalnızca **tablo1**, kullanarak başvuru **dataSet.Tables["TABLE1"]**.</span><span class="sxs-lookup"><span data-stu-id="1e523-114">For example, if the <xref:System.Data.DataSet> has only **Table1**, you can reference it using **dataSet.Tables["TABLE1"]**.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1e523-115"><xref:System.Data.DataSet.CaseSensitive%2A> Özelliği <xref:System.Data.DataSet> bu davranışını etkilemez.</span><span class="sxs-lookup"><span data-stu-id="1e523-115">The <xref:System.Data.DataSet.CaseSensitive%2A> property of the <xref:System.Data.DataSet> does not affect this behavior.</span></span> <span data-ttu-id="1e523-116"><xref:System.Data.DataSet.CaseSensitive%2A> Özelliği uygulanır verilerde <xref:System.Data.DataSet> ve sıralama, arama, filtreleme, zorunlu kısıtlamaları ve benzeri etkiler.</span><span class="sxs-lookup"><span data-stu-id="1e523-116">The <xref:System.Data.DataSet.CaseSensitive%2A> property applies to the data in the <xref:System.Data.DataSet> and affects sorting, searching, filtering, enforcing constraints, and so on.</span></span>  
  
## <a name="namespace-support"></a><span data-ttu-id="1e523-117">Namespace desteği</span><span class="sxs-lookup"><span data-stu-id="1e523-117">Namespace Support</span></span>  
 <span data-ttu-id="1e523-118">Farklı ad alanlarında olsa bile ADO.NET'ın 2.0'den önceki sürümlerinde aynı adlı iki tablo sahip.</span><span class="sxs-lookup"><span data-stu-id="1e523-118">In versions of ADO.NET earlier than 2.0, two tables could not have the same name, even if they were in different namespaces.</span></span> <span data-ttu-id="1e523-119">Bu sınırlama aşağıdaki haller ADO.NET 2.0 kaldırıldı.</span><span class="sxs-lookup"><span data-stu-id="1e523-119">This limitation was removed in ADO.NET 2.0.</span></span> <span data-ttu-id="1e523-120">A <xref:System.Data.DataSet> aynı olan iki tablo içerebilir <xref:System.Data.DataTable.TableName%2A> özellik değeri farklı ancak <xref:System.Data.DataTable.Namespace%2A> özellik değerleri.</span><span class="sxs-lookup"><span data-stu-id="1e523-120">A <xref:System.Data.DataSet> can contain two tables that have the same <xref:System.Data.DataTable.TableName%2A> property value but different <xref:System.Data.DataTable.Namespace%2A> property values.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e523-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1e523-121">See Also</span></span>  
 [<span data-ttu-id="1e523-122">DataSets, DataTables ve DataViews</span><span class="sxs-lookup"><span data-stu-id="1e523-122">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="1e523-123">ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="1e523-123">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
