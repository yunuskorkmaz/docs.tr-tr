---
title: Internet Information Services Barındırma En İyi Uygulamaları
ms.date: 03/30/2017
ms.assetid: 0834768e-9665-46bf-86eb-d4b09ab91af5
ms.openlocfilehash: e09a42f0f4a98728e588961425d8b6f5b50e6ccb
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69957223"
---
# <a name="internet-information-services-hosting-best-practices"></a>Internet Information Services Barındırma En İyi Uygulamaları
Bu konuda Windows Communication Foundation (WCF) Hizmetleri barındırmak için bazı en iyi yöntemler özetlenmektedir.  
  
## <a name="implementing-wcf-services-as-dlls"></a>WCF hizmetlerini dll olarak uygulama  
 Bir Web uygulamasının \bin dizinine dağıtılan bir DLL olarak bir WCF hizmeti uygulamak, hizmeti Web uygulaması modelinin dışında (örneğin, Internet Information Services (IIS) dağıtılan bir test ortamında yeniden kullanmanıza olanak tanır.  
  
## <a name="service-hosts-in-iis-hosted-applications"></a>IIS tarafından barındırılan uygulamalarda hizmet ana bilgisayarları  
 IIS barındırma ortamı tarafından yerel olarak desteklenmeyen ağ taşımalarını dinleyen yeni hizmet Konakları oluşturmak için zorunlu Self-Host API 'Lerini kullanmayın (örneğin, TCP iletişimi IIS 6,0 ' de yerel olarak desteklenmediğinden, TCP hizmetlerini barındırmak için IIS 6,0). Bu yaklaşım önerilmez. İmperatively oluşturulan hizmet ana bilgisayarları IIS barındırma ortamı içinde bilinmiyor. Kritik nokta, imperatively tarafından oluşturulan hizmetler tarafından gerçekleştirilen işleme, barındırma uygulama havuzunun boşta olup olmadığını belirlediğinde IIS tarafından hesaba katılmaz. Sonuç olarak, imperatively tarafından oluşturulan hizmet Konakları olan uygulamalarda IIS ana bilgisayar işlemlerinin ortadan kaldırılmış bir IIS barındırma ortamı vardır.  
  
## <a name="uris-and-iis-hosted-endpoints"></a>URI 'Ler ve IIS tarafından barındırılan uç noktalar  
 IIS tarafından barındırılan bir hizmetin uç noktaları, mutlak adresler değil göreli Tekdüzen Kaynak tanımlayıcıları (URI) kullanılarak yapılandırılmalıdır. Bu, uç nokta adresinin barındırma uygulamasına ait olan URI adresleri kümesi içinde olmasını güvence altına alır ve ileti tabanlı etkinleştirmenin beklenen şekilde gerçekleşmesini sağlar.  
  
## <a name="state-management-and-process-recycling"></a>Durum yönetimi ve Işlem geri dönüştürme  
 IIS barındırma ortamı, bellekteki yerel durumu korumayan hizmetler için en iyi duruma getirilmiştir. IIS, çeşitli dış ve iç olaylara yanıt olarak ana bilgisayar işlemini geri dönüştürür ve yalnızca bellekte depolanan geçici durumun kaybolmasına neden olur. IIS 'de barındırılan hizmetler, bir uygulamanın (örneğin, bir veritabanında) veya bir uygulama geri dönüşüm olayı gerçekleştiğinde kolayca yeniden oluşturulabilen bir bellek içi önbellekte yer almalıdır.  
  
> [!NOTE]
> WCF protokolleri ileti katmanı güvenilirliği ve güvenliği için kullanılan protokoller, geçici bellek içi durumu kullanır. WCF güvenilir oturumlar ve güvenlik oturumları, uygulama geri dönüştürme nedeniyle beklenmedik bir şekilde sonlandırılabilir. Bu protokollerin kullanıldığı IIS tarafından barındırılan uygulamalar, uygulama katmanı durumunun (örneğin, bir uygulama katmanı yapısı veya özel bağıntı üstbilgisi) bağıntısı için, WCF tarafından sağlanmış oturum anahtarı dışında bir şeye bağlı olmalıdır veya devre dışı bırakılır Barındırılan uygulama için IIS işlem geri dönüşümü.  
  
## <a name="optimizing-performance-in-middle-tier-scenarios"></a>Orta katman senaryolarında performansı en iyi duruma getirme  
 *Orta katman senaryosunda*en iyi performansı elde etmek için, gelen iletilere yanıt olarak diğer hizmetlere çağrı yapan bir hizmet olan bir kez, WCF hizmeti istemcisini uzak hizmete bir kez oluşturun ve birden çok gelen istek genelinde yeniden kullanın. WCF hizmeti istemcilerini örnekleme, önceden var olan bir istemci örneğinde hizmet çağrısı yapmaya yönelik maliyetli bir işlemdir ve orta katmanlı senaryolar uzak istemcileri istekler arasında önbelleğe alarak ayrı performans kazançları üretir. WCF hizmeti istemcileri iş parçacığı açısından güvenlidir, bu nedenle birden çok iş parçacığında bir istemciye erişimi eşitlemeniz gerekmez.  
  
 Orta katman senaryoları, `svcutil /a` seçeneği tarafından oluşturulan zaman uyumsuz API 'leri kullanarak da performans kazançları üretir. Bu seçenek, [ServiceModel meta veri yardımcı programı aracının (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) her `BeginXXX/EndXXX` bir hizmet işlemi için yöntemler oluşturmasına neden olur ve bu da arka plan iş parçacıklarında uzak hizmetlere uzun süreli çağrılar yapılmasına izin verir. `/a`  
  
## <a name="wcf-in-multi-homed-or-multi-named-scenarios"></a>Çoklu bağlantılı veya çok adlı senaryolarda WCF  
 Bir dizi bilgisayarın ortak bir dış adı ( `http://www.contoso.com`Örneğin,) paylaştığı ancak farklı ana bilgisayar adları tarafından tek tek adreslendiği bir IIS Web grubunun içinde WCF Hizmetleri dağıtabilirsiniz (örneğin, `http://www.contoso.com` trafiği iki farklı makineye yönlendirebilir Adlandırılmış `http://machine1.internal.contoso.com` ve`http://machine2.internal.contoso.com`). Bu dağıtım senaryosu WCF tarafından tam olarak desteklenir, ancak hizmet meta verilerinde doğru (harici) ana bilgisayar adını (Web Hizmetleri Açıklama Dili) göstermek için WCF hizmetleri barındıran IIS Web sitesinin özel yapılandırmasını gerektirir.  
  
 Hizmet meta verileri WCF 'nin oluşturduğu doğru ana bilgisayar adının göründüğünden emin olmak için, WCF hizmetlerini barındıran IIS Web sitesinin varsayılan kimliğini açık bir ana bilgisayar adı kullanacak şekilde yapılandırın. Örneğin, `www.contoso.com` grubun içinde bulunan bilgisayarlar için bir IIS site bağlaması *: 80: www. contoso. com for http ve \*: 443: www. contoso. com for https.  
  
 IIS Web sitesi bağlamalarını IIS Microsoft Yönetim Konsolu (MMC) ek bileşenini kullanarak yapılandırabilirsiniz.  
  
## <a name="application-pools-running-in-different-user-contexts-overwrite-assemblies-from-other-accounts-in-the-temporary-folder"></a>Farklı Kullanıcı bağlamlarında çalışan uygulama havuzları, geçici klasördeki diğer hesaplardan derlemelerin üzerine yazar  
 Farklı Kullanıcı bağlamlarında çalışan uygulama havuzlarının geçici ASP.NET dosyaları klasöründeki diğer hesaplardan derlemelerin üzerine yazamayacağını sağlamak için farklı kimlikler ve farklı uygulamalar için geçici klasörler kullanın. Örneğin,/Application1 ve/application2 iki sanal uygulamanız varsa iki farklı kimlik ile iki uygulama havuzu (A ve B) oluşturabilirsiniz. A uygulama havuzu bir kullanıcı kimliği (Kullanıcı1) altında, uygulama havuzu B başka bir kullanıcı kimliği (kullanıcı2) altında çalışabilir ve/Application1 ' i bir ve/application2 kullanarak B 'yi kullanacak şekilde yapılandırabilirler.  
  
 Web. config dosyasında, > kullanarak \< system.web/compilation/@tempFoldergeçici klasörü yapılandırabilirsiniz. /Application1 için, "c:\tempForUser1" olabilir ve application2 için "c:\tempForUser2" olabilir. Bu klasörlere ilgili yazma iznini iki kimlik için verin.  
  
 Sonra kullanıcı2,/Application2 (c:\tempForUser1 altında) kod oluşturma klasörünü değiştiremez.  
  
## <a name="enabling-asynchronous-processing"></a>Zaman uyumsuz işlemeyi etkinleştirme  
 Varsayılan olarak, IIS 6,0 ve önceki sürümlerde barındırılan bir WCF hizmetine gönderilen iletiler, zaman uyumlu bir şekilde işlenir. ASP.NET, kendi iş parçacığında (ASP.NET Worker iş parçacığı) WCF 'ye çağrılar sağlar ve WCF, isteği işlemek için başka bir iş parçacığı kullanır. WCF, işlemesini tamamlayana kadar ASP.NET Worker iş parçacığı üzerinde tutulur. Bu, isteklerin zaman uyumlu olarak işlenmesine yol açar. İstekleri zaman uyumsuz olarak işlemek, isteği işlemek için gereken iş parçacığı sayısını azalttığından daha fazla ölçeklenebilirlik sağlar-WCF, isteği işlerken ASP.NET iş parçacığına açık tutmaz. Sunucu *hizmet reddi* (DOS) saldırılarını açan gelen istekleri kısıtlama yolu OLMADıĞıNDAN, IIS 6,0 çalıştıran makineler için zaman uyumsuz davranışın kullanılması önerilmez. IIS 7,0 ' den itibaren, eşzamanlı bir istek kısıtlaması sunuldu: `[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ASP.NET\2.0.50727.0]"MaxConcurrentRequestsPerCpu`. Bu yeni kısıtlama sayesinde zaman uyumsuz işlemenin kullanılması güvenlidir.  IIS 7,0 ' de varsayılan olarak, zaman uyumsuz işleyici ve modül kaydedilir. Bu kapatılmışsa, uygulamanızın Web. config dosyasındaki isteklerin zaman uyumsuz işlemesini el ile etkinleştirebilirsiniz. Kullandığınız ayarlar ayarlarınıza bağlıdır `aspNetCompatibilityEnabled` . `aspNetCompatibilityEnabled` Olarak ayarlarsanız`false`, aşağıdakiyapılandırmaparçacığındagösterildiği`System.ServiceModel.Activation.ServiceHttpModule` gibi öğesini yapılandırın.  
  
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
  
 `System.ServiceModel.Activation.ServiceHttpHandlerFactory` Olarak `aspNetCompatibilityEnabled` ayarlarsanız,aşağıdakiyapılandırmaparçacığındagösterildiği`true`gibi öğesini yapılandırın.  
  
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

- [Hizmet barındırma örnekleri](../samples/hosting.md)
- [Windows Server App Fabric barındırma özellikleri](https://go.microsoft.com/fwlink/?LinkId=201276)
