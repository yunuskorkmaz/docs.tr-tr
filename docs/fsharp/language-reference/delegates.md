---
title: Temsilciler (F#)
description: 'F # temsilciler çalışmak öğrenin.'
ms.date: 05/16/2016
ms.openlocfilehash: 664b4f80302871d05ea9604ca90219e19bc14ddb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33563447"
---
# <a name="delegates"></a><span data-ttu-id="76331-103">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="76331-103">Delegates</span></span>

<span data-ttu-id="76331-104">Temsilci bir nesne olarak bir işlev çağrısını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="76331-104">A delegate represents a function call as an object.</span></span> <span data-ttu-id="76331-105">F #'ta, normalde işlevi ilk sınıf değerleri olarak işlevler göstermek için değerleri kullanmanız; Ancak, temsilciler .NET Framework kullanılır ve bunları beklediğiniz API'leri ile birlikte çalışmak, böylece ihtiyaç vardır.</span><span class="sxs-lookup"><span data-stu-id="76331-105">In F#, you ordinarily should use function values to represent functions as first-class values; however, delegates are used in the .NET Framework and so are needed when you interoperate with APIs that expect them.</span></span> <span data-ttu-id="76331-106">Geliştirme kitaplıkları için tasarlanan diğer .NET Framework dillerinden kullandığınızda da kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="76331-106">They may also be used when authoring libraries designed for use from other .NET Framework languages.</span></span>


## <a name="syntax"></a><span data-ttu-id="76331-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="76331-107">Syntax</span></span>

```fsharp
type delegate-typename = delegate of type1 -> type2
```

## <a name="remarks"></a><span data-ttu-id="76331-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="76331-108">Remarks</span></span>
<span data-ttu-id="76331-109">Önceki sözdiziminde `type1` bağımsız değişken türü veya türleri temsil eder ve `type2` dönüş türünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="76331-109">In the previous syntax, `type1` represents the argument type or types and `type2` represents the return type.</span></span> <span data-ttu-id="76331-110">Tarafından temsil edilen bağımsız değişken türleri `type1` otomatik olarak curried.</span><span class="sxs-lookup"><span data-stu-id="76331-110">The argument types that are represented by `type1` are automatically curried.</span></span> <span data-ttu-id="76331-111">Bu, bu tür bağımsız değişkenleri hedef işlevinin curried varsa bir tanımlama grubu formu kullanın ve kayıt formunda önceden olan bağımsız değişkenler için parantez içine alınmış bir tanımlama grubu için önerir.</span><span class="sxs-lookup"><span data-stu-id="76331-111">This suggests that for this type you use a tuple form if the arguments of the target function are curried, and a parenthesized tuple for arguments that are already in the tuple form.</span></span> <span data-ttu-id="76331-112">Otomatik currying hedef yöntemin eşleşen bir tanımlama grubu bağımsız değişkeni bırakarak parantez kümesini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="76331-112">The automatic currying removes a set of parentheses, leaving a tuple argument that matches the target method.</span></span> <span data-ttu-id="76331-113">Her durumda kullanmalısınız söz dizimi kod örneğine bakın.</span><span class="sxs-lookup"><span data-stu-id="76331-113">Refer to the code example for the syntax you should use in each case.</span></span>

<span data-ttu-id="76331-114">Temsilciler F # işlev değerlerini ve statik eklenebilecek veya yöntemleri örneği.</span><span class="sxs-lookup"><span data-stu-id="76331-114">Delegates can be attached to F# function values, and static or instance methods.</span></span> <span data-ttu-id="76331-115">F # işlev değerlerini oluşturucuları temsilci seçmek için doğrudan bağımsız değişken olarak geçirilebilir.</span><span class="sxs-lookup"><span data-stu-id="76331-115">F# function values can be passed directly as arguments to delegate constructors.</span></span> <span data-ttu-id="76331-116">Statik bir yöntem için sınıf ve yöntem adını kullanarak temsilci oluşturun.</span><span class="sxs-lookup"><span data-stu-id="76331-116">For a static method, you construct the delegate by using the name of the class and the method.</span></span> <span data-ttu-id="76331-117">Bir örnek yöntemi için nesne örneği ve tek bir bağımsız değişken yöntemi sağlar.</span><span class="sxs-lookup"><span data-stu-id="76331-117">For an instance method, you provide the object instance and method in one argument.</span></span> <span data-ttu-id="76331-118">Her iki durumda da, üye erişimi işleci (`.`) kullanılır.</span><span class="sxs-lookup"><span data-stu-id="76331-118">In both cases, the member access operator (`.`) is used.</span></span>

<span data-ttu-id="76331-119">`Invoke` Temsilci türünün yöntemi kapsüllenmiş işlevi çağırır.</span><span class="sxs-lookup"><span data-stu-id="76331-119">The `Invoke` method on the delegate type calls the encapsulated function.</span></span> <span data-ttu-id="76331-120">Ayrıca, temsilciler işlevi değerleri olarak parantezler olmadan Invoke yöntemi adına başvuran tarafından gönderilir.</span><span class="sxs-lookup"><span data-stu-id="76331-120">Also, delegates can be passed as function values by referencing the Invoke method name without the parentheses.</span></span>

<span data-ttu-id="76331-121">Aşağıdaki kod bir sınıf çeşitli yöntemlerle temsil temsilciler oluşturmak için söz dizimi görülmektedir.</span><span class="sxs-lookup"><span data-stu-id="76331-121">The following code shows the syntax for creating delegates that represent various methods in a class.</span></span> <span data-ttu-id="76331-122">Bildirme ve temsilci atamak için sözdizimi yöntemi bir statik veya örnek yöntemini olup ve bağımsız değişkenleri tanımlama grubu form veya curried biçiminde olup bağlı olarak biraz farklıdır.</span><span class="sxs-lookup"><span data-stu-id="76331-122">Depending on whether the method is a static method or an instance method, and whether it has arguments in the tuple form or the curried form, the syntax for declaring and assigning the delegate is a little different.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4201.fs)]

<span data-ttu-id="76331-123">Aşağıdaki kod, temsilci ile çalışabilirsiniz farklı yollardan bazılarını gösterir.</span><span class="sxs-lookup"><span data-stu-id="76331-123">The following code shows some of the different ways you can work with delegates.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4202.fs)]

<span data-ttu-id="76331-124">Önceki kod örneğinde çıktı aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="76331-124">The output of the previous code example is as follows.</span></span>

```console
aaaaa
bbbbb
ccccc
[|"aaa"; "bbb"|]
```

## <a name="see-also"></a><span data-ttu-id="76331-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="76331-125">See Also</span></span>
[<span data-ttu-id="76331-126">F# Dili Başvurusu</span><span class="sxs-lookup"><span data-stu-id="76331-126">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="76331-127">Parametreler ve Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="76331-127">Parameters and Arguments</span></span>](parameters-and-arguments.md)

[<span data-ttu-id="76331-128">Olaylar</span><span class="sxs-lookup"><span data-stu-id="76331-128">Events</span></span>](members/events.md)
