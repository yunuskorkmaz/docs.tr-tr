---
title: 'Risk azaltma: yeni 64-bit JıT derleyicisi'
ms.date: 03/30/2017
helpviewer_keywords:
- JIT compiler, 64-bit
- JIT compilation, 64-bit
- RyuJIT compiler
ms.assetid: 0332dabc-72c5-4bdc-8975-20d717802b17
ms.openlocfilehash: dd8c2c6b3cfa919970f68f2faae2044568f6c9ac
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73457917"
---
# <a name="mitigation-new-64-bit-jit-compiler"></a><span data-ttu-id="baf67-102">Risk azaltma: yeni 64-bit JıT derleyicisi</span><span class="sxs-lookup"><span data-stu-id="baf67-102">Mitigation: New 64-bit JIT Compiler</span></span>
<span data-ttu-id="baf67-103">.NET Framework 4,6 ' den başlayarak, çalışma zamanı tam zamanında derleme için yeni bir 64 bit JıT derleyicisi içerir.</span><span class="sxs-lookup"><span data-stu-id="baf67-103">Starting with the .NET Framework 4.6, the runtime includes a new 64-bit JIT compiler for just-in-time compilation.</span></span> <span data-ttu-id="baf67-104">Bu değişiklik, 32 bit JıT derleyicisi ile derlemeyi etkilemez.</span><span class="sxs-lookup"><span data-stu-id="baf67-104">This change does not affect compilation with the  32-bit JIT compiler.</span></span>  
  
## <a name="unexpected-behavior-or-exceptions"></a><span data-ttu-id="baf67-105">Beklenmeyen davranış veya özel durumlar</span><span class="sxs-lookup"><span data-stu-id="baf67-105">Unexpected behavior or exceptions</span></span>  
 <span data-ttu-id="baf67-106">Bazı durumlarda, yeni 64-bit JıT derleyicisi ile derleme, çalışma zamanı özel durumu veya eski 64 bit JıT derleyicisi tarafından derlenen kodu yürütürken gözlemlenmemiş davranışlar ile sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="baf67-106">In some cases, compilation with the new 64-bit JIT compiler results in a runtime exception or in behavior that is not observed when executing code compiled by the older 64-bit JIT compiler.</span></span> <span data-ttu-id="baf67-107">Bilinen farklılıklar şunları içerir:</span><span class="sxs-lookup"><span data-stu-id="baf67-107">The known differences include the following:</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="baf67-108">Bu bilinen sorunların tümü, .NET Framework 4.6.2 ile yayınlanan yeni 64 bit derleyicide ele alındı.</span><span class="sxs-lookup"><span data-stu-id="baf67-108">All of these known issues have been addressed in the new 64-bit compiler released with the .NET Framework 4.6.2.</span></span> <span data-ttu-id="baf67-109">Çoğu Ayrıca, Windows Update dahil edilen .NET Framework 4,6 ve 4.6.1 hizmet sürümlerinde de giderilmiştir.</span><span class="sxs-lookup"><span data-stu-id="baf67-109">Most have also been addressed in service releases of the .NET Framework 4.6 and 4.6.1 that are included with Windows Update.</span></span> <span data-ttu-id="baf67-110">Windows sürümünüzün güncel olmasını sağlayarak veya 4.6.2 .NET Framework yükselterek bu sorunları ortadan kaldırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="baf67-110">You can eliminate these issues by ensuring that your version of Windows is up to date, or by upgrading to the .NET Framework 4.6.2.</span></span>  
  
- <span data-ttu-id="baf67-111">Belirli koşullar altında, bir kutudan çıkarma işlemi en iyi duruma getirme özelliği açık olan yayın yapılarından <xref:System.NullReferenceException> oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="baf67-111">Under certain conditions, an unboxing operation may throw a <xref:System.NullReferenceException> in Release builds with optimization turned on.</span></span>  
  
- <span data-ttu-id="baf67-112">Bazı durumlarda, büyük bir yöntem gövdesinde üretim kodunun yürütülmesi <xref:System.StackOverflowException>oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="baf67-112">In some cases, execution of production code in a large method body may throw a <xref:System.StackOverflowException>.</span></span>  
  
- <span data-ttu-id="baf67-113">Belirli koşullar altında, bir yönteme geçirilen yapılar, yayın Derlemeleriyle değer türleri yerine başvuru türleri olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="baf67-113">Under certain conditions, structures passed to a method are treated as reference types rather than value types in Release builds.</span></span> <span data-ttu-id="baf67-114">Bu sorunun bildirimli bir şekilde, bir koleksiyondaki tek öğelerin beklenmeyen bir sırada görünmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="baf67-114">One of the manifestations of this issue is that the individual items in a collection appear in an unexpected order.</span></span>  
  
- <span data-ttu-id="baf67-115">Belirli koşullar altında, en iyi duruma getirme etkinse <xref:System.UInt16> değerlerinin yüksek bit kümesiyle karşılaştırılması yanlış olur.</span><span class="sxs-lookup"><span data-stu-id="baf67-115">Under certain conditions, the comparison of <xref:System.UInt16> values with their high bit set is incorrect if optimization is enabled.</span></span>  
  
- <span data-ttu-id="baf67-116">Belirli koşullar altında, özellikle dizi değerlerini başlatırken, <xref:System.Reflection.Emit.OpCodes.Initblk?displayProperty=nameWithType> Il yönergesi tarafından bellek başlatma, hatalı bir değerle belleği başlatabilir.</span><span class="sxs-lookup"><span data-stu-id="baf67-116">Under certain conditions, particularly when initializing array values, memory initialization by the <xref:System.Reflection.Emit.OpCodes.Initblk?displayProperty=nameWithType> IL instruction may initialize memory with an incorrect value.</span></span> <span data-ttu-id="baf67-117">Bu, işlenmemiş bir özel durum ya da yanlış çıkışa neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="baf67-117">This can result either in an unhandled exception or incorrect output.</span></span>  
  
- <span data-ttu-id="baf67-118">Bazı nadir koşullarda, koşullu bir bit testi yanlış <xref:System.Boolean> değerini döndürebilir veya derleyici iyileştirmeleri etkinse bir özel durum oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="baf67-118">Under certain rare conditions, a conditional bit test can return the incorrect <xref:System.Boolean> value or throw an exception if compiler optimizations are enabled.</span></span>  
  
- <span data-ttu-id="baf67-119">Belirli koşullar altında, bir `if` bildiri, bir `try` bloğunu girmeden önce bir koşulu test etmek için kullanılırsa ve `try` bloğundan çıkışta, `catch` veya `finally` bloğunda aynı koşul değerlendirilir Yeni 64-bit JıT derleyicisi, kodu en iyi duruma getirirken `catch` veya `finally` bloğundan `if` koşulunu kaldırır.</span><span class="sxs-lookup"><span data-stu-id="baf67-119">Under certain conditions, if an `if` statement is used to test for a condition before entering  a `try` block and in the exit from the `try` block, and the same condition is evaluated in the `catch` or `finally` block, the new 64-bit JIT compiler removes the `if` condition from the `catch` or `finally` block when it optimizes code.</span></span> <span data-ttu-id="baf67-120">Sonuç olarak, `catch` veya `finally` bloğundaki `if` deyimin içindeki kod koşulsuz olarak yürütülür.</span><span class="sxs-lookup"><span data-stu-id="baf67-120">As a result, code inside the `if` statement in the `catch` or `finally` block is executed unconditionally.</span></span>  
  
<a name="General"></a>   
## <a name="mitigation-of-known-issues"></a><span data-ttu-id="baf67-121">Bilinen sorunların risk azaltma</span><span class="sxs-lookup"><span data-stu-id="baf67-121">Mitigation of known issues</span></span>  
 <span data-ttu-id="baf67-122">Yukarıda listelenen sorunlarla karşılaşırsanız, aşağıdakilerden birini yaparak bunları ele alabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="baf67-122">If you encounter the issues listed above, you can address them by doing any of the following:</span></span>  
  
- <span data-ttu-id="baf67-123">.NET Framework 4.6.2 ' ye yükseltin.</span><span class="sxs-lookup"><span data-stu-id="baf67-123">Upgrade to the .NET Framework 4.6.2.</span></span> <span data-ttu-id="baf67-124">.NET Framework 4.6.2 ile birlikte sunulan yeni 64 bitlik derleyici, bu bilinen sorunların her birini ele alır.</span><span class="sxs-lookup"><span data-stu-id="baf67-124">The new 64-bit compiler included with the .NET Framework 4.6.2 addresses each of these known issues.</span></span>  
  
- <span data-ttu-id="baf67-125">Windows Update çalıştırarak Windows sürümünüzün güncel olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="baf67-125">Ensure that your version of Windows is up to date by running Windows Update.</span></span> <span data-ttu-id="baf67-126">.NET Framework 4,6 ve 4.6.1 için hizmet güncelleştirmeleri, kutudan çıkarma işleminde <xref:System.NullReferenceException> hariç, bu sorunlardan her birini adresleyen.</span><span class="sxs-lookup"><span data-stu-id="baf67-126">Service updates to the .NET Framework 4.6 and 4.6.1 address each of these issues except the <xref:System.NullReferenceException> in an unboxing operation.</span></span>  
  
- <span data-ttu-id="baf67-127">Daha eski 64 bit JıT derleyicisi ile derleyin.</span><span class="sxs-lookup"><span data-stu-id="baf67-127">Compile with the older 64-bit JIT compiler.</span></span> <span data-ttu-id="baf67-128">Bunun nasıl yapılacağı hakkında daha fazla bilgi için [diğer sorunların hafifletme](#Other) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="baf67-128">See the [Mitigation of other issues](#Other) section for more information on how to do this.</span></span>  
  
<a name="Other"></a>   
## <a name="mitigation-of-other-issues"></a><span data-ttu-id="baf67-129">Diğer sorunları azaltma</span><span class="sxs-lookup"><span data-stu-id="baf67-129">Mitigation of other issues</span></span>  
 <span data-ttu-id="baf67-130">Eski 64 bit derleyicisi ile derlenen kod ve yeni 64-bit JıT derleyicisi ile derlenmiş kod arasındaki davranışta veya yeni 64-bit JıT derleyicisi ile derlenen uygulamanızın hata ayıklama ve yayın sürümleri arasında başka bir farklılık yaşarsanız, aşağıdakileri yapabilirsiniz Uygulamanızı eski 64 bit JıT derleyicisi ile derlemek için:</span><span class="sxs-lookup"><span data-stu-id="baf67-130">If you encounter any other difference in behavior between code compiled with the older 64-bit compiler and the new 64-bit JIT compiler, or between the debug and release versions of your app that are both compiled with the new 64-bit JIT compiler, you can do the following to compile your app with the older 64-bit JIT compiler:</span></span>  
  
- <span data-ttu-id="baf67-131">Uygulama başına temelinde, [\<useLegacyJit >](../configure-apps/file-schema/runtime/uselegacyjit-element.md) öğesini uygulamanızın yapılandırma dosyasına ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="baf67-131">On a per-application basis, you can add the [\<useLegacyJit>](../configure-apps/file-schema/runtime/uselegacyjit-element.md) element to your application's configuration file.</span></span> <span data-ttu-id="baf67-132">Aşağıdakiler, yeni 64-bit JıT derleyicisi ile derlemeyi devre dışı bırakır ve bunun yerine eski 64 bit JıT derleyicisini kullanır.</span><span class="sxs-lookup"><span data-stu-id="baf67-132">The following disables compilation with the new 64-bit JIT compiler and instead uses the legacy 64-bit JIT compiler.</span></span>  
  
    ```xml  
    <?xml version ="1.0"?>  
    <configuration>  
        <runtime>  
           <useLegacyJit enabled="1" />  
        </runtime>  
    </configuration>  
    ```  
  
- <span data-ttu-id="baf67-133">Kullanıcı başına temelinde, kayıt defterinin `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` anahtarına `useLegacyJit` adlı `REG_DWORD` bir değer ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="baf67-133">On a per-user basis, you can add a `REG_DWORD` value named `useLegacyJit` to the `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` key of the registry.</span></span> <span data-ttu-id="baf67-134">1 değeri, eski 64-bit JıT derleyicisini sunar; 0 değeri devre dışı bırakır ve yeni 64 bit JıT derleyicisini etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="baf67-134">A value of 1 enables the legacy 64-bit JIT compiler; a value of 0 disables it and enables the new 64-bit JIT compiler.</span></span>  
  
- <span data-ttu-id="baf67-135">Makine başına temelinde, kayıt defterinin `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` anahtarına `useLegacyJit` adlı `REG_DWORD` bir değer ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="baf67-135">On a per-machine basis, you can add a `REG_DWORD` value named `useLegacyJit` to the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` key of the registry.</span></span> <span data-ttu-id="baf67-136">1 değeri, eski 64-bit JıT derleyicisini sunar; 0 değeri devre dışı bırakır ve yeni 64 bit JıT derleyicisini etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="baf67-136">A value of 1 enables the legacy 64-bit JIT compiler; a value of 0 disables it and enables the new 64-bit JIT compiler.</span></span>  
  
 <span data-ttu-id="baf67-137">Ayrıca, [Microsoft Connect](https://connect.microsoft.com/VisualStudio)'te bir hata bildirerek sorun hakkında bilgi sahibi olalım.</span><span class="sxs-lookup"><span data-stu-id="baf67-137">You can also let us know about the problem by reporting a bug on [Microsoft Connect](https://connect.microsoft.com/VisualStudio).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="baf67-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="baf67-138">See also</span></span>

- [<span data-ttu-id="baf67-139">Uygulama uyumluluğu</span><span class="sxs-lookup"><span data-stu-id="baf67-139">Application compatibility</span></span>](application-compatibility.md)
- [<span data-ttu-id="baf67-140">\<useLegacyJit > öğesi</span><span class="sxs-lookup"><span data-stu-id="baf67-140">\<useLegacyJit> Element</span></span>](../configure-apps/file-schema/runtime/uselegacyjit-element.md)
