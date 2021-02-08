---
description: 'Hakkında daha fazla bilgi edinin: <message> öğesi <wsFederationHttpBinding>'
title: <message> öğesi <wsFederationHttpBinding>
ms.date: 03/30/2017
ms.assetid: 9d710389-d9d8-4454-9bf2-da4ccda31cec
ms.openlocfilehash: 64978902081ec9e5a603804fed3b378da12fe42e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802196"
---
# <a name="message-element-of-wsfederationhttpbinding"></a><span data-ttu-id="4c84f-103">\<message> öğesi \<wsFederationHttpBinding></span><span class="sxs-lookup"><span data-stu-id="4c84f-103">\<message> element of \<wsFederationHttpBinding></span></span>

<span data-ttu-id="4c84f-104">İçin ileti düzeyi güvenlik ayarlarını tanımlar [\<wsFederationHttpBinding>](wsfederationhttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="4c84f-104">Defines the settings for the message-level security for the [\<wsFederationHttpBinding>](wsfederationhttpbinding.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<message>**  
  
## <a name="syntax"></a><span data-ttu-id="4c84f-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="4c84f-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4c84f-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="4c84f-106">Attributes and Elements</span></span>  

 <span data-ttu-id="4c84f-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4c84f-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4c84f-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="4c84f-108">Attributes</span></span>  
  
|<span data-ttu-id="4c84f-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="4c84f-109">Attribute</span></span>|<span data-ttu-id="4c84f-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4c84f-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4c84f-111">algorithmSuite</span><span class="sxs-lookup"><span data-stu-id="4c84f-111">algorithmSuite</span></span>|<span data-ttu-id="4c84f-112">İleti şifrelemesini ve anahtar sarması algoritmalarını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="4c84f-112">Sets the message encryption and key-wrap algorithms.</span></span> <span data-ttu-id="4c84f-113">Bu özniteliğin geçerli değerleri için "algorithmSuite Attribute" tablosuna bakın.</span><span class="sxs-lookup"><span data-stu-id="4c84f-113">See the "algorithmSuite attribute" table for valid values of this attribute.</span></span> <span data-ttu-id="4c84f-114">`Basic256` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="4c84f-114">The default value is `Basic256`.</span></span><br /><br /> <span data-ttu-id="4c84f-115">Bu öznitelik türü <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> .</span><span class="sxs-lookup"><span data-stu-id="4c84f-115">This attribute is of type <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span></span> <span data-ttu-id="4c84f-116">Bu algoritmalar güvenlik Ilkesi dili (WS-SecurityPolicy) belirtiminde belirtilen olanlarla eşlenir.</span><span class="sxs-lookup"><span data-stu-id="4c84f-116">These algorithms map to those specified in the Security Policy Language (WS-SecurityPolicy) specification.</span></span>|  
|<span data-ttu-id="4c84f-117">IssuedKeyType</span><span class="sxs-lookup"><span data-stu-id="4c84f-117">issuedKeyType</span></span>|<span data-ttu-id="4c84f-118">Verilecek anahtarın türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="4c84f-118">Specifies the type of key to be issued.</span></span> <span data-ttu-id="4c84f-119">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="4c84f-119">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="4c84f-120">-SymmetricKey</span><span class="sxs-lookup"><span data-stu-id="4c84f-120">-   SymmetricKey</span></span><br /><span data-ttu-id="4c84f-121">-PublicKey</span><span class="sxs-lookup"><span data-stu-id="4c84f-121">-   PublicKey</span></span><br /><br /> <span data-ttu-id="4c84f-122">Varsayılan değer: `SymmetricKey`.</span><span class="sxs-lookup"><span data-stu-id="4c84f-122">The default is `SymmetricKey`.</span></span> <span data-ttu-id="4c84f-123">Bu öznitelik türü <xref:System.IdentityModel.Tokens.SecurityKeyType> .</span><span class="sxs-lookup"><span data-stu-id="4c84f-123">This attribute is of type <xref:System.IdentityModel.Tokens.SecurityKeyType>.</span></span>|  
|<span data-ttu-id="4c84f-124">IssuedTokenType</span><span class="sxs-lookup"><span data-stu-id="4c84f-124">issuedTokenType</span></span>|<span data-ttu-id="4c84f-125">Verilecek belirtecin türünü belirten bir URI içeren dize.</span><span class="sxs-lookup"><span data-stu-id="4c84f-125">A string that contains a URI that specifies the type of token to be issued.</span></span> <span data-ttu-id="4c84f-126">Varsayılan değer: `null`.</span><span class="sxs-lookup"><span data-stu-id="4c84f-126">The default is `null`.</span></span>|  
|<span data-ttu-id="4c84f-127">negotiateServiceCredential</span><span class="sxs-lookup"><span data-stu-id="4c84f-127">negotiateServiceCredential</span></span>|<span data-ttu-id="4c84f-128">Hizmet kimlik bilgisinin, anlaşmanın parçası olarak alınıp alınmayacağını veya bant dışı kullanılabilir olup olmadığını belirten bir Boolean değer.</span><span class="sxs-lookup"><span data-stu-id="4c84f-128">A Boolean value that specifies whether the service credential should be exchanged as part of negotiation or is available out of band.</span></span> <span data-ttu-id="4c84f-129">Varsayılan olarak, `true` hizmet kimlik bilgisinin anlaşıldığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="4c84f-129">The default is `true`, which means that the service credential is negotiated.</span></span>|  
  
## <a name="algorithmsuite-attribute"></a><span data-ttu-id="4c84f-130">algorithmSuite özniteliği</span><span class="sxs-lookup"><span data-stu-id="4c84f-130">algorithmSuite Attribute</span></span>  
  
|<span data-ttu-id="4c84f-131">Değer</span><span class="sxs-lookup"><span data-stu-id="4c84f-131">Value</span></span>|<span data-ttu-id="4c84f-132">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4c84f-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="4c84f-133">Basic128</span><span class="sxs-lookup"><span data-stu-id="4c84f-133">Basic128</span></span>|<span data-ttu-id="4c84f-134">Anahtar kaydırması için Basic128 şifrelemesi, ileti özeti için SHA1 ve rsa-oaep-mgf1p kullanın.</span><span class="sxs-lookup"><span data-stu-id="4c84f-134">Use Basic128 encryption, Sha1 for message digest, and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="4c84f-135">Basic192</span><span class="sxs-lookup"><span data-stu-id="4c84f-135">Basic192</span></span>|<span data-ttu-id="4c84f-136">Anahtar kaydırması için Basic192 şifrelemesi, ileti özeti için SHA1, rsa-oaep-mgf1p kullanın.</span><span class="sxs-lookup"><span data-stu-id="4c84f-136">Use Basic192 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="4c84f-137">Basic256</span><span class="sxs-lookup"><span data-stu-id="4c84f-137">Basic256</span></span>|<span data-ttu-id="4c84f-138">Anahtar kaydırması için Basic256 şifrelemesi, ileti özeti için SHA1, rsa-oaep-mgf1p kullanın.</span><span class="sxs-lookup"><span data-stu-id="4c84f-138">Use Basic256 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="4c84f-139">Basic256Rsa15</span><span class="sxs-lookup"><span data-stu-id="4c84f-139">Basic256Rsa15</span></span>|<span data-ttu-id="4c84f-140">İleti şifreleme için Basic256, ileti özeti için SHA1 ve anahtar kaydırması için Rsa15 kullanın.</span><span class="sxs-lookup"><span data-stu-id="4c84f-140">Use Basic256 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="4c84f-141">Basic192Rsa15</span><span class="sxs-lookup"><span data-stu-id="4c84f-141">Basic192Rsa15</span></span>|<span data-ttu-id="4c84f-142">İleti şifreleme için Basic192, ileti özeti için SHA1 ve anahtar kaydırması için Rsa15 kullanın.</span><span class="sxs-lookup"><span data-stu-id="4c84f-142">Use Basic192 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="4c84f-143">TripleDes</span><span class="sxs-lookup"><span data-stu-id="4c84f-143">TripleDes</span></span>|<span data-ttu-id="4c84f-144">Anahtar kaydırması için, TripleDes şifrelemesi, ileti özeti için SHA1, rsa-oaep-mgf1p kullanın.</span><span class="sxs-lookup"><span data-stu-id="4c84f-144">Use TripleDes encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="4c84f-145">Basic128Rsa15</span><span class="sxs-lookup"><span data-stu-id="4c84f-145">Basic128Rsa15</span></span>|<span data-ttu-id="4c84f-146">İleti şifreleme için Basic128, ileti özeti için SHA1 ve anahtar kaydırması için Rsa15 kullanın.</span><span class="sxs-lookup"><span data-stu-id="4c84f-146">Use Basic128 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="4c84f-147">TripleDesRsa15</span><span class="sxs-lookup"><span data-stu-id="4c84f-147">TripleDesRsa15</span></span>|<span data-ttu-id="4c84f-148">TripleDes şifrelemesi, ileti özeti için SHA1 ve anahtar kaydırması için Rsa15 kullanın.</span><span class="sxs-lookup"><span data-stu-id="4c84f-148">Use TripleDes encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="4c84f-149">Basic128Sha256</span><span class="sxs-lookup"><span data-stu-id="4c84f-149">Basic128Sha256</span></span>|<span data-ttu-id="4c84f-150">İleti için Basic128, ileti özeti için SHA256, anahtar kaydırması için rsa-oaep-mgf1p kullanın.</span><span class="sxs-lookup"><span data-stu-id="4c84f-150">Use Basic128 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="4c84f-151">Basic192Sha256</span><span class="sxs-lookup"><span data-stu-id="4c84f-151">Basic192Sha256</span></span>|<span data-ttu-id="4c84f-152">İleti için Basic192, ileti özeti için SHA256, anahtar kaydırması için rsa-oaep-mgf1p kullanın.</span><span class="sxs-lookup"><span data-stu-id="4c84f-152">Use Basic192 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="4c84f-153">Basic256Sha256</span><span class="sxs-lookup"><span data-stu-id="4c84f-153">Basic256Sha256</span></span>|<span data-ttu-id="4c84f-154">İleti için Basic256, ileti özeti için SHA256, anahtar kaydırması için rsa-oaep-mgf1p kullanın.</span><span class="sxs-lookup"><span data-stu-id="4c84f-154">Use Basic256 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="4c84f-155">TripleDesSha256</span><span class="sxs-lookup"><span data-stu-id="4c84f-155">TripleDesSha256</span></span>|<span data-ttu-id="4c84f-156">İleti şifreleme için TripleDes, SHA256 for Message Digest ve rsa-oaep-mgf1p için anahtar kaydırması kullanın.</span><span class="sxs-lookup"><span data-stu-id="4c84f-156">Use TripleDes for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="4c84f-157">Basic128Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="4c84f-157">Basic128Sha256Rsa15</span></span>|<span data-ttu-id="4c84f-158">İleti şifreleme için Basic128, ileti özeti için SHA256 ve anahtar kaydırması için Rsa15 kullanın.</span><span class="sxs-lookup"><span data-stu-id="4c84f-158">Use Basic128 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="4c84f-159">Basic192Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="4c84f-159">Basic192Sha256Rsa15</span></span>|<span data-ttu-id="4c84f-160">İleti şifreleme için Aes192, ileti özeti için SHA256 ve anahtar kaydırması için Rsa15 kullanın.</span><span class="sxs-lookup"><span data-stu-id="4c84f-160">Use Aes192 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="4c84f-161">Basic256Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="4c84f-161">Basic256Sha256Rsa15</span></span>|<span data-ttu-id="4c84f-162">İleti şifreleme için Basic256, ileti özeti için SHA256 ve anahtar kaydırması için Rsa15 kullanın.</span><span class="sxs-lookup"><span data-stu-id="4c84f-162">Use Basic256 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="4c84f-163">TripleDesSha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="4c84f-163">TripleDesSha256Rsa15</span></span>|<span data-ttu-id="4c84f-164">İleti şifreleme için TripleDes, SHA256 for Message Digest ve Rsa15 anahtar kaydırması için kullanın.</span><span class="sxs-lookup"><span data-stu-id="4c84f-164">Use TripleDes for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4c84f-165">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="4c84f-165">Child Elements</span></span>  
  
|<span data-ttu-id="4c84f-166">Öğe</span><span class="sxs-lookup"><span data-stu-id="4c84f-166">Element</span></span>|<span data-ttu-id="4c84f-167">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4c84f-167">Description</span></span>|  
|-------------|-----------------|  
|[\<claimTypeRequirements>](claimtyperequirements-element.md)|<span data-ttu-id="4c84f-168">Bu bağlama için bir talep türleri koleksiyonu belirtir.</span><span class="sxs-lookup"><span data-stu-id="4c84f-168">Specifies a collection of claim types for this binding.</span></span> <span data-ttu-id="4c84f-169">Her öğe türündedir <xref:System.ServiceModel.Configuration.ClaimTypeElement> .</span><span class="sxs-lookup"><span data-stu-id="4c84f-169">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span>|  
|<span data-ttu-id="4c84f-170">yayınlayan</span><span class="sxs-lookup"><span data-stu-id="4c84f-170">issuer</span></span>|<span data-ttu-id="4c84f-171">Bir güvenlik belirteci veren bir uç nokta belirtir.</span><span class="sxs-lookup"><span data-stu-id="4c84f-171">Specifies an endpoint that issues a security token.</span></span> <span data-ttu-id="4c84f-172">Bu öğe türündedir <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement> .</span><span class="sxs-lookup"><span data-stu-id="4c84f-172">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>.</span></span>|  
|<span data-ttu-id="4c84f-173">issuerMetadata</span><span class="sxs-lookup"><span data-stu-id="4c84f-173">issuerMetadata</span></span>|<span data-ttu-id="4c84f-174">Verenin uç nokta adresini belirtir.</span><span class="sxs-lookup"><span data-stu-id="4c84f-174">Specifies the endpoint address of the issuer.</span></span>|  
|[\<tokenRequestParameters>](tokenrequestparameters.md)|<span data-ttu-id="4c84f-175">Belirteç isteği parametrelerinin bir koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="4c84f-175">A collection of token request parameters.</span></span> <span data-ttu-id="4c84f-176">Her parametre bir XML öğesidir.</span><span class="sxs-lookup"><span data-stu-id="4c84f-176">Each parameter is an XML element.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4c84f-177">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="4c84f-177">Parent Elements</span></span>  
  
|<span data-ttu-id="4c84f-178">Öğe</span><span class="sxs-lookup"><span data-stu-id="4c84f-178">Element</span></span>|<span data-ttu-id="4c84f-179">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4c84f-179">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-wsfederationhttpbinding.md)|<span data-ttu-id="4c84f-180">Bağlama için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="4c84f-180">Defines the security settings for a binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4c84f-181">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4c84f-181">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp>
- <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement.Message%2A>
- <xref:System.ServiceModel.WSFederationHttpSecurity.Message%2A>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>
- [<span data-ttu-id="4c84f-182">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="4c84f-182">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="4c84f-183">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="4c84f-183">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="4c84f-184">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="4c84f-184">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="4c84f-185">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="4c84f-185">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
