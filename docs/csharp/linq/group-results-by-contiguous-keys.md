---
title: Grup sonuçları bitişik anahtarlara (C# üzerinde LINQ)
description: C# içinde LINQ kullanarak bitişik anahtarlara göre sonuçları gruplandırmak nasıl.
ms.date: 08/14/2018
ms.assetid: cbda9c08-151b-4c9e-82f7-c3d7f3dac66b
ms.openlocfilehash: b5753c85bb07be4fc84b78a299eece961969ff9d
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/03/2018
ms.locfileid: "43484008"
---
# <a name="group-results-by-contiguous-keys"></a><span data-ttu-id="05fc2-103">Grup sonuçları bitişik anahtarlara göre</span><span class="sxs-lookup"><span data-stu-id="05fc2-103">Group results by contiguous keys</span></span>

<span data-ttu-id="05fc2-104">Aşağıdaki örnek, bitişik anahtarların sıraları temsil eden öbeklere öğeleri gruplayın gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="05fc2-104">The following example shows how to group elements into chunks that represent subsequences of contiguous keys.</span></span> <span data-ttu-id="05fc2-105">Örneğin, aşağıdaki anahtar-değer çiftleri dizisi verilen varsayın:</span><span class="sxs-lookup"><span data-stu-id="05fc2-105">For example, assume that you are given the following sequence of key-value pairs:</span></span>

|<span data-ttu-id="05fc2-106">Anahtar</span><span class="sxs-lookup"><span data-stu-id="05fc2-106">Key</span></span>|<span data-ttu-id="05fc2-107">Değer</span><span class="sxs-lookup"><span data-stu-id="05fc2-107">Value</span></span>|
|---------|-----------|
|<span data-ttu-id="05fc2-108">BİR</span><span class="sxs-lookup"><span data-stu-id="05fc2-108">A</span></span>|<span data-ttu-id="05fc2-109">Biz</span><span class="sxs-lookup"><span data-stu-id="05fc2-109">We</span></span>|
|<span data-ttu-id="05fc2-110">BİR</span><span class="sxs-lookup"><span data-stu-id="05fc2-110">A</span></span>|<span data-ttu-id="05fc2-111">Düşünme</span><span class="sxs-lookup"><span data-stu-id="05fc2-111">think</span></span>|
|<span data-ttu-id="05fc2-112">BİR</span><span class="sxs-lookup"><span data-stu-id="05fc2-112">A</span></span>|<span data-ttu-id="05fc2-113">,</span><span class="sxs-lookup"><span data-stu-id="05fc2-113">that</span></span>|
|<span data-ttu-id="05fc2-114">B</span><span class="sxs-lookup"><span data-stu-id="05fc2-114">B</span></span>|<span data-ttu-id="05fc2-115">LINQ</span><span class="sxs-lookup"><span data-stu-id="05fc2-115">Linq</span></span>|
|<span data-ttu-id="05fc2-116">C</span><span class="sxs-lookup"><span data-stu-id="05fc2-116">C</span></span>|<span data-ttu-id="05fc2-117">is</span><span class="sxs-lookup"><span data-stu-id="05fc2-117">is</span></span>|
|<span data-ttu-id="05fc2-118">BİR</span><span class="sxs-lookup"><span data-stu-id="05fc2-118">A</span></span>|<span data-ttu-id="05fc2-119">gerçekten</span><span class="sxs-lookup"><span data-stu-id="05fc2-119">really</span></span>|
|<span data-ttu-id="05fc2-120">B</span><span class="sxs-lookup"><span data-stu-id="05fc2-120">B</span></span>|<span data-ttu-id="05fc2-121">seyrek erişimli</span><span class="sxs-lookup"><span data-stu-id="05fc2-121">cool</span></span>|
|<span data-ttu-id="05fc2-122">B</span><span class="sxs-lookup"><span data-stu-id="05fc2-122">B</span></span>|<span data-ttu-id="05fc2-123">!</span><span class="sxs-lookup"><span data-stu-id="05fc2-123">!</span></span>|

<span data-ttu-id="05fc2-124">Aşağıdaki gruplar bu sırayla oluşturulur:</span><span class="sxs-lookup"><span data-stu-id="05fc2-124">The following groups will be created in this order:</span></span>

1. <span data-ttu-id="05fc2-125">Düşünüyoruz,</span><span class="sxs-lookup"><span data-stu-id="05fc2-125">We, think, that</span></span>

2. <span data-ttu-id="05fc2-126">LINQ</span><span class="sxs-lookup"><span data-stu-id="05fc2-126">Linq</span></span>

3. <span data-ttu-id="05fc2-127">is</span><span class="sxs-lookup"><span data-stu-id="05fc2-127">is</span></span>

4. <span data-ttu-id="05fc2-128">gerçekten</span><span class="sxs-lookup"><span data-stu-id="05fc2-128">really</span></span>

5. <span data-ttu-id="05fc2-129">seyrek!</span><span class="sxs-lookup"><span data-stu-id="05fc2-129">cool, !</span></span>

<span data-ttu-id="05fc2-130">Çözüm, iş parçacığı açısından güvenli ve akıcı bir şekilde sonuçları döndüren bir genişletme yöntemi olarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="05fc2-130">The solution is implemented as an extension method that is thread-safe and that returns its results in a streaming manner.</span></span> <span data-ttu-id="05fc2-131">Diğer bir deyişle, kaynak sırası boyunca hareket ettikçe, grupları üretir.</span><span class="sxs-lookup"><span data-stu-id="05fc2-131">In other words, it produces its groups as it moves through the source sequence.</span></span> <span data-ttu-id="05fc2-132">Farklı `group` veya `orderby` operatörleri onu başlayabilir çağırana grupları döndüren tüm dizinin okumadan önce.</span><span class="sxs-lookup"><span data-stu-id="05fc2-132">Unlike the `group` or `orderby` operators, it can begin returning groups to the caller before all of the sequence has been read.</span></span>

<span data-ttu-id="05fc2-133">İş parçacığı güvenliği kaynak sırası yinelendiğinde gibi her bir grup veya öbek bir kopyasını kaynak kod yorumlar bölümünde açıklandığı gibi kullanılarak gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="05fc2-133">Thread-safety is accomplished by making a copy of each group or chunk as the source sequence is iterated, as explained in the source code comments.</span></span> <span data-ttu-id="05fc2-134">Kaynak sırası büyük bir dizi bitişik öğesi varsa, ortak dil çalışma zamanı oluşturabilecek bir <xref:System.OutOfMemoryException>.</span><span class="sxs-lookup"><span data-stu-id="05fc2-134">If the source sequence has a large sequence of contiguous items, the common language runtime may throw an <xref:System.OutOfMemoryException>.</span></span>

## <a name="example"></a><span data-ttu-id="05fc2-135">Örnek</span><span class="sxs-lookup"><span data-stu-id="05fc2-135">Example</span></span>

<span data-ttu-id="05fc2-136">Aşağıdaki örnek, hem genişletme yöntemi hem de onu kullanan istemci kodu gösterir:</span><span class="sxs-lookup"><span data-stu-id="05fc2-136">The following example shows both the extension method and the client code that uses it:</span></span>

[!code-csharp[cscsrefContiguousGroups#1](~/samples/snippets/csharp/concepts/linq/how-to-group-results-by-contiguous-keys_1.cs)]

<span data-ttu-id="05fc2-137">Projenizde genişletme yöntemini kullanmak için kopyalayın `MyExtensions` statik sınıf için yeni veya mevcut bir kaynak kod dosyası ve, gerekirse ekleme bir `using` bulunduğu olduğu ad alanı için yönerge.</span><span class="sxs-lookup"><span data-stu-id="05fc2-137">To use the extension method in your project, copy the `MyExtensions` static class to a new or existing source code file and if it is required, add a `using` directive for the namespace where it is located.</span></span>

## <a name="see-also"></a><span data-ttu-id="05fc2-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="05fc2-138">See also</span></span>

- [<span data-ttu-id="05fc2-139">Dil ile Tümleşik Sorgu (LINQ)</span><span class="sxs-lookup"><span data-stu-id="05fc2-139">Language Integrated Query (LINQ)</span></span>](index.md)
