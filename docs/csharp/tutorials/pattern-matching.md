---
title: Veri türlerini genişletmek için model eşleştirme özelliklerini kullanma
description: Bu gelişmiş öğreticide, ayrı olarak oluşturulan verileri ve algoritmaları kullanarak işlevsellik oluşturmak için model eşleştirme tekniklerini nasıl kullanabileceğiniz gösterilmektedir.
ms.date: 03/13/2019
ms-technology: csharp-whats-new
ms.custom: mvc
ms.openlocfilehash: fd08e707402bfcd552997111a9c3fa58841a5466
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/03/2020
ms.locfileid: "78240060"
---
# <a name="tutorial-using-pattern-matching-features-to-extend-data-types"></a><span data-ttu-id="13c2a-103">Öğretici: veri türlerini genişletmek için model eşleştirme özelliklerini kullanma</span><span class="sxs-lookup"><span data-stu-id="13c2a-103">Tutorial: Using pattern matching features to extend data types</span></span>

<span data-ttu-id="13c2a-104">C#7 temel desenler eşleşen özellikler sunmuştur.</span><span class="sxs-lookup"><span data-stu-id="13c2a-104">C# 7 introduced basic pattern matching features.</span></span> <span data-ttu-id="13c2a-105">Bu özellikler yeni ifadelerle ve C# desenlerle 8 ' de genişletilir.</span><span class="sxs-lookup"><span data-stu-id="13c2a-105">Those features are extended in C# 8 with new expressions and patterns.</span></span> <span data-ttu-id="13c2a-106">Başka kitaplıklarda olabilecek türleri genişletmekle birlikte davranan işlevselliği yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="13c2a-106">You can write functionality that behaves as though you extended types that may be in other libraries.</span></span> <span data-ttu-id="13c2a-107">Desenler için başka bir kullanım, uygulamanızın genişletilmekte olan türün temel bir özelliği olmayan bir işlev oluşturmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="13c2a-107">Another use for patterns is to create functionality your application requires that isn't a fundamental feature of the type being extended.</span></span>

<span data-ttu-id="13c2a-108">Bu öğreticide şunların nasıl yapıldığını öğreneceksiniz:</span><span class="sxs-lookup"><span data-stu-id="13c2a-108">In this tutorial, you'll learn how to:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="13c2a-109">Model eşleştirmesinin kullanılması gereken durumları tanıyın.</span><span class="sxs-lookup"><span data-stu-id="13c2a-109">Recognize situations where pattern matching should be used.</span></span>
> - <span data-ttu-id="13c2a-110">Türleri ve özellik değerlerini temel alan davranışı uygulamak için kalıp eşleştirme ifadelerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="13c2a-110">Use pattern matching expressions to implement behavior based on types and property values.</span></span>
> - <span data-ttu-id="13c2a-111">Tüm algoritmalar oluşturmak için model eşleştirmeyi diğer tekniklerle birleştirin.</span><span class="sxs-lookup"><span data-stu-id="13c2a-111">Combine pattern matching with other techniques to create complete algorithms.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="13c2a-112">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="13c2a-112">Prerequisites</span></span>

<span data-ttu-id="13c2a-113">Makinenizi, C# 8,0 derleyicisi dahil .NET Core çalıştıracak şekilde ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="13c2a-113">You’ll need to set up your machine to run .NET Core, including the C# 8.0 compiler.</span></span> <span data-ttu-id="13c2a-114">8 C# derleyicisi, [Visual Studio 2019 sürüm 16,3](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) veya [.NET Core 3,0 SDK](https://dotnet.microsoft.com/download)ile başlayarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="13c2a-114">The C# 8 compiler is available starting with [Visual Studio 2019 version 16.3](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) or [.NET Core 3.0 SDK](https://dotnet.microsoft.com/download).</span></span>

<span data-ttu-id="13c2a-115">Bu öğreticide, Visual Studio veya C# .NET Core CLI dahil olmak üzere, .net hakkında bilgi sahibi olduğunuz varsayılır.</span><span class="sxs-lookup"><span data-stu-id="13c2a-115">This tutorial assumes you're familiar with C# and .NET, including either Visual Studio or the .NET Core CLI.</span></span>

## <a name="scenarios-for-pattern-matching"></a><span data-ttu-id="13c2a-116">Model eşleştirme senaryoları</span><span class="sxs-lookup"><span data-stu-id="13c2a-116">Scenarios for pattern matching</span></span>

<span data-ttu-id="13c2a-117">Modern geliştirme genellikle birden çok kaynaktaki verilerin tümleştirilmesine ve bu verilerden tek bir ortak uygulamada bilgi ve Öngörüler sunmaya dahildir.</span><span class="sxs-lookup"><span data-stu-id="13c2a-117">Modern development often includes integrating data from multiple sources and presenting information and insights from that data in a single cohesive application.</span></span> <span data-ttu-id="13c2a-118">Siz ve takımınız gelen verileri temsil eden tüm türler için denetime veya erişime sahip olmayacaktır.</span><span class="sxs-lookup"><span data-stu-id="13c2a-118">You and your team won't have control or access for all the types that represent the incoming data.</span></span>

<span data-ttu-id="13c2a-119">Klasik nesne odaklı tasarım, uygulamanızda, bu birden çok veri kaynağından her bir veri türünü temsil eden türler oluşturmak için çağrı yapılır.</span><span class="sxs-lookup"><span data-stu-id="13c2a-119">The classic object-oriented design would call for creating types in your application that represent each data type from those multiple data sources.</span></span> <span data-ttu-id="13c2a-120">Daha sonra uygulamanız bu yeni türlerle çalışarak devralma hiyerarşileri oluşturun, sanal yöntemler oluşturur ve soyutlamalar uygular.</span><span class="sxs-lookup"><span data-stu-id="13c2a-120">Then, your application would work with those new types, build inheritance hierarchies, create virtual methods, and implement abstractions.</span></span> <span data-ttu-id="13c2a-121">Bu teknikler çalışır ve bazen en iyi araçlardır.</span><span class="sxs-lookup"><span data-stu-id="13c2a-121">Those techniques work, and sometimes they are the best tools.</span></span> <span data-ttu-id="13c2a-122">Diğer zamanlarda da daha az kod yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="13c2a-122">Other times you can write less code.</span></span> <span data-ttu-id="13c2a-123">Verileri işleyen işlemlerden verileri ayıran teknikleri kullanarak daha fazla şifresiz kod yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="13c2a-123">You can write more clear code using techniques that separate the data from the operations that manipulate that data.</span></span>

<span data-ttu-id="13c2a-124">Bu öğreticide, tek bir senaryo için çeşitli dış kaynaklardan gelen verileri alan bir uygulama oluşturacaksınız ve keşfedeceğiz.</span><span class="sxs-lookup"><span data-stu-id="13c2a-124">In this tutorial, you'll create and explore an application that takes incoming data from several external sources for a single scenario.</span></span> <span data-ttu-id="13c2a-125">**Düzenin** , bu verileri özgün sistemin parçası olmayan yollarla tüketmek ve işlemek için etkili bir yol sağladığını görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="13c2a-125">You'll see how **pattern matching** provides an efficient way to consume and process that data in ways that weren't part of the original system.</span></span>

<span data-ttu-id="13c2a-126">Trafiği yönetmek için Tolls ve yoğun zaman fiyatlandırması kullanan bir ana metropol alanı düşünün.</span><span class="sxs-lookup"><span data-stu-id="13c2a-126">Consider a major metropolitan area that is using tolls and peak time pricing to manage traffic.</span></span> <span data-ttu-id="13c2a-127">Türüne göre bir araç için Tolls 'yi hesaplayan bir uygulama yazarsınız.</span><span class="sxs-lookup"><span data-stu-id="13c2a-127">You write an application that calculates tolls for a vehicle based on its type.</span></span> <span data-ttu-id="13c2a-128">Daha sonraki geliştirmeler, araç çubuğundaki alan sayısına göre fiyatlandırmaya dahil değildir.</span><span class="sxs-lookup"><span data-stu-id="13c2a-128">Later enhancements incorporate pricing based on the number of occupants in the vehicle.</span></span> <span data-ttu-id="13c2a-129">Daha fazla geliştirmeler, haftanın saatine ve gününe göre fiyatlandırma ekler.</span><span class="sxs-lookup"><span data-stu-id="13c2a-129">Further enhancements add pricing based on the time and the day of the week.</span></span>

<span data-ttu-id="13c2a-130">Bu kısa açıklamadan, bu sistemi modellemek için bir nesne hiyerarşisinde hızlıca taslak oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="13c2a-130">From that brief description, you may have quickly sketched out an object hierarchy to model this system.</span></span> <span data-ttu-id="13c2a-131">Ancak, verileriniz diğer araç kayıt yönetimi sistemleri gibi birden çok kaynaktan geliyor.</span><span class="sxs-lookup"><span data-stu-id="13c2a-131">However, your data is coming from multiple sources like other vehicle registration management systems.</span></span> <span data-ttu-id="13c2a-132">Bu sistemler, verileri modellemek için farklı sınıflar sağlar ve kullanabileceğiniz tek bir nesne modeli yoktur.</span><span class="sxs-lookup"><span data-stu-id="13c2a-132">These systems provide different classes to model that data and you don't have a single object model you can use.</span></span> <span data-ttu-id="13c2a-133">Bu öğreticide, aşağıdaki kodda gösterildiği gibi bu dış sistemlerden araç verilerini modellemek için bu Basitleştirilmiş sınıfları kullanacaksınız:</span><span class="sxs-lookup"><span data-stu-id="13c2a-133">In this tutorial, you'll use these simplified classes to model for the vehicle data from these external systems, as shown in the following code:</span></span>

[!code-csharp[ExternalSystems](~/samples/snippets/csharp/tutorials/patterns/start/toll-calculator/ExternalSystems.cs)]

<span data-ttu-id="13c2a-134">Başlangıç kodunu [DotNet/Samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/patterns/start) GitHub deposundan indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="13c2a-134">You can download the starter code from the [dotnet/samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/patterns/start) GitHub repository.</span></span> <span data-ttu-id="13c2a-135">Araç sınıflarının farklı sistemlerden olduğunu ve farklı ad alanlarında olduğunu görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="13c2a-135">You can see that the vehicle classes are from different systems, and are in different namespaces.</span></span> <span data-ttu-id="13c2a-136">`System.Object` dışındaki ortak bir temel sınıf yararlanılabilir olabilir.</span><span class="sxs-lookup"><span data-stu-id="13c2a-136">No common base class, other than `System.Object` can be leveraged.</span></span>

## <a name="pattern-matching-designs"></a><span data-ttu-id="13c2a-137">Desen eşleştirme tasarımları</span><span class="sxs-lookup"><span data-stu-id="13c2a-137">Pattern matching designs</span></span>

<span data-ttu-id="13c2a-138">Bu öğreticide kullanılan senaryo, düzenin eşleşmesi için uygun olan sorun türlerini vurgular:</span><span class="sxs-lookup"><span data-stu-id="13c2a-138">The scenario used in this tutorial highlights the kinds of problems that pattern matching is well-suited to solve:</span></span>

- <span data-ttu-id="13c2a-139">Çalışmanız gereken nesneler, hedeflerinizle eşleşen bir nesne hiyerarşisinde değildir.</span><span class="sxs-lookup"><span data-stu-id="13c2a-139">The objects you need to work with aren't in an object hierarchy that matches your goals.</span></span> <span data-ttu-id="13c2a-140">İlişkisiz sistemlerin parçası olan sınıflarla çalışıyor olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="13c2a-140">You may be working with classes that are part of unrelated systems.</span></span>
- <span data-ttu-id="13c2a-141">Eklemekte olduğunuz işlevsellik, bu sınıfların temel soyutlama kapsamında değildir.</span><span class="sxs-lookup"><span data-stu-id="13c2a-141">The functionality you're adding isn't part of the core abstraction for these classes.</span></span> <span data-ttu-id="13c2a-142">Bir araç tarafından ücretli bir araç, farklı araç türlerine göre *değişir* ancak ücretli bir temel işlev değildir.</span><span class="sxs-lookup"><span data-stu-id="13c2a-142">The toll paid by a vehicle *changes* for different types of vehicles, but the toll isn't a core function of the vehicle.</span></span>

<span data-ttu-id="13c2a-143">Verilerin *şekli* ve bu verilerdeki *işlemler* birlikte açıklanmadığında, ' deki C# model eşleme özellikleri ile çalışmayı kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="13c2a-143">When the *shape* of the data and the *operations* on that data are not described together, the pattern matching features in C# make it easier to work with.</span></span>

## <a name="implement-the-basic-toll-calculations"></a><span data-ttu-id="13c2a-144">Temel ücretli hesaplamaları uygulayın</span><span class="sxs-lookup"><span data-stu-id="13c2a-144">Implement the basic toll calculations</span></span>

<span data-ttu-id="13c2a-145">En temel ücretli hesaplama yalnızca araç türüne bağlıdır:</span><span class="sxs-lookup"><span data-stu-id="13c2a-145">The most basic toll calculation relies only on the vehicle type:</span></span>

- <span data-ttu-id="13c2a-146">`Car` $2,00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="13c2a-146">A `Car` is $2.00.</span></span>
- <span data-ttu-id="13c2a-147">`Taxi` $3,50 ' dir.</span><span class="sxs-lookup"><span data-stu-id="13c2a-147">A `Taxi` is $3.50.</span></span>
- <span data-ttu-id="13c2a-148">`Bus` $5,00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="13c2a-148">A `Bus` is $5.00.</span></span>
- <span data-ttu-id="13c2a-149">`DeliveryTruck` $10,00</span><span class="sxs-lookup"><span data-stu-id="13c2a-149">A `DeliveryTruck` is $10.00</span></span>

<span data-ttu-id="13c2a-150">Yeni bir `TollCalculator` sınıfı oluşturun ve ücretli miktarı almak için araç türünde kalıp eşleştirmeyi uygulayın.</span><span class="sxs-lookup"><span data-stu-id="13c2a-150">Create a new `TollCalculator` class, and implement pattern matching on the vehicle type to get the toll amount.</span></span> <span data-ttu-id="13c2a-151">Aşağıdaki kod `TollCalculator`ilk uygulamasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="13c2a-151">The following code shows the initial implementation of the `TollCalculator`.</span></span>

```csharp
using System;
using CommercialRegistration;
using ConsumerVehicleRegistration;
using LiveryRegistration;

namespace toll_calculator
{
    public class TollCalculator
    {
        public decimal CalculateToll(object vehicle) =>
            vehicle switch
        {
            Car c           => 2.00m,
            Taxi t          => 3.50m,
            Bus b           => 5.00m,
            DeliveryTruck t => 10.00m,
            { }             => throw new ArgumentException(message: "Not a known vehicle type", paramName: nameof(vehicle)),
            null            => throw new ArgumentNullException(nameof(vehicle))
        };
    }
}
```

<span data-ttu-id="13c2a-152">Yukarıdaki kod, **tür modelini**test eden bir **switch ifadesi** (bir [`switch`](../language-reference/keywords/switch.md) ifadesiyle aynı değildir) kullanır.</span><span class="sxs-lookup"><span data-stu-id="13c2a-152">The preceding code uses a **switch expression** (not the same as a [`switch`](../language-reference/keywords/switch.md) statement) that tests the **type pattern**.</span></span> <span data-ttu-id="13c2a-153">Bir **switch ifadesi** , önceki kodda `vehicle` ve ardından `switch` anahtar sözcüğü ile başlar.</span><span class="sxs-lookup"><span data-stu-id="13c2a-153">A **switch expression** begins with the variable, `vehicle` in the preceding code, followed by the `switch` keyword.</span></span> <span data-ttu-id="13c2a-154">Ardından, küme ayraçları içindeki tüm **anahtar kolları** gelir.</span><span class="sxs-lookup"><span data-stu-id="13c2a-154">Next comes all the **switch arms** inside curly braces.</span></span> <span data-ttu-id="13c2a-155">`switch` ifadesi, `switch` deyimini çevreleyen söz dizimi için diğer işlevselliklerindeki yapar.</span><span class="sxs-lookup"><span data-stu-id="13c2a-155">The `switch` expression makes other refinements to the syntax that surrounds the `switch` statement.</span></span> <span data-ttu-id="13c2a-156">`case` anahtar sözcüğü atlanır ve her bir ARM 'nin sonucu bir ifadedir.</span><span class="sxs-lookup"><span data-stu-id="13c2a-156">The `case` keyword is omitted, and the result of each arm is an expression.</span></span> <span data-ttu-id="13c2a-157">Son iki kolonun yeni bir dil özelliği gösterir.</span><span class="sxs-lookup"><span data-stu-id="13c2a-157">The last two arms show a new language feature.</span></span> <span data-ttu-id="13c2a-158">`{ }` Case, önceki bir ARM ile eşleşmeyen null olmayan tüm nesneler ile eşleşir.</span><span class="sxs-lookup"><span data-stu-id="13c2a-158">The `{ }` case matches any non-null object that didn't match an earlier arm.</span></span> <span data-ttu-id="13c2a-159">Bu ARM, bu yönteme geçirilen hatalı türleri yakalar.</span><span class="sxs-lookup"><span data-stu-id="13c2a-159">This arm catches any incorrect types passed to this method.</span></span>  <span data-ttu-id="13c2a-160">`{ }` durum, her bir araç türü için durumları izlemelidir.</span><span class="sxs-lookup"><span data-stu-id="13c2a-160">The `{ }` case must follow the cases for each vehicle type.</span></span> <span data-ttu-id="13c2a-161">Sıra tersine çevrilirse, `{ }` durumu öncelik kazanır.</span><span class="sxs-lookup"><span data-stu-id="13c2a-161">If the order were reversed, the `{ }` case would take precedence.</span></span> <span data-ttu-id="13c2a-162">Son olarak, `null` deseninin bu yönteme bir `null` geçtiğini algılar.</span><span class="sxs-lookup"><span data-stu-id="13c2a-162">Finally, the `null` pattern detects when a `null` is passed to this method.</span></span> <span data-ttu-id="13c2a-163">Diğer tür desenleri doğru türdeki yalnızca null olmayan bir nesneyle eşleştiğinden `null` deseni son olabilir.</span><span class="sxs-lookup"><span data-stu-id="13c2a-163">The `null` pattern can be last because the other type patterns match only a non-null object of the correct type.</span></span>

<span data-ttu-id="13c2a-164">`Program.cs`' de aşağıdaki kodu kullanarak bu kodu test edebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="13c2a-164">You can test this code using the following code in `Program.cs`:</span></span>

```csharp
using System;
using CommercialRegistration;
using ConsumerVehicleRegistration;
using LiveryRegistration;

namespace toll_calculator
{
    class Program
    {
        static void Main(string[] args)
        {
            var tollCalc = new TollCalculator();

            var car = new Car();
            var taxi = new Taxi();
            var bus = new Bus();
            var truck = new DeliveryTruck();

            Console.WriteLine($"The toll for a car is {tollCalc.CalculateToll(car)}");
            Console.WriteLine($"The toll for a taxi is {tollCalc.CalculateToll(taxi)}");
            Console.WriteLine($"The toll for a bus is {tollCalc.CalculateToll(bus)}");
            Console.WriteLine($"The toll for a truck is {tollCalc.CalculateToll(truck)}");

            try
            {
                tollCalc.CalculateToll("this will fail");
            }
            catch (ArgumentException e)
            {
                Console.WriteLine("Caught an argument exception when using the wrong type");
            }
            try
            {
                tollCalc.CalculateToll(null);
            }
            catch (ArgumentNullException e)
            {
                Console.WriteLine("Caught an argument exception when using null");
            }
        }
    }
}
```

<span data-ttu-id="13c2a-165">Bu kod, başlatıcı projesine dahil edilmiştir, ancak açıklama eklenir. Açıklamaları kaldırın ve ne yazdığınızı test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="13c2a-165">That code is included in the starter project, but is commented out. Remove the comments, and you can test what you've written.</span></span>

<span data-ttu-id="13c2a-166">Desenlerin kodun ve verilerin ayrı olduğu algoritmalar oluşturmanıza nasıl yardımcı olduğunu görmeyi başlıyoruz.</span><span class="sxs-lookup"><span data-stu-id="13c2a-166">You're starting to see how patterns can help you create algorithms where the code and the data are separate.</span></span> <span data-ttu-id="13c2a-167">`switch` ifade, türü sınar ve sonuçlara göre farklı değerler üretir.</span><span class="sxs-lookup"><span data-stu-id="13c2a-167">The `switch` expression tests the type and produces different values based on the results.</span></span> <span data-ttu-id="13c2a-168">Bu yalnızca başlangıç amaçlıdır.</span><span class="sxs-lookup"><span data-stu-id="13c2a-168">That's only the beginning.</span></span>

## <a name="add-occupancy-pricing"></a><span data-ttu-id="13c2a-169">İskan fiyatlandırması Ekle</span><span class="sxs-lookup"><span data-stu-id="13c2a-169">Add occupancy pricing</span></span>

<span data-ttu-id="13c2a-170">Ücretli yetkili, en yüksek kapasiteden gezilerin gezmelerini teşvik etmek istiyor.</span><span class="sxs-lookup"><span data-stu-id="13c2a-170">The toll authority wants to encourage vehicles to travel at maximum capacity.</span></span> <span data-ttu-id="13c2a-171">Araçlar daha az pastlar olduğunda daha fazla ücret ödemelerine ve daha düşük fiyatlandırma sunarak tam bir şekilde teşvik etmeye karar vermiştir:</span><span class="sxs-lookup"><span data-stu-id="13c2a-171">They've decided to charge more when vehicles have fewer passengers, and encourage full vehicles by offering lower pricing:</span></span>

- <span data-ttu-id="13c2a-172">Otomobiller ve Tax, hiçbir Pasca, ek $0,50 ödeyebilir.</span><span class="sxs-lookup"><span data-stu-id="13c2a-172">Cars and taxis with no passengers pay an extra $0.50.</span></span>
- <span data-ttu-id="13c2a-173">Otomobiller ve Tax, iki pasa, $0,50 indirimi alır.</span><span class="sxs-lookup"><span data-stu-id="13c2a-173">Cars and taxis with two passengers get a $0.50 discount.</span></span>
- <span data-ttu-id="13c2a-174">Üç veya daha fazla Pascal ile otomobiller ve Tax, $1,00 indirimi alır.</span><span class="sxs-lookup"><span data-stu-id="13c2a-174">Cars and taxis with three or more passengers get a $1.00 discount.</span></span>
- <span data-ttu-id="13c2a-175">%50 ' den küçük veri yolları, fazladan $2,00 oranında ödeyin.</span><span class="sxs-lookup"><span data-stu-id="13c2a-175">Buses that are less than 50% full pay an extra $2.00.</span></span>
- <span data-ttu-id="13c2a-176">%90 ' den fazla tam veri yolları $1,00 indirimi elde edin.</span><span class="sxs-lookup"><span data-stu-id="13c2a-176">Buses that are more than 90% full get a $1.00 discount.</span></span>

<span data-ttu-id="13c2a-177">Bu kurallar, aynı anahtar ifadesinde **özellik düzeniyle** kullanılarak uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="13c2a-177">These rules can be implemented using the **property pattern** in the same switch expression.</span></span> <span data-ttu-id="13c2a-178">Özellik deseninin türü belirlendikten sonra nesnenin özellikleri incelenir.</span><span class="sxs-lookup"><span data-stu-id="13c2a-178">The property pattern examines properties of the object once the type has been determined.</span></span> <span data-ttu-id="13c2a-179">`Car` için tek durum dört farklı durumda genişler:</span><span class="sxs-lookup"><span data-stu-id="13c2a-179">The single case for a `Car` expands to four different cases:</span></span>

```csharp
vehicle switch
{
    Car { Passengers: 0}        => 2.00m + 0.50m,
    Car { Passengers: 1 }       => 2.0m,
    Car { Passengers: 2}        => 2.0m - 0.50m,
    Car c                       => 2.00m - 1.0m,

    // ...
};
```

<span data-ttu-id="13c2a-180">İlk üç durum türü `Car`olarak test edin ve sonra `Passengers` özelliğinin değerini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="13c2a-180">The first three cases test the type as a `Car`, then check the value of the `Passengers` property.</span></span> <span data-ttu-id="13c2a-181">Her ikisi de eşleşiyorsa, bu ifade değerlendirilir ve döndürülür.</span><span class="sxs-lookup"><span data-stu-id="13c2a-181">If both match, that expression is evaluated and returned.</span></span>

<span data-ttu-id="13c2a-182">Ayrıca, taxiçin de benzer bir şekilde durum da genişletebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="13c2a-182">You would also expand the cases for taxis in a similar manner:</span></span>

```csharp
vehicle switch
{
    // ...

    Taxi { Fares: 0}  => 3.50m + 1.00m,
    Taxi { Fares: 1 } => 3.50m,
    Taxi { Fares: 2}  => 3.50m - 0.50m,
    Taxi t            => 3.50m - 1.00m,

    // ...
};
```

<span data-ttu-id="13c2a-183">Yukarıdaki örnekte, son durumda `when` yan tümcesi atlandı.</span><span class="sxs-lookup"><span data-stu-id="13c2a-183">In the preceding example, the `when` clause was omitted on the final case.</span></span>

<span data-ttu-id="13c2a-184">Ardından, aşağıdaki örnekte gösterildiği gibi, veri yolları için durumları genişleterek sahiplik kurallarını uygulayın:</span><span class="sxs-lookup"><span data-stu-id="13c2a-184">Next, implement the occupancy rules by expanding the cases for buses, as shown in the following example:</span></span>

```csharp
vehicle switch
{
    // ...

    Bus b when ((double)b.Riders / (double)b.Capacity) < 0.50 => 5.00m + 2.00m,
    Bus b when ((double)b.Riders / (double)b.Capacity) > 0.90 => 5.00m - 1.00m,
    Bus b => 5.00m,

    // ...
};
```

<span data-ttu-id="13c2a-185">Ücretli yetkili, teslim kamyonları içindeki pastıcılar sayısıyla ilgilenmez.</span><span class="sxs-lookup"><span data-stu-id="13c2a-185">The toll authority isn't concerned with the number of passengers in the delivery trucks.</span></span> <span data-ttu-id="13c2a-186">Bunun yerine, aşağıdaki gibi, kamyonlar ağırlık sınıfına göre ücretli miktarı ayarlar:</span><span class="sxs-lookup"><span data-stu-id="13c2a-186">Instead, they adjust the toll amount based on the weight class of the trucks as follows:</span></span>

- <span data-ttu-id="13c2a-187">5000 lbs üzerinde structuralks, fazladan $5,00 ücretlendirilir.</span><span class="sxs-lookup"><span data-stu-id="13c2a-187">Trucks over 5000 lbs are charged an extra $5.00.</span></span>
- <span data-ttu-id="13c2a-188">3000 lbs kapsamında hafif bir $2,00 indirimi verilir.</span><span class="sxs-lookup"><span data-stu-id="13c2a-188">Light trucks under 3000 lbs are given a $2.00 discount.</span></span>

<span data-ttu-id="13c2a-189">Bu kural aşağıdaki kodla uygulanır:</span><span class="sxs-lookup"><span data-stu-id="13c2a-189">That rule is implemented with the following code:</span></span>

```csharp
vehicle switch
{
    // ...

    DeliveryTruck t when (t.GrossWeightClass > 5000) => 10.00m + 5.00m,
    DeliveryTruck t when (t.GrossWeightClass < 3000) => 10.00m - 2.00m,
    DeliveryTruck t => 10.00m,
};
```

<span data-ttu-id="13c2a-190">Yukarıdaki kod, anahtar ARM 'nin `when` yan tümcesini gösterir.</span><span class="sxs-lookup"><span data-stu-id="13c2a-190">The preceding code shows the `when` clause of a switch arm.</span></span> <span data-ttu-id="13c2a-191">Bir özellikte eşitlik dışındaki koşulları test etmek için `when` yan tümcesini kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="13c2a-191">You use the `when` clause to test conditions other than equality on a property.</span></span> <span data-ttu-id="13c2a-192">İşiniz bittiğinde aşağıdakine benzer bir yönteme sahip olacaksınız:</span><span class="sxs-lookup"><span data-stu-id="13c2a-192">When you've finished, you'll have a method that looks much like the following:</span></span>

```csharp
vehicle switch
{
    Car { Passengers: 0}        => 2.00m + 0.50m,
    Car { Passengers: 1}        => 2.0m,
    Car { Passengers: 2}        => 2.0m - 0.50m,
    Car c                       => 2.00m - 1.0m,

    Taxi { Fares: 0}  => 3.50m + 1.00m,
    Taxi { Fares: 1 } => 3.50m,
    Taxi { Fares: 2}  => 3.50m - 0.50m,
    Taxi t            => 3.50m - 1.00m,

    Bus b when ((double)b.Riders / (double)b.Capacity) < 0.50 => 5.00m + 2.00m,
    Bus b when ((double)b.Riders / (double)b.Capacity) > 0.90 => 5.00m - 1.00m,
    Bus b => 5.00m,

    DeliveryTruck t when (t.GrossWeightClass > 5000) => 10.00m + 5.00m,
    DeliveryTruck t when (t.GrossWeightClass < 3000) => 10.00m - 2.00m,
    DeliveryTruck t => 10.00m,
    
    { }     => throw new ArgumentException(message: "Not a known vehicle type", paramName: nameof(vehicle)),
    null    => throw new ArgumentNullException(nameof(vehicle))
};
```

<span data-ttu-id="13c2a-193">Bu anahtar kolları çoğu **özyinelemeli desenlere**örnektir.</span><span class="sxs-lookup"><span data-stu-id="13c2a-193">Many of these switch arms are examples of **recursive patterns**.</span></span> <span data-ttu-id="13c2a-194">Örneğin `Car { Passengers: 1}`, bir özellik deseninin içinde sabit bir model gösterir.</span><span class="sxs-lookup"><span data-stu-id="13c2a-194">For example, `Car { Passengers: 1}` shows a constant pattern inside a property pattern.</span></span>

<span data-ttu-id="13c2a-195">İç içe geçmiş anahtarlar kullanarak bu kodu daha az tekrarlı hale getirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="13c2a-195">You can make this code less repetitive by using nested switches.</span></span> <span data-ttu-id="13c2a-196">`Car` ve `Taxi` her ikisi de önceki örneklerde dört farklı kollu bir sahiptir.</span><span class="sxs-lookup"><span data-stu-id="13c2a-196">The `Car` and `Taxi` both have four different arms in the preceding examples.</span></span> <span data-ttu-id="13c2a-197">Her iki durumda da, bir özellik düzeninde akışlara bir tür stili oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="13c2a-197">In both cases, you can create a type pattern that feeds into a property pattern.</span></span> <span data-ttu-id="13c2a-198">Bu teknik aşağıdaki kodda gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="13c2a-198">This technique is shown in the following code:</span></span>

```csharp
public decimal CalculateToll(object vehicle) =>
    vehicle switch
    {
        Car c => c.Passengers switch
        {
            0 => 2.00m + 0.5m,
            1 => 2.0m,
            2 => 2.0m - 0.5m,
            _ => 2.00m - 1.0m
        },

        Taxi t => t.Fares switch
        {
            0 => 3.50m + 1.00m,
            1 => 3.50m,
            2 => 3.50m - 0.50m,
            _ => 3.50m - 1.00m
        },

        Bus b when ((double)b.Riders / (double)b.Capacity) < 0.50 => 5.00m + 2.00m,
        Bus b when ((double)b.Riders / (double)b.Capacity) > 0.90 => 5.00m - 1.00m,
        Bus b => 5.00m,

        DeliveryTruck t when (t.GrossWeightClass > 5000) => 10.00m + 5.00m,
        DeliveryTruck t when (t.GrossWeightClass < 3000) => 10.00m - 2.00m,
        DeliveryTruck t => 10.00m,

        { }  => throw new ArgumentException(message: "Not a known vehicle type", paramName: nameof(vehicle)),
        null => throw new ArgumentNullException(nameof(vehicle))
    };
```

<span data-ttu-id="13c2a-199">Önceki örnekte, özyinelemeli bir ifade kullanılması, özellik değerini test eden alt kolları içeren `Car` ve `Taxi` kolları yinelemediğiniz anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="13c2a-199">In the preceding sample, using a recursive expression means you don't repeat the `Car` and `Taxi` arms containing child arms that test the property value.</span></span> <span data-ttu-id="13c2a-200">Bu özellikler, `Bus` ve `DeliveryTruck` kolları için kullanılmaz, çünkü bu Koller özellik için aralıkları test ettiğinden ayrık değerler değildir.</span><span class="sxs-lookup"><span data-stu-id="13c2a-200">This technique isn't used for the `Bus` and `DeliveryTruck` arms because those arms are testing ranges for the property, not discrete values.</span></span>

## <a name="add-peak-pricing"></a><span data-ttu-id="13c2a-201">Tepe fiyatlandırması Ekle</span><span class="sxs-lookup"><span data-stu-id="13c2a-201">Add peak pricing</span></span>

<span data-ttu-id="13c2a-202">Son özellik için, ücretli yetkili zamana duyarlı tepe fiyatlandırması eklemek istemektedir.</span><span class="sxs-lookup"><span data-stu-id="13c2a-202">For the final feature, the toll authority wants to add time sensitive peak pricing.</span></span> <span data-ttu-id="13c2a-203">Sabah ve akşam aceleniz saatlerinde, Tolls iki katına çıkar.</span><span class="sxs-lookup"><span data-stu-id="13c2a-203">During the morning and evening rush hours, the tolls are doubled.</span></span> <span data-ttu-id="13c2a-204">Bu kural yalnızca bir yönde trafiği etkiler: sabah şehrine gelen ve akşam aceleniz Hour 'daki çıkış.</span><span class="sxs-lookup"><span data-stu-id="13c2a-204">That rule only affects traffic in one direction: inbound to the city in the morning, and outbound in the evening rush hour.</span></span> <span data-ttu-id="13c2a-205">İş gününde diğer saatlerde, Tolls %50 oranında artar.</span><span class="sxs-lookup"><span data-stu-id="13c2a-205">During other times during the workday, tolls increase by 50%.</span></span> <span data-ttu-id="13c2a-206">Geç gece ve erken sabah, Tolls %25 oranında azaltılır.</span><span class="sxs-lookup"><span data-stu-id="13c2a-206">Late night and early morning, tolls are reduced by 25%.</span></span> <span data-ttu-id="13c2a-207">Hafta sonu sırasında, zamandan bağımsız olarak normal fiyat olur.</span><span class="sxs-lookup"><span data-stu-id="13c2a-207">During the weekend, it's the normal rate, regardless of the time.</span></span>

<span data-ttu-id="13c2a-208">Bu özellik için model eşleştirmeyi kullanacaksınız, ancak diğer tekniklerle tümleştirilecek.</span><span class="sxs-lookup"><span data-stu-id="13c2a-208">You'll use pattern matching for this feature, but you'll integrate it with other techniques.</span></span> <span data-ttu-id="13c2a-209">Tüm yön, hafta günü ve saat birleşimleri için hesap oluşturacak tek bir kalıp eşleştirme ifadesi oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="13c2a-209">You could build a single pattern match expression that would account for all the combinations of direction, day of the week, and time.</span></span> <span data-ttu-id="13c2a-210">Sonuç karmaşık bir ifade olacaktır.</span><span class="sxs-lookup"><span data-stu-id="13c2a-210">The result would be a complicated expression.</span></span> <span data-ttu-id="13c2a-211">Okunması zor olabilir.</span><span class="sxs-lookup"><span data-stu-id="13c2a-211">It would be hard to read and difficult to understand.</span></span> <span data-ttu-id="13c2a-212">Bu, doğruluğu garanti etmelerini zorlaştırır.</span><span class="sxs-lookup"><span data-stu-id="13c2a-212">That makes it hard to ensure correctness.</span></span> <span data-ttu-id="13c2a-213">Bunun yerine, öz 'in tüm bu durumları açıkladığı bir dizi değer oluşturmak için bu yöntemleri birleştirin.</span><span class="sxs-lookup"><span data-stu-id="13c2a-213">Instead, combine those methods to build a tuple of values that concisely describes all those states.</span></span> <span data-ttu-id="13c2a-214">Ardından, ücretli bir çarpanı hesaplamak için model eşleştirmeyi kullanın.</span><span class="sxs-lookup"><span data-stu-id="13c2a-214">Then use pattern matching to calculate a multiplier for the toll.</span></span> <span data-ttu-id="13c2a-215">Kayıt düzeni üç farklı koşul içerir:</span><span class="sxs-lookup"><span data-stu-id="13c2a-215">The tuple contains three discrete conditions:</span></span>

- <span data-ttu-id="13c2a-216">Gün, bir hafta içi veya bir hafta sonu olabilir.</span><span class="sxs-lookup"><span data-stu-id="13c2a-216">The day is either a weekday or a weekend.</span></span>
- <span data-ttu-id="13c2a-217">Ücretli sürenin toplanacağı zaman bandı.</span><span class="sxs-lookup"><span data-stu-id="13c2a-217">The band of time when the toll is collected.</span></span>
- <span data-ttu-id="13c2a-218">Yön City veya City 'den</span><span class="sxs-lookup"><span data-stu-id="13c2a-218">The direction is into the city or out of the city</span></span>

<span data-ttu-id="13c2a-219">Aşağıdaki tabloda, giriş değerleri ve en yüksek fiyatlandırma çarpanı birleşimleri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="13c2a-219">The following table shows the combinations of input values and the peak pricing multiplier:</span></span>

| <span data-ttu-id="13c2a-220">Gün</span><span class="sxs-lookup"><span data-stu-id="13c2a-220">Day</span></span>        | <span data-ttu-id="13c2a-221">Zaman</span><span class="sxs-lookup"><span data-stu-id="13c2a-221">Time</span></span>         | <span data-ttu-id="13c2a-222">Yön</span><span class="sxs-lookup"><span data-stu-id="13c2a-222">Direction</span></span> | <span data-ttu-id="13c2a-223">Premium</span><span class="sxs-lookup"><span data-stu-id="13c2a-223">Premium</span></span> |
| ---------- | ------------ | --------- |--------:|
| <span data-ttu-id="13c2a-224">HAFTANINGÜNÜ</span><span class="sxs-lookup"><span data-stu-id="13c2a-224">Weekday</span></span>    | <span data-ttu-id="13c2a-225">sabah aceleniz</span><span class="sxs-lookup"><span data-stu-id="13c2a-225">morning rush</span></span> | <span data-ttu-id="13c2a-226">gelen</span><span class="sxs-lookup"><span data-stu-id="13c2a-226">inbound</span></span>   | <span data-ttu-id="13c2a-227">x 2,00</span><span class="sxs-lookup"><span data-stu-id="13c2a-227">x 2.00</span></span>  |
| <span data-ttu-id="13c2a-228">HAFTANINGÜNÜ</span><span class="sxs-lookup"><span data-stu-id="13c2a-228">Weekday</span></span>    | <span data-ttu-id="13c2a-229">sabah aceleniz</span><span class="sxs-lookup"><span data-stu-id="13c2a-229">morning rush</span></span> | <span data-ttu-id="13c2a-230">giden</span><span class="sxs-lookup"><span data-stu-id="13c2a-230">outbound</span></span>  | <span data-ttu-id="13c2a-231">x 1,00</span><span class="sxs-lookup"><span data-stu-id="13c2a-231">x 1.00</span></span>  |
| <span data-ttu-id="13c2a-232">HAFTANINGÜNÜ</span><span class="sxs-lookup"><span data-stu-id="13c2a-232">Weekday</span></span>    | <span data-ttu-id="13c2a-233">saati</span><span class="sxs-lookup"><span data-stu-id="13c2a-233">daytime</span></span>      | <span data-ttu-id="13c2a-234">gelen</span><span class="sxs-lookup"><span data-stu-id="13c2a-234">inbound</span></span>   | <span data-ttu-id="13c2a-235">x 1,50</span><span class="sxs-lookup"><span data-stu-id="13c2a-235">x 1.50</span></span>  |
| <span data-ttu-id="13c2a-236">HAFTANINGÜNÜ</span><span class="sxs-lookup"><span data-stu-id="13c2a-236">Weekday</span></span>    | <span data-ttu-id="13c2a-237">saati</span><span class="sxs-lookup"><span data-stu-id="13c2a-237">daytime</span></span>      | <span data-ttu-id="13c2a-238">giden</span><span class="sxs-lookup"><span data-stu-id="13c2a-238">outbound</span></span>  | <span data-ttu-id="13c2a-239">x 1,50</span><span class="sxs-lookup"><span data-stu-id="13c2a-239">x 1.50</span></span>  |
| <span data-ttu-id="13c2a-240">HAFTANINGÜNÜ</span><span class="sxs-lookup"><span data-stu-id="13c2a-240">Weekday</span></span>    | <span data-ttu-id="13c2a-241">akşam aceleniz</span><span class="sxs-lookup"><span data-stu-id="13c2a-241">evening rush</span></span> | <span data-ttu-id="13c2a-242">gelen</span><span class="sxs-lookup"><span data-stu-id="13c2a-242">inbound</span></span>   | <span data-ttu-id="13c2a-243">x 1,00</span><span class="sxs-lookup"><span data-stu-id="13c2a-243">x 1.00</span></span>  |
| <span data-ttu-id="13c2a-244">HAFTANINGÜNÜ</span><span class="sxs-lookup"><span data-stu-id="13c2a-244">Weekday</span></span>    | <span data-ttu-id="13c2a-245">akşam aceleniz</span><span class="sxs-lookup"><span data-stu-id="13c2a-245">evening rush</span></span> | <span data-ttu-id="13c2a-246">giden</span><span class="sxs-lookup"><span data-stu-id="13c2a-246">outbound</span></span>  | <span data-ttu-id="13c2a-247">x 2,00</span><span class="sxs-lookup"><span data-stu-id="13c2a-247">x 2.00</span></span>  |
| <span data-ttu-id="13c2a-248">HAFTANINGÜNÜ</span><span class="sxs-lookup"><span data-stu-id="13c2a-248">Weekday</span></span>    | <span data-ttu-id="13c2a-249">gece</span><span class="sxs-lookup"><span data-stu-id="13c2a-249">overnight</span></span>    | <span data-ttu-id="13c2a-250">gelen</span><span class="sxs-lookup"><span data-stu-id="13c2a-250">inbound</span></span>   | <span data-ttu-id="13c2a-251">x 0,75</span><span class="sxs-lookup"><span data-stu-id="13c2a-251">x 0.75</span></span>  |
| <span data-ttu-id="13c2a-252">HAFTANINGÜNÜ</span><span class="sxs-lookup"><span data-stu-id="13c2a-252">Weekday</span></span>    | <span data-ttu-id="13c2a-253">gece</span><span class="sxs-lookup"><span data-stu-id="13c2a-253">overnight</span></span>    | <span data-ttu-id="13c2a-254">giden</span><span class="sxs-lookup"><span data-stu-id="13c2a-254">outbound</span></span>  | <span data-ttu-id="13c2a-255">x 0,75</span><span class="sxs-lookup"><span data-stu-id="13c2a-255">x 0.75</span></span>  |
| <span data-ttu-id="13c2a-256">Hafta</span><span class="sxs-lookup"><span data-stu-id="13c2a-256">Weekend</span></span>    | <span data-ttu-id="13c2a-257">sabah aceleniz</span><span class="sxs-lookup"><span data-stu-id="13c2a-257">morning rush</span></span> | <span data-ttu-id="13c2a-258">gelen</span><span class="sxs-lookup"><span data-stu-id="13c2a-258">inbound</span></span>   | <span data-ttu-id="13c2a-259">x 1,00</span><span class="sxs-lookup"><span data-stu-id="13c2a-259">x 1.00</span></span>  |
| <span data-ttu-id="13c2a-260">Hafta</span><span class="sxs-lookup"><span data-stu-id="13c2a-260">Weekend</span></span>    | <span data-ttu-id="13c2a-261">sabah aceleniz</span><span class="sxs-lookup"><span data-stu-id="13c2a-261">morning rush</span></span> | <span data-ttu-id="13c2a-262">giden</span><span class="sxs-lookup"><span data-stu-id="13c2a-262">outbound</span></span>  | <span data-ttu-id="13c2a-263">x 1,00</span><span class="sxs-lookup"><span data-stu-id="13c2a-263">x 1.00</span></span>  |
| <span data-ttu-id="13c2a-264">Hafta</span><span class="sxs-lookup"><span data-stu-id="13c2a-264">Weekend</span></span>    | <span data-ttu-id="13c2a-265">saati</span><span class="sxs-lookup"><span data-stu-id="13c2a-265">daytime</span></span>      | <span data-ttu-id="13c2a-266">gelen</span><span class="sxs-lookup"><span data-stu-id="13c2a-266">inbound</span></span>   | <span data-ttu-id="13c2a-267">x 1,00</span><span class="sxs-lookup"><span data-stu-id="13c2a-267">x 1.00</span></span>  |
| <span data-ttu-id="13c2a-268">Hafta</span><span class="sxs-lookup"><span data-stu-id="13c2a-268">Weekend</span></span>    | <span data-ttu-id="13c2a-269">saati</span><span class="sxs-lookup"><span data-stu-id="13c2a-269">daytime</span></span>      | <span data-ttu-id="13c2a-270">giden</span><span class="sxs-lookup"><span data-stu-id="13c2a-270">outbound</span></span>  | <span data-ttu-id="13c2a-271">x 1,00</span><span class="sxs-lookup"><span data-stu-id="13c2a-271">x 1.00</span></span>  |
| <span data-ttu-id="13c2a-272">Hafta</span><span class="sxs-lookup"><span data-stu-id="13c2a-272">Weekend</span></span>    | <span data-ttu-id="13c2a-273">akşam aceleniz</span><span class="sxs-lookup"><span data-stu-id="13c2a-273">evening rush</span></span> | <span data-ttu-id="13c2a-274">gelen</span><span class="sxs-lookup"><span data-stu-id="13c2a-274">inbound</span></span>   | <span data-ttu-id="13c2a-275">x 1,00</span><span class="sxs-lookup"><span data-stu-id="13c2a-275">x 1.00</span></span>  |
| <span data-ttu-id="13c2a-276">Hafta</span><span class="sxs-lookup"><span data-stu-id="13c2a-276">Weekend</span></span>    | <span data-ttu-id="13c2a-277">akşam aceleniz</span><span class="sxs-lookup"><span data-stu-id="13c2a-277">evening rush</span></span> | <span data-ttu-id="13c2a-278">giden</span><span class="sxs-lookup"><span data-stu-id="13c2a-278">outbound</span></span>  | <span data-ttu-id="13c2a-279">x 1,00</span><span class="sxs-lookup"><span data-stu-id="13c2a-279">x 1.00</span></span>  |
| <span data-ttu-id="13c2a-280">Hafta</span><span class="sxs-lookup"><span data-stu-id="13c2a-280">Weekend</span></span>    | <span data-ttu-id="13c2a-281">gece</span><span class="sxs-lookup"><span data-stu-id="13c2a-281">overnight</span></span>    | <span data-ttu-id="13c2a-282">gelen</span><span class="sxs-lookup"><span data-stu-id="13c2a-282">inbound</span></span>   | <span data-ttu-id="13c2a-283">x 1,00</span><span class="sxs-lookup"><span data-stu-id="13c2a-283">x 1.00</span></span>  |
| <span data-ttu-id="13c2a-284">Hafta</span><span class="sxs-lookup"><span data-stu-id="13c2a-284">Weekend</span></span>    | <span data-ttu-id="13c2a-285">gece</span><span class="sxs-lookup"><span data-stu-id="13c2a-285">overnight</span></span>    | <span data-ttu-id="13c2a-286">giden</span><span class="sxs-lookup"><span data-stu-id="13c2a-286">outbound</span></span>  | <span data-ttu-id="13c2a-287">x 1,00</span><span class="sxs-lookup"><span data-stu-id="13c2a-287">x 1.00</span></span>  |

<span data-ttu-id="13c2a-288">Üç değişkenin 16 farklı birleşimi vardır.</span><span class="sxs-lookup"><span data-stu-id="13c2a-288">There are 16 different combinations of the three variables.</span></span> <span data-ttu-id="13c2a-289">Bazı koşulları birleştirerek son anahtar ifadesini basitleştirirsiniz.</span><span class="sxs-lookup"><span data-stu-id="13c2a-289">By combining some of the conditions, you'll simplify the final switch expression.</span></span>

<span data-ttu-id="13c2a-290">Tolls 'yi toplayan sistem, ücretli bir süre için <xref:System.DateTime> yapısını kullanır.</span><span class="sxs-lookup"><span data-stu-id="13c2a-290">The system that collects the tolls uses a <xref:System.DateTime> structure for the time when the toll was collected.</span></span> <span data-ttu-id="13c2a-291">Yukarıdaki tablodan değişkenleri oluşturan üye yöntemleri oluşturun.</span><span class="sxs-lookup"><span data-stu-id="13c2a-291">Build member methods that create the variables from the preceding table.</span></span> <span data-ttu-id="13c2a-292">Aşağıdaki işlev bir <xref:System.DateTime> hafta sonu veya haftanın gününü temsil edip etmediğini ifade etmek için bir model eşleştirme anahtar ifadesi kullanır:</span><span class="sxs-lookup"><span data-stu-id="13c2a-292">The following function uses a pattern matching switch expression to express whether a <xref:System.DateTime> represents a weekend or a weekday:</span></span>

```csharp
private static bool IsWeekDay(DateTime timeOfToll) =>
    timeOfToll.DayOfWeek switch
    {
        DayOfWeek.Monday    => true,
        DayOfWeek.Tuesday   => true,
        DayOfWeek.Wednesday => true,
        DayOfWeek.Thursday  => true,
        DayOfWeek.Friday    => true,
        DayOfWeek.Saturday  => false,
        DayOfWeek.Sunday    => false
    };
```

<span data-ttu-id="13c2a-293">Bu yöntem işe yarar, ancak repetitious.</span><span class="sxs-lookup"><span data-stu-id="13c2a-293">That method works, but it's repetitious.</span></span> <span data-ttu-id="13c2a-294">Aşağıdaki kodda gösterildiği gibi basitleşebilir:</span><span class="sxs-lookup"><span data-stu-id="13c2a-294">You can simplify it, as shown in the following code:</span></span>

[!code-csharp[IsWeekDay](~/samples/snippets/csharp/tutorials/patterns/finished/toll-calculator/TollCalculator.cs#IsWeekDay)]

<span data-ttu-id="13c2a-295">Sonra, zaman bloklara zaman kategorize etmek için benzer bir işlev ekleyin:</span><span class="sxs-lookup"><span data-stu-id="13c2a-295">Next, add a similar function to categorize the time into the blocks:</span></span>

[!code-csharp[GetTimeBand](~/samples/snippets/csharp/tutorials/patterns/finished/toll-calculator/TollCalculator.cs#GetTimeBand)]

<span data-ttu-id="13c2a-296">Önceki yöntem, model eşleştirme kullanmaz.</span><span class="sxs-lookup"><span data-stu-id="13c2a-296">The previous method doesn't use pattern matching.</span></span> <span data-ttu-id="13c2a-297">`if` deyimleri tanıdık bir basamakla daha net.</span><span class="sxs-lookup"><span data-stu-id="13c2a-297">It's clearer using a familiar cascade of `if` statements.</span></span> <span data-ttu-id="13c2a-298">Her zaman aralığını ayrı bir değere dönüştürmek için özel bir `enum` eklersiniz.</span><span class="sxs-lookup"><span data-stu-id="13c2a-298">You do add a private `enum` to convert each range of time to a discrete value.</span></span>

<span data-ttu-id="13c2a-299">Bu yöntemleri oluşturduktan sonra, fiyatlandırma Premium 'u hesaplamak için **tanımlama grubu düzeniyle** başka bir `switch` ifadesini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="13c2a-299">After you create those methods, you can use another `switch` expression with the **tuple pattern** to calculate the pricing premium.</span></span> <span data-ttu-id="13c2a-300">Tüm 16 kollu bir `switch` ifadesi oluşturabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="13c2a-300">You could build a `switch` expression with all 16 arms:</span></span>

[!code-csharp[FullTuplePattern](~/samples/snippets/csharp/tutorials/patterns/finished/toll-calculator/TollCalculator.cs#TuplePatternOne)]

<span data-ttu-id="13c2a-301">Yukarıdaki kod işe yarar, ancak basitleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="13c2a-301">The above code works, but it can be simplified.</span></span> <span data-ttu-id="13c2a-302">Hafta sonu için sekiz kombinasyonun hepsi de aynı ücretli bir.</span><span class="sxs-lookup"><span data-stu-id="13c2a-302">All eight combinations for the weekend have the same toll.</span></span> <span data-ttu-id="13c2a-303">Tüm sekiz değerini aşağıdaki satırla değiştirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="13c2a-303">You can replace all eight with the following line:</span></span>

```csharp
(false, _, _) => 1.0m,
```

<span data-ttu-id="13c2a-304">Hem gelen hem de giden trafik, hafta içi gündüz ve gece saatlerinde aynı katkılar.</span><span class="sxs-lookup"><span data-stu-id="13c2a-304">Both inbound and outbound traffic have the same multiplier during the weekday daytime and overnight hours.</span></span> <span data-ttu-id="13c2a-305">Bu dört anahtar kolları aşağıdaki iki satır ile değiştirilebilir:</span><span class="sxs-lookup"><span data-stu-id="13c2a-305">Those four switch arms can be replaced with the following two lines:</span></span>

```csharp
(true, TimeBand.Overnight, _) => 0.75m,
(true, TimeBand.Daytime, _)   => 1.5m,
```

<span data-ttu-id="13c2a-306">Kod, bu iki değişiklikten sonra aşağıdaki kod gibi görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="13c2a-306">The code should look like the following code after those two changes:</span></span>

```csharp
public decimal PeakTimePremium(DateTime timeOfToll, bool inbound) =>
    (IsWeekDay(timeOfToll), GetTimeBand(timeOfToll), inbound) switch
    {
        (true, TimeBand.MorningRush, true)  => 2.00m,
        (true, TimeBand.MorningRush, false) => 1.00m,
        (true, TimeBand.Daytime,     _)     => 1.50m,
        (true, TimeBand.EveningRush, true)  => 1.00m,
        (true, TimeBand.EveningRush, false) => 2.00m,
        (true, TimeBand.Overnight,   _)     => 0.75m,
        (false, _,                   _)     => 1.00m,
    };
```

<span data-ttu-id="13c2a-307">Son olarak, normal fiyatı ödeyerek iki aceleniz saatlik saati kaldırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="13c2a-307">Finally, you can remove the two rush hour times that pay the regular price.</span></span> <span data-ttu-id="13c2a-308">Bu kolları kaldırdıktan sonra, `false` son anahtar ARM içindeki bir atma (`_`) ile değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="13c2a-308">Once you remove those arms, you can replace the `false` with a discard (`_`) in the final switch arm.</span></span> <span data-ttu-id="13c2a-309">Aşağıdaki tamamlanmış yönteme sahip olacaksınız:</span><span class="sxs-lookup"><span data-stu-id="13c2a-309">You'll have the following finished method:</span></span>

[!code-csharp[SimplifiedTuplePattern](../../../samples/snippets/csharp/tutorials/patterns/finished/toll-calculator/TollCalculator.cs#FinalTuplePattern)]

<span data-ttu-id="13c2a-310">Bu örnek, düzen eşleştirmesinin avantajlarından birini vurgular: düzen dalları sırayla değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="13c2a-310">This example highlights one of the advantages of pattern matching: the pattern branches are evaluated in order.</span></span> <span data-ttu-id="13c2a-311">Daha önceki bir dalın daha sonraki durumlardan birini işleyeceği şekilde yeniden ayarlarsanız, derleyici ulaşılamaz kod hakkında sizi uyarır.</span><span class="sxs-lookup"><span data-stu-id="13c2a-311">If you rearrange them so that an earlier branch handles one of your later cases, the compiler warns you about the unreachable code.</span></span> <span data-ttu-id="13c2a-312">Bu dil kuralları, önceki basitleştirmeleri kodun değiştirmiyordu güvenle daha kolay hale getirir.</span><span class="sxs-lookup"><span data-stu-id="13c2a-312">Those language rules made it easier to do the preceding simplifications with confidence that the code didn't change.</span></span>

<span data-ttu-id="13c2a-313">Model eşleştirme bazı kod türlerini daha okunaklı hale getirir ve sınıflarınıza kod ekleyemadığınızda nesne odaklı teknikler için bir alternatif sağlar.</span><span class="sxs-lookup"><span data-stu-id="13c2a-313">Pattern matching makes some types of code more readable and offers an alternative to object-oriented techniques when you can't add code to your classes.</span></span> <span data-ttu-id="13c2a-314">Bulut, verilerin ve işlevlerin canlı olmasına neden oluyor.</span><span class="sxs-lookup"><span data-stu-id="13c2a-314">The cloud is causing data and functionality to live apart.</span></span> <span data-ttu-id="13c2a-315">Verilerin *şekli* ve üzerindeki *işlemler* birlikte açıklanmamaktadır.</span><span class="sxs-lookup"><span data-stu-id="13c2a-315">The *shape* of the data and the *operations* on it aren't necessarily described together.</span></span> <span data-ttu-id="13c2a-316">Bu öğreticide, var olan verileri özgün işlevinden tamamen farklı şekillerde kullandınız.</span><span class="sxs-lookup"><span data-stu-id="13c2a-316">In this tutorial, you consumed existing data in entirely different ways from its original function.</span></span> <span data-ttu-id="13c2a-317">Model eşleştirme, bunları genişletmemiş olsanız bile, bu türlerin üzerine geçen işlevselliği yazma olanağını vermiştir.</span><span class="sxs-lookup"><span data-stu-id="13c2a-317">Pattern matching gave you the ability to write functionality that overrode those types, even though you couldn't extend them.</span></span>

## <a name="next-steps"></a><span data-ttu-id="13c2a-318">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="13c2a-318">Next steps</span></span>

<span data-ttu-id="13c2a-319">Tamamlanan kodu [DotNet/Samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/patterns/finished) GitHub deposundan indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="13c2a-319">You can download the finished code from the [dotnet/samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/patterns/finished) GitHub repository.</span></span> <span data-ttu-id="13c2a-320">Kendi hiyerarşinizdeki desenleri keşfedebilir ve bu tekniği düzenli kodlama etkinliklerinize ekleyin.</span><span class="sxs-lookup"><span data-stu-id="13c2a-320">Explore patterns on your own and add this technique into your regular coding activities.</span></span> <span data-ttu-id="13c2a-321">Bu teknikleri öğrenirken, sorun yaklaşımı ve yeni işlevler oluşturmak için kullanabileceğiniz başka bir yol sunulmaktadır.</span><span class="sxs-lookup"><span data-stu-id="13c2a-321">Learning these techniques gives you another way to approach problems and create new functionality.</span></span>
