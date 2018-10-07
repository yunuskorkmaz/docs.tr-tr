---
title: '&lt;wsFederationHttpBinding&gt; &lt;iletisi&gt; öğesi'
ms.date: 03/30/2017
ms.assetid: 9d710389-d9d8-4454-9bf2-da4ccda31cec
ms.openlocfilehash: d959d43d9f7d232dea2972b81f1ad2697c8d494a
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2018
ms.locfileid: "48840325"
---
# <a name="ltmessagegt-element-of-ltwsfederationhttpbindinggt"></a><span data-ttu-id="e6440-102">&lt;wsFederationHttpBinding&gt; &lt;iletisi&gt; öğesi</span><span class="sxs-lookup"><span data-stu-id="e6440-102">&lt;message&gt; element of &lt;wsFederationHttpBinding&gt;</span></span>
<span data-ttu-id="e6440-103">İleti düzeyi güvenlik ayarlarını tanımlar [ \<wsFederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="e6440-103">Defines the settings for the message-level security for the [\<wsFederationHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md).</span></span>  
  
 <span data-ttu-id="e6440-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="e6440-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="e6440-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="e6440-105">\<bindings></span></span>  
<span data-ttu-id="e6440-106">\<wsFederatedBinding ></span><span class="sxs-lookup"><span data-stu-id="e6440-106">\<wsFederatedBinding></span></span>  
<span data-ttu-id="e6440-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="e6440-107">\<binding></span></span>  
<span data-ttu-id="e6440-108">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="e6440-108">\<security></span></span>  
<span data-ttu-id="e6440-109">\<İleti ></span><span class="sxs-lookup"><span data-stu-id="e6440-109">\<message></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6440-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e6440-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e6440-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="e6440-111">Attributes and Elements</span></span>  
 <span data-ttu-id="e6440-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e6440-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e6440-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e6440-113">Attributes</span></span>  
  
|<span data-ttu-id="e6440-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="e6440-114">Attribute</span></span>|<span data-ttu-id="e6440-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e6440-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e6440-116">algorithmSuite</span><span class="sxs-lookup"><span data-stu-id="e6440-116">algorithmSuite</span></span>|<span data-ttu-id="e6440-117">İleti şifreleme ve anahtar-wrap algoritmaları ayarlar.</span><span class="sxs-lookup"><span data-stu-id="e6440-117">Sets the message encryption and key-wrap algorithms.</span></span> <span data-ttu-id="e6440-118">Bu özniteliğin geçerli değerleri için "algorithmSuite özniteliği" tablosuna bakın.</span><span class="sxs-lookup"><span data-stu-id="e6440-118">See the "algorithmSuite attribute" table for valid values of this attribute.</span></span> <span data-ttu-id="e6440-119">Varsayılan değer `Basic256` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="e6440-119">The default value is `Basic256`.</span></span><br /><br /> <span data-ttu-id="e6440-120">Bu öznitelik türünde <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span><span class="sxs-lookup"><span data-stu-id="e6440-120">This attribute is of type <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span></span> <span data-ttu-id="e6440-121">Bu algoritmalar, güvenlik ilkesi dili (WS-SecurityPolicy) belirtiminde belirtilen platformlarla eşlenir.</span><span class="sxs-lookup"><span data-stu-id="e6440-121">These algorithms map to those specified in the Security Policy Language (WS-SecurityPolicy) specification.</span></span>|  
|<span data-ttu-id="e6440-122">issuedKeyType</span><span class="sxs-lookup"><span data-stu-id="e6440-122">issuedKeyType</span></span>|<span data-ttu-id="e6440-123">Kesilecek anahtar türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="e6440-123">Specifies the type of key to be issued.</span></span> <span data-ttu-id="e6440-124">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="e6440-124">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="e6440-125">-SymmetricKey</span><span class="sxs-lookup"><span data-stu-id="e6440-125">-   SymmetricKey</span></span><br /><span data-ttu-id="e6440-126">-PublicKey</span><span class="sxs-lookup"><span data-stu-id="e6440-126">-   PublicKey</span></span><br /><br /> <span data-ttu-id="e6440-127">Varsayılan, `SymmetricKey` değeridir.</span><span class="sxs-lookup"><span data-stu-id="e6440-127">The default is `SymmetricKey`.</span></span> <span data-ttu-id="e6440-128">Bu öznitelik türünde <xref:System.IdentityModel.Tokens.SecurityKeyType>.</span><span class="sxs-lookup"><span data-stu-id="e6440-128">This attribute is of type <xref:System.IdentityModel.Tokens.SecurityKeyType>.</span></span>|  
|<span data-ttu-id="e6440-129">issuedTokenType</span><span class="sxs-lookup"><span data-stu-id="e6440-129">issuedTokenType</span></span>|<span data-ttu-id="e6440-130">Verilmesi için belirteç türünü belirten bir URI içeren dize.</span><span class="sxs-lookup"><span data-stu-id="e6440-130">A string that contains a URI that specifies the type of token to be issued.</span></span> <span data-ttu-id="e6440-131">Varsayılan, `null` değeridir.</span><span class="sxs-lookup"><span data-stu-id="e6440-131">The default is `null`.</span></span>|  
|<span data-ttu-id="e6440-132">negotiateServiceCredential</span><span class="sxs-lookup"><span data-stu-id="e6440-132">negotiateServiceCredential</span></span>|<span data-ttu-id="e6440-133">Hizmet kimlik bilgisi anlaşmasının bir parçası değiştirilen veya bant dışından mevcut olup olmadığını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="e6440-133">A Boolean value that specifies whether the service credential should be exchanged as part of negotiation or is available out of band.</span></span> <span data-ttu-id="e6440-134">Varsayılan `true`, hizmet kimlik bilgisi anlaşılır anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="e6440-134">The default is `true`, which means that the service credential is negotiated.</span></span>|  
  
## <a name="algorithmsuite-attribute"></a><span data-ttu-id="e6440-135">algorithmSuite özniteliği</span><span class="sxs-lookup"><span data-stu-id="e6440-135">algorithmSuite Attribute</span></span>  
  
|<span data-ttu-id="e6440-136">Değer</span><span class="sxs-lookup"><span data-stu-id="e6440-136">Value</span></span>|<span data-ttu-id="e6440-137">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e6440-137">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e6440-138">Basic128</span><span class="sxs-lookup"><span data-stu-id="e6440-138">Basic128</span></span>|<span data-ttu-id="e6440-139">İleti özeti için Sha1 ve Rsa oaep mgf1p Basic128 şifreleme anahtarı kaydırma için kullanın.</span><span class="sxs-lookup"><span data-stu-id="e6440-139">Use Basic128 encryption, Sha1 for message digest, and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="e6440-140">Basic192</span><span class="sxs-lookup"><span data-stu-id="e6440-140">Basic192</span></span>|<span data-ttu-id="e6440-141">İleti özeti, anahtar kaydırma için Rsa-oaep mgf1p için Sha1 Basic192 şifrelemesi kullanın.</span><span class="sxs-lookup"><span data-stu-id="e6440-141">Use Basic192 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="e6440-142">Basic256</span><span class="sxs-lookup"><span data-stu-id="e6440-142">Basic256</span></span>|<span data-ttu-id="e6440-143">İleti özeti, anahtar kaydırma için Rsa-oaep mgf1p için Sha1 Basic256 şifrelemesi kullanın.</span><span class="sxs-lookup"><span data-stu-id="e6440-143">Use Basic256 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="e6440-144">Basic256Rsa15</span><span class="sxs-lookup"><span data-stu-id="e6440-144">Basic256Rsa15</span></span>|<span data-ttu-id="e6440-145">İleti şifreleme, ileti özeti için Sha1 ve anahtar kaydırma için Rsa15 Basic256 kullanın.</span><span class="sxs-lookup"><span data-stu-id="e6440-145">Use Basic256 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="e6440-146">Basic192Rsa15</span><span class="sxs-lookup"><span data-stu-id="e6440-146">Basic192Rsa15</span></span>|<span data-ttu-id="e6440-147">İleti şifreleme, ileti özeti için Sha1 ve anahtar kaydırma için Rsa15 Basic192 kullanın.</span><span class="sxs-lookup"><span data-stu-id="e6440-147">Use Basic192 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="e6440-148">TripleDes</span><span class="sxs-lookup"><span data-stu-id="e6440-148">TripleDes</span></span>|<span data-ttu-id="e6440-149">İleti özeti, anahtar kaydırma için Rsa-oaep mgf1p için Sha1 TripleDes şifrelemesi kullanın.</span><span class="sxs-lookup"><span data-stu-id="e6440-149">Use TripleDes encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="e6440-150">Basic128Rsa15</span><span class="sxs-lookup"><span data-stu-id="e6440-150">Basic128Rsa15</span></span>|<span data-ttu-id="e6440-151">İleti şifreleme, ileti özeti için Sha1 ve anahtar kaydırma için Rsa15 Basic128 kullanın.</span><span class="sxs-lookup"><span data-stu-id="e6440-151">Use Basic128 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="e6440-152">TripleDesRsa15</span><span class="sxs-lookup"><span data-stu-id="e6440-152">TripleDesRsa15</span></span>|<span data-ttu-id="e6440-153">İleti özeti için Sha1 ve anahtar kaydırma için Rsa15 TripleDes şifrelemesi kullanın.</span><span class="sxs-lookup"><span data-stu-id="e6440-153">Use TripleDes encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="e6440-154">Basic128Sha256</span><span class="sxs-lookup"><span data-stu-id="e6440-154">Basic128Sha256</span></span>|<span data-ttu-id="e6440-155">İleti şifreleme, ileti özeti için Sha256 ve anahtar kaydırma için Rsa-oaep mgf1p Basic128 kullanın.</span><span class="sxs-lookup"><span data-stu-id="e6440-155">Use Basic128 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="e6440-156">Basic192Sha256</span><span class="sxs-lookup"><span data-stu-id="e6440-156">Basic192Sha256</span></span>|<span data-ttu-id="e6440-157">İleti şifreleme, ileti özeti için Sha256 ve anahtar kaydırma için Rsa-oaep mgf1p Basic192 kullanın.</span><span class="sxs-lookup"><span data-stu-id="e6440-157">Use Basic192 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="e6440-158">Basic256Sha256</span><span class="sxs-lookup"><span data-stu-id="e6440-158">Basic256Sha256</span></span>|<span data-ttu-id="e6440-159">İleti şifreleme, ileti özeti için Sha256 ve anahtar kaydırma için Rsa-oaep mgf1p Basic256 kullanın.</span><span class="sxs-lookup"><span data-stu-id="e6440-159">Use Basic256 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="e6440-160">TripleDesSha256</span><span class="sxs-lookup"><span data-stu-id="e6440-160">TripleDesSha256</span></span>|<span data-ttu-id="e6440-161">TripleDes ileti özeti için Sha256 ve anahtar kaydırma için Rsa-oaep mgf1p ileti şifreleme için kullanın.</span><span class="sxs-lookup"><span data-stu-id="e6440-161">Use TripleDes for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="e6440-162">Basic128Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="e6440-162">Basic128Sha256Rsa15</span></span>|<span data-ttu-id="e6440-163">İleti şifreleme, ileti özeti için Sha256 ve anahtar kaydırma için Rsa15 Basic128 kullanın.</span><span class="sxs-lookup"><span data-stu-id="e6440-163">Use Basic128 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="e6440-164">Basic192Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="e6440-164">Basic192Sha256Rsa15</span></span>|<span data-ttu-id="e6440-165">İleti şifreleme, ileti özeti için Sha256 ve anahtar kaydırma için Rsa15 Aes192 kullanın.</span><span class="sxs-lookup"><span data-stu-id="e6440-165">Use Aes192 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="e6440-166">Basic256Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="e6440-166">Basic256Sha256Rsa15</span></span>|<span data-ttu-id="e6440-167">İleti şifreleme, ileti özeti için Sha256 ve anahtar kaydırma için Rsa15 Basic256 kullanın.</span><span class="sxs-lookup"><span data-stu-id="e6440-167">Use Basic256 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="e6440-168">TripleDesSha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="e6440-168">TripleDesSha256Rsa15</span></span>|<span data-ttu-id="e6440-169">TripleDes ileti özeti için Sha256 ve anahtar kaydırma için Rsa15 ileti şifreleme için kullanın.</span><span class="sxs-lookup"><span data-stu-id="e6440-169">Use TripleDes for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e6440-170">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="e6440-170">Child Elements</span></span>  
  
|<span data-ttu-id="e6440-171">Öğe</span><span class="sxs-lookup"><span data-stu-id="e6440-171">Element</span></span>|<span data-ttu-id="e6440-172">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e6440-172">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e6440-173">\<claimTypeRequirements ></span><span class="sxs-lookup"><span data-stu-id="e6440-173">\<claimTypeRequirements></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-element.md)|<span data-ttu-id="e6440-174">Bu bağlama için talep türlerinin koleksiyonunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="e6440-174">Specifies a collection of claim types for this binding.</span></span> <span data-ttu-id="e6440-175">Her öğe türünde <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span><span class="sxs-lookup"><span data-stu-id="e6440-175">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span>|  
|<span data-ttu-id="e6440-176">yayınlayan</span><span class="sxs-lookup"><span data-stu-id="e6440-176">issuer</span></span>|<span data-ttu-id="e6440-177">Bir güvenlik belirteci veren bir uç noktasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="e6440-177">Specifies an endpoint that issues a security token.</span></span> <span data-ttu-id="e6440-178">Bu öğe türünde <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>.</span><span class="sxs-lookup"><span data-stu-id="e6440-178">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>.</span></span>|  
|<span data-ttu-id="e6440-179">issuerMetadata</span><span class="sxs-lookup"><span data-stu-id="e6440-179">issuerMetadata</span></span>|<span data-ttu-id="e6440-180">Verenin uç nokta adresini belirtir.</span><span class="sxs-lookup"><span data-stu-id="e6440-180">Specifies the endpoint address of the issuer.</span></span>|  
|[<span data-ttu-id="e6440-181">\<tokenRequestParameters></span><span class="sxs-lookup"><span data-stu-id="e6440-181">\<tokenRequestParameters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/tokenrequestparameters.md)|<span data-ttu-id="e6440-182">Belirteç isteği parametreleri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="e6440-182">A collection of token request parameters.</span></span> <span data-ttu-id="e6440-183">Her bir XML öğesi parametredir.</span><span class="sxs-lookup"><span data-stu-id="e6440-183">Each parameter is an XML element.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e6440-184">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="e6440-184">Parent Elements</span></span>  
  
|<span data-ttu-id="e6440-185">Öğe</span><span class="sxs-lookup"><span data-stu-id="e6440-185">Element</span></span>|<span data-ttu-id="e6440-186">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e6440-186">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e6440-187">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="e6440-187">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wsfederationhttpbinding.md)|<span data-ttu-id="e6440-188">Bir bağlama için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e6440-188">Defines the security settings for a binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e6440-189">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e6440-189">See Also</span></span>  
 <xref:System.ServiceModel.FederatedMessageSecurityOverHttp>  
 <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement.Message%2A>  
 <xref:System.ServiceModel.WSFederationHttpSecurity.Message%2A>  
 <span data-ttu-id="e6440-190">`System.ServiceModel.Configuration.FederatedMessageSecurityElement` [Hizmetler ve istemcileri güvenli hale getirme](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)</span><span class="sxs-lookup"><span data-stu-id="e6440-190">`System.ServiceModel.Configuration.FederatedMessageSecurityElement` [Securing Services and Clients](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)</span></span>  
 [<span data-ttu-id="e6440-191">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="e6440-191">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="e6440-192">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="e6440-192">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="e6440-193">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="e6440-193">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [<span data-ttu-id="e6440-194">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="e6440-194">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
