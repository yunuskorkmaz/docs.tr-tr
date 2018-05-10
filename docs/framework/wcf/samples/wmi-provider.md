---
title: WMI Sağlayıcısı
ms.date: 03/30/2017
ms.assetid: 462f0db3-f4a4-4a4b-ac26-41fc25c670a4
ms.openlocfilehash: d135466c402fa21b6a1b11f208ca900f58748bdb
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2018
---
# <a name="wmi-provider"></a>WMI Sağlayıcısı
Bu örnek, WCF yerleşik Windows Yönetim Araçları (WMI) sağlayıcısını kullanarak çalışma zamanında Windows Communication Foundation (WCF) Hizmetleri'nden veri toplamak üzere gösterilmiştir. Ayrıca, bu örnek bir kullanıcı tanımlı WMI nesnesi için bir hizmet eklemek gösterilmiştir. Örnek için WMI sağlayıcısını etkinleştirir [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md) ve veri toplamaya gösterilmiştir `ICalculator` çalışma zamanında hizmet.  
  
 WMI, Web tabanlı Kuruluş Yönetimi'nin (WBEM) standart Microsoft uygulamasıdır. WMI SDK'sı hakkında daha fazla bilgi için bkz: [Windows Yönetim Araçları](https://msdn.microsoft.com/library/aa394582.aspx). WBEM nasıl uygulamaları dış Yönetim Araçları için Yönetim Araçları'nı kullanıma sunmak için bir endüstri standardıdır.  
  
 WCF WMI sağlayıcısı, izleme çalışma zamanında bir WBEM uyumlu arabirimi aracılığıyla kullanıma sunan bir bileşen uygular. Yönetim Araçları, çalışma zamanında arabirimi üzerinden hizmetlere bağlanabilir. WCF hizmetleri adresler, bağlamalar, davranışları ve dinleyicileri gibi özniteliklerini kullanır.  
  
 Yerleşik WMI sağlayıcısı, uygulama yapılandırma dosyasında etkinleştirilir. Bu yoluyla yapılır `wmiProviderEnabled` özniteliği [ \<Tanılama >](../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md) içinde [ \<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) bölümünde, aşağıdaki örnekte gösterildiği gibi yapılandırma:  
  
```xml  
<system.serviceModel>  
    ...  
    <diagnostics wmiProviderEnabled="true" />  
    ...  
</system.serviceModel>  
```  
  
 Bu yapılandırma girdisi WMI arabirimini kullanıma sunar. Yönetim uygulamaları artık bu arabirimi üzerinden bağlanır ve Yönetim Araçları'nı uygulamanın erişir.  
  
## <a name="custom-wmi-object"></a>Özel WMI nesnesi  
 Bir hizmet için WMI Nesne ekleme, kullanıcı tarafından tanımlanan bilgileri yerleşik WMI sağlayıcısı bilgilerle birlikte ortaya mümkün kılar. Bu, Installutil.exe uygulamasını kullanarak WMI hizmetinin şema yayımlama tarafından gerçekleştirilir. Bunun yanı sıra daha fazla ayrıntı için yönergeler konunun sonunda kurulum yönergelerini bulunabilir.  
  
## <a name="accessing-wmi-information"></a>WMI bilgilerine erişme  
 WMI veri birçok farklı yolu erişilebilir. Microsoft, komut dosyaları, Visual Basic uygulamaları, C++ uygulamaları için WMI API'lerini sağlar ve [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] (http://msdn.microsoft.com/library/default.asp?url=/library/wmisdk/wmi/using_wmi.asp).  
  
 Bu örnek iki Java betiklerini kullanır: biri özellikleri ve kullanıcı tanımlı WMI verilerini görüntülemek için ikinci bazılarını yanı sıra bilgisayar üzerinde çalışan hizmetleri numaralandırılacak. Betik WMI sağlayıcısına bir bağlantı açar, verileri ayrıştırır ve toplanan verileri görüntüler.  
  
 Bir WCF hizmeti çalışan bir örneğini oluşturmak için örnek başlatın. Hizmet çalışırken, komut istemine aşağıdaki komutu kullanarak her Java betiği çalıştırın:  
  
```  
cscript EnumerateServices.js  
```  
  
 Komut dosyası hizmetinde bulunan araçları erişir ve şu çıkışı üretir:  
  
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
  
 Ardından, kullanıcı tanımlı WMI verilerini görüntülemek için ikinci Java betiği çalıştırın:  
  
```  
cscript EnumerateCustomObjects.js  
```  
  
 Komut dosyası, kullanıcı tanımlı araçları hizmetlerinde bulunan erişir ve şu çıkışı üretir:  
  
```  
1 WMIObject(s) found.  
|-PID:           30285bfd-9d66-4c4e-9be2-310499c5cef5  
|-InstanceId:    3839  
|-WMIInfo:       User Defined WMI Information.  
```  
  
 Çıkış bilgisayar üzerinde çalışan tek bir hizmet olduğunu gösterir. Hizmet uygulayan bir uç noktasını kullanıma sunar `ICalculator` sözleşme. Bitiş noktası tarafından uygulanan davranış ayarları ve bağlama Mesajlaşma yığınının ayrı ayrı öğeler toplamı olarak listelenir.  
  
 WMI WCF altyapısının Yönetim Araçları'nı gösterme için sınırlı değildir. Uygulamanın kendi etki alanına özgü veri öğeleri aynı mekanizma getirebilir. WMI, denetleme ve bir Web hizmeti denetimi için birleşik bir mekanizmadır.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örnek çalıştırın  
  
1.  Gerçekleştirilen olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  WMI hizmetleri şeması (InstallUtil.exe için varsayılan konumları olan "% WINDIR%\Microsoft.NET\Framework\v4.0.30319") InstallUtil.exe çalıştırarak barındırma dizinindeki service.dll dosyasını yayımlayın. Bu adım yalnızca service.dll dosyaya yapılan değişiklikler olduğunda yürütülmesi gerekiyor. Sağlama yönetim bilgilerini düzenleme uygulamaları tarafından daha fazla bilgi için bkz: http://msdn2.microsoft.com/library/ms186147.aspx "Nasıl için: yayımlama düzeni için WMI için bir izleme eklenmiş uygulamayı" bölümünde.  
  
4.  Tek veya çapraz bilgisayar yapılandırmasında örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
    > [!NOTE]
    >  WCF ASP.NET yükledikten sonra yüklerseniz, "%WINDIR%\ çalıştırmanız gerekebilir Microsoft.Net\Framework\v3.0\Windows iletişim Foundation\servicemodelreg.exe "- r - WMI nesnelerini yayınlamak için ASPNET hesabı izin vermek için x.  
  
5.  WMI aracılığıyla komutları kullanarak ortaya örnek verileri görüntüleyin: `cscript EnumerateServices.js` veya `cscript EnumerateCustomObjects.js`.  
  
> [!IMPORTANT]
>  Örnekler, bilgisayarınızda yüklü. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\WMIProvider`  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [AppFabric izleme örnekleri](http://go.microsoft.com/fwlink/?LinkId=193959)
