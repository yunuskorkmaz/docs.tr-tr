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
ms.openlocfilehash: 679351fd2d6f0727d40bd57c9ef2016738462eb7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltnetworkgt-element-network-settings"></a><span data-ttu-id="3e2e9-102">&lt;Ağ&gt; öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="3e2e9-102">&lt;network&gt; Element (Network Settings)</span></span>
<span data-ttu-id="3e2e9-103">Harici bir Basit Posta Aktarım Protokolü (SMTP) sunucusu için ağ seçenekleri yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="3e2e9-103">Configures the network options for an external Simple Mail Transport Protocol (SMTP) server.</span></span>  
  
 <span data-ttu-id="3e2e9-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="3e2e9-104">\<configuration></span></span>  
<span data-ttu-id="3e2e9-105">\<System.NET ></span><span class="sxs-lookup"><span data-stu-id="3e2e9-105">\<system.net></span></span>  
<span data-ttu-id="3e2e9-106">\<mailSettings ></span><span class="sxs-lookup"><span data-stu-id="3e2e9-106">\<mailSettings></span></span>  
<span data-ttu-id="3e2e9-107">\<SMTP ></span><span class="sxs-lookup"><span data-stu-id="3e2e9-107">\<smtp></span></span>  
<span data-ttu-id="3e2e9-108">\<Ağ ></span><span class="sxs-lookup"><span data-stu-id="3e2e9-108">\<network></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e2e9-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3e2e9-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3e2e9-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="3e2e9-110">Attributes and Elements</span></span>  
 <span data-ttu-id="3e2e9-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3e2e9-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3e2e9-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="3e2e9-112">Attributes</span></span>  
  
|<span data-ttu-id="3e2e9-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="3e2e9-113">Attribute</span></span>|<span data-ttu-id="3e2e9-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3e2e9-114">Description</span></span>|  
|---------------|-----------------|  
|`clientDomain`|<span data-ttu-id="3e2e9-115">İlk SMTP protokolü istekte SMTP posta sunucusuna bağlanmak için kullanılacak istemci etki alanı adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="3e2e9-115">Specifies the client domain name to use in the initial SMTP protocol request to connect to the SMTP mail server.</span></span> <span data-ttu-id="3e2e9-116">Varsayılan değer isteği gönderilirken yerel bilgisayar localhost adıdır.</span><span class="sxs-lookup"><span data-stu-id="3e2e9-116">The default value is the localhost name of the local computer sending the request.</span></span>|  
|`defaultCredentials`|<span data-ttu-id="3e2e9-117">Varsayılan kullanıcı kimlik bilgilerini SMTP işlemleri için SMTP posta sunucusuna erişmek için kullanılması gerekip gerekmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="3e2e9-117">Specifies whether the default user credentials should be used to access the SMTP mail server for SMTP transactions.</span></span> <span data-ttu-id="3e2e9-118">Varsayılan değer `false` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="3e2e9-118">The default value is `false`.</span></span>|  
|`enableSsl`|<span data-ttu-id="3e2e9-119">Bir SMTP posta sunucusuna erişmek için SSL kullanılıp kullanılmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="3e2e9-119">Specifies whether SSL is used to access an SMTP mail server.</span></span> <span data-ttu-id="3e2e9-120">Varsayılan değer `false` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="3e2e9-120">The default value is `false`.</span></span>|  
|`host`|<span data-ttu-id="3e2e9-121">SMTP işlemleri için kullanılacak SMTP posta sunucusu konak adı belirtir.</span><span class="sxs-lookup"><span data-stu-id="3e2e9-121">Specifies the hostname of the SMTP mail server to use for SMTP transactions.</span></span> <span data-ttu-id="3e2e9-122">Bu öznitelik varsayılan değeri yok.</span><span class="sxs-lookup"><span data-stu-id="3e2e9-122">This attribute has no default value.</span></span>|  
|`password`|<span data-ttu-id="3e2e9-123">SMTP posta sunucusuna kimlik doğrulaması için kullanılacak parolayı belirtir.</span><span class="sxs-lookup"><span data-stu-id="3e2e9-123">Specifies the password to use for authentication to the SMTP mail server.</span></span> <span data-ttu-id="3e2e9-124">Bu öznitelik varsayılan değeri yok.</span><span class="sxs-lookup"><span data-stu-id="3e2e9-124">This attribute has no default value.</span></span>|  
|`port`|<span data-ttu-id="3e2e9-125">SMTP posta sunucusuna bağlanmak için kullanılacak bağlantı noktası numarasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="3e2e9-125">Specifies the port number to use to connect to the SMTP mail server.</span></span> <span data-ttu-id="3e2e9-126">Varsayılan değer 25'tir.</span><span class="sxs-lookup"><span data-stu-id="3e2e9-126">The default value is 25.</span></span>|  
|`targetName`|<span data-ttu-id="3e2e9-127">SMTP işlemleri için genişletilmiş koruma kullanırken, kimlik doğrulaması için kullanılacak hizmet sağlayıcı adı (SPN) belirtir.</span><span class="sxs-lookup"><span data-stu-id="3e2e9-127">Specifies the Service Provider Name (SPN) to use for authentication when using extended protection for SMTP transactions.</span></span> <span data-ttu-id="3e2e9-128">Bu öznitelik varsayılan değeri yok.</span><span class="sxs-lookup"><span data-stu-id="3e2e9-128">This attribute has no default value.</span></span>|  
|`userName`|<span data-ttu-id="3e2e9-129">SMTP posta sunucusuna kimlik doğrulaması için kullanılacak kullanıcı adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="3e2e9-129">Specifies the user name to use for authentication to the SMTP mail server.</span></span> <span data-ttu-id="3e2e9-130">Bu öznitelik varsayılan değeri yok.</span><span class="sxs-lookup"><span data-stu-id="3e2e9-130">This attribute has no default value.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3e2e9-131">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="3e2e9-131">Child Elements</span></span>  
 <span data-ttu-id="3e2e9-132">Yok.</span><span class="sxs-lookup"><span data-stu-id="3e2e9-132">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3e2e9-133">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="3e2e9-133">Parent Elements</span></span>  
  
|<span data-ttu-id="3e2e9-134">Öğe</span><span class="sxs-lookup"><span data-stu-id="3e2e9-134">Element</span></span>|<span data-ttu-id="3e2e9-135">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3e2e9-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3e2e9-136">\<SMTP > öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="3e2e9-136">\<smtp> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/smtp-element-network-settings.md)|<span data-ttu-id="3e2e9-137">Basit Posta Aktarım Protokolü (SMTP) posta gönderme seçenekleri yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="3e2e9-137">Configures Simple Mail Transport Protocol (SMTP) mail sending options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3e2e9-138">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3e2e9-138">Remarks</span></span>  
 <span data-ttu-id="3e2e9-139">Bazı SMTP sunucuları kendiniz kullanmadan önce sunucuya kimliğiniz olmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="3e2e9-139">Some SMTP servers require that you authenticate yourself to the server before use.</span></span> <span data-ttu-id="3e2e9-140">Kendiniz ana bilgisayarda varsayılan ağ kimlik bilgilerini kullanarak kimlik doğrulaması yapmak istiyorsanız ayarlamak `defaultCredentials` özniteliğini `true`.</span><span class="sxs-lookup"><span data-stu-id="3e2e9-140">If you want to authenticate yourself using the default network credentials on your host, set the `defaultCredentials` attribute to `true`.</span></span> <span data-ttu-id="3e2e9-141"><xref:System.Net.Configuration.SmtpNetworkElement.DefaultCredentials%2A?displayProperty=nameWithType> Özelliği, geçerli değerini almak için kullanılabilir `defaultCredentials` geçerli yapılandırma dosyalarını özniteliği.</span><span class="sxs-lookup"><span data-stu-id="3e2e9-141">The <xref:System.Net.Configuration.SmtpNetworkElement.DefaultCredentials%2A?displayProperty=nameWithType> property can be used to get the current value of the `defaultCredentials` attribute from applicable configuration files.</span></span>  
  
 <span data-ttu-id="3e2e9-142">Temel kimlik doğrulaması (bir kullanıcı adı ve parola) kendiniz SMTP sunucusuna kimlik doğrulaması için de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3e2e9-142">You can also use basic authentication (a user name and password) to authenticate yourself to the SMTP server.</span></span> <span data-ttu-id="3e2e9-143">Bu seçeneği kullanmak için geçerli bir kullanıcı adı ve belirtilen SMTP sunucusu için parola belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="3e2e9-143">To use this option, you must specify a valid user name and password for the specified SMTP server.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3e2e9-144">Temel kimlik doğrulaması gönderir `userName` ve `password` şifrelenmemiş sunucuya değerleri.</span><span class="sxs-lookup"><span data-stu-id="3e2e9-144">Basic authentication sends the `userName` and `password` values to the server unencrypted.</span></span> <span data-ttu-id="3e2e9-145">Herkes ağ trafiğini izleme kimlik bilgilerinizi görüntülemek ve bunları sunucuya bağlanmak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="3e2e9-145">Anyone monitoring network traffic can view your credentials and use them to connect to the server.</span></span> <span data-ttu-id="3e2e9-146">Kerberos ya da NT LAN Yöneticisi (NTLM) gibi daha güvenli bir kimlik doğrulama mekanizması kullanmayı düşünmeniz gerekir Varsa `defaultCredentials` olan `true`, Kerberos veya NTLM kullanılacak sunucunun bu protokollerin destekliyorsa.</span><span class="sxs-lookup"><span data-stu-id="3e2e9-146">You should consider using a more secure authentication mechanism, such as Kerberos or NT LAN Manager (NTLM.) If `defaultCredentials` is `true`, Kerberos or NTLM will be used if the server supports these protocols.</span></span>  
  
 <span data-ttu-id="3e2e9-147">Temel kimlik doğrulaması ve varsayılan ağ kimlik bilgileri seçenekleri karşılıklı olarak birbirini dışlar; ayarlarsanız `defaultCredentials` için `true` ve bir kullanıcı adı ve parola belirtin, varsayılan ağ kimlik bilgisi kullanılır ve temel kimlik doğrulama verileri göz ardı edilir.</span><span class="sxs-lookup"><span data-stu-id="3e2e9-147">The basic authentication and default network credentials options are mutually exclusive; if you set `defaultCredentials` to `true` and specify a user name and password, the default network credential is used, and the basic authentication data is ignored.</span></span>  
  
 <span data-ttu-id="3e2e9-148">Belirtirseniz, temel kimlik doğrulaması için bir `userName`, ayrıca belirtmelisiniz bir `password` kimlik doğrulaması için kendiniz posta sunucusuna.</span><span class="sxs-lookup"><span data-stu-id="3e2e9-148">For basic authentication if you specify a `userName`, you should also specify a `password` to authentication yourself to the mail server.</span></span>  
  
 <span data-ttu-id="3e2e9-149"><xref:System.Net.Configuration.SmtpNetworkElement.UserName%2A?displayProperty=nameWithType> Özelliği, geçerli değerini almak için kullanılabilir `userName` geçerli yapılandırma dosyalarını özniteliği.</span><span class="sxs-lookup"><span data-stu-id="3e2e9-149">The <xref:System.Net.Configuration.SmtpNetworkElement.UserName%2A?displayProperty=nameWithType> property can be used to get the current value of the `userName` attribute from applicable configuration files.</span></span> <span data-ttu-id="3e2e9-150"><xref:System.Net.Configuration.SmtpNetworkElement.Password%2A?displayProperty=nameWithType> Özelliği, geçerli değerini almak için kullanılabilir `password` geçerli yapılandırma dosyalarını özniteliği.</span><span class="sxs-lookup"><span data-stu-id="3e2e9-150">The <xref:System.Net.Configuration.SmtpNetworkElement.Password%2A?displayProperty=nameWithType> property can be used to get the current value of the `password` attribute from applicable configuration files.</span></span> <span data-ttu-id="3e2e9-151">A `password` özniteliği değil normalde girilmesi güvenlik nedenleriyle yapılandırma dosyalarında.</span><span class="sxs-lookup"><span data-stu-id="3e2e9-151">A `password` attribute would not normally be entered in configuration files for security reasons.</span></span>  
  
 <span data-ttu-id="3e2e9-152">`clientDomain` Özniteliği ilk SMTP protokolü isteği bir SMTP sunucusu için kullanılan istemci etki alanı adı değiştirir.</span><span class="sxs-lookup"><span data-stu-id="3e2e9-152">The `clientDomain` attribute changes the client domain name used in the initial SMTP protocol request to an SMTP server.</span></span> <span data-ttu-id="3e2e9-153">`clientDomain` Özniteliği, varsayılan olarak kullanılan localhost adı yerine yerel makinenin tam etki alanı adı için ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="3e2e9-153">The `clientDomain` attribute can be set to the fully-qualified domain name of the local machine, rather than the localhost name that is used by default.</span></span> <span data-ttu-id="3e2e9-154">Bu, SMTP protokolü standartları ile büyük uyumluluk sağlar.</span><span class="sxs-lookup"><span data-stu-id="3e2e9-154">This provides greater compliance with the SMTP protocol standards.</span></span> <span data-ttu-id="3e2e9-155">Varsayılan değer isteği gönderilirken yerel bilgisayar localhost adıdır.</span><span class="sxs-lookup"><span data-stu-id="3e2e9-155">The default value is the localhost name of the local computer sending the request.</span></span> <span data-ttu-id="3e2e9-156"><xref:System.Net.Configuration.SmtpNetworkElement.ClientDomain%2A?displayProperty=nameWithType> Özelliği, geçerli değerini almak için kullanılabilir `clientDomain` geçerli yapılandırma dosyalarını özniteliği.</span><span class="sxs-lookup"><span data-stu-id="3e2e9-156">The <xref:System.Net.Configuration.SmtpNetworkElement.ClientDomain%2A?displayProperty=nameWithType> property can be used to get the current value of the `clientDomain` attribute from applicable configuration files.</span></span>  
  
 <span data-ttu-id="3e2e9-157">`targetName` Genişletilmiş koruma kullanırken özniteliği kimlik doğrulaması için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3e2e9-157">The `targetName` attribute is used for authentication when using extended protection.</span></span> <span data-ttu-id="3e2e9-158">Varsayılan değer biçimindedir "SMTPSVC /\<ana bilgisayar >" nerede \<ana bilgisayar > SMTP posta sunucusunu barındırıcı adıdır.</span><span class="sxs-lookup"><span data-stu-id="3e2e9-158">The default value is of the form "SMTPSVC/\<host>" where \<host> is the hostname of the SMTP mail server.</span></span> <span data-ttu-id="3e2e9-159"><xref:System.Net.Configuration.SmtpNetworkElement.TargetName%2A?displayProperty=nameWithType> Özelliği, geçerli değerini almak için kullanılabilir `targetName` geçerli yapılandırma dosyalarını özniteliği.</span><span class="sxs-lookup"><span data-stu-id="3e2e9-159">The <xref:System.Net.Configuration.SmtpNetworkElement.TargetName%2A?displayProperty=nameWithType> property can be used to get the current value of the `targetName` attribute from applicable configuration files.</span></span>  
  
 <span data-ttu-id="3e2e9-160">`enableSsl` Özniteliği, bir SMTP posta sunucusuna erişmek için SSL kullanılıp kullanılmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="3e2e9-160">The `enableSsl` attribute specifies whether SSL is used to access an SMTP mail server.</span></span> <span data-ttu-id="3e2e9-161"><xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType> Sınıfı yalnızca destekler SMTP hizmeti uzantı güvenli SMTP için Aktarım Katmanı Güvenliği RFC 3207 içinde tanımlanan.</span><span class="sxs-lookup"><span data-stu-id="3e2e9-161">The <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType> class only supports the SMTP Service Extension for Secure SMTP over Transport Layer Security as defined in RFC 3207.</span></span> <span data-ttu-id="3e2e9-162">Bu modda, şifrelenmemiş bir kanal üzerinde SMTP oturumunu başlar, sonra STARTTLS komut SSL ile güvenli iletişim için geçiş yapmak için sunucuya istemci tarafından verilir.</span><span class="sxs-lookup"><span data-stu-id="3e2e9-162">In this mode, the SMTP session begins on an unencrypted channel, then a STARTTLS command is issued by the client to the server to switch to secure communication using SSL.</span></span> <span data-ttu-id="3e2e9-163">RFC Internet Engineering Task Force (IETF) tarafından daha fazla bilgi için yayımlanan 3207 bakın.</span><span class="sxs-lookup"><span data-stu-id="3e2e9-163">See RFC 3207 published by the Internet Engineering Task Force (IETF) for more information.</span></span>  
  
 <span data-ttu-id="3e2e9-164">Bir SSL oturumu komutları gönderilen herhangi bir protokol önce Önden burada kurulmuş bir alternatif bağlantı yöntemidir.</span><span class="sxs-lookup"><span data-stu-id="3e2e9-164">An alternate connection method is where an SSL session is established up front before any protocol commands are sent.</span></span> <span data-ttu-id="3e2e9-165">Bu bağlantı yöntemi SMTPS adlandırılır ve varsayılan olarak bağlantı noktası 465 kullanır.</span><span class="sxs-lookup"><span data-stu-id="3e2e9-165">This connection method is sometimes called SMTPS and by default uses port 465.</span></span> <span data-ttu-id="3e2e9-166">Bu alternatif bağlantı yöntemi SSL kullanarak şu anda desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="3e2e9-166">This alternate connection method using SSL is not currently supported.</span></span>  
  
 <span data-ttu-id="3e2e9-167"><xref:System.Net.Configuration.SmtpNetworkElement.EnableSsl%2A?displayProperty=nameWithType> Özelliği, geçerli değerini almak için kullanılabilir `enableSsl` geçerli yapılandırma dosyalarını özniteliği.</span><span class="sxs-lookup"><span data-stu-id="3e2e9-167">The <xref:System.Net.Configuration.SmtpNetworkElement.EnableSsl%2A?displayProperty=nameWithType> property can be used to get the current value of the `enableSsl` attribute from applicable configuration files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3e2e9-168">Örnek</span><span class="sxs-lookup"><span data-stu-id="3e2e9-168">Example</span></span>  
 <span data-ttu-id="3e2e9-169">Aşağıdaki örnek, varsayılan ağ kimlik bilgilerini kullanarak e-posta göndermek için uygun SMTP parametreleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="3e2e9-169">The following example specifies the appropriate SMTP parameters to send e-mail using the default network credentials.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3e2e9-170">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3e2e9-170">See Also</span></span>  
 <xref:System.Net.Configuration.SmtpNetworkElement?displayProperty=nameWithType>  
 <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>  
 <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>  
 [<span data-ttu-id="3e2e9-171">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="3e2e9-171">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
