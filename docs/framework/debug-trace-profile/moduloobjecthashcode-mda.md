---
title: moduloObjectHashcode MDA
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managed debugging assistants (MDAs), hashcode modulus
- Modulo object hash code
- moduloObjectHashcode MDA
- hashcode modulus
- MDAs (managed debugging assistants), hashcode modulus
- GetHashCode method
- modulus of hashcodes
ms.assetid: b45366ff-2a7a-4b8e-ab01-537b72e9de68
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 618196473e8e947e84b0506771bce84ee71a1c2d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="moduloobjecthashcode-mda"></a><span data-ttu-id="e68b0-102">moduloObjectHashcode MDA</span><span class="sxs-lookup"><span data-stu-id="e68b0-102">moduloObjectHashcode MDA</span></span>
<span data-ttu-id="e68b0-103">`moduloObjectHashcode` Yönetilen hata ayıklama Yardımcısı (MDA) davranışını değiştirir <xref:System.Object> sınıfı gerçekleştirmek için bir işlem tarafından döndürülen karma kodu modulo <xref:System.Object.GetHashCode%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="e68b0-103">The `moduloObjectHashcode` managed debugging assistant (MDA) changes the behavior of the <xref:System.Object> class to perform a modulo operation on the hash code returned by the <xref:System.Object.GetHashCode%2A> method.</span></span> <span data-ttu-id="e68b0-104">Bu MDA varsayılan mod neden olan 1 ' dir <xref:System.Object.GetHashCode%2A> tüm nesneleri için 0 dönün.</span><span class="sxs-lookup"><span data-stu-id="e68b0-104">The default modulus for this MDA is 1, which causes <xref:System.Object.GetHashCode%2A> to return 0 for all objects.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="e68b0-105">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="e68b0-105">Symptoms</span></span>  
 <span data-ttu-id="e68b0-106">Ortak dil çalışma zamanı (CLR) yeni bir sürüme taşıdıktan sonra bir program artık düzgün şekilde çalışır:</span><span class="sxs-lookup"><span data-stu-id="e68b0-106">After moving to a new version of the common language runtime (CLR), a program no longer executes properly:</span></span>  
  
-   <span data-ttu-id="e68b0-107">Program yanlış nesneden alınırken bir <xref:System.Collections.Hashtable>.</span><span class="sxs-lookup"><span data-stu-id="e68b0-107">The program is getting the wrong object from a <xref:System.Collections.Hashtable>.</span></span>  
  
-   <span data-ttu-id="e68b0-108">Numaralandırma içinden sırasını bir <xref:System.Collections.Hashtable> program keser bir değişiklik vardır.</span><span class="sxs-lookup"><span data-stu-id="e68b0-108">The order of enumeration from a <xref:System.Collections.Hashtable> has a change that breaks the program.</span></span>  
  
-   <span data-ttu-id="e68b0-109">Eşit olması için kullanılan iki nesne artık eşit değildir.</span><span class="sxs-lookup"><span data-stu-id="e68b0-109">Two objects that used to be equal are no longer equal.</span></span>  
  
-   <span data-ttu-id="e68b0-110">Eşit olmaması için kullanılan iki nesne eşit.</span><span class="sxs-lookup"><span data-stu-id="e68b0-110">Two objects that used to not be equal are now equal.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="e68b0-111">Sebep</span><span class="sxs-lookup"><span data-stu-id="e68b0-111">Cause</span></span>  
 <span data-ttu-id="e68b0-112">Programınızı yanlış nesnesinden alma bir <xref:System.Collections.Hashtable> çünkü uygulanması <xref:System.Object.Equals%2A> anahtara sınıfında yöntemi <xref:System.Collections.Hashtable> çağrısı sonuçlarını karşılaştırarak nesnelerin eşitlik için test <xref:System.Object.GetHashCode%2A> yöntemi .</span><span class="sxs-lookup"><span data-stu-id="e68b0-112">Your program may be getting the wrong object from a <xref:System.Collections.Hashtable> because the implementation of the <xref:System.Object.Equals%2A> method on the class for the key into the <xref:System.Collections.Hashtable> tests for equality of objects by comparing the results of the call to the <xref:System.Object.GetHashCode%2A> method.</span></span> <span data-ttu-id="e68b0-113">Karma kodlarını kendi ilgili alanlarını farklı değerlere sahip olsa bile iki nesnenin aynı karma koda sahip olabileceği için nesnenin eşitlik için test etmek için kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="e68b0-113">Hash codes should not be used to test for object equality because two objects may have the same hash code even if their respective fields have different values.</span></span> <span data-ttu-id="e68b0-114">Bu karma kodu çakışmaları ender olsa, uygulamada oluşur.</span><span class="sxs-lookup"><span data-stu-id="e68b0-114">These hash code collisions, although rare in practice, do occur.</span></span> <span data-ttu-id="e68b0-115">Bu açmıştır etkili bir <xref:System.Collections.Hashtable> arama, eşit olmayan iki anahtar görünüyor eşit ve yanlış nesne sunucudan döndürülen <xref:System.Collections.Hashtable>.</span><span class="sxs-lookup"><span data-stu-id="e68b0-115">The effect this has on a <xref:System.Collections.Hashtable> lookup is that two keys which are not equal appear to be equal, and the wrong object is returned from the <xref:System.Collections.Hashtable>.</span></span> <span data-ttu-id="e68b0-116">Performans nedenleriyle uygulanması <xref:System.Object.GetHashCode%2A> bir sürümünde gerçekleşmeyebilir çakışmaları oluşabilir ve sonraki sürümlerinde şekilde çalışma zamanı sürümleri arasında değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e68b0-116">For performance reasons, the implementation of <xref:System.Object.GetHashCode%2A> can change between runtime versions, so collisions that might not occur on one version might occur on subsequent versions.</span></span> <span data-ttu-id="e68b0-117">Karma kodlarını birbiriyle çakışır zaman kodunuzu hataları olup olmadığını sınamak bu MDA etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="e68b0-117">Enable this MDA to test whether your code has bugs when hash codes collide.</span></span> <span data-ttu-id="e68b0-118">Etkinleştirildiğinde, bu MDA neden olan <xref:System.Object.GetHashCode%2A> 0, döndürülecek yöntemi yazılımlarla çakışma tüm karma kodlarını sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="e68b0-118">When enabled, this MDA causes the <xref:System.Object.GetHashCode%2A> method to return 0, resulting in all hash codes colliding.</span></span> <span data-ttu-id="e68b0-119">Yalnızca etkin bu MDA programınızın olmalıdır programınız daha yavaş çalışır etkinleştirmektir.</span><span class="sxs-lookup"><span data-stu-id="e68b0-119">The only effect enabling this MDA should have on your program is that your program runs slower.</span></span>  
  
 <span data-ttu-id="e68b0-120">Numaralandırma içinden sırasını bir <xref:System.Collections.Hashtable> bir çalışma zamanı sürümünden anahtar değişikliği için karma kodları hesaplamak için kullanılan algoritma için başka bir if değişebilir.</span><span class="sxs-lookup"><span data-stu-id="e68b0-120">The order of enumeration from a <xref:System.Collections.Hashtable> may change from one version of the runtime to another if the algorithm used to compute the hash codes for the key change.</span></span> <span data-ttu-id="e68b0-121">Programınızı bir bağımlılık anahtarları ve değerleri bir karma tablosu dışında numaralandırması terabayt sürdü olup olmadığını sınamak için bu MDA etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e68b0-121">To test whether your program has taken a dependency on the order of enumeration of keys or values out of a hash table, you can enable this MDA.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="e68b0-122">Çözüm</span><span class="sxs-lookup"><span data-stu-id="e68b0-122">Resolution</span></span>  
 <span data-ttu-id="e68b0-123">Hiç karma kodlarını nesne kimliği için bir yedek olarak kullanın.</span><span class="sxs-lookup"><span data-stu-id="e68b0-123">Never use hash codes as a substitute for object identity.</span></span> <span data-ttu-id="e68b0-124">Geçersiz kılma uygulamak <xref:System.Object.Equals%2A?displayProperty=nameWithType> karma kodlarını değil Karşılaştırılacak yöntemi.</span><span class="sxs-lookup"><span data-stu-id="e68b0-124">Implement the override of the <xref:System.Object.Equals%2A?displayProperty=nameWithType> method to not compare hash codes.</span></span>  
  
 <span data-ttu-id="e68b0-125">Numaralandırmalar anahtarları ve değerleri terabayt bağımlılıkları karma tablolarda oluşturmayın.</span><span class="sxs-lookup"><span data-stu-id="e68b0-125">Do not create dependencies on the order of enumerations of keys or values in hash tables.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="e68b0-126">Çalışma zamanı etkisi</span><span class="sxs-lookup"><span data-stu-id="e68b0-126">Effect on the Runtime</span></span>  
 <span data-ttu-id="e68b0-127">Bu MDA etkinleştirildiğinde, uygulamaları daha yavaş çalışır.</span><span class="sxs-lookup"><span data-stu-id="e68b0-127">Applications run more slowly when this MDA is enabled.</span></span> <span data-ttu-id="e68b0-128">Bu MDA yalnızca döndürülen karma kodu alır ve bunun yerine bir modül tarafından bölünmüş zaman kalanı döndürür.</span><span class="sxs-lookup"><span data-stu-id="e68b0-128">This MDA simply takes the hash code that would have been returned and instead returns the remainder when divided by a modulus.</span></span>  
  
## <a name="output"></a><span data-ttu-id="e68b0-129">Çıkış</span><span class="sxs-lookup"><span data-stu-id="e68b0-129">Output</span></span>  
 <span data-ttu-id="e68b0-130">Bu MDA hiçbir çıktısı yok.</span><span class="sxs-lookup"><span data-stu-id="e68b0-130">There is no output for this MDA.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="e68b0-131">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="e68b0-131">Configuration</span></span>  
 <span data-ttu-id="e68b0-132">`modulus` Özniteliği, karma kod kullanılan modül belirtir.</span><span class="sxs-lookup"><span data-stu-id="e68b0-132">The `modulus` attribute specifies the modulus used on the hash code.</span></span> <span data-ttu-id="e68b0-133">Varsayılan değer 1’dir.</span><span class="sxs-lookup"><span data-stu-id="e68b0-133">The default value is 1.</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <moduloObjectHashcode modulus="1" />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e68b0-134">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e68b0-134">See Also</span></span>  
 <xref:System.Object.GetHashCode%2A?displayProperty=nameWithType>  
 <xref:System.Object.Equals%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="e68b0-135">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="e68b0-135">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
