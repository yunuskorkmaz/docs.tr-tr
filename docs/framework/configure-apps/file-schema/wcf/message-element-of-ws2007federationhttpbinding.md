---
title: '&lt;ws2007FederationHttpBinding&gt; &lt;iletisi&gt; öğesi'
ms.date: 03/30/2017
ms.assetid: 52cd941d-e230-4c82-8b29-333a7d20eca8
ms.openlocfilehash: 565a0c6027e94954c81c11f96fbd5473dbcd4fdf
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="ltmessagegt-element-of-ltws2007federationhttpbindinggt"></a><span data-ttu-id="a0b76-102">&lt;ws2007FederationHttpBinding&gt; &lt;iletisi&gt; öğesi</span><span class="sxs-lookup"><span data-stu-id="a0b76-102">&lt;message&gt; element of &lt;ws2007FederationHttpBinding&gt;</span></span>
<span data-ttu-id="a0b76-103">İleti düzeyi güvenlik ayarlarını tanımlar [ \<ws2007FederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007federationhttpbinding.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="a0b76-103">Defines settings for the message-level security for the [\<ws2007FederationHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007federationhttpbinding.md) element.</span></span>  
  
 <span data-ttu-id="a0b76-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="a0b76-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="a0b76-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="a0b76-105">\<bindings></span></span>  
<span data-ttu-id="a0b76-106">\<ws2007FederationHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="a0b76-106">\<ws2007FederationHttpBinding></span></span>  
<span data-ttu-id="a0b76-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="a0b76-107">\<binding></span></span>  
<span data-ttu-id="a0b76-108">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="a0b76-108">\<security></span></span>  
<span data-ttu-id="a0b76-109">\<İleti ></span><span class="sxs-lookup"><span data-stu-id="a0b76-109">\<message></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0b76-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a0b76-110">Syntax</span></span>  
  
```xml  
<ws2007FederationBinding>  
   <binding >  
      <security>  
         <message   
            algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
            issuedTokenType="string"   
            issuedKeyType="SymmetricKey/PublicKey"  
            negotiateServiceCredential="Boolean" >  
            <claimTypeRequirements>  
               <add claimType="URI"  
                    isOptional="Boolean" />  
            </claimTypeRequirements>  
            <issuer address="Uri" >  
               <headers>  
                  <add name="String"  
                       namespace="String" />  
               </headers>  
               <identity>  
                  <certificate encodedValue="String"/>  
                  <certificateReference findValue="String"   
                     isChainIncluded="Boolean"  
                     storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"  
                     storeLocation="LocalMachine/CurrentUser"  
                     x509FindType=System.Security.Cryptography.X509certificates.X509findtype/>  
                  <dns value="String"/>  
                  <rsa value="String"/>  
                  <servicePrincipalName value="String"/>  
                  <usePrincipalName value="String"/>  
               </identity>  
            </issuer>  
            <issuerMetadata address=String" >  
               <headers>  
                  <add name="String"  
                       namespace="String" />  
               </headers>  
               <identity>  
                  <certificate encodedValue="String"/>  
                  <certificateReference findValue="String"   
                     isChainIncluded="Boolean"  
                     storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"  
                     storeLocation="LocalMachine/CurrentUser"  
                     X509FindType=System.Security.Cryptography.X509certificates.X509findtype/>  
                  <dns value="String"/>  
                  <rsa value="String"/>  
                  <servicePrincipalName value="String"/>  
                  <usePrincipalName value="String"/>  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a0b76-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="a0b76-111">Attributes and Elements</span></span>  
 <span data-ttu-id="a0b76-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a0b76-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a0b76-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a0b76-113">Attributes</span></span>  
  
|<span data-ttu-id="a0b76-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="a0b76-114">Attribute</span></span>|<span data-ttu-id="a0b76-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a0b76-115">Description</span></span>|  
|---------------|-----------------|  
|`algorithmSuite`|<span data-ttu-id="a0b76-116">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="a0b76-116">Optional.</span></span> <span data-ttu-id="a0b76-117">İleti şifreleme, imza ve anahtar-wrap algoritmaları ayarlar.</span><span class="sxs-lookup"><span data-stu-id="a0b76-117">Sets the message encryption, signature, and key-wrap algorithms.</span></span> <span data-ttu-id="a0b76-118">Algoritmaları ve anahtar boyutları tarafından belirlenen <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="a0b76-118">The algorithms and the key sizes are determined by the <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> class.</span></span> <span data-ttu-id="a0b76-119">Bu algoritmalar, güvenlik ilkesi dili (WS-SecurityPolicy) belirtiminde belirtilen eşlenir.</span><span class="sxs-lookup"><span data-stu-id="a0b76-119">These algorithms map to those specified in the Security Policy Language (WS-SecurityPolicy) specification.</span></span><br /><br /> <span data-ttu-id="a0b76-120">Olası değerler için aşağıdaki tabloya bakın.</span><span class="sxs-lookup"><span data-stu-id="a0b76-120">See the following table for possible values.</span></span> <span data-ttu-id="a0b76-121">Basic256 varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="a0b76-121">The default value is Basic256.</span></span>|  
|`issuedKeyType`|<span data-ttu-id="a0b76-122">Kesilecek anahtar türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="a0b76-122">Specifies the type of key to be issued.</span></span> <span data-ttu-id="a0b76-123">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="a0b76-123">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="a0b76-124">-SymmetricKey</span><span class="sxs-lookup"><span data-stu-id="a0b76-124">-   SymmetricKey</span></span><br /><span data-ttu-id="a0b76-125">-PublicKey</span><span class="sxs-lookup"><span data-stu-id="a0b76-125">-   PublicKey</span></span><br /><span data-ttu-id="a0b76-126">-BearerKey</span><span class="sxs-lookup"><span data-stu-id="a0b76-126">-   BearerKey</span></span><br /><br /> <span data-ttu-id="a0b76-127">SymmetricKey varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="a0b76-127">The default is SymmetricKey.</span></span> <span data-ttu-id="a0b76-128">Bu öznitelik türünde <xref:System.IdentityModel.Tokens.SecurityKeyType>.</span><span class="sxs-lookup"><span data-stu-id="a0b76-128">This attribute is of type <xref:System.IdentityModel.Tokens.SecurityKeyType>.</span></span>|  
|`issuedTokenType`|<span data-ttu-id="a0b76-129">Kesilecek Belirtecin türü belirtir URI.</span><span class="sxs-lookup"><span data-stu-id="a0b76-129">A URI that specifies the type of token to be issued.</span></span> <span data-ttu-id="a0b76-130">Varsayılan, `null` değeridir.</span><span class="sxs-lookup"><span data-stu-id="a0b76-130">The default is `null`.</span></span>|  
|`negotiateServiceCredential`|<span data-ttu-id="a0b76-131">Hizmet kimlik bilgilerini anlaşmasının bir parçası değiştirilen veya bant dışı kullanılabilir olup olmadığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="a0b76-131">A value that specifies whether the service credential should be exchanged as part of negotiation or is available out of band.</span></span> <span data-ttu-id="a0b76-132">Varsayılan değer `true`, hizmet kimlik bilgilerini anlaşılmadan anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="a0b76-132">The default is `true`, which means that the service credential is negotiated.</span></span>|  
  
## <a name="algorithmsuite-attribute"></a><span data-ttu-id="a0b76-133">algorithmSuite özniteliği</span><span class="sxs-lookup"><span data-stu-id="a0b76-133">algorithmSuite Attribute</span></span>  
  
|<span data-ttu-id="a0b76-134">Değer</span><span class="sxs-lookup"><span data-stu-id="a0b76-134">Value</span></span>|<span data-ttu-id="a0b76-135">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a0b76-135">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a0b76-136">Basic128</span><span class="sxs-lookup"><span data-stu-id="a0b76-136">Basic128</span></span>|<span data-ttu-id="a0b76-137">İleti özeti için Sha1 ve Rsa oaep mgf1p Aes128 şifreleme anahtarı kaydırma için kullanın.</span><span class="sxs-lookup"><span data-stu-id="a0b76-137">Use Aes128 encryption, Sha1 for message digest, and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="a0b76-138">Basic192</span><span class="sxs-lookup"><span data-stu-id="a0b76-138">Basic192</span></span>|<span data-ttu-id="a0b76-139">Aes192 şifreleme, Sha1 oaep Rsa mgf1p anahtar kaydırma için ileti özeti için kullanın.</span><span class="sxs-lookup"><span data-stu-id="a0b76-139">Use Aes192 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="a0b76-140">Basic256</span><span class="sxs-lookup"><span data-stu-id="a0b76-140">Basic256</span></span>|<span data-ttu-id="a0b76-141">Aes256 şifreleme, Sha1 oaep Rsa mgf1p anahtar kaydırma için ileti özeti için kullanın.</span><span class="sxs-lookup"><span data-stu-id="a0b76-141">Use Aes256 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="a0b76-142">Basic256Rsa15</span><span class="sxs-lookup"><span data-stu-id="a0b76-142">Basic256Rsa15</span></span>|<span data-ttu-id="a0b76-143">İleti şifreleme, ileti özeti için Sha1 ve anahtar sarma Rsa15 için Aes256 kullanın.</span><span class="sxs-lookup"><span data-stu-id="a0b76-143">Use Aes256 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="a0b76-144">Basic192Rsa15</span><span class="sxs-lookup"><span data-stu-id="a0b76-144">Basic192Rsa15</span></span>|<span data-ttu-id="a0b76-145">İleti şifreleme, ileti özeti için Sha1 ve anahtar sarma Rsa15 için Aes192 kullanın.</span><span class="sxs-lookup"><span data-stu-id="a0b76-145">Use Aes192 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="a0b76-146">TripleDes</span><span class="sxs-lookup"><span data-stu-id="a0b76-146">TripleDes</span></span>|<span data-ttu-id="a0b76-147">TripleDes şifreleme, Sha1 oaep Rsa mgf1p anahtar kaydırma için ileti özeti için kullanın.</span><span class="sxs-lookup"><span data-stu-id="a0b76-147">Use TripleDes encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="a0b76-148">Basic128Rsa15</span><span class="sxs-lookup"><span data-stu-id="a0b76-148">Basic128Rsa15</span></span>|<span data-ttu-id="a0b76-149">İleti şifreleme, ileti özeti için Sha1 ve anahtar sarma Rsa15 için Aes128 kullanın.</span><span class="sxs-lookup"><span data-stu-id="a0b76-149">Use Aes128 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="a0b76-150">TripleDesRsa15</span><span class="sxs-lookup"><span data-stu-id="a0b76-150">TripleDesRsa15</span></span>|<span data-ttu-id="a0b76-151">TripleDes şifreleme, ileti özeti için Sha1 ve Rsa15 anahtar kaydırma için kullanın.</span><span class="sxs-lookup"><span data-stu-id="a0b76-151">Use TripleDes encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="a0b76-152">Basic128Sha256</span><span class="sxs-lookup"><span data-stu-id="a0b76-152">Basic128Sha256</span></span>|<span data-ttu-id="a0b76-153">İleti şifreleme, ileti özeti için Sha256 ve oaep Rsa mgf1p anahtar kaydırma için için Aes256 kullanın.</span><span class="sxs-lookup"><span data-stu-id="a0b76-153">Use Aes256 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="a0b76-154">Basic192Sha256</span><span class="sxs-lookup"><span data-stu-id="a0b76-154">Basic192Sha256</span></span>|<span data-ttu-id="a0b76-155">İleti şifreleme, ileti özeti için Sha256 ve anahtar kaydırma için Rsa-oaep mgf1p için Aes192 kullanın.</span><span class="sxs-lookup"><span data-stu-id="a0b76-155">Use Aes192 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="a0b76-156">Basic256Sha256</span><span class="sxs-lookup"><span data-stu-id="a0b76-156">Basic256Sha256</span></span>|<span data-ttu-id="a0b76-157">İleti şifreleme, ileti özeti için Sha256 ve oaep Rsa mgf1p anahtar kaydırma için için Aes256 kullanın.</span><span class="sxs-lookup"><span data-stu-id="a0b76-157">Use Aes256 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="a0b76-158">TripleDesSha256</span><span class="sxs-lookup"><span data-stu-id="a0b76-158">TripleDesSha256</span></span>|<span data-ttu-id="a0b76-159">TripleDes ileti şifreleme, ileti özeti için Sha256 ve oaep Rsa mgf1p anahtar kaydırma için kullanın.</span><span class="sxs-lookup"><span data-stu-id="a0b76-159">Use TripleDes for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="a0b76-160">Basic128Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="a0b76-160">Basic128Sha256Rsa15</span></span>|<span data-ttu-id="a0b76-161">İleti şifreleme, ileti özeti için Sha256 ve anahtar sarma Rsa15 için Aes128 kullanın.</span><span class="sxs-lookup"><span data-stu-id="a0b76-161">Use Aes128 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="a0b76-162">Basic192Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="a0b76-162">Basic192Sha256Rsa15</span></span>|<span data-ttu-id="a0b76-163">İleti şifreleme, ileti özeti için Sha256 ve anahtar sarma Rsa15 için Aes192 kullanın.</span><span class="sxs-lookup"><span data-stu-id="a0b76-163">Use Aes192 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="a0b76-164">Basic256Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="a0b76-164">Basic256Sha256Rsa15</span></span>|<span data-ttu-id="a0b76-165">İleti şifreleme, ileti özeti için Sha256 ve anahtar sarma Rsa15 için Aes256 kullanın.</span><span class="sxs-lookup"><span data-stu-id="a0b76-165">Use Aes256 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="a0b76-166">TripleDesSha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="a0b76-166">TripleDesSha256Rsa15</span></span>|<span data-ttu-id="a0b76-167">TripleDes ileti şifreleme, ileti özeti için Sha256 ve Rsa15 anahtar kaydırma için kullanın.</span><span class="sxs-lookup"><span data-stu-id="a0b76-167">Use TripleDes for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a0b76-168">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="a0b76-168">Child Elements</span></span>  
  
|<span data-ttu-id="a0b76-169">Öğe</span><span class="sxs-lookup"><span data-stu-id="a0b76-169">Element</span></span>|<span data-ttu-id="a0b76-170">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a0b76-170">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a0b76-171">\<claimTypeRequirements ></span><span class="sxs-lookup"><span data-stu-id="a0b76-171">\<claimTypeRequirements></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-element.md)|<span data-ttu-id="a0b76-172">Bu bağlama için talep türleri koleksiyonunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="a0b76-172">Specifies a collection of claim types for this binding.</span></span> <span data-ttu-id="a0b76-173">Her öğe türünde <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span><span class="sxs-lookup"><span data-stu-id="a0b76-173">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span>|  
|[<span data-ttu-id="a0b76-174">\<veren ></span><span class="sxs-lookup"><span data-stu-id="a0b76-174">\<issuer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuer.md)|<span data-ttu-id="a0b76-175">Bir güvenlik belirteci verir bir uç nokta belirtir.</span><span class="sxs-lookup"><span data-stu-id="a0b76-175">Specifies an endpoint that issues a security token.</span></span> <span data-ttu-id="a0b76-176">Bu öğe türünde <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>.</span><span class="sxs-lookup"><span data-stu-id="a0b76-176">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>.</span></span>|  
|[<span data-ttu-id="a0b76-177">\<İssuedtokenparameters ></span><span class="sxs-lookup"><span data-stu-id="a0b76-177">\<issuerMetadata></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuermetadata.md)|<span data-ttu-id="a0b76-178">Uç nokta adresi verenin belirtir.</span><span class="sxs-lookup"><span data-stu-id="a0b76-178">Specifies the endpoint address of the issuer.</span></span>|  
|[<span data-ttu-id="a0b76-179">\<tokenRequestParameters></span><span class="sxs-lookup"><span data-stu-id="a0b76-179">\<tokenRequestParameters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/tokenrequestparameters.md)|<span data-ttu-id="a0b76-180">Belirteç isteği parametreleri topluluğu.</span><span class="sxs-lookup"><span data-stu-id="a0b76-180">A collection of token request parameters.</span></span> <span data-ttu-id="a0b76-181">Her bir XML öğesi parametresidir.</span><span class="sxs-lookup"><span data-stu-id="a0b76-181">Each parameter is an XML element.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a0b76-182">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="a0b76-182">Parent Elements</span></span>  
  
|<span data-ttu-id="a0b76-183">Öğe</span><span class="sxs-lookup"><span data-stu-id="a0b76-183">Element</span></span>|<span data-ttu-id="a0b76-184">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a0b76-184">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a0b76-185">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="a0b76-185">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md)|<span data-ttu-id="a0b76-186">Bağlama için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a0b76-186">Defines the security settings for a binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a0b76-187">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a0b76-187">See Also</span></span>  
 <xref:System.ServiceModel.FederatedMessageSecurityOverHttp>  
 <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement.Message%2A>  
 <xref:System.ServiceModel.WSFederationHttpSecurity.Message%2A>  
 <span data-ttu-id="a0b76-188">`System.ServiceModel.Configuration.FederatedMessageSecurityElement` [Hizmetler ve istemcileri güvenli hale getirme](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)</span><span class="sxs-lookup"><span data-stu-id="a0b76-188">`System.ServiceModel.Configuration.FederatedMessageSecurityElement` [Securing Services and Clients](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)</span></span>  
 [<span data-ttu-id="a0b76-189">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="a0b76-189">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="a0b76-190">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="a0b76-190">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="a0b76-191">Windows Communication Foundation Hizmetleri ve istemcileri yapılandırmak için bağlamaları kullanma</span><span class="sxs-lookup"><span data-stu-id="a0b76-191">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="a0b76-192">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="a0b76-192">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
