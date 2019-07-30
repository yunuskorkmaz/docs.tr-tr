---
title: do Bağlamaları
description: Bir işlev veya F# değer tanımlamadan kodu yürütmek için bir ' do ' bağlamasının nasıl kullanıldığını öğrenin.
ms.date: 05/16/2016
ms.openlocfilehash: f98f523296bfaceeda35d4861eafbfeaa5a60c32
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630533"
---
# <a name="do-bindings"></a><span data-ttu-id="3207e-103">do Bağlamaları</span><span class="sxs-lookup"><span data-stu-id="3207e-103">do Bindings</span></span>

<span data-ttu-id="3207e-104">Bir `do` bağlama, bir işlev veya değer tanımlamadan kodu yürütmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3207e-104">A `do` binding is used to execute code without defining a function or value.</span></span> <span data-ttu-id="3207e-105">Ayrıca, do bağlamaları sınıflarda kullanılabilir, bkz [ `do` . sınıflarda bağlamalar](../members/do-bindings-in-classes.md).</span><span class="sxs-lookup"><span data-stu-id="3207e-105">Also, do bindings can be used in classes, see [`do` Bindings in Classes](../members/do-bindings-in-classes.md).</span></span>

## <a name="syntax"></a><span data-ttu-id="3207e-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3207e-106">Syntax</span></span>

```fsharp
[ attributes ]
[ do ]expression
```

## <a name="remarks"></a><span data-ttu-id="3207e-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3207e-107">Remarks</span></span>

<span data-ttu-id="3207e-108">Kodu bir `do` işlevden veya değer tanımından bağımsız olarak yürütmek istediğinizde bir bağlama kullanın.</span><span class="sxs-lookup"><span data-stu-id="3207e-108">Use a `do` binding when you want to execute code independently of a function or value definition.</span></span> <span data-ttu-id="3207e-109">Bir `do` bağlamadaki ifade döndürmelidir `unit`.</span><span class="sxs-lookup"><span data-stu-id="3207e-109">The expression in a `do` binding must return `unit`.</span></span> <span data-ttu-id="3207e-110">Üst düzey `do` bağlamadaki kod, modül başlatıldığında yürütülür.</span><span class="sxs-lookup"><span data-stu-id="3207e-110">Code in a top-level `do` binding is executed when the module is initialized.</span></span> <span data-ttu-id="3207e-111">Anahtar sözcüğü `do` isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="3207e-111">The keyword `do` is optional.</span></span>

<span data-ttu-id="3207e-112">Öznitelikler, üst düzey `do` bağlamaya uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="3207e-112">Attributes can be applied to a top-level `do` binding.</span></span> <span data-ttu-id="3207e-113">Örneğin, programınız com birlikte çalışabilirliği kullanıyorsa, bu `STAThread` özniteliği programınıza uygulamak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3207e-113">For example, if your program uses COM interop, you might want to apply the `STAThread` attribute to your program.</span></span> <span data-ttu-id="3207e-114">Bunu, aşağıdaki kodda gösterildiği gibi `do` bağlamadaki bir özniteliği kullanarak yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3207e-114">You can do this by using an attribute on a `do` binding, as shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet201.fs)]

## <a name="see-also"></a><span data-ttu-id="3207e-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3207e-115">See also</span></span>

- [<span data-ttu-id="3207e-116">F# Dili Başvurusu</span><span class="sxs-lookup"><span data-stu-id="3207e-116">F# Language Reference</span></span>](../index.md)
- [<span data-ttu-id="3207e-117">İşlevler</span><span class="sxs-lookup"><span data-stu-id="3207e-117">Functions</span></span>](index.md)
