---
title: Sınıflardaki let Bağlamaları (F#)
description: "Özel alanlar ve F # sınıfları için özel işlevler sınıf tanımında 'let' bağlamaları kullanarak tanımlamayı öğrenin."
ms.date: 05/16/2016
ms.openlocfilehash: 237eb98a57571a21c9187abf31f05160374cf4fc
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43866799"
---
# <a name="let-bindings-in-classes"></a><span data-ttu-id="f7574-103">Sınıflardaki let Bağlamaları</span><span class="sxs-lookup"><span data-stu-id="f7574-103">let Bindings in Classes</span></span>

<span data-ttu-id="f7574-104">Özel alanlar ve özel işlevler için F # sınıfları kullanarak tanımlayabilirsiniz `let` sınıf tanımında bağlar.</span><span class="sxs-lookup"><span data-stu-id="f7574-104">You can define private fields and private functions for F# classes by using `let` bindings in the class definition.</span></span>

## <a name="syntax"></a><span data-ttu-id="f7574-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f7574-105">Syntax</span></span>

```fsharp
// Field.
[static] let [ mutable ] binding1 [ and ... binding-n ]

// Function.
[static] let [ rec ] binding1 [ and ... binding-n ]
```

## <a name="remarks"></a><span data-ttu-id="f7574-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f7574-106">Remarks</span></span>

<span data-ttu-id="f7574-107">Önceki sözdizimini, başlık ve devralma sınıf bildirimleri sonra ancak herhangi bir üye tanımı önce görünür.</span><span class="sxs-lookup"><span data-stu-id="f7574-107">The previous syntax appears after the class heading and inheritance declarations but before any member definitions.</span></span> <span data-ttu-id="f7574-108">Söz dizimi şu şekildedir gibi `let` bağlamaları sınıfları, ancak bir sınıfta tanımlanan adlar dışında sınıfa sınırlı kapsamı vardır.</span><span class="sxs-lookup"><span data-stu-id="f7574-108">The syntax is like that of `let` bindings outside of classes, but the names defined in a class have a scope that is limited to the class.</span></span> <span data-ttu-id="f7574-109">A `let` bağlama, bir özel alan veya verileri ortaya çıkarmak için işlev; oluşturur veya işlevleri genel olarak, bir özellik veya bir üye yöntem bildirin.</span><span class="sxs-lookup"><span data-stu-id="f7574-109">A `let` binding creates a private field or function; to expose data or functions publicly, declare a property or a member method.</span></span>

<span data-ttu-id="f7574-110">A `let` bağlama değil örneği statik olarak adlandırılan `let` bağlama.</span><span class="sxs-lookup"><span data-stu-id="f7574-110">A `let` binding that is not static is called an instance `let` binding.</span></span> <span data-ttu-id="f7574-111">Örnek `let` bağlamaları yürütmek nesneler oluşturulduğunda.</span><span class="sxs-lookup"><span data-stu-id="f7574-111">Instance `let` bindings execute when objects are created.</span></span> <span data-ttu-id="f7574-112">Statik `let` bağlamaları türü ilk kez kullanılmadan önce yürütülecek garanti sınıfı için statik Başlatıcı bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="f7574-112">Static `let` bindings are part of the static initializer for the class, which is guaranteed to execute before the type is first used.</span></span>

<span data-ttu-id="f7574-113">Kod örneği içinde `let` bağlamaları birincil oluşturucunun parametreleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f7574-113">The code within instance `let` bindings can use the primary constructor's parameters.</span></span>

<span data-ttu-id="f7574-114">Öznitelikler ve erişilebilirlik değiştiricileri verilmez üzerinde `let` sınıflardaki bağlar.</span><span class="sxs-lookup"><span data-stu-id="f7574-114">Attributes and accessibility modifiers are not permitted on `let` bindings in classes.</span></span>

<span data-ttu-id="f7574-115">Aşağıdaki kod örnekleri birkaç türde göstermek `let` sınıflardaki bağlar.</span><span class="sxs-lookup"><span data-stu-id="f7574-115">The following code examples illustrate several types of `let` bindings in classes.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3001.fs)]

<span data-ttu-id="f7574-116">Çıktı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="f7574-116">The output is as follows.</span></span>

```
10 52 1 204
```

## <a name="alternative-ways-to-create-fields"></a><span data-ttu-id="f7574-117">Alanları oluşturmak için alternatif yollar</span><span class="sxs-lookup"><span data-stu-id="f7574-117">Alternative Ways to Create Fields</span></span>

<span data-ttu-id="f7574-118">Ayrıca `val` özel bir alan oluşturmak için anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="f7574-118">You can also use the `val` keyword to create a private field.</span></span> <span data-ttu-id="f7574-119">Kullanırken `val` anahtar sözcüğü, alan verilmemiş bir değer nesnesi oluşturulur, ancak bunun yerine varsayılan bir değerle başlatılır.</span><span class="sxs-lookup"><span data-stu-id="f7574-119">When using the `val` keyword, the field is not given a value when the object is created, but instead is initialized with a default value.</span></span> <span data-ttu-id="f7574-120">Daha fazla bilgi için [açık alanlar: val anahtar sözcüğü](explicit-fields-the-val-keyword.md).</span><span class="sxs-lookup"><span data-stu-id="f7574-120">For more information, see [Explicit Fields: The val Keyword](explicit-fields-the-val-keyword.md).</span></span>

<span data-ttu-id="f7574-121">Ayrıca özel alanlar bir sınıfta bir üye tanımı kullanarak ve anahtar sözcüğü ekleyerek tanımlayabilirsiniz `private` tanımına.</span><span class="sxs-lookup"><span data-stu-id="f7574-121">You can also define private fields in a class by using a member definition and adding the keyword `private` to the definition.</span></span> <span data-ttu-id="f7574-122">Bu, kodunuzu yeniden yazma olmadan bir üyenin erişilebilirliğini değiştirmek bekliyorsanız yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="f7574-122">This can be useful if you expect to change the accessibility of a member without rewriting your code.</span></span> <span data-ttu-id="f7574-123">Daha fazla bilgi için [erişim denetimi](../access-control.md).</span><span class="sxs-lookup"><span data-stu-id="f7574-123">For more information, see [Access Control](../access-control.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f7574-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f7574-124">See also</span></span>

- [<span data-ttu-id="f7574-125">Üyeler</span><span class="sxs-lookup"><span data-stu-id="f7574-125">Members</span></span>](index.md)
- [<span data-ttu-id="f7574-126">`do` Sınıflardaki bağlamaları</span><span class="sxs-lookup"><span data-stu-id="f7574-126">`do` Bindings in Classes</span></span>](do-bindings-in-classes.md)
- [<span data-ttu-id="f7574-127">`let` Bağlamaları</span><span class="sxs-lookup"><span data-stu-id="f7574-127">`let` Bindings</span></span>](../functions/let-bindings.md)
