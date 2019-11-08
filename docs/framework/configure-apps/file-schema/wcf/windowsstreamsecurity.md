---
title: <windowsStreamSecurity>
ms.date: 03/30/2017
ms.assetid: 926bea29-90c7-4a26-9cf0-fb4aa44f6f70
ms.openlocfilehash: dab8505a9ddb348a6f7fe16ae9acb3a0119a8b06
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73735886"
---
# <a name="windowsstreamsecurity"></a><span data-ttu-id="5ed05-101">windowsStreamSecurity > \<</span><span class="sxs-lookup"><span data-stu-id="5ed05-101">\<windowsStreamSecurity></span></span>
<span data-ttu-id="5ed05-102">Özel bağlamanın Windows akış güvenlik ayarlarını belirtin.</span><span class="sxs-lookup"><span data-stu-id="5ed05-102">Specify Windows stream security settings of the custom binding.</span></span>  
  
<span data-ttu-id="5ed05-103">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="5ed05-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="5ed05-104">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="5ed05-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="5ed05-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bağlamaları >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="5ed05-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="5ed05-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<customBinding >** ](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="5ed05-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="5ed05-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<bağlama >** </span><span class="sxs-lookup"><span data-stu-id="5ed05-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="5ed05-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<windowsStreamSecurity >**</span><span class="sxs-lookup"><span data-stu-id="5ed05-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<windowsStreamSecurity>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ed05-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5ed05-109">Syntax</span></span>  
  
```xml  
<windowsStreamSecurity protectionLevel="None/Sign/EncryptAndSign" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5ed05-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="5ed05-110">Attributes and Elements</span></span>  
 <span data-ttu-id="5ed05-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5ed05-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5ed05-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="5ed05-112">Attributes</span></span>  
  
|<span data-ttu-id="5ed05-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="5ed05-113">Attribute</span></span>|<span data-ttu-id="5ed05-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5ed05-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5ed05-115">protectionLevel</span><span class="sxs-lookup"><span data-stu-id="5ed05-115">protectionLevel</span></span>|<span data-ttu-id="5ed05-116">İleti düzeyi güvenliği tanımlar.</span><span class="sxs-lookup"><span data-stu-id="5ed05-116">Defines message-level security.</span></span> <span data-ttu-id="5ed05-117">İmzalama iletileri, üçüncü bir tarafın aktarılırken ileti üzerinde izinsiz değişiklik yaptığı riski azaltır.</span><span class="sxs-lookup"><span data-stu-id="5ed05-117">Signing messages mitigates the risk of a third party tampering with the message while it is being transferred.</span></span> <span data-ttu-id="5ed05-118">Şifreleme, aktarım sırasında veri düzeyinde gizlilik sağlar.</span><span class="sxs-lookup"><span data-stu-id="5ed05-118">Encryption provides data-level privacy during transport.</span></span> <span data-ttu-id="5ed05-119">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="5ed05-119">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="5ed05-120">-None: koruma yok.</span><span class="sxs-lookup"><span data-stu-id="5ed05-120">-   None: No protection.</span></span><br /><span data-ttu-id="5ed05-121">-Sign: Iletiler imzalanır.</span><span class="sxs-lookup"><span data-stu-id="5ed05-121">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="5ed05-122">-EncryptAndSign: Iletiler imzalanır ve şifrelenir.</span><span class="sxs-lookup"><span data-stu-id="5ed05-122">-   EncryptAndSign: Messages are signed and encrypted.</span></span><br /><br /> <span data-ttu-id="5ed05-123">Varsayılan değer EncryptAndSign ' dır.</span><span class="sxs-lookup"><span data-stu-id="5ed05-123">The default is EncryptAndSign.</span></span><br /><br /> <span data-ttu-id="5ed05-124">Bu öznitelik <xref:System.Net.Security.ProtectionLevel>türündedir.</span><span class="sxs-lookup"><span data-stu-id="5ed05-124">This attribute is of type <xref:System.Net.Security.ProtectionLevel>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5ed05-125">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="5ed05-125">Child Elements</span></span>  
 <span data-ttu-id="5ed05-126">Yok.</span><span class="sxs-lookup"><span data-stu-id="5ed05-126">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5ed05-127">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="5ed05-127">Parent Elements</span></span>  
  
|<span data-ttu-id="5ed05-128">Öğe</span><span class="sxs-lookup"><span data-stu-id="5ed05-128">Element</span></span>|<span data-ttu-id="5ed05-129">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5ed05-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5ed05-130">\< bağlama ></span><span class="sxs-lookup"><span data-stu-id="5ed05-130">\<binding></span></span>](bindings.md)|<span data-ttu-id="5ed05-131">Özel bağlamanın tüm bağlama yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="5ed05-131">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5ed05-132">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5ed05-132">Remarks</span></span>  
 <span data-ttu-id="5ed05-133">TCP ve adlandırılmış kanallar gibi akış yönelimli protokol kullanan aktarımlar, akış tabanlı Aktarım yükseltmelerini destekler.</span><span class="sxs-lookup"><span data-stu-id="5ed05-133">Transports that use a stream-oriented protocol such as TCP and named pipes support stream-based transport upgrades.</span></span> <span data-ttu-id="5ed05-134">Özel olarak, WCF güvenlik yükseltmeleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="5ed05-134">Specifically, WCF provides security upgrades.</span></span> <span data-ttu-id="5ed05-135">Bu aktarım güvenliği yapılandırması, bu yapılandırma öğesiyle ve özel bir bağlamaya eklenebilen [\<sslStreamSecurity >](sslstreamsecurity.md)tarafından kapsüllenir</span><span class="sxs-lookup"><span data-stu-id="5ed05-135">The configuration of this transport security is encapsulated by this configuration element  as well as by [\<sslStreamSecurity>](sslstreamsecurity.md), which can be configured and added to a custom binding</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ed05-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5ed05-136">See also</span></span>

- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Configuration.WindowsStreamSecurityElement>
- <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>
- [<span data-ttu-id="5ed05-137">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="5ed05-137">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="5ed05-138">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="5ed05-138">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="5ed05-139">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="5ed05-139">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="5ed05-140">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="5ed05-140">\<customBinding></span></span>](custombinding.md)
