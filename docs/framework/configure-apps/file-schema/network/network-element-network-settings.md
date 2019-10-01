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
ms.openlocfilehash: bac288bb28c4176e52366d0e0b7d8bc7d313cf96
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71698013"
---
# <a name="network-element-network-settings"></a><span data-ttu-id="7863a-102">\<network > öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="7863a-102">\<network> Element (Network Settings)</span></span>
<span data-ttu-id="7863a-103">Harici bir Basit Posta Aktarım Protokolü (SMTP) sunucusu için ağ seçeneklerini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="7863a-103">Configures the network options for an external Simple Mail Transport Protocol (SMTP) server.</span></span>  
  
[<span data-ttu-id="7863a-104"> **\<Yapılandırma >** </span><span class="sxs-lookup"><span data-stu-id="7863a-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="7863a-105">&nbsp; @ no__t-1[ **@no__t -4system. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="7863a-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>  
<span data-ttu-id="7863a-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<mailSettings >** ](mailsettings-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="7863a-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<mailSettings>**](mailsettings-element-network-settings.md)</span></span>  
<span data-ttu-id="7863a-107">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5[ **\<smtp >** ](smtp-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="7863a-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<smtp>**](smtp-element-network-settings.md)</span></span>  
<span data-ttu-id="7863a-108">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 @ no__t-6 @ no__t-7 **\<network >**</span><span class="sxs-lookup"><span data-stu-id="7863a-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<network>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7863a-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7863a-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7863a-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="7863a-110">Attributes and Elements</span></span>  
 <span data-ttu-id="7863a-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="7863a-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7863a-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="7863a-112">Attributes</span></span>  
  
|<span data-ttu-id="7863a-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="7863a-113">Attribute</span></span>|<span data-ttu-id="7863a-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7863a-114">Description</span></span>|  
|---------------|-----------------|  
|`clientDomain`|<span data-ttu-id="7863a-115">SMTP posta sunucusuna bağlanmak için ilk SMTP protokol isteğinde kullanılacak istemci etki alanı adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="7863a-115">Specifies the client domain name to use in the initial SMTP protocol request to connect to the SMTP mail server.</span></span> <span data-ttu-id="7863a-116">Varsayılan değer, isteği gönderen yerel bilgisayarın localhost adıdır.</span><span class="sxs-lookup"><span data-stu-id="7863a-116">The default value is the localhost name of the local computer sending the request.</span></span>|  
|`defaultCredentials`|<span data-ttu-id="7863a-117">SMTP işlemleri için SMTP posta sunucusuna erişmek üzere varsayılan kullanıcı kimlik bilgilerinin kullanılıp kullanılmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="7863a-117">Specifies whether the default user credentials should be used to access the SMTP mail server for SMTP transactions.</span></span> <span data-ttu-id="7863a-118">Varsayılan değer `false` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="7863a-118">The default value is `false`.</span></span>|  
|`enableSsl`|<span data-ttu-id="7863a-119">SMTP posta sunucusuna erişmek için SSL kullanılıp kullanılmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="7863a-119">Specifies whether SSL is used to access an SMTP mail server.</span></span> <span data-ttu-id="7863a-120">Varsayılan değer `false` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="7863a-120">The default value is `false`.</span></span>|  
|`host`|<span data-ttu-id="7863a-121">SMTP işlemleri için kullanılacak SMTP posta sunucusunun ana bilgisayar adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="7863a-121">Specifies the hostname of the SMTP mail server to use for SMTP transactions.</span></span> <span data-ttu-id="7863a-122">Bu özniteliğin varsayılan değeri yok.</span><span class="sxs-lookup"><span data-stu-id="7863a-122">This attribute has no default value.</span></span>|  
|`password`|<span data-ttu-id="7863a-123">SMTP posta sunucusunda kimlik doğrulaması için kullanılacak parolayı belirtir.</span><span class="sxs-lookup"><span data-stu-id="7863a-123">Specifies the password to use for authentication to the SMTP mail server.</span></span> <span data-ttu-id="7863a-124">Bu özniteliğin varsayılan değeri yok.</span><span class="sxs-lookup"><span data-stu-id="7863a-124">This attribute has no default value.</span></span>|  
|`port`|<span data-ttu-id="7863a-125">SMTP posta sunucusuna bağlanmak için kullanılacak bağlantı noktası numarasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="7863a-125">Specifies the port number to use to connect to the SMTP mail server.</span></span> <span data-ttu-id="7863a-126">Varsayılan değer 25 ' tir.</span><span class="sxs-lookup"><span data-stu-id="7863a-126">The default value is 25.</span></span>|  
|`targetName`|<span data-ttu-id="7863a-127">SMTP işlemleri için genişletilmiş koruma kullanılırken kimlik doğrulaması için kullanılacak hizmet sağlayıcı adını (SPN) belirtir.</span><span class="sxs-lookup"><span data-stu-id="7863a-127">Specifies the Service Provider Name (SPN) to use for authentication when using extended protection for SMTP transactions.</span></span> <span data-ttu-id="7863a-128">Bu özniteliğin varsayılan değeri yok.</span><span class="sxs-lookup"><span data-stu-id="7863a-128">This attribute has no default value.</span></span>|  
|`userName`|<span data-ttu-id="7863a-129">SMTP posta sunucusunda kimlik doğrulaması için kullanılacak kullanıcı adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="7863a-129">Specifies the user name to use for authentication to the SMTP mail server.</span></span> <span data-ttu-id="7863a-130">Bu özniteliğin varsayılan değeri yok.</span><span class="sxs-lookup"><span data-stu-id="7863a-130">This attribute has no default value.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7863a-131">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="7863a-131">Child Elements</span></span>  
 <span data-ttu-id="7863a-132">Yok.</span><span class="sxs-lookup"><span data-stu-id="7863a-132">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7863a-133">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="7863a-133">Parent Elements</span></span>  
  
|<span data-ttu-id="7863a-134">Öğe</span><span class="sxs-lookup"><span data-stu-id="7863a-134">Element</span></span>|<span data-ttu-id="7863a-135">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7863a-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7863a-136">\<smtp > öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="7863a-136">\<smtp> Element (Network Settings)</span></span>](smtp-element-network-settings.md)|<span data-ttu-id="7863a-137">Basit Posta Aktarım Protokolü (SMTP) posta gönderme seçeneklerini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="7863a-137">Configures Simple Mail Transport Protocol (SMTP) mail sending options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7863a-138">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7863a-138">Remarks</span></span>  
 <span data-ttu-id="7863a-139">Bazı SMTP sunucuları, kullanmadan önce sunucuda kimlik doğrulamasından geçmesini gerektirir.</span><span class="sxs-lookup"><span data-stu-id="7863a-139">Some SMTP servers require that you authenticate yourself to the server before use.</span></span> <span data-ttu-id="7863a-140">Ana bilgisayarınızdaki varsayılan ağ kimlik bilgilerini kullanarak kendiniz kimlik doğrulaması yapmak istiyorsanız, `defaultCredentials` özniteliğini `true` olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="7863a-140">If you want to authenticate yourself using the default network credentials on your host, set the `defaultCredentials` attribute to `true`.</span></span> <span data-ttu-id="7863a-141">@No__t-0 özelliği uygulanabilir yapılandırma dosyalarından `defaultCredentials` özniteliğinin geçerli değerini almak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="7863a-141">The <xref:System.Net.Configuration.SmtpNetworkElement.DefaultCredentials%2A?displayProperty=nameWithType> property can be used to get the current value of the `defaultCredentials` attribute from applicable configuration files.</span></span>  
  
 <span data-ttu-id="7863a-142">SMTP sunucusunda kimlik doğrulaması yapmak için temel kimlik doğrulaması (bir Kullanıcı adı ve parola) de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7863a-142">You can also use basic authentication (a user name and password) to authenticate yourself to the SMTP server.</span></span> <span data-ttu-id="7863a-143">Bu seçeneği kullanmak için, belirtilen SMTP sunucusu için geçerli bir Kullanıcı adı ve parola belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="7863a-143">To use this option, you must specify a valid user name and password for the specified SMTP server.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7863a-144">Temel kimlik doğrulaması `userName` ve `password` değerlerini sunucuya şifrelenmemiş şekilde gönderir.</span><span class="sxs-lookup"><span data-stu-id="7863a-144">Basic authentication sends the `userName` and `password` values to the server unencrypted.</span></span> <span data-ttu-id="7863a-145">Ağ trafiğini izleyen herkes, kimlik bilgilerinizi görüntüleyip sunucuya bağlanmak için kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="7863a-145">Anyone monitoring network traffic can view your credentials and use them to connect to the server.</span></span> <span data-ttu-id="7863a-146">Kerberos veya NT LAN Manager (NTLM) gibi daha güvenli bir kimlik doğrulama mekanizması kullanmayı göz önünde bulundurmanız gerekir. @No__t-0 `true` ise, sunucu bu protokolleri destekliyorsa Kerberos veya NTLM kullanılacaktır.</span><span class="sxs-lookup"><span data-stu-id="7863a-146">You should consider using a more secure authentication mechanism, such as Kerberos or NT LAN Manager (NTLM.) If `defaultCredentials` is `true`, Kerberos or NTLM will be used if the server supports these protocols.</span></span>  
  
 <span data-ttu-id="7863a-147">Temel kimlik doğrulaması ve varsayılan ağ kimlik bilgileri seçenekleri birbirini dışlıyor; `defaultCredentials` ' ı `true` olarak ayarlarsanız ve bir Kullanıcı adı ve parola belirtirseniz, varsayılan ağ kimlik bilgileri kullanılır ve temel kimlik doğrulama verileri yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="7863a-147">The basic authentication and default network credentials options are mutually exclusive; if you set `defaultCredentials` to `true` and specify a user name and password, the default network credential is used, and the basic authentication data is ignored.</span></span>  
  
 <span data-ttu-id="7863a-148">@No__t-0 belirtirseniz temel kimlik doğrulaması için, posta sunucusu için kimlik doğrulaması yapmak üzere bir `password` de belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="7863a-148">For basic authentication if you specify a `userName`, you should also specify a `password` to authentication yourself to the mail server.</span></span>  
  
 <span data-ttu-id="7863a-149">@No__t-0 özelliği uygulanabilir yapılandırma dosyalarından `userName` özniteliğinin geçerli değerini almak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="7863a-149">The <xref:System.Net.Configuration.SmtpNetworkElement.UserName%2A?displayProperty=nameWithType> property can be used to get the current value of the `userName` attribute from applicable configuration files.</span></span> <span data-ttu-id="7863a-150">@No__t-0 özelliği uygulanabilir yapılandırma dosyalarından `password` özniteliğinin geçerli değerini almak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="7863a-150">The <xref:System.Net.Configuration.SmtpNetworkElement.Password%2A?displayProperty=nameWithType> property can be used to get the current value of the `password` attribute from applicable configuration files.</span></span> <span data-ttu-id="7863a-151">@No__t-0 özniteliği normalde güvenlik nedenleriyle yapılandırma dosyalarına girilmemelidir.</span><span class="sxs-lookup"><span data-stu-id="7863a-151">A `password` attribute would not normally be entered in configuration files for security reasons.</span></span>  
  
 <span data-ttu-id="7863a-152">@No__t-0 özniteliği, ilk SMTP protokol isteğinde kullanılan istemci etki alanı adını bir SMTP sunucusuna değiştirir.</span><span class="sxs-lookup"><span data-stu-id="7863a-152">The `clientDomain` attribute changes the client domain name used in the initial SMTP protocol request to an SMTP server.</span></span> <span data-ttu-id="7863a-153">@No__t-0 özniteliği, varsayılan olarak kullanılan localhost adı yerine, yerel makinenin tam etki alanı adına ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="7863a-153">The `clientDomain` attribute can be set to the fully-qualified domain name of the local machine, rather than the localhost name that is used by default.</span></span> <span data-ttu-id="7863a-154">Bu, SMTP protokol standartları ile daha fazla uyumluluk sağlar.</span><span class="sxs-lookup"><span data-stu-id="7863a-154">This provides greater compliance with the SMTP protocol standards.</span></span> <span data-ttu-id="7863a-155">Varsayılan değer, isteği gönderen yerel bilgisayarın localhost adıdır.</span><span class="sxs-lookup"><span data-stu-id="7863a-155">The default value is the localhost name of the local computer sending the request.</span></span> <span data-ttu-id="7863a-156">@No__t-0 özelliği uygulanabilir yapılandırma dosyalarından `clientDomain` özniteliğinin geçerli değerini almak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="7863a-156">The <xref:System.Net.Configuration.SmtpNetworkElement.ClientDomain%2A?displayProperty=nameWithType> property can be used to get the current value of the `clientDomain` attribute from applicable configuration files.</span></span>  
  
 <span data-ttu-id="7863a-157">@No__t-0 özniteliği, genişletilmiş koruma kullanılırken kimlik doğrulaması için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7863a-157">The `targetName` attribute is used for authentication when using extended protection.</span></span> <span data-ttu-id="7863a-158">Varsayılan değer "SMTPSVC/\<host >" biçimindedir, burada \<host >, SMTP posta sunucusunun ana bilgisayar adıdır.</span><span class="sxs-lookup"><span data-stu-id="7863a-158">The default value is of the form "SMTPSVC/\<host>" where \<host> is the hostname of the SMTP mail server.</span></span> <span data-ttu-id="7863a-159">@No__t-0 özelliği uygulanabilir yapılandırma dosyalarından `targetName` özniteliğinin geçerli değerini almak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="7863a-159">The <xref:System.Net.Configuration.SmtpNetworkElement.TargetName%2A?displayProperty=nameWithType> property can be used to get the current value of the `targetName` attribute from applicable configuration files.</span></span>  
  
 <span data-ttu-id="7863a-160">@No__t-0 özniteliği, SSL 'nin bir SMTP posta sunucusuna erişmek için kullanılıp kullanılmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="7863a-160">The `enableSsl` attribute specifies whether SSL is used to access an SMTP mail server.</span></span> <span data-ttu-id="7863a-161">@No__t-0 sınıfı, RFC 3207 ' de tanımlanan Aktarım Katmanı Güvenliği üzerinden güvenli SMTP için SMTP hizmeti uzantısını destekler.</span><span class="sxs-lookup"><span data-stu-id="7863a-161">The <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType> class only supports the SMTP Service Extension for Secure SMTP over Transport Layer Security as defined in RFC 3207.</span></span> <span data-ttu-id="7863a-162">Bu modda, SMTP oturumu şifrelenmemiş bir kanalda başlar, sonra SSL kullanarak güvenli iletişime geçmek için istemci tarafından sunucuya bir STARTTLS komutu verilir.</span><span class="sxs-lookup"><span data-stu-id="7863a-162">In this mode, the SMTP session begins on an unencrypted channel, then a STARTTLS command is issued by the client to the server to switch to secure communication using SSL.</span></span> <span data-ttu-id="7863a-163">Daha fazla bilgi için bkz. Internet Mühendisliği görev gücü (IETF) tarafından yayımlanan RFC 3207.</span><span class="sxs-lookup"><span data-stu-id="7863a-163">See RFC 3207 published by the Internet Engineering Task Force (IETF) for more information.</span></span>  
  
 <span data-ttu-id="7863a-164">Diğer bir bağlantı yöntemi, herhangi bir protokol komutu gönderilmeden önce bir SSL oturumunun kurulduğu yerdir.</span><span class="sxs-lookup"><span data-stu-id="7863a-164">An alternate connection method is where an SSL session is established up front before any protocol commands are sent.</span></span> <span data-ttu-id="7863a-165">Bu bağlantı yöntemi bazen SMTPS olarak adlandırılır ve varsayılan olarak 465 numaralı bağlantı noktasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="7863a-165">This connection method is sometimes called SMTPS and by default uses port 465.</span></span> <span data-ttu-id="7863a-166">SSL kullanan bu alternatif bağlantı yöntemi şu anda desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="7863a-166">This alternate connection method using SSL is not currently supported.</span></span>  
  
 <span data-ttu-id="7863a-167">@No__t-0 özelliği uygulanabilir yapılandırma dosyalarından `enableSsl` özniteliğinin geçerli değerini almak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="7863a-167">The <xref:System.Net.Configuration.SmtpNetworkElement.EnableSsl%2A?displayProperty=nameWithType> property can be used to get the current value of the `enableSsl` attribute from applicable configuration files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7863a-168">Örnek</span><span class="sxs-lookup"><span data-stu-id="7863a-168">Example</span></span>  
 <span data-ttu-id="7863a-169">Aşağıdaki örnek, varsayılan ağ kimlik bilgilerini kullanarak e-posta göndermek için uygun SMTP parametrelerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="7863a-169">The following example specifies the appropriate SMTP parameters to send email using the default network credentials.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7863a-170">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7863a-170">See also</span></span>

- <xref:System.Net.Configuration.SmtpNetworkElement?displayProperty=nameWithType>
- <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>
- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- [<span data-ttu-id="7863a-171">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="7863a-171">Network Settings Schema</span></span>](index.md)
