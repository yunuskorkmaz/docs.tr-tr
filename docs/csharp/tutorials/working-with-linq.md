---
title: LINQ ile çalışma
description: Bu öğretici LINQ sıralarıyla oluşturmak, kullanım için yöntemleri LINQ sorguları yazma ve istekli ve geç değerlendirme arasında ayrım öğretir.
ms.date: 03/28/2017
ms.assetid: 0db12548-82cb-4903-ac88-13103d70aa77
ms.openlocfilehash: 17c294a372a05a05d3893fce7b3adc426c6305fd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="working-with-linq"></a>LINQ ile çalışma

## <a name="introduction"></a>Giriş

Bu öğretici bir dizi özellik .NET Core ve C# dili öğretir. Şunları öğreneceksiniz:

*   LINQ ile sıraları oluşturma
*   Kolayca kullanılabilir yöntemleri LINQ sorguları yazma yapma.
*   İstekli ve geç değerlendirme arasında ayrım yapma.

Tüm magician temel becerileri birini gösteren bir uygulama oluşturarak bu tekniklerini öğreneceksiniz: [faro karışık](https://en.wikipedia.org/wiki/Faro_shuffle). Kısaca, faro karışık burada yarısı içinde tam olarak bir kart deste bölme ve ardından her bir özgün deste yeniden oluşturmak için her yarım kartından karışık interleaves bir tekniktir.

Magicians her karttır sonra her karışık bilinen bir konumda ve yinelenen bir desen sırasını olduğu için bu tekniği kullanın. 

Bizim, bu veri dizisi düzenleme bir ışık hearted göz amaçlıdır. Oluşturacağınız uygulama kartı deste oluşturun ve sonra her zaman sırası yazma seçeneği, bir dizi gerçekleştirin. Ayrıca orijinal siparişine güncelleştirilmiş sipariş karşılaştırın.

Bu öğretici, birden çok adım vardır. Her adımdan sonra uygulamayı çalıştırın ve ilerleme bakın. Ayrıca bkz [tamamlanan örnek](https://github.com/dotnet/samples/blob/master/csharp/getting-started/console-linq) dotnet/samples GitHub deposunda. Yükleme yönergeleri için bkz: [örnekler ve öğreticiler](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

## <a name="prerequisites"></a>Önkoşullar

.NET core çalışmasına, makine Kurulum gerekir. Yükleme yönergelerini bulabilirsiniz [.NET Core](https://www.microsoft.com/net/core) sayfası. Bu uygulama, Windows, Ubuntu Linux, OS X veya Docker kapsayıcısı çalıştırabilirsiniz. Sık kullanılan Kod Düzenleyicisi'ni yüklemeniz gerekir. Kullanım aşağıda açıklamaları [Visual Studio Code](https://code.visualstudio.com/) platform Düzenleyicisi arası bir açık kaynak olduğu. Ancak, tanımanız ne olursa olsun araçları kullanabilirsiniz.

## <a name="create-the-application"></a>Uygulama oluşturma

İlk adım, yeni bir uygulama oluşturmaktır. Bir komut istemi açın ve uygulamanız için yeni bir dizin oluşturun. Geçerli dizin oluşturun. Komut türü `dotnet new console` komut isteminde. Bu, temel bir "Hello World" uygulaması için başlangıç dosyaları oluşturur.

Hiç C# daha önce kullanmadıysanız [Bu öğretici](console-teleprompter.md) C# programının yapısını açıklar. Okuma ve LINQ hakkında daha fazla bilgi edinmek için buraya dönün. 

## <a name="creating-the-data-set"></a>Veri kümesi oluşturma

Bir deste oluşturarak başlayalım. Bu iki kaynaklarına (dört için uygun, on üç değerleri için bir tane) sahip bir LINQ Sorgu kullanarak gerçekleştirirsiniz. Bu kaynakları 52 kart deste birleştirmeniz. A `Console.WriteLine` deyimi içinde bir `foreach` döngü kartları görüntüler.

Sorgu şöyledir:

```csharp
var startingDeck = from s in Suits()
                   from r in Ranks()
                   select new { Suit = s, Rank = r };

foreach (var c in startingDeck)
{
    Console.WriteLine(c);
}
```

Birden çok `from` yan tümceleri üreten bir `SelectMany`, ilk dizisindeki her öğe ikinci dizideki her öğe ile birleştirerek tek bir dizi oluşturulur. Bizim amaçlar için sıralama önemlidir. İlk kaynak dizisi (Setleri) ilk öğe (değerler) ikinci dizisindeki her öğe ile birleştirilir. Bu ilk seri tüm On üç kartı oluşturur. Bu işlem, ilk sırada (Setleri) her bir öğesiyle yinelenir. Sonuç değerleri tarafından izlenen Setleri göre sıralanmış deste ' dir.

Ardından, Suits() ve Ranks() yöntemleri yapı gerekir. Çok basit bir dizi birlikte başlayalım *yineleyici metotları* olarak dizeler dizisi oluştur:

```csharp
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

Bu iki yöntem hem kullanan `yield return` çalıştıkları gibi bir dizi üretmek için sözdizimi. Arabirimini uygulayan bir nesneye derleyici derlemeler `IEnumerable<T>` ve bunların istendiği gibi bir dizi dize oluşturur.

Devam etmek ve bu noktada oluşturuncaya örneğini çalıştırın. Bunu tüm 52 kartları deste görüntüler. Bu örnek izlemek için bir hata ayıklayıcı altında çalıştırmak çok faydalı bulabileceğiniz nasıl `Suits()` ve `Values()` bir yöntem yürütülemez. Yalnızca gerektiği gibi her dizisindeki her dize oluşturulur açıkça görebilirsiniz.

![Out 52 kart yazma uygulamasını gösteren konsol penceresi](./media/working-with-linq/console.png)

## <a name="manipulating-the-order"></a>Sıra düzenleme

Ardından, şimdi karışık gerçekleştirebileceğiniz bir yardımcı program yöntemi oluşturun. İlk iki deste bölüneceği bir adımdır. `Take()` Ve `Skip()` LINQ API'leri parçası olan yöntemleri bize bu özelliği sağlar:

```csharp
var top = startingDeck.Take(26);
var bottom = startingDeck.Skip(26);
```

Kendi yazma gerekir böylece karışık yöntemi Standart kitaplığında yok. Bu yeni yöntemi LINQ tabanlı programlarla sağlandığından kullanacağınız çeşitli teknikler gösterilmektedir adımları yönteminde her bölümünü açıklar.

Yöntem için imza oluşturur bir *genişletme yöntemi*:

```csharp
public static IEnumerable<T> InterleaveSequenceWith<T>
    (this IEnumerable<T> first, IEnumerable<T> second)
```

Özel bir amaç için bir genişletme yöntemi olan *statik yöntemi.* Eklenmesi görebilirsiniz `this` yöntemi ilk bağımsız değişken değiştiricisi. Dizinindeymiş gibi ilk bağımsız değişkenin türünün üye yöntemi yöntemi çağırma anlamına gelir.

Genişletme yöntemleri, yalnızca içinde bildirilebilir `static` sağlandığından sınıfları adlı yeni bir statik sınıf oluşturmak `extensions` bu işlevsellik için. Bu öğretici devam etmek ve bu aynı sınıfta yerleştirilecek gibi daha fazla genişletme yöntemleri ekleyeceksiniz.

Ayrıca bu yöntem bildirimi giriş ve çıkış türleri nerede standart bir deyim izleyen `IEnumerable<T>`. Uygulama zincirlenmesine izin LINQ yöntemleri sağlar birlikte daha karmaşık sorgular gerçekleştirmek için.

```csharp
using System.Collections.Generic;

namespace LinqFaroShuffle
{
    public static class Extensions
    {
        public static IEnumerable<T> InterleaveSequenceWith<T>
            (this IEnumerable<T> first, IEnumerable<T> second)
        {
            // implementation coming.
        }
    }
}
```

Aynı anda hem sıraları numaralandırma, öğelerin Interleaving ve bir nesne oluşturma.  Bir LINQ yazma iki sıralarıyla birlikte çalışarak yöntemi anladığınızı gerektirir nasıl `IEnumerable` çalışır.

`IEnumerable` Arabirimi bir yöntem vardır: `GetEnumerator()`. Tarafından döndürülen nesne `GetEnumerator()` sonraki öğeye ve dizisi geçerli öğe alır bir özellik taşımak için bir yöntem vardır. Bu iki üyeler toplamasını ve öğeleri dönmek için kullanır. Bu ayırma yöntemi bir yineleyici yöntemi olacak bir koleksiyon oluşturma ve koleksiyonu döndüren yerine kullanacağınız şekilde `yield return` yukarıda gösterilen sözdizimi. 

Bu yöntemin kullanımı şöyledir:

[!CODE-csharp[InterleaveSequenceWith](../../../samples/csharp/getting-started/console-linq/extensions.cs?name=snippet1)]

Bu yöntem yazdıktan, geri dönüp `Main` yöntemi ve karışık bir kez deste:

```csharp
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

Kaç tane seçeneği deste ayarlamak için gereken özgün siparişe geri görelim. İki sıraları eşit olup olmadığını belirleyen bir yöntem yazmak gerekir. Bu yöntem aldıktan sonra döngü ve deste geri sırayla olduğunda denetleyin deste seçimdeki kod yerleştirmek gerekir.

İki sıraları eşit olup olmadığını belirlemek için bir yöntem yazma kolay olmalıdır. Deste karışık yazdığınız yöntemine benzer bir yapıdır. Yalnızca bu kez, her öğeye döndürme verim yerine, her dizinin eşleşen öğeleri karşılaştırmak. Her bir öğe eşleşmiyorsa tüm sırası, numaralandırılmış olduğunda, dizileri aynıdır:

[!CODE-csharp[SequenceEquals](../../../samples/csharp/getting-started/console-linq/extensions.cs?name=snippet2)]

Bu ikinci bir LINQ deyim gösterir: terminal yöntemleri. Bunlar bir dizi girişi olarak (veya bu durumda, iki sıraları) alın ve tek bir sayı değerini döndürür. Kullanıldığında, bu yöntemlerin her zaman son bir sorgunun bir yöntemdir. (Bu nedenle adı). 

Deste özgün sırayla olduğunda belirlemek için kullandığınızda, bu eylemde görebilirsiniz. Karışık kod döngü içinde koy ve dizisi özgün sırayla uygulayarak olduğunda Durdur `SequenceEquals()` yöntemi. Bir dizi yerine tek bir değer döndürdüğünden, her zaman herhangi bir sorgu son yönteminde olacaktır görebilirsiniz:

```csharp
var times = 0;
var shuffle = startingDeck;

do
{
    shuffle = shuffle.Take(26).InterleaveSequenceWith(shuffle.Skip(26));

    foreach (var c in shuffle)
    {
        Console.WriteLine(c);
    }

    Console.WriteLine();
    times++;
} while (!startingDeck.SequenceEquals(shuffle));

Console.WriteLine(times);
```

Örneği çalıştırmak ve 8 yinelemeden sonra orijinal yapılandırmasına döndürür kadar nasıl deste her çalmayı yeniden düzenler bakın.

## <a name="optimizations"></a>En iyi duruma getirme

Oluşturulan kadarki örnek yürüten bir *karışık olarak*, burada üst ve alt kartları her çalıştırmada aynı kalır. Bir değiştirin ve çalıştırın olalım bir *karışık çıkışı*, burada tüm 52 kartları konumunu değiştirme. Bir çıkış karışık için ilk kartı böylece alt yarısında deste Interleave deste ilk kart olur. Üst yarısındaki son kartı altındaki kartı hale anlamına gelir. Yalnızca tek bir çizgi değişiklik olmasıdır. Deste üst ve alt yarısının sırasını değiştirmek için karışık çağrısı güncelleştirin:

```csharp
shuffle = shuffle.Skip(26).InterleaveSequenceWith(shuffle.Take(26));
```

Programı yeniden çalıştırın ve kendisini yeniden sıralamak deste 52 yinelemeleri sürdüğünü görürsünüz. Program çalıştırmaya devam gibi bazı önemli performans degradations fark edilecek başlayacağız.

Bunun nedeni vardır. Şimdi başlıca nedenlerinden üstesinden gelmek: verimsiz kullanımı *geç değerlendirme*.

LINQ sorgularını gevşek değerlendirilir. Öğeleri yalnızca istendiği gibi dizileri üretilir. Genellikle, önemli bir avantajı LINQ olmasıdır. Ancak, bu programı gibi bir kullanımda bu yürütme süresini üstel artışa neden olur.

Özgün deste LINQ sorgusu kullanılarak oluşturuldu. Her karışık önceki deste üzerinde üç LINQ sorgularını gerçekleştirerek oluşturulur. Bunların tümü gevşek gerçekleştirilir. Ayrıca istenen sırası her zaman tekrar gerçekleştirilen anlamına gelir. 52nd yinelemeye alma zamanına göre özgün deste çoğu, birçok kez yeniden. Bu davranış göstermek için bir günlük yazalım. Ardından, onu düzeltmesi.

Sorgu yürütülür işaretlemek için herhangi bir sorgu için eklenen bir günlük yöntemi aşağıda verilmiştir.

[!CODE-csharp[LogQuery](../../../samples/csharp/getting-started/console-linq/extensions.cs?name=snippet3)]

Ardından, her bir günlük iletisine sorguyla tanımını izleme:

```csharp
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
        /*
        shuffle = shuffle.Take(26)
            .LogQuery("Top Half")
            .InterleaveSequenceWith(shuffle.Skip(26)
            .LogQuery("Bottom Half"))
            .LogQuery("Shuffle");
        */

        shuffle = shuffle.Skip(26)
            .LogQuery("Bottom Half")
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

Bir sorgu her eriştiğinde oturum yok dikkat edin. Yalnızca özgün sorgu oluşturduğunuzda, oturum açın. Program hala çalıştırmak için uzun bir zaman alır, ancak artık neden görebilirsiniz. Çalıştırırsanız açık günlük ile dış çalıştıran sabırdan karışık, geri iç karışık için geçin. Geç değerlendirme etkileri hala görürsünüz. Tek çalıştırmada tüm değer ve seri oluşturma gibi 2592 sorguları yürütür.

Bu yürütmeleri önlemek için bu programı güncelleştirmek için kolay bir yolu yoktur. LINQ yöntemlerdir `ToArray()` ve `ToList()` , sorguyu çalıştırmak neden ve sonuçları bir dizi veya bir liste, sırasıyla depolamak. Bu yöntemler bir sorgu veri sonuçlarını önbelleğe yerine kaynak sorguyu yeniden çalıştırmak için kullanın.  Ekleme çağrısıyla kartı deste oluşturmak sorgularını `ToArray()` ve sorguyu yeniden çalıştırın:

[!CODE-csharp[Main](../../../samples/csharp/getting-started/console-linq/Program.cs?name=snippet1)]

Yeniden çalıştırın ve iç karışık aşağıya doğru 30 sorgudur. Dış karışık ile yeniden çalıştırın ve benzer geliştirmeleri görürsünüz. (Bunu şimdi 162 sorguları yürüten).

Bu örnekte, tüm sorguları isteğini önleyebiliriz çalışması gerektiğini göz önünde tarafından hatalı yorumlayan yok. Bu örnek, geç değerlendirme performans sorunlar neden olduğu kullanım örnekleri vurgulamak için tasarlanmıştır. Her yeni deste düzenlenmesi önceki düzenlemeden diğerine oluşturulduğundan olmasıdır. Geç değerlendirme kullanılması anlamına gelir her yeni deste yapılandırma bile yerleşik kod yürütmek özgün deste yerleşik `startingDeck`. Bu, büyük miktarda ek iş neden olur. 

Uygulamada, bazı algoritmaları istekli değerlendirme kullanarak daha iyi ve diğerleri geç değerlendirme kullanarak daha iyi çalıştırın. (Veri kaynağı bir veritabanı motoru gibi ayrı bir işlem olduğunda genel olarak, geç değerlendirme kadar daha iyi bir seçimdir. Bu durumlarda, geç değerlendirme veritabanı işlemi için yalnızca bir gidiş dönüş yürütmek daha karmaşık sorgular etkinleştirir.) LINQ yavaş ve istekli değerlendirme sağlar. Ölçü ve en iyi seçenek seçin.

## <a name="preparing-for-new-features"></a>Yeni özellikler için hazırlama

Bu örnek için yazdığınız kodu işi halleder basit bir prototip oluşturma örneğidir. Bu bir sorun alanı keşfetmek için harika bir yoludur ve birçok özellik için en iyi kalıcı çözüm olabilir. İşlevden *anonim türler* kartları ve her kartı temsil edildiği için dizeler.

*Anonim türler* birçok üretkenlik avantajı vardır. Bir sınıf tanımlama gerekmez kendinize depolama temsil eder. Derleyici türü sizin için oluşturur. Oluşturulan derleyici türü çok basit veri nesneler için en iyi uygulamaları kullanır. Bunun *değişmez*, onu oluşturulan sonra özelliklerini hiçbiri değiştirilebileceği anlamına gelir. Anonim türler bir derlemeye iç olduğundan bu derleme için genel API'si bir parçası olarak görülen değil. Anonim türler de içeren bir geçersiz kılma `ToString()` yöntemi her değeri ile biçimlendirilmiş bir dize döndürür.

Anonim türler de dezavantajları vardır. Dönüş değerleri veya bağımsız olarak bunları kullanamazsınız şekilde erişilebilir adları sahip değilsiniz. Yukarıdaki herhangi bir yöntem bu anonim türler kullanılan genel yöntemlerdir fark edeceksiniz. Geçersiz kılma `ToString()` uygulamanın daha fazla özellik büyüdükçe istediğinizi olmayabilir. 

Örnek dizeleri her kart derecesini ve uyacak için de kullanır. Oldukça sona erdi açan değil. C# tür sistemi yararlanarak daha iyi bir kod olun yardımcı olabilecek `enum` türleri için bu değerleri.

Setleri ile başlatın. Bu kullanmak için uygun bir zamandır bir `enum`:

[!CODE-csharp[Suit enum](../../../samples/csharp/getting-started/console-linq/Program.cs?name=snippet2)]

`Suits()` Yöntemi de değişiklikleri türü ve uygulama:

[!CODE-csharp[Suit IEnumerable](../../../samples/csharp/getting-started/console-linq/Program.cs?name=snippet4)]

Ardından, kartları dereceye sahip aynı değişiklik yapın:

[!CODE-csharp[Rank enum](../../../samples/csharp/getting-started/console-linq/Program.cs?name=snippet3)]

Ve bunları oluşturan yöntem:

[!CODE-csharp[Rank IEnumerable](../../../samples/csharp/getting-started/console-linq/Program.cs?name=snippet5)]

Bir son temizleme anonim bir tür kalmak yerine, kartı temsil etmek için bir tür olalım. Anonim türler basit, yerel türleri için harika, ancak bu örnekte, oyun kartı kavramlarla biridir. Somut bir türde olmalıdır.

[!CODE-csharp[PlayingCard](../../../samples/csharp/getting-started/console-linq/playingcard.cs?name=snippet1)]

Bu tür kullanır *otomatik uygulanan salt okunur özellikler* oluşturucuda ayarlayın ve sonra değiştirilemez. Bunu yapar kullanımını da [dize ilişkilendirme](../language-reference/tokens/interpolated.md) biçim dizesi çıkışı kolaylaştırır özelliği.

Yeni türünü kullanmak için başlangıç deste üreten sorgu güncelleştirin:

```csharp
var startingDeck = (from s in Suits().LogQuery("Suit Generation")
                    from r in Ranks().LogQuery("Value Generation")
                    select new PlayingCard(s, r))
                    .LogQuery("Starting Deck")
                    .ToArray();
```

Derleme ve yeniden çalıştırın. Çıktı biraz temizleyici ve kod biraz daha açıktır ve daha kolay genişletilebilir.

## <a name="conclusion"></a>Sonuç

Bu örnek, LINQ kullanılan yöntemlerin bazıları gösterdi, kodu LINQ ile kolayca kullanılacak kendi yöntemleri oluşturmak nasıl etkinleştirildi. Bu ayrıca, yavaş ve istekli değerlendirme karar performans üzerinde olabilir etkisi arasındaki farkları gösterilmiştir.

Bir bit hakkında bir magician'ın tekniği de öğrendiniz. Burada, her kartı deste taşır kontrol sağladığından magicians faro karışık kullanın. Bazı ipuçlarını magician deste en üstünde bir kart yerleştirin bir izleyici üyenin ve burada bu kartı gider bilerek birkaç kez seçimdeki. Belirli bir yolla deste ayarlamak diğer İllüzyonları gerektirir. Bir magician eli gerçekleştirmeden önce deste ayarlar. Ardından aynen 5 kez iç karışık kullanarak deste karışık. Aşama üzerinde aynen rastgele deste gibi göründüğünü göster, 3 kez daha karışık ve tam olarak nasıl istediği ayarlamak deste sahip.
