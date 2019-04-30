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
ms.openlocfilehash: c411e00026f03fdb355664049f8db00f3c800352
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61674460"
---
# <a name="network-element-network-settings"></a>\<Ağ > öğesi (ağ ayarları)
Harici bir Basit Posta Aktarım Protokolü (SMTP) sunucusu ağ seçeneklerini yapılandırır.  
  
 \<Yapılandırma >  
\<system.net>  
\<mailSettings >  
\<SMTP >  
\<Ağ >  
  
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
|`clientDomain`|İlk SMTP protokolünü istekte SMTP posta sunucusuna bağlanmak için kullanılacak istemci etki alanı adını belirtir. Varsayılan değer isteği yerel bilgisayar localhost adıdır.|  
|`defaultCredentials`|SMTP işlemleri için SMTP posta sunucusuna erişmek için varsayılan kullanıcı kimlik bilgilerinin kullanılıp kullanılmayacağını belirtir. Varsayılan değer `false` şeklindedir.|  
|`enableSsl`|Bir SMTP posta sunucusuna erişmek için SSL kullanılıp kullanılmayacağını belirtir. Varsayılan değer `false` şeklindedir.|  
|`host`|SMTP işlemleri için kullanılacak SMTP posta sunucusu konak adı belirtir. Bu öznitelik varsayılan değeri yok.|  
|`password`|SMTP posta sunucusuna kimlik doğrulaması için kullanılacak parolayı belirtir. Bu öznitelik varsayılan değeri yok.|  
|`port`|SMTP posta sunucusuna bağlanmak için kullanılacak bağlantı noktası numarasını belirtir. Varsayılan değer 25'tir.|  
|`targetName`|SMTP işlemleri için genişletilmiş koruma kullanarak kimlik doğrulaması için kullanılacak hizmet sağlayıcı adı (SPN) belirtir. Bu öznitelik varsayılan değeri yok.|  
|`userName`|SMTP posta sunucusuna kimlik doğrulaması için kullanılacak kullanıcı adını belirtir. Bu öznitelik varsayılan değeri yok.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<SMTP > öğesi (ağ ayarları)](../../../../../docs/framework/configure-apps/file-schema/network/smtp-element-network-settings.md)|Basit Posta Aktarım Protokolü (SMTP) posta gönderme seçeneklerini yapılandırır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bazı SMTP sunucuları, kendiniz kullanmadan önce sunucuya kimlik doğrulaması gerektirir. İsterseniz, konaktaki varsayılan ağ kimlik bilgilerini kullanarak kimlik doğrulaması ayarlayın `defaultCredentials` özniteliğini `true`. <xref:System.Net.Configuration.SmtpNetworkElement.DefaultCredentials%2A?displayProperty=nameWithType> Özelliği, geçerli değerini almak için kullanılabilir `defaultCredentials` geçerli yapılandırma dosyalarından özniteliği.  
  
 Temel kimlik doğrulaması (bir kullanıcı adı ve parola) kendiniz SMTP sunucusuna kimlik doğrulaması için de kullanabilirsiniz. Bu seçeneği kullanmak için geçerli bir kullanıcı adı ve belirtilen SMTP sunucusu için parola belirtmeniz gerekir.  
  
> [!NOTE]
>  Temel kimlik doğrulaması `userName` ve `password` sunucuya şifrelenmemiş değerleri. Herkes ağ trafiğini izleme, kimlik bilgilerinizi görüntüleyin ve sunucuya bağlanmak için bunları kullanın. Kerberos ya da NT LAN Manager (NTLM) gibi daha güvenli bir kimlik doğrulama mekanizması kullanmayı düşünmeniz gerekir Varsa `defaultCredentials` olduğu `true`, Kerberos veya NTLM kullanılacak sunucunun bu protokolleri destekliyorsa.  
  
 Temel kimlik doğrulaması ve varsayılan ağ kimlik bilgileri seçenekler birbirini dışlıyor; ayarlarsanız `defaultCredentials` için `true` ve bir kullanıcı adı ve parola belirtin, varsayılan ağ kimlik bilgisi kullanılır ve temel kimlik doğrulama verilerini göz ardı edilir.  
  
 Belirtirseniz, temel kimlik doğrulaması için bir `userName`, de belirtmeniz bir `password` kimlik doğrulaması için kendinize e-posta sunucusu.  
  
 <xref:System.Net.Configuration.SmtpNetworkElement.UserName%2A?displayProperty=nameWithType> Özelliği, geçerli değerini almak için kullanılabilir `userName` geçerli yapılandırma dosyalarından özniteliği. <xref:System.Net.Configuration.SmtpNetworkElement.Password%2A?displayProperty=nameWithType> Özelliği, geçerli değerini almak için kullanılabilir `password` geçerli yapılandırma dosyalarından özniteliği. A `password` özniteliği değil normalde girilmesi yapılandırma dosyalarında güvenlik nedenleriyle.  
  
 `clientDomain` İlk SMTP protokolünü isteğinde bir SMTP sunucusu için kullanılan istemci etki alanı adı özniteliği değiştirir. `clientDomain` Özniteliği, varsayılan olarak kullanılan localhost adı yerine tam etki alanı adı yerel makine ayarlanabilir. Bu, SMTP protokolü standartları ile daha yüksek uyumluluk sağlar. Varsayılan değer isteği yerel bilgisayar localhost adıdır. <xref:System.Net.Configuration.SmtpNetworkElement.ClientDomain%2A?displayProperty=nameWithType> Özelliği, geçerli değerini almak için kullanılabilir `clientDomain` geçerli yapılandırma dosyalarından özniteliği.  
  
 `targetName` Özniteliği, genişletilmiş koruma kullanarak kimlik doğrulaması için kullanılır. Varsayılan değer biçimindedir "SMTPSVC /\<konak >" nerede \<konak > SMTP posta sunucusunun adıdır. <xref:System.Net.Configuration.SmtpNetworkElement.TargetName%2A?displayProperty=nameWithType> Özelliği, geçerli değerini almak için kullanılabilir `targetName` geçerli yapılandırma dosyalarından özniteliği.  
  
 `enableSsl` Özniteliği, bir SMTP posta sunucusuna erişmek için SSL kullanılıp kullanılmayacağını belirtir. <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType> Sınıfı yalnızca destekler SMTP hizmeti uzantısı için SMTP güvenli Aktarım Katmanı Güvenliği RFC 3207 içinde tanımlanan. Bu modda, şifrelenmemiş bir kanal SMTP oturumunu başlar ve daha STARTTLS komutu sunucusuna SSL kullanarak güvenli iletişim için geçiş yapmak için istemci tarafından verilir. RFC 3207 yayımlanan Internet Engineering Task Force (IETF) tarafından daha fazla bilgi için bkz.  
  
 Burada bir SSL Önden komutları gönderilen herhangi bir protokol önce oturumun bir alternatif bağlantı yöntemidir. Bu bağlantı yöntemi SMTPS adlandırılır ve varsayılan olarak bağlantı noktası 465 kullanır. SSL kullanarak bu alternatif bağlantı yöntemini şu anda desteklenmiyor.  
  
 <xref:System.Net.Configuration.SmtpNetworkElement.EnableSsl%2A?displayProperty=nameWithType> Özelliği, geçerli değerini almak için kullanılabilir `enableSsl` geçerli yapılandırma dosyalarından özniteliği.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, varsayılan ağ kimlik bilgilerini kullanarak e-posta göndermek için uygun SMTP parametrelerini belirtir.  
  
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
- [Ağ Ayarları Şeması](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
