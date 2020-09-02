---
title: .NET mikro hizmetleri. Kapsayıcılı .NET Uygulamaları Mimarisi
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmetleri mimarisi | Mikro hizmetler modüler ve bağımsız olarak dağıtılabilir hizmetlerdir. Docker Kapsayıcıları (Linux ve Windows için), bir hizmet ve bağımlılıklarını tek bir birim halinde paketleyerek dağıtım ve test etmeyi basitleştirir. Bu, daha sonra yalıtılmış bir ortamda çalıştırılır.
ms.date: 09/02/2020
ms.openlocfilehash: aea5012fee102f388827d146043e69592e14f22b
ms.sourcegitcommit: b78018c850590dfc0348301e1748b779c28604cc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "89379141"
---
# <a name="net-microservices-architecture-for-containerized-net-applications"></a>.NET Mikro Hizmetleri: Kapsayıcılı .NET Uygulamaları Mimarisi

![Kitap kapağı](./media/cover-small.png)

**Sürüm v 3.1.2** -ASP.NET Core 3,1 ' ye güncelleştirildi

Bu kılavuz, mikro hizmet tabanlı uygulamalar geliştirmeye ve kapsayıcıları kullanarak bunları yönetmeye yönelik bir giriş niteliğindedir. .NET Core ve Docker Kapsayıcıları kullanılarak mimari tasarımı ve uygulama yaklaşımlarını ele alır.

Daha kolay çalışmaya başlamak için kılavuz, keşfedebileceğiniz bir başvuru Kapsayıcılı ve mikro hizmet tabanlı uygulamaya odaklanır. Başvuru uygulaması [Eshoponcontainers](https://github.com/dotnet-architecture/eShopOnContainers) GitHub deposunda mevcuttur.

## <a name="action-links"></a>Eylem bağlantıları

- Bu e-kitap ayrıca bir PDF biçiminde (Yalnızca Ingilizce sürüm) [indirilebilir](https://aka.ms/microservicesebook)

- [GitHub 'daki başvuru uygulaması Eshoponcontainers 'ı](https://github.com/dotnet-architecture/eShopOnContainers) kopyalama/çatal

- [Kanal 9 ' da tanıtım videosunu](https://aka.ms/microservices-video) izleyin

- [Mikro hizmet mimarisini](https://aka.ms/MicroservicesArchitecture) hemen öğrenin

## <a name="introduction"></a>Giriş

Kuruluşlar daha fazla maliyet tasarrufu, dağıtım sorunlarını çözme ve kapsayıcıları kullanarak DevOps ve üretim işlemlerini geliştirme. Microsoft, Azure Kubernetes hizmeti ve Azure Service Fabric gibi ürünler oluşturarak ve Docker, Mesosphere ve Kubernetes gibi sektör liderleriyle işbirliği yaparak Windows ve Linux için kapsayıcı yenilikleri yayımlamaktadır. Bu ürünler, şirketlerin bulut hızında ve ölçekte uygulama oluşturup dağıtmalarına yardımcı olan kapsayıcı çözümleri sunar.

Docker, Windows ve Linux ekosistemlerindeki en önemli satıcılar tarafından desteklenen kapsayıcı sektöründe standart bir standart haline geliyor. (Microsoft, Docker destekleyen ana bulut satıcılarından biridir.) Gelecekte Docker, büyük olasılıkla buluttaki veya Şirket içindeki herhangi bir veri merkezinde yer alır.

Ayrıca, [mikro hizmetler](https://martinfowler.com/articles/microservices.html) mimarisi, dağıtılmış görev açısından kritik uygulamalar için önemli bir yaklaşım olarak gelişmekte. Mikro hizmet tabanlı bir mimaride, uygulama, bağımsız olarak geliştirilen, test edilmiş, dağıtılan ve sürümü tutulan bir hizmetler koleksiyonu üzerine kurulmuştur.

## <a name="about-this-guide"></a>Bu kılavuz hakkında

Bu kılavuz, mikro hizmet tabanlı uygulamalar geliştirmeye ve kapsayıcıları kullanarak bunları yönetmeye yönelik bir giriş niteliğindedir. .NET Core ve Docker Kapsayıcıları kullanılarak mimari tasarımı ve uygulama yaklaşımlarını ele alır. Kapsayıcılar ve mikro hizmetlerle çalışmaya başlamanızı kolaylaştırmak için, rehber, keşfedebileceğiniz bir başvuru Kapsayıcılı ve mikro hizmet tabanlı uygulamaya odaklanır. Örnek uygulama [Eshoponcontainers](https://github.com/dotnet-architecture/eShopOnContainers) GitHub deposunda mevcuttur.

Bu kılavuzda, temel olarak iki teknolojiyi içeren bir geliştirme ortamı düzeyinde temel geliştirme ve mimari yönergeler sunulmaktadır: Docker ve .NET Core. Amaç, üretim ortamınızın altyapısına (bulut veya şirket içi) odaklanmadan uygulama tasarımınız hakkında düşünce yaparken bu kılavuzu okuduğunuzdan emin olur. Daha sonra, üretime yönelik uygulamalar oluşturduğunuzda altyapınızla ilgili kararlar alırsınız. Bu nedenle, bu kılavuzun altyapı belirsiz ve daha fazla geliştirme ortamı merkezli olması amaçlanmıştır.

Bu kılavuzu araştırdık aldıktan sonra, bir sonraki adımınız Microsoft Azure üzerinde üretime Ready mikro hizmetler hakkında bilgi almak için olacaktır.

## <a name="version"></a>Sürüm

Bu kılavuz, .NET Core 3,1 sürümüyle aynı "Wave" teknolojileri (Azure ve ek üçüncü taraf teknolojileri) ile ilgili birçok ek güncelleştirme ile birlikte **.net core 3,1** sürümünü kapsayacak şekilde değiştirilmiştir. Kitap sürümü de **3,1**sürümüne güncelleştirilmiştir.

## <a name="what-this-guide-does-not-cover"></a>Bu kılavuzun kapsamayan

Bu kılavuz uygulama yaşam döngüsü, DevOps, CI/CD işlem hatları veya takım çalışmasına odaklanmaz. [Microsoft platformu ve araçları ile tamamlayıcı kılavuz Kapsayıcılı Docker uygulaması yaşam döngüsü](https://aka.ms/dockerlifecycleebook) ilgili konuya odaklanır. Geçerli kılavuz Ayrıca, belirli düzenleyiciler hakkında bilgi gibi Azure altyapısında uygulama ayrıntıları sağlamaz.

### <a name="additional-resources"></a>Ek kaynaklar

- **Microsoft platformu ve araçları Ile Kapsayıcılı Docker uygulaması yaşam döngüsü** (indirilebilir e-kitap)  
    <https://aka.ms/dockerlifecycleebook>

## <a name="who-should-use-this-guide"></a>Bu kılavuzu kimler kullanmalıdır?

Docker tabanlı uygulama geliştirmeye ve mikro hizmet tabanlı mimariye yönelik yeni olan geliştiriciler ve çözüm mimarları için bu kılavuzu yazdık. Bu kılavuz, Microsoft geliştirme teknolojileri (.NET Core 'ta özel odak ile) ve Docker kapsayıcılarıyla kavram kanıtı uygulamalarının nasıl mimarilerini, tasarlanacağını ve uygulandığını öğrenmek istiyorsanız size yöneliktir.

Ayrıca, yeni ve modern dağıtılmış uygulamalar için seçilecek yaklaşıma karar vermeden önce bir mimari ve teknolojiye genel bakış isteyen bir kuruluş mimarı gibi teknik bir karar veren bu kılavuzu da bulabilirsiniz.

### <a name="how-to-use-this-guide"></a>Bu kılavuz nasıl kullanılır?

Bu kılavuzun ilk bölümü Docker kapsayıcılarını tanıtır, .NET Core ve .NET Framework bir geliştirme çerçevesi olarak arasından nasıl seçim yapılacağını açıklar ve mikro hizmetlere genel bir bakış sağlar. Bu içerik, genel bakış isteyen, ancak kod uygulama ayrıntılarına odaklanmayı gerektirmeyen mimarlar ve teknik karar mekanizmaları içindir.

Kılavuzun ikinci bölümü, [Docker tabanlı uygulamalar Için geliştirme süreci](./docker-application-development-process/index.md) bölümüne başlar. .NET Core ve Docker kullanarak uygulama uygulamaya yönelik geliştirme ve mikro hizmet düzenlerine odaklanır. Bu bölüm, kod ve düzen ve uygulama ayrıntılarına odaklanmak isteyen geliştiricilere ve mimarlara yönelik en çok ilgi çekici olacaktır.

## <a name="related-microservice-and-container-based-reference-application-eshoponcontainers"></a>İlgili mikro hizmet ve kapsayıcı tabanlı başvuru uygulaması: eShopOnContainers

EShopOnContainers uygulaması, Docker Kapsayıcıları kullanılarak dağıtılacak şekilde tasarlanan .NET Core ve mikro hizmetlere yönelik açık kaynaklı bir başvuru uygulamasıdır. Uygulama, çeşitli e-mağaza Kullanıcı arabirimi ön uçları (bir Web MVC uygulaması, Web SPA ve yerel bir mobil uygulama) dahil olmak üzere birden çok alt sistemi içerir. Ayrıca, tüm gerekli sunucu tarafı işlemler için arka uç mikro hizmetleri ve kapsayıcıları da içerir.

Uygulamanın amacı, mimari desenleri göstersağlamaktır. Gerçek dünyada uygulamaları başlatmak için ÜRETIME yönelik olarak **hazırlanmayan BIR şablon değildir** . Aslında, yeni ilginç teknolojileri göründükleri gibi test etmek için de kullanıldığından, uygulama kalıcı bir beta durumundadır.

## <a name="send-us-your-feedback"></a>Bize geri bildirimlerinizi gönderin!

.NET 'teki Kapsayıcılı uygulamaların ve mikro hizmetlerin mimarisini anlamanıza yardımcı olması için bu kılavuzu yazdık. Kılavuz ve ilgili başvuru uygulaması geliştireceğiz, bu nedenle geri bildirimlerinize hoş geldiniz! Bu kılavuzun nasıl iyileştirilen hakkında açıklamalara sahipseniz, konusunda geri bildirimde bulunun <https://aka.ms/ebookfeedback> .

## <a name="credits"></a>Krediler

Ortak Yazarlar:

> **Cesar de La Torre**, SR. PM, .net ürün ekibi, Microsoft Corp.
>
> **Bill Wagner**, SR. Content geliştirici, C + E, Microsoft Corp.
>
> **Mike Rousos**, sorumlu yazılım mühendisi, DEVDIV Cat ekibi, Microsoft

Edit

> **Mike Pope**
>
> **Steve Hoag**

Katılımcılar ve gözden geçirenler:

> **Jeffrey Richter**, Iş ortağı yazılım eng, Azure ekibi, Microsoft
>
> **Jimmy Bogard**, yay Başkan mimarı
>
> **UDI Dahan**, & CEO, belirli yazılımlar
>
> **Jimmy Nilsson**, Co-foin ve CEO of Factor10
>
> **Glenn CONDRON**, SR. program yöneticisi, ASP.NET ekibi
>
> **Mark Fussell**, sorumlu PM lideri, Azure Service Fabric ekibi, Microsoft
>
> **Diego Vega**, PM lideri, Entity Framework ekibi, Microsoft
>
> **Barry Dorrans**, SR. Security Program Yöneticisi
>
> **Rowa Miller**, SR. Program Yöneticisi, Microsoft
>
> **Ankit Asthana**, ana PM Yöneticisi, .NET ekibi, Microsoft
>
> **Scott Hunter**, Iş ortağı Direktörü, .NET ekibi, Microsoft
>
> **Hayvan anıl**, SR. Program Yöneticisi, .NET ekibi, Microsoft
>
> **Dylan Reisenberger**, mimarı ve dev lideri, Polly
>
> **Steve "ardalış" Smith** -yazılım mimarı ve trainer- [Ardalis.com](https://ardalis.com)
>
> **Ian Cooper**, kod mimarı parlaktır
>
> Düz kavramlarda **Unaı Zorrilla**, mimar ve dev lideri
>
> **Eğitik Tomas**, geliştirme lideri, düz kavramlar
>
> **Vamon Tomas**, geliştirici basit kavramlar
>
> **David Sanz**, basit kavramlarda geliştirici
>
> **Javier Valero**, çalışma müdürü, Grupo 'da
>
> **Pierre millet**, SR. danışman, Microsoft
>
> **Michael Fri,** Ürün Yöneticisi, Docker Inc
>
> **Charles Lowell**, yazılım mühendısı, vs Cat ekibi, Microsoft
>
> **MIGUEL Veloso**, düz kavramlarda yazılım geliştirme mühendisi
>
> **Sumit Ghosh**, sorumlu danışman Neudesic

## <a name="copyright"></a>Telif Hakkı

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

Docker balina logosu,, izin tarafından kullanılan Docker, Inc. ' in tescilli ticari markasıdır.

Diğer tüm işaretler ve amblemler kendi sahiplerinin mülkiyetindedir.

>[!div class="step-by-step"]
>[Sonraki](container-docker-introduction/index.md)
