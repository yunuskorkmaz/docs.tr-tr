---
title: Keşif Güvenliği Örneği
ms.date: 03/30/2017
ms.assetid: b8db01f4-b4a1-43fe-8e31-26d4e9304a65
ms.openlocfilehash: 00f81d1879d9157a7ecdfa0db8d2ea0d505ad5b6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183740"
---
# <a name="discovery-security-sample"></a>Keşif Güvenliği Örneği

Bulma belirtimi, bulma işlemine katılan uç noktaların güvenli olmasını gerektirmez. Keşif iletilerini güvenlikle birlikte geliştirmek çeşitli saldırı türlerini azaltır (ileti değişikliği, hizmet reddi, yeniden oynatma, sızdırma). Bu örnek, ileti imzalarını kompakt imza biçimini kullanarak (WS-Discovery belirtiminin Bölüm 8.2'sinde açıklanan) oluşturan ve doğrulayan özel kanallar uygular. Örnek hem [2005 Discovery belirtimi](http://specs.xmlsoap.org/ws/2005/04/discovery/ws-discovery.pdf) ve [1.1 sürümünü](http://docs.oasis-open.org/ws-dd/discovery/1.1/cs-01/wsdd-discovery-1.1-spec-cs-01.pdf)destekler.  
  
 Özel kanal, Bulma ve Duyuru uç noktaları için varolan kanal yığınının üstüne uygulanır. Bu şekilde, gönderilen her ileti için imza üstbilgisi uygulanır. İmza alınan iletilerde doğrulanır ve eşleşmediğinde veya iletilerin imzası olmadığında iletiler bırakılır. İletileri imzalamak ve doğrulamak için örnek sertifikalar kullanır.  
  
## <a name="discussion"></a>Tartışma  
 WCF çok genişletilebilir ve kullanıcıların istediği gibi kanalları özelleştirme olanağı sağlar. Örnek, güvenli kanallar oluşturan bir keşif güvenli bağlama öğesi uygular. Güvenli kanallar ileti imzalarını uygular ve doğrular ve geçerli yığının üstüne uygulanır.  
  
 Güvenli bağlama öğesi güvenli kanal fabrikaları ve kanal dinleyicileri oluşturur.  
  
## <a name="secure-channel-factory"></a>Güvenli Kanal Fabrikası  
 Güvenli kanal fabrikası, ileti üstbilgilerine kompakt imza ekleyen çıktı veya çift yönlü kanallar oluşturur. İletileri mümkün olduğunca küçük tutmak için kompakt imza biçimi kullanılır. Kompakt imzanın yapısı aşağıdaki örnekte gösterilmiştir.  
  
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
> 2008 `PrefixList` Discovery sürüm protokolüne eklendi.  
  
 İmzayı hesaplamak için, örnek genişletilmiş imza öğelerini belirler. WS-Discovery belirtiminin gerektirdiği`SignedInfo` `ds` ad alanı öneki kullanılarak bir XML imzası ( ) oluşturulur. Gövde ve bulma ve adresleme ad boşluklarındaki tüm üstbilgileri imzada başvurulur, bu nedenle değiştirilemezler. Başvurulan her öğe Özel Kanonializasyonhttp://www.w3.org/2001/10/xml-exc-c14n# (), kullanılarak dönüştürülür ve ardından SHA-1 özet değerihttp://www.w3.org/2000/09/xmldsig#sha1 () olarak hesaplanır. Başvurulan tüm öğeler ve bunların özet değerlerine göre imza değeri RSAhttp://www.w3.org/2000/09/xmldsig#rsa-sha1 algoritması kullanılarak hesaplanır .  
  
 İletiler istemci tarafından belirtilen bir sertifikayla imzalanır. Bağlama öğesi oluşturulduğunda mağaza konumu, adı ve sertifika özne adı belirtilmelidir. Kompakt `KeyId` imza, imza belirtecinin anahtar tanımlayıcısını temsil eder ve imza belirtecinin Özne Anahtarı Tanımlayıcısi 'dir (SKI yoksa) veya (SKI yoksa) imza belirtecinin ortak anahtarının SHA-1 karmasidır.  
  
## <a name="secure-channel-listener"></a>Güvenli Kanal Dinleyicisi  
 Güvenli kanal dinleyicisi, alınan iletilerde kompakt imzayı doğrulayan giriş veya çift yönlü kanallar oluşturur. İmzayı doğrulamak için, iletiye iliştirilen kompakt imzada `KeyId` belirtilen belge, belirtilen mağazadan bir sertifika seçmek için kullanılır. İletinin imzası yoksa veya imza denetimi başarısız olursa, iletiler bırakılır. Güvenli bağlamayı kullanmak için, örnek özel <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> ve eklenen <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> bulma güvenli bağlama öğesi ile bir fabrika tanımlar. Bu güvenli uç noktalar keşif duyuru dinleyicilerinde ve bulunabilir hizmetlerde kullanılabilir.  
  
## <a name="sample-details"></a>Örnek Ayrıntılar  
 Örnek bir kitaplık ve 4 konsol uygulamaları içerir:  
  
- **DiscoverySecurityChannels**: Güvenli bağlamayı ortaya çıkaran kitaplık. Kitaplık, giden/gelen iletiler için kompakt imzayı bilgive doğrular.  
  
- **Hizmet**: ICalculatorService sözleşmesini ortaya çıkaran bir hizmet, kendi kendine barındırılan. Hizmet Keşfedilebilir olarak işaretlenir. Kullanıcı, mağaza konumunu ve adını ve sertifikanın özadını veya diğer benzersiz tanımlayıcısını belirterek iletileri imzalamak için kullanılan sertifikanın ayrıntılarını ve istemci sertifikalarının bulunduğu mağazayı (kullanılan sertifikalar gelen iletiler için imzayı denetleyin). Bu ayrıntılara dayanarak, ek güvenliğe sahip bir UdpDiscoveryEndpoint oluşturulur ve kullanılır.  
  
- **İstemci**: Bu sınıf bir ICalculatorService keşfetmeye ve hizmetteki yöntemleri çağırmaya çalışır. Yine, <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> ek güvenlik ile bir yapılı ve imzalamak ve iletileri doğrulamak için kullanılır.  
  
- **AnnouncementListener**: Çevrimiçi ve çevrimdışı duyuruları dinleyen ve güvenli duyuru bitiş noktasını kullanan kendi kendine barındırılan bir hizmet.  
  
> [!NOTE]
> Setup.bat birden çok kez çalıştırılırsa, sertifika yöneticisi yinelenen sertifikalar olduğu için ekleyeceğiniz bir sertifika seçmenizi ister. Bu durumda, Setup.bat iptal edilmeli ve Temizleme.bat çağrılmalıdır, çünkü yinelenenler zaten oluşturulmuştur. Cleanup.bat ayrıca silmek için bir sertifika seçmenize de izin ister. Listeden bir sertifika seçin ve sertifika kalmayıp kalana kadar Cleanup.bat'ı yürütmeye devam edin.  
  
#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1. Setup.bat komut dosyasını Visual Studio için Geliştirici Komut Komut Ustem'den çalıştırın. Örnek, iletileri imzalamak ve doğrulamak için sertifikalar kullanır. Komut dosyası, Sertifikaları Makecert.exe kullanarak oluşturur ve certmgr.exe kullanarak yükler. Komut dosyası yönetici ayrıcalıkları ile çalıştırılmalıdır.  
  
2. Örneği oluşturmak ve çalıştırmak için Visual Studio'da Security.sln dosyasını açın ve **Tümlerini Yeniden Oluştur'u**seçin. Birden çok proje başlatmak için çözüm özelliklerini güncelleştirin: DiscoverySecureChannels dışındaki tüm projeler için **Başlat'ı** seçin. Çözümü normal çalıştırın.  
  
3. Örnekle birlikte bittikten sonra, bu örnek için oluşturulan sertifikaları kaldıran Cleanup.bat komut dosyasını çalıştırın.  
  
> [!IMPORTANT]
> Numuneler makinenize zaten yüklenmiş olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek aşağıdaki dizinde yer almaktadır.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DiscoveryScenario`  
