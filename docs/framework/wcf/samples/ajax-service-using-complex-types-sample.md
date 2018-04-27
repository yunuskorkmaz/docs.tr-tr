---
title: Karmaşık Türler Kullanan AJAX Hizmeti Örneği
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 88242b99-4811-4cbe-8201-52ddf48fb174
caps.latest.revision: 16
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b821a252e202f0fef719e1545b38b4423237d0c7
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2018
---
# <a name="ajax-service-using-complex-types-sample"></a>Karmaşık Türler Kullanan AJAX Hizmeti Örneği
Bu örnek nasıl kullanılacağı ortaya [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] karmaşık türler örneklerini oluşturur ve bunları hizmeti ve istemci JavaScript nesne gösterimi (JSON) olarak arasındaki gönderen bir ASP.NET zaman uyumsuz JavaScript ve XML (AJAX) bir hizmet oluşturmak için. Bir AJAX hizmeti bir Web tarayıcısı istemciden JavaScript kodu kullanarak erişebilirsiniz. Bu örnek derlemeler [temel AJAX hizmeti](../../../../docs/framework/wcf/samples/basic-ajax-service.md) örnek.  
  
 AJAX Destek [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ASP.NET AJAX ile kullanım için optimize edilmiştir <xref:System.Web.UI.ScriptManager> denetim. Kullanarak bir örnek için [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ASP.NET AJAX ile bkz [AJAX örnekleri](http://msdn.microsoft.com/library/f3fa45b3-44d5-4926-8cc4-a13c30a3bf3e).  
  
> [!NOTE]
>  Kurulum yordamı ve yapı yönergeleri Bu örnek için bu konunun sonunda yer alır.  
  
 Aşağıdaki örnek hizmetinde bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmeti ile AJAX özgü kodu yok. Çünkü <xref:System.ServiceModel.Web.WebGetAttribute> özniteliği uygulanmamış, varsayılan HTTP fiili ("POST") kullanılır. Hizmet bir işlem var `DoMath`, adlandırılmış bir karmaşık tür döndüren `MathResult`. Karmaşık türü de AJAX özgü kod içerir bir standart veri sözleşmesi türüdür.  

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

 Kullanarak hizmette bir AJAX uç noktası oluşturma <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>, yalnızca temel AJAX hizmeti örneği olduğu gibi.  
  
 İstemci Web sayfası ComplexTypeClientPage.aspx kullanıcı tıklattığında hizmetini çağırmak için ASP.NET ve JavaScript kodu içeren **hesaplamayı** sayfasında düğmesini. Hizmetini çağırmak için kodu JSON gövdesi oluşturur ve HTTP POST, benzer şekilde kullanarak gönderir [AJAX hizmeti kullanarak HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md) örnek.  
  
 Hizmet çağrı başarılı olduktan sonra tek tek veri üyeleri erişebilir (`sum`, `difference`, `product` ve `quotient`) üzerinde elde edilen JavaScript nesne.  

```javascript
function onSuccess(mathResult){  
     document.getElementById("sum").value = mathResult.sum;  
     document.getElementById("difference").value = mathResult.difference;  
     document.getElementById("product").value = mathResult.product;  
     document.getElementById("quotient").value = mathResult.quotient;  
}  
```

### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örnek çalıştırın  
  
1.  Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Çözüm ComplexTypeAjaxService.sln açıklandığı gibi yapı [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Gidin http://localhost/ServiceModelSamples/ComplexTypeClientPage.aspx (ComplexTypeClientPage.aspx proje dizininden tarayıcıda aç değil).  
  
> [!IMPORTANT]
>  Örnekler, bilgisayarınızda yüklü. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\ComplexTypeAjaxService`  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Temel AJAX Hizmeti](../../../../docs/framework/wcf/samples/basic-ajax-service.md)
