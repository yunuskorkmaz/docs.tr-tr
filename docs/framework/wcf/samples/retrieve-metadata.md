---
title: Meta Verileri Alma
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e8a6ef8c-a195-495a-a15e-7d92bdf0b28c
caps.latest.revision: "22"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: b7d9af0a76922bb9c4c1ef30c6377173a887e73b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="retrieve-metadata"></a><span data-ttu-id="f7a7b-102">Meta Verileri Alma</span><span class="sxs-lookup"><span data-stu-id="f7a7b-102">Retrieve Metadata</span></span>
<span data-ttu-id="f7a7b-103">Bu örnek, dinamik olarak hangi iletişim kurmak bir uç nokta seçmek için bir hizmet meta verileri alır istemcisini uygulama gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="f7a7b-103">This sample demonstrates how to implement a client that dynamically retrieves metadata from a service to choose an endpoint with which to communicate.</span></span> <span data-ttu-id="f7a7b-104">Bu örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="f7a7b-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span> <span data-ttu-id="f7a7b-105">İki uç nokta kullanıma sunmak için hizmetin değiştirilmiş — taban adresi kullanarak bir uç nokta `basicHttpBinding` bağlama ve güvenli bir uç noktada {*baseaddress*} / kullanarak güvenli `wsHttpBinding` bağlama.</span><span class="sxs-lookup"><span data-stu-id="f7a7b-105">The service has been modified to expose two endpoints—an endpoint at the base address using the `basicHttpBinding` binding, and a secure endpoint at {*baseaddress*}/secure using the `wsHttpBinding` binding.</span></span> <span data-ttu-id="f7a7b-106">İstemci uç nokta adresleri ve bağlamalarla yapılandırmak yerine, istemci dinamik olarak kullanarak hizmet için meta verileri alır <xref:System.ServiceModel.Description.MetadataExchangeClient> sınıfı ve meta veri içe aktaran bir <xref:System.ServiceModel.Description.ServiceEndpointCollection> kullanarak <xref:System.ServiceModel.Description.WsdlImporter> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="f7a7b-106">Instead of configuring the client with the endpoint addresses and bindings, the client dynamically retrieves the metadata for the service using the <xref:System.ServiceModel.Description.MetadataExchangeClient> class and then imports the metadata as a <xref:System.ServiceModel.Description.ServiceEndpointCollection> using the <xref:System.ServiceModel.Description.WsdlImporter> class.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f7a7b-107">Kurulum yordamı ve yapı yönergeleri Bu örnek için bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="f7a7b-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="f7a7b-108">İstemci uygulaması alınan kullanan <xref:System.ServiceModel.Description.ServiceEndpointCollection> hizmetiyle iletişim kurmak için istemcileri oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="f7a7b-108">The client application uses the imported <xref:System.ServiceModel.Description.ServiceEndpointCollection> to create clients to communicate with the service.</span></span> <span data-ttu-id="f7a7b-109">İstemci uygulaması alınan her uç noktası aracılığıyla tekrarlanan ve uygulayan her bitiş noktası ile iletişim kurar `ICalculator` sözleşme.</span><span class="sxs-lookup"><span data-stu-id="f7a7b-109">The client application iterates through each retrieved endpoint and communicates with each endpoint that implements the `ICalculator` contract.</span></span> <span data-ttu-id="f7a7b-110">İstemci her bitiş noktası ile iletişim kurmak için aşağıdaki örnek kodda gösterildiği şekilde yapılandırılmasını sağlamak amacıyla uygun adresi ve bağlama alınan noktayla sağlanır.</span><span class="sxs-lookup"><span data-stu-id="f7a7b-110">The appropriate address and binding are provided with the retrieved endpoint, so that the client is configured to communicate with each endpoint, as shown in the following sample code.</span></span>  
  
```  
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
  
 <span data-ttu-id="f7a7b-111">İstemci konsol penceresi, her bağlama ad ve adres yolunu görüntüleme uç noktaları, gönderilen işlemleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="f7a7b-111">The client console window displays the operations sent to each of the endpoints, displaying the address path and binding name.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="f7a7b-112">Ayarlamak için derleme ve örnek çalıştırın</span><span class="sxs-lookup"><span data-stu-id="f7a7b-112">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="f7a7b-113">Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f7a7b-113">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="f7a7b-114">C#, C++, Visual Basic .NET edition çözümü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f7a7b-114">To build the C#, C++, or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="f7a7b-115">Tek veya çapraz makine yapılandırmada örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f7a7b-115">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="f7a7b-116">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="f7a7b-116">The samples may already be installed on your machine.</span></span> <span data-ttu-id="f7a7b-117">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="f7a7b-117">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="f7a7b-118">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="f7a7b-118">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f7a7b-119">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="f7a7b-119">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\RetrieveMetadata`  
  
## <a name="see-also"></a><span data-ttu-id="f7a7b-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f7a7b-120">See Also</span></span>
