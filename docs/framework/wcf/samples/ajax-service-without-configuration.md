---
title: Yapılandırma Olmadan AJAX Hizmeti
ms.date: 03/30/2017
ms.assetid: e6db7acd-5679-45d4-b98a-8449c6873838
ms.openlocfilehash: ab3731ab6aeb80e0e46228b8bf702b0fe5c6e6e9
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84575907"
---
# <a name="ajax-service-without-configuration"></a>Yapılandırma Olmadan AJAX Hizmeti

Bu örnekte, herhangi bir yapılandırma ayarı kullanmadan temel bir ASP.NET zaman uyumsuz JavaScript ve XML (AJAX) hizmeti (bir Web tarayıcısı istemcisinden JavaScript kodu kullanarak erişebileceğiniz bir hizmet) oluşturmak için Windows Communication Foundation (WCF) kullanımı gösterilmektedir. Hizmet, bir AJAX uç noktasını otomatik olarak etkinleştirmek için. svc dosyasında özel söz dizimini kullanır.

WCF 'de AJAX desteği, ASP.NET AJAX ile denetim aracılığıyla kullanılmak üzere iyileştirilmiştir `ScriptManager` . WCF 'yi ASP.NET AJAX ile kullanmayla ilgili bir örnek için bkz. [Ajax örnekleri](ajax.md).

> [!NOTE]
> Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.

 Bu örnek, HTTP POST kullanan AJAX hizmeti üzerinde oluşturulur. [Temel Ajax hizmet](basic-ajax-service.md) örneğinde açıklandığı gibi, <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> hizmetini barındırmak için kullanılır.

```text
<%ServiceHost
    language=c#
    Debug="true"
    Service="Microsoft.Ajax.Samples.CalculatorService
    Factory="System.ServiceModel.Activation.WebScriptServiceHostFactory"
%>
```

<xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>otomatik olarak hizmetine bir ekler <xref:System.ServiceModel.Description.WebScriptEndpoint> . Uç noktada hiçbir yapılandırma değişikliği yapılması gerekmiyorsa, bu `<system.ServiceModel>` bölüm hizmetin Web. config dosyasından tamamen kaldırılabilir. Web. config dosyası, ConfigFreeClientPage. aspx tarafından kullanılan bazı ASP.NET ayarlarını içerir. Böyle bir durum söz konusu değilse, Web. config dosyasının tamamı kaldırılabilir.

> [!IMPORTANT]
> Örnekler bilgisayarınızda zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Bu örnek, aşağıdaki dizinde bulunur.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\ConfigFreeAjaxService`

#### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için

1. [Windows Communication Foundation örnekleri için kurulum yönergelerini bir kerelik kurulum yordamında](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.

2. [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)bölümünde açıklandığı gibi ConfigFreeAjaxService. sln çözümünü oluşturun.

3. `http://localhost/ServiceModelSamples/ConfigFreeClientPage.aspx`(ConfigFreeClientPage. aspx ' i tarayıcıda proje dizininden açmayın) bölümüne gidin.

> [!NOTE]
> Bu örneği çalıştırırken, anonim kimlik doğrulaması ve Windows kimlik doğrulamasının IIS 'deki ServiceModelSamples klasörü için eşzamanlı olarak etkinleştirilmediğinden emin olun. Bu durumda, lütfen Windows kimlik doğrulamasını devre dışı bırakın. Örneği çalıştırdığınızda, Windows kimlik doğrulamasını etkinleştirin ve "iisreset" komutunu çalıştırın.

## <a name="see-also"></a>Ayrıca bkz.

- [Temel AJAX Hizmeti](basic-ajax-service.md)
