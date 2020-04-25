---
title: C#-C# Kılavuzu turu
description: C# ' ta yeni misiniz? Dilin temel bilgilerini öğrenin.
ms.date: 02/26/2020
ms.openlocfilehash: 7476356ceab39d5cccb6ccbeb991653f08a324ea
ms.sourcegitcommit: 839777281a281684a7e2906dccb3acd7f6a32023
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/24/2020
ms.locfileid: "82141040"
---
# <a name="a-tour-of-the-c-language"></a>C# dilinin turu

C# ("bkz. diyez") modern, nesne odaklı ve tür açısından güvenli bir programlama dilidir. C#, C ailesinin köklerine sahiptir ve C, C++, Java ve JavaScript programcıları için hemen tanıdık gelecektir.

Bu tur, C# 8 ve önceki sürümlerde dilin önemli bileşenlerine genel bakış sunar. Etkileşimli örneklerle dili araştırmak istiyorsanız C# öğreticilerine [giriş](../tutorials/intro-to-csharp/index.md) ' i deneyin.

C#, nesne odaklı bir dildir, ancak c# buna ek olarak ***bileşen odaklı*** programlama için destek içerir. Modern yazılım tasarımı giderek, yazılım bileşenlerini, kendi kendine içerilen ve kendi kendine açıklayan işlev paketleri biçiminde kullanır. Bu bileşenlere anahtar, özellikler, Yöntemler ve olaylar içeren bir programlama modeli sundukları özelliklerdir. Bunlar bileşen hakkında bildirime dayalı bilgiler sağlayan özniteliklere sahiptir. Kendi belgelerini içerirler. C#, doğrudan bu kavramları desteklemek için dil yapıları sağlar ve C# ' ı yazılım bileşenlerinin oluşturulması ve kullanılması için doğal bir dil yapar.

Birçok C# özelliği sağlam ve dayanıklı uygulamalar oluşturmaya yardımcı olur. ***Çöp toplama*** , erişilemeyen kullanılmayan nesneler tarafından kullanılan belleği otomatik olarak geri kazanır. ***Özel durum işleme*** , hata algılama ve kurtarmaya yönelik yapılandırılmış ve genişletilebilir bir yaklaşım sağlar. Dilin ***tür kullanımı uyumlu*** tasarımı, başlatılmamış değişkenlerden okumayı, sınırları ötesinde dizileri dizin haline getirmek veya Denetlenmemiş tür yayınları gerçekleştirmeyi olanaksız hale getirir.

C# Birleşik bir ***tür sistemine***sahiptir. Ve gibi temel türler dahil olmak üzere tüm C# türleri, tek bir kök `object` türünden devralınır. `double` `int` Bu nedenle, tüm türler ortak işlemler kümesini paylaşır ve herhangi bir türdeki değerler tutarlı bir şekilde depolanabilir, taşınır ve çalıştırılabilir. Ayrıca, C# hem Kullanıcı tanımlı başvuru türlerini hem de değer türlerini destekler, bu da nesnelerin dinamik ayrılmasına ve basit yapıların satır içi depolamamasına olanak tanır.

C# programlarının ve kitaplıklarının zaman içinde zaman içinde gelişebilmesini sağlamak için c# tasarımında ***sürüm oluşturma*** konusuna çok fazla vurgu konulmuştur. Birçok programlama dili bu sorunla ilgilenmeyi çok fazla ödeyin. Sonuç olarak, bu diğer dillerde yazılmış programlar, bağımlı kitaplıkların daha yeni sürümleri tanıtıldığında gerekenden daha sık kesilir. C# tasarımının sürüm oluşturma konuları tarafından doğrudan etkilenmiş olan yönleri, ayrı `virtual` ve `override` değiştiriciler, yöntem aşırı yükleme çözümlemesi kurallarını ve açık arabirim üyesi bildirimleri için desteği içerir.

C# ' nin daha yeni sürümlerinde, diğer programlama paradigmalarına daha fazla. C# lambda ifadeleri gibi işlevsel programlama tekniklerini destekleyen özellikleri içerir. Diğer yeni özellikler, model eşleştirme gibi verileri ve algoritmaları ayırmayı destekler.

## <a name="hello-world"></a>Merhaba dünya

"Hello, World" programı, genellikle bir programlama dilini tanıtmak için kullanılır. Burada C# ' de yer verilmiştir:

[!code-csharp[Hello World](~/samples/snippets/csharp/tour/hello/Program.cs)]

C# kaynak dosyaları genellikle dosya uzantısına `.cs`sahiptir. Bu programı oluşturmak için önce [.NET Core SDK](https://dotnet.microsoft.com/download)indirip yükleyin. Ardından, yeni bir program `dotnet new console -o hello` ve bir yapı betiği oluşturmak için komutunu yürütün. Program ve derleme betiği dosyalarında `Program.cs` ve `hello.csproj`sırasıyla. Uygulamayı şu `run` komutlarla derleyin ve çalıştırın:

```dotnetcli
cd hello
dotnet run
```

Program aşağıdaki çıktıyı üretir:

```dotnetcli
Hello, World!
```

"Hello, World" programı, `using` `System` ad alanına başvuran bir yönergeyle başlar. Ad alanları, C# programlarının ve kitaplıklarının düzenlenmesi için hiyerarşik bir yol sağlar. Ad alanları türler ve diğer ad alanlarını içerir — örneğin, `System` ad alanı programda başvurulan `Console` sınıf gibi bir dizi tür içerir ve `IO` ve `Collections`gibi diğer ad alanları vardır. Verilen `using` bir ad alanına başvuruda bulunan bir yönerge, bu ad alanının üyesi olan türlerin nitelenmemiş kullanımını mümkün değildir. `using` Yönergesi nedeniyle program, için `System.Console.WriteLine`toplu olarak kullanabilir `Console.WriteLine` .

" `Hello` Hello, World" programı tarafından belirtilen sınıf tek bir üyeye sahiptir, yöntemi adlı `Main`. `Main` Yöntemi statik değiştiriciyle birlikte bildirilmiştir. Örnek yöntemleri, anahtar sözcüğünü `this`kullanarak belirli bir kapsayan nesne örneğine başvurabilir, ancak statik yöntemler belirli bir nesneye başvuru olmadan çalışır. Kurala göre, adlı `Main` statik bir yöntem, bir programın giriş noktası olarak görev yapar.

Programın çıktısı, `WriteLine` `Console` `System` ad alanındaki sınıfının yöntemi tarafından üretilir. Bu sınıf, varsayılan olarak derleyicinin otomatik olarak başvurduğu standart sınıf kitaplıkları tarafından sağlanır.

## <a name="elements-of-the-c-language"></a>C# dilinin öğeleri

C# hakkında daha fazla bilgi edinmek için çok daha fazla şey vardır. Aşağıdaki konular C# dilinin öğelerine bir genel bakış sağlar. Bu genel bakışlar, dilin tüm öğeleriyle ilgili temel bilgileri sağlar ve daha ayrıntılı bilgi edinmek için gereken bilgileri verir:

- [Program Yapısı](program-structure.md)
  - C# dilinde temel kurumsal kavramları öğrenin: ***Programlar***, ***ad alanları***, ***türler***, ***Üyeler***ve ***derlemeler***.
- [Türler ve Değişkenler](types-and-variables.md)
  - C# dilinde ***değer türleri***, ***başvuru türleri***ve ***değişkenler*** hakkında bilgi edinin.
- [İfadeler](expressions.md)
  - ***İfadeler*** , ***işlenenler*** ve ***işleçlerden***oluşturulur. İfadeler bir değer üretir.
- [Deyimler](statements.md)
  - Bir programın eylemlerini ifade etmek için ***deyimlerini*** kullanırsınız.
- [Sınıflar ve nesneler](classes-and-objects.md)
  - ***Sınıflar*** C# türlerinin en temel larıdır. ***Nesneler*** bir sınıfın örnekleridir. Sınıflar, bu konunun de ele alındığı ***Üyeler***kullanılarak oluşturulmuştur.
- [Diziler](arrays.md)
  - ***Dizi*** , hesaplanan dizinler üzerinden erişilen çeşitli değişkenler içeren bir veri yapısıdır.
- [Arabirimler](interfaces.md)
  - ***Arabirim*** , sınıflar ve yapılar tarafından uygulanabilecek bir sözleşmeyi tanımlar. Arabirim, Yöntemler, özellikler, olaylar ve Dizin oluşturucular içerebilir. Arabirim, tanımladığı üyelerin uygulamalarını sağlamaz; yalnızca arabirimini uygulayan sınıflar veya yapılar tarafından sağlanması gereken üyeleri belirtir.
- [Temsilciler](delegates.md)
  - Bir ***temsilci türü*** , belirli bir parametre listesi ve dönüş türü olan yöntemlere yapılan başvuruları temsil eder. Temsilciler, yöntemleri değişkenlere atanabilecek ve parametre olarak geçirilen varlıklar olarak işleme olanağı tanır. Temsilciler, bazı diğer dillerde bulunan işlev işaretçileri kavramına benzerdir, ancak işlev işaretçilerinden farklı olarak Temsilciler nesne yönelimli ve tür açısından güvenlidir.
- [Öznitelikler](attributes.md)
  - ***Öznitelikler*** , programların türler, Üyeler ve diğer varlıklar hakkında ek bildirime dayalı bilgiler belirtmesini sağlar.
  
> [!NOTE]
> Bu makaleler C# 7,0 ve üzeri için geçerlidir. Bazı özellikler, önceki sürümlerde kullanılamayabilir.

> [!div class="step-by-step"]
> [Sonraki](program-structure.md)
