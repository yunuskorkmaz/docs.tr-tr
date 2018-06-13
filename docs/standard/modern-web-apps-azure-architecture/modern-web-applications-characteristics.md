---
title: Modern web uygulamalarının özellikleri
description: ASP.NET Core ve Azure ile modern Web uygulamaları mimari | modern web uygulamalarının özellikleri
author: ardalis
ms.author: wiwagn
ms.date: 10/06/2017
ms.openlocfilehash: e01d07f4006982b21ff952b89375b0ab0d8f36b4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33583061"
---
# <a name="characteristics-of-modern-web-applications"></a>Modern Web uygulamalarının özellikleri

> "… uygun tasarımıyla özellikleri ailenin gelir. Bu yaklaşım arduous, ancak başarılı olması devam ediyor."  
> _\- Dennis Ritchie_

## <a name="summary"></a>Özet

Modern web uygulamaları daha yüksek kullanıcı beklentilerini ve büyük taleplerini zamankinden sahiptir. Günümüzün web uygulamaları kullanılabilir 24/7'den, dünyanın ve neredeyse tüm cihazlardan kullanılabilir olması veya ekran boyutu beklenir. Web uygulamaları, güvenli, esnek ve ani talep karşılamak için ölçeklenebilir olması gerekir. Giderek karmaşık senaryolar JavaScript kullanarak ve verimli bir şekilde web API'leri iletişim kurarken istemcide yerleşik zengin kullanıcı deneyimleri tarafından yapılması gerekir.

ASP.NET Core modern web uygulamaları ve bulut tabanlı barındırma senaryoları için optimize edilmiştir. Modüler tasarımı uygulamaların yalnızca gerçekten, uygulama güvenliği ve barındırma kaynak gereksinimlerini azaltırken performansı artırma kullandıkları özelliklerine bağlıdır olanak sağlar.

## <a name="reference-application-eshoponweb"></a>Başvuru uygulama: eShopOnWeb

Bu kılavuz bir başvuru uygulaması içeren *eShopOnWeb*, bazı prensipler ve öneriler gösterir. Gömlekler, kahve bardaklar ve pazarlama diğer öğeler bir katalog tarama destekleyen basit bir çevrimiçi mağaza uygulamasıdır. Başvuru uygulaması anlaşılması kolay hale getirmek için kasıtlı olarak basit bir işlemdir.

**Şekil 2-1.** eShopOnWeb

![](./media/image2-1.png)

> ### <a name="reference-application"></a>Başvuru uygulaması
> - **eShopOnWeb**  
> <https://github.com/dotnet/eShopOnWeb>

## <a name="cloud-hosted-and-scalable"></a>Bulut tarafından barındırılan ve ölçeklenebilir

Düşük bellek ve yüksek verimlilik olduğundan ASP.NET Core (genel bulut, özel bulut, tüm bulut) bulut için optimize edilmiştir. ASP.NET Core uygulamaları daha küçük ayak izini daha fazlası aynı donanımda barındırabilir ve ödeme-olarak-kullandığınız olduğunuzda, bulut barındırma hizmetleri için daha az kaynak ödeme anlamına gelir. Daha yüksek-verimlilik aynı donanım, verilen bir uygulama daha fazla müşterilerden başka sunucular ve barındırma altyapı yatırım gereksinimini azaltır kullanılabileceği anlamına gelir.

## <a name="cross-platform"></a>Çoklu Platform

ASP.NET Core platformlar arası ve Linux ve MacOS aynı zamanda Windows çalıştırabilirsiniz. Bu geliştirme ve ASP.NET Core ile oluşturulan uygulamaların dağıtılması için birçok yeni seçenek açar. Genellikle Linux bugün çalıştırmak, docker kapsayıcıları avantajlarından yararlanmak vermeden ASP.NET Core uygulamaları barındırabilir [kapsayıcıları ve mikro](../microservices-architecture/index.md).

## <a name="modular-and-loosely-coupled"></a>Modüler ve geniş bağlı

İlk sınıf kullanıcılarının, .NET Core NuGet paketlerini olan ve ASP.NET Core uygulamaları birçok kitaplıkları NuGet aracılığıyla oluşur. Bu işlevsellik kesinliği uygulamalar yalnızca bağlıdır ve gerçekte, kendi ayak izini ve güvenlik açığı yüzey alanını azaltma gereksinim duydukları işlevselliği dağıtabilirsiniz sağlamaya yardımcı olur.

ASP.NET Core bağımlılık ekleme, hem iç hem de uygulama düzeyinde tam olarak destekler. Arabirimleri gerektiğinde takas edilebilir birden fazla uygulaması olabilir. Bağımlılık ekleme geniş birkaç genişletmek, korumak ve test kolaylaştıran bu arabirimlerine uygulamalara izin verir.

## <a name="easily-tested-with-automated-tests"></a>Otomatikleştirilmiş testleri ile kolayca test

Birim testi ASP.NET Core uygulamaları destekler ve kendi gevşek bağlantı ve bağımlılık eklemelerini desteği altyapı sorunları test amacıyla sahte uygulamalarıyla birlikte takas yapmayı kolaylaştırır. ASP.NET Core de bellekte ana bilgisayar uygulamaları için kullanılan bir TestServer gelir. İşlevsel testleri istekleri (Ara yazılım, yönlendirme, model bağlama, filtreleri, vb. dahil) tüm uygulama yığınını kullanan bu bellek içi sunucuya yapabilir ve tüm bir kesir zaman içinde bir yanıt alma, gerçek bir sunucuda uygulamayı barındırmak için harcanacak ve ağ katmanı isteklerini yapın. Bu testleri yazmak özellikle kolay ve değerli, API için hangi modern web uygulamalarında giderek daha çok önemlidir.

## <a name="traditional-and-spa-behaviors-supported"></a>Geleneksel ve desteklenen SPA davranışları

Geleneksel web uygulamaları biraz istemci tarafı davranışı söz konusu, ancak bunun yerine tüm gezinti, sorgular ve uygulama yapmanız gerekebilecek güncelleştirmeler için sunucuda dayanıyordu. Kullanıcı tarafından yapılan her yeni işlem yeni bir web isteği, son kullanıcının tarayıcıda tam sayfa yeniden olan sonucunda çevrilmesi. Klasik Model-View-Controller (MVC) çerçeveleri bu yaklaşım, sırayla ve bir modeliyle çalışacak bir görünüme dönmek bir farklı denetleyici eylemi için karşılık gelen her yeni isteği ile genellikle izleyin. Bazı tek tek işlemleri belirli bir sayfadaki AJAX (zaman uyumsuz JavaScript ve XML) işlevselliği ile geliştirilmiş, ancak uygulama genel mimarisi birçok farklı MVC görünümleri ve URL uç noktaları kullanılır.

Tek sayfa uygulamaları (SPAs), (varsa) aksine, çok az dinamik olarak üretilen sunucu tarafı sayfa yüklerinin içerir. Birçok SPAs başlatmak ve uygulamayı çalıştırmak için gerekli JavaScript kitaplıklarını yükleyen bir statik HTML dosyası içinde başlatılır. Bu uygulamalar, web API'leri için veri gereksinimlerine ağır kullanımını olun ve çok daha zengin kullanıcı deneyimleri sağlayabilir.

Birçok web uygulamaları geleneksel web uygulama davranışına (genellikle içerik için) ve (için etkileşim) SPAs bir birleşimini içerir. ASP.NET Core, MVC ve web aynı uygulama aynı birtakım araçlar kullanarak ve framework kitaplıkları temel API'leri destekler.

## <a name="simple-development-and-deployment"></a>Basit geliştirme ve dağıtım

ASP.NET Core uygulamaları basit metin düzenleyicileri ve komut satırı arabirimi ya da tam özellikli bir geliştirme ortamları Visual Studio gibi kullanılarak yazılabilir. Tek yapılı uygulamalar genellikle tek bir uç noktasına dağıtılır. Sürekli Tümleştirme (CI) ve kesintisiz teslim (CD) ardışık düzen parçası olarak gerçekleşecek şekilde dağıtımları kolayca otomatik olarak yapılabilir. Geleneksel CI/CD araçları yanı sıra Windows Azure destek git depoları için tümleşik olan ve belirtilen git şube ya da etiketi gerçekleştirilmediğinden güncelleştirmelerini otomatik olarak dağıtabilirsiniz.

## <a name="traditional-aspnet-and-web-forms"></a>Geleneksel ASP.NET ve Web formları

Ek olarak ASP.NET Core, geleneksel ASP.NET web uygulamaları oluşturmak için güçlü ve güvenilir bir platformu 4.x devam eder. ASP.NET MVC ve Web API geliştirme modelleri gibi zengin sayfa tabanlı uygulama geliştirme için oldukça uygun olan ve zengin üçüncü taraf bileşen ekosistemi özellikleri Web Forms destekler. Windows Azure ASP.NET 4.x uygulamaları için harika döngümüzün desteğine sahip ve geliştiricilerin çoğu Bu platformla bilginiz.

> ### <a name="references--modern-web-applications"></a>Başvuruları – Modern Web uygulamaları
> - **ASP.NET Core giriş**  
> <https://docs.microsoft.com/aspnet/core/>
> - **Altı anahtar avantajları, ASP.NET farklı ve daha iyi oluşturan çekirdek**  
> <https://blog.trigent.com/six-key-benefits-of-asp-net-core-1-0-which-make-it-different-better/>
> - **ASP.NET çekirdek test etme**  
> <https://docs.microsoft.com/aspnet/core/testing/>

>[!div class="step-by-step"]
[Önceki] (index.md) [sonraki] (choose-between-traditional-web-and-single-page-apps.md)
