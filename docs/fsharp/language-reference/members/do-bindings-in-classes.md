---
title: Sınıflardaki do Bağlamaları (F#)
description: "F # 'nesne oluşturulduğunda veya türü ilk kullanıldığında eylemler gerçekleştiren bir sınıf tanımı bağlamasında do' kullanmayı öğrenin."
ms.date: 05/16/2016
ms.openlocfilehash: 779b33c44b1518135f4c7f270173ec8124fec101
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33565197"
---
# <a name="do-bindings-in-classes"></a><span data-ttu-id="d15ef-103">Sınıflardaki do Bağlamaları</span><span class="sxs-lookup"><span data-stu-id="d15ef-103">do Bindings in Classes</span></span>

<span data-ttu-id="d15ef-104">A `do` sınıf tanımında bağlama nesnesi oluşturulduğunda veya bir statik eylemleri gerçekleştirir `do` bağlama, türü ilk kullanıldığında.</span><span class="sxs-lookup"><span data-stu-id="d15ef-104">A `do` binding in a class definition performs actions when the object is constructed or, for a static `do` binding, when the type is first used.</span></span>


## <a name="syntax"></a><span data-ttu-id="d15ef-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d15ef-105">Syntax</span></span>

```fsharp
[static] do expression
```

## <a name="remarks"></a><span data-ttu-id="d15ef-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d15ef-106">Remarks</span></span>
<span data-ttu-id="d15ef-107">A `do` bağlama görünür ile birlikte veya sonra `let` bağlamaları ancak bir sınıf tanımı üye tanımlarında önce.</span><span class="sxs-lookup"><span data-stu-id="d15ef-107">A `do` binding appears together with or after `let` bindings but before member definitions in a class definition.</span></span> <span data-ttu-id="d15ef-108">Ancak `do` anahtar sözcüğü için isteğe bağlı `do` bağlamaları Modül düzeyinde onu için isteğe bağlı değil `do` bir sınıf tanımı bağlama.</span><span class="sxs-lookup"><span data-stu-id="d15ef-108">Although the `do` keyword is optional for `do` bindings at the module level, it is not optional for `do` bindings in a class definition.</span></span>

<span data-ttu-id="d15ef-109">Her nesne herhangi yapımı için belirtilen tür, statik olmayan `do` bağlamalar ve statik olmayan `let` bağlamaları sınıf tanımında göründükleri sırada çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="d15ef-109">For the construction of every object of any given type, non-static `do` bindings and non-static `let` bindings are executed in the order in which they appear in the class definition.</span></span> <span data-ttu-id="d15ef-110">Birden çok `do` bağlamaları bir türüne meydana gelebilir.</span><span class="sxs-lookup"><span data-stu-id="d15ef-110">Multiple `do` bindings can occur in one type.</span></span> <span data-ttu-id="d15ef-111">Statik olmayan `let` bağlamalar ve statik olmayan `do` bağlamaları birincil Oluşturucusu gövdesi haline gelir.</span><span class="sxs-lookup"><span data-stu-id="d15ef-111">The non-static `let` bindings and the non-static `do` bindings become the body of the primary constructor.</span></span> <span data-ttu-id="d15ef-112">Statik olmayan kodda `do` bağlamaları bölümü başvuru birincil Oluşturucusu parametreler ve değerler veya tanımlanan işlevler `let` bağlamaları bölümü.</span><span class="sxs-lookup"><span data-stu-id="d15ef-112">The code in the non-static `do` bindings section can reference the primary constructor parameters and any values or functions that are defined in the `let` bindings section.</span></span>

<span data-ttu-id="d15ef-113">Statik olmayan `do` bağlamaları, sınıf üyeleri erişebilir, sınıf tarafından tanımlanan bir kendi kendini tanımlayıcısı olduğu sürece bir `as` başlık ve tüm bu üyeler kullanımlarını sınıfı için kendi kendine tanımlayıcısı ile tam olarak uzun sınıfı anahtar sözcük.</span><span class="sxs-lookup"><span data-stu-id="d15ef-113">Non-static `do` bindings can access members of the class as long as the class has a self identifier that is defined by an `as` keyword in the class heading, and as long as all uses of those members are qualified with the self identifier for the class.</span></span>

<span data-ttu-id="d15ef-114">Çünkü `let` bağlamaları başlatma özel alanları genellikle üyeleri beklendiği gibi davranır güvence altına almak gerekli olan, bir sınıfın `do` bağlamaları sonra genellikle konur `let` kod, böylece bağlamaları `do` bağlama can tamamen başlatılmış bir nesneyle yürütün.</span><span class="sxs-lookup"><span data-stu-id="d15ef-114">Because `let` bindings initialize the private fields of a class, which is often necessary to guarantee that members behave as expected, `do` bindings are usually put after `let` bindings so that code in the `do` binding can execute with a fully initialized object.</span></span> <span data-ttu-id="d15ef-115">Kodunuzu başlatılması tamamlanmadan önce bir üyesini kullanmaya çalışırsa, bir InvalidOperationException tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="d15ef-115">If your code attempts to use a member before the initialization is complete, an InvalidOperationException is raised.</span></span>

<span data-ttu-id="d15ef-116">Statik `do` bağlamaları statik üyeler başvuru veya kapsayan alanların sınıf ancak üyeleri veya alanlar örneği değil.</span><span class="sxs-lookup"><span data-stu-id="d15ef-116">Static `do` bindings can reference static members or fields of the enclosing class but not instance members or fields.</span></span> <span data-ttu-id="d15ef-117">Statik `do` bağlamaları statik Başlatıcı sınıfı ilk kullanılmadan önce yürütülecek garanti sınıfının bir parçası haline gelir.</span><span class="sxs-lookup"><span data-stu-id="d15ef-117">Static `do` bindings become part of the static initializer for the class, which is guaranteed to execute before the class is first used.</span></span>

<span data-ttu-id="d15ef-118">Öznitelikler için yoksayılır `do` türlerinde bağlar.</span><span class="sxs-lookup"><span data-stu-id="d15ef-118">Attributes are ignored for `do` bindings in types.</span></span> <span data-ttu-id="d15ef-119">Bir öznitelik olarak yürütülen kodu için gerekli olup olmadığını bir `do` bağlama, bunun birincil oluşturucuya uygulanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="d15ef-119">If an attribute is required for code that executes in a `do` binding, it must be applied to the primary constructor.</span></span>

<span data-ttu-id="d15ef-120">Aşağıdaki kodda bir sınıf statik sahip `do` bağlama ve statik olmayan `do` bağlama.</span><span class="sxs-lookup"><span data-stu-id="d15ef-120">In the following code, a class has a static `do` binding and a non-static `do` binding.</span></span> <span data-ttu-id="d15ef-121">Nesne iki parametreye sahip bir kurucusunun `a` ve `b`, ve iki özel alan tanımlanmış `let` sınıfı için bağlamalar.</span><span class="sxs-lookup"><span data-stu-id="d15ef-121">The object has a constructor that has two parameters, `a` and `b`, and two private fields are defined in the `let` bindings for the class.</span></span> <span data-ttu-id="d15ef-122">İki özellik de tanımlanabilir.</span><span class="sxs-lookup"><span data-stu-id="d15ef-122">Two properties are also defined.</span></span> <span data-ttu-id="d15ef-123">Bu statik olmayan kapsamda tümü `do` bağlamaları bölümünde, bu değerleri yazdırır satırı ile gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="d15ef-123">All of these are in scope in the non-static `do` bindings section, as is illustrated by the line that prints all those values.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3101.fs)]

<span data-ttu-id="d15ef-124">Çıktı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="d15ef-124">The output is as follows.</span></span>

```console
Initializing MyType.
Initializing object 1 2 2 4 8 16
```

## <a name="see-also"></a><span data-ttu-id="d15ef-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d15ef-125">See Also</span></span>
[<span data-ttu-id="d15ef-126">Üyeler</span><span class="sxs-lookup"><span data-stu-id="d15ef-126">Members</span></span>](index.md)

[<span data-ttu-id="d15ef-127">Sınıflar</span><span class="sxs-lookup"><span data-stu-id="d15ef-127">Classes</span></span>](../classes.md)

[<span data-ttu-id="d15ef-128">Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="d15ef-128">Constructors</span></span>](constructors.md)

[<span data-ttu-id="d15ef-129">`let` Sınıflardaki bağlamaları</span><span class="sxs-lookup"><span data-stu-id="d15ef-129">`let` Bindings in Classes</span></span>](let-bindings-in-classes.md)

[<span data-ttu-id="d15ef-130">`do` Bağlamaları</span><span class="sxs-lookup"><span data-stu-id="d15ef-130">`do` Bindings</span></span>](../functions/do-Bindings.md)
