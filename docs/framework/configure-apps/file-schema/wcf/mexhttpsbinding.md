---
title: '&lt;mexHttpsBinding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f2ed3774-78b9-4a15-b79b-655f1ad68b86
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4990965e364765628174f9e8765663c7a7df70d2
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="ltmexhttpsbindinggt"></a><span data-ttu-id="bffb3-102">&lt;mexHttpsBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="bffb3-102">&lt;mexHttpsBinding&gt;</span></span>
<span data-ttu-id="bffb3-103">HTTPS üzerinden WS-MetadataExchange (WS-MEX) ileti değişimi için kullanılan bir bağlama ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="bffb3-103">Specifies the settings for a binding used for the WS-MetadataExchange (WS-MEX) message exchange over HTTPS.</span></span>  
  
 <span data-ttu-id="bffb3-104">\<Sistem. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="bffb3-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="bffb3-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="bffb3-105">\<bindings></span></span>  
<span data-ttu-id="bffb3-106">\<mexHttpsBinding ></span><span class="sxs-lookup"><span data-stu-id="bffb3-106">\<mexHttpsBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bffb3-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bffb3-107">Syntax</span></span>  
  
```xml  
<mexHttpsBinding>  
   <binding   
       closeTimeout="TimeSpan"   
       name="string"   
       openTimeout="TimeSpan"   
       receiveTimeout="TimeSpan"  
       sendTimeout="TimeSpan">  
   </binding>  
</mexHttpsBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bffb3-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="bffb3-108">Attributes and Elements</span></span>  
 <span data-ttu-id="bffb3-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="bffb3-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bffb3-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="bffb3-110">Attributes</span></span>  
  
|<span data-ttu-id="bffb3-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="bffb3-111">Attribute</span></span>|<span data-ttu-id="bffb3-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bffb3-112">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="bffb3-113">A <xref:System.TimeSpan> bir kapatma işlemi tamamlamak sağlanan zaman aralığı belirten değer.</span><span class="sxs-lookup"><span data-stu-id="bffb3-113">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="bffb3-114">Bu değer sıfırdan büyük veya eşit olmalıdır <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="bffb3-114">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="bffb3-115">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="bffb3-115">The default is 00:01:00.</span></span>|  
|`name`|<span data-ttu-id="bffb3-116">Bağlama yapılandırma adını içeren dize.</span><span class="sxs-lookup"><span data-stu-id="bffb3-116">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="bffb3-117">Bağlama için bir tanımlayıcı olarak kullanıldığından, bu değer benzersiz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="bffb3-117">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="bffb3-118">Her bağlama sahip bir `name` ve `namespace` birlikte benzersiz olarak özniteliği hizmet meta verilerde tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="bffb3-118">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span> <span data-ttu-id="bffb3-119">Ayrıca, bu ad aynı türde bağlamaları arasında benzersizdir.</span><span class="sxs-lookup"><span data-stu-id="bffb3-119">In addition, this name is unique among bindings of the same type.</span></span> <span data-ttu-id="bffb3-120">İle başlayarak [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bağlamalar ve davranışları olmayan bir adı olması için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="bffb3-120">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="bffb3-121">Varsayılan yapılandırma ve adsız bağlamalar ve davranışları hakkında daha fazla bilgi için bkz: [Basitleştirilmiş yapılandırma](../../../../../docs/framework/wcf/simplified-configuration.md) ve [WCF hizmetleri için Basitleştirilmiş yapılandırma](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="bffb3-121">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="bffb3-122">A <xref:System.TimeSpan> tamamlamak açık işlem için sağlanan zaman aralığını belirten değer.</span><span class="sxs-lookup"><span data-stu-id="bffb3-122">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="bffb3-123">Bu değer sıfırdan büyük veya eşit olmalıdır <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="bffb3-123">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="bffb3-124">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="bffb3-124">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="bffb3-125">A <xref:System.TimeSpan> bir alma işleminin tamamlanması için sağlanan zaman aralığı belirten değer.</span><span class="sxs-lookup"><span data-stu-id="bffb3-125">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="bffb3-126">Bu değer sıfırdan büyük veya eşit olmalıdır <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="bffb3-126">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="bffb3-127">Varsayılan değer 00:10: 00'dır.</span><span class="sxs-lookup"><span data-stu-id="bffb3-127">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="bffb3-128">A <xref:System.TimeSpan> bir gönderme işleminin tamamlanması için sağlanan zaman aralığı belirten değer.</span><span class="sxs-lookup"><span data-stu-id="bffb3-128">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="bffb3-129">Bu değer sıfırdan büyük veya eşit olmalıdır <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="bffb3-129">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="bffb3-130">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="bffb3-130">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bffb3-131">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="bffb3-131">Child Elements</span></span>  
 <span data-ttu-id="bffb3-132">Yok.</span><span class="sxs-lookup"><span data-stu-id="bffb3-132">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bffb3-133">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="bffb3-133">Parent Elements</span></span>  
  
|<span data-ttu-id="bffb3-134">Öğe</span><span class="sxs-lookup"><span data-stu-id="bffb3-134">Element</span></span>|<span data-ttu-id="bffb3-135">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bffb3-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bffb3-136">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="bffb3-136">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="bffb3-137">Bu öğe, standart ve özel bağlamaları koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="bffb3-137">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bffb3-138">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bffb3-138">Remarks</span></span>  
 <span data-ttu-id="bffb3-139">Bu bağlamanın temelde olduğu bir `WSHttpBinding` bağlaması, sertifikalar kullanılarak aktarım düzeyinde güvenlik destekler.</span><span class="sxs-lookup"><span data-stu-id="bffb3-139">This binding is essentially a `WSHttpBinding` binding that supports transport-level security using certificates.</span></span> <span data-ttu-id="bffb3-140">Yapılandırma ve bu tür, bir meta veri uç noktasının kullanma hakkında daha fazla bilgi için bkz: [nasıl yapılır: bir özel bir WS-Metadata değişimi bağlaması yapılandırma](../../../../../docs/framework/wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md), [nasıl yapılır: almak meta verileri üzerinden bir MEX olmayan bağlama](../../../../../docs/framework/wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md)ve örnek [özel güvenli meta veri uç noktasının](../../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md).</span><span class="sxs-lookup"><span data-stu-id="bffb3-140">For more information about configuring and using such a metadata endpoint, see [How to: Configure a Custom WS-Metadata Exchange Binding](../../../../../docs/framework/wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md), [How to: Retrieve Metadata Over a non-MEX Binding](../../../../../docs/framework/wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md), and the sample [Custom Secure Metadata Endpoint](../../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bffb3-141">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="bffb3-141">See Also</span></span>  
 <xref:System.ServiceModel.Description.MetadataExchangeBindings.CreateMexHttpsBinding%2A>  
 <xref:System.ServiceModel.Configuration.MexHttpsBindingElement>  
 [<span data-ttu-id="bffb3-142">Nasıl yapılır: bir yapılandırma dosyası kullanarak bir hizmet için meta verileri yayımlama</span><span class="sxs-lookup"><span data-stu-id="bffb3-142">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)  
 [<span data-ttu-id="bffb3-143">Yayımlama ve özel bağlama üzerinden meta verileri alma</span><span class="sxs-lookup"><span data-stu-id="bffb3-143">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../../../docs/framework/wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)  
 [<span data-ttu-id="bffb3-144">Nasıl yapılır: yapılandırma özel bir WS-Metadata değişimi bağlaması</span><span class="sxs-lookup"><span data-stu-id="bffb3-144">How to: Configure a Custom WS-Metadata Exchange Binding</span></span>](../../../../../docs/framework/wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md)  
 [<span data-ttu-id="bffb3-145">Nasıl yapılır: meta verileri üzerinden alma bir MEX olmayan bağlama</span><span class="sxs-lookup"><span data-stu-id="bffb3-145">How to: Retrieve Metadata Over a non-MEX Binding</span></span>](../../../../../docs/framework/wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md)  
 [<span data-ttu-id="bffb3-146">Özel güvenli meta veri uç noktası</span><span class="sxs-lookup"><span data-stu-id="bffb3-146">Custom Secure Metadata Endpoint</span></span>](../../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md)  
 [<span data-ttu-id="bffb3-147">Meta veriler</span><span class="sxs-lookup"><span data-stu-id="bffb3-147">Metadata</span></span>](../../../../../docs/framework/wcf/feature-details/metadata.md)  
 [<span data-ttu-id="bffb3-148">Bağlamaları</span><span class="sxs-lookup"><span data-stu-id="bffb3-148">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="bffb3-149">Sistem tarafından sağlanan bağlamaları yapılandırma</span><span class="sxs-lookup"><span data-stu-id="bffb3-149">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="bffb3-150">Windows Communication Foundation Hizmetleri ve istemcileri yapılandırmak için bağlamaları kullanma</span><span class="sxs-lookup"><span data-stu-id="bffb3-150">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="bffb3-151">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="bffb3-151">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
