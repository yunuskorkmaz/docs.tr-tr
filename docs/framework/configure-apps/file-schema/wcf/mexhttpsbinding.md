---
title: <mexHttpsBinding>
ms.date: 03/30/2017
ms.assetid: f2ed3774-78b9-4a15-b79b-655f1ad68b86
ms.openlocfilehash: 924d68dd828622b74c5e424a695f80874391b453
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74430346"
---
# <a name="mexhttpsbinding"></a><span data-ttu-id="29d85-101">\<mexHttpsBinding></span><span class="sxs-lookup"><span data-stu-id="29d85-101">\<mexHttpsBinding></span></span>
<span data-ttu-id="29d85-102">Specifies the settings for a binding used for the WS-MetadataExchange (WS-MEX) message exchange over HTTPS.</span><span class="sxs-lookup"><span data-stu-id="29d85-102">Specifies the settings for a binding used for the WS-MetadataExchange (WS-MEX) message exchange over HTTPS.</span></span>  
  
<span data-ttu-id="29d85-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="29d85-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="29d85-104">&nbsp;&nbsp;[ **\<system.serviceModel>** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="29d85-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="29d85-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bindings>** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="29d85-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="29d85-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<mexHttpsBinding>**</span><span class="sxs-lookup"><span data-stu-id="29d85-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<mexHttpsBinding>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29d85-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="29d85-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="29d85-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="29d85-108">Attributes and Elements</span></span>  
 <span data-ttu-id="29d85-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="29d85-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="29d85-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="29d85-110">Attributes</span></span>  
  
|<span data-ttu-id="29d85-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="29d85-111">Attribute</span></span>|<span data-ttu-id="29d85-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="29d85-112">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="29d85-113">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span><span class="sxs-lookup"><span data-stu-id="29d85-113">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="29d85-114">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="29d85-114">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="29d85-115">The default is 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="29d85-115">The default is 00:01:00.</span></span>|  
|`name`|<span data-ttu-id="29d85-116">A string that contains the configuration name of the binding.</span><span class="sxs-lookup"><span data-stu-id="29d85-116">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="29d85-117">This value should be unique because it is used as an identification for the binding.</span><span class="sxs-lookup"><span data-stu-id="29d85-117">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="29d85-118">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span><span class="sxs-lookup"><span data-stu-id="29d85-118">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="29d85-119">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="29d85-119">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="29d85-120">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span><span class="sxs-lookup"><span data-stu-id="29d85-120">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="29d85-121">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="29d85-121">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="29d85-122">The default is 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="29d85-122">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="29d85-123">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span><span class="sxs-lookup"><span data-stu-id="29d85-123">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="29d85-124">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="29d85-124">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="29d85-125">The default is 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="29d85-125">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="29d85-126">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span><span class="sxs-lookup"><span data-stu-id="29d85-126">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="29d85-127">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="29d85-127">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="29d85-128">The default is 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="29d85-128">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="29d85-129">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="29d85-129">Child Elements</span></span>  
 <span data-ttu-id="29d85-130">Yok.</span><span class="sxs-lookup"><span data-stu-id="29d85-130">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="29d85-131">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="29d85-131">Parent Elements</span></span>  
  
|<span data-ttu-id="29d85-132">Öğe</span><span class="sxs-lookup"><span data-stu-id="29d85-132">Element</span></span>|<span data-ttu-id="29d85-133">Açıklama</span><span class="sxs-lookup"><span data-stu-id="29d85-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="29d85-134">\<bindings></span><span class="sxs-lookup"><span data-stu-id="29d85-134">\<bindings></span></span>](bindings.md)|<span data-ttu-id="29d85-135">This element holds a collection of standard and custom bindings.</span><span class="sxs-lookup"><span data-stu-id="29d85-135">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="29d85-136">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="29d85-136">Remarks</span></span>  
 <span data-ttu-id="29d85-137">This binding is essentially a `WSHttpBinding` binding that supports transport-level security using certificates.</span><span class="sxs-lookup"><span data-stu-id="29d85-137">This binding is essentially a `WSHttpBinding` binding that supports transport-level security using certificates.</span></span> <span data-ttu-id="29d85-138">For more information about configuring and using such a metadata endpoint, see [How to: Configure a Custom WS-Metadata Exchange Binding](../../../wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md), [How to: Retrieve Metadata Over a non-MEX Binding](../../../wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md), and the sample [Custom Secure Metadata Endpoint](../../../wcf/samples/custom-secure-metadata-endpoint.md).</span><span class="sxs-lookup"><span data-stu-id="29d85-138">For more information about configuring and using such a metadata endpoint, see [How to: Configure a Custom WS-Metadata Exchange Binding](../../../wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md), [How to: Retrieve Metadata Over a non-MEX Binding](../../../wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md), and the sample [Custom Secure Metadata Endpoint](../../../wcf/samples/custom-secure-metadata-endpoint.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29d85-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="29d85-139">See also</span></span>

- <xref:System.ServiceModel.Description.MetadataExchangeBindings.CreateMexHttpsBinding%2A>
- <xref:System.ServiceModel.Configuration.MexHttpsBindingElement>
- [<span data-ttu-id="29d85-140">Nasıl yapılır: Yapılandırma Dosyası Kullanarak Bir Hizmet için Meta Verileri Yayımlama</span><span class="sxs-lookup"><span data-stu-id="29d85-140">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [<span data-ttu-id="29d85-141">Özel Bağlama Üzerinden Meta Veri Yayımlama ve Alma</span><span class="sxs-lookup"><span data-stu-id="29d85-141">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)
- [<span data-ttu-id="29d85-142">Nasıl yapılır: Özel Bir WS-Metadata Exchange Bağlaması Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="29d85-142">How to: Configure a Custom WS-Metadata Exchange Binding</span></span>](../../../wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md)
- [<span data-ttu-id="29d85-143">Nasıl yapılır: MEX Olmayan Bağlama Üzerinden Meta Verileri Alma</span><span class="sxs-lookup"><span data-stu-id="29d85-143">How to: Retrieve Metadata Over a non-MEX Binding</span></span>](../../../wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md)
- [<span data-ttu-id="29d85-144">Özel Güvenli Meta Veri Uç Noktaları</span><span class="sxs-lookup"><span data-stu-id="29d85-144">Custom Secure Metadata Endpoint</span></span>](../../../wcf/samples/custom-secure-metadata-endpoint.md)
- [<span data-ttu-id="29d85-145">Meta Veriler</span><span class="sxs-lookup"><span data-stu-id="29d85-145">Metadata</span></span>](../../../wcf/feature-details/metadata.md)
- [<span data-ttu-id="29d85-146">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="29d85-146">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="29d85-147">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="29d85-147">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="29d85-148">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="29d85-148">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="29d85-149">\<binding></span><span class="sxs-lookup"><span data-stu-id="29d85-149">\<binding></span></span>](bindings.md)
