---
title: Meta Verileri Alma
ms.date: 03/30/2017
ms.assetid: e8a6ef8c-a195-495a-a15e-7d92bdf0b28c
ms.openlocfilehash: 9b1adf4ed2a09625ca19016f531936002fff757d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183389"
---
# <a name="retrieve-metadata"></a>Meta Verileri Alma
Bu örnek, iletişim kurmak için bir uç nokta seçmek için bir hizmetten meta verileri dinamik olarak alan bir istemcinin nasıl uygulanacağını gösterir. Bu örnek [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md)dayanmaktadır. Hizmet, `basicHttpBinding` bağlamayı kullanarak temel adreste bir bitiş noktası ve `wsHttpBinding` {*baseaddress*}/secure'da bağlayıcıyı kullanarak güvenli bir uç noktası olmak üzere iki uç noktayı ortaya çıkaracak şekilde değiştirilmiştir. İstemci, son nokta adresleri ve bağlamalarla yapılandırmak yerine, <xref:System.ServiceModel.Description.MetadataExchangeClient> istemci sınıfı kullanarak hizmetin meta verilerini dinamik olarak <xref:System.ServiceModel.Description.ServiceEndpointCollection> alır <xref:System.ServiceModel.Description.WsdlImporter> ve sonra meta verileri sınıfı kullanarak alır.  
  
> [!NOTE]
> Bu örnek için kurulum yordamı ve yapı yönergeleri bu konunun sonunda yer alır.  
  
 İstemci uygulaması, <xref:System.ServiceModel.Description.ServiceEndpointCollection> hizmetle iletişim kurmak için istemcioluşturmak için içe aktarılan ları kullanır. İstemci uygulaması alınan her bitiş noktası üzerinden yineler ve `ICalculator` sözleşmeyi uygulayan her bitiş noktasıyla iletişim kurar. İstemci aşağıdaki örnek kodda gösterildiği gibi, her bitiş noktası ile iletişim kurmak için yapılandırılan, böylece alınan bitiş noktası ile uygun adres ve bağlama sağlanır.  
  
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
  
 İstemci konsol penceresi, adres yolunu ve bağlama adını görüntüleyen uç noktaların her birine gönderilen işlemleri görüntüler.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, oluşturmak ve çalıştırmak için  
  
1. Windows Communication Foundation [Samples için Tek Seferlik Kurulum Yordamı'nı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizi emin olun.  
  
2. Çözümün C#, C++veya Visual Basic .NET sürümünü oluşturmak için [Windows Communication Foundation Örneklerini Oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.  
  
3. Örneği tek veya çapraz makine yapılandırmasında çalıştırmak için, [Windows Communication Foundation Samples'ı çalıştıran](../../../../docs/framework/wcf/samples/running-the-samples.md)yönergeleri izleyin.  
  
> [!IMPORTANT]
> Numuneler makinenize zaten yüklenmiş olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek aşağıdaki dizinde yer almaktadır.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\RetrieveMetadata`  
