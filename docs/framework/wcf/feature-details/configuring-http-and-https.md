---
title: HTTP ve HTTPS Yapılandırma
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- configuring HTTP [WCF]
ms.assetid: b0c29a86-bc0c-41b3-bc1e-4eb5bb5714d4
caps.latest.revision: 17
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 8d3317cd4bba7c9935bd7555f16599dc94725fbd
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="configuring-http-and-https"></a>HTTP ve HTTPS Yapılandırma
WCF hizmetleri ve istemcilerin HTTP ve HTTPS iletişim kurabilir. HTTP/HTTPS ayarları, Internet Information Services (IIS) kullanarak veya bir komut satırı aracı kullanılarak yapılandırılır. Bir WCF Hizmeti IIS HTTP veya HTTPS ayarları altında olduğunda barındırılan (inetmgr.exe Aracı'nı kullanarak) IIS içinde yapılandırılabilir. Bir WCF Hizmeti kendini barındıran ise, bir komut satırı aracını kullanarak HTTP veya HTTPS ayarları yapılandırılır.  
  
 En azından bir URL kaydı yapılandırmak ve hizmetinizi kullanarak URL için bir güvenlik duvarı özel durumu eklemek istersiniz.  
  
 HTTP ayarlarını yapılandırmak için kullanılan aracı bilgisayarda çalışan işletim sistemine bağlıdır.  
  
 Çalıştırırken [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] veya [!INCLUDE[wxp](../../../../includes/wxp-md.md)], HttpCfg.exe aracını kullanın. [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] Bu araç otomatik olarak yükler. Çalıştırırken [!INCLUDE[wxp](../../../../includes/wxp-md.md)], aracı indirebilirsiniz [Windows XP Service Pack 2 Destek Araçları](http://go.microsoft.com/fwlink/?LinkId=88606). Daha fazla bilgi için bkz: [Httpcfg genel bakış](http://go.microsoft.com/fwlink/?LinkId=88605).  
  
 Çalıştırırken [!INCLUDE[wv](../../../../includes/wv-md.md)]veya Windows 7, yapılandırdığınız bu ayarlar Netsh.exe aracıyla.  
  
## <a name="configuring-namespace-reservations"></a>Namespace ayırmaları yapılandırma  
 Namespace ayırma HTTP URL ad alanı bir kısmı rights kullanıcıların belirli bir gruba atar. Bir ayırma kullanıcılarla ad alanı bu kısmı üzerinde dinleme hizmetler oluşturma hakkı verir. Ayırmalar ayırma ayırma yolun tüm alt yolları kapsanmakta anlamına gelir, URL ön ekleri. Namespace ayırmaları joker karakter kullanmanın iki yolu izin verir. HTTP Sunucusu API belgelerine açıklar [joker karakterler içeren ad alanı talep arasında çözümleme sırasını](http://go.microsoft.com/fwlink/?LinkId=94841).  
  
 Çalışan bir uygulama, ad alanı kayıtları eklemek için benzer bir isteği oluşturabilirsiniz. Kayıtlar ve ayırmaları ad bölümleri için rekabet. Bir ayırma verilen çözümleme sırasını göre bir kayıt üzerinden öncelik olabilir [joker karakterler içeren ad alanı talep arasında çözümleme sırasını](http://go.microsoft.com/fwlink/?LinkId=94841). Bu durumda, ayırma isteklerini almasını çalışan uygulama engeller.  
  
### <a name="running-windows-xp-or-server-2003"></a>Çalışan Windows XP veya Server 2003  
 Kullanım `httpcfg.exe set urlacl` ad alanı ayırmalarını değiştirmek için komutu. [Windows Destek Araçları belgeleri](http://go.microsoft.com/fwlink/?LinkId=94840) Httpcfg.exe araç söz dizimi açıklanmıştır. Ad alanı bir kısmı için ayırma hakları değiştirme, yönetici ayrıcalıkları veya ad alanı bölümünü sahipliğini gerektirir. Başlangıçta, tüm HTTP ad alanı için yerel yönetici aittir.  
  
 Aşağıdaki Httpcfg komutuyla söz dizimi görülmektedir `set urlacl` seçeneği  
  
```  
httpcfg set urlacl /u {http://URL:Port/ | https://URL:Port/} /aACL  
```  
  
 `/u` Parametresi, kullanılırken gereklidir `set urlacl`. Yapılmakta ayırma kayıt anahtarı olarak hizmet veren tam bir URL içeren bir dize alır.  
  
 `/a` Parametresi gereklidir da kullanırken `set urlacl`. Bir güvenlik tanımlayıcısı tanım dili (SDDL) dizesi biçiminde erişim denetimi listesi (ACL) içeren bir dize alır.  
  
 Bu komutu kullanma örneği gösterir.  
  
```  
httpcfg.exe set urlacl /u http://myhost:8000/ /a "O:AOG:DAD:(A;;RPWPCCDCLCSWRCWDWOGA;;;S-1-0-0)"  
```  
  
### <a name="running-windows-vista-windows-server-2008-r2-or-windows-7"></a>Windows Vista, Windows Server 2008 R2 veya Windows 7 çalıştıran  
 Çalıştırıyorsanız, [!INCLUDE[wv](../../../../includes/wv-md.md)], Windows Server 2008 R2 veya Windows 7, Netsh.exe aracını kullanın. Bu komutu kullanma örneği gösterir.  
  
```  
netsh http add urlacl url=http://+:80/MyUri user=DOMAIN\user  
```  
  
 Bu komut, etki alanı\kullanıcı hesabı için belirtilen URL ad alanı için bir URL ayırmasını ekler.  Netsh komut türü kullanma hakkında daha fazla bilgi için "netsh http add urlacl" bir komut istemi ve tuşuna girin.  
  
## <a name="configuring-a-firewall-exception"></a>Bir güvenlik duvarı özel durumu yapılandırma  
 HTTP üzerinden iletişim kuran bir WCF Hizmeti kendini barındırdığında, belirli bir URL'yi kullanarak gelen bağlantılara izin vermek için güvenlik duvarı yapılandırması için bir özel durum eklenmesi gerekir. Daha fazla bilgi için bkz: [(Windows 7) Windows Güvenlik Duvarı'nda bir bağlantı noktasını açın](http://go.microsoft.com/fwlink/?LinkId=239961)  
  
## <a name="configuring-ssl-certificates"></a>SSL sertifikalarını yapılandırma  
 Güvenli Yuva Katmanı (SSL) protokolü şifreleme anahtarlarını depolamak için istemci ve sunucu sertifikaları kullanır. Böylece istemci, sunucu kimliğini doğrulayabilir bir bağlantı yapıldığında sunucu SSL sertifikasını sağlar. Sunucu bağlantısı her iki tarafının karşılıklı kimlik doğrulaması sağlamak için istemciden bir sertifika isteğinde bulunabilirsiniz.  
  
 Sertifikaları Merkezi bir mağaza bağlantısı IP adresi ve bağlantı noktası numarasını göre depolanır. Özel IP adresi 0.0.0.0 yerel makine için herhangi bir IP adresi eşleşir. Sertifika deposu URL'leri yola göre ayırt etmez unutmayın. Hizmetler için URL yolu farklı olsa bile aynı IP adresi ve bağlantı noktası bileşimi hizmetleriyle sertifikaları paylaşmalıdır.  
  
 Adım adım yönergeler için bkz: [nasıl yapılır: bir SSL sertifikası ile bir bağlantı noktası yapılandırın](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md).  
  
## <a name="configuring-the-ip-listen-list"></a>IP dinleme listesi yapılandırma  
 Bir kullanıcı bir URL kaydeder sonra HTTP sunucu API'sini yalnızca bir IP adresi ve bağlantı noktasına bağlar. Varsayılan olarak, HTTP sunucu API'sini tüm makinenin IP adresleri için URL'de bağlantı noktasına bağlar. HTTP Sunucusu API kullanmayan bir uygulama bu IP adresi ve bağlantı noktası bileşimi için daha önce bağlı bir çakışma ortaya çıkar. IP dinleme listesi verir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] bazı makinenin IP adresleri için bir bağlantı noktası kullanan uygulamalar ile bir arada Hizmetleri. IP dinleme listesi herhangi bir giriş içeriyorsa, HTTP sunucu API'sini listesini belirtir bu IP adreslerinden yalnızca bağlar. IP dinleme listesi değiştirme yönetici ayrıcalıkları gerektirir.  
  
### <a name="running-windows-xp-or-server-2003"></a>Çalışan Windows XP veya Server 2003  
 Aşağıdaki örnekte gösterildiği gibi IP dinleme listesi değiştirmek için httpcfg Aracı'nı kullanın. [Windows Destek Araçları belgeleri](http://go.microsoft.com/fwlink/?LinkId=94840) httpcfg.exe araç söz dizimi açıklanmıştır.  
  
```  
httpcfg.exe set iplisten -i 0.0.0.0:8000  
```  
  
### <a name="running-windows-vista-or-windows-7"></a>Windows çalıştıran Vista veya Windows 7  
 Aşağıdaki örnekte gösterildiği gibi IP dinleme listesi değiştirmek için netsh aracını kullanın.  
  
```  
netsh http add iplisten ipaddress=0.0.0.0:8000  
```  
  
## <a name="other-configuration-settings"></a>Diğer yapılandırma ayarları  
 Kullanırken <xref:System.ServiceModel.WSDualHttpBinding>, istemci bağlantısı ad alanı ayırmaları ve Windows Güvenlik Duvarı ile uyumlu Varsayılanları kullanır. Bir çift bağlantı istemci temel adresini özelleştirmek seçerseniz, ardından bu HTTP ayarları yeni adresi eşleştirmek için istemcide yapılandırmanız da gerekir.  
  
 HTTP Sunucusu API HttpCfg kullanılabilir olmayan bazı gelişmiş yapılandırma ayarları vardır. Bu ayarlar kayıt defterinde saklanır ve HTTP sunucusu API'lerini kullanan sistemleri üzerinde çalışan tüm uygulamaları için geçerlidir. Bu ayarlar hakkında daha fazla bilgi için bkz: [IIS için Http.sys kayıt defteri ayarları](http://go.microsoft.com/fwlink/?LinkId=94843). Çoğu kullanıcı bu ayarları değiştirmek gerekmez.  
  
## <a name="issues-specific-to-windows-xp"></a>Windows XP özgü sorunlar  
 IIS üzerinde bağlantı noktası paylaşımı desteklemiyor [!INCLUDE[wxp](../../../../includes/wxp-md.md)]. IIS çalışıyorsa ve bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmeti çalışır aynı bağlantı noktası ile bir ad alanını kullanmak [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmet başarısız başlatmak. IIS ve [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] her ikisi de 80 numaralı bağlantı noktasını kullanarak varsayılan. Hizmetlerden biri için bağlantı noktası atamasını değiştirin veya atamak için IP dinleme listesi kullanmaya [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] IIS tarafından kullanılmayan bir ağ bağdaştırıcısı için hizmet. IIS 6.0 ve sonraki HTTP Sunucusu API'ları kullanmak için tasarlanmıştır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.WSDualHttpBinding>  
 [Nasıl Yapılır: SSL Sertifikası ile Bir Bağlantı Noktasını Yapılandırma](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)
