---
title: "Nesne İfadeleri (F#)"
description: "Ek kod ve yeni, oluşturmak için gerekli ek yükünü engellemek istediğinizde F # nesne ifadeleri kullanmayı türü adlı öğrenin."
keywords: "Visual f #, f # işlevsel programlama"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: c6dcf4c9-e7fd-4eee-9e4e-1176f4c27f57
ms.openlocfilehash: 28660d430473de02a8a55e37a26609827b364012
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="object-expressions"></a><span data-ttu-id="12af7-104">Nesne İfadeleri</span><span class="sxs-lookup"><span data-stu-id="12af7-104">Object Expressions</span></span>

<span data-ttu-id="12af7-105">Bir *nesne ifadesi* dinamik olarak oluşturulan, anonim nesne türü yeni bir örneğini oluşturan bir ifade bir varolan temel türü, arabirim veya arabirim kümesine dayalıdır.</span><span class="sxs-lookup"><span data-stu-id="12af7-105">An *object expression* is an expression that creates a new instance of a dynamically created, anonymous object type that is based on an existing base type, interface, or set of interfaces.</span></span>


## <a name="syntax"></a><span data-ttu-id="12af7-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="12af7-106">Syntax</span></span>

```fsharp
// When typename is a class:
{ new typename [type-params]arguments with
    member-definitions
    [ additional-interface-definitions ]
}
// When typename is not a class:
{ new typename [generic-type-args] with
    member-definitions
    [ additional-interface-definitions ]
}
```

## <a name="remarks"></a><span data-ttu-id="12af7-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="12af7-107">Remarks</span></span>
<span data-ttu-id="12af7-108">Önceki sözdiziminde *typename* varolan bir sınıf veya arabirim türü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="12af7-108">In the previous syntax, the *typename* represents an existing class type or interface type.</span></span> <span data-ttu-id="12af7-109">*Tür parametreleri* isteğe bağlı genel tür parametreleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="12af7-109">*type-params* describes the optional generic type parameters.</span></span> <span data-ttu-id="12af7-110">*Bağımsız değişkenleri* Oluşturucu parametreleri gerektiren yalnızca sınıf türleri için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="12af7-110">The *arguments* are used only for class types, which require constructor parameters.</span></span> <span data-ttu-id="12af7-111">*Üye tanımları* taban sınıf yöntemlerini, geçersiz kılmalar ya da bir taban sınıf veya arabirim soyut yöntemler uygulamaları.</span><span class="sxs-lookup"><span data-stu-id="12af7-111">The *member-definitions* are overrides of base class methods, or implementations of abstract methods from either a base class or an interface.</span></span>

<span data-ttu-id="12af7-112">Aşağıdaki örnek, birkaç farklı türde nesne ifadeleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="12af7-112">The following example illustrates several different types of object expressions.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4301.fs)]

## <a name="using-object-expressions"></a><span data-ttu-id="12af7-113">Nesne ifadeleri kullanma</span><span class="sxs-lookup"><span data-stu-id="12af7-113">Using Object Expressions</span></span>
<span data-ttu-id="12af7-114">Türü adlı gerekli yeni bir oluşturmak için ek yükü ve ek kod engellemek istediğinizde nesne ifadeleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="12af7-114">You use object expressions when you want to avoid the extra code and overhead that is required to create a new, named type.</span></span> <span data-ttu-id="12af7-115">Nesne ifadeleri bir programda oluşturulan türleri sayısını en aza indirmek için kullanırsanız, kod satırı sayısını azaltın ve türleri gereksiz artışı engelleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="12af7-115">If you use object expressions to minimize the number of types created in a program, you can reduce the number of lines of code and prevent the unnecessary proliferation of types.</span></span> <span data-ttu-id="12af7-116">Yalnızca özel durumları işlemek için birçok türleri oluşturmak yerine, mevcut bir türle özelleştirir veya elinizdeki belirli çalışması için uygun bir uygulaması, bir arabirim sağlayan bir nesne ifadesi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="12af7-116">Instead of creating many types just to handle specific situations, you can use an object expression that customizes an existing type or provides an appropriate implementation of an interface for the specific case at hand.</span></span>


## <a name="see-also"></a><span data-ttu-id="12af7-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="12af7-117">See Also</span></span>
[<span data-ttu-id="12af7-118">F # dili başvurusu</span><span class="sxs-lookup"><span data-stu-id="12af7-118">F# Language Reference</span></span>](index.md)
