---
title: HTTP POST Kullanan AJAX Hizmeti
ms.date: 03/30/2017
ms.assetid: 1ac80f20-ac1c-4ed1-9850-7e49569ff44e
ms.openlocfilehash: c5e5de34573fbfc8a5c6e9607d10881941a9bed5
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68972017"
---
# <a name="ajax-service-using-http-post"></a>HTTP POST Kullanan AJAX Hizmeti

Bu örnek, HTTP POST kullanan bir ASP.NET zaman uyumsuz JavaScript ve XML (AJAX) hizmeti oluşturmak için Windows Communication Foundation (WCF) kullanmayı gösterir. AJAX Hizmeti, bir Web tarayıcısı istemcisinden temel JavaScript kodu kullanarak erişebileceğiniz bir hizmettir. Bu örnek, [Temel AJAX Hizmeti](../../../../docs/framework/wcf/samples/basic-ajax-service.md) örneği üzerinde oluşturulur; iki örnek arasındaki tek fark HTTP GET yerine HTTP POST 'un kullanımı değildir.

Windows Communication Foundation (WCF) ' de Ajax desteği, `ScriptManager` ASP.NET AJAX ile denetim aracılığıyla kullanılmak üzere iyileştirilmiştir. WCF 'yi ASP.NET AJAX ile kullanmayla ilgili bir örnek için bkz. [Ajax örnekleri](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).

> [!NOTE]
> Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.

Aşağıdaki örnekteki hizmet, AJAX 'a özgü kod içermeyen bir WCF hizmetidir.

Öznitelik bir işleme uygulanmışsa <xref:System.ServiceModel.Web.WebGetAttribute> veya öznitelik uygulanmadığından, varsayılan http fiili ("Post") kullanılır. <xref:System.ServiceModel.Web.WebInvokeAttribute> POST isteklerinin oluşturulması, GET isteklerinin daha zordur, ancak önbelleğe alınmaz; önbelleğe almanın uygun olmadığı tüm işlemler için POST istekleri kullanın.

```csharp
[ServiceContract(Namespace = "PostAjaxService")]
public interface ICalculator
{
    [WebInvoke]
    double Add(double n1, double n2);
    //Other operations omitted…
}
```

Temel Ajax hizmet örneğinde olduğu gibi, kullanarak <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>hizmette bir AJAX uç noktası oluşturun.

GET isteklerinin aksine tarayıcıdan POST hizmetlerini çağıramazsınız. Örneğin, Post hizmeti, `http://localhost/ServiceModelSamples/service.svc/Add?n1=100&n2=200` `n1` ve `n2` parametrelerinin URL 'de değil JSON biçimindeki ileti gövdesinde gönderilmesini beklediği için, bir hata ile sonuçlara gidiliyor.

PostAjaxClientPage. aspx istemci Web sayfası, kullanıcının sayfadaki işlem düğmelerinden birine tıkladığı her seferinde hizmeti çağırmak için ASP.NET kodunu içerir. Hizmet, GET isteğiyle birlikte [temel Ajax hizmet](../../../../docs/framework/wcf/samples/basic-ajax-service.md) örneğinde olduğu gibi yanıt verir.

> [!IMPORTANT]
> Örnekler bilgisayarınızda zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ' e gidin. Bu örnek, aşağıdaki dizinde bulunur.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\PostAjaxService`

## <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için

1. [Windows Communication Foundation örnekleri için kurulum yönergeleri tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.

2. [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)bölümünde açıklandığı gibi, PostAjaxService. sln çözümünü oluşturun.

3. ' A gidin (tarayıcıda, proje dizininden PostAjaxClientPage. aspx ' i açmayın). `http://localhost/ServiceModelSamples/PostAjaxClientPage.aspx`
