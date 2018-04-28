---
title: do Bağlamaları (F#)
description: "F # 'bağlaması yapma' bir işlevi veya değer tanımlamadan kod yürütmek için nasıl kullanıldığı hakkında bilgi edinin."
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 4c63da0c5e2f4130d59f9efa6bc54a55e5fe9fd8
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="do-bindings"></a><span data-ttu-id="33aae-103">do Bağlamaları</span><span class="sxs-lookup"><span data-stu-id="33aae-103">do Bindings</span></span>

<span data-ttu-id="33aae-104">A `do` bağlama bir işlevi veya değer tanımlamadan kod yürütmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="33aae-104">A `do` binding is used to execute code without defining a function or value.</span></span> <span data-ttu-id="33aae-105">Ayrıca, bağlamaları olabilir yapmak sınıflarda kullanıldığında, bkz: [ `do` sınıflardaki bağlamaları](../members/do-bindings-in-classes.md).</span><span class="sxs-lookup"><span data-stu-id="33aae-105">Also, do bindings can be used in classes, see [`do` Bindings in Classes](../members/do-bindings-in-classes.md).</span></span>


## <a name="syntax"></a><span data-ttu-id="33aae-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="33aae-106">Syntax</span></span>

```fsharp
[ attributes ]
[ do ]expression
```

## <a name="remarks"></a><span data-ttu-id="33aae-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="33aae-107">Remarks</span></span>
<span data-ttu-id="33aae-108">Kullanım bir `do` bir işlevi veya değer tanımı bağımsız olarak kod yürütmek istediğinizde bağlama.</span><span class="sxs-lookup"><span data-stu-id="33aae-108">Use a `do` binding when you want to execute code independently of a function or value definition.</span></span> <span data-ttu-id="33aae-109">İfade bir `do` bağlama döndürmelidir `unit`.</span><span class="sxs-lookup"><span data-stu-id="33aae-109">The expression in a `do` binding must return `unit`.</span></span> <span data-ttu-id="33aae-110">Kodda bir üst düzey `do` bağlama modül başlatıldığında gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="33aae-110">Code in a top-level `do` binding is executed when the module is initialized.</span></span> <span data-ttu-id="33aae-111">Anahtar sözcüğü `do` isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="33aae-111">The keyword `do` is optional.</span></span>

<span data-ttu-id="33aae-112">Öznitelikleri uygulanabilir için üst düzey `do` bağlama.</span><span class="sxs-lookup"><span data-stu-id="33aae-112">Attributes can be applied to a top-level `do` binding.</span></span> <span data-ttu-id="33aae-113">Örneğin, programınızı COM birlikte çalışma kullanıyorsa, uygulamak isteyebilirsiniz `STAThread` programınıza özniteliği.</span><span class="sxs-lookup"><span data-stu-id="33aae-113">For example, if your program uses COM interop, you might want to apply the `STAThread` attribute to your program.</span></span> <span data-ttu-id="33aae-114">Bir öznitelik kullanarak bunu yapabilirsiniz bir `do` aşağıdaki kodda gösterildiği gibi bağlama.</span><span class="sxs-lookup"><span data-stu-id="33aae-114">You can do this by using an attribute on a `do` binding, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet201.fs)]
    
## <a name="see-also"></a><span data-ttu-id="33aae-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="33aae-115">See Also</span></span>
[<span data-ttu-id="33aae-116">F# Dili Başvurusu</span><span class="sxs-lookup"><span data-stu-id="33aae-116">F# Language Reference</span></span>](../index.md)

[<span data-ttu-id="33aae-117">İşlevler</span><span class="sxs-lookup"><span data-stu-id="33aae-117">Functions</span></span>](index.md)

