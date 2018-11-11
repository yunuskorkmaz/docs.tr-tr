---
title: Nesne İfadeleri (F#)
description: Türü adlı ek bir kod ve yeni, oluşturmak için gereken ek yükü önlemek istediğinizde F# nesne ifadeleri kullanmayı öğrenin.
ms.date: 05/16/2016
ms.openlocfilehash: 1a971044d680d3bf5a6fff38affdaf001d5403b4
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/02/2018
ms.locfileid: "43865468"
---
# <a name="object-expressions"></a><span data-ttu-id="284db-103">Nesne İfadeleri</span><span class="sxs-lookup"><span data-stu-id="284db-103">Object Expressions</span></span>

<span data-ttu-id="284db-104">Bir *ifade nesne* dinamik olarak oluşturulmuş, anonim nesne türü yeni bir örneğini oluşturan bir ifade bir var olan temel tür, arabirim veya arabirimleri kümesi bağlı.</span><span class="sxs-lookup"><span data-stu-id="284db-104">An *object expression* is an expression that creates a new instance of a dynamically created, anonymous object type that is based on an existing base type, interface, or set of interfaces.</span></span>

## <a name="syntax"></a><span data-ttu-id="284db-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="284db-105">Syntax</span></span>

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

## <a name="remarks"></a><span data-ttu-id="284db-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="284db-106">Remarks</span></span>

<span data-ttu-id="284db-107">Önceki sözdiziminde, *typename* var olan bir sınıf veya arabirim türü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="284db-107">In the previous syntax, the *typename* represents an existing class type or interface type.</span></span> <span data-ttu-id="284db-108">*Tür parametreleri* isteğe bağlı bir genel tür parametreleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="284db-108">*type-params* describes the optional generic type parameters.</span></span> <span data-ttu-id="284db-109">*Bağımsız değişkenleri* Oluşturucu parametresi gerektiren yalnızca sınıf türleri için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="284db-109">The *arguments* are used only for class types, which require constructor parameters.</span></span> <span data-ttu-id="284db-110">*Üye tanımları* taban sınıf yöntemlerini geçersiz kılmalarına ya da soyut yöntemler bir temel sınıf veya arabirim uygulamaları.</span><span class="sxs-lookup"><span data-stu-id="284db-110">The *member-definitions* are overrides of base class methods, or implementations of abstract methods from either a base class or an interface.</span></span>

<span data-ttu-id="284db-111">Aşağıdaki örnek, birkaç farklı türde nesne ifadeleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="284db-111">The following example illustrates several different types of object expressions.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4301.fs)]

## <a name="using-object-expressions"></a><span data-ttu-id="284db-112">Nesne ifadeleri kullanma</span><span class="sxs-lookup"><span data-stu-id="284db-112">Using Object Expressions</span></span>

<span data-ttu-id="284db-113">Nesne ifadeleri, ek bir kod ve tür adında gereken yeni, ek yükü önlemek istediğinizde kullanın.</span><span class="sxs-lookup"><span data-stu-id="284db-113">You use object expressions when you want to avoid the extra code and overhead that is required to create a new, named type.</span></span> <span data-ttu-id="284db-114">Nesne ifadeleri bir programında oluşturulan türleri sayısını en aza indirmek için kullanırsanız, kod satırı sayısını azaltın ve türleri gereksiz çoğalan engelle.</span><span class="sxs-lookup"><span data-stu-id="284db-114">If you use object expressions to minimize the number of types created in a program, you can reduce the number of lines of code and prevent the unnecessary proliferation of types.</span></span> <span data-ttu-id="284db-115">Yalnızca özel durumları işlemek için birçok türleri oluşturmak yerine var olan bir türü özelleştirir veya bir arabirimin uygun uygulama eldeki özel durum sağlayan bir nesne ifadesi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="284db-115">Instead of creating many types just to handle specific situations, you can use an object expression that customizes an existing type or provides an appropriate implementation of an interface for the specific case at hand.</span></span>

## <a name="see-also"></a><span data-ttu-id="284db-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="284db-116">See also</span></span>

- [<span data-ttu-id="284db-117">F# Dili Başvurusu</span><span class="sxs-lookup"><span data-stu-id="284db-117">F# Language Reference</span></span>](index.md)
