---
title: Grup sonuçları bitişik anahtarlara (C# üzerinde LINQ)
description: C# içinde LINQ kullanarak bitişik anahtarlara göre sonuçları gruplandırmak nasıl.
ms.date: 12/1/2016
ms.assetid: cbda9c08-151b-4c9e-82f7-c3d7f3dac66b
ms.openlocfilehash: 8ad08d861e2d0f5ee0f8a2eceeb8d82a9aa2a5a6
ms.sourcegitcommit: 4c158beee818c408d45a9609bfc06f209a523e22
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/03/2018
ms.locfileid: "37404768"
---
# <a name="group-results-by-contiguous-keys"></a><span data-ttu-id="99539-103">Grup sonuçları bitişik anahtarlara göre</span><span class="sxs-lookup"><span data-stu-id="99539-103">Group results by contiguous keys</span></span>

<span data-ttu-id="99539-104">Aşağıdaki örnek, bitişik anahtarların sıraları temsil eden öbeklere öğeleri gruplayın gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="99539-104">The following example shows how to group elements into chunks that represent subsequences of contiguous keys.</span></span> <span data-ttu-id="99539-105">Örneğin, aşağıdaki anahtar-değer çiftleri dizisi verilen varsayın:</span><span class="sxs-lookup"><span data-stu-id="99539-105">For example, assume that you are given the following sequence of key-value pairs:</span></span>

|<span data-ttu-id="99539-106">Anahtar</span><span class="sxs-lookup"><span data-stu-id="99539-106">Key</span></span>|<span data-ttu-id="99539-107">Değer</span><span class="sxs-lookup"><span data-stu-id="99539-107">Value</span></span>|
|---------|-----------|
|<span data-ttu-id="99539-108">BİR</span><span class="sxs-lookup"><span data-stu-id="99539-108">A</span></span>|<span data-ttu-id="99539-109">Biz</span><span class="sxs-lookup"><span data-stu-id="99539-109">We</span></span>|
|<span data-ttu-id="99539-110">BİR</span><span class="sxs-lookup"><span data-stu-id="99539-110">A</span></span>|<span data-ttu-id="99539-111">Düşünme</span><span class="sxs-lookup"><span data-stu-id="99539-111">think</span></span>|
|<span data-ttu-id="99539-112">BİR</span><span class="sxs-lookup"><span data-stu-id="99539-112">A</span></span>|<span data-ttu-id="99539-113">,</span><span class="sxs-lookup"><span data-stu-id="99539-113">that</span></span>|
|<span data-ttu-id="99539-114">B</span><span class="sxs-lookup"><span data-stu-id="99539-114">B</span></span>|<span data-ttu-id="99539-115">LINQ</span><span class="sxs-lookup"><span data-stu-id="99539-115">Linq</span></span>|
|<span data-ttu-id="99539-116">C</span><span class="sxs-lookup"><span data-stu-id="99539-116">C</span></span>|<span data-ttu-id="99539-117">is</span><span class="sxs-lookup"><span data-stu-id="99539-117">is</span></span>|
|<span data-ttu-id="99539-118">BİR</span><span class="sxs-lookup"><span data-stu-id="99539-118">A</span></span>|<span data-ttu-id="99539-119">gerçekten</span><span class="sxs-lookup"><span data-stu-id="99539-119">really</span></span>|
|<span data-ttu-id="99539-120">B</span><span class="sxs-lookup"><span data-stu-id="99539-120">B</span></span>|<span data-ttu-id="99539-121">seyrek erişimli</span><span class="sxs-lookup"><span data-stu-id="99539-121">cool</span></span>|
|<span data-ttu-id="99539-122">B</span><span class="sxs-lookup"><span data-stu-id="99539-122">B</span></span>|<span data-ttu-id="99539-123">!</span><span class="sxs-lookup"><span data-stu-id="99539-123">!</span></span>|

<span data-ttu-id="99539-124">Aşağıdaki gruplar bu sırayla oluşturulur:</span><span class="sxs-lookup"><span data-stu-id="99539-124">The following groups will be created in this order:</span></span>

1. <span data-ttu-id="99539-125">Düşünüyoruz,</span><span class="sxs-lookup"><span data-stu-id="99539-125">We, think, that</span></span>

2. <span data-ttu-id="99539-126">LINQ</span><span class="sxs-lookup"><span data-stu-id="99539-126">Linq</span></span>

3. <span data-ttu-id="99539-127">is</span><span class="sxs-lookup"><span data-stu-id="99539-127">is</span></span>

4. <span data-ttu-id="99539-128">gerçekten</span><span class="sxs-lookup"><span data-stu-id="99539-128">really</span></span>

5. <span data-ttu-id="99539-129">seyrek!</span><span class="sxs-lookup"><span data-stu-id="99539-129">cool, !</span></span>

<span data-ttu-id="99539-130">Çözüm, iş parçacığı açısından güvenli ve akıcı bir şekilde sonuçları döndüren bir genişletme yöntemi olarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="99539-130">The solution is implemented as an extension method that is thread-safe and that returns its results in a streaming manner.</span></span> <span data-ttu-id="99539-131">Diğer bir deyişle, kaynak sırası boyunca hareket ettikçe, grupları üretir.</span><span class="sxs-lookup"><span data-stu-id="99539-131">In other words, it produces its groups as it moves through the source sequence.</span></span> <span data-ttu-id="99539-132">Farklı `group` veya `orderby` operatörleri onu başlayabilir çağırana grupları döndüren tüm dizinin okumadan önce.</span><span class="sxs-lookup"><span data-stu-id="99539-132">Unlike the `group` or `orderby` operators, it can begin returning groups to the caller before all of the sequence has been read.</span></span>

<span data-ttu-id="99539-133">İş parçacığı güvenliği kaynak sırası yinelendiğinde gibi her bir grup veya öbek bir kopyasını kaynak kod yorumlar bölümünde açıklandığı gibi kullanılarak gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="99539-133">Thread-safety is accomplished by making a copy of each group or chunk as the source sequence is iterated, as explained in the source code comments.</span></span> <span data-ttu-id="99539-134">Kaynak sırası büyük bir dizi bitişik öğesi varsa, ortak dil çalışma zamanı oluşturabilecek bir <xref:System.OutOfMemoryException>.</span><span class="sxs-lookup"><span data-stu-id="99539-134">If the source sequence has a large sequence of contiguous items, the common language runtime may throw an <xref:System.OutOfMemoryException>.</span></span>

## <a name="example"></a><span data-ttu-id="99539-135">Örnek</span><span class="sxs-lookup"><span data-stu-id="99539-135">Example</span></span>

<span data-ttu-id="99539-136">Aşağıdaki örnek, hem genişletme yöntemi hem de onu kullanan istemci kodu gösterir:</span><span class="sxs-lookup"><span data-stu-id="99539-136">The following example shows both the extension method and the client code that uses it:</span></span>

[!code-csharp[cscsrefContiguousGroups#1](~/samples/snippets/csharp/concepts/linq/how-to-group-results-by-contiguous-keys_1.cs)]

<span data-ttu-id="99539-137">Projenizde genişletme yöntemini kullanmak için kopyalayın `MyExtensions` statik sınıf için yeni veya mevcut bir kaynak kod dosyası ve, gerekirse ekleme bir `using` bulunduğu olduğu ad alanı için yönerge.</span><span class="sxs-lookup"><span data-stu-id="99539-137">To use the extension method in your project, copy the `MyExtensions` static class to a new or existing source code file and if it is required, add a `using` directive for the namespace where it is located.</span></span>

## <a name="see-also"></a><span data-ttu-id="99539-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="99539-138">See also</span></span>

[<span data-ttu-id="99539-139">Dil ile Tümleşik Sorgu (LINQ)</span><span class="sxs-lookup"><span data-stu-id="99539-139">Language Integrated Query (LINQ)</span></span>](index.md)