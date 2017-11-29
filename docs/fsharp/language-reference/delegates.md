---
title: Temsilciler (F#)
description: "F # temsilciler çalışmak öğrenin."
keywords: "Visual f #, f # işlevsel programlama"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 719948a3-83ba-4618-82d6-a22945c3f4b0
ms.openlocfilehash: c929a342ab4c5098062417691a99cee3b007d2d2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="delegates"></a><span data-ttu-id="069b4-104">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="069b4-104">Delegates</span></span>

<span data-ttu-id="069b4-105">Temsilci bir nesne olarak bir işlev çağrısını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="069b4-105">A delegate represents a function call as an object.</span></span> <span data-ttu-id="069b4-106">F #'ta, normalde işlevi ilk sınıf değerleri olarak işlevler göstermek için değerleri kullanmanız; Ancak, temsilciler .NET Framework kullanılır ve bunları beklediğiniz API'leri ile birlikte çalışmak, böylece ihtiyaç vardır.</span><span class="sxs-lookup"><span data-stu-id="069b4-106">In F#, you ordinarily should use function values to represent functions as first-class values; however, delegates are used in the .NET Framework and so are needed when you interoperate with APIs that expect them.</span></span> <span data-ttu-id="069b4-107">Geliştirme kitaplıkları için tasarlanan diğer .NET Framework dillerinden kullandığınızda da kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="069b4-107">They may also be used when authoring libraries designed for use from other .NET Framework languages.</span></span>


## <a name="syntax"></a><span data-ttu-id="069b4-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="069b4-108">Syntax</span></span>

```fsharp
type delegate-typename = delegate of type1 -> type2
```

## <a name="remarks"></a><span data-ttu-id="069b4-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="069b4-109">Remarks</span></span>
<span data-ttu-id="069b4-110">Önceki sözdiziminde `type1` bağımsız değişken türü veya türleri temsil eder ve `type2` dönüş türünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="069b4-110">In the previous syntax, `type1` represents the argument type or types and `type2` represents the return type.</span></span> <span data-ttu-id="069b4-111">Tarafından temsil edilen bağımsız değişken türleri `type1` otomatik olarak curried.</span><span class="sxs-lookup"><span data-stu-id="069b4-111">The argument types that are represented by `type1` are automatically curried.</span></span> <span data-ttu-id="069b4-112">Bu, bu tür bağımsız değişkenleri hedef işlevinin curried varsa bir tanımlama grubu formu kullanın ve kayıt formunda önceden olan bağımsız değişkenler için parantez içine alınmış bir tanımlama grubu için önerir.</span><span class="sxs-lookup"><span data-stu-id="069b4-112">This suggests that for this type you use a tuple form if the arguments of the target function are curried, and a parenthesized tuple for arguments that are already in the tuple form.</span></span> <span data-ttu-id="069b4-113">Otomatik currying hedef yöntemin eşleşen bir tanımlama grubu bağımsız değişkeni bırakarak parantez kümesini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="069b4-113">The automatic currying removes a set of parentheses, leaving a tuple argument that matches the target method.</span></span> <span data-ttu-id="069b4-114">Her durumda kullanmalısınız söz dizimi kod örneğine bakın.</span><span class="sxs-lookup"><span data-stu-id="069b4-114">Refer to the code example for the syntax you should use in each case.</span></span>

<span data-ttu-id="069b4-115">Temsilciler F # işlev değerlerini ve statik eklenebilecek veya yöntemleri örneği.</span><span class="sxs-lookup"><span data-stu-id="069b4-115">Delegates can be attached to F# function values, and static or instance methods.</span></span> <span data-ttu-id="069b4-116">F # işlev değerlerini oluşturucuları temsilci seçmek için doğrudan bağımsız değişken olarak geçirilebilir.</span><span class="sxs-lookup"><span data-stu-id="069b4-116">F# function values can be passed directly as arguments to delegate constructors.</span></span> <span data-ttu-id="069b4-117">Statik bir yöntem için sınıf ve yöntem adını kullanarak temsilci oluşturun.</span><span class="sxs-lookup"><span data-stu-id="069b4-117">For a static method, you construct the delegate by using the name of the class and the method.</span></span> <span data-ttu-id="069b4-118">Bir örnek yöntemi için nesne örneği ve tek bir bağımsız değişken yöntemi sağlar.</span><span class="sxs-lookup"><span data-stu-id="069b4-118">For an instance method, you provide the object instance and method in one argument.</span></span> <span data-ttu-id="069b4-119">Her iki durumda da, üye erişimi işleci (`.`) kullanılır.</span><span class="sxs-lookup"><span data-stu-id="069b4-119">In both cases, the member access operator (`.`) is used.</span></span>

<span data-ttu-id="069b4-120">`Invoke` Temsilci türünün yöntemi kapsüllenmiş işlevi çağırır.</span><span class="sxs-lookup"><span data-stu-id="069b4-120">The `Invoke` method on the delegate type calls the encapsulated function.</span></span> <span data-ttu-id="069b4-121">Ayrıca, temsilciler işlevi değerleri olarak parantezler olmadan Invoke yöntemi adına başvuran tarafından gönderilir.</span><span class="sxs-lookup"><span data-stu-id="069b4-121">Also, delegates can be passed as function values by referencing the Invoke method name without the parentheses.</span></span>

<span data-ttu-id="069b4-122">Aşağıdaki kod bir sınıf çeşitli yöntemlerle temsil temsilciler oluşturmak için söz dizimi görülmektedir.</span><span class="sxs-lookup"><span data-stu-id="069b4-122">The following code shows the syntax for creating delegates that represent various methods in a class.</span></span> <span data-ttu-id="069b4-123">Bildirme ve temsilci atamak için sözdizimi yöntemi bir statik veya örnek yöntemini olup ve bağımsız değişkenleri tanımlama grubu form veya curried biçiminde olup bağlı olarak biraz farklıdır.</span><span class="sxs-lookup"><span data-stu-id="069b4-123">Depending on whether the method is a static method or an instance method, and whether it has arguments in the tuple form or the curried form, the syntax for declaring and assigning the delegate is a little different.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4201.fs)]

<span data-ttu-id="069b4-124">Aşağıdaki kod, temsilci ile çalışabilirsiniz farklı yollardan bazılarını gösterir.</span><span class="sxs-lookup"><span data-stu-id="069b4-124">The following code shows some of the different ways you can work with delegates.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4202.fs)]

<span data-ttu-id="069b4-125">Önceki kod örneğinde çıktı aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="069b4-125">The output of the previous code example is as follows.</span></span>

```console
aaaaa
bbbbb
ccccc
[|"aaa"; "bbb"|]
```

## <a name="see-also"></a><span data-ttu-id="069b4-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="069b4-126">See Also</span></span>
[<span data-ttu-id="069b4-127">F # dili başvurusu</span><span class="sxs-lookup"><span data-stu-id="069b4-127">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="069b4-128">Parametreler ve bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="069b4-128">Parameters and Arguments</span></span>](parameters-and-arguments.md)

[<span data-ttu-id="069b4-129">Olayları</span><span class="sxs-lookup"><span data-stu-id="069b4-129">Events</span></span>](members/events.md)
