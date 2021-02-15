---
title: ASP.NET Core geçiş yaparken dağıtım senaryoları
description: ASP.NET 'den ASP.NET Core 'e geçiş yaparken kullanılabilecek, yan yana ve aşamalı geçişlere izin veren, dağıtıma yönelik farklı yaklaşımlara genel bakış.
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: 8a3b658c777f2243c7c63908d9d0b24822b6790e
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100488912"
---
# <a name="deployment-scenarios-when-migrating-to-aspnet-core"></a>ASP.NET Core geçiş yaparken dağıtım senaryoları

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Mevcut ASP.NET MVC ve Web API Apps, IIS ve Windows üzerinde çalışır. Büyük uygulamalar, ASP.NET Core taşıma sırasında aşamalı veya yan yana bir yaklaşım gerektirebilir. Önceki bölümlerde, büyük .NET Framework uygulamalarını aşamalar halinde ASP.NET Core geçirmeye yönelik bir dizi strateji öğrendiniz. Bu bölümde, bir kısmını geçirirken üretimde orijinal uygulamanın bakımını yapma ihtiyacı olduğunda farklı dağıtım senaryolarına nasıl ulaşılacağını göreceksiniz.

## <a name="split-a-large-web-app"></a>Büyük bir Web uygulamasını bölme

Şu anda tek bir Web sitesinde IIS üzerinde barındırılan büyük bir Web uygulamasının yaygın senaryosunu göz önünde bulundurun. Büyük uygulama içinde, işlevselliği farklı yollara ve/veya dizinlere bölünmüştür. Uygulama, MVC görünümlerinin ve API uç noktalarının bir karışımıdır. MVC yolları, işlevleri temel alan birçok farklı yol ve standart yol şablonu kullanılarak uygulamanın kökünden itibaren başlangıç içerir `/{controller}/{action}/{id?}` . API uç noktaları benzer bir düzene uyar, ancak tümü bir kök altında `/api` .

Uygulamanın taşıma görevinin, MVC işlevselliği veya API işlevselliği ilk ASP.NET Core geçirilecek şekilde bölündüğü varsayılırsa, özgün site başka bir yerde çalışan yeni ASP.NET Core uygulamayla sorunsuz bir şekilde çalışmaya devam eder mi? Sistemin kullanıcıları, bunları değiştirmek kesinlikle gerekli olmadığı müddetçe geçişten önceki URL 'Leri görmeye devam etmelidir.

Neyse ki IIS, çok özellik zengin bir Web sunucusudur ve bir süredir bir süre içinde bulunan iki özellik [URL yeniden yazma modülü ve uygulama Isteği yönlendirme](https://docs.microsoft.com/iis/extensions/url-rewrite-module/reverse-proxy-with-url-rewrite-v2-and-application-request-routing)' dir. IIS, bu özellikleri kullanarak, istemci isteklerini uygun arka uç Web uygulamasına yönlendiren bir [ters proxy](https://docs.microsoft.com/iis/extensions/url-rewrite-module/reverse-proxy-with-url-rewrite-v2-and-application-request-routing)işlevi görebilir. IIS 'yi ters bir ara sunucu olarak yapılandırmak için uygulama Isteği yönlendirme özelliğindeki **proxy 'Yi etkinleştir** onay kutusunu işaretleyin ve aşağıdakine benzer bir URL yeniden yazma kuralı ekleyin:

```xml
<rule name="NetCoreProxy">
  <match url="(.*)> />
  <action type="Rewrite" url="http://servername/{R:1}" />
</rule>
```

Ters bir ara sunucu olarak, IIS belirli desenleri eşleşen trafiği, farklı sunuculardaki potansiyel olarak tamamen ayrı uygulamalarla yönlendirebilir.

Yalnızca URL yeniden yazma modülünü (Belki de ana bilgisayar üstbilgileri ile Birleşik) kullanarak IIS, her biri farklı .NET sürümlerini çalıştıran birden çok Web sitesini kolayca destekleyebilir. Büyük bir Web uygulaması, her biri farklı IP adreslerine ve/veya ana bilgisayar başlığına yanıt veren tek bir Web sitesi olarak veya belirli URL yollarına yanıt veren bir veya daha fazla alt uygulama (yani, URL yeniden yazma gerektirse) bir koleksiyon olarak dağıtılabilir.

> [!IMPORTANT]
> Alt etki alanları genellikle en üstteki iki düzeyden önceki bir etki alanının bölümüne başvurur. Örneğin, etki alanında etki `api.contoso.com` `api` `contoso.com` alanının (kendisi `contoso` etki alanı adı ve `.com` en üst düzey etki alanı veya TLD) bir alt etki alanıdır. URL yolları, ile başlayan, etki alanı adını izleyen URL 'nin bölümüne başvurur `/` . URL `https://contoso.com/api` 'nin bir yolu vardır `/api` .

Tek bir uygulamayı barındırmak için aynı veya farklı alt etki alanlarını (ve etki alanlarını) kullanmanın olumlu ve olumsuz yönleri vardır. [CORS](https://docs.microsoft.com/aspnet/core/security/cors) gibi mekanizmalar kullanılarak tanımlama bilgileri ve uygulama içi iletişim gibi özellikler, dağıtılmış uygulamalarda daha fazla yapılandırmanın düzgün çalışmasını gerektirebilir. Ancak, farklı alt etki alanları kullanan uygulamalar, istekleri tamamen farklı ağ hedeflerine yönlendirmek için DNS 'yi daha kolay bir şekilde kullanabilir ve bu sayede IIS 'nin ters ara sunucu olarak davranmasına gerek kalmadan çok sayıda farklı sunucuya (sanal veya diğer) daha kolay bir şekilde dağıtılabilir.

Yukarıda açıklanan örnekte, API uç noktalarının ASP.NET Core, uygulamanın ilk parçası olarak tasarlandığını varsayın. Bu durumda, yeni bir ASP.NET Core uygulaması, IIS 'de mevcut ASP.NET MVC web *sitesi* içinde ayrı bir Web *uygulaması* olarak oluşturulur ve barındırılır. Özgün Web sitesinin bir alt öğesi olarak eklenecekse ve *API* adı verilecek olduğundan, varsayılan yolu artık ile başlamamalıdır `api/` . Bunu korumak, formun URL 'Leri ile eşleşmesine neden olur `/api/api/endpoint` .

Şekil 5-1, mevcut *Dotnetmvcapp* sitesinin bir PARÇASı olarak ııs yöneticisinde ASP.NET Core 2,1 *API* uygulamasının nasıl göründüğünü gösterir.

![.NET Framework sitesi içinde API uygulamasını gösteren IIS Yöneticisi](./media/Figure5-1.png)

**Şekil 5-1**. IIS 'de .NET Core uygulaması olan site .NET Framework.

*Dotnetmvcapp* sitesi, .NET Framework 4.7.2 üzerinde çalışan bir MVC 5 uygulaması olarak barındırılır. Kendi IIS uygulama havuzu tümleşik modda yapılandırılmış ve .NET CLR Version 4.0.30319 çalıştırıyorsa. *API* uygulaması, .NET Framework 4.6.1 () üzerinde çalışan bir ASP.NET Core uygulamasıdır `net461` . *Dotnetmvcapp* 'e yenı bir IIS uygulaması olarak eklenmiştir ve kendi uygulama havuzunu kullanacak şekilde yapılandırılmıştır. Uygulama havuzu tümleşik modda da çalışır, ancak [ASP.NET Core modülü](https://docs.microsoft.com/aspnet/core/host-and-deploy/aspnet-core-module?view=aspnetcore-2.1&preserve-view=true)kullanılarak yürütüleceği Için, **yönetilen kod IÇERMEYEN** bir .NET CLR sürümü ile yapılandırılır. ASP.NET Core uygulamasının sürümü yalnızca bir örnektir. Ayrıca .NET Core 3,1 veya .NET 5,0 ' de çalışacak şekilde yapılandırılabilir. Bu noktada, artık .NET Framework kitaplıklarını hedefleyemiyor (bkz [. doğru .NET Core sürümünü seçme](choose-net-core-version.md))

Bu şekilde yapılandırıldığında, ASP.NET Core uygulamasının API 'Lerinin düzgün şekilde yönlendirilmesi için yapılması gereken tek değişiklik, varsayılan yol şablonunu ' den ' ye değiştirmesidir `[Route("[api/controller]")]` `[Route("[controller]")]` .

Alternatif olarak, ASP.NET Core uygulaması IIS 'de başka bir üst düzey Web sitesi olabilir. Bu durumda, başlangıç sitesini, yol ile başlıyorsa diğer uygulamaya yönlendiren bir yeniden yazma kuralı ( [URL yeniden yazma](https://www.iis.net/downloads/microsoft/url-rewrite)ile) kullanacak şekilde yapılandırabilirsiniz `/api` . ASP.NET Core uygulaması, yolu için farklı bir ana bilgisayar üst bilgisi kullanabilir ve bu sayede ana uygulamayla çakışmaz, ancak yine de kök tabanlı yollar kullanan isteklere yanıt verebilir.

Örnek olarak, Şekil 5-1 ' de kullanılan ASP.NET Core uygulaması IIS Web sitesi olarak yapılandırılmış başka bir klasöre dağıtılabilir. Site, **yönetilen kod olmadan** daha önce olduğu gibi yapılandırılmış bir uygulama havuzu kullanmalıdır. Sunucu üzerindeki benzersiz bir ana bilgisayar adına yanıt vermek için bağlamalarını yapılandırın (örneğin,) `api.contoso.com` . URL yeniden yazmayı, eşleşen istekleri yeniden yazmak üzere yapılandırmak için `/api` yalnızca IIS sunucusu (veya ayrı site) düzeyinde yeni bir gelen kuralı ekleyin. Düzeniyle eşleştirin `^/api(.*)` ve bir eylem türü `Rewrite` ve bir yeniden yazma URL 'si belirtin `api.contoso.com/{R:1}` . `(.*)`Eşleştirme modelinde ve yeniden yazma URL 'sinde kullanmanın birleşimi, `{R:1}` yolun geri KALANıNıN yeni URL ile kullanılmasını sağlayacaktır. Bu şekilde, aynı IIS sunucusundaki ayrı siteler .NET 'in ayrı sürümlerini çalıştırıyor olabilir, ancak Internet 'Te tek bir Web uygulaması olarak gözükme yapılabilir. Şekil 5-2, IIS 'de ayrı Web sitesiyle yapılandırılan yeniden yazma kuralını gösterir.

![Alt klasör isteklerini ayrı Web sitesine yönlendirmek için URL yeniden yazma kuralını gösteren IIS Yöneticisi](./media/Figure5-2.png)

**Şekil 5-2**. Alt klasör isteklerini başka bir Web sitesine yeniden yazmak için kuralı yeniden yazın.

Uygulamanız IIS içindeki farklı siteler veya uygulamalar arasında çoklu oturum açma gerektiriyorsa, bu senaryoyu destekleme hakkında ayrıntılı yönergeler için [ASP.net Apps arasında kimlik doğrulama tanımlama bilgilerini paylaşma](https://docs.microsoft.com/aspnet/core/host-and-deploy/iis/) hakkındaki belgelere bakın.

## <a name="summary"></a>Özet

.NET Framework büyük uygulamaları ASP.NET Core ' A taşımaya yönelik yaygın bir yaklaşım, uygulamanın tek bir bölümünü tek tek taşımak için tek tek seçmektir. Uygulamanın her parçası, ilk yapılandırmasında çalışan bazı bölümler ve .NET Core 'un bazı sürümlerinde çalışan diğer parçalar sayesinde uygulamanın tamamı çalışır durumda ve kullanılabilir durumda kalır. Bu yaklaşımı izleyerek, büyük bir uygulama geçişi artımlı olarak gerçekleştirilebilir. Bu yaklaşım, daha hızlı geri bildirim sağlayarak ve test etme ile ilgili toplam yüzey alanını azaltarak riski sınırlandırmaya neden olur. Ayrıca, performans artışı gibi .NET Core 'un sağladığı avantajlardan daha hızlı bir şekilde tahakkuk etmesine olanak tanır. ASP.NET Core uygulamaların IIS 'de barındırılmasına gerek kalmasa da IIS, aynı IIS örneğindeki ve hatta farklı sunucularda barındırılan .NET Framework ve ASP.NET Core uygulamaları içeren çeşitli barındırma senaryolarını destekleyecek şekilde yapılandırılabilen çok esnek ve güçlü bir Web sunucusu kalır.

## <a name="references"></a>Başvurular

- [IIS ile Windows üzerinde ASP.NET Core barındırma](https://docs.microsoft.com/aspnet/core/host-and-deploy/iis/)
- [URL yeniden yazma modülü ve uygulama Isteği yönlendirme](https://docs.microsoft.com/iis/extensions/url-rewrite-module/reverse-proxy-with-url-rewrite-v2-and-application-request-routing)
- [URL yeniden yazma](https://www.iis.net/downloads/microsoft/url-rewrite)
- [ASP.NET Core Modülü](https://docs.microsoft.com/aspnet/core/host-and-deploy/aspnet-core-module?view=aspnetcore-2.1&preserve-view=true)
- [ASP.NET uygulamaları arasında kimlik doğrulama tanımlama bilgilerini paylaşma](https://docs.microsoft.com/aspnet/core/host-and-deploy/iis/)

>[!div class="step-by-step"]
>[Önceki](example-migration-eshop.md) 
> [Sonraki](summary.md)
