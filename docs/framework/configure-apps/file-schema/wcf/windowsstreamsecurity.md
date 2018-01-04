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
ms.workload: dotnet
ms.openlocfilehash: 3ebbb7749a5ca24072e62bb482ee33abadcfb8b8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltwindowsstreamsecuritygt"></a><span data-ttu-id="fe0f2-102">&lt;windowsStreamSecurity&gt;</span><span class="sxs-lookup"><span data-stu-id="fe0f2-102">&lt;windowsStreamSecurity&gt;</span></span>
<span data-ttu-id="fe0f2-103">Özel bağlama Windows akış güvenlik ayarlarını belirtin.</span><span class="sxs-lookup"><span data-stu-id="fe0f2-103">Specify Windows stream security settings of the custom binding.</span></span>  
  
 <span data-ttu-id="fe0f2-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="fe0f2-104">\<system.serviceModel></span></span>  
<span data-ttu-id="fe0f2-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="fe0f2-105">\<bindings></span></span>  
<span data-ttu-id="fe0f2-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="fe0f2-106">\<customBinding></span></span>  
<span data-ttu-id="fe0f2-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="fe0f2-107">\<binding></span></span>  
<span data-ttu-id="fe0f2-108">\<windowsStreamSecurity ></span><span class="sxs-lookup"><span data-stu-id="fe0f2-108">\<windowsStreamSecurity></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe0f2-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fe0f2-109">Syntax</span></span>  
  
```xml  
<windowsStreamSecurity protectionLevel="None/Sign/EncryptAndSign"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fe0f2-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="fe0f2-110">Attributes and Elements</span></span>  
 <span data-ttu-id="fe0f2-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="fe0f2-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fe0f2-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="fe0f2-112">Attributes</span></span>  
  
|<span data-ttu-id="fe0f2-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="fe0f2-113">Attribute</span></span>|<span data-ttu-id="fe0f2-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fe0f2-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="fe0f2-115">ProtectionLevel</span><span class="sxs-lookup"><span data-stu-id="fe0f2-115">protectionLevel</span></span>|<span data-ttu-id="fe0f2-116">İleti düzeyi güvenlik tanımlar.</span><span class="sxs-lookup"><span data-stu-id="fe0f2-116">Defines message-level security.</span></span> <span data-ttu-id="fe0f2-117">İletileri imzalama bir üçüncü taraf onu aktarılırken iletiyle oynama riskini azaltır.</span><span class="sxs-lookup"><span data-stu-id="fe0f2-117">Signing messages mitigates the risk of a third party tampering with the message while it is being transferred.</span></span> <span data-ttu-id="fe0f2-118">Şifreleme, aktarım sırasında veri düzeyi gizliliği sağlar.</span><span class="sxs-lookup"><span data-stu-id="fe0f2-118">Encryption provides data-level privacy during transport.</span></span> <span data-ttu-id="fe0f2-119">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="fe0f2-119">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="fe0f2-120">-Hiçbiri: Koruma yok.</span><span class="sxs-lookup"><span data-stu-id="fe0f2-120">-   None: No protection.</span></span><br /><span data-ttu-id="fe0f2-121">-Oturum: İletileri imzalanmıştır.</span><span class="sxs-lookup"><span data-stu-id="fe0f2-121">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="fe0f2-122">-Da EncryptAndSign: İletileri imzalanmış ve şifrelenmiş.</span><span class="sxs-lookup"><span data-stu-id="fe0f2-122">-   EncryptAndSign: Messages are signed and encrypted.</span></span><br /><br /> <span data-ttu-id="fe0f2-123">Da EncryptAndSign varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="fe0f2-123">The default is EncryptAndSign.</span></span><br /><br /> <span data-ttu-id="fe0f2-124">Bu öznitelik türünde <xref:System.Net.Security.ProtectionLevel>.</span><span class="sxs-lookup"><span data-stu-id="fe0f2-124">This attribute is of type <xref:System.Net.Security.ProtectionLevel>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fe0f2-125">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="fe0f2-125">Child Elements</span></span>  
 <span data-ttu-id="fe0f2-126">Yok.</span><span class="sxs-lookup"><span data-stu-id="fe0f2-126">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fe0f2-127">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="fe0f2-127">Parent Elements</span></span>  
  
|<span data-ttu-id="fe0f2-128">Öğe</span><span class="sxs-lookup"><span data-stu-id="fe0f2-128">Element</span></span>|<span data-ttu-id="fe0f2-129">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fe0f2-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fe0f2-130">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="fe0f2-130">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="fe0f2-131">Özel bağlama tüm bağlama özelliklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="fe0f2-131">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fe0f2-132">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fe0f2-132">Remarks</span></span>  
 <span data-ttu-id="fe0f2-133">Adlandırılmış Kanallar ve akış odaklı bir protokol TCP gibi kullanan taşımaları aktarım akışı tabanlı yükseltmeyi destekler.</span><span class="sxs-lookup"><span data-stu-id="fe0f2-133">Transports that use a stream-oriented protocol such as TCP and named pipes support stream-based transport upgrades.</span></span> <span data-ttu-id="fe0f2-134">Özellikle, WCF güvenlik yükseltmeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="fe0f2-134">Specifically, WCF provides security upgrades.</span></span> <span data-ttu-id="fe0f2-135">Bu taşıma güvenliği yapılandırma bu yapılandırma öğesi tarafından yanı kapsüllenir [ \<sslStreamSecurity >](../../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md), hangi yapılandırılabilir ve özel bağlama için eklenen</span><span class="sxs-lookup"><span data-stu-id="fe0f2-135">The configuration of this transport security is encapsulated by this configuration element  as well as by [\<sslStreamSecurity>](../../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md), which can be configured and added to a custom binding</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe0f2-136">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fe0f2-136">See Also</span></span>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 <xref:System.ServiceModel.Configuration.WindowsStreamSecurityElement>  
 <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>  
 [<span data-ttu-id="fe0f2-137">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="fe0f2-137">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="fe0f2-138">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="fe0f2-138">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="fe0f2-139">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="fe0f2-139">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="fe0f2-140">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="fe0f2-140">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
