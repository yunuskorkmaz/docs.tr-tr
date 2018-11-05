---
title: Temsilciler (F#)
description: 'Temsilciler F # ile çalışmayı öğrenin.'
ms.date: 05/16/2016
ms.openlocfilehash: be58997dffe8fcd949bbc2d47d86ffccc157d43e
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/02/2018
ms.locfileid: "45745500"
---
# <a name="delegates"></a><span data-ttu-id="c36ba-103">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="c36ba-103">Delegates</span></span>

<span data-ttu-id="c36ba-104">Bir temsilci, bir nesne olarak bir işlev çağrısını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="c36ba-104">A delegate represents a function call as an object.</span></span> <span data-ttu-id="c36ba-105">F # programında, genellikle işlev değerleri ilk sınıf değerleri olarak işlevler temsil etmek için kullanmanız gerekir; Ancak, temsilciler .NET Framework'teki kullanılır ve bunları beklediğiniz API'leri ile birlikte çalışmak, bu nedenle gereklidir.</span><span class="sxs-lookup"><span data-stu-id="c36ba-105">In F#, you ordinarily should use function values to represent functions as first-class values; however, delegates are used in the .NET Framework and so are needed when you interoperate with APIs that expect them.</span></span> <span data-ttu-id="c36ba-106">Geliştirme kitaplıkları için tasarlanan diğer .NET Framework dillerde kullandığınızda da kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c36ba-106">They may also be used when authoring libraries designed for use from other .NET Framework languages.</span></span>

## <a name="syntax"></a><span data-ttu-id="c36ba-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c36ba-107">Syntax</span></span>

```fsharp
type delegate-typename = delegate of type1 -> type2
```

## <a name="remarks"></a><span data-ttu-id="c36ba-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c36ba-108">Remarks</span></span>

<span data-ttu-id="c36ba-109">Önceki sözdiziminde, `type1` bağımsız değişken türü veya türleri temsil eder ve `type2` dönüş türünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="c36ba-109">In the previous syntax, `type1` represents the argument type or types and `type2` represents the return type.</span></span> <span data-ttu-id="c36ba-110">Tarafından temsil edilen bağımsız değişken türleri `type1` otomatik olarak curried.</span><span class="sxs-lookup"><span data-stu-id="c36ba-110">The argument types that are represented by `type1` are automatically curried.</span></span> <span data-ttu-id="c36ba-111">Bu, bu tür hedef işlevinin bağımsız değişkenleri curried bir tanımlama grubu form kullanmanızı ve parantez içine alınmış demet tanımlama grubu biçiminde olan bağımsız değişkenler için önerir.</span><span class="sxs-lookup"><span data-stu-id="c36ba-111">This suggests that for this type you use a tuple form if the arguments of the target function are curried, and a parenthesized tuple for arguments that are already in the tuple form.</span></span> <span data-ttu-id="c36ba-112">Otomatik currying hedef yöntemin eşleşen bir tanımlama grubu bağımsız değişkenini bırakarak, parantez kümesi kaldırır.</span><span class="sxs-lookup"><span data-stu-id="c36ba-112">The automatic currying removes a set of parentheses, leaving a tuple argument that matches the target method.</span></span> <span data-ttu-id="c36ba-113">Her durumda kullanmalısınız söz dizimi kod örneğine bakın.</span><span class="sxs-lookup"><span data-stu-id="c36ba-113">Refer to the code example for the syntax you should use in each case.</span></span>

<span data-ttu-id="c36ba-114">Temsilciler, F # işlev değerleri olarak ve statik eklenebilecek veya örnek yöntemler.</span><span class="sxs-lookup"><span data-stu-id="c36ba-114">Delegates can be attached to F# function values, and static or instance methods.</span></span> <span data-ttu-id="c36ba-115">F # işlev değerleri oluşturucuları temsilci olarak doğrudan bağımsız değişken olarak geçirilebilir.</span><span class="sxs-lookup"><span data-stu-id="c36ba-115">F# function values can be passed directly as arguments to delegate constructors.</span></span> <span data-ttu-id="c36ba-116">Statik bir yöntem için temsilci sınıf ve yöntem adını kullanarak oluşturun.</span><span class="sxs-lookup"><span data-stu-id="c36ba-116">For a static method, you construct the delegate by using the name of the class and the method.</span></span> <span data-ttu-id="c36ba-117">Bir örnek yöntemi için nesne örneği ve bir bağımsız değişkende yöntemi sağlar.</span><span class="sxs-lookup"><span data-stu-id="c36ba-117">For an instance method, you provide the object instance and method in one argument.</span></span> <span data-ttu-id="c36ba-118">Her iki durumda da, üye erişim işleci (`.`) kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c36ba-118">In both cases, the member access operator (`.`) is used.</span></span>

<span data-ttu-id="c36ba-119">`Invoke` Temsilci türünde yöntemi kapsüllenmiş işlevi çağırır.</span><span class="sxs-lookup"><span data-stu-id="c36ba-119">The `Invoke` method on the delegate type calls the encapsulated function.</span></span> <span data-ttu-id="c36ba-120">Ayrıca, parantezler olmadan Invoke yöntemi ada başvurarak Temsilciler, işlev değerleri ' e geçirilebilir.</span><span class="sxs-lookup"><span data-stu-id="c36ba-120">Also, delegates can be passed as function values by referencing the Invoke method name without the parentheses.</span></span>

<span data-ttu-id="c36ba-121">Aşağıdaki kod, bir sınıfta çeşitli yöntemleri temsil eden temsilciler oluşturmak için sözdizimi gösterir.</span><span class="sxs-lookup"><span data-stu-id="c36ba-121">The following code shows the syntax for creating delegates that represent various methods in a class.</span></span> <span data-ttu-id="c36ba-122">Yöntem statik bir yöntem veya bir örnek yöntemi olup ve demet veya curried formundaki değişkenlerinde olup bağlı olarak bildirmek ve temsilci atamak için söz dizimi biraz farklıdır.</span><span class="sxs-lookup"><span data-stu-id="c36ba-122">Depending on whether the method is a static method or an instance method, and whether it has arguments in the tuple form or the curried form, the syntax for declaring and assigning the delegate is a little different.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4201.fs)]

<span data-ttu-id="c36ba-123">Aşağıdaki kod temsilcileri ile çalışabilir farklı yollardan bazılarını gösterir.</span><span class="sxs-lookup"><span data-stu-id="c36ba-123">The following code shows some of the different ways you can work with delegates.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4202.fs)]

<span data-ttu-id="c36ba-124">Önceki kod örnek çıktısı aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="c36ba-124">The output of the previous code example is as follows.</span></span>

```console
aaaaa
bbbbb
ccccc
[|"aaa"; "bbb"|]
```

## <a name="see-also"></a><span data-ttu-id="c36ba-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c36ba-125">See also</span></span>

- [<span data-ttu-id="c36ba-126">F# Dili Başvurusu</span><span class="sxs-lookup"><span data-stu-id="c36ba-126">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="c36ba-127">Parametreler ve Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="c36ba-127">Parameters and Arguments</span></span>](parameters-and-arguments.md)
- [<span data-ttu-id="c36ba-128">Olaylar</span><span class="sxs-lookup"><span data-stu-id="c36ba-128">Events</span></span>](members/events.md)
