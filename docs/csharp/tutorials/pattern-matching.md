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
# <a name="tutorial-using-pattern-matching-features-to-extend-data-types"></a>Öğretici: Veri türlerini genişletmek için desen eşleştirme özelliklerini kullanma

C# 7 temel desen eşleştirme özelliklerini tanıttı. Bu özellikler C# 8'de yeni ifadeler ve desenlerle genişletilir. Diğer kitaplıklarda olabilecek türleri genişletmiş gibi görünen işlevler yazabilirsiniz. Desenler için başka bir kullanım, uygulamanızın genişletilmekte olan türün temel bir özelliği olmayan işlevselliği oluşturmaktır.

Bu öğreticide şunların nasıl yapıldığını öğreneceksiniz:

> [!div class="checklist"]
>
> - Desen eşleştirmenin kullanılması gereken durumları tanıyın.
> - Türleri ve özellik değerlerini temel alan davranışı uygulamak için desen eşleştirme ifadelerini kullanın.
> - Tam algoritmalar oluşturmak için desen eşleştirmeyi diğer tekniklerle birleştirin.

## <a name="prerequisites"></a>Önkoşullar

C# 8.0 derleyicisi de dahil olmak üzere .NET Core'u çalıştıracak şekilde makinenizi ayarlamanız gerekir. C# 8 derleyicisi [Visual Studio 2019 sürüm 16.3](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) veya [.NET Core 3.0 SDK](https://dotnet.microsoft.com/download)ile başlayarak kullanılabilir.

Bu öğretici, Visual Studio veya .NET Core CLI dahil olmak üzere C# ve .NET'e aşina olduğunuzu varsayar.

## <a name="scenarios-for-pattern-matching"></a>Desen eşleştirme senaryoları

Modern geliştirme genellikle birden çok kaynaktan gelen verileri tümleştirmeyi ve bu verilerden elde edilen bilgi ve öngörüleri tek bir tutarlı uygulamada sunmayı içerir. Siz ve ekibiniz, gelen verileri temsil eden tüm türler için denetime veya erişime sahip olmazsınız.

Klasik nesne yönelimli tasarım, uygulamanızda bu birden çok veri kaynağından her veri türünü temsil eden türler oluşturmayı çağırır. Ardından, uygulamanız bu yeni türlerle çalışır, devralma hiyerarşileri oluşturur, sanal yöntemler oluşturur ve soyutlamalar uygular. Bu teknikler çalışır ve bazen en iyi araçlardır. Diğer zamanlarda daha az kod yazabilirsiniz. Verileri, bu verileri işleyen işlemlerden ayıran teknikleri kullanarak daha net kod yazabilirsiniz.

Bu öğreticide, tek bir senaryo için çeşitli dış kaynaklardan gelen verileri alan bir uygulama oluşturur ve keşfe esünüz. **Desen eşleştirmenin,** bu verileri özgün sistemin bir parçası olmayan şekillerde tüketmenin ve işlemenin etkili bir yolunu nasıl sağladığını görürsünüz.

Trafiği yönetmek için geçiş ücretleri ve en yüksek zaman fiyatlandırması kullanan büyük bir metropol alanı düşünün. Bir aracın geçiş ücretlerini türüne göre hesaplayan bir uygulama yazarsınız. Daha sonraki geliştirmeler, araçtaki yolcu sayısına bağlı olarak fiyatlandırmayı içerir. Diğer geliştirmeler, haftanın saatine ve gününe bağlı olarak fiyatlandırma ekler.

Bu kısa açıklamadan, bu sistemi modellemek için hızlı bir şekilde bir nesne hiyerarşisi çizmiş olabilirsiniz. Ancak, verileriniz diğer araç kayıt yönetim sistemleri gibi birden fazla kaynaktan geliyor. Bu sistemler, bu verileri modellemek için farklı sınıflar sağlar ve kullanabileceğiniz tek bir nesne modeli yoktur. Bu öğreticide, aşağıdaki kodda gösterildiği gibi, bu dış sistemlerden araç verilerini modellemek için bu basitleştirilmiş sınıfları kullanırsınız:

[!code-csharp[ExternalSystems](~/samples/snippets/csharp/tutorials/patterns/start/toll-calculator/ExternalSystems.cs)]

Başlangıç kodunu [dotnet/samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/patterns/start) GitHub deposundan indirebilirsiniz. Araç sınıflarının farklı sistemlerden ve farklı ad alanlarında olduğunu görebilirsiniz. Kaldıraçtan başka `System.Object` ortak bir taban sınıfı yoktur.

## <a name="pattern-matching-designs"></a>Desen eşleştirme tasarımları

Bu öğreticide kullanılan senaryo, desen eşleştirmesinin çözmek için uygun olduğu sorun türlerini vurgular:

- Birlikte çalışmanız gereken nesneler, hedeflerinizle eşleşen bir nesne hiyerarşisinde değildir. İlişkisiz sistemlerin bir parçası olan sınıflarla çalışıyor olabilirsiniz.
- Eklediğiniz işlevsellik, bu sınıflar için temel soyutlamanın bir parçası değildir. Bir araç tarafından ödenen geçiş ücreti farklı araç türleri için *değişir,* ancak geçiş ücreti aracın temel işlevi değildir.

Verilerin *şekli* ve bu verilerdeki *işlemler* birlikte açıklanmadığında, C#'daki desen eşleştirme özellikleri çalışmayı kolaylaştırır.

## <a name="implement-the-basic-toll-calculations"></a>Temel geçiş ücreti hesaplamalarını uygulayın

En temel geçiş ücreti hesaplaması yalnızca araç tipine bağlıdır:

- A `Car` 2.00 dolar.
- A `Taxi` 3.50 dolar.
- A `Bus` 5.00 dolar.
- A `DeliveryTruck` 10,00 $ olduğunu

Yeni `TollCalculator` bir sınıf oluşturun ve geçiş ücreti miktarını almak için araç türüne uygun desen uygulayın. Aşağıdaki `TollCalculator`kod, ilk uygulama gösterir.

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

Önceki kod, **tür deseni**test eden [`switch`](../language-reference/keywords/switch.md) bir anahtar **ifadesi** (deyimle aynı değil) kullanır. Bir **anahtar ifadesi,** önceki `vehicle` kodda, `switch` anahtar kelime tarafından izlenen değişkenile başlar. Sonra kıvırcık parantez içinde tüm **geçiş kolları** geliyor. İfade, `switch` `switch` deyimi çevreleyen sözdiziminde başka iyileştirmeler yapar. Anahtar `case` kelime atlanır ve her kolun sonucu bir ifadedir. Son iki kol yeni bir dil özelliği gösteriyor. Kasa, `{ }` önceki bir kolla eşleşmeyen null olmayan nesnelerle eşleşiyor. Bu kol, bu yönteme geçirilen herhangi bir yanlış türleri yakalar.  Dava, `{ }` her araç tipi için vakaları takip etmelidir. Sipariş tersine çevrilseydi, `{ }` servis talebi öncelikli olurdu. Son olarak, `null` desen bu `null` yönteme bir geçirildiğinde algılar. Diğer `null` tür desenleri yalnızca doğru türün null olmayan bir nesnesi ile eşleştirdiği için desen son olabilir.

Bu kodu aşağıdaki kodu kullanarak `Program.cs`test edebilirsiniz:

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

Bu kod başlangıç projesine dahil edilir, ancak yorumlanır. Yorumları kaldırın ve yazdıklarınızı test edebilirsiniz.

Desenlerin, kod ve verilerin ayrı olduğu algoritmalar oluşturmanıza nasıl yardımcı olabileceğini görmeye başlıyorsunuz. İfade `switch` türünü sınar ve sonuçlara göre farklı değerler üretir. Bu sadece başlangıç.

## <a name="add-occupancy-pricing"></a>Doluluk fiyatlandırması ekleme

Ücretli makamlar araçları maksimum kapasitede seyahat etmeye teşvik etmek istiyor. Araçlar daha az yolcu olduğunda daha fazla ücret almaya ve daha düşük fiyatlandırma sunarak tam araçları teşvik etmeye karar verdiler:

- Yolcusuz arabalar ve taksiler fazladan 0.50 dolar ödüyor.
- İki yolculu araba ve taksiler 0,50 $ indirim olsun.
- Üç veya daha fazla yolcu ile otomobil ve taksiler 1,00 $ indirim olsun.
- Otobüsler az% 50 tam ekstra 2,00 $ ödemek.
- %90'dan fazla tam otobüs 1,00 $ indirim alırsınız.

Bu kurallar, aynı anahtar ifadesinde **özellik deseni** kullanılarak uygulanabilir. Özellik deseni, tür belirlendikten sonra nesnenin özelliklerini inceler. Bir `Car` durum için tek bir durum dört farklı durumda genişletir:

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

İlk üç durumda bir `Car`olarak türünü test , `Passengers` sonra özelliğin değerini kontrol edin. Her ikisi de eşleşirse, bu ifade değerlendirilir ve döndürülür.

Ayrıca benzer bir şekilde taksiler için durumlarda genişletmek istiyorsunuz:

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

Önceki örnekte, `when` son durumda madde atlandı.

Ardından, aşağıdaki örnekte gösterildiği gibi, otobüsler için servis taleplerini genişleterek doluluk kurallarını uygulayın:

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

Gişe yetkilisi teslimat kamyonlarında yolcu sayısı ile ilgili değildir. Bunun yerine, kamyonların ağırlık sınıfına göre geçiş ücreti tutarını aşağıdaki gibi ayarlarlar:

- 5000 lbs üzerinde kamyonlar ekstra 5,00 $ tahsil edilir.
- 3000 £ altında hafif kamyonlar 2,00 $ indirim verilir.

Bu kural aşağıdaki kodla uygulanır:

```csharp
vehicle switch
{
    // ...

    DeliveryTruck t when (t.GrossWeightClass > 5000) => 10.00m + 5.00m,
    DeliveryTruck t when (t.GrossWeightClass < 3000) => 10.00m - 2.00m,
    DeliveryTruck t => 10.00m,
};
```

Önceki kod, bir `when` anahtar kolunun yan tümcesini gösterir. Bu yan `when` tümceyi, bir mülkte eşitlik dışındaki koşulları test etmek için kullanırsınız. Bitirdikten sonra, aşağıdakigibi görünen bir yönteme sahip olacaksınız:

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

Bu anahtar kollarıçoğu **özyinelemeli desenler**e-örnektir. Örneğin, `Car { Passengers: 1}` bir özellik deseni içinde sabit bir desen gösterir.

İç içe geçen anahtarları kullanarak bu kodu daha az yineleyebilirsiniz. Ve `Car` `Taxi` her ikisi de önceki örneklerde dört farklı kola sahiptir. Her iki durumda da, bir özellik deseni içine beslenen bir tür deseni oluşturabilirsiniz. Bu teknik aşağıdaki kodda gösterilmiştir:

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

Önceki örnekte, özyinelemeli bir ifade kullanmak, özellik değerini `Car` test `Taxi` eden alt kollar içeren kolları tekrarlamadığınız anlamına gelir. Bu teknik ve `Bus` `DeliveryTruck` kollar için kullanılmaz çünkü bu kollar ayrık değerler için değil, özellik için test aralıklarıdır.

## <a name="add-peak-pricing"></a>En yüksek fiyatlandırma ekleme

Son özellik için, ücretli makam zamana duyarlı pik fiyatlandırma eklemek istiyor. Sabah ve akşam yoğun saatlerde geçiş ücretleri iki katına çıkar. Bu kural sadece bir yönde trafiği etkiler: sabah şehre gelen ve akşam yoğun saatlerde giden. İş günü boyunca diğer zamanlarda, geçiş ücretleri% 50 oranında artar. Gece geç saatlerde ve sabahın erken saatlerinde geçiş ücretleri %25 oranında azalır. Hafta sonu, ne olursa olsun zaman, normal oran's.

Bu özellik için desen eşleştirme kullanırsınız, ancak diğer tekniklerle tümleştirirsiniz. Tüm yön, haftanın günü ve zaman birleşimlerini hesaba katacak tek bir desen eşlemi ifadesi oluşturabilirsiniz. Sonuç karmaşık bir ifade olacaktır. Okuması ve anlaşılması zor olurdu. Bu da doğruluğu sağlamayı zorlaştırıyor. Bunun yerine, tüm bu durumları kısa bir şekilde açıklayan bir değer tuple'ı oluşturmak için bu yöntemleri birleştirin. Ardından, geçiş ücreti için çarpanı hesaplamak için desen eşleştirmesini kullanın. Tuple üç ayrı koşul içerir:

- Gün ya hafta içi ya da hafta sonu.
- Geçiş ücretinin tahsil edildiği zaman grubu.
- Yön şehre ya da şehir dışına doğru

Aşağıdaki tablo, giriş değerlerinin ve en yüksek fiyatlandırma çarpanının birleşimlerini gösterir:

| Gün        | Zaman         | Yön | Premium |
| ---------- | ------------ | --------- |--------:|
| Weekday    | sabah acele | gelen   | x 2,00  |
| Weekday    | sabah acele | Giden  | x 1,00  |
| Weekday    | Gündüz      | gelen   | x 1,50  |
| Weekday    | Gündüz      | Giden  | x 1,50  |
| Weekday    | akşam acele | gelen   | x 1,00  |
| Weekday    | akşam acele | Giden  | x 2,00  |
| Weekday    | Gece    | gelen   | x 0,75  |
| Weekday    | Gece    | Giden  | x 0,75  |
| Hafta Sonu    | sabah acele | gelen   | x 1,00  |
| Hafta Sonu    | sabah acele | Giden  | x 1,00  |
| Hafta Sonu    | Gündüz      | gelen   | x 1,00  |
| Hafta Sonu    | Gündüz      | Giden  | x 1,00  |
| Hafta Sonu    | akşam acele | gelen   | x 1,00  |
| Hafta Sonu    | akşam acele | Giden  | x 1,00  |
| Hafta Sonu    | Gece    | gelen   | x 1,00  |
| Hafta Sonu    | Gece    | Giden  | x 1,00  |

Üç değişkenin 16 farklı kombinasyonu vardır. Bazı koşulları birleştirerek, son geçiş ifadesini basitleştirirsiniz.

Geçiş ücretlerini toplayan sistem, <xref:System.DateTime> geçiş ücretinin toplandığı zaman için bir yapı kullanır. Önceki tablodaki değişkenleri oluşturan üye yöntemler oluşturun. Aşağıdaki işlev, bir <xref:System.DateTime> hafta sonunu mu yoksa hafta içi mi temsil etmediğini ifade etmek için bir desen eşleştirme anahtarı ifadesi kullanır:

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

Bu yöntem işe yarıyor, ama tekrarediyor. Aşağıdaki kodda gösterildiği gibi basitleştirebilirsiniz:

[!code-csharp[IsWeekDay](~/samples/snippets/csharp/tutorials/patterns/finished/toll-calculator/TollCalculator.cs#IsWeekDay)]

Ardından, zaman bloklar içine kategorize etmek için benzer bir işlev ekleyin:

[!code-csharp[GetTimeBand](~/samples/snippets/csharp/tutorials/patterns/finished/toll-calculator/TollCalculator.cs#GetTimeBand)]

Önceki yöntem desen eşleştirme kullanmaz. Tanıdık bir `if` dizi ifade kullanarak daha açık. Her zaman aralığını ayrı bir `enum` değere dönüştürmek için özel bir ürün eklersiniz.

Bu yöntemleri oluşturduktan sonra, `switch` fiyatlandırma primini hesaplamak için **tuple deseni** olan başka bir ifade kullanabilirsiniz. 16 kolu `switch` yla bir ifade oluşturabilirsiniz:

[!code-csharp[FullTuplePattern](~/samples/snippets/csharp/tutorials/patterns/finished/toll-calculator/TollCalculator.cs#TuplePatternOne)]

Yukarıdaki kod çalışır, ancak basitleştirilmiş olabilir. Hafta sonu için tüm sekiz kombinasyonları aynı geçiş ücreti var. Sekizini de aşağıdaki satırla değiştirebilirsiniz:

```csharp
(false, _, _) => 1.0m,
```

Hem gelen hem de giden trafik hafta içi gündüz ve gece saatlerinde aynı çarpana sahiptir. Bu dört anahtar kolu aşağıdaki iki satırla değiştirilebilir:

```csharp
(true, TimeBand.Overnight, _) => 0.75m,
(true, TimeBand.Daytime, _)   => 1.5m,
```

Kod, bu iki değişiklikten sonra aşağıdaki kod gibi görünmelidir:

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

Son olarak, normal fiyatı ödeyen iki acele saat zaman kaldırabilirsiniz. Bu kolları çıkardıktan sonra, `false` son anahtar`_`kolundaki bir atma ( ) ile değiştirebilirsiniz. Aşağıdaki bitmiş yönteme sahip olacaksınız:

[!code-csharp[SimplifiedTuplePattern](../../../samples/snippets/csharp/tutorials/patterns/finished/toll-calculator/TollCalculator.cs#FinalTuplePattern)]

Bu örnek, desen eşleştirmenin avantajlarından birini vurgular: desen dalları sırayla değerlendirilir. Önceki bir şubenin sonraki durumlarından birini işlemesi için bunları yeniden düzenlerseniz, derleyici erişilemez kod hakkında sizi uyarır. Bu dil kuralları, önceki basitleştirmeleri kodun değişmediği konusunda güvenle yapmayı kolaylaştırdı.

Desen eşleştirme, bazı kod türlerini daha okunabilir hale getirir ve sınıflarınıza kod ekleyemediğınızda nesne yönelimli tekniklere alternatif sunar. Bulut, verilerin ve işlevselliğin birbirinden ayrılmasına neden oluyor. Verilerin *şekli* ve üzerindeki *işlemler* birlikte açıklanmaz. Bu eğitimde, varolan verileri özgün işlevinden tamamen farklı şekillerde tükettin. Desen eşleştirme, bu türleri genişletemeseniz bile, bu türleri geçersiz kılması gereken işlevsellik yazma olanağı sağlar.

## <a name="next-steps"></a>Sonraki adımlar

Bitmiş kodu [dotnet/samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/patterns/finished) GitHub deposundan indirebilirsiniz. Desenleri kendi gözlerinize ekleyin ve bu tekniği düzenli kodlama etkinliklerinize ekleyin. Bu teknikleri öğrenmek, sorunlara yaklaşmanız ve yeni işlevler oluşturmanız için başka bir yol sağlar.
