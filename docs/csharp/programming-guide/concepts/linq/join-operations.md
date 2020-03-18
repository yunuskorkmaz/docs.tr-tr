---
title: Joinİşlemler (C#)
ms.date: 07/20/2015
ms.assetid: 5105e0da-1267-4c00-837a-f0e9602279b8
no-loc:
- Join
- GroupJoin
ms.openlocfilehash: 6e2ec1a0c8120f6869b7c0a196b77d118762a8dd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76868011"
---
# <a name="join-operations-c"></a><span data-ttu-id="5e715-102">İşleme Katılma (C#)</span><span class="sxs-lookup"><span data-stu-id="5e715-102">Join Operations (C#)</span></span>

<span data-ttu-id="5e715-103">İki veri kaynağının *birleştirilmesi,* bir veri kaynağındaki nesnelerin başka bir veri kaynağında ortak bir özniteliği paylaşan nesnelerle ilişkilendirilmesidir.</span><span class="sxs-lookup"><span data-stu-id="5e715-103">A *join* of two data sources is the association of objects in one data source with objects that share a common attribute in another data source.</span></span>  
  
 <span data-ttu-id="5e715-104">Birleştirme, birbirleriyle ilişkileri doğrudan izlenemeyen veri kaynaklarını hedefleyen sorgularda önemli bir işlemdir.</span><span class="sxs-lookup"><span data-stu-id="5e715-104">Joining is an important operation in queries that target data sources whose relationships to each other cannot be followed directly.</span></span> <span data-ttu-id="5e715-105">Nesne yönelimli programlamada, bu, tek yönlü bir ilişkinin geriye doğru yönü gibi modellenmemiş nesneler arasında bir ilişki anlamına gelebilir.</span><span class="sxs-lookup"><span data-stu-id="5e715-105">In object-oriented programming, this could mean a correlation between objects that is not modeled, such as the backwards direction of a one-way relationship.</span></span> <span data-ttu-id="5e715-106">Tek yönlü bir ilişkinin bir örneği, Şehir türü özelliğine sahip bir Müşteri sınıfıdır, ancak Şehir sınıfının Müşteri nesneleri koleksiyonu olan bir özelliği yoktur.</span><span class="sxs-lookup"><span data-stu-id="5e715-106">An example of a one-way relationship is a Customer class that has a property of type City, but the City class does not have a property that is a collection of Customer objects.</span></span> <span data-ttu-id="5e715-107">Şehir nesnelerinin bir listesi varsa ve her şehirdeki tüm müşterileri bulmak istiyorsanız, bunları bulmak için bir birleştirme işlemi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5e715-107">If you have a list of City objects and you want to find all the customers in each city, you could use a join operation to find them.</span></span>  
  
 <span data-ttu-id="5e715-108">LINQ çerçevesinde sağlanan birleştirme yöntemleri <xref:System.Linq.Enumerable.Join%2A> <xref:System.Linq.Enumerable.GroupJoin%2A>ve .</span><span class="sxs-lookup"><span data-stu-id="5e715-108">The join methods provided in the LINQ framework are <xref:System.Linq.Enumerable.Join%2A> and <xref:System.Linq.Enumerable.GroupJoin%2A>.</span></span> <span data-ttu-id="5e715-109">Bu yöntemler, anahtarlarının eşitliğini temel alan iki veri kaynağıyla eşleşen equijoins gerçekleştirir veya birleştirir.</span><span class="sxs-lookup"><span data-stu-id="5e715-109">These methods perform equijoins, or joins that match two data sources based on equality of their keys.</span></span> <span data-ttu-id="5e715-110">(Karşılaştırma için, Transact-SQL 'eşittir' dışında birleştirme işleçleri destekler, örneğin 'daha az' işleci.) İlişkisel veritabanı terimlerinde, <xref:System.Linq.Enumerable.Join%2A> yalnızca diğer veri kümesinde eşleşmesi olan nesnelerin döndürüldildiği bir iç birleştirme türü uygular.</span><span class="sxs-lookup"><span data-stu-id="5e715-110">(For comparison, Transact-SQL supports join operators other than 'equals', for example the 'less than' operator.) In relational database terms, <xref:System.Linq.Enumerable.Join%2A> implements an inner join, a type of join in which only those objects that have a match in the other data set are returned.</span></span> <span data-ttu-id="5e715-111">Yöntem <xref:System.Linq.Enumerable.GroupJoin%2A> ilişkisel veritabanı açısından doğrudan eşdeğeri yoktur, ancak iç birleştirmeler ve sol dış birleştirmeler bir süper kümesi uygular.</span><span class="sxs-lookup"><span data-stu-id="5e715-111">The <xref:System.Linq.Enumerable.GroupJoin%2A> method has no direct equivalent in relational database terms, but it implements a superset of inner joins and left outer joins.</span></span> <span data-ttu-id="5e715-112">Sol dış birleştirme, diğer veri kaynağında ilişkili öğe olmasa bile, ilk (sol) veri kaynağının her öğesini döndüren bir birleştirmedir.</span><span class="sxs-lookup"><span data-stu-id="5e715-112">A left outer join is a join that returns each element of the first (left) data source, even if it has no correlated elements in the other data source.</span></span>  
  
 <span data-ttu-id="5e715-113">Aşağıdaki resimde, iki kümenin kavramsal görünümü ve bu kümeler içindeki iç birleştirme veya sol dış birleştirmede yer alan öğeler gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="5e715-113">The following illustration shows a conceptual view of two sets and the elements within those sets that are included in either an inner join or a left outer join.</span></span>  
  
 ![İç&#47;gösteren iki çakışan daire.](./media/join-operations/join-method-overlapping-circles.png)  
  
## <a name="methods"></a><span data-ttu-id="5e715-115">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="5e715-115">Methods</span></span>  
  
|<span data-ttu-id="5e715-116">Yöntem Adı</span><span class="sxs-lookup"><span data-stu-id="5e715-116">Method Name</span></span>|<span data-ttu-id="5e715-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5e715-117">Description</span></span>|<span data-ttu-id="5e715-118">C# Sorgu İfade Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5e715-118">C# Query Expression Syntax</span></span>|<span data-ttu-id="5e715-119">Daha Fazla Bilgi</span><span class="sxs-lookup"><span data-stu-id="5e715-119">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|Join|<span data-ttu-id="5e715-120">Anahtar seçici işlevlerine dayalı iki diziyi birleştirir ve değer çiftlerini ayıklar.</span><span class="sxs-lookup"><span data-stu-id="5e715-120">Joins two sequences based on key selector functions and extracts pairs of values.</span></span>|`join … in … on … equals …`|<xref:System.Linq.Enumerable.Join%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Join%2A?displayProperty=nameWithType>|  
|GroupJoin|<span data-ttu-id="5e715-121">Anahtar seçici işlevlerine dayalı iki diziyi birleştirir ve her öğe için elde edilen eşleşmeleri gruplandırmaz.</span><span class="sxs-lookup"><span data-stu-id="5e715-121">Joins two sequences based on key selector functions and groups the resulting matches for each element.</span></span>|`join … in … on … equals … into …`|<xref:System.Linq.Enumerable.GroupJoin%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.GroupJoin%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="5e715-122">Sorgu ifade sözdizimi örnekleri</span><span class="sxs-lookup"><span data-stu-id="5e715-122">Query expression syntax examples</span></span>
  
### Join  
  
<span data-ttu-id="5e715-123">Aşağıdaki örnek, `join … in … on … equals …` belirli bir değere dayalı iki diziyi birleştirmek için yan tümceyi kullanır:</span><span class="sxs-lookup"><span data-stu-id="5e715-123">The following example uses the `join … in … on … equals …` clause to join two sequences based on specific value:</span></span>
  
[!code-csharp[Join](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csLINQJoinOperation/CS/JoinOperation.cs#Join)]  

### GroupJoin  

<span data-ttu-id="5e715-124">Aşağıdaki örnek, `join … in … on … equals … into …` belirli bir değere dayalı iki diziyi birleştirmek için yan tümceyi kullanır ve her öğe için elde edilen eşleşmeleri gruplar:</span><span class="sxs-lookup"><span data-stu-id="5e715-124">The following example uses the `join … in … on … equals … into …` clause to join two sequences based on specific value and groups the resulting matches for each element:</span></span>
  
[!code-csharp[GroupJoin](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csLINQJoinOperation/CS/JoinOperation.cs#GroupJoin)]  
  
## <a name="see-also"></a><span data-ttu-id="5e715-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5e715-125">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="5e715-126">Standart Sorgu Operatörlerine Genel Bakış (C#)</span><span class="sxs-lookup"><span data-stu-id="5e715-126">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="5e715-127">Anonim Türler</span><span class="sxs-lookup"><span data-stu-id="5e715-127">Anonymous Types</span></span>](../../classes-and-structs/anonymous-types.md)
- [<span data-ttu-id="5e715-128">Birleşimler ve Çapraz Ürün Sorguları Düzenleme</span><span class="sxs-lookup"><span data-stu-id="5e715-128">Formulate Joins and Cross-Product Queries</span></span>](../../../../framework/data/adonet/sql/linq/formulate-joins-and-cross-product-queries.md)
- [<span data-ttu-id="5e715-129">birleştirme yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="5e715-129">join clause</span></span>](../../../language-reference/keywords/join-clause.md)
- <span data-ttu-id="5e715-130">[Joinkompozit tuşlar kullanarak](../../../linq/join-by-using-composite-keys.md)</span><span class="sxs-lookup"><span data-stu-id="5e715-130">[Join by using composite keys](../../../linq/join-by-using-composite-keys.md)</span></span>
- [<span data-ttu-id="5e715-131">Farklı dosyalardan (LINQ) (C#) içerik birleştirme</span><span class="sxs-lookup"><span data-stu-id="5e715-131">How to join content from dissimilar files (LINQ) (C#)</span></span>](./how-to-join-content-from-dissimilar-files-linq.md)
- [<span data-ttu-id="5e715-132">Join yan tümcesinin sonuçlarını sıralama</span><span class="sxs-lookup"><span data-stu-id="5e715-132">Order the results of a join clause</span></span>](../../../linq/order-the-results-of-a-join-clause.md)
- [<span data-ttu-id="5e715-133">Özel birleştirme işlemleri gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="5e715-133">Perform custom join operations</span></span>](../../../linq/perform-custom-join-operations.md)
- [<span data-ttu-id="5e715-134">Gruplanmış birleşimler gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="5e715-134">Perform grouped joins</span></span>](../../../linq/perform-grouped-joins.md)
- [<span data-ttu-id="5e715-135">İç birleşimler gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="5e715-135">Perform inner joins</span></span>](../../../linq/perform-inner-joins.md)
- [<span data-ttu-id="5e715-136">Sol dış birleşimler gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="5e715-136">Perform left outer joins</span></span>](../../../linq/perform-left-outer-joins.md)
- [<span data-ttu-id="5e715-137">Nesne koleksiyonları birden çok kaynaktan (LINQ) (C#) doldurma</span><span class="sxs-lookup"><span data-stu-id="5e715-137">How to populate object collections from multiple sources (LINQ) (C#)</span></span>](./how-to-populate-object-collections-from-multiple-sources-linq.md)
