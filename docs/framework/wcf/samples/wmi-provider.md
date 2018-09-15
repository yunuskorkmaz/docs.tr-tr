---
title: WMI Sağlayıcısı
ms.date: 03/30/2017
ms.assetid: 462f0db3-f4a4-4a4b-ac26-41fc25c670a4
ms.openlocfilehash: c3eb97537706282491de1863224e1502d6b56fda
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2018
ms.locfileid: "45617947"
---
# <a name="wmi-provider"></a>WMI Sağlayıcısı
Bu örnek, WCF yerleşik Windows Yönetim Araçları (WMI) sağlayıcısını kullanarak çalışma zamanında Windows Communication Foundation (WCF) hizmetlerden veri toplamak nasıl gösterir. Ayrıca, bu örnek, bir kullanıcı tanımlı WMI nesnesi için bir hizmet eklemek nasıl gösterir. Örnek için WMI sağlayıcısını etkinleştirir [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md) ve veri toplamaya gösterilmiştir `ICalculator` zamanında hizmet.  
  
 WMI Web tabanlı kuruluş yönetimi (WBEM) standart Microsoft uygulamasıdır. WMI SDK'sı hakkında daha fazla bilgi için bkz. [Windows Yönetim Araçları'nı](/windows/desktop/WmiSdk/wmi-start-page). WBEM, uygulamaları dış Yönetim Araçları için Yönetim Araçları'nı nasıl kullanıma için standart bir endüstri standardıdır.  
  
 WCF izleme çalışma zamanında bir WBEM uyumlu arabirimi üzerinden kullanıma sunan bir bileşen bir WMI sağlayıcısını uygular. Yönetim Araçları hizmetler zamanında arabirimi aracılığıyla bağlanabilirsiniz. WCF hizmetleri adresler, bağlamalar, davranışları ve dinleyicileri gibi öznitelikleri gösterir.  
  
 Yerleşik WMI sağlayıcısı, uygulamanın yapılandırma dosyasında etkinleştirilir. Bu yoluyla yapılır `wmiProviderEnabled` özniteliği [ \<Tanılama >](../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md) içinde [ \<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) bölümünde, aşağıdaki örnekte gösterildiği gibi yapılandırma:  
  
```xml  
<system.serviceModel>  
    ...  
    <diagnostics wmiProviderEnabled="true" />  
    ...  
</system.serviceModel>  
```  
  
 Bu yapılandırma girişi WMI arabirimini kullanıma sunar. Yönetim uygulamaları artık bu arabirimi üzerinden bağlanabilir ve Yönetim Araçları uygulamanın erişim.  
  
## <a name="custom-wmi-object"></a>Özel WMI nesnesi  
 WMI nesnelerini bir hizmete ekleme yerleşik WMI sağlayıcısı bilgileriyle birlikte kullanıcı tarafından tanımlanan bilgileri açığa çıkarmak mümkün kılar. Bu, Installutil.exe uygulamayı kullanarak hizmet şeması için WMI yayımlayarak gerçekleştirilir. Bunun yanı sıra daha fazla ayrıntı için yönergeler konunun sonunda kurulum yönergelerini bulunabilir.  
  
## <a name="accessing-wmi-information"></a>WMI bilgilerine erişme  
 WMI verilerini birçok farklı yolu erişilebilir. Microsoft, betikleri, Visual Basic uygulamaları, C++ uygulamaları için WMI API'lerini sağlar ve [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] (http://msdn.microsoft.com/library/default.asp?url=/library/wmisdk/wmi/using_wmi.asp).  
  
 Bu örnek iki Java betiklerini kullanır: biri yanı sıra bazı kendi özellikleri ve kullanıcı tanımlı WMI verilerini görüntülemek için ikinci bir bilgisayar üzerinde çalışan hizmetleri listeleme. Betik, WMI sağlayıcısı bir bağlantı açar, verilerini ayrıştırır ve toplanan verileri görüntüler.  
  
 Bir WCF hizmeti çalışan bir örneğini oluşturmak için örneği başlatır. Hizmet çalışırken, komut isteminde aşağıdaki komutu kullanarak her Java betiği çalıştırın:  
  
```  
cscript EnumerateServices.js  
```  
  
 Betik, hizmette bulunan izleme erişir ve aşağıdaki çıktıyı üretir:  
  
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
  
 Betik ve hizmetlerde yer alan kullanıcı tanımlı araçları erişir ve aşağıdaki çıktıyı üretir:  
  
```  
1 WMIObject(s) found.  
|-PID:           30285bfd-9d66-4c4e-9be2-310499c5cef5  
|-InstanceId:    3839  
|-WMIInfo:       User Defined WMI Information.  
```  
  
 Çıktı bilgisayar üzerinde çalışan tek bir hizmet olduğunu gösterir. Hizmet uygulayan bir uç noktasını kullanıma sunar. `ICalculator` sözleşme. Bitiş noktası tarafından uygulanan ayarları davranış ve bağlama Mesajlaşma yığını tek tek öğelerine toplamı olarak listelenir.  
  
 WMI WCF altyapısının Yönetim Araçları'nı kullanıma sunmak için sınırlı değildir. Uygulama kendi etki alanına özgü veri öğelerini aynı bir mekanizma aracılığıyla kullanıma sunabilirsiniz. WMI, inceleme ve Denetim Web hizmetinin birleşik bir mekanizmadır.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örneği çalıştırma  
  
1.  Gerçekleştirdiğiniz olun [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  WMI hizmetleri şeması (InstallUtil.exe varsayılan konumları, "% WINDIR%\Microsoft.NET\Framework\v4.0.30319" dır) InstallUtil.exe çalıştırarak barındırma dizininde service.dll dosyasını yayımlayın. Bu adım yalnızca service.dll dosyasına değişiklikler yapıldığında yürütülmesi gerekiyor. Sağlama yönetim bilgilerini izleme uygulamaları tarafından daha fazla bilgi için bkz: http://msdn2.microsoft.com/library/ms186147.aspx "Nasıl için: yayımlama düzeni için WMI için bir izleme eklenmiş uygulama" bölümünde.  
  
4.  Tek veya çoklu bilgisayar yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
    > [!NOTE]
    >  WCF ASP.NET'ı yükledikten sonra yüklerseniz, "%WINDIR%\ çalıştırmanız gerekebilir Microsoft.Net\Framework\v3.0\Windows iletişimi Foundation\servicemodelreg.exe "- r - WMI Nesne yayımlamak için ASP.NET hesabı izin vermek için x.  
  
5.  WMI aracılığıyla komutları kullanarak ortaya örnekten verileri görüntüleme: `cscript EnumerateServices.js` veya `cscript EnumerateCustomObjects.js`.  
  
> [!IMPORTANT]
>  Örnekler, bilgisayarınızda yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\WMIProvider`  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [AppFabric izleme örnekleri](https://go.microsoft.com/fwlink/?LinkId=193959)
