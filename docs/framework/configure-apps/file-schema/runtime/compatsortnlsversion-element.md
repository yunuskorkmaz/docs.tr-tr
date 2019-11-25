---
title: <CompatSortNLSVersion> Öğesi
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- <CompatSortNLSVersion> element
- CompatSortNLSVersion element
ms.assetid: 782cc82e-83f7-404a-80b7-6d3061a8b6e3
ms.openlocfilehash: 5de760fe07283ddee36b3475fa0975c8d46776e5
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73969253"
---
# <a name="compatsortnlsversion-element"></a><span data-ttu-id="e7552-102">\<CompatSortNLSVersion > öğesi</span><span class="sxs-lookup"><span data-stu-id="e7552-102">\<CompatSortNLSVersion> Element</span></span>
<span data-ttu-id="e7552-103">Çalışma zamanının, dize karşılaştırmaları yaparken eski sıralama düzenlerini kullanması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="e7552-103">Specifies that the runtime should use legacy sort orders when performing string comparisons.</span></span>  
  
<span data-ttu-id="e7552-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="e7552-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="e7552-105">&nbsp; &nbsp;[ **\<runtime >** ](runtime-element.md) </span><span class="sxs-lookup"><span data-stu-id="e7552-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="e7552-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<CompatSortNLSVersion >**</span><span class="sxs-lookup"><span data-stu-id="e7552-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<CompatSortNLSVersion>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7552-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e7552-107">Syntax</span></span>  
  
```xml  
<CompatSortNLSVersion    
   enabled="4096"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e7552-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="e7552-108">Attributes and Elements</span></span>  
 <span data-ttu-id="e7552-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e7552-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e7552-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e7552-110">Attributes</span></span>  
  
|<span data-ttu-id="e7552-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="e7552-111">Attribute</span></span>|<span data-ttu-id="e7552-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e7552-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="e7552-113">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="e7552-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="e7552-114">Sıralama düzeni kullanılacak olan yerel ayar kimliğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="e7552-114">Specifies the locale ID whose sort order is to be used.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="e7552-115">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="e7552-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="e7552-116">Değer</span><span class="sxs-lookup"><span data-stu-id="e7552-116">Value</span></span>|<span data-ttu-id="e7552-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e7552-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e7552-118">4096</span><span class="sxs-lookup"><span data-stu-id="e7552-118">4096</span></span>|<span data-ttu-id="e7552-119">Alternatif bir sıralama düzenini temsil eden yerel ayar kimliği.</span><span class="sxs-lookup"><span data-stu-id="e7552-119">The locale ID that represents an alternate sort order.</span></span> <span data-ttu-id="e7552-120">Bu durumda 4096, .NET Framework 3,5 ve önceki sürümlerin sıralama düzenini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="e7552-120">In this case, 4096 represents the sort order of the .NET Framework 3.5 and earlier versions.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e7552-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="e7552-121">Child Elements</span></span>  
 <span data-ttu-id="e7552-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="e7552-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e7552-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="e7552-123">Parent Elements</span></span>  
  
|<span data-ttu-id="e7552-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="e7552-124">Element</span></span>|<span data-ttu-id="e7552-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e7552-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="e7552-126">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="e7552-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="e7552-127">Çalışma zamanı başlatma seçenekleri hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="e7552-127">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e7552-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e7552-128">Remarks</span></span>  
 <span data-ttu-id="e7552-129">.NET Framework 4 ' te <xref:System.Globalization.CompareInfo?displayProperty=nameWithType> sınıfı tarafından gerçekleştirilen dize karşılaştırma, sıralama ve büyük/küçük harf işlemleri Unicode 5,1 standardına uygun olduğundan, <xref:System.String.Compare%28System.String%2CSystem.String%29?displayProperty=nameWithType> ve <xref:System.String.LastIndexOf%28System.String%29?displayProperty=nameWithType> gibi dize karşılaştırma yöntemlerinin sonuçları .NET Framework önceki sürümlerinden farklı olabilir.</span><span class="sxs-lookup"><span data-stu-id="e7552-129">Because string comparison, sorting, and casing operations performed by the <xref:System.Globalization.CompareInfo?displayProperty=nameWithType> class in the .NET Framework 4 conform to the Unicode 5.1 standard, the results of string comparison methods such as <xref:System.String.Compare%28System.String%2CSystem.String%29?displayProperty=nameWithType> and <xref:System.String.LastIndexOf%28System.String%29?displayProperty=nameWithType> may differ from previous versions of the .NET Framework.</span></span> <span data-ttu-id="e7552-130">Uygulamanız eski davranışa bağımlıysa, uygulamanızın yapılandırma dosyasına `<CompatSortNLSVersion>` öğesini ekleyerek .NET Framework 3,5 ve önceki sürümlerde kullanılan dize karşılaştırma ve sıralama kurallarını geri yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e7552-130">If your application depends on legacy behavior, you can restore the string comparison and sorting rules used in the .NET Framework 3.5 and earlier versions by including the `<CompatSortNLSVersion>` element in your application's configuration file.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="e7552-131">Eski dize karşılaştırma ve sıralama kurallarını geri yüklemek, sort00001000.dll dinamik bağlantı kitaplığının yerel sistemde kullanılabilir olmasını da gerektirir.</span><span class="sxs-lookup"><span data-stu-id="e7552-131">Restoring legacy string comparison and sorting rules also requires the sort00001000.dll dynamic link library to be available on the local system.</span></span>  
  
 <span data-ttu-id="e7552-132">Ayrıca, uygulama etki alanını oluştururken "NetFx40_Legacy20SortingBehavior" dizesini <xref:System.AppDomainSetup.SetCompatibilitySwitches%2A> yöntemine geçirerek belirli bir uygulama etki alanındaki eski dize sıralama ve karşılaştırma kurallarını da kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e7552-132">You can also use legacy string sorting and comparison rules in a specific application domain by passing the string "NetFx40_Legacy20SortingBehavior" to the <xref:System.AppDomainSetup.SetCompatibilitySwitches%2A> method when you create the application domain.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e7552-133">Örnek</span><span class="sxs-lookup"><span data-stu-id="e7552-133">Example</span></span>  
 <span data-ttu-id="e7552-134">Aşağıdaki örnek iki <xref:System.String> nesnesini örnekleyerek, geçerli kültürün kurallarını kullanarak bunları karşılaştırmak için <xref:System.String.Compare%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="e7552-134">The following example instantiates two <xref:System.String> objects and calls the <xref:System.String.Compare%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> method to compare them by using the conventions of the current culture.</span></span>  
  
 [!code-csharp[String.BreakingChanges#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/string.breakingchanges/cs/example1.cs#1)]
 [!code-vb[String.BreakingChanges#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/string.breakingchanges/vb/example1.vb#1)]  
  
 <span data-ttu-id="e7552-135">.NET Framework 4 ' te örneği çalıştırdığınızda aşağıdaki çıktıyı görüntüler:</span><span class="sxs-lookup"><span data-stu-id="e7552-135">When you run the example on the .NET Framework 4, it displays the following output:</span></span>
  
```console
sta follows a in the sort order.  
```  
  
 <span data-ttu-id="e7552-136">Bu, örneği .NET Framework 3,5 ' de çalıştırdığınızda görüntülenen çıktıdan tamamen farklıdır:</span><span class="sxs-lookup"><span data-stu-id="e7552-136">This is completely different from the output that is displayed when you run the example on the .NET Framework 3.5:</span></span>
  
```console
sta equals a in the sort order.  
```  
  
 <span data-ttu-id="e7552-137">Ancak, aşağıdaki yapılandırma dosyasını örnek dizinine ekleyip .NET Framework 4 ' te örneği çalıştırırsanız, çıkış, .NET Framework 3,5 üzerinde çalıştırıldığında örnek tarafından oluşturulan ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="e7552-137">However, if you add the following configuration file to the example's directory and then run the example on the .NET Framework 4, the output is identical to that produced by the example when it is run on the .NET Framework 3.5.</span></span>  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
   <runtime>  
      <CompatSortNLSVersion enabled="4096"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e7552-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e7552-138">See also</span></span>

- [<span data-ttu-id="e7552-139">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="e7552-139">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="e7552-140">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="e7552-140">Configuration File Schema</span></span>](../index.md)
