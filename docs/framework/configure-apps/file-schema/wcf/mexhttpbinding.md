---
title: <mexHttpBinding>
ms.date: 03/30/2017
ms.assetid: e50b2e1f-9668-41a5-8077-dee7abff9f0f
ms.openlocfilehash: 1aa9512c3d0d52f8cc3c7bd7b82bcfd37c418ce7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61773457"
---
# <a name="mexhttpbinding"></a><span data-ttu-id="952eb-101">\<mexHttpBinding></span><span class="sxs-lookup"><span data-stu-id="952eb-101">\<mexHttpBinding></span></span>
<span data-ttu-id="952eb-102">HTTP üzerinde WS-MetadataExchange (WS-MEX) ileti değişimi için kullanılan bir bağlama için olan ayarları belirler.</span><span class="sxs-lookup"><span data-stu-id="952eb-102">Specifies the settings for a binding used for the WS-MetadataExchange (WS-MEX) message exchange over HTTP.</span></span>  
  
 <span data-ttu-id="952eb-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="952eb-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="952eb-104">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="952eb-104">\<bindings></span></span>  
<span data-ttu-id="952eb-105">\<mexHttpBinding></span><span class="sxs-lookup"><span data-stu-id="952eb-105">\<mexHttpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="952eb-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="952eb-106">Syntax</span></span>  
  
```xml  
<mexHttpBinding>
  <binding closeTimeout="TimeSpan"
           name="string"
           openTimeout="TimeSpan"
           receiveTimeout="TimeSpan"
           sendTimeout="TimeSpan">
  </binding>
</mexHttpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="952eb-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="952eb-107">Attributes and Elements</span></span>  
 <span data-ttu-id="952eb-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="952eb-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="952eb-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="952eb-109">Attributes</span></span>  
  
|<span data-ttu-id="952eb-110">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="952eb-110">Attribute</span></span>|<span data-ttu-id="952eb-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="952eb-111">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="952eb-112">A <xref:System.TimeSpan> bir kapatma işlemi tamamlamak sağlanan zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="952eb-112">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="952eb-113">Bu değer, büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="952eb-113">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="952eb-114">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="952eb-114">The default is 00:01:00.</span></span>|  
|`name`|<span data-ttu-id="952eb-115">Bağlama yapılandırma adını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="952eb-115">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="952eb-116">Bağlama için bir tanımlayıcı olarak kullanıldığından, bu değer benzersiz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="952eb-116">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="952eb-117">Her bağlama sahip bir `name` ve `namespace` birlikte benzersiz özniteliği hizmetinin meta verilerde tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="952eb-117">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span> <span data-ttu-id="952eb-118">Ayrıca, bu ad aynı türdeki bağlamaları arasında benzersizdir.</span><span class="sxs-lookup"><span data-stu-id="952eb-118">In addition, this name is unique among bindings of the same type.</span></span> <span data-ttu-id="952eb-119">İle başlayarak [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bağlamalar ve davranışları için gerekli değildir bir ada sahip.</span><span class="sxs-lookup"><span data-stu-id="952eb-119">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="952eb-120">Varsayılan yapılandırma ve adsız bağlamaları ve davranışları hakkında daha fazla bilgi için bkz: [Basitleştirilmiş yapılandırma](../../../../../docs/framework/wcf/simplified-configuration.md) ve [WCF hizmetleri için Basitleştirilmiş yapılandırma](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="952eb-120">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="952eb-121">A <xref:System.TimeSpan> tamamlamak açık işlem için sağlanan zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="952eb-121">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="952eb-122">Bu değer, büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="952eb-122">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="952eb-123">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="952eb-123">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="952eb-124">A <xref:System.TimeSpan> tamamlamak alma işlemi için sağlanan zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="952eb-124">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="952eb-125">Bu değer, büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="952eb-125">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="952eb-126">Varsayılan değer 00:10:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="952eb-126">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="952eb-127">A <xref:System.TimeSpan> tamamlamak bir gönderme işlemi için sağlanan zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="952eb-127">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="952eb-128">Bu değer, büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="952eb-128">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="952eb-129">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="952eb-129">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="952eb-130">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="952eb-130">Child Elements</span></span>  
 <span data-ttu-id="952eb-131">Yok.</span><span class="sxs-lookup"><span data-stu-id="952eb-131">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="952eb-132">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="952eb-132">Parent Elements</span></span>  
  
|<span data-ttu-id="952eb-133">Öğe</span><span class="sxs-lookup"><span data-stu-id="952eb-133">Element</span></span>|<span data-ttu-id="952eb-134">Açıklama</span><span class="sxs-lookup"><span data-stu-id="952eb-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="952eb-135">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="952eb-135">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="952eb-136">Bu öğe, standart ve özel bağlamalar koleksiyonunu tutar.</span><span class="sxs-lookup"><span data-stu-id="952eb-136">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="952eb-137">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="952eb-137">Remarks</span></span>  
 <span data-ttu-id="952eb-138">Bu bağlamanın temelde olduğu bir `WSHttpBinding` devre dışı güvenlikle bağlama.</span><span class="sxs-lookup"><span data-stu-id="952eb-138">This binding is essentially a `WSHttpBinding` binding with security disabled.</span></span> <span data-ttu-id="952eb-139">Bu, çoğu meta veri isteklerini destekler.</span><span class="sxs-lookup"><span data-stu-id="952eb-139">It supports most metadata requests.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="952eb-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="952eb-140">See also</span></span>

- <xref:System.ServiceModel.Description.MetadataExchangeBindings.CreateMexHttpBinding%2A>
- <xref:System.ServiceModel.Configuration.MexHttpBindingElement>
- [<span data-ttu-id="952eb-141">Nasıl yapılır: Bir yapılandırma dosyası kullanarak bir hizmet için meta verileri yayımlama</span><span class="sxs-lookup"><span data-stu-id="952eb-141">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [<span data-ttu-id="952eb-142">Özel Bağlama Üzerinden Meta Veri Yayımlama ve Alma</span><span class="sxs-lookup"><span data-stu-id="952eb-142">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../../../docs/framework/wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)
- [<span data-ttu-id="952eb-143">Meta Veriler</span><span class="sxs-lookup"><span data-stu-id="952eb-143">Metadata</span></span>](../../../../../docs/framework/wcf/feature-details/metadata.md)
- [<span data-ttu-id="952eb-144">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="952eb-144">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="952eb-145">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="952eb-145">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="952eb-146">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="952eb-146">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="952eb-147">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="952eb-147">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
