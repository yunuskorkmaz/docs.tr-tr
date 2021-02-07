---
description: 'Daha fazla bilgi edinin: <messageSenderAuthentication> öğesi'
title: <messageSenderAuthentication> öğesi
ms.date: 03/30/2017
ms.assetid: 8d979dfc-a6f9-42ec-96d5-7fbc13a48118
ms.openlocfilehash: 03c1cd626e7c3ad71026c076df3d757419810d74
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99749343"
---
# <a name="messagesenderauthentication-element"></a><span data-ttu-id="44460-103">\<messageSenderAuthentication> öğesi</span><span class="sxs-lookup"><span data-stu-id="44460-103">\<messageSenderAuthentication> element</span></span>

<span data-ttu-id="44460-104">Eşler arası ileti gönderenler için kimlik doğrulama seçeneklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="44460-104">Specifies authentication options for peer-to-peer message senders.</span></span>  
  
 <span data-ttu-id="44460-105">Eşler arası programlama hakkında daha fazla bilgi için bkz. eşler [arası ağ iletişimi](../../../wcf/feature-details/peer-to-peer-networking.md).</span><span class="sxs-lookup"><span data-stu-id="44460-105">For more information about peer-to-peer programming, see [Peer-to-Peer Networking](../../../wcf/feature-details/peer-to-peer-networking.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<peer>**](peer-of-clientcredentials-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<messageSenderAuthentication>**  
  
## <a name="syntax"></a><span data-ttu-id="44460-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="44460-106">Syntax</span></span>  
  
```xml  
<messageSenderAuthentication customCertificateValidatorType= "namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"
                             certificateValidationMode = "ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"
                             revocationMode="NoCheck/Online/Offline"
                             trustedStoreLocation="CurrentUser/LocalMachine" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="44460-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="44460-107">Attributes and Elements</span></span>  

 <span data-ttu-id="44460-108">Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır</span><span class="sxs-lookup"><span data-stu-id="44460-108">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="44460-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="44460-109">Attributes</span></span>  
  
|<span data-ttu-id="44460-110">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="44460-110">Attribute</span></span>|<span data-ttu-id="44460-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="44460-111">Description</span></span>|  
|---------------|-----------------|  
|`customCertificateValidatorType`|<span data-ttu-id="44460-112">Özel bir türü doğrulamak için kullanılan tür ve derleme.</span><span class="sxs-lookup"><span data-stu-id="44460-112">A type and assembly used to validate a custom type.</span></span> <span data-ttu-id="44460-113">Bu öznitelik `certificateValidationMode` , olarak ayarlandığında ayarlanmalıdır `Custom` .</span><span class="sxs-lookup"><span data-stu-id="44460-113">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span>|  
|`certificateValidationMode`|<span data-ttu-id="44460-114">Kimlik bilgilerini doğrulamak için kullanılan üç moddan birini belirtir.</span><span class="sxs-lookup"><span data-stu-id="44460-114">Specifies one of three modes used to validate credentials.</span></span> <span data-ttu-id="44460-115">Olarak ayarlanırsa `Custom` , bir `customCertificateValidator` de sağlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="44460-115">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span>|  
|`revocationMode`|<span data-ttu-id="44460-116">İptal edilen bir sertifika listesini (CRL) denetlemek için kullanılan modlardan biri.</span><span class="sxs-lookup"><span data-stu-id="44460-116">One of the modes used to check for a revoked certificate lists (CRL).</span></span>|  
|`trustedStoreLocation`|<span data-ttu-id="44460-117">İki sistem depolama konumlarından biri: `LocalMachine` veya `CurrentUser` .</span><span class="sxs-lookup"><span data-stu-id="44460-117">One of the two system store locations: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="44460-118">Bu değer, bir hizmet sertifikası istemciye anlaşılırken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="44460-118">This value is used when a service certificate is negotiated to the client.</span></span> <span data-ttu-id="44460-119">Doğrulama, belirtilen depo konumundaki **güvenilir kişiler** deposuna göre gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="44460-119">Validation is performed against the **Trusted People** store in the specified store location.</span></span>|  
  
## <a name="customcertificatevalidatortype-attribute"></a><span data-ttu-id="44460-120">Customcercertificate Atevalidatortype özniteliği</span><span class="sxs-lookup"><span data-stu-id="44460-120">customCertificateValidatorType Attribute</span></span>  
  
|<span data-ttu-id="44460-121">Değer</span><span class="sxs-lookup"><span data-stu-id="44460-121">Value</span></span>|<span data-ttu-id="44460-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="44460-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="44460-123">Dize</span><span class="sxs-lookup"><span data-stu-id="44460-123">String</span></span>|<span data-ttu-id="44460-124">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="44460-124">Optional.</span></span> <span data-ttu-id="44460-125">Türü bulmak için kullanılan tür adını ve derlemeyi ve diğer verileri belirtir.</span><span class="sxs-lookup"><span data-stu-id="44460-125">Specifies the type name and assembly and other data used to find the type.</span></span> <span data-ttu-id="44460-126">En azından, bir ad alanı ve tür adı gereklidir.</span><span class="sxs-lookup"><span data-stu-id="44460-126">At minimum, a namespace and type name are required.</span></span> <span data-ttu-id="44460-127">İsteğe bağlı bilgiler şunları içerir: derleme adı, sürüm numarası, kültür ve ortak anahtar belirteci.</span><span class="sxs-lookup"><span data-stu-id="44460-127">Optional information includes: assembly name, version number, culture, and public key token.</span></span>|  
  
## <a name="certificatevalidationmode-attribute"></a><span data-ttu-id="44460-128">certificateValidationMode özniteliği</span><span class="sxs-lookup"><span data-stu-id="44460-128">certificateValidationMode Attribute</span></span>  
  
|<span data-ttu-id="44460-129">Değer</span><span class="sxs-lookup"><span data-stu-id="44460-129">Value</span></span>|<span data-ttu-id="44460-130">Açıklama</span><span class="sxs-lookup"><span data-stu-id="44460-130">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="44460-131">Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="44460-131">Enumeration</span></span>|<span data-ttu-id="44460-132">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="44460-132">Optional.</span></span> <span data-ttu-id="44460-133">Aşağıdaki değerlerden biri: `None` ,,, `PeerTrust` `ChainTrust` `PeerOrChainTrust` , `Custom` .</span><span class="sxs-lookup"><span data-stu-id="44460-133">One of the following values: `None`, `PeerTrust`, `ChainTrust`, `PeerOrChainTrust`, `Custom`.</span></span> <span data-ttu-id="44460-134">Varsayılan değer: `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="44460-134">The default is `ChainTrust`.</span></span> <span data-ttu-id="44460-135">Varsayılan değer: `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="44460-135">The default is `ChainTrust`.</span></span><br /><br /> <span data-ttu-id="44460-136">Daha fazla bilgi için bkz. [sertifikalarla çalışma](../../../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="44460-136">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="revocationmode-attribute"></a><span data-ttu-id="44460-137">revocationMode özniteliği</span><span class="sxs-lookup"><span data-stu-id="44460-137">revocationMode Attribute</span></span>  
  
|<span data-ttu-id="44460-138">Değer</span><span class="sxs-lookup"><span data-stu-id="44460-138">Value</span></span>|<span data-ttu-id="44460-139">Açıklama</span><span class="sxs-lookup"><span data-stu-id="44460-139">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="44460-140">Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="44460-140">Enumeration</span></span>|<span data-ttu-id="44460-141">Aşağıdaki değerlerden biri: `NoCheck` , `Online` , `Offline` .</span><span class="sxs-lookup"><span data-stu-id="44460-141">One of the following values: `NoCheck`, `Online`, `Offline`.</span></span> <span data-ttu-id="44460-142">Varsayılan değer: `Online`.</span><span class="sxs-lookup"><span data-stu-id="44460-142">The default is `Online`.</span></span><br /><br /> <span data-ttu-id="44460-143">Daha fazla bilgi için bkz. [sertifikalarla çalışma](../../../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="44460-143">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="trustedstorelocation-attribute"></a><span data-ttu-id="44460-144">trustedStoreLocation özniteliği</span><span class="sxs-lookup"><span data-stu-id="44460-144">trustedStoreLocation Attribute</span></span>  
  
|<span data-ttu-id="44460-145">Değer</span><span class="sxs-lookup"><span data-stu-id="44460-145">Value</span></span>|<span data-ttu-id="44460-146">Açıklama</span><span class="sxs-lookup"><span data-stu-id="44460-146">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="44460-147">Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="44460-147">Enumeration</span></span>|<span data-ttu-id="44460-148">Şu değerlerden biri: `LocalMachine` veya `CurrentUser` .</span><span class="sxs-lookup"><span data-stu-id="44460-148">One of the following values: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="44460-149">Varsayılan değer: `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="44460-149">The default is `CurrentUser`.</span></span> <span data-ttu-id="44460-150">İstemci uygulaması bir sistem hesabı altında çalışıyorsa, sertifika genellikle altında olur `LocalMachine` .</span><span class="sxs-lookup"><span data-stu-id="44460-150">If the client application is running under a system account then the certificate is typically under `LocalMachine`.</span></span> <span data-ttu-id="44460-151">İstemci uygulaması bir kullanıcı hesabı altında çalışıyorsa, sertifika genellikle içinde olur `CurrentUser` .</span><span class="sxs-lookup"><span data-stu-id="44460-151">If the client application is running under a user account then the certificate is typically in `CurrentUser`.</span></span> <span data-ttu-id="44460-152">Varsayılan değer: `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="44460-152">The default is `CurrentUser`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="44460-153">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="44460-153">Child Elements</span></span>  

 <span data-ttu-id="44460-154">Yok.</span><span class="sxs-lookup"><span data-stu-id="44460-154">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="44460-155">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="44460-155">Parent Elements</span></span>  
  
|<span data-ttu-id="44460-156">Öğe</span><span class="sxs-lookup"><span data-stu-id="44460-156">Element</span></span>|<span data-ttu-id="44460-157">Açıklama</span><span class="sxs-lookup"><span data-stu-id="44460-157">Description</span></span>|  
|-------------|-----------------|  
|[\<peer>](peer-of-clientcredentials-element.md)|<span data-ttu-id="44460-158">İstemcinin kimliğini bir eş hizmette doğrulamak için kullanılan kimlik bilgisini belirtir.</span><span class="sxs-lookup"><span data-stu-id="44460-158">Specifies a credential used for authenticating the client to a peer service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="44460-159">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="44460-159">Remarks</span></span>  

 <span data-ttu-id="44460-160">İleti kimlik doğrulaması seçilirse, bu öğenin yapılandırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="44460-160">This element must be configured if message authentication is chosen.</span></span> <span data-ttu-id="44460-161">Çıkış kanalları için, her ileti tarafından belirtilen sertifika kullanılarak imzalanır [\<certificate>](certificate-element.md) .</span><span class="sxs-lookup"><span data-stu-id="44460-161">For output channels, each message is signed using the certificate provided by [\<certificate>](certificate-element.md).</span></span> <span data-ttu-id="44460-162">Uygulamaya teslim edilmeden önce tüm iletiler, bu öğenin özniteliği tarafından belirtilen Doğrulayıcı kullanılarak ileti kimlik bilgisine karşı denetlenir `customCertificateValidatorType` .</span><span class="sxs-lookup"><span data-stu-id="44460-162">All messages, before delivered to the application, are checked against the message credential using the validator specified by the `customCertificateValidatorType` attribute of this element.</span></span> <span data-ttu-id="44460-163">Doğrulayıcı kimlik bilgisini kabul edebilir veya reddedebilir.</span><span class="sxs-lookup"><span data-stu-id="44460-163">The validator can either accept or reject the credential.</span></span>  
  
## <a name="example"></a><span data-ttu-id="44460-164">Örnek</span><span class="sxs-lookup"><span data-stu-id="44460-164">Example</span></span>  

 <span data-ttu-id="44460-165">Aşağıdaki kod ileti gönderici doğrulama modunu olarak ayarlar `PeerOrChainTrust` .</span><span class="sxs-lookup"><span data-stu-id="44460-165">The following code sets the message sender validation mode to `PeerOrChainTrust`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="44460-166">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="44460-166">See also</span></span>

- <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>
- <xref:System.ServiceModel.Security.PeerCredential.MessageSenderAuthentication%2A>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement.MessageSenderAuthentication%2A>
- <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>
- [<span data-ttu-id="44460-167">Sertifikalarla Çalışma</span><span class="sxs-lookup"><span data-stu-id="44460-167">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="44460-168">Eşler Arası Ağ</span><span class="sxs-lookup"><span data-stu-id="44460-168">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
- <span data-ttu-id="44460-169">[Eş kanal Iletisi kimlik doğrulaması](/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="44460-169">[Peer Channel Message Authentication](/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="44460-170">[Eş kanal özel kimlik doğrulaması](/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="44460-170">[Peer Channel Custom Authentication](/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="44460-171">Eş Kanalı Uygulamalarını Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="44460-171">Securing Peer Channel Applications</span></span>](../../../wcf/feature-details/securing-peer-channel-applications.md)
