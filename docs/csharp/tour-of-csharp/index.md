---
title: C# Turu - C# Rehberi
description: C#'da yeni misiniz? Dilin temellerini öğrenin.
ms.date: 02/26/2020
ms.openlocfilehash: bf5a200f2ee777698ae8564f348ffc117d9abab0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79156850"
---
# <a name="a-tour-of-the-c-language"></a>C# dilinde bir tur

C# ("Bkz. Sharp") modern, nesne yönelimli ve tür güvenli bir programlama dilidir. C#'nın kökleri C dil ailesine dayanır ve C, C++, Java ve JavaScript programcılarına hemen aşina olacaktır.

Bu tur, C# 8 ve daha önceki dilin ana bileşenlerine genel bir bakış sağlar. Dili etkileşimli örneklerle keşfetmek istiyorsanız, [C#](../tutorials/intro-to-csharp/index.md) öğreticilerine giriş yapmayı deneyin.

C# nesne yönelimli bir dildir, ancak C# bileşen ***yönelimli*** programlama desteği içerir. Çağdaş yazılım tasarımı giderek kendi kendine yeten ve kendi kendini tanımlayan işlevsellik paketleri şeklinde yazılım bileşenlerine dayanır. Bu bileşenlerin anahtarı, özellikleri, yöntemleri ve olayları içeren bir programlama modeli sunmalarıdır. Bunlar bileşen hakkında bildirimsel bilgi sağlayan öznitelikleri vardır. Kendi belgelerini dahil ediyorlar. C# bu kavramları doğrudan desteklemek için dil yapıları sağlayarak C#'ı yazılım bileşenlerinin oluşturulması ve kullanılması için doğal bir dil haline getirir.

Birkaç C# sağlam ve dayanıklı uygulamaların yapımında yardımcı özellikleri. ***Çöp toplama,*** erişileemeyen kullanılmayan nesneler tarafından işgal edilen belleği otomatik olarak geri alır. ***Özel durum işleme,*** hata algılama ve kurtarma için yapılandırılmış ve genişletilebilir bir yaklaşım sağlar. Dilin ***tür-güvenli*** tasarımı, başlatılmamış değişkenlerden okunmasını, dizileri sınırlarının ötesinde dizilere diziler oluşturmayı veya işaretlenmemiş tür dökümlerini gerçekleştirmeyi imkansız hale getirir.

C# birleşik bir ***tür sistemine***sahiptir. Gibi ilkel türleri de dahil olmak `int` `double`üzere tüm C# `object` türleri ve , tek bir kök türünden devral. Böylece, tüm türler ortak işlemler kümesini paylaşır ve her türden değerler tutarlı bir şekilde depolanabilir, taşınabilir ve çalıştırılabilir. Ayrıca, C# hem kullanıcı tarafından tanımlanan başvuru türlerini hem de değer türlerini destekleyerek nesnelerin dinamik olarak tahsisine ve hafif yapıların satır içi depolamasına olanak sağlar.

C# programlarının ve kitaplıklarının zaman içinde uyumlu bir şekilde gelişebilmesini sağlamak için, C#'ın tasarımında ***sürüm üzerinde*** çok fazla önem verilmiştir. Birçok programlama dili bu konuya çok az dikkat. Sonuç olarak, bağımlı kitaplıkların yeni sürümleri tanıtıldığında, diğer dillerde yazılan programlar gerekenden daha sık kırılır. C#'ın tasarımının doğrudan sürüm özelliklerinden etkilenen yönleri arasında `virtual` `override` ayrı ve değiştiriciler, yöntem aşırı yükleme çözümü kuralları ve açık arabirim üye bildirimleri desteği yer almaktadır.

Daha yeni sürümlerde, C# diğer programlama paradigmalarını benimsemiştir. C# lambda ifadeleri gibi fonksiyonel programlama tekniklerini destekleyen özellikler eklemiştir. Diğer yeni özellikler, desen eşleştirme gibi verileri ve algoritmaları ayıran desteği destekler.

## <a name="hello-world"></a>Merhaba dünya

"Hello, World" programı geleneksel olarak bir programlama dili tanıtmak için kullanılır. İşte C#' da:

[!code-csharp[Hello World](~/samples/snippets/csharp/tour/hello/Program.cs)]

C# kaynak dosyaları genellikle dosya `.cs`uzantısı var. Bu programı oluşturmak için, ilk indirin ve [.NET Çekirdek SDK](https://dotnet.microsoft.com/download)yükleyin. Ardından, yeni `dotnet new console -o hello` bir program ve yapı komut dosyası oluşturmak için komutu çalıştırın. Program ve yapı komut dosyası `Program.cs` `hello.csproj`dosyalarda ve sırasıyla bulunmaktadır. Uygulamayı `run` komutlarla oluşturur ve çalıştırın:

```dotnetcli
cd hello
dotnet run
```

Program aşağıdaki çıktıyı üretir:

```console
Hello, World!
```

"Hello, World" `using` `System` programı, ad alanına başvuran bir yönergeyle başlar. Ad alanları, C# programlarını ve kitaplıklarını düzenlemek için hiyerarşik bir araç sağlar. Ad alanları türleri ve diğer ad alanları `System` içerir-örneğin, ad alanı programda başvurulan `Console` sınıf gibi bir dizi tür ve `IO` diğer `Collections`ad alanları gibi bir dizi. Belirli `using` bir ad alanına başvuran bir yönerge, bu ad alanının üyesi olan türlerin niteliksiz kullanımına olanak tanır. `using` Yönerge nedeniyle, program için `Console.WriteLine` `System.Console.WriteLine`steno olarak kullanabilirsiniz.

"Hello, World" programı tarafından bildirilen `Hello` sınıfın tek bir `Main`üyesi vardır, adlı yöntem. Yöntem `Main` statik değiştirici ile bildirilir. Örnek yöntemleri anahtar sözcüğü `this`kullanarak belirli bir çevreleyen nesne örneğine başvuru yapabilse de, statik yöntemler belirli bir nesneye başvurmadan çalışır. Kural olarak, adlı `Main` statik bir yöntem bir programın giriş noktası olarak hizmet vermektedir.

Programın çıktısı `WriteLine` `Console` `System` ad alanında sınıfın yöntemi ile üretilir. Bu sınıf, varsayılan olarak derleyici tarafından otomatik olarak başvurulan standart sınıf kitaplıkları tarafından sağlanır.

## <a name="elements-of-the-c-language"></a>C# dilinin öğeleri

C# hakkında öğrenecek çok şey var. Aşağıdaki konular C# dilinin öğelerine genel bir bakış sağlar. Bu genel bakışlar, dilin tüm öğeleri hakkında temel bilgiler sağlar ve daha derine dalmak için gerekli bilgileri sağlar:

- [Program Yapısı](program-structure.md)
  - C# dilindeki temel kuruluş kavramlarını öğrenin: ***programlar,*** ***ad alanları,*** ***türleri,*** ***üyeler***ve ***derlemeler.***
- [Türler ve Değişkenler](types-and-variables.md)
  - C# ***dilindeki değer türleri,*** ***başvuru türleri***ve ***değişkenler*** hakkında bilgi edinin.
- [İfadeler](expressions.md)
  - ***İfadeler*** ***operands*** ve ***işleçler***inşa edilmiştir. İfadeler bir değer üretir.
- [Deyimler](statements.md)
  - Bir programın eylemlerini ifade etmek için ***deyimler*** kullanırsınız.
- [Sınıflar ve nesneler](classes-and-objects.md)
  - ***Sınıflar*** C# türlerinin en temelidir. ***Nesneler*** bir sınıfın örnekleridir. Sınıflar da bu konuda ele alınan ***üyeler***kullanılarak oluşturulur.
- [Diziler](arrays.md)
  - ***Dizi,*** hesaplanan endeksler aracılığıyla erişilen bir dizi değişken içeren bir veri yapısıdır.
- [Arabirimler](interfaces.md)
  - ***Arabirim,*** sınıflar ve structs tarafından uygulanabilen bir sözleşme tanımlar. Arabirim yöntemleri, özellikleri, olayları ve dizinleyicileri içerebilir. Arabirim, tanımladığı üyelerin uygulamalarını sağlamaz, yalnızca arabirimi uygulayan sınıflar veya yapıstları tarafından sağlanmalıdır.
- [Temsilciler](delegates.md)
  - ***Temsilci türü,*** belirli bir parametre listesi ve dönüş türüne sahip yöntemlere yapılan başvuruları temsil eder. Temsilciler, yöntemleri değişkenlere atanabilen ve parametre olarak geçirilebilen varlıklar olarak ele alabilen varlıklar olarak ele alabilmektir. Temsilciler, diğer bazı dillerde bulunan işlev işaretçileri kavramına benzer, ancak işlev işaretçilerin aksine, temsilciler nesne yönelimli ve tür güvenlidir.
- [Öznitelikler](attributes.md)
  - ***Öznitelikler,*** programların türler, üyeler ve diğer varlıklar hakkında ek bildirimsel bilgiler belirtmesini sağlar.
  
> [!NOTE]
> Bu makaleler C# 7.0 ve sonrası için geçerlidir. Bazı özellikler önceki sürümlerde kullanılamayabilir.

> [!div class="step-by-step"]
> [Sonraki](program-structure.md)
