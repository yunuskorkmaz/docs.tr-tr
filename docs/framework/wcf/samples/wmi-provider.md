---
title: WMI Sağlayıcısı
ms.date: 03/30/2017
ms.assetid: 462f0db3-f4a4-4a4b-ac26-41fc25c670a4
ms.openlocfilehash: 04fdbb7efcae6fdbb78f467352e6106ac5218799
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183197"
---
# <a name="wmi-provider"></a>WMI Sağlayıcısı
Bu örnek, WCF'de yerleşik olan Windows Yönetim Araçları (WMI) sağlayıcısını kullanarak çalışma zamanında Windows Communication Foundation (WCF) hizmetlerinden nasıl veri toplanacağını göstermektedir. Ayrıca, bu örnek, bir hizmete kullanıcı tanımlı WMI nesnesi nasıl ekleyeceğini gösterir. Örnek, [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md) için WMI sağlayıcısını etkinleştirir ve çalışma `ICalculator` zamanında hizmetten nasıl veri toplanacaklarını gösterir.  
  
 WMI, Microsoft'un Web Tabanlı Kurumsal Yönetim (WBEM) standardını uygulamasıdır. WMI SDK hakkında daha fazla bilgi için [Windows Management Instrumentation'a](/windows/desktop/WmiSdk/wmi-start-page)bakın. WBEM, uygulamaların yönetim araçlarını dış yönetim araçlarına nasıl maruz bıraktamaları için bir endüstri standardıdır.  
  
 WCF, WBEM uyumlu bir arayüz aracılığıyla çalışma zamanında enstrümantasyonu ortaya çıkaran bir bileşen olan bir WMI sağlayıcısı uygular. Yönetim araçları, çalışma zamanında arabirim üzerinden hizmetlere bağlanabilir. WCF, adresler, bağlamalar, davranışlar ve dinleyiciler gibi hizmetlerin özniteliklerini ortaya çıkarır.  
  
 Yerleşik WMI sağlayıcısı uygulamanın yapılandırma dosyasında etkinleştirilir. Bu, aşağıdaki `wmiProviderEnabled` örnek yapılandırmada gösterildiği gibi, [ \<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) bölümündeki [ \<>tanılama](../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md) özelliği ile yapılır:  
  
```xml  
<system.serviceModel>  
    ...  
    <diagnostics wmiProviderEnabled="true" />  
    ...  
</system.serviceModel>  
```  
  
 Bu yapılandırma girişi bir WMI arabirimini ortaya çıkarır. Yönetim uygulamaları artık bu arayüz üzerinden bağlanabilir ve uygulamanın yönetim enstrümantasyonuna erişebilir.  
  
## <a name="custom-wmi-object"></a>Özel WMI Nesnesi  
 Bir hizmete WMI nesneleri eklemek, yerleşik WMI sağlayıcı bilgileriyle birlikte kullanıcı tanımlı bilgileri ortaya çıkarmasını mümkün kılar. Bu, Installutil.exe uygulamasını kullanarak hizmetin şemasını WMI'ye yayımlayarak gerçekleştirilir. Bunu gerçekleştirmek için talimatlar, daha fazla ayrıntı ile birlikte konunun sonunda kurulum talimatları bulunabilir.  
  
## <a name="accessing-wmi-information"></a>WMI Bilgilerine Erişim  

WMI verilerine birçok farklı şekilde erişilebilir. Microsoft komut dosyaları, Visual Basic uygulamaları, C++ uygulamaları ve .NET Framework için WMI API'leri sağlar. Daha fazla bilgi için [WMI kullanma'ya](/windows/desktop/wmisdk/using-wmi)bakın.
  
 Bu örnekte iki Java komut dosyası kullanılır: biri bilgisayarda çalışan hizmetleri bazı özellikleriyle birlikte, ikincisi de kullanıcı tarafından tanımlanan WMI verilerini görüntülemek için sıralamak için kullanılır. Komut dosyası WMI sağlayıcısına bir bağlantı açar, verileri parses ve toplanan verileri görüntüler.  
  
 Bir WCF hizmetinin çalışan bir örneğini oluşturmak için örneği başlatın. Hizmet çalışırken, komut isteminde aşağıdaki komutu kullanarak her Java komut dosyasını çalıştırın:  
  
```console  
cscript EnumerateServices.js  
```  
  
 Komut dosyası, hizmette bulunan enstrümantasyona erişir ve aşağıdaki çıktıyı üretir:  
  
```console  
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
  
 Ardından, kullanıcı tanımlı WMI verilerini görüntülemek için ikinci Java Komut Dosyasını çalıştırın:  
  
```console  
cscript EnumerateCustomObjects.js  
```  
  
 Komut dosyası, hizmetlerde bulunan kullanıcı tanımlı enstrümantasyona erişir ve aşağıdaki çıktıyı üretir:  
  
```console
1 WMIObject(s) found.  
|-PID:           30285bfd-9d66-4c4e-9be2-310499c5cef5  
|-InstanceId:    3839  
|-WMIInfo:       User Defined WMI Information.  
```  
  
 Çıktı, bilgisayarda çalışan tek bir hizmet olduğunu gösterir. Hizmet, sözleşmeyi `ICalculator` uygulayan bir bitiş noktasını ortaya çıkarır. Bitiş noktası tarafından uygulanan davranış ve bağlama ayarları, ileti yığınının tek tek öğelerinin toplamı olarak listelenir.  
  
 WMI, WCF altyapısının yönetim enstrümantasyonunu ortaya çıkarmakla sınırlı değildir. Uygulama, aynı mekanizma aracılığıyla kendi etki alanına özgü veri öğelerini ortaya çıkarabilir. WMI, bir Web hizmetinin denetimi ve denetimi için birleşik bir mekanizmadır.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, oluşturmak ve çalıştırmak için  
  
1. [Windows Communication Foundation Samples için Tek Seferlik Kurulum Yordamı'nı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizi sağlayın.  
  
2. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak [için, Windows Communication Foundation Samples'i oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.  
  
3. InstallUtil.exe için varsayılan konumlar barındırma dizinindeki service.dll dosyasında InstallUtil.exe 'yi çalıştırarak hizmetleri schema'yı WMI'ye yayımlayın (InstallUtil.exe için varsayılan konumlar "%WINDIR%\Microsoft.NET\Framework\v4.0.30319"dur). Bu adımın yalnızca service.dll dosyasında değişiklikler yapıldığında yürütülmesi gerekir.
  
4. Örneği tek veya bilgisayar lar arası yapılandırmada çalıştırmak [için, Windows Communication Foundation Samples'ı çalıştıran](../../../../docs/framework/wcf/samples/running-the-samples.md)yönergeleri izleyin.  
  
    > [!NOTE]
    > wcf'yi ASP.NET yükledikten sonra yüklediyseniz,%WINDIR%\ Microsoft.Net\Framework\v3.0\Windows Communication Foundation\servicemodelreg.exe " -r -x ASPNET hesabına WMI nesnelerini yayımlama izni vermek için.  
  
5. WMI aracılığıyla yüzeye çıkan örnekteki verileri komutları kullanarak görüntüleyin: `cscript EnumerateServices.js` veya `cscript EnumerateCustomObjects.js`.  
  
> [!IMPORTANT]
> Örnekler bilgisayarınıza zaten yüklenmiş olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek aşağıdaki dizinde yer almaktadır.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\WMIProvider`  
  
## <a name="see-also"></a>Ayrıca bkz.

- [AppFabric İzleme Örnekleri](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))
