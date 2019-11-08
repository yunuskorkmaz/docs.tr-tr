---
title: <mexHttpBinding>
ms.date: 03/30/2017
ms.assetid: e50b2e1f-9668-41a5-8077-dee7abff9f0f
ms.openlocfilehash: 8a8145bbfcb3eefb06d159d834232d94166fa6dd
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73736710"
---
# <a name="mexhttpbinding"></a><span data-ttu-id="bafd2-101">\<mexHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="bafd2-101">\<mexHttpBinding></span></span>
<span data-ttu-id="bafd2-102">HTTP üzerinde WS-MetadataExchange (WS-MEX) ileti değişimi için kullanılan bir bağlamanın ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="bafd2-102">Specifies the settings for a binding used for the WS-MetadataExchange (WS-MEX) message exchange over HTTP.</span></span>  
  
<span data-ttu-id="bafd2-103">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="bafd2-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="bafd2-104">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="bafd2-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="bafd2-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bağlamaları >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="bafd2-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="bafd2-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<mexHttpBinding >**</span><span class="sxs-lookup"><span data-stu-id="bafd2-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<mexHttpBinding>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bafd2-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bafd2-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bafd2-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="bafd2-108">Attributes and Elements</span></span>  
 <span data-ttu-id="bafd2-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="bafd2-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bafd2-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="bafd2-110">Attributes</span></span>  
  
|<span data-ttu-id="bafd2-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="bafd2-111">Attribute</span></span>|<span data-ttu-id="bafd2-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bafd2-112">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="bafd2-113">Bir kapatma işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir <xref:System.TimeSpan> değeri.</span><span class="sxs-lookup"><span data-stu-id="bafd2-113">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="bafd2-114">Bu değer, <xref:System.TimeSpan.Zero>eşit veya ondan büyük olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="bafd2-114">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="bafd2-115">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="bafd2-115">The default is 00:01:00.</span></span>|  
|`name`|<span data-ttu-id="bafd2-116">Bağlamanın yapılandırma adını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="bafd2-116">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="bafd2-117">Bağlama için bir kimlik olarak kullanıldığından, bu değer benzersiz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="bafd2-117">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="bafd2-118">Her bağlamada bir `name` ve `namespace` özniteliği, hizmetin meta verilerinde benzersiz bir şekilde tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="bafd2-118">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span> <span data-ttu-id="bafd2-119">Ayrıca, bu ad aynı türdeki bağlamalar arasında benzersizdir.</span><span class="sxs-lookup"><span data-stu-id="bafd2-119">In addition, this name is unique among bindings of the same type.</span></span> <span data-ttu-id="bafd2-120">[!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)]başlayarak bağlamalar ve davranışları bir ada sahip olmak için gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="bafd2-120">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="bafd2-121">Varsayılan yapılandırma ve ad Less bağlamaları ve davranışları hakkında daha fazla bilgi için bkz. [WCF Hizmetleri Için](../../../wcf/samples/simplified-configuration-for-wcf-services.md) [Basitleştirilmiş yapılandırma](../../../wcf/simplified-configuration.md) ve Basitleştirilmiş yapılandırma.</span><span class="sxs-lookup"><span data-stu-id="bafd2-121">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="bafd2-122">Bir açık işlemin tamamlanabilmesi için belirtilen zaman aralığını belirten bir <xref:System.TimeSpan> değeri.</span><span class="sxs-lookup"><span data-stu-id="bafd2-122">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="bafd2-123">Bu değer, <xref:System.TimeSpan.Zero>eşit veya ondan büyük olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="bafd2-123">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="bafd2-124">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="bafd2-124">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="bafd2-125">Alma işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir <xref:System.TimeSpan> değeri.</span><span class="sxs-lookup"><span data-stu-id="bafd2-125">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="bafd2-126">Bu değer, <xref:System.TimeSpan.Zero>eşit veya ondan büyük olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="bafd2-126">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="bafd2-127">Varsayılan değer 00:10:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="bafd2-127">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="bafd2-128">Bir gönderme işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir <xref:System.TimeSpan> değeri.</span><span class="sxs-lookup"><span data-stu-id="bafd2-128">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="bafd2-129">Bu değer, <xref:System.TimeSpan.Zero>eşit veya ondan büyük olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="bafd2-129">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="bafd2-130">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="bafd2-130">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bafd2-131">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="bafd2-131">Child Elements</span></span>  
 <span data-ttu-id="bafd2-132">Yok.</span><span class="sxs-lookup"><span data-stu-id="bafd2-132">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bafd2-133">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="bafd2-133">Parent Elements</span></span>  
  
|<span data-ttu-id="bafd2-134">Öğe</span><span class="sxs-lookup"><span data-stu-id="bafd2-134">Element</span></span>|<span data-ttu-id="bafd2-135">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bafd2-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bafd2-136">\<bindings ></span><span class="sxs-lookup"><span data-stu-id="bafd2-136">\<bindings></span></span>](bindings.md)|<span data-ttu-id="bafd2-137">Bu öğe, standart ve özel bağlamaların bir koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="bafd2-137">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bafd2-138">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bafd2-138">Remarks</span></span>  
 <span data-ttu-id="bafd2-139">Bu bağlama temelde güvenlik devre dışı `WSHttpBinding` bağlamadır.</span><span class="sxs-lookup"><span data-stu-id="bafd2-139">This binding is essentially a `WSHttpBinding` binding with security disabled.</span></span> <span data-ttu-id="bafd2-140">Meta veri isteklerinin çoğunu destekler.</span><span class="sxs-lookup"><span data-stu-id="bafd2-140">It supports most metadata requests.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bafd2-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bafd2-141">See also</span></span>

- <xref:System.ServiceModel.Description.MetadataExchangeBindings.CreateMexHttpBinding%2A>
- <xref:System.ServiceModel.Configuration.MexHttpBindingElement>
- [<span data-ttu-id="bafd2-142">Nasıl yapılır: Yapılandırma Dosyası Kullanarak Bir Hizmet için Meta Verileri Yayımlama</span><span class="sxs-lookup"><span data-stu-id="bafd2-142">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [<span data-ttu-id="bafd2-143">Özel Bağlama Üzerinden Meta Veri Yayımlama ve Alma</span><span class="sxs-lookup"><span data-stu-id="bafd2-143">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)
- [<span data-ttu-id="bafd2-144">Meta Veriler</span><span class="sxs-lookup"><span data-stu-id="bafd2-144">Metadata</span></span>](../../../wcf/feature-details/metadata.md)
- [<span data-ttu-id="bafd2-145">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="bafd2-145">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="bafd2-146">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="bafd2-146">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="bafd2-147">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="bafd2-147">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="bafd2-148">\< bağlama ></span><span class="sxs-lookup"><span data-stu-id="bafd2-148">\<binding></span></span>](bindings.md)
