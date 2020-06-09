---
title: Meta Verileri Alma
ms.date: 03/30/2017
ms.assetid: e8a6ef8c-a195-495a-a15e-7d92bdf0b28c
ms.openlocfilehash: 4763686485dfe97844fad78cf0bb279113c0ce08
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84594614"
---
# <a name="retrieve-metadata"></a>Meta Verileri Alma
Bu örnek, iletişim kuracak bir uç nokta seçmek üzere bir hizmetten meta verileri dinamik olarak alan bir istemcinin nasıl uygulanacağını gösterir. Bu örnek, [Başlarken](getting-started-sample.md)' i temel alır. Hizmet iki uç nokta sergilemek üzere değiştirilmiştir — bağlamayı kullanarak temel adresteki bir uç nokta `basicHttpBinding` ve bağlamayı kullanarak {*BaseAddress*}/Secure konumundaki güvenli bir uç nokta `wsHttpBinding` . İstemci, uç nokta adresleriyle ve bağlamalarıyla yapılandırmak yerine, sınıfını kullanarak hizmetin meta verilerini dinamik olarak alır <xref:System.ServiceModel.Description.MetadataExchangeClient> ve ardından meta verileri sınıfını kullanarak bir olarak içeri aktarır <xref:System.ServiceModel.Description.ServiceEndpointCollection> <xref:System.ServiceModel.Description.WsdlImporter> .  
  
> [!NOTE]
> Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.  
  
 İstemci uygulaması, <xref:System.ServiceModel.Description.ServiceEndpointCollection> hizmet ile iletişim kurmak için istemcileri oluşturmak üzere içeri aktarılan öğesini kullanır. İstemci uygulaması, alınan her bir uç nokta boyunca yinelenir ve sözleşmeyi uygulayan her bir uç nokta ile iletişim kurar `ICalculator` . Aşağıdaki örnek kodda gösterildiği gibi, istemcinin her bir uç noktayla iletişim kuracak şekilde yapılandırılması için, alınan bitiş noktasıyla ilgili adres ve bağlama birlikte sağlanır.  
  
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
  
1. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.  
  
2. Çözümün C#, C++ veya Visual Basic .NET sürümünü oluşturmak için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)konusundaki yönergeleri izleyin.  
  
3. Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.  
  
> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Bu örnek, aşağıdaki dizinde bulunur.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\RetrieveMetadata`  
