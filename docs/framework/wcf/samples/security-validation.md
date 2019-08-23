---
title: Güvenlik Doğrulaması
ms.date: 03/30/2017
ms.assetid: 48dcd496-0c4f-48ce-8b9b-0e25b77ffa58
ms.openlocfilehash: 5d37c6a46f807d5f1634348044e04bbc60f7eb98
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965454"
---
# <a name="security-validation"></a>Güvenlik Doğrulaması
Bu örnek, belirli ölçütlere uyması için bir bilgisayardaki hizmetleri doğrulamak üzere özel bir davranışın nasıl kullanılacağını gösterir. Bu örnekte, hizmetler, hizmet üzerindeki her bir uç nokta arasında tarama yaparak ve güvenli bağlama öğeleri içerip içermediğini kontrol ederek özel davranış tarafından onaylanır. Bu örnek, [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md)' i temel alır.  
  
> [!NOTE]
> Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.  
  
## <a name="endpoint-validation-custom-behavior"></a>Uç nokta doğrulama özel davranışı  
 Arabirimde<xref:System.ServiceModel.Description.IServiceBehavior> bulunan `Validate` yönteme Kullanıcı kodu ekleyerek, Kullanıcı tanımlı eylemler gerçekleştirmek için bir hizmete veya uç noktaya özel davranış verilebilir. Aşağıdaki kod, bir hizmette yer alan her bir uç noktada, güvenli bağlamalar için bağlama koleksiyonlarında arama yapmak üzere kullanılır.  
  
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
  
 Aşağıdaki kodu Web. config dosyasına eklemek, hizmetinin tanınması için `serviceValidate` davranış uzantısını ekler.  
  
```xml  
<system.serviceModel>  
    <extensions>  
        <behaviorExtensions>  
            <add name="endpointValidate" type="Microsoft.ServiceModel.Samples.EndpointValidateElement, endpointValidate, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null" />  
        </behaviorExtensions>  
    </extensions>  
...  
```  
  
 Davranış uzantısı hizmete eklendikten sonra, bu `endpointValidate` davranış, Web. config dosyasındaki davranış listesine ve dolayısıyla hizmete eklenebilir.  
  
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
  
 Web. config dosyasına eklenen davranışlar ve uzantıları, her bir hizmete davranış uygular, ancak Machine. config dosyasına eklendiğinde, bilgisayarda etkin olan her hizmete davranış uygular.  
  
> [!NOTE]
> Tüm hizmetlere davranış eklerken, herhangi bir değişiklik yapmadan önce Machine. config dosyasını yedeklemeniz önerilir.  
  
 Şimdi bu örneğin client\bin dizininde belirtilen istemciyi çalıştırın. Aşağıdaki iletiyle bir özel durum oluşur: "İstenen hizmet, 'http://localhost/servicemodelsamples/service.svc ' etkinleştirilemedi." Uç nokta doğrulama davranışının güvenli olmadığı kabul edildiği ve hizmetin başlatılmasını önleyen için bu durum beklenmektedir. Davranış ayrıca, hangi uç noktanın güvenli olmayan olduğunu ve "System. ServiceModel 4.0.0.0" kaynağı ve "WebHost" kategorisinin altına bir Olay Görüntüleyicisi ileti yazdığını belirten bir iç özel durum oluşturur. Bu örnekteki hizmette izlemeyi açmak de mümkündür. Bu, kullanıcının Endpoint doğrulama davranışı tarafından oluşturulan özel durumları, hizmet Izleme Görüntüleyicisi aracını kullanarak elde edilen hizmet izlemelerini açarak görüntülemesine olanak tanır.  
  
#### <a name="to-view-failed-endpoint-validation-exception-messages-in-the-event-viewer"></a>Olay Görüntüleyicisi başarısız uç nokta doğrulama özel durum iletilerini görüntülemek için  
  
1. **Başlat** menüsüne tıklayın ve **Çalıştır...** seçeneğini belirleyin.  
  
2. Yazın `eventvwr` ve **Tamam**' a tıklayın.  
  
3. Olay Görüntüleyicisi penceresinde **uygulama**' ya tıklayın.  
  
4. Güvenli olmayan uç nokta iletilerini görüntülemek için **uygulama** penceresindeki "Webhost" kategorisinin altındaki son eklenen "System. ServiceModel 4.0.0.0" olayına çift tıklayın.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için  
  
1. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.  
  
2. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak Için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)konusundaki yönergeleri izleyin.  
  
3. Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md)bölümündeki yönergeleri izleyin.  
  
> [!IMPORTANT]
>  Örnekler bilgisayarınızda zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ' e gidin. Bu örnek, aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ServiceValidation`  
  
## <a name="see-also"></a>Ayrıca bkz.

- [AppFabric Izleme örnekleri](https://go.microsoft.com/fwlink/?LinkId=193959)
