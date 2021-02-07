---
description: 'Daha fazla bilgi edinin: <peerAuthentication> öğesi'
title: <peerAuthentication> Öğesi
ms.date: 03/30/2017
ms.assetid: 09a8a9ff-e395-42f6-8ceb-9d44bdc1cbe1
ms.openlocfilehash: 887b65a4a2a7da9d545bc25636be0ea6c646f6fb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99683729"
---
# <a name="peerauthentication-element"></a><span data-ttu-id="3d07b-103">\<peerAuthentication> Öğesi</span><span class="sxs-lookup"><span data-stu-id="3d07b-103">\<peerAuthentication> Element</span></span>

<span data-ttu-id="3d07b-104">Eşler arası istemciler için kimlik doğrulama seçeneklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="3d07b-104">Specifies authentication options for peer-to-peer clients.</span></span>  
  
 <span data-ttu-id="3d07b-105">Eşler arası programlama hakkında daha fazla bilgi için bkz. eşler [arası ağ iletişimi](../../../wcf/feature-details/peer-to-peer-networking.md).</span><span class="sxs-lookup"><span data-stu-id="3d07b-105">For more information about peer-to-peer programming, see [Peer-to-Peer Networking](../../../wcf/feature-details/peer-to-peer-networking.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<peer>**](peer-of-clientcredentials-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<peerAuthentication>**  
  
## <a name="syntax"></a><span data-ttu-id="3d07b-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="3d07b-106">Syntax</span></span>  
  
```xml  
<peerAuthentication customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"
                    certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"
                    revocationMode="NoCheck/Online/Offline"
                    trustedStoreLocation="CurrentUser/LocalMachine" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3d07b-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="3d07b-107">Attributes and Elements</span></span>  

 <span data-ttu-id="3d07b-108">Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır</span><span class="sxs-lookup"><span data-stu-id="3d07b-108">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3d07b-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="3d07b-109">Attributes</span></span>  
  
|<span data-ttu-id="3d07b-110">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="3d07b-110">Attribute</span></span>|<span data-ttu-id="3d07b-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3d07b-111">Description</span></span>|  
|---------------|-----------------|  
|`customCertificateValidatorType`|<span data-ttu-id="3d07b-112">İsteğe bağlı dize.</span><span class="sxs-lookup"><span data-stu-id="3d07b-112">Optional string.</span></span> <span data-ttu-id="3d07b-113">Özel bir türü doğrulamak için kullanılan tür ve derleme.</span><span class="sxs-lookup"><span data-stu-id="3d07b-113">A type and assembly used to validate a custom type.</span></span> <span data-ttu-id="3d07b-114">Bu öznitelik `certificateValidationMode` , olarak ayarlandığında ayarlanmalıdır `Custom` .</span><span class="sxs-lookup"><span data-stu-id="3d07b-114">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span>|  
|`certificateValidationMode`|<span data-ttu-id="3d07b-115">İsteğe bağlı sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="3d07b-115">Optional enumeration.</span></span> <span data-ttu-id="3d07b-116">Kimlik bilgilerini doğrulamak için kullanılan üç moddan birini belirtir.</span><span class="sxs-lookup"><span data-stu-id="3d07b-116">Specifies one of three modes used to validate credentials.</span></span> <span data-ttu-id="3d07b-117">Olarak ayarlanırsa `Custom` , bir `customCertificateValidator` de sağlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3d07b-117">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span> <span data-ttu-id="3d07b-118">Varsayılan değer: `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="3d07b-118">The default is `ChainTrust`.</span></span>|  
|`revocationMode`|<span data-ttu-id="3d07b-119">İsteğe bağlı sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="3d07b-119">Optional enumeration.</span></span> <span data-ttu-id="3d07b-120">İptal edilen bir sertifika listesini (CRL) denetlemek için kullanılan modlardan biri.</span><span class="sxs-lookup"><span data-stu-id="3d07b-120">One of the modes used to check for a revoked certificate lists (CRL).</span></span> <span data-ttu-id="3d07b-121">Varsayılan değer: `Online`.</span><span class="sxs-lookup"><span data-stu-id="3d07b-121">The default is `Online`.</span></span>|  
|`trustedStoreLocation`|<span data-ttu-id="3d07b-122">İsteğe bağlı sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="3d07b-122">Optional enumeration.</span></span> <span data-ttu-id="3d07b-123">İki sistem depolama konumlarından biri: `LocalMachine` veya `CurrentUser` .</span><span class="sxs-lookup"><span data-stu-id="3d07b-123">One of the two system store locations: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="3d07b-124">Bu değer, bir hizmet sertifikası istemciye anlaşılırken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3d07b-124">This value is used when a service certificate is negotiated to the client.</span></span> <span data-ttu-id="3d07b-125">Doğrulama, belirtilen depo konumundaki **güvenilir kişiler** deposuna göre gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="3d07b-125">Validation is performed against the **Trusted People** store in the specified store location.</span></span> <span data-ttu-id="3d07b-126">Varsayılan değer: `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="3d07b-126">The default is `CurrentUser`.</span></span>|  
  
## <a name="customcertificatevalidatortype-attribute"></a><span data-ttu-id="3d07b-127">Customcercertificate Atevalidatortype özniteliği</span><span class="sxs-lookup"><span data-stu-id="3d07b-127">customCertificateValidatorType Attribute</span></span>  
  
|<span data-ttu-id="3d07b-128">Değer</span><span class="sxs-lookup"><span data-stu-id="3d07b-128">Value</span></span>|<span data-ttu-id="3d07b-129">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3d07b-129">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="3d07b-130">Dize</span><span class="sxs-lookup"><span data-stu-id="3d07b-130">String</span></span>|<span data-ttu-id="3d07b-131">Türü bulmak için kullanılan tür adını ve derlemeyi ve diğer verileri belirtir.</span><span class="sxs-lookup"><span data-stu-id="3d07b-131">Specifies the type name and assembly and other data used to find the type.</span></span> <span data-ttu-id="3d07b-132">En azından, bir ad alanı ve tür adı gereklidir.</span><span class="sxs-lookup"><span data-stu-id="3d07b-132">At minimum, a namespace and type name are required.</span></span> <span data-ttu-id="3d07b-133">İsteğe bağlı bilgiler şunları içerir: derleme adı, sürüm numarası, kültür ve ortak anahtar belirteci.</span><span class="sxs-lookup"><span data-stu-id="3d07b-133">Optional information includes: assembly name, version number, culture, and public key token.</span></span>|  
  
## <a name="certificatevalidationmode-attribute"></a><span data-ttu-id="3d07b-134">certificateValidationMode özniteliği</span><span class="sxs-lookup"><span data-stu-id="3d07b-134">certificateValidationMode Attribute</span></span>  
  
|<span data-ttu-id="3d07b-135">Değer</span><span class="sxs-lookup"><span data-stu-id="3d07b-135">Value</span></span>|<span data-ttu-id="3d07b-136">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3d07b-136">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="3d07b-137">Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="3d07b-137">Enumeration</span></span>|<span data-ttu-id="3d07b-138">Aşağıdaki değerlerden biri: `None` ,,, `PeerTrust` `ChainTrust` `PeerOrChainTrust` , `Custom` .</span><span class="sxs-lookup"><span data-stu-id="3d07b-138">One of the following values: `None`, `PeerTrust`, `ChainTrust`, `PeerOrChainTrust`, `Custom`.</span></span> <span data-ttu-id="3d07b-139">Varsayılan değer: `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="3d07b-139">The default is `ChainTrust`.</span></span><br /><br /> <span data-ttu-id="3d07b-140">Daha fazla bilgi için bkz. [sertifikalarla çalışma](../../../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="3d07b-140">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="revocationmode-attribute"></a><span data-ttu-id="3d07b-141">revocationMode özniteliği</span><span class="sxs-lookup"><span data-stu-id="3d07b-141">revocationMode Attribute</span></span>  
  
|<span data-ttu-id="3d07b-142">Değer</span><span class="sxs-lookup"><span data-stu-id="3d07b-142">Value</span></span>|<span data-ttu-id="3d07b-143">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3d07b-143">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="3d07b-144">Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="3d07b-144">Enumeration</span></span>|<span data-ttu-id="3d07b-145">Aşağıdaki değerlerden biri: `NoCheck` , `Online` , `Offline` .</span><span class="sxs-lookup"><span data-stu-id="3d07b-145">One of the following values: `NoCheck`, `Online`, `Offline`.</span></span> <span data-ttu-id="3d07b-146">Varsayılan değer: `Online`.</span><span class="sxs-lookup"><span data-stu-id="3d07b-146">The default is `Online`.</span></span><br /><br /> <span data-ttu-id="3d07b-147">Daha fazla bilgi için bkz. [sertifikalarla çalışma](../../../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="3d07b-147">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="trustedstorelocation-attribute"></a><span data-ttu-id="3d07b-148">trustedStoreLocation özniteliği</span><span class="sxs-lookup"><span data-stu-id="3d07b-148">trustedStoreLocation Attribute</span></span>  
  
|<span data-ttu-id="3d07b-149">Değer</span><span class="sxs-lookup"><span data-stu-id="3d07b-149">Value</span></span>|<span data-ttu-id="3d07b-150">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3d07b-150">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="3d07b-151">Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="3d07b-151">Enumeration</span></span>|<span data-ttu-id="3d07b-152">Şu değerlerden biri: `LocalMachine` veya `CurrentUser` .</span><span class="sxs-lookup"><span data-stu-id="3d07b-152">One of the following values: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="3d07b-153">Varsayılan değer: `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="3d07b-153">The default is `CurrentUser`.</span></span> <span data-ttu-id="3d07b-154">İstemci uygulaması bir sistem hesabı altında çalışıyorsa, sertifika genellikle altında olur `LocalMachine` .</span><span class="sxs-lookup"><span data-stu-id="3d07b-154">If the client application is running under a system account then the certificate is typically under `LocalMachine`.</span></span> <span data-ttu-id="3d07b-155">İstemci uygulaması bir kullanıcı hesabı altında çalışıyorsa, sertifika genellikle içinde olur `CurrentUser` .</span><span class="sxs-lookup"><span data-stu-id="3d07b-155">If the client application is running under a user account then the certificate is typically in `CurrentUser`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3d07b-156">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="3d07b-156">Child Elements</span></span>  

 <span data-ttu-id="3d07b-157">Yok.</span><span class="sxs-lookup"><span data-stu-id="3d07b-157">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3d07b-158">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="3d07b-158">Parent Elements</span></span>  
  
|<span data-ttu-id="3d07b-159">Öğe</span><span class="sxs-lookup"><span data-stu-id="3d07b-159">Element</span></span>|<span data-ttu-id="3d07b-160">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3d07b-160">Description</span></span>|  
|-------------|-----------------|  
|[\<peer>](peer-of-clientcredentials-element.md)|<span data-ttu-id="3d07b-161">İstemcinin kimliğini bir eş hizmette doğrulamak için kullanılan kimlik bilgisini belirtir.</span><span class="sxs-lookup"><span data-stu-id="3d07b-161">Specifies a credential used for authenticating the client to a peer service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3d07b-162">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3d07b-162">Remarks</span></span>  

 <span data-ttu-id="3d07b-163">`<authentication>`Öğesi sınıfına karşılık gelir <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication> .</span><span class="sxs-lookup"><span data-stu-id="3d07b-163">The `<authentication>` element corresponds to the <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication> class.</span></span> <span data-ttu-id="3d07b-164">Bu öğe, ağ içinde komşu-komşu kimlik doğrulaması sırasında çağrılan bir doğrulayıcısı belirtir.</span><span class="sxs-lookup"><span data-stu-id="3d07b-164">This element specifies a validator, which is invoked during neighbor-to-neighbor authentication in the mesh.</span></span> <span data-ttu-id="3d07b-165">Yeni bir eş bir komşu bağlantı kurmaya çalıştığında, kendi kimlik bilgilerini yanıt veren eşe geçirir.</span><span class="sxs-lookup"><span data-stu-id="3d07b-165">When a new peer tries to establish a neighbor connection, it passes its own credential to the responding peer.</span></span> <span data-ttu-id="3d07b-166">Yanıtlayanın Doğrulayıcısı, uzak tarafın kimlik bilgilerini doğrulamak için çağrılır.</span><span class="sxs-lookup"><span data-stu-id="3d07b-166">The validator of the responder is invoked to verify the credential of the remote party.</span></span> <span data-ttu-id="3d07b-167">Kafeste bir eş bağlantı oluşturulduğunda her iki eş de karşılıklı olarak doğrulanır, her iki uçta da doğrulayıcılar çağrılır.</span><span class="sxs-lookup"><span data-stu-id="3d07b-167">Whenever a peer connection is established in the mesh, both peers are mutually authenticated, meaning validators on both ends are invoked.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3d07b-168">Örnek</span><span class="sxs-lookup"><span data-stu-id="3d07b-168">Example</span></span>  

 <span data-ttu-id="3d07b-169">Aşağıdaki kod, sertifika doğrulama modunu olarak ayarlar `PeerOrChainTrust` .</span><span class="sxs-lookup"><span data-stu-id="3d07b-169">The following code sets the certificate validation mode to `PeerOrChainTrust`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3d07b-170">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3d07b-170">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>
- <xref:System.ServiceModel.Security.PeerCredential.PeerAuthentication%2A>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement.PeerAuthentication%2A>
- <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>
- [<span data-ttu-id="3d07b-171">Sertifikalarla Çalışma</span><span class="sxs-lookup"><span data-stu-id="3d07b-171">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="3d07b-172">Eşler Arası Ağ</span><span class="sxs-lookup"><span data-stu-id="3d07b-172">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
- <span data-ttu-id="3d07b-173">[Eş kanal Iletisi kimlik doğrulaması](/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="3d07b-173">[Peer Channel Message Authentication](/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="3d07b-174">[Eş kanal özel kimlik doğrulaması](/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="3d07b-174">[Peer Channel Custom Authentication](/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="3d07b-175">Eş Kanalı Uygulamalarını Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="3d07b-175">Securing Peer Channel Applications</span></span>](../../../wcf/feature-details/securing-peer-channel-applications.md)
