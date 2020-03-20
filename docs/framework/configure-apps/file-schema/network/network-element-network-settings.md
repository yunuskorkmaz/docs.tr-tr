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
# <a name="network-element-network-settings"></a><span data-ttu-id="a4d1e-102">\<ağ> Öğesi (Ağ Ayarları)</span><span class="sxs-lookup"><span data-stu-id="a4d1e-102">\<network> Element (Network Settings)</span></span>
<span data-ttu-id="a4d1e-103">Harici bir Basit Posta Aktarım Protokolü (SMTP) sunucusu için ağ seçeneklerini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="a4d1e-103">Configures the network options for an external Simple Mail Transport Protocol (SMTP) server.</span></span>  

<span data-ttu-id="a4d1e-104">[**\<yapılandırma>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="a4d1e-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="a4d1e-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="a4d1e-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="a4d1e-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<mailAyarlar>**](mailsettings-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="a4d1e-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<mailSettings>**](mailsettings-element-network-settings.md)</span></span>\
<span data-ttu-id="a4d1e-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<smtp>**](smtp-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="a4d1e-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<smtp>**](smtp-element-network-settings.md)</span></span>\
<span data-ttu-id="a4d1e-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<ağ>**</span><span class="sxs-lookup"><span data-stu-id="a4d1e-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<network>**</span></span>

## <a name="syntax"></a><span data-ttu-id="a4d1e-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a4d1e-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a4d1e-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="a4d1e-110">Attributes and Elements</span></span>  
 <span data-ttu-id="a4d1e-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a4d1e-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a4d1e-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a4d1e-112">Attributes</span></span>  
  
|<span data-ttu-id="a4d1e-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="a4d1e-113">Attribute</span></span>|<span data-ttu-id="a4d1e-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a4d1e-114">Description</span></span>|  
|---------------|-----------------|  
|`clientDomain`|<span data-ttu-id="a4d1e-115">SMTP posta sunucusuna bağlanmak için ilk SMTP protokolü isteğinde kullanılacak istemci etki alanı adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="a4d1e-115">Specifies the client domain name to use in the initial SMTP protocol request to connect to the SMTP mail server.</span></span> <span data-ttu-id="a4d1e-116">Varsayılan değer, isteği gönderen yerel bilgisayarın yerel ana bilgisayar adıdır.</span><span class="sxs-lookup"><span data-stu-id="a4d1e-116">The default value is the localhost name of the local computer sending the request.</span></span>|  
|`defaultCredentials`|<span data-ttu-id="a4d1e-117">Varsayılan kullanıcı kimlik bilgilerinin SMTP işlemleri için SMTP posta sunucusuna erişmek için kullanılıp kullanılmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="a4d1e-117">Specifies whether the default user credentials should be used to access the SMTP mail server for SMTP transactions.</span></span> <span data-ttu-id="a4d1e-118">Varsayılan değer: `false`.</span><span class="sxs-lookup"><span data-stu-id="a4d1e-118">The default value is `false`.</span></span>|  
|`enableSsl`|<span data-ttu-id="a4d1e-119">SSL'nin bir SMTP posta sunucusuna erişmek için kullanılıp kullanılmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="a4d1e-119">Specifies whether SSL is used to access an SMTP mail server.</span></span> <span data-ttu-id="a4d1e-120">Varsayılan değer: `false`.</span><span class="sxs-lookup"><span data-stu-id="a4d1e-120">The default value is `false`.</span></span>|  
|`host`|<span data-ttu-id="a4d1e-121">SMTP işlemleri için kullanılacak SMTP posta sunucusunun ana bilgisayar adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="a4d1e-121">Specifies the hostname of the SMTP mail server to use for SMTP transactions.</span></span> <span data-ttu-id="a4d1e-122">Bu öznitelik varsayılan değeri vardır.</span><span class="sxs-lookup"><span data-stu-id="a4d1e-122">This attribute has no default value.</span></span>|  
|`password`|<span data-ttu-id="a4d1e-123">Kimlik doğrulaması için Kullanılacak parolayı SMTP posta sunucusuna belirtir.</span><span class="sxs-lookup"><span data-stu-id="a4d1e-123">Specifies the password to use for authentication to the SMTP mail server.</span></span> <span data-ttu-id="a4d1e-124">Bu öznitelik varsayılan değeri vardır.</span><span class="sxs-lookup"><span data-stu-id="a4d1e-124">This attribute has no default value.</span></span>|  
|`port`|<span data-ttu-id="a4d1e-125">SMTP posta sunucusuna bağlanmak için kullanılacak bağlantı noktası numarasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="a4d1e-125">Specifies the port number to use to connect to the SMTP mail server.</span></span> <span data-ttu-id="a4d1e-126">Varsayılan değer 25'tir.</span><span class="sxs-lookup"><span data-stu-id="a4d1e-126">The default value is 25.</span></span>|  
|`targetName`|<span data-ttu-id="a4d1e-127">SMTP işlemleri için genişletilmiş koruma kullanırken kimlik doğrulaması için kullanılacak Servis Sağlayıcı Adını (SPN) belirtir.</span><span class="sxs-lookup"><span data-stu-id="a4d1e-127">Specifies the Service Provider Name (SPN) to use for authentication when using extended protection for SMTP transactions.</span></span> <span data-ttu-id="a4d1e-128">Bu öznitelik varsayılan değeri vardır.</span><span class="sxs-lookup"><span data-stu-id="a4d1e-128">This attribute has no default value.</span></span>|  
|`userName`|<span data-ttu-id="a4d1e-129">SMTP posta sunucusunda kimlik doğrulaması için kullanılacak kullanıcı adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="a4d1e-129">Specifies the user name to use for authentication to the SMTP mail server.</span></span> <span data-ttu-id="a4d1e-130">Bu öznitelik varsayılan değeri vardır.</span><span class="sxs-lookup"><span data-stu-id="a4d1e-130">This attribute has no default value.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a4d1e-131">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="a4d1e-131">Child Elements</span></span>  
 <span data-ttu-id="a4d1e-132">Yok.</span><span class="sxs-lookup"><span data-stu-id="a4d1e-132">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a4d1e-133">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="a4d1e-133">Parent Elements</span></span>  
  
|<span data-ttu-id="a4d1e-134">Öğe</span><span class="sxs-lookup"><span data-stu-id="a4d1e-134">Element</span></span>|<span data-ttu-id="a4d1e-135">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a4d1e-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a4d1e-136">\<smtp> Elemanı (Ağ Ayarları)</span><span class="sxs-lookup"><span data-stu-id="a4d1e-136">\<smtp> Element (Network Settings)</span></span>](smtp-element-network-settings.md)|<span data-ttu-id="a4d1e-137">Basit Posta Aktarım Protokolü (SMTP) posta gönderme seçeneklerini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="a4d1e-137">Configures Simple Mail Transport Protocol (SMTP) mail sending options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a4d1e-138">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a4d1e-138">Remarks</span></span>  
 <span data-ttu-id="a4d1e-139">Bazı SMTP sunucuları, kullanmadan önce kendinizi sunucuya doğrulamanızı gerektirir.</span><span class="sxs-lookup"><span data-stu-id="a4d1e-139">Some SMTP servers require that you authenticate yourself to the server before use.</span></span> <span data-ttu-id="a4d1e-140">Ana bilgisayarınızdaki varsayılan ağ kimlik bilgilerini kullanarak kimliğinizi `defaultCredentials` doğrulamak istiyorsanız, özniteliği `true`' ne göre ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="a4d1e-140">If you want to authenticate yourself using the default network credentials on your host, set the `defaultCredentials` attribute to `true`.</span></span> <span data-ttu-id="a4d1e-141">Özellik, <xref:System.Net.Configuration.SmtpNetworkElement.DefaultCredentials%2A?displayProperty=nameWithType> özniteliğin `defaultCredentials` geçerli değerini geçerli yapılandırma dosyalarından almak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a4d1e-141">The <xref:System.Net.Configuration.SmtpNetworkElement.DefaultCredentials%2A?displayProperty=nameWithType> property can be used to get the current value of the `defaultCredentials` attribute from applicable configuration files.</span></span>  
  
 <span data-ttu-id="a4d1e-142">SMTP sunucusuna kimlik doğrulamak için temel kimlik doğrulamayı (kullanıcı adı ve parola) da kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a4d1e-142">You can also use basic authentication (a user name and password) to authenticate yourself to the SMTP server.</span></span> <span data-ttu-id="a4d1e-143">Bu seçeneği kullanmak için, belirtilen SMTP sunucusu için geçerli bir kullanıcı adı ve parola belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="a4d1e-143">To use this option, you must specify a valid user name and password for the specified SMTP server.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a4d1e-144">Temel kimlik doğrulaması `password` ve değerleri şifrelenmemiş sunucuya gönderir. `userName`</span><span class="sxs-lookup"><span data-stu-id="a4d1e-144">Basic authentication sends the `userName` and `password` values to the server unencrypted.</span></span> <span data-ttu-id="a4d1e-145">Ağ trafiğini izleyen herkes kimlik bilgilerinizi görüntüleyebilir ve bunları sunucuya bağlanmak için kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="a4d1e-145">Anyone monitoring network traffic can view your credentials and use them to connect to the server.</span></span> <span data-ttu-id="a4d1e-146">Kerberos veya NT LAN Yöneticisi (NTLM) gibi daha güvenli bir kimlik doğrulama mekanizması kullanmayı düşünmelisiniz. `defaultCredentials` Eğer, `true`sunucu bu protokolleri destekliyorsa, Kerberos veya NTLM kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a4d1e-146">You should consider using a more secure authentication mechanism, such as Kerberos or NT LAN Manager (NTLM.) If `defaultCredentials` is `true`, Kerberos or NTLM will be used if the server supports these protocols.</span></span>  
  
 <span data-ttu-id="a4d1e-147">Temel kimlik doğrulama ve varsayılan ağ kimlik bilgileri seçenekleri birbirini dışlar; Bir kullanıcı `defaultCredentials` `true` adı ve parola yı ayarlar ve belirtirseniz, varsayılan ağ kimlik bilgisi kullanılır ve temel kimlik doğrulama verileri yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="a4d1e-147">The basic authentication and default network credentials options are mutually exclusive; if you set `defaultCredentials` to `true` and specify a user name and password, the default network credential is used, and the basic authentication data is ignored.</span></span>  
  
 <span data-ttu-id="a4d1e-148">Temel kimlik doğrulaması için, bir `userName`de `password` posta sunucusuna bir kimlik doğrulaması belirtmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="a4d1e-148">For basic authentication if you specify a `userName`, you should also specify a `password` to authentication yourself to the mail server.</span></span>  
  
 <span data-ttu-id="a4d1e-149">Özellik, <xref:System.Net.Configuration.SmtpNetworkElement.UserName%2A?displayProperty=nameWithType> özniteliğin `userName` geçerli değerini geçerli yapılandırma dosyalarından almak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a4d1e-149">The <xref:System.Net.Configuration.SmtpNetworkElement.UserName%2A?displayProperty=nameWithType> property can be used to get the current value of the `userName` attribute from applicable configuration files.</span></span> <span data-ttu-id="a4d1e-150">Özellik, <xref:System.Net.Configuration.SmtpNetworkElement.Password%2A?displayProperty=nameWithType> özniteliğin `password` geçerli değerini geçerli yapılandırma dosyalarından almak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a4d1e-150">The <xref:System.Net.Configuration.SmtpNetworkElement.Password%2A?displayProperty=nameWithType> property can be used to get the current value of the `password` attribute from applicable configuration files.</span></span> <span data-ttu-id="a4d1e-151">Bir `password` öznitelik normalde güvenlik nedenleriyle yapılandırma dosyalarına girilmez.</span><span class="sxs-lookup"><span data-stu-id="a4d1e-151">A `password` attribute would not normally be entered in configuration files for security reasons.</span></span>  
  
 <span data-ttu-id="a4d1e-152">Öznitelik, `clientDomain` ilk SMTP iletişim kuralı isteğinde kullanılan istemci etki alanı adını bir SMTP sunucusuna değiştirir.</span><span class="sxs-lookup"><span data-stu-id="a4d1e-152">The `clientDomain` attribute changes the client domain name used in the initial SMTP protocol request to an SMTP server.</span></span> <span data-ttu-id="a4d1e-153">Öznitelik, `clientDomain` varsayılan olarak kullanılan yerel ana bilgisayar adı yerine yerel makinenin tam nitelikli etki alanı adına ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="a4d1e-153">The `clientDomain` attribute can be set to the fully-qualified domain name of the local machine, rather than the localhost name that is used by default.</span></span> <span data-ttu-id="a4d1e-154">Bu, SMTP protokol standartlarına daha fazla uyumluluk sağlar.</span><span class="sxs-lookup"><span data-stu-id="a4d1e-154">This provides greater compliance with the SMTP protocol standards.</span></span> <span data-ttu-id="a4d1e-155">Varsayılan değer, isteği gönderen yerel bilgisayarın yerel ana bilgisayar adıdır.</span><span class="sxs-lookup"><span data-stu-id="a4d1e-155">The default value is the localhost name of the local computer sending the request.</span></span> <span data-ttu-id="a4d1e-156">Özellik, <xref:System.Net.Configuration.SmtpNetworkElement.ClientDomain%2A?displayProperty=nameWithType> özniteliğin `clientDomain` geçerli değerini geçerli yapılandırma dosyalarından almak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a4d1e-156">The <xref:System.Net.Configuration.SmtpNetworkElement.ClientDomain%2A?displayProperty=nameWithType> property can be used to get the current value of the `clientDomain` attribute from applicable configuration files.</span></span>  
  
 <span data-ttu-id="a4d1e-157">Öznitelik, `targetName` genişletilmiş koruma kullanılırken kimlik doğrulama için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a4d1e-157">The `targetName` attribute is used for authentication when using extended protection.</span></span> <span data-ttu-id="a4d1e-158">Varsayılan değer,\< \<ana bilgisayar> SMTP posta sunucusunun ana bilgisayarı olduğu "SMTPSVC/ ana bilgisayar>" biçimindedir.</span><span class="sxs-lookup"><span data-stu-id="a4d1e-158">The default value is of the form "SMTPSVC/\<host>" where \<host> is the hostname of the SMTP mail server.</span></span> <span data-ttu-id="a4d1e-159">Özellik, <xref:System.Net.Configuration.SmtpNetworkElement.TargetName%2A?displayProperty=nameWithType> özniteliğin `targetName` geçerli değerini geçerli yapılandırma dosyalarından almak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a4d1e-159">The <xref:System.Net.Configuration.SmtpNetworkElement.TargetName%2A?displayProperty=nameWithType> property can be used to get the current value of the `targetName` attribute from applicable configuration files.</span></span>  
  
 <span data-ttu-id="a4d1e-160">Öznitelik, SSL'nin `enableSsl` bir SMTP posta sunucusuna erişmek için kullanılıp kullanılmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="a4d1e-160">The `enableSsl` attribute specifies whether SSL is used to access an SMTP mail server.</span></span> <span data-ttu-id="a4d1e-161">Sınıf <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType> yalnızca RFC 3207'de tanımlandığı gibi Taşıma Katmanı Güvenliği üzerinden Güvenli SMTP için SMTP Hizmet Uzantısını destekler.</span><span class="sxs-lookup"><span data-stu-id="a4d1e-161">The <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType> class only supports the SMTP Service Extension for Secure SMTP over Transport Layer Security as defined in RFC 3207.</span></span> <span data-ttu-id="a4d1e-162">Bu modda, SMTP oturumu şifresiz bir kanalda başlar, ardından istemci tarafından sunucuya bir STARTTLS komutu verilir ve SSL kullanarak güvenli iletişime geçer.</span><span class="sxs-lookup"><span data-stu-id="a4d1e-162">In this mode, the SMTP session begins on an unencrypted channel, then a STARTTLS command is issued by the client to the server to switch to secure communication using SSL.</span></span> <span data-ttu-id="a4d1e-163">Daha fazla bilgi için Internet Engineering Task Force (IETF) tarafından yayınlanan RFC 3207'ye bakın.</span><span class="sxs-lookup"><span data-stu-id="a4d1e-163">See RFC 3207 published by the Internet Engineering Task Force (IETF) for more information.</span></span>  
  
 <span data-ttu-id="a4d1e-164">Alternatif bağlantı yöntemi, herhangi bir protokol komutu gönderilmeden önce bir SSL oturumunun önceden oluşturulduğü yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="a4d1e-164">An alternate connection method is where an SSL session is established up front before any protocol commands are sent.</span></span> <span data-ttu-id="a4d1e-165">Bu bağlantı yöntemi bazen SMTPS olarak adlandırılır ve varsayılan olarak 465 bağlantı noktasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="a4d1e-165">This connection method is sometimes called SMTPS and by default uses port 465.</span></span> <span data-ttu-id="a4d1e-166">SSL kullanan bu alternatif bağlantı yöntemi şu anda desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="a4d1e-166">This alternate connection method using SSL is not currently supported.</span></span>  
  
 <span data-ttu-id="a4d1e-167">Özellik, <xref:System.Net.Configuration.SmtpNetworkElement.EnableSsl%2A?displayProperty=nameWithType> özniteliğin `enableSsl` geçerli değerini geçerli yapılandırma dosyalarından almak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a4d1e-167">The <xref:System.Net.Configuration.SmtpNetworkElement.EnableSsl%2A?displayProperty=nameWithType> property can be used to get the current value of the `enableSsl` attribute from applicable configuration files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a4d1e-168">Örnek</span><span class="sxs-lookup"><span data-stu-id="a4d1e-168">Example</span></span>  
 <span data-ttu-id="a4d1e-169">Aşağıdaki örnekte, varsayılan ağ kimlik bilgilerini kullanarak e-posta göndermek için uygun SMTP parametreleri belirtilmez.</span><span class="sxs-lookup"><span data-stu-id="a4d1e-169">The following example specifies the appropriate SMTP parameters to send email using the default network credentials.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a4d1e-170">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a4d1e-170">See also</span></span>

- <xref:System.Net.Configuration.SmtpNetworkElement?displayProperty=nameWithType>
- <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>
- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- [<span data-ttu-id="a4d1e-171">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="a4d1e-171">Network Settings Schema</span></span>](index.md)
