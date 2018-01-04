---
title: "&lt;ws2007FederationHttpBinding&gt; &lt;iletisi&gt; öğesi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 52cd941d-e230-4c82-8b29-333a7d20eca8
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 97c0ad9c64046e9c93ce8690016f71d0950fb2d5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltmessagegt-element-of-ltws2007federationhttpbindinggt"></a><span data-ttu-id="34ce4-102">&lt;ws2007FederationHttpBinding&gt; &lt;iletisi&gt; öğesi</span><span class="sxs-lookup"><span data-stu-id="34ce4-102">&lt;message&gt; element of &lt;ws2007FederationHttpBinding&gt;</span></span>
<span data-ttu-id="34ce4-103">İleti düzeyi güvenlik ayarlarını tanımlar [ \<ws2007FederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007federationhttpbinding.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="34ce4-103">Defines settings for the message-level security for the [\<ws2007FederationHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007federationhttpbinding.md) element.</span></span>  
  
 <span data-ttu-id="34ce4-104">\<Sistem. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="34ce4-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="34ce4-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="34ce4-105">\<bindings></span></span>  
<span data-ttu-id="34ce4-106">\<ws2007FederationHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="34ce4-106">\<ws2007FederationHttpBinding></span></span>  
<span data-ttu-id="34ce4-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="34ce4-107">\<binding></span></span>  
<span data-ttu-id="34ce4-108">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="34ce4-108">\<security></span></span>  
<span data-ttu-id="34ce4-109">\<İleti ></span><span class="sxs-lookup"><span data-stu-id="34ce4-109">\<message></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34ce4-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="34ce4-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="34ce4-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="34ce4-111">Attributes and Elements</span></span>  
 <span data-ttu-id="34ce4-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="34ce4-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="34ce4-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="34ce4-113">Attributes</span></span>  
  
|<span data-ttu-id="34ce4-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="34ce4-114">Attribute</span></span>|<span data-ttu-id="34ce4-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="34ce4-115">Description</span></span>|  
|---------------|-----------------|  
|`algorithmSuite`|<span data-ttu-id="34ce4-116">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="34ce4-116">Optional.</span></span> <span data-ttu-id="34ce4-117">İleti şifreleme, imza ve anahtar-wrap algoritmaları ayarlar.</span><span class="sxs-lookup"><span data-stu-id="34ce4-117">Sets the message encryption, signature, and key-wrap algorithms.</span></span> <span data-ttu-id="34ce4-118">Algoritmaları ve anahtar boyutları tarafından belirlenen <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="34ce4-118">The algorithms and the key sizes are determined by the <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> class.</span></span> <span data-ttu-id="34ce4-119">Bu algoritmalar, güvenlik ilkesi dili (WS-SecurityPolicy) belirtiminde belirtilen eşlenir.</span><span class="sxs-lookup"><span data-stu-id="34ce4-119">These algorithms map to those specified in the Security Policy Language (WS-SecurityPolicy) specification.</span></span><br /><br /> <span data-ttu-id="34ce4-120">Olası değerler için aşağıdaki tabloya bakın.</span><span class="sxs-lookup"><span data-stu-id="34ce4-120">See the following table for possible values.</span></span> <span data-ttu-id="34ce4-121">Basic256 varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="34ce4-121">The default value is Basic256.</span></span>|  
|`issuedKeyType`|<span data-ttu-id="34ce4-122">Kesilecek anahtar türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="34ce4-122">Specifies the type of key to be issued.</span></span> <span data-ttu-id="34ce4-123">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="34ce4-123">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="34ce4-124">-SymmetricKey</span><span class="sxs-lookup"><span data-stu-id="34ce4-124">-   SymmetricKey</span></span><br /><span data-ttu-id="34ce4-125">-PublicKey</span><span class="sxs-lookup"><span data-stu-id="34ce4-125">-   PublicKey</span></span><br /><span data-ttu-id="34ce4-126">-BearerKey</span><span class="sxs-lookup"><span data-stu-id="34ce4-126">-   BearerKey</span></span><br /><br /> <span data-ttu-id="34ce4-127">SymmetricKey varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="34ce4-127">The default is SymmetricKey.</span></span> <span data-ttu-id="34ce4-128">Bu öznitelik türünde <xref:System.IdentityModel.Tokens.SecurityKeyType>.</span><span class="sxs-lookup"><span data-stu-id="34ce4-128">This attribute is of type <xref:System.IdentityModel.Tokens.SecurityKeyType>.</span></span>|  
|`issuedTokenType`|<span data-ttu-id="34ce4-129">Kesilecek Belirtecin türü belirtir URI.</span><span class="sxs-lookup"><span data-stu-id="34ce4-129">A URI that specifies the type of token to be issued.</span></span> <span data-ttu-id="34ce4-130">Varsayılan, `null` değeridir.</span><span class="sxs-lookup"><span data-stu-id="34ce4-130">The default is `null`.</span></span>|  
|`negotiateServiceCredential`|<span data-ttu-id="34ce4-131">Hizmet kimlik bilgilerini anlaşmasının bir parçası değiştirilen veya bant dışı kullanılabilir olup olmadığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="34ce4-131">A value that specifies whether the service credential should be exchanged as part of negotiation or is available out of band.</span></span> <span data-ttu-id="34ce4-132">Varsayılan değer `true`, hizmet kimlik bilgilerini anlaşılmadan anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="34ce4-132">The default is `true`, which means that the service credential is negotiated.</span></span>|  
  
## <a name="algorithmsuite-attribute"></a><span data-ttu-id="34ce4-133">algorithmSuite özniteliği</span><span class="sxs-lookup"><span data-stu-id="34ce4-133">algorithmSuite Attribute</span></span>  
  
|<span data-ttu-id="34ce4-134">Değer</span><span class="sxs-lookup"><span data-stu-id="34ce4-134">Value</span></span>|<span data-ttu-id="34ce4-135">Açıklama</span><span class="sxs-lookup"><span data-stu-id="34ce4-135">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="34ce4-136">Basic128</span><span class="sxs-lookup"><span data-stu-id="34ce4-136">Basic128</span></span>|<span data-ttu-id="34ce4-137">İleti özeti için Sha1 ve Rsa oaep mgf1p Aes128 şifreleme anahtarı kaydırma için kullanın.</span><span class="sxs-lookup"><span data-stu-id="34ce4-137">Use Aes128 encryption, Sha1 for message digest, and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="34ce4-138">Basic192</span><span class="sxs-lookup"><span data-stu-id="34ce4-138">Basic192</span></span>|<span data-ttu-id="34ce4-139">Aes192 şifreleme, Sha1 oaep Rsa mgf1p anahtar kaydırma için ileti özeti için kullanın.</span><span class="sxs-lookup"><span data-stu-id="34ce4-139">Use Aes192 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="34ce4-140">Basic256</span><span class="sxs-lookup"><span data-stu-id="34ce4-140">Basic256</span></span>|<span data-ttu-id="34ce4-141">Aes256 şifreleme, Sha1 oaep Rsa mgf1p anahtar kaydırma için ileti özeti için kullanın.</span><span class="sxs-lookup"><span data-stu-id="34ce4-141">Use Aes256 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="34ce4-142">Basic256Rsa15</span><span class="sxs-lookup"><span data-stu-id="34ce4-142">Basic256Rsa15</span></span>|<span data-ttu-id="34ce4-143">İleti şifreleme, ileti özeti için Sha1 ve anahtar sarma Rsa15 için Aes256 kullanın.</span><span class="sxs-lookup"><span data-stu-id="34ce4-143">Use Aes256 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="34ce4-144">Basic192Rsa15</span><span class="sxs-lookup"><span data-stu-id="34ce4-144">Basic192Rsa15</span></span>|<span data-ttu-id="34ce4-145">İleti şifreleme, ileti özeti için Sha1 ve anahtar sarma Rsa15 için Aes192 kullanın.</span><span class="sxs-lookup"><span data-stu-id="34ce4-145">Use Aes192 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="34ce4-146">TripleDes</span><span class="sxs-lookup"><span data-stu-id="34ce4-146">TripleDes</span></span>|<span data-ttu-id="34ce4-147">TripleDes şifreleme, Sha1 oaep Rsa mgf1p anahtar kaydırma için ileti özeti için kullanın.</span><span class="sxs-lookup"><span data-stu-id="34ce4-147">Use TripleDes encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="34ce4-148">Basic128Rsa15</span><span class="sxs-lookup"><span data-stu-id="34ce4-148">Basic128Rsa15</span></span>|<span data-ttu-id="34ce4-149">İleti şifreleme, ileti özeti için Sha1 ve anahtar sarma Rsa15 için Aes128 kullanın.</span><span class="sxs-lookup"><span data-stu-id="34ce4-149">Use Aes128 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="34ce4-150">TripleDesRsa15</span><span class="sxs-lookup"><span data-stu-id="34ce4-150">TripleDesRsa15</span></span>|<span data-ttu-id="34ce4-151">TripleDes şifreleme, ileti özeti için Sha1 ve Rsa15 anahtar kaydırma için kullanın.</span><span class="sxs-lookup"><span data-stu-id="34ce4-151">Use TripleDes encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="34ce4-152">Basic128Sha256</span><span class="sxs-lookup"><span data-stu-id="34ce4-152">Basic128Sha256</span></span>|<span data-ttu-id="34ce4-153">İleti şifreleme, ileti özeti için Sha256 ve oaep Rsa mgf1p anahtar kaydırma için için Aes256 kullanın.</span><span class="sxs-lookup"><span data-stu-id="34ce4-153">Use Aes256 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="34ce4-154">Basic192Sha256</span><span class="sxs-lookup"><span data-stu-id="34ce4-154">Basic192Sha256</span></span>|<span data-ttu-id="34ce4-155">İleti şifreleme, ileti özeti için Sha256 ve anahtar kaydırma için Rsa-oaep mgf1p için Aes192 kullanın.</span><span class="sxs-lookup"><span data-stu-id="34ce4-155">Use Aes192 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="34ce4-156">Basic256Sha256</span><span class="sxs-lookup"><span data-stu-id="34ce4-156">Basic256Sha256</span></span>|<span data-ttu-id="34ce4-157">İleti şifreleme, ileti özeti için Sha256 ve oaep Rsa mgf1p anahtar kaydırma için için Aes256 kullanın.</span><span class="sxs-lookup"><span data-stu-id="34ce4-157">Use Aes256 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="34ce4-158">TripleDesSha256</span><span class="sxs-lookup"><span data-stu-id="34ce4-158">TripleDesSha256</span></span>|<span data-ttu-id="34ce4-159">TripleDes ileti şifreleme, ileti özeti için Sha256 ve oaep Rsa mgf1p anahtar kaydırma için kullanın.</span><span class="sxs-lookup"><span data-stu-id="34ce4-159">Use TripleDes for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="34ce4-160">Basic128Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="34ce4-160">Basic128Sha256Rsa15</span></span>|<span data-ttu-id="34ce4-161">İleti şifreleme, ileti özeti için Sha256 ve anahtar sarma Rsa15 için Aes128 kullanın.</span><span class="sxs-lookup"><span data-stu-id="34ce4-161">Use Aes128 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="34ce4-162">Basic192Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="34ce4-162">Basic192Sha256Rsa15</span></span>|<span data-ttu-id="34ce4-163">İleti şifreleme, ileti özeti için Sha256 ve anahtar sarma Rsa15 için Aes192 kullanın.</span><span class="sxs-lookup"><span data-stu-id="34ce4-163">Use Aes192 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="34ce4-164">Basic256Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="34ce4-164">Basic256Sha256Rsa15</span></span>|<span data-ttu-id="34ce4-165">İleti şifreleme, ileti özeti için Sha256 ve anahtar sarma Rsa15 için Aes256 kullanın.</span><span class="sxs-lookup"><span data-stu-id="34ce4-165">Use Aes256 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="34ce4-166">TripleDesSha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="34ce4-166">TripleDesSha256Rsa15</span></span>|<span data-ttu-id="34ce4-167">TripleDes ileti şifreleme, ileti özeti için Sha256 ve Rsa15 anahtar kaydırma için kullanın.</span><span class="sxs-lookup"><span data-stu-id="34ce4-167">Use TripleDes for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="34ce4-168">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="34ce4-168">Child Elements</span></span>  
  
|<span data-ttu-id="34ce4-169">Öğe</span><span class="sxs-lookup"><span data-stu-id="34ce4-169">Element</span></span>|<span data-ttu-id="34ce4-170">Açıklama</span><span class="sxs-lookup"><span data-stu-id="34ce4-170">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="34ce4-171">\<claimTypeRequirements ></span><span class="sxs-lookup"><span data-stu-id="34ce4-171">\<claimTypeRequirements></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-element.md)|<span data-ttu-id="34ce4-172">Bu bağlama için talep türleri koleksiyonunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="34ce4-172">Specifies a collection of claim types for this binding.</span></span> <span data-ttu-id="34ce4-173">Her öğe türünde <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span><span class="sxs-lookup"><span data-stu-id="34ce4-173">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span>|  
|[<span data-ttu-id="34ce4-174">\<veren ></span><span class="sxs-lookup"><span data-stu-id="34ce4-174">\<issuer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuer.md)|<span data-ttu-id="34ce4-175">Bir güvenlik belirteci verir bir uç nokta belirtir.</span><span class="sxs-lookup"><span data-stu-id="34ce4-175">Specifies an endpoint that issues a security token.</span></span> <span data-ttu-id="34ce4-176">Bu öğe türünde <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>.</span><span class="sxs-lookup"><span data-stu-id="34ce4-176">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>.</span></span>|  
|[<span data-ttu-id="34ce4-177">\<İssuedtokenparameters ></span><span class="sxs-lookup"><span data-stu-id="34ce4-177">\<issuerMetadata></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuermetadata.md)|<span data-ttu-id="34ce4-178">Uç nokta adresi verenin belirtir.</span><span class="sxs-lookup"><span data-stu-id="34ce4-178">Specifies the endpoint address of the issuer.</span></span>|  
|[<span data-ttu-id="34ce4-179">\<tokenRequestParameters ></span><span class="sxs-lookup"><span data-stu-id="34ce4-179">\<tokenRequestParameters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/tokenrequestparameters.md)|<span data-ttu-id="34ce4-180">Belirteç isteği parametreleri topluluğu.</span><span class="sxs-lookup"><span data-stu-id="34ce4-180">A collection of token request parameters.</span></span> <span data-ttu-id="34ce4-181">Her bir XML öğesi parametresidir.</span><span class="sxs-lookup"><span data-stu-id="34ce4-181">Each parameter is an XML element.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="34ce4-182">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="34ce4-182">Parent Elements</span></span>  
  
|<span data-ttu-id="34ce4-183">Öğe</span><span class="sxs-lookup"><span data-stu-id="34ce4-183">Element</span></span>|<span data-ttu-id="34ce4-184">Açıklama</span><span class="sxs-lookup"><span data-stu-id="34ce4-184">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="34ce4-185">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="34ce4-185">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md)|<span data-ttu-id="34ce4-186">Bağlama için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="34ce4-186">Defines the security settings for a binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="34ce4-187">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="34ce4-187">See Also</span></span>  
 <xref:System.ServiceModel.FederatedMessageSecurityOverHttp>  
 <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement.Message%2A>  
 <xref:System.ServiceModel.WSFederationHttpSecurity.Message%2A>  
 <span data-ttu-id="34ce4-188">`System.ServiceModel.Configuration.FederatedMessageSecurityElement`[Hizmetler ve istemcileri güvenli hale getirme](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)</span><span class="sxs-lookup"><span data-stu-id="34ce4-188">`System.ServiceModel.Configuration.FederatedMessageSecurityElement` [Securing Services and Clients](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)</span></span>  
 [<span data-ttu-id="34ce4-189">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="34ce4-189">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="34ce4-190">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="34ce4-190">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="34ce4-191">Windows Communication Foundation Hizmetleri ve istemcileri yapılandırmak için bağlamaları kullanma</span><span class="sxs-lookup"><span data-stu-id="34ce4-191">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="34ce4-192">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="34ce4-192">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
