---
title: <messageSenderAuthentication> öğesi
ms.date: 03/30/2017
ms.assetid: 8d979dfc-a6f9-42ec-96d5-7fbc13a48118
ms.openlocfilehash: 804c280bcdb0fecc87f71121b7d95b5fd0268de9
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/28/2019
ms.locfileid: "67423117"
---
# <a name="messagesenderauthentication-element"></a><span data-ttu-id="18ca7-102">\<messageSenderAuthentication > öğesi</span><span class="sxs-lookup"><span data-stu-id="18ca7-102">\<messageSenderAuthentication> element</span></span>
<span data-ttu-id="18ca7-103">Eşler arası ileti gönderenler için kimlik doğrulama seçeneklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="18ca7-103">Specifies authentication options for peer-to-peer message senders.</span></span>  
  
 <span data-ttu-id="18ca7-104">Eşler arası programlama hakkında daha fazla bilgi için bkz. [eşler arası ağ](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).</span><span class="sxs-lookup"><span data-stu-id="18ca7-104">For more information about peer-to-peer programming, see [Peer-to-Peer Networking](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).</span></span>  
  
 <span data-ttu-id="18ca7-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="18ca7-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="18ca7-106">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="18ca7-106">\<behaviors></span></span>  
<span data-ttu-id="18ca7-107">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="18ca7-107">\<endpointBehaviors></span></span>  
<span data-ttu-id="18ca7-108">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="18ca7-108">\<behavior></span></span>  
<span data-ttu-id="18ca7-109">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="18ca7-109">\<clientCredentials></span></span>  
<span data-ttu-id="18ca7-110">\<Eş ></span><span class="sxs-lookup"><span data-stu-id="18ca7-110">\<peer></span></span>  
<span data-ttu-id="18ca7-111">\<messageSenderAuthentication ></span><span class="sxs-lookup"><span data-stu-id="18ca7-111">\<messageSenderAuthentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="18ca7-112">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="18ca7-112">Syntax</span></span>  
  
```xml  
<messageSenderAuthentication customCertificateValidatorType= "namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"
                             certificateValidationMode = "ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"
                             revocationMode="NoCheck/Online/Offline"
                             trustedStoreLocation="CurrentUser/LocalMachine" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="18ca7-113">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="18ca7-113">Attributes and Elements</span></span>  
 <span data-ttu-id="18ca7-114">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="18ca7-114">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="18ca7-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="18ca7-115">Attributes</span></span>  
  
|<span data-ttu-id="18ca7-116">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="18ca7-116">Attribute</span></span>|<span data-ttu-id="18ca7-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="18ca7-117">Description</span></span>|  
|---------------|-----------------|  
|`customCertificateValidatorType`|<span data-ttu-id="18ca7-118">Tür ve özel bir tür doğrulamak için kullanılan bir derleme.</span><span class="sxs-lookup"><span data-stu-id="18ca7-118">A type and assembly used to validate a custom type.</span></span> <span data-ttu-id="18ca7-119">Bu öznitelik olduğunda ayarlanmalıdır `certificateValidationMode` ayarlanır `Custom`.</span><span class="sxs-lookup"><span data-stu-id="18ca7-119">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span>|  
|`certificateValidationMode`|<span data-ttu-id="18ca7-120">Kimlik bilgilerini doğrulamak için kullanılan üç moddan birini belirtir.</span><span class="sxs-lookup"><span data-stu-id="18ca7-120">Specifies one of three modes used to validate credentials.</span></span> <span data-ttu-id="18ca7-121">Varsa kümesine `Custom`, ardından bir `customCertificateValidator` de sağlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="18ca7-121">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span>|  
|`revocationMode`|<span data-ttu-id="18ca7-122">İptal edilen sertifikalar listelerini (CRL) denetlemek için kullanılan modlardan biri.</span><span class="sxs-lookup"><span data-stu-id="18ca7-122">One of the modes used to check for a revoked certificate lists (CRL).</span></span>|  
|`trustedStoreLocation`|<span data-ttu-id="18ca7-123">İki sistem depolama konumlarından biri: `LocalMachine` veya `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="18ca7-123">One of the two system store locations: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="18ca7-124">Bir hizmet sertifikası istemciye anlaşıldığında, bu değer kullanılır.</span><span class="sxs-lookup"><span data-stu-id="18ca7-124">This value is used when a service certificate is negotiated to the client.</span></span> <span data-ttu-id="18ca7-125">Doğrulama işlemi gerçekleştirildiğinde karşı **güvenilir kişiler** depolamak belirtilen depolama konumu.</span><span class="sxs-lookup"><span data-stu-id="18ca7-125">Validation is performed against the **Trusted People** store in the specified store location.</span></span>|  
  
## <a name="customcertificatevalidatortype-attribute"></a><span data-ttu-id="18ca7-126">customCertificateValidatorType özniteliği</span><span class="sxs-lookup"><span data-stu-id="18ca7-126">customCertificateValidatorType Attribute</span></span>  
  
|<span data-ttu-id="18ca7-127">Değer</span><span class="sxs-lookup"><span data-stu-id="18ca7-127">Value</span></span>|<span data-ttu-id="18ca7-128">Açıklama</span><span class="sxs-lookup"><span data-stu-id="18ca7-128">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="18ca7-129">Dize</span><span class="sxs-lookup"><span data-stu-id="18ca7-129">String</span></span>|<span data-ttu-id="18ca7-130">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="18ca7-130">Optional.</span></span> <span data-ttu-id="18ca7-131">Tür adı ve derleme ve diğer veri türünü bulmak için kullanılan belirtir.</span><span class="sxs-lookup"><span data-stu-id="18ca7-131">Specifies the type name and assembly and other data used to find the type.</span></span> <span data-ttu-id="18ca7-132">En az bir ad ve tür adı gereklidir.</span><span class="sxs-lookup"><span data-stu-id="18ca7-132">At minimum, a namespace and type name are required.</span></span> <span data-ttu-id="18ca7-133">İsteğe bağlı bilgileri içerir: derleme adı, sürüm numarasını, kültürü ve ortak anahtar belirteci.</span><span class="sxs-lookup"><span data-stu-id="18ca7-133">Optional information includes: assembly name, version number, culture, and public key token.</span></span>|  
  
## <a name="certificatevalidationmode-attribute"></a><span data-ttu-id="18ca7-134">Certificatevalidationmode'u özniteliği</span><span class="sxs-lookup"><span data-stu-id="18ca7-134">certificateValidationMode Attribute</span></span>  
  
|<span data-ttu-id="18ca7-135">Değer</span><span class="sxs-lookup"><span data-stu-id="18ca7-135">Value</span></span>|<span data-ttu-id="18ca7-136">Açıklama</span><span class="sxs-lookup"><span data-stu-id="18ca7-136">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="18ca7-137">Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="18ca7-137">Enumeration</span></span>|<span data-ttu-id="18ca7-138">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="18ca7-138">Optional.</span></span> <span data-ttu-id="18ca7-139">Aşağıdaki değerlerden biri: `None`, `PeerTrust`, `ChainTrust`, `PeerOrChainTrust`, `Custom`.</span><span class="sxs-lookup"><span data-stu-id="18ca7-139">One of the following values: `None`, `PeerTrust`, `ChainTrust`, `PeerOrChainTrust`, `Custom`.</span></span> <span data-ttu-id="18ca7-140">Varsayılan, `ChainTrust` değeridir.</span><span class="sxs-lookup"><span data-stu-id="18ca7-140">The default is `ChainTrust`.</span></span> <span data-ttu-id="18ca7-141">Varsayılan, `ChainTrust` değeridir.</span><span class="sxs-lookup"><span data-stu-id="18ca7-141">The default is `ChainTrust`.</span></span><br /><br /> <span data-ttu-id="18ca7-142">Daha fazla bilgi için [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="18ca7-142">For more information, see [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="revocationmode-attribute"></a><span data-ttu-id="18ca7-143">revocationMode özniteliği</span><span class="sxs-lookup"><span data-stu-id="18ca7-143">revocationMode Attribute</span></span>  
  
|<span data-ttu-id="18ca7-144">Değer</span><span class="sxs-lookup"><span data-stu-id="18ca7-144">Value</span></span>|<span data-ttu-id="18ca7-145">Açıklama</span><span class="sxs-lookup"><span data-stu-id="18ca7-145">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="18ca7-146">Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="18ca7-146">Enumeration</span></span>|<span data-ttu-id="18ca7-147">Aşağıdaki değerlerden biri: `NoCheck`, `Online`, `Offline`.</span><span class="sxs-lookup"><span data-stu-id="18ca7-147">One of the following values: `NoCheck`, `Online`, `Offline`.</span></span> <span data-ttu-id="18ca7-148">Varsayılan, `Online` değeridir.</span><span class="sxs-lookup"><span data-stu-id="18ca7-148">The default is `Online`.</span></span><br /><br /> <span data-ttu-id="18ca7-149">Daha fazla bilgi için [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="18ca7-149">For more information, see [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="trustedstorelocation-attribute"></a><span data-ttu-id="18ca7-150">trustedStoreLocation özniteliği</span><span class="sxs-lookup"><span data-stu-id="18ca7-150">trustedStoreLocation Attribute</span></span>  
  
|<span data-ttu-id="18ca7-151">Değer</span><span class="sxs-lookup"><span data-stu-id="18ca7-151">Value</span></span>|<span data-ttu-id="18ca7-152">Açıklama</span><span class="sxs-lookup"><span data-stu-id="18ca7-152">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="18ca7-153">Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="18ca7-153">Enumeration</span></span>|<span data-ttu-id="18ca7-154">Aşağıdaki değerlerden biri: `LocalMachine` veya `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="18ca7-154">One of the following values: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="18ca7-155">Varsayılan, `CurrentUser` değeridir.</span><span class="sxs-lookup"><span data-stu-id="18ca7-155">The default is `CurrentUser`.</span></span> <span data-ttu-id="18ca7-156">İstemci uygulama bir sistem hesabı altında çalıştığından sonra sertifika genellikle altında olduğu `LocalMachine`.</span><span class="sxs-lookup"><span data-stu-id="18ca7-156">If the client application is running under a system account then the certificate is typically under `LocalMachine`.</span></span> <span data-ttu-id="18ca7-157">İstemci uygulama bir kullanıcı hesabı altında çalıştığından sonra sertifika genellikle kullanımda `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="18ca7-157">If the client application is running under a user account then the certificate is typically in `CurrentUser`.</span></span> <span data-ttu-id="18ca7-158">Varsayılan, `CurrentUser` değeridir.</span><span class="sxs-lookup"><span data-stu-id="18ca7-158">The default is `CurrentUser`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="18ca7-159">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="18ca7-159">Child Elements</span></span>  
 <span data-ttu-id="18ca7-160">Yok.</span><span class="sxs-lookup"><span data-stu-id="18ca7-160">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="18ca7-161">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="18ca7-161">Parent Elements</span></span>  
  
|<span data-ttu-id="18ca7-162">Öğe</span><span class="sxs-lookup"><span data-stu-id="18ca7-162">Element</span></span>|<span data-ttu-id="18ca7-163">Açıklama</span><span class="sxs-lookup"><span data-stu-id="18ca7-163">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="18ca7-164">\<Eş ></span><span class="sxs-lookup"><span data-stu-id="18ca7-164">\<peer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-clientcredentials-element.md)|<span data-ttu-id="18ca7-165">Bir eş hizmeti istemcisi kimlik doğrulaması için kullanılan bir kimlik bilgisini belirtir.</span><span class="sxs-lookup"><span data-stu-id="18ca7-165">Specifies a credential used for authenticating the client to a peer service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="18ca7-166">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="18ca7-166">Remarks</span></span>  
 <span data-ttu-id="18ca7-167">İleti kimlik doğrulaması seçilirse, bu öğe yapılandırılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="18ca7-167">This element must be configured if message authentication is chosen.</span></span> <span data-ttu-id="18ca7-168">Çıkış kanallar için her ileti tarafından sağlanan sertifikayı kullanarak imzalanmış [ \<sertifika >](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-element.md).</span><span class="sxs-lookup"><span data-stu-id="18ca7-168">For output channels, each message is signed using the certificate provided by [\<certificate>](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-element.md).</span></span> <span data-ttu-id="18ca7-169">Tüm iletileri tarafından belirtilen Doğrulayıcı kullanarak ileti kimlik bilgileri karşı uygulamaya teslim önce iade `customCertificateValidatorType` bu öğenin özniteliği.</span><span class="sxs-lookup"><span data-stu-id="18ca7-169">All messages, before delivered to the application, are checked against the message credential using the validator specified by the `customCertificateValidatorType` attribute of this element.</span></span> <span data-ttu-id="18ca7-170">Doğrulayıcı kabul edin veya kimlik bilgilerini reddedebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="18ca7-170">The validator can either accept or reject the credential.</span></span>  
  
## <a name="example"></a><span data-ttu-id="18ca7-171">Örnek</span><span class="sxs-lookup"><span data-stu-id="18ca7-171">Example</span></span>  
 <span data-ttu-id="18ca7-172">Aşağıdaki kodu ileti gönderen doğrulama modunu ayarlar `PeerOrChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="18ca7-172">The following code sets the message sender validation mode to `PeerOrChainTrust`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="18ca7-173">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="18ca7-173">See also</span></span>

- <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>
- <xref:System.ServiceModel.Security.PeerCredential.MessageSenderAuthentication%2A>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement.MessageSenderAuthentication%2A>
- <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>
- [<span data-ttu-id="18ca7-174">Sertifikalarla Çalışma</span><span class="sxs-lookup"><span data-stu-id="18ca7-174">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="18ca7-175">Eşler Arası Ağ</span><span class="sxs-lookup"><span data-stu-id="18ca7-175">Peer-to-Peer Networking</span></span>](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)
- <span data-ttu-id="18ca7-176">[Eş kanal ileti kimlik doğrulaması](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="18ca7-176">[Peer Channel Message Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="18ca7-177">[Eş kanal özel kimlik doğrulama](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="18ca7-177">[Peer Channel Custom Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="18ca7-178">Eş Kanalı Uygulamalarını Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="18ca7-178">Securing Peer Channel Applications</span></span>](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)
