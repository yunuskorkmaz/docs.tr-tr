---
title: '&lt;netNamedPipeBinding&gt; &lt;taşıma&gt;'
ms.date: 03/30/2017
ms.assetid: d9eff52d-4bde-4586-b56a-b0ec24611f8d
ms.openlocfilehash: 9116532c8b4aae2f7539706b97d564444195c79d
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32753150"
---
# <a name="lttransportgt-of-ltnetnamedpipebindinggt"></a><span data-ttu-id="aaaf8-102">&lt;netNamedPipeBinding&gt; &lt;taşıma&gt;</span><span class="sxs-lookup"><span data-stu-id="aaaf8-102">&lt;transport&gt; of &lt;netNamedPipeBinding&gt;</span></span>
<span data-ttu-id="aaaf8-103">Bir adlandırılmış kanal taşıma güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="aaaf8-103">Defines the transport security settings for a named pipe.</span></span>  
  
 <span data-ttu-id="aaaf8-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="aaaf8-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="aaaf8-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="aaaf8-105">\<bindings></span></span>  
<span data-ttu-id="aaaf8-106">\<netNamedPipeBinding></span><span class="sxs-lookup"><span data-stu-id="aaaf8-106">\<netNamedPipeBinding></span></span>  
<span data-ttu-id="aaaf8-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="aaaf8-107">\<binding></span></span>  
<span data-ttu-id="aaaf8-108">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="aaaf8-108">\<security></span></span>  
<span data-ttu-id="aaaf8-109">\<taşıma ></span><span class="sxs-lookup"><span data-stu-id="aaaf8-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aaaf8-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="aaaf8-110">Syntax</span></span>  
  
```xml  
<netNamedPipeBinding>  
   <binding>  
      <security mode="None/Transport">  
            <transport protectionLevel="None/Sign/EncryptAndSign" />  
      </security>  
   </binding>  
</netNamedPipeBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="aaaf8-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="aaaf8-111">Attributes and Elements</span></span>  
 <span data-ttu-id="aaaf8-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="aaaf8-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="aaaf8-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="aaaf8-113">Attributes</span></span>  
  
|<span data-ttu-id="aaaf8-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="aaaf8-114">Attribute</span></span>|<span data-ttu-id="aaaf8-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="aaaf8-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="aaaf8-116">ProtectionLevel</span><span class="sxs-lookup"><span data-stu-id="aaaf8-116">protectionLevel</span></span>|<span data-ttu-id="aaaf8-117">Adlandırılmış kanal koruma düzeyini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="aaaf8-117">Defines protection level of the named pipe.</span></span> <span data-ttu-id="aaaf8-118">İletileri imzalama bir üçüncü taraf onu aktarılırken iletiyle oynama riskini azaltır.</span><span class="sxs-lookup"><span data-stu-id="aaaf8-118">Signing messages mitigates the risk of a third party tampering with the message while it is being transferred.</span></span> <span data-ttu-id="aaaf8-119">Şifreleme, aktarım sırasında veri düzeyi gizliliği sağlar.</span><span class="sxs-lookup"><span data-stu-id="aaaf8-119">Encryption provides data-level privacy during transport.</span></span> <span data-ttu-id="aaaf8-120">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="aaaf8-120">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="aaaf8-121">-Hiçbiri: Koruma yok.</span><span class="sxs-lookup"><span data-stu-id="aaaf8-121">-   None: No protection.</span></span><br /><span data-ttu-id="aaaf8-122">-Oturum: İletileri imzalanmıştır.</span><span class="sxs-lookup"><span data-stu-id="aaaf8-122">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="aaaf8-123">-Da EncryptAndSign: İletileri şifrelenmiş ve imzalanmış.</span><span class="sxs-lookup"><span data-stu-id="aaaf8-123">-   EncryptAndSign: Messages are encrypted and signed.</span></span><br /><br /> <span data-ttu-id="aaaf8-124">Da EncryptAndSign varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="aaaf8-124">The default value is EncryptAndSign.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="aaaf8-125">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="aaaf8-125">Child Elements</span></span>  
 <span data-ttu-id="aaaf8-126">Yok.</span><span class="sxs-lookup"><span data-stu-id="aaaf8-126">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="aaaf8-127">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="aaaf8-127">Parent Elements</span></span>  
  
|<span data-ttu-id="aaaf8-128">Öğe</span><span class="sxs-lookup"><span data-stu-id="aaaf8-128">Element</span></span>|<span data-ttu-id="aaaf8-129">Açıklama</span><span class="sxs-lookup"><span data-stu-id="aaaf8-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="aaaf8-130">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="aaaf8-130">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netnamedpipebinding.md)|<span data-ttu-id="aaaf8-131">Bağlama için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="aaaf8-131">Defines the security settings for a binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="aaaf8-132">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="aaaf8-132">See Also</span></span>  
 <xref:System.ServiceModel.NamedPipeTransportSecurity>  
 <xref:System.ServiceModel.Configuration.NetNamedPipeSecurityElement.Transport%2A>  
 <xref:System.ServiceModel.NetNamedPipeSecurity.Transport%2A>  
 <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>  
 [<span data-ttu-id="aaaf8-133">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="aaaf8-133">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="aaaf8-134">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="aaaf8-134">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="aaaf8-135">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="aaaf8-135">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="aaaf8-136">Windows Communication Foundation Hizmetleri ve istemcileri yapılandırmak için bağlamaları kullanma</span><span class="sxs-lookup"><span data-stu-id="aaaf8-136">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="aaaf8-137">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="aaaf8-137">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
