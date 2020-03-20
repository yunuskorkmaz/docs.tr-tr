---
title: Gövdeye göre Yönlendir
ms.date: 03/30/2017
ms.assetid: 07a6fc3b-c360-42e0-b663-3d0f22cf4502
ms.openlocfilehash: c3f4b19e646a6a9716d2264a3969b339208c60a1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144194"
---
# <a name="route-by-body"></a><span data-ttu-id="40c31-102">Gövdeye göre Yönlendir</span><span class="sxs-lookup"><span data-stu-id="40c31-102">Route by Body</span></span>
<span data-ttu-id="40c31-103">Bu örnek, herhangi bir SOAP eylemi ile ileti nesneleri kabul eden bir hizmetin nasıl uygulanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="40c31-103">This sample demonstrates how to implement a service that accepts message objects with any SOAP action.</span></span> <span data-ttu-id="40c31-104">Bu örnek, bir hesap makinesi hizmeti uygulayan [Başlarken'e](../../../../docs/framework/wcf/samples/getting-started-sample.md) dayanır.</span><span class="sxs-lookup"><span data-stu-id="40c31-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span> <span data-ttu-id="40c31-105">Hizmet, istek `Calculate` <xref:System.ServiceModel.Channels.Message> parametresini kabul eden ve yanıt <xref:System.ServiceModel.Channels.Message> döndüren tek bir işlem uygular.</span><span class="sxs-lookup"><span data-stu-id="40c31-105">The service implements a single `Calculate` operation that accepts a <xref:System.ServiceModel.Channels.Message> request parameter and returns a <xref:System.ServiceModel.Channels.Message> response.</span></span>  
  
 <span data-ttu-id="40c31-106">Bu örnekte, istemci bir konsol uygulamasıdır (.exe) ve hizmet IIS'de barındırılır.</span><span class="sxs-lookup"><span data-stu-id="40c31-106">In this sample, the client is a console application (.exe) and the service is hosted in IIS.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="40c31-107">Bu örnek için kurulum yordamı ve yapı yönergeleri bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="40c31-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="40c31-108">Örnek, gövde içeriğine dayalı ileti göndermeyi gösterir.</span><span class="sxs-lookup"><span data-stu-id="40c31-108">The sample demonstrates message dispatch based on the body content.</span></span> <span data-ttu-id="40c31-109">Yerleşik Windows Communication Foundation (WCF) hizmet modeli ileti gönderme mekanizması ileti Eylemleri'ni temel alır.</span><span class="sxs-lookup"><span data-stu-id="40c31-109">The built-in Windows Communication Foundation (WCF) service model message dispatch mechanism is based on message Actions.</span></span> <span data-ttu-id="40c31-110">Ancak, tüm işlemlerini Action="" ile tanımlayan birçok varolan Web hizmeti vardır.</span><span class="sxs-lookup"><span data-stu-id="40c31-110">However, there are many existing Web services that define all of their operations with Action="".</span></span> <span data-ttu-id="40c31-111">Eylem bilgilerine dayalı istek iletileri göndermeye devam eden WSDL tabanlı bir hizmet oluşturmak mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="40c31-111">It is impossible to build a service based on WSDL that keeps dispatching request messages based on Action information.</span></span> <span data-ttu-id="40c31-112">Bu örnek, WSDL'yi temel alan bir hizmet sözleşmesi gösterir (WSDL, örnekle birlikte service.wsdl'de bulunur).</span><span class="sxs-lookup"><span data-stu-id="40c31-112">This sample demonstrates a service contract that is based on WSDL (the WSDL is contained in Service.wsdl that is included with the sample).</span></span> <span data-ttu-id="40c31-113">Hizmet sözleşmesi, [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md)kullanılana benzer olan Hesap Makinesi'dir.</span><span class="sxs-lookup"><span data-stu-id="40c31-113">The service contract is Calculator, similar to the one used in [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span> <span data-ttu-id="40c31-114">Ancak `[OperationContract]` tüm işlemler `Action=""` için belirtir.</span><span class="sxs-lookup"><span data-stu-id="40c31-114">However the `[OperationContract]` specifies `Action=""` for all operations.</span></span>  
  
```csharp  
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
  
 <span data-ttu-id="40c31-115">Bir sözleşme göz önüne alındığında, `DispatchByBodyBehavior` bir hizmet iletilerin işlemler arasında gönderilmesine izin vermek için özel gönderme davranışı gerektirir.</span><span class="sxs-lookup"><span data-stu-id="40c31-115">Given a contract, a service requires custom dispatch behavior `DispatchByBodyBehavior` to allow messages to be dispatched between operations.</span></span> <span data-ttu-id="40c31-116">Bu gönderme davranışı, `DispatchByBodyElementOperationSelector` ilgili sarıcı öğelerinin QName tarafından anahtarlanmış işlem adlarının bir tablosuyla özel işlem seçicisini devreye ait hale sağlar.</span><span class="sxs-lookup"><span data-stu-id="40c31-116">This dispatch behavior initializes the `DispatchByBodyElementOperationSelector` custom operation selector with a table of the operation names keyed by QName of respective wrapper elements.</span></span> <span data-ttu-id="40c31-117">`DispatchByBodyElementOperationSelector`Gövdenin ilk çocuğunun başlangıç etiketine bakar ve daha önce bahsedilen tabloyu kullanarak işlemi seçer.</span><span class="sxs-lookup"><span data-stu-id="40c31-117">`DispatchByBodyElementOperationSelector` looks at the start tag of the first child of the Body and selects the operation using the table previously mentioned.</span></span>  
  
 <span data-ttu-id="40c31-118">İstemci [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)kullanarak hizmet tarafından dışa aktarılan WSDL'den otomatik olarak oluşturulan bir proxy kullanır.</span><span class="sxs-lookup"><span data-stu-id="40c31-118">The client uses a proxy auto-generated from the WSDL exported by the service using [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>  
  
```console  
svcutil.exe  /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples /uxs http://localhost/servicemodelsamples/service.svc?wsdl /out:generatedProxy.cs  
```  
  
 <span data-ttu-id="40c31-119">Otomatik oluşturulan proxy'deki Eylem parametreleri dışında, tüm işlemlerin eylemlerinin boş olması istemci kodu üzerinde hiçbir etkiye sahip değildir.</span><span class="sxs-lookup"><span data-stu-id="40c31-119">The fact that actions of all operations are empty has no impact on the client code, except for the Action parameters in the auto-generated proxy.</span></span>  
  
 <span data-ttu-id="40c31-120">İstemci kodu çeşitli hesaplamalar gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="40c31-120">The client code performs several calculations.</span></span> <span data-ttu-id="40c31-121">Örneği çalıştırdığınızda, işlem istekleri ve yanıtları istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="40c31-121">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="40c31-122">İstemciyi kapatmak için istemci penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="40c31-122">Press ENTER in the client window to shut down the client.</span></span>  
  
```console
Add(100, 15.99) = 115.99  
Subtract(145, 76.54) = 68.46  
Multiply(9, 81.25) = 731.25  
Divide(22, 7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="40c31-123">Örneği ayarlamak, oluşturmak ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="40c31-123">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="40c31-124">Windows Communication Foundation [Samples için Tek Seferlik Kurulum Yordamı'nı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizi emin olun.</span><span class="sxs-lookup"><span data-stu-id="40c31-124">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="40c31-125">Çözümü oluşturmak için, Windows [Communication Foundation Samples'i oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="40c31-125">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="40c31-126">Örneği tek veya çapraz makine yapılandırmasında çalıştırmak için, [Windows Communication Foundation Samples'ı çalıştıran](../../../../docs/framework/wcf/samples/running-the-samples.md)yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="40c31-126">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="40c31-127">Numuneler makinenize zaten yüklenmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="40c31-127">The samples may already be installed on your machine.</span></span> <span data-ttu-id="40c31-128">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="40c31-128">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="40c31-129">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="40c31-129">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="40c31-130">Bu örnek aşağıdaki dizinde yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="40c31-130">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Interop\RouteByBody`  
