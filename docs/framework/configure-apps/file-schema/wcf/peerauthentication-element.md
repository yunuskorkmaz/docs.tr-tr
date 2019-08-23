---
title: <peerAuthentication> Öğesi
ms.date: 03/30/2017
ms.assetid: 09a8a9ff-e395-42f6-8ceb-9d44bdc1cbe1
ms.openlocfilehash: 09094c00b8faa28c37e202112251fee7cb4580be
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934014"
---
# <a name="peerauthentication-element"></a><span data-ttu-id="2e5ad-102">\<peerAuthentication > öğesi</span><span class="sxs-lookup"><span data-stu-id="2e5ad-102">\<peerAuthentication> Element</span></span>
<span data-ttu-id="2e5ad-103">Eşler arası istemciler için kimlik doğrulama seçeneklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="2e5ad-103">Specifies authentication options for peer-to-peer clients.</span></span>  
  
 <span data-ttu-id="2e5ad-104">Eşler arası programlama hakkında daha fazla bilgi için bkz. eşler [arası ağ iletişimi](../../../wcf/feature-details/peer-to-peer-networking.md).</span><span class="sxs-lookup"><span data-stu-id="2e5ad-104">For more information about peer-to-peer programming, see [Peer-to-Peer Networking](../../../wcf/feature-details/peer-to-peer-networking.md).</span></span>  
  
 <span data-ttu-id="2e5ad-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="2e5ad-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="2e5ad-106">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="2e5ad-106">\<behaviors></span></span>  
<span data-ttu-id="2e5ad-107">\<Endpointdavranışlar ></span><span class="sxs-lookup"><span data-stu-id="2e5ad-107">\<endpointBehaviors></span></span>  
<span data-ttu-id="2e5ad-108">\<davranış ></span><span class="sxs-lookup"><span data-stu-id="2e5ad-108">\<behavior></span></span>  
<span data-ttu-id="2e5ad-109">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="2e5ad-109">\<clientCredentials></span></span>  
<span data-ttu-id="2e5ad-110">\<eş ></span><span class="sxs-lookup"><span data-stu-id="2e5ad-110">\<peer></span></span>  
<span data-ttu-id="2e5ad-111">\<PeerAuthentication ></span><span class="sxs-lookup"><span data-stu-id="2e5ad-111">\<PeerAuthentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e5ad-112">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2e5ad-112">Syntax</span></span>  
  
```xml  
<peerAuthentication customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"
                    certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"
                    revocationMode="NoCheck/Online/Offline"
                    trustedStoreLocation="CurrentUser/LocalMachine" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2e5ad-113">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="2e5ad-113">Attributes and Elements</span></span>  
 <span data-ttu-id="2e5ad-114">Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır</span><span class="sxs-lookup"><span data-stu-id="2e5ad-114">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2e5ad-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="2e5ad-115">Attributes</span></span>  
  
|<span data-ttu-id="2e5ad-116">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="2e5ad-116">Attribute</span></span>|<span data-ttu-id="2e5ad-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2e5ad-117">Description</span></span>|  
|---------------|-----------------|  
|`customCertificateValidatorType`|<span data-ttu-id="2e5ad-118">İsteğe bağlı dize.</span><span class="sxs-lookup"><span data-stu-id="2e5ad-118">Optional string.</span></span> <span data-ttu-id="2e5ad-119">Özel bir türü doğrulamak için kullanılan tür ve derleme.</span><span class="sxs-lookup"><span data-stu-id="2e5ad-119">A type and assembly used to validate a custom type.</span></span> <span data-ttu-id="2e5ad-120">Bu öznitelik `certificateValidationMode` , olarak `Custom`ayarlandığında ayarlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2e5ad-120">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span>|  
|`certificateValidationMode`|<span data-ttu-id="2e5ad-121">İsteğe bağlı sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="2e5ad-121">Optional enumeration.</span></span> <span data-ttu-id="2e5ad-122">Kimlik bilgilerini doğrulamak için kullanılan üç moddan birini belirtir.</span><span class="sxs-lookup"><span data-stu-id="2e5ad-122">Specifies one of three modes used to validate credentials.</span></span> <span data-ttu-id="2e5ad-123">Olarak `Custom`ayarlanırsa, bir `customCertificateValidator` de sağlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2e5ad-123">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span> <span data-ttu-id="2e5ad-124">Varsayılan, `ChainTrust` değeridir.</span><span class="sxs-lookup"><span data-stu-id="2e5ad-124">The default is `ChainTrust`.</span></span>|  
|`revocationMode`|<span data-ttu-id="2e5ad-125">İsteğe bağlı sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="2e5ad-125">Optional enumeration.</span></span> <span data-ttu-id="2e5ad-126">İptal edilen bir sertifika listesini (CRL) denetlemek için kullanılan modlardan biri.</span><span class="sxs-lookup"><span data-stu-id="2e5ad-126">One of the modes used to check for a revoked certificate lists (CRL).</span></span> <span data-ttu-id="2e5ad-127">Varsayılan, `Online` değeridir.</span><span class="sxs-lookup"><span data-stu-id="2e5ad-127">The default is `Online`.</span></span>|  
|`trustedStoreLocation`|<span data-ttu-id="2e5ad-128">İsteğe bağlı sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="2e5ad-128">Optional enumeration.</span></span> <span data-ttu-id="2e5ad-129">İki sistem depolama konumlarından biri: `LocalMachine` veya. `CurrentUser`</span><span class="sxs-lookup"><span data-stu-id="2e5ad-129">One of the two system store locations: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="2e5ad-130">Bu değer, bir hizmet sertifikası istemciye anlaşılırken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2e5ad-130">This value is used when a service certificate is negotiated to the client.</span></span> <span data-ttu-id="2e5ad-131">Doğrulama, belirtilen depo konumundaki **güvenilir kişiler** deposuna göre gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="2e5ad-131">Validation is performed against the **Trusted People** store in the specified store location.</span></span> <span data-ttu-id="2e5ad-132">Varsayılan, `CurrentUser` değeridir.</span><span class="sxs-lookup"><span data-stu-id="2e5ad-132">The default is `CurrentUser`.</span></span>|  
  
## <a name="customcertificatevalidatortype-attribute"></a><span data-ttu-id="2e5ad-133">Customcercertificate Atevalidatortype özniteliği</span><span class="sxs-lookup"><span data-stu-id="2e5ad-133">customCertificateValidatorType Attribute</span></span>  
  
|<span data-ttu-id="2e5ad-134">Değer</span><span class="sxs-lookup"><span data-stu-id="2e5ad-134">Value</span></span>|<span data-ttu-id="2e5ad-135">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2e5ad-135">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="2e5ad-136">Dize</span><span class="sxs-lookup"><span data-stu-id="2e5ad-136">String</span></span>|<span data-ttu-id="2e5ad-137">Türü bulmak için kullanılan tür adını ve derlemeyi ve diğer verileri belirtir.</span><span class="sxs-lookup"><span data-stu-id="2e5ad-137">Specifies the type name and assembly and other data used to find the type.</span></span> <span data-ttu-id="2e5ad-138">En azından, bir ad alanı ve tür adı gereklidir.</span><span class="sxs-lookup"><span data-stu-id="2e5ad-138">At minimum, a namespace and type name are required.</span></span> <span data-ttu-id="2e5ad-139">İsteğe bağlı bilgiler şunları içerir: derleme adı, sürüm numarası, kültür ve ortak anahtar belirteci.</span><span class="sxs-lookup"><span data-stu-id="2e5ad-139">Optional information includes: assembly name, version number, culture, and public key token.</span></span>|  
  
## <a name="certificatevalidationmode-attribute"></a><span data-ttu-id="2e5ad-140">certificateValidationMode özniteliği</span><span class="sxs-lookup"><span data-stu-id="2e5ad-140">certificateValidationMode Attribute</span></span>  
  
|<span data-ttu-id="2e5ad-141">Değer</span><span class="sxs-lookup"><span data-stu-id="2e5ad-141">Value</span></span>|<span data-ttu-id="2e5ad-142">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2e5ad-142">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="2e5ad-143">Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="2e5ad-143">Enumeration</span></span>|<span data-ttu-id="2e5ad-144">Aşağıdaki değerlerden biri: `None`, `PeerTrust`, `ChainTrust` `PeerOrChainTrust`, ,`Custom`.</span><span class="sxs-lookup"><span data-stu-id="2e5ad-144">One of the following values: `None`, `PeerTrust`, `ChainTrust`, `PeerOrChainTrust`, `Custom`.</span></span> <span data-ttu-id="2e5ad-145">Varsayılan, `ChainTrust` değeridir.</span><span class="sxs-lookup"><span data-stu-id="2e5ad-145">The default is `ChainTrust`.</span></span><br /><br /> <span data-ttu-id="2e5ad-146">Daha fazla bilgi için bkz. [sertifikalarla çalışma](../../../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="2e5ad-146">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="revocationmode-attribute"></a><span data-ttu-id="2e5ad-147">revocationMode özniteliği</span><span class="sxs-lookup"><span data-stu-id="2e5ad-147">revocationMode Attribute</span></span>  
  
|<span data-ttu-id="2e5ad-148">Değer</span><span class="sxs-lookup"><span data-stu-id="2e5ad-148">Value</span></span>|<span data-ttu-id="2e5ad-149">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2e5ad-149">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="2e5ad-150">Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="2e5ad-150">Enumeration</span></span>|<span data-ttu-id="2e5ad-151">Aşağıdaki değerlerden biri: `NoCheck`, `Online`, `Offline`.</span><span class="sxs-lookup"><span data-stu-id="2e5ad-151">One of the following values: `NoCheck`, `Online`, `Offline`.</span></span> <span data-ttu-id="2e5ad-152">Varsayılan, `Online` değeridir.</span><span class="sxs-lookup"><span data-stu-id="2e5ad-152">The default is `Online`.</span></span><br /><br /> <span data-ttu-id="2e5ad-153">Daha fazla bilgi için bkz. [sertifikalarla çalışma](../../../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="2e5ad-153">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="trustedstorelocation-attribute"></a><span data-ttu-id="2e5ad-154">trustedStoreLocation özniteliği</span><span class="sxs-lookup"><span data-stu-id="2e5ad-154">trustedStoreLocation Attribute</span></span>  
  
|<span data-ttu-id="2e5ad-155">Değer</span><span class="sxs-lookup"><span data-stu-id="2e5ad-155">Value</span></span>|<span data-ttu-id="2e5ad-156">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2e5ad-156">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="2e5ad-157">Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="2e5ad-157">Enumeration</span></span>|<span data-ttu-id="2e5ad-158">Şu değerlerden biri: `LocalMachine` veya. `CurrentUser`</span><span class="sxs-lookup"><span data-stu-id="2e5ad-158">One of the following values: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="2e5ad-159">Varsayılan, `CurrentUser` değeridir.</span><span class="sxs-lookup"><span data-stu-id="2e5ad-159">The default is `CurrentUser`.</span></span> <span data-ttu-id="2e5ad-160">İstemci uygulaması bir sistem hesabı altında çalışıyorsa, sertifika genellikle altında `LocalMachine`olur.</span><span class="sxs-lookup"><span data-stu-id="2e5ad-160">If the client application is running under a system account then the certificate is typically under `LocalMachine`.</span></span> <span data-ttu-id="2e5ad-161">İstemci uygulaması bir kullanıcı hesabı altında çalışıyorsa, sertifika genellikle içinde `CurrentUser`olur.</span><span class="sxs-lookup"><span data-stu-id="2e5ad-161">If the client application is running under a user account then the certificate is typically in `CurrentUser`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2e5ad-162">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="2e5ad-162">Child Elements</span></span>  
 <span data-ttu-id="2e5ad-163">Yok.</span><span class="sxs-lookup"><span data-stu-id="2e5ad-163">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2e5ad-164">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="2e5ad-164">Parent Elements</span></span>  
  
|<span data-ttu-id="2e5ad-165">Öğe</span><span class="sxs-lookup"><span data-stu-id="2e5ad-165">Element</span></span>|<span data-ttu-id="2e5ad-166">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2e5ad-166">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2e5ad-167">\<eş ></span><span class="sxs-lookup"><span data-stu-id="2e5ad-167">\<peer></span></span>](peer-of-clientcredentials-element.md)|<span data-ttu-id="2e5ad-168">İstemcinin kimliğini bir eş hizmette doğrulamak için kullanılan kimlik bilgisini belirtir.</span><span class="sxs-lookup"><span data-stu-id="2e5ad-168">Specifies a credential used for authenticating the client to a peer service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2e5ad-169">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2e5ad-169">Remarks</span></span>  
 <span data-ttu-id="2e5ad-170">`<authentication>` Öğesi <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication> sınıfına karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="2e5ad-170">The `<authentication>` element corresponds to the <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication> class.</span></span> <span data-ttu-id="2e5ad-171">Bu öğe, ağ içinde komşu-komşu kimlik doğrulaması sırasında çağrılan bir doğrulayıcısı belirtir.</span><span class="sxs-lookup"><span data-stu-id="2e5ad-171">This element specifies a validator, which is invoked during neighbor-to-neighbor authentication in the mesh.</span></span> <span data-ttu-id="2e5ad-172">Yeni bir eş bir komşu bağlantı kurmaya çalıştığında, kendi kimlik bilgilerini yanıt veren eşe geçirir.</span><span class="sxs-lookup"><span data-stu-id="2e5ad-172">When a new peer tries to establish a neighbor connection, it passes its own credential to the responding peer.</span></span> <span data-ttu-id="2e5ad-173">Yanıtlayanın Doğrulayıcısı, uzak tarafın kimlik bilgilerini doğrulamak için çağrılır.</span><span class="sxs-lookup"><span data-stu-id="2e5ad-173">The validator of the responder is invoked to verify the credential of the remote party.</span></span> <span data-ttu-id="2e5ad-174">Kafeste bir eş bağlantı oluşturulduğunda her iki eş de karşılıklı olarak doğrulanır, her iki uçta da doğrulayıcılar çağrılır.</span><span class="sxs-lookup"><span data-stu-id="2e5ad-174">Whenever a peer connection is established in the mesh, both peers are mutually authenticated, meaning validators on both ends are invoked.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2e5ad-175">Örnek</span><span class="sxs-lookup"><span data-stu-id="2e5ad-175">Example</span></span>  
 <span data-ttu-id="2e5ad-176">Aşağıdaki kod, sertifika doğrulama modunu olarak `PeerOrChainTrust`ayarlar.</span><span class="sxs-lookup"><span data-stu-id="2e5ad-176">The following code sets the certificate validation mode to `PeerOrChainTrust`.</span></span>  
  
```xml  
<behaviors>
  <endpointBehaviors>
    <behavior name="MyEndpointBehavior">
      <clientCredentials>
        <peer>
          <certificate findValue="www.contoso.com"
                       storeLocation="LocalMachine"
                       x509FindType="FindByIssuerName" />
          <peerAuthentication certificateValidationMode="PeerOrChainTrust" />
          <messageSenderAuthentication certificateValidationMode="None" />
        </peer>
      </clientCredentials>
    </behavior>
  </endpointBehaviors>
</behaviors>
```  
  
## <a name="see-also"></a><span data-ttu-id="2e5ad-177">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2e5ad-177">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>
- <xref:System.ServiceModel.Security.PeerCredential.PeerAuthentication%2A>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement.PeerAuthentication%2A>
- <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>
- [<span data-ttu-id="2e5ad-178">Sertifikalarla Çalışma</span><span class="sxs-lookup"><span data-stu-id="2e5ad-178">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="2e5ad-179">Eşler Arası Ağ</span><span class="sxs-lookup"><span data-stu-id="2e5ad-179">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
- <span data-ttu-id="2e5ad-180">[Eş kanal Iletisi kimlik doğrulaması](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="2e5ad-180">[Peer Channel Message Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="2e5ad-181">[Eş kanal özel kimlik doğrulaması](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="2e5ad-181">[Peer Channel Custom Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="2e5ad-182">Eş Kanalı Uygulamalarını Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="2e5ad-182">Securing Peer Channel Applications</span></span>](../../../wcf/feature-details/securing-peer-channel-applications.md)
