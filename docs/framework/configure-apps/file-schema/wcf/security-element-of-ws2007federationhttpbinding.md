---
title: "&lt;ws2007FederationHttpBinding&gt; &lt;güvenlik&gt; öğesi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 826219b4-3a16-45fc-832d-0cd7cbbd3b84
caps.latest.revision: "10"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 27fedcd8ae7501f484de0aa2f21af8c701990285
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltsecuritygt-element-of-ltws2007federationhttpbindinggt"></a><span data-ttu-id="a99ac-102">&lt;ws2007FederationHttpBinding&gt; &lt;güvenlik&gt; öğesi</span><span class="sxs-lookup"><span data-stu-id="a99ac-102">&lt;security&gt; element of &lt;ws2007FederationHttpBinding&gt;</span></span>
<span data-ttu-id="a99ac-103">Güvenlik ayarlarını tanımlar [ \<ws2007FederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007federationhttpbinding.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="a99ac-103">Defines the security settings of the [\<ws2007FederationHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007federationhttpbinding.md) element.</span></span>  
  
 <span data-ttu-id="a99ac-104">\<Sistem. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="a99ac-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="a99ac-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="a99ac-105">\<bindings></span></span>  
<span data-ttu-id="a99ac-106">\<ws2007FederationHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="a99ac-106">\<ws2007FederationHttpBinding></span></span>  
<span data-ttu-id="a99ac-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="a99ac-107">\<binding></span></span>  
<span data-ttu-id="a99ac-108">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="a99ac-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a99ac-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a99ac-109">Syntax</span></span>  
  
```xml  
<ws2007FederationBinding>  
    <binding >  
        <security mode="None/Message/TransportWithMessageCredential">  
           <message negotiateServiceCredential="Boolean"  
                algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/ Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
                defaultProtectionLevel="none/sign/EncryptAndSign"   
                issuedTokenType="string"   
                issuedKeyType="SymmetricKey/PublicKey"  
           </message>  
        </security>  
    </binding>  
</ws2007FederationBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a99ac-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="a99ac-110">Attributes and Elements</span></span>  
 <span data-ttu-id="a99ac-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a99ac-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a99ac-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a99ac-112">Attributes</span></span>  
  
|<span data-ttu-id="a99ac-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="a99ac-113">Attribute</span></span>|<span data-ttu-id="a99ac-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a99ac-114">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="a99ac-115">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="a99ac-115">Optional.</span></span> <span data-ttu-id="a99ac-116">Uygulanan güvenlik türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="a99ac-116">Specifies the type of security that is applied.</span></span> <span data-ttu-id="a99ac-117">Varsayılan değer `Message` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="a99ac-117">The default value is `Message`.</span></span> <span data-ttu-id="a99ac-118">Bu öznitelik türünde <xref:System.ServiceModel.WSFederationHttpSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="a99ac-118">This attribute is of type <xref:System.ServiceModel.WSFederationHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="a99ac-119">mod özniteliği</span><span class="sxs-lookup"><span data-stu-id="a99ac-119">mode Attribute</span></span>  
  
|<span data-ttu-id="a99ac-120">Değer</span><span class="sxs-lookup"><span data-stu-id="a99ac-120">Value</span></span>|<span data-ttu-id="a99ac-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a99ac-121">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a99ac-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="a99ac-122">None</span></span>|<span data-ttu-id="a99ac-123">SOAP iletisi aktarımı sırasında güvenli değildir.</span><span class="sxs-lookup"><span data-stu-id="a99ac-123">The SOAP message is not secure during transfer.</span></span>|  
|<span data-ttu-id="a99ac-124">İleti</span><span class="sxs-lookup"><span data-stu-id="a99ac-124">Message</span></span>|<span data-ttu-id="a99ac-125">Bütünlük, gizlilik, sunucu kimlik doğrulaması ve istemci kimlik doğrulaması SOAP iletisi güvenlik kullanılarak sağlanır.</span><span class="sxs-lookup"><span data-stu-id="a99ac-125">Integrity, confidentiality, server authentication and client authentication are provided using SOAP message security.</span></span> <span data-ttu-id="a99ac-126">Varsayılan olarak, gövde imzalı ve şifrelenir.</span><span class="sxs-lookup"><span data-stu-id="a99ac-126">By default, the body is encrypted and signed.</span></span> <span data-ttu-id="a99ac-127">Hizmeti bir sertifikayla yapılandırılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a99ac-127">The service must be configured with a certificate.</span></span> <span data-ttu-id="a99ac-128">İstemci kimlik doğrulaması istemci için bir güvenlik belirteci hizmeti tarafından verilen belirteç temel alır.</span><span class="sxs-lookup"><span data-stu-id="a99ac-128">Client authentication is based on the token issued to the client by a security token service.</span></span>|  
|<span data-ttu-id="a99ac-129">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="a99ac-129">TransportWithMessageCredential</span></span>|<span data-ttu-id="a99ac-130">Bütünlük, gizlilik ve sunucu kimlik doğrulaması HTTPS tarafından sağlanır.</span><span class="sxs-lookup"><span data-stu-id="a99ac-130">Integrity, confidentiality and server authentication are provided by HTTPS.</span></span> <span data-ttu-id="a99ac-131">Hizmeti bir sertifikayla yapılandırılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a99ac-131">The service must be configured with a certificate.</span></span> <span data-ttu-id="a99ac-132">İstemci kimlik doğrulaması SOAP iletisi güvenlik yoluyla sağlanır ve istemci için bir güvenlik belirteci hizmeti tarafından verilen belirteç dayanır.</span><span class="sxs-lookup"><span data-stu-id="a99ac-132">Client authentication is provided by means of SOAP message security and is based on the token issued to the client by a security token service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a99ac-133">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="a99ac-133">Child Elements</span></span>  
  
|<span data-ttu-id="a99ac-134">Öğe</span><span class="sxs-lookup"><span data-stu-id="a99ac-134">Element</span></span>|<span data-ttu-id="a99ac-135">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a99ac-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a99ac-136">\<İleti ></span><span class="sxs-lookup"><span data-stu-id="a99ac-136">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-of-ws2007httpbinding.md)|<span data-ttu-id="a99ac-137">İleti düzeyi güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a99ac-137">Defines the settings for the message-level security.</span></span> <span data-ttu-id="a99ac-138">Bu öğe türünde <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>.</span><span class="sxs-lookup"><span data-stu-id="a99ac-138">This element is of type <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a99ac-139">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="a99ac-139">Parent Elements</span></span>  
  
|<span data-ttu-id="a99ac-140">Öğe</span><span class="sxs-lookup"><span data-stu-id="a99ac-140">Element</span></span>|<span data-ttu-id="a99ac-141">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a99ac-141">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a99ac-142">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="a99ac-142">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="a99ac-143">Tüm bağlama özelliklerini tanımlayan [ \<wsDualHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="a99ac-143">Defines all binding capabilities of the [\<wsDualHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a99ac-144">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a99ac-144">See Also</span></span>  
 <xref:System.ServiceModel.WSFederationHttpSecurity>  
 <xref:System.ServiceModel.WSFederationHttpBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.WSFederationHttpBindingElement.Security%2A>  
 <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>  
 [<span data-ttu-id="a99ac-145">Nasıl yapılır: WSFederationHttpBinding Oluşturma</span><span class="sxs-lookup"><span data-stu-id="a99ac-145">How to: Create a WSFederationHttpBinding</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)  
 [<span data-ttu-id="a99ac-146">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="a99ac-146">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="a99ac-147">Kimlik Bilgisi Türü Seçme</span><span class="sxs-lookup"><span data-stu-id="a99ac-147">Selecting a Credential Type</span></span>](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)  
 [<span data-ttu-id="a99ac-148">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="a99ac-148">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="a99ac-149">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="a99ac-149">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="a99ac-150">Windows Communication Foundation Hizmetleri ve istemcileri yapılandırmak için bağlamaları kullanma</span><span class="sxs-lookup"><span data-stu-id="a99ac-150">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="a99ac-151">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="a99ac-151">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
