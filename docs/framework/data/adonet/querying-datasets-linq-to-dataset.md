---
description: 'Hakkında daha fazla bilgi edinin: veri kümelerini sorgulama (LINQ to DataSet)'
title: Veri kümelerini sorgulama (LINQ to DataSet)
ms.date: 03/30/2017
ms.assetid: bb68d2e4-623d-4d60-85e3-965254f6fee7
ms.openlocfilehash: 609de99069d39317d8d372cb2a7f43ea301ada2d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99663462"
---
# <a name="querying-datasets-linq-to-dataset"></a><span data-ttu-id="14d73-103">Veri kümelerini sorgulama (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="14d73-103">Querying DataSets (LINQ to DataSet)</span></span>

<span data-ttu-id="14d73-104">Bir <xref:System.Data.DataSet> nesne verilerle doldurulduktan sonra sorgulama işlemine başlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="14d73-104">After a <xref:System.Data.DataSet> object has been populated with data, you can begin querying it.</span></span> <span data-ttu-id="14d73-105">Sorguları LINQ to DataSet ile formül, diğer LINQ özellikli veri kaynaklarına karşı Language-Integrated sorgusu (LINQ) kullanılmasına benzerdir.</span><span class="sxs-lookup"><span data-stu-id="14d73-105">Formulating queries with LINQ to DataSet is similar to using Language-Integrated Query (LINQ) against other LINQ-enabled data sources.</span></span> <span data-ttu-id="14d73-106">Ancak, bir nesne üzerinde LINQ sorguları kullandığınızda <xref:System.Data.DataSet> , bir <xref:System.Data.DataRow> özel türün numaralandırması yerine nesnelerin bir listesini sorgulamakta olduğunuzu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="14d73-106">Remember, however, that when you use LINQ queries over a <xref:System.Data.DataSet> object, you're querying an enumeration of <xref:System.Data.DataRow> objects instead of an enumeration of a custom type.</span></span> <span data-ttu-id="14d73-107">Bu, LINQ Sorgularınızdaki sınıfının herhangi bir üyesini kullanabileceğiniz anlamına gelir <xref:System.Data.DataRow> .</span><span class="sxs-lookup"><span data-stu-id="14d73-107">This means that you can use any of the members of the <xref:System.Data.DataRow> class in your LINQ queries.</span></span> <span data-ttu-id="14d73-108">Bu, zengin, karmaşık sorgular oluşturmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="14d73-108">This lets you create rich, complex queries.</span></span>  
  
 <span data-ttu-id="14d73-109">Diğer LINQ uygulamalarında olduğu gibi, iki farklı biçimde LINQ to DataSet sorguları oluşturabilirsiniz: sorgu ifadesi sözdizimi ve Yöntem tabanlı sorgu söz dizimi.</span><span class="sxs-lookup"><span data-stu-id="14d73-109">As with other implementations of LINQ, you can create LINQ to DataSet queries in two different forms: query expression syntax and method-based query syntax.</span></span> <span data-ttu-id="14d73-110">Sorgu ifadesi söz dizimini veya Yöntem tabanlı sorgu söz dizimini kullanarak, bir içindeki <xref:System.Data.DataSet> birden çok tabloya karşı <xref:System.Data.DataSet> veya bir tür içindeki tablolarda tek tek tablolara karşı sorgular gerçekleştirebilirsiniz <xref:System.Data.DataSet> .</span><span class="sxs-lookup"><span data-stu-id="14d73-110">You can use query expression syntax or method-based query syntax to perform queries against single tables in a <xref:System.Data.DataSet>, against multiple tables in a <xref:System.Data.DataSet>, or against tables in a typed <xref:System.Data.DataSet>.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="14d73-111">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="14d73-111">In This Section</span></span>  

 [<span data-ttu-id="14d73-112">Tek Tablolu Sorgular</span><span class="sxs-lookup"><span data-stu-id="14d73-112">Single-Table Queries</span></span>](single-table-queries-linq-to-dataset.md)  
 <span data-ttu-id="14d73-113">Tek tablo sorgularının nasıl gerçekleştirileceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="14d73-113">Describes how to perform single-table queries.</span></span>  
  
 [<span data-ttu-id="14d73-114">Tablolar Arası Sorgular</span><span class="sxs-lookup"><span data-stu-id="14d73-114">Cross-Table Queries</span></span>](cross-table-queries-linq-to-dataset.md)  
 <span data-ttu-id="14d73-115">Çapraz tablo sorgularının nasıl gerçekleştirileceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="14d73-115">Describes how to perform cross-table queries.</span></span>  
  
 [<span data-ttu-id="14d73-116">Türü Belirtilmiş DataSet’leri Sorgulama</span><span class="sxs-lookup"><span data-stu-id="14d73-116">Querying Typed DataSets</span></span>](querying-typed-datasets.md)  
 <span data-ttu-id="14d73-117">Yazılan nesnelerin nasıl sorgulanılacağını açıklar <xref:System.Data.DataSet> .</span><span class="sxs-lookup"><span data-stu-id="14d73-117">Describes how to query typed <xref:System.Data.DataSet> objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14d73-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="14d73-118">See also</span></span>

- [<span data-ttu-id="14d73-119">LINQ to DataSet Örnekleri</span><span class="sxs-lookup"><span data-stu-id="14d73-119">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
- [<span data-ttu-id="14d73-120">DataSet’e Veri Yükleme</span><span class="sxs-lookup"><span data-stu-id="14d73-120">Loading Data Into a DataSet</span></span>](loading-data-into-a-dataset.md)
