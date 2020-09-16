---
title: Güvenlik Doğrulaması
ms.date: 03/30/2017
ms.assetid: 48dcd496-0c4f-48ce-8b9b-0e25b77ffa58
ms.openlocfilehash: ec7b7f96c1f6489f677970164f74c176b301f55b
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90557391"
---
# <a name="security-validation"></a>Güvenlik doğrulaması
Bu örnek, belirli ölçütlere uyması için bir bilgisayardaki hizmetleri doğrulamak üzere özel bir davranışın nasıl kullanılacağını gösterir. Bu örnekte, hizmetler, hizmet üzerindeki her bir uç nokta arasında tarama yaparak ve güvenli bağlama öğeleri içerip içermediğini kontrol ederek özel davranış tarafından onaylanır. Bu örnek, [Başlarken](getting-started-sample.md)' i temel alır.  
  
> [!NOTE]
> Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.  
  
## <a name="endpoint-validation-custom-behavior"></a>Uç nokta doğrulama özel davranışı  
 Arabirimde bulunan yönteme Kullanıcı kodu ekleyerek `Validate` <xref:System.ServiceModel.Description.IServiceBehavior> , Kullanıcı tanımlı eylemler gerçekleştirmek için bir hizmete veya uç noktaya özel davranış verilebilir. Aşağıdaki kod, bir hizmette yer alan her bir uç noktada, güvenli bağlamalar için bağlama koleksiyonlarında arama yapmak üzere kullanılır.  
  
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
  
 Aşağıdaki kodu Web.config dosyasına eklemek `serviceValidate` , hizmetin, tanıması için davranış uzantısını ekler.  
  
```xml  
<system.serviceModel>  
    <extensions>  
        <behaviorExtensions>  
            <add name="endpointValidate" type="Microsoft.ServiceModel.Samples.EndpointValidateElement, endpointValidate, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null" />  
        </behaviorExtensions>  
    </extensions>
    ...
</system.serviceModel>
```  
  
 Davranış uzantısı hizmete eklendikten sonra, bu `endpointValidate` davranış, Web.config dosyadaki davranışlar listesine ve bu nedenle hizmete eklenebilir.  
  
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
  
 Web.config dosyasına eklenen davranışlar ve uzantıları, her bir hizmete davranış uygular, Machine.config dosyasına eklendiğinde, bilgisayarda etkin olan her hizmete davranış uygular.  
  
> [!NOTE]
> Tüm hizmetlere davranış eklerken, herhangi bir değişiklik yapmadan önce Machine.config dosyasını yedeklemeniz önerilir.  
  
 Şimdi bu örneğin client\bin dizininde belirtilen istemciyi çalıştırın. Şu iletiyle bir özel durum oluşturuldu: "istenen hizmet, ' http://localhost/servicemodelsamples/service.svc ' etkinleştirilemedi." Uç nokta doğrulama davranışının güvenli olmadığı kabul edildiği ve hizmetin başlatılmasını önleyen için bu durum beklenmektedir. Davranış ayrıca, hangi uç noktanın güvenli olmayan olduğunu ve "System. ServiceModel 4.0.0.0" kaynağı ve "WebHost" kategorisinin altına bir Olay Görüntüleyicisi ileti yazdığını belirten bir iç özel durum oluşturur. Bu örnekteki hizmette izlemeyi açmak de mümkündür. Bu, kullanıcının Endpoint doğrulama davranışı tarafından oluşturulan özel durumları, hizmet Izleme Görüntüleyicisi aracını kullanarak elde edilen hizmet izlemelerini açarak görüntülemesine olanak tanır.  
  
### <a name="view-failed-endpoint-validation-exception-messages-in-the-event-viewer"></a>Olay Görüntüleyicisi başarısız uç nokta doğrulama özel durum iletilerini görüntüleme  
  
1. **Başlat** menüsüne tıklayın ve **Çalıştır...** seçeneğini belirleyin.  
  
2. Yazın `eventvwr` ve **Tamam**' a tıklayın.  
  
3. Olay Görüntüleyicisi penceresinde **uygulama**' ya tıklayın.  
  
4. Güvenli olmayan uç nokta iletilerini görüntülemek için **uygulama** penceresindeki "Webhost" kategorisinin altındaki son eklenen "System. ServiceModel 4.0.0.0" olayına çift tıklayın.  
  
## <a name="set-up-build-and-run-the-sample"></a>Örneği kurma, oluşturma ve çalıştırma  
  
1. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.  
  
2. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)konusundaki yönergeleri izleyin.  
  
3. Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.  
  
> [!IMPORTANT]
> Örnekler bilgisayarınızda zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Bu örnek, aşağıdaki dizinde bulunur.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ServiceValidation`  
  
## <a name="see-also"></a>Ayrıca bkz.

- [AppFabric Izleme örnekleri](/previous-versions/appfabric/ff383407(v=azure.10))
