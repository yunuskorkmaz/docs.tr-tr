---
description: 'Hakkında daha fazla bilgi <security> edinin: <netNamedPipeBinding>'
title: <security> / <netNamedPipeBinding>
ms.date: 03/30/2017
ms.assetid: bb3cb022-637e-49fd-92e8-6766038affa7
ms.openlocfilehash: d64917c53390cade00d9e104c8581ce45355ac34
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99683105"
---
# <a name="security-of-netnamedpipebinding"></a><span data-ttu-id="6c187-103">\<security> / \<netNamedPipeBinding></span><span class="sxs-lookup"><span data-stu-id="6c187-103">\<security> of \<netNamedPipeBinding></span></span>

<span data-ttu-id="6c187-104">Bağlama için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6c187-104">Defines the security settings for a binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netNamedPipeBinding>**](netnamedpipebinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a><span data-ttu-id="6c187-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="6c187-105">Syntax</span></span>  
  
```xml  
<netNamedPipeBinding>
  <binding>
    <security mode="None/Transport">
      <transport protectionLevel="None/Sign/EncryptAndSign" />
    </security>
  </binding>
</netNamedPipeBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6c187-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="6c187-106">Attributes and Elements</span></span>  

 <span data-ttu-id="6c187-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6c187-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6c187-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="6c187-108">Attributes</span></span>  
  
|<span data-ttu-id="6c187-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="6c187-109">Attribute</span></span>|<span data-ttu-id="6c187-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6c187-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6c187-111">mod</span><span class="sxs-lookup"><span data-stu-id="6c187-111">mode</span></span>|<span data-ttu-id="6c187-112">Bu bağlamaya uygulanan güvenlik türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="6c187-112">Specifies the type of security that is applied to this binding.</span></span> <span data-ttu-id="6c187-113">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="6c187-113">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="6c187-114">-None: Bu, güvenliği devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="6c187-114">-   None: This disables security.</span></span><br /><span data-ttu-id="6c187-115">-Transport: güvenlik, temel alınan aktarım tabanlı güvenlik kullanılarak sağlanır.</span><span class="sxs-lookup"><span data-stu-id="6c187-115">-   Transport: Security is provided using underlying transport based security.</span></span> <span data-ttu-id="6c187-116">Koruma düzeyini Bu modla denetlemek mümkündür.</span><span class="sxs-lookup"><span data-stu-id="6c187-116">It is possible to control the protection level with this mode.</span></span><br /><span data-ttu-id="6c187-117">-Varsayılan değer Transport ' dır.</span><span class="sxs-lookup"><span data-stu-id="6c187-117">-   The default value is Transport.</span></span> <span data-ttu-id="6c187-118">Bu öznitelik türü <xref:System.ServiceModel.NetNamedPipeSecurityMode> .</span><span class="sxs-lookup"><span data-stu-id="6c187-118">This attribute is of type <xref:System.ServiceModel.NetNamedPipeSecurityMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6c187-119">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="6c187-119">Child Elements</span></span>  
  
|<span data-ttu-id="6c187-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="6c187-120">Element</span></span>|<span data-ttu-id="6c187-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6c187-121">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6c187-122">taşıma</span><span class="sxs-lookup"><span data-stu-id="6c187-122">transport</span></span>|<span data-ttu-id="6c187-123">Taşımanın güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6c187-123">Defines the security settings for the transport.</span></span> <span data-ttu-id="6c187-124">Bu öğe türündedir <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement> .</span><span class="sxs-lookup"><span data-stu-id="6c187-124">This element is of type <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6c187-125">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="6c187-125">Parent Elements</span></span>  
  
|<span data-ttu-id="6c187-126">Öğe</span><span class="sxs-lookup"><span data-stu-id="6c187-126">Element</span></span>|<span data-ttu-id="6c187-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6c187-127">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6c187-128">bağlama</span><span class="sxs-lookup"><span data-stu-id="6c187-128">binding</span></span>|<span data-ttu-id="6c187-129">Öğesinin bağlama öğesi [\<netNamedPipeBinding>](netnamedpipebinding.md) .</span><span class="sxs-lookup"><span data-stu-id="6c187-129">The binding element of the [\<netNamedPipeBinding>](netnamedpipebinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6c187-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6c187-130">See also</span></span>

- <xref:System.ServiceModel.NetNamedPipeSecurity>
- <xref:System.ServiceModel.NetNamedPipeBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.NetNamedPipeSecurityElement>
- [<span data-ttu-id="6c187-131">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="6c187-131">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="6c187-132">Kimlik Bilgisi Türü Seçme</span><span class="sxs-lookup"><span data-stu-id="6c187-132">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="6c187-133">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="6c187-133">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="6c187-134">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="6c187-134">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="6c187-135">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="6c187-135">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
