---
title: MTOM Kodlama
ms.date: 03/30/2017
ms.assetid: 820e316f-4ee1-4eb5-ae38-b6a536e8a14f
ms.openlocfilehash: 83dbe9e51da1cc9e55bfffb862e2601d70fc7695
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144389"
---
# <a name="mtom-encoding"></a>MTOM Kodlama
Bu örnek, Bir WSHttpBinding ile kodlama İleti Aktarım Optimizasyonu Mekanizması (MTOM) iletisinin kullanımını gösterir. MTOM, büyük ikili ekleri SOAP iletileri ile ham bayt olarak iletmek için bir mekanizmadır ve daha küçük iletilere olanak sağlar.  
  
> [!IMPORTANT]
> Numuneler makinenize zaten yüklenmiş olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek aşağıdaki dizinde yer almaktadır.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\MTOM`  
  
 Varsayılan olarak, WSHttpBinding gönderir ve normal metin XML olarak iletileri aldı. MTOM iletilerinin gönderilmesini ve alınmasını `messageEncoding` etkinleştirmek için, özniteliği bağlama yapılandırmasına (aşağıdaki örnek kodda olduğu `MessageEncoding` gibi) veya özelliği kullanarak doğrudan bağlamaya ayarlayın. Hizmet veya istemci artık MTOM iletileri gönderip alabilir.  
  
```xml  
<wsHttpBinding>  
  <binding name="WSHttpBinding_IUpload" messageEncoding="Mtom" />  
</wsHttpBinding>  
```  
  
 MTOM kodlayıcısı bayt ve akış dizilerini optimize edebilir. Bu örnekte, işlem `Stream` bir parametre kullanır ve bu nedenle en iyi duruma getirilebilir.  

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
  public interface IUpload  
  {  
      [OperationContract]  
      int Upload(Stream data);  
  }  
```
  
 Bu örnek için seçilen sözleşme, ikili verileri hizmete iletir ve iade değeri olarak yüklenen bayt sayısını alır. Hizmet yüklendiğinde ve istemci çalıştırıldığında, 1000 baytın tamamının alındığını gösteren 1000 sayısını yazdırır. Çıktının geri kalanı, çeşitli yükler için en iyi duruma getirilmiş ve optimize edilmeyen ileti boyutlarını listeler.  
  
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
  
 MTOM'u kullanmanın amacı, büyük ikili yüklerin iletimini optimize etmektir. MTOM kullanarak soap iletisi göndermek, küçük ikili yükler için gözle görülür bir yüke sahiptir, ancak birkaç bin baytın üzerinde büyüdüklerinde büyük bir tasarruf sağlar. Bunun nedeni, normal metin XML'in her üç bayt için dört karakter gerektiren Base64 kullanarak ikili verileri kodlaması ve verilerin boyutunu üçte bir oranında artırmasıdır. MTOM, ikili verileri ham bayt olarak iletebilir, kodlama/çözme süresini kaydeder ve ortaya çıkan iletiler daha küçüktür. Birkaç bin bayt eşiği bugünün iş belgeleri ve dijital fotoğraflar ile karşılaştırıldığında küçüktür.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, oluşturmak ve çalıştırmak için  
  
1. Aşağıdaki komutu kullanarak 4.0 ASP.NET yükleyin.  
  
    ```console
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. Windows Communication Foundation [Samples için Tek Seferlik Kurulum Yordamı'nı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizi emin olun.  
  
3. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak [için, Windows Communication Foundation Samples'i oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.  
  
4. Örneği tek veya çapraz makine yapılandırmasında çalıştırmak için, [Windows Communication Foundation Samples'ı çalıştıran](../../../../docs/framework/wcf/samples/running-the-samples.md)yönergeleri izleyin.  
