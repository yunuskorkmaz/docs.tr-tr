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
ms.openlocfilehash: 27d532633f08a5a560da61e904917c1faa35126c
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91151369"
---
# <a name="compatsortnlsversion-element"></a><span data-ttu-id="a4eba-102">\<CompatSortNLSVersion> Öğesi</span><span class="sxs-lookup"><span data-stu-id="a4eba-102">\<CompatSortNLSVersion> Element</span></span>

<span data-ttu-id="a4eba-103">Çalışma zamanının, dize karşılaştırmaları yaparken eski sıralama düzenlerini kullanması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="a4eba-103">Specifies that the runtime should use legacy sort orders when performing string comparisons.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<CompatSortNLSVersion>**  
  
## <a name="syntax"></a><span data-ttu-id="a4eba-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="a4eba-104">Syntax</span></span>  
  
```xml  
<CompatSortNLSVersion
   enabled="4096"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a4eba-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="a4eba-105">Attributes and Elements</span></span>  

 <span data-ttu-id="a4eba-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a4eba-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a4eba-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a4eba-107">Attributes</span></span>  
  
|<span data-ttu-id="a4eba-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="a4eba-108">Attribute</span></span>|<span data-ttu-id="a4eba-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a4eba-109">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="a4eba-110">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="a4eba-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="a4eba-111">Sıralama düzeni kullanılacak olan yerel ayar kimliğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="a4eba-111">Specifies the locale ID whose sort order is to be used.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="a4eba-112">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="a4eba-112">enabled Attribute</span></span>  
  
|<span data-ttu-id="a4eba-113">Değer</span><span class="sxs-lookup"><span data-stu-id="a4eba-113">Value</span></span>|<span data-ttu-id="a4eba-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a4eba-114">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a4eba-115">4096</span><span class="sxs-lookup"><span data-stu-id="a4eba-115">4096</span></span>|<span data-ttu-id="a4eba-116">Alternatif bir sıralama düzenini temsil eden yerel ayar kimliği.</span><span class="sxs-lookup"><span data-stu-id="a4eba-116">The locale ID that represents an alternate sort order.</span></span> <span data-ttu-id="a4eba-117">Bu durumda 4096, .NET Framework 3,5 ve önceki sürümlerin sıralama düzenini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="a4eba-117">In this case, 4096 represents the sort order of the .NET Framework 3.5 and earlier versions.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a4eba-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="a4eba-118">Child Elements</span></span>  

 <span data-ttu-id="a4eba-119">Yok.</span><span class="sxs-lookup"><span data-stu-id="a4eba-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a4eba-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="a4eba-120">Parent Elements</span></span>  
  
|<span data-ttu-id="a4eba-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="a4eba-121">Element</span></span>|<span data-ttu-id="a4eba-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a4eba-122">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="a4eba-123">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="a4eba-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="a4eba-124">Çalışma zamanı başlatma seçenekleri hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="a4eba-124">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a4eba-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a4eba-125">Remarks</span></span>  

 <span data-ttu-id="a4eba-126">.NET Framework 4 ' deki sınıf tarafından gerçekleştirilen dize karşılaştırma, sıralama ve büyük/küçük harf işlemleri <xref:System.Globalization.CompareInfo?displayProperty=nameWithType> Unicode 5,1 standardına uygun olduğundan, ve gibi dize karşılaştırma yöntemlerinin sonuçları, <xref:System.String.Compare%28System.String%2CSystem.String%29?displayProperty=nameWithType> <xref:System.String.LastIndexOf%28System.String%29?displayProperty=nameWithType> .NET Framework önceki sürümlerinden farklı olabilir.</span><span class="sxs-lookup"><span data-stu-id="a4eba-126">Because string comparison, sorting, and casing operations performed by the <xref:System.Globalization.CompareInfo?displayProperty=nameWithType> class in the .NET Framework 4 conform to the Unicode 5.1 standard, the results of string comparison methods such as <xref:System.String.Compare%28System.String%2CSystem.String%29?displayProperty=nameWithType> and <xref:System.String.LastIndexOf%28System.String%29?displayProperty=nameWithType> may differ from previous versions of the .NET Framework.</span></span> <span data-ttu-id="a4eba-127">Uygulamanız eski davranışa bağımlıysa, uygulamanın yapılandırma dosyasına öğesini ekleyerek .NET Framework 3,5 ve önceki sürümlerde kullanılan dize karşılaştırma ve sıralama kurallarını geri yükleyebilirsiniz `<CompatSortNLSVersion>` .</span><span class="sxs-lookup"><span data-stu-id="a4eba-127">If your application depends on legacy behavior, you can restore the string comparison and sorting rules used in the .NET Framework 3.5 and earlier versions by including the `<CompatSortNLSVersion>` element in your application's configuration file.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="a4eba-128">Eski dize karşılaştırma ve sıralama kurallarını geri yüklemek, sort00001000.dll dinamik bağlantı kitaplığının yerel sistemde kullanılabilir olmasını da gerektirir.</span><span class="sxs-lookup"><span data-stu-id="a4eba-128">Restoring legacy string comparison and sorting rules also requires the sort00001000.dll dynamic link library to be available on the local system.</span></span>  
  
 <span data-ttu-id="a4eba-129">Ayrıca, <xref:System.AppDomainSetup.SetCompatibilitySwitches%2A> uygulama etki alanını oluştururken "NetFx40_Legacy20SortingBehavior" dizesini yöntemine geçirerek belirli bir uygulama etki alanındaki eski dize sıralama ve karşılaştırma kurallarını da kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a4eba-129">You can also use legacy string sorting and comparison rules in a specific application domain by passing the string "NetFx40_Legacy20SortingBehavior" to the <xref:System.AppDomainSetup.SetCompatibilitySwitches%2A> method when you create the application domain.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a4eba-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="a4eba-130">Example</span></span>  

 <span data-ttu-id="a4eba-131">Aşağıdaki örnek iki nesne oluşturur <xref:System.String> ve <xref:System.String.Compare%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> geçerli kültürün kurallarını kullanarak bunları karşılaştırmak için yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="a4eba-131">The following example instantiates two <xref:System.String> objects and calls the <xref:System.String.Compare%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> method to compare them by using the conventions of the current culture.</span></span>  
  
 [!code-csharp[String.BreakingChanges#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/string.breakingchanges/cs/example1.cs#1)]
 [!code-vb[String.BreakingChanges#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/string.breakingchanges/vb/example1.vb#1)]  
  
 <span data-ttu-id="a4eba-132">.NET Framework 4 ' te örneği çalıştırdığınızda aşağıdaki çıktıyı görüntüler:</span><span class="sxs-lookup"><span data-stu-id="a4eba-132">When you run the example on the .NET Framework 4, it displays the following output:</span></span>
  
```console
sta follows a in the sort order.  
```  
  
 <span data-ttu-id="a4eba-133">Bu, örneği .NET Framework 3,5 ' de çalıştırdığınızda görüntülenen çıktıdan tamamen farklıdır:</span><span class="sxs-lookup"><span data-stu-id="a4eba-133">This is completely different from the output that is displayed when you run the example on the .NET Framework 3.5:</span></span>
  
```console
sta equals a in the sort order.  
```  
  
 <span data-ttu-id="a4eba-134">Ancak, aşağıdaki yapılandırma dosyasını örnek dizinine ekleyip .NET Framework 4 ' te örneği çalıştırırsanız, çıkış, .NET Framework 3,5 üzerinde çalıştırıldığında örnek tarafından oluşturulan ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="a4eba-134">However, if you add the following configuration file to the example's directory and then run the example on the .NET Framework 4, the output is identical to that produced by the example when it is run on the .NET Framework 3.5.</span></span>  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
   <runtime>  
      <CompatSortNLSVersion enabled="4096"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a4eba-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a4eba-135">See also</span></span>

- [<span data-ttu-id="a4eba-136">Çalışma zamanı ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="a4eba-136">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="a4eba-137">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="a4eba-137">Configuration File Schema</span></span>](../index.md)
