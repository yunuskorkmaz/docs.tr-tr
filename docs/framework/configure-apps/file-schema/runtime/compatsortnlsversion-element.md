---
title: '&lt;CompatSortNLSVersion&gt; öğesi'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- <CompatSortNLSVersion> element
- CompatSortNLSVersion element
ms.assetid: 782cc82e-83f7-404a-80b7-6d3061a8b6e3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a40a9e7ad5eb0b6e978054b5e7edcf35e53c42c7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54578513"
---
# <a name="ltcompatsortnlsversiongt-element"></a><span data-ttu-id="bd235-102">&lt;CompatSortNLSVersion&gt; öğesi</span><span class="sxs-lookup"><span data-stu-id="bd235-102">&lt;CompatSortNLSVersion&gt; Element</span></span>
<span data-ttu-id="bd235-103">Çalışma zamanının, dize karşılaştırmaları yaparken eski sıralama düzenlerini kullanması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="bd235-103">Specifies that the runtime should use legacy sort orders when performing string comparisons.</span></span>  
  
 <span data-ttu-id="bd235-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="bd235-104">\<configuration></span></span>  
<span data-ttu-id="bd235-105">\<çalışma zamanı ></span><span class="sxs-lookup"><span data-stu-id="bd235-105">\<runtime></span></span>  
<span data-ttu-id="bd235-106">\<CompatSortNLSVersion > öğesi</span><span class="sxs-lookup"><span data-stu-id="bd235-106">\<CompatSortNLSVersion> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd235-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bd235-107">Syntax</span></span>  
  
```xml  
<CompatSortNLSVersion    
   enabled="4096"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bd235-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="bd235-108">Attributes and Elements</span></span>  
 <span data-ttu-id="bd235-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="bd235-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bd235-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="bd235-110">Attributes</span></span>  
  
|<span data-ttu-id="bd235-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="bd235-111">Attribute</span></span>|<span data-ttu-id="bd235-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bd235-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="bd235-113">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="bd235-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="bd235-114">Sıralama düzeni kullanılacak olan yerel ayar kimliğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="bd235-114">Specifies the locale ID whose sort order is to be used.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="bd235-115">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="bd235-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="bd235-116">Değer</span><span class="sxs-lookup"><span data-stu-id="bd235-116">Value</span></span>|<span data-ttu-id="bd235-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bd235-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="bd235-118">4096</span><span class="sxs-lookup"><span data-stu-id="bd235-118">4096</span></span>|<span data-ttu-id="bd235-119">Alternatif bir sıralama düzenini temsil eden yerel ayar kimliği.</span><span class="sxs-lookup"><span data-stu-id="bd235-119">The locale ID that represents an alternate sort order.</span></span> <span data-ttu-id="bd235-120">Bu durumda, 4096 sıralama düzenini temsil eden [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)] ve önceki sürümleri.</span><span class="sxs-lookup"><span data-stu-id="bd235-120">In this case, 4096 represents the sort order of the [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)] and earlier versions.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bd235-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="bd235-121">Child Elements</span></span>  
 <span data-ttu-id="bd235-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="bd235-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bd235-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="bd235-123">Parent Elements</span></span>  
  
|<span data-ttu-id="bd235-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="bd235-124">Element</span></span>|<span data-ttu-id="bd235-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bd235-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="bd235-126">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="bd235-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="bd235-127">Çalışma zamanı başlatma seçenekleri hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="bd235-127">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bd235-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bd235-128">Remarks</span></span>  
 <span data-ttu-id="bd235-129">Dize karşılaştırması, sıralama ve büyük/küçük harf işlemleri tarafından gerçekleştirilen çünkü <xref:System.Globalization.CompareInfo?displayProperty=nameWithType> sınıfını [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] Unicode 5.1 standardına dize karşılaştırma yöntemlerinin sonuçları gibi uygun <xref:System.String.Compare%28System.String%2CSystem.String%29?displayProperty=nameWithType> ve <xref:System.String.LastIndexOf%28System.String%29?displayProperty=nameWithType> farklı olabilir .NET Framework'ün önceki'yi tıklatın.</span><span class="sxs-lookup"><span data-stu-id="bd235-129">Because string comparison, sorting, and casing operations performed by the <xref:System.Globalization.CompareInfo?displayProperty=nameWithType> class in the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] conform to the Unicode 5.1 standard, the results of string comparison methods such as <xref:System.String.Compare%28System.String%2CSystem.String%29?displayProperty=nameWithType> and <xref:System.String.LastIndexOf%28System.String%29?displayProperty=nameWithType> may differ from previous versions of the .NET Framework.</span></span> <span data-ttu-id="bd235-130">Uygulamanız eski davranışa bağlıysa, dize karşılaştırması geri yükleyebilirsiniz ve sıralama kurallarını kullanılan [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)] ve önceki sürümleri ekleyerek `<CompatSortNLSVersion>` uygulamanızın yapılandırma dosyasında öğesi.</span><span class="sxs-lookup"><span data-stu-id="bd235-130">If your application depends on legacy behavior, you can restore the string comparison and sorting rules used in the [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)] and earlier versions by including the `<CompatSortNLSVersion>` element in your application's configuration file.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="bd235-131">Eski dize karşılaştırma ve sıralama kurallarını geri yüklemek, sort00001000.dll dinamik bağlantı kitaplığının yerel sistemde kullanılabilir olmasını da gerektirir.</span><span class="sxs-lookup"><span data-stu-id="bd235-131">Restoring legacy string comparison and sorting rules also requires the sort00001000.dll dynamic link library to be available on the local system.</span></span>  
  
 <span data-ttu-id="bd235-132">Ayrıca eski dize sıralama ve karşılaştırma kurallarını belirli uygulama etki alanındaki "NetFx40_Legacy20SortingBehavior" dizesini geçirerek için kullanabileceğiniz <xref:System.AppDomainSetup.SetCompatibilitySwitches%2A> uygulama etki alanı oluşturduğunuzda yöntemi.</span><span class="sxs-lookup"><span data-stu-id="bd235-132">You can also use legacy string sorting and comparison rules in a specific application domain by passing the string "NetFx40_Legacy20SortingBehavior" to the <xref:System.AppDomainSetup.SetCompatibilitySwitches%2A> method when you create the application domain.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bd235-133">Örnek</span><span class="sxs-lookup"><span data-stu-id="bd235-133">Example</span></span>  
 <span data-ttu-id="bd235-134">Aşağıdaki örnek iki başlatır <xref:System.String> nesneleri ve çağrıları <xref:System.String.Compare%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> geçerli kültürün kurallarını kullanarak karşılaştırmak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="bd235-134">The following example instantiates two <xref:System.String> objects and calls the <xref:System.String.Compare%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> method to compare them by using the conventions of the current culture.</span></span>  
  
 [!code-csharp[String.BreakingChanges#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/string.breakingchanges/cs/example1.cs#1)]
 [!code-vb[String.BreakingChanges#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/string.breakingchanges/vb/example1.vb#1)]  
  
 <span data-ttu-id="bd235-135">Örnek çalıştırıldığında [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], aşağıdaki çıkışı görüntüler.</span><span class="sxs-lookup"><span data-stu-id="bd235-135">When you run the example on the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], it displays the following output.</span></span>  
  
```  
sta follows a in the sort order.  
```  
  
 <span data-ttu-id="bd235-136">Bu örneği çalıştırdığınızda, görüntülenen çıktısından tamamen farklıdır [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bd235-136">This is completely different from the output that is displayed when you run the example on the [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)].</span></span>  
  
```  
sta equals a in the sort order.  
```  
  
 <span data-ttu-id="bd235-137">Ancak, örneği aşağıdaki yapılandırma dosyası eklerseniz dizinine ve sonra örneği çalıştırırsanız [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], çıkış, çalıştırıldığında örnek tarafından oluşturulanla aynıdır [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bd235-137">However, if you add the following configuration file to the example's directory and then run the example on the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], the output is identical to that produced by the example when it is run on the [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)].</span></span>  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
   <runtime>  
      <CompatSortNLSVersion enabled="4096"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="bd235-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bd235-138">See also</span></span>
- [<span data-ttu-id="bd235-139">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="bd235-139">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="bd235-140">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="bd235-140">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
