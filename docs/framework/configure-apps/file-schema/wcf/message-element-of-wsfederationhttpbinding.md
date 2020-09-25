---
title: <message> öğesi <wsFederationHttpBinding>
ms.date: 03/30/2017
ms.assetid: 9d710389-d9d8-4454-9bf2-da4ccda31cec
ms.openlocfilehash: ea320b1d97e742d4f90ec55502f3bd429803283d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91204898"
---
# <a name="message-element-of-wsfederationhttpbinding"></a><span data-ttu-id="d2d4a-102">\<message> öğesi \<wsFederationHttpBinding></span><span class="sxs-lookup"><span data-stu-id="d2d4a-102">\<message> element of \<wsFederationHttpBinding></span></span>

<span data-ttu-id="d2d4a-103">İçin ileti düzeyi güvenlik ayarlarını tanımlar [\<wsFederationHttpBinding>](wsfederationhttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="d2d4a-103">Defines the settings for the message-level security for the [\<wsFederationHttpBinding>](wsfederationhttpbinding.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<message>**  
  
## <a name="syntax"></a><span data-ttu-id="d2d4a-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="d2d4a-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d2d4a-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="d2d4a-105">Attributes and Elements</span></span>  

 <span data-ttu-id="d2d4a-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d2d4a-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d2d4a-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d2d4a-107">Attributes</span></span>  
  
|<span data-ttu-id="d2d4a-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="d2d4a-108">Attribute</span></span>|<span data-ttu-id="d2d4a-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d2d4a-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d2d4a-110">algorithmSuite</span><span class="sxs-lookup"><span data-stu-id="d2d4a-110">algorithmSuite</span></span>|<span data-ttu-id="d2d4a-111">İleti şifrelemesini ve anahtar sarması algoritmalarını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="d2d4a-111">Sets the message encryption and key-wrap algorithms.</span></span> <span data-ttu-id="d2d4a-112">Bu özniteliğin geçerli değerleri için "algorithmSuite Attribute" tablosuna bakın.</span><span class="sxs-lookup"><span data-stu-id="d2d4a-112">See the "algorithmSuite attribute" table for valid values of this attribute.</span></span> <span data-ttu-id="d2d4a-113">Varsayılan değer: `Basic256`.</span><span class="sxs-lookup"><span data-stu-id="d2d4a-113">The default value is `Basic256`.</span></span><br /><br /> <span data-ttu-id="d2d4a-114">Bu öznitelik türü <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> .</span><span class="sxs-lookup"><span data-stu-id="d2d4a-114">This attribute is of type <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span></span> <span data-ttu-id="d2d4a-115">Bu algoritmalar güvenlik Ilkesi dili (WS-SecurityPolicy) belirtiminde belirtilen olanlarla eşlenir.</span><span class="sxs-lookup"><span data-stu-id="d2d4a-115">These algorithms map to those specified in the Security Policy Language (WS-SecurityPolicy) specification.</span></span>|  
|<span data-ttu-id="d2d4a-116">IssuedKeyType</span><span class="sxs-lookup"><span data-stu-id="d2d4a-116">issuedKeyType</span></span>|<span data-ttu-id="d2d4a-117">Verilecek anahtarın türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="d2d4a-117">Specifies the type of key to be issued.</span></span> <span data-ttu-id="d2d4a-118">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="d2d4a-118">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="d2d4a-119">-SymmetricKey</span><span class="sxs-lookup"><span data-stu-id="d2d4a-119">-   SymmetricKey</span></span><br /><span data-ttu-id="d2d4a-120">-PublicKey</span><span class="sxs-lookup"><span data-stu-id="d2d4a-120">-   PublicKey</span></span><br /><br /> <span data-ttu-id="d2d4a-121">Varsayılan değer: `SymmetricKey`.</span><span class="sxs-lookup"><span data-stu-id="d2d4a-121">The default is `SymmetricKey`.</span></span> <span data-ttu-id="d2d4a-122">Bu öznitelik türü <xref:System.IdentityModel.Tokens.SecurityKeyType> .</span><span class="sxs-lookup"><span data-stu-id="d2d4a-122">This attribute is of type <xref:System.IdentityModel.Tokens.SecurityKeyType>.</span></span>|  
|<span data-ttu-id="d2d4a-123">IssuedTokenType</span><span class="sxs-lookup"><span data-stu-id="d2d4a-123">issuedTokenType</span></span>|<span data-ttu-id="d2d4a-124">Verilecek belirtecin türünü belirten bir URI içeren dize.</span><span class="sxs-lookup"><span data-stu-id="d2d4a-124">A string that contains a URI that specifies the type of token to be issued.</span></span> <span data-ttu-id="d2d4a-125">Varsayılan değer: `null`.</span><span class="sxs-lookup"><span data-stu-id="d2d4a-125">The default is `null`.</span></span>|  
|<span data-ttu-id="d2d4a-126">negotiateServiceCredential</span><span class="sxs-lookup"><span data-stu-id="d2d4a-126">negotiateServiceCredential</span></span>|<span data-ttu-id="d2d4a-127">Hizmet kimlik bilgisinin, anlaşmanın parçası olarak alınıp alınmayacağını veya bant dışı kullanılabilir olup olmadığını belirten bir Boolean değer.</span><span class="sxs-lookup"><span data-stu-id="d2d4a-127">A Boolean value that specifies whether the service credential should be exchanged as part of negotiation or is available out of band.</span></span> <span data-ttu-id="d2d4a-128">Varsayılan olarak, `true` hizmet kimlik bilgisinin anlaşıldığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="d2d4a-128">The default is `true`, which means that the service credential is negotiated.</span></span>|  
  
## <a name="algorithmsuite-attribute"></a><span data-ttu-id="d2d4a-129">algorithmSuite özniteliği</span><span class="sxs-lookup"><span data-stu-id="d2d4a-129">algorithmSuite Attribute</span></span>  
  
|<span data-ttu-id="d2d4a-130">Değer</span><span class="sxs-lookup"><span data-stu-id="d2d4a-130">Value</span></span>|<span data-ttu-id="d2d4a-131">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d2d4a-131">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d2d4a-132">Basic128</span><span class="sxs-lookup"><span data-stu-id="d2d4a-132">Basic128</span></span>|<span data-ttu-id="d2d4a-133">Anahtar kaydırması için Basic128 şifrelemesi, ileti özeti için SHA1 ve rsa-oaep-mgf1p kullanın.</span><span class="sxs-lookup"><span data-stu-id="d2d4a-133">Use Basic128 encryption, Sha1 for message digest, and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="d2d4a-134">Basic192</span><span class="sxs-lookup"><span data-stu-id="d2d4a-134">Basic192</span></span>|<span data-ttu-id="d2d4a-135">Anahtar kaydırması için Basic192 şifrelemesi, ileti özeti için SHA1, rsa-oaep-mgf1p kullanın.</span><span class="sxs-lookup"><span data-stu-id="d2d4a-135">Use Basic192 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="d2d4a-136">Basic256</span><span class="sxs-lookup"><span data-stu-id="d2d4a-136">Basic256</span></span>|<span data-ttu-id="d2d4a-137">Anahtar kaydırması için Basic256 şifrelemesi, ileti özeti için SHA1, rsa-oaep-mgf1p kullanın.</span><span class="sxs-lookup"><span data-stu-id="d2d4a-137">Use Basic256 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="d2d4a-138">Basic256Rsa15</span><span class="sxs-lookup"><span data-stu-id="d2d4a-138">Basic256Rsa15</span></span>|<span data-ttu-id="d2d4a-139">İleti şifreleme için Basic256, ileti özeti için SHA1 ve anahtar kaydırması için Rsa15 kullanın.</span><span class="sxs-lookup"><span data-stu-id="d2d4a-139">Use Basic256 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="d2d4a-140">Basic192Rsa15</span><span class="sxs-lookup"><span data-stu-id="d2d4a-140">Basic192Rsa15</span></span>|<span data-ttu-id="d2d4a-141">İleti şifreleme için Basic192, ileti özeti için SHA1 ve anahtar kaydırması için Rsa15 kullanın.</span><span class="sxs-lookup"><span data-stu-id="d2d4a-141">Use Basic192 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="d2d4a-142">TripleDes</span><span class="sxs-lookup"><span data-stu-id="d2d4a-142">TripleDes</span></span>|<span data-ttu-id="d2d4a-143">Anahtar kaydırması için, TripleDes şifrelemesi, ileti özeti için SHA1, rsa-oaep-mgf1p kullanın.</span><span class="sxs-lookup"><span data-stu-id="d2d4a-143">Use TripleDes encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="d2d4a-144">Basic128Rsa15</span><span class="sxs-lookup"><span data-stu-id="d2d4a-144">Basic128Rsa15</span></span>|<span data-ttu-id="d2d4a-145">İleti şifreleme için Basic128, ileti özeti için SHA1 ve anahtar kaydırması için Rsa15 kullanın.</span><span class="sxs-lookup"><span data-stu-id="d2d4a-145">Use Basic128 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="d2d4a-146">TripleDesRsa15</span><span class="sxs-lookup"><span data-stu-id="d2d4a-146">TripleDesRsa15</span></span>|<span data-ttu-id="d2d4a-147">TripleDes şifrelemesi, ileti özeti için SHA1 ve anahtar kaydırması için Rsa15 kullanın.</span><span class="sxs-lookup"><span data-stu-id="d2d4a-147">Use TripleDes encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="d2d4a-148">Basic128Sha256</span><span class="sxs-lookup"><span data-stu-id="d2d4a-148">Basic128Sha256</span></span>|<span data-ttu-id="d2d4a-149">İleti için Basic128, ileti özeti için SHA256, anahtar kaydırması için rsa-oaep-mgf1p kullanın.</span><span class="sxs-lookup"><span data-stu-id="d2d4a-149">Use Basic128 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="d2d4a-150">Basic192Sha256</span><span class="sxs-lookup"><span data-stu-id="d2d4a-150">Basic192Sha256</span></span>|<span data-ttu-id="d2d4a-151">İleti için Basic192, ileti özeti için SHA256, anahtar kaydırması için rsa-oaep-mgf1p kullanın.</span><span class="sxs-lookup"><span data-stu-id="d2d4a-151">Use Basic192 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="d2d4a-152">Basic256Sha256</span><span class="sxs-lookup"><span data-stu-id="d2d4a-152">Basic256Sha256</span></span>|<span data-ttu-id="d2d4a-153">İleti için Basic256, ileti özeti için SHA256, anahtar kaydırması için rsa-oaep-mgf1p kullanın.</span><span class="sxs-lookup"><span data-stu-id="d2d4a-153">Use Basic256 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="d2d4a-154">TripleDesSha256</span><span class="sxs-lookup"><span data-stu-id="d2d4a-154">TripleDesSha256</span></span>|<span data-ttu-id="d2d4a-155">İleti şifreleme için TripleDes, SHA256 for Message Digest ve rsa-oaep-mgf1p için anahtar kaydırması kullanın.</span><span class="sxs-lookup"><span data-stu-id="d2d4a-155">Use TripleDes for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="d2d4a-156">Basic128Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="d2d4a-156">Basic128Sha256Rsa15</span></span>|<span data-ttu-id="d2d4a-157">İleti şifreleme için Basic128, ileti özeti için SHA256 ve anahtar kaydırması için Rsa15 kullanın.</span><span class="sxs-lookup"><span data-stu-id="d2d4a-157">Use Basic128 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="d2d4a-158">Basic192Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="d2d4a-158">Basic192Sha256Rsa15</span></span>|<span data-ttu-id="d2d4a-159">İleti şifreleme için Aes192, ileti özeti için SHA256 ve anahtar kaydırması için Rsa15 kullanın.</span><span class="sxs-lookup"><span data-stu-id="d2d4a-159">Use Aes192 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="d2d4a-160">Basic256Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="d2d4a-160">Basic256Sha256Rsa15</span></span>|<span data-ttu-id="d2d4a-161">İleti şifreleme için Basic256, ileti özeti için SHA256 ve anahtar kaydırması için Rsa15 kullanın.</span><span class="sxs-lookup"><span data-stu-id="d2d4a-161">Use Basic256 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="d2d4a-162">TripleDesSha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="d2d4a-162">TripleDesSha256Rsa15</span></span>|<span data-ttu-id="d2d4a-163">İleti şifreleme için TripleDes, SHA256 for Message Digest ve Rsa15 anahtar kaydırması için kullanın.</span><span class="sxs-lookup"><span data-stu-id="d2d4a-163">Use TripleDes for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d2d4a-164">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="d2d4a-164">Child Elements</span></span>  
  
|<span data-ttu-id="d2d4a-165">Öğe</span><span class="sxs-lookup"><span data-stu-id="d2d4a-165">Element</span></span>|<span data-ttu-id="d2d4a-166">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d2d4a-166">Description</span></span>|  
|-------------|-----------------|  
|[\<claimTypeRequirements>](claimtyperequirements-element.md)|<span data-ttu-id="d2d4a-167">Bu bağlama için bir talep türleri koleksiyonu belirtir.</span><span class="sxs-lookup"><span data-stu-id="d2d4a-167">Specifies a collection of claim types for this binding.</span></span> <span data-ttu-id="d2d4a-168">Her öğe türündedir <xref:System.ServiceModel.Configuration.ClaimTypeElement> .</span><span class="sxs-lookup"><span data-stu-id="d2d4a-168">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span>|  
|<span data-ttu-id="d2d4a-169">yayınlayan</span><span class="sxs-lookup"><span data-stu-id="d2d4a-169">issuer</span></span>|<span data-ttu-id="d2d4a-170">Bir güvenlik belirteci veren bir uç nokta belirtir.</span><span class="sxs-lookup"><span data-stu-id="d2d4a-170">Specifies an endpoint that issues a security token.</span></span> <span data-ttu-id="d2d4a-171">Bu öğe türündedir <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement> .</span><span class="sxs-lookup"><span data-stu-id="d2d4a-171">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>.</span></span>|  
|<span data-ttu-id="d2d4a-172">issuerMetadata</span><span class="sxs-lookup"><span data-stu-id="d2d4a-172">issuerMetadata</span></span>|<span data-ttu-id="d2d4a-173">Verenin uç nokta adresini belirtir.</span><span class="sxs-lookup"><span data-stu-id="d2d4a-173">Specifies the endpoint address of the issuer.</span></span>|  
|[\<tokenRequestParameters>](tokenrequestparameters.md)|<span data-ttu-id="d2d4a-174">Belirteç isteği parametrelerinin bir koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="d2d4a-174">A collection of token request parameters.</span></span> <span data-ttu-id="d2d4a-175">Her parametre bir XML öğesidir.</span><span class="sxs-lookup"><span data-stu-id="d2d4a-175">Each parameter is an XML element.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d2d4a-176">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="d2d4a-176">Parent Elements</span></span>  
  
|<span data-ttu-id="d2d4a-177">Öğe</span><span class="sxs-lookup"><span data-stu-id="d2d4a-177">Element</span></span>|<span data-ttu-id="d2d4a-178">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d2d4a-178">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-wsfederationhttpbinding.md)|<span data-ttu-id="d2d4a-179">Bağlama için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d2d4a-179">Defines the security settings for a binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d2d4a-180">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d2d4a-180">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp>
- <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement.Message%2A>
- <xref:System.ServiceModel.WSFederationHttpSecurity.Message%2A>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>
- [<span data-ttu-id="d2d4a-181">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="d2d4a-181">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="d2d4a-182">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="d2d4a-182">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="d2d4a-183">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="d2d4a-183">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="d2d4a-184">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="d2d4a-184">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
