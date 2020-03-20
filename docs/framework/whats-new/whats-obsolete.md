---
title: .NET Framework'de neler geçersizdir?
ms.custom: updateeachrelease
ms.date: 04/02/2019
helpviewer_keywords:
- obsolete [.NET Framework]
- what's obsolete [.NET Framework]
- deprecated [.NET Framework]
ms.assetid: d356a43a-73df-4ae2-a457-b9628074c7cd
ms.openlocfilehash: 7cfebfde859a95495e9d2d5e42bd034ad5d55e61
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79143141"
---
# <a name="whats-obsolete-in-the-net-framework-class-library"></a><span data-ttu-id="4f047-102">.NET Framework sınıf kitaplığında geçersiz olanlar</span><span class="sxs-lookup"><span data-stu-id="4f047-102">What's obsolete in the .NET Framework class library</span></span>

<span data-ttu-id="4f047-103">.NET zaman içinde değişir.</span><span class="sxs-lookup"><span data-stu-id="4f047-103">.NET changes over time.</span></span> <span data-ttu-id="4f047-104">Her yeni sürüm, yeni işlevler sağlayan yeni türler ve tür üyeleri ekler.</span><span class="sxs-lookup"><span data-stu-id="4f047-104">Each new version adds new types and type members that provide new functionality.</span></span> <span data-ttu-id="4f047-105">Varolan türler ve üyeleri de zaman içinde değişir.</span><span class="sxs-lookup"><span data-stu-id="4f047-105">Existing types and their members also change over time.</span></span> <span data-ttu-id="4f047-106">Örneğin, destekledikleri teknoloji yeni bir teknolojiyle değiştirildikçe bazı türler daha az önem eger ve bazı yöntemlerin yerini bir şekilde üstün olan yeni yöntemler alır.</span><span class="sxs-lookup"><span data-stu-id="4f047-106">For example, some types become less important as the technology they support is replaced by a new technology, and some methods are superseded by newer methods that are superior in some way.</span></span>

<span data-ttu-id="4f047-107">.NET Framework ve ortak dil çalışma süresi geriye dönük uyumluluğu desteklemeye çalışır (.NET Framework'ün bir sürümüyle geliştirilen uygulamaların .NET Framework'ün bir sonraki sürümünde çalışmasına izin verir).</span><span class="sxs-lookup"><span data-stu-id="4f047-107">.NET Framework and the common language runtime strive to support backward compatibility (allowing applications that were developed with one version of .NET Framework to run on the next version of .NET Framework).</span></span> <span data-ttu-id="4f047-108">Bu, yalnızca bir türü veya bir tür üyesini kaldırmayı zorlaştırır.</span><span class="sxs-lookup"><span data-stu-id="4f047-108">This makes it difficult to simply remove a type or a type member.</span></span> <span data-ttu-id="4f047-109">Bunun yerine,.NET, bir tür veya tür üyesinin artık eski veya amortismanlı olarak işaretlenerek kullanılmaması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="4f047-109">Instead, .NET indicates that a type or a type member should no longer be used by marking it as obsolete or deprecated.</span></span> <span data-ttu-id="4f047-110">Bir türü veya bir üyeyi küçümsemek, geliştiricilerin bu türün ortadan kaldırılacağını ve kaldırılmasına yanıt vermek için zamana sahip olacağının farkında olması için işaretlemeyi içerir.</span><span class="sxs-lookup"><span data-stu-id="4f047-110">Deprecating a type or a member involves marking it so that developers are aware it will go away and have time to respond to its removal.</span></span> <span data-ttu-id="4f047-111">Ancak, türü veya üyeyi kullanan varolan kod .NET'in yeni sürümünde çalışmamaya devam eder.</span><span class="sxs-lookup"><span data-stu-id="4f047-111">However, existing code that uses the type or member continues to run in the new version of .NET.</span></span>

> [!NOTE]
> <span data-ttu-id="4f047-112">.NET türleri ve üyelerine uygulandığında *eski* ve *amortismana uygulanan* terimler aynı anlama gelir.</span><span class="sxs-lookup"><span data-stu-id="4f047-112">The terms *obsolete* and *deprecated* have the same meaning when applied to .NET types and members.</span></span>

## <a name="the-obsoleteattribute-attribute"></a><span data-ttu-id="4f047-113">EskiÖz Öznitelik özniteliği</span><span class="sxs-lookup"><span data-stu-id="4f047-113">The ObsoleteAttribute attribute</span></span>

<span data-ttu-id="4f047-114">.NET Framework, bir tür veya tür üyesinin <xref:System.ObsoleteAttribute> öznitelik ile işaretleyerek eski olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="4f047-114">The .NET Framework indicates that a type or type member is obsolete by marking it with the <xref:System.ObsoleteAttribute> attribute.</span></span> <span data-ttu-id="4f047-115">Bir türe veya üyeye öznitelik uygulanması, bu üyeyi kullanan derlenmiş kodu bozmadan .NET Framework'ün gelecekteki bazı sürümünde tür veya üyenin kaldırılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="4f047-115">Applying the attribute to a type or member indicates that type or member will be removed in some future version of the .NET Framework without breaking compiled code that uses that member.</span></span>

<span data-ttu-id="4f047-116">Bir tür veya tür üyesinin eski olduğunu belirtmenin <xref:System.ObsoleteAttribute> yanı sıra, derleyicinin bu türü veya üyeyi içeren kaynak kodu nasıl işleyeceğini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="4f047-116">In addition to indicating that a type or a type member is obsolete, <xref:System.ObsoleteAttribute> defines how the compiler handles source code that includes that type or member.</span></span> <span data-ttu-id="4f047-117">Derleyici kodu derleyebilir, ancak bir uyarı iletisi yatabilir veya tür veya üyenin kullanımını bir hata olarak değerlendirebilir.</span><span class="sxs-lookup"><span data-stu-id="4f047-117">The compiler can compile the code but emit a warning message, or it can treat the use of the type or member as an error.</span></span> <span data-ttu-id="4f047-118">İlk durumda, kod başarıyla derlenebilir, ancak bir uyarı iletisi türün veya üyenin geçersiz olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="4f047-118">In the first case, the code can successfully compile, but a warning message indicates that the type or member is obsolete.</span></span> <span data-ttu-id="4f047-119">İkinci durumda, derleme başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="4f047-119">In the second case, compilation fails.</span></span>

<span data-ttu-id="4f047-120">Derleme uyarı iletisi yerine bir hata <xref:System.ObsoleteAttribute> üretse bile, çalışma zamanı davranışını etkilemez.</span><span class="sxs-lookup"><span data-stu-id="4f047-120">Even if compilation produces an error instead of a warning message, <xref:System.ObsoleteAttribute> does not affect run-time behavior.</span></span> <span data-ttu-id="4f047-121">Diğer bir arada, türü veya üyeyi kullanan ve başarılı bir şekilde derlenen uygulamalar her zaman başarılı bir şekilde çalışır.</span><span class="sxs-lookup"><span data-stu-id="4f047-121">That is, applications that use the type or member and that have compiled successfully will always run successfully.</span></span> <span data-ttu-id="4f047-122">Yalnızca türü veya üyeyi kullanan bir uygulamayı yeniden derleme girişimi başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="4f047-122">Only the attempt to recompile an application that uses the type or member fails.</span></span>

## <a name="how-to-handle-obsolete-types-and-members"></a><span data-ttu-id="4f047-123">Eski türleri ve üyeleri işlemek için nasıl</span><span class="sxs-lookup"><span data-stu-id="4f047-123">How to handle obsolete types and members</span></span>

<span data-ttu-id="4f047-124">Varolan kodu yükselttidiğinizde ve yeniden derlediğinizde, eski bir tür veya uygulamanızda derleyici uyarısı üreten üye yi kullanarak mükemmel bir şekilde kabul edilebilir.</span><span class="sxs-lookup"><span data-stu-id="4f047-124">When you upgrade and recompile existing code, using an obsolete type or member that produces a compiler warning in your application is perfectly acceptable.</span></span> <span data-ttu-id="4f047-125">Ancak, uygulama kodunuzu değiştirip değiştirmemeniz gerekmediğini belirlemek için derleyici uyarı iletisini gözden geçirmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="4f047-125">However, you should review the compiler warning message to determine whether you should change your application code.</span></span> <span data-ttu-id="4f047-126">İleti uygun bir alternatife işaret etmiyorsa, aşağıdakilerden birini yapmalısınız:</span><span class="sxs-lookup"><span data-stu-id="4f047-126">If the message does not point to a suitable alternative, you should do either of the following:</span></span>

- <span data-ttu-id="4f047-127">Mümkünse türü veya üyekullanımını kaldırarak kodunuzu değiştirin.</span><span class="sxs-lookup"><span data-stu-id="4f047-127">Change your code by removing the use of the type or member, if possible.</span></span>

     <span data-ttu-id="4f047-128">-veya-</span><span class="sxs-lookup"><span data-stu-id="4f047-128">-or-</span></span>

- <span data-ttu-id="4f047-129">Amortismana nasıl yanıt verileceksiniz belirlemek için bu teknoloji alanı için belgeleri gözden geçirin.</span><span class="sxs-lookup"><span data-stu-id="4f047-129">Review the documentation for this technology area to determine how to respond to the deprecation.</span></span>

<span data-ttu-id="4f047-130">Varolan kodu .NET Framework'ün sonraki bir sürümüne göre yeniden derlememeyi seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4f047-130">You may choose not to recompile existing code against a later version of the .NET Framework.</span></span> <span data-ttu-id="4f047-131">Bunun yerine, .NET Framework'ün mevcut derlenmiş kodunuzu çalıştırdığı sürümünü belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4f047-131">Instead, you can specify the version of the .NET Framework against which your existing compiled code runs.</span></span> <span data-ttu-id="4f047-132">Örneğin, .NET Framework 3.5'e karşı derlenmiş app1.exe adında bir uygulamanız olduğunu, ancak uygulamanın .NET Framework 4.5'e karşı çalışmasını istediğinizi varsayalım.</span><span class="sxs-lookup"><span data-stu-id="4f047-132">For example, suppose that you have an application named app1.exe that was compiled against the .NET Framework 3.5, but you want the application to run against the .NET Framework 4.5.</span></span> <span data-ttu-id="4f047-133">Bu, aşağıdaki adımları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="4f047-133">This requires the following steps:</span></span>

1. <span data-ttu-id="4f047-134">Ana yürütülebilirliğiniz için bir yapılandırma dosyası oluşturun ve *appName*.exe.config adını ve *appName'nin* yürütülebilir uygulamanın adı olduğunu belirtin.</span><span class="sxs-lookup"><span data-stu-id="4f047-134">Create a configuration file for your main executable and name it *appName*.exe.config, where *appName* is the name of the application executable.</span></span> <span data-ttu-id="4f047-135">Örneğimizde *app1.exe* adlı uygulama için *app1.exe.config*adlı bir yapılandırma dosyası oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="4f047-135">For the application named *app1.exe* in our example, you would create a configuration file named *app1.exe.config*.</span></span>

2. <span data-ttu-id="4f047-136">Yapılandırma dosyasına aşağıdakileri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="4f047-136">Add the following to the configuration file.</span></span>

    ```xml
    <configuration>
       <startup>
          <supportedRuntime version="v4.0" />
       </startup>
    </configuration>
    ```

<span data-ttu-id="4f047-137">.NET Framework'ün belirli bir sürümünü hedeflemek için, `version` özniteliğe aşağıdaki dize değerlerinden birini atayın:</span><span class="sxs-lookup"><span data-stu-id="4f047-137">To target a specific version of .NET Framework, assign one of the following string values to the `version` attribute:</span></span>

|<span data-ttu-id="4f047-138">.NET Framework sürümü</span><span class="sxs-lookup"><span data-stu-id="4f047-138">.NET Framework version</span></span>|<span data-ttu-id="4f047-139">`version`Dize</span><span class="sxs-lookup"><span data-stu-id="4f047-139">`version` string</span></span>|
|-|-|
|<span data-ttu-id="4f047-140">4.8</span><span class="sxs-lookup"><span data-stu-id="4f047-140">4.8</span></span>|<span data-ttu-id="4f047-141">v4.0</span><span class="sxs-lookup"><span data-stu-id="4f047-141">v4.0</span></span>|
|<span data-ttu-id="4f047-142">4.7 (4.7.1 ve 4.7.2 dahil)</span><span class="sxs-lookup"><span data-stu-id="4f047-142">4.7 (including 4.7.1 and 4.7.2)</span></span>|<span data-ttu-id="4f047-143">v4.0</span><span class="sxs-lookup"><span data-stu-id="4f047-143">v4.0</span></span>|
|<span data-ttu-id="4f047-144">4.6 (4.6.1 ve 4.6.2 dahil)</span><span class="sxs-lookup"><span data-stu-id="4f047-144">4.6 (including 4.6.1 and 4.6.2)</span></span>|<span data-ttu-id="4f047-145">v4.0</span><span class="sxs-lookup"><span data-stu-id="4f047-145">v4.0</span></span>|
|<span data-ttu-id="4f047-146">4.5 (4.5.1 ve 4.5.2 dahil)</span><span class="sxs-lookup"><span data-stu-id="4f047-146">4.5 (including 4.5.1 and 4.5.2)</span></span>|<span data-ttu-id="4f047-147">v4.0</span><span class="sxs-lookup"><span data-stu-id="4f047-147">v4.0</span></span>|
|<span data-ttu-id="4f047-148">4</span><span class="sxs-lookup"><span data-stu-id="4f047-148">4</span></span>|<span data-ttu-id="4f047-149">v4.0</span><span class="sxs-lookup"><span data-stu-id="4f047-149">v4.0</span></span>|
|<span data-ttu-id="4f047-150">3,5</span><span class="sxs-lookup"><span data-stu-id="4f047-150">3.5</span></span>|<span data-ttu-id="4f047-151">v2.0.50727</span><span class="sxs-lookup"><span data-stu-id="4f047-151">v2.0.50727</span></span>|
|<span data-ttu-id="4f047-152">2,0</span><span class="sxs-lookup"><span data-stu-id="4f047-152">2.0</span></span>|<span data-ttu-id="4f047-153">v2.0.50727</span><span class="sxs-lookup"><span data-stu-id="4f047-153">v2.0.50727</span></span>|
|<span data-ttu-id="4f047-154">1.1</span><span class="sxs-lookup"><span data-stu-id="4f047-154">1.1</span></span>|<span data-ttu-id="4f047-155">v1.1.4322</span><span class="sxs-lookup"><span data-stu-id="4f047-155">v1.1.4322</span></span>|
|<span data-ttu-id="4f047-156">1.0</span><span class="sxs-lookup"><span data-stu-id="4f047-156">1.0</span></span>|<span data-ttu-id="4f047-157">v1.0.3705</span><span class="sxs-lookup"><span data-stu-id="4f047-157">v1.0.3705</span></span>|

## <a name="obsolete-apis-for-net-framework-45-and-later-versions"></a><span data-ttu-id="4f047-158">.NET Framework 4.5 ve sonraki sürümler için eski API'ler</span><span class="sxs-lookup"><span data-stu-id="4f047-158">Obsolete APIs for .NET Framework 4.5 and later versions</span></span>

- [<span data-ttu-id="4f047-159">Eski Türler</span><span class="sxs-lookup"><span data-stu-id="4f047-159">Obsolete Types</span></span>](obsolete-types.md)
- [<span data-ttu-id="4f047-160">Eski Üyeler</span><span class="sxs-lookup"><span data-stu-id="4f047-160">Obsolete Members</span></span>](obsolete-members.md)

## <a name="obsolete-apis-for-previous-versions"></a><span data-ttu-id="4f047-161">Önceki sürümler için eski API'ler</span><span class="sxs-lookup"><span data-stu-id="4f047-161">Obsolete APIs for previous versions</span></span>

- <span data-ttu-id="4f047-162">[.NET Framework 4'te Eski Türler](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ee461503(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="4f047-162">[Obsolete Types in .NET Framework 4](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ee461503(v=vs.100))</span></span>
- <span data-ttu-id="4f047-163">[.NET Framework 4'te Eski Üyeler](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ee471421(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="4f047-163">[Obsolete Members in .NET Framework 4](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ee471421(v=vs.100))</span></span>
- <span data-ttu-id="4f047-164">[.NET Framework 3.5 Eski Liste](https://docs.microsoft.com/previous-versions/cc835481(v=msdn.10))</span><span class="sxs-lookup"><span data-stu-id="4f047-164">[.NET Framework 3.5 Obsolete List](https://docs.microsoft.com/previous-versions/cc835481(v=msdn.10))</span></span>
- <span data-ttu-id="4f047-165">[.NET Framework 2.0 Eski Liste](https://docs.microsoft.com/previous-versions/aa497286(v=msdn.10))</span><span class="sxs-lookup"><span data-stu-id="4f047-165">[.NET Framework 2.0 Obsolete List](https://docs.microsoft.com/previous-versions/aa497286(v=msdn.10))</span></span>

## <a name="see-also"></a><span data-ttu-id="4f047-166">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4f047-166">See also</span></span>

- [<span data-ttu-id="4f047-167">\<desteklenenRuntime> Öğesi</span><span class="sxs-lookup"><span data-stu-id="4f047-167">\<supportedRuntime> Element</span></span>](../configure-apps/file-schema/startup/supportedruntime-element.md)
