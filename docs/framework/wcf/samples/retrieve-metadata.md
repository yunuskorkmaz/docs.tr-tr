---
title: Meta Verileri Alma
ms.date: 03/30/2017
ms.assetid: e8a6ef8c-a195-495a-a15e-7d92bdf0b28c
ms.openlocfilehash: 83db86ff46d4d1e5d8382c2bd11bce85360d2ff1
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70038956"
---
# <a name="retrieve-metadata"></a>Meta Verileri Alma
Bu örnek, iletişim kuracak bir uç nokta seçmek üzere bir hizmetten meta verileri dinamik olarak alan bir istemcinin nasıl uygulanacağını gösterir. Bu örnek, [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md)' i temel alır. Hizmet iki uç nokta sergilemek üzere değiştirilmiştir — `basicHttpBinding` bağlamayı kullanarak temel adresteki bir uç nokta ve `wsHttpBinding` bağlamayı kullanarak {*BaseAddress*}/Secure konumundaki güvenli bir uç nokta. İstemci, uç nokta adresleriyle ve bağlamalarıyla yapılandırmak yerine, <xref:System.ServiceModel.Description.MetadataExchangeClient> sınıfını kullanarak hizmetin meta verilerini dinamik olarak alır ve ardından meta verileri <xref:System.ServiceModel.Description.WsdlImporter> sınıfını kullanarak bir <xref:System.ServiceModel.Description.ServiceEndpointCollection> olarak içeri aktarır.  
  
> [!NOTE]
> Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.  
  
 İstemci uygulaması, hizmet ile iletişim <xref:System.ServiceModel.Description.ServiceEndpointCollection> kurmak için istemcileri oluşturmak üzere içeri aktarılan öğesini kullanır. İstemci uygulaması, alınan her bir uç nokta boyunca yinelenir ve `ICalculator` sözleşmeyi uygulayan her bir uç nokta ile iletişim kurar. Aşağıdaki örnek kodda gösterildiği gibi, istemcinin her bir uç noktayla iletişim kuracak şekilde yapılandırılması için, alınan bitiş noktasıyla ilgili adres ve bağlama birlikte sağlanır.  
  
```csharp   
// Create a MetadataExchangeClient for retrieving metadata.  
EndpointAddress mexAddress = new EndpointAddress(ConfigurationManager.AppSettings["mexAddress"]);  
MetadataExchangeClient mexClient = new MetadataExchangeClient(mexAddress);  
  
// Retrieve the metadata for all endpoints using metadata exchange protocol (mex).  
MetadataSet metadataSet = mexClient.GetMetadata();  
  
//Convert the metadata into endpoints.  
WsdlImporter importer = new WsdlImporter(metadataSet);  
ServiceEndpointCollection endpoints = importer.ImportAllEndpoints();  
  
CalculatorClient client = null;  
ContractDescription contract = ContractDescription.GetContract(typeof(ICalculator));  
// Communicate with each endpoint that supports the ICalculator contract.  
foreach (ServiceEndpoint ep in endpoints)  
{  
    if (ep.Contract.Namespace.Equals(contract.Namespace) && ep.Contract.Name.Equals(contract.Name))  
    {  
        // Create a client using the endpoint address and binding.  
        client = new CalculatorClient(ep.Binding, new EndpointAddress(ep.Address.Uri));  
        Console.WriteLine("Communicate with endpoint: ");  
        Console.WriteLine("   AddressPath={0}", ep.Address.Uri.PathAndQuery);  
        Console.WriteLine("   Binding={0}", ep.Binding.Name);  
        // Call operations.  
        DoCalculations(client);  
  
        //Closing the client gracefully closes the connection and cleans up resources.  
        client.Close();  
    }  
}  
```  
  
 İstemci Konsolu penceresi, uç noktaların her birine gönderilen işlemleri görüntüler ve adres yolunu ve bağlama adını görüntüler.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için  
  
1. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.  
  
2. Çözümün C#, C++veya Visual Basic .NET sürümünü oluşturmak için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)konusundaki yönergeleri izleyin.  
  
3. Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md)bölümündeki yönergeleri izleyin.  
  
> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ' e gidin. Bu örnek, aşağıdaki dizinde bulunur.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\RetrieveMetadata`  
