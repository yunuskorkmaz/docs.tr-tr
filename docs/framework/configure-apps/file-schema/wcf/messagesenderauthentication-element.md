---
title: '&lt;messageSenderAuthentication&gt; öğesi'
ms.date: 03/30/2017
ms.assetid: 8d979dfc-a6f9-42ec-96d5-7fbc13a48118
ms.openlocfilehash: 898569796c65a7999583f4faba9f11a6172a5af8
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32750745"
---
# <a name="ltmessagesenderauthenticationgt-element"></a><span data-ttu-id="a80f2-102">&lt;messageSenderAuthentication&gt; öğesi</span><span class="sxs-lookup"><span data-stu-id="a80f2-102">&lt;messageSenderAuthentication&gt; element</span></span>
<span data-ttu-id="a80f2-103">Eşler arası ileti gönderenler için kimlik doğrulama seçeneklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="a80f2-103">Specifies authentication options for peer-to-peer message senders.</span></span>  
  
 <span data-ttu-id="a80f2-104">Eşler arası programlama hakkında daha fazla bilgi için bkz: [eşler arası ağ](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).</span><span class="sxs-lookup"><span data-stu-id="a80f2-104">For more information about peer-to-peer programming, see [Peer-to-Peer Networking](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).</span></span>  
  
 <span data-ttu-id="a80f2-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="a80f2-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="a80f2-106">\<davranışları ></span><span class="sxs-lookup"><span data-stu-id="a80f2-106">\<behaviors></span></span>  
<span data-ttu-id="a80f2-107">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="a80f2-107">\<endpointBehaviors></span></span>  
<span data-ttu-id="a80f2-108">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="a80f2-108">\<behavior></span></span>  
<span data-ttu-id="a80f2-109">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="a80f2-109">\<clientCredentials></span></span>  
<span data-ttu-id="a80f2-110">\<Eş ></span><span class="sxs-lookup"><span data-stu-id="a80f2-110">\<peer></span></span>  
<span data-ttu-id="a80f2-111">\<messageSenderAuthentication ></span><span class="sxs-lookup"><span data-stu-id="a80f2-111">\<messageSenderAuthentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a80f2-112">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a80f2-112">Syntax</span></span>  
  
```xml  
<messageSenderAuthentication  
customCertificateValidatorType= "namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"  
certificateValidationMode = "ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"  
revocationMode="NoCheck/Online/Offline"  
trustedStoreLocation="CurrentUser/LocalMachine"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a80f2-113">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="a80f2-113">Attributes and Elements</span></span>  
 <span data-ttu-id="a80f2-114">Öznitelikler, alt öğelerini ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır</span><span class="sxs-lookup"><span data-stu-id="a80f2-114">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a80f2-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a80f2-115">Attributes</span></span>  
  
|<span data-ttu-id="a80f2-116">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="a80f2-116">Attribute</span></span>|<span data-ttu-id="a80f2-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a80f2-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a80f2-118">customCertificateValidatorType</span><span class="sxs-lookup"><span data-stu-id="a80f2-118">customCertificateValidatorType</span></span>|<span data-ttu-id="a80f2-119">Tür ve bir özel tür doğrulamak için kullanılan derleme.</span><span class="sxs-lookup"><span data-stu-id="a80f2-119">A type and assembly used to validate a custom type.</span></span> <span data-ttu-id="a80f2-120">Bu öznitelik ne zaman ayarlanmalıdır `certificateValidationMode` ayarlanır `Custom`.</span><span class="sxs-lookup"><span data-stu-id="a80f2-120">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span>|  
|<span data-ttu-id="a80f2-121">certifcateValidationMode</span><span class="sxs-lookup"><span data-stu-id="a80f2-121">certifcateValidationMode</span></span>|<span data-ttu-id="a80f2-122">Kimlik bilgilerini doğrulamak için kullanılan üç modlarından birini belirtir.</span><span class="sxs-lookup"><span data-stu-id="a80f2-122">Specifies one of three modes used to validate credentials.</span></span> <span data-ttu-id="a80f2-123">Varsa kümesine `Custom`, sonra bir `customCertificateValidator` de sağlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a80f2-123">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span>|  
|<span data-ttu-id="a80f2-124">revocationMode</span><span class="sxs-lookup"><span data-stu-id="a80f2-124">revocationMode</span></span>|<span data-ttu-id="a80f2-125">İptal edilen sertifika (CRL) listeler denetlemek için kullanılan modlarından birini.</span><span class="sxs-lookup"><span data-stu-id="a80f2-125">One of the modes used to check for a revoked certificate lists (CRL).</span></span>|  
|<span data-ttu-id="a80f2-126">trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="a80f2-126">trustedStoreLocation</span></span>|<span data-ttu-id="a80f2-127">İki sistem deposu konumlardan birini: `LocalMachine` veya `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="a80f2-127">One of the two system store locations: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="a80f2-128">Bu değer, bir hizmet sertifikası istemciye anlaşıldığında kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a80f2-128">This value is used when a service certificate is negotiated to the client.</span></span> <span data-ttu-id="a80f2-129">Doğrulama işlemi gerçekleştirildiğinde karşı **güvenilir kişiler** belirtilen depo konumda saklayın.</span><span class="sxs-lookup"><span data-stu-id="a80f2-129">Validation is performed against the **Trusted People** store in the specified store location.</span></span>|  
  
## <a name="customcertificatevalidatortype-attribute"></a><span data-ttu-id="a80f2-130">customCertificateValidatorType özniteliği</span><span class="sxs-lookup"><span data-stu-id="a80f2-130">customCertificateValidatorType Attribute</span></span>  
  
|<span data-ttu-id="a80f2-131">Değer</span><span class="sxs-lookup"><span data-stu-id="a80f2-131">Value</span></span>|<span data-ttu-id="a80f2-132">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a80f2-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a80f2-133">Dize</span><span class="sxs-lookup"><span data-stu-id="a80f2-133">String</span></span>|<span data-ttu-id="a80f2-134">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="a80f2-134">Optional.</span></span> <span data-ttu-id="a80f2-135">Tür adı ve derleme ve diğer veri türü bulmak için kullanılan belirtir.</span><span class="sxs-lookup"><span data-stu-id="a80f2-135">Specifies the type name and assembly and other data used to find the type.</span></span> <span data-ttu-id="a80f2-136">En azından bir ad ve tür adı gereklidir.</span><span class="sxs-lookup"><span data-stu-id="a80f2-136">At minimum, a namespace and type name are required.</span></span> <span data-ttu-id="a80f2-137">İsteğe bağlı bilgileri içerir: derleme adı, sürüm numarası, kültür ve ortak anahtar belirteci.</span><span class="sxs-lookup"><span data-stu-id="a80f2-137">Optional information includes: assembly name, version number, culture, and public key token.</span></span>|  
  
## <a name="certificatevalidationmode-attribute"></a><span data-ttu-id="a80f2-138">certificateValidationMode değerini özniteliği</span><span class="sxs-lookup"><span data-stu-id="a80f2-138">certificateValidationMode Attribute</span></span>  
  
|<span data-ttu-id="a80f2-139">Değer</span><span class="sxs-lookup"><span data-stu-id="a80f2-139">Value</span></span>|<span data-ttu-id="a80f2-140">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a80f2-140">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a80f2-141">Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="a80f2-141">Enumeration</span></span>|<span data-ttu-id="a80f2-142">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="a80f2-142">Optional.</span></span> <span data-ttu-id="a80f2-143">Aşağıdaki değerlerden birini: `None`, `PeerTrust`, `ChainTrust`, `PeerOrChainTrust`, `Custom`.</span><span class="sxs-lookup"><span data-stu-id="a80f2-143">One of the following values: `None`, `PeerTrust`, `ChainTrust`, `PeerOrChainTrust`, `Custom`.</span></span> <span data-ttu-id="a80f2-144">Varsayılan, `ChainTrust` değeridir.</span><span class="sxs-lookup"><span data-stu-id="a80f2-144">The default is `ChainTrust`.</span></span> <span data-ttu-id="a80f2-145">Varsayılan, `ChainTrust` değeridir.</span><span class="sxs-lookup"><span data-stu-id="a80f2-145">The default is `ChainTrust`.</span></span><br /><br /> <span data-ttu-id="a80f2-146">Daha fazla bilgi için bkz: [sertifikalarla çalışma](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="a80f2-146">For more information, see [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="revocationmode-attribute"></a><span data-ttu-id="a80f2-147">revocationMode özniteliği</span><span class="sxs-lookup"><span data-stu-id="a80f2-147">revocationMode Attribute</span></span>  
  
|<span data-ttu-id="a80f2-148">Değer</span><span class="sxs-lookup"><span data-stu-id="a80f2-148">Value</span></span>|<span data-ttu-id="a80f2-149">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a80f2-149">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a80f2-150">Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="a80f2-150">Enumeration</span></span>|<span data-ttu-id="a80f2-151">Aşağıdaki değerlerden birini: `NoCheck`, `Online`, `Offline`.</span><span class="sxs-lookup"><span data-stu-id="a80f2-151">One of the following values: `NoCheck`, `Online`, `Offline`.</span></span> <span data-ttu-id="a80f2-152">Varsayılan, `Online` değeridir.</span><span class="sxs-lookup"><span data-stu-id="a80f2-152">The default is `Online`.</span></span><br /><br /> <span data-ttu-id="a80f2-153">Daha fazla bilgi için bkz: [sertifikalarla çalışma](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="a80f2-153">For more information, see [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="trustedstorelocation-attribute"></a><span data-ttu-id="a80f2-154">trustedStoreLocation özniteliği</span><span class="sxs-lookup"><span data-stu-id="a80f2-154">trustedStoreLocation Attribute</span></span>  
  
|<span data-ttu-id="a80f2-155">Değer</span><span class="sxs-lookup"><span data-stu-id="a80f2-155">Value</span></span>|<span data-ttu-id="a80f2-156">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a80f2-156">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a80f2-157">Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="a80f2-157">Enumeration</span></span>|<span data-ttu-id="a80f2-158">Aşağıdaki değerlerden birini: `LocalMachine` veya `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="a80f2-158">One of the following values: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="a80f2-159">Varsayılan, `CurrentUser` değeridir.</span><span class="sxs-lookup"><span data-stu-id="a80f2-159">The default is `CurrentUser`.</span></span> <span data-ttu-id="a80f2-160">İstemci uygulaması bir sistem hesabı altında çalışan sonra sertifika genellikle altında olduğu `LocalMachine`.</span><span class="sxs-lookup"><span data-stu-id="a80f2-160">If the client application is running under a system account then the certificate is typically under `LocalMachine`.</span></span> <span data-ttu-id="a80f2-161">İstemci uygulama bir kullanıcı hesabı altında çalışan sonra sertifikayı genellikle kullanımda `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="a80f2-161">If the client application is running under a user account then the certificate is typically in `CurrentUser`.</span></span> <span data-ttu-id="a80f2-162">Varsayılan, `CurrentUser` değeridir.</span><span class="sxs-lookup"><span data-stu-id="a80f2-162">The default is `CurrentUser`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a80f2-163">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="a80f2-163">Child Elements</span></span>  
 <span data-ttu-id="a80f2-164">Yok.</span><span class="sxs-lookup"><span data-stu-id="a80f2-164">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a80f2-165">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="a80f2-165">Parent Elements</span></span>  
  
|<span data-ttu-id="a80f2-166">Öğe</span><span class="sxs-lookup"><span data-stu-id="a80f2-166">Element</span></span>|<span data-ttu-id="a80f2-167">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a80f2-167">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a80f2-168">\<Eş ></span><span class="sxs-lookup"><span data-stu-id="a80f2-168">\<peer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-clientcredentials-element.md)|<span data-ttu-id="a80f2-169">İstemci bir eş hizmeti için kimlik doğrulaması için kullanılan kimlik bilgisini belirtir.</span><span class="sxs-lookup"><span data-stu-id="a80f2-169">Specifies a credential used for authenticating the client to a peer service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a80f2-170">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a80f2-170">Remarks</span></span>  
 <span data-ttu-id="a80f2-171">Bu öğe, ileti kimlik doğrulaması seçilirse yapılandırılmış olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="a80f2-171">This element must be configured if message authentication is chosen.</span></span> <span data-ttu-id="a80f2-172">Çıktı kanallar için her ileti tarafından sağlanan sertifika kullanılarak imzalanmıştır [ \<sertifika >](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-element.md).</span><span class="sxs-lookup"><span data-stu-id="a80f2-172">For output channels, each message is signed using the certificate provided by [\<certificate>](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-element.md).</span></span> <span data-ttu-id="a80f2-173">Tüm iletiler, uygulamaya teslim önce tarafından belirtilen Doğrulayıcı kullanarak ileti kimlik bilgileri karşı denetlenir `customCertificateValidatorType` bu öğesinin özniteliği.</span><span class="sxs-lookup"><span data-stu-id="a80f2-173">All messages, before delivered to the application, are checked against the message credential using the validator specified by the `customCertificateValidatorType` attribute of this element.</span></span> <span data-ttu-id="a80f2-174">Doğrulayıcı kabul edin veya kimlik bilgisi reddedin.</span><span class="sxs-lookup"><span data-stu-id="a80f2-174">The validator can either accept or reject the credential.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a80f2-175">Örnek</span><span class="sxs-lookup"><span data-stu-id="a80f2-175">Example</span></span>  
 <span data-ttu-id="a80f2-176">Aşağıdaki kod ileti gönderen doğrulama modunu ayarlar `PeerOrChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="a80f2-176">The following code sets the message sender validation mode to `PeerOrChainTrust`.</span></span>  
  
```xml  
<behaviors>  
 <endpointBehaviors>  
  <behavior name="MyEndpointBehavior">  
   <clientCredentials>  
    <peer>  
      <certificate findValue="www.contoso.com"   
                   storeLocation="LocalMachine"  
                   x509FindType="FindByIssuerName" />  
        <messageSenderAuthentication   
          certificateValidationMode="PeerOrChainTrust" />  
       <messageSenderAuthentication certificateValidationMode="None" />  
    </peer>  
   </clientCredentials>  
  </behavior>  
 </endpointBehaviors>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a80f2-177">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a80f2-177">See Also</span></span>  
 <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>  
 <xref:System.ServiceModel.Security.PeerCredential.MessageSenderAuthentication%2A>  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement.MessageSenderAuthentication%2A>  
 <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>  
 [<span data-ttu-id="a80f2-178">Sertifikalarla Çalışma</span><span class="sxs-lookup"><span data-stu-id="a80f2-178">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="a80f2-179">Eşler Arası Ağ</span><span class="sxs-lookup"><span data-stu-id="a80f2-179">Peer-to-Peer Networking</span></span>](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)  
 [<span data-ttu-id="a80f2-180">Eş kanal ileti kimlik doğrulaması</span><span class="sxs-lookup"><span data-stu-id="a80f2-180">Peer Channel Message Authentication</span></span>](http://msdn.microsoft.com/library/80e73386-514e-4c30-9e4a-b9ca8c173a95)  
 [<span data-ttu-id="a80f2-181">Eş kanal özel kimlik doğrulama</span><span class="sxs-lookup"><span data-stu-id="a80f2-181">Peer Channel Custom Authentication</span></span>](http://msdn.microsoft.com/library/4aa8a82e-41a8-48e2-8621-7e1cbabdca7c)  
 [<span data-ttu-id="a80f2-182">Eş Kanalı Uygulamalarını Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="a80f2-182">Securing Peer Channel Applications</span></span>](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)
