---
title: "Beklenen Özel Durumlar"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 299a6987-ae6b-43c6-987f-12b034b583ae
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 77ddddd51229712f85bc780889169e159c1c83e8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="expected-exceptions"></a>Beklenen Özel Durumlar
Bu örnek, bir türü belirlenmiş istemci kullanırken beklenen özel durumları yakalamak gösterilmiştir. Bu örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md) hesap makinesi hizmetinin uygular. Bu örnekte, istemci bir konsol uygulaması (.exe) ve Internet Information Services (IIS) tarafından barındırılan hizmetindeki.  
  
> [!NOTE]
>  Kurulum yordamı ve yapı yönergeleri Bu örnek için bu konunun sonunda yer alır.  
  
 Bu örnek yakalama gösterir ve programları düzeltmek iki beklenen özel durum türleri işleme gerekir işlemek: `TimeoutException` ve `CommunicationException`.  
  
 İletişim yöntemleri oluşturulan özel durumlar bir [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] istemci beklenen veya beklenmeyen. Beklenmeyen özel durumları içerecek yıkıcı hataları gibi `OutOfMemoryException` ve programlama hataları `ArgumentNullException` veya `InvalidOperationException`. Genellikle beklenmeyen hataları, bu nedenle genellikle, değil catch bunları çağrılırken işlemek için kullanışlı bir yolu yoktur bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] istemci iletişim yönteminin.  
  
 Özel durumlar iletişim yöntemleri beklenen bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] istemcisini içeren `TimeoutException`, `CommunicationException`, ve herhangi bir türetilmiş sınıf `CommunicationException`. Bunlar güvenli bir şekilde durduruluyor tarafından işlenebilir iletişimi sırasında bir sorun gösterir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] istemci ve bir iletişim hatası raporlama. Herhangi bir uygulamada dış etkenler bu hataların neden olabileceğinden, doğru uygulamaları bu özel durumları yakalamak ve bunlar ortaya çıktığında kurtarın.  
  
 Birkaç türetilmiş sınıfları vardır `CommunicationException` , bir istemci atabilirsiniz. Bazı durumlarda, uygulamaların da özel işleme yapın, ancak diğer kişilerin olarak işlenmesine izin vermek için bunlardan bazıları catch bir `CommunicationException`. Bu ayrıntılı özel durum türü ilk yakalama ve ardından Yakalama gerçekleştirilebilir `CommunicationException` bir sonraki catch yan tümcesinde.  
  
 İstemci iletişim yöntemini çağıran kodu gerekir catch `TimeoutException` ve `CommunicationException`. Bu tür hataları işlemek için bir istemci iptal etmek ve iletişim hatası rapor yoludur.  
  
```  
try  
{  
    ...  
    double result = client.Add(value1, value2);  
    ...  
    client.Close();  
}  
catch (TimeoutException exception)  
{  
    Console.WriteLine("Got {0}", exception.GetType());  
    client.Abort();  
}  
catch (CommunicationException exception)  
{  
    Console.WriteLine("Got {0}", exception.GetType());  
    client.Abort();  
}  
```  
  
 Beklenen bir özel durum oluşursa, istemci olabilir veya daha sonra kullanılamayabilir. İstemci hala kullanılabilir olup olmadığını belirlemek için kontrol `State` özelliği `CommunicationState`. Açılır. Sonra hala açılırsa, hala kullanılabilir durumda değil. Aksi takdirde istemci iptal etmek ve tüm başvurularını serbest bırakın.  
  
> [!CAUTION]
>  Bir oturum sahip istemciler genellikle artık özel durumdan sonra kullanılabilir ve bir oturum olmayan istemciler hala genellikle özel durumdan sonra kullanılabilir gözlemleyebilirsiniz. Ancak, hiçbirini garanti, bunu istemci uygulamanız denetlemelidir özel durumdan sonra kullanmaya devam etmek denemek istiyorsanız `State` bir istemci özelliğini hala açık.  
  
 Örneği çalıştırdığınızda, özel durumlar ve işlem yanıtları istemci konsol penceresinde görüntülenir.  
  
 İki senaryo, istemci işlemini çalıştıran her hangi aranır `Add` arkasından `Divide`. İlk senaryoda, istemci iptal etme çağrısı yapmadan önce bir ağ sorunu taklit eder `Divide`. İkinci senaryo, zaman aşımı tamamlanması için çok yöntemi ayarlayarak bir zaman aşımı koşulu neden olur. İstemci işlemi beklenen çıktısı şöyledir:  
  
```  
Add(100,15.99) = 115.99  
Simulated network problem occurs...  
Got System.ServiceModel.CommunicationObjectAbortedException  
Add(100,15.99) = 115.99  
Set timeout too short for method to complete...  
Got System.TimeoutException  
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
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\ExpectedExceptions`  
  
## <a name="see-also"></a>Ayrıca Bkz.
