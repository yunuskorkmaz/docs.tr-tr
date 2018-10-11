---
title: LINQ ile çalışma
description: Bu öğreticide LINQ ile dizileri oluşturmak, yöntemleri kullanmak için LINQ sorguları yazma ve eager ve geç değerlendirme arasında ayrım öğretir.
ms.date: 03/28/2017
ms.assetid: 0db12548-82cb-4903-ac88-13103d70aa77
ms.openlocfilehash: dc5f6cc4fd38b32f54a576a3947187cbed4e70e8
ms.sourcegitcommit: 2eb5ca4956231c1a0efd34b6a9cab6153a5438af
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/11/2018
ms.locfileid: "49086758"
---
# <a name="working-with-linq"></a>LINQ ile çalışma

## <a name="introduction"></a>Giriş

Bu öğretici, .NET Core ve C# dili özellikleri sayısı öğretir. Şunları öğreneceksiniz:

*   LINQ ile dizileri oluşturma
*   Nasıl kolayca kullanılabilecek yöntemleri LINQ sorguları yazma.
*   İstekli ve geç değerlendirme arasında ayrım yapma.

Tüm magician temel becerilerini birini gösteren bir uygulama oluşturarak bu tekniklerini öğreneceksiniz: [faro shuffle](https://en.wikipedia.org/wiki/Faro_shuffle). Kısaca, faro shuffle burada yarıya birden tam olarak bir kart Destesi bölün ve ardından her yarım özgün Destesi yeniden oluşturmak için her bir karttaki shuffle karışır bir tekniktir.

Magicians, her kart sonra her shuffle bilinen bir konumda olan ve yinelenen bir desen sırasıdır olduğundan bu tekniği kullanın. 

Amaçlarımız doğrultusunda, bu veri dizisi düzenleme ışık hearted göz olur. Oluşturacağınız uygulama Kart destesi oluşturmak ve ardından her zaman sırası yazma seçeneği, bir dizi gerçekleştirin. Ayrıca, özgün sırasını güncelleştirilmiş siparişe karşılaştıracağız.

Bu öğreticide, birden fazla adım vardır. Her adımdan sonra uygulamayı çalıştırmak ve ilerleme durumuna bakın. Ayrıca bkz [tamamlanan örnek](https://github.com/dotnet/samples/blob/master/csharp/getting-started/console-linq) dotnet/samples GitHub deposunda. Yükleme yönergeleri için bkz: [örnekler ve öğreticiler](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

## <a name="prerequisites"></a>Önkoşullar

.NET core çalıştırmak için makinenizi ayarlamak gerekir. Yükleme yönergelerini bulabilirsiniz [.NET Core](https://www.microsoft.com/net/core) sayfası. Bu uygulama, Windows, Ubuntu Linux, OS X veya Docker kapsayıcısı çalıştırabilirsiniz. Sık kullandığınız Kod Düzenleyicisi'ni yüklemeniz gerekir. Aşağıdaki tanımlamalar [Visual Studio Code](https://code.visualstudio.com/) açık kaynaklı, çapraz platform Düzenleyicisi olduğu. Ancak, rahat sevdiğiniz araçları kullanabilirsiniz.

## <a name="create-the-application"></a>Uygulama oluşturma

İlk adım, yeni bir uygulama oluşturmaktır. Bir komut istemi açın ve uygulamanız için yeni bir dizin oluşturun. Bu, geçerli bir dizin oluşturun. Komut türü `dotnet new console` komut isteminde. Bu, temel bir "Hello World" uygulaması için başlangıç dosyaları oluşturur.

C# daha önce kullanmadıysanız [Bu öğreticide](console-teleprompter.md) bir C# programı yapısını açıklar. Okuma ve LINQ hakkında daha fazla bilgi edinmek için buraya dönün. 

## <a name="creating-the-data-set"></a>Veri kümesi oluşturma

Bir deste oluşturarak başlayalım. Bu iki kaynağı (dört için uygun, on üç değerleri için bir tane) sahip bir LINQ Sorgu kullanarak yaparsınız. Bir 52 Kart destesi kaynaklarda birleştirmeniz. A `Console.WriteLine` deyimi içinde bir `foreach` döngü kartlarını görüntüler.

Sorguyu şu şekildedir:

```csharp
var startingDeck = from s in Suits()
                   from r in Ranks()
                   select new { Suit = s, Rank = r };

foreach (var c in startingDeck)
{
    Console.WriteLine(c);
}
```

Birden çok `from` yan tümceleri üreten bir `SelectMany`, ilk dizideki her öğe ikinci dizideki her öğe birleşiminden tek bir dizisi oluşturulur. Sıralama amaçlarımız doğrultusunda büyük/küçük harf önemlidir. İlk kaynak sırası (cins) içindeki ilk öğeye (değerler) ikinci dizideki her öğe ile birleştirilir. Bu ilk uyacak tüm On üç kartları oluşturur. Bu işlem, (cins) ilk dizideki her öğe tekrarlanır. Bitiş değerleri tarafından izlenen cins göre sıralanmış bir deste sonucudur.

Ardından, Suits() ve Ranks() yöntemler oluşturmak gerekir. Gerçekten basit bir dizi ile başlayalım *yineleyici yöntemleri* olarak dizeler dizisi oluşturur:

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

Bu iki yöntem her iki yazılımınız `yield return` çalıştırılmakta olan bir dizi oluşturmak için söz dizimi. Derleyici uygulayan bir nesne oluşturur `IEnumerable<T>` ve bunların istendiği gibi dize sırası üretir.

Bu derleme aşağıdaki iki satırı dosyasının en üstüne eklemeniz gerekir:

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
```

Devam edip bu noktada derlediğiniz örneği çalıştırın. Tüm 52 kartları deste içinde görüntüler. Gözlemlemek için hata ayıklayıcı altında bu örneği çalıştırmak çok yararlı bulabilirsiniz nasıl `Suits()` ve `Values()` bir yöntem yürütülemez. Yalnızca gerektiği gibi her bir dizideki her bir dizenin oluşturulan açıkça görebilirsiniz.

![52 kartları yazma uygulamayı gösteren konsol penceresi](./media/working-with-linq/console.png)

## <a name="manipulating-the-order"></a>Sipariş işleme

Ardından, karışık gerçekleştirebilirsiniz bir yardımcı yöntem oluşturalım. İlk adım, iki Destesi bölme sağlamaktır. `Take()` Ve `Skip()` LINQ API'leri parçası olan yöntemler bizim için bu özelliği sağlar:

```csharp
var top = startingDeck.Take(26);
var bottom = startingDeck.Skip(26);
```

Shuffle yöntemi, kendi yazmak zorunda standart kitaplıkta mevcut değil. Bu yeni yöntem LINQ tabanlı programlarla Haydi kullanacağınız çeşitli teknikler gösterir adımları yöntemi her bir parçasının açıklanmaktadır.

Yöntem imzası oluşturur bir *genişletme yöntemi*:

```csharp
public static IEnumerable<T> InterleaveSequenceWith<T>
    (this IEnumerable<T> first, IEnumerable<T> second)
```

Özel bir amaç için bir genişletme yöntemi olduğunu *statik yöntem.* Ek gördüğünüz `this` yöntemin ilk bağımsız değişkeni değiştiricisi. İşlevmiş gibi bir üye yöntemi ilk bağımsız değişken türünü yöntem çağrısı anlamına gelir.

Genişletme yöntemleri, yalnızca içinde bildirilebilir `static` sınıfları, Haydi adlı yeni bir statik sınıf oluşturma `extensions` bu işlevselliği. Daha fazla genişletme yöntemleri, bu öğreticiye devam edin ve bunları aynı sınıf içinde yerleştirileceği ekleyeceksiniz.

Ayrıca bu yöntem bildiriminde girdi ve çıktı türleri nerede standart bir deyim izleyen `IEnumerable<T>`. Uygulama zincirlenmesine izin LINQ yöntemleri sağlayan daha karmaşık sorgular birlikte gerçekleştirilecek.

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

Aynı anda hem dizileri numaralandırma, öğelerin Interleaving ve bir nesne oluşturma.  Bir LINQ yazma iki sıralarıyla birlikte çalışarak yöntemi anladığınızdan gerektirir. nasıl `IEnumerable` çalışır.

`IEnumerable` Arabirimi bir yöntemi vardır: `GetEnumerator()`. Tarafından döndürülen nesne `GetEnumerator()` sonraki öğeyi ve dizideki geçerli öğe alır. bir özellik taşımak için bir yöntemi vardır. Bu iki üyeler toplamasını ve öğeleri döndürmek için kullanır. Bu ayırma yöntemi, bir yineleyici yöntemini olacak bir koleksiyon oluşturma ve koleksiyon döndürmek yerine kullanacaksınız böylece `yield return` yukarıda gösterilen sözdizimi. 

Bu yöntemin uygulanmasını şu şekildedir:

[!CODE-csharp[InterleaveSequenceWith](../../../samples/csharp/getting-started/console-linq/extensions.cs?name=snippet1)]

Bu yöntem, yazdığınız, dönün `Main` yöntemi ve karışık bir kez Destesi:

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

Kaç seçeneği Destesi ayarlamak için gereken kendi özgün siparişe geri görelim. İki sıranın eşit olup olmadığını belirleyen bir yöntem yazmaktır gerekir. Bu yöntem sonra seçimdeki Destesi bir döngüde arkanıza Destesi geri sırayla olduğunda kontrol edin kodu gerekir.

İki sıranın eşit olup olmadığını belirlemek için bir yöntem yazma basit olması gerekir. Destesi karıştırmak için yazdığınız yöntemine benzer bir yapıdır. Yalnızca bu kez, her öğe iade verimi yerine, her dizinin eşleşen öğeleri karşılaştıracağız. Her bir öğe eşleşmiyorsa dizinin tamamıyla, numaralandırılmış olduğunda, dizileri aynıdır:

[!CODE-csharp[SequenceEquals](../../../samples/csharp/getting-started/console-linq/extensions.cs?name=snippet2)]

Bu ikinci bir LINQ deyim gösterir: terminal yöntemleri. Bunlar bir dizisi giriş olarak (veya bu durumda, iki sıranın) alır ve tek bir sayı değerini döndürür. Kullanıldığında, bu yöntemlerin her zaman son sorguda yöntemdir. (Bu nedenle adı). 

Destesi özgün sırayla olduğunda belirlemek için kullandığınızda, bu eylem görebilirsiniz. Bir döngü içinde karışık kod ve sıra özgün sırayla uygulayarak olduğunda Dur `SequenceEquals()` yöntemi. Bir dizi yerine tek bir değer döndürdüğünden, her zaman son yöntemi herhangi bir sorgu olacaktır görebilirsiniz:

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

Örneği çalıştırmak ve nasıl 8 yinelemeden sonra orijinal yapılandırmasına için dönene kadar her çalmayı Destesi düzenlemelerinin bakın.

## <a name="optimizations"></a>En iyi duruma getirme

Yapılandırdığınıza kadar örnek yürüten bir *shuffle kullanıma*, burada üst ve alt kartları her çalıştırma aynı kalır. Birini değiştirin ve çalıştırın olalım bir *karışık olarak*burada tüm 52 kart konumu değiştirin. İçinde bir karışık için ilk kart böylece alt yarısında Destesi Interleave Destesi ilk kartta olur. Üst kısmında son kartın altındaki kartı haline gelir anlamına gelir. Bu yalnızca bir satır farklıdır. Destesi üst ve alt yarısının sırasını değiştirmek için geri çağrı güncelleştirin:

```csharp
shuffle = shuffle.Skip(26).InterleaveSequenceWith(shuffle.Take(26));
```

Programı yeniden çalıştırın ve kendisini yeniden sıralamak Destesi için 52 yinelemeler alan görürsünüz. Bazı önemli performans performansındaki düşüşleri program çalışmaya devam ettikçe fark etmeye başlayacaksınız.

Bunun nedeni vardır. Şimdi başlıca nedenlerinden üstesinden: verimsiz kullanılmasına *geç değerlendirme*.

LINQ sorguları gevşek değerlendirilir. Öğeleri yalnızca istendiğinde dizileri oluşturulur. Genellikle, önemli bir avantajı LINQ olmasıdır. Ancak, bu programı gibi bir kullanımda bu yürütme zamanı içinde hızlı büyümesine neden olur.

Özgün Destesi LINQ sorgusu kullanılarak oluşturuldu. Her shuffle önceki Destesi üzerinde üç LINQ sorguları uygulayarak oluşturulur. Tüm bu gevşek gerçekleştirilir. Bu, ayrıca bunların sırası istenen olarak yeniden her zaman gerçekleştirilir anlamına gelir. 52nd yinelemeye alma süresi, orijinal Destesi çoğu, birçok kez yeniden. Bu davranış göstermek için bir günlük yazalım. Ardından, bu çözeceksiniz.

Sorgu çalıştırılmış işaretlemek için herhangi bir sorgu için eklenmiş bir günlük yöntemi aşağıda verilmiştir.

[!CODE-csharp[LogQuery](../../../samples/csharp/getting-started/console-linq/extensions.cs?name=snippet3)]

Ardından, her bir günlük iletisine Sorgu tanımını izleme:

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

Bir sorguyu her eriştiğinde oturum yok dikkat edin. Özgün sorgu oluşturduğunuzda oturumunuzu açın. Program hala çalıştırmak uzun zaman alır, ancak artık neden görebilirsiniz. Çalıştırırsanız iç çalıştıran sabırdan açık günlük kaydı ile karışık, dış shuffle için geri geçin. Geç değerlendirme etkileri yine de görürsünüz. Tek bir çalıştırmada tüm değeri ve takım oluşturma dahil, 2592 sorgularını yürütür.

Bu yürütme önlemek için bu programı güncelleştirmek için kolay bir yolu yoktur. LINQ yöntemleri vardır `ToArray()` ve `ToList()` , neden sorgusu çalıştırma ve sonuçları bir dizi veya bir listedeki sırasıyla depolamak. Bu yöntemler yerine bir sorgu veri sonuçlarını önbelleğe kaynak sorguyu yeniden çalıştırmak için kullanın.  Kart desteleri çağrısıyla Oluştur sorguları Ekle `ToArray()` ve sorguyu yeniden çalıştırın:

[!CODE-csharp[Main](../../../samples/csharp/getting-started/console-linq/Program.cs?name=snippet1)]

Tekrar çalıştırın ve dış shuffle aşağı 30 sorgudur. İç karışık ile yeniden çalıştırın ve benzer geliştirmeleri göreceksiniz. (Bunu şimdi 162 sorguları yürüten).

Bu örnekte, tüm sorguları eagerly çalışması gerektiğini düşünmek tarafından hatalı yorumlayan yok. Bu örnek, geç değerlendirme performans zorluklarla neden olduğu durumlara vurgulamak için tasarlanmıştır. Önceki düzenlemeyi her yeni deste yerleşimini inşa edildiğinden olmasıdır. Geç değerlendirme kullanılması anlamına gelir her yeni Destesi yapılandırma bile yerleşik kod yürütülürken özgün Destesi oluşturulan `startingDeck`. Bu, çok miktarda ek iş neden olur. 

Uygulamada, bazı algoritmalar istekli değerlendirme kullanarak çok daha iyi ve diğerleri geç değerlendirme kullanarak çok daha iyi çalıştırın. (Veri kaynağı bir veritabanı altyapısı gibi ayrı bir işlem olduğunda genel olarak, geç değerlendirme çok daha iyi bir seçimdir. Bu gibi durumlarda, geç değerlendirme yalnızca bir gidiş dönüş için veritabanı işlemi yürütmek daha karmaşık sorgular etkinleştirir.) LINQ yavaş ve istekli değerlendirme sağlar. Ölçün ve en iyi seçenek seçin.

## <a name="preparing-for-new-features"></a>Yeni özellikler için hazırlama

Bu örnek için yazdığınız kodu işi yapan basit bir prototip oluşturmaya bir örnektir. Bu bir sorun alanı keşfetmek için harika bir yoludur ve birçok özellik için kalıcı en iyi çözüm olabilir. Kullanılabilir *anonim türler* kartlar ve her bir kartı temsil için dizeler.

*Anonim türler* birçok üretkenlik avantajı vardır. Bir sınıfı tanımlamanız gerekmez kendinize depolama temsil eder. Derleyici bu tür sizin için oluşturur. Derleyicinin ürettiği tür birçok basit veri nesneleri için en iyi yöntemler kullanır. Sahip *değişmez*, sonra oluşturduğu özelliklerini hiçbiri değiştirilebilir anlamına gelir. Anonim türler bir derlemeye iç olduğundan bu derleme için genel API bir parçası olarak görülen değildir. Anonim türler de içeren bir geçersiz kılma `ToString()` yönteminin her değeri ile biçimlendirilmiş bir dize döndürür.

Anonim türler de dezavantajları vardır. Dönüş değerleri ya da bağımsız değişkenler bunları kullanamazsınız şekilde erişilebilir adları, sahip değilsiniz. Yukarıdaki herhangi bir yöntem bu anonim türler kullanılan genel yöntemlerdir fark edeceksiniz. Geçersiz kılmasını `ToString()` uygulamanın daha fazla özellik büyüdükçe istediğinizi olmayabilir. 

Örnek, dizeleri ayrıca seri ve boyut sayısı her kart için kullanır. Oldukça bitişi açan olduğu. C# türünde sistem yararlanarak daha iyi kod yapmak bize yardımcı olabilecek `enum` türleri için bu değerleri.

Cins ile başlayın. Bunu kullanmak için uygun bir zamandır bir `enum`:

[!CODE-csharp[Suit enum](../../../samples/csharp/getting-started/console-linq/Program.cs?name=snippet2)]

`Suits()` Yöntemi ayrıca türü ve uygulama değiştirir:

[!CODE-csharp[Suit IEnumerable](../../../samples/csharp/getting-started/console-linq/Program.cs?name=snippet4)]

Ardından, kartların dereceye sahip aynı değişiklik yapın:

[!CODE-csharp[Rank enum](../../../samples/csharp/getting-started/console-linq/Program.cs?name=snippet3)]

Ve bunları oluşturan yöntemi:

[!CODE-csharp[Rank IEnumerable](../../../samples/csharp/getting-started/console-linq/Program.cs?name=snippet5)]

Bir son temizleme anonim bir tür üzerinde kalmak yerine, kartı temsil edecek bir tür olalım. Anonim türler basit, yerel türleri için kullanışlı olsa da bu örnekte, oyun kartı kavramlarla biridir. Somut bir türde olmalıdır.

[!CODE-csharp[PlayingCard](../../../samples/csharp/getting-started/console-linq/playingcard.cs?name=snippet1)]

Bu tür kullanan *otomatik uygulanan özellikler salt okunur* hangi Oluşturucu ayarlayın ve sonra değiştirilemez. Bunu yaptığı ayrıca kullanım [dize ilişkilendirme](../language-reference/tokens/interpolated.md) biçim dizesi çıkış kolaylaştırır özelliği.

Yeni türü kullanmak için başlangıç Destesi üreten bir sorgu güncelleştirin:

```csharp
var startingDeck = (from s in Suits().LogQuery("Suit Generation")
                    from r in Ranks().LogQuery("Value Generation")
                    select new PlayingCard(s, r))
                    .LogQuery("Starting Deck")
                    .ToArray();
```

Derleme ve yeniden çalıştırın. Çıkış biraz daha net ve kod biraz daha açıktır ve daha bir kolayca genişletilebilir.

## <a name="conclusion"></a>Sonuç

Bu örnek, LINQ to kullanılan yöntemlerden bazıları gösterdi, kodu LINQ ile kolayca kullanılacak kendi yöntemlerinizi oluşturma etkinleştirildi. Bu ayrıca, yavaş ve istekli değerlendirmesini ve performans üzerinde karar olan etkisi arasındaki farklar gösterilmiştir.

Bir magician'ın teknik hakkında biraz bilgi edindiniz. Her kart deste içinde geçtiği kontrol edebildiğiniz magicians faro shuffle kullanın. Bazı ipuçlarını magician bir kart Destesi üzerine yerleştirin bir hedef kitle üyenin ve burada bu kartı gider bilerek birkaç kez seçimdeki. Diğer İllüzyonları Destesi belirli bir yol ayarlamak gerektirir. Bir magician ux'in gerçekleştirmeden önce Destesi ayarlar. Ardından Filiz 5 kez bir dış karıştırma kullanarak Destesi karışık. Sahneye çıkarak, o rastgele bir deste gibi göründüğünü gösterir, 3 kez daha karışık ve tam olarak nasıl istediği ayarlamak Destesi sahip.
