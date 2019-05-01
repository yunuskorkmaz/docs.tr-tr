---
title: Internet Information Services Barındırma En İyi Uygulamaları
ms.date: 03/30/2017
ms.assetid: 0834768e-9665-46bf-86eb-d4b09ab91af5
ms.openlocfilehash: a4312a9affc1103f613f3f8ffd9a14696f9d4bcc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61972620"
---
# <a name="internet-information-services-hosting-best-practices"></a>Internet Information Services Barındırma En İyi Uygulamaları
Bu konuda, Windows Communication Foundation (WCF) hizmetlerini barındırmak için bazı en iyi uygulamalar açıklanmaktadır.  
  
## <a name="implementing-wcf-services-as-dlls"></a>Dll olarak uygulama WCF hizmetleri  
 Uygulama bir WCF hizmeti bir Web uygulamasının \bin dizinine dağıtılan bir DLL olarak dağıtılan Internet Information Services (IIS) sahip olmayan bir test ortamında Web uygulama modeli dışında hizmet Örneğin, yeniden sağlar.  
  
## <a name="service-hosts-in-iis-hosted-applications"></a>IIS barındırılan uygulamalarda hizmet konakları  
 Kesinlik temelli barındırılan API'ler, ağ aktarımı barındırma ortamı IIS tarafından yerel olarak desteklenen, dinleme yeni hizmet konakları oluşturmak için kullanmayın (örneğin, [!INCLUDE[iis601](../../../../includes/iis601-md.md)] TCP barındırmak için Hizmetleri, çünkü TCP iletişimi üzerinde yerel olarak desteklenmiyor [!INCLUDE[iis601](../../../../includes/iis601-md.md)]). Bu yaklaşım önerilmez. IIS barındırma ortamında kesin oluşturulan hizmet konakları bilinmiyor. Barındırma uygulama havuzu boşta olup olmadığını belirlerken kesin oluşturulan Hizmetleri tarafından gerçekleştirilen işleme için IIS tarafından tasarlanan değil kritik noktasıdır. Sonuç tür kesin oluşturulan hizmet konakları sahip uygulamalar IIS ana bilgisayarı işlemlerinin agresif siler bir IIS barındırma ortamı olmasıdır.  
  
## <a name="uris-and-iis-hosted-endpoints"></a>URI ve IIS tarafından barındırılan uç noktaları  
 IIS barındırılan hizmeti için uç noktalar göreli Tekdüzen Kaynak Tanımlayıcıları (URI'lar) değil mutlak adresleri kullanarak yapılandırılması gerekir. Bu uç nokta adresini barındırma uygulamaya ait URI adresleri kümesi içinde döner ve ileti tabanlı etkinleştirme beklendiği gibi olur sağlar güvence altına alır.  
  
## <a name="state-management-and-process-recycling"></a>Durum Yönetimi ve işlem geri dönüştürme  
 IIS barındırma ortamı, bellekteki yerel durum bilgisi bulundurmaz Hizmetleri için optimize edilmiştir. IIS, çeşitli dış ve iç olaylara yanıt olarak ana bilgisayar işlemi kaybolacak özel bellekte herhangi bir geçici durum neden geri dönüştürür. IIS'de barındırılan hizmetler, dış işlem (örneğin, bir veritabanı) bunların durumunu depolamanız gerekir veya bir bellek içi önbelleği bir uygulamanın olay Geri Dönüşüm, kolayca yeniden oluşturulabilir gerçekleşir.  
  
> [!NOTE]
>  İleti düzeyi güvenilirliği ve güvenliği için WCF kullanan olun protokolleri geçici bellek içi durumunu kullanın. WCF güvenilir oturumlar ve güvenlik oturumu beklenmedik bir şekilde uygulama geri dönüşümlerine genel nedeniyle sonlandırabilir. IIS barındırılan uygulamalar ya da uygulama katmanı durumu (örneğin, bir uygulama katmanı yapısı veya özel korelasyon başlığı) veya devre dışı bırakma ilişkilendirmek için WCF tarafından sağlanan oturum anahtarı dışında bir şey bağlı olmamalıdır bu protokolleri kullanın. IIS işlemi barındırılan uygulamayı geri dönüştürülüyor.  
  
## <a name="optimizing-performance-in-middle-tier-scenarios"></a>Orta katman senaryolarda performansı en iyi duruma getirme  
 En iyi performans için bir *orta katman senaryo*— diğer hizmetlere gelen iletilere yanıt olarak çağıran bir hizmet — WCF hizmeti istemcisi uzak hizmet için bir kez örneklemek ve birden çok gelen arasında yeniden istek sayısı. WCF hizmeti istemcileri örnekleme hizmeti önceden var olan bir istemci örneği üzerinde çağrısı yaparak göre pahalı bir işlemdir ve istekler genelinde uzak istemciler önbelleğe alarak farklı bir performans kazancı elde edildi orta katman senaryoları üretir. WCF hizmeti istemcileri iş parçacığı açısından güvenli olduğundan, birden çok iş parçacığı arasında bir istemci erişimi eşitlemek gerekli değildir.  
  
 Orta katman senaryoları da tarafından oluşturulan zaman uyumsuz API'leri kullanarak performans kazancı elde edildi üretmek `svcutil /a` seçeneği. `/a` Seçeneğini neden [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) oluşturulacak `BeginXXX/EndXXX` üzerinde yapılacak muhtemelen uzun süren çağrısına uzak hizmetleri sağlayan her bir hizmet işlemi için yöntemleri arka plan iş parçacıkları.  
  
## <a name="wcf-in-multi-homed-or-multi-named-scenarios"></a>Birden çok girişli veya çok adlandırılmış senaryolarda WCF  
 WCF hizmetleri bilgisayarlar kümesi, ortak bir dış ad paylaşacağı bir IIS Web grubu içinde dağıttığınız (gibi `http://www.contoso.com`) farklı ana bilgisayar adları tarafından ayrı ayrı ele alınır ancak (örneğin, `http://www.contoso.com` iki farklı makinelere trafiği yönlendirebilir adlı `http://machine1.internal.contoso.com` ve `http://machine2.internal.contoso.com`). Bu dağıtım senaryosu WCF tarafından tam olarak desteklenir, ancak özel yapılandırma (Web Hizmetleri Açıklama Dili) hizmetin meta verilerde doğru (Dış) ana bilgisayar adını görüntülemek için WCF hizmetlerini barındıran IIS Web sitesinin gerektirir.  
  
 Doğru ana bilgisayar adını oluşturan WCF hizmet meta verileri görünmesini sağlamak için açık bir ana bilgisayar adı kullanmak için WCF hizmetlerini barındıran IIS Web sitesi için varsayılan kimlik yapılandırın. Örneğin, içinde bulunan bilgisayarları `www.contoso.com` grubu, bir IIS sitesi bağlamasının kullanmalıdır *:80:www.contoso.com http ve \*: 443:www.contoso.com HTTPS için.  
  
 IIS Web sitesi bağlamalarının IIS Microsoft Yönetim Konsolu (MMC) ek bileşenini kullanarak yapılandırabilirsiniz.  
  
## <a name="application-pools-running-in-different-user-contexts-overwrite-assemblies-from-other-accounts-in-the-temporary-folder"></a>Derlemeleri geçici klasörde diğer hesaplardan farklı kullanıcı bağlamı içinde çalışan uygulama havuzları üzerine  
 Uygulama havuzları farklı kullanıcı bağlamı içinde çalışan diğer hesapların geçici derlemelerden üzerine yazılamaz emin olmak için [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] dosyaları klasörü, farklı kimlikler kullanın ve farklı uygulamalara yönelik geçici klasör. Örneğin, iki sanal uygulamaları /Application1 varsa ve / Uygulama2 dizinlerini, iki uygulama havuzları, A ve B ile iki farklı kimlikler oluşturabilirsiniz. Uygulama havuzu bir uygulama havuzu B çalıştırabilirsiniz (kullanıcı2) başka bir kullanıcı kimliği altında bir kullanıcı kimliği (kullanıcı1) çalışmasına ve /Application1 kullanmayın ve /Application2 b kullanmak için yapılandırma  
  
 Web.config dosyasında kullanarak geçici klasörü yapılandırabilirsiniz \< system.web/compilation/@tempFolder>. /Application1, "c:\tempForUser1" olabilir ve Uygulama2 dizinlerini için "c:\tempForUser2" olabilir. Bu klasörleri iki kimlikleri için karşılık gelen yazma izni verin.  
  
 Ardından kullanıcı2 /application2 (c:\tempForUser1 altında) kod üretimi klasörünü değiştiremezsiniz.  
  
## <a name="enabling-asynchronous-processing"></a>Zaman uyumsuz işleme etkinleştirme  
 Varsayılan olarak IIS 6.0 ve önceki barındırılan bir WCF hizmetine gönderilen iletiler, zaman uyumlu bir şekilde işlenir. ASP.NET WCF kendi iş parçacığında (ASP.NET çalışan iş parçacığı) çağırır ve WCF isteği işlemek için başka bir iş parçacığı kullanır. İşleme tamamlanana kadar WCF ASP.NET çalışan iş parçacığı tutar. Bu istek için zaman uyumlu işleme neden olur. – WCF ASP.NET iş parçacığı için istek işlenirken bulundurmayan bir isteği işlemek için gerekli iş parçacığı sayısını azaltır çünkü isteklerini zaman uyumsuz olarak işlenmesi daha büyük ölçeklendirme sağlar. IIS 6.0 sunucusunu açın gelen istekleri azaltma hiçbir yolu olmadığından çalışan makineler için zaman uyumsuz davranış kullanımı önerilmez *hizmet reddi* (DOS) saldırıları. IIS 7. 0'ile başlayarak, eş zamanlı istek azaltma sunulmuştur: `[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ASP.NET\2.0.50727.0]"MaxConcurrentRequestsPerCpu`. Bu yeni kısıtlama ile zaman uyumsuz işleme kullanmak güvenlidir.  IIS 7.0 varsayılan olarak, zaman uyumsuz işleyicisi ve modül kaydedilir. Bu devre dışı bırakıldıysa, uygulamanızın Web.config dosyasında isteklerin zaman uyumsuz işleme el ile etkinleştirebilirsiniz. Kullandığınız ayarlar bağlıdır, `aspNetCompatibilityEnabled` ayarı. Varsa `aspNetCompatibilityEnabled` kümesine `false`, yapılandırma `System.ServiceModel.Activation.ServiceHttpModule` aşağıdaki yapılandırma kod parçacığında gösterildiği gibi.  
  
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
  
 Varsa `aspNetCompatibilityEnabled` kümesine `true`, yapılandırma `System.ServiceModel.Activation.ServiceHttpHandlerFactory` aşağıdaki yapılandırma kod parçacığında gösterildiği gibi.  
  
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

- [Barındırma hizmeti örnekleri](../samples/hosting.md)
- [Windows Server App Fabric barındırma özellikleri](https://go.microsoft.com/fwlink/?LinkId=201276)
