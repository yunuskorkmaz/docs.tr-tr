---
title: "Güvenlik Doğrulaması"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 48dcd496-0c4f-48ce-8b9b-0e25b77ffa58
caps.latest.revision: "35"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 86a10a4117a5bbeb48e9d1d15b1ce8da9d7c7751
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="security-validation"></a>Güvenlik Doğrulaması
Bu örnek özel bir davranış Hizmetleri belirli ölçütlere uyan emin olmak için bir bilgisayar üzerinde doğrulamak için nasıl kullanılacağını gösterir. Bu örnekte, Hizmetleri hizmetinin her uç nokta aracılığıyla tarama ve güvenli bağlama öğelerini içeren denetleniyor özel davranış tarafından doğrulanır. Bu örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md).  
  
> [!NOTE]
>  Kurulum yordamı ve yapı yönergeleri Bu örnek için bu konunun sonunda yer alır.  
  
## <a name="endpoint-validation-custom-behavior"></a>Uç nokta doğrulama özel davranışı  
 Kullanıcı kodu ekleyerek `Validate` içinde yer alan yöntemi <xref:System.ServiceModel.Description.IServiceBehavior> arabirimi, özel davranışı verilebilir bir hizmet veya uç nokta için kullanıcı tanımlı eylemleri gerçekleştirmek için. Aşağıdaki kod, bir hizmeti güvenli bağlamaları için kendi bağlama koleksiyonları arar içinde yer alan her bitiş döngü için kullanılır.  
  
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
  
 Aşağıdaki kodu Web.config dosyasına ekleyerek ekler `serviceValidate` hizmetinin tanımak davranış uzantısı.  
  
```xml  
<system.serviceModel>  
    <extensions>  
        <behaviorExtensions>  
            <add name="endpointValidate" type="Microsoft.ServiceModel.Samples.EndpointValidateElement, endpointValidate, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null" />  
        </behaviorExtensions>  
    </extensions>  
...  
```  
  
 Davranış uzantısı hizmete eklendikten sonra artık eklemek mümkündür `endpointValidate` davranışı Web.config dosyasında davranışları listesi ve bu nedenle, hizmet.  
  
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
  
 Davranışları ve Web.config dosyasına eklendi kendi uzantıları tek tek Hizmetleri için davranış uygulamak Machine.config dosyasının eklendiğinde while her hizmetin bilgisayarda etkin davranış uygulanır.  
  
> [!NOTE]
>  Davranış tüm hizmetlere eklerken, herhangi bir değişiklik yapmadan önce Machine.config dosyasının yedeklemek için önerilir.  
  
 Şimdi bu örnek client\bin dizininde sağlanan istemci çalıştırın. Bir özel durum olan aşağıdaki iletiyle oluşur: "İstenen hizmet 'http://localhost/servicemodelsamples/service.svc' etkinleştirilemedi." Bu bir uç nokta davranışını doğrulama uç noktası tarafından güvenli olduğu kabul edildiği için beklenen ve hizmetin başlatılmasını engeller. Davranış Ayrıca hangi uç noktası güvenli olmayan ve "System.ServiceModel 4.0.0.0" kaynak ve "WebHost" kategorisi altında Sistem Olay Görüntüleyicisi'ni bir ileti yazar açıklayan iç özel durum oluşturur. Bu örnek hizmetinde izlemeyi etkinleştirmek mümkündür. Kullanıcının hizmet izleme Görüntüleyicisi aracı kullanılarak elde edilen hizmet izlemeleri açarak uç nokta doğrulama davranışı tarafından oluşturulan özel durumları görüntülemesine izin verir.  
  
#### <a name="to-view-failed-endpoint-validation-exception-messages-in-the-event-viewer"></a>Görüntülemek için uç nokta doğrulama özel durum iletilerinin Olay Görüntüleyicisi'nde başarısız oldu  
  
1.  ' I tıklatın **Başlat** menü ve select **Çalıştır...** .  
  
2.  Tür `eventvwr` tıklatıp **Tamam**.  
  
3.  Olay Görüntüleyicisi'ni penceresinde **uygulama**.  
  
4.  "WebHost" kategorisi altında son eklenen "System.ServiceModel 4.0.0.0" olayı çift **uygulama** güvensiz endpoint iletileri görüntülemek için pencere.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örnek çalıştırın  
  
1.  Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Tek veya çapraz makine yapılandırmada örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Örnekler, bilgisayarınızda yüklü. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ServiceValidation`  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [AppFabric izleme örnekleri](http://go.microsoft.com/fwlink/?LinkId=193959)
