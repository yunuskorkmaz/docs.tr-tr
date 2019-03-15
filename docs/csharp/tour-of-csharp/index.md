---
title: 'Turu C# - C# Kılavuzu'
description: 'Yeni C#? Dilinin temellerini öğrenin.'
ms.date: 08/10/2016
ms.assetid: ebc727cd-8112-42e7-b59c-3c2873ad661c
---

# <a name="a-tour-of-the-c-language"></a>Turu C# dil

C# (okunur "Bkz Sharp") bir basit, modern, nesne yönelimli ve tür kullanımı uyumlu programlama dilidir. C#kendi kökleri dilleri C ailesinde vardır ve C, C++, Java ve JavaScript programcıları için hemen tanıdık gelecektir.

C#, nesne yönelimli bir dildir ancak C# daha fazla için destek içerir ***bileşen odaklı*** programlama. Çağdaş yazılım tasarımı giderek daha fazla işlevsellik müstakil ve kendiliğinden açıklayıcı paketleri biçiminde yazılım bileşenlerini kullanır. Bu bileşenler özellikleri, yöntemleri ve olayları ile bunların bir programlama modeli sunar, anahtarıdır; bileşen hakkında tanımlayıcı bilgiler sağlayan özniteliklerine sahip oldukları; ve bunlar kendi belgelerinin dahil edilip derecelendirilir. C#dil yapıları doğrudan yaparak, bu kavramları desteklemek için sağlar C# doğal dilde çok oluşturun ve yazılım bileşenlerini kullanın.

Birkaç C# ürettiği yapımı güçlü ve dayanıklı uygulamaların özellikleri: ***Çöp toplama*** otomatik olarak kullanılmayan erişilemeyen nesneler tarafından; kapladığı belleği geri kazanır ***özel durum işleme*** hata algılama ve kurtarma; yapılandırılmış ve Genişletilebilir bir yaklaşım sunan ve ***tür kullanımı uyumlu*** dilinin tasarım kılar imkansız başlatılmamış değişkenlerinden okuyun dizin için kendi sınırları ötesinde veya denetlenmeyen gerçekleştirmek için bir dizi yayınları yazın.

C# sahip bir ***tür sistemi birleşik***. Gibi ilkel türler dahil olmak üzere tüm C# türü, `int` ve `double`, tek bir kök devral `object` türü. Bu nedenle, bir dizi ortak işlemlerini tüm türleri paylaşın ve herhangi bir tür değerleri depolanan, taşınan ve tutarlı bir şekilde üzerinde işlem. Ayrıca, C# hem kullanıcı tarafından tanımlanan başvuru türleri ve değer türleri, nesnelerin dinamik ayırması yanı sıra basit yapılar satır içi depolanmasını sağlayan destekler.

Emin olmak için C# programlar ve kitaplıklar evrim Geçiren zamanla uyumlu bir şekilde, çok Vurgu yerleştirilir ***sürüm*** içinde C#kullanıcının tasarlayın. Birçok programlama dili bu sorun için çok az dikkat edin ve sonuç olarak, bu dillerin sonu bağımlı kitaplıkları gerekli olduğunda daha yeni sürümleri daha sık yazılan programlar sunulmuştur. Yönlerini C#kullanıcının sürüm hususları doğrudan etkileyen tasarım dahil ayrı `virtual` ve `override` değiştiriciler, yöntem aşırı yükleme çözümlemesi için kurallar ve açık arabirim üyesi bildirimi için destek.

## <a name="hello-world"></a>Merhaba Dünya

"Hello, World" programı, geleneksel bir programlama dili tanıtmak için kullanılır. Bunu C# ' de şu şekildedir:

[!code-csharp[Hello World](../../../samples/snippets/csharp/tour/hello/Program.cs#L1-L8)]

C# kaynak dosyaları, genellikle dosya uzantısına sahip `.cs`. "Hello, World" program dosyasında depolanan varsayarak `hello.cs`, programın komut satırı kullanılarak derlenmiş:

```console
csc hello.cs
```

hangi hello.exe adlı yürütülebilir bir derleme oluşturur. Çalıştırıldığında, bu uygulama tarafından üretilen çıktı.

```console
Hello, World
```

> [!IMPORTANT]
> `csc` Tam Framework komut ve tüm platformlarda kullanılamayabilir.


"Hello, World" programı ile başlayan bir `using` başvuran yönergesi `System` ad alanı. Ad alanlarında, C# programları ve kitaplıkları düzenleme, hiyerarşik bir yöntem sağlar. Ad alanları, türler ve diğer ad alanları içerir — örneğin, `System` ad alanı içeren bir dizi türleri gibi `Console` program ve diğer ad alanları, bir sayı gibi başvurulan sınıfı `IO` ve `Collections`. A `using` belirtilen bir ad alanı başvuruyor yönergesi bu ad alanının üyeleri olan türlerinin nitelenmemiş kullanımı sağlar. Nedeniyle `using` yönerge, programın kullanabilirsiniz `Console.WriteLine` için kısayol olarak `System.Console.WriteLine`.

`Hello` "Hello, World" program tarafından bildirilen adlı yöntem tek bir üye sınıfında `Main`. `Main` Yöntemi statik değiştiriciyle bildirildi. Örnek yöntemleri anahtar sözcüğü kullanılarak belirli kapsayan nesne örneği başvurabilirsiniz ancak `this`, belirli bir nesneye başvuru olmadan statik yöntemleri çalışır. Kural gereği, adlı statik bir yöntemi `Main` bir programın giriş noktası olarak görev yapar.

Program çıktısı tarafından üretilen `WriteLine` yöntemi `Console` sınıfını `System` ad alanı. Bu sınıf, varsayılan olarak, derleyici tarafından otomatik olarak başvurulur, standart sınıf kitaplıkları tarafından sağlanır.

Hakkında bilgi edinmek için çok daha fazla C#.  Aşağıdaki konularda öğelerinin genel bir bakış C# dili. Bu genel bakışlar dilinin tüm öğeleri hakkında temel bilgiler sağlar ve ayrıntılar daha kapsamlı öğeleri için gerekli bilgileri size C# dil:

* [Program Yapısı](program-structure.md)
    - Kuruluş temel kavramları öğrenin C# dil: ***programlar***, ***ad alanları***, ***türleri***, ***üyeleri***ve ***derlemeleri***.
* [Türler ve Değişkenler](types-and-variables.md)
    - Hakkında bilgi edinin ***değer türleri***, ***başvuru türleri***, ve ***değişkenleri*** içinde C# dili.
* [İfadeler](expressions.md)
    - ***İfadeleri*** oluşturulan ***işlenenler*** ve ***işleçleri***. İfade bir değer üretir.
* [Deyimler](statements.md)
    - Kullandığınız ***deyimleri*** eylemleri bir programın ifade etmek için.
* [Sınıflar ve nesneler](classes-and-objects.md)
    - ***Sınıflar*** olan en temel C# türü. ***Nesneleri*** sınıfının örnekleridir. Sınıflar kullanılarak oluşturulur ***üyeleri***, hangi de ele alınmıştır bölümüne bakın.
* [Yapılar](structs.md)
    - ***Yapılar*** , farklı sınıflar, değer türleri veri yapılarını.
* [Diziler](arrays.md)
    - Bir ***dizi*** hesaplanan dizinlerini erişilen değişken bir sayı içeren bir veri yapısıdır.
* [Arabirimler](interfaces.md)
    - Bir ***arabirimi*** sınıfları ve yapıları tarafından uygulanan bir sözleşmeyi tanımlar. Bir arabirim yöntemleri, özellikleri, olayları ve dizin oluşturucular içerebilir. Bir arabirim tanımlar üyelerinin uygulamalarını sağlamaz; yalnızca bir sınıf ya da arabirimi uygulayan yapının tarafından sağlanması gereken üyeleri belirtir.
* [Sabit listeleri](enums.md)
    - Bir ***sabit listesi türü*** adlandırılmış sabitler kümesini içeren farklı bir değer türüdür.
* [Temsilciler](delegates.md)
    - A ***temsilci türü*** belirli bir parametre olan yöntemlere başvuruları temsil listesi ve dönüş türü. Temsilciler, yöntemleri değişkenine atanır ve parametre olarak geçirilen varlıklar olarak değerlendirmek mümkün kılar. Diğer dillerde bulunan işlev işaretçileri kavramı temsilcileri benzerdir ancak işlev işaretçileri, nesne yönelimli ve tür kullanımı uyumlu temsilciler.
* [Öznitelikler](attributes.md)
     * ***Öznitelikleri*** programları türleri, üyeleri ve diğer varlıkları hakkında daha fazla bildirim temelli bilgi belirtmek etkinleştirin.

> [!div class="step-by-step"]
> [Next](program-structure.md)
