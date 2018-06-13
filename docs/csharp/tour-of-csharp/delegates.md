---
title: C# temsilciler - C# dili turu
description: Geç bağlama C# temsilciler ile bilgi edinin
ms.date: 08/10/2016
ms.assetid: 3cc27357-3ac2-43a1-aad0-86a77b88f884
ms.openlocfilehash: 1dcd078b275d951b049b0c5bb6e084a4083d042d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33360576"
---
# <a name="delegates"></a><span data-ttu-id="5ee58-103">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="5ee58-103">Delegates</span></span>

<span data-ttu-id="5ee58-104">A ***temsilci türü*** belirli bir parametre yöntemleriyle temsil başvuruları listesinde ve dönüş türü.</span><span class="sxs-lookup"><span data-stu-id="5ee58-104">A ***delegate type*** represents references to methods with a particular parameter list and return type.</span></span> <span data-ttu-id="5ee58-105">Temsilciler yöntemleri değişkenleri için atanan ve parametre olarak geçirilen varlıklar olarak değerlendirmek mümkün kılar.</span><span class="sxs-lookup"><span data-stu-id="5ee58-105">Delegates make it possible to treat methods as entities that can be assigned to variables and passed as parameters.</span></span> <span data-ttu-id="5ee58-106">Temsilciler diğer bazı dillerde bulunan işlev işaretçileri kavramı benzer, ancak işlev işaretçileri, nesne yönelimli ve tür kullanımı uyumlu temsilciler.</span><span class="sxs-lookup"><span data-stu-id="5ee58-106">Delegates are similar to the concept of function pointers found in some other languages, but unlike function pointers, delegates are object-oriented and type-safe.</span></span>

<span data-ttu-id="5ee58-107">Aşağıdaki örnek bildirir ve adlı bir temsilci türü kullanan `Function`.</span><span class="sxs-lookup"><span data-stu-id="5ee58-107">The following example declares and uses a delegate type named `Function`.</span></span>

[!code-csharp[DelegateExample](../../../samples/snippets/csharp/tour/delegates/Program.cs#L3-L37)]

<span data-ttu-id="5ee58-108">Örneği `Function` temsilci türü alır herhangi bir yöntemini başvuran bir `double` bağımsız değişkeni ve döndürür bir `double` değeri.</span><span class="sxs-lookup"><span data-stu-id="5ee58-108">An instance of the `Function` delegate type can reference any method that takes a `double` argument and returns a `double` value.</span></span> <span data-ttu-id="5ee58-109">`Apply` Yöntemi öğelerine verilen işlevin geçerli bir `double[]`, geri dönen bir `double[]` sonuçları.</span><span class="sxs-lookup"><span data-stu-id="5ee58-109">The `Apply` method applies a given Function to the elements of a `double[]`, returning a `double[]` with the results.</span></span> <span data-ttu-id="5ee58-110">İçinde `Main` yöntemi, `Apply` üç farklı işleve uygulamak için kullanılan bir `double[]`.</span><span class="sxs-lookup"><span data-stu-id="5ee58-110">In the `Main` method, `Apply` is used to apply three different functions to a `double[]`.</span></span>

<span data-ttu-id="5ee58-111">Bir temsilci statik bir yöntem başvurusu yapabilir (gibi `Square` veya `Math.Sin` önceki örnekte) veya bir örnek yöntemi (gibi `m.Multiply` önceki örnekte).</span><span class="sxs-lookup"><span data-stu-id="5ee58-111">A delegate can reference either a static method (such as `Square` or `Math.Sin` in the previous example) or an instance method (such as `m.Multiply` in the previous example).</span></span> <span data-ttu-id="5ee58-112">Örnek yöntemi başvuran bir temsilci Ayrıca belirli bir nesnenin başvuruda bulunduğundan ve temsilci örnek yöntemi çağrıldığında, bu nesne haline gelir `this` çağrısı.</span><span class="sxs-lookup"><span data-stu-id="5ee58-112">A delegate that references an instance method also references a particular object, and when the instance method is invoked through the delegate, that object becomes `this` in the invocation.</span></span>

<span data-ttu-id="5ee58-113">Temsilciler ayrıca "üzerinde çalışma sırasında oluşturulan satır içi yöntemleri" anonim işlevler kullanılarak oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="5ee58-113">Delegates can also be created using anonymous functions, which are "inline methods" that are created on the fly.</span></span> <span data-ttu-id="5ee58-114">Anonim işlevler çevresindeki yöntemlerin yerel değişkenler görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5ee58-114">Anonymous functions can see the local variables of the surrounding methods.</span></span> <span data-ttu-id="5ee58-115">Bu nedenle, yukarıdaki çarpanı örnek daha kolay çarpanı sınıfı kullanmadan yazılabilir:</span><span class="sxs-lookup"><span data-stu-id="5ee58-115">Thus, the multiplier example above can be written more easily without using a Multiplier class:</span></span>

[!code-csharp[LambdaExample](../../../samples/snippets/csharp/tour/delegates/Program.cs#L44-L44)]

<span data-ttu-id="5ee58-116">Bir ilginç ve yararlı bir temsilci, bilmiyorsanız veya başvurduğu yöntemi sınıfı hakkında önemli olduğunu özelliğidir; önemli olan başvurulan yöntemi temsilci olarak dönüş türü ve aynı parametrelere sahip.</span><span class="sxs-lookup"><span data-stu-id="5ee58-116">An interesting and useful property of a delegate is that it does not know or care about the class of the method it references; all that matters is that the referenced method has the same parameters and return type as the delegate.</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="5ee58-117">[Önceki](enums.md)
[sonraki](attributes.md)</span><span class="sxs-lookup"><span data-stu-id="5ee58-117">[Previous](enums.md)
[Next](attributes.md)</span></span>
