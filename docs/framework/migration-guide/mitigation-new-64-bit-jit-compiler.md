---
title: 'Azaltma: Yeni 64 bit JIT Derleyici'
ms.date: 03/30/2017
helpviewer_keywords:
- JIT compiler, 64-bit
- JIT compilation, 64-bit
- RyuJIT compiler
ms.assetid: 0332dabc-72c5-4bdc-8975-20d717802b17
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f3177ae53d8b932a52dccf11b12d44fd07ec1c4f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59226631"
---
# <a name="mitigation-new-64-bit-jit-compiler"></a><span data-ttu-id="c4a35-102">Azaltma: Yeni 64 bit JIT Derleyici</span><span class="sxs-lookup"><span data-stu-id="c4a35-102">Mitigation: New 64-bit JIT Compiler</span></span>
<span data-ttu-id="c4a35-103">.NET Framework 4. 6 ile başlayarak, çalışma zamanı tam zamanında derleme için yeni bir 64 bit JIT derleyicisi içerir.</span><span class="sxs-lookup"><span data-stu-id="c4a35-103">Starting with the .NET Framework 4.6, the runtime includes a new 64-bit JIT compiler for just-in-time compilation.</span></span> <span data-ttu-id="c4a35-104">Bu değişiklik, 32-bit JIT Derleyici ile derleme etkilemez.</span><span class="sxs-lookup"><span data-stu-id="c4a35-104">This change does not affect compilation with the  32-bit JIT compiler.</span></span>  
  
## <a name="unexpected-behavior-or-exceptions"></a><span data-ttu-id="c4a35-105">Beklenmeyen davranış veya özel durumları</span><span class="sxs-lookup"><span data-stu-id="c4a35-105">Unexpected behavior or exceptions</span></span>  
 <span data-ttu-id="c4a35-106">Bazı durumlarda, yeni 64 bit JIT Derleyici ile derleme çalışma zamanı özel veya eski 64 bit JIT derleyicisi tarafından derlenen kod yürütülürken uyulmuyor davranışı sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="c4a35-106">In some cases, compilation with the new 64-bit JIT compiler results in a runtime exception or in behavior that is not observed when executing code compiled by the older 64-bit JIT compiler.</span></span> <span data-ttu-id="c4a35-107">Bilinen farklar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="c4a35-107">The known differences include the following:</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c4a35-108">Bu bilinen sorunlara ilişkin tüm .NET Framework 4.6.2 ile sunulan yeni 64 bit derleyicide çözüldü.</span><span class="sxs-lookup"><span data-stu-id="c4a35-108">All of these known issues have been addressed in the new 64-bit compiler released with the .NET Framework 4.6.2.</span></span> <span data-ttu-id="c4a35-109">Çoğu, ayrıca Windows Update ile birlikte hizmet sürümlerinde .NET Framework 4.6 ve 4.6.1 çözüldü.</span><span class="sxs-lookup"><span data-stu-id="c4a35-109">Most have also been addressed in service releases of the .NET Framework 4.6 and 4.6.1 that are included with Windows Update.</span></span> <span data-ttu-id="c4a35-110">Windows sürümünüz güncel veya .NET Framework 4.6.2 yükselterek sağlayarak bu sorunları ortadan kaldırabilir.</span><span class="sxs-lookup"><span data-stu-id="c4a35-110">You can eliminate these issues by ensuring that your version of Windows is up to date, or by upgrading to the .NET Framework 4.6.2.</span></span>  
  
-   <span data-ttu-id="c4a35-111">Belirli koşullar altında bir kutudan çıkarma işlemi oluşturabilecek bir <xref:System.NullReferenceException> sürüm yapılarında açık iyileştirme.</span><span class="sxs-lookup"><span data-stu-id="c4a35-111">Under certain conditions, an unboxing operation may throw a <xref:System.NullReferenceException> in Release builds with optimization turned on.</span></span>  
  
-   <span data-ttu-id="c4a35-112">Bazı durumlarda, üretim kodunda büyük yöntem gövdesinin yürütülmesini oluşturabilecek bir <xref:System.StackOverflowException>.</span><span class="sxs-lookup"><span data-stu-id="c4a35-112">In some cases, execution of production code in a large method body may throw a <xref:System.StackOverflowException>.</span></span>  
  
-   <span data-ttu-id="c4a35-113">Belirli koşullar altında yayın içindeki değer türleri derlemeler yerine bir yönteme yapıları başvuru türleri olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="c4a35-113">Under certain conditions, structures passed to a method are treated as reference types rather than value types in Release builds.</span></span> <span data-ttu-id="c4a35-114">Bu sorunun belirtileri bir koleksiyondaki tek tek öğelerin beklenmedik bir sırada göründüğünü biridir.</span><span class="sxs-lookup"><span data-stu-id="c4a35-114">One of the manifestations of this issue is that the individual items in a collection appear in an unexpected order.</span></span>  
  
-   <span data-ttu-id="c4a35-115">Karşılaştırma işleminin belirli koşullar altında <xref:System.UInt16> bunların yüksek bit kümesi değerlerle iyileştirme etkinleştirildiğinde yanlış.</span><span class="sxs-lookup"><span data-stu-id="c4a35-115">Under certain conditions, the comparison of <xref:System.UInt16> values with their high bit set is incorrect if optimization is enabled.</span></span>  
  
-   <span data-ttu-id="c4a35-116">Bazı koşullar altında özellikle zaman dizi başlatma değerleri, bellek başlatma tarafından <xref:System.Reflection.Emit.OpCodes.Initblk?displayProperty=nameWithType> IL yönergesinin başlatmak bellek yanlış bir değere sahip.</span><span class="sxs-lookup"><span data-stu-id="c4a35-116">Under certain conditions, particularly when initializing array values, memory initialization by the <xref:System.Reflection.Emit.OpCodes.Initblk?displayProperty=nameWithType> IL instruction may initialize memory with an incorrect value.</span></span> <span data-ttu-id="c4a35-117">Bu, bir işlenmeyen özel durum veya yanlış çıkış sonuçlanabilir.</span><span class="sxs-lookup"><span data-stu-id="c4a35-117">This can result either in an unhandled exception or incorrect output.</span></span>  
  
-   <span data-ttu-id="c4a35-118">Nadir bazı koşullarda koşullu bit test yanlış döndürebilir <xref:System.Boolean> değer veya derleyici iyileştirmeleri etkinleştirilip etkinleştirilmediğini bir özel durum.</span><span class="sxs-lookup"><span data-stu-id="c4a35-118">Under certain rare conditions, a conditional bit test can return the incorrect <xref:System.Boolean> value or throw an exception if compiler optimizations are enabled.</span></span>  
  
-   <span data-ttu-id="c4a35-119">Belirli koşullar altında bir `if` deyimi girmeden önce koşulu test etmek için kullanılır bir `try` blok ve çıkın `try` blok ve aynı koşul içinde değerlendirilir `catch` veya `finally` blok, yeni 64 bit JIT Derleyici kaldırır `if` gelen koşul `catch` veya `finally` kodu en iyi duruma getirir, engelleyin.</span><span class="sxs-lookup"><span data-stu-id="c4a35-119">Under certain conditions, if an `if` statement is used to test for a condition before entering  a `try` block and in the exit from the `try` block, and the same condition is evaluated in the `catch` or `finally` block, the new 64-bit JIT compiler removes the `if` condition from the `catch` or `finally` block when it optimizes code.</span></span> <span data-ttu-id="c4a35-120">Sonuç olarak, içindeki kod `if` deyiminde `catch` veya `finally` blok koşulsuz olarak yürütülür.</span><span class="sxs-lookup"><span data-stu-id="c4a35-120">As a result, code inside the `if` statement in the `catch` or `finally` block is executed unconditionally.</span></span>  
  
<a name="General"></a>   
## <a name="mitigation-of-known-issues"></a><span data-ttu-id="c4a35-121">Bilinen sorunlara ilişkin azaltma</span><span class="sxs-lookup"><span data-stu-id="c4a35-121">Mitigation of known issues</span></span>  
 <span data-ttu-id="c4a35-122">Yukarıda listelenen bir sorunla karşılaşırsanız aşağıdakilerden birini yaparak karşılayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="c4a35-122">If you encounter the issues listed above, you can address them by doing any of the following:</span></span>  
  
-   <span data-ttu-id="c4a35-123">.NET Framework 4.6.2 yükseltin.</span><span class="sxs-lookup"><span data-stu-id="c4a35-123">Upgrade to the .NET Framework 4.6.2.</span></span> <span data-ttu-id="c4a35-124">.NET Framework 4.6.2 dahil yeni bir 64 bit Derleyici her biri bu bilinen sorunları ele alır.</span><span class="sxs-lookup"><span data-stu-id="c4a35-124">The new 64-bit compiler included with the .NET Framework 4.6.2 addresses each of these known issues.</span></span>  
  
-   <span data-ttu-id="c4a35-125">Windows Update çalıştırarak Windows sürümünüz güncel olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="c4a35-125">Ensure that your version of Windows is up to date by running Windows Update.</span></span> <span data-ttu-id="c4a35-126">.NET Framework 4.6 ve 4.6.1 için hizmet güncelleştirmeleri her dışında bu sorunları gidermek <xref:System.NullReferenceException> kutudan Çıkarma işleminde.</span><span class="sxs-lookup"><span data-stu-id="c4a35-126">Service updates to the .NET Framework 4.6 and 4.6.1 address each of these issues except the <xref:System.NullReferenceException> in an unboxing operation.</span></span>  
  
-   <span data-ttu-id="c4a35-127">Eski 64 bit JIT Derleyici ile derleyin.</span><span class="sxs-lookup"><span data-stu-id="c4a35-127">Compile with the older 64-bit JIT compiler.</span></span> <span data-ttu-id="c4a35-128">Bkz: [diğer sorunların azaltma](#Other) bölüm bunun nasıl yapılacağı hakkında daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="c4a35-128">See the [Mitigation of other issues](#Other) section for more information on how to do this.</span></span>  
  
<a name="Other"></a>   
## <a name="mitigation-of-other-issues"></a><span data-ttu-id="c4a35-129">Diğer sorunları riskini azaltma</span><span class="sxs-lookup"><span data-stu-id="c4a35-129">Mitigation of other issues</span></span>  
 <span data-ttu-id="c4a35-130">Herhangi diğer davranıştaki farkı eski 64 bit derleyici ve yeni 64 bit JIT Derleyici ile derlenmiş kod arasında ya da uygulamanızın yeni bir 64 bit JIT Derleyici ile derlenmiş hata ayıklama ve yayın sürümleri arasında karşılaşırsanız, aşağıdakileri yapabilirsiniz eski 64 bit JIT Derleyici ile uygulamanızı derlemek için:</span><span class="sxs-lookup"><span data-stu-id="c4a35-130">If you encounter any other difference in behavior between code compiled with the older 64-bit compiler and the new 64-bit JIT compiler, or between the debug and release versions of your app that are both compiled with the new 64-bit JIT compiler, you can do the following to compile your app with the older 64-bit JIT compiler:</span></span>  
  
-   <span data-ttu-id="c4a35-131">Uygulama başına temelinde, eklediğiniz [ \<useLegacyJit >](../../../docs/framework/configure-apps/file-schema/runtime/uselegacyjit-element.md) uygulamanızın yapılandırma dosyasına öğesi.</span><span class="sxs-lookup"><span data-stu-id="c4a35-131">On a per-application basis, you can add the [\<useLegacyJit>](../../../docs/framework/configure-apps/file-schema/runtime/uselegacyjit-element.md) element to your application's configuration file.</span></span> <span data-ttu-id="c4a35-132">Aşağıdaki yeni 64 bit JIT Derleyici ile derleme devre dışı bırakır ve bunun yerine, eski 64 bit JIT Derleyici kullanır.</span><span class="sxs-lookup"><span data-stu-id="c4a35-132">The following disables compilation with the new 64-bit JIT compiler and instead uses the legacy 64-bit JIT compiler.</span></span>  
  
    ```xml  
    <?xml version ="1.0"?>  
    <configuration>  
        <runtime>  
           <useLegacyJit enabled="1" />  
        </runtime>  
    </configuration>  
    ```  
  
-   <span data-ttu-id="c4a35-133">Bir kullanıcı başına esasına göre ekleyebileceğiniz bir `REG_DWORD` değeri `useLegacyJit` için `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` kayıt defteri anahtarı.</span><span class="sxs-lookup"><span data-stu-id="c4a35-133">On a per-user basis, you can add a `REG_DWORD` value named `useLegacyJit` to the `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` key of the registry.</span></span> <span data-ttu-id="c4a35-134">1 değeri, eski 64 bit JIT Derleyici etkinleştirir; 0 değeri, devre dışı bırakır ve yeni 64 bit JIT Derleyici sağlar.</span><span class="sxs-lookup"><span data-stu-id="c4a35-134">A value of 1 enables the legacy 64-bit JIT compiler; a value of 0 disables it and enables the new 64-bit JIT compiler.</span></span>  
  
-   <span data-ttu-id="c4a35-135">Bir makine başına temelinde ekleyebileceğiniz bir `REG_DWORD` değeri `useLegacyJit` için `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` kayıt defteri anahtarı.</span><span class="sxs-lookup"><span data-stu-id="c4a35-135">On a per-machine basis, you can add a `REG_DWORD` value named `useLegacyJit` to the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` key of the registry.</span></span> <span data-ttu-id="c4a35-136">1 değeri, eski 64 bit JIT Derleyici etkinleştirir; 0 değeri, devre dışı bırakır ve yeni 64 bit JIT Derleyici sağlar.</span><span class="sxs-lookup"><span data-stu-id="c4a35-136">A value of 1 enables the legacy 64-bit JIT compiler; a value of 0 disables it and enables the new 64-bit JIT compiler.</span></span>  
  
 <span data-ttu-id="c4a35-137">Ayrıca sorun hakkında bir hata bildirimi tarafından bize [Microsoft Connect](https://connect.microsoft.com/VisualStudio).</span><span class="sxs-lookup"><span data-stu-id="c4a35-137">You can also let us know about the problem by reporting a bug on [Microsoft Connect](https://connect.microsoft.com/VisualStudio).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4a35-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c4a35-138">See also</span></span>

- [<span data-ttu-id="c4a35-139">Çalışma Zamanı Değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="c4a35-139">Runtime Changes</span></span>](../../../docs/framework/migration-guide/runtime-changes-in-the-net-framework-4-6.md)
- [<span data-ttu-id="c4a35-140">\<useLegacyJit > öğesi</span><span class="sxs-lookup"><span data-stu-id="c4a35-140">\<useLegacyJit> Element</span></span>](../../../docs/framework/configure-apps/file-schema/runtime/uselegacyjit-element.md)
