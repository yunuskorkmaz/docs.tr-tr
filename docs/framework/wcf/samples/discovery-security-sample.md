---
title: Keşif Güvenliği Örneği
ms.date: 03/30/2017
ms.assetid: b8db01f4-b4a1-43fe-8e31-26d4e9304a65
ms.openlocfilehash: 09b7bad2e0b6b68a00d5ad2ed18e6ec831b04416
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/26/2018
ms.locfileid: "50041212"
---
# <a name="discovery-security-sample"></a>Keşif Güvenliği Örneği
Bulma belirtimi olmasını bulma işlemine katılmasını uç noktalarını güvenli gerektirmez. Bulma iletileri ile güvenlik geliştirme azaltır çeşitli türdeki saldırıları (ileti değişikliğinin, hizmet reddi, yeniden yürütme, kimlik sahtekarlığı). Bu örnek, işlem ve (WS-bulma belirtiminin bölüm 8.2 içinde açıklanmıştır) compact imza biçimini kullanarak ileti imzaları doğrulamak özel kanallar uygular. Örnek her ikisini de destekler [2005 bulma belirtimi](https://go.microsoft.com/fwlink/?LinkId=177912) ve [1.1 sürümü](https://go.microsoft.com/fwlink/?LinkId=179677).  
  
 Özel kanal, bulma ve duyuru uç noktalar için var olan kanal yığın üzerine uygulanır. Bu şekilde, bir imza üst bilgisi gönderilen her ileti için uygulanır. İmza alınan iletiler üzerinde doğrulanır ve eşleşmiyor veya iletileri bir imzaya sahip değilse, iletileri bırakılır. Oturum ve iletileri doğrulamak için örnek sertifikaları kullanır.  
  
## <a name="discussion"></a>Tartışma  
 WCF çok genişletilebilir ve kullanıcılara olasılığını kanalları istediğiniz şekilde özelleştirin. Güvenli kanal oluşturan bir bulma güvenli bağlama öğesi örneği uygular. Güvenli kanal iletisi imzaları doğrulamak uygulamak ve geçerli yığının en üstünde uygulanır.  
  
 Güvenli bağlama öğesi, güvenli kanal fabrikaları ve kanal dinleyicisi oluşturur.  
  
## <a name="secure-channel-factory"></a>Güvenli kanal fabrikası  
 Güvenli kanal fabrikası çıkış veya compact imza ileti üstbilgilerini eklemek çift yönlü kanalı oluşturur. İletileri compact İmza biçiminin olabildiğince küçük tutmak için kullanılır. Aşağıdaki örnekte compact imza yapısı gösterilmektedir.  
  
```xml  
<d:Security ... >   
  [<d:Sig Scheme="xs:anyURI"   
         [KeyId="xs:base64Binary"]?  
          Refs="..."  
         [PrefixList]="xs:NMTOKENS"   
          Sig="xs:base64Binary"   
          ... />]?  
  ...   
</d:Security>  
```  
  
> [!NOTE]
>  `PrefixList` 2008 bulma sürüm protokolünde eklendi.  
  
 İmza hesaplamak için örnek genişletilmiş imza öğeleri belirler. Podpis XML (`SignedInfo`), kullanılarak oluşturulan `ds` WS-bulma belirtimi gerektirdiği gibi ad alanı öneki. İle değiştirilmemesi için gövde ve bulma ve ad alanları addressing üst bilgileri imza ile başvurulur. Başvurulan her öğenin özel Standartlaştırma kullanarak dönüştürülür (http://www.w3.org/2001/10/xml-exc-c14n# ), ve ardından bir SHA-1 Özet değer hesaplanır (http://www.w3.org/2000/09/xmldsig#sha1 ). Başvurulan tüm öğeleri ve Özet değerlerine bağlı olarak, imza değeri RSA algoritması kullanılarak hesaplanır (http://www.w3.org/2000/09/xmldsig#rsa-sha1 ).  
  
 İletileri, istemci tarafından belirtilen bir sertifika ile imzalanmış. Bağlama öğesi oluşturulduğunda, depolama konumu, adı ve sertifika konu adı belirtilmelidir. `KeyId` Compact imzasında imzalama belirtecinin anahtar tanımlayıcısını temsil eder ve imzalama belirtecinin konu anahtar tanımlayıcısı (KAYAK) olan veya (KAYAK yoksa) bir ortak anahtar imzalama belirtecinin SHA-1 karması.  
  
## <a name="secure-channel-listener"></a>Güvenli kanal dinleyicisi  
 Güvenli kanal dinleyicisi compact imzasını alınan iletiler, giriş ya da çift yönlü kanalı oluşturur. İmzayı doğrulamak için `KeyId` compact içinde belirtilen iletiye imza belirtilen deposundan bir sertifikayı seçmek için kullanılır. İleti bir imzası yok veya imza denetimi başarısız olursa, iletileri bırakılır. Güvenli bağlama kullanmak için özel oluşturan bir üreteci örneği tanımlar <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> ve <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> eklenen bulma güvenli bağlama öğesi. Bu güvenli uç noktaları, bulma duyuru dinleyicileri ve bulunabilirlik hizmetlerinde kullanılabilir.  
  
## <a name="sample-details"></a>Örnek Ayrıntıları  
 Örnek, bir kitaplık ve 4 konsol uygulamaları içerir:  
  
-   **DiscoverySecurityChannels**: Güvenli bağlama kullanıma sunan bir kitaplık. Kitaplığı, hesaplar ve giden/gelen iletiler için compact imzayı doğrular.  
  
-   **Hizmet**: ICalculatorService sözleşmeyi doğrulamasıyla açığa çıkaran hizmet, kendi kendine barındırılan. Hizmet bulunabilir işaretlenir. Kullanıcı depolama konumu ve adı ve konu adı veya diğer sertifika için benzersiz bir tanımlayıcı belirterek iletileri imzalamak için kullanılan sertifika ayrıntılarını belirtir ve istemci sertifikalarını nerede deposu (için kullanılan sertifikaları yer gelen iletiler için imza denetleyin). Bu ayrıntılara bağlı olarak, bir UdpDiscoveryEndpoint eklenen güvenlik ile yerleşik olarak kullanılan ve.  
  
-   **İstemci**: Bu sınıf bir ICalculatorService bulmak ve hizmet üzerinde yöntemleri çağırmak için çalışır. Tekrar bir <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> ile güvenlik oluşturulur ve oturum açın ve iletileri doğrulamak için kullanılan eklendi.  
  
-   **AnnouncementListener**: şirket içinde barındırılan hizmet için çevrimiçi ve çevrimdışı duyuruları dinleyen ve güvenli bir duyuru uç nokta kullanır.  
  
> [!NOTE]
>  Setup.bat birden çok kez çalıştırılırsa, yinelenen sertifikalar bulunduğundan eklemek için bir sertifika seçmek için Sertifika Yöneticisi ister. Bu durumda, Setup.bat durduruldu ve yinelenen bir önceden oluşturulmuş olduğundan Cleanup.bat çağrılmalıdır. CleanUp.bat silmek için bir sertifika seçmenizi ister. Listeden bir sertifika seçin ve sertifika kalan kadar Cleanup.bat yürütme devam edin.  
  
#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1.  Bir Visual Studio Komut İstemi'nden Setup.bat betiği yürütün. Örnek, oturum ve iletileri doğrulamak için sertifikaları kullanır. Betik Makecert.exe ile bir sertifika oluşturur ve bunları yükler Certmgr.exe kullanarak. Betik, yönetici ayrıcalıklarıyla çalıştırılmalıdır.  
  
2.  Derleme ve çalıştırma örneği için Security.sln dosyasını Visual Studio'da açın ve seçin **Rebuild All**. Birden çok proje başlatmak için çözüm özellikleri güncelleştirin: seçin **Başlat** DiscoverySecureChannels dışındaki tüm projeler için. Normalde çözümü çalıştırın.  
  
3.  Örnek ile bitirdikten sonra bu örnek için oluşturulan sertifikalar kaldıran Cleanup.bat betiği yürütün.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DiscoveryScenario`  
  
## <a name="see-also"></a>Ayrıca Bkz.
