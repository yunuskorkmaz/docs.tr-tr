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
ms.openlocfilehash: cc9708b8cca6520932fbf0e1975a05cad5fad485
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73115037"
---
# <a name="userandomizedstringhashalgorithm-element"></a><span data-ttu-id="c9fb6-102">\<UseRandomizedStringHashAlgorithm > öğesi</span><span class="sxs-lookup"><span data-stu-id="c9fb6-102">\<UseRandomizedStringHashAlgorithm> Element</span></span>
<span data-ttu-id="c9fb6-103">Ortak dil çalışma zamanının, her uygulama etki alanı temelinde dizeler için karma kodları hesaplayıp hesaplamadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="c9fb6-103">Determines whether the common language runtime calculates hash codes for strings on a per application domain basis.</span></span>  
  
<span data-ttu-id="c9fb6-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="c9fb6-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="c9fb6-105">&nbsp; &nbsp;[ **\<runtime >** ](runtime-element.md) </span><span class="sxs-lookup"><span data-stu-id="c9fb6-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="c9fb6-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<UseRandomizedStringHashAlgorithm >**</span><span class="sxs-lookup"><span data-stu-id="c9fb6-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<UseRandomizedStringHashAlgorithm>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9fb6-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c9fb6-107">Syntax</span></span>  
  
```xml  
<UseRandomizedStringHashAlgorithm   
   enabled=0|1 />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c9fb6-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="c9fb6-108">Attributes and Elements</span></span>  
 <span data-ttu-id="c9fb6-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c9fb6-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c9fb6-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c9fb6-110">Attributes</span></span>  
  
|<span data-ttu-id="c9fb6-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="c9fb6-111">Attribute</span></span>|<span data-ttu-id="c9fb6-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c9fb6-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="c9fb6-113">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="c9fb6-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="c9fb6-114">Dizelerin karma kodlarının her uygulama etki alanı temelinde hesaplanıp hesaplanmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="c9fb6-114">Specifies whether hash codes for strings are calculated on a per application domain basis.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="c9fb6-115">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="c9fb6-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="c9fb6-116">Değer</span><span class="sxs-lookup"><span data-stu-id="c9fb6-116">Value</span></span>|<span data-ttu-id="c9fb6-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c9fb6-117">Description</span></span>|  
|-----------|-----------------|  
|`0`|<span data-ttu-id="c9fb6-118">Ortak dil çalışma zamanı, her uygulama etki alanı temelinde dizeler için karma kodları hesaplamaz; dize karma kodlarını hesaplamak için tek bir algoritma kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c9fb6-118">The common language runtime does not compute hash codes for strings on a per application domain basis; a single algorithm is used to calculate string hash codes.</span></span> <span data-ttu-id="c9fb6-119">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="c9fb6-119">This is the default.</span></span>|  
|`1`|<span data-ttu-id="c9fb6-120">Ortak dil çalışma zamanı, her uygulama etki alanı temelinde dizeler için karma kodları hesaplar.</span><span class="sxs-lookup"><span data-stu-id="c9fb6-120">The common language runtime computes hash codes for strings on a per application domain basis.</span></span> <span data-ttu-id="c9fb6-121">Farklı uygulama etki alanlarındaki ve farklı işlemlerdeki özdeş dizeler farklı karma kodlara sahip olur.</span><span class="sxs-lookup"><span data-stu-id="c9fb6-121">Identical strings in different application domains and in different processes will have different hash codes.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c9fb6-122">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="c9fb6-122">Child Elements</span></span>  
 <span data-ttu-id="c9fb6-123">Yok.</span><span class="sxs-lookup"><span data-stu-id="c9fb6-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c9fb6-124">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="c9fb6-124">Parent Elements</span></span>  
  
|<span data-ttu-id="c9fb6-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="c9fb6-125">Element</span></span>|<span data-ttu-id="c9fb6-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c9fb6-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="c9fb6-127">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="c9fb6-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="c9fb6-128">Çalışma zamanı başlatma seçenekleri hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="c9fb6-128">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c9fb6-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c9fb6-129">Remarks</span></span>  
 <span data-ttu-id="c9fb6-130">Varsayılan olarak, <xref:System.StringComparer> sınıfı ve <xref:System.String.GetHashCode%2A?displayProperty=nameWithType> yöntemi, uygulama etki alanları arasında tutarlı bir karma kod üreten tek bir karma algoritması kullanır.</span><span class="sxs-lookup"><span data-stu-id="c9fb6-130">By default, the <xref:System.StringComparer> class and the <xref:System.String.GetHashCode%2A?displayProperty=nameWithType> method use a single hashing algorithm that produces a consistent hash code across application domains.</span></span> <span data-ttu-id="c9fb6-131">Bu, `<UseRandomizedStringHashAlgorithm>` öğesinin `enabled` özniteliğini `0`ayarlamaya eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="c9fb6-131">This is equivalent to setting the `enabled` attribute of the `<UseRandomizedStringHashAlgorithm>` element to `0`.</span></span> <span data-ttu-id="c9fb6-132">Bu, .NET Framework 4 ' te kullanılan karma algoritmadır.</span><span class="sxs-lookup"><span data-stu-id="c9fb6-132">This is the hashing algorithm used in the .NET Framework 4.</span></span>  
  
 <span data-ttu-id="c9fb6-133"><xref:System.StringComparer> sınıfı ve <xref:System.String.GetHashCode%2A?displayProperty=nameWithType> yöntemi, her uygulama etki alanı temelinde karma kodları hesaplayan farklı bir karma algoritması da kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="c9fb6-133">The <xref:System.StringComparer> class and the <xref:System.String.GetHashCode%2A?displayProperty=nameWithType> method can also use a different hashing algorithm that computes hash codes on a per application domain basis.</span></span> <span data-ttu-id="c9fb6-134">Sonuç olarak, eşdeğer dizeler için karma kodları uygulama etki alanları arasında farklılık gösterir.</span><span class="sxs-lookup"><span data-stu-id="c9fb6-134">As a result, hash codes for equivalent strings will differ across application domains.</span></span> <span data-ttu-id="c9fb6-135">Bu bir kabul etme özelliğidir; Bundan faydalanmak için `<UseRandomizedStringHashAlgorithm>` öğesinin `enabled` özniteliğini `1`olarak ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="c9fb6-135">This is an opt-in feature; to take advantage of it, you must set the `enabled` attribute of the `<UseRandomizedStringHashAlgorithm>` element to `1`.</span></span>  
  
 <span data-ttu-id="c9fb6-136">Karma tablodaki dize araması genellikle bir O (1) işlemidir.</span><span class="sxs-lookup"><span data-stu-id="c9fb6-136">The string lookup in a hash table is typically an O(1) operation.</span></span> <span data-ttu-id="c9fb6-137">Ancak, çok sayıda çakışma oluştuğunda, arama bir O (n<sup>2</sup>) işlemi olabilir.</span><span class="sxs-lookup"><span data-stu-id="c9fb6-137">However, when a large number of collisions occur, the lookup can become an O(n<sup>2</sup>) operation.</span></span> <span data-ttu-id="c9fb6-138">Uygulama etki alanı başına rastgele bir karma algoritması oluşturmak için `<UseRandomizedStringHashAlgorithm>` yapılandırma öğesini kullanabilirsiniz. Bu, özellikle de karma kodlarının hesaplandığı anahtarlar tarafından veri girişine bağlı olduğunda olası çakışmaların sayısını sınırlar. kullanıcılarına.</span><span class="sxs-lookup"><span data-stu-id="c9fb6-138">You can use the `<UseRandomizedStringHashAlgorithm>` configuration element to generate a random hashing algorithm per application domain, which in turn limits the number of potential collisions, particularly when the keys from which the hash codes are calculated are based on data input by users.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c9fb6-139">Örnek</span><span class="sxs-lookup"><span data-stu-id="c9fb6-139">Example</span></span>  
 <span data-ttu-id="c9fb6-140">Aşağıdaki örnek, değeri "This bir dizedir" olan `s`özel bir dize sabiti içeren bir `DisplayString` sınıfını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c9fb6-140">The following example defines a `DisplayString` class that includes a private string constant, `s`, whose value is "This is a string."</span></span> <span data-ttu-id="c9fb6-141">Ayrıca, yöntemin yürütüldüğü uygulama etki alanının adı ile birlikte dize değerini ve karma kodunu görüntüleyen bir `ShowStringHashCode` yöntemi içerir.</span><span class="sxs-lookup"><span data-stu-id="c9fb6-141">It also includes a `ShowStringHashCode` method that displays the string value and its hash code along with the name of the application domain in which the method is executing.</span></span>  
  
 [!code-csharp[System.String.GetHashCode#2](../../../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.String.GetHashCode/CS/perdomain.cs#2)]
 [!code-vb[System.String.GetHashCode#2](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.String.GetHashCode/VB/perdomain.vb#2)]  
  
 <span data-ttu-id="c9fb6-142">Bir yapılandırma dosyası vermeden örneği çalıştırdığınızda aşağıdakine benzer bir çıktı görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="c9fb6-142">When you run the example without supplying a configuration file, it displays output similar to the following.</span></span> <span data-ttu-id="c9fb6-143">Dizenin karma kodlarının iki uygulama etki alanında aynı olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="c9fb6-143">Note that the hash codes for the string are identical in the two application domains.</span></span>  
  
```  
String 'This is a string.' in domain 'PerDomain.exe': 941BCEAC  
String 'This is a string.' in domain 'NewDomain': 941BCEAC  
```  
  
 <span data-ttu-id="c9fb6-144">Ancak, aşağıdaki yapılandırma dosyasını örnek dizinine ekler ve sonra örneği çalıştırırsanız, aynı dizenin karma kodları uygulama etki alanına göre farklılık gösterir.</span><span class="sxs-lookup"><span data-stu-id="c9fb6-144">However, if you add the following configuration file to the example's directory and then run the example, the hash codes for the same string will differ by application domain.</span></span>  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
   <runtime>  
      <UseRandomizedStringHashAlgorithm enabled="1" />  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="c9fb6-145">Yapılandırma dosyası mevcut olduğunda, örnek aşağıdaki çıktıyı görüntüler:</span><span class="sxs-lookup"><span data-stu-id="c9fb6-145">When the configuration file is present, the example displays the following output:</span></span>  
  
```  
String 'This is a string.' in domain 'PerDomain.exe': 5435776D  
String 'This is a string.' in domain 'NewDomain': 75CC8236  
```  
  
## <a name="see-also"></a><span data-ttu-id="c9fb6-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c9fb6-146">See also</span></span>

- <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType>
- <xref:System.String.GetHashCode%2A?displayProperty=nameWithType>
- <xref:System.Object.GetHashCode%2A?displayProperty=nameWithType>
