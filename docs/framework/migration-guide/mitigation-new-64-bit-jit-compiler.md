---
title: 'Azaltma: Yeni 64-bit JIT derleme'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-bcl
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- JIT compiler, 64-bit
- JIT compilation, 64-bit
- RyuJIT compiler
ms.assetid: 0332dabc-72c5-4bdc-8975-20d717802b17
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 091b83cc0d7829c8ff078e6397aa480895b7a115
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="mitigation-new-64-bit-jit-compiler"></a><span data-ttu-id="e542c-102">Azaltma: Yeni 64-bit JIT derleme</span><span class="sxs-lookup"><span data-stu-id="e542c-102">Mitigation: New 64-bit JIT Compiler</span></span>
<span data-ttu-id="e542c-103">.NET Framework 4.6 ile başlayarak, çalışma zamanı tam zamanında derleme için yeni bir 64-bit JIT Derleyici içerir.</span><span class="sxs-lookup"><span data-stu-id="e542c-103">Starting with the .NET Framework 4.6, the runtime includes a new 64-bit JIT compiler for just-in-time compilation.</span></span> <span data-ttu-id="e542c-104">Bu değişiklik, 32-bit JIT derleyicisi ile derleme etkilemez.</span><span class="sxs-lookup"><span data-stu-id="e542c-104">This change does not affect compilation with the  32-bit JIT compiler.</span></span>  
  
## <a name="unexpected-behavior-or-exceptions"></a><span data-ttu-id="e542c-105">Beklenmeyen davranışları ya da özel durumlar</span><span class="sxs-lookup"><span data-stu-id="e542c-105">Unexpected behavior or exceptions</span></span>  
 <span data-ttu-id="e542c-106">Bazı durumlarda, bir çalışma zamanı özel veya eski 64-bit JIT derleyicisi tarafından derlenen kod yürütülürken gözlenir değil davranışı derleme yeni 64-bit JIT derleyicisi ile sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="e542c-106">In some cases, compilation with the new 64-bit JIT compiler results in a runtime exception or in behavior that is not observed when executing code compiled by the older 64-bit JIT compiler.</span></span> <span data-ttu-id="e542c-107">Bilinen farklar aşağıdakileri içerir:</span><span class="sxs-lookup"><span data-stu-id="e542c-107">The known differences include the following:</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="e542c-108">Bu bilinen sorunların tümünü .NET Framework 4.6.2 ile yayımlanan yeni 64 bit derleyici giderilmiştir.</span><span class="sxs-lookup"><span data-stu-id="e542c-108">All of these known issues have been addressed in the new 64-bit compiler released with the .NET Framework 4.6.2.</span></span> <span data-ttu-id="e542c-109">Çoğu ayrıca Windows Update ile dahil edilen hizmet sürümlerinde .NET Framework 4.6 ve 4.6.1 giderilmiştir.</span><span class="sxs-lookup"><span data-stu-id="e542c-109">Most have also been addressed in service releases of the .NET Framework 4.6 and 4.6.1 that are included with Windows Update.</span></span> <span data-ttu-id="e542c-110">Windows sürümünüz güncel, .NET Framework 4.6.2 yükselterek mi sağlayarak bu sorunları ortadan kaldırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e542c-110">You can eliminate these issues by ensuring that your version of Windows is up to date, or by upgrading to the .NET Framework 4.6.2.</span></span>  
  
-   <span data-ttu-id="e542c-111">Belirli koşullar altında kutudan çıkarma işlemi atabilir bir <xref:System.NullReferenceException> yayın derlemelerinde açık iyileştirme.</span><span class="sxs-lookup"><span data-stu-id="e542c-111">Under certain conditions, an unboxing operation may throw a <xref:System.NullReferenceException> in Release builds with optimization turned on.</span></span>  
  
-   <span data-ttu-id="e542c-112">Bazı durumlarda, üretim kodunda büyük yöntem gövdesi yürütülmesi atabilir bir <xref:System.StackOverflowException>.</span><span class="sxs-lookup"><span data-stu-id="e542c-112">In some cases, execution of production code in a large method body may throw a <xref:System.StackOverflowException>.</span></span>  
  
-   <span data-ttu-id="e542c-113">Değer türleri sürümdeki derlemeler yerine belirli koşullar altında bir yönteme geçirilen yapıları başvuru türleri olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="e542c-113">Under certain conditions, structures passed to a method are treated as reference types rather than value types in Release builds.</span></span> <span data-ttu-id="e542c-114">Bu sorun belirtileri bir koleksiyon içindeki öğeleri beklenmeyen bir düzende görünür biridir.</span><span class="sxs-lookup"><span data-stu-id="e542c-114">One of the manifestations of this issue is that the individual items in a collection appear in an unexpected order.</span></span>  
  
-   <span data-ttu-id="e542c-115">Karşılaştırması belirli koşullar altında <xref:System.UInt16> değerleri kendi yüksek bit kümesiyle iyileştirme etkinleştirilirse yanlış.</span><span class="sxs-lookup"><span data-stu-id="e542c-115">Under certain conditions, the comparison of <xref:System.UInt16> values with their high bit set is incorrect if optimization is enabled.</span></span>  
  
-   <span data-ttu-id="e542c-116">Belirli koşullar altında özellikle zaman dizi başlatma değerleri, bellek başlatma tarafından <xref:System.Reflection.Emit.OpCodes.Initblk?displayProperty=nameWithType> IL yönerge belleğe yanlış bir değere sahip başlatmak.</span><span class="sxs-lookup"><span data-stu-id="e542c-116">Under certain conditions, particularly when initializing array values, memory initialization by the <xref:System.Reflection.Emit.OpCodes.Initblk?displayProperty=nameWithType> IL instruction may initialize memory with an incorrect value.</span></span> <span data-ttu-id="e542c-117">Bu da bir işlenmeyen özel durum ya da hatalı çıktı neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="e542c-117">This can result either in an unhandled exception or incorrect output.</span></span>  
  
-   <span data-ttu-id="e542c-118">Nadir belirli koşullar altında koşullu bit test yanlış döndürebilir <xref:System.Boolean> değer veya derleyici iyileştirmesi etkinleştirilmişse bir özel durum.</span><span class="sxs-lookup"><span data-stu-id="e542c-118">Under certain rare conditions, a conditional bit test can return the incorrect <xref:System.Boolean> value or throw an exception if compiler optimizations are enabled.</span></span>  
  
-   <span data-ttu-id="e542c-119">Belirli koşullar altında bir `if` deyimi için bir koşul girmeden önce sınamak için kullanılan bir `try` blok ve çıkın `try` bloğu ve aynı koşul olarak değerlendirildiği `catch` veya `finally` bloğu, yeni 64 bit JIT Derleyici kaldırır `if` gelen koşul `catch` veya `finally` kod iyileştirir olduğunda engelleme.</span><span class="sxs-lookup"><span data-stu-id="e542c-119">Under certain conditions, if an `if` statement is used to test for a condition before entering  a `try` block and in the exit from the `try` block, and the same condition is evaluated in the `catch` or `finally` block, the new 64-bit JIT compiler removes the `if` condition from the `catch` or `finally` block when it optimizes code.</span></span> <span data-ttu-id="e542c-120">Sonuç olarak, içindeki kod `if` deyiminde `catch` veya `finally` blok koşulsuz olarak yürütülür.</span><span class="sxs-lookup"><span data-stu-id="e542c-120">As a result, code inside the `if` statement in the `catch` or `finally` block is executed unconditionally.</span></span>  
  
<a name="General"></a>   
## <a name="mitigation-of-known-issues"></a><span data-ttu-id="e542c-121">Bilinen sorunlar azaltma</span><span class="sxs-lookup"><span data-stu-id="e542c-121">Mitigation of known issues</span></span>  
 <span data-ttu-id="e542c-122">Yukarıda listelenen sorunlarla karşılaşırsanız, aşağıdakilerden birini yaparak karşılayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="e542c-122">If you encounter the issues listed above, you can address them by doing any of the following:</span></span>  
  
-   <span data-ttu-id="e542c-123">.NET Framework 4.6.2'ye yükseltin.</span><span class="sxs-lookup"><span data-stu-id="e542c-123">Upgrade to the .NET Framework 4.6.2.</span></span> <span data-ttu-id="e542c-124">.NET Framework 4.6.2 dahil yeni 64 bit Derleyici her bu bilinen sorunları giderir.</span><span class="sxs-lookup"><span data-stu-id="e542c-124">The new 64-bit compiler included with the .NET Framework 4.6.2 addresses each of these known issues.</span></span>  
  
-   <span data-ttu-id="e542c-125">Windows Update çalıştırarak Windows sürümünüz güncel olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="e542c-125">Ensure that your version of Windows is up to date by running Windows Update.</span></span> <span data-ttu-id="e542c-126">.NET Framework 4.6 ve 4.6.1 için hizmet güncelleştirmeleri her dışında bu sorunların adres <xref:System.NullReferenceException> kutudan Çıkarma işleminde.</span><span class="sxs-lookup"><span data-stu-id="e542c-126">Service updates to the .NET Framework 4.6 and 4.6.1 address each of these issues except the <xref:System.NullReferenceException> in an unboxing operation.</span></span>  
  
-   <span data-ttu-id="e542c-127">Eski 64-bit JIT derleyicisi ile derleyin.</span><span class="sxs-lookup"><span data-stu-id="e542c-127">Compile with the older 64-bit JIT compiler.</span></span> <span data-ttu-id="e542c-128">Bkz: [azaltma diğer sorunların](#Other) bunun nasıl yapılacağı hakkında daha fazla bilgi için bölüm.</span><span class="sxs-lookup"><span data-stu-id="e542c-128">See the [Mitigation of other issues](#Other) section for more information on how to do this.</span></span>  
  
<a name="Other"></a>   
## <a name="mitigation-of-other-issues"></a><span data-ttu-id="e542c-129">Diğer sorunlar azaltma</span><span class="sxs-lookup"><span data-stu-id="e542c-129">Mitigation of other issues</span></span>  
 <span data-ttu-id="e542c-130">Herhangi diğer bir fark davranış eski 64 bit derleyici ve yeni 64-bit JIT derleyicisi ile derlenmiş kod arasında ya da her ikisini de yeni 64-bit JIT derleyicisi ile derlenen hata ayıklama ve yayın sürümleri arasında uygulamanızı karşılaşırsanız, şunları yapabilirsiniz eski 64-bit JIT derleyicisi ile uygulamanızı derlemek için:</span><span class="sxs-lookup"><span data-stu-id="e542c-130">If you encounter any other difference in behavior between code compiled with the older 64-bit compiler and the new 64-bit JIT compiler, or between the debug and release versions of your app that are both compiled with the new 64-bit JIT compiler, you can do the following to compile your app with the older 64-bit JIT compiler:</span></span>  
  
-   <span data-ttu-id="e542c-131">Bir uygulama başına temelinde eklediğiniz [ \<useLegacyJit >](../../../docs/framework/configure-apps/file-schema/runtime/uselegacyjit-element.md) , uygulamanızın yapılandırma dosyasına öğesi.</span><span class="sxs-lookup"><span data-stu-id="e542c-131">On a per-application basis, you can add the [\<useLegacyJit>](../../../docs/framework/configure-apps/file-schema/runtime/uselegacyjit-element.md) element to your application's configuration file.</span></span> <span data-ttu-id="e542c-132">Aşağıdaki yeni 64-bit JIT derleyicisi ile derlemeyi devre dışı bırakır ve bunun yerine eski 64-bit JIT Derleyici kullanır.</span><span class="sxs-lookup"><span data-stu-id="e542c-132">The following disables compilation with the new 64-bit JIT compiler and instead uses the legacy 64-bit JIT compiler.</span></span>  
  
    ```xml  
    <?xml version ="1.0"?>  
    <configuration>  
        <runtime>  
           <useLegacyJit enabled="1" />  
        </runtime>  
    </configuration>  
    ```  
  
-   <span data-ttu-id="e542c-133">Bir kullanıcı başına temelinde eklediğiniz bir `REG_DWORD` adlı değeri `useLegacyJit` için `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` kayıt defteri anahtarı.</span><span class="sxs-lookup"><span data-stu-id="e542c-133">On a per-user basis, you can add a `REG_DWORD` value named `useLegacyJit` to the `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` key of the registry.</span></span> <span data-ttu-id="e542c-134">1 değeri eski 64-bit JIT derleyicisi tanır; 0 değeri, devre dışı bırakır ve yeni 64-bit JIT Derleyici sağlar.</span><span class="sxs-lookup"><span data-stu-id="e542c-134">A value of 1 enables the legacy 64-bit JIT compiler; a value of 0 disables it and enables the new 64-bit JIT compiler.</span></span>  
  
-   <span data-ttu-id="e542c-135">Bir makine başına temelinde eklediğiniz bir `REG_DWORD` adlı değeri `useLegacyJit` için `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` kayıt defteri anahtarı.</span><span class="sxs-lookup"><span data-stu-id="e542c-135">On a per-machine basis, you can add a `REG_DWORD` value named `useLegacyJit` to the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` key of the registry.</span></span> <span data-ttu-id="e542c-136">1 değeri eski 64-bit JIT derleyicisi tanır; 0 değeri, devre dışı bırakır ve yeni 64-bit JIT Derleyici sağlar.</span><span class="sxs-lookup"><span data-stu-id="e542c-136">A value of 1 enables the legacy 64-bit JIT compiler; a value of 0 disables it and enables the new 64-bit JIT compiler.</span></span>  
  
 <span data-ttu-id="e542c-137">Ayrıca bize sorun hakkında bir hata bildirimi tarafından bilmeniz [Microsoft Connect](https://connect.microsoft.com/VisualStudio).</span><span class="sxs-lookup"><span data-stu-id="e542c-137">You can also let us know about the problem by reporting a bug on [Microsoft Connect](https://connect.microsoft.com/VisualStudio).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e542c-138">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e542c-138">See Also</span></span>  
 [<span data-ttu-id="e542c-139">Çalışma zamanı değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="e542c-139">Runtime Changes</span></span>](../../../docs/framework/migration-guide/runtime-changes-in-the-net-framework-4-6.md)  
 [<span data-ttu-id="e542c-140">\<useLegacyJit > öğesi</span><span class="sxs-lookup"><span data-stu-id="e542c-140">\<useLegacyJit> Element</span></span>](../../../docs/framework/configure-apps/file-schema/runtime/uselegacyjit-element.md)
