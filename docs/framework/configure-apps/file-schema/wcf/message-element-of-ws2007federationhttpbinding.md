---
title: <message> öğesi <ws2007FederationHttpBinding>
ms.date: 03/30/2017
ms.assetid: 52cd941d-e230-4c82-8b29-333a7d20eca8
ms.openlocfilehash: d71bce5e94568bdad3c52226fa1029a1dd87bfd9
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91204924"
---
# <a name="message-element-of-ws2007federationhttpbinding"></a><span data-ttu-id="cbac2-102">\<message> öğesi \<ws2007FederationHttpBinding></span><span class="sxs-lookup"><span data-stu-id="cbac2-102">\<message> element of \<ws2007FederationHttpBinding></span></span>

<span data-ttu-id="cbac2-103">Öğesi için ileti düzeyi güvenlik ayarlarını tanımlar [\<ws2007FederationHttpBinding>](ws2007federationhttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="cbac2-103">Defines settings for the message-level security for the [\<ws2007FederationHttpBinding>](ws2007federationhttpbinding.md) element.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<ws2007FederationHttpBinding>**](ws2007federationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-element-of-ws2007federationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<message>**  
  
## <a name="syntax"></a><span data-ttu-id="cbac2-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="cbac2-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cbac2-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="cbac2-105">Attributes and Elements</span></span>  

 <span data-ttu-id="cbac2-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="cbac2-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cbac2-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="cbac2-107">Attributes</span></span>  
  
|<span data-ttu-id="cbac2-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="cbac2-108">Attribute</span></span>|<span data-ttu-id="cbac2-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cbac2-109">Description</span></span>|  
|---------------|-----------------|  
|`algorithmSuite`|<span data-ttu-id="cbac2-110">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="cbac2-110">Optional.</span></span> <span data-ttu-id="cbac2-111">İleti şifrelemesini, imzayı ve anahtar sarması algoritmalarını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="cbac2-111">Sets the message encryption, signature, and key-wrap algorithms.</span></span> <span data-ttu-id="cbac2-112">Algoritmalar ve anahtar boyutları sınıfına göre belirlenir <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> .</span><span class="sxs-lookup"><span data-stu-id="cbac2-112">The algorithms and the key sizes are determined by the <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> class.</span></span> <span data-ttu-id="cbac2-113">Bu algoritmalar güvenlik Ilkesi dili (WS-SecurityPolicy) belirtiminde belirtilen olanlarla eşlenir.</span><span class="sxs-lookup"><span data-stu-id="cbac2-113">These algorithms map to those specified in the Security Policy Language (WS-SecurityPolicy) specification.</span></span><br /><br /> <span data-ttu-id="cbac2-114">Olası değerler için aşağıdaki tabloya bakın.</span><span class="sxs-lookup"><span data-stu-id="cbac2-114">See the following table for possible values.</span></span> <span data-ttu-id="cbac2-115">Varsayılan değer Basic256 ' dir.</span><span class="sxs-lookup"><span data-stu-id="cbac2-115">The default value is Basic256.</span></span>|  
|`issuedKeyType`|<span data-ttu-id="cbac2-116">Verilecek anahtarın türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="cbac2-116">Specifies the type of key to be issued.</span></span> <span data-ttu-id="cbac2-117">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="cbac2-117">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="cbac2-118">-SymmetricKey</span><span class="sxs-lookup"><span data-stu-id="cbac2-118">-   SymmetricKey</span></span><br /><span data-ttu-id="cbac2-119">-PublicKey</span><span class="sxs-lookup"><span data-stu-id="cbac2-119">-   PublicKey</span></span><br /><span data-ttu-id="cbac2-120">-Yataerkey</span><span class="sxs-lookup"><span data-stu-id="cbac2-120">-   BearerKey</span></span><br /><br /> <span data-ttu-id="cbac2-121">Varsayılan değer SymmetricKey ' dir.</span><span class="sxs-lookup"><span data-stu-id="cbac2-121">The default is SymmetricKey.</span></span> <span data-ttu-id="cbac2-122">Bu öznitelik türü <xref:System.IdentityModel.Tokens.SecurityKeyType> .</span><span class="sxs-lookup"><span data-stu-id="cbac2-122">This attribute is of type <xref:System.IdentityModel.Tokens.SecurityKeyType>.</span></span>|  
|`issuedTokenType`|<span data-ttu-id="cbac2-123">Verilecek belirtecin türünü belirten bir URI.</span><span class="sxs-lookup"><span data-stu-id="cbac2-123">A URI that specifies the type of token to be issued.</span></span> <span data-ttu-id="cbac2-124">Varsayılan değer: `null`.</span><span class="sxs-lookup"><span data-stu-id="cbac2-124">The default is `null`.</span></span>|  
|`negotiateServiceCredential`|<span data-ttu-id="cbac2-125">Hizmet kimlik bilgisinin, anlaşmanın parçası olarak alınıp alınmayacağını veya bant dışı kullanılabilir olup olmadığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="cbac2-125">A value that specifies whether the service credential should be exchanged as part of negotiation or is available out of band.</span></span> <span data-ttu-id="cbac2-126">Varsayılan olarak, `true` hizmet kimlik bilgisinin anlaşıldığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="cbac2-126">The default is `true`, which means that the service credential is negotiated.</span></span>|  
  
## <a name="algorithmsuite-attribute"></a><span data-ttu-id="cbac2-127">algorithmSuite özniteliği</span><span class="sxs-lookup"><span data-stu-id="cbac2-127">algorithmSuite Attribute</span></span>  
  
|<span data-ttu-id="cbac2-128">Değer</span><span class="sxs-lookup"><span data-stu-id="cbac2-128">Value</span></span>|<span data-ttu-id="cbac2-129">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cbac2-129">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="cbac2-130">Basic128</span><span class="sxs-lookup"><span data-stu-id="cbac2-130">Basic128</span></span>|<span data-ttu-id="cbac2-131">Anahtar kaydırması için AES128 şifrelemesi, ileti özeti için SHA1 ve rsa-oaep-mgf1p kullanın.</span><span class="sxs-lookup"><span data-stu-id="cbac2-131">Use Aes128 encryption, Sha1 for message digest, and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="cbac2-132">Basic192</span><span class="sxs-lookup"><span data-stu-id="cbac2-132">Basic192</span></span>|<span data-ttu-id="cbac2-133">Anahtar kaydırması için Aes192 şifrelemesi, ileti özeti için SHA1, rsa-oaep-mgf1p kullanın.</span><span class="sxs-lookup"><span data-stu-id="cbac2-133">Use Aes192 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="cbac2-134">Basic256</span><span class="sxs-lookup"><span data-stu-id="cbac2-134">Basic256</span></span>|<span data-ttu-id="cbac2-135">Anahtar kaydırması için AES256 şifrelemesi, ileti özeti için SHA1, rsa-oaep-mgf1p kullanın.</span><span class="sxs-lookup"><span data-stu-id="cbac2-135">Use Aes256 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="cbac2-136">Basic256Rsa15</span><span class="sxs-lookup"><span data-stu-id="cbac2-136">Basic256Rsa15</span></span>|<span data-ttu-id="cbac2-137">İleti şifreleme için AES256, ileti özeti için SHA1 ve anahtar kaydırması için Rsa15 kullanın.</span><span class="sxs-lookup"><span data-stu-id="cbac2-137">Use Aes256 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="cbac2-138">Basic192Rsa15</span><span class="sxs-lookup"><span data-stu-id="cbac2-138">Basic192Rsa15</span></span>|<span data-ttu-id="cbac2-139">İleti şifreleme için Aes192, ileti özeti için SHA1 ve anahtar kaydırması için Rsa15 kullanın.</span><span class="sxs-lookup"><span data-stu-id="cbac2-139">Use Aes192 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="cbac2-140">TripleDes</span><span class="sxs-lookup"><span data-stu-id="cbac2-140">TripleDes</span></span>|<span data-ttu-id="cbac2-141">Anahtar kaydırması için, TripleDes şifrelemesi, ileti özeti için SHA1, rsa-oaep-mgf1p kullanın.</span><span class="sxs-lookup"><span data-stu-id="cbac2-141">Use TripleDes encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="cbac2-142">Basic128Rsa15</span><span class="sxs-lookup"><span data-stu-id="cbac2-142">Basic128Rsa15</span></span>|<span data-ttu-id="cbac2-143">İleti şifreleme için AES128, ileti özeti için SHA1 ve anahtar kaydırması için Rsa15 kullanın.</span><span class="sxs-lookup"><span data-stu-id="cbac2-143">Use Aes128 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="cbac2-144">TripleDesRsa15</span><span class="sxs-lookup"><span data-stu-id="cbac2-144">TripleDesRsa15</span></span>|<span data-ttu-id="cbac2-145">TripleDes şifrelemesi, ileti özeti için SHA1 ve anahtar kaydırması için Rsa15 kullanın.</span><span class="sxs-lookup"><span data-stu-id="cbac2-145">Use TripleDes encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="cbac2-146">Basic128Sha256</span><span class="sxs-lookup"><span data-stu-id="cbac2-146">Basic128Sha256</span></span>|<span data-ttu-id="cbac2-147">İleti için AES256, ileti özeti için SHA256, anahtar kaydırması için rsa-oaep-mgf1p kullanın.</span><span class="sxs-lookup"><span data-stu-id="cbac2-147">Use Aes256 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="cbac2-148">Basic192Sha256</span><span class="sxs-lookup"><span data-stu-id="cbac2-148">Basic192Sha256</span></span>|<span data-ttu-id="cbac2-149">İleti için Aes192, ileti özeti için SHA256, anahtar kaydırması için rsa-oaep-mgf1p kullanın.</span><span class="sxs-lookup"><span data-stu-id="cbac2-149">Use Aes192 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="cbac2-150">Basic256Sha256</span><span class="sxs-lookup"><span data-stu-id="cbac2-150">Basic256Sha256</span></span>|<span data-ttu-id="cbac2-151">İleti için AES256, ileti özeti için SHA256, anahtar kaydırması için rsa-oaep-mgf1p kullanın.</span><span class="sxs-lookup"><span data-stu-id="cbac2-151">Use Aes256 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="cbac2-152">TripleDesSha256</span><span class="sxs-lookup"><span data-stu-id="cbac2-152">TripleDesSha256</span></span>|<span data-ttu-id="cbac2-153">İleti şifreleme için TripleDes, SHA256 for Message Digest ve rsa-oaep-mgf1p için anahtar kaydırması kullanın.</span><span class="sxs-lookup"><span data-stu-id="cbac2-153">Use TripleDes for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="cbac2-154">Basic128Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="cbac2-154">Basic128Sha256Rsa15</span></span>|<span data-ttu-id="cbac2-155">İleti şifreleme için AES128, ileti özeti için SHA256 ve anahtar kaydırması için Rsa15 kullanın.</span><span class="sxs-lookup"><span data-stu-id="cbac2-155">Use Aes128 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="cbac2-156">Basic192Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="cbac2-156">Basic192Sha256Rsa15</span></span>|<span data-ttu-id="cbac2-157">İleti şifreleme için Aes192, ileti özeti için SHA256 ve anahtar kaydırması için Rsa15 kullanın.</span><span class="sxs-lookup"><span data-stu-id="cbac2-157">Use Aes192 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="cbac2-158">Basic256Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="cbac2-158">Basic256Sha256Rsa15</span></span>|<span data-ttu-id="cbac2-159">İleti şifreleme için AES256, ileti özeti için SHA256 ve anahtar kaydırması için Rsa15 kullanın.</span><span class="sxs-lookup"><span data-stu-id="cbac2-159">Use Aes256 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="cbac2-160">TripleDesSha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="cbac2-160">TripleDesSha256Rsa15</span></span>|<span data-ttu-id="cbac2-161">İleti şifreleme için TripleDes, SHA256 for Message Digest ve Rsa15 anahtar kaydırması için kullanın.</span><span class="sxs-lookup"><span data-stu-id="cbac2-161">Use TripleDes for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cbac2-162">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="cbac2-162">Child Elements</span></span>  
  
|<span data-ttu-id="cbac2-163">Öğe</span><span class="sxs-lookup"><span data-stu-id="cbac2-163">Element</span></span>|<span data-ttu-id="cbac2-164">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cbac2-164">Description</span></span>|  
|-------------|-----------------|  
|[\<claimTypeRequirements>](claimtyperequirements-element.md)|<span data-ttu-id="cbac2-165">Bu bağlama için bir talep türleri koleksiyonu belirtir.</span><span class="sxs-lookup"><span data-stu-id="cbac2-165">Specifies a collection of claim types for this binding.</span></span> <span data-ttu-id="cbac2-166">Her öğe türündedir <xref:System.ServiceModel.Configuration.ClaimTypeElement> .</span><span class="sxs-lookup"><span data-stu-id="cbac2-166">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span>|  
|[\<issuer>](issuer.md)|<span data-ttu-id="cbac2-167">Bir güvenlik belirteci veren bir uç nokta belirtir.</span><span class="sxs-lookup"><span data-stu-id="cbac2-167">Specifies an endpoint that issues a security token.</span></span> <span data-ttu-id="cbac2-168">Bu öğe türündedir <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement> .</span><span class="sxs-lookup"><span data-stu-id="cbac2-168">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>.</span></span>|  
|[\<issuerMetadata>](issuermetadata.md)|<span data-ttu-id="cbac2-169">Verenin uç nokta adresini belirtir.</span><span class="sxs-lookup"><span data-stu-id="cbac2-169">Specifies the endpoint address of the issuer.</span></span>|  
|[\<tokenRequestParameters>](tokenrequestparameters.md)|<span data-ttu-id="cbac2-170">Belirteç isteği parametrelerinin bir koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="cbac2-170">A collection of token request parameters.</span></span> <span data-ttu-id="cbac2-171">Her parametre bir XML öğesidir.</span><span class="sxs-lookup"><span data-stu-id="cbac2-171">Each parameter is an XML element.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="cbac2-172">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="cbac2-172">Parent Elements</span></span>  
  
|<span data-ttu-id="cbac2-173">Öğe</span><span class="sxs-lookup"><span data-stu-id="cbac2-173">Element</span></span>|<span data-ttu-id="cbac2-174">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cbac2-174">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-element-of-ws2007federationhttpbinding.md)|<span data-ttu-id="cbac2-175">Bağlama için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="cbac2-175">Defines the security settings for a binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cbac2-176">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cbac2-176">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp>
- <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement.Message%2A>
- <xref:System.ServiceModel.WSFederationHttpSecurity.Message%2A>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>
- [<span data-ttu-id="cbac2-177">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="cbac2-177">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="cbac2-178">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="cbac2-178">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="cbac2-179">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="cbac2-179">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="cbac2-180">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="cbac2-180">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
