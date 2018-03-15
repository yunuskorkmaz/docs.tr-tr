---
title: "C# yapılar - C# dili turu"
description: "C# temelleri yapılar adlı türleri, değer öğrenin"
keywords: ".NET, C#, yapısı, değer türü"
author: BillWagner
ms.author: wiwagn
ms.date: 08/10/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 88a74571-f741-4a31-a2b5-1ccf165535b8
ms.openlocfilehash: fa840d80bba98889f75863db2612f196d78bd3c5
ms.sourcegitcommit: 83dd5ec003e788ccb3e33f3412a7af39ae347646
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2018
---
# <a name="structs"></a><span data-ttu-id="c5df9-104">Yapılar</span><span class="sxs-lookup"><span data-stu-id="c5df9-104">Structs</span></span>

<span data-ttu-id="c5df9-105">Sınıfları, ister ***yapılar*** veri üyeleri ve işlev üyeleri içerebilir veri yapılarını, ancak farklı sınıflar, yapılar değer türleri ve yığın ayırma gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="c5df9-105">Like classes, ***structs*** are data structures that can contain data members and function members, but unlike classes, structs are value types and do not require heap allocation.</span></span> <span data-ttu-id="c5df9-106">Sınıf türü bir değişken dinamik olarak ayrılan bir nesneye başvuru depoladığı bir yapı türünde bir değişken doğrudan yapısı veri depolar.</span><span class="sxs-lookup"><span data-stu-id="c5df9-106">A variable of a struct type directly stores the data of the struct, whereas a variable of a class type stores a reference to a dynamically allocated object.</span></span> <span data-ttu-id="c5df9-107">Struct türleri, kullanıcı tarafından belirtilen devralma desteklemez ve tüm yapı türleri örtük olarak türünden devralan <xref:System.ValueType>, hangi de örtük olarak Aç devraldığı `object`.</span><span class="sxs-lookup"><span data-stu-id="c5df9-107">Struct types do not support user-specified inheritance, and all struct types implicitly inherit from type <xref:System.ValueType>, which in turn implicitly inherits from `object`.</span></span>

<span data-ttu-id="c5df9-108">Yapılar değer semantiklerine sahip küçük veri yapıları için özellikle yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="c5df9-108">Structs are particularly useful for small data structures that have value semantics.</span></span> <span data-ttu-id="c5df9-109">Karmaşık numaralar, koordinat sistemi noktaları veya anahtar-değer çiftleri sözlükteki tüm iyi yapılar gösterilebilir.</span><span class="sxs-lookup"><span data-stu-id="c5df9-109">Complex numbers, points in a coordinate system, or key-value pairs in a dictionary are all good examples of structs.</span></span> <span data-ttu-id="c5df9-110">Küçük veri yapıları için sınıflar, bir uygulama bellek ayırmaları sayısı büyük bir fark yaratabilir yerine yapılar kullanımını gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="c5df9-110">The use of structs rather than classes for small data structures can make a large difference in the number of memory allocations an application performs.</span></span> <span data-ttu-id="c5df9-111">Örneğin, aşağıdaki programı oluşturur ve 100 puan dizisini başlatır.</span><span class="sxs-lookup"><span data-stu-id="c5df9-111">For example, the following program creates and initializes an array of 100 points.</span></span> <span data-ttu-id="c5df9-112">İle `Point` bir sınıf olarak uygulanan, 101 ayrı nesneler örneği oluşturulmadan — bir dizi ve her biri için 100 öğeleri için.</span><span class="sxs-lookup"><span data-stu-id="c5df9-112">With `Point` implemented as a class, 101 separate objects are instantiated—one for the array and one each for the 100 elements.</span></span>

[!code-csharp[PointClassUse](../../../samples/snippets/csharp/tour/structs/Program.cs#L5-L13)]

<span data-ttu-id="c5df9-113">Yapı noktası yapmak için kullanılan bir alternatiftir.</span><span class="sxs-lookup"><span data-stu-id="c5df9-113">An alternative is to make Point a struct.</span></span>

[!code-csharp[PointStruct](../../../samples/snippets/csharp/tour/structs/Point.cs#L3-L11)]

<span data-ttu-id="c5df9-114">Şimdi, yalnızca bir nesne örneği — bir dizi — ve `Point` saklı satır içi dizideki örnekleridir.</span><span class="sxs-lookup"><span data-stu-id="c5df9-114">Now, only one object is instantiated—the one for the array—and the `Point` instances are stored in-line in the array.</span></span>

<span data-ttu-id="c5df9-115">Yapı oluşturucuları yeni işleciyle çağrılır, ancak bu bellek göstermez tahsis edilir.</span><span class="sxs-lookup"><span data-stu-id="c5df9-115">Struct constructors are invoked with the new operator, but that does not imply that memory is being allocated.</span></span> <span data-ttu-id="c5df9-116">Dinamik bir nesne ayırma ve kendisine bir başvuru döndürme, yerine bir yapı Oluşturucu yalnızca yapısı değeri kendisini (genellikle geçici bir konuma yığında) döndürür ve bu değer daha sonra gerektiğinde kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="c5df9-116">Instead of dynamically allocating an object and returning a reference to it, a struct constructor simply returns the struct value itself (typically in a temporary location on the stack), and this value is then copied as necessary.</span></span>

<span data-ttu-id="c5df9-117">Sınıflar ile aynı nesneye başvurmak iki değişken için olası ve böylece olası bir değişkeni tarafından başvurulan nesne etkilemek için bir değişken üzerinde işlemler için.</span><span class="sxs-lookup"><span data-stu-id="c5df9-117">With classes, it is possible for two variables to reference the same object and thus possible for operations on one variable to affect the object referenced by the other variable.</span></span> <span data-ttu-id="c5df9-118">Yapılar, her değişkenleri veri kendi kopyasına sahip ve bir diğer etkileyen işlemler için kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="c5df9-118">With structs, the variables each have their own copy of the data, and it is not possible for operations on one to affect the other.</span></span> <span data-ttu-id="c5df9-119">Örneğin, aşağıdaki kod parçası tarafından üretilen çıkış noktası bir sınıf veya yapı olduğuna bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="c5df9-119">For example, the output produced by the following code fragment depends on whether Point is a class or a struct.</span></span>

[!code-csharp[PointUse](../../../samples/snippets/csharp/tour/structs/Program.cs#L19-L22)]

<span data-ttu-id="c5df9-120">Varsa `Point` bir sınıf çıkış 20 çünkü bir ve b aynı nesne başvurusu.</span><span class="sxs-lookup"><span data-stu-id="c5df9-120">If `Point` is a class, the output is 20 because a and b reference the same object.</span></span> <span data-ttu-id="c5df9-121">Noktası yapı çıktı 10 çünkü ise, atanması `a` için `b` değeri bir kopyasını oluşturur ve bu kopyayı sonraki atamayı tarafından etkilenmez `a.x`.</span><span class="sxs-lookup"><span data-stu-id="c5df9-121">If Point is a struct, the output is 10 because the assignment of `a` to `b` creates a copy of the value, and this copy is unaffected by the subsequent assignment to `a.x`.</span></span>

<span data-ttu-id="c5df9-122">Önceki örnekte iki yapılar sınırlamaları vurgular.</span><span class="sxs-lookup"><span data-stu-id="c5df9-122">The previous example highlights two of the limitations of structs.</span></span> <span data-ttu-id="c5df9-123">İlk olarak, bir yapının tamamını kopyalama atama ve değerin parametre geçirme yapılar başvuru türleri ile birlikte daha pahalı olabilir bir nesne başvurusu kopyalama daha genellikle daha az verimlidir.</span><span class="sxs-lookup"><span data-stu-id="c5df9-123">First, copying an entire struct is typically less efficient than copying an object reference, so assignment and value parameter passing can be more expensive with structs than with reference types.</span></span> <span data-ttu-id="c5df9-124">İkinci dışında `in`, `ref`, ve `out` parametreleri, bu kullanımları durumlarda çeşitli giden kuralları yapılar başvuruları oluşturmak mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="c5df9-124">Second, except for `in`, `ref`, and `out` parameters, it is not possible to create references to structs, which rules out their usage in a number of situations.</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="c5df9-125">[Önceki](classes-and-objects.md)
[sonraki](arrays.md)</span><span class="sxs-lookup"><span data-stu-id="c5df9-125">[Previous](classes-and-objects.md)
[Next](arrays.md)</span></span>
