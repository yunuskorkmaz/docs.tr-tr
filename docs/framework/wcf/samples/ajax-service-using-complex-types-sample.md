---
title: Karmaşık Türler Kullanan AJAX Hizmeti Örneği
ms.date: 03/30/2017
ms.assetid: 88242b99-4811-4cbe-8201-52ddf48fb174
ms.openlocfilehash: 54d8c90f8317b69195401eda64e8a482aaf8460a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59128511"
---
# <a name="ajax-service-using-complex-types-sample"></a>Karmaşık Türler Kullanan AJAX Hizmeti Örneği
Bu örnek, Windows Communication Foundation (WCF) karmaşık türler örneklerini oluşturur ve bunları arasındaki hizmet ve istemci JavaScript nesne gösterimi (JSON) olarak gönderir, bir ASP.NET zaman uyumsuz JavaScript ve XML (AJAX) hizmet oluşturma için nasıl kullanılacağını gösterir. JavaScript kodu bir Web tarayıcısı istemcisini kullanarak bir AJAX hizmete erişebilir. Bu örnek yapılar [temel AJAX hizmeti](../../../../docs/framework/wcf/samples/basic-ajax-service.md) örnek.  
  
 WCF AJAX desteği ASP.NET AJAX ile kullanım için optimize <xref:System.Web.UI.ScriptManager> denetimi. ASP.NET AJAX ile WCF kullanan bir örnek için bkz: [AJAX örnekleri](ajax.md).  
  
> [!NOTE]
>  Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.  
  
 Aşağıdaki örnekte bir WCF Hizmeti AJAX özgü kod olmadan hizmetidir. Çünkü <xref:System.ServiceModel.Web.WebGetAttribute> öznitelik uygulanmadı, varsayılan HTTP fiili ("POST") kullanılır. Tek bir işlem hizmeti olan `DoMath`, adlı karmaşık bir tür döndüren `MathResult`. Karmaşık tür AJAX özgü kod içeren bir standart veri anlaşması türü ' dir.  

```csharp
[DataContract]  
public class MathResult  
{  
    [DataMember]  
    public double sum;  
    [DataMember]  
    public double difference;  
    [DataMember]  
    public double product;  
    [DataMember]  
    public double quotient;  
}  
```

 Kullanarak, hizmette bir AJAX uç noktası oluşturma <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>, yalnızca temel AJAX hizmeti örneği olduğu gibi.  
  
 İstemci Web sayfası ComplexTypeClientPage.aspx kullanıcı tıkladığında hizmeti çağırmak için ASP.NET ve JavaScript kodu içeren **hesaplamayı** sayfasında düğme. Hizmet çağırmak için kodu JSON gövdesi oluşturur ve benzer HTTP POST kullanarak gönderir [hizmet HTTP POST kullanan AJAX](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md) örnek.  
  
 Hizmet çağrısı başarılı olduktan sonra bireysel veri üyeleri erişebilir (`sum`, `difference`, `product` ve `quotient`) üzerinde oluşturulan JavaScript nesnesi.  

```javascript
function onSuccess(mathResult){  
     document.getElementById("sum").value = mathResult.sum;  
     document.getElementById("difference").value = mathResult.difference;  
     document.getElementById("product").value = mathResult.product;  
     document.getElementById("quotient").value = mathResult.quotient;  
}  
```

### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örneği çalıştırma  
  
1.  Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  ' % S'çözüm ComplexTypeAjaxService.sln açıklandığı gibi oluşturmak [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Gidin `http://localhost/ServiceModelSamples/ComplexTypeClientPage.aspx` (ComplexTypeClientPage.aspx proje dizininden tarayıcıda aç değil).  
  
> [!IMPORTANT]
>  Örnekler, bilgisayarınızda yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\ComplexTypeAjaxService`  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Temel AJAX Hizmeti](../../../../docs/framework/wcf/samples/basic-ajax-service.md)
