---
title: Hizmet Açıklaması
ms.date: 03/30/2017
ms.assetid: 7034b5d6-d608-45f3-b57d-ec135f83ff24
ms.openlocfilehash: d77797ed2871f2211ff142e2f45c160a92632138
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144093"
---
# <a name="service-description"></a>Hizmet Açıklaması
Hizmet Açıklaması örneği, bir hizmetin hizmet açıklama bilgilerini çalışma zamanında nasıl alabileceğinizi gösterir. Örnek, hizmet hakkında açıklayıcı bilgileri döndürmek için tanımlanan ek bir hizmet işlemiyle [Başlarken'e](../../../../docs/framework/wcf/samples/getting-started-sample.md)dayanır. Döndürülen bilgiler, hizmetin temel adreslerini ve uç noktalarını listeler. Hizmet, bu bilgileri <xref:System.ServiceModel.OperationContext>, <xref:System.ServiceModel.ServiceHost>, <xref:System.ServiceModel.Description.ServiceDescription> ve sınıfları kullanarak sağlar.  
  
 Bu örnekte, istemci bir konsol uygulamasıdır (.exe) ve hizmet Internet Information Services (IIS) tarafından barındırılır.  
  
> [!NOTE]
> Bu örnek için kurulum yordamı ve yapı yönergeleri bu konunun sonunda yer alır.  
  
 Bu örnek, hesap makinesi sözleşmesinin `IServiceDescriptionCalculator`değiştirilmiş bir sürümüne sahiptir. Sözleşme, istemciye hizmetin `GetServiceDescriptionInfo` temel adresini veya adreslerini ve hizmet bitiş noktasını veya bitiş noktasını açıklayan çok satırlı bir dize döndüren adlandırılmış ek bir hizmet işlemi tanımlar.  
  
```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IServiceDescriptionCalculator  
{  
    [OperationContract]  
    int Add(int n1, int n2);  
    [OperationContract]  
    int Subtract(int n1, int n2);  
    [OperationContract]  
    int Multiply(int n1, int n2);  
    [OperationContract]  
    int Divide(int n1, int n2);  
    [OperationContract]  
    string GetServiceDescriptionInfo();  
}  
```  
  
 Hizmet uç `GetServiceDescriptionInfo` noktalarını <xref:System.ServiceModel.Description.ServiceDescription> listelemek için uygulama kodu kullanır. Hizmet uç noktaları göreli adresleri olabileceğinden, önce hizmetin temel adreslerini listeler. Tüm bu bilgileri almak için kod, çalışma <xref:System.ServiceModel.OperationContext.Current%2A>bağlamını kullanarak elde eder. Ve <xref:System.ServiceModel.ServiceHost> <xref:System.ServiceModel.Description.ServiceDescription> nesnesi işlem bağlamından alınır. Hizmetin temel uç noktalarını listelemek için, kod hizmet ana <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A> bilgisayar koleksiyonunu nitedin. Hizmetin hizmet bitiş noktalarını listelemek için, kod hizmet açıklamasının uç noktaları koleksiyonunda yineler.  
  
```csharp
public string GetServiceDescriptionInfo()  
{  
    string info = "";  
    OperationContext operationContext = OperationContext.Current;  
    ServiceHost host = (ServiceHost)operationContext.Host;  
    ServiceDescription desc = host.Description;  
    // Enumerate the base addresses in the service host.  
    info += "Base addresses:\n";  
    foreach (Uri uri in host.BaseAddresses)  
    {  
        info += "    " + uri + "\n";  
    }  
    // Enumerate the service endpoints in the service description.  
    info += "Service endpoints:\n";  
    foreach (ServiceEndpoint endpoint in desc.Endpoints)  
    {  
        info += "    Address:  " + endpoint.Address + "\n";  
        info += "    Binding:  " + endpoint.Binding.Name + "\n";  
        info += "    Contract: " + endpoint.Contract.Name + "\n";  
    }  
     return info;  
}  
```  
  
 Örneği çalıştırdığınızda, hesap makinesi işlemlerini ve ardından `GetServiceDescriptionInfo` işlem tarafından döndürülen hizmet bilgilerini görürsünüz. İstemciyi kapatmak için istemci penceresinde ENTER tuşuna basın.  
  
```console  
Add(15,3) = 18  
Subtract(145,76) = 69  
Multiply(9,81) = 729  
Divide(22,7) = 3  
GetServiceDescriptionInfo  
Base addresses:  
    http://<machine-name>/ServiceModelSamples/service.svc  
    https://<machine-name>/ServiceModelSamples/service.svc  
Service endpoints:  
    Address:  http://<machine-name>/ServiceModelSamples/service.svc  
    Binding:  WSHttpBinding  
    Contract: IServiceDescriptionCalculator  
    Address:  http://<machine-name>/ServiceModelSamples/service.svc/mex  
    Binding:  MetadataExchangeHttpBinding  
    Contract: IMetadataExchange  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, oluşturmak ve çalıştırmak için  
  
1. Windows Communication Foundation [Samples için Tek Seferlik Kurulum Yordamı'nı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizi emin olun.  
  
2. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak [için, Windows Communication Foundation Samples'i oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.  
  
3. Örneği tek veya çapraz makine yapılandırmasında çalıştırmak için, [Windows Communication Foundation Samples'ı çalıştıran](../../../../docs/framework/wcf/samples/running-the-samples.md)yönergeleri izleyin.  
  
> [!IMPORTANT]
> Numuneler makinenize zaten yüklenmiş olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek aşağıdaki dizinde yer almaktadır.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\ServiceDescription`  
