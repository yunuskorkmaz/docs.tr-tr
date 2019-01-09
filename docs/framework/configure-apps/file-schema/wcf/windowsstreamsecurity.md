---
title: '&lt;windowsStreamSecurity&gt;'
ms.date: 03/30/2017
ms.assetid: 926bea29-90c7-4a26-9cf0-fb4aa44f6f70
ms.openlocfilehash: 6cce178910767d7fd197aff0d007b7cc3f4e60f3
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54151130"
---
# <a name="ltwindowsstreamsecuritygt"></a><span data-ttu-id="59206-102">&lt;windowsStreamSecurity&gt;</span><span class="sxs-lookup"><span data-stu-id="59206-102">&lt;windowsStreamSecurity&gt;</span></span>
<span data-ttu-id="59206-103">Özel bağlamanın Windows akış güvenliği ayarlarını belirtin.</span><span class="sxs-lookup"><span data-stu-id="59206-103">Specify Windows stream security settings of the custom binding.</span></span>  
  
 <span data-ttu-id="59206-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="59206-104">\<system.serviceModel></span></span>  
<span data-ttu-id="59206-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="59206-105">\<bindings></span></span>  
<span data-ttu-id="59206-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="59206-106">\<customBinding></span></span>  
<span data-ttu-id="59206-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="59206-107">\<binding></span></span>  
<span data-ttu-id="59206-108">\<windowsStreamSecurity ></span><span class="sxs-lookup"><span data-stu-id="59206-108">\<windowsStreamSecurity></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59206-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="59206-109">Syntax</span></span>  
  
```xml  
<windowsStreamSecurity protectionLevel="None/Sign/EncryptAndSign" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="59206-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="59206-110">Attributes and Elements</span></span>  
 <span data-ttu-id="59206-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="59206-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="59206-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="59206-112">Attributes</span></span>  
  
|<span data-ttu-id="59206-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="59206-113">Attribute</span></span>|<span data-ttu-id="59206-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="59206-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="59206-115">protectionLevel</span><span class="sxs-lookup"><span data-stu-id="59206-115">protectionLevel</span></span>|<span data-ttu-id="59206-116">İleti düzeyi güvenliği tanımlar.</span><span class="sxs-lookup"><span data-stu-id="59206-116">Defines message-level security.</span></span> <span data-ttu-id="59206-117">İleti imzalama, bir üçüncü taraf aktarılırken iletinin oynama riskini azaltır.</span><span class="sxs-lookup"><span data-stu-id="59206-117">Signing messages mitigates the risk of a third party tampering with the message while it is being transferred.</span></span> <span data-ttu-id="59206-118">Şifreleme, aktarım sırasında verileri düzeyinde gizlilik sağlar.</span><span class="sxs-lookup"><span data-stu-id="59206-118">Encryption provides data-level privacy during transport.</span></span> <span data-ttu-id="59206-119">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="59206-119">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="59206-120">-Yok: Koruma yok.</span><span class="sxs-lookup"><span data-stu-id="59206-120">-   None: No protection.</span></span><br /><span data-ttu-id="59206-121">-Oturum: İmzalı iletiler.</span><span class="sxs-lookup"><span data-stu-id="59206-121">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="59206-122">-EncryptAndSign: İletileri imzalanacak ve şifrelenecek.</span><span class="sxs-lookup"><span data-stu-id="59206-122">-   EncryptAndSign: Messages are signed and encrypted.</span></span><br /><br /> <span data-ttu-id="59206-123">EncryptAndSign varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="59206-123">The default is EncryptAndSign.</span></span><br /><br /> <span data-ttu-id="59206-124">Bu öznitelik türünde <xref:System.Net.Security.ProtectionLevel>.</span><span class="sxs-lookup"><span data-stu-id="59206-124">This attribute is of type <xref:System.Net.Security.ProtectionLevel>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="59206-125">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="59206-125">Child Elements</span></span>  
 <span data-ttu-id="59206-126">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="59206-126">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="59206-127">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="59206-127">Parent Elements</span></span>  
  
|<span data-ttu-id="59206-128">Öğe</span><span class="sxs-lookup"><span data-stu-id="59206-128">Element</span></span>|<span data-ttu-id="59206-129">Açıklama</span><span class="sxs-lookup"><span data-stu-id="59206-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="59206-130">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="59206-130">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="59206-131">Özel bağlama tüm bağlama yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="59206-131">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="59206-132">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="59206-132">Remarks</span></span>  
 <span data-ttu-id="59206-133">Bir akışa dayalı Protokolü gibi TCP ve adlandırılmış kanallar taşımalar aktarım akışı tabanlı yükseltmeyi destekler.</span><span class="sxs-lookup"><span data-stu-id="59206-133">Transports that use a stream-oriented protocol such as TCP and named pipes support stream-based transport upgrades.</span></span> <span data-ttu-id="59206-134">Özellikle, WCF güvenlik yükseltmeleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="59206-134">Specifically, WCF provides security upgrades.</span></span> <span data-ttu-id="59206-135">Bu aktarım güvenliği yapılandırma bu yapılandırma öğesi tarafından yanı kapsüllenir [ \<sslStreamSecurity >](../../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md), hangi yapılandırılabilir ve özel bağlama için eklendi</span><span class="sxs-lookup"><span data-stu-id="59206-135">The configuration of this transport security is encapsulated by this configuration element  as well as by [\<sslStreamSecurity>](../../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md), which can be configured and added to a custom binding</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59206-136">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="59206-136">See Also</span></span>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 <xref:System.ServiceModel.Configuration.WindowsStreamSecurityElement>  
 <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>  
 [<span data-ttu-id="59206-137">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="59206-137">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="59206-138">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="59206-138">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="59206-139">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="59206-139">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="59206-140">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="59206-140">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
