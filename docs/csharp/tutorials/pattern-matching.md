---
title: Veri türlerini genişletmek için desen eşleştirme özelliklerini kullanma
description: Bu gelişmiş öğretici, ayrı olarak oluşturulan veri ve algoritmaları kullanarak işlevsellik oluşturmak için desen eşleştirme tekniklerinin nasıl kullanılacağını gösterir.
ms.date: 03/13/2019
ms-technology: csharp-whats-new
ms.custom: mvc
ms.openlocfilehash: df1054d8e0ec2b2539e6a1d00bf353d8ca927397
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79156538"
---
# <a name="tutorial-using-pattern-matching-features-to-extend-data-types"></a><span data-ttu-id="50c12-103">Öğretici: Veri türlerini genişletmek için desen eşleştirme özelliklerini kullanma</span><span class="sxs-lookup"><span data-stu-id="50c12-103">Tutorial: Using pattern matching features to extend data types</span></span>

<span data-ttu-id="50c12-104">C# 7 temel desen eşleştirme özelliklerini tanıttı.</span><span class="sxs-lookup"><span data-stu-id="50c12-104">C# 7 introduced basic pattern matching features.</span></span> <span data-ttu-id="50c12-105">Bu özellikler C# 8'de yeni ifadeler ve desenlerle genişletilir.</span><span class="sxs-lookup"><span data-stu-id="50c12-105">Those features are extended in C# 8 with new expressions and patterns.</span></span> <span data-ttu-id="50c12-106">Diğer kitaplıklarda olabilecek türleri genişletmiş gibi görünen işlevler yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="50c12-106">You can write functionality that behaves as though you extended types that may be in other libraries.</span></span> <span data-ttu-id="50c12-107">Desenler için başka bir kullanım, uygulamanızın genişletilmekte olan türün temel bir özelliği olmayan işlevselliği oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="50c12-107">Another use for patterns is to create functionality your application requires that isn't a fundamental feature of the type being extended.</span></span>

<span data-ttu-id="50c12-108">Bu öğreticide şunların nasıl yapıldığını öğreneceksiniz:</span><span class="sxs-lookup"><span data-stu-id="50c12-108">In this tutorial, you'll learn how to:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="50c12-109">Desen eşleştirmenin kullanılması gereken durumları tanıyın.</span><span class="sxs-lookup"><span data-stu-id="50c12-109">Recognize situations where pattern matching should be used.</span></span>
> - <span data-ttu-id="50c12-110">Türleri ve özellik değerlerini temel alan davranışı uygulamak için desen eşleştirme ifadelerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="50c12-110">Use pattern matching expressions to implement behavior based on types and property values.</span></span>
> - <span data-ttu-id="50c12-111">Tam algoritmalar oluşturmak için desen eşleştirmeyi diğer tekniklerle birleştirin.</span><span class="sxs-lookup"><span data-stu-id="50c12-111">Combine pattern matching with other techniques to create complete algorithms.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="50c12-112">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="50c12-112">Prerequisites</span></span>

<span data-ttu-id="50c12-113">C# 8.0 derleyicisi de dahil olmak üzere .NET Core'u çalıştıracak şekilde makinenizi ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="50c12-113">You’ll need to set up your machine to run .NET Core, including the C# 8.0 compiler.</span></span> <span data-ttu-id="50c12-114">C# 8 derleyicisi [Visual Studio 2019 sürüm 16.3](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) veya [.NET Core 3.0 SDK](https://dotnet.microsoft.com/download)ile başlayarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="50c12-114">The C# 8 compiler is available starting with [Visual Studio 2019 version 16.3](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) or [.NET Core 3.0 SDK](https://dotnet.microsoft.com/download).</span></span>

<span data-ttu-id="50c12-115">Bu öğretici, Visual Studio veya .NET Core CLI dahil olmak üzere C# ve .NET'e aşina olduğunuzu varsayar.</span><span class="sxs-lookup"><span data-stu-id="50c12-115">This tutorial assumes you're familiar with C# and .NET, including either Visual Studio or the .NET Core CLI.</span></span>

## <a name="scenarios-for-pattern-matching"></a><span data-ttu-id="50c12-116">Desen eşleştirme senaryoları</span><span class="sxs-lookup"><span data-stu-id="50c12-116">Scenarios for pattern matching</span></span>

<span data-ttu-id="50c12-117">Modern geliştirme genellikle birden çok kaynaktan gelen verileri tümleştirmeyi ve bu verilerden elde edilen bilgi ve öngörüleri tek bir tutarlı uygulamada sunmayı içerir.</span><span class="sxs-lookup"><span data-stu-id="50c12-117">Modern development often includes integrating data from multiple sources and presenting information and insights from that data in a single cohesive application.</span></span> <span data-ttu-id="50c12-118">Siz ve ekibiniz, gelen verileri temsil eden tüm türler için denetime veya erişime sahip olmazsınız.</span><span class="sxs-lookup"><span data-stu-id="50c12-118">You and your team won't have control or access for all the types that represent the incoming data.</span></span>

<span data-ttu-id="50c12-119">Klasik nesne yönelimli tasarım, uygulamanızda bu birden çok veri kaynağından her veri türünü temsil eden türler oluşturmayı çağırır.</span><span class="sxs-lookup"><span data-stu-id="50c12-119">The classic object-oriented design would call for creating types in your application that represent each data type from those multiple data sources.</span></span> <span data-ttu-id="50c12-120">Ardından, uygulamanız bu yeni türlerle çalışır, devralma hiyerarşileri oluşturur, sanal yöntemler oluşturur ve soyutlamalar uygular.</span><span class="sxs-lookup"><span data-stu-id="50c12-120">Then, your application would work with those new types, build inheritance hierarchies, create virtual methods, and implement abstractions.</span></span> <span data-ttu-id="50c12-121">Bu teknikler çalışır ve bazen en iyi araçlardır.</span><span class="sxs-lookup"><span data-stu-id="50c12-121">Those techniques work, and sometimes they are the best tools.</span></span> <span data-ttu-id="50c12-122">Diğer zamanlarda daha az kod yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="50c12-122">Other times you can write less code.</span></span> <span data-ttu-id="50c12-123">Verileri, bu verileri işleyen işlemlerden ayıran teknikleri kullanarak daha net kod yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="50c12-123">You can write more clear code using techniques that separate the data from the operations that manipulate that data.</span></span>

<span data-ttu-id="50c12-124">Bu öğreticide, tek bir senaryo için çeşitli dış kaynaklardan gelen verileri alan bir uygulama oluşturur ve keşfe esünüz.</span><span class="sxs-lookup"><span data-stu-id="50c12-124">In this tutorial, you'll create and explore an application that takes incoming data from several external sources for a single scenario.</span></span> <span data-ttu-id="50c12-125">**Desen eşleştirmenin,** bu verileri özgün sistemin bir parçası olmayan şekillerde tüketmenin ve işlemenin etkili bir yolunu nasıl sağladığını görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="50c12-125">You'll see how **pattern matching** provides an efficient way to consume and process that data in ways that weren't part of the original system.</span></span>

<span data-ttu-id="50c12-126">Trafiği yönetmek için geçiş ücretleri ve en yüksek zaman fiyatlandırması kullanan büyük bir metropol alanı düşünün.</span><span class="sxs-lookup"><span data-stu-id="50c12-126">Consider a major metropolitan area that is using tolls and peak time pricing to manage traffic.</span></span> <span data-ttu-id="50c12-127">Bir aracın geçiş ücretlerini türüne göre hesaplayan bir uygulama yazarsınız.</span><span class="sxs-lookup"><span data-stu-id="50c12-127">You write an application that calculates tolls for a vehicle based on its type.</span></span> <span data-ttu-id="50c12-128">Daha sonraki geliştirmeler, araçtaki yolcu sayısına bağlı olarak fiyatlandırmayı içerir.</span><span class="sxs-lookup"><span data-stu-id="50c12-128">Later enhancements incorporate pricing based on the number of occupants in the vehicle.</span></span> <span data-ttu-id="50c12-129">Diğer geliştirmeler, haftanın saatine ve gününe bağlı olarak fiyatlandırma ekler.</span><span class="sxs-lookup"><span data-stu-id="50c12-129">Further enhancements add pricing based on the time and the day of the week.</span></span>

<span data-ttu-id="50c12-130">Bu kısa açıklamadan, bu sistemi modellemek için hızlı bir şekilde bir nesne hiyerarşisi çizmiş olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="50c12-130">From that brief description, you may have quickly sketched out an object hierarchy to model this system.</span></span> <span data-ttu-id="50c12-131">Ancak, verileriniz diğer araç kayıt yönetim sistemleri gibi birden fazla kaynaktan geliyor.</span><span class="sxs-lookup"><span data-stu-id="50c12-131">However, your data is coming from multiple sources like other vehicle registration management systems.</span></span> <span data-ttu-id="50c12-132">Bu sistemler, bu verileri modellemek için farklı sınıflar sağlar ve kullanabileceğiniz tek bir nesne modeli yoktur.</span><span class="sxs-lookup"><span data-stu-id="50c12-132">These systems provide different classes to model that data and you don't have a single object model you can use.</span></span> <span data-ttu-id="50c12-133">Bu öğreticide, aşağıdaki kodda gösterildiği gibi, bu dış sistemlerden araç verilerini modellemek için bu basitleştirilmiş sınıfları kullanırsınız:</span><span class="sxs-lookup"><span data-stu-id="50c12-133">In this tutorial, you'll use these simplified classes to model for the vehicle data from these external systems, as shown in the following code:</span></span>

[!code-csharp[ExternalSystems](~/samples/snippets/csharp/tutorials/patterns/start/toll-calculator/ExternalSystems.cs)]

<span data-ttu-id="50c12-134">Başlangıç kodunu [dotnet/samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/patterns/start) GitHub deposundan indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="50c12-134">You can download the starter code from the [dotnet/samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/patterns/start) GitHub repository.</span></span> <span data-ttu-id="50c12-135">Araç sınıflarının farklı sistemlerden ve farklı ad alanlarında olduğunu görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="50c12-135">You can see that the vehicle classes are from different systems, and are in different namespaces.</span></span> <span data-ttu-id="50c12-136">Kaldıraçtan başka `System.Object` ortak bir taban sınıfı yoktur.</span><span class="sxs-lookup"><span data-stu-id="50c12-136">No common base class, other than `System.Object` can be leveraged.</span></span>

## <a name="pattern-matching-designs"></a><span data-ttu-id="50c12-137">Desen eşleştirme tasarımları</span><span class="sxs-lookup"><span data-stu-id="50c12-137">Pattern matching designs</span></span>

<span data-ttu-id="50c12-138">Bu öğreticide kullanılan senaryo, desen eşleştirmesinin çözmek için uygun olduğu sorun türlerini vurgular:</span><span class="sxs-lookup"><span data-stu-id="50c12-138">The scenario used in this tutorial highlights the kinds of problems that pattern matching is well-suited to solve:</span></span>

- <span data-ttu-id="50c12-139">Birlikte çalışmanız gereken nesneler, hedeflerinizle eşleşen bir nesne hiyerarşisinde değildir.</span><span class="sxs-lookup"><span data-stu-id="50c12-139">The objects you need to work with aren't in an object hierarchy that matches your goals.</span></span> <span data-ttu-id="50c12-140">İlişkisiz sistemlerin bir parçası olan sınıflarla çalışıyor olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="50c12-140">You may be working with classes that are part of unrelated systems.</span></span>
- <span data-ttu-id="50c12-141">Eklediğiniz işlevsellik, bu sınıflar için temel soyutlamanın bir parçası değildir.</span><span class="sxs-lookup"><span data-stu-id="50c12-141">The functionality you're adding isn't part of the core abstraction for these classes.</span></span> <span data-ttu-id="50c12-142">Bir araç tarafından ödenen geçiş ücreti farklı araç türleri için *değişir,* ancak geçiş ücreti aracın temel işlevi değildir.</span><span class="sxs-lookup"><span data-stu-id="50c12-142">The toll paid by a vehicle *changes* for different types of vehicles, but the toll isn't a core function of the vehicle.</span></span>

<span data-ttu-id="50c12-143">Verilerin *şekli* ve bu verilerdeki *işlemler* birlikte açıklanmadığında, C#'daki desen eşleştirme özellikleri çalışmayı kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="50c12-143">When the *shape* of the data and the *operations* on that data are not described together, the pattern matching features in C# make it easier to work with.</span></span>

## <a name="implement-the-basic-toll-calculations"></a><span data-ttu-id="50c12-144">Temel geçiş ücreti hesaplamalarını uygulayın</span><span class="sxs-lookup"><span data-stu-id="50c12-144">Implement the basic toll calculations</span></span>

<span data-ttu-id="50c12-145">En temel geçiş ücreti hesaplaması yalnızca araç tipine bağlıdır:</span><span class="sxs-lookup"><span data-stu-id="50c12-145">The most basic toll calculation relies only on the vehicle type:</span></span>

- <span data-ttu-id="50c12-146">A `Car` 2.00 dolar.</span><span class="sxs-lookup"><span data-stu-id="50c12-146">A `Car` is $2.00.</span></span>
- <span data-ttu-id="50c12-147">A `Taxi` 3.50 dolar.</span><span class="sxs-lookup"><span data-stu-id="50c12-147">A `Taxi` is $3.50.</span></span>
- <span data-ttu-id="50c12-148">A `Bus` 5.00 dolar.</span><span class="sxs-lookup"><span data-stu-id="50c12-148">A `Bus` is $5.00.</span></span>
- <span data-ttu-id="50c12-149">A `DeliveryTruck` 10,00 $ olduğunu</span><span class="sxs-lookup"><span data-stu-id="50c12-149">A `DeliveryTruck` is $10.00</span></span>

<span data-ttu-id="50c12-150">Yeni `TollCalculator` bir sınıf oluşturun ve geçiş ücreti miktarını almak için araç türüne uygun desen uygulayın.</span><span class="sxs-lookup"><span data-stu-id="50c12-150">Create a new `TollCalculator` class, and implement pattern matching on the vehicle type to get the toll amount.</span></span> <span data-ttu-id="50c12-151">Aşağıdaki `TollCalculator`kod, ilk uygulama gösterir.</span><span class="sxs-lookup"><span data-stu-id="50c12-151">The following code shows the initial implementation of the `TollCalculator`.</span></span>

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

<span data-ttu-id="50c12-152">Önceki kod, **tür deseni**test eden [`switch`](../language-reference/keywords/switch.md) bir anahtar **ifadesi** (deyimle aynı değil) kullanır.</span><span class="sxs-lookup"><span data-stu-id="50c12-152">The preceding code uses a **switch expression** (not the same as a [`switch`](../language-reference/keywords/switch.md) statement) that tests the **type pattern**.</span></span> <span data-ttu-id="50c12-153">Bir **anahtar ifadesi,** önceki `vehicle` kodda, `switch` anahtar kelime tarafından izlenen değişkenile başlar.</span><span class="sxs-lookup"><span data-stu-id="50c12-153">A **switch expression** begins with the variable, `vehicle` in the preceding code, followed by the `switch` keyword.</span></span> <span data-ttu-id="50c12-154">Sonra kıvırcık parantez içinde tüm **geçiş kolları** geliyor.</span><span class="sxs-lookup"><span data-stu-id="50c12-154">Next comes all the **switch arms** inside curly braces.</span></span> <span data-ttu-id="50c12-155">İfade, `switch` `switch` deyimi çevreleyen sözdiziminde başka iyileştirmeler yapar.</span><span class="sxs-lookup"><span data-stu-id="50c12-155">The `switch` expression makes other refinements to the syntax that surrounds the `switch` statement.</span></span> <span data-ttu-id="50c12-156">Anahtar `case` kelime atlanır ve her kolun sonucu bir ifadedir.</span><span class="sxs-lookup"><span data-stu-id="50c12-156">The `case` keyword is omitted, and the result of each arm is an expression.</span></span> <span data-ttu-id="50c12-157">Son iki kol yeni bir dil özelliği gösteriyor.</span><span class="sxs-lookup"><span data-stu-id="50c12-157">The last two arms show a new language feature.</span></span> <span data-ttu-id="50c12-158">Kasa, `{ }` önceki bir kolla eşleşmeyen null olmayan nesnelerle eşleşiyor.</span><span class="sxs-lookup"><span data-stu-id="50c12-158">The `{ }` case matches any non-null object that didn't match an earlier arm.</span></span> <span data-ttu-id="50c12-159">Bu kol, bu yönteme geçirilen herhangi bir yanlış türleri yakalar.</span><span class="sxs-lookup"><span data-stu-id="50c12-159">This arm catches any incorrect types passed to this method.</span></span>  <span data-ttu-id="50c12-160">Dava, `{ }` her araç tipi için vakaları takip etmelidir.</span><span class="sxs-lookup"><span data-stu-id="50c12-160">The `{ }` case must follow the cases for each vehicle type.</span></span> <span data-ttu-id="50c12-161">Sipariş tersine çevrilseydi, `{ }` servis talebi öncelikli olurdu.</span><span class="sxs-lookup"><span data-stu-id="50c12-161">If the order were reversed, the `{ }` case would take precedence.</span></span> <span data-ttu-id="50c12-162">Son olarak, `null` desen bu `null` yönteme bir geçirildiğinde algılar.</span><span class="sxs-lookup"><span data-stu-id="50c12-162">Finally, the `null` pattern detects when a `null` is passed to this method.</span></span> <span data-ttu-id="50c12-163">Diğer `null` tür desenleri yalnızca doğru türün null olmayan bir nesnesi ile eşleştirdiği için desen son olabilir.</span><span class="sxs-lookup"><span data-stu-id="50c12-163">The `null` pattern can be last because the other type patterns match only a non-null object of the correct type.</span></span>

<span data-ttu-id="50c12-164">Bu kodu aşağıdaki kodu kullanarak `Program.cs`test edebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="50c12-164">You can test this code using the following code in `Program.cs`:</span></span>

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

<span data-ttu-id="50c12-165">Bu kod başlangıç projesine dahil edilir, ancak yorumlanır. Yorumları kaldırın ve yazdıklarınızı test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="50c12-165">That code is included in the starter project, but is commented out. Remove the comments, and you can test what you've written.</span></span>

<span data-ttu-id="50c12-166">Desenlerin, kod ve verilerin ayrı olduğu algoritmalar oluşturmanıza nasıl yardımcı olabileceğini görmeye başlıyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="50c12-166">You're starting to see how patterns can help you create algorithms where the code and the data are separate.</span></span> <span data-ttu-id="50c12-167">İfade `switch` türünü sınar ve sonuçlara göre farklı değerler üretir.</span><span class="sxs-lookup"><span data-stu-id="50c12-167">The `switch` expression tests the type and produces different values based on the results.</span></span> <span data-ttu-id="50c12-168">Bu sadece başlangıç.</span><span class="sxs-lookup"><span data-stu-id="50c12-168">That's only the beginning.</span></span>

## <a name="add-occupancy-pricing"></a><span data-ttu-id="50c12-169">Doluluk fiyatlandırması ekleme</span><span class="sxs-lookup"><span data-stu-id="50c12-169">Add occupancy pricing</span></span>

<span data-ttu-id="50c12-170">Ücretli makamlar araçları maksimum kapasitede seyahat etmeye teşvik etmek istiyor.</span><span class="sxs-lookup"><span data-stu-id="50c12-170">The toll authority wants to encourage vehicles to travel at maximum capacity.</span></span> <span data-ttu-id="50c12-171">Araçlar daha az yolcu olduğunda daha fazla ücret almaya ve daha düşük fiyatlandırma sunarak tam araçları teşvik etmeye karar verdiler:</span><span class="sxs-lookup"><span data-stu-id="50c12-171">They've decided to charge more when vehicles have fewer passengers, and encourage full vehicles by offering lower pricing:</span></span>

- <span data-ttu-id="50c12-172">Yolcusuz arabalar ve taksiler fazladan 0.50 dolar ödüyor.</span><span class="sxs-lookup"><span data-stu-id="50c12-172">Cars and taxis with no passengers pay an extra $0.50.</span></span>
- <span data-ttu-id="50c12-173">İki yolculu araba ve taksiler 0,50 $ indirim olsun.</span><span class="sxs-lookup"><span data-stu-id="50c12-173">Cars and taxis with two passengers get a $0.50 discount.</span></span>
- <span data-ttu-id="50c12-174">Üç veya daha fazla yolcu ile otomobil ve taksiler 1,00 $ indirim olsun.</span><span class="sxs-lookup"><span data-stu-id="50c12-174">Cars and taxis with three or more passengers get a $1.00 discount.</span></span>
- <span data-ttu-id="50c12-175">Otobüsler az% 50 tam ekstra 2,00 $ ödemek.</span><span class="sxs-lookup"><span data-stu-id="50c12-175">Buses that are less than 50% full pay an extra $2.00.</span></span>
- <span data-ttu-id="50c12-176">%90'dan fazla tam otobüs 1,00 $ indirim alırsınız.</span><span class="sxs-lookup"><span data-stu-id="50c12-176">Buses that are more than 90% full get a $1.00 discount.</span></span>

<span data-ttu-id="50c12-177">Bu kurallar, aynı anahtar ifadesinde **özellik deseni** kullanılarak uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="50c12-177">These rules can be implemented using the **property pattern** in the same switch expression.</span></span> <span data-ttu-id="50c12-178">Özellik deseni, tür belirlendikten sonra nesnenin özelliklerini inceler.</span><span class="sxs-lookup"><span data-stu-id="50c12-178">The property pattern examines properties of the object once the type has been determined.</span></span> <span data-ttu-id="50c12-179">Bir `Car` durum için tek bir durum dört farklı durumda genişletir:</span><span class="sxs-lookup"><span data-stu-id="50c12-179">The single case for a `Car` expands to four different cases:</span></span>

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

<span data-ttu-id="50c12-180">İlk üç durumda bir `Car`olarak türünü test , `Passengers` sonra özelliğin değerini kontrol edin.</span><span class="sxs-lookup"><span data-stu-id="50c12-180">The first three cases test the type as a `Car`, then check the value of the `Passengers` property.</span></span> <span data-ttu-id="50c12-181">Her ikisi de eşleşirse, bu ifade değerlendirilir ve döndürülür.</span><span class="sxs-lookup"><span data-stu-id="50c12-181">If both match, that expression is evaluated and returned.</span></span>

<span data-ttu-id="50c12-182">Ayrıca benzer bir şekilde taksiler için durumlarda genişletmek istiyorsunuz:</span><span class="sxs-lookup"><span data-stu-id="50c12-182">You would also expand the cases for taxis in a similar manner:</span></span>

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

<span data-ttu-id="50c12-183">Önceki örnekte, `when` son durumda madde atlandı.</span><span class="sxs-lookup"><span data-stu-id="50c12-183">In the preceding example, the `when` clause was omitted on the final case.</span></span>

<span data-ttu-id="50c12-184">Ardından, aşağıdaki örnekte gösterildiği gibi, otobüsler için servis taleplerini genişleterek doluluk kurallarını uygulayın:</span><span class="sxs-lookup"><span data-stu-id="50c12-184">Next, implement the occupancy rules by expanding the cases for buses, as shown in the following example:</span></span>

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

<span data-ttu-id="50c12-185">Gişe yetkilisi teslimat kamyonlarında yolcu sayısı ile ilgili değildir.</span><span class="sxs-lookup"><span data-stu-id="50c12-185">The toll authority isn't concerned with the number of passengers in the delivery trucks.</span></span> <span data-ttu-id="50c12-186">Bunun yerine, kamyonların ağırlık sınıfına göre geçiş ücreti tutarını aşağıdaki gibi ayarlarlar:</span><span class="sxs-lookup"><span data-stu-id="50c12-186">Instead, they adjust the toll amount based on the weight class of the trucks as follows:</span></span>

- <span data-ttu-id="50c12-187">5000 lbs üzerinde kamyonlar ekstra 5,00 $ tahsil edilir.</span><span class="sxs-lookup"><span data-stu-id="50c12-187">Trucks over 5000 lbs are charged an extra $5.00.</span></span>
- <span data-ttu-id="50c12-188">3000 £ altında hafif kamyonlar 2,00 $ indirim verilir.</span><span class="sxs-lookup"><span data-stu-id="50c12-188">Light trucks under 3000 lbs are given a $2.00 discount.</span></span>

<span data-ttu-id="50c12-189">Bu kural aşağıdaki kodla uygulanır:</span><span class="sxs-lookup"><span data-stu-id="50c12-189">That rule is implemented with the following code:</span></span>

```csharp
vehicle switch
{
    // ...

    DeliveryTruck t when (t.GrossWeightClass > 5000) => 10.00m + 5.00m,
    DeliveryTruck t when (t.GrossWeightClass < 3000) => 10.00m - 2.00m,
    DeliveryTruck t => 10.00m,
};
```

<span data-ttu-id="50c12-190">Önceki kod, bir `when` anahtar kolunun yan tümcesini gösterir.</span><span class="sxs-lookup"><span data-stu-id="50c12-190">The preceding code shows the `when` clause of a switch arm.</span></span> <span data-ttu-id="50c12-191">Bu yan `when` tümceyi, bir mülkte eşitlik dışındaki koşulları test etmek için kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="50c12-191">You use the `when` clause to test conditions other than equality on a property.</span></span> <span data-ttu-id="50c12-192">Bitirdikten sonra, aşağıdakigibi görünen bir yönteme sahip olacaksınız:</span><span class="sxs-lookup"><span data-stu-id="50c12-192">When you've finished, you'll have a method that looks much like the following:</span></span>

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

<span data-ttu-id="50c12-193">Bu anahtar kollarıçoğu **özyinelemeli desenler**e-örnektir.</span><span class="sxs-lookup"><span data-stu-id="50c12-193">Many of these switch arms are examples of **recursive patterns**.</span></span> <span data-ttu-id="50c12-194">Örneğin, `Car { Passengers: 1}` bir özellik deseni içinde sabit bir desen gösterir.</span><span class="sxs-lookup"><span data-stu-id="50c12-194">For example, `Car { Passengers: 1}` shows a constant pattern inside a property pattern.</span></span>

<span data-ttu-id="50c12-195">İç içe geçen anahtarları kullanarak bu kodu daha az yineleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="50c12-195">You can make this code less repetitive by using nested switches.</span></span> <span data-ttu-id="50c12-196">Ve `Car` `Taxi` her ikisi de önceki örneklerde dört farklı kola sahiptir.</span><span class="sxs-lookup"><span data-stu-id="50c12-196">The `Car` and `Taxi` both have four different arms in the preceding examples.</span></span> <span data-ttu-id="50c12-197">Her iki durumda da, bir özellik deseni içine beslenen bir tür deseni oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="50c12-197">In both cases, you can create a type pattern that feeds into a property pattern.</span></span> <span data-ttu-id="50c12-198">Bu teknik aşağıdaki kodda gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="50c12-198">This technique is shown in the following code:</span></span>

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

<span data-ttu-id="50c12-199">Önceki örnekte, özyinelemeli bir ifade kullanmak, özellik değerini `Car` test `Taxi` eden alt kollar içeren kolları tekrarlamadığınız anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="50c12-199">In the preceding sample, using a recursive expression means you don't repeat the `Car` and `Taxi` arms containing child arms that test the property value.</span></span> <span data-ttu-id="50c12-200">Bu teknik ve `Bus` `DeliveryTruck` kollar için kullanılmaz çünkü bu kollar ayrık değerler için değil, özellik için test aralıklarıdır.</span><span class="sxs-lookup"><span data-stu-id="50c12-200">This technique isn't used for the `Bus` and `DeliveryTruck` arms because those arms are testing ranges for the property, not discrete values.</span></span>

## <a name="add-peak-pricing"></a><span data-ttu-id="50c12-201">En yüksek fiyatlandırma ekleme</span><span class="sxs-lookup"><span data-stu-id="50c12-201">Add peak pricing</span></span>

<span data-ttu-id="50c12-202">Son özellik için, ücretli makam zamana duyarlı pik fiyatlandırma eklemek istiyor.</span><span class="sxs-lookup"><span data-stu-id="50c12-202">For the final feature, the toll authority wants to add time sensitive peak pricing.</span></span> <span data-ttu-id="50c12-203">Sabah ve akşam yoğun saatlerde geçiş ücretleri iki katına çıkar.</span><span class="sxs-lookup"><span data-stu-id="50c12-203">During the morning and evening rush hours, the tolls are doubled.</span></span> <span data-ttu-id="50c12-204">Bu kural sadece bir yönde trafiği etkiler: sabah şehre gelen ve akşam yoğun saatlerde giden.</span><span class="sxs-lookup"><span data-stu-id="50c12-204">That rule only affects traffic in one direction: inbound to the city in the morning, and outbound in the evening rush hour.</span></span> <span data-ttu-id="50c12-205">İş günü boyunca diğer zamanlarda, geçiş ücretleri% 50 oranında artar.</span><span class="sxs-lookup"><span data-stu-id="50c12-205">During other times during the workday, tolls increase by 50%.</span></span> <span data-ttu-id="50c12-206">Gece geç saatlerde ve sabahın erken saatlerinde geçiş ücretleri %25 oranında azalır.</span><span class="sxs-lookup"><span data-stu-id="50c12-206">Late night and early morning, tolls are reduced by 25%.</span></span> <span data-ttu-id="50c12-207">Hafta sonu, ne olursa olsun zaman, normal oran's.</span><span class="sxs-lookup"><span data-stu-id="50c12-207">During the weekend, it's the normal rate, regardless of the time.</span></span>

<span data-ttu-id="50c12-208">Bu özellik için desen eşleştirme kullanırsınız, ancak diğer tekniklerle tümleştirirsiniz.</span><span class="sxs-lookup"><span data-stu-id="50c12-208">You'll use pattern matching for this feature, but you'll integrate it with other techniques.</span></span> <span data-ttu-id="50c12-209">Tüm yön, haftanın günü ve zaman birleşimlerini hesaba katacak tek bir desen eşlemi ifadesi oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="50c12-209">You could build a single pattern match expression that would account for all the combinations of direction, day of the week, and time.</span></span> <span data-ttu-id="50c12-210">Sonuç karmaşık bir ifade olacaktır.</span><span class="sxs-lookup"><span data-stu-id="50c12-210">The result would be a complicated expression.</span></span> <span data-ttu-id="50c12-211">Okuması ve anlaşılması zor olurdu.</span><span class="sxs-lookup"><span data-stu-id="50c12-211">It would be hard to read and difficult to understand.</span></span> <span data-ttu-id="50c12-212">Bu da doğruluğu sağlamayı zorlaştırıyor.</span><span class="sxs-lookup"><span data-stu-id="50c12-212">That makes it hard to ensure correctness.</span></span> <span data-ttu-id="50c12-213">Bunun yerine, tüm bu durumları kısa bir şekilde açıklayan bir değer tuple'ı oluşturmak için bu yöntemleri birleştirin.</span><span class="sxs-lookup"><span data-stu-id="50c12-213">Instead, combine those methods to build a tuple of values that concisely describes all those states.</span></span> <span data-ttu-id="50c12-214">Ardından, geçiş ücreti için çarpanı hesaplamak için desen eşleştirmesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="50c12-214">Then use pattern matching to calculate a multiplier for the toll.</span></span> <span data-ttu-id="50c12-215">Tuple üç ayrı koşul içerir:</span><span class="sxs-lookup"><span data-stu-id="50c12-215">The tuple contains three discrete conditions:</span></span>

- <span data-ttu-id="50c12-216">Gün ya hafta içi ya da hafta sonu.</span><span class="sxs-lookup"><span data-stu-id="50c12-216">The day is either a weekday or a weekend.</span></span>
- <span data-ttu-id="50c12-217">Geçiş ücretinin tahsil edildiği zaman grubu.</span><span class="sxs-lookup"><span data-stu-id="50c12-217">The band of time when the toll is collected.</span></span>
- <span data-ttu-id="50c12-218">Yön şehre ya da şehir dışına doğru</span><span class="sxs-lookup"><span data-stu-id="50c12-218">The direction is into the city or out of the city</span></span>

<span data-ttu-id="50c12-219">Aşağıdaki tablo, giriş değerlerinin ve en yüksek fiyatlandırma çarpanının birleşimlerini gösterir:</span><span class="sxs-lookup"><span data-stu-id="50c12-219">The following table shows the combinations of input values and the peak pricing multiplier:</span></span>

| <span data-ttu-id="50c12-220">Gün</span><span class="sxs-lookup"><span data-stu-id="50c12-220">Day</span></span>        | <span data-ttu-id="50c12-221">Zaman</span><span class="sxs-lookup"><span data-stu-id="50c12-221">Time</span></span>         | <span data-ttu-id="50c12-222">Yön</span><span class="sxs-lookup"><span data-stu-id="50c12-222">Direction</span></span> | <span data-ttu-id="50c12-223">Premium</span><span class="sxs-lookup"><span data-stu-id="50c12-223">Premium</span></span> |
| ---------- | ------------ | --------- |--------:|
| <span data-ttu-id="50c12-224">Weekday</span><span class="sxs-lookup"><span data-stu-id="50c12-224">Weekday</span></span>    | <span data-ttu-id="50c12-225">sabah acele</span><span class="sxs-lookup"><span data-stu-id="50c12-225">morning rush</span></span> | <span data-ttu-id="50c12-226">gelen</span><span class="sxs-lookup"><span data-stu-id="50c12-226">inbound</span></span>   | <span data-ttu-id="50c12-227">x 2,00</span><span class="sxs-lookup"><span data-stu-id="50c12-227">x 2.00</span></span>  |
| <span data-ttu-id="50c12-228">Weekday</span><span class="sxs-lookup"><span data-stu-id="50c12-228">Weekday</span></span>    | <span data-ttu-id="50c12-229">sabah acele</span><span class="sxs-lookup"><span data-stu-id="50c12-229">morning rush</span></span> | <span data-ttu-id="50c12-230">Giden</span><span class="sxs-lookup"><span data-stu-id="50c12-230">outbound</span></span>  | <span data-ttu-id="50c12-231">x 1,00</span><span class="sxs-lookup"><span data-stu-id="50c12-231">x 1.00</span></span>  |
| <span data-ttu-id="50c12-232">Weekday</span><span class="sxs-lookup"><span data-stu-id="50c12-232">Weekday</span></span>    | <span data-ttu-id="50c12-233">Gündüz</span><span class="sxs-lookup"><span data-stu-id="50c12-233">daytime</span></span>      | <span data-ttu-id="50c12-234">gelen</span><span class="sxs-lookup"><span data-stu-id="50c12-234">inbound</span></span>   | <span data-ttu-id="50c12-235">x 1,50</span><span class="sxs-lookup"><span data-stu-id="50c12-235">x 1.50</span></span>  |
| <span data-ttu-id="50c12-236">Weekday</span><span class="sxs-lookup"><span data-stu-id="50c12-236">Weekday</span></span>    | <span data-ttu-id="50c12-237">Gündüz</span><span class="sxs-lookup"><span data-stu-id="50c12-237">daytime</span></span>      | <span data-ttu-id="50c12-238">Giden</span><span class="sxs-lookup"><span data-stu-id="50c12-238">outbound</span></span>  | <span data-ttu-id="50c12-239">x 1,50</span><span class="sxs-lookup"><span data-stu-id="50c12-239">x 1.50</span></span>  |
| <span data-ttu-id="50c12-240">Weekday</span><span class="sxs-lookup"><span data-stu-id="50c12-240">Weekday</span></span>    | <span data-ttu-id="50c12-241">akşam acele</span><span class="sxs-lookup"><span data-stu-id="50c12-241">evening rush</span></span> | <span data-ttu-id="50c12-242">gelen</span><span class="sxs-lookup"><span data-stu-id="50c12-242">inbound</span></span>   | <span data-ttu-id="50c12-243">x 1,00</span><span class="sxs-lookup"><span data-stu-id="50c12-243">x 1.00</span></span>  |
| <span data-ttu-id="50c12-244">Weekday</span><span class="sxs-lookup"><span data-stu-id="50c12-244">Weekday</span></span>    | <span data-ttu-id="50c12-245">akşam acele</span><span class="sxs-lookup"><span data-stu-id="50c12-245">evening rush</span></span> | <span data-ttu-id="50c12-246">Giden</span><span class="sxs-lookup"><span data-stu-id="50c12-246">outbound</span></span>  | <span data-ttu-id="50c12-247">x 2,00</span><span class="sxs-lookup"><span data-stu-id="50c12-247">x 2.00</span></span>  |
| <span data-ttu-id="50c12-248">Weekday</span><span class="sxs-lookup"><span data-stu-id="50c12-248">Weekday</span></span>    | <span data-ttu-id="50c12-249">Gece</span><span class="sxs-lookup"><span data-stu-id="50c12-249">overnight</span></span>    | <span data-ttu-id="50c12-250">gelen</span><span class="sxs-lookup"><span data-stu-id="50c12-250">inbound</span></span>   | <span data-ttu-id="50c12-251">x 0,75</span><span class="sxs-lookup"><span data-stu-id="50c12-251">x 0.75</span></span>  |
| <span data-ttu-id="50c12-252">Weekday</span><span class="sxs-lookup"><span data-stu-id="50c12-252">Weekday</span></span>    | <span data-ttu-id="50c12-253">Gece</span><span class="sxs-lookup"><span data-stu-id="50c12-253">overnight</span></span>    | <span data-ttu-id="50c12-254">Giden</span><span class="sxs-lookup"><span data-stu-id="50c12-254">outbound</span></span>  | <span data-ttu-id="50c12-255">x 0,75</span><span class="sxs-lookup"><span data-stu-id="50c12-255">x 0.75</span></span>  |
| <span data-ttu-id="50c12-256">Hafta Sonu</span><span class="sxs-lookup"><span data-stu-id="50c12-256">Weekend</span></span>    | <span data-ttu-id="50c12-257">sabah acele</span><span class="sxs-lookup"><span data-stu-id="50c12-257">morning rush</span></span> | <span data-ttu-id="50c12-258">gelen</span><span class="sxs-lookup"><span data-stu-id="50c12-258">inbound</span></span>   | <span data-ttu-id="50c12-259">x 1,00</span><span class="sxs-lookup"><span data-stu-id="50c12-259">x 1.00</span></span>  |
| <span data-ttu-id="50c12-260">Hafta Sonu</span><span class="sxs-lookup"><span data-stu-id="50c12-260">Weekend</span></span>    | <span data-ttu-id="50c12-261">sabah acele</span><span class="sxs-lookup"><span data-stu-id="50c12-261">morning rush</span></span> | <span data-ttu-id="50c12-262">Giden</span><span class="sxs-lookup"><span data-stu-id="50c12-262">outbound</span></span>  | <span data-ttu-id="50c12-263">x 1,00</span><span class="sxs-lookup"><span data-stu-id="50c12-263">x 1.00</span></span>  |
| <span data-ttu-id="50c12-264">Hafta Sonu</span><span class="sxs-lookup"><span data-stu-id="50c12-264">Weekend</span></span>    | <span data-ttu-id="50c12-265">Gündüz</span><span class="sxs-lookup"><span data-stu-id="50c12-265">daytime</span></span>      | <span data-ttu-id="50c12-266">gelen</span><span class="sxs-lookup"><span data-stu-id="50c12-266">inbound</span></span>   | <span data-ttu-id="50c12-267">x 1,00</span><span class="sxs-lookup"><span data-stu-id="50c12-267">x 1.00</span></span>  |
| <span data-ttu-id="50c12-268">Hafta Sonu</span><span class="sxs-lookup"><span data-stu-id="50c12-268">Weekend</span></span>    | <span data-ttu-id="50c12-269">Gündüz</span><span class="sxs-lookup"><span data-stu-id="50c12-269">daytime</span></span>      | <span data-ttu-id="50c12-270">Giden</span><span class="sxs-lookup"><span data-stu-id="50c12-270">outbound</span></span>  | <span data-ttu-id="50c12-271">x 1,00</span><span class="sxs-lookup"><span data-stu-id="50c12-271">x 1.00</span></span>  |
| <span data-ttu-id="50c12-272">Hafta Sonu</span><span class="sxs-lookup"><span data-stu-id="50c12-272">Weekend</span></span>    | <span data-ttu-id="50c12-273">akşam acele</span><span class="sxs-lookup"><span data-stu-id="50c12-273">evening rush</span></span> | <span data-ttu-id="50c12-274">gelen</span><span class="sxs-lookup"><span data-stu-id="50c12-274">inbound</span></span>   | <span data-ttu-id="50c12-275">x 1,00</span><span class="sxs-lookup"><span data-stu-id="50c12-275">x 1.00</span></span>  |
| <span data-ttu-id="50c12-276">Hafta Sonu</span><span class="sxs-lookup"><span data-stu-id="50c12-276">Weekend</span></span>    | <span data-ttu-id="50c12-277">akşam acele</span><span class="sxs-lookup"><span data-stu-id="50c12-277">evening rush</span></span> | <span data-ttu-id="50c12-278">Giden</span><span class="sxs-lookup"><span data-stu-id="50c12-278">outbound</span></span>  | <span data-ttu-id="50c12-279">x 1,00</span><span class="sxs-lookup"><span data-stu-id="50c12-279">x 1.00</span></span>  |
| <span data-ttu-id="50c12-280">Hafta Sonu</span><span class="sxs-lookup"><span data-stu-id="50c12-280">Weekend</span></span>    | <span data-ttu-id="50c12-281">Gece</span><span class="sxs-lookup"><span data-stu-id="50c12-281">overnight</span></span>    | <span data-ttu-id="50c12-282">gelen</span><span class="sxs-lookup"><span data-stu-id="50c12-282">inbound</span></span>   | <span data-ttu-id="50c12-283">x 1,00</span><span class="sxs-lookup"><span data-stu-id="50c12-283">x 1.00</span></span>  |
| <span data-ttu-id="50c12-284">Hafta Sonu</span><span class="sxs-lookup"><span data-stu-id="50c12-284">Weekend</span></span>    | <span data-ttu-id="50c12-285">Gece</span><span class="sxs-lookup"><span data-stu-id="50c12-285">overnight</span></span>    | <span data-ttu-id="50c12-286">Giden</span><span class="sxs-lookup"><span data-stu-id="50c12-286">outbound</span></span>  | <span data-ttu-id="50c12-287">x 1,00</span><span class="sxs-lookup"><span data-stu-id="50c12-287">x 1.00</span></span>  |

<span data-ttu-id="50c12-288">Üç değişkenin 16 farklı kombinasyonu vardır.</span><span class="sxs-lookup"><span data-stu-id="50c12-288">There are 16 different combinations of the three variables.</span></span> <span data-ttu-id="50c12-289">Bazı koşulları birleştirerek, son geçiş ifadesini basitleştirirsiniz.</span><span class="sxs-lookup"><span data-stu-id="50c12-289">By combining some of the conditions, you'll simplify the final switch expression.</span></span>

<span data-ttu-id="50c12-290">Geçiş ücretlerini toplayan sistem, <xref:System.DateTime> geçiş ücretinin toplandığı zaman için bir yapı kullanır.</span><span class="sxs-lookup"><span data-stu-id="50c12-290">The system that collects the tolls uses a <xref:System.DateTime> structure for the time when the toll was collected.</span></span> <span data-ttu-id="50c12-291">Önceki tablodaki değişkenleri oluşturan üye yöntemler oluşturun.</span><span class="sxs-lookup"><span data-stu-id="50c12-291">Build member methods that create the variables from the preceding table.</span></span> <span data-ttu-id="50c12-292">Aşağıdaki işlev, bir <xref:System.DateTime> hafta sonunu mu yoksa hafta içi mi temsil etmediğini ifade etmek için bir desen eşleştirme anahtarı ifadesi kullanır:</span><span class="sxs-lookup"><span data-stu-id="50c12-292">The following function uses a pattern matching switch expression to express whether a <xref:System.DateTime> represents a weekend or a weekday:</span></span>

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

<span data-ttu-id="50c12-293">Bu yöntem işe yarıyor, ama tekrarediyor.</span><span class="sxs-lookup"><span data-stu-id="50c12-293">That method works, but it's repetitious.</span></span> <span data-ttu-id="50c12-294">Aşağıdaki kodda gösterildiği gibi basitleştirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="50c12-294">You can simplify it, as shown in the following code:</span></span>

[!code-csharp[IsWeekDay](~/samples/snippets/csharp/tutorials/patterns/finished/toll-calculator/TollCalculator.cs#IsWeekDay)]

<span data-ttu-id="50c12-295">Ardından, zaman bloklar içine kategorize etmek için benzer bir işlev ekleyin:</span><span class="sxs-lookup"><span data-stu-id="50c12-295">Next, add a similar function to categorize the time into the blocks:</span></span>

[!code-csharp[GetTimeBand](~/samples/snippets/csharp/tutorials/patterns/finished/toll-calculator/TollCalculator.cs#GetTimeBand)]

<span data-ttu-id="50c12-296">Önceki yöntem desen eşleştirme kullanmaz.</span><span class="sxs-lookup"><span data-stu-id="50c12-296">The previous method doesn't use pattern matching.</span></span> <span data-ttu-id="50c12-297">Tanıdık bir `if` dizi ifade kullanarak daha açık.</span><span class="sxs-lookup"><span data-stu-id="50c12-297">It's clearer using a familiar cascade of `if` statements.</span></span> <span data-ttu-id="50c12-298">Her zaman aralığını ayrı bir `enum` değere dönüştürmek için özel bir ürün eklersiniz.</span><span class="sxs-lookup"><span data-stu-id="50c12-298">You do add a private `enum` to convert each range of time to a discrete value.</span></span>

<span data-ttu-id="50c12-299">Bu yöntemleri oluşturduktan sonra, `switch` fiyatlandırma primini hesaplamak için **tuple deseni** olan başka bir ifade kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="50c12-299">After you create those methods, you can use another `switch` expression with the **tuple pattern** to calculate the pricing premium.</span></span> <span data-ttu-id="50c12-300">16 kolu `switch` yla bir ifade oluşturabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="50c12-300">You could build a `switch` expression with all 16 arms:</span></span>

[!code-csharp[FullTuplePattern](~/samples/snippets/csharp/tutorials/patterns/finished/toll-calculator/TollCalculator.cs#TuplePatternOne)]

<span data-ttu-id="50c12-301">Yukarıdaki kod çalışır, ancak basitleştirilmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="50c12-301">The above code works, but it can be simplified.</span></span> <span data-ttu-id="50c12-302">Hafta sonu için tüm sekiz kombinasyonları aynı geçiş ücreti var.</span><span class="sxs-lookup"><span data-stu-id="50c12-302">All eight combinations for the weekend have the same toll.</span></span> <span data-ttu-id="50c12-303">Sekizini de aşağıdaki satırla değiştirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="50c12-303">You can replace all eight with the following line:</span></span>

```csharp
(false, _, _) => 1.0m,
```

<span data-ttu-id="50c12-304">Hem gelen hem de giden trafik hafta içi gündüz ve gece saatlerinde aynı çarpana sahiptir.</span><span class="sxs-lookup"><span data-stu-id="50c12-304">Both inbound and outbound traffic have the same multiplier during the weekday daytime and overnight hours.</span></span> <span data-ttu-id="50c12-305">Bu dört anahtar kolu aşağıdaki iki satırla değiştirilebilir:</span><span class="sxs-lookup"><span data-stu-id="50c12-305">Those four switch arms can be replaced with the following two lines:</span></span>

```csharp
(true, TimeBand.Overnight, _) => 0.75m,
(true, TimeBand.Daytime, _)   => 1.5m,
```

<span data-ttu-id="50c12-306">Kod, bu iki değişiklikten sonra aşağıdaki kod gibi görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="50c12-306">The code should look like the following code after those two changes:</span></span>

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

<span data-ttu-id="50c12-307">Son olarak, normal fiyatı ödeyen iki acele saat zaman kaldırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="50c12-307">Finally, you can remove the two rush hour times that pay the regular price.</span></span> <span data-ttu-id="50c12-308">Bu kolları çıkardıktan sonra, `false` son anahtar`_`kolundaki bir atma ( ) ile değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="50c12-308">Once you remove those arms, you can replace the `false` with a discard (`_`) in the final switch arm.</span></span> <span data-ttu-id="50c12-309">Aşağıdaki bitmiş yönteme sahip olacaksınız:</span><span class="sxs-lookup"><span data-stu-id="50c12-309">You'll have the following finished method:</span></span>

[!code-csharp[SimplifiedTuplePattern](../../../samples/snippets/csharp/tutorials/patterns/finished/toll-calculator/TollCalculator.cs#FinalTuplePattern)]

<span data-ttu-id="50c12-310">Bu örnek, desen eşleştirmenin avantajlarından birini vurgular: desen dalları sırayla değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="50c12-310">This example highlights one of the advantages of pattern matching: the pattern branches are evaluated in order.</span></span> <span data-ttu-id="50c12-311">Önceki bir şubenin sonraki durumlarından birini işlemesi için bunları yeniden düzenlerseniz, derleyici erişilemez kod hakkında sizi uyarır.</span><span class="sxs-lookup"><span data-stu-id="50c12-311">If you rearrange them so that an earlier branch handles one of your later cases, the compiler warns you about the unreachable code.</span></span> <span data-ttu-id="50c12-312">Bu dil kuralları, önceki basitleştirmeleri kodun değişmediği konusunda güvenle yapmayı kolaylaştırdı.</span><span class="sxs-lookup"><span data-stu-id="50c12-312">Those language rules made it easier to do the preceding simplifications with confidence that the code didn't change.</span></span>

<span data-ttu-id="50c12-313">Desen eşleştirme, bazı kod türlerini daha okunabilir hale getirir ve sınıflarınıza kod ekleyemediğınızda nesne yönelimli tekniklere alternatif sunar.</span><span class="sxs-lookup"><span data-stu-id="50c12-313">Pattern matching makes some types of code more readable and offers an alternative to object-oriented techniques when you can't add code to your classes.</span></span> <span data-ttu-id="50c12-314">Bulut, verilerin ve işlevselliğin birbirinden ayrılmasına neden oluyor.</span><span class="sxs-lookup"><span data-stu-id="50c12-314">The cloud is causing data and functionality to live apart.</span></span> <span data-ttu-id="50c12-315">Verilerin *şekli* ve üzerindeki *işlemler* birlikte açıklanmaz.</span><span class="sxs-lookup"><span data-stu-id="50c12-315">The *shape* of the data and the *operations* on it aren't necessarily described together.</span></span> <span data-ttu-id="50c12-316">Bu eğitimde, varolan verileri özgün işlevinden tamamen farklı şekillerde tükettin.</span><span class="sxs-lookup"><span data-stu-id="50c12-316">In this tutorial, you consumed existing data in entirely different ways from its original function.</span></span> <span data-ttu-id="50c12-317">Desen eşleştirme, bu türleri genişletemeseniz bile, bu türleri geçersiz kılması gereken işlevsellik yazma olanağı sağlar.</span><span class="sxs-lookup"><span data-stu-id="50c12-317">Pattern matching gave you the ability to write functionality that overrode those types, even though you couldn't extend them.</span></span>

## <a name="next-steps"></a><span data-ttu-id="50c12-318">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="50c12-318">Next steps</span></span>

<span data-ttu-id="50c12-319">Bitmiş kodu [dotnet/samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/patterns/finished) GitHub deposundan indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="50c12-319">You can download the finished code from the [dotnet/samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/patterns/finished) GitHub repository.</span></span> <span data-ttu-id="50c12-320">Desenleri kendi gözlerinize ekleyin ve bu tekniği düzenli kodlama etkinliklerinize ekleyin.</span><span class="sxs-lookup"><span data-stu-id="50c12-320">Explore patterns on your own and add this technique into your regular coding activities.</span></span> <span data-ttu-id="50c12-321">Bu teknikleri öğrenmek, sorunlara yaklaşmanız ve yeni işlevler oluşturmanız için başka bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="50c12-321">Learning these techniques gives you another way to approach problems and create new functionality.</span></span>
