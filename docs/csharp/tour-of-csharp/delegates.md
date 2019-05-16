---
title: C#Temsilciler - Turu C# dil
description: Geç bağlama ile bilgi C# temsilciler
ms.date: 08/10/2016
ms.assetid: 3cc27357-3ac2-43a1-aad0-86a77b88f884
ms.openlocfilehash: 35a1e212b50e77eb43271a657c8abb21eb6cfb4a
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65634628"
---
# <a name="delegates"></a><span data-ttu-id="275bc-103">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="275bc-103">Delegates</span></span>

<span data-ttu-id="275bc-104">A ***temsilci türü*** belirli bir parametre olan yöntemlere başvuruları temsil listesi ve dönüş türü.</span><span class="sxs-lookup"><span data-stu-id="275bc-104">A ***delegate type*** represents references to methods with a particular parameter list and return type.</span></span> <span data-ttu-id="275bc-105">Temsilciler, yöntemleri değişkenine atanır ve parametre olarak geçirilen varlıklar olarak değerlendirmek mümkün kılar.</span><span class="sxs-lookup"><span data-stu-id="275bc-105">Delegates make it possible to treat methods as entities that can be assigned to variables and passed as parameters.</span></span> <span data-ttu-id="275bc-106">Diğer dillerde bulunan işlev işaretçileri kavramı temsilcileri benzerdir ancak işlev işaretçileri, nesne yönelimli ve tür kullanımı uyumlu temsilciler.</span><span class="sxs-lookup"><span data-stu-id="275bc-106">Delegates are similar to the concept of function pointers found in some other languages, but unlike function pointers, delegates are object-oriented and type-safe.</span></span>

<span data-ttu-id="275bc-107">Aşağıdaki örnek bildirir ve adlandırılmış bir temsilci türü kullanır `Function`.</span><span class="sxs-lookup"><span data-stu-id="275bc-107">The following example declares and uses a delegate type named `Function`.</span></span>

[!code-csharp[DelegateExample](../../../samples/snippets/csharp/tour/delegates/Program.cs#L3-L37)]

<span data-ttu-id="275bc-108">Örneği `Function` temsilci türü, alan herhangi bir yöntemi başvurabilir bir `double` bağımsız değişkeni ve döndürür bir `double` değeri.</span><span class="sxs-lookup"><span data-stu-id="275bc-108">An instance of the `Function` delegate type can reference any method that takes a `double` argument and returns a `double` value.</span></span> <span data-ttu-id="275bc-109">`Apply` Yöntemi öğelerine verilen işlevi uygular bir `double[]`, döndüren bir `double[]` sonuçları.</span><span class="sxs-lookup"><span data-stu-id="275bc-109">The `Apply` method applies a given Function to the elements of a `double[]`, returning a `double[]` with the results.</span></span> <span data-ttu-id="275bc-110">İçinde `Main` yöntemi `Apply` üç farklı işlevlere uygulamak için kullanılan bir `double[]`.</span><span class="sxs-lookup"><span data-stu-id="275bc-110">In the `Main` method, `Apply` is used to apply three different functions to a `double[]`.</span></span>

<span data-ttu-id="275bc-111">Bir temsilci bir statik yöntem başvurabilir (gibi `Square` veya `Math.Sin` önceki örnekte) veya bir örnek yöntemi (gibi `m.Multiply` önceki örnekte).</span><span class="sxs-lookup"><span data-stu-id="275bc-111">A delegate can reference either a static method (such as `Square` or `Math.Sin` in the previous example) or an instance method (such as `m.Multiply` in the previous example).</span></span> <span data-ttu-id="275bc-112">Bir örnek yöntemi başvuran bir temsilci Ayrıca belirli bir nesnenin başvuruda bulunduğundan ve temsilci örnek yöntemi çağrıldığında, bu nesne haline gelir `this` çağrısı.</span><span class="sxs-lookup"><span data-stu-id="275bc-112">A delegate that references an instance method also references a particular object, and when the instance method is invoked through the delegate, that object becomes `this` in the invocation.</span></span>

<span data-ttu-id="275bc-113">Temsilciler da "anında oluşturulan satır içi yöntemler" anonim işlevler kullanılarak oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="275bc-113">Delegates can also be created using anonymous functions, which are "inline methods" that are created on the fly.</span></span> <span data-ttu-id="275bc-114">Anonim İşlevler, yerel değişkenler çevreleyen yöntemlerden görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="275bc-114">Anonymous functions can see the local variables of the surrounding methods.</span></span> <span data-ttu-id="275bc-115">Bu nedenle, yukarıdaki çarpan örneği daha kolay bir çarpan sınıf kullanmadan yazılabilir:</span><span class="sxs-lookup"><span data-stu-id="275bc-115">Thus, the multiplier example above can be written more easily without using a Multiplier class:</span></span>

[!code-csharp[LambdaExample](../../../samples/snippets/csharp/tour/delegates/Program.cs#L44-L44)]

<span data-ttu-id="275bc-116">Bir ilgi çekici ve kullanışlı bir temsilci, bilmiyorsanız veya yöntemin başvurduğu sınıfı hakkında dikkatli olun, özelliğidir; önemli olan başvurulan yöntemi aynı parametre ve dönüş türü temsilciyle sahiptir.</span><span class="sxs-lookup"><span data-stu-id="275bc-116">An interesting and useful property of a delegate is that it does not know or care about the class of the method it references; all that matters is that the referenced method has the same parameters and return type as the delegate.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="275bc-117">[Önceki](enums.md)
>[İleri](attributes.md)</span><span class="sxs-lookup"><span data-stu-id="275bc-117">[Previous](enums.md)
[Next](attributes.md)</span></span>
