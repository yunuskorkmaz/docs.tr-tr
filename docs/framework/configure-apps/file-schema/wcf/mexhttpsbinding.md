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
ms.workload: dotnet
ms.openlocfilehash: a6725741e6e0e67f3d26dc3bc1e83a57f6fcd430
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="ltmexhttpsbindinggt"></a><span data-ttu-id="2fd25-102">&lt;mexHttpsBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="2fd25-102">&lt;mexHttpsBinding&gt;</span></span>
<span data-ttu-id="2fd25-103">HTTPS üzerinden WS-MetadataExchange (WS-MEX) ileti değişimi için kullanılan bir bağlama ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="2fd25-103">Specifies the settings for a binding used for the WS-MetadataExchange (WS-MEX) message exchange over HTTPS.</span></span>  
  
 <span data-ttu-id="2fd25-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="2fd25-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="2fd25-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="2fd25-105">\<bindings></span></span>  
<span data-ttu-id="2fd25-106">\<mexHttpsBinding></span><span class="sxs-lookup"><span data-stu-id="2fd25-106">\<mexHttpsBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2fd25-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2fd25-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2fd25-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="2fd25-108">Attributes and Elements</span></span>  
 <span data-ttu-id="2fd25-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="2fd25-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2fd25-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="2fd25-110">Attributes</span></span>  
  
|<span data-ttu-id="2fd25-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="2fd25-111">Attribute</span></span>|<span data-ttu-id="2fd25-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2fd25-112">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="2fd25-113">A <xref:System.TimeSpan> bir kapatma işlemi tamamlamak sağlanan zaman aralığı belirten değer.</span><span class="sxs-lookup"><span data-stu-id="2fd25-113">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="2fd25-114">Bu değer sıfırdan büyük veya eşit olmalıdır <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="2fd25-114">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="2fd25-115">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="2fd25-115">The default is 00:01:00.</span></span>|  
|`name`|<span data-ttu-id="2fd25-116">Bağlama yapılandırma adını içeren dize.</span><span class="sxs-lookup"><span data-stu-id="2fd25-116">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="2fd25-117">Bağlama için bir tanımlayıcı olarak kullanıldığından, bu değer benzersiz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2fd25-117">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="2fd25-118">Her bağlama sahip bir `name` ve `namespace` birlikte benzersiz olarak özniteliği hizmet meta verilerde tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="2fd25-118">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span> <span data-ttu-id="2fd25-119">Ayrıca, bu ad aynı türde bağlamaları arasında benzersizdir.</span><span class="sxs-lookup"><span data-stu-id="2fd25-119">In addition, this name is unique among bindings of the same type.</span></span> <span data-ttu-id="2fd25-120">İle başlayarak [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bağlamalar ve davranışları olmayan bir adı olması için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="2fd25-120">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="2fd25-121">Varsayılan yapılandırma ve adsız bağlamalar ve davranışları hakkında daha fazla bilgi için bkz: [Basitleştirilmiş yapılandırma](../../../../../docs/framework/wcf/simplified-configuration.md) ve [WCF hizmetleri için Basitleştirilmiş yapılandırma](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="2fd25-121">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="2fd25-122">A <xref:System.TimeSpan> tamamlamak açık işlem için sağlanan zaman aralığını belirten değer.</span><span class="sxs-lookup"><span data-stu-id="2fd25-122">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="2fd25-123">Bu değer sıfırdan büyük veya eşit olmalıdır <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="2fd25-123">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="2fd25-124">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="2fd25-124">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="2fd25-125">A <xref:System.TimeSpan> bir alma işleminin tamamlanması için sağlanan zaman aralığı belirten değer.</span><span class="sxs-lookup"><span data-stu-id="2fd25-125">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="2fd25-126">Bu değer sıfırdan büyük veya eşit olmalıdır <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="2fd25-126">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="2fd25-127">Varsayılan değer 00:10: 00'dır.</span><span class="sxs-lookup"><span data-stu-id="2fd25-127">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="2fd25-128">A <xref:System.TimeSpan> bir gönderme işleminin tamamlanması için sağlanan zaman aralığı belirten değer.</span><span class="sxs-lookup"><span data-stu-id="2fd25-128">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="2fd25-129">Bu değer sıfırdan büyük veya eşit olmalıdır <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="2fd25-129">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="2fd25-130">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="2fd25-130">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2fd25-131">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="2fd25-131">Child Elements</span></span>  
 <span data-ttu-id="2fd25-132">Yok.</span><span class="sxs-lookup"><span data-stu-id="2fd25-132">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2fd25-133">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="2fd25-133">Parent Elements</span></span>  
  
|<span data-ttu-id="2fd25-134">Öğe</span><span class="sxs-lookup"><span data-stu-id="2fd25-134">Element</span></span>|<span data-ttu-id="2fd25-135">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2fd25-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2fd25-136">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="2fd25-136">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="2fd25-137">Bu öğe, standart ve özel bağlamaları koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="2fd25-137">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2fd25-138">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2fd25-138">Remarks</span></span>  
 <span data-ttu-id="2fd25-139">Bu bağlamanın temelde olduğu bir `WSHttpBinding` bağlaması, sertifikalar kullanılarak aktarım düzeyinde güvenlik destekler.</span><span class="sxs-lookup"><span data-stu-id="2fd25-139">This binding is essentially a `WSHttpBinding` binding that supports transport-level security using certificates.</span></span> <span data-ttu-id="2fd25-140">Yapılandırma ve bu tür, bir meta veri uç noktasının kullanma hakkında daha fazla bilgi için bkz: [nasıl yapılır: bir özel bir WS-Metadata değişimi bağlaması yapılandırma](../../../../../docs/framework/wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md), [nasıl yapılır: almak meta verileri üzerinden bir MEX olmayan bağlama](../../../../../docs/framework/wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md)ve örnek [özel güvenli meta veri uç noktasının](../../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md).</span><span class="sxs-lookup"><span data-stu-id="2fd25-140">For more information about configuring and using such a metadata endpoint, see [How to: Configure a Custom WS-Metadata Exchange Binding](../../../../../docs/framework/wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md), [How to: Retrieve Metadata Over a non-MEX Binding](../../../../../docs/framework/wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md), and the sample [Custom Secure Metadata Endpoint](../../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2fd25-141">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2fd25-141">See Also</span></span>  
 <xref:System.ServiceModel.Description.MetadataExchangeBindings.CreateMexHttpsBinding%2A>  
 <xref:System.ServiceModel.Configuration.MexHttpsBindingElement>  
 [<span data-ttu-id="2fd25-142">Nasıl yapılır: Yapılandırma Dosyası Kullanarak Bir Hizmet için Meta Verileri Yayımlama</span><span class="sxs-lookup"><span data-stu-id="2fd25-142">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)  
 [<span data-ttu-id="2fd25-143">Özel Bağlama Üzerinden Meta Veri Yayımlama ve Alma</span><span class="sxs-lookup"><span data-stu-id="2fd25-143">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../../../docs/framework/wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)  
 [<span data-ttu-id="2fd25-144">Nasıl yapılır: Özel Bir WS-Metadata Exchange Bağlaması Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="2fd25-144">How to: Configure a Custom WS-Metadata Exchange Binding</span></span>](../../../../../docs/framework/wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md)  
 [<span data-ttu-id="2fd25-145">Nasıl yapılır: MEX Olmayan Bağlama Üzerinden Meta Verileri Alma</span><span class="sxs-lookup"><span data-stu-id="2fd25-145">How to: Retrieve Metadata Over a non-MEX Binding</span></span>](../../../../../docs/framework/wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md)  
 [<span data-ttu-id="2fd25-146">Özel Güvenli Meta Veri Uç Noktaları</span><span class="sxs-lookup"><span data-stu-id="2fd25-146">Custom Secure Metadata Endpoint</span></span>](../../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md)  
 [<span data-ttu-id="2fd25-147">Meta Veriler</span><span class="sxs-lookup"><span data-stu-id="2fd25-147">Metadata</span></span>](../../../../../docs/framework/wcf/feature-details/metadata.md)  
 [<span data-ttu-id="2fd25-148">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="2fd25-148">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="2fd25-149">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="2fd25-149">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="2fd25-150">Windows Communication Foundation Hizmetleri ve istemcileri yapılandırmak için bağlamaları kullanma</span><span class="sxs-lookup"><span data-stu-id="2fd25-150">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="2fd25-151">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="2fd25-151">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
