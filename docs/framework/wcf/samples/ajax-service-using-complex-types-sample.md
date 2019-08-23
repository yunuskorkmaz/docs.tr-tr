---
title: Karmaşık Türler Kullanan AJAX Hizmeti Örneği
ms.date: 03/30/2017
ms.assetid: 88242b99-4811-4cbe-8201-52ddf48fb174
ms.openlocfilehash: 98d33c250be31ac43eef6d76ade997a30af87090
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923687"
---
# <a name="ajax-service-using-complex-types-sample"></a>Karmaşık Türler Kullanan AJAX Hizmeti Örneği
Bu örnek, karmaşık türlerin örneklerini oluşturan ve bunları JavaScript Nesne Gösterimi (JSON) olarak hizmet ve istemci arasında gönderen bir ASP.NET zaman uyumsuz JavaScript ve XML (AJAX) hizmeti oluşturmak için Windows Communication Foundation (WCF) öğesinin nasıl kullanılacağını gösterir. Bir Web tarayıcısı istemcisinden JavaScript kodu kullanarak bir AJAX hizmetine erişebilirsiniz. Bu örnek, [temel Ajax hizmet](../../../../docs/framework/wcf/samples/basic-ajax-service.md) örneğinde oluşturulur.  
  
 WCF 'de Ajax desteği, <xref:System.Web.UI.ScriptManager> ASP.NET AJAX ile denetim aracılığıyla kullanılmak üzere iyileştirilmiştir. WCF 'yi ASP.NET AJAX ile kullanmayla ilgili bir örnek için bkz. [Ajax örnekleri](ajax.md).  
  
> [!NOTE]
> Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.  
  
 Aşağıdaki örnekteki hizmet, AJAX 'a özgü kod içermeyen bir WCF hizmetidir. <xref:System.ServiceModel.Web.WebGetAttribute> Özniteliği uygulanmadığından, varsayılan http fiili ("Post") kullanılır. Hizmette, adlı `MathResult`bir karmaşık tür `DoMath`döndüren bir işlem vardır. Karmaşık tür, AJAX 'a özgü kod içermeyen standart bir veri anlaşması türüdür.  

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

 Temel Ajax hizmet örneğinde olduğu gibi, kullanarak <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>hizmette bir AJAX uç noktası oluşturun.  
  
 ComplexTypeClientPage. aspx istemci Web sayfası, Kullanıcı sayfadaki **hesaplamayı gerçekleştir** düğmesine tıkladığında hizmeti çağırmak için ASP.net ve JavaScript kodunu içerir. Hizmeti çağırmak için kod bir JSON gövdesi oluşturur ve http post örneği [kullanılarak Ajax hizmetine](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md) benzer şekılde http post kullanarak gönderir.  
  
 Hizmet çağrısı başarılı olduktan sonra, sonuçta elde edilen JavaScript nesnesine bireysel veri üyelerine`sum`( `difference`, `product` , `quotient`ve) erişebilirsiniz.  

```javascript
function onSuccess(mathResult){  
     document.getElementById("sum").value = mathResult.sum;  
     document.getElementById("difference").value = mathResult.difference;  
     document.getElementById("product").value = mathResult.product;  
     document.getElementById("quotient").value = mathResult.quotient;  
}  
```

### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için  
  
1. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.  
  
2. [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)bölümünde açıklandığı gibi ComplexTypeAjaxService. sln çözümünü oluşturun.  
  
3. `http://localhost/ServiceModelSamples/ComplexTypeClientPage.aspx` (ComplexTypeClientPage. aspx ' i tarayıcıda proje dizininden açmayın) bölümüne gidin.  
  
> [!IMPORTANT]
>  Örnekler bilgisayarınızda zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ' e gidin. Bu örnek, aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\ComplexTypeAjaxService`  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Temel AJAX Hizmeti](../../../../docs/framework/wcf/samples/basic-ajax-service.md)
