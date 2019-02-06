---
title: <peerAuthentication> Öğesi
ms.date: 03/30/2017
ms.assetid: 09a8a9ff-e395-42f6-8ceb-9d44bdc1cbe1
ms.openlocfilehash: 7607f5bab6083c190303fd0a9121ffab55c620c3
ms.sourcegitcommit: 01ea420eaa4bf76d5fc47673294c8881379b3369
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2019
ms.locfileid: "55759450"
---
# <a name="peerauthentication-element"></a><span data-ttu-id="f1305-102">\<peerAuthentication > öğesi</span><span class="sxs-lookup"><span data-stu-id="f1305-102">\<peerAuthentication> Element</span></span>
<span data-ttu-id="f1305-103">Eşler arası istemcilerin kimlik doğrulama seçeneklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="f1305-103">Specifies authentication options for peer-to-peer clients.</span></span>  
  
 <span data-ttu-id="f1305-104">Eşler arası programlama hakkında daha fazla bilgi için bkz. [eşler arası ağ](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).</span><span class="sxs-lookup"><span data-stu-id="f1305-104">For more information about peer-to-peer programming, see [Peer-to-Peer Networking](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).</span></span>  
  
 <span data-ttu-id="f1305-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="f1305-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="f1305-106">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="f1305-106">\<behaviors></span></span>  
<span data-ttu-id="f1305-107">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="f1305-107">\<endpointBehaviors></span></span>  
<span data-ttu-id="f1305-108">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="f1305-108">\<behavior></span></span>  
<span data-ttu-id="f1305-109">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="f1305-109">\<clientCredentials></span></span>  
<span data-ttu-id="f1305-110">\<Eş ></span><span class="sxs-lookup"><span data-stu-id="f1305-110">\<peer></span></span>  
<span data-ttu-id="f1305-111">\<peerAuthentication ></span><span class="sxs-lookup"><span data-stu-id="f1305-111">\<PeerAuthentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1305-112">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f1305-112">Syntax</span></span>  
  
```xml  
<peerAuthentication customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"
                    certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"
                    revocationMode="NoCheck/Online/Offline"
                    trustedStoreLocation="CurrentUser/LocalMachine" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f1305-113">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="f1305-113">Attributes and Elements</span></span>  
 <span data-ttu-id="f1305-114">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f1305-114">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f1305-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f1305-115">Attributes</span></span>  
  
|<span data-ttu-id="f1305-116">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="f1305-116">Attribute</span></span>|<span data-ttu-id="f1305-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f1305-117">Description</span></span>|  
|---------------|-----------------|  
|`customCertificateValidatorType`|<span data-ttu-id="f1305-118">İsteğe bağlı dize.</span><span class="sxs-lookup"><span data-stu-id="f1305-118">Optional string.</span></span> <span data-ttu-id="f1305-119">Tür ve özel bir tür doğrulamak için kullanılan bir derleme.</span><span class="sxs-lookup"><span data-stu-id="f1305-119">A type and assembly used to validate a custom type.</span></span> <span data-ttu-id="f1305-120">Bu öznitelik olduğunda ayarlanmalıdır `certificateValidationMode` ayarlanır `Custom`.</span><span class="sxs-lookup"><span data-stu-id="f1305-120">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span>|  
|`certifcateValidationMode`|<span data-ttu-id="f1305-121">İsteğe bağlı sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="f1305-121">Optional enumeration.</span></span> <span data-ttu-id="f1305-122">Kimlik bilgilerini doğrulamak için kullanılan üç moddan birini belirtir.</span><span class="sxs-lookup"><span data-stu-id="f1305-122">Specifies one of three modes used to validate credentials.</span></span> <span data-ttu-id="f1305-123">Varsa kümesine `Custom`, ardından bir `customCertificateValidator` de sağlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f1305-123">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span> <span data-ttu-id="f1305-124">Varsayılan, `ChainTrust` değeridir.</span><span class="sxs-lookup"><span data-stu-id="f1305-124">The default is `ChainTrust`.</span></span>|  
|`revocationMode`|<span data-ttu-id="f1305-125">İsteğe bağlı sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="f1305-125">Optional enumeration.</span></span> <span data-ttu-id="f1305-126">İptal edilen sertifikalar listelerini (CRL) denetlemek için kullanılan modlardan biri.</span><span class="sxs-lookup"><span data-stu-id="f1305-126">One of the modes used to check for a revoked certificate lists (CRL).</span></span> <span data-ttu-id="f1305-127">Varsayılan, `Online` değeridir.</span><span class="sxs-lookup"><span data-stu-id="f1305-127">The default is `Online`.</span></span>|  
|`trustedStoreLocation`|<span data-ttu-id="f1305-128">İsteğe bağlı sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="f1305-128">Optional enumeration.</span></span> <span data-ttu-id="f1305-129">İki sistem depolama konumlarından biri: `LocalMachine` veya `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="f1305-129">One of the two system store locations: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="f1305-130">Bir hizmet sertifikası istemciye anlaşıldığında, bu değer kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f1305-130">This value is used when a service certificate is negotiated to the client.</span></span> <span data-ttu-id="f1305-131">Doğrulama işlemi gerçekleştirildiğinde karşı **güvenilir kişiler** depolamak belirtilen depolama konumu.</span><span class="sxs-lookup"><span data-stu-id="f1305-131">Validation is performed against the **Trusted People** store in the specified store location.</span></span> <span data-ttu-id="f1305-132">Varsayılan, `CurrentUser` değeridir.</span><span class="sxs-lookup"><span data-stu-id="f1305-132">The default is `CurrentUser`.</span></span>|  
  
## <a name="customcertificatevalidatortype-attribute"></a><span data-ttu-id="f1305-133">customCertificateValidatorType özniteliği</span><span class="sxs-lookup"><span data-stu-id="f1305-133">customCertificateValidatorType Attribute</span></span>  
  
|<span data-ttu-id="f1305-134">Değer</span><span class="sxs-lookup"><span data-stu-id="f1305-134">Value</span></span>|<span data-ttu-id="f1305-135">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f1305-135">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="f1305-136">Dize</span><span class="sxs-lookup"><span data-stu-id="f1305-136">String</span></span>|<span data-ttu-id="f1305-137">Tür adı ve derleme ve diğer veri türünü bulmak için kullanılan belirtir.</span><span class="sxs-lookup"><span data-stu-id="f1305-137">Specifies the type name and assembly and other data used to find the type.</span></span> <span data-ttu-id="f1305-138">En az bir ad ve tür adı gereklidir.</span><span class="sxs-lookup"><span data-stu-id="f1305-138">At minimum, a namespace and type name are required.</span></span> <span data-ttu-id="f1305-139">İsteğe bağlı bilgileri içerir: derleme adı, sürüm numarasını, kültürü ve ortak anahtar belirteci.</span><span class="sxs-lookup"><span data-stu-id="f1305-139">Optional information includes: assembly name, version number, culture, and public key token.</span></span>|  
  
## <a name="certificatevalidationmode-attribute"></a><span data-ttu-id="f1305-140">Certificatevalidationmode'u özniteliği</span><span class="sxs-lookup"><span data-stu-id="f1305-140">certificateValidationMode Attribute</span></span>  
  
|<span data-ttu-id="f1305-141">Değer</span><span class="sxs-lookup"><span data-stu-id="f1305-141">Value</span></span>|<span data-ttu-id="f1305-142">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f1305-142">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="f1305-143">Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="f1305-143">Enumeration</span></span>|<span data-ttu-id="f1305-144">Aşağıdaki değerlerden biri: `None`, `PeerTrust`, `ChainTrust`, `PeerOrChainTrust`, `Custom`.</span><span class="sxs-lookup"><span data-stu-id="f1305-144">One of the following values: `None`, `PeerTrust`, `ChainTrust`, `PeerOrChainTrust`, `Custom`.</span></span> <span data-ttu-id="f1305-145">Varsayılan, `ChainTrust` değeridir.</span><span class="sxs-lookup"><span data-stu-id="f1305-145">The default is `ChainTrust`.</span></span><br /><br /> <span data-ttu-id="f1305-146">Daha fazla bilgi için [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="f1305-146">For more information, see [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="revocationmode-attribute"></a><span data-ttu-id="f1305-147">revocationMode özniteliği</span><span class="sxs-lookup"><span data-stu-id="f1305-147">revocationMode Attribute</span></span>  
  
|<span data-ttu-id="f1305-148">Değer</span><span class="sxs-lookup"><span data-stu-id="f1305-148">Value</span></span>|<span data-ttu-id="f1305-149">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f1305-149">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="f1305-150">Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="f1305-150">Enumeration</span></span>|<span data-ttu-id="f1305-151">Aşağıdaki değerlerden biri: `NoCheck`, `Online`, `Offline`.</span><span class="sxs-lookup"><span data-stu-id="f1305-151">One of the following values: `NoCheck`, `Online`, `Offline`.</span></span> <span data-ttu-id="f1305-152">Varsayılan, `Online` değeridir.</span><span class="sxs-lookup"><span data-stu-id="f1305-152">The default is `Online`.</span></span><br /><br /> <span data-ttu-id="f1305-153">Daha fazla bilgi için [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="f1305-153">For more information, see [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="trustedstorelocation-attribute"></a><span data-ttu-id="f1305-154">trustedStoreLocation özniteliği</span><span class="sxs-lookup"><span data-stu-id="f1305-154">trustedStoreLocation Attribute</span></span>  
  
|<span data-ttu-id="f1305-155">Değer</span><span class="sxs-lookup"><span data-stu-id="f1305-155">Value</span></span>|<span data-ttu-id="f1305-156">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f1305-156">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="f1305-157">Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="f1305-157">Enumeration</span></span>|<span data-ttu-id="f1305-158">Aşağıdaki değerlerden biri: `LocalMachine` veya `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="f1305-158">One of the following values: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="f1305-159">Varsayılan, `CurrentUser` değeridir.</span><span class="sxs-lookup"><span data-stu-id="f1305-159">The default is `CurrentUser`.</span></span> <span data-ttu-id="f1305-160">İstemci uygulama bir sistem hesabı altında çalıştığından sonra sertifika genellikle altında olduğu `LocalMachine`.</span><span class="sxs-lookup"><span data-stu-id="f1305-160">If the client application is running under a system account then the certificate is typically under `LocalMachine`.</span></span> <span data-ttu-id="f1305-161">İstemci uygulama bir kullanıcı hesabı altında çalıştığından sonra sertifika genellikle kullanımda `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="f1305-161">If the client application is running under a user account then the certificate is typically in `CurrentUser`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f1305-162">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="f1305-162">Child Elements</span></span>  
 <span data-ttu-id="f1305-163">Yok.</span><span class="sxs-lookup"><span data-stu-id="f1305-163">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f1305-164">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="f1305-164">Parent Elements</span></span>  
  
|<span data-ttu-id="f1305-165">Öğe</span><span class="sxs-lookup"><span data-stu-id="f1305-165">Element</span></span>|<span data-ttu-id="f1305-166">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f1305-166">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f1305-167">\<Eş ></span><span class="sxs-lookup"><span data-stu-id="f1305-167">\<peer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-clientcredentials-element.md)|<span data-ttu-id="f1305-168">Bir eş hizmeti istemcisi kimlik doğrulaması için kullanılan bir kimlik bilgisini belirtir.</span><span class="sxs-lookup"><span data-stu-id="f1305-168">Specifies a credential used for authenticating the client to a peer service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f1305-169">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f1305-169">Remarks</span></span>  
 <span data-ttu-id="f1305-170">`<authentication>` Karşılık gelen öğe <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="f1305-170">The `<authentication>` element corresponds to the <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication> class.</span></span> <span data-ttu-id="f1305-171">Bu öğe kafes komşu komşu kimlik doğrulaması sırasında çağrılan bir doğrulayıcı belirtir.</span><span class="sxs-lookup"><span data-stu-id="f1305-171">This element specifies a validator, which is invoked during neighbor-to-neighbor authentication in the mesh.</span></span> <span data-ttu-id="f1305-172">Yeni bir eş komşu bağlantı kurmaya çalıştığında, kendi kimlik bilgisi eşe geçirir.</span><span class="sxs-lookup"><span data-stu-id="f1305-172">When a new peer tries to establish a neighbor connection, it passes its own credential to the responding peer.</span></span> <span data-ttu-id="f1305-173">Yanıtlayıcı Doğrulayıcı uzak taraf kimlik doğrulamak için çağrılır.</span><span class="sxs-lookup"><span data-stu-id="f1305-173">The validator of the responder is invoked to verify the credential of the remote party.</span></span> <span data-ttu-id="f1305-174">Ağ içinde bir eş bağlantı kurulsa hem eşleri karşılıklı kimlik doğrulaması, her iki ucunda anlamı doğrulayıcıları çağrılır.</span><span class="sxs-lookup"><span data-stu-id="f1305-174">Whenever a peer connection is established in the mesh, both peers are mutually authenticated, meaning validators on both ends are invoked.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f1305-175">Örnek</span><span class="sxs-lookup"><span data-stu-id="f1305-175">Example</span></span>  
 <span data-ttu-id="f1305-176">Aşağıdaki kod sertifika doğrulama modunu ayarlar `PeerOrChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="f1305-176">The following code sets the certificate validation mode to `PeerOrChainTrust`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f1305-177">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f1305-177">See also</span></span>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>
- <xref:System.ServiceModel.Security.PeerCredential.PeerAuthentication%2A>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement.PeerAuthentication%2A>
- <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>
- [<span data-ttu-id="f1305-178">Sertifikalarla Çalışma</span><span class="sxs-lookup"><span data-stu-id="f1305-178">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="f1305-179">Eşler Arası Ağ</span><span class="sxs-lookup"><span data-stu-id="f1305-179">Peer-to-Peer Networking</span></span>](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)
- <span data-ttu-id="f1305-180">[Eş kanal ileti kimlik doğrulaması](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="f1305-180">[Peer Channel Message Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="f1305-181">[Eş kanal özel kimlik doğrulama](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="f1305-181">[Peer Channel Custom Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="f1305-182">Eş Kanalı Uygulamalarını Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="f1305-182">Securing Peer Channel Applications</span></span>](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)
