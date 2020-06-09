---
title: Karmaşık Türler Kullanan AJAX Hizmeti Örneği
ms.date: 03/30/2017
ms.assetid: 88242b99-4811-4cbe-8201-52ddf48fb174
ms.openlocfilehash: 4227446e8844accd06490d8e7cf933da43d875a6
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84575920"
---
# <a name="ajax-service-using-complex-types-sample"></a>Karmaşık Türler Kullanan AJAX Hizmeti Örneği

Bu örnek, karmaşık türlerin örneklerini oluşturan ve bunları JavaScript Nesne Gösterimi (JSON) olarak hizmet ve istemci arasında gönderen bir ASP.NET zaman uyumsuz JavaScript ve XML (AJAX) hizmeti oluşturmak için Windows Communication Foundation (WCF) öğesinin nasıl kullanılacağını gösterir. Bir Web tarayıcısı istemcisinden JavaScript kodu kullanarak bir AJAX hizmetine erişebilirsiniz. Bu örnek, [temel Ajax hizmet](basic-ajax-service.md) örneğinde oluşturulur.

WCF 'de AJAX desteği, ASP.NET AJAX ile denetim aracılığıyla kullanılmak üzere iyileştirilmiştir <xref:System.Web.UI.ScriptManager> . WCF 'yi ASP.NET AJAX ile kullanmayla ilgili bir örnek için bkz. [Ajax örnekleri](ajax.md).

> [!NOTE]
> Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.

Aşağıdaki örnekteki hizmet, AJAX 'a özgü kod içermeyen bir WCF hizmetidir. <xref:System.ServiceModel.Web.WebGetAttribute>Özniteliği uygulanmadığından, varsayılan http fiili ("Post") kullanılır. Hizmette, `DoMath` adlı bir karmaşık tür döndüren bir işlem vardır `MathResult` . Karmaşık tür, AJAX 'a özgü kod içermeyen standart bir veri anlaşması türüdür.

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

Temel AJAX hizmet örneğinde olduğu gibi, kullanarak hizmette bir AJAX uç noktası oluşturun <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> .

ComplexTypeClientPage. aspx istemci Web sayfası, Kullanıcı sayfadaki **hesaplamayı gerçekleştir** düğmesine tıkladığında hizmeti çağırmak için ASP.net ve JavaScript kodunu içerir. Hizmeti çağırmak için kod bir JSON gövdesi oluşturur ve http post örneği [kullanılarak Ajax hizmetine](ajax-service-using-http-post.md) benzer şekılde http post kullanarak gönderir.

Hizmet çağrısı başarılı olduktan sonra, `sum` `difference` `product` `quotient` sonuçta elde edilen JavaScript nesnesine bireysel veri üyelerine (,, ve) erişebilirsiniz.

```javascript
function onSuccess(mathResult){
     document.getElementById("sum").value = mathResult.sum;
     document.getElementById("difference").value = mathResult.difference;
     document.getElementById("product").value = mathResult.product;
     document.getElementById("quotient").value = mathResult.quotient;
}
```

### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için

1. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.

2. [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)bölümünde açıklandığı gibi ComplexTypeAjaxService. sln çözümünü oluşturun.

3. `http://localhost/ServiceModelSamples/ComplexTypeClientPage.aspx`(ComplexTypeClientPage. aspx ' i tarayıcıda proje dizininden açmayın) bölümüne gidin.

> [!IMPORTANT]
> Örnekler bilgisayarınızda zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Bu örnek, aşağıdaki dizinde bulunur.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\ComplexTypeAjaxService`

## <a name="see-also"></a>Ayrıca bkz.

- [Temel AJAX Hizmeti](basic-ajax-service.md)
