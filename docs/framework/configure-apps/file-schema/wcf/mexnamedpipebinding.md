---
title: <mexNamedPipeBinding>
ms.date: 03/30/2017
ms.assetid: 193412fa-3260-414c-92c6-b32ed3b94a34
ms.openlocfilehash: 41f5b19f5067d9ac7faa2c7329dd07dd9d48e9b3
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "74430880"
---
# \<mexNamedPipeBinding>
<span data-ttu-id="5fe46-101">Adlandırılmış kanal üzerinde WS-MetadataExchange (WS-MEX) ileti değişimi için kullanılan bir bağlamanın ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="5fe46-101">Specifies the settings for a binding used for the WS-MetadataExchange (WS-MEX) message exchange over named pipe.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<mexNamedPipeBinding>**  
  
## <a name="syntax"></a><span data-ttu-id="5fe46-102">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5fe46-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5fe46-103">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="5fe46-103">Attributes and Elements</span></span>  
 <span data-ttu-id="5fe46-104">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5fe46-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5fe46-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="5fe46-105">Attributes</span></span>  
  
|<span data-ttu-id="5fe46-106">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="5fe46-106">Attribute</span></span>|<span data-ttu-id="5fe46-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5fe46-107">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="5fe46-108"><xref:System.TimeSpan>Bir kapatma işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="5fe46-108">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="5fe46-109">Bu değer, değerinden büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="5fe46-109">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="5fe46-110">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="5fe46-110">The default is 00:01:00.</span></span>|  
|`name`|<span data-ttu-id="5fe46-111">Bağlamanın yapılandırma adını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="5fe46-111">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="5fe46-112">Bağlama için bir kimlik olarak kullanıldığından, bu değer benzersiz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5fe46-112">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="5fe46-113">.NET Framework 4 ' den başlayarak bağlamalar ve davranışlar bir ada sahip olmak için gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="5fe46-113">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="5fe46-114">Varsayılan yapılandırma ve ad Less bağlamaları ve davranışları hakkında daha fazla bilgi için bkz. [WCF Hizmetleri Için](../../../wcf/samples/simplified-configuration-for-wcf-services.md) [Basitleştirilmiş yapılandırma](../../../wcf/simplified-configuration.md) ve Basitleştirilmiş yapılandırma.</span><span class="sxs-lookup"><span data-stu-id="5fe46-114">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="5fe46-115">Bir <xref:System.TimeSpan> Açık işlemin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="5fe46-115">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="5fe46-116">Bu değer, değerinden büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="5fe46-116">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="5fe46-117">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="5fe46-117">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="5fe46-118"><xref:System.TimeSpan>Alma işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="5fe46-118">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="5fe46-119">Bu değer, değerinden büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="5fe46-119">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="5fe46-120">Varsayılan değer 00:10:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="5fe46-120">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="5fe46-121"><xref:System.TimeSpan>Bir gönderme işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="5fe46-121">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="5fe46-122">Bu değer, değerinden büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="5fe46-122">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="5fe46-123">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="5fe46-123">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5fe46-124">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="5fe46-124">Child Elements</span></span>  
 <span data-ttu-id="5fe46-125">Yok.</span><span class="sxs-lookup"><span data-stu-id="5fe46-125">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5fe46-126">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="5fe46-126">Parent Elements</span></span>  
  
|<span data-ttu-id="5fe46-127">Öğe</span><span class="sxs-lookup"><span data-stu-id="5fe46-127">Element</span></span>|<span data-ttu-id="5fe46-128">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5fe46-128">Description</span></span>|  
|-------------|-----------------|  
|[\<bindings>](bindings.md)|<span data-ttu-id="5fe46-129">Bu öğe, standart ve özel bağlamaların bir koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="5fe46-129">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5fe46-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5fe46-130">See also</span></span>

- <xref:System.ServiceModel.Description.MetadataExchangeBindings.CreateMexNamedPipeBinding%2A>
- <xref:System.ServiceModel.Configuration.MexNamedPipeBindingElement>
- [<span data-ttu-id="5fe46-131">Nasıl yapılır: Yapılandırma Dosyası Kullanarak Bir Hizmet için Meta Verileri Yayımlama</span><span class="sxs-lookup"><span data-stu-id="5fe46-131">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [<span data-ttu-id="5fe46-132">Özel Bağlama Üzerinden Meta Veri Yayımlama ve Alma</span><span class="sxs-lookup"><span data-stu-id="5fe46-132">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)
- [<span data-ttu-id="5fe46-133">Meta Veriler</span><span class="sxs-lookup"><span data-stu-id="5fe46-133">Metadata</span></span>](../../../wcf/feature-details/metadata.md)
- [<span data-ttu-id="5fe46-134">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="5fe46-134">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="5fe46-135">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="5fe46-135">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="5fe46-136">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="5fe46-136">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
