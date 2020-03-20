---
title: <UseRandomizedStringHashAlgorithm> Öğesi
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- UseRandomizedStringHashAlgorithm element
- <UseRandomizedStringHashAlgorithm> element
ms.assetid: c08125d6-56cc-4b23-b482-813ff85dc630
ms.openlocfilehash: a9afa0db516a542b74d08a4c3754a3244abbbea7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153783"
---
# <a name="userandomizedstringhashalgorithm-element"></a><span data-ttu-id="75f50-102">\<RandomizeStringHashAlgorithm> Elemanı</span><span class="sxs-lookup"><span data-stu-id="75f50-102">\<UseRandomizedStringHashAlgorithm> Element</span></span>
<span data-ttu-id="75f50-103">Ortak dil çalışma zamanının, uygulama etki alanı bazında dizeleri karma kodları hesaplayıp hesaplamadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="75f50-103">Determines whether the common language runtime calculates hash codes for strings on a per application domain basis.</span></span>  
  
<span data-ttu-id="75f50-104">[**\<yapılandırma>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="75f50-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="75f50-105">&nbsp;&nbsp;[**\<çalışma zamanı>**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="75f50-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="75f50-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<RandomizeStringHashAlgorithm>kullanın**</span><span class="sxs-lookup"><span data-stu-id="75f50-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<UseRandomizedStringHashAlgorithm>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="75f50-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="75f50-107">Syntax</span></span>  
  
```xml  
<UseRandomizedStringHashAlgorithm
   enabled=0|1 />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="75f50-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="75f50-108">Attributes and Elements</span></span>  
 <span data-ttu-id="75f50-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="75f50-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="75f50-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="75f50-110">Attributes</span></span>  
  
|<span data-ttu-id="75f50-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="75f50-111">Attribute</span></span>|<span data-ttu-id="75f50-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="75f50-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="75f50-113">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="75f50-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="75f50-114">Dizeleri için karma kodları uygulama etki alanı bazında hesaplanıp hesaplanmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="75f50-114">Specifies whether hash codes for strings are calculated on a per application domain basis.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="75f50-115">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="75f50-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="75f50-116">Değer</span><span class="sxs-lookup"><span data-stu-id="75f50-116">Value</span></span>|<span data-ttu-id="75f50-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="75f50-117">Description</span></span>|  
|-----------|-----------------|  
|`0`|<span data-ttu-id="75f50-118">Ortak dil çalışma süresi, uygulama etki alanı bazında dizeleri için karma kodları hesaplamaz; dize karma kodlarını hesaplamak için tek bir algoritma kullanılır.</span><span class="sxs-lookup"><span data-stu-id="75f50-118">The common language runtime does not compute hash codes for strings on a per application domain basis; a single algorithm is used to calculate string hash codes.</span></span> <span data-ttu-id="75f50-119">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="75f50-119">This is the default.</span></span>|  
|`1`|<span data-ttu-id="75f50-120">Ortak dil çalışma zamanı, uygulama etki alanı bazında dizeleri karma kodları bilgi işlem.</span><span class="sxs-lookup"><span data-stu-id="75f50-120">The common language runtime computes hash codes for strings on a per application domain basis.</span></span> <span data-ttu-id="75f50-121">Farklı uygulama etki alanlarında ve farklı işlemlerde aynı dizeleri farklı karma kodları olacaktır.</span><span class="sxs-lookup"><span data-stu-id="75f50-121">Identical strings in different application domains and in different processes will have different hash codes.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="75f50-122">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="75f50-122">Child Elements</span></span>  
 <span data-ttu-id="75f50-123">Yok.</span><span class="sxs-lookup"><span data-stu-id="75f50-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="75f50-124">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="75f50-124">Parent Elements</span></span>  
  
|<span data-ttu-id="75f50-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="75f50-125">Element</span></span>|<span data-ttu-id="75f50-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="75f50-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="75f50-127">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="75f50-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="75f50-128">Çalışma zamanı başlatma seçenekleri hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="75f50-128">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="75f50-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="75f50-129">Remarks</span></span>  
 <span data-ttu-id="75f50-130">Varsayılan olarak, <xref:System.StringComparer> sınıf <xref:System.String.GetHashCode%2A?displayProperty=nameWithType> ve yöntem, uygulama etki alanları arasında tutarlı bir karma kod üreten tek bir karma algoritmakullanır.</span><span class="sxs-lookup"><span data-stu-id="75f50-130">By default, the <xref:System.StringComparer> class and the <xref:System.String.GetHashCode%2A?displayProperty=nameWithType> method use a single hashing algorithm that produces a consistent hash code across application domains.</span></span> <span data-ttu-id="75f50-131">Bu, öğenin `enabled` özniteliğini `<UseRandomizedStringHashAlgorithm>` `0`.</span><span class="sxs-lookup"><span data-stu-id="75f50-131">This is equivalent to setting the `enabled` attribute of the `<UseRandomizedStringHashAlgorithm>` element to `0`.</span></span> <span data-ttu-id="75f50-132">Bu.NET Framework 4'te kullanılan karma algoritmadır.</span><span class="sxs-lookup"><span data-stu-id="75f50-132">This is the hashing algorithm used in the .NET Framework 4.</span></span>  
  
 <span data-ttu-id="75f50-133">Sınıf <xref:System.StringComparer> ve <xref:System.String.GetHashCode%2A?displayProperty=nameWithType> yöntem, uygulama etki alanı bazında karma kodları oluşturan farklı bir karma algoritmada da kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="75f50-133">The <xref:System.StringComparer> class and the <xref:System.String.GetHashCode%2A?displayProperty=nameWithType> method can also use a different hashing algorithm that computes hash codes on a per application domain basis.</span></span> <span data-ttu-id="75f50-134">Sonuç olarak, eşdeğer dizeleri için karma kodları uygulama etki alanları arasında farklılık gösterir.</span><span class="sxs-lookup"><span data-stu-id="75f50-134">As a result, hash codes for equivalent strings will differ across application domains.</span></span> <span data-ttu-id="75f50-135">Bu bir tercih özelliğidir; bundan yararlanmak için, öğenin `enabled` özniteliğini `<UseRandomizedStringHashAlgorithm>` . `1`</span><span class="sxs-lookup"><span data-stu-id="75f50-135">This is an opt-in feature; to take advantage of it, you must set the `enabled` attribute of the `<UseRandomizedStringHashAlgorithm>` element to `1`.</span></span>  
  
 <span data-ttu-id="75f50-136">Karma tablodaki dize araması genellikle bir O(1) işlemidir.</span><span class="sxs-lookup"><span data-stu-id="75f50-136">The string lookup in a hash table is typically an O(1) operation.</span></span> <span data-ttu-id="75f50-137">Ancak, çok sayıda çakışma meydana geldiğinde, arama bir O(n<sup>2)</sup>işlemi olabilir.</span><span class="sxs-lookup"><span data-stu-id="75f50-137">However, when a large number of collisions occur, the lookup can become an O(n<sup>2</sup>) operation.</span></span> <span data-ttu-id="75f50-138">Yapılandırma öğesini, `<UseRandomizedStringHashAlgorithm>` uygulama etki alanı başına rasgele bir karma algoritma oluşturmak için kullanabilirsiniz, bu da olası çakışma sayısını sınırlar, özellikle karma kodlarının hesaplandığı anahtarlar kullanıcılar tarafından veri girişine dayanıyorsa.</span><span class="sxs-lookup"><span data-stu-id="75f50-138">You can use the `<UseRandomizedStringHashAlgorithm>` configuration element to generate a random hashing algorithm per application domain, which in turn limits the number of potential collisions, particularly when the keys from which the hash codes are calculated are based on data input by users.</span></span>  
  
## <a name="example"></a><span data-ttu-id="75f50-139">Örnek</span><span class="sxs-lookup"><span data-stu-id="75f50-139">Example</span></span>  
 <span data-ttu-id="75f50-140">Aşağıdaki örnekte, `s` `DisplayString` değeri "Bu bir dizedir" olan özel bir dize sabiti içeren bir sınıf tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="75f50-140">The following example defines a `DisplayString` class that includes a private string constant, `s`, whose value is "This is a string."</span></span> <span data-ttu-id="75f50-141">Ayrıca, yöntemin yürütüldettiği uygulama etki alanının adı ile birlikte dize değerini ve karma kodunu görüntüleyen bir `ShowStringHashCode` yöntem de içerir.</span><span class="sxs-lookup"><span data-stu-id="75f50-141">It also includes a `ShowStringHashCode` method that displays the string value and its hash code along with the name of the application domain in which the method is executing.</span></span>  
  
 [!code-csharp[System.String.GetHashCode#2](../../../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.String.GetHashCode/CS/perdomain.cs#2)]
 [!code-vb[System.String.GetHashCode#2](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.String.GetHashCode/VB/perdomain.vb#2)]  
  
 <span data-ttu-id="75f50-142">Bir yapılandırma dosyası sağlamadan örneği çalıştırdığınızda, aşağıdakine benzer çıktı görüntüler.</span><span class="sxs-lookup"><span data-stu-id="75f50-142">When you run the example without supplying a configuration file, it displays output similar to the following.</span></span> <span data-ttu-id="75f50-143">Dize için karma kodları iki uygulama etki alanında aynı olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="75f50-143">Note that the hash codes for the string are identical in the two application domains.</span></span>  
  
```console
String 'This is a string.' in domain 'PerDomain.exe': 941BCEAC  
String 'This is a string.' in domain 'NewDomain': 941BCEAC  
```  
  
 <span data-ttu-id="75f50-144">Ancak, aşağıdaki yapılandırma dosyasını örnek dizine ekler ve örneği çalıştırırsanız, aynı dize için karma kodlar uygulama etki alanına göre farklılık gösterir.</span><span class="sxs-lookup"><span data-stu-id="75f50-144">However, if you add the following configuration file to the example's directory and then run the example, the hash codes for the same string will differ by application domain.</span></span>  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
   <runtime>  
      <UseRandomizedStringHashAlgorithm enabled="1" />  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="75f50-145">Yapılandırma dosyası bulunduğunda, örnek aşağıdaki çıktıyı görüntüler:</span><span class="sxs-lookup"><span data-stu-id="75f50-145">When the configuration file is present, the example displays the following output:</span></span>  
  
```console
String 'This is a string.' in domain 'PerDomain.exe': 5435776D  
String 'This is a string.' in domain 'NewDomain': 75CC8236  
```  
  
## <a name="see-also"></a><span data-ttu-id="75f50-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="75f50-146">See also</span></span>

- <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType>
- <xref:System.String.GetHashCode%2A?displayProperty=nameWithType>
- <xref:System.Object.GetHashCode%2A?displayProperty=nameWithType>
