---
title: Gövdeye göre Yönlendir
ms.date: 03/30/2017
ms.assetid: 07a6fc3b-c360-42e0-b663-3d0f22cf4502
ms.openlocfilehash: 4266068bb53e5ae90a05cc6537df2ab9b65b6b07
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965508"
---
# <a name="route-by-body"></a><span data-ttu-id="e2f14-102">Gövdeye göre Yönlendir</span><span class="sxs-lookup"><span data-stu-id="e2f14-102">Route by Body</span></span>
<span data-ttu-id="e2f14-103">Bu örnek, herhangi bir SOAP eylemiyle ileti nesnelerini kabul eden bir hizmetin nasıl uygulanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e2f14-103">This sample demonstrates how to implement a service that accepts message objects with any SOAP action.</span></span> <span data-ttu-id="e2f14-104">Bu örnek, bir Hesaplayıcı hizmeti uygulayan [kullanmaya](../../../../docs/framework/wcf/samples/getting-started-sample.md) Başlarken hizmetini temel alır.</span><span class="sxs-lookup"><span data-stu-id="e2f14-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span> <span data-ttu-id="e2f14-105">Hizmet, <xref:System.ServiceModel.Channels.Message> istek parametresini kabul `Calculate` eden ve bir <xref:System.ServiceModel.Channels.Message> yanıt döndüren tek bir işlem uygular.</span><span class="sxs-lookup"><span data-stu-id="e2f14-105">The service implements a single `Calculate` operation that accepts a <xref:System.ServiceModel.Channels.Message> request parameter and returns a <xref:System.ServiceModel.Channels.Message> response.</span></span>  
  
 <span data-ttu-id="e2f14-106">Bu örnekte, istemci bir konsol uygulaması (. exe) ve hizmet IIS 'de barındırılır.</span><span class="sxs-lookup"><span data-stu-id="e2f14-106">In this sample, the client is a console application (.exe) and the service is hosted in IIS.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e2f14-107">Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="e2f14-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="e2f14-108">Örnek, gövde içeriğine göre ileti gönderimi gösterir.</span><span class="sxs-lookup"><span data-stu-id="e2f14-108">The sample demonstrates message dispatch based on the body content.</span></span> <span data-ttu-id="e2f14-109">Yerleşik Windows Communication Foundation (WCF) hizmet modeli ileti gönderme mekanizması ileti eylemlerini temel alır.</span><span class="sxs-lookup"><span data-stu-id="e2f14-109">The built-in Windows Communication Foundation (WCF) service model message dispatch mechanism is based on message Actions.</span></span> <span data-ttu-id="e2f14-110">Ancak, eylem = "" ile tüm işlemlerini tanımlayan birçok mevcut Web hizmeti vardır.</span><span class="sxs-lookup"><span data-stu-id="e2f14-110">However, there are many existing Web services that define all of their operations with Action="".</span></span> <span data-ttu-id="e2f14-111">Eylem bilgilerine göre istek iletilerinin dağıtımını tutan WSDL 'yi temel alan bir hizmet derlemek olanaksızdır.</span><span class="sxs-lookup"><span data-stu-id="e2f14-111">It is impossible to build a service based on WSDL that keeps dispatching request messages based on Action information.</span></span> <span data-ttu-id="e2f14-112">Bu örnek, WSDL 'yi temel alan bir hizmet sözleşmesini gösterir (WSDL, örnekle birlikte gelen Service. wsdl ' de bulunur).</span><span class="sxs-lookup"><span data-stu-id="e2f14-112">This sample demonstrates a service contract that is based on WSDL (the WSDL is contained in Service.wsdl that is included with the sample).</span></span> <span data-ttu-id="e2f14-113">Hizmet sözleşmesinin, [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md)' de kullanılan bir hesap hesaplayıcısı.</span><span class="sxs-lookup"><span data-stu-id="e2f14-113">The service contract is Calculator, similar to the one used in [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span> <span data-ttu-id="e2f14-114">Ancak, `[OperationContract]` tüm `Action=""` işlemleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="e2f14-114">However the `[OperationContract]` specifies `Action=""` for all operations.</span></span>  
  
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
  
 <span data-ttu-id="e2f14-115">Bir sözleşme verildiğinde, bir hizmet, işlemler arasında iletilerin `DispatchByBodyBehavior` dağıtılması için özel dağıtım davranışı gerektirir.</span><span class="sxs-lookup"><span data-stu-id="e2f14-115">Given a contract, a service requires custom dispatch behavior `DispatchByBodyBehavior` to allow messages to be dispatched between operations.</span></span> <span data-ttu-id="e2f14-116">Bu dağıtım davranışı, özel `DispatchByBodyElementOperationSelector` işlem seçiciyi, ilgili sarmalayıcı öğelerinin QName tarafından anahtarlanan işlem adlarından oluşan bir tabloyla başlatır.</span><span class="sxs-lookup"><span data-stu-id="e2f14-116">This dispatch behavior initializes the `DispatchByBodyElementOperationSelector` custom operation selector with a table of the operation names keyed by QName of respective wrapper elements.</span></span> <span data-ttu-id="e2f14-117">`DispatchByBodyElementOperationSelector`, gövdenin ilk alt öğesinin başlangıç etiketine bakar ve daha önce bahsedilen tabloyu kullanarak işlemi seçer.</span><span class="sxs-lookup"><span data-stu-id="e2f14-117">`DispatchByBodyElementOperationSelector` looks at the start tag of the first child of the Body and selects the operation using the table previously mentioned.</span></span>  
  
 <span data-ttu-id="e2f14-118">İstemci, [ServiceModel meta veri yardımcı programı Aracı (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)kullanılarak hizmet tarafından DıŞARıYA aktarılmış WSDL 'den otomatik olarak oluşturulan bir proxy kullanır.</span><span class="sxs-lookup"><span data-stu-id="e2f14-118">The client uses a proxy auto-generated from the WSDL exported by the service using [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>  
  
```  
svcutil.exe  /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples /uxs http://localhost/servicemodelsamples/service.svc?wsdl /out:generatedProxy.cs  
```  
  
 <span data-ttu-id="e2f14-119">Tüm işlemlerin eylemlerinin boş olması, otomatik olarak oluşturulan ara sunucu 'daki eylem parametreleri dışında, istemci kodunda hiçbir etkiye sahip değildir.</span><span class="sxs-lookup"><span data-stu-id="e2f14-119">The fact that actions of all operations are empty has no impact on the client code, except for the Action parameters in the auto-generated proxy.</span></span>  
  
 <span data-ttu-id="e2f14-120">İstemci kodu birkaç hesaplama gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="e2f14-120">The client code performs several calculations.</span></span> <span data-ttu-id="e2f14-121">Örneği çalıştırdığınızda, işlem istekleri ve yanıtları istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="e2f14-121">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="e2f14-122">İstemcisini kapatmak için istemci penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="e2f14-122">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Add(100, 15.99) = 115.99  
Subtract(145, 76.54) = 68.46  
Multiply(9, 81.25) = 731.25  
Divide(22, 7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="e2f14-123">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="e2f14-123">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="e2f14-124">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="e2f14-124">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="e2f14-125">Çözümü derlemek için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="e2f14-125">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="e2f14-126">Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="e2f14-126">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="e2f14-127">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="e2f14-127">The samples may already be installed on your machine.</span></span> <span data-ttu-id="e2f14-128">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="e2f14-128">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="e2f14-129">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ' e gidin.</span><span class="sxs-lookup"><span data-stu-id="e2f14-129">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e2f14-130">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="e2f14-130">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Interop\RouteByBody`  
