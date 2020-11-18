---
title: Hangi .NET Framework sürümlerinin yüklü olduğunu belirleme
description: Windows kayıt defterini sorgulayarak bir makineye hangi .NET Framework sürümlerinin yükleneceğini algılamak için kod, regedit.exe veya PowerShell kullanın.
ms.date: 02/03/2020
dev_langs:
- csharp
- vb
helpviewer_keywords:
- versions, determining for .NET Framework
- .NET Framework, determining version
ms.assetid: 40a67826-e4df-4f59-a651-d9eb0fdc755d
ms.openlocfilehash: fe28a4bf4a5432d6e33b7ad3238c1d7c0d4e7a84
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94831370"
---
# <a name="how-to-determine-which-net-framework-versions-are-installed"></a><span data-ttu-id="bf852-103">Nasıl yapılır: hangi .NET Framework sürümlerinin yüklendiğini belirleme</span><span class="sxs-lookup"><span data-stu-id="bf852-103">How to: Determine which .NET Framework versions are installed</span></span>

<span data-ttu-id="bf852-104">Kullanıcılar, .NET Framework birden çok sürümünü bilgisayarlarına [yükleyebilir](../install/index.md) ve çalıştırabilir.</span><span class="sxs-lookup"><span data-stu-id="bf852-104">Users can [install](../install/index.md) and run multiple versions of .NET Framework on their computers.</span></span> <span data-ttu-id="bf852-105">Uygulamanızı geliştirirken veya dağıtırken, kullanıcının bilgisayarında hangi .NET Framework sürümlerinin yüklü olduğunu bilmeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="bf852-105">When you develop or deploy your app, you might need to know which .NET Framework versions are installed on the user's computer.</span></span> <span data-ttu-id="bf852-106">Kayıt defteri, bilgisayarda yüklü .NET Framework sürümlerinin bir listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="bf852-106">The registry contains a list of the versions of .NET Framework installed on the computer.</span></span>

<span data-ttu-id="bf852-107">.NET Framework, sürümü ayrı olan iki ana bileşenden oluşur:</span><span class="sxs-lookup"><span data-stu-id="bf852-107">.NET Framework consists of two main components, which are versioned separately:</span></span>

- <span data-ttu-id="bf852-108">Uygulamalarınız için işlevsellik sağlayan tür ve kaynak koleksiyonları olan derlemeler kümesi.</span><span class="sxs-lookup"><span data-stu-id="bf852-108">A set of assemblies, which are collections of types and resources that provide the functionality for your apps.</span></span> <span data-ttu-id="bf852-109">.NET Framework ve derlemeler aynı sürüm numarasını paylaşır.</span><span class="sxs-lookup"><span data-stu-id="bf852-109">.NET Framework and the assemblies share the same version number.</span></span> <span data-ttu-id="bf852-110">Örneğin, .NET Framework sürümler 4,5, 4.6.1 ve 4.7.2 ' i içerir.</span><span class="sxs-lookup"><span data-stu-id="bf852-110">For example, .NET Framework versions include 4.5, 4.6.1, and 4.7.2.</span></span>

- <span data-ttu-id="bf852-111">Uygulamanızın kodunu yöneten ve yürüten ortak dil çalışma zamanı (CLR).</span><span class="sxs-lookup"><span data-stu-id="bf852-111">The common language runtime (CLR), which manages and executes your app's code.</span></span> <span data-ttu-id="bf852-112">Tek bir CLR sürümü genellikle birden çok .NET Framework sürümü destekler.</span><span class="sxs-lookup"><span data-stu-id="bf852-112">A single CLR version typically supports multiple .NET Framework versions.</span></span> <span data-ttu-id="bf852-113">Örneğin, CLR sürüm 4.0.30319. *xxxxx* , *xxxxx* 42000 ' den az olduğunda, 4 ile 4.5.2 arası sürüm .NET Framework destekler.</span><span class="sxs-lookup"><span data-stu-id="bf852-113">For example, CLR version 4.0.30319.*xxxxx* where *xxxxx* is less than 42000, supports .NET Framework versions 4 through 4.5.2.</span></span> <span data-ttu-id="bf852-114">4.0.30319.42000 'den büyük veya buna eşit CLR sürümü, .NET Framework 4,6 ' den başlayarak .NET Framework sürümlerini destekler.</span><span class="sxs-lookup"><span data-stu-id="bf852-114">CLR version greater than or equal to 4.0.30319.42000 supports .NET Framework versions starting with .NET Framework 4.6.</span></span>

<span data-ttu-id="bf852-115">Hangi .NET Framework sürümlerinin yüklü olduğunu algılamaya yardımcı olmak için topluluk ile korunan araçlar sunulmaktadır:</span><span class="sxs-lookup"><span data-stu-id="bf852-115">Community-maintained tools are available to help detect which .NET Framework versions are installed:</span></span>

- [https://github.com/jmalarcon/DotNetVersions](https://github.com/jmalarcon/DotNetVersions)

  <span data-ttu-id="bf852-116">.NET 2,0 komut satırı aracı.</span><span class="sxs-lookup"><span data-stu-id="bf852-116">A .NET 2.0 command-line tool.</span></span>

- [https://github.com/EliteLoser/DotNetVersionLister](https://github.com/EliteLoser/DotNetVersionLister)

  <span data-ttu-id="bf852-117">Bir PowerShell 2,0 modülü.</span><span class="sxs-lookup"><span data-stu-id="bf852-117">A PowerShell 2.0 module.</span></span>

<span data-ttu-id="bf852-118">Her bir .NET Framework sürümü için yüklü güncelleştirmeleri algılama hakkında bilgi için bkz. [nasıl yapılır: hangi .NET Framework güncelleştirmelerinin yükleneceğini belirleme](how-to-determine-which-net-framework-updates-are-installed.md).</span><span class="sxs-lookup"><span data-stu-id="bf852-118">For information about detecting the installed updates for each version of .NET Framework, see [How to: Determine which .NET Framework updates are installed](how-to-determine-which-net-framework-updates-are-installed.md).</span></span>

## <a name="detect-net-framework-45-and-later-versions"></a><span data-ttu-id="bf852-119">.NET Framework 4,5 ve sonraki sürümleri Algıla</span><span class="sxs-lookup"><span data-stu-id="bf852-119">Detect .NET Framework 4.5 and later versions</span></span>

<span data-ttu-id="bf852-120">Bir makinede yüklü .NET Framework (4,5 ve üzeri) sürümü, **HKEY_LOCAL_MACHINE \\ yazılım \\ Microsoft \\ net Framework Setup \\ NDP \\ v4 \\ Full** bölümünde kayıt defterinde listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="bf852-120">The version of .NET Framework (4.5 and later) installed on a machine is listed in the registry at **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\NET Framework Setup\\NDP\\v4\\Full**.</span></span> <span data-ttu-id="bf852-121">**Tam** alt anahtar eksikse, .NET Framework 4,5 veya üzeri yüklü değildir.</span><span class="sxs-lookup"><span data-stu-id="bf852-121">If the **Full** subkey is missing, then .NET Framework 4.5 or above isn't installed.</span></span>

> [!NOTE]
> <span data-ttu-id="bf852-122">Kayıt defteri yolundaki **net Framework kurulum** alt anahtarı bir noktayla *başlamaz.*</span><span class="sxs-lookup"><span data-stu-id="bf852-122">The **NET Framework Setup** subkey in the registry path does *not* begin with a period.</span></span>

<span data-ttu-id="bf852-123">Kayıt defterindeki **Release** REG_DWORD değeri, yüklü .NET Framework sürümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="bf852-123">The **Release** REG_DWORD value in the registry represents the version of .NET Framework installed.</span></span>

<a name="version_table"></a>

| <span data-ttu-id="bf852-124">.NET Framework sürümü</span><span class="sxs-lookup"><span data-stu-id="bf852-124">.NET Framework version</span></span> | <span data-ttu-id="bf852-125">**Yayın** değeri</span><span class="sxs-lookup"><span data-stu-id="bf852-125">Value of **Release**</span></span> |
| ---------------------- | -------------------------- |
| <span data-ttu-id="bf852-126">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="bf852-126">.NET Framework 4.5</span></span>     | <span data-ttu-id="bf852-127">Tüm Windows işletim sistemleri: 378389</span><span class="sxs-lookup"><span data-stu-id="bf852-127">All Windows operating systems: 378389</span></span> |
| <span data-ttu-id="bf852-128">.NET Framework 4.5.1</span><span class="sxs-lookup"><span data-stu-id="bf852-128">.NET Framework 4.5.1</span></span>   | <span data-ttu-id="bf852-129">Windows 8.1 ve Windows Server 2012 R2 'de: 378675</span><span class="sxs-lookup"><span data-stu-id="bf852-129">On Windows 8.1 and Windows Server 2012 R2: 378675</span></span><br /><span data-ttu-id="bf852-130">Diğer tüm Windows işletim sistemlerinde: 378758</span><span class="sxs-lookup"><span data-stu-id="bf852-130">On all other Windows operating systems: 378758</span></span> |
| <span data-ttu-id="bf852-131">.NET Framework 4.5.2</span><span class="sxs-lookup"><span data-stu-id="bf852-131">.NET Framework 4.5.2</span></span>   | <span data-ttu-id="bf852-132">Tüm Windows işletim sistemleri: 379893</span><span class="sxs-lookup"><span data-stu-id="bf852-132">All Windows operating systems: 379893</span></span> |
| <span data-ttu-id="bf852-133">.NET Framework 4.6</span><span class="sxs-lookup"><span data-stu-id="bf852-133">.NET Framework 4.6</span></span>     | <span data-ttu-id="bf852-134">Windows 10:393295 ' de</span><span class="sxs-lookup"><span data-stu-id="bf852-134">On Windows 10: 393295</span></span><br /><span data-ttu-id="bf852-135">Diğer tüm Windows işletim sistemlerinde: 393297</span><span class="sxs-lookup"><span data-stu-id="bf852-135">On all other Windows operating systems: 393297</span></span> |
| <span data-ttu-id="bf852-136">.NET Framework 4.6.1</span><span class="sxs-lookup"><span data-stu-id="bf852-136">.NET Framework 4.6.1</span></span>   | <span data-ttu-id="bf852-137">Windows 10 Kasım güncelleştirme sistemlerinde: 394254</span><span class="sxs-lookup"><span data-stu-id="bf852-137">On Windows 10 November Update systems: 394254</span></span><br /><span data-ttu-id="bf852-138">Diğer tüm Windows işletim sistemlerinde (Windows 10 dahil): 394271</span><span class="sxs-lookup"><span data-stu-id="bf852-138">On all other Windows operating systems (including Windows 10): 394271</span></span> |
| <span data-ttu-id="bf852-139">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="bf852-139">.NET Framework 4.6.2</span></span>   | <span data-ttu-id="bf852-140">Windows 10 yıldönümü güncelleştirmesi ve Windows Server 2016:394802</span><span class="sxs-lookup"><span data-stu-id="bf852-140">On Windows 10 Anniversary Update and Windows Server 2016: 394802</span></span><br /><span data-ttu-id="bf852-141">Diğer tüm Windows işletim sistemlerinde (diğer Windows 10 işletim sistemleri dahil): 394806</span><span class="sxs-lookup"><span data-stu-id="bf852-141">On all other Windows operating systems (including other Windows 10 operating systems): 394806</span></span> |
| <span data-ttu-id="bf852-142"> .NET Framework 4.7</span><span class="sxs-lookup"><span data-stu-id="bf852-142">.NET Framework 4.7</span></span>     | <span data-ttu-id="bf852-143">Windows 10 Creators Update üzerinde: 460798</span><span class="sxs-lookup"><span data-stu-id="bf852-143">On Windows 10 Creators Update: 460798</span></span><br /><span data-ttu-id="bf852-144">Diğer tüm Windows işletim sistemlerinde (diğer Windows 10 işletim sistemleri dahil): 460805</span><span class="sxs-lookup"><span data-stu-id="bf852-144">On all other Windows operating systems (including other Windows 10 operating systems): 460805</span></span> |
| <span data-ttu-id="bf852-145">.NET Framework 4.7.1</span><span class="sxs-lookup"><span data-stu-id="bf852-145">.NET Framework 4.7.1</span></span>   | <span data-ttu-id="bf852-146">Windows 10 Fall Creators Update ve Windows Server, sürüm 1709:461308</span><span class="sxs-lookup"><span data-stu-id="bf852-146">On Windows 10 Fall Creators Update and Windows Server, version 1709: 461308</span></span><br/><span data-ttu-id="bf852-147">Diğer tüm Windows işletim sistemlerinde (diğer Windows 10 işletim sistemleri dahil): 461310</span><span class="sxs-lookup"><span data-stu-id="bf852-147">On all other Windows operating systems (including other Windows 10 operating systems): 461310</span></span> |
| <span data-ttu-id="bf852-148"> .NET Framework 4.7.2</span><span class="sxs-lookup"><span data-stu-id="bf852-148">.NET Framework 4.7.2</span></span>   | <span data-ttu-id="bf852-149">Windows 10 Nisan 2018 güncelleştirmesi ve Windows Server, sürüm 1803:461808</span><span class="sxs-lookup"><span data-stu-id="bf852-149">On Windows 10 April 2018 Update and Windows Server, version 1803: 461808</span></span><br/><span data-ttu-id="bf852-150">Windows 10 Nisan 2018 güncelleştirmesi ve Windows Server, sürüm 1803 dışındaki tüm Windows işletim sistemlerinde: 461814</span><span class="sxs-lookup"><span data-stu-id="bf852-150">On all Windows operating systems other than Windows 10 April 2018 Update and Windows Server, version 1803: 461814</span></span> |
| <span data-ttu-id="bf852-151"> .NET Framework 4.8</span><span class="sxs-lookup"><span data-stu-id="bf852-151">.NET Framework 4.8</span></span>     | <span data-ttu-id="bf852-152">Windows 10 Mayıs 2019 güncelleştirmesi ve Windows 10 Kasım 2019 güncelleştirmesi: 528040</span><span class="sxs-lookup"><span data-stu-id="bf852-152">On Windows 10 May 2019 Update and Windows 10 November 2019 Update: 528040</span></span><br/><span data-ttu-id="bf852-153">Windows 10 Mayıs 2020 güncelleştirmesi ve Windows 10 Ekim 2020 güncelleştirmesi: 528372</span><span class="sxs-lookup"><span data-stu-id="bf852-153">On Windows 10 May 2020 Update and Windows 10 October 2020 Update: 528372</span></span><br/><span data-ttu-id="bf852-154">Diğer tüm Windows işletim sistemlerinde (diğer Windows 10 işletim sistemleri dahil): 528049</span><span class="sxs-lookup"><span data-stu-id="bf852-154">On all other Windows operating systems (including other Windows 10 operating systems): 528049</span></span> |

### <a name="minimum-version"></a><span data-ttu-id="bf852-155">En düşük sürüm</span><span class="sxs-lookup"><span data-stu-id="bf852-155">Minimum version</span></span>

<span data-ttu-id="bf852-156">*En düşük* .NET Framework sürümünün mevcut olup olmadığını anlamak için, aşağıdaki tabloda listelenen değere eşit veya ondan daha büyük bir **Sürüm** REG_DWORD değeri denetleyin.</span><span class="sxs-lookup"><span data-stu-id="bf852-156">To determine whether a *minimum* version of .NET Framework is present, check for a **Release** REG_DWORD value that's greater than or equal to the corresponding value listed in the following table.</span></span> <span data-ttu-id="bf852-157">Örneğin, uygulamanız .NET Framework 4,8 veya sonraki bir sürümde çalışıyorsa, 528040 ' *e eşit veya daha büyük* olan bir **yayın** REG_DWORD değeri için test edin.</span><span class="sxs-lookup"><span data-stu-id="bf852-157">For example, if your application runs under .NET Framework 4.8 or a later version, test for a **Release** REG_DWORD value that's *greater than or equal to* 528040.</span></span>

| <span data-ttu-id="bf852-158">.NET Framework sürümü</span><span class="sxs-lookup"><span data-stu-id="bf852-158">.NET Framework version</span></span> | <span data-ttu-id="bf852-159">En küçük değer</span><span class="sxs-lookup"><span data-stu-id="bf852-159">Minimum value</span></span> |
| ---------------------- | ------------- |
| <span data-ttu-id="bf852-160">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="bf852-160">.NET Framework 4.5</span></span>     | <span data-ttu-id="bf852-161">378389</span><span class="sxs-lookup"><span data-stu-id="bf852-161">378389</span></span> |
| <span data-ttu-id="bf852-162">.NET Framework 4.5.1</span><span class="sxs-lookup"><span data-stu-id="bf852-162">.NET Framework 4.5.1</span></span>   | <span data-ttu-id="bf852-163">378675</span><span class="sxs-lookup"><span data-stu-id="bf852-163">378675</span></span> |
| <span data-ttu-id="bf852-164">.NET Framework 4.5.2</span><span class="sxs-lookup"><span data-stu-id="bf852-164">.NET Framework 4.5.2</span></span>   | <span data-ttu-id="bf852-165">379893</span><span class="sxs-lookup"><span data-stu-id="bf852-165">379893</span></span> |
| <span data-ttu-id="bf852-166">.NET Framework 4.6</span><span class="sxs-lookup"><span data-stu-id="bf852-166">.NET Framework 4.6</span></span>     | <span data-ttu-id="bf852-167">393295</span><span class="sxs-lookup"><span data-stu-id="bf852-167">393295</span></span> |
| <span data-ttu-id="bf852-168">.NET Framework 4.6.1</span><span class="sxs-lookup"><span data-stu-id="bf852-168">.NET Framework 4.6.1</span></span>   | <span data-ttu-id="bf852-169">394254</span><span class="sxs-lookup"><span data-stu-id="bf852-169">394254</span></span> |
| <span data-ttu-id="bf852-170">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="bf852-170">.NET Framework 4.6.2</span></span>   | <span data-ttu-id="bf852-171">394802</span><span class="sxs-lookup"><span data-stu-id="bf852-171">394802</span></span> |
| <span data-ttu-id="bf852-172"> .NET Framework 4.7</span><span class="sxs-lookup"><span data-stu-id="bf852-172">.NET Framework 4.7</span></span>     | <span data-ttu-id="bf852-173">460798</span><span class="sxs-lookup"><span data-stu-id="bf852-173">460798</span></span> |
| <span data-ttu-id="bf852-174">.NET Framework 4.7.1</span><span class="sxs-lookup"><span data-stu-id="bf852-174">.NET Framework 4.7.1</span></span>   | <span data-ttu-id="bf852-175">461308</span><span class="sxs-lookup"><span data-stu-id="bf852-175">461308</span></span> |
| <span data-ttu-id="bf852-176"> .NET Framework 4.7.2</span><span class="sxs-lookup"><span data-stu-id="bf852-176">.NET Framework 4.7.2</span></span>   | <span data-ttu-id="bf852-177">461808</span><span class="sxs-lookup"><span data-stu-id="bf852-177">461808</span></span> |
| <span data-ttu-id="bf852-178"> .NET Framework 4.8</span><span class="sxs-lookup"><span data-stu-id="bf852-178">.NET Framework 4.8</span></span>     | <span data-ttu-id="bf852-179">528040</span><span class="sxs-lookup"><span data-stu-id="bf852-179">528040</span></span> |

### <a name="use-registry-editor"></a><span data-ttu-id="bf852-180">Kayıt Defteri Düzenleyicisi 'Ni kullan</span><span class="sxs-lookup"><span data-stu-id="bf852-180">Use Registry Editor</span></span>

01. <span data-ttu-id="bf852-181">**Başlat** menüsünde, **Çalıştır**' ı seçin, *Regedit*' i girin ve **Tamam**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="bf852-181">From the **Start** menu, choose **Run**, enter *regedit*, and then select **OK**.</span></span>

   <span data-ttu-id="bf852-182">(Regedit çalıştırmak için yönetici kimlik bilgilerine sahip olmanız gerekir.)</span><span class="sxs-lookup"><span data-stu-id="bf852-182">(You must have administrative credentials to run regedit.)</span></span>

01. <span data-ttu-id="bf852-183">Kayıt Defteri Düzenleyicisi 'nde, aşağıdaki alt anahtarı açın: **\\ yazılım \\ Microsoft \\ net Framework Setup \\ NDP \\ v4 \\ Full HKEY_LOCAL_MACHINE**.</span><span class="sxs-lookup"><span data-stu-id="bf852-183">In the Registry Editor, open the following subkey: **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\NET Framework Setup\\NDP\\v4\\Full**.</span></span> <span data-ttu-id="bf852-184">**Tam** alt anahtar yoksa, .NET Framework 4,5 veya sonraki bir sürümü yüklü değildir.</span><span class="sxs-lookup"><span data-stu-id="bf852-184">If the **Full** subkey isn't present, then you don't have .NET Framework 4.5 or later installed.</span></span>

01. <span data-ttu-id="bf852-185">**Yayın** adlı REG_DWORD girişi olup olmadığını denetleyin.</span><span class="sxs-lookup"><span data-stu-id="bf852-185">Check for a REG_DWORD entry named **Release**.</span></span> <span data-ttu-id="bf852-186">Varsa, .NET Framework 4,5 veya sonraki bir sürümü yüklemiş olursunuz.</span><span class="sxs-lookup"><span data-stu-id="bf852-186">If it exists, then you have .NET Framework 4.5 or later installed.</span></span> <span data-ttu-id="bf852-187">Değeri, .NET Framework belirli bir sürümüne karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="bf852-187">Its value corresponds to a particular version of .NET Framework.</span></span> <span data-ttu-id="bf852-188">Aşağıdaki şekilde, örneğin, **Sürüm** girişinin değeri 528040 ' dir. bu, .NET Framework 4,8 ' in sürüm anahtarıdır.</span><span class="sxs-lookup"><span data-stu-id="bf852-188">In the following figure, for example, the value of the **Release** entry is 528040, which is the release key for .NET Framework 4.8.</span></span>

   ![.NET Framework 4,5 için kayıt defteri girişi](./media/clr-installdir.png )

### <a name="use-powershell-to-check-for-a-minimum-version"></a><span data-ttu-id="bf852-190">En düşük sürümü denetlemek için PowerShell 'i kullanma</span><span class="sxs-lookup"><span data-stu-id="bf852-190">Use PowerShell to check for a minimum version</span></span>

<span data-ttu-id="bf852-191">PowerShell komutlarını, **HKEY_LOCAL_MACHINE \\ yazılım \\ Microsoft \\ net Framework Setup \\ NDP \\ v4 \\ Full** alt anahtarının **yayın** girişinin değerini denetlemek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="bf852-191">Use PowerShell commands to check the value of the **Release** entry of the **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\NET Framework Setup\\NDP\\v4\\Full** subkey.</span></span>

<span data-ttu-id="bf852-192">Aşağıdaki örnekler, .NET Framework 4.6.2 veya sonraki bir sürümün yüklenip yüklenmediğini anlamak için **yayın** girişinin değerini denetler.</span><span class="sxs-lookup"><span data-stu-id="bf852-192">The following examples check the value of the **Release** entry to determine whether .NET Framework 4.6.2 or later is installed.</span></span> <span data-ttu-id="bf852-193">Bu kod `True` , yüklenmişse ve `False` Aksi takdirde döndürülür.</span><span class="sxs-lookup"><span data-stu-id="bf852-193">This code returns `True` if it's installed and `False` otherwise.</span></span>

```powershell
(Get-ItemProperty "HKLM:SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full").Release -ge 394802
```

### <a name="query-the-registry-using-code"></a><span data-ttu-id="bf852-194">Kodu kullanarak kayıt defterini sorgulama</span><span class="sxs-lookup"><span data-stu-id="bf852-194">Query the registry using code</span></span>

01. <span data-ttu-id="bf852-195"><xref:Microsoft.Win32.RegistryKey.OpenBaseKey%2A?displayProperty=nameWithType> <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A?displayProperty=nameWithType> Windows kayıt defterindeki **HKEY_LOCAL_MACHINE \\ Software \\ Microsoft \\ net Framework Setup \\ NDP \\ v4 \\ Full** alt anahtarına erişmek için ve yöntemlerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="bf852-195">Use the <xref:Microsoft.Win32.RegistryKey.OpenBaseKey%2A?displayProperty=nameWithType> and <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A?displayProperty=nameWithType> methods to access the **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\NET Framework Setup\\NDP\\v4\\Full** subkey in the Windows registry.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="bf852-196">Çalıştırdığınız uygulama 32-bit ise ve 64 bit Windows 'da çalışıyorsa, kayıt defteri yolları daha önce listelenenden farklı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="bf852-196">If the app you're running is 32-bit and running in 64-bit Windows, the registry paths will be different than previously listed.</span></span> <span data-ttu-id="bf852-197">64 bit kayıt defteri **HKEY_LOCAL_MACHINE \\ Software \\ Wow6432Node \\** alt anahtarında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="bf852-197">The 64-bit registry is available in the **HKEY_LOCAL_MACHINE\\SOFTWARE\\Wow6432Node\\** subkey.</span></span> <span data-ttu-id="bf852-198">Örneğin, .NET Framework 4,5 için kayıt defteri alt anahtarı **HKEY_LOCAL_MACHINE \\ Software \\ Wow6432Node \\ Microsoft \\ net Framework Setup \\ NDP \\ v4 \\ Full**' dır.</span><span class="sxs-lookup"><span data-stu-id="bf852-198">For example, the registry subkey for .NET Framework 4.5 is **HKEY_LOCAL_MACHINE\\SOFTWARE\\Wow6432Node\\Microsoft\\NET Framework Setup\\NDP\\v4\\Full**.</span></span>

01. <span data-ttu-id="bf852-199">Yüklü sürümü öğrenmek için **yayın** REG_DWORD değerini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="bf852-199">Check the **Release** REG_DWORD value to determine the installed version.</span></span> <span data-ttu-id="bf852-200">İleriye dönük olarak uyumlu olması için [.NET Framework sürüm tablosunda](#version_table)listelenen değerden daha büyük veya ona eşit bir değer olup olmadığını kontrol edin.</span><span class="sxs-lookup"><span data-stu-id="bf852-200">To be forward-compatible, check for a value greater than or equal to the value listed in the [.NET Framework version table](#version_table).</span></span>

<span data-ttu-id="bf852-201">Aşağıdaki örnek, yüklü .NET Framework 4.5-4.8 sürümlerini bulmak için kayıt defterindeki **yayın** girişinin değerini denetler:</span><span class="sxs-lookup"><span data-stu-id="bf852-201">The following example checks the value of the **Release** entry in the registry to find the versions of .NET Framework 4.5-4.8 that are installed:</span></span>

:::code language="csharp" source="snippets/csharp/versions-installed.cs" id="2":::

:::code language="vb" source="snippets/visual-basic/versions-installed.vb" id="2":::

<span data-ttu-id="bf852-202">Örneğin, aşağıdaki gibi bir çıktı görüntülenir:</span><span class="sxs-lookup"><span data-stu-id="bf852-202">The example displays output like the following:</span></span>

```output
.NET Framework Version: 4.6.1
```

<span data-ttu-id="bf852-203">Bu örnek sürüm denetimi için önerilen yöntemi izler:</span><span class="sxs-lookup"><span data-stu-id="bf852-203">This example follows the recommended practice for version checking:</span></span>

- <span data-ttu-id="bf852-204">**Yayın** girişi değerinin bilinen yayın anahtarlarının değerinden *büyük veya* bu değere eşit olup olmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="bf852-204">It checks whether the value of the **Release** entry is *greater than or equal to* the value of the known release keys.</span></span>
- <span data-ttu-id="bf852-205">En son sürümden en eski sürüme sırayla kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="bf852-205">It checks in order from most recent version to earliest version.</span></span>

## <a name="detect-net-framework-10-through-40"></a><span data-ttu-id="bf852-206">1,0 ile 4,0 arasındaki .NET Framework Algıla</span><span class="sxs-lookup"><span data-stu-id="bf852-206">Detect .NET Framework 1.0 through 4.0</span></span>

<span data-ttu-id="bf852-207">1,1 ' den 4,0 ' e .NET Framework her sürümü **HKEY_LOCAL_MACHINE \\ Software \\ Microsoft \\ net Framework Setup \\ NDP** alt anahtarı olarak listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="bf852-207">Each version of .NET Framework from 1.1 to 4.0 is listed as a subkey at **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\NET Framework Setup\\NDP**.</span></span> <span data-ttu-id="bf852-208">Aşağıdaki tabloda her bir .NET Framework sürümünün yolu listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="bf852-208">The following table lists the path to each .NET Framework version.</span></span> <span data-ttu-id="bf852-209">Çoğu sürümde, **Install** `1` Bu sürümün yüklü olduğunu göstermek için bir Install REG_DWORD değeri vardır.</span><span class="sxs-lookup"><span data-stu-id="bf852-209">For most versions, there's an **Install** REG_DWORD value of `1` to indicate this version is installed.</span></span> <span data-ttu-id="bf852-210">Bu alt anahtarlarda, sürüm dizesi içeren bir **sürüm** REG_SZ değeri de vardır.</span><span class="sxs-lookup"><span data-stu-id="bf852-210">In these subkeys, there's also a **Version** REG_SZ value that contains a version string.</span></span>

> [!NOTE]
> <span data-ttu-id="bf852-211">Kayıt defteri yolundaki **net Framework kurulum** alt anahtarı bir noktayla *başlamaz.*</span><span class="sxs-lookup"><span data-stu-id="bf852-211">The **NET Framework Setup** subkey in the registry path does *not* begin with a period.</span></span>

| <span data-ttu-id="bf852-212">Framework sürümü</span><span class="sxs-lookup"><span data-stu-id="bf852-212">Framework Version</span></span>  | <span data-ttu-id="bf852-213">Kayıt defteri alt anahtarı</span><span class="sxs-lookup"><span data-stu-id="bf852-213">Registry Subkey</span></span> | <span data-ttu-id="bf852-214">Değer</span><span class="sxs-lookup"><span data-stu-id="bf852-214">Value</span></span> |
| ------------------ | --------------- | ----- |
| <span data-ttu-id="bf852-215">1,0</span><span class="sxs-lookup"><span data-stu-id="bf852-215">1.0</span></span>                | <span data-ttu-id="bf852-216">**HKLM \\ Software \\ Microsoft \\ . NETFramework \\ ilkesi \\ v 1.0 \\ 3705**</span><span class="sxs-lookup"><span data-stu-id="bf852-216">**HKLM\\Software\\Microsoft\\.NETFramework\\Policy\\v1.0\\3705**</span></span>     | <span data-ttu-id="bf852-217">**Yüklemesi** REG_SZ eşittir `1`</span><span class="sxs-lookup"><span data-stu-id="bf852-217">**Install** REG_SZ equals `1`</span></span> |
| <span data-ttu-id="bf852-218">1.1</span><span class="sxs-lookup"><span data-stu-id="bf852-218">1.1</span></span>                | <span data-ttu-id="bf852-219">**HKLM \\ Software \\ Microsoft \\ net Framework Setup \\ NDP \\ v 1.1.4322**</span><span class="sxs-lookup"><span data-stu-id="bf852-219">**HKLM\\Software\\Microsoft\\NET Framework Setup\\NDP\\v1.1.4322**</span></span>   | <span data-ttu-id="bf852-220">**Yüklemesi** REG_DWORD eşittir `1`</span><span class="sxs-lookup"><span data-stu-id="bf852-220">**Install** REG_DWORD equals `1`</span></span> |
| <span data-ttu-id="bf852-221">2,0</span><span class="sxs-lookup"><span data-stu-id="bf852-221">2.0</span></span>                | <span data-ttu-id="bf852-222">**HKLM \\ Software \\ Microsoft \\ net Framework Setup \\ NDP \\ v 2.0.50727**</span><span class="sxs-lookup"><span data-stu-id="bf852-222">**HKLM\\Software\\Microsoft\\NET Framework Setup\\NDP\\v2.0.50727**</span></span>  | <span data-ttu-id="bf852-223">**Yüklemesi** REG_DWORD eşittir `1`</span><span class="sxs-lookup"><span data-stu-id="bf852-223">**Install** REG_DWORD equals `1`</span></span> |
| <span data-ttu-id="bf852-224">3,0</span><span class="sxs-lookup"><span data-stu-id="bf852-224">3.0</span></span>                | <span data-ttu-id="bf852-225">**HKLM \\ Software \\ Microsoft \\ net Framework Setup \\ NDP \\ v 3.0 \\ kurulumu**</span><span class="sxs-lookup"><span data-stu-id="bf852-225">**HKLM\\Software\\Microsoft\\NET Framework Setup\\NDP\\v3.0\\Setup**</span></span> | <span data-ttu-id="bf852-226">**Installsuccess** REG_DWORD eşittir `1`</span><span class="sxs-lookup"><span data-stu-id="bf852-226">**InstallSuccess** REG_DWORD equals `1`</span></span> |
| <span data-ttu-id="bf852-227">3,5</span><span class="sxs-lookup"><span data-stu-id="bf852-227">3.5</span></span>                | <span data-ttu-id="bf852-228">**HKLM \\ Software \\ Microsoft \\ net Framework Setup \\ NDP \\ v 3.5**</span><span class="sxs-lookup"><span data-stu-id="bf852-228">**HKLM\\Software\\Microsoft\\NET Framework Setup\\NDP\\v3.5**</span></span>        | <span data-ttu-id="bf852-229">**Yüklemesi** REG_DWORD eşittir `1`</span><span class="sxs-lookup"><span data-stu-id="bf852-229">**Install** REG_DWORD equals `1`</span></span> |
| <span data-ttu-id="bf852-230">4,0 istemci profili</span><span class="sxs-lookup"><span data-stu-id="bf852-230">4.0 Client Profile</span></span> | <span data-ttu-id="bf852-231">**HKLM \\ Software \\ Microsoft \\ net Framework Setup \\ NDP \\ v4 \\ istemcisi**</span><span class="sxs-lookup"><span data-stu-id="bf852-231">**HKLM\\Software\\Microsoft\\NET Framework Setup\\NDP\\v4\\Client**</span></span>  | <span data-ttu-id="bf852-232">**Yüklemesi** REG_DWORD eşittir `1`</span><span class="sxs-lookup"><span data-stu-id="bf852-232">**Install** REG_DWORD equals `1`</span></span> |
| <span data-ttu-id="bf852-233">4,0 tam profil</span><span class="sxs-lookup"><span data-stu-id="bf852-233">4.0 Full Profile</span></span>   | <span data-ttu-id="bf852-234">**HKLM \\ Software \\ Microsoft \\ net Framework Kurulumu \\ NDP \\ v4 \\ dolu**</span><span class="sxs-lookup"><span data-stu-id="bf852-234">**HKLM\\Software\\Microsoft\\NET Framework Setup\\NDP\\v4\\Full**</span></span>    | <span data-ttu-id="bf852-235">**Yüklemesi** REG_DWORD eşittir `1`</span><span class="sxs-lookup"><span data-stu-id="bf852-235">**Install** REG_DWORD equals `1`</span></span> |

> [!IMPORTANT]
> <span data-ttu-id="bf852-236">Çalıştırdığınız uygulama 32-bit ise ve 64 bit Windows 'da çalışıyorsa, kayıt defteri yolları daha önce listelenenden farklı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="bf852-236">If the app you're running is 32-bit and running in 64-bit Windows, the registry paths will be different than previously listed.</span></span> <span data-ttu-id="bf852-237">64 bit kayıt defteri **HKEY_LOCAL_MACHINE \\ Software \\ Wow6432Node \\** alt anahtarında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="bf852-237">The 64-bit registry is available in the **HKEY_LOCAL_MACHINE\\SOFTWARE\\Wow6432Node\\** subkey.</span></span> <span data-ttu-id="bf852-238">Örneğin, .NET Framework 3,5 için kayıt defteri alt anahtarı **HKEY_LOCAL_MACHINE \\ Software \\ Wow6432Node \\ Microsoft \\ net Framework Setup \\ NDP \\ v 3.5**' dir.</span><span class="sxs-lookup"><span data-stu-id="bf852-238">For example, the registry subkey for .NET Framework 3.5 is **HKEY_LOCAL_MACHINE\\SOFTWARE\\Wow6432Node\\Microsoft\\NET Framework Setup\\NDP\\v3.5**.</span></span>

<span data-ttu-id="bf852-239">.NET Framework 1,0 alt anahtarına yönelik kayıt defteri yolunun diğerlerinden farklı olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="bf852-239">Notice that the registry path to the .NET Framework 1.0 subkey is different from the others.</span></span>

### <a name="use-registry-editor-older-framework-versions"></a><span data-ttu-id="bf852-240">Kayıt Defteri Düzenleyicisi 'Ni kullan (eski Framework sürümleri)</span><span class="sxs-lookup"><span data-stu-id="bf852-240">Use Registry Editor (older framework versions)</span></span>

01. <span data-ttu-id="bf852-241">**Başlat** menüsünde, **Çalıştır**' ı seçin, *Regedit*' i girin ve **Tamam**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="bf852-241">From the **Start** menu, choose **Run**, enter *regedit*, and then select **OK**.</span></span>

    <span data-ttu-id="bf852-242">Regedit 'i çalıştırmak için yönetici kimlik bilgilerine sahip olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="bf852-242">You must have administrative credentials to run regedit.</span></span>

01. <span data-ttu-id="bf852-243">Denetlemek istediğiniz sürümle eşleşen alt anahtarı açın.</span><span class="sxs-lookup"><span data-stu-id="bf852-243">Open the subkey that matches the version you want to check.</span></span> <span data-ttu-id="bf852-244">[.NET Framework 1,0 ile 4,0 arasında algılama](#detect-net-framework-10-through-40) bölümünde bulunan tabloyu kullanın.</span><span class="sxs-lookup"><span data-stu-id="bf852-244">Use the table in the [Detect .NET Framework 1.0 through 4.0](#detect-net-framework-10-through-40) section.</span></span>

    <span data-ttu-id="bf852-245">Aşağıdaki şekilde, .NET Framework 3,5 için alt anahtar ve **Sürüm** değeri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="bf852-245">The following figure shows the subkey and its **Version** value for .NET Framework 3.5.</span></span>

    <span data-ttu-id="bf852-246">![.NET Framework 3,5 için kayıt defteri girişi.](./media/net-4-and-earlier.png ".NET Framework 3,5 ve önceki sürümler")</span><span class="sxs-lookup"><span data-stu-id="bf852-246">![The registry entry for .NET Framework 3.5.](./media/net-4-and-earlier.png ".NET Framework 3.5 and earlier versions")</span></span>

### <a name="query-the-registry-using-code-older-framework-versions"></a><span data-ttu-id="bf852-247">Kodu kullanarak kayıt defterini sorgulama (eski Framework sürümleri)</span><span class="sxs-lookup"><span data-stu-id="bf852-247">Query the registry using code (older framework versions)</span></span>

<span data-ttu-id="bf852-248"><xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType>Windows kayıt defterindeki **HKEY_LOCAL_MACHINE \\ Software \\ Microsoft \\ net Framework Setup \\ NDP** alt anahtarına erişmek için sınıfını kullanın.</span><span class="sxs-lookup"><span data-stu-id="bf852-248">Use the <xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType> class to access the **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\NET Framework Setup\\NDP** subkey in the Windows registry.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bf852-249">Çalıştırdığınız uygulama 32-bit ise ve 64 bit Windows 'da çalışıyorsa, kayıt defteri yolları daha önce listelenenden farklı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="bf852-249">If the app you're running is 32-bit and running in 64-bit Windows, the registry paths will be different than previously listed.</span></span> <span data-ttu-id="bf852-250">64 bit kayıt defteri **HKEY_LOCAL_MACHINE \\ Software \\ Wow6432Node \\** alt anahtarında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="bf852-250">The 64-bit registry is available in the **HKEY_LOCAL_MACHINE\\SOFTWARE\\Wow6432Node\\** subkey.</span></span> <span data-ttu-id="bf852-251">Örneğin, .NET Framework 3,5 için kayıt defteri alt anahtarı **HKEY_LOCAL_MACHINE \\ Software \\ Wow6432Node \\ Microsoft \\ net Framework Setup \\ NDP \\ v 3.5**' dir.</span><span class="sxs-lookup"><span data-stu-id="bf852-251">For example, the registry subkey for .NET Framework 3.5 is **HKEY_LOCAL_MACHINE\\SOFTWARE\\Wow6432Node\\Microsoft\\NET Framework Setup\\NDP\\v3.5**.</span></span>

<span data-ttu-id="bf852-252">Aşağıdaki örnek, yüklü .NET Framework 1-4 sürümlerini bulur:</span><span class="sxs-lookup"><span data-stu-id="bf852-252">The following example finds the versions of .NET Framework 1-4 that are installed:</span></span>

:::code language="csharp" source="snippets/csharp/versions-installed.cs" id="1":::

:::code language="vb" source="snippets/visual-basic/versions-installed.vb" id="1":::

<span data-ttu-id="bf852-253">Örnek aşağıdakine benzer bir çıktı görüntüler:</span><span class="sxs-lookup"><span data-stu-id="bf852-253">The example displays output similar to the following:</span></span>

```output
v2.0.50727  2.0.50727.4927  SP2
v3.0  3.0.30729.4926  SP2
v3.5  3.5.30729.4926  SP1
v4.0
  Client  4.0.0.0
```

## <a name="find-clr-versions"></a><span data-ttu-id="bf852-254">CLR sürümlerini bul</span><span class="sxs-lookup"><span data-stu-id="bf852-254">Find CLR versions</span></span>

<span data-ttu-id="bf852-255">.NET Framework ile yüklenen .NET Framework CLR 'nin sürümü ayrı olarak sağlanır.</span><span class="sxs-lookup"><span data-stu-id="bf852-255">The .NET Framework CLR installed with .NET Framework is versioned separately.</span></span> <span data-ttu-id="bf852-256">.NET Framework CLR sürümünü algılamamanın iki yolu vardır:</span><span class="sxs-lookup"><span data-stu-id="bf852-256">There are two ways to detect the version of the .NET Framework CLR:</span></span>

- <span data-ttu-id="bf852-257">**Clrver.exe aracı**</span><span class="sxs-lookup"><span data-stu-id="bf852-257">**The Clrver.exe tool**</span></span>

  <span data-ttu-id="bf852-258">Clr [Sürüm aracı 'nı (Clrver.exe)](../tools/clrver-exe-clr-version-tool.md) kullanarak bir bılgısayarda hangi CLR sürümlerinin yüklü olduğunu saptayın.</span><span class="sxs-lookup"><span data-stu-id="bf852-258">Use the [CLR Version tool (Clrver.exe)](../tools/clrver-exe-clr-version-tool.md) to determine which versions of the CLR are installed on a computer.</span></span> <span data-ttu-id="bf852-259">[Visual Studio için geliştirici komut istemi](../tools/developer-command-prompt-for-vs.md) açın ve girin `clrver` .</span><span class="sxs-lookup"><span data-stu-id="bf852-259">Open the [Developer Command Prompt for Visual Studio](../tools/developer-command-prompt-for-vs.md) and enter `clrver`.</span></span>

  <span data-ttu-id="bf852-260">Örnek çıktı:</span><span class="sxs-lookup"><span data-stu-id="bf852-260">Sample output:</span></span>

  ```console
  Versions installed on the machine:
  v2.0.50727
  v4.0.30319
  ```

- <span data-ttu-id="bf852-261">**`Environment`Sınıfı**</span><span class="sxs-lookup"><span data-stu-id="bf852-261">**The `Environment` class**</span></span>

  > [!IMPORTANT]
  > <span data-ttu-id="bf852-262">.NET Framework 4,5 ve sonraki sürümlerinde, <xref:System.Environment.Version%2A?displayProperty=nameWithType> CLR sürümünü algılamak için özelliğini kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="bf852-262">For .NET Framework 4.5 and later versions, don't use the <xref:System.Environment.Version%2A?displayProperty=nameWithType> property to detect the version of the CLR.</span></span> <span data-ttu-id="bf852-263">Bunun yerine, kayıt defterini [.NET Framework 4,5 ve sonraki sürümlerinde](#detect-net-framework-45-and-later-versions)açıklandığı gibi sorgulayın.</span><span class="sxs-lookup"><span data-stu-id="bf852-263">Instead, query the registry as described in [Detect .NET Framework 4.5 and later versions](#detect-net-framework-45-and-later-versions).</span></span>

  1. <span data-ttu-id="bf852-264"><xref:System.Environment.Version?displayProperty=nameWithType>Nesneyi almak için özelliği sorgulayın <xref:System.Version> .</span><span class="sxs-lookup"><span data-stu-id="bf852-264">Query the <xref:System.Environment.Version?displayProperty=nameWithType> property to retrieve a <xref:System.Version> object.</span></span>

     <span data-ttu-id="bf852-265">Döndürülen `System.Version` nesne, şu anda kodu yürüten çalışma zamanının sürümünü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="bf852-265">The returned `System.Version` object identifies the version of the runtime that's currently executing the code.</span></span> <span data-ttu-id="bf852-266">Derleme sürümlerini veya çalışma zamanının bilgisayarda yüklü olabilecek diğer sürümlerini döndürmez.</span><span class="sxs-lookup"><span data-stu-id="bf852-266">It doesn't return assembly versions or other versions of the runtime that may have been installed on the computer.</span></span>

     <span data-ttu-id="bf852-267">.NET Framework sürümleri 4, 4,5, 4.5.1 ve 4.5.2 için, döndürülen nesnenin dize temsili <xref:System.Version> 4.0.30319 biçimindedir.*xxxxx*, *xxxxx* 42000 ' den küçük.</span><span class="sxs-lookup"><span data-stu-id="bf852-267">For .NET Framework versions 4, 4.5, 4.5.1, and 4.5.2, the string representation of the returned <xref:System.Version> object has the form 4.0.30319.*xxxxx*, where *xxxxx* is less than 42000.</span></span> <span data-ttu-id="bf852-268">.NET Framework 4,6 ve sonraki sürümlerinde, 4.0.30319.42000 biçiminde olur.</span><span class="sxs-lookup"><span data-stu-id="bf852-268">For .NET Framework 4.6 and later versions, it has the form 4.0.30319.42000.</span></span>

  1. <span data-ttu-id="bf852-269">**Sürüm** nesnesine sahip olduktan sonra, aşağıdaki gibi sorgulayın:</span><span class="sxs-lookup"><span data-stu-id="bf852-269">After you have the **Version** object, query it as follows:</span></span>

     - <span data-ttu-id="bf852-270">Ana yayın tanımlayıcısı için (örneğin, sürüm 4,0 için *4* ), <xref:System.Version.Major%2A?displayProperty=nameWithType> özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="bf852-270">For the major release identifier (for example, *4* for version 4.0), use the <xref:System.Version.Major%2A?displayProperty=nameWithType> property.</span></span>

     - <span data-ttu-id="bf852-271">Küçük yayın tanımlayıcısı için (örneğin, sürüm 4,0 için *0* ), <xref:System.Version.Minor%2A?displayProperty=nameWithType> özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="bf852-271">For the minor release identifier (for example, *0* for version 4.0), use the <xref:System.Version.Minor%2A?displayProperty=nameWithType> property.</span></span>

     - <span data-ttu-id="bf852-272">Tüm sürüm dizesi için (örneğin, *4.0.30319.18010*), <xref:System.Version.ToString%2A?displayProperty=nameWithType> yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="bf852-272">For the entire version string (for example, *4.0.30319.18010*), use the <xref:System.Version.ToString%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="bf852-273">Bu yöntem, kodu yürüten çalışma zamanının sürümünü yansıtan tek bir değer döndürür.</span><span class="sxs-lookup"><span data-stu-id="bf852-273">This method returns a single value that reflects the version of the runtime that's executing the code.</span></span> <span data-ttu-id="bf852-274">Bu, bilgisayarda yüklü olabilecek derleme sürümlerini veya diğer çalışma zamanı sürümlerini döndürmez.</span><span class="sxs-lookup"><span data-stu-id="bf852-274">It doesn't return assembly versions or other runtime versions that may be installed on the computer.</span></span>

  <span data-ttu-id="bf852-275">Aşağıdaki örnek <xref:System.Environment.Version%2A?displayProperty=nameWithType> CLR sürüm bilgilerini almak için özelliğini kullanır:</span><span class="sxs-lookup"><span data-stu-id="bf852-275">The following example uses the <xref:System.Environment.Version%2A?displayProperty=nameWithType> property to retrieve CLR version information:</span></span>

  ```csharp
  Console.WriteLine($"Version: {Environment.Version}");
  ```

  ```vb
  Console.WriteLine($"Version: {Environment.Version}")
  ```

  <span data-ttu-id="bf852-276">Örnek aşağıdakine benzer bir çıktı görüntüler:</span><span class="sxs-lookup"><span data-stu-id="bf852-276">The example displays output similar to the following:</span></span>

  ```output
  Version: 4.0.30319.18010
  ```

## <a name="see-also"></a><span data-ttu-id="bf852-277">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bf852-277">See also</span></span>

- [<span data-ttu-id="bf852-278">Nasıl yapılır: hangi .NET Framework güncelleştirmelerinin yükleneceğini belirleme</span><span class="sxs-lookup"><span data-stu-id="bf852-278">How to: Determine which .NET Framework updates are installed</span></span>](how-to-determine-which-net-framework-updates-are-installed.md)
- [<span data-ttu-id="bf852-279">Geliştiriciler için .NET Framework yükler</span><span class="sxs-lookup"><span data-stu-id="bf852-279">Install .NET Framework for developers</span></span>](../install/guide-for-developers.md)
- [<span data-ttu-id="bf852-280">.NET Framework sürümleri ve bağımlılıklar</span><span class="sxs-lookup"><span data-stu-id="bf852-280">.NET Framework versions and dependencies</span></span>](versions-and-dependencies.md)
