---
title: "&lt;Ağ&gt; öğesi (ağ ayarları)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#network
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings/smtp/network
helpviewer_keywords:
- <network> element
- network element
ms.assetid: 2c2c6ad4-ed11-48ab-b28e-2bc0ba9b42c7
caps.latest.revision: "13"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: d3e99a10403a735383ee5e1a78c1f85ac7fd8281
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltnetworkgt-element-network-settings"></a>&lt;Ağ&gt; öğesi (ağ ayarları)
Harici bir Basit Posta Aktarım Protokolü (SMTP) sunucusu için ağ seçenekleri yapılandırır.  
  
 \<Yapılandırma >  
\<System.NET >  
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
|`clientDomain`|İlk SMTP protokolü istekte SMTP posta sunucusuna bağlanmak için kullanılacak istemci etki alanı adını belirtir. Varsayılan değer isteği gönderilirken yerel bilgisayar localhost adıdır.|  
|`defaultCredentials`|Varsayılan kullanıcı kimlik bilgilerini SMTP işlemleri için SMTP posta sunucusuna erişmek için kullanılması gerekip gerekmediğini belirtir. Varsayılan değer `false` şeklindedir.|  
|`enableSsl`|Bir SMTP posta sunucusuna erişmek için SSL kullanılıp kullanılmayacağını belirtir. Varsayılan değer `false` şeklindedir.|  
|`host`|SMTP işlemleri için kullanılacak SMTP posta sunucusu konak adı belirtir. Bu öznitelik varsayılan değeri yok.|  
|`password`|SMTP posta sunucusuna kimlik doğrulaması için kullanılacak parolayı belirtir. Bu öznitelik varsayılan değeri yok.|  
|`port`|SMTP posta sunucusuna bağlanmak için kullanılacak bağlantı noktası numarasını belirtir. Varsayılan değer 25'tir.|  
|`targetName`|SMTP işlemleri için genişletilmiş koruma kullanırken, kimlik doğrulaması için kullanılacak hizmet sağlayıcı adı (SPN) belirtir. Bu öznitelik varsayılan değeri yok.|  
|`userName`|SMTP posta sunucusuna kimlik doğrulaması için kullanılacak kullanıcı adını belirtir. Bu öznitelik varsayılan değeri yok.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<SMTP > öğesi (ağ ayarları)](../../../../../docs/framework/configure-apps/file-schema/network/smtp-element-network-settings.md)|Basit Posta Aktarım Protokolü (SMTP) posta gönderme seçenekleri yapılandırır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bazı SMTP sunucuları kendiniz kullanmadan önce sunucuya kimliğiniz olmasını gerektirir. Kendiniz ana bilgisayarda varsayılan ağ kimlik bilgilerini kullanarak kimlik doğrulaması yapmak istiyorsanız ayarlamak `defaultCredentials` özniteliğini `true`. <xref:System.Net.Configuration.SmtpNetworkElement.DefaultCredentials%2A?displayProperty=nameWithType> Özelliği, geçerli değerini almak için kullanılabilir `defaultCredentials` geçerli yapılandırma dosyalarını özniteliği.  
  
 Temel kimlik doğrulaması (bir kullanıcı adı ve parola) kendiniz SMTP sunucusuna kimlik doğrulaması için de kullanabilirsiniz. Bu seçeneği kullanmak için geçerli bir kullanıcı adı ve belirtilen SMTP sunucusu için parola belirtmeniz gerekir.  
  
> [!NOTE]
>  Temel kimlik doğrulaması gönderir `userName` ve `password` şifrelenmemiş sunucuya değerleri. Herkes ağ trafiğini izleme kimlik bilgilerinizi görüntülemek ve bunları sunucuya bağlanmak için kullanın. Kerberos ya da NT LAN Yöneticisi (NTLM) gibi daha güvenli bir kimlik doğrulama mekanizması kullanmayı düşünmeniz gerekir Varsa `defaultCredentials` olan `true`, Kerberos veya NTLM kullanılacak sunucunun bu protokollerin destekliyorsa.  
  
 Temel kimlik doğrulaması ve varsayılan ağ kimlik bilgileri seçenekleri karşılıklı olarak birbirini dışlar; ayarlarsanız `defaultCredentials` için `true` ve bir kullanıcı adı ve parola belirtin, varsayılan ağ kimlik bilgisi kullanılır ve temel kimlik doğrulama verileri göz ardı edilir.  
  
 Belirtirseniz, temel kimlik doğrulaması için bir `userName`, ayrıca belirtmelisiniz bir `password` kimlik doğrulaması için kendiniz posta sunucusuna.  
  
 <xref:System.Net.Configuration.SmtpNetworkElement.UserName%2A?displayProperty=nameWithType> Özelliği, geçerli değerini almak için kullanılabilir `userName` geçerli yapılandırma dosyalarını özniteliği. <xref:System.Net.Configuration.SmtpNetworkElement.Password%2A?displayProperty=nameWithType> Özelliği, geçerli değerini almak için kullanılabilir `password` geçerli yapılandırma dosyalarını özniteliği. A `password` özniteliği değil normalde girilmesi güvenlik nedenleriyle yapılandırma dosyalarında.  
  
 `clientDomain` Özniteliği ilk SMTP protokolü isteği bir SMTP sunucusu için kullanılan istemci etki alanı adı değiştirir. `clientDomain` Özniteliği, varsayılan olarak kullanılan localhost adı yerine yerel makinenin tam etki alanı adı için ayarlanabilir. Bu, SMTP protokolü standartları ile büyük uyumluluk sağlar. Varsayılan değer isteği gönderilirken yerel bilgisayar localhost adıdır. <xref:System.Net.Configuration.SmtpNetworkElement.ClientDomain%2A?displayProperty=nameWithType> Özelliği, geçerli değerini almak için kullanılabilir `clientDomain` geçerli yapılandırma dosyalarını özniteliği.  
  
 `targetName` Genişletilmiş koruma kullanırken özniteliği kimlik doğrulaması için kullanılır. Varsayılan değer biçimindedir "SMTPSVC /\<ana bilgisayar >" nerede \<ana bilgisayar > SMTP posta sunucusunu barındırıcı adıdır. <xref:System.Net.Configuration.SmtpNetworkElement.TargetName%2A?displayProperty=nameWithType> Özelliği, geçerli değerini almak için kullanılabilir `targetName` geçerli yapılandırma dosyalarını özniteliği.  
  
 `enableSsl` Özniteliği, bir SMTP posta sunucusuna erişmek için SSL kullanılıp kullanılmayacağını belirtir. <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType> Sınıfı yalnızca destekler SMTP hizmeti uzantı güvenli SMTP için Aktarım Katmanı Güvenliği RFC 3207 içinde tanımlanan. Bu modda, şifrelenmemiş bir kanal üzerinde SMTP oturumunu başlar, sonra STARTTLS komut SSL ile güvenli iletişim için geçiş yapmak için sunucuya istemci tarafından verilir. RFC Internet Engineering Task Force (IETF) tarafından daha fazla bilgi için yayımlanan 3207 bakın.  
  
 Bir SSL oturumu komutları gönderilen herhangi bir protokol önce Önden burada kurulmuş bir alternatif bağlantı yöntemidir. Bu bağlantı yöntemi SMTPS adlandırılır ve varsayılan olarak bağlantı noktası 465 kullanır. Bu alternatif bağlantı yöntemi SSL kullanarak şu anda desteklenmiyor.  
  
 <xref:System.Net.Configuration.SmtpNetworkElement.EnableSsl%2A?displayProperty=nameWithType> Özelliği, geçerli değerini almak için kullanılabilir `enableSsl` geçerli yapılandırma dosyalarını özniteliği.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, varsayılan ağ kimlik bilgilerini kullanarak e-posta göndermek için uygun SMTP parametreleri belirtir.  
  
```xml  
<configuration>  
  <system.net>  
    <mailSettings>  
      <smtp deliveryMethod="network">  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Net.Configuration.SmtpNetworkElement?displayProperty=nameWithType>  
 <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>  
 <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>  
 [Ağ Ayarları Şeması](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
