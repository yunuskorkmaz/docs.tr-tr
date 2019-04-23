---
title: <message> öğesi <wsFederationHttpBinding>
ms.date: 03/30/2017
ms.assetid: 9d710389-d9d8-4454-9bf2-da4ccda31cec
ms.openlocfilehash: 79739dd715d7982555e5577c921cb65156af5923
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59223820"
---
# <a name="message-element-of-wsfederationhttpbinding"></a><span data-ttu-id="40f45-102">\<İleti > öğesi \<wsFederationHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="40f45-102">\<message> element of \<wsFederationHttpBinding></span></span>
<span data-ttu-id="40f45-103">İleti düzeyi güvenlik ayarlarını tanımlar [ \<wsFederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="40f45-103">Defines the settings for the message-level security for the [\<wsFederationHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md).</span></span>  
  
 <span data-ttu-id="40f45-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="40f45-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="40f45-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="40f45-105">\<bindings></span></span>  
<span data-ttu-id="40f45-106">\<wsFederatedBinding ></span><span class="sxs-lookup"><span data-stu-id="40f45-106">\<wsFederatedBinding></span></span>  
<span data-ttu-id="40f45-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="40f45-107">\<binding></span></span>  
<span data-ttu-id="40f45-108">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="40f45-108">\<security></span></span>  
<span data-ttu-id="40f45-109">\<İleti ></span><span class="sxs-lookup"><span data-stu-id="40f45-109">\<message></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40f45-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="40f45-110">Syntax</span></span>  
  
```xml  
<wsFederationBinding>
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
</wsFederationBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="40f45-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="40f45-111">Attributes and Elements</span></span>  
 <span data-ttu-id="40f45-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="40f45-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="40f45-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="40f45-113">Attributes</span></span>  
  
|<span data-ttu-id="40f45-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="40f45-114">Attribute</span></span>|<span data-ttu-id="40f45-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="40f45-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="40f45-116">algorithmSuite</span><span class="sxs-lookup"><span data-stu-id="40f45-116">algorithmSuite</span></span>|<span data-ttu-id="40f45-117">İleti şifreleme ve anahtar-wrap algoritmaları ayarlar.</span><span class="sxs-lookup"><span data-stu-id="40f45-117">Sets the message encryption and key-wrap algorithms.</span></span> <span data-ttu-id="40f45-118">Bu özniteliğin geçerli değerleri için "algorithmSuite özniteliği" tablosuna bakın.</span><span class="sxs-lookup"><span data-stu-id="40f45-118">See the "algorithmSuite attribute" table for valid values of this attribute.</span></span> <span data-ttu-id="40f45-119">Varsayılan değer `Basic256` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="40f45-119">The default value is `Basic256`.</span></span><br /><br /> <span data-ttu-id="40f45-120">Bu öznitelik türünde <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span><span class="sxs-lookup"><span data-stu-id="40f45-120">This attribute is of type <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span></span> <span data-ttu-id="40f45-121">Bu algoritmalar, güvenlik ilkesi dili (WS-SecurityPolicy) belirtiminde belirtilen platformlarla eşlenir.</span><span class="sxs-lookup"><span data-stu-id="40f45-121">These algorithms map to those specified in the Security Policy Language (WS-SecurityPolicy) specification.</span></span>|  
|<span data-ttu-id="40f45-122">issuedKeyType</span><span class="sxs-lookup"><span data-stu-id="40f45-122">issuedKeyType</span></span>|<span data-ttu-id="40f45-123">Kesilecek anahtar türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="40f45-123">Specifies the type of key to be issued.</span></span> <span data-ttu-id="40f45-124">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="40f45-124">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="40f45-125">-   SymmetricKey</span><span class="sxs-lookup"><span data-stu-id="40f45-125">-   SymmetricKey</span></span><br /><span data-ttu-id="40f45-126">-   PublicKey</span><span class="sxs-lookup"><span data-stu-id="40f45-126">-   PublicKey</span></span><br /><br /> <span data-ttu-id="40f45-127">Varsayılan, `SymmetricKey` değeridir.</span><span class="sxs-lookup"><span data-stu-id="40f45-127">The default is `SymmetricKey`.</span></span> <span data-ttu-id="40f45-128">Bu öznitelik türünde <xref:System.IdentityModel.Tokens.SecurityKeyType>.</span><span class="sxs-lookup"><span data-stu-id="40f45-128">This attribute is of type <xref:System.IdentityModel.Tokens.SecurityKeyType>.</span></span>|  
|<span data-ttu-id="40f45-129">issuedTokenType</span><span class="sxs-lookup"><span data-stu-id="40f45-129">issuedTokenType</span></span>|<span data-ttu-id="40f45-130">Verilmesi için belirteç türünü belirten bir URI içeren dize.</span><span class="sxs-lookup"><span data-stu-id="40f45-130">A string that contains a URI that specifies the type of token to be issued.</span></span> <span data-ttu-id="40f45-131">Varsayılan, `null` değeridir.</span><span class="sxs-lookup"><span data-stu-id="40f45-131">The default is `null`.</span></span>|  
|<span data-ttu-id="40f45-132">negotiateServiceCredential</span><span class="sxs-lookup"><span data-stu-id="40f45-132">negotiateServiceCredential</span></span>|<span data-ttu-id="40f45-133">Hizmet kimlik bilgisi anlaşmasının bir parçası değiştirilen veya bant dışından mevcut olup olmadığını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="40f45-133">A Boolean value that specifies whether the service credential should be exchanged as part of negotiation or is available out of band.</span></span> <span data-ttu-id="40f45-134">Varsayılan `true`, hizmet kimlik bilgisi anlaşılır anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="40f45-134">The default is `true`, which means that the service credential is negotiated.</span></span>|  
  
## <a name="algorithmsuite-attribute"></a><span data-ttu-id="40f45-135">algorithmSuite özniteliği</span><span class="sxs-lookup"><span data-stu-id="40f45-135">algorithmSuite Attribute</span></span>  
  
|<span data-ttu-id="40f45-136">Değer</span><span class="sxs-lookup"><span data-stu-id="40f45-136">Value</span></span>|<span data-ttu-id="40f45-137">Açıklama</span><span class="sxs-lookup"><span data-stu-id="40f45-137">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="40f45-138">Basic128</span><span class="sxs-lookup"><span data-stu-id="40f45-138">Basic128</span></span>|<span data-ttu-id="40f45-139">İleti özeti için Sha1 ve Rsa oaep mgf1p Basic128 şifreleme anahtarı kaydırma için kullanın.</span><span class="sxs-lookup"><span data-stu-id="40f45-139">Use Basic128 encryption, Sha1 for message digest, and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="40f45-140">Basic192</span><span class="sxs-lookup"><span data-stu-id="40f45-140">Basic192</span></span>|<span data-ttu-id="40f45-141">İleti özeti, anahtar kaydırma için Rsa-oaep mgf1p için Sha1 Basic192 şifrelemesi kullanın.</span><span class="sxs-lookup"><span data-stu-id="40f45-141">Use Basic192 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="40f45-142">Basic256</span><span class="sxs-lookup"><span data-stu-id="40f45-142">Basic256</span></span>|<span data-ttu-id="40f45-143">İleti özeti, anahtar kaydırma için Rsa-oaep mgf1p için Sha1 Basic256 şifrelemesi kullanın.</span><span class="sxs-lookup"><span data-stu-id="40f45-143">Use Basic256 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="40f45-144">Basic256Rsa15</span><span class="sxs-lookup"><span data-stu-id="40f45-144">Basic256Rsa15</span></span>|<span data-ttu-id="40f45-145">İleti şifreleme, ileti özeti için Sha1 ve anahtar kaydırma için Rsa15 Basic256 kullanın.</span><span class="sxs-lookup"><span data-stu-id="40f45-145">Use Basic256 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="40f45-146">Basic192Rsa15</span><span class="sxs-lookup"><span data-stu-id="40f45-146">Basic192Rsa15</span></span>|<span data-ttu-id="40f45-147">İleti şifreleme, ileti özeti için Sha1 ve anahtar kaydırma için Rsa15 Basic192 kullanın.</span><span class="sxs-lookup"><span data-stu-id="40f45-147">Use Basic192 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="40f45-148">TripleDes</span><span class="sxs-lookup"><span data-stu-id="40f45-148">TripleDes</span></span>|<span data-ttu-id="40f45-149">İleti özeti, anahtar kaydırma için Rsa-oaep mgf1p için Sha1 TripleDes şifrelemesi kullanın.</span><span class="sxs-lookup"><span data-stu-id="40f45-149">Use TripleDes encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="40f45-150">Basic128Rsa15</span><span class="sxs-lookup"><span data-stu-id="40f45-150">Basic128Rsa15</span></span>|<span data-ttu-id="40f45-151">İleti şifreleme, ileti özeti için Sha1 ve anahtar kaydırma için Rsa15 Basic128 kullanın.</span><span class="sxs-lookup"><span data-stu-id="40f45-151">Use Basic128 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="40f45-152">TripleDesRsa15</span><span class="sxs-lookup"><span data-stu-id="40f45-152">TripleDesRsa15</span></span>|<span data-ttu-id="40f45-153">İleti özeti için Sha1 ve anahtar kaydırma için Rsa15 TripleDes şifrelemesi kullanın.</span><span class="sxs-lookup"><span data-stu-id="40f45-153">Use TripleDes encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="40f45-154">Basic128Sha256</span><span class="sxs-lookup"><span data-stu-id="40f45-154">Basic128Sha256</span></span>|<span data-ttu-id="40f45-155">İleti şifreleme, ileti özeti için Sha256 ve anahtar kaydırma için Rsa-oaep mgf1p Basic128 kullanın.</span><span class="sxs-lookup"><span data-stu-id="40f45-155">Use Basic128 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="40f45-156">Basic192Sha256</span><span class="sxs-lookup"><span data-stu-id="40f45-156">Basic192Sha256</span></span>|<span data-ttu-id="40f45-157">İleti şifreleme, ileti özeti için Sha256 ve anahtar kaydırma için Rsa-oaep mgf1p Basic192 kullanın.</span><span class="sxs-lookup"><span data-stu-id="40f45-157">Use Basic192 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="40f45-158">Basic256Sha256</span><span class="sxs-lookup"><span data-stu-id="40f45-158">Basic256Sha256</span></span>|<span data-ttu-id="40f45-159">İleti şifreleme, ileti özeti için Sha256 ve anahtar kaydırma için Rsa-oaep mgf1p Basic256 kullanın.</span><span class="sxs-lookup"><span data-stu-id="40f45-159">Use Basic256 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="40f45-160">TripleDesSha256</span><span class="sxs-lookup"><span data-stu-id="40f45-160">TripleDesSha256</span></span>|<span data-ttu-id="40f45-161">TripleDes ileti özeti için Sha256 ve anahtar kaydırma için Rsa-oaep mgf1p ileti şifreleme için kullanın.</span><span class="sxs-lookup"><span data-stu-id="40f45-161">Use TripleDes for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="40f45-162">Basic128Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="40f45-162">Basic128Sha256Rsa15</span></span>|<span data-ttu-id="40f45-163">İleti şifreleme, ileti özeti için Sha256 ve anahtar kaydırma için Rsa15 Basic128 kullanın.</span><span class="sxs-lookup"><span data-stu-id="40f45-163">Use Basic128 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="40f45-164">Basic192Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="40f45-164">Basic192Sha256Rsa15</span></span>|<span data-ttu-id="40f45-165">İleti şifreleme, ileti özeti için Sha256 ve anahtar kaydırma için Rsa15 Aes192 kullanın.</span><span class="sxs-lookup"><span data-stu-id="40f45-165">Use Aes192 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="40f45-166">Basic256Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="40f45-166">Basic256Sha256Rsa15</span></span>|<span data-ttu-id="40f45-167">İleti şifreleme, ileti özeti için Sha256 ve anahtar kaydırma için Rsa15 Basic256 kullanın.</span><span class="sxs-lookup"><span data-stu-id="40f45-167">Use Basic256 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="40f45-168">TripleDesSha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="40f45-168">TripleDesSha256Rsa15</span></span>|<span data-ttu-id="40f45-169">TripleDes ileti özeti için Sha256 ve anahtar kaydırma için Rsa15 ileti şifreleme için kullanın.</span><span class="sxs-lookup"><span data-stu-id="40f45-169">Use TripleDes for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="40f45-170">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="40f45-170">Child Elements</span></span>  
  
|<span data-ttu-id="40f45-171">Öğe</span><span class="sxs-lookup"><span data-stu-id="40f45-171">Element</span></span>|<span data-ttu-id="40f45-172">Açıklama</span><span class="sxs-lookup"><span data-stu-id="40f45-172">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="40f45-173">\<claimTypeRequirements ></span><span class="sxs-lookup"><span data-stu-id="40f45-173">\<claimTypeRequirements></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-element.md)|<span data-ttu-id="40f45-174">Bu bağlama için talep türlerinin koleksiyonunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="40f45-174">Specifies a collection of claim types for this binding.</span></span> <span data-ttu-id="40f45-175">Her öğe türünde <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span><span class="sxs-lookup"><span data-stu-id="40f45-175">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span>|  
|<span data-ttu-id="40f45-176">yayınlayan</span><span class="sxs-lookup"><span data-stu-id="40f45-176">issuer</span></span>|<span data-ttu-id="40f45-177">Bir güvenlik belirteci veren bir uç noktasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="40f45-177">Specifies an endpoint that issues a security token.</span></span> <span data-ttu-id="40f45-178">Bu öğe türünde <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>.</span><span class="sxs-lookup"><span data-stu-id="40f45-178">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>.</span></span>|  
|<span data-ttu-id="40f45-179">issuerMetadata</span><span class="sxs-lookup"><span data-stu-id="40f45-179">issuerMetadata</span></span>|<span data-ttu-id="40f45-180">Verenin uç nokta adresini belirtir.</span><span class="sxs-lookup"><span data-stu-id="40f45-180">Specifies the endpoint address of the issuer.</span></span>|  
|[<span data-ttu-id="40f45-181">\<tokenRequestParameters></span><span class="sxs-lookup"><span data-stu-id="40f45-181">\<tokenRequestParameters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/tokenrequestparameters.md)|<span data-ttu-id="40f45-182">Belirteç isteği parametreleri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="40f45-182">A collection of token request parameters.</span></span> <span data-ttu-id="40f45-183">Her bir XML öğesi parametredir.</span><span class="sxs-lookup"><span data-stu-id="40f45-183">Each parameter is an XML element.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="40f45-184">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="40f45-184">Parent Elements</span></span>  
  
|<span data-ttu-id="40f45-185">Öğe</span><span class="sxs-lookup"><span data-stu-id="40f45-185">Element</span></span>|<span data-ttu-id="40f45-186">Açıklama</span><span class="sxs-lookup"><span data-stu-id="40f45-186">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="40f45-187">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="40f45-187">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wsfederationhttpbinding.md)|<span data-ttu-id="40f45-188">Bir bağlama için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="40f45-188">Defines the security settings for a binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="40f45-189">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="40f45-189">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp>
- <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement.Message%2A>
- <xref:System.ServiceModel.WSFederationHttpSecurity.Message%2A>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>
- [<span data-ttu-id="40f45-190">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="40f45-190">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="40f45-191">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="40f45-191">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="40f45-192">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="40f45-192">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="40f45-193">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="40f45-193">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="40f45-194">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="40f45-194">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
