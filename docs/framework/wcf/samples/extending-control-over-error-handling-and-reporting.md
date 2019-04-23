---
title: Hata İşleme ve Bildirme Denetimini Genişletme
ms.date: 03/30/2017
ms.assetid: 45f996a7-fa00-45cb-9d6f-b368f5778aaa
ms.openlocfilehash: 4a12ab62a9ec25d207a88b041bcdf498eaff7228
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59303212"
---
# <a name="extending-control-over-error-handling-and-reporting"></a>Hata İşleme ve Bildirme Denetimini Genişletme
Bu örnek nasıl hata işleme ve hata raporlama kullanarak bir Windows Communication Foundation (WCF) hizmet üzerinde denetim genişletileceğini gösterir <xref:System.ServiceModel.Dispatcher.IErrorHandler> arabirimi. Örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md) hataları işlemek için hizmetine eklenen bazı ek kod. İstemci, birden çok hata koşulları zorlar. Hizmet hataları yakalar ve bunları bir dosyaya kaydeder.  
  
> [!NOTE]
>  Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.  
  
 Hizmetleri ıntercept hataları, işleme gerçekleştirmek ve hataları nasıl bildirildiğini etkileyen kullanarak <xref:System.ServiceModel.Dispatcher.IErrorHandler> arabirimi. Arabirimin uygulanabilir iki yöntemi vardır: <xref:System.ServiceModel.Dispatcher.IErrorHandler.ProvideFault%28System.Exception%2CSystem.ServiceModel.Channels.MessageVersion%2CSystem.ServiceModel.Channels.Message%40%29> ve <xref:System.ServiceModel.Dispatcher.IErrorHandler.HandleError%2A>. <xref:System.ServiceModel.Dispatcher.IErrorHandler.ProvideFault%28System.Exception%2CSystem.ServiceModel.Channels.MessageVersion%2CSystem.ServiceModel.Channels.Message%40%29> Yöntemi ekleme, değiştirme veya yanıt olarak bir özel durum oluşturan bir hata iletisi gösterme olanak tanır. <xref:System.ServiceModel.Dispatcher.IErrorHandler.HandleError%2A> Yöntemi ek hata işleme çalıştırıp çalıştıramayacağını hata ve denetimleri olması durumunda gerçekleşmesi hata işleme sağlar.  
  
 Bu örnekte `CalculatorErrorHandler` yazın uygular <xref:System.ServiceModel.Dispatcher.IErrorHandler> arabirimi. İçinde  
  
 <xref:System.ServiceModel.Dispatcher.IErrorHandler.HandleError%2A> yöntemi, `CalculatorErrorHandler` hata günlüğünü c:\logs Error.txt bir metin dosyasına yazar. Örnek Hata günlüklerini ve, istemciye yeniden bildirilmesine izin veren engellemez unutmayın.  
  
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
  
 `ErrorBehaviorAttribute` Hizmeti ile bir hata işleyicisini kaydetmek için bir mekanizma olarak bulunmaktadır. Bu öznitelik, bir tek tür parametresi alır. Tür uygulamalıdır <xref:System.ServiceModel.Dispatcher.IErrorHandler> arabirimi ve ortak, boş bir oluşturucusu olmalıdır. Özniteliği, hata işleyicisi türü bir örneğini başlatır ve hizmete yüklenir. Bunu uygulayarak yapar <xref:System.ServiceModel.Description.IServiceBehavior> arabirimi ve ardından kullanarak <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A> hizmetine hata işleyicisini örneklerini eklemek için yöntemi.  
  
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
  
 Örnek hesaplayıcı hizmet uygular. İstemci, kasıtlı olarak geçersiz değerlerle parametreleri sağlayarak hizmeti üzerinde gerçekleşmesi iki hatalarına neden olur. `CalculatorErrorHandler` Kullanan <xref:System.ServiceModel.Dispatcher.IErrorHandler> yerel bir dosyaya hataları günlüğe kaydetmek için arabirim ve bunları istemciye geri bildirilmesini sağlar. İstemci, sıfır hem de aralık, bağımsız değişkeni çıkış koşulu ile bir bölme zorlar.  
  
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
  
 Örneği çalıştırdığınızda, işlem isteklerini ve yanıtlarını istemci konsol penceresinde görüntülenir. Sıfır ve hataları bildirilen aralığı, bağımsız değişkeni çıkış koşulları bölme görürsünüz. İstemci bilgisayarı için istemci penceresinde ENTER tuşuna basın.  
  
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
  
 Dosya c:\logs\errors.txt hizmet tarafından günlüğüne hatalar hakkında bilgileri içerir. Hizmet emin olmanız gerekir dizine yazmak hizmetin çalıştırıldığı işlemin (genellikle ASP.NET veya ağ hizmeti) dizine yazma izni etkide bulunur.  
  
```  
Fault: Reason = Invalid Argument: The second argument must not be zero.  
Fault: Reason = Invalid Argument: The argument must be greater than zero.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örneği çalıştırma  
  
1. Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Çözümü derlemek için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Error.txt dosyanın c:\logs dizinini oluşturduğunuz emin olun. Veya kullanılan dosya adı değiştirme `CalculatorErrorHandler.HandleError`.  
  
4. Tek veya çapraz makine yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\ErrorHandling`  
