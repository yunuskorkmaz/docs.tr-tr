---
title: C# Kılavuz turu C#
description: Yeni C#misiniz? Dilin temel bilgilerini öğrenin.
ms.date: 04/05/2019
ms.custom: seoapril2019
ms.openlocfilehash: eaaa5a259f0776a2749ed899d0406aee041a8442
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/28/2019
ms.locfileid: "70105658"
---
# <a name="a-tour-of-the-c-language"></a>C# Dilin turu

C#("bkz. diyez") basit, modern, nesne odaklı ve tür açısından güvenli bir programlama dilidir. C#C 'nin dil ailesinde köklerine sahiptir ve C, C++, Java ve JavaScript programcıları için hemen tanıdık gelecektir. Bu tur, dilin önemli bileşenlerine genel bir bakış sağlar. Etkileşimli örneklerle dili araştırmak isterseniz, öğreticilere [giriş C# ](../tutorials/intro-to-csharp/index.md) deneyimimizi deneyin.

C#, nesne odaklı bir dildir, ancak C# daha fazla ***bileşen odaklı*** programlama desteğini içerir. Modern yazılım tasarımı giderek, yazılım bileşenlerini, kendi kendine içerilen ve kendi kendine açıklayan işlev paketleri biçiminde kullanır. Bu bileşenlere anahtar, özellikler, Yöntemler ve olaylar içeren bir programlama modeli sunduklarında; Bunlar, bileşen hakkında bildirime dayalı bilgiler sağlayan özniteliklere sahiptir; ve kendi belgelerini içerirler. C#, yazılım bileşenlerinin oluşturulması ve kullanılması için çok doğal bir C# dil sunarak, bu kavramları doğrudan desteklemek için dil yapıları sağlar.

Birçok C# Özellik sağlam ve dayanıklı uygulamaların yapımasına yardımcı olur: ***Çöp toplama*** , erişilemeyen kullanılmayan nesneler tarafından kullanılan belleği otomatik olarak geri kazanır; ***özel durum işleme*** , hata algılama ve kurtarmaya yönelik yapılandırılmış ve genişletilebilir bir yaklaşım sağlar; dilin ***tür kullanımı uyumlu*** tasarımı, başlatılmamış değişkenlerden okumayı, sınırları ötesinde dizileri dizin haline getirmek veya Denetlenmemiş tür yayınları gerçekleştirmeyi olanaksız hale getirir.

C#Birleşik bir ***tür sistemine***sahiptir. `int` Ve `object` C# gibitemeltürlerdahilolmaküzeretümtürler,tekbirköktüründendevralınır.`double` Bu nedenle, tüm türler ortak işlemler kümesini paylaşır ve herhangi bir türdeki değerler tutarlı bir şekilde depolanabilir, taşınır ve çalıştırılabilir. Ayrıca, C# hem Kullanıcı tanımlı başvuru türlerini hem de değer türlerini destekler, bu da nesnelerin dinamik ayrılmasına ve basit yapıların satır içi depolamamasına olanak tanır.

Programlar ve kitaplıkların zaman içinde zaman içinde gelişebilmesini sağlamak için, tasarımına daha fazla vurgu konulmuştur. C# C# Birçok programlama dili bu sorunla ilgileniyor ve sonuç olarak, bu dillerde yazılmış programlar, bağımlı kitaplıkların daha yeni sürümleri tanıtıldığında gerekenden çok daha fazla. C#Sürüm oluşturma konuları tarafından doğrudan etkilenen tasarımın yönleri, ayrı `virtual` ve `override` değiştiriciler, yöntem aşırı yükleme çözümlemesi kuralları ve açık arabirim üye bildirimleri için destek içerir.

## <a name="hello-world"></a>Merhaba dünya

"Hello, World" programı, genellikle bir programlama dilini tanıtmak için kullanılır. Burada yer C#verilmiştir:

[!code-csharp[Hello World](../../../samples/snippets/csharp/tour/hello/Program.cs#L1-L8)]

C#Kaynak dosyalar genellikle dosya uzantısına `.cs`sahiptir. "Hello, World" programının dosyada `hello.cs`depolandığını varsayarak, program komut satırı kullanılarak derlenir:

```console
csc hello.cs
```

Hello. exe adlı bir yürütülebilir derleme üreten. Bu uygulama tarafından oluşturulan çıktı şu şekilde çalışır:

```console
Hello, World
```

> [!IMPORTANT]
> `csc` Komutu tam Framework için derlenir ve tüm platformlarda kullanılamayabilir.

"Hello, World" programı, `using` `System` ad alanına başvuran bir yönergeyle başlar. Ad alanları, programları ve kitaplıkları düzenlemek C# için hiyerarşik bir yol sağlar. Ad alanları türler ve diğer ad alanlarını içerir — örneğin, `System` ad alanı programda başvurulan `Console` sınıf gibi bir dizi tür içerir ve `IO` ve `Collections`gibi diğer ad alanları vardır. Verilen `using` bir ad alanına başvuruda bulunan bir yönerge, bu ad alanının üyesi olan türlerin nitelenmemiş kullanımını mümkün değildir. Yönergesi nedeniyle program, için `System.Console.WriteLine`toplu olarak kullanabilir `Console.WriteLine`. `using`

"Hello, World" programı tarafından belirtilen `Main` sınıftekbirüyeyesahiptir,yöntemiadlı.`Hello` `Main` Yöntemi statik değiştiriciyle birlikte bildirilmiştir. Örnek yöntemleri, anahtar sözcüğünü `this`kullanarak belirli bir kapsayan nesne örneğine başvurabilir, ancak statik yöntemler belirli bir nesneye başvuru olmadan çalışır. Kurala göre, adlı `Main` statik bir yöntem, bir programın giriş noktası olarak görev yapar.

Programın çıktısı, `WriteLine` `System` ad alanındaki `Console` sınıfının yöntemi tarafından üretilir. Bu sınıf, varsayılan olarak derleyicinin otomatik olarak başvurduğu standart sınıf kitaplıkları tarafından sağlanır.

Hakkında C#daha fazla bilgi edinmek için çok daha fazla şey vardır.  Aşağıdaki konular, C# dilin öğelerine bir genel bakış sağlar. Bu genel bakışlar, dilin tüm öğeleriyle ilgili temel bilgileri sağlar ve bu C# dilin öğelerine daha ayrıntılı bilgi edinmek için gereken bilgileri verir:

- [Program Yapısı](program-structure.md)
  - C# Dilde temel kurumsal kavramları öğrenin: ***Programlar***, ***ad alanları***, ***türler***, ***Üyeler***ve ***derlemeler***.
- [Türler ve Değişkenler](types-and-variables.md)
  - Dildeki değer ***türleri***, ***başvuru türleri***ve değişkenler hakkında bilgi edinin. C#
- [İfadeler](expressions.md)
  - ***İfadeler*** , ***işlenenler*** ve işleçlerdenoluşturulur. İfadeler bir değer üretir.
- [Deyimler](statements.md)
  - Bir programın eylemlerini ifade etmek için ***deyimlerini*** kullanırsınız.
- [Sınıflar ve nesneler](classes-and-objects.md)
  - ***Sınıflar*** , türlerin en temel C#larıdır. ***Nesneler*** bir sınıfın örnekleridir. Sınıflar, bu konunun de ele alındığı ***Üyeler***kullanılarak oluşturulmuştur.
- [Yapılar](structs.md)
  - ***Yapılar*** , sınıfların aksine değer türleri olan veri yapılarıdır.
- [Diziler](arrays.md)
  - ***Dizi*** , hesaplanan dizinler üzerinden erişilen çeşitli değişkenler içeren bir veri yapısıdır.
- [Arabirimler](interfaces.md)
  - ***Arabirim*** , sınıflar ve yapılar tarafından uygulanabilecek bir sözleşmeyi tanımlar. Arabirim, Yöntemler, özellikler, olaylar ve Dizin oluşturucular içerebilir. Arabirim, tanımladığı üyelerin uygulamalarını sağlamaz; yalnızca arabirimini uygulayan sınıflar veya yapılar tarafından sağlanması gereken üyeleri belirtir.
- [Sabit listeleri](enums.md)
  - ***Sabit listesi türü*** , adlandırılmış sabitler kümesi olan ayrı bir değer türüdür.
- [Temsilciler](delegates.md)
  - Bir ***temsilci türü*** , belirli bir parametre listesi ve dönüş türü olan yöntemlere yapılan başvuruları temsil eder. Temsilciler, yöntemleri değişkenlere atanabilecek ve parametre olarak geçirilen varlıklar olarak işleme olanağı tanır. Temsilciler, bazı diğer dillerde bulunan işlev işaretçileri kavramına benzerdir, ancak işlev işaretçilerinden farklı olarak Temsilciler nesne yönelimli ve tür açısından güvenlidir.
- [Öznitelikler](attributes.md)
  - ***Öznitelikler*** , programların türler, Üyeler ve diğer varlıklar hakkında ek bildirime dayalı bilgiler belirtmesini sağlar.

> [!div class="step-by-step"]
> [Next](program-structure.md)
