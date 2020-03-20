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
# <a name="service-description"></a><span data-ttu-id="f8af8-102">Hizmet Açıklaması</span><span class="sxs-lookup"><span data-stu-id="f8af8-102">Service Description</span></span>
<span data-ttu-id="f8af8-103">Hizmet Açıklaması örneği, bir hizmetin hizmet açıklama bilgilerini çalışma zamanında nasıl alabileceğinizi gösterir.</span><span class="sxs-lookup"><span data-stu-id="f8af8-103">The Service Description sample demonstrates how a service can retrieve its service description information at runtime.</span></span> <span data-ttu-id="f8af8-104">Örnek, hizmet hakkında açıklayıcı bilgileri döndürmek için tanımlanan ek bir hizmet işlemiyle [Başlarken'e](../../../../docs/framework/wcf/samples/getting-started-sample.md)dayanır.</span><span class="sxs-lookup"><span data-stu-id="f8af8-104">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), with an additional service operation defined to return descriptive information about the service.</span></span> <span data-ttu-id="f8af8-105">Döndürülen bilgiler, hizmetin temel adreslerini ve uç noktalarını listeler.</span><span class="sxs-lookup"><span data-stu-id="f8af8-105">The information that is returned lists the base addresses and endpoints for the service.</span></span> <span data-ttu-id="f8af8-106">Hizmet, bu bilgileri <xref:System.ServiceModel.OperationContext>, <xref:System.ServiceModel.ServiceHost>, <xref:System.ServiceModel.Description.ServiceDescription> ve sınıfları kullanarak sağlar.</span><span class="sxs-lookup"><span data-stu-id="f8af8-106">The service provides this information using the <xref:System.ServiceModel.OperationContext>, <xref:System.ServiceModel.ServiceHost>, and <xref:System.ServiceModel.Description.ServiceDescription> classes.</span></span>  
  
 <span data-ttu-id="f8af8-107">Bu örnekte, istemci bir konsol uygulamasıdır (.exe) ve hizmet Internet Information Services (IIS) tarafından barındırılır.</span><span class="sxs-lookup"><span data-stu-id="f8af8-107">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f8af8-108">Bu örnek için kurulum yordamı ve yapı yönergeleri bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="f8af8-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="f8af8-109">Bu örnek, hesap makinesi sözleşmesinin `IServiceDescriptionCalculator`değiştirilmiş bir sürümüne sahiptir.</span><span class="sxs-lookup"><span data-stu-id="f8af8-109">This sample has a modified version of the calculator contract called `IServiceDescriptionCalculator`.</span></span> <span data-ttu-id="f8af8-110">Sözleşme, istemciye hizmetin `GetServiceDescriptionInfo` temel adresini veya adreslerini ve hizmet bitiş noktasını veya bitiş noktasını açıklayan çok satırlı bir dize döndüren adlandırılmış ek bir hizmet işlemi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f8af8-110">The contract defines an additional service operation named `GetServiceDescriptionInfo` that returns a multi-line string to the client that describes the base address or addresses and service endpoint or endpoints for the service.</span></span>  
  
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
  
 <span data-ttu-id="f8af8-111">Hizmet uç `GetServiceDescriptionInfo` noktalarını <xref:System.ServiceModel.Description.ServiceDescription> listelemek için uygulama kodu kullanır.</span><span class="sxs-lookup"><span data-stu-id="f8af8-111">The implementation code for `GetServiceDescriptionInfo` uses the <xref:System.ServiceModel.Description.ServiceDescription> to list the service endpoints.</span></span> <span data-ttu-id="f8af8-112">Hizmet uç noktaları göreli adresleri olabileceğinden, önce hizmetin temel adreslerini listeler.</span><span class="sxs-lookup"><span data-stu-id="f8af8-112">Because service endpoints can have relative addresses, it first lists the base addresses for the service.</span></span> <span data-ttu-id="f8af8-113">Tüm bu bilgileri almak için kod, çalışma <xref:System.ServiceModel.OperationContext.Current%2A>bağlamını kullanarak elde eder.</span><span class="sxs-lookup"><span data-stu-id="f8af8-113">To get all of this information, the code obtains its operation context using <xref:System.ServiceModel.OperationContext.Current%2A>.</span></span> <span data-ttu-id="f8af8-114">Ve <xref:System.ServiceModel.ServiceHost> <xref:System.ServiceModel.Description.ServiceDescription> nesnesi işlem bağlamından alınır.</span><span class="sxs-lookup"><span data-stu-id="f8af8-114">The <xref:System.ServiceModel.ServiceHost> and its <xref:System.ServiceModel.Description.ServiceDescription> object are retrieved from the operation context.</span></span> <span data-ttu-id="f8af8-115">Hizmetin temel uç noktalarını listelemek için, kod hizmet ana <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A> bilgisayar koleksiyonunu nitedin.</span><span class="sxs-lookup"><span data-stu-id="f8af8-115">To list the base endpoints for the service, the code iterates through the service host's <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A> collection.</span></span> <span data-ttu-id="f8af8-116">Hizmetin hizmet bitiş noktalarını listelemek için, kod hizmet açıklamasının uç noktaları koleksiyonunda yineler.</span><span class="sxs-lookup"><span data-stu-id="f8af8-116">To list the service endpoints for the service, the code iterates through the service description's endpoints collection.</span></span>  
  
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
  
 <span data-ttu-id="f8af8-117">Örneği çalıştırdığınızda, hesap makinesi işlemlerini ve ardından `GetServiceDescriptionInfo` işlem tarafından döndürülen hizmet bilgilerini görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="f8af8-117">When you run the sample, you see the calculator operations and then the service information returned by the `GetServiceDescriptionInfo` operation.</span></span> <span data-ttu-id="f8af8-118">İstemciyi kapatmak için istemci penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="f8af8-118">Press ENTER in the client window to shut down the client.</span></span>  
  
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
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="f8af8-119">Örneği ayarlamak, oluşturmak ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="f8af8-119">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="f8af8-120">Windows Communication Foundation [Samples için Tek Seferlik Kurulum Yordamı'nı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizi emin olun.</span><span class="sxs-lookup"><span data-stu-id="f8af8-120">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="f8af8-121">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak [için, Windows Communication Foundation Samples'i oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="f8af8-121">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="f8af8-122">Örneği tek veya çapraz makine yapılandırmasında çalıştırmak için, [Windows Communication Foundation Samples'ı çalıştıran](../../../../docs/framework/wcf/samples/running-the-samples.md)yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="f8af8-122">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="f8af8-123">Numuneler makinenize zaten yüklenmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="f8af8-123">The samples may already be installed on your machine.</span></span> <span data-ttu-id="f8af8-124">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="f8af8-124">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="f8af8-125">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="f8af8-125">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f8af8-126">Bu örnek aşağıdaki dizinde yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="f8af8-126">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\ServiceDescription`  
