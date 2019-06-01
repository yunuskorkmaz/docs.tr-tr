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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 91983a0910b272e621783f0fdb68242ddbd20f03
ms.sourcegitcommit: 518e7634b86d3980ec7da5f8c308cc1054daedb7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/01/2019
ms.locfileid: "66456176"
---
# <a name="userandomizedstringhashalgorithm-element"></a><span data-ttu-id="8bc96-102">\<UseRandomizedStringHashAlgorithm > öğesi</span><span class="sxs-lookup"><span data-stu-id="8bc96-102">\<UseRandomizedStringHashAlgorithm> Element</span></span>
<span data-ttu-id="8bc96-103">Ortak dil çalışma zamanı için dizelerin karma kodlarını hesaplayıp belirleyen bir her uygulama etki alanı.</span><span class="sxs-lookup"><span data-stu-id="8bc96-103">Determines whether the common language runtime calculates hash codes for strings on a per application domain basis.</span></span>  
  
 <span data-ttu-id="8bc96-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="8bc96-104">\<configuration></span></span>  
<span data-ttu-id="8bc96-105">\<çalışma zamanı ></span><span class="sxs-lookup"><span data-stu-id="8bc96-105">\<runtime></span></span>  
<span data-ttu-id="8bc96-106">\<UseRandomizedStringHashAlgorithm ></span><span class="sxs-lookup"><span data-stu-id="8bc96-106">\<UseRandomizedStringHashAlgorithm></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8bc96-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8bc96-107">Syntax</span></span>  
  
```xml  
<UseRandomizedStringHashAlgorithm   
   enabled=0|1 />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8bc96-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="8bc96-108">Attributes and Elements</span></span>  
 <span data-ttu-id="8bc96-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8bc96-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8bc96-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="8bc96-110">Attributes</span></span>  
  
|<span data-ttu-id="8bc96-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="8bc96-111">Attribute</span></span>|<span data-ttu-id="8bc96-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8bc96-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="8bc96-113">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="8bc96-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="8bc96-114">Dizeler için karma kodları hesaplanıp hesaplanmadığını belirtir bir her uygulama etki alanı.</span><span class="sxs-lookup"><span data-stu-id="8bc96-114">Specifies whether hash codes for strings are calculated on a per application domain basis.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="8bc96-115">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="8bc96-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="8bc96-116">Değer</span><span class="sxs-lookup"><span data-stu-id="8bc96-116">Value</span></span>|<span data-ttu-id="8bc96-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8bc96-117">Description</span></span>|  
|-----------|-----------------|  
|`0`|<span data-ttu-id="8bc96-118">Ortak dil çalışma zamanı dizeler için karma kodları hesaplama olmayan bir uygulama etki alanı temelinde; tek bir algoritma dize karma kodlarını hesaplamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8bc96-118">The common language runtime does not compute hash codes for strings on a per application domain basis; a single algorithm is used to calculate string hash codes.</span></span> <span data-ttu-id="8bc96-119">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="8bc96-119">This is the default.</span></span>|  
|`1`|<span data-ttu-id="8bc96-120">Ortak dil çalışma zamanı dizeler için karma kodlar hesaplayan bir her uygulama etki alanı.</span><span class="sxs-lookup"><span data-stu-id="8bc96-120">The common language runtime computes hash codes for strings on a per application domain basis.</span></span> <span data-ttu-id="8bc96-121">Farklı uygulama etki alanlarındaki ve farklı işlemlerdeki aynı dizeler, farklı karma kodlarına sahip olacaktır.</span><span class="sxs-lookup"><span data-stu-id="8bc96-121">Identical strings in different application domains and in different processes will have different hash codes.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8bc96-122">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="8bc96-122">Child Elements</span></span>  
 <span data-ttu-id="8bc96-123">Yok.</span><span class="sxs-lookup"><span data-stu-id="8bc96-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8bc96-124">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="8bc96-124">Parent Elements</span></span>  
  
|<span data-ttu-id="8bc96-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="8bc96-125">Element</span></span>|<span data-ttu-id="8bc96-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8bc96-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="8bc96-127">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="8bc96-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="8bc96-128">Çalışma zamanı başlatma seçenekleri hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="8bc96-128">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8bc96-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8bc96-129">Remarks</span></span>  
 <span data-ttu-id="8bc96-130">Varsayılan olarak, <xref:System.StringComparer> sınıfı ve <xref:System.String.GetHashCode%2A?displayProperty=nameWithType> yöntemi, uygulama etki alanları arasında tutarlı bir karma kod üreten tek bir karma algoritma kullanın.</span><span class="sxs-lookup"><span data-stu-id="8bc96-130">By default, the <xref:System.StringComparer> class and the <xref:System.String.GetHashCode%2A?displayProperty=nameWithType> method use a single hashing algorithm that produces a consistent hash code across application domains.</span></span> <span data-ttu-id="8bc96-131">Bu ayarlamakla eşdeğerdir `enabled` özniteliği `<UseRandomizedStringHashAlgorithm>` öğesine `0`.</span><span class="sxs-lookup"><span data-stu-id="8bc96-131">This is equivalent to setting the `enabled` attribute of the `<UseRandomizedStringHashAlgorithm>` element to `0`.</span></span> <span data-ttu-id="8bc96-132">.NET Framework 4'te kullanılan karma algoritması budur.</span><span class="sxs-lookup"><span data-stu-id="8bc96-132">This is the hashing algorithm used in the .NET Framework 4.</span></span>  
  
 <span data-ttu-id="8bc96-133"><xref:System.StringComparer> Sınıfı ve <xref:System.String.GetHashCode%2A?displayProperty=nameWithType> yöntemi ayrıca karma kodlar hesaplayan farklı bir karma algoritması kullanan bir her uygulama etki alanı.</span><span class="sxs-lookup"><span data-stu-id="8bc96-133">The <xref:System.StringComparer> class and the <xref:System.String.GetHashCode%2A?displayProperty=nameWithType> method can also use a different hashing algorithm that computes hash codes on a per application domain basis.</span></span> <span data-ttu-id="8bc96-134">Sonuç olarak, eşdeğer dizeler için karma kodlarını uygulama etki alanları arasında farklılık gösterir.</span><span class="sxs-lookup"><span data-stu-id="8bc96-134">As a result, hash codes for equivalent strings will differ across application domains.</span></span> <span data-ttu-id="8bc96-135">Bu bir katılım özelliğidir; yararlanmak için ayarlamalısınız `enabled` özniteliği `<UseRandomizedStringHashAlgorithm>` öğesine `1`.</span><span class="sxs-lookup"><span data-stu-id="8bc96-135">This is an opt-in feature; to take advantage of it, you must set the `enabled` attribute of the `<UseRandomizedStringHashAlgorithm>` element to `1`.</span></span>  
  
 <span data-ttu-id="8bc96-136">Karma tabloda dize arama genellikle bir o(1) işlemidir.</span><span class="sxs-lookup"><span data-stu-id="8bc96-136">The string lookup in a hash table is typically an O(1) operation.</span></span> <span data-ttu-id="8bc96-137">Ancak, çok sayıda çakışma oluştuğunda arama bir O olabilir (n<sup>2</sup>) işlemi.</span><span class="sxs-lookup"><span data-stu-id="8bc96-137">However, when a large number of collisions occur, the lookup can become an O(n<sup>2</sup>) operation.</span></span> <span data-ttu-id="8bc96-138">Kullanabileceğiniz `<UseRandomizedStringHashAlgorithm>` yapılandırma öğesi, karma kodlarının hesaplandığı anahtarlar girilen verilere dayalı özellikle hangi sırayla olası çakışmaların sayısını sınırlayan, uygulama etki alanı başına rasgele bir karma algoritma oluşturmak için kullanıcılar tarafından.</span><span class="sxs-lookup"><span data-stu-id="8bc96-138">You can use the `<UseRandomizedStringHashAlgorithm>` configuration element to generate a random hashing algorithm per application domain, which in turn limits the number of potential collisions, particularly when the keys from which the hash codes are calculated are based on data input by users.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8bc96-139">Örnek</span><span class="sxs-lookup"><span data-stu-id="8bc96-139">Example</span></span>  
 <span data-ttu-id="8bc96-140">Aşağıdaki örnekte tanımlayan bir `DisplayString` bir özel dize sabiti içeren sınıf `s`, değeri olan "Dize budur."</span><span class="sxs-lookup"><span data-stu-id="8bc96-140">The following example defines a `DisplayString` class that includes a private string constant, `s`, whose value is "This is a string."</span></span> <span data-ttu-id="8bc96-141">Ayrıca bir `ShowStringHashCode` dize değeri ve Yöntem yürütme, uygulama etki alanı adı karma kodunu görüntüler yöntemi.</span><span class="sxs-lookup"><span data-stu-id="8bc96-141">It also includes a `ShowStringHashCode` method that displays the string value and its hash code along with the name of the application domain in which the method is executing.</span></span>  
  
 [!code-csharp[System.String.GetHashCode#2](../../../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.String.GetHashCode/CS/perdomain.cs#2)]
 [!code-vb[System.String.GetHashCode#2](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.String.GetHashCode/VB/perdomain.vb#2)]  
  
 <span data-ttu-id="8bc96-142">Örnek bir yapılandırma dosyası sağlamadan çalıştırdığınızda, aşağıdakine benzer bir çıktı görüntüler.</span><span class="sxs-lookup"><span data-stu-id="8bc96-142">When you run the example without supplying a configuration file, it displays output similar to the following.</span></span> <span data-ttu-id="8bc96-143">Dize için karma kodları iki uygulama etki alanında aynı olduğuna dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="8bc96-143">Note that the hash codes for the string are identical in the two application domains.</span></span>  
  
```  
String 'This is a string.' in domain 'PerDomain.exe': 941BCEAC  
String 'This is a string.' in domain 'NewDomain': 941BCEAC  
```  
  
 <span data-ttu-id="8bc96-144">Ancak örneğin dizinine şu yapılandırma dosyasını ekleyin ve sonra örneği çalıştırırsanız, aynı dize için karma kodlarını uygulama etki alanına göre farklılık gösterir.</span><span class="sxs-lookup"><span data-stu-id="8bc96-144">However, if you add the following configuration file to the example's directory and then run the example, the hash codes for the same string will differ by application domain.</span></span>  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
   <runtime>  
      <UseRandomizedStringHashAlgorithm enabled="1" />  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="8bc96-145">Yapılandırma dosyası varolduğunda, örnek aşağıdaki çıkışı görüntüler:</span><span class="sxs-lookup"><span data-stu-id="8bc96-145">When the configuration file is present, the example displays the following output:</span></span>  
  
```  
String 'This is a string.' in domain 'PerDomain.exe': 5435776D  
String 'This is a string.' in domain 'NewDomain': 75CC8236  
```  
  
## <a name="see-also"></a><span data-ttu-id="8bc96-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8bc96-146">See also</span></span>

- <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType>
- <xref:System.String.GetHashCode%2A?displayProperty=nameWithType>
- <xref:System.Object.GetHashCode%2A?displayProperty=nameWithType>
