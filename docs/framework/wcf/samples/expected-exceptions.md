---
title: Beklenen Özel Durumlar
ms.date: 03/30/2017
ms.assetid: 299a6987-ae6b-43c6-987f-12b034b583ae
ms.openlocfilehash: 3add9faa9a07249639c1ff3e83469d0634008472
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61990203"
---
# <a name="expected-exceptions"></a>Beklenen Özel Durumlar
Bu örnek, türü belirlenmiş istemci kullanırken beklenen özel durumları yakalamak nasıl gösterir. Bu örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md) hesaplayıcı hizmet uygulayan. Bu örnekte, istemci bir konsol uygulaması (.exe) ve hizmet Internet Information Services (IIS) tarafından barındırılır.  
  
> [!NOTE]
>  Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.  
  
 Bu örnek, yakalama gösterir ve programlar düzeltmek iki beklenen özel durum türlerini işleme gerekir işlemek: `TimeoutException` ve `CommunicationException`.  
  
 Bir Windows Communication Foundation (WCF) istemcisi üzerinde iletişim yöntemlerinden oluşan özel durumlar, beklenen ya da beklenmeyen. Beklenmeyen özel durumları içerecek gibi yıkıcı hataları `OutOfMemoryException` ve programlama hatalarını `ArgumentNullException` veya `InvalidOperationException`. Genellikle beklenmeyen hatalar, bu nedenle genellikle, bunları bir WCF istemci iletişim yöntemini çağırırken yakalamalısınız değil işlemek için kullanışlı bir yolu yoktur.  
  
 Bir WCF istemcisi üzerinde iletişim yöntemlerinden özel durumları içerecek beklenen `TimeoutException`, `CommunicationException`, ve herhangi bir türetilmiş sınıf `CommunicationException`. Bunlar, WCF istemcisini iptal ediliyor ve bir iletişim hatası raporlama güvenli bir şekilde işlenebilir iletişimi sırasında bir sorun gösterir. Herhangi bir uygulamada dış etkenler bu hataların neden olabileceğinden, doğru uygulamaları bu özel durumları yakalama ve ortaya çıkan kurtarma gerekir.  
  
 Türetilmiş sınıfları yok `CommunicationException` istemci oluşturabilecek. Bazı durumlarda, uygulamaların da bazı özel işlem yapın, ancak diğerleri olarak işleneceğini izin için catch bir `CommunicationException`. Bu ayrıntılı özel durum türü ilk yakalama ve ardından yakalamak gerçekleştirilebilir `CommunicationException` daha sonraki bir catch yan tümcesinde.  
  
 İstemci iletişim yöntemini çağıran kod gerekir catch `TimeoutException` ve `CommunicationException`. Bu tür hataları işlemek için bir yol, istemci durdurmak ve iletişim hatası göstermektir.  
  
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
  
 Beklenen bir özel durum oluşursa, istemci olabilir veya daha sonra kullanılamayabilir. İstemci hala kullanılabilir olup olmadığını belirlemek için kontrol `State` özelliği `CommunicationState`. Açılır. Ardından hala açık değilse, yine de kullanılabilir. Aksi takdirde istemci iptal etmek ve tüm başvuruları bırakın.  
  
> [!CAUTION]
>  Bir oturuma sahip istemciler artık genellikle bir özel durumdan sonra kullanılabilir ve bir oturuma sahip olmayan istemciler hala özel durumdan sonra kullanılabilir mümkün. Ancak, bunlar garanti edilir, bunu istemci uygulamanızı denetlemelidir özel durumdan sonra kullanmaya devam etmek denemek istiyorsanız `State` özelliği istemci doğrulamak için yine de açılır.  
  
 Örneği çalıştırdığınızda, işlem yanıtları ve özel durumlar istemci konsol penceresinde görüntülenir.  
  
 İki senaryo, istemci işlemini çalıştıran her çağırmak için hangi girişimleri `Add` ardından `Divide`. İlk senaryoda, istemci tarafından iptal ediliyor çağrı yapmadan önce bir ağ sorunu benzetimini yapar `Divide`. İkinci senaryo, bir zaman aşımı koşul tamamlanması için çok fazla yöntem zaman aşımı ayarlayarak neden olur. İstemci işlemi beklenen çıktısı bulunmaktadır:  
  
```  
Add(100,15.99) = 115.99  
Simulated network problem occurs...  
Got System.ServiceModel.CommunicationObjectAbortedException  
Add(100,15.99) = 115.99  
Set timeout too short for method to complete...  
Got System.TimeoutException  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örneği çalıştırma  
  
1. Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Tek veya çapraz makine yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\ExpectedExceptions`  
