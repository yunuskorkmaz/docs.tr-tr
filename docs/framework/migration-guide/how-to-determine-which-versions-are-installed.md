---
title: 'Nasıl yapılır: hangi .NET Framework sürümlerinin yüklendiğini belirleme'
ms.date: 04/18/2019
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
ms.openlocfilehash: abfa42be4b8c759da3fb34a2204058143e39689c
ms.sourcegitcommit: 7bfe1682d9368cf88d43e895d1e80ba2d88c3a99
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/04/2019
ms.locfileid: "71956664"
---
# <a name="how-to-determine-which-net-framework-versions-are-installed"></a><span data-ttu-id="59761-102">Nasıl yapılır: hangi .NET Framework sürümlerinin yüklendiğini belirleme</span><span class="sxs-lookup"><span data-stu-id="59761-102">How to: Determine which .NET Framework versions are installed</span></span>

<span data-ttu-id="59761-103">Kullanıcılar bilgisayarlarına .NET Framework birden çok sürümünü [yükleyebilir](https://docs.microsoft.com/dotnet/framework/install) ve çalıştırabilir.</span><span class="sxs-lookup"><span data-stu-id="59761-103">Users can [install](https://docs.microsoft.com/dotnet/framework/install) and run multiple versions of the .NET Framework on their computers.</span></span> <span data-ttu-id="59761-104">Uygulamanızı geliştirirken veya dağıtırken, kullanıcının bilgisayarında hangi .NET Framework sürümlerinin yüklü olduğunu bilmeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="59761-104">When you develop or deploy your app, you might need to know which .NET Framework versions are installed on the user’s computer.</span></span>

<span data-ttu-id="59761-105">.NET Framework, sürümü ayrı olan iki ana bileşenden oluşur:</span><span class="sxs-lookup"><span data-stu-id="59761-105">The .NET Framework consists of two main components, which are versioned separately:</span></span>

- <span data-ttu-id="59761-106">Uygulamalarınız için işlevsellik sağlayan tür ve kaynak koleksiyonları olan derlemeler kümesi.</span><span class="sxs-lookup"><span data-stu-id="59761-106">A set of assemblies, which are collections of types and resources that provide the functionality for your apps.</span></span> <span data-ttu-id="59761-107">.NET Framework ve derlemeler aynı sürüm numarasını paylaşır.</span><span class="sxs-lookup"><span data-stu-id="59761-107">The .NET Framework and assemblies share the same version number.</span></span>

- <span data-ttu-id="59761-108">Uygulamanızın kodunu yöneten ve yürüten ortak dil çalışma zamanı (CLR).</span><span class="sxs-lookup"><span data-stu-id="59761-108">The common language runtime (CLR), which manages and executes your app's code.</span></span> <span data-ttu-id="59761-109">CLR kendi sürüm numarasıyla tanımlanır (bkz. [sürümler ve bağımlılıklar](versions-and-dependencies.md)).</span><span class="sxs-lookup"><span data-stu-id="59761-109">The CLR is identified by its own version number (see [Versions and Dependencies](versions-and-dependencies.md)).</span></span>

> [!NOTE]
> <span data-ttu-id="59761-110">.NET Framework'ün her yeni sürümü önceki sürümlerdeki özellikleri korur ve yeni özellikler ekler.</span><span class="sxs-lookup"><span data-stu-id="59761-110">Each new version of the .NET Framework retains features from the previous versions and adds new features.</span></span> <span data-ttu-id="59761-111">.NET Framework birden çok sürümünü aynı anda tek bir bilgisayara yükleyebilirsiniz; Yani, önceki sürümleri kaldırmak zorunda kalmadan .NET Framework yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="59761-111">You can load multiple versions of the .NET Framework on a single computer at the same time, which means that you can install the .NET Framework without having to uninstall previous versions.</span></span> <span data-ttu-id="59761-112">Genel olarak, kullandığınız bir uygulama belirli bir sürüme bağlı olabileceğinden ve bu sürüm kaldırılırsa kesintiye uğraabileceğinden, .NET Framework önceki sürümlerini kaldırmamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="59761-112">In general, you shouldn't uninstall previous versions of the .NET Framework, because an application you use may depend on a specific version and may break if that version is removed.</span></span>
>
> <span data-ttu-id="59761-113">.NET Framework sürümü ile CLR sürümü arasında bir fark vardır:</span><span class="sxs-lookup"><span data-stu-id="59761-113">There is a difference between the .NET Framework version and the CLR version:</span></span>
>
> - <span data-ttu-id="59761-114">.NET Framework sürümü, .NET Framework sınıf kitaplığını oluşturan derlemeler kümesini temel alır.</span><span class="sxs-lookup"><span data-stu-id="59761-114">The .NET Framework version is based on the set of assemblies that form the .NET Framework class library.</span></span> <span data-ttu-id="59761-115">Örneğin, .NET Framework sürümler 4,5, 4.6.1 ve 4.7.2 ' i içerir.</span><span class="sxs-lookup"><span data-stu-id="59761-115">For example, .NET Framework versions include 4.5, 4.6.1, and 4.7.2.</span></span>
>- <span data-ttu-id="59761-116">CLR sürümü .NET Framework uygulamalarının çalıştırıldığı çalışma zamanına dayalıdır.</span><span class="sxs-lookup"><span data-stu-id="59761-116">The CLR version is based on the runtime on which .NET Framework applications execute.</span></span> <span data-ttu-id="59761-117">Tek bir CLR sürümü genellikle birden çok .NET Framework sürümü destekler.</span><span class="sxs-lookup"><span data-stu-id="59761-117">A single CLR version typically supports multiple .NET Framework versions.</span></span> <span data-ttu-id="59761-118">Örneğin, CLR sürüm 4.0.30319. *xxxxx* , 42000 .NET Framework sürümlerini destekler; burada *xxxxx* , ' den küçük ve CLR sürüm 4.0.30319.42000 .NET Framework 4,6 ' den başlayarak .NET Framework sürümlerini destekler.</span><span class="sxs-lookup"><span data-stu-id="59761-118">For example, CLR version 4.0.30319.*xxxxx* supports .NET Framework versions 4 through 4.5.2, where *xxxxx* is less than 42000, and CLR version 4.0.30319.42000 supports .NET Framework versions starting with .NET Framework 4.6.</span></span>
>
> <span data-ttu-id="59761-119">Sürümler hakkında daha fazla bilgi için bkz. [.NET Framework sürümler ve bağımlılıklar](versions-and-dependencies.md).</span><span class="sxs-lookup"><span data-stu-id="59761-119">For more information about versions, see [.NET Framework versions and dependencies](versions-and-dependencies.md).</span></span>

<span data-ttu-id="59761-120">Bir bilgisayarda yüklü .NET Framework sürümlerinin bir listesini almak için, kayıt defterine erişirsiniz.</span><span class="sxs-lookup"><span data-stu-id="59761-120">To get a list of the .NET Framework versions installed on a computer, you access the registry.</span></span> <span data-ttu-id="59761-121">Kayıt defteri düzenleyicisini kullanarak kayıt defterini görüntüleyebilir veya sorgulamak için kodu kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="59761-121">You can either use the Registry Editor to view the registry or use code to query it:</span></span>

- <span data-ttu-id="59761-122">Daha yeni .NET Framework sürümlerini bul (4,5 ve üzeri):</span><span class="sxs-lookup"><span data-stu-id="59761-122">Find newer .NET Framework versions (4.5 and later):</span></span>
  - [<span data-ttu-id="59761-123">.NET Framework sürümlerini bulmak için kayıt defteri düzenleyicisini kullanın</span><span class="sxs-lookup"><span data-stu-id="59761-123">Use the Registry Editor to find .NET Framework versions</span></span>](#net_b)
  - [<span data-ttu-id="59761-124">.NET Framework sürümleri için kayıt defterini sorgulamak üzere kodu kullanma</span><span class="sxs-lookup"><span data-stu-id="59761-124">Use code to query the registry for .NET Framework versions</span></span>](#net_d)
  - [<span data-ttu-id="59761-125">.NET Framework sürümleri için kayıt defterini sorgulamak üzere PowerShell 'i kullanma</span><span class="sxs-lookup"><span data-stu-id="59761-125">Use PowerShell to query the registry for .NET Framework versions</span></span>](#ps_a)
- <span data-ttu-id="59761-126">Eski .NET Framework sürümlerini bul (1&#8211;4):</span><span class="sxs-lookup"><span data-stu-id="59761-126">Find older .NET Framework versions (1&#8211;4):</span></span>
  - [<span data-ttu-id="59761-127">.NET Framework sürümlerini bulmak için kayıt defteri düzenleyicisini kullanın</span><span class="sxs-lookup"><span data-stu-id="59761-127">Use the Registry Editor to find .NET Framework versions</span></span>](#net_a)
  - [<span data-ttu-id="59761-128">.NET Framework sürümleri için kayıt defterini sorgulamak üzere kodu kullanma</span><span class="sxs-lookup"><span data-stu-id="59761-128">Use code to query the registry for .NET Framework versions</span></span>](#net_c)

<span data-ttu-id="59761-129">Bir bilgisayarda yüklü olan CLR sürümlerinin bir listesini almak için bir araç veya kod kullanın:</span><span class="sxs-lookup"><span data-stu-id="59761-129">To get a list of the CLR versions installed on a computer, use a tool or code:</span></span>

- [<span data-ttu-id="59761-130">Clrver aracını kullanma</span><span class="sxs-lookup"><span data-stu-id="59761-130">Use the Clrver tool</span></span>](#clr_a)
- [<span data-ttu-id="59761-131">Ortam sınıfını sorgulamak için kodu kullanma</span><span class="sxs-lookup"><span data-stu-id="59761-131">Use code to query the Environment class</span></span>](#clr_b)

<span data-ttu-id="59761-132">.NET Framework her sürümü için yüklü güncelleştirmeleri algılama hakkında bilgi için bkz. [nasıl yapılır: hangi .NET Framework güncelleştirmelerinin yükleneceğini belirleme](how-to-determine-which-net-framework-updates-are-installed.md).</span><span class="sxs-lookup"><span data-stu-id="59761-132">For information about detecting the installed updates for each version of the .NET Framework, see [How to: Determine which .NET Framework updates are installed](how-to-determine-which-net-framework-updates-are-installed.md).</span></span>

## <a name="find-newer-net-framework-versions-45-and-later"></a><span data-ttu-id="59761-133">Daha yeni .NET Framework sürümlerini bul (4,5 ve üzeri)</span><span class="sxs-lookup"><span data-stu-id="59761-133">Find newer .NET Framework versions (4.5 and later)</span></span>

<a name="net_b"></a>

### <a name="find-net-framework-versions-45-and-later-in-the-registry"></a><span data-ttu-id="59761-134">Kayıt defterinde .NET Framework sürümler 4,5 ve üstünü bulun</span><span class="sxs-lookup"><span data-stu-id="59761-134">Find .NET Framework versions 4.5 and later in the registry</span></span>

1. <span data-ttu-id="59761-135">**Başlat** menüsünde, **Çalıştır**' ı seçin, *Regedit*' i girin ve **Tamam**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="59761-135">From the **Start** menu, choose **Run**, enter *regedit*, and then select **OK**.</span></span>

     <span data-ttu-id="59761-136">Regedit 'i çalıştırmak için yönetici kimlik bilgilerine sahip olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="59761-136">You must have administrative credentials to run regedit.</span></span>

2. <span data-ttu-id="59761-137">Kayıt Defteri Düzenleyicisi 'nde, aşağıdaki alt anahtarı açın: **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full**.</span><span class="sxs-lookup"><span data-stu-id="59761-137">In the Registry Editor, open the following subkey: **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full**.</span></span> <span data-ttu-id="59761-138">**Tam** alt anahtar yoksa, .NET Framework 4,5 veya sonraki bir sürümü yüklü değildir.</span><span class="sxs-lookup"><span data-stu-id="59761-138">If the **Full** subkey isn't present, then you don't have the .NET Framework 4.5 or later installed.</span></span>

    > [!NOTE]
    > <span data-ttu-id="59761-139">Kayıt defterindeki **net Framework kurulum** klasörü bir *noktayla başlamaz.*</span><span class="sxs-lookup"><span data-stu-id="59761-139">The **NET Framework Setup** folder in the registry does *not* begin with a period.</span></span>

3. <span data-ttu-id="59761-140">**Yayın**ADLı bir DWORD girişini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="59761-140">Check for a DWORD entry named **Release**.</span></span> <span data-ttu-id="59761-141">Varsa, .NET Framework 4,5 veya sonraki sürümlerin yüklü olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="59761-141">If it exists, then you have .NET Framework 4.5 or later versions installed.</span></span> <span data-ttu-id="59761-142">Değeri, .NET Framework belirli bir sürümüne karşılık gelen bir sürüm anahtarıdır.</span><span class="sxs-lookup"><span data-stu-id="59761-142">Its value is a release key that corresponds to a particular version of the .NET Framework.</span></span> <span data-ttu-id="59761-143">Aşağıdaki şekilde, örneğin, **Sürüm** girişinin değeri *378389*' dir. Bu, .NET Framework 4,5 ' in sürüm anahtarıdır.</span><span class="sxs-lookup"><span data-stu-id="59761-143">In the following figure, for example, the value of the **Release** entry is *378389*, which is the release key for .NET Framework 4.5.</span></span>

     <span data-ttu-id="59761-144">(./media/clr-installdir.png ".NET Framework 4,5 için .NET Framework 4,5 kayıt defteri girdisi") ![kayıt defteri girişi]</span><span class="sxs-lookup"><span data-stu-id="59761-144">![Registry entry for the .NET Framework 4.5](./media/clr-installdir.png "Registry entry for the .NET Framework 4.5")</span></span>

<span data-ttu-id="59761-145">Aşağıdaki tabloda, .NET Framework 4,5 ve üzeri sürümler için tek tek işletim sistemlerindeki **Sürüm** DWORD değeri listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="59761-145">The following table lists the value of the **Release** DWORD on individual operating systems for .NET Framework 4.5 and later versions.</span></span>

[!INCLUDE[Release key values note](~/includes/version-keys-note.md)]

<a name="version_table"></a>

|<span data-ttu-id="59761-146">.NET Framework sürümü</span><span class="sxs-lookup"><span data-stu-id="59761-146">.NET Framework version</span></span>|<span data-ttu-id="59761-147">Yayın DWORD değeri</span><span class="sxs-lookup"><span data-stu-id="59761-147">Value of the Release DWORD</span></span>|
|--------------------------------|-------------|
|<span data-ttu-id="59761-148">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="59761-148">.NET Framework 4.5</span></span>|<span data-ttu-id="59761-149">Tüm Windows işletim sistemleri: 378389</span><span class="sxs-lookup"><span data-stu-id="59761-149">All Windows operating systems: 378389</span></span>|
|<span data-ttu-id="59761-150">.NET Framework 4.5.1</span><span class="sxs-lookup"><span data-stu-id="59761-150">.NET Framework 4.5.1</span></span>|<span data-ttu-id="59761-151">Windows 8.1 ve Windows Server 2012 R2 'de: 378675</span><span class="sxs-lookup"><span data-stu-id="59761-151">On Windows 8.1 and Windows Server 2012 R2: 378675</span></span><br /><span data-ttu-id="59761-152">Diğer tüm Windows işletim sistemlerinde: 378758</span><span class="sxs-lookup"><span data-stu-id="59761-152">On all other Windows operating systems: 378758</span></span>|
|<span data-ttu-id="59761-153">.NET Framework 4.5.2</span><span class="sxs-lookup"><span data-stu-id="59761-153">.NET Framework 4.5.2</span></span>|<span data-ttu-id="59761-154">Tüm Windows işletim sistemleri: 379893</span><span class="sxs-lookup"><span data-stu-id="59761-154">All Windows operating systems: 379893</span></span>|
|<span data-ttu-id="59761-155">.NET Framework 4.6</span><span class="sxs-lookup"><span data-stu-id="59761-155">.NET Framework 4.6</span></span>|<span data-ttu-id="59761-156">Windows 10:393295 ' de</span><span class="sxs-lookup"><span data-stu-id="59761-156">On Windows 10: 393295</span></span><br /><span data-ttu-id="59761-157">Diğer tüm Windows işletim sistemlerinde: 393297</span><span class="sxs-lookup"><span data-stu-id="59761-157">On all other Windows operating systems: 393297</span></span>|
|<span data-ttu-id="59761-158">.NET Framework 4.6.1</span><span class="sxs-lookup"><span data-stu-id="59761-158">.NET Framework 4.6.1</span></span>|<span data-ttu-id="59761-159">Windows 10 Kasım güncelleştirme sistemlerinde: 394254</span><span class="sxs-lookup"><span data-stu-id="59761-159">On Windows 10 November Update systems: 394254</span></span><br /><span data-ttu-id="59761-160">Diğer tüm Windows işletim sistemlerinde (Windows 10 dahil): 394271</span><span class="sxs-lookup"><span data-stu-id="59761-160">On all other Windows operating systems (including Windows 10): 394271</span></span>|
|<span data-ttu-id="59761-161">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="59761-161">.NET Framework 4.6.2</span></span>|<span data-ttu-id="59761-162">Windows 10 yıldönümü güncelleştirmesi ve Windows Server 2016:394802</span><span class="sxs-lookup"><span data-stu-id="59761-162">On Windows 10 Anniversary Update and Windows Server 2016: 394802</span></span><br /><span data-ttu-id="59761-163">Diğer tüm Windows işletim sistemlerinde (diğer Windows 10 işletim sistemleri dahil): 394806</span><span class="sxs-lookup"><span data-stu-id="59761-163">On all other Windows operating systems (including other Windows 10 operating systems): 394806</span></span>|
|<span data-ttu-id="59761-164">.NET Framework 4,7</span><span class="sxs-lookup"><span data-stu-id="59761-164">.NET Framework 4.7</span></span>|<span data-ttu-id="59761-165">Windows 10 Creators Update üzerinde: 460798</span><span class="sxs-lookup"><span data-stu-id="59761-165">On Windows 10 Creators Update: 460798</span></span><br /><span data-ttu-id="59761-166">Diğer tüm Windows işletim sistemlerinde (diğer Windows 10 işletim sistemleri dahil): 460805</span><span class="sxs-lookup"><span data-stu-id="59761-166">On all other Windows operating systems (including other Windows 10 operating systems): 460805</span></span>|
|<span data-ttu-id="59761-167">.NET Framework 4.7.1</span><span class="sxs-lookup"><span data-stu-id="59761-167">.NET Framework 4.7.1</span></span>|<span data-ttu-id="59761-168">Windows 10 Fall Creators Update ve Windows Server, sürüm 1709:461308</span><span class="sxs-lookup"><span data-stu-id="59761-168">On Windows 10 Fall Creators Update and Windows Server, version 1709: 461308</span></span><br/><span data-ttu-id="59761-169">Diğer tüm Windows işletim sistemlerinde (diğer Windows 10 işletim sistemleri dahil): 461310</span><span class="sxs-lookup"><span data-stu-id="59761-169">On all other Windows operating systems (including other Windows 10 operating systems): 461310</span></span>|
|<span data-ttu-id="59761-170">.NET Framework 4.7.2</span><span class="sxs-lookup"><span data-stu-id="59761-170">.NET Framework 4.7.2</span></span>|<span data-ttu-id="59761-171">Windows 10 Nisan 2018 güncelleştirmesi ve Windows Server, sürüm 1803:461808</span><span class="sxs-lookup"><span data-stu-id="59761-171">On Windows 10 April 2018 Update and Windows Server, version 1803: 461808</span></span><br/><span data-ttu-id="59761-172">Windows 10 Nisan 2018 güncelleştirmesi ve Windows Server, sürüm 1803 dışındaki tüm Windows işletim sistemlerinde: 461814</span><span class="sxs-lookup"><span data-stu-id="59761-172">On all Windows operating systems other than Windows 10 April 2018 Update and Windows Server, version 1803: 461814</span></span>|
|<span data-ttu-id="59761-173">.NET Framework 4,8</span><span class="sxs-lookup"><span data-stu-id="59761-173">.NET Framework 4.8</span></span>|<span data-ttu-id="59761-174">Windows 10 Mayıs 2019 güncelleştirmesi: 528040</span><span class="sxs-lookup"><span data-stu-id="59761-174">On Windows 10 May 2019 Update: 528040</span></span><br/><span data-ttu-id="59761-175">Tüm diğer Windows işletim sistemlerinde (diğer Windows 10 işletim sistemleri dahil): 528049</span><span class="sxs-lookup"><span data-stu-id="59761-175">On all others Windows operating systems (including other Windows 10 operating systems): 528049</span></span>|

<span data-ttu-id="59761-176">Bu değerleri şu şekilde kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="59761-176">You can use these values as follows:</span></span>

- <span data-ttu-id="59761-177">Belirli bir .NET Framework sürümünün Windows işletim sisteminin belirli bir sürümüne yüklenip yüklenmediğini öğrenmek için, **yayın** DWORD değerinin tabloda listelenen değere *eşit* olup olmadığını test edin.</span><span class="sxs-lookup"><span data-stu-id="59761-177">To determine whether a specific version of the .NET Framework is installed on a particular version of the Windows operating system, test whether the **Release** DWORD value is *equal to* the value listed in the table.</span></span> <span data-ttu-id="59761-178">Örneğin, Windows 10 sisteminde .NET Framework 4,6 olup olmadığını anlamak için, 393295 ' *e eşit* olan bir **yayın** değeri için test edin.</span><span class="sxs-lookup"><span data-stu-id="59761-178">For example, to determine whether .NET Framework 4.6 is present on a Windows 10 system, test for the a **Release** value that is *equal to* 393295.</span></span>

- <span data-ttu-id="59761-179">.NET Framework en düşük sürümünün mevcut olup olmadığını anlamak için, bu sürüm için daha küçük **yayın** DWORD değerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="59761-179">To determine whether a minimum version of the .NET Framework is present, use the smaller **RELEASE** DWORD value for that version.</span></span> <span data-ttu-id="59761-180">Örneğin, uygulamanız .NET Framework 4,6 veya sonraki bir sürümde çalışıyorsa, 393295 ' *den büyük veya buna eşit* bir **yayın** DWORD değeri testi yapın.</span><span class="sxs-lookup"><span data-stu-id="59761-180">For example, if your application runs under .NET Framework 4.6 or a later version, test for a **RELEASE** DWORD value that is *greater than or equal to* 393295.</span></span> <span data-ttu-id="59761-181">Her bir .NET Framework sürümü için yalnızca en düşük **yayın** DWORD değerini listeleyen bir tablo için, [.NET Framework 4,5 ve sonraki sürümler Için en düşük sürüm DWORD değerlerini](minimum-release-dword.md)inceleyin.</span><span class="sxs-lookup"><span data-stu-id="59761-181">For a table that lists only the minimum **RELEASE** DWORD value for each .NET Framework version, see [The minimum values of the Release DWORD for .NET Framework 4.5 and later versions](minimum-release-dword.md).</span></span>

- <span data-ttu-id="59761-182">Birden çok sürümü test etmek için, en son .NET Framework sürümü için daha küçük DWORD değerinden *büyük veya ona eşit* bir değer için test yaparak başlayın ve ardından değeri, sonraki her önceki sürüm için daha küçük DWORD değeri ile karşılaştırın.</span><span class="sxs-lookup"><span data-stu-id="59761-182">To test for multiple versions, begin by testing for a value that is *greater than or equal to* the smaller DWORD value for the latest .NET Framework version, and then compare the value with the smaller DWORD value for each successive earlier version.</span></span> <span data-ttu-id="59761-183">Örneğin, uygulamanız .NET Framework 4,7 veya üzeri bir sürüm gerektiriyorsa ve mevcut .NET Framework sürümünü belirleyebilmek istiyorsanız, 461808 ' e *eşit veya* daha küçük olan bir **yayın** DWORD değeri için test yaparak BAŞLAYıN (daha küçük DWORD .NET Framework 4.7.2) değeri.</span><span class="sxs-lookup"><span data-stu-id="59761-183">For example, if your application requires .NET Framework 4.7 or later and you want to determine the specific version of .NET Framework present, start by testing for a **RELEASE** DWORD value that is *great than or equal to* to 461808 (the smaller DWORD value for .NET Framework 4.7.2).</span></span> <span data-ttu-id="59761-184">Ardından, **yayın** DWORD değerini her bir sonraki .NET Framework sürümü için daha küçük bir değerle karşılaştırın.</span><span class="sxs-lookup"><span data-stu-id="59761-184">Then compare the **RELEASE** DWORD value with the smaller value for each later .NET Framework version.</span></span> <span data-ttu-id="59761-185">Her bir .NET Framework sürümü için yalnızca en düşük **yayın** DWORD değerini listeleyen bir tablo için, [.NET Framework 4,5 ve sonraki sürümler Için en düşük sürüm DWORD değerlerini](minimum-release-dword.md)inceleyin.</span><span class="sxs-lookup"><span data-stu-id="59761-185">For a table that lists only the minimum **RELEASE** DWORD value for each .NET Framework version, see [The minimum values of the Release DWORD for .NET Framework 4.5 and later versions](minimum-release-dword.md).</span></span>

<a name="net_d"></a>

### <a name="find-net-framework-versions-45-and-later-with-code"></a><span data-ttu-id="59761-186">Kod ile 4,5 ve üzeri .NET Framework sürümlerini bulun</span><span class="sxs-lookup"><span data-stu-id="59761-186">Find .NET Framework versions 4.5 and later with code</span></span>

1. <span data-ttu-id="59761-187">Windows kayıt defterindeki **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full** alt anahtarına erişmek için <xref:Microsoft.Win32.RegistryKey.OpenBaseKey%2A?displayProperty=nameWithType> ve <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A?displayProperty=nameWithType> yöntemlerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="59761-187">Use the <xref:Microsoft.Win32.RegistryKey.OpenBaseKey%2A?displayProperty=nameWithType> and <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A?displayProperty=nameWithType> methods to access the **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full** subkey in the Windows registry.</span></span>

    <span data-ttu-id="59761-188">**HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full** alt anahtarındaki **Release** DWORD girişinin varlığı, bir bilgisayarda .NET Framework 4,5 veya sonraki bir sürümün yüklü olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="59761-188">The existence of the **Release** DWORD entry in the **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full** subkey indicates that the .NET Framework 4.5 or a later version is installed on a computer.</span></span>

2. <span data-ttu-id="59761-189">Yüklü sürümü öğrenmek için **yayın** girişinin değerini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="59761-189">Check the value of the **Release** entry to determine the installed version.</span></span> <span data-ttu-id="59761-190">İleriye dönük olarak uyumlu olması için [.NET Framework sürüm tablosunda](#version_table)listelenen değerden daha büyük veya ona eşit bir değer olup olmadığını kontrol edin.</span><span class="sxs-lookup"><span data-stu-id="59761-190">To be forward-compatible, check for a value greater than or equal to the value listed in the [.NET Framework version table](#version_table).</span></span>

<span data-ttu-id="59761-191">Aşağıdaki örnek, yüklü olan .NET Framework 4,5 ve sonraki sürümlerini bulmak için kayıt defterindeki **yayın** girişinin değerini denetler:</span><span class="sxs-lookup"><span data-stu-id="59761-191">The following example checks the value of the **Release** entry in the registry to find the .NET Framework 4.5 and later versions that are installed:</span></span>

[!code-csharp[ListVersions#5](../../../samples/snippets/csharp/framework/migration-guide/versions-installed3.cs)]
[!code-vb[ListVersions#5](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed3.vb)]

<span data-ttu-id="59761-192">Bu örnek sürüm denetimi için önerilen yöntemi izler:</span><span class="sxs-lookup"><span data-stu-id="59761-192">This example follows the recommended practice for version checking:</span></span>

- <span data-ttu-id="59761-193">**Yayın** girişi değerinin bilinen yayın anahtarlarının değerinden *büyük veya* bu değere eşit olup olmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="59761-193">It checks whether the value of the **Release** entry is *greater than or equal to* the value of the known release keys.</span></span>

- <span data-ttu-id="59761-194">En son sürümden en eski sürüme sırayla kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="59761-194">It checks in order from most recent version to earliest version.</span></span>

<a name="ps_a"></a>

### <a name="check-for-a-minimum-required-net-framework-version-45-and-later-with-powershell"></a><span data-ttu-id="59761-195">PowerShell ile gerekli en düşük .NET Framework sürümü (4,5 ve üzeri) denetleyin</span><span class="sxs-lookup"><span data-stu-id="59761-195">Check for a minimum-required .NET Framework version (4.5 and later) with PowerShell</span></span>

- <span data-ttu-id="59761-196">**HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full** alt anahtarının **yayın** girişinin değerini denetlemek için PowerShell komutlarını kullanın.</span><span class="sxs-lookup"><span data-stu-id="59761-196">Use PowerShell commands to check the value of the **Release** entry of the **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full** subkey.</span></span>

<span data-ttu-id="59761-197">Aşağıdaki örnekler, .NET Framework 4.6.2 veya sonraki bir sürümün yüklenip yüklenmediğini anlamak için **yayın** girişinin değerini denetler.</span><span class="sxs-lookup"><span data-stu-id="59761-197">The following examples check the value of the **Release** entry to determine whether the .NET Framework 4.6.2 or later is installed.</span></span> <span data-ttu-id="59761-198">Bu kod, yüklenmişse `True` döndürür ve aksi takdirde `False`.</span><span class="sxs-lookup"><span data-stu-id="59761-198">This code returns `True` if it's installed and `False` otherwise.</span></span>

```PowerShell
(Get-ItemProperty "HKLM:SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full").Release -ge 394802
```

<span data-ttu-id="59761-199">Farklı bir en düşük gerekli .NET Framework sürümünü denetlemek için, bu örneklerde *394802* değerini [.NET Framework sürüm tablosundan](#version_table)bir **Sürüm** değeri ile değiştirin.</span><span class="sxs-lookup"><span data-stu-id="59761-199">To check for a different minimum-required .NET Framework version, replace *394802* in these examples with a **Release** value from the [.NET Framework version table](#version_table).</span></span>

## <a name="find-older-net-framework-versions-182114"></a><span data-ttu-id="59761-200">Eski .NET Framework sürümlerini bul (1&#8211;4)</span><span class="sxs-lookup"><span data-stu-id="59761-200">Find older .NET Framework versions (1&#8211;4)</span></span>

<a name="net_a"></a>

### <a name="find-net-framework-versions-182114-in-the-registry"></a><span data-ttu-id="59761-201">Kayıt defterinde .NET Framework sürüm&#8211;1 4 bulun</span><span class="sxs-lookup"><span data-stu-id="59761-201">Find .NET Framework versions 1&#8211;4 in the registry</span></span>

1. <span data-ttu-id="59761-202">**Başlat** menüsünde, **Çalıştır**' ı seçin, *Regedit*' i girin ve **Tamam**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="59761-202">From the **Start** menu, choose **Run**, enter *regedit*, and then select **OK**.</span></span>

    <span data-ttu-id="59761-203">Regedit 'i çalıştırmak için yönetici kimlik bilgilerine sahip olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="59761-203">You must have administrative credentials to run regedit.</span></span>

2. <span data-ttu-id="59761-204">Kayıt Defteri Düzenleyicisi 'nde, aşağıdaki alt anahtarı açın: **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP**:</span><span class="sxs-lookup"><span data-stu-id="59761-204">In the Registry Editor, open the following subkey: **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP**:</span></span>

    - <span data-ttu-id="59761-205">1,1 ile 3,5 arasındaki .NET Framework sürümleri için, yüklü her sürüm **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP** alt anahtarı altında bir alt anahtar olarak listelenir.</span><span class="sxs-lookup"><span data-stu-id="59761-205">For .NET Framework versions 1.1 through 3.5, each installed version is listed as a subkey under the **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP** subkey.</span></span> <span data-ttu-id="59761-206">Örneğin, **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v3.5**.</span><span class="sxs-lookup"><span data-stu-id="59761-206">For example, **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v3.5**.</span></span> <span data-ttu-id="59761-207">Sürüm numarası, sürüm alt anahtarının **Sürüm** girişinde bir değer olarak depolanır.</span><span class="sxs-lookup"><span data-stu-id="59761-207">The version number is stored as a value in the version subkey's **Version** entry.</span></span>

    - <span data-ttu-id="59761-208">.NET Framework 4 için **Sürüm** girdisi **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4.0\Client** alt anahtarı, **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4.0\Full** altındadır. alt anahtar veya her iki alt anahtarda.</span><span class="sxs-lookup"><span data-stu-id="59761-208">For .NET Framework 4, the **Version** entry is under the **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4.0\Client** subkey, the **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4.0\Full** subkey, or under both subkeys.</span></span>

    > [!NOTE]
    > <span data-ttu-id="59761-209">Kayıt defterindeki **net Framework kurulum** klasörü bir noktayla başlamaz.</span><span class="sxs-lookup"><span data-stu-id="59761-209">The **NET Framework Setup** folder in the registry does not begin with a period.</span></span>

    <span data-ttu-id="59761-210">Aşağıdaki şekilde, .NET Framework 3,5 için alt anahtar ve **Sürüm** girişi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="59761-210">The following figure shows the subkey and its **Version** entry for the .NET Framework 3.5.</span></span>

    <span data-ttu-id="59761-211">![3,5 .NET Framework için kayıt defteri girişi.](./media/net-4-and-earlier.png ".NET Framework 3,5 ve önceki sürümler")</span><span class="sxs-lookup"><span data-stu-id="59761-211">![The registry entry for the .NET Framework 3.5.](./media/net-4-and-earlier.png ".NET Framework 3.5 and earlier versions")</span></span>

<a name="net_c"></a>

### <a name="find-net-framework-versions-182114-with-code"></a><span data-ttu-id="59761-212">.NET Framework sürüm 1&#8211;4 ile kodla bulun</span><span class="sxs-lookup"><span data-stu-id="59761-212">Find .NET Framework versions 1&#8211;4 with code</span></span>

- <span data-ttu-id="59761-213">Windows kayıt defterindeki **HKEY_LOCAL_MACHINE\Software\Microsoft\NET Framework Setup\NDP** alt anahtarına erişmek için <xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType> sınıfını kullanın.</span><span class="sxs-lookup"><span data-stu-id="59761-213">Use the <xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType> class to access the **HKEY_LOCAL_MACHINE\Software\Microsoft\NET Framework Setup\NDP** subkey in the Windows registry.</span></span>

<span data-ttu-id="59761-214">Aşağıdaki örnek, yüklü .NET Framework 1&#8211;4 sürümünü bulur:</span><span class="sxs-lookup"><span data-stu-id="59761-214">The following example finds the .NET Framework 1&#8211;4 versions that are installed:</span></span>

[!code-csharp[ListVersions](../../../samples/snippets/csharp/framework/migration-guide/versions-installed1.cs)]
[!code-vb[ListVersions](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed1.vb)]

## <a name="find-clr-versions"></a><span data-ttu-id="59761-215">CLR sürümlerini bul</span><span class="sxs-lookup"><span data-stu-id="59761-215">Find CLR versions</span></span>

<a name="clr_a"></a>

### <a name="find-the-current-clr-version-with-clrverexe"></a><span data-ttu-id="59761-216">Geçerli CLR sürümünü Clrver. exe ile bulun</span><span class="sxs-lookup"><span data-stu-id="59761-216">Find the current CLR version with Clrver.exe</span></span>

<span data-ttu-id="59761-217">Clr [Sürüm aracı 'nı (Clrver. exe)](../tools/clrver-exe-clr-version-tool.md) kullanarak bir bılgısayarda hangi CLR sürümlerinin yüklü olduğunu belirleme:</span><span class="sxs-lookup"><span data-stu-id="59761-217">Use the [CLR Version tool (Clrver.exe)](../tools/clrver-exe-clr-version-tool.md) to determine which versions of the CLR are installed on a computer:</span></span>

- <span data-ttu-id="59761-218">[Visual Studio için Geliştirici Komut İstemi](https://docs.microsoft.com/dotnet/framework/tools/developer-command-prompt-for-vs)`clrver` girin.</span><span class="sxs-lookup"><span data-stu-id="59761-218">From a [Developer Command Prompt for Visual Studio](https://docs.microsoft.com/dotnet/framework/tools/developer-command-prompt-for-vs), enter `clrver`.</span></span>

    <span data-ttu-id="59761-219">Örnek çıktı:</span><span class="sxs-lookup"><span data-stu-id="59761-219">Sample output:</span></span>

    ```console
    Versions installed on the machine:
    v2.0.50727
    v4.0.30319
    ```

<a name="clr_b"></a>

### <a name="find-the-current-clr-version-with-the-environment-class"></a><span data-ttu-id="59761-220">Ortam sınıfıyla geçerli CLR sürümünü bulma</span><span class="sxs-lookup"><span data-stu-id="59761-220">Find the current CLR version with the Environment class</span></span>

> [!IMPORTANT]
> <span data-ttu-id="59761-221">.NET Framework 4,5 ve sonraki sürümlerinde, CLR sürümünü algılamak için <xref:System.Environment.Version%2A?displayProperty=nameWithType> özelliğini kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="59761-221">For the .NET Framework 4.5 and later versions, don't use the <xref:System.Environment.Version%2A?displayProperty=nameWithType> property to detect the version of the CLR.</span></span> <span data-ttu-id="59761-222">Bunun yerine, kayıt defterini, [kodla .NET Framework sürümler 4,5 ve sonraki kısımlarında](#net_d)açıklandığı gibi sorgulayın.</span><span class="sxs-lookup"><span data-stu-id="59761-222">Instead, query the registry as described in [Find .NET Framework versions 4.5 and later with code](#net_d).</span></span>

1. <span data-ttu-id="59761-223">@No__t-1 nesnesini almak için <xref:System.Environment.Version?displayProperty=nameWithType> özelliğini sorgulayın.</span><span class="sxs-lookup"><span data-stu-id="59761-223">Query the <xref:System.Environment.Version?displayProperty=nameWithType> property to retrieve a <xref:System.Version> object.</span></span>

    <span data-ttu-id="59761-224">Döndürülen `System.Version` nesnesi şu anda kodu yürüten çalışma zamanının sürümünü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="59761-224">The returned `System.Version` object identifies the version of the runtime that's currently executing the code.</span></span> <span data-ttu-id="59761-225">Derleme sürümlerini veya çalışma zamanının bilgisayarda yüklü olabilecek diğer sürümlerini döndürmez.</span><span class="sxs-lookup"><span data-stu-id="59761-225">It doesn't return assembly versions or other versions of the runtime that may have been installed on the computer.</span></span>

    <span data-ttu-id="59761-226">.NET Framework sürümleri 4, 4,5, 4.5.1 ve 4.5.2 için, döndürülen <xref:System.Version> nesnesinin dize temsili 4.0.30319 biçimindedir. *xxxxx*, *xxxxx* 42000 ' den küçük.</span><span class="sxs-lookup"><span data-stu-id="59761-226">For the .NET Framework versions 4, 4.5, 4.5.1, and 4.5.2, the string representation of the returned <xref:System.Version> object has the form 4.0.30319.*xxxxx*, where *xxxxx* is less than 42000.</span></span> <span data-ttu-id="59761-227">.NET Framework 4,6 ve sonraki sürümlerinde, 4.0.30319.42000 biçiminde olur.</span><span class="sxs-lookup"><span data-stu-id="59761-227">For the .NET Framework 4.6 and later versions, it has the form 4.0.30319.42000.</span></span>

2. <span data-ttu-id="59761-228">@No__t-0 nesnesine sahip olduktan sonra, bunu aşağıdaki gibi sorgulayın:</span><span class="sxs-lookup"><span data-stu-id="59761-228">After you have the `Version` object, query it as follows:</span></span>

   - <span data-ttu-id="59761-229">Ana yayın tanımlayıcısı için (örneğin, sürüm 4,0 için *4* ) <xref:System.Version.Major%2A?displayProperty=nameWithType> özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="59761-229">For the major release identifier (for example, *4* for version 4.0), use the <xref:System.Version.Major%2A?displayProperty=nameWithType> property.</span></span>

   - <span data-ttu-id="59761-230">Küçük yayın tanımlayıcısı için (örneğin, sürüm 4,0 için *0* ) <xref:System.Version.Minor%2A?displayProperty=nameWithType> özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="59761-230">For the minor release identifier (for example, *0* for version 4.0), use the <xref:System.Version.Minor%2A?displayProperty=nameWithType> property.</span></span>

   - <span data-ttu-id="59761-231">Tüm sürüm dizesi için (örneğin, *4.0.30319.18010*) <xref:System.Version.ToString%2A?displayProperty=nameWithType> metodunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="59761-231">For the entire version string (for example, *4.0.30319.18010*), use the <xref:System.Version.ToString%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="59761-232">Bu yöntem, kodu yürüten çalışma zamanının sürümünü yansıtan tek bir değer döndürür.</span><span class="sxs-lookup"><span data-stu-id="59761-232">This method returns a single value that reflects the version of the runtime that's executing the code.</span></span> <span data-ttu-id="59761-233">Bu, bilgisayarda yüklü olabilecek derleme sürümlerini veya diğer çalışma zamanı sürümlerini döndürmez.</span><span class="sxs-lookup"><span data-stu-id="59761-233">It doesn't return assembly versions or other runtime versions that may be installed on the computer.</span></span>

<span data-ttu-id="59761-234">Aşağıdaki örnek, CLR sürüm bilgilerini almak için <xref:System.Environment.Version%2A?displayProperty=nameWithType> özelliğini kullanır:</span><span class="sxs-lookup"><span data-stu-id="59761-234">The following example uses the <xref:System.Environment.Version%2A?displayProperty=nameWithType> property to retrieve CLR version information:</span></span>

[!code-csharp[ListVersions](../../../samples/snippets/csharp/framework/migration-guide/versions-installed2.cs)]
[!code-vb[ListVersions](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed2.vb)]

## <a name="see-also"></a><span data-ttu-id="59761-235">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="59761-235">See also</span></span>

- [<span data-ttu-id="59761-236">Nasıl yapılır: hangi .NET Framework güncelleştirmelerinin yükleneceğini belirleme</span><span class="sxs-lookup"><span data-stu-id="59761-236">How to: Determine which .NET Framework updates are installed</span></span>](how-to-determine-which-net-framework-updates-are-installed.md)
- [<span data-ttu-id="59761-237">Geliştiriciler için .NET Framework yüklemesi</span><span class="sxs-lookup"><span data-stu-id="59761-237">Install the .NET Framework for developers</span></span>](../install/guide-for-developers.md)
- [<span data-ttu-id="59761-238">.NET Framework sürümleri ve bağımlılıklar</span><span class="sxs-lookup"><span data-stu-id="59761-238">.NET Framework versions and dependencies</span></span>](versions-and-dependencies.md)
