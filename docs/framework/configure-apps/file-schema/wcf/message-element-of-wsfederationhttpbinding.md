---
title: <message>öğesi<wsFederationHttpBinding>
ms.date: 03/30/2017
ms.assetid: 9d710389-d9d8-4454-9bf2-da4ccda31cec
ms.openlocfilehash: 4730d7e573eefdfcd5704621d0a7ccaa15f76d3a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931585"
---
# <a name="message-element-of-wsfederationhttpbinding"></a><span data-ttu-id="3f7ad-102">\<ileti > \<WSFederationHttpBinding > öğesi</span><span class="sxs-lookup"><span data-stu-id="3f7ad-102">\<message> element of \<wsFederationHttpBinding></span></span>
<span data-ttu-id="3f7ad-103">[ \<WSFederationHttpBinding >](wsfederationhttpbinding.md)için ileti düzeyi güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3f7ad-103">Defines the settings for the message-level security for the [\<wsFederationHttpBinding>](wsfederationhttpbinding.md).</span></span>  
  
 <span data-ttu-id="3f7ad-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="3f7ad-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="3f7ad-105">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="3f7ad-105">\<bindings></span></span>  
<span data-ttu-id="3f7ad-106">\<wsFederatedBinding ></span><span class="sxs-lookup"><span data-stu-id="3f7ad-106">\<wsFederatedBinding></span></span>  
<span data-ttu-id="3f7ad-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="3f7ad-107">\<binding></span></span>  
<span data-ttu-id="3f7ad-108">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="3f7ad-108">\<security></span></span>  
<span data-ttu-id="3f7ad-109">\<ileti ></span><span class="sxs-lookup"><span data-stu-id="3f7ad-109">\<message></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f7ad-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3f7ad-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3f7ad-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="3f7ad-111">Attributes and Elements</span></span>  
 <span data-ttu-id="3f7ad-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3f7ad-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3f7ad-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="3f7ad-113">Attributes</span></span>  
  
|<span data-ttu-id="3f7ad-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="3f7ad-114">Attribute</span></span>|<span data-ttu-id="3f7ad-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3f7ad-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3f7ad-116">algorithmSuite</span><span class="sxs-lookup"><span data-stu-id="3f7ad-116">algorithmSuite</span></span>|<span data-ttu-id="3f7ad-117">İleti şifrelemesini ve anahtar sarması algoritmalarını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="3f7ad-117">Sets the message encryption and key-wrap algorithms.</span></span> <span data-ttu-id="3f7ad-118">Bu özniteliğin geçerli değerleri için "algorithmSuite Attribute" tablosuna bakın.</span><span class="sxs-lookup"><span data-stu-id="3f7ad-118">See the "algorithmSuite attribute" table for valid values of this attribute.</span></span> <span data-ttu-id="3f7ad-119">Varsayılan değer `Basic256` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="3f7ad-119">The default value is `Basic256`.</span></span><br /><br /> <span data-ttu-id="3f7ad-120">Bu öznitelik türü <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span><span class="sxs-lookup"><span data-stu-id="3f7ad-120">This attribute is of type <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span></span> <span data-ttu-id="3f7ad-121">Bu algoritmalar güvenlik Ilkesi dili (WS-SecurityPolicy) belirtiminde belirtilen olanlarla eşlenir.</span><span class="sxs-lookup"><span data-stu-id="3f7ad-121">These algorithms map to those specified in the Security Policy Language (WS-SecurityPolicy) specification.</span></span>|  
|<span data-ttu-id="3f7ad-122">IssuedKeyType</span><span class="sxs-lookup"><span data-stu-id="3f7ad-122">issuedKeyType</span></span>|<span data-ttu-id="3f7ad-123">Verilecek anahtarın türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="3f7ad-123">Specifies the type of key to be issued.</span></span> <span data-ttu-id="3f7ad-124">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="3f7ad-124">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="3f7ad-125">-SymmetricKey</span><span class="sxs-lookup"><span data-stu-id="3f7ad-125">-   SymmetricKey</span></span><br /><span data-ttu-id="3f7ad-126">-PublicKey</span><span class="sxs-lookup"><span data-stu-id="3f7ad-126">-   PublicKey</span></span><br /><br /> <span data-ttu-id="3f7ad-127">Varsayılan, `SymmetricKey` değeridir.</span><span class="sxs-lookup"><span data-stu-id="3f7ad-127">The default is `SymmetricKey`.</span></span> <span data-ttu-id="3f7ad-128">Bu öznitelik türü <xref:System.IdentityModel.Tokens.SecurityKeyType>.</span><span class="sxs-lookup"><span data-stu-id="3f7ad-128">This attribute is of type <xref:System.IdentityModel.Tokens.SecurityKeyType>.</span></span>|  
|<span data-ttu-id="3f7ad-129">issuedTokenType</span><span class="sxs-lookup"><span data-stu-id="3f7ad-129">issuedTokenType</span></span>|<span data-ttu-id="3f7ad-130">Verilecek belirtecin türünü belirten bir URI içeren dize.</span><span class="sxs-lookup"><span data-stu-id="3f7ad-130">A string that contains a URI that specifies the type of token to be issued.</span></span> <span data-ttu-id="3f7ad-131">Varsayılan, `null` değeridir.</span><span class="sxs-lookup"><span data-stu-id="3f7ad-131">The default is `null`.</span></span>|  
|<span data-ttu-id="3f7ad-132">negotiateServiceCredential</span><span class="sxs-lookup"><span data-stu-id="3f7ad-132">negotiateServiceCredential</span></span>|<span data-ttu-id="3f7ad-133">Hizmet kimlik bilgisinin, anlaşmanın parçası olarak alınıp alınmayacağını veya bant dışı kullanılabilir olup olmadığını belirten bir Boolean değer.</span><span class="sxs-lookup"><span data-stu-id="3f7ad-133">A Boolean value that specifies whether the service credential should be exchanged as part of negotiation or is available out of band.</span></span> <span data-ttu-id="3f7ad-134">Varsayılan `true`olarak, hizmet kimlik bilgisinin anlaşıldığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="3f7ad-134">The default is `true`, which means that the service credential is negotiated.</span></span>|  
  
## <a name="algorithmsuite-attribute"></a><span data-ttu-id="3f7ad-135">algorithmSuite özniteliği</span><span class="sxs-lookup"><span data-stu-id="3f7ad-135">algorithmSuite Attribute</span></span>  
  
|<span data-ttu-id="3f7ad-136">Değer</span><span class="sxs-lookup"><span data-stu-id="3f7ad-136">Value</span></span>|<span data-ttu-id="3f7ad-137">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3f7ad-137">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="3f7ad-138">Basic128</span><span class="sxs-lookup"><span data-stu-id="3f7ad-138">Basic128</span></span>|<span data-ttu-id="3f7ad-139">Anahtar kaydırması için Basic128 şifrelemesi, ileti özeti için SHA1 ve rsa-oaep-mgf1p kullanın.</span><span class="sxs-lookup"><span data-stu-id="3f7ad-139">Use Basic128 encryption, Sha1 for message digest, and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="3f7ad-140">Basic192</span><span class="sxs-lookup"><span data-stu-id="3f7ad-140">Basic192</span></span>|<span data-ttu-id="3f7ad-141">Anahtar kaydırması için Basic192 şifrelemesi, ileti özeti için SHA1, rsa-oaep-mgf1p kullanın.</span><span class="sxs-lookup"><span data-stu-id="3f7ad-141">Use Basic192 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="3f7ad-142">Basic256</span><span class="sxs-lookup"><span data-stu-id="3f7ad-142">Basic256</span></span>|<span data-ttu-id="3f7ad-143">Anahtar kaydırması için Basic256 şifrelemesi, ileti özeti için SHA1, rsa-oaep-mgf1p kullanın.</span><span class="sxs-lookup"><span data-stu-id="3f7ad-143">Use Basic256 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="3f7ad-144">Basic256Rsa15</span><span class="sxs-lookup"><span data-stu-id="3f7ad-144">Basic256Rsa15</span></span>|<span data-ttu-id="3f7ad-145">İleti şifreleme için Basic256, ileti özeti için SHA1 ve anahtar kaydırması için Rsa15 kullanın.</span><span class="sxs-lookup"><span data-stu-id="3f7ad-145">Use Basic256 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="3f7ad-146">Basic192Rsa15</span><span class="sxs-lookup"><span data-stu-id="3f7ad-146">Basic192Rsa15</span></span>|<span data-ttu-id="3f7ad-147">İleti şifreleme için Basic192, ileti özeti için SHA1 ve anahtar kaydırması için Rsa15 kullanın.</span><span class="sxs-lookup"><span data-stu-id="3f7ad-147">Use Basic192 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="3f7ad-148">TripleDes</span><span class="sxs-lookup"><span data-stu-id="3f7ad-148">TripleDes</span></span>|<span data-ttu-id="3f7ad-149">Anahtar kaydırması için, TripleDes şifrelemesi, ileti özeti için SHA1, rsa-oaep-mgf1p kullanın.</span><span class="sxs-lookup"><span data-stu-id="3f7ad-149">Use TripleDes encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="3f7ad-150">Basic128Rsa15</span><span class="sxs-lookup"><span data-stu-id="3f7ad-150">Basic128Rsa15</span></span>|<span data-ttu-id="3f7ad-151">İleti şifreleme için Basic128, ileti özeti için SHA1 ve anahtar kaydırması için Rsa15 kullanın.</span><span class="sxs-lookup"><span data-stu-id="3f7ad-151">Use Basic128 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="3f7ad-152">TripleDesRsa15</span><span class="sxs-lookup"><span data-stu-id="3f7ad-152">TripleDesRsa15</span></span>|<span data-ttu-id="3f7ad-153">TripleDes şifrelemesi, ileti özeti için SHA1 ve anahtar kaydırması için Rsa15 kullanın.</span><span class="sxs-lookup"><span data-stu-id="3f7ad-153">Use TripleDes encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="3f7ad-154">Basic128Sha256</span><span class="sxs-lookup"><span data-stu-id="3f7ad-154">Basic128Sha256</span></span>|<span data-ttu-id="3f7ad-155">İleti için Basic128, ileti özeti için SHA256, anahtar kaydırması için rsa-oaep-mgf1p kullanın.</span><span class="sxs-lookup"><span data-stu-id="3f7ad-155">Use Basic128 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="3f7ad-156">Basic192Sha256</span><span class="sxs-lookup"><span data-stu-id="3f7ad-156">Basic192Sha256</span></span>|<span data-ttu-id="3f7ad-157">İleti için Basic192, ileti özeti için SHA256, anahtar kaydırması için rsa-oaep-mgf1p kullanın.</span><span class="sxs-lookup"><span data-stu-id="3f7ad-157">Use Basic192 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="3f7ad-158">Basic256Sha256</span><span class="sxs-lookup"><span data-stu-id="3f7ad-158">Basic256Sha256</span></span>|<span data-ttu-id="3f7ad-159">İleti için Basic256, ileti özeti için SHA256, anahtar kaydırması için rsa-oaep-mgf1p kullanın.</span><span class="sxs-lookup"><span data-stu-id="3f7ad-159">Use Basic256 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="3f7ad-160">TripleDesSha256</span><span class="sxs-lookup"><span data-stu-id="3f7ad-160">TripleDesSha256</span></span>|<span data-ttu-id="3f7ad-161">İleti şifreleme için TripleDes, SHA256 for Message Digest ve rsa-oaep-mgf1p için anahtar kaydırması kullanın.</span><span class="sxs-lookup"><span data-stu-id="3f7ad-161">Use TripleDes for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="3f7ad-162">Basic128Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="3f7ad-162">Basic128Sha256Rsa15</span></span>|<span data-ttu-id="3f7ad-163">İleti şifreleme için Basic128, ileti özeti için SHA256 ve anahtar kaydırması için Rsa15 kullanın.</span><span class="sxs-lookup"><span data-stu-id="3f7ad-163">Use Basic128 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="3f7ad-164">Basic192Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="3f7ad-164">Basic192Sha256Rsa15</span></span>|<span data-ttu-id="3f7ad-165">İleti şifreleme için Aes192, ileti özeti için SHA256 ve anahtar kaydırması için Rsa15 kullanın.</span><span class="sxs-lookup"><span data-stu-id="3f7ad-165">Use Aes192 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="3f7ad-166">Basic256Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="3f7ad-166">Basic256Sha256Rsa15</span></span>|<span data-ttu-id="3f7ad-167">İleti şifreleme için Basic256, ileti özeti için SHA256 ve anahtar kaydırması için Rsa15 kullanın.</span><span class="sxs-lookup"><span data-stu-id="3f7ad-167">Use Basic256 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="3f7ad-168">TripleDesSha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="3f7ad-168">TripleDesSha256Rsa15</span></span>|<span data-ttu-id="3f7ad-169">İleti şifreleme için TripleDes, SHA256 for Message Digest ve Rsa15 anahtar kaydırması için kullanın.</span><span class="sxs-lookup"><span data-stu-id="3f7ad-169">Use TripleDes for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3f7ad-170">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="3f7ad-170">Child Elements</span></span>  
  
|<span data-ttu-id="3f7ad-171">Öğe</span><span class="sxs-lookup"><span data-stu-id="3f7ad-171">Element</span></span>|<span data-ttu-id="3f7ad-172">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3f7ad-172">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3f7ad-173">\<claimTypeRequirements ></span><span class="sxs-lookup"><span data-stu-id="3f7ad-173">\<claimTypeRequirements></span></span>](claimtyperequirements-element.md)|<span data-ttu-id="3f7ad-174">Bu bağlama için bir talep türleri koleksiyonu belirtir.</span><span class="sxs-lookup"><span data-stu-id="3f7ad-174">Specifies a collection of claim types for this binding.</span></span> <span data-ttu-id="3f7ad-175">Her öğe türündedir <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span><span class="sxs-lookup"><span data-stu-id="3f7ad-175">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span>|  
|<span data-ttu-id="3f7ad-176">yayınlayan</span><span class="sxs-lookup"><span data-stu-id="3f7ad-176">issuer</span></span>|<span data-ttu-id="3f7ad-177">Bir güvenlik belirteci veren bir uç nokta belirtir.</span><span class="sxs-lookup"><span data-stu-id="3f7ad-177">Specifies an endpoint that issues a security token.</span></span> <span data-ttu-id="3f7ad-178">Bu öğe türündedir <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>.</span><span class="sxs-lookup"><span data-stu-id="3f7ad-178">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>.</span></span>|  
|<span data-ttu-id="3f7ad-179">issuerMetadata</span><span class="sxs-lookup"><span data-stu-id="3f7ad-179">issuerMetadata</span></span>|<span data-ttu-id="3f7ad-180">Verenin uç nokta adresini belirtir.</span><span class="sxs-lookup"><span data-stu-id="3f7ad-180">Specifies the endpoint address of the issuer.</span></span>|  
|[<span data-ttu-id="3f7ad-181">\<tokenRequestParameters></span><span class="sxs-lookup"><span data-stu-id="3f7ad-181">\<tokenRequestParameters></span></span>](tokenrequestparameters.md)|<span data-ttu-id="3f7ad-182">Belirteç isteği parametrelerinin bir koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="3f7ad-182">A collection of token request parameters.</span></span> <span data-ttu-id="3f7ad-183">Her parametre bir XML öğesidir.</span><span class="sxs-lookup"><span data-stu-id="3f7ad-183">Each parameter is an XML element.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3f7ad-184">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="3f7ad-184">Parent Elements</span></span>  
  
|<span data-ttu-id="3f7ad-185">Öğe</span><span class="sxs-lookup"><span data-stu-id="3f7ad-185">Element</span></span>|<span data-ttu-id="3f7ad-186">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3f7ad-186">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3f7ad-187">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="3f7ad-187">\<security></span></span>](security-of-wsfederationhttpbinding.md)|<span data-ttu-id="3f7ad-188">Bağlama için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3f7ad-188">Defines the security settings for a binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3f7ad-189">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3f7ad-189">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp>
- <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement.Message%2A>
- <xref:System.ServiceModel.WSFederationHttpSecurity.Message%2A>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>
- [<span data-ttu-id="3f7ad-190">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="3f7ad-190">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="3f7ad-191">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="3f7ad-191">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="3f7ad-192">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="3f7ad-192">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="3f7ad-193">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="3f7ad-193">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="3f7ad-194">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="3f7ad-194">\<binding></span></span>](../../../misc/binding.md)
