---
title: <messageSenderAuthentication> öğesi
ms.date: 03/30/2017
ms.assetid: 8d979dfc-a6f9-42ec-96d5-7fbc13a48118
ms.openlocfilehash: 1e63b6fa93e1abfa87c83da4b5d46f492c59b9bc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931372"
---
# <a name="messagesenderauthentication-element"></a><span data-ttu-id="cf8fc-102">\<Iletienderauthentication > öğesi</span><span class="sxs-lookup"><span data-stu-id="cf8fc-102">\<messageSenderAuthentication> element</span></span>
<span data-ttu-id="cf8fc-103">Eşler arası ileti gönderenler için kimlik doğrulama seçeneklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="cf8fc-103">Specifies authentication options for peer-to-peer message senders.</span></span>  
  
 <span data-ttu-id="cf8fc-104">Eşler arası programlama hakkında daha fazla bilgi için bkz. eşler [arası ağ iletişimi](../../../wcf/feature-details/peer-to-peer-networking.md).</span><span class="sxs-lookup"><span data-stu-id="cf8fc-104">For more information about peer-to-peer programming, see [Peer-to-Peer Networking](../../../wcf/feature-details/peer-to-peer-networking.md).</span></span>  
  
 <span data-ttu-id="cf8fc-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="cf8fc-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="cf8fc-106">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="cf8fc-106">\<behaviors></span></span>  
<span data-ttu-id="cf8fc-107">\<Endpointdavranışlar ></span><span class="sxs-lookup"><span data-stu-id="cf8fc-107">\<endpointBehaviors></span></span>  
<span data-ttu-id="cf8fc-108">\<davranış ></span><span class="sxs-lookup"><span data-stu-id="cf8fc-108">\<behavior></span></span>  
<span data-ttu-id="cf8fc-109">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="cf8fc-109">\<clientCredentials></span></span>  
<span data-ttu-id="cf8fc-110">\<eş ></span><span class="sxs-lookup"><span data-stu-id="cf8fc-110">\<peer></span></span>  
<span data-ttu-id="cf8fc-111">\<Iletienderauthentication ></span><span class="sxs-lookup"><span data-stu-id="cf8fc-111">\<messageSenderAuthentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf8fc-112">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cf8fc-112">Syntax</span></span>  
  
```xml  
<messageSenderAuthentication customCertificateValidatorType= "namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"
                             certificateValidationMode = "ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"
                             revocationMode="NoCheck/Online/Offline"
                             trustedStoreLocation="CurrentUser/LocalMachine" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cf8fc-113">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="cf8fc-113">Attributes and Elements</span></span>  
 <span data-ttu-id="cf8fc-114">Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır</span><span class="sxs-lookup"><span data-stu-id="cf8fc-114">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cf8fc-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="cf8fc-115">Attributes</span></span>  
  
|<span data-ttu-id="cf8fc-116">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="cf8fc-116">Attribute</span></span>|<span data-ttu-id="cf8fc-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cf8fc-117">Description</span></span>|  
|---------------|-----------------|  
|`customCertificateValidatorType`|<span data-ttu-id="cf8fc-118">Özel bir türü doğrulamak için kullanılan tür ve derleme.</span><span class="sxs-lookup"><span data-stu-id="cf8fc-118">A type and assembly used to validate a custom type.</span></span> <span data-ttu-id="cf8fc-119">Bu öznitelik `certificateValidationMode` , olarak `Custom`ayarlandığında ayarlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="cf8fc-119">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span>|  
|`certificateValidationMode`|<span data-ttu-id="cf8fc-120">Kimlik bilgilerini doğrulamak için kullanılan üç moddan birini belirtir.</span><span class="sxs-lookup"><span data-stu-id="cf8fc-120">Specifies one of three modes used to validate credentials.</span></span> <span data-ttu-id="cf8fc-121">Olarak `Custom`ayarlanırsa, bir `customCertificateValidator` de sağlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="cf8fc-121">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span>|  
|`revocationMode`|<span data-ttu-id="cf8fc-122">İptal edilen bir sertifika listesini (CRL) denetlemek için kullanılan modlardan biri.</span><span class="sxs-lookup"><span data-stu-id="cf8fc-122">One of the modes used to check for a revoked certificate lists (CRL).</span></span>|  
|`trustedStoreLocation`|<span data-ttu-id="cf8fc-123">İki sistem depolama konumlarından biri: `LocalMachine` veya. `CurrentUser`</span><span class="sxs-lookup"><span data-stu-id="cf8fc-123">One of the two system store locations: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="cf8fc-124">Bu değer, bir hizmet sertifikası istemciye anlaşılırken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="cf8fc-124">This value is used when a service certificate is negotiated to the client.</span></span> <span data-ttu-id="cf8fc-125">Doğrulama, belirtilen depo konumundaki **güvenilir kişiler** deposuna göre gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="cf8fc-125">Validation is performed against the **Trusted People** store in the specified store location.</span></span>|  
  
## <a name="customcertificatevalidatortype-attribute"></a><span data-ttu-id="cf8fc-126">Customcercertificate Atevalidatortype özniteliği</span><span class="sxs-lookup"><span data-stu-id="cf8fc-126">customCertificateValidatorType Attribute</span></span>  
  
|<span data-ttu-id="cf8fc-127">Değer</span><span class="sxs-lookup"><span data-stu-id="cf8fc-127">Value</span></span>|<span data-ttu-id="cf8fc-128">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cf8fc-128">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="cf8fc-129">Dize</span><span class="sxs-lookup"><span data-stu-id="cf8fc-129">String</span></span>|<span data-ttu-id="cf8fc-130">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="cf8fc-130">Optional.</span></span> <span data-ttu-id="cf8fc-131">Türü bulmak için kullanılan tür adını ve derlemeyi ve diğer verileri belirtir.</span><span class="sxs-lookup"><span data-stu-id="cf8fc-131">Specifies the type name and assembly and other data used to find the type.</span></span> <span data-ttu-id="cf8fc-132">En azından, bir ad alanı ve tür adı gereklidir.</span><span class="sxs-lookup"><span data-stu-id="cf8fc-132">At minimum, a namespace and type name are required.</span></span> <span data-ttu-id="cf8fc-133">İsteğe bağlı bilgiler şunları içerir: derleme adı, sürüm numarası, kültür ve ortak anahtar belirteci.</span><span class="sxs-lookup"><span data-stu-id="cf8fc-133">Optional information includes: assembly name, version number, culture, and public key token.</span></span>|  
  
## <a name="certificatevalidationmode-attribute"></a><span data-ttu-id="cf8fc-134">certificateValidationMode özniteliği</span><span class="sxs-lookup"><span data-stu-id="cf8fc-134">certificateValidationMode Attribute</span></span>  
  
|<span data-ttu-id="cf8fc-135">Değer</span><span class="sxs-lookup"><span data-stu-id="cf8fc-135">Value</span></span>|<span data-ttu-id="cf8fc-136">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cf8fc-136">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="cf8fc-137">Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="cf8fc-137">Enumeration</span></span>|<span data-ttu-id="cf8fc-138">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="cf8fc-138">Optional.</span></span> <span data-ttu-id="cf8fc-139">Aşağıdaki değerlerden biri: `None`, `PeerTrust`, `ChainTrust` `PeerOrChainTrust`, ,`Custom`.</span><span class="sxs-lookup"><span data-stu-id="cf8fc-139">One of the following values: `None`, `PeerTrust`, `ChainTrust`, `PeerOrChainTrust`, `Custom`.</span></span> <span data-ttu-id="cf8fc-140">Varsayılan, `ChainTrust` değeridir.</span><span class="sxs-lookup"><span data-stu-id="cf8fc-140">The default is `ChainTrust`.</span></span> <span data-ttu-id="cf8fc-141">Varsayılan, `ChainTrust` değeridir.</span><span class="sxs-lookup"><span data-stu-id="cf8fc-141">The default is `ChainTrust`.</span></span><br /><br /> <span data-ttu-id="cf8fc-142">Daha fazla bilgi için bkz. [sertifikalarla çalışma](../../../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="cf8fc-142">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="revocationmode-attribute"></a><span data-ttu-id="cf8fc-143">revocationMode özniteliği</span><span class="sxs-lookup"><span data-stu-id="cf8fc-143">revocationMode Attribute</span></span>  
  
|<span data-ttu-id="cf8fc-144">Değer</span><span class="sxs-lookup"><span data-stu-id="cf8fc-144">Value</span></span>|<span data-ttu-id="cf8fc-145">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cf8fc-145">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="cf8fc-146">Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="cf8fc-146">Enumeration</span></span>|<span data-ttu-id="cf8fc-147">Aşağıdaki değerlerden biri: `NoCheck`, `Online`, `Offline`.</span><span class="sxs-lookup"><span data-stu-id="cf8fc-147">One of the following values: `NoCheck`, `Online`, `Offline`.</span></span> <span data-ttu-id="cf8fc-148">Varsayılan, `Online` değeridir.</span><span class="sxs-lookup"><span data-stu-id="cf8fc-148">The default is `Online`.</span></span><br /><br /> <span data-ttu-id="cf8fc-149">Daha fazla bilgi için bkz. [sertifikalarla çalışma](../../../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="cf8fc-149">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="trustedstorelocation-attribute"></a><span data-ttu-id="cf8fc-150">trustedStoreLocation özniteliği</span><span class="sxs-lookup"><span data-stu-id="cf8fc-150">trustedStoreLocation Attribute</span></span>  
  
|<span data-ttu-id="cf8fc-151">Değer</span><span class="sxs-lookup"><span data-stu-id="cf8fc-151">Value</span></span>|<span data-ttu-id="cf8fc-152">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cf8fc-152">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="cf8fc-153">Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="cf8fc-153">Enumeration</span></span>|<span data-ttu-id="cf8fc-154">Şu değerlerden biri: `LocalMachine` veya. `CurrentUser`</span><span class="sxs-lookup"><span data-stu-id="cf8fc-154">One of the following values: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="cf8fc-155">Varsayılan, `CurrentUser` değeridir.</span><span class="sxs-lookup"><span data-stu-id="cf8fc-155">The default is `CurrentUser`.</span></span> <span data-ttu-id="cf8fc-156">İstemci uygulaması bir sistem hesabı altında çalışıyorsa, sertifika genellikle altında `LocalMachine`olur.</span><span class="sxs-lookup"><span data-stu-id="cf8fc-156">If the client application is running under a system account then the certificate is typically under `LocalMachine`.</span></span> <span data-ttu-id="cf8fc-157">İstemci uygulaması bir kullanıcı hesabı altında çalışıyorsa, sertifika genellikle içinde `CurrentUser`olur.</span><span class="sxs-lookup"><span data-stu-id="cf8fc-157">If the client application is running under a user account then the certificate is typically in `CurrentUser`.</span></span> <span data-ttu-id="cf8fc-158">Varsayılan, `CurrentUser` değeridir.</span><span class="sxs-lookup"><span data-stu-id="cf8fc-158">The default is `CurrentUser`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cf8fc-159">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="cf8fc-159">Child Elements</span></span>  
 <span data-ttu-id="cf8fc-160">Yok.</span><span class="sxs-lookup"><span data-stu-id="cf8fc-160">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="cf8fc-161">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="cf8fc-161">Parent Elements</span></span>  
  
|<span data-ttu-id="cf8fc-162">Öğe</span><span class="sxs-lookup"><span data-stu-id="cf8fc-162">Element</span></span>|<span data-ttu-id="cf8fc-163">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cf8fc-163">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cf8fc-164">\<eş ></span><span class="sxs-lookup"><span data-stu-id="cf8fc-164">\<peer></span></span>](peer-of-clientcredentials-element.md)|<span data-ttu-id="cf8fc-165">İstemcinin kimliğini bir eş hizmette doğrulamak için kullanılan kimlik bilgisini belirtir.</span><span class="sxs-lookup"><span data-stu-id="cf8fc-165">Specifies a credential used for authenticating the client to a peer service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cf8fc-166">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cf8fc-166">Remarks</span></span>  
 <span data-ttu-id="cf8fc-167">İleti kimlik doğrulaması seçilirse, bu öğenin yapılandırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="cf8fc-167">This element must be configured if message authentication is chosen.</span></span> <span data-ttu-id="cf8fc-168">Çıkış kanalları için her ileti, [ \<sertifika >](certificate-element.md)tarafından belirtilen sertifika kullanılarak imzalanır.</span><span class="sxs-lookup"><span data-stu-id="cf8fc-168">For output channels, each message is signed using the certificate provided by [\<certificate>](certificate-element.md).</span></span> <span data-ttu-id="cf8fc-169">Uygulamaya teslim edilmeden önce tüm iletiler, bu öğenin `customCertificateValidatorType` özniteliği tarafından belirtilen Doğrulayıcı kullanılarak ileti kimlik bilgisine karşı denetlenir.</span><span class="sxs-lookup"><span data-stu-id="cf8fc-169">All messages, before delivered to the application, are checked against the message credential using the validator specified by the `customCertificateValidatorType` attribute of this element.</span></span> <span data-ttu-id="cf8fc-170">Doğrulayıcı kimlik bilgisini kabul edebilir veya reddedebilir.</span><span class="sxs-lookup"><span data-stu-id="cf8fc-170">The validator can either accept or reject the credential.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cf8fc-171">Örnek</span><span class="sxs-lookup"><span data-stu-id="cf8fc-171">Example</span></span>  
 <span data-ttu-id="cf8fc-172">Aşağıdaki kod ileti gönderici doğrulama modunu olarak `PeerOrChainTrust`ayarlar.</span><span class="sxs-lookup"><span data-stu-id="cf8fc-172">The following code sets the message sender validation mode to `PeerOrChainTrust`.</span></span>  
  
```xml  
<behaviors>
  <endpointBehaviors>
    <behavior name="MyEndpointBehavior">
      <clientCredentials>
        <peer>
          <certificate findValue="www.contoso.com"
                       storeLocation="LocalMachine"
                       x509FindType="FindByIssuerName" />
          <messageSenderAuthentication certificateValidationMode="PeerOrChainTrust" />
          <messageSenderAuthentication certificateValidationMode="None" />
        </peer>
      </clientCredentials>
    </behavior>
  </endpointBehaviors>
</behaviors>
```  
  
## <a name="see-also"></a><span data-ttu-id="cf8fc-173">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cf8fc-173">See also</span></span>

- <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>
- <xref:System.ServiceModel.Security.PeerCredential.MessageSenderAuthentication%2A>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement.MessageSenderAuthentication%2A>
- <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>
- [<span data-ttu-id="cf8fc-174">Sertifikalarla Çalışma</span><span class="sxs-lookup"><span data-stu-id="cf8fc-174">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="cf8fc-175">Eşler Arası Ağ</span><span class="sxs-lookup"><span data-stu-id="cf8fc-175">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
- <span data-ttu-id="cf8fc-176">[Eş kanal Iletisi kimlik doğrulaması](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="cf8fc-176">[Peer Channel Message Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="cf8fc-177">[Eş kanal özel kimlik doğrulaması](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="cf8fc-177">[Peer Channel Custom Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="cf8fc-178">Eş Kanalı Uygulamalarını Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="cf8fc-178">Securing Peer Channel Applications</span></span>](../../../wcf/feature-details/securing-peer-channel-applications.md)
