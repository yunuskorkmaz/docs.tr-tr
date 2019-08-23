---
title: <message>öğesi<ws2007FederationHttpBinding>
ms.date: 03/30/2017
ms.assetid: 52cd941d-e230-4c82-8b29-333a7d20eca8
ms.openlocfilehash: 4340727026cb151f2efe813dfa005c1c5a1908be
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931618"
---
# <a name="message-element-of-ws2007federationhttpbinding"></a><span data-ttu-id="28123-102">\<ileti > \<WS2007FederationHttpBinding > öğesi</span><span class="sxs-lookup"><span data-stu-id="28123-102">\<message> element of \<ws2007FederationHttpBinding></span></span>
<span data-ttu-id="28123-103">WS2007FederationHttpBinding > öğesi için [ \<](ws2007federationhttpbinding.md) ileti düzeyi güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="28123-103">Defines settings for the message-level security for the [\<ws2007FederationHttpBinding>](ws2007federationhttpbinding.md) element.</span></span>  
  
 <span data-ttu-id="28123-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="28123-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="28123-105">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="28123-105">\<bindings></span></span>  
<span data-ttu-id="28123-106">\<ws2007FederationHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="28123-106">\<ws2007FederationHttpBinding></span></span>  
<span data-ttu-id="28123-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="28123-107">\<binding></span></span>  
<span data-ttu-id="28123-108">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="28123-108">\<security></span></span>  
<span data-ttu-id="28123-109">\<ileti ></span><span class="sxs-lookup"><span data-stu-id="28123-109">\<message></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28123-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="28123-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="28123-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="28123-111">Attributes and Elements</span></span>  
 <span data-ttu-id="28123-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="28123-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="28123-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="28123-113">Attributes</span></span>  
  
|<span data-ttu-id="28123-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="28123-114">Attribute</span></span>|<span data-ttu-id="28123-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="28123-115">Description</span></span>|  
|---------------|-----------------|  
|`algorithmSuite`|<span data-ttu-id="28123-116">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="28123-116">Optional.</span></span> <span data-ttu-id="28123-117">İleti şifrelemesini, imzayı ve anahtar sarması algoritmalarını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="28123-117">Sets the message encryption, signature, and key-wrap algorithms.</span></span> <span data-ttu-id="28123-118">Algoritmalar ve anahtar boyutları <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> sınıfına göre belirlenir.</span><span class="sxs-lookup"><span data-stu-id="28123-118">The algorithms and the key sizes are determined by the <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> class.</span></span> <span data-ttu-id="28123-119">Bu algoritmalar güvenlik Ilkesi dili (WS-SecurityPolicy) belirtiminde belirtilen olanlarla eşlenir.</span><span class="sxs-lookup"><span data-stu-id="28123-119">These algorithms map to those specified in the Security Policy Language (WS-SecurityPolicy) specification.</span></span><br /><br /> <span data-ttu-id="28123-120">Olası değerler için aşağıdaki tabloya bakın.</span><span class="sxs-lookup"><span data-stu-id="28123-120">See the following table for possible values.</span></span> <span data-ttu-id="28123-121">Varsayılan değer Basic256 ' dir.</span><span class="sxs-lookup"><span data-stu-id="28123-121">The default value is Basic256.</span></span>|  
|`issuedKeyType`|<span data-ttu-id="28123-122">Verilecek anahtarın türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="28123-122">Specifies the type of key to be issued.</span></span> <span data-ttu-id="28123-123">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="28123-123">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="28123-124">-SymmetricKey</span><span class="sxs-lookup"><span data-stu-id="28123-124">-   SymmetricKey</span></span><br /><span data-ttu-id="28123-125">-PublicKey</span><span class="sxs-lookup"><span data-stu-id="28123-125">-   PublicKey</span></span><br /><span data-ttu-id="28123-126">-Yataerkey</span><span class="sxs-lookup"><span data-stu-id="28123-126">-   BearerKey</span></span><br /><br /> <span data-ttu-id="28123-127">Varsayılan değer SymmetricKey ' dir.</span><span class="sxs-lookup"><span data-stu-id="28123-127">The default is SymmetricKey.</span></span> <span data-ttu-id="28123-128">Bu öznitelik türü <xref:System.IdentityModel.Tokens.SecurityKeyType>.</span><span class="sxs-lookup"><span data-stu-id="28123-128">This attribute is of type <xref:System.IdentityModel.Tokens.SecurityKeyType>.</span></span>|  
|`issuedTokenType`|<span data-ttu-id="28123-129">Verilecek belirtecin türünü belirten bir URI.</span><span class="sxs-lookup"><span data-stu-id="28123-129">A URI that specifies the type of token to be issued.</span></span> <span data-ttu-id="28123-130">Varsayılan, `null` değeridir.</span><span class="sxs-lookup"><span data-stu-id="28123-130">The default is `null`.</span></span>|  
|`negotiateServiceCredential`|<span data-ttu-id="28123-131">Hizmet kimlik bilgisinin, anlaşmanın parçası olarak alınıp alınmayacağını veya bant dışı kullanılabilir olup olmadığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="28123-131">A value that specifies whether the service credential should be exchanged as part of negotiation or is available out of band.</span></span> <span data-ttu-id="28123-132">Varsayılan `true`olarak, hizmet kimlik bilgisinin anlaşıldığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="28123-132">The default is `true`, which means that the service credential is negotiated.</span></span>|  
  
## <a name="algorithmsuite-attribute"></a><span data-ttu-id="28123-133">algorithmSuite özniteliği</span><span class="sxs-lookup"><span data-stu-id="28123-133">algorithmSuite Attribute</span></span>  
  
|<span data-ttu-id="28123-134">Değer</span><span class="sxs-lookup"><span data-stu-id="28123-134">Value</span></span>|<span data-ttu-id="28123-135">Açıklama</span><span class="sxs-lookup"><span data-stu-id="28123-135">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="28123-136">Basic128</span><span class="sxs-lookup"><span data-stu-id="28123-136">Basic128</span></span>|<span data-ttu-id="28123-137">Anahtar kaydırması için AES128 şifrelemesi, ileti özeti için SHA1 ve rsa-oaep-mgf1p kullanın.</span><span class="sxs-lookup"><span data-stu-id="28123-137">Use Aes128 encryption, Sha1 for message digest, and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="28123-138">Basic192</span><span class="sxs-lookup"><span data-stu-id="28123-138">Basic192</span></span>|<span data-ttu-id="28123-139">Anahtar kaydırması için Aes192 şifrelemesi, ileti özeti için SHA1, rsa-oaep-mgf1p kullanın.</span><span class="sxs-lookup"><span data-stu-id="28123-139">Use Aes192 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="28123-140">Basic256</span><span class="sxs-lookup"><span data-stu-id="28123-140">Basic256</span></span>|<span data-ttu-id="28123-141">Anahtar kaydırması için AES256 şifrelemesi, ileti özeti için SHA1, rsa-oaep-mgf1p kullanın.</span><span class="sxs-lookup"><span data-stu-id="28123-141">Use Aes256 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="28123-142">Basic256Rsa15</span><span class="sxs-lookup"><span data-stu-id="28123-142">Basic256Rsa15</span></span>|<span data-ttu-id="28123-143">İleti şifreleme için AES256, ileti özeti için SHA1 ve anahtar kaydırması için Rsa15 kullanın.</span><span class="sxs-lookup"><span data-stu-id="28123-143">Use Aes256 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="28123-144">Basic192Rsa15</span><span class="sxs-lookup"><span data-stu-id="28123-144">Basic192Rsa15</span></span>|<span data-ttu-id="28123-145">İleti şifreleme için Aes192, ileti özeti için SHA1 ve anahtar kaydırması için Rsa15 kullanın.</span><span class="sxs-lookup"><span data-stu-id="28123-145">Use Aes192 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="28123-146">TripleDes</span><span class="sxs-lookup"><span data-stu-id="28123-146">TripleDes</span></span>|<span data-ttu-id="28123-147">Anahtar kaydırması için, TripleDes şifrelemesi, ileti özeti için SHA1, rsa-oaep-mgf1p kullanın.</span><span class="sxs-lookup"><span data-stu-id="28123-147">Use TripleDes encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="28123-148">Basic128Rsa15</span><span class="sxs-lookup"><span data-stu-id="28123-148">Basic128Rsa15</span></span>|<span data-ttu-id="28123-149">İleti şifreleme için AES128, ileti özeti için SHA1 ve anahtar kaydırması için Rsa15 kullanın.</span><span class="sxs-lookup"><span data-stu-id="28123-149">Use Aes128 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="28123-150">TripleDesRsa15</span><span class="sxs-lookup"><span data-stu-id="28123-150">TripleDesRsa15</span></span>|<span data-ttu-id="28123-151">TripleDes şifrelemesi, ileti özeti için SHA1 ve anahtar kaydırması için Rsa15 kullanın.</span><span class="sxs-lookup"><span data-stu-id="28123-151">Use TripleDes encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="28123-152">Basic128Sha256</span><span class="sxs-lookup"><span data-stu-id="28123-152">Basic128Sha256</span></span>|<span data-ttu-id="28123-153">İleti için AES256, ileti özeti için SHA256, anahtar kaydırması için rsa-oaep-mgf1p kullanın.</span><span class="sxs-lookup"><span data-stu-id="28123-153">Use Aes256 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="28123-154">Basic192Sha256</span><span class="sxs-lookup"><span data-stu-id="28123-154">Basic192Sha256</span></span>|<span data-ttu-id="28123-155">İleti için Aes192, ileti özeti için SHA256, anahtar kaydırması için rsa-oaep-mgf1p kullanın.</span><span class="sxs-lookup"><span data-stu-id="28123-155">Use Aes192 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="28123-156">Basic256Sha256</span><span class="sxs-lookup"><span data-stu-id="28123-156">Basic256Sha256</span></span>|<span data-ttu-id="28123-157">İleti için AES256, ileti özeti için SHA256, anahtar kaydırması için rsa-oaep-mgf1p kullanın.</span><span class="sxs-lookup"><span data-stu-id="28123-157">Use Aes256 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="28123-158">TripleDesSha256</span><span class="sxs-lookup"><span data-stu-id="28123-158">TripleDesSha256</span></span>|<span data-ttu-id="28123-159">İleti şifreleme için TripleDes, SHA256 for Message Digest ve rsa-oaep-mgf1p için anahtar kaydırması kullanın.</span><span class="sxs-lookup"><span data-stu-id="28123-159">Use TripleDes for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="28123-160">Basic128Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="28123-160">Basic128Sha256Rsa15</span></span>|<span data-ttu-id="28123-161">İleti şifreleme için AES128, ileti özeti için SHA256 ve anahtar kaydırması için Rsa15 kullanın.</span><span class="sxs-lookup"><span data-stu-id="28123-161">Use Aes128 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="28123-162">Basic192Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="28123-162">Basic192Sha256Rsa15</span></span>|<span data-ttu-id="28123-163">İleti şifreleme için Aes192, ileti özeti için SHA256 ve anahtar kaydırması için Rsa15 kullanın.</span><span class="sxs-lookup"><span data-stu-id="28123-163">Use Aes192 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="28123-164">Basic256Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="28123-164">Basic256Sha256Rsa15</span></span>|<span data-ttu-id="28123-165">İleti şifreleme için AES256, ileti özeti için SHA256 ve anahtar kaydırması için Rsa15 kullanın.</span><span class="sxs-lookup"><span data-stu-id="28123-165">Use Aes256 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="28123-166">TripleDesSha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="28123-166">TripleDesSha256Rsa15</span></span>|<span data-ttu-id="28123-167">İleti şifreleme için TripleDes, SHA256 for Message Digest ve Rsa15 anahtar kaydırması için kullanın.</span><span class="sxs-lookup"><span data-stu-id="28123-167">Use TripleDes for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="28123-168">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="28123-168">Child Elements</span></span>  
  
|<span data-ttu-id="28123-169">Öğe</span><span class="sxs-lookup"><span data-stu-id="28123-169">Element</span></span>|<span data-ttu-id="28123-170">Açıklama</span><span class="sxs-lookup"><span data-stu-id="28123-170">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="28123-171">\<claimTypeRequirements ></span><span class="sxs-lookup"><span data-stu-id="28123-171">\<claimTypeRequirements></span></span>](claimtyperequirements-element.md)|<span data-ttu-id="28123-172">Bu bağlama için bir talep türleri koleksiyonu belirtir.</span><span class="sxs-lookup"><span data-stu-id="28123-172">Specifies a collection of claim types for this binding.</span></span> <span data-ttu-id="28123-173">Her öğe türündedir <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span><span class="sxs-lookup"><span data-stu-id="28123-173">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span>|  
|[<span data-ttu-id="28123-174">\<veren ></span><span class="sxs-lookup"><span data-stu-id="28123-174">\<issuer></span></span>](issuer.md)|<span data-ttu-id="28123-175">Bir güvenlik belirteci veren bir uç nokta belirtir.</span><span class="sxs-lookup"><span data-stu-id="28123-175">Specifies an endpoint that issues a security token.</span></span> <span data-ttu-id="28123-176">Bu öğe türündedir <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>.</span><span class="sxs-lookup"><span data-stu-id="28123-176">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>.</span></span>|  
|[<span data-ttu-id="28123-177">\<IssuerMetadata ></span><span class="sxs-lookup"><span data-stu-id="28123-177">\<issuerMetadata></span></span>](issuermetadata.md)|<span data-ttu-id="28123-178">Verenin uç nokta adresini belirtir.</span><span class="sxs-lookup"><span data-stu-id="28123-178">Specifies the endpoint address of the issuer.</span></span>|  
|[<span data-ttu-id="28123-179">\<tokenRequestParameters></span><span class="sxs-lookup"><span data-stu-id="28123-179">\<tokenRequestParameters></span></span>](tokenrequestparameters.md)|<span data-ttu-id="28123-180">Belirteç isteği parametrelerinin bir koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="28123-180">A collection of token request parameters.</span></span> <span data-ttu-id="28123-181">Her parametre bir XML öğesidir.</span><span class="sxs-lookup"><span data-stu-id="28123-181">Each parameter is an XML element.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="28123-182">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="28123-182">Parent Elements</span></span>  
  
|<span data-ttu-id="28123-183">Öğe</span><span class="sxs-lookup"><span data-stu-id="28123-183">Element</span></span>|<span data-ttu-id="28123-184">Açıklama</span><span class="sxs-lookup"><span data-stu-id="28123-184">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="28123-185">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="28123-185">\<security></span></span>](security-element-of-ws2007federationhttpbinding.md)|<span data-ttu-id="28123-186">Bağlama için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="28123-186">Defines the security settings for a binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="28123-187">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="28123-187">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp>
- <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement.Message%2A>
- <xref:System.ServiceModel.WSFederationHttpSecurity.Message%2A>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>
- [<span data-ttu-id="28123-188">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="28123-188">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="28123-189">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="28123-189">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="28123-190">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="28123-190">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="28123-191">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="28123-191">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="28123-192">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="28123-192">\<binding></span></span>](../../../misc/binding.md)
