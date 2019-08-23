---
title: <mexNamedPipeBinding>
ms.date: 03/30/2017
ms.assetid: 193412fa-3260-414c-92c6-b32ed3b94a34
ms.openlocfilehash: 0d0904c02e31def1b5264bec9f61eac0c9a8e964
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931228"
---
# <a name="mexnamedpipebinding"></a><span data-ttu-id="244f7-101">\<mexNamedPipeBinding></span><span class="sxs-lookup"><span data-stu-id="244f7-101">\<mexNamedPipeBinding></span></span>
<span data-ttu-id="244f7-102">Adlandırılmış kanal üzerinde WS-MetadataExchange (WS-MEX) ileti değişimi için kullanılan bir bağlamanın ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="244f7-102">Specifies the settings for a binding used for the WS-MetadataExchange (WS-MEX) message exchange over named pipe.</span></span>  
  
 <span data-ttu-id="244f7-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="244f7-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="244f7-104">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="244f7-104">\<bindings></span></span>  
<span data-ttu-id="244f7-105">\<mexNamedPipeBinding></span><span class="sxs-lookup"><span data-stu-id="244f7-105">\<mexNamedPipeBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="244f7-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="244f7-106">Syntax</span></span>  
  
```xml  
<mexNamedPipeBinding>
  <binding closeTimeout="TimeSpan"
           name="string"
           openTimeout="TimeSpan"
           receiveTimeout="TimeSpan"
           sendTimeout="TimeSpan">
  </binding>
</mexNamedPipeBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="244f7-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="244f7-107">Attributes and Elements</span></span>  
 <span data-ttu-id="244f7-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="244f7-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="244f7-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="244f7-109">Attributes</span></span>  
  
|<span data-ttu-id="244f7-110">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="244f7-110">Attribute</span></span>|<span data-ttu-id="244f7-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="244f7-111">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="244f7-112">Bir <xref:System.TimeSpan> kapatma işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="244f7-112">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="244f7-113">Bu değer, değerinden büyük veya buna eşit <xref:System.TimeSpan.Zero>olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="244f7-113">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="244f7-114">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="244f7-114">The default is 00:01:00.</span></span>|  
|`name`|<span data-ttu-id="244f7-115">Bağlamanın yapılandırma adını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="244f7-115">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="244f7-116">Bağlama için bir kimlik olarak kullanıldığından, bu değer benzersiz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="244f7-116">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="244f7-117">Her bağlamada bir ve `name` özniteliği `namespace` , hizmetin meta verilerinde benzersiz bir şekilde tanımlayan bir ve özniteliği vardır.</span><span class="sxs-lookup"><span data-stu-id="244f7-117">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span> <span data-ttu-id="244f7-118">Ayrıca, bu ad aynı türdeki bağlamalar arasında benzersizdir.</span><span class="sxs-lookup"><span data-stu-id="244f7-118">In addition, this name is unique among bindings of the same type.</span></span> <span data-ttu-id="244f7-119">İle [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)]başlayarak, bağlamaların ve davranışların bir ada sahip olması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="244f7-119">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="244f7-120">Varsayılan yapılandırma ve ad Less bağlamaları ve davranışları hakkında daha fazla bilgi için bkz. [WCF Hizmetleri Için](../../../wcf/samples/simplified-configuration-for-wcf-services.md) [Basitleştirilmiş yapılandırma](../../../wcf/simplified-configuration.md) ve Basitleştirilmiş yapılandırma.</span><span class="sxs-lookup"><span data-stu-id="244f7-120">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="244f7-121">Bir <xref:System.TimeSpan> açık işlemin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="244f7-121">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="244f7-122">Bu değer, değerinden büyük veya buna eşit <xref:System.TimeSpan.Zero>olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="244f7-122">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="244f7-123">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="244f7-123">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="244f7-124">Alma <xref:System.TimeSpan> işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="244f7-124">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="244f7-125">Bu değer, değerinden büyük veya buna eşit <xref:System.TimeSpan.Zero>olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="244f7-125">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="244f7-126">Varsayılan değer 00:10:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="244f7-126">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="244f7-127">Bir <xref:System.TimeSpan> gönderme işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="244f7-127">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="244f7-128">Bu değer, değerinden büyük veya buna eşit <xref:System.TimeSpan.Zero>olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="244f7-128">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="244f7-129">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="244f7-129">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="244f7-130">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="244f7-130">Child Elements</span></span>  
 <span data-ttu-id="244f7-131">Yok.</span><span class="sxs-lookup"><span data-stu-id="244f7-131">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="244f7-132">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="244f7-132">Parent Elements</span></span>  
  
|<span data-ttu-id="244f7-133">Öğe</span><span class="sxs-lookup"><span data-stu-id="244f7-133">Element</span></span>|<span data-ttu-id="244f7-134">Açıklama</span><span class="sxs-lookup"><span data-stu-id="244f7-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="244f7-135">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="244f7-135">\<bindings></span></span>](bindings.md)|<span data-ttu-id="244f7-136">Bu öğe, standart ve özel bağlamaların bir koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="244f7-136">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="244f7-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="244f7-137">See also</span></span>

- <xref:System.ServiceModel.Description.MetadataExchangeBindings.CreateMexNamedPipeBinding%2A>
- <xref:System.ServiceModel.Configuration.MexNamedPipeBindingElement>
- [<span data-ttu-id="244f7-138">Nasıl yapılır: Yapılandırma dosyası kullanarak bir hizmet için meta verileri yayımlama</span><span class="sxs-lookup"><span data-stu-id="244f7-138">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [<span data-ttu-id="244f7-139">Özel Bağlama Üzerinden Meta Veri Yayımlama ve Alma</span><span class="sxs-lookup"><span data-stu-id="244f7-139">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)
- [<span data-ttu-id="244f7-140">Meta Veriler</span><span class="sxs-lookup"><span data-stu-id="244f7-140">Metadata</span></span>](../../../wcf/feature-details/metadata.md)
- [<span data-ttu-id="244f7-141">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="244f7-141">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="244f7-142">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="244f7-142">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="244f7-143">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="244f7-143">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="244f7-144">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="244f7-144">\<binding></span></span>](../../../misc/binding.md)
