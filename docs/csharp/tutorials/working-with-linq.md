---
title: LINQ ile çalışma
description: Bu öğreticide LINQ ile dizileri oluşturmak, yöntemleri kullanmak için LINQ sorguları yazma ve eager ve geç değerlendirme arasında ayrım öğretir.
ms.date: 10/29/2018
ms.assetid: 0db12548-82cb-4903-ac88-13103d70aa77
ms.openlocfilehash: 702770650533b0549e414a1de87acf17d77af4e3
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/06/2019
ms.locfileid: "65063224"
---
# <a name="working-with-linq"></a>LINQ ile çalışma

## <a name="introduction"></a>Giriş

Bu öğretici, .NET core'da özelliklerini öğretir ve C# dili. Şunları öğreneceksiniz:

- LINQ ile dizileri oluşturma adımları.
- Nasıl kolayca kullanılabilecek yöntemleri LINQ sorguları yazma.
- İstekli ve geç değerlendirme arasında ayrım yapma.

Tüm magician temel becerilerini birini gösteren bir uygulama oluşturarak bu tekniklerini öğreneceksiniz: [faro shuffle](https://en.wikipedia.org/wiki/Faro_shuffle). Kısaca, faro shuffle burada yarıya birden tam olarak bir kart Destesi bölün ve ardından her yarım özgün Destesi yeniden oluşturmak için her bir karttaki shuffle karışır bir tekniktir.

Magicians, her kart sonra her shuffle bilinen bir konumda olan ve yinelenen bir desen sırasıdır olduğundan bu tekniği kullanın.

Amaçlarınız doğrultusunda, bu veri dizisi düzenleme ışık hearted göz olur. Oluşturacağınız uygulama Kart destesi oluşturmak ve ardından her zaman sırası yazma seçeneği, bir dizi gerçekleştirin. Ayrıca, özgün sırasını güncelleştirilmiş siparişe karşılaştıracağız.

Bu öğreticide, birden fazla adım vardır. Her adımdan sonra uygulamayı çalıştırmak ve ilerleme durumuna bakın. Ayrıca bkz [tamamlanan örnek](https://github.com/dotnet/samples/blob/master/csharp/getting-started/console-linq) dotnet/samples GitHub deposunda. Yükleme yönergeleri için bkz: [örnekler ve öğreticiler](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

## <a name="prerequisites"></a>Önkoşullar

.NET core çalıştırmak için makinenizi ayarlamak gerekir. Yükleme yönergelerini bulabilirsiniz [.NET Core](https://www.microsoft.com/net/core) sayfası. Bu uygulama, Windows, Ubuntu Linux, OS X veya Docker kapsayıcısı çalıştırabilirsiniz. Sık kullandığınız Kod Düzenleyicisi'ni yüklemeniz gerekir. Aşağıdaki tanımlamalar [Visual Studio Code](https://code.visualstudio.com/) açık kaynaklı, çapraz platform Düzenleyicisi olduğu. Ancak, rahat sevdiğiniz araçları kullanabilirsiniz.

## <a name="create-the-application"></a>Uygulama oluşturma

İlk adım, yeni bir uygulama oluşturmaktır. Bir komut istemi açın ve uygulamanız için yeni bir dizin oluşturun. Bu, geçerli bir dizin oluşturun. Komut türü `dotnet new console` komut isteminde. Bu, temel bir "Hello World" uygulaması için başlangıç dosyaları oluşturur.

C# daha önce kullanmadıysanız [Bu öğreticide](console-teleprompter.md) bir C# programı yapısını açıklar. Okuma ve LINQ hakkında daha fazla bilgi edinmek için buraya dönün.

## <a name="creating-the-data-set"></a>Veri kümesi oluşturma

Başlamadan önce aşağıdaki satırları başında olduğundan emin olun `Program.cs` tarafından oluşturulan dosya `dotnet new console`:

```csharp
// Program.cs
using System;
using System.Collections.Generic;
using System.Linq;
```

Bu üç satır varsa (`using` deyimleri) olmayan dosyasının en üstüne programımız derlenmez.

Tüm ihtiyacınız olacak başvuruları sahip olduğunuza göre bir deste nelerden göz önünde bulundurun. Genellikle, bir deste oyun dört cins varsa ve her seri On üç değerleri. Normalde, oluşturmayı düşünebilirsiniz bir `Card` uygulamalarımızın sağ kapalı sınıf ve koleksiyonu doldurma `Card` el ile nesneleri. LINQ ile ilgilenen bir deste oluştururken, her zamanki gibi daha kısa olabilir. Oluşturmak yerine bir `Card` sınıfı iki diziyi cins ve sıralamalar, sırasıyla göstermek için oluşturabilir. Gerçekten basit bir çift oluşturacaksınız [ *yineleyici yöntemleri* ](../iterators.md#enumeration-sources-with-iterator-methods) cins olarak ve derecelerini oluşturacağını <xref:System.Collections.Generic.IEnumerable%601>s dize:

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

Bunlar altındaki yerleştirmek `Main` yönteminde, `Program.cs` dosya. Bu iki yöntem her iki yazılımınız `yield return` çalıştırılmakta olan bir dizi oluşturmak için söz dizimi. Derleyici uygulayan bir nesne oluşturur <xref:System.Collections.Generic.IEnumerable%601> ve bunların istendiği gibi dize sırası üretir.

Şimdi bu yineleyici yöntemlerin deste oluşturmak için kullanın. LINQ sorgusu olarak ekleyeceğiniz bizim `Main` yöntemi. İncelememiz şu şekildedir:

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

Birden çok `from` yan tümceleri üreten bir <xref:System.Linq.Enumerable.SelectMany%2A>, ilk dizideki her öğe ikinci dizideki her öğe birleşiminden tek bir dizisi oluşturulur. Sıralama amaçlarımız doğrultusunda büyük/küçük harf önemlidir. İlk kaynak sırası (cins) içindeki ilk öğeye (sıralamalara sahip) ikinci dizideki her öğe ile birleştirilir. Bu ilk uyacak tüm On üç kartları oluşturur. Bu işlem, (cins) ilk dizideki her öğe tekrarlanır. Bitiş değerleri tarafından izlenen cins göre sıralanmış bir deste sonucudur.

Bunun yerine, yukarıda kullanılan sorgu söz dizimi LINQ yazılacak seçin veya yöntemi söz dizimini kullanın, akılda tutulması gereken önemli olduğu, söz dizimi bir biçimden diğerine diğerine gitmek her zaman mümkündür. Sorgu söz dizimi içinde yazılan yukarıdaki sorguda yöntem sözdizimi yazılabilir:

```csharp
var startingDeck = Suits().SelectMany(suit => Ranks().Select(rank => new { Suit = suit, Rank = rank }));
```

Derleyici, eşdeğer yöntemi çağrısı sözdizimine sorgu sözdizimi kullanılarak yazılsa LINQ deyimleriyle çevirir. Bu nedenle, söz dizimi seçiminizden bağımsız olarak sorgu iki sürümü aynı sonucu üretir. Hangi söz dizimi durumunuza en iyi şekilde çalışır seçin: zorluk yöntemi söz dizimi ile bazı üyeler sahip olduğu bir takımda çalışıyorsanız, sorgu söz dizimi kullanarak tercih ettiğiniz örneği için deneyin.

Devam edip bu noktada derlediğiniz örneği çalıştırın. Tüm 52 kartları deste içinde görüntüler. Gözlemlemek için hata ayıklayıcı altında bu örneği çalıştırmak çok yararlı bulabilirsiniz nasıl `Suits()` ve `Ranks()` bir yöntem yürütülemez. Yalnızca gerektiği gibi her bir dizideki her bir dizenin oluşturulan açıkça görebilirsiniz.

![52 kartları yazma uygulamayı gösteren bir konsol penceresi.](./media/working-with-linq/console-52-card-application.png)

## <a name="manipulating-the-order"></a>Sipariş işleme

Ardından, nasıl kullanıp kartları Karıştırılmasına gideceğinizi odaklanın. İlk adımda herhangi bir iyi shuffle Destesi iki bölme sağlamaktır. <xref:System.Linq.Enumerable.Take%2A> Ve <xref:System.Linq.Enumerable.Skip%2A> LINQ API'leri parçası olan yöntemler sizin için bu özelliği sağlar. Bunları altındaki yerleştirmek `foreach` döngü:

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

Ancak, kendi yazmak zorunda standart kitaplıkta avantajlarından yararlanmak için karışık yöntemi yoktur. Bu işlem her bir parçasının adımlarda açıklanacaktır böylece LINQ tabanlı programlar ile kullanacağınız çeşitli teknikler, oluşturduğunuz shuffle yöntemi gösterir.

Nasıl etkileşim için bazı işlevler eklemek amacıyla <xref:System.Collections.Generic.IEnumerable%601> LINQ sorguları döneceğiz, bazı özel tür adı verilen yöntemler yazmak ihtiyacınız olacak [genişletme yöntemleri](../../csharp/programming-guide/classes-and-structs/extension-methods.md). Kısaca, özel amaçlı bir genişletme yöntemi olduğunu *statik yöntem* ekleyen yeni işlevler için zaten varolan bir tür işlevselliği için eklemek istediğiniz özgün türünü değiştirmek zorunda kalmadan.

Yeni bir ekleyerek yeni bir giriş, genişletme yöntemleri sağlar *statik* programınız için sınıf dosyası adında `Extensions.cs`ve ardından ilk bulunan uzantı yöntemine oluşturmaya başlayın:

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

Yöntem imzası bir süre için özel olarak parametreleri bakın:

```csharp
public static IEnumerable<T> InterleaveSequenceWith<T> (this IEnumerable<T> first, IEnumerable<T> second)
```

Ek gördüğünüz `this` yöntemin ilk bağımsız değişkeni değiştiricisi. İşlevmiş gibi bir üye yöntemi ilk bağımsız değişken türünü yöntem çağrısı anlamına gelir. Ayrıca bu yöntem bildiriminde girdi ve çıktı türleri nerede standart bir deyim izleyen `IEnumerable<T>`. Uygulama zincirlenmesine izin LINQ yöntemleri sağlayan daha karmaşık sorgular birlikte gerçekleştirilecek.

Doğal olarak, yarıları Destesi bölme olduğundan, bu yarıları birbirine birleştirmek gerekir. Kodda, numaralandırma aracılığıyla edinilen sıralarının her ikisi de başka bir deyişle <xref:System.Linq.Enumerable.Take%2A> ve <xref:System.Linq.Enumerable.Skip%2A> aynı anda *`interleaving`* öğeleri ve oluşturma bir sıralı:, şimdi karışık deste. Bir LINQ yazma iki sıralarıyla birlikte çalışarak yöntemi anladığınızdan gerektirir. nasıl <xref:System.Collections.Generic.IEnumerable%601> çalışır.

<xref:System.Collections.Generic.IEnumerable%601> Arabirimi bir yöntemi vardır: <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A>. Tarafından döndürülen nesne <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> sonraki öğeyi ve dizideki geçerli öğe alır. bir özellik taşımak için bir yöntemi vardır. Bu iki üyeler toplamasını ve öğeleri döndürmek için kullanır. Bu ayırma yöntemi, bir yineleyici yöntemini olacak bir koleksiyon oluşturma ve koleksiyon döndürmek yerine kullanacaksınız böylece `yield return` yukarıda gösterilen sözdizimi.

Bu yöntemin uygulanmasını şu şekildedir:

[!CODE-csharp[InterleaveSequenceWith](../../../samples/csharp/getting-started/console-linq/extensions.cs?name=snippet1)]

Bu yöntem, yazdığınız, dönün `Main` yöntemi ve karışık bir kez Destesi:

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

Kaç seçeneği Destesi ayarlamak için gereken kendi özgün siparişe yedekleme? Öğrenmek için iki diziyi eşit olup olmadığını belirleyen bir yöntem yazmaktır gerekir. Bu yöntem sonra seçimdeki Destesi bir döngüde arkanıza Destesi geri sırayla olduğunda kontrol edin kodu gerekir.

İki sıranın eşit olup olmadığını belirlemek için bir yöntem yazma basit olması gerekir. Destesi karıştırmak için yazdığınız yöntemine benzer bir yapıdır. Yalnızca bu zaman yerine `yield return`ing her öğe eşleşen her dizi öğelerini karşılaştıracağız. Her bir öğe eşleşmiyorsa dizinin tamamıyla, numaralandırılmış olduğunda, dizileri aynıdır:

[!CODE-csharp[SequenceEquals](../../../samples/csharp/getting-started/console-linq/extensions.cs?name=snippet2)]

Bu ikinci bir LINQ deyim gösterir: terminal yöntemleri. Bunlar bir dizisi giriş olarak (veya bu durumda, iki sıranın) alır ve tek bir sayı değerini döndürür. Terminal yöntemlerini kullanırken her zaman en son oldukları yöntemi bir LINQ yöntemleri zincirindeki sorgu, bu nedenle "terminal" adı.

Destesi özgün sırayla olduğunda belirlemek için kullandığınızda, bu eylem görebilirsiniz. Bir döngü içinde karışık kod ve sıra özgün sırayla uygulayarak olduğunda Dur `SequenceEquals()` yöntemi. Bir dizi yerine tek bir değer döndürdüğünden, her zaman son yöntemi herhangi bir sorgu olacaktır görebilirsiniz:

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

Şu ana kadar var ve Destesi her çalmayı nasıl yeniden düzenler, Not kodu çalıştırın. 8 seçeneği sonra (yineleme do-while döngüsü), Destesi olduğu içinde ilk başlangıç LINQ Sorgu oluşturduğunuz sırada ilk yapılandırmasına döndürür.

## <a name="optimizations"></a>En iyi duruma getirme

Yapılandırdığınıza kadar örnek yürüten bir *shuffle kullanıma*, burada üst ve alt kartları her çalıştırma aynı kalır. Bir değişiklik bakalım: kullanacağız bir *karışık olarak* bunun yerine, burada tüm 52 kartları değiştirmek konumu. İçinde bir karışık için ilk kart böylece alt yarısında Destesi Interleave Destesi ilk kartta olur. Üst kısmında son kartın altındaki kartı haline gelir anlamına gelir. Bu, tek satırlık bir kod için basit bir değişikliktir. Geçerli shuffle sorgu konumlarını geçerek güncelleştirme <xref:System.Linq.Enumerable.Take%2A> ve <xref:System.Linq.Enumerable.Skip%2A>. Bu Destesi üst ve alt yarısının sırasını değiştirir:

```csharp
shuffle = shuffle.Skip(26).InterleaveSequenceWith(shuffle.Take(26));
```

Programı yeniden çalıştırın ve kendisini yeniden sıralamak Destesi için 52 yinelemeler alan görürsünüz. Bazı önemli performans performansındaki düşüşleri program çalışmaya devam ettikçe fark etmeye başlayacaksınız.

Bunun nedeni vardır. Bu performans bırakma başlıca nedenlerinden üstesinden: verimsiz kullanılmasına [ *geç değerlendirme*](../programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).

Kısaca, geç değerlendirme değeri gerekli olana kadar bir deyimi değerlendirmesi gerçekleştirilmez belirtir. LINQ sorguları gevşek değerlendirilen ifadeleri ' dir. Öğeleri yalnızca istendiğinde dizileri oluşturulur. Genellikle, önemli bir avantajı LINQ olmasıdır. Ancak, bu programı gibi bir kullanımda bu yürütme zamanı içinde hızlı büyümesine neden olur.

Biz bir LINQ Sorgu kullanarak özgün Destesi oluşturulan unutmayın. Her shuffle önceki Destesi üzerinde üç LINQ sorguları uygulayarak oluşturulur. Tüm bu gevşek gerçekleştirilir. Bu, ayrıca bunların sırası istenen olarak yeniden her zaman gerçekleştirilir anlamına gelir. 52nd yinelemeye alma süresi, orijinal Destesi çoğu, birçok kez yeniden. Bu davranış göstermek için bir günlük yazalım. Ardından, bu çözeceksiniz.

İçinde `Extensions.cs` dosya yazın ya da aşağıdaki yöntemi kopyalayın. Bu genişletme yöntemi adlı yeni bir dosya oluşturur `debug.log` kayıtları ve proje dizini içinde hangi sorgu şu anda günlük dosyasına yapılıyor. Sorgu çalıştırılmış işaretlemek için herhangi bir sorgu için bir genişletme yöntemi bu eklenmesi.

[!CODE-csharp[LogQuery](../../../samples/csharp/getting-started/console-linq/extensions.cs?name=snippet3)]

Ardından, her bir günlük iletisine Sorgu tanımını izleme:

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

Bir sorguyu her eriştiğinde oturum yok dikkat edin. Özgün sorgu oluşturduğunuzda oturumunuzu açın. Program hala çalıştırmak uzun zaman alır, ancak artık neden görebilirsiniz. İçinde karışık açıktır, geçiş için geri dışı karışık günlüğü'yle çalıştıran sabırdan çalıştırırsanız. Geç değerlendirme etkileri yine de görürsünüz. Tek bir çalıştırmada tüm değeri ve takım oluşturma dahil, 2592 sorgularını yürütür.

Yaptığınız yürütme sayısını azaltmak için kodu buraya performansını artırabilir. Yapabilirsiniz basit bir düzeltme olmaktır *önbellek* deste oluşturan özgün LINQ sorgusunun sonuçları. Şu anda, sorguları yeniden ve her zaman do yürütüyorsunuz-döngü yineleme gerçekleştirirken deste yeniden oluşturmak ve her seferinde reshuffling. Deste önbelleğe almak için LINQ yöntemleri yararlanabilir <xref:System.Linq.Enumerable.ToArray%2A> ve <xref:System.Linq.Enumerable.ToList%2A>; sorgular ekleme, sizin bir uyarıyla bunları aynı eylemleri gerçekleştirmeniz, ancak bunlar bir dizideki veya listesi, hangi yöntemine bağlı olarak sonuçları artık depolayacağınızı çağırmak seçin. Append LINQ yöntemi <xref:System.Linq.Enumerable.ToArray%2A> hem sorgular, hem de yeniden programını çalıştırın:

[!CODE-csharp[Main](../../../samples/csharp/getting-started/console-linq/Program.cs?name=snippet1)]

Out shuffle aşağı 30 sorguları sunulmuştur. İçinde karışık ile yeniden çalıştırın ve benzer geliştirmeleri göreceksiniz: artık 162 sorguları yürütür.

Bu örnek olduğunu lütfen unutmayın. **tasarlanmış** geç değerlendirme neden olduğu performans zorluklarla kullanım örneklerini vurgulamaya. Burada geç değerlendirme kod performansını etkileyebilir görmek önemli olsa da, tüm sorguları eagerly çalışması gerektiğini anlamak aynı derecede önemlidir. Performans, isabet kullanmadan tabi <xref:System.Linq.Enumerable.ToArray%2A> önceki düzenlemeyi her yeni deste yerleşimini inşa edildiğinden olduğu. Geç değerlendirme kullanılması anlamına gelir her yeni Destesi yapılandırma bile yerleşik kod yürütülürken özgün Destesi oluşturulan `startingDeck`. Bu, çok miktarda ek iş neden olur.

Uygulamada, bazı algoritmalar istekli değerlendirme kullanılarak ve diğerleri de geç değerlendirme kullanarak çalıştırın. Veri kaynağı bir veritabanı altyapısı gibi ayrı bir işlem olduğunda günlük kullanım için geç değerlendirme genellikle daha iyi bir seçimdir. Veritabanları için yalnızca bir gidiş dönüş için veritabanı işlemi daha sonra tekrar kodunuzun kalanını yürütmek daha karmaşık sorgular geç değerlendirme sağlar. LINQ yavaş veya istekli değerlendirme kullanır, böylece işlemlerinizi ölçün ve hangi tür değerlendirme en iyi performansı sağlar çekmek üzere seçtiğiniz esnektir.

## <a name="conclusion"></a>Sonuç

Bu projede kapsamına:
- anlamlı bir dizisi veri toplama LINQ sorguları kullanma
- LINQ sorguları için kendi özel işlevsellik eklemek için uzantı metotları yazma
- hız düşürülmüş alanlar burada gibi performans sorunlarını bizim LINQ sorguları karşılaşabileceğiniz bizim kod bulma
- LINQ sorguları ve etkileri ilgili yavaş ve istekli değerlendirme sorgu performansı üzerindeki sahip olabilir

LINQ yanı sıra, biraz teknik magicians kullanımı için kart püf noktaları hakkında bilgi edindiniz. Her kart deste içinde geçtiği kontrol edebildiğiniz magicians Faro shuffle kullanın. Artık bildiğinize göre diğer herkes için spoil yok!

LINQ hakkında daha fazla bilgi için bkz:
- [Dil ile Tümleşik Sorgu (LINQ)](../programming-guide/concepts/linq/index.md)
  - [LINQ'e Giriş](../programming-guide/concepts/linq/introduction-to-linq.md)
  - [' De Lınq'e BaşlarkenC#](../programming-guide/concepts/linq/getting-started-with-linq.md)
    - [Temel LINQ Sorgu işlemleri (C#)](../programming-guide/concepts/linq/basic-linq-query-operations.md)
    - [LINQ ile veri dönüştürmeler (C#)](../programming-guide/concepts/linq/data-transformations-with-linq.md)
    - [Sorgu sözdizimi ve yöntem sözdizimi LINQ (C#)](../programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md)
    - [LINQ'i Destekleyen C# Özellikleri](../programming-guide/concepts/linq/features-that-support-linq.md)
