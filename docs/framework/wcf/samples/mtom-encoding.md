---
title: MTOM Kodlama
ms.date: 03/30/2017
ms.assetid: 820e316f-4ee1-4eb5-ae38-b6a536e8a14f
ms.openlocfilehash: 1f30c3a1c7a9a4874f4b831ee27192468e63c192
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="mtom-encoding"></a>MTOM Kodlama
Bu örnek bir WSHttpBinding kodlama ileti iletim en iyi duruma getirme mekanizmasını (MTOM) iletisi kullanımını göstermektedir. MTOM SOAP iletilerle büyük ikili dosya eklerini ham bayt olarak iletmek için bir küçük iletiler için izin verme mekanizmadır.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\MTOM`  
  
 Varsayılan, WSHttpBinding gönderir ve normal metin XML olarak alınan iletiler. MTOM ileti gönderme ve alma etkinleştirmek için ayarlanmış `messageEncoding` özniteliği bağlamanın yapılandırma (örneğin, aşağıdaki örnek kod) veya doğrudan bağlamayı kullanarak `MessageEncoding` özelliği. Hizmet veya istemci şimdi gönderip MTOM iletileri alabilirsiniz.  
  
```xml  
<wsHttpBinding>  
  <binding name="WSHttpBinding_IUpload" messageEncoding="Mtom" />  
</wsHttpBinding>  
```  
  
 MTOM Kodlayıcısı bayt ve akışlar dizileri en iyi duruma getirebilirsiniz. Bu örnekte, işlem kullanan bir `Stream` parametresi ve bu nedenle iyileştirilebilir.  

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
  public interface IUpload  
  {  
      [OperationContract]  
      int Upload(Stream data);  
  }  
```
  
 Bu örnek için seçilen sözleşme hizmetine ikili veri aktaran ve dönüş değeri olarak karşıya bayt sayısını alır. Hizmetin yüklü olduğundan ve istemci çalıştırın, tüm 1000 bayt aldığını gösteren sayı 1000 yazdırır. Çıktı kalanı çeşitli yükü için en iyileştirilmiş veya iyileştirilmemiş ileti boyutlarını listeler.  
  
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
  
 MTOM kullanma büyük ikili yüklerini iletimini en iyi duruma getirme amaçtır. MTOM kullanarak bir SOAP iletisi gönderme küçük ikili yükleri için belirgin yüke sahiptir, ancak birkaç bin bayt büyümeden harika tasarruf haline gelir. Bunun nedeni, normal metin XML için üç her bayt dört karakter gerektirir ve verilerin boyutunu üçte tarafından artıran Base64 kullanarak ikili veri kodlar ' dir. MTOM kodlama/kod çözme süresi kaydetme ham bayt ikili veri iletmek için ve elde edilen küçük ileti. Günümüzün iş belgeleri ve dijital fotoğraflar karşılaştırıldığında birkaç bin bayt eşiğinin küçüktür.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örnek çalıştırın  
  
1.  Yükleme [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aşağıdaki komutu kullanarak 4.0.  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
3.  Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4.  Tek veya çapraz makine yapılandırmada örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.
