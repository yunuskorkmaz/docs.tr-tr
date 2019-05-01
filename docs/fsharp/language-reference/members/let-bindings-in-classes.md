---
title: Sınıflardaki let Bağlamaları
description: Özel alanlar ve özel işlevler için tanımlamayı öğrenin F# kullanarak sınıfları 'let' sınıf tanımında bağlar.
ms.date: 05/16/2016
ms.openlocfilehash: 03dd583a141971284e6a8ddaad02272236cd1e4c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61903778"
---
# <a name="let-bindings-in-classes"></a><span data-ttu-id="1cac9-103">Sınıflardaki let Bağlamaları</span><span class="sxs-lookup"><span data-stu-id="1cac9-103">let Bindings in Classes</span></span>

<span data-ttu-id="1cac9-104">Özel alanlar ve özel işlevler için tanımlayabileceğiniz F# sınıfları kullanarak `let` sınıf tanımında bağlar.</span><span class="sxs-lookup"><span data-stu-id="1cac9-104">You can define private fields and private functions for F# classes by using `let` bindings in the class definition.</span></span>

## <a name="syntax"></a><span data-ttu-id="1cac9-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1cac9-105">Syntax</span></span>

```fsharp
// Field.
[static] let [ mutable ] binding1 [ and ... binding-n ]

// Function.
[static] let [ rec ] binding1 [ and ... binding-n ]
```

## <a name="remarks"></a><span data-ttu-id="1cac9-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1cac9-106">Remarks</span></span>

<span data-ttu-id="1cac9-107">Önceki sözdizimini, başlık ve devralma sınıf bildirimleri sonra ancak herhangi bir üye tanımı önce görünür.</span><span class="sxs-lookup"><span data-stu-id="1cac9-107">The previous syntax appears after the class heading and inheritance declarations but before any member definitions.</span></span> <span data-ttu-id="1cac9-108">Söz dizimi şu şekildedir gibi `let` bağlamaları sınıfları, ancak bir sınıfta tanımlanan adlar dışında sınıfa sınırlı kapsamı vardır.</span><span class="sxs-lookup"><span data-stu-id="1cac9-108">The syntax is like that of `let` bindings outside of classes, but the names defined in a class have a scope that is limited to the class.</span></span> <span data-ttu-id="1cac9-109">A `let` bağlama, bir özel alan veya verileri ortaya çıkarmak için işlev; oluşturur veya işlevleri genel olarak, bir özellik veya bir üye yöntem bildirin.</span><span class="sxs-lookup"><span data-stu-id="1cac9-109">A `let` binding creates a private field or function; to expose data or functions publicly, declare a property or a member method.</span></span>

<span data-ttu-id="1cac9-110">A `let` bağlama değil örneği statik olarak adlandırılan `let` bağlama.</span><span class="sxs-lookup"><span data-stu-id="1cac9-110">A `let` binding that is not static is called an instance `let` binding.</span></span> <span data-ttu-id="1cac9-111">Örnek `let` bağlamaları yürütmek nesneler oluşturulduğunda.</span><span class="sxs-lookup"><span data-stu-id="1cac9-111">Instance `let` bindings execute when objects are created.</span></span> <span data-ttu-id="1cac9-112">Statik `let` bağlamaları türü ilk kez kullanılmadan önce yürütülecek garanti sınıfı için statik Başlatıcı bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="1cac9-112">Static `let` bindings are part of the static initializer for the class, which is guaranteed to execute before the type is first used.</span></span>

<span data-ttu-id="1cac9-113">Kod örneği içinde `let` bağlamaları birincil oluşturucunun parametreleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1cac9-113">The code within instance `let` bindings can use the primary constructor's parameters.</span></span>

<span data-ttu-id="1cac9-114">Öznitelikler ve erişilebilirlik değiştiricileri verilmez üzerinde `let` sınıflardaki bağlar.</span><span class="sxs-lookup"><span data-stu-id="1cac9-114">Attributes and accessibility modifiers are not permitted on `let` bindings in classes.</span></span>

<span data-ttu-id="1cac9-115">Aşağıdaki kod örnekleri birkaç türde göstermek `let` sınıflardaki bağlar.</span><span class="sxs-lookup"><span data-stu-id="1cac9-115">The following code examples illustrate several types of `let` bindings in classes.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3001.fs)]

<span data-ttu-id="1cac9-116">Çıktı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="1cac9-116">The output is as follows.</span></span>

```
10 52 1 204
```

## <a name="alternative-ways-to-create-fields"></a><span data-ttu-id="1cac9-117">Alanları oluşturmak için alternatif yollar</span><span class="sxs-lookup"><span data-stu-id="1cac9-117">Alternative Ways to Create Fields</span></span>

<span data-ttu-id="1cac9-118">Ayrıca `val` özel bir alan oluşturmak için anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="1cac9-118">You can also use the `val` keyword to create a private field.</span></span> <span data-ttu-id="1cac9-119">Kullanırken `val` anahtar sözcüğü, alan verilmemiş bir değer nesnesi oluşturulur, ancak bunun yerine varsayılan bir değerle başlatılır.</span><span class="sxs-lookup"><span data-stu-id="1cac9-119">When using the `val` keyword, the field is not given a value when the object is created, but instead is initialized with a default value.</span></span> <span data-ttu-id="1cac9-120">Daha fazla bilgi için [açık alanlar: Val anahtar sözcüğü](explicit-fields-the-val-keyword.md).</span><span class="sxs-lookup"><span data-stu-id="1cac9-120">For more information, see [Explicit Fields: The val Keyword](explicit-fields-the-val-keyword.md).</span></span>

<span data-ttu-id="1cac9-121">Ayrıca özel alanlar bir sınıfta bir üye tanımı kullanarak ve anahtar sözcüğü ekleyerek tanımlayabilirsiniz `private` tanımına.</span><span class="sxs-lookup"><span data-stu-id="1cac9-121">You can also define private fields in a class by using a member definition and adding the keyword `private` to the definition.</span></span> <span data-ttu-id="1cac9-122">Bu, kodunuzu yeniden yazma olmadan bir üyenin erişilebilirliğini değiştirmek bekliyorsanız yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="1cac9-122">This can be useful if you expect to change the accessibility of a member without rewriting your code.</span></span> <span data-ttu-id="1cac9-123">Daha fazla bilgi için [erişim denetimi](../access-control.md).</span><span class="sxs-lookup"><span data-stu-id="1cac9-123">For more information, see [Access Control](../access-control.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1cac9-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1cac9-124">See also</span></span>

- [<span data-ttu-id="1cac9-125">Üyeler</span><span class="sxs-lookup"><span data-stu-id="1cac9-125">Members</span></span>](index.md)
- [<span data-ttu-id="1cac9-126">`do` Sınıflardaki bağlamaları</span><span class="sxs-lookup"><span data-stu-id="1cac9-126">`do` Bindings in Classes</span></span>](do-bindings-in-classes.md)
- [<span data-ttu-id="1cac9-127">`let` Bağlamaları</span><span class="sxs-lookup"><span data-stu-id="1cac9-127">`let` Bindings</span></span>](../functions/let-bindings.md)