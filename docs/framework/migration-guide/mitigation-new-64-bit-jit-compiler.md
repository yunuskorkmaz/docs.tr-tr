---
title: 'Azaltma: Yeni 64-bit JIT Derleyici'
ms.date: 03/30/2017
helpviewer_keywords:
- JIT compiler, 64-bit
- JIT compilation, 64-bit
- RyuJIT compiler
ms.assetid: 0332dabc-72c5-4bdc-8975-20d717802b17
ms.openlocfilehash: 883aaf032bde632b08f965d3450cfbea4feb8e65
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79181261"
---
# <a name="mitigation-new-64-bit-jit-compiler"></a><span data-ttu-id="f2003-102">Azaltma: Yeni 64-bit JIT Derleyici</span><span class="sxs-lookup"><span data-stu-id="f2003-102">Mitigation: New 64-bit JIT Compiler</span></span>
<span data-ttu-id="f2003-103">.NET Framework 4.6 ile başlayarak, çalışma süresi tam zamanında derleme için yeni bir 64 bit JIT derleyicisi içerir.</span><span class="sxs-lookup"><span data-stu-id="f2003-103">Starting with the .NET Framework 4.6, the runtime includes a new 64-bit JIT compiler for just-in-time compilation.</span></span> <span data-ttu-id="f2003-104">Bu değişiklik 32 bit JIT derleyicisi ile derleme etkilemez.</span><span class="sxs-lookup"><span data-stu-id="f2003-104">This change does not affect compilation with the  32-bit JIT compiler.</span></span>  
  
## <a name="unexpected-behavior-or-exceptions"></a><span data-ttu-id="f2003-105">Beklenmeyen davranış veya özel durumlar</span><span class="sxs-lookup"><span data-stu-id="f2003-105">Unexpected behavior or exceptions</span></span>  
 <span data-ttu-id="f2003-106">Bazı durumlarda, yeni 64 bit JIT derleyicisi ile derleme bir çalışma zamanı özel durum veya eski 64-bit JIT derleyicisi tarafından derlenen kod yürütüldüğünde gözlenmeyen davranış sonuçları.</span><span class="sxs-lookup"><span data-stu-id="f2003-106">In some cases, compilation with the new 64-bit JIT compiler results in a runtime exception or in behavior that is not observed when executing code compiled by the older 64-bit JIT compiler.</span></span> <span data-ttu-id="f2003-107">Bilinen farklar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="f2003-107">The known differences include the following:</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="f2003-108">Bilinen tüm bu sorunlar .NET Framework 4.6.2 ile yayımlanan yeni 64 bit derleyicide ele alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="f2003-108">All of these known issues have been addressed in the new 64-bit compiler released with the .NET Framework 4.6.2.</span></span> <span data-ttu-id="f2003-109">Çoğu, Windows Update ile birlikte verilen .NET Framework 4.6 ve 4.6.1'in hizmet sürümlerinde de ele alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="f2003-109">Most have also been addressed in service releases of the .NET Framework 4.6 and 4.6.1 that are included with Windows Update.</span></span> <span data-ttu-id="f2003-110">Windows sürümünüzün güncel olmasını sağlayarak veya .NET Framework 4.6.2'ye yükselterek bu sorunları ortadan kaldırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f2003-110">You can eliminate these issues by ensuring that your version of Windows is up to date, or by upgrading to the .NET Framework 4.6.2.</span></span>  
  
- <span data-ttu-id="f2003-111">Belirli koşullar altında, bir unboxing <xref:System.NullReferenceException> işlemi bir in Release oluşturur en iyi duruma getirilmesi açık atabilir.</span><span class="sxs-lookup"><span data-stu-id="f2003-111">Under certain conditions, an unboxing operation may throw a <xref:System.NullReferenceException> in Release builds with optimization turned on.</span></span>  
  
- <span data-ttu-id="f2003-112">Bazı durumlarda, büyük bir yöntem gövdesinde üretim <xref:System.StackOverflowException>kodunun yürütülmesi bir.</span><span class="sxs-lookup"><span data-stu-id="f2003-112">In some cases, execution of production code in a large method body may throw a <xref:System.StackOverflowException>.</span></span>  
  
- <span data-ttu-id="f2003-113">Belirli koşullar altında, bir yönteme geçirilen yapılar, Sürüm yapılarındaki değer türleri yerine başvuru türleri olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="f2003-113">Under certain conditions, structures passed to a method are treated as reference types rather than value types in Release builds.</span></span> <span data-ttu-id="f2003-114">Bu sorunun tezahürlerinden biri, koleksiyondaki tek tek öğelerin beklenmeyen bir sırada görünmesidir.</span><span class="sxs-lookup"><span data-stu-id="f2003-114">One of the manifestations of this issue is that the individual items in a collection appear in an unexpected order.</span></span>  
  
- <span data-ttu-id="f2003-115">Belirli koşullar altında, <xref:System.UInt16> en iyi duruma getirilmesi etkinse değerlerin yüksek bit kümeleriyle karşılaştırılması yanlıştır.</span><span class="sxs-lookup"><span data-stu-id="f2003-115">Under certain conditions, the comparison of <xref:System.UInt16> values with their high bit set is incorrect if optimization is enabled.</span></span>  
  
- <span data-ttu-id="f2003-116">Belirli koşullar altında, özellikle dizi değerlerini alırken, IL <xref:System.Reflection.Emit.OpCodes.Initblk?displayProperty=nameWithType> yönergesi ile bellek başlatma yanlış bir değerle belleği başlatmayı sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="f2003-116">Under certain conditions, particularly when initializing array values, memory initialization by the <xref:System.Reflection.Emit.OpCodes.Initblk?displayProperty=nameWithType> IL instruction may initialize memory with an incorrect value.</span></span> <span data-ttu-id="f2003-117">Bu, işlenmemiş bir özel durum veya yanlış çıktı neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="f2003-117">This can result either in an unhandled exception or incorrect output.</span></span>  
  
- <span data-ttu-id="f2003-118">Belirli nadir koşullar altında, koşullu bit <xref:System.Boolean> testi yanlış değeri döndürebilir veya derleyici optimizasyonları etkinse bir özel durum atabilir.</span><span class="sxs-lookup"><span data-stu-id="f2003-118">Under certain rare conditions, a conditional bit test can return the incorrect <xref:System.Boolean> value or throw an exception if compiler optimizations are enabled.</span></span>  
  
- <span data-ttu-id="f2003-119">Belirli koşullar altında, `if` bir `try` ifade bir blok girmeden önce ve `try` blok çıkışında bir durum için test etmek `catch` `finally` için kullanılırsa ve aynı koşul veya blok `if` tadisi sinde degistirilirse, yeni 64 bit JIT derleyicisi kodu en iyi duruma getirince durumu `catch` veya `finally` bloğu kaldırır.</span><span class="sxs-lookup"><span data-stu-id="f2003-119">Under certain conditions, if an `if` statement is used to test for a condition before entering  a `try` block and in the exit from the `try` block, and the same condition is evaluated in the `catch` or `finally` block, the new 64-bit JIT compiler removes the `if` condition from the `catch` or `finally` block when it optimizes code.</span></span> <span data-ttu-id="f2003-120">Sonuç olarak, ekstre `if` içindeki `catch` `finally` veya bloktaki kod koşulsuz olarak yürütülür.</span><span class="sxs-lookup"><span data-stu-id="f2003-120">As a result, code inside the `if` statement in the `catch` or `finally` block is executed unconditionally.</span></span>  
  
<a name="General"></a>
## <a name="mitigation-of-known-issues"></a><span data-ttu-id="f2003-121">Bilinen sorunların azaltılması</span><span class="sxs-lookup"><span data-stu-id="f2003-121">Mitigation of known issues</span></span>  
 <span data-ttu-id="f2003-122">Yukarıda listelenen sorunlarla karşılaşırsanız, aşağıdakilerden birini yaparak bunları ele alabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="f2003-122">If you encounter the issues listed above, you can address them by doing any of the following:</span></span>  
  
- <span data-ttu-id="f2003-123">.NET Framework 4.6.2'ye yükseltin.</span><span class="sxs-lookup"><span data-stu-id="f2003-123">Upgrade to the .NET Framework 4.6.2.</span></span> <span data-ttu-id="f2003-124">.NET Framework 4.6.2 ile birlikte eklenen yeni 64 bit derleyici, bilinen bu sorunların her birini giderir.</span><span class="sxs-lookup"><span data-stu-id="f2003-124">The new 64-bit compiler included with the .NET Framework 4.6.2 addresses each of these known issues.</span></span>  
  
- <span data-ttu-id="f2003-125">Windows Update çalıştırarak Windows sürümünüzün güncel olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="f2003-125">Ensure that your version of Windows is up to date by running Windows Update.</span></span> <span data-ttu-id="f2003-126">.NET Framework 4.6 ve 4.6.1'deki hizmet güncelleştirmeleri, kutudan çıkarma işlemi dışında <xref:System.NullReferenceException> bu sorunların her birini giderir.</span><span class="sxs-lookup"><span data-stu-id="f2003-126">Service updates to the .NET Framework 4.6 and 4.6.1 address each of these issues except the <xref:System.NullReferenceException> in an unboxing operation.</span></span>  
  
- <span data-ttu-id="f2003-127">Eski 64 bit JIT derleyicisi ile derle.</span><span class="sxs-lookup"><span data-stu-id="f2003-127">Compile with the older 64-bit JIT compiler.</span></span> <span data-ttu-id="f2003-128">Bunun nasıl yapılacıla ilgili daha fazla bilgi için [diğer sorunların azaltımı](#Other) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="f2003-128">See the [Mitigation of other issues](#Other) section for more information on how to do this.</span></span>  
  
<a name="Other"></a>
## <a name="mitigation-of-other-issues"></a><span data-ttu-id="f2003-129">Diğer konuların azaltılması</span><span class="sxs-lookup"><span data-stu-id="f2003-129">Mitigation of other issues</span></span>  
 <span data-ttu-id="f2003-130">Eski 64 bit derleyici ile derlenen kod ile yeni 64 bit JIT derleyicisi arasında veya uygulamanızın yeni 64 bit JIT derleyicisi ile derlenen hata ayıklama ve sürüm sürümleri arasında başka bir davranış farkıyla karşılaşırsanız, aşağıdakileri yapabilirsiniz: eski 64 bit JIT derleyicisi ile uygulamanızı derlemek için:</span><span class="sxs-lookup"><span data-stu-id="f2003-130">If you encounter any other difference in behavior between code compiled with the older 64-bit compiler and the new 64-bit JIT compiler, or between the debug and release versions of your app that are both compiled with the new 64-bit JIT compiler, you can do the following to compile your app with the older 64-bit JIT compiler:</span></span>  
  
- <span data-ttu-id="f2003-131">Uygulama başına olarak, uygulamanızın yapılandırma dosyasına [ \<LegacyJit>](../configure-apps/file-schema/runtime/uselegacyjit-element.md) öğesini ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f2003-131">On a per-application basis, you can add the [\<useLegacyJit>](../configure-apps/file-schema/runtime/uselegacyjit-element.md) element to your application's configuration file.</span></span> <span data-ttu-id="f2003-132">Aşağıdaki devre dışı bırakma derlemesi yeni 64 bit JIT derleyicisi ile ve bunun yerine eski 64 bit JIT derleyicisi kullanır.</span><span class="sxs-lookup"><span data-stu-id="f2003-132">The following disables compilation with the new 64-bit JIT compiler and instead uses the legacy 64-bit JIT compiler.</span></span>  
  
    ```xml  
    <?xml version ="1.0"?>  
    <configuration>  
        <runtime>  
           <useLegacyJit enabled="1" />  
        </runtime>  
    </configuration>  
    ```  
  
- <span data-ttu-id="f2003-133">Kullanıcı başına bazda, kayıt defterinin `REG_DWORD` `useLegacyJit` `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` anahtarına adlandırılmış bir değer ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f2003-133">On a per-user basis, you can add a `REG_DWORD` value named `useLegacyJit` to the `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` key of the registry.</span></span> <span data-ttu-id="f2003-134">1 değeri eski 64 bit JIT derleyicisini sağlar; 0 değerini devre dışı kılabilir ve yeni 64 bit JIT derleyicisini etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="f2003-134">A value of 1 enables the legacy 64-bit JIT compiler; a value of 0 disables it and enables the new 64-bit JIT compiler.</span></span>  
  
- <span data-ttu-id="f2003-135">Makine başına olarak, kayıt defterinin `REG_DWORD` `useLegacyJit` `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` anahtarına adlandırılmış bir değer ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f2003-135">On a per-machine basis, you can add a `REG_DWORD` value named `useLegacyJit` to the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` key of the registry.</span></span> <span data-ttu-id="f2003-136">1 değeri eski 64 bit JIT derleyicisini sağlar; 0 değerini devre dışı kılabilir ve yeni 64 bit JIT derleyicisini etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="f2003-136">A value of 1 enables the legacy 64-bit JIT compiler; a value of 0 disables it and enables the new 64-bit JIT compiler.</span></span>  
  
 <span data-ttu-id="f2003-137">Microsoft [Connect'te](https://connect.microsoft.com/VisualStudio)bir hata bildirerek sorun hakkında da bize bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f2003-137">You can also let us know about the problem by reporting a bug on [Microsoft Connect](https://connect.microsoft.com/VisualStudio).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2003-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f2003-138">See also</span></span>

- [<span data-ttu-id="f2003-139">Uygulama uyumluluğu</span><span class="sxs-lookup"><span data-stu-id="f2003-139">Application compatibility</span></span>](application-compatibility.md)
- [<span data-ttu-id="f2003-140">\<useLegacyJit> Element</span><span class="sxs-lookup"><span data-stu-id="f2003-140">\<useLegacyJit> Element</span></span>](../configure-apps/file-schema/runtime/uselegacyjit-element.md)
