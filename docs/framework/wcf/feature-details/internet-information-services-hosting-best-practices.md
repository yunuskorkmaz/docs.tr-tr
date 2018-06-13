---
title: Internet Information Services Barındırma En İyi Uygulamaları
ms.date: 03/30/2017
ms.assetid: 0834768e-9665-46bf-86eb-d4b09ab91af5
ms.openlocfilehash: 119f14df9d46883a33272903558d83128501b293
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33495768"
---
# <a name="internet-information-services-hosting-best-practices"></a>Internet Information Services Barındırma En İyi Uygulamaları
Bu konu, Windows Communication Foundation (WCF) hizmetlerini barındıran bazı en iyi uygulamalar özetler.  
  
## <a name="implementing-wcf-services-as-dlls"></a>WCF hizmetleri DLL'ler olarak uygulama  
 Uygulama bir WCF hizmeti bir Web uygulaması \bin dizinine dağıtılmış bir DLL olarak hizmet Web uygulama modeli dışında Internet Information Services (IIS) dağıtılan olmayabilir bir test ortamında Örneğin, yeniden sağlar.  
  
## <a name="service-hosts-in-iis-hosted-applications"></a>IIS barındırılan uygulamalarında hizmet konakları  
 Yeni hizmet konakları, dinleme yerel barındırma ortamı IIS tarafından desteklenen ağ aktarımı oluşturmak için kesinlik temelli kendini barındırma API'ları kullanmayın (örneğin, [!INCLUDE[iis601](../../../../includes/iis601-md.md)] TCP barındırmak için Hizmetleri, TCP iletişimi üzerinde yerel olarak desteklenmediği için [!INCLUDE[iis601](../../../../includes/iis601-md.md)]). Bu yaklaşım önerilmez. IIS barındırma ortamında imperatively oluşturulan hizmet konakları bilinmiyor. Barındırma uygulama havuzunun boşta olup olmadığını belirlerken imperatively oluşturulan Hizmetleri tarafından yapılan işleme için IIS tarafından alındığından değil, kritik noktasıdır. Bu tür imperatively oluşturulan servis konağınız uygulamaları titizlikle IIS ana bilgisayar işlemleri siler bir IIS barındırma ortamına sahip sonucudur.  
  
## <a name="uris-and-iis-hosted-endpoints"></a>URI ve IIS tarafından barındırılan uç noktaları  
 IIS barındırılan hizmeti için uç noktalar göreli Tekdüzen Kaynak Tanımlayıcıları (URI'ler) değil mutlak adresleri kullanarak yapılandırılması gerekir. Bu uç nokta adresi barındırma uygulamaya ait URI adresleri kümesini yer alması ve ileti tabanlı etkinleştirme beklendiği gibi olur sağlar güvence altına alır.  
  
## <a name="state-management-and-process-recycling"></a>Durum Yönetimi ve işlem geri dönüştürme  
 IIS barındırma ortamı yerel durumu bellekte sürekli olmayan hizmetler için optimize edilmiştir. IIS, kaybolur için özel olarak bellekte depolanan tüm geçici durumuna neden yanıt dış ve iç olayları çeşitli olarak ana bilgisayar işlemi geri dönüştürüldüğünde. IIS'de barındırılan hizmetleri durumlarına dış işlem (örneğin, bir veritabanı) depolamanız gerekir veya bir uygulama olay Geri Dönüşüm, kolaylıkla yeniden oluşturulabilir bir bellek içi önbellekte oluşur.  
  
> [!NOTE]
>  Yaptığınız WCF kullanır ileti katman güvenilirlik ve güvenlik protokolleri geçici bellek içi durumunu kullanır. WCF güvenilir oturumlar ve güvenlik oturumları uygulama dönüştürür nedeniyle beklenmedik şekilde sonlandırabilir. IIS barındırılan uygulamalar ya da uygulama katmanı durumu (örneğin, bir uygulama katmanı yapı veya özel bağıntı üstbilgi) ya da devre dışı bırak ilişkilendirme için WCF tarafından sağlanan oturum anahtarı dışında bir şey bağımlı bu protokollerin kullanın IIS işlemi barındırılan uygulama için geri dönüştürülüyor.  
  
## <a name="optimizing-performance-in-middle-tier-scenarios"></a>Orta katman senaryolarda performansı en iyi duruma getirme  
 En iyi performans için bir *orta katman senaryo*— diğer hizmetlere gelen iletilere yanıt olarak çağıran bir hizmet — WCF hizmeti istemcisi uzak hizmet için bir kez örneği ve birden çok gelen arasında yeniden istek sayısı. WCF hizmeti istemcileri başlatmasını önceden var olan bir istemci örneğinde çağrısı bir hizmeti yapmadan göreli bir pahalı bir işlemdir ve istekler genelinde uzak istemciler önbelleğe alarak farklı performans artışı orta katman senaryoları üreten. WCF hizmeti istemcileri iş parçacığı açısından güvenli olduğundan, bir istemci erişimi birden çok iş parçacıkları arasında eşitlemek gerekli değildir.  
  
 Orta katman senaryoları ayrıca tarafından oluşturulan zaman uyumsuz API'lerini kullanarak performans artışı oluşturabilir `svcutil /a` seçeneği. `/a` Seçeneği neden [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) oluşturmak için `BeginXXX/EndXXX` yöntemleri üzerinde yapılan uzak Hizmetleri için büyük olasılıkla uzun süre çalışan çağrı sağlayan her hizmet işlemi arka plan iş parçacıkları.  
  
## <a name="wcf-in-multi-homed-or-multi-named-scenarios"></a>WCF çok Konaklı veya birden çok adlandırılmış senaryolarda  
 WCF hizmetleri olduğu bir bilgisayar kümesi paylaşmak ortak bir dış adına bir IIS Web grubu içinde dağıtabilirsiniz (gibi http://www.contoso.com) farklı ana bilgisayar adları tarafından ayrı ayrı ele alınan ancak (örneğin, http://www.contoso.com iki farklı makinelerde trafiği yönlendirebilir adlı http://machine1.internal.contoso.com ve http://machine2.internal.contoso.com). Bu dağıtım senaryosu WCF tarafından tamamen desteklenir, ancak hizmetin meta veriler (Web Hizmetleri Açıklama Dili) doğru (harici) ana bilgisayar adını görüntülemek için WCF hizmetlerini barındıran IIS Web sitesinin özel yapılandırma gerektirir.  
  
 Doğru hostname WCF oluşturur hizmeti meta veri görünmesini sağlamak için açık bir ana bilgisayar adı kullanmak için WCF hizmetlerini barındıran IIS Web sitesi için varsayılan kimlik yapılandırın. Örneğin, www.contoso.com grubu içinde bulunan bilgisayarları bir IIS site bağlaması kullanması gereken * HTTP:80:www.contoso.com ve \*: 443:www.contoso.com HTTPS için.  
  
 IIS Web sitesi bağlamalarını IIS Microsoft Yönetim Konsolu (MMC) ek bileşenini kullanarak yapılandırabilirsiniz.  
  
## <a name="application-pools-running-in-different-user-contexts-overwrite-assemblies-from-other-accounts-in-the-temporary-folder"></a>Uygulama havuzları farklı kullanıcı bağlamlarda çalıştıran diğer hesapları geçici klasörde derlemelerden üzerine yaz  
 Farklı kullanıcı bağlamı içinde çalışan uygulama havuzlarının derlemeler geçici diğer hesapları arasından üzerine yazılamıyor emin olmak için [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] dosyaları klasörü, kullanım farklı kimlikleri ve farklı uygulamalar için geçici klasör. Örneğin, iki sanal uygulamaları /Application1 varsa ve / Uygulama2 dizinlerini, iki uygulama havuzları, A ve B, iki farklı kimliklerle oluşturabilirsiniz. Uygulama havuzu bir uygulama havuzu B çalışabilir sırada başka bir kullanıcı kimliği altında (kullanıcı2) altında bir kullanıcı kimliği (kullanıcı1) çalıştırın ve /Application1 Kullanım A ve /Application2 B. kullanmak için yapılandırın  
  
 Web.config dosyasında kullanarak geçici klasörü yapılandırabilirsiniz \< system.web/compilation/@tempFolder>. /Application1, "c:\tempForUser1" olabilir ve Uygulama2 dizinlerini için "c:\tempForUser2" olabilir. Bu klasörleri iki kimlikleri için karşılık gelen yazma izni verin.  
  
 Ardından kullanıcı2 /application2 (c:\tempForUser1 altında) kod oluşturma klasörünü değiştiremezsiniz.  
  
## <a name="enabling-asynchronous-processing"></a>Zaman uyumsuz işleme etkinleştirme  
 Varsayılan olarak IIS 6.0 ve önceki barındırılan bir WCF hizmetine gönderilen iletiler zaman uyumlu bir şekilde işlenir. ASP.NET WCF kendi iş parçacığında (ASP.NET çalışan iş parçacığı) çağırır ve WCF isteğini işlemek için başka bir iş parçacığı kullanır. İşleme tamamlanana kadar WCF ASP.NET çalışan iş parçacığı tutar. Bu istekler zaman uyumlu işleme için yol gösterir. – WCF ASP.NET iş parçacığına istek işlenirken tutmaz bir isteği işlemek için gerekli iş parçacığı sayısını azalttığı isteklerini zaman uyumsuz olarak işleme daha yüksek ölçeklenebilirlik sağlar. Zaman uyumsuz davranışı kullanımını sunucuya açmak gelen istek kısıtlama mümkün olduğundan, IIS 6.0 çalışan makineler için tavsiye edilmez *hizmet reddi* (DOS) saldırıları. IIS 7. 0'dan başlayarak, eş zamanlı istek azaltma sunulmuştur: `[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ASP.NET\2.0.50727.0]"MaxConcurrentRequestsPerCpu`. Bu yeni azaltma ile zaman uyumsuz işleme kullanmak güvenlidir.  IIS 7.0 varsayılan olarak, modül ve zaman uyumsuz işleyici kaydedilir. Bu kapatıldı, zaman uyumsuz işleme, uygulamanızın Web.config dosyasında isteklerinin el ile etkinleştirebilirsiniz. Kullandığınız ayarlar bağlıdır, `aspNetCompatibilityEnabled` ayarı. Varsa `aspNetCompatibilityEnabled` kümesine `false`, yapılandırma `System.ServiceModel.Activation.ServiceHttpModule` aşağıdaki yapılandırma parçacığında gösterildiği gibi.  
  
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
  
 Varsa `aspNetCompatibilityEnabled` kümesine `true`, yapılandırma `System.ServiceModel.Activation.ServiceHttpHandlerFactory` aşağıdaki yapılandırma parçacığında gösterildiği gibi.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Barındırma hizmeti örnekleri](http://msdn.microsoft.com/library/f703a3f6-0fba-418a-a92f-7ce75ccfa47e)  
 [Windows Server App Fabric barındırma özellikleri](http://go.microsoft.com/fwlink/?LinkId=201276)
