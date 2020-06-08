---
title: <network> Öğesi (Ağ Ayarları)
description: <network>Ağ ayarları öğesi, .NET Framework dış SMTP sunucusu seçeneklerinin ağ seçeneklerini yapılandırır.
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#network
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings/smtp/network
helpviewer_keywords:
- <network> element
- network element
ms.assetid: 2c2c6ad4-ed11-48ab-b28e-2bc0ba9b42c7
ms.openlocfilehash: 36857e63871b4672df349934594f0887a042609e
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504556"
---
# <a name="network-element-network-settings"></a><span data-ttu-id="4aaea-103">\<network> Öğesi (Ağ Ayarları)</span><span class="sxs-lookup"><span data-stu-id="4aaea-103">\<network> Element (Network Settings)</span></span>
<span data-ttu-id="4aaea-104">Harici bir Basit Posta Aktarım Protokolü (SMTP) sunucusu için ağ seçeneklerini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="4aaea-104">Configures the network options for an external Simple Mail Transport Protocol (SMTP) server.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<mailSettings>**](mailsettings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<smtp>**](smtp-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<network>**

## <a name="syntax"></a><span data-ttu-id="4aaea-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4aaea-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4aaea-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="4aaea-106">Attributes and Elements</span></span>  
 <span data-ttu-id="4aaea-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4aaea-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4aaea-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="4aaea-108">Attributes</span></span>  
  
|<span data-ttu-id="4aaea-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="4aaea-109">Attribute</span></span>|<span data-ttu-id="4aaea-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4aaea-110">Description</span></span>|  
|---------------|-----------------|  
|`clientDomain`|<span data-ttu-id="4aaea-111">SMTP posta sunucusuna bağlanmak için ilk SMTP protokol isteğinde kullanılacak istemci etki alanı adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="4aaea-111">Specifies the client domain name to use in the initial SMTP protocol request to connect to the SMTP mail server.</span></span> <span data-ttu-id="4aaea-112">Varsayılan değer, isteği gönderen yerel bilgisayarın localhost adıdır.</span><span class="sxs-lookup"><span data-stu-id="4aaea-112">The default value is the localhost name of the local computer sending the request.</span></span>|  
|`defaultCredentials`|<span data-ttu-id="4aaea-113">SMTP işlemleri için SMTP posta sunucusuna erişmek üzere varsayılan kullanıcı kimlik bilgilerinin kullanılıp kullanılmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="4aaea-113">Specifies whether the default user credentials should be used to access the SMTP mail server for SMTP transactions.</span></span> <span data-ttu-id="4aaea-114">Varsayılan değer: `false`.</span><span class="sxs-lookup"><span data-stu-id="4aaea-114">The default value is `false`.</span></span>|  
|`enableSsl`|<span data-ttu-id="4aaea-115">SMTP posta sunucusuna erişmek için SSL kullanılıp kullanılmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="4aaea-115">Specifies whether SSL is used to access an SMTP mail server.</span></span> <span data-ttu-id="4aaea-116">Varsayılan değer: `false`.</span><span class="sxs-lookup"><span data-stu-id="4aaea-116">The default value is `false`.</span></span>|  
|`host`|<span data-ttu-id="4aaea-117">SMTP işlemleri için kullanılacak SMTP posta sunucusunun ana bilgisayar adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="4aaea-117">Specifies the hostname of the SMTP mail server to use for SMTP transactions.</span></span> <span data-ttu-id="4aaea-118">Bu özniteliğin varsayılan değeri yok.</span><span class="sxs-lookup"><span data-stu-id="4aaea-118">This attribute has no default value.</span></span>|  
|`password`|<span data-ttu-id="4aaea-119">SMTP posta sunucusunda kimlik doğrulaması için kullanılacak parolayı belirtir.</span><span class="sxs-lookup"><span data-stu-id="4aaea-119">Specifies the password to use for authentication to the SMTP mail server.</span></span> <span data-ttu-id="4aaea-120">Bu özniteliğin varsayılan değeri yok.</span><span class="sxs-lookup"><span data-stu-id="4aaea-120">This attribute has no default value.</span></span>|  
|`port`|<span data-ttu-id="4aaea-121">SMTP posta sunucusuna bağlanmak için kullanılacak bağlantı noktası numarasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="4aaea-121">Specifies the port number to use to connect to the SMTP mail server.</span></span> <span data-ttu-id="4aaea-122">Varsayılan değer 25 ' tir.</span><span class="sxs-lookup"><span data-stu-id="4aaea-122">The default value is 25.</span></span>|  
|`targetName`|<span data-ttu-id="4aaea-123">SMTP işlemleri için genişletilmiş koruma kullanılırken kimlik doğrulaması için kullanılacak hizmet sağlayıcı adını (SPN) belirtir.</span><span class="sxs-lookup"><span data-stu-id="4aaea-123">Specifies the Service Provider Name (SPN) to use for authentication when using extended protection for SMTP transactions.</span></span> <span data-ttu-id="4aaea-124">Bu özniteliğin varsayılan değeri yok.</span><span class="sxs-lookup"><span data-stu-id="4aaea-124">This attribute has no default value.</span></span>|  
|`userName`|<span data-ttu-id="4aaea-125">SMTP posta sunucusunda kimlik doğrulaması için kullanılacak kullanıcı adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="4aaea-125">Specifies the user name to use for authentication to the SMTP mail server.</span></span> <span data-ttu-id="4aaea-126">Bu özniteliğin varsayılan değeri yok.</span><span class="sxs-lookup"><span data-stu-id="4aaea-126">This attribute has no default value.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4aaea-127">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="4aaea-127">Child Elements</span></span>  
 <span data-ttu-id="4aaea-128">Yok.</span><span class="sxs-lookup"><span data-stu-id="4aaea-128">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4aaea-129">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="4aaea-129">Parent Elements</span></span>  
  
|<span data-ttu-id="4aaea-130">Öğe</span><span class="sxs-lookup"><span data-stu-id="4aaea-130">Element</span></span>|<span data-ttu-id="4aaea-131">Description</span><span class="sxs-lookup"><span data-stu-id="4aaea-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4aaea-132">\<smtp>Öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="4aaea-132">\<smtp> Element (Network Settings)</span></span>](smtp-element-network-settings.md)|<span data-ttu-id="4aaea-133">Basit Posta Aktarım Protokolü (SMTP) posta gönderme seçeneklerini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="4aaea-133">Configures Simple Mail Transport Protocol (SMTP) mail sending options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4aaea-134">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4aaea-134">Remarks</span></span>  
 <span data-ttu-id="4aaea-135">Bazı SMTP sunucuları, kullanmadan önce sunucuda kimlik doğrulamasından geçmesini gerektirir.</span><span class="sxs-lookup"><span data-stu-id="4aaea-135">Some SMTP servers require that you authenticate yourself to the server before use.</span></span> <span data-ttu-id="4aaea-136">Ana bilgisayarınızdaki varsayılan ağ kimlik bilgilerini kullanarak kendiniz kimlik doğrulaması yapmak istiyorsanız, `defaultCredentials` özniteliğini olarak ayarlayın `true` .</span><span class="sxs-lookup"><span data-stu-id="4aaea-136">If you want to authenticate yourself using the default network credentials on your host, set the `defaultCredentials` attribute to `true`.</span></span> <span data-ttu-id="4aaea-137"><xref:System.Net.Configuration.SmtpNetworkElement.DefaultCredentials%2A?displayProperty=nameWithType>Özelliği, geçerli yapılandırma dosyalarından özniteliğin geçerli değerini almak için kullanılabilir `defaultCredentials` .</span><span class="sxs-lookup"><span data-stu-id="4aaea-137">The <xref:System.Net.Configuration.SmtpNetworkElement.DefaultCredentials%2A?displayProperty=nameWithType> property can be used to get the current value of the `defaultCredentials` attribute from applicable configuration files.</span></span>  
  
 <span data-ttu-id="4aaea-138">SMTP sunucusunda kimlik doğrulaması yapmak için temel kimlik doğrulaması (bir Kullanıcı adı ve parola) de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4aaea-138">You can also use basic authentication (a user name and password) to authenticate yourself to the SMTP server.</span></span> <span data-ttu-id="4aaea-139">Bu seçeneği kullanmak için, belirtilen SMTP sunucusu için geçerli bir Kullanıcı adı ve parola belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="4aaea-139">To use this option, you must specify a valid user name and password for the specified SMTP server.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4aaea-140">Temel kimlik doğrulaması, `userName` ve `password` değerlerini sunucuya şifrelenmemiş şekilde gönderir.</span><span class="sxs-lookup"><span data-stu-id="4aaea-140">Basic authentication sends the `userName` and `password` values to the server unencrypted.</span></span> <span data-ttu-id="4aaea-141">Ağ trafiğini izleyen herkes, kimlik bilgilerinizi görüntüleyip sunucuya bağlanmak için kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="4aaea-141">Anyone monitoring network traffic can view your credentials and use them to connect to the server.</span></span> <span data-ttu-id="4aaea-142">Kerberos veya NT LAN Manager (NTLM) gibi daha güvenli bir kimlik doğrulama mekanizması kullanmayı göz önünde bulundurmanız gerekir. `defaultCredentials`İse `true` , sunucu bu protokolleri destekliyorsa Kerberos veya NTLM kullanılacaktır.</span><span class="sxs-lookup"><span data-stu-id="4aaea-142">You should consider using a more secure authentication mechanism, such as Kerberos or NT LAN Manager (NTLM.) If `defaultCredentials` is `true`, Kerberos or NTLM will be used if the server supports these protocols.</span></span>  
  
 <span data-ttu-id="4aaea-143">Temel kimlik doğrulaması ve varsayılan ağ kimlik bilgileri seçenekleri birbirini dışlıyor; `defaultCredentials`olarak ayarlarsanız `true` ve bir Kullanıcı adı ve parola belirtirseniz, varsayılan ağ kimlik bilgileri kullanılır ve temel kimlik doğrulama verileri yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="4aaea-143">The basic authentication and default network credentials options are mutually exclusive; if you set `defaultCredentials` to `true` and specify a user name and password, the default network credential is used, and the basic authentication data is ignored.</span></span>  
  
 <span data-ttu-id="4aaea-144">Bir belirtirseniz temel kimlik doğrulaması için `userName` , `password` posta sunucusuna kendiniz kimlik doğrulaması yapmak için bir de belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="4aaea-144">For basic authentication if you specify a `userName`, you should also specify a `password` to authentication yourself to the mail server.</span></span>  
  
 <span data-ttu-id="4aaea-145"><xref:System.Net.Configuration.SmtpNetworkElement.UserName%2A?displayProperty=nameWithType>Özelliği, geçerli yapılandırma dosyalarından özniteliğin geçerli değerini almak için kullanılabilir `userName` .</span><span class="sxs-lookup"><span data-stu-id="4aaea-145">The <xref:System.Net.Configuration.SmtpNetworkElement.UserName%2A?displayProperty=nameWithType> property can be used to get the current value of the `userName` attribute from applicable configuration files.</span></span> <span data-ttu-id="4aaea-146"><xref:System.Net.Configuration.SmtpNetworkElement.Password%2A?displayProperty=nameWithType>Özelliği, geçerli yapılandırma dosyalarından özniteliğin geçerli değerini almak için kullanılabilir `password` .</span><span class="sxs-lookup"><span data-stu-id="4aaea-146">The <xref:System.Net.Configuration.SmtpNetworkElement.Password%2A?displayProperty=nameWithType> property can be used to get the current value of the `password` attribute from applicable configuration files.</span></span> <span data-ttu-id="4aaea-147">Bir `password` öznitelik normalde güvenlik nedenleriyle yapılandırma dosyalarına girilmemelidir.</span><span class="sxs-lookup"><span data-stu-id="4aaea-147">A `password` attribute would not normally be entered in configuration files for security reasons.</span></span>  
  
 <span data-ttu-id="4aaea-148">`clientDomain`Özniteliği, Ilk SMTP protokol isteğinde kullanılan istemci etki alanı adını BIR SMTP sunucusuna değiştirir.</span><span class="sxs-lookup"><span data-stu-id="4aaea-148">The `clientDomain` attribute changes the client domain name used in the initial SMTP protocol request to an SMTP server.</span></span> <span data-ttu-id="4aaea-149">`clientDomain`Özniteliği, varsayılan olarak kullanılan localhost adı yerine, yerel makinenin tam etki alanı adına ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="4aaea-149">The `clientDomain` attribute can be set to the fully-qualified domain name of the local machine, rather than the localhost name that is used by default.</span></span> <span data-ttu-id="4aaea-150">Bu, SMTP protokol standartları ile daha fazla uyumluluk sağlar.</span><span class="sxs-lookup"><span data-stu-id="4aaea-150">This provides greater compliance with the SMTP protocol standards.</span></span> <span data-ttu-id="4aaea-151">Varsayılan değer, isteği gönderen yerel bilgisayarın localhost adıdır.</span><span class="sxs-lookup"><span data-stu-id="4aaea-151">The default value is the localhost name of the local computer sending the request.</span></span> <span data-ttu-id="4aaea-152"><xref:System.Net.Configuration.SmtpNetworkElement.ClientDomain%2A?displayProperty=nameWithType>Özelliği, geçerli yapılandırma dosyalarından özniteliğin geçerli değerini almak için kullanılabilir `clientDomain` .</span><span class="sxs-lookup"><span data-stu-id="4aaea-152">The <xref:System.Net.Configuration.SmtpNetworkElement.ClientDomain%2A?displayProperty=nameWithType> property can be used to get the current value of the `clientDomain` attribute from applicable configuration files.</span></span>  
  
 <span data-ttu-id="4aaea-153">`targetName`Öznitelik, genişletilmiş koruma kullanılırken kimlik doğrulaması için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4aaea-153">The `targetName` attribute is used for authentication when using extended protection.</span></span> <span data-ttu-id="4aaea-154">Varsayılan değer, \<host> \<host> SMTP posta sunucusunun ana bilgisayar adı olan "smtpsvc/" biçimindedir.</span><span class="sxs-lookup"><span data-stu-id="4aaea-154">The default value is of the form "SMTPSVC/\<host>" where \<host> is the hostname of the SMTP mail server.</span></span> <span data-ttu-id="4aaea-155"><xref:System.Net.Configuration.SmtpNetworkElement.TargetName%2A?displayProperty=nameWithType>Özelliği, geçerli yapılandırma dosyalarından özniteliğin geçerli değerini almak için kullanılabilir `targetName` .</span><span class="sxs-lookup"><span data-stu-id="4aaea-155">The <xref:System.Net.Configuration.SmtpNetworkElement.TargetName%2A?displayProperty=nameWithType> property can be used to get the current value of the `targetName` attribute from applicable configuration files.</span></span>  
  
 <span data-ttu-id="4aaea-156">`enableSsl`Özniteliği, SSL 'nin BIR SMTP posta sunucusuna erişmek için kullanılıp kullanılmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="4aaea-156">The `enableSsl` attribute specifies whether SSL is used to access an SMTP mail server.</span></span> <span data-ttu-id="4aaea-157"><xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>Sınıfı, RFC 3207 ' de tanımlanan Aktarım Katmanı Güvenliği üzerinden GÜVENLI SMTP IÇIN SMTP hizmeti uzantısını destekler.</span><span class="sxs-lookup"><span data-stu-id="4aaea-157">The <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType> class only supports the SMTP Service Extension for Secure SMTP over Transport Layer Security as defined in RFC 3207.</span></span> <span data-ttu-id="4aaea-158">Bu modda, SMTP oturumu şifrelenmemiş bir kanalda başlar, sonra SSL kullanarak güvenli iletişime geçmek için istemci tarafından sunucuya bir STARTTLS komutu verilir.</span><span class="sxs-lookup"><span data-stu-id="4aaea-158">In this mode, the SMTP session begins on an unencrypted channel, then a STARTTLS command is issued by the client to the server to switch to secure communication using SSL.</span></span> <span data-ttu-id="4aaea-159">Daha fazla bilgi için bkz. Internet Mühendisliği görev gücü (IETF) tarafından yayımlanan RFC 3207.</span><span class="sxs-lookup"><span data-stu-id="4aaea-159">See RFC 3207 published by the Internet Engineering Task Force (IETF) for more information.</span></span>  
  
 <span data-ttu-id="4aaea-160">Diğer bir bağlantı yöntemi, herhangi bir protokol komutu gönderilmeden önce bir SSL oturumunun kurulduğu yerdir.</span><span class="sxs-lookup"><span data-stu-id="4aaea-160">An alternate connection method is where an SSL session is established up front before any protocol commands are sent.</span></span> <span data-ttu-id="4aaea-161">Bu bağlantı yöntemi bazen SMTPS olarak adlandırılır ve varsayılan olarak 465 numaralı bağlantı noktasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="4aaea-161">This connection method is sometimes called SMTPS and by default uses port 465.</span></span> <span data-ttu-id="4aaea-162">SSL kullanan bu alternatif bağlantı yöntemi şu anda desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="4aaea-162">This alternate connection method using SSL is not currently supported.</span></span>  
  
 <span data-ttu-id="4aaea-163"><xref:System.Net.Configuration.SmtpNetworkElement.EnableSsl%2A?displayProperty=nameWithType>Özelliği, geçerli yapılandırma dosyalarından özniteliğin geçerli değerini almak için kullanılabilir `enableSsl` .</span><span class="sxs-lookup"><span data-stu-id="4aaea-163">The <xref:System.Net.Configuration.SmtpNetworkElement.EnableSsl%2A?displayProperty=nameWithType> property can be used to get the current value of the `enableSsl` attribute from applicable configuration files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4aaea-164">Örnek</span><span class="sxs-lookup"><span data-stu-id="4aaea-164">Example</span></span>  
 <span data-ttu-id="4aaea-165">Aşağıdaki örnek, varsayılan ağ kimlik bilgilerini kullanarak e-posta göndermek için uygun SMTP parametrelerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="4aaea-165">The following example specifies the appropriate SMTP parameters to send email using the default network credentials.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4aaea-166">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4aaea-166">See also</span></span>

- <xref:System.Net.Configuration.SmtpNetworkElement?displayProperty=nameWithType>
- <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>
- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- [<span data-ttu-id="4aaea-167">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="4aaea-167">Network Settings Schema</span></span>](index.md)
