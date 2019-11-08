---
title: <wsFederationHttpBinding> <message> öğesi
ms.date: 03/30/2017
ms.assetid: 9d710389-d9d8-4454-9bf2-da4ccda31cec
ms.openlocfilehash: 8e0903dd1313e68e2de65730e129079199ebe2f2
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738985"
---
# <a name="message-element-of-wsfederationhttpbinding"></a><span data-ttu-id="86a32-102">\<wsFederationHttpBinding > \<ileti > öğesi</span><span class="sxs-lookup"><span data-stu-id="86a32-102">\<message> element of \<wsFederationHttpBinding></span></span>
<span data-ttu-id="86a32-103">[\<wsFederationHttpBinding >](wsfederationhttpbinding.md)için ileti düzeyi güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="86a32-103">Defines the settings for the message-level security for the [\<wsFederationHttpBinding>](wsfederationhttpbinding.md).</span></span>  
  
<span data-ttu-id="86a32-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="86a32-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="86a32-105">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="86a32-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="86a32-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bağlamaları >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="86a32-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="86a32-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<wsFederationHttpBinding >** ](wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="86a32-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)</span></span>\
<span data-ttu-id="86a32-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<bağlama >** </span><span class="sxs-lookup"><span data-stu-id="86a32-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="86a32-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<güvenlik >** ](security-of-wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="86a32-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-wsfederationhttpbinding.md)</span></span>\
<span data-ttu-id="86a32-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<ileti >**</span><span class="sxs-lookup"><span data-stu-id="86a32-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<message>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86a32-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="86a32-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="86a32-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="86a32-112">Attributes and Elements</span></span>  
 <span data-ttu-id="86a32-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="86a32-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="86a32-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="86a32-114">Attributes</span></span>  
  
|<span data-ttu-id="86a32-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="86a32-115">Attribute</span></span>|<span data-ttu-id="86a32-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="86a32-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="86a32-117">algorithmSuite</span><span class="sxs-lookup"><span data-stu-id="86a32-117">algorithmSuite</span></span>|<span data-ttu-id="86a32-118">İleti şifrelemesini ve anahtar sarması algoritmalarını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="86a32-118">Sets the message encryption and key-wrap algorithms.</span></span> <span data-ttu-id="86a32-119">Bu özniteliğin geçerli değerleri için "algorithmSuite Attribute" tablosuna bakın.</span><span class="sxs-lookup"><span data-stu-id="86a32-119">See the "algorithmSuite attribute" table for valid values of this attribute.</span></span> <span data-ttu-id="86a32-120">Varsayılan değer `Basic256` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="86a32-120">The default value is `Basic256`.</span></span><br /><br /> <span data-ttu-id="86a32-121">Bu öznitelik <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>türündedir.</span><span class="sxs-lookup"><span data-stu-id="86a32-121">This attribute is of type <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span></span> <span data-ttu-id="86a32-122">Bu algoritmalar güvenlik Ilkesi dili (WS-SecurityPolicy) belirtiminde belirtilen olanlarla eşlenir.</span><span class="sxs-lookup"><span data-stu-id="86a32-122">These algorithms map to those specified in the Security Policy Language (WS-SecurityPolicy) specification.</span></span>|  
|<span data-ttu-id="86a32-123">IssuedKeyType</span><span class="sxs-lookup"><span data-stu-id="86a32-123">issuedKeyType</span></span>|<span data-ttu-id="86a32-124">Verilecek anahtarın türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="86a32-124">Specifies the type of key to be issued.</span></span> <span data-ttu-id="86a32-125">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="86a32-125">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="86a32-126">-SymmetricKey</span><span class="sxs-lookup"><span data-stu-id="86a32-126">-   SymmetricKey</span></span><br /><span data-ttu-id="86a32-127">-PublicKey</span><span class="sxs-lookup"><span data-stu-id="86a32-127">-   PublicKey</span></span><br /><br /> <span data-ttu-id="86a32-128">Varsayılan, `SymmetricKey` değeridir.</span><span class="sxs-lookup"><span data-stu-id="86a32-128">The default is `SymmetricKey`.</span></span> <span data-ttu-id="86a32-129">Bu öznitelik <xref:System.IdentityModel.Tokens.SecurityKeyType>türündedir.</span><span class="sxs-lookup"><span data-stu-id="86a32-129">This attribute is of type <xref:System.IdentityModel.Tokens.SecurityKeyType>.</span></span>|  
|<span data-ttu-id="86a32-130">IssuedTokenType</span><span class="sxs-lookup"><span data-stu-id="86a32-130">issuedTokenType</span></span>|<span data-ttu-id="86a32-131">Verilecek belirtecin türünü belirten bir URI içeren dize.</span><span class="sxs-lookup"><span data-stu-id="86a32-131">A string that contains a URI that specifies the type of token to be issued.</span></span> <span data-ttu-id="86a32-132">Varsayılan, `null` değeridir.</span><span class="sxs-lookup"><span data-stu-id="86a32-132">The default is `null`.</span></span>|  
|<span data-ttu-id="86a32-133">negotiateServiceCredential</span><span class="sxs-lookup"><span data-stu-id="86a32-133">negotiateServiceCredential</span></span>|<span data-ttu-id="86a32-134">Hizmet kimlik bilgisinin, anlaşmanın parçası olarak alınıp alınmayacağını veya bant dışı kullanılabilir olup olmadığını belirten bir Boolean değer.</span><span class="sxs-lookup"><span data-stu-id="86a32-134">A Boolean value that specifies whether the service credential should be exchanged as part of negotiation or is available out of band.</span></span> <span data-ttu-id="86a32-135">Varsayılan değer `true`, bu, hizmet kimlik bilgisinin üzerinde anlaşılan anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="86a32-135">The default is `true`, which means that the service credential is negotiated.</span></span>|  
  
## <a name="algorithmsuite-attribute"></a><span data-ttu-id="86a32-136">algorithmSuite özniteliği</span><span class="sxs-lookup"><span data-stu-id="86a32-136">algorithmSuite Attribute</span></span>  
  
|<span data-ttu-id="86a32-137">Değer</span><span class="sxs-lookup"><span data-stu-id="86a32-137">Value</span></span>|<span data-ttu-id="86a32-138">Açıklama</span><span class="sxs-lookup"><span data-stu-id="86a32-138">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="86a32-139">Basic128</span><span class="sxs-lookup"><span data-stu-id="86a32-139">Basic128</span></span>|<span data-ttu-id="86a32-140">Anahtar kaydırması için Basic128 şifrelemesi, ileti özeti için SHA1 ve rsa-oaep-mgf1p kullanın.</span><span class="sxs-lookup"><span data-stu-id="86a32-140">Use Basic128 encryption, Sha1 for message digest, and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="86a32-141">Basic192</span><span class="sxs-lookup"><span data-stu-id="86a32-141">Basic192</span></span>|<span data-ttu-id="86a32-142">Anahtar kaydırması için Basic192 şifrelemesi, ileti özeti için SHA1, rsa-oaep-mgf1p kullanın.</span><span class="sxs-lookup"><span data-stu-id="86a32-142">Use Basic192 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="86a32-143">Basic256</span><span class="sxs-lookup"><span data-stu-id="86a32-143">Basic256</span></span>|<span data-ttu-id="86a32-144">Anahtar kaydırması için Basic256 şifrelemesi, ileti özeti için SHA1, rsa-oaep-mgf1p kullanın.</span><span class="sxs-lookup"><span data-stu-id="86a32-144">Use Basic256 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="86a32-145">Basic256Rsa15</span><span class="sxs-lookup"><span data-stu-id="86a32-145">Basic256Rsa15</span></span>|<span data-ttu-id="86a32-146">İleti şifreleme için Basic256, ileti özeti için SHA1 ve anahtar kaydırması için Rsa15 kullanın.</span><span class="sxs-lookup"><span data-stu-id="86a32-146">Use Basic256 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="86a32-147">Basic192Rsa15</span><span class="sxs-lookup"><span data-stu-id="86a32-147">Basic192Rsa15</span></span>|<span data-ttu-id="86a32-148">İleti şifreleme için Basic192, ileti özeti için SHA1 ve anahtar kaydırması için Rsa15 kullanın.</span><span class="sxs-lookup"><span data-stu-id="86a32-148">Use Basic192 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="86a32-149">TripleDes</span><span class="sxs-lookup"><span data-stu-id="86a32-149">TripleDes</span></span>|<span data-ttu-id="86a32-150">Anahtar kaydırması için, TripleDes şifrelemesi, ileti özeti için SHA1, rsa-oaep-mgf1p kullanın.</span><span class="sxs-lookup"><span data-stu-id="86a32-150">Use TripleDes encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="86a32-151">Basic128Rsa15</span><span class="sxs-lookup"><span data-stu-id="86a32-151">Basic128Rsa15</span></span>|<span data-ttu-id="86a32-152">İleti şifreleme için Basic128, ileti özeti için SHA1 ve anahtar kaydırması için Rsa15 kullanın.</span><span class="sxs-lookup"><span data-stu-id="86a32-152">Use Basic128 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="86a32-153">TripleDesRsa15</span><span class="sxs-lookup"><span data-stu-id="86a32-153">TripleDesRsa15</span></span>|<span data-ttu-id="86a32-154">TripleDes şifrelemesi, ileti özeti için SHA1 ve anahtar kaydırması için Rsa15 kullanın.</span><span class="sxs-lookup"><span data-stu-id="86a32-154">Use TripleDes encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="86a32-155">Basic128Sha256</span><span class="sxs-lookup"><span data-stu-id="86a32-155">Basic128Sha256</span></span>|<span data-ttu-id="86a32-156">İleti için Basic128, ileti özeti için SHA256, anahtar kaydırması için rsa-oaep-mgf1p kullanın.</span><span class="sxs-lookup"><span data-stu-id="86a32-156">Use Basic128 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="86a32-157">Basic192Sha256</span><span class="sxs-lookup"><span data-stu-id="86a32-157">Basic192Sha256</span></span>|<span data-ttu-id="86a32-158">İleti için Basic192, ileti özeti için SHA256, anahtar kaydırması için rsa-oaep-mgf1p kullanın.</span><span class="sxs-lookup"><span data-stu-id="86a32-158">Use Basic192 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="86a32-159">Basic256Sha256</span><span class="sxs-lookup"><span data-stu-id="86a32-159">Basic256Sha256</span></span>|<span data-ttu-id="86a32-160">İleti için Basic256, ileti özeti için SHA256, anahtar kaydırması için rsa-oaep-mgf1p kullanın.</span><span class="sxs-lookup"><span data-stu-id="86a32-160">Use Basic256 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="86a32-161">TripleDesSha256</span><span class="sxs-lookup"><span data-stu-id="86a32-161">TripleDesSha256</span></span>|<span data-ttu-id="86a32-162">İleti şifreleme için TripleDes, SHA256 for Message Digest ve rsa-oaep-mgf1p için anahtar kaydırması kullanın.</span><span class="sxs-lookup"><span data-stu-id="86a32-162">Use TripleDes for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="86a32-163">Basic128Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="86a32-163">Basic128Sha256Rsa15</span></span>|<span data-ttu-id="86a32-164">İleti şifreleme için Basic128, ileti özeti için SHA256 ve anahtar kaydırması için Rsa15 kullanın.</span><span class="sxs-lookup"><span data-stu-id="86a32-164">Use Basic128 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="86a32-165">Basic192Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="86a32-165">Basic192Sha256Rsa15</span></span>|<span data-ttu-id="86a32-166">İleti şifreleme için Aes192, ileti özeti için SHA256 ve anahtar kaydırması için Rsa15 kullanın.</span><span class="sxs-lookup"><span data-stu-id="86a32-166">Use Aes192 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="86a32-167">Basic256Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="86a32-167">Basic256Sha256Rsa15</span></span>|<span data-ttu-id="86a32-168">İleti şifreleme için Basic256, ileti özeti için SHA256 ve anahtar kaydırması için Rsa15 kullanın.</span><span class="sxs-lookup"><span data-stu-id="86a32-168">Use Basic256 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="86a32-169">TripleDesSha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="86a32-169">TripleDesSha256Rsa15</span></span>|<span data-ttu-id="86a32-170">İleti şifreleme için TripleDes, SHA256 for Message Digest ve Rsa15 anahtar kaydırması için kullanın.</span><span class="sxs-lookup"><span data-stu-id="86a32-170">Use TripleDes for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="86a32-171">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="86a32-171">Child Elements</span></span>  
  
|<span data-ttu-id="86a32-172">Öğe</span><span class="sxs-lookup"><span data-stu-id="86a32-172">Element</span></span>|<span data-ttu-id="86a32-173">Açıklama</span><span class="sxs-lookup"><span data-stu-id="86a32-173">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="86a32-174">\<claimTypeRequirements ></span><span class="sxs-lookup"><span data-stu-id="86a32-174">\<claimTypeRequirements></span></span>](claimtyperequirements-element.md)|<span data-ttu-id="86a32-175">Bu bağlama için bir talep türleri koleksiyonu belirtir.</span><span class="sxs-lookup"><span data-stu-id="86a32-175">Specifies a collection of claim types for this binding.</span></span> <span data-ttu-id="86a32-176">Her öğe <xref:System.ServiceModel.Configuration.ClaimTypeElement>türündedir.</span><span class="sxs-lookup"><span data-stu-id="86a32-176">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span>|  
|<span data-ttu-id="86a32-177">yayınlayan</span><span class="sxs-lookup"><span data-stu-id="86a32-177">issuer</span></span>|<span data-ttu-id="86a32-178">Bir güvenlik belirteci veren bir uç nokta belirtir.</span><span class="sxs-lookup"><span data-stu-id="86a32-178">Specifies an endpoint that issues a security token.</span></span> <span data-ttu-id="86a32-179">Bu öğe <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>türündedir.</span><span class="sxs-lookup"><span data-stu-id="86a32-179">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>.</span></span>|  
|<span data-ttu-id="86a32-180">issuerMetadata</span><span class="sxs-lookup"><span data-stu-id="86a32-180">issuerMetadata</span></span>|<span data-ttu-id="86a32-181">Verenin uç nokta adresini belirtir.</span><span class="sxs-lookup"><span data-stu-id="86a32-181">Specifies the endpoint address of the issuer.</span></span>|  
|[<span data-ttu-id="86a32-182">\<tokenRequestParameters ></span><span class="sxs-lookup"><span data-stu-id="86a32-182">\<tokenRequestParameters></span></span>](tokenrequestparameters.md)|<span data-ttu-id="86a32-183">Belirteç isteği parametrelerinin bir koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="86a32-183">A collection of token request parameters.</span></span> <span data-ttu-id="86a32-184">Her parametre bir XML öğesidir.</span><span class="sxs-lookup"><span data-stu-id="86a32-184">Each parameter is an XML element.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="86a32-185">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="86a32-185">Parent Elements</span></span>  
  
|<span data-ttu-id="86a32-186">Öğe</span><span class="sxs-lookup"><span data-stu-id="86a32-186">Element</span></span>|<span data-ttu-id="86a32-187">Açıklama</span><span class="sxs-lookup"><span data-stu-id="86a32-187">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="86a32-188">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="86a32-188">\<security></span></span>](security-of-wsfederationhttpbinding.md)|<span data-ttu-id="86a32-189">Bağlama için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="86a32-189">Defines the security settings for a binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="86a32-190">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="86a32-190">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp>
- <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement.Message%2A>
- <xref:System.ServiceModel.WSFederationHttpSecurity.Message%2A>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>
- [<span data-ttu-id="86a32-191">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="86a32-191">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="86a32-192">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="86a32-192">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="86a32-193">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="86a32-193">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="86a32-194">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="86a32-194">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="86a32-195">\< bağlama ></span><span class="sxs-lookup"><span data-stu-id="86a32-195">\<binding></span></span>](bindings.md)
