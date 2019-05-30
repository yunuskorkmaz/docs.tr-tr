---
title: Veri türlerini genişletmek için desen eşleştirme özelliklerini kullanın
description: Gelişmiş Bu öğretici, verileri ve ayrı oluşturulur algoritmaları kullanarak işlevi oluşturmak için desen eşleştirme teknikleri kullanmayı gösterir.
ms.date: 03/13/2019
ms.custom: mvc
ms.openlocfilehash: 58e4a9175752c7845507f48a3684747092dc609a
ms.sourcegitcommit: 4735bb7741555bcb870d7b42964d3774f4897a6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/30/2019
ms.locfileid: "66378076"
---
# <a name="tutorial-using-pattern-matching-features-to-extend-data-types"></a><span data-ttu-id="3089a-103">Öğretici: Veri türlerini genişletmek için özellikler desen kullanma</span><span class="sxs-lookup"><span data-stu-id="3089a-103">Tutorial: Using pattern matching features to extend data types</span></span>

<span data-ttu-id="3089a-104">C#7 özellikleri temel desen kullanıma sunuldu.</span><span class="sxs-lookup"><span data-stu-id="3089a-104">C# 7 introduced basic pattern matching features.</span></span> <span data-ttu-id="3089a-105">Bu özellikler, Genişletilmiş C# yeni ifadeleri ve desenleriyle 8.</span><span class="sxs-lookup"><span data-stu-id="3089a-105">Those features are extended in C# 8 with new expressions and patterns.</span></span> <span data-ttu-id="3089a-106">Diğer kitaplıkları olabilecek türler genişletilmiş olarak gibi davranır işlevselliği yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3089a-106">You can write functionality that behaves as though you extended types that may be in other libraries.</span></span> <span data-ttu-id="3089a-107">Başka bir kullanım desenleri için temel bir özelliği Genişletilmekte olan türü değil, uygulamanızın gerektirdiği işlevselliği oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="3089a-107">Another use for patterns is to create functionality your application requires that isn't a fundamental feature of the type being extended.</span></span>

<span data-ttu-id="3089a-108">Bu öğreticide şunları öğrenirsiniz nasıl yapılır:</span><span class="sxs-lookup"><span data-stu-id="3089a-108">In this tutorial, you'll learn how to:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="3089a-109">Desen eşleştirme burada kullanılması gereken durumları algılar.</span><span class="sxs-lookup"><span data-stu-id="3089a-109">Recognize situations where pattern matching should be used.</span></span>
> * <span data-ttu-id="3089a-110">Desen eşleştirme ifadelerinde, türleri ve özellik değerlerine göre davranışı uygulamak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="3089a-110">Use pattern matching expressions to implement behavior based on types and property values.</span></span>
> * <span data-ttu-id="3089a-111">Desen eşleştirme tam algoritmalar oluşturmak için diğer teknikleri ile birleştirin.</span><span class="sxs-lookup"><span data-stu-id="3089a-111">Combine pattern matching with other techniques to create complete algorithms.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="3089a-112">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="3089a-112">Prerequisites</span></span>

<span data-ttu-id="3089a-113">.NET Core çalıştırmak için makinenizi ayarlamak ihtiyacınız olacak dahil olmak üzere C# 8.0 Önizleme derleyici.</span><span class="sxs-lookup"><span data-stu-id="3089a-113">You'll need to set up your machine to run .NET Core, including the C# 8.0 preview compiler.</span></span> <span data-ttu-id="3089a-114">C# 8 preview derleyici en son kullanılabilir [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019), veya en son [.NET Core 3.0 Önizleme](https://dotnet.microsoft.com/download/dotnet-core/3.0).</span><span class="sxs-lookup"><span data-stu-id="3089a-114">The C# 8 preview compiler is available with the latest [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019), or the latest [.NET Core 3.0 preview](https://dotnet.microsoft.com/download/dotnet-core/3.0).</span></span>

<span data-ttu-id="3089a-115">Bu öğreticide, aşina olduğunuz varsayılır C# ve .NET, Visual Studio veya .NET Core CLI gibi.</span><span class="sxs-lookup"><span data-stu-id="3089a-115">This tutorial assumes you're familiar with C# and .NET, including either Visual Studio or the .NET Core CLI.</span></span>

## <a name="scenarios-for-pattern-matching"></a><span data-ttu-id="3089a-116">Desen eşleştirme senaryoları</span><span class="sxs-lookup"><span data-stu-id="3089a-116">Scenarios for pattern matching</span></span>

<span data-ttu-id="3089a-117">Modern geliştirme genellikle birden çok kaynaktan veri tümleştirme ve bilgi ve bu verilerden Öngörüler elde cohesive tek bir uygulama içinde sunma içerir.</span><span class="sxs-lookup"><span data-stu-id="3089a-117">Modern development often includes integrating data from multiple sources and presenting information and insights from that data in a single cohesive application.</span></span> <span data-ttu-id="3089a-118">Size ve ekibinize denetim veya gelen verilerini temsil eden tüm türleri için erişimi olmaz.</span><span class="sxs-lookup"><span data-stu-id="3089a-118">You and your team won't have control or access for all the types that represent the incoming data.</span></span>

<span data-ttu-id="3089a-119">Uygulamanızdaki her veri türü bu birden çok veri kaynağından temsil eden türleri oluşturmak için Klasik nesne yönelimli tasarım çağırırsınız.</span><span class="sxs-lookup"><span data-stu-id="3089a-119">The classic object-oriented design would call for creating types in your application that represent each data type from those multiple data sources.</span></span> <span data-ttu-id="3089a-120">Ardından, uygulamanızı bu yeni türleriyle çalışır, devralma Hiyerarşiler, sanal yöntemler oluşturmak ve soyutlama uygulamak.</span><span class="sxs-lookup"><span data-stu-id="3089a-120">Then, your application would work with those new types, build inheritance hierarchies, create virtual methods, and implement abstractions.</span></span> <span data-ttu-id="3089a-121">En iyi Araçlar bazen olduklarını ve bu teknikler çalışır.</span><span class="sxs-lookup"><span data-stu-id="3089a-121">Those techniques work, and sometimes they are the best tools.</span></span> <span data-ttu-id="3089a-122">Bazen daha az kod yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3089a-122">Other times you can write less code.</span></span> <span data-ttu-id="3089a-123">Veriler, veri işleme işlemlerinden ayıran teknikleri kullanarak daha fazla kod yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3089a-123">You can write more clear code using techniques that separate the data from the operations that manipulate that data.</span></span>

<span data-ttu-id="3089a-124">Bu öğreticide, oluşturun ve tek bir senaryo için çeşitli dış kaynaklardan gelen verileri alan bir uygulama keşfedin.</span><span class="sxs-lookup"><span data-stu-id="3089a-124">In this tutorial, you'll create and explore an application that takes incoming data from several external sources for a single scenario.</span></span> <span data-ttu-id="3089a-125">Göreceğiniz nasıl **desen eşleştirme** kullanır ve bu verileri özgün sisteminin bir parçası olmayan bir şekilde işlemek için etkili bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="3089a-125">You'll see how **pattern matching** provides an efficient way to consume and process that data in ways that weren't part of the original system.</span></span>

<span data-ttu-id="3089a-126">Trafiği yönetmek için ücretli geçişler ve en yüksek süre fiyatlandırma kullanarak büyük bir metropol alanı göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="3089a-126">Consider a major metropolitan area that is using tolls and peak time pricing to manage traffic.</span></span> <span data-ttu-id="3089a-127">Ücretli geçişler için bir araç kendi türüne göre hesaplayan bir uygulaması yazma.</span><span class="sxs-lookup"><span data-stu-id="3089a-127">You write an application that calculates tolls for a vehicle based on its type.</span></span> <span data-ttu-id="3089a-128">Sonraki geliştirmeleri occupants araç içinde sayısına bağlı fiyatlandırma dahil edilip derecelendirilir.</span><span class="sxs-lookup"><span data-stu-id="3089a-128">Later enhancements incorporate pricing based on the number of occupants in the vehicle.</span></span> <span data-ttu-id="3089a-129">Başka bir geliştirme, saat ve haftanın günü göre fiyatlandırma ekleyin.</span><span class="sxs-lookup"><span data-stu-id="3089a-129">Further enhancements add pricing based on the time and the day of the week.</span></span>

<span data-ttu-id="3089a-130">Bu kısa açıklamasından, hızlı bir şekilde bu sistem modeli için bir nesne hiyerarşisine ince ince.</span><span class="sxs-lookup"><span data-stu-id="3089a-130">From that brief description, you may have quickly sketched out an object hierarchy to model this system.</span></span> <span data-ttu-id="3089a-131">Bununla birlikte, verilerinizi diğer araç kayıt yönetim sistemleri gibi birden çok kaynaktan geliyor.</span><span class="sxs-lookup"><span data-stu-id="3089a-131">However, your data is coming from multiple sources like other vehicle registration management systems.</span></span> <span data-ttu-id="3089a-132">Bu sistemler, veri modeli için farklı sınıfları sağlar ve bir tek nesne modeli kullandığınız yok.</span><span class="sxs-lookup"><span data-stu-id="3089a-132">These systems provide different classes to model that data and you don't have a single object model you can use.</span></span> <span data-ttu-id="3089a-133">Bu öğreticide, bu dış sistemlerden vehicle veri modeli için aşağıdaki kodda gösterildiği gibi bu Basitleştirilmiş sınıfların kullanacaksınız:</span><span class="sxs-lookup"><span data-stu-id="3089a-133">In this tutorial, you'll use these simplified classes to model for the vehicle data from these external systems, as shown in the following code:</span></span>

[!code-csharp[ExternalSystems](~/samples/csharp/tutorials/patterns/start/toll-calculator/ExternalSystems.cs)]

<span data-ttu-id="3089a-134">Başlatıcı kodu indirebileceğiniz [dotnet/samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/patterns/start) GitHub deposu.</span><span class="sxs-lookup"><span data-stu-id="3089a-134">You can download the starter code from the [dotnet/samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/patterns/start) GitHub repository.</span></span> <span data-ttu-id="3089a-135">Araç sınıfları farklı sistemlerden ve farklı ad alanlarında, görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3089a-135">You can see that the vehicle classes are from different systems, and are in different namespaces.</span></span> <span data-ttu-id="3089a-136">Dışındaki hiçbir ortak bir taban sınıf `System.Object` yararlanılabilir.</span><span class="sxs-lookup"><span data-stu-id="3089a-136">No common base class, other than `System.Object` can be leveraged.</span></span>

## <a name="pattern-matching-designs"></a><span data-ttu-id="3089a-137">Desen eşleştirme tasarımları</span><span class="sxs-lookup"><span data-stu-id="3089a-137">Pattern matching designs</span></span>

<span data-ttu-id="3089a-138">Bu öğretici vurguların kullanılan senaryo tür desen eşleştirme sorunları çözmek için uygundur:</span><span class="sxs-lookup"><span data-stu-id="3089a-138">The scenario used in this tutorial highlights the kinds of problems that pattern matching is well-suited to solve:</span></span>

- <span data-ttu-id="3089a-139">Çalışmanız için gereken nesneleri hedeflerinizi karşılayan bir nesne hiyerarşisine değildir.</span><span class="sxs-lookup"><span data-stu-id="3089a-139">The objects you need to work with aren't in an object hierarchy that matches your goals.</span></span> <span data-ttu-id="3089a-140">İlişkisiz sistemleri parçası olan sınıfları ile çalışıyor.</span><span class="sxs-lookup"><span data-stu-id="3089a-140">You may be working with classes that are part of unrelated systems.</span></span>
- <span data-ttu-id="3089a-141">Ekliyorsunuz işlevselliği, bu sınıflar için temel Özet bir parçası değildir.</span><span class="sxs-lookup"><span data-stu-id="3089a-141">The functionality you're adding isn't part of the core abstraction for these classes.</span></span> <span data-ttu-id="3089a-142">Ücretli bir araç tarafından ödenen *değişiklikleri* vehicle çekirdek işlevi araçları, ancak Ücretli farklı türde değil.</span><span class="sxs-lookup"><span data-stu-id="3089a-142">The toll paid by a vehicle *changes* for different types of vehicles, but the toll isn't a core function of the vehicle.</span></span>

<span data-ttu-id="3089a-143">Zaman *şekli* verilerin ve *işlemleri* üzerinde veri değil açıklanacak olan birlikte özelliklerinde desen C# çalışmak daha kolay hale getirmek.</span><span class="sxs-lookup"><span data-stu-id="3089a-143">When the *shape* of the data and the *operations* on that data are not described together, the pattern matching features in C# make it easier to work with.</span></span>

## <a name="implement-the-basic-toll-calculations"></a><span data-ttu-id="3089a-144">Temel Ücretli hesaplamalar uygulayın</span><span class="sxs-lookup"><span data-stu-id="3089a-144">Implement the basic toll calculations</span></span>

<span data-ttu-id="3089a-145">En temel Ücret hesaplama vehicle türüne bağlıdır:</span><span class="sxs-lookup"><span data-stu-id="3089a-145">The most basic toll calculation relies only on the vehicle type:</span></span>

- <span data-ttu-id="3089a-146">A `Car` 2,00 olduğu.</span><span class="sxs-lookup"><span data-stu-id="3089a-146">A `Car` is $2.00.</span></span>
- <span data-ttu-id="3089a-147">A `Taxi` $3.50 olduğu.</span><span class="sxs-lookup"><span data-stu-id="3089a-147">A `Taxi` is $3.50.</span></span>
- <span data-ttu-id="3089a-148">A `Bus` 5,00 $ ise.</span><span class="sxs-lookup"><span data-stu-id="3089a-148">A `Bus` is $5.00.</span></span>
- <span data-ttu-id="3089a-149">A `DeliveryTruck` $10,00 olduğu</span><span class="sxs-lookup"><span data-stu-id="3089a-149">A `DeliveryTruck` is $10.00</span></span>

<span data-ttu-id="3089a-150">Yeni bir `TollCalculator` sınıfı ve ücret tutarı almak için araç türüne desen uygulayın.</span><span class="sxs-lookup"><span data-stu-id="3089a-150">Create a new `TollCalculator` class, and implement pattern matching on the vehicle type to get the toll amount.</span></span> <span data-ttu-id="3089a-151">Aşağıdaki kod ilk uygulamasını gösterir `TollCalculator`.</span><span class="sxs-lookup"><span data-stu-id="3089a-151">The following code shows the initial implementation of the `TollCalculator`.</span></span>

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

<span data-ttu-id="3089a-152">Önceki kod bir **geçiş ifadesi** (aynı bir [ `switch` ](../language-reference/keywords/switch.md) deyimi) kullanan testlerin **türü deseni**.</span><span class="sxs-lookup"><span data-stu-id="3089a-152">The preceding code uses a **switch expression** (not the same as a [`switch`](../language-reference/keywords/switch.md) statement) that tests the **type pattern**.</span></span> <span data-ttu-id="3089a-153">A **geçiş ifadesi** değişkeniyle başlar `vehicle` önceki kodda, arkasından `switch` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="3089a-153">A **switch expression** begins with the variable, `vehicle` in the preceding code, followed by the `switch` keyword.</span></span> <span data-ttu-id="3089a-154">Sonraki tüm gelen **geçiş Silah** küme ayraçlarının içindeki.</span><span class="sxs-lookup"><span data-stu-id="3089a-154">Next comes all the **switch arms** inside curly braces.</span></span> <span data-ttu-id="3089a-155">`switch` İfade çevreleyen sözdizimine diğer iyileştirme yapar `switch` deyimi.</span><span class="sxs-lookup"><span data-stu-id="3089a-155">The `switch` expression makes other refinements to the syntax that surrounds the `switch` statement.</span></span> <span data-ttu-id="3089a-156">`case` Anahtar sözcüğü atlanırsa ve her bir arm sonucunu bir ifadedir.</span><span class="sxs-lookup"><span data-stu-id="3089a-156">The `case` keyword is omitted, and the result of each arm is an expression.</span></span> <span data-ttu-id="3089a-157">Son iki Silah yeni bir dil özelliği gösterir.</span><span class="sxs-lookup"><span data-stu-id="3089a-157">The last two arms show a new language feature.</span></span> <span data-ttu-id="3089a-158">`{ }` Çalışması eşleşen bir önceki arm eşleşmedi herhangi bir null olmayan nesne.</span><span class="sxs-lookup"><span data-stu-id="3089a-158">The `{ }` case matches any non-null object that didn't match an earlier arm.</span></span> <span data-ttu-id="3089a-159">Bu arm bu yönteme geçirilen yanlış türler yakalar.</span><span class="sxs-lookup"><span data-stu-id="3089a-159">This arm catches any incorrect types passed to this method.</span></span>  <span data-ttu-id="3089a-160">`{ }` Çalışması, her bir araç türü durumlarda izlemelidir.</span><span class="sxs-lookup"><span data-stu-id="3089a-160">The `{ }` case must follow the cases for each vehicle type.</span></span> <span data-ttu-id="3089a-161">Sırasını tersine çevrilmiş, `{ }` çalışması önceliklidir.</span><span class="sxs-lookup"><span data-stu-id="3089a-161">If the order were reversed, the `{ }` case would take precedence.</span></span> <span data-ttu-id="3089a-162">Son olarak, `null` algılar deseni bir `null` bu yönteme iletilir.</span><span class="sxs-lookup"><span data-stu-id="3089a-162">Finally, the `null` pattern detects when a `null` is passed to this method.</span></span> <span data-ttu-id="3089a-163">`null` Deseni bir türü desenleri yalnızca null olmayan bir nesne doğru türde olduğundan son olabilir.</span><span class="sxs-lookup"><span data-stu-id="3089a-163">The `null` pattern can be last because the other type patterns match only a non-null object of the correct type.</span></span>

<span data-ttu-id="3089a-164">Aşağıdaki kodu kullanarak bu kodu test edebilirsiniz `Program.cs`:</span><span class="sxs-lookup"><span data-stu-id="3089a-164">You can test this code using the following code in `Program.cs`:</span></span>

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

<span data-ttu-id="3089a-165">Bu kod, başlangıç projesine dahil, ancak devre dışı bırakılmışsa. Açıklamaları kaldırma ve yazdıklarınızı test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3089a-165">That code is included in the starter project, but is commented out. Remove the comments, and you can test what you've written.</span></span>

<span data-ttu-id="3089a-166">Desenler, kod ve verileri ayrı olduğu algoritmaları oluşturmanıza nasıl yardımcı olabileceğini görmek başlatılıyor.</span><span class="sxs-lookup"><span data-stu-id="3089a-166">You're starting to see how patterns can help you create algorithms where the code and the data are separate.</span></span> <span data-ttu-id="3089a-167">`switch` İfade türü test eder ve sonuçlarına bağlı olarak farklı değerlere üretir.</span><span class="sxs-lookup"><span data-stu-id="3089a-167">The `switch` expression tests the type and produces different values based on the results.</span></span> <span data-ttu-id="3089a-168">Bu yalnızca başlangıç adımıdır.</span><span class="sxs-lookup"><span data-stu-id="3089a-168">That's only the beginning.</span></span>

## <a name="add-occupancy-pricing"></a><span data-ttu-id="3089a-169">Sahiplik fiyatlandırma Ekle</span><span class="sxs-lookup"><span data-stu-id="3089a-169">Add occupancy pricing</span></span>

<span data-ttu-id="3089a-170">Maksimum kapasitede her fırsatta seyahat etmeye taşıtlardan teşvik etmek Ücretli yetkilisi istiyor.</span><span class="sxs-lookup"><span data-stu-id="3089a-170">The toll authority wants to encourage vehicles to travel at maximum capacity.</span></span> <span data-ttu-id="3089a-171">Araçlar daha az Yolcuların varsa ve daha düşük fiyatlandırma sunarak tam taşıtlardan teşvik daha kaydedilecek verdiyseniz:</span><span class="sxs-lookup"><span data-stu-id="3089a-171">They've decided to charge more when vehicles have fewer passengers, and encourage full vehicles by offering lower pricing:</span></span>

- <span data-ttu-id="3089a-172">Arabalar ve taksiler hiçbir Yolcuların ile bir ek 0,50 ABD Doları ücret ödersiniz.</span><span class="sxs-lookup"><span data-stu-id="3089a-172">Cars and taxis with no passengers pay an extra $0.50.</span></span>
- <span data-ttu-id="3089a-173">Arabalar ve iki Yolcuların ile taksiler 0,50 indirim elde edin.</span><span class="sxs-lookup"><span data-stu-id="3089a-173">Cars and taxis with two passengers get a 0.50 discount.</span></span>
- <span data-ttu-id="3089a-174">Arabalar ve üç veya daha fazla Yolcuların ile taksiler 1,00 indirim elde edin.</span><span class="sxs-lookup"><span data-stu-id="3089a-174">Cars and taxis with three or more passengers get a $1.00 discount.</span></span>
- <span data-ttu-id="3089a-175">Değerinden % 50 tam yolları 2,00 fazladan bir ücret ödersiniz.</span><span class="sxs-lookup"><span data-stu-id="3089a-175">Buses that are less than 50% full pay an extra $2.00.</span></span>
- <span data-ttu-id="3089a-176">Birden fazla % 90 tam olan yollarına 1,00 indirim alın.</span><span class="sxs-lookup"><span data-stu-id="3089a-176">Buses that are more than 90% full get a $1.00 discount.</span></span>

<span data-ttu-id="3089a-177">Bu kurallar kullanılarak uygulanır **özelliği desenini** aynı ifade geçin.</span><span class="sxs-lookup"><span data-stu-id="3089a-177">These rules can be implemented using the **property pattern** in the same switch expression.</span></span> <span data-ttu-id="3089a-178">Türü belirlendikten sonra özelliği düzeni nesnenin özelliklerini inceler.</span><span class="sxs-lookup"><span data-stu-id="3089a-178">The property pattern examines properties of the object once the type has been determined.</span></span> <span data-ttu-id="3089a-179">Tek bir kasada bir `Car` dört farklı çalışmalarına genişletir:</span><span class="sxs-lookup"><span data-stu-id="3089a-179">The single case for a `Car` expands to four different cases:</span></span>

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

<span data-ttu-id="3089a-180">İlk üç çalışmalarını test türü olarak bir `Car`, ardından değerini kontrol `Passengers` özelliği.</span><span class="sxs-lookup"><span data-stu-id="3089a-180">The first three cases test the type as a `Car`, then check the value of the `Passengers` property.</span></span> <span data-ttu-id="3089a-181">Her ikisi de eşleşirse, ifade değerlendirilir ve döndürdü.</span><span class="sxs-lookup"><span data-stu-id="3089a-181">If both match, that expression is evaluated and returned.</span></span>

<span data-ttu-id="3089a-182">Benzer şekilde taksiler durumlarda da genişletin:</span><span class="sxs-lookup"><span data-stu-id="3089a-182">You would also expand the cases for taxis in a similar manner:</span></span>

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

<span data-ttu-id="3089a-183">Önceki örnekte `when` son talebinde yan tümcesi çıkarılsaydı.</span><span class="sxs-lookup"><span data-stu-id="3089a-183">In the preceding example, the `when` clause was omitted on the final case.</span></span>

<span data-ttu-id="3089a-184">Ardından, sahiplik kuralları veri yolları durumlarda genişleterek aşağıdaki örnekte gösterildiği gibi uygulayın:</span><span class="sxs-lookup"><span data-stu-id="3089a-184">Next, implement the occupancy rules by expanding the cases for buses, as shown in the following example:</span></span>

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

<span data-ttu-id="3089a-185">Ücretli yetkilisi yolcu teslimi kamyon içinde sayısı ile ilgili değildir.</span><span class="sxs-lookup"><span data-stu-id="3089a-185">The toll authority isn't concerned with the number of passengers in the delivery trucks.</span></span> <span data-ttu-id="3089a-186">Bunun yerine, bunlar daha kamyon ağırlık sınıfında göre ücret alınır.</span><span class="sxs-lookup"><span data-stu-id="3089a-186">Instead, they charge more based on the weight class of the trucks.</span></span> <span data-ttu-id="3089a-187">Kamyon 5000 lbs üzerinde fazladan bir $5.00 ücretlendirilir.</span><span class="sxs-lookup"><span data-stu-id="3089a-187">Trucks over 5000 lbs are charged an extra $5.00.</span></span> <span data-ttu-id="3089a-188">Açık kamyon altında 3000 lbs 2,00 fiyatla sunulur.</span><span class="sxs-lookup"><span data-stu-id="3089a-188">Light trucks under 3000 lbs are given a $2.00 discount.</span></span> <span data-ttu-id="3089a-189">Bu kural, aşağıdaki kod ile gerçekleştirilir:</span><span class="sxs-lookup"><span data-stu-id="3089a-189">That rule is implemented with the following code:</span></span>

```csharp
vehicle switch
{
    // ...

    DeliveryTruck t when (t.GrossWeightClass > 5000) => 10.00m + 5.00m,
    DeliveryTruck t when (t.GrossWeightClass < 3000) => 10.00m - 2.00m,
    DeliveryTruck t => 10.00m,
};
```

<span data-ttu-id="3089a-190">Önceki kodun gösterdiği `when` anahtar arm yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="3089a-190">The preceding code shows the `when` clause of a switch arm.</span></span> <span data-ttu-id="3089a-191">Kullandığınız `when` özellikte eşitlik dışındaki koşulları test etmeye yönelik yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="3089a-191">You use the `when` clause to test conditions other than equality on a property.</span></span> <span data-ttu-id="3089a-192">İşiniz bittiğinde, aşağıdaki gibi görünen bir yöntem sahip olacaksınız:</span><span class="sxs-lookup"><span data-stu-id="3089a-192">When you've finished, you'll have a method that looks much like the following:</span></span>

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
};
```

<span data-ttu-id="3089a-193">Bunların çoğu Silah geçiş örnekler **özyinelemeli desenleri**.</span><span class="sxs-lookup"><span data-stu-id="3089a-193">Many of these switch arms are examples of **recursive patterns**.</span></span> <span data-ttu-id="3089a-194">Örneğin, `Car { Passengers: 1}` özelliği desenini içinde sabit bir deseni gösterir.</span><span class="sxs-lookup"><span data-stu-id="3089a-194">For example, `Car { Passengers: 1}` shows a constant pattern inside a property pattern.</span></span>

<span data-ttu-id="3089a-195">İç içe geçmiş anahtarlarını kullanarak bu kodu daha az tekrarlı yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3089a-195">You can make this code less repetitive by using nested switches.</span></span> <span data-ttu-id="3089a-196">`Car` Ve `Taxi` her ikisi de Yukarıdaki örneklerde dört farklı Silah sahiptir.</span><span class="sxs-lookup"><span data-stu-id="3089a-196">The `Car` and `Taxi` both have four different arms in the preceding examples.</span></span> <span data-ttu-id="3089a-197">Her iki durumda da, bir özellik modele akışları bir tür deseni oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3089a-197">In both cases, you can create a type pattern that feeds into a property pattern.</span></span> <span data-ttu-id="3089a-198">Bu teknik, aşağıdaki kodda gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="3089a-198">This technique is shown in the following code:</span></span>

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

<span data-ttu-id="3089a-199">Yukarıdaki örnekte, özyinelemeli ifadesi kullanarak yoksa yineleyin anlamına gelir `Car` ve `Taxi` içeren özellik değeri test alt Silah Silah.</span><span class="sxs-lookup"><span data-stu-id="3089a-199">In the preceding sample, using a recursive expression means you don't repeat the `Car` and `Taxi` arms containing child arms that test the property value.</span></span> <span data-ttu-id="3089a-200">Bu yöntem için kullanılmayan `Bus` ve `DeliveryTruck` bu Silah aralıkları özelliği değil ayrık değerler için test çünkü etkinleştirme.</span><span class="sxs-lookup"><span data-stu-id="3089a-200">This technique isn't used for the `Bus` and `DeliveryTruck` arms because those arms are testing ranges for the property, not discrete values.</span></span>

## <a name="add-peak-pricing"></a><span data-ttu-id="3089a-201">En yüksek fiyatlandırma Ekle</span><span class="sxs-lookup"><span data-stu-id="3089a-201">Add peak pricing</span></span>

<span data-ttu-id="3089a-202">Son bir özellik için ücretli yetkilisi hassas en yüksek süre fiyatlandırma eklemek istiyor.</span><span class="sxs-lookup"><span data-stu-id="3089a-202">For the final feature, the toll authority wants to add time sensitive peak pricing.</span></span> <span data-ttu-id="3089a-203">Ücretli geçişler iki katına sabah ve akşam yoğun saatler sırasında.</span><span class="sxs-lookup"><span data-stu-id="3089a-203">During the morning and evening rush hours, the tolls are doubled.</span></span> <span data-ttu-id="3089a-204">Bu kural yalnızca bir yöndeki trafiği etkiler: sabah şehirde gelen ve giden Akşam sağladığından saat içinde.</span><span class="sxs-lookup"><span data-stu-id="3089a-204">That rule only affects traffic in one direction: inbound to the city in the morning, and outbound in the evening rush hour.</span></span> <span data-ttu-id="3089a-205">Workday sırasında diğer zamanlarda, ücretli geçişler % 50'ye yükseltin.</span><span class="sxs-lookup"><span data-stu-id="3089a-205">During other times during the workday, tolls increase by 50%.</span></span> <span data-ttu-id="3089a-206">Gece geç ve erken sabah, ücretli geçişler 25 oranında azalır.</span><span class="sxs-lookup"><span data-stu-id="3089a-206">Late night and early morning, tolls are reduced by 25%.</span></span> <span data-ttu-id="3089a-207">Normal fiyat, saat bakılmaksızın olduğu tarihlerinde.</span><span class="sxs-lookup"><span data-stu-id="3089a-207">During the weekend, it's the normal rate, regardless of the time.</span></span>

<span data-ttu-id="3089a-208">Bu özellik için desen kullanacağız ancak bunu diğer teknikleri ile tümleştirmeniz.</span><span class="sxs-lookup"><span data-stu-id="3089a-208">You'll use pattern matching for this feature, but you'll integrate it with other techniques.</span></span> <span data-ttu-id="3089a-209">Hesap yön tüm bileşimleri, haftanın günü ve saat için bir tek desen eşleştirme ifadesi oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3089a-209">You could build a single pattern match expression that would account for all the combinations of direction, day of the week, and time.</span></span> <span data-ttu-id="3089a-210">Sonuç, karmaşık bir ifadeyi olur.</span><span class="sxs-lookup"><span data-stu-id="3089a-210">The result would be a complicated expression.</span></span> <span data-ttu-id="3089a-211">Okunmasını ve anlaşılması zor olacaktır.</span><span class="sxs-lookup"><span data-stu-id="3089a-211">It would be hard to read and difficult to understand.</span></span> <span data-ttu-id="3089a-212">Doğruluk emin olmak zorlaştırır.</span><span class="sxs-lookup"><span data-stu-id="3089a-212">That makes it hard to ensure correctness.</span></span> <span data-ttu-id="3089a-213">Bunun yerine, tüm eyaletler kısaca açıklayan bir demet değerler oluşturmak için bu yöntemleri birleştirin.</span><span class="sxs-lookup"><span data-stu-id="3089a-213">Instead, combine those methods to build a tuple of values that concisely describes all those states.</span></span> <span data-ttu-id="3089a-214">Ardından Ücretli çarpanı hesaplamak için desen eşleştirme kullanın.</span><span class="sxs-lookup"><span data-stu-id="3089a-214">Then use pattern matching to calculate a multiplier for the toll.</span></span> <span data-ttu-id="3089a-215">Tanımlama grubu üç farklı koşullar içeriyor:</span><span class="sxs-lookup"><span data-stu-id="3089a-215">The tuple contains three discrete conditions:</span></span>

- <span data-ttu-id="3089a-216">, Bir hafta içi gün veya hafta günüdür.</span><span class="sxs-lookup"><span data-stu-id="3089a-216">The day is either a weekday or a weekend.</span></span>
- <span data-ttu-id="3089a-217">Zaman zaman Ücretli toplandıktan bant.</span><span class="sxs-lookup"><span data-stu-id="3089a-217">The band of time when the toll is collected.</span></span>
- <span data-ttu-id="3089a-218">Şehir veya şehir dışında yönüdür</span><span class="sxs-lookup"><span data-stu-id="3089a-218">The direction is into the city or out of the city</span></span>

<span data-ttu-id="3089a-219">Aşağıdaki tabloda, giriş değerleri birleşimlerini ve çarpan fiyatlandırma yoğun gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="3089a-219">The following table shows the combinations of input values and the peak pricing multiplier:</span></span>

| <span data-ttu-id="3089a-220">Gün</span><span class="sxs-lookup"><span data-stu-id="3089a-220">Day</span></span>        | <span data-ttu-id="3089a-221">Zaman</span><span class="sxs-lookup"><span data-stu-id="3089a-221">Time</span></span>         | <span data-ttu-id="3089a-222">Yön</span><span class="sxs-lookup"><span data-stu-id="3089a-222">Direction</span></span> | <span data-ttu-id="3089a-223">Premium</span><span class="sxs-lookup"><span data-stu-id="3089a-223">Premium</span></span> |
| ---------- | ------------ | --------- |--------:|
| <span data-ttu-id="3089a-224">Haftanın günü</span><span class="sxs-lookup"><span data-stu-id="3089a-224">Weekday</span></span>    | <span data-ttu-id="3089a-225">sabah sağladığından</span><span class="sxs-lookup"><span data-stu-id="3089a-225">morning rush</span></span> | <span data-ttu-id="3089a-226">Gelen</span><span class="sxs-lookup"><span data-stu-id="3089a-226">inbound</span></span>   | <span data-ttu-id="3089a-227">2,00 x</span><span class="sxs-lookup"><span data-stu-id="3089a-227">x 2.00</span></span>  |
| <span data-ttu-id="3089a-228">Haftanın günü</span><span class="sxs-lookup"><span data-stu-id="3089a-228">Weekday</span></span>    | <span data-ttu-id="3089a-229">sabah sağladığından</span><span class="sxs-lookup"><span data-stu-id="3089a-229">morning rush</span></span> | <span data-ttu-id="3089a-230">Giden</span><span class="sxs-lookup"><span data-stu-id="3089a-230">outbound</span></span>  | <span data-ttu-id="3089a-231">1,00 x</span><span class="sxs-lookup"><span data-stu-id="3089a-231">x 1.00</span></span>  |
| <span data-ttu-id="3089a-232">Haftanın günü</span><span class="sxs-lookup"><span data-stu-id="3089a-232">Weekday</span></span>    | <span data-ttu-id="3089a-233">Daytime</span><span class="sxs-lookup"><span data-stu-id="3089a-233">daytime</span></span>      | <span data-ttu-id="3089a-234">Gelen</span><span class="sxs-lookup"><span data-stu-id="3089a-234">inbound</span></span>   | <span data-ttu-id="3089a-235">1.50 x</span><span class="sxs-lookup"><span data-stu-id="3089a-235">x 1.50</span></span>  |
| <span data-ttu-id="3089a-236">Haftanın günü</span><span class="sxs-lookup"><span data-stu-id="3089a-236">Weekday</span></span>    | <span data-ttu-id="3089a-237">Daytime</span><span class="sxs-lookup"><span data-stu-id="3089a-237">daytime</span></span>      | <span data-ttu-id="3089a-238">Giden</span><span class="sxs-lookup"><span data-stu-id="3089a-238">outbound</span></span>  | <span data-ttu-id="3089a-239">1.50 x</span><span class="sxs-lookup"><span data-stu-id="3089a-239">x 1.50</span></span>  |
| <span data-ttu-id="3089a-240">Haftanın günü</span><span class="sxs-lookup"><span data-stu-id="3089a-240">Weekday</span></span>    | <span data-ttu-id="3089a-241">Akşam sağladığından</span><span class="sxs-lookup"><span data-stu-id="3089a-241">evening rush</span></span> | <span data-ttu-id="3089a-242">Gelen</span><span class="sxs-lookup"><span data-stu-id="3089a-242">inbound</span></span>   | <span data-ttu-id="3089a-243">1,00 x</span><span class="sxs-lookup"><span data-stu-id="3089a-243">x 1.00</span></span>  |
| <span data-ttu-id="3089a-244">Haftanın günü</span><span class="sxs-lookup"><span data-stu-id="3089a-244">Weekday</span></span>    | <span data-ttu-id="3089a-245">Akşam sağladığından</span><span class="sxs-lookup"><span data-stu-id="3089a-245">evening rush</span></span> | <span data-ttu-id="3089a-246">Giden</span><span class="sxs-lookup"><span data-stu-id="3089a-246">outbound</span></span>  | <span data-ttu-id="3089a-247">2,00 x</span><span class="sxs-lookup"><span data-stu-id="3089a-247">x 2.00</span></span>  |
| <span data-ttu-id="3089a-248">Haftanın günü</span><span class="sxs-lookup"><span data-stu-id="3089a-248">Weekday</span></span>    | <span data-ttu-id="3089a-249">gece</span><span class="sxs-lookup"><span data-stu-id="3089a-249">overnight</span></span>    | <span data-ttu-id="3089a-250">Gelen</span><span class="sxs-lookup"><span data-stu-id="3089a-250">inbound</span></span>   | <span data-ttu-id="3089a-251">0,75 x</span><span class="sxs-lookup"><span data-stu-id="3089a-251">x 0.75</span></span>  |
| <span data-ttu-id="3089a-252">Haftanın günü</span><span class="sxs-lookup"><span data-stu-id="3089a-252">Weekday</span></span>    | <span data-ttu-id="3089a-253">gece</span><span class="sxs-lookup"><span data-stu-id="3089a-253">overnight</span></span>    | <span data-ttu-id="3089a-254">Giden</span><span class="sxs-lookup"><span data-stu-id="3089a-254">outbound</span></span>  | <span data-ttu-id="3089a-255">0,75 x</span><span class="sxs-lookup"><span data-stu-id="3089a-255">x 0.75</span></span>  |
| <span data-ttu-id="3089a-256">Hafta sonu</span><span class="sxs-lookup"><span data-stu-id="3089a-256">Weekend</span></span>    | <span data-ttu-id="3089a-257">sabah sağladığından</span><span class="sxs-lookup"><span data-stu-id="3089a-257">morning rush</span></span> | <span data-ttu-id="3089a-258">Gelen</span><span class="sxs-lookup"><span data-stu-id="3089a-258">inbound</span></span>   | <span data-ttu-id="3089a-259">1,00 x</span><span class="sxs-lookup"><span data-stu-id="3089a-259">x 1.00</span></span>  |
| <span data-ttu-id="3089a-260">Hafta sonu</span><span class="sxs-lookup"><span data-stu-id="3089a-260">Weekend</span></span>    | <span data-ttu-id="3089a-261">sabah sağladığından</span><span class="sxs-lookup"><span data-stu-id="3089a-261">morning rush</span></span> | <span data-ttu-id="3089a-262">Giden</span><span class="sxs-lookup"><span data-stu-id="3089a-262">outbound</span></span>  | <span data-ttu-id="3089a-263">1,00 x</span><span class="sxs-lookup"><span data-stu-id="3089a-263">x 1.00</span></span>  |
| <span data-ttu-id="3089a-264">Hafta sonu</span><span class="sxs-lookup"><span data-stu-id="3089a-264">Weekend</span></span>    | <span data-ttu-id="3089a-265">Daytime</span><span class="sxs-lookup"><span data-stu-id="3089a-265">daytime</span></span>      | <span data-ttu-id="3089a-266">Gelen</span><span class="sxs-lookup"><span data-stu-id="3089a-266">inbound</span></span>   | <span data-ttu-id="3089a-267">1,00 x</span><span class="sxs-lookup"><span data-stu-id="3089a-267">x 1.00</span></span>  |
| <span data-ttu-id="3089a-268">Hafta sonu</span><span class="sxs-lookup"><span data-stu-id="3089a-268">Weekend</span></span>    | <span data-ttu-id="3089a-269">Daytime</span><span class="sxs-lookup"><span data-stu-id="3089a-269">daytime</span></span>      | <span data-ttu-id="3089a-270">Giden</span><span class="sxs-lookup"><span data-stu-id="3089a-270">outbound</span></span>  | <span data-ttu-id="3089a-271">1,00 x</span><span class="sxs-lookup"><span data-stu-id="3089a-271">x 1.00</span></span>  |
| <span data-ttu-id="3089a-272">Hafta sonu</span><span class="sxs-lookup"><span data-stu-id="3089a-272">Weekend</span></span>    | <span data-ttu-id="3089a-273">Akşam sağladığından</span><span class="sxs-lookup"><span data-stu-id="3089a-273">evening rush</span></span> | <span data-ttu-id="3089a-274">Gelen</span><span class="sxs-lookup"><span data-stu-id="3089a-274">inbound</span></span>   | <span data-ttu-id="3089a-275">1,00 x</span><span class="sxs-lookup"><span data-stu-id="3089a-275">x 1.00</span></span>  |
| <span data-ttu-id="3089a-276">Hafta sonu</span><span class="sxs-lookup"><span data-stu-id="3089a-276">Weekend</span></span>    | <span data-ttu-id="3089a-277">Akşam sağladığından</span><span class="sxs-lookup"><span data-stu-id="3089a-277">evening rush</span></span> | <span data-ttu-id="3089a-278">Giden</span><span class="sxs-lookup"><span data-stu-id="3089a-278">outbound</span></span>  | <span data-ttu-id="3089a-279">1,00 x</span><span class="sxs-lookup"><span data-stu-id="3089a-279">x 1.00</span></span>  |
| <span data-ttu-id="3089a-280">Hafta sonu</span><span class="sxs-lookup"><span data-stu-id="3089a-280">Weekend</span></span>    | <span data-ttu-id="3089a-281">gece</span><span class="sxs-lookup"><span data-stu-id="3089a-281">overnight</span></span>    | <span data-ttu-id="3089a-282">Gelen</span><span class="sxs-lookup"><span data-stu-id="3089a-282">inbound</span></span>   | <span data-ttu-id="3089a-283">1,00 x</span><span class="sxs-lookup"><span data-stu-id="3089a-283">x 1.00</span></span>  |
| <span data-ttu-id="3089a-284">Hafta sonu</span><span class="sxs-lookup"><span data-stu-id="3089a-284">Weekend</span></span>    | <span data-ttu-id="3089a-285">gece</span><span class="sxs-lookup"><span data-stu-id="3089a-285">overnight</span></span>    | <span data-ttu-id="3089a-286">Giden</span><span class="sxs-lookup"><span data-stu-id="3089a-286">outbound</span></span>  | <span data-ttu-id="3089a-287">1,00 x</span><span class="sxs-lookup"><span data-stu-id="3089a-287">x 1.00</span></span>  |

<span data-ttu-id="3089a-288">Üç değişkenin 16 farklı birleşimlerini vardır.</span><span class="sxs-lookup"><span data-stu-id="3089a-288">There are 16 different combinations of the three variables.</span></span> <span data-ttu-id="3089a-289">Bazı koşullar birleştirerek son switch ifadesi basitleştireceğiz.</span><span class="sxs-lookup"><span data-stu-id="3089a-289">By combining some of the conditions, you'll simplify the final switch expression.</span></span>

<span data-ttu-id="3089a-290">Ücretli geçişler toplayan sistem kullanan bir <xref:System.DateTime> zaman Ücretli toplanmıştır kez yapısı.</span><span class="sxs-lookup"><span data-stu-id="3089a-290">The system that collects the tolls uses a <xref:System.DateTime> structure for the time when the toll was collected.</span></span> <span data-ttu-id="3089a-291">Önceki tabloda değişkenlerinin üye yöntemleri oluşturun.</span><span class="sxs-lookup"><span data-stu-id="3089a-291">Build member methods that create the variables from the preceding table.</span></span> <span data-ttu-id="3089a-292">Aşağıdaki işlev express için switch ifadesi bir desen kullanır. olup olmadığını bir <xref:System.DateTime> hafta veya bir iş günü temsil eder:</span><span class="sxs-lookup"><span data-stu-id="3089a-292">The following function uses a pattern matching switch expression to express whether a <xref:System.DateTime> represents a weekend or a weekday:</span></span>

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

<span data-ttu-id="3089a-293">Bu yöntem çalışır, ancak tekrarlayan.</span><span class="sxs-lookup"><span data-stu-id="3089a-293">That method works, but it's repetitious.</span></span> <span data-ttu-id="3089a-294">Aşağıdaki kodda gösterildiği gibi basitleştirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="3089a-294">You can simplify it, as shown in the following code:</span></span>

[!code-csharp[IsWeekDay](~/samples/csharp/tutorials/patterns/finished/toll-calculator/TollCalculator.cs#IsWeekDay)]

<span data-ttu-id="3089a-295">Ardından, bloklarda süreyi kategorilere ayıran bir benzer işlevi ekleyin:</span><span class="sxs-lookup"><span data-stu-id="3089a-295">Next, add a similar function to categorize the time into the blocks:</span></span>

[!code-csharp[GetTimeBand](~/samples/csharp/tutorials/patterns/finished/toll-calculator/TollCalculator.cs#GetTimeBand)]

<span data-ttu-id="3089a-296">Desen eşleştirme yönteminin kullanmaz.</span><span class="sxs-lookup"><span data-stu-id="3089a-296">The previous method doesn't use pattern matching.</span></span> <span data-ttu-id="3089a-297">Tanıdık bir cascade birini kullanarak nettir `if` deyimleri.</span><span class="sxs-lookup"><span data-stu-id="3089a-297">It's clearer using a familiar cascade of `if` statements.</span></span> <span data-ttu-id="3089a-298">Özel bir ekleme `enum` her zaman aralığı bir ayrık değere dönüştürülecek.</span><span class="sxs-lookup"><span data-stu-id="3089a-298">You do add a private `enum` to convert each range of time to a discrete value.</span></span>

<span data-ttu-id="3089a-299">Bu yöntemleri oluşturduktan sonra başka kullanabilirsiniz `switch` ifadesiyle **kayıt düzeni deseni** fiyatlandırma premium hesaplamak için.</span><span class="sxs-lookup"><span data-stu-id="3089a-299">After you create those methods, you can use another `switch` expression with the **tuple pattern** to calculate the pricing premium.</span></span> <span data-ttu-id="3089a-300">Derleme bir `switch` 16 kollu ifade:</span><span class="sxs-lookup"><span data-stu-id="3089a-300">You could build a `switch` expression with all 16 arms:</span></span>

[!code-csharp[FullTuplePattern](~/samples/csharp/tutorials/patterns/finished/toll-calculator/TollCalculator.cs#TuplePatternOne)]

<span data-ttu-id="3089a-301">Yukarıdaki kodu çalışır, ancak Basitleştirilmiş.</span><span class="sxs-lookup"><span data-stu-id="3089a-301">The above code works, but it can be simplified.</span></span> <span data-ttu-id="3089a-302">Tüm sekiz hafta birleşimlerini aynı Ücretli vardır.</span><span class="sxs-lookup"><span data-stu-id="3089a-302">All eight combinations for the weekend have the same toll.</span></span> <span data-ttu-id="3089a-303">Tüm sekiz aşağıdaki satırı ile değiştirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="3089a-303">You can replace all eight with the following line:</span></span>

```csharp
(false, _, _) => 1.0m,
```

<span data-ttu-id="3089a-304">Gelen ve giden trafiği, ertesi gün saat ve haftanın günü daytime sırasında aynı çarpan vardır.</span><span class="sxs-lookup"><span data-stu-id="3089a-304">Both inbound and outbound traffic have the same multiplier during the weekday daytime and overnight hours.</span></span> <span data-ttu-id="3089a-305">Bu dört anahtar Silah aşağıdaki iki satır ile değiştirilebilir:</span><span class="sxs-lookup"><span data-stu-id="3089a-305">Those four switch arms can be replaced with the following two lines:</span></span>

```csharp
(true, TimeBand.Overnight, _) => 0.75m,
(true, TimeBand.Daytime, _)   => 1.5m,
```

<span data-ttu-id="3089a-306">Kod, sonra bu iki değişikliği şu kod gibi görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="3089a-306">The code should look like the following code after those two changes:</span></span>

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

<span data-ttu-id="3089a-307">Son olarak, normal ücretini ödemem saat kez iki sağladığından kaldırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3089a-307">Finally, you can remove the two rush hour times that pay the regular price.</span></span> <span data-ttu-id="3089a-308">Bu Silah kaldırdıktan sonra değiştirebileceğiniz `false` bir atma ile (`_`) son anahtar arm içinde.</span><span class="sxs-lookup"><span data-stu-id="3089a-308">Once you remove those arms, you can replace the `false` with a discard (`_`) in the final switch arm.</span></span> <span data-ttu-id="3089a-309">Aşağıdaki tamamlanmış yöntemi vardır:</span><span class="sxs-lookup"><span data-stu-id="3089a-309">You'll have the following finished method:</span></span>

[!code-csharp[SimplifiedTuplePattern](../../../samples/csharp/tutorials/patterns/finished/toll-calculator/TollCalculator.cs#FinalTuplePattern)]

<span data-ttu-id="3089a-310">Bu örnek bir desen eşleştirme avantajlarını vurgular: Düzen dalları sırayla değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="3089a-310">This example highlights one of the advantages of pattern matching: the pattern branches are evaluated in order.</span></span> <span data-ttu-id="3089a-311">Önceki bir dalı, sonraki durumlarından biri işler, böylece bunları yeniden düzenlerseniz, derleyici, erişilemeyen kod hakkında sizi uyarır.</span><span class="sxs-lookup"><span data-stu-id="3089a-311">If you rearrange them so that an earlier branch handles one of your later cases, the compiler warns you about the unreachable code.</span></span> <span data-ttu-id="3089a-312">Bu dil kuralları önceki basitleştirme kod değişmedi güvenle yapmak daha kolay yapılır.</span><span class="sxs-lookup"><span data-stu-id="3089a-312">Those language rules made it easier to do the preceding simplifications with confidence that the code didn't change.</span></span>

<span data-ttu-id="3089a-313">Desen eşleştirme, bazı türleri kod daha okunabilir hale getirir ve sınıflarınızı için kod eklenemiyor, teknikleri nesne yönelimli bir alternatif sunar.</span><span class="sxs-lookup"><span data-stu-id="3089a-313">Pattern matching makes some types of code more readable and offers an alternative to object-oriented techniques when you can't add code to your classes.</span></span> <span data-ttu-id="3089a-314">Bulut, veri ve İşlevler parçalayın Canlı neden oluyor.</span><span class="sxs-lookup"><span data-stu-id="3089a-314">The cloud is causing data and functionality to live apart.</span></span> <span data-ttu-id="3089a-315">*Şekli* verilerin ve *işlemleri* açık olmayan mutlaka anlatılan birlikte.</span><span class="sxs-lookup"><span data-stu-id="3089a-315">The *shape* of the data and the *operations* on it aren't necessarily described together.</span></span> <span data-ttu-id="3089a-316">Bu öğreticide, kendi özgün işlevden tamamen farklı şekillerde mevcut verilerini kullandınız.</span><span class="sxs-lookup"><span data-stu-id="3089a-316">In this tutorial, you consumed existing data in entirely different ways from its original function.</span></span> <span data-ttu-id="3089a-317">Desen eşleştirme genişletmek uygulanamadı olsa da bu türlerin geçersiz kılınmış işlevselliği yazma olanağı getirdi.</span><span class="sxs-lookup"><span data-stu-id="3089a-317">Pattern matching gave you the ability to write functionality that overrode those types, even though you couldn't extend them.</span></span>

## <a name="next-steps"></a><span data-ttu-id="3089a-318">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="3089a-318">Next steps</span></span>

<span data-ttu-id="3089a-319">Tamamlanan kodu indirebileceğiniz [dotnet/samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/patterns/finished) GitHub deposu.</span><span class="sxs-lookup"><span data-stu-id="3089a-319">You can download the finished code from the [dotnet/samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/patterns/finished) GitHub repository.</span></span> <span data-ttu-id="3089a-320">Desenler kendiniz keşfedin ve bu tekniği normal kodlama etkinliklerinizi ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3089a-320">Explore patterns on your own and add this technique into your regular coding activities.</span></span> <span data-ttu-id="3089a-321">Bu teknikler öğrenme, sorunları yaklaşımını ve yeni işlevler oluşturmak için başka bir yol sunar.</span><span class="sxs-lookup"><span data-stu-id="3089a-321">Learning these techniques gives you another way to approach problems and create new functionality.</span></span>
