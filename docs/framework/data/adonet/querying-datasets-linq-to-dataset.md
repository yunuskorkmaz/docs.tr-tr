---
title: "Veri kümeleri (LINQ-DataSet) sorgulama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bb68d2e4-623d-4d60-85e3-965254f6fee7
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: c9830587e70d7671200fac20c8384f1a470a751e
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="querying-datasets-linq-to-dataset"></a><span data-ttu-id="ffecb-102">Veri kümeleri (LINQ-DataSet) sorgulama</span><span class="sxs-lookup"><span data-stu-id="ffecb-102">Querying DataSets (LINQ to DataSet)</span></span>
<span data-ttu-id="ffecb-103">Sonra bir <xref:System.Data.DataSet> nesnesi, verilerle doldurulur, bu sorgulama başlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ffecb-103">After a <xref:System.Data.DataSet> object has been populated with data, you can begin querying it.</span></span> <span data-ttu-id="ffecb-104">Sorgularıyla formulating [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] kullanmaya benzer [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] diğer karşı [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]-veri kaynaklarının etkin.</span><span class="sxs-lookup"><span data-stu-id="ffecb-104">Formulating queries with [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] is similar to using [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] against other [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]-enabled data sources.</span></span> <span data-ttu-id="ffecb-105">Kullandığınızda, ancak unutmayın [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] üzerinden sorgular bir <xref:System.Data.DataSet> numaralandırması sorgulama nesne <xref:System.Data.DataRow> nesneleri yerine bir özel tür numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="ffecb-105">Remember, however, that when you use [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] queries over a <xref:System.Data.DataSet> object you are querying an enumeration of <xref:System.Data.DataRow> objects, instead of an enumeration of a custom type.</span></span> <span data-ttu-id="ffecb-106">Bu tüm üyeleri kullanabileceğiniz anlamına gelir <xref:System.Data.DataRow> sınıfını, [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] sorgular.</span><span class="sxs-lookup"><span data-stu-id="ffecb-106">This means that you can use any of the members of the <xref:System.Data.DataRow> class in your [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] queries.</span></span> <span data-ttu-id="ffecb-107">Bu, zengin, karmaşık sorgular oluşturmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="ffecb-107">This lets you to create rich, complex queries.</span></span>  
  
 <span data-ttu-id="ffecb-108">Diğer uygulamaları ile [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)], oluşturabileceğiniz [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] iki farklı form sorgularda: Sorgu ifade sözdizimi ve yöntem temelli sorgu sözdizimi.</span><span class="sxs-lookup"><span data-stu-id="ffecb-108">As with other implementations of [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)], you can create [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] queries in two different forms: query expression syntax and method-based query syntax.</span></span> <span data-ttu-id="ffecb-109">İki yöntemden birini hakkında daha fazla bilgi için bkz: [LINQ ile çalışmaya başlama](http://msdn.microsoft.com/en-us/6cc9af04-950a-4cc3-83d4-2aeb4abe4de9).</span><span class="sxs-lookup"><span data-stu-id="ffecb-109">For more information about these two forms, see [Getting Started with LINQ](http://msdn.microsoft.com/en-us/6cc9af04-950a-4cc3-83d4-2aeb4abe4de9).</span></span> <span data-ttu-id="ffecb-110">Sorgu ifade sözdizimi kullanabilir veya gerçekleştirmek için yöntem temelli sorgu söz dizimi sorgular tek tablolarda karşı bir <xref:System.Data.DataSet>, birden fazla tabloya karşı bir <xref:System.Data.DataSet>, veya bir yazılı tablolarda karşı <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="ffecb-110">You can use query expression syntax or method-based query syntax to perform queries against single tables in a <xref:System.Data.DataSet>, against multiple tables in a <xref:System.Data.DataSet>, or against tables in a typed <xref:System.Data.DataSet>.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ffecb-111">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="ffecb-111">In This Section</span></span>  
 [<span data-ttu-id="ffecb-112">Tek Tablolu Sorgular</span><span class="sxs-lookup"><span data-stu-id="ffecb-112">Single-Table Queries</span></span>](../../../../docs/framework/data/adonet/single-table-queries-linq-to-dataset.md)  
 <span data-ttu-id="ffecb-113">Tek tablo sorguları gerçekleştirmeyi açıklar.</span><span class="sxs-lookup"><span data-stu-id="ffecb-113">Describes how to perform single-table queries.</span></span>  
  
 [<span data-ttu-id="ffecb-114">Tablolar Arası Sorgular</span><span class="sxs-lookup"><span data-stu-id="ffecb-114">Cross-Table Queries</span></span>](../../../../docs/framework/data/adonet/cross-table-queries-linq-to-dataset.md)  
 <span data-ttu-id="ffecb-115">Geçici tablo sorguları gerçekleştirmeyi açıklar.</span><span class="sxs-lookup"><span data-stu-id="ffecb-115">Describes how to perform cross-table queries.</span></span>  
  
 [<span data-ttu-id="ffecb-116">Türü Belirtilmiş DataSet’leri Sorgulama</span><span class="sxs-lookup"><span data-stu-id="ffecb-116">Querying Typed DataSets</span></span>](../../../../docs/framework/data/adonet/querying-typed-datasets.md)  
 <span data-ttu-id="ffecb-117">Sorgu açıklar yazılan <xref:System.Data.DataSet> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="ffecb-117">Describes how to query typed <xref:System.Data.DataSet> objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ffecb-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ffecb-118">See Also</span></span>  
 [<span data-ttu-id="ffecb-119">LINQ to DataSet Örnekleri</span><span class="sxs-lookup"><span data-stu-id="ffecb-119">LINQ to DataSet Examples</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)  
 [<span data-ttu-id="ffecb-120">DataSet’e Veri Yükleme</span><span class="sxs-lookup"><span data-stu-id="ffecb-120">Loading Data Into a DataSet</span></span>](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)
