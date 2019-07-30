---
title: Temsilciler
description: "' De F#temsilcilerle çalışmayı öğrenin."
ms.date: 05/16/2016
ms.openlocfilehash: 65875897d5fc4b2ac66f1dfbe913f29fb74137cd
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630361"
---
# <a name="delegates"></a><span data-ttu-id="4b8ff-103">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="4b8ff-103">Delegates</span></span>

<span data-ttu-id="4b8ff-104">Bir temsilci, bir işlev çağrısını bir nesne olarak temsil eder.</span><span class="sxs-lookup"><span data-stu-id="4b8ff-104">A delegate represents a function call as an object.</span></span> <span data-ttu-id="4b8ff-105">' F#De, işlevleri ilk sınıf değerler olarak göstermek için normalde işlev değerlerini kullanmanız gerekir; Ancak, temsilciler .NET Framework kullanılır ve bu nedenle, bunları bekleyen API 'lerle birlikte çalışırken gereklidir.</span><span class="sxs-lookup"><span data-stu-id="4b8ff-105">In F#, you ordinarily should use function values to represent functions as first-class values; however, delegates are used in the .NET Framework and so are needed when you interoperate with APIs that expect them.</span></span> <span data-ttu-id="4b8ff-106">Bunlar ayrıca, diğer .NET Framework dillerden kullanılmak üzere tasarlanan kitaplıkları yazmak için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="4b8ff-106">They may also be used when authoring libraries designed for use from other .NET Framework languages.</span></span>

## <a name="syntax"></a><span data-ttu-id="4b8ff-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4b8ff-107">Syntax</span></span>

```fsharp
type delegate-typename = delegate of type1 -> type2
```

## <a name="remarks"></a><span data-ttu-id="4b8ff-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4b8ff-108">Remarks</span></span>

<span data-ttu-id="4b8ff-109">Önceki sözdiziminde, `type1` bağımsız değişken türünü veya türlerini temsil eder ve `type2` dönüş türünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="4b8ff-109">In the previous syntax, `type1` represents the argument type or types and `type2` represents the return type.</span></span> <span data-ttu-id="4b8ff-110">Tarafından `type1` temsil edilen bağımsız değişken türleri otomatik olarak curried ' dir.</span><span class="sxs-lookup"><span data-stu-id="4b8ff-110">The argument types that are represented by `type1` are automatically curried.</span></span> <span data-ttu-id="4b8ff-111">Bu, bu tür için hedef işlevin bağımsız değişkenleri curried ise ve başlık formunda zaten olan bağımsız değişkenler için parantez içine alınmış bir tanımlama grubu olan bir demet formu kullanmanızı önerir.</span><span class="sxs-lookup"><span data-stu-id="4b8ff-111">This suggests that for this type you use a tuple form if the arguments of the target function are curried, and a parenthesized tuple for arguments that are already in the tuple form.</span></span> <span data-ttu-id="4b8ff-112">Otomatik currying, target yöntemiyle eşleşen bir demet bağımsız değişkeni bırakarak bir parantez kümesini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="4b8ff-112">The automatic currying removes a set of parentheses, leaving a tuple argument that matches the target method.</span></span> <span data-ttu-id="4b8ff-113">Her durumda kullanmanız gereken sözdiziminin kod örneğine bakın.</span><span class="sxs-lookup"><span data-stu-id="4b8ff-113">Refer to the code example for the syntax you should use in each case.</span></span>

<span data-ttu-id="4b8ff-114">Temsilciler F# işlev değerlerine, statik veya örnek yöntemlerine eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="4b8ff-114">Delegates can be attached to F# function values, and static or instance methods.</span></span> <span data-ttu-id="4b8ff-115">F#işlev değerleri, doğrudan temsilci oluşturucularına bağımsız değişken olarak geçirilebilir.</span><span class="sxs-lookup"><span data-stu-id="4b8ff-115">F# function values can be passed directly as arguments to delegate constructors.</span></span> <span data-ttu-id="4b8ff-116">Statik bir yöntemde, sınıfının adını ve yöntemini kullanarak temsilciyi oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="4b8ff-116">For a static method, you construct the delegate by using the name of the class and the method.</span></span> <span data-ttu-id="4b8ff-117">Bir örnek yönteminde, nesne örneğini ve yöntemini bir bağımsız değişkende sağlarsınız.</span><span class="sxs-lookup"><span data-stu-id="4b8ff-117">For an instance method, you provide the object instance and method in one argument.</span></span> <span data-ttu-id="4b8ff-118">Her iki durumda da, üye erişim işleci (`.`) kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4b8ff-118">In both cases, the member access operator (`.`) is used.</span></span>

<span data-ttu-id="4b8ff-119">Temsilci `Invoke` türündeki yöntemi kapsüllenmiş işlevi çağırır.</span><span class="sxs-lookup"><span data-stu-id="4b8ff-119">The `Invoke` method on the delegate type calls the encapsulated function.</span></span> <span data-ttu-id="4b8ff-120">Ayrıca, temsilciler, parantez olmadan Invoke yöntemi adına başvurarak işlev değerleri olarak geçirilebilir.</span><span class="sxs-lookup"><span data-stu-id="4b8ff-120">Also, delegates can be passed as function values by referencing the Invoke method name without the parentheses.</span></span>

<span data-ttu-id="4b8ff-121">Aşağıdaki kod, bir sınıftaki çeşitli yöntemleri temsil eden temsilciler oluşturmak için söz dizimini gösterir.</span><span class="sxs-lookup"><span data-stu-id="4b8ff-121">The following code shows the syntax for creating delegates that represent various methods in a class.</span></span> <span data-ttu-id="4b8ff-122">Yöntemin statik bir yöntem veya örnek yöntemi olmasına ve tanımlama grubu formunda veya curried formunda bağımsız değişkenler içerip içermediğini bağlı olarak, temsilciyi bildirme ve atamaya yönelik sözdizimi biraz farklıdır.</span><span class="sxs-lookup"><span data-stu-id="4b8ff-122">Depending on whether the method is a static method or an instance method, and whether it has arguments in the tuple form or the curried form, the syntax for declaring and assigning the delegate is a little different.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4201.fs)]

<span data-ttu-id="4b8ff-123">Aşağıdaki kod temsilcilerle çalışabilmeniz için kullanabileceğiniz farklı yolları gösterir.</span><span class="sxs-lookup"><span data-stu-id="4b8ff-123">The following code shows some of the different ways you can work with delegates.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4202.fs)]

<span data-ttu-id="4b8ff-124">Önceki kod örneği çıkışı aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="4b8ff-124">The output of the previous code example is as follows.</span></span>

```console
aaaaa
bbbbb
ccccc
[|"aaa"; "bbb"|]
```

## <a name="see-also"></a><span data-ttu-id="4b8ff-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4b8ff-125">See also</span></span>

- [<span data-ttu-id="4b8ff-126">F# Dili Başvurusu</span><span class="sxs-lookup"><span data-stu-id="4b8ff-126">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="4b8ff-127">Parametreler ve Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="4b8ff-127">Parameters and Arguments</span></span>](parameters-and-arguments.md)
- [<span data-ttu-id="4b8ff-128">Olaylar</span><span class="sxs-lookup"><span data-stu-id="4b8ff-128">Events</span></span>](./members/events.md)
