---
title: <peerAuthentication> Öğesi
ms.date: 03/30/2017
ms.assetid: 09a8a9ff-e395-42f6-8ceb-9d44bdc1cbe1
ms.openlocfilehash: 4c29c84a2cc56a890c8273e410ba31b5f3900732
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400091"
---
# <a name="peerauthentication-element"></a><span data-ttu-id="3a742-102">\<peerAuthentication > öğesi</span><span class="sxs-lookup"><span data-stu-id="3a742-102">\<peerAuthentication> Element</span></span>
<span data-ttu-id="3a742-103">Eşler arası istemciler için kimlik doğrulama seçeneklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="3a742-103">Specifies authentication options for peer-to-peer clients.</span></span>  
  
 <span data-ttu-id="3a742-104">Eşler arası programlama hakkında daha fazla bilgi için bkz. eşler [arası ağ iletişimi](../../../wcf/feature-details/peer-to-peer-networking.md).</span><span class="sxs-lookup"><span data-stu-id="3a742-104">For more information about peer-to-peer programming, see [Peer-to-Peer Networking](../../../wcf/feature-details/peer-to-peer-networking.md).</span></span>  
  
<span data-ttu-id="3a742-105">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="3a742-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="3a742-106">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="3a742-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="3a742-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranışlar >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="3a742-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="3a742-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Endpointdavranışlar >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="3a742-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="3a742-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranış >** ](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="3a742-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="3a742-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<clientCredentials >** ](clientcredentials.md)</span><span class="sxs-lookup"><span data-stu-id="3a742-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)</span></span>\
<span data-ttu-id="3a742-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<eş >** ](peer-of-clientcredentials-element.md)</span><span class="sxs-lookup"><span data-stu-id="3a742-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<peer>**](peer-of-clientcredentials-element.md)</span></span>\
<span data-ttu-id="3a742-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<peerAuthentication >**</span><span class="sxs-lookup"><span data-stu-id="3a742-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<peerAuthentication>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a742-113">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3a742-113">Syntax</span></span>  
  
```xml  
<peerAuthentication customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"
                    certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"
                    revocationMode="NoCheck/Online/Offline"
                    trustedStoreLocation="CurrentUser/LocalMachine" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3a742-114">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="3a742-114">Attributes and Elements</span></span>  
 <span data-ttu-id="3a742-115">Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır</span><span class="sxs-lookup"><span data-stu-id="3a742-115">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3a742-116">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="3a742-116">Attributes</span></span>  
  
|<span data-ttu-id="3a742-117">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="3a742-117">Attribute</span></span>|<span data-ttu-id="3a742-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3a742-118">Description</span></span>|  
|---------------|-----------------|  
|`customCertificateValidatorType`|<span data-ttu-id="3a742-119">İsteğe bağlı dize.</span><span class="sxs-lookup"><span data-stu-id="3a742-119">Optional string.</span></span> <span data-ttu-id="3a742-120">Özel bir türü doğrulamak için kullanılan tür ve derleme.</span><span class="sxs-lookup"><span data-stu-id="3a742-120">A type and assembly used to validate a custom type.</span></span> <span data-ttu-id="3a742-121">Bu öznitelik `certificateValidationMode` , olarak `Custom`ayarlandığında ayarlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3a742-121">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span>|  
|`certificateValidationMode`|<span data-ttu-id="3a742-122">İsteğe bağlı sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="3a742-122">Optional enumeration.</span></span> <span data-ttu-id="3a742-123">Kimlik bilgilerini doğrulamak için kullanılan üç moddan birini belirtir.</span><span class="sxs-lookup"><span data-stu-id="3a742-123">Specifies one of three modes used to validate credentials.</span></span> <span data-ttu-id="3a742-124">Olarak `Custom`ayarlanırsa, bir `customCertificateValidator` de sağlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3a742-124">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span> <span data-ttu-id="3a742-125">Varsayılan, `ChainTrust` değeridir.</span><span class="sxs-lookup"><span data-stu-id="3a742-125">The default is `ChainTrust`.</span></span>|  
|`revocationMode`|<span data-ttu-id="3a742-126">İsteğe bağlı sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="3a742-126">Optional enumeration.</span></span> <span data-ttu-id="3a742-127">İptal edilen bir sertifika listesini (CRL) denetlemek için kullanılan modlardan biri.</span><span class="sxs-lookup"><span data-stu-id="3a742-127">One of the modes used to check for a revoked certificate lists (CRL).</span></span> <span data-ttu-id="3a742-128">Varsayılan, `Online` değeridir.</span><span class="sxs-lookup"><span data-stu-id="3a742-128">The default is `Online`.</span></span>|  
|`trustedStoreLocation`|<span data-ttu-id="3a742-129">İsteğe bağlı sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="3a742-129">Optional enumeration.</span></span> <span data-ttu-id="3a742-130">İki sistem depolama konumlarından biri: `LocalMachine` veya. `CurrentUser`</span><span class="sxs-lookup"><span data-stu-id="3a742-130">One of the two system store locations: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="3a742-131">Bu değer, bir hizmet sertifikası istemciye anlaşılırken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3a742-131">This value is used when a service certificate is negotiated to the client.</span></span> <span data-ttu-id="3a742-132">Doğrulama, belirtilen depo konumundaki **güvenilir kişiler** deposuna göre gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="3a742-132">Validation is performed against the **Trusted People** store in the specified store location.</span></span> <span data-ttu-id="3a742-133">Varsayılan, `CurrentUser` değeridir.</span><span class="sxs-lookup"><span data-stu-id="3a742-133">The default is `CurrentUser`.</span></span>|  
  
## <a name="customcertificatevalidatortype-attribute"></a><span data-ttu-id="3a742-134">Customcercertificate Atevalidatortype özniteliği</span><span class="sxs-lookup"><span data-stu-id="3a742-134">customCertificateValidatorType Attribute</span></span>  
  
|<span data-ttu-id="3a742-135">Değer</span><span class="sxs-lookup"><span data-stu-id="3a742-135">Value</span></span>|<span data-ttu-id="3a742-136">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3a742-136">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="3a742-137">Dize</span><span class="sxs-lookup"><span data-stu-id="3a742-137">String</span></span>|<span data-ttu-id="3a742-138">Türü bulmak için kullanılan tür adını ve derlemeyi ve diğer verileri belirtir.</span><span class="sxs-lookup"><span data-stu-id="3a742-138">Specifies the type name and assembly and other data used to find the type.</span></span> <span data-ttu-id="3a742-139">En azından, bir ad alanı ve tür adı gereklidir.</span><span class="sxs-lookup"><span data-stu-id="3a742-139">At minimum, a namespace and type name are required.</span></span> <span data-ttu-id="3a742-140">İsteğe bağlı bilgiler şunları içerir: derleme adı, sürüm numarası, kültür ve ortak anahtar belirteci.</span><span class="sxs-lookup"><span data-stu-id="3a742-140">Optional information includes: assembly name, version number, culture, and public key token.</span></span>|  
  
## <a name="certificatevalidationmode-attribute"></a><span data-ttu-id="3a742-141">certificateValidationMode özniteliği</span><span class="sxs-lookup"><span data-stu-id="3a742-141">certificateValidationMode Attribute</span></span>  
  
|<span data-ttu-id="3a742-142">Değer</span><span class="sxs-lookup"><span data-stu-id="3a742-142">Value</span></span>|<span data-ttu-id="3a742-143">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3a742-143">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="3a742-144">Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="3a742-144">Enumeration</span></span>|<span data-ttu-id="3a742-145">Aşağıdaki değerlerden biri: `None`, `PeerTrust`, `ChainTrust` `PeerOrChainTrust`, ,`Custom`.</span><span class="sxs-lookup"><span data-stu-id="3a742-145">One of the following values: `None`, `PeerTrust`, `ChainTrust`, `PeerOrChainTrust`, `Custom`.</span></span> <span data-ttu-id="3a742-146">Varsayılan, `ChainTrust` değeridir.</span><span class="sxs-lookup"><span data-stu-id="3a742-146">The default is `ChainTrust`.</span></span><br /><br /> <span data-ttu-id="3a742-147">Daha fazla bilgi için bkz. [sertifikalarla çalışma](../../../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="3a742-147">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="revocationmode-attribute"></a><span data-ttu-id="3a742-148">revocationMode özniteliği</span><span class="sxs-lookup"><span data-stu-id="3a742-148">revocationMode Attribute</span></span>  
  
|<span data-ttu-id="3a742-149">Değer</span><span class="sxs-lookup"><span data-stu-id="3a742-149">Value</span></span>|<span data-ttu-id="3a742-150">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3a742-150">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="3a742-151">Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="3a742-151">Enumeration</span></span>|<span data-ttu-id="3a742-152">Aşağıdaki değerlerden biri: `NoCheck`, `Online`, `Offline`.</span><span class="sxs-lookup"><span data-stu-id="3a742-152">One of the following values: `NoCheck`, `Online`, `Offline`.</span></span> <span data-ttu-id="3a742-153">Varsayılan, `Online` değeridir.</span><span class="sxs-lookup"><span data-stu-id="3a742-153">The default is `Online`.</span></span><br /><br /> <span data-ttu-id="3a742-154">Daha fazla bilgi için bkz. [sertifikalarla çalışma](../../../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="3a742-154">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="trustedstorelocation-attribute"></a><span data-ttu-id="3a742-155">trustedStoreLocation özniteliği</span><span class="sxs-lookup"><span data-stu-id="3a742-155">trustedStoreLocation Attribute</span></span>  
  
|<span data-ttu-id="3a742-156">Değer</span><span class="sxs-lookup"><span data-stu-id="3a742-156">Value</span></span>|<span data-ttu-id="3a742-157">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3a742-157">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="3a742-158">Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="3a742-158">Enumeration</span></span>|<span data-ttu-id="3a742-159">Şu değerlerden biri: `LocalMachine` veya. `CurrentUser`</span><span class="sxs-lookup"><span data-stu-id="3a742-159">One of the following values: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="3a742-160">Varsayılan, `CurrentUser` değeridir.</span><span class="sxs-lookup"><span data-stu-id="3a742-160">The default is `CurrentUser`.</span></span> <span data-ttu-id="3a742-161">İstemci uygulaması bir sistem hesabı altında çalışıyorsa, sertifika genellikle altında `LocalMachine`olur.</span><span class="sxs-lookup"><span data-stu-id="3a742-161">If the client application is running under a system account then the certificate is typically under `LocalMachine`.</span></span> <span data-ttu-id="3a742-162">İstemci uygulaması bir kullanıcı hesabı altında çalışıyorsa, sertifika genellikle içinde `CurrentUser`olur.</span><span class="sxs-lookup"><span data-stu-id="3a742-162">If the client application is running under a user account then the certificate is typically in `CurrentUser`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3a742-163">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="3a742-163">Child Elements</span></span>  
 <span data-ttu-id="3a742-164">Yok.</span><span class="sxs-lookup"><span data-stu-id="3a742-164">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3a742-165">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="3a742-165">Parent Elements</span></span>  
  
|<span data-ttu-id="3a742-166">Öğe</span><span class="sxs-lookup"><span data-stu-id="3a742-166">Element</span></span>|<span data-ttu-id="3a742-167">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3a742-167">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3a742-168">\<eş ></span><span class="sxs-lookup"><span data-stu-id="3a742-168">\<peer></span></span>](peer-of-clientcredentials-element.md)|<span data-ttu-id="3a742-169">İstemcinin kimliğini bir eş hizmette doğrulamak için kullanılan kimlik bilgisini belirtir.</span><span class="sxs-lookup"><span data-stu-id="3a742-169">Specifies a credential used for authenticating the client to a peer service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3a742-170">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3a742-170">Remarks</span></span>  
 <span data-ttu-id="3a742-171">`<authentication>` Öğesi <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication> sınıfına karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="3a742-171">The `<authentication>` element corresponds to the <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication> class.</span></span> <span data-ttu-id="3a742-172">Bu öğe, ağ içinde komşu-komşu kimlik doğrulaması sırasında çağrılan bir doğrulayıcısı belirtir.</span><span class="sxs-lookup"><span data-stu-id="3a742-172">This element specifies a validator, which is invoked during neighbor-to-neighbor authentication in the mesh.</span></span> <span data-ttu-id="3a742-173">Yeni bir eş bir komşu bağlantı kurmaya çalıştığında, kendi kimlik bilgilerini yanıt veren eşe geçirir.</span><span class="sxs-lookup"><span data-stu-id="3a742-173">When a new peer tries to establish a neighbor connection, it passes its own credential to the responding peer.</span></span> <span data-ttu-id="3a742-174">Yanıtlayanın Doğrulayıcısı, uzak tarafın kimlik bilgilerini doğrulamak için çağrılır.</span><span class="sxs-lookup"><span data-stu-id="3a742-174">The validator of the responder is invoked to verify the credential of the remote party.</span></span> <span data-ttu-id="3a742-175">Kafeste bir eş bağlantı oluşturulduğunda her iki eş de karşılıklı olarak doğrulanır, her iki uçta da doğrulayıcılar çağrılır.</span><span class="sxs-lookup"><span data-stu-id="3a742-175">Whenever a peer connection is established in the mesh, both peers are mutually authenticated, meaning validators on both ends are invoked.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3a742-176">Örnek</span><span class="sxs-lookup"><span data-stu-id="3a742-176">Example</span></span>  
 <span data-ttu-id="3a742-177">Aşağıdaki kod, sertifika doğrulama modunu olarak `PeerOrChainTrust`ayarlar.</span><span class="sxs-lookup"><span data-stu-id="3a742-177">The following code sets the certificate validation mode to `PeerOrChainTrust`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3a742-178">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3a742-178">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>
- <xref:System.ServiceModel.Security.PeerCredential.PeerAuthentication%2A>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement.PeerAuthentication%2A>
- <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>
- [<span data-ttu-id="3a742-179">Sertifikalarla Çalışma</span><span class="sxs-lookup"><span data-stu-id="3a742-179">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="3a742-180">Eşler Arası Ağ</span><span class="sxs-lookup"><span data-stu-id="3a742-180">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
- <span data-ttu-id="3a742-181">[Eş kanal Iletisi kimlik doğrulaması](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="3a742-181">[Peer Channel Message Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="3a742-182">[Eş kanal özel kimlik doğrulaması](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="3a742-182">[Peer Channel Custom Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="3a742-183">Eş Kanalı Uygulamalarını Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="3a742-183">Securing Peer Channel Applications</span></span>](../../../wcf/feature-details/securing-peer-channel-applications.md)
