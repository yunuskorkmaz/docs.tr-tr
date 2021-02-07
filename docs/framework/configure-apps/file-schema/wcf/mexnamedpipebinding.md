---
description: 'Hakkında daha fazla bilgi edinin: <mexNamedPipeBinding>'
title: <mexNamedPipeBinding>
ms.date: 03/30/2017
ms.assetid: 193412fa-3260-414c-92c6-b32ed3b94a34
ms.openlocfilehash: a7d1c6b10ed436d5ec1b20092d042d6b0a80bd34
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99684327"
---
# \<mexNamedPipeBinding>

<span data-ttu-id="92ffd-102">Adlandırılmış kanal üzerinde WS-MetadataExchange (WS-MEX) ileti değişimi için kullanılan bir bağlamanın ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="92ffd-102">Specifies the settings for a binding used for the WS-MetadataExchange (WS-MEX) message exchange over named pipe.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<mexNamedPipeBinding>**  
  
## <a name="syntax"></a><span data-ttu-id="92ffd-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="92ffd-103">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="92ffd-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="92ffd-104">Attributes and Elements</span></span>  

 <span data-ttu-id="92ffd-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="92ffd-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="92ffd-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="92ffd-106">Attributes</span></span>  
  
|<span data-ttu-id="92ffd-107">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="92ffd-107">Attribute</span></span>|<span data-ttu-id="92ffd-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="92ffd-108">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="92ffd-109"><xref:System.TimeSpan>Bir kapatma işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="92ffd-109">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="92ffd-110">Bu değer, değerinden büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="92ffd-110">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="92ffd-111">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="92ffd-111">The default is 00:01:00.</span></span>|  
|`name`|<span data-ttu-id="92ffd-112">Bağlamanın yapılandırma adını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="92ffd-112">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="92ffd-113">Bağlama için bir kimlik olarak kullanıldığından, bu değer benzersiz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="92ffd-113">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="92ffd-114">.NET Framework 4 ' den başlayarak bağlamalar ve davranışlar bir ada sahip olmak için gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="92ffd-114">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="92ffd-115">Varsayılan yapılandırma ve ad Less bağlamaları ve davranışları hakkında daha fazla bilgi için bkz. [WCF Hizmetleri Için](../../../wcf/samples/simplified-configuration-for-wcf-services.md) [Basitleştirilmiş yapılandırma](../../../wcf/simplified-configuration.md) ve Basitleştirilmiş yapılandırma.</span><span class="sxs-lookup"><span data-stu-id="92ffd-115">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="92ffd-116">Bir <xref:System.TimeSpan> Açık işlemin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="92ffd-116">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="92ffd-117">Bu değer, değerinden büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="92ffd-117">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="92ffd-118">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="92ffd-118">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="92ffd-119"><xref:System.TimeSpan>Alma işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="92ffd-119">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="92ffd-120">Bu değer, değerinden büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="92ffd-120">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="92ffd-121">Varsayılan değer 00:10:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="92ffd-121">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="92ffd-122"><xref:System.TimeSpan>Bir gönderme işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="92ffd-122">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="92ffd-123">Bu değer, değerinden büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="92ffd-123">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="92ffd-124">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="92ffd-124">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="92ffd-125">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="92ffd-125">Child Elements</span></span>  

 <span data-ttu-id="92ffd-126">Yok.</span><span class="sxs-lookup"><span data-stu-id="92ffd-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="92ffd-127">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="92ffd-127">Parent Elements</span></span>  
  
|<span data-ttu-id="92ffd-128">Öğe</span><span class="sxs-lookup"><span data-stu-id="92ffd-128">Element</span></span>|<span data-ttu-id="92ffd-129">Açıklama</span><span class="sxs-lookup"><span data-stu-id="92ffd-129">Description</span></span>|  
|-------------|-----------------|  
|[\<bindings>](bindings.md)|<span data-ttu-id="92ffd-130">Bu öğe, standart ve özel bağlamaların bir koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="92ffd-130">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="92ffd-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="92ffd-131">See also</span></span>

- <xref:System.ServiceModel.Description.MetadataExchangeBindings.CreateMexNamedPipeBinding%2A>
- <xref:System.ServiceModel.Configuration.MexNamedPipeBindingElement>
- [<span data-ttu-id="92ffd-132">Nasıl yapılır: Yapılandırma Dosyası Kullanarak Bir Hizmet için Meta Verileri Yayımlama</span><span class="sxs-lookup"><span data-stu-id="92ffd-132">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [<span data-ttu-id="92ffd-133">Özel Bağlama Üzerinden Meta Veri Yayımlama ve Alma</span><span class="sxs-lookup"><span data-stu-id="92ffd-133">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)
- [<span data-ttu-id="92ffd-134">Meta veri</span><span class="sxs-lookup"><span data-stu-id="92ffd-134">Metadata</span></span>](../../../wcf/feature-details/metadata.md)
- [<span data-ttu-id="92ffd-135">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="92ffd-135">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="92ffd-136">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="92ffd-136">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="92ffd-137">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="92ffd-137">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
