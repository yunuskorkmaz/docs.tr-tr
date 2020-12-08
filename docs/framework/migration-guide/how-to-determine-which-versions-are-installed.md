---
title: Hangi .NET Framework sürümlerinin yüklü olduğunu belirleme
description: Windows kayıt defterini sorgulayarak bir makineye hangi .NET Framework sürümlerinin yükleneceğini algılamak için kod, regedit.exe veya PowerShell kullanın.
ms.date: 12/04/2020
dev_langs:
- csharp
- vb
helpviewer_keywords:
- versions, determining for .NET Framework
- .NET Framework, determining installed versions
ms.assetid: 40a67826-e4df-4f59-a651-d9eb0fdc755d
ms.openlocfilehash: a219514fafdcb17db259e089afa8318dbab24811
ms.sourcegitcommit: 45c7148f2483db2501c1aa696ab6ed2ed8cb71b2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/08/2020
ms.locfileid: "96851835"
---
# <a name="how-to-determine-which-net-framework-versions-are-installed"></a><span data-ttu-id="a4687-103">Nasıl yapılır: hangi .NET Framework sürümlerinin yüklendiğini belirleme</span><span class="sxs-lookup"><span data-stu-id="a4687-103">How to: Determine which .NET Framework versions are installed</span></span>

<span data-ttu-id="a4687-104">Kullanıcılar, .NET Framework birden çok sürümünü bilgisayarlarına [yükleyebilir](../install/index.md) ve çalıştırabilir.</span><span class="sxs-lookup"><span data-stu-id="a4687-104">Users can [install](../install/index.md) and run multiple versions of .NET Framework on their computers.</span></span> <span data-ttu-id="a4687-105">Uygulamanızı geliştirirken veya dağıtırken, kullanıcının bilgisayarında hangi .NET Framework sürümlerinin yüklü olduğunu bilmeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="a4687-105">When you develop or deploy your app, you might need to know which .NET Framework versions are installed on the user's computer.</span></span> <span data-ttu-id="a4687-106">Kayıt defteri, bilgisayarda yüklü .NET Framework sürümlerinin bir listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="a4687-106">The registry contains a list of the versions of .NET Framework installed on the computer.</span></span>

> [!NOTE]
> <span data-ttu-id="a4687-107">Bu makale .NET Framework özeldir.</span><span class="sxs-lookup"><span data-stu-id="a4687-107">This article is specific to .NET Framework.</span></span> <span data-ttu-id="a4687-108">Hangi .NET Core ve .NET 5 + SDK ve çalışma zamanlarının yüklendiğini öğrenmek için bkz. [.net 'in zaten yüklü olduğunu denetleme](../../core/install/how-to-detect-installed-versions.md).</span><span class="sxs-lookup"><span data-stu-id="a4687-108">To determine which .NET Core and .NET 5+ SDKs and runtimes are installed, see [How to check that .NET is already installed](../../core/install/how-to-detect-installed-versions.md).</span></span>

<span data-ttu-id="a4687-109">.NET Framework, sürümü ayrı olan iki ana bileşenden oluşur:</span><span class="sxs-lookup"><span data-stu-id="a4687-109">.NET Framework consists of two main components, which are versioned separately:</span></span>

- <span data-ttu-id="a4687-110">Uygulamalarınız için işlevsellik sağlayan tür ve kaynak koleksiyonları olan derlemeler kümesi.</span><span class="sxs-lookup"><span data-stu-id="a4687-110">A set of assemblies, which are collections of types and resources that provide the functionality for your apps.</span></span> <span data-ttu-id="a4687-111">.NET Framework ve derlemeler aynı sürüm numarasını paylaşır.</span><span class="sxs-lookup"><span data-stu-id="a4687-111">.NET Framework and the assemblies share the same version number.</span></span> <span data-ttu-id="a4687-112">Örneğin, .NET Framework sürümler 4,5, 4.6.1 ve 4.7.2 ' i içerir.</span><span class="sxs-lookup"><span data-stu-id="a4687-112">For example, .NET Framework versions include 4.5, 4.6.1, and 4.7.2.</span></span>

- <span data-ttu-id="a4687-113">Uygulamanızın kodunu yöneten ve yürüten ortak dil çalışma zamanı (CLR).</span><span class="sxs-lookup"><span data-stu-id="a4687-113">The common language runtime (CLR), which manages and executes your app's code.</span></span> <span data-ttu-id="a4687-114">Tek bir CLR sürümü genellikle birden çok .NET Framework sürümü destekler.</span><span class="sxs-lookup"><span data-stu-id="a4687-114">A single CLR version typically supports multiple .NET Framework versions.</span></span> <span data-ttu-id="a4687-115">Örneğin, CLR sürüm 4.0.30319. *xxxxx* , *xxxxx* 42000 ' den az olduğunda, 4 ile 4.5.2 arası sürüm .NET Framework destekler.</span><span class="sxs-lookup"><span data-stu-id="a4687-115">For example, CLR version 4.0.30319.*xxxxx* where *xxxxx* is less than 42000, supports .NET Framework versions 4 through 4.5.2.</span></span> <span data-ttu-id="a4687-116">4.0.30319.42000 'den büyük veya buna eşit CLR sürümü, .NET Framework 4,6 ' den başlayarak .NET Framework sürümlerini destekler.</span><span class="sxs-lookup"><span data-stu-id="a4687-116">CLR version greater than or equal to 4.0.30319.42000 supports .NET Framework versions starting with .NET Framework 4.6.</span></span>

<span data-ttu-id="a4687-117">Hangi .NET Framework sürümlerinin yüklü olduğunu algılamaya yardımcı olmak için topluluk ile korunan araçlar sunulmaktadır:</span><span class="sxs-lookup"><span data-stu-id="a4687-117">Community-maintained tools are available to help detect which .NET Framework versions are installed:</span></span>

- [https://github.com/jmalarcon/DotNetVersions](https://github.com/jmalarcon/DotNetVersions)

  <span data-ttu-id="a4687-118">.NET Framework 2,0 komut satırı aracı.</span><span class="sxs-lookup"><span data-stu-id="a4687-118">A .NET Framework 2.0 command-line tool.</span></span>

- [https://github.com/EliteLoser/DotNetVersionLister](https://github.com/EliteLoser/DotNetVersionLister)

  <span data-ttu-id="a4687-119">Bir PowerShell 2,0 modülü.</span><span class="sxs-lookup"><span data-stu-id="a4687-119">A PowerShell 2.0 module.</span></span>

<span data-ttu-id="a4687-120">Her bir .NET Framework sürümü için yüklü güncelleştirmeleri algılama hakkında bilgi için bkz. [nasıl yapılır: hangi .NET Framework güncelleştirmelerinin yükleneceğini belirleme](how-to-determine-which-net-framework-updates-are-installed.md).</span><span class="sxs-lookup"><span data-stu-id="a4687-120">For information about detecting the installed updates for each version of .NET Framework, see [How to: Determine which .NET Framework updates are installed](how-to-determine-which-net-framework-updates-are-installed.md).</span></span>

## <a name="determine-which-net-implementation-and-version-an-app-is-running-on"></a><span data-ttu-id="a4687-121">Uygulamanın hangi .NET uygulaması ve sürümü üzerinde çalıştığını belirleme</span><span class="sxs-lookup"><span data-stu-id="a4687-121">Determine which .NET implementation and version an app is running on</span></span>

<span data-ttu-id="a4687-122"><xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType>Özelliğini kullanarak uygulamanızın üzerinde çalıştığı .NET uygulaması ve sürümü için sorgulama yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a4687-122">You can use the <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType> property to query for which .NET implementation and version your app is running on.</span></span> <span data-ttu-id="a4687-123">Uygulama .NET Framework çalışıyorsa, çıkış şuna benzer olacaktır:</span><span class="sxs-lookup"><span data-stu-id="a4687-123">If the app is running on .NET Framework, the output will be similar to:</span></span>

```output
.NET Framework 4.8.4250.0
```

<span data-ttu-id="a4687-124">Karşılaştırma yaparak, uygulama .NET Core veya .NET 5 + üzerinde çalışıyorsa, çıkış şuna benzer olacaktır:</span><span class="sxs-lookup"><span data-stu-id="a4687-124">By comparison, if the app is running on .NET Core or .NET 5+, the output will be similar to:</span></span>

```output
.NET Core 3.1.9
.NET 5.0.0
```

## <a name="detect-net-framework-45-and-later-versions"></a><span data-ttu-id="a4687-125">.NET Framework 4,5 ve sonraki sürümleri Algıla</span><span class="sxs-lookup"><span data-stu-id="a4687-125">Detect .NET Framework 4.5 and later versions</span></span>

<span data-ttu-id="a4687-126">Bir makinede yüklü .NET Framework (4,5 ve üzeri) sürümü, **HKEY_LOCAL_MACHINE \\ yazılım \\ Microsoft \\ net Framework Setup \\ NDP \\ v4 \\ Full** bölümünde kayıt defterinde listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="a4687-126">The version of .NET Framework (4.5 and later) installed on a machine is listed in the registry at **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\NET Framework Setup\\NDP\\v4\\Full**.</span></span> <span data-ttu-id="a4687-127">**Tam** alt anahtar eksikse, .NET Framework 4,5 veya üzeri yüklü değildir.</span><span class="sxs-lookup"><span data-stu-id="a4687-127">If the **Full** subkey is missing, then .NET Framework 4.5 or above isn't installed.</span></span>

> [!NOTE]
> <span data-ttu-id="a4687-128">Kayıt defteri yolundaki **net Framework kurulum** alt anahtarı bir noktayla *başlamaz.*</span><span class="sxs-lookup"><span data-stu-id="a4687-128">The **NET Framework Setup** subkey in the registry path does *not* begin with a period.</span></span>

<span data-ttu-id="a4687-129">Kayıt defterindeki **Release** REG_DWORD değeri, yüklü .NET Framework sürümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="a4687-129">The **Release** REG_DWORD value in the registry represents the version of .NET Framework installed.</span></span>

<a name="version_table"></a>

| <span data-ttu-id="a4687-130">.NET Framework sürümü</span><span class="sxs-lookup"><span data-stu-id="a4687-130">.NET Framework version</span></span> | <span data-ttu-id="a4687-131">**Yayın** değeri</span><span class="sxs-lookup"><span data-stu-id="a4687-131">Value of **Release**</span></span> |
| ---------------------- | -------------------------- |
| <span data-ttu-id="a4687-132">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="a4687-132">.NET Framework 4.5</span></span>     | <span data-ttu-id="a4687-133">Tüm Windows işletim sistemleri: 378389</span><span class="sxs-lookup"><span data-stu-id="a4687-133">All Windows operating systems: 378389</span></span> |
| <span data-ttu-id="a4687-134">.NET Framework 4.5.1</span><span class="sxs-lookup"><span data-stu-id="a4687-134">.NET Framework 4.5.1</span></span>   | <span data-ttu-id="a4687-135">Windows 8.1 ve Windows Server 2012 R2 'de: 378675</span><span class="sxs-lookup"><span data-stu-id="a4687-135">On Windows 8.1 and Windows Server 2012 R2: 378675</span></span><br /><span data-ttu-id="a4687-136">Diğer tüm Windows işletim sistemlerinde: 378758</span><span class="sxs-lookup"><span data-stu-id="a4687-136">On all other Windows operating systems: 378758</span></span> |
| <span data-ttu-id="a4687-137">.NET Framework 4.5.2</span><span class="sxs-lookup"><span data-stu-id="a4687-137">.NET Framework 4.5.2</span></span>   | <span data-ttu-id="a4687-138">Tüm Windows işletim sistemleri: 379893</span><span class="sxs-lookup"><span data-stu-id="a4687-138">All Windows operating systems: 379893</span></span> |
| <span data-ttu-id="a4687-139">.NET Framework 4.6</span><span class="sxs-lookup"><span data-stu-id="a4687-139">.NET Framework 4.6</span></span>     | <span data-ttu-id="a4687-140">Windows 10:393295 ' de</span><span class="sxs-lookup"><span data-stu-id="a4687-140">On Windows 10: 393295</span></span><br /><span data-ttu-id="a4687-141">Diğer tüm Windows işletim sistemlerinde: 393297</span><span class="sxs-lookup"><span data-stu-id="a4687-141">On all other Windows operating systems: 393297</span></span> |
| <span data-ttu-id="a4687-142">.NET Framework 4.6.1</span><span class="sxs-lookup"><span data-stu-id="a4687-142">.NET Framework 4.6.1</span></span>   | <span data-ttu-id="a4687-143">Windows 10 Kasım güncelleştirme sistemlerinde: 394254</span><span class="sxs-lookup"><span data-stu-id="a4687-143">On Windows 10 November Update systems: 394254</span></span><br /><span data-ttu-id="a4687-144">Diğer tüm Windows işletim sistemlerinde (Windows 10 dahil): 394271</span><span class="sxs-lookup"><span data-stu-id="a4687-144">On all other Windows operating systems (including Windows 10): 394271</span></span> |
| <span data-ttu-id="a4687-145">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="a4687-145">.NET Framework 4.6.2</span></span>   | <span data-ttu-id="a4687-146">Windows 10 yıldönümü güncelleştirmesi ve Windows Server 2016:394802</span><span class="sxs-lookup"><span data-stu-id="a4687-146">On Windows 10 Anniversary Update and Windows Server 2016: 394802</span></span><br /><span data-ttu-id="a4687-147">Diğer tüm Windows işletim sistemlerinde (diğer Windows 10 işletim sistemleri dahil): 394806</span><span class="sxs-lookup"><span data-stu-id="a4687-147">On all other Windows operating systems (including other Windows 10 operating systems): 394806</span></span> |
| <span data-ttu-id="a4687-148"> .NET Framework 4.7</span><span class="sxs-lookup"><span data-stu-id="a4687-148">.NET Framework 4.7</span></span>     | <span data-ttu-id="a4687-149">Windows 10 Creators Update üzerinde: 460798</span><span class="sxs-lookup"><span data-stu-id="a4687-149">On Windows 10 Creators Update: 460798</span></span><br /><span data-ttu-id="a4687-150">Diğer tüm Windows işletim sistemlerinde (diğer Windows 10 işletim sistemleri dahil): 460805</span><span class="sxs-lookup"><span data-stu-id="a4687-150">On all other Windows operating systems (including other Windows 10 operating systems): 460805</span></span> |
| <span data-ttu-id="a4687-151">.NET Framework 4.7.1</span><span class="sxs-lookup"><span data-stu-id="a4687-151">.NET Framework 4.7.1</span></span>   | <span data-ttu-id="a4687-152">Windows 10 Fall Creators Update ve Windows Server, sürüm 1709:461308</span><span class="sxs-lookup"><span data-stu-id="a4687-152">On Windows 10 Fall Creators Update and Windows Server, version 1709: 461308</span></span><br/><span data-ttu-id="a4687-153">Diğer tüm Windows işletim sistemlerinde (diğer Windows 10 işletim sistemleri dahil): 461310</span><span class="sxs-lookup"><span data-stu-id="a4687-153">On all other Windows operating systems (including other Windows 10 operating systems): 461310</span></span> |
| <span data-ttu-id="a4687-154"> .NET Framework 4.7.2</span><span class="sxs-lookup"><span data-stu-id="a4687-154">.NET Framework 4.7.2</span></span>   | <span data-ttu-id="a4687-155">Windows 10 Nisan 2018 güncelleştirmesi ve Windows Server, sürüm 1803:461808</span><span class="sxs-lookup"><span data-stu-id="a4687-155">On Windows 10 April 2018 Update and Windows Server, version 1803: 461808</span></span><br/><span data-ttu-id="a4687-156">Windows 10 Nisan 2018 güncelleştirmesi ve Windows Server, sürüm 1803 dışındaki tüm Windows işletim sistemlerinde: 461814</span><span class="sxs-lookup"><span data-stu-id="a4687-156">On all Windows operating systems other than Windows 10 April 2018 Update and Windows Server, version 1803: 461814</span></span> |
| <span data-ttu-id="a4687-157"> .NET Framework 4.8</span><span class="sxs-lookup"><span data-stu-id="a4687-157">.NET Framework 4.8</span></span>     | <span data-ttu-id="a4687-158">Windows 10 Mayıs 2019 güncelleştirmesi ve Windows 10 Kasım 2019 güncelleştirmesi: 528040</span><span class="sxs-lookup"><span data-stu-id="a4687-158">On Windows 10 May 2019 Update and Windows 10 November 2019 Update: 528040</span></span><br/><span data-ttu-id="a4687-159">Windows 10 Mayıs 2020 güncelleştirmesi ve Windows 10 Ekim 2020 güncelleştirmesi: 528372</span><span class="sxs-lookup"><span data-stu-id="a4687-159">On Windows 10 May 2020 Update and Windows 10 October 2020 Update: 528372</span></span><br/><span data-ttu-id="a4687-160">Diğer tüm Windows işletim sistemlerinde (diğer Windows 10 işletim sistemleri dahil): 528049</span><span class="sxs-lookup"><span data-stu-id="a4687-160">On all other Windows operating systems (including other Windows 10 operating systems): 528049</span></span> |

### <a name="minimum-version"></a><span data-ttu-id="a4687-161">En düşük sürüm</span><span class="sxs-lookup"><span data-stu-id="a4687-161">Minimum version</span></span>

<span data-ttu-id="a4687-162">*En düşük* .NET Framework sürümünün mevcut olup olmadığını anlamak için, aşağıdaki tabloda listelenen değere eşit veya ondan daha büyük bir **Sürüm** REG_DWORD değeri denetleyin.</span><span class="sxs-lookup"><span data-stu-id="a4687-162">To determine whether a *minimum* version of .NET Framework is present, check for a **Release** REG_DWORD value that's greater than or equal to the corresponding value listed in the following table.</span></span> <span data-ttu-id="a4687-163">Örneğin, uygulamanız .NET Framework 4,8 veya sonraki bir sürümde çalışıyorsa, 528040 ' *e eşit veya daha büyük* olan bir **yayın** REG_DWORD değeri için test edin.</span><span class="sxs-lookup"><span data-stu-id="a4687-163">For example, if your application runs under .NET Framework 4.8 or a later version, test for a **Release** REG_DWORD value that's *greater than or equal to* 528040.</span></span>

| <span data-ttu-id="a4687-164">.NET Framework sürümü</span><span class="sxs-lookup"><span data-stu-id="a4687-164">.NET Framework version</span></span> | <span data-ttu-id="a4687-165">En küçük değer</span><span class="sxs-lookup"><span data-stu-id="a4687-165">Minimum value</span></span> |
| ---------------------- | ------------- |
| <span data-ttu-id="a4687-166">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="a4687-166">.NET Framework 4.5</span></span>     | <span data-ttu-id="a4687-167">378389</span><span class="sxs-lookup"><span data-stu-id="a4687-167">378389</span></span> |
| <span data-ttu-id="a4687-168">.NET Framework 4.5.1</span><span class="sxs-lookup"><span data-stu-id="a4687-168">.NET Framework 4.5.1</span></span>   | <span data-ttu-id="a4687-169">378675</span><span class="sxs-lookup"><span data-stu-id="a4687-169">378675</span></span> |
| <span data-ttu-id="a4687-170">.NET Framework 4.5.2</span><span class="sxs-lookup"><span data-stu-id="a4687-170">.NET Framework 4.5.2</span></span>   | <span data-ttu-id="a4687-171">379893</span><span class="sxs-lookup"><span data-stu-id="a4687-171">379893</span></span> |
| <span data-ttu-id="a4687-172">.NET Framework 4.6</span><span class="sxs-lookup"><span data-stu-id="a4687-172">.NET Framework 4.6</span></span>     | <span data-ttu-id="a4687-173">393295</span><span class="sxs-lookup"><span data-stu-id="a4687-173">393295</span></span> |
| <span data-ttu-id="a4687-174">.NET Framework 4.6.1</span><span class="sxs-lookup"><span data-stu-id="a4687-174">.NET Framework 4.6.1</span></span>   | <span data-ttu-id="a4687-175">394254</span><span class="sxs-lookup"><span data-stu-id="a4687-175">394254</span></span> |
| <span data-ttu-id="a4687-176">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="a4687-176">.NET Framework 4.6.2</span></span>   | <span data-ttu-id="a4687-177">394802</span><span class="sxs-lookup"><span data-stu-id="a4687-177">394802</span></span> |
| <span data-ttu-id="a4687-178"> .NET Framework 4.7</span><span class="sxs-lookup"><span data-stu-id="a4687-178">.NET Framework 4.7</span></span>     | <span data-ttu-id="a4687-179">460798</span><span class="sxs-lookup"><span data-stu-id="a4687-179">460798</span></span> |
| <span data-ttu-id="a4687-180">.NET Framework 4.7.1</span><span class="sxs-lookup"><span data-stu-id="a4687-180">.NET Framework 4.7.1</span></span>   | <span data-ttu-id="a4687-181">461308</span><span class="sxs-lookup"><span data-stu-id="a4687-181">461308</span></span> |
| <span data-ttu-id="a4687-182"> .NET Framework 4.7.2</span><span class="sxs-lookup"><span data-stu-id="a4687-182">.NET Framework 4.7.2</span></span>   | <span data-ttu-id="a4687-183">461808</span><span class="sxs-lookup"><span data-stu-id="a4687-183">461808</span></span> |
| <span data-ttu-id="a4687-184"> .NET Framework 4.8</span><span class="sxs-lookup"><span data-stu-id="a4687-184">.NET Framework 4.8</span></span>     | <span data-ttu-id="a4687-185">528040</span><span class="sxs-lookup"><span data-stu-id="a4687-185">528040</span></span> |

### <a name="use-registry-editor"></a><span data-ttu-id="a4687-186">Kayıt Defteri Düzenleyicisi 'Ni kullan</span><span class="sxs-lookup"><span data-stu-id="a4687-186">Use Registry Editor</span></span>

1. <span data-ttu-id="a4687-187">**Başlat** menüsünde, **Çalıştır**' ı seçin, *Regedit*' i girin ve **Tamam**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="a4687-187">From the **Start** menu, choose **Run**, enter *regedit*, and then select **OK**.</span></span>

   <span data-ttu-id="a4687-188">(Regedit çalıştırmak için yönetici kimlik bilgilerine sahip olmanız gerekir.)</span><span class="sxs-lookup"><span data-stu-id="a4687-188">(You must have administrative credentials to run regedit.)</span></span>

1. <span data-ttu-id="a4687-189">Kayıt Defteri Düzenleyicisi 'nde, aşağıdaki alt anahtarı açın: **\\ yazılım \\ Microsoft \\ net Framework Setup \\ NDP \\ v4 \\ Full HKEY_LOCAL_MACHINE**.</span><span class="sxs-lookup"><span data-stu-id="a4687-189">In the Registry Editor, open the following subkey: **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\NET Framework Setup\\NDP\\v4\\Full**.</span></span> <span data-ttu-id="a4687-190">**Tam** alt anahtar yoksa, .NET Framework 4,5 veya sonraki bir sürümü yüklü değildir.</span><span class="sxs-lookup"><span data-stu-id="a4687-190">If the **Full** subkey isn't present, then you don't have .NET Framework 4.5 or later installed.</span></span>

1. <span data-ttu-id="a4687-191">**Yayın** adlı REG_DWORD girişi olup olmadığını denetleyin.</span><span class="sxs-lookup"><span data-stu-id="a4687-191">Check for a REG_DWORD entry named **Release**.</span></span> <span data-ttu-id="a4687-192">Varsa, .NET Framework 4,5 veya sonraki bir sürümü yüklemiş olursunuz.</span><span class="sxs-lookup"><span data-stu-id="a4687-192">If it exists, then you have .NET Framework 4.5 or later installed.</span></span> <span data-ttu-id="a4687-193">Değeri, .NET Framework belirli bir sürümüne karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="a4687-193">Its value corresponds to a particular version of .NET Framework.</span></span> <span data-ttu-id="a4687-194">Aşağıdaki şekilde, örneğin, **Sürüm** girişinin değeri 528040 ' dir. bu, .NET Framework 4,8 ' in sürüm anahtarıdır.</span><span class="sxs-lookup"><span data-stu-id="a4687-194">In the following figure, for example, the value of the **Release** entry is 528040, which is the release key for .NET Framework 4.8.</span></span>

   ![.NET Framework 4,5 için kayıt defteri girişi](./media/clr-installdir.png )

### <a name="use-powershell-to-check-for-a-minimum-version"></a><span data-ttu-id="a4687-196">En düşük sürümü denetlemek için PowerShell 'i kullanma</span><span class="sxs-lookup"><span data-stu-id="a4687-196">Use PowerShell to check for a minimum version</span></span>

<span data-ttu-id="a4687-197">PowerShell komutlarını, **HKEY_LOCAL_MACHINE \\ yazılım \\ Microsoft \\ net Framework Setup \\ NDP \\ v4 \\ Full** alt anahtarının **yayın** girişinin değerini denetlemek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="a4687-197">Use PowerShell commands to check the value of the **Release** entry of the **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\NET Framework Setup\\NDP\\v4\\Full** subkey.</span></span>

<span data-ttu-id="a4687-198">Aşağıdaki örnekler, .NET Framework 4.6.2 veya sonraki bir sürümün yüklenip yüklenmediğini anlamak için **yayın** girişinin değerini denetler.</span><span class="sxs-lookup"><span data-stu-id="a4687-198">The following examples check the value of the **Release** entry to determine whether .NET Framework 4.6.2 or later is installed.</span></span> <span data-ttu-id="a4687-199">Bu kod `True` , yüklenmişse ve `False` Aksi takdirde döndürülür.</span><span class="sxs-lookup"><span data-stu-id="a4687-199">This code returns `True` if it's installed and `False` otherwise.</span></span>

```powershell
(Get-ItemProperty "HKLM:\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full").Release -ge 394802
```

### <a name="query-the-registry-using-code"></a><span data-ttu-id="a4687-200">Kodu kullanarak kayıt defterini sorgulama</span><span class="sxs-lookup"><span data-stu-id="a4687-200">Query the registry using code</span></span>

01. <span data-ttu-id="a4687-201"><xref:Microsoft.Win32.RegistryKey.OpenBaseKey%2A?displayProperty=nameWithType> <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A?displayProperty=nameWithType> Windows kayıt defterindeki **HKEY_LOCAL_MACHINE \\ Software \\ Microsoft \\ net Framework Setup \\ NDP \\ v4 \\ Full** alt anahtarına erişmek için ve yöntemlerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="a4687-201">Use the <xref:Microsoft.Win32.RegistryKey.OpenBaseKey%2A?displayProperty=nameWithType> and <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A?displayProperty=nameWithType> methods to access the **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\NET Framework Setup\\NDP\\v4\\Full** subkey in the Windows registry.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="a4687-202">Çalıştırdığınız uygulama 32-bit ise ve 64 bit Windows 'da çalışıyorsa, kayıt defteri yolları daha önce listelenenden farklı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="a4687-202">If the app you're running is 32-bit and running in 64-bit Windows, the registry paths will be different than previously listed.</span></span> <span data-ttu-id="a4687-203">64 bit kayıt defteri **HKEY_LOCAL_MACHINE \\ Software \\ Wow6432Node \\** alt anahtarında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a4687-203">The 64-bit registry is available in the **HKEY_LOCAL_MACHINE\\SOFTWARE\\Wow6432Node\\** subkey.</span></span> <span data-ttu-id="a4687-204">Örneğin, .NET Framework 4,5 için kayıt defteri alt anahtarı **HKEY_LOCAL_MACHINE \\ Software \\ Wow6432Node \\ Microsoft \\ net Framework Setup \\ NDP \\ v4 \\ Full**' dır.</span><span class="sxs-lookup"><span data-stu-id="a4687-204">For example, the registry subkey for .NET Framework 4.5 is **HKEY_LOCAL_MACHINE\\SOFTWARE\\Wow6432Node\\Microsoft\\NET Framework Setup\\NDP\\v4\\Full**.</span></span>

01. <span data-ttu-id="a4687-205">Yüklü sürümü öğrenmek için **yayın** REG_DWORD değerini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="a4687-205">Check the **Release** REG_DWORD value to determine the installed version.</span></span> <span data-ttu-id="a4687-206">İleriye dönük olarak uyumlu olması için [.NET Framework sürüm tablosunda](#version_table)listelenen değerden daha büyük veya ona eşit bir değer olup olmadığını kontrol edin.</span><span class="sxs-lookup"><span data-stu-id="a4687-206">To be forward-compatible, check for a value greater than or equal to the value listed in the [.NET Framework version table](#version_table).</span></span>

<span data-ttu-id="a4687-207">Aşağıdaki örnek, yüklü .NET Framework 4.5-4.8 sürümlerini bulmak için kayıt defterindeki **yayın** girişinin değerini denetler:</span><span class="sxs-lookup"><span data-stu-id="a4687-207">The following example checks the value of the **Release** entry in the registry to find the versions of .NET Framework 4.5-4.8 that are installed:</span></span>

:::code language="csharp" source="snippets/csharp/versions-installed.cs" id="2":::

:::code language="vb" source="snippets/visual-basic/versions-installed.vb" id="2":::

<span data-ttu-id="a4687-208">Örneğin, aşağıdaki gibi bir çıktı görüntülenir:</span><span class="sxs-lookup"><span data-stu-id="a4687-208">The example displays output like the following:</span></span>

```output
.NET Framework Version: 4.6.1
```

<span data-ttu-id="a4687-209">Bu örnek sürüm denetimi için önerilen yöntemi izler:</span><span class="sxs-lookup"><span data-stu-id="a4687-209">This example follows the recommended practice for version checking:</span></span>

- <span data-ttu-id="a4687-210">**Yayın** girişi değerinin bilinen yayın anahtarlarının değerinden *büyük veya* bu değere eşit olup olmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="a4687-210">It checks whether the value of the **Release** entry is *greater than or equal to* the value of the known release keys.</span></span>
- <span data-ttu-id="a4687-211">En son sürümden en eski sürüme sırayla kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="a4687-211">It checks in order from most recent version to earliest version.</span></span>

## <a name="detect-net-framework-10-through-40"></a><span data-ttu-id="a4687-212">1,0 ile 4,0 arasındaki .NET Framework Algıla</span><span class="sxs-lookup"><span data-stu-id="a4687-212">Detect .NET Framework 1.0 through 4.0</span></span>

<span data-ttu-id="a4687-213">1,1 ' den 4,0 ' e .NET Framework her sürümü **HKEY_LOCAL_MACHINE \\ Software \\ Microsoft \\ net Framework Setup \\ NDP** alt anahtarı olarak listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="a4687-213">Each version of .NET Framework from 1.1 to 4.0 is listed as a subkey at **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\NET Framework Setup\\NDP**.</span></span> <span data-ttu-id="a4687-214">Aşağıdaki tabloda her bir .NET Framework sürümünün yolu listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="a4687-214">The following table lists the path to each .NET Framework version.</span></span> <span data-ttu-id="a4687-215">Çoğu sürümde, **Install** `1` Bu sürümün yüklü olduğunu göstermek için bir Install REG_DWORD değeri vardır.</span><span class="sxs-lookup"><span data-stu-id="a4687-215">For most versions, there's an **Install** REG_DWORD value of `1` to indicate this version is installed.</span></span> <span data-ttu-id="a4687-216">Bu alt anahtarlarda, sürüm dizesi içeren bir **sürüm** REG_SZ değeri de vardır.</span><span class="sxs-lookup"><span data-stu-id="a4687-216">In these subkeys, there's also a **Version** REG_SZ value that contains a version string.</span></span>

> [!NOTE]
> <span data-ttu-id="a4687-217">Kayıt defteri yolundaki **net Framework kurulum** alt anahtarı bir noktayla *başlamaz.*</span><span class="sxs-lookup"><span data-stu-id="a4687-217">The **NET Framework Setup** subkey in the registry path does *not* begin with a period.</span></span>

| <span data-ttu-id="a4687-218">Framework sürümü</span><span class="sxs-lookup"><span data-stu-id="a4687-218">Framework Version</span></span>  | <span data-ttu-id="a4687-219">Kayıt defteri alt anahtarı</span><span class="sxs-lookup"><span data-stu-id="a4687-219">Registry Subkey</span></span> | <span data-ttu-id="a4687-220">Değer</span><span class="sxs-lookup"><span data-stu-id="a4687-220">Value</span></span> |
| ------------------ | --------------- | ----- |
| <span data-ttu-id="a4687-221">1,0</span><span class="sxs-lookup"><span data-stu-id="a4687-221">1.0</span></span>                | <span data-ttu-id="a4687-222">**HKLM \\ Software \\ Microsoft \\ . NETFramework \\ ilkesi \\ v 1.0 \\ 3705**</span><span class="sxs-lookup"><span data-stu-id="a4687-222">**HKLM\\Software\\Microsoft\\.NETFramework\\Policy\\v1.0\\3705**</span></span>     | <span data-ttu-id="a4687-223">**Yüklemesi** REG_SZ eşittir `1`</span><span class="sxs-lookup"><span data-stu-id="a4687-223">**Install** REG_SZ equals `1`</span></span> |
| <span data-ttu-id="a4687-224">1.1</span><span class="sxs-lookup"><span data-stu-id="a4687-224">1.1</span></span>                | <span data-ttu-id="a4687-225">**HKLM \\ Software \\ Microsoft \\ net Framework Setup \\ NDP \\ v 1.1.4322**</span><span class="sxs-lookup"><span data-stu-id="a4687-225">**HKLM\\Software\\Microsoft\\NET Framework Setup\\NDP\\v1.1.4322**</span></span>   | <span data-ttu-id="a4687-226">**Yüklemesi** REG_DWORD eşittir `1`</span><span class="sxs-lookup"><span data-stu-id="a4687-226">**Install** REG_DWORD equals `1`</span></span> |
| <span data-ttu-id="a4687-227">2,0</span><span class="sxs-lookup"><span data-stu-id="a4687-227">2.0</span></span>                | <span data-ttu-id="a4687-228">**HKLM \\ Software \\ Microsoft \\ net Framework Setup \\ NDP \\ v 2.0.50727**</span><span class="sxs-lookup"><span data-stu-id="a4687-228">**HKLM\\Software\\Microsoft\\NET Framework Setup\\NDP\\v2.0.50727**</span></span>  | <span data-ttu-id="a4687-229">**Yüklemesi** REG_DWORD eşittir `1`</span><span class="sxs-lookup"><span data-stu-id="a4687-229">**Install** REG_DWORD equals `1`</span></span> |
| <span data-ttu-id="a4687-230">3,0</span><span class="sxs-lookup"><span data-stu-id="a4687-230">3.0</span></span>                | <span data-ttu-id="a4687-231">**HKLM \\ Software \\ Microsoft \\ net Framework Setup \\ NDP \\ v 3.0 \\ kurulumu**</span><span class="sxs-lookup"><span data-stu-id="a4687-231">**HKLM\\Software\\Microsoft\\NET Framework Setup\\NDP\\v3.0\\Setup**</span></span> | <span data-ttu-id="a4687-232">**Installsuccess** REG_DWORD eşittir `1`</span><span class="sxs-lookup"><span data-stu-id="a4687-232">**InstallSuccess** REG_DWORD equals `1`</span></span> |
| <span data-ttu-id="a4687-233">3,5</span><span class="sxs-lookup"><span data-stu-id="a4687-233">3.5</span></span>                | <span data-ttu-id="a4687-234">**HKLM \\ Software \\ Microsoft \\ net Framework Setup \\ NDP \\ v 3.5**</span><span class="sxs-lookup"><span data-stu-id="a4687-234">**HKLM\\Software\\Microsoft\\NET Framework Setup\\NDP\\v3.5**</span></span>        | <span data-ttu-id="a4687-235">**Yüklemesi** REG_DWORD eşittir `1`</span><span class="sxs-lookup"><span data-stu-id="a4687-235">**Install** REG_DWORD equals `1`</span></span> |
| <span data-ttu-id="a4687-236">4,0 istemci profili</span><span class="sxs-lookup"><span data-stu-id="a4687-236">4.0 Client Profile</span></span> | <span data-ttu-id="a4687-237">**HKLM \\ Software \\ Microsoft \\ net Framework Setup \\ NDP \\ v4 \\ istemcisi**</span><span class="sxs-lookup"><span data-stu-id="a4687-237">**HKLM\\Software\\Microsoft\\NET Framework Setup\\NDP\\v4\\Client**</span></span>  | <span data-ttu-id="a4687-238">**Yüklemesi** REG_DWORD eşittir `1`</span><span class="sxs-lookup"><span data-stu-id="a4687-238">**Install** REG_DWORD equals `1`</span></span> |
| <span data-ttu-id="a4687-239">4,0 tam profil</span><span class="sxs-lookup"><span data-stu-id="a4687-239">4.0 Full Profile</span></span>   | <span data-ttu-id="a4687-240">**HKLM \\ Software \\ Microsoft \\ net Framework Kurulumu \\ NDP \\ v4 \\ dolu**</span><span class="sxs-lookup"><span data-stu-id="a4687-240">**HKLM\\Software\\Microsoft\\NET Framework Setup\\NDP\\v4\\Full**</span></span>    | <span data-ttu-id="a4687-241">**Yüklemesi** REG_DWORD eşittir `1`</span><span class="sxs-lookup"><span data-stu-id="a4687-241">**Install** REG_DWORD equals `1`</span></span> |

> [!IMPORTANT]
> <span data-ttu-id="a4687-242">Çalıştırdığınız uygulama 32-bit ise ve 64 bit Windows 'da çalışıyorsa, kayıt defteri yolları daha önce listelenenden farklı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="a4687-242">If the app you're running is 32-bit and running in 64-bit Windows, the registry paths will be different than previously listed.</span></span> <span data-ttu-id="a4687-243">64 bit kayıt defteri **HKEY_LOCAL_MACHINE \\ Software \\ Wow6432Node \\** alt anahtarında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a4687-243">The 64-bit registry is available in the **HKEY_LOCAL_MACHINE\\SOFTWARE\\Wow6432Node\\** subkey.</span></span> <span data-ttu-id="a4687-244">Örneğin, .NET Framework 3,5 için kayıt defteri alt anahtarı **HKEY_LOCAL_MACHINE \\ Software \\ Wow6432Node \\ Microsoft \\ net Framework Setup \\ NDP \\ v 3.5**' dir.</span><span class="sxs-lookup"><span data-stu-id="a4687-244">For example, the registry subkey for .NET Framework 3.5 is **HKEY_LOCAL_MACHINE\\SOFTWARE\\Wow6432Node\\Microsoft\\NET Framework Setup\\NDP\\v3.5**.</span></span>

<span data-ttu-id="a4687-245">.NET Framework 1,0 alt anahtarına yönelik kayıt defteri yolunun diğerlerinden farklı olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="a4687-245">Notice that the registry path to the .NET Framework 1.0 subkey is different from the others.</span></span>

### <a name="use-registry-editor-older-framework-versions"></a><span data-ttu-id="a4687-246">Kayıt Defteri Düzenleyicisi 'Ni kullan (eski Framework sürümleri)</span><span class="sxs-lookup"><span data-stu-id="a4687-246">Use Registry Editor (older framework versions)</span></span>

01. <span data-ttu-id="a4687-247">**Başlat** menüsünde, **Çalıştır**' ı seçin, *Regedit*' i girin ve **Tamam**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="a4687-247">From the **Start** menu, choose **Run**, enter *regedit*, and then select **OK**.</span></span>

    <span data-ttu-id="a4687-248">Regedit 'i çalıştırmak için yönetici kimlik bilgilerine sahip olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="a4687-248">You must have administrative credentials to run regedit.</span></span>

01. <span data-ttu-id="a4687-249">Denetlemek istediğiniz sürümle eşleşen alt anahtarı açın.</span><span class="sxs-lookup"><span data-stu-id="a4687-249">Open the subkey that matches the version you want to check.</span></span> <span data-ttu-id="a4687-250">[.NET Framework 1,0 ile 4,0 arasında algılama](#detect-net-framework-10-through-40) bölümünde bulunan tabloyu kullanın.</span><span class="sxs-lookup"><span data-stu-id="a4687-250">Use the table in the [Detect .NET Framework 1.0 through 4.0](#detect-net-framework-10-through-40) section.</span></span>

    <span data-ttu-id="a4687-251">Aşağıdaki şekilde, .NET Framework 3,5 için alt anahtar ve **Sürüm** değeri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="a4687-251">The following figure shows the subkey and its **Version** value for .NET Framework 3.5.</span></span>

    <span data-ttu-id="a4687-252">![.NET Framework 3,5 için kayıt defteri girişi.](./media/net-4-and-earlier.png ".NET Framework 3,5 ve önceki sürümler")</span><span class="sxs-lookup"><span data-stu-id="a4687-252">![The registry entry for .NET Framework 3.5.](./media/net-4-and-earlier.png ".NET Framework 3.5 and earlier versions")</span></span>

### <a name="query-the-registry-using-code-older-framework-versions"></a><span data-ttu-id="a4687-253">Kodu kullanarak kayıt defterini sorgulama (eski Framework sürümleri)</span><span class="sxs-lookup"><span data-stu-id="a4687-253">Query the registry using code (older framework versions)</span></span>

<span data-ttu-id="a4687-254"><xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType>Windows kayıt defterindeki **HKEY_LOCAL_MACHINE \\ Software \\ Microsoft \\ net Framework Setup \\ NDP** alt anahtarına erişmek için sınıfını kullanın.</span><span class="sxs-lookup"><span data-stu-id="a4687-254">Use the <xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType> class to access the **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\NET Framework Setup\\NDP** subkey in the Windows registry.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a4687-255">Çalıştırdığınız uygulama 32-bit ise ve 64 bit Windows 'da çalışıyorsa, kayıt defteri yolları daha önce listelenenden farklı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="a4687-255">If the app you're running is 32-bit and running in 64-bit Windows, the registry paths will be different than previously listed.</span></span> <span data-ttu-id="a4687-256">64 bit kayıt defteri **HKEY_LOCAL_MACHINE \\ Software \\ Wow6432Node \\** alt anahtarında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a4687-256">The 64-bit registry is available in the **HKEY_LOCAL_MACHINE\\SOFTWARE\\Wow6432Node\\** subkey.</span></span> <span data-ttu-id="a4687-257">Örneğin, .NET Framework 3,5 için kayıt defteri alt anahtarı **HKEY_LOCAL_MACHINE \\ Software \\ Wow6432Node \\ Microsoft \\ net Framework Setup \\ NDP \\ v 3.5**' dir.</span><span class="sxs-lookup"><span data-stu-id="a4687-257">For example, the registry subkey for .NET Framework 3.5 is **HKEY_LOCAL_MACHINE\\SOFTWARE\\Wow6432Node\\Microsoft\\NET Framework Setup\\NDP\\v3.5**.</span></span>

<span data-ttu-id="a4687-258">Aşağıdaki örnek, yüklü .NET Framework 1-4 sürümlerini bulur:</span><span class="sxs-lookup"><span data-stu-id="a4687-258">The following example finds the versions of .NET Framework 1-4 that are installed:</span></span>

:::code language="csharp" source="snippets/csharp/versions-installed.cs" id="1":::

:::code language="vb" source="snippets/visual-basic/versions-installed.vb" id="1":::

<span data-ttu-id="a4687-259">Örnek aşağıdakine benzer bir çıktı görüntüler:</span><span class="sxs-lookup"><span data-stu-id="a4687-259">The example displays output similar to the following:</span></span>

```output
v2.0.50727  2.0.50727.4927  SP2
v3.0  3.0.30729.4926  SP2
v3.5  3.5.30729.4926  SP1
v4.0
  Client  4.0.0.0
```

## <a name="find-clr-versions"></a><span data-ttu-id="a4687-260">CLR sürümlerini bul</span><span class="sxs-lookup"><span data-stu-id="a4687-260">Find CLR versions</span></span>

<span data-ttu-id="a4687-261">.NET Framework ile yüklenen .NET Framework CLR 'nin sürümü ayrı olarak sağlanır.</span><span class="sxs-lookup"><span data-stu-id="a4687-261">The .NET Framework CLR installed with .NET Framework is versioned separately.</span></span> <span data-ttu-id="a4687-262">.NET Framework CLR sürümünü algılamamanın iki yolu vardır:</span><span class="sxs-lookup"><span data-stu-id="a4687-262">There are two ways to detect the version of the .NET Framework CLR:</span></span>

- <span data-ttu-id="a4687-263">**Clrver.exe aracı**</span><span class="sxs-lookup"><span data-stu-id="a4687-263">**The Clrver.exe tool**</span></span>

  <span data-ttu-id="a4687-264">Clr [Sürüm aracı 'nı (Clrver.exe)](../tools/clrver-exe-clr-version-tool.md) kullanarak bir bılgısayarda hangi CLR sürümlerinin yüklü olduğunu saptayın.</span><span class="sxs-lookup"><span data-stu-id="a4687-264">Use the [CLR Version tool (Clrver.exe)](../tools/clrver-exe-clr-version-tool.md) to determine which versions of the CLR are installed on a computer.</span></span> <span data-ttu-id="a4687-265">[Visual Studio için geliştirici komut istemi](../tools/developer-command-prompt-for-vs.md) açın ve girin `clrver` .</span><span class="sxs-lookup"><span data-stu-id="a4687-265">Open the [Developer Command Prompt for Visual Studio](../tools/developer-command-prompt-for-vs.md) and enter `clrver`.</span></span>

  <span data-ttu-id="a4687-266">Örnek çıktı:</span><span class="sxs-lookup"><span data-stu-id="a4687-266">Sample output:</span></span>

  ```console
  Versions installed on the machine:
  v2.0.50727
  v4.0.30319
  ```

- <span data-ttu-id="a4687-267">**`Environment`Sınıfı**</span><span class="sxs-lookup"><span data-stu-id="a4687-267">**The `Environment` class**</span></span>

  > [!IMPORTANT]
  > <span data-ttu-id="a4687-268">.NET Framework 4,5 ve sonraki sürümlerinde, <xref:System.Environment.Version%2A?displayProperty=nameWithType> CLR sürümünü algılamak için özelliğini kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="a4687-268">For .NET Framework 4.5 and later versions, don't use the <xref:System.Environment.Version%2A?displayProperty=nameWithType> property to detect the version of the CLR.</span></span> <span data-ttu-id="a4687-269">Bunun yerine, kayıt defterini [.NET Framework 4,5 ve sonraki sürümlerinde](#detect-net-framework-45-and-later-versions)açıklandığı gibi sorgulayın.</span><span class="sxs-lookup"><span data-stu-id="a4687-269">Instead, query the registry as described in [Detect .NET Framework 4.5 and later versions](#detect-net-framework-45-and-later-versions).</span></span>

  1. <span data-ttu-id="a4687-270"><xref:System.Environment.Version?displayProperty=nameWithType>Nesneyi almak için özelliği sorgulayın <xref:System.Version> .</span><span class="sxs-lookup"><span data-stu-id="a4687-270">Query the <xref:System.Environment.Version?displayProperty=nameWithType> property to retrieve a <xref:System.Version> object.</span></span>

     <span data-ttu-id="a4687-271">Döndürülen `System.Version` nesne, şu anda kodu yürüten çalışma zamanının sürümünü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a4687-271">The returned `System.Version` object identifies the version of the runtime that's currently executing the code.</span></span> <span data-ttu-id="a4687-272">Derleme sürümlerini veya çalışma zamanının bilgisayarda yüklü olabilecek diğer sürümlerini döndürmez.</span><span class="sxs-lookup"><span data-stu-id="a4687-272">It doesn't return assembly versions or other versions of the runtime that may have been installed on the computer.</span></span>

     <span data-ttu-id="a4687-273">.NET Framework sürümleri 4, 4,5, 4.5.1 ve 4.5.2 için, döndürülen nesnenin dize temsili <xref:System.Version> 4.0.30319 biçimindedir.*xxxxx*, *xxxxx* 42000 ' den küçük.</span><span class="sxs-lookup"><span data-stu-id="a4687-273">For .NET Framework versions 4, 4.5, 4.5.1, and 4.5.2, the string representation of the returned <xref:System.Version> object has the form 4.0.30319.*xxxxx*, where *xxxxx* is less than 42000.</span></span> <span data-ttu-id="a4687-274">.NET Framework 4,6 ve sonraki sürümlerinde, 4.0.30319.42000 biçiminde olur.</span><span class="sxs-lookup"><span data-stu-id="a4687-274">For .NET Framework 4.6 and later versions, it has the form 4.0.30319.42000.</span></span>

  1. <span data-ttu-id="a4687-275">**Sürüm** nesnesine sahip olduktan sonra, aşağıdaki gibi sorgulayın:</span><span class="sxs-lookup"><span data-stu-id="a4687-275">After you have the **Version** object, query it as follows:</span></span>

     - <span data-ttu-id="a4687-276">Ana yayın tanımlayıcısı için (örneğin, sürüm 4,0 için *4* ), <xref:System.Version.Major%2A?displayProperty=nameWithType> özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="a4687-276">For the major release identifier (for example, *4* for version 4.0), use the <xref:System.Version.Major%2A?displayProperty=nameWithType> property.</span></span>

     - <span data-ttu-id="a4687-277">Küçük yayın tanımlayıcısı için (örneğin, sürüm 4,0 için *0* ), <xref:System.Version.Minor%2A?displayProperty=nameWithType> özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="a4687-277">For the minor release identifier (for example, *0* for version 4.0), use the <xref:System.Version.Minor%2A?displayProperty=nameWithType> property.</span></span>

     - <span data-ttu-id="a4687-278">Tüm sürüm dizesi için (örneğin, *4.0.30319.18010*), <xref:System.Version.ToString%2A?displayProperty=nameWithType> yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="a4687-278">For the entire version string (for example, *4.0.30319.18010*), use the <xref:System.Version.ToString%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="a4687-279">Bu yöntem, kodu yürüten çalışma zamanının sürümünü yansıtan tek bir değer döndürür.</span><span class="sxs-lookup"><span data-stu-id="a4687-279">This method returns a single value that reflects the version of the runtime that's executing the code.</span></span> <span data-ttu-id="a4687-280">Bu, bilgisayarda yüklü olabilecek derleme sürümlerini veya diğer çalışma zamanı sürümlerini döndürmez.</span><span class="sxs-lookup"><span data-stu-id="a4687-280">It doesn't return assembly versions or other runtime versions that may be installed on the computer.</span></span>

  <span data-ttu-id="a4687-281">Aşağıdaki örnek <xref:System.Environment.Version%2A?displayProperty=nameWithType> CLR sürüm bilgilerini almak için özelliğini kullanır:</span><span class="sxs-lookup"><span data-stu-id="a4687-281">The following example uses the <xref:System.Environment.Version%2A?displayProperty=nameWithType> property to retrieve CLR version information:</span></span>

  ```csharp
  Console.WriteLine($"Version: {Environment.Version}");
  ```

  ```vb
  Console.WriteLine($"Version: {Environment.Version}")
  ```

  <span data-ttu-id="a4687-282">Örnek aşağıdakine benzer bir çıktı görüntüler:</span><span class="sxs-lookup"><span data-stu-id="a4687-282">The example displays output similar to the following:</span></span>

  ```output
  Version: 4.0.30319.18010
  ```

## <a name="see-also"></a><span data-ttu-id="a4687-283">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a4687-283">See also</span></span>

- [<span data-ttu-id="a4687-284">Nasıl yapılır: hangi .NET Framework güncelleştirmelerinin yükleneceğini belirleme</span><span class="sxs-lookup"><span data-stu-id="a4687-284">How to: Determine which .NET Framework updates are installed</span></span>](how-to-determine-which-net-framework-updates-are-installed.md)
- [<span data-ttu-id="a4687-285">Geliştiriciler için .NET Framework yükler</span><span class="sxs-lookup"><span data-stu-id="a4687-285">Install .NET Framework for developers</span></span>](../install/guide-for-developers.md)
- [<span data-ttu-id="a4687-286">.NET Framework sürümleri ve bağımlılıklar</span><span class="sxs-lookup"><span data-stu-id="a4687-286">.NET Framework versions and dependencies</span></span>](versions-and-dependencies.md)
