---
title: Oturum
ms.date: 03/30/2017
helpviewer_keywords:
- Sessions
ms.assetid: 36e1db50-008c-4b32-8d09-b56e790b8417
ms.openlocfilehash: 85f1034999fc4cd36075c49bd8f4631bbd283679
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183358"
---
# <a name="session"></a><span data-ttu-id="3a143-102">Oturum</span><span class="sxs-lookup"><span data-stu-id="3a143-102">Session</span></span>
<span data-ttu-id="3a143-103">Oturum örneği, oturum gerektiren bir sözleşmenin nasıl uygulanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="3a143-103">The Session sample demonstrates how to implement a contract that requires a session.</span></span> <span data-ttu-id="3a143-104">Oturum, birden çok işlem gerçekleştirmek için bağlam sağlar.</span><span class="sxs-lookup"><span data-stu-id="3a143-104">A session provides context for performing multiple operations.</span></span> <span data-ttu-id="3a143-105">Bu, bir hizmetin durumu belirli bir oturumla ilişkilendirmesine olanak tanır, böylece sonraki işlemler önceki bir işlemin durumunu kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="3a143-105">This allows a service to associate state with a given session, such that subsequent operations can use the state of a previous operation.</span></span> <span data-ttu-id="3a143-106">Bu örnek, bir hesap makinesi hizmeti uygulayan [Başlarken'e](../../../../docs/framework/wcf/samples/getting-started-sample.md)dayanır.</span><span class="sxs-lookup"><span data-stu-id="3a143-106">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), which implements a calculator service.</span></span> <span data-ttu-id="3a143-107">Sözleşme, `ICalculator` çalışan bir sonucu tutarken bir dizi aritmetik işlem yapılmasına izin verecek şekilde değiştirildi.</span><span class="sxs-lookup"><span data-stu-id="3a143-107">The `ICalculator` contract has been modified to allow a set of arithmetic operations to be performed, while keeping a running result.</span></span> <span data-ttu-id="3a143-108">Bu işlevsellik `ICalculatorSession` sözleşme tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="3a143-108">This functionality is defined by the `ICalculatorSession` contract.</span></span> <span data-ttu-id="3a143-109">Birden çok hizmet işlemleri bir hesaplama gerçekleştirmek için çağrıldığı gibi hizmet bir istemci için durumu tutar.</span><span class="sxs-lookup"><span data-stu-id="3a143-109">The service maintains the state for a client as multiple service operations are called to perform a calculation.</span></span> <span data-ttu-id="3a143-110">İstemci arayarak `Result()` geçerli sonucu alabilir ve arayarak `Clear()`sonucu sıfıra temizleyebilir.</span><span class="sxs-lookup"><span data-stu-id="3a143-110">The client can retrieve the current result by calling `Result()` and clear the result to zero by calling `Clear()`.</span></span>  
  
 <span data-ttu-id="3a143-111">Bu örnekte, istemci bir konsol uygulamasıdır (.exe) ve hizmet Internet Information Services (IIS) tarafından barındırılır.</span><span class="sxs-lookup"><span data-stu-id="3a143-111">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3a143-112">Bu örnek için kurulum yordamı ve yapı yönergeleri bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="3a143-112">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="3a143-113"><xref:System.ServiceModel.SessionMode> Sözleşmenin belirli bir `Required` bağlayıcı üzerinde maruz kaldığında, bağlamanın oturumları desteklemesini sağlayacak şekilde ayarlanması.</span><span class="sxs-lookup"><span data-stu-id="3a143-113">Setting the <xref:System.ServiceModel.SessionMode> of the contract to `Required` ensures that when the contract is exposed over a particular binding, the binding supports sessions.</span></span> <span data-ttu-id="3a143-114">Bağlama oturumları desteklemiyorsa bir özel durum atılır.</span><span class="sxs-lookup"><span data-stu-id="3a143-114">If the binding does not support sessions an exception is thrown.</span></span> <span data-ttu-id="3a143-115">Arabirim, `ICalculatorSession` aşağıdaki örnek kodda gösterildiği gibi çalışan bir sonucu değiştiren bir veya daha fazla işlem çağrılabilen şekilde tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="3a143-115">The `ICalculatorSession` interface is defined such that one or more operations can be called, which modifies a running result, as shown in the following sample code.</span></span>  
  
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
  
 <span data-ttu-id="3a143-116">Hizmet, belirli <xref:System.ServiceModel.InstanceContextMode> <xref:System.ServiceModel.InstanceContextMode.PerSession> bir hizmet örneği bağlamını gelen her oturuma bağlamak için a kullanır.</span><span class="sxs-lookup"><span data-stu-id="3a143-116">The service uses a <xref:System.ServiceModel.InstanceContextMode> of <xref:System.ServiceModel.InstanceContextMode.PerSession> to bind a given service instance context to each incoming session.</span></span> <span data-ttu-id="3a143-117">Bu, hizmetin her oturum için çalışan sonucu yerel bir üye değişkende korumasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="3a143-117">This allows the service to maintain the running result for each session in a local member variable.</span></span>  
  
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
  
 <span data-ttu-id="3a143-118">Örneği çalıştırdığınızda, istemci sunucuya çeşitli isteklerde bulunur ve sonucu ister ve bu istek daha sonra istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="3a143-118">When you run the sample, the client makes several requests to the server and requests the result, which it then displays in the client console window.</span></span> <span data-ttu-id="3a143-119">İstemciyi kapatmak için istemci penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="3a143-119">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
(((0 + 100) - 50) * 17.65) / 2 = 441.25  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="3a143-120">Örneği ayarlamak, oluşturmak ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="3a143-120">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="3a143-121">Windows Communication Foundation [Samples için Tek Seferlik Kurulum Yordamı'nı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizi emin olun.</span><span class="sxs-lookup"><span data-stu-id="3a143-121">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="3a143-122">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak [için, Windows Communication Foundation Samples'i oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="3a143-122">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="3a143-123">Örneği tek veya çapraz makine yapılandırmasında çalıştırmak için, [Windows Communication Foundation Samples'ı çalıştıran](../../../../docs/framework/wcf/samples/running-the-samples.md)yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="3a143-123">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="3a143-124">Numuneler makinenize zaten yüklenmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="3a143-124">The samples may already be installed on your machine.</span></span> <span data-ttu-id="3a143-125">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="3a143-125">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="3a143-126">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="3a143-126">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="3a143-127">Bu örnek aşağıdaki dizinde yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="3a143-127">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Session`  
