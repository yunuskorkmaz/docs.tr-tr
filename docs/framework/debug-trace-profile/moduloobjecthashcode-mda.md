---
title: moduloObjectHashcode MDA
ms.date: 03/30/2017
helpviewer_keywords:
- managed debugging assistants (MDAs), hashcode modulus
- Modulo object hash code
- moduloObjectHashcode MDA
- hashcode modulus
- MDAs (managed debugging assistants), hashcode modulus
- GetHashCode method
- modulus of hashcodes
ms.assetid: b45366ff-2a7a-4b8e-ab01-537b72e9de68
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6d8f6975d117d9920d2199c3996246822d1fdb6c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59170787"
---
# <a name="moduloobjecthashcode-mda"></a><span data-ttu-id="e8442-102">moduloObjectHashcode MDA</span><span class="sxs-lookup"><span data-stu-id="e8442-102">moduloObjectHashcode MDA</span></span>
<span data-ttu-id="e8442-103">`moduloObjectHashcode` Yönetilen hata ayıklama Yardımcısı (MDA) davranışını değiştirir <xref:System.Object> sınıf gerçekleştirmek için bir işlem tarafından döndürülen ilişkin karma kodu modül <xref:System.Object.GetHashCode%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="e8442-103">The `moduloObjectHashcode` managed debugging assistant (MDA) changes the behavior of the <xref:System.Object> class to perform a modulo operation on the hash code returned by the <xref:System.Object.GetHashCode%2A> method.</span></span> <span data-ttu-id="e8442-104">Bu MDA için'varsayılan mod neden olan 1 ' dir <xref:System.Object.GetHashCode%2A> 0 tüm nesneleri için döndürülecek.</span><span class="sxs-lookup"><span data-stu-id="e8442-104">The default modulus for this MDA is 1, which causes <xref:System.Object.GetHashCode%2A> to return 0 for all objects.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="e8442-105">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="e8442-105">Symptoms</span></span>  
 <span data-ttu-id="e8442-106">Ortak dil çalışma zamanı (CLR) yeni bir sürüme taşıdıktan sonra bir program artık düzgün şekilde çalışır:</span><span class="sxs-lookup"><span data-stu-id="e8442-106">After moving to a new version of the common language runtime (CLR), a program no longer executes properly:</span></span>  
  
-   <span data-ttu-id="e8442-107">Program, yanlış nesneden alınırken bir <xref:System.Collections.Hashtable>.</span><span class="sxs-lookup"><span data-stu-id="e8442-107">The program is getting the wrong object from a <xref:System.Collections.Hashtable>.</span></span>  
  
-   <span data-ttu-id="e8442-108">Sabit listesinden alınmış sırasını bir <xref:System.Collections.Hashtable> programın sonu değişmedi.</span><span class="sxs-lookup"><span data-stu-id="e8442-108">The order of enumeration from a <xref:System.Collections.Hashtable> has a change that breaks the program.</span></span>  
  
-   <span data-ttu-id="e8442-109">Artık eşit olacak şekilde kullanılan iki nesne eşit değildir.</span><span class="sxs-lookup"><span data-stu-id="e8442-109">Two objects that used to be equal are no longer equal.</span></span>  
  
-   <span data-ttu-id="e8442-110">Eşit olmaması için kullanılan iki nesne eşit olur.</span><span class="sxs-lookup"><span data-stu-id="e8442-110">Two objects that used to not be equal are now equal.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="e8442-111">Sebep</span><span class="sxs-lookup"><span data-stu-id="e8442-111">Cause</span></span>  
 <span data-ttu-id="e8442-112">Programınızı yanlış nesneden alma bir <xref:System.Collections.Hashtable> çünkü yürütmesinin <xref:System.Object.Equals%2A> anahtarını sınıfındaki yöntemi <xref:System.Collections.Hashtable> çağrı sonuçlarını karşılaştırarak nesnelerin eşitliği testleri <xref:System.Object.GetHashCode%2A> yöntemi .</span><span class="sxs-lookup"><span data-stu-id="e8442-112">Your program may be getting the wrong object from a <xref:System.Collections.Hashtable> because the implementation of the <xref:System.Object.Equals%2A> method on the class for the key into the <xref:System.Collections.Hashtable> tests for equality of objects by comparing the results of the call to the <xref:System.Object.GetHashCode%2A> method.</span></span> <span data-ttu-id="e8442-113">Karma kodları, kendi ilgili alanlarını farklı değerlere sahip olsa bile iki nesnenin aynı karma koda sahip olabileceği için nesne eşitliği test etmek için kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="e8442-113">Hash codes should not be used to test for object equality because two objects may have the same hash code even if their respective fields have different values.</span></span> <span data-ttu-id="e8442-114">Bu karma kod çakışmaları ender olsa, uygulamada oluşur.</span><span class="sxs-lookup"><span data-stu-id="e8442-114">These hash code collisions, although rare in practice, do occur.</span></span> <span data-ttu-id="e8442-115">Bu sahip olduğu etkiyi bir <xref:System.Collections.Hashtable> arama, eşit olacak şekilde eşit olmayan iki anahtar görünür ve yanlış nesne öğesinden döndürülen <xref:System.Collections.Hashtable>.</span><span class="sxs-lookup"><span data-stu-id="e8442-115">The effect this has on a <xref:System.Collections.Hashtable> lookup is that two keys which are not equal appear to be equal, and the wrong object is returned from the <xref:System.Collections.Hashtable>.</span></span> <span data-ttu-id="e8442-116">Performans nedenleriyle yürütmesinin <xref:System.Object.GetHashCode%2A> sonraki sürümlerinde bir sürümünde gerçekleşmeyebilir çakışmaları oluşabilir için çalışma zamanı sürümleri arasında geçiş.</span><span class="sxs-lookup"><span data-stu-id="e8442-116">For performance reasons, the implementation of <xref:System.Object.GetHashCode%2A> can change between runtime versions, so collisions that might not occur on one version might occur on subsequent versions.</span></span> <span data-ttu-id="e8442-117">Bu mda'nın karma kodları birbiriyle çakışır olduğunda, kod hataları olup olmadığını test etmek etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="e8442-117">Enable this MDA to test whether your code has bugs when hash codes collide.</span></span> <span data-ttu-id="e8442-118">Etkin olduğunda, bu mda'nın neden <xref:System.Object.GetHashCode%2A> 0, döndürülecek yöntemi çakışmadan tüm karma kodları kaynaklanan.</span><span class="sxs-lookup"><span data-stu-id="e8442-118">When enabled, this MDA causes the <xref:System.Object.GetHashCode%2A> method to return 0, resulting in all hash codes colliding.</span></span> <span data-ttu-id="e8442-119">Yalnızca etkin bu MDA, programınızın olmalıdır, programınızı daha yavaş çalıştırır etkinleştirmektir.</span><span class="sxs-lookup"><span data-stu-id="e8442-119">The only effect enabling this MDA should have on your program is that your program runs slower.</span></span>  
  
 <span data-ttu-id="e8442-120">Sabit listesinden alınmış sırasını bir <xref:System.Collections.Hashtable> bir çalışma zamanı sürümünden anahtar değişikliği için karma kodları hesaplamak için kullanılan algoritma için başka bir IF değişebilir.</span><span class="sxs-lookup"><span data-stu-id="e8442-120">The order of enumeration from a <xref:System.Collections.Hashtable> may change from one version of the runtime to another if the algorithm used to compute the hash codes for the key change.</span></span> <span data-ttu-id="e8442-121">Programınız bir bağımlılık anahtarlar veya değerler dışında bir karma tablo numaralandırmasını bazında sürdü olup olmadığını test etmek için bu mda'nın etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e8442-121">To test whether your program has taken a dependency on the order of enumeration of keys or values out of a hash table, you can enable this MDA.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="e8442-122">Çözüm</span><span class="sxs-lookup"><span data-stu-id="e8442-122">Resolution</span></span>  
 <span data-ttu-id="e8442-123">Nesne kimliği için bir alternatif olarak, hiçbir zaman karma kodları kullanın.</span><span class="sxs-lookup"><span data-stu-id="e8442-123">Never use hash codes as a substitute for object identity.</span></span> <span data-ttu-id="e8442-124">Geçersiz kılmasını uygulamak <xref:System.Object.Equals%2A?displayProperty=nameWithType> karma kodları değil karşılaştırmak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="e8442-124">Implement the override of the <xref:System.Object.Equals%2A?displayProperty=nameWithType> method to not compare hash codes.</span></span>  
  
 <span data-ttu-id="e8442-125">Anahtarlar veya değerler numaralandırmalar bazında bağımlılıkları karma tabloları oluşturmayın.</span><span class="sxs-lookup"><span data-stu-id="e8442-125">Do not create dependencies on the order of enumerations of keys or values in hash tables.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="e8442-126">Çalışma zamanı üzerindeki etkisi</span><span class="sxs-lookup"><span data-stu-id="e8442-126">Effect on the Runtime</span></span>  
 <span data-ttu-id="e8442-127">Bu MDA etkinleştirildiğinde uygulamaları daha yavaş çalışır.</span><span class="sxs-lookup"><span data-stu-id="e8442-127">Applications run more slowly when this MDA is enabled.</span></span> <span data-ttu-id="e8442-128">Bu MDA, yalnızca döndürülen ilişkin karma kodu alır ve bunun yerine bir modül tarafından bölündüğünde kalanı döndürür.</span><span class="sxs-lookup"><span data-stu-id="e8442-128">This MDA simply takes the hash code that would have been returned and instead returns the remainder when divided by a modulus.</span></span>  
  
## <a name="output"></a><span data-ttu-id="e8442-129">Çıkış</span><span class="sxs-lookup"><span data-stu-id="e8442-129">Output</span></span>  
 <span data-ttu-id="e8442-130">Bu MDA için'hiçbir çıktı yok.</span><span class="sxs-lookup"><span data-stu-id="e8442-130">There is no output for this MDA.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="e8442-131">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="e8442-131">Configuration</span></span>  
 <span data-ttu-id="e8442-132">`modulus` İlişkin karma kod üzerinde kullanılan mod özniteliği belirtir.</span><span class="sxs-lookup"><span data-stu-id="e8442-132">The `modulus` attribute specifies the modulus used on the hash code.</span></span> <span data-ttu-id="e8442-133">Varsayılan değer 1’dir.</span><span class="sxs-lookup"><span data-stu-id="e8442-133">The default value is 1.</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <moduloObjectHashcode modulus="1" />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e8442-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e8442-134">See also</span></span>

- <xref:System.Object.GetHashCode%2A?displayProperty=nameWithType>
- <xref:System.Object.Equals%2A?displayProperty=nameWithType>
- [<span data-ttu-id="e8442-135">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="e8442-135">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
