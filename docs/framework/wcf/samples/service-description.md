---
title: Hizmet Açıklaması
ms.date: 03/30/2017
ms.assetid: 7034b5d6-d608-45f3-b57d-ec135f83ff24
ms.openlocfilehash: 467d8437ec6b3383974b1faf2a96aacb1524771a
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596584"
---
# <a name="service-description"></a><span data-ttu-id="94d01-102">Hizmet Açıklaması</span><span class="sxs-lookup"><span data-stu-id="94d01-102">Service Description</span></span>
<span data-ttu-id="94d01-103">Hizmet açıklaması örneği, bir hizmetin çalışma zamanında hizmet açıklaması bilgilerini nasıl alabileceğinizi gösterir.</span><span class="sxs-lookup"><span data-stu-id="94d01-103">The Service Description sample demonstrates how a service can retrieve its service description information at runtime.</span></span> <span data-ttu-id="94d01-104">Örnek, hizmet hakkında açıklayıcı bilgiler döndürmek için tanımlanmış ek bir hizmet işlemi ile [Başlarken](getting-started-sample.md)' i temel alır.</span><span class="sxs-lookup"><span data-stu-id="94d01-104">The sample is based on the [Getting Started](getting-started-sample.md), with an additional service operation defined to return descriptive information about the service.</span></span> <span data-ttu-id="94d01-105">Döndürülen bilgiler, hizmetin temel adreslerini ve uç noktalarını listeler.</span><span class="sxs-lookup"><span data-stu-id="94d01-105">The information that is returned lists the base addresses and endpoints for the service.</span></span> <span data-ttu-id="94d01-106">Hizmet,, ve sınıflarını kullanarak bu bilgileri sağlar <xref:System.ServiceModel.OperationContext> <xref:System.ServiceModel.ServiceHost> <xref:System.ServiceModel.Description.ServiceDescription> .</span><span class="sxs-lookup"><span data-stu-id="94d01-106">The service provides this information using the <xref:System.ServiceModel.OperationContext>, <xref:System.ServiceModel.ServiceHost>, and <xref:System.ServiceModel.Description.ServiceDescription> classes.</span></span>  
  
 <span data-ttu-id="94d01-107">Bu örnekte, istemci bir konsol uygulaması (. exe) ve hizmet Internet Information Services (IIS) tarafından barındırılır.</span><span class="sxs-lookup"><span data-stu-id="94d01-107">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="94d01-108">Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="94d01-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="94d01-109">Bu örnek, adlı Hesaplayıcı sözleşmesinin değiştirilmiş bir sürümüne sahiptir `IServiceDescriptionCalculator` .</span><span class="sxs-lookup"><span data-stu-id="94d01-109">This sample has a modified version of the calculator contract called `IServiceDescriptionCalculator`.</span></span> <span data-ttu-id="94d01-110">Sözleşme, `GetServiceDescriptionInfo` istemciye yönelik temel adresi veya adresleri, hizmet uç noktasını veya bitiş noktalarını tanımlayan, istemciye çok satırlı bir dize döndüren adlı ek bir hizmet işlemi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="94d01-110">The contract defines an additional service operation named `GetServiceDescriptionInfo` that returns a multi-line string to the client that describes the base address or addresses and service endpoint or endpoints for the service.</span></span>  
  
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
  
 <span data-ttu-id="94d01-111">İçin uygulama kodu, `GetServiceDescriptionInfo` <xref:System.ServiceModel.Description.ServiceDescription> hizmet uç noktalarını listelemek için öğesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="94d01-111">The implementation code for `GetServiceDescriptionInfo` uses the <xref:System.ServiceModel.Description.ServiceDescription> to list the service endpoints.</span></span> <span data-ttu-id="94d01-112">Hizmet uç noktalarında göreli adresler olabileceğinden, önce hizmetin temel adreslerini listeler.</span><span class="sxs-lookup"><span data-stu-id="94d01-112">Because service endpoints can have relative addresses, it first lists the base addresses for the service.</span></span> <span data-ttu-id="94d01-113">Bu bilgilerin tümünü almak için kod, kullanarak işlem bağlamını edinir <xref:System.ServiceModel.OperationContext.Current%2A> .</span><span class="sxs-lookup"><span data-stu-id="94d01-113">To get all of this information, the code obtains its operation context using <xref:System.ServiceModel.OperationContext.Current%2A>.</span></span> <span data-ttu-id="94d01-114"><xref:System.ServiceModel.ServiceHost>Ve nesnesi, <xref:System.ServiceModel.Description.ServiceDescription> işlem bağlamından alınır.</span><span class="sxs-lookup"><span data-stu-id="94d01-114">The <xref:System.ServiceModel.ServiceHost> and its <xref:System.ServiceModel.Description.ServiceDescription> object are retrieved from the operation context.</span></span> <span data-ttu-id="94d01-115">Hizmetin temel uç noktalarını listelemek için, kod hizmet ana bilgisayarının koleksiyonu üzerinden yinelenir <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A> .</span><span class="sxs-lookup"><span data-stu-id="94d01-115">To list the base endpoints for the service, the code iterates through the service host's <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A> collection.</span></span> <span data-ttu-id="94d01-116">Hizmetin hizmet uç noktalarını listelemek için, kod hizmet açıklamasının uç noktalar koleksiyonu üzerinden yinelenir.</span><span class="sxs-lookup"><span data-stu-id="94d01-116">To list the service endpoints for the service, the code iterates through the service description's endpoints collection.</span></span>  
  
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
  
 <span data-ttu-id="94d01-117">Örneği çalıştırdığınızda, hesap makinesi işlemlerini ve sonra işlemin döndürdüğü hizmet bilgilerini görürsünüz `GetServiceDescriptionInfo` .</span><span class="sxs-lookup"><span data-stu-id="94d01-117">When you run the sample, you see the calculator operations and then the service information returned by the `GetServiceDescriptionInfo` operation.</span></span> <span data-ttu-id="94d01-118">İstemcisini kapatmak için istemci penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="94d01-118">Press ENTER in the client window to shut down the client.</span></span>  
  
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
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="94d01-119">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="94d01-119">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="94d01-120">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="94d01-120">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="94d01-121">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)konusundaki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="94d01-121">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="94d01-122">Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="94d01-122">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="94d01-123">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="94d01-123">The samples may already be installed on your machine.</span></span> <span data-ttu-id="94d01-124">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="94d01-124">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="94d01-125">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="94d01-125">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="94d01-126">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="94d01-126">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\ServiceDescription`  
