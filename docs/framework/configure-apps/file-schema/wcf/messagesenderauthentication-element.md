---
title: '&lt;messageSenderAuthentication&gt; öğesi'
ms.date: 03/30/2017
ms.assetid: 8d979dfc-a6f9-42ec-96d5-7fbc13a48118
ms.openlocfilehash: cb727df7b8d7605cbe984a8f6737c89bf1bfb2be
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43532210"
---
# <a name="ltmessagesenderauthenticationgt-element"></a><span data-ttu-id="40aca-102">&lt;messageSenderAuthentication&gt; öğesi</span><span class="sxs-lookup"><span data-stu-id="40aca-102">&lt;messageSenderAuthentication&gt; element</span></span>
<span data-ttu-id="40aca-103">Eşler arası ileti gönderenler için kimlik doğrulama seçeneklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="40aca-103">Specifies authentication options for peer-to-peer message senders.</span></span>  
  
 <span data-ttu-id="40aca-104">Eşler arası programlama hakkında daha fazla bilgi için bkz. [eşler arası ağ](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).</span><span class="sxs-lookup"><span data-stu-id="40aca-104">For more information about peer-to-peer programming, see [Peer-to-Peer Networking](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).</span></span>  
  
 <span data-ttu-id="40aca-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="40aca-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="40aca-106">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="40aca-106">\<behaviors></span></span>  
<span data-ttu-id="40aca-107">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="40aca-107">\<endpointBehaviors></span></span>  
<span data-ttu-id="40aca-108">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="40aca-108">\<behavior></span></span>  
<span data-ttu-id="40aca-109">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="40aca-109">\<clientCredentials></span></span>  
<span data-ttu-id="40aca-110">\<Eş ></span><span class="sxs-lookup"><span data-stu-id="40aca-110">\<peer></span></span>  
<span data-ttu-id="40aca-111">\<messageSenderAuthentication ></span><span class="sxs-lookup"><span data-stu-id="40aca-111">\<messageSenderAuthentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40aca-112">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="40aca-112">Syntax</span></span>  
  
```xml  
<messageSenderAuthentication  
customCertificateValidatorType= "namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"  
certificateValidationMode = "ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"  
revocationMode="NoCheck/Online/Offline"  
trustedStoreLocation="CurrentUser/LocalMachine"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="40aca-113">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="40aca-113">Attributes and Elements</span></span>  
 <span data-ttu-id="40aca-114">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="40aca-114">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="40aca-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="40aca-115">Attributes</span></span>  
  
|<span data-ttu-id="40aca-116">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="40aca-116">Attribute</span></span>|<span data-ttu-id="40aca-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="40aca-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="40aca-118">customCertificateValidatorType</span><span class="sxs-lookup"><span data-stu-id="40aca-118">customCertificateValidatorType</span></span>|<span data-ttu-id="40aca-119">Tür ve özel bir tür doğrulamak için kullanılan bir derleme.</span><span class="sxs-lookup"><span data-stu-id="40aca-119">A type and assembly used to validate a custom type.</span></span> <span data-ttu-id="40aca-120">Bu öznitelik olduğunda ayarlanmalıdır `certificateValidationMode` ayarlanır `Custom`.</span><span class="sxs-lookup"><span data-stu-id="40aca-120">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span>|  
|<span data-ttu-id="40aca-121">certifcateValidationMode</span><span class="sxs-lookup"><span data-stu-id="40aca-121">certifcateValidationMode</span></span>|<span data-ttu-id="40aca-122">Kimlik bilgilerini doğrulamak için kullanılan üç moddan birini belirtir.</span><span class="sxs-lookup"><span data-stu-id="40aca-122">Specifies one of three modes used to validate credentials.</span></span> <span data-ttu-id="40aca-123">Varsa kümesine `Custom`, ardından bir `customCertificateValidator` de sağlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="40aca-123">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span>|  
|<span data-ttu-id="40aca-124">revocationMode</span><span class="sxs-lookup"><span data-stu-id="40aca-124">revocationMode</span></span>|<span data-ttu-id="40aca-125">İptal edilen sertifikalar listelerini (CRL) denetlemek için kullanılan modlardan biri.</span><span class="sxs-lookup"><span data-stu-id="40aca-125">One of the modes used to check for a revoked certificate lists (CRL).</span></span>|  
|<span data-ttu-id="40aca-126">trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="40aca-126">trustedStoreLocation</span></span>|<span data-ttu-id="40aca-127">İki sistem depolama konumlarından biri: `LocalMachine` veya `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="40aca-127">One of the two system store locations: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="40aca-128">Bir hizmet sertifikası istemciye anlaşıldığında, bu değer kullanılır.</span><span class="sxs-lookup"><span data-stu-id="40aca-128">This value is used when a service certificate is negotiated to the client.</span></span> <span data-ttu-id="40aca-129">Doğrulama işlemi gerçekleştirildiğinde karşı **güvenilir kişiler** depolamak belirtilen depolama konumu.</span><span class="sxs-lookup"><span data-stu-id="40aca-129">Validation is performed against the **Trusted People** store in the specified store location.</span></span>|  
  
## <a name="customcertificatevalidatortype-attribute"></a><span data-ttu-id="40aca-130">customCertificateValidatorType özniteliği</span><span class="sxs-lookup"><span data-stu-id="40aca-130">customCertificateValidatorType Attribute</span></span>  
  
|<span data-ttu-id="40aca-131">Değer</span><span class="sxs-lookup"><span data-stu-id="40aca-131">Value</span></span>|<span data-ttu-id="40aca-132">Açıklama</span><span class="sxs-lookup"><span data-stu-id="40aca-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="40aca-133">Dize</span><span class="sxs-lookup"><span data-stu-id="40aca-133">String</span></span>|<span data-ttu-id="40aca-134">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="40aca-134">Optional.</span></span> <span data-ttu-id="40aca-135">Tür adı ve derleme ve diğer veri türünü bulmak için kullanılan belirtir.</span><span class="sxs-lookup"><span data-stu-id="40aca-135">Specifies the type name and assembly and other data used to find the type.</span></span> <span data-ttu-id="40aca-136">En az bir ad ve tür adı gereklidir.</span><span class="sxs-lookup"><span data-stu-id="40aca-136">At minimum, a namespace and type name are required.</span></span> <span data-ttu-id="40aca-137">İsteğe bağlı bilgileri içerir: derleme adı, sürüm numarasını, kültürü ve ortak anahtar belirteci.</span><span class="sxs-lookup"><span data-stu-id="40aca-137">Optional information includes: assembly name, version number, culture, and public key token.</span></span>|  
  
## <a name="certificatevalidationmode-attribute"></a><span data-ttu-id="40aca-138">Certificatevalidationmode'u özniteliği</span><span class="sxs-lookup"><span data-stu-id="40aca-138">certificateValidationMode Attribute</span></span>  
  
|<span data-ttu-id="40aca-139">Değer</span><span class="sxs-lookup"><span data-stu-id="40aca-139">Value</span></span>|<span data-ttu-id="40aca-140">Açıklama</span><span class="sxs-lookup"><span data-stu-id="40aca-140">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="40aca-141">Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="40aca-141">Enumeration</span></span>|<span data-ttu-id="40aca-142">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="40aca-142">Optional.</span></span> <span data-ttu-id="40aca-143">Aşağıdaki değerlerden biri: `None`, `PeerTrust`, `ChainTrust`, `PeerOrChainTrust`, `Custom`.</span><span class="sxs-lookup"><span data-stu-id="40aca-143">One of the following values: `None`, `PeerTrust`, `ChainTrust`, `PeerOrChainTrust`, `Custom`.</span></span> <span data-ttu-id="40aca-144">Varsayılan, `ChainTrust` değeridir.</span><span class="sxs-lookup"><span data-stu-id="40aca-144">The default is `ChainTrust`.</span></span> <span data-ttu-id="40aca-145">Varsayılan, `ChainTrust` değeridir.</span><span class="sxs-lookup"><span data-stu-id="40aca-145">The default is `ChainTrust`.</span></span><br /><br /> <span data-ttu-id="40aca-146">Daha fazla bilgi için [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="40aca-146">For more information, see [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="revocationmode-attribute"></a><span data-ttu-id="40aca-147">revocationMode özniteliği</span><span class="sxs-lookup"><span data-stu-id="40aca-147">revocationMode Attribute</span></span>  
  
|<span data-ttu-id="40aca-148">Değer</span><span class="sxs-lookup"><span data-stu-id="40aca-148">Value</span></span>|<span data-ttu-id="40aca-149">Açıklama</span><span class="sxs-lookup"><span data-stu-id="40aca-149">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="40aca-150">Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="40aca-150">Enumeration</span></span>|<span data-ttu-id="40aca-151">Aşağıdaki değerlerden biri: `NoCheck`, `Online`, `Offline`.</span><span class="sxs-lookup"><span data-stu-id="40aca-151">One of the following values: `NoCheck`, `Online`, `Offline`.</span></span> <span data-ttu-id="40aca-152">Varsayılan, `Online` değeridir.</span><span class="sxs-lookup"><span data-stu-id="40aca-152">The default is `Online`.</span></span><br /><br /> <span data-ttu-id="40aca-153">Daha fazla bilgi için [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="40aca-153">For more information, see [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="trustedstorelocation-attribute"></a><span data-ttu-id="40aca-154">trustedStoreLocation özniteliği</span><span class="sxs-lookup"><span data-stu-id="40aca-154">trustedStoreLocation Attribute</span></span>  
  
|<span data-ttu-id="40aca-155">Değer</span><span class="sxs-lookup"><span data-stu-id="40aca-155">Value</span></span>|<span data-ttu-id="40aca-156">Açıklama</span><span class="sxs-lookup"><span data-stu-id="40aca-156">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="40aca-157">Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="40aca-157">Enumeration</span></span>|<span data-ttu-id="40aca-158">Aşağıdaki değerlerden biri: `LocalMachine` veya `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="40aca-158">One of the following values: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="40aca-159">Varsayılan, `CurrentUser` değeridir.</span><span class="sxs-lookup"><span data-stu-id="40aca-159">The default is `CurrentUser`.</span></span> <span data-ttu-id="40aca-160">İstemci uygulama bir sistem hesabı altında çalıştığından sonra sertifika genellikle altında olduğu `LocalMachine`.</span><span class="sxs-lookup"><span data-stu-id="40aca-160">If the client application is running under a system account then the certificate is typically under `LocalMachine`.</span></span> <span data-ttu-id="40aca-161">İstemci uygulama bir kullanıcı hesabı altında çalıştığından sonra sertifika genellikle kullanımda `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="40aca-161">If the client application is running under a user account then the certificate is typically in `CurrentUser`.</span></span> <span data-ttu-id="40aca-162">Varsayılan, `CurrentUser` değeridir.</span><span class="sxs-lookup"><span data-stu-id="40aca-162">The default is `CurrentUser`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="40aca-163">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="40aca-163">Child Elements</span></span>  
 <span data-ttu-id="40aca-164">Yok.</span><span class="sxs-lookup"><span data-stu-id="40aca-164">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="40aca-165">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="40aca-165">Parent Elements</span></span>  
  
|<span data-ttu-id="40aca-166">Öğe</span><span class="sxs-lookup"><span data-stu-id="40aca-166">Element</span></span>|<span data-ttu-id="40aca-167">Açıklama</span><span class="sxs-lookup"><span data-stu-id="40aca-167">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="40aca-168">\<Eş ></span><span class="sxs-lookup"><span data-stu-id="40aca-168">\<peer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-clientcredentials-element.md)|<span data-ttu-id="40aca-169">Bir eş hizmeti istemcisi kimlik doğrulaması için kullanılan bir kimlik bilgisini belirtir.</span><span class="sxs-lookup"><span data-stu-id="40aca-169">Specifies a credential used for authenticating the client to a peer service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="40aca-170">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="40aca-170">Remarks</span></span>  
 <span data-ttu-id="40aca-171">İleti kimlik doğrulaması seçilirse, bu öğe yapılandırılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="40aca-171">This element must be configured if message authentication is chosen.</span></span> <span data-ttu-id="40aca-172">Çıkış kanallar için her ileti tarafından sağlanan sertifikayı kullanarak imzalanmış [ \<sertifika >](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-element.md).</span><span class="sxs-lookup"><span data-stu-id="40aca-172">For output channels, each message is signed using the certificate provided by [\<certificate>](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-element.md).</span></span> <span data-ttu-id="40aca-173">Tüm iletileri tarafından belirtilen Doğrulayıcı kullanarak ileti kimlik bilgileri karşı uygulamaya teslim önce iade `customCertificateValidatorType` bu öğenin özniteliği.</span><span class="sxs-lookup"><span data-stu-id="40aca-173">All messages, before delivered to the application, are checked against the message credential using the validator specified by the `customCertificateValidatorType` attribute of this element.</span></span> <span data-ttu-id="40aca-174">Doğrulayıcı kabul edin veya kimlik bilgilerini reddedebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="40aca-174">The validator can either accept or reject the credential.</span></span>  
  
## <a name="example"></a><span data-ttu-id="40aca-175">Örnek</span><span class="sxs-lookup"><span data-stu-id="40aca-175">Example</span></span>  
 <span data-ttu-id="40aca-176">Aşağıdaki kodu ileti gönderen doğrulama modunu ayarlar `PeerOrChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="40aca-176">The following code sets the message sender validation mode to `PeerOrChainTrust`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="40aca-177">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="40aca-177">See Also</span></span>  
 <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>  
 <xref:System.ServiceModel.Security.PeerCredential.MessageSenderAuthentication%2A>  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement.MessageSenderAuthentication%2A>  
 <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>  
 [<span data-ttu-id="40aca-178">Sertifikalarla Çalışma</span><span class="sxs-lookup"><span data-stu-id="40aca-178">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="40aca-179">Eşler Arası Ağ</span><span class="sxs-lookup"><span data-stu-id="40aca-179">Peer-to-Peer Networking</span></span>](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)  
 [<span data-ttu-id="40aca-180">Eş kanal ileti kimlik doğrulaması</span><span class="sxs-lookup"><span data-stu-id="40aca-180">Peer Channel Message Authentication</span></span>](https://msdn.microsoft.com/library/80e73386-514e-4c30-9e4a-b9ca8c173a95)  
 [<span data-ttu-id="40aca-181">Eş kanal özel kimlik doğrulama</span><span class="sxs-lookup"><span data-stu-id="40aca-181">Peer Channel Custom Authentication</span></span>](https://msdn.microsoft.com/library/4aa8a82e-41a8-48e2-8621-7e1cbabdca7c)  
 [<span data-ttu-id="40aca-182">Eş Kanalı Uygulamalarını Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="40aca-182">Securing Peer Channel Applications</span></span>](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)
