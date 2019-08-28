---
title: Yapılandırma Olmadan AJAX Hizmeti
ms.date: 03/30/2017
ms.assetid: e6db7acd-5679-45d4-b98a-8449c6873838
ms.openlocfilehash: b3c12801d14c7f6850a985c521c0e3fff92ba8e4
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70045805"
---
# <a name="ajax-service-without-configuration"></a>Yapılandırma Olmadan AJAX Hizmeti

Bu örnek, herhangi bir yapılandırma kullanmadan temel bir ASP.NET zaman uyumsuz JavaScript ve XML (AJAX) hizmeti (bir Web tarayıcısı istemcisinden JavaScript kodu kullanarak erişebileceğiniz bir hizmet) oluşturmak için Windows Communication Foundation (WCF) kullanmayı gösterir Ayarlar. Hizmet, bir AJAX uç noktasını otomatik olarak etkinleştirmek için. svc dosyasında özel söz dizimini kullanır.

WCF 'de Ajax desteği, `ScriptManager` ASP.NET AJAX ile denetim aracılığıyla kullanılmak üzere iyileştirilmiştir. WCF 'yi ASP.NET AJAX ile kullanmayla ilgili bir örnek için bkz. [Ajax örnekleri](ajax.md).

> [!NOTE]
> Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.

 Bu örnek, HTTP POST kullanan AJAX hizmeti üzerinde oluşturulur. [Temel Ajax hizmet](../../../../docs/framework/wcf/samples/basic-ajax-service.md) örneğinde açıklandığı gibi, <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> hizmetini barındırmak için kullanılır.

```svc
<%ServiceHost
    language=c#
    Debug="true"
    Service="Microsoft.Ajax.Samples.CalculatorService
    Factory="System.ServiceModel.Activation.WebScriptServiceHostFactory"
%>
```

<xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>otomatik olarak hizmetine <xref:System.ServiceModel.Description.WebScriptEndpoint> bir ekler. Uç noktada hiçbir yapılandırma değişikliği yapılması gerekmiyorsa, `<system.ServiceModel>` Bu bölüm hizmetin Web. config dosyasından tamamen kaldırılabilir. Web. config dosyası, ConfigFreeClientPage. aspx tarafından kullanılan bazı ASP.NET ayarlarını içerir. Böyle bir durum söz konusu değilse, Web. config dosyasının tamamı kaldırılabilir.

> [!IMPORTANT]
> Örnekler bilgisayarınızda zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ' e gidin. Bu örnek, aşağıdaki dizinde bulunur.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\ConfigFreeAjaxService`

#### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için

1. [Windows Communication Foundation örnekleri için kurulum yönergelerini bir kerelik kurulum yordamında](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.

2. [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)bölümünde açıklandığı gibi ConfigFreeAjaxService. sln çözümünü oluşturun.

3. `http://localhost/ServiceModelSamples/ConfigFreeClientPage.aspx` (ConfigFreeClientPage. aspx ' i tarayıcıda proje dizininden açmayın) bölümüne gidin.

> [!NOTE]
> Bu örneği çalıştırırken, anonim kimlik doğrulaması ve Windows kimlik doğrulamasının IIS 'deki ServiceModelSamples klasörü için eşzamanlı olarak etkinleştirilmediğinden emin olun. Bu durumda, lütfen Windows kimlik doğrulamasını devre dışı bırakın. Örneği çalıştırdığınızda, Windows kimlik doğrulamasını etkinleştirin ve "iisreset" komutunu çalıştırın.

## <a name="see-also"></a>Ayrıca bkz.

- [Temel AJAX Hizmeti](../../../../docs/framework/wcf/samples/basic-ajax-service.md)
