---
title: Programlama Kılavuzu (LINQ to DataSet)
ms.date: 03/30/2017
ms.assetid: 977aedd7-0084-46a0-b56f-345787a55da1
ms.openlocfilehash: dc13af06cf6c439d739d76904f206ebc50ba3187
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/03/2020
ms.locfileid: "75634813"
---
# <a name="programming-guide-linq-to-dataset"></a><span data-ttu-id="6fefe-102">Programlama Kılavuzu (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="6fefe-102">Programming Guide (LINQ to DataSet)</span></span>
<span data-ttu-id="6fefe-103">Bu bölümde LINQ to DataSet programlamaya yönelik kavramsal bilgiler ve örnekler sağlanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6fefe-103">This section provides conceptual information and examples for programming with LINQ to DataSet.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6fefe-104">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="6fefe-104">In This Section</span></span>  
 [<span data-ttu-id="6fefe-105">LINQ to DataSet Sorguları</span><span class="sxs-lookup"><span data-stu-id="6fefe-105">Queries in LINQ to DataSet</span></span>](queries-in-linq-to-dataset.md)  
 <span data-ttu-id="6fefe-106">LINQ to DataSet sorgularının nasıl yazılacağı hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="6fefe-106">Provides information about how to write LINQ to DataSet queries.</span></span>  
  
 [<span data-ttu-id="6fefe-107">DataSet’leri Sorgulama</span><span class="sxs-lookup"><span data-stu-id="6fefe-107">Querying DataSets</span></span>](querying-datasets-linq-to-dataset.md)  
 <span data-ttu-id="6fefe-108"><xref:System.Data.DataSet> nesnelerinin nasıl sorgulanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="6fefe-108">Describes how to query <xref:System.Data.DataSet> objects.</span></span>  
  
 [<span data-ttu-id="6fefe-109">DataRow Karşılaştırma</span><span class="sxs-lookup"><span data-stu-id="6fefe-109">Comparing DataRows</span></span>](comparing-datarows-linq-to-dataset.md)  
 <span data-ttu-id="6fefe-110">Veri satırlarını karşılaştırmak için <xref:System.Data.DataRowComparer> nesnesinin nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="6fefe-110">Describes how to use the <xref:System.Data.DataRowComparer> object to compare data rows.</span></span>  
  
 [<span data-ttu-id="6fefe-111">Sorgudan DataTable Oluşturma</span><span class="sxs-lookup"><span data-stu-id="6fefe-111">Creating a DataTable From a Query</span></span>](creating-a-datatable-from-a-query-linq-to-dataset.md)  
 <span data-ttu-id="6fefe-112"><xref:System.Data.DataTableExtensions.CopyToDataTable%2A> yöntemini kullanarak bir LINQ to DataSet sorgusundan <xref:System.Data.DataTable> oluşturma hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="6fefe-112">Provides information about creating a <xref:System.Data.DataTable> from a LINQ to DataSet query by using the <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> method.</span></span>  
  
 [<span data-ttu-id="6fefe-113">Nasıl yapılır: genel tür T 'Nin bir DataRow olmadığı CopyToDataTable\<T > uygulama</span><span class="sxs-lookup"><span data-stu-id="6fefe-113">How to: Implement CopyToDataTable\<T> Where the Generic Type T Is Not a DataRow</span></span>](implement-copytodatatable-where-type-not-a-datarow.md)  
 <span data-ttu-id="6fefe-114">Genel parametre T <xref:System.Data.DataRow>türünde olmayan bir özel `CopyToDataTable<T>` yönteminin nasıl uygulanacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="6fefe-114">Describes how to implement a custom `CopyToDataTable<T>` method where the generic parameter T is not of type <xref:System.Data.DataRow>.</span></span>  
  
 [<span data-ttu-id="6fefe-115">Genel Alan ve SetField Yöntemleri</span><span class="sxs-lookup"><span data-stu-id="6fefe-115">Generic Field and SetField Methods</span></span>](generic-field-and-setfield-methods-linq-to-dataset.md)  
 <span data-ttu-id="6fefe-116">Genel <xref:System.Data.DataRowExtensions.Field%2A> ve <xref:System.Data.DataRowExtensions.SetField%2A> yöntemleriyle ilgili bilgiler sağlar.</span><span class="sxs-lookup"><span data-stu-id="6fefe-116">Provides information about the generic <xref:System.Data.DataRowExtensions.Field%2A> and <xref:System.Data.DataRowExtensions.SetField%2A> methods.</span></span>  
  
 [<span data-ttu-id="6fefe-117">Veri Bağlama ve LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="6fefe-117">Data Binding and LINQ to DataSet</span></span>](data-binding-and-linq-to-dataset.md)  
 <span data-ttu-id="6fefe-118"><xref:System.Data.DataView> nesnesi kullanılarak veri bağlamayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="6fefe-118">Describes databinding using the <xref:System.Data.DataView> object.</span></span>  
  
 [<span data-ttu-id="6fefe-119">LINQ to DataSet Sorgularında Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="6fefe-119">Debugging LINQ to DataSet Queries</span></span>](debugging-linq-to-dataset-queries.md)  
 <span data-ttu-id="6fefe-120">Hata ayıklama ve sorgu sorunlarını giderme hakkında bilgi sağlar LINQ to DataSet.</span><span class="sxs-lookup"><span data-stu-id="6fefe-120">Provides information about debugging and troubleshooting LINQ to DataSet queries.</span></span>  
  
 [<span data-ttu-id="6fefe-121">Security</span><span class="sxs-lookup"><span data-stu-id="6fefe-121">Security</span></span>](security-linq-to-dataset.md)  
 <span data-ttu-id="6fefe-122">LINQ to DataSet güvenlik sorunlarını açıklar.</span><span class="sxs-lookup"><span data-stu-id="6fefe-122">Describes security issues in LINQ to DataSet.</span></span>  
  
 [<span data-ttu-id="6fefe-123">LINQ to DataSet Örnekleri</span><span class="sxs-lookup"><span data-stu-id="6fefe-123">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)  
 <span data-ttu-id="6fefe-124">LINQ işleçlerini kullanan sorgu örnekleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="6fefe-124">Provides query examples that use the LINQ operators.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="6fefe-125">Başvuru</span><span class="sxs-lookup"><span data-stu-id="6fefe-125">Reference</span></span>  
 <xref:System.Data.DataRowComparer>  
  
 <xref:System.Data.DataRowExtensions>  
  
 <xref:System.Data.DataTableExtensions>  
  
 <xref:System.Data.DataView>  
  
## <a name="see-also"></a><span data-ttu-id="6fefe-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6fefe-126">See also</span></span>

- [<span data-ttu-id="6fefe-127">LINQ ve ADO.NET</span><span class="sxs-lookup"><span data-stu-id="6fefe-127">LINQ and ADO.NET</span></span>](linq-and-ado-net.md)
- [<span data-ttu-id="6fefe-128">Dil ile Tümleşik Sorgu (LINQ)</span><span class="sxs-lookup"><span data-stu-id="6fefe-128">Language Integrated Query (LINQ)</span></span>](../../../csharp/programming-guide/concepts/linq/index.md)
