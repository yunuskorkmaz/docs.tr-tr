---
title: HTTP ve HTTPS Yapılandırma
description: WCF Hizmetleri ve istemcilerinin iletişim kurmasına izin vermek için HTTP/HTTPS 'yi nasıl yapılandıracağınızı öğrenin. Netsh.exe kullanarak bir URL kaydı ve güvenlik duvarı özel durumu yapılandırın.
ms.date: 04/08/2019
helpviewer_keywords:
- configuring HTTP [WCF]
ms.assetid: b0c29a86-bc0c-41b3-bc1e-4eb5bb5714d4
ms.openlocfilehash: fbff78ff8e2c5c4fa73a56a3fdc15163596aa985
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85245147"
---
# <a name="configuring-http-and-https"></a>HTTP ve HTTPS Yapılandırma

WCF Hizmetleri ve istemcileri HTTP ve HTTPS üzerinden iletişim kurabilir. HTTP/HTTPS ayarları, Internet Information Services (IIS) kullanılarak veya bir komut satırı aracının kullanımı aracılığıyla yapılandırılır. Bir WCF hizmeti IIS HTTP altında barındırılıyorsa veya HTTPS ayarları IIS içinde yapılandırılabilirler (inetmgr.exe Aracı kullanılarak). Bir WCF hizmeti kendinden barındırılıyorsa, HTTP veya HTTPS ayarları bir komut satırı aracı kullanılarak yapılandırılır.

En azından, bir URL kaydı yapılandırmak ve hizmetinizin kullanacağı URL için bir güvenlik duvarı özel durumu eklemek istersiniz. Bu ayarları Netsh.exe aracı ile yapılandırabilirsiniz.

## <a name="configuring-namespace-reservations"></a>Ad alanı ayırmalarını yapılandırma

Ad alanı ayırma, HTTP URL ad alanının bir bölümü için belirli bir kullanıcı grubuna haklar atar. Ayırma, bu kullanıcılara ad alanının o bölümünü dinleyen hizmetler oluşturma hakkını verir. Ayırmalar, rezervasyon yolunun tüm alt yollarını kapsamakta olduğu anlamına gelen URL öneklerdir. Ad alanı ayırmaları, joker karakterleri kullanmanın iki yolunu sağlar. HTTP Sunucusu API 'SI belgeleri, [joker karakterleri içeren ad alanı talepleri arasındaki çözümlemenin sırasını](/windows/desktop/Http/routing-incoming-requests)açıklar.

Çalışan bir uygulama, ad alanı kayıtları eklemek için benzer bir istek oluşturabilir. Kayıt ve rezervasyonlar ad alanının bölümleri için rekabet. Bir ayırma, [joker karakterleri içeren ad alanı talepleri arasındaki çözümleme sırasında](/windows/desktop/Http/routing-incoming-requests)verilen çözümleme sırasına göre kayıt üzerinde önceliğe sahip olabilir. Bu durumda, ayırma çalışan uygulamanın istekleri almasını engeller.

Aşağıdaki örnek Netsh.exe aracını kullanır:

```console
netsh http add urlacl url=http://+:80/MyUri user=DOMAIN\user
```

Bu komut, etkialanı \ Kullanıcı hesabı için belirtilen URL ad alanı için bir URL ayırması ekler. Netsh komutunu kullanma hakkında daha fazla bilgi için `netsh http add urlacl /?` komut istemine yazın ve ENTER tuşuna basın.

## <a name="configuring-a-firewall-exception"></a>Güvenlik Duvarı özel durumu yapılandırma

HTTP üzerinden iletişim kuran bir WCF hizmetini kendinden barındırdığında, belirli bir URL 'YI kullanarak gelen bağlantılara izin vermek için Güvenlik Duvarı yapılandırmasına bir özel durum eklenmelidir.

## <a name="configuring-ssl-certificates"></a>SSL sertifikalarını yapılandırma

Güvenli Yuva Katmanı (SSL) protokolü, şifreleme anahtarlarını depolamak için istemci ve sunucu üzerindeki sertifikaları kullanır. İstemcinin sunucu kimliğini doğrulayabilmesi için bir bağlantı yapıldığında sunucu, SSL sertifikasını sağlar. Sunucu Ayrıca, bağlantının her iki tarafında da karşılıklı kimlik doğrulaması sağlamak üzere istemciden bir sertifika isteyebilir.

Sertifikalar, bağlantının IP adresine ve bağlantı noktası numarasına göre merkezi bir depoda depolanır. 0.0.0.0 özel IP adresi, yerel makinenin herhangi bir IP adresiyle eşleşir. Sertifika deposunun URL 'Leri yola göre ayıramadığını unutmayın. Hizmetler URL 'sindeki yol farklı olsa da, aynı IP adresi ve bağlantı noktası birleşimine sahip hizmetler sertifikaları paylaşmalıdır.

Adım adım yönergeler için bkz. [nasıl yapılır: SSL sertifikası Ile bağlantı noktası yapılandırma](how-to-configure-a-port-with-an-ssl-certificate.md).

## <a name="configuring-the-ip-listen-list"></a>IP dinleme listesini yapılandırma

HTTP Sunucusu API 'si, bir Kullanıcı bir URL 'yi kaydettiğinde bir IP adresine ve bağlantı noktasına bağlanır. Varsayılan olarak, HTTP Sunucusu API 'SI, makinenin tüm IP adresleri için URL 'deki bağlantı noktasına bağlanır. HTTP sunucu API 'sini kullanmayan bir uygulama daha önce bu IP adresi ve bağlantı noktası birleşimine bağlanmışsa bir çakışma ortaya çıkar. IP dinleme listesi, WCF hizmetlerinin, makinenin bazı IP adresleri için bir bağlantı noktası kullanan uygulamalarla birlikte çalışmasına izin verir. IP dinleme listesi herhangi bir giriş içeriyorsa, HTTP Sunucusu API yalnızca listenin belirttiği IP adreslerine bağlanır. IP dinleme listesini değiştirmek için yönetici ayrıcalıkları gerekir.

Aşağıdaki örnekte gösterildiği gibi, IP dinleme listesini değiştirmek için Netsh aracını kullanın:

```console
netsh http add iplisten ipaddress=0.0.0.0:8000
```

## <a name="other-configuration-settings"></a>Diğer yapılandırma ayarları

Kullanırken <xref:System.ServiceModel.WSDualHttpBinding> , istemci bağlantısı ad alanı ayırmaları ve Windows Güvenlik Duvarı ile uyumlu olan Varsayılanları kullanır. İkili bir bağlantının istemci temel adresini özelleştirmeyi seçerseniz, bu HTTP ayarlarını, yeni adresle eşleşecek şekilde istemci üzerinde de yapılandırmanız gerekir.

HTTP Sunucusu API 'sinde, HttpCfg aracılığıyla kullanılamayan bazı gelişmiş yapılandırma ayarları vardır. Bu ayarlar kayıt defterinde tutulur ve HTTP sunucu API 'Lerini kullanan sistemlerde çalışan tüm uygulamalara uygulanır. Bu ayarlar hakkında daha fazla bilgi için bkz. [IIS Için kayıt defteri ayarlarıHttp.sys](https://support.microsoft.com/help/820129/http-sys-registry-settings-for-windows). Çoğu kullanıcının bu ayarları değiştirmesi gerekmez.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.WSDualHttpBinding>
- [Nasıl Yapılır: SSL Sertifikası ile Bir Bağlantı Noktasını Yapılandırma](how-to-configure-a-port-with-an-ssl-certificate.md)
