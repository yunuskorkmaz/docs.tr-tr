---
title: Blazor ASP.NET Web Forms geliştiricileri için
description: .NET Blazor Core ile basit ve tanıdık bir şekilde tam yığın Web uygulamaları oluşturmayı öğrenin.
author: danroth27
ms.author: daroth
no-loc:
- Blazor
- WebAssembly
ms.date: 09/11/2019
ms.openlocfilehash: 1c869cce6ab8a0ab7c4b83817fe1afc3d6a4a7fd
ms.sourcegitcommit: 0100be20fcf23f61dab672deced70059ed71bb2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88267482"
---
# <a name="no-locblazor-for-aspnet-web-forms-developers"></a>Blazor ASP.NET Web Forms geliştiricileri için

![Sunucusuz uygulamalar e-kitap kapağını gösteren ekran görüntüsü.](./media/index/blazor-for-aspnet-web-forms-developers.png)

> INDIRME: <https://aka.ms/blazor-ebook>

YAYIMLAYAN

Microsoft Geliştirici bölümü, .NET ve Visual Studio ürün ekipleri

Microsoft Corporation 'ın bir bölümü

One Microsoft Way

Redmond, Washington 98052-6399

Telif hakkı © 2020 Microsoft Corporation

All rights reserved. Bu kitabın içeriğinin herhangi bir bölümü herhangi bir biçimde veya herhangi bir şekilde veya başka bir şekilde herhangi bir şekilde çoğaltılamaz veya herhangi bir şekilde gönderilebilir.

Bu kitap, "olduğu gibi" verilmiştir ve yazarın görünümlerini ve opnons 'yi ifade eder. Bu kitapta ifade edilen görünümler, eklentiler ve bilgiler, URL ve diğer Internet Web sitesi başvuruları da dahil olmak üzere bildirimde bulunmaksızın değiştirilebilir.

Burada tarif edilen bazı örnekler yalnızca açıklama için sağlanmıştır ve kurgusaldır. Gerçek bir ilişki veya bağlantı amaçlanmamıştır veya böyle bir bağlantı olduğu sonucuna varılmamalıdır.

Microsoft ve <https://www.microsoft.com> "ticari markalar" Web sayfasında listelenen ticari markalar, Microsoft şirketler grubunun ticari markalarıdır.

Mac ve macOS, Apple Inc. ' in ticari markalarıdır.

Diğer tüm işaretler ve amblemler kendi sahiplerinin mülkiyetindedir.

Düzenliyor

> **[Daniel Roth](https://github.com/danroth27)**, sorumlu Program Yöneticisi, Microsoft Corp.

> **[Jeff Fritz](https://github.com/csharpfritz)**, üst düzey Program Yöneticisi, Microsoft Corp.

> **[Taylor Güney Wick](https://github.com/twsouthwick)**, üst düzey yazılım mühendisi, Microsoft Corp.

> **[Scott Ade](https://github.com/scottaddie)**, üst düzey içerik Geliştirici, Microsoft Corp.

> **[Steve "ardalış" Smith](https://ardalis.com)**, yazılım mimarı ve Trainer, Ardalış Hizmetleri LLC

## <a name="introduction"></a>Giriş

.NET, ASP.NET aracılığıyla desteklenen Web uygulaması geliştirmeyi, her türlü Web uygulaması oluşturmak için kapsamlı bir çerçeve ve araç kümesi içerir. ASP.NET, klasik Active Server sayfalarına (ASP) kadar tüm Web çerçeveleri ve teknolojileri içeren kendi kökenini sahiptir. ASP.NET Web Forms, ASP.NET MVC, ASP.NET Web sayfaları ve daha yeni ASP.NET Core gibi çerçeveler, Kullanıcı arabirimi içeriğinin HTTP isteklerine yanıt olarak dinamik olarak oluşturulduğu *sunucu tarafından işlenmiş* Web uygulamaları oluşturmak için üretken ve güçlü bir yol sağlar. Her bir ASP.NET çerçevesi, farklı bir hedef kitleye ve uygulama oluşturma felsekasında bulunur. ASP.NET Web Forms .NET Framework özgün sürümüyle birlikte sunulan ve basit olay işleme özellikli yeniden kullanılabilir kullanıcı arabirimi denetimleri gibi masaüstü geliştiricilere tanıdık olan çok sayıda desenden yararlanarak web geliştirmeyi etkin bir şekilde. Ancak, ASP.NET tekliflerinin hiçbiri kullanıcının tarayıcısında yürütülen kodu çalıştırmak için bir yol sağlamaz. Bunu yapmak için, JavaScript yazma ve yıl boyunca açık ve popüler olan birçok JavaScript çerçevesini ve araçlarından birini kullanmanızı gerektirir: jQuery, altını gizleme, angular, tepki verme ve benzeri.

[Blazor](https://blazor.net) , .NET ile Web uygulamaları oluştururken mümkün olan şeyleri değiştiren yeni bir Web çerçevesidir. Blazor JavaScript yerine C# tabanlı bir istemci tarafı Web Kullanıcı arabirimi çerçevesidir. İle Blazor , istemci tarafı mantığınızı ve Kullanıcı arabirimi bileşenlerinizi C# dilinde yazabilir, bunları normal .net Derlemeleriyle derleyebilir ve ardından doğrudan tarayıcıda çalıştırarak, yeni bir açık web standardı kullanın WebAssembly Ya da alternatif olarak, Blazor .net UI bileşenlerinizi sunucuda çalıştırabilir ve tarayıcı ile gerçek zamanlı bir bağlantı üzerinden tüm Kullanıcı arabirimi etkileşimlerini akıcı bir şekilde işleyebilir. Sunucuda çalışan .NET ile eşlendiğinde, Blazor .NET ile tam yığın Web geliştirmesini mümkün bir şekilde sunar. BlazorYeniden kullanılabilir bir bileşen modeli ve Kullanıcı olaylarını işlemek için basit bir yol gibi ASP.NET Web Forms ile çok sayıda ortak paylaşım yaparken, modern ve yüksek performanslı bir Web geliştirme deneyimi sağlamak üzere .NET Core 'un temelleri de oluşturulur.

Bu kitap, ASP.NET Web Forms geliştiricilerin Blazor tanıdık ve kullanışlı bir şekilde tanıtılmasını sağlar. BlazorASP.NET Web Forms benzer kavramlarla paralel kavramları tanıtır, aynı zamanda daha az tanıdık olabilecek yeni kavramları de açıklamıştır. Bileşen yazma, yönlendirme, düzen, yapılandırma ve güvenlik dahil olmak üzere çok çeşitli konuları ve sorunları ele alır. Bu kitabın içeriği öncelikli olarak yeni geliştirmeyi etkinleştirmek için, var olan bir uygulamayı modernleştirin istediğinizde mevcut ASP.NET Web Forms geçişine yönelik yönergeleri ve stratejileri de ele alır Blazor .

## <a name="who-should-use-the-book"></a>Kitabı kimler kullanmalıdır?

Bu kitap, Blazor mevcut bilgi ve becerileriyle ilgili bir giriş isteyen ASP.NET Web Forms geliştiricilere yöneliktir. Bu kitap, yeni tabanlı bir projede hızlı bir şekilde çalışmaya Blazor veya var olan bir ASP.NET Web Forms uygulamasının modernleştirilmesi için bir yol haritası sağlanmasına yardımcı olabilir.

## <a name="how-to-use-the-book"></a>Kitabı kullanma

Bu kitabın ilk bölümünde ne olduğu ele alınmaktadır Blazor ve ASP.NET Web Forms ile Web uygulaması geliştirmeyle karşılaştırılmaktadır. Daha sonra kitap, Blazor bölüm tarafından sunulan çeşitli konuları ve her bir Blazor kavramı ASP.NET Web Forms ilgili kavramla ilişkilendirir veya tamamen tamamen yeni kavramların olduğunu anlatmaktadır. Kitap ayrıca, her iki ASP.NET Web Forms uygulanmış olan ve Blazor Blazor özellikleri göstermek ve ASP.NET Web Forms ' dan ' a geçiş için bir örnek olay incelemesi sağlamak üzere her ikisi de düzenli olarak bir örnek uygulamaya başvurur Blazor . GitHub üzerinde örnek uygulamanın (ASP.NET Web Forms ve sürümleri) her iki uygulamasını da bulabilirsiniz Blazor . [GitHub](https://github.com/dotnet-architecture/eshoponblazor)

## <a name="what-this-book-doesnt-cover"></a>Bu kitabın kapsamıyor

Bu kitap Blazor , kapsamlı bir geçiş kılavuzu değil, için bir giriş niteliğindedir. Bir projeyi ASP.NET Web Forms ' den ' a geçirme yaklaşımına yönelik yönergeler de dahil olsa Blazor da, her Nuance ve ayrıntıyı ele geçirmeye çalışmaz. ASP.NET ' den ASP.NET Core geçişe yönelik daha genel rehberlik için ASP.NET Core belgelerindeki [geçiş kılavuzuna](https://docs.microsoft.com/aspnet/core/migration/proper-to-2x/) bakın.

### <a name="additional-resources"></a>Ek kaynaklar

Resmi Blazor giriş sayfası ve belgelerini adresinde bulabilirsiniz <https://blazor.net> .

## <a name="send-your-feedback"></a>Geri bildiriminizi gönderin

Bu kitap ve ilgili örnekler sürekli gelişiyor, bu nedenle geri bildiriminiz kullanıma açıldı! Bu kitabın nasıl iyileştirilen hakkında açıklamalara sahipseniz, [GitHub sorunları](https://github.com/dotnet/docs/issues)üzerinde oluşturulmuş herhangi bir sayfanın altındaki geri bildirim bölümünü kullanın.

>[!div class="step-by-step"]
>[Sonraki](introduction.md)
