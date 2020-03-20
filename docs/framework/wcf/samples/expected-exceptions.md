---
title: Beklenen Özel Durumlar
ms.date: 03/30/2017
ms.assetid: 299a6987-ae6b-43c6-987f-12b034b583ae
ms.openlocfilehash: f250e526b528adf0b67365ceb07f13e4087d773d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144715"
---
# <a name="expected-exceptions"></a>Beklenen Özel Durumlar
Bu örnek, yazılı istemci kullanırken beklenen özel durumların nasıl yakaılacağını gösterir. Bu örnek, bir hesap makinesi hizmeti uygulayan [Başlarken'e](../../../../docs/framework/wcf/samples/getting-started-sample.md) dayanır. Bu örnekte, istemci bir konsol uygulamasıdır (.exe) ve hizmet Internet Information Services (IIS) tarafından barındırılır.  
  
> [!NOTE]
> Bu örnek için kurulum yordamı ve yapı yönergeleri bu konunun sonunda yer alır.  
  
 Bu örnek, doğru programların işlemesi gereken beklenen iki `TimeoutException` `CommunicationException`özel durum türünü yakalamayı ve işlemeyi gösterir: ve.  
  
 Windows Communication Foundation (WCF) istemcisindeki iletişim yöntemlerinden atılan özel durumlar beklenen veya beklenmeyen durumlardır. Beklenmeyen özel durumlar gibi `OutOfMemoryException` felaket hataları ve `ArgumentNullException` `InvalidOperationException`programlama hataları içerir. Genellikle beklenmeyen hataları işlemek için yararlı bir yol yoktur, bu nedenle genellikle bir WCF istemci iletişim yöntemi ni ararken bunları yakalamamalısınız.  
  
 WCF istemcisindeki iletişim yöntemlerinden `TimeoutException` `CommunicationException`beklenen özel durumlar `CommunicationException`, ve türetilmiş herhangi bir sınıf . Bunlar, WCF istemcisinin iptali ve bir iletişim hatası bildirilmesi yle güvenli bir şekilde işlenebilen iletişim sırasında ki bir sorunu gösterir. Dış etkenler herhangi bir uygulamada bu hatalara neden olabileceğinden, doğru uygulamaların bu özel durumları yakalaması ve oluştuğunda kurtarması gerekir.  
  
 Bir istemcinin `CommunicationException` atabileceği birkaç türemiş sınıf vardır. Bazı durumlarda, uygulamalar da özel işleme yapmak için bunlardan bazılarını yakalamak, `CommunicationException`ancak diğerleri olarak ele alınmasını sağlar . Bu, önce daha özel özel özel durum türünü `CommunicationException` yakalayarak ve daha sonra daha sonra catch-clause'da yakalayarak gerçekleştirilebilir.  
  
 İstemci iletişim yöntemiçağıran kod `TimeoutException` `CommunicationException`yakalamak gerekir ve . Bu tür hataları işlemek için bir yolu istemci iptal etmek ve iletişim hatası rapor etmektir.  
  
```csharp
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
  
 Beklenen bir özel durum oluşursa, istemci daha sonra kullanılabilir olabilir veya olmayabilir. İstemcinin hala kullanılabilir olup olmadığını `State` belirlemek `CommunicationState`için özelliğin. Açıldı. Hala açılırsa, o zaman hala kullanılabilir. Aksi takdirde istemciyi iptal etmeli ve tüm başvuruları serbest bırakmalısınız.  
  
> [!CAUTION]
> Oturumu olan istemcilerin genellikle bir özel durum sonrasında artık kullanılabilir olmadığını ve oturumu olmayan istemcilerin genellikle bir özel durum sonra da kullanılabilir olduğunu gözlemleyebilirsiniz. Ancak, bunların hiçbiri garanti değildir, bu nedenle bir özel durum sonra istemci kullanmaya `State` devam etmek istiyorsanız, uygulamanız istemci hala açık olduğunu doğrulamak için özelliği kontrol etmelidir.  
  
 Örneği çalıştırdığınızda, işlem yanıtları ve özel durumlar istemci konsol penceresinde görüntülenir.  
  
 İstem işlemi, her biri çağırılan `Add` iki `Divide`senaryo çalıştırır. İlk senaryo, aramayı yapmadan önce istemciyi iptal ederek bir `Divide`ağ sorununu simüle eder. İkinci senaryo, yöntemin tamamlanması için çok kısa zaman ayarı yaparak bir zaman ayarı durumuna neden olur. İstemci işleminden beklenen çıktı:  
  
```output
Add(100,15.99) = 115.99  
Simulated network problem occurs...  
Got System.ServiceModel.CommunicationObjectAbortedException  
Add(100,15.99) = 115.99  
Set timeout too short for method to complete...  
Got System.TimeoutException  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, oluşturmak ve çalıştırmak için  
  
1. Windows Communication Foundation [Samples için Tek Seferlik Kurulum Yordamı'nı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizi emin olun.  
  
2. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak [için, Windows Communication Foundation Samples'i oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.  
  
3. Örneği tek veya çapraz makine yapılandırmasında çalıştırmak için, [Windows Communication Foundation Samples'ı çalıştıran](../../../../docs/framework/wcf/samples/running-the-samples.md)yönergeleri izleyin.  
  
> [!IMPORTANT]
> Numuneler makinenize zaten yüklenmiş olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek aşağıdaki dizinde yer almaktadır.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\ExpectedExceptions`  
