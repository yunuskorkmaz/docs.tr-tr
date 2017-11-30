---
title: ".NET mikro. Kapsayıcılı .NET uygulamaları için mimarisi"
description: "Kapsayıcılı .NET uygulamaları için .NET mikro mimarisi | Ön konular"
keywords: "Docker, mikro, ASP.NET, kapsayıcı"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: f869656be4c211c9b028f8ac574eb3bf2de139e2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
![](./media/cover.png)

# <a name="net-microservices-architecture-for-containerized-net-applications"></a>.NET mikro. Kapsayıcılı .NET uygulamaları için mimarisi

İNDİRME bulunabilir: <https://aka.ms/microservicesebook>

TARAFINDAN YAYIMLANAN

Microsoft Developer bölme, .NET ve Visual Studio ürün ekipleriyle

Microsoft Corporation'ın bölme

One Microsoft Way

Redmond, Washington 98052-6399

Telif Hakkı © Microsoft Corporation'ın 2017

Tüm hakları saklıdır. Bu kitap içeriğini hiçbir bölümü çoğaltılamaz veya herhangi bir biçimde veya publisher'ın yazılı izni olmadan herhangi bir yöntemle aktarılamaz.

Bu kitap sağlanan "olarak-olan" ve yazar görünümler ve görüşlerini ifade eder. Görünümler, görüşlerini ve URL ve diğer Internet Web sitesi başvuruları dahil olmak üzere bu Defteri'nde ifade bilgileri bildirilmeksizin değiştirilebilir.

Burada açıklanan bazı örnekler yalnızca çizim için sağlanmıştır ve kurgusaldır. Gerçek bir ilişki veya bağlantı amaçlanmamıştır veya çıkarılmamalıdır.

Microsoft ve http://www.microsoft.com "Ticari" Web sayfasında listelenen ticari Microsoft şirketler grubunun ticari markalarıdır.

Mac ve macOS Apple Inc.'in ticari markalarıdır.

Docker whale logosu, Docker, Inc.'in kayıtlı ticari markasıdır İzni tarafından kullanılır.

Diğer tüm işaretler ve logo markalar, ilgili sahiplerinin mülkiyetindedir.

Ortak yazarlar:

> **Cesar de la Torre**, Sr. PM .NET ürün ekibi, Microsoft Corp.
>
> **Fatura Wagner**, Sr. Geliştirici, C + E, Microsoft Corp. içerik
>
> **Can Rousos**, asıl yazılım mühendisi, DevDiv CAT ekibi, Microsoft

Düzenleyiciler:

> **Can Pope**
>
> **Steve Hoag**

Katılımcıların ve gözden geçirenler:

> **Gamze Ritcher**, iş ortağı yazılım Eng, Azure ekibi, Microsoft
>
> **Jimmy Bogard**, Headspring adresindeki Baş Mimarı
>
> **UDI Dahan**, kurucusu & CEO, belirli yazılım
>
> **Jimmy Nilsson**, ortak kurucusu ve Factor10 CEO
>
> **Glenn Condron**, Sr. Program Yöneticisi, ASP.NET ekibi
>
> **İşareti Fussell**, asıl PM sağlama, Microsoft Azure Service Fabric ekibi
>
> **Diego Vega**, PM sağlama, Entity Framework takım, Microsoft
>
> **Hakan Dorrans**, Sr. Güvenlik Program Yöneticisi
>
> **Rowan Mert**, Sr. Program Yöneticisi, Microsoft
>
> **Ankit Asthana**, asıl PM Yöneticisi, .NET ekibi, Microsoft
>
> **Tan Hunter**, .NET ekibi, Microsoft iş ortağı Director PM
>
> **Dylan Reisenberger**, mimarı ve Polly adresindeki Geliştirici sağlama
>
> **Steve Smith**, yazılım Craftsman & ASPSmith Ltd. şirketindeki Eğitmen
>
> **Yen Cooper**, kodlama mimari adresindeki parlak
>
> **Unai Zorrilla**, mimarı ve düz kavramları adresindeki Geliştirici sağlama
>
> **Eduard Tomas**, düz kavramları adresindeki Geliştirici sağlama
>
> **Ramon Tomas**, düz kavramları adresindeki Geliştirici
>
> **David Sanz**, düz kavramları adresindeki Geliştirici
>
> **Javier Valero**, baş Müdürü Grupo çözümleri adresindeki işletim
>
> **Pierre Millet**, Sr. Danışman, Microsoft
>
> **Michael Friis**, ürün Yöneticisi, Docker Inc
>
> **Charles Lowell**, yazılım mühendisi, VS CAT ekibi, Microsoft

## <a name="introduction"></a>Giriş

Giderek kuruluşların maliyet tasarrufu kullanıldıklarını, dağıtım sorunlarını çözmek ve kapsayıcılar kullanarak DevOps ve üretim işlemlerini artırma. Microsoft Windows ve Linux için kapsayıcı yenilikleri Azure kapsayıcı hizmeti ve Azure Service Fabric gibi ürün oluşturma ve Docker, Mesosphere ve Kubernetes gibi endüstri kılavuzları ile ortaklık serbest. Bu ürünler bulut hızı ve ölçek, hangi uygulamalar oluşturma ve dağıtma şirketlerin yardımcı kapsayıcı çözümleri teslim kendi seçtikleri platform veya Araçlar.

Docker gerçek Windows ve Linux ekosistemlerini en önemli satıcılar tarafından desteklenen kapsayıcı endüstri standardında durumundadır. (Microsoft Docker destekleyen ana bulut satıcılar biridir.) Gelecekte, Docker büyük olasılıkla bulutta veya şirket içi herhangi bir veri merkezinde bulunabilen olacaktır.

Ayrıca, [mikro](https://martinfowler.com/articles/microservices.html) mimarisi gelişen dağıtılmış görev açısından kritik uygulamalar için önemli bir yaklaşım olarak. Mikro hizmet tabanlı bir mimari, uygulama, test edilmiş, dağıtılan ve sürümü tutulan bağımsız olarak geliştirilebilir hizmetler koleksiyonu üzerinde oluşturulmuştur.

## <a name="about-this-guide"></a>Bu kılavuz hakkında

Bu kılavuz mikro tabanlı uygulamaları geliştirmek ve bunları yönetmek için bir giriş olduğunu kapsayıcıları kullanma. Mimari Tasarım açıklanır ve .NET Core ve Docker kapsayıcıları kullanma uygulaması yaklaşıyor. Kapsayıcılar ve mikro kullanmaya başlama kolaylaştırmak için bir kapsayıcılı başvurusu ve keşfedebilirsiniz mikro hizmet tabanlı bir Uygulama Kılavuzu odaklanır. Örnek uygulama kullanılabilir [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) GitHub depo.

Bu kılavuz temel geliştirme ve Mimari Kılavuzu birincil olarak geliştirme ortamı düzeyde iki teknolojiyi odaklanmak sağlar: Docker ve .NET Core. Bizim amaç, yapı üretim ortamınızın (Bulut veya şirket içi) odaklanan olmadan uygulama tasarımı hakkında düşünürken, bu kılavuzu okumadan ' dir. Üretime hazır uygulamalarınızı oluşturduğunuzda altyapınızı hakkında kararlar daha sonra hale getirir. Bu nedenle, bu kılavuz, altyapı belirsiz ve daha fazla geliştirme ortamı-merkezli olması amaçlanmıştır.

Bu kılavuz eğitim sonra sonraki adımınız üretime hazır mikro Microsoft Azure üzerinde hakkında bilgi edinmek için olacaktır.

## <a name="what-this-guide-does-not-cover"></a>Ne bu kılavuzda ele alınmamaktadır

Bu kılavuz uygulama yaşam döngüsü DevOps, CI/CD ardışık odaklanan değil veya ekibi çalışın. Tamamlayıcı Kılavuzu [Microsoft Platformu ve araçları ile kapsayıcılı Docker uygulama yaşam döngüsü](https://aka.ms/dockerlifecycleebook) bu konuda odaklanır. Geçerli Kılavuz ayrıca uygulama ayrıntılarını belirli orchestrators hakkında bilgi gibi Azure altyapı sağlamaz.

### <a name="additional-resources"></a>Ek kaynaklar

-   **Microsoft Platformu ve araçları ile Docker uygulama yaşam döngüsü kapsayıcılı** (indirilebilir e-kitap) [ *https://aka.ms/dockerlifecycleebook*](https://aka.ms/dockerlifecycleebook)

## <a name="who-should-use-this-guide"></a>Bu kılavuz kullanan

Geliştiriciler ve Docker tabanlı uygulama geliştirme ve mikro tabanlı mimari yeni çözüm mimarları için bu kılavuzu yazıldı. Bu kılavuz, mimari, öğrenmek istiyorsanız, tasarlayıp (odaklanılan özel .NET Core üzerinde) Microsoft geliştirme teknolojileriyle kavram kanıtı uygulamaları için olan ve Docker kapsayıcılarla.

Da bu kılavuzda yararlı bir mimari isteyen bir kuruluş Mimarı gibi bir teknik karar veren olan ve teknoloji genel bakış, önce karar verirseniz dağıtılmış uygulamalar yeni ve modern seçmek için hangi yaklaşımın üzerinde bulacaksınız.

### <a name="how-to-use-this-guide"></a>Bu kılavuz kullanma

Bu kılavuzun ilk bölümü Docker kapsayıcıları tanıtır, .NET Core ve .NET Framework geliştirme framework olarak arasında seçim yapma açıklanır ve mikro genel bir bakış sağlar. Bu içerik mimarları ve genel bir bakış isteyen ancak kimin kod uygulama ayrıntılara odaklanmak gerekmez teknik karar alıcılar içindir.

Kılavuzu ikinci bölümü ile başlayan [geliştirme işlemi için Docker tabanlı uygulamalar](#ch_dev_process_for_docker_based_apps) bölümü. .NET Core ve Docker kullanan uygulamalar uygulama geliştirme ve mikro hizmet desenleri odaklanır. Bu bölümde, geliştiriciler ve odak kodu ve modelleri ve uygulama ayrıntılarını istediğiniz mimarları için en ilgi olacaktır.

## <a name="related-microservice-and-container-based-reference-application-eshoponcontainers"></a>İlgili mikro hizmet ve kapsayıcı tabanlı başvuru uygulaması: eShopOnContainers

.NET Core ve Docker kapsayıcıları kullanma dağıtılması için tasarlanmış mikro hizmetler için bir başvuru uygulaması eShopOnContainers uygulamasıdır. Uygulama birkaç e deposu UI ön uçlar (bir Web uygulaması ve yerel bir mobil uygulama) dahil olmak üzere birden çok alt oluşur. Arka uç mikro ve gerekli tüm sunucu tarafı işlemleri için kapsayıcı de içerir.

Bu mikro hizmet ve kapsayıcı tabanlı uygulama kaynak kodudur açık kaynaklı ve adresinde [eShopOnContainers](http://aka.ms/MicroservicesArchitecture) GitHub depo.

## <a name="send-us-your-feedback"></a>Bize Geri bildiriminizi gönderin!

Kapsayıcılı uygulamaları ve .NET mikro mimarisini anlamanıza yardımcı olması için bu kılavuzu yazdığımız. Bildiriminiz bizim için kılavuz ve ilgili başvuru uygulaması, Gelişmekte olan! Bu kılavuz nasıl geliştirilebilir hakkında yorumlar varsa, lütfen gönderebilirsiniz:

[dotnet-architecture-ebooks-feedback@service.microsoft.com](mailto:dotnet-architecture-ebooks-feedback@service.microsoft.com)

>[!div class="step-by-step"]
[Sonraki] (kapsayıcı-docker-giriş/index.md)
