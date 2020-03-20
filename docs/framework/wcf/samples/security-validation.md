---
title: Güvenlik Doğrulaması
ms.date: 03/30/2017
ms.assetid: 48dcd496-0c4f-48ce-8b9b-0e25b77ffa58
ms.openlocfilehash: 17e6e250c6b345477f7c9b377eb8e16ff4331ca7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183376"
---
# <a name="security-validation"></a>Güvenlik Doğrulaması
Bu örnek, belirli ölçütleri karşıladıklarından emin olmak için bilgisayardaki hizmetleri doğrulamak için özel bir davranışın nasıl kullanılacağını gösterir. Bu örnekte, hizmetler, hizmetteki her bitiş noktası üzerinden taranarak ve güvenli bağlama öğeleri içerip içermediklerini denetleyerek özel davranış tarafından doğrulanır. Bu örnek [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md)dayanmaktadır.  
  
> [!NOTE]
> Bu örnek için kurulum yordamı ve yapı yönergeleri bu konunun sonunda yer alır.  
  
## <a name="endpoint-validation-custom-behavior"></a>Uç Nokta Doğrulama Özel Davranış  
 Arabirimde bulunan `Validate` yönteme kullanıcı kodu eklenerek, kullanıcı tanımlı eylemleri gerçekleştirmek için bir hizmete veya bitiş noktasına özel davranış verilebilir. <xref:System.ServiceModel.Description.IServiceBehavior> Aşağıdaki kod, güvenli bağlamalar için bağlama koleksiyonları nda arama yapan bir hizmette bulunan her uç noktayı döngüye almak için kullanılır.  
  
```csharp
public void Validate(ServiceDescription serviceDescription,
                                       ServiceHostBase serviceHostBase)  
{  
    // Loop through each endpoint individually, gathering their
    // binding elements.  
    foreach (ServiceEndpoint endpoint in serviceDescription.Endpoints)  
    {  
        secureElementFound = false;  
  
        // Retrieve the endpoint's binding element collection.  
        BindingElementCollection bindingElements =
            endpoint.Binding.CreateBindingElements();  
  
        // Look to see if the binding elements collection contains any
        // secure binding elements. Transport, Asymmetric, and Symmetric
        // binding elements are all derived from SecurityBindingElement.  
        if ((bindingElements.Find<SecurityBindingElement>() != null) || (bindingElements.Find<HttpsTransportBindingElement>() != null) || (bindingElements.Find<WindowsStreamSecurityBindingElement>() != null) || (bindingElements.Find<SslStreamSecurityBindingElement>() != null))  
        {  
            secureElementFound = true;  
        }  
  
    // Send a message to the system event viewer when an endpoint is deemed insecure.  
    if (!secureElementFound)  
        throw new Exception(System.DateTime.Now.ToString() + ": The endpoint \"" + endpoint.Name + "\" has no secure bindings.");  
    }  
}  
```  
  
 Web.config dosyasına aşağıdaki kodu `serviceValidate` eklemek, hizmetin tanıyacak davranış uzantısını ekler.  
  
```xml  
<system.serviceModel>  
    <extensions>  
        <behaviorExtensions>  
            <add name="endpointValidate" type="Microsoft.ServiceModel.Samples.EndpointValidateElement, endpointValidate, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null" />  
        </behaviorExtensions>  
    </extensions>  
...  
```  
  
 Davranış uzantısı hizmete eklendikten sonra, `endpointValidate` davranışı Web.config dosyasındaki davranışlar listesine ve böylece hizmete eklemek mümkündür.  
  
```xml  
<behaviors>  
    <serviceBehaviors>  
        <behavior name="CalcServiceSEB1">  
            <serviceMetadata httpGetEnabled="true" />  
            <endpointValidate />  
        </behavior>  
    </serviceBehaviors>  
</behaviors>  
```  
  
 Web.config dosyasına eklenen davranışlar ve uzantıları, machine.config dosyasına eklendiğinde bilgisayarda etkin olan her hizmete davranış uygularken, davranışı tek tek hizmetlere uygular.  
  
> [!NOTE]
> Tüm hizmetlere davranış eklerken, herhangi bir değişiklik yapmadan önce Machine.config dosyasını yedeklemek önerilir.  
  
 Şimdi bu örnek istemci\bin dizini sağlanan istemci çalıştırın. Aşağıdaki iletide bir özel durum oluşur: "İstenen hizmet'http://localhost/servicemodelsamples/service.svcetkinleştirilemedi." Uç nokta doğrulama davranışı tarafından güvenli olarak kabul edilir ve hizmetin başlatılmasını engeller, çünkü bu bekleniyor. Davranış ayrıca hangi uç noktanın güvenli olmadığını açıklayan bir iç özel durum oluşturur ve "System.ServiceModel 4.0.0.0" kaynağı ve "WebHost" kategorisi altında sistem Olay Görüntüleyicisi'ne bir ileti yazar. Bu örnekteki hizmeti takip etmeyi de açmak mümkündür. Bu, kullanıcının, Service Trace Viewer aracını kullanarak ortaya çıkan hizmet izleme lerini açarak uç nokta doğrulama davranışıyla atılan özel durumları görüntülemesine olanak tanır.  
  
#### <a name="to-view-failed-endpoint-validation-exception-messages-in-the-event-viewer"></a>Olay Görüntüleyici'nde başarısız uç nokta doğrulama özel durum iletilerini görüntülemek için  
  
1. **Başlat** menüsüne tıklayın ve **Çalıştır'ı seçin... seçeneğini belirleyin.**  
  
2. Yaz `eventvwr` ve **Tamam'ı**tıklatın.  
  
3. Olay Görüntüleyicisi penceresinde **Uygulama'yı**tıklatın.  
  
4. Güvenli olmayan uç nokta iletilerini görüntülemek için **Uygulama** penceresinde "WebHost" kategorisi altında yeni eklenen "System.ServiceModel 4.0.0.0" etkinliğini çift tıklatın.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, oluşturmak ve çalıştırmak için  
  
1. Windows Communication Foundation [Samples için Tek Seferlik Kurulum Yordamı'nı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizi emin olun.  
  
2. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak [için, Windows Communication Foundation Samples'i oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.  
  
3. Örneği tek veya çapraz makine yapılandırmasında çalıştırmak için, [Windows Communication Foundation Samples'ı çalıştıran](../../../../docs/framework/wcf/samples/running-the-samples.md)yönergeleri izleyin.  
  
> [!IMPORTANT]
> Örnekler bilgisayarınıza zaten yüklenmiş olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek aşağıdaki dizinde yer almaktadır.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ServiceValidation`  
  
## <a name="see-also"></a>Ayrıca bkz.

- [AppFabric İzleme Örnekleri](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))
