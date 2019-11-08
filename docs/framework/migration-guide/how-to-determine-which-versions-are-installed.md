---
title: Hangi .NET Framework sürümlerinin yüklendiğini belirleme
ms.date: 04/18/2019
dev_langs:
- csharp
- vb
ms.custom: updateeachrelease
helpviewer_keywords:
- versions, determining for .NET Framework
- .NET Framework, determining version
ms.assetid: 40a67826-e4df-4f59-a651-d9eb0fdc755d
ms.openlocfilehash: b860aac01780acb67c53e822eff478b78198996b
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738196"
---
# <a name="how-to-determine-which-net-framework-versions-are-installed"></a><span data-ttu-id="528cb-102">Nasıl yapılır: hangi .NET Framework sürümlerinin yüklendiğini belirleme</span><span class="sxs-lookup"><span data-stu-id="528cb-102">How to: Determine which .NET Framework versions are installed</span></span>

<span data-ttu-id="528cb-103">Kullanıcılar bilgisayarlarına .NET Framework birden çok sürümünü [yükleyebilir](../install/index.md) ve çalıştırabilir.</span><span class="sxs-lookup"><span data-stu-id="528cb-103">Users can [install](../install/index.md) and run multiple versions of the .NET Framework on their computers.</span></span> <span data-ttu-id="528cb-104">Uygulamanızı geliştirirken veya dağıtırken, kullanıcının bilgisayarında hangi .NET Framework sürümlerinin yüklü olduğunu bilmeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="528cb-104">When you develop or deploy your app, you might need to know which .NET Framework versions are installed on the user’s computer.</span></span>

<span data-ttu-id="528cb-105">.NET Framework, sürümü ayrı olan iki ana bileşenden oluşur:</span><span class="sxs-lookup"><span data-stu-id="528cb-105">The .NET Framework consists of two main components, which are versioned separately:</span></span>

- <span data-ttu-id="528cb-106">Uygulamalarınız için işlevsellik sağlayan tür ve kaynak koleksiyonları olan derlemeler kümesi.</span><span class="sxs-lookup"><span data-stu-id="528cb-106">A set of assemblies, which are collections of types and resources that provide the functionality for your apps.</span></span> <span data-ttu-id="528cb-107">.NET Framework ve derlemeler aynı sürüm numarasını paylaşır.</span><span class="sxs-lookup"><span data-stu-id="528cb-107">The .NET Framework and assemblies share the same version number.</span></span>

- <span data-ttu-id="528cb-108">Uygulamanızın kodunu yöneten ve yürüten ortak dil çalışma zamanı (CLR).</span><span class="sxs-lookup"><span data-stu-id="528cb-108">The common language runtime (CLR), which manages and executes your app's code.</span></span> <span data-ttu-id="528cb-109">CLR kendi sürüm numarasıyla tanımlanır (bkz. [sürümler ve bağımlılıklar](versions-and-dependencies.md)).</span><span class="sxs-lookup"><span data-stu-id="528cb-109">The CLR is identified by its own version number (see [Versions and dependencies](versions-and-dependencies.md)).</span></span>

> [!NOTE]
> <span data-ttu-id="528cb-110">.NET Framework'ün her yeni sürümü önceki sürümlerdeki özellikleri korur ve yeni özellikler ekler.</span><span class="sxs-lookup"><span data-stu-id="528cb-110">Each new version of the .NET Framework retains features from the previous versions and adds new features.</span></span> <span data-ttu-id="528cb-111">.NET Framework birden çok sürümünü aynı anda tek bir bilgisayara yükleyebilirsiniz; Yani, önceki sürümleri kaldırmak zorunda kalmadan .NET Framework yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="528cb-111">You can load multiple versions of the .NET Framework on a single computer at the same time, which means that you can install the .NET Framework without having to uninstall previous versions.</span></span> <span data-ttu-id="528cb-112">Genel olarak, kullandığınız bir uygulama belirli bir sürüme bağlı olabileceğinden ve bu sürüm kaldırılırsa kesintiye uğraabileceğinden, .NET Framework önceki sürümlerini kaldırmamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="528cb-112">In general, you shouldn't uninstall previous versions of the .NET Framework, because an application you use may depend on a specific version and may break if that version is removed.</span></span>
>
> <span data-ttu-id="528cb-113">.NET Framework sürümü ile CLR sürümü arasında bir fark vardır:</span><span class="sxs-lookup"><span data-stu-id="528cb-113">There is a difference between the .NET Framework version and the CLR version:</span></span>
>
> - <span data-ttu-id="528cb-114">.NET Framework sürümü, .NET Framework sınıf kitaplığını oluşturan derlemeler kümesini temel alır.</span><span class="sxs-lookup"><span data-stu-id="528cb-114">The .NET Framework version is based on the set of assemblies that form the .NET Framework class library.</span></span> <span data-ttu-id="528cb-115">Örneğin, .NET Framework sürümler 4,5, 4.6.1 ve 4.7.2 ' i içerir.</span><span class="sxs-lookup"><span data-stu-id="528cb-115">For example, .NET Framework versions include 4.5, 4.6.1, and 4.7.2.</span></span>
> - <span data-ttu-id="528cb-116">CLR sürümü .NET Framework uygulamalarının çalıştırıldığı çalışma zamanına dayalıdır.</span><span class="sxs-lookup"><span data-stu-id="528cb-116">The CLR version is based on the runtime on which .NET Framework applications execute.</span></span> <span data-ttu-id="528cb-117">Tek bir CLR sürümü genellikle birden çok .NET Framework sürümü destekler.</span><span class="sxs-lookup"><span data-stu-id="528cb-117">A single CLR version typically supports multiple .NET Framework versions.</span></span> <span data-ttu-id="528cb-118">Örneğin, CLR sürüm 4.0.30319. *xxxxx* , 42000 .NET Framework sürümlerini destekler; burada *xxxxx* , ' den küçük ve CLR sürüm 4.0.30319.42000 .NET Framework 4,6 ' den başlayarak .NET Framework sürümlerini destekler.</span><span class="sxs-lookup"><span data-stu-id="528cb-118">For example, CLR version 4.0.30319.*xxxxx* supports .NET Framework versions 4 through 4.5.2, where *xxxxx* is less than 42000, and CLR version 4.0.30319.42000 supports .NET Framework versions starting with .NET Framework 4.6.</span></span>
>
> <span data-ttu-id="528cb-119">Sürümler hakkında daha fazla bilgi için bkz. [.NET Framework sürümler ve bağımlılıklar](versions-and-dependencies.md).</span><span class="sxs-lookup"><span data-stu-id="528cb-119">For more information about versions, see [.NET Framework versions and dependencies](versions-and-dependencies.md).</span></span>

<span data-ttu-id="528cb-120">Kayıt defteri, bir bilgisayarda yüklü .NET Framework sürümlerinin bir listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="528cb-120">The registry contains a list of the .NET Framework versions installed on a computer.</span></span> <span data-ttu-id="528cb-121">Kayıt defterini görüntülemek veya kodu kullanarak sorgulamak için kayıt defteri düzenleyicisini kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="528cb-121">You can either use the Registry Editor to view the registry or query it with code:</span></span>

- <span data-ttu-id="528cb-122">Daha yeni .NET Framework sürümlerini bul (4,5 ve üzeri):</span><span class="sxs-lookup"><span data-stu-id="528cb-122">Find newer .NET Framework versions (4.5 and later):</span></span>

  - [<span data-ttu-id="528cb-123">.NET Framework sürümlerini bulmak için kayıt defteri düzenleyicisini kullanın</span><span class="sxs-lookup"><span data-stu-id="528cb-123">Use the Registry Editor to find .NET Framework versions</span></span>](#net_b)
  - [<span data-ttu-id="528cb-124">.NET Framework sürümleri için kayıt defterini sorgulamak üzere kodu kullanma</span><span class="sxs-lookup"><span data-stu-id="528cb-124">Use code to query the registry for .NET Framework versions</span></span>](#net_d)
  - [<span data-ttu-id="528cb-125">.NET Framework sürümleri için kayıt defterini sorgulamak üzere PowerShell 'i kullanma</span><span class="sxs-lookup"><span data-stu-id="528cb-125">Use PowerShell to query the registry for .NET Framework versions</span></span>](#ps_a)

- <span data-ttu-id="528cb-126">Eski .NET Framework sürümlerini bul (1 ile 4 arasında):</span><span class="sxs-lookup"><span data-stu-id="528cb-126">Find older .NET Framework versions (1 through 4):</span></span>

  - [<span data-ttu-id="528cb-127">.NET Framework sürümlerini bulmak için kayıt defteri düzenleyicisini kullanın</span><span class="sxs-lookup"><span data-stu-id="528cb-127">Use the Registry Editor to find .NET Framework versions</span></span>](#net_a)
  - [<span data-ttu-id="528cb-128">.NET Framework sürümleri için kayıt defterini sorgulamak üzere kodu kullanma</span><span class="sxs-lookup"><span data-stu-id="528cb-128">Use code to query the registry for .NET Framework versions</span></span>](#net_c)

<span data-ttu-id="528cb-129">Bir bilgisayarda yüklü olan CLR sürümlerinin bir listesini almak için bir araç veya kod kullanın:</span><span class="sxs-lookup"><span data-stu-id="528cb-129">To get a list of the CLR versions installed on a computer, use a tool or code:</span></span>

- [<span data-ttu-id="528cb-130">Clrver aracını kullanma</span><span class="sxs-lookup"><span data-stu-id="528cb-130">Use the Clrver tool</span></span>](#clr_a)
- [<span data-ttu-id="528cb-131">Ortam sınıfını sorgulamak için kodu kullanma</span><span class="sxs-lookup"><span data-stu-id="528cb-131">Use code to query the Environment class</span></span>](#clr_b)

<span data-ttu-id="528cb-132">.NET Framework her sürümü için yüklü güncelleştirmeleri algılama hakkında bilgi için bkz. [nasıl yapılır: hangi .NET Framework güncelleştirmelerinin yükleneceğini belirleme](how-to-determine-which-net-framework-updates-are-installed.md).</span><span class="sxs-lookup"><span data-stu-id="528cb-132">For information about detecting the installed updates for each version of the .NET Framework, see [How to: Determine which .NET Framework updates are installed](how-to-determine-which-net-framework-updates-are-installed.md).</span></span>

## <a name="find-newer-net-framework-versions-45-and-later"></a><span data-ttu-id="528cb-133">Daha yeni .NET Framework sürümlerini bul (4,5 ve üzeri)</span><span class="sxs-lookup"><span data-stu-id="528cb-133">Find newer .NET Framework versions (4.5 and later)</span></span>

<span data-ttu-id="528cb-134">Kayıt Defteri Düzenleyicisi 'ni kullanarak kayıt defterindeki sürüm bilgilerini bulabilir veya kayıt defterini programlı bir şekilde sorgulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="528cb-134">You can use Registry Editor to find version information in the registry, or you can query the registry programmatically.</span></span>

<a name="net_b"></a>

### <a name="use-registry-editor"></a><span data-ttu-id="528cb-135">Kayıt Defteri Düzenleyicisi 'Ni kullan</span><span class="sxs-lookup"><span data-stu-id="528cb-135">Use Registry Editor</span></span>

1. <span data-ttu-id="528cb-136">**Başlat** menüsünde, **Çalıştır**' ı seçin, *Regedit*' i girin ve **Tamam**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="528cb-136">From the **Start** menu, choose **Run**, enter *regedit*, and then select **OK**.</span></span>

     <span data-ttu-id="528cb-137">Regedit 'i çalıştırmak için yönetici kimlik bilgilerine sahip olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="528cb-137">You must have administrative credentials to run regedit.</span></span>

2. <span data-ttu-id="528cb-138">Kayıt Defteri Düzenleyicisi 'nde, aşağıdaki alt anahtarı açın: **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full**.</span><span class="sxs-lookup"><span data-stu-id="528cb-138">In the Registry Editor, open the following subkey: **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full**.</span></span> <span data-ttu-id="528cb-139">**Tam** alt anahtar yoksa, .NET Framework 4,5 veya sonraki bir sürümü yüklü değildir.</span><span class="sxs-lookup"><span data-stu-id="528cb-139">If the **Full** subkey isn't present, then you don't have the .NET Framework 4.5 or later installed.</span></span>

    > [!NOTE]
    > <span data-ttu-id="528cb-140">Kayıt defterindeki **net Framework kurulum** klasörü bir *noktayla başlamaz.*</span><span class="sxs-lookup"><span data-stu-id="528cb-140">The **NET Framework Setup** folder in the registry does *not* begin with a period.</span></span>

3. <span data-ttu-id="528cb-141">**Yayın**ADLı bir DWORD girişini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="528cb-141">Check for a DWORD entry named **Release**.</span></span> <span data-ttu-id="528cb-142">Varsa, .NET Framework 4,5 veya sonraki bir sürümü yüklemiş olursunuz.</span><span class="sxs-lookup"><span data-stu-id="528cb-142">If it exists, then you have .NET Framework 4.5 or later installed.</span></span> <span data-ttu-id="528cb-143">Değeri, .NET Framework belirli bir sürümüne karşılık gelen bir sürüm anahtarıdır.</span><span class="sxs-lookup"><span data-stu-id="528cb-143">Its value is a release key that corresponds to a particular version of the .NET Framework.</span></span> <span data-ttu-id="528cb-144">Aşağıdaki şekilde, örneğin, **Sürüm** girişinin değeri 378389 ' dir. bu, .NET Framework 4,5 ' in sürüm anahtarıdır.</span><span class="sxs-lookup"><span data-stu-id="528cb-144">In the following figure, for example, the value of the **Release** entry is 378389, which is the release key for .NET Framework 4.5.</span></span>

   <span data-ttu-id="528cb-145">![.NET Framework 4,5 için kayıt defteri girişi](./media/clr-installdir.png ".NET Framework 4,5 için kayıt defteri girişi")</span><span class="sxs-lookup"><span data-stu-id="528cb-145">![Registry entry for the .NET Framework 4.5](./media/clr-installdir.png "Registry entry for the .NET Framework 4.5")</span></span>

<span data-ttu-id="528cb-146">Aşağıdaki tabloda, .NET Framework 4,5 ve üzeri sürümler için tek tek işletim sistemlerindeki **Sürüm** DWORD değeri listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="528cb-146">The following table lists the value of the **Release** DWORD on individual operating systems for .NET Framework 4.5 and later versions.</span></span>

[!INCLUDE[Release key values note](~/includes/version-keys-note.md)]

<a name="version_table"></a>

|<span data-ttu-id="528cb-147">.NET Framework sürümü</span><span class="sxs-lookup"><span data-stu-id="528cb-147">.NET Framework version</span></span>|<span data-ttu-id="528cb-148">Yayın DWORD değeri</span><span class="sxs-lookup"><span data-stu-id="528cb-148">Value of the Release DWORD</span></span>|
|--------------------------------|-------------|
|<span data-ttu-id="528cb-149">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="528cb-149">.NET Framework 4.5</span></span>|<span data-ttu-id="528cb-150">Tüm Windows işletim sistemleri: 378389</span><span class="sxs-lookup"><span data-stu-id="528cb-150">All Windows operating systems: 378389</span></span>|
|<span data-ttu-id="528cb-151">.NET Framework 4.5.1</span><span class="sxs-lookup"><span data-stu-id="528cb-151">.NET Framework 4.5.1</span></span>|<span data-ttu-id="528cb-152">Windows 8.1 ve Windows Server 2012 R2 'de: 378675</span><span class="sxs-lookup"><span data-stu-id="528cb-152">On Windows 8.1 and Windows Server 2012 R2: 378675</span></span><br /><span data-ttu-id="528cb-153">Diğer tüm Windows işletim sistemlerinde: 378758</span><span class="sxs-lookup"><span data-stu-id="528cb-153">On all other Windows operating systems: 378758</span></span>|
|<span data-ttu-id="528cb-154">.NET Framework 4.5.2</span><span class="sxs-lookup"><span data-stu-id="528cb-154">.NET Framework 4.5.2</span></span>|<span data-ttu-id="528cb-155">Tüm Windows işletim sistemleri: 379893</span><span class="sxs-lookup"><span data-stu-id="528cb-155">All Windows operating systems: 379893</span></span>|
|<span data-ttu-id="528cb-156">.NET Framework 4.6</span><span class="sxs-lookup"><span data-stu-id="528cb-156">.NET Framework 4.6</span></span>|<span data-ttu-id="528cb-157">Windows 10:393295 ' de</span><span class="sxs-lookup"><span data-stu-id="528cb-157">On Windows 10: 393295</span></span><br /><span data-ttu-id="528cb-158">Diğer tüm Windows işletim sistemlerinde: 393297</span><span class="sxs-lookup"><span data-stu-id="528cb-158">On all other Windows operating systems: 393297</span></span>|
|<span data-ttu-id="528cb-159">.NET Framework 4.6.1</span><span class="sxs-lookup"><span data-stu-id="528cb-159">.NET Framework 4.6.1</span></span>|<span data-ttu-id="528cb-160">Windows 10 Kasım güncelleştirme sistemlerinde: 394254</span><span class="sxs-lookup"><span data-stu-id="528cb-160">On Windows 10 November Update systems: 394254</span></span><br /><span data-ttu-id="528cb-161">Diğer tüm Windows işletim sistemlerinde (Windows 10 dahil): 394271</span><span class="sxs-lookup"><span data-stu-id="528cb-161">On all other Windows operating systems (including Windows 10): 394271</span></span>|
|<span data-ttu-id="528cb-162">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="528cb-162">.NET Framework 4.6.2</span></span>|<span data-ttu-id="528cb-163">Windows 10 yıldönümü güncelleştirmesi ve Windows Server 2016:394802</span><span class="sxs-lookup"><span data-stu-id="528cb-163">On Windows 10 Anniversary Update and Windows Server 2016: 394802</span></span><br /><span data-ttu-id="528cb-164">Diğer tüm Windows işletim sistemlerinde (diğer Windows 10 işletim sistemleri dahil): 394806</span><span class="sxs-lookup"><span data-stu-id="528cb-164">On all other Windows operating systems (including other Windows 10 operating systems): 394806</span></span>|
|<span data-ttu-id="528cb-165">.NET Framework 4,7</span><span class="sxs-lookup"><span data-stu-id="528cb-165">.NET Framework 4.7</span></span>|<span data-ttu-id="528cb-166">Windows 10 Creators Update üzerinde: 460798</span><span class="sxs-lookup"><span data-stu-id="528cb-166">On Windows 10 Creators Update: 460798</span></span><br /><span data-ttu-id="528cb-167">Diğer tüm Windows işletim sistemlerinde (diğer Windows 10 işletim sistemleri dahil): 460805</span><span class="sxs-lookup"><span data-stu-id="528cb-167">On all other Windows operating systems (including other Windows 10 operating systems): 460805</span></span>|
|<span data-ttu-id="528cb-168">.NET Framework 4.7.1</span><span class="sxs-lookup"><span data-stu-id="528cb-168">.NET Framework 4.7.1</span></span>|<span data-ttu-id="528cb-169">Windows 10 Fall Creators Update ve Windows Server, sürüm 1709:461308</span><span class="sxs-lookup"><span data-stu-id="528cb-169">On Windows 10 Fall Creators Update and Windows Server, version 1709: 461308</span></span><br/><span data-ttu-id="528cb-170">Diğer tüm Windows işletim sistemlerinde (diğer Windows 10 işletim sistemleri dahil): 461310</span><span class="sxs-lookup"><span data-stu-id="528cb-170">On all other Windows operating systems (including other Windows 10 operating systems): 461310</span></span>|
|<span data-ttu-id="528cb-171">.NET Framework 4.7.2</span><span class="sxs-lookup"><span data-stu-id="528cb-171">.NET Framework 4.7.2</span></span>|<span data-ttu-id="528cb-172">Windows 10 Nisan 2018 güncelleştirmesi ve Windows Server, sürüm 1803:461808</span><span class="sxs-lookup"><span data-stu-id="528cb-172">On Windows 10 April 2018 Update and Windows Server, version 1803: 461808</span></span><br/><span data-ttu-id="528cb-173">Windows 10 Nisan 2018 güncelleştirmesi ve Windows Server, sürüm 1803 dışındaki tüm Windows işletim sistemlerinde: 461814</span><span class="sxs-lookup"><span data-stu-id="528cb-173">On all Windows operating systems other than Windows 10 April 2018 Update and Windows Server, version 1803: 461814</span></span>|
|<span data-ttu-id="528cb-174">.NET Framework 4,8</span><span class="sxs-lookup"><span data-stu-id="528cb-174">.NET Framework 4.8</span></span>|<span data-ttu-id="528cb-175">Windows 10 Mayıs 2019 güncelleştirmesi ve Windows 10 Kasım 2019 güncelleştirmesi: 528040</span><span class="sxs-lookup"><span data-stu-id="528cb-175">On Windows 10 May 2019 Update and Windows 10 November 2019 Update: 528040</span></span><br/><span data-ttu-id="528cb-176">Diğer tüm Windows işletim sistemlerinde (diğer Windows 10 işletim sistemleri dahil): 528049</span><span class="sxs-lookup"><span data-stu-id="528cb-176">On all other Windows operating systems (including other Windows 10 operating systems): 528049</span></span>|

#### <a name="specific-version"></a><span data-ttu-id="528cb-177">Belirli sürüm</span><span class="sxs-lookup"><span data-stu-id="528cb-177">Specific version</span></span>

<span data-ttu-id="528cb-178">*Belirli* bir .NET Framework sürümünün Windows işletim sisteminin belirli bir sürümüne yüklenip yüklenmediğini öğrenmek Için, **yayın** DWORD değerinin tabloda listelenen değere *eşit* olup olmadığını test edin.</span><span class="sxs-lookup"><span data-stu-id="528cb-178">To determine whether a *specific* version of the .NET Framework is installed on a particular version of the Windows operating system, test whether the **Release** DWORD value is *equal to* the value listed in the table.</span></span> <span data-ttu-id="528cb-179">Örneğin, Windows 10 sisteminde .NET Framework 4,6 olup olmadığını anlamak için, 393295 ' *e eşit* olan bir **yayın** değeri için test edin.</span><span class="sxs-lookup"><span data-stu-id="528cb-179">For example, to determine whether .NET Framework 4.6 is present on a Windows 10 system, test for the a **Release** value that is *equal to* 393295.</span></span>

#### <a name="minimum-version"></a><span data-ttu-id="528cb-180">En düşük sürüm</span><span class="sxs-lookup"><span data-stu-id="528cb-180">Minimum version</span></span>

<span data-ttu-id="528cb-181">.NET Framework *En düşük* sürümünün mevcut olup olmadığını anlamak için önceki tablodan bu sürüm için en küçük **yayın** DWORD değerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="528cb-181">To determine whether a *minimum* version of the .NET Framework is present, use the smallest **RELEASE** DWORD value for that version from the previous table.</span></span> <span data-ttu-id="528cb-182">(Kolaylık olması için, aşağıdaki tabloda yer alan minimum değerler de listelenmiştir.)</span><span class="sxs-lookup"><span data-stu-id="528cb-182">(For convenience, the minimum values are also listed in the table that follows.)</span></span>

<span data-ttu-id="528cb-183">Örneğin, uygulamanız .NET Framework 4,8 veya sonraki bir sürümde çalışıyorsa, 528040 ' *den büyük veya buna eşit* bir **yayın** DWORD değeri testi yapın.</span><span class="sxs-lookup"><span data-stu-id="528cb-183">For example, if your application runs under .NET Framework 4.8 or a later version, test for a **RELEASE** DWORD value that is *greater than or equal to* 528040.</span></span>

|<span data-ttu-id="528cb-184">.NET Framework sürümü</span><span class="sxs-lookup"><span data-stu-id="528cb-184">.NET Framework version</span></span>|<span data-ttu-id="528cb-185">En küçük yayın DWORD değeri</span><span class="sxs-lookup"><span data-stu-id="528cb-185">Minimum value of the Release DWORD</span></span>|
|--------------------------------|-------------|
|<span data-ttu-id="528cb-186">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="528cb-186">.NET Framework 4.5</span></span>|<span data-ttu-id="528cb-187">378389</span><span class="sxs-lookup"><span data-stu-id="528cb-187">378389</span></span>|
|<span data-ttu-id="528cb-188">.NET Framework 4.5.1</span><span class="sxs-lookup"><span data-stu-id="528cb-188">.NET Framework 4.5.1</span></span>|<span data-ttu-id="528cb-189">378675</span><span class="sxs-lookup"><span data-stu-id="528cb-189">378675</span></span>|
|<span data-ttu-id="528cb-190">.NET Framework 4.5.2</span><span class="sxs-lookup"><span data-stu-id="528cb-190">.NET Framework 4.5.2</span></span>|<span data-ttu-id="528cb-191">379893</span><span class="sxs-lookup"><span data-stu-id="528cb-191">379893</span></span>|
|<span data-ttu-id="528cb-192">.NET Framework 4.6</span><span class="sxs-lookup"><span data-stu-id="528cb-192">.NET Framework 4.6</span></span>|<span data-ttu-id="528cb-193">393295</span><span class="sxs-lookup"><span data-stu-id="528cb-193">393295</span></span>|
|<span data-ttu-id="528cb-194">.NET Framework 4.6.1</span><span class="sxs-lookup"><span data-stu-id="528cb-194">.NET Framework 4.6.1</span></span>|<span data-ttu-id="528cb-195">394254</span><span class="sxs-lookup"><span data-stu-id="528cb-195">394254</span></span>|
|<span data-ttu-id="528cb-196">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="528cb-196">.NET Framework 4.6.2</span></span>|<span data-ttu-id="528cb-197">394802</span><span class="sxs-lookup"><span data-stu-id="528cb-197">394802</span></span>|
|<span data-ttu-id="528cb-198">.NET Framework 4,7</span><span class="sxs-lookup"><span data-stu-id="528cb-198">.NET Framework 4.7</span></span>|<span data-ttu-id="528cb-199">460798</span><span class="sxs-lookup"><span data-stu-id="528cb-199">460798</span></span>|
|<span data-ttu-id="528cb-200">.NET Framework 4.7.1</span><span class="sxs-lookup"><span data-stu-id="528cb-200">.NET Framework 4.7.1</span></span>|<span data-ttu-id="528cb-201">461308</span><span class="sxs-lookup"><span data-stu-id="528cb-201">461308</span></span>|
|<span data-ttu-id="528cb-202">.NET Framework 4.7.2</span><span class="sxs-lookup"><span data-stu-id="528cb-202">.NET Framework 4.7.2</span></span>|<span data-ttu-id="528cb-203">461808</span><span class="sxs-lookup"><span data-stu-id="528cb-203">461808</span></span>|
|<span data-ttu-id="528cb-204">.NET Framework 4,8</span><span class="sxs-lookup"><span data-stu-id="528cb-204">.NET Framework 4.8</span></span>|<span data-ttu-id="528cb-205">528040</span><span class="sxs-lookup"><span data-stu-id="528cb-205">528040</span></span>|

#### <a name="multiple-versions"></a><span data-ttu-id="528cb-206">Birden çok sürüm</span><span class="sxs-lookup"><span data-stu-id="528cb-206">Multiple versions</span></span>

<span data-ttu-id="528cb-207">Birden çok sürümü test etmek için, en son .NET Framework sürümü için daha küçük DWORD değerinden *büyük veya ona eşit* bir değer için test yaparak başlayın ve ardından değeri, sonraki her önceki sürüm için daha küçük DWORD değeri ile karşılaştırın.</span><span class="sxs-lookup"><span data-stu-id="528cb-207">To test for multiple versions, begin by testing for a value that is *greater than or equal to* the smaller DWORD value for the latest .NET Framework version, and then compare the value with the smaller DWORD value for each successive earlier version.</span></span> <span data-ttu-id="528cb-208">Örneğin, uygulamanız .NET Framework 4,7 veya üzeri bir sürüm gerektiriyorsa ve mevcut .NET Framework sürümünü belirleyebilmek istiyorsanız, 461808 ' e *eşit veya* daha küçük olan bir **yayın** DWORD değeri için test yaparak BAŞLAYıN (daha küçük DWORD .NET Framework 4.7.2) değeri.</span><span class="sxs-lookup"><span data-stu-id="528cb-208">For example, if your application requires .NET Framework 4.7 or later and you want to determine the specific version of .NET Framework present, start by testing for a **RELEASE** DWORD value that is *great than or equal to* to 461808 (the smaller DWORD value for .NET Framework 4.7.2).</span></span> <span data-ttu-id="528cb-209">Ardından, **yayın** DWORD değerini her bir sonraki .NET Framework sürümü için daha küçük bir değerle karşılaştırın.</span><span class="sxs-lookup"><span data-stu-id="528cb-209">Then compare the **RELEASE** DWORD value with the smaller value for each later .NET Framework version.</span></span>

<a name="net_d"></a>

### <a name="query-the-registry-using-code"></a><span data-ttu-id="528cb-210">Kodu kullanarak kayıt defterini sorgulama</span><span class="sxs-lookup"><span data-stu-id="528cb-210">Query the registry using code</span></span>

1. <span data-ttu-id="528cb-211">Windows kayıt defterindeki **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full** alt anahtarına erişmek için <xref:Microsoft.Win32.RegistryKey.OpenBaseKey%2A?displayProperty=nameWithType> ve <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A?displayProperty=nameWithType> yöntemlerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="528cb-211">Use the <xref:Microsoft.Win32.RegistryKey.OpenBaseKey%2A?displayProperty=nameWithType> and <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A?displayProperty=nameWithType> methods to access the **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full** subkey in the Windows registry.</span></span>

   <span data-ttu-id="528cb-212">**HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full** alt anahtarındaki **Release** DWORD girişinin varlığı, bir bilgisayarda .NET Framework 4,5 veya sonraki bir sürümün yüklü olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="528cb-212">The existence of the **Release** DWORD entry in the **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full** subkey indicates that the .NET Framework 4.5 or a later version is installed on a computer.</span></span>

2. <span data-ttu-id="528cb-213">Yüklü sürümü öğrenmek için **yayın** girişinin değerini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="528cb-213">Check the value of the **Release** entry to determine the installed version.</span></span> <span data-ttu-id="528cb-214">İleriye dönük olarak uyumlu olması için [.NET Framework sürüm tablosunda](#version_table)listelenen değerden daha büyük veya ona eşit bir değer olup olmadığını kontrol edin.</span><span class="sxs-lookup"><span data-stu-id="528cb-214">To be forward-compatible, check for a value greater than or equal to the value listed in the [.NET Framework version table](#version_table).</span></span>

<span data-ttu-id="528cb-215">Aşağıdaki örnek, yüklü olan .NET Framework 4,5 ve sonraki sürümlerini bulmak için kayıt defterindeki **yayın** girişinin değerini denetler:</span><span class="sxs-lookup"><span data-stu-id="528cb-215">The following example checks the value of the **Release** entry in the registry to find the .NET Framework 4.5 and later versions that are installed:</span></span>

[!code-csharp[ListVersions#5](../../../samples/snippets/csharp/framework/migration-guide/versions-installed3.cs)]
[!code-vb[ListVersions#5](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed3.vb)]

<span data-ttu-id="528cb-216">Bu örnek sürüm denetimi için önerilen yöntemi izler:</span><span class="sxs-lookup"><span data-stu-id="528cb-216">This example follows the recommended practice for version checking:</span></span>

- <span data-ttu-id="528cb-217">**Yayın** girişi değerinin bilinen yayın anahtarlarının değerinden *büyük veya* bu değere eşit olup olmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="528cb-217">It checks whether the value of the **Release** entry is *greater than or equal to* the value of the known release keys.</span></span>

- <span data-ttu-id="528cb-218">En son sürümden en eski sürüme sırayla kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="528cb-218">It checks in order from most recent version to earliest version.</span></span>

<a name="ps_a"></a>

### <a name="use-powershell-to-check-for-a-minimum-required-version"></a><span data-ttu-id="528cb-219">Gerekli en düşük sürümü denetlemek için PowerShell 'i kullanın</span><span class="sxs-lookup"><span data-stu-id="528cb-219">Use PowerShell to check for a minimum-required version</span></span>

<span data-ttu-id="528cb-220">**HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full** alt anahtarının **yayın** girişinin değerini denetlemek için PowerShell komutlarını kullanın.</span><span class="sxs-lookup"><span data-stu-id="528cb-220">Use PowerShell commands to check the value of the **Release** entry of the **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full** subkey.</span></span>

<span data-ttu-id="528cb-221">Aşağıdaki örnekler, .NET Framework 4.6.2 veya sonraki bir sürümün yüklenip yüklenmediğini anlamak için **yayın** girişinin değerini denetler.</span><span class="sxs-lookup"><span data-stu-id="528cb-221">The following examples check the value of the **Release** entry to determine whether the .NET Framework 4.6.2 or later is installed.</span></span> <span data-ttu-id="528cb-222">Bu kod, yüklenmişse `True` döndürür ve yoksa `False`.</span><span class="sxs-lookup"><span data-stu-id="528cb-222">This code returns `True` if it's installed and `False` otherwise.</span></span>

```PowerShell
(Get-ItemProperty "HKLM:SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full").Release -ge 394802
```

<span data-ttu-id="528cb-223">Farklı bir en düşük gerekli .NET Framework sürümünü denetlemek için örnekteki `394802` [.NET Framework sürüm tablosundan](#version_table)bir değer ile değiştirin.</span><span class="sxs-lookup"><span data-stu-id="528cb-223">To check for a different minimum-required .NET Framework version, replace `394802` in the example with a value from the [.NET Framework version table](#version_table).</span></span> <span data-ttu-id="528cb-224">Bu sürüm için gösterilen en küçük değeri kullanın.</span><span class="sxs-lookup"><span data-stu-id="528cb-224">Use the smallest value shown for that version.</span></span>

## <a name="find-older-net-framework-versions-1-through-4"></a><span data-ttu-id="528cb-225">Eski .NET Framework sürümlerini bul (1 ile 4 arasında)</span><span class="sxs-lookup"><span data-stu-id="528cb-225">Find older .NET Framework versions (1 through 4)</span></span>

<a name="net_a"></a>

### <a name="use-registry-editor-older-framework-versions"></a><span data-ttu-id="528cb-226">Kayıt Defteri Düzenleyicisi 'Ni kullan (eski Framework sürümleri)</span><span class="sxs-lookup"><span data-stu-id="528cb-226">Use Registry Editor (older framework versions)</span></span>

1. <span data-ttu-id="528cb-227">**Başlat** menüsünde, **Çalıştır**' ı seçin, *Regedit*' i girin ve **Tamam**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="528cb-227">From the **Start** menu, choose **Run**, enter *regedit*, and then select **OK**.</span></span>

    <span data-ttu-id="528cb-228">Regedit 'i çalıştırmak için yönetici kimlik bilgilerine sahip olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="528cb-228">You must have administrative credentials to run regedit.</span></span>

2. <span data-ttu-id="528cb-229">Kayıt Defteri Düzenleyicisi 'nde, aşağıdaki alt anahtarı açın: **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP**:</span><span class="sxs-lookup"><span data-stu-id="528cb-229">In the Registry Editor, open the following subkey: **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP**:</span></span>

    - <span data-ttu-id="528cb-230">1,1 ile 3,5 arasındaki .NET Framework sürümleri için, yüklü her sürüm **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP** alt anahtarı altında bir alt anahtar olarak listelenir.</span><span class="sxs-lookup"><span data-stu-id="528cb-230">For .NET Framework versions 1.1 through 3.5, each installed version is listed as a subkey under the **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP** subkey.</span></span> <span data-ttu-id="528cb-231">Örneğin, **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v3.5**.</span><span class="sxs-lookup"><span data-stu-id="528cb-231">For example, **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v3.5**.</span></span> <span data-ttu-id="528cb-232">Sürüm numarası, sürüm alt anahtarının **Sürüm** girişinde bir değer olarak depolanır.</span><span class="sxs-lookup"><span data-stu-id="528cb-232">The version number is stored as a value in the version subkey's **Version** entry.</span></span>

    - <span data-ttu-id="528cb-233">.NET Framework 4 için **Sürüm** girdisi **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4.0\Client** alt anahtarı, **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4.0\Full** altındadır. alt anahtar veya her iki alt anahtarda.</span><span class="sxs-lookup"><span data-stu-id="528cb-233">For .NET Framework 4, the **Version** entry is under the **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4.0\Client** subkey, the **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4.0\Full** subkey, or under both subkeys.</span></span>

    > [!NOTE]
    > <span data-ttu-id="528cb-234">Kayıt defterindeki **net Framework kurulum** klasörü bir noktayla başlamaz.</span><span class="sxs-lookup"><span data-stu-id="528cb-234">The **NET Framework Setup** folder in the registry does not begin with a period.</span></span>

    <span data-ttu-id="528cb-235">Aşağıdaki şekilde, .NET Framework 3,5 için alt anahtar ve **Sürüm** girişi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="528cb-235">The following figure shows the subkey and its **Version** entry for the .NET Framework 3.5.</span></span>

    <span data-ttu-id="528cb-236">![3,5 .NET Framework için kayıt defteri girişi.](./media/net-4-and-earlier.png ".NET Framework 3,5 ve önceki sürümler")</span><span class="sxs-lookup"><span data-stu-id="528cb-236">![The registry entry for the .NET Framework 3.5.](./media/net-4-and-earlier.png ".NET Framework 3.5 and earlier versions")</span></span>

<a name="net_c"></a>

### <a name="query-the-registry-using-code-older-framework-versions"></a><span data-ttu-id="528cb-237">Kodu kullanarak kayıt defterini sorgulama (eski Framework sürümleri)</span><span class="sxs-lookup"><span data-stu-id="528cb-237">Query the registry using code (older framework versions)</span></span>

<span data-ttu-id="528cb-238">Windows kayıt defterindeki **HKEY_LOCAL_MACHINE\Software\Microsoft\NET Framework Setup\NDP** alt anahtarına erişmek için <xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType> sınıfını kullanın.</span><span class="sxs-lookup"><span data-stu-id="528cb-238">Use the <xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType> class to access the **HKEY_LOCAL_MACHINE\Software\Microsoft\NET Framework Setup\NDP** subkey in the Windows registry.</span></span>

<span data-ttu-id="528cb-239">Aşağıdaki örnek, yüklü .NET Framework 1 ila 4 sürümü bulur:</span><span class="sxs-lookup"><span data-stu-id="528cb-239">The following example finds the .NET Framework 1 through 4 versions that are installed:</span></span>

[!code-csharp[ListVersions](../../../samples/snippets/csharp/framework/migration-guide/versions-installed1.cs)]
[!code-vb[ListVersions](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed1.vb)]

## <a name="find-clr-versions"></a><span data-ttu-id="528cb-240">CLR sürümlerini bul</span><span class="sxs-lookup"><span data-stu-id="528cb-240">Find CLR versions</span></span>

<a name="clr_a"></a>

### <a name="use-clrverexe"></a><span data-ttu-id="528cb-241">Clrver. exe kullanma</span><span class="sxs-lookup"><span data-stu-id="528cb-241">Use Clrver.exe</span></span>

<span data-ttu-id="528cb-242">Clr [Sürüm aracı 'nı (Clrver. exe)](../tools/clrver-exe-clr-version-tool.md) kullanarak bir bılgısayarda hangi CLR sürümlerinin yüklü olduğunu belirleme:</span><span class="sxs-lookup"><span data-stu-id="528cb-242">Use the [CLR Version tool (Clrver.exe)](../tools/clrver-exe-clr-version-tool.md) to determine which versions of the CLR are installed on a computer:</span></span>

- <span data-ttu-id="528cb-243">[Visual Studio için Geliştirici Komut İstemi](../tools/developer-command-prompt-for-vs.md)`clrver`girin.</span><span class="sxs-lookup"><span data-stu-id="528cb-243">From a [Developer Command Prompt for Visual Studio](../tools/developer-command-prompt-for-vs.md), enter `clrver`.</span></span>

    <span data-ttu-id="528cb-244">Örnek çıktı:</span><span class="sxs-lookup"><span data-stu-id="528cb-244">Sample output:</span></span>

    ```console
    Versions installed on the machine:
    v2.0.50727
    v4.0.30319
    ```

<a name="clr_b"></a>

### <a name="use-the-environment-class"></a><span data-ttu-id="528cb-245">Ortam sınıfını kullanma</span><span class="sxs-lookup"><span data-stu-id="528cb-245">Use the Environment class</span></span>

> [!IMPORTANT]
> <span data-ttu-id="528cb-246">.NET Framework 4,5 ve sonraki sürümlerinde, CLR sürümünü algılamak için <xref:System.Environment.Version%2A?displayProperty=nameWithType> özelliğini kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="528cb-246">For the .NET Framework 4.5 and later versions, don't use the <xref:System.Environment.Version%2A?displayProperty=nameWithType> property to detect the version of the CLR.</span></span> <span data-ttu-id="528cb-247">Bunun yerine, kayıt defterini, [kodla .NET Framework sürümler 4,5 ve sonraki kısımlarında](#net_d)açıklandığı gibi sorgulayın.</span><span class="sxs-lookup"><span data-stu-id="528cb-247">Instead, query the registry as described in [Find .NET Framework versions 4.5 and later with code](#net_d).</span></span>

1. <span data-ttu-id="528cb-248"><xref:System.Version> nesnesini almak için <xref:System.Environment.Version?displayProperty=nameWithType> özelliğini sorgulayın.</span><span class="sxs-lookup"><span data-stu-id="528cb-248">Query the <xref:System.Environment.Version?displayProperty=nameWithType> property to retrieve a <xref:System.Version> object.</span></span>

    <span data-ttu-id="528cb-249">Döndürülen `System.Version` nesnesi şu anda kodu yürüten çalışma zamanının sürümünü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="528cb-249">The returned `System.Version` object identifies the version of the runtime that's currently executing the code.</span></span> <span data-ttu-id="528cb-250">Derleme sürümlerini veya çalışma zamanının bilgisayarda yüklü olabilecek diğer sürümlerini döndürmez.</span><span class="sxs-lookup"><span data-stu-id="528cb-250">It doesn't return assembly versions or other versions of the runtime that may have been installed on the computer.</span></span>

    <span data-ttu-id="528cb-251">.NET Framework sürümleri 4, 4,5, 4.5.1 ve 4.5.2 için, döndürülen <xref:System.Version> nesnesinin dize temsili 4.0.30319 biçimindedir. *xxxxx*, *xxxxx* 42000 ' den küçük.</span><span class="sxs-lookup"><span data-stu-id="528cb-251">For the .NET Framework versions 4, 4.5, 4.5.1, and 4.5.2, the string representation of the returned <xref:System.Version> object has the form 4.0.30319.*xxxxx*, where *xxxxx* is less than 42000.</span></span> <span data-ttu-id="528cb-252">.NET Framework 4,6 ve sonraki sürümlerinde, 4.0.30319.42000 biçiminde olur.</span><span class="sxs-lookup"><span data-stu-id="528cb-252">For the .NET Framework 4.6 and later versions, it has the form 4.0.30319.42000.</span></span>

2. <span data-ttu-id="528cb-253">`Version` nesnesine sahip olduktan sonra aşağıdaki gibi sorgulayın:</span><span class="sxs-lookup"><span data-stu-id="528cb-253">After you have the `Version` object, query it as follows:</span></span>

   - <span data-ttu-id="528cb-254">Ana yayın tanımlayıcısı için (örneğin, sürüm 4,0 için *4* ) <xref:System.Version.Major%2A?displayProperty=nameWithType> özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="528cb-254">For the major release identifier (for example, *4* for version 4.0), use the <xref:System.Version.Major%2A?displayProperty=nameWithType> property.</span></span>

   - <span data-ttu-id="528cb-255">Küçük yayın tanımlayıcısı için (örneğin, sürüm 4,0 için *0* ) <xref:System.Version.Minor%2A?displayProperty=nameWithType> özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="528cb-255">For the minor release identifier (for example, *0* for version 4.0), use the <xref:System.Version.Minor%2A?displayProperty=nameWithType> property.</span></span>

   - <span data-ttu-id="528cb-256">Tüm sürüm dizesi için (örneğin, *4.0.30319.18010*) <xref:System.Version.ToString%2A?displayProperty=nameWithType> yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="528cb-256">For the entire version string (for example, *4.0.30319.18010*), use the <xref:System.Version.ToString%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="528cb-257">Bu yöntem, kodu yürüten çalışma zamanının sürümünü yansıtan tek bir değer döndürür.</span><span class="sxs-lookup"><span data-stu-id="528cb-257">This method returns a single value that reflects the version of the runtime that's executing the code.</span></span> <span data-ttu-id="528cb-258">Bu, bilgisayarda yüklü olabilecek derleme sürümlerini veya diğer çalışma zamanı sürümlerini döndürmez.</span><span class="sxs-lookup"><span data-stu-id="528cb-258">It doesn't return assembly versions or other runtime versions that may be installed on the computer.</span></span>

<span data-ttu-id="528cb-259">Aşağıdaki örnek CLR sürüm bilgilerini almak için <xref:System.Environment.Version%2A?displayProperty=nameWithType> özelliğini kullanır:</span><span class="sxs-lookup"><span data-stu-id="528cb-259">The following example uses the <xref:System.Environment.Version%2A?displayProperty=nameWithType> property to retrieve CLR version information:</span></span>

[!code-csharp[ListVersions](../../../samples/snippets/csharp/framework/migration-guide/versions-installed2.cs)]
[!code-vb[ListVersions](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed2.vb)]

## <a name="see-also"></a><span data-ttu-id="528cb-260">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="528cb-260">See also</span></span>

- [<span data-ttu-id="528cb-261">Nasıl yapılır: hangi .NET Framework güncelleştirmelerinin yükleneceğini belirleme</span><span class="sxs-lookup"><span data-stu-id="528cb-261">How to: Determine which .NET Framework updates are installed</span></span>](how-to-determine-which-net-framework-updates-are-installed.md)
- [<span data-ttu-id="528cb-262">Geliştiriciler için .NET Framework yüklemesi</span><span class="sxs-lookup"><span data-stu-id="528cb-262">Install the .NET Framework for developers</span></span>](../install/guide-for-developers.md)
- [<span data-ttu-id="528cb-263">.NET Framework sürümleri ve bağımlılıklar</span><span class="sxs-lookup"><span data-stu-id="528cb-263">.NET Framework versions and dependencies</span></span>](versions-and-dependencies.md)
