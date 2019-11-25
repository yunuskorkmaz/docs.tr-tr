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
ms.openlocfilehash: f7b73a725cd406df9ce41e2c4522850ce974022f
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74089211"
---
# <a name="network-element-network-settings"></a>\<ağ > öğesi (ağ ayarları)
Harici bir Basit Posta Aktarım Protokolü (SMTP) sunucusu için ağ seçeneklerini yapılandırır.  

[ **\<configuration >** ](../configuration-element.md) \
[**System. net >\<** ](system-net-element-network-settings.md) &nbsp;&nbsp;\
&nbsp;&nbsp;&nbsp;&nbsp;\<[**mailSettings >** ](mailsettings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<smtp >** ](smtp-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<ağ >**

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
|`clientDomain`|SMTP posta sunucusuna bağlanmak için ilk SMTP protokol isteğinde kullanılacak istemci etki alanı adını belirtir. Varsayılan değer, isteği gönderen yerel bilgisayarın localhost adıdır.|  
|`defaultCredentials`|SMTP işlemleri için SMTP posta sunucusuna erişmek üzere varsayılan kullanıcı kimlik bilgilerinin kullanılıp kullanılmayacağını belirtir. Varsayılan değer `false` şeklindedir.|  
|`enableSsl`|SMTP posta sunucusuna erişmek için SSL kullanılıp kullanılmayacağını belirtir. Varsayılan değer `false` şeklindedir.|  
|`host`|SMTP işlemleri için kullanılacak SMTP posta sunucusunun ana bilgisayar adını belirtir. Bu özniteliğin varsayılan değeri yok.|  
|`password`|SMTP posta sunucusunda kimlik doğrulaması için kullanılacak parolayı belirtir. Bu özniteliğin varsayılan değeri yok.|  
|`port`|SMTP posta sunucusuna bağlanmak için kullanılacak bağlantı noktası numarasını belirtir. Varsayılan değer 25 ' tir.|  
|`targetName`|SMTP işlemleri için genişletilmiş koruma kullanılırken kimlik doğrulaması için kullanılacak hizmet sağlayıcı adını (SPN) belirtir. Bu özniteliğin varsayılan değeri yok.|  
|`userName`|SMTP posta sunucusunda kimlik doğrulaması için kullanılacak kullanıcı adını belirtir. Bu özniteliğin varsayılan değeri yok.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<SMTP > öğesi (ağ ayarları)](smtp-element-network-settings.md)|Basit Posta Aktarım Protokolü (SMTP) posta gönderme seçeneklerini yapılandırır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bazı SMTP sunucuları, kullanmadan önce sunucuda kimlik doğrulamasından geçmesini gerektirir. Ana bilgisayarınızdaki varsayılan ağ kimlik bilgilerini kullanarak kendiniz kimlik doğrulaması yapmak istiyorsanız `defaultCredentials` özniteliğini `true`olarak ayarlayın. <xref:System.Net.Configuration.SmtpNetworkElement.DefaultCredentials%2A?displayProperty=nameWithType> özelliği, uygun yapılandırma dosyalarından `defaultCredentials` özniteliğinin geçerli değerini almak için kullanılabilir.  
  
 SMTP sunucusunda kimlik doğrulaması yapmak için temel kimlik doğrulaması (bir Kullanıcı adı ve parola) de kullanabilirsiniz. Bu seçeneği kullanmak için, belirtilen SMTP sunucusu için geçerli bir Kullanıcı adı ve parola belirtmeniz gerekir.  
  
> [!NOTE]
> Temel kimlik doğrulaması, `userName` ve `password` değerlerini sunucuya şifrelenmemiş şekilde gönderir. Ağ trafiğini izleyen herkes, kimlik bilgilerinizi görüntüleyip sunucuya bağlanmak için kullanabilir. Kerberos veya NT LAN Manager (NTLM) gibi daha güvenli bir kimlik doğrulama mekanizması kullanmayı göz önünde bulundurmanız gerekir. `defaultCredentials` `true`, sunucu bu protokolleri destekliyorsa Kerberos veya NTLM kullanılacaktır.  
  
 Temel kimlik doğrulaması ve varsayılan ağ kimlik bilgileri seçenekleri birbirini dışlıyor; `defaultCredentials` `true` ve bir Kullanıcı adı ve parola belirtirseniz, varsayılan ağ kimlik bilgileri kullanılır ve temel kimlik doğrulama verileri yok sayılır.  
  
 `userName`belirtirseniz temel kimlik doğrulaması için, posta sunucusu için kimlik doğrulaması yapmak üzere bir `password` de belirtmeniz gerekir.  
  
 <xref:System.Net.Configuration.SmtpNetworkElement.UserName%2A?displayProperty=nameWithType> özelliği, uygun yapılandırma dosyalarından `userName` özniteliğinin geçerli değerini almak için kullanılabilir. <xref:System.Net.Configuration.SmtpNetworkElement.Password%2A?displayProperty=nameWithType> özelliği, uygun yapılandırma dosyalarından `password` özniteliğinin geçerli değerini almak için kullanılabilir. `password` öznitelik, normalde güvenlik nedenleriyle yapılandırma dosyalarına girilmemelidir.  
  
 `clientDomain` özniteliği, ilk SMTP protokol isteğinde kullanılan istemci etki alanı adını bir SMTP sunucusuna değiştirir. `clientDomain` özniteliği, varsayılan olarak kullanılan localhost adı yerine, yerel makinenin tam etki alanı adına ayarlanabilir. Bu, SMTP protokol standartları ile daha fazla uyumluluk sağlar. Varsayılan değer, isteği gönderen yerel bilgisayarın localhost adıdır. <xref:System.Net.Configuration.SmtpNetworkElement.ClientDomain%2A?displayProperty=nameWithType> özelliği, uygun yapılandırma dosyalarından `clientDomain` özniteliğinin geçerli değerini almak için kullanılabilir.  
  
 `targetName` özniteliği, genişletilmiş koruma kullanılırken kimlik doğrulaması için kullanılır. Varsayılan değer "SMTPSVC/\<Host >" biçimindedir, burada \<Host >, SMTP posta sunucusunun ana bilgisayar adıdır. <xref:System.Net.Configuration.SmtpNetworkElement.TargetName%2A?displayProperty=nameWithType> özelliği, uygun yapılandırma dosyalarından `targetName` özniteliğinin geçerli değerini almak için kullanılabilir.  
  
 `enableSsl` özniteliği, SSL 'nin bir SMTP posta sunucusuna erişmek için kullanılıp kullanılmayacağını belirtir. <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType> sınıfı, RFC 3207 ' de tanımlanan Aktarım Katmanı Güvenliği üzerinden güvenli SMTP için SMTP hizmeti uzantısını destekler. Bu modda, SMTP oturumu şifrelenmemiş bir kanalda başlar, sonra SSL kullanarak güvenli iletişime geçmek için istemci tarafından sunucuya bir STARTTLS komutu verilir. Daha fazla bilgi için bkz. Internet Mühendisliği görev gücü (IETF) tarafından yayımlanan RFC 3207.  
  
 Diğer bir bağlantı yöntemi, herhangi bir protokol komutu gönderilmeden önce bir SSL oturumunun kurulduğu yerdir. Bu bağlantı yöntemi bazen SMTPS olarak adlandırılır ve varsayılan olarak 465 numaralı bağlantı noktasını kullanır. SSL kullanan bu alternatif bağlantı yöntemi şu anda desteklenmiyor.  
  
 <xref:System.Net.Configuration.SmtpNetworkElement.EnableSsl%2A?displayProperty=nameWithType> özelliği, uygun yapılandırma dosyalarından `enableSsl` özniteliğinin geçerli değerini almak için kullanılabilir.  
  
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
- [Ağ Ayarları Şeması](index.md)
