---
title: WMI Sağlayıcısı
ms.date: 03/30/2017
ms.assetid: 462f0db3-f4a4-4a4b-ac26-41fc25c670a4
ms.openlocfilehash: 89e2d370919519953e714cb0d0020587b3f53c9d
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70038511"
---
# <a name="wmi-provider"></a>WMI Sağlayıcısı
Bu örnek, WCF 'de yerleşik olarak bulunan Windows Yönetim Araçları (WMI) sağlayıcısını kullanarak çalışma zamanında Windows Communication Foundation (WCF) hizmetlerinden nasıl veri toplanacağını göstermektedir. Ayrıca, bu örnek, bir hizmete Kullanıcı tanımlı WMI nesnesinin nasıl ekleneceğini gösterir. Örnek, [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md) için WMI sağlayıcısını etkinleştirir ve çalışma zamanında `ICalculator` hizmetten nasıl veri toplanacağını gösterir.  
  
 WMI, Microsoft 'un web tabanlı kuruluş yönetimi (WBEM) standardı uygulamasıdır. WMI SDK hakkında daha fazla bilgi için bkz. [Windows Yönetim Araçları](/windows/desktop/WmiSdk/wmi-start-page). WBEM, uygulamaların yönetim araçları 'nı dış yönetim araçlarına nasıl sergilekullandığını gösteren bir sektör standardıdır.  
  
 WCF, bir WBEM uyumlu arabirim aracılığıyla çalışma zamanında izleme sunan bir bileşen olan WMI sağlayıcısını uygular. Yönetim Araçları, çalışma zamanında arabirim aracılığıyla hizmetlere bağlanabilir. WCF, adresler, bağlamalar, davranışlar ve dinleyicileri gibi hizmetlerin özniteliklerini gösterir.  
  
 Yerleşik WMI sağlayıcısı, uygulamanın yapılandırma dosyasında etkinleştirilir. Bu, aşağıdaki örnek yapılandırmada `wmiProviderEnabled` gösterildiği gibi [ \<System. ServiceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) bölümündeki [ \<Tanılama >](../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md) özniteliği aracılığıyla yapılır:  
  
```xml  
<system.serviceModel>  
    ...  
    <diagnostics wmiProviderEnabled="true" />  
    ...  
</system.serviceModel>  
```  
  
 Bu yapılandırma girişi bir WMI arabirimi sunar. Yönetim uygulamaları artık bu arabirimden bağlanabilir ve uygulamanın yönetim araçlarına erişebilir.  
  
## <a name="custom-wmi-object"></a>Özel WMI nesnesi  
 WMI nesnelerini bir hizmete eklemek, yerleşik WMI sağlayıcısı bilgileriyle birlikte Kullanıcı tanımlı bilgilerin açığa çıkarmasına olanak tanır. Bu, InstallUtil. exe uygulaması kullanılarak hizmetin şeması WMI 'ye yayınlanarak yapılır. Bunu gerçekleştirmeye yönelik yönergeler, konunun sonundaki Kurulum yönergelerindeki daha ayrıntılı bilgi bulabilirsiniz.  
  
## <a name="accessing-wmi-information"></a>WMI bilgilerine erişme  
 WMI verilerine birçok farklı şekilde erişilebilir. Microsoft, betikler, Visual Basic uygulamalar, C++ uygulamalar ve .NET Framework Için WMI API 'leri sağlar (https://docs.microsoft.com/windows/desktop/wmisdk/using-wmi).  
  
 Bu örnek iki Java komut dosyası kullanır: biri bilgisayarda çalışan hizmetleri, bazı özellikleriyle birlikte, Kullanıcı tanımlı WMI verilerini görüntülemek için ikincisini görüntüler. Betik, WMI sağlayıcısına bir bağlantı açar, verileri ayrıştırır ve toplanan verileri görüntüler.  
  
 WCF hizmetinin çalışan bir örneğini oluşturmak için örneği başlatın. Hizmet çalışırken, komut isteminde aşağıdaki komutu kullanarak her bir Java betiğini çalıştırın:  
  
```  
cscript EnumerateServices.js  
```  
  
 Betik, hizmette bulunan izleme erişimine erişir ve aşağıdaki çıktıyı üretir:  
  
```  
Microsoft (R) Windows Script Host Version 5.6  
Copyright © Microsoft Corporation 1996-2001. All rights reserved.  
  
1 service(s) found.  
|-PID:           5776  
|-DistinguishedName:  CalculatorService@http://localhost/ServiceModelSamples/service.svc  
|-Endpoints:     1 endpoints  
  |-CalculatorService.ICalculator@http://localhost/ServiceModelSamples/service.svc  
    |-Address:                        http://localhost/ServiceModelSamples/service.svc  
    |-CounterInstanceName:  
    |-AddressHeaders:                 0  
    |-ContractType:                   Contract.Name='ICalculator'  
    |-BindingElements:                4 bindings  
      |-BindingElements[0]  
        |-Type:                       TransactionFlowBindingElement  
      |-BindingElements[1]  
        |-Type:                       SymmetricSecurityBindingElement  
      |-BindingElements[2]  
        |-Type:                       TextMessageEncodingBindingElement  
        |-MaxReadPoolSize:            64  
        |-MaxWritePoolSize:           16  
      |-BindingElements[3]  
        |-Type:                       HttpTransportBindingElement  
        |-ManualAddressing:           false  
        |-MaxBufferSize:              65536  
        |-AllowCookies:               false  
        |-AuthenticationScheme:       Anonymous  
        |-BypassProxyOnLocal:         false  
        |-HostNameComparisonMode:     StrongWildcard  
        |-ProxyAddress:               null  
        |-ProxyAuthenticationScheme:  Anonymous  
        |-Realm:  
        |-TransferMode:               Buffered  
        |-UseDefaultWebProxy:         true  
|-Behaviors:     5 behaviors  
      |-Behavior[0]  
      |-Type:                       ServiceBehaviorAttribute  
        |-AddressFilterMode:               Exact  
        |-AutomaticSessionShutdown:        true  
        |-ConcurrencyMode:                 Single  
        |-IncludeExceptionDetailInFaults:  false  
        |-InstanceContextMode:             PerSession  
        |-TransactionIsolationLevel:       Unspecified  
        |-TransactionTimeout:              null  
        |-ValidateMustUnderstand:          true  
      |-Behavior[1]  
      |-Type:                       AspNetCompatibilityRequirementsAttribute  
      |-Behavior[2]  
      |-Type:                       ServiceDebugBehavior  
      |-Behavior[3]  
      |-Type:                       ServiceAuthorizationBehavior  
      |-Behavior[4]  
      |-Type:                       Behavior  
```  
  
 Sonra, Kullanıcı tanımlı WMI verilerini göstermek için ikinci Java betiğini çalıştırın:  
  
```  
cscript EnumerateCustomObjects.js  
```  
  
 Betik, hizmetlerde bulunan Kullanıcı tanımlı izleme erişimine erişir ve aşağıdaki çıktıyı üretir:  
  
```  
1 WMIObject(s) found.  
|-PID:           30285bfd-9d66-4c4e-9be2-310499c5cef5  
|-InstanceId:    3839  
|-WMIInfo:       User Defined WMI Information.  
```  
  
 Çıktı, bilgisayarda çalışan tek bir hizmet olduğunu gösterir. Hizmet, `ICalculator` sözleşmeyi uygulayan bir uç noktayı kullanıma sunar. Uç nokta tarafından uygulanan davranışın ve bağlamanın ayarları, mesajlaşma yığınındaki bireysel öğelerin toplamı olarak listelenir.  
  
 WMI, WCF altyapısının yönetim araçlarını açığa çıkarmak için sınırlı değildir. Uygulama, kendi etki alanına özgü veri öğelerini aynı mekanizmaya göre kullanıma sunabilir. WMI, bir Web hizmeti denetimi ve denetimi için Birleşik bir mekanizmadır.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için  
  
1. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.  
  
2. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak Için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)konusundaki yönergeleri izleyin.  
  
3. InstallUtil. exe ' yi çalıştırarak (InstallUtil. exe için varsayılan konumlar "%WINDIR%\Microsoft.NET\Framework\v4.0.30319"), barındırma dizinindeki Service. dll dosyasında, hizmet şemasını WMI 'ya yayımlayın. Bu adımın yalnızca Service. dll dosyasında değişiklik yapıldığında yürütülmesi gerekir.
  
4. Örneği tek veya bir çoklu bilgisayar yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md)bölümündeki yönergeleri izleyin.  
  
    > [!NOTE]
    > ASP.NET yükledikten sonra WCF 'yi yüklediyseniz, "% WINDIR% \ öğesini çalıştırmanız gerekebilir Microsoft. Net\Framework\v3.0\Windows Communication Foundation\servicemodelreg.exe "-r-x" ASPNET hesabına WMI nesneleri yayımlama izni vermek için.  
  
5. Komutları kullanarak WMI üzerinden ortaya çıkacak örnekteki verileri görüntüleyin: `cscript EnumerateServices.js` veya. `cscript EnumerateCustomObjects.js`  
  
> [!IMPORTANT]
> Örnekler bilgisayarınızda zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ' e gidin. Bu örnek, aşağıdaki dizinde bulunur.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\WMIProvider`  
  
## <a name="see-also"></a>Ayrıca bkz.

- [AppFabric Izleme örnekleri](https://go.microsoft.com/fwlink/?LinkId=193959)
