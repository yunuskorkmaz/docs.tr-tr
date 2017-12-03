---
title: Oturum
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Sessions
ms.assetid: 36e1db50-008c-4b32-8d09-b56e790b8417
caps.latest.revision: "31"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 01c1bc2d202080349db32452adfe549d7a6dd3cc
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="session"></a><span data-ttu-id="19339-102">Oturum</span><span class="sxs-lookup"><span data-stu-id="19339-102">Session</span></span>
<span data-ttu-id="19339-103">Oturum örnek, bir oturum gerektiren bir sözleşmesini uygulama gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="19339-103">The Session sample demonstrates how to implement a contract that requires a session.</span></span> <span data-ttu-id="19339-104">Bir oturum, birden çok işlemleri gerçekleştirmek için bir bağlam sağlar.</span><span class="sxs-lookup"><span data-stu-id="19339-104">A session provides context for performing multiple operations.</span></span> <span data-ttu-id="19339-105">Sonraki işlemleri önceki bir işlemin durumunu kullanabilirsiniz, bu durum belirli bir oturum ile ilişkilendirmek bir hizmet sağlar.</span><span class="sxs-lookup"><span data-stu-id="19339-105">This allows a service to associate state with a given session, such that subsequent operations can use the state of a previous operation.</span></span> <span data-ttu-id="19339-106">Bu örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md), hesap makinesi hizmetinin uygular.</span><span class="sxs-lookup"><span data-stu-id="19339-106">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), which implements a calculator service.</span></span> <span data-ttu-id="19339-107">`ICalculator` Sözleşme, çalışan bir sonuç tutarken gerçekleştirilecek aritmetik işlemler kümesi izin verecek şekilde değiştirildi.</span><span class="sxs-lookup"><span data-stu-id="19339-107">The `ICalculator` contract has been modified to allow a set of arithmetic operations to be performed, while keeping a running result.</span></span> <span data-ttu-id="19339-108">Bu işlev tarafından tanımlanan `ICalculatorSession` sözleşme.</span><span class="sxs-lookup"><span data-stu-id="19339-108">This functionality is defined by the `ICalculatorSession` contract.</span></span> <span data-ttu-id="19339-109">Bir hesaplama gerçekleştirmek için birden çok hizmet işlemleri adlı olarak hizmet için bir istemci durumu tutar.</span><span class="sxs-lookup"><span data-stu-id="19339-109">The service maintains the state for a client as multiple service operations are called to perform a calculation.</span></span> <span data-ttu-id="19339-110">İstemcisi, çağırarak geçerli sonucu alabilir `Result()` ve çağırarak sıfır sonucu temizleyin `Clear()`.</span><span class="sxs-lookup"><span data-stu-id="19339-110">The client can retrieve the current result by calling `Result()` and clear the result to zero by calling `Clear()`.</span></span>  
  
 <span data-ttu-id="19339-111">Bu örnekte, istemci bir konsol uygulaması (.exe) ve Internet Information Services (IIS) tarafından barındırılan hizmetindeki.</span><span class="sxs-lookup"><span data-stu-id="19339-111">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="19339-112">Kurulum yordamı ve yapı yönergeleri Bu örnek için bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="19339-112">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="19339-113">Ayarı <xref:System.ServiceModel.SessionMode> sözleşmesinin `Required` sözleşme belirli bir bağlama üzerinden kullanıma sunulduğunda bağlama oturumları desteklediğini sağlar.</span><span class="sxs-lookup"><span data-stu-id="19339-113">Setting the <xref:System.ServiceModel.SessionMode> of the contract to `Required` ensures that when the contract is exposed over a particular binding, the binding supports sessions.</span></span> <span data-ttu-id="19339-114">Bağlama oturumları desteklemiyorsa özel durum oluşur.</span><span class="sxs-lookup"><span data-stu-id="19339-114">If the binding does not support sessions an exception is thrown.</span></span> <span data-ttu-id="19339-115">`ICalculatorSession` Arabirimi tanımlanmış bir veya daha fazla işlem çağrılabilir şekilde, çalışan bir sonuç değiştirir aşağıdaki örnek kodda gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="19339-115">The `ICalculatorSession` interface is defined such that one or more operations can be called, which modifies a running result, as shown in the following sample code.</span></span>  
  
```  
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
  
 <span data-ttu-id="19339-116">Hizmet kullanan bir <xref:System.ServiceModel.InstanceContextMode> , <xref:System.ServiceModel.InstanceContextMode.PerSession> gelen her oturum için belirli hizmeti örnek bağlamı bağlamak için.</span><span class="sxs-lookup"><span data-stu-id="19339-116">The service uses a <xref:System.ServiceModel.InstanceContextMode> of <xref:System.ServiceModel.InstanceContextMode.PerSession> to bind a given service instance context to each incoming session.</span></span> <span data-ttu-id="19339-117">Bu bir yerel üye değişkeninde her oturum için çalışan sonuç korumak hizmet sağlar.</span><span class="sxs-lookup"><span data-stu-id="19339-117">This allows the service to maintain the running result for each session in a local member variable.</span></span>  
  
```  
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
  
 <span data-ttu-id="19339-118">Örneği çalıştırdığınızda, istemci sunucuya birçok istek yapar ve sonra istemci konsol penceresinde görüntüler sonucu ister.</span><span class="sxs-lookup"><span data-stu-id="19339-118">When you run the sample, the client makes several requests to the server and requests the result, which it then displays in the client console window.</span></span> <span data-ttu-id="19339-119">İstemcisi penceresinde istemciyi aşağı kapatmak için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="19339-119">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
(((0 + 100) - 50) * 17.65) / 2 = 441.25  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="19339-120">Ayarlamak için derleme ve örnek çalıştırın</span><span class="sxs-lookup"><span data-stu-id="19339-120">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="19339-121">Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="19339-121">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="19339-122">Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="19339-122">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="19339-123">Tek veya çapraz makine yapılandırmada örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="19339-123">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="19339-124">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="19339-124">The samples may already be installed on your machine.</span></span> <span data-ttu-id="19339-125">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="19339-125">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="19339-126">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="19339-126">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="19339-127">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="19339-127">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Session`  
  
## <a name="see-also"></a><span data-ttu-id="19339-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="19339-128">See Also</span></span>
