---
title: MTOM Kodlama
ms.date: 03/30/2017
ms.assetid: 820e316f-4ee1-4eb5-ae38-b6a536e8a14f
ms.openlocfilehash: f54a22b0004623c8aef8f2788ed7d59f7d777ce7
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/11/2018
ms.locfileid: "44368059"
---
# <a name="mtom-encoding"></a>MTOM Kodlama
Bu örnek, bir WSHttpBinding kodlamasını ileti aktarım en iyi duruma getirme mekanizması (MTOM) kullanımını gösterir. MTOM ham bayt, büyük ikili eklerle SOAP iletilerini ileten bir izin vermek için daha küçük iletileri mekanizmadır.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\MTOM`  
  
 Varsayılan, WSHttpBinding gönderir ve normal metin XML olarak alınan iletiler. MTOM ileti gönderme ve alma etkinleştirmek için ayarlayın `messageEncoding` özniteliği bağlama yapılandırma (örneğin, aşağıdaki kod örneği), veya doğrudan bağlama kullanarak `MessageEncoding` özelliği. Hizmet veya istemcinin artık gönderebilir ve MTOM iletileri alır.  
  
```xml  
<wsHttpBinding>  
  <binding name="WSHttpBinding_IUpload" messageEncoding="Mtom" />  
</wsHttpBinding>  
```  
  
 MTOM Kodlayıcısı dizileri bayt akışları ve en iyi duruma getirebilirsiniz. Bu örnekte, işlemi kullanan bir `Stream` parametre ve bu nedenle iyileştirilebilir.  

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
  public interface IUpload  
  {  
      [OperationContract]  
      int Upload(Stream data);  
  }  
```
  
 Bu örnek için seçilen sözleşme ikili veri hizmetine ileten ve dönüş değeri olarak karşıya yüklenen bayt sayısını alır. Yüklü hizmeti algılayamaz ve istemci çalıştırın, tüm 1000 bayt aldığını gösteren sayı 1000 yazdırır. Çıkış geri kalanı için çeşitli yüklerini en iyi duruma getirilmiş ve getirilmemiş ileti boyutları listeler.  
  
```  
Output:  
1000  
  
Text encoding with a 100 byte payload: 433  
MTOM encoding with a 100 byte payload: 912  
  
Text encoding with a 1000 byte payload: 1633  
MTOM encoding with a 1000 byte payload: 2080  
  
Text encoding with a 10000 byte payload: 13633  
MTOM encoding with a 10000 byte payload: 11080  
  
Text encoding with a 100000 byte payload: 133633  
MTOM encoding with a 100000 byte payload: 101080  
  
Text encoding with a 1000000 byte payload: 1333633  
MTOM encoding with a 1000000 byte payload: 1001080  
  
Press <ENTER> to terminate client.  
```  
  
 MTOM kullanma amacı, büyük ikili yükler iletimini en iyi duruma getirme sağlamaktır. MTOM kullanarak bir SOAP ileti gönderme küçük ikili yükler için fark edilebilir bir yüke sahiptir, ancak birkaç bin bayttan fazla büyürler harika tasarruf olur. Bunun nedeni, normal metin XML dört karakter için her üç bayt gerektirir ve üçte tarafından verilerin boyutunu artırır, Base64 kullanarak ikili verileri kodlar ' dir. MTOM kodlama/kod çözme zamandan tasarruf ikili veri ham bayt aktarmak mümkün ve elde edilen küçük ileti. Günümüzde iş belgeleri ve dijital fotoğraflar karşılaştırıldığında birkaç bin bayt sayısı eşiğini küçüktür.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örneği çalıştırma  
  
1.  Yükleme [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aşağıdaki komutu kullanarak 4.0.  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
3.  Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4.  Tek veya çapraz makine yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.
