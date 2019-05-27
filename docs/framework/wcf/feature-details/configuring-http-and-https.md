---
title: HTTP ve HTTPS - WCF yapılandırma
ms.date: 04/08/2019
helpviewer_keywords:
- configuring HTTP [WCF]
ms.assetid: b0c29a86-bc0c-41b3-bc1e-4eb5bb5714d4
ms.openlocfilehash: 4bfdbbc19bb9ed72bc50ebeeac114241ccd47c25
ms.sourcegitcommit: 7e129d879ddb42a8b4334eee35727afe3d437952
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66053408"
---
# <a name="configuring-http-and-https"></a>HTTP ve HTTPS Yapılandırma

WCF hizmetleri ve istemcilerin HTTP ve HTTPS üzerinden iletişim kurabilir. HTTP/HTTPS ayarları, Internet Information Services (IIS) kullanarak veya bir komut satırı aracı kullanılarak yapılandırılır. Bir WCF Hizmeti IIS HTTP veya HTTPS ayarlarında zaman barındırılan (inetmgr.exe aracını kullanarak) IIS içinde yapılandırılabilir. Şirket içinde barındırılan bir WCF Hizmeti ise, bir komut satırı aracını kullanarak HTTP veya HTTPS ayarları yapılandırılır.

En az bir URL kaydını yapılandırma ve hizmetinizi kullanarak URL için bir güvenlik duvarı istisnasının eklemek istiyor. Netsh.exe aracı, bu ayarları yapılandırabilirsiniz.

## <a name="configuring-namespace-reservations"></a>Ad alanı ayırmaları yapılandırma

Namespace ayırma HTTP URL ad alanını bir kısmını haklarını belirli bir kullanıcı grubuna atar. Rezervasyon kullanıcılarla ad alanı kısmı üzerinde dinleme hizmetleri oluşturma hakkı verir. Ayırmaları URL ön ekleri, rezervasyon ayırma yolun tüm alt kapsayan anlamı olan. Namespace ayırmaları joker karakter kullanmanın iki yolu izin verir. HTTP sunucu API belgelerde [joker karakterler içeren ad alanı talep arasındaki çözümleme sırasını](/windows/desktop/Http/routing-incoming-requests).

Ad alanı kayıtları eklemek için benzer bir istek, çalışan bir uygulama oluşturabilirsiniz. Kayıtları ve ayırmaları ad alanının bölümleri için yarışın. Rezervasyon çözümleme verilen sırasına göre bir kayıt üzerinde önceliğe sahip [joker karakterler içeren ad alanı talep arasındaki çözümleme sırasını](/windows/desktop/Http/routing-incoming-requests). Bu durumda, rezervasyon çalışan uygulama isteklerini almasını engeller.

Aşağıdaki örnek, Netsh.exe aracını kullanır:

```console
netsh http add urlacl url=http://+:80/MyUri user=DOMAIN\user
```

Bu komut, etki alanı\kullanıcı hesabı için belirtilen URL ad alanı için bir URL ayırmasını ekler. Netsh komutunu kullanma hakkında daha fazla bilgi için türü `netsh http add urlacl /?` bir komut istemi ve Enter tuşuna basın.

## <a name="configuring-a-firewall-exception"></a>Bir güvenlik duvarı özel durum yapılandırma

Bir özel durum kendi kendine HTTP üzerinden iletişim kuran bir WCF Hizmeti barındırma, belirli bir URL kullanarak gelen bağlantılara izin vermek için güvenlik duvarı yapılandırması eklenmesi gerekir.

## <a name="configuring-ssl-certificates"></a>SSL sertifikaları yapılandırma

Güvenli Yuva Katmanı (SSL) protokolü şifreleme anahtarlarını depolamak için istemci ve sunucu sertifikaları kullanır. İstemci, sunucu kimliğini doğrulayabilir bir bağlantı yapıldığında sunucu SSL sertifikasını sağlar. Sunucu, istemciden bağlantının her iki tarafının karşılıklı kimlik doğrulaması sağlamak için ayrıca bir sertifika isteyebilir.

Sertifikaları Merkezi bir depolama bağlantı IP adresi ve bağlantı noktası numarasını göre depolanır. Özel IP adresi 0.0.0.0 yerel makine için herhangi bir IP adresi ile eşleşir. Sertifika deposu URL'leri yola göre ayırt etmez unutmayın. Hizmetler için URL yolu farklı olsa bile aynı IP adresi ve bağlantı noktası bileşimi ile hizmet sertifikaları paylaşmanız gerekir.

Adım adım yönergeler için bkz: [nasıl yapılır: Bir SSL sertifikası ile bir bağlantı noktası yapılandırma](how-to-configure-a-port-with-an-ssl-certificate.md).

## <a name="configuring-the-ip-listen-list"></a>IP dinleme listesini yapılandırma

Bir kullanıcı bir URL kaydeder sonra HTTP Sunucusu API yalnızca bir IP adresi ve bağlantı noktası bağlar. Varsayılan olarak, tüm IP adreslerini makinenin URL'si bağlantı noktası HTTP Sunucusu API bağlar. HTTP sunucu API kullanmayan bir uygulama daha önce bu IP adresi ve bağlantı noktası bileşimi için bağlıysa bir çakışma ortaya çıkar. Dinleme IP listesi ile makine IP adreslerini bazıları için bağlantı noktası kullanan uygulamalar bulunabilmesi WCF hizmetleri sağlar. Dinleme IP listesi herhangi bir giriş içeriyorsa, HTTP sunucu API yalnızca listesini belirtir. Bu IP adresine bağlar. Dinleme IP listesini değiştirme yönetimsel ayrıcalıklar gerekiyor.

Aşağıdaki örnekte gösterildiği gibi IP dinleme listesini değiştirmek için netsh aracını kullanın:

```console
netsh http add iplisten ipaddress=0.0.0.0:8000
```

## <a name="other-configuration-settings"></a>Diğer yapılandırma ayarları

Kullanırken <xref:System.ServiceModel.WSDualHttpBinding>, ad alanı ayırmaları ve Windows Güvenlik Duvarı ile uyumlu olan varsayılan istemci bağlantı kullanır. Bir çift bağlantı istemci temel adresini özelleştirmek seçerseniz, ardından bu HTTP ayarları yeni adresiyle eşleşecek şekilde istemcide yapılandırmanız da gerekir.

HTTP sunucu API HttpCfg kullanılamayan bazı gelişmiş yapılandırma ayarları vardır. Bu ayarlar kayıt defterinde saklanır ve HTTP sunucusu API'lerini kullanan sistemlerde çalışan tüm uygulamalar için geçerlidir. Bu ayarlar hakkında daha fazla bilgi için bkz: [IIS için Http.sys kayıt defteri ayarları](https://support.microsoft.com/help/820129/http-sys-registry-settings-for-windows). Çoğu kullanıcı bu ayarları değiştirmek gerekmez.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.WSDualHttpBinding>
- [Nasıl yapılır: Bir SSL sertifikası ile bir bağlantı noktası yapılandırma](how-to-configure-a-port-with-an-ssl-certificate.md)
