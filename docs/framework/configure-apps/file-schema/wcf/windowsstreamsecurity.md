---
description: 'Hakkında daha fazla bilgi edinin: <windowsStreamSecurity>'
title: <windowsStreamSecurity>
ms.date: 03/30/2017
ms.assetid: 926bea29-90c7-4a26-9cf0-fb4aa44f6f70
ms.openlocfilehash: c623dc23ca67d0341b66a2a4d97de564be77dcc5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99682403"
---
# \<windowsStreamSecurity>

<span data-ttu-id="1ceb9-102">Özel bağlamanın Windows akış güvenlik ayarlarını belirtin.</span><span class="sxs-lookup"><span data-stu-id="1ceb9-102">Specify Windows stream security settings of the custom binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<windowsStreamSecurity>**  
  
## <a name="syntax"></a><span data-ttu-id="1ceb9-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="1ceb9-103">Syntax</span></span>  
  
```xml  
<windowsStreamSecurity protectionLevel="None/Sign/EncryptAndSign" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1ceb9-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="1ceb9-104">Attributes and Elements</span></span>  

 <span data-ttu-id="1ceb9-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1ceb9-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1ceb9-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="1ceb9-106">Attributes</span></span>  
  
|<span data-ttu-id="1ceb9-107">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="1ceb9-107">Attribute</span></span>|<span data-ttu-id="1ceb9-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1ceb9-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1ceb9-109">protectionLevel</span><span class="sxs-lookup"><span data-stu-id="1ceb9-109">protectionLevel</span></span>|<span data-ttu-id="1ceb9-110">İleti düzeyi güvenliği tanımlar.</span><span class="sxs-lookup"><span data-stu-id="1ceb9-110">Defines message-level security.</span></span> <span data-ttu-id="1ceb9-111">İmzalama iletileri, üçüncü bir tarafın aktarılırken ileti üzerinde izinsiz değişiklik yaptığı riski azaltır.</span><span class="sxs-lookup"><span data-stu-id="1ceb9-111">Signing messages mitigates the risk of a third party tampering with the message while it is being transferred.</span></span> <span data-ttu-id="1ceb9-112">Şifreleme, aktarım sırasında veri düzeyinde gizlilik sağlar.</span><span class="sxs-lookup"><span data-stu-id="1ceb9-112">Encryption provides data-level privacy during transport.</span></span> <span data-ttu-id="1ceb9-113">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="1ceb9-113">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="1ceb9-114">-None: koruma yok.</span><span class="sxs-lookup"><span data-stu-id="1ceb9-114">-   None: No protection.</span></span><br /><span data-ttu-id="1ceb9-115">-Sign: Iletiler imzalanır.</span><span class="sxs-lookup"><span data-stu-id="1ceb9-115">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="1ceb9-116">-EncryptAndSign: Iletiler imzalanır ve şifrelenir.</span><span class="sxs-lookup"><span data-stu-id="1ceb9-116">-   EncryptAndSign: Messages are signed and encrypted.</span></span><br /><br /> <span data-ttu-id="1ceb9-117">Varsayılan değer EncryptAndSign ' dır.</span><span class="sxs-lookup"><span data-stu-id="1ceb9-117">The default is EncryptAndSign.</span></span><br /><br /> <span data-ttu-id="1ceb9-118">Bu öznitelik türü <xref:System.Net.Security.ProtectionLevel> .</span><span class="sxs-lookup"><span data-stu-id="1ceb9-118">This attribute is of type <xref:System.Net.Security.ProtectionLevel>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1ceb9-119">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="1ceb9-119">Child Elements</span></span>  

 <span data-ttu-id="1ceb9-120">Yok</span><span class="sxs-lookup"><span data-stu-id="1ceb9-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1ceb9-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="1ceb9-121">Parent Elements</span></span>  
  
|<span data-ttu-id="1ceb9-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="1ceb9-122">Element</span></span>|<span data-ttu-id="1ceb9-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1ceb9-123">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="1ceb9-124">Özel bağlamanın tüm bağlama yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="1ceb9-124">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1ceb9-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1ceb9-125">Remarks</span></span>  

 <span data-ttu-id="1ceb9-126">TCP ve adlandırılmış kanallar gibi akış yönelimli protokol kullanan aktarımlar, akış tabanlı Aktarım yükseltmelerini destekler.</span><span class="sxs-lookup"><span data-stu-id="1ceb9-126">Transports that use a stream-oriented protocol such as TCP and named pipes support stream-based transport upgrades.</span></span> <span data-ttu-id="1ceb9-127">Özel olarak, WCF güvenlik yükseltmeleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="1ceb9-127">Specifically, WCF provides security upgrades.</span></span> <span data-ttu-id="1ceb9-128">Bu aktarım güvenliği yapılandırması, bu yapılandırma öğesi tarafından [\<sslStreamSecurity>](sslstreamsecurity.md) ve tarafından ve özel bir bağlamaya eklenebilen tarafından kapsüllenir</span><span class="sxs-lookup"><span data-stu-id="1ceb9-128">The configuration of this transport security is encapsulated by this configuration element  as well as by [\<sslStreamSecurity>](sslstreamsecurity.md), which can be configured and added to a custom binding</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ceb9-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1ceb9-129">See also</span></span>

- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Configuration.WindowsStreamSecurityElement>
- <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>
- [<span data-ttu-id="1ceb9-130">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="1ceb9-130">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="1ceb9-131">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="1ceb9-131">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="1ceb9-132">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="1ceb9-132">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
