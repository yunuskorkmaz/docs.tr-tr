---
title: <windowsStreamSecurity>
ms.date: 03/30/2017
ms.assetid: 926bea29-90c7-4a26-9cf0-fb4aa44f6f70
ms.openlocfilehash: 3c82bd81bd0fabf10f2dd835188b346f62d038b5
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91167086"
---
# \<windowsStreamSecurity>

<span data-ttu-id="8904e-101">Özel bağlamanın Windows akış güvenlik ayarlarını belirtin.</span><span class="sxs-lookup"><span data-stu-id="8904e-101">Specify Windows stream security settings of the custom binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<windowsStreamSecurity>**  
  
## <a name="syntax"></a><span data-ttu-id="8904e-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="8904e-102">Syntax</span></span>  
  
```xml  
<windowsStreamSecurity protectionLevel="None/Sign/EncryptAndSign" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8904e-103">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="8904e-103">Attributes and Elements</span></span>  

 <span data-ttu-id="8904e-104">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8904e-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8904e-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="8904e-105">Attributes</span></span>  
  
|<span data-ttu-id="8904e-106">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="8904e-106">Attribute</span></span>|<span data-ttu-id="8904e-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8904e-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8904e-108">protectionLevel</span><span class="sxs-lookup"><span data-stu-id="8904e-108">protectionLevel</span></span>|<span data-ttu-id="8904e-109">İleti düzeyi güvenliği tanımlar.</span><span class="sxs-lookup"><span data-stu-id="8904e-109">Defines message-level security.</span></span> <span data-ttu-id="8904e-110">İmzalama iletileri, üçüncü bir tarafın aktarılırken ileti üzerinde izinsiz değişiklik yaptığı riski azaltır.</span><span class="sxs-lookup"><span data-stu-id="8904e-110">Signing messages mitigates the risk of a third party tampering with the message while it is being transferred.</span></span> <span data-ttu-id="8904e-111">Şifreleme, aktarım sırasında veri düzeyinde gizlilik sağlar.</span><span class="sxs-lookup"><span data-stu-id="8904e-111">Encryption provides data-level privacy during transport.</span></span> <span data-ttu-id="8904e-112">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="8904e-112">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="8904e-113">-None: koruma yok.</span><span class="sxs-lookup"><span data-stu-id="8904e-113">-   None: No protection.</span></span><br /><span data-ttu-id="8904e-114">-Sign: Iletiler imzalanır.</span><span class="sxs-lookup"><span data-stu-id="8904e-114">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="8904e-115">-EncryptAndSign: Iletiler imzalanır ve şifrelenir.</span><span class="sxs-lookup"><span data-stu-id="8904e-115">-   EncryptAndSign: Messages are signed and encrypted.</span></span><br /><br /> <span data-ttu-id="8904e-116">Varsayılan değer EncryptAndSign ' dır.</span><span class="sxs-lookup"><span data-stu-id="8904e-116">The default is EncryptAndSign.</span></span><br /><br /> <span data-ttu-id="8904e-117">Bu öznitelik türü <xref:System.Net.Security.ProtectionLevel> .</span><span class="sxs-lookup"><span data-stu-id="8904e-117">This attribute is of type <xref:System.Net.Security.ProtectionLevel>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8904e-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="8904e-118">Child Elements</span></span>  

 <span data-ttu-id="8904e-119">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="8904e-119">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8904e-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="8904e-120">Parent Elements</span></span>  
  
|<span data-ttu-id="8904e-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="8904e-121">Element</span></span>|<span data-ttu-id="8904e-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8904e-122">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="8904e-123">Özel bağlamanın tüm bağlama yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="8904e-123">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8904e-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8904e-124">Remarks</span></span>  

 <span data-ttu-id="8904e-125">TCP ve adlandırılmış kanallar gibi akış yönelimli protokol kullanan aktarımlar, akış tabanlı Aktarım yükseltmelerini destekler.</span><span class="sxs-lookup"><span data-stu-id="8904e-125">Transports that use a stream-oriented protocol such as TCP and named pipes support stream-based transport upgrades.</span></span> <span data-ttu-id="8904e-126">Özel olarak, WCF güvenlik yükseltmeleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="8904e-126">Specifically, WCF provides security upgrades.</span></span> <span data-ttu-id="8904e-127">Bu aktarım güvenliği yapılandırması, bu yapılandırma öğesi tarafından [\<sslStreamSecurity>](sslstreamsecurity.md) ve tarafından ve özel bir bağlamaya eklenebilen tarafından kapsüllenir</span><span class="sxs-lookup"><span data-stu-id="8904e-127">The configuration of this transport security is encapsulated by this configuration element  as well as by [\<sslStreamSecurity>](sslstreamsecurity.md), which can be configured and added to a custom binding</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8904e-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8904e-128">See also</span></span>

- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Configuration.WindowsStreamSecurityElement>
- <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>
- [<span data-ttu-id="8904e-129">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="8904e-129">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="8904e-130">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="8904e-130">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="8904e-131">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="8904e-131">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
