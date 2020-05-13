---
title: Koleksiyonlardaki Karşılaştırmalar ve Sıralamalar
ms.date: 04/30/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sorting data, collections
- IComparable.CompareTo method
- Collections classes
- Equals method
- collections [.NET Framework], comparisons
ms.assetid: 5e4d3b45-97f0-423c-a65f-c492ed40e73b
ms.openlocfilehash: 8e4530063f14211688e5ef2d2ec4ed7e4834cdf1
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212973"
---
# <a name="comparisons-and-sorts-within-collections"></a><span data-ttu-id="88cb3-102">Koleksiyonlardaki karşılaştırma ve sıralamalar</span><span class="sxs-lookup"><span data-stu-id="88cb3-102">Comparisons and sorts within collections</span></span>

<span data-ttu-id="88cb3-103"><xref:System.Collections>Sınıflar, bir anahtar-değer çiftinin değerini kaldırmak ya da döndürmek için arama yapılıp yapılmayacağını, koleksiyonları yönetmeye dahil olan tüm işlemlerde karşılaştırmalar gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="88cb3-103">The <xref:System.Collections> classes perform comparisons in almost all the processes involved in managing collections, whether searching for the element to remove or returning the value of a key-and-value pair.</span></span>

<span data-ttu-id="88cb3-104">Koleksiyonlar genellikle bir eşitlik karşılaştırıcısı ve/veya bir sıralama karşılaştırıcısı kullanır.</span><span class="sxs-lookup"><span data-stu-id="88cb3-104">Collections typically utilize an equality comparer and/or an ordering comparer.</span></span> <span data-ttu-id="88cb3-105">Karşılaştırmalar için iki yapı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="88cb3-105">Two constructs are used for comparisons.</span></span>

<a name="BKMK_Checkingforequality"></a>
## <a name="check-for-equality"></a><span data-ttu-id="88cb3-106">Eşitlik için denetle</span><span class="sxs-lookup"><span data-stu-id="88cb3-106">Check for equality</span></span>

<span data-ttu-id="88cb3-107">,, Ve gibi yöntemler, `Contains` <xref:System.Collections.IList.IndexOf%2A> <xref:System.Collections.Generic.List%601.LastIndexOf%2A> `Remove` koleksiyon öğeleri için eşitlik karşılaştırıcısı kullanır.</span><span class="sxs-lookup"><span data-stu-id="88cb3-107">Methods such as `Contains`, <xref:System.Collections.IList.IndexOf%2A>, <xref:System.Collections.Generic.List%601.LastIndexOf%2A>, and `Remove` use an equality comparer for the collection elements.</span></span> <span data-ttu-id="88cb3-108">Koleksiyon genel ise, öğeler aşağıdaki yönergelere göre eşitlik için karşılaştırılır:</span><span class="sxs-lookup"><span data-stu-id="88cb3-108">If the collection is generic, then items are compared for equality according to the following guidelines:</span></span>

- <span data-ttu-id="88cb3-109">Tür T <xref:System.IEquatable%601> genel arabirimi uygularsa, eşitlik karşılaştırıcısı <xref:System.IEquatable%601.Equals%2A> Bu arabirimin yöntemidir.</span><span class="sxs-lookup"><span data-stu-id="88cb3-109">If type T implements the <xref:System.IEquatable%601> generic interface, then the equality comparer is the <xref:System.IEquatable%601.Equals%2A> method of that interface.</span></span>

- <span data-ttu-id="88cb3-110">T türü uygulamadıysanız <xref:System.IEquatable%601> , <xref:System.Object.Equals%2A?displayProperty=nameWithType> kullanılır.</span><span class="sxs-lookup"><span data-stu-id="88cb3-110">If type T does not implement <xref:System.IEquatable%601>, <xref:System.Object.Equals%2A?displayProperty=nameWithType> is used.</span></span>

<span data-ttu-id="88cb3-111">Ayrıca, sözlük koleksiyonları için bazı Oluşturucu aşırı yüklemeleri <xref:System.Collections.Generic.IEqualityComparer%601> , anahtarları eşitlik için karşılaştırmak üzere kullanılan bir uygulamayı kabul eder.</span><span class="sxs-lookup"><span data-stu-id="88cb3-111">In addition, some constructor overloads for dictionary collections accept an <xref:System.Collections.Generic.IEqualityComparer%601> implementation, which is used to compare keys for equality.</span></span> <span data-ttu-id="88cb3-112">Bir örnek için, oluşturucuya bakın <xref:System.Collections.Generic.Dictionary%602.%23ctor%2A> .</span><span class="sxs-lookup"><span data-stu-id="88cb3-112">For an example, see the <xref:System.Collections.Generic.Dictionary%602.%23ctor%2A> constructor.</span></span>

<a name="BKMK_Determiningsortorder"></a>
## <a name="determine-sort-order"></a><span data-ttu-id="88cb3-113">Sıralama düzenini belirleme</span><span class="sxs-lookup"><span data-stu-id="88cb3-113">Determine sort order</span></span>

<span data-ttu-id="88cb3-114">Ve gibi yöntemler `BinarySearch` `Sort` , koleksiyon öğeleri için bir sıralama karşılaştırıcısı kullanır.</span><span class="sxs-lookup"><span data-stu-id="88cb3-114">Methods such as `BinarySearch` and `Sort` use an ordering comparer for the collection elements.</span></span> <span data-ttu-id="88cb3-115">Karşılaştırmalar koleksiyonun öğeleri arasında veya bir öğe ile belirtilen değer arasında olabilir.</span><span class="sxs-lookup"><span data-stu-id="88cb3-115">The comparisons can be between elements of the collection, or between an element and a specified value.</span></span> <span data-ttu-id="88cb3-116">Nesneleri karşılaştırmak için ve bir kavramı vardır `default comparer` `explicit comparer` .</span><span class="sxs-lookup"><span data-stu-id="88cb3-116">For comparing objects, there is the concept of a `default comparer` and an `explicit comparer`.</span></span>

<span data-ttu-id="88cb3-117">Varsayılan karşılaştırıcı, **IComparable** arabirimini uygulamak için karşılaştırılan nesnelerden en az birini temel alır.</span><span class="sxs-lookup"><span data-stu-id="88cb3-117">The default comparer relies on at least one of the objects being compared to implement the **IComparable** interface.</span></span> <span data-ttu-id="88cb3-118">Tüm sınıflarda **IComparable** uygulamak iyi bir uygulamadır, bir liste koleksiyonunda değer olarak veya bir sözlük koleksiyonundaki anahtarlar olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="88cb3-118">It is a good practice to implement **IComparable** on all classes are used as values in a list collection or as keys in a dictionary collection.</span></span> <span data-ttu-id="88cb3-119">Genel bir koleksiyon için eşitlik karşılaştırması aşağıdakilere göre belirlenir:</span><span class="sxs-lookup"><span data-stu-id="88cb3-119">For a generic collection, equality comparison is determined according to the following:</span></span>

- <span data-ttu-id="88cb3-120">Tür T <xref:System.IComparable%601?displayProperty=nameWithType> genel arabirimi uygularsa, varsayılan karşılaştırıcı <xref:System.IComparable%601.CompareTo%28%600%29?displayProperty=nameWithType> Bu arabirimin yöntemidir</span><span class="sxs-lookup"><span data-stu-id="88cb3-120">If type T implements the <xref:System.IComparable%601?displayProperty=nameWithType> generic interface, then the default comparer is the <xref:System.IComparable%601.CompareTo%28%600%29?displayProperty=nameWithType> method of that interface</span></span>

- <span data-ttu-id="88cb3-121">Tür T genel olmayan arabirimi uygularsa <xref:System.IComparable?displayProperty=nameWithType> , varsayılan karşılaştırıcı <xref:System.IComparable.CompareTo%28System.Object%29?displayProperty=nameWithType> Bu arabirimin yöntemidir.</span><span class="sxs-lookup"><span data-stu-id="88cb3-121">If type T implements the non-generic <xref:System.IComparable?displayProperty=nameWithType> interface, then the default comparer is the <xref:System.IComparable.CompareTo%28System.Object%29?displayProperty=nameWithType> method of that interface.</span></span>

- <span data-ttu-id="88cb3-122">Tür T her iki arabirimi de uygulamadığından, varsayılan karşılaştırıcı yoktur ve açıkça bir karşılaştırıcı veya karşılaştırma temsilcisi sağlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="88cb3-122">If type T doesn't implement either interface, then there is no default comparer, and a comparer or comparison delegate must be provided explicitly.</span></span>

<span data-ttu-id="88cb3-123">Açık karşılaştırmalar sağlamak için bazı yöntemler bir **IComparer** uygulamasını parametre olarak kabul eder.</span><span class="sxs-lookup"><span data-stu-id="88cb3-123">To provide explicit comparisons, some methods accept an **IComparer** implementation as a parameter.</span></span> <span data-ttu-id="88cb3-124">Örneğin, <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType> yöntemi bir uygulamayı kabul eder <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="88cb3-124">For example, the <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType> method accepts an <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> implementation.</span></span>

<span data-ttu-id="88cb3-125">Sistemin geçerli kültür ayarı karşılaştırmaları etkileyebilir ve bir koleksiyon içinde sıralama yapabilir.</span><span class="sxs-lookup"><span data-stu-id="88cb3-125">The current culture setting of the system can affect the comparisons and sorts within a collection.</span></span> <span data-ttu-id="88cb3-126">Varsayılan olarak, **koleksiyonlar** sınıflarında karşılaştırmalar ve sıralamalar kültüre duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="88cb3-126">By default, the comparisons and sorts in the **Collections** classes are culture-sensitive.</span></span> <span data-ttu-id="88cb3-127">Kültür ayarını yoksaymak ve bu nedenle tutarlı karşılaştırma ve sıralama sonuçları elde etmek için, <xref:System.Globalization.CultureInfo.InvariantCulture%2A> bir kabul eden üye aşırı yüklerini kullanın <xref:System.Globalization.CultureInfo> .</span><span class="sxs-lookup"><span data-stu-id="88cb3-127">To ignore the culture setting and therefore obtain consistent comparison and sorting results, use the <xref:System.Globalization.CultureInfo.InvariantCulture%2A> with member overloads that accept a <xref:System.Globalization.CultureInfo>.</span></span> <span data-ttu-id="88cb3-128">Daha fazla bilgi için bkz. [koleksiyonlarda kültüre duyarsız dize Işlemleri gerçekleştirme](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-collections.md) ve [dizilerde kültüre duyarsız dize işlemlerini gerçekleştirme](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-arrays.md).</span><span class="sxs-lookup"><span data-stu-id="88cb3-128">For more information, see [Performing Culture-Insensitive String Operations in Collections](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-collections.md) and [Performing Culture-Insensitive String Operations in Arrays](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-arrays.md).</span></span>

<a name="BKMK_Equalityandsortexample"></a>
## <a name="equality-and-sort-example"></a><span data-ttu-id="88cb3-129">Eşitlik ve sıralama örneği</span><span class="sxs-lookup"><span data-stu-id="88cb3-129">Equality and sort example</span></span>

<span data-ttu-id="88cb3-130">Aşağıdaki kod <xref:System.IEquatable%601> <xref:System.IComparable%601> basit bir iş nesnesi üzerinde ve üzerinde bir uygulamasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="88cb3-130">The following code demonstrates an implementation of <xref:System.IEquatable%601> and <xref:System.IComparable%601> on a simple business object.</span></span> <span data-ttu-id="88cb3-131">Ayrıca, nesnesi bir listede depolandığında ve sıralandığında, yöntemi çağırmanın, <xref:System.Collections.Generic.List%601.Sort> tür için varsayılan karşılaştırıcının kullanılmasına `Part` ve <xref:System.Collections.Generic.List%601.Sort%28System.Comparison%7B%600%7D%29> bir anonim yöntem kullanılarak uygulanan yönteme neden olduğunu görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="88cb3-131">In addition, when the object is stored in a list and sorted, you will see that calling the <xref:System.Collections.Generic.List%601.Sort> method results in the use of the default comparer for the `Part` type, and the <xref:System.Collections.Generic.List%601.Sort%28System.Comparison%7B%600%7D%29> method implemented by using an anonymous method.</span></span>

[!code-csharp[System.Collections.Generic.List.Sort#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.collections.generic.list.sort/cs/program.cs#1)]
[!code-vb[System.Collections.Generic.List.Sort#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.collections.generic.list.sort/vb/module1.vb#1)]

## <a name="see-also"></a><span data-ttu-id="88cb3-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="88cb3-132">See also</span></span>

- <xref:System.Collections.IComparer>
- <xref:System.IEquatable%601>
- <xref:System.Collections.Generic.IComparer%601>
- <xref:System.IComparable>
- <xref:System.IComparable%601>
