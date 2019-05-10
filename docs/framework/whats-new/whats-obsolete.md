---
title: .NET Framework Sınıf Kitaplığı'nda eski nedir
ms.custom: updateeachrelease
ms.date: 04/02/2019
helpviewer_keywords:
- obsolete [.NET Framework]
- what's obsolete [.NET Framework]
- deprecated [.NET Framework]
ms.assetid: d356a43a-73df-4ae2-a457-b9628074c7cd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d7315768c8f81795fa334ba2fcc6d65084844627
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64649414"
---
# <a name="whats-obsolete-in-the-net-framework-class-library"></a><span data-ttu-id="42c96-102">.NET Framework sınıf kitaplığında artık Kullanılmayanlar</span><span class="sxs-lookup"><span data-stu-id="42c96-102">What's obsolete in the .NET Framework class library</span></span>

<span data-ttu-id="42c96-103">.NET Framework, zaman içinde değişir.</span><span class="sxs-lookup"><span data-stu-id="42c96-103">The .NET Framework changes over time.</span></span> <span data-ttu-id="42c96-104">Her yeni sürümü, yeni türler ve yeni işlevleri sağlayan bir tür üyeleri ekler.</span><span class="sxs-lookup"><span data-stu-id="42c96-104">Each new version adds new types and type members that provide new functionality.</span></span> <span data-ttu-id="42c96-105">Ayrıca varolan türleri ve üyeleri zamanla değişir.</span><span class="sxs-lookup"><span data-stu-id="42c96-105">Existing types and their members also change over time.</span></span> <span data-ttu-id="42c96-106">Örneğin, bazı türleri destekledikleri teknoloji tarafından yeni bir teknoloji değiştirilir daha az önemli hale gelir ve bazı yöntemler daha kullanışlı ya da daha tam özellikli olan yeni yöntemlerle olandır.</span><span class="sxs-lookup"><span data-stu-id="42c96-106">For example, some types become less important as the technology they support is replaced by a new technology, and some methods are superseded by newer methods that are either more convenient or more full-featured.</span></span>

<span data-ttu-id="42c96-107">.NET Framework ve ortak dil çalışma zamanı desteği (bir .NET Framework'ün sonraki sürüm üzerinde çalıştırmak için .NET Framework sürümü ile geliştirilen uygulamaları olanak tanır) geriye dönük uyumluluk çaba harcar.</span><span class="sxs-lookup"><span data-stu-id="42c96-107">The .NET Framework and the common language runtime strive to support backward compatibility (allowing applications that were developed with one version of the .NET Framework to run on the next version of the .NET Framework).</span></span> <span data-ttu-id="42c96-108">Bu, yalnızca bir tür veya tür üyesi kaldırmak zorlaştırır.</span><span class="sxs-lookup"><span data-stu-id="42c96-108">This makes it difficult to simply remove a type or a type member.</span></span> <span data-ttu-id="42c96-109">Bunun yerine, .NET Framework türü veya tür üyesi artık kullanılmayan veya kullanım dışı olarak işaretleyerek kullanılması gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="42c96-109">Instead, the .NET Framework indicates that a type or a type member should no longer be used by marking it as obsolete or deprecated.</span></span> <span data-ttu-id="42c96-110">Bir tür veya üye kullanım dışı bırakılıyor, böylece geliştiriciler, kaybolur ve yanıtlamak için bunun kaldırılması için zamanınız farkında İmleme içerir.</span><span class="sxs-lookup"><span data-stu-id="42c96-110">Deprecating a type or a member involves marking it so that developers are aware it will go away and have time to respond to its removal.</span></span> <span data-ttu-id="42c96-111">Ancak, türe veya üyeye kullanan mevcut kodu .NET Framework'ün yeni sürümde çalışmaya devam eder.</span><span class="sxs-lookup"><span data-stu-id="42c96-111">However, existing code that uses the type or member continues to run in the new version of the .NET Framework.</span></span>

> [!NOTE]
> <span data-ttu-id="42c96-112">Koşulları *eski* ve *kullanım dışı* türleri ve üyeleri .NET Framework'ün uygulandığında anlamı yoktur.</span><span class="sxs-lookup"><span data-stu-id="42c96-112">The terms *obsolete* and *deprecated* have the same meaning when applied to the types and members of the .NET Framework.</span></span>

## <a name="the-obsoleteattribute-attribute"></a><span data-ttu-id="42c96-113">ObsoleteAttribute özniteliği</span><span class="sxs-lookup"><span data-stu-id="42c96-113">The ObsoleteAttribute attribute</span></span>

<span data-ttu-id="42c96-114">.NET Framework tür veya üyenin türü ile işaretleyerek eski gösterir <xref:System.ObsoleteAttribute> özniteliği.</span><span class="sxs-lookup"><span data-stu-id="42c96-114">The .NET Framework indicates that a type or type member is obsolete by marking it with the <xref:System.ObsoleteAttribute> attribute.</span></span> <span data-ttu-id="42c96-115">Öznitelik bir türe veya üyeye uygulama .NET Framework bu üyeyi kullanan son derlenen kod olmadan bazı gelecek sürümünde türe veya üyeye kaldırılacak gösterir.</span><span class="sxs-lookup"><span data-stu-id="42c96-115">Applying the attribute to a type or member indicates that type or member will be removed in some future version of the .NET Framework without breaking compiled code that uses that member.</span></span>

<span data-ttu-id="42c96-116">Bir tür veya tür üye eski olduğunu belirten ek olarak <xref:System.ObsoleteAttribute> derleyici bu tür veya üye içeren kaynak kodu nasıl işlediğini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="42c96-116">In addition to indicating that a type or a type member is obsolete, <xref:System.ObsoleteAttribute> defines how the compiler handles source code that includes that type or member.</span></span> <span data-ttu-id="42c96-117">Derleyici, kodu derlemek ancak bir uyarı iletisi yayma ya da hata olarak türe veya üyeye kullanımını davranabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="42c96-117">The compiler can compile the code but emit a warning message, or it can treat the use of the type or member as an error.</span></span> <span data-ttu-id="42c96-118">İlk durumda, kod başarıyla derleme, ancak bir uyarı iletisi türe veya üyeye geçersiz olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="42c96-118">In the first case, the code can successfully compile, but a warning message indicates that the type or member is obsolete.</span></span> <span data-ttu-id="42c96-119">İkinci durumda, derleme başarısız oluyor.</span><span class="sxs-lookup"><span data-stu-id="42c96-119">In the second case, compilation fails.</span></span>

<span data-ttu-id="42c96-120">Derleme hata yerine bir uyarı iletisi üretse <xref:System.ObsoleteAttribute> çalışma zamanı davranışını etkilemez.</span><span class="sxs-lookup"><span data-stu-id="42c96-120">Even if compilation produces an error instead of a warning message, <xref:System.ObsoleteAttribute> does not affect run-time behavior.</span></span> <span data-ttu-id="42c96-121">Diğer bir deyişle, türe veya üyeye kullanan ve başarıyla derlediğiniz uygulamalar her zaman başarılı bir şekilde çalışır.</span><span class="sxs-lookup"><span data-stu-id="42c96-121">That is, applications that use the type or member and that have compiled successfully will always run successfully.</span></span> <span data-ttu-id="42c96-122">Yalnızca türe veya üyeye kullanan bir uygulamayı yeniden derle denemesi başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="42c96-122">Only the attempt to recompile an application that uses the type or member fails.</span></span>

## <a name="how-to-handle-obsolete-types-and-members"></a><span data-ttu-id="42c96-123">Kullanılmayan türlerin ve üyelerin nasıl ele alınacağını</span><span class="sxs-lookup"><span data-stu-id="42c96-123">How to handle obsolete types and members</span></span>

<span data-ttu-id="42c96-124">Yükseltme ve mevcut kodu yeniden derlemeniz, bir eski türü veya uygulamanızdaki bir derleyici uyarısı üreten üye edilebilir kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="42c96-124">When you upgrade and recompile existing code, using an obsolete type or member that produces a compiler warning in your application is perfectly acceptable.</span></span> <span data-ttu-id="42c96-125">Ancak, uygulama kodunuzu değiştirmeniz olup olmadığını belirlemek için derleyici uyarı iletisini gözden geçirmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="42c96-125">However, you should review the compiler warning message to determine whether you should change your application code.</span></span> <span data-ttu-id="42c96-126">İleti için uygun bir alternatif işaret etmiyorsa, aşağıdakilerden birini yapmalısınız:</span><span class="sxs-lookup"><span data-stu-id="42c96-126">If the message does not point to a suitable alternative, you should do either of the following:</span></span>

- <span data-ttu-id="42c96-127">Türe veya üyeye, kullanımını mümkünse kaldırarak kodunuzu değiştirin.</span><span class="sxs-lookup"><span data-stu-id="42c96-127">Change your code by removing the use of the type or member, if possible.</span></span>

     <span data-ttu-id="42c96-128">-veya-</span><span class="sxs-lookup"><span data-stu-id="42c96-128">-or-</span></span>

- <span data-ttu-id="42c96-129">Nasıl için kullanımdan kaldırılma yanıtlanacağını belirlemek bu teknoloji alanı için belgeleri gözden geçirin.</span><span class="sxs-lookup"><span data-stu-id="42c96-129">Review the documentation for this technology area to determine how to respond to the deprecation.</span></span>

<span data-ttu-id="42c96-130">.NET Framework'ün daha sonraki bir sürüme karşı mevcut kodu yeniden derlemeniz değil tercih edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="42c96-130">You may choose not to recompile existing code against a later version of the .NET Framework.</span></span> <span data-ttu-id="42c96-131">Bunun yerine, karşı mevcut kodu çalıştırır derlenmiş .NET Framework sürümünü belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="42c96-131">Instead, you can specify the version of the .NET Framework against which your existing compiled code runs.</span></span> <span data-ttu-id="42c96-132">Örneğin, karşı derlenen app1.exe adlı bir uygulama olduğunu varsayın [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)], ancak uygulamayı karşı çalıştırmak istediğiniz [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].</span><span class="sxs-lookup"><span data-stu-id="42c96-132">For example, suppose that you have an application named app1.exe that was compiled against the [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)], but you want the application to run against the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].</span></span> <span data-ttu-id="42c96-133">Bu, aşağıdaki adımları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="42c96-133">This requires the following steps:</span></span>

1. <span data-ttu-id="42c96-134">Ana, yürütülebilir dosya için bir yapılandırma dosyası oluşturun ve adlandırın *appName*. exe.config olarak, burada *appName* uygulama yürütülebilir adıdır.</span><span class="sxs-lookup"><span data-stu-id="42c96-134">Create a configuration file for your main executable and name it *appName*.exe.config, where *appName* is the name of the application executable.</span></span> <span data-ttu-id="42c96-135">Bizim örneğimizde App1.exe adlı uygulama için app1.exe.config adlı bir yapılandırma dosyası oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="42c96-135">For the application named app1.exe in our example, you would create a configuration file named app1.exe.config.</span></span>

2. <span data-ttu-id="42c96-136">Aşağıdaki yapılandırma dosyasına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="42c96-136">Add the following to the configuration file.</span></span>

    ```xml
    <configuration>
       <startup> 
          <supportedRuntime version="v4.0" />
       </startup>
    </configuration>
    ```

<span data-ttu-id="42c96-137">Aşağıdaki tablo, atayabileceğiniz dize değerleri listeler `version` belirli bir .NET Framework sürümünü hedefleyecek şekilde özniteliği:</span><span class="sxs-lookup"><span data-stu-id="42c96-137">The following table lists the string values that you can assign to the `version` attribute to target a specific version of the .NET Framework:</span></span>

|<span data-ttu-id="42c96-138">.NET Framework sürümü</span><span class="sxs-lookup"><span data-stu-id="42c96-138">.NET Framework version</span></span>|<span data-ttu-id="42c96-139">`version` dize</span><span class="sxs-lookup"><span data-stu-id="42c96-139">`version` string</span></span>|
|-|-|
|<span data-ttu-id="42c96-140">4.8</span><span class="sxs-lookup"><span data-stu-id="42c96-140">4.8</span></span>|<span data-ttu-id="42c96-141">v4.0</span><span class="sxs-lookup"><span data-stu-id="42c96-141">v4.0</span></span>|
|<span data-ttu-id="42c96-142">4.7 (4.7.1 ve 4.7.2 dahil)</span><span class="sxs-lookup"><span data-stu-id="42c96-142">4.7 (including 4.7.1 and 4.7.2)</span></span>|<span data-ttu-id="42c96-143">v4.0</span><span class="sxs-lookup"><span data-stu-id="42c96-143">v4.0</span></span>|
|<span data-ttu-id="42c96-144">4.6 (4.6.1 ve 4.6.2 dahil)</span><span class="sxs-lookup"><span data-stu-id="42c96-144">4.6 (including 4.6.1 and 4.6.2)</span></span>|<span data-ttu-id="42c96-145">v4.0</span><span class="sxs-lookup"><span data-stu-id="42c96-145">v4.0</span></span>|
|<span data-ttu-id="42c96-146">4.5 (4.5.1 ve 4.5.2'yi dahil)</span><span class="sxs-lookup"><span data-stu-id="42c96-146">4.5 (including 4.5.1 and 4.5.2)</span></span>|<span data-ttu-id="42c96-147">v4.0</span><span class="sxs-lookup"><span data-stu-id="42c96-147">v4.0</span></span>|
|<span data-ttu-id="42c96-148">4</span><span class="sxs-lookup"><span data-stu-id="42c96-148">4</span></span>|<span data-ttu-id="42c96-149">v4.0</span><span class="sxs-lookup"><span data-stu-id="42c96-149">v4.0</span></span>|
|<span data-ttu-id="42c96-150">3.5</span><span class="sxs-lookup"><span data-stu-id="42c96-150">3.5</span></span>|<span data-ttu-id="42c96-151">v2.0.50727</span><span class="sxs-lookup"><span data-stu-id="42c96-151">v2.0.50727</span></span>|
|<span data-ttu-id="42c96-152">2,0</span><span class="sxs-lookup"><span data-stu-id="42c96-152">2.0</span></span>|<span data-ttu-id="42c96-153">v2.0.50727</span><span class="sxs-lookup"><span data-stu-id="42c96-153">v2.0.50727</span></span>|
|<span data-ttu-id="42c96-154">1.1</span><span class="sxs-lookup"><span data-stu-id="42c96-154">1.1</span></span>|<span data-ttu-id="42c96-155">v1.1.4322</span><span class="sxs-lookup"><span data-stu-id="42c96-155">v1.1.4322</span></span>|
|<span data-ttu-id="42c96-156">1.0</span><span class="sxs-lookup"><span data-stu-id="42c96-156">1.0</span></span>|<span data-ttu-id="42c96-157">v1.0.3705</span><span class="sxs-lookup"><span data-stu-id="42c96-157">v1.0.3705</span></span>|

## <a name="obsolete-lists-for-the-net-framework-45-and-later-versions"></a><span data-ttu-id="42c96-158">.NET Framework 4.5 ve sonraki sürümler için eski listeleri</span><span class="sxs-lookup"><span data-stu-id="42c96-158">Obsolete lists for the .NET Framework 4.5 and later versions</span></span>

- [<span data-ttu-id="42c96-159">Eski Türler</span><span class="sxs-lookup"><span data-stu-id="42c96-159">Obsolete Types</span></span>](obsolete-types.md)
- [<span data-ttu-id="42c96-160">Eski Üyeler</span><span class="sxs-lookup"><span data-stu-id="42c96-160">Obsolete Members</span></span>](obsolete-members.md)

## <a name="obsolete-lists-for-previous-versions"></a><span data-ttu-id="42c96-161">Önceki sürümler için eski listeler</span><span class="sxs-lookup"><span data-stu-id="42c96-161">Obsolete lists for previous versions</span></span>

- <span data-ttu-id="42c96-162">[.NET Framework 4 içinde eski türler](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ee461503(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="42c96-162">[Obsolete Types in the .NET Framework 4](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ee461503(v=vs.100))</span></span>

- <span data-ttu-id="42c96-163">[.NET Framework 4 içinde eski üyeler](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ee471421(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="42c96-163">[Obsolete Members in the .NET Framework 4](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ee471421(v=vs.100))</span></span>

- <span data-ttu-id="42c96-164">[.NET framework 3.5 eski listesi](https://docs.microsoft.com/previous-versions/cc835481(v=msdn.10))</span><span class="sxs-lookup"><span data-stu-id="42c96-164">[.NET Framework 3.5 Obsolete List](https://docs.microsoft.com/previous-versions/cc835481(v=msdn.10))</span></span>

- <span data-ttu-id="42c96-165">[.NET framework 2.0 eski listesi](https://docs.microsoft.com/previous-versions/aa497286(v=msdn.10))</span><span class="sxs-lookup"><span data-stu-id="42c96-165">[.NET Framework 2.0 Obsolete List](https://docs.microsoft.com/previous-versions/aa497286(v=msdn.10))</span></span>

## <a name="see-also"></a><span data-ttu-id="42c96-166">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="42c96-166">See also</span></span>

- [<span data-ttu-id="42c96-167">\<supportedRuntime > öğesi</span><span class="sxs-lookup"><span data-stu-id="42c96-167">\<supportedRuntime> Element</span></span>](../configure-apps/file-schema/startup/supportedruntime-element.md)