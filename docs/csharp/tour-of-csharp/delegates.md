---
title: C#Temsilciler- C# dilin turu
description: Temsilcilerle C# geç bağlamayı öğrenin
ms.date: 02/27/2020
ms.assetid: 3cc27357-3ac2-43a1-aad0-86a77b88f884
ms.openlocfilehash: b1740ddc65dcb0ee8775f4cbaa8356293ea55fae
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159175"
---
# <a name="delegates"></a><span data-ttu-id="1139c-103">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="1139c-103">Delegates</span></span>

<span data-ttu-id="1139c-104">Bir ***temsilci türü*** , belirli bir parametre listesi ve dönüş türü olan yöntemlere yapılan başvuruları temsil eder.</span><span class="sxs-lookup"><span data-stu-id="1139c-104">A ***delegate type*** represents references to methods with a particular parameter list and return type.</span></span> <span data-ttu-id="1139c-105">Temsilciler, yöntemleri değişkenlere atanabilecek ve parametre olarak geçirilen varlıklar olarak işleme olanağı tanır.</span><span class="sxs-lookup"><span data-stu-id="1139c-105">Delegates make it possible to treat methods as entities that can be assigned to variables and passed as parameters.</span></span> <span data-ttu-id="1139c-106">Temsilciler, bazı diğer dillerde bulunan işlev işaretçileri kavramına benzerdir.</span><span class="sxs-lookup"><span data-stu-id="1139c-106">Delegates are similar to the concept of function pointers found in some other languages.</span></span> <span data-ttu-id="1139c-107">İşlev işaretçilerinden farklı olarak, temsilciler nesne odaklı ve tür açısından güvenlidir.</span><span class="sxs-lookup"><span data-stu-id="1139c-107">Unlike function pointers, delegates are object-oriented and type-safe.</span></span>

<span data-ttu-id="1139c-108">Aşağıdaki örnek, `Function`adlı bir temsilci türü bildirir ve kullanır.</span><span class="sxs-lookup"><span data-stu-id="1139c-108">The following example declares and uses a delegate type named `Function`.</span></span>

[!code-csharp[DelegateExample](../../../samples/snippets/csharp/tour/delegates/Program.cs#L3-L37)]

<span data-ttu-id="1139c-109">`Function` temsilci türünün bir örneği, `double` bağımsız değişken alan ve `double` bir değer döndüren herhangi bir yönteme başvurabilir.</span><span class="sxs-lookup"><span data-stu-id="1139c-109">An instance of the `Function` delegate type can reference any method that takes a `double` argument and returns a `double` value.</span></span> <span data-ttu-id="1139c-110">`Apply` yöntemi, belirli bir Işlevi bir `double[]`öğelerine uygular, sonuçlarla bir `double[]` döndürüyor.</span><span class="sxs-lookup"><span data-stu-id="1139c-110">The `Apply` method applies a given Function to the elements of a `double[]`, returning a `double[]` with the results.</span></span> <span data-ttu-id="1139c-111">`Main` yönteminde, bir `double[]`üç farklı işlevi uygulamak için `Apply` kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1139c-111">In the `Main` method, `Apply` is used to apply three different functions to a `double[]`.</span></span>

<span data-ttu-id="1139c-112">Bir temsilci, statik bir yönteme (örneğin, `Square` veya önceki örnekteki `Math.Sin`) veya bir örnek yöntemine (önceki örnekte `m.Multiply` gibi) başvurabilir.</span><span class="sxs-lookup"><span data-stu-id="1139c-112">A delegate can reference either a static method (such as `Square` or `Math.Sin` in the previous example) or an instance method (such as `m.Multiply` in the previous example).</span></span> <span data-ttu-id="1139c-113">Aynı zamanda bir örnek yöntemine başvuran bir temsilci belirli bir nesneye başvurur ve örnek yöntemi temsilci aracılığıyla çağrıldığında, bu nesne çağrıdan `this` olur.</span><span class="sxs-lookup"><span data-stu-id="1139c-113">A delegate that references an instance method also references a particular object, and when the instance method is invoked through the delegate, that object becomes `this` in the invocation.</span></span>

<span data-ttu-id="1139c-114">Temsilciler, bildirildiği sırada oluşturulan "satır içi Yöntemler" olan anonim işlevler kullanılarak da oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="1139c-114">Delegates can also be created using anonymous functions, which are "inline methods" that are created when declared.</span></span> <span data-ttu-id="1139c-115">Anonim işlevler, çevresindeki yöntemlerin yerel değişkenlerini görebilir.</span><span class="sxs-lookup"><span data-stu-id="1139c-115">Anonymous functions can see the local variables of the surrounding methods.</span></span> <span data-ttu-id="1139c-116">Aşağıdaki örnek bir sınıf oluşturmaz:</span><span class="sxs-lookup"><span data-stu-id="1139c-116">The following example doesn't create a class:</span></span>

[!code-csharp[LambdaExample](../../../samples/snippets/csharp/tour/delegates/Program.cs#L44-L44)]

<span data-ttu-id="1139c-117">Bir temsilci, başvurduğu yöntemin sınıfını bilmez veya ilgilenmez; her önemli şey, başvurulan yöntemin aynı parametrelere sahip olması ve temsilciyle aynı türde dönüş türüdür.</span><span class="sxs-lookup"><span data-stu-id="1139c-117">A delegate doesn't know or care about the class of the method it references; all that matters is that the referenced method has the same parameters and return type as the delegate.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="1139c-118">[Önceki](interfaces.md)
>[İleri](attributes.md)</span><span class="sxs-lookup"><span data-stu-id="1139c-118">[Previous](interfaces.md)
[Next](attributes.md)</span></span>
