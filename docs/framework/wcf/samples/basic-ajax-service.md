---
title: Temel AJAX Hizmeti
ms.date: 03/30/2017
ms.assetid: d66d0c91-0109-45a0-a901-f3e4667c2465
ms.openlocfilehash: d8da6469101511b6b5a9ce19a11f1e5e3fe9d83e
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43402722"
---
# <a name="basic-ajax-service"></a>Temel AJAX Hizmeti
Bu örnek, Windows Communication Foundation (WCF) temel bir ASP.NET zaman uyumsuz JavaScript ve XML (AJAX) hizmeti (bir Web tarayıcısı istemciden JavaScript kodu kullanarak erişebileceğiniz bir hizmeti) oluşturmak için nasıl kullanılacağını gösterir. Hizmeti kullandığı <xref:System.ServiceModel.Web.WebGetAttribute> hizmet HTTP GET isteklerine yanıt verir ve yanıtları için JavaScript nesne gösterimi (JSON) veri biçimini kullanacak şekilde yapılandırılmış emin olmak için özniteliği.  
  
 WCF AJAX desteği ASP.NET AJAX ile kullanım için optimize `ScriptManager` denetimi. ASP.NET AJAX ile WCF kullanan bir örnek için bkz: [AJAX örnekleri](https://msdn.microsoft.com/library/f3fa45b3-44d5-4926-8cc4-a13c30a3bf3e).  
  
> [!NOTE]
>  Bu örnek için Kurulum yordamı ve derleme yönergeleri Bu konunun sonunda yer alır.  
  
 Aşağıdaki kodda, <xref:System.ServiceModel.Web.WebGetAttribute> özniteliği uygulandığı `Add` hizmet HTTP GET isteklerine yanıt vermesini sağlamak için işlemi. Kod Al (herhangi bir Web tarayıcısından HTTP GET isteği oluşturabilirsiniz) kolaylık sağlamak için kullanır. GET, önbelleğe almayı etkinleştirmek için de kullanabilirsiniz. HTTP POST, varsayılan olmadığında `WebGetAttribute` özniteliği.  

```csharp
[ServiceContract(Namespace = "SimpleAjaxService")]
public interface ICalculator
{
    [WebGet]
    double Add(double n1, double n2);
    //Other operations omitted…
}
```

 Örnek .svc dosyasını kullanan <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>, hangi ekler bir <xref:System.ServiceModel.Description.WebScriptEndpoint> hizmetine standart uç noktası. Uç nokta, boş bir adresten .svc dosyanın göreli yapılandırılır. Bu hizmet adresini olduğu anlamına gelir http://localhost/ServiceModelSamples/service.svc, işlem adı dışında hiçbir ek sonekleri ile.  

```svc
<%@ServiceHost language="C#" Debug="true" Service="Microsoft.Samples.SimpleAjaxService.CalculatorService" Factory="System.ServiceModel.Activation.WebScriptServiceHostFactory" %>
```

 <xref:System.ServiceModel.Description.WebScriptEndpoint> Hizmeti bir ASP.NET AJAX istemci sayfasından erişilebilir hale getirmek için önceden yapılandırılmıştır. Web.config dosyasında aşağıdaki bölümde, uç nokta için ek yapılandırma değişiklikleri yapmak için kullanılabilir. Ek bir değişikliğe ihtiyaç olup olmadığını kaldırılabilir.  
  
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
  
 <xref:System.ServiceModel.Description.WebScriptEndpoint> Hizmeti için varsayılan veri biçimi XML yerine JSON ayarlar. Hizmetini çağırmak için gidin http://localhost/ServiceModelSamples/service.svc/Add?n1=100&n2=200 sonra kümesi kurma tamamlanıyor ve bu konunun ilerleyen bölümlerinde gösterilen adımları oluşturun. Bu test işlevi bir HTTP GET isteği kullanımını tarafından etkinleştirilir.  
  
 İstemci Web sayfası SimpleAjaxClientPage.aspx sayfasında işlemi düğmelerden birine kullanıcı tıkladığında hizmeti çağırmak için ASP.NET kodu içerir. `ScriptManager` Denetimi proxy hizmet için JavaScript üzerinden erişilebilir hale getirmek için kullanılır.  

```aspx-csharp
<asp:ScriptManager ID="ScriptManager" runat="server">  
    <Services>  
        <asp:ServiceReference Path="service.svc" />  
    </Services>  
</asp:ScriptManager>  
```

 Yerel proxy örneği ve aşağıdaki JavaScript kodunu kullanarak işlem çağrılır.  

```javascript
// Code for extracting arguments n1 and n2 omitted…  
// Instantiate a service proxy  
var proxy = new SimpleAjaxService.ICalculator();  
// Code for selecting operation omitted…  
proxy.Add(parseFloat(n1), parseFloat(n2), onSuccess, onFail, null);  
```

 Hizmet çağrısı başarılı olursa, kodu çağıran `onSuccess` işleyicisi ve işlemin sonucunu bir metin kutusunda görüntülenir.  

```javascript
function onSuccess(mathResult){  
     document.getElementById("result").value = mathResult;  
}
```

> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\SimpleAjaxService`  
  
## <a name="see-also"></a>Ayrıca Bkz.
