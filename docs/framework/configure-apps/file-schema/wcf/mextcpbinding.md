---
title: <mexTcpBinding>
ms.date: 03/30/2017
ms.assetid: 01baba8d-d784-4255-9ea2-7afff1482bf0
ms.openlocfilehash: 9e76d65a27e7732d1d62c4ba25afac76d73be167
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59078895"
---
# <a name="mextcpbinding"></a><span data-ttu-id="bc934-101">\<mexTcpBinding ></span><span class="sxs-lookup"><span data-stu-id="bc934-101">\<mexTcpBinding></span></span>
<span data-ttu-id="bc934-102">TCP üzerinde WS-MetadataExchange (WS-MEX) ileti değişimi için kullanılan bir bağlama için olan ayarları belirler.</span><span class="sxs-lookup"><span data-stu-id="bc934-102">Specifies the settings for a binding used for the WS-MetadataExchange (WS-MEX) message exchange over TCP.</span></span>  
  
 <span data-ttu-id="bc934-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="bc934-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="bc934-104">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="bc934-104">\<bindings></span></span>  
<span data-ttu-id="bc934-105">\<mexTcpBinding ></span><span class="sxs-lookup"><span data-stu-id="bc934-105">\<mexTcpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc934-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bc934-106">Syntax</span></span>  
  
```xml  
<mexTcpBinding>
  <binding closeTimeout="TimeSpan"
           name="string"
           openTimeout="TimeSpan"
           receiveTimeout="TimeSpan"
           sendTimeout="TimeSpan">
  </binding>
</mexTcpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bc934-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="bc934-107">Attributes and Elements</span></span>  
 <span data-ttu-id="bc934-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="bc934-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bc934-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="bc934-109">Attributes</span></span>  
  
|<span data-ttu-id="bc934-110">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="bc934-110">Attribute</span></span>|<span data-ttu-id="bc934-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bc934-111">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="bc934-112">A <xref:System.TimeSpan> bir kapatma işlemi tamamlamak sağlanan zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="bc934-112">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="bc934-113">Bu değer, büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="bc934-113">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="bc934-114">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="bc934-114">The default is 00:01:00.</span></span>|  
|`name`|<span data-ttu-id="bc934-115">Bağlama yapılandırma adını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="bc934-115">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="bc934-116">Bağlama için bir tanımlayıcı olarak kullanıldığından, bu değer benzersiz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="bc934-116">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="bc934-117">Her bağlama sahip bir `name` ve `namespace` birlikte benzersiz özniteliği hizmetinin meta verilerde tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="bc934-117">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span> <span data-ttu-id="bc934-118">Ayrıca, bu ad aynı türdeki bağlamaları arasında benzersizdir.</span><span class="sxs-lookup"><span data-stu-id="bc934-118">In addition, this name is unique among bindings of the same type.</span></span> <span data-ttu-id="bc934-119">İle başlayarak [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bağlamalar ve davranışları için gerekli değildir bir ada sahip.</span><span class="sxs-lookup"><span data-stu-id="bc934-119">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="bc934-120">Varsayılan yapılandırma ve adsız bağlamaları ve davranışları hakkında daha fazla bilgi için bkz: [Basitleştirilmiş yapılandırma](../../../../../docs/framework/wcf/simplified-configuration.md) ve [WCF hizmetleri için Basitleştirilmiş yapılandırma](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="bc934-120">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="bc934-121">A <xref:System.TimeSpan> tamamlamak açık işlem için sağlanan zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="bc934-121">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="bc934-122">Bu değer, büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="bc934-122">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="bc934-123">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="bc934-123">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="bc934-124">A <xref:System.TimeSpan> tamamlamak alma işlemi için sağlanan zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="bc934-124">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="bc934-125">Bu değer, büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="bc934-125">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="bc934-126">Varsayılan değer 00:10:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="bc934-126">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="bc934-127">A <xref:System.TimeSpan> tamamlamak bir gönderme işlemi için sağlanan zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="bc934-127">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="bc934-128">Bu değer, büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="bc934-128">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="bc934-129">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="bc934-129">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bc934-130">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="bc934-130">Child Elements</span></span>  
 <span data-ttu-id="bc934-131">Yok.</span><span class="sxs-lookup"><span data-stu-id="bc934-131">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bc934-132">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="bc934-132">Parent Elements</span></span>  
  
|<span data-ttu-id="bc934-133">Öğe</span><span class="sxs-lookup"><span data-stu-id="bc934-133">Element</span></span>|<span data-ttu-id="bc934-134">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bc934-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bc934-135">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="bc934-135">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="bc934-136">Bu öğe, standart ve özel bağlamalar koleksiyonunu tutar.</span><span class="sxs-lookup"><span data-stu-id="bc934-136">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bc934-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bc934-137">See also</span></span>

- <xref:System.ServiceModel.Configuration.MexTcpBindingElement>
- <xref:System.ServiceModel.Description.MetadataExchangeBindings.CreateMexTcpBinding%2A>
- [<span data-ttu-id="bc934-138">Nasıl yapılır: Bir yapılandırma dosyası kullanarak bir hizmet için meta verileri yayımlama</span><span class="sxs-lookup"><span data-stu-id="bc934-138">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [<span data-ttu-id="bc934-139">Özel Bağlama Üzerinden Meta Veri Yayımlama ve Alma</span><span class="sxs-lookup"><span data-stu-id="bc934-139">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../../../docs/framework/wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)
- [<span data-ttu-id="bc934-140">Meta Veriler</span><span class="sxs-lookup"><span data-stu-id="bc934-140">Metadata</span></span>](../../../../../docs/framework/wcf/feature-details/metadata.md)
- [<span data-ttu-id="bc934-141">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="bc934-141">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="bc934-142">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="bc934-142">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="bc934-143">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="bc934-143">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="bc934-144">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="bc934-144">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
