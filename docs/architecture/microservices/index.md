---
title: .NET MikroHizmetler. Kapsayıcılı .NET Uygulamaları Mimarisi
description: .NET Microservices Mimari Containerized .NET Uygulamaları için | Mikro hizmetler modüler ve bağımsız olarak dağıtılabilir hizmetlerdir. Docker kapsayıcıları (Linux ve Windows için), bir hizmeti ve bağımlılıklarını tek bir birime birleştirerek dağıtım ve sınamayı basitleştirir ve bu da daha sonra yalıtılmış bir ortamda çalıştırılır.
ms.date: 01/30/2020
ms.openlocfilehash: 1337fe56e78e03a85627737bd52a089fd946b842
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "77543540"
---
# <a name="net-microservices-architecture-for-containerized-net-applications"></a>.NET Mikro Hizmetleri: Kapsayıcılı .NET Uygulamaları Mimarisi

![Kitap kapağı](./media/cover-small.png)

**EDITION v3.1** - Core 3.1 ASP.NET güncellendi

Bu kılavuz, mikrohizmetlere dayalı uygulamalar geliştirmeye ve bunları kapsayıcılar kullanarak yönetmeye giriştir. .NET Core ve Docker kaplarını kullanarak mimari tasarım ve uygulama yaklaşımlarını tartışır.

Daha kolay başlamak için, kılavuz keşfedebilirsiniz bir referans konteyner ve mikrohizmet tabanlı uygulama odaklanır. Referans uygulaması [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) GitHub repo mevcuttur.

## <a name="action-links"></a>Eylem bağlantıları

- Bu e-kitap pdf formatında da mevcuttur (yalnızca İngilizce sürüm) [İndirin](https://aka.ms/microservicesebook)

- Clone / Fork github üzerinde referans uygulaması [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers)

- Kanal [9'da tanıtım videosunu](https://aka.ms/microservices-video) izleyin

- [Microservices Mimarisini](https://aka.ms/MicroservicesArchitecture) hemen tanıyın

## <a name="introduction"></a>Giriş

İşletmeler giderek maliyet tasarrufu gerçekleştirerek, dağıtım sorunlarını çözüyor ve devops ve üretim operasyonlarını kapsayıcılar kullanarak geliştiriyor. Microsoft, Azure Kubernetes Service ve Azure Service Fabric gibi ürünler oluşturarak ve Docker, Mezossphere ve Kubernetes gibi sektör liderleriyle ortaklık kurarak Windows ve Linux için kapsayıcı yenilikleri yayımlamaktadır. Bu ürünler, şirketlerin platform veya araç seçenekleri ne olursa olsun bulut hızında ve ölçekte uygulamalar oluşturmalarına ve dağıtmalarına yardımcı olan konteyner çözümleri sunar.

Docker, Windows ve Linux ekosistemlerinin en önemli satıcıları tarafından desteklenen konteyner endüstrisinde fiili standart haline gelmektedir. (Microsoft, Docker'ı destekleyen ana bulut satıcılarından biridir.) Gelecekte, Docker muhtemelen bulut veya şirket içinde herhangi bir veri merkezinde her yerde olacak.

Buna ek olarak, [mikro hizmetler](https://martinfowler.com/articles/microservices.html) mimarisi dağıtılmış görev kritik uygulamalar için önemli bir yaklaşım olarak ortaya çıkmaktadır. Mikro hizmet tabanlı bir mimaride uygulama, geliştirilebilen, sınanabilen, dağıtılabilen ve bağımsız olarak sürülenebilen hizmetler koleksiyonu üzerine inşa edilmiştir.

## <a name="about-this-guide"></a>Bu kılavuz hakkında

Bu kılavuz, mikrohizmetlere dayalı uygulamalar geliştirmeye ve bunları kapsayıcılar kullanarak yönetmeye giriştir. .NET Core ve Docker kaplarını kullanarak mimari tasarım ve uygulama yaklaşımlarını tartışır. Konteynerler ve mikro hizmetlerle daha kolay başlamak için kılavuz, keşfedebileceğiniz bir referans konteynerve mikrohizmet tabanlı bir uygulamaya odaklanır. Örnek uygulama [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) GitHub repo mevcuttur.

Bu kılavuz, temel geliştirme ve mimari rehberlik temel iki teknoloji: Docker ve .NET Core odaklanarak bir geliştirme ortamı düzeyinde öncelikle sağlar. Amacımız, üretim ortamınızın altyapısına (bulut veya şirket içi) odaklanmadan uygulama tasarımınızı düşünürken bu kılavuzu okumanızdır. Üretime hazır uygulamalarınızı oluşturduğunuzda altyapınızla ilgili kararları daha sonra vereceksiniz. Bu nedenle, bu kılavuz altyapı agnostik ve daha fazla geliştirme-çevre merkezli olması amaçlanmıştır.

Bu kılavuzu inceledikten sonra, bir sonraki adımınız Microsoft Azure'da üretime hazır mikro hizmetler hakkında bilgi edinmek olacaktır.

## <a name="version"></a>Sürüm

Bu kılavuz, **.NET Core 3.1** sürümüyle birlikte aynı "teknoloji dalgası" (yani Azure ve ek üçüncü taraf teknolojileri) ile ilgili birçok ek güncelleştirmeyle birlikte .NET Core 3.1 sürümüyle aynı zamana denk gelecek şekilde revize edilmiştir. Bu nedenle kitap sürümü de sürüm **3.1**güncellendi.

## <a name="what-this-guide-does-not-cover"></a>Bu kılavuzun kapsamadığı

Bu kılavuz, uygulama yaşam döngüsü, DevOps, CI/CD ardışık hatları veya takım çalışmasına odaklanmaz. Microsoft Platform [ve Tools ile](https://aka.ms/dockerlifecycleebook) tamamlayıcı kılavuz Konteyner Docker Uygulama Yaşam Döngüsü bu konuya odaklanır. Geçerli kılavuz, azure altyapısıyla ilgili belirli orkestratörler hakkındaki bilgiler gibi uygulama ayrıntıları da sağlamaz.

### <a name="additional-resources"></a>Ek kaynaklar

- **Microsoft Platform ve Araçları ile Containerized Docker Uygulama Yaşam Döngüsü** (indirilebilir e-kitap)  
    <https://aka.ms/dockerlifecycleebook>

## <a name="who-should-use-this-guide"></a>Bu kılavuzu kimler kullanmalı?

Bu kılavuzu, Docker tabanlı uygulama geliştirme ve mikro hizmetler tabanlı mimaride yeni olan geliştiriciler ve çözüm mimarları için yazdık. Bu kılavuz, Microsoft geliştirme teknolojileri (.NET Core'a özel olarak odaklanarak) ve Docker kapsayıcılarıyla kavram kanıtı uygulamalarını nasıl tasarlayıp tasarlaacağınızı ve uygulayacağınızı öğrenmek istiyorsanız tam size göre dir.

Yeni ve modern dağıtılmış uygulamalar için hangi yaklaşımı seçeceğiniz konusunda karar vermeden önce mimari ve teknolojiye genel bakış isteyen bir kurumsal mimar gibi teknik bir karar vericiyseniz, bu kılavuzu da yararlı bulacaksınız.

### <a name="how-to-use-this-guide"></a>Bu kılavuz nasıl kullanılır?

Bu kılavuzun ilk bölümünde Docker kapsayıcıları tanıtılır, geliştirme çerçevesi olarak .NET Core ve .NET Framework arasında nasıl seçim yapılacağını tartışır ve mikro hizmetlere genel bir bakış sağlar. Bu içerik, genel bir bakış isteyen ancak kod uygulama ayrıntılarına odaklanması gerekmeyen mimarlar ve teknik karar vericiler içindir.

Kılavuzun ikinci bölümü Docker [tabanlı uygulamalar](./docker-application-development-process/index.md) bölümü için Geliştirme süreci ile başlar. .NET Core ve Docker kullanarak uygulama uygulamak için geliştirme ve mikrohizmet kalıplarına odaklanır. Bu bölüm, kod ve desenler ve uygulama ayrıntıları üzerinde odaklanmak isteyen geliştiriciler ve mimarlar için en çok ilgi olacaktır.

## <a name="related-microservice-and-container-based-reference-application-eshoponcontainers"></a>İlgili microservice ve konteyner tabanlı referans uygulaması: eShopOnContainers

eShopOnContainers uygulaması ,NET Core ve Docker konteynerleri kullanılarak dağıtılmak üzere tasarlanmış mikro hizmetler için bir açık kaynak referans uygulamasıdır. Uygulama, birden fazla e-mağaza Kullanıcı UI ön uçları (Bir Web MVC uygulaması, bir Web SPA ve yerel bir mobil uygulama) dahil olmak üzere birden çok alt sistemden oluşur. Ayrıca, gerekli tüm sunucu tarafı işlemleri için arka uç mikro hizmetleri ve kapsayıcıları içerir.

Uygulamanın amacı mimari desenleri sergilemektir. GERÇEK UYGULAMA YILI BAŞLATMAK İçİn **ÜRETİmHAZIR Bİr ŞABLON Değİl.** Aslında, uygulama kalıcı bir beta durumundadır, aynı zamanda yeni potansiyel olarak ilginç teknolojileri test etmek için kullanılır gibi onlar göstermek gibi.

## <a name="send-us-your-feedback"></a>Geri bildiriminizi bize gönderin!

Bu kılavuzu , .NET'te konteyner uygulamalarının ve mikro hizmetlerin mimarisini anlamanıza yardımcı olmak için yazdık. Kılavuz ve ilgili referans uygulaması gelişmekte olacak, bu yüzden geribildirim bekliyoruz! Bu kılavuzun nasıl geliştirilebileceği hakkında yorumlarınız <https://aka.ms/ebookfeedback>varsa, 'den geri bildirim gönderin.

## <a name="credits"></a>Krediler

Ortak Yazarlar:

> **Cesar de la Torre**, Sr. PM, .NET ürün ekibi, Microsoft Corp.
>
> **Bill Wagner**, Sr. İçerik Geliştirici, C +E, Microsoft Corp.
>
> **Mike Rousos**, Baş Yazılım Mühendisi, DevDiv CAT ekibi, Microsoft

Editörler:

> **Mike Pope**
>
> **Steve Hoag**

Katılımcılar ve gözden geçirenler:

> **Jeffrey Richter**, İş Ortağı Yazılım Müg, Azure ekibi, Microsoft
>
> **Jimmy Bogard**, Headspring Baş Mimarı
>
> **Udi Dahan**, Kurucu & CEO'su, Özel Yazılım
>
> **Jimmy Nilsson**, Factor10'un kurucu ortağı ve CEO'su
>
> **Glenn Condron**, Sr. Program Yöneticisi, ASP.NET takım
>
> **Mark Fussell**, Baş PM Müşteri Adayı, Azure Hizmet Kumaşı ekibi, Microsoft
>
> **Diego Vega**, PM Kurşun, Varlık Çerçeve ekibi, Microsoft
>
> **Barry Dorrans**, Sr. Güvenlik Programı Yöneticisi
>
> **Rowan Miller**, Sr. Program Yöneticisi, Microsoft
>
> **Ankit Asthana**, Baş PM Yöneticisi, .NET ekibi, Microsoft
>
> **Scott Hunter**, İş Ortağı Direktörü PM, .NET ekibi, Microsoft
>
> **Nish Anıl**, Sr. Program Yöneticisi, .NET ekibi, Microsoft
>
> **Dylan Reisenberger**, Polly'de Mimar ve Dev Kurşun
>
> **Steve "ardalis" Smith** - Yazılım Mimarı ve Eğitmen - [Ardalis.com](https://ardalis.com)
>
> **Ian Cooper**, Brighter'da Kodlama Mimarı
>
> **Unai Zorrilla**, Mimar ve Dev Kurşun Düz Kavramlar at
>
> **Eduard Tomas**, Düz Kavramlar dev kurşun
>
> **Ramon Tomas**, Düz Kavramlar Geliştirici
>
> **David Sanz**, Geliştirici Düz Kavramlar at
>
> **Javier Valero**, Grupo Solutio'da Operasyon Müdürü
>
> **Pierre Millet**, Sr. Danışman, Microsoft
>
> **Michael Friis,** Ürün Müdürü, Docker Inc
>
> **Charles Lowell**, Yazılım Mühendisi, VS CAT ekibi, Microsoft
>
> **Miguel Veloso**, Düz Kavramlar Yazılım Geliştirme Mühendisi

## <a name="copyright"></a>Telif Hakkı

YAYIMLAYAN

Microsoft Developer Division, .NET ve Visual Studio ürün ekipleri

Microsoft Corporation'ın bir bölümü

One Microsoft Way

Redmond, Washington 98052-6399

Telif hakkı © 2020 Microsoft Corporation tarafından

Tüm hakları saklıdır. Bu kitabın içeriğinin hiçbir bölümü, yayımcının yazılı izni olmadan herhangi bir biçimde veya herhangi bir şekilde çoğaltılamaz veya aktarılamaz.

Bu kitap "olduğu gibi" sağlanır ve yazarın görüş ve görüşlerini ifade eder. URL ve diğer Internet web sitesi referansları da dahil olmak üzere bu kitapta ifade edilen görüşler, görüşler ve bilgiler önceden haber verilmeden değişebilir.

Burada tarif edilen bazı örnekler yalnızca açıklama için sağlanmıştır ve kurgusaldır. Gerçek bir ilişki veya bağlantı amaçlanmamıştır veya böyle bir bağlantı olduğu sonucuna varılmamalıdır.

Microsoft ve "Ticari <https://www.microsoft.com> Markalar" web sayfasında listelenen ticari markalar, Microsoft şirketler grubunun ticari markalarıdır.

Mac ve macOS, Apple Inc. şirketinin ticari markalarıdır.

Docker balina logosu, Docker, Inc. şirketinin izni yle kullanılan tescilli ticari markasıdır.

Diğer tüm işaretler ve logolar ilgili sahiplerinin mülkiyetindedir.

>[!div class="step-by-step"]
>[Sonraki](container-docker-introduction/index.md)
