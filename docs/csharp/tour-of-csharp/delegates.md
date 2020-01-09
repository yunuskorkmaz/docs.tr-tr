---
title: C#Temsilciler- C# dilin turu
description: Temsilcilerle C# geç bağlamayı öğrenin
ms.date: 08/10/2016
ms.assetid: 3cc27357-3ac2-43a1-aad0-86a77b88f884
ms.openlocfilehash: 317d3ee6fb1350824fa9b3b4d0e3e851780ce4d4
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75346879"
---
# <a name="delegates"></a><span data-ttu-id="94a0c-103">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="94a0c-103">Delegates</span></span>

<span data-ttu-id="94a0c-104">Bir ***temsilci türü*** , belirli bir parametre listesi ve dönüş türü olan yöntemlere yapılan başvuruları temsil eder.</span><span class="sxs-lookup"><span data-stu-id="94a0c-104">A ***delegate type*** represents references to methods with a particular parameter list and return type.</span></span> <span data-ttu-id="94a0c-105">Temsilciler, yöntemleri değişkenlere atanabilecek ve parametre olarak geçirilen varlıklar olarak işleme olanağı tanır.</span><span class="sxs-lookup"><span data-stu-id="94a0c-105">Delegates make it possible to treat methods as entities that can be assigned to variables and passed as parameters.</span></span> <span data-ttu-id="94a0c-106">Temsilciler, bazı diğer dillerde bulunan işlev işaretçileri kavramına benzerdir, ancak işlev işaretçilerinden farklı olarak Temsilciler nesne yönelimli ve tür açısından güvenlidir.</span><span class="sxs-lookup"><span data-stu-id="94a0c-106">Delegates are similar to the concept of function pointers found in some other languages, but unlike function pointers, delegates are object-oriented and type-safe.</span></span>

<span data-ttu-id="94a0c-107">Aşağıdaki örnek, `Function`adlı bir temsilci türü bildirir ve kullanır.</span><span class="sxs-lookup"><span data-stu-id="94a0c-107">The following example declares and uses a delegate type named `Function`.</span></span>

[!code-csharp[DelegateExample](../../../samples/snippets/csharp/tour/delegates/Program.cs#L3-L37)]

<span data-ttu-id="94a0c-108">`Function` temsilci türünün bir örneği, `double` bağımsız değişken alan ve `double` bir değer döndüren herhangi bir yönteme başvurabilir.</span><span class="sxs-lookup"><span data-stu-id="94a0c-108">An instance of the `Function` delegate type can reference any method that takes a `double` argument and returns a `double` value.</span></span> <span data-ttu-id="94a0c-109">`Apply` yöntemi, belirli bir Işlevi bir `double[]`öğelerine uygular, sonuçlarla bir `double[]` döndürüyor.</span><span class="sxs-lookup"><span data-stu-id="94a0c-109">The `Apply` method applies a given Function to the elements of a `double[]`, returning a `double[]` with the results.</span></span> <span data-ttu-id="94a0c-110">`Main` yönteminde, bir `double[]`üç farklı işlevi uygulamak için `Apply` kullanılır.</span><span class="sxs-lookup"><span data-stu-id="94a0c-110">In the `Main` method, `Apply` is used to apply three different functions to a `double[]`.</span></span>

<span data-ttu-id="94a0c-111">Bir temsilci, statik bir yönteme (örneğin, `Square` veya önceki örnekteki `Math.Sin`) veya bir örnek yöntemine (önceki örnekte `m.Multiply` gibi) başvurabilir.</span><span class="sxs-lookup"><span data-stu-id="94a0c-111">A delegate can reference either a static method (such as `Square` or `Math.Sin` in the previous example) or an instance method (such as `m.Multiply` in the previous example).</span></span> <span data-ttu-id="94a0c-112">Aynı zamanda bir örnek yöntemine başvuran bir temsilci belirli bir nesneye başvurur ve örnek yöntemi temsilci aracılığıyla çağrıldığında, bu nesne çağrıdan `this` olur.</span><span class="sxs-lookup"><span data-stu-id="94a0c-112">A delegate that references an instance method also references a particular object, and when the instance method is invoked through the delegate, that object becomes `this` in the invocation.</span></span>

<span data-ttu-id="94a0c-113">Temsilciler, anında oluşturulan "satır içi Yöntemler" olan anonim işlevler kullanılarak da oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="94a0c-113">Delegates can also be created using anonymous functions, which are "inline methods" that are created on the fly.</span></span> <span data-ttu-id="94a0c-114">Anonim işlevler, çevresindeki yöntemlerin yerel değişkenlerini görebilir.</span><span class="sxs-lookup"><span data-stu-id="94a0c-114">Anonymous functions can see the local variables of the surrounding methods.</span></span> <span data-ttu-id="94a0c-115">Bu nedenle, yukarıdaki çarpan örneği bir çarpan sınıfı kullanılmadan daha kolay yazılabilir:</span><span class="sxs-lookup"><span data-stu-id="94a0c-115">Thus, the multiplier example above can be written more easily without using a Multiplier class:</span></span>

[!code-csharp[LambdaExample](../../../samples/snippets/csharp/tour/delegates/Program.cs#L44-L44)]

<span data-ttu-id="94a0c-116">Bir temsilcinin ilgi çekici ve yararlı bir özelliği, başvurduğu yöntemin sınıfını bilmez veya ilgilenmez; her önemli şey, başvurulan yöntemin aynı parametrelere sahip olması ve temsilciyle aynı türde dönüş türüdür.</span><span class="sxs-lookup"><span data-stu-id="94a0c-116">An interesting and useful property of a delegate is that it does not know or care about the class of the method it references; all that matters is that the referenced method has the same parameters and return type as the delegate.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="94a0c-117">[Önceki](interfaces.md)
>[İleri](attributes.md)</span><span class="sxs-lookup"><span data-stu-id="94a0c-117">[Previous](interfaces.md)
[Next](attributes.md)</span></span>
