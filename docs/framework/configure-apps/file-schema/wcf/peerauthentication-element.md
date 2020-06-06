---
title: <peerAuthentication> Öğesi
ms.date: 03/30/2017
ms.assetid: 09a8a9ff-e395-42f6-8ceb-9d44bdc1cbe1
ms.openlocfilehash: 4c29c84a2cc56a890c8273e410ba31b5f3900732
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400091"
---
# <a name="peerauthentication-element"></a><span data-ttu-id="2c3cd-102">\<peerAuthentication> Öğesi</span><span class="sxs-lookup"><span data-stu-id="2c3cd-102">\<peerAuthentication> Element</span></span>
<span data-ttu-id="2c3cd-103">Eşler arası istemciler için kimlik doğrulama seçeneklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="2c3cd-103">Specifies authentication options for peer-to-peer clients.</span></span>  
  
 <span data-ttu-id="2c3cd-104">Eşler arası programlama hakkında daha fazla bilgi için bkz. eşler [arası ağ iletişimi](../../../wcf/feature-details/peer-to-peer-networking.md).</span><span class="sxs-lookup"><span data-stu-id="2c3cd-104">For more information about peer-to-peer programming, see [Peer-to-Peer Networking](../../../wcf/feature-details/peer-to-peer-networking.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<peer>**](peer-of-clientcredentials-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<peerAuthentication>**  
  
## <a name="syntax"></a><span data-ttu-id="2c3cd-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2c3cd-105">Syntax</span></span>  
  
```xml  
<peerAuthentication customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"
                    certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"
                    revocationMode="NoCheck/Online/Offline"
                    trustedStoreLocation="CurrentUser/LocalMachine" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2c3cd-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="2c3cd-106">Attributes and Elements</span></span>  
 <span data-ttu-id="2c3cd-107">Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır</span><span class="sxs-lookup"><span data-stu-id="2c3cd-107">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2c3cd-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="2c3cd-108">Attributes</span></span>  
  
|<span data-ttu-id="2c3cd-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="2c3cd-109">Attribute</span></span>|<span data-ttu-id="2c3cd-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2c3cd-110">Description</span></span>|  
|---------------|-----------------|  
|`customCertificateValidatorType`|<span data-ttu-id="2c3cd-111">İsteğe bağlı dize.</span><span class="sxs-lookup"><span data-stu-id="2c3cd-111">Optional string.</span></span> <span data-ttu-id="2c3cd-112">Özel bir türü doğrulamak için kullanılan tür ve derleme.</span><span class="sxs-lookup"><span data-stu-id="2c3cd-112">A type and assembly used to validate a custom type.</span></span> <span data-ttu-id="2c3cd-113">Bu öznitelik `certificateValidationMode` , olarak ayarlandığında ayarlanmalıdır `Custom` .</span><span class="sxs-lookup"><span data-stu-id="2c3cd-113">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span>|  
|`certificateValidationMode`|<span data-ttu-id="2c3cd-114">İsteğe bağlı sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="2c3cd-114">Optional enumeration.</span></span> <span data-ttu-id="2c3cd-115">Kimlik bilgilerini doğrulamak için kullanılan üç moddan birini belirtir.</span><span class="sxs-lookup"><span data-stu-id="2c3cd-115">Specifies one of three modes used to validate credentials.</span></span> <span data-ttu-id="2c3cd-116">Olarak ayarlanırsa `Custom` , bir `customCertificateValidator` de sağlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2c3cd-116">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span> <span data-ttu-id="2c3cd-117">Varsayılan değer: `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="2c3cd-117">The default is `ChainTrust`.</span></span>|  
|`revocationMode`|<span data-ttu-id="2c3cd-118">İsteğe bağlı sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="2c3cd-118">Optional enumeration.</span></span> <span data-ttu-id="2c3cd-119">İptal edilen bir sertifika listesini (CRL) denetlemek için kullanılan modlardan biri.</span><span class="sxs-lookup"><span data-stu-id="2c3cd-119">One of the modes used to check for a revoked certificate lists (CRL).</span></span> <span data-ttu-id="2c3cd-120">Varsayılan değer: `Online`.</span><span class="sxs-lookup"><span data-stu-id="2c3cd-120">The default is `Online`.</span></span>|  
|`trustedStoreLocation`|<span data-ttu-id="2c3cd-121">İsteğe bağlı sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="2c3cd-121">Optional enumeration.</span></span> <span data-ttu-id="2c3cd-122">İki sistem depolama konumlarından biri: `LocalMachine` veya `CurrentUser` .</span><span class="sxs-lookup"><span data-stu-id="2c3cd-122">One of the two system store locations: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="2c3cd-123">Bu değer, bir hizmet sertifikası istemciye anlaşılırken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2c3cd-123">This value is used when a service certificate is negotiated to the client.</span></span> <span data-ttu-id="2c3cd-124">Doğrulama, belirtilen depo konumundaki **güvenilir kişiler** deposuna göre gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="2c3cd-124">Validation is performed against the **Trusted People** store in the specified store location.</span></span> <span data-ttu-id="2c3cd-125">Varsayılan değer: `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="2c3cd-125">The default is `CurrentUser`.</span></span>|  
  
## <a name="customcertificatevalidatortype-attribute"></a><span data-ttu-id="2c3cd-126">Customcercertificate Atevalidatortype özniteliği</span><span class="sxs-lookup"><span data-stu-id="2c3cd-126">customCertificateValidatorType Attribute</span></span>  
  
|<span data-ttu-id="2c3cd-127">Değer</span><span class="sxs-lookup"><span data-stu-id="2c3cd-127">Value</span></span>|<span data-ttu-id="2c3cd-128">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2c3cd-128">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="2c3cd-129">Dize</span><span class="sxs-lookup"><span data-stu-id="2c3cd-129">String</span></span>|<span data-ttu-id="2c3cd-130">Türü bulmak için kullanılan tür adını ve derlemeyi ve diğer verileri belirtir.</span><span class="sxs-lookup"><span data-stu-id="2c3cd-130">Specifies the type name and assembly and other data used to find the type.</span></span> <span data-ttu-id="2c3cd-131">En azından, bir ad alanı ve tür adı gereklidir.</span><span class="sxs-lookup"><span data-stu-id="2c3cd-131">At minimum, a namespace and type name are required.</span></span> <span data-ttu-id="2c3cd-132">İsteğe bağlı bilgiler şunları içerir: derleme adı, sürüm numarası, kültür ve ortak anahtar belirteci.</span><span class="sxs-lookup"><span data-stu-id="2c3cd-132">Optional information includes: assembly name, version number, culture, and public key token.</span></span>|  
  
## <a name="certificatevalidationmode-attribute"></a><span data-ttu-id="2c3cd-133">certificateValidationMode özniteliği</span><span class="sxs-lookup"><span data-stu-id="2c3cd-133">certificateValidationMode Attribute</span></span>  
  
|<span data-ttu-id="2c3cd-134">Değer</span><span class="sxs-lookup"><span data-stu-id="2c3cd-134">Value</span></span>|<span data-ttu-id="2c3cd-135">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2c3cd-135">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="2c3cd-136">Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="2c3cd-136">Enumeration</span></span>|<span data-ttu-id="2c3cd-137">Aşağıdaki değerlerden biri: `None` ,,, `PeerTrust` `ChainTrust` `PeerOrChainTrust` , `Custom` .</span><span class="sxs-lookup"><span data-stu-id="2c3cd-137">One of the following values: `None`, `PeerTrust`, `ChainTrust`, `PeerOrChainTrust`, `Custom`.</span></span> <span data-ttu-id="2c3cd-138">Varsayılan değer: `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="2c3cd-138">The default is `ChainTrust`.</span></span><br /><br /> <span data-ttu-id="2c3cd-139">Daha fazla bilgi için bkz. [sertifikalarla çalışma](../../../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="2c3cd-139">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="revocationmode-attribute"></a><span data-ttu-id="2c3cd-140">revocationMode özniteliği</span><span class="sxs-lookup"><span data-stu-id="2c3cd-140">revocationMode Attribute</span></span>  
  
|<span data-ttu-id="2c3cd-141">Değer</span><span class="sxs-lookup"><span data-stu-id="2c3cd-141">Value</span></span>|<span data-ttu-id="2c3cd-142">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2c3cd-142">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="2c3cd-143">Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="2c3cd-143">Enumeration</span></span>|<span data-ttu-id="2c3cd-144">Aşağıdaki değerlerden biri: `NoCheck` , `Online` , `Offline` .</span><span class="sxs-lookup"><span data-stu-id="2c3cd-144">One of the following values: `NoCheck`, `Online`, `Offline`.</span></span> <span data-ttu-id="2c3cd-145">Varsayılan değer: `Online`.</span><span class="sxs-lookup"><span data-stu-id="2c3cd-145">The default is `Online`.</span></span><br /><br /> <span data-ttu-id="2c3cd-146">Daha fazla bilgi için bkz. [sertifikalarla çalışma](../../../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="2c3cd-146">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="trustedstorelocation-attribute"></a><span data-ttu-id="2c3cd-147">trustedStoreLocation özniteliği</span><span class="sxs-lookup"><span data-stu-id="2c3cd-147">trustedStoreLocation Attribute</span></span>  
  
|<span data-ttu-id="2c3cd-148">Değer</span><span class="sxs-lookup"><span data-stu-id="2c3cd-148">Value</span></span>|<span data-ttu-id="2c3cd-149">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2c3cd-149">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="2c3cd-150">Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="2c3cd-150">Enumeration</span></span>|<span data-ttu-id="2c3cd-151">Şu değerlerden biri: `LocalMachine` veya `CurrentUser` .</span><span class="sxs-lookup"><span data-stu-id="2c3cd-151">One of the following values: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="2c3cd-152">Varsayılan değer: `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="2c3cd-152">The default is `CurrentUser`.</span></span> <span data-ttu-id="2c3cd-153">İstemci uygulaması bir sistem hesabı altında çalışıyorsa, sertifika genellikle altında olur `LocalMachine` .</span><span class="sxs-lookup"><span data-stu-id="2c3cd-153">If the client application is running under a system account then the certificate is typically under `LocalMachine`.</span></span> <span data-ttu-id="2c3cd-154">İstemci uygulaması bir kullanıcı hesabı altında çalışıyorsa, sertifika genellikle içinde olur `CurrentUser` .</span><span class="sxs-lookup"><span data-stu-id="2c3cd-154">If the client application is running under a user account then the certificate is typically in `CurrentUser`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2c3cd-155">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="2c3cd-155">Child Elements</span></span>  
 <span data-ttu-id="2c3cd-156">Yok.</span><span class="sxs-lookup"><span data-stu-id="2c3cd-156">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2c3cd-157">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="2c3cd-157">Parent Elements</span></span>  
  
|<span data-ttu-id="2c3cd-158">Öğe</span><span class="sxs-lookup"><span data-stu-id="2c3cd-158">Element</span></span>|<span data-ttu-id="2c3cd-159">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2c3cd-159">Description</span></span>|  
|-------------|-----------------|  
|[\<peer>](peer-of-clientcredentials-element.md)|<span data-ttu-id="2c3cd-160">İstemcinin kimliğini bir eş hizmette doğrulamak için kullanılan kimlik bilgisini belirtir.</span><span class="sxs-lookup"><span data-stu-id="2c3cd-160">Specifies a credential used for authenticating the client to a peer service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2c3cd-161">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2c3cd-161">Remarks</span></span>  
 <span data-ttu-id="2c3cd-162">`<authentication>`Öğesi sınıfına karşılık gelir <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication> .</span><span class="sxs-lookup"><span data-stu-id="2c3cd-162">The `<authentication>` element corresponds to the <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication> class.</span></span> <span data-ttu-id="2c3cd-163">Bu öğe, ağ içinde komşu-komşu kimlik doğrulaması sırasında çağrılan bir doğrulayıcısı belirtir.</span><span class="sxs-lookup"><span data-stu-id="2c3cd-163">This element specifies a validator, which is invoked during neighbor-to-neighbor authentication in the mesh.</span></span> <span data-ttu-id="2c3cd-164">Yeni bir eş bir komşu bağlantı kurmaya çalıştığında, kendi kimlik bilgilerini yanıt veren eşe geçirir.</span><span class="sxs-lookup"><span data-stu-id="2c3cd-164">When a new peer tries to establish a neighbor connection, it passes its own credential to the responding peer.</span></span> <span data-ttu-id="2c3cd-165">Yanıtlayanın Doğrulayıcısı, uzak tarafın kimlik bilgilerini doğrulamak için çağrılır.</span><span class="sxs-lookup"><span data-stu-id="2c3cd-165">The validator of the responder is invoked to verify the credential of the remote party.</span></span> <span data-ttu-id="2c3cd-166">Kafeste bir eş bağlantı oluşturulduğunda her iki eş de karşılıklı olarak doğrulanır, her iki uçta da doğrulayıcılar çağrılır.</span><span class="sxs-lookup"><span data-stu-id="2c3cd-166">Whenever a peer connection is established in the mesh, both peers are mutually authenticated, meaning validators on both ends are invoked.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2c3cd-167">Örnek</span><span class="sxs-lookup"><span data-stu-id="2c3cd-167">Example</span></span>  
 <span data-ttu-id="2c3cd-168">Aşağıdaki kod, sertifika doğrulama modunu olarak ayarlar `PeerOrChainTrust` .</span><span class="sxs-lookup"><span data-stu-id="2c3cd-168">The following code sets the certificate validation mode to `PeerOrChainTrust`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2c3cd-169">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2c3cd-169">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>
- <xref:System.ServiceModel.Security.PeerCredential.PeerAuthentication%2A>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement.PeerAuthentication%2A>
- <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>
- [<span data-ttu-id="2c3cd-170">Sertifikalarla Çalışma</span><span class="sxs-lookup"><span data-stu-id="2c3cd-170">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="2c3cd-171">Eşler Arası Ağ</span><span class="sxs-lookup"><span data-stu-id="2c3cd-171">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
- <span data-ttu-id="2c3cd-172">[Eş kanal Iletisi kimlik doğrulaması](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="2c3cd-172">[Peer Channel Message Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="2c3cd-173">[Eş kanal özel kimlik doğrulaması](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="2c3cd-173">[Peer Channel Custom Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="2c3cd-174">Eş Kanalı Uygulamalarını Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="2c3cd-174">Securing Peer Channel Applications</span></span>](../../../wcf/feature-details/securing-peer-channel-applications.md)
