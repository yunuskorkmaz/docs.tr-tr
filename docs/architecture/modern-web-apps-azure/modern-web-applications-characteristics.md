---
title: Modern web uygulamalarının özellikleri
description: ASP.NET Core ve Azure ile Mimar Modern Web Uygulamaları | Modern web uygulamalarının özellikleri
author: ardalis
ms.author: wiwagn
ms.date: 12/04/2019
ms.openlocfilehash: d70fa54adeb505fd37807399402281dfda67cf52
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77451570"
---
# <a name="characteristics-of-modern-web-applications"></a>Modern Web Uygulamalarının Özellikleri

> "… uygun tasarımı ile, özellikleri ucuza gelir. Bu yaklaşım çetin, ama başarılı olmaya devam ediyor."  
> _\-Dennis Ritchie_

Modern web uygulamaları, kullanıcı beklentilerinin her zamankinden daha yüksek olması ve daha fazla talep Günümüzün web uygulamalarının dünyanın herhangi bir yerinden 7/24 kullanıma sunulması ve hemen hemen her cihaz veya ekran boyutundan kullanılabilmesi beklenmektedir. Web uygulamaları, talepteki ani artışları karşılamak için güvenli, esnek ve ölçeklenebilir olmalıdır. Giderek daha karmaşık senaryolar, JavaScript kullanarak istemci üzerine inşa edilmiş zengin kullanıcı deneyimleri tarafından ele alınmalıdır ve web API'leri aracılığıyla verimli bir şekilde iletişim kurmalıdır.

ASP.NET Core modern web uygulamaları ve bulut tabanlı barındırma senaryoları için optimize edilebiyi kullansın. Modüler tasarımı, uygulamaların yalnızca gerçekte kullandıkları özelliklere bağlı olmasını sağlarken, barındırma kaynağı gereksinimlerini azaltırken uygulama güvenliğini ve performansını artırır.

## <a name="reference-application-eshoponweb"></a>Referans uygulaması: eShopOnWeb

Bu kılavuz, bazı ilke ve önerileri gösteren bir referans uygulaması, _eShopOnWeb_içerir. Uygulama gömlek, kahve kupaları ve diğer pazarlama öğeleri bir katalog üzerinden tarama destekleyen basit bir online mağaza. Başvuru uygulaması, anlaşılmasını kolaylaştırmak için kasıtlı olarak basittir.

![eShopOnWeb](./media/image2-1.png)

**Şekil 2-1.** eShopOnWeb

> ### <a name="reference-application"></a>Başvuru Başvurusu
>
> - **eShopOnWeb**  
>   <https://github.com/dotnet/eShopOnWeb>

## <a name="cloud-hosted-and-scalable"></a>Bulut barındırılan ve ölçeklenebilir

ASP.NET Core bulut (genel bulut, özel bulut, herhangi bir bulut) için optimize edilsin, çünkü düşük bellekli ve yüksek iş çıkışlıdır. ASP.NET Core uygulamalarının daha küçük ayak izi, aynı donanımda daha fazla sayıda uygulama barındırabileceğiniz ve kullandıkça öde bulut barındırma hizmetlerini kullanırken daha az kaynak için ödeme yapabileceğiniz anlamına gelir. Yüksek iş gücü, aynı donanımı verilen bir uygulamadan daha fazla müşteriye hizmet verebileceğiniz ve sunuculara yatırım yapma ve altyapı barındırma ihtiyacını daha da azaltabileceğiniz anlamına gelir.

## <a name="cross-platform"></a>Çapraz platform

ASP.NET Core çapraz platformdur ve Linux, macOS ve Windows'da çalıştırılabilir. Bu, ASP.NET Core ile oluşturulmuş uygulamaların hem geliştirilmesi hem de dağıtımı için birçok yeni seçenek sunar. Docker konteynerleri - hem Linux hem de Windows - ASP.NET Core uygulamalarına ev sahipliği yapabilir ve bu [uygulamalarkapların ve mikro hizmetlerin](../microservices/index.md)avantajlarından yararlanmalarını sağlar.

## <a name="modular-and-loosely-coupled"></a>Modüler ve gevşek birleştirilmiş

NuGet paketleri .NET Core'da birinci sınıf vatandaşlardır ve ASP.NET Core uygulamaları NuGet aracılığıyla birçok kütüphaneden oluşur. Bu işlevsellik ayrıntılılığı, uygulamaların yalnızca gerçekten gereksinim duydukları işlevlere bağımlı olmalarını ve dağıtmalarını, ayak izlerini ve güvenlik açığı yüzey alanını azaltmalarına yardımcı olur.

ASP.NET Core ayrıca hem dahili hem de uygulama düzeyinde [bağımlılık enjeksiyonuna](https://deviq.com/dependency-injection/)tam olarak destek ver. Arabirimler, gerektiğinde değiştirilebilen birden çok uygulama olabilir. Bağımlılık enjeksiyonu, uygulamaların belirli uygulamalar yerine bu arabirimlere gevşek bir şekilde çift olarak çift olmasını sağlayarak, uygulamaların genişletmesini, bakımını ve test ini kolaylaştırır.

## <a name="easily-tested-with-automated-tests"></a>Otomatik testler ile kolayca test edilebilir

ASP.NET Core uygulamaları birim testini destekler ve bunların gevşek bağlantı ve bağımlılık enjeksiyonu desteği, altyapı endişelerini test amacıyla sahte uygulamalarla değiştirmeyi kolaylaştırır. ASP.NET Core ayrıca bellekte uygulamaları barındırmak için kullanılabilecek bir TestServer ile gemi. İşlevsel testler daha sonra bu bellek içi sunucuya istekte bulunarak, tam uygulama yığınını (ara yazılım, yönlendirme, model bağlama, filtreler vb. dahil) uygulayabilir ve yanıt alabilir, hepsi de uygulamayı gerçek bir sunucuda barındırmak için gereken sürenin çok kısa bir kısmında ve ağ katmanı üzerinden istekte bulunun. Bu testlerin yazılması özellikle kolaydır ve modern web uygulamalarında giderek daha önemli hale gelen API'ler için değerlidir.

## <a name="traditional-and-spa-behaviors-supported"></a>Desteklenen geleneksel ve SPA davranışları

Geleneksel web uygulamaları çok az istemci tarafı davranışı içeriyordu, ancak bunun yerine uygulamanın yapması gerekebilecek tüm gezinme, sorgular ve güncelleştirmeler için sunucuya güvendi. Kullanıcı tarafından yapılan her yeni işlem yeni bir web isteğine dönüştürülür ve sonuç son kullanıcının tarayıcısında tam sayfa yeniden yüklenir. Klasik Model Görünümü-Denetleyicisi (MVC) çerçeveleri genellikle bu yaklaşımı izler, her yeni istek farklı bir denetleyici eylemine karşılık gelir, bu da bir modelle çalışır ve bir görünüm döndürer. Belirli bir sayfadaki bazı bireysel işlemler AJAX (Asynchronous JavaScript ve XML) işlevleriyle geliştirilebilir, ancak uygulamanın genel mimarisinde birçok farklı MVC görünümü ve URL bitiş noktası kullanılmıştır. Buna ek olarak, ASP.NET Core MVC de Razor Pages, MVC tarzı sayfaları düzenlemek için daha basit bir yolu destekler.

Tek Sayfa uygulamaları (SPA'lar), bunun aksine, çok az dinamik olarak oluşturulan sunucu tarafı sayfa yüklerini içerir (varsa). Birçok SCA, uygulamayı başlatmak ve çalıştırmak için gerekli JavaScript kitaplıklarını yükleyen statik bir HTML dosyası nda başlatılır. Bu uygulamalar, veri ihtiyaçları için web API'lerini yoğun olarak kullanır ve çok daha zengin kullanıcı deneyimleri sağlayabilir.

Birçok web uygulaması, geleneksel web uygulaması davranışı (genellikle içerik için) ve SCA'ların (etkileşim için) bir birleşimini içerir. ASP.NET Core, aynı araç kümesini ve temel çerçeve kitaplıklarını kullanarak aynı uygulamada hem MVC 'yi (Görünümler veya Sayfa tabanlı) hem de web API'lerini destekler.

## <a name="simple-development-and-deployment"></a>Basit geliştirme ve dağıtım

ASP.NET Core uygulamaları basit metin editörleri ve komut satırı arabirimleri veya Visual Studio gibi tam özellikli geliştirme ortamları kullanılarak yazılabilir. Monolitik uygulamalar genellikle tek bir uç noktaya dağıtılır. Dağıtımlar, sürekli tümleştirme (CI) ve sürekli teslimat (CD) ardışık hattının bir parçası olarak kolayca otomatikleştirilebilir. Microsoft Azure, geleneksel CI/CD araçlarına ek olarak git depoları için tümleşik desteğe sahiptir ve güncelleştirmeleri belirli bir git dalı veya etiketinde yapıldıkça otomatik olarak dağıtabilir. Azure DevOps tam özellikli bir CI/CD oluşturma ve dağıtım ardışık hattı sağlarken, GitHub Eylemleri burada barındırılan projeler için başka bir seçenek sunar.

## <a name="traditional-aspnet-and-web-forms"></a>Geleneksel ASP.NET ve Web Formları

ASP.NET Core'a ek olarak, geleneksel ASP.NET 4.x, web uygulamaları oluşturmak için sağlam ve güvenilir bir platform olmaya devam etmektedir. ASP.NET, MVC ve Web API geliştirme modellerinin yanı sıra zengin sayfa tabanlı uygulama geliştirme için çok uygun olan ve zengin bir üçüncü taraf bileşen ekosistemine sahip Web Formlarını destekler. Microsoft Azure, ASP.NET 4.x uygulamaları için uzun zamandır devam eden büyük bir desteğe sahiptir ve birçok geliştirici bu platforma aşinadır.

## <a name="blazor"></a>Blazor

Blazor core 3.0 ve daha sonra ASP.NET ile dahildir. Razor, C#ve ASP.NET Core kullanarak zengin etkileşimli web istemcisi uygulamaları oluşturmak için yeni bir mekanizma sağlar. Modern web uygulamaları geliştirirken göz önünde bulundurulması gereken başka bir çözüm sunar. Blazor'un göz önünde bulundurulması gereken iki sürümü vardır: sunucu tarafı ve istemci tarafı.

Sunucu tarafı Blazor, 2019 yılında ASP.NET Core 3.0 ile piyasaya sürüldü. Adından da anlaşılacağı gibi, sunucuda çalışır ve istemci belgesindeki değişiklikleri ağ üzerinden tarayıcıya geri döndürer. Sunucu tarafı Blazor, istemci tarafı JavaScript gerektirmeden ve her istemci sayfası etkileşimi için ayrı sayfa yükleri gerektirmeden zengin bir istemci deneyimi sağlar. Yüklenen sayfadaki değişiklikler sunucudan istenir ve sunucu tarafından işlenir ve SignalR kullanılarak istemciye geri gönderilir.

İstemci tarafı Blazor 2020 yılında piyasaya sürülecek ve sunucuda değişiklik oluşturma ihtiyacını ortadan kaldıracaktır. Bunun yerine, istemci içinde .NET kodunu çalıştırmak için WebAssembly kaldıraç olacaktır. İstemci, veri istemek için gerekirse sunucuya API çağrıları yapmaya devam edebilir, ancak tüm istemci tarafı davranışı zaten tüm büyük tarayıcılar tarafından desteklenen ve yalnızca bir Javascript kitaplığı olan WebAssembly üzerinden istemcide çalışır.

> ### <a name="references--modern-web-applications"></a>Referanslar – Modern Web Uygulamaları
>
> - **ASP.NET Core’a Giriş**  
>   <https://docs.microsoft.com/aspnet/core/>
> - **ASP.NET Core'da Test**  
>   <https://docs.microsoft.com/aspnet/core/testing/>
> - **Blazor - Başlayın**  
>   <https://blazor.net/docs/get-started.html>

>[!div class="step-by-step"]
>[Önceki](index.md)
>[Sonraki](choose-between-traditional-web-and-single-page-apps.md)
