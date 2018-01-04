---
title: "&lt;wsFederationHttpBinding&gt; &lt;iletisi&gt; öğesi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9d710389-d9d8-4454-9bf2-da4ccda31cec
caps.latest.revision: "28"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 09e384311f50553585c0a7a14a51df20858fb439
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltmessagegt-element-of-ltwsfederationhttpbindinggt"></a><span data-ttu-id="bd602-102">&lt;wsFederationHttpBinding&gt; &lt;iletisi&gt; öğesi</span><span class="sxs-lookup"><span data-stu-id="bd602-102">&lt;message&gt; element of &lt;wsFederationHttpBinding&gt;</span></span>
<span data-ttu-id="bd602-103">İleti düzeyi güvenlik ayarlarını tanımlar [ \<wsFederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="bd602-103">Defines the settings for the message-level security for the [\<wsFederationHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md).</span></span>  
  
 <span data-ttu-id="bd602-104">\<Sistem. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="bd602-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="bd602-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="bd602-105">\<bindings></span></span>  
<span data-ttu-id="bd602-106">\<wsFederatedBinding ></span><span class="sxs-lookup"><span data-stu-id="bd602-106">\<wsFederatedBinding></span></span>  
<span data-ttu-id="bd602-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="bd602-107">\<binding></span></span>  
<span data-ttu-id="bd602-108">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="bd602-108">\<security></span></span>  
<span data-ttu-id="bd602-109">\<İleti ></span><span class="sxs-lookup"><span data-stu-id="bd602-109">\<message></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd602-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bd602-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bd602-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="bd602-111">Attributes and Elements</span></span>  
 <span data-ttu-id="bd602-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="bd602-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bd602-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="bd602-113">Attributes</span></span>  
  
|<span data-ttu-id="bd602-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="bd602-114">Attribute</span></span>|<span data-ttu-id="bd602-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bd602-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="bd602-116">algorithmSuite</span><span class="sxs-lookup"><span data-stu-id="bd602-116">algorithmSuite</span></span>|<span data-ttu-id="bd602-117">İleti şifreleme ve anahtar-wrap algoritmaları ayarlar.</span><span class="sxs-lookup"><span data-stu-id="bd602-117">Sets the message encryption and key-wrap algorithms.</span></span> <span data-ttu-id="bd602-118">Bu özniteliğin geçerli değerler "algorithmSuite özniteliği" tablosuna bakın.</span><span class="sxs-lookup"><span data-stu-id="bd602-118">See the "algorithmSuite attribute" table for valid values of this attribute.</span></span> <span data-ttu-id="bd602-119">Varsayılan değer `Basic256` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="bd602-119">The default value is `Basic256`.</span></span><br /><br /> <span data-ttu-id="bd602-120">Bu öznitelik türünde <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span><span class="sxs-lookup"><span data-stu-id="bd602-120">This attribute is of type <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span></span> <span data-ttu-id="bd602-121">Bu algoritmalar, güvenlik ilkesi dili (WS-SecurityPolicy) belirtiminde belirtilen eşlenir.</span><span class="sxs-lookup"><span data-stu-id="bd602-121">These algorithms map to those specified in the Security Policy Language (WS-SecurityPolicy) specification.</span></span>|  
|<span data-ttu-id="bd602-122">issuedKeyType</span><span class="sxs-lookup"><span data-stu-id="bd602-122">issuedKeyType</span></span>|<span data-ttu-id="bd602-123">Kesilecek anahtar türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="bd602-123">Specifies the type of key to be issued.</span></span> <span data-ttu-id="bd602-124">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="bd602-124">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="bd602-125">-SymmetricKey</span><span class="sxs-lookup"><span data-stu-id="bd602-125">-   SymmetricKey</span></span><br /><span data-ttu-id="bd602-126">-PublicKey</span><span class="sxs-lookup"><span data-stu-id="bd602-126">-   PublicKey</span></span><br /><br /> <span data-ttu-id="bd602-127">Varsayılan, `SymmetricKey` değeridir.</span><span class="sxs-lookup"><span data-stu-id="bd602-127">The default is `SymmetricKey`.</span></span> <span data-ttu-id="bd602-128">Bu öznitelik türünde <xref:System.IdentityModel.Tokens.SecurityKeyType>.</span><span class="sxs-lookup"><span data-stu-id="bd602-128">This attribute is of type <xref:System.IdentityModel.Tokens.SecurityKeyType>.</span></span>|  
|<span data-ttu-id="bd602-129">issuedTokenType</span><span class="sxs-lookup"><span data-stu-id="bd602-129">issuedTokenType</span></span>|<span data-ttu-id="bd602-130">Verilmesine Belirtecin türü belirten bir URI'yı içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="bd602-130">A string that contains a URI that specifies the type of token to be issued.</span></span> <span data-ttu-id="bd602-131">Varsayılan, `null` değeridir.</span><span class="sxs-lookup"><span data-stu-id="bd602-131">The default is `null`.</span></span>|  
|<span data-ttu-id="bd602-132">negotiateServiceCredential</span><span class="sxs-lookup"><span data-stu-id="bd602-132">negotiateServiceCredential</span></span>|<span data-ttu-id="bd602-133">Hizmet kimlik bilgilerini anlaşmasının bir parçası değiştirilen veya bant dışı kullanılabilir olup olmadığını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="bd602-133">A Boolean value that specifies whether the service credential should be exchanged as part of negotiation or is available out of band.</span></span> <span data-ttu-id="bd602-134">Varsayılan değer `true`, hizmet kimlik bilgilerini anlaşılmadan anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="bd602-134">The default is `true`, which means that the service credential is negotiated.</span></span>|  
  
## <a name="algorithmsuite-attribute"></a><span data-ttu-id="bd602-135">algorithmSuite özniteliği</span><span class="sxs-lookup"><span data-stu-id="bd602-135">algorithmSuite Attribute</span></span>  
  
|<span data-ttu-id="bd602-136">Değer</span><span class="sxs-lookup"><span data-stu-id="bd602-136">Value</span></span>|<span data-ttu-id="bd602-137">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bd602-137">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="bd602-138">Basic128</span><span class="sxs-lookup"><span data-stu-id="bd602-138">Basic128</span></span>|<span data-ttu-id="bd602-139">İleti özeti için Sha1 ve Rsa oaep mgf1p Basic128 şifreleme anahtarı kaydırma için kullanın.</span><span class="sxs-lookup"><span data-stu-id="bd602-139">Use Basic128 encryption, Sha1 for message digest, and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="bd602-140">Basic192</span><span class="sxs-lookup"><span data-stu-id="bd602-140">Basic192</span></span>|<span data-ttu-id="bd602-141">Basic192 şifreleme, Sha1 oaep Rsa mgf1p anahtar kaydırma için ileti özeti için kullanın.</span><span class="sxs-lookup"><span data-stu-id="bd602-141">Use Basic192 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="bd602-142">Basic256</span><span class="sxs-lookup"><span data-stu-id="bd602-142">Basic256</span></span>|<span data-ttu-id="bd602-143">Basic256 şifreleme, Sha1 oaep Rsa mgf1p anahtar kaydırma için ileti özeti için kullanın.</span><span class="sxs-lookup"><span data-stu-id="bd602-143">Use Basic256 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="bd602-144">Basic256Rsa15</span><span class="sxs-lookup"><span data-stu-id="bd602-144">Basic256Rsa15</span></span>|<span data-ttu-id="bd602-145">İleti şifreleme, ileti özeti için Sha1 ve anahtar sarma Rsa15 için Basic256 kullanın.</span><span class="sxs-lookup"><span data-stu-id="bd602-145">Use Basic256 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="bd602-146">Basic192Rsa15</span><span class="sxs-lookup"><span data-stu-id="bd602-146">Basic192Rsa15</span></span>|<span data-ttu-id="bd602-147">İleti şifreleme, ileti özeti için Sha1 ve anahtar sarma Rsa15 için Basic192 kullanın.</span><span class="sxs-lookup"><span data-stu-id="bd602-147">Use Basic192 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="bd602-148">TripleDes</span><span class="sxs-lookup"><span data-stu-id="bd602-148">TripleDes</span></span>|<span data-ttu-id="bd602-149">TripleDes şifreleme, Sha1 oaep Rsa mgf1p anahtar kaydırma için ileti özeti için kullanın.</span><span class="sxs-lookup"><span data-stu-id="bd602-149">Use TripleDes encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="bd602-150">Basic128Rsa15</span><span class="sxs-lookup"><span data-stu-id="bd602-150">Basic128Rsa15</span></span>|<span data-ttu-id="bd602-151">İleti şifreleme, ileti özeti için Sha1 ve anahtar sarma Rsa15 için Basic128 kullanın.</span><span class="sxs-lookup"><span data-stu-id="bd602-151">Use Basic128 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="bd602-152">TripleDesRsa15</span><span class="sxs-lookup"><span data-stu-id="bd602-152">TripleDesRsa15</span></span>|<span data-ttu-id="bd602-153">TripleDes şifreleme, ileti özeti için Sha1 ve Rsa15 anahtar kaydırma için kullanın.</span><span class="sxs-lookup"><span data-stu-id="bd602-153">Use TripleDes encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="bd602-154">Basic128Sha256</span><span class="sxs-lookup"><span data-stu-id="bd602-154">Basic128Sha256</span></span>|<span data-ttu-id="bd602-155">İleti şifreleme, ileti özeti için Sha256 ve anahtar kaydırma için Rsa-oaep mgf1p için Basic128 kullanın.</span><span class="sxs-lookup"><span data-stu-id="bd602-155">Use Basic128 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="bd602-156">Basic192Sha256</span><span class="sxs-lookup"><span data-stu-id="bd602-156">Basic192Sha256</span></span>|<span data-ttu-id="bd602-157">İleti şifreleme, ileti özeti için Sha256 ve anahtar kaydırma için Rsa-oaep mgf1p için Basic192 kullanın.</span><span class="sxs-lookup"><span data-stu-id="bd602-157">Use Basic192 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="bd602-158">Basic256Sha256</span><span class="sxs-lookup"><span data-stu-id="bd602-158">Basic256Sha256</span></span>|<span data-ttu-id="bd602-159">İleti şifreleme, ileti özeti için Sha256 ve anahtar kaydırma için Rsa-oaep mgf1p için Basic256 kullanın.</span><span class="sxs-lookup"><span data-stu-id="bd602-159">Use Basic256 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="bd602-160">TripleDesSha256</span><span class="sxs-lookup"><span data-stu-id="bd602-160">TripleDesSha256</span></span>|<span data-ttu-id="bd602-161">TripleDes ileti şifreleme, ileti özeti için Sha256 ve oaep Rsa mgf1p anahtar kaydırma için kullanın.</span><span class="sxs-lookup"><span data-stu-id="bd602-161">Use TripleDes for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="bd602-162">Basic128Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="bd602-162">Basic128Sha256Rsa15</span></span>|<span data-ttu-id="bd602-163">İleti şifreleme, ileti özeti için Sha256 ve anahtar sarma Rsa15 için Basic128 kullanın.</span><span class="sxs-lookup"><span data-stu-id="bd602-163">Use Basic128 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="bd602-164">Basic192Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="bd602-164">Basic192Sha256Rsa15</span></span>|<span data-ttu-id="bd602-165">İleti şifreleme, ileti özeti için Sha256 ve anahtar sarma Rsa15 için Aes192 kullanın.</span><span class="sxs-lookup"><span data-stu-id="bd602-165">Use Aes192 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="bd602-166">Basic256Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="bd602-166">Basic256Sha256Rsa15</span></span>|<span data-ttu-id="bd602-167">İleti şifreleme, ileti özeti için Sha256 ve anahtar sarma Rsa15 için Basic256 kullanın.</span><span class="sxs-lookup"><span data-stu-id="bd602-167">Use Basic256 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="bd602-168">TripleDesSha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="bd602-168">TripleDesSha256Rsa15</span></span>|<span data-ttu-id="bd602-169">TripleDes ileti şifreleme, ileti özeti için Sha256 ve Rsa15 anahtar kaydırma için kullanın.</span><span class="sxs-lookup"><span data-stu-id="bd602-169">Use TripleDes for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bd602-170">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="bd602-170">Child Elements</span></span>  
  
|<span data-ttu-id="bd602-171">Öğe</span><span class="sxs-lookup"><span data-stu-id="bd602-171">Element</span></span>|<span data-ttu-id="bd602-172">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bd602-172">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bd602-173">\<claimTypeRequirements ></span><span class="sxs-lookup"><span data-stu-id="bd602-173">\<claimTypeRequirements></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-element.md)|<span data-ttu-id="bd602-174">Bu bağlama için talep türleri koleksiyonunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="bd602-174">Specifies a collection of claim types for this binding.</span></span> <span data-ttu-id="bd602-175">Her öğe türünde <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span><span class="sxs-lookup"><span data-stu-id="bd602-175">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span>|  
|<span data-ttu-id="bd602-176">yayınlayan</span><span class="sxs-lookup"><span data-stu-id="bd602-176">issuer</span></span>|<span data-ttu-id="bd602-177">Bir güvenlik belirteci verir bir uç nokta belirtir.</span><span class="sxs-lookup"><span data-stu-id="bd602-177">Specifies an endpoint that issues a security token.</span></span> <span data-ttu-id="bd602-178">Bu öğe türünde <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>.</span><span class="sxs-lookup"><span data-stu-id="bd602-178">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>.</span></span>|  
|<span data-ttu-id="bd602-179">issuerMetadata</span><span class="sxs-lookup"><span data-stu-id="bd602-179">issuerMetadata</span></span>|<span data-ttu-id="bd602-180">Uç nokta adresi verenin belirtir.</span><span class="sxs-lookup"><span data-stu-id="bd602-180">Specifies the endpoint address of the issuer.</span></span>|  
|[<span data-ttu-id="bd602-181">\<tokenRequestParameters ></span><span class="sxs-lookup"><span data-stu-id="bd602-181">\<tokenRequestParameters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/tokenrequestparameters.md)|<span data-ttu-id="bd602-182">Belirteç isteği parametreleri topluluğu.</span><span class="sxs-lookup"><span data-stu-id="bd602-182">A collection of token request parameters.</span></span> <span data-ttu-id="bd602-183">Her bir XML öğesi parametresidir.</span><span class="sxs-lookup"><span data-stu-id="bd602-183">Each parameter is an XML element.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="bd602-184">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="bd602-184">Parent Elements</span></span>  
  
|<span data-ttu-id="bd602-185">Öğe</span><span class="sxs-lookup"><span data-stu-id="bd602-185">Element</span></span>|<span data-ttu-id="bd602-186">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bd602-186">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bd602-187">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="bd602-187">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wsfederationhttpbinding.md)|<span data-ttu-id="bd602-188">Bağlama için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="bd602-188">Defines the security settings for a binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bd602-189">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="bd602-189">See Also</span></span>  
 <xref:System.ServiceModel.FederatedMessageSecurityOverHttp>  
 <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement.Message%2A>  
 <xref:System.ServiceModel.WSFederationHttpSecurity.Message%2A>  
 <span data-ttu-id="bd602-190">`System.ServiceModel.Configuration.FederatedMessageSecurityElement`[Hizmetler ve istemcileri güvenli hale getirme](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)</span><span class="sxs-lookup"><span data-stu-id="bd602-190">`System.ServiceModel.Configuration.FederatedMessageSecurityElement` [Securing Services and Clients](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)</span></span>  
 [<span data-ttu-id="bd602-191">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="bd602-191">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="bd602-192">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="bd602-192">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="bd602-193">Windows Communication Foundation Hizmetleri ve istemcileri yapılandırmak için bağlamaları kullanma</span><span class="sxs-lookup"><span data-stu-id="bd602-193">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="bd602-194">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="bd602-194">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
