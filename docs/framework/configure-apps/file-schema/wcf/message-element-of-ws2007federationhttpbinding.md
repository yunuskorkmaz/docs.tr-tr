---
title: <message> öğesi <ws2007FederationHttpBinding>
ms.date: 03/30/2017
ms.assetid: 52cd941d-e230-4c82-8b29-333a7d20eca8
ms.openlocfilehash: f05bd90bd2e4c7e1fd606518d9e5cb8d4e5ad974
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59093000"
---
# <a name="message-element-of-ws2007federationhttpbinding"></a><span data-ttu-id="984cd-102">\<İleti > öğesi \<ws2007FederationHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="984cd-102">\<message> element of \<ws2007FederationHttpBinding></span></span>
<span data-ttu-id="984cd-103">İleti düzeyi güvenlik ayarlarını tanımlar [ \<ws2007FederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007federationhttpbinding.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="984cd-103">Defines settings for the message-level security for the [\<ws2007FederationHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007federationhttpbinding.md) element.</span></span>  
  
 <span data-ttu-id="984cd-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="984cd-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="984cd-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="984cd-105">\<bindings></span></span>  
<span data-ttu-id="984cd-106">\<ws2007FederationHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="984cd-106">\<ws2007FederationHttpBinding></span></span>  
<span data-ttu-id="984cd-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="984cd-107">\<binding></span></span>  
<span data-ttu-id="984cd-108">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="984cd-108">\<security></span></span>  
<span data-ttu-id="984cd-109">\<İleti ></span><span class="sxs-lookup"><span data-stu-id="984cd-109">\<message></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="984cd-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="984cd-110">Syntax</span></span>  
  
```xml  
<ws2007FederationBinding>
  <binding>
    <security>
      <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
               issuedTokenType="string"
               issuedKeyType="SymmetricKey/PublicKey"
               negotiateServiceCredential="Boolean">
        <claimTypeRequirements>
          <add claimType="URI"
               isOptional="Boolean" />
        </claimTypeRequirements>
        <issuer address="Uri">
          <headers>
            <add name="String"
                 namespace="String" />
          </headers>
          <identity>
            <certificate encodedValue="String" />
            <certificateReference findValue="String"
                                  isChainIncluded="Boolean"
                                  storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
                                  storeLocation="LocalMachine/CurrentUser"
                                  x509FindType="System.Security.Cryptography.X509certificates.X509findtype" />
            <dns value="String" />
            <rsa value="String" />
            <servicePrincipalName value="String" />
            <usePrincipalName value="String" />
          </identity>
        </issuer>
        <issuerMetadata address="String">
          <headers>
            <add name="String"
                 namespace="String" />
          </headers>
          <identity>
            <certificate encodedValue="String" />
            <certificateReference findValue="String"
                                  isChainIncluded="Boolean"
                                  storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
                                  storeLocation="LocalMachine/CurrentUser"
                                  X509FindType="System.Security.Cryptography.X509certificates.X509findtype" />
            <dns value="String" />
            <rsa value="String" />
            <servicePrincipalName value="String" />
            <usePrincipalName value="String" />
          </identity>
        </issuerMetadata>
        <tokenRequestParameters>
          <xmlElement>
          </xmlElement>
        </tokenRequestParameters>
      </message>
    </security>
  </binding>
</ws2007FederationBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="984cd-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="984cd-111">Attributes and Elements</span></span>  
 <span data-ttu-id="984cd-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="984cd-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="984cd-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="984cd-113">Attributes</span></span>  
  
|<span data-ttu-id="984cd-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="984cd-114">Attribute</span></span>|<span data-ttu-id="984cd-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="984cd-115">Description</span></span>|  
|---------------|-----------------|  
|`algorithmSuite`|<span data-ttu-id="984cd-116">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="984cd-116">Optional.</span></span> <span data-ttu-id="984cd-117">İleti şifreleme, imza ve anahtar-wrap algoritmaları ayarlar.</span><span class="sxs-lookup"><span data-stu-id="984cd-117">Sets the message encryption, signature, and key-wrap algorithms.</span></span> <span data-ttu-id="984cd-118">Algoritmalar ve anahtar boyutları tarafından belirlenen <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="984cd-118">The algorithms and the key sizes are determined by the <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> class.</span></span> <span data-ttu-id="984cd-119">Bu algoritmalar, güvenlik ilkesi dili (WS-SecurityPolicy) belirtiminde belirtilen platformlarla eşlenir.</span><span class="sxs-lookup"><span data-stu-id="984cd-119">These algorithms map to those specified in the Security Policy Language (WS-SecurityPolicy) specification.</span></span><br /><br /> <span data-ttu-id="984cd-120">Olası değerler için aşağıdaki tabloya bakın.</span><span class="sxs-lookup"><span data-stu-id="984cd-120">See the following table for possible values.</span></span> <span data-ttu-id="984cd-121">Basic256 varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="984cd-121">The default value is Basic256.</span></span>|  
|`issuedKeyType`|<span data-ttu-id="984cd-122">Kesilecek anahtar türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="984cd-122">Specifies the type of key to be issued.</span></span> <span data-ttu-id="984cd-123">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="984cd-123">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="984cd-124">-   SymmetricKey</span><span class="sxs-lookup"><span data-stu-id="984cd-124">-   SymmetricKey</span></span><br /><span data-ttu-id="984cd-125">-   PublicKey</span><span class="sxs-lookup"><span data-stu-id="984cd-125">-   PublicKey</span></span><br /><span data-ttu-id="984cd-126">-   BearerKey</span><span class="sxs-lookup"><span data-stu-id="984cd-126">-   BearerKey</span></span><br /><br /> <span data-ttu-id="984cd-127">SymmetricKey varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="984cd-127">The default is SymmetricKey.</span></span> <span data-ttu-id="984cd-128">Bu öznitelik türünde <xref:System.IdentityModel.Tokens.SecurityKeyType>.</span><span class="sxs-lookup"><span data-stu-id="984cd-128">This attribute is of type <xref:System.IdentityModel.Tokens.SecurityKeyType>.</span></span>|  
|`issuedTokenType`|<span data-ttu-id="984cd-129">Verilmesi için belirteç türünü belirten bir URI.</span><span class="sxs-lookup"><span data-stu-id="984cd-129">A URI that specifies the type of token to be issued.</span></span> <span data-ttu-id="984cd-130">Varsayılan, `null` değeridir.</span><span class="sxs-lookup"><span data-stu-id="984cd-130">The default is `null`.</span></span>|  
|`negotiateServiceCredential`|<span data-ttu-id="984cd-131">Hizmet kimlik bilgisi anlaşmasının bir parçası değiştirilen veya bant dışından mevcut olup olmadığını belirten bir değeri.</span><span class="sxs-lookup"><span data-stu-id="984cd-131">A value that specifies whether the service credential should be exchanged as part of negotiation or is available out of band.</span></span> <span data-ttu-id="984cd-132">Varsayılan `true`, hizmet kimlik bilgisi anlaşılır anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="984cd-132">The default is `true`, which means that the service credential is negotiated.</span></span>|  
  
## <a name="algorithmsuite-attribute"></a><span data-ttu-id="984cd-133">algorithmSuite özniteliği</span><span class="sxs-lookup"><span data-stu-id="984cd-133">algorithmSuite Attribute</span></span>  
  
|<span data-ttu-id="984cd-134">Değer</span><span class="sxs-lookup"><span data-stu-id="984cd-134">Value</span></span>|<span data-ttu-id="984cd-135">Açıklama</span><span class="sxs-lookup"><span data-stu-id="984cd-135">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="984cd-136">Basic128</span><span class="sxs-lookup"><span data-stu-id="984cd-136">Basic128</span></span>|<span data-ttu-id="984cd-137">İleti özeti için Sha1 ve Rsa oaep mgf1p Aes128 şifreleme anahtarı kaydırma için kullanın.</span><span class="sxs-lookup"><span data-stu-id="984cd-137">Use Aes128 encryption, Sha1 for message digest, and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="984cd-138">Basic192</span><span class="sxs-lookup"><span data-stu-id="984cd-138">Basic192</span></span>|<span data-ttu-id="984cd-139">İleti özeti, anahtar kaydırma için Rsa-oaep mgf1p için Sha1 Aes192 şifrelemesi kullanın.</span><span class="sxs-lookup"><span data-stu-id="984cd-139">Use Aes192 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="984cd-140">Basic256</span><span class="sxs-lookup"><span data-stu-id="984cd-140">Basic256</span></span>|<span data-ttu-id="984cd-141">İleti özeti, anahtar kaydırma için Rsa-oaep mgf1p için Sha1 Aes256 şifrelemesi kullanın.</span><span class="sxs-lookup"><span data-stu-id="984cd-141">Use Aes256 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="984cd-142">Basic256Rsa15</span><span class="sxs-lookup"><span data-stu-id="984cd-142">Basic256Rsa15</span></span>|<span data-ttu-id="984cd-143">İleti şifreleme, ileti özeti için Sha1 ve anahtar kaydırma için Rsa15 Aes256 kullanın.</span><span class="sxs-lookup"><span data-stu-id="984cd-143">Use Aes256 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="984cd-144">Basic192Rsa15</span><span class="sxs-lookup"><span data-stu-id="984cd-144">Basic192Rsa15</span></span>|<span data-ttu-id="984cd-145">İleti şifreleme, ileti özeti için Sha1 ve anahtar kaydırma için Rsa15 Aes192 kullanın.</span><span class="sxs-lookup"><span data-stu-id="984cd-145">Use Aes192 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="984cd-146">TripleDes</span><span class="sxs-lookup"><span data-stu-id="984cd-146">TripleDes</span></span>|<span data-ttu-id="984cd-147">İleti özeti, anahtar kaydırma için Rsa-oaep mgf1p için Sha1 TripleDes şifrelemesi kullanın.</span><span class="sxs-lookup"><span data-stu-id="984cd-147">Use TripleDes encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="984cd-148">Basic128Rsa15</span><span class="sxs-lookup"><span data-stu-id="984cd-148">Basic128Rsa15</span></span>|<span data-ttu-id="984cd-149">İleti özeti için Sha1 ve anahtar kaydırma için Rsa15 ileti şifreleme için Aes128'i kullanın.</span><span class="sxs-lookup"><span data-stu-id="984cd-149">Use Aes128 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="984cd-150">TripleDesRsa15</span><span class="sxs-lookup"><span data-stu-id="984cd-150">TripleDesRsa15</span></span>|<span data-ttu-id="984cd-151">İleti özeti için Sha1 ve anahtar kaydırma için Rsa15 TripleDes şifrelemesi kullanın.</span><span class="sxs-lookup"><span data-stu-id="984cd-151">Use TripleDes encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="984cd-152">Basic128Sha256</span><span class="sxs-lookup"><span data-stu-id="984cd-152">Basic128Sha256</span></span>|<span data-ttu-id="984cd-153">İleti şifreleme, ileti özeti için Sha256 ve anahtar kaydırma için Rsa-oaep mgf1p Aes256 kullanın.</span><span class="sxs-lookup"><span data-stu-id="984cd-153">Use Aes256 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="984cd-154">Basic192Sha256</span><span class="sxs-lookup"><span data-stu-id="984cd-154">Basic192Sha256</span></span>|<span data-ttu-id="984cd-155">İleti şifreleme, ileti özeti için Sha256 ve anahtar kaydırma için Rsa-oaep mgf1p Aes192 kullanın.</span><span class="sxs-lookup"><span data-stu-id="984cd-155">Use Aes192 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="984cd-156">Basic256Sha256</span><span class="sxs-lookup"><span data-stu-id="984cd-156">Basic256Sha256</span></span>|<span data-ttu-id="984cd-157">İleti şifreleme, ileti özeti için Sha256 ve anahtar kaydırma için Rsa-oaep mgf1p Aes256 kullanın.</span><span class="sxs-lookup"><span data-stu-id="984cd-157">Use Aes256 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="984cd-158">TripleDesSha256</span><span class="sxs-lookup"><span data-stu-id="984cd-158">TripleDesSha256</span></span>|<span data-ttu-id="984cd-159">TripleDes ileti özeti için Sha256 ve anahtar kaydırma için Rsa-oaep mgf1p ileti şifreleme için kullanın.</span><span class="sxs-lookup"><span data-stu-id="984cd-159">Use TripleDes for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="984cd-160">Basic128Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="984cd-160">Basic128Sha256Rsa15</span></span>|<span data-ttu-id="984cd-161">İleti özeti için Sha256 ve anahtar kaydırma için Rsa15 ileti şifreleme için Aes128'i kullanın.</span><span class="sxs-lookup"><span data-stu-id="984cd-161">Use Aes128 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="984cd-162">Basic192Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="984cd-162">Basic192Sha256Rsa15</span></span>|<span data-ttu-id="984cd-163">İleti şifreleme, ileti özeti için Sha256 ve anahtar kaydırma için Rsa15 Aes192 kullanın.</span><span class="sxs-lookup"><span data-stu-id="984cd-163">Use Aes192 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="984cd-164">Basic256Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="984cd-164">Basic256Sha256Rsa15</span></span>|<span data-ttu-id="984cd-165">İleti şifreleme, ileti özeti için Sha256 ve anahtar kaydırma için Rsa15 Aes256 kullanın.</span><span class="sxs-lookup"><span data-stu-id="984cd-165">Use Aes256 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="984cd-166">TripleDesSha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="984cd-166">TripleDesSha256Rsa15</span></span>|<span data-ttu-id="984cd-167">TripleDes ileti özeti için Sha256 ve anahtar kaydırma için Rsa15 ileti şifreleme için kullanın.</span><span class="sxs-lookup"><span data-stu-id="984cd-167">Use TripleDes for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="984cd-168">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="984cd-168">Child Elements</span></span>  
  
|<span data-ttu-id="984cd-169">Öğe</span><span class="sxs-lookup"><span data-stu-id="984cd-169">Element</span></span>|<span data-ttu-id="984cd-170">Açıklama</span><span class="sxs-lookup"><span data-stu-id="984cd-170">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="984cd-171">\<claimTypeRequirements ></span><span class="sxs-lookup"><span data-stu-id="984cd-171">\<claimTypeRequirements></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-element.md)|<span data-ttu-id="984cd-172">Bu bağlama için talep türlerinin koleksiyonunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="984cd-172">Specifies a collection of claim types for this binding.</span></span> <span data-ttu-id="984cd-173">Her öğe türünde <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span><span class="sxs-lookup"><span data-stu-id="984cd-173">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span>|  
|[<span data-ttu-id="984cd-174">\<veren ></span><span class="sxs-lookup"><span data-stu-id="984cd-174">\<issuer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuer.md)|<span data-ttu-id="984cd-175">Bir güvenlik belirteci veren bir uç noktasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="984cd-175">Specifies an endpoint that issues a security token.</span></span> <span data-ttu-id="984cd-176">Bu öğe türünde <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>.</span><span class="sxs-lookup"><span data-stu-id="984cd-176">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>.</span></span>|  
|[<span data-ttu-id="984cd-177">\<issuerMetadata></span><span class="sxs-lookup"><span data-stu-id="984cd-177">\<issuerMetadata></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuermetadata.md)|<span data-ttu-id="984cd-178">Verenin uç nokta adresini belirtir.</span><span class="sxs-lookup"><span data-stu-id="984cd-178">Specifies the endpoint address of the issuer.</span></span>|  
|[<span data-ttu-id="984cd-179">\<tokenRequestParameters ></span><span class="sxs-lookup"><span data-stu-id="984cd-179">\<tokenRequestParameters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/tokenrequestparameters.md)|<span data-ttu-id="984cd-180">Belirteç isteği parametreleri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="984cd-180">A collection of token request parameters.</span></span> <span data-ttu-id="984cd-181">Her bir XML öğesi parametredir.</span><span class="sxs-lookup"><span data-stu-id="984cd-181">Each parameter is an XML element.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="984cd-182">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="984cd-182">Parent Elements</span></span>  
  
|<span data-ttu-id="984cd-183">Öğe</span><span class="sxs-lookup"><span data-stu-id="984cd-183">Element</span></span>|<span data-ttu-id="984cd-184">Açıklama</span><span class="sxs-lookup"><span data-stu-id="984cd-184">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="984cd-185">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="984cd-185">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md)|<span data-ttu-id="984cd-186">Bir bağlama için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="984cd-186">Defines the security settings for a binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="984cd-187">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="984cd-187">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp>
- <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement.Message%2A>
- <xref:System.ServiceModel.WSFederationHttpSecurity.Message%2A>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>
- [<span data-ttu-id="984cd-188">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="984cd-188">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="984cd-189">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="984cd-189">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="984cd-190">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="984cd-190">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="984cd-191">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="984cd-191">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="984cd-192">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="984cd-192">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
