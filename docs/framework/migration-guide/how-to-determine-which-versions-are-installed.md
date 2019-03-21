---
title: 'Nasıl yapılır: Hangi .NET Framework sürümlerinin yüklü olduğunu belirleme'
ms.date: 03/18/2019
dev_langs:
- csharp
- vb
ms.custom: updateeachrelease
helpviewer_keywords:
- versions, determining for .NET Framework
- .NET Framework, determining version
ms.assetid: 40a67826-e4df-4f59-a651-d9eb0fdc755d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8b7c7704c4f417ef16d3a79fa6d955265e42cf14
ms.sourcegitcommit: e994e47d3582bf09ae487ecbd53c0dac30aebaf7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2019
ms.locfileid: "58262448"
---
# <a name="how-to-determine-which-net-framework-versions-are-installed"></a><span data-ttu-id="3118e-102">Nasıl yapılır: Hangi .NET Framework sürümlerinin yüklü olduğunu belirleme</span><span class="sxs-lookup"><span data-stu-id="3118e-102">How to: Determine which .NET Framework versions are installed</span></span>

<span data-ttu-id="3118e-103">Kullanıcılar [yükleme](https://docs.microsoft.com/dotnet/framework/install) ve .NET Framework'ün birden çok sürümü bilgisayarlarında çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="3118e-103">Users can [install](https://docs.microsoft.com/dotnet/framework/install) and run multiple versions of the .NET Framework on their computers.</span></span> <span data-ttu-id="3118e-104">Geliştirme veya uygulamanızı dağıtma, hangi .NET Framework sürümlerinin kullanıcının bilgisayarında yüklü olduğunu bilmeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="3118e-104">When you develop or deploy your app, you might need to know which .NET Framework versions are installed on the user’s computer.</span></span> 

<span data-ttu-id="3118e-105">.NET Framework, ayrı ayrı uyarlandı iki ana bileşenden, oluşur:</span><span class="sxs-lookup"><span data-stu-id="3118e-105">The .NET Framework consists of two main components, which are versioned separately:</span></span>  
  
- <span data-ttu-id="3118e-106">Koleksiyonları türlerin ve uygulamalarınız için işlevsellik sağlayan kaynaklar derlemelere kümesi.</span><span class="sxs-lookup"><span data-stu-id="3118e-106">A set of assemblies, which are collections of types and resources that provide the functionality for your apps.</span></span> <span data-ttu-id="3118e-107">.NET Framework ve derlemeleri, aynı sürüm numarasını paylaşır.</span><span class="sxs-lookup"><span data-stu-id="3118e-107">The .NET Framework and assemblies share the same version number.</span></span>  
  
- <span data-ttu-id="3118e-108">Yönetir ve uygulamanızın kod yürüten ortak dil çalışma zamanı (CLR).</span><span class="sxs-lookup"><span data-stu-id="3118e-108">The common language runtime (CLR), which manages and executes your app's code.</span></span> <span data-ttu-id="3118e-109">CLR kendi sürüm numarasıyla tanımlanır (bkz [sürümler ve bağımlılıklar](~/docs/framework/migration-guide/versions-and-dependencies.md)).</span><span class="sxs-lookup"><span data-stu-id="3118e-109">The CLR is identified by its own version number (see [Versions and Dependencies](~/docs/framework/migration-guide/versions-and-dependencies.md)).</span></span>  

> [!NOTE]
> <span data-ttu-id="3118e-110">.NET Framework'ün her yeni sürümü önceki sürümlerdeki özellikleri korur ve yeni özellikler ekler.</span><span class="sxs-lookup"><span data-stu-id="3118e-110">Each new version of the .NET Framework retains features from the previous versions and adds new features.</span></span> <span data-ttu-id="3118e-111">Önceki sürümleri kaldırmadan .NET Framework yükleme, yani aynı anda tek bir bilgisayara .NET Framework'ün birden çok sürümü yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3118e-111">You can load multiple versions of the .NET Framework on a single computer at the same time, which means that you can install the .NET Framework without having to uninstall previous versions.</span></span> <span data-ttu-id="3118e-112">Genel olarak, bir uygulama belirli bir sürüme bağlı olabileceği veya o sürüm kaldırılırsa bozulabileceği için .NET Framework'ün önceki sürümlerini kaldırın olmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="3118e-112">In general, you shouldn't uninstall previous versions of the .NET Framework, because an application you use may depend on a specific version and may break if that version is removed.</span></span>
>
> <span data-ttu-id="3118e-113">.NET Framework sürümü ve CLR sürümü arasında bir fark vardır:</span><span class="sxs-lookup"><span data-stu-id="3118e-113">There is a difference between the .NET Framework version and the CLR version:</span></span> 
> - <span data-ttu-id="3118e-114">.NET Framework sürümü .NET Framework sınıf kitaplığı oluşturan derlemeleri kümesini temel alır.</span><span class="sxs-lookup"><span data-stu-id="3118e-114">The .NET Framework version is based on the set of assemblies that form the .NET Framework class library.</span></span> <span data-ttu-id="3118e-115">Örneğin, .NET Framework sürüm 4.5, 4.6.1 ve 4.7.2 içerir.</span><span class="sxs-lookup"><span data-stu-id="3118e-115">For example, .NET Framework versions include 4.5, 4.6.1, and 4.7.2.</span></span> 
>- <span data-ttu-id="3118e-116">CLR sürümü, .NET Framework uygulamaları, üzerinde yürütme çalışma zamanı temel alır.</span><span class="sxs-lookup"><span data-stu-id="3118e-116">The CLR version is based on the runtime on which .NET Framework applications execute.</span></span> <span data-ttu-id="3118e-117">Tek bir CLR sürümü, genellikle birden çok .NET Framework sürümlerini destekler.</span><span class="sxs-lookup"><span data-stu-id="3118e-117">A single CLR version typically supports multiple .NET Framework versions.</span></span> <span data-ttu-id="3118e-118">Örneğin, CLR sürüm 4.0.30319. *xxxxx* 4.5.2 aracılığıyla .NET Framework sürüm 4 ve 4.0.30319.42000 .NET Framework 4. 6'ile başlayan .NET Framework sürümlerini destekleyen CLR sürümünü destekler.</span><span class="sxs-lookup"><span data-stu-id="3118e-118">For example, CLR version 4.0.30319.*xxxxx* supports .NET Framework versions 4 through 4.5.2 and CLR version 4.0.30319.42000 supports .NET Framework versions starting with .NET Framework 4.6.</span></span> 
>
> <span data-ttu-id="3118e-119">Sürümleri hakkında daha fazla bilgi için bkz. [.NET Framework sürümleri ve bağımlılıkları](versions-and-dependencies.md).</span><span class="sxs-lookup"><span data-stu-id="3118e-119">For more information about versions, see [.NET Framework versions and dependencies](versions-and-dependencies.md).</span></span>


<span data-ttu-id="3118e-120">Bir bilgisayarda yüklü .NET Framework sürümlerinin bir listesini almak için kayıt defterine erişim.</span><span class="sxs-lookup"><span data-stu-id="3118e-120">To get a list of the .NET Framework versions installed on a computer, you access the registry.</span></span> <span data-ttu-id="3118e-121">Kayıt defterini veya kodu sorgulamanız için bunu kullanın ya da Kayıt Defteri Düzenleyicisi'ni kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="3118e-121">You can either use the Registry Editor to view the registry or use code to query it:</span></span>
 
- <span data-ttu-id="3118e-122">Yeni bir .NET Framework sürümleri (4.5 ve üzeri) bulun:</span><span class="sxs-lookup"><span data-stu-id="3118e-122">Find newer .NET Framework versions (4.5 and later):</span></span> 
     - [<span data-ttu-id="3118e-123">.NET Framework sürümlerini bulmak için Kayıt Defteri Düzenleyicisi'ni kullanın</span><span class="sxs-lookup"><span data-stu-id="3118e-123">Use the Registry Editor to find .NET Framework versions</span></span>](#net_b)  
     - [<span data-ttu-id="3118e-124">.NET Framework sürümleri için kayıt defterini sorgulayın için kodu kullanın</span><span class="sxs-lookup"><span data-stu-id="3118e-124">Use code to query the registry for .NET Framework versions</span></span>](#net_d)  
     - [<span data-ttu-id="3118e-125">.NET Framework sürümleri için kayıt defterini sorgulayın için PowerShell kullanma</span><span class="sxs-lookup"><span data-stu-id="3118e-125">Use PowerShell to query the registry for .NET Framework versions</span></span>](#ps_a)
 - <span data-ttu-id="3118e-126">Eski .NET Framework sürümlerini bulmak (1&#8211;4):</span><span class="sxs-lookup"><span data-stu-id="3118e-126">Find older .NET Framework versions (1&#8211;4):</span></span>
     - [<span data-ttu-id="3118e-127">.NET Framework sürümlerini bulmak için Kayıt Defteri Düzenleyicisi'ni kullanın</span><span class="sxs-lookup"><span data-stu-id="3118e-127">Use the Registry Editor to find .NET Framework versions</span></span>](#net_a)
     - [<span data-ttu-id="3118e-128">.NET Framework sürümleri için kayıt defterini sorgulayın için kodu kullanın</span><span class="sxs-lookup"><span data-stu-id="3118e-128">Use code to query the registry for .NET Framework versions</span></span>](#net_c)   

<span data-ttu-id="3118e-129">Bir bilgisayarda yüklü CLR sürümlerin listesini almak için bir aracı veya kod kullanın:</span><span class="sxs-lookup"><span data-stu-id="3118e-129">To get a list of the CLR versions installed on a computer, use a tool or code:</span></span>  
  
 - [<span data-ttu-id="3118e-130">Clrver aracını kullanma</span><span class="sxs-lookup"><span data-stu-id="3118e-130">Use the Clrver tool</span></span>](#clr_a)  
 - [<span data-ttu-id="3118e-131">Ortam sınıfını sorgulamak için kodu kullanın.</span><span class="sxs-lookup"><span data-stu-id="3118e-131">Use code to query the Environment class</span></span>](#clr_b)  

<span data-ttu-id="3118e-132">.NET Framework'ün her sürümü için yüklü güncelleştirmeleri algılama hakkında daha fazla bilgi için bkz: [nasıl yapılır: Hangi .NET Framework güncelleştirmelerinin yüklü olduğunu belirleme](how-to-determine-which-net-framework-updates-are-installed.md).</span><span class="sxs-lookup"><span data-stu-id="3118e-132">For information about detecting the installed updates for each version of the .NET Framework, see [How to: Determine which .NET Framework updates are installed](how-to-determine-which-net-framework-updates-are-installed.md).</span></span> 
  

## <a name="find-newer-net-framework-versions-45-and-later"></a><span data-ttu-id="3118e-133">(4.5 ve üzeri) daha yeni .NET Framework sürümlerini bulmak</span><span class="sxs-lookup"><span data-stu-id="3118e-133">Find newer .NET Framework versions (4.5 and later)</span></span>

<a name="net_b"></a> 
### <a name="find-net-framework-versions-45-and-later-in-the-registry"></a><span data-ttu-id="3118e-134">.NET Framework sürüm 4.5 ve sonraki kayıt defterinde bulun</span><span class="sxs-lookup"><span data-stu-id="3118e-134">Find .NET Framework versions 4.5 and later in the registry</span></span>

1. <span data-ttu-id="3118e-135">Gelen **Başlat** menüsünde seçin **çalıştırma**, girin *regedit*ve ardından **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="3118e-135">From the **Start** menu, choose **Run**, enter *regedit*, and then select **OK**.</span></span>

     <span data-ttu-id="3118e-136">Regedit çalıştırmak için yönetici kimlik bilgileriniz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3118e-136">You must have administrative credentials to run regedit.</span></span>

2. <span data-ttu-id="3118e-137">Kayıt Defteri Düzenleyicisi'nde, aşağıdaki alt anahtarı açın: **Hkey_local_machıne\software\microsoft\net Framework Setup\NDP\v4\Full**.</span><span class="sxs-lookup"><span data-stu-id="3118e-137">In the Registry Editor, open the following subkey: **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full**.</span></span> <span data-ttu-id="3118e-138">Varsa **tam** alt hazır değilse, ardından .NET Framework 4.5 yoksa veya sonraki bir sürümü yüklü.</span><span class="sxs-lookup"><span data-stu-id="3118e-138">If the **Full** subkey isn't present, then you don't have the .NET Framework 4.5 or later installed.</span></span>

    > [!NOTE]
    > <span data-ttu-id="3118e-139">**NET Framework Kurulum** klasörünü noktayla başlayan değil.</span><span class="sxs-lookup"><span data-stu-id="3118e-139">The **NET Framework Setup** folder in the registry does not begin with a period.</span></span>

3. <span data-ttu-id="3118e-140">Adlı bir DWORD girişini denetleyin **yayın**.</span><span class="sxs-lookup"><span data-stu-id="3118e-140">Check for a DWORD entry named **Release**.</span></span> <span data-ttu-id="3118e-141">Varsa, ardından, .NET Framework 4.5 veya sonraki bir sürümünün yüklü olması.</span><span class="sxs-lookup"><span data-stu-id="3118e-141">If it exists, then you have .NET Framework 4.5 or later versions installed.</span></span> <span data-ttu-id="3118e-142">Değerini belirli bir .NET Framework sürümüne karşılık gelen bir yayın anahtardır.</span><span class="sxs-lookup"><span data-stu-id="3118e-142">Its value is a release key that corresponds to a particular version of the .NET Framework.</span></span> <span data-ttu-id="3118e-143">Aşağıdaki şekilde, örneğin değerini **yayın** girdidir *378389*, .NET Framework 4.5 için yayın anahtar olduğu.</span><span class="sxs-lookup"><span data-stu-id="3118e-143">In the following figure, for example, the value of the **Release** entry is *378389*, which is the release key for .NET Framework 4.5.</span></span> 

     <span data-ttu-id="3118e-144">![.NET Framework 4.5 için kayıt defteri girişi](media/clr-installdir.png ".NET Framework 4.5 için kayıt defteri girişi")</span><span class="sxs-lookup"><span data-stu-id="3118e-144">![Registry entry for the .NET Framework 4.5](media/clr-installdir.png "Registry entry for the .NET Framework 4.5")</span></span>

<span data-ttu-id="3118e-145">Aşağıdaki tabloda en küçük değerini **yayın** her .NET Framework sürümü için giriş.</span><span class="sxs-lookup"><span data-stu-id="3118e-145">The following table lists the minimum value of the **Release** entry for each .NET Framework version.</span></span> <span data-ttu-id="3118e-146">Bu değerleri şu şekilde kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="3118e-146">You can use these values as follows:</span></span>

- <span data-ttu-id="3118e-147">Bir en düşük .NET Framework sürümü mevcut olup olmadığını belirlemek için test olmadığını **yayın** DWORD değeri kayıt defterinde bulundu *büyüktür veya eşittir* değeri tabloda listelenen.</span><span class="sxs-lookup"><span data-stu-id="3118e-147">To determine whether a minimum .NET Framework version is present, test whether the **Release** DWORD value found in the registry is *greater than or equal to* the value listed in the table.</span></span> <span data-ttu-id="3118e-148">Örneğin, uygulamanız .NET Framework 4.7 veya üzeri gerektiriyorsa, en düşük sürüm anahtar değeri için test *460798*.</span><span class="sxs-lookup"><span data-stu-id="3118e-148">For example, if your application requires the .NET Framework 4.7 or later, you test for a minimum release key value of *460798*.</span></span>

- <span data-ttu-id="3118e-149">Birden çok sürümü için test etmek için en son .NET Framework sürümü ile başlayın ve ardından her art arda gelen önceki sürümü için test.</span><span class="sxs-lookup"><span data-stu-id="3118e-149">To test for multiple versions, begin with the latest .NET Framework version, and then test for each successive earlier version.</span></span>

[!INCLUDE[Release key values note](~/includes/version-keys-note.md)]

<a name="version_table"></a>

|<span data-ttu-id="3118e-150">.NET Framework sürümü</span><span class="sxs-lookup"><span data-stu-id="3118e-150">.NET Framework version</span></span>|<span data-ttu-id="3118e-151">Yayın DWORD değeri</span><span class="sxs-lookup"><span data-stu-id="3118e-151">Value of the Release DWORD</span></span>|
|--------------------------------|-------------|
|<span data-ttu-id="3118e-152">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="3118e-152">.NET Framework 4.5</span></span>|<span data-ttu-id="3118e-153">378389</span><span class="sxs-lookup"><span data-stu-id="3118e-153">378389</span></span>|
|<span data-ttu-id="3118e-154">.NET Framework 4.5.1</span><span class="sxs-lookup"><span data-stu-id="3118e-154">.NET Framework 4.5.1</span></span>|<span data-ttu-id="3118e-155">378675</span><span class="sxs-lookup"><span data-stu-id="3118e-155">378675</span></span>|
|<span data-ttu-id="3118e-156">.NET Framework 4.5.2</span><span class="sxs-lookup"><span data-stu-id="3118e-156">.NET Framework 4.5.2</span></span>|<span data-ttu-id="3118e-157">379893</span><span class="sxs-lookup"><span data-stu-id="3118e-157">379893</span></span>|
|<span data-ttu-id="3118e-158">.NET Framework 4.6</span><span class="sxs-lookup"><span data-stu-id="3118e-158">.NET Framework 4.6</span></span>|<span data-ttu-id="3118e-159">393295</span><span class="sxs-lookup"><span data-stu-id="3118e-159">393295</span></span>|
|<span data-ttu-id="3118e-160">.NET Framework 4.6.1</span><span class="sxs-lookup"><span data-stu-id="3118e-160">.NET Framework 4.6.1</span></span>|<span data-ttu-id="3118e-161">394254</span><span class="sxs-lookup"><span data-stu-id="3118e-161">394254</span></span>|
|<span data-ttu-id="3118e-162">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="3118e-162">.NET Framework 4.6.2</span></span>|<span data-ttu-id="3118e-163">394802</span><span class="sxs-lookup"><span data-stu-id="3118e-163">394802</span></span>|
|<span data-ttu-id="3118e-164">.NET framework 4.7</span><span class="sxs-lookup"><span data-stu-id="3118e-164">.NET Framework 4.7</span></span>|<span data-ttu-id="3118e-165">460798</span><span class="sxs-lookup"><span data-stu-id="3118e-165">460798</span></span>|
|<span data-ttu-id="3118e-166">.NET framework 4.7.1</span><span class="sxs-lookup"><span data-stu-id="3118e-166">.NET Framework 4.7.1</span></span>|<span data-ttu-id="3118e-167">461308</span><span class="sxs-lookup"><span data-stu-id="3118e-167">461308</span></span>|
|<span data-ttu-id="3118e-168">.NET Framework 4.7.2</span><span class="sxs-lookup"><span data-stu-id="3118e-168">.NET Framework 4.7.2</span></span>|<span data-ttu-id="3118e-169">461808</span><span class="sxs-lookup"><span data-stu-id="3118e-169">461808</span></span>|

<span data-ttu-id="3118e-170">.NET Framework belirli Windows işletim sistemi sürümleri için yayın anahtar tam bir tablo için bkz. [.NET Framework sürüm anahtarları ve Windows işletim sistemi sürümleri](release-keys-and-os-versions.md).</span><span class="sxs-lookup"><span data-stu-id="3118e-170">For a complete table of release keys for the .NET Framework for specific Windows operating system versions, see [.NET Framework release keys and Windows operating system versions](release-keys-and-os-versions.md).</span></span>


<a name="net_d"></a> 
### <a name="find-net-framework-versions-45-and-later-with-code"></a><span data-ttu-id="3118e-171">.NET Framework sürüm 4.5 ve sonraki kodu bulun</span><span class="sxs-lookup"><span data-stu-id="3118e-171">Find .NET Framework versions 4.5 and later with code</span></span>

1. <span data-ttu-id="3118e-172">Kullanım <xref:Microsoft.Win32.RegistryKey.OpenBaseKey%2A?displayProperty=nameWithType> ve <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A?displayProperty=nameWithType> erişmek için yöntemleri **hkey_local_machıne\software\microsoft\net Framework Setup\NDP\v4\Full** Windows kayıt defteri alt anahtarı.</span><span class="sxs-lookup"><span data-stu-id="3118e-172">Use the <xref:Microsoft.Win32.RegistryKey.OpenBaseKey%2A?displayProperty=nameWithType> and <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A?displayProperty=nameWithType> methods to access the **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full** subkey in the Windows registry.</span></span>

    <span data-ttu-id="3118e-173">Varlığını **yayın** DWORD girişte **hkey_local_machıne\software\microsoft\net Framework Setup\NDP\v4\Full** alt anahtar, .NET Framework 4.5 veya sonraki bir sürümü olduğunu gösterir bir bilgisayarda yüklü.</span><span class="sxs-lookup"><span data-stu-id="3118e-173">The existence of the **Release** DWORD entry in the **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full** subkey indicates that the .NET Framework 4.5 or a later version is installed on a computer.</span></span> 

2. <span data-ttu-id="3118e-174">Değerini kontrol edin **yayın** yüklenen sürümü belirlemek için giriş.</span><span class="sxs-lookup"><span data-stu-id="3118e-174">Check the value of the **Release** entry to determine the installed version.</span></span> <span data-ttu-id="3118e-175">İleri uyumlu olacak şekilde, daha büyük bir değer olup olmadığını denetleyin veya listelenen değerine eşit [.NET Framework sürüm tablosu](#version_table).</span><span class="sxs-lookup"><span data-stu-id="3118e-175">To be forward-compatible, check for a value greater than or equal to the value listed in the [.NET Framework version table](#version_table).</span></span>

<span data-ttu-id="3118e-176">Aşağıdaki örnek değeri kontrol **yayın** yüklü olan sonraki sürümleri ve .NET Framework 4.5 bulmak için kayıt defteri girişi:</span><span class="sxs-lookup"><span data-stu-id="3118e-176">The following example checks the value of the **Release** entry in the registry to find the .NET Framework 4.5 and later versions that are installed:</span></span>

[!code-csharp[ListVersions#5](../../../samples/snippets/csharp/framework/migration-guide/versions-installed3.cs)]
[!code-vb[ListVersions#5](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed3.vb)]

<span data-ttu-id="3118e-177">Bu örnek, sürüm denetimi için önerilen yöntem aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="3118e-177">This example follows the recommended practice for version checking:</span></span>

- <span data-ttu-id="3118e-178">Denetler olup olmadığını değerini **yayın** girdidir *büyüktür veya eşittir* bilinen yayın anahtar değeri.</span><span class="sxs-lookup"><span data-stu-id="3118e-178">It checks whether the value of the **Release** entry is *greater than or equal to* the value of the known release keys.</span></span>

- <span data-ttu-id="3118e-179">Eski sürümü için en son sürüm sırayla denetler.</span><span class="sxs-lookup"><span data-stu-id="3118e-179">It checks in order from most recent version to earliest version.</span></span>

<a name="ps_a"></a> 
### <a name="check-for-a-minimum-required-net-framework-version-45-and-later-with-powershell"></a><span data-ttu-id="3118e-180">Gereken en düşük .NET Framework sürümünü (4.5 ve üzeri) PowerShell ile denetle</span><span class="sxs-lookup"><span data-stu-id="3118e-180">Check for a minimum-required .NET Framework version (4.5 and later) with PowerShell</span></span>

- <span data-ttu-id="3118e-181">Değerini denetlemek için PowerShell komutlarını kullanın **yayın** girişi **hkey_local_machıne\software\microsoft\net Framework Setup\NDP\v4\Full** alt.</span><span class="sxs-lookup"><span data-stu-id="3118e-181">Use PowerShell commands to check the value of the **Release** entry of the **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full** subkey.</span></span>

<span data-ttu-id="3118e-182">Aşağıdaki örnekler değerini kontrol edin **yayın** belirlemek için giriş olmadığını .NET Framework 4.6.2 veya üzeri yüklü.</span><span class="sxs-lookup"><span data-stu-id="3118e-182">The following examples check the value of the **Release** entry to determine whether the .NET Framework 4.6.2 or later is installed.</span></span> <span data-ttu-id="3118e-183">Bu kodu döndürür `True` yüklüyse ve `False` Aksi takdirde.</span><span class="sxs-lookup"><span data-stu-id="3118e-183">This code returns `True` if it's installed and `False` otherwise.</span></span>

```PowerShell
# PowerShell 5
 Get-ChildItem 'HKLM:\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full\' |  Get-ItemPropertyValue -Name Release | Foreach-Object { $_ -ge 394802 } 
 ```

```PowerShell
# PowerShell 4
(Get-ItemProperty "HKLM:SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full").Release -gt 394802
```

<span data-ttu-id="3118e-184">Bir farklı gereken en düşük .NET Framework sürümü için denetlenecek değiştirin *394802* ile bu örneklerde bir **yayın** değerini [.NET Framework sürüm tablosu](#version_table).</span><span class="sxs-lookup"><span data-stu-id="3118e-184">To check for a different minimum-required .NET Framework version, replace *394802* in these examples with a **Release** value from the [.NET Framework version table](#version_table).</span></span>

## <a name="find-older-net-framework-versions-182114"></a><span data-ttu-id="3118e-185">Eski .NET Framework sürümlerini bulmak (1&#8211;4)</span><span class="sxs-lookup"><span data-stu-id="3118e-185">Find older .NET Framework versions (1&#8211;4)</span></span>

<a name="net_a"></a>
### <a name="find-net-framework-versions-182114-in-the-registry"></a><span data-ttu-id="3118e-186">.NET Framework sürümlerini 1 bulmak&#8211;4'te kayıt defteri</span><span class="sxs-lookup"><span data-stu-id="3118e-186">Find .NET Framework versions 1&#8211;4 in the registry</span></span> 
  
1. <span data-ttu-id="3118e-187">Gelen **Başlat** menüsünde seçin **çalıştırma**, girin *regedit*ve ardından **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="3118e-187">From the **Start** menu, choose **Run**, enter *regedit*, and then select **OK**.</span></span>
  
    <span data-ttu-id="3118e-188">Regedit çalıştırmak için yönetici kimlik bilgileriniz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3118e-188">You must have administrative credentials to run regedit.</span></span>  

2. <span data-ttu-id="3118e-189">Kayıt Defteri Düzenleyicisi'nde, aşağıdaki alt anahtarı açın: **Hkey_local_machıne\software\microsoft\net Framework Setup\NDP**:</span><span class="sxs-lookup"><span data-stu-id="3118e-189">In the Registry Editor, open the following subkey: **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP**:</span></span>  

    - <span data-ttu-id="3118e-190">.NET Framework sürüm 3.5 ile 1.1 yüklü her sürüm alt anahtarı altında listelenir **hkey_local_machıne\software\microsoft\net Framework Setup\NDP** alt.</span><span class="sxs-lookup"><span data-stu-id="3118e-190">For .NET Framework versions 1.1 through 3.5, each installed version is listed as a subkey under the **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP** subkey.</span></span> <span data-ttu-id="3118e-191">Örneğin, **hkey_local_machıne\software\microsoft\net Framework Setup\NDP\v3.5**.</span><span class="sxs-lookup"><span data-stu-id="3118e-191">For example, **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v3.5**.</span></span> <span data-ttu-id="3118e-192">Sürüm numarasını sürümü alt anahtarının değeri olarak depolanan **sürüm** girişi.</span><span class="sxs-lookup"><span data-stu-id="3118e-192">The version number is stored as a value in the version subkey's **Version** entry.</span></span> 
     
    - <span data-ttu-id="3118e-193">.NET Framework 4 için **sürüm** girdidir altında **hkey_local_machıne\software\microsoft\net Framework Setup\NDP\v4.0\Client** alt anahtarı **HKEY_LOCAL_MACHINE\SOFTWARE\ Microsoft\NET Framework Setup\NDP\v4.0\Full** alt anahtar, veya her iki alt altında.</span><span class="sxs-lookup"><span data-stu-id="3118e-193">For .NET Framework 4, the **Version** entry is under the **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4.0\Client** subkey, the **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4.0\Full** subkey, or under both subkeys.</span></span>

    > [!NOTE]
    > <span data-ttu-id="3118e-194">**NET Framework Kurulum** klasörünü noktayla başlayan değil.</span><span class="sxs-lookup"><span data-stu-id="3118e-194">The **NET Framework Setup** folder in the registry does not begin with a period.</span></span>

    <span data-ttu-id="3118e-195">Alt aşağıdaki şekilde gösterilmiştir ve kendi **sürüm** .NET Framework 3.5 için giriş.</span><span class="sxs-lookup"><span data-stu-id="3118e-195">The following figure shows the subkey and its **Version** entry for the .NET Framework 3.5.</span></span>

    <span data-ttu-id="3118e-196">![.NET Framework 3.5 için kayıt defteri girişi. ](media/net-4-and-earlier.png ".NET framework 3.5 ve önceki sürümleri")</span><span class="sxs-lookup"><span data-stu-id="3118e-196">![The registry entry for the .NET Framework 3.5.](media/net-4-and-earlier.png ".NET Framework 3.5 and earlier versions")</span></span>

<a name="net_c"></a> 
### <a name="find-net-framework-versions-182114-with-code"></a><span data-ttu-id="3118e-197">.NET Framework sürümlerini 1 bulmak&#8211;kodla 4</span><span class="sxs-lookup"><span data-stu-id="3118e-197">Find .NET Framework versions 1&#8211;4 with code</span></span>

- <span data-ttu-id="3118e-198">Kullanım <xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType> sınıfı erişimi **hkey_local_machıne\software\microsoft\net Framework Setup\NDP** Windows kayıt defteri alt anahtarı.</span><span class="sxs-lookup"><span data-stu-id="3118e-198">Use the <xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType> class to access the **HKEY_LOCAL_MACHINE\Software\Microsoft\NET Framework Setup\NDP** subkey in the Windows registry.</span></span>

<span data-ttu-id="3118e-199">Aşağıdaki örnek, .NET Framework 1 bulur&#8211;yüklü olan 4 sürümleri:</span><span class="sxs-lookup"><span data-stu-id="3118e-199">The following example finds the .NET Framework 1&#8211;4 versions that are installed:</span></span>

[!code-csharp[ListVersions](../../../samples/snippets/csharp/framework/migration-guide/versions-installed1.cs)]
[!code-vb[ListVersions](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed1.vb)]


## <a name="find-clr-versions"></a><span data-ttu-id="3118e-200">CLR sürümleri bulun</span><span class="sxs-lookup"><span data-stu-id="3118e-200">Find CLR versions</span></span>
  
<a name="clr_a"></a> 
### <a name="find-the-current-clr-version-with-clrverexe"></a><span data-ttu-id="3118e-201">Clrver.exe geçerli CLR sürümüyle Bul</span><span class="sxs-lookup"><span data-stu-id="3118e-201">Find the current CLR version with Clrver.exe</span></span>

<span data-ttu-id="3118e-202">Kullanım [CLR sürüm Aracı (Clrver.exe)](../tools/clrver-exe-clr-version-tool.md) CLR'ın hangi sürümleri bir bilgisayarda yüklü olduğunu saptamak için:</span><span class="sxs-lookup"><span data-stu-id="3118e-202">Use the [CLR Version tool (Clrver.exe)](../tools/clrver-exe-clr-version-tool.md) to determine which versions of the CLR are installed on a computer:</span></span>

- <span data-ttu-id="3118e-203">Gelen bir [Visual Studio için geliştirici komut istemi](https://docs.microsoft.com/dotnet/framework/tools/developer-command-prompt-for-vs), girin `clrver`.</span><span class="sxs-lookup"><span data-stu-id="3118e-203">From a [Developer Command Prompt for Visual Studio](https://docs.microsoft.com/dotnet/framework/tools/developer-command-prompt-for-vs), enter `clrver`.</span></span>

    <span data-ttu-id="3118e-204">Örnek çıktı:</span><span class="sxs-lookup"><span data-stu-id="3118e-204">Sample output:</span></span>

    ```console
    Versions installed on the machine:
    v2.0.50727
    v4.0.30319
    ```

<a name="clr_b"></a> 
### <a name="find-the-current-clr-version-with-the-environment-class"></a><span data-ttu-id="3118e-205">Geçerli ortam sınıfını CLR sürümüyle Bul</span><span class="sxs-lookup"><span data-stu-id="3118e-205">Find the current CLR version with the Environment class</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3118e-206">.NET Framework 4.5 ve sonraki sürümler için kullanmadığınız <xref:System.Environment.Version%2A?displayProperty=nameWithType> özelliği CLR sürümünü algılayamaz.</span><span class="sxs-lookup"><span data-stu-id="3118e-206">For the .NET Framework 4.5 and later versions, don't use the <xref:System.Environment.Version%2A?displayProperty=nameWithType> property to detect the version of the CLR.</span></span> <span data-ttu-id="3118e-207">Bunun yerine, açıklanan şekilde kayıt defterini sorgulayın [Bul .NET Framework sürüm 4.5 ve sonraki kod ile](#net_d).</span><span class="sxs-lookup"><span data-stu-id="3118e-207">Instead, query the registry as described in [Find .NET Framework versions 4.5 and later with code](#net_d).</span></span>

1. <span data-ttu-id="3118e-208">Sorgu <xref:System.Environment.Version?displayProperty=nameWithType> almak için özellik bir <xref:System.Version> nesne.</span><span class="sxs-lookup"><span data-stu-id="3118e-208">Query the <xref:System.Environment.Version?displayProperty=nameWithType> property to retrieve a <xref:System.Version> object.</span></span> 

    <span data-ttu-id="3118e-209">Döndürülen `System.Version` nesne şu anda kodu yürüten çalışma zamanının sürümünü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3118e-209">The returned `System.Version` object identifies the version of the runtime that's currently executing the code.</span></span> <span data-ttu-id="3118e-210">Derleme sürümlerini ya da diğer sürümleri bilgisayarda yüklü çalışma zamanı döndürmüyor.</span><span class="sxs-lookup"><span data-stu-id="3118e-210">It doesn't return assembly versions or other versions of the runtime that may have been installed on the computer.</span></span>

    <span data-ttu-id="3118e-211">.NET Framework sürüm 4, 4.5, 4.5.1 ve 4.5.2'yi, döndürülen dize gösterimi için <xref:System.Version> nenesindeki formun 4.0.30319. *xxxxx*.</span><span class="sxs-lookup"><span data-stu-id="3118e-211">For the .NET Framework versions 4, 4.5, 4.5.1, and 4.5.2, the string representation of the returned <xref:System.Version> object has the form 4.0.30319.*xxxxx*.</span></span> <span data-ttu-id="3118e-212">.NET Framework 4.6 ve sonraki sürümler için formun 4.0.30319.42000 sahiptir.</span><span class="sxs-lookup"><span data-stu-id="3118e-212">For the .NET Framework 4.6 and later versions, it has the form 4.0.30319.42000.</span></span>    

2. <span data-ttu-id="3118e-213">Sonra `Version` nesne, şu şekilde sorgulayın:</span><span class="sxs-lookup"><span data-stu-id="3118e-213">After you have the `Version` object, query it as follows:</span></span>

   - <span data-ttu-id="3118e-214">Tanımlayıcı için ana sürüm (örneğin, *4* sürüm 4.0 için), kullanın <xref:System.Version.Major%2A?displayProperty=nameWithType> özelliği.</span><span class="sxs-lookup"><span data-stu-id="3118e-214">For the major release identifier (for example, *4* for version 4.0), use the <xref:System.Version.Major%2A?displayProperty=nameWithType> property.</span></span>

   - <span data-ttu-id="3118e-215">Tanımlayıcı için ikincil sürüm (örneğin, *0* sürüm 4.0 için), kullanın <xref:System.Version.Minor%2A?displayProperty=nameWithType> özelliği.</span><span class="sxs-lookup"><span data-stu-id="3118e-215">For the minor release identifier (for example, *0* for version 4.0), use the <xref:System.Version.Minor%2A?displayProperty=nameWithType> property.</span></span>

   - <span data-ttu-id="3118e-216">İçin tüm sürüm dizesini (örneğin, *4.0.30319.18010*), kullanın <xref:System.Version.ToString%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="3118e-216">For the entire version string (for example, *4.0.30319.18010*), use the <xref:System.Version.ToString%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="3118e-217">Bu yöntem, kodu yürüten çalışma zamanının sürümünü gösteren tek bir değer döndürür.</span><span class="sxs-lookup"><span data-stu-id="3118e-217">This method returns a single value that reflects the version of the runtime that's executing the code.</span></span> <span data-ttu-id="3118e-218">Derleme sürümlerini veya bilgisayarda yüklü diğer çalışma zamanı sürümleri döndürmez.</span><span class="sxs-lookup"><span data-stu-id="3118e-218">It doesn't return assembly versions or other runtime versions that may be installed on the computer.</span></span>



<span data-ttu-id="3118e-219">Aşağıdaki örnekte <xref:System.Environment.Version%2A?displayProperty=nameWithType> CLR sürümü bilgisini almak için özellik:</span><span class="sxs-lookup"><span data-stu-id="3118e-219">The following example uses the <xref:System.Environment.Version%2A?displayProperty=nameWithType> property to retrieve CLR version information:</span></span>

[!code-csharp[ListVersions](../../../samples/snippets/csharp/framework/migration-guide/versions-installed2.cs)]
[!code-vb[ListVersions](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed2.vb)]

## <a name="see-also"></a><span data-ttu-id="3118e-220">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3118e-220">See also</span></span>

- [<span data-ttu-id="3118e-221">Nasıl yapılır: Hangi .NET Framework güncelleştirmelerinin yüklü olduğunu belirleme</span><span class="sxs-lookup"><span data-stu-id="3118e-221">How to: Determine which .NET Framework updates are installed</span></span>](how-to-determine-which-net-framework-updates-are-installed.md)
- [<span data-ttu-id="3118e-222">Geliştiriciler için .NET Framework'ü yükleme</span><span class="sxs-lookup"><span data-stu-id="3118e-222">Install the .NET Framework for developers</span></span>](../install/guide-for-developers.md)
- [<span data-ttu-id="3118e-223">.NET framework sürümleri ve bağımlılıkları</span><span class="sxs-lookup"><span data-stu-id="3118e-223">.NET Framework versions and dependencies</span></span>](versions-and-dependencies.md)
