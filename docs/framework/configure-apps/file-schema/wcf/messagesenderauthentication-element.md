---
title: <messageSenderAuthentication> öğesi
ms.date: 03/30/2017
ms.assetid: 8d979dfc-a6f9-42ec-96d5-7fbc13a48118
ms.openlocfilehash: bab0e50d7feba3ea55d505be07cfa41427a5cbbc
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397782"
---
# <a name="messagesenderauthentication-element"></a><span data-ttu-id="f0570-102">\<Iletienderauthentication > öğesi</span><span class="sxs-lookup"><span data-stu-id="f0570-102">\<messageSenderAuthentication> element</span></span>
<span data-ttu-id="f0570-103">Eşler arası ileti gönderenler için kimlik doğrulama seçeneklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="f0570-103">Specifies authentication options for peer-to-peer message senders.</span></span>  
  
 <span data-ttu-id="f0570-104">Eşler arası programlama hakkında daha fazla bilgi için bkz. eşler [arası ağ iletişimi](../../../wcf/feature-details/peer-to-peer-networking.md).</span><span class="sxs-lookup"><span data-stu-id="f0570-104">For more information about peer-to-peer programming, see [Peer-to-Peer Networking](../../../wcf/feature-details/peer-to-peer-networking.md).</span></span>  
  
<span data-ttu-id="f0570-105">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="f0570-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="f0570-106">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="f0570-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="f0570-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranışlar >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="f0570-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="f0570-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Endpointdavranışlar >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="f0570-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="f0570-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranış >** ](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="f0570-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="f0570-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<clientCredentials >** ](clientcredentials.md)</span><span class="sxs-lookup"><span data-stu-id="f0570-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)</span></span>\
<span data-ttu-id="f0570-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<eş >** ](peer-of-clientcredentials-element.md)</span><span class="sxs-lookup"><span data-stu-id="f0570-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<peer>**](peer-of-clientcredentials-element.md)</span></span>\
<span data-ttu-id="f0570-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Iletienderauthentication >**</span><span class="sxs-lookup"><span data-stu-id="f0570-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<messageSenderAuthentication>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0570-113">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f0570-113">Syntax</span></span>  
  
```xml  
<messageSenderAuthentication customCertificateValidatorType= "namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"
                             certificateValidationMode = "ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"
                             revocationMode="NoCheck/Online/Offline"
                             trustedStoreLocation="CurrentUser/LocalMachine" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f0570-114">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="f0570-114">Attributes and Elements</span></span>  
 <span data-ttu-id="f0570-115">Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır</span><span class="sxs-lookup"><span data-stu-id="f0570-115">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f0570-116">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f0570-116">Attributes</span></span>  
  
|<span data-ttu-id="f0570-117">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="f0570-117">Attribute</span></span>|<span data-ttu-id="f0570-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f0570-118">Description</span></span>|  
|---------------|-----------------|  
|`customCertificateValidatorType`|<span data-ttu-id="f0570-119">Özel bir türü doğrulamak için kullanılan tür ve derleme.</span><span class="sxs-lookup"><span data-stu-id="f0570-119">A type and assembly used to validate a custom type.</span></span> <span data-ttu-id="f0570-120">Bu öznitelik `certificateValidationMode` , olarak `Custom`ayarlandığında ayarlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f0570-120">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span>|  
|`certificateValidationMode`|<span data-ttu-id="f0570-121">Kimlik bilgilerini doğrulamak için kullanılan üç moddan birini belirtir.</span><span class="sxs-lookup"><span data-stu-id="f0570-121">Specifies one of three modes used to validate credentials.</span></span> <span data-ttu-id="f0570-122">Olarak `Custom`ayarlanırsa, bir `customCertificateValidator` de sağlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f0570-122">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span>|  
|`revocationMode`|<span data-ttu-id="f0570-123">İptal edilen bir sertifika listesini (CRL) denetlemek için kullanılan modlardan biri.</span><span class="sxs-lookup"><span data-stu-id="f0570-123">One of the modes used to check for a revoked certificate lists (CRL).</span></span>|  
|`trustedStoreLocation`|<span data-ttu-id="f0570-124">İki sistem depolama konumlarından biri: `LocalMachine` veya. `CurrentUser`</span><span class="sxs-lookup"><span data-stu-id="f0570-124">One of the two system store locations: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="f0570-125">Bu değer, bir hizmet sertifikası istemciye anlaşılırken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f0570-125">This value is used when a service certificate is negotiated to the client.</span></span> <span data-ttu-id="f0570-126">Doğrulama, belirtilen depo konumundaki **güvenilir kişiler** deposuna göre gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="f0570-126">Validation is performed against the **Trusted People** store in the specified store location.</span></span>|  
  
## <a name="customcertificatevalidatortype-attribute"></a><span data-ttu-id="f0570-127">Customcercertificate Atevalidatortype özniteliği</span><span class="sxs-lookup"><span data-stu-id="f0570-127">customCertificateValidatorType Attribute</span></span>  
  
|<span data-ttu-id="f0570-128">Değer</span><span class="sxs-lookup"><span data-stu-id="f0570-128">Value</span></span>|<span data-ttu-id="f0570-129">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f0570-129">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="f0570-130">Dize</span><span class="sxs-lookup"><span data-stu-id="f0570-130">String</span></span>|<span data-ttu-id="f0570-131">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="f0570-131">Optional.</span></span> <span data-ttu-id="f0570-132">Türü bulmak için kullanılan tür adını ve derlemeyi ve diğer verileri belirtir.</span><span class="sxs-lookup"><span data-stu-id="f0570-132">Specifies the type name and assembly and other data used to find the type.</span></span> <span data-ttu-id="f0570-133">En azından, bir ad alanı ve tür adı gereklidir.</span><span class="sxs-lookup"><span data-stu-id="f0570-133">At minimum, a namespace and type name are required.</span></span> <span data-ttu-id="f0570-134">İsteğe bağlı bilgiler şunları içerir: derleme adı, sürüm numarası, kültür ve ortak anahtar belirteci.</span><span class="sxs-lookup"><span data-stu-id="f0570-134">Optional information includes: assembly name, version number, culture, and public key token.</span></span>|  
  
## <a name="certificatevalidationmode-attribute"></a><span data-ttu-id="f0570-135">certificateValidationMode özniteliği</span><span class="sxs-lookup"><span data-stu-id="f0570-135">certificateValidationMode Attribute</span></span>  
  
|<span data-ttu-id="f0570-136">Değer</span><span class="sxs-lookup"><span data-stu-id="f0570-136">Value</span></span>|<span data-ttu-id="f0570-137">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f0570-137">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="f0570-138">Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="f0570-138">Enumeration</span></span>|<span data-ttu-id="f0570-139">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="f0570-139">Optional.</span></span> <span data-ttu-id="f0570-140">Aşağıdaki değerlerden biri: `None`, `PeerTrust`, `ChainTrust` `PeerOrChainTrust`, ,`Custom`.</span><span class="sxs-lookup"><span data-stu-id="f0570-140">One of the following values: `None`, `PeerTrust`, `ChainTrust`, `PeerOrChainTrust`, `Custom`.</span></span> <span data-ttu-id="f0570-141">Varsayılan, `ChainTrust` değeridir.</span><span class="sxs-lookup"><span data-stu-id="f0570-141">The default is `ChainTrust`.</span></span> <span data-ttu-id="f0570-142">Varsayılan, `ChainTrust` değeridir.</span><span class="sxs-lookup"><span data-stu-id="f0570-142">The default is `ChainTrust`.</span></span><br /><br /> <span data-ttu-id="f0570-143">Daha fazla bilgi için bkz. [sertifikalarla çalışma](../../../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="f0570-143">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="revocationmode-attribute"></a><span data-ttu-id="f0570-144">revocationMode özniteliği</span><span class="sxs-lookup"><span data-stu-id="f0570-144">revocationMode Attribute</span></span>  
  
|<span data-ttu-id="f0570-145">Değer</span><span class="sxs-lookup"><span data-stu-id="f0570-145">Value</span></span>|<span data-ttu-id="f0570-146">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f0570-146">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="f0570-147">Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="f0570-147">Enumeration</span></span>|<span data-ttu-id="f0570-148">Aşağıdaki değerlerden biri: `NoCheck`, `Online`, `Offline`.</span><span class="sxs-lookup"><span data-stu-id="f0570-148">One of the following values: `NoCheck`, `Online`, `Offline`.</span></span> <span data-ttu-id="f0570-149">Varsayılan, `Online` değeridir.</span><span class="sxs-lookup"><span data-stu-id="f0570-149">The default is `Online`.</span></span><br /><br /> <span data-ttu-id="f0570-150">Daha fazla bilgi için bkz. [sertifikalarla çalışma](../../../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="f0570-150">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="trustedstorelocation-attribute"></a><span data-ttu-id="f0570-151">trustedStoreLocation özniteliği</span><span class="sxs-lookup"><span data-stu-id="f0570-151">trustedStoreLocation Attribute</span></span>  
  
|<span data-ttu-id="f0570-152">Değer</span><span class="sxs-lookup"><span data-stu-id="f0570-152">Value</span></span>|<span data-ttu-id="f0570-153">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f0570-153">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="f0570-154">Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="f0570-154">Enumeration</span></span>|<span data-ttu-id="f0570-155">Şu değerlerden biri: `LocalMachine` veya. `CurrentUser`</span><span class="sxs-lookup"><span data-stu-id="f0570-155">One of the following values: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="f0570-156">Varsayılan, `CurrentUser` değeridir.</span><span class="sxs-lookup"><span data-stu-id="f0570-156">The default is `CurrentUser`.</span></span> <span data-ttu-id="f0570-157">İstemci uygulaması bir sistem hesabı altında çalışıyorsa, sertifika genellikle altında `LocalMachine`olur.</span><span class="sxs-lookup"><span data-stu-id="f0570-157">If the client application is running under a system account then the certificate is typically under `LocalMachine`.</span></span> <span data-ttu-id="f0570-158">İstemci uygulaması bir kullanıcı hesabı altında çalışıyorsa, sertifika genellikle içinde `CurrentUser`olur.</span><span class="sxs-lookup"><span data-stu-id="f0570-158">If the client application is running under a user account then the certificate is typically in `CurrentUser`.</span></span> <span data-ttu-id="f0570-159">Varsayılan, `CurrentUser` değeridir.</span><span class="sxs-lookup"><span data-stu-id="f0570-159">The default is `CurrentUser`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f0570-160">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="f0570-160">Child Elements</span></span>  
 <span data-ttu-id="f0570-161">Yok.</span><span class="sxs-lookup"><span data-stu-id="f0570-161">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f0570-162">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="f0570-162">Parent Elements</span></span>  
  
|<span data-ttu-id="f0570-163">Öğe</span><span class="sxs-lookup"><span data-stu-id="f0570-163">Element</span></span>|<span data-ttu-id="f0570-164">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f0570-164">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f0570-165">\<eş ></span><span class="sxs-lookup"><span data-stu-id="f0570-165">\<peer></span></span>](peer-of-clientcredentials-element.md)|<span data-ttu-id="f0570-166">İstemcinin kimliğini bir eş hizmette doğrulamak için kullanılan kimlik bilgisini belirtir.</span><span class="sxs-lookup"><span data-stu-id="f0570-166">Specifies a credential used for authenticating the client to a peer service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f0570-167">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f0570-167">Remarks</span></span>  
 <span data-ttu-id="f0570-168">İleti kimlik doğrulaması seçilirse, bu öğenin yapılandırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="f0570-168">This element must be configured if message authentication is chosen.</span></span> <span data-ttu-id="f0570-169">Çıkış kanalları için her ileti, [ \<sertifika >](certificate-element.md)tarafından belirtilen sertifika kullanılarak imzalanır.</span><span class="sxs-lookup"><span data-stu-id="f0570-169">For output channels, each message is signed using the certificate provided by [\<certificate>](certificate-element.md).</span></span> <span data-ttu-id="f0570-170">Uygulamaya teslim edilmeden önce tüm iletiler, bu öğenin `customCertificateValidatorType` özniteliği tarafından belirtilen Doğrulayıcı kullanılarak ileti kimlik bilgisine karşı denetlenir.</span><span class="sxs-lookup"><span data-stu-id="f0570-170">All messages, before delivered to the application, are checked against the message credential using the validator specified by the `customCertificateValidatorType` attribute of this element.</span></span> <span data-ttu-id="f0570-171">Doğrulayıcı kimlik bilgisini kabul edebilir veya reddedebilir.</span><span class="sxs-lookup"><span data-stu-id="f0570-171">The validator can either accept or reject the credential.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f0570-172">Örnek</span><span class="sxs-lookup"><span data-stu-id="f0570-172">Example</span></span>  
 <span data-ttu-id="f0570-173">Aşağıdaki kod ileti gönderici doğrulama modunu olarak `PeerOrChainTrust`ayarlar.</span><span class="sxs-lookup"><span data-stu-id="f0570-173">The following code sets the message sender validation mode to `PeerOrChainTrust`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f0570-174">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f0570-174">See also</span></span>

- <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>
- <xref:System.ServiceModel.Security.PeerCredential.MessageSenderAuthentication%2A>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement.MessageSenderAuthentication%2A>
- <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>
- [<span data-ttu-id="f0570-175">Sertifikalarla Çalışma</span><span class="sxs-lookup"><span data-stu-id="f0570-175">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="f0570-176">Eşler Arası Ağ</span><span class="sxs-lookup"><span data-stu-id="f0570-176">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
- <span data-ttu-id="f0570-177">[Eş kanal Iletisi kimlik doğrulaması](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="f0570-177">[Peer Channel Message Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="f0570-178">[Eş kanal özel kimlik doğrulaması](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="f0570-178">[Peer Channel Custom Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="f0570-179">Eş Kanalı Uygulamalarını Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="f0570-179">Securing Peer Channel Applications</span></span>](../../../wcf/feature-details/securing-peer-channel-applications.md)
