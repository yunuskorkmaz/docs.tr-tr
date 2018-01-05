---
title: "Koleksiyonlardaki Karşılaştırmalar ve Sıralamalar"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 826adbecfc6a57b05db482766baae397ce72bc9d
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="comparisons-and-sorts-within-collections"></a><span data-ttu-id="5cdf2-102">Koleksiyonlardaki Karşılaştırmalar ve Sıralamalar</span><span class="sxs-lookup"><span data-stu-id="5cdf2-102">Comparisons and Sorts Within Collections</span></span>
<span data-ttu-id="5cdf2-103"><xref:System.Collections> Sınıfları öğesi kaldırmak arama olup olmadığını koleksiyonlar, yönetme veya bir anahtar-değer çiftinin değer döndürme söz konusu neredeyse tüm işlemlerde karşılaştırmaları gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="5cdf2-103">The <xref:System.Collections> classes perform comparisons in almost all the processes involved in managing collections, whether searching for the element to remove or returning the value of a key-and-value pair.</span></span>  
  
 <span data-ttu-id="5cdf2-104">Koleksiyonlar, genellikle bir eşitlik karşılaştırıcısını ve/veya bir sıralama karşılaştırıcı kullanın.</span><span class="sxs-lookup"><span data-stu-id="5cdf2-104">Collections typically utilize an equality comparer and/or an ordering comparer.</span></span> <span data-ttu-id="5cdf2-105">İki yapıları karşılaştırmaları için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5cdf2-105">Two constructs are used for comparisons.</span></span>  
  
<a name="BKMK_Checkingforequality"></a>   
## <a name="checking-for-equality"></a><span data-ttu-id="5cdf2-106">Eşitlik için denetleniyor</span><span class="sxs-lookup"><span data-stu-id="5cdf2-106">Checking for equality</span></span>  
 <span data-ttu-id="5cdf2-107">Gibi yöntemler `Contains`, <xref:System.Collections.IList.IndexOf%2A>, <xref:System.Collections.Generic.List%601.LastIndexOf%2A>, ve `Remove` bir eşitlik karşılaştırıcısını koleksiyon öğeleri için kullanın.</span><span class="sxs-lookup"><span data-stu-id="5cdf2-107">Methods such as `Contains`, <xref:System.Collections.IList.IndexOf%2A>, <xref:System.Collections.Generic.List%601.LastIndexOf%2A>, and `Remove` use an equality comparer for the collection elements.</span></span> <span data-ttu-id="5cdf2-108">Koleksiyon genel ise, öğeleri aşağıdaki kılavuzlara göre eşitliği karşılaştırılır:</span><span class="sxs-lookup"><span data-stu-id="5cdf2-108">If the collection is generic, than items are compared for equality according to the following guidelines:</span></span>  
  
-   <span data-ttu-id="5cdf2-109">Varsa T türü uygular <xref:System.IEquatable%601> genel arabirim eşitlik karşılaştırıcısını olduğundan <xref:System.IEquatable%601.Equals%2A> arabirimi yöntemi.</span><span class="sxs-lookup"><span data-stu-id="5cdf2-109">If type T implements the <xref:System.IEquatable%601> generic interface, then the equality comparer is the <xref:System.IEquatable%601.Equals%2A> method of that interface.</span></span>  
  
-   <span data-ttu-id="5cdf2-110">T türü uygulamazsa <xref:System.IEquatable%601>, <xref:System.Object.Equals%2A?displayProperty=nameWithType> kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5cdf2-110">If type T does not implement <xref:System.IEquatable%601>, <xref:System.Object.Equals%2A?displayProperty=nameWithType> is used.</span></span>  
  
 <span data-ttu-id="5cdf2-111">Ayrıca, bazı Oluşturucusu aşırı sözlük koleksiyonlar için kabul bir <xref:System.Collections.Generic.IEqualityComparer%601> eşitlik tuşları karşılaştırmak için kullanılan uygulama.</span><span class="sxs-lookup"><span data-stu-id="5cdf2-111">In addition, Some constructor overloads for dictionary collections accept an <xref:System.Collections.Generic.IEqualityComparer%601> implementation, which is used to compare keys for equality.</span></span> <span data-ttu-id="5cdf2-112">Bir örnek için bkz: <xref:System.Collections.Generic.Dictionary%602.%23ctor%2A?displayProperty=nameWithType> Oluşturucusu.</span><span class="sxs-lookup"><span data-stu-id="5cdf2-112">For an example, see the <xref:System.Collections.Generic.Dictionary%602.%23ctor%2A?displayProperty=nameWithType> constructor.</span></span>  
  
<a name="BKMK_Determiningsortorder"></a>   
## <a name="determining-sort-order"></a><span data-ttu-id="5cdf2-113">Sıralama düzenini belirleme</span><span class="sxs-lookup"><span data-stu-id="5cdf2-113">Determining sort order</span></span>  
 <span data-ttu-id="5cdf2-114">Gibi yöntemler `BinarySearch` ve `Sort` için koleksiyon öğeleri sıralama karşılaştırıcı kullanın.</span><span class="sxs-lookup"><span data-stu-id="5cdf2-114">Methods such as `BinarySearch` and `Sort` use an ordering comparer for the collection elements.</span></span> <span data-ttu-id="5cdf2-115">Karşılaştırmaları koleksiyon öğelerini bir öğe ile belirtilen değer arasında veya olabilir.</span><span class="sxs-lookup"><span data-stu-id="5cdf2-115">The comparisons can be between elements of the collection, or between an element and a specified value.</span></span> <span data-ttu-id="5cdf2-116">Nesneleri karşılaştırma için kavramı yoktur bir `default comparer` ve bir `explicit comparer`.</span><span class="sxs-lookup"><span data-stu-id="5cdf2-116">For comparing objects, there is the concept of a `default comparer` and an `explicit comparer`.</span></span>  
  
 <span data-ttu-id="5cdf2-117">En az bir uygulamak için karşılaştırılan nesnelerin varsayılan karşılaştırıcı dayanır **IComparable** arabirimi.</span><span class="sxs-lookup"><span data-stu-id="5cdf2-117">The default comparer relies on at least one of the objects being compared to implement the **IComparable** interface.</span></span> <span data-ttu-id="5cdf2-118">Uygulamak için iyi bir uygulamadır **IComparable** tüm sınıflarında değerler liste koleksiyonu olarak veya bir sözlük koleksiyonu anahtar olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5cdf2-118">It is a good practice to implement **IComparable** on all classes are used as values in a list collection or as keys in a dictionary collection.</span></span> <span data-ttu-id="5cdf2-119">Genel bir koleksiyon için eşitlik karşılaştırması aşağıdaki göre belirlenir:</span><span class="sxs-lookup"><span data-stu-id="5cdf2-119">For a generic collection, equality comparison is determined according to the following:</span></span>  
  
-   <span data-ttu-id="5cdf2-120">Varsa T türü uygular <xref:System.IComparable%601?displayProperty=nameWithType> genel arabirim olduğundan, varsayılan karşılaştırıcı <xref:System.IComparable%601.CompareTo%28%600%29?displayProperty=nameWithType> bu arabirimin yöntemi</span><span class="sxs-lookup"><span data-stu-id="5cdf2-120">If type T implements the <xref:System.IComparable%601?displayProperty=nameWithType> generic interface, then the default comparer is the <xref:System.IComparable%601.CompareTo%28%600%29?displayProperty=nameWithType> method of that interface</span></span>  
  
-   <span data-ttu-id="5cdf2-121">T türü genel olmayan uyguluyorsa <xref:System.IComparable?displayProperty=nameWithType> arabirim ise varsayılan karşılaştırıcı <xref:System.IComparable.CompareTo%28System.Object%29?displayProperty=nameWithType> arabirimi yöntemi.</span><span class="sxs-lookup"><span data-stu-id="5cdf2-121">If type T implements the non-generic <xref:System.IComparable?displayProperty=nameWithType> interface, then the default comparer is the <xref:System.IComparable.CompareTo%28System.Object%29?displayProperty=nameWithType> method of that interface.</span></span>  
  
-   <span data-ttu-id="5cdf2-122">T türü ya da arabirimi uygulamaz, ardından varsayılan karşılaştırıcı yoktur ve karşılaştırıcı veya karşılaştırma temsilci açıkça sağlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5cdf2-122">If type T doesn’t implement either interface, then there is no default comparer, and a comparer or comparison delegate must be provided explicitly.</span></span>  
  
 <span data-ttu-id="5cdf2-123">Açık karşılaştırmaları sağlamak için bazı yöntemler kabul bir **IComparer** bir parametre olarak uygulama.</span><span class="sxs-lookup"><span data-stu-id="5cdf2-123">To provide explicit comparisons, some methods accept an **IComparer** implementation as a parameter.</span></span> <span data-ttu-id="5cdf2-124">Örneğin, <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType> yöntemi kabul eden bir <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> uygulaması.</span><span class="sxs-lookup"><span data-stu-id="5cdf2-124">For example, the <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType> method accepts an <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> implementation.</span></span>  
  
 <span data-ttu-id="5cdf2-125">Geçerli kültür ayarı sisteminin karşılaştırmalar ve sıralamalar bir koleksiyon içinde etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="5cdf2-125">The current culture setting of the system can affect the comparisons and sorts within a collection.</span></span> <span data-ttu-id="5cdf2-126">Varsayılan, karşılaştırmaları ve sıralar **koleksiyonları** sınıfları kültüre duyarlı.</span><span class="sxs-lookup"><span data-stu-id="5cdf2-126">By default, the comparisons and sorts in the **Collections** classes are culture-sensitive.</span></span> <span data-ttu-id="5cdf2-127">Kültür ayarı yoksay ve bu nedenle tutarlı karşılaştırma ve sıralama sonuçları almak için kullanmak <xref:System.Globalization.CultureInfo.InvariantCulture%2A> kabul üye aşırı ile bir <xref:System.Globalization.CultureInfo>.</span><span class="sxs-lookup"><span data-stu-id="5cdf2-127">To ignore the culture setting and therefore obtain consistent comparison and sorting results, use the <xref:System.Globalization.CultureInfo.InvariantCulture%2A> with member overloads that accept a <xref:System.Globalization.CultureInfo>.</span></span> <span data-ttu-id="5cdf2-128">Daha fazla bilgi için bkz: [koleksiyonlarda kültüre duyarsız dize işlemlerini gerçekleştirme](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-collections.md) ve [dizilerde kültüre duyarsız dize işlemlerini gerçekleştirme](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-arrays.md).</span><span class="sxs-lookup"><span data-stu-id="5cdf2-128">For more information, see [Performing Culture-Insensitive String Operations in Collections](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-collections.md) and [Performing Culture-Insensitive String Operations in Arrays](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-arrays.md).</span></span>  
  
<a name="BKMK_Equalityandsortexample"></a>   
## <a name="equality-and-sort-example"></a><span data-ttu-id="5cdf2-129">Eşitlik ve sıralama örneği</span><span class="sxs-lookup"><span data-stu-id="5cdf2-129">Equality and sort example</span></span>  
 <span data-ttu-id="5cdf2-130">Aşağıdaki kod bir uygulama ortaya koyar <xref:System.IEquatable%601> ve <xref:System.IComparable%601> basit iş nesnesi üzerinde.</span><span class="sxs-lookup"><span data-stu-id="5cdf2-130">The following code demonstrates an implementation of <xref:System.IEquatable%601> and <xref:System.IComparable%601> on a simple business object.</span></span> <span data-ttu-id="5cdf2-131">Ayrıca, nesne bir listede depolanıp sıralanmış çağırmanın görürsünüz <xref:System.Collections.Generic.List%601.Sort> yöntemi için varsayılan karşılaştırıcı kullanımıyla sonuçlanıyor `Part` türü ve <xref:System.Collections.Generic.List%601.Sort%28System.Comparison%7B%600%7D%29> anonim bir yöntemi kullanarak uygulanan yöntemi.</span><span class="sxs-lookup"><span data-stu-id="5cdf2-131">In addition, when the object is stored in a list and sorted, you will see that calling the <xref:System.Collections.Generic.List%601.Sort> method results in the use of the default comparer for the `Part` type, and the <xref:System.Collections.Generic.List%601.Sort%28System.Comparison%7B%600%7D%29> method implemented by using an anonymous method.</span></span>  
  
 [!code-csharp[System.Collections.Generic.List.Sort#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.collections.generic.list.sort/cs/program.cs#1)]
 [!code-vb[System.Collections.Generic.List.Sort#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.collections.generic.list.sort/vb/module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="5cdf2-132">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5cdf2-132">See Also</span></span>  
 <xref:System.Collections.IComparer>  
 <xref:System.IEquatable%601>  
 <xref:System.Collections.Generic.IComparer%601>  
 <xref:System.IComparable>  
 <xref:System.IComparable%601>
