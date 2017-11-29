---
title: "&lt;CompatSortNLSVersion&gt; öğesi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- <CompatSortNLSVersion> element
- CompatSortNLSVersion element
ms.assetid: 782cc82e-83f7-404a-80b7-6d3061a8b6e3
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 8d82187248e743d9081a97411f2ff2ad84707e61
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltcompatsortnlsversiongt-element"></a><span data-ttu-id="43c93-102">&lt;CompatSortNLSVersion&gt; öğesi</span><span class="sxs-lookup"><span data-stu-id="43c93-102">&lt;CompatSortNLSVersion&gt; Element</span></span>
<span data-ttu-id="43c93-103">Çalışma zamanının, dize karşılaştırmaları yaparken eski sıralama düzenlerini kullanması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="43c93-103">Specifies that the runtime should use legacy sort orders when performing string comparisons.</span></span>  
  
 <span data-ttu-id="43c93-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="43c93-104">\<configuration></span></span>  
<span data-ttu-id="43c93-105">\<çalışma zamanı ></span><span class="sxs-lookup"><span data-stu-id="43c93-105">\<runtime></span></span>  
<span data-ttu-id="43c93-106">\<CompatSortNLSVersion > öğesi</span><span class="sxs-lookup"><span data-stu-id="43c93-106">\<CompatSortNLSVersion> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43c93-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="43c93-107">Syntax</span></span>  
  
```xml  
<CompatSortNLSVersion    
   enabled="4096"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="43c93-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="43c93-108">Attributes and Elements</span></span>  
 <span data-ttu-id="43c93-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="43c93-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="43c93-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="43c93-110">Attributes</span></span>  
  
|<span data-ttu-id="43c93-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="43c93-111">Attribute</span></span>|<span data-ttu-id="43c93-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="43c93-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="43c93-113">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="43c93-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="43c93-114">Sıralama düzeni kullanılacak olan yerel ayar kimliğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="43c93-114">Specifies the locale ID whose sort order is to be used.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="43c93-115">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="43c93-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="43c93-116">Değer</span><span class="sxs-lookup"><span data-stu-id="43c93-116">Value</span></span>|<span data-ttu-id="43c93-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="43c93-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="43c93-118">4096</span><span class="sxs-lookup"><span data-stu-id="43c93-118">4096</span></span>|<span data-ttu-id="43c93-119">Alternatif bir sıralama düzenini temsil eden yerel ayar kimliği.</span><span class="sxs-lookup"><span data-stu-id="43c93-119">The locale ID that represents an alternate sort order.</span></span> <span data-ttu-id="43c93-120">Bu durumda, 4096 sıralama düzenini temsil eden [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)] ve önceki sürümleri.</span><span class="sxs-lookup"><span data-stu-id="43c93-120">In this case, 4096 represents the sort order of the [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)] and earlier versions.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="43c93-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="43c93-121">Child Elements</span></span>  
 <span data-ttu-id="43c93-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="43c93-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="43c93-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="43c93-123">Parent Elements</span></span>  
  
|<span data-ttu-id="43c93-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="43c93-124">Element</span></span>|<span data-ttu-id="43c93-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="43c93-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="43c93-126">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="43c93-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="43c93-127">Çalışma zamanı başlatma seçenekleri hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="43c93-127">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="43c93-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="43c93-128">Remarks</span></span>  
 <span data-ttu-id="43c93-129">Dize karşılaştırması, sıralama ve büyük/küçük harf işlemleri tarafından gerçekleştirilen çünkü <xref:System.Globalization.CompareInfo?displayProperty=nameWithType> sınıfını [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] Unicode 5.1 için standart, dize karşılaştırma yöntemlerini sonuçlarını gibi uygun <xref:System.String.Compare%28System.String%2CSystem.String%29?displayProperty=nameWithType> ve <xref:System.String.LastIndexOf%28System.String%29?displayProperty=nameWithType> farklı olabilir .NET Framework'ün önceki'yi tıklatın.</span><span class="sxs-lookup"><span data-stu-id="43c93-129">Because string comparison, sorting, and casing operations performed by the <xref:System.Globalization.CompareInfo?displayProperty=nameWithType> class in the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] conform to the Unicode 5.1 standard, the results of string comparison methods such as <xref:System.String.Compare%28System.String%2CSystem.String%29?displayProperty=nameWithType> and <xref:System.String.LastIndexOf%28System.String%29?displayProperty=nameWithType> may differ from previous versions of the .NET Framework.</span></span> <span data-ttu-id="43c93-130">Eski davranışı, uygulamanızın bağımlı olması durumunda, dize karşılaştırma geri yükleyebilir ve kuralları sıralama kullanılır [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)] ve önceki sürümleri de dahil olmak üzere tarafından `<CompatSortNLSVersion>` uygulamanızın yapılandırma dosyasına öğe.</span><span class="sxs-lookup"><span data-stu-id="43c93-130">If your application depends on legacy behavior, you can restore the string comparison and sorting rules used in the [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)] and earlier versions by including the `<CompatSortNLSVersion>` element in your application's configuration file.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="43c93-131">Eski dize karşılaştırma ve sıralama kurallarını geri yüklemek, sort00001000.dll dinamik bağlantı kitaplığının yerel sistemde kullanılabilir olmasını da gerektirir.</span><span class="sxs-lookup"><span data-stu-id="43c93-131">Restoring legacy string comparison and sorting rules also requires the sort00001000.dll dynamic link library to be available on the local system.</span></span>  
  
 <span data-ttu-id="43c93-132">Aynı zamanda eski dize sıralama ve karşılaştırma kurallarında belirli uygulama etki alanı "NetFx40_Legacy20SortingBehavior" dizesi geçirerek için kullanabileceğiniz <xref:System.AppDomainSetup.SetCompatibilitySwitches%2A> uygulama etki alanı oluşturduğunuzda yöntemi.</span><span class="sxs-lookup"><span data-stu-id="43c93-132">You can also use legacy string sorting and comparison rules in a specific application domain by passing the string "NetFx40_Legacy20SortingBehavior" to the <xref:System.AppDomainSetup.SetCompatibilitySwitches%2A> method when you create the application domain.</span></span>  
  
## <a name="example"></a><span data-ttu-id="43c93-133">Örnek</span><span class="sxs-lookup"><span data-stu-id="43c93-133">Example</span></span>  
 <span data-ttu-id="43c93-134">Aşağıdaki örnekte iki başlatır <xref:System.String> nesneleri ve çağrıları <xref:System.String.Compare%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> geçerli kültürü kurallarını kullanarak karşılaştırmak için yöntem.</span><span class="sxs-lookup"><span data-stu-id="43c93-134">The following example instantiates two <xref:System.String> objects and calls the <xref:System.String.Compare%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> method to compare them by using the conventions of the current culture.</span></span>  
  
 [!code-csharp[String.BreakingChanges#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/string.breakingchanges/cs/example1.cs#1)]
 [!code-vb[String.BreakingChanges#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/string.breakingchanges/vb/example1.vb#1)]  
  
 <span data-ttu-id="43c93-135">Örnek çalıştırdığınızda [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], aşağıdaki çıkış görüntüler.</span><span class="sxs-lookup"><span data-stu-id="43c93-135">When you run the example on the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], it displays the following output.</span></span>  
  
```  
sta follows a in the sort order.  
```  
  
 <span data-ttu-id="43c93-136">Bu örnek çalıştırdığınızda, görüntülenen çıktısından tamamen farklı [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="43c93-136">This is completely different from the output that is displayed when you run the example on the [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)].</span></span>  
  
```  
sta equals a in the sort order.  
```  
  
 <span data-ttu-id="43c93-137">Ancak, örneği aşağıdaki yapılandırma dosyası eklerseniz, dizin adı ve örnek sonra çalıştıracağınız [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], çıktı çalışırken örnek tarafından üretilen özdeş [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="43c93-137">However, if you add the following configuration file to the example's directory and then run the example on the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], the output is identical to that produced by the example when it is run on the [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)].</span></span>  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
   <runtime>  
      <CompatSortNLSVersion enabled="4096"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="43c93-138">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="43c93-138">See Also</span></span>  
 [<span data-ttu-id="43c93-139">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="43c93-139">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="43c93-140">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="43c93-140">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
