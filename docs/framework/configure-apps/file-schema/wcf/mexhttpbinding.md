---
title: <mexHttpBinding>
ms.date: 03/30/2017
ms.assetid: e50b2e1f-9668-41a5-8077-dee7abff9f0f
ms.openlocfilehash: 8d5b9378bf7769754586d0b13f742659aee18f03
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74430913"
---
# <a name="mexhttpbinding"></a><span data-ttu-id="88be8-101">\<mexHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="88be8-101">\<mexHttpBinding></span></span>
<span data-ttu-id="88be8-102">HTTP üzerinde WS-MetadataExchange (WS-MEX) ileti değişimi için kullanılan bir bağlamanın ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="88be8-102">Specifies the settings for a binding used for the WS-MetadataExchange (WS-MEX) message exchange over HTTP.</span></span>  
  
<span data-ttu-id="88be8-103">[ **\<yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="88be8-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="88be8-104">[**System. serviceModel >\<** ](system-servicemodel.md) &nbsp;&nbsp;</span><span class="sxs-lookup"><span data-stu-id="88be8-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="88be8-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bağlamaları >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="88be8-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="88be8-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<mexHttpBinding >**</span><span class="sxs-lookup"><span data-stu-id="88be8-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<mexHttpBinding>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="88be8-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="88be8-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="88be8-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="88be8-108">Attributes and Elements</span></span>  
 <span data-ttu-id="88be8-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="88be8-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="88be8-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="88be8-110">Attributes</span></span>  
  
|<span data-ttu-id="88be8-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="88be8-111">Attribute</span></span>|<span data-ttu-id="88be8-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="88be8-112">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="88be8-113">Bir kapatma işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir <xref:System.TimeSpan> değeri.</span><span class="sxs-lookup"><span data-stu-id="88be8-113">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="88be8-114">Bu değer, <xref:System.TimeSpan.Zero>eşit veya ondan büyük olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="88be8-114">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="88be8-115">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="88be8-115">The default is 00:01:00.</span></span>|  
|`name`|<span data-ttu-id="88be8-116">Bağlamanın yapılandırma adını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="88be8-116">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="88be8-117">Bağlama için bir kimlik olarak kullanıldığından, bu değer benzersiz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="88be8-117">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="88be8-118">.NET Framework 4 ' den başlayarak bağlamalar ve davranışlar bir ada sahip olmak için gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="88be8-118">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="88be8-119">Varsayılan yapılandırma ve ad Less bağlamaları ve davranışları hakkında daha fazla bilgi için bkz. [WCF Hizmetleri Için](../../../wcf/samples/simplified-configuration-for-wcf-services.md) [Basitleştirilmiş yapılandırma](../../../wcf/simplified-configuration.md) ve Basitleştirilmiş yapılandırma.</span><span class="sxs-lookup"><span data-stu-id="88be8-119">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="88be8-120">Bir açık işlemin tamamlanabilmesi için belirtilen zaman aralığını belirten bir <xref:System.TimeSpan> değeri.</span><span class="sxs-lookup"><span data-stu-id="88be8-120">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="88be8-121">Bu değer, <xref:System.TimeSpan.Zero>eşit veya ondan büyük olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="88be8-121">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="88be8-122">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="88be8-122">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="88be8-123">Alma işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir <xref:System.TimeSpan> değeri.</span><span class="sxs-lookup"><span data-stu-id="88be8-123">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="88be8-124">Bu değer, <xref:System.TimeSpan.Zero>eşit veya ondan büyük olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="88be8-124">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="88be8-125">Varsayılan değer 00:10:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="88be8-125">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="88be8-126">Bir gönderme işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir <xref:System.TimeSpan> değeri.</span><span class="sxs-lookup"><span data-stu-id="88be8-126">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="88be8-127">Bu değer, <xref:System.TimeSpan.Zero>eşit veya ondan büyük olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="88be8-127">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="88be8-128">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="88be8-128">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="88be8-129">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="88be8-129">Child Elements</span></span>  
 <span data-ttu-id="88be8-130">Yok.</span><span class="sxs-lookup"><span data-stu-id="88be8-130">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="88be8-131">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="88be8-131">Parent Elements</span></span>  
  
|<span data-ttu-id="88be8-132">Öğe</span><span class="sxs-lookup"><span data-stu-id="88be8-132">Element</span></span>|<span data-ttu-id="88be8-133">Açıklama</span><span class="sxs-lookup"><span data-stu-id="88be8-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="88be8-134">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="88be8-134">\<bindings></span></span>](bindings.md)|<span data-ttu-id="88be8-135">Bu öğe, standart ve özel bağlamaların bir koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="88be8-135">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="88be8-136">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="88be8-136">Remarks</span></span>  
 <span data-ttu-id="88be8-137">Bu bağlama temelde güvenlik devre dışı `WSHttpBinding` bağlamadır.</span><span class="sxs-lookup"><span data-stu-id="88be8-137">This binding is essentially a `WSHttpBinding` binding with security disabled.</span></span> <span data-ttu-id="88be8-138">Meta veri isteklerinin çoğunu destekler.</span><span class="sxs-lookup"><span data-stu-id="88be8-138">It supports most metadata requests.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88be8-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="88be8-139">See also</span></span>

- <xref:System.ServiceModel.Description.MetadataExchangeBindings.CreateMexHttpBinding%2A>
- <xref:System.ServiceModel.Configuration.MexHttpBindingElement>
- [<span data-ttu-id="88be8-140">Nasıl yapılır: Yapılandırma Dosyası Kullanarak Bir Hizmet için Meta Verileri Yayımlama</span><span class="sxs-lookup"><span data-stu-id="88be8-140">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [<span data-ttu-id="88be8-141">Özel Bağlama Üzerinden Meta Veri Yayımlama ve Alma</span><span class="sxs-lookup"><span data-stu-id="88be8-141">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)
- [<span data-ttu-id="88be8-142">Meta Veriler</span><span class="sxs-lookup"><span data-stu-id="88be8-142">Metadata</span></span>](../../../wcf/feature-details/metadata.md)
- [<span data-ttu-id="88be8-143">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="88be8-143">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="88be8-144">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="88be8-144">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="88be8-145">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="88be8-145">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="88be8-146">bağlama > \<</span><span class="sxs-lookup"><span data-stu-id="88be8-146">\<binding></span></span>](bindings.md)
