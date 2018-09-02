---
title: Using Deyimi Sorunlarını Önleme
ms.date: 03/30/2017
ms.assetid: aff82a8d-933d-4bdc-b0c2-c2f7527204fb
ms.openlocfilehash: 2c7534a56b2cc8fdc674242e135d70bec7f5017a
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43394704"
---
# <a name="avoiding-problems-with-the-using-statement"></a>Using Deyimi Sorunlarını Önleme
Bu örnek nasıl, C# "türü belirlenmiş istemci kullanırken kaynakları otomatik olarak temizlemek için using deyimi" kullanmamanız gösterir. Bu örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md) hesaplayıcı hizmet uygulayan. Bu örnekte, istemci bir konsol uygulaması (.exe) ve hizmet Internet Information Services (IIS) tarafından barındırılır.  
  
> [!NOTE]
>  Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.  
  
 Bu örnek iki C# "özel durumları sonra doğru şekilde temizler kod yanı sıra, belirlenmiş istemcileri ile using deyimi" kullanırken oluşan genel sorunları gösterir.  
  
 C# "using deyimi" sonuçları bir çağrıda `Dispose`(). Bu, aynı `Close`bir ağ hatası oluştuğunda, özel durumlar oluşturabilir (). Çünkü çağrısı `Dispose`() "kullanma" blok kapanış ayracı örtük olarak olur, bu özel durum büyük olasılıkla Git bilgisi dışında kod yazmak ve kodunuzu okuyan kişi tarafından kaynağıdır. Bu uygulama hatalarının olası bir kaynağı temsil eder.  
  
 Gösterilen ilk sorun `DemonstrateProblemUsingCanThrow` yöntemi olduğundan kapanış ayracı değil yürüttükten sonra kapanış küme ayracı ve kod özel durum oluşturur:  
  
```csharp   
using (CalculatorClient client = new CalculatorClient())  
{  
    ...  
} // <-- this line might throw  
Console.WriteLine("Hope this code wasn't important, because it might not happen.");  
```  
  
 Kullanarak içinde hiçbir şey engelleyecek bir özel durum veya içeriden kullanarak tüm özel durumları bile blok yakalanır, `Console.Writeline` nedeni aşağıdakiler olabilir değil örtük `Dispose`kapanış ayracı () çağrısında bir özel durum throw.  
  
 Gösterilen ikinci sorun `DemonstrateProblemUsingCanThrowAndMask` yöntemi olduğundan, bir özel durum kapanış ayracı başka bir uygulanır:  
  
```csharp   
using (CalculatorClient client = new CalculatorClient())  
{  
    ...  
    throw new ApplicationException("Hope this exception was not important, because "+  
                                   "it might be masked by the Close exception.");  
} // <-- this line might throw an exception.  
```  
  
 Çünkü `Dispose`() "finally" bloğun içinde gerçekleşir `ApplicationException` kullanarak dışında hiçbir zaman görülmedi bloke `Dispose`() başarısız olur. Kodun dışında ne zaman hakkında bilmeniz gerekir, `ApplicationException` ortaya "kullanarak" yapısı, bu özel durumun maskeleyerek sorunlarla karşılaşabilirsiniz.  
  
 Son olarak, örnek doğru olduğunda özel durumlar ortaya yukarı temizlemek nasıl gösterir `DemonstrateCleanupWithExceptions`. Bu bir try/catch bloğu hatalarını raporlamak ve çağrı kullanır `Abort`. Bkz: [beklenen özel durumlar](../../../../docs/framework/wcf/samples/expected-exceptions.md) istemci çağrılarının özel durumları yakalama hakkında daha fazla ayrıntı için örnek.  
  
```csharp   
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
>  Deyimi ServiceHost ile: çoğu kendi kendini barındıran uygulama biraz daha uzun bir hizmeti barındırma ve ServiceHost.Close söz konusu uygulamalar kullanarak güvenli bir şekilde kullanabilmeniz için bir özel durum nadiren oluşturur ServiceHost deyimiyle. Ancak ServiceHost.Close oluşturabilecek dikkat bir `CommunicationException`, uygulamanızın ServiceHost kapattıktan sonra devam ederse, kullanmaktan kaçınmanız gerekir böylece deyimi ve daha önce verilen desenle izleyin.  
  
 Örneği çalıştırdığınızda, işlem yanıtları ve özel durumlar istemci konsol penceresinde görüntülenir.  
  
 İstemci işlemi üç senaryo çalıştıran her çağırmak için hangi girişimleri `Divide`. İlk senaryoda adresinden bir özel durum nedeniyle atlandı kod gösterir `Dispose`(). İkinci senaryoda adresinden bir özel durum nedeniyle maskelenen önemli bir özel durum gösterir `Dispose`(). Üçüncü senaryo temizleme doğru gösterir.  
  
 İstemci işlemi beklenen çıktısı bulunmaktadır:  
  
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
  
### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örneği çalıştırma  
  
1.  Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Tek veya çapraz makine yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\UsingUsing`  
  
## <a name="see-also"></a>Ayrıca Bkz.
