---
title: <ws2007FederationHttpBinding> <message> öğesi
ms.date: 03/30/2017
ms.assetid: 52cd941d-e230-4c82-8b29-333a7d20eca8
ms.openlocfilehash: dde763687dbc62d6fb342a21a4c614208f28d7e8
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73739003"
---
# <a name="message-element-of-ws2007federationhttpbinding"></a><span data-ttu-id="285b7-102">\<ws2007FederationHttpBinding > \<ileti > öğesi</span><span class="sxs-lookup"><span data-stu-id="285b7-102">\<message> element of \<ws2007FederationHttpBinding></span></span>
<span data-ttu-id="285b7-103">[\<ws2007FederationHttpBinding >](ws2007federationhttpbinding.md) öğesi için ileti düzeyi güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="285b7-103">Defines settings for the message-level security for the [\<ws2007FederationHttpBinding>](ws2007federationhttpbinding.md) element.</span></span>  
  
<span data-ttu-id="285b7-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="285b7-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="285b7-105">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="285b7-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="285b7-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bağlamaları >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="285b7-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="285b7-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<ws2007FederationHttpBinding >** ](ws2007federationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="285b7-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<ws2007FederationHttpBinding>**](ws2007federationhttpbinding.md)</span></span>\
<span data-ttu-id="285b7-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<bağlama >** </span><span class="sxs-lookup"><span data-stu-id="285b7-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="285b7-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<güvenlik >** ](security-element-of-ws2007federationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="285b7-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-element-of-ws2007federationhttpbinding.md)</span></span>\
<span data-ttu-id="285b7-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<ileti >**</span><span class="sxs-lookup"><span data-stu-id="285b7-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<message>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="285b7-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="285b7-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="285b7-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="285b7-112">Attributes and Elements</span></span>  
 <span data-ttu-id="285b7-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="285b7-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="285b7-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="285b7-114">Attributes</span></span>  
  
|<span data-ttu-id="285b7-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="285b7-115">Attribute</span></span>|<span data-ttu-id="285b7-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="285b7-116">Description</span></span>|  
|---------------|-----------------|  
|`algorithmSuite`|<span data-ttu-id="285b7-117">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="285b7-117">Optional.</span></span> <span data-ttu-id="285b7-118">İleti şifrelemesini, imzayı ve anahtar sarması algoritmalarını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="285b7-118">Sets the message encryption, signature, and key-wrap algorithms.</span></span> <span data-ttu-id="285b7-119">Algoritmalar ve anahtar boyutları <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> sınıfı tarafından belirlenir.</span><span class="sxs-lookup"><span data-stu-id="285b7-119">The algorithms and the key sizes are determined by the <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> class.</span></span> <span data-ttu-id="285b7-120">Bu algoritmalar güvenlik Ilkesi dili (WS-SecurityPolicy) belirtiminde belirtilen olanlarla eşlenir.</span><span class="sxs-lookup"><span data-stu-id="285b7-120">These algorithms map to those specified in the Security Policy Language (WS-SecurityPolicy) specification.</span></span><br /><br /> <span data-ttu-id="285b7-121">Olası değerler için aşağıdaki tabloya bakın.</span><span class="sxs-lookup"><span data-stu-id="285b7-121">See the following table for possible values.</span></span> <span data-ttu-id="285b7-122">Varsayılan değer Basic256 ' dir.</span><span class="sxs-lookup"><span data-stu-id="285b7-122">The default value is Basic256.</span></span>|  
|`issuedKeyType`|<span data-ttu-id="285b7-123">Verilecek anahtarın türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="285b7-123">Specifies the type of key to be issued.</span></span> <span data-ttu-id="285b7-124">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="285b7-124">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="285b7-125">-SymmetricKey</span><span class="sxs-lookup"><span data-stu-id="285b7-125">-   SymmetricKey</span></span><br /><span data-ttu-id="285b7-126">-PublicKey</span><span class="sxs-lookup"><span data-stu-id="285b7-126">-   PublicKey</span></span><br /><span data-ttu-id="285b7-127">-Yataerkey</span><span class="sxs-lookup"><span data-stu-id="285b7-127">-   BearerKey</span></span><br /><br /> <span data-ttu-id="285b7-128">Varsayılan değer SymmetricKey ' dir.</span><span class="sxs-lookup"><span data-stu-id="285b7-128">The default is SymmetricKey.</span></span> <span data-ttu-id="285b7-129">Bu öznitelik <xref:System.IdentityModel.Tokens.SecurityKeyType>türündedir.</span><span class="sxs-lookup"><span data-stu-id="285b7-129">This attribute is of type <xref:System.IdentityModel.Tokens.SecurityKeyType>.</span></span>|  
|`issuedTokenType`|<span data-ttu-id="285b7-130">Verilecek belirtecin türünü belirten bir URI.</span><span class="sxs-lookup"><span data-stu-id="285b7-130">A URI that specifies the type of token to be issued.</span></span> <span data-ttu-id="285b7-131">Varsayılan, `null` değeridir.</span><span class="sxs-lookup"><span data-stu-id="285b7-131">The default is `null`.</span></span>|  
|`negotiateServiceCredential`|<span data-ttu-id="285b7-132">Hizmet kimlik bilgisinin, anlaşmanın parçası olarak alınıp alınmayacağını veya bant dışı kullanılabilir olup olmadığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="285b7-132">A value that specifies whether the service credential should be exchanged as part of negotiation or is available out of band.</span></span> <span data-ttu-id="285b7-133">Varsayılan değer `true`, bu, hizmet kimlik bilgisinin üzerinde anlaşılan anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="285b7-133">The default is `true`, which means that the service credential is negotiated.</span></span>|  
  
## <a name="algorithmsuite-attribute"></a><span data-ttu-id="285b7-134">algorithmSuite özniteliği</span><span class="sxs-lookup"><span data-stu-id="285b7-134">algorithmSuite Attribute</span></span>  
  
|<span data-ttu-id="285b7-135">Değer</span><span class="sxs-lookup"><span data-stu-id="285b7-135">Value</span></span>|<span data-ttu-id="285b7-136">Açıklama</span><span class="sxs-lookup"><span data-stu-id="285b7-136">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="285b7-137">Basic128</span><span class="sxs-lookup"><span data-stu-id="285b7-137">Basic128</span></span>|<span data-ttu-id="285b7-138">Anahtar kaydırması için AES128 şifrelemesi, ileti özeti için SHA1 ve rsa-oaep-mgf1p kullanın.</span><span class="sxs-lookup"><span data-stu-id="285b7-138">Use Aes128 encryption, Sha1 for message digest, and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="285b7-139">Basic192</span><span class="sxs-lookup"><span data-stu-id="285b7-139">Basic192</span></span>|<span data-ttu-id="285b7-140">Anahtar kaydırması için Aes192 şifrelemesi, ileti özeti için SHA1, rsa-oaep-mgf1p kullanın.</span><span class="sxs-lookup"><span data-stu-id="285b7-140">Use Aes192 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="285b7-141">Basic256</span><span class="sxs-lookup"><span data-stu-id="285b7-141">Basic256</span></span>|<span data-ttu-id="285b7-142">Anahtar kaydırması için AES256 şifrelemesi, ileti özeti için SHA1, rsa-oaep-mgf1p kullanın.</span><span class="sxs-lookup"><span data-stu-id="285b7-142">Use Aes256 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="285b7-143">Basic256Rsa15</span><span class="sxs-lookup"><span data-stu-id="285b7-143">Basic256Rsa15</span></span>|<span data-ttu-id="285b7-144">İleti şifreleme için AES256, ileti özeti için SHA1 ve anahtar kaydırması için Rsa15 kullanın.</span><span class="sxs-lookup"><span data-stu-id="285b7-144">Use Aes256 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="285b7-145">Basic192Rsa15</span><span class="sxs-lookup"><span data-stu-id="285b7-145">Basic192Rsa15</span></span>|<span data-ttu-id="285b7-146">İleti şifreleme için Aes192, ileti özeti için SHA1 ve anahtar kaydırması için Rsa15 kullanın.</span><span class="sxs-lookup"><span data-stu-id="285b7-146">Use Aes192 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="285b7-147">TripleDes</span><span class="sxs-lookup"><span data-stu-id="285b7-147">TripleDes</span></span>|<span data-ttu-id="285b7-148">Anahtar kaydırması için, TripleDes şifrelemesi, ileti özeti için SHA1, rsa-oaep-mgf1p kullanın.</span><span class="sxs-lookup"><span data-stu-id="285b7-148">Use TripleDes encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="285b7-149">Basic128Rsa15</span><span class="sxs-lookup"><span data-stu-id="285b7-149">Basic128Rsa15</span></span>|<span data-ttu-id="285b7-150">İleti şifreleme için AES128, ileti özeti için SHA1 ve anahtar kaydırması için Rsa15 kullanın.</span><span class="sxs-lookup"><span data-stu-id="285b7-150">Use Aes128 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="285b7-151">TripleDesRsa15</span><span class="sxs-lookup"><span data-stu-id="285b7-151">TripleDesRsa15</span></span>|<span data-ttu-id="285b7-152">TripleDes şifrelemesi, ileti özeti için SHA1 ve anahtar kaydırması için Rsa15 kullanın.</span><span class="sxs-lookup"><span data-stu-id="285b7-152">Use TripleDes encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="285b7-153">Basic128Sha256</span><span class="sxs-lookup"><span data-stu-id="285b7-153">Basic128Sha256</span></span>|<span data-ttu-id="285b7-154">İleti için AES256, ileti özeti için SHA256, anahtar kaydırması için rsa-oaep-mgf1p kullanın.</span><span class="sxs-lookup"><span data-stu-id="285b7-154">Use Aes256 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="285b7-155">Basic192Sha256</span><span class="sxs-lookup"><span data-stu-id="285b7-155">Basic192Sha256</span></span>|<span data-ttu-id="285b7-156">İleti için Aes192, ileti özeti için SHA256, anahtar kaydırması için rsa-oaep-mgf1p kullanın.</span><span class="sxs-lookup"><span data-stu-id="285b7-156">Use Aes192 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="285b7-157">Basic256Sha256</span><span class="sxs-lookup"><span data-stu-id="285b7-157">Basic256Sha256</span></span>|<span data-ttu-id="285b7-158">İleti için AES256, ileti özeti için SHA256, anahtar kaydırması için rsa-oaep-mgf1p kullanın.</span><span class="sxs-lookup"><span data-stu-id="285b7-158">Use Aes256 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="285b7-159">TripleDesSha256</span><span class="sxs-lookup"><span data-stu-id="285b7-159">TripleDesSha256</span></span>|<span data-ttu-id="285b7-160">İleti şifreleme için TripleDes, SHA256 for Message Digest ve rsa-oaep-mgf1p için anahtar kaydırması kullanın.</span><span class="sxs-lookup"><span data-stu-id="285b7-160">Use TripleDes for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="285b7-161">Basic128Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="285b7-161">Basic128Sha256Rsa15</span></span>|<span data-ttu-id="285b7-162">İleti şifreleme için AES128, ileti özeti için SHA256 ve anahtar kaydırması için Rsa15 kullanın.</span><span class="sxs-lookup"><span data-stu-id="285b7-162">Use Aes128 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="285b7-163">Basic192Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="285b7-163">Basic192Sha256Rsa15</span></span>|<span data-ttu-id="285b7-164">İleti şifreleme için Aes192, ileti özeti için SHA256 ve anahtar kaydırması için Rsa15 kullanın.</span><span class="sxs-lookup"><span data-stu-id="285b7-164">Use Aes192 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="285b7-165">Basic256Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="285b7-165">Basic256Sha256Rsa15</span></span>|<span data-ttu-id="285b7-166">İleti şifreleme için AES256, ileti özeti için SHA256 ve anahtar kaydırması için Rsa15 kullanın.</span><span class="sxs-lookup"><span data-stu-id="285b7-166">Use Aes256 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="285b7-167">TripleDesSha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="285b7-167">TripleDesSha256Rsa15</span></span>|<span data-ttu-id="285b7-168">İleti şifreleme için TripleDes, SHA256 for Message Digest ve Rsa15 anahtar kaydırması için kullanın.</span><span class="sxs-lookup"><span data-stu-id="285b7-168">Use TripleDes for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="285b7-169">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="285b7-169">Child Elements</span></span>  
  
|<span data-ttu-id="285b7-170">Öğe</span><span class="sxs-lookup"><span data-stu-id="285b7-170">Element</span></span>|<span data-ttu-id="285b7-171">Açıklama</span><span class="sxs-lookup"><span data-stu-id="285b7-171">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="285b7-172">\<claimTypeRequirements ></span><span class="sxs-lookup"><span data-stu-id="285b7-172">\<claimTypeRequirements></span></span>](claimtyperequirements-element.md)|<span data-ttu-id="285b7-173">Bu bağlama için bir talep türleri koleksiyonu belirtir.</span><span class="sxs-lookup"><span data-stu-id="285b7-173">Specifies a collection of claim types for this binding.</span></span> <span data-ttu-id="285b7-174">Her öğe <xref:System.ServiceModel.Configuration.ClaimTypeElement>türündedir.</span><span class="sxs-lookup"><span data-stu-id="285b7-174">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span>|  
|[<span data-ttu-id="285b7-175">\<veren ></span><span class="sxs-lookup"><span data-stu-id="285b7-175">\<issuer></span></span>](issuer.md)|<span data-ttu-id="285b7-176">Bir güvenlik belirteci veren bir uç nokta belirtir.</span><span class="sxs-lookup"><span data-stu-id="285b7-176">Specifies an endpoint that issues a security token.</span></span> <span data-ttu-id="285b7-177">Bu öğe <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>türündedir.</span><span class="sxs-lookup"><span data-stu-id="285b7-177">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>.</span></span>|  
|[<span data-ttu-id="285b7-178">\<IssuerMetadata ></span><span class="sxs-lookup"><span data-stu-id="285b7-178">\<issuerMetadata></span></span>](issuermetadata.md)|<span data-ttu-id="285b7-179">Verenin uç nokta adresini belirtir.</span><span class="sxs-lookup"><span data-stu-id="285b7-179">Specifies the endpoint address of the issuer.</span></span>|  
|[<span data-ttu-id="285b7-180">\<tokenRequestParameters ></span><span class="sxs-lookup"><span data-stu-id="285b7-180">\<tokenRequestParameters></span></span>](tokenrequestparameters.md)|<span data-ttu-id="285b7-181">Belirteç isteği parametrelerinin bir koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="285b7-181">A collection of token request parameters.</span></span> <span data-ttu-id="285b7-182">Her parametre bir XML öğesidir.</span><span class="sxs-lookup"><span data-stu-id="285b7-182">Each parameter is an XML element.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="285b7-183">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="285b7-183">Parent Elements</span></span>  
  
|<span data-ttu-id="285b7-184">Öğe</span><span class="sxs-lookup"><span data-stu-id="285b7-184">Element</span></span>|<span data-ttu-id="285b7-185">Açıklama</span><span class="sxs-lookup"><span data-stu-id="285b7-185">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="285b7-186">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="285b7-186">\<security></span></span>](security-element-of-ws2007federationhttpbinding.md)|<span data-ttu-id="285b7-187">Bağlama için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="285b7-187">Defines the security settings for a binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="285b7-188">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="285b7-188">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp>
- <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement.Message%2A>
- <xref:System.ServiceModel.WSFederationHttpSecurity.Message%2A>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>
- [<span data-ttu-id="285b7-189">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="285b7-189">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="285b7-190">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="285b7-190">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="285b7-191">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="285b7-191">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="285b7-192">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="285b7-192">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="285b7-193">\< bağlama ></span><span class="sxs-lookup"><span data-stu-id="285b7-193">\<binding></span></span>](bindings.md)
