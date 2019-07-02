---
title: Programlama Kılavuzu (LINQ to DataSet)
ms.date: 03/30/2017
ms.assetid: 977aedd7-0084-46a0-b56f-345787a55da1
ms.openlocfilehash: d454448771e14b1a540b5a066683bd4c747991ec
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67504782"
---
# <a name="programming-guide-linq-to-dataset"></a><span data-ttu-id="8fcf0-102">Programlama Kılavuzu (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="8fcf0-102">Programming Guide (LINQ to DataSet)</span></span>
<span data-ttu-id="8fcf0-103">Bu bölümde kavramsal bilgiler ve örnekler için LINQ ile programlama için veri kümesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="8fcf0-103">This section provides conceptual information and examples for programming with LINQ to DataSet.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8fcf0-104">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="8fcf0-104">In This Section</span></span>  
 [<span data-ttu-id="8fcf0-105">LINQ to DataSet Sorguları</span><span class="sxs-lookup"><span data-stu-id="8fcf0-105">Queries in LINQ to DataSet</span></span>](../../../../docs/framework/data/adonet/queries-in-linq-to-dataset.md)  
 <span data-ttu-id="8fcf0-106">DataSet sorgularında LINQ yazma hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="8fcf0-106">Provides information about how to write LINQ to DataSet queries.</span></span>  
  
 [<span data-ttu-id="8fcf0-107">DataSet’leri Sorgulama</span><span class="sxs-lookup"><span data-stu-id="8fcf0-107">Querying DataSets</span></span>](../../../../docs/framework/data/adonet/querying-datasets-linq-to-dataset.md)  
 <span data-ttu-id="8fcf0-108">Açıklayan nasıl sorgu <xref:System.Data.DataSet> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="8fcf0-108">Describes how to query <xref:System.Data.DataSet> objects.</span></span>  
  
 [<span data-ttu-id="8fcf0-109">DataRow Karşılaştırma</span><span class="sxs-lookup"><span data-stu-id="8fcf0-109">Comparing DataRows</span></span>](../../../../docs/framework/data/adonet/comparing-datarows-linq-to-dataset.md)  
 <span data-ttu-id="8fcf0-110">Nasıl kullanılacağını açıklar <xref:System.Data.DataRowComparer> veri satırları Karşılaştırılacak nesne.</span><span class="sxs-lookup"><span data-stu-id="8fcf0-110">Describes how to use the <xref:System.Data.DataRowComparer> object to compare data rows.</span></span>  
  
 [<span data-ttu-id="8fcf0-111">Sorgudan DataTable Oluşturma</span><span class="sxs-lookup"><span data-stu-id="8fcf0-111">Creating a DataTable From a Query</span></span>](../../../../docs/framework/data/adonet/creating-a-datatable-from-a-query-linq-to-dataset.md)  
 <span data-ttu-id="8fcf0-112">Oluşturma hakkında bilgi sağlayan bir <xref:System.Data.DataTable> bir LINQ to DataSet sorgu kullanarak gelen <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="8fcf0-112">Provides information about creating a <xref:System.Data.DataTable> from a LINQ to DataSet query by using the <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> method.</span></span>  
  
 [<span data-ttu-id="8fcf0-113">Nasıl yapılır: CopyToDataTable uygulamak\<T > Burada T genel türünün DataRow olmadığı</span><span class="sxs-lookup"><span data-stu-id="8fcf0-113">How to: Implement CopyToDataTable\<T> Where the Generic Type T Is Not a DataRow</span></span>](../../../../docs/framework/data/adonet/implement-copytodatatable-where-type-not-a-datarow.md)  
 <span data-ttu-id="8fcf0-114">Özel bir uygulamayı açıklar `CopyToDataTable<T>` yöntemi burada genel parametre T türünde değil <xref:System.Data.DataRow>.</span><span class="sxs-lookup"><span data-stu-id="8fcf0-114">Describes how to implement a custom `CopyToDataTable<T>` method where the generic parameter T is not of type <xref:System.Data.DataRow>.</span></span>  
  
 [<span data-ttu-id="8fcf0-115">Genel Alan ve SetField Yöntemleri</span><span class="sxs-lookup"><span data-stu-id="8fcf0-115">Generic Field and SetField Methods</span></span>](../../../../docs/framework/data/adonet/generic-field-and-setfield-methods-linq-to-dataset.md)  
 <span data-ttu-id="8fcf0-116">Genel hakkında bilgi sağlar <xref:System.Data.DataRowExtensions.Field%2A> ve <xref:System.Data.DataRowExtensions.SetField%2A> yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="8fcf0-116">Provides information about the generic <xref:System.Data.DataRowExtensions.Field%2A> and <xref:System.Data.DataRowExtensions.SetField%2A> methods.</span></span>  
  
 [<span data-ttu-id="8fcf0-117">Veri Bağlama ve LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="8fcf0-117">Data Binding and LINQ to DataSet</span></span>](../../../../docs/framework/data/adonet/data-binding-and-linq-to-dataset.md)  
 <span data-ttu-id="8fcf0-118">Veri bağlamasını kullanma açıklanmaktadır <xref:System.Data.DataView> nesne.</span><span class="sxs-lookup"><span data-stu-id="8fcf0-118">Describes databinding using the <xref:System.Data.DataView> object.</span></span>  
  
 [<span data-ttu-id="8fcf0-119">LINQ to DataSet Sorgularında Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="8fcf0-119">Debugging LINQ to DataSet Queries</span></span>](../../../../docs/framework/data/adonet/debugging-linq-to-dataset-queries.md)  
 <span data-ttu-id="8fcf0-120">Hata ayıklama ve LINQ sorguları DataSet sorun giderme hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="8fcf0-120">Provides information about debugging and troubleshooting LINQ to DataSet queries.</span></span>  
  
 [<span data-ttu-id="8fcf0-121">Güvenlik</span><span class="sxs-lookup"><span data-stu-id="8fcf0-121">Security</span></span>](../../../../docs/framework/data/adonet/security-linq-to-dataset.md)  
 <span data-ttu-id="8fcf0-122">LINQ to DataSet güvenlik konularını açıklar.</span><span class="sxs-lookup"><span data-stu-id="8fcf0-122">Describes security issues in LINQ to DataSet.</span></span>  
  
 [<span data-ttu-id="8fcf0-123">LINQ to DataSet Örnekleri</span><span class="sxs-lookup"><span data-stu-id="8fcf0-123">LINQ to DataSet Examples</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)  
 <span data-ttu-id="8fcf0-124">Kullanan bir sorgu örnekleri sağlar [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] işleçleri.</span><span class="sxs-lookup"><span data-stu-id="8fcf0-124">Provides query examples that use the [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] operators.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="8fcf0-125">Başvuru</span><span class="sxs-lookup"><span data-stu-id="8fcf0-125">Reference</span></span>  
 <xref:System.Data.DataRowComparer>  
  
 <xref:System.Data.DataRowExtensions>  
  
 <xref:System.Data.DataTableExtensions>  
  
 <xref:System.Data.DataView>  
  
## <a name="see-also"></a><span data-ttu-id="8fcf0-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8fcf0-126">See also</span></span>

- [<span data-ttu-id="8fcf0-127">LINQ ve ADO.NET</span><span class="sxs-lookup"><span data-stu-id="8fcf0-127">LINQ and ADO.NET</span></span>](linq-and-ado-net.md)
- [<span data-ttu-id="8fcf0-128">Dil ile Tümleşik Sorgu (LINQ)</span><span class="sxs-lookup"><span data-stu-id="8fcf0-128">Language Integrated Query (LINQ)</span></span>](../../../csharp/programming-guide/concepts/linq/index.md)
