---
title: "Using Deyimi Sorunlarını Önleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: aff82a8d-933d-4bdc-b0c2-c2f7527204fb
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 123081683f122f68fded94aed5735d7058496366
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="avoiding-problems-with-the-using-statement"></a>Using Deyimi Sorunlarını Önleme
Bu örnek nasıl, C# "türü belirlenmiş istemci kullanırken kaynakları otomatik olarak temizlemek için using deyimi" kullanmamanız gösterir. Bu örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md) hesap makinesi hizmetinin uygular. Bu örnekte, istemci bir konsol uygulaması (.exe) ve Internet Information Services (IIS) tarafından barındırılan hizmetindeki.  
  
> [!NOTE]
>  Kurulum yordamı ve yapı yönergeleri Bu örnek için bu konunun sonunda yer alır.  
  
 Bu örnek iki C# "deyimi yazılan istemcileri gibi özel durumlar sonra doğru bir şekilde temizler kodu kullanarak" kullanırken oluşan genel sorunları gösterir.  
  
 C# "deyimi kullanarak" sonuçları çağrıda `Dispose`(). Bu aynı sonucu verir `Close`bir ağ hatası oluştuğunda, özel durumlar oluşturma (). Çünkü çağrısı `Dispose`() olur dolaylı olarak "kullanarak" blok kapanış ayracı, bu özel durumlar olasılıkla Git bilgisi dışında her ikisi için de kod yazma ve kodu okuyan kişilerin kaynağıdır. Bu uygulama hatalarının olası bir kaynağı temsil eder.  
  
 Gösterilen ilk sorun `DemonstrateProblemUsingCanThrow` yöntemidir kapanış ayracı değil yürüttükten sonra kapanış ayracı bir özel durum ve kod oluşturur:  
  
```  
using (CalculatorClient client = new CalculatorClient())  
{  
    ...  
} // <-- this line might throw  
Console.WriteLine("Hope this code wasn't important, because it might not happen.");  
```  
  
 Nothing using içinde engelleme olsa bile bir özel durum ya da kullanarak içindeki tüm özel durumları blok yakalandı, `Console.Writeline` nedeniyle gerçekleşebilir değil örtük `Dispose`kapanış ayracı () çağrısı bir özel durum.  
  
 Gösterilen ikinci sorun `DemonstrateProblemUsingCanThrowAndMask` yöntemidir, bir özel durum atma kapanış ayracı, başka bir uygulanır:  
  
```  
using (CalculatorClient client = new CalculatorClient())  
{  
    ...  
    throw new ApplicationException("Hope this exception was not important, because "+  
                                   "it might be masked by the Close exception.");  
} // <-- this line might throw an exception.  
```  
  
 Çünkü `Dispose`() oluşur bir "son" bloğunun içine, `ApplicationException` kullanarak dışında hiçbir zaman görülür bloke `Dispose`() başarısız. Kod dışında ne zaman hakkında bilmeniz gerekir, `ApplicationException` oluşur, bu özel durumun maskeleyerek "kullanarak" yapı sorunlarla karşılaşabilirsiniz.  
  
 Son olarak, örnek doğru olduğunda özel durumlar ortaya yukarı temizlemeyi gösteren `DemonstrateCleanupWithExceptions`. Bu rapor hataları ve arama için bir try/catch bloğu kullanır `Abort`. Bkz: [beklenen özel durumlar](../../../../docs/framework/wcf/samples/expected-exceptions.md) istemci aramalardan özel durumları yakalama hakkında daha fazla ayrıntı için örnek.  
  
```  
try  
{  
    ...  
    client.Close();  
}  
catch (CommunicationException e)  
{  
    ...  
    client.Abort();  
}  
catch (TimeoutException e)  
{  
    ...  
    client.Abort();  
}  
catch (Exception e)  
{  
    ...  
    client.Abort();  
    throw;  
}  
```  
  
> [!NOTE]
>  Deyimi ve ServiceHost kullanarak: birçok kendi kendine barındırma uygulama biraz birden fazla hizmet barındırma ve ServiceHost.Close kullanarak bu tür uygulamalar güvenli bir şekilde kullanabilmeniz için bir özel durum nadiren oluşturur ServiceHost deyimiyle. Ancak, ServiceHost.Close atabilirsiniz unutmayın bir `CommunicationException`, uygulamanızın ServiceHost kapattıktan sonra devam ederse, yapmaktan kaçınmalısınız deyimi ve daha önce verilen desenle izleyin.  
  
 Örneği çalıştırdığınızda, özel durumlar ve işlem yanıtları istemci konsol penceresinde görüntülenir.  
  
 Üç senaryo, istemci işlemini çalıştıran her hangi aranır `Divide`. İlk senaryoda özel durumu nedeniyle geçiliyor kodu gösterir `Dispose`(). İkinci senaryo özel durumu nedeniyle maskelenen önemli bir özel durum gösterir `Dispose`(). Üçüncü senaryo temizleme doğru gösterir.  
  
 İstemci işlemi beklenen çıktısı şöyledir:  
  
```  
=  
= Demonstrating problem:  closing brace of using statement can throw.  
=  
Got System.ServiceModel.CommunicationException from Divide.  
Got System.ServiceModel.Security.MessageSecurityException  
=  
= Demonstrating problem:  closing brace of using statement can mask other Exceptions.  
=  
Got System.ServiceModel.CommunicationException from Divide.  
Got System.ServiceModel.Security.MessageSecurityException  
=  
= Demonstrating cleanup with Exceptions.  
=  
Calling client.Add(0.0, 0.0);  
        client.Add(0.0, 0.0); returned 0  
Calling client.Divide(0.0, 0.0);  
Got System.ServiceModel.CommunicationException from Divide.  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örnek çalıştırın  
  
1.  Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Tek veya çapraz makine yapılandırmada örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\UsingUsing`  
  
## <a name="see-also"></a>Ayrıca Bkz.
