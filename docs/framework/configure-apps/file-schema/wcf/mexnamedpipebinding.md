---
title: <mexNamedPipeBinding>
ms.date: 03/30/2017
ms.assetid: 193412fa-3260-414c-92c6-b32ed3b94a34
ms.openlocfilehash: b26201064aad3a8a09d8604a9706fe3c149cbf58
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400228"
---
# <a name="mexnamedpipebinding"></a><span data-ttu-id="78bc1-101">\<mexNamedPipeBinding></span><span class="sxs-lookup"><span data-stu-id="78bc1-101">\<mexNamedPipeBinding></span></span>
<span data-ttu-id="78bc1-102">Adlandırılmış kanal üzerinde WS-MetadataExchange (WS-MEX) ileti değişimi için kullanılan bir bağlamanın ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="78bc1-102">Specifies the settings for a binding used for the WS-MetadataExchange (WS-MEX) message exchange over named pipe.</span></span>  
  
<span data-ttu-id="78bc1-103">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="78bc1-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="78bc1-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="78bc1-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="78bc1-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bağlama >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="78bc1-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="78bc1-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<mexNamedPipeBinding >**</span><span class="sxs-lookup"><span data-stu-id="78bc1-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<mexNamedPipeBinding>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78bc1-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="78bc1-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="78bc1-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="78bc1-108">Attributes and Elements</span></span>  
 <span data-ttu-id="78bc1-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="78bc1-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="78bc1-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="78bc1-110">Attributes</span></span>  
  
|<span data-ttu-id="78bc1-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="78bc1-111">Attribute</span></span>|<span data-ttu-id="78bc1-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="78bc1-112">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="78bc1-113">Bir <xref:System.TimeSpan> kapatma işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="78bc1-113">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="78bc1-114">Bu değer, değerinden büyük veya buna eşit <xref:System.TimeSpan.Zero>olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="78bc1-114">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="78bc1-115">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="78bc1-115">The default is 00:01:00.</span></span>|  
|`name`|<span data-ttu-id="78bc1-116">Bağlamanın yapılandırma adını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="78bc1-116">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="78bc1-117">Bağlama için bir kimlik olarak kullanıldığından, bu değer benzersiz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="78bc1-117">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="78bc1-118">Her bağlamada bir ve `name` özniteliği `namespace` , hizmetin meta verilerinde benzersiz bir şekilde tanımlayan bir ve özniteliği vardır.</span><span class="sxs-lookup"><span data-stu-id="78bc1-118">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span> <span data-ttu-id="78bc1-119">Ayrıca, bu ad aynı türdeki bağlamalar arasında benzersizdir.</span><span class="sxs-lookup"><span data-stu-id="78bc1-119">In addition, this name is unique among bindings of the same type.</span></span> <span data-ttu-id="78bc1-120">İle [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)]başlayarak, bağlamaların ve davranışların bir ada sahip olması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="78bc1-120">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="78bc1-121">Varsayılan yapılandırma ve ad Less bağlamaları ve davranışları hakkında daha fazla bilgi için bkz. [WCF Hizmetleri Için](../../../wcf/samples/simplified-configuration-for-wcf-services.md) [Basitleştirilmiş yapılandırma](../../../wcf/simplified-configuration.md) ve Basitleştirilmiş yapılandırma.</span><span class="sxs-lookup"><span data-stu-id="78bc1-121">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="78bc1-122">Bir <xref:System.TimeSpan> açık işlemin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="78bc1-122">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="78bc1-123">Bu değer, değerinden büyük veya buna eşit <xref:System.TimeSpan.Zero>olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="78bc1-123">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="78bc1-124">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="78bc1-124">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="78bc1-125">Alma <xref:System.TimeSpan> işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="78bc1-125">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="78bc1-126">Bu değer, değerinden büyük veya buna eşit <xref:System.TimeSpan.Zero>olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="78bc1-126">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="78bc1-127">Varsayılan değer 00:10:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="78bc1-127">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="78bc1-128">Bir <xref:System.TimeSpan> gönderme işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="78bc1-128">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="78bc1-129">Bu değer, değerinden büyük veya buna eşit <xref:System.TimeSpan.Zero>olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="78bc1-129">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="78bc1-130">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="78bc1-130">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="78bc1-131">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="78bc1-131">Child Elements</span></span>  
 <span data-ttu-id="78bc1-132">Yok.</span><span class="sxs-lookup"><span data-stu-id="78bc1-132">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="78bc1-133">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="78bc1-133">Parent Elements</span></span>  
  
|<span data-ttu-id="78bc1-134">Öğe</span><span class="sxs-lookup"><span data-stu-id="78bc1-134">Element</span></span>|<span data-ttu-id="78bc1-135">Açıklama</span><span class="sxs-lookup"><span data-stu-id="78bc1-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="78bc1-136">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="78bc1-136">\<bindings></span></span>](bindings.md)|<span data-ttu-id="78bc1-137">Bu öğe, standart ve özel bağlamaların bir koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="78bc1-137">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="78bc1-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="78bc1-138">See also</span></span>

- <xref:System.ServiceModel.Description.MetadataExchangeBindings.CreateMexNamedPipeBinding%2A>
- <xref:System.ServiceModel.Configuration.MexNamedPipeBindingElement>
- [<span data-ttu-id="78bc1-139">Nasıl yapılır: Yapılandırma dosyası kullanarak bir hizmet için meta verileri yayımlama</span><span class="sxs-lookup"><span data-stu-id="78bc1-139">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [<span data-ttu-id="78bc1-140">Özel Bağlama Üzerinden Meta Veri Yayımlama ve Alma</span><span class="sxs-lookup"><span data-stu-id="78bc1-140">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)
- [<span data-ttu-id="78bc1-141">Meta Veriler</span><span class="sxs-lookup"><span data-stu-id="78bc1-141">Metadata</span></span>](../../../wcf/feature-details/metadata.md)
- [<span data-ttu-id="78bc1-142">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="78bc1-142">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="78bc1-143">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="78bc1-143">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="78bc1-144">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="78bc1-144">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="78bc1-145">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="78bc1-145">\<binding></span></span>](../../../misc/binding.md)
