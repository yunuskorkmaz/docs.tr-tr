---
title: Meta Verileri Alma
ms.date: 03/30/2017
ms.assetid: e8a6ef8c-a195-495a-a15e-7d92bdf0b28c
ms.openlocfilehash: f35bb14b9338197828189a1d91d5653fd1680b86
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59208689"
---
# <a name="retrieve-metadata"></a><span data-ttu-id="92ca5-102">Meta Verileri Alma</span><span class="sxs-lookup"><span data-stu-id="92ca5-102">Retrieve Metadata</span></span>
<span data-ttu-id="92ca5-103">Bu örnek nasıl dinamik olarak bir hizmet ile iletişim kurmak için bir uç noktayı seçmek için meta verileri alır bir istemci uygulanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="92ca5-103">This sample demonstrates how to implement a client that dynamically retrieves metadata from a service to choose an endpoint with which to communicate.</span></span> <span data-ttu-id="92ca5-104">Bu örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="92ca5-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span> <span data-ttu-id="92ca5-105">Hizmet, iki uç nokta kullanıma sunmak için değiştirilmiş — kullanarak temel adres bir uç nokta `basicHttpBinding` bağlama ve güvenli bir uç noktada {*baseaddress*} / kullanarak güvenli hale getirme `wsHttpBinding` bağlama.</span><span class="sxs-lookup"><span data-stu-id="92ca5-105">The service has been modified to expose two endpoints—an endpoint at the base address using the `basicHttpBinding` binding, and a secure endpoint at {*baseaddress*}/secure using the `wsHttpBinding` binding.</span></span> <span data-ttu-id="92ca5-106">İstemci uç nokta adresleri ve bağlamalar ile yapılandırmak yerine, istemci dinamik olarak kullanarak hizmet için meta verileri alır <xref:System.ServiceModel.Description.MetadataExchangeClient> sınıfı ve ardından olarak meta veriler alır bir <xref:System.ServiceModel.Description.ServiceEndpointCollection> kullanarak <xref:System.ServiceModel.Description.WsdlImporter> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="92ca5-106">Instead of configuring the client with the endpoint addresses and bindings, the client dynamically retrieves the metadata for the service using the <xref:System.ServiceModel.Description.MetadataExchangeClient> class and then imports the metadata as a <xref:System.ServiceModel.Description.ServiceEndpointCollection> using the <xref:System.ServiceModel.Description.WsdlImporter> class.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="92ca5-107">Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="92ca5-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="92ca5-108">İstemci uygulamasını içeri aktarılan kullanan <xref:System.ServiceModel.Description.ServiceEndpointCollection> hizmetiyle iletişim kurmak için istemcilerin oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="92ca5-108">The client application uses the imported <xref:System.ServiceModel.Description.ServiceEndpointCollection> to create clients to communicate with the service.</span></span> <span data-ttu-id="92ca5-109">İstemci uygulaması, alınan her uç nokta yinelenir ve uygulayan her bir uç noktası ile iletişim kuran `ICalculator` sözleşme.</span><span class="sxs-lookup"><span data-stu-id="92ca5-109">The client application iterates through each retrieved endpoint and communicates with each endpoint that implements the `ICalculator` contract.</span></span> <span data-ttu-id="92ca5-110">İstemci her uç nokta ile iletişim kurmak için aşağıdaki örnek kodda gösterildiği gibi yapılandırılması bağlamasını ve adresini uygun alınan uç nokta ile sağlanır.</span><span class="sxs-lookup"><span data-stu-id="92ca5-110">The appropriate address and binding are provided with the retrieved endpoint, so that the client is configured to communicate with each endpoint, as shown in the following sample code.</span></span>  
  
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
  
 <span data-ttu-id="92ca5-111">Her bağlama adı ve adresi yolunu görüntüleme uç noktaları, gönderilen operations istemci konsol penceresinde görüntüler.</span><span class="sxs-lookup"><span data-stu-id="92ca5-111">The client console window displays the operations sent to each of the endpoints, displaying the address path and binding name.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="92ca5-112">Ayarlamak için derleme ve örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="92ca5-112">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="92ca5-113">Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="92ca5-113">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="92ca5-114">Çözüm C#, C++ veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="92ca5-114">To build the C#, C++, or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="92ca5-115">Tek veya çapraz makine yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="92ca5-115">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="92ca5-116">Örnekler, makinenizde zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="92ca5-116">The samples may already be installed on your machine.</span></span> <span data-ttu-id="92ca5-117">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="92ca5-117">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="92ca5-118">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="92ca5-118">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="92ca5-119">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="92ca5-119">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\RetrieveMetadata`  
