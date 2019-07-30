---
title: Sınıflardaki do Bağlamaları
description: Nesne oluşturulduğunda veya tür ilk F# kullanıldığında eylemler gerçekleştiren bir sınıf tanımında ' do ' bağlamayı nasıl kullanacağınızı öğrenin.
ms.date: 05/16/2016
ms.openlocfilehash: ced4f1bb17d9e23bf51cc79b5a275cc334cca013
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68627579"
---
# <a name="do-bindings-in-classes"></a><span data-ttu-id="595ca-103">Sınıflardaki do Bağlamaları</span><span class="sxs-lookup"><span data-stu-id="595ca-103">do Bindings in Classes</span></span>

<span data-ttu-id="595ca-104">Bir sınıf tanımındaki `do` bağlama,nesneoluşturulduğundaveyabirstatikbağlamaiçintürilk`do` kullanıldığında eylemler gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="595ca-104">A `do` binding in a class definition performs actions when the object is constructed or, for a static `do` binding, when the type is first used.</span></span>

## <a name="syntax"></a><span data-ttu-id="595ca-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="595ca-105">Syntax</span></span>

```fsharp
[static] do expression
```

## <a name="remarks"></a><span data-ttu-id="595ca-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="595ca-106">Remarks</span></span>

<span data-ttu-id="595ca-107">Bağlama bağlamalarla birlikte veya sonra `let` , ancak bir sınıf tanımındaki üye tanımlarından önce görüntülenir. `do`</span><span class="sxs-lookup"><span data-stu-id="595ca-107">A `do` binding appears together with or after `let` bindings but before member definitions in a class definition.</span></span> <span data-ttu-id="595ca-108">Anahtar sözcüğü, modül düzeyindeki bağlamalar `do` için isteğe bağlı olsa da, bir sınıf tanımındaki bağlamalar için `do` isteğe bağlı değildir. `do`</span><span class="sxs-lookup"><span data-stu-id="595ca-108">Although the `do` keyword is optional for `do` bindings at the module level, it is not optional for `do` bindings in a class definition.</span></span>

<span data-ttu-id="595ca-109">Verili herhangi bir türdeki her nesnenin oluşturulması için, statik `do` olmayan bağlamalar ve statik `let` olmayan bağlamalar, sınıf tanımında göründükleri sırada yürütülür.</span><span class="sxs-lookup"><span data-stu-id="595ca-109">For the construction of every object of any given type, non-static `do` bindings and non-static `let` bindings are executed in the order in which they appear in the class definition.</span></span> <span data-ttu-id="595ca-110">Tek `do` bir türde birden çok bağlama meydana gelebilir.</span><span class="sxs-lookup"><span data-stu-id="595ca-110">Multiple `do` bindings can occur in one type.</span></span> <span data-ttu-id="595ca-111">Statik `let` olmayan bağlamalar ve statik `do` olmayan bağlamalar, birincil oluşturucunun gövdesi olur.</span><span class="sxs-lookup"><span data-stu-id="595ca-111">The non-static `let` bindings and the non-static `do` bindings become the body of the primary constructor.</span></span> <span data-ttu-id="595ca-112">Statik `do` olmayan bağlamalar bölümündeki kod, birincil Oluşturucu parametrelerine ve `let` bağlamalar bölümünde tanımlanan herhangi bir değere veya işleve başvurabilir.</span><span class="sxs-lookup"><span data-stu-id="595ca-112">The code in the non-static `do` bindings section can reference the primary constructor parameters and any values or functions that are defined in the `let` bindings section.</span></span>

<span data-ttu-id="595ca-113">Statik `do` olmayan bağlamalar, sınıf başlığında bir `as` anahtar sözcük tarafından tanımlanan bir kendine tanımlayıcı olduğu sürece ve bu üyelerin tüm kullanımları sınıf için kendi kendine tanımlayıcı ile nitelendirilse de, sınıfın üyelerine erişebilir.</span><span class="sxs-lookup"><span data-stu-id="595ca-113">Non-static `do` bindings can access members of the class as long as the class has a self identifier that is defined by an `as` keyword in the class heading, and as long as all uses of those members are qualified with the self identifier for the class.</span></span>

<span data-ttu-id="595ca-114">Bağlamalar, genellikle üyelerin `do` beklenen `let` şekilde davranmasını güvence altına almak için gerekli olan bir sınıfın özel alanlarını başlatırken, bağlamaların bağlamadaki `do`kodun `let` tamamen başlatılmış bir nesneyle yürütün.</span><span class="sxs-lookup"><span data-stu-id="595ca-114">Because `let` bindings initialize the private fields of a class, which is often necessary to guarantee that members behave as expected, `do` bindings are usually put after `let` bindings so that code in the `do` binding can execute with a fully initialized object.</span></span> <span data-ttu-id="595ca-115">Kodunuz, başlatma tamamlanmadan önce bir üye kullanmayı denerse, bir InvalidOperationException oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="595ca-115">If your code attempts to use a member before the initialization is complete, an InvalidOperationException is raised.</span></span>

<span data-ttu-id="595ca-116">Statik `do` bağlamalar, kapsayan sınıfın statik üyelerine veya alanlarına başvurabilir ancak örnek üye veya alanlar değildir.</span><span class="sxs-lookup"><span data-stu-id="595ca-116">Static `do` bindings can reference static members or fields of the enclosing class but not instance members or fields.</span></span> <span data-ttu-id="595ca-117">Statik `do` bağlamalar, sınıfının ilk kullanılmadan önce yürütülmesi garanti edilen, sınıfının statik başlatıcısının bir parçası haline gelir.</span><span class="sxs-lookup"><span data-stu-id="595ca-117">Static `do` bindings become part of the static initializer for the class, which is guaranteed to execute before the class is first used.</span></span>

<span data-ttu-id="595ca-118">Türler içindeki bağlamalar için `do` öznitelikler yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="595ca-118">Attributes are ignored for `do` bindings in types.</span></span> <span data-ttu-id="595ca-119">Bir `do` bağlamada yürütülen kod için bir öznitelik gerekliyse, birincil oluşturucuya uygulanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="595ca-119">If an attribute is required for code that executes in a `do` binding, it must be applied to the primary constructor.</span></span>

<span data-ttu-id="595ca-120">Aşağıdaki kodda, bir sınıfta statik `do` bağlama ve statik `do` olmayan bağlama bulunur.</span><span class="sxs-lookup"><span data-stu-id="595ca-120">In the following code, a class has a static `do` binding and a non-static `do` binding.</span></span> <span data-ttu-id="595ca-121">Nesnesi iki parametreye `a` sahip bir oluşturucuya sahiptir ve `b`ve iki özel `let` alan, sınıf bağlamalarında tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="595ca-121">The object has a constructor that has two parameters, `a` and `b`, and two private fields are defined in the `let` bindings for the class.</span></span> <span data-ttu-id="595ca-122">İki özellik de tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="595ca-122">Two properties are also defined.</span></span> <span data-ttu-id="595ca-123">Bunların hepsi, statik `do` olmayan bağlamalar bölümünde, tüm bu değerleri yazdıran satıra göre gösterildiği gibi kapsamdadır.</span><span class="sxs-lookup"><span data-stu-id="595ca-123">All of these are in scope in the non-static `do` bindings section, as is illustrated by the line that prints all those values.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3101.fs)]

<span data-ttu-id="595ca-124">Çıktı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="595ca-124">The output is as follows.</span></span>

```console
Initializing MyType.
Initializing object 1 2 2 4 8 16
```

## <a name="see-also"></a><span data-ttu-id="595ca-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="595ca-125">See also</span></span>

- [<span data-ttu-id="595ca-126">Üyeler</span><span class="sxs-lookup"><span data-stu-id="595ca-126">Members</span></span>](index.md)
- [<span data-ttu-id="595ca-127">Sınıflar</span><span class="sxs-lookup"><span data-stu-id="595ca-127">Classes</span></span>](../classes.md)
- [<span data-ttu-id="595ca-128">Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="595ca-128">Constructors</span></span>](constructors.md)
- [<span data-ttu-id="595ca-129">`let`Sınıflarda bağlamalar</span><span class="sxs-lookup"><span data-stu-id="595ca-129">`let` Bindings in Classes</span></span>](let-bindings-in-classes.md)
- [<span data-ttu-id="595ca-130">`do`Lara</span><span class="sxs-lookup"><span data-stu-id="595ca-130">`do` Bindings</span></span>](../functions/do-Bindings.md)
