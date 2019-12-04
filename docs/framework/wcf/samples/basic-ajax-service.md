---
title: Temel AJAX Hizmeti
ms.date: 03/30/2017
ms.assetid: d66d0c91-0109-45a0-a901-f3e4667c2465
ms.openlocfilehash: 334cc9e53d7d9746c204abe37e7c30d00baa824b
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74716119"
---
# <a name="basic-ajax-service"></a>Temel AJAX Hizmeti

Bu örnek, temel bir ASP.NET zaman uyumsuz JavaScript ve XML (AJAX) hizmeti (bir Web tarayıcısı istemcisinden JavaScript kodu kullanarak erişebileceğiniz bir hizmet) oluşturmak için Windows Communication Foundation (WCF) nasıl kullanılacağını gösterir. Hizmet, hizmetin HTTP GET isteklerine yanıt vermesini sağlamak için <xref:System.ServiceModel.Web.WebGetAttribute> özniteliğini kullanır ve yanıtlar için JavaScript Nesne Gösterimi (JSON) veri biçimini kullanacak şekilde yapılandırılmıştır.

WCF 'de AJAX desteği, `ScriptManager` denetimi aracılığıyla ASP.NET AJAX ile kullanım için iyileştirilmiştir. WCF 'yi ASP.NET AJAX ile kullanmayla ilgili bir örnek için bkz. [Ajax örnekleri](ajax.md).

> [!NOTE]
> Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.

Aşağıdaki kodda <xref:System.ServiceModel.Web.WebGetAttribute> özniteliği, hizmetin HTTP GET isteklerine yanıt vermesini sağlamak için `Add` işlemine uygulanır. Kod basitlik için GET kullanır (herhangi bir Web tarayıcısından bir HTTP GET isteği oluşturabilirsiniz). Ayrıca, önbelleğe almayı etkinleştirmek için Al ' i de kullanabilirsiniz. HTTP POST, `WebGetAttribute` özniteliği yokluğunda varsayılandır.

```csharp
[ServiceContract(Namespace = "SimpleAjaxService")]
public interface ICalculator
{
    [WebGet]
    double Add(double n1, double n2);
    //Other operations omitted…
}
```

Sample. svc dosyası, hizmete <xref:System.ServiceModel.Description.WebScriptEndpoint> standart uç nokta ekleyen <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>kullanır. Uç nokta,. svc dosyasına göre boş bir adreste yapılandırılır. Bu, hizmet adresinin, işlem adından farklı ek sonekler olmadan `http://localhost/ServiceModelSamples/service.svc`olduğu anlamına gelir.

`<%@ServiceHost language="C#" Debug="true" Service="Microsoft.Samples.SimpleAjaxService.CalculatorService" Factory="System.ServiceModel.Activation.WebScriptServiceHostFactory" %>`

<xref:System.ServiceModel.Description.WebScriptEndpoint>, hizmeti bir ASP.NET AJAX istemci sayfasından erişilebilir hale getirmek için önceden yapılandırılmıştır. Web. config dosyasındaki aşağıdaki bölüm, uç noktada ek yapılandırma değişiklikleri yapmak için kullanılabilir. Ek değişiklik gerekmiyorsa bu, kaldırılabilir.

```xml
<system.serviceModel>
  <standardEndpoints>
    <webScriptEndpoint>
      <!-- Use this element to configure the endpoint -->
      <standardEndpoint name=""  />
    </webScriptEndpoint>
  </standardEndpoints>
</system.serviceModel>
```

<xref:System.ServiceModel.Description.WebScriptEndpoint>, hizmetin varsayılan veri biçimini XML yerine JSON olarak ayarlar. Hizmeti çağırmak için, bu konunun ilerleyen kısımlarında gösterilen kurulum ve oluşturma adımlarını tamamladıktan sonra `http://localhost/ServiceModelSamples/service.svc/Add?n1=100&n2=200` gidin. Bu test işlevselliği bir HTTP GET isteği kullanılarak etkinleştirildi.

Simpleleajaxclientpage. aspx istemci Web sayfası, Kullanıcı sayfadaki işlem düğmelerinden birine her tıkladığında hizmeti çağırmak için ASP.NET kodunu içerir. `ScriptManager` denetimi, hizmet için JavaScript aracılığıyla erişilebilen bir proxy oluşturmak için kullanılır.

```aspx-csharp
<asp:ScriptManager ID="ScriptManager" runat="server">
    <Services>
        <asp:ServiceReference Path="service.svc" />
    </Services>
</asp:ScriptManager>
```

Yerel ara sunucu örneği oluşturulur ve işlemler aşağıdaki JavaScript kodu kullanılarak çağrılır.

```javascript
// Code for extracting arguments n1 and n2 omitted…
// Instantiate a service proxy
var proxy = new SimpleAjaxService.ICalculator();
// Code for selecting operation omitted…
proxy.Add(parseFloat(n1), parseFloat(n2), onSuccess, onFail, null);
```

Hizmet çağrısı başarılı olursa, kod `onSuccess` işleyicisini çağırır ve işlemin sonucu bir metin kutusunda görüntülenir.

```javascript
function onSuccess(mathResult){
     document.getElementById("result").value = mathResult;
}
```

> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek, aşağıdaki dizinde bulunur.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\SimpleAjaxService`
