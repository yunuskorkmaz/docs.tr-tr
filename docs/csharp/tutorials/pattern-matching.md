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
# <a name="tutorial-using-pattern-matching-features-to-extend-data-types"></a>Öğretici: Veri türlerini genişletmek için özellikler desen kullanma

C#7 özellikleri temel desen kullanıma sunuldu. Bu özellikler, Genişletilmiş C# yeni ifadeleri ve desenleriyle 8. Diğer kitaplıkları olabilecek türler genişletilmiş olarak gibi davranır işlevselliği yazabilirsiniz. Başka bir kullanım desenleri için temel bir özelliği Genişletilmekte olan türü değil, uygulamanızın gerektirdiği işlevselliği oluşturmaktır.

Bu öğreticide şunları öğrenirsiniz nasıl yapılır:

> [!div class="checklist"]
> * Desen eşleştirme burada kullanılması gereken durumları algılar.
> * Desen eşleştirme ifadelerinde, türleri ve özellik değerlerine göre davranışı uygulamak için kullanın.
> * Desen eşleştirme tam algoritmalar oluşturmak için diğer teknikleri ile birleştirin.

## <a name="prerequisites"></a>Önkoşullar

.NET Core çalıştırmak için makinenizi ayarlamak ihtiyacınız olacak dahil olmak üzere C# 8.0 Önizleme derleyici. C# 8 preview derleyici en son kullanılabilir [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019), veya en son [.NET Core 3.0 Önizleme](https://dotnet.microsoft.com/download/dotnet-core/3.0).

Bu öğreticide, aşina olduğunuz varsayılır C# ve .NET, Visual Studio veya .NET Core CLI gibi.

## <a name="scenarios-for-pattern-matching"></a>Desen eşleştirme senaryoları

Modern geliştirme genellikle birden çok kaynaktan veri tümleştirme ve bilgi ve bu verilerden Öngörüler elde cohesive tek bir uygulama içinde sunma içerir. Size ve ekibinize denetim veya gelen verilerini temsil eden tüm türleri için erişimi olmaz.

Uygulamanızdaki her veri türü bu birden çok veri kaynağından temsil eden türleri oluşturmak için Klasik nesne yönelimli tasarım çağırırsınız. Ardından, uygulamanızı bu yeni türleriyle çalışır, devralma Hiyerarşiler, sanal yöntemler oluşturmak ve soyutlama uygulamak. En iyi Araçlar bazen olduklarını ve bu teknikler çalışır. Bazen daha az kod yazabilirsiniz. Veriler, veri işleme işlemlerinden ayıran teknikleri kullanarak daha fazla kod yazabilirsiniz.

Bu öğreticide, oluşturun ve tek bir senaryo için çeşitli dış kaynaklardan gelen verileri alan bir uygulama keşfedin. Göreceğiniz nasıl **desen eşleştirme** kullanır ve bu verileri özgün sisteminin bir parçası olmayan bir şekilde işlemek için etkili bir yol sağlar.

Trafiği yönetmek için ücretli geçişler ve en yüksek süre fiyatlandırma kullanarak büyük bir metropol alanı göz önünde bulundurun. Ücretli geçişler için bir araç kendi türüne göre hesaplayan bir uygulaması yazma. Sonraki geliştirmeleri occupants araç içinde sayısına bağlı fiyatlandırma dahil edilip derecelendirilir. Başka bir geliştirme, saat ve haftanın günü göre fiyatlandırma ekleyin.

Bu kısa açıklamasından, hızlı bir şekilde bu sistem modeli için bir nesne hiyerarşisine ince ince. Bununla birlikte, verilerinizi diğer araç kayıt yönetim sistemleri gibi birden çok kaynaktan geliyor. Bu sistemler, veri modeli için farklı sınıfları sağlar ve bir tek nesne modeli kullandığınız yok. Bu öğreticide, bu dış sistemlerden vehicle veri modeli için aşağıdaki kodda gösterildiği gibi bu Basitleştirilmiş sınıfların kullanacaksınız:

[!code-csharp[ExternalSystems](~/samples/csharp/tutorials/patterns/start/toll-calculator/ExternalSystems.cs)]

Başlatıcı kodu indirebileceğiniz [dotnet/samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/patterns/start) GitHub deposu. Araç sınıfları farklı sistemlerden ve farklı ad alanlarında, görebilirsiniz. Dışındaki hiçbir ortak bir taban sınıf `System.Object` yararlanılabilir.

## <a name="pattern-matching-designs"></a>Desen eşleştirme tasarımları

Bu öğretici vurguların kullanılan senaryo tür desen eşleştirme sorunları çözmek için uygundur:

- Çalışmanız için gereken nesneleri hedeflerinizi karşılayan bir nesne hiyerarşisine değildir. İlişkisiz sistemleri parçası olan sınıfları ile çalışıyor.
- Ekliyorsunuz işlevselliği, bu sınıflar için temel Özet bir parçası değildir. Ücretli bir araç tarafından ödenen *değişiklikleri* vehicle çekirdek işlevi araçları, ancak Ücretli farklı türde değil.

Zaman *şekli* verilerin ve *işlemleri* üzerinde veri değil açıklanacak olan birlikte özelliklerinde desen C# çalışmak daha kolay hale getirmek.

## <a name="implement-the-basic-toll-calculations"></a>Temel Ücretli hesaplamalar uygulayın

En temel Ücret hesaplama vehicle türüne bağlıdır:

- A `Car` 2,00 olduğu.
- A `Taxi` $3.50 olduğu.
- A `Bus` 5,00 $ ise.
- A `DeliveryTruck` $10,00 olduğu

Yeni bir `TollCalculator` sınıfı ve ücret tutarı almak için araç türüne desen uygulayın. Aşağıdaki kod ilk uygulamasını gösterir `TollCalculator`.

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

Önceki kod bir **geçiş ifadesi** (aynı bir [ `switch` ](../language-reference/keywords/switch.md) deyimi) kullanan testlerin **türü deseni**. A **geçiş ifadesi** değişkeniyle başlar `vehicle` önceki kodda, arkasından `switch` anahtar sözcüğü. Sonraki tüm gelen **geçiş Silah** küme ayraçlarının içindeki. `switch` İfade çevreleyen sözdizimine diğer iyileştirme yapar `switch` deyimi. `case` Anahtar sözcüğü atlanırsa ve her bir arm sonucunu bir ifadedir. Son iki Silah yeni bir dil özelliği gösterir. `{ }` Çalışması eşleşen bir önceki arm eşleşmedi herhangi bir null olmayan nesne. Bu arm bu yönteme geçirilen yanlış türler yakalar.  `{ }` Çalışması, her bir araç türü durumlarda izlemelidir. Sırasını tersine çevrilmiş, `{ }` çalışması önceliklidir. Son olarak, `null` algılar deseni bir `null` bu yönteme iletilir. `null` Deseni bir türü desenleri yalnızca null olmayan bir nesne doğru türde olduğundan son olabilir.

Aşağıdaki kodu kullanarak bu kodu test edebilirsiniz `Program.cs`:

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

Bu kod, başlangıç projesine dahil, ancak devre dışı bırakılmışsa. Açıklamaları kaldırma ve yazdıklarınızı test edebilirsiniz.

Desenler, kod ve verileri ayrı olduğu algoritmaları oluşturmanıza nasıl yardımcı olabileceğini görmek başlatılıyor. `switch` İfade türü test eder ve sonuçlarına bağlı olarak farklı değerlere üretir. Bu yalnızca başlangıç adımıdır.

## <a name="add-occupancy-pricing"></a>Sahiplik fiyatlandırma Ekle

Maksimum kapasitede her fırsatta seyahat etmeye taşıtlardan teşvik etmek Ücretli yetkilisi istiyor. Araçlar daha az Yolcuların varsa ve daha düşük fiyatlandırma sunarak tam taşıtlardan teşvik daha kaydedilecek verdiyseniz:

- Arabalar ve taksiler hiçbir Yolcuların ile bir ek 0,50 ABD Doları ücret ödersiniz.
- Arabalar ve iki Yolcuların ile taksiler 0,50 indirim elde edin.
- Arabalar ve üç veya daha fazla Yolcuların ile taksiler 1,00 indirim elde edin.
- Değerinden % 50 tam yolları 2,00 fazladan bir ücret ödersiniz.
- Birden fazla % 90 tam olan yollarına 1,00 indirim alın.

Bu kurallar kullanılarak uygulanır **özelliği desenini** aynı ifade geçin. Türü belirlendikten sonra özelliği düzeni nesnenin özelliklerini inceler. Tek bir kasada bir `Car` dört farklı çalışmalarına genişletir:

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

İlk üç çalışmalarını test türü olarak bir `Car`, ardından değerini kontrol `Passengers` özelliği. Her ikisi de eşleşirse, ifade değerlendirilir ve döndürdü.

Benzer şekilde taksiler durumlarda da genişletin:

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

Önceki örnekte `when` son talebinde yan tümcesi çıkarılsaydı.

Ardından, sahiplik kuralları veri yolları durumlarda genişleterek aşağıdaki örnekte gösterildiği gibi uygulayın:

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

Ücretli yetkilisi yolcu teslimi kamyon içinde sayısı ile ilgili değildir. Bunun yerine, bunlar daha kamyon ağırlık sınıfında göre ücret alınır. Kamyon 5000 lbs üzerinde fazladan bir $5.00 ücretlendirilir. Açık kamyon altında 3000 lbs 2,00 fiyatla sunulur. Bu kural, aşağıdaki kod ile gerçekleştirilir:

```csharp
vehicle switch
{
    // ...

    DeliveryTruck t when (t.GrossWeightClass > 5000) => 10.00m + 5.00m,
    DeliveryTruck t when (t.GrossWeightClass < 3000) => 10.00m - 2.00m,
    DeliveryTruck t => 10.00m,
};
```

Önceki kodun gösterdiği `when` anahtar arm yan tümcesi. Kullandığınız `when` özellikte eşitlik dışındaki koşulları test etmeye yönelik yan tümcesi. İşiniz bittiğinde, aşağıdaki gibi görünen bir yöntem sahip olacaksınız:

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

Bunların çoğu Silah geçiş örnekler **özyinelemeli desenleri**. Örneğin, `Car { Passengers: 1}` özelliği desenini içinde sabit bir deseni gösterir.

İç içe geçmiş anahtarlarını kullanarak bu kodu daha az tekrarlı yapabilirsiniz. `Car` Ve `Taxi` her ikisi de Yukarıdaki örneklerde dört farklı Silah sahiptir. Her iki durumda da, bir özellik modele akışları bir tür deseni oluşturabilirsiniz. Bu teknik, aşağıdaki kodda gösterilmiştir:

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

Yukarıdaki örnekte, özyinelemeli ifadesi kullanarak yoksa yineleyin anlamına gelir `Car` ve `Taxi` içeren özellik değeri test alt Silah Silah. Bu yöntem için kullanılmayan `Bus` ve `DeliveryTruck` bu Silah aralıkları özelliği değil ayrık değerler için test çünkü etkinleştirme.

## <a name="add-peak-pricing"></a>En yüksek fiyatlandırma Ekle

Son bir özellik için ücretli yetkilisi hassas en yüksek süre fiyatlandırma eklemek istiyor. Ücretli geçişler iki katına sabah ve akşam yoğun saatler sırasında. Bu kural yalnızca bir yöndeki trafiği etkiler: sabah şehirde gelen ve giden Akşam sağladığından saat içinde. Workday sırasında diğer zamanlarda, ücretli geçişler % 50'ye yükseltin. Gece geç ve erken sabah, ücretli geçişler 25 oranında azalır. Normal fiyat, saat bakılmaksızın olduğu tarihlerinde.

Bu özellik için desen kullanacağız ancak bunu diğer teknikleri ile tümleştirmeniz. Hesap yön tüm bileşimleri, haftanın günü ve saat için bir tek desen eşleştirme ifadesi oluşturabilirsiniz. Sonuç, karmaşık bir ifadeyi olur. Okunmasını ve anlaşılması zor olacaktır. Doğruluk emin olmak zorlaştırır. Bunun yerine, tüm eyaletler kısaca açıklayan bir demet değerler oluşturmak için bu yöntemleri birleştirin. Ardından Ücretli çarpanı hesaplamak için desen eşleştirme kullanın. Tanımlama grubu üç farklı koşullar içeriyor:

- , Bir hafta içi gün veya hafta günüdür.
- Zaman zaman Ücretli toplandıktan bant.
- Şehir veya şehir dışında yönüdür

Aşağıdaki tabloda, giriş değerleri birleşimlerini ve çarpan fiyatlandırma yoğun gösterilmektedir:

| Gün        | Zaman         | Yön | Premium |
| ---------- | ------------ | --------- |--------:|
| Haftanın günü    | sabah sağladığından | Gelen   | 2,00 x  |
| Haftanın günü    | sabah sağladığından | Giden  | 1,00 x  |
| Haftanın günü    | Daytime      | Gelen   | 1.50 x  |
| Haftanın günü    | Daytime      | Giden  | 1.50 x  |
| Haftanın günü    | Akşam sağladığından | Gelen   | 1,00 x  |
| Haftanın günü    | Akşam sağladığından | Giden  | 2,00 x  |
| Haftanın günü    | gece    | Gelen   | 0,75 x  |
| Haftanın günü    | gece    | Giden  | 0,75 x  |
| Hafta sonu    | sabah sağladığından | Gelen   | 1,00 x  |
| Hafta sonu    | sabah sağladığından | Giden  | 1,00 x  |
| Hafta sonu    | Daytime      | Gelen   | 1,00 x  |
| Hafta sonu    | Daytime      | Giden  | 1,00 x  |
| Hafta sonu    | Akşam sağladığından | Gelen   | 1,00 x  |
| Hafta sonu    | Akşam sağladığından | Giden  | 1,00 x  |
| Hafta sonu    | gece    | Gelen   | 1,00 x  |
| Hafta sonu    | gece    | Giden  | 1,00 x  |

Üç değişkenin 16 farklı birleşimlerini vardır. Bazı koşullar birleştirerek son switch ifadesi basitleştireceğiz.

Ücretli geçişler toplayan sistem kullanan bir <xref:System.DateTime> zaman Ücretli toplanmıştır kez yapısı. Önceki tabloda değişkenlerinin üye yöntemleri oluşturun. Aşağıdaki işlev express için switch ifadesi bir desen kullanır. olup olmadığını bir <xref:System.DateTime> hafta veya bir iş günü temsil eder:

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

Bu yöntem çalışır, ancak tekrarlayan. Aşağıdaki kodda gösterildiği gibi basitleştirebilirsiniz:

[!code-csharp[IsWeekDay](~/samples/csharp/tutorials/patterns/finished/toll-calculator/TollCalculator.cs#IsWeekDay)]

Ardından, bloklarda süreyi kategorilere ayıran bir benzer işlevi ekleyin:

[!code-csharp[GetTimeBand](~/samples/csharp/tutorials/patterns/finished/toll-calculator/TollCalculator.cs#GetTimeBand)]

Desen eşleştirme yönteminin kullanmaz. Tanıdık bir cascade birini kullanarak nettir `if` deyimleri. Özel bir ekleme `enum` her zaman aralığı bir ayrık değere dönüştürülecek.

Bu yöntemleri oluşturduktan sonra başka kullanabilirsiniz `switch` ifadesiyle **kayıt düzeni deseni** fiyatlandırma premium hesaplamak için. Derleme bir `switch` 16 kollu ifade:

[!code-csharp[FullTuplePattern](~/samples/csharp/tutorials/patterns/finished/toll-calculator/TollCalculator.cs#TuplePatternOne)]

Yukarıdaki kodu çalışır, ancak Basitleştirilmiş. Tüm sekiz hafta birleşimlerini aynı Ücretli vardır. Tüm sekiz aşağıdaki satırı ile değiştirebilirsiniz:

```csharp
(false, _, _) => 1.0m,
```

Gelen ve giden trafiği, ertesi gün saat ve haftanın günü daytime sırasında aynı çarpan vardır. Bu dört anahtar Silah aşağıdaki iki satır ile değiştirilebilir:

```csharp
(true, TimeBand.Overnight, _) => 0.75m,
(true, TimeBand.Daytime, _)   => 1.5m,
```

Kod, sonra bu iki değişikliği şu kod gibi görünmelidir:

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

Son olarak, normal ücretini ödemem saat kez iki sağladığından kaldırabilirsiniz. Bu Silah kaldırdıktan sonra değiştirebileceğiniz `false` bir atma ile (`_`) son anahtar arm içinde. Aşağıdaki tamamlanmış yöntemi vardır:

[!code-csharp[SimplifiedTuplePattern](../../../samples/csharp/tutorials/patterns/finished/toll-calculator/TollCalculator.cs#FinalTuplePattern)]

Bu örnek bir desen eşleştirme avantajlarını vurgular: Düzen dalları sırayla değerlendirilir. Önceki bir dalı, sonraki durumlarından biri işler, böylece bunları yeniden düzenlerseniz, derleyici, erişilemeyen kod hakkında sizi uyarır. Bu dil kuralları önceki basitleştirme kod değişmedi güvenle yapmak daha kolay yapılır.

Desen eşleştirme, bazı türleri kod daha okunabilir hale getirir ve sınıflarınızı için kod eklenemiyor, teknikleri nesne yönelimli bir alternatif sunar. Bulut, veri ve İşlevler parçalayın Canlı neden oluyor. *Şekli* verilerin ve *işlemleri* açık olmayan mutlaka anlatılan birlikte. Bu öğreticide, kendi özgün işlevden tamamen farklı şekillerde mevcut verilerini kullandınız. Desen eşleştirme genişletmek uygulanamadı olsa da bu türlerin geçersiz kılınmış işlevselliği yazma olanağı getirdi.

## <a name="next-steps"></a>Sonraki adımlar

Tamamlanan kodu indirebileceğiniz [dotnet/samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/patterns/finished) GitHub deposu. Desenler kendiniz keşfedin ve bu tekniği normal kodlama etkinliklerinizi ekleyebilirsiniz. Bu teknikler öğrenme, sorunları yaklaşımını ve yeni işlevler oluşturmak için başka bir yol sunar.
