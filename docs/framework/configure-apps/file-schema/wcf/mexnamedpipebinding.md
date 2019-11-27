---
title: <mexNamedPipeBinding>
ms.date: 03/30/2017
ms.assetid: 193412fa-3260-414c-92c6-b32ed3b94a34
ms.openlocfilehash: 41f5b19f5067d9ac7faa2c7329dd07dd9d48e9b3
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74430880"
---
# <a name="mexnamedpipebinding"></a><span data-ttu-id="ccb8a-101">\<mexNamedPipeBinding ></span><span class="sxs-lookup"><span data-stu-id="ccb8a-101">\<mexNamedPipeBinding></span></span>
<span data-ttu-id="ccb8a-102">Adlandırılmış kanal üzerinde WS-MetadataExchange (WS-MEX) ileti değişimi için kullanılan bir bağlamanın ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="ccb8a-102">Specifies the settings for a binding used for the WS-MetadataExchange (WS-MEX) message exchange over named pipe.</span></span>  
  
<span data-ttu-id="ccb8a-103">[ **\<yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="ccb8a-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="ccb8a-104">[**System. serviceModel >\<** ](system-servicemodel.md) &nbsp;&nbsp;</span><span class="sxs-lookup"><span data-stu-id="ccb8a-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="ccb8a-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bağlamaları >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="ccb8a-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="ccb8a-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<mexNamedPipeBinding >**</span><span class="sxs-lookup"><span data-stu-id="ccb8a-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<mexNamedPipeBinding>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ccb8a-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ccb8a-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ccb8a-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="ccb8a-108">Attributes and Elements</span></span>  
 <span data-ttu-id="ccb8a-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ccb8a-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ccb8a-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="ccb8a-110">Attributes</span></span>  
  
|<span data-ttu-id="ccb8a-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="ccb8a-111">Attribute</span></span>|<span data-ttu-id="ccb8a-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ccb8a-112">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="ccb8a-113">Bir kapatma işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir <xref:System.TimeSpan> değeri.</span><span class="sxs-lookup"><span data-stu-id="ccb8a-113">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="ccb8a-114">Bu değer, <xref:System.TimeSpan.Zero>eşit veya ondan büyük olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ccb8a-114">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="ccb8a-115">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="ccb8a-115">The default is 00:01:00.</span></span>|  
|`name`|<span data-ttu-id="ccb8a-116">Bağlamanın yapılandırma adını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="ccb8a-116">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="ccb8a-117">Bağlama için bir kimlik olarak kullanıldığından, bu değer benzersiz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ccb8a-117">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="ccb8a-118">.NET Framework 4 ' den başlayarak bağlamalar ve davranışlar bir ada sahip olmak için gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="ccb8a-118">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="ccb8a-119">Varsayılan yapılandırma ve ad Less bağlamaları ve davranışları hakkında daha fazla bilgi için bkz. [WCF Hizmetleri Için](../../../wcf/samples/simplified-configuration-for-wcf-services.md) [Basitleştirilmiş yapılandırma](../../../wcf/simplified-configuration.md) ve Basitleştirilmiş yapılandırma.</span><span class="sxs-lookup"><span data-stu-id="ccb8a-119">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="ccb8a-120">Bir açık işlemin tamamlanabilmesi için belirtilen zaman aralığını belirten bir <xref:System.TimeSpan> değeri.</span><span class="sxs-lookup"><span data-stu-id="ccb8a-120">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="ccb8a-121">Bu değer, <xref:System.TimeSpan.Zero>eşit veya ondan büyük olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ccb8a-121">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="ccb8a-122">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="ccb8a-122">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="ccb8a-123">Alma işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir <xref:System.TimeSpan> değeri.</span><span class="sxs-lookup"><span data-stu-id="ccb8a-123">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="ccb8a-124">Bu değer, <xref:System.TimeSpan.Zero>eşit veya ondan büyük olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ccb8a-124">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="ccb8a-125">Varsayılan değer 00:10:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="ccb8a-125">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="ccb8a-126">Bir gönderme işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir <xref:System.TimeSpan> değeri.</span><span class="sxs-lookup"><span data-stu-id="ccb8a-126">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="ccb8a-127">Bu değer, <xref:System.TimeSpan.Zero>eşit veya ondan büyük olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ccb8a-127">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="ccb8a-128">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="ccb8a-128">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ccb8a-129">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="ccb8a-129">Child Elements</span></span>  
 <span data-ttu-id="ccb8a-130">Yok.</span><span class="sxs-lookup"><span data-stu-id="ccb8a-130">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ccb8a-131">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="ccb8a-131">Parent Elements</span></span>  
  
|<span data-ttu-id="ccb8a-132">Öğe</span><span class="sxs-lookup"><span data-stu-id="ccb8a-132">Element</span></span>|<span data-ttu-id="ccb8a-133">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ccb8a-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ccb8a-134">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="ccb8a-134">\<bindings></span></span>](bindings.md)|<span data-ttu-id="ccb8a-135">Bu öğe, standart ve özel bağlamaların bir koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="ccb8a-135">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ccb8a-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ccb8a-136">See also</span></span>

- <xref:System.ServiceModel.Description.MetadataExchangeBindings.CreateMexNamedPipeBinding%2A>
- <xref:System.ServiceModel.Configuration.MexNamedPipeBindingElement>
- [<span data-ttu-id="ccb8a-137">Nasıl yapılır: Yapılandırma Dosyası Kullanarak Bir Hizmet için Meta Verileri Yayımlama</span><span class="sxs-lookup"><span data-stu-id="ccb8a-137">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [<span data-ttu-id="ccb8a-138">Özel Bağlama Üzerinden Meta Veri Yayımlama ve Alma</span><span class="sxs-lookup"><span data-stu-id="ccb8a-138">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)
- [<span data-ttu-id="ccb8a-139">Meta Veriler</span><span class="sxs-lookup"><span data-stu-id="ccb8a-139">Metadata</span></span>](../../../wcf/feature-details/metadata.md)
- [<span data-ttu-id="ccb8a-140">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="ccb8a-140">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="ccb8a-141">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="ccb8a-141">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="ccb8a-142">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="ccb8a-142">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="ccb8a-143">bağlama > \<</span><span class="sxs-lookup"><span data-stu-id="ccb8a-143">\<binding></span></span>](bindings.md)
