---
title: Hata İşleme ve Bildirme Denetimini Genişletme
ms.date: 03/30/2017
ms.assetid: 45f996a7-fa00-45cb-9d6f-b368f5778aaa
ms.openlocfilehash: 68f3381e8db9d7c0222720dda335b47e30f57ac7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183675"
---
# <a name="extending-control-over-error-handling-and-reporting"></a>Hata İşleme ve Bildirme Denetimini Genişletme
Bu örnek, arabirimi kullanarak bir Windows Communication Foundation (WCF) hizmetinde <xref:System.ServiceModel.Dispatcher.IErrorHandler> hata işleme ve hata raporlama denetiminin nasıl genişletilebildiğini göstermektedir. Örnek, hataları işlemek için hizmete eklenen bazı ek kodla [Başlarken'e](../../../../docs/framework/wcf/samples/getting-started-sample.md) dayanır. İstemci birkaç hata koşulu zorlar. Hizmet hataları yakalar ve bunları bir dosyada kaydeder.  
  
> [!NOTE]
> Bu örnek için kurulum yordamı ve yapı yönergeleri bu konunun sonunda yer alır.  
  
 Hizmetler hataları engelleyebilir, işleme gerçekleştirebilir ve arabirimi kullanarak hataların nasıl raporlanınbildirildiğini <xref:System.ServiceModel.Dispatcher.IErrorHandler> etkileyebilir. Arabirimde uygulanabilecek iki yöntem <xref:System.ServiceModel.Dispatcher.IErrorHandler.ProvideFault%28System.Exception%2CSystem.ServiceModel.Channels.MessageVersion%2CSystem.ServiceModel.Channels.Message%40%29> vardır: ve <xref:System.ServiceModel.Dispatcher.IErrorHandler.HandleError%2A>. Yöntem, <xref:System.ServiceModel.Dispatcher.IErrorHandler.ProvideFault%28System.Exception%2CSystem.ServiceModel.Channels.MessageVersion%2CSystem.ServiceModel.Channels.Message%40%29> bir özel durum yanıt olarak oluşturulan bir hata iletisi eklemenize, değiştirmenize veya bastırmanıza olanak tanır. Yöntem, <xref:System.ServiceModel.Dispatcher.IErrorHandler.HandleError%2A> bir hata durumunda hata işlemenin gerçekleşmesine izin verir ve ek hata işlemenin çalışıp çalışmayacağını denetler.  
  
 Bu örnekte, `CalculatorErrorHandler` tür <xref:System.ServiceModel.Dispatcher.IErrorHandler> arabirimi uygular. İçinde  
  
 <xref:System.ServiceModel.Dispatcher.IErrorHandler.HandleError%2A>yöntem, `CalculatorErrorHandler` c:\logs bir Hata.txt metin dosyasına hata nın bir günlük yazar. Örnek hatayı günlüğe kaydettiğini ve bu hatayı bastırmadığını ve istemciye geri bildirilmesine izin verdiğini unutmayın.  
  
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
  
 Bir `ErrorBehaviorAttribute` hata işleyicisini bir hizmete kaydetmek için bir mekanizma olarak var. Bu öznitelik tek bir tür parametresi alır. Bu tür <xref:System.ServiceModel.Dispatcher.IErrorHandler> arabirimi uygulamalı ve ortak, boş bir oluşturucu olmalıdır. Öznitelik daha sonra bu hata işleyicisi türübir örnek anında ve hizmete yükler. Bunu, <xref:System.ServiceModel.Description.IServiceBehavior> arabirimi uygulayarak ve ardından <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A> hizmete hata işleyicisi örneklerini eklemek için yöntemi kullanarak yapar.  
  
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
  
 Örnek bir hesap makinesi hizmeti uygular. İstemci, parametreleri yasadışı değerlerle sağlayarak hizmette kasıtlı olarak iki hata oluşmasına neden olur. Hatalarını `CalculatorErrorHandler` <xref:System.ServiceModel.Dispatcher.IErrorHandler> yerel bir dosyaya günlüğe kaydetmek için arabirimi kullanır ve ardından istemciye geri bildirilmesine olanak tanır. İstemci bir bayrılığı sıfıra ve kapsama alanı dışında bir koşula zorlar.  
  
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
  
 Örneği çalıştırdığınızda, işlem istekleri ve yanıtları istemci konsol penceresinde görüntülenir. Bölünmeyi sıfıra göre görürsünüz ve aralık dışı bağımsız değişken koşulları hata olarak bildirilir. İstemciyi kapatmak için istemci penceresinde ENTER tuşuna basın.  
  
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
  
 c:\logs\errors.txt dosyası, hizmetin hataları hakkında günlüğe kaydedilen bilgileri içerir. Hizmetin dizine yazabilmesi için, hizmetin (genellikle ASP.NET veya Ağ Hizmeti) çalıştırıldığı işlemin dizine yazma izni olduğundan emin olmalısınız.  
  
```txt
Fault: Reason = Invalid Argument: The second argument must not be zero.  
Fault: Reason = Invalid Argument: The argument must be greater than zero.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, oluşturmak ve çalıştırmak için  
  
1. Windows Communication Foundation [Samples için Tek Seferlik Kurulum Yordamı'nı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizi emin olun.  
  
2. Çözümü oluşturmak için, Windows [Communication Foundation Samples'i oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.  
  
3. hata.txt dosyası için c:\logs dizinini oluşturduğunuzdan emin olun. Veya kullanılan dosya adını `CalculatorErrorHandler.HandleError`değiştirin.  
  
4. Örneği tek veya çapraz makine yapılandırmasında çalıştırmak için, [Windows Communication Foundation Samples'ı çalıştıran](../../../../docs/framework/wcf/samples/running-the-samples.md)yönergeleri izleyin.  
  
> [!IMPORTANT]
> Numuneler makinenize zaten yüklenmiş olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek aşağıdaki dizinde yer almaktadır.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\ErrorHandling`  
