---
title: '&lt;ws2007FederationHttpBinding&gt; &lt;güvenlik&gt; öğesi'
ms.date: 03/30/2017
ms.assetid: 826219b4-3a16-45fc-832d-0cd7cbbd3b84
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 5f1a7d0ed1bffe2ca2da9318eef700b1d4924c22
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32749887"
---
# <a name="ltsecuritygt-element-of-ltws2007federationhttpbindinggt"></a><span data-ttu-id="d6405-102">&lt;ws2007FederationHttpBinding&gt; &lt;güvenlik&gt; öğesi</span><span class="sxs-lookup"><span data-stu-id="d6405-102">&lt;security&gt; element of &lt;ws2007FederationHttpBinding&gt;</span></span>
<span data-ttu-id="d6405-103">Güvenlik ayarlarını tanımlar [ \<ws2007FederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007federationhttpbinding.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="d6405-103">Defines the security settings of the [\<ws2007FederationHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007federationhttpbinding.md) element.</span></span>  
  
 <span data-ttu-id="d6405-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="d6405-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="d6405-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="d6405-105">\<bindings></span></span>  
<span data-ttu-id="d6405-106">\<ws2007FederationHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="d6405-106">\<ws2007FederationHttpBinding></span></span>  
<span data-ttu-id="d6405-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="d6405-107">\<binding></span></span>  
<span data-ttu-id="d6405-108">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="d6405-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6405-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d6405-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d6405-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="d6405-110">Attributes and Elements</span></span>  
 <span data-ttu-id="d6405-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d6405-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d6405-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d6405-112">Attributes</span></span>  
  
|<span data-ttu-id="d6405-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="d6405-113">Attribute</span></span>|<span data-ttu-id="d6405-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d6405-114">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="d6405-115">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="d6405-115">Optional.</span></span> <span data-ttu-id="d6405-116">Uygulanan güvenlik türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="d6405-116">Specifies the type of security that is applied.</span></span> <span data-ttu-id="d6405-117">Varsayılan değer `Message` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="d6405-117">The default value is `Message`.</span></span> <span data-ttu-id="d6405-118">Bu öznitelik türünde <xref:System.ServiceModel.WSFederationHttpSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="d6405-118">This attribute is of type <xref:System.ServiceModel.WSFederationHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="d6405-119">mod özniteliği</span><span class="sxs-lookup"><span data-stu-id="d6405-119">mode Attribute</span></span>  
  
|<span data-ttu-id="d6405-120">Değer</span><span class="sxs-lookup"><span data-stu-id="d6405-120">Value</span></span>|<span data-ttu-id="d6405-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d6405-121">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d6405-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="d6405-122">None</span></span>|<span data-ttu-id="d6405-123">SOAP iletisi aktarımı sırasında güvenli değildir.</span><span class="sxs-lookup"><span data-stu-id="d6405-123">The SOAP message is not secure during transfer.</span></span>|  
|<span data-ttu-id="d6405-124">İleti</span><span class="sxs-lookup"><span data-stu-id="d6405-124">Message</span></span>|<span data-ttu-id="d6405-125">Bütünlük, gizlilik, sunucu kimlik doğrulaması ve istemci kimlik doğrulaması SOAP iletisi güvenlik kullanılarak sağlanır.</span><span class="sxs-lookup"><span data-stu-id="d6405-125">Integrity, confidentiality, server authentication and client authentication are provided using SOAP message security.</span></span> <span data-ttu-id="d6405-126">Varsayılan olarak, gövde imzalı ve şifrelenir.</span><span class="sxs-lookup"><span data-stu-id="d6405-126">By default, the body is encrypted and signed.</span></span> <span data-ttu-id="d6405-127">Hizmeti bir sertifikayla yapılandırılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d6405-127">The service must be configured with a certificate.</span></span> <span data-ttu-id="d6405-128">İstemci kimlik doğrulaması istemci için bir güvenlik belirteci hizmeti tarafından verilen belirteç temel alır.</span><span class="sxs-lookup"><span data-stu-id="d6405-128">Client authentication is based on the token issued to the client by a security token service.</span></span>|  
|<span data-ttu-id="d6405-129">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="d6405-129">TransportWithMessageCredential</span></span>|<span data-ttu-id="d6405-130">Bütünlük, gizlilik ve sunucu kimlik doğrulaması HTTPS tarafından sağlanır.</span><span class="sxs-lookup"><span data-stu-id="d6405-130">Integrity, confidentiality and server authentication are provided by HTTPS.</span></span> <span data-ttu-id="d6405-131">Hizmeti bir sertifikayla yapılandırılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d6405-131">The service must be configured with a certificate.</span></span> <span data-ttu-id="d6405-132">İstemci kimlik doğrulaması SOAP iletisi güvenlik yoluyla sağlanır ve istemci için bir güvenlik belirteci hizmeti tarafından verilen belirteç dayanır.</span><span class="sxs-lookup"><span data-stu-id="d6405-132">Client authentication is provided by means of SOAP message security and is based on the token issued to the client by a security token service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d6405-133">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="d6405-133">Child Elements</span></span>  
  
|<span data-ttu-id="d6405-134">Öğe</span><span class="sxs-lookup"><span data-stu-id="d6405-134">Element</span></span>|<span data-ttu-id="d6405-135">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d6405-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d6405-136">\<İleti ></span><span class="sxs-lookup"><span data-stu-id="d6405-136">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-of-ws2007httpbinding.md)|<span data-ttu-id="d6405-137">İleti düzeyi güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d6405-137">Defines the settings for the message-level security.</span></span> <span data-ttu-id="d6405-138">Bu öğe türünde <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>.</span><span class="sxs-lookup"><span data-stu-id="d6405-138">This element is of type <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d6405-139">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="d6405-139">Parent Elements</span></span>  
  
|<span data-ttu-id="d6405-140">Öğe</span><span class="sxs-lookup"><span data-stu-id="d6405-140">Element</span></span>|<span data-ttu-id="d6405-141">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d6405-141">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d6405-142">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="d6405-142">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="d6405-143">Tüm bağlama özelliklerini tanımlayan [ \<wsDualHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="d6405-143">Defines all binding capabilities of the [\<wsDualHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d6405-144">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d6405-144">See Also</span></span>  
 <xref:System.ServiceModel.WSFederationHttpSecurity>  
 <xref:System.ServiceModel.WSFederationHttpBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.WSFederationHttpBindingElement.Security%2A>  
 <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>  
 [<span data-ttu-id="d6405-145">Nasıl yapılır: WSFederationHttpBinding Oluşturma</span><span class="sxs-lookup"><span data-stu-id="d6405-145">How to: Create a WSFederationHttpBinding</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)  
 [<span data-ttu-id="d6405-146">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="d6405-146">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="d6405-147">Kimlik Bilgisi Türü Seçme</span><span class="sxs-lookup"><span data-stu-id="d6405-147">Selecting a Credential Type</span></span>](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)  
 [<span data-ttu-id="d6405-148">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="d6405-148">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="d6405-149">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="d6405-149">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="d6405-150">Windows Communication Foundation Hizmetleri ve istemcileri yapılandırmak için bağlamaları kullanma</span><span class="sxs-lookup"><span data-stu-id="d6405-150">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="d6405-151">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="d6405-151">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
