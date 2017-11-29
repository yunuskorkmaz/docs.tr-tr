---
title: '&lt;windowsStreamSecurity&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 926bea29-90c7-4a26-9cf0-fb4aa44f6f70
caps.latest.revision: "10"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 5a0d3b61f473b49abdb2470a9fa5381dc9929274
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltwindowsstreamsecuritygt"></a><span data-ttu-id="cbe67-102">&lt;windowsStreamSecurity&gt;</span><span class="sxs-lookup"><span data-stu-id="cbe67-102">&lt;windowsStreamSecurity&gt;</span></span>
<span data-ttu-id="cbe67-103">Özel bağlama Windows akış güvenlik ayarlarını belirtin.</span><span class="sxs-lookup"><span data-stu-id="cbe67-103">Specify Windows stream security settings of the custom binding.</span></span>  
  
 <span data-ttu-id="cbe67-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="cbe67-104">\<system.serviceModel></span></span>  
<span data-ttu-id="cbe67-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="cbe67-105">\<bindings></span></span>  
<span data-ttu-id="cbe67-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="cbe67-106">\<customBinding></span></span>  
<span data-ttu-id="cbe67-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="cbe67-107">\<binding></span></span>  
<span data-ttu-id="cbe67-108">\<windowsStreamSecurity ></span><span class="sxs-lookup"><span data-stu-id="cbe67-108">\<windowsStreamSecurity></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cbe67-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cbe67-109">Syntax</span></span>  
  
```xml  
<windowsStreamSecurity protectionLevel="None/Sign/EncryptAndSign"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cbe67-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="cbe67-110">Attributes and Elements</span></span>  
 <span data-ttu-id="cbe67-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="cbe67-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cbe67-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="cbe67-112">Attributes</span></span>  
  
|<span data-ttu-id="cbe67-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="cbe67-113">Attribute</span></span>|<span data-ttu-id="cbe67-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cbe67-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="cbe67-115">ProtectionLevel</span><span class="sxs-lookup"><span data-stu-id="cbe67-115">protectionLevel</span></span>|<span data-ttu-id="cbe67-116">İleti düzeyi güvenlik tanımlar.</span><span class="sxs-lookup"><span data-stu-id="cbe67-116">Defines message-level security.</span></span> <span data-ttu-id="cbe67-117">İletileri imzalama bir üçüncü taraf onu aktarılırken iletiyle oynama riskini azaltır.</span><span class="sxs-lookup"><span data-stu-id="cbe67-117">Signing messages mitigates the risk of a third party tampering with the message while it is being transferred.</span></span> <span data-ttu-id="cbe67-118">Şifreleme, aktarım sırasında veri düzeyi gizliliği sağlar.</span><span class="sxs-lookup"><span data-stu-id="cbe67-118">Encryption provides data-level privacy during transport.</span></span> <span data-ttu-id="cbe67-119">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="cbe67-119">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="cbe67-120">-Hiçbiri: Koruma yok.</span><span class="sxs-lookup"><span data-stu-id="cbe67-120">-   None: No protection.</span></span><br /><span data-ttu-id="cbe67-121">-Oturum: İletileri imzalanmıştır.</span><span class="sxs-lookup"><span data-stu-id="cbe67-121">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="cbe67-122">-Da EncryptAndSign: İletileri imzalanmış ve şifrelenmiş.</span><span class="sxs-lookup"><span data-stu-id="cbe67-122">-   EncryptAndSign: Messages are signed and encrypted.</span></span><br /><br /> <span data-ttu-id="cbe67-123">Da EncryptAndSign varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="cbe67-123">The default is EncryptAndSign.</span></span><br /><br /> <span data-ttu-id="cbe67-124">Bu öznitelik türünde <xref:System.Net.Security.ProtectionLevel>.</span><span class="sxs-lookup"><span data-stu-id="cbe67-124">This attribute is of type <xref:System.Net.Security.ProtectionLevel>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cbe67-125">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="cbe67-125">Child Elements</span></span>  
 <span data-ttu-id="cbe67-126">Yok.</span><span class="sxs-lookup"><span data-stu-id="cbe67-126">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="cbe67-127">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="cbe67-127">Parent Elements</span></span>  
  
|<span data-ttu-id="cbe67-128">Öğe</span><span class="sxs-lookup"><span data-stu-id="cbe67-128">Element</span></span>|<span data-ttu-id="cbe67-129">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cbe67-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cbe67-130">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="cbe67-130">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="cbe67-131">Özel bağlama tüm bağlama özelliklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="cbe67-131">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cbe67-132">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cbe67-132">Remarks</span></span>  
 <span data-ttu-id="cbe67-133">Adlandırılmış Kanallar ve akış odaklı bir protokol TCP gibi kullanan taşımaları aktarım akışı tabanlı yükseltmeyi destekler.</span><span class="sxs-lookup"><span data-stu-id="cbe67-133">Transports that use a stream-oriented protocol such as TCP and named pipes support stream-based transport upgrades.</span></span> <span data-ttu-id="cbe67-134">Özellikle, WCF güvenlik yükseltmeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="cbe67-134">Specifically, WCF provides security upgrades.</span></span> <span data-ttu-id="cbe67-135">Bu taşıma güvenliği yapılandırma bu yapılandırma öğesi tarafından yanı kapsüllenir [ \<sslStreamSecurity >](../../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md), hangi yapılandırılabilir ve özel bağlama için eklenen</span><span class="sxs-lookup"><span data-stu-id="cbe67-135">The configuration of this transport security is encapsulated by this configuration element  as well as by [\<sslStreamSecurity>](../../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md), which can be configured and added to a custom binding</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cbe67-136">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="cbe67-136">See Also</span></span>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 <xref:System.ServiceModel.Configuration.WindowsStreamSecurityElement>  
 <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>  
 [<span data-ttu-id="cbe67-137">Bağlamaları</span><span class="sxs-lookup"><span data-stu-id="cbe67-137">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="cbe67-138">Bağlamaları genişletme</span><span class="sxs-lookup"><span data-stu-id="cbe67-138">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="cbe67-139">Özel bağlamalar</span><span class="sxs-lookup"><span data-stu-id="cbe67-139">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="cbe67-140">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="cbe67-140">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
