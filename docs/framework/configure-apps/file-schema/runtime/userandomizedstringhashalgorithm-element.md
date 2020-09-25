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
ms.openlocfilehash: 148d55c8b8a63737867c4bfdf3ab118dfdefd6f9
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91174101"
---
# <a name="userandomizedstringhashalgorithm-element"></a><span data-ttu-id="8f0f9-102">\<UseRandomizedStringHashAlgorithm> Öğesi</span><span class="sxs-lookup"><span data-stu-id="8f0f9-102">\<UseRandomizedStringHashAlgorithm> Element</span></span>

<span data-ttu-id="8f0f9-103">Ortak dil çalışma zamanının, her uygulama etki alanı temelinde dizeler için karma kodları hesaplayıp hesaplamadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="8f0f9-103">Determines whether the common language runtime calculates hash codes for strings on a per application domain basis.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<UseRandomizedStringHashAlgorithm>**  
  
## <a name="syntax"></a><span data-ttu-id="8f0f9-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="8f0f9-104">Syntax</span></span>  
  
```xml  
<UseRandomizedStringHashAlgorithm
   enabled=0|1 />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8f0f9-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="8f0f9-105">Attributes and Elements</span></span>  

 <span data-ttu-id="8f0f9-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8f0f9-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8f0f9-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="8f0f9-107">Attributes</span></span>  
  
|<span data-ttu-id="8f0f9-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="8f0f9-108">Attribute</span></span>|<span data-ttu-id="8f0f9-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8f0f9-109">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="8f0f9-110">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="8f0f9-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="8f0f9-111">Dizelerin karma kodlarının her uygulama etki alanı temelinde hesaplanıp hesaplanmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="8f0f9-111">Specifies whether hash codes for strings are calculated on a per application domain basis.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="8f0f9-112">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="8f0f9-112">enabled Attribute</span></span>  
  
|<span data-ttu-id="8f0f9-113">Değer</span><span class="sxs-lookup"><span data-stu-id="8f0f9-113">Value</span></span>|<span data-ttu-id="8f0f9-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8f0f9-114">Description</span></span>|  
|-----------|-----------------|  
|`0`|<span data-ttu-id="8f0f9-115">Ortak dil çalışma zamanı, her uygulama etki alanı temelinde dizeler için karma kodları hesaplamaz; dize karma kodlarını hesaplamak için tek bir algoritma kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8f0f9-115">The common language runtime does not compute hash codes for strings on a per application domain basis; a single algorithm is used to calculate string hash codes.</span></span> <span data-ttu-id="8f0f9-116">Bu varsayılan seçenektir.</span><span class="sxs-lookup"><span data-stu-id="8f0f9-116">This is the default.</span></span>|  
|`1`|<span data-ttu-id="8f0f9-117">Ortak dil çalışma zamanı, her uygulama etki alanı temelinde dizeler için karma kodları hesaplar.</span><span class="sxs-lookup"><span data-stu-id="8f0f9-117">The common language runtime computes hash codes for strings on a per application domain basis.</span></span> <span data-ttu-id="8f0f9-118">Farklı uygulama etki alanlarındaki ve farklı işlemlerdeki özdeş dizeler farklı karma kodlara sahip olur.</span><span class="sxs-lookup"><span data-stu-id="8f0f9-118">Identical strings in different application domains and in different processes will have different hash codes.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8f0f9-119">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="8f0f9-119">Child Elements</span></span>  

 <span data-ttu-id="8f0f9-120">Yok.</span><span class="sxs-lookup"><span data-stu-id="8f0f9-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8f0f9-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="8f0f9-121">Parent Elements</span></span>  
  
|<span data-ttu-id="8f0f9-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="8f0f9-122">Element</span></span>|<span data-ttu-id="8f0f9-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8f0f9-123">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="8f0f9-124">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="8f0f9-124">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="8f0f9-125">Çalışma zamanı başlatma seçenekleri hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="8f0f9-125">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8f0f9-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8f0f9-126">Remarks</span></span>  

 <span data-ttu-id="8f0f9-127">Varsayılan olarak, <xref:System.StringComparer> sınıfı ve yöntemi, <xref:System.String.GetHashCode%2A?displayProperty=nameWithType> uygulama etki alanları arasında tutarlı bir karma kod üreten tek bir karma algoritması kullanır.</span><span class="sxs-lookup"><span data-stu-id="8f0f9-127">By default, the <xref:System.StringComparer> class and the <xref:System.String.GetHashCode%2A?displayProperty=nameWithType> method use a single hashing algorithm that produces a consistent hash code across application domains.</span></span> <span data-ttu-id="8f0f9-128">Bu, `enabled` öğesinin özniteliğini olarak ayarlamaya eşdeğerdir `<UseRandomizedStringHashAlgorithm>` `0` .</span><span class="sxs-lookup"><span data-stu-id="8f0f9-128">This is equivalent to setting the `enabled` attribute of the `<UseRandomizedStringHashAlgorithm>` element to `0`.</span></span> <span data-ttu-id="8f0f9-129">Bu, .NET Framework 4 ' te kullanılan karma algoritmadır.</span><span class="sxs-lookup"><span data-stu-id="8f0f9-129">This is the hashing algorithm used in the .NET Framework 4.</span></span>  
  
 <span data-ttu-id="8f0f9-130"><xref:System.StringComparer>Sınıfı ve yöntemi, <xref:System.String.GetHashCode%2A?displayProperty=nameWithType> her uygulama etki alanı temelinde karma kodları hesaplayan farklı bir karma algoritması da kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="8f0f9-130">The <xref:System.StringComparer> class and the <xref:System.String.GetHashCode%2A?displayProperty=nameWithType> method can also use a different hashing algorithm that computes hash codes on a per application domain basis.</span></span> <span data-ttu-id="8f0f9-131">Sonuç olarak, eşdeğer dizeler için karma kodları uygulama etki alanları arasında farklılık gösterir.</span><span class="sxs-lookup"><span data-stu-id="8f0f9-131">As a result, hash codes for equivalent strings will differ across application domains.</span></span> <span data-ttu-id="8f0f9-132">Bu bir kabul etme özelliğidir; Bundan faydalanmak için, `enabled` öğesinin özniteliğini olarak ayarlamanız gerekir `<UseRandomizedStringHashAlgorithm>` `1` .</span><span class="sxs-lookup"><span data-stu-id="8f0f9-132">This is an opt-in feature; to take advantage of it, you must set the `enabled` attribute of the `<UseRandomizedStringHashAlgorithm>` element to `1`.</span></span>  
  
 <span data-ttu-id="8f0f9-133">Karma tablodaki dize araması genellikle bir O (1) işlemidir.</span><span class="sxs-lookup"><span data-stu-id="8f0f9-133">The string lookup in a hash table is typically an O(1) operation.</span></span> <span data-ttu-id="8f0f9-134">Ancak, çok sayıda çakışma oluştuğunda, arama bir O (n<sup>2</sup>) işlemi olabilir.</span><span class="sxs-lookup"><span data-stu-id="8f0f9-134">However, when a large number of collisions occur, the lookup can become an O(n<sup>2</sup>) operation.</span></span> <span data-ttu-id="8f0f9-135">`<UseRandomizedStringHashAlgorithm>`Yapılandırma öğesini, uygulama etki alanı başına rastgele bir karma algoritması oluşturmak için kullanabilirsiniz. Bu, özellikle de karma kodlarının hesaplandığı anahtarlar kullanıcılara göre veri girişini temel alırken olası çakışmaların sayısını sınırlar.</span><span class="sxs-lookup"><span data-stu-id="8f0f9-135">You can use the `<UseRandomizedStringHashAlgorithm>` configuration element to generate a random hashing algorithm per application domain, which in turn limits the number of potential collisions, particularly when the keys from which the hash codes are calculated are based on data input by users.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8f0f9-136">Örnek</span><span class="sxs-lookup"><span data-stu-id="8f0f9-136">Example</span></span>  

 <span data-ttu-id="8f0f9-137">Aşağıdaki örnek, `DisplayString` `s` değeri "This bir dizedir" olan özel bir dize sabiti içeren bir sınıfı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="8f0f9-137">The following example defines a `DisplayString` class that includes a private string constant, `s`, whose value is "This is a string."</span></span> <span data-ttu-id="8f0f9-138">Ayrıca, `ShowStringHashCode` yöntemin yürütüldüğü uygulama etki alanının adı ile birlikte dize değerini ve karma kodunu görüntüleyen bir yöntemi içerir.</span><span class="sxs-lookup"><span data-stu-id="8f0f9-138">It also includes a `ShowStringHashCode` method that displays the string value and its hash code along with the name of the application domain in which the method is executing.</span></span>  
  
 [!code-csharp[System.String.GetHashCode#2](../../../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.String.GetHashCode/CS/perdomain.cs#2)]
 [!code-vb[System.String.GetHashCode#2](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.String.GetHashCode/VB/perdomain.vb#2)]  
  
 <span data-ttu-id="8f0f9-139">Bir yapılandırma dosyası vermeden örneği çalıştırdığınızda aşağıdakine benzer bir çıktı görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="8f0f9-139">When you run the example without supplying a configuration file, it displays output similar to the following.</span></span> <span data-ttu-id="8f0f9-140">Dizenin karma kodlarının iki uygulama etki alanında aynı olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="8f0f9-140">Note that the hash codes for the string are identical in the two application domains.</span></span>  
  
```console
String 'This is a string.' in domain 'PerDomain.exe': 941BCEAC  
String 'This is a string.' in domain 'NewDomain': 941BCEAC  
```  
  
 <span data-ttu-id="8f0f9-141">Ancak, aşağıdaki yapılandırma dosyasını örnek dizinine ekler ve sonra örneği çalıştırırsanız, aynı dizenin karma kodları uygulama etki alanına göre farklılık gösterir.</span><span class="sxs-lookup"><span data-stu-id="8f0f9-141">However, if you add the following configuration file to the example's directory and then run the example, the hash codes for the same string will differ by application domain.</span></span>  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
   <runtime>  
      <UseRandomizedStringHashAlgorithm enabled="1" />  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="8f0f9-142">Yapılandırma dosyası mevcut olduğunda, örnek aşağıdaki çıktıyı görüntüler:</span><span class="sxs-lookup"><span data-stu-id="8f0f9-142">When the configuration file is present, the example displays the following output:</span></span>  
  
```console
String 'This is a string.' in domain 'PerDomain.exe': 5435776D  
String 'This is a string.' in domain 'NewDomain': 75CC8236  
```  
  
## <a name="see-also"></a><span data-ttu-id="8f0f9-143">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8f0f9-143">See also</span></span>

- <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType>
- <xref:System.String.GetHashCode%2A?displayProperty=nameWithType>
- <xref:System.Object.GetHashCode%2A?displayProperty=nameWithType>
