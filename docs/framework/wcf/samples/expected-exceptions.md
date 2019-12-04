---
title: Beklenen Özel Durumlar
ms.date: 03/30/2017
ms.assetid: 299a6987-ae6b-43c6-987f-12b034b583ae
ms.openlocfilehash: 24bb9b483a3f26241f895d68b763a1974b02151b
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74716449"
---
# <a name="expected-exceptions"></a>Beklenen Özel Durumlar
Bu örnek, yazılan bir istemci kullanılırken beklenen özel durumların nasıl yakalanacağını gösterir. Bu örnek, bir Hesaplayıcı hizmeti uygulayan [kullanmaya](../../../../docs/framework/wcf/samples/getting-started-sample.md) Başlarken hizmetini temel alır. Bu örnekte, istemci bir konsol uygulaması (. exe) ve hizmet Internet Information Services (IIS) tarafından barındırılır.  
  
> [!NOTE]
> Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.  
  
 Bu örnek, doğru programların işlenmesi gereken iki beklenen özel durum türünü yakalama ve işlemeyi gösterir: `TimeoutException` ve `CommunicationException`.  
  
 Windows Communication Foundation (WCF) istemcisinde iletişim yöntemlerinden oluşturulan özel durumlar bekleniyor veya beklenmiyor. Beklenmeyen özel durumlar, `OutOfMemoryException` ve `ArgumentNullException` veya `InvalidOperationException`gibi programlama hataları gibi çok zararlı hatalara sahiptir. Genellikle beklenmeyen hataları işlemenin yararlı bir yolu yoktur, bu nedenle genellikle WCF istemci iletişim yöntemini çağırırken bunları yakalamayın.  
  
 Bir WCF istemcisinde iletişim yöntemlerinden beklenen özel durumlar, `TimeoutException`, `CommunicationException`ve `CommunicationException`türetilmiş tüm sınıflarını içerir. Bu, WCF istemcisini iptal ederek ve bir iletişim hatası bildirerek güvenli bir şekilde işlenebilen iletişim sırasında bir sorun olduğunu gösterir. Dış faktörler herhangi bir uygulamada bu hatalara neden olabileceğinden, doğru uygulamalar bu özel durumları yakalamalı ve oluştuğunda kurtarmalıdır.  
  
 Bir istemcinin oluşturbileceği birkaç türetilmiş `CommunicationException` sınıfı vardır. Bazı durumlarda, uygulamalar özel işlem yapmak için bunlardan bazılarını da yakalar, ancak diğerlerinin `CommunicationException`olarak işlenmesine izin verir. Bu, önce daha özel bir özel durum türü yakalayıp sonra `CommunicationException` daha sonra bir catch yan tümcesinde yakalanarak gerçekleştirilebilir.  
  
 İstemci iletişim yöntemini çağıran kodun `TimeoutException` ve `CommunicationException`yakalamalı olması gerekir. Bu tür hataları işlemenin bir yolu, istemciyi durdurmak ve iletişim başarısızlığını raporlamak olur.  
  
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
  
 Beklenen bir özel durum oluşursa, istemci daha sonra kullanılabilir olmayabilir veya olmayabilir. İstemcinin hala kullanılabilir olup olmadığını anlamak için `State` özelliğinin `CommunicationState`olup olmadığını kontrol edin. Makta. Hala açılırsa, hala kullanılabilir olur. Aksi takdirde, istemciyi iptal etmeniz ve tüm başvurularını serbest bırakmanız gerekir.  
  
> [!CAUTION]
> Bir oturumun bulunduğu istemciler genellikle özel bir durum sonrasında artık kullanılamaz ve bir oturumu olmayan istemciler genellikle bir özel durumla sonra hala kullanılabilir. Ancak, bunlardan hiçbiri garanti edilmez, bu nedenle istemciyi kullanmaya devam etmeyi denemek istiyorsanız, uygulamanızın hala açık olduğunu doğrulamak için `State` özelliğini denetlemesi gerekir.  
  
 Örneği çalıştırdığınızda, işlem yanıtları ve özel durumlar istemci konsol penceresinde görüntülenir.  
  
 İstemci işlemi, her biri `Add` ve ardından `Divide`tarafından her bir çağrı girişiminde bulunan iki senaryo çalıştırır. İlk senaryo, `Divide`çağrısı yapmadan önce istemciyi iptal ederek bir ağ sorununun benzetimini yapar. İkinci senaryo, yöntemin tamamlanabilmesi için çok kısa süre sonu ayarlayarak zaman aşımı koşuluna neden olur. İstemci işlemindeki beklenen çıkış:  
  
```output
Add(100,15.99) = 115.99  
Simulated network problem occurs...  
Got System.ServiceModel.CommunicationObjectAbortedException  
Add(100,15.99) = 115.99  
Set timeout too short for method to complete...  
Got System.TimeoutException  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için  
  
1. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.  
  
2. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak Için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)konusundaki yönergeleri izleyin.  
  
3. Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md)bölümündeki yönergeleri izleyin.  
  
> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek, aşağıdaki dizinde bulunur.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\ExpectedExceptions`  
