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
ms.openlocfilehash: 65bbdfec2d7050d1b474a8186a9ea6e9bb93bd9e
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77216175"
---
# <a name="moduloobjecthashcode-mda"></a><span data-ttu-id="558e2-102">moduloObjectHashcode MDA</span><span class="sxs-lookup"><span data-stu-id="558e2-102">moduloObjectHashcode MDA</span></span>
<span data-ttu-id="558e2-103">`moduloObjectHashcode` yönetilen hata ayıklama Yardımcısı (MDA), <xref:System.Object.GetHashCode%2A> yöntemi tarafından döndürülen karma kodda bir mod işlemi gerçekleştirmek için <xref:System.Object> sınıfının davranışını değiştirir.</span><span class="sxs-lookup"><span data-stu-id="558e2-103">The `moduloObjectHashcode` managed debugging assistant (MDA) changes the behavior of the <xref:System.Object> class to perform a modulo operation on the hash code returned by the <xref:System.Object.GetHashCode%2A> method.</span></span> <span data-ttu-id="558e2-104">Bu MDA için varsayılan mod 1 ' dir ve bu, <xref:System.Object.GetHashCode%2A> tüm nesneler için 0 döndürmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="558e2-104">The default modulus for this MDA is 1, which causes <xref:System.Object.GetHashCode%2A> to return 0 for all objects.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="558e2-105">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="558e2-105">Symptoms</span></span>  
 <span data-ttu-id="558e2-106">Ortak dil çalışma zamanının (CLR) yeni bir sürümüne taşıdıktan sonra, bir program artık düzgün şekilde çalışmaz:</span><span class="sxs-lookup"><span data-stu-id="558e2-106">After moving to a new version of the common language runtime (CLR), a program no longer executes properly:</span></span>  
  
- <span data-ttu-id="558e2-107">Program <xref:System.Collections.Hashtable>yanlış nesneyi alıyor.</span><span class="sxs-lookup"><span data-stu-id="558e2-107">The program is getting the wrong object from a <xref:System.Collections.Hashtable>.</span></span>  
  
- <span data-ttu-id="558e2-108"><xref:System.Collections.Hashtable> numaralandırmanın sırası, programı kesen bir değişikliğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="558e2-108">The order of enumeration from a <xref:System.Collections.Hashtable> has a change that breaks the program.</span></span>  
  
- <span data-ttu-id="558e2-109">Eşit olmak için kullanılan iki nesne artık eşit değildir.</span><span class="sxs-lookup"><span data-stu-id="558e2-109">Two objects that used to be equal are no longer equal.</span></span>  
  
- <span data-ttu-id="558e2-110">Eşit olmaması için kullanılan iki nesne artık eşittir.</span><span class="sxs-lookup"><span data-stu-id="558e2-110">Two objects that used to not be equal are now equal.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="558e2-111">Nedeni</span><span class="sxs-lookup"><span data-stu-id="558e2-111">Cause</span></span>  
 <span data-ttu-id="558e2-112">Bir <xref:System.Collections.Hashtable>, anahtar için sınıfındaki <xref:System.Object.Equals%2A> yönteminin, <xref:System.Object.GetHashCode%2A> yöntemine yapılan çağrının sonuçlarını karşılaştırarak, nesne eşitlik için <xref:System.Collections.Hashtable> testlerindeki yanlış nesneyi alıyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="558e2-112">Your program may be getting the wrong object from a <xref:System.Collections.Hashtable> because the implementation of the <xref:System.Object.Equals%2A> method on the class for the key into the <xref:System.Collections.Hashtable> tests for equality of objects by comparing the results of the call to the <xref:System.Object.GetHashCode%2A> method.</span></span> <span data-ttu-id="558e2-113">Kendi alanları farklı değerlere sahip olsa bile iki nesne aynı karma koda sahip olabileceğinden, nesne eşitliğini test etmek için karma kodları kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="558e2-113">Hash codes should not be used to test for object equality because two objects may have the same hash code even if their respective fields have different values.</span></span> <span data-ttu-id="558e2-114">Bu karma kod çakışmaları, ancak uygulamada nadir olarak ortaya çıkar.</span><span class="sxs-lookup"><span data-stu-id="558e2-114">These hash code collisions, although rare in practice, do occur.</span></span> <span data-ttu-id="558e2-115">Bunun <xref:System.Collections.Hashtable> arama üzerindeki etkisi, eşit olmayan iki anahtarın eşit olduğu gibi görüneceği ve <xref:System.Collections.Hashtable>yanlış nesnenin döndürüldüğü anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="558e2-115">The effect this has on a <xref:System.Collections.Hashtable> lookup is that two keys which are not equal appear to be equal, and the wrong object is returned from the <xref:System.Collections.Hashtable>.</span></span> <span data-ttu-id="558e2-116">Performans nedenleriyle, <xref:System.Object.GetHashCode%2A> uygulanması çalışma zamanı sürümleri arasında değişebilir, bu nedenle, bir sürümde gerçekleşmeyecek olan çakışmalar sonraki sürümlerde meydana gelebilir.</span><span class="sxs-lookup"><span data-stu-id="558e2-116">For performance reasons, the implementation of <xref:System.Object.GetHashCode%2A> can change between runtime versions, so collisions that might not occur on one version might occur on subsequent versions.</span></span> <span data-ttu-id="558e2-117">Bu MDA ' i etkinleştirerek, karma kodları çarpışdığınızda kodunuzun hatalara sahip olup olmadığını test edin.</span><span class="sxs-lookup"><span data-stu-id="558e2-117">Enable this MDA to test whether your code has bugs when hash codes collide.</span></span> <span data-ttu-id="558e2-118">Etkinleştirildiğinde, bu MDA <xref:System.Object.GetHashCode%2A> yönteminin 0 döndürmesini sağlar, sonuçta tüm karma kodlarının çakışmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="558e2-118">When enabled, this MDA causes the <xref:System.Object.GetHashCode%2A> method to return 0, resulting in all hash codes colliding.</span></span> <span data-ttu-id="558e2-119">Bu MDA ' i etkinleştiren tek efekt, programınızın daha yavaş çalışmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="558e2-119">The only effect enabling this MDA should have on your program is that your program runs slower.</span></span>  
  
 <span data-ttu-id="558e2-120">Bir <xref:System.Collections.Hashtable> numaralandırma sırası, anahtar değişikliği için karma kodları hesaplamak üzere kullanılan algoritma, çalışma zamanının bir sürümünden diğerine değişebilir.</span><span class="sxs-lookup"><span data-stu-id="558e2-120">The order of enumeration from a <xref:System.Collections.Hashtable> may change from one version of the runtime to another if the algorithm used to compute the hash codes for the key change.</span></span> <span data-ttu-id="558e2-121">Programınızın bir karma tablonun anahtar veya değer listesi sırasına göre bağımlılığı yapıp gerçekleştirmediğini test etmek için bu MDA ' yi etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="558e2-121">To test whether your program has taken a dependency on the order of enumeration of keys or values out of a hash table, you can enable this MDA.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="558e2-122">Çözüm</span><span class="sxs-lookup"><span data-stu-id="558e2-122">Resolution</span></span>  
 <span data-ttu-id="558e2-123">Karma kodları, nesne kimliği için bir alternatif olarak hiçbir şekilde kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="558e2-123">Never use hash codes as a substitute for object identity.</span></span> <span data-ttu-id="558e2-124">Karma kodları karşılaştırmadan <xref:System.Object.Equals%2A?displayProperty=nameWithType> yönteminin geçersiz kılmasını uygulayın.</span><span class="sxs-lookup"><span data-stu-id="558e2-124">Implement the override of the <xref:System.Object.Equals%2A?displayProperty=nameWithType> method to not compare hash codes.</span></span>  
  
 <span data-ttu-id="558e2-125">Karma tablolardaki anahtarların veya değerlerin numaralandırmalar sırasıyla bağımlılıklar oluşturmayın.</span><span class="sxs-lookup"><span data-stu-id="558e2-125">Do not create dependencies on the order of enumerations of keys or values in hash tables.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="558e2-126">Çalışma zamanında etki</span><span class="sxs-lookup"><span data-stu-id="558e2-126">Effect on the Runtime</span></span>  
 <span data-ttu-id="558e2-127">Bu MDA etkinleştirildiğinde uygulamalar daha yavaş çalışır.</span><span class="sxs-lookup"><span data-stu-id="558e2-127">Applications run more slowly when this MDA is enabled.</span></span> <span data-ttu-id="558e2-128">Bu MDA yalnızca döndürülen karma kodu alır ve bunun yerine, bir mod ile ayrıldığınızda kalanı döndürür.</span><span class="sxs-lookup"><span data-stu-id="558e2-128">This MDA simply takes the hash code that would have been returned and instead returns the remainder when divided by a modulus.</span></span>  
  
## <a name="output"></a><span data-ttu-id="558e2-129">Çıktı</span><span class="sxs-lookup"><span data-stu-id="558e2-129">Output</span></span>  
 <span data-ttu-id="558e2-130">Bu MDA için çıkış yok.</span><span class="sxs-lookup"><span data-stu-id="558e2-130">There is no output for this MDA.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="558e2-131">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="558e2-131">Configuration</span></span>  
 <span data-ttu-id="558e2-132">`modulus` özniteliği, karma kodda kullanılan mod 'u belirtir.</span><span class="sxs-lookup"><span data-stu-id="558e2-132">The `modulus` attribute specifies the modulus used on the hash code.</span></span> <span data-ttu-id="558e2-133">Varsayılan değer 1’dir.</span><span class="sxs-lookup"><span data-stu-id="558e2-133">The default value is 1.</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <moduloObjectHashcode modulus="1" />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="558e2-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="558e2-134">See also</span></span>

- <xref:System.Object.GetHashCode%2A?displayProperty=nameWithType>
- <xref:System.Object.Equals%2A?displayProperty=nameWithType>
- [<span data-ttu-id="558e2-135">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="558e2-135">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
