---
title: Veri kümelerini sorgulama (LINQ to DataSet)
ms.date: 03/30/2017
ms.assetid: bb68d2e4-623d-4d60-85e3-965254f6fee7
ms.openlocfilehash: 79a9b320fbdbfecc3f7d531d992b1529873871a5
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70783043"
---
# <a name="querying-datasets-linq-to-dataset"></a><span data-ttu-id="68365-102">Veri kümelerini sorgulama (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="68365-102">Querying DataSets (LINQ to DataSet)</span></span>
<span data-ttu-id="68365-103">Bir <xref:System.Data.DataSet> nesne verilerle doldurulduktan sonra sorgulama işlemine başlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="68365-103">After a <xref:System.Data.DataSet> object has been populated with data, you can begin querying it.</span></span> <span data-ttu-id="68365-104">Sorguları LINQ to DataSet ile formül, diğer [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]etkin veri kaynaklarında kullanılmasına benzer.</span><span class="sxs-lookup"><span data-stu-id="68365-104">Formulating queries with LINQ to DataSet is similar to using [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] against other [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]-enabled data sources.</span></span> <span data-ttu-id="68365-105">Ancak, bir [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] <xref:System.Data.DataSet> nesne üzerinde sorgu kullandığınızda, bir özel türün numaralandırması yerine, <xref:System.Data.DataRow> nesneleri bir numaralandırma sorgulamakta olduğunuz durumlarda unutmayın.</span><span class="sxs-lookup"><span data-stu-id="68365-105">Remember, however, that when you use [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] queries over a <xref:System.Data.DataSet> object you are querying an enumeration of <xref:System.Data.DataRow> objects, instead of an enumeration of a custom type.</span></span> <span data-ttu-id="68365-106">Bu, Sorgularınızdaki <xref:System.Data.DataRow> [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] sınıfının herhangi bir üyesini kullanabileceğiniz anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="68365-106">This means that you can use any of the members of the <xref:System.Data.DataRow> class in your [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] queries.</span></span> <span data-ttu-id="68365-107">Bu, zengin, karmaşık sorgular oluşturmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="68365-107">This lets you to create rich, complex queries.</span></span>  
  
 <span data-ttu-id="68365-108">Diğer uygulamalarında [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]olduğu gibi, iki farklı biçimde LINQ to DataSet sorguları oluşturabilirsiniz: sorgu ifadesi sözdizimi ve Yöntem tabanlı sorgu söz dizimi.</span><span class="sxs-lookup"><span data-stu-id="68365-108">As with other implementations of [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)], you can create LINQ to DataSet queries in two different forms: query expression syntax and method-based query syntax.</span></span> <span data-ttu-id="68365-109">Sorgu ifadesi söz dizimini veya Yöntem tabanlı sorgu söz dizimini kullanarak <xref:System.Data.DataSet>, bir içindeki birden çok tabloya <xref:System.Data.DataSet>karşı veya bir tür <xref:System.Data.DataSet>içindeki tablolarda tek tek tablolara karşı sorgular gerçekleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="68365-109">You can use query expression syntax or method-based query syntax to perform queries against single tables in a <xref:System.Data.DataSet>, against multiple tables in a <xref:System.Data.DataSet>, or against tables in a typed <xref:System.Data.DataSet>.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="68365-110">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="68365-110">In This Section</span></span>  
 [<span data-ttu-id="68365-111">Tek Tablolu Sorgular</span><span class="sxs-lookup"><span data-stu-id="68365-111">Single-Table Queries</span></span>](single-table-queries-linq-to-dataset.md)  
 <span data-ttu-id="68365-112">Tek tablo sorgularının nasıl gerçekleştirileceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="68365-112">Describes how to perform single-table queries.</span></span>  
  
 [<span data-ttu-id="68365-113">Tablolar Arası Sorgular</span><span class="sxs-lookup"><span data-stu-id="68365-113">Cross-Table Queries</span></span>](cross-table-queries-linq-to-dataset.md)  
 <span data-ttu-id="68365-114">Çapraz tablo sorgularının nasıl gerçekleştirileceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="68365-114">Describes how to perform cross-table queries.</span></span>  
  
 [<span data-ttu-id="68365-115">Türü Belirtilmiş DataSet’leri Sorgulama</span><span class="sxs-lookup"><span data-stu-id="68365-115">Querying Typed DataSets</span></span>](querying-typed-datasets.md)  
 <span data-ttu-id="68365-116">Yazılan <xref:System.Data.DataSet> nesnelerin nasıl sorgulanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="68365-116">Describes how to query typed <xref:System.Data.DataSet> objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68365-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="68365-117">See also</span></span>

- [<span data-ttu-id="68365-118">LINQ to DataSet Örnekleri</span><span class="sxs-lookup"><span data-stu-id="68365-118">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
- [<span data-ttu-id="68365-119">DataSet’e Veri Yükleme</span><span class="sxs-lookup"><span data-stu-id="68365-119">Loading Data Into a DataSet</span></span>](loading-data-into-a-dataset.md)
