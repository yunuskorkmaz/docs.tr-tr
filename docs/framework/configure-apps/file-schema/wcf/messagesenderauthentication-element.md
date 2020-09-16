---
title: <messageSenderAuthentication> öğesi
ms.date: 03/30/2017
ms.assetid: 8d979dfc-a6f9-42ec-96d5-7fbc13a48118
ms.openlocfilehash: 3693b2b4c6b6cbc3705a25967aedc88e36291407
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90547017"
---
# <a name="messagesenderauthentication-element"></a><span data-ttu-id="7e673-102">\<messageSenderAuthentication> öğesi</span><span class="sxs-lookup"><span data-stu-id="7e673-102">\<messageSenderAuthentication> element</span></span>
<span data-ttu-id="7e673-103">Eşler arası ileti gönderenler için kimlik doğrulama seçeneklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="7e673-103">Specifies authentication options for peer-to-peer message senders.</span></span>  
  
 <span data-ttu-id="7e673-104">Eşler arası programlama hakkında daha fazla bilgi için bkz. eşler [arası ağ iletişimi](../../../wcf/feature-details/peer-to-peer-networking.md).</span><span class="sxs-lookup"><span data-stu-id="7e673-104">For more information about peer-to-peer programming, see [Peer-to-Peer Networking](../../../wcf/feature-details/peer-to-peer-networking.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<peer>**](peer-of-clientcredentials-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<messageSenderAuthentication>**  
  
## <a name="syntax"></a><span data-ttu-id="7e673-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="7e673-105">Syntax</span></span>  
  
```xml  
<messageSenderAuthentication customCertificateValidatorType= "namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"
                             certificateValidationMode = "ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"
                             revocationMode="NoCheck/Online/Offline"
                             trustedStoreLocation="CurrentUser/LocalMachine" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7e673-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="7e673-106">Attributes and Elements</span></span>  
 <span data-ttu-id="7e673-107">Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır</span><span class="sxs-lookup"><span data-stu-id="7e673-107">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7e673-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="7e673-108">Attributes</span></span>  
  
|<span data-ttu-id="7e673-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="7e673-109">Attribute</span></span>|<span data-ttu-id="7e673-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7e673-110">Description</span></span>|  
|---------------|-----------------|  
|`customCertificateValidatorType`|<span data-ttu-id="7e673-111">Özel bir türü doğrulamak için kullanılan tür ve derleme.</span><span class="sxs-lookup"><span data-stu-id="7e673-111">A type and assembly used to validate a custom type.</span></span> <span data-ttu-id="7e673-112">Bu öznitelik `certificateValidationMode` , olarak ayarlandığında ayarlanmalıdır `Custom` .</span><span class="sxs-lookup"><span data-stu-id="7e673-112">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span>|  
|`certificateValidationMode`|<span data-ttu-id="7e673-113">Kimlik bilgilerini doğrulamak için kullanılan üç moddan birini belirtir.</span><span class="sxs-lookup"><span data-stu-id="7e673-113">Specifies one of three modes used to validate credentials.</span></span> <span data-ttu-id="7e673-114">Olarak ayarlanırsa `Custom` , bir `customCertificateValidator` de sağlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7e673-114">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span>|  
|`revocationMode`|<span data-ttu-id="7e673-115">İptal edilen bir sertifika listesini (CRL) denetlemek için kullanılan modlardan biri.</span><span class="sxs-lookup"><span data-stu-id="7e673-115">One of the modes used to check for a revoked certificate lists (CRL).</span></span>|  
|`trustedStoreLocation`|<span data-ttu-id="7e673-116">İki sistem depolama konumlarından biri: `LocalMachine` veya `CurrentUser` .</span><span class="sxs-lookup"><span data-stu-id="7e673-116">One of the two system store locations: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="7e673-117">Bu değer, bir hizmet sertifikası istemciye anlaşılırken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7e673-117">This value is used when a service certificate is negotiated to the client.</span></span> <span data-ttu-id="7e673-118">Doğrulama, belirtilen depo konumundaki **güvenilir kişiler** deposuna göre gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="7e673-118">Validation is performed against the **Trusted People** store in the specified store location.</span></span>|  
  
## <a name="customcertificatevalidatortype-attribute"></a><span data-ttu-id="7e673-119">Customcercertificate Atevalidatortype özniteliği</span><span class="sxs-lookup"><span data-stu-id="7e673-119">customCertificateValidatorType Attribute</span></span>  
  
|<span data-ttu-id="7e673-120">Değer</span><span class="sxs-lookup"><span data-stu-id="7e673-120">Value</span></span>|<span data-ttu-id="7e673-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7e673-121">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="7e673-122">Dize</span><span class="sxs-lookup"><span data-stu-id="7e673-122">String</span></span>|<span data-ttu-id="7e673-123">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="7e673-123">Optional.</span></span> <span data-ttu-id="7e673-124">Türü bulmak için kullanılan tür adını ve derlemeyi ve diğer verileri belirtir.</span><span class="sxs-lookup"><span data-stu-id="7e673-124">Specifies the type name and assembly and other data used to find the type.</span></span> <span data-ttu-id="7e673-125">En azından, bir ad alanı ve tür adı gereklidir.</span><span class="sxs-lookup"><span data-stu-id="7e673-125">At minimum, a namespace and type name are required.</span></span> <span data-ttu-id="7e673-126">İsteğe bağlı bilgiler şunları içerir: derleme adı, sürüm numarası, kültür ve ortak anahtar belirteci.</span><span class="sxs-lookup"><span data-stu-id="7e673-126">Optional information includes: assembly name, version number, culture, and public key token.</span></span>|  
  
## <a name="certificatevalidationmode-attribute"></a><span data-ttu-id="7e673-127">certificateValidationMode özniteliği</span><span class="sxs-lookup"><span data-stu-id="7e673-127">certificateValidationMode Attribute</span></span>  
  
|<span data-ttu-id="7e673-128">Değer</span><span class="sxs-lookup"><span data-stu-id="7e673-128">Value</span></span>|<span data-ttu-id="7e673-129">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7e673-129">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="7e673-130">Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="7e673-130">Enumeration</span></span>|<span data-ttu-id="7e673-131">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="7e673-131">Optional.</span></span> <span data-ttu-id="7e673-132">Aşağıdaki değerlerden biri: `None` ,,, `PeerTrust` `ChainTrust` `PeerOrChainTrust` , `Custom` .</span><span class="sxs-lookup"><span data-stu-id="7e673-132">One of the following values: `None`, `PeerTrust`, `ChainTrust`, `PeerOrChainTrust`, `Custom`.</span></span> <span data-ttu-id="7e673-133">Varsayılan değer: `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="7e673-133">The default is `ChainTrust`.</span></span> <span data-ttu-id="7e673-134">Varsayılan değer: `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="7e673-134">The default is `ChainTrust`.</span></span><br /><br /> <span data-ttu-id="7e673-135">Daha fazla bilgi için bkz. [sertifikalarla çalışma](../../../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="7e673-135">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="revocationmode-attribute"></a><span data-ttu-id="7e673-136">revocationMode özniteliği</span><span class="sxs-lookup"><span data-stu-id="7e673-136">revocationMode Attribute</span></span>  
  
|<span data-ttu-id="7e673-137">Değer</span><span class="sxs-lookup"><span data-stu-id="7e673-137">Value</span></span>|<span data-ttu-id="7e673-138">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7e673-138">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="7e673-139">Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="7e673-139">Enumeration</span></span>|<span data-ttu-id="7e673-140">Aşağıdaki değerlerden biri: `NoCheck` , `Online` , `Offline` .</span><span class="sxs-lookup"><span data-stu-id="7e673-140">One of the following values: `NoCheck`, `Online`, `Offline`.</span></span> <span data-ttu-id="7e673-141">Varsayılan değer: `Online`.</span><span class="sxs-lookup"><span data-stu-id="7e673-141">The default is `Online`.</span></span><br /><br /> <span data-ttu-id="7e673-142">Daha fazla bilgi için bkz. [sertifikalarla çalışma](../../../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="7e673-142">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="trustedstorelocation-attribute"></a><span data-ttu-id="7e673-143">trustedStoreLocation özniteliği</span><span class="sxs-lookup"><span data-stu-id="7e673-143">trustedStoreLocation Attribute</span></span>  
  
|<span data-ttu-id="7e673-144">Değer</span><span class="sxs-lookup"><span data-stu-id="7e673-144">Value</span></span>|<span data-ttu-id="7e673-145">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7e673-145">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="7e673-146">Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="7e673-146">Enumeration</span></span>|<span data-ttu-id="7e673-147">Şu değerlerden biri: `LocalMachine` veya `CurrentUser` .</span><span class="sxs-lookup"><span data-stu-id="7e673-147">One of the following values: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="7e673-148">Varsayılan değer: `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="7e673-148">The default is `CurrentUser`.</span></span> <span data-ttu-id="7e673-149">İstemci uygulaması bir sistem hesabı altında çalışıyorsa, sertifika genellikle altında olur `LocalMachine` .</span><span class="sxs-lookup"><span data-stu-id="7e673-149">If the client application is running under a system account then the certificate is typically under `LocalMachine`.</span></span> <span data-ttu-id="7e673-150">İstemci uygulaması bir kullanıcı hesabı altında çalışıyorsa, sertifika genellikle içinde olur `CurrentUser` .</span><span class="sxs-lookup"><span data-stu-id="7e673-150">If the client application is running under a user account then the certificate is typically in `CurrentUser`.</span></span> <span data-ttu-id="7e673-151">Varsayılan değer: `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="7e673-151">The default is `CurrentUser`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7e673-152">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="7e673-152">Child Elements</span></span>  
 <span data-ttu-id="7e673-153">Yok.</span><span class="sxs-lookup"><span data-stu-id="7e673-153">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7e673-154">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="7e673-154">Parent Elements</span></span>  
  
|<span data-ttu-id="7e673-155">Öğe</span><span class="sxs-lookup"><span data-stu-id="7e673-155">Element</span></span>|<span data-ttu-id="7e673-156">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7e673-156">Description</span></span>|  
|-------------|-----------------|  
|[\<peer>](peer-of-clientcredentials-element.md)|<span data-ttu-id="7e673-157">İstemcinin kimliğini bir eş hizmette doğrulamak için kullanılan kimlik bilgisini belirtir.</span><span class="sxs-lookup"><span data-stu-id="7e673-157">Specifies a credential used for authenticating the client to a peer service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7e673-158">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7e673-158">Remarks</span></span>  
 <span data-ttu-id="7e673-159">İleti kimlik doğrulaması seçilirse, bu öğenin yapılandırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="7e673-159">This element must be configured if message authentication is chosen.</span></span> <span data-ttu-id="7e673-160">Çıkış kanalları için, her ileti tarafından belirtilen sertifika kullanılarak imzalanır [\<certificate>](certificate-element.md) .</span><span class="sxs-lookup"><span data-stu-id="7e673-160">For output channels, each message is signed using the certificate provided by [\<certificate>](certificate-element.md).</span></span> <span data-ttu-id="7e673-161">Uygulamaya teslim edilmeden önce tüm iletiler, bu öğenin özniteliği tarafından belirtilen Doğrulayıcı kullanılarak ileti kimlik bilgisine karşı denetlenir `customCertificateValidatorType` .</span><span class="sxs-lookup"><span data-stu-id="7e673-161">All messages, before delivered to the application, are checked against the message credential using the validator specified by the `customCertificateValidatorType` attribute of this element.</span></span> <span data-ttu-id="7e673-162">Doğrulayıcı kimlik bilgisini kabul edebilir veya reddedebilir.</span><span class="sxs-lookup"><span data-stu-id="7e673-162">The validator can either accept or reject the credential.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7e673-163">Örnek</span><span class="sxs-lookup"><span data-stu-id="7e673-163">Example</span></span>  
 <span data-ttu-id="7e673-164">Aşağıdaki kod ileti gönderici doğrulama modunu olarak ayarlar `PeerOrChainTrust` .</span><span class="sxs-lookup"><span data-stu-id="7e673-164">The following code sets the message sender validation mode to `PeerOrChainTrust`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7e673-165">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7e673-165">See also</span></span>

- <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>
- <xref:System.ServiceModel.Security.PeerCredential.MessageSenderAuthentication%2A>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement.MessageSenderAuthentication%2A>
- <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>
- [<span data-ttu-id="7e673-166">Sertifikalarla Çalışma</span><span class="sxs-lookup"><span data-stu-id="7e673-166">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="7e673-167">Eşler Arası Ağ</span><span class="sxs-lookup"><span data-stu-id="7e673-167">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
- <span data-ttu-id="7e673-168">[Eş kanal Iletisi kimlik doğrulaması](/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="7e673-168">[Peer Channel Message Authentication](/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="7e673-169">[Eş kanal özel kimlik doğrulaması](/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="7e673-169">[Peer Channel Custom Authentication](/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="7e673-170">Eş Kanalı Uygulamalarını Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="7e673-170">Securing Peer Channel Applications</span></span>](../../../wcf/feature-details/securing-peer-channel-applications.md)
