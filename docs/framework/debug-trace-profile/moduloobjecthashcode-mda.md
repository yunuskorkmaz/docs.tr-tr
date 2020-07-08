---
title: moduloObjectHashcode MDA
description: ModuloObjectHashcode yönetilen hata ayıklama Yardımcısı 'nı (MDA) gözden geçirin. Bu, nesne sınıfını bir GetHashCode Yöntem sonucu üzerinde geri kalan bir değer elde etmek için değiştirir.
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
ms.openlocfilehash: a929ec2b9196f1f6cad0528fdf7323839a86fa55
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: tr-TR
ms.lasthandoff: 07/07/2020
ms.locfileid: "86052071"
---
# <a name="moduloobjecthashcode-mda"></a><span data-ttu-id="2fd2c-103">moduloObjectHashcode MDA</span><span class="sxs-lookup"><span data-stu-id="2fd2c-103">moduloObjectHashcode MDA</span></span>
<span data-ttu-id="2fd2c-104">`moduloObjectHashcode`Yönetilen hata ayıklama Yardımcısı (MDA), sınıfının davranışını, <xref:System.Object> yöntemi tarafından döndürülen karma kodda bir mod işlemi gerçekleştirmek için değiştirir <xref:System.Object.GetHashCode%2A> .</span><span class="sxs-lookup"><span data-stu-id="2fd2c-104">The `moduloObjectHashcode` managed debugging assistant (MDA) changes the behavior of the <xref:System.Object> class to perform a modulo operation on the hash code returned by the <xref:System.Object.GetHashCode%2A> method.</span></span> <span data-ttu-id="2fd2c-105">Bu MDA için varsayılan mod 1 ' dir ve <xref:System.Object.GetHashCode%2A> tüm nesneler için 0 döndürmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="2fd2c-105">The default modulus for this MDA is 1, which causes <xref:System.Object.GetHashCode%2A> to return 0 for all objects.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="2fd2c-106">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="2fd2c-106">Symptoms</span></span>  
 <span data-ttu-id="2fd2c-107">Ortak dil çalışma zamanının (CLR) yeni bir sürümüne taşıdıktan sonra, bir program artık düzgün şekilde çalışmaz:</span><span class="sxs-lookup"><span data-stu-id="2fd2c-107">After moving to a new version of the common language runtime (CLR), a program no longer executes properly:</span></span>  
  
- <span data-ttu-id="2fd2c-108">Program, öğesinden yanlış bir nesne alıyor <xref:System.Collections.Hashtable> .</span><span class="sxs-lookup"><span data-stu-id="2fd2c-108">The program is getting the wrong object from a <xref:System.Collections.Hashtable>.</span></span>  
  
- <span data-ttu-id="2fd2c-109">Bir öğesinden numaralandırmanın sırası, <xref:System.Collections.Hashtable> programı kesen bir değişikliğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="2fd2c-109">The order of enumeration from a <xref:System.Collections.Hashtable> has a change that breaks the program.</span></span>  
  
- <span data-ttu-id="2fd2c-110">Eşit olmak için kullanılan iki nesne artık eşit değildir.</span><span class="sxs-lookup"><span data-stu-id="2fd2c-110">Two objects that used to be equal are no longer equal.</span></span>  
  
- <span data-ttu-id="2fd2c-111">Eşit olmaması için kullanılan iki nesne artık eşittir.</span><span class="sxs-lookup"><span data-stu-id="2fd2c-111">Two objects that used to not be equal are now equal.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="2fd2c-112">Nedeni</span><span class="sxs-lookup"><span data-stu-id="2fd2c-112">Cause</span></span>  
 <span data-ttu-id="2fd2c-113">Yöntemi, <xref:System.Collections.Hashtable> <xref:System.Object.Equals%2A> <xref:System.Collections.Hashtable> çağrı sonuçlarını yönteme göre karşılaştırarak, anahtarın sınıf üzerindeki yöntemi, anahtar için olan yöntem için yanlış nesneyi alıyor olabilir <xref:System.Object.GetHashCode%2A> .</span><span class="sxs-lookup"><span data-stu-id="2fd2c-113">Your program may be getting the wrong object from a <xref:System.Collections.Hashtable> because the implementation of the <xref:System.Object.Equals%2A> method on the class for the key into the <xref:System.Collections.Hashtable> tests for equality of objects by comparing the results of the call to the <xref:System.Object.GetHashCode%2A> method.</span></span> <span data-ttu-id="2fd2c-114">Kendi alanları farklı değerlere sahip olsa bile iki nesne aynı karma koda sahip olabileceğinden, nesne eşitliğini test etmek için karma kodları kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="2fd2c-114">Hash codes should not be used to test for object equality because two objects may have the same hash code even if their respective fields have different values.</span></span> <span data-ttu-id="2fd2c-115">Bu karma kod çakışmaları, ancak uygulamada nadir olarak ortaya çıkar.</span><span class="sxs-lookup"><span data-stu-id="2fd2c-115">These hash code collisions, although rare in practice, do occur.</span></span> <span data-ttu-id="2fd2c-116">Bunun bir aramada sahip olduğu efekt, <xref:System.Collections.Hashtable> eşit olmayan iki anahtarın eşit gibi görüneceği ve öğesinden yanlış nesne döndürüldüğü anlamına gelir <xref:System.Collections.Hashtable> .</span><span class="sxs-lookup"><span data-stu-id="2fd2c-116">The effect this has on a <xref:System.Collections.Hashtable> lookup is that two keys which are not equal appear to be equal, and the wrong object is returned from the <xref:System.Collections.Hashtable>.</span></span> <span data-ttu-id="2fd2c-117">Performans nedenleriyle, ' nin uygulanması <xref:System.Object.GetHashCode%2A> çalışma zamanı sürümleri arasında değişebilir, bu nedenle, bir sürümde gerçekleşmeyecek olan çakışmalar sonraki sürümlerde meydana gelebilir.</span><span class="sxs-lookup"><span data-stu-id="2fd2c-117">For performance reasons, the implementation of <xref:System.Object.GetHashCode%2A> can change between runtime versions, so collisions that might not occur on one version might occur on subsequent versions.</span></span> <span data-ttu-id="2fd2c-118">Bu MDA ' i etkinleştirerek, karma kodları çarpışdığınızda kodunuzun hatalara sahip olup olmadığını test edin.</span><span class="sxs-lookup"><span data-stu-id="2fd2c-118">Enable this MDA to test whether your code has bugs when hash codes collide.</span></span> <span data-ttu-id="2fd2c-119">Etkinleştirildiğinde bu MDA, <xref:System.Object.GetHashCode%2A> yöntemin 0 döndürmesini sağlar, sonuçta tüm karma kodlarının çakışmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="2fd2c-119">When enabled, this MDA causes the <xref:System.Object.GetHashCode%2A> method to return 0, resulting in all hash codes colliding.</span></span> <span data-ttu-id="2fd2c-120">Bu MDA ' i etkinleştiren tek efekt, programınızın daha yavaş çalışmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="2fd2c-120">The only effect enabling this MDA should have on your program is that your program runs slower.</span></span>  
  
 <span data-ttu-id="2fd2c-121"><xref:System.Collections.Hashtable>Anahtar değişikliği için karma kodları hesaplamak üzere kullanılan algoritma bir çalışma zamanının bir sürümünden diğerine değişebilir.</span><span class="sxs-lookup"><span data-stu-id="2fd2c-121">The order of enumeration from a <xref:System.Collections.Hashtable> may change from one version of the runtime to another if the algorithm used to compute the hash codes for the key change.</span></span> <span data-ttu-id="2fd2c-122">Programınızın bir karma tablonun anahtar veya değer listesi sırasına göre bağımlılığı yapıp gerçekleştirmediğini test etmek için bu MDA ' yi etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2fd2c-122">To test whether your program has taken a dependency on the order of enumeration of keys or values out of a hash table, you can enable this MDA.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="2fd2c-123">Çözüm</span><span class="sxs-lookup"><span data-stu-id="2fd2c-123">Resolution</span></span>  
 <span data-ttu-id="2fd2c-124">Karma kodları, nesne kimliği için bir alternatif olarak hiçbir şekilde kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="2fd2c-124">Never use hash codes as a substitute for object identity.</span></span> <span data-ttu-id="2fd2c-125"><xref:System.Object.Equals%2A?displayProperty=nameWithType>Karma kodlarını karşılaştırmayan yöntemi geçersiz kılmayı uygulayın.</span><span class="sxs-lookup"><span data-stu-id="2fd2c-125">Implement the override of the <xref:System.Object.Equals%2A?displayProperty=nameWithType> method to not compare hash codes.</span></span>  
  
 <span data-ttu-id="2fd2c-126">Karma tablolardaki anahtarların veya değerlerin numaralandırmalar sırasıyla bağımlılıklar oluşturmayın.</span><span class="sxs-lookup"><span data-stu-id="2fd2c-126">Do not create dependencies on the order of enumerations of keys or values in hash tables.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="2fd2c-127">Çalışma zamanında etki</span><span class="sxs-lookup"><span data-stu-id="2fd2c-127">Effect on the Runtime</span></span>  
 <span data-ttu-id="2fd2c-128">Bu MDA etkinleştirildiğinde uygulamalar daha yavaş çalışır.</span><span class="sxs-lookup"><span data-stu-id="2fd2c-128">Applications run more slowly when this MDA is enabled.</span></span> <span data-ttu-id="2fd2c-129">Bu MDA yalnızca döndürülen karma kodu alır ve bunun yerine, bir mod ile ayrıldığınızda kalanı döndürür.</span><span class="sxs-lookup"><span data-stu-id="2fd2c-129">This MDA simply takes the hash code that would have been returned and instead returns the remainder when divided by a modulus.</span></span>  
  
## <a name="output"></a><span data-ttu-id="2fd2c-130">Çıktı</span><span class="sxs-lookup"><span data-stu-id="2fd2c-130">Output</span></span>  
 <span data-ttu-id="2fd2c-131">Bu MDA için çıkış yok.</span><span class="sxs-lookup"><span data-stu-id="2fd2c-131">There is no output for this MDA.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="2fd2c-132">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="2fd2c-132">Configuration</span></span>  
 <span data-ttu-id="2fd2c-133">`modulus`Öznitelik, karma kodunda kullanılan mod 'u belirtir.</span><span class="sxs-lookup"><span data-stu-id="2fd2c-133">The `modulus` attribute specifies the modulus used on the hash code.</span></span> <span data-ttu-id="2fd2c-134">Varsayılan değer 1’dir.</span><span class="sxs-lookup"><span data-stu-id="2fd2c-134">The default value is 1.</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <moduloObjectHashcode modulus="1" />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="2fd2c-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2fd2c-135">See also</span></span>

- <xref:System.Object.GetHashCode%2A?displayProperty=nameWithType>
- <xref:System.Object.Equals%2A?displayProperty=nameWithType>
- [<span data-ttu-id="2fd2c-136">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="2fd2c-136">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
