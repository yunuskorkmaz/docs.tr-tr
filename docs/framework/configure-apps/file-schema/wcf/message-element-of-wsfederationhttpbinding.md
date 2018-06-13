---
title: '&lt;wsFederationHttpBinding&gt; &lt;iletisi&gt; öğesi'
ms.date: 03/30/2017
ms.assetid: 9d710389-d9d8-4454-9bf2-da4ccda31cec
ms.openlocfilehash: 24d7370eaadba08d449b886a09cb9903ca0a64c2
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32751109"
---
# <a name="ltmessagegt-element-of-ltwsfederationhttpbindinggt"></a><span data-ttu-id="27ac7-102">&lt;wsFederationHttpBinding&gt; &lt;iletisi&gt; öğesi</span><span class="sxs-lookup"><span data-stu-id="27ac7-102">&lt;message&gt; element of &lt;wsFederationHttpBinding&gt;</span></span>
<span data-ttu-id="27ac7-103">İleti düzeyi güvenlik ayarlarını tanımlar [ \<wsFederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="27ac7-103">Defines the settings for the message-level security for the [\<wsFederationHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md).</span></span>  
  
 <span data-ttu-id="27ac7-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="27ac7-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="27ac7-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="27ac7-105">\<bindings></span></span>  
<span data-ttu-id="27ac7-106">\<wsFederatedBinding ></span><span class="sxs-lookup"><span data-stu-id="27ac7-106">\<wsFederatedBinding></span></span>  
<span data-ttu-id="27ac7-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="27ac7-107">\<binding></span></span>  
<span data-ttu-id="27ac7-108">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="27ac7-108">\<security></span></span>  
<span data-ttu-id="27ac7-109">\<İleti ></span><span class="sxs-lookup"><span data-stu-id="27ac7-109">\<message></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27ac7-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="27ac7-110">Syntax</span></span>  
  
```xml  
<wsFederationBinding>  
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
</wsFederationBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="27ac7-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="27ac7-111">Attributes and Elements</span></span>  
 <span data-ttu-id="27ac7-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="27ac7-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="27ac7-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="27ac7-113">Attributes</span></span>  
  
|<span data-ttu-id="27ac7-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="27ac7-114">Attribute</span></span>|<span data-ttu-id="27ac7-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="27ac7-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="27ac7-116">algorithmSuite</span><span class="sxs-lookup"><span data-stu-id="27ac7-116">algorithmSuite</span></span>|<span data-ttu-id="27ac7-117">İleti şifreleme ve anahtar-wrap algoritmaları ayarlar.</span><span class="sxs-lookup"><span data-stu-id="27ac7-117">Sets the message encryption and key-wrap algorithms.</span></span> <span data-ttu-id="27ac7-118">Bu özniteliğin geçerli değerler "algorithmSuite özniteliği" tablosuna bakın.</span><span class="sxs-lookup"><span data-stu-id="27ac7-118">See the "algorithmSuite attribute" table for valid values of this attribute.</span></span> <span data-ttu-id="27ac7-119">Varsayılan değer `Basic256` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="27ac7-119">The default value is `Basic256`.</span></span><br /><br /> <span data-ttu-id="27ac7-120">Bu öznitelik türünde <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span><span class="sxs-lookup"><span data-stu-id="27ac7-120">This attribute is of type <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span></span> <span data-ttu-id="27ac7-121">Bu algoritmalar, güvenlik ilkesi dili (WS-SecurityPolicy) belirtiminde belirtilen eşlenir.</span><span class="sxs-lookup"><span data-stu-id="27ac7-121">These algorithms map to those specified in the Security Policy Language (WS-SecurityPolicy) specification.</span></span>|  
|<span data-ttu-id="27ac7-122">issuedKeyType</span><span class="sxs-lookup"><span data-stu-id="27ac7-122">issuedKeyType</span></span>|<span data-ttu-id="27ac7-123">Kesilecek anahtar türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="27ac7-123">Specifies the type of key to be issued.</span></span> <span data-ttu-id="27ac7-124">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="27ac7-124">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="27ac7-125">-SymmetricKey</span><span class="sxs-lookup"><span data-stu-id="27ac7-125">-   SymmetricKey</span></span><br /><span data-ttu-id="27ac7-126">-PublicKey</span><span class="sxs-lookup"><span data-stu-id="27ac7-126">-   PublicKey</span></span><br /><br /> <span data-ttu-id="27ac7-127">Varsayılan, `SymmetricKey` değeridir.</span><span class="sxs-lookup"><span data-stu-id="27ac7-127">The default is `SymmetricKey`.</span></span> <span data-ttu-id="27ac7-128">Bu öznitelik türünde <xref:System.IdentityModel.Tokens.SecurityKeyType>.</span><span class="sxs-lookup"><span data-stu-id="27ac7-128">This attribute is of type <xref:System.IdentityModel.Tokens.SecurityKeyType>.</span></span>|  
|<span data-ttu-id="27ac7-129">issuedTokenType</span><span class="sxs-lookup"><span data-stu-id="27ac7-129">issuedTokenType</span></span>|<span data-ttu-id="27ac7-130">Verilmesine Belirtecin türü belirten bir URI'yı içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="27ac7-130">A string that contains a URI that specifies the type of token to be issued.</span></span> <span data-ttu-id="27ac7-131">Varsayılan, `null` değeridir.</span><span class="sxs-lookup"><span data-stu-id="27ac7-131">The default is `null`.</span></span>|  
|<span data-ttu-id="27ac7-132">negotiateServiceCredential</span><span class="sxs-lookup"><span data-stu-id="27ac7-132">negotiateServiceCredential</span></span>|<span data-ttu-id="27ac7-133">Hizmet kimlik bilgilerini anlaşmasının bir parçası değiştirilen veya bant dışı kullanılabilir olup olmadığını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="27ac7-133">A Boolean value that specifies whether the service credential should be exchanged as part of negotiation or is available out of band.</span></span> <span data-ttu-id="27ac7-134">Varsayılan değer `true`, hizmet kimlik bilgilerini anlaşılmadan anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="27ac7-134">The default is `true`, which means that the service credential is negotiated.</span></span>|  
  
## <a name="algorithmsuite-attribute"></a><span data-ttu-id="27ac7-135">algorithmSuite özniteliği</span><span class="sxs-lookup"><span data-stu-id="27ac7-135">algorithmSuite Attribute</span></span>  
  
|<span data-ttu-id="27ac7-136">Değer</span><span class="sxs-lookup"><span data-stu-id="27ac7-136">Value</span></span>|<span data-ttu-id="27ac7-137">Açıklama</span><span class="sxs-lookup"><span data-stu-id="27ac7-137">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="27ac7-138">Basic128</span><span class="sxs-lookup"><span data-stu-id="27ac7-138">Basic128</span></span>|<span data-ttu-id="27ac7-139">İleti özeti için Sha1 ve Rsa oaep mgf1p Basic128 şifreleme anahtarı kaydırma için kullanın.</span><span class="sxs-lookup"><span data-stu-id="27ac7-139">Use Basic128 encryption, Sha1 for message digest, and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="27ac7-140">Basic192</span><span class="sxs-lookup"><span data-stu-id="27ac7-140">Basic192</span></span>|<span data-ttu-id="27ac7-141">Basic192 şifreleme, Sha1 oaep Rsa mgf1p anahtar kaydırma için ileti özeti için kullanın.</span><span class="sxs-lookup"><span data-stu-id="27ac7-141">Use Basic192 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="27ac7-142">Basic256</span><span class="sxs-lookup"><span data-stu-id="27ac7-142">Basic256</span></span>|<span data-ttu-id="27ac7-143">Basic256 şifreleme, Sha1 oaep Rsa mgf1p anahtar kaydırma için ileti özeti için kullanın.</span><span class="sxs-lookup"><span data-stu-id="27ac7-143">Use Basic256 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="27ac7-144">Basic256Rsa15</span><span class="sxs-lookup"><span data-stu-id="27ac7-144">Basic256Rsa15</span></span>|<span data-ttu-id="27ac7-145">İleti şifreleme, ileti özeti için Sha1 ve anahtar sarma Rsa15 için Basic256 kullanın.</span><span class="sxs-lookup"><span data-stu-id="27ac7-145">Use Basic256 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="27ac7-146">Basic192Rsa15</span><span class="sxs-lookup"><span data-stu-id="27ac7-146">Basic192Rsa15</span></span>|<span data-ttu-id="27ac7-147">İleti şifreleme, ileti özeti için Sha1 ve anahtar sarma Rsa15 için Basic192 kullanın.</span><span class="sxs-lookup"><span data-stu-id="27ac7-147">Use Basic192 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="27ac7-148">TripleDes</span><span class="sxs-lookup"><span data-stu-id="27ac7-148">TripleDes</span></span>|<span data-ttu-id="27ac7-149">TripleDes şifreleme, Sha1 oaep Rsa mgf1p anahtar kaydırma için ileti özeti için kullanın.</span><span class="sxs-lookup"><span data-stu-id="27ac7-149">Use TripleDes encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="27ac7-150">Basic128Rsa15</span><span class="sxs-lookup"><span data-stu-id="27ac7-150">Basic128Rsa15</span></span>|<span data-ttu-id="27ac7-151">İleti şifreleme, ileti özeti için Sha1 ve anahtar sarma Rsa15 için Basic128 kullanın.</span><span class="sxs-lookup"><span data-stu-id="27ac7-151">Use Basic128 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="27ac7-152">TripleDesRsa15</span><span class="sxs-lookup"><span data-stu-id="27ac7-152">TripleDesRsa15</span></span>|<span data-ttu-id="27ac7-153">TripleDes şifreleme, ileti özeti için Sha1 ve Rsa15 anahtar kaydırma için kullanın.</span><span class="sxs-lookup"><span data-stu-id="27ac7-153">Use TripleDes encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="27ac7-154">Basic128Sha256</span><span class="sxs-lookup"><span data-stu-id="27ac7-154">Basic128Sha256</span></span>|<span data-ttu-id="27ac7-155">İleti şifreleme, ileti özeti için Sha256 ve anahtar kaydırma için Rsa-oaep mgf1p için Basic128 kullanın.</span><span class="sxs-lookup"><span data-stu-id="27ac7-155">Use Basic128 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="27ac7-156">Basic192Sha256</span><span class="sxs-lookup"><span data-stu-id="27ac7-156">Basic192Sha256</span></span>|<span data-ttu-id="27ac7-157">İleti şifreleme, ileti özeti için Sha256 ve anahtar kaydırma için Rsa-oaep mgf1p için Basic192 kullanın.</span><span class="sxs-lookup"><span data-stu-id="27ac7-157">Use Basic192 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="27ac7-158">Basic256Sha256</span><span class="sxs-lookup"><span data-stu-id="27ac7-158">Basic256Sha256</span></span>|<span data-ttu-id="27ac7-159">İleti şifreleme, ileti özeti için Sha256 ve anahtar kaydırma için Rsa-oaep mgf1p için Basic256 kullanın.</span><span class="sxs-lookup"><span data-stu-id="27ac7-159">Use Basic256 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="27ac7-160">TripleDesSha256</span><span class="sxs-lookup"><span data-stu-id="27ac7-160">TripleDesSha256</span></span>|<span data-ttu-id="27ac7-161">TripleDes ileti şifreleme, ileti özeti için Sha256 ve oaep Rsa mgf1p anahtar kaydırma için kullanın.</span><span class="sxs-lookup"><span data-stu-id="27ac7-161">Use TripleDes for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="27ac7-162">Basic128Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="27ac7-162">Basic128Sha256Rsa15</span></span>|<span data-ttu-id="27ac7-163">İleti şifreleme, ileti özeti için Sha256 ve anahtar sarma Rsa15 için Basic128 kullanın.</span><span class="sxs-lookup"><span data-stu-id="27ac7-163">Use Basic128 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="27ac7-164">Basic192Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="27ac7-164">Basic192Sha256Rsa15</span></span>|<span data-ttu-id="27ac7-165">İleti şifreleme, ileti özeti için Sha256 ve anahtar sarma Rsa15 için Aes192 kullanın.</span><span class="sxs-lookup"><span data-stu-id="27ac7-165">Use Aes192 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="27ac7-166">Basic256Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="27ac7-166">Basic256Sha256Rsa15</span></span>|<span data-ttu-id="27ac7-167">İleti şifreleme, ileti özeti için Sha256 ve anahtar sarma Rsa15 için Basic256 kullanın.</span><span class="sxs-lookup"><span data-stu-id="27ac7-167">Use Basic256 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="27ac7-168">TripleDesSha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="27ac7-168">TripleDesSha256Rsa15</span></span>|<span data-ttu-id="27ac7-169">TripleDes ileti şifreleme, ileti özeti için Sha256 ve Rsa15 anahtar kaydırma için kullanın.</span><span class="sxs-lookup"><span data-stu-id="27ac7-169">Use TripleDes for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="27ac7-170">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="27ac7-170">Child Elements</span></span>  
  
|<span data-ttu-id="27ac7-171">Öğe</span><span class="sxs-lookup"><span data-stu-id="27ac7-171">Element</span></span>|<span data-ttu-id="27ac7-172">Açıklama</span><span class="sxs-lookup"><span data-stu-id="27ac7-172">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="27ac7-173">\<claimTypeRequirements ></span><span class="sxs-lookup"><span data-stu-id="27ac7-173">\<claimTypeRequirements></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-element.md)|<span data-ttu-id="27ac7-174">Bu bağlama için talep türleri koleksiyonunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="27ac7-174">Specifies a collection of claim types for this binding.</span></span> <span data-ttu-id="27ac7-175">Her öğe türünde <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span><span class="sxs-lookup"><span data-stu-id="27ac7-175">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span>|  
|<span data-ttu-id="27ac7-176">yayınlayan</span><span class="sxs-lookup"><span data-stu-id="27ac7-176">issuer</span></span>|<span data-ttu-id="27ac7-177">Bir güvenlik belirteci verir bir uç nokta belirtir.</span><span class="sxs-lookup"><span data-stu-id="27ac7-177">Specifies an endpoint that issues a security token.</span></span> <span data-ttu-id="27ac7-178">Bu öğe türünde <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>.</span><span class="sxs-lookup"><span data-stu-id="27ac7-178">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>.</span></span>|  
|<span data-ttu-id="27ac7-179">issuerMetadata</span><span class="sxs-lookup"><span data-stu-id="27ac7-179">issuerMetadata</span></span>|<span data-ttu-id="27ac7-180">Uç nokta adresi verenin belirtir.</span><span class="sxs-lookup"><span data-stu-id="27ac7-180">Specifies the endpoint address of the issuer.</span></span>|  
|[<span data-ttu-id="27ac7-181">\<tokenRequestParameters></span><span class="sxs-lookup"><span data-stu-id="27ac7-181">\<tokenRequestParameters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/tokenrequestparameters.md)|<span data-ttu-id="27ac7-182">Belirteç isteği parametreleri topluluğu.</span><span class="sxs-lookup"><span data-stu-id="27ac7-182">A collection of token request parameters.</span></span> <span data-ttu-id="27ac7-183">Her bir XML öğesi parametresidir.</span><span class="sxs-lookup"><span data-stu-id="27ac7-183">Each parameter is an XML element.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="27ac7-184">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="27ac7-184">Parent Elements</span></span>  
  
|<span data-ttu-id="27ac7-185">Öğe</span><span class="sxs-lookup"><span data-stu-id="27ac7-185">Element</span></span>|<span data-ttu-id="27ac7-186">Açıklama</span><span class="sxs-lookup"><span data-stu-id="27ac7-186">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="27ac7-187">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="27ac7-187">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wsfederationhttpbinding.md)|<span data-ttu-id="27ac7-188">Bağlama için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="27ac7-188">Defines the security settings for a binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="27ac7-189">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="27ac7-189">See Also</span></span>  
 <xref:System.ServiceModel.FederatedMessageSecurityOverHttp>  
 <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement.Message%2A>  
 <xref:System.ServiceModel.WSFederationHttpSecurity.Message%2A>  
 <span data-ttu-id="27ac7-190">`System.ServiceModel.Configuration.FederatedMessageSecurityElement` [Hizmetler ve istemcileri güvenli hale getirme](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)</span><span class="sxs-lookup"><span data-stu-id="27ac7-190">`System.ServiceModel.Configuration.FederatedMessageSecurityElement` [Securing Services and Clients](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)</span></span>  
 [<span data-ttu-id="27ac7-191">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="27ac7-191">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="27ac7-192">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="27ac7-192">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="27ac7-193">Windows Communication Foundation Hizmetleri ve istemcileri yapılandırmak için bağlamaları kullanma</span><span class="sxs-lookup"><span data-stu-id="27ac7-193">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="27ac7-194">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="27ac7-194">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
