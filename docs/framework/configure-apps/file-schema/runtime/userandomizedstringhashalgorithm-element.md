---
title: '&lt;UseRandomizedStringHashAlgorithm&gt; öğesi'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- UseRandomizedStringHashAlgorithm element
- <UseRandomizedStringHashAlgorithm> element
ms.assetid: c08125d6-56cc-4b23-b482-813ff85dc630
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a515c3011905c4f5c18ed9d3e8edf489428c04d8
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="ltuserandomizedstringhashalgorithmgt-element"></a><span data-ttu-id="d5c11-102">&lt;UseRandomizedStringHashAlgorithm&gt; öğesi</span><span class="sxs-lookup"><span data-stu-id="d5c11-102">&lt;UseRandomizedStringHashAlgorithm&gt; Element</span></span>
<span data-ttu-id="d5c11-103">Ortak dil çalışma zamanı üzerinde karma kodlarını dizeleri hesaplar olup olmadığını belirleyen bir uygulama etki alanı temelinde.</span><span class="sxs-lookup"><span data-stu-id="d5c11-103">Determines whether the common language runtime calculates hash codes for strings on a per application domain basis.</span></span>  
  
 <span data-ttu-id="d5c11-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="d5c11-104">\<configuration></span></span>  
<span data-ttu-id="d5c11-105">\<çalışma zamanı ></span><span class="sxs-lookup"><span data-stu-id="d5c11-105">\<runtime></span></span>  
<span data-ttu-id="d5c11-106">\<UseRandomizedStringHashAlgorithm ></span><span class="sxs-lookup"><span data-stu-id="d5c11-106">\<UseRandomizedStringHashAlgorithm></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5c11-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d5c11-107">Syntax</span></span>  
  
```xml  
<UseRandomizedStringHashAlgorithm   
   enabled=0|1 />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d5c11-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="d5c11-108">Attributes and Elements</span></span>  
 <span data-ttu-id="d5c11-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d5c11-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d5c11-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d5c11-110">Attributes</span></span>  
  
|<span data-ttu-id="d5c11-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="d5c11-111">Attribute</span></span>|<span data-ttu-id="d5c11-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d5c11-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="d5c11-113">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="d5c11-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="d5c11-114">Dizeler için karma kodlarını çubuğunda hesaplanıp hesaplanmayacağını belirler bir uygulama etki alanı temelinde.</span><span class="sxs-lookup"><span data-stu-id="d5c11-114">Specifies whether hash codes for strings are calculated on a per application domain basis.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="d5c11-115">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="d5c11-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="d5c11-116">Değer</span><span class="sxs-lookup"><span data-stu-id="d5c11-116">Value</span></span>|<span data-ttu-id="d5c11-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d5c11-117">Description</span></span>|  
|-----------|-----------------|  
|`0`|<span data-ttu-id="d5c11-118">Ortak dil çalışma zamanı dizeleri için karma kodları üzerinde işlem olmayan bir uygulama etki alanı temelinde; tek bir algoritma dize karma kodlarını hesaplamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d5c11-118">The common language runtime does not compute hash codes for strings on a per application domain basis; a single algorithm is used to calculate string hash codes.</span></span> <span data-ttu-id="d5c11-119">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="d5c11-119">This is the default.</span></span>|  
|`1`|<span data-ttu-id="d5c11-120">Ortak dil çalışma zamanı üzerinde karma kodlarını dizeleri hesaplar bir uygulama etki alanı temelinde.</span><span class="sxs-lookup"><span data-stu-id="d5c11-120">The common language runtime computes hash codes for strings on a per application domain basis.</span></span> <span data-ttu-id="d5c11-121">Farklı uygulama etki alanları ve farklı işlemler aynı dizeleri farklı karma kodlarını olacaktır.</span><span class="sxs-lookup"><span data-stu-id="d5c11-121">Identical strings in different application domains and in different processes will have different hash codes.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d5c11-122">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="d5c11-122">Child Elements</span></span>  
 <span data-ttu-id="d5c11-123">Yok.</span><span class="sxs-lookup"><span data-stu-id="d5c11-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d5c11-124">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="d5c11-124">Parent Elements</span></span>  
  
|<span data-ttu-id="d5c11-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="d5c11-125">Element</span></span>|<span data-ttu-id="d5c11-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d5c11-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="d5c11-127">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="d5c11-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="d5c11-128">Çalışma zamanı başlatma seçenekleri hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="d5c11-128">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d5c11-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d5c11-129">Remarks</span></span>  
 <span data-ttu-id="d5c11-130">Varsayılan olarak, <xref:System.StringComparer> sınıfı ve <xref:System.String.GetHashCode%2A?displayProperty=nameWithType> yöntemi uygulama etki alanları arasında tutarlı karma kodu oluşturan tek bir karma algoritmasını kullanın.</span><span class="sxs-lookup"><span data-stu-id="d5c11-130">By default, the <xref:System.StringComparer> class and the <xref:System.String.GetHashCode%2A?displayProperty=nameWithType> method use a single hashing algorithm that produces a consistent hash code across application domains.</span></span> <span data-ttu-id="d5c11-131">Bu ayar için eşdeğerdir `enabled` özniteliği `<UseRandomizedStringHashAlgorithm>` öğesine `0`.</span><span class="sxs-lookup"><span data-stu-id="d5c11-131">This is equivalent to setting the `enabled` attribute of the `<UseRandomizedStringHashAlgorithm>` element to `0`.</span></span> <span data-ttu-id="d5c11-132">Kullanılan karma algoritma budur [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d5c11-132">This is the hashing algorithm used in the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)].</span></span>  
  
 <span data-ttu-id="d5c11-133"><xref:System.StringComparer> Sınıfı ve <xref:System.String.GetHashCode%2A?displayProperty=nameWithType> yöntemi de karma kodlarını çubuğunda hesaplar farklı bir karma algoritma kullanın bir uygulama etki alanı temelinde.</span><span class="sxs-lookup"><span data-stu-id="d5c11-133">The <xref:System.StringComparer> class and the <xref:System.String.GetHashCode%2A?displayProperty=nameWithType> method can also use a different hashing algorithm that computes hash codes on a per application domain basis.</span></span> <span data-ttu-id="d5c11-134">Sonuç olarak, karma kodlarını eşdeğer dizeleri için uygulama etki alanları arasında farklılık gösterir.</span><span class="sxs-lookup"><span data-stu-id="d5c11-134">As a result, hash codes for equivalent strings will differ across application domains.</span></span> <span data-ttu-id="d5c11-135">Bu bir katılımı özelliğidir; Bunu yararlanmak için ayarlamalısınız `enabled` özniteliği `<UseRandomizedStringHashAlgorithm>` öğesine `1`.</span><span class="sxs-lookup"><span data-stu-id="d5c11-135">This is an opt-in feature; to take advantage of it, you must set the `enabled` attribute of the `<UseRandomizedStringHashAlgorithm>` element to `1`.</span></span>  
  
 <span data-ttu-id="d5c11-136">Bir karma tablosu dize aramada genellikle bir O(1) işlemdir.</span><span class="sxs-lookup"><span data-stu-id="d5c11-136">The string lookup in a hash table is typically an O(1) operation.</span></span> <span data-ttu-id="d5c11-137">Ancak, çok sayıda çakışma oluştuğunda, arama O olabilir (n<sup>2</sup>) işlemi.</span><span class="sxs-lookup"><span data-stu-id="d5c11-137">However, when a large number of collisions occur, the lookup can become an O(n<sup>2</sup>) operation.</span></span> <span data-ttu-id="d5c11-138">Kullanabileceğiniz `<UseRandomizedStringHashAlgorithm>` rastgele bir karma algoritma başına içinden karma kodlarını hesaplanır anahtarlar veri giriş, özellikle dayanır bağlandığınızda sırayla olası çakışmaları sayısını sınırlar, uygulama etki alanı oluşturmak için yapılandırma öğesi kullanıcılar tarafından.</span><span class="sxs-lookup"><span data-stu-id="d5c11-138">You can use the `<UseRandomizedStringHashAlgorithm>` configuration element to generate a random hashing algorithm per application domain, which in turn limits the number of potential collisions, particularly when the keys from which the hash codes are calculated are based on data input by users.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d5c11-139">Örnek</span><span class="sxs-lookup"><span data-stu-id="d5c11-139">Example</span></span>  
 <span data-ttu-id="d5c11-140">Aşağıdaki örnek tanımlayan bir `DisplayString` özel dize sabiti içeren sınıf `s`, değeri olan "Dize budur."</span><span class="sxs-lookup"><span data-stu-id="d5c11-140">The following example defines a `DisplayString` class that includes a private string constant, `s`, whose value is "This is a string."</span></span> <span data-ttu-id="d5c11-141">Ayrıca içeren bir `ShowStringHashCode` dize değeri ve karma kodunu içinde yöntemi Yürütülüyor uygulama etki alanı adı ile birlikte görüntüler yöntemi.</span><span class="sxs-lookup"><span data-stu-id="d5c11-141">It also includes a `ShowStringHashCode` method that displays the string value and its hash code along with the name of the application domain in which the method is executing.</span></span>  
  
 [!code-csharp[System.String.GetHashCode#2](../../../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.String.GetHashCode/CS/perdomain.cs#2)]
 [!code-vb[System.String.GetHashCode#2](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.String.GetHashCode/VB/perdomain.vb#2)]  
  
 <span data-ttu-id="d5c11-142">Örnek bir yapılandırma dosyası girmeden çalıştırdığınızda, aşağıdakine benzer bir çıktı görüntüler.</span><span class="sxs-lookup"><span data-stu-id="d5c11-142">When you run the example without supplying a configuration file, it displays output similar to the following.</span></span> <span data-ttu-id="d5c11-143">Karma kodlarını dize için iki uygulama etki alanları aynı olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="d5c11-143">Note that the hash codes for the string are identical in the two application domains.</span></span>  
  
```  
String 'This is a string.' in domain 'PerDomain.exe': 941BCEAC  
String 'This is a string.' in domain 'NewDomain': 941BCEAC  
```  
  
 <span data-ttu-id="d5c11-144">Ancak, örneğin dizinine aşağıdaki yapılandırma dosyası ekleyin ve ardından örnek çalıştırırsanız, karma kodlarını aynı dize için uygulama etki alanına göre farklılık gösterir.</span><span class="sxs-lookup"><span data-stu-id="d5c11-144">However, if you add the following configuration file to the example's directory and then run the example, the hash codes for the same string will differ by application domain.</span></span>  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
   <runtime>  
      <UseRandomizedStringHashAlgorithm enabled="1" />  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="d5c11-145">Yapılandırma dosyası mevcut olduğunda, aşağıdaki çıktı örneği görüntüler:</span><span class="sxs-lookup"><span data-stu-id="d5c11-145">When the configuration file is present, the example displays the following output:</span></span>  
  
```  
String 'This is a string.' in domain 'PerDomain.exe': 5435776D  
String 'This is a string.' in domain 'NewDomain': 75CC8236  
```  
  
## <a name="see-also"></a><span data-ttu-id="d5c11-146">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d5c11-146">See Also</span></span>  
 <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType>  
 <xref:System.String.GetHashCode%2A?displayProperty=nameWithType>  
 <xref:System.Object.GetHashCode%2A?displayProperty=nameWithType>
