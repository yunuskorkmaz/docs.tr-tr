---
title: Modern web uygulamalarının özellikleri
description: ASP.NET Core ve Azure ile modern Web uygulamaları tasarlama | Modern web uygulamalarının özellikleri
author: ardalis
ms.author: wiwagn
ms.date: 01/30/2019
ms.openlocfilehash: eacc66ff5d2c4bfb8d8645bc6bd319eab52437a3
ms.sourcegitcommit: 3500c4845f96a91a438a02ef2c6b4eef45a5e2af
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/07/2019
ms.locfileid: "55828130"
---
# <a name="characteristics-of-modern-web-applications"></a>Modern Web uygulamalarının özellikleri

> "… uygun tasarımla özelliği hesaplı bir şekilde gelir. Bu yaklaşım işlemini merkezileştirir, ancak başarılı olması devam ediyor."  
> _\- Dennis Ritchie_

Modern web uygulamaları, daha yüksek kullanıcı beklentileri ve hiç olmadığı kadar büyük taleplerine sahiptir. Günümüzün web uygulamalarını kullanılabilir 24/7'den, dünyanın her yerinden ve neredeyse tüm cihazlardan kullanılabilir olması veya ekran boyutu beklenir. Web uygulamaları, güvenli, esnek ve artış taleplerini karşılamak için ölçeklenebilir olması gerekir. Giderek karmaşık senaryolar JavaScript kullanarak ve verimli bir şekilde web API'leri iletişim kuran istemci üzerinde oluşturulan zengin kullanıcı deneyimleri tarafından yapılması gerekir.

ASP.NET Core, modern web uygulamaları ve bulut tabanlı bir barındırma senaryolar için optimize edilmiştir. Modüler tasarımı, yalnızca gerçekten, uygulama güvenliği ve barındırma kaynak gereksinimlerini azaltırken performans iyileştirme kullandıkları özelliklere bağımlı uygulamalar sağlar.

## <a name="reference-application-eshoponweb"></a>Başvuru uygulama: eShopOnWeb

Bu kılavuz, bir başvuru uygulaması içerir. _eShopOnWeb_, bazı ilkeler ve öneriler gösterir. Uygulama gömlekler, kahve bardaklar ve pazarlama diğer öğeleri Kataloğu aracılığıyla göz atma destekleyen basit bir çevrimiçi mağazadır. Başvuru uygulaması anlamak daha kolay yapmak için kasıtlı olarak basit bir işlemdir.

**Şekil 2-1.** eShopOnWeb

![](./media/image2-1.png)

> ### <a name="reference-application"></a>Başvuru uygulaması
>
> - **eShopOnWeb**  
>   <https://github.com/dotnet/eShopOnWeb>

## <a name="cloud-hosted-and-scalable"></a>Bulutta barındırılan ve ölçeklenebilir

ASP.NET Core, düşük bellek ve işleme düzeyi yüksek olduğu için (genel bulut, özel bulut, herhangi bir buluttaki) bulut için optimize edilmiştir. ASP.NET Core uygulamalarının daha küçük kaplama alanı, daha fazla belgeyi donanımda barındırabilir ve ödeme-olarak-kullanmakta gidin, bulut barındırma hizmetleri daha az kaynaklar için ödeme yaparsınız anlamına gelir. Daha yüksek performanslı, sunucuları ve barındırma altyapısına yatırım yapmaya gerek daha da azaltmak daha fazla müşteriye aynı donanım, verilen bir uygulamadan kullanılabileceği anlamına gelir.

## <a name="cross-platform"></a>Platformlar arası

ASP.NET Core platformlar arası ve Linux, macOS ve Windows üzerinde çalıştırabilirsiniz. Bu hem geliştirme hem de ASP.NET Core ile oluşturulan uygulamaları dağıtımını için birçok yeni seçenek açar. Docker kapsayıcıları - hem Linux hem de Windows - avantajlarından yararlanmak ASP.NET Core uygulamalar, ana bilgisayar [kapsayıcıları ve mikro Hizmetler](../microservices-architecture/index.md).

## <a name="modular-and-loosely-coupled"></a>Modüler ve gevşek bir şekilde

Birinci sınıf vatandaşlar .NET Core NuGet paketleri olan ve ASP.NET Core uygulamaları birçok kitaplıkları NuGet aracılığıyla oluşur. İşlevinin bu ayrıntı düzeyi, uygulamaları yalnızca bağlıdır ve gerçekten, kendi Ayak izi ve güvenlik açığı yüzey alanı azaltma gerektirdikleri işlevi dağıtmaya sağlamaya yardımcı olur.

ASP.NET Core da tam olarak destekler [bağımlılık ekleme](https://deviq.com/dependency-injection/), hem iç hem de uygulama düzeyi. Arabirimleri, gerektiğinde takas edilebilir birden çok uygulamalara sahip olabilir. Bu arabirimler için gevşek eşleştirmektir uygulamaların bağımlılık ekleme verir yerine bunları genişletmek daha kolay hale getirir, belirli uygulamaları korumak ve test edin.

## <a name="easily-tested-with-automated-tests"></a>Kolayca otomatik testler ile test

Birim testi ASP.NET Core uygulamaları desteklemek ve kendi gevşek eşleştirme ve bağımlılık ekleme desteği altyapıyla ilgili endişelerini test amacıyla sahte uygulamaları ile takas yapmayı kolaylaştırır. ASP.NET Core, ayrıca bellekte ana bilgisayar uygulamaları için kullanılabilir bir TestServer birlikte gelir. İşlevsel testleri istekleri (Ara yazılım, yönlendirme, model bağlama, filtreler, vb. dahil) tüm uygulama yığınını kullanan bu bellek içi sunucuya yapabilir ve tüm bir kesir zaman içinde bir yanıt almak, gerçek bir sunucudaki bir uygulamayı barındırmak için gereken ve ağ katmanı aracılığıyla istekleri. Bu testler yazmak özellikle kolaydır ve değerli, API'leri, modern web uygulamaları gittikçe önem kazandığını.

## <a name="traditional-and-spa-behaviors-supported"></a>Desteklenen geleneksel ve SPA davranışları

Geleneksel web uygulamaları, biraz istemci tarafı davranışı söz konusu, ancak bunun yerine tüm gezinti, sorgular ve uygulama yapmanız gerekebilecek güncelleştirmeleri için sunucuda güvenmiştir. Kullanıcı tarafından yapılan her yeni işlem yeni bir web isteği, son kullanıcının tarayıcısında tam sayfada yeniden yüklenmesi olan sonuç çevrilmesi. Klasik Model-View-Controller (MVC) çerçeveleri, bu yaklaşım genellikle hangi sırayla ve bir modeli ile çalışmak bir görünüme dönmek bir farklı denetleyici eylemi için karşılık gelen her yeni isteği ile izleyin. Belirli bir sayfada tek bazı işlemler (zaman uyumsuz JavaScript ve XML) AJAX işlevselliği ile Gelişmiş, ancak birçok farklı MVC görünümleri ve URL uç noktalarına genel uygulama mimarisi kullanılır. Ayrıca, ASP.NET Core MVC Razor sayfaları, MVC stil sayfaları düzenlemek için daha basit bir yol da destekler.

Tek sayfa uygulamaları (Spa'lar) aksine, çok az dinamik olarak üretilen sunucu tarafı sayfa yüklemelerinin (varsa) içerir. Birçok Spa'lar başlatmak ve uygulamayı çalıştırmak için gerekli JavaScript kitaplıklarını yükleyen bir statik HTML dosyası içinde başlatılır. Bu uygulamalar, web API'leri için veri gereksinimlerine ağır kullanımını olun ve çok daha zengin kullanıcı deneyimleri sağlayabilir.

Birçok web uygulamaları (genellikle için içerik) geleneksel web uygulama davranışını ve Spa'lar (etkileşim için) bir bileşimini içerir. ASP.NET Core MVC iki destekler (görünümleri ya da sayfa tabanlı) ve aynı araçları kullanarak ve framework kitaplıkları arka plandaki aynı uygulamada, web API'leri.

## <a name="simple-development-and-deployment"></a>Basit bir geliştirme ve dağıtma

Basit Metin Düzenleyicisi ve komut satırı arabirimleri veya tam özellikli bir geliştirme ortamları gibi Visual Studio kullanarak ASP.NET Core uygulamaları yazılabilir. Tek yapılı uygulamalar genellikle tek bir uç noktasına dağıtılır. Dağıtımlar, sürekli tümleştirme (CI) ve sürekli teslim (CD) işlem hattı bir parçası olarak gerçekleşecek şekilde kolayca otomatikleştirilebilir. Geleneksel bir CI/CD araçları yanı sıra Windows Azure destek git depoları için tümleşik olan ve bir belirtilen git dalı veya da etiketi yapıldıkça güncelleştirmelerini otomatik olarak dağıtabilirsiniz.

## <a name="traditional-aspnet-and-web-forms"></a>Geleneksel ASP.NET ve Web formları

Ek ASP.NET Core, geleneksel ASP.NET 4.x web uygulamaları oluşturmaya yönelik sağlam ve güvenilir bir platform olması devam eder. ASP.NET MVC ve Web API geliştirme modelleri yanı sıra zengin sayfa tabanlı uygulama geliştirme için uygun olan ve zengin üçüncü parti bileşeniniz ekosistemi özellikleri Web Forms destekler. Windows Azure ASP.NET 4.x uygulamalar için harika çalışmalarını uzun süredir davam desteği bulunur ve birçok geliştiricinin Bu platformla ilgili bilgi sahibi.

> ### <a name="references--modern-web-applications"></a>Başvuruları – Modern Web uygulamaları
>
> - **ASP.NET Core'a giriş**  
>   <https://docs.microsoft.com/aspnet/core/>
> - **Altı anahtar avantajları, ASP.NET farklı ve daha iyi hale çekirdek**  
>   <https://blog.trigent.com/six-key-benefits-of-asp-net-core-1-0-which-make-it-different-better/>
> - **ASP.NET Core testi**  
>   <https://docs.microsoft.com/aspnet/core/testing/>

>[!div class="step-by-step"]
>[Önceki](index.md)
>[İleri](choose-between-traditional-web-and-single-page-apps.md)
