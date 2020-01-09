---
title: LINQ ile Çalışma
description: Bu öğreticide LINQ, LINQ sorgularında kullanılmak üzere yazma yöntemleriyle diziler oluşturma ve Eager ile yavaş değerlendirme arasında ayrım yapma öğretilir.
ms.date: 10/29/2018
ms.technology: csharp-linq
ms.assetid: 0db12548-82cb-4903-ac88-13103d70aa77
ms.openlocfilehash: 8984fdf0ff26726b6d05e8bee8a9e8ae1c350ea7
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75345618"
---
# <a name="work-with-language-integrated-query-linq"></a>Dil ile tümleşik sorgu (LINQ) ile çalışma

## <a name="introduction"></a>Giriş

Bu öğretici, .NET Core ve C# dil özelliklerini size öğretir. Şunları öğreneceksiniz:

- LINQ ile sıralar oluşturun.
- LINQ sorgularında kolay bir şekilde kullanılabilecek yazma yöntemleri.
- Eager ve geç değerlendirme arasında ayrım yapın.

Herhangi bir Magician temel becerilerinden birini gösteren bir uygulama oluşturarak bu teknikleri öğrenirsiniz: [Faro karışık](https://en.wikipedia.org/wiki/Faro_shuffle). Kısaca, bir kağıt destesi yarısını tamamen yarıya böldüğünüz bir tekniktir, sonra da orijinal destesi yeniden derlemek için her bir yarısını her bir karmadan karıştırın.

Magicians bu tekniği, her kart her karıştırmadan sonra bilinen bir konumda olduğundan ve sipariş yinelenen bir düzen olduğundan kullanın.

Amacınıza uygun olarak, veri dizilerini işlemek için bir hafif göz atın. Oluşturacağınız uygulama bir kart destesi oluşturur ve sonra sıra sonuna kadar her seferinde bir sıra yazarak bir dizi karışık izler. Ayrıca, güncelleştirilmiş siparişi orijinal siparişle karşılaştırırsınız.

Bu öğreticide birden çok adım vardır. Her adımdan sonra, uygulamayı çalıştırabilir ve ilerleme durumunu görebilirsiniz. Ayrıca, DotNet/Samples GitHub deposunda [Tamamlanan örneği](https://github.com/dotnet/samples/blob/master/csharp/getting-started/console-linq) görebilirsiniz. İndirme yönergeleri için bkz. [örnekler ve öğreticiler](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

## <a name="prerequisites"></a>Prerequisites

Makinenizi .NET Core çalıştıracak şekilde ayarlamanız gerekir. Yükleme yönergelerini [.NET Core indirme](https://dotnet.microsoft.com/download) sayfasında bulabilirsiniz. Bu uygulamayı Windows, Ubuntu Linux veya OS X 'te veya bir Docker kapsayıcısında çalıştırabilirsiniz. En sevdiğiniz kod düzenleyicinizi yüklemeniz gerekir. Aşağıdaki açıklamalar açık kaynaklı, platformlar arası bir düzenleyici olan [Visual Studio Code](https://code.visualstudio.com/) kullanır. Bununla birlikte, rahat olan her türlü aracı kullanabilirsiniz.

## <a name="create-the-application"></a>Uygulamayı oluşturma

İlk adım yeni bir uygulama oluşturmaktır. Bir komut istemi açın ve uygulamanız için yeni bir dizin oluşturun. Geçerli dizini oluşturun. Komut istemine komut `dotnet new console` yazın. Bu, temel bir "Merhaba Dünya" uygulaması için başlangıç dosyalarını oluşturur.

Daha önce hiç kullanmadıysanız C# , [Bu öğretici](console-teleprompter.md) bir C# programın yapısını açıklar. Bunu okuyabilir ve sonra LINQ hakkında daha fazla bilgi edinmek için buraya dönebilirsiniz.

## <a name="create-the-data-set"></a>Veri kümesi oluşturma

Başlamadan önce, aşağıdaki satırların `dotnet new console`tarafından oluşturulan `Program.cs` dosyanın en üstünde olduğundan emin olun:

```csharp
// Program.cs
using System;
using System.Collections.Generic;
using System.Linq;
```

Bu üç satır (`using` deyimleri) dosyanın en üstünde değilse, programımız derlenmeyecektir.

İhtiyacınız olan tüm başvurulara sahip olduğunuza göre, kart destesi ne olduğunu göz önünde bulundurun. Yaygın olarak, kart oynamaya yönelik bir deste dört cins içerir ve her cinsten on yedi değer vardır. Normalde, bir `Card` sınıfını doğrudan bat üzerinde oluşturup el ile bir `Card` nesne koleksiyonu doldurarak göz önüne alabilirsiniz. LINQ ile, kart destesi oluşturma konusunda olağan yollardan daha kısa bir işlem yapabilirsiniz. `Card` sınıfı oluşturmak yerine, sırasıyla cins ve dereceleri temsil eden iki sıra oluşturabilirsiniz. <xref:System.Collections.Generic.IEnumerable%601>dizeleri olarak derecelendirmelerinin ve cinslerin üretebileceği, aslında basit bir [*Yineleyici yöntemleri*](../iterators.md#enumeration-sources-with-iterator-methods) oluşturacaksınız:

```csharp
// Program.cs
// The Main() method

static IEnumerable<string> Suits()
{
    yield return "clubs";
    yield return "diamonds";
    yield return "hearts";
    yield return "spades";
}

static IEnumerable<string> Ranks()
{
    yield return "two";
    yield return "three";
    yield return "four";
    yield return "five";
    yield return "six";
    yield return "seven";
    yield return "eight";
    yield return "nine";
    yield return "ten";
    yield return "jack";
    yield return "queen";
    yield return "king";
    yield return "ace";
}
```

Bunları `Program.cs` dosyanıza `Main` yönteminin altına yerleştirin. Bu iki yöntem her ikisi de çalıştıkları sırada bir sıra üretmek için `yield return` söz dizimini kullanır. Derleyici, <xref:System.Collections.Generic.IEnumerable%601> uygulayan bir nesne oluşturur ve bunların istendiği sırada dizelerin dizisini oluşturur.

Şimdi, kart destesi oluşturmak için bu yineleyici yöntemleri kullanın. LINQ sorgusunu `Main` yönteimize yerleştirebilirsiniz. İşte buna bir göz atın:

```csharp
// Program.cs
static void Main(string[] args)
{
    var startingDeck = from s in Suits()
                       from r in Ranks()
                       select new { Suit = s, Rank = r };

    // Display each card that we've generated and placed in startingDeck in the console
    foreach (var card in startingDeck)
    {
        Console.WriteLine(card);
    }
}
```

Çoklu `from` yan tümceleri, ikinci dizideki her öğe ile ilk dizideki her öğeyi birleştiren tek bir sıra oluşturan bir <xref:System.Linq.Enumerable.SelectMany%2A>oluşturur. Sıra, amacınız açısından önemlidir. İlk kaynak dizideki (cins) ilk öğe, ikinci dizideki her öğe (Rütler) ile birleştirilir. Bu, birinci cins 'in tüm üçüncü dört kartını üretir. Bu işlem, ilk dizideki (cins) her öğe ile yinelenir. Nihai sonuç, cinsler tarafından, ardından değerler tarafından sıralanan kartların bir destesi.

Yukarıda kullanılan sorgu söz diziminde LINQ 'nizi yazmayı veya bunun yerine Yöntem sözdizimini kullanmayı tercih etmeksizin, bir sözdizimi formundan diğerine gitmeniz her zaman mümkündür. Sorgu sözdiziminde yazılan yukarıdaki sorgu yöntem sözdiziminde şöyle yazılabilir:

```csharp
var startingDeck = Suits().SelectMany(suit => Ranks().Select(rank => new { Suit = suit, Rank = rank }));
```

Derleyici, sorgu söz dizimi ile yazılan LINQ deyimlerini eşdeğer Yöntem çağrısı sözdizimine dönüştürür. Bu nedenle, söz dizimi seçiminizden bağımsız olarak, sorgunun iki sürümü aynı sonucu üretir. Hangi sözdiziminin durumunuz için en iyi şekilde çalıştığını seçin: Örneğin, bir ekip içinde çalışıyorsanız, bazı üyelerin Yöntem sözdizimi konusunda zorluk yaşıyorsanız, sorgu söz dizimini kullanmayı tercih edin.

Devam edin ve bu noktada derlediğiniz örneği çalıştırın. Bu, destedeki tüm 52 kartları görüntüler. `Suits()` ve `Ranks()` yöntemlerinin nasıl yürütüleceğini gözlemlemek için bu örneği bir hata ayıklayıcı altında çalıştırmanın çok yararlı olduğunu fark edebilirsiniz. Her bir dizinin her bir dizesinin yalnızca gerektiğinde oluşturulduğunu açıkça görebilirsiniz.

![52 kart yazan uygulamayı gösteren bir konsol penceresi.](./media/working-with-linq/console-52-card-application.png)

## <a name="manipulate-the-order"></a>Siparişi değiştirme

Ardından, destedeki kartları nasıl karıştığınıza odaklanın. Her iyi karışmaya yönelik ilk adım, desteyi ikiye bölmenizde yarar vardır. LINQ API 'lerinin parçası olan <xref:System.Linq.Enumerable.Take%2A> ve <xref:System.Linq.Enumerable.Skip%2A> yöntemleri bu özelliği sizin için sağlar. `foreach` döngüsünün altına yerleştirin:

```csharp
// Program.cs
public static void Main(string[] args)
{
    var startingDeck = from s in Suits()
                       from r in Ranks()
                       select new { Suit = s, Rank = r };

    foreach (var c in startingDeck)
    {
        Console.WriteLine(c);
    }

    // 52 cards in a deck, so 52 / 2 = 26
    var top = startingDeck.Take(26);
    var bottom = startingDeck.Skip(26);
}
```

Ancak, standart kitaplıkta avantajlarından yararlanmak için bir karıştırma yöntemi yoktur, bu nedenle kendi kodunuzu yazmanız gerekir. Oluşturmakta olduğunuz karıştırma yöntemi, LINQ tabanlı programlarla birlikte kullanacağınız birkaç tekniği gösterir. bu nedenle, bu işlemin her bir bölümü adımlarda açıklanacaktır.

LINQ sorgularından geri döndüğünüzde <xref:System.Collections.Generic.IEnumerable%601> nasıl etkileşim kurabileceğine ilişkin bazı işlevler eklemek için, [Uzantı yöntemleri](../programming-guide/classes-and-structs/extension-methods.md)adlı bazı özel tür yöntemler yazmanız gerekir. Kısaca, bir genişletme yöntemi, işlevselliği eklemek istediğiniz orijinal türü değiştirmek zorunda kalmadan, zaten var olan bir türe yeni işlevsellik ekleyen özel amaçlı *statik bir yöntemdir* .

`Extensions.cs`adlı programınıza yeni bir *statik* sınıf dosyası ekleyerek uzatma yöntemlerinizi yeni bir giriş yapın ve ardından ilk uzantı yöntemini oluşturmaya başlayın:

```csharp
// Extensions.cs
using System;
using System.Collections.Generic;
using System.Linq;

namespace LinqFaroShuffle
{
    public static class Extensions
    {
        public static IEnumerable<T> InterleaveSequenceWith<T>(this IEnumerable<T> first, IEnumerable<T> second)
        {
            // Your implementation will go here soon enough
        }
    }
}
```

Yöntem imzasına bir süre için bakın, özellikle Parametreler:

```csharp
public static IEnumerable<T> InterleaveSequenceWith<T> (this IEnumerable<T> first, IEnumerable<T> second)
```

Yöntemin ilk bağımsız değişkeninde `this` değiştiricinin eklenmesini görebilirsiniz. Bu, yöntemi ilk bağımsız değişkenin türünün bir Member yöntemi gibi çağırmış olmanız anlamına gelir. Bu yöntem bildirimi Ayrıca, giriş ve çıkış türlerinin `IEnumerable<T>`olduğu standart bir iDom izler. Bu uygulama, LINQ yöntemlerinin daha karmaşık sorgular gerçekleştirmek için birlikte zincirde olmasını sağlar.

Doğal olarak, desteyi halele böldüğünüz için bu kilitlenenlere birlikte katılmanız gerekir. Kod içinde bu, hem <xref:System.Linq.Enumerable.Take%2A>, hem de <xref:System.Linq.Enumerable.Skip%2A>, öğeleri *`interleaving`* ve tek bir sıra oluşturmak istediğiniz her iki diziyi de numaralandırdığınız anlamına gelir: şimdi karlı kart destesi. İki diziyle çalışacak bir LINQ yöntemi yazmak için <xref:System.Collections.Generic.IEnumerable%601> nasıl çalıştığını anlamanız gerekir.

<xref:System.Collections.Generic.IEnumerable%601> arabiriminin bir yöntemi vardır: <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A>. <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> tarafından döndürülen nesne, sonraki öğeye ve dizideki geçerli öğeyi alan bir özelliğe geçiş yöntemine sahiptir. Bu iki üyeyi, koleksiyonu numaralandırmak ve öğeleri döndürmek için kullanacaksınız. Bu ayırma yöntemi bir yineleyici yöntemi olacak, bu nedenle bir koleksiyon oluşturmak ve koleksiyonu döndürmek yerine yukarıda gösterilen `yield return` söz dizimini kullanacaksınız.

Bu yöntemin uygulanması aşağıda verilmiştir:

[!CODE-csharp[InterleaveSequenceWith](../../../samples/csharp/getting-started/console-linq/extensions.cs?name=snippet1)]

Bu yöntemi yazdıktan sonra `Main` yöntemine dönün ve destesi bir kez karışın:

```csharp
// Program.cs
public static void Main(string[] args)
{
    var startingDeck = from s in Suits()
                       from r in Ranks()
                       select new { Suit = s, Rank = r };

    foreach (var c in startingDeck)
    {
        Console.WriteLine(c);
    }

    var top = startingDeck.Take(26);
    var bottom = startingDeck.Skip(26);
    var shuffle = top.InterleaveSequenceWith(bottom);

    foreach (var c in shuffle)
    {
        Console.WriteLine(c);
    }
}
```

## <a name="comparisons"></a>Karşılaştırma

Destesi orijinal sıralarına geri ayarlamak için kaç tane karışık? Bunu öğrenmek için, iki sıranın eşit olup olmadığını belirleyen bir yöntem yazmanız gerekir. Bu yöntemi aldıktan sonra, destesi bir döngüyle karışık olarak sunan kodu yerleştirmeniz ve destenin sırasıyla ne zaman geri olduğunu kontrol etmeniz gerekir.

İki sıranın eşit olup olmadığını anlamak için bir yöntem yazmak basit olmalıdır. Bu, destesi karıştırmak için yazdığınız yöntemin benzer bir yapısıdır. Her bir öğe `yield return`yerine yalnızca bu kez her bir sıranın eşleşen öğelerini karşılaştırırsınız. Tüm sıra numaralandırılmışsa, her öğe eşleşiyorsa, sıralar aynıdır:

[!CODE-csharp[SequenceEquals](../../../samples/csharp/getting-started/console-linq/extensions.cs?name=snippet2)]

Bu, ikinci bir LINQ deyimidir: Terminal yöntemlerini gösterir. Bunlar girdi olarak bir sıra alır (veya bu durumda iki dizi) ve tek bir skaler değer döndürür. Terminal yöntemleri kullanılırken, her zaman bir LINQ sorgusunun Yöntem zincirindeki son yöntem ve bu nedenle "Terminal" adı verilir.

Bu işlemi, deste 'nın orijinal düzeninde ne zaman geri yükleneceğini tespit etmek için kullandığınızda görebilirsiniz. Karışık kodu bir döngü içine koyun ve `SequenceEquals()` yöntemi uygulanarak sıranın özgün sırasına geri döndüğünüzde durdurulur. Bir dizi yerine tek bir değer döndürdüğünden, her sorguda her zaman son yöntem olacağını görebilirsiniz:

```csharp
// Program.cs
static void Main(string[] args)
{
    // Query for building the deck

    // Shuffling using InterleaveSequenceWith<T>();

    var times = 0;
    // We can re-use the shuffle variable from earlier, or you can make a new one
    shuffle = startingDeck;
    do
    {
        shuffle = shuffle.Take(26).InterleaveSequenceWith(shuffle.Skip(26));

        foreach (var card in shuffle)
        {
            Console.WriteLine(card);
        }
        Console.WriteLine();
        times++;

    } while (!startingDeck.SequenceEquals(shuffle));

    Console.WriteLine(times);
}
```

Şimdiye kadar aldığınız kodu çalıştırın ve her bir karıştırmadan destesi nasıl yeniden bir şekilde yeniden düzenler. 8 karışık (do-while döngüsünün yinelemesi) sonrasında, deste başlangıç LINQ sorgusundan ilk kez oluşturduğunuz sırada bulunduğu özgün yapılandırmaya geri döner.

## <a name="optimizations"></a>İyileştirmeler

Şimdiye kadar derlediğiniz örnek, üst ve alt kartların her çalıştırmada aynı kalacağı *karışık*bir şekilde yürütülür. Tek bir değişiklik yapabiliriz: bunun yerine, tüm 52 kartlar konum değiştiren bir *karışık olarak* kullanacağız. Bir karışık olarak, alt yarısı ilk kartın destedeki ilk kart haline gelmesi için destesi bir kez ayırmada kullanırsınız. Bu, üstteki yarısında son kartın alt kart haline geldiği anlamına gelir. Bu, tekil kod satırında basit bir değişiklik. <xref:System.Linq.Enumerable.Take%2A> ve <xref:System.Linq.Enumerable.Skip%2A>konumlarını değiştirerek geçerli karıştırma sorgusunu güncelleştirin. Bu, deste 'nın üst ve alt kilitlenme sırasını değiştirir:

```csharp
shuffle = shuffle.Skip(26).InterleaveSequenceWith(shuffle.Take(26));
```

Programı yeniden çalıştırın ve deste 'nın kendisini yeniden sıralamak için 52 yineleme aldığını görürsünüz. Program çalışmaya devam ettiğinden bazı önemli performans düşüşlerinden de karşılaşırsınız.

Bunun birçok nedeni vardır. Bu performans durmasının önemli nedenlerine bir tane ekleyebilirsiniz: verimsiz [*yavaş değerlendirme*](../programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)kullanımı.

Kısaca, yavaş değerlendirme bir deyimin değerlendirmesinin değeri gerekli olana kadar gerçekleştirilmediğini belirtir. LINQ sorguları, geç değerlendirilen ifadelerdir. Sıralar yalnızca öğeler istendiğinde oluşturulur. Genellikle bu, LINQ 'ın önemli bir avantajıdır. Bununla birlikte, bu program gibi bir kullanımda, yürütme zamanında üstel büyümeye neden olur.

Bir LINQ sorgusu kullanarak özgün destesi oluşturduğumuz unutulmamalıdır. Her karıştırma, önceki destede üç LINQ sorgusu gerçekleştirerek oluşturulur. Bunların tümü geç gerçekleştirilir. Bu Ayrıca, sıranın her istenilişinde yeniden gerçekleştirdikleri anlamına gelir. 5 TB yinelemesine alışışınızda, ilk desteyi pek çok kez yeniden oluşturuluyor olursunuz. Bu davranışı göstermek için bir günlük yazalım. Ardından, onu düzeltireceksiniz.

`Extensions.cs` dosyanızda, aşağıdaki yöntemi yazın veya kopyalayın. Bu genişletme yöntemi, proje dizininizde `debug.log` adlı yeni bir dosya oluşturur ve şu anda günlük dosyasına yürütülmekte olan sorguyu kaydeder. Bu genişletme yöntemi sorgunun yürütüldüğünü işaretlemek için herhangi bir sorguya eklenebilir.

[!CODE-csharp[LogQuery](../../../samples/csharp/getting-started/console-linq/extensions.cs?name=snippet3)]

`File`altında kırmızı renkli bir çizgi görürsünüz, bunun anlamı yoktur. Derleyici `File` ne olduğunu bilmediğinden derlenmez. Bu sorunu çözmek için `Extensions.cs`ilk satırın altına aşağıdaki kod satırını eklediğinizden emin olun:

```csharp
using System.IO;
```

Bu, sorunu çözmeli ve kırmızı hata kaybolur.

Ardından, her bir sorgunun tanımını bir günlük iletisiyle işaretleyin:

```csharp
// Program.cs
public static void Main(string[] args)
{
    var startingDeck = (from s in Suits().LogQuery("Suit Generation")
                        from r in Ranks().LogQuery("Rank Generation")
                        select new { Suit = s, Rank = r }).LogQuery("Starting Deck");

    foreach (var c in startingDeck)
    {
        Console.WriteLine(c);
    }

    Console.WriteLine();
    var times = 0;
    var shuffle = startingDeck;

    do
    {
        // Out shuffle
        /*
        shuffle = shuffle.Take(26)
            .LogQuery("Top Half")
            .InterleaveSequenceWith(shuffle.Skip(26)
            .LogQuery("Bottom Half"))
            .LogQuery("Shuffle");
        */

        // In shuffle
        shuffle = shuffle.Skip(26).LogQuery("Bottom Half")
                .InterleaveSequenceWith(shuffle.Take(26).LogQuery("Top Half"))
                .LogQuery("Shuffle");

        foreach (var c in shuffle)
        {
            Console.WriteLine(c);
        }

        times++;
        Console.WriteLine(times);
    } while (!startingDeck.SequenceEquals(shuffle));

    Console.WriteLine(times);
}
```

Her sorguya eriştiğinizde günlüğe kayıt yapmayın. Yalnızca özgün sorguyu oluşturduğunuzda günlüğe kaydedilir. Programın çalıştırılması uzun sürer, ancak artık neden de görebilirsiniz. Oturum açma özelliği etkinken karışık olarak çalışan haya 'nın dışında çalıştırırsanız, arka arkaya geri dönün. Hala yavaş değerlendirme etkileri görürsünüz. Tek bir çalıştırmasında, tüm değer ve cins üretimi dahil 2592 sorgu yürütür.

Yaptığınız yürütmelerin sayısını azaltmak için kodun performansını buradan geliştirebilirsiniz. Yapabilmeniz gereken basit bir çözüm, kart destesi oluşturan orijinal LINQ sorgusunun sonuçlarını *önbelleğe* almak için kullanılır. Şu anda sorguları yeniden yürütüyorsunuz ve do-while döngüsü bir yinelemeden sonra yeniden oluşturuyor, kartlar ve reshuffling her seferinde yeniden oluşturacağız. Kartların destesi önbelleğe almak için <xref:System.Linq.Enumerable.ToArray%2A> LINQ yöntemlerinden yararlanabilir ve <xref:System.Linq.Enumerable.ToList%2A>; sorguları sorgulara eklediğinizde, onlara söyledikleri aynı eylemleri gerçekleştirir, ancak artık sonuçları çağırmak istediğiniz yönteme bağlı olarak bir dizide veya listede depolayacağız. LINQ metodu <xref:System.Linq.Enumerable.ToArray%2A> her iki sorguya de ekleyin ve programı yeniden çalıştırın:

[!CODE-csharp[Main](../../../samples/csharp/getting-started/console-linq/Program.cs?name=snippet1)]

Şimdi, karışık karıştırma 30 sorguya kadar. Karıştırma ile birlikte yeniden çalıştırın ve benzer iyileştirmeler görürsünüz: şimdi 162 sorguları yürütür.

Lütfen bu örneğin, yavaş değerlendirmenin performans sorunlarına neden olabileceği kullanım durumlarını vurgulamak için **tasarlandığını** unutmayın. Yavaş değerlendirmenin kod performansını etkileyebileceğini görmek önemli olsa da, tüm sorguların bir şekilde çalışması gerektiğini anlamak önemlidir. <xref:System.Linq.Enumerable.ToArray%2A> kullanmadan yaptığınız performans isabeti, kart destesi için her yeni düzenlemenin önceki düzenlemeden derlenme nedeni. Geç değerlendirme kullanmak, her yeni deste yapılandırmasının orijinal deste tarafından oluşturulduğu anlamına gelir ve bu da `startingDeck`oluşturan kodu yürütüyordur. Bu, büyük miktarda ekstra iş oluşmasına neden olur.

Uygulamada, bazı algoritmalar Eager değerlendirmesi kullanılarak iyi çalışır ve diğerleri, yavaş değerlendirme kullanarak iyi çalışır. Günlük kullanım için, veri kaynağı bir veritabanı altyapısı gibi ayrı bir işlem olduğunda, yavaş değerlendirme genellikle daha iyi bir seçenektir. Veritabanları için, yavaş değerlendirme, daha karmaşık sorguların veritabanı işlemine yalnızca bir gidiş dönüş ve kodunuzun geri kalanına geri dönmesi için izin verir. Bu, yavaş veya Eager değerlendirmesi kullanmayı tercih etmeksizin, süreçlerinizi ölçmenize ve hangi tür değerlendirme türünün size en iyi performansı sunmasına bakılmaksızın LINQ esnektir.

## <a name="conclusion"></a>Sonuç

Bu projede şunları kapsamış olursunuz:

- verileri anlamlı bir sırayla toplamak için LINQ sorguları kullanma
- LINQ Sorgularına kendi özel işlevselümüzü eklemek için uzantı yöntemleri yazma
- LINQ sorgularımızın, düşürülmüş hız gibi performans sorunları üzerinde çalıştığı, kodumuza ait yerleri bulma
- ' deki geç ve Eager değerlendirmesi, LINQ sorguları ve sorgu performansı üzerinde olabilecek etkileri

LINQ 'ten itibaren, kart püf noktaları için bir teknik Magicians kullanımı hakkında biraz bilgi edindiniz. Magicians, her kartın destede nereye taşındığını denetleyebildiğinden Faro karıştırmasını kullanın. Artık bilineceğimize göre, diğer herkese açık yapmayın!

LINQ hakkında daha fazla bilgi için bkz.

- [Dil ile Tümleşik Sorgu (LINQ)](../programming-guide/concepts/linq/index.md)
- [LINQ'ye Giriş](../programming-guide/concepts/linq/index.md)
- [Temel LINQ sorgu Işlemleri (C#)](../programming-guide/concepts/linq/basic-linq-query-operations.md)
- [LINQ (C#) Ile veri dönüştürmeleri](../programming-guide/concepts/linq/data-transformations-with-linq.md)
- [LINQ (C#) Içinde sorgu sözdizimi ve Yöntem sözdizimi](../programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md)
- [LINQ'i Destekleyen C# Özellikleri](../programming-guide/concepts/linq/features-that-support-linq.md)
