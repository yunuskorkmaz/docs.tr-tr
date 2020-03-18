---
title: C# Delegeleri - C# dilinde bir tur
description: C# temsilcileriyle geç bağlanmayı öğrenin
ms.date: 02/27/2020
ms.assetid: 3cc27357-3ac2-43a1-aad0-86a77b88f884
ms.openlocfilehash: b1740ddc65dcb0ee8775f4cbaa8356293ea55fae
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78159175"
---
# <a name="delegates"></a><span data-ttu-id="71931-103">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="71931-103">Delegates</span></span>

<span data-ttu-id="71931-104">***Temsilci türü,*** belirli bir parametre listesi ve dönüş türüne sahip yöntemlere yapılan başvuruları temsil eder.</span><span class="sxs-lookup"><span data-stu-id="71931-104">A ***delegate type*** represents references to methods with a particular parameter list and return type.</span></span> <span data-ttu-id="71931-105">Temsilciler, yöntemleri değişkenlere atanabilen ve parametre olarak geçirilebilen varlıklar olarak ele alabilen varlıklar olarak ele alabilmektir.</span><span class="sxs-lookup"><span data-stu-id="71931-105">Delegates make it possible to treat methods as entities that can be assigned to variables and passed as parameters.</span></span> <span data-ttu-id="71931-106">Temsilciler, diğer bazı dillerde bulunan işlev işaretçileri kavramına benzer.</span><span class="sxs-lookup"><span data-stu-id="71931-106">Delegates are similar to the concept of function pointers found in some other languages.</span></span> <span data-ttu-id="71931-107">Işlev işaretçilerinaksine, temsilciler nesne yönelimli ve tür güvenlidir.</span><span class="sxs-lookup"><span data-stu-id="71931-107">Unlike function pointers, delegates are object-oriented and type-safe.</span></span>

<span data-ttu-id="71931-108">Aşağıdaki örnek, .. `Function`</span><span class="sxs-lookup"><span data-stu-id="71931-108">The following example declares and uses a delegate type named `Function`.</span></span>

[!code-csharp[DelegateExample](../../../samples/snippets/csharp/tour/delegates/Program.cs#L3-L37)]

<span data-ttu-id="71931-109">`Function` Temsilci türünün bir örneği, bağımsız değişken alan ve bir değer döndüren herhangi bir `double` `double` yönteme başvurur.</span><span class="sxs-lookup"><span data-stu-id="71931-109">An instance of the `Function` delegate type can reference any method that takes a `double` argument and returns a `double` value.</span></span> <span data-ttu-id="71931-110">Yöntem, `Apply` bir , sonuçları ile a `double[]` `double[]` dönen elemanları için verilen bir İşlev uygular.</span><span class="sxs-lookup"><span data-stu-id="71931-110">The `Apply` method applies a given Function to the elements of a `double[]`, returning a `double[]` with the results.</span></span> <span data-ttu-id="71931-111">`Main` Yöntemde, `Apply` bir `double[]`üç farklı işlevleri uygulamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="71931-111">In the `Main` method, `Apply` is used to apply three different functions to a `double[]`.</span></span>

<span data-ttu-id="71931-112">Temsilci, statik bir yönteme `Square` (önceki `Math.Sin` örnekte gibi) veya örnek yöntemine (önceki örnekte olduğu gibi) `m.Multiply` başvuru yapabilir.</span><span class="sxs-lookup"><span data-stu-id="71931-112">A delegate can reference either a static method (such as `Square` or `Math.Sin` in the previous example) or an instance method (such as `m.Multiply` in the previous example).</span></span> <span data-ttu-id="71931-113">Örnek bir yönteme başvuran bir temsilci de belirli bir nesneye başvurur ve örnek `this` yöntemi temsilci aracılığıyla çağrıldığında, bu nesne çağırmada olur.</span><span class="sxs-lookup"><span data-stu-id="71931-113">A delegate that references an instance method also references a particular object, and when the instance method is invoked through the delegate, that object becomes `this` in the invocation.</span></span>

<span data-ttu-id="71931-114">Temsilciler, beyan edildiğinde oluşturulan "satır dışı yöntemler" olan anonim işlevler kullanılarak da oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="71931-114">Delegates can also be created using anonymous functions, which are "inline methods" that are created when declared.</span></span> <span data-ttu-id="71931-115">Anonim işlevler, çevreleyen yöntemlerin yerel değişkenlerini görebilir.</span><span class="sxs-lookup"><span data-stu-id="71931-115">Anonymous functions can see the local variables of the surrounding methods.</span></span> <span data-ttu-id="71931-116">Aşağıdaki örnek bir sınıf oluşturmaz:</span><span class="sxs-lookup"><span data-stu-id="71931-116">The following example doesn't create a class:</span></span>

[!code-csharp[LambdaExample](../../../samples/snippets/csharp/tour/delegates/Program.cs#L44-L44)]

<span data-ttu-id="71931-117">Bir temsilci, başvurulmadığı yöntemin sınıfını bilmez veya önemsemaz; önemli olan tek şey, başvurulan yöntemin temsilciyle aynı parametrelere ve dönüş türüne sahip olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="71931-117">A delegate doesn't know or care about the class of the method it references; all that matters is that the referenced method has the same parameters and return type as the delegate.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="71931-118">[Önceki](interfaces.md)
>[Sonraki](attributes.md)</span><span class="sxs-lookup"><span data-stu-id="71931-118">[Previous](interfaces.md)
[Next](attributes.md)</span></span>
