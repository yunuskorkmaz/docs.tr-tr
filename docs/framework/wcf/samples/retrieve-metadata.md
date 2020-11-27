---
title: Meta Verileri Alma
ms.date: 03/30/2017
ms.assetid: e8a6ef8c-a195-495a-a15e-7d92bdf0b28c
ms.openlocfilehash: a7a30fee36b14d0414f2f5bed513c21a694f3484
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96255409"
---
# <a name="retrieve-metadata"></a><span data-ttu-id="ead42-102">Meta Verileri Alma</span><span class="sxs-lookup"><span data-stu-id="ead42-102">Retrieve Metadata</span></span>

<span data-ttu-id="ead42-103">Bu örnek, iletişim kuracak bir uç nokta seçmek üzere bir hizmetten meta verileri dinamik olarak alan bir istemcinin nasıl uygulanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="ead42-103">This sample demonstrates how to implement a client that dynamically retrieves metadata from a service to choose an endpoint with which to communicate.</span></span> <span data-ttu-id="ead42-104">Bu örnek, [Başlarken](getting-started-sample.md)' i temel alır.</span><span class="sxs-lookup"><span data-stu-id="ead42-104">This sample is based on the [Getting Started](getting-started-sample.md).</span></span> <span data-ttu-id="ead42-105">Hizmet iki uç nokta sergilemek üzere değiştirilmiştir — bağlamayı kullanarak temel adresteki bir uç nokta `basicHttpBinding` ve bağlamayı kullanarak {*BaseAddress*}/Secure konumundaki güvenli bir uç nokta `wsHttpBinding` .</span><span class="sxs-lookup"><span data-stu-id="ead42-105">The service has been modified to expose two endpoints—an endpoint at the base address using the `basicHttpBinding` binding, and a secure endpoint at {*baseaddress*}/secure using the `wsHttpBinding` binding.</span></span> <span data-ttu-id="ead42-106">İstemci, uç nokta adresleriyle ve bağlamalarıyla yapılandırmak yerine, sınıfını kullanarak hizmetin meta verilerini dinamik olarak alır <xref:System.ServiceModel.Description.MetadataExchangeClient> ve ardından meta verileri sınıfını kullanarak bir olarak içeri aktarır <xref:System.ServiceModel.Description.ServiceEndpointCollection> <xref:System.ServiceModel.Description.WsdlImporter> .</span><span class="sxs-lookup"><span data-stu-id="ead42-106">Instead of configuring the client with the endpoint addresses and bindings, the client dynamically retrieves the metadata for the service using the <xref:System.ServiceModel.Description.MetadataExchangeClient> class and then imports the metadata as a <xref:System.ServiceModel.Description.ServiceEndpointCollection> using the <xref:System.ServiceModel.Description.WsdlImporter> class.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ead42-107">Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="ead42-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="ead42-108">İstemci uygulaması, <xref:System.ServiceModel.Description.ServiceEndpointCollection> hizmet ile iletişim kurmak için istemcileri oluşturmak üzere içeri aktarılan öğesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="ead42-108">The client application uses the imported <xref:System.ServiceModel.Description.ServiceEndpointCollection> to create clients to communicate with the service.</span></span> <span data-ttu-id="ead42-109">İstemci uygulaması, alınan her bir uç nokta boyunca yinelenir ve sözleşmeyi uygulayan her bir uç nokta ile iletişim kurar `ICalculator` .</span><span class="sxs-lookup"><span data-stu-id="ead42-109">The client application iterates through each retrieved endpoint and communicates with each endpoint that implements the `ICalculator` contract.</span></span> <span data-ttu-id="ead42-110">Aşağıdaki örnek kodda gösterildiği gibi, istemcinin her bir uç noktayla iletişim kuracak şekilde yapılandırılması için, alınan bitiş noktasıyla ilgili adres ve bağlama birlikte sağlanır.</span><span class="sxs-lookup"><span data-stu-id="ead42-110">The appropriate address and binding are provided with the retrieved endpoint, so that the client is configured to communicate with each endpoint, as shown in the following sample code.</span></span>  
  
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
  
 <span data-ttu-id="ead42-111">İstemci Konsolu penceresi, uç noktaların her birine gönderilen işlemleri görüntüler ve adres yolunu ve bağlama adını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="ead42-111">The client console window displays the operations sent to each of the endpoints, displaying the address path and binding name.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="ead42-112">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="ead42-112">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="ead42-113">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="ead42-113">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="ead42-114">Çözümün C#, C++ veya Visual Basic .NET sürümünü oluşturmak için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)konusundaki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="ead42-114">To build the C#, C++, or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="ead42-115">Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="ead42-115">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="ead42-116">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="ead42-116">The samples may already be installed on your machine.</span></span> <span data-ttu-id="ead42-117">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="ead42-117">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="ead42-118">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="ead42-118">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ead42-119">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="ead42-119">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\RetrieveMetadata`  
