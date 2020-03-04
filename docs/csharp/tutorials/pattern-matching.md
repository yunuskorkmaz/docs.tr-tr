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
# <a name="tutorial-using-pattern-matching-features-to-extend-data-types"></a>Öğretici: veri türlerini genişletmek için model eşleştirme özelliklerini kullanma

C#7 temel desenler eşleşen özellikler sunmuştur. Bu özellikler yeni ifadelerle ve C# desenlerle 8 ' de genişletilir. Başka kitaplıklarda olabilecek türleri genişletmekle birlikte davranan işlevselliği yazabilirsiniz. Desenler için başka bir kullanım, uygulamanızın genişletilmekte olan türün temel bir özelliği olmayan bir işlev oluşturmasını gerektirir.

Bu öğreticide şunların nasıl yapıldığını öğreneceksiniz:

> [!div class="checklist"]
>
> - Model eşleştirmesinin kullanılması gereken durumları tanıyın.
> - Türleri ve özellik değerlerini temel alan davranışı uygulamak için kalıp eşleştirme ifadelerini kullanın.
> - Tüm algoritmalar oluşturmak için model eşleştirmeyi diğer tekniklerle birleştirin.

## <a name="prerequisites"></a>Önkoşullar

Makinenizi, C# 8,0 derleyicisi dahil .NET Core çalıştıracak şekilde ayarlamanız gerekir. 8 C# derleyicisi, [Visual Studio 2019 sürüm 16,3](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) veya [.NET Core 3,0 SDK](https://dotnet.microsoft.com/download)ile başlayarak kullanılabilir.

Bu öğreticide, Visual Studio veya C# .NET Core CLI dahil olmak üzere, .net hakkında bilgi sahibi olduğunuz varsayılır.

## <a name="scenarios-for-pattern-matching"></a>Model eşleştirme senaryoları

Modern geliştirme genellikle birden çok kaynaktaki verilerin tümleştirilmesine ve bu verilerden tek bir ortak uygulamada bilgi ve Öngörüler sunmaya dahildir. Siz ve takımınız gelen verileri temsil eden tüm türler için denetime veya erişime sahip olmayacaktır.

Klasik nesne odaklı tasarım, uygulamanızda, bu birden çok veri kaynağından her bir veri türünü temsil eden türler oluşturmak için çağrı yapılır. Daha sonra uygulamanız bu yeni türlerle çalışarak devralma hiyerarşileri oluşturun, sanal yöntemler oluşturur ve soyutlamalar uygular. Bu teknikler çalışır ve bazen en iyi araçlardır. Diğer zamanlarda da daha az kod yazabilirsiniz. Verileri işleyen işlemlerden verileri ayıran teknikleri kullanarak daha fazla şifresiz kod yazabilirsiniz.

Bu öğreticide, tek bir senaryo için çeşitli dış kaynaklardan gelen verileri alan bir uygulama oluşturacaksınız ve keşfedeceğiz. **Düzenin** , bu verileri özgün sistemin parçası olmayan yollarla tüketmek ve işlemek için etkili bir yol sağladığını görürsünüz.

Trafiği yönetmek için Tolls ve yoğun zaman fiyatlandırması kullanan bir ana metropol alanı düşünün. Türüne göre bir araç için Tolls 'yi hesaplayan bir uygulama yazarsınız. Daha sonraki geliştirmeler, araç çubuğundaki alan sayısına göre fiyatlandırmaya dahil değildir. Daha fazla geliştirmeler, haftanın saatine ve gününe göre fiyatlandırma ekler.

Bu kısa açıklamadan, bu sistemi modellemek için bir nesne hiyerarşisinde hızlıca taslak oluşturabilirsiniz. Ancak, verileriniz diğer araç kayıt yönetimi sistemleri gibi birden çok kaynaktan geliyor. Bu sistemler, verileri modellemek için farklı sınıflar sağlar ve kullanabileceğiniz tek bir nesne modeli yoktur. Bu öğreticide, aşağıdaki kodda gösterildiği gibi bu dış sistemlerden araç verilerini modellemek için bu Basitleştirilmiş sınıfları kullanacaksınız:

[!code-csharp[ExternalSystems](~/samples/snippets/csharp/tutorials/patterns/start/toll-calculator/ExternalSystems.cs)]

Başlangıç kodunu [DotNet/Samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/patterns/start) GitHub deposundan indirebilirsiniz. Araç sınıflarının farklı sistemlerden olduğunu ve farklı ad alanlarında olduğunu görebilirsiniz. `System.Object` dışındaki ortak bir temel sınıf yararlanılabilir olabilir.

## <a name="pattern-matching-designs"></a>Desen eşleştirme tasarımları

Bu öğreticide kullanılan senaryo, düzenin eşleşmesi için uygun olan sorun türlerini vurgular:

- Çalışmanız gereken nesneler, hedeflerinizle eşleşen bir nesne hiyerarşisinde değildir. İlişkisiz sistemlerin parçası olan sınıflarla çalışıyor olabilirsiniz.
- Eklemekte olduğunuz işlevsellik, bu sınıfların temel soyutlama kapsamında değildir. Bir araç tarafından ücretli bir araç, farklı araç türlerine göre *değişir* ancak ücretli bir temel işlev değildir.

Verilerin *şekli* ve bu verilerdeki *işlemler* birlikte açıklanmadığında, ' deki C# model eşleme özellikleri ile çalışmayı kolaylaştırır.

## <a name="implement-the-basic-toll-calculations"></a>Temel ücretli hesaplamaları uygulayın

En temel ücretli hesaplama yalnızca araç türüne bağlıdır:

- `Car` $2,00 ' dir.
- `Taxi` $3,50 ' dir.
- `Bus` $5,00 ' dir.
- `DeliveryTruck` $10,00

Yeni bir `TollCalculator` sınıfı oluşturun ve ücretli miktarı almak için araç türünde kalıp eşleştirmeyi uygulayın. Aşağıdaki kod `TollCalculator`ilk uygulamasını gösterir.

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

Yukarıdaki kod, **tür modelini**test eden bir **switch ifadesi** (bir [`switch`](../language-reference/keywords/switch.md) ifadesiyle aynı değildir) kullanır. Bir **switch ifadesi** , önceki kodda `vehicle` ve ardından `switch` anahtar sözcüğü ile başlar. Ardından, küme ayraçları içindeki tüm **anahtar kolları** gelir. `switch` ifadesi, `switch` deyimini çevreleyen söz dizimi için diğer işlevselliklerindeki yapar. `case` anahtar sözcüğü atlanır ve her bir ARM 'nin sonucu bir ifadedir. Son iki kolonun yeni bir dil özelliği gösterir. `{ }` Case, önceki bir ARM ile eşleşmeyen null olmayan tüm nesneler ile eşleşir. Bu ARM, bu yönteme geçirilen hatalı türleri yakalar.  `{ }` durum, her bir araç türü için durumları izlemelidir. Sıra tersine çevrilirse, `{ }` durumu öncelik kazanır. Son olarak, `null` deseninin bu yönteme bir `null` geçtiğini algılar. Diğer tür desenleri doğru türdeki yalnızca null olmayan bir nesneyle eşleştiğinden `null` deseni son olabilir.

`Program.cs`' de aşağıdaki kodu kullanarak bu kodu test edebilirsiniz:

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

Bu kod, başlatıcı projesine dahil edilmiştir, ancak açıklama eklenir. Açıklamaları kaldırın ve ne yazdığınızı test edebilirsiniz.

Desenlerin kodun ve verilerin ayrı olduğu algoritmalar oluşturmanıza nasıl yardımcı olduğunu görmeyi başlıyoruz. `switch` ifade, türü sınar ve sonuçlara göre farklı değerler üretir. Bu yalnızca başlangıç amaçlıdır.

## <a name="add-occupancy-pricing"></a>İskan fiyatlandırması Ekle

Ücretli yetkili, en yüksek kapasiteden gezilerin gezmelerini teşvik etmek istiyor. Araçlar daha az pastlar olduğunda daha fazla ücret ödemelerine ve daha düşük fiyatlandırma sunarak tam bir şekilde teşvik etmeye karar vermiştir:

- Otomobiller ve Tax, hiçbir Pasca, ek $0,50 ödeyebilir.
- Otomobiller ve Tax, iki pasa, $0,50 indirimi alır.
- Üç veya daha fazla Pascal ile otomobiller ve Tax, $1,00 indirimi alır.
- %50 ' den küçük veri yolları, fazladan $2,00 oranında ödeyin.
- %90 ' den fazla tam veri yolları $1,00 indirimi elde edin.

Bu kurallar, aynı anahtar ifadesinde **özellik düzeniyle** kullanılarak uygulanabilir. Özellik deseninin türü belirlendikten sonra nesnenin özellikleri incelenir. `Car` için tek durum dört farklı durumda genişler:

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

İlk üç durum türü `Car`olarak test edin ve sonra `Passengers` özelliğinin değerini denetleyin. Her ikisi de eşleşiyorsa, bu ifade değerlendirilir ve döndürülür.

Ayrıca, taxiçin de benzer bir şekilde durum da genişletebilirsiniz:

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

Yukarıdaki örnekte, son durumda `when` yan tümcesi atlandı.

Ardından, aşağıdaki örnekte gösterildiği gibi, veri yolları için durumları genişleterek sahiplik kurallarını uygulayın:

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

Ücretli yetkili, teslim kamyonları içindeki pastıcılar sayısıyla ilgilenmez. Bunun yerine, aşağıdaki gibi, kamyonlar ağırlık sınıfına göre ücretli miktarı ayarlar:

- 5000 lbs üzerinde structuralks, fazladan $5,00 ücretlendirilir.
- 3000 lbs kapsamında hafif bir $2,00 indirimi verilir.

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

Yukarıdaki kod, anahtar ARM 'nin `when` yan tümcesini gösterir. Bir özellikte eşitlik dışındaki koşulları test etmek için `when` yan tümcesini kullanırsınız. İşiniz bittiğinde aşağıdakine benzer bir yönteme sahip olacaksınız:

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

Bu anahtar kolları çoğu **özyinelemeli desenlere**örnektir. Örneğin `Car { Passengers: 1}`, bir özellik deseninin içinde sabit bir model gösterir.

İç içe geçmiş anahtarlar kullanarak bu kodu daha az tekrarlı hale getirebilirsiniz. `Car` ve `Taxi` her ikisi de önceki örneklerde dört farklı kollu bir sahiptir. Her iki durumda da, bir özellik düzeninde akışlara bir tür stili oluşturabilirsiniz. Bu teknik aşağıdaki kodda gösterilmiştir:

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

Önceki örnekte, özyinelemeli bir ifade kullanılması, özellik değerini test eden alt kolları içeren `Car` ve `Taxi` kolları yinelemediğiniz anlamına gelir. Bu özellikler, `Bus` ve `DeliveryTruck` kolları için kullanılmaz, çünkü bu Koller özellik için aralıkları test ettiğinden ayrık değerler değildir.

## <a name="add-peak-pricing"></a>Tepe fiyatlandırması Ekle

Son özellik için, ücretli yetkili zamana duyarlı tepe fiyatlandırması eklemek istemektedir. Sabah ve akşam aceleniz saatlerinde, Tolls iki katına çıkar. Bu kural yalnızca bir yönde trafiği etkiler: sabah şehrine gelen ve akşam aceleniz Hour 'daki çıkış. İş gününde diğer saatlerde, Tolls %50 oranında artar. Geç gece ve erken sabah, Tolls %25 oranında azaltılır. Hafta sonu sırasında, zamandan bağımsız olarak normal fiyat olur.

Bu özellik için model eşleştirmeyi kullanacaksınız, ancak diğer tekniklerle tümleştirilecek. Tüm yön, hafta günü ve saat birleşimleri için hesap oluşturacak tek bir kalıp eşleştirme ifadesi oluşturabilirsiniz. Sonuç karmaşık bir ifade olacaktır. Okunması zor olabilir. Bu, doğruluğu garanti etmelerini zorlaştırır. Bunun yerine, öz 'in tüm bu durumları açıkladığı bir dizi değer oluşturmak için bu yöntemleri birleştirin. Ardından, ücretli bir çarpanı hesaplamak için model eşleştirmeyi kullanın. Kayıt düzeni üç farklı koşul içerir:

- Gün, bir hafta içi veya bir hafta sonu olabilir.
- Ücretli sürenin toplanacağı zaman bandı.
- Yön City veya City 'den

Aşağıdaki tabloda, giriş değerleri ve en yüksek fiyatlandırma çarpanı birleşimleri gösterilmektedir:

| Gün        | Zaman         | Yön | Premium |
| ---------- | ------------ | --------- |--------:|
| HAFTANINGÜNÜ    | sabah aceleniz | gelen   | x 2,00  |
| HAFTANINGÜNÜ    | sabah aceleniz | giden  | x 1,00  |
| HAFTANINGÜNÜ    | saati      | gelen   | x 1,50  |
| HAFTANINGÜNÜ    | saati      | giden  | x 1,50  |
| HAFTANINGÜNÜ    | akşam aceleniz | gelen   | x 1,00  |
| HAFTANINGÜNÜ    | akşam aceleniz | giden  | x 2,00  |
| HAFTANINGÜNÜ    | gece    | gelen   | x 0,75  |
| HAFTANINGÜNÜ    | gece    | giden  | x 0,75  |
| Hafta    | sabah aceleniz | gelen   | x 1,00  |
| Hafta    | sabah aceleniz | giden  | x 1,00  |
| Hafta    | saati      | gelen   | x 1,00  |
| Hafta    | saati      | giden  | x 1,00  |
| Hafta    | akşam aceleniz | gelen   | x 1,00  |
| Hafta    | akşam aceleniz | giden  | x 1,00  |
| Hafta    | gece    | gelen   | x 1,00  |
| Hafta    | gece    | giden  | x 1,00  |

Üç değişkenin 16 farklı birleşimi vardır. Bazı koşulları birleştirerek son anahtar ifadesini basitleştirirsiniz.

Tolls 'yi toplayan sistem, ücretli bir süre için <xref:System.DateTime> yapısını kullanır. Yukarıdaki tablodan değişkenleri oluşturan üye yöntemleri oluşturun. Aşağıdaki işlev bir <xref:System.DateTime> hafta sonu veya haftanın gününü temsil edip etmediğini ifade etmek için bir model eşleştirme anahtar ifadesi kullanır:

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

Bu yöntem işe yarar, ancak repetitious. Aşağıdaki kodda gösterildiği gibi basitleşebilir:

[!code-csharp[IsWeekDay](~/samples/snippets/csharp/tutorials/patterns/finished/toll-calculator/TollCalculator.cs#IsWeekDay)]

Sonra, zaman bloklara zaman kategorize etmek için benzer bir işlev ekleyin:

[!code-csharp[GetTimeBand](~/samples/snippets/csharp/tutorials/patterns/finished/toll-calculator/TollCalculator.cs#GetTimeBand)]

Önceki yöntem, model eşleştirme kullanmaz. `if` deyimleri tanıdık bir basamakla daha net. Her zaman aralığını ayrı bir değere dönüştürmek için özel bir `enum` eklersiniz.

Bu yöntemleri oluşturduktan sonra, fiyatlandırma Premium 'u hesaplamak için **tanımlama grubu düzeniyle** başka bir `switch` ifadesini kullanabilirsiniz. Tüm 16 kollu bir `switch` ifadesi oluşturabilirsiniz:

[!code-csharp[FullTuplePattern](~/samples/snippets/csharp/tutorials/patterns/finished/toll-calculator/TollCalculator.cs#TuplePatternOne)]

Yukarıdaki kod işe yarar, ancak basitleştirilebilir. Hafta sonu için sekiz kombinasyonun hepsi de aynı ücretli bir. Tüm sekiz değerini aşağıdaki satırla değiştirebilirsiniz:

```csharp
(false, _, _) => 1.0m,
```

Hem gelen hem de giden trafik, hafta içi gündüz ve gece saatlerinde aynı katkılar. Bu dört anahtar kolları aşağıdaki iki satır ile değiştirilebilir:

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

Son olarak, normal fiyatı ödeyerek iki aceleniz saatlik saati kaldırabilirsiniz. Bu kolları kaldırdıktan sonra, `false` son anahtar ARM içindeki bir atma (`_`) ile değiştirebilirsiniz. Aşağıdaki tamamlanmış yönteme sahip olacaksınız:

[!code-csharp[SimplifiedTuplePattern](../../../samples/snippets/csharp/tutorials/patterns/finished/toll-calculator/TollCalculator.cs#FinalTuplePattern)]

Bu örnek, düzen eşleştirmesinin avantajlarından birini vurgular: düzen dalları sırayla değerlendirilir. Daha önceki bir dalın daha sonraki durumlardan birini işleyeceği şekilde yeniden ayarlarsanız, derleyici ulaşılamaz kod hakkında sizi uyarır. Bu dil kuralları, önceki basitleştirmeleri kodun değiştirmiyordu güvenle daha kolay hale getirir.

Model eşleştirme bazı kod türlerini daha okunaklı hale getirir ve sınıflarınıza kod ekleyemadığınızda nesne odaklı teknikler için bir alternatif sağlar. Bulut, verilerin ve işlevlerin canlı olmasına neden oluyor. Verilerin *şekli* ve üzerindeki *işlemler* birlikte açıklanmamaktadır. Bu öğreticide, var olan verileri özgün işlevinden tamamen farklı şekillerde kullandınız. Model eşleştirme, bunları genişletmemiş olsanız bile, bu türlerin üzerine geçen işlevselliği yazma olanağını vermiştir.

## <a name="next-steps"></a>Sonraki adımlar

Tamamlanan kodu [DotNet/Samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/patterns/finished) GitHub deposundan indirebilirsiniz. Kendi hiyerarşinizdeki desenleri keşfedebilir ve bu tekniği düzenli kodlama etkinliklerinize ekleyin. Bu teknikleri öğrenirken, sorun yaklaşımı ve yeni işlevler oluşturmak için kullanabileceğiniz başka bir yol sunulmaktadır.
