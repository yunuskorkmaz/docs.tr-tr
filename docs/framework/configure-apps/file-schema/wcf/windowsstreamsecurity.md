---
title: <windowsStreamSecurity>
ms.date: 03/30/2017
ms.assetid: 926bea29-90c7-4a26-9cf0-fb4aa44f6f70
ms.openlocfilehash: 32e8ed6b70a23462fac3c53d1bc353167ff67560
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59113639"
---
# <a name="windowsstreamsecurity"></a><span data-ttu-id="83a32-101">\<windowsStreamSecurity ></span><span class="sxs-lookup"><span data-stu-id="83a32-101">\<windowsStreamSecurity></span></span>
<span data-ttu-id="83a32-102">Özel bağlamanın Windows akış güvenliği ayarlarını belirtin.</span><span class="sxs-lookup"><span data-stu-id="83a32-102">Specify Windows stream security settings of the custom binding.</span></span>  
  
 <span data-ttu-id="83a32-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="83a32-103">\<system.serviceModel></span></span>  
<span data-ttu-id="83a32-104">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="83a32-104">\<bindings></span></span>  
<span data-ttu-id="83a32-105">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="83a32-105">\<customBinding></span></span>  
<span data-ttu-id="83a32-106">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="83a32-106">\<binding></span></span>  
<span data-ttu-id="83a32-107">\<windowsStreamSecurity ></span><span class="sxs-lookup"><span data-stu-id="83a32-107">\<windowsStreamSecurity></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83a32-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="83a32-108">Syntax</span></span>  
  
```xml  
<windowsStreamSecurity protectionLevel="None/Sign/EncryptAndSign" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="83a32-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="83a32-109">Attributes and Elements</span></span>  
 <span data-ttu-id="83a32-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="83a32-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="83a32-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="83a32-111">Attributes</span></span>  
  
|<span data-ttu-id="83a32-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="83a32-112">Attribute</span></span>|<span data-ttu-id="83a32-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="83a32-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="83a32-114">protectionLevel</span><span class="sxs-lookup"><span data-stu-id="83a32-114">protectionLevel</span></span>|<span data-ttu-id="83a32-115">İleti düzeyi güvenliği tanımlar.</span><span class="sxs-lookup"><span data-stu-id="83a32-115">Defines message-level security.</span></span> <span data-ttu-id="83a32-116">İleti imzalama, bir üçüncü taraf aktarılırken iletinin oynama riskini azaltır.</span><span class="sxs-lookup"><span data-stu-id="83a32-116">Signing messages mitigates the risk of a third party tampering with the message while it is being transferred.</span></span> <span data-ttu-id="83a32-117">Şifreleme, aktarım sırasında verileri düzeyinde gizlilik sağlar.</span><span class="sxs-lookup"><span data-stu-id="83a32-117">Encryption provides data-level privacy during transport.</span></span> <span data-ttu-id="83a32-118">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="83a32-118">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="83a32-119">-Yok: Koruma yok.</span><span class="sxs-lookup"><span data-stu-id="83a32-119">-   None: No protection.</span></span><br /><span data-ttu-id="83a32-120">-Oturum: İmzalı iletiler.</span><span class="sxs-lookup"><span data-stu-id="83a32-120">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="83a32-121">-   EncryptAndSign: İletileri imzalanacak ve şifrelenecek.</span><span class="sxs-lookup"><span data-stu-id="83a32-121">-   EncryptAndSign: Messages are signed and encrypted.</span></span><br /><br /> <span data-ttu-id="83a32-122">EncryptAndSign varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="83a32-122">The default is EncryptAndSign.</span></span><br /><br /> <span data-ttu-id="83a32-123">Bu öznitelik türünde <xref:System.Net.Security.ProtectionLevel>.</span><span class="sxs-lookup"><span data-stu-id="83a32-123">This attribute is of type <xref:System.Net.Security.ProtectionLevel>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="83a32-124">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="83a32-124">Child Elements</span></span>  
 <span data-ttu-id="83a32-125">Yok.</span><span class="sxs-lookup"><span data-stu-id="83a32-125">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="83a32-126">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="83a32-126">Parent Elements</span></span>  
  
|<span data-ttu-id="83a32-127">Öğe</span><span class="sxs-lookup"><span data-stu-id="83a32-127">Element</span></span>|<span data-ttu-id="83a32-128">Açıklama</span><span class="sxs-lookup"><span data-stu-id="83a32-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="83a32-129">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="83a32-129">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="83a32-130">Özel bağlama tüm bağlama yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="83a32-130">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="83a32-131">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="83a32-131">Remarks</span></span>  
 <span data-ttu-id="83a32-132">Bir akışa dayalı Protokolü gibi TCP ve adlandırılmış kanallar taşımalar aktarım akışı tabanlı yükseltmeyi destekler.</span><span class="sxs-lookup"><span data-stu-id="83a32-132">Transports that use a stream-oriented protocol such as TCP and named pipes support stream-based transport upgrades.</span></span> <span data-ttu-id="83a32-133">Özellikle, WCF güvenlik yükseltmeleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="83a32-133">Specifically, WCF provides security upgrades.</span></span> <span data-ttu-id="83a32-134">Bu aktarım güvenliği yapılandırma bu yapılandırma öğesi tarafından yanı kapsüllenir [ \<sslStreamSecurity >](../../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md), hangi yapılandırılabilir ve özel bağlama için eklendi</span><span class="sxs-lookup"><span data-stu-id="83a32-134">The configuration of this transport security is encapsulated by this configuration element  as well as by [\<sslStreamSecurity>](../../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md), which can be configured and added to a custom binding</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83a32-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="83a32-135">See also</span></span>

- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Configuration.WindowsStreamSecurityElement>
- <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>
- [<span data-ttu-id="83a32-136">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="83a32-136">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="83a32-137">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="83a32-137">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="83a32-138">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="83a32-138">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="83a32-139">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="83a32-139">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
