---
title: Güvenlik Doğrulaması
ms.date: 03/30/2017
ms.assetid: 48dcd496-0c4f-48ce-8b9b-0e25b77ffa58
author: BrucePerlerMS
ms.openlocfilehash: 4b80457fb551c2ee99f910710c5f30fa59c53a01
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47203430"
---
# <a name="security-validation"></a>Güvenlik Doğrulaması
Bu örnek, özel bir davranış Hizmetleri bunlar belirli ölçütlere uyan emin olmak için bir bilgisayar üzerinde doğrulamak için nasıl kullanılacağını gösterir. Bu örnekte, hizmetleri, hizmette her bir uç noktası aracılığıyla tarama ve güvenli bir bağlama öğeleri içeren denetleniyor özel davranış tarafından doğrulanır. Bu örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md).  
  
> [!NOTE]
>  Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.  
  
## <a name="endpoint-validation-custom-behavior"></a>Uç nokta doğrulama özel davranışı  
 Kullanıcı kodu ekleyerek `Validate` bulunan yöntemi <xref:System.ServiceModel.Description.IServiceBehavior> arabirimi, özel davranış verilebilir bir hizmet ya da uç noktası için kullanıcı tanımlı eylemleri gerçekleştirmek için. Aşağıdaki kod, bunların güvenli bağlamaları için bağlama koleksiyonları arar bir hizmette yer alan her bir uç nokta döngü için kullanılır.  
  
```  
public void Validate(ServiceDescription serviceDescription,   
                                       ServiceHostBase serviceHostBase)  
{  
    // Loop through each endpoint individually gathering their    
       binding elements.  
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
  
 Web.config dosyasına aşağıdaki kodu ekleyerek ekler `serviceValidate` hizmeti tanımak davranış uzantısı.  
  
```xml  
<system.serviceModel>  
    <extensions>  
        <behaviorExtensions>  
            <add name="endpointValidate" type="Microsoft.ServiceModel.Samples.EndpointValidateElement, endpointValidate, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null" />  
        </behaviorExtensions>  
    </extensions>  
...  
```  
  
 Davranış uzantısı hizmete eklendikten sonra artık eklemek mümkündür `endpointValidate` Web.config dosyasında davranışları listesi ve bu nedenle, hizmet davranışı.  
  
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
  
 Davranışları ve Web.config dosyasına eklenen uzantılarını ayrı ayrı hizmetlere davranışı uygulamak Machine.config dosyasına eklediğinizde while bilgisayarda etkin olan her bir hizmet davranışı uygulanır.  
  
> [!NOTE]
>  Davranış tüm hizmetlere eklerken, herhangi bir değişiklik yapmadan önce Machine.config dosyasına yedeklemek için önerilir.  
  
 Şimdi bu örnek client\bin dizininde sağlanan istemci çalıştırın. Bir özel durum olan şu ileti ile oluşur: "istenen hizmeti 'http://localhost/servicemodelsamples/service.svc' etkinleştirilemedi." Bu, bir uç nokta davranışı doğrulama uç noktası tarafından güvenli olduğu kabul edildiği için beklenen ve hizmetin başlatılmasını önler. Davranışı, ayrıca hangi uç nokta çalınabildiği için güvenli değildir ve "System.ServiceModel 4.0.0.0" kaynağı ve "WebHost" kategorisi altındaki Olay Görüntüleyicisi'ni sistem için bir ileti yazar açıklayan bir iç özel durum oluşturur. Bu örnekte service izlemeyi etkinleştirmek mümkündür. Bu hizmet izleme Görüntüleyicisi aracı kullanılarak elde edilen hizmet izlemeleri açarak doğrulama uç nokta davranışı tarafından oluşturulan özel durumları görüntülemesini sağlar.  
  
#### <a name="to-view-failed-endpoint-validation-exception-messages-in-the-event-viewer"></a>Uç nokta doğrulama özel durum iletilerinin Olay Görüntüleyicisi'nde görüntülemek için başarısız oldu  
  
1.  Tıklayın **Başlat** menü ve select **Çalıştır...** .  
  
2.  Tür `eventvwr` tıklatıp **Tamam**.  
  
3.  Olay Görüntüleyicisi'ni pencerede **uygulama**.  
  
4.  Son eklenen "System.ServiceModel 4.0.0.0" olay "WebHost" kategorisi altında çift **uygulama** güvenli bir uç nokta iletilerini görüntülemek için penceresi.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örneği çalıştırma  
  
1.  Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Tek veya çapraz makine yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Örnekler, bilgisayarınızda yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ServiceValidation`  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [AppFabric izleme örnekleri](https://go.microsoft.com/fwlink/?LinkId=193959)
