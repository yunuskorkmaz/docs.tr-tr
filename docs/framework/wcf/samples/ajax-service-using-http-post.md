---
title: HTTP POST Kullanan AJAX Hizmeti
ms.date: 03/30/2017
ms.assetid: 1ac80f20-ac1c-4ed1-9850-7e49569ff44e
ms.openlocfilehash: df199b40a4a9ebb9a36cea7234b484273348cd9e
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50192804"
---
# <a name="ajax-service-using-http-post"></a>HTTP POST Kullanan AJAX Hizmeti
Bu örnek oluşturmak için Windows Communication Foundation (WCF) kullanmayı gösteren bir [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] HTTP POST kullanan zaman uyumsuz JavaScript ve XML (AJAX) hizmet. Bir AJAX temel JavaScript kodunu bir Web tarayıcısı istemcisini kullanarak erişebileceğiniz bir hizmettir. Bu örnek yapılar [temel AJAX hizmeti](../../../../docs/framework/wcf/samples/basic-ajax-service.md) örnek; iki örnek arasındaki tek fark, HTTP POST HTTP GET yerine kullanılmasıdır.  
  
 AJAX desteği Windows Communication Foundation (WCF) ASP.NET AJAX ile kullanım için optimize `ScriptManager` denetimi. ASP.NET AJAX ile WCF kullanan bir örnek için bkz: [Ajax örnekleri](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).  
  
> [!NOTE]
>  Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.  
  
 Aşağıdaki örnekte bir WCF Hizmeti AJAX özgü kod olmadan hizmetidir.  
  
 Varsa <xref:System.ServiceModel.Web.WebInvokeAttribute> öznitelik, bir işlem üzerinde uygulanan veya <xref:System.ServiceModel.Web.WebGetAttribute> öznitelik uygulanmadı, varsayılan HTTP fiili ("POST") kullanılır. GET isteği oluşturmak için POST istekleri daha zor olan, ancak önbelleğe alınmaz. POST istekleri önbelleğe alma uygun olduğu tüm işlemler için kullanın.  

```csharp
[ServiceContract(Namespace = "PostAjaxService")]  
public interface ICalculator  
{
    [WebInvoke]  
    double Add(double n1, double n2);  
    //Other operations omitted…  
}
```

 Kullanarak, hizmette bir AJAX uç noktası oluşturma <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>, yalnızca temel AJAX hizmeti örneği olduğu gibi.  
  
 GET istekleri tarayıcıdan GÖNDERİSİNE Hizmetleri çağrılamıyor. Örneğin, giderek `http://localhost/ServiceModelSamples/service.svc/Add?n1=100&n2=200` POST hizmet beklediği için hata sonuçları `n1` ve `n2` JSON biçiminde ve URL içinde değil ileti gövdesinde gönderilecek parametreleri.  
  
 İstemci Web sayfası PostAjaxClientPage.aspx sayfasında işlemi düğmelerden birine kullanıcı tıkladığında hizmeti çağırmak için ASP.NET kodu içerir. Hizmet yanıt olarak aynı şekilde [temel AJAX hizmeti](../../../../docs/framework/wcf/samples/basic-ajax-service.md) GET isteğiyle örnek.  
  
> [!IMPORTANT]
>  Örnekler, bilgisayarınızda yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\PostAjaxService`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örneği çalıştırma  
  
1.  Kurulum yönergelerini gerçekleştirdiğinizden emin olun [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  ' % S'çözüm PostAjaxService.sln açıklandığı gibi oluşturmak [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Gidin `http://localhost/ServiceModelSamples/PostAjaxClientPage.aspx` (PostAjaxClientPage.aspx proje dizininden tarayıcıda aç değil).
