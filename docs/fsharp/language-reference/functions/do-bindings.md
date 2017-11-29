---
title: "do Bağlamaları (F#)"
description: "F # 'bağlaması yapma' bir işlevi veya değer tanımlamadan kod yürütmek için nasıl kullanıldığı hakkında bilgi edinin."
keywords: "Visual f #, f # işlevsel programlama"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 4c1057a3-3aa1-4b64-b46a-25ffe33f0be9
ms.openlocfilehash: f2563d384b67c005c96c2ff487c786476d385e70
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="do-bindings"></a><span data-ttu-id="e1d29-104">do Bağlamaları</span><span class="sxs-lookup"><span data-stu-id="e1d29-104">do Bindings</span></span>

<span data-ttu-id="e1d29-105">A `do` bağlama bir işlevi veya değer tanımlamadan kod yürütmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e1d29-105">A `do` binding is used to execute code without defining a function or value.</span></span> <span data-ttu-id="e1d29-106">Ayrıca, bağlamaları olabilir yapmak sınıflarda kullanıldığında, bkz: [ `do` sınıflardaki bağlamaları](../members/do-bindings-in-classes.md).</span><span class="sxs-lookup"><span data-stu-id="e1d29-106">Also, do bindings can be used in classes, see [`do` Bindings in Classes](../members/do-bindings-in-classes.md).</span></span>


## <a name="syntax"></a><span data-ttu-id="e1d29-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e1d29-107">Syntax</span></span>

```fsharp
[ attributes ]
[ do ]expression
```

## <a name="remarks"></a><span data-ttu-id="e1d29-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e1d29-108">Remarks</span></span>
<span data-ttu-id="e1d29-109">Kullanım bir `do` bir işlevi veya değer tanımı bağımsız olarak kod yürütmek istediğinizde bağlama.</span><span class="sxs-lookup"><span data-stu-id="e1d29-109">Use a `do` binding when you want to execute code independently of a function or value definition.</span></span> <span data-ttu-id="e1d29-110">İfade bir `do` bağlama döndürmelidir `unit`.</span><span class="sxs-lookup"><span data-stu-id="e1d29-110">The expression in a `do` binding must return `unit`.</span></span> <span data-ttu-id="e1d29-111">Kodda bir üst düzey `do` bağlama modül başlatıldığında gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="e1d29-111">Code in a top-level `do` binding is executed when the module is initialized.</span></span> <span data-ttu-id="e1d29-112">Anahtar sözcüğü `do` isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="e1d29-112">The keyword `do` is optional.</span></span>

<span data-ttu-id="e1d29-113">Öznitelikleri uygulanabilir için üst düzey `do` bağlama.</span><span class="sxs-lookup"><span data-stu-id="e1d29-113">Attributes can be applied to a top-level `do` binding.</span></span> <span data-ttu-id="e1d29-114">Örneğin, programınızı COM birlikte çalışma kullanıyorsa, uygulamak isteyebilirsiniz `STAThread` programınıza özniteliği.</span><span class="sxs-lookup"><span data-stu-id="e1d29-114">For example, if your program uses COM interop, you might want to apply the `STAThread` attribute to your program.</span></span> <span data-ttu-id="e1d29-115">Bir öznitelik kullanarak bunu yapabilirsiniz bir `do` aşağıdaki kodda gösterildiği gibi bağlama.</span><span class="sxs-lookup"><span data-stu-id="e1d29-115">You can do this by using an attribute on a `do` binding, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet201.fs)]
    
## <a name="see-also"></a><span data-ttu-id="e1d29-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e1d29-116">See Also</span></span>
[<span data-ttu-id="e1d29-117">F # dili başvurusu</span><span class="sxs-lookup"><span data-stu-id="e1d29-117">F# Language Reference</span></span>](../index.md)

[<span data-ttu-id="e1d29-118">İşlevler</span><span class="sxs-lookup"><span data-stu-id="e1d29-118">Functions</span></span>](index.md)

