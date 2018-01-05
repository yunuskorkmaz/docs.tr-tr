---
title: "Keşif Güvenliği Örneği"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b8db01f4-b4a1-43fe-8e31-26d4e9304a65
caps.latest.revision: "13"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: f50334c8477b8823ef1dfb6abcae640e439d5ddd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="discovery-security-sample"></a>Keşif Güvenliği Örneği
Bulma belirtiminin olmasını bulma işlemi katılmak uç noktalarını güvenli gerektirmez. Bulma iletileri ile güvenliği artırmaya azaltır saldırıları çeşitli türlerde (ileti değişikliğinin, hizmet reddi, yeniden yürütme, kimlik sahtekarlığı). Bu örnek, işlem ve (WS-bulma belirtimi bölüm 8.2 içinde açıklanan) compact imza biçimini kullanarak ileti imzaları doğrulamak özel kanalları uygular. Örnek destekler [2005 bulma belirtimi](http://go.microsoft.com/fwlink/?LinkId=177912) ve [1.1 sürümünü](http://go.microsoft.com/fwlink/?LinkId=179677).  
  
 Özel kanal bulma ve duyuru uç noktalar için varolan kanal yığın üzerinde uygulanır. Bu şekilde, bir imza üstbilgisi gönderilen her ileti için uygulanır. İmza alınan iletiler üzerinde doğrulanır ve eşleşmiyor veya iletileri bir imzaya sahip değilse, iletileri bırakılır. Oturum açın ve iletileri doğrulamak için örnek sertifikaları kullanır.  
  
## <a name="discussion"></a>Tartışma  
 WCF çok genişletilebilir ve kullanıcıların istendiği kanalları özelleştirmek olasılığı sağlar. Güvenli kanal oluşturan bir bulma güvenli bağlama öğesi örneği uygular. Güvenli kanal uygulamak ve ileti imzaları doğrulamak ve geçerli yığının en üstünde uygulanır.  
  
 Güvenli kanal fabrikaları ve kanal dinleyicileri güvenli bağlama öğesi oluşturur.  
  
## <a name="secure-channel-factory"></a>Güvenli kanal fabrikası  
 Güvenli kanal fabrikası çıkış veya compact imza ileti üstbilgilerini eklemek çift yönlü kanalı oluşturur. İletileri compact imza biçimi olabildiğince küçük tutmak için kullanılır. Compact imza yapısını, aşağıdaki örnekte gösterilir.  
  
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
  
 İmza işlem için örnek genişletilmiş imza öğeleri belirler. Bir XML imzası (`SignedInfo`), kullanılarak oluşturulan `ds` WS-bulma belirtimine göre gerektiği gibi ad alanı öneki. İle değiştirilmemesi şekilde gövdesi ve bulma ve ad alanları adresleme tüm üstbilgileri imzada başvurulur. Başvurulan her öğenin özel Standartlaştırma (http://www.w3.org/2001/10/xml-exc-c14n#) kullanılarak dönüştürülen ve ardından SHA-1 Özet hesaplanan (http://www.w3.org/2000/09/xmldsig#sha1) bir değerdir. Tüm başvurulan öğelerin ve Özet değerlerine bağlı olarak, imza değeri (http://www.w3.org/2000/09/xmldsig#rsa-sha1) RSA algoritması kullanılarak hesaplanır.  
  
 İstemci tarafından belirtilen bir sertifikayla imzalı iletiler. Bağlama öğesi oluşturulduğunda, depolama konumu, adı ve sertifika konu adı belirtilmelidir. `KeyId` Compact imzada imzalama belirteci anahtar tanımlayıcısını temsil eder ve imzalama belirtecinin konu anahtarı tanımlayıcısı (SKI) olan veya (SKI yoksa) imzalama belirtecinin ortak anahtarın SHA-1 karması.  
  
## <a name="secure-channel-listener"></a>Güvenli kanal dinleyicisi  
 Güvenli kanal dinleyicisi alınan iletilerde compact imzasını giriş veya çift yönlü kanalı oluşturur. İmzayı doğrulamak için `KeyId` compact belirtilen iletisine imza belirtilen deposundan bir sertifikayı seçmek için kullanılır. İleti bir imzası yok veya imza denetimi başarısız olursa, iletileri bırakılır. Güvenli bağlama kullanmak için örnek özel oluşturan bir Üreteç tanımlar <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> ve <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> eklenen bulma güvenli bağlama öğeye sahip. Bu güvenli uç noktalarını bulma duyuru dinleyicileri ve bulunabilirlik Hizmetleri'nde kullanılabilir.  
  
## <a name="sample-details"></a>Örnek Ayrıntıları  
 Örnek, bir kitaplık ve 4 konsol uygulamaları içerir:  
  
-   **DiscoverySecurityChannels**: Güvenli bağlama kullanıma sunan bir kitaplık. Kitaplık hesaplar ve giden/gelen iletiler için compact imzayı doğrular.  
  
-   **Hizmet**: kendini barındıran ICalculatorService sözleşme gösterme bir hizmet. Hizmet bulunabilir işaretlenir. Kullanıcının depolama konumu ve adı ve konu adı veya diğer sertifika için benzersiz bir tanımlayıcı belirterek iletileri imzalamak için kullanılan sertifika ayrıntılarını belirtir ve istemci sertifikalarını nerede deposu (için kullanılan sertifikaları yer gelen iletiler için imza denetleyin). Bu ayrıntıları bağlı olarak, ek güvenlik ile UdpDiscoveryEndpoint yerleşik olarak kullanılan ve.  
  
-   **İstemci**: Bu sınıf bir ICalculatorService bulmak ve hizmette yöntemleri çağırmak için çalışır. Yeniden, bir <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> güvenlik yerleşik ve oturum açın ve iletileri doğrulamak için kullanılan eklendi.  
  
-   **AnnouncementListener**: çevrimiçi ve çevrimdışı duyurularını dinler ve güvenli duyuru uç noktası kullanan bir kendi kendini barındıran hizmet.  
  
> [!NOTE]
>  Birden çok kez Setup.bat çalıştırırsanız, yinelenen sertifikalar olarak eklemek için bir sertifika seçmek için Sertifika Yöneticisi'ni ister. Bu durumda, Setup.bat durduruldu ve yinelemeleri zaten oluşturulduğundan Cleanup.bat çağrılmalıdır. CleanUp.bat silmek için bir sertifika seçmek ister. Listeden bir sertifika seçin ve sertifika kalan kadar Cleanup.bat yürütme devam edin.  
  
#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1.  Visual Studio komut isteminden Setup.bat betiğini yürütün. Örnek, oturum ve iletileri doğrulamak için sertifikaları kullanır. Komut dosyası Makecert.exe ile sertifikalar oluşturur ve bunları yükler Certmgr.exe kullanma. Komut dosyasını yönetici ayrıcalıklarıyla çalıştırılmalıdır.  
  
2.  Derleme ve örneği çalıştırmak için Security.sln dosyasını Visual Studio'da açın ve seçin **yeniden tüm**. Birden çok proje başlatmak için çözüm özelliklerini güncelleştirmek: seçin **Başlat** DiscoverySecureChannels dışındaki tüm projeleri için. Çözüm normal olarak çalışır.  
  
3.  Örnekle tamamladıktan sonra bu örnek için oluşturulan sertifikalar kaldırır Cleanup.bat betiğini yürütün.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DiscoveryScenario`  
  
## <a name="see-also"></a>Ayrıca Bkz.
