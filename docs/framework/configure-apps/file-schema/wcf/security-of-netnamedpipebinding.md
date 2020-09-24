---
title: <security> / <netNamedPipeBinding>
ms.date: 03/30/2017
ms.assetid: bb3cb022-637e-49fd-92e8-6766038affa7
ms.openlocfilehash: 1a231a60d29cc6a4460de69a98753c23c0386027
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91170044"
---
# <a name="security-of-netnamedpipebinding"></a><span data-ttu-id="43725-102">\<security> / \<netNamedPipeBinding></span><span class="sxs-lookup"><span data-stu-id="43725-102">\<security> of \<netNamedPipeBinding></span></span>

<span data-ttu-id="43725-103">Bağlama için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="43725-103">Defines the security settings for a binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netNamedPipeBinding>**](netnamedpipebinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a><span data-ttu-id="43725-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="43725-104">Syntax</span></span>  
  
```xml  
<netNamedPipeBinding>
  <binding>
    <security mode="None/Transport">
      <transport protectionLevel="None/Sign/EncryptAndSign" />
    </security>
  </binding>
</netNamedPipeBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="43725-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="43725-105">Attributes and Elements</span></span>  

 <span data-ttu-id="43725-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="43725-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="43725-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="43725-107">Attributes</span></span>  
  
|<span data-ttu-id="43725-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="43725-108">Attribute</span></span>|<span data-ttu-id="43725-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="43725-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="43725-110">mod</span><span class="sxs-lookup"><span data-stu-id="43725-110">mode</span></span>|<span data-ttu-id="43725-111">Bu bağlamaya uygulanan güvenlik türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="43725-111">Specifies the type of security that is applied to this binding.</span></span> <span data-ttu-id="43725-112">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="43725-112">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="43725-113">-None: Bu, güvenliği devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="43725-113">-   None: This disables security.</span></span><br /><span data-ttu-id="43725-114">-Transport: güvenlik, temel alınan aktarım tabanlı güvenlik kullanılarak sağlanır.</span><span class="sxs-lookup"><span data-stu-id="43725-114">-   Transport: Security is provided using underlying transport based security.</span></span> <span data-ttu-id="43725-115">Koruma düzeyini Bu modla denetlemek mümkündür.</span><span class="sxs-lookup"><span data-stu-id="43725-115">It is possible to control the protection level with this mode.</span></span><br /><span data-ttu-id="43725-116">-Varsayılan değer Transport ' dır.</span><span class="sxs-lookup"><span data-stu-id="43725-116">-   The default value is Transport.</span></span> <span data-ttu-id="43725-117">Bu öznitelik türü <xref:System.ServiceModel.NetNamedPipeSecurityMode> .</span><span class="sxs-lookup"><span data-stu-id="43725-117">This attribute is of type <xref:System.ServiceModel.NetNamedPipeSecurityMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="43725-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="43725-118">Child Elements</span></span>  
  
|<span data-ttu-id="43725-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="43725-119">Element</span></span>|<span data-ttu-id="43725-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="43725-120">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="43725-121">taşıma</span><span class="sxs-lookup"><span data-stu-id="43725-121">transport</span></span>|<span data-ttu-id="43725-122">Taşımanın güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="43725-122">Defines the security settings for the transport.</span></span> <span data-ttu-id="43725-123">Bu öğe türündedir <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement> .</span><span class="sxs-lookup"><span data-stu-id="43725-123">This element is of type <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="43725-124">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="43725-124">Parent Elements</span></span>  
  
|<span data-ttu-id="43725-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="43725-125">Element</span></span>|<span data-ttu-id="43725-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="43725-126">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="43725-127">bağlama</span><span class="sxs-lookup"><span data-stu-id="43725-127">binding</span></span>|<span data-ttu-id="43725-128">Öğesinin bağlama öğesi [\<netNamedPipeBinding>](netnamedpipebinding.md) .</span><span class="sxs-lookup"><span data-stu-id="43725-128">The binding element of the [\<netNamedPipeBinding>](netnamedpipebinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="43725-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="43725-129">See also</span></span>

- <xref:System.ServiceModel.NetNamedPipeSecurity>
- <xref:System.ServiceModel.NetNamedPipeBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.NetNamedPipeSecurityElement>
- [<span data-ttu-id="43725-130">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="43725-130">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="43725-131">Kimlik Bilgisi Türü Seçme</span><span class="sxs-lookup"><span data-stu-id="43725-131">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="43725-132">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="43725-132">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="43725-133">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="43725-133">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="43725-134">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="43725-134">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
