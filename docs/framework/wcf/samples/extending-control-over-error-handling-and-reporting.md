---
title: Hata İşleme ve Bildirme Denetimini Genişletme
ms.date: 03/30/2017
ms.assetid: 45f996a7-fa00-45cb-9d6f-b368f5778aaa
ms.openlocfilehash: 6492807b55b50662790cf25807a35ddd65fbe01d
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2018
ms.locfileid: "45595301"
---
# <a name="extending-control-over-error-handling-and-reporting"></a><span data-ttu-id="8804a-102">Hata İşleme ve Bildirme Denetimini Genişletme</span><span class="sxs-lookup"><span data-stu-id="8804a-102">Extending Control Over Error Handling and Reporting</span></span>
<span data-ttu-id="8804a-103">Bu örnek nasıl hata işleme ve hata raporlama kullanarak bir Windows Communication Foundation (WCF) hizmet üzerinde denetim genişletileceğini gösterir <xref:System.ServiceModel.Dispatcher.IErrorHandler> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="8804a-103">This sample demonstrates how to extend control over error handling and error reporting in a Windows Communication Foundation (WCF) service using the <xref:System.ServiceModel.Dispatcher.IErrorHandler> interface.</span></span> <span data-ttu-id="8804a-104">Örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md) hataları işlemek için hizmetine eklenen bazı ek kod.</span><span class="sxs-lookup"><span data-stu-id="8804a-104">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) with some additional code added to the service to handle errors.</span></span> <span data-ttu-id="8804a-105">İstemci, birden çok hata koşulları zorlar.</span><span class="sxs-lookup"><span data-stu-id="8804a-105">The client forces several error conditions.</span></span> <span data-ttu-id="8804a-106">Hizmet hataları yakalar ve bunları bir dosyaya kaydeder.</span><span class="sxs-lookup"><span data-stu-id="8804a-106">The service intercepts the errors and logs them in a file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8804a-107">Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="8804a-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="8804a-108">Hizmetleri ıntercept hataları, işleme gerçekleştirmek ve hataları nasıl bildirildiğini etkileyen kullanarak <xref:System.ServiceModel.Dispatcher.IErrorHandler> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="8804a-108">Services can intercept errors, perform processing, and affect how errors are reported using the <xref:System.ServiceModel.Dispatcher.IErrorHandler> interface.</span></span> <span data-ttu-id="8804a-109">Arabirimin uygulanabilir iki yöntemi vardır: <xref:System.ServiceModel.Dispatcher.IErrorHandler.ProvideFault%28System.Exception%2CSystem.ServiceModel.Channels.MessageVersion%2CSystem.ServiceModel.Channels.Message%40%29> ve <xref:System.ServiceModel.Dispatcher.IErrorHandler.HandleError%2A>.</span><span class="sxs-lookup"><span data-stu-id="8804a-109">The interface has two methods that can be implemented: <xref:System.ServiceModel.Dispatcher.IErrorHandler.ProvideFault%28System.Exception%2CSystem.ServiceModel.Channels.MessageVersion%2CSystem.ServiceModel.Channels.Message%40%29> and <xref:System.ServiceModel.Dispatcher.IErrorHandler.HandleError%2A>.</span></span> <span data-ttu-id="8804a-110"><xref:System.ServiceModel.Dispatcher.IErrorHandler.ProvideFault%28System.Exception%2CSystem.ServiceModel.Channels.MessageVersion%2CSystem.ServiceModel.Channels.Message%40%29> Yöntemi ekleme, değiştirme veya yanıt olarak bir özel durum oluşturan bir hata iletisi gösterme olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="8804a-110">The <xref:System.ServiceModel.Dispatcher.IErrorHandler.ProvideFault%28System.Exception%2CSystem.ServiceModel.Channels.MessageVersion%2CSystem.ServiceModel.Channels.Message%40%29> method allows you to add, modify, or suppress a fault message that is generated in response to an exception.</span></span> <span data-ttu-id="8804a-111"><xref:System.ServiceModel.Dispatcher.IErrorHandler.HandleError%2A> Yöntemi ek hata işleme çalıştırıp çalıştıramayacağını hata ve denetimleri olması durumunda gerçekleşmesi hata işleme sağlar.</span><span class="sxs-lookup"><span data-stu-id="8804a-111">The <xref:System.ServiceModel.Dispatcher.IErrorHandler.HandleError%2A> method allows error processing to take place in the event of an error and controls whether additional error handling can run.</span></span>  
  
 <span data-ttu-id="8804a-112">Bu örnekte `CalculatorErrorHandler` yazın uygular <xref:System.ServiceModel.Dispatcher.IErrorHandler> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="8804a-112">In this sample, the `CalculatorErrorHandler` type implements the <xref:System.ServiceModel.Dispatcher.IErrorHandler> interface.</span></span> <span data-ttu-id="8804a-113">İçinde</span><span class="sxs-lookup"><span data-stu-id="8804a-113">In the</span></span>  
  
 <span data-ttu-id="8804a-114"><xref:System.ServiceModel.Dispatcher.IErrorHandler.HandleError%2A> yöntemi, `CalculatorErrorHandler` hata günlüğünü c:\logs Error.txt bir metin dosyasına yazar.</span><span class="sxs-lookup"><span data-stu-id="8804a-114"><xref:System.ServiceModel.Dispatcher.IErrorHandler.HandleError%2A> method, the `CalculatorErrorHandler` writes a log of the error to an Error.txt text file in c:\logs.</span></span> <span data-ttu-id="8804a-115">Örnek Hata günlüklerini ve, istemciye yeniden bildirilmesine izin veren engellemez unutmayın.</span><span class="sxs-lookup"><span data-stu-id="8804a-115">Note that the sample logs the fault and does not suppress it, allowing it to be reported back to the client.</span></span>  
  
```  
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
  
 <span data-ttu-id="8804a-116">`ErrorBehaviorAttribute` Hizmeti ile bir hata işleyicisini kaydetmek için bir mekanizma olarak bulunmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8804a-116">The `ErrorBehaviorAttribute` exists as a mechanism to register an error handler with a service.</span></span> <span data-ttu-id="8804a-117">Bu öznitelik, bir tek tür parametresi alır.</span><span class="sxs-lookup"><span data-stu-id="8804a-117">This attribute takes a single type parameter.</span></span> <span data-ttu-id="8804a-118">Tür uygulamalıdır <xref:System.ServiceModel.Dispatcher.IErrorHandler> arabirimi ve ortak, boş bir oluşturucusu olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8804a-118">That type should implement the <xref:System.ServiceModel.Dispatcher.IErrorHandler> interface and should have a public, empty constructor.</span></span> <span data-ttu-id="8804a-119">Özniteliği, hata işleyicisi türü bir örneğini başlatır ve hizmete yüklenir.</span><span class="sxs-lookup"><span data-stu-id="8804a-119">The attribute then instantiates an instance of that error handler type and installs it into the service.</span></span> <span data-ttu-id="8804a-120">Bunu uygulayarak yapar <xref:System.ServiceModel.Description.IServiceBehavior> arabirimi ve ardından kullanarak <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A> hizmetine hata işleyicisini örneklerini eklemek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="8804a-120">It does this by implementing the <xref:System.ServiceModel.Description.IServiceBehavior> interface and then using the <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A> method to add instances of the error handler to the service.</span></span>  
  
```  
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
  
 <span data-ttu-id="8804a-121">Örnek hesaplayıcı hizmet uygular.</span><span class="sxs-lookup"><span data-stu-id="8804a-121">The sample implements a calculator service.</span></span> <span data-ttu-id="8804a-122">İstemci, kasıtlı olarak geçersiz değerlerle parametreleri sağlayarak hizmeti üzerinde gerçekleşmesi iki hatalarına neden olur.</span><span class="sxs-lookup"><span data-stu-id="8804a-122">The client deliberately causes two errors to occur on the service by providing parameters with illegal values.</span></span> <span data-ttu-id="8804a-123">`CalculatorErrorHandler` Kullanan <xref:System.ServiceModel.Dispatcher.IErrorHandler> yerel bir dosyaya hataları günlüğe kaydetmek için arabirim ve bunları istemciye geri bildirilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="8804a-123">The `CalculatorErrorHandler` uses the <xref:System.ServiceModel.Dispatcher.IErrorHandler> interface to log the errors to a local file and then allows them to be reported back to the client.</span></span> <span data-ttu-id="8804a-124">İstemci, sıfır hem de aralık, bağımsız değişkeni çıkış koşulu ile bir bölme zorlar.</span><span class="sxs-lookup"><span data-stu-id="8804a-124">The client forces a divide by zero and an argument-out-of-range condition.</span></span>  
  
```  
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
  
 <span data-ttu-id="8804a-125">Örneği çalıştırdığınızda, işlem isteklerini ve yanıtlarını istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="8804a-125">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="8804a-126">Sıfır ve hataları bildirilen aralığı, bağımsız değişkeni çıkış koşulları bölme görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="8804a-126">You see the division by zero and the argument-out-of-range conditions being reported as faults.</span></span> <span data-ttu-id="8804a-127">İstemci bilgisayarı için istemci penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="8804a-127">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Add(15,3) = 18  
Subtract(145,76) = 69  
Multiply(9,81) = 729  
Forcing an error in Divide  
FaultException: FaultException - Invalid Argument: The second argument must not be zero.  
Forcing an error in Factorial  
FaultException: FaultException - Invalid Argument: The argument must be greater than zero.  
  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="8804a-128">Dosya c:\logs\errors.txt hizmet tarafından günlüğüne hatalar hakkında bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="8804a-128">The file c:\logs\errors.txt contains the information logged about the errors by the service.</span></span> <span data-ttu-id="8804a-129">Hizmet emin olmanız gerekir dizine yazmak hizmetin çalıştırıldığı işlemin (genellikle ASP.NET veya ağ hizmeti) dizine yazma izni etkide bulunur.</span><span class="sxs-lookup"><span data-stu-id="8804a-129">Note that for the service to write to the directory you must make sure that the process under which the service is running, (typically ASP.NET or Network Service), has the permission to write to the directory.</span></span>  
  
```  
Fault: Reason = Invalid Argument: The second argument must not be zero.  
Fault: Reason = Invalid Argument: The argument must be greater than zero.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="8804a-130">Ayarlamak için derleme ve örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="8804a-130">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="8804a-131">Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="8804a-131">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="8804a-132">Çözümü derlemek için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="8804a-132">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="8804a-133">Error.txt dosyanın c:\logs dizinini oluşturduğunuz emin olun.</span><span class="sxs-lookup"><span data-stu-id="8804a-133">Ensure you have created the c:\logs directory for the error.txt file.</span></span> <span data-ttu-id="8804a-134">Veya kullanılan dosya adı değiştirme `CalculatorErrorHandler.HandleError`.</span><span class="sxs-lookup"><span data-stu-id="8804a-134">Or modify the file name used in `CalculatorErrorHandler.HandleError`.</span></span>  
  
4.  <span data-ttu-id="8804a-135">Tek veya çapraz makine yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="8804a-135">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="8804a-136">Örnekler, makinenizde zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="8804a-136">The samples may already be installed on your machine.</span></span> <span data-ttu-id="8804a-137">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="8804a-137">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="8804a-138">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="8804a-138">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="8804a-139">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="8804a-139">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\ErrorHandling`  
  
## <a name="see-also"></a><span data-ttu-id="8804a-140">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8804a-140">See Also</span></span>
