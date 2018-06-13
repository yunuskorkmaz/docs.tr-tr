---
title: Grup sonuçları bitişik anahtarlara göre
description: Nasıl Grup sonuçları bitişik anahtarlara göre yapılır.
ms.date: 12/1/2016
ms.assetid: cbda9c08-151b-4c9e-82f7-c3d7f3dac66b
ms.openlocfilehash: a8d6ac133932a12154d5b23454065144c7652067
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33281443"
---
# <a name="group-results-by-contiguous-keys"></a><span data-ttu-id="fd58e-103">Grup sonuçları bitişik anahtarlara göre</span><span class="sxs-lookup"><span data-stu-id="fd58e-103">Group results by contiguous keys</span></span>

<span data-ttu-id="fd58e-104">Aşağıdaki örnek, bitişik anahtarlara sıraları temsil eden parçalara öğeleri gruplandırmak gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="fd58e-104">The following example shows how to group elements into chunks that represent subsequences of contiguous keys.</span></span> <span data-ttu-id="fd58e-105">Örneğin, aşağıdaki anahtar-değer çiftleri dizisi verildiğini varsayın:</span><span class="sxs-lookup"><span data-stu-id="fd58e-105">For example, assume that you are given the following sequence of key-value pairs:</span></span>  
  
|<span data-ttu-id="fd58e-106">Anahtar</span><span class="sxs-lookup"><span data-stu-id="fd58e-106">Key</span></span>|<span data-ttu-id="fd58e-107">Değer</span><span class="sxs-lookup"><span data-stu-id="fd58e-107">Value</span></span>|  
|---------|-----------|  
|<span data-ttu-id="fd58e-108">BİR</span><span class="sxs-lookup"><span data-stu-id="fd58e-108">A</span></span>|<span data-ttu-id="fd58e-109">Biz</span><span class="sxs-lookup"><span data-stu-id="fd58e-109">We</span></span>|  
|<span data-ttu-id="fd58e-110">BİR</span><span class="sxs-lookup"><span data-stu-id="fd58e-110">A</span></span>|<span data-ttu-id="fd58e-111">Düşünme</span><span class="sxs-lookup"><span data-stu-id="fd58e-111">think</span></span>|  
|<span data-ttu-id="fd58e-112">BİR</span><span class="sxs-lookup"><span data-stu-id="fd58e-112">A</span></span>|<span data-ttu-id="fd58e-113">,</span><span class="sxs-lookup"><span data-stu-id="fd58e-113">that</span></span>|  
|<span data-ttu-id="fd58e-114">B</span><span class="sxs-lookup"><span data-stu-id="fd58e-114">B</span></span>|<span data-ttu-id="fd58e-115">LINQ</span><span class="sxs-lookup"><span data-stu-id="fd58e-115">Linq</span></span>|  
|<span data-ttu-id="fd58e-116">C</span><span class="sxs-lookup"><span data-stu-id="fd58e-116">C</span></span>|<span data-ttu-id="fd58e-117">is</span><span class="sxs-lookup"><span data-stu-id="fd58e-117">is</span></span>|  
|<span data-ttu-id="fd58e-118">BİR</span><span class="sxs-lookup"><span data-stu-id="fd58e-118">A</span></span>|<span data-ttu-id="fd58e-119">gerçekten</span><span class="sxs-lookup"><span data-stu-id="fd58e-119">really</span></span>|  
|<span data-ttu-id="fd58e-120">B</span><span class="sxs-lookup"><span data-stu-id="fd58e-120">B</span></span>|<span data-ttu-id="fd58e-121">Seyrek erişimli</span><span class="sxs-lookup"><span data-stu-id="fd58e-121">cool</span></span>|  
|<span data-ttu-id="fd58e-122">B</span><span class="sxs-lookup"><span data-stu-id="fd58e-122">B</span></span>|<span data-ttu-id="fd58e-123">!</span><span class="sxs-lookup"><span data-stu-id="fd58e-123">!</span></span>|  
  
 <span data-ttu-id="fd58e-124">Bu sırada aşağıdaki grupları oluşturulur:</span><span class="sxs-lookup"><span data-stu-id="fd58e-124">The following groups will be created in this order:</span></span>  
  
1.  <span data-ttu-id="fd58e-125">Düşünüyoruz,</span><span class="sxs-lookup"><span data-stu-id="fd58e-125">We, think, that</span></span>  
  
2.  <span data-ttu-id="fd58e-126">LINQ</span><span class="sxs-lookup"><span data-stu-id="fd58e-126">Linq</span></span>  
  
3.  <span data-ttu-id="fd58e-127">is</span><span class="sxs-lookup"><span data-stu-id="fd58e-127">is</span></span>  
  
4.  <span data-ttu-id="fd58e-128">gerçekten</span><span class="sxs-lookup"><span data-stu-id="fd58e-128">really</span></span>  
  
5.  <span data-ttu-id="fd58e-129">Cool!</span><span class="sxs-lookup"><span data-stu-id="fd58e-129">cool, !</span></span>  
  
 <span data-ttu-id="fd58e-130">Çözüm, iş parçacığı açısından güvenli olan ve bir akış şekilde sonuçları döndüren bir genişletme yöntemi olarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="fd58e-130">The solution is implemented as an extension method that is thread-safe and that returns its results in a streaming manner.</span></span> <span data-ttu-id="fd58e-131">Diğer bir deyişle, kaynak sırası hareket ederken, grupları oluşturur.</span><span class="sxs-lookup"><span data-stu-id="fd58e-131">In other words, it produces its groups as it moves through the source sequence.</span></span> <span data-ttu-id="fd58e-132">Farklı `group` veya `orderby` operatörleri onu başlayabilir çağırana grupları döndüren dizisi tümüne okumadan önce.</span><span class="sxs-lookup"><span data-stu-id="fd58e-132">Unlike the `group` or `orderby` operators, it can begin returning groups to the caller before all of the sequence has been read.</span></span>  
  
 <span data-ttu-id="fd58e-133">İş parçacığı güvenliği kaynak sıradaki yinelendiğinde gibi her bir grup veya öbek bir kopyasını kaynak kodu açıklamaları açıklandığı gibi sağlayarak gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="fd58e-133">Thread-safety is accomplished by making a copy of each group or chunk as the source sequence is iterated, as explained in the source code comments.</span></span> <span data-ttu-id="fd58e-134">Kaynak sırası büyük dizi bitişik öğesi içeriyorsa, ortak dil çalışma zamanı atabilir bir <xref:System.OutOfMemoryException>.</span><span class="sxs-lookup"><span data-stu-id="fd58e-134">If the source sequence has a large sequence of contiguous items, the common language runtime may throw an <xref:System.OutOfMemoryException>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fd58e-135">Örnek</span><span class="sxs-lookup"><span data-stu-id="fd58e-135">Example</span></span>  
 <span data-ttu-id="fd58e-136">Aşağıdaki örnek, genişletme yöntemi ve onu kullanan istemci kodu gösterir.</span><span class="sxs-lookup"><span data-stu-id="fd58e-136">The following example shows both the extension method and the client code that uses it.</span></span>  
  
 [!code-csharp[cscsrefContiguousGroups#1](../../../samples/snippets/csharp/concepts/linq/how-to-group-results-by-contiguous-keys_1.cs)]  
  
 <span data-ttu-id="fd58e-137">Projenizde genişletme yöntemi kullanmak için kopyalayın `MyExtensions` yeni veya var olan bir kaynak için statik sınıf kod dosyası ve gerekli ise ekleyin bir `using` bulunduğu olduğu ad alanı için yönerge.</span><span class="sxs-lookup"><span data-stu-id="fd58e-137">To use the extension method in your project, copy the `MyExtensions` static class to a new or existing source code file and if it is required, add a `using` directive for the namespace where it is located.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd58e-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fd58e-138">See also</span></span>  
 [<span data-ttu-id="fd58e-139">LINQ Sorgu ifadeleri</span><span class="sxs-lookup"><span data-stu-id="fd58e-139">LINQ Query Expressions</span></span>](index.md)  
 
