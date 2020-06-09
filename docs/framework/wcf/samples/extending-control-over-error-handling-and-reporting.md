---
title: Hata İşleme ve Bildirme Denetimini Genişletme
ms.date: 03/30/2017
ms.assetid: 45f996a7-fa00-45cb-9d6f-b368f5778aaa
ms.openlocfilehash: c7ca8d85220d65905bc4d9d220de366c331504a4
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600548"
---
# <a name="extending-control-over-error-handling-and-reporting"></a><span data-ttu-id="5250f-102">Hata İşleme ve Bildirme Denetimini Genişletme</span><span class="sxs-lookup"><span data-stu-id="5250f-102">Extending Control Over Error Handling and Reporting</span></span>
<span data-ttu-id="5250f-103">Bu örnek, arabirimi kullanarak bir Windows Communication Foundation (WCF) hizmetinde hata işleme ve hata raporlama üzerinde denetimin nasıl genişletileceğini gösterir <xref:System.ServiceModel.Dispatcher.IErrorHandler> .</span><span class="sxs-lookup"><span data-stu-id="5250f-103">This sample demonstrates how to extend control over error handling and error reporting in a Windows Communication Foundation (WCF) service using the <xref:System.ServiceModel.Dispatcher.IErrorHandler> interface.</span></span> <span data-ttu-id="5250f-104">Örnek, hataları işlemek için hizmete eklenen bazı ek kod ile [çalışmaya](getting-started-sample.md) başlama konusunda temel alır.</span><span class="sxs-lookup"><span data-stu-id="5250f-104">The sample is based on the [Getting Started](getting-started-sample.md) with some additional code added to the service to handle errors.</span></span> <span data-ttu-id="5250f-105">İstemci birkaç hata koşulu zorlar.</span><span class="sxs-lookup"><span data-stu-id="5250f-105">The client forces several error conditions.</span></span> <span data-ttu-id="5250f-106">Hizmet hataları karşılar ve bunları bir dosyada günlüğe kaydeder.</span><span class="sxs-lookup"><span data-stu-id="5250f-106">The service intercepts the errors and logs them in a file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5250f-107">Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="5250f-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="5250f-108">Hizmetler hataları ele geçirebilir, işleme gerçekleştirebilir ve arabirim kullanarak hataların nasıl raporlanacağı etkisini etkileyebilir <xref:System.ServiceModel.Dispatcher.IErrorHandler> .</span><span class="sxs-lookup"><span data-stu-id="5250f-108">Services can intercept errors, perform processing, and affect how errors are reported using the <xref:System.ServiceModel.Dispatcher.IErrorHandler> interface.</span></span> <span data-ttu-id="5250f-109">Arabirimin uygulanıuygulanabilen iki yöntemi vardır: <xref:System.ServiceModel.Dispatcher.IErrorHandler.ProvideFault%28System.Exception%2CSystem.ServiceModel.Channels.MessageVersion%2CSystem.ServiceModel.Channels.Message%40%29> ve <xref:System.ServiceModel.Dispatcher.IErrorHandler.HandleError%2A> .</span><span class="sxs-lookup"><span data-stu-id="5250f-109">The interface has two methods that can be implemented: <xref:System.ServiceModel.Dispatcher.IErrorHandler.ProvideFault%28System.Exception%2CSystem.ServiceModel.Channels.MessageVersion%2CSystem.ServiceModel.Channels.Message%40%29> and <xref:System.ServiceModel.Dispatcher.IErrorHandler.HandleError%2A>.</span></span> <span data-ttu-id="5250f-110"><xref:System.ServiceModel.Dispatcher.IErrorHandler.ProvideFault%28System.Exception%2CSystem.ServiceModel.Channels.MessageVersion%2CSystem.ServiceModel.Channels.Message%40%29>Yöntemi, bir özel duruma yanıt olarak oluşturulan bir hata iletisini eklemenize, değiştirmenize veya gizlemesine olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="5250f-110">The <xref:System.ServiceModel.Dispatcher.IErrorHandler.ProvideFault%28System.Exception%2CSystem.ServiceModel.Channels.MessageVersion%2CSystem.ServiceModel.Channels.Message%40%29> method allows you to add, modify, or suppress a fault message that is generated in response to an exception.</span></span> <span data-ttu-id="5250f-111"><xref:System.ServiceModel.Dispatcher.IErrorHandler.HandleError%2A>Yöntemi hata işlemenin hata durumunda gerçekleşmesini sağlar ve ek hata işlemenin çalıştırılıp çalıştırılmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="5250f-111">The <xref:System.ServiceModel.Dispatcher.IErrorHandler.HandleError%2A> method allows error processing to take place in the event of an error and controls whether additional error handling can run.</span></span>  
  
 <span data-ttu-id="5250f-112">Bu örnekte, `CalculatorErrorHandler` türü <xref:System.ServiceModel.Dispatcher.IErrorHandler> arabirimini uygular.</span><span class="sxs-lookup"><span data-stu-id="5250f-112">In this sample, the `CalculatorErrorHandler` type implements the <xref:System.ServiceModel.Dispatcher.IErrorHandler> interface.</span></span> <span data-ttu-id="5250f-113">İçinde</span><span class="sxs-lookup"><span data-stu-id="5250f-113">In the</span></span>  
  
 <span data-ttu-id="5250f-114"><xref:System.ServiceModel.Dispatcher.IErrorHandler.HandleError%2A>yöntemi, `CalculatorErrorHandler` c:\logs. içindeki Error. txt metin dosyasına hata günlüğü yazar.</span><span class="sxs-lookup"><span data-stu-id="5250f-114"><xref:System.ServiceModel.Dispatcher.IErrorHandler.HandleError%2A> method, the `CalculatorErrorHandler` writes a log of the error to an Error.txt text file in c:\logs.</span></span> <span data-ttu-id="5250f-115">Örneğin hatayı günlüğe kaydettiğine ve bunu göstermez ve istemciye geri raporlanmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="5250f-115">Note that the sample logs the fault and does not suppress it, allowing it to be reported back to the client.</span></span>  
  
```csharp
public class CalculatorErrorHandler : IErrorHandler
{
    // Provide a fault. The Message fault parameter can be replaced, or set to
    // null to suppress reporting a fault.

    public void ProvideFault(Exception error, MessageVersion version, ref Message fault)
    {
    }

    // HandleError. Log an error, then allow the error to be handled as usual.
    // Return true if the error is considered as already handled

    public bool HandleError(Exception error)
    {
        using (TextWriter tw = File.AppendText(@"c:\logs\error.txt"))
        {
            if (error != null)
            {
                tw.WriteLine("Exception: " + error.GetType().Name + " - " + error.Message);
            }
            tw.Close();
        }
        return true;
    }
}  
```  
  
 <span data-ttu-id="5250f-116">`ErrorBehaviorAttribute`Bir hizmet ile bir hata işleyicisini kaydetme mekanizması olarak mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="5250f-116">The `ErrorBehaviorAttribute` exists as a mechanism to register an error handler with a service.</span></span> <span data-ttu-id="5250f-117">Bu öznitelik tek bir tür parametresi alır.</span><span class="sxs-lookup"><span data-stu-id="5250f-117">This attribute takes a single type parameter.</span></span> <span data-ttu-id="5250f-118">Bu tür <xref:System.ServiceModel.Dispatcher.IErrorHandler> arabirimini uygulamalıdır ve genel, boş bir oluşturucuya sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5250f-118">That type should implement the <xref:System.ServiceModel.Dispatcher.IErrorHandler> interface and should have a public, empty constructor.</span></span> <span data-ttu-id="5250f-119">Özniteliği daha sonra bu hata işleyicisi türünün bir örneğini başlatır ve hizmete kurar.</span><span class="sxs-lookup"><span data-stu-id="5250f-119">The attribute then instantiates an instance of that error handler type and installs it into the service.</span></span> <span data-ttu-id="5250f-120">Bunu, <xref:System.ServiceModel.Description.IServiceBehavior> arabirimini uygulayarak ve sonra <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A> Hata işleyicisinin örneklerine eklemek için yöntemini kullanarak yapar.</span><span class="sxs-lookup"><span data-stu-id="5250f-120">It does this by implementing the <xref:System.ServiceModel.Description.IServiceBehavior> interface and then using the <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A> method to add instances of the error handler to the service.</span></span>  
  
```csharp
// This attribute can be used to install a custom error handler for a service.  
public class ErrorBehaviorAttribute : Attribute, IServiceBehavior  
{  
    Type errorHandlerType;  
  
    public ErrorBehaviorAttribute(Type errorHandlerType)  
    {  
        this.errorHandlerType = errorHandlerType;  
    }  
  
    void IServiceBehavior.Validate(ServiceDescription description, ServiceHostBase serviceHostBase)  
    {  
    }  
  
    void IServiceBehavior.AddBindingParameters(ServiceDescription description, ServiceHostBase serviceHostBase, System.Collections.ObjectModel.Collection<ServiceEndpoint> endpoints, BindingParameterCollection parameters)  
    {  
    }  
  
    void IServiceBehavior.ApplyDispatchBehavior(ServiceDescription description, ServiceHostBase serviceHostBase)  
    {  
        IErrorHandler errorHandler;  
  
        try  
        {  
            errorHandler = (IErrorHandler)Activator.CreateInstance(errorHandlerType);  
        }  
        catch (MissingMethodException e)  
        {  
            throw new ArgumentException("The errorHandlerType specified in the ErrorBehaviorAttribute constructor must have a public empty constructor.", e);  
        }  
        catch (InvalidCastException e)  
        {  
            throw new ArgumentException("The errorHandlerType specified in the ErrorBehaviorAttribute constructor must implement System.ServiceModel.Dispatcher.IErrorHandler.", e);  
        }  
  
        foreach (ChannelDispatcherBase channelDispatcherBase in serviceHostBase.ChannelDispatchers)  
        {  
            ChannelDispatcher channelDispatcher = channelDispatcherBase as ChannelDispatcher;  
            channelDispatcher.ErrorHandlers.Add(errorHandler);  
        }
    }  
}  
```  
  
 <span data-ttu-id="5250f-121">Örnek, bir Hesaplayıcı hizmeti uygular.</span><span class="sxs-lookup"><span data-stu-id="5250f-121">The sample implements a calculator service.</span></span> <span data-ttu-id="5250f-122">İstemci, geçersiz değerlere sahip parametreler sağlayarak hizmette iki hatanın oluşmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="5250f-122">The client deliberately causes two errors to occur on the service by providing parameters with illegal values.</span></span> <span data-ttu-id="5250f-123">, `CalculatorErrorHandler` <xref:System.ServiceModel.Dispatcher.IErrorHandler> Hataları yerel bir dosyaya kaydetmek için arabirimini kullanır ve ardından istemciye geri bildirilmelerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="5250f-123">The `CalculatorErrorHandler` uses the <xref:System.ServiceModel.Dispatcher.IErrorHandler> interface to log the errors to a local file and then allows them to be reported back to the client.</span></span> <span data-ttu-id="5250f-124">İstemci, sıfıra bölme ve bağımsız değişken olmayan bir koşula zorlar.</span><span class="sxs-lookup"><span data-stu-id="5250f-124">The client forces a divide by zero and an argument-out-of-range condition.</span></span>  
  
```csharp
try
{  
    Console.WriteLine("Forcing an error in Divide");  
    // Call the Divide service operation - trigger a divide by 0 error.  
    value1 = 22;  
    value2 = 0;  
    result = proxy.Divide(value1, value2);  
    Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result);  
}  
catch (FaultException e)  
{  
    Console.WriteLine("FaultException: " + e.GetType().Name + " - " + e.Message);  
}  
catch (Exception e)  
{  
    Console.WriteLine("Exception: " + e.GetType().Name + " - " + e.Message);  
}  
```  
  
 <span data-ttu-id="5250f-125">Örneği çalıştırdığınızda, işlem istekleri ve yanıtları istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="5250f-125">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="5250f-126">Sıfıra göre bölme ve bağımsız değişken dışı koşulların hata olarak raporlanmakta olduğunu görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="5250f-126">You see the division by zero and the argument-out-of-range conditions being reported as faults.</span></span> <span data-ttu-id="5250f-127">İstemcisini kapatmak için istemci penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="5250f-127">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Add(15,3) = 18  
Subtract(145,76) = 69  
Multiply(9,81) = 729  
Forcing an error in Divide  
FaultException: FaultException - Invalid Argument: The second argument must not be zero.  
Forcing an error in Factorial  
FaultException: FaultException - Invalid Argument: The argument must be greater than zero.  
  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="5250f-128">C:\logs\errors.txt dosyası, hizmet tarafından karşılaşılan hatalar hakkında günlüğe kaydedilen bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="5250f-128">The file c:\logs\errors.txt contains the information logged about the errors by the service.</span></span> <span data-ttu-id="5250f-129">Hizmetin dizine yazması için hizmetin çalıştığı işlemin (genellikle ASP.NET veya ağ hizmeti) dizine yazma iznine sahip olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="5250f-129">Note that for the service to write to the directory you must make sure that the process under which the service is running (typically ASP.NET or Network Service) has permission to write to the directory.</span></span>  
  
```txt
Fault: Reason = Invalid Argument: The second argument must not be zero.  
Fault: Reason = Invalid Argument: The argument must be greater than zero.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="5250f-130">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="5250f-130">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="5250f-131">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="5250f-131">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="5250f-132">Çözümü derlemek için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="5250f-132">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="5250f-133">Error. txt dosyası için c:\logs. dizinini oluşturduğunuzdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="5250f-133">Ensure you have created the c:\logs directory for the error.txt file.</span></span> <span data-ttu-id="5250f-134">Veya ' de kullanılan dosya adını değiştirebilirsiniz `CalculatorErrorHandler.HandleError` .</span><span class="sxs-lookup"><span data-stu-id="5250f-134">Or modify the file name used in `CalculatorErrorHandler.HandleError`.</span></span>  
  
4. <span data-ttu-id="5250f-135">Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="5250f-135">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="5250f-136">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="5250f-136">The samples may already be installed on your machine.</span></span> <span data-ttu-id="5250f-137">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="5250f-137">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="5250f-138">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="5250f-138">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="5250f-139">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="5250f-139">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\ErrorHandling`  
