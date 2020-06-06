---
title: <security> / <netNamedPipeBinding>
ms.date: 03/30/2017
ms.assetid: bb3cb022-637e-49fd-92e8-6766038affa7
ms.openlocfilehash: 31ea31ce6880a770c966350cd931e487396c4d63
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73736440"
---
# <a name="security-of-netnamedpipebinding"></a><span data-ttu-id="ce2d9-102">\<security> / \<netNamedPipeBinding></span><span class="sxs-lookup"><span data-stu-id="ce2d9-102">\<security> of \<netNamedPipeBinding></span></span>
<span data-ttu-id="ce2d9-103">Bağlama için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="ce2d9-103">Defines the security settings for a binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netNamedPipeBinding>**](netnamedpipebinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a><span data-ttu-id="ce2d9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ce2d9-104">Syntax</span></span>  
  
```xml  
<netNamedPipeBinding>
  <binding>
    <security mode="None/Transport">
      <transport protectionLevel="None/Sign/EncryptAndSign" />
    </security>
  </binding>
</netNamedPipeBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ce2d9-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="ce2d9-105">Attributes and Elements</span></span>  
 <span data-ttu-id="ce2d9-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ce2d9-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ce2d9-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="ce2d9-107">Attributes</span></span>  
  
|<span data-ttu-id="ce2d9-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="ce2d9-108">Attribute</span></span>|<span data-ttu-id="ce2d9-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ce2d9-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ce2d9-110">mod</span><span class="sxs-lookup"><span data-stu-id="ce2d9-110">mode</span></span>|<span data-ttu-id="ce2d9-111">Bu bağlamaya uygulanan güvenlik türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="ce2d9-111">Specifies the type of security that is applied to this binding.</span></span> <span data-ttu-id="ce2d9-112">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="ce2d9-112">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="ce2d9-113">-None: Bu, güvenliği devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="ce2d9-113">-   None: This disables security.</span></span><br /><span data-ttu-id="ce2d9-114">-Transport: güvenlik, temel alınan aktarım tabanlı güvenlik kullanılarak sağlanır.</span><span class="sxs-lookup"><span data-stu-id="ce2d9-114">-   Transport: Security is provided using underlying transport based security.</span></span> <span data-ttu-id="ce2d9-115">Koruma düzeyini Bu modla denetlemek mümkündür.</span><span class="sxs-lookup"><span data-stu-id="ce2d9-115">It is possible to control the protection level with this mode.</span></span><br /><span data-ttu-id="ce2d9-116">-Varsayılan değer Transport ' dır.</span><span class="sxs-lookup"><span data-stu-id="ce2d9-116">-   The default value is Transport.</span></span> <span data-ttu-id="ce2d9-117">Bu öznitelik türü <xref:System.ServiceModel.NetNamedPipeSecurityMode> .</span><span class="sxs-lookup"><span data-stu-id="ce2d9-117">This attribute is of type <xref:System.ServiceModel.NetNamedPipeSecurityMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ce2d9-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="ce2d9-118">Child Elements</span></span>  
  
|<span data-ttu-id="ce2d9-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="ce2d9-119">Element</span></span>|<span data-ttu-id="ce2d9-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ce2d9-120">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ce2d9-121">taşıma</span><span class="sxs-lookup"><span data-stu-id="ce2d9-121">transport</span></span>|<span data-ttu-id="ce2d9-122">Taşımanın güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="ce2d9-122">Defines the security settings for the transport.</span></span> <span data-ttu-id="ce2d9-123">Bu öğe türündedir <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement> .</span><span class="sxs-lookup"><span data-stu-id="ce2d9-123">This element is of type <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ce2d9-124">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="ce2d9-124">Parent Elements</span></span>  
  
|<span data-ttu-id="ce2d9-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="ce2d9-125">Element</span></span>|<span data-ttu-id="ce2d9-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ce2d9-126">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ce2d9-127">bağlama</span><span class="sxs-lookup"><span data-stu-id="ce2d9-127">binding</span></span>|<span data-ttu-id="ce2d9-128">Öğesinin bağlama öğesi [\<netNamedPipeBinding>](netnamedpipebinding.md) .</span><span class="sxs-lookup"><span data-stu-id="ce2d9-128">The binding element of the [\<netNamedPipeBinding>](netnamedpipebinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ce2d9-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ce2d9-129">See also</span></span>

- <xref:System.ServiceModel.NetNamedPipeSecurity>
- <xref:System.ServiceModel.NetNamedPipeBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.NetNamedPipeSecurityElement>
- [<span data-ttu-id="ce2d9-130">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="ce2d9-130">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="ce2d9-131">Kimlik Bilgisi Türü Seçme</span><span class="sxs-lookup"><span data-stu-id="ce2d9-131">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="ce2d9-132">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="ce2d9-132">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="ce2d9-133">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="ce2d9-133">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="ce2d9-134">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="ce2d9-134">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
