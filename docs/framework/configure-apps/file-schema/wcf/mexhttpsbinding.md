---
title: <mexHttpsBinding>
ms.date: 03/30/2017
ms.assetid: f2ed3774-78b9-4a15-b79b-655f1ad68b86
ms.openlocfilehash: 4e96c28ac9b372092d06538d24d165dde6c5fe48
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59203138"
---
# <a name="mexhttpsbinding"></a><span data-ttu-id="e13ad-101">\<mexHttpsBinding></span><span class="sxs-lookup"><span data-stu-id="e13ad-101">\<mexHttpsBinding></span></span>
<span data-ttu-id="e13ad-102">HTTPS üzerinden WS-MetadataExchange (WS-MEX) ileti değişimi için kullanılan bir bağlama için olan ayarları belirler.</span><span class="sxs-lookup"><span data-stu-id="e13ad-102">Specifies the settings for a binding used for the WS-MetadataExchange (WS-MEX) message exchange over HTTPS.</span></span>  
  
 <span data-ttu-id="e13ad-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="e13ad-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="e13ad-104">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="e13ad-104">\<bindings></span></span>  
<span data-ttu-id="e13ad-105">\<mexHttpsBinding></span><span class="sxs-lookup"><span data-stu-id="e13ad-105">\<mexHttpsBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e13ad-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e13ad-106">Syntax</span></span>  
  
```xml  
<mexHttpsBinding>
  <binding closeTimeout="TimeSpan"
            name="string"
            openTimeout="TimeSpan"
            receiveTimeout="TimeSpan"
            sendTimeout="TimeSpan">
  </binding>
</mexHttpsBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e13ad-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="e13ad-107">Attributes and Elements</span></span>  
 <span data-ttu-id="e13ad-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e13ad-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e13ad-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e13ad-109">Attributes</span></span>  
  
|<span data-ttu-id="e13ad-110">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="e13ad-110">Attribute</span></span>|<span data-ttu-id="e13ad-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e13ad-111">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="e13ad-112">A <xref:System.TimeSpan> bir kapatma işlemi tamamlamak sağlanan zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="e13ad-112">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="e13ad-113">Bu değer, büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="e13ad-113">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="e13ad-114">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="e13ad-114">The default is 00:01:00.</span></span>|  
|`name`|<span data-ttu-id="e13ad-115">Bağlama yapılandırma adını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="e13ad-115">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="e13ad-116">Bağlama için bir tanımlayıcı olarak kullanıldığından, bu değer benzersiz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e13ad-116">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="e13ad-117">Her bağlama sahip bir `name` ve `namespace` birlikte benzersiz özniteliği hizmetinin meta verilerde tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="e13ad-117">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span> <span data-ttu-id="e13ad-118">Ayrıca, bu ad aynı türdeki bağlamaları arasında benzersizdir.</span><span class="sxs-lookup"><span data-stu-id="e13ad-118">In addition, this name is unique among bindings of the same type.</span></span> <span data-ttu-id="e13ad-119">İle başlayarak [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bağlamalar ve davranışları için gerekli değildir bir ada sahip.</span><span class="sxs-lookup"><span data-stu-id="e13ad-119">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="e13ad-120">Varsayılan yapılandırma ve adsız bağlamaları ve davranışları hakkında daha fazla bilgi için bkz: [Basitleştirilmiş yapılandırma](../../../../../docs/framework/wcf/simplified-configuration.md) ve [WCF hizmetleri için Basitleştirilmiş yapılandırma](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="e13ad-120">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="e13ad-121">A <xref:System.TimeSpan> tamamlamak açık işlem için sağlanan zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="e13ad-121">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="e13ad-122">Bu değer, büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="e13ad-122">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="e13ad-123">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="e13ad-123">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="e13ad-124">A <xref:System.TimeSpan> tamamlamak alma işlemi için sağlanan zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="e13ad-124">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="e13ad-125">Bu değer, büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="e13ad-125">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="e13ad-126">Varsayılan değer 00:10:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="e13ad-126">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="e13ad-127">A <xref:System.TimeSpan> tamamlamak bir gönderme işlemi için sağlanan zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="e13ad-127">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="e13ad-128">Bu değer, büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="e13ad-128">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="e13ad-129">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="e13ad-129">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e13ad-130">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="e13ad-130">Child Elements</span></span>  
 <span data-ttu-id="e13ad-131">Yok.</span><span class="sxs-lookup"><span data-stu-id="e13ad-131">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e13ad-132">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="e13ad-132">Parent Elements</span></span>  
  
|<span data-ttu-id="e13ad-133">Öğe</span><span class="sxs-lookup"><span data-stu-id="e13ad-133">Element</span></span>|<span data-ttu-id="e13ad-134">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e13ad-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e13ad-135">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="e13ad-135">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="e13ad-136">Bu öğe, standart ve özel bağlamalar koleksiyonunu tutar.</span><span class="sxs-lookup"><span data-stu-id="e13ad-136">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e13ad-137">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e13ad-137">Remarks</span></span>  
 <span data-ttu-id="e13ad-138">Bu bağlamanın temelde olduğu bir `WSHttpBinding` bağlama aktarım düzeyi güvenlik sertifikaları kullanarak destekler.</span><span class="sxs-lookup"><span data-stu-id="e13ad-138">This binding is essentially a `WSHttpBinding` binding that supports transport-level security using certificates.</span></span> <span data-ttu-id="e13ad-139">Yapılandırma ve böyle bir meta veri uç noktası kullanma hakkında daha fazla bilgi için bkz. [nasıl yapılır: Yapılandırma özel bir WS-Metadata değişimi bağlaması](../../../../../docs/framework/wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md), [nasıl yapılır: Bağlama üzerinden meta verileri bir olmayan - MEX almak](../../../../../docs/framework/wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md)ve örnek [özel güvenli meta veri uç noktası](../../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md).</span><span class="sxs-lookup"><span data-stu-id="e13ad-139">For more information about configuring and using such a metadata endpoint, see [How to: Configure a Custom WS-Metadata Exchange Binding](../../../../../docs/framework/wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md), [How to: Retrieve Metadata Over a non-MEX Binding](../../../../../docs/framework/wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md), and the sample [Custom Secure Metadata Endpoint](../../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e13ad-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e13ad-140">See also</span></span>

- <xref:System.ServiceModel.Description.MetadataExchangeBindings.CreateMexHttpsBinding%2A>
- <xref:System.ServiceModel.Configuration.MexHttpsBindingElement>
- [<span data-ttu-id="e13ad-141">Nasıl yapılır: Bir yapılandırma dosyası kullanarak bir hizmet için meta verileri yayımlama</span><span class="sxs-lookup"><span data-stu-id="e13ad-141">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [<span data-ttu-id="e13ad-142">Özel Bağlama Üzerinden Meta Veri Yayımlama ve Alma</span><span class="sxs-lookup"><span data-stu-id="e13ad-142">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../../../docs/framework/wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)
- [<span data-ttu-id="e13ad-143">Nasıl yapılır: Yapılandırma özel bir WS-Metadata değişimi bağlaması</span><span class="sxs-lookup"><span data-stu-id="e13ad-143">How to: Configure a Custom WS-Metadata Exchange Binding</span></span>](../../../../../docs/framework/wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md)
- [<span data-ttu-id="e13ad-144">Nasıl yapılır: Bağlama üzerinden meta verileri bir olmayan - MEX alma</span><span class="sxs-lookup"><span data-stu-id="e13ad-144">How to: Retrieve Metadata Over a non-MEX Binding</span></span>](../../../../../docs/framework/wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md)
- [<span data-ttu-id="e13ad-145">Özel Güvenli Meta Veri Uç Noktaları</span><span class="sxs-lookup"><span data-stu-id="e13ad-145">Custom Secure Metadata Endpoint</span></span>](../../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md)
- [<span data-ttu-id="e13ad-146">Meta Veriler</span><span class="sxs-lookup"><span data-stu-id="e13ad-146">Metadata</span></span>](../../../../../docs/framework/wcf/feature-details/metadata.md)
- [<span data-ttu-id="e13ad-147">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="e13ad-147">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="e13ad-148">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="e13ad-148">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="e13ad-149">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="e13ad-149">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="e13ad-150">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="e13ad-150">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
