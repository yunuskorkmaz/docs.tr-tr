---
title: .NET Framework sınıfı kitaplığındaki kullanım dışı Özellikler
ms.custom: updateeachrelease
ms.date: 04/02/2019
helpviewer_keywords:
- obsolete [.NET Framework]
- what's obsolete [.NET Framework]
- deprecated [.NET Framework]
ms.assetid: d356a43a-73df-4ae2-a457-b9628074c7cd
ms.openlocfilehash: 4de441ff55c3728f43742d6e467deeb47f400507
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140593"
---
# <a name="whats-obsolete-in-the-net-framework-class-library"></a><span data-ttu-id="3adf3-102">.NET Framework sınıfı kitaplığındaki kullanım dışı Özellikler</span><span class="sxs-lookup"><span data-stu-id="3adf3-102">What's obsolete in the .NET Framework class library</span></span>

<span data-ttu-id="3adf3-103">.NET Framework zaman içinde değişir.</span><span class="sxs-lookup"><span data-stu-id="3adf3-103">The .NET Framework changes over time.</span></span> <span data-ttu-id="3adf3-104">Her yeni sürüm yeni türler ve yeni işlevsellik sağlayan tür üyeleri ekler.</span><span class="sxs-lookup"><span data-stu-id="3adf3-104">Each new version adds new types and type members that provide new functionality.</span></span> <span data-ttu-id="3adf3-105">Mevcut türler ve üyeleri zaman içinde de değişir.</span><span class="sxs-lookup"><span data-stu-id="3adf3-105">Existing types and their members also change over time.</span></span> <span data-ttu-id="3adf3-106">Örneğin, destekledikleri teknolojinin yeni bir teknoloji tarafından değiştirildiği ve bazı yöntemlerin yerini daha uygun veya daha fazla tam özellikli olan daha yeni yöntemlerle değiştiren bazı türler daha az önemli hale gelir.</span><span class="sxs-lookup"><span data-stu-id="3adf3-106">For example, some types become less important as the technology they support is replaced by a new technology, and some methods are superseded by newer methods that are either more convenient or more full-featured.</span></span>

<span data-ttu-id="3adf3-107">.NET Framework ve ortak dil çalışma zamanı, geriye dönük uyumluluğu desteklemeye çalışır (.NET Framework bir sürümü ile geliştirilen uygulamaların .NET Framework bir sonraki sürümünde çalıştırılmasına izin verir).</span><span class="sxs-lookup"><span data-stu-id="3adf3-107">The .NET Framework and the common language runtime strive to support backward compatibility (allowing applications that were developed with one version of the .NET Framework to run on the next version of the .NET Framework).</span></span> <span data-ttu-id="3adf3-108">Bu, bir türü veya tür üyesini kaldırmayı zorlaştırır.</span><span class="sxs-lookup"><span data-stu-id="3adf3-108">This makes it difficult to simply remove a type or a type member.</span></span> <span data-ttu-id="3adf3-109">Bunun yerine .NET Framework, bir türün veya bir tür üyesinin artık eski veya kullanım dışı olarak işaretleyerek kullanılmayacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="3adf3-109">Instead, the .NET Framework indicates that a type or a type member should no longer be used by marking it as obsolete or deprecated.</span></span> <span data-ttu-id="3adf3-110">Bir türün veya üyenin kullanım dışı bırakılması, geliştiricilerin göz önünde bulundurulmasını ve kaldırılmasına yanıt vermek için zaman aldığını bilmesini sağlayacak şekilde işaretlemeyi içerir.</span><span class="sxs-lookup"><span data-stu-id="3adf3-110">Deprecating a type or a member involves marking it so that developers are aware it will go away and have time to respond to its removal.</span></span> <span data-ttu-id="3adf3-111">Ancak, türü veya üyeyi kullanan mevcut kod .NET Framework yeni sürümünde çalışmaya devam eder.</span><span class="sxs-lookup"><span data-stu-id="3adf3-111">However, existing code that uses the type or member continues to run in the new version of the .NET Framework.</span></span>

> [!NOTE]
> <span data-ttu-id="3adf3-112">Kullanım dışı *ve* *kullanımdan kaldırılan* koşullar, .NET Framework türlerine ve üyelerine uygulanırken aynı anlama sahiptir.</span><span class="sxs-lookup"><span data-stu-id="3adf3-112">The terms *obsolete* and *deprecated* have the same meaning when applied to the types and members of the .NET Framework.</span></span>

## <a name="the-obsoleteattribute-attribute"></a><span data-ttu-id="3adf3-113">Kullanımdan kaldırma Teattribute özniteliği</span><span class="sxs-lookup"><span data-stu-id="3adf3-113">The ObsoleteAttribute attribute</span></span>

<span data-ttu-id="3adf3-114">.NET Framework, bir tür veya tür üyesinin <xref:System.ObsoleteAttribute> özniteliğiyle işaretlenerek eski olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="3adf3-114">The .NET Framework indicates that a type or type member is obsolete by marking it with the <xref:System.ObsoleteAttribute> attribute.</span></span> <span data-ttu-id="3adf3-115">Özniteliği bir türe veya üyeye uygulamak, türün veya üyenin, bu üyeyi kullanan derlenmiş kodu bozmadan .NET Framework sonraki bir sürümünde kaldırılacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="3adf3-115">Applying the attribute to a type or member indicates that type or member will be removed in some future version of the .NET Framework without breaking compiled code that uses that member.</span></span>

<span data-ttu-id="3adf3-116">Bir türün veya tür üyesinin kullanılmıyor olduğunu belirten ek olarak, <xref:System.ObsoleteAttribute> derleyicinin bu türü veya üyeyi içeren kaynak kodu nasıl işlediğini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3adf3-116">In addition to indicating that a type or a type member is obsolete, <xref:System.ObsoleteAttribute> defines how the compiler handles source code that includes that type or member.</span></span> <span data-ttu-id="3adf3-117">Derleyici kodu derleyebilir, ancak bir uyarı iletisi yayabilir veya bir hata olarak türün veya üyenin kullanımını ele alabilir.</span><span class="sxs-lookup"><span data-stu-id="3adf3-117">The compiler can compile the code but emit a warning message, or it can treat the use of the type or member as an error.</span></span> <span data-ttu-id="3adf3-118">İlk durumda, kod başarıyla derleyebilir, ancak bir uyarı iletisi türün veya üyenin artık kullanılmıyor olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="3adf3-118">In the first case, the code can successfully compile, but a warning message indicates that the type or member is obsolete.</span></span> <span data-ttu-id="3adf3-119">İkinci durumda, derleme başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="3adf3-119">In the second case, compilation fails.</span></span>

<span data-ttu-id="3adf3-120">Derleme bir uyarı iletisi yerine bir hata üretse bile <xref:System.ObsoleteAttribute>, çalışma zamanı davranışını etkilemez.</span><span class="sxs-lookup"><span data-stu-id="3adf3-120">Even if compilation produces an error instead of a warning message, <xref:System.ObsoleteAttribute> does not affect run-time behavior.</span></span> <span data-ttu-id="3adf3-121">Diğer bir deyişle, türü veya üyeyi kullanan ve başarıyla derlenen uygulamalar her zaman başarıyla çalışacaktır.</span><span class="sxs-lookup"><span data-stu-id="3adf3-121">That is, applications that use the type or member and that have compiled successfully will always run successfully.</span></span> <span data-ttu-id="3adf3-122">Yalnızca türü veya üyeyi kullanan bir uygulamayı yeniden derleme girişimi başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="3adf3-122">Only the attempt to recompile an application that uses the type or member fails.</span></span>

## <a name="how-to-handle-obsolete-types-and-members"></a><span data-ttu-id="3adf3-123">Eski türleri ve üyeleri işleme</span><span class="sxs-lookup"><span data-stu-id="3adf3-123">How to handle obsolete types and members</span></span>

<span data-ttu-id="3adf3-124">Mevcut kodu yükselttiğinizde ve yeniden derleyeceğinden, eski bir tür veya uygulamanızda bir derleyici uyarısı üreten bir üyenin kullanılması kusursuz kabul edilebilir.</span><span class="sxs-lookup"><span data-stu-id="3adf3-124">When you upgrade and recompile existing code, using an obsolete type or member that produces a compiler warning in your application is perfectly acceptable.</span></span> <span data-ttu-id="3adf3-125">Ancak, uygulama kodunuzu değiştirip değiştirmeyeceğinizi öğrenmek için derleyici uyarı iletisini gözden geçirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="3adf3-125">However, you should review the compiler warning message to determine whether you should change your application code.</span></span> <span data-ttu-id="3adf3-126">İleti uygun bir alternatifi işaret etmez, aşağıdakilerden birini yapmalısınız:</span><span class="sxs-lookup"><span data-stu-id="3adf3-126">If the message does not point to a suitable alternative, you should do either of the following:</span></span>

- <span data-ttu-id="3adf3-127">Mümkünse, türün veya üyenin kullanımını kaldırarak kodunuzu değiştirin.</span><span class="sxs-lookup"><span data-stu-id="3adf3-127">Change your code by removing the use of the type or member, if possible.</span></span>

     <span data-ttu-id="3adf3-128">veya</span><span class="sxs-lookup"><span data-stu-id="3adf3-128">-or-</span></span>

- <span data-ttu-id="3adf3-129">Kullanımdan kaldırma işlemine nasıl yanıt verileceğini öğrenmek için bu teknoloji alanının belgelerini gözden geçirin.</span><span class="sxs-lookup"><span data-stu-id="3adf3-129">Review the documentation for this technology area to determine how to respond to the deprecation.</span></span>

<span data-ttu-id="3adf3-130">Mevcut kodu .NET Framework sonraki bir sürümüne karşı yeniden derleyemeyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3adf3-130">You may choose not to recompile existing code against a later version of the .NET Framework.</span></span> <span data-ttu-id="3adf3-131">Bunun yerine, mevcut derlenmiş kodunuzun çalıştığı .NET Framework sürümünü belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3adf3-131">Instead, you can specify the version of the .NET Framework against which your existing compiled code runs.</span></span> <span data-ttu-id="3adf3-132">Örneğin, app1. exe adlı ve 3,5 .NET Framework için derlenen bir uygulamanız olduğunu varsayalım, ancak uygulamanın 4,5 .NET Framework karşı çalışmasını istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="3adf3-132">For example, suppose that you have an application named app1.exe that was compiled against the .NET Framework 3.5, but you want the application to run against the .NET Framework 4.5.</span></span> <span data-ttu-id="3adf3-133">Bu, aşağıdaki adımları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="3adf3-133">This requires the following steps:</span></span>

1. <span data-ttu-id="3adf3-134">Ana yürütülebilir dosyanız için bir yapılandırma dosyası oluşturun ve bu dosyayı *appname*. exe. config olarak adlandırın; burada *appname* uygulamanın yürütülebilir dosyasının adıdır.</span><span class="sxs-lookup"><span data-stu-id="3adf3-134">Create a configuration file for your main executable and name it *appName*.exe.config, where *appName* is the name of the application executable.</span></span> <span data-ttu-id="3adf3-135">Örneğimizde app1. exe adlı uygulama için, app1. exe. config adlı bir yapılandırma dosyası oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="3adf3-135">For the application named app1.exe in our example, you would create a configuration file named app1.exe.config.</span></span>

2. <span data-ttu-id="3adf3-136">Yapılandırma dosyasına aşağıdakini ekleyin.</span><span class="sxs-lookup"><span data-stu-id="3adf3-136">Add the following to the configuration file.</span></span>

    ```xml
    <configuration>
       <startup> 
          <supportedRuntime version="v4.0" />
       </startup>
    </configuration>
    ```

<span data-ttu-id="3adf3-137">Aşağıdaki tablo, .NET Framework belirli bir sürümünü hedeflemek için `version` özniteliğine atayabileceğiniz dize değerlerini listeler:</span><span class="sxs-lookup"><span data-stu-id="3adf3-137">The following table lists the string values that you can assign to the `version` attribute to target a specific version of the .NET Framework:</span></span>

|<span data-ttu-id="3adf3-138">.NET Framework sürümü</span><span class="sxs-lookup"><span data-stu-id="3adf3-138">.NET Framework version</span></span>|<span data-ttu-id="3adf3-139">`version` dize</span><span class="sxs-lookup"><span data-stu-id="3adf3-139">`version` string</span></span>|
|-|-|
|<span data-ttu-id="3adf3-140">4,8</span><span class="sxs-lookup"><span data-stu-id="3adf3-140">4.8</span></span>|<span data-ttu-id="3adf3-141">v4.0</span><span class="sxs-lookup"><span data-stu-id="3adf3-141">v4.0</span></span>|
|<span data-ttu-id="3adf3-142">4,7 (4.7.1 ve 4.7.2 dahil)</span><span class="sxs-lookup"><span data-stu-id="3adf3-142">4.7 (including 4.7.1 and 4.7.2)</span></span>|<span data-ttu-id="3adf3-143">v4.0</span><span class="sxs-lookup"><span data-stu-id="3adf3-143">v4.0</span></span>|
|<span data-ttu-id="3adf3-144">4,6 (4.6.1 ve 4.6.2 dahil)</span><span class="sxs-lookup"><span data-stu-id="3adf3-144">4.6 (including 4.6.1 and 4.6.2)</span></span>|<span data-ttu-id="3adf3-145">v4.0</span><span class="sxs-lookup"><span data-stu-id="3adf3-145">v4.0</span></span>|
|<span data-ttu-id="3adf3-146">4,5 (4.5.1 ve 4.5.2 dahil)</span><span class="sxs-lookup"><span data-stu-id="3adf3-146">4.5 (including 4.5.1 and 4.5.2)</span></span>|<span data-ttu-id="3adf3-147">v4.0</span><span class="sxs-lookup"><span data-stu-id="3adf3-147">v4.0</span></span>|
|<span data-ttu-id="3adf3-148">4</span><span class="sxs-lookup"><span data-stu-id="3adf3-148">4</span></span>|<span data-ttu-id="3adf3-149">v4.0</span><span class="sxs-lookup"><span data-stu-id="3adf3-149">v4.0</span></span>|
|<span data-ttu-id="3adf3-150">3.5</span><span class="sxs-lookup"><span data-stu-id="3adf3-150">3.5</span></span>|<span data-ttu-id="3adf3-151">v 2.0.50727</span><span class="sxs-lookup"><span data-stu-id="3adf3-151">v2.0.50727</span></span>|
|<span data-ttu-id="3adf3-152">2,0</span><span class="sxs-lookup"><span data-stu-id="3adf3-152">2.0</span></span>|<span data-ttu-id="3adf3-153">v 2.0.50727</span><span class="sxs-lookup"><span data-stu-id="3adf3-153">v2.0.50727</span></span>|
|<span data-ttu-id="3adf3-154">1.1</span><span class="sxs-lookup"><span data-stu-id="3adf3-154">1.1</span></span>|<span data-ttu-id="3adf3-155">v 1.1.4322</span><span class="sxs-lookup"><span data-stu-id="3adf3-155">v1.1.4322</span></span>|
|<span data-ttu-id="3adf3-156">1.0</span><span class="sxs-lookup"><span data-stu-id="3adf3-156">1.0</span></span>|<span data-ttu-id="3adf3-157">v 1.0.3705</span><span class="sxs-lookup"><span data-stu-id="3adf3-157">v1.0.3705</span></span>|

## <a name="obsolete-lists-for-the-net-framework-45-and-later-versions"></a><span data-ttu-id="3adf3-158">.NET Framework 4,5 ve sonraki sürümleri için eski listeler</span><span class="sxs-lookup"><span data-stu-id="3adf3-158">Obsolete lists for the .NET Framework 4.5 and later versions</span></span>

- [<span data-ttu-id="3adf3-159">Eski Türler</span><span class="sxs-lookup"><span data-stu-id="3adf3-159">Obsolete Types</span></span>](obsolete-types.md)
- [<span data-ttu-id="3adf3-160">Eski Üyeler</span><span class="sxs-lookup"><span data-stu-id="3adf3-160">Obsolete Members</span></span>](obsolete-members.md)

## <a name="obsolete-lists-for-previous-versions"></a><span data-ttu-id="3adf3-161">Önceki sürümler için eski listeler</span><span class="sxs-lookup"><span data-stu-id="3adf3-161">Obsolete lists for previous versions</span></span>

- <span data-ttu-id="3adf3-162">[.NET Framework 4 ' te kullanılmıyor türler](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ee461503(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="3adf3-162">[Obsolete Types in the .NET Framework 4](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ee461503(v=vs.100))</span></span>

- <span data-ttu-id="3adf3-163">[.NET Framework 4 ' te kullanılmayan Üyeler](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ee471421(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="3adf3-163">[Obsolete Members in the .NET Framework 4](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ee471421(v=vs.100))</span></span>

- <span data-ttu-id="3adf3-164">[.NET Framework 3,5 listesi artık kullanılmıyor](https://docs.microsoft.com/previous-versions/cc835481(v=msdn.10))</span><span class="sxs-lookup"><span data-stu-id="3adf3-164">[.NET Framework 3.5 Obsolete List](https://docs.microsoft.com/previous-versions/cc835481(v=msdn.10))</span></span>

- <span data-ttu-id="3adf3-165">[.NET Framework 2,0 listesi artık kullanılmıyor](https://docs.microsoft.com/previous-versions/aa497286(v=msdn.10))</span><span class="sxs-lookup"><span data-stu-id="3adf3-165">[.NET Framework 2.0 Obsolete List](https://docs.microsoft.com/previous-versions/aa497286(v=msdn.10))</span></span>

## <a name="see-also"></a><span data-ttu-id="3adf3-166">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3adf3-166">See also</span></span>

- [<span data-ttu-id="3adf3-167">\<supportedRuntime > öğesi</span><span class="sxs-lookup"><span data-stu-id="3adf3-167">\<supportedRuntime> Element</span></span>](../configure-apps/file-schema/startup/supportedruntime-element.md)
