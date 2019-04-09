---
title: Hizmet Açıklaması
ms.date: 03/30/2017
ms.assetid: 7034b5d6-d608-45f3-b57d-ec135f83ff24
ms.openlocfilehash: a1288329283eb611fa82733a2557af73a019796f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59159816"
---
# <a name="service-description"></a>Hizmet Açıklaması
Hizmet açıklaması örnek, bir hizmet, hizmet açıklaması bilgilerini, çalışma zamanında nasıl alabilirsiniz gösterir. Örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md), hizmeti hakkında açıklayıcı bilgileri döndürmek için tanımlanmış bir ek hizmet işlemi. Döndürülen bilgi tabanı ve hizmet uç noktaları listeler. Bu bilgileri kullanarak hizmeti sağlayan <xref:System.ServiceModel.OperationContext>, <xref:System.ServiceModel.ServiceHost>, ve <xref:System.ServiceModel.Description.ServiceDescription> sınıfları.  
  
 Bu örnekte, istemci bir konsol uygulaması (.exe) ve hizmet Internet Information Services (IIS) tarafından barındırılır.  
  
> [!NOTE]
>  Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.  
  
 Bu örnek adlı hesaplayıcısı sözleşme değiştirilmiş bir sürümünü sahiptir `IServiceDescriptionCalculator`. Sözleşme adında bir ek hizmet işlemi tanımlar `GetServiceDescriptionInfo` taban adresi veya adresleri ve hizmet uç noktası veya hizmet için uç noktaları açıklayan istemciye çok satırlı dize döndürür.  
  
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
  
 Uygulama kodunu `GetServiceDescriptionInfo` kullanan <xref:System.ServiceModel.Description.ServiceDescription> hizmet uç noktalarını listelemek için. Hizmet uç noktaları göreli adreslerine sahip olabileceğinden, ilk hizmeti için temel adresler listeler. Tüm bu bilgileri almak için işlem bağlamını kullanarak kod alır <xref:System.ServiceModel.OperationContext.Current%2A>. <xref:System.ServiceModel.ServiceHost> Ve kendi <xref:System.ServiceModel.Description.ServiceDescription> nesne işlemi bağlamdan alınır. Temel hizmet uç noktaları listesi için kod hizmeti konağın yinelenir <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A> koleksiyonu. Hizmeti için hizmet uç noktalarını listelemek için kod hizmet açıklaması'nın uç noktaları koleksiyonu yinelenir.  
  
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
  
 Örneği çalıştırdığınızda, hesap makinesi işlemleri ve hizmet tarafından döndürülen bilgileri görmeniz `GetServiceDescriptionInfo` işlemi. İstemci bilgisayarı için istemci penceresinde ENTER tuşuna basın.  
  
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
  
### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örneği çalıştırma  
  
1.  Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Tek veya çapraz makine yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\ServiceDescription`  
