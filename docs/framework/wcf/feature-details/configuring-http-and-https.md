---
title: HTTP ve HTTPS Yapılandırma
ms.date: 03/30/2017
helpviewer_keywords:
- configuring HTTP [WCF]
ms.assetid: b0c29a86-bc0c-41b3-bc1e-4eb5bb5714d4
ms.openlocfilehash: 25ca96104ef8a63a7c6988f6dfba309e9aa44a9b
ms.sourcegitcommit: facefcacd7ae2e5645e463bc841df213c505ffd4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/05/2019
ms.locfileid: "55738935"
---
# <a name="configuring-http-and-https"></a>HTTP ve HTTPS Yapılandırma
WCF hizmetleri ve istemcilerin HTTP ve HTTPS üzerinden iletişim kurabilir. HTTP/HTTPS ayarları, Internet Information Services (IIS) kullanarak veya bir komut satırı aracı kullanılarak yapılandırılır. Bir WCF Hizmeti IIS HTTP veya HTTPS ayarlarında zaman barındırılan (inetmgr.exe aracını kullanarak) IIS içinde yapılandırılabilir. Şirket içinde barındırılan bir WCF Hizmeti ise, bir komut satırı aracını kullanarak HTTP veya HTTPS ayarları yapılandırılır.  
  
 En az bir URL kaydını yapılandırma ve güvenlik duvarı özel durumu hizmetinizi kullanarak URL'si eklemek isteyeceksiniz.  
  
 HTTP ayarları yapılandırmak için kullanılan aracın çalıştığı bilgisayar işletim sistemine bağlıdır.  
  
 Çalıştırırken [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] veya [!INCLUDE[wxp](../../../../includes/wxp-md.md)], HttpCfg.exe aracını kullanın. [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] Bu araç otomatik olarak yükler. Çalıştırırken [!INCLUDE[wxp](../../../../includes/wxp-md.md)], aracı indirebileceğiniz [Windows XP Service Pack 2 Destek Araçları](https://go.microsoft.com/fwlink/?LinkId=88606). Daha fazla bilgi için [Httpcfg genel bakış](https://go.microsoft.com/fwlink/?LinkId=88605).  
  
 Çalıştırırken [!INCLUDE[wv](../../../../includes/wv-md.md)] veya Windows 7'de, bu ayarlarını yapılandırdığınız Netsh.exe aracı.  
  
## <a name="configuring-namespace-reservations"></a>Namespace ayırmaları yapılandırma  
 Namespace ayırma HTTP URL ad alanını bir kısmını haklarını belirli bir kullanıcı grubuna atar. Rezervasyon kullanıcılarla ad alanı kısmı üzerinde dinleme hizmetleri oluşturma hakkı verir. Rezervasyonlar URL ön ekleri ayırma ayırma yolun tüm alt yollar ele alınmaktadır anlamı, ' dir. Namespace ayırmaları joker karakter kullanmanın iki yolu izin verir. HTTP sunucu API belgelerde [joker karakterler içeren ad alanı talep arasındaki çözümleme sırasını](https://go.microsoft.com/fwlink/?LinkId=94841).  
  
 Ad alanı kayıtları eklemek için benzer bir istek, çalışan bir uygulama oluşturabilirsiniz. Kayıtları ve ayırmaları ad alanının bölümleri için yarışın. Rezervasyon çözümleme verilen sırasına göre bir kayıt üzerinde önceliğe sahip [joker karakterler içeren ad alanı talep arasındaki çözümleme sırasını](https://go.microsoft.com/fwlink/?LinkId=94841). Bu durumda, rezervasyon çalışan uygulama isteklerini almasını engeller.  
  
### <a name="running-windows-xp-or-server-2003"></a>Çalışan Windows XP veya Server 2003  
 Kullanım `httpcfg.exe set urlacl` ad alanı ayırmalarını değiştirmek için komutu. [Windows Destek Araçları belgeleri](https://go.microsoft.com/fwlink/?LinkId=94840) Httpcfg.exe aracın sözdizimi açıklar. Ad alanı değerinin bir bölümü için ayırma hakları değiştirme, yönetim ayrıcalıkları ya da söz konusu bölümü ad alanının sahipliğini gerektirir. Başlangıçta, tüm HTTP ad alanı için yerel yönetici aittir.  
  
 Aşağıdaki Httpcfg komutuyla söz dizimi görülmektedir `set urlacl` seçeneği  
  
```console  
httpcfg set urlacl /u {http://URL:Port/ | https://URL:Port/} /a ACL  
```  
  
 `/u` Kullanırken parametresi zorunludur `set urlacl`. İşlem yapılan rezervasyonu için kayıt anahtarı olarak hizmet veren tam bir URL içeren bir dize alır.  
  
 `/a` Parametresi zorunludur ayrıca kullanırken `set urlacl`. İşlem, bir güvenlik tanımlayıcısı tanım dili (SDDL) dizesi şeklinde erişim denetimi listesi (ACL) içeren bir dize alır.  
  
 Aşağıda, bu komutu kullanarak bir örnek gösterilmektedir.  
  
```console  
httpcfg.exe set urlacl /u http://myhost:8000/ /a "O:AOG:DAD:(A;;RPWPCCDCLCSWRCWDWOGA;;;S-1-0-0)"  
```  
  
### <a name="running-windows-vista-windows-server-2008-r2-or-windows-7"></a>Windows Vista, Windows Server 2008 R2 veya Windows 7 çalıştıran  
 Çalıştırıyorsanız, [!INCLUDE[wv](../../../../includes/wv-md.md)], Windows Server 2008 R2 veya Windows 7'de, Netsh.exe aracını kullanın. Aşağıda, bu komutu kullanarak bir örnek gösterilmektedir.  
  
```console  
netsh http add urlacl url=http://+:80/MyUri user=DOMAIN\user  
```  
  
 Bu komut, etki alanı\kullanıcı hesabı için belirtilen URL ad alanı için bir URL ayırmasını ekler.  Netsh komutu türü kullanma hakkında daha fazla bilgi için "netsh http add urlacl" bir komut istemi veya basın'girin.  
  
## <a name="configuring-a-firewall-exception"></a>Bir güvenlik duvarı özel durum yapılandırma  
 Bir özel durum kendi kendine HTTP üzerinden iletişim kuran bir WCF Hizmeti barındırma, belirli bir URL kullanarak gelen bağlantılara izin vermek için güvenlik duvarı yapılandırması eklenmesi gerekir. Daha fazla bilgi için [(Windows 7) Windows Güvenlik Duvarı'nda bir bağlantı noktasını açın](https://go.microsoft.com/fwlink/?LinkId=239961)  
  
## <a name="configuring-ssl-certificates"></a>SSL sertifikaları yapılandırma  
 Güvenli Yuva Katmanı (SSL) protokolü şifreleme anahtarlarını depolamak için istemci ve sunucu sertifikaları kullanır. İstemci, sunucu kimliğini doğrulayabilir bir bağlantı yapıldığında sunucu SSL sertifikasını sağlar. Sunucu, istemciden bağlantının her iki tarafının karşılıklı kimlik doğrulaması sağlamak için ayrıca bir sertifika isteyebilir.  
  
 Sertifikaları Merkezi bir depolama bağlantı IP adresi ve bağlantı noktası numarasını göre depolanır. Özel IP adresi 0.0.0.0 yerel makine için herhangi bir IP adresi ile eşleşir. Sertifika deposu yola göre URL'leri gözetmez unutmayın. Hizmetler için URL yolu farklı olsa bile aynı IP adresi ve bağlantı noktası bileşimi ile hizmet sertifikaları paylaşmanız gerekir.  
  
 Adım adım yönergeler için bkz: [nasıl yapılır: Bir SSL sertifikası ile bir bağlantı noktası yapılandırma](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md).  
  
## <a name="configuring-the-ip-listen-list"></a>IP dinleme listesini yapılandırma  
 Bir kullanıcı bir URL kaydeder sonra HTTP Sunucusu API yalnızca bir IP adresi ve bağlantı noktası bağlar. Varsayılan olarak, tüm IP adreslerini makinenin URL'si bağlantı noktası HTTP Sunucusu API bağlar. HTTP sunucu API kullanmaz uygulamanın IP adresini ve bağlantı noktası birleşimi için önceden bağlıysa bir çakışma ortaya çıkar. Dinleme IP listesi ile makine IP adreslerini bazıları için bağlantı noktası kullanan uygulamalar bulunabilmesi WCF hizmetleri sağlar. Dinleme IP listesi herhangi bir giriş içeriyorsa, HTTP sunucu API yalnızca listesini belirtir. Bu IP adresine bağlar. Dinleme IP listesini değiştirme yönetimsel ayrıcalıklar gerekiyor.  
  
### <a name="running-windows-xp-or-server-2003"></a>Çalışan Windows XP veya Server 2003  
 Aşağıdaki örnekte gösterildiği gibi IP dinleme listesini değiştirmek için httpcfg aracını kullanın. [Windows Destek Araçları belgeleri](https://go.microsoft.com/fwlink/?LinkId=94840) httpcfg.exe aracın sözdizimi açıklar.  
  
```console  
httpcfg.exe set iplisten -i 0.0.0.0:8000  
```  
  
### <a name="running-windows-vista-or-windows-7"></a>Çalıştıran Windows Vista veya Windows 7  
 Aşağıdaki örnekte gösterildiği gibi dinleme IP listesini değiştirmek için netsh aracını kullanın.  
  
```console  
netsh http add iplisten ipaddress=0.0.0.0:8000  
```  
  
## <a name="other-configuration-settings"></a>Diğer yapılandırma ayarları  
 Kullanırken <xref:System.ServiceModel.WSDualHttpBinding>, ad alanı ayırmaları ve Windows Güvenlik Duvarı ile uyumlu olan varsayılan istemci bağlantı kullanır. Bir çift bağlantı istemci temel adresini özelleştirmek seçerseniz, ardından bu HTTP ayarları yeni adresiyle eşleşecek şekilde istemcide yapılandırmanız da gerekir.  
  
 HTTP sunucu API HttpCfg kullanılabilir olmayan bazı gelişmiş yapılandırma ayarları vardır. Bu ayarlar kayıt defterinde saklanır ve HTTP sunucusu API'lerini kullanan sistemlerde çalışan tüm uygulamalar için geçerlidir. Bu ayarlar hakkında daha fazla bilgi için bkz: [IIS için Http.sys kayıt defteri ayarları](https://go.microsoft.com/fwlink/?LinkId=94843). Çoğu kullanıcı bu ayarları değiştirmek gerekmez.  
  
## <a name="issues-specific-to-windows-xp"></a>Windows XP için belirli sorunları  
 IIS üzerinde bağlantı noktası paylaşımı desteklemez [!INCLUDE[wxp](../../../../includes/wxp-md.md)]. IIS çalıştıran ve bir WCF hizmeti bir ad alanı ile aynı bağlantı noktası kullanmayı dener WCF hizmeti başlatmak başarısız olur. 80 numaralı bağlantı noktasını kullanarak hem de varsayılan IIS ve WCF. Hizmetlerden biri için bağlantı noktası atamasını değiştirin veya WCF hizmeti, IIS tarafından kullanılmayan bir ağ bağdaştırıcısı atamak için dinleme IP listeyi kullanın. IIS 6.0 ve üzeri HTTP sunucu API'leri kullanmak için tasarlanmıştır.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.ServiceModel.WSDualHttpBinding>
- [Nasıl yapılır: Bir SSL sertifikası ile bir bağlantı noktası yapılandırma](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)
