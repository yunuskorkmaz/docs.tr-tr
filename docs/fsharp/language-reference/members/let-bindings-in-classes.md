---
title: Sınıflardaki let Bağlamaları (F#)
description: "Sınıf tanımı'nda 'let' bağlamaları kullanarak özel alanlar ve F # sınıfları için özel işlevler tanımlamak öğrenin."
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: c4511a541403dde517acaf902e86de8d48f13781
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="let-bindings-in-classes"></a><span data-ttu-id="7fce0-103">Sınıflardaki let Bağlamaları</span><span class="sxs-lookup"><span data-stu-id="7fce0-103">let Bindings in Classes</span></span>

<span data-ttu-id="7fce0-104">Kullanarak özel alanlar ve F # sınıfları için özel işlevler tanımlayabilirsiniz `let` sınıf tanımında bağlar.</span><span class="sxs-lookup"><span data-stu-id="7fce0-104">You can define private fields and private functions for F# classes by using `let` bindings in the class definition.</span></span>


## <a name="syntax"></a><span data-ttu-id="7fce0-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7fce0-105">Syntax</span></span>

```fsharp
// Field.
[static] let [ mutable ] binding1 [ and ... binding-n ]

// Function.
[static] let [ rec ] binding1 [ and ... binding-n ]
```

## <a name="remarks"></a><span data-ttu-id="7fce0-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7fce0-106">Remarks</span></span>
<span data-ttu-id="7fce0-107">Önceki sözdizimi sınıf başlık ve devralma bildirimleri sonra ancak herhangi bir üye tanımları önce görünür.</span><span class="sxs-lookup"><span data-stu-id="7fce0-107">The previous syntax appears after the class heading and inheritance declarations but before any member definitions.</span></span> <span data-ttu-id="7fce0-108">Söz dizimi, gibi `let` sınıfları, ancak bir sınıf içinde tanımlanan adlar dışında bağlamaları sınıfa sınırlı bir kapsam vardır.</span><span class="sxs-lookup"><span data-stu-id="7fce0-108">The syntax is like that of `let` bindings outside of classes, but the names defined in a class have a scope that is limited to the class.</span></span> <span data-ttu-id="7fce0-109">A `let` özel alan veya verileri açığa işlevi; bağlama oluşturur veya işlevleri genel olarak, bildirme bir özellik ya da bir üye yöntemi.</span><span class="sxs-lookup"><span data-stu-id="7fce0-109">A `let` binding creates a private field or function; to expose data or functions publicly, declare a property or a member method.</span></span>

<span data-ttu-id="7fce0-110">A `let` bağlaması değil örneği statik olarak adlandırılan `let` bağlama.</span><span class="sxs-lookup"><span data-stu-id="7fce0-110">A `let` binding that is not static is called an instance `let` binding.</span></span> <span data-ttu-id="7fce0-111">Örnek `let` bağlamaları nesneler oluşturulduğunda yürütün.</span><span class="sxs-lookup"><span data-stu-id="7fce0-111">Instance `let` bindings execute when objects are created.</span></span> <span data-ttu-id="7fce0-112">Statik `let` bağlamaları statik Başlatıcı türü ilk kullanılmadan önce yürütülecek garanti sınıf için bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="7fce0-112">Static `let` bindings are part of the static initializer for the class, which is guaranteed to execute before the type is first used.</span></span>

<span data-ttu-id="7fce0-113">Örnek içindeki kod `let` bağlamaları birincil Oluşturucusu 's parametrelerini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7fce0-113">The code within instance `let` bindings can use the primary constructor's parameters.</span></span>

<span data-ttu-id="7fce0-114">Öznitelikler ve erişilebilirlik değiştiricileri verilmez üzerinde `let` sınıflardaki bağlar.</span><span class="sxs-lookup"><span data-stu-id="7fce0-114">Attributes and accessibility modifiers are not permitted on `let` bindings in classes.</span></span>

<span data-ttu-id="7fce0-115">Aşağıdaki kod örneğinde çeşitli türlerde göstermeye `let` sınıflardaki bağlar.</span><span class="sxs-lookup"><span data-stu-id="7fce0-115">The following code examples illustrate several types of `let` bindings in classes.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3001.fs)]

<span data-ttu-id="7fce0-116">Çıktı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="7fce0-116">The output is as follows.</span></span>

```
10 52 1 204
```

## <a name="alternative-ways-to-create-fields"></a><span data-ttu-id="7fce0-117">Alanları oluşturmak için alternatif yöntemler</span><span class="sxs-lookup"><span data-stu-id="7fce0-117">Alternative Ways to Create Fields</span></span>
<span data-ttu-id="7fce0-118">Aynı zamanda `val` özel alanı oluşturmak için anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="7fce0-118">You can also use the `val` keyword to create a private field.</span></span> <span data-ttu-id="7fce0-119">Kullanırken `val` anahtar sözcüğü, alanın değil verilen bir değer nesnesi oluşturulur, ancak bunun yerine varsayılan bir değerle başlatılır.</span><span class="sxs-lookup"><span data-stu-id="7fce0-119">When using the `val` keyword, the field is not given a value when the object is created, but instead is initialized with a default value.</span></span> <span data-ttu-id="7fce0-120">Daha fazla bilgi için bkz: [açık alanlar: val anahtar sözcüğü](explicit-fields-the-val-keyword.md).</span><span class="sxs-lookup"><span data-stu-id="7fce0-120">For more information, see [Explicit Fields: The val Keyword](explicit-fields-the-val-keyword.md).</span></span>

<span data-ttu-id="7fce0-121">Ayrıca özel alanlar bir sınıfta bir üye tanımı kullanılarak ve anahtar sözcüğü ekleyerek tanımlayabilirsiniz `private` tanımı.</span><span class="sxs-lookup"><span data-stu-id="7fce0-121">You can also define private fields in a class by using a member definition and adding the keyword `private` to the definition.</span></span> <span data-ttu-id="7fce0-122">Bu üye erişilebilirliğini kodunuzu yeniden yazma işlemi değiştirmek bekliyorsanız yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="7fce0-122">This can be useful if you expect to change the accessibility of a member without rewriting your code.</span></span> <span data-ttu-id="7fce0-123">Daha fazla bilgi için bkz: [erişim denetimi](../access-control.md).</span><span class="sxs-lookup"><span data-stu-id="7fce0-123">For more information, see [Access Control](../access-control.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="7fce0-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7fce0-124">See Also</span></span>
[<span data-ttu-id="7fce0-125">Üyeler</span><span class="sxs-lookup"><span data-stu-id="7fce0-125">Members</span></span>](index.md)

[<span data-ttu-id="7fce0-126">`do` Sınıflardaki bağlamaları</span><span class="sxs-lookup"><span data-stu-id="7fce0-126">`do` Bindings in Classes</span></span>](do-bindings-in-classes.md)

[<span data-ttu-id="7fce0-127">`let` Bağlamaları</span><span class="sxs-lookup"><span data-stu-id="7fce0-127">`let` Bindings</span></span>](../functions/let-bindings.md)
