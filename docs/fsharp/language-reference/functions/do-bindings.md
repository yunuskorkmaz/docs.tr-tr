---
title: do Bağlamaları
description: Bilgi nasıl bir F# 'do binding' bir işlev veya değer tanımlamadan kod yürütmek için kullanılır.
ms.date: 05/16/2016
ms.openlocfilehash: d29f8557fda06097d2e85748ab6286f0415730b3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61683385"
---
# <a name="do-bindings"></a><span data-ttu-id="5c27e-103">do Bağlamaları</span><span class="sxs-lookup"><span data-stu-id="5c27e-103">do Bindings</span></span>

<span data-ttu-id="5c27e-104">A `do` bağlama, bir işlev veya değer tanımlamadan kod yürütmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5c27e-104">A `do` binding is used to execute code without defining a function or value.</span></span> <span data-ttu-id="5c27e-105">Ayrıca, bağlamaları olabilir misiniz sınıflarda kullanıldığında, bkz: [ `do` sınıflardaki bağlamaları](../members/do-bindings-in-classes.md).</span><span class="sxs-lookup"><span data-stu-id="5c27e-105">Also, do bindings can be used in classes, see [`do` Bindings in Classes](../members/do-bindings-in-classes.md).</span></span>

## <a name="syntax"></a><span data-ttu-id="5c27e-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5c27e-106">Syntax</span></span>

```fsharp
[ attributes ]
[ do ]expression
```

## <a name="remarks"></a><span data-ttu-id="5c27e-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5c27e-107">Remarks</span></span>

<span data-ttu-id="5c27e-108">Kullanım bir `do` bir işlev veya değer tanımı bağımsız olarak kod yürütmek istediğiniz zaman bağlama.</span><span class="sxs-lookup"><span data-stu-id="5c27e-108">Use a `do` binding when you want to execute code independently of a function or value definition.</span></span> <span data-ttu-id="5c27e-109">İfade bir `do` bağlama döndürmelidir `unit`.</span><span class="sxs-lookup"><span data-stu-id="5c27e-109">The expression in a `do` binding must return `unit`.</span></span> <span data-ttu-id="5c27e-110">En üst düzey bir kod `do` bağlama modülü başlatıldığında yürütülür.</span><span class="sxs-lookup"><span data-stu-id="5c27e-110">Code in a top-level `do` binding is executed when the module is initialized.</span></span> <span data-ttu-id="5c27e-111">Anahtar sözcüğü `do` isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="5c27e-111">The keyword `do` is optional.</span></span>

<span data-ttu-id="5c27e-112">Öznitelikleri uygulanabilir için üst düzey `do` bağlama.</span><span class="sxs-lookup"><span data-stu-id="5c27e-112">Attributes can be applied to a top-level `do` binding.</span></span> <span data-ttu-id="5c27e-113">Örneğin, programınız COM birlikte çalışma kullanıyorsa, uygulamak isteyebilirsiniz `STAThread` programınıza özniteliği.</span><span class="sxs-lookup"><span data-stu-id="5c27e-113">For example, if your program uses COM interop, you might want to apply the `STAThread` attribute to your program.</span></span> <span data-ttu-id="5c27e-114">Bir öznitelik kullanarak bunu yapabilirsiniz bir `do` aşağıdaki kodda gösterildiği gibi bağlama.</span><span class="sxs-lookup"><span data-stu-id="5c27e-114">You can do this by using an attribute on a `do` binding, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet201.fs)]

## <a name="see-also"></a><span data-ttu-id="5c27e-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5c27e-115">See also</span></span>

- [<span data-ttu-id="5c27e-116">F# Dili Başvurusu</span><span class="sxs-lookup"><span data-stu-id="5c27e-116">F# Language Reference</span></span>](../index.md)
- [<span data-ttu-id="5c27e-117">İşlevler</span><span class="sxs-lookup"><span data-stu-id="5c27e-117">Functions</span></span>](index.md)