---
title: Gövdeye göre Yönlendir
ms.date: 03/30/2017
ms.assetid: 07a6fc3b-c360-42e0-b663-3d0f22cf4502
ms.openlocfilehash: a7fc6eb142b091a25bb1dd182cf43e006c187a96
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54633995"
---
# <a name="route-by-body"></a><span data-ttu-id="a6b59-102">Gövdeye göre Yönlendir</span><span class="sxs-lookup"><span data-stu-id="a6b59-102">Route by Body</span></span>
<span data-ttu-id="a6b59-103">Bu örnek nasıl herhangi bir SOAP eylemi ileti nesneleri kabul eden bir hizmet uygulanacağı gösterir.</span><span class="sxs-lookup"><span data-stu-id="a6b59-103">This sample demonstrates how to implement a service that accepts message objects with any SOAP action.</span></span> <span data-ttu-id="a6b59-104">Bu örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md) hesaplayıcı hizmet uygulayan.</span><span class="sxs-lookup"><span data-stu-id="a6b59-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span> <span data-ttu-id="a6b59-105">Tek bir hizmeti uygulayan `Calculate` kabul eden bir işlem bir <xref:System.ServiceModel.Channels.Message> istek parametresi ve döndürür bir <xref:System.ServiceModel.Channels.Message> yanıt.</span><span class="sxs-lookup"><span data-stu-id="a6b59-105">The service implements a single `Calculate` operation that accepts a <xref:System.ServiceModel.Channels.Message> request parameter and returns a <xref:System.ServiceModel.Channels.Message> response.</span></span>  
  
 <span data-ttu-id="a6b59-106">Bu örnekte, istemci bir konsol uygulaması (.exe) ve hizmet IIS'de barındırılan.</span><span class="sxs-lookup"><span data-stu-id="a6b59-106">In this sample, the client is a console application (.exe) and the service is hosted in IIS.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a6b59-107">Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="a6b59-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="a6b59-108">Örnek ileti gönderme gövdesi içeriğine göre gösterir.</span><span class="sxs-lookup"><span data-stu-id="a6b59-108">The sample demonstrates message dispatch based on the body content.</span></span> <span data-ttu-id="a6b59-109">Yerleşik Windows Communication Foundation (WCF) hizmet modeli ileti gönderme mekanizması eylemleri iletide temel alır.</span><span class="sxs-lookup"><span data-stu-id="a6b59-109">The built-in Windows Communication Foundation (WCF) service model message dispatch mechanism is based on message Actions.</span></span> <span data-ttu-id="a6b59-110">Ancak, tüm eylem işlemlerini tanımlayan birçok mevcut Web hizmeti vardır = "".</span><span class="sxs-lookup"><span data-stu-id="a6b59-110">However, there are many existing Web services that define all of their operations with Action="".</span></span> <span data-ttu-id="a6b59-111">Eylem bilgi iletileri alan isteği gönderme tutar WSDL dayalı bir hizmet oluşturmak mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="a6b59-111">It is impossible to build a service based on WSDL that keeps dispatching request messages based on Action information.</span></span> <span data-ttu-id="a6b59-112">Bu örnek, WSDL (WSDL örnek ile birlikte sağlanan. Service.wsdl bulunur) temel alan bir hizmet sözleşmesini gösterir.</span><span class="sxs-lookup"><span data-stu-id="a6b59-112">This sample demonstrates a service contract that is based on WSDL (the WSDL is contained in Service.wsdl that is included with the sample).</span></span> <span data-ttu-id="a6b59-113">Hizmet sözleşmesi hesaplayıcı kullanılanla benzer olan [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="a6b59-113">The service contract is Calculator, similar to the one used in [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span> <span data-ttu-id="a6b59-114">Ancak `[OperationContract]` belirtir `Action=""` tüm işlemler için.</span><span class="sxs-lookup"><span data-stu-id="a6b59-114">However the `[OperationContract]` specifies `Action=""` for all operations.</span></span>  
  
```  
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples"),    
                 XmlSerializerFormat, DispatchByBodyBehavior]  
    public interface ICalculator  
    {  
        [OperationContract(Action="")]  
        double Add(double n1, double n2);  
        [OperationContract(Action = "")]  
        double Subtract(double n1, double n2);  
        [OperationContract(Action = "")]  
        double Multiply(double n1, double n2);  
        [OperationContract(Action = "")]  
        double Divide(double n1, double n2);  
    }  
```  
  
 <span data-ttu-id="a6b59-115">Bir sözleşme göz önünde bulundurulduğunda, bir hizmetin özel gönderme davranışı gerektirir `DispatchByBodyBehavior` işlemleri arasında dağıtılması iletilere izin verecek şekilde.</span><span class="sxs-lookup"><span data-stu-id="a6b59-115">Given a contract, a service requires custom dispatch behavior `DispatchByBodyBehavior` to allow messages to be dispatched between operations.</span></span> <span data-ttu-id="a6b59-116">Bu dağıtım davranışı başlatır `DispatchByBodyElementOperationSelector` işlem adları ilgili sarmalayıcı öğe bir QName tarafından Anahtarlanan bir tablo ile özel işlem Seçici.</span><span class="sxs-lookup"><span data-stu-id="a6b59-116">This dispatch behavior initializes the `DispatchByBodyElementOperationSelector` custom operation selector with a table of the operation names keyed by QName of respective wrapper elements.</span></span> <span data-ttu-id="a6b59-117">`DispatchByBodyElementOperationSelector` Gövde ilk alt öğenin başlangıç etiketi olarak görünür ve daha önce bahsedilen tabloyu kullanarak işlemi seçer.</span><span class="sxs-lookup"><span data-stu-id="a6b59-117">`DispatchByBodyElementOperationSelector` looks at the start tag of the first child of the Body and selects the operation using the table previously mentioned.</span></span>  
  
 <span data-ttu-id="a6b59-118">İstemci hizmetini kullanarak dışarı WSDL gelen otomatik üretilmiş bir proxy kullanır [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="a6b59-118">The client uses a proxy auto-generated from the WSDL exported by the service using [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>  
  
```  
svcutil.exe  /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples /uxs http://localhost/servicemodelsamples/service.svc?wsdl /out:generatedProxy.cs  
```  
  
 <span data-ttu-id="a6b59-119">Tüm işlemlerin Eylemler boş olması, istemci kodu eylem parametrelerini otomatik olarak oluşturulan proxy'sinde dışında herhangi bir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="a6b59-119">The fact that actions of all operations are empty has no impact on the client code, except for the Action parameters in the auto-generated proxy.</span></span>  
  
 <span data-ttu-id="a6b59-120">İstemci kodu birkaç hesaplamalar gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="a6b59-120">The client code performs several calculations.</span></span> <span data-ttu-id="a6b59-121">Örneği çalıştırdığınızda, işlem isteklerini ve yanıtlarını istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="a6b59-121">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="a6b59-122">İstemci bilgisayarı için istemci penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="a6b59-122">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Add(100, 15.99) = 115.99  
Subtract(145, 76.54) = 68.46  
Multiply(9, 81.25) = 731.25  
Divide(22, 7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="a6b59-123">Ayarlamak için derleme ve örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="a6b59-123">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="a6b59-124">Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a6b59-124">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="a6b59-125">Çözümü derlemek için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a6b59-125">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="a6b59-126">Tek veya çapraz makine yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a6b59-126">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a6b59-127">Örnekler, makinenizde zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="a6b59-127">The samples may already be installed on your machine.</span></span> <span data-ttu-id="a6b59-128">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="a6b59-128">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="a6b59-129">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="a6b59-129">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a6b59-130">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="a6b59-130">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Interop\RouteByBody`  
  
## <a name="see-also"></a><span data-ttu-id="a6b59-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a6b59-131">See also</span></span>
