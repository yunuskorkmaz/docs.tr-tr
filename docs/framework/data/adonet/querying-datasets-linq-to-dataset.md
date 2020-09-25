---
title: Veri kümelerini sorgulama (LINQ to DataSet)
ms.date: 03/30/2017
ms.assetid: bb68d2e4-623d-4d60-85e3-965254f6fee7
ms.openlocfilehash: f42cd792772a4e2b9f24ea8f76ea588da10d9c51
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91184982"
---
# <a name="querying-datasets-linq-to-dataset"></a><span data-ttu-id="60d7d-102">Veri kümelerini sorgulama (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="60d7d-102">Querying DataSets (LINQ to DataSet)</span></span>

<span data-ttu-id="60d7d-103">Bir <xref:System.Data.DataSet> nesne verilerle doldurulduktan sonra sorgulama işlemine başlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="60d7d-103">After a <xref:System.Data.DataSet> object has been populated with data, you can begin querying it.</span></span> <span data-ttu-id="60d7d-104">Sorguları LINQ to DataSet ile formül, diğer LINQ özellikli veri kaynaklarına karşı dil ile tümleşik sorgu (LINQ) kullanılmasına benzer.</span><span class="sxs-lookup"><span data-stu-id="60d7d-104">Formulating queries with LINQ to DataSet is similar to using Language-Integrated Query (LINQ) against other LINQ-enabled data sources.</span></span> <span data-ttu-id="60d7d-105">Ancak, bir nesne üzerinde LINQ sorguları kullandığınızda <xref:System.Data.DataSet> , bir <xref:System.Data.DataRow> özel türün numaralandırması yerine nesnelerin bir listesini sorgulamakta olduğunuzu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="60d7d-105">Remember, however, that when you use LINQ queries over a <xref:System.Data.DataSet> object, you're querying an enumeration of <xref:System.Data.DataRow> objects instead of an enumeration of a custom type.</span></span> <span data-ttu-id="60d7d-106">Bu, LINQ Sorgularınızdaki sınıfının herhangi bir üyesini kullanabileceğiniz anlamına gelir <xref:System.Data.DataRow> .</span><span class="sxs-lookup"><span data-stu-id="60d7d-106">This means that you can use any of the members of the <xref:System.Data.DataRow> class in your LINQ queries.</span></span> <span data-ttu-id="60d7d-107">Bu, zengin, karmaşık sorgular oluşturmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="60d7d-107">This lets you create rich, complex queries.</span></span>  
  
 <span data-ttu-id="60d7d-108">Diğer LINQ uygulamalarında olduğu gibi, iki farklı biçimde LINQ to DataSet sorguları oluşturabilirsiniz: sorgu ifadesi sözdizimi ve Yöntem tabanlı sorgu söz dizimi.</span><span class="sxs-lookup"><span data-stu-id="60d7d-108">As with other implementations of LINQ, you can create LINQ to DataSet queries in two different forms: query expression syntax and method-based query syntax.</span></span> <span data-ttu-id="60d7d-109">Sorgu ifadesi söz dizimini veya Yöntem tabanlı sorgu söz dizimini kullanarak, bir içindeki <xref:System.Data.DataSet> birden çok tabloya karşı <xref:System.Data.DataSet> veya bir tür içindeki tablolarda tek tek tablolara karşı sorgular gerçekleştirebilirsiniz <xref:System.Data.DataSet> .</span><span class="sxs-lookup"><span data-stu-id="60d7d-109">You can use query expression syntax or method-based query syntax to perform queries against single tables in a <xref:System.Data.DataSet>, against multiple tables in a <xref:System.Data.DataSet>, or against tables in a typed <xref:System.Data.DataSet>.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="60d7d-110">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="60d7d-110">In This Section</span></span>  

 [<span data-ttu-id="60d7d-111">Tek Tablolu Sorgular</span><span class="sxs-lookup"><span data-stu-id="60d7d-111">Single-Table Queries</span></span>](single-table-queries-linq-to-dataset.md)  
 <span data-ttu-id="60d7d-112">Tek tablo sorgularının nasıl gerçekleştirileceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="60d7d-112">Describes how to perform single-table queries.</span></span>  
  
 [<span data-ttu-id="60d7d-113">Tablolar Arası Sorgular</span><span class="sxs-lookup"><span data-stu-id="60d7d-113">Cross-Table Queries</span></span>](cross-table-queries-linq-to-dataset.md)  
 <span data-ttu-id="60d7d-114">Çapraz tablo sorgularının nasıl gerçekleştirileceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="60d7d-114">Describes how to perform cross-table queries.</span></span>  
  
 [<span data-ttu-id="60d7d-115">Türü Belirtilmiş DataSet’leri Sorgulama</span><span class="sxs-lookup"><span data-stu-id="60d7d-115">Querying Typed DataSets</span></span>](querying-typed-datasets.md)  
 <span data-ttu-id="60d7d-116">Yazılan nesnelerin nasıl sorgulanılacağını açıklar <xref:System.Data.DataSet> .</span><span class="sxs-lookup"><span data-stu-id="60d7d-116">Describes how to query typed <xref:System.Data.DataSet> objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60d7d-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="60d7d-117">See also</span></span>

- [<span data-ttu-id="60d7d-118">LINQ to DataSet Örnekleri</span><span class="sxs-lookup"><span data-stu-id="60d7d-118">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
- [<span data-ttu-id="60d7d-119">DataSet’e Veri Yükleme</span><span class="sxs-lookup"><span data-stu-id="60d7d-119">Loading Data Into a DataSet</span></span>](loading-data-into-a-dataset.md)
