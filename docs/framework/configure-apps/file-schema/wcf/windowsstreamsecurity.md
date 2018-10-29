---
title: '&lt;windowsStreamSecurity&gt;'
ms.date: 03/30/2017
ms.assetid: 926bea29-90c7-4a26-9cf0-fb4aa44f6f70
ms.openlocfilehash: e117c30ba2583158ee21fd11ff4a38b094c18fd9
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/28/2018
ms.locfileid: "50197645"
---
# <a name="ltwindowsstreamsecuritygt"></a><span data-ttu-id="952f3-102">&lt;windowsStreamSecurity&gt;</span><span class="sxs-lookup"><span data-stu-id="952f3-102">&lt;windowsStreamSecurity&gt;</span></span>
<span data-ttu-id="952f3-103">Özel bağlamanın Windows akış güvenliği ayarlarını belirtin.</span><span class="sxs-lookup"><span data-stu-id="952f3-103">Specify Windows stream security settings of the custom binding.</span></span>  
  
 <span data-ttu-id="952f3-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="952f3-104">\<system.serviceModel></span></span>  
<span data-ttu-id="952f3-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="952f3-105">\<bindings></span></span>  
<span data-ttu-id="952f3-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="952f3-106">\<customBinding></span></span>  
<span data-ttu-id="952f3-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="952f3-107">\<binding></span></span>  
<span data-ttu-id="952f3-108">\<windowsStreamSecurity ></span><span class="sxs-lookup"><span data-stu-id="952f3-108">\<windowsStreamSecurity></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="952f3-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="952f3-109">Syntax</span></span>  
  
```xml  
<windowsStreamSecurity protectionLevel="None/Sign/EncryptAndSign"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="952f3-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="952f3-110">Attributes and Elements</span></span>  
 <span data-ttu-id="952f3-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="952f3-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="952f3-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="952f3-112">Attributes</span></span>  
  
|<span data-ttu-id="952f3-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="952f3-113">Attribute</span></span>|<span data-ttu-id="952f3-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="952f3-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="952f3-115">protectionLevel</span><span class="sxs-lookup"><span data-stu-id="952f3-115">protectionLevel</span></span>|<span data-ttu-id="952f3-116">İleti düzeyi güvenliği tanımlar.</span><span class="sxs-lookup"><span data-stu-id="952f3-116">Defines message-level security.</span></span> <span data-ttu-id="952f3-117">İleti imzalama, bir üçüncü taraf aktarılırken iletinin oynama riskini azaltır.</span><span class="sxs-lookup"><span data-stu-id="952f3-117">Signing messages mitigates the risk of a third party tampering with the message while it is being transferred.</span></span> <span data-ttu-id="952f3-118">Şifreleme, aktarım sırasında verileri düzeyinde gizlilik sağlar.</span><span class="sxs-lookup"><span data-stu-id="952f3-118">Encryption provides data-level privacy during transport.</span></span> <span data-ttu-id="952f3-119">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="952f3-119">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="952f3-120">-Hiçbiri: Koruma yok.</span><span class="sxs-lookup"><span data-stu-id="952f3-120">-   None: No protection.</span></span><br /><span data-ttu-id="952f3-121">-Oturum: İletileri imzalanmıştır.</span><span class="sxs-lookup"><span data-stu-id="952f3-121">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="952f3-122">-EncryptAndSign: İletileri imzalanmış ve şifrelenmiş.</span><span class="sxs-lookup"><span data-stu-id="952f3-122">-   EncryptAndSign: Messages are signed and encrypted.</span></span><br /><br /> <span data-ttu-id="952f3-123">EncryptAndSign varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="952f3-123">The default is EncryptAndSign.</span></span><br /><br /> <span data-ttu-id="952f3-124">Bu öznitelik türünde <xref:System.Net.Security.ProtectionLevel>.</span><span class="sxs-lookup"><span data-stu-id="952f3-124">This attribute is of type <xref:System.Net.Security.ProtectionLevel>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="952f3-125">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="952f3-125">Child Elements</span></span>  
 <span data-ttu-id="952f3-126">Yok.</span><span class="sxs-lookup"><span data-stu-id="952f3-126">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="952f3-127">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="952f3-127">Parent Elements</span></span>  
  
|<span data-ttu-id="952f3-128">Öğe</span><span class="sxs-lookup"><span data-stu-id="952f3-128">Element</span></span>|<span data-ttu-id="952f3-129">Açıklama</span><span class="sxs-lookup"><span data-stu-id="952f3-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="952f3-130">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="952f3-130">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="952f3-131">Özel bağlama tüm bağlama yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="952f3-131">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="952f3-132">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="952f3-132">Remarks</span></span>  
 <span data-ttu-id="952f3-133">Bir akışa dayalı Protokolü gibi TCP ve adlandırılmış kanallar taşımalar aktarım akışı tabanlı yükseltmeyi destekler.</span><span class="sxs-lookup"><span data-stu-id="952f3-133">Transports that use a stream-oriented protocol such as TCP and named pipes support stream-based transport upgrades.</span></span> <span data-ttu-id="952f3-134">Özellikle, WCF güvenlik yükseltmeleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="952f3-134">Specifically, WCF provides security upgrades.</span></span> <span data-ttu-id="952f3-135">Bu aktarım güvenliği yapılandırma bu yapılandırma öğesi tarafından yanı kapsüllenir [ \<sslStreamSecurity >](../../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md), hangi yapılandırılabilir ve özel bağlama için eklendi</span><span class="sxs-lookup"><span data-stu-id="952f3-135">The configuration of this transport security is encapsulated by this configuration element  as well as by [\<sslStreamSecurity>](../../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md), which can be configured and added to a custom binding</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="952f3-136">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="952f3-136">See Also</span></span>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 <xref:System.ServiceModel.Configuration.WindowsStreamSecurityElement>  
 <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>  
 [<span data-ttu-id="952f3-137">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="952f3-137">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="952f3-138">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="952f3-138">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="952f3-139">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="952f3-139">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="952f3-140">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="952f3-140">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
