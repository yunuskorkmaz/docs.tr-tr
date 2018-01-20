---
title: "&lt;netNamedPipeBinding&gt; &lt;taşıma&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d9eff52d-4bde-4586-b56a-b0ec24611f8d
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 84811c70f2f3608c10d8886900169f804a8c9b62
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="lttransportgt-of-ltnetnamedpipebindinggt"></a><span data-ttu-id="e996e-102">&lt;netNamedPipeBinding&gt; &lt;taşıma&gt;</span><span class="sxs-lookup"><span data-stu-id="e996e-102">&lt;transport&gt; of &lt;netNamedPipeBinding&gt;</span></span>
<span data-ttu-id="e996e-103">Bir adlandırılmış kanal taşıma güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e996e-103">Defines the transport security settings for a named pipe.</span></span>  
  
 <span data-ttu-id="e996e-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="e996e-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="e996e-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="e996e-105">\<bindings></span></span>  
<span data-ttu-id="e996e-106">\<netNamedPipeBinding></span><span class="sxs-lookup"><span data-stu-id="e996e-106">\<netNamedPipeBinding></span></span>  
<span data-ttu-id="e996e-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="e996e-107">\<binding></span></span>  
<span data-ttu-id="e996e-108">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="e996e-108">\<security></span></span>  
<span data-ttu-id="e996e-109">\<taşıma ></span><span class="sxs-lookup"><span data-stu-id="e996e-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e996e-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e996e-110">Syntax</span></span>  
  
```xml  
<netNamedPipeBinding>  
   <binding>  
      <security mode="None/Transport">  
            <transport protectionLevel="None/Sign/EncryptAndSign" />  
      </security>  
   </binding>  
</netNamedPipeBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e996e-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="e996e-111">Attributes and Elements</span></span>  
 <span data-ttu-id="e996e-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e996e-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e996e-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e996e-113">Attributes</span></span>  
  
|<span data-ttu-id="e996e-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="e996e-114">Attribute</span></span>|<span data-ttu-id="e996e-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e996e-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e996e-116">protectionLevel</span><span class="sxs-lookup"><span data-stu-id="e996e-116">protectionLevel</span></span>|<span data-ttu-id="e996e-117">Adlandırılmış kanal koruma düzeyini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e996e-117">Defines protection level of the named pipe.</span></span> <span data-ttu-id="e996e-118">İletileri imzalama bir üçüncü taraf onu aktarılırken iletiyle oynama riskini azaltır.</span><span class="sxs-lookup"><span data-stu-id="e996e-118">Signing messages mitigates the risk of a third party tampering with the message while it is being transferred.</span></span> <span data-ttu-id="e996e-119">Şifreleme, aktarım sırasında veri düzeyi gizliliği sağlar.</span><span class="sxs-lookup"><span data-stu-id="e996e-119">Encryption provides data-level privacy during transport.</span></span> <span data-ttu-id="e996e-120">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="e996e-120">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="e996e-121">-Hiçbiri: Koruma yok.</span><span class="sxs-lookup"><span data-stu-id="e996e-121">-   None: No protection.</span></span><br /><span data-ttu-id="e996e-122">-Oturum: İletileri imzalanmıştır.</span><span class="sxs-lookup"><span data-stu-id="e996e-122">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="e996e-123">-Da EncryptAndSign: İletileri şifrelenmiş ve imzalanmış.</span><span class="sxs-lookup"><span data-stu-id="e996e-123">-   EncryptAndSign: Messages are encrypted and signed.</span></span><br /><br /> <span data-ttu-id="e996e-124">Da EncryptAndSign varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="e996e-124">The default value is EncryptAndSign.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e996e-125">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="e996e-125">Child Elements</span></span>  
 <span data-ttu-id="e996e-126">Yok.</span><span class="sxs-lookup"><span data-stu-id="e996e-126">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e996e-127">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="e996e-127">Parent Elements</span></span>  
  
|<span data-ttu-id="e996e-128">Öğe</span><span class="sxs-lookup"><span data-stu-id="e996e-128">Element</span></span>|<span data-ttu-id="e996e-129">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e996e-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e996e-130">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="e996e-130">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netnamedpipebinding.md)|<span data-ttu-id="e996e-131">Bağlama için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e996e-131">Defines the security settings for a binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e996e-132">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e996e-132">See Also</span></span>  
 <xref:System.ServiceModel.NamedPipeTransportSecurity>  
 <xref:System.ServiceModel.Configuration.NetNamedPipeSecurityElement.Transport%2A>  
 <xref:System.ServiceModel.NetNamedPipeSecurity.Transport%2A>  
 <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>  
 [<span data-ttu-id="e996e-133">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="e996e-133">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="e996e-134">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="e996e-134">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="e996e-135">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="e996e-135">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="e996e-136">Windows Communication Foundation Hizmetleri ve istemcileri yapılandırmak için bağlamaları kullanma</span><span class="sxs-lookup"><span data-stu-id="e996e-136">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="e996e-137">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="e996e-137">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
