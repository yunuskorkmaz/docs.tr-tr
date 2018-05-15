---
title: '&lt;windowsStreamSecurity&gt;'
ms.date: 03/30/2017
ms.assetid: 926bea29-90c7-4a26-9cf0-fb4aa44f6f70
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: a089a6fb61e8f7fac4116b2280a5c2fe0b703f94
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="ltwindowsstreamsecuritygt"></a><span data-ttu-id="b6836-102">&lt;windowsStreamSecurity&gt;</span><span class="sxs-lookup"><span data-stu-id="b6836-102">&lt;windowsStreamSecurity&gt;</span></span>
<span data-ttu-id="b6836-103">Özel bağlama Windows akış güvenlik ayarlarını belirtin.</span><span class="sxs-lookup"><span data-stu-id="b6836-103">Specify Windows stream security settings of the custom binding.</span></span>  
  
 <span data-ttu-id="b6836-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="b6836-104">\<system.serviceModel></span></span>  
<span data-ttu-id="b6836-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="b6836-105">\<bindings></span></span>  
<span data-ttu-id="b6836-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="b6836-106">\<customBinding></span></span>  
<span data-ttu-id="b6836-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="b6836-107">\<binding></span></span>  
<span data-ttu-id="b6836-108">\<windowsStreamSecurity ></span><span class="sxs-lookup"><span data-stu-id="b6836-108">\<windowsStreamSecurity></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6836-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b6836-109">Syntax</span></span>  
  
```xml  
<windowsStreamSecurity protectionLevel="None/Sign/EncryptAndSign"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b6836-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="b6836-110">Attributes and Elements</span></span>  
 <span data-ttu-id="b6836-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b6836-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b6836-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="b6836-112">Attributes</span></span>  
  
|<span data-ttu-id="b6836-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="b6836-113">Attribute</span></span>|<span data-ttu-id="b6836-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b6836-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b6836-115">ProtectionLevel</span><span class="sxs-lookup"><span data-stu-id="b6836-115">protectionLevel</span></span>|<span data-ttu-id="b6836-116">İleti düzeyi güvenlik tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b6836-116">Defines message-level security.</span></span> <span data-ttu-id="b6836-117">İletileri imzalama bir üçüncü taraf onu aktarılırken iletiyle oynama riskini azaltır.</span><span class="sxs-lookup"><span data-stu-id="b6836-117">Signing messages mitigates the risk of a third party tampering with the message while it is being transferred.</span></span> <span data-ttu-id="b6836-118">Şifreleme, aktarım sırasında veri düzeyi gizliliği sağlar.</span><span class="sxs-lookup"><span data-stu-id="b6836-118">Encryption provides data-level privacy during transport.</span></span> <span data-ttu-id="b6836-119">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="b6836-119">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="b6836-120">-Hiçbiri: Koruma yok.</span><span class="sxs-lookup"><span data-stu-id="b6836-120">-   None: No protection.</span></span><br /><span data-ttu-id="b6836-121">-Oturum: İletileri imzalanmıştır.</span><span class="sxs-lookup"><span data-stu-id="b6836-121">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="b6836-122">-Da EncryptAndSign: İletileri imzalanmış ve şifrelenmiş.</span><span class="sxs-lookup"><span data-stu-id="b6836-122">-   EncryptAndSign: Messages are signed and encrypted.</span></span><br /><br /> <span data-ttu-id="b6836-123">Da EncryptAndSign varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="b6836-123">The default is EncryptAndSign.</span></span><br /><br /> <span data-ttu-id="b6836-124">Bu öznitelik türünde <xref:System.Net.Security.ProtectionLevel>.</span><span class="sxs-lookup"><span data-stu-id="b6836-124">This attribute is of type <xref:System.Net.Security.ProtectionLevel>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b6836-125">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="b6836-125">Child Elements</span></span>  
 <span data-ttu-id="b6836-126">Yok.</span><span class="sxs-lookup"><span data-stu-id="b6836-126">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b6836-127">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="b6836-127">Parent Elements</span></span>  
  
|<span data-ttu-id="b6836-128">Öğe</span><span class="sxs-lookup"><span data-stu-id="b6836-128">Element</span></span>|<span data-ttu-id="b6836-129">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b6836-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b6836-130">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="b6836-130">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="b6836-131">Özel bağlama tüm bağlama özelliklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b6836-131">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b6836-132">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b6836-132">Remarks</span></span>  
 <span data-ttu-id="b6836-133">Adlandırılmış Kanallar ve akış odaklı bir protokol TCP gibi kullanan taşımaları aktarım akışı tabanlı yükseltmeyi destekler.</span><span class="sxs-lookup"><span data-stu-id="b6836-133">Transports that use a stream-oriented protocol such as TCP and named pipes support stream-based transport upgrades.</span></span> <span data-ttu-id="b6836-134">Özellikle, WCF güvenlik yükseltmeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="b6836-134">Specifically, WCF provides security upgrades.</span></span> <span data-ttu-id="b6836-135">Bu taşıma güvenliği yapılandırma bu yapılandırma öğesi tarafından yanı kapsüllenir [ \<sslStreamSecurity >](../../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md), hangi yapılandırılabilir ve özel bağlama için eklenen</span><span class="sxs-lookup"><span data-stu-id="b6836-135">The configuration of this transport security is encapsulated by this configuration element  as well as by [\<sslStreamSecurity>](../../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md), which can be configured and added to a custom binding</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6836-136">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b6836-136">See Also</span></span>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 <xref:System.ServiceModel.Configuration.WindowsStreamSecurityElement>  
 <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>  
 [<span data-ttu-id="b6836-137">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="b6836-137">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="b6836-138">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="b6836-138">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="b6836-139">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="b6836-139">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="b6836-140">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="b6836-140">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
