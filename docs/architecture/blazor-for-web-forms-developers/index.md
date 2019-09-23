---
title: ASP.NET Web Forms geliştiricileri için Blazor
description: Basit ve tanıdık bir şekilde Blazor ve .NET Core kullanarak .NET ile tam yığın Web uygulamaları oluşturmayı öğrenin.
author: danroth27
ms.author: daroth
ms.date: 09/11/2019
ms.openlocfilehash: a80483f6a1f1cb9e5a3e2ffff18cbd59c5b67af3
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71183800"
---
# <a name="blazor-for-aspnet-web-forms-developers"></a>ASP.NET Web Forms geliştiricileri için Blazor

![Sunucusuz uygulamalar eKitap kapağını gösteren ekran görüntüsü.](./media/index/blazor-for-web-forms-developers-cover.png)

> INDIRME:<https://aka.ms/blazor-ebook>

YAYIMLAYAN

Microsoft Geliştirici bölümü, .NET ve Visual Studio ürün ekipleri

Microsoft Corporation 'ın bir bölümü

One Microsoft Way

Redmond, Washington 98052-6399

Telif hakkı © 2019 Microsoft Corporation

Tüm hakları saklıdır. Bu kitabın içeriğinin herhangi bir bölümü herhangi bir biçimde veya herhangi bir şekilde veya başka bir şekilde herhangi bir şekilde çoğaltılamaz veya herhangi bir şekilde gönderilebilir.

Bu kitap, "olduğu gibi" verilmiştir ve yazarın görünümlerini ve opnons 'yi ifade eder. Bu kitapta ifade edilen görünümler, eklentiler ve bilgiler, URL ve diğer Internet Web sitesi başvuruları da dahil olmak üzere bildirimde bulunmaksızın değiştirilebilir.

Burada gösterilen bazı örnekler yalnızca gösterim amaçlıdır ve hayal ürünüdür. Hiçbir gerçek ilişkilendirme veya bağlantı amaçlanmaz veya çıkarsanmamalıdır.

Microsoft ve "ticari markalar" <https://www.microsoft.com> Web sayfasında listelenen ticari markalar, Microsoft şirketler grubunun ticari markalarıdır.

Mac ve macOS, Apple Inc. ' in ticari markalarıdır.

Diğer tüm işaretler ve amblemler kendi sahiplerinin mülkiyetindedir.

Düzenliyor

> **[Daniel Roth](https://github.com/danroth27)** , sorumlu Program Yöneticisi, Microsoft Corp.

> **[Jeff Fritz](https://github.com/csharpfritz)** , üst düzey Program Yöneticisi, Microsoft Corp.

> **[Taylor Güney Wick](https://github.com/twsouthwick)** , üst düzey yazılım mühendisi, Microsoft Corp.

> **[Scott Ade](https://github.com/scottaddie)** , üst düzey içerik Geliştirici, Microsoft Corp.

## <a name="introduction"></a>Giriş

.NET, ASP.NET aracılığıyla desteklenen Web uygulaması geliştirmeyi, her türlü Web uygulaması oluşturmak için kapsamlı bir çerçeve ve araç kümesi içerir. ASP.NET, klasik Active Server sayfalarına (ASP) kadar tüm Web çerçeveleri ve teknolojileri içeren kendi kökenini sahiptir. ASP.NET Web Forms, ASP.NET MVC, ASP.NET Web sayfaları ve daha yeni ASP.NET Core gibi çerçeveler, *sunucu tarafından işlenmiş* Web uygulamaları oluşturmaya yönelik üretken ve güçlü bir yol sağlar. burada, kullanıcı ARABIRIMI içeriği http 'e yanıt olarak sunucu üzerinde dinamik olarak oluşturulur. istekleri. Her bir ASP.NET çerçevesi, farklı bir hedef kitleye ve uygulama oluşturma felsekasında bulunur. ASP.NET Web Forms .NET Framework özgün sürümüyle birlikte sunulan ve basit olay işleme özellikli yeniden kullanılabilir kullanıcı arabirimi denetimleri gibi masaüstü geliştiricilere tanıdık olan çok sayıda desenden yararlanarak web geliştirmeyi etkin bir şekilde. Ancak, ASP.NET tekliflerinin hiçbiri kullanıcının tarayıcısında yürütülen kodu çalıştırmak için bir yol sağlamaz. Bunu yapmak için, JavaScript yazma ve yıl boyunca açık ve popüler olan birçok JavaScript çerçevesini ve araçlarından birini kullanmanızı gerektirir: jQuery, altını gizleme, angular, tepki verme ve benzeri.

[Blazor](https://blazor.net) , .NET ile Web uygulamaları oluştururken mümkün olan şeyleri değiştiren yeni bir Web çerçevesidir. Blazor, JavaScript C# yerine bir istemci tarafı Web UI çerçevesidir. Blazor ile istemci tarafı mantığınızı ve Kullanıcı arabirimi bileşenlerinizi ' de C#yazabilir, bunları normal .NET derlemelerine derleyebilir ve ardından WebAssembly adlı yeni bir açık web standardı kullanarak doğrudan tarayıcıda çalıştırabilirsiniz. Alternatif olarak, Blazor, .NET UI bileşenlerinizi sunucuda çalıştırabilir ve tarayıcı ile gerçek zamanlı bir bağlantı üzerinden tüm Kullanıcı arabirimi etkileşimlerini akıcı bir şekilde işleyebilir. Sunucu üzerinde çalışan .NET ile eşlendiğinde Blazor, .NET ile tam yığın Web geliştirmesini mümkün bir şekilde sunar. Blazor, ASP.NET Web Forms ile çok sayıda ortak paylaşır, ancak yeniden kullanılabilir bir bileşen modeli ve Kullanıcı olaylarını işlemek için basit bir yoldur. Ayrıca, modern ve yüksek performanslı bir Web geliştirme deneyimi sağlamak üzere .NET Core 'un temelleri de oluşturulur.

Bu kitap, ASP.NET Web Forms geliştiricilerin tanıdık ve kullanışlı bir şekilde Blazor tanıtır. Blazor kavramlarını, ASP.NET Web Forms 'teki benzer kavramlarla paralel olarak tanıtır, ayrıca daha az tanıdık olabilecek yeni kavramları de açıklamıştır. Bileşen yazma, yönlendirme, düzen, yapılandırma ve güvenlik dahil olmak üzere çok çeşitli konuları ve sorunları ele alır. Bu kitabın içeriği öncelikli olarak yeni geliştirmeyi etkinleştirmek için, var olan bir uygulamayı modernleştirin istediğinizde, mevcut ASP.NET Web Forms için Blazor 'e geçirmeye yönelik yönergeleri ve stratejileri de ele alır.

## <a name="who-should-use-the-book"></a>Kitabı kimler kullanmalıdır?

Bu kitap, var olan bilgi ve becerileriyle ilgili Blazor 'e giriş isteyen ASP.NET Web Forms geliştiricilere yöneliktir. Bu kitap, yeni bir Blazor tabanlı projede hızlı bir şekilde çalışmaya başlama veya var olan bir ASP.NET Web Forms uygulamasını modernize etmek için bir yol haritası sağlamanıza yardımcı olabilir.

## <a name="how-to-use-the-book"></a>Kitabı kullanma

Bu kitabın ilk bölümünde Blazor olduğu ele alınmaktadır ve ASP.NET Web Forms ile Web uygulaması geliştirmeyle karşılaştırılmaktadır. Daha sonra kitap, Bölüm tarafından sunulan ve her bir Blazor kavramını ASP.NET Web Forms ilgili kavramla ilişkilendiren ve tamamen tamamen yeni kavramların bulunduğu çeşitli Blazor konularını ele alır. Kitap ayrıca, Blazor özelliklerini göstermek ve ASP.NET Web Forms ' den Blazor ' a geçiş için bir örnek olay incelemesi sağlamak üzere hem ASP.NET Web Forms hem de Blazor ' de uygulanan bir bütün örnek uygulamaya düzenli olarak başvurur. [GitHub](https://github.com/dotnet-architecture/eshoponblazor)üzerinde örnek uygulamanın (ASP.NET Web Forms ve Blazor sürümleri) her iki uygulamasını da bulabilirsiniz.

## <a name="what-this-book-doesnt-cover"></a>Bu kitabın kapsamıyor

Bu kitap, kapsamlı bir geçiş kılavuzu değil, Blazor 'e giriş niteliğindedir. Bir projeyi ASP.NET Web Forms 'tan Blazor 'e geçirmeye nasıl yaklaşılacağını gösteren yönergeler de vardır. Bu, her Nuance ve ayrıntıyı ele geçirmeye çalışmaz. ASP.NET ' den ASP.NET Core geçişe yönelik daha genel rehberlik için ASP.NET Core belgelerindeki [geçiş kılavuzuna](https://docs.microsoft.com/aspnet/core/migration/proper-to-2x/) bakın.

### <a name="additional-resources"></a>Ek kaynaklar

Resmi Blazor ana sayfası ve belgelerini adresinde <https://blazor.net>bulabilirsiniz.

## <a name="send-your-feedback"></a>Geri bildiriminizi gönderin

Bu kitap ve ilgili örnekler sürekli gelişiyor, bu nedenle geri bildiriminiz kullanıma açıldı! Bu kitabın nasıl iyileştirilen hakkında açıklamalara sahipseniz, [GitHub sorunları](https://github.com/dotnet/docs/issues)üzerinde oluşturulmuş herhangi bir sayfanın altındaki geri bildirim bölümünü kullanın.

>[!div class="step-by-step"]
>[Next](introduction.md)
