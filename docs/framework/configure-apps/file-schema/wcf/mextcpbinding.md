---
title: '&lt;mexTcpBinding&gt;'
ms.date: 03/30/2017
ms.assetid: 01baba8d-d784-4255-9ea2-7afff1482bf0
ms.openlocfilehash: 4c3858ee0dc7fd20bd1269c74a4499998d530f03
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54733993"
---
# <a name="ltmextcpbindinggt"></a><span data-ttu-id="47a3b-102">&lt;mexTcpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="47a3b-102">&lt;mexTcpBinding&gt;</span></span>
<span data-ttu-id="47a3b-103">TCP üzerinde WS-MetadataExchange (WS-MEX) ileti değişimi için kullanılan bir bağlama için olan ayarları belirler.</span><span class="sxs-lookup"><span data-stu-id="47a3b-103">Specifies the settings for a binding used for the WS-MetadataExchange (WS-MEX) message exchange over TCP.</span></span>  
  
 <span data-ttu-id="47a3b-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="47a3b-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="47a3b-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="47a3b-105">\<bindings></span></span>  
<span data-ttu-id="47a3b-106">\<mexTcpBinding ></span><span class="sxs-lookup"><span data-stu-id="47a3b-106">\<mexTcpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="47a3b-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="47a3b-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="47a3b-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="47a3b-108">Attributes and Elements</span></span>  
 <span data-ttu-id="47a3b-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="47a3b-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="47a3b-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="47a3b-110">Attributes</span></span>  
  
|<span data-ttu-id="47a3b-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="47a3b-111">Attribute</span></span>|<span data-ttu-id="47a3b-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="47a3b-112">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="47a3b-113">A <xref:System.TimeSpan> bir kapatma işlemi tamamlamak sağlanan zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="47a3b-113">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="47a3b-114">Bu değer, büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="47a3b-114">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="47a3b-115">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="47a3b-115">The default is 00:01:00.</span></span>|  
|`name`|<span data-ttu-id="47a3b-116">Bağlama yapılandırma adını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="47a3b-116">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="47a3b-117">Bağlama için bir tanımlayıcı olarak kullanıldığından, bu değer benzersiz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="47a3b-117">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="47a3b-118">Her bağlama sahip bir `name` ve `namespace` birlikte benzersiz özniteliği hizmetinin meta verilerde tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="47a3b-118">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span> <span data-ttu-id="47a3b-119">Ayrıca, bu ad aynı türdeki bağlamaları arasında benzersizdir.</span><span class="sxs-lookup"><span data-stu-id="47a3b-119">In addition, this name is unique among bindings of the same type.</span></span> <span data-ttu-id="47a3b-120">İle başlayarak [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bağlamalar ve davranışları için gerekli değildir bir ada sahip.</span><span class="sxs-lookup"><span data-stu-id="47a3b-120">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="47a3b-121">Varsayılan yapılandırma ve adsız bağlamaları ve davranışları hakkında daha fazla bilgi için bkz: [Basitleştirilmiş yapılandırma](../../../../../docs/framework/wcf/simplified-configuration.md) ve [WCF hizmetleri için Basitleştirilmiş yapılandırma](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="47a3b-121">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="47a3b-122">A <xref:System.TimeSpan> tamamlamak açık işlem için sağlanan zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="47a3b-122">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="47a3b-123">Bu değer, büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="47a3b-123">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="47a3b-124">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="47a3b-124">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="47a3b-125">A <xref:System.TimeSpan> tamamlamak alma işlemi için sağlanan zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="47a3b-125">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="47a3b-126">Bu değer, büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="47a3b-126">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="47a3b-127">Varsayılan değer 00:10:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="47a3b-127">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="47a3b-128">A <xref:System.TimeSpan> tamamlamak bir gönderme işlemi için sağlanan zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="47a3b-128">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="47a3b-129">Bu değer, büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="47a3b-129">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="47a3b-130">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="47a3b-130">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="47a3b-131">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="47a3b-131">Child Elements</span></span>  
 <span data-ttu-id="47a3b-132">Yok.</span><span class="sxs-lookup"><span data-stu-id="47a3b-132">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="47a3b-133">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="47a3b-133">Parent Elements</span></span>  
  
|<span data-ttu-id="47a3b-134">Öğe</span><span class="sxs-lookup"><span data-stu-id="47a3b-134">Element</span></span>|<span data-ttu-id="47a3b-135">Açıklama</span><span class="sxs-lookup"><span data-stu-id="47a3b-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="47a3b-136">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="47a3b-136">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="47a3b-137">Bu öğe, standart ve özel bağlamalar koleksiyonunu tutar.</span><span class="sxs-lookup"><span data-stu-id="47a3b-137">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="47a3b-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="47a3b-138">See also</span></span>
- <xref:System.ServiceModel.Configuration.MexTcpBindingElement>
- <xref:System.ServiceModel.Description.MetadataExchangeBindings.CreateMexTcpBinding%2A>
- [<span data-ttu-id="47a3b-139">Nasıl yapılır: Bir yapılandırma dosyası kullanarak bir hizmet için meta verileri yayımlama</span><span class="sxs-lookup"><span data-stu-id="47a3b-139">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [<span data-ttu-id="47a3b-140">Özel Bağlama Üzerinden Meta Veri Yayımlama ve Alma</span><span class="sxs-lookup"><span data-stu-id="47a3b-140">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../../../docs/framework/wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)
- [<span data-ttu-id="47a3b-141">Meta Veriler</span><span class="sxs-lookup"><span data-stu-id="47a3b-141">Metadata</span></span>](../../../../../docs/framework/wcf/feature-details/metadata.md)
- [<span data-ttu-id="47a3b-142">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="47a3b-142">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="47a3b-143">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="47a3b-143">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="47a3b-144">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="47a3b-144">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="47a3b-145">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="47a3b-145">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
