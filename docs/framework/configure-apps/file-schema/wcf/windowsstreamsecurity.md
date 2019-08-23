---
title: <windowsStreamSecurity>
ms.date: 03/30/2017
ms.assetid: 926bea29-90c7-4a26-9cf0-fb4aa44f6f70
ms.openlocfilehash: 0f1dfd523e593c82727354db7ce39ffc992bdfb4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69932800"
---
# <a name="windowsstreamsecurity"></a><span data-ttu-id="b1371-101">\<windowsStreamSecurity ></span><span class="sxs-lookup"><span data-stu-id="b1371-101">\<windowsStreamSecurity></span></span>
<span data-ttu-id="b1371-102">Özel bağlamanın Windows akış güvenlik ayarlarını belirtin.</span><span class="sxs-lookup"><span data-stu-id="b1371-102">Specify Windows stream security settings of the custom binding.</span></span>  
  
 <span data-ttu-id="b1371-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="b1371-103">\<system.serviceModel></span></span>  
<span data-ttu-id="b1371-104">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="b1371-104">\<bindings></span></span>  
<span data-ttu-id="b1371-105">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="b1371-105">\<customBinding></span></span>  
<span data-ttu-id="b1371-106">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="b1371-106">\<binding></span></span>  
<span data-ttu-id="b1371-107">\<windowsStreamSecurity ></span><span class="sxs-lookup"><span data-stu-id="b1371-107">\<windowsStreamSecurity></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1371-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b1371-108">Syntax</span></span>  
  
```xml  
<windowsStreamSecurity protectionLevel="None/Sign/EncryptAndSign" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b1371-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="b1371-109">Attributes and Elements</span></span>  
 <span data-ttu-id="b1371-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b1371-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b1371-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="b1371-111">Attributes</span></span>  
  
|<span data-ttu-id="b1371-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="b1371-112">Attribute</span></span>|<span data-ttu-id="b1371-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b1371-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b1371-114">protectionLevel</span><span class="sxs-lookup"><span data-stu-id="b1371-114">protectionLevel</span></span>|<span data-ttu-id="b1371-115">İleti düzeyi güvenliği tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b1371-115">Defines message-level security.</span></span> <span data-ttu-id="b1371-116">İmzalama iletileri, üçüncü bir tarafın aktarılırken ileti üzerinde izinsiz değişiklik yaptığı riski azaltır.</span><span class="sxs-lookup"><span data-stu-id="b1371-116">Signing messages mitigates the risk of a third party tampering with the message while it is being transferred.</span></span> <span data-ttu-id="b1371-117">Şifreleme, aktarım sırasında veri düzeyinde gizlilik sağlar.</span><span class="sxs-lookup"><span data-stu-id="b1371-117">Encryption provides data-level privacy during transport.</span></span> <span data-ttu-id="b1371-118">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="b1371-118">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="b1371-119">Seçim Koruma yok.</span><span class="sxs-lookup"><span data-stu-id="b1371-119">-   None: No protection.</span></span><br /><span data-ttu-id="b1371-120">İmzalayabilirsiniz İletiler imzalanır.</span><span class="sxs-lookup"><span data-stu-id="b1371-120">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="b1371-121">EncryptAndSign özelliğini İletiler imzalanır ve şifrelenir.</span><span class="sxs-lookup"><span data-stu-id="b1371-121">-   EncryptAndSign: Messages are signed and encrypted.</span></span><br /><br /> <span data-ttu-id="b1371-122">Varsayılan değer EncryptAndSign ' dır.</span><span class="sxs-lookup"><span data-stu-id="b1371-122">The default is EncryptAndSign.</span></span><br /><br /> <span data-ttu-id="b1371-123">Bu öznitelik türü <xref:System.Net.Security.ProtectionLevel>.</span><span class="sxs-lookup"><span data-stu-id="b1371-123">This attribute is of type <xref:System.Net.Security.ProtectionLevel>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b1371-124">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="b1371-124">Child Elements</span></span>  
 <span data-ttu-id="b1371-125">Yok.</span><span class="sxs-lookup"><span data-stu-id="b1371-125">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b1371-126">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="b1371-126">Parent Elements</span></span>  
  
|<span data-ttu-id="b1371-127">Öğe</span><span class="sxs-lookup"><span data-stu-id="b1371-127">Element</span></span>|<span data-ttu-id="b1371-128">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b1371-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b1371-129">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="b1371-129">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="b1371-130">Özel bağlamanın tüm bağlama yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b1371-130">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b1371-131">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b1371-131">Remarks</span></span>  
 <span data-ttu-id="b1371-132">TCP ve adlandırılmış kanallar gibi akış yönelimli protokol kullanan aktarımlar, akış tabanlı Aktarım yükseltmelerini destekler.</span><span class="sxs-lookup"><span data-stu-id="b1371-132">Transports that use a stream-oriented protocol such as TCP and named pipes support stream-based transport upgrades.</span></span> <span data-ttu-id="b1371-133">Özel olarak, WCF güvenlik yükseltmeleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="b1371-133">Specifically, WCF provides security upgrades.</span></span> <span data-ttu-id="b1371-134">Bu taşıma güvenliği yapılandırması, bu yapılandırma öğesiyle ve özel bir bağlamaya eklenebilen ve bu yapılandırma öğesi [ \<tarafından, sslStreamSecurity >](sslstreamsecurity.md)tarafından kapsüllenir</span><span class="sxs-lookup"><span data-stu-id="b1371-134">The configuration of this transport security is encapsulated by this configuration element  as well as by [\<sslStreamSecurity>](sslstreamsecurity.md), which can be configured and added to a custom binding</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1371-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b1371-135">See also</span></span>

- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Configuration.WindowsStreamSecurityElement>
- <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>
- [<span data-ttu-id="b1371-136">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="b1371-136">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="b1371-137">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="b1371-137">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="b1371-138">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="b1371-138">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="b1371-139">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="b1371-139">\<customBinding></span></span>](custombinding.md)
