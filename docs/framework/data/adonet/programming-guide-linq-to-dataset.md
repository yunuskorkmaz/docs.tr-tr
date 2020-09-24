---
title: Programlama Kılavuzu (LINQ to DataSet)
ms.date: 03/30/2017
ms.assetid: 977aedd7-0084-46a0-b56f-345787a55da1
ms.openlocfilehash: 720d9a90583a0dcf3453689a362f6043157a326c
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91161565"
---
# <a name="programming-guide-linq-to-dataset"></a><span data-ttu-id="c5650-102">Programlama Kılavuzu (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="c5650-102">Programming Guide (LINQ to DataSet)</span></span>

<span data-ttu-id="c5650-103">Bu bölümde LINQ to DataSet programlamaya yönelik kavramsal bilgiler ve örnekler sağlanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c5650-103">This section provides conceptual information and examples for programming with LINQ to DataSet.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c5650-104">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="c5650-104">In This Section</span></span>  

 [<span data-ttu-id="c5650-105">LINQ to DataSet Sorguları</span><span class="sxs-lookup"><span data-stu-id="c5650-105">Queries in LINQ to DataSet</span></span>](queries-in-linq-to-dataset.md)  
 <span data-ttu-id="c5650-106">LINQ to DataSet sorgularının nasıl yazılacağı hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="c5650-106">Provides information about how to write LINQ to DataSet queries.</span></span>  
  
 [<span data-ttu-id="c5650-107">DataSet’leri Sorgulama</span><span class="sxs-lookup"><span data-stu-id="c5650-107">Querying DataSets</span></span>](querying-datasets-linq-to-dataset.md)  
 <span data-ttu-id="c5650-108">Nesnelerin nasıl sorgulanılacağını açıklar <xref:System.Data.DataSet> .</span><span class="sxs-lookup"><span data-stu-id="c5650-108">Describes how to query <xref:System.Data.DataSet> objects.</span></span>  
  
 [<span data-ttu-id="c5650-109">DataRow Karşılaştırma</span><span class="sxs-lookup"><span data-stu-id="c5650-109">Comparing DataRows</span></span>](comparing-datarows-linq-to-dataset.md)  
 <span data-ttu-id="c5650-110"><xref:System.Data.DataRowComparer>Veri satırlarını karşılaştırmak için nesnesinin nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="c5650-110">Describes how to use the <xref:System.Data.DataRowComparer> object to compare data rows.</span></span>  
  
 [<span data-ttu-id="c5650-111">Sorgudan DataTable Oluşturma</span><span class="sxs-lookup"><span data-stu-id="c5650-111">Creating a DataTable From a Query</span></span>](creating-a-datatable-from-a-query-linq-to-dataset.md)  
 <span data-ttu-id="c5650-112">Yöntemini kullanarak bir LINQ to DataSet sorgusundan oluşturma hakkında bilgi sağlar <xref:System.Data.DataTable> <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> .</span><span class="sxs-lookup"><span data-stu-id="c5650-112">Provides information about creating a <xref:System.Data.DataTable> from a LINQ to DataSet query by using the <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> method.</span></span>  
  
 [<span data-ttu-id="c5650-113">Nasıl yapılır: \<T> genel tür T 'nin bir DataRow olmadığı CopyToDataTable uygulama</span><span class="sxs-lookup"><span data-stu-id="c5650-113">How to: Implement CopyToDataTable\<T> Where the Generic Type T Is Not a DataRow</span></span>](implement-copytodatatable-where-type-not-a-datarow.md)  
 <span data-ttu-id="c5650-114">`CopyToDataTable<T>`Genel parametre T türünde olmayan bir özel yöntemin nasıl uygulanacağını açıklar <xref:System.Data.DataRow> .</span><span class="sxs-lookup"><span data-stu-id="c5650-114">Describes how to implement a custom `CopyToDataTable<T>` method where the generic parameter T is not of type <xref:System.Data.DataRow>.</span></span>  
  
 [<span data-ttu-id="c5650-115">Genel Alan ve SetField Yöntemleri</span><span class="sxs-lookup"><span data-stu-id="c5650-115">Generic Field and SetField Methods</span></span>](generic-field-and-setfield-methods-linq-to-dataset.md)  
 <span data-ttu-id="c5650-116">Genel ve yöntemler hakkında bilgi <xref:System.Data.DataRowExtensions.Field%2A> sağlar <xref:System.Data.DataRowExtensions.SetField%2A> .</span><span class="sxs-lookup"><span data-stu-id="c5650-116">Provides information about the generic <xref:System.Data.DataRowExtensions.Field%2A> and <xref:System.Data.DataRowExtensions.SetField%2A> methods.</span></span>  
  
 [<span data-ttu-id="c5650-117">Veri Bağlama ve LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="c5650-117">Data Binding and LINQ to DataSet</span></span>](data-binding-and-linq-to-dataset.md)  
 <span data-ttu-id="c5650-118">Nesnesini kullanarak veri bağlamayı açıklar <xref:System.Data.DataView> .</span><span class="sxs-lookup"><span data-stu-id="c5650-118">Describes databinding using the <xref:System.Data.DataView> object.</span></span>  
  
 [<span data-ttu-id="c5650-119">LINQ to DataSet Sorgularında Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="c5650-119">Debugging LINQ to DataSet Queries</span></span>](debugging-linq-to-dataset-queries.md)  
 <span data-ttu-id="c5650-120">Hata ayıklama ve sorgu sorunlarını giderme hakkında bilgi sağlar LINQ to DataSet.</span><span class="sxs-lookup"><span data-stu-id="c5650-120">Provides information about debugging and troubleshooting LINQ to DataSet queries.</span></span>  
  
 [<span data-ttu-id="c5650-121">Güvenlik</span><span class="sxs-lookup"><span data-stu-id="c5650-121">Security</span></span>](security-linq-to-dataset.md)  
 <span data-ttu-id="c5650-122">LINQ to DataSet güvenlik sorunlarını açıklar.</span><span class="sxs-lookup"><span data-stu-id="c5650-122">Describes security issues in LINQ to DataSet.</span></span>  
  
 [<span data-ttu-id="c5650-123">LINQ to DataSet Örnekleri</span><span class="sxs-lookup"><span data-stu-id="c5650-123">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)  
 <span data-ttu-id="c5650-124">LINQ işleçlerini kullanan sorgu örnekleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="c5650-124">Provides query examples that use the LINQ operators.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="c5650-125">Başvuru</span><span class="sxs-lookup"><span data-stu-id="c5650-125">Reference</span></span>  

 <xref:System.Data.DataRowComparer>  
  
 <xref:System.Data.DataRowExtensions>  
  
 <xref:System.Data.DataTableExtensions>  
  
 <xref:System.Data.DataView>  
  
## <a name="see-also"></a><span data-ttu-id="c5650-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c5650-126">See also</span></span>

- [<span data-ttu-id="c5650-127">LINQ ve ADO.NET</span><span class="sxs-lookup"><span data-stu-id="c5650-127">LINQ and ADO.NET</span></span>](linq-and-ado-net.md)
- [<span data-ttu-id="c5650-128">Dil ile Tümleşik Sorgu (LINQ)</span><span class="sxs-lookup"><span data-stu-id="c5650-128">Language Integrated Query (LINQ)</span></span>](../../../csharp/programming-guide/concepts/linq/index.md)
