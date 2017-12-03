---
title: '&lt;mexTcpBinding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 01baba8d-d784-4255-9ea2-7afff1482bf0
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ef9df72d06c598cc641d884dadbf9d4f5cee9f5b
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="ltmextcpbindinggt"></a><span data-ttu-id="ff8b7-102">&lt;mexTcpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="ff8b7-102">&lt;mexTcpBinding&gt;</span></span>
<span data-ttu-id="ff8b7-103">TCP üzerinden WS-MetadataExchange (WS-MEX) ileti değişimi için kullanılan bir bağlama ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="ff8b7-103">Specifies the settings for a binding used for the WS-MetadataExchange (WS-MEX) message exchange over TCP.</span></span>  
  
 <span data-ttu-id="ff8b7-104">\<Sistem. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="ff8b7-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="ff8b7-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="ff8b7-105">\<bindings></span></span>  
<span data-ttu-id="ff8b7-106">\<mexTcpBinding ></span><span class="sxs-lookup"><span data-stu-id="ff8b7-106">\<mexTcpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff8b7-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ff8b7-107">Syntax</span></span>  
  
```xml  
<mexTcpBinding>  
   <binding   
       closeTimeout="TimeSpan"   
       name="string"   
       openTimeout="TimeSpan"   
       receiveTimeout="TimeSpan"  
       sendTimeout="TimeSpan">  
   </binding>  
</mexTcpBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ff8b7-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="ff8b7-108">Attributes and Elements</span></span>  
 <span data-ttu-id="ff8b7-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ff8b7-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ff8b7-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="ff8b7-110">Attributes</span></span>  
  
|<span data-ttu-id="ff8b7-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="ff8b7-111">Attribute</span></span>|<span data-ttu-id="ff8b7-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ff8b7-112">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="ff8b7-113">A <xref:System.TimeSpan> bir kapatma işlemi tamamlamak sağlanan zaman aralığı belirten değer.</span><span class="sxs-lookup"><span data-stu-id="ff8b7-113">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="ff8b7-114">Bu değer sıfırdan büyük veya eşit olmalıdır <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="ff8b7-114">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="ff8b7-115">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="ff8b7-115">The default is 00:01:00.</span></span>|  
|`name`|<span data-ttu-id="ff8b7-116">Bağlama yapılandırma adını içeren dize.</span><span class="sxs-lookup"><span data-stu-id="ff8b7-116">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="ff8b7-117">Bağlama için bir tanımlayıcı olarak kullanıldığından, bu değer benzersiz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ff8b7-117">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="ff8b7-118">Her bağlama sahip bir `name` ve `namespace` birlikte benzersiz olarak özniteliği hizmet meta verilerde tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="ff8b7-118">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span> <span data-ttu-id="ff8b7-119">Ayrıca, bu ad aynı türde bağlamaları arasında benzersizdir.</span><span class="sxs-lookup"><span data-stu-id="ff8b7-119">In addition, this name is unique among bindings of the same type.</span></span> <span data-ttu-id="ff8b7-120">İle başlayarak [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bağlamalar ve davranışları olmayan bir adı olması için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="ff8b7-120">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="ff8b7-121">Varsayılan yapılandırma ve adsız bağlamalar ve davranışları hakkında daha fazla bilgi için bkz: [Basitleştirilmiş yapılandırma](../../../../../docs/framework/wcf/simplified-configuration.md) ve [WCF hizmetleri için Basitleştirilmiş yapılandırma](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="ff8b7-121">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="ff8b7-122">A <xref:System.TimeSpan> tamamlamak açık işlem için sağlanan zaman aralığını belirten değer.</span><span class="sxs-lookup"><span data-stu-id="ff8b7-122">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="ff8b7-123">Bu değer sıfırdan büyük veya eşit olmalıdır <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="ff8b7-123">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="ff8b7-124">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="ff8b7-124">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="ff8b7-125">A <xref:System.TimeSpan> bir alma işleminin tamamlanması için sağlanan zaman aralığı belirten değer.</span><span class="sxs-lookup"><span data-stu-id="ff8b7-125">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="ff8b7-126">Bu değer sıfırdan büyük veya eşit olmalıdır <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="ff8b7-126">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="ff8b7-127">Varsayılan değer 00:10: 00'dır.</span><span class="sxs-lookup"><span data-stu-id="ff8b7-127">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="ff8b7-128">A <xref:System.TimeSpan> bir gönderme işleminin tamamlanması için sağlanan zaman aralığı belirten değer.</span><span class="sxs-lookup"><span data-stu-id="ff8b7-128">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="ff8b7-129">Bu değer sıfırdan büyük veya eşit olmalıdır <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="ff8b7-129">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="ff8b7-130">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="ff8b7-130">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ff8b7-131">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="ff8b7-131">Child Elements</span></span>  
 <span data-ttu-id="ff8b7-132">Yok.</span><span class="sxs-lookup"><span data-stu-id="ff8b7-132">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ff8b7-133">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="ff8b7-133">Parent Elements</span></span>  
  
|<span data-ttu-id="ff8b7-134">Öğe</span><span class="sxs-lookup"><span data-stu-id="ff8b7-134">Element</span></span>|<span data-ttu-id="ff8b7-135">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ff8b7-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ff8b7-136">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="ff8b7-136">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="ff8b7-137">Bu öğe, standart ve özel bağlamaları koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="ff8b7-137">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ff8b7-138">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ff8b7-138">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.MexTcpBindingElement>  
 <xref:System.ServiceModel.Description.MetadataExchangeBindings.CreateMexTcpBinding%2A>  
 [<span data-ttu-id="ff8b7-139">Nasıl yapılır: bir yapılandırma dosyası kullanarak bir hizmet için meta verileri yayımlama</span><span class="sxs-lookup"><span data-stu-id="ff8b7-139">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)  
 [<span data-ttu-id="ff8b7-140">Yayımlama ve özel bağlama üzerinden meta verileri alma</span><span class="sxs-lookup"><span data-stu-id="ff8b7-140">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../../../docs/framework/wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)  
 [<span data-ttu-id="ff8b7-141">Meta veriler</span><span class="sxs-lookup"><span data-stu-id="ff8b7-141">Metadata</span></span>](../../../../../docs/framework/wcf/feature-details/metadata.md)  
 [<span data-ttu-id="ff8b7-142">Bağlamaları</span><span class="sxs-lookup"><span data-stu-id="ff8b7-142">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="ff8b7-143">Sistem tarafından sağlanan bağlamaları yapılandırma</span><span class="sxs-lookup"><span data-stu-id="ff8b7-143">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="ff8b7-144">Windows Communication Foundation Hizmetleri ve istemcileri yapılandırmak için bağlamaları kullanma</span><span class="sxs-lookup"><span data-stu-id="ff8b7-144">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="ff8b7-145">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="ff8b7-145">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
