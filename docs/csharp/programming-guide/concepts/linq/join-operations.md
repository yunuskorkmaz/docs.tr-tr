---
title: Join Işlemler (C#)
ms.date: 07/20/2015
ms.assetid: 5105e0da-1267-4c00-837a-f0e9602279b8
no-loc:
- Join
- GroupJoin
ms.openlocfilehash: 6e2ec1a0c8120f6869b7c0a196b77d118762a8dd
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868011"
---
# <a name="join-operations-c"></a><span data-ttu-id="013fc-102">JOIN Işlemleri (C#)</span><span class="sxs-lookup"><span data-stu-id="013fc-102">Join Operations (C#)</span></span>

<span data-ttu-id="013fc-103">İki veri kaynağının *birleşimi* , bir veri kaynağındaki nesnelerin, başka bir veri kaynağında ortak bir özniteliği paylaşan nesnelerle ilişkilendirilmesi.</span><span class="sxs-lookup"><span data-stu-id="013fc-103">A *join* of two data sources is the association of objects in one data source with objects that share a common attribute in another data source.</span></span>  
  
 <span data-ttu-id="013fc-104">Birleştirme, birbirleriyle ilişkilerini hedefleyen veri kaynaklarını hedef alan sorgularda önemli bir işlemdir.</span><span class="sxs-lookup"><span data-stu-id="013fc-104">Joining is an important operation in queries that target data sources whose relationships to each other cannot be followed directly.</span></span> <span data-ttu-id="013fc-105">Nesne odaklı programlamada bu, tek yönlü bir ilişkinin geriye doğru yönü gibi Modellenmemiş nesneler arasındaki bir bağıntı anlamına gelebilir.</span><span class="sxs-lookup"><span data-stu-id="013fc-105">In object-oriented programming, this could mean a correlation between objects that is not modeled, such as the backwards direction of a one-way relationship.</span></span> <span data-ttu-id="013fc-106">Tek yönlü ilişki örneği, şehir türünde bir özelliği olan bir müşteri sınıfıdır, ancak City sınıfı, müşteri nesnelerinin bir koleksiyonu olan bir özelliğine sahip değildir.</span><span class="sxs-lookup"><span data-stu-id="013fc-106">An example of a one-way relationship is a Customer class that has a property of type City, but the City class does not have a property that is a collection of Customer objects.</span></span> <span data-ttu-id="013fc-107">Bir şehir nesneleri listeniz varsa ve her bir şehirde tüm müşterileri bulmak istiyorsanız, bunları bulmak için bir JOIN işlemi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="013fc-107">If you have a list of City objects and you want to find all the customers in each city, you could use a join operation to find them.</span></span>  
  
 <span data-ttu-id="013fc-108">LINQ çerçevesinde sunulan JOIN yöntemleri <xref:System.Linq.Enumerable.Join%2A> ve <xref:System.Linq.Enumerable.GroupJoin%2A>.</span><span class="sxs-lookup"><span data-stu-id="013fc-108">The join methods provided in the LINQ framework are <xref:System.Linq.Enumerable.Join%2A> and <xref:System.Linq.Enumerable.GroupJoin%2A>.</span></span> <span data-ttu-id="013fc-109">Bu yöntemler, anahtarlarının eşitliğine göre iki veri kaynağıyla eşleşen eş birleştirmeleri veya birleştirmeleri gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="013fc-109">These methods perform equijoins, or joins that match two data sources based on equality of their keys.</span></span> <span data-ttu-id="013fc-110">(Karşılaştırma için Transact-SQL ' Equals ' dışındaki bir JOIN işleçlerini destekler, örneğin ' küçüktür ' işleci.) İlişkisel veritabanı koşullarında <xref:System.Linq.Enumerable.Join%2A>, yalnızca diğer veri kümesinde eşleşme olan nesnelerin döndürüldüğü bir birleşim türü olan bir iç birleşim uygular.</span><span class="sxs-lookup"><span data-stu-id="013fc-110">(For comparison, Transact-SQL supports join operators other than 'equals', for example the 'less than' operator.) In relational database terms, <xref:System.Linq.Enumerable.Join%2A> implements an inner join, a type of join in which only those objects that have a match in the other data set are returned.</span></span> <span data-ttu-id="013fc-111"><xref:System.Linq.Enumerable.GroupJoin%2A> yönteminin ilişkisel veritabanı terimlerinde doğrudan eşdeğeri yoktur, ancak iç birleştirmeler ve sol dış birleşimlerin bir üst kümesini uygular.</span><span class="sxs-lookup"><span data-stu-id="013fc-111">The <xref:System.Linq.Enumerable.GroupJoin%2A> method has no direct equivalent in relational database terms, but it implements a superset of inner joins and left outer joins.</span></span> <span data-ttu-id="013fc-112">Sol dış birleşim, diğer veri kaynağında bağıntılı bir öğesi olmasa bile, ilk (soldaki) veri kaynağının her bir öğesini döndüren birleşimdir.</span><span class="sxs-lookup"><span data-stu-id="013fc-112">A left outer join is a join that returns each element of the first (left) data source, even if it has no correlated elements in the other data source.</span></span>  
  
 <span data-ttu-id="013fc-113">Aşağıdaki çizimde, iki kümenin kavramsal görünümü ve bu kümeler içindeki öğelerin bir iç birleşime veya bir sol dış birleşime dahil olduğu gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="013fc-113">The following illustration shows a conceptual view of two sets and the elements within those sets that are included in either an inner join or a left outer join.</span></span>  
  
 ![İç&#47;dıştaki gösteren iki çakışan daire.](./media/join-operations/join-method-overlapping-circles.png)  
  
## <a name="methods"></a><span data-ttu-id="013fc-115">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="013fc-115">Methods</span></span>  
  
|<span data-ttu-id="013fc-116">Yöntem adı</span><span class="sxs-lookup"><span data-stu-id="013fc-116">Method Name</span></span>|<span data-ttu-id="013fc-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="013fc-117">Description</span></span>|<span data-ttu-id="013fc-118">C#Sorgu Ifadesi söz dizimi</span><span class="sxs-lookup"><span data-stu-id="013fc-118">C# Query Expression Syntax</span></span>|<span data-ttu-id="013fc-119">Daha fazla bilgi</span><span class="sxs-lookup"><span data-stu-id="013fc-119">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|Join|<span data-ttu-id="013fc-120">Anahtar Seçici işlevlerine göre iki diziyi birleştirir ve değer çiftlerini ayıklar.</span><span class="sxs-lookup"><span data-stu-id="013fc-120">Joins two sequences based on key selector functions and extracts pairs of values.</span></span>|`join … in … on … equals …`|<xref:System.Linq.Enumerable.Join%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Join%2A?displayProperty=nameWithType>|  
|GroupJoin|<span data-ttu-id="013fc-121">Anahtar Seçici işlevlerine göre iki diziyi birleştirir ve her öğe için elde edilen eşleşmeleri gruplandırır.</span><span class="sxs-lookup"><span data-stu-id="013fc-121">Joins two sequences based on key selector functions and groups the resulting matches for each element.</span></span>|`join … in … on … equals … into …`|<xref:System.Linq.Enumerable.GroupJoin%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.GroupJoin%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="013fc-122">Sorgu ifadesi söz dizimi örnekleri</span><span class="sxs-lookup"><span data-stu-id="013fc-122">Query expression syntax examples</span></span>
  
### Join  
  
<span data-ttu-id="013fc-123">Aşağıdaki örnek, belirli bir değere göre iki diziyi birleştirmek için `join … in … on … equals …` yan tümcesini kullanır:</span><span class="sxs-lookup"><span data-stu-id="013fc-123">The following example uses the `join … in … on … equals …` clause to join two sequences based on specific value:</span></span>
  
[!code-csharp[Join](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csLINQJoinOperation/CS/JoinOperation.cs#Join)]  

### GroupJoin  

<span data-ttu-id="013fc-124">Aşağıdaki örnek, belirli bir değere göre iki diziyi birleştirmek için `join … in … on … equals … into …` yan tümcesini kullanır ve her öğe için elde edilen eşleşmeleri gruplandırır:</span><span class="sxs-lookup"><span data-stu-id="013fc-124">The following example uses the `join … in … on … equals … into …` clause to join two sequences based on specific value and groups the resulting matches for each element:</span></span>
  
[!code-csharp[GroupJoin](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csLINQJoinOperation/CS/JoinOperation.cs#GroupJoin)]  
  
## <a name="see-also"></a><span data-ttu-id="013fc-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="013fc-125">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="013fc-126">Standart sorgu Işleçlerine genelC#bakış ()</span><span class="sxs-lookup"><span data-stu-id="013fc-126">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="013fc-127">Anonim Tipler</span><span class="sxs-lookup"><span data-stu-id="013fc-127">Anonymous Types</span></span>](../../classes-and-structs/anonymous-types.md)
- [<span data-ttu-id="013fc-128">Birleşimler ve Çapraz Ürün Sorguları Düzenleme</span><span class="sxs-lookup"><span data-stu-id="013fc-128">Formulate Joins and Cross-Product Queries</span></span>](../../../../framework/data/adonet/sql/linq/formulate-joins-and-cross-product-queries.md)
- [<span data-ttu-id="013fc-129">join yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="013fc-129">join clause</span></span>](../../../language-reference/keywords/join-clause.md)
- <span data-ttu-id="013fc-130">[bileşik anahtarlar kullanarak Join](../../../linq/join-by-using-composite-keys.md)</span><span class="sxs-lookup"><span data-stu-id="013fc-130">[Join by using composite keys](../../../linq/join-by-using-composite-keys.md)</span></span>
- [<span data-ttu-id="013fc-131">Benzer olmayan dosyalardaki (LINQ) (C#) içerik ekleme</span><span class="sxs-lookup"><span data-stu-id="013fc-131">How to join content from dissimilar files (LINQ) (C#)</span></span>](./how-to-join-content-from-dissimilar-files-linq.md)
- [<span data-ttu-id="013fc-132">Join yan tümcesinin sonuçlarını sıralama</span><span class="sxs-lookup"><span data-stu-id="013fc-132">Order the results of a join clause</span></span>](../../../linq/order-the-results-of-a-join-clause.md)
- [<span data-ttu-id="013fc-133">Özel birleştirme işlemleri gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="013fc-133">Perform custom join operations</span></span>](../../../linq/perform-custom-join-operations.md)
- [<span data-ttu-id="013fc-134">Gruplanmış birleşimler gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="013fc-134">Perform grouped joins</span></span>](../../../linq/perform-grouped-joins.md)
- [<span data-ttu-id="013fc-135">İç birleşimler gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="013fc-135">Perform inner joins</span></span>](../../../linq/perform-inner-joins.md)
- [<span data-ttu-id="013fc-136">Sol dış birleştirmeler gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="013fc-136">Perform left outer joins</span></span>](../../../linq/perform-left-outer-joins.md)
- [<span data-ttu-id="013fc-137">Birden çok kaynaktan nesne koleksiyonları doldurma (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="013fc-137">How to populate object collections from multiple sources (LINQ) (C#)</span></span>](./how-to-populate-object-collections-from-multiple-sources-linq.md)
