---
title: Satır İçi Kod Kullanarak IIS Barındırma
ms.date: 03/30/2017
helpviewer_keywords:
- Web hosted service
- IIS Hosting Using Inline Code Sample [Windows Communication Foundation]
ms.assetid: 56fe3687-a34b-4661-8e30-b33770f413fa
ms.openlocfilehash: 30e50d39b0edb34bcda1bec6d1848a09eabd34fa
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43524943"
---
# <a name="iis-hosting-using-inline-code"></a><span data-ttu-id="0f1b5-102">Satır İçi Kod Kullanarak IIS Barındırma</span><span class="sxs-lookup"><span data-stu-id="0f1b5-102">IIS Hosting Using Inline Code</span></span>
<span data-ttu-id="0f1b5-103">Bu örnek, Internet Information Services (IIS) tarafından barındırılan bir hizmet ekleme işlemi gösterilmektedir hizmet kodu bulunduğu satır içi .svc dosyasında ve isteğe bağlı olarak derlenir.</span><span class="sxs-lookup"><span data-stu-id="0f1b5-103">This sample demonstrates how to implement a service hosted by Internet Information Services (IIS), where the service code is contained in-line in a .svc file and is compiled on demand.</span></span> <span data-ttu-id="0f1b5-104">Hizmet kodu, uygulamanın \App_Code dizininde veya derlemesini \bin içinde dağıtılan derlenmiş doğrudan kaynak kodu dosyalarında de uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="0f1b5-104">Service code can also be implemented directly in source code files located in the application's \App_Code directory, or compiled into assembly deployed in \bin.</span></span> <span data-ttu-id="0f1b5-105">Bu örnek, bu teknikler göstermemiz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="0f1b5-105">This sample does not demonstrate these techniques.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0f1b5-106">Bu örnek için Kurulum yordamı ve derleme yönergeleri Bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="0f1b5-106">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="0f1b5-107">Örnekler, bilgisayarınızda yüklü.</span><span class="sxs-lookup"><span data-stu-id="0f1b5-107">The samples may already be installed on your computer.</span></span> <span data-ttu-id="0f1b5-108">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="0f1b5-108">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="0f1b5-109">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="0f1b5-109">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="0f1b5-110">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="0f1b5-110">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WebHost\InlineCode`  
  
 <span data-ttu-id="0f1b5-111">Örnek, bir istek-yanıt iletişim deseni tanımlayan bir sözleşme uygulayan normal bir hizmette gösterir.</span><span class="sxs-lookup"><span data-stu-id="0f1b5-111">The sample demonstrates a typical service that implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="0f1b5-112">IIS'de barındırılan hizmet ve hizmet kod tamamen Service.svc dosyasında yer alır.</span><span class="sxs-lookup"><span data-stu-id="0f1b5-112">The service is hosted in IIS and the service code is entirely contained in the Service.svc file.</span></span> <span data-ttu-id="0f1b5-113">Hizmet ana bilgisayarı-etkinleştirilir ve isteğe bağlı hizmetine gönderilen ilk ileti tarafından derlenmiş.</span><span class="sxs-lookup"><span data-stu-id="0f1b5-113">The service is host-activated and compiled on-demand by the first message sent to the service.</span></span> <span data-ttu-id="0f1b5-114">Hiçbir ön derleme gerekli yoktur.</span><span class="sxs-lookup"><span data-stu-id="0f1b5-114">There is no pre-compilation necessary.</span></span> <span data-ttu-id="0f1b5-115">Hizmet uygulayan bir `ICalculator` aşağıdaki kodda tanımlanan Sözleşme:</span><span class="sxs-lookup"><span data-stu-id="0f1b5-115">The service implements an `ICalculator` contract as defined in the following code:</span></span>  
  
```  
// Define a service contract.  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
    public interface ICalculator  
{  
    [OperationContract]  
    double Add(double n1, double n2);  
    [OperationContract]  
    double Subtract(double n1, double n2);  
    [OperationContract]  
    double Multiply(double n1, double n2);  
    [OperationContract]  
    double Divide(double n1, double n2);  
}  
```  
  
 <span data-ttu-id="0f1b5-116">Hizmet uygulaması, hesaplar ve uygun sonucunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="0f1b5-116">The service implementation calculates and returns the appropriate result.</span></span>  
  
```  
<%@ServiceHost language=c# Debug="true" Service="Microsoft.ServiceModel.Samples.CalculatorService" %>   
…  
// Service class that implements the service contract.  
public class CalculatorService : ICalculator  
{  
    public double Add(double n1, double n2)  
    {  
        return n1 + n2;  
    }  
    public double Subtract(double n1, double n2)  
    {  
        return n1 - n2;  
    }  
    public double Multiply(double n1, double n2)  
    {  
        return n1 * n2;  
    }  
    public double Divide(double n1, double n2)  
    {  
        return n1 / n2;  
    }  
}  
```  
  
 <span data-ttu-id="0f1b5-117">Örneği çalıştırdığınızda, işlem isteklerini ve yanıtlarını istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="0f1b5-117">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="0f1b5-118">İstemci bilgisayarı için istemci penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="0f1b5-118">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="0f1b5-119">Ayarlamak için derleme ve örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="0f1b5-119">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="0f1b5-120">Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="0f1b5-120">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="0f1b5-121">Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="0f1b5-121">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="0f1b5-122">Çözüm oluşturulduktan sonra ServiceModelSamples uygulamada ayarlamak için setup.bat çalıştırma [!INCLUDE[iisver](../../../../includes/iisver-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0f1b5-122">After the solution has been built, run setup.bat to set up the ServiceModelSamples Application in [!INCLUDE[iisver](../../../../includes/iisver-md.md)].</span></span> <span data-ttu-id="0f1b5-123">ServiceModelSamples dizin artık olarak görünmesi gereken bir [!INCLUDE[iisver](../../../../includes/iisver-md.md)] uygulama.</span><span class="sxs-lookup"><span data-stu-id="0f1b5-123">The ServiceModelSamples directory should now appear as an [!INCLUDE[iisver](../../../../includes/iisver-md.md)] Application.</span></span>  
  
4.  <span data-ttu-id="0f1b5-124">Tek veya çoklu bilgisayar yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="0f1b5-124">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span> <span data-ttu-id="0f1b5-125">Bu hizmeti çağıran bir istemci uygulaması oluşturma hakkında bir örnek için bkz. [nasıl yapılır: istemci oluşturma](../../../../docs/framework/wcf/how-to-create-a-wcf-client.md).</span><span class="sxs-lookup"><span data-stu-id="0f1b5-125">For an example on how to create a client application that can call this service, see [How to: Create a Client](../../../../docs/framework/wcf/how-to-create-a-wcf-client.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f1b5-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0f1b5-126">See Also</span></span>  
 [<span data-ttu-id="0f1b5-127">AppFabric barındırma ve Kalıcılık örnekleri</span><span class="sxs-lookup"><span data-stu-id="0f1b5-127">AppFabric Hosting and Persistence Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=193961)
