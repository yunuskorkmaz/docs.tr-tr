---
title: Modern web uygulamalarının özellikleri
description: ASP.NET Core ve Azure ile modern web uygulamalarını mimarın Modern Web uygulamalarının özellikleri
author: ardalis
ms.author: wiwagn
ms.date: 12/04/2019
ms.openlocfilehash: d70fa54adeb505fd37807399402281dfda67cf52
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77451570"
---
# <a name="characteristics-of-modern-web-applications"></a>Modern Web uygulamalarının özellikleri

> "… uygun tasarımla, özellikler de birlikte gelir. Bu yaklaşım, bir dizi değildir ancak başarılı olmaya devam eder. "  
> _\- dennıs Ritchie_

Modern Web uygulamalarının daha fazla Kullanıcı beklentileri ve daha önce her zamankinden daha fazla olması gerekir. Bugünün Web uygulamalarının dünyanın herhangi bir yerinden 24/7 kullanılabilir olması ve neredeyse tüm cihazlardan veya ekran boyutundan kullanılabilir olması beklenmektedir. Web uygulamaları, istek üzerine ani artışları karşılamak için güvenli, esnek ve ölçeklenebilir olmalıdır. Giderek karmaşık senaryolar, JavaScript kullanılarak istemci üzerinde oluşturulmuş zengin kullanıcı deneyimleri tarafından işlenmeli ve Web API 'Leri aracılığıyla etkin bir şekilde iletişim edilmelidir.

ASP.NET Core, modern web uygulamaları ve bulut tabanlı barındırma senaryoları için iyileştirilmiştir. Modüler tasarımı, uygulamaların yalnızca gerçekten kullandıkları özelliklere bağlı olmasına olanak tanılarken, barındırma kaynağı gereksinimlerini azaltırken uygulama güvenliğini ve performansını geliştirir.

## <a name="reference-application-eshoponweb"></a>Başvuru uygulaması: eShopOnWeb

Bu kılavuz, bazı ilkeleri ve önerileri gösteren bir başvuru uygulaması olan _Eshoponweb_içerir. Uygulama, Shirts, kahve Mug 'ler ve diğer pazarlama öğelerinin bir kataloğuna göz atmayı destekleyen basit bir çevrimiçi depodur. Daha kolay anlaşılır olması için başvuru uygulaması kasıtlı olarak basittir.

![eShopOnWeb](./media/image2-1.png)

**Şekil 2-1.** eShopOnWeb

> ### <a name="reference-application"></a>Başvuru uygulaması
>
> - **eShopOnWeb**  
>   <https://github.com/dotnet/eShopOnWeb>

## <a name="cloud-hosted-and-scalable"></a>Bulutta barındırılan ve ölçeklenebilir

ASP.NET Core, düşük bellek ve yüksek aktarım hızı olduğundan bulut (genel bulut, özel bulut, tüm bulut) için iyileştirilmiştir. ASP.NET Core uygulamaların daha küçük bir şekilde kapladığı alanı, bunları aynı donanımda barındırabilmeniz ve kullandıkça öde bulut barındırma hizmetleri 'ni kullanırken daha az kaynak ödemenize yol açabilir. Daha yüksek aktarım hızı, aynı donanıma verilen bir uygulamadan daha fazla müşteriye, sunuculara ve barındırma altyapısına yatırım ihtiyacını azaltmaya daha fazla bilgi verebileceğiniz anlamına gelir.

## <a name="cross-platform"></a>Platformlar arası

ASP.NET Core platformlar arası ve Linux, macOS ve Windows üzerinde çalışabilir. Bu, ASP.NET Core ile oluşturulmuş uygulamaların geliştirilmesi ve dağıtılması için birçok yeni seçenek açar. Docker Kapsayıcıları-hem Linux hem de Windows-ASP.NET Core uygulamalarını barındırabilir ve bu da [kapsayıcıların ve mikro hizmetlerin](../microservices/index.md)avantajlarından yararlanmasını sağlar.

## <a name="modular-and-loosely-coupled"></a>Modüler ve gevşek olarak bağlanmış

NuGet paketleri .NET Core 'da birinci sınıf vatandaşları ve ASP.NET Core uygulamalar, NuGet aracılığıyla birçok Kitaplığı temel alarak oluşur. Bu işlevsellik ayrıntı düzeyi, uygulamaların yalnızca gerçekten ihtiyaç duydukları işlevlere bağlı olarak, parmak izi ve güvenlik güvenlik açığı yüzeyi alanını azalttığından emin olmanıza yardımcı olur.

ASP.NET Core Ayrıca, hem dahili olarak hem de uygulama düzeyinde [bağımlılık ekleme](https://deviq.com/dependency-injection/)işlemini tam olarak destekler. Arabirimlerde, gerektiğinde değiştirilebilen birden fazla uygulama olabilir. Bağımlılık ekleme, uygulamaların belirli uygulamalar yerine, bu arabirimlere gevşek bir şekilde çift olmasını sağlar, bu sayede genişletmeyi, bakımını ve testi kolaylaştırır.

## <a name="easily-tested-with-automated-tests"></a>Otomatikleştirilmiş testlerle kolayca test edilmiştir

ASP.NET Core uygulamalar birim testini destekler ve bağımlılık ekleme için gevşek bir SLA ve destek sayesinde altyapı sorunları, test amacıyla sahte uygulamalarla takas edilmesini kolaylaştırır. ASP.NET Core Ayrıca, uygulamaları bellekte barındırmak için kullanılabilecek bir TestServer ile birlikte gelir. İşlevsel testler daha sonra bu bellek içi sunucuya istek yapabilir, tüm uygulama yığınını (ara yazılım, yönlendirme, model bağlama, filtreler vb. dahil) kullanabilir ve bir yanıt alarak, uygulamayı gerçek bir sunucuda barındırmak için gereken sürenin bir kesilişinde ve ağ katmanı üzerinden istekler yapın. Modern Web uygulamalarında daha fazla önem taşıyan API 'Ler için bu testlerin yazılması ve değerli olması özellikle kolaydır.

## <a name="traditional-and-spa-behaviors-supported"></a>Geleneksel ve SPA davranışları destekleniyor

Geleneksel web uygulamaları çok sayıda istemci tarafı davranışına sahiptir, ancak bunun yerine uygulamanın yapması gerekebilecek tüm gezinme, sorgu ve güncelleştirmelerin sunucusuna güvenmesi gerekir. Kullanıcı tarafından yapılan her yeni işlem, son kullanıcının tarayıcısına tam sayfa yeniden yükleme işlemi ile yeni bir Web isteğine çevrilir. Klasik model-görünüm-denetleyicisi (MVC) çerçeveleri genellikle bu yaklaşımı, farklı bir denetleyici eylemine karşılık gelen her yeni istekle birlikte çalışarak, bir modelle birlikte çalışarak bir görünüm döndürecek şekilde izler. Belirli bir sayfadaki bazı ayrı işlemler AJAX (zaman uyumsuz JavaScript ve XML) işlevselliğiyle geliştirilebilir, ancak uygulamanın genel mimarisi birçok farklı MVC görünümü ve URL uç noktası kullandı. Ayrıca, ASP.NET Core MVC, MVC stili sayfaları düzenlemenin daha basit bir yolunu da Razor Pages destekler.

Tek sayfalı uygulamalar (maça), aksine, dinamik olarak üretilen çok sayıda sunucu tarafı sayfa yükü (varsa) içerir. Birçok Spaon, uygulamayı başlatmak ve çalıştırmak için gerekli JavaScript kitaplıklarını yükleyen statik bir HTML dosyası içinde başlatılır. Bu uygulamalar, veri ihtiyaçları için Web API 'lerinin yoğun bir şekilde kullanılmasını sağlar ve çok daha zengin kullanıcı deneyimleri sağlayabilir.

Birçok Web uygulaması geleneksel Web uygulaması davranışının (genellikle içerik için) ve maça (etkileşim için) bir birleşimini içerir. ASP.NET Core, aynı araç ve temel çerçeve kitaplıklarını kullanarak aynı uygulamadaki MVC (görünümler veya sayfa tabanlı) ve Web API 'Lerini destekler.

## <a name="simple-development-and-deployment"></a>Basit geliştirme ve dağıtım

ASP.NET Core uygulamalar basit metin düzenleyicileri, komut satırı arabirimleri veya Visual Studio gibi tam özellikli geliştirme ortamları kullanılarak yazılabilir. Tek parçalı uygulamalar genellikle tek bir uç noktaya dağıtılır. Dağıtımlar sürekli tümleştirme (CI) ve sürekli teslim (CD) işlem hattının parçası olarak kolayca otomatikleştirilebilir. Geleneksel CI/CD araçlarına ek olarak, Microsoft Azure Git depoları için tümleşik desteğe sahiptir ve belirli bir git dalında veya etiketinde yapılan güncelleştirmeleri otomatik olarak dağıtabilir. Azure DevOps, tam özellikli bir CI/CD derleme ve dağıtım Işlem hattı sağlar ve GitHub eylemleri orada barındırılan projeler için başka bir seçenek sağlar.

## <a name="traditional-aspnet-and-web-forms"></a>Geleneksel ASP.NET ve Web Forms

ASP.NET Core buna ek olarak, geleneksel ASP.NET 4. x Web uygulamaları oluşturmaya yönelik sağlam ve güvenilir bir platform olmaya devam etmektedir. ASP.NET, MVC ve Web API Geliştirme modellerini destekler, ayrıca zengin sayfa tabanlı uygulama geliştirmeye uygun olan ve zengin bir üçüncü taraf bileşen ekosistemi özelliklerine sahip olan Web Forms. Microsoft Azure, ASP.NET 4. x uygulamaları için harika bir destek içerir ve bu platformda çok sayıda geliştirici tanıdık gelecektir.

## <a name="blazor"></a>Blazor

Blazor ASP.NET Core 3,0 ve üzeri bir sürüme dahildir. Razor, C#ve ASP.NET Core kullanarak zengin etkileşimli Web istemcisi uygulamaları oluşturmaya yönelik yeni bir mekanizma sağlar. Modern Web uygulamaları geliştirirken göz önünde bulundurmanız gereken başka bir çözüm sunar. Göz önünde bulundurmanız gereken iki Blazor sürümü vardır: sunucu tarafı ve istemci tarafı.

Sunucu tarafı Blazor ASP.NET Core 3,0 ile 2019 ' de yayımlanmıştır. Adından da anlaşılacağı gibi, sunucu üzerinde çalışır ve değişiklikler istemci belgesinde ağ üzerinden tarayıcıya geri getirilir. Sunucu tarafı Blazor, istemci tarafı JavaScript gerekmeden ve her istemci sayfa etkileşimi için ayrı sayfa yükleri gerekmeden zengin bir istemci deneyimi sağlar. Yüklenen sayfadaki değişiklikler sunucu tarafından istenir ve işlenir ve ardından SignalR kullanılarak istemciye geri gönderilir.

İstemci tarafı Blazor 2020 ' de yayımlanacak ve sunucudaki değişiklikleri işleme gereksinimini ortadan kaldıracak. Bunun yerine, istemci içinde .NET kodu çalıştırmak için WebAssembly 'ten faydalanır. İstemci, veri istemek için gerekliyse sunucuya API çağrıları yapmaya devam edebilir, ancak tüm istemci tarafı davranışı, tüm büyük tarayıcılarda zaten desteklenen ve yalnızca bir JavaScript kitaplığı olduğu WebAssembly aracılığıyla istemcide çalışır.

> ### <a name="references--modern-web-applications"></a>Başvurular – Modern Web uygulamaları
>
> - **ASP.NET Core giriş**  
>   <https://docs.microsoft.com/aspnet/core/>
> - **ASP.NET Core 'de test etme**  
>   <https://docs.microsoft.com/aspnet/core/testing/>
> - **Blazor-kullanmaya başlama**  
>   <https://blazor.net/docs/get-started.html>

>[!div class="step-by-step"]
>[Önceki](index.md)
>[İleri](choose-between-traditional-web-and-single-page-apps.md)
