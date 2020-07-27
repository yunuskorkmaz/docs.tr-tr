---
title: :::no-loc(Join):::İşlemler (C#)
description: İki veri kaynağı birleşimi, nesneleri veri kaynakları genelinde bir özniteliği paylaşan nesnelerle ilişkilendirir. C# ' de LINQ çerçevesindeki JOIN yöntemleri hakkında bilgi edinin.
ms.date: 07/20/2015
ms.assetid: 5105e0da-1267-4c00-837a-f0e9602279b8
no-loc:
- ':::no-loc(Join):::'
- ':::no-loc(GroupJoin):::'
ms.openlocfilehash: 1b453f1752edf0cc126f8e27dbdd9e91ad9143f3
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165695"
---
# <a name="no-locjoin-operations-c"></a><span data-ttu-id="77bb6-104">:::no-loc(Join):::İşlemler (C#)</span><span class="sxs-lookup"><span data-stu-id="77bb6-104">:::no-loc(Join)::: Operations (C#)</span></span>

<span data-ttu-id="77bb6-105">İki veri kaynağının *birleşimi* , bir veri kaynağındaki nesnelerin, başka bir veri kaynağında ortak bir özniteliği paylaşan nesnelerle ilişkilendirilmesi.</span><span class="sxs-lookup"><span data-stu-id="77bb6-105">A *join* of two data sources is the association of objects in one data source with objects that share a common attribute in another data source.</span></span>  
  
 <span data-ttu-id="77bb6-106">:::no-loc(Join):::oluşturma, birbirleriyle ilişkilerini hedefleyen veri kaynaklarını hedef alan sorgularda önemli bir işlemdir.</span><span class="sxs-lookup"><span data-stu-id="77bb6-106">:::no-loc(Join):::ing is an important operation in queries that target data sources whose relationships to each other cannot be followed directly.</span></span> <span data-ttu-id="77bb6-107">Nesne odaklı programlamada bu, tek yönlü bir ilişkinin geriye doğru yönü gibi Modellenmemiş nesneler arasındaki bir bağıntı anlamına gelebilir.</span><span class="sxs-lookup"><span data-stu-id="77bb6-107">In object-oriented programming, this could mean a correlation between objects that is not modeled, such as the backwards direction of a one-way relationship.</span></span> <span data-ttu-id="77bb6-108">Tek yönlü ilişki örneği, şehir türünde bir özelliği olan bir müşteri sınıfıdır, ancak City sınıfı, müşteri nesnelerinin bir koleksiyonu olan bir özelliğine sahip değildir.</span><span class="sxs-lookup"><span data-stu-id="77bb6-108">An example of a one-way relationship is a Customer class that has a property of type City, but the City class does not have a property that is a collection of Customer objects.</span></span> <span data-ttu-id="77bb6-109">Bir şehir nesneleri listeniz varsa ve her bir şehirde tüm müşterileri bulmak istiyorsanız, bunları bulmak için bir JOIN işlemi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="77bb6-109">If you have a list of City objects and you want to find all the customers in each city, you could use a join operation to find them.</span></span>  
  
 <span data-ttu-id="77bb6-110">LINQ çerçevesinde sunulan JOIN yöntemleri <xref:System.Linq.Enumerable.:::no-loc(Join):::%2A> ve ' dir <xref:System.Linq.Enumerable.:::no-loc(GroupJoin):::%2A> .</span><span class="sxs-lookup"><span data-stu-id="77bb6-110">The join methods provided in the LINQ framework are <xref:System.Linq.Enumerable.:::no-loc(Join):::%2A> and <xref:System.Linq.Enumerable.:::no-loc(GroupJoin):::%2A>.</span></span> <span data-ttu-id="77bb6-111">Bu yöntemler, anahtarlarının eşitliğine göre iki veri kaynağıyla eşleşen eş birleştirmeleri veya birleştirmeleri gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="77bb6-111">These methods perform equijoins, or joins that match two data sources based on equality of their keys.</span></span> <span data-ttu-id="77bb6-112">(Karşılaştırma için Transact-SQL ' Equals ' dışındaki bir JOIN işleçlerini destekler, örneğin ' küçüktür ' işleci.) İlişkisel veritabanı koşullarında, bir <xref:System.Linq.Enumerable.:::no-loc(Join):::%2A> iç birleşim ve yalnızca diğer veri kümesinde eşleşme olan nesnelerin döndürüldüğü bir birleşim türü uygular.</span><span class="sxs-lookup"><span data-stu-id="77bb6-112">(For comparison, Transact-SQL supports join operators other than 'equals', for example the 'less than' operator.) In relational database terms, <xref:System.Linq.Enumerable.:::no-loc(Join):::%2A> implements an inner join, a type of join in which only those objects that have a match in the other data set are returned.</span></span> <span data-ttu-id="77bb6-113"><xref:System.Linq.Enumerable.:::no-loc(GroupJoin):::%2A>Metodun ilişkisel veritabanı terimlerinde doğrudan eşdeğeri yoktur, ancak iç birleştirmeler ve sol dış birleştirmeler üst kümesini uygular.</span><span class="sxs-lookup"><span data-stu-id="77bb6-113">The <xref:System.Linq.Enumerable.:::no-loc(GroupJoin):::%2A> method has no direct equivalent in relational database terms, but it implements a superset of inner joins and left outer joins.</span></span> <span data-ttu-id="77bb6-114">Sol dış birleşim, diğer veri kaynağında bağıntılı bir öğesi olmasa bile, ilk (soldaki) veri kaynağının her bir öğesini döndüren birleşimdir.</span><span class="sxs-lookup"><span data-stu-id="77bb6-114">A left outer join is a join that returns each element of the first (left) data source, even if it has no correlated elements in the other data source.</span></span>  
  
 <span data-ttu-id="77bb6-115">Aşağıdaki çizimde, iki kümenin kavramsal görünümü ve bu kümeler içindeki öğelerin bir iç birleşime veya bir sol dış birleşime dahil olduğu gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="77bb6-115">The following illustration shows a conceptual view of two sets and the elements within those sets that are included in either an inner join or a left outer join.</span></span>  
  
 ![İç&#47;dıştaki gösteren iki çakışan daire.](./media/join-operations/join-method-overlapping-circles.png)  
  
## <a name="methods"></a><span data-ttu-id="77bb6-117">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="77bb6-117">Methods</span></span>  
  
|<span data-ttu-id="77bb6-118">Yöntem adı</span><span class="sxs-lookup"><span data-stu-id="77bb6-118">Method Name</span></span>|<span data-ttu-id="77bb6-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="77bb6-119">Description</span></span>|<span data-ttu-id="77bb6-120">C# sorgu Ifadesi sözdizimi</span><span class="sxs-lookup"><span data-stu-id="77bb6-120">C# Query Expression Syntax</span></span>|<span data-ttu-id="77bb6-121">Daha Fazla Bilgi</span><span class="sxs-lookup"><span data-stu-id="77bb6-121">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|:::no-loc(Join):::|<span data-ttu-id="77bb6-122">:::no-loc(Join):::anahtar Seçici işlevlerine dayanan ve değer çiftlerini çıkaran iki sıra.</span><span class="sxs-lookup"><span data-stu-id="77bb6-122">:::no-loc(Join):::s two sequences based on key selector functions and extracts pairs of values.</span></span>|`join … in … on … equals …`|<xref:System.Linq.Enumerable.:::no-loc(Join):::%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.:::no-loc(Join):::%2A?displayProperty=nameWithType>|  
|:::no-loc(GroupJoin):::|<span data-ttu-id="77bb6-123">:::no-loc(Join):::iki sıra, anahtar Seçici işlevlerine dayalıdır ve her öğe için elde edilen eşleşmeleri gruplandırır.</span><span class="sxs-lookup"><span data-stu-id="77bb6-123">:::no-loc(Join):::s two sequences based on key selector functions and groups the resulting matches for each element.</span></span>|`join … in … on … equals … into …`|<xref:System.Linq.Enumerable.:::no-loc(GroupJoin):::%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.:::no-loc(GroupJoin):::%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="77bb6-124">Sorgu ifadesi söz dizimi örnekleri</span><span class="sxs-lookup"><span data-stu-id="77bb6-124">Query expression syntax examples</span></span>
  
### :::no-loc(Join):::  
  
<span data-ttu-id="77bb6-125">Aşağıdaki örnek, belirli bir `join … in … on … equals …` değere göre iki diziyi birleştirmek için yan tümcesini kullanır:</span><span class="sxs-lookup"><span data-stu-id="77bb6-125">The following example uses the `join … in … on … equals …` clause to join two sequences based on specific value:</span></span>
  
[!code-csharp[:::no-loc(Join):::](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csLINQ:::no-loc(Join):::Operation/CS/:::no-loc(Join):::Operation.cs#:::no-loc(Join):::)]  

### :::no-loc(GroupJoin):::  

<span data-ttu-id="77bb6-126">Aşağıdaki örnek, belirli bir `join … in … on … equals … into …` değere göre iki diziyi birleştirmek için yan tümcesini kullanır ve her öğe için elde edilen eşleşmeleri gruplandırır:</span><span class="sxs-lookup"><span data-stu-id="77bb6-126">The following example uses the `join … in … on … equals … into …` clause to join two sequences based on specific value and groups the resulting matches for each element:</span></span>
  
[!code-csharp[:::no-loc(GroupJoin):::](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csLINQ:::no-loc(Join):::Operation/CS/:::no-loc(Join):::Operation.cs#:::no-loc(GroupJoin):::)]  
  
## <a name="see-also"></a><span data-ttu-id="77bb6-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="77bb6-127">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="77bb6-128">Standart sorgu Işleçlerine genel bakış (C#)</span><span class="sxs-lookup"><span data-stu-id="77bb6-128">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="77bb6-129">Anonim Türler</span><span class="sxs-lookup"><span data-stu-id="77bb6-129">Anonymous Types</span></span>](../../classes-and-structs/anonymous-types.md)
- [<span data-ttu-id="77bb6-130">:::no-loc(Join):::Ve çoklu ürün sorgularını formüller</span><span class="sxs-lookup"><span data-stu-id="77bb6-130">Formulate :::no-loc(Join):::s and Cross-Product Queries</span></span>](../../../../framework/data/adonet/sql/linq/formulate-joins-and-cross-product-queries.md)
- [<span data-ttu-id="77bb6-131">join tümcesi</span><span class="sxs-lookup"><span data-stu-id="77bb6-131">join clause</span></span>](../../../language-reference/keywords/join-clause.md)
- [<span data-ttu-id="77bb6-132">:::no-loc(Join):::bileşik anahtarlar kullanarak</span><span class="sxs-lookup"><span data-stu-id="77bb6-132">:::no-loc(Join)::: by using composite keys</span></span>](../../../linq/join-by-using-composite-keys.md)
- [<span data-ttu-id="77bb6-133">Benzer olmayan dosyalardaki (LINQ) içerik ekleme (C#)</span><span class="sxs-lookup"><span data-stu-id="77bb6-133">How to join content from dissimilar files (LINQ) (C#)</span></span>](./how-to-join-content-from-dissimilar-files-linq.md)
- [<span data-ttu-id="77bb6-134">Join yan tümcesinin sonuçlarını sıralama</span><span class="sxs-lookup"><span data-stu-id="77bb6-134">Order the results of a join clause</span></span>](../../../linq/order-the-results-of-a-join-clause.md)
- [<span data-ttu-id="77bb6-135">Özel birleştirme işlemleri gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="77bb6-135">Perform custom join operations</span></span>](../../../linq/perform-custom-join-operations.md)
- [<span data-ttu-id="77bb6-136">Gruplanmış birleşimler gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="77bb6-136">Perform grouped joins</span></span>](../../../linq/perform-grouped-joins.md)
- [<span data-ttu-id="77bb6-137">İç birleşimler gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="77bb6-137">Perform inner joins</span></span>](../../../linq/perform-inner-joins.md)
- [<span data-ttu-id="77bb6-138">Sol dış birleşimler gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="77bb6-138">Perform left outer joins</span></span>](../../../linq/perform-left-outer-joins.md)
- [<span data-ttu-id="77bb6-139">Birden çok kaynaktan nesne koleksiyonlarını doldurma (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="77bb6-139">How to populate object collections from multiple sources (LINQ) (C#)</span></span>](./how-to-populate-object-collections-from-multiple-sources-linq.md)
