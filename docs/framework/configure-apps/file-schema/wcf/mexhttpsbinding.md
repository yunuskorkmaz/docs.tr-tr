---
title: '&lt;mexHttpsBinding&gt;'
ms.date: 03/30/2017
ms.assetid: f2ed3774-78b9-4a15-b79b-655f1ad68b86
ms.openlocfilehash: e39a4e1e6b1b2346f3a6e0ca36d91d3719009be1
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54151923"
---
# <a name="ltmexhttpsbindinggt"></a><span data-ttu-id="773c0-102">&lt;mexHttpsBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="773c0-102">&lt;mexHttpsBinding&gt;</span></span>
<span data-ttu-id="773c0-103">HTTPS üzerinden WS-MetadataExchange (WS-MEX) ileti değişimi için kullanılan bir bağlama için olan ayarları belirler.</span><span class="sxs-lookup"><span data-stu-id="773c0-103">Specifies the settings for a binding used for the WS-MetadataExchange (WS-MEX) message exchange over HTTPS.</span></span>  
  
 <span data-ttu-id="773c0-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="773c0-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="773c0-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="773c0-105">\<bindings></span></span>  
<span data-ttu-id="773c0-106">\<mexHttpsBinding></span><span class="sxs-lookup"><span data-stu-id="773c0-106">\<mexHttpsBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="773c0-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="773c0-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="773c0-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="773c0-108">Attributes and Elements</span></span>  
 <span data-ttu-id="773c0-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="773c0-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="773c0-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="773c0-110">Attributes</span></span>  
  
|<span data-ttu-id="773c0-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="773c0-111">Attribute</span></span>|<span data-ttu-id="773c0-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="773c0-112">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="773c0-113">A <xref:System.TimeSpan> bir kapatma işlemi tamamlamak sağlanan zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="773c0-113">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="773c0-114">Bu değer, büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="773c0-114">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="773c0-115">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="773c0-115">The default is 00:01:00.</span></span>|  
|`name`|<span data-ttu-id="773c0-116">Bağlama yapılandırma adını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="773c0-116">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="773c0-117">Bağlama için bir tanımlayıcı olarak kullanıldığından, bu değer benzersiz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="773c0-117">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="773c0-118">Her bağlama sahip bir `name` ve `namespace` birlikte benzersiz özniteliği hizmetinin meta verilerde tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="773c0-118">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span> <span data-ttu-id="773c0-119">Ayrıca, bu ad aynı türdeki bağlamaları arasında benzersizdir.</span><span class="sxs-lookup"><span data-stu-id="773c0-119">In addition, this name is unique among bindings of the same type.</span></span> <span data-ttu-id="773c0-120">İle başlayarak [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bağlamalar ve davranışları için gerekli değildir bir ada sahip.</span><span class="sxs-lookup"><span data-stu-id="773c0-120">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="773c0-121">Varsayılan yapılandırma ve adsız bağlamaları ve davranışları hakkında daha fazla bilgi için bkz: [Basitleştirilmiş yapılandırma](../../../../../docs/framework/wcf/simplified-configuration.md) ve [WCF hizmetleri için Basitleştirilmiş yapılandırma](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="773c0-121">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="773c0-122">A <xref:System.TimeSpan> tamamlamak açık işlem için sağlanan zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="773c0-122">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="773c0-123">Bu değer, büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="773c0-123">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="773c0-124">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="773c0-124">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="773c0-125">A <xref:System.TimeSpan> tamamlamak alma işlemi için sağlanan zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="773c0-125">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="773c0-126">Bu değer, büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="773c0-126">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="773c0-127">Varsayılan değer 00:10:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="773c0-127">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="773c0-128">A <xref:System.TimeSpan> tamamlamak bir gönderme işlemi için sağlanan zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="773c0-128">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="773c0-129">Bu değer, büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="773c0-129">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="773c0-130">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="773c0-130">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="773c0-131">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="773c0-131">Child Elements</span></span>  
 <span data-ttu-id="773c0-132">Yok.</span><span class="sxs-lookup"><span data-stu-id="773c0-132">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="773c0-133">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="773c0-133">Parent Elements</span></span>  
  
|<span data-ttu-id="773c0-134">Öğe</span><span class="sxs-lookup"><span data-stu-id="773c0-134">Element</span></span>|<span data-ttu-id="773c0-135">Açıklama</span><span class="sxs-lookup"><span data-stu-id="773c0-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="773c0-136">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="773c0-136">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="773c0-137">Bu öğe, standart ve özel bağlamalar koleksiyonunu tutar.</span><span class="sxs-lookup"><span data-stu-id="773c0-137">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="773c0-138">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="773c0-138">Remarks</span></span>  
 <span data-ttu-id="773c0-139">Bu bağlamanın temelde olduğu bir `WSHttpBinding` bağlama aktarım düzeyi güvenlik sertifikaları kullanarak destekler.</span><span class="sxs-lookup"><span data-stu-id="773c0-139">This binding is essentially a `WSHttpBinding` binding that supports transport-level security using certificates.</span></span> <span data-ttu-id="773c0-140">Yapılandırma ve böyle bir meta veri uç noktası kullanma hakkında daha fazla bilgi için bkz. [nasıl yapılır: Yapılandırma özel bir WS-Metadata değişimi bağlaması](../../../../../docs/framework/wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md), [nasıl yapılır: Bağlama üzerinden meta verileri bir olmayan - MEX almak](../../../../../docs/framework/wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md)ve örnek [özel güvenli meta veri uç noktası](../../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md).</span><span class="sxs-lookup"><span data-stu-id="773c0-140">For more information about configuring and using such a metadata endpoint, see [How to: Configure a Custom WS-Metadata Exchange Binding](../../../../../docs/framework/wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md), [How to: Retrieve Metadata Over a non-MEX Binding](../../../../../docs/framework/wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md), and the sample [Custom Secure Metadata Endpoint](../../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="773c0-141">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="773c0-141">See Also</span></span>  
 <xref:System.ServiceModel.Description.MetadataExchangeBindings.CreateMexHttpsBinding%2A>  
 <xref:System.ServiceModel.Configuration.MexHttpsBindingElement>  
 [<span data-ttu-id="773c0-142">Nasıl yapılır: Bir yapılandırma dosyası kullanarak bir hizmet için meta verileri yayımlama</span><span class="sxs-lookup"><span data-stu-id="773c0-142">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)  
 [<span data-ttu-id="773c0-143">Özel Bağlama Üzerinden Meta Veri Yayımlama ve Alma</span><span class="sxs-lookup"><span data-stu-id="773c0-143">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../../../docs/framework/wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)  
 [<span data-ttu-id="773c0-144">Nasıl yapılır: Yapılandırma özel bir WS-Metadata değişimi bağlaması</span><span class="sxs-lookup"><span data-stu-id="773c0-144">How to: Configure a Custom WS-Metadata Exchange Binding</span></span>](../../../../../docs/framework/wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md)  
 [<span data-ttu-id="773c0-145">Nasıl yapılır: Bağlama üzerinden meta verileri bir olmayan - MEX alma</span><span class="sxs-lookup"><span data-stu-id="773c0-145">How to: Retrieve Metadata Over a non-MEX Binding</span></span>](../../../../../docs/framework/wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md)  
 [<span data-ttu-id="773c0-146">Özel Güvenli Meta Veri Uç Noktaları</span><span class="sxs-lookup"><span data-stu-id="773c0-146">Custom Secure Metadata Endpoint</span></span>](../../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md)  
 [<span data-ttu-id="773c0-147">Meta Veriler</span><span class="sxs-lookup"><span data-stu-id="773c0-147">Metadata</span></span>](../../../../../docs/framework/wcf/feature-details/metadata.md)  
 [<span data-ttu-id="773c0-148">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="773c0-148">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="773c0-149">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="773c0-149">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="773c0-150">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="773c0-150">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [<span data-ttu-id="773c0-151">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="773c0-151">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
