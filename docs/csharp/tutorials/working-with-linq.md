---
title: LINQ ile Çalışma
description: Bu öğretici, LINQ ile diziler oluşturmayı, LINQ sorgularında kullanım yöntemlerini yazmayı ve istekli ve tembel değerlendirmeyi birbirinden nasıl ayıracağınızı öğretir.
ms.date: 10/29/2018
ms.technology: csharp-linq
ms.assetid: 0db12548-82cb-4903-ac88-13103d70aa77
ms.openlocfilehash: ece001e82c0aa44a91999bea78d2fd695ff9362b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78240021"
---
# <a name="work-with-language-integrated-query-linq"></a>Dil-Entegre Sorgu (LINQ) ile Çalışma

## <a name="introduction"></a>Giriş

Bu öğretici size .NET Core ve C# dilinde ki özellikleri öğretir. Şunları öğrenirsiniz:

- LINQ ile diziler oluşturun.
- LINQ sorgularında kolayca kullanılabilen yazma yöntemleri.
- Istekli ve tembel değerlendirme arasında ayrım.

Faro [shuffle:](https://en.wikipedia.org/wiki/Faro_shuffle)Herhangi bir sihirbaz temel becerilerinden birini gösteren bir uygulama oluşturarak bu teknikleri öğreneceksiniz. Kısaca, bir faro shuffle tam olarak ikiye bir kart destebölünmüş bir tekniktir, sonra shuffle orijinal güverte yeniden oluşturmak için her yarısından her bir kart interleaves.

Sihirbazlar bu tekniği kullanır, çünkü her kart her karıştırmadan sonra bilinen bir yerdedir ve sıra yinelenen bir desendir.

Sizin amaçlarınız için, veri dizilerini manipüle etmek için açık yürekli bir bakış. Oluşturacağınız uygulama bir kart destesi oluşturur ve ardından her seferinde sırayı yazarak bir dizi karışıklık gerçekleştirir. Ayrıca güncelleştirilmiş siparişi orijinal siparişle karşılaştıracaksınız.

Bu öğreticinin birden çok adımı vardır. Her adımdan sonra, uygulamayı çalıştırabilir ve ilerlemeyi görebilirsiniz. [Tamamlanan örneği](https://github.com/dotnet/samples/blob/master/csharp/getting-started/console-linq) dotnet/örnek GitHub deposunda da görebilirsiniz. İndirme talimatları için [Örnekler ve Öğreticiler'e](../../samples-and-tutorials/index.md#viewing-and-downloading-samples)bakın.

## <a name="prerequisites"></a>Önkoşullar

.NET çekirdeğini çalıştırmak için makinenizi ayarlamanız gerekir. Yükleme yönergelerini [.NET Çekirdek İndirme](https://dotnet.microsoft.com/download) sayfasında bulabilirsiniz. Bu uygulamayı Windows, Ubuntu Linux veya OS X'te veya Docker kapsayıcısında çalıştırabilirsiniz. En sevdiğiniz kod düzenleyicisini yüklemeniz gerekir. Aşağıdaki açıklamalar açık kaynak, çapraz platform düzenleyicisi [olan Visual Studio Code'u](https://code.visualstudio.com/) kullanabilmiştir. Ancak, hangi araçları ile rahat kullanabilirsiniz.

## <a name="create-the-application"></a>Uygulamayı Oluştur

İlk adım yeni bir uygulama oluşturmaktır. Bir komut istemi açın ve uygulamanız için yeni bir dizin oluşturun. Bunu geçerli dizini yapın. Komut istemine komut `dotnet new console` yazın. Bu, temel bir "Hello World" uygulaması için başlangıç dosyalarını oluşturur.

Daha önce Hiç C# kullanmadıysanız, [bu öğretici](console-teleprompter.md) bir C# programının yapısını açıklar. Bunu okuyabilir ve linq hakkında daha fazla bilgi edinmek için buraya geri dönebilirsiniz.

## <a name="create-the-data-set"></a>Veri Kümesini Oluşturma

Başlamadan önce, aşağıdaki satırların aşağıdaki tarafından `Program.cs` `dotnet new console`oluşturulan dosyanın en üstünde olduğundan emin olun:

```csharp
// Program.cs
using System;
using System.Collections.Generic;
using System.Linq;
```

Bu üç satır`using` (deyimler) dosyanın en üstünde değilse, programımız derlemez.

Artık ihtiyacınız olan tüm referanslara sahip olduğunuza göre, bir kart destesini neyin oluşturduğunu düşünün. Genellikle, bir deste iskambil kartı dört takım elbiseye sahiptir ve her takım elbisenin on üç değeri vardır. Normalde, yarasa dan sağ `Card` kapalı bir sınıf oluşturma ve `Card` elle nesnelerin bir koleksiyon doldurma düşünebilirsiniz. LINQ ile, bir kart destesi oluşturma yla başa çıkmanın her zamankinden daha kısa olabilir. Bir `Card` sınıf oluşturmak yerine, sırasıyla takım elbise ve sıralamaları temsil edecek iki dizi oluşturabilirsiniz. Dereceleri ve dizeleri s olarak <xref:System.Collections.Generic.IEnumerable%601>uygun üretecek [*yineleyici yöntemleri*](../iterators.md#enumeration-sources-with-iterator-methods) gerçekten basit bir çift oluşturacaksınız:

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

Bunları dosyanızdaki `Program.cs` `Main` yöntemin altına yerleştirin. Bu iki yöntem, `yield return` çalışırken bir sıra oluşturmak için sözdizimini kullanır. Derleyici, dizeleri istedikleri gibi <xref:System.Collections.Generic.IEnumerable%601> uygulayan ve üreten bir nesne oluşturur.

Şimdi, kart destesi oluşturmak için bu yineleyici yöntemlerikullanın. LINQ sorgusunu yöntemimize `Main` yerleştireceksiniz. İşte bir bakış:

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

Birden `from` çok yan <xref:System.Linq.Enumerable.SelectMany%2A>tümce, ilk dizideki her öğeyi ikinci sırada her öğeyle birleştirerek tek bir sıra oluşturan bir , üretir. Emir bizim amaçlarımız için önemlidir. İlk kaynak dizisindeki ilk öğe (Suit) ikinci dizideki (Sıralar) her öğeyle birleştirilir. Bu ilk takım tüm on üç kart üretir. Bu işlem, ilk sırada (Suits) her öğe ile tekrarlanır. Sonuç, takım elbiseler tarafından sipariş edilen bir kart destesi ve ardından değerlerdir.

LinQ'unuzu yukarıda kullanılan sorgu sözdizimine yazmayı veya bunun yerine yöntem sözdizimini kullanmayı seçseniz de, bir sözdiziminden diğerine geçmenin her zaman mümkün olduğunu unutmayın. Sorgu sözdiziminde yazılan yukarıdaki sorgu yöntem sözdiziminde şöyle yazılabilir:

```csharp
var startingDeck = Suits().SelectMany(suit => Ranks().Select(rank => new { Suit = suit, Rank = rank }));
```

Derleyici, sorgu sözdizimi ile yazılmış LINQ deyimlerini eşdeğer yöntem çağrı sözdizimine çevirir. Bu nedenle, sözdizimi seçiminiz ne olursa olsun, sorgunun iki sürümü aynı sonucu üretir. Durumunuz için en iyi sonucu seçin: örneğin, bazı üyelerin yöntem sözdizimi ile ilgili zorluk yaşadığı bir takımda çalışıyorsanız, sorgu sözdizimini kullanmayı tercih etmeyi deneyin.

Devam edin ve bu noktada oluşturduğun örneği çalıştırın. 52 kartın tümlerini destede gösterecektir. Bu örneği bir hata ayıklama altında çalıştırmayı ve `Suits()` `Ranks()` yöntemlerin nasıl yürütüldünlerini gözlemlemeniz çok yararlı olabilir. Her dizideki her dizenin yalnızca gerektiği gibi oluşturulduğunu açıkça görebilirsiniz.

![Uygulamanın 52 kart yazdığını gösteren bir konsol penceresi.](./media/working-with-linq/console-52-card-application.png)

## <a name="manipulate-the-order"></a>Siparişi Manipüle Edin

Sonra, destedeki kartları nasıl karıştıracağınız üzerine odaklanın. Herhangi bir iyi shuffle ilk adım iki güverte bölmektir. LINQ API'lerinin bir parçası olan yöntemler <xref:System.Linq.Enumerable.Take%2A> ve <xref:System.Linq.Enumerable.Skip%2A> yöntemler bu özelliği sizin için sağlar. Onları döngünün `foreach` altına yerleştirin:

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

Ancak, standart kitaplıkta yararlanabileceğiniz bir karıştırma yöntemi yoktur, bu nedenle kendi kitaplığınızı yazmanız gerekir. Oluşturacağınız karıştırma yöntemi, LINQ tabanlı programlarda kullanacağınız çeşitli teknikleri gösterir, böylece bu işlemin her bölümü adım adım açıklanır.

LINQ sorgularından geri <xref:System.Collections.Generic.IEnumerable%601> alacağınız ile nasıl etkileşimde bulunacağınız [için, uzantı yöntemleri](../programming-guide/classes-and-structs/extension-methods.md)adı verilen bazı özel yöntemler yazmanız gerekir. Kısaca, uzantı yöntemi, işlevsellik eklemek istediğiniz özgün türü değiştirmek zorunda kalmadan zaten varolan bir türe yeni işlevler ekleyen özel amaçlı statik bir *yöntemdir.*

Programınıza `Extensions.cs`yeni bir *statik* sınıf dosyası ekleyerek uzantı yöntemlerinize yeni bir ev verin ve ardından ilk uzantı yöntemini oluşturmaya başlayın:

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

Bir an için yöntem imzabak, özellikle parametreleri:

```csharp
public static IEnumerable<T> InterleaveSequenceWith<T> (this IEnumerable<T> first, IEnumerable<T> second)
```

Yönteme ilk bağımsız `this` değişkende değiştiricinin ekini görebilirsiniz. Bu, yöntemi ilk bağımsız değişken türünün bir üyesi yöntemiymiş gibi adlandırdığınız anlamına gelir. Bu yöntem bildirimi, giriş ve çıkış türlerinin bulunduğu `IEnumerable<T>`standart bir deyim de izler. Bu uygulama, linq yöntemlerinin daha karmaşık sorgular gerçekleştirmek için birbirine zincirlemesini sağlar.

Doğal olarak, desteyi ikiye böldüğün için bu yarılara birlikte katılman gerekecek. Kod olarak, bu, elde <xref:System.Linq.Enumerable.Take%2A> <xref:System.Linq.Enumerable.Skip%2A> *`interleaving`* ettiğiniz her iki diziyi de, öğeleri ve bir sırayı şu anda karıştırDığınız kart destenizi sıralaacağınız anlamına gelir. İki diziyle çalışan bir LINQ yöntemi yazmak, <xref:System.Collections.Generic.IEnumerable%601> nasıl çalıştığını anlamanızı gerektirir.

<xref:System.Collections.Generic.IEnumerable%601> Arabirimin tek bir <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A>yöntemi vardır: . Döndürülen <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> nesnenin bir sonraki öğeye taşımak için bir yöntemi ve dizideki geçerli öğeyi alan bir özelliği vardır. Bu iki üyeyi koleksiyonu sayısallandırmak ve öğeleri döndürmek için kullanacaksınız. Bu Interleave yöntemi bir yineleyici yöntemi olacaktır, bu nedenle bir koleksiyon oluşturmak ve koleksiyonu `yield return` döndürmek yerine, yukarıda gösterilen sözdizimini kullanırsınız.

İşte bu yöntemin uygulanması:

[!CODE-csharp[InterleaveSequenceWith](../../../samples/snippets/csharp/getting-started/console-linq/extensions.cs?name=snippet1)]

Artık bu yöntemi yazdığınız için yönteme `Main` geri dön ve desteyi bir kez karıştırın:

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

## <a name="comparisons"></a>Karşılaştırmalar

Desteyi orijinal düzenine geri ayarlamak için kaç değişiklik gerekiyor? Öğrenmek için, iki dizinin eşit olup olmadığını belirleyen bir yöntem yazmanız gerekir. Bu yönteme sahip olduktan sonra, desteyi bir döngüye karıştıran kodu yerleştirmeniz ve destenin ne zaman düzene geri döndüğünü kontrol etmeniz gerekir.

İki dizinin eşit olup olmadığını belirlemek için bir yöntem yazmak basit olmalıdır. Desteyi karıştırmak için yazdığın yönteme benzer bir yapı. Yalnızca bu kez, `yield return`her öğeyi almak yerine, her dizinin eşleşen öğelerini karşılaştıracaksınız. Tüm sıra numaralandırıldığında, her öğe eşleşirse, diziler aynıdır:

[!CODE-csharp[SequenceEquals](../../../samples/snippets/csharp/getting-started/console-linq/extensions.cs?name=snippet2)]

Bu ikinci bir LINQ deyimini gösterir: terminal yöntemleri. Giriş olarak bir sıra alırlar (veya bu durumda, iki dizi) ve tek bir skaler değer döndürerler. Terminal yöntemlerini kullanırken, linq sorgusu için bir yöntem zincirinde her zaman son yöntemdir, dolayısıyla "terminal" adı verilir.

Destenin orijinal sırasına ne zaman geri döndüğünü belirlemek için kullandığınızda bunu iş başında görebilirsiniz. Karıştırma kodunu bir döngüye koyun ve yöntemi uygulayarak dizi orijinal sırasına geri döndüğünde durdurun. `SequenceEquals()` Bir dizi yerine tek bir değer döndürdüğünden, her sorguda her zaman son yöntem olacağını görebilirsiniz:

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

Şimdiye kadar var olan kodu çalıştırın ve her shuffle'da destenin nasıl yeniden düzenlediğini göz önünde virde edin. 8 karışıklıktan (yap döngüsüyinelemeleri) sonra, güverte, başlangıç LINQ sorgusundan ilk oluşturduğunuzda olduğu orijinal yapılandırmaya geri döner.

## <a name="optimizations"></a>İyileştirmeler

Şimdiye kadar oluşturabileceğiniz örnek, üst ve alt kartların her çalıştırmada aynı kaldığı bir *dış karıştırma*işlemini yürütür. Bir değişiklik yapalım: 52 kartın tamamının yerini değiştirdiği bir *karışık* lık kullanacağız. Bir karıştırma için, alt yarısında ilk kart destedeki ilk kart olur, böylece deste interleave. Bu da üst yarıdaki son kartın alt kart olduğu anlamına gelir. Bu, tekil bir kod satırında yapılan basit bir değişikliktir. Konumlarını değiştirerek geçerli karıştırma <xref:System.Linq.Enumerable.Take%2A> sorgusunu güncelleştirin ve <xref:System.Linq.Enumerable.Skip%2A>. Bu, destenin üst ve alt yarısının sırasını değiştirir:

```csharp
shuffle = shuffle.Skip(26).InterleaveSequenceWith(shuffle.Take(26));
```

Programı yeniden çalıştırDığınızda, destenin kendisini yeniden sipariş etmesi için 52 yineleme gerektiğini görürsünüz. Ayrıca, program çalışmaya devam ettikçe bazı ciddi performans bozulmaları fark etmeye başlarsınız.

Bunun birkaç nedeni vardır. Bu performans düşüşünün başlıca nedenlerinden biriyle başa çıkabilirsiniz: [*tembel değerlendirmenin*](../programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)verimsiz kullanımı.

Kısaca, tembel değerlendirme, bir deyimin değerinin gerekli olana kadar değerlendirilmesinin gerçekleştirilmediğini belirtir. LINQ sorguları tembelce değerlendirilen ifadelerdir. Diziler yalnızca öğeler istendiğinde oluşturulur. Genellikle, bu LINQ büyük bir yararı' s. Ancak, bu program gibi bir kullanımda, bu yürütme süresi üstel büyüme neden olur.

Orijinal desteyi LINQ sorgusu kullanarak oluşturduğumuzu unutmayın. Her karıştırma, önceki güvertede üç LINQ sorgusu gerçekleştirerek oluşturulur. Tüm bunlar tembelce yapılır. Bu aynı zamanda, dizi her istendiğinde yeniden gerçekleştirildikleri anlamına gelir. 52. yinelemeye geldiğinizde orijinal güverteyi birçok kez yenilin. Bu davranışı göstermek için bir günlük yazalım. O zaman tamir edeceksin.

Dosyanızda `Extensions.cs` aşağıdaki yöntemi yazın veya kopyalayın. Bu uzantı yöntemi, proje `debug.log` dizininizde adı verilen yeni bir dosya oluşturur ve günlük dosyasına şu anda yürütülmekte olan sorguyu kaydeder. Bu uzantı yöntemi, sorgunun yürütüldettiğini işaretlemek için herhangi bir sorguya eklenebilir.

[!CODE-csharp[LogQuery](../../../samples/snippets/csharp/getting-started/console-linq/extensions.cs?name=snippet3)]

Altında `File`kırmızı bir dalgalı göreceksiniz, yani öyle bir şey yok. Derleyici ne `File` olduğunu bilmediği için derleme yapmaz. Bu sorunu çözmek için, aşağıdaki kod satırını aşağıdaki ilk `Extensions.cs`satırın altına eklediğinizden emin olun:

```csharp
using System.IO;
```

Bu sorunu çözmek gerekir ve kırmızı hata kaybolur.

Ardından, günlük iletisi ile her sorgunun tanımını enstrüman:

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

Bir sorguya her erişimede günlüğe kaydetmediğinize dikkat edin. Yalnızca özgün sorguyu oluşturduğunuzda oturum açarsınız. Program hala çalıştırmak için uzun bir zaman alır, ama şimdi neden görebilirsiniz. Giriş açıkken in shuffle çalıştıran sabrınız biterse, çıkış shuffle'ına geri geçin. Hala tembel değerlendirme etkilerini göreceksiniz. Bir çalıştırmada, tüm değer ve takım elbise oluşturma dahil olmak üzere 2592 sorgu yürütür.

Yaptığınız yürütme sayısını azaltmak için burada kodun performansını artırabilirsiniz. Yapabileceğiniz basit bir düzeltme, kart destesini oluşturan orijinal LINQ sorgusunun sonuçlarını *önbelleğe* almaktır. Şu anda, do-while döngüsü bir yinelemeden geçse, kart destesini yeniden oluşturup her seferinde yeniden karıştırarak sorguları tekrar tekrar yürütesiniz. Kart destesini önbelleğe almak için LINQ <xref:System.Linq.Enumerable.ToArray%2A> <xref:System.Linq.Enumerable.ToList%2A>yöntemlerinden ve; Sorguları eklediğinizde, onlara söylediğiniz eylemleri gerçekleştirirler, ancak şimdi aramayı seçtiğiniz yönteme bağlı olarak sonuçları bir dizi veya liste halinde depolarlar. Linq yöntemini <xref:System.Linq.Enumerable.ToArray%2A> her iki sorguya de ekleyip programı yeniden çalıştırın:

[!CODE-csharp[Main](../../../samples/snippets/csharp/getting-started/console-linq/Program.cs?name=snippet1)]

Şimdi çıkış karışıklığı 30 sorguya düştü. In shuffle ile yeniden çalıştırın ve benzer iyileştirmeler görürsünüz: şimdi 162 sorguları yürütür.

Bu örneğin, tembel değerlendirmenin performans güçlüklerine neden olabileceği kullanım örneklerini vurgulamak için **tasarlandığına** dikkat edin. Tembel değerlendirmenin kod performansını nerede etkileebileceğini görmek önemli olsa da, tüm sorguların hevesle çalışmaması gerektiğini anlamak da aynı derecede önemlidir. Kullanmadan maruz kalmanızı <xref:System.Linq.Enumerable.ToArray%2A> sağlar, çünkü kart destesinin her yeni düzenlemesi önceki düzenlemeden oluşturulmuştür. Tembel değerlendirme kullanarak her yeni güverte yapılandırması orijinal güverteden inşa edilir `startingDeck`anlamına gelir, hatta inşa kodu yürütme . Bu da büyük miktarda ekstra çalışmaya neden olur.

Uygulamada, bazı algoritmalar istekli değerlendirme kullanarak iyi çalışır ve diğerleri tembel değerlendirme kullanarak iyi çalıştırın. Günlük kullanım için, veri kaynağı ayrı bir işlem olduğunda, veritabanı altyapısı gibi tembel değerlendirme genellikle daha iyi bir seçimdir. Veritabanları için, tembel değerlendirme daha karmaşık sorguları veritabanı işlemine yalnızca bir gidiş-dönüş yürütmek ve kodunuzun geri dönmek için izin verir. LINQ ister tembel ister istekli değerlendirmeyi kullanmayı seçseniz de esnektir, bu nedenle süreçlerinizi ölçün ve size en iyi performansı veren değerlendirme türünü seçin.

## <a name="conclusion"></a>Sonuç

Bu projede şunları ele alasınız:

- verileri anlamlı bir sıraya toplamak için LINQ sorgularını kullanma
- LINQ sorgularına kendi özel işlevselliğimizi eklemek için Uzantı yöntemleri yazma
- kurallarımızda LINQ sorgularımızın bozulmuş hız gibi performans sorunlarıyla karşılaşabileceği alanları bulma
- LINQ sorguları ve sorgu performansı üzerindeki etkileri açısından tembel ve istekli değerlendirme

Linq dışında, sihirbazların kart numaraları için kullandıkları bir teknik hakkında biraz bilgi edindin. Sihirbazlar Faro karışıklığını kullanırlar çünkü destedeki her kartın nereye gittiğini kontrol edebilirler. Artık bildiğine göre, herkes için bunu mahvetme!

LINQ hakkında daha fazla bilgi için bkz:

- [Dil ile Tümleşik Sorgu (LINQ)](../programming-guide/concepts/linq/index.md)
- [LINQ'ye Giriş](../programming-guide/concepts/linq/index.md)
- [Temel LINQ Sorgu İşlemleri (C#)](../programming-guide/concepts/linq/basic-linq-query-operations.md)
- [LINQ ile Veri Dönüşümleri (C#)](../programming-guide/concepts/linq/data-transformations-with-linq.md)
- [LINQ'te Sorgu Sözdizimi ve Yöntem Sözdizimi (C#)](../programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md)
- [LINQ'i Destekleyen C# Özellikleri](../programming-guide/concepts/linq/features-that-support-linq.md)
