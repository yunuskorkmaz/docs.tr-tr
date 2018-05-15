---
title: '&lt;mexHttpBinding&gt;'
ms.date: 03/30/2017
ms.assetid: e50b2e1f-9668-41a5-8077-dee7abff9f0f
ms.openlocfilehash: 5822064af711c1a2c16bddfd142f415541b9604d
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="ltmexhttpbindinggt"></a><span data-ttu-id="6c1b6-102">&lt;mexHttpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="6c1b6-102">&lt;mexHttpBinding&gt;</span></span>
<span data-ttu-id="6c1b6-103">HTTP üzerinden WS-MetadataExchange (WS-MEX) ileti değişimi için kullanılan bir bağlama ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="6c1b6-103">Specifies the settings for a binding used for the WS-MetadataExchange (WS-MEX) message exchange over HTTP.</span></span>  
  
 <span data-ttu-id="6c1b6-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="6c1b6-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="6c1b6-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="6c1b6-105">\<bindings></span></span>  
<span data-ttu-id="6c1b6-106">\<mexHttpBinding></span><span class="sxs-lookup"><span data-stu-id="6c1b6-106">\<mexHttpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c1b6-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6c1b6-107">Syntax</span></span>  
  
```xml  
<mexHttpBinding>  
   <binding   
       closeTimeout="TimeSpan"   
       name="string"   
       openTimeout="TimeSpan"   
       receiveTimeout="TimeSpan"  
       sendTimeout="TimeSpan">  
   </binding>  
</mexHttpBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6c1b6-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="6c1b6-108">Attributes and Elements</span></span>  
 <span data-ttu-id="6c1b6-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6c1b6-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6c1b6-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="6c1b6-110">Attributes</span></span>  
  
|<span data-ttu-id="6c1b6-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="6c1b6-111">Attribute</span></span>|<span data-ttu-id="6c1b6-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6c1b6-112">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="6c1b6-113">A <xref:System.TimeSpan> bir kapatma işlemi tamamlamak sağlanan zaman aralığı belirten değer.</span><span class="sxs-lookup"><span data-stu-id="6c1b6-113">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="6c1b6-114">Bu değer sıfırdan büyük veya eşit olmalıdır <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="6c1b6-114">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="6c1b6-115">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="6c1b6-115">The default is 00:01:00.</span></span>|  
|`name`|<span data-ttu-id="6c1b6-116">Bağlama yapılandırma adını içeren dize.</span><span class="sxs-lookup"><span data-stu-id="6c1b6-116">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="6c1b6-117">Bağlama için bir tanımlayıcı olarak kullanıldığından, bu değer benzersiz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6c1b6-117">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="6c1b6-118">Her bağlama sahip bir `name` ve `namespace` birlikte benzersiz olarak özniteliği hizmet meta verilerde tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="6c1b6-118">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span> <span data-ttu-id="6c1b6-119">Ayrıca, bu ad aynı türde bağlamaları arasında benzersizdir.</span><span class="sxs-lookup"><span data-stu-id="6c1b6-119">In addition, this name is unique among bindings of the same type.</span></span> <span data-ttu-id="6c1b6-120">İle başlayarak [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bağlamalar ve davranışları olmayan bir adı olması için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="6c1b6-120">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="6c1b6-121">Varsayılan yapılandırma ve adsız bağlamalar ve davranışları hakkında daha fazla bilgi için bkz: [Basitleştirilmiş yapılandırma](../../../../../docs/framework/wcf/simplified-configuration.md) ve [WCF hizmetleri için Basitleştirilmiş yapılandırma](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="6c1b6-121">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="6c1b6-122">A <xref:System.TimeSpan> tamamlamak açık işlem için sağlanan zaman aralığını belirten değer.</span><span class="sxs-lookup"><span data-stu-id="6c1b6-122">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="6c1b6-123">Bu değer sıfırdan büyük veya eşit olmalıdır <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="6c1b6-123">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="6c1b6-124">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="6c1b6-124">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="6c1b6-125">A <xref:System.TimeSpan> bir alma işleminin tamamlanması için sağlanan zaman aralığı belirten değer.</span><span class="sxs-lookup"><span data-stu-id="6c1b6-125">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="6c1b6-126">Bu değer sıfırdan büyük veya eşit olmalıdır <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="6c1b6-126">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="6c1b6-127">Varsayılan değer 00:10: 00'dır.</span><span class="sxs-lookup"><span data-stu-id="6c1b6-127">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="6c1b6-128">A <xref:System.TimeSpan> bir gönderme işleminin tamamlanması için sağlanan zaman aralığı belirten değer.</span><span class="sxs-lookup"><span data-stu-id="6c1b6-128">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="6c1b6-129">Bu değer sıfırdan büyük veya eşit olmalıdır <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="6c1b6-129">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="6c1b6-130">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="6c1b6-130">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6c1b6-131">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="6c1b6-131">Child Elements</span></span>  
 <span data-ttu-id="6c1b6-132">Yok.</span><span class="sxs-lookup"><span data-stu-id="6c1b6-132">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6c1b6-133">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="6c1b6-133">Parent Elements</span></span>  
  
|<span data-ttu-id="6c1b6-134">Öğe</span><span class="sxs-lookup"><span data-stu-id="6c1b6-134">Element</span></span>|<span data-ttu-id="6c1b6-135">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6c1b6-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6c1b6-136">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="6c1b6-136">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="6c1b6-137">Bu öğe, standart ve özel bağlamaları koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="6c1b6-137">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6c1b6-138">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6c1b6-138">Remarks</span></span>  
 <span data-ttu-id="6c1b6-139">Bu bağlamanın temelde olduğu bir `WSHttpBinding` güvenliği devre dışı bağlama.</span><span class="sxs-lookup"><span data-stu-id="6c1b6-139">This binding is essentially a `WSHttpBinding` binding with security disabled.</span></span> <span data-ttu-id="6c1b6-140">Çoğu meta veri isteklerini destekler.</span><span class="sxs-lookup"><span data-stu-id="6c1b6-140">It supports most metadata requests.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c1b6-141">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6c1b6-141">See Also</span></span>  
 <xref:System.ServiceModel.Description.MetadataExchangeBindings.CreateMexHttpBinding%2A>  
 <xref:System.ServiceModel.Configuration.MexHttpBindingElement>  
 [<span data-ttu-id="6c1b6-142">Nasıl yapılır: Yapılandırma Dosyası Kullanarak Bir Hizmet için Meta Verileri Yayımlama</span><span class="sxs-lookup"><span data-stu-id="6c1b6-142">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)  
 [<span data-ttu-id="6c1b6-143">Özel Bağlama Üzerinden Meta Veri Yayımlama ve Alma</span><span class="sxs-lookup"><span data-stu-id="6c1b6-143">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../../../docs/framework/wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)  
 [<span data-ttu-id="6c1b6-144">Meta Veriler</span><span class="sxs-lookup"><span data-stu-id="6c1b6-144">Metadata</span></span>](../../../../../docs/framework/wcf/feature-details/metadata.md)  
 [<span data-ttu-id="6c1b6-145">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="6c1b6-145">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="6c1b6-146">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="6c1b6-146">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="6c1b6-147">Windows Communication Foundation Hizmetleri ve istemcileri yapılandırmak için bağlamaları kullanma</span><span class="sxs-lookup"><span data-stu-id="6c1b6-147">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="6c1b6-148">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="6c1b6-148">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
