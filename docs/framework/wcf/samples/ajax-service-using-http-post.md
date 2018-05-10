---
title: HTTP POST Kullanan AJAX Hizmeti
ms.date: 03/30/2017
ms.assetid: 1ac80f20-ac1c-4ed1-9850-7e49569ff44e
ms.openlocfilehash: f904a26d87a21a931035b45261dbcd970f7d63a1
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2018
---
# <a name="ajax-service-using-http-post"></a>HTTP POST Kullanan AJAX Hizmeti
Bu örnek Windows Communication Foundation (WCF) oluşturmak için nasıl kullanılacağını gösteren bir [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] HTTP POST kullanan zaman uyumsuz JavaScript ve XML (AJAX) hizmet. Bir AJAX hizmeti bir Web tarayıcısı istemciden temel JavaScript kodu kullanarak erişebilirsiniz biridir. Bu örnek derlemeler [temel AJAX hizmeti](../../../../docs/framework/wcf/samples/basic-ajax-service.md) örnek; iki örnek arasındaki tek fark, HTTP POST HTTP GET yerine kullanılmasıdır.  
  
 AJAX destek Windows Communication Foundation (WCF) ASP.NET AJAX ile kullanmak için en iyisi olan `ScriptManager` denetim. WCF ile ASP.NET AJAX kullanılarak bir örnek için bkz: [Ajax örnekleri](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).  
  
> [!NOTE]
>  Kurulum yordamı ve yapı yönergeleri Bu örnek için bu konunun sonunda yer alır.  
  
 Aşağıdaki örnek hizmetinde bir AJAX özgü kod olmadan WCF hizmetidir.  
  
 Varsa <xref:System.ServiceModel.Web.WebInvokeAttribute> özniteliği üzerinde bir işlemi, uygulanan veya <xref:System.ServiceModel.Web.WebGetAttribute> özniteliği uygulanmamış, varsayılan HTTP fiili ("POST") kullanılır. POST istekleri GET istekleri oluşturmak için daha zor olan ancak önbelleğe alınmaz; POST istekleri önbelleğe alma uygun olduğu tüm işlemler için kullanın.  

```csharp
[ServiceContract(Namespace = "PostAjaxService")]  
public interface ICalculator  
{
    [WebInvoke]  
    double Add(double n1, double n2);  
    //Other operations omitted…  
}
```

 Kullanarak hizmette bir AJAX uç noktası oluşturma <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>, yalnızca temel AJAX hizmeti örneği olduğu gibi.  
  
 GET isteklerinin tersine, tarayıcı POST Hizmetleri'nden çağıramaz. Örneğin, gezinme http://localhost/ServiceModelSamples/service.svc/Add?n1=100&n2=200 POST hizmet beklediği bir hatayla sonuçlanır `n1` ve `n2` ileti gövdesi içinde gönderilmek üzere parametreleri — JSON biçiminde — ve URL içinde değil.  
  
 İstemci Web sayfası PostAjaxClientPage.aspx kullanıcı işlemi düğmeleri sayfasında birini tıkladığında hizmetini çağırmak için ASP.NET kodu içerir. Hizmet yanıt olarak aynı şekilde [temel AJAX hizmeti](../../../../docs/framework/wcf/samples/basic-ajax-service.md) GET isteği ile örnek.  
  
> [!IMPORTANT]
>  Örnekler, bilgisayarınızda yüklü. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\PostAjaxService`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örnek çalıştırın  
  
1.  Kurulum yönergelerini gerçekleştirdiğinizden emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Çözüm PostAjaxService.sln açıklandığı gibi yapı [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Gidin http://localhost/ServiceModelSamples/PostAjaxClientPage.aspx (PostAjaxClientPage.aspx proje dizininden tarayıcıda aç değil).  
  
## <a name="see-also"></a>Ayrıca Bkz.
