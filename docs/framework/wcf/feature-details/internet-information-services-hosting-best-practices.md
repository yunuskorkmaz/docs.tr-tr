---
title: "Internet Information Services Barındırma En İyi Uygulamaları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0834768e-9665-46bf-86eb-d4b09ab91af5
caps.latest.revision: "22"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 60d703336aeac3471e4b554f65998621b5cc8ef8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="internet-information-services-hosting-best-practices"></a>Internet Information Services Barındırma En İyi Uygulamaları
Barındırma için bazı en iyi uygulamalar bu konuda özetlenir [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Hizmetleri.  
  
## <a name="implementing-wcf-services-as-dlls"></a>WCF hizmetleri DLL'ler olarak uygulama  
 Uygulama bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmeti bir Web uygulaması \bin dizinine dağıtılmış bir DLL yeniden Web uygulama modeli dışında hizmet Örneğin, Internet Information Services (IIS) olmayabilir bir test ortamında verdiğinden Dağıtılmış.  
  
## <a name="service-hosts-in-iis-hosted-applications"></a>IIS barındırılan uygulamalarında hizmet konakları  
 Yeni hizmet konakları, dinleme yerel barındırma ortamı IIS tarafından desteklenen ağ aktarımı oluşturmak için kesinlik temelli kendini barındırma API'ları kullanmayın (örneğin, [!INCLUDE[iis601](../../../../includes/iis601-md.md)] TCP barındırmak için Hizmetleri, TCP iletişimi üzerinde yerel olarak desteklenmediği için [!INCLUDE[iis601](../../../../includes/iis601-md.md)]). Bu yaklaşım önerilmez. IIS barındırma ortamında imperatively oluşturulan hizmet konakları bilinmiyor. Barındırma uygulama havuzunun boşta olup olmadığını belirlerken imperatively oluşturulan Hizmetleri tarafından yapılan işleme için IIS tarafından alındığından değil, kritik noktasıdır. Bu tür imperatively oluşturulan servis konağınız uygulamaları titizlikle IIS ana bilgisayar işlemleri siler bir IIS barındırma ortamına sahip sonucudur.  
  
## <a name="uris-and-iis-hosted-endpoints"></a>URI ve IIS tarafından barındırılan uç noktaları  
 IIS barındırılan hizmeti için uç noktalar göreli Tekdüzen Kaynak Tanımlayıcıları (URI'ler) değil mutlak adresleri kullanarak yapılandırılması gerekir. Bu uç nokta adresi barındırma uygulamaya ait URI adresleri kümesini yer alması ve ileti tabanlı etkinleştirme beklendiği gibi olur sağlar güvence altına alır.  
  
## <a name="state-management-and-process-recycling"></a>Durum Yönetimi ve işlem geri dönüştürme  
 IIS barındırma ortamı yerel durumu bellekte sürekli olmayan hizmetler için optimize edilmiştir. IIS, kaybolur için özel olarak bellekte depolanan tüm geçici durumuna neden yanıt dış ve iç olayları çeşitli olarak ana bilgisayar işlemi geri dönüştürüldüğünde. IIS'de barındırılan hizmetleri durumlarına dış işlem (örneğin, bir veritabanı) depolamanız gerekir veya bir uygulama olay Geri Dönüşüm, kolaylıkla yeniden oluşturulabilir bir bellek içi önbellekte oluşur.  
  
> [!NOTE]
>  Protokolleri [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] yaptığınız kullanır ileti katman güvenilirlik ve güvenlik için geçici bellek içi durumu kullanın. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]güvenilir oturumlar ve güvenlik oturumları uygulama dönüştürür nedeniyle beklenmedik şekilde sonlandırabilir. IIS barındırılan uygulamalar ya da bağlı şeye dışında bu protokollerin kullanmak [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]-uygulama katmanı durumu (örneğin, bir uygulama katmanı yapı veya özel bağıntı üstbilgi) ilişkilendirme için oturum anahtarı girildi veya IIS işlem geri dönüştürme barındırılan uygulama için devre dışı.  
  
## <a name="optimizing-performance-in-middle-tier-scenarios"></a>Orta katman senaryolarda performansı en iyi duruma getirme  
 En iyi performans için bir *orta katman senaryo*— diğer hizmetlere gelen iletilere yanıt olarak çağıran bir hizmet — örneği [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmet istemci uzak hizmet için bir kez ve birden çok yeniden gelen istek sayısı. Örnek oluşturma [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmeti istemcileri önceden var olan bir istemci örneğinde çağrısı bir hizmeti yapmadan göre pahalı bir işlem olduğundan ve orta katman senaryoları üretmek farklı performans artışı istekler genelinde uzak istemciler'önbelleğe alma. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]istemcilere hizmet iş parçacığı açısından güvenli olduğundan, bir istemci erişimi birden çok iş parçacıkları arasında eşitlemek gerekli değildir.  
  
 Orta katman senaryoları ayrıca tarafından oluşturulan zaman uyumsuz API'lerini kullanarak performans artışı oluşturabilir `svcutil /a` seçeneği. `/a` Seçeneği neden [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) oluşturmak için `BeginXXX/EndXXX` yöntemleri üzerinde yapılan uzak Hizmetleri için büyük olasılıkla uzun süre çalışan çağrı sağlayan her hizmet işlemi arka plan iş parçacıkları.  
  
## <a name="wcf-in-multi-homed-or-multi-named-scenarios"></a>WCF çok Konaklı veya birden çok adlandırılmış senaryolarda  
 Dağıtabileceğiniz [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Hizmetleri olduğu bir bilgisayar kümesi paylaşmak ortak bir dış bir IIS Web grubu içinde adı (http://www.contoso.com gibi), ancak farklı ana bilgisayar adları tarafından ayrı ayrı ele (örneğin, http://www.contoso.com doğrudan http://machine1.internal.contoso.com ve http://machine2.internal.contoso.com adlı iki farklı makinelerde trafiği). Bu dağıtım senaryosunun tam tarafından desteklenen [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], ancak IIS Web sitesi barındırma özel yapılandırma gerektirir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] doğru (harici) ana bilgisayar adı hizmetin meta veriler (Web Hizmetleri Açıklama Dili) görüntülemek için hizmetleri.  
  
 Doğru ana bilgisayar hizmeti meta verilerde görünmesini sağlamak için [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] oluşturur, barındıran IIS Web sitesi için varsayılan kimlik yapılandırma [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Hizmetleri açık bir ana bilgisayar adı kullanın. Örneğin, www.contoso.com grubu içinde bulunan bilgisayarları bir IIS site bağlaması kullanması gereken * HTTP:80:www.contoso.com ve \*: 443:www.contoso.com HTTPS için.  
  
 IIS Web sitesi bağlamalarını IIS Microsoft Yönetim Konsolu (MMC) ek bileşenini kullanarak yapılandırabilirsiniz.  
  
## <a name="application-pools-running-in-different-user-contexts-overwrite-assemblies-from-other-accounts-in-the-temporary-folder"></a>Uygulama havuzları farklı kullanıcı bağlamlarda çalıştıran diğer hesapları geçici klasörde derlemelerden üzerine yaz  
 Farklı kullanıcı bağlamı içinde çalışan uygulama havuzlarının derlemeler geçici diğer hesapları arasından üzerine yazılamıyor emin olmak için [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] dosyaları klasörü, kullanım farklı kimlikleri ve farklı uygulamalar için geçici klasör. Örneğin, iki sanal uygulamaları /Application1 varsa ve / Uygulama2 dizinlerini, iki uygulama havuzları, A ve B, iki farklı kimliklerle oluşturabilirsiniz. Uygulama havuzu bir uygulama havuzu B çalışabilir sırada başka bir kullanıcı kimliği altında (kullanıcı2) altında bir kullanıcı kimliği (kullanıcı1) çalıştırın ve /Application1 Kullanım A ve /Application2 B. kullanmak için yapılandırın  
  
 Web.config dosyasında kullanarak geçici klasörü yapılandırabilirsiniz \< system.web/compilation/@tempFolder>. /Application1, "c:\tempForUser1" olabilir ve Uygulama2 dizinlerini için "c:\tempForUser2" olabilir. Bu klasörleri iki kimlikleri için karşılık gelen yazma izni verin.  
  
 Ardından kullanıcı2 /application2 (c:\tempForUser1 altında) kod oluşturma klasörünü değiştiremezsiniz.  
  
## <a name="enabling-asynchronous-processing"></a>Zaman uyumsuz işleme etkinleştirme  
 Gönderilen varsayılan ileti bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmeti IIS 6.0 altında barındırılan ve daha önceki bir zaman uyumlu şekilde işlenir. ASP.NET çağırır içine [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kendi iş parçacığında (ASP.NET çalışan iş parçacığı) ve [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] isteğini işlemek için başka bir iş parçacığı kullanır. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]işleme tamamlanana kadar ASP.NET çalışan iş parçacığı tutar. Bu istekler zaman uyumlu işleme için yol gösterir. İsteklerini zaman uyumsuz olarak işleme sağlayan daha yüksek ölçeklenebilirlik – bir isteği işlemek için gerekli iş parçacığı sayısını azalttığı[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ASP.NET iş parçacığına istek işlenirken tutmaz. Zaman uyumsuz davranışı kullanımını sunucuya açmak gelen istek kısıtlama mümkün olduğundan, IIS 6.0 çalışan makineler için tavsiye edilmez *hizmet reddi* (DOS) saldırıları. IIS 7. 0'dan başlayarak, eş zamanlı istek azaltma sunulmuştur: `[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ASP.NET\2.0.50727.0]"MaxConcurrentRequestsPerCpu`. Bu yeni azaltma ile zaman uyumsuz işleme kullanmak güvenlidir.  IIS 7.0 varsayılan olarak, modül ve zaman uyumsuz işleyici kaydedilir. Bu kapatıldı, zaman uyumsuz işleme, uygulamanızın Web.config dosyasında isteklerinin el ile etkinleştirebilirsiniz. Kullandığınız ayarlar bağlıdır, `aspNetCompatibilityEnabled` ayarı. Varsa `aspNetCompatibilityEnabled` kümesine `false`, yapılandırma `System.ServiceModel.Activation.ServiceHttpModule` aşağıdaki yapılandırma parçacığında gösterildiği gibi.  
  
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
 [Barındırma hizmeti örnekleri](http://msdn.microsoft.com/en-us/f703a3f6-0fba-418a-a92f-7ce75ccfa47e)  
 [Windows Server App Fabric barındırma özellikleri](http://go.microsoft.com/fwlink/?LinkId=201276)
