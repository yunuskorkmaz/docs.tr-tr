---
title: <mexHttpBinding>
ms.date: 03/30/2017
ms.assetid: e50b2e1f-9668-41a5-8077-dee7abff9f0f
ms.openlocfilehash: 8d5b9378bf7769754586d0b13f742659aee18f03
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "74430913"
---
# \<mexHttpBinding>
<span data-ttu-id="c5404-101">HTTP üzerinde WS-MetadataExchange (WS-MEX) ileti değişimi için kullanılan bir bağlamanın ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="c5404-101">Specifies the settings for a binding used for the WS-MetadataExchange (WS-MEX) message exchange over HTTP.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<mexHttpBinding>**  
  
## <a name="syntax"></a><span data-ttu-id="c5404-102">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c5404-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c5404-103">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="c5404-103">Attributes and Elements</span></span>  
 <span data-ttu-id="c5404-104">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c5404-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c5404-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c5404-105">Attributes</span></span>  
  
|<span data-ttu-id="c5404-106">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="c5404-106">Attribute</span></span>|<span data-ttu-id="c5404-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c5404-107">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="c5404-108"><xref:System.TimeSpan>Bir kapatma işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="c5404-108">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="c5404-109">Bu değer, değerinden büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="c5404-109">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="c5404-110">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="c5404-110">The default is 00:01:00.</span></span>|  
|`name`|<span data-ttu-id="c5404-111">Bağlamanın yapılandırma adını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="c5404-111">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="c5404-112">Bağlama için bir kimlik olarak kullanıldığından, bu değer benzersiz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c5404-112">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="c5404-113">.NET Framework 4 ' den başlayarak bağlamalar ve davranışlar bir ada sahip olmak için gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="c5404-113">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="c5404-114">Varsayılan yapılandırma ve ad Less bağlamaları ve davranışları hakkında daha fazla bilgi için bkz. [WCF Hizmetleri Için](../../../wcf/samples/simplified-configuration-for-wcf-services.md) [Basitleştirilmiş yapılandırma](../../../wcf/simplified-configuration.md) ve Basitleştirilmiş yapılandırma.</span><span class="sxs-lookup"><span data-stu-id="c5404-114">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="c5404-115">Bir <xref:System.TimeSpan> Açık işlemin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="c5404-115">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="c5404-116">Bu değer, değerinden büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="c5404-116">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="c5404-117">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="c5404-117">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="c5404-118"><xref:System.TimeSpan>Alma işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="c5404-118">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="c5404-119">Bu değer, değerinden büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="c5404-119">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="c5404-120">Varsayılan değer 00:10:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="c5404-120">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="c5404-121"><xref:System.TimeSpan>Bir gönderme işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="c5404-121">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="c5404-122">Bu değer, değerinden büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="c5404-122">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="c5404-123">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="c5404-123">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c5404-124">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="c5404-124">Child Elements</span></span>  
 <span data-ttu-id="c5404-125">Yok.</span><span class="sxs-lookup"><span data-stu-id="c5404-125">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c5404-126">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="c5404-126">Parent Elements</span></span>  
  
|<span data-ttu-id="c5404-127">Öğe</span><span class="sxs-lookup"><span data-stu-id="c5404-127">Element</span></span>|<span data-ttu-id="c5404-128">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c5404-128">Description</span></span>|  
|-------------|-----------------|  
|[\<bindings>](bindings.md)|<span data-ttu-id="c5404-129">Bu öğe, standart ve özel bağlamaların bir koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="c5404-129">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c5404-130">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c5404-130">Remarks</span></span>  
 <span data-ttu-id="c5404-131">Bu bağlama temelde `WSHttpBinding` güvenlik devre dışı olan bir bağlamadır.</span><span class="sxs-lookup"><span data-stu-id="c5404-131">This binding is essentially a `WSHttpBinding` binding with security disabled.</span></span> <span data-ttu-id="c5404-132">Meta veri isteklerinin çoğunu destekler.</span><span class="sxs-lookup"><span data-stu-id="c5404-132">It supports most metadata requests.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5404-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c5404-133">See also</span></span>

- <xref:System.ServiceModel.Description.MetadataExchangeBindings.CreateMexHttpBinding%2A>
- <xref:System.ServiceModel.Configuration.MexHttpBindingElement>
- [<span data-ttu-id="c5404-134">Nasıl yapılır: Yapılandırma Dosyası Kullanarak Bir Hizmet için Meta Verileri Yayımlama</span><span class="sxs-lookup"><span data-stu-id="c5404-134">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [<span data-ttu-id="c5404-135">Özel Bağlama Üzerinden Meta Veri Yayımlama ve Alma</span><span class="sxs-lookup"><span data-stu-id="c5404-135">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)
- [<span data-ttu-id="c5404-136">Meta Veriler</span><span class="sxs-lookup"><span data-stu-id="c5404-136">Metadata</span></span>](../../../wcf/feature-details/metadata.md)
- [<span data-ttu-id="c5404-137">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="c5404-137">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="c5404-138">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="c5404-138">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="c5404-139">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="c5404-139">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
