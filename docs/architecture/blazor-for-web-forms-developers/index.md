---
title: ASP.NET Web Forms Geliştiricileri için Blazor
description: Blazor ve .NET Core'u basit ve tanıdık bir şekilde kullanarak .NET ile tam yığın web uygulamaları oluşturmayı öğrenin.
author: danroth27
ms.author: daroth
ms.date: 09/11/2019
ms.openlocfilehash: 394d11038b59f4cbe9e9955df43b6198eb5daaf8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73088123"
---
# <a name="blazor-for-aspnet-web-forms-developers"></a>ASP.NET Web Forms Geliştiricileri için Blazor

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

![Serverless Apps e-kitap kapağını gösteren ekran görüntüsü.](./media/index/blazor-for-web-forms-developers-cover.png)

> DOWNLOAD kullanılabilir:<https://aka.ms/blazor-ebook>

YAYIMLAYAN

Microsoft Developer Division, .NET ve Visual Studio ürün ekipleri

Microsoft Corporation'ın bir bölümü

One Microsoft Way

Redmond, Washington 98052-6399

Telif Hakkı © 2019 Microsoft Corporation tarafından

Tüm hakları saklıdır. Bu kitabın içeriğinin hiçbir bölümü, yayımcının yazılı izni olmadan herhangi bir biçimde veya herhangi bir şekilde çoğaltılamaz veya aktarılamaz.

Bu kitap "olduğu gibi" sağlanır ve yazarın görüş ve görüşlerini ifade eder. URL ve diğer Internet web sitesi referansları da dahil olmak üzere bu kitapta ifade edilen görüşler, görüşler ve bilgiler önceden haber verilmeden değişebilir.

Burada tarif edilen bazı örnekler yalnızca açıklama için sağlanmıştır ve kurgusaldır. Gerçek bir ilişki veya bağlantı amaçlanmamıştır veya böyle bir bağlantı olduğu sonucuna varılmamalıdır.

Microsoft ve "Ticari <https://www.microsoft.com> Markalar" web sayfasında listelenen ticari markalar, Microsoft şirketler grubunun ticari markalarıdır.

Mac ve macOS, Apple Inc. şirketinin ticari markalarıdır.

Diğer tüm işaretler ve logolar ilgili sahiplerinin mülkiyetindedir.

Yazar:

> **[Daniel Roth](https://github.com/danroth27)**, Baş Program Yöneticisi, Microsoft Corp.

> **[Jeff Fritz](https://github.com/csharpfritz)**, Kıdemli Program Yöneticisi, Microsoft Corp.

> **[Taylor Southwick](https://github.com/twsouthwick)**, Kıdemli Yazılım Mühendisi, Microsoft Corp.

> **[Scott Addie](https://github.com/scottaddie)**, Kıdemli İçerik Geliştiricisi, Microsoft Corp.

## <a name="introduction"></a>Giriş

.NET, her türlü web uygulaması oluşturmak için kapsamlı bir çerçeve ve araç seti olan ASP.NET aracılığıyla uzun zamandır web uygulaması geliştirmeyi desteklemiştir. ASP.NET klasik Active Server Pages (ASP) ile tüm yol geri başlayan web çerçeveleri ve teknolojileri kendi soyu vardır. Web Formlarını ASP.NET, MVCASP.NET, ASP.NET Web Sayfaları ve daha yakın zamanda Core ASP.NET gibi çerçeveler, Kullanıcı Arabirimi içeriğinin HTTP isteklerine yanıt olarak sunucuda dinamik olarak oluşturulduğu sunucu tarafından *oluşturulmuş* web uygulamaları oluşturmak için üretken ve güçlü bir yol sağlar. Her ASP.NET çerçevesi farklı bir kitleye ve uygulama oluşturma felsefesine hitap eder. ASP.NET Web Formları .NET Framework orijinal sürümü ile sevk ve basit olay işleme ile yeniden kullanılabilir Kullanıcı Durumu denetimleri gibi masaüstü geliştiricileri için tanıdık desenleri birçok kullanarak web geliştirme etkin. Ancak, ASP.NET tekliflerihiçbiri kullanıcının tarayıcısında yürütülen kodu çalıştırmak için bir yol sağlar. Bunu yapmak için JavaScript yazma ve yıllar içinde ve popülerlik dışında aşamalı olan birçok JavaScript çerçeveleri ve araçları kullanarak gerektirir: jQuery, Knockout, Angular, React, ve benzeri.

[Blazor,](https://blazor.net) .NET ile web uygulamaları yaparken nelerin mümkün olduğunu değiştiren yeni bir web çerçevesidir. Blazor, JavaScript yerine C# tabanlı istemci tarafı web ui çerçevesidir. Blazor ile istemci tarafı mantığınızı ve UI bileşenlerinizi C#'a yazabilir, bunları normal .NET derlemelerine derleyebilir ve webassembly adı verilen yeni bir açık web standardı kullanarak doğrudan tarayıcıda çalıştırabilirsiniz. Veya alternatif olarak, Blazor sunucuda .NET UI bileşenlerini çalıştırabilir ve tarayıcıyla gerçek zamanlı bağlantı üzerinden tüm UI etkileşimlerini akıcı bir şekilde işleyebilir. Sunucuda çalışan .NET ile eşleştirildiğinde, Blazor .NET ile tam yığın web geliştirmeyi sağlar. Blazor, yeniden kullanılabilir bir bileşen modeline ve kullanıcı olaylarını işlemek için basit bir yol olması gibi ASP.NET Web Formları ile birçok ortak noktayı paylaşırken, modern ve yüksek performanslı bir web geliştirme deneyimi sağlamak için .NET Core'un temellerini de temellerini oluşturur.

Bu kitap blazor tanıdık ve uygun bir şekilde ASP.NET Web Forms geliştiricileri tanıttı. Blazor kavramlarını ASP.NET Web Formlar'daki benzer kavramlara paralel olarak tanıtırken, daha az tanıdık olabilecek yeni kavramları da açıklar. Bileşen yazma, yönlendirme, düzen, yapılandırma ve güvenlik gibi çok çeşitli konuları ve endişeleri kapsar. Ve bu kitabın içeriği öncelikle yeni bir geliştirme sağlamak için olsa da, aynı zamanda mevcut bir uygulamayı modernize etmek istediğinizde Blazor için mevcut ASP.NET Web Formları geçiş için kurallar ve stratejiler kapsar.

## <a name="who-should-use-the-book"></a>Kitabı kim kullanmalı?

Bu kitap, Blazor'a mevcut bilgi ve becerileriyle ilgili bir giriş arayan ASP.NET Web Forms geliştiricileri içindir. Bu kitap, blazor tabanlı yeni bir projeye hızla başlamaya veya mevcut bir ASP.NET Web Formları uygulamasını modernize etmek için bir yol haritası çizmeye yardımcı olabilir.

## <a name="how-to-use-the-book"></a>Kitap nasıl kullanılır?

Bu kitabın ilk bölümü Blazor ne olduğunu kapsar ve ASP.NET Web Formlar ile web uygulaması geliştirme karşılaştırır. Kitap daha sonra, bölüm bölüm, blazor konuları çeşitli kapsar ve ASP.NET Web Formlar ilgili kavram her Blazor kavramı ile ilgilidir, ya da tamamen yeni kavramlar açıklar. Kitap ayrıca, Blazor'un özelliklerini göstermek ve ASP.NET Web Formlarından Blazor'a geçiş için bir vaka çalışması sağlamak için hem ASP.NET Web Formları hem de Blazor'da uygulanan tam bir örnek uygulamaya da düzenli olarak atıfta bulunmaktadır. Örnek uygulamanın her iki uygulamasını da (Web Formları ve Blazor [sürümleriASP.NET) GitHub'da](https://github.com/dotnet-architecture/eshoponblazor)bulabilirsiniz.

## <a name="what-this-book-doesnt-cover"></a>Bu kitabın kapsamadığı şey.

Bu kitap Blazor için bir giriş değil, kapsamlı bir göç rehberidir. Bir projeyi ASP.NET Web Formlarından Blazor'a nasıl geçirilire ilişkin rehberlik içerse de, her nüansı ve ayrıntıyı kapsamaya çalışmaz. ASP.NET'dan ASP.NET Core'a geçiş konusunda daha genel rehberlik için, ASP.NET Core belgelerindeki [geçiş kılavuzuna](https://docs.microsoft.com/aspnet/core/migration/proper-to-2x/) bakın.

### <a name="additional-resources"></a>Ek kaynaklar

Resmi Blazor giriş sayfasını ve dokümantasyonlarını <https://blazor.net>.

## <a name="send-your-feedback"></a>Geri bildiriminizi gönderin

Bu kitap ve ilgili örnekler sürekli gelişmektedir, bu yüzden geribildirim memnuniyetle karşılanır! Bu kitabın nasıl geliştirilebileceği yle ilgili yorumlarınız varsa, [GitHub sorunları](https://github.com/dotnet/docs/issues)üzerine oluşturulmuş herhangi bir sayfanın altındaki geri bildirim bölümünü kullanın.

>[!div class="step-by-step"]
>[Sonraki](introduction.md)
