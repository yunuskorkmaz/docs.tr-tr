---
title: '&lt;ws2007FederationHttpBinding&gt; &lt;güvenlik&gt; öğesi'
ms.date: 03/30/2017
ms.assetid: 826219b4-3a16-45fc-832d-0cd7cbbd3b84
ms.openlocfilehash: 32dcf2995780c4a92109232bbdf8d92b3365fdd7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54629594"
---
# <a name="ltsecuritygt-element-of-ltws2007federationhttpbindinggt"></a><span data-ttu-id="cab64-102">&lt;ws2007FederationHttpBinding&gt; &lt;güvenlik&gt; öğesi</span><span class="sxs-lookup"><span data-stu-id="cab64-102">&lt;security&gt; element of &lt;ws2007FederationHttpBinding&gt;</span></span>
<span data-ttu-id="cab64-103">Güvenlik ayarlarını tanımlar [ \<ws2007FederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007federationhttpbinding.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="cab64-103">Defines the security settings of the [\<ws2007FederationHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007federationhttpbinding.md) element.</span></span>  
  
 <span data-ttu-id="cab64-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="cab64-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="cab64-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="cab64-105">\<bindings></span></span>  
<span data-ttu-id="cab64-106">\<ws2007FederationHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="cab64-106">\<ws2007FederationHttpBinding></span></span>  
<span data-ttu-id="cab64-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="cab64-107">\<binding></span></span>  
<span data-ttu-id="cab64-108">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="cab64-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cab64-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cab64-109">Syntax</span></span>  
  
```xml  
<ws2007FederationBinding>
  <binding>
    <security mode="None/Message/TransportWithMessageCredential">
      <message negotiateServiceCredential="Boolean"
               algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/  Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
               defaultProtectionLevel="none/sign/EncryptAndSign"
               issuedTokenType="string"
               issuedKeyType="SymmetricKey/PublicKey">
      </message>
    </security>
  </binding>
</ws2007FederationBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cab64-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="cab64-110">Attributes and Elements</span></span>  
 <span data-ttu-id="cab64-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="cab64-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cab64-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="cab64-112">Attributes</span></span>  
  
|<span data-ttu-id="cab64-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="cab64-113">Attribute</span></span>|<span data-ttu-id="cab64-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cab64-114">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="cab64-115">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="cab64-115">Optional.</span></span> <span data-ttu-id="cab64-116">Uygulanan güvenlik türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="cab64-116">Specifies the type of security that is applied.</span></span> <span data-ttu-id="cab64-117">Varsayılan değer `Message` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="cab64-117">The default value is `Message`.</span></span> <span data-ttu-id="cab64-118">Bu öznitelik türünde <xref:System.ServiceModel.WSFederationHttpSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="cab64-118">This attribute is of type <xref:System.ServiceModel.WSFederationHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="cab64-119">mod özniteliği</span><span class="sxs-lookup"><span data-stu-id="cab64-119">mode Attribute</span></span>  
  
|<span data-ttu-id="cab64-120">Değer</span><span class="sxs-lookup"><span data-stu-id="cab64-120">Value</span></span>|<span data-ttu-id="cab64-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cab64-121">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="cab64-122">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="cab64-122">None</span></span>|<span data-ttu-id="cab64-123">SOAP ileti aktarım sırasında güvenli değildir.</span><span class="sxs-lookup"><span data-stu-id="cab64-123">The SOAP message is not secure during transfer.</span></span>|  
|<span data-ttu-id="cab64-124">İleti</span><span class="sxs-lookup"><span data-stu-id="cab64-124">Message</span></span>|<span data-ttu-id="cab64-125">SOAP ileti güveliği kullanarak bütünlüğü, gizlilik, sunucu kimlik doğrulaması ve istemci kimlik doğrulaması sağlanır.</span><span class="sxs-lookup"><span data-stu-id="cab64-125">Integrity, confidentiality, server authentication and client authentication are provided using SOAP message security.</span></span> <span data-ttu-id="cab64-126">Varsayılan olarak, gövde imzalı ve şifrelenir.</span><span class="sxs-lookup"><span data-stu-id="cab64-126">By default, the body is encrypted and signed.</span></span> <span data-ttu-id="cab64-127">Hizmeti bir sertifikayla yapılandırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="cab64-127">The service must be configured with a certificate.</span></span> <span data-ttu-id="cab64-128">İstemci kimlik doğrulaması güvenlik belirteci hizmeti tarafından istemciye verilen belirtecin temel alır.</span><span class="sxs-lookup"><span data-stu-id="cab64-128">Client authentication is based on the token issued to the client by a security token service.</span></span>|  
|<span data-ttu-id="cab64-129">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="cab64-129">TransportWithMessageCredential</span></span>|<span data-ttu-id="cab64-130">Bütünlüğü, gizliliği ve sunucu kimlik doğrulaması HTTPS tarafından sağlanır.</span><span class="sxs-lookup"><span data-stu-id="cab64-130">Integrity, confidentiality and server authentication are provided by HTTPS.</span></span> <span data-ttu-id="cab64-131">Hizmeti bir sertifikayla yapılandırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="cab64-131">The service must be configured with a certificate.</span></span> <span data-ttu-id="cab64-132">İstemci kimlik doğrulaması yoluyla SOAP ileti güvenliği sağlanır ve istemciye bir güvenlik belirteci hizmeti tarafından verilen belirtecin dayanır.</span><span class="sxs-lookup"><span data-stu-id="cab64-132">Client authentication is provided by means of SOAP message security and is based on the token issued to the client by a security token service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cab64-133">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="cab64-133">Child Elements</span></span>  
  
|<span data-ttu-id="cab64-134">Öğe</span><span class="sxs-lookup"><span data-stu-id="cab64-134">Element</span></span>|<span data-ttu-id="cab64-135">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cab64-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cab64-136">\<İleti ></span><span class="sxs-lookup"><span data-stu-id="cab64-136">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-of-ws2007httpbinding.md)|<span data-ttu-id="cab64-137">İleti düzeyi güvenlik ayarları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="cab64-137">Defines the settings for the message-level security.</span></span> <span data-ttu-id="cab64-138">Bu öğe türünde <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>.</span><span class="sxs-lookup"><span data-stu-id="cab64-138">This element is of type <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="cab64-139">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="cab64-139">Parent Elements</span></span>  
  
|<span data-ttu-id="cab64-140">Öğe</span><span class="sxs-lookup"><span data-stu-id="cab64-140">Element</span></span>|<span data-ttu-id="cab64-141">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cab64-141">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cab64-142">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="cab64-142">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="cab64-143">Tüm bağlama yeteneklerini tanımlar [ \<wsDualHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="cab64-143">Defines all binding capabilities of the [\<wsDualHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cab64-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cab64-144">See also</span></span>
- <xref:System.ServiceModel.WSFederationHttpSecurity>
- <xref:System.ServiceModel.WSFederationHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WSFederationHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>
- [<span data-ttu-id="cab64-145">Nasıl yapılır: WSFederationHttpBinding oluşturma</span><span class="sxs-lookup"><span data-stu-id="cab64-145">How to: Create a WSFederationHttpBinding</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)
- [<span data-ttu-id="cab64-146">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="cab64-146">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="cab64-147">Kimlik Bilgisi Türü Seçme</span><span class="sxs-lookup"><span data-stu-id="cab64-147">Selecting a Credential Type</span></span>](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="cab64-148">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="cab64-148">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="cab64-149">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="cab64-149">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="cab64-150">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="cab64-150">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="cab64-151">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="cab64-151">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
