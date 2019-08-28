---
title: Keşif Güvenliği Örneği
ms.date: 03/30/2017
ms.assetid: b8db01f4-b4a1-43fe-8e31-26d4e9304a65
ms.openlocfilehash: dfc0dfcd3b4d814a158b328ef202d5438e583a8c
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70039810"
---
# <a name="discovery-security-sample"></a>Keşif Güvenliği Örneği
Bulma belirtimi, bulma işlemine katılan uç noktaların güvenli olmasını gerektirmez. Bulma iletilerini güvenlikle birlikte geliştirmek, çeşitli saldırı türlerini azaltır (ileti değişikliği, hizmet reddi, yeniden kimlik sahtekarlığı). Bu örnek, sıkıştırılmış imza biçimini kullanarak ileti imzalarını hesapladığı ve doğrulayan özel kanallar uygular (WS-Discovery belirtiminin 8,2 bölümünde açıklanmıştır). Örnek, hem [2005 bulma belirtimini](https://go.microsoft.com/fwlink/?LinkId=177912) hem de [1,1 sürümünü](https://go.microsoft.com/fwlink/?LinkId=179677)destekler.  
  
 Özel kanal, bulma ve duyuru uç noktaları için mevcut kanal yığınının üzerine uygulanır. Bu şekilde, gönderilen her ileti için bir imza üst bilgisi uygulanır. İmza, alınan iletilerde doğrulanır ve eşleşmediği zaman veya iletilerde imza yoksa iletiler bırakılır. İletileri imzalamak ve doğrulamak için, örnek sertifikaları kullanır.  
  
## <a name="discussion"></a>Tartışma  
 WCF çok genişletilebilir ve kullanıcılara kanalları istenen şekilde özelleştirme olasılığa izin verir. Örnek, güvenli kanallar oluşturan bir bulgu güvenli bağlama öğesi uygular. Güvenli kanallar, ileti imzalarını uygular ve doğrular ve geçerli yığının üzerine uygulanır.  
  
 Güvenli bağlama öğesi, güvenli kanal fabrikaları ve kanal dinleyicileri oluşturur.  
  
## <a name="secure-channel-factory"></a>Güvenli kanal fabrikası  
 Güvenli kanal fabrikası, ileti üst bilgilerine bir küçük imza ekleyen çıkış veya çift yönlü kanallar oluşturur. Sıkıştırılmış imza biçimi kullanılan iletileri olabildiğince küçük tutmak için. Bir Compact imzasının yapısı aşağıdaki örnekte gösterilmiştir.  
  
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
> , `PrefixList` 2008 bulma sürümü protokolüne eklenmiştir.  
  
 İmzayı hesaplamak için, örnek genişletilmiş imza öğelerini belirler. WS-Discovery belirtiminin`SignedInfo`gerektirdiği şekilde `ds` ad alanı öneki kullanılarak bir XML imzası () oluşturulur. Bulma ve adresleme ad alanlarındaki gövdeye ve tüm üst bilgilere imza içinde başvuruluyor, bu nedenle üzerinde değişiklik yapılamaz. Başvurulan her öğe, dışlamalı kurallı kullanım (http://www.w3.org/2001/10/xml-exc-c14n# ) kullanılarak dönüştürülür ve ardından bir SHA-1 Özet değeri hesaplanır (http://www.w3.org/2000/09/xmldsig#sha1 ). Başvurulan tüm öğelere ve bunların Özet değerlerine göre imza değeri, RSA algoritması (http://www.w3.org/2000/09/xmldsig#rsa-sha1 ) kullanılarak hesaplanır.  
  
 İletiler, istemci tarafından belirtilen sertifikayla imzalanır. Bağlama öğesi oluşturulduğunda depo konumu, ad ve sertifika konu adı belirtilmelidir. Sıkıştırma `KeyId` imzasında, imzalama belirtecinin anahtar tanımlayıcısını temsil eder ve imzalama belirtecinin konu anahtar tanımlayıcısı (kayak) veya imza belirtecinin ortak anahtarının bir SHA-1 karması vardır.  
  
## <a name="secure-channel-listener"></a>Güvenli kanal dinleyicisi  
 Güvenli kanal dinleyicisi, alınan iletilerde sıkıştırılmış imzayı doğrulayan giriş veya çift yönlü kanallar oluşturur. İmzayı doğrulamak için, `KeyId` iletiye iliştirilmiş, belirtilen depodan bir sertifika seçmek için kullanılan sıkıştır imzasında belirtilen. İletinin imzası yoksa veya imza denetimi başarısız olursa iletiler bırakılır. Güvenli bağlamayı kullanmak için örnek, eklenen bulma güvenli bağlama öğesi ile özel <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> ve <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> oluşturan bir fabrika tanımlar. Bu güvenli uç noktalar, bulma duyurusu dinleyicileri ve keşfedilebilir hizmetlerde kullanılabilir.  
  
## <a name="sample-details"></a>Örnek Ayrıntılar  
 Örnek, bir kitaplık ve 4 konsol uygulaması içerir:  
  
- **DiscoverySecurityChannels**: Güvenli bağlamayı kullanıma sunan bir kitaplık. Kitaplık, giden/gelen iletiler için sıkıştırılmış imzayı hesaplar ve doğrular.  
  
- **Hizmet**: Kendi kendine barındırılan bir hizmet olan Icalbir hizmet sözleşmesini kullanıma sunma. Hizmet bulunabilir olarak işaretlendi. Kullanıcı, sertifika için depolama konumunu ve adı ve konu adını ya da diğer benzersiz tanımlayıcıyı ve istemci sertifikalarının bulunduğu mağazayı (için kullanılan sertifikalar) belirterek iletileri imzalamak için kullanılan sertifikanın ayrıntılarını belirtir. gelen iletiler için imzayı denetleyin). Bu ayrıntılara dayanarak, ek güvenlik içeren bir UdpDiscoveryEndpoint oluşturulur ve kullanılır.  
  
- **İstemci**: Bu sınıf bir Icalbir Torservice bulmaya çalışır ve hizmette Yöntemler çağırabilir. Yine, eklenen <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> güvenliği olan bir, iletileri imzalamak ve doğrulamak için oluşturulur ve kullanılır.  
  
- **Announcementlistener**: Çevrimiçi ve çevrimdışı duyuruları dinleyen ve güvenli duyuru uç noktasını kullanan, şirket içinde barındırılan bir hizmet.  
  
> [!NOTE]
> Setup. bat birden çok kez çalışıyorsa, Sertifika Yöneticisi yinelenen sertifikalar olduğu için eklemek üzere bir sertifika seçmenizi ister. Bu durumda, yinelemeleri zaten oluşturulduğundan Setup. bat durdurulmalı ve Cleanup. bat çağrılmalıdır. Cleanup. bat Ayrıca, silinecek sertifikayı seçmenizi ister. Listeden bir sertifika seçin ve hiçbir sertifika geri alınana kadar Cleanup. bat çalıştırmaya devam edin.  
  
#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1. Visual Studio için Geliştirici Komut İstemi Setup. bat betiğini yürütün. Örnek, iletileri imzalamak ve doğrulamak için sertifikaları kullanır. Betik, MakeCert. exe kullanarak sertifikaları oluşturur ve sonra certmgr. exe ' yi kullanarak bunları kurar. Betiğin yönetici ayrıcalıklarıyla çalıştırılması gerekir.  
  
2. Örneği derlemek ve çalıştırmak için, Visual Studio 'da Security. sln dosyasını açın ve **tümünü yeniden derle**' yi seçin. Birden çok proje başlatmak için çözüm özelliklerini güncelleştirin: DiscoverySecureChannels hariç tüm projeler için **Başlat** ' ı seçin. Çözümü normal olarak çalıştırın.  
  
3. Örnekle işiniz bittiğinde, bu örnek için oluşturulan sertifikaları kaldıran Cleanup. bat betiğini yürütün.  
  
> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ' e gidin. Bu örnek, aşağıdaki dizinde bulunur.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DiscoveryScenario`  
