---
title: C# temsilciler - C# dili turu
description: "Geç bağlama C# temsilciler ile bilgi edinin"
keywords: "Geç bağlama .NET csharp, temsilci, lambda,"
author: BillWagner
ms.author: wiwagn
ms.date: 08/10/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 3cc27357-3ac2-43a1-aad0-86a77b88f884
ms.openlocfilehash: bb304b2e5c762a44aab931b5e8f7fe9c99805eba
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="delegates"></a><span data-ttu-id="d5382-104">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="d5382-104">Delegates</span></span>

<span data-ttu-id="d5382-105">A ***temsilci türü*** belirli bir parametre yöntemleriyle temsil başvuruları listesinde ve dönüş türü.</span><span class="sxs-lookup"><span data-stu-id="d5382-105">A ***delegate type*** represents references to methods with a particular parameter list and return type.</span></span> <span data-ttu-id="d5382-106">Temsilciler yöntemleri değişkenleri için atanan ve parametre olarak geçirilen varlıklar olarak değerlendirmek mümkün kılar.</span><span class="sxs-lookup"><span data-stu-id="d5382-106">Delegates make it possible to treat methods as entities that can be assigned to variables and passed as parameters.</span></span> <span data-ttu-id="d5382-107">Temsilciler diğer bazı dillerde bulunan işlev işaretçileri kavramı benzer, ancak işlev işaretçileri, nesne yönelimli ve tür kullanımı uyumlu temsilciler.</span><span class="sxs-lookup"><span data-stu-id="d5382-107">Delegates are similar to the concept of function pointers found in some other languages, but unlike function pointers, delegates are object-oriented and type-safe.</span></span>

<span data-ttu-id="d5382-108">Aşağıdaki örnek bildirir ve adlı bir temsilci türü kullanan `Function`.</span><span class="sxs-lookup"><span data-stu-id="d5382-108">The following example declares and uses a delegate type named `Function`.</span></span>

[!code-csharp[DelegateExample](../../../samples/snippets/csharp/tour/delegates/Program.cs#L3-L37)]

<span data-ttu-id="d5382-109">Örneği `Function` temsilci türü alır herhangi bir yöntemini başvuran bir `double` bağımsız değişkeni ve döndürür bir `double` değeri.</span><span class="sxs-lookup"><span data-stu-id="d5382-109">An instance of the `Function` delegate type can reference any method that takes a `double` argument and returns a `double` value.</span></span> <span data-ttu-id="d5382-110">`Apply` Yöntemi öğelerine verilen işlevin geçerli bir `double[]`, geri dönen bir `double[]` sonuçları.</span><span class="sxs-lookup"><span data-stu-id="d5382-110">The `Apply` method applies a given Function to the elements of a `double[]`, returning a `double[]` with the results.</span></span> <span data-ttu-id="d5382-111">İçinde `Main` yöntemi, `Apply` üç farklı işleve uygulamak için kullanılan bir `double[]`.</span><span class="sxs-lookup"><span data-stu-id="d5382-111">In the `Main` method, `Apply` is used to apply three different functions to a `double[]`.</span></span>

<span data-ttu-id="d5382-112">Bir temsilci statik bir yöntem başvurusu yapabilir (gibi `Square` veya `Math.Sin` önceki örnekte) veya bir örnek yöntemi (gibi `m.Multiply` önceki örnekte).</span><span class="sxs-lookup"><span data-stu-id="d5382-112">A delegate can reference either a static method (such as `Square` or `Math.Sin` in the previous example) or an instance method (such as `m.Multiply` in the previous example).</span></span> <span data-ttu-id="d5382-113">Örnek yöntemi başvuran bir temsilci Ayrıca belirli bir nesnenin başvuruda bulunduğundan ve temsilci örnek yöntemi çağrıldığında, bu nesne haline gelir `this` çağrısı.</span><span class="sxs-lookup"><span data-stu-id="d5382-113">A delegate that references an instance method also references a particular object, and when the instance method is invoked through the delegate, that object becomes `this` in the invocation.</span></span>

<span data-ttu-id="d5382-114">Temsilciler ayrıca "üzerinde çalışma sırasında oluşturulan satır içi yöntemleri" anonim işlevler kullanılarak oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="d5382-114">Delegates can also be created using anonymous functions, which are "inline methods" that are created on the fly.</span></span> <span data-ttu-id="d5382-115">Anonim işlevler çevresindeki yöntemlerin yerel değişkenler görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d5382-115">Anonymous functions can see the local variables of the surrounding methods.</span></span> <span data-ttu-id="d5382-116">Bu nedenle, yukarıdaki çarpanı örnek daha kolay çarpanı sınıfı kullanmadan yazılabilir:</span><span class="sxs-lookup"><span data-stu-id="d5382-116">Thus, the multiplier example above can be written more easily without using a Multiplier class:</span></span>

[!code-csharp[LambdaExample](../../../samples/snippets/csharp/tour/delegates/Program.cs#L44-L44)]

<span data-ttu-id="d5382-117">Bir ilginç ve yararlı bir temsilci, bilmiyorsanız veya başvurduğu yöntemi sınıfı hakkında önemli olduğunu özelliğidir; önemli olan başvurulan yöntemi temsilci olarak dönüş türü ve aynı parametrelere sahip.</span><span class="sxs-lookup"><span data-stu-id="d5382-117">An interesting and useful property of a delegate is that it does not know or care about the class of the method it references; all that matters is that the referenced method has the same parameters and return type as the delegate.</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="d5382-118">[Önceki](enums.md)
[sonraki](attributes.md)</span><span class="sxs-lookup"><span data-stu-id="d5382-118">[Previous](enums.md)
[Next](attributes.md)</span></span>
