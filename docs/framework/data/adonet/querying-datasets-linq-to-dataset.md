---
title: Veri kümelerini sorgulama (LINQ to DataSet)
ms.date: 03/30/2017
ms.assetid: bb68d2e4-623d-4d60-85e3-965254f6fee7
ms.openlocfilehash: bb64abcffdbbcd46dfb11b2564619c565e461436
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/03/2020
ms.locfileid: "75634787"
---
# <a name="querying-datasets-linq-to-dataset"></a><span data-ttu-id="6c5ce-102">Veri kümelerini sorgulama (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="6c5ce-102">Querying DataSets (LINQ to DataSet)</span></span>
<span data-ttu-id="6c5ce-103"><xref:System.Data.DataSet> nesne verilerle doldurulduktan sonra, sorgulama işlemine başlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6c5ce-103">After a <xref:System.Data.DataSet> object has been populated with data, you can begin querying it.</span></span> <span data-ttu-id="6c5ce-104">Sorguları LINQ to DataSet ile formül, diğer LINQ özellikli veri kaynaklarına karşı dil ile tümleşik sorgu (LINQ) kullanılmasına benzer.</span><span class="sxs-lookup"><span data-stu-id="6c5ce-104">Formulating queries with LINQ to DataSet is similar to using Language-Integrated Query (LINQ) against other LINQ-enabled data sources.</span></span> <span data-ttu-id="6c5ce-105">Ancak, <xref:System.Data.DataSet> nesnesi üzerinde LINQ sorguları kullandığınızda, özel bir türün numaralandırılması yerine <xref:System.Data.DataRow> nesnelerinin bir listesini sorgulamakta olduğunuzu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="6c5ce-105">Remember, however, that when you use LINQ queries over a <xref:System.Data.DataSet> object, you're querying an enumeration of <xref:System.Data.DataRow> objects instead of an enumeration of a custom type.</span></span> <span data-ttu-id="6c5ce-106">Bu, LINQ sorgularınızda <xref:System.Data.DataRow> sınıfının herhangi bir üyesini kullanabileceğiniz anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="6c5ce-106">This means that you can use any of the members of the <xref:System.Data.DataRow> class in your LINQ queries.</span></span> <span data-ttu-id="6c5ce-107">Bu, zengin, karmaşık sorgular oluşturmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="6c5ce-107">This lets you create rich, complex queries.</span></span>  
  
 <span data-ttu-id="6c5ce-108">Diğer LINQ uygulamalarında olduğu gibi, iki farklı biçimde LINQ to DataSet sorguları oluşturabilirsiniz: sorgu ifadesi sözdizimi ve Yöntem tabanlı sorgu söz dizimi.</span><span class="sxs-lookup"><span data-stu-id="6c5ce-108">As with other implementations of LINQ, you can create LINQ to DataSet queries in two different forms: query expression syntax and method-based query syntax.</span></span> <span data-ttu-id="6c5ce-109">Sorgu ifadesi söz dizimini veya Yöntem tabanlı sorgu söz dizimini kullanarak bir <xref:System.Data.DataSet>tek tablolara karşı sorgular gerçekleştirebilir, bir <xref:System.Data.DataSet>birden çok tabloya karşı veya yazılan <xref:System.Data.DataSet>tablolardaki tablolara karşı sorgu sözdizimini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6c5ce-109">You can use query expression syntax or method-based query syntax to perform queries against single tables in a <xref:System.Data.DataSet>, against multiple tables in a <xref:System.Data.DataSet>, or against tables in a typed <xref:System.Data.DataSet>.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6c5ce-110">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="6c5ce-110">In This Section</span></span>  
 [<span data-ttu-id="6c5ce-111">Tek Tablolu Sorgular</span><span class="sxs-lookup"><span data-stu-id="6c5ce-111">Single-Table Queries</span></span>](single-table-queries-linq-to-dataset.md)  
 <span data-ttu-id="6c5ce-112">Tek tablo sorgularının nasıl gerçekleştirileceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="6c5ce-112">Describes how to perform single-table queries.</span></span>  
  
 [<span data-ttu-id="6c5ce-113">Tablolar Arası Sorgular</span><span class="sxs-lookup"><span data-stu-id="6c5ce-113">Cross-Table Queries</span></span>](cross-table-queries-linq-to-dataset.md)  
 <span data-ttu-id="6c5ce-114">Çapraz tablo sorgularının nasıl gerçekleştirileceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="6c5ce-114">Describes how to perform cross-table queries.</span></span>  
  
 [<span data-ttu-id="6c5ce-115">Türü Belirtilmiş DataSet’leri Sorgulama</span><span class="sxs-lookup"><span data-stu-id="6c5ce-115">Querying Typed DataSets</span></span>](querying-typed-datasets.md)  
 <span data-ttu-id="6c5ce-116">Yazılan <xref:System.Data.DataSet> nesnelerinin nasıl sorgulanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="6c5ce-116">Describes how to query typed <xref:System.Data.DataSet> objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c5ce-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6c5ce-117">See also</span></span>

- [<span data-ttu-id="6c5ce-118">LINQ to DataSet Örnekleri</span><span class="sxs-lookup"><span data-stu-id="6c5ce-118">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
- [<span data-ttu-id="6c5ce-119">DataSet’e Veri Yükleme</span><span class="sxs-lookup"><span data-stu-id="6c5ce-119">Loading Data Into a DataSet</span></span>](loading-data-into-a-dataset.md)
