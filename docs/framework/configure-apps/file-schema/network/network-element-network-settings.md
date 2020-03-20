---
title: <network> Öğesi (Ağ Ayarları)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#network
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings/smtp/network
helpviewer_keywords:
- <network> element
- network element
ms.assetid: 2c2c6ad4-ed11-48ab-b28e-2bc0ba9b42c7
ms.openlocfilehash: f7cfcc3b9d5a717c23175cd15aa48ae97c828e57
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154822"
---
# <a name="network-element-network-settings"></a>\<ağ> Öğesi (Ağ Ayarları)
Harici bir Basit Posta Aktarım Protokolü (SMTP) sunucusu için ağ seçeneklerini yapılandırır.  

[**\<yapılandırma>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<mailAyarlar>**](mailsettings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<smtp>**](smtp-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<ağ>**

## <a name="syntax"></a>Sözdizimi  
  
```xml  
<network  
  clientDomain="string"
  defaultCredentials="true|false"  
  enableSsl="true|false"  
  host="string"
  password="string"  
  port="integer"
  targetName="string"  
  userName="string"  
/>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`clientDomain`|SMTP posta sunucusuna bağlanmak için ilk SMTP protokolü isteğinde kullanılacak istemci etki alanı adını belirtir. Varsayılan değer, isteği gönderen yerel bilgisayarın yerel ana bilgisayar adıdır.|  
|`defaultCredentials`|Varsayılan kullanıcı kimlik bilgilerinin SMTP işlemleri için SMTP posta sunucusuna erişmek için kullanılıp kullanılmayacağını belirtir. Varsayılan değer: `false`.|  
|`enableSsl`|SSL'nin bir SMTP posta sunucusuna erişmek için kullanılıp kullanılmayacağını belirtir. Varsayılan değer: `false`.|  
|`host`|SMTP işlemleri için kullanılacak SMTP posta sunucusunun ana bilgisayar adını belirtir. Bu öznitelik varsayılan değeri vardır.|  
|`password`|Kimlik doğrulaması için Kullanılacak parolayı SMTP posta sunucusuna belirtir. Bu öznitelik varsayılan değeri vardır.|  
|`port`|SMTP posta sunucusuna bağlanmak için kullanılacak bağlantı noktası numarasını belirtir. Varsayılan değer 25'tir.|  
|`targetName`|SMTP işlemleri için genişletilmiş koruma kullanırken kimlik doğrulaması için kullanılacak Servis Sağlayıcı Adını (SPN) belirtir. Bu öznitelik varsayılan değeri vardır.|  
|`userName`|SMTP posta sunucusunda kimlik doğrulaması için kullanılacak kullanıcı adını belirtir. Bu öznitelik varsayılan değeri vardır.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<smtp> Elemanı (Ağ Ayarları)](smtp-element-network-settings.md)|Basit Posta Aktarım Protokolü (SMTP) posta gönderme seçeneklerini yapılandırır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bazı SMTP sunucuları, kullanmadan önce kendinizi sunucuya doğrulamanızı gerektirir. Ana bilgisayarınızdaki varsayılan ağ kimlik bilgilerini kullanarak kimliğinizi `defaultCredentials` doğrulamak istiyorsanız, özniteliği `true`' ne göre ayarlayın. Özellik, <xref:System.Net.Configuration.SmtpNetworkElement.DefaultCredentials%2A?displayProperty=nameWithType> özniteliğin `defaultCredentials` geçerli değerini geçerli yapılandırma dosyalarından almak için kullanılabilir.  
  
 SMTP sunucusuna kimlik doğrulamak için temel kimlik doğrulamayı (kullanıcı adı ve parola) da kullanabilirsiniz. Bu seçeneği kullanmak için, belirtilen SMTP sunucusu için geçerli bir kullanıcı adı ve parola belirtmeniz gerekir.  
  
> [!NOTE]
> Temel kimlik doğrulaması `password` ve değerleri şifrelenmemiş sunucuya gönderir. `userName` Ağ trafiğini izleyen herkes kimlik bilgilerinizi görüntüleyebilir ve bunları sunucuya bağlanmak için kullanabilir. Kerberos veya NT LAN Yöneticisi (NTLM) gibi daha güvenli bir kimlik doğrulama mekanizması kullanmayı düşünmelisiniz. `defaultCredentials` Eğer, `true`sunucu bu protokolleri destekliyorsa, Kerberos veya NTLM kullanılır.  
  
 Temel kimlik doğrulama ve varsayılan ağ kimlik bilgileri seçenekleri birbirini dışlar; Bir kullanıcı `defaultCredentials` `true` adı ve parola yı ayarlar ve belirtirseniz, varsayılan ağ kimlik bilgisi kullanılır ve temel kimlik doğrulama verileri yoksayılır.  
  
 Temel kimlik doğrulaması için, bir `userName`de `password` posta sunucusuna bir kimlik doğrulaması belirtmelisiniz.  
  
 Özellik, <xref:System.Net.Configuration.SmtpNetworkElement.UserName%2A?displayProperty=nameWithType> özniteliğin `userName` geçerli değerini geçerli yapılandırma dosyalarından almak için kullanılabilir. Özellik, <xref:System.Net.Configuration.SmtpNetworkElement.Password%2A?displayProperty=nameWithType> özniteliğin `password` geçerli değerini geçerli yapılandırma dosyalarından almak için kullanılabilir. Bir `password` öznitelik normalde güvenlik nedenleriyle yapılandırma dosyalarına girilmez.  
  
 Öznitelik, `clientDomain` ilk SMTP iletişim kuralı isteğinde kullanılan istemci etki alanı adını bir SMTP sunucusuna değiştirir. Öznitelik, `clientDomain` varsayılan olarak kullanılan yerel ana bilgisayar adı yerine yerel makinenin tam nitelikli etki alanı adına ayarlanabilir. Bu, SMTP protokol standartlarına daha fazla uyumluluk sağlar. Varsayılan değer, isteği gönderen yerel bilgisayarın yerel ana bilgisayar adıdır. Özellik, <xref:System.Net.Configuration.SmtpNetworkElement.ClientDomain%2A?displayProperty=nameWithType> özniteliğin `clientDomain` geçerli değerini geçerli yapılandırma dosyalarından almak için kullanılabilir.  
  
 Öznitelik, `targetName` genişletilmiş koruma kullanılırken kimlik doğrulama için kullanılır. Varsayılan değer,\< \<ana bilgisayar> SMTP posta sunucusunun ana bilgisayarı olduğu "SMTPSVC/ ana bilgisayar>" biçimindedir. Özellik, <xref:System.Net.Configuration.SmtpNetworkElement.TargetName%2A?displayProperty=nameWithType> özniteliğin `targetName` geçerli değerini geçerli yapılandırma dosyalarından almak için kullanılabilir.  
  
 Öznitelik, SSL'nin `enableSsl` bir SMTP posta sunucusuna erişmek için kullanılıp kullanılmayacağını belirtir. Sınıf <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType> yalnızca RFC 3207'de tanımlandığı gibi Taşıma Katmanı Güvenliği üzerinden Güvenli SMTP için SMTP Hizmet Uzantısını destekler. Bu modda, SMTP oturumu şifresiz bir kanalda başlar, ardından istemci tarafından sunucuya bir STARTTLS komutu verilir ve SSL kullanarak güvenli iletişime geçer. Daha fazla bilgi için Internet Engineering Task Force (IETF) tarafından yayınlanan RFC 3207'ye bakın.  
  
 Alternatif bağlantı yöntemi, herhangi bir protokol komutu gönderilmeden önce bir SSL oturumunun önceden oluşturulduğü yöntemdir. Bu bağlantı yöntemi bazen SMTPS olarak adlandırılır ve varsayılan olarak 465 bağlantı noktasını kullanır. SSL kullanan bu alternatif bağlantı yöntemi şu anda desteklenmez.  
  
 Özellik, <xref:System.Net.Configuration.SmtpNetworkElement.EnableSsl%2A?displayProperty=nameWithType> özniteliğin `enableSsl` geçerli değerini geçerli yapılandırma dosyalarından almak için kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, varsayılan ağ kimlik bilgilerini kullanarak e-posta göndermek için uygun SMTP parametreleri belirtilmez.  
  
```xml  
<configuration>  
  <system.net>  
    <mailSettings>  
      <smtp deliveryMethod="Network">  
        <network  
          clientDomain="www.contoso.com"  
          defaultCredentials="true"  
          enableSsl="false"  
          host="mail.contoso.com"  
          port="25"  
        />  
      </smtp>  
    </mailSettings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Net.Configuration.SmtpNetworkElement?displayProperty=nameWithType>
- <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>
- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- [Ağ Ayarları Şeması](index.md)
