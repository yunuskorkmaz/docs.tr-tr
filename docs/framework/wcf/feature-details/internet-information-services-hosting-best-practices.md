---
title: Internet Information Services Barındırma En İyi Uygulamaları
ms.date: 03/30/2017
ms.assetid: 0834768e-9665-46bf-86eb-d4b09ab91af5
ms.openlocfilehash: 3be9d4c81f891ad898099ba9041a09b16388b7e4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184711"
---
# <a name="internet-information-services-hosting-best-practices"></a>Internet Information Services Barındırma En İyi Uygulamaları
Bu konu, Windows Communication Foundation (WCF) hizmetlerini barındırmak için en iyi uygulamaları özetlemektedir.  
  
## <a name="implementing-wcf-services-as-dlls"></a>WCF Hizmetlerinin DL olarak uygulanması  
 Bir WCF hizmetini, bir Web uygulamasının \bin dizinine dağıtılan bir DLL olarak uygulamak, hizmeti Web uygulama modelinin dışında( örneğin, Internet Information Services (IIS) dağıtılmayan bir test ortamında yeniden kullanmanıza olanak tanır.  
  
## <a name="service-hosts-in-iis-hosted-applications"></a>IIS Tarafından Barındırılan Uygulamalarda Hizmet Barındıran Sunucular  
 Zorunlu kendi barındırma API'lerini, IIS barındırma ortamı tarafından yerel olarak desteklenmeyen ağ aktarımlarında dinleyen yeni hizmet barındıran ları oluşturmak için kullanmayın (Örneğin, TCP iletişimi IIS 6.0'da yerel olarak desteklenmediği için IIS 6.0 TCP hizmetlerini barındırmak için). Bu yaklaşım önerilmez. Zorunlu olarak oluşturulan hizmet ana bilgisayarları IIS barındırma ortamında bilinmemektedir. Kritik nokta, barındırma uygulama havuzunun boşta olup olmadığını belirlerken zorunlu olarak oluşturulan hizmetler tarafından yapılan işlemlerin IIS tarafından muhasebelemediğidir. Sonuç olarak, bu tür zorunlu olarak oluşturulan hizmet ana bilgisayarları olan uygulamaların, IIS ana bilgisayar süreçlerini agresif bir şekilde bertaraf eden bir IIS barındırma ortamına sahip olmasıdır.  
  
## <a name="uris-and-iis-hosted-endpoints"></a>URI'ler ve IIS Tarafından Barındırılan Uç Noktalar  
 IIS tarafından barındırılan bir hizmetin bitiş noktaları, mutlak adresler kullanılarak değil, göreli Tekdüzen Kaynak Tanımlayıcıları (URI'ler) kullanılarak yapılandırılmalıdır. Bu, bitiş noktası adresinin barındırma uygulamasına ait URI adresleri kümesine düştüğünü garanti eder ve ileti tabanlı etkinleştirmenin beklendiği gibi gerçekleşmesini sağlar.  
  
## <a name="state-management-and-process-recycling"></a>Devlet Yönetimi ve Süreç Geri Dönüşümü  
 IIS barındırma ortamı, bellekte yerel durumu korumayan hizmetler için optimize edilebiyi raydır. IIS, çeşitli dış ve iç olaylara yanıt olarak ana bilgisayar işlemini geri dönüştürür ve yalnızca bellekte depolanan geçici durumların kaybolmasına neden olur. IIS'de barındırılan hizmetler, durumlarını işlemin dışında (örneğin, bir veritabanında) veya bir uygulama geri dönüştürme olayı oluşursa kolayca yeniden oluşturulabilecek bir bellek önbelleğinde depolamalıdır.  
  
> [!NOTE]
> WCF'nin ileti katmanı güvenilirliği ve güvenliği için kullandığı protokoller, geçici bellek içi durumu kullanır. WCF güvenilir oturumları ve güvenlik oturumları, uygulama geri dönüşümleri nedeniyle beklenmedik bir şekilde sona erebilir. Bu protokollerden yararlanan IIS barındırılan uygulamalar, uygulama katmanı durumunu ilişkilendirme (örneğin, uygulama katmanı yapısı veya özel korelasyon üstbilgisi) için WCF tarafından sağlanan oturum anahtarından başka bir şeye bağlı olmalı veya devre dışı Barındırılan uygulama için IIS proses geri dönüşümü.  
  
## <a name="optimizing-performance-in-middle-tier-scenarios"></a>Orta Katman Senaryolarda Performansı Optimize Etme  
 Gelen iletilere yanıt olarak diğer hizmetlere sesilen bir hizmet olan *orta katman senaryosunda*en iyi performans için, WCF hizmet istemcisini bir kez uzak hizmete anında iletin ve birden çok gelen istekarasında yeniden kullanın. WCF hizmet istemcilerini anında algılamak, önceden varolan bir istemci örneğinde bir hizmet çağrısı yapmaya göre pahalı bir işlemdir ve orta katman senaryoları istekler arasında uzak istemcileri önbelleğe alarak farklı performans kazançları üretir. WCF hizmet istemcileri iş parçacığı için güvenlidir, bu nedenle birden çok iş parçacığı arasında bir istemciye erişimi eşitlemek gerekli değildir.  
  
 Orta katman senaryoları da `svcutil /a` seçenek tarafından oluşturulan eşzamanlı API'ler kullanarak performans kazançları üretir. Bu `/a` seçenek, [ServiceModel Metadata Utility Tool'un (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) her hizmet işlemi için yöntemler oluşturmasına `BeginXXX/EndXXX` neden olur ve bu da uzak hizmetlere uzun süreli aramaların arka plan iş parçacıkları üzerinde yapılmasına olanak tanır.  
  
## <a name="wcf-in-multi-homed-or-multi-named-scenarios"></a>Çok Homed veya Çok adlı senaryolarda WCF  
 WCF hizmetlerini, bir bilgisayar kümesinin ortak bir dış adı paylaştığı `http://www.contoso.com`(örneğin) ancak farklı ana bilgisayar adlarıyla tek tek `http://www.contoso.com` ele alınan bir IIS `http://machine1.internal.contoso.com` Web çiftliğinin içinde dağıtabilirsiniz (örneğin, trafiği iki farklı makineye yönlendirebilir ve). `http://machine2.internal.contoso.com` Bu dağıtım senaryosu tamamen WCF tarafından desteklenir, ancak hizmetin meta verilerinde (Web Hizmetleri Açıklama Dili) doğru (harici) ana bilgisayar adını görüntülemek için WCF hizmetlerini barındıran IIS Web sitesinin özel yapılandırmasını gerektirir.  
  
 WCF'nin oluşturduğu hizmet meta verilerinde doğru ana bilgisayar adının görünmesini sağlamak için, WCF hizmetlerini barındıran IIS Web sitesinin varsayılan kimliğini açık bir ana bilgisayar adı kullanacak şekilde yapılandırın. Örneğin, çiftliğin `www.contoso.com` içinde ikamet eden bilgisayarlar HTTP için *:80:www.contoso.com ve \*HTTPS için :443:www.contoso.com ciltleme iIS sitesi kullanmalıdır.  
  
 IIS Microsoft Yönetim Konsolu (MMC) snap-in'i kullanarak IIS Web sitesi bağlamalarını yapılandırabilirsiniz.  
  
## <a name="application-pools-running-in-different-user-contexts-overwrite-assemblies-from-other-accounts-in-the-temporary-folder"></a>Farklı Kullanıcı Bağlamlarında Çalışan Uygulama Havuzları Geçici Klasördeki Diğer Hesaplardan Derlemeleri Üzerine Yazar  
 Farklı kullanıcı bağlamlarında çalışan uygulama havuzlarının geçici ASP.NET dosyaları klasöründeki diğer hesaplardan derlemelerin üzerine yazamamasını sağlamak için, farklı uygulamalar için farklı kimlikler ve geçici klasörler kullanın. Örneğin, iki sanal uygulamanız varsa /Application1 ve / Application2, iki farklı kimlikle A ve B olmak üzere iki Uygulama havuzu oluşturabilirsiniz. Uygulama havuzu A bir kullanıcı kimliği (user1) altında çalışırken, B uygulama havuzu başka bir kullanıcı kimliği (user2) altında çalıştırılabilir ve /Application1'i B kullanmak için A ve /Application2'yi kullanacak şekilde yapılandırabilir.  
  
 Web.config'de, geçici klasörü> \< system.web/compilation/@tempFolder kullanarak yapılandırabilirsiniz. /Application1 için "c:\tempForUser1" ve uygulama2 için "c:\tempForUser2" olabilir. İki kimlik için bu klasörlere karşılık gelen yazma izni verir.  
  
 Sonra user2 /application2 için kod oluşturma klasörünü değiştiremez (c:\tempForUser1 altında).  
  
## <a name="enabling-asynchronous-processing"></a>Eşzamanlı işlemeyi etkinleştirme  
 Varsayılan olarak, IIS 6.0 ve daha önce barındırılan bir WCF hizmetine gönderilen iletiler eşzamanlı bir şekilde işlenir. ASP.NET wcf içine kendi iş parçacığı (ASP.NET alt iş parçacığı) aramaları ve WCF isteği işlemek için başka bir iş parçacığı kullanır. WCF, işleme işlemini tamamlayana kadar ASP.NET alt iş parçacığına tutunrabilir. Bu, isteklerin eşzamanlı olarak işlenmesine yol açar. İstekleri işleme, isteği işlemek için gereken iş parçacığı sayısını azalttığı için daha fazla ölçeklenebilirlik sağlar –WCF isteği işlerken ASP.NET iş parçacığına tutunmaz. Sunucuyu *Hizmet Reddi* (DOS) saldırılarına açan gelen istekleri azaltmanın bir yolu olmadığından, IIS 6.0 çalıştıran makineler için eşsenkronize davranış kullanılması önerilmez. IIS 7.0 ile başlayarak, eşzamanlı bir istek azaltma `[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ASP.NET\2.0.50727.0]"MaxConcurrentRequestsPerCpu`tanıtıldı: . Bu yeni gaz ile asynchronous işleme kullanmak güvenlidir.  Varsayılan olarak IIS 7.0'da, eşzamanlı işleyici ve modül kaydedilir. Bu kapatılmışsa, uygulamanızın Web.config dosyasındaki isteklerin eşsenkronize olarak işlenmesini el ile etkinleştirebilirsiniz. Kullandığınız ayarlar ayarınıza `aspNetCompatibilityEnabled` bağlıdır. `aspNetCompatibilityEnabled` Ayarladıysanız, aşağıdaki yapılandırma snippet'inde gösterildiği `System.ServiceModel.Activation.ServiceHttpModule` gibi yapılandırın. `false`  
  
```xml  
<system.serviceModel>  
    <serviceHostingEnvironment aspNetCompatibilityEnabled="false" />
  </system.serviceModel>  
  <system.webServer>  
    <modules>  
      <remove name="ServiceModel"/>  
      <add name="ServiceModel"
           preCondition="integratedMode,runtimeVersionv2.0"
           type="System.ServiceModel.Activation.ServiceHttpModule, System.ServiceModel,Version=3.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"/>  
    </modules>  
    </system.webServer>  
```  
  
 `aspNetCompatibilityEnabled` Eğer `true`ayarladıysanız, aşağıdaki config snippet gösterildiği `System.ServiceModel.Activation.ServiceHttpHandlerFactory` gibi yapılandırın.  
  
```xml  
<system.serviceModel>  
    <serviceHostingEnvironment aspNetCompatibilityEnabled="true" />
  </system.serviceModel>  
  <system.webServer>  
    <handlers>  
          <clear/>  
          <add name="TestAsyncHttpHandler"
               path="*.svc"
               verb="*"
               type="System.ServiceModel.Activation.ServiceHttpHandlerFactory, System.ServiceModel, Version=3.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
               />  
    </handlers>
  </system.webServer>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hizmet Barındırma Örnekleri](../samples/hosting.md)
- [Windows Server App Kumaş Barındırma Özellikleri](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))
