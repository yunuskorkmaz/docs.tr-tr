---
title: "&lt;wsFederationHttpBinding&gt; &lt;güvenliği&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a8e5e854-b8dc-4921-843d-34b6a4a6a8ba
caps.latest.revision: "15"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: dd4f517c17efce85f7a83d7d8545cf58322d5373
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltsecuritygt-of-ltwsfederationhttpbindinggt"></a><span data-ttu-id="34385-102">&lt;wsFederationHttpBinding&gt; &lt;güvenliği&gt;</span><span class="sxs-lookup"><span data-stu-id="34385-102">&lt;security&gt; of &lt;wsFederationHttpBinding&gt;</span></span>
<span data-ttu-id="34385-103">Güvenlik ayarlarını tanımlar [ \<wsFederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="34385-103">Defines the security settings of the [\<wsFederationHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md).</span></span>  
  
 <span data-ttu-id="34385-104">\<Sistem. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="34385-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="34385-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="34385-105">\<bindings></span></span>  
<span data-ttu-id="34385-106">\<wsFederatedBinding ></span><span class="sxs-lookup"><span data-stu-id="34385-106">\<wsFederatedBinding></span></span>  
<span data-ttu-id="34385-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="34385-107">\<binding></span></span>  
<span data-ttu-id="34385-108">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="34385-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34385-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="34385-109">Syntax</span></span>  
  
```xml  
<wsFederationBinding>  
    <binding >  
       <security mode="None/Message/TransportWithMessageCredential">  
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
                                   X509FindType=System.Security.Cryptography.X509certificates.X509findtype/>  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="34385-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="34385-110">Attributes and Elements</span></span>  
 <span data-ttu-id="34385-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="34385-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="34385-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="34385-112">Attributes</span></span>  
  
|<span data-ttu-id="34385-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="34385-113">Attribute</span></span>|<span data-ttu-id="34385-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="34385-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="34385-115">Mod</span><span class="sxs-lookup"><span data-stu-id="34385-115">Mode</span></span>|<span data-ttu-id="34385-116">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="34385-116">Optional.</span></span> <span data-ttu-id="34385-117">Uygulanan güvenlik türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="34385-117">Specifies the type of security that is applied.</span></span> <span data-ttu-id="34385-118">Varsayılan değer `Message` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="34385-118">The default value is `Message`.</span></span> <span data-ttu-id="34385-119">Bu öznitelik türünde <xref:System.ServiceModel.WSFederationHttpSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="34385-119">This attribute is of type <xref:System.ServiceModel.WSFederationHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="34385-120">mod özniteliği</span><span class="sxs-lookup"><span data-stu-id="34385-120">Mode Attribute</span></span>  
  
|<span data-ttu-id="34385-121">Değer</span><span class="sxs-lookup"><span data-stu-id="34385-121">Value</span></span>|<span data-ttu-id="34385-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="34385-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="34385-123">Yok.</span><span class="sxs-lookup"><span data-stu-id="34385-123">None</span></span>|<span data-ttu-id="34385-124">SOAP iletisi aktarımı sırasında güvenli değildir.</span><span class="sxs-lookup"><span data-stu-id="34385-124">The SOAP message is not secure during transfer.</span></span>|  
|<span data-ttu-id="34385-125">İleti</span><span class="sxs-lookup"><span data-stu-id="34385-125">Message</span></span>|<span data-ttu-id="34385-126">Bütünlük, gizlilik, sunucu kimlik doğrulaması ve istemci kimlik doğrulaması SOAP iletisi güvenlik kullanılarak sağlanır.</span><span class="sxs-lookup"><span data-stu-id="34385-126">Integrity, confidentiality, server authentication and client authentication are provided using SOAP message security.</span></span> <span data-ttu-id="34385-127">Varsayılan olarak, gövde imzalı ve şifrelenir.</span><span class="sxs-lookup"><span data-stu-id="34385-127">By default, the body is encrypted and signed.</span></span> <span data-ttu-id="34385-128">Hizmet bir sertifika ile yapılandırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="34385-128">The service needs to be configured with a certificate.</span></span> <span data-ttu-id="34385-129">İstemci kimlik doğrulaması, istemci için bir güvenlik belirteci hizmeti tarafından verilen belirteç dayalı</span><span class="sxs-lookup"><span data-stu-id="34385-129">Client authentication is based on the token issued to the client by a security token service</span></span>|  
|<span data-ttu-id="34385-130">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="34385-130">TransportWithMessageCredential</span></span>|<span data-ttu-id="34385-131">Bütünlük, gizlilik ve sunucu kimlik doğrulaması HTTPS tarafından sağlanır.</span><span class="sxs-lookup"><span data-stu-id="34385-131">Integrity, confidentiality and server authentication are provided by HTTPS.</span></span> <span data-ttu-id="34385-132">Hizmet bir sertifika ile yapılandırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="34385-132">The service needs to be configured with a certificate.</span></span> <span data-ttu-id="34385-133">İstemci kimlik doğrulaması SOAP iletisi güvenlik yoluyla sağlanır ve istemci için bir güvenlik belirteci hizmeti tarafından verilen belirteç dayanır.</span><span class="sxs-lookup"><span data-stu-id="34385-133">Client authentication is provided by means of SOAP message security and is based on the token issued to the client by a security token service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="34385-134">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="34385-134">Child Elements</span></span>  
  
|<span data-ttu-id="34385-135">Öğe</span><span class="sxs-lookup"><span data-stu-id="34385-135">Element</span></span>|<span data-ttu-id="34385-136">Açıklama</span><span class="sxs-lookup"><span data-stu-id="34385-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="34385-137">\<İleti ></span><span class="sxs-lookup"><span data-stu-id="34385-137">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-wsfederationhttpbinding.md)|<span data-ttu-id="34385-138">İleti düzeyi güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="34385-138">Defines the settings for the message-level security.</span></span> <span data-ttu-id="34385-139">Bu öğe türünde <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>.</span><span class="sxs-lookup"><span data-stu-id="34385-139">This element is of type <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="34385-140">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="34385-140">Parent Elements</span></span>  
  
|<span data-ttu-id="34385-141">Öğe</span><span class="sxs-lookup"><span data-stu-id="34385-141">Element</span></span>|<span data-ttu-id="34385-142">Açıklama</span><span class="sxs-lookup"><span data-stu-id="34385-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="34385-143">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="34385-143">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="34385-144">Tüm bağlama özelliklerini tanımlayan [ \<wsDualHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="34385-144">Defines all binding capabilities of the [\<wsDualHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="34385-145">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="34385-145">See Also</span></span>  
 <xref:System.ServiceModel.WSFederationHttpSecurity>  
 <xref:System.ServiceModel.WSFederationHttpBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.WSFederationHttpBindingElement.Security%2A>  
 <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>  
 [<span data-ttu-id="34385-146">Nasıl yapılır: WSFederationHttpBinding oluşturma</span><span class="sxs-lookup"><span data-stu-id="34385-146">How to: Create a WSFederationHttpBinding</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)  
 [<span data-ttu-id="34385-147">Hizmetler ve istemcileri güvenli hale getirme</span><span class="sxs-lookup"><span data-stu-id="34385-147">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="34385-148">Bir kimlik bilgisi türü seçme</span><span class="sxs-lookup"><span data-stu-id="34385-148">Selecting a Credential Type</span></span>](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)  
 [<span data-ttu-id="34385-149">Bağlamaları</span><span class="sxs-lookup"><span data-stu-id="34385-149">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="34385-150">Sistem tarafından sağlanan bağlamaları yapılandırma</span><span class="sxs-lookup"><span data-stu-id="34385-150">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="34385-151">Windows Communication Foundation Hizmetleri ve istemcileri yapılandırmak için bağlamaları kullanma</span><span class="sxs-lookup"><span data-stu-id="34385-151">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="34385-152">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="34385-152">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
