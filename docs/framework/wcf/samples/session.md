---
title: Oturum
ms.date: 03/30/2017
helpviewer_keywords:
- Sessions
ms.assetid: 36e1db50-008c-4b32-8d09-b56e790b8417
ms.openlocfilehash: 84f0cc34e5de0634eff2edecead08aae3a143068
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54554172"
---
# <a name="session"></a><span data-ttu-id="ea4a2-102">Oturum</span><span class="sxs-lookup"><span data-stu-id="ea4a2-102">Session</span></span>
<span data-ttu-id="ea4a2-103">Oturum örnek bir oturum gerektiren bir sözleşmesini uygulama gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="ea4a2-103">The Session sample demonstrates how to implement a contract that requires a session.</span></span> <span data-ttu-id="ea4a2-104">Oturum, birden çok işlemi gerçekleştirmek için bağlam sağlar.</span><span class="sxs-lookup"><span data-stu-id="ea4a2-104">A session provides context for performing multiple operations.</span></span> <span data-ttu-id="ea4a2-105">Önceki bir işlemin durumunu sonraki işlemleri kullanabilir bu durum belirli bir oturum ile ilişkilendirmek bir hizmet sağlar.</span><span class="sxs-lookup"><span data-stu-id="ea4a2-105">This allows a service to associate state with a given session, such that subsequent operations can use the state of a previous operation.</span></span> <span data-ttu-id="ea4a2-106">Bu örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md), hesaplayıcı hizmet uygular.</span><span class="sxs-lookup"><span data-stu-id="ea4a2-106">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), which implements a calculator service.</span></span> <span data-ttu-id="ea4a2-107">`ICalculator` Sözleşme, çalışan bir sonuç tutarken gerçekleştirilecek aritmetik işlemler kümesi izin verecek şekilde değiştirildi.</span><span class="sxs-lookup"><span data-stu-id="ea4a2-107">The `ICalculator` contract has been modified to allow a set of arithmetic operations to be performed, while keeping a running result.</span></span> <span data-ttu-id="ea4a2-108">Bu işlev tarafından tanımlanan `ICalculatorSession` sözleşme.</span><span class="sxs-lookup"><span data-stu-id="ea4a2-108">This functionality is defined by the `ICalculatorSession` contract.</span></span> <span data-ttu-id="ea4a2-109">Birden çok hizmet işlemleri bir hesaplama gerçekleştirmek için adlandırıldığı gibi hizmet için bir istemci durumu korur.</span><span class="sxs-lookup"><span data-stu-id="ea4a2-109">The service maintains the state for a client as multiple service operations are called to perform a calculation.</span></span> <span data-ttu-id="ea4a2-110">İstemci, çağırarak geçerli sonucu alabilirsiniz `Result()` çağırarak sıfır sonucu temizleyin `Clear()`.</span><span class="sxs-lookup"><span data-stu-id="ea4a2-110">The client can retrieve the current result by calling `Result()` and clear the result to zero by calling `Clear()`.</span></span>  
  
 <span data-ttu-id="ea4a2-111">Bu örnekte, istemci bir konsol uygulaması (.exe) ve hizmet Internet Information Services (IIS) tarafından barındırılır.</span><span class="sxs-lookup"><span data-stu-id="ea4a2-111">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ea4a2-112">Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="ea4a2-112">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="ea4a2-113">Ayarı <xref:System.ServiceModel.SessionMode> için sözleşmenin `Required` sözleşme üzerinden belirli bir bağlama olarak sunulduğunda oturumları bağlamayı desteklediğini sağlar.</span><span class="sxs-lookup"><span data-stu-id="ea4a2-113">Setting the <xref:System.ServiceModel.SessionMode> of the contract to `Required` ensures that when the contract is exposed over a particular binding, the binding supports sessions.</span></span> <span data-ttu-id="ea4a2-114">Bağlama oturumları desteklemiyorsa bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="ea4a2-114">If the binding does not support sessions an exception is thrown.</span></span> <span data-ttu-id="ea4a2-115">`ICalculatorSession` Arabirimi tanımlanmış bir veya daha fazla işlemler çağrılabilir Öyle ki, çalışan bir sonuç değiştirir aşağıdaki örnek kodda gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="ea4a2-115">The `ICalculatorSession` interface is defined such that one or more operations can be called, which modifies a running result, as shown in the following sample code.</span></span>  
  
```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples", SessionMode=SessionMode.Required)]  
public interface ICalculatorSession  
{  
    [OperationContract(IsOneWay=true)]  
    void Clear();  
    [OperationContract(IsOneWay = true)]  
    void AddTo(double n);  
    [OperationContract(IsOneWay = true)]  
    void SubtractFrom(double n);  
    [OperationContract(IsOneWay = true)]  
    void MultiplyBy(double n);  
    [OperationContract(IsOneWay = true)]  
    void DivideBy(double n);  
    [OperationContract]  
    double Result();  
}  
```  
  
 <span data-ttu-id="ea4a2-116">Hizmeti kullandığı bir <xref:System.ServiceModel.InstanceContextMode> , <xref:System.ServiceModel.InstanceContextMode.PerSession> gelen her oturum için belirli hizmet örneğinin bağlamı bağlamak için.</span><span class="sxs-lookup"><span data-stu-id="ea4a2-116">The service uses a <xref:System.ServiceModel.InstanceContextMode> of <xref:System.ServiceModel.InstanceContextMode.PerSession> to bind a given service instance context to each incoming session.</span></span> <span data-ttu-id="ea4a2-117">Bu, yerel üye değişkenini her oturumda çalışan sonucu bir hizmet sağlar.</span><span class="sxs-lookup"><span data-stu-id="ea4a2-117">This allows the service to maintain the running result for each session in a local member variable.</span></span>  
  
```csharp
[ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)]  
public class CalculatorService : ICalculatorSession  
{  
    double result = 0.0D;  
  
    public void Clear()  
    {  result = 0.0D; }  
  
    public void AddTo(double n)  
    {  result += n;   }  
  
    public void SubtractFrom(double n)  
    {  result -= n;   }  
  
    public void MultiplyBy(double n)  
    {  result *= n;   }  
  
    public void DivideBy(double n)  
    {  result /= n;   }  
  
    public double Result()  
    {  return result; }  
}  
```  
  
 <span data-ttu-id="ea4a2-118">Örneği çalıştırdığında istemci sunucuya birden çok isteği yapan ve ardından istemci konsol penceresinde görüntüler sonucu ister.</span><span class="sxs-lookup"><span data-stu-id="ea4a2-118">When you run the sample, the client makes several requests to the server and requests the result, which it then displays in the client console window.</span></span> <span data-ttu-id="ea4a2-119">İstemci bilgisayarı için istemci penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="ea4a2-119">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
(((0 + 100) - 50) * 17.65) / 2 = 441.25  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="ea4a2-120">Ayarlamak için derleme ve örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="ea4a2-120">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="ea4a2-121">Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ea4a2-121">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="ea4a2-122">Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ea4a2-122">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="ea4a2-123">Tek veya çapraz makine yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ea4a2-123">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ea4a2-124">Örnekler, makinenizde zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="ea4a2-124">The samples may already be installed on your machine.</span></span> <span data-ttu-id="ea4a2-125">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="ea4a2-125">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="ea4a2-126">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="ea4a2-126">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ea4a2-127">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="ea4a2-127">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Session`  
  
## <a name="see-also"></a><span data-ttu-id="ea4a2-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ea4a2-128">See also</span></span>
