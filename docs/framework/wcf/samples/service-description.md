---
title: "Hizmet Açıklaması"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7034b5d6-d608-45f3-b57d-ec135f83ff24
caps.latest.revision: "16"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 1d3251d960b00d34c08826957e0db9c30bd5aae3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="service-description"></a>Hizmet Açıklaması
Hizmet açıklaması örnek, bir hizmet çalışma zamanında hizmet açıklaması bilgilerini nasıl alabileceğiniz gösterilir. Örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md), hizmeti hakkında tanımlayıcı bilgileri döndürmek için tanımlanmış bir ek hizmet işlemi. Döndürülen bilgi hizmeti için uç noktalar ve temel adresler listeler. Bu bilgileri kullanarak hizmeti sağlayan <xref:System.ServiceModel.OperationContext>, <xref:System.ServiceModel.ServiceHost>, ve <xref:System.ServiceModel.Description.ServiceDescription> sınıfları.  
  
 Bu örnekte, istemci bir konsol uygulaması (.exe) ve Internet Information Services (IIS) tarafından barındırılan hizmetindeki.  
  
> [!NOTE]
>  Kurulum yordamı ve yapı yönergeleri Bu örnek için bu konunun sonunda yer alır.  
  
 Bu örnek hesaplayıcı sözleşmenin adlı değiştirilmiş bir sürümünü sahip `IServiceDescriptionCalculator`. Adlı bir ek hizmet işlemi sözleşmesini tanımlayan `GetServiceDescriptionInfo` taban adresi veya adresleri ve hizmet uç noktası veya hizmeti için uç nokta tanımlayan istemciye çok satırlı dize getirir.  
  
```  
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
  
 Uygulama kodunu `GetServiceDescriptionInfo` kullanan <xref:System.ServiceModel.Description.ServiceDescription> hizmet uç noktalarına listelemek için. Hizmet uç noktaları göreli adresleri olabileceği için önce hizmeti için temel adreslerini listeler. Tüm bu bilgileri almak için işlem bağlamını kullanarak kod edinir <xref:System.ServiceModel.OperationContext.Current%2A>. <xref:System.ServiceModel.ServiceHost> Ve kendi <xref:System.ServiceModel.Description.ServiceDescription> nesne işlemi bağlamdan alınır. Hizmet için taban uç noktaları listelemek için hizmet konağın kodu tekrarlanan <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A> koleksiyonu. Hizmeti için hizmet uç noktalarına listelemek için kod hizmet açıklaması 's uç noktaları toplulukta tekrarlanan.  
  
```  
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
  
 Hesaplayıcı işlemler'i ve ardından tarafından döndürülen hizmet bilgileri örneği çalıştırdığınızda, gördüğünüz `GetServiceDescriptionInfo` işlemi. İstemcisi penceresinde istemciyi aşağı kapatmak için ENTER tuşuna basın.  
  
```  
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
  
### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örnek çalıştırın  
  
1.  Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Tek veya çapraz makine yapılandırmada örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\ServiceDescription`  
  
## <a name="see-also"></a>Ayrıca Bkz.
