---
title: '&lt;netMsmqBinding&gt; &lt;güvenliği&gt;'
ms.date: 03/30/2017
ms.assetid: 001d11a9-7439-498c-b09d-fca20eaf8cd3
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: c525344b18322cef05f64e46c75cdab7b271561a
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44205938"
---
# <a name="ltsecuritygt-of-ltnetmsmqbindinggt"></a><span data-ttu-id="525b5-102">&lt;netMsmqBinding&gt; &lt;güvenliği&gt;</span><span class="sxs-lookup"><span data-stu-id="525b5-102">&lt;security&gt; of &lt;netMsmqBinding&gt;</span></span>
<span data-ttu-id="525b5-103">MSMQ bağlama için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="525b5-103">Defines the security settings for a MSMQ binding.</span></span> <span data-ttu-id="525b5-104">Bu aktarım veya SOAP Güvenliği etkinleştirilmiş ve bu durumda, hangi kimlik doğrulama modu ve koruma düzeyleri kullanımda olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="525b5-104">It specifies whether transport or SOAP security is enabled and, if so, what authentication mode and protection levels are in use.</span></span>  
  
 <span data-ttu-id="525b5-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="525b5-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="525b5-106">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="525b5-106">\<bindings></span></span>  
<span data-ttu-id="525b5-107">\<netMsmqBinding ></span><span class="sxs-lookup"><span data-stu-id="525b5-107">\<netMsmqBinding></span></span>  
<span data-ttu-id="525b5-108">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="525b5-108">\<binding></span></span>  
<span data-ttu-id="525b5-109">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="525b5-109">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="525b5-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="525b5-110">Syntax</span></span>  
  
```xml  
<security mode="None/Transport/Message/Both">  
   <transport msmqAuthenticationMode="None/WindowsDomain/Certificate"  
      msmqEncryptionAlgorithm="RC4Stream/AES"  
      msmqProtectionLevel="None/Sign/EncryptAndSign"  
      msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />  
      <message  
      algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
      clientCredentialType="None/Windows/UserName/Certificate/CardSpace"/>  
</security>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="525b5-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="525b5-111">Attributes and Elements</span></span>  
 <span data-ttu-id="525b5-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="525b5-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="525b5-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="525b5-113">Attributes</span></span>  
  
|<span data-ttu-id="525b5-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="525b5-114">Attribute</span></span>|<span data-ttu-id="525b5-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="525b5-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="525b5-116">mod</span><span class="sxs-lookup"><span data-stu-id="525b5-116">mode</span></span>|<span data-ttu-id="525b5-117">Bütünlüğü, gizlilik ve kimlik doğrulama denetimleri güvenlik türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="525b5-117">Specifies the type of security that controls integrity, confidentiality and authentication.</span></span> <span data-ttu-id="525b5-118">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="525b5-118">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="525b5-119">-Yok: Bu güvenlik devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="525b5-119">-   None: This disables security.</span></span><br /><span data-ttu-id="525b5-120">-Taşıma: Koruma ve kimlik doğrulaması taşıma tarafından sunulur.</span><span class="sxs-lookup"><span data-stu-id="525b5-120">-   Transport: Protection and authentication are offered by the transport.</span></span> <span data-ttu-id="525b5-121">Bu ileti güvenliği iki sıra yöneticileri arasında geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="525b5-121">This applies to the message security between the two queue managers.</span></span> <span data-ttu-id="525b5-122">Kuyruk Yöneticisi ve uygulama arasında sunulan güvenlik yoktur.</span><span class="sxs-lookup"><span data-stu-id="525b5-122">There is no security offered between the application and queue manager.</span></span> <span data-ttu-id="525b5-123">Msmq uygulamalara güvenlik modu bu tür işlevsel olarak eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="525b5-123">Existing Msmq applications are functionally equivalent with this type of security mode.</span></span><br /><span data-ttu-id="525b5-124">-İleti: uçtan uca uygulama güvenliği belirtir.</span><span class="sxs-lookup"><span data-stu-id="525b5-124">-   Message: Specifies end-end application security.</span></span> <span data-ttu-id="525b5-125">Aktarım katmanında sunulan güvenlik yoktur.</span><span class="sxs-lookup"><span data-stu-id="525b5-125">There is no security offered at the transport layer.</span></span> <span data-ttu-id="525b5-126">Bu, standart diğer bağlamalar tarafından sunulan güvenlik benzer.</span><span class="sxs-lookup"><span data-stu-id="525b5-126">This is similar to the security offered by other standard bindings.</span></span><br /><span data-ttu-id="525b5-127">-Hem: hem aktarım hem de Katman Mesajlaşma SOAP güvenlik sunar.</span><span class="sxs-lookup"><span data-stu-id="525b5-127">-   Both: Offers security at both the transport and SOAP messaging layer.</span></span> <span data-ttu-id="525b5-128">Aynı kimlik bilgisini iki düzeyde gereklidir.</span><span class="sxs-lookup"><span data-stu-id="525b5-128">The same credential is required at both the levels.</span></span><br /><br /> <span data-ttu-id="525b5-129">Aktarım varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="525b5-129">The default value is Transport.</span></span> <span data-ttu-id="525b5-130">Bu öznitelik türünde <xref:System.ServiceModel.NetMsmqSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="525b5-130">This attribute is of type <xref:System.ServiceModel.NetMsmqSecurityMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="525b5-131">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="525b5-131">Child Elements</span></span>  
  
|<span data-ttu-id="525b5-132">Öğe</span><span class="sxs-lookup"><span data-stu-id="525b5-132">Element</span></span>|<span data-ttu-id="525b5-133">Açıklama</span><span class="sxs-lookup"><span data-stu-id="525b5-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="525b5-134">\<İleti ></span><span class="sxs-lookup"><span data-stu-id="525b5-134">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-of-netmsmqbinding.md)|<span data-ttu-id="525b5-135">SOAP ileti güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="525b5-135">Defines the SOAP message security settings.</span></span> <span data-ttu-id="525b5-136">Bu öğe türünde <xref:System.ServiceModel.Configuration.MessageSecurityOverMsmqElement>.</span><span class="sxs-lookup"><span data-stu-id="525b5-136">This element is of type <xref:System.ServiceModel.Configuration.MessageSecurityOverMsmqElement>.</span></span>|  
|[<span data-ttu-id="525b5-137">\<taşıma ></span><span class="sxs-lookup"><span data-stu-id="525b5-137">\<transport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-netmsmqbinding.md)|<span data-ttu-id="525b5-138">MSMQ taşıma güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="525b5-138">Defines the security settings for the MSMQ transport.</span></span> <span data-ttu-id="525b5-139">Bu öğe türünde <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="525b5-139">This element is of type <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="525b5-140">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="525b5-140">Parent Elements</span></span>  
  
|<span data-ttu-id="525b5-141">Öğe</span><span class="sxs-lookup"><span data-stu-id="525b5-141">Element</span></span>|<span data-ttu-id="525b5-142">Açıklama</span><span class="sxs-lookup"><span data-stu-id="525b5-142">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="525b5-143">bağlama</span><span class="sxs-lookup"><span data-stu-id="525b5-143">binding</span></span>|<span data-ttu-id="525b5-144">Bağlama öğesi [ \<netMsmqBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netmsmqbinding.md)</span><span class="sxs-lookup"><span data-stu-id="525b5-144">The binding element of the [\<netMsmqBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netmsmqbinding.md)</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="525b5-145">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="525b5-145">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement>  
 <xref:System.ServiceModel.NetMsmqBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.NetMsmqBindingElement.Security%2A>  
 <xref:System.ServiceModel.NetMsmqSecurity>  
 [<span data-ttu-id="525b5-146">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="525b5-146">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="525b5-147">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="525b5-147">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="525b5-148">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="525b5-148">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="525b5-149">Windows Communication Foundation Hizmetleri ve istemcileri yapılandırmak için bağlamaları kullanma</span><span class="sxs-lookup"><span data-stu-id="525b5-149">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](https://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="525b5-150">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="525b5-150">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)  
 [<span data-ttu-id="525b5-151">WCF'de Kuyruklar</span><span class="sxs-lookup"><span data-stu-id="525b5-151">Queues in WCF</span></span>](../../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)
