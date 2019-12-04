---
title: HTTP POST Kullanan AJAX Hizmeti
ms.date: 03/30/2017
ms.assetid: 1ac80f20-ac1c-4ed1-9850-7e49569ff44e
ms.openlocfilehash: 560739c576965d597010a6885b53c7905aaeb8e7
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74716188"
---
# <a name="ajax-service-using-http-post"></a>HTTP POST Kullanan AJAX Hizmeti

Bu örnek, HTTP POST kullanan bir ASP.NET zaman uyumsuz JavaScript ve XML (AJAX) hizmeti oluşturmak için Windows Communication Foundation (WCF) kullanmayı gösterir. AJAX Hizmeti, bir Web tarayıcısı istemcisinden temel JavaScript kodu kullanarak erişebileceğiniz bir hizmettir. Bu örnek, [Temel AJAX Hizmeti](../../../../docs/framework/wcf/samples/basic-ajax-service.md) örneği üzerinde oluşturulur; iki örnek arasındaki tek fark HTTP GET yerine HTTP POST 'un kullanımı değildir.

Windows Communication Foundation (WCF) ' de AJAX desteği, `ScriptManager` denetim aracılığıyla ASP.NET AJAX ile kullanım için iyileştirilmiştir. WCF 'yi ASP.NET AJAX ile kullanmayla ilgili bir örnek için bkz. [Ajax örnekleri](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).

> [!NOTE]
> Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.

Aşağıdaki örnekteki hizmet, AJAX 'a özgü kod içermeyen bir WCF hizmetidir.

<xref:System.ServiceModel.Web.WebInvokeAttribute> özniteliği bir işleme uygulanmışsa veya <xref:System.ServiceModel.Web.WebGetAttribute> özniteliği uygulanmadığından, varsayılan HTTP fiili ("POST") kullanılır. POST isteklerinin oluşturulması, GET isteklerinin daha zordur, ancak önbelleğe alınmaz; önbelleğe almanın uygun olmadığı tüm işlemler için POST istekleri kullanın.

```csharp
[ServiceContract(Namespace = "PostAjaxService")]
public interface ICalculator
{
    [WebInvoke]
    double Add(double n1, double n2);
    //Other operations omitted…
}
```

Temel AJAX hizmet örneğinde olduğu gibi <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>kullanarak hizmette bir AJAX uç noktası oluşturun.

GET isteklerinin aksine tarayıcıdan POST hizmetlerini çağıramazsınız. Örneğin, POST hizmeti `n1` ve `n2` parametrelerinin URL 'de değil JSON biçimindeki ileti gövdesinde gönderilmesini beklediği için `http://localhost/ServiceModelSamples/service.svc/Add?n1=100&n2=200` ' a gitme bir hatayla sonuçlanır.

PostAjaxClientPage. aspx istemci Web sayfası, kullanıcının sayfadaki işlem düğmelerinden birine tıkladığı her seferinde hizmeti çağırmak için ASP.NET kodunu içerir. Hizmet, GET isteğiyle birlikte [temel Ajax hizmet](../../../../docs/framework/wcf/samples/basic-ajax-service.md) örneğinde olduğu gibi yanıt verir.

> [!IMPORTANT]
> Örnekler bilgisayarınızda zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek, aşağıdaki dizinde bulunur.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\PostAjaxService`

## <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için

1. [Windows Communication Foundation örnekleri için kurulum yönergeleri tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.

2. [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)bölümünde açıklandığı gibi, PostAjaxService. sln çözümünü oluşturun.

3. `http://localhost/ServiceModelSamples/PostAjaxClientPage.aspx` gidin (Bu, tarayıcıda bulunan PostAjaxClientPage. aspx ' i açın).
