---
title: Temel AJAX Hizmeti
ms.date: 03/30/2017
ms.assetid: d66d0c91-0109-45a0-a901-f3e4667c2465
ms.openlocfilehash: 8029549ea348ebc8337bcb649b8b0d3b1f8426b9
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70045764"
---
# <a name="basic-ajax-service"></a>Temel AJAX Hizmeti

Bu örnek, temel bir ASP.NET zaman uyumsuz JavaScript ve XML (AJAX) hizmeti (bir Web tarayıcısı istemcisinden JavaScript kodu kullanarak erişebileceğiniz bir hizmet) oluşturmak için Windows Communication Foundation (WCF) nasıl kullanılacağını gösterir. Hizmet, hizmetin http <xref:System.ServiceModel.Web.WebGetAttribute> Get isteklerini yanıtlaması ve yanıtlar için JavaScript nesne gösterimi (JSON) veri biçimini kullanacak şekilde yapılandırıldığından emin olmak için özniteliğini kullanır.

WCF 'de Ajax desteği, `ScriptManager` ASP.NET AJAX ile denetim aracılığıyla kullanılmak üzere iyileştirilmiştir. WCF 'yi ASP.NET AJAX ile kullanmayla ilgili bir örnek için bkz. [Ajax örnekleri](ajax.md).

> [!NOTE]
> Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.

Aşağıdaki kodda, <xref:System.ServiceModel.Web.WebGetAttribute> hizmetin HTTP GET isteklerine yanıt vermesini sağlamak için `Add` özniteliği işlemine uygulanır. Kod basitlik için GET kullanır (herhangi bir Web tarayıcısından bir HTTP GET isteği oluşturabilirsiniz). Ayrıca, önbelleğe almayı etkinleştirmek için Al ' i de kullanabilirsiniz. HTTP post, `WebGetAttribute` öznitelik yokluğunda varsayılandır.

```csharp
[ServiceContract(Namespace = "SimpleAjaxService")]
public interface ICalculator
{
    [WebGet]
    double Add(double n1, double n2);
    //Other operations omitted…
}
```

Örnek. svc dosyası, hizmete <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>standart bir <xref:System.ServiceModel.Description.WebScriptEndpoint> uç nokta ekleyen kullanır. Uç nokta,. svc dosyasına göre boş bir adreste yapılandırılır. Bu, hizmetin adresinin, işlem adından farklı ek `http://localhost/ServiceModelSamples/service.svc`sonekler olmadan olduğu anlamına gelir.

```svc
<%@ServiceHost language="C#" Debug="true" Service="Microsoft.Samples.SimpleAjaxService.CalculatorService" Factory="System.ServiceModel.Activation.WebScriptServiceHostFactory" %>
```

, <xref:System.ServiceModel.Description.WebScriptEndpoint> Hizmeti bir ASP.NET Ajax istemci sayfasından erişilebilir hale getirmek için önceden yapılandırılmıştır. Web. config dosyasındaki aşağıdaki bölüm, uç noktada ek yapılandırma değişiklikleri yapmak için kullanılabilir. Ek değişiklik gerekmiyorsa bu, kaldırılabilir.

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

, <xref:System.ServiceModel.Description.WebScriptEndpoint> Hizmetin varsayılan veri biçimini, XML yerine JSON olarak ayarlar. Hizmeti çağırmak için, bu konunun ilerleyen `http://localhost/ServiceModelSamples/service.svc/Add?n1=100&n2=200` kısımlarında bulunan kurulum ve oluşturma adımlarını tamamladıktan sonra ' a gidin. Bu test işlevselliği bir HTTP GET isteği kullanılarak etkinleştirildi.

Simpleleajaxclientpage. aspx istemci Web sayfası, Kullanıcı sayfadaki işlem düğmelerinden birine her tıkladığında hizmeti çağırmak için ASP.NET kodunu içerir. `ScriptManager` Denetim, hizmet üzerinde JavaScript üzerinden erişilebilen bir proxy oluşturmak için kullanılır.

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

Hizmet çağrısı başarılı olursa, kod `onSuccess` işleyiciyi çağırır ve işlemin sonucu bir metin kutusunda görüntülenir.

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
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ' e gidin. Bu örnek, aşağıdaki dizinde bulunur.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\SimpleAjaxService`
