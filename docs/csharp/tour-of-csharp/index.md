---
title: C# ' ta - turu bir C# Kılavuzu
description: C# yeni misiniz? Dil temelleri öğrenin.
ms.date: 08/10/2016
ms.assetid: ebc727cd-8112-42e7-b59c-3c2873ad661c
ms.openlocfilehash: bdb8a84083b391c27d39f5c566a01b2db318123f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="a-tour-of-the-c-language"></a>C# dili turu  

C# (okunur "Bkz Sharp") bir basit, modern, nesne yönelimli ve tür kullanımı uyumlu programlama dilidir. C# dil C ailesinde kendi kökleri sahiptir ve C, C++, Java ve JavaScript hemen programcıları olacaktır.

C# nesne yönelimli bir dil olmakla birlikte, C# daha fazla için destek içerir ***bileşen yönelimli*** programlama. Çağdaş yazılım tasarımı giderek kendi içinde bulunan ve kendiliğinden açıklayıcı paketleri işlevlerin biçiminde yazılım bileşenleri kullanır. Bu tür bileşenleri bunlar bir programlama modeli özellikleri, yöntemleri ve olayları sunmasını anahtarıdır; bileşenle ilgili tanımlayıcı bilgiler sağlayan öznitelikler sahip oldukları; ve kendi belgelerinin içerecek. C# dili doğrudan bu kavramlar desteklemek için yapılandırmalarını C# oluşturmak ve yazılım bileşenleri kullanmak üzere çok doğal dil yapmak sağlar.

Sağlam ve sağlam uygulamalar yapısında birkaç C# özelliklerini yardımcı: ***çöp toplama*** ulaşılamaz kullanılmayan nesneler tarafından; kapladığı bellek otomatik olarak kaldırsa ***özel durum işleme*** hata algılama ve kurtarma; yapılandırılmış ve Genişletilebilir bir yaklaşım sağlar ve ***tür kullanımı uyumlu*** dil tasarımını kılar gelen başlatılmamış okumak imkansız Dizin dizilerine kendi sınırları dışında ya da işaretsiz tür atamaları gerçekleştirmek için değişkenleri.

C# sahip bir ***tür sistemi birleşik***. İlkel türler gibi dahil tüm C# türleri, `int` ve `double`, tek bir kökünden devralır `object` türü. Bu nedenle, bir dizi ortak işlemleri tüm türleri paylaşır ve herhangi bir tür değerleri depolanan, taşınan ve bağlı tutarlı bir şekilde çalıştırılır. Ayrıca, C# kullanıcı tanımlı başvuru türleri ve değer türleri, nesnelerin dinamik ayırması ve aynı zamanda satır içi depolama basit yapıların izin vererek destekler.

C# programları ve kitaplıklarını zamanla uyumlu bir biçimde gelişmesi emin olmak için çok Vurgu üzerinde yerleştirildi ***sürüm*** C# ' ın tasarım. Birçok programlama dilleri bu sorun için çok az dikkat edin ve sonuç olarak, bu diller aranın bağımlı kitaplıkları gerekli olduğunda daha yeni sürümleri daha sık yazılmış programları sunulur. Sürüm oluşturma hususları doğrudan etkileyen C# ' ın tasarım yönlerini dahil ayrı `virtual` ve `override` değiştiricileri, yöntemi aşırı yükleme çözümü için kurallar ve açık arabirim üye bildirimleri için destek.

## <a name="hello-world"></a>Merhaba Dünya

"Hello, World" programı, geleneksel bir programlama dili tanıtmak için kullanılır. C# ' ta İşte:

[!code-csharp[Hello World](../../../samples/snippets/csharp/tour/hello/Program.cs#L1-L8)]

C# kaynak dosyaları genellikle dosya uzantısına sahip `.cs`. "Hello, World" program dosyasında depolanan varsayılarak `hello.cs`, programın komut satırı kullanılarak derlenmiş:

```console
csc hello.cs
```

hangi hello.exe adlı bir yürütülebilir derleme üretir. Çalışırken bu uygulama tarafından üretilen çıktısı şöyledir:

```console
Hello, World
```

> [!IMPORTANT]
> `csc` Komutunu tam Framework derlenir ve tüm platformlarda kullanılamayabilir.


"Hello, World" program ile başlayan bir `using` başvuruyor yönergesi `System` ad alanı. Ad alanları düzenleme C# programları ve kitaplıkları hiyerarşik bir yöntemdir. Ad alanları içeren türleri ve diğer ad — örneğin, `System` ad alanında türleri, bir dizi gibi `Console` program ve diğer ad alanları, bir dizi gibi başvurulan sınıfı `IO` ve `Collections`. A `using` belirli bir ad alanı referanslarını yönergesi bu ad alanı, üyesi türlerinin nitelenmemiş kullanımını etkinleştirir. Nedeniyle `using` program yönergesi kullanabilir `Console.WriteLine` için toplu olarak `System.Console.WriteLine`.

`Hello` "Hello, World" program tarafından bildirilen sınıfına sahip tek bir üyeyi adlı yöntemi `Main`. `Main` Yöntemi statik değiştirici ile bildirilmedi. Örnek yöntemleri anahtar sözcüğünü kullanarak belirli kapsayan nesne örneği başvurusu yapabilir sırada `this`, belirli bir nesneye başvuru olmadan statik yöntemler çalışmayabilir. Kurala göre bir statik yöntem adlı `Main` bir program giriş noktası olarak hizmet verir.

Programın çıkışı tarafından üretilen `WriteLine` yöntemi `Console` sınıfını `System` ad alanı. Bu sınıf, varsayılan olarak, otomatik olarak derleyici tarafından başvurulan standart sınıf kitaplıkları tarafından sağlanır.

C# hakkında bilgi edinmek için çok daha fazla yoktur.  Aşağıdaki konular, C# dili öğelerini genel bir bakış sağlar. Bu genel bakışlar dilin tüm öğeler hakkında temel bilgiler sağlar ve C# dili elemanlara daha derin çalışmak gerekli bilgileri verin:

* [Program Yapısı](program-structure.md)
    - C# dilinde anahtar kuruluş kavramları öğrenin: ***programları***, ***ad alanları***, ***türleri***, ***üyeleri***, ve  ***derlemeleri***.
* [Türler ve Değişkenler](types-and-variables.md)
    - Hakkında bilgi edinin ***değer türleri***, ***başvuru türleri***, ve ***değişkenleri*** C# dilinde.
* [İfadeler](expressions.md)
    - ***İfadeleri*** gelen oluşturulan ***işlenenler*** ve ***işleçleri***. İfadeler bir değer oluşturur.
* [Deyimler](statements.md)
    - Kullandığınız ***deyimleri*** bir programın Eylemler ifade etmek için.
* [Sınıflar ve nesneler](classes-and-objects.md)
    - ***Sınıfları*** olan en temel C# ' ın türü. ***Nesneleri*** sınıfının örnekleridir. Sınıfları kullanarak yerleşiktir ***üyeleri***, hangi da ele alınmıştır bu konuda.
* [Yapılar](structs.md)
    - ***Yapılar*** olan, sınıflar, aksine değer türleri veri yapılarını.
* [Diziler](arrays.md)
    - Bir ***dizi*** içeren bir dizi hesaplanan dizinlerini erişilen değişken bir veri yapısıdır.
* [Arabirimler](interfaces.md)
    - Bir ***arabirimi*** sınıflar ve yapılar tarafından uygulanan bir sözleşme tanımlar. Arabirim yöntemleri, özellikleri, olayları ve dizin oluşturucular içerebilir. Arabirim uygulamaları tanımladığı üyelerinin sağlamaz — yalnızca bir sınıf ya da arabirimini uygulayan yapının tarafından sağlanmalıdır üyeleri belirtir.
* [Sabit listeleri](enums.md)
    - Bir ***enum türü*** adlandırılmış sabitler kümesiyle ayrı değer türüdür.
* [Temsilciler](delegates.md)
    - A ***temsilci türü*** belirli bir parametre yöntemleriyle temsil başvuruları listesinde ve dönüş türü. Temsilciler yöntemleri değişkenleri için atanan ve parametre olarak geçirilen varlıklar olarak değerlendirmek mümkün kılar. Temsilciler diğer bazı dillerde bulunan işlev işaretçileri kavramı benzer, ancak işlev işaretçileri, nesne yönelimli ve tür kullanımı uyumlu temsilciler.
* [Öznitelikler](attributes.md)
    * ***Öznitelikleri*** türleri, üyeleri ve diğer varlıklar hakkında ek tanımlayıcı bilgileri belirtmek programları etkinleştirin.

>[!div class="step-by-step"]
[Next](program-structure.md)
