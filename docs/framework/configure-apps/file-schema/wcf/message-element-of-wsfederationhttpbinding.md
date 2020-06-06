---
title: <message>öğesi<wsFederationHttpBinding>
ms.date: 03/30/2017
ms.assetid: 9d710389-d9d8-4454-9bf2-da4ccda31cec
ms.openlocfilehash: 8e0903dd1313e68e2de65730e129079199ebe2f2
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73738985"
---
# <a name="message-element-of-wsfederationhttpbinding"></a><span data-ttu-id="38f29-102">\<message>öğesi\<wsFederationHttpBinding></span><span class="sxs-lookup"><span data-stu-id="38f29-102">\<message> element of \<wsFederationHttpBinding></span></span>
<span data-ttu-id="38f29-103">İçin ileti düzeyi güvenlik ayarlarını tanımlar [\<wsFederationHttpBinding>](wsfederationhttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="38f29-103">Defines the settings for the message-level security for the [\<wsFederationHttpBinding>](wsfederationhttpbinding.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<message>**  
  
## <a name="syntax"></a><span data-ttu-id="38f29-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="38f29-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="38f29-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="38f29-105">Attributes and Elements</span></span>  
 <span data-ttu-id="38f29-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="38f29-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="38f29-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="38f29-107">Attributes</span></span>  
  
|<span data-ttu-id="38f29-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="38f29-108">Attribute</span></span>|<span data-ttu-id="38f29-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="38f29-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="38f29-110">algorithmSuite</span><span class="sxs-lookup"><span data-stu-id="38f29-110">algorithmSuite</span></span>|<span data-ttu-id="38f29-111">İleti şifrelemesini ve anahtar sarması algoritmalarını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="38f29-111">Sets the message encryption and key-wrap algorithms.</span></span> <span data-ttu-id="38f29-112">Bu özniteliğin geçerli değerleri için "algorithmSuite Attribute" tablosuna bakın.</span><span class="sxs-lookup"><span data-stu-id="38f29-112">See the "algorithmSuite attribute" table for valid values of this attribute.</span></span> <span data-ttu-id="38f29-113">Varsayılan değer: `Basic256`.</span><span class="sxs-lookup"><span data-stu-id="38f29-113">The default value is `Basic256`.</span></span><br /><br /> <span data-ttu-id="38f29-114">Bu öznitelik türü <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> .</span><span class="sxs-lookup"><span data-stu-id="38f29-114">This attribute is of type <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span></span> <span data-ttu-id="38f29-115">Bu algoritmalar güvenlik Ilkesi dili (WS-SecurityPolicy) belirtiminde belirtilen olanlarla eşlenir.</span><span class="sxs-lookup"><span data-stu-id="38f29-115">These algorithms map to those specified in the Security Policy Language (WS-SecurityPolicy) specification.</span></span>|  
|<span data-ttu-id="38f29-116">IssuedKeyType</span><span class="sxs-lookup"><span data-stu-id="38f29-116">issuedKeyType</span></span>|<span data-ttu-id="38f29-117">Verilecek anahtarın türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="38f29-117">Specifies the type of key to be issued.</span></span> <span data-ttu-id="38f29-118">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="38f29-118">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="38f29-119">-SymmetricKey</span><span class="sxs-lookup"><span data-stu-id="38f29-119">-   SymmetricKey</span></span><br /><span data-ttu-id="38f29-120">-PublicKey</span><span class="sxs-lookup"><span data-stu-id="38f29-120">-   PublicKey</span></span><br /><br /> <span data-ttu-id="38f29-121">Varsayılan değer: `SymmetricKey`.</span><span class="sxs-lookup"><span data-stu-id="38f29-121">The default is `SymmetricKey`.</span></span> <span data-ttu-id="38f29-122">Bu öznitelik türü <xref:System.IdentityModel.Tokens.SecurityKeyType> .</span><span class="sxs-lookup"><span data-stu-id="38f29-122">This attribute is of type <xref:System.IdentityModel.Tokens.SecurityKeyType>.</span></span>|  
|<span data-ttu-id="38f29-123">IssuedTokenType</span><span class="sxs-lookup"><span data-stu-id="38f29-123">issuedTokenType</span></span>|<span data-ttu-id="38f29-124">Verilecek belirtecin türünü belirten bir URI içeren dize.</span><span class="sxs-lookup"><span data-stu-id="38f29-124">A string that contains a URI that specifies the type of token to be issued.</span></span> <span data-ttu-id="38f29-125">Varsayılan değer: `null`.</span><span class="sxs-lookup"><span data-stu-id="38f29-125">The default is `null`.</span></span>|  
|<span data-ttu-id="38f29-126">negotiateServiceCredential</span><span class="sxs-lookup"><span data-stu-id="38f29-126">negotiateServiceCredential</span></span>|<span data-ttu-id="38f29-127">Hizmet kimlik bilgisinin, anlaşmanın parçası olarak alınıp alınmayacağını veya bant dışı kullanılabilir olup olmadığını belirten bir Boolean değer.</span><span class="sxs-lookup"><span data-stu-id="38f29-127">A Boolean value that specifies whether the service credential should be exchanged as part of negotiation or is available out of band.</span></span> <span data-ttu-id="38f29-128">Varsayılan olarak, `true` hizmet kimlik bilgisinin anlaşıldığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="38f29-128">The default is `true`, which means that the service credential is negotiated.</span></span>|  
  
## <a name="algorithmsuite-attribute"></a><span data-ttu-id="38f29-129">algorithmSuite özniteliği</span><span class="sxs-lookup"><span data-stu-id="38f29-129">algorithmSuite Attribute</span></span>  
  
|<span data-ttu-id="38f29-130">Değer</span><span class="sxs-lookup"><span data-stu-id="38f29-130">Value</span></span>|<span data-ttu-id="38f29-131">Açıklama</span><span class="sxs-lookup"><span data-stu-id="38f29-131">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="38f29-132">Basic128</span><span class="sxs-lookup"><span data-stu-id="38f29-132">Basic128</span></span>|<span data-ttu-id="38f29-133">Anahtar kaydırması için Basic128 şifrelemesi, ileti özeti için SHA1 ve rsa-oaep-mgf1p kullanın.</span><span class="sxs-lookup"><span data-stu-id="38f29-133">Use Basic128 encryption, Sha1 for message digest, and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="38f29-134">Basic192</span><span class="sxs-lookup"><span data-stu-id="38f29-134">Basic192</span></span>|<span data-ttu-id="38f29-135">Anahtar kaydırması için Basic192 şifrelemesi, ileti özeti için SHA1, rsa-oaep-mgf1p kullanın.</span><span class="sxs-lookup"><span data-stu-id="38f29-135">Use Basic192 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="38f29-136">Basic256</span><span class="sxs-lookup"><span data-stu-id="38f29-136">Basic256</span></span>|<span data-ttu-id="38f29-137">Anahtar kaydırması için Basic256 şifrelemesi, ileti özeti için SHA1, rsa-oaep-mgf1p kullanın.</span><span class="sxs-lookup"><span data-stu-id="38f29-137">Use Basic256 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="38f29-138">Basic256Rsa15</span><span class="sxs-lookup"><span data-stu-id="38f29-138">Basic256Rsa15</span></span>|<span data-ttu-id="38f29-139">İleti şifreleme için Basic256, ileti özeti için SHA1 ve anahtar kaydırması için Rsa15 kullanın.</span><span class="sxs-lookup"><span data-stu-id="38f29-139">Use Basic256 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="38f29-140">Basic192Rsa15</span><span class="sxs-lookup"><span data-stu-id="38f29-140">Basic192Rsa15</span></span>|<span data-ttu-id="38f29-141">İleti şifreleme için Basic192, ileti özeti için SHA1 ve anahtar kaydırması için Rsa15 kullanın.</span><span class="sxs-lookup"><span data-stu-id="38f29-141">Use Basic192 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="38f29-142">TripleDes</span><span class="sxs-lookup"><span data-stu-id="38f29-142">TripleDes</span></span>|<span data-ttu-id="38f29-143">Anahtar kaydırması için, TripleDes şifrelemesi, ileti özeti için SHA1, rsa-oaep-mgf1p kullanın.</span><span class="sxs-lookup"><span data-stu-id="38f29-143">Use TripleDes encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="38f29-144">Basic128Rsa15</span><span class="sxs-lookup"><span data-stu-id="38f29-144">Basic128Rsa15</span></span>|<span data-ttu-id="38f29-145">İleti şifreleme için Basic128, ileti özeti için SHA1 ve anahtar kaydırması için Rsa15 kullanın.</span><span class="sxs-lookup"><span data-stu-id="38f29-145">Use Basic128 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="38f29-146">TripleDesRsa15</span><span class="sxs-lookup"><span data-stu-id="38f29-146">TripleDesRsa15</span></span>|<span data-ttu-id="38f29-147">TripleDes şifrelemesi, ileti özeti için SHA1 ve anahtar kaydırması için Rsa15 kullanın.</span><span class="sxs-lookup"><span data-stu-id="38f29-147">Use TripleDes encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="38f29-148">Basic128Sha256</span><span class="sxs-lookup"><span data-stu-id="38f29-148">Basic128Sha256</span></span>|<span data-ttu-id="38f29-149">İleti için Basic128, ileti özeti için SHA256, anahtar kaydırması için rsa-oaep-mgf1p kullanın.</span><span class="sxs-lookup"><span data-stu-id="38f29-149">Use Basic128 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="38f29-150">Basic192Sha256</span><span class="sxs-lookup"><span data-stu-id="38f29-150">Basic192Sha256</span></span>|<span data-ttu-id="38f29-151">İleti için Basic192, ileti özeti için SHA256, anahtar kaydırması için rsa-oaep-mgf1p kullanın.</span><span class="sxs-lookup"><span data-stu-id="38f29-151">Use Basic192 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="38f29-152">Basic256Sha256</span><span class="sxs-lookup"><span data-stu-id="38f29-152">Basic256Sha256</span></span>|<span data-ttu-id="38f29-153">İleti için Basic256, ileti özeti için SHA256, anahtar kaydırması için rsa-oaep-mgf1p kullanın.</span><span class="sxs-lookup"><span data-stu-id="38f29-153">Use Basic256 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="38f29-154">TripleDesSha256</span><span class="sxs-lookup"><span data-stu-id="38f29-154">TripleDesSha256</span></span>|<span data-ttu-id="38f29-155">İleti şifreleme için TripleDes, SHA256 for Message Digest ve rsa-oaep-mgf1p için anahtar kaydırması kullanın.</span><span class="sxs-lookup"><span data-stu-id="38f29-155">Use TripleDes for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="38f29-156">Basic128Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="38f29-156">Basic128Sha256Rsa15</span></span>|<span data-ttu-id="38f29-157">İleti şifreleme için Basic128, ileti özeti için SHA256 ve anahtar kaydırması için Rsa15 kullanın.</span><span class="sxs-lookup"><span data-stu-id="38f29-157">Use Basic128 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="38f29-158">Basic192Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="38f29-158">Basic192Sha256Rsa15</span></span>|<span data-ttu-id="38f29-159">İleti şifreleme için Aes192, ileti özeti için SHA256 ve anahtar kaydırması için Rsa15 kullanın.</span><span class="sxs-lookup"><span data-stu-id="38f29-159">Use Aes192 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="38f29-160">Basic256Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="38f29-160">Basic256Sha256Rsa15</span></span>|<span data-ttu-id="38f29-161">İleti şifreleme için Basic256, ileti özeti için SHA256 ve anahtar kaydırması için Rsa15 kullanın.</span><span class="sxs-lookup"><span data-stu-id="38f29-161">Use Basic256 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="38f29-162">TripleDesSha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="38f29-162">TripleDesSha256Rsa15</span></span>|<span data-ttu-id="38f29-163">İleti şifreleme için TripleDes, SHA256 for Message Digest ve Rsa15 anahtar kaydırması için kullanın.</span><span class="sxs-lookup"><span data-stu-id="38f29-163">Use TripleDes for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="38f29-164">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="38f29-164">Child Elements</span></span>  
  
|<span data-ttu-id="38f29-165">Öğe</span><span class="sxs-lookup"><span data-stu-id="38f29-165">Element</span></span>|<span data-ttu-id="38f29-166">Açıklama</span><span class="sxs-lookup"><span data-stu-id="38f29-166">Description</span></span>|  
|-------------|-----------------|  
|[\<claimTypeRequirements>](claimtyperequirements-element.md)|<span data-ttu-id="38f29-167">Bu bağlama için bir talep türleri koleksiyonu belirtir.</span><span class="sxs-lookup"><span data-stu-id="38f29-167">Specifies a collection of claim types for this binding.</span></span> <span data-ttu-id="38f29-168">Her öğe türündedir <xref:System.ServiceModel.Configuration.ClaimTypeElement> .</span><span class="sxs-lookup"><span data-stu-id="38f29-168">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span>|  
|<span data-ttu-id="38f29-169">yayınlayan</span><span class="sxs-lookup"><span data-stu-id="38f29-169">issuer</span></span>|<span data-ttu-id="38f29-170">Bir güvenlik belirteci veren bir uç nokta belirtir.</span><span class="sxs-lookup"><span data-stu-id="38f29-170">Specifies an endpoint that issues a security token.</span></span> <span data-ttu-id="38f29-171">Bu öğe türündedir <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement> .</span><span class="sxs-lookup"><span data-stu-id="38f29-171">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>.</span></span>|  
|<span data-ttu-id="38f29-172">issuerMetadata</span><span class="sxs-lookup"><span data-stu-id="38f29-172">issuerMetadata</span></span>|<span data-ttu-id="38f29-173">Verenin uç nokta adresini belirtir.</span><span class="sxs-lookup"><span data-stu-id="38f29-173">Specifies the endpoint address of the issuer.</span></span>|  
|[\<tokenRequestParameters>](tokenrequestparameters.md)|<span data-ttu-id="38f29-174">Belirteç isteği parametrelerinin bir koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="38f29-174">A collection of token request parameters.</span></span> <span data-ttu-id="38f29-175">Her parametre bir XML öğesidir.</span><span class="sxs-lookup"><span data-stu-id="38f29-175">Each parameter is an XML element.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="38f29-176">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="38f29-176">Parent Elements</span></span>  
  
|<span data-ttu-id="38f29-177">Öğe</span><span class="sxs-lookup"><span data-stu-id="38f29-177">Element</span></span>|<span data-ttu-id="38f29-178">Açıklama</span><span class="sxs-lookup"><span data-stu-id="38f29-178">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-wsfederationhttpbinding.md)|<span data-ttu-id="38f29-179">Bağlama için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="38f29-179">Defines the security settings for a binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="38f29-180">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="38f29-180">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp>
- <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement.Message%2A>
- <xref:System.ServiceModel.WSFederationHttpSecurity.Message%2A>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>
- [<span data-ttu-id="38f29-181">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="38f29-181">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="38f29-182">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="38f29-182">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="38f29-183">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="38f29-183">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="38f29-184">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="38f29-184">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
