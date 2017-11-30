---
title: "Grup sonuçları bitişik anahtarlara göre"
description: "Nasıl Grup sonuçları bitişik anahtarlara göre yapılır."
keywords: .NET, .NET core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.assetid: cbda9c08-151b-4c9e-82f7-c3d7f3dac66b
ms.openlocfilehash: cdd06a6fad037291bbc5aa011b47bb668fa2f062
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="group-results-by-contiguous-keys"></a><span data-ttu-id="77fe5-104">Grup sonuçları bitişik anahtarlara göre</span><span class="sxs-lookup"><span data-stu-id="77fe5-104">Group results by contiguous keys</span></span>

<span data-ttu-id="77fe5-105">Aşağıdaki örnek, bitişik anahtarlara sıraları temsil eden parçalara öğeleri gruplandırmak gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="77fe5-105">The following example shows how to group elements into chunks that represent subsequences of contiguous keys.</span></span> <span data-ttu-id="77fe5-106">Örneğin, aşağıdaki anahtar-değer çiftleri dizisi verildiğini varsayın:</span><span class="sxs-lookup"><span data-stu-id="77fe5-106">For example, assume that you are given the following sequence of key-value pairs:</span></span>  
  
|<span data-ttu-id="77fe5-107">Anahtar</span><span class="sxs-lookup"><span data-stu-id="77fe5-107">Key</span></span>|<span data-ttu-id="77fe5-108">Değer</span><span class="sxs-lookup"><span data-stu-id="77fe5-108">Value</span></span>|  
|---------|-----------|  
|<span data-ttu-id="77fe5-109">BİR</span><span class="sxs-lookup"><span data-stu-id="77fe5-109">A</span></span>|<span data-ttu-id="77fe5-110">Biz</span><span class="sxs-lookup"><span data-stu-id="77fe5-110">We</span></span>|  
|<span data-ttu-id="77fe5-111">BİR</span><span class="sxs-lookup"><span data-stu-id="77fe5-111">A</span></span>|<span data-ttu-id="77fe5-112">Düşünme</span><span class="sxs-lookup"><span data-stu-id="77fe5-112">think</span></span>|  
|<span data-ttu-id="77fe5-113">BİR</span><span class="sxs-lookup"><span data-stu-id="77fe5-113">A</span></span>|<span data-ttu-id="77fe5-114">,</span><span class="sxs-lookup"><span data-stu-id="77fe5-114">that</span></span>|  
|<span data-ttu-id="77fe5-115">B</span><span class="sxs-lookup"><span data-stu-id="77fe5-115">B</span></span>|<span data-ttu-id="77fe5-116">LINQ</span><span class="sxs-lookup"><span data-stu-id="77fe5-116">Linq</span></span>|  
|<span data-ttu-id="77fe5-117">C</span><span class="sxs-lookup"><span data-stu-id="77fe5-117">C</span></span>|<span data-ttu-id="77fe5-118">is</span><span class="sxs-lookup"><span data-stu-id="77fe5-118">is</span></span>|  
|<span data-ttu-id="77fe5-119">BİR</span><span class="sxs-lookup"><span data-stu-id="77fe5-119">A</span></span>|<span data-ttu-id="77fe5-120">gerçekten</span><span class="sxs-lookup"><span data-stu-id="77fe5-120">really</span></span>|  
|<span data-ttu-id="77fe5-121">B</span><span class="sxs-lookup"><span data-stu-id="77fe5-121">B</span></span>|<span data-ttu-id="77fe5-122">Seyrek erişimli</span><span class="sxs-lookup"><span data-stu-id="77fe5-122">cool</span></span>|  
|<span data-ttu-id="77fe5-123">B</span><span class="sxs-lookup"><span data-stu-id="77fe5-123">B</span></span>|<span data-ttu-id="77fe5-124">!</span><span class="sxs-lookup"><span data-stu-id="77fe5-124">!</span></span>|  
  
 <span data-ttu-id="77fe5-125">Bu sırada aşağıdaki grupları oluşturulur:</span><span class="sxs-lookup"><span data-stu-id="77fe5-125">The following groups will be created in this order:</span></span>  
  
1.  <span data-ttu-id="77fe5-126">Düşünüyoruz,</span><span class="sxs-lookup"><span data-stu-id="77fe5-126">We, think, that</span></span>  
  
2.  <span data-ttu-id="77fe5-127">LINQ</span><span class="sxs-lookup"><span data-stu-id="77fe5-127">Linq</span></span>  
  
3.  <span data-ttu-id="77fe5-128">is</span><span class="sxs-lookup"><span data-stu-id="77fe5-128">is</span></span>  
  
4.  <span data-ttu-id="77fe5-129">gerçekten</span><span class="sxs-lookup"><span data-stu-id="77fe5-129">really</span></span>  
  
5.  <span data-ttu-id="77fe5-130">Cool!</span><span class="sxs-lookup"><span data-stu-id="77fe5-130">cool, !</span></span>  
  
 <span data-ttu-id="77fe5-131">Çözüm, iş parçacığı açısından güvenli olan ve bir akış şekilde sonuçları döndüren bir genişletme yöntemi olarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="77fe5-131">The solution is implemented as an extension method that is thread-safe and that returns its results in a streaming manner.</span></span> <span data-ttu-id="77fe5-132">Diğer bir deyişle, kaynak sırası hareket ederken, grupları oluşturur.</span><span class="sxs-lookup"><span data-stu-id="77fe5-132">In other words, it produces its groups as it moves through the source sequence.</span></span> <span data-ttu-id="77fe5-133">Farklı `group` veya `orderby` operatörleri onu başlayabilir çağırana grupları döndüren dizisi tümüne okumadan önce.</span><span class="sxs-lookup"><span data-stu-id="77fe5-133">Unlike the `group` or `orderby` operators, it can begin returning groups to the caller before all of the sequence has been read.</span></span>  
  
 <span data-ttu-id="77fe5-134">İş parçacığı güvenliği kaynak sıradaki yinelendiğinde gibi her bir grup veya öbek bir kopyasını kaynak kodu açıklamaları açıklandığı gibi sağlayarak gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="77fe5-134">Thread-safety is accomplished by making a copy of each group or chunk as the source sequence is iterated, as explained in the source code comments.</span></span> <span data-ttu-id="77fe5-135">Kaynak sırası büyük dizi bitişik öğesi içeriyorsa, ortak dil çalışma zamanı atabilir bir <xref:System.OutOfMemoryException>.</span><span class="sxs-lookup"><span data-stu-id="77fe5-135">If the source sequence has a large sequence of contiguous items, the common language runtime may throw an <xref:System.OutOfMemoryException>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="77fe5-136">Örnek</span><span class="sxs-lookup"><span data-stu-id="77fe5-136">Example</span></span>  
 <span data-ttu-id="77fe5-137">Aşağıdaki örnek, genişletme yöntemi ve onu kullanan istemci kodu gösterir.</span><span class="sxs-lookup"><span data-stu-id="77fe5-137">The following example shows both the extension method and the client code that uses it.</span></span>  
  
 [!code-csharp[cscsrefContiguousGroups#1](../../../samples/snippets/csharp/concepts/linq/how-to-group-results-by-contiguous-keys_1.cs)]  
  
 <span data-ttu-id="77fe5-138">Projenizde genişletme yöntemi kullanmak için kopyalayın `MyExtensions` yeni veya var olan bir kaynak için statik sınıf kod dosyası ve gerekli ise ekleyin bir `using` bulunduğu olduğu ad alanı için yönerge.</span><span class="sxs-lookup"><span data-stu-id="77fe5-138">To use the extension method in your project, copy the `MyExtensions` static class to a new or existing source code file and if it is required, add a `using` directive for the namespace where it is located.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77fe5-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="77fe5-139">See also</span></span>  
 [<span data-ttu-id="77fe5-140">LINQ Sorgu ifadeleri</span><span class="sxs-lookup"><span data-stu-id="77fe5-140">LINQ Query Expressions</span></span>](index.md)  
 
