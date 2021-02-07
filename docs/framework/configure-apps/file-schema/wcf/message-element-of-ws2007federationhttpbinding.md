---
description: 'Hakkında daha fazla bilgi edinin: <message> öğesi <ws2007FederationHttpBinding>'
title: <message> öğesi <ws2007FederationHttpBinding>
ms.date: 03/30/2017
ms.assetid: 52cd941d-e230-4c82-8b29-333a7d20eca8
ms.openlocfilehash: f9116a5075f30421dfb26adc29ec0b167db33673
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99725460"
---
# <a name="message-element-of-ws2007federationhttpbinding"></a><span data-ttu-id="6fff2-103">\<message> öğesi \<ws2007FederationHttpBinding></span><span class="sxs-lookup"><span data-stu-id="6fff2-103">\<message> element of \<ws2007FederationHttpBinding></span></span>

<span data-ttu-id="6fff2-104">Öğesi için ileti düzeyi güvenlik ayarlarını tanımlar [\<ws2007FederationHttpBinding>](ws2007federationhttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="6fff2-104">Defines settings for the message-level security for the [\<ws2007FederationHttpBinding>](ws2007federationhttpbinding.md) element.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<ws2007FederationHttpBinding>**](ws2007federationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-element-of-ws2007federationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<message>**  
  
## <a name="syntax"></a><span data-ttu-id="6fff2-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="6fff2-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6fff2-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="6fff2-106">Attributes and Elements</span></span>  

 <span data-ttu-id="6fff2-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6fff2-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6fff2-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="6fff2-108">Attributes</span></span>  
  
|<span data-ttu-id="6fff2-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="6fff2-109">Attribute</span></span>|<span data-ttu-id="6fff2-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6fff2-110">Description</span></span>|  
|---------------|-----------------|  
|`algorithmSuite`|<span data-ttu-id="6fff2-111">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="6fff2-111">Optional.</span></span> <span data-ttu-id="6fff2-112">İleti şifrelemesini, imzayı ve anahtar sarması algoritmalarını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="6fff2-112">Sets the message encryption, signature, and key-wrap algorithms.</span></span> <span data-ttu-id="6fff2-113">Algoritmalar ve anahtar boyutları sınıfına göre belirlenir <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> .</span><span class="sxs-lookup"><span data-stu-id="6fff2-113">The algorithms and the key sizes are determined by the <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> class.</span></span> <span data-ttu-id="6fff2-114">Bu algoritmalar güvenlik Ilkesi dili (WS-SecurityPolicy) belirtiminde belirtilen olanlarla eşlenir.</span><span class="sxs-lookup"><span data-stu-id="6fff2-114">These algorithms map to those specified in the Security Policy Language (WS-SecurityPolicy) specification.</span></span><br /><br /> <span data-ttu-id="6fff2-115">Olası değerler için aşağıdaki tabloya bakın.</span><span class="sxs-lookup"><span data-stu-id="6fff2-115">See the following table for possible values.</span></span> <span data-ttu-id="6fff2-116">Varsayılan değer Basic256 ' dir.</span><span class="sxs-lookup"><span data-stu-id="6fff2-116">The default value is Basic256.</span></span>|  
|`issuedKeyType`|<span data-ttu-id="6fff2-117">Verilecek anahtarın türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="6fff2-117">Specifies the type of key to be issued.</span></span> <span data-ttu-id="6fff2-118">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="6fff2-118">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="6fff2-119">-SymmetricKey</span><span class="sxs-lookup"><span data-stu-id="6fff2-119">-   SymmetricKey</span></span><br /><span data-ttu-id="6fff2-120">-PublicKey</span><span class="sxs-lookup"><span data-stu-id="6fff2-120">-   PublicKey</span></span><br /><span data-ttu-id="6fff2-121">-Yataerkey</span><span class="sxs-lookup"><span data-stu-id="6fff2-121">-   BearerKey</span></span><br /><br /> <span data-ttu-id="6fff2-122">Varsayılan değer SymmetricKey ' dir.</span><span class="sxs-lookup"><span data-stu-id="6fff2-122">The default is SymmetricKey.</span></span> <span data-ttu-id="6fff2-123">Bu öznitelik türü <xref:System.IdentityModel.Tokens.SecurityKeyType> .</span><span class="sxs-lookup"><span data-stu-id="6fff2-123">This attribute is of type <xref:System.IdentityModel.Tokens.SecurityKeyType>.</span></span>|  
|`issuedTokenType`|<span data-ttu-id="6fff2-124">Verilecek belirtecin türünü belirten bir URI.</span><span class="sxs-lookup"><span data-stu-id="6fff2-124">A URI that specifies the type of token to be issued.</span></span> <span data-ttu-id="6fff2-125">Varsayılan değer: `null`.</span><span class="sxs-lookup"><span data-stu-id="6fff2-125">The default is `null`.</span></span>|  
|`negotiateServiceCredential`|<span data-ttu-id="6fff2-126">Hizmet kimlik bilgisinin, anlaşmanın parçası olarak alınıp alınmayacağını veya bant dışı kullanılabilir olup olmadığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="6fff2-126">A value that specifies whether the service credential should be exchanged as part of negotiation or is available out of band.</span></span> <span data-ttu-id="6fff2-127">Varsayılan olarak, `true` hizmet kimlik bilgisinin anlaşıldığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="6fff2-127">The default is `true`, which means that the service credential is negotiated.</span></span>|  
  
## <a name="algorithmsuite-attribute"></a><span data-ttu-id="6fff2-128">algorithmSuite özniteliği</span><span class="sxs-lookup"><span data-stu-id="6fff2-128">algorithmSuite Attribute</span></span>  
  
|<span data-ttu-id="6fff2-129">Değer</span><span class="sxs-lookup"><span data-stu-id="6fff2-129">Value</span></span>|<span data-ttu-id="6fff2-130">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6fff2-130">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="6fff2-131">Basic128</span><span class="sxs-lookup"><span data-stu-id="6fff2-131">Basic128</span></span>|<span data-ttu-id="6fff2-132">Anahtar kaydırması için AES128 şifrelemesi, ileti özeti için SHA1 ve rsa-oaep-mgf1p kullanın.</span><span class="sxs-lookup"><span data-stu-id="6fff2-132">Use Aes128 encryption, Sha1 for message digest, and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="6fff2-133">Basic192</span><span class="sxs-lookup"><span data-stu-id="6fff2-133">Basic192</span></span>|<span data-ttu-id="6fff2-134">Anahtar kaydırması için Aes192 şifrelemesi, ileti özeti için SHA1, rsa-oaep-mgf1p kullanın.</span><span class="sxs-lookup"><span data-stu-id="6fff2-134">Use Aes192 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="6fff2-135">Basic256</span><span class="sxs-lookup"><span data-stu-id="6fff2-135">Basic256</span></span>|<span data-ttu-id="6fff2-136">Anahtar kaydırması için AES256 şifrelemesi, ileti özeti için SHA1, rsa-oaep-mgf1p kullanın.</span><span class="sxs-lookup"><span data-stu-id="6fff2-136">Use Aes256 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="6fff2-137">Basic256Rsa15</span><span class="sxs-lookup"><span data-stu-id="6fff2-137">Basic256Rsa15</span></span>|<span data-ttu-id="6fff2-138">İleti şifreleme için AES256, ileti özeti için SHA1 ve anahtar kaydırması için Rsa15 kullanın.</span><span class="sxs-lookup"><span data-stu-id="6fff2-138">Use Aes256 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="6fff2-139">Basic192Rsa15</span><span class="sxs-lookup"><span data-stu-id="6fff2-139">Basic192Rsa15</span></span>|<span data-ttu-id="6fff2-140">İleti şifreleme için Aes192, ileti özeti için SHA1 ve anahtar kaydırması için Rsa15 kullanın.</span><span class="sxs-lookup"><span data-stu-id="6fff2-140">Use Aes192 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="6fff2-141">TripleDes</span><span class="sxs-lookup"><span data-stu-id="6fff2-141">TripleDes</span></span>|<span data-ttu-id="6fff2-142">Anahtar kaydırması için, TripleDes şifrelemesi, ileti özeti için SHA1, rsa-oaep-mgf1p kullanın.</span><span class="sxs-lookup"><span data-stu-id="6fff2-142">Use TripleDes encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="6fff2-143">Basic128Rsa15</span><span class="sxs-lookup"><span data-stu-id="6fff2-143">Basic128Rsa15</span></span>|<span data-ttu-id="6fff2-144">İleti şifreleme için AES128, ileti özeti için SHA1 ve anahtar kaydırması için Rsa15 kullanın.</span><span class="sxs-lookup"><span data-stu-id="6fff2-144">Use Aes128 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="6fff2-145">TripleDesRsa15</span><span class="sxs-lookup"><span data-stu-id="6fff2-145">TripleDesRsa15</span></span>|<span data-ttu-id="6fff2-146">TripleDes şifrelemesi, ileti özeti için SHA1 ve anahtar kaydırması için Rsa15 kullanın.</span><span class="sxs-lookup"><span data-stu-id="6fff2-146">Use TripleDes encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="6fff2-147">Basic128Sha256</span><span class="sxs-lookup"><span data-stu-id="6fff2-147">Basic128Sha256</span></span>|<span data-ttu-id="6fff2-148">İleti için AES256, ileti özeti için SHA256, anahtar kaydırması için rsa-oaep-mgf1p kullanın.</span><span class="sxs-lookup"><span data-stu-id="6fff2-148">Use Aes256 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="6fff2-149">Basic192Sha256</span><span class="sxs-lookup"><span data-stu-id="6fff2-149">Basic192Sha256</span></span>|<span data-ttu-id="6fff2-150">İleti için Aes192, ileti özeti için SHA256, anahtar kaydırması için rsa-oaep-mgf1p kullanın.</span><span class="sxs-lookup"><span data-stu-id="6fff2-150">Use Aes192 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="6fff2-151">Basic256Sha256</span><span class="sxs-lookup"><span data-stu-id="6fff2-151">Basic256Sha256</span></span>|<span data-ttu-id="6fff2-152">İleti için AES256, ileti özeti için SHA256, anahtar kaydırması için rsa-oaep-mgf1p kullanın.</span><span class="sxs-lookup"><span data-stu-id="6fff2-152">Use Aes256 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="6fff2-153">TripleDesSha256</span><span class="sxs-lookup"><span data-stu-id="6fff2-153">TripleDesSha256</span></span>|<span data-ttu-id="6fff2-154">İleti şifreleme için TripleDes, SHA256 for Message Digest ve rsa-oaep-mgf1p için anahtar kaydırması kullanın.</span><span class="sxs-lookup"><span data-stu-id="6fff2-154">Use TripleDes for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="6fff2-155">Basic128Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="6fff2-155">Basic128Sha256Rsa15</span></span>|<span data-ttu-id="6fff2-156">İleti şifreleme için AES128, ileti özeti için SHA256 ve anahtar kaydırması için Rsa15 kullanın.</span><span class="sxs-lookup"><span data-stu-id="6fff2-156">Use Aes128 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="6fff2-157">Basic192Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="6fff2-157">Basic192Sha256Rsa15</span></span>|<span data-ttu-id="6fff2-158">İleti şifreleme için Aes192, ileti özeti için SHA256 ve anahtar kaydırması için Rsa15 kullanın.</span><span class="sxs-lookup"><span data-stu-id="6fff2-158">Use Aes192 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="6fff2-159">Basic256Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="6fff2-159">Basic256Sha256Rsa15</span></span>|<span data-ttu-id="6fff2-160">İleti şifreleme için AES256, ileti özeti için SHA256 ve anahtar kaydırması için Rsa15 kullanın.</span><span class="sxs-lookup"><span data-stu-id="6fff2-160">Use Aes256 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="6fff2-161">TripleDesSha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="6fff2-161">TripleDesSha256Rsa15</span></span>|<span data-ttu-id="6fff2-162">İleti şifreleme için TripleDes, SHA256 for Message Digest ve Rsa15 anahtar kaydırması için kullanın.</span><span class="sxs-lookup"><span data-stu-id="6fff2-162">Use TripleDes for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6fff2-163">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="6fff2-163">Child Elements</span></span>  
  
|<span data-ttu-id="6fff2-164">Öğe</span><span class="sxs-lookup"><span data-stu-id="6fff2-164">Element</span></span>|<span data-ttu-id="6fff2-165">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6fff2-165">Description</span></span>|  
|-------------|-----------------|  
|[\<claimTypeRequirements>](claimtyperequirements-element.md)|<span data-ttu-id="6fff2-166">Bu bağlama için bir talep türleri koleksiyonu belirtir.</span><span class="sxs-lookup"><span data-stu-id="6fff2-166">Specifies a collection of claim types for this binding.</span></span> <span data-ttu-id="6fff2-167">Her öğe türündedir <xref:System.ServiceModel.Configuration.ClaimTypeElement> .</span><span class="sxs-lookup"><span data-stu-id="6fff2-167">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span>|  
|[\<issuer>](issuer.md)|<span data-ttu-id="6fff2-168">Bir güvenlik belirteci veren bir uç nokta belirtir.</span><span class="sxs-lookup"><span data-stu-id="6fff2-168">Specifies an endpoint that issues a security token.</span></span> <span data-ttu-id="6fff2-169">Bu öğe türündedir <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement> .</span><span class="sxs-lookup"><span data-stu-id="6fff2-169">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>.</span></span>|  
|[\<issuerMetadata>](issuermetadata.md)|<span data-ttu-id="6fff2-170">Verenin uç nokta adresini belirtir.</span><span class="sxs-lookup"><span data-stu-id="6fff2-170">Specifies the endpoint address of the issuer.</span></span>|  
|[\<tokenRequestParameters>](tokenrequestparameters.md)|<span data-ttu-id="6fff2-171">Belirteç isteği parametrelerinin bir koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="6fff2-171">A collection of token request parameters.</span></span> <span data-ttu-id="6fff2-172">Her parametre bir XML öğesidir.</span><span class="sxs-lookup"><span data-stu-id="6fff2-172">Each parameter is an XML element.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6fff2-173">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="6fff2-173">Parent Elements</span></span>  
  
|<span data-ttu-id="6fff2-174">Öğe</span><span class="sxs-lookup"><span data-stu-id="6fff2-174">Element</span></span>|<span data-ttu-id="6fff2-175">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6fff2-175">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-element-of-ws2007federationhttpbinding.md)|<span data-ttu-id="6fff2-176">Bağlama için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6fff2-176">Defines the security settings for a binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6fff2-177">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6fff2-177">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp>
- <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement.Message%2A>
- <xref:System.ServiceModel.WSFederationHttpSecurity.Message%2A>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>
- [<span data-ttu-id="6fff2-178">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="6fff2-178">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="6fff2-179">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="6fff2-179">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="6fff2-180">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="6fff2-180">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="6fff2-181">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="6fff2-181">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
