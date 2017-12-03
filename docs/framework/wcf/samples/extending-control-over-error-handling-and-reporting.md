---
title: "Hata İşleme ve Bildirme Denetimini Genişletme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 45f996a7-fa00-45cb-9d6f-b368f5778aaa
caps.latest.revision: "28"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a4284f07a21a9bb176a78a8a2abefe7c7c7c6b66
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="extending-control-over-error-handling-and-reporting"></a>Hata İşleme ve Bildirme Denetimini Genişletme
Bu örnek hata işleme ve içinde hata bildirimi üzerinden denetimini genişletme yapmayı gösteren bir [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] kullanarak hizmet <xref:System.ServiceModel.Dispatcher.IErrorHandler> arabirimi. Örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md) hataları işlemek için hizmetine eklenen bazı ek kod. İstemci birkaç hata koşulları zorlar. Hizmet hataları yakalar ve bunları bir dosyasına kaydeder.  
  
> [!NOTE]
>  Kurulum yordamı ve yapı yönergeleri Bu örnek için bu konunun sonunda yer alır.  
  
 Hizmetleri müdahale hatalar, işlem gerçekleştirmek ve nasıl hataları bildirilen etkileyen kullanarak <xref:System.ServiceModel.Dispatcher.IErrorHandler> arabirimi. Arabirimin uygulanabilir iki yöntemi vardır: <xref:System.ServiceModel.Dispatcher.IErrorHandler.ProvideFault%28System.Exception%2CSystem.ServiceModel.Channels.MessageVersion%2CSystem.ServiceModel.Channels.Message%40%29> ve <xref:System.ServiceModel.Dispatcher.IErrorHandler.HandleError%2A>. <xref:System.ServiceModel.Dispatcher.IErrorHandler.ProvideFault%28System.Exception%2CSystem.ServiceModel.Channels.MessageVersion%2CSystem.ServiceModel.Channels.Message%40%29> Yöntemi ekleme, değiştirme ve yanıt bir özel durum olarak oluşturulan bir hata iletisi bastırmak olanak tanır. <xref:System.ServiceModel.Dispatcher.IErrorHandler.HandleError%2A> Yöntemi ek hata işleme çalıştırıp çalıştıramayacağını bir hata ve denetimleri durumunda gerçekleşmesi işlenirken hata verir.  
  
 Bu örnekte `CalculatorErrorHandler` yazın uygulayan <xref:System.ServiceModel.Dispatcher.IErrorHandler> arabirimi. İçinde  
  
 <xref:System.ServiceModel.Dispatcher.IErrorHandler.HandleError%2A>yöntemi, `CalculatorErrorHandler` c:\logs Error.txt metin dosyasında hata günlüğünü yazar. Örnek Hata günlüklerini ve, istemciye geri bildirilmesini izin veren engelleme unutmayın.  
  
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
  
 `ErrorBehaviorAttribute` Hata işleyicisine bir hizmete kaydolmak için bir mekanizma olarak bulunmaktadır. Bu öznitelik, bir tek tür parametresi alır. Türü uygulamalıdır <xref:System.ServiceModel.Dispatcher.IErrorHandler> arabirim ve genel, boş bir oluşturucuya sahip olması. Öznitelik, ardından bu olay işleyicisi türü bir örneğini başlatır ve hizmete yükler. Bunu uygulayarak yapar <xref:System.ServiceModel.Description.IServiceBehavior> arabirimi ve ardından kullanarak <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A> hizmete hata işleyicisine örneklerini ekleme yöntemi.  
  
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
  
 Örnek hesaplayıcı hizmeti uygular. İstemci kasıtlı olarak iki hatalar geçersiz değerlerle parametreleri sağlayarak hizmette oluşmasına neden olur. `CalculatorErrorHandler` Kullanan <xref:System.ServiceModel.Dispatcher.IErrorHandler> yerel bir dosyaya hataları günlüğe kaydetmek için arabirim ve bunları istemciye geri bildirilmesini sağlar. İstemci bir sıfıra bölünme sıfır ve aralığın bağımsız değişkeni çıkış koşulu zorlar.  
  
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
  
 Örneği çalıştırdığınızda, işlem isteklerini ve yanıtlarını istemci konsol penceresinde görüntülenir. Sıfır ve hataları rapor edilen aralığın bağımsız değişkeni çıkış koşulları bölme bakın. İstemcisi penceresinde istemciyi aşağı kapatmak için ENTER tuşuna basın.  
  
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
  
 Dosya c:\logs\errors.txt hataları hakkında hizmeti tarafından günlüğe kaydedilen bilgi içerir. Hizmetin emin olmanız gerekir dizine yazma için hizmet çalıştırıldığı işlemin (genellikle ASP.NET veya ağ hizmeti), dizine yazma izni etkilemez.  
  
```  
Fault: Reason = Invalid Argument: The second argument must not be zero.  
Fault: Reason = Invalid Argument: The argument must be greater than zero.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örnek çalıştırın  
  
1.  Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Çözümü derlemek için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Error.txt dosyası için c:\logs dizin oluşturdunuz. emin olun. Ya da kullanılan dosya adı değiştirmek `CalculatorErrorHandler.HandleError`.  
  
4.  Tek veya çapraz makine yapılandırmada örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\ErrorHandling`  
  
## <a name="see-also"></a>Ayrıca Bkz.
