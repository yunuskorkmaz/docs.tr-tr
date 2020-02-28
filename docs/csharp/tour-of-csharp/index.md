---
title: C# Kılavuz turu C#
description: Yeni C#misiniz? Dilin temel bilgilerini öğrenin.
ms.date: 04/05/2019
ms.openlocfilehash: b510342f957a259a6c7763441778461b3dd4ef1e
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/27/2020
ms.locfileid: "77673296"
---
# <a name="a-tour-of-the-c-language"></a>C# Dilin turu

C#("bkz. diyez") basit, modern, nesne odaklı ve tür açısından güvenli bir programlama dilidir. C#C 'nin dil ailesinde köklerine sahiptir ve C, C++, Java ve JavaScript programcıları için hemen tanıdık gelecektir.

Bu tur, C# 7 ve üzeri dilin önemli bileşenlerine genel bakış sunar. Etkileşimli örneklerle dili araştırmak istiyorsanız öğreticilere [giriş C# ](../tutorials/intro-to-csharp/index.md) ' i deneyin.

C#, nesne odaklı bir dildir, ancak C# daha fazla ***bileşen odaklı*** programlama desteğini içerir. Modern yazılım tasarımı giderek, yazılım bileşenlerini, kendi kendine içerilen ve kendi kendine açıklayan işlev paketleri biçiminde kullanır. Bu bileşenlere anahtar, özellikler, Yöntemler ve olaylar içeren bir programlama modeli sunduklarında; Bunlar, bileşen hakkında bildirime dayalı bilgiler sağlayan özniteliklere sahiptir; ve kendi belgelerini içerirler. C#, yazılım bileşenlerinin oluşturulması ve kullanılması için çok doğal bir C# dil sunarak, bu kavramları doğrudan desteklemek için dil yapıları sağlar.

Birçok C# Özellik sağlam ve dayanıklı uygulamalar oluşturmaya yardımcı olur: ***çöp toplama*** , erişilemeyen kullanılmayan nesneler tarafından kullanılan belleği otomatik olarak geri kazanır; ***özel durum işleme*** , hata algılama ve kurtarmaya yönelik yapılandırılmış ve genişletilebilir bir yaklaşım sağlar; dilin ***tür kullanımı uyumlu*** tasarımı, başlatılmamış değişkenlerden okumayı, sınırları ötesinde dizileri dizin haline getirmek veya Denetlenmemiş tür yayınları gerçekleştirmeyi olanaksız hale getirir.

C#Birleşik bir ***tür sistemine***sahiptir. `int` C# ve `double`gibi temel türler dahil olmak üzere tüm türler tek bir kök `object` türünden devralınır. Bu nedenle, tüm türler ortak işlemler kümesini paylaşır ve herhangi bir türdeki değerler tutarlı bir şekilde depolanabilir, taşınır ve çalıştırılabilir. Ayrıca, C# hem Kullanıcı tanımlı başvuru türlerini hem de değer türlerini destekler, bu da nesnelerin dinamik ayrılmasına ve basit yapıların satır içi depolamamasına olanak tanır.

Programlar ve kitaplıkların zaman içinde zaman içinde gelişebilmesini sağlamak için, tasarımına daha fazla vurgu konulmuştur. C# C# Birçok programlama dili bu sorunla ilgileniyor ve sonuç olarak, bu dillerde yazılmış programlar, bağımlı kitaplıkların daha yeni sürümleri tanıtıldığında gerekenden çok daha fazla. C#Sürüm oluşturma konuları tarafından doğrudan etkilenen tasarımın yönleri, ayrı `virtual` ve `override` değiştiricileri, yöntem aşırı yükleme çözümlemesi kurallarını ve açık arabirim üye bildirimleri için desteği içerir.

## <a name="hello-world"></a>Merhaba dünya

"Hello, World" programı, genellikle bir programlama dilini tanıtmak için kullanılır. Burada yer C#verilmiştir:

[!code-csharp[Hello World](~/samples/snippets/csharp/tour/hello/Program.cs)]

C#Kaynak dosyalar genellikle `.cs`dosya uzantısına sahiptir. "Hello, World" programının *Hello.cs*dosyasında depolandığını varsayarsak, program komut satırı kullanılarak derlenmiş olabilir:

```console
csc hello.cs
```

*Hello. exe*adlı bir yürütülebilir derleme üreten. Bu uygulama tarafından oluşturulan çıktı şu şekilde çalışır:

```console
Hello, World
```

> [!IMPORTANT]
> `csc` komutu tam Framework için derlenir ve tüm platformlarda bulunmayabilir.

"Hello, World" programı, `System` ad alanına başvuran bir `using` yönergesi ile başlar. Ad alanları, programları ve kitaplıkları düzenlemek C# için hiyerarşik bir yol sağlar. Ad alanları türler ve diğer ad alanlarını içerir — örneğin, `System` ad alanı, programda başvurulan `Console` sınıfı ve `IO` ve `Collections`gibi birçok farklı ad alanı gibi bir dizi tür içerir. Verilen bir ad alanına başvuran `using` yönergesi, bu ad alanının üyesi olan türlerin nitelenmemiş kullanımını mümkün değildir. `using` yönergesi nedeniyle, program `System.Console.WriteLine`için toplu `Console.WriteLine` kullanabilir.

"Hello, World" programı tarafından tanımlanan `Hello` sınıfı tek bir üyeye sahiptir ve `Main`adlı yöntem. `Main` yöntemi statik değiştiriciyle birlikte bildirilmiştir. Örnek yöntemleri, anahtar sözcük `this`kullanarak belirli bir kapsayan nesne örneğine başvurabilir, statik yöntemler belirli bir nesneye başvuru olmadan çalışır. Kurala göre, `Main` adlı statik bir yöntem, bir programın giriş noktası olarak işlev görür.

Programın çıktısı, `System` ad alanındaki `Console` sınıfının `WriteLine` yöntemi tarafından üretilir. Bu sınıf, varsayılan olarak derleyicinin otomatik olarak başvurduğu standart sınıf kitaplıkları tarafından sağlanır.

## <a name="elements-of-the-c-language"></a>C# Dilin öğeleri

Hakkında C#daha fazla bilgi edinmek için çok daha fazla şey vardır. Aşağıdaki konular, C# dilin öğelerine bir genel bakış sağlar. Bu genel bakışlar, dilin tüm öğeleriyle ilgili temel bilgileri sağlar ve daha ayrıntılı bilgi edinmek için gereken bilgileri verir:

- [Program Yapısı](program-structure.md)
  - C# Dilde temel kurumsal kavramları öğrenin: ***Programlar***, ***ad alanları***, ***türler***, ***Üyeler***ve ***derlemeler***.
- [Türler ve Değişkenler](types-and-variables.md)
  - Dildeki değer ***türleri***, ***başvuru türleri***ve değişkenler hakkında bilgi edinin. C#
- [İfadeler](expressions.md)
  - ***İfadeler*** , ***işlenenler*** ve ***işleçlerden***oluşturulur. İfadeler bir değer üretir.
- [Deyimler](statements.md)
  - Bir programın eylemlerini ifade etmek için ***deyimlerini*** kullanırsınız.
- [Sınıflar ve nesneler](classes-and-objects.md)
  - ***Sınıflar*** , türlerin en temel C#larıdır. ***Nesneler*** bir sınıfın örnekleridir. Sınıflar, bu konunun de ele alındığı ***Üyeler***kullanılarak oluşturulmuştur.
- [Diziler](arrays.md)
  - ***Dizi*** , hesaplanan dizinler üzerinden erişilen çeşitli değişkenler içeren bir veri yapısıdır.
- [Arabirimler](interfaces.md)
  - ***Arabirim*** , sınıflar ve yapılar tarafından uygulanabilecek bir sözleşmeyi tanımlar. Arabirim, Yöntemler, özellikler, olaylar ve Dizin oluşturucular içerebilir. Arabirim, tanımladığı üyelerin uygulamalarını sağlamaz; yalnızca arabirimini uygulayan sınıflar veya yapılar tarafından sağlanması gereken üyeleri belirtir.
- [Temsilciler](delegates.md)
  - Bir ***temsilci türü*** , belirli bir parametre listesi ve dönüş türü olan yöntemlere yapılan başvuruları temsil eder. Temsilciler, yöntemleri değişkenlere atanabilecek ve parametre olarak geçirilen varlıklar olarak işleme olanağı tanır. Temsilciler, bazı diğer dillerde bulunan işlev işaretçileri kavramına benzerdir, ancak işlev işaretçilerinden farklı olarak Temsilciler nesne yönelimli ve tür açısından güvenlidir.
- [Öznitelikler](attributes.md)
  - ***Öznitelikler*** , programların türler, Üyeler ve diğer varlıklar hakkında ek bildirime dayalı bilgiler belirtmesini sağlar.
  
> [!NOTE]
> Bu makaleler 7,0 ve C# üzeri sürümler için geçerlidir. Bazı özellikler, önceki sürümlerde kullanılamayabilir.

> [!div class="step-by-step"]
> [Next](program-structure.md)
