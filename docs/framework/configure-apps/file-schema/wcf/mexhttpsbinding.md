---
description: 'Hakkında daha fazla bilgi edinin: <mexHttpsBinding>'
title: <mexHttpsBinding>
ms.date: 03/30/2017
ms.assetid: f2ed3774-78b9-4a15-b79b-655f1ad68b86
ms.openlocfilehash: 1e6eb66e1379cb8f351e34d4fd406dd3cc1f9a4e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99684340"
---
# \<mexHttpsBinding>

<span data-ttu-id="bfd65-102">HTTPS üzerinden WS-MetadataExchange (WS-MEX) ileti değişimi için kullanılan bir bağlamanın ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="bfd65-102">Specifies the settings for a binding used for the WS-MetadataExchange (WS-MEX) message exchange over HTTPS.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<mexHttpsBinding>**  
  
## <a name="syntax"></a><span data-ttu-id="bfd65-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="bfd65-103">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bfd65-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="bfd65-104">Attributes and Elements</span></span>  

 <span data-ttu-id="bfd65-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="bfd65-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bfd65-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="bfd65-106">Attributes</span></span>  
  
|<span data-ttu-id="bfd65-107">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="bfd65-107">Attribute</span></span>|<span data-ttu-id="bfd65-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bfd65-108">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="bfd65-109"><xref:System.TimeSpan>Bir kapatma işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="bfd65-109">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="bfd65-110">Bu değer, değerinden büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="bfd65-110">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="bfd65-111">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="bfd65-111">The default is 00:01:00.</span></span>|  
|`name`|<span data-ttu-id="bfd65-112">Bağlamanın yapılandırma adını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="bfd65-112">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="bfd65-113">Bağlama için bir kimlik olarak kullanıldığından, bu değer benzersiz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="bfd65-113">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="bfd65-114">.NET Framework 4 ' den başlayarak bağlamalar ve davranışlar bir ada sahip olmak için gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="bfd65-114">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="bfd65-115">Varsayılan yapılandırma ve ad Less bağlamaları ve davranışları hakkında daha fazla bilgi için bkz. [WCF Hizmetleri Için](../../../wcf/samples/simplified-configuration-for-wcf-services.md) [Basitleştirilmiş yapılandırma](../../../wcf/simplified-configuration.md) ve Basitleştirilmiş yapılandırma.</span><span class="sxs-lookup"><span data-stu-id="bfd65-115">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="bfd65-116">Bir <xref:System.TimeSpan> Açık işlemin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="bfd65-116">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="bfd65-117">Bu değer, değerinden büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="bfd65-117">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="bfd65-118">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="bfd65-118">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="bfd65-119"><xref:System.TimeSpan>Alma işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="bfd65-119">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="bfd65-120">Bu değer, değerinden büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="bfd65-120">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="bfd65-121">Varsayılan değer 00:10:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="bfd65-121">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="bfd65-122"><xref:System.TimeSpan>Bir gönderme işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="bfd65-122">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="bfd65-123">Bu değer, değerinden büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="bfd65-123">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="bfd65-124">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="bfd65-124">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bfd65-125">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="bfd65-125">Child Elements</span></span>  

 <span data-ttu-id="bfd65-126">Yok.</span><span class="sxs-lookup"><span data-stu-id="bfd65-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bfd65-127">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="bfd65-127">Parent Elements</span></span>  
  
|<span data-ttu-id="bfd65-128">Öğe</span><span class="sxs-lookup"><span data-stu-id="bfd65-128">Element</span></span>|<span data-ttu-id="bfd65-129">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bfd65-129">Description</span></span>|  
|-------------|-----------------|  
|[\<bindings>](bindings.md)|<span data-ttu-id="bfd65-130">Bu öğe, standart ve özel bağlamaların bir koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="bfd65-130">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bfd65-131">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bfd65-131">Remarks</span></span>  

 <span data-ttu-id="bfd65-132">Bu bağlama temelde, `WSHttpBinding` sertifikaları kullanarak aktarım düzeyi güvenliği destekleyen bir bağlamadır.</span><span class="sxs-lookup"><span data-stu-id="bfd65-132">This binding is essentially a `WSHttpBinding` binding that supports transport-level security using certificates.</span></span> <span data-ttu-id="bfd65-133">Bu tür bir meta veri uç noktası yapılandırma ve kullanma hakkında daha fazla bilgi için bkz. [nasıl yapılır: özel bir WS-Metadata Exchange bağlamasını yapılandırma](../../../wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md), [nasıl yapılır: meta verileri bir MEX olmayan bağlama üzerinden alma](../../../wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md)ve örnek [özel güvenli meta veri uç noktası](../../../wcf/samples/custom-secure-metadata-endpoint.md).</span><span class="sxs-lookup"><span data-stu-id="bfd65-133">For more information about configuring and using such a metadata endpoint, see [How to: Configure a Custom WS-Metadata Exchange Binding](../../../wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md), [How to: Retrieve Metadata Over a non-MEX Binding](../../../wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md), and the sample [Custom Secure Metadata Endpoint](../../../wcf/samples/custom-secure-metadata-endpoint.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bfd65-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bfd65-134">See also</span></span>

- <xref:System.ServiceModel.Description.MetadataExchangeBindings.CreateMexHttpsBinding%2A>
- <xref:System.ServiceModel.Configuration.MexHttpsBindingElement>
- [<span data-ttu-id="bfd65-135">Nasıl yapılır: Yapılandırma Dosyası Kullanarak Bir Hizmet için Meta Verileri Yayımlama</span><span class="sxs-lookup"><span data-stu-id="bfd65-135">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [<span data-ttu-id="bfd65-136">Özel Bağlama Üzerinden Meta Veri Yayımlama ve Alma</span><span class="sxs-lookup"><span data-stu-id="bfd65-136">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)
- [<span data-ttu-id="bfd65-137">Nasıl yapılır: Özel Bir WS-Metadata Değişimi Bağlaması Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="bfd65-137">How to: Configure a Custom WS-Metadata Exchange Binding</span></span>](../../../wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md)
- [<span data-ttu-id="bfd65-138">Nasıl yapılır: MEX Olmayan Bağlama Üzerinden Meta Verileri Alma</span><span class="sxs-lookup"><span data-stu-id="bfd65-138">How to: Retrieve Metadata Over a non-MEX Binding</span></span>](../../../wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md)
- [<span data-ttu-id="bfd65-139">Özel Güvenli Meta Veri Uç Noktaları</span><span class="sxs-lookup"><span data-stu-id="bfd65-139">Custom Secure Metadata Endpoint</span></span>](../../../wcf/samples/custom-secure-metadata-endpoint.md)
- [<span data-ttu-id="bfd65-140">Meta veri</span><span class="sxs-lookup"><span data-stu-id="bfd65-140">Metadata</span></span>](../../../wcf/feature-details/metadata.md)
- [<span data-ttu-id="bfd65-141">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="bfd65-141">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="bfd65-142">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="bfd65-142">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="bfd65-143">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="bfd65-143">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
