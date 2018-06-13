---
title: Temel AJAX Hizmeti
ms.date: 03/30/2017
ms.assetid: d66d0c91-0109-45a0-a901-f3e4667c2465
ms.openlocfilehash: 0bb8a2b28ea87cb0c22126540f6cdab604ca5120
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33805986"
---
# <a name="basic-ajax-service"></a>Temel AJAX Hizmeti
Bu örnek, Windows Communication Foundation (WCF) temel bir ASP.NET zaman uyumsuz JavaScript ve XML (AJAX) hizmet (bir Web tarayıcısı istemciden JavaScript kodu kullanarak erişebilirsiniz hizmeti) oluşturmak için nasıl kullanılacağını gösterir. Hizmet kullandığı <xref:System.ServiceModel.Web.WebGetAttribute> özniteliği hizmetinin HTTP GET isteklerine yanıt verir ve JavaScript nesne gösterimi (JSON) veri biçimi yanıtlar için kullanmak üzere yapılandırılmış emin olun.  
  
 WCF AJAX desteği ASP.NET AJAX ile kullanmak için en iyisi olan `ScriptManager` denetim. WCF ile ASP.NET AJAX kullanılarak bir örnek için bkz: [AJAX örnekleri](http://msdn.microsoft.com/library/f3fa45b3-44d5-4926-8cc4-a13c30a3bf3e).  
  
> [!NOTE]
>  Kurulum yordam ve yapılandırma yönergeleri Bu örneği için bu konunun sonunda yer alır.  
  
 Aşağıdaki kodda, <xref:System.ServiceModel.Web.WebGetAttribute> özniteliği uygulanan `Add` hizmetinin HTTP GET isteklerine yanıt vermesini sağlamak için işlem. Kod GET (bir HTTP GET isteği herhangi bir Web tarayıcısından oluşturabileceğiniz) basitleştirmek için kullanır. GET, önbelleğe almayı etkinleştirmek için de kullanabilirsiniz. HTTP POST de varsayılandır yokluğu `WebGetAttribute` özniteliği.  

```csharp
[ServiceContract(Namespace = "SimpleAjaxService")]
public interface ICalculator
{
    [WebGet]
    double Add(double n1, double n2);
    //Other operations omitted…
}
```

 Örnek .svc dosyasını kullanan <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>, hangi ekler bir <xref:System.ServiceModel.Description.WebScriptEndpoint> hizmetine standart uç noktası. Uç nokta .svc dosyasıyla ilişkili boş bir adresindeki yapılandırılır. Bu hizmet adresini anlamına gelir http://localhost/ServiceModelSamples/service.svc, işlem adı dışında hiçbir ek sonek ile.  

```svc
<%@ServiceHost language="C#" Debug="true" Service="Microsoft.Samples.SimpleAjaxService.CalculatorService" Factory="System.ServiceModel.Activation.WebScriptServiceHostFactory" %>
```

 <xref:System.ServiceModel.Description.WebScriptEndpoint> Servisi bir ASP.NET AJAX istemci sayfasından erişilebilir duruma getirmek üzere önceden yapılandırılmıştır. Web.config dosyasında aşağıdaki bölümde, uç nokta için ek yapılandırma değişiklikleri yapmak için kullanılabilir. Ek bir değişikliğe ihtiyaç olup olmadığını kaldırılabilir.  
  
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
  
 <xref:System.ServiceModel.Description.WebScriptEndpoint> Hizmeti için varsayılan veri biçimi XML yerine JSON olarak ayarlar. Hizmetini çağırmak için gidin http://localhost/ServiceModelSamples/service.svc/Add?n1=100&n2=200 sonra Yukarı kümesi tamamlama ve bu konunun ilerleyen bölümlerinde gösterilen adımlar oluşturun. Bu test işlev tarafından bir HTTP GET isteği kullanımını etkindir.  
  
 İstemci Web sayfası SimpleAjaxClientPage.aspx kullanıcı işlemi düğmeleri sayfasında birini tıkladığında hizmetini çağırmak için ASP.NET kodu içerir. `ScriptManager` Denetimi, bir proxy hizmetinde JavaScript üzerinden erişilebilir yapmak için kullanılır.  

```aspx-csharp
<asp:ScriptManager ID="ScriptManager" runat="server">  
    <Services>  
        <asp:ServiceReference Path="service.svc" />  
    </Services>  
</asp:ScriptManager>  
```

 Yerel proxy örneği ve işlemleri şu JavaScript kodunu kullanarak çağrılır.  

```javascript
// Code for extracting arguments n1 and n2 omitted…  
// Instantiate a service proxy  
var proxy = new SimpleAjaxService.ICalculator();  
// Code for selecting operation omitted…  
proxy.Add(parseFloat(n1), parseFloat(n2), onSuccess, onFail, null);  
```

 Hizmet çağrı başarılı olursa, kodu çağırır `onSuccess` işleyicisi ve işlemin sonucunu bir metin kutusunda görüntülenir.  

```javascript
function onSuccess(mathResult){  
     document.getElementById("result").value = mathResult;  
}
```

> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\SimpleAjaxService`  
  
## <a name="see-also"></a>Ayrıca Bkz.
