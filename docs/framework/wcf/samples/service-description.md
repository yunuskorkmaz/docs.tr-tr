---
title: Hizmet Açıklaması
ms.date: 03/30/2017
ms.assetid: 7034b5d6-d608-45f3-b57d-ec135f83ff24
ms.openlocfilehash: d86a6a78995042f0c6a45cf6e40e31c3e515e8eb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33504217"
---
# <a name="service-description"></a><span data-ttu-id="388bb-102">Hizmet Açıklaması</span><span class="sxs-lookup"><span data-stu-id="388bb-102">Service Description</span></span>
<span data-ttu-id="388bb-103">Hizmet açıklaması örnek, bir hizmet çalışma zamanında hizmet açıklaması bilgilerini nasıl alabileceğiniz gösterilir.</span><span class="sxs-lookup"><span data-stu-id="388bb-103">The Service Description sample demonstrates how a service can retrieve its service description information at runtime.</span></span> <span data-ttu-id="388bb-104">Örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md), hizmeti hakkında tanımlayıcı bilgileri döndürmek için tanımlanmış bir ek hizmet işlemi.</span><span class="sxs-lookup"><span data-stu-id="388bb-104">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), with an additional service operation defined to return descriptive information about the service.</span></span> <span data-ttu-id="388bb-105">Döndürülen bilgi hizmeti için uç noktalar ve temel adresler listeler.</span><span class="sxs-lookup"><span data-stu-id="388bb-105">The information that is returned lists the base addresses and endpoints for the service.</span></span> <span data-ttu-id="388bb-106">Bu bilgileri kullanarak hizmeti sağlayan <xref:System.ServiceModel.OperationContext>, <xref:System.ServiceModel.ServiceHost>, ve <xref:System.ServiceModel.Description.ServiceDescription> sınıfları.</span><span class="sxs-lookup"><span data-stu-id="388bb-106">The service provides this information using the <xref:System.ServiceModel.OperationContext>, <xref:System.ServiceModel.ServiceHost>, and <xref:System.ServiceModel.Description.ServiceDescription> classes.</span></span>  
  
 <span data-ttu-id="388bb-107">Bu örnekte, istemci bir konsol uygulaması (.exe) ve Internet Information Services (IIS) tarafından barındırılan hizmetindeki.</span><span class="sxs-lookup"><span data-stu-id="388bb-107">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="388bb-108">Kurulum yordamı ve yapı yönergeleri Bu örnek için bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="388bb-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="388bb-109">Bu örnek hesaplayıcı sözleşmenin adlı değiştirilmiş bir sürümünü sahip `IServiceDescriptionCalculator`.</span><span class="sxs-lookup"><span data-stu-id="388bb-109">This sample has a modified version of the calculator contract called `IServiceDescriptionCalculator`.</span></span> <span data-ttu-id="388bb-110">Adlı bir ek hizmet işlemi sözleşmesini tanımlayan `GetServiceDescriptionInfo` taban adresi veya adresleri ve hizmet uç noktası veya hizmeti için uç nokta tanımlayan istemciye çok satırlı dize getirir.</span><span class="sxs-lookup"><span data-stu-id="388bb-110">The contract defines an additional service operation named `GetServiceDescriptionInfo` that returns a multi-line string to the client that describes the base address or addresses and service endpoint or endpoints for the service.</span></span>  
  
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
  
 <span data-ttu-id="388bb-111">Uygulama kodunu `GetServiceDescriptionInfo` kullanan <xref:System.ServiceModel.Description.ServiceDescription> hizmet uç noktalarına listelemek için.</span><span class="sxs-lookup"><span data-stu-id="388bb-111">The implementation code for `GetServiceDescriptionInfo` uses the <xref:System.ServiceModel.Description.ServiceDescription> to list the service endpoints.</span></span> <span data-ttu-id="388bb-112">Hizmet uç noktaları göreli adresleri olabileceği için önce hizmeti için temel adreslerini listeler.</span><span class="sxs-lookup"><span data-stu-id="388bb-112">Because service endpoints can have relative addresses, it first lists the base addresses for the service.</span></span> <span data-ttu-id="388bb-113">Tüm bu bilgileri almak için işlem bağlamını kullanarak kod edinir <xref:System.ServiceModel.OperationContext.Current%2A>.</span><span class="sxs-lookup"><span data-stu-id="388bb-113">To get all of this information, the code obtains its operation context using <xref:System.ServiceModel.OperationContext.Current%2A>.</span></span> <span data-ttu-id="388bb-114"><xref:System.ServiceModel.ServiceHost> Ve kendi <xref:System.ServiceModel.Description.ServiceDescription> nesne işlemi bağlamdan alınır.</span><span class="sxs-lookup"><span data-stu-id="388bb-114">The <xref:System.ServiceModel.ServiceHost> and its <xref:System.ServiceModel.Description.ServiceDescription> object are retrieved from the operation context.</span></span> <span data-ttu-id="388bb-115">Hizmet için taban uç noktaları listelemek için hizmet konağın kodu tekrarlanan <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A> koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="388bb-115">To list the base endpoints for the service, the code iterates through the service host's <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A> collection.</span></span> <span data-ttu-id="388bb-116">Hizmeti için hizmet uç noktalarına listelemek için kod hizmet açıklaması 's uç noktaları toplulukta tekrarlanan.</span><span class="sxs-lookup"><span data-stu-id="388bb-116">To list the service endpoints for the service, the code iterates through the service description's endpoints collection.</span></span>  
  
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
  
 <span data-ttu-id="388bb-117">Hesaplayıcı işlemler'i ve ardından tarafından döndürülen hizmet bilgileri örneği çalıştırdığınızda, gördüğünüz `GetServiceDescriptionInfo` işlemi.</span><span class="sxs-lookup"><span data-stu-id="388bb-117">When you run the sample, you see the calculator operations and then the service information returned by the `GetServiceDescriptionInfo` operation.</span></span> <span data-ttu-id="388bb-118">İstemcisi penceresinde istemciyi aşağı kapatmak için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="388bb-118">Press ENTER in the client window to shut down the client.</span></span>  
  
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
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="388bb-119">Ayarlamak için derleme ve örnek çalıştırın</span><span class="sxs-lookup"><span data-stu-id="388bb-119">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="388bb-120">Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="388bb-120">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="388bb-121">Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="388bb-121">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="388bb-122">Tek veya çapraz makine yapılandırmada örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="388bb-122">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="388bb-123">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="388bb-123">The samples may already be installed on your machine.</span></span> <span data-ttu-id="388bb-124">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="388bb-124">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="388bb-125">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="388bb-125">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="388bb-126">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="388bb-126">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\ServiceDescription`  
  
## <a name="see-also"></a><span data-ttu-id="388bb-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="388bb-127">See Also</span></span>
