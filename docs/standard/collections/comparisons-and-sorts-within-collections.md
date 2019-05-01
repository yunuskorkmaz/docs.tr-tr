---
title: Koleksiyonlardaki Karşılaştırmalar ve Sıralamalar
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 45f0e30efac32dec42cf0687fa0da40f4d6dca4f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61909083"
---
# <a name="comparisons-and-sorts-within-collections"></a><span data-ttu-id="b3053-102">Koleksiyonlardaki Karşılaştırmalar ve Sıralamalar</span><span class="sxs-lookup"><span data-stu-id="b3053-102">Comparisons and Sorts Within Collections</span></span>
<span data-ttu-id="b3053-103"><xref:System.Collections> Sınıfları kaldırılacak öğe için arama olup olmadığını koleksiyonları, yönetme veya anahtar-değer çiftinin değer döndüren ilgili neredeyse tüm işlemler karşılaştırmalar gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="b3053-103">The <xref:System.Collections> classes perform comparisons in almost all the processes involved in managing collections, whether searching for the element to remove or returning the value of a key-and-value pair.</span></span>  
  
 <span data-ttu-id="b3053-104">Koleksiyonlar, genellikle bir eşitlik karşılaştırıcısının ve/veya bir sipariş karşılaştırıcı kullanır.</span><span class="sxs-lookup"><span data-stu-id="b3053-104">Collections typically utilize an equality comparer and/or an ordering comparer.</span></span> <span data-ttu-id="b3053-105">İki yapıları karşılaştırmalar için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b3053-105">Two constructs are used for comparisons.</span></span>  
  
<a name="BKMK_Checkingforequality"></a>   
## <a name="checking-for-equality"></a><span data-ttu-id="b3053-106">Eşitlik için denetleniyor</span><span class="sxs-lookup"><span data-stu-id="b3053-106">Checking for equality</span></span>  
 <span data-ttu-id="b3053-107">Yöntemler gibi `Contains`, <xref:System.Collections.IList.IndexOf%2A>, <xref:System.Collections.Generic.List%601.LastIndexOf%2A>, ve `Remove` eşitlik karşılaştırıcısının koleksiyon öğeleri için kullanın.</span><span class="sxs-lookup"><span data-stu-id="b3053-107">Methods such as `Contains`, <xref:System.Collections.IList.IndexOf%2A>, <xref:System.Collections.Generic.List%601.LastIndexOf%2A>, and `Remove` use an equality comparer for the collection elements.</span></span> <span data-ttu-id="b3053-108">Koleksiyon genelse, öğe eşitlik aşağıdaki kılavuzlara göre karşılaştırılır:</span><span class="sxs-lookup"><span data-stu-id="b3053-108">If the collection is generic, than items are compared for equality according to the following guidelines:</span></span>  
  
- <span data-ttu-id="b3053-109">T türü uygulayan <xref:System.IEquatable%601> genel arabirim sonra eşitlik karşılaştırıcısının <xref:System.IEquatable%601.Equals%2A> o arabirimin yöntemi.</span><span class="sxs-lookup"><span data-stu-id="b3053-109">If type T implements the <xref:System.IEquatable%601> generic interface, then the equality comparer is the <xref:System.IEquatable%601.Equals%2A> method of that interface.</span></span>  
  
- <span data-ttu-id="b3053-110">T türü uygulamazsa <xref:System.IEquatable%601>, <xref:System.Object.Equals%2A?displayProperty=nameWithType> kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b3053-110">If type T does not implement <xref:System.IEquatable%601>, <xref:System.Object.Equals%2A?displayProperty=nameWithType> is used.</span></span>  
  
 <span data-ttu-id="b3053-111">Ayrıca, bazı oluşturucu aşırı yüklemeleri sözlük koleksiyonlar için kabul bir <xref:System.Collections.Generic.IEqualityComparer%601> eşitlik için anahtarları karşılaştırmak için kullanılan uygulama.</span><span class="sxs-lookup"><span data-stu-id="b3053-111">In addition, Some constructor overloads for dictionary collections accept an <xref:System.Collections.Generic.IEqualityComparer%601> implementation, which is used to compare keys for equality.</span></span> <span data-ttu-id="b3053-112">Bir örnek için bkz <xref:System.Collections.Generic.Dictionary%602.%23ctor%2A?displayProperty=nameWithType> Oluşturucusu.</span><span class="sxs-lookup"><span data-stu-id="b3053-112">For an example, see the <xref:System.Collections.Generic.Dictionary%602.%23ctor%2A?displayProperty=nameWithType> constructor.</span></span>  
  
<a name="BKMK_Determiningsortorder"></a>   
## <a name="determining-sort-order"></a><span data-ttu-id="b3053-113">Sıralama düzenini belirleme</span><span class="sxs-lookup"><span data-stu-id="b3053-113">Determining sort order</span></span>  
 <span data-ttu-id="b3053-114">Yöntemler gibi `BinarySearch` ve `Sort` koleksiyon öğeleri için bir sıralama karşılaştırıcı kullanın.</span><span class="sxs-lookup"><span data-stu-id="b3053-114">Methods such as `BinarySearch` and `Sort` use an ordering comparer for the collection elements.</span></span> <span data-ttu-id="b3053-115">Karşılaştırmalar, koleksiyonun öğeleri arasında veya bir öğe ile belirtilen değer arasında olabilir.</span><span class="sxs-lookup"><span data-stu-id="b3053-115">The comparisons can be between elements of the collection, or between an element and a specified value.</span></span> <span data-ttu-id="b3053-116">Nesneleri karşılaştırma için kavramı yoktur bir `default comparer` ve `explicit comparer`.</span><span class="sxs-lookup"><span data-stu-id="b3053-116">For comparing objects, there is the concept of a `default comparer` and an `explicit comparer`.</span></span>  
  
 <span data-ttu-id="b3053-117">En az bir uygulama karşılaştırılan nesnelerin varsayılan karşılaştırıcı kullanır **IComparable** arabirimi.</span><span class="sxs-lookup"><span data-stu-id="b3053-117">The default comparer relies on at least one of the objects being compared to implement the **IComparable** interface.</span></span> <span data-ttu-id="b3053-118">Uygulamak için iyi bir uygulamadır **IComparable** üzerinde tüm sınıflar, değerleri bir liste koleksiyon veya bir sözlük koleksiyondaki anahtarlar olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b3053-118">It is a good practice to implement **IComparable** on all classes are used as values in a list collection or as keys in a dictionary collection.</span></span> <span data-ttu-id="b3053-119">Genel bir koleksiyon için eşitlik karşılaştırma aşağıdakilere göre belirlenir:</span><span class="sxs-lookup"><span data-stu-id="b3053-119">For a generic collection, equality comparison is determined according to the following:</span></span>  
  
- <span data-ttu-id="b3053-120">T türü uygulayan <xref:System.IComparable%601?displayProperty=nameWithType> genel arabirim sonra varsayılan karşılaştırıcı <xref:System.IComparable%601.CompareTo%28%600%29?displayProperty=nameWithType> o arabirimin yöntemi</span><span class="sxs-lookup"><span data-stu-id="b3053-120">If type T implements the <xref:System.IComparable%601?displayProperty=nameWithType> generic interface, then the default comparer is the <xref:System.IComparable%601.CompareTo%28%600%29?displayProperty=nameWithType> method of that interface</span></span>  
  
- <span data-ttu-id="b3053-121">T türü genel olmayan uyguluyorsa <xref:System.IComparable?displayProperty=nameWithType> arabirim ise varsayılan karşılaştırıcı <xref:System.IComparable.CompareTo%28System.Object%29?displayProperty=nameWithType> o arabirimin yöntemi.</span><span class="sxs-lookup"><span data-stu-id="b3053-121">If type T implements the non-generic <xref:System.IComparable?displayProperty=nameWithType> interface, then the default comparer is the <xref:System.IComparable.CompareTo%28System.Object%29?displayProperty=nameWithType> method of that interface.</span></span>  
  
- <span data-ttu-id="b3053-122">T türü ya da arabirimi uygulamaz, ardından hiçbir varsayılan karşılaştırıcı yoktur ve bir karşılaştırıcı veya karşılaştırma temsilciyi açıkça belirtilmelidir.</span><span class="sxs-lookup"><span data-stu-id="b3053-122">If type T doesn’t implement either interface, then there is no default comparer, and a comparer or comparison delegate must be provided explicitly.</span></span>  
  
 <span data-ttu-id="b3053-123">Açık karşılaştırma sağlamak için bazı yöntemler kabul bir **IComparer** bir parametre olarak bir uygulama.</span><span class="sxs-lookup"><span data-stu-id="b3053-123">To provide explicit comparisons, some methods accept an **IComparer** implementation as a parameter.</span></span> <span data-ttu-id="b3053-124">Örneğin, <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType> yöntemi kabul bir <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> uygulaması.</span><span class="sxs-lookup"><span data-stu-id="b3053-124">For example, the <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType> method accepts an <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> implementation.</span></span>  
  
 <span data-ttu-id="b3053-125">Koleksiyonlardaki karşılaştırmalar ve sıralamalar bir koleksiyon içinde sistemin geçerli kültür ayarı etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="b3053-125">The current culture setting of the system can affect the comparisons and sorts within a collection.</span></span> <span data-ttu-id="b3053-126">Varsayılan, karşılaştırma ve sıralar **koleksiyonları** kültüre duyarlı sınıflardır.</span><span class="sxs-lookup"><span data-stu-id="b3053-126">By default, the comparisons and sorts in the **Collections** classes are culture-sensitive.</span></span> <span data-ttu-id="b3053-127">Kültür ayarı yok sayılır ve bu nedenle tutarlı karşılaştırma ve sıralama sonuçları elde etmek için kullanın <xref:System.Globalization.CultureInfo.InvariantCulture%2A> kabul üye aşırı yüklemeleri ile bir <xref:System.Globalization.CultureInfo>.</span><span class="sxs-lookup"><span data-stu-id="b3053-127">To ignore the culture setting and therefore obtain consistent comparison and sorting results, use the <xref:System.Globalization.CultureInfo.InvariantCulture%2A> with member overloads that accept a <xref:System.Globalization.CultureInfo>.</span></span> <span data-ttu-id="b3053-128">Daha fazla bilgi için [koleksiyonlarda kültüre duyarsız dize işlemlerini gerçekleştirme](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-collections.md) ve [dizilerde kültüre duyarsız dize işlemlerini gerçekleştirme](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-arrays.md).</span><span class="sxs-lookup"><span data-stu-id="b3053-128">For more information, see [Performing Culture-Insensitive String Operations in Collections](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-collections.md) and [Performing Culture-Insensitive String Operations in Arrays](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-arrays.md).</span></span>  
  
<a name="BKMK_Equalityandsortexample"></a>   
## <a name="equality-and-sort-example"></a><span data-ttu-id="b3053-129">Eşitlik ve sıralama örneği</span><span class="sxs-lookup"><span data-stu-id="b3053-129">Equality and sort example</span></span>  
 <span data-ttu-id="b3053-130">Aşağıdaki kod bir uygulamasını gösterir <xref:System.IEquatable%601> ve <xref:System.IComparable%601> basit iş nesnesinde.</span><span class="sxs-lookup"><span data-stu-id="b3053-130">The following code demonstrates an implementation of <xref:System.IEquatable%601> and <xref:System.IComparable%601> on a simple business object.</span></span> <span data-ttu-id="b3053-131">Ayrıca, nesnenin bir listede depolanıp sıralanmış çağırmanın görürsünüz <xref:System.Collections.Generic.List%601.Sort> yöntemi için varsayılan karşılaştırıcı kullanımıyla sonuçlanıyor `Part` türü ve <xref:System.Collections.Generic.List%601.Sort%28System.Comparison%7B%600%7D%29> anonim bir yöntem kullanılarak uygulanan yöntem.</span><span class="sxs-lookup"><span data-stu-id="b3053-131">In addition, when the object is stored in a list and sorted, you will see that calling the <xref:System.Collections.Generic.List%601.Sort> method results in the use of the default comparer for the `Part` type, and the <xref:System.Collections.Generic.List%601.Sort%28System.Comparison%7B%600%7D%29> method implemented by using an anonymous method.</span></span>  
  
 [!code-csharp[System.Collections.Generic.List.Sort#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.collections.generic.list.sort/cs/program.cs#1)]
 [!code-vb[System.Collections.Generic.List.Sort#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.collections.generic.list.sort/vb/module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="b3053-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b3053-132">See also</span></span>

- <xref:System.Collections.IComparer>
- <xref:System.IEquatable%601>
- <xref:System.Collections.Generic.IComparer%601>
- <xref:System.IComparable>
- <xref:System.IComparable%601>
