---
title: Sınıflardaki let Bağlamaları
description: Sınıf tanımındaki ' Let ' bağlamalarını kullanarak sınıflar için F# özel alanları ve özel işlevleri tanımlamayı öğrenin.
ms.date: 05/16/2016
ms.openlocfilehash: 1366ab8f1f4f606fe5947a8fc4df10de49346b3e
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71216522"
---
# <a name="let-bindings-in-classes"></a><span data-ttu-id="9d90c-103">Sınıflardaki let Bağlamaları</span><span class="sxs-lookup"><span data-stu-id="9d90c-103">let Bindings in Classes</span></span>

<span data-ttu-id="9d90c-104">Sınıf tanımındaki bağlamaları kullanarak F# `let` sınıflar için özel alanlar ve özel işlevler tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9d90c-104">You can define private fields and private functions for F# classes by using `let` bindings in the class definition.</span></span>

## <a name="syntax"></a><span data-ttu-id="9d90c-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9d90c-105">Syntax</span></span>

```fsharp
// Field.
[static] let [ mutable ] binding1 [ and ... binding-n ]

// Function.
[static] let [ rec ] binding1 [ and ... binding-n ]
```

## <a name="remarks"></a><span data-ttu-id="9d90c-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9d90c-106">Remarks</span></span>

<span data-ttu-id="9d90c-107">Önceki sözdizimi, sınıf başlığı ve devralma bildirimlerinden sonra, tüm üye tanımlarından önce görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="9d90c-107">The previous syntax appears after the class heading and inheritance declarations but before any member definitions.</span></span> <span data-ttu-id="9d90c-108">Söz dizimi sınıfların dışındaki `let` bağlamalardan gibidir, ancak bir sınıfta tanımlanan adların, sınıfıyla sınırlı bir kapsamı vardır.</span><span class="sxs-lookup"><span data-stu-id="9d90c-108">The syntax is like that of `let` bindings outside of classes, but the names defined in a class have a scope that is limited to the class.</span></span> <span data-ttu-id="9d90c-109">`let` Bağlama, verileri veya işlevleri herkese açık bir şekilde göstermek için bir özel alan veya işlev oluşturur; bir özellik veya bir üye yöntemi bildirir.</span><span class="sxs-lookup"><span data-stu-id="9d90c-109">A `let` binding creates a private field or function; to expose data or functions publicly, declare a property or a member method.</span></span>

<span data-ttu-id="9d90c-110">Statik `let` olmayan bir bağlama örnek `let` bağlama olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="9d90c-110">A `let` binding that is not static is called an instance `let` binding.</span></span> <span data-ttu-id="9d90c-111">Nesneler `let` oluşturulduğunda örnek bağlamaları yürütülür.</span><span class="sxs-lookup"><span data-stu-id="9d90c-111">Instance `let` bindings execute when objects are created.</span></span> <span data-ttu-id="9d90c-112">Statik `let` bağlamalar, türü ilk kullanılmadan önce yürütülmesi garanti edilen, sınıfının statik başlatıcısının bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="9d90c-112">Static `let` bindings are part of the static initializer for the class, which is guaranteed to execute before the type is first used.</span></span>

<span data-ttu-id="9d90c-113">Örnek `let` bağlamaların içindeki kod, birincil oluşturucunun parametrelerini kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="9d90c-113">The code within instance `let` bindings can use the primary constructor's parameters.</span></span>

<span data-ttu-id="9d90c-114">Sınıflardaki bağlamalarda `let` özniteliklere ve erişilebilirlik değiştiricilerine izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="9d90c-114">Attributes and accessibility modifiers are not permitted on `let` bindings in classes.</span></span>

<span data-ttu-id="9d90c-115">Aşağıdaki kod örnekleri sınıflardaki çeşitli `let` bağlama türlerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="9d90c-115">The following code examples illustrate several types of `let` bindings in classes.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3001.fs)]

<span data-ttu-id="9d90c-116">Çıktı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="9d90c-116">The output is as follows.</span></span>

```console
10 52 1 204
```

## <a name="alternative-ways-to-create-fields"></a><span data-ttu-id="9d90c-117">Alan oluşturmak için alternatif yollar</span><span class="sxs-lookup"><span data-stu-id="9d90c-117">Alternative Ways to Create Fields</span></span>

<span data-ttu-id="9d90c-118">Özel bir alan oluşturmak için `val` anahtar sözcüğünü de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9d90c-118">You can also use the `val` keyword to create a private field.</span></span> <span data-ttu-id="9d90c-119">`val` Anahtar sözcüğü kullanılırken, nesne oluşturulduğunda alana bir değer verilmez, bunun yerine varsayılan bir değerle başlatılır.</span><span class="sxs-lookup"><span data-stu-id="9d90c-119">When using the `val` keyword, the field is not given a value when the object is created, but instead is initialized with a default value.</span></span> <span data-ttu-id="9d90c-120">Daha fazla bilgi için bkz [. açık alanlar: Val anahtar sözcüğü](explicit-fields-the-val-keyword.md).</span><span class="sxs-lookup"><span data-stu-id="9d90c-120">For more information, see [Explicit Fields: The val Keyword](explicit-fields-the-val-keyword.md).</span></span>

<span data-ttu-id="9d90c-121">Ayrıca, bir üye tanımı kullanarak ve tanımına anahtar sözcüğünü `private` ekleyerek bir sınıfta özel alanlar tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9d90c-121">You can also define private fields in a class by using a member definition and adding the keyword `private` to the definition.</span></span> <span data-ttu-id="9d90c-122">Bu, kodunuzu yeniden yazmadan bir üyenin erişilebilirliğini değiştirmeniz beklendiğinde yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="9d90c-122">This can be useful if you expect to change the accessibility of a member without rewriting your code.</span></span> <span data-ttu-id="9d90c-123">Daha fazla bilgi için bkz. [Access Control](../access-control.md).</span><span class="sxs-lookup"><span data-stu-id="9d90c-123">For more information, see [Access Control](../access-control.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="9d90c-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9d90c-124">See also</span></span>

- [<span data-ttu-id="9d90c-125">Üyeler</span><span class="sxs-lookup"><span data-stu-id="9d90c-125">Members</span></span>](index.md)
- [<span data-ttu-id="9d90c-126">`do`Sınıflarda bağlamalar</span><span class="sxs-lookup"><span data-stu-id="9d90c-126">`do` Bindings in Classes</span></span>](do-bindings-in-classes.md)
- [<span data-ttu-id="9d90c-127">`let`Lara</span><span class="sxs-lookup"><span data-stu-id="9d90c-127">`let` Bindings</span></span>](../functions/let-bindings.md)
