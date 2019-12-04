---
title: Yapılandırma Olmadan AJAX Hizmeti
ms.date: 03/30/2017
ms.assetid: e6db7acd-5679-45d4-b98a-8449c6873838
ms.openlocfilehash: bf80f00bbca370c973dab9f20024284a465be521
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74716206"
---
# <a name="ajax-service-without-configuration"></a>Yapılandırma Olmadan AJAX Hizmeti

Bu örnek, herhangi bir yapılandırma kullanmadan temel bir ASP.NET zaman uyumsuz JavaScript ve XML (AJAX) hizmeti (bir Web tarayıcısı istemcisinden JavaScript kodu kullanarak erişebileceğiniz bir hizmet) oluşturmak için Windows Communication Foundation (WCF) kullanmayı gösterir Ayarlar. Hizmet, bir AJAX uç noktasını otomatik olarak etkinleştirmek için. svc dosyasında özel söz dizimini kullanır.

WCF 'de AJAX desteği, `ScriptManager` denetimi aracılığıyla ASP.NET AJAX ile kullanım için iyileştirilmiştir. WCF 'yi ASP.NET AJAX ile kullanmayla ilgili bir örnek için bkz. [Ajax örnekleri](ajax.md).

> [!NOTE]
> Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.

 Bu örnek, HTTP POST kullanan AJAX hizmeti üzerinde oluşturulur. [Temel Ajax hizmet](../../../../docs/framework/wcf/samples/basic-ajax-service.md) örneğinde açıklandığı gibi, <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> hizmeti barındırmak için kullanılır.

```text
<%ServiceHost
    language=c#
    Debug="true"
    Service="Microsoft.Ajax.Samples.CalculatorService
    Factory="System.ServiceModel.Activation.WebScriptServiceHostFactory"
%>
```

<xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> otomatik olarak hizmete bir <xref:System.ServiceModel.Description.WebScriptEndpoint> ekler. Uç noktada hiçbir yapılandırma değişikliği yapılması gerekmiyorsa, `<system.ServiceModel>` bölümü hizmetin Web. config dosyasından tamamen kaldırılabilir. Web. config dosyası, ConfigFreeClientPage. aspx tarafından kullanılan bazı ASP.NET ayarlarını içerir. Böyle bir durum söz konusu değilse, Web. config dosyasının tamamı kaldırılabilir.

> [!IMPORTANT]
> Örnekler bilgisayarınızda zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek, aşağıdaki dizinde bulunur.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\ConfigFreeAjaxService`

#### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için

1. [Windows Communication Foundation örnekleri için kurulum yönergelerini bir kerelik kurulum yordamında](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.

2. [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)bölümünde açıklandığı gibi ConfigFreeAjaxService. sln çözümünü oluşturun.

3. `http://localhost/ServiceModelSamples/ConfigFreeClientPage.aspx` gidin (ConfigFreeClientPage. aspx ' i tarayıcıda proje dizini içinden açmayın).

> [!NOTE]
> Bu örneği çalıştırırken, anonim kimlik doğrulaması ve Windows kimlik doğrulamasının IIS 'deki ServiceModelSamples klasörü için eşzamanlı olarak etkinleştirilmediğinden emin olun. Bu durumda, lütfen Windows kimlik doğrulamasını devre dışı bırakın. Örneği çalıştırdığınızda, Windows kimlik doğrulamasını etkinleştirin ve "iisreset" komutunu çalıştırın.

## <a name="see-also"></a>Ayrıca bkz.

- [Temel AJAX Hizmeti](../../../../docs/framework/wcf/samples/basic-ajax-service.md)
