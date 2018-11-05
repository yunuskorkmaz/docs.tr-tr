---
title: Sınıflardaki do Bağlamaları (F#)
description: "F # 'nesne oluşturulduğunda veya türü ilk defa kullanıldığında eylemler gerçekleştiren bir sınıf tanımı bağlaması yapma' kullanmayı öğrenin."
ms.date: 05/16/2016
ms.openlocfilehash: e54a5bde52bf6973cc338c929ba99e6fd5b53127
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/02/2018
ms.locfileid: "43801547"
---
# <a name="do-bindings-in-classes"></a><span data-ttu-id="b56cd-103">Sınıflardaki do Bağlamaları</span><span class="sxs-lookup"><span data-stu-id="b56cd-103">do Bindings in Classes</span></span>

<span data-ttu-id="b56cd-104">A `do` nesne oluşturulduğunda veya statik bir sınıf tanımı bağlamasında eylemleri gerçekleştirir `do` bağlamayı türü ilk kez kullanıldığında.</span><span class="sxs-lookup"><span data-stu-id="b56cd-104">A `do` binding in a class definition performs actions when the object is constructed or, for a static `do` binding, when the type is first used.</span></span>

## <a name="syntax"></a><span data-ttu-id="b56cd-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b56cd-105">Syntax</span></span>

```fsharp
[static] do expression
```

## <a name="remarks"></a><span data-ttu-id="b56cd-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b56cd-106">Remarks</span></span>

<span data-ttu-id="b56cd-107">A `do` bağlama ile birlikte veya sonra görünür `let` bağlamaları, ancak bir sınıf tanımının üye tanımlarında önce.</span><span class="sxs-lookup"><span data-stu-id="b56cd-107">A `do` binding appears together with or after `let` bindings but before member definitions in a class definition.</span></span> <span data-ttu-id="b56cd-108">Ancak `do` anahtar sözcüğü için isteğe bağlı `do` bağlamaları Modül düzeyinde bu için isteğe bağlı değil `do` bağlamaları bir sınıf tanımı.</span><span class="sxs-lookup"><span data-stu-id="b56cd-108">Although the `do` keyword is optional for `do` bindings at the module level, it is not optional for `do` bindings in a class definition.</span></span>

<span data-ttu-id="b56cd-109">Türü, statik olmayan her nesne herhangi oluşumu için verilen `do` bağlamaları ve statik olmayan `let` bağlamaları, sınıf tanımında göründükleri sırayla yürütülür.</span><span class="sxs-lookup"><span data-stu-id="b56cd-109">For the construction of every object of any given type, non-static `do` bindings and non-static `let` bindings are executed in the order in which they appear in the class definition.</span></span> <span data-ttu-id="b56cd-110">Birden çok `do` bağlamaları bir türüne meydana gelebilir.</span><span class="sxs-lookup"><span data-stu-id="b56cd-110">Multiple `do` bindings can occur in one type.</span></span> <span data-ttu-id="b56cd-111">Statik olmayan `let` bağlamaları ve statik olmayan `do` bağlamaları birincil oluşturucusunun gövdesi olur.</span><span class="sxs-lookup"><span data-stu-id="b56cd-111">The non-static `let` bindings and the non-static `do` bindings become the body of the primary constructor.</span></span> <span data-ttu-id="b56cd-112">Statik olmayan kodda `do` bağlamalar bölümü birincil Oluşturucu parametreler ve değerler veya tanımlanan işlevleri başvurabilir `let` bağlamalar bölümü.</span><span class="sxs-lookup"><span data-stu-id="b56cd-112">The code in the non-static `do` bindings section can reference the primary constructor parameters and any values or functions that are defined in the `let` bindings section.</span></span>

<span data-ttu-id="b56cd-113">Statik olmayan `do` bağlamaları, sınıfın üyelerine erişebilir, sınıf tarafından tanımlanan bir kendi kendini tanımlayıcısı olduğu sürece bir `as` başlık ve bu üyelerin tüm kullanımları sınıfı için kendi kendine tanımlayıcısı ile tam olarak uzun sınıfı anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="b56cd-113">Non-static `do` bindings can access members of the class as long as the class has a self identifier that is defined by an `as` keyword in the class heading, and as long as all uses of those members are qualified with the self identifier for the class.</span></span>

<span data-ttu-id="b56cd-114">Çünkü `let` bağlamaları başlatmak özel alanlar genellikle üyeleri beklendiği gibi davranmaya garanti etmek gerekli olan, bir sınıfın `do` bağlamaları sonra genellikle isimlerine `let` kod, bu nedenle bağlamaları `do` bağlama can tam olarak başlatılmış bir nesneyle yürütün.</span><span class="sxs-lookup"><span data-stu-id="b56cd-114">Because `let` bindings initialize the private fields of a class, which is often necessary to guarantee that members behave as expected, `do` bindings are usually put after `let` bindings so that code in the `do` binding can execute with a fully initialized object.</span></span> <span data-ttu-id="b56cd-115">Kodunuzu başlatılması tamamlanmadan önce bir üyesini kullanın çalışırsa, bir InvalidOperationException ortaya çıkar.</span><span class="sxs-lookup"><span data-stu-id="b56cd-115">If your code attempts to use a member before the initialization is complete, an InvalidOperationException is raised.</span></span>

<span data-ttu-id="b56cd-116">Statik `do` bağlamaları statik üyeleri başvurabilir veya kapsayan alan sınıfının ancak örnek üye veya alan değil.</span><span class="sxs-lookup"><span data-stu-id="b56cd-116">Static `do` bindings can reference static members or fields of the enclosing class but not instance members or fields.</span></span> <span data-ttu-id="b56cd-117">Statik `do` bağlamaları sınıfı ilk kez kullanılmadan önce yürütülecek garanti sınıfı için statik Başlatıcı bir parçası haline gelir.</span><span class="sxs-lookup"><span data-stu-id="b56cd-117">Static `do` bindings become part of the static initializer for the class, which is guaranteed to execute before the class is first used.</span></span>

<span data-ttu-id="b56cd-118">Öznitelikler için yoksayıldı `do` türlerinde bağlar.</span><span class="sxs-lookup"><span data-stu-id="b56cd-118">Attributes are ignored for `do` bindings in types.</span></span> <span data-ttu-id="b56cd-119">Bir öznitelik için yürütülen kodu gerekli olup olmadığını bir `do` bağlama, bunun birincil oluşturucuya uygulanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="b56cd-119">If an attribute is required for code that executes in a `do` binding, it must be applied to the primary constructor.</span></span>

<span data-ttu-id="b56cd-120">Aşağıdaki kodda, statik sınıfında `do` bağlama ve statik olmayan `do` bağlama.</span><span class="sxs-lookup"><span data-stu-id="b56cd-120">In the following code, a class has a static `do` binding and a non-static `do` binding.</span></span> <span data-ttu-id="b56cd-121">Nesne iki parametreye sahip bir oluşturucuya sahip `a` ve `b`, ve iki özel alan tanımlanmış `let` bağlamaları sınıfı.</span><span class="sxs-lookup"><span data-stu-id="b56cd-121">The object has a constructor that has two parameters, `a` and `b`, and two private fields are defined in the `let` bindings for the class.</span></span> <span data-ttu-id="b56cd-122">İki özellik de tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="b56cd-122">Two properties are also defined.</span></span> <span data-ttu-id="b56cd-123">Tüm bunların statik olmayan kapsamda bulunan `do` bağlamalar bölümü, tüm bu değerlere yazdırır çizgiyle gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="b56cd-123">All of these are in scope in the non-static `do` bindings section, as is illustrated by the line that prints all those values.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3101.fs)]

<span data-ttu-id="b56cd-124">Çıktı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="b56cd-124">The output is as follows.</span></span>

```console
Initializing MyType.
Initializing object 1 2 2 4 8 16
```

## <a name="see-also"></a><span data-ttu-id="b56cd-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b56cd-125">See also</span></span>

- [<span data-ttu-id="b56cd-126">Üyeler</span><span class="sxs-lookup"><span data-stu-id="b56cd-126">Members</span></span>](index.md)
- [<span data-ttu-id="b56cd-127">Sınıflar</span><span class="sxs-lookup"><span data-stu-id="b56cd-127">Classes</span></span>](../classes.md)
- [<span data-ttu-id="b56cd-128">Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="b56cd-128">Constructors</span></span>](constructors.md)
- [<span data-ttu-id="b56cd-129">`let` Sınıflardaki bağlamaları</span><span class="sxs-lookup"><span data-stu-id="b56cd-129">`let` Bindings in Classes</span></span>](let-bindings-in-classes.md)
- [<span data-ttu-id="b56cd-130">`do` Bağlamaları</span><span class="sxs-lookup"><span data-stu-id="b56cd-130">`do` Bindings</span></span>](../functions/do-Bindings.md)
