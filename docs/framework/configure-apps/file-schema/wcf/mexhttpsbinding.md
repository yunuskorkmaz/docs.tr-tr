---
title: <mexHttpsBinding>
ms.date: 03/30/2017
ms.assetid: f2ed3774-78b9-4a15-b79b-655f1ad68b86
ms.openlocfilehash: 79c3c68d69bf3cf5a018e6cf62f34e5ec2ce0cd5
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738928"
---
# <a name="mexhttpsbinding"></a><span data-ttu-id="8b2fc-101">\<mexHttpsBinding ></span><span class="sxs-lookup"><span data-stu-id="8b2fc-101">\<mexHttpsBinding></span></span>
<span data-ttu-id="8b2fc-102">HTTPS üzerinde WS-MetadataExchange (WS-MEX) ileti değişimi için kullanılan bir bağlamanın ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="8b2fc-102">Specifies the settings for a binding used for the WS-MetadataExchange (WS-MEX) message exchange over HTTPS.</span></span>  
  
<span data-ttu-id="8b2fc-103">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="8b2fc-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="8b2fc-104">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="8b2fc-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="8b2fc-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bağlamaları >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="8b2fc-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="8b2fc-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<mexHttpsBinding >**</span><span class="sxs-lookup"><span data-stu-id="8b2fc-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<mexHttpsBinding>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b2fc-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8b2fc-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8b2fc-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="8b2fc-108">Attributes and Elements</span></span>  
 <span data-ttu-id="8b2fc-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8b2fc-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8b2fc-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="8b2fc-110">Attributes</span></span>  
  
|<span data-ttu-id="8b2fc-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="8b2fc-111">Attribute</span></span>|<span data-ttu-id="8b2fc-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8b2fc-112">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="8b2fc-113">Bir kapatma işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir <xref:System.TimeSpan> değeri.</span><span class="sxs-lookup"><span data-stu-id="8b2fc-113">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="8b2fc-114">Bu değer, <xref:System.TimeSpan.Zero>eşit veya ondan büyük olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8b2fc-114">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="8b2fc-115">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="8b2fc-115">The default is 00:01:00.</span></span>|  
|`name`|<span data-ttu-id="8b2fc-116">Bağlamanın yapılandırma adını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="8b2fc-116">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="8b2fc-117">Bağlama için bir kimlik olarak kullanıldığından, bu değer benzersiz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8b2fc-117">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="8b2fc-118">Her bağlamada bir `name` ve `namespace` özniteliği, hizmetin meta verilerinde benzersiz bir şekilde tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="8b2fc-118">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span> <span data-ttu-id="8b2fc-119">Ayrıca, bu ad aynı türdeki bağlamalar arasında benzersizdir.</span><span class="sxs-lookup"><span data-stu-id="8b2fc-119">In addition, this name is unique among bindings of the same type.</span></span> <span data-ttu-id="8b2fc-120">[!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)]başlayarak bağlamalar ve davranışları bir ada sahip olmak için gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="8b2fc-120">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="8b2fc-121">Varsayılan yapılandırma ve ad Less bağlamaları ve davranışları hakkında daha fazla bilgi için bkz. [WCF Hizmetleri Için](../../../wcf/samples/simplified-configuration-for-wcf-services.md) [Basitleştirilmiş yapılandırma](../../../wcf/simplified-configuration.md) ve Basitleştirilmiş yapılandırma.</span><span class="sxs-lookup"><span data-stu-id="8b2fc-121">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="8b2fc-122">Bir açık işlemin tamamlanabilmesi için belirtilen zaman aralığını belirten bir <xref:System.TimeSpan> değeri.</span><span class="sxs-lookup"><span data-stu-id="8b2fc-122">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="8b2fc-123">Bu değer, <xref:System.TimeSpan.Zero>eşit veya ondan büyük olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8b2fc-123">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="8b2fc-124">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="8b2fc-124">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="8b2fc-125">Alma işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir <xref:System.TimeSpan> değeri.</span><span class="sxs-lookup"><span data-stu-id="8b2fc-125">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="8b2fc-126">Bu değer, <xref:System.TimeSpan.Zero>eşit veya ondan büyük olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8b2fc-126">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="8b2fc-127">Varsayılan değer 00:10:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="8b2fc-127">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="8b2fc-128">Bir gönderme işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir <xref:System.TimeSpan> değeri.</span><span class="sxs-lookup"><span data-stu-id="8b2fc-128">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="8b2fc-129">Bu değer, <xref:System.TimeSpan.Zero>eşit veya ondan büyük olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8b2fc-129">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="8b2fc-130">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="8b2fc-130">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8b2fc-131">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="8b2fc-131">Child Elements</span></span>  
 <span data-ttu-id="8b2fc-132">Yok.</span><span class="sxs-lookup"><span data-stu-id="8b2fc-132">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8b2fc-133">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="8b2fc-133">Parent Elements</span></span>  
  
|<span data-ttu-id="8b2fc-134">Öğe</span><span class="sxs-lookup"><span data-stu-id="8b2fc-134">Element</span></span>|<span data-ttu-id="8b2fc-135">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8b2fc-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8b2fc-136">\<bindings ></span><span class="sxs-lookup"><span data-stu-id="8b2fc-136">\<bindings></span></span>](bindings.md)|<span data-ttu-id="8b2fc-137">Bu öğe, standart ve özel bağlamaların bir koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="8b2fc-137">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8b2fc-138">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8b2fc-138">Remarks</span></span>  
 <span data-ttu-id="8b2fc-139">Bu bağlama temel olarak, sertifikaları kullanarak aktarım düzeyi güvenliği destekleyen bir `WSHttpBinding` bağlamadır.</span><span class="sxs-lookup"><span data-stu-id="8b2fc-139">This binding is essentially a `WSHttpBinding` binding that supports transport-level security using certificates.</span></span> <span data-ttu-id="8b2fc-140">Bu tür bir meta veri uç noktası yapılandırma ve kullanma hakkında daha fazla bilgi için bkz. [nasıl yapılır: özel bir WS-Metadata Exchange bağlamayı yapılandırma](../../../wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md), [nasıl yapılır: meta verileri bir MEX olmayan bağlama üzerinden alma](../../../wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md)ve örnek [özel güvenli meta veri uç noktası](../../../wcf/samples/custom-secure-metadata-endpoint.md) .</span><span class="sxs-lookup"><span data-stu-id="8b2fc-140">For more information about configuring and using such a metadata endpoint, see [How to: Configure a Custom WS-Metadata Exchange Binding](../../../wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md), [How to: Retrieve Metadata Over a non-MEX Binding](../../../wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md), and the sample [Custom Secure Metadata Endpoint](../../../wcf/samples/custom-secure-metadata-endpoint.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b2fc-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8b2fc-141">See also</span></span>

- <xref:System.ServiceModel.Description.MetadataExchangeBindings.CreateMexHttpsBinding%2A>
- <xref:System.ServiceModel.Configuration.MexHttpsBindingElement>
- [<span data-ttu-id="8b2fc-142">Nasıl yapılır: Yapılandırma Dosyası Kullanarak Bir Hizmet için Meta Verileri Yayımlama</span><span class="sxs-lookup"><span data-stu-id="8b2fc-142">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [<span data-ttu-id="8b2fc-143">Özel Bağlama Üzerinden Meta Veri Yayımlama ve Alma</span><span class="sxs-lookup"><span data-stu-id="8b2fc-143">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)
- [<span data-ttu-id="8b2fc-144">Nasıl yapılır: Özel Bir WS-Metadata Exchange Bağlaması Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="8b2fc-144">How to: Configure a Custom WS-Metadata Exchange Binding</span></span>](../../../wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md)
- [<span data-ttu-id="8b2fc-145">Nasıl yapılır: MEX Olmayan Bağlama Üzerinden Meta Verileri Alma</span><span class="sxs-lookup"><span data-stu-id="8b2fc-145">How to: Retrieve Metadata Over a non-MEX Binding</span></span>](../../../wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md)
- [<span data-ttu-id="8b2fc-146">Özel Güvenli Meta Veri Uç Noktaları</span><span class="sxs-lookup"><span data-stu-id="8b2fc-146">Custom Secure Metadata Endpoint</span></span>](../../../wcf/samples/custom-secure-metadata-endpoint.md)
- [<span data-ttu-id="8b2fc-147">Meta Veriler</span><span class="sxs-lookup"><span data-stu-id="8b2fc-147">Metadata</span></span>](../../../wcf/feature-details/metadata.md)
- [<span data-ttu-id="8b2fc-148">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="8b2fc-148">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="8b2fc-149">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="8b2fc-149">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="8b2fc-150">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="8b2fc-150">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="8b2fc-151">\< bağlama ></span><span class="sxs-lookup"><span data-stu-id="8b2fc-151">\<binding></span></span>](bindings.md)
