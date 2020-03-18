---
title: Sonuçları bitişik tuşlara göre gruplandırma (C#'da LINQ)
description: C#'da LINQ kullanarak bitişik tuşlarla sonuçları nasıl gruplandırmak.
ms.date: 08/14/2018
ms.assetid: cbda9c08-151b-4c9e-82f7-c3d7f3dac66b
ms.openlocfilehash: b5753c85bb07be4fc84b78a299eece961969ff9d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "61659910"
---
# <a name="group-results-by-contiguous-keys"></a><span data-ttu-id="79095-103">Sonuçları bitişik anahtarlara göre gruplama</span><span class="sxs-lookup"><span data-stu-id="79095-103">Group results by contiguous keys</span></span>

<span data-ttu-id="79095-104">Aşağıdaki örnek, öğeleri bitişik anahtarların alt dizilerini temsil eden parçalar halinde nasıl gruplanır gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="79095-104">The following example shows how to group elements into chunks that represent subsequences of contiguous keys.</span></span> <span data-ttu-id="79095-105">Örneğin, size aşağıdaki anahtar değeri çiftleri sırasının verildiğini varsayalım:</span><span class="sxs-lookup"><span data-stu-id="79095-105">For example, assume that you are given the following sequence of key-value pairs:</span></span>

|<span data-ttu-id="79095-106">Anahtar</span><span class="sxs-lookup"><span data-stu-id="79095-106">Key</span></span>|<span data-ttu-id="79095-107">Değer</span><span class="sxs-lookup"><span data-stu-id="79095-107">Value</span></span>|
|---------|-----------|
|<span data-ttu-id="79095-108">A</span><span class="sxs-lookup"><span data-stu-id="79095-108">A</span></span>|<span data-ttu-id="79095-109">Biz</span><span class="sxs-lookup"><span data-stu-id="79095-109">We</span></span>|
|<span data-ttu-id="79095-110">A</span><span class="sxs-lookup"><span data-stu-id="79095-110">A</span></span>|<span data-ttu-id="79095-111">Düşünü</span><span class="sxs-lookup"><span data-stu-id="79095-111">think</span></span>|
|<span data-ttu-id="79095-112">A</span><span class="sxs-lookup"><span data-stu-id="79095-112">A</span></span>|<span data-ttu-id="79095-113">bu</span><span class="sxs-lookup"><span data-stu-id="79095-113">that</span></span>|
|<span data-ttu-id="79095-114">B</span><span class="sxs-lookup"><span data-stu-id="79095-114">B</span></span>|<span data-ttu-id="79095-115">Lınq</span><span class="sxs-lookup"><span data-stu-id="79095-115">Linq</span></span>|
|<span data-ttu-id="79095-116">C</span><span class="sxs-lookup"><span data-stu-id="79095-116">C</span></span>|<span data-ttu-id="79095-117">is</span><span class="sxs-lookup"><span data-stu-id="79095-117">is</span></span>|
|<span data-ttu-id="79095-118">A</span><span class="sxs-lookup"><span data-stu-id="79095-118">A</span></span>|<span data-ttu-id="79095-119">Gerçek -ten</span><span class="sxs-lookup"><span data-stu-id="79095-119">really</span></span>|
|<span data-ttu-id="79095-120">B</span><span class="sxs-lookup"><span data-stu-id="79095-120">B</span></span>|<span data-ttu-id="79095-121">Serin</span><span class="sxs-lookup"><span data-stu-id="79095-121">cool</span></span>|
|<span data-ttu-id="79095-122">B</span><span class="sxs-lookup"><span data-stu-id="79095-122">B</span></span>|<span data-ttu-id="79095-123">!</span><span class="sxs-lookup"><span data-stu-id="79095-123">!</span></span>|

<span data-ttu-id="79095-124">Aşağıdaki gruplar bu sırada oluşturulur:</span><span class="sxs-lookup"><span data-stu-id="79095-124">The following groups will be created in this order:</span></span>

1. <span data-ttu-id="79095-125">Biz, düşünüyorum, bu</span><span class="sxs-lookup"><span data-stu-id="79095-125">We, think, that</span></span>

2. <span data-ttu-id="79095-126">Lınq</span><span class="sxs-lookup"><span data-stu-id="79095-126">Linq</span></span>

3. <span data-ttu-id="79095-127">is</span><span class="sxs-lookup"><span data-stu-id="79095-127">is</span></span>

4. <span data-ttu-id="79095-128">Gerçek -ten</span><span class="sxs-lookup"><span data-stu-id="79095-128">really</span></span>

5. <span data-ttu-id="79095-129">Serin!</span><span class="sxs-lookup"><span data-stu-id="79095-129">cool, !</span></span>

<span data-ttu-id="79095-130">Çözüm, iş parçacığı güvenli ve sonuçlarını akışlı bir şekilde döndüren bir uzantı yöntemi olarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="79095-130">The solution is implemented as an extension method that is thread-safe and that returns its results in a streaming manner.</span></span> <span data-ttu-id="79095-131">Başka bir deyişle, kaynak sırayla hareket ederken gruplarını üretir.</span><span class="sxs-lookup"><span data-stu-id="79095-131">In other words, it produces its groups as it moves through the source sequence.</span></span> <span data-ttu-id="79095-132">Veya `group` `orderby` işleçlerin aksine, tüm sıra okunmadan önce grupları arayanın anına döndürmeye başlayabilir.</span><span class="sxs-lookup"><span data-stu-id="79095-132">Unlike the `group` or `orderby` operators, it can begin returning groups to the caller before all of the sequence has been read.</span></span>

<span data-ttu-id="79095-133">Konu güvenliği, kaynak kod yorumlarında açıklandığı gibi, kaynak sırası yinelenirken her grubun veya yığının bir kopyasını oluşturarak gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="79095-133">Thread-safety is accomplished by making a copy of each group or chunk as the source sequence is iterated, as explained in the source code comments.</span></span> <span data-ttu-id="79095-134">Kaynak sıranın büyük bir bitişik öğe sırası varsa, ortak dil <xref:System.OutOfMemoryException>çalışma süresi bir .</span><span class="sxs-lookup"><span data-stu-id="79095-134">If the source sequence has a large sequence of contiguous items, the common language runtime may throw an <xref:System.OutOfMemoryException>.</span></span>

## <a name="example"></a><span data-ttu-id="79095-135">Örnek</span><span class="sxs-lookup"><span data-stu-id="79095-135">Example</span></span>

<span data-ttu-id="79095-136">Aşağıdaki örnek, hem uzantı yöntemini hem de onu kullanan istemci kodunu gösterir:</span><span class="sxs-lookup"><span data-stu-id="79095-136">The following example shows both the extension method and the client code that uses it:</span></span>

[!code-csharp[cscsrefContiguousGroups#1](~/samples/snippets/csharp/concepts/linq/how-to-group-results-by-contiguous-keys_1.cs)]

<span data-ttu-id="79095-137">Projenizdeki uzantı yöntemini kullanmak `MyExtensions` için statik sınıfı yeni veya varolan kaynak kodu dosyasına kopyalayın ve gerekirse bulunduğu ad alanı için bir `using` yönerge ekleyin.</span><span class="sxs-lookup"><span data-stu-id="79095-137">To use the extension method in your project, copy the `MyExtensions` static class to a new or existing source code file and if it is required, add a `using` directive for the namespace where it is located.</span></span>

## <a name="see-also"></a><span data-ttu-id="79095-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="79095-138">See also</span></span>

- [<span data-ttu-id="79095-139">Dil ile Tümleşik Sorgu (LINQ)</span><span class="sxs-lookup"><span data-stu-id="79095-139">Language Integrated Query (LINQ)</span></span>](index.md)
