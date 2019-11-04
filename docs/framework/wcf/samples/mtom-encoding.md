---
title: MTOM Kodlama
ms.date: 03/30/2017
ms.assetid: 820e316f-4ee1-4eb5-ae38-b6a536e8a14f
ms.openlocfilehash: ab8abdf79304037f2b4039407115a3f64a0afa4e
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73424065"
---
# <a name="mtom-encoding"></a>MTOM Kodlama
Bu örnek, bir WSHttpBinding ile Ileti Iletimi Iyileştirme mekanizması (MTOM) ileti kodlamasının kullanımını gösterir. MTOM, SOAP iletileri olan büyük ikili ekleri ham bayt olarak iletme ve daha küçük iletilere izin veren bir mekanizmadır.  
  
> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://go.microsoft.com/fwlink/?LinkId=150780) gidin. Bu örnek, aşağıdaki dizinde bulunur.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\MTOM`  
  
 Varsayılan olarak, WSHttpBinding iletileri normal metin XML olarak gönderir ve gönderir. MTOM iletilerinin gönderilmesini ve alınmasını etkinleştirmek için, bağlamanın yapılandırmasındaki `messageEncoding` özniteliğini (Aşağıdaki örnek kodda olduğu gibi) veya doğrudan bağlama üzerinde `MessageEncoding` özelliğini kullanarak ayarlayın. Hizmet veya istemci artık MTOM iletileri gönderebilir ve alabilir.  
  
```xml  
<wsHttpBinding>  
  <binding name="WSHttpBinding_IUpload" messageEncoding="Mtom" />  
</wsHttpBinding>  
```  
  
 MTOM Kodlayıcısı, bayt ve akış dizilerini iyileştirebilirler. Bu örnekte, işlem bir `Stream` parametresi kullanır ve bu nedenle en iyi duruma getirilebilir.  

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
  public interface IUpload  
  {  
      [OperationContract]  
      int Upload(Stream data);  
  }  
```
  
 Bu örnek için seçilen sözleşme, ikili verileri hizmete aktarır ve dönüş değeri olarak karşıya yüklenen bayt sayısını alır. Hizmet yüklendiğinde ve istemci çalıştırıldığında, tüm 1000 baytlarının alındığını belirten 1000 sayısını yazdırır. Çıktının geri kalanı, çeşitli yükleri için iyileştirilmiş ve en iyi duruma getirilmemiş ileti boyutlarını listeler.  
  
```console
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
  
 MTOM kullanmanın amacı, büyük ikili yüklerin iletimini en iyi hale getirsağlamaktır. MTOM kullanarak bir SOAP iletisi gönderdiğinizde küçük ikili yükleri için fark edilebilir bir ek yük vardır, ancak birkaç bin baytlık büyürken harika bir tasarruf olur. Bunun nedeni, normal metin XML 'nin ikili verileri her üç bayt için dört karakter gerektiren Base64 kullanarak kodlayacağı ve verilerin boyutunu bir üçüncü artırır. MTOM, ikili verileri ham bayt olarak aktarabilir, kodlama/kod çözme süresini ve sonuç olarak daha küçük mesajlar elde edebilir. Bugünün iş belgelerinin ve dijital fotoğraflarına kıyasla birkaç bin baytlık eşik değeri küçüktür.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için  
  
1. Aşağıdaki komutu kullanarak ASP.NET 4,0 ' ü yükler.  
  
    ```console
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.  
  
3. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak Için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)konusundaki yönergeleri izleyin.  
  
4. Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md)bölümündeki yönergeleri izleyin.  
