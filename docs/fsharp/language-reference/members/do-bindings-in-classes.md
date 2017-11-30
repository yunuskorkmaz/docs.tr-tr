---
title: "Sınıflardaki do Bağlamaları (F#)"
description: "F # 'nesne oluşturulduğunda veya türü ilk kullanıldığında eylemler gerçekleştiren bir sınıf tanımı bağlamasında do' kullanmayı öğrenin."
keywords: "Visual f #, f # işlevsel programlama"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 78987cb8-bdba-46e2-b5b2-994c83fe42c4
ms.openlocfilehash: f9582338306d87c3dd799425083037cc95b31b1e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="do-bindings-in-classes"></a><span data-ttu-id="5e2e8-104">Sınıflardaki do Bağlamaları</span><span class="sxs-lookup"><span data-stu-id="5e2e8-104">do Bindings in Classes</span></span>

<span data-ttu-id="5e2e8-105">A `do` sınıf tanımında bağlama nesnesi oluşturulduğunda veya bir statik eylemleri gerçekleştirir `do` bağlama, türü ilk kullanıldığında.</span><span class="sxs-lookup"><span data-stu-id="5e2e8-105">A `do` binding in a class definition performs actions when the object is constructed or, for a static `do` binding, when the type is first used.</span></span>


## <a name="syntax"></a><span data-ttu-id="5e2e8-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5e2e8-106">Syntax</span></span>

```fsharp
[static] do expression
```

## <a name="remarks"></a><span data-ttu-id="5e2e8-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5e2e8-107">Remarks</span></span>
<span data-ttu-id="5e2e8-108">A `do` bağlama görünür ile birlikte veya sonra `let` bağlamaları ancak bir sınıf tanımı üye tanımlarında önce.</span><span class="sxs-lookup"><span data-stu-id="5e2e8-108">A `do` binding appears together with or after `let` bindings but before member definitions in a class definition.</span></span> <span data-ttu-id="5e2e8-109">Ancak `do` anahtar sözcüğü için isteğe bağlı `do` bağlamaları Modül düzeyinde onu için isteğe bağlı değil `do` bir sınıf tanımı bağlama.</span><span class="sxs-lookup"><span data-stu-id="5e2e8-109">Although the `do` keyword is optional for `do` bindings at the module level, it is not optional for `do` bindings in a class definition.</span></span>

<span data-ttu-id="5e2e8-110">Her nesne herhangi yapımı için belirtilen tür, statik olmayan `do` bağlamalar ve statik olmayan `let` bağlamaları sınıf tanımında göründükleri sırada çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="5e2e8-110">For the construction of every object of any given type, non-static `do` bindings and non-static `let` bindings are executed in the order in which they appear in the class definition.</span></span> <span data-ttu-id="5e2e8-111">Birden çok `do` bağlamaları bir türüne meydana gelebilir.</span><span class="sxs-lookup"><span data-stu-id="5e2e8-111">Multiple `do` bindings can occur in one type.</span></span> <span data-ttu-id="5e2e8-112">Statik olmayan `let` bağlamalar ve statik olmayan `do` bağlamaları birincil Oluşturucusu gövdesi haline gelir.</span><span class="sxs-lookup"><span data-stu-id="5e2e8-112">The non-static `let` bindings and the non-static `do` bindings become the body of the primary constructor.</span></span> <span data-ttu-id="5e2e8-113">Statik olmayan kodda `do` bağlamaları bölümü başvuru birincil Oluşturucusu parametreler ve değerler veya tanımlanan işlevler `let` bağlamaları bölümü.</span><span class="sxs-lookup"><span data-stu-id="5e2e8-113">The code in the non-static `do` bindings section can reference the primary constructor parameters and any values or functions that are defined in the `let` bindings section.</span></span>

<span data-ttu-id="5e2e8-114">Statik olmayan `do` bağlamaları, sınıf üyeleri erişebilir, sınıf tarafından tanımlanan bir kendi kendini tanımlayıcısı olduğu sürece bir `as` başlık ve tüm bu üyeler kullanımlarını sınıfı için kendi kendine tanımlayıcısı ile tam olarak uzun sınıfı anahtar sözcük.</span><span class="sxs-lookup"><span data-stu-id="5e2e8-114">Non-static `do` bindings can access members of the class as long as the class has a self identifier that is defined by an `as` keyword in the class heading, and as long as all uses of those members are qualified with the self identifier for the class.</span></span>

<span data-ttu-id="5e2e8-115">Çünkü `let` bağlamaları başlatma özel alanları genellikle üyeleri beklendiği gibi davranır güvence altına almak gerekli olan, bir sınıfın `do` bağlamaları sonra genellikle konur `let` kod, böylece bağlamaları `do` bağlama can tamamen başlatılmış bir nesneyle yürütün.</span><span class="sxs-lookup"><span data-stu-id="5e2e8-115">Because `let` bindings initialize the private fields of a class, which is often necessary to guarantee that members behave as expected, `do` bindings are usually put after `let` bindings so that code in the `do` binding can execute with a fully initialized object.</span></span> <span data-ttu-id="5e2e8-116">Kodunuzu başlatılması tamamlanmadan önce bir üyesini kullanmaya çalışırsa, bir InvalidOperationException tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="5e2e8-116">If your code attempts to use a member before the initialization is complete, an InvalidOperationException is raised.</span></span>

<span data-ttu-id="5e2e8-117">Statik `do` bağlamaları statik üyeler başvuru veya kapsayan alanların sınıf ancak üyeleri veya alanlar örneği değil.</span><span class="sxs-lookup"><span data-stu-id="5e2e8-117">Static `do` bindings can reference static members or fields of the enclosing class but not instance members or fields.</span></span> <span data-ttu-id="5e2e8-118">Statik `do` bağlamaları statik Başlatıcı sınıfı ilk kullanılmadan önce yürütülecek garanti sınıfının bir parçası haline gelir.</span><span class="sxs-lookup"><span data-stu-id="5e2e8-118">Static `do` bindings become part of the static initializer for the class, which is guaranteed to execute before the class is first used.</span></span>

<span data-ttu-id="5e2e8-119">Öznitelikler için yoksayılır `do` türlerinde bağlar.</span><span class="sxs-lookup"><span data-stu-id="5e2e8-119">Attributes are ignored for `do` bindings in types.</span></span> <span data-ttu-id="5e2e8-120">Bir öznitelik olarak yürütülen kodu için gerekli olup olmadığını bir `do` bağlama, bunun birincil oluşturucuya uygulanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="5e2e8-120">If an attribute is required for code that executes in a `do` binding, it must be applied to the primary constructor.</span></span>

<span data-ttu-id="5e2e8-121">Aşağıdaki kodda bir sınıf statik sahip `do` bağlama ve statik olmayan `do` bağlama.</span><span class="sxs-lookup"><span data-stu-id="5e2e8-121">In the following code, a class has a static `do` binding and a non-static `do` binding.</span></span> <span data-ttu-id="5e2e8-122">Nesne iki parametreye sahip bir kurucusunun `a` ve `b`, ve iki özel alan tanımlanmış `let` sınıfı için bağlamalar.</span><span class="sxs-lookup"><span data-stu-id="5e2e8-122">The object has a constructor that has two parameters, `a` and `b`, and two private fields are defined in the `let` bindings for the class.</span></span> <span data-ttu-id="5e2e8-123">İki özellik de tanımlanabilir.</span><span class="sxs-lookup"><span data-stu-id="5e2e8-123">Two properties are also defined.</span></span> <span data-ttu-id="5e2e8-124">Bu statik olmayan kapsamda tümü `do` bağlamaları bölümünde, bu değerleri yazdırır satırı ile gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="5e2e8-124">All of these are in scope in the non-static `do` bindings section, as is illustrated by the line that prints all those values.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3101.fs)]

<span data-ttu-id="5e2e8-125">Çıktı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="5e2e8-125">The output is as follows.</span></span>

```console
Initializing MyType.
Initializing object 1 2 2 4 8 16
```

## <a name="see-also"></a><span data-ttu-id="5e2e8-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5e2e8-126">See Also</span></span>
[<span data-ttu-id="5e2e8-127">Üyeleri</span><span class="sxs-lookup"><span data-stu-id="5e2e8-127">Members</span></span>](index.md)

[<span data-ttu-id="5e2e8-128">Sınıfları</span><span class="sxs-lookup"><span data-stu-id="5e2e8-128">Classes</span></span>](../classes.md)

[<span data-ttu-id="5e2e8-129">Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="5e2e8-129">Constructors</span></span>](constructors.md)

[<span data-ttu-id="5e2e8-130">`let`Sınıflardaki bağlamaları</span><span class="sxs-lookup"><span data-stu-id="5e2e8-130">`let` Bindings in Classes</span></span>](let-bindings-in-classes.md)

[<span data-ttu-id="5e2e8-131">`do`Bağlamaları</span><span class="sxs-lookup"><span data-stu-id="5e2e8-131">`do` Bindings</span></span>](../functions/do-Bindings.md)
