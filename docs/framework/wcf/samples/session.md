---
title: Oturum
ms.date: 03/30/2017
helpviewer_keywords:
- Sessions
ms.assetid: 36e1db50-008c-4b32-8d09-b56e790b8417
ms.openlocfilehash: 283c8b9641dcce8b0207d3be0024b57369d125ff
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84591468"
---
# <a name="session"></a><span data-ttu-id="745e0-102">Oturum</span><span class="sxs-lookup"><span data-stu-id="745e0-102">Session</span></span>
<span data-ttu-id="745e0-103">Oturum örneği, oturum gerektiren bir sözleşmenin nasıl uygulanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="745e0-103">The Session sample demonstrates how to implement a contract that requires a session.</span></span> <span data-ttu-id="745e0-104">Bir oturum, birden çok işlemi gerçekleştirmek için bağlam sağlar.</span><span class="sxs-lookup"><span data-stu-id="745e0-104">A session provides context for performing multiple operations.</span></span> <span data-ttu-id="745e0-105">Bu, bir hizmetin, sonraki işlemlerin önceki bir işlemin durumunu kullanabilmesi gibi, durumu belirli bir oturumla ilişkilendirmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="745e0-105">This allows a service to associate state with a given session, such that subsequent operations can use the state of a previous operation.</span></span> <span data-ttu-id="745e0-106">Bu örnek, bir Hesaplayıcı hizmeti uygulayan [kullanmaya](getting-started-sample.md)Başlarken ' i temel alır.</span><span class="sxs-lookup"><span data-stu-id="745e0-106">This sample is based on the [Getting Started](getting-started-sample.md), which implements a calculator service.</span></span> <span data-ttu-id="745e0-107">`ICalculator`Sözleşme, çalışan bir sonuç tutarken bir dizi aritmetik işlemin gerçekleştirilmesine izin verecek şekilde değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="745e0-107">The `ICalculator` contract has been modified to allow a set of arithmetic operations to be performed, while keeping a running result.</span></span> <span data-ttu-id="745e0-108">Bu işlev, sözleşme tarafından tanımlanır `ICalculatorSession` .</span><span class="sxs-lookup"><span data-stu-id="745e0-108">This functionality is defined by the `ICalculatorSession` contract.</span></span> <span data-ttu-id="745e0-109">Bir hesaplama gerçekleştirmek için birden çok hizmet işlemi çağrıldığında hizmet, bir istemcinin durumunu tutar.</span><span class="sxs-lookup"><span data-stu-id="745e0-109">The service maintains the state for a client as multiple service operations are called to perform a calculation.</span></span> <span data-ttu-id="745e0-110">İstemci, çağırarak sonucunu sıfıra getirerek geçerli sonucu alabilir `Result()` `Clear()` .</span><span class="sxs-lookup"><span data-stu-id="745e0-110">The client can retrieve the current result by calling `Result()` and clear the result to zero by calling `Clear()`.</span></span>  
  
 <span data-ttu-id="745e0-111">Bu örnekte, istemci bir konsol uygulaması (. exe) ve hizmet Internet Information Services (IIS) tarafından barındırılır.</span><span class="sxs-lookup"><span data-stu-id="745e0-111">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="745e0-112">Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="745e0-112">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="745e0-113">Sözleşmenin <xref:System.ServiceModel.SessionMode> `Required` belirli bir bağlama üzerinden kullanıma sunulduğunu sağlamak için sözleşmenin, bağlamanın oturumları desteklediğini sağlar.</span><span class="sxs-lookup"><span data-stu-id="745e0-113">Setting the <xref:System.ServiceModel.SessionMode> of the contract to `Required` ensures that when the contract is exposed over a particular binding, the binding supports sessions.</span></span> <span data-ttu-id="745e0-114">Bağlama oturumları desteklemiyorsa, bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="745e0-114">If the binding does not support sessions an exception is thrown.</span></span> <span data-ttu-id="745e0-115">`ICalculatorSession`Arabirim, aşağıdaki örnek kodda gösterildiği gibi, çalışan bir sonucu değiştiren bir veya daha fazla işlemin çağrılabilmesi için tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="745e0-115">The `ICalculatorSession` interface is defined such that one or more operations can be called, which modifies a running result, as shown in the following sample code.</span></span>  
  
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
  
 <span data-ttu-id="745e0-116">Hizmet, belirli bir <xref:System.ServiceModel.InstanceContextMode> <xref:System.ServiceModel.InstanceContextMode.PerSession> hizmet örneği bağlamını her bir gelen oturuma bağlamak için ' nı kullanır.</span><span class="sxs-lookup"><span data-stu-id="745e0-116">The service uses a <xref:System.ServiceModel.InstanceContextMode> of <xref:System.ServiceModel.InstanceContextMode.PerSession> to bind a given service instance context to each incoming session.</span></span> <span data-ttu-id="745e0-117">Bu, hizmetin yerel bir üye değişkeninde her oturum için çalışan sonucu korumasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="745e0-117">This allows the service to maintain the running result for each session in a local member variable.</span></span>  
  
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
  
 <span data-ttu-id="745e0-118">Örneği çalıştırdığınızda, istemci sunucuya birkaç istek yapar ve sonuç ister ve daha sonra istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="745e0-118">When you run the sample, the client makes several requests to the server and requests the result, which it then displays in the client console window.</span></span> <span data-ttu-id="745e0-119">İstemcisini kapatmak için istemci penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="745e0-119">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
(((0 + 100) - 50) * 17.65) / 2 = 441.25  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="745e0-120">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="745e0-120">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="745e0-121">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="745e0-121">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="745e0-122">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)konusundaki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="745e0-122">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="745e0-123">Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="745e0-123">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="745e0-124">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="745e0-124">The samples may already be installed on your machine.</span></span> <span data-ttu-id="745e0-125">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="745e0-125">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="745e0-126">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="745e0-126">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="745e0-127">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="745e0-127">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Session`  
