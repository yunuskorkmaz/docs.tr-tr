---
title: "Sıralanmış Koleksiyon Türleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SortedDictionary collection type
- SortedList class, grouping data in collections
- grouping data in collections, SortedList collection type
- SortedList collection type
- collections [.NET Framework], SortedList collection type
ms.assetid: 3db965b2-36a6-4b12-b76e-7f074ff7275a
caps.latest.revision: "16"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 7efe53d472e1789d49acc3973acdf190c8ff6662
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="sorted-collection-types"></a><span data-ttu-id="fb7cb-102">Sıralanmış Koleksiyon Türleri</span><span class="sxs-lookup"><span data-stu-id="fb7cb-102">Sorted Collection Types</span></span>
<span data-ttu-id="fb7cb-103"><xref:System.Collections.SortedList?displayProperty=nameWithType> Sınıfı, <xref:System.Collections.Generic.SortedList%602?displayProperty=nameWithType> genel bir sınıf ve <xref:System.Collections.Generic.SortedDictionary%602?displayProperty=nameWithType> genel sınıfı benzer <xref:System.Collections.Hashtable> sınıfı ve <xref:System.Collections.Generic.Dictionary%602> genel sınıf uyguladıkları, <xref:System.Collections.IDictionary> arabirimi, ancak bunların bakımını kendi anahtara göre sıralama öğelerinde sipariş ve O(1) ekleme ve alma karma tablosu özellik yok.</span><span class="sxs-lookup"><span data-stu-id="fb7cb-103">The <xref:System.Collections.SortedList?displayProperty=nameWithType> class, the <xref:System.Collections.Generic.SortedList%602?displayProperty=nameWithType> generic class, and the <xref:System.Collections.Generic.SortedDictionary%602?displayProperty=nameWithType> generic class are similar to the <xref:System.Collections.Hashtable> class and the <xref:System.Collections.Generic.Dictionary%602> generic class in that they implement the <xref:System.Collections.IDictionary> interface, but they maintain their elements in sort order by key, and they do not have the O(1) insertion and retrieval characteristic of hash tables.</span></span> <span data-ttu-id="fb7cb-104">Üç sınıfları ortak çeşitli özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="fb7cb-104">The three classes have several features in common:</span></span>  
  
-   <span data-ttu-id="fb7cb-105">Tüm üç sınıf uygulamak <xref:System.Collections.IDictionary?displayProperty=nameWithType> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="fb7cb-105">All three classes implement the <xref:System.Collections.IDictionary?displayProperty=nameWithType> interface.</span></span> <span data-ttu-id="fb7cb-106">İki genel sınıfları Ayrıca uygulama <xref:System.Collections.Generic.IDictionary%602?displayProperty=nameWithType> genel arabirim.</span><span class="sxs-lookup"><span data-stu-id="fb7cb-106">The two generic classes also implement the <xref:System.Collections.Generic.IDictionary%602?displayProperty=nameWithType> generic interface.</span></span>  
  
-   <span data-ttu-id="fb7cb-107">Her bir anahtar/değer çifti numaralandırması amacıyla öğedir.</span><span class="sxs-lookup"><span data-stu-id="fb7cb-107">Each element is a key/value pair for enumeration purposes.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="fb7cb-108">Nongeneric <xref:System.Collections.SortedList> sınıf döndürür <xref:System.Collections.DictionaryEntry> nesneleri numaralandırıldığı zaman dönüş iki genel türleri rağmen <xref:System.Collections.Generic.KeyValuePair%602> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="fb7cb-108">The nongeneric <xref:System.Collections.SortedList> class returns <xref:System.Collections.DictionaryEntry> objects when enumerated, although the two generic types return <xref:System.Collections.Generic.KeyValuePair%602> objects.</span></span>  
  
-   <span data-ttu-id="fb7cb-109">Öğeleri göre sıralanır bir <xref:System.Collections.IComparer?displayProperty=nameWithType> uygulaması (nongeneric için <xref:System.Collections.SortedList>) veya bir <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> (için iki genel sınıflar) uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="fb7cb-109">Elements are sorted according to a <xref:System.Collections.IComparer?displayProperty=nameWithType> implementation (for nongeneric <xref:System.Collections.SortedList>) or a <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> implementation (for the two generic classes).</span></span>  
  
-   <span data-ttu-id="fb7cb-110">Her sınıf yalnızca anahtarları ya da yalnızca değerleri içeren koleksiyonları döndüren özellikleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="fb7cb-110">Each class provides properties that return collections containing only the keys or only the values.</span></span>  
  
 <span data-ttu-id="fb7cb-111">Aşağıdaki tabloda iki sıralanmış sınıflar arasındaki farklılıklar listelenmiştir ve <xref:System.Collections.Generic.SortedDictionary%602> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="fb7cb-111">The following table lists some of the differences between the two sorted list classes and the <xref:System.Collections.Generic.SortedDictionary%602> class.</span></span>  
  
|<span data-ttu-id="fb7cb-112"><xref:System.Collections.SortedList>nongeneric sınıfı ve <xref:System.Collections.Generic.SortedList%602> genel sınıfı</span><span class="sxs-lookup"><span data-stu-id="fb7cb-112"><xref:System.Collections.SortedList> nongeneric class and <xref:System.Collections.Generic.SortedList%602> generic class</span></span>|<span data-ttu-id="fb7cb-113"><xref:System.Collections.Generic.SortedDictionary%602>Genel sınıfı</span><span class="sxs-lookup"><span data-stu-id="fb7cb-113"><xref:System.Collections.Generic.SortedDictionary%602> generic class</span></span>|  
|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<span data-ttu-id="fb7cb-114">Anahtarlar ve değerler döndüren özellikleri dizine, dizine alma verimli izin verme.</span><span class="sxs-lookup"><span data-stu-id="fb7cb-114">The properties that return keys and values are indexed, allowing efficient indexed retrieval.</span></span>|<span data-ttu-id="fb7cb-115">Dizinli alma yok.</span><span class="sxs-lookup"><span data-stu-id="fb7cb-115">No indexed retrieval.</span></span>|  
|<span data-ttu-id="fb7cb-116">Alma işlemi olan O (günlük `n`).</span><span class="sxs-lookup"><span data-stu-id="fb7cb-116">Retrieval is O(log `n`).</span></span>|<span data-ttu-id="fb7cb-117">Alma işlemi olan O (günlük `n`).</span><span class="sxs-lookup"><span data-stu-id="fb7cb-117">Retrieval is O(log `n`).</span></span>|  
|<span data-ttu-id="fb7cb-118">Ekleme ve kaldırma olan genellikle O (`n`); ancak, ekleme, O olduğu (günlük `n`) zaten adınız verileri sıralama düzeni, böylece her öğe listesinin sonuna eklenen için.</span><span class="sxs-lookup"><span data-stu-id="fb7cb-118">Insertion and removal are generally O(`n`); however, insertion is O(log `n`) for data that are already in sort order, so that each element is added to the end of the list.</span></span> <span data-ttu-id="fb7cb-119">(Bu, bir yeniden boyutlandırma gerekli olmadığını varsayar.)</span><span class="sxs-lookup"><span data-stu-id="fb7cb-119">(This assumes that a resize is not required.)</span></span>|<span data-ttu-id="fb7cb-120">Ekleme ve kaldırma olan O (günlük `n`).</span><span class="sxs-lookup"><span data-stu-id="fb7cb-120">Insertion and removal are O(log `n`).</span></span>|  
|<span data-ttu-id="fb7cb-121">Daha az bellek kullanır bir <xref:System.Collections.Generic.SortedDictionary%602>.</span><span class="sxs-lookup"><span data-stu-id="fb7cb-121">Uses less memory than a <xref:System.Collections.Generic.SortedDictionary%602>.</span></span>|<span data-ttu-id="fb7cb-122">Daha fazla bellek kullanılır <xref:System.Collections.SortedList> nongeneric sınıfı ve <xref:System.Collections.Generic.SortedList%602> genel bir sınıf.</span><span class="sxs-lookup"><span data-stu-id="fb7cb-122">Uses more memory than the <xref:System.Collections.SortedList> nongeneric class and the <xref:System.Collections.Generic.SortedList%602> generic class.</span></span>|  
  
 <span data-ttu-id="fb7cb-123">Sıralanmış listeleri veya aynı anda birden çok iş parçacığı tarafından erişilebilir olmalıdır sözlükler için sıralama mantığını türeyen bir sınıf ekleyebileceğiniz <xref:System.Collections.Concurrent.ConcurrentDictionary%602>.</span><span class="sxs-lookup"><span data-stu-id="fb7cb-123">For sorted lists or dictionaries that must be accessible concurrently from multiple threads, you can add sorting logic to a class that derives from <xref:System.Collections.Concurrent.ConcurrentDictionary%602>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fb7cb-124">Kendi anahtarları (çalışan kimlik numarası içeren Örneğin, çalışan kayıtları) içeren değerler için türetme tarafından listesini bazı özellikleri ve bir sözlük bazı özelliklerine sahip anahtarlı bir koleksiyon oluşturabilirsiniz <xref:System.Collections.ObjectModel.KeyedCollection%602> genel sınıf.</span><span class="sxs-lookup"><span data-stu-id="fb7cb-124">For values that contain their own keys (for example, employee records that contain an employee ID number), you can create a keyed collection that has some characteristics of a list and some characteristics of a dictionary by deriving from the <xref:System.Collections.ObjectModel.KeyedCollection%602> generic class.</span></span>  
  
 <span data-ttu-id="fb7cb-125">İle başlayarak [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], <xref:System.Collections.Generic.SortedSet%601> sınıfı eklemeler, silme ve aramaları sonra sıralanmış olarak verileri tutar Self karşı bir ağaç sağlar.</span><span class="sxs-lookup"><span data-stu-id="fb7cb-125">Starting with the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], the <xref:System.Collections.Generic.SortedSet%601> class provides a self-balancing tree that maintains data in sorted order after insertions, deletions, and searches.</span></span> <span data-ttu-id="fb7cb-126">Bu sınıf ve <xref:System.Collections.Generic.HashSet%601> sınıfı uygulama <xref:System.Collections.Generic.ISet%601> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="fb7cb-126">This class and the <xref:System.Collections.Generic.HashSet%601> class implement the <xref:System.Collections.Generic.ISet%601> interface.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb7cb-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fb7cb-127">See Also</span></span>  
 <xref:System.Collections.IDictionary?displayProperty=nameWithType>  
 <xref:System.Collections.Generic.IDictionary%602?displayProperty=nameWithType>  
 <xref:System.Collections.Concurrent.ConcurrentDictionary%602>  
 [<span data-ttu-id="fb7cb-128">Yaygın Olarak Kullanılan Koleksiyon Türleri</span><span class="sxs-lookup"><span data-stu-id="fb7cb-128">Commonly Used Collection Types</span></span>](../../../docs/standard/collections/commonly-used-collection-types.md)
