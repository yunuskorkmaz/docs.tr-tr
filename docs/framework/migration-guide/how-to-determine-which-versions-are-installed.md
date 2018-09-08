---
title: 'Nasıl yapılır: hangi .NET Framework sürümlerinin yüklü olduğunu belirleme'
ms.date: 04/10/2018
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
ms.openlocfilehash: 1874d5512f04f22b9c53bdc9e92d0c96e45d21c8
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44222746"
---
# <a name="how-to-determine-which-net-framework-versions-are-installed"></a><span data-ttu-id="87ec0-102">Nasıl yapılır: hangi .NET Framework sürümlerinin yüklü olduğunu belirleme</span><span class="sxs-lookup"><span data-stu-id="87ec0-102">How to: Determine which .NET Framework versions are installed</span></span>

<span data-ttu-id="87ec0-103">Kullanıcılar yükleyebilir ve kendi bilgisayarlarına .NET Framework'ün birden çok sürümünü çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="87ec0-103">Users can install and run multiple versions of the .NET Framework on their computers.</span></span> <span data-ttu-id="87ec0-104">Geliştirme veya uygulamanızı dağıtma, hangi .NET Framework sürümlerinin kullanıcının bilgisayarında yüklü olduğunu bilmeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="87ec0-104">When you develop or deploy your app, you might need to know which .NET Framework versions are installed on the user’s computer.</span></span> <span data-ttu-id="87ec0-105">Not: .NET Framework, ayrı ayrı uyarlandı iki ana bileşenden, oluşur</span><span class="sxs-lookup"><span data-stu-id="87ec0-105">Note that the .NET Framework consists of two main components, which are versioned separately:</span></span>  
  
-   <span data-ttu-id="87ec0-106">Koleksiyonları türlerin ve uygulamalarınız için işlevsellik sağlayan kaynaklar derlemelere kümesi.</span><span class="sxs-lookup"><span data-stu-id="87ec0-106">A set of assemblies, which are collections of types and resources that provide the functionality for your apps.</span></span> <span data-ttu-id="87ec0-107">.NET Framework ve derlemeleri, aynı sürüm numarasını paylaşır.</span><span class="sxs-lookup"><span data-stu-id="87ec0-107">The .NET Framework and assemblies share the same version number.</span></span>  
  
-   <span data-ttu-id="87ec0-108">Yönetir ve uygulamanızın kod yürüten ortak dil çalışma zamanı (CLR).</span><span class="sxs-lookup"><span data-stu-id="87ec0-108">The common language runtime (CLR), which manages and executes your app's code.</span></span> <span data-ttu-id="87ec0-109">CLR kendi sürüm numarasıyla tanımlanır (bkz [sürümler ve bağımlılıklar](~/docs/framework/migration-guide/versions-and-dependencies.md)).</span><span class="sxs-lookup"><span data-stu-id="87ec0-109">The CLR is identified by its own version number (see [Versions and Dependencies](~/docs/framework/migration-guide/versions-and-dependencies.md)).</span></span>  
  
 <span data-ttu-id="87ec0-110">Bir bilgisayarda yüklü .NET Framework sürümünü doğru bir listesini almak için kayıt defteri görüntüleyebilir veya kod içinde kayıt defterini sorgulayın:</span><span class="sxs-lookup"><span data-stu-id="87ec0-110">To get an accurate list of the .NET Framework versions installed on a computer, you can view the registry or query the registry in code:</span></span>  
  
 [<span data-ttu-id="87ec0-111">Kayıt defteri (sürüm 1-4) görüntüleme</span><span class="sxs-lookup"><span data-stu-id="87ec0-111">Viewing the registry (versions 1-4)</span></span>](#net_a)  
 [<span data-ttu-id="87ec0-112">Kayıt defteri (sürüm 4.5 ve üstü) görüntüleme</span><span class="sxs-lookup"><span data-stu-id="87ec0-112">Viewing the registry (version 4.5 and later)</span></span>](#net_b)  
 [<span data-ttu-id="87ec0-113">Kayıt defteri (sürüm 1-4) sorgulamak için kod kullanma</span><span class="sxs-lookup"><span data-stu-id="87ec0-113">Using code to query the registry (versions 1-4)</span></span>](#net_c)  
 [<span data-ttu-id="87ec0-114">Kayıt defteri (sürüm 4.5 ve üstü) sorgulamak için kod kullanma</span><span class="sxs-lookup"><span data-stu-id="87ec0-114">Using code to query the registry (version 4.5 and later)</span></span>](#net_d)  
 [<span data-ttu-id="87ec0-115">Kayıt defteri (sürüm 4.5 ve üstü) sorgulamak için PowerShell'i kullanma</span><span class="sxs-lookup"><span data-stu-id="87ec0-115">Using PowerShell to query the registry (version 4.5 and later)</span></span>](#ps_a)  
  
 <span data-ttu-id="87ec0-116">CLR sürümü bulmak için bir aracı veya kodu kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="87ec0-116">To find the CLR version, you can use a tool or code:</span></span>  
  
 [<span data-ttu-id="87ec0-117">Clrver Aracı'nı kullanma</span><span class="sxs-lookup"><span data-stu-id="87ec0-117">Using the Clrver tool</span></span>](#clr_a)  
 [<span data-ttu-id="87ec0-118">System.Environment sınıfı sorgulamak için kod kullanma</span><span class="sxs-lookup"><span data-stu-id="87ec0-118">Using code to query the System.Environment class</span></span>](#clr_b)  
  
 <span data-ttu-id="87ec0-119">.NET Framework'ün her sürümü için yüklü güncelleştirmeleri algılama hakkında daha fazla bilgi için bkz: [nasıl yapılır: belirlemek, .NET Framework Updates Are Installed](~/docs/framework/migration-guide/how-to-determine-which-net-framework-updates-are-installed.md).</span><span class="sxs-lookup"><span data-stu-id="87ec0-119">For information about detecting the installed updates for each version of the .NET Framework, see [How to: Determine Which .NET Framework Updates Are Installed](~/docs/framework/migration-guide/how-to-determine-which-net-framework-updates-are-installed.md).</span></span> <span data-ttu-id="87ec0-120">.NET Framework'ü yükleme hakkında daha fazla bilgi için bkz: [geliştiriciler için .NET Framework yükleme](../../../docs/framework/install/guide-for-developers.md).</span><span class="sxs-lookup"><span data-stu-id="87ec0-120">For information about installing the .NET Framework, see [Install the .NET Framework for developers](../../../docs/framework/install/guide-for-developers.md).</span></span>  
  
<a name="net_a"></a>   
## <a name="to-find-net-framework-versions-by-viewing-the-registry-net-framework-1-4"></a><span data-ttu-id="87ec0-121">Kayıt defteri (.NET Framework 1-4) görüntüleyerek .NET Framework sürümlerini bulmak için</span><span class="sxs-lookup"><span data-stu-id="87ec0-121">To find .NET Framework versions by viewing the registry (.NET Framework 1-4)</span></span>  
  
1.  <span data-ttu-id="87ec0-122">Üzerinde **Başlat** menüsünde seçin **çalıştırma**.</span><span class="sxs-lookup"><span data-stu-id="87ec0-122">On the **Start** menu, choose **Run**.</span></span>  
  
2.  <span data-ttu-id="87ec0-123">İçinde **açık** kutusuna **regedit.exe**.</span><span class="sxs-lookup"><span data-stu-id="87ec0-123">In the **Open** box, enter **regedit.exe**.</span></span>  
  
     <span data-ttu-id="87ec0-124">regedit.exe'yi çalıştırmak için yönetici kimlik bilgileriniz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="87ec0-124">You must have administrative credentials to run regedit.exe.</span></span>  
  
3.  <span data-ttu-id="87ec0-125">Kayıt Defteri Düzenleyicisi'nde, aşağıdaki alt anahtarı açın:</span><span class="sxs-lookup"><span data-stu-id="87ec0-125">In the Registry Editor, open the following subkey:</span></span>  
  
     `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP`  
  
     <span data-ttu-id="87ec0-126">Yüklenen sürümler NDP alt anahtarı altında listelenir.</span><span class="sxs-lookup"><span data-stu-id="87ec0-126">The installed versions are listed under the NDP subkey.</span></span> <span data-ttu-id="87ec0-127">Sürüm numarasını depolanan **sürüm** girişi.</span><span class="sxs-lookup"><span data-stu-id="87ec0-127">The version number is stored in the **Version** entry.</span></span> <span data-ttu-id="87ec0-128">İçin [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] **sürüm** girdidir istemci veya tam alt anahtarın (NDP'nin), altında veya her iki alt altında.</span><span class="sxs-lookup"><span data-stu-id="87ec0-128">For the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] the **Version** entry is under the Client or Full subkey (under NDP), or under both subkeys.</span></span>  
  

    > [!NOTE]
    > <span data-ttu-id="87ec0-129">Kayıt defterindeki "NET Framework Kurulum" klasörü, nokta karakteri ile başlamaz.</span><span class="sxs-lookup"><span data-stu-id="87ec0-129">The "NET Framework Setup" folder in the registry does not begin with a period.</span></span>

<a name="net_b"></a> 
## <a name="to-find-net-framework-versions-by-viewing-the-registry-net-framework-45-and-later"></a><span data-ttu-id="87ec0-130">Kayıt defteri (.NET Framework 4.5 ve üstü) görüntüleyerek .NET Framework sürümlerini bulmak için</span><span class="sxs-lookup"><span data-stu-id="87ec0-130">To find .NET Framework versions by viewing the registry (.NET Framework 4.5 and later)</span></span>

1. <span data-ttu-id="87ec0-131">Üzerinde **Başlat** menüsünde seçin **çalıştırma**.</span><span class="sxs-lookup"><span data-stu-id="87ec0-131">On the **Start** menu, choose **Run**.</span></span>

2. <span data-ttu-id="87ec0-132">İçinde **açık** kutusuna **regedit.exe**.</span><span class="sxs-lookup"><span data-stu-id="87ec0-132">In the **Open** box, enter **regedit.exe**.</span></span>

     <span data-ttu-id="87ec0-133">regedit.exe'yi çalıştırmak için yönetici kimlik bilgileriniz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="87ec0-133">You must have administrative credentials to run regedit.exe.</span></span>

3. <span data-ttu-id="87ec0-134">Kayıt Defteri Düzenleyicisi'nde, aşağıdaki alt anahtarı açın:</span><span class="sxs-lookup"><span data-stu-id="87ec0-134">In the Registry Editor, open the following subkey:</span></span>

     `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full`

     <span data-ttu-id="87ec0-135">Unutmayın yoluna `Full` alt anahtar alt anahtar içerir `Net Framework` yerine `.NET Framework`.</span><span class="sxs-lookup"><span data-stu-id="87ec0-135">Note that the path to the `Full` subkey includes the subkey `Net Framework` rather than `.NET Framework`.</span></span>

    > [!NOTE]
    > <span data-ttu-id="87ec0-136">Varsa `Full` alt mevcut değil, ardından .NET Framework 4.5 yok veya sonraki bir sürümü yüklü.</span><span class="sxs-lookup"><span data-stu-id="87ec0-136">If the `Full` subkey is not present, then you do not have the .NET Framework 4.5 or later installed.</span></span>

     <span data-ttu-id="87ec0-137">Adlı bir DWORD değerini denetleyin `Release`.</span><span class="sxs-lookup"><span data-stu-id="87ec0-137">Check for a DWORD value named `Release`.</span></span> <span data-ttu-id="87ec0-138">Varlığını `Release` DWORD gösterir [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] ya da daha yeni bu bilgisayarda yüklü.</span><span class="sxs-lookup"><span data-stu-id="87ec0-138">The existence of the `Release` DWORD indicates that the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] or newer has been installed on that computer.</span></span>

     <span data-ttu-id="87ec0-139">![.NET Framework 4.5 için kayıt defteri girişi. ](../../../docs/framework/migration-guide/media/clr-installdir.png "CLR_InstallDir")</span><span class="sxs-lookup"><span data-stu-id="87ec0-139">![The registry entry for the .NET Framework 4.5.](../../../docs/framework/migration-guide/media/clr-installdir.png "CLR_InstallDir")</span></span>

     <span data-ttu-id="87ec0-140">Değerini `Release` DWORD hangi .NET Framework sürümünün yüklü olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="87ec0-140">The value of the `Release` DWORD indicates which version of the .NET Framework is installed.</span></span>

    [!INCLUDE[Release key values note](~/includes/version-keys-note.md)]

    |<span data-ttu-id="87ec0-141">Yayın DWORD değeri</span><span class="sxs-lookup"><span data-stu-id="87ec0-141">Value of the Release DWORD</span></span>|<span data-ttu-id="87ec0-142">Sürüm</span><span class="sxs-lookup"><span data-stu-id="87ec0-142">Version</span></span>|
    |--------------------------------|-------------|
    |<span data-ttu-id="87ec0-143">378389</span><span class="sxs-lookup"><span data-stu-id="87ec0-143">378389</span></span>|<span data-ttu-id="87ec0-144">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="87ec0-144">.NET Framework 4.5</span></span>|
    |<span data-ttu-id="87ec0-145">378675</span><span class="sxs-lookup"><span data-stu-id="87ec0-145">378675</span></span>|<span data-ttu-id="87ec0-146">.NET framework 4.5.1 Windows 8.1 veya Windows Server 2012 R2 ile yüklenen</span><span class="sxs-lookup"><span data-stu-id="87ec0-146">.NET Framework 4.5.1 installed with Windows 8.1 or Windows Server 2012 R2</span></span>|
    |<span data-ttu-id="87ec0-147">378758</span><span class="sxs-lookup"><span data-stu-id="87ec0-147">378758</span></span>|<span data-ttu-id="87ec0-148">.NET framework 4.5.1 Windows 8, Windows 7 SP1 veya Windows Vista SP2 yüklü</span><span class="sxs-lookup"><span data-stu-id="87ec0-148">.NET Framework 4.5.1 installed on Windows 8, Windows 7 SP1, or Windows Vista SP2</span></span>|
    |<span data-ttu-id="87ec0-149">379893</span><span class="sxs-lookup"><span data-stu-id="87ec0-149">379893</span></span>|<span data-ttu-id="87ec0-150">.NET Framework 4.5.2</span><span class="sxs-lookup"><span data-stu-id="87ec0-150">.NET Framework 4.5.2</span></span>|
    |<span data-ttu-id="87ec0-151">Yalnızca Windows 10 sistemlerinde: 393295</span><span class="sxs-lookup"><span data-stu-id="87ec0-151">On Windows 10 systems only: 393295</span></span><br /><br /> <span data-ttu-id="87ec0-152">Diğer tüm işletim sistemi sürümlerinde: 393297</span><span class="sxs-lookup"><span data-stu-id="87ec0-152">On all other OS versions: 393297</span></span>|[!INCLUDE[net_v46](../../../includes/net-v46-md.md)]|
    |<span data-ttu-id="87ec0-153">Yalnızca Windows 10 Kasım güncelleştirmesi sistemlerinde: 394254</span><span class="sxs-lookup"><span data-stu-id="87ec0-153">On Windows 10 November Update systems only: 394254</span></span><br /><br /> <span data-ttu-id="87ec0-154">Diğer tüm işletim sistemi sürümlerinde: 394271</span><span class="sxs-lookup"><span data-stu-id="87ec0-154">On all other OS versions: 394271</span></span>|[!INCLUDE[net_v461](../../../includes/net-v461-md.md)]|
    |<span data-ttu-id="87ec0-155">Windows 10 Yıldönümü güncelleştirmesi ve Windows Server 2016:394802</span><span class="sxs-lookup"><span data-stu-id="87ec0-155">On Windows 10 Anniversary Update and Windows Server 2016: 394802</span></span><br /><br /> <span data-ttu-id="87ec0-156">Diğer tüm işletim sistemi sürümlerinde: 394806</span><span class="sxs-lookup"><span data-stu-id="87ec0-156">On all other OS versions: 394806</span></span>|[!INCLUDE[net_v462](../../../includes/net-v462-md.md)]| 
    |<span data-ttu-id="87ec0-157">Üzerinde Windows 10 Creators güncelleştirmesi yalnızca: 460798</span><span class="sxs-lookup"><span data-stu-id="87ec0-157">On Windows 10 Creators Update only: 460798</span></span><br/><br/> <span data-ttu-id="87ec0-158">Diğer tüm işletim sistemi sürümlerinde: 460805</span><span class="sxs-lookup"><span data-stu-id="87ec0-158">On all other OS versions: 460805</span></span> | <span data-ttu-id="87ec0-159">.NET framework 4.7</span><span class="sxs-lookup"><span data-stu-id="87ec0-159">.NET Framework 4.7</span></span> |
    |<span data-ttu-id="87ec0-160">Windows 10 Fall Creators Update üzerinde yalnızca: 461308</span><span class="sxs-lookup"><span data-stu-id="87ec0-160">On Windows 10 Fall Creators Update only: 461308</span></span><br/><br/> <span data-ttu-id="87ec0-161">Diğer tüm işletim sistemi sürümlerinde: 461310</span><span class="sxs-lookup"><span data-stu-id="87ec0-161">On all other OS versions: 461310</span></span> | <span data-ttu-id="87ec0-162">.NET framework 4.7.1</span><span class="sxs-lookup"><span data-stu-id="87ec0-162">.NET Framework 4.7.1</span></span> |
    |<span data-ttu-id="87ec0-163">Yalnızca Windows 10 Nisan 2018 güncelleştirmesi: 461808</span><span class="sxs-lookup"><span data-stu-id="87ec0-163">On Windows 10 April 2018 Update only: 461808</span></span><br/><br/> <span data-ttu-id="87ec0-164">Diğer tüm işletim sistemi sürümlerinde: 461814</span><span class="sxs-lookup"><span data-stu-id="87ec0-164">On all other OS versions: 461814</span></span>| <span data-ttu-id="87ec0-165">.NET framework 4.7.2</span><span class="sxs-lookup"><span data-stu-id="87ec0-165">.NET Framework 4.7.2</span></span> |
    
<a name="net_c"></a> 
## <a name="to-find-net-framework-versions-by-querying-the-registry-in-code-net-framework-1-4"></a><span data-ttu-id="87ec0-166">(.NET Framework 1-4) kod içinde kayıt defterini sorgulayarak .NET Framework sürümlerini bulmak için</span><span class="sxs-lookup"><span data-stu-id="87ec0-166">To find .NET Framework versions by querying the registry in code (.NET Framework 1-4)</span></span>

- <span data-ttu-id="87ec0-167">Kullanım <xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType> Software\Microsoft\NET Framework Setup\NDP\ subkey under HKEY_LOCAL_MACHINE Windows kayıt defterinde erişmek için sınıf.</span><span class="sxs-lookup"><span data-stu-id="87ec0-167">Use the <xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType> class to access the Software\Microsoft\NET Framework Setup\NDP\ subkey under HKEY_LOCAL_MACHINE in the Windows registry.</span></span>

     <span data-ttu-id="87ec0-168">Aşağıdaki kod, bu sorgunun bir örneğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="87ec0-168">The following code shows an example of this query.</span></span>

    > [!NOTE]
    > <span data-ttu-id="87ec0-169">Bu kodu nasıl algılanacağını göstermez [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] veya üzeri.</span><span class="sxs-lookup"><span data-stu-id="87ec0-169">This code does not show how to detect the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] or later.</span></span> <span data-ttu-id="87ec0-170">Denetleme `Release` önceki bölümde açıklandığı gibi bu sürümleri algılamak için DWORD.</span><span class="sxs-lookup"><span data-stu-id="87ec0-170">Check the `Release` DWORD to detect those versions, as described in the previous section.</span></span> <span data-ttu-id="87ec0-171">Algılayan kod için [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] veya sonraki sürümlerinde, bu makalenin sonraki bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="87ec0-171">For code that does detect the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] or later versions, see the next section in this article.</span></span>

     [!code-csharp[ListVersions](../../../samples/snippets/csharp/framework/migration-guide/versions-installed1.cs)]
     [!code-vb[ListVersions](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed1.vb)]

     <span data-ttu-id="87ec0-172">Örnekte aşağıdakine benzer bir çıktı oluşturulur:</span><span class="sxs-lookup"><span data-stu-id="87ec0-172">The example produces output that's similar to the following:</span></span>

    ```
    v2.0.50727  2.0.50727.4016  SP2
    v3.0  3.0.30729.4037  SP2
    v3.5  3.5.30729.01  SP1
    v4
      Client  4.0.30319
      Full  4.0.30319
    ```

<a name="net_d"></a> 
## <a name="to-find-net-framework-versions-by-querying-the-registry-in-code-net-framework-45-and-later"></a><span data-ttu-id="87ec0-173">(.NET Framework 4.5 ve üstü) kod içinde kayıt defterini sorgulayarak .NET Framework sürümlerini bulmak için</span><span class="sxs-lookup"><span data-stu-id="87ec0-173">To find .NET Framework versions by querying the registry in code (.NET Framework 4.5 and later)</span></span>

1. <span data-ttu-id="87ec0-174">Varlığını `Release` DWORD .NET Framework 4.5 veya sonraki bir bilgisayarda yüklü olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="87ec0-174">The existence of the `Release` DWORD indicates that the .NET Framework 4.5 or later has been installed on a computer.</span></span> <span data-ttu-id="87ec0-175">Anahtar sözcüğü değerini yüklü olan sürümü gösterir.</span><span class="sxs-lookup"><span data-stu-id="87ec0-175">The value of the keyword indicates the installed version.</span></span> <span data-ttu-id="87ec0-176">Bu anahtar sözcük denetlemek için kullanmak <xref:Microsoft.Win32.RegistryKey.OpenBaseKey%2A> ve <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A> yöntemlerinin <xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType> Windows kayıt defterinde HKEY_LOCAL_MACHINE altındaki Software\Microsoft\NET Framework Setup\NDP\v4\Full alt anahtarına erişmek için sınıf.</span><span class="sxs-lookup"><span data-stu-id="87ec0-176">To check this keyword, use the <xref:Microsoft.Win32.RegistryKey.OpenBaseKey%2A> and <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A> methods of the <xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType> class to access the Software\Microsoft\NET Framework Setup\NDP\v4\Full subkey under HKEY_LOCAL_MACHINE in the Windows registry.</span></span>

2. <span data-ttu-id="87ec0-177">Değerini kontrol edin `Release` yüklenen sürümü belirlemek için anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="87ec0-177">Check the value of the `Release` keyword to determine the installed version.</span></span> <span data-ttu-id="87ec0-178">İleri uyumlu olacak şekilde tabloda listelenen değerler eşit veya büyük bir değer denetleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="87ec0-178">To be forward-compatible, you can check for a value greater than or equal to the values listed in the table.</span></span> <span data-ttu-id="87ec0-179">.NET Framework sürümleri şunlardır ve ilişkili `Release` anahtar sözcükleri.</span><span class="sxs-lookup"><span data-stu-id="87ec0-179">Here are the .NET Framework versions and associated `Release` keywords.</span></span>

    [!INCLUDE[Release key values note](~/includes/version-keys-note.md)]

    |<span data-ttu-id="87ec0-180">Sürüm</span><span class="sxs-lookup"><span data-stu-id="87ec0-180">Version</span></span>|<span data-ttu-id="87ec0-181">Yayın DWORD değeri</span><span class="sxs-lookup"><span data-stu-id="87ec0-181">Value of the Release DWORD</span></span>|
    |-------------|--------------------------------|
    |<span data-ttu-id="87ec0-182">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="87ec0-182">.NET Framework 4.5</span></span>|<span data-ttu-id="87ec0-183">378389</span><span class="sxs-lookup"><span data-stu-id="87ec0-183">378389</span></span>|
    |<span data-ttu-id="87ec0-184">.NET framework 4.5.1 Windows 8.1 ile yüklü</span><span class="sxs-lookup"><span data-stu-id="87ec0-184">.NET Framework 4.5.1 installed with Windows 8.1</span></span>|<span data-ttu-id="87ec0-185">378675</span><span class="sxs-lookup"><span data-stu-id="87ec0-185">378675</span></span>|
    |<span data-ttu-id="87ec0-186">.NET framework 4.5.1 Windows 8, Windows 7 SP1 veya Windows Vista SP2 yüklü</span><span class="sxs-lookup"><span data-stu-id="87ec0-186">.NET Framework 4.5.1 installed on Windows 8, Windows 7 SP1, or Windows Vista SP2</span></span>|<span data-ttu-id="87ec0-187">378758</span><span class="sxs-lookup"><span data-stu-id="87ec0-187">378758</span></span>|
    |<span data-ttu-id="87ec0-188">.NET Framework 4.5.2</span><span class="sxs-lookup"><span data-stu-id="87ec0-188">.NET Framework 4.5.2</span></span>|<span data-ttu-id="87ec0-189">379893</span><span class="sxs-lookup"><span data-stu-id="87ec0-189">379893</span></span>|
    |<span data-ttu-id="87ec0-190">.NET framework 4.6 ile Windows 10 yüklü</span><span class="sxs-lookup"><span data-stu-id="87ec0-190">.NET Framework 4.6 installed with Windows 10</span></span>|<span data-ttu-id="87ec0-191">393295</span><span class="sxs-lookup"><span data-stu-id="87ec0-191">393295</span></span>|
    |<span data-ttu-id="87ec0-192">Diğer tüm Windows işletim sistemi sürümlerinde yüklü .NET framework 4.6</span><span class="sxs-lookup"><span data-stu-id="87ec0-192">.NET Framework 4.6 installed on all other Windows OS versions</span></span>|<span data-ttu-id="87ec0-193">393297</span><span class="sxs-lookup"><span data-stu-id="87ec0-193">393297</span></span>|
    |<span data-ttu-id="87ec0-194">.NET framework 4.6.1 yüklü Windows 10'da</span><span class="sxs-lookup"><span data-stu-id="87ec0-194">.NET Framework 4.6.1 installed on Windows 10</span></span>|<span data-ttu-id="87ec0-195">394254</span><span class="sxs-lookup"><span data-stu-id="87ec0-195">394254</span></span>|
    |<span data-ttu-id="87ec0-196">.NET framework 4.6.1 yüklü diğer tüm Windows işletim sistemi sürümlerinde</span><span class="sxs-lookup"><span data-stu-id="87ec0-196">.NET Framework 4.6.1 installed on all other Windows OS versions</span></span>|<span data-ttu-id="87ec0-197">394271</span><span class="sxs-lookup"><span data-stu-id="87ec0-197">394271</span></span>|
    |<span data-ttu-id="87ec0-198">.NET framework 4.6.2, Windows 10 Yıldönümü güncelleştirmesi ve Windows Server 2016 yüklü</span><span class="sxs-lookup"><span data-stu-id="87ec0-198">.NET Framework 4.6.2 installed on Windows 10 Anniversary Update and Windows Server 2016</span></span>|<span data-ttu-id="87ec0-199">394802</span><span class="sxs-lookup"><span data-stu-id="87ec0-199">394802</span></span>|
    |<span data-ttu-id="87ec0-200">.NET framework 4.6.2 diğer tüm Windows işletim sistemi sürümlerinde yüklü</span><span class="sxs-lookup"><span data-stu-id="87ec0-200">.NET Framework 4.6.2 installed on all other Windows OS versions</span></span>|<span data-ttu-id="87ec0-201">394806</span><span class="sxs-lookup"><span data-stu-id="87ec0-201">394806</span></span>|
    |<span data-ttu-id="87ec0-202">Windows 10 Creators Update üzerinde yüklü olan .NET framework 4.7</span><span class="sxs-lookup"><span data-stu-id="87ec0-202">.NET Framework 4.7 installed on Windows 10 Creators Update</span></span>|<span data-ttu-id="87ec0-203">460798</span><span class="sxs-lookup"><span data-stu-id="87ec0-203">460798</span></span>|
    |<span data-ttu-id="87ec0-204">Diğer tüm Windows işletim sistemi sürümlerinde yüklü .NET framework 4.7</span><span class="sxs-lookup"><span data-stu-id="87ec0-204">.NET Framework 4.7 installed on all other Windows OS versions</span></span>|<span data-ttu-id="87ec0-205">460805</span><span class="sxs-lookup"><span data-stu-id="87ec0-205">460805</span></span>|
    |<span data-ttu-id="87ec0-206">.NET framework 4.7.1 Windows 10 Fall Creators Update üzerinde yüklü</span><span class="sxs-lookup"><span data-stu-id="87ec0-206">.NET Framework 4.7.1 installed on Windows 10 Fall Creators Update</span></span>|<span data-ttu-id="87ec0-207">461308</span><span class="sxs-lookup"><span data-stu-id="87ec0-207">461308</span></span>|
    |<span data-ttu-id="87ec0-208">.NET framework 4.7.1 diğer tüm Windows işletim sistemi sürümlerinde yüklü</span><span class="sxs-lookup"><span data-stu-id="87ec0-208">.NET Framework 4.7.1 installed on all other Windows OS versions</span></span>|<span data-ttu-id="87ec0-209">461310</span><span class="sxs-lookup"><span data-stu-id="87ec0-209">461310</span></span>|
    |<span data-ttu-id="87ec0-210">.NET framework Windows yüklü 4.7.2 10 Nisan 2018 güncelleştirmesi</span><span class="sxs-lookup"><span data-stu-id="87ec0-210">.NET Framework 4.7.2 installed on Windows 10 April 2018 Update</span></span>|<span data-ttu-id="87ec0-211">461808</span><span class="sxs-lookup"><span data-stu-id="87ec0-211">461808</span></span>|
    |<span data-ttu-id="87ec0-212">.NET framework yüklü diğer tüm Windows işletim sistemi sürümlerinde 4.7.2</span><span class="sxs-lookup"><span data-stu-id="87ec0-212">.NET Framework 4.7.2 installed on all other Windows OS versions</span></span>|<span data-ttu-id="87ec0-213">461814</span><span class="sxs-lookup"><span data-stu-id="87ec0-213">461814</span></span>|
    
     <span data-ttu-id="87ec0-214">Aşağıdaki örnek denetimlerini `Release` belirlemek için kayıt defteri değerindeki olmadığını [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] veya .NET Framework'ün daha sonraki bir sürümü yüklü.</span><span class="sxs-lookup"><span data-stu-id="87ec0-214">The following example checks the `Release` value in the registry to determine whether the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] or a later version of the .NET Framework is installed.</span></span>

     [!code-csharp[ListVersions#5](../../../samples/snippets/csharp/framework/migration-guide/versions-installed3.cs)]
     [!code-vb[ListVersions#5](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed3.vb)]

     <span data-ttu-id="87ec0-215">Bu örnek, sürüm denetimi için önerilen yöntem aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="87ec0-215">This example follows the recommended practice for version checking:</span></span>

    - <span data-ttu-id="87ec0-216">Denetlediği olup olmadığını değerini `Release` giriş *büyüktür veya eşittir* bilinen yayın anahtarları değeri.</span><span class="sxs-lookup"><span data-stu-id="87ec0-216">It checks whether the value of the `Release` entry is *greater than or equal to* the value of the known release keys.</span></span>

    - <span data-ttu-id="87ec0-217">Eski sürümü için en son sürüm sırayla denetler.</span><span class="sxs-lookup"><span data-stu-id="87ec0-217">It checks in order from most recent version to earliest version.</span></span>

<a name="ps_a"></a> 
## <a name="to-check-for-a-minimum-required-net-framework-version-by-querying-the-registry-in-powershell-net-framework-45-and-later"></a><span data-ttu-id="87ec0-218">PowerShell (.NET Framework 4.5 ve üzeri) içinde kayıt defterini sorgulayarak için gereken en düşük .NET Framework sürümü denetlemek için</span><span class="sxs-lookup"><span data-stu-id="87ec0-218">To check for a minimum-required .NET Framework version by querying the registry in PowerShell (.NET Framework 4.5 and later)</span></span>

- <span data-ttu-id="87ec0-219">Aşağıdaki örnek değerini denetler `Release` belirlemek için anahtar sözcüğü olup olmadığını .NET Framework 4.6.2 veya üzeri yüklü, Windows işletim sistemi sürümü bakılmaksızın (döndüren `True` etkinleştirilmişse ve `False` yoksa).</span><span class="sxs-lookup"><span data-stu-id="87ec0-219">The following example checks the value of the `Release` keyword to determine whether .NET Framework 4.6.2 or higher is installed, regardless of Windows OS version (returning `True` if it is and `False` otherwise).</span></span>

    ```PowerShell
    Get-ChildItem "HKLM:SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full\" | Get-ItemPropertyValue -Name Release | ForEach-Object { $_ -ge 394802 } 
    ```

    <span data-ttu-id="87ec0-220">Değiştirebilirsiniz `394802` için farklı bir gerekli en düşük .NET Framework sürüm denetlemek için aşağıdaki tabloda önceki örnekte başka bir değere sahip.</span><span class="sxs-lookup"><span data-stu-id="87ec0-220">You can replace `394802` in the previous example with another value from the following table to check for a different minimum-required .NET Framework version.</span></span>
  
    |<span data-ttu-id="87ec0-221">Sürüm</span><span class="sxs-lookup"><span data-stu-id="87ec0-221">Version</span></span>|<span data-ttu-id="87ec0-222">En düşük yayın DWORD değeri</span><span class="sxs-lookup"><span data-stu-id="87ec0-222">Minimum value of the Release DWORD</span></span>|
    |-------------|--------------------------------|
    |<span data-ttu-id="87ec0-223">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="87ec0-223">.NET Framework 4.5</span></span>|<span data-ttu-id="87ec0-224">378389</span><span class="sxs-lookup"><span data-stu-id="87ec0-224">378389</span></span>|
    |<span data-ttu-id="87ec0-225">.NET Framework 4.5.1</span><span class="sxs-lookup"><span data-stu-id="87ec0-225">.NET Framework 4.5.1</span></span>|<span data-ttu-id="87ec0-226">378675</span><span class="sxs-lookup"><span data-stu-id="87ec0-226">378675</span></span>|
    |<span data-ttu-id="87ec0-227">.NET Framework 4.5.2</span><span class="sxs-lookup"><span data-stu-id="87ec0-227">.NET Framework 4.5.2</span></span>|<span data-ttu-id="87ec0-228">379893</span><span class="sxs-lookup"><span data-stu-id="87ec0-228">379893</span></span>|
    |[!INCLUDE[net_v46](../../../includes/net-v46-md.md)]|<span data-ttu-id="87ec0-229">393295</span><span class="sxs-lookup"><span data-stu-id="87ec0-229">393295</span></span>|
    |[!INCLUDE[net_v461](../../../includes/net-v461-md.md)]|<span data-ttu-id="87ec0-230">394254</span><span class="sxs-lookup"><span data-stu-id="87ec0-230">394254</span></span>|
    |[!INCLUDE[net_v462](../../../includes/net-v462-md.md)]|<span data-ttu-id="87ec0-231">394802</span><span class="sxs-lookup"><span data-stu-id="87ec0-231">394802</span></span>|
    |<span data-ttu-id="87ec0-232">.NET framework 4.7</span><span class="sxs-lookup"><span data-stu-id="87ec0-232">.NET Framework 4.7</span></span>|<span data-ttu-id="87ec0-233">460798</span><span class="sxs-lookup"><span data-stu-id="87ec0-233">460798</span></span>|
    |<span data-ttu-id="87ec0-234">.NET framework 4.7.1</span><span class="sxs-lookup"><span data-stu-id="87ec0-234">.NET Framework 4.7.1</span></span>|<span data-ttu-id="87ec0-235">461308</span><span class="sxs-lookup"><span data-stu-id="87ec0-235">461308</span></span>|
    |<span data-ttu-id="87ec0-236">.NET framework 4.7.2</span><span class="sxs-lookup"><span data-stu-id="87ec0-236">.NET Framework 4.7.2</span></span>|<span data-ttu-id="87ec0-237">461808</span><span class="sxs-lookup"><span data-stu-id="87ec0-237">461808</span></span>|

<a name="clr_a"></a> 
## <a name="to-find-the-current-runtime-version-by-using-the-clrver-tool"></a><span data-ttu-id="87ec0-238">Clrver aracını kullanarak geçerli çalışma zamanı sürümünü bulmak için</span><span class="sxs-lookup"><span data-stu-id="87ec0-238">To find the current runtime version by using the Clrver tool</span></span>

- <span data-ttu-id="87ec0-239">Bilgisayarda ortak dil çalışma zamanının hangi sürümlerinin yüklü olduğunu saptamak için CLR Sürüm Aracı'nı (Clrver.exe) kullanın.</span><span class="sxs-lookup"><span data-stu-id="87ec0-239">Use the CLR Version Tool (Clrver.exe) to determine which versions of the common language runtime are installed on a computer.</span></span>

     <span data-ttu-id="87ec0-240">Bir Visual Studio komut isteminden girin `clrver`.</span><span class="sxs-lookup"><span data-stu-id="87ec0-240">From a Visual Studio Command Prompt, enter `clrver`.</span></span> <span data-ttu-id="87ec0-241">Bu komut aşağıdakine benzer bir çıktı oluşturur:</span><span class="sxs-lookup"><span data-stu-id="87ec0-241">This command produces output similar to the following:</span></span>

    ```
    Versions installed on the machine:
    v2.0.50727
    v4.0.30319
    ```

     <span data-ttu-id="87ec0-242">Bu aracı kullanma hakkında daha fazla bilgi için bkz. [Clrver.exe (CLR sürüm aracı)](~/docs/framework/tools/clrver-exe-clr-version-tool.md).</span><span class="sxs-lookup"><span data-stu-id="87ec0-242">For more information about using this tool, see [Clrver.exe (CLR Version Tool)](~/docs/framework/tools/clrver-exe-clr-version-tool.md).</span></span>

<a name="clr_b"></a> 
## <a name="to-find-the-current-runtime-version-by-querying-the-environment-class-in-code"></a><span data-ttu-id="87ec0-243">Kod içinde Ortam sınıfını sorgulayarak geçerli çalışma zamanı sürümünü bulmak için</span><span class="sxs-lookup"><span data-stu-id="87ec0-243">To find the current runtime version by querying the Environment class in code</span></span>

- <span data-ttu-id="87ec0-244">Sorgu <xref:System.Environment.Version%2A?displayProperty=nameWithType> almak için özellik bir <xref:System.Version> şu anda kodu yürüten çalışma zamanının sürümünü tanımlayan nesne.</span><span class="sxs-lookup"><span data-stu-id="87ec0-244">Query the <xref:System.Environment.Version%2A?displayProperty=nameWithType> property to retrieve a <xref:System.Version> object that identifies the version of the runtime that is currently executing the code.</span></span> <span data-ttu-id="87ec0-245">Kullanabileceğiniz <xref:System.Version.Major%2A?displayProperty=nameWithType> (örneğin, "4" sürüm 4.0 için), ana sürüm tanıtıcısını almak için özellik <xref:System.Version.Minor%2A?displayProperty=nameWithType> (örneğin, "0" sürüm 4.0 için), alt sürüm tanıtıcısını almak için özellik veya <xref:System.Object.ToString%2A?displayProperty=nameWithType> tüm sürümü almak için yöntemi dize ("aşağıdaki kodda gösterildiği gibi 4.0.30319.18010").</span><span class="sxs-lookup"><span data-stu-id="87ec0-245">You can use the <xref:System.Version.Major%2A?displayProperty=nameWithType> property to get the major release identifier (for example, "4" for version 4.0), the <xref:System.Version.Minor%2A?displayProperty=nameWithType> property to get the minor release identifier (for example, "0" for version 4.0), or the <xref:System.Object.ToString%2A?displayProperty=nameWithType> method to get the entire version string (for example, "4.0.30319.18010", as shown in the following code).</span></span> <span data-ttu-id="87ec0-246">Bu özellik, kodu şu anda yürüten çalışma zamanı sürümünü gösteren tek bir değer döndürür; diğer sürümleri bilgisayarda yüklü çalışma zamanı derleme sürümleri döndürmez.</span><span class="sxs-lookup"><span data-stu-id="87ec0-246">This property returns a single value that reflects the version of the runtime that is currently executing the code; it does not return assembly versions or other versions of the runtime that may have been installed on the computer.</span></span>

     <span data-ttu-id="87ec0-247">4, 4.5, 4.5.1 ve 4.5.2'yi, .NET Framework sürümleri için <xref:System.Environment.Version%2A?displayProperty=nameWithType> özelliği döndürür bir <xref:System.Version> nesnenin dize temsili olan form `4.0.30319.xxxxx`.</span><span class="sxs-lookup"><span data-stu-id="87ec0-247">For the .NET Framework Versions 4, 4.5, 4.5.1, and 4.5.2, the <xref:System.Environment.Version%2A?displayProperty=nameWithType> property returns a <xref:System.Version> object whose string representation has the form `4.0.30319.xxxxx`.</span></span> <span data-ttu-id="87ec0-248">.NET Framework 4.6 ve daha sonra bu biçimde `4.0.30319.42000`.</span><span class="sxs-lookup"><span data-stu-id="87ec0-248">For the .NET Framework 4.6 and later, it has the form `4.0.30319.42000`.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="87ec0-249">İçin [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] ve kullanarak daha sonra önermiyoruz <xref:System.Environment.Version%2A?displayProperty=nameWithType> özelliği çalışma zamanı sürümünü algılayamaz.</span><span class="sxs-lookup"><span data-stu-id="87ec0-249">For the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] and later, we do not recommend using the  <xref:System.Environment.Version%2A?displayProperty=nameWithType> property to detect the version of the runtime.</span></span> <span data-ttu-id="87ec0-250">Bunun yerine, kayıt defteri sorgu açıklandığı öneririz [(.NET Framework 4.5 ve üstü) kod içinde kayıt defterini sorgulayarak .NET Framework sürümlerini bulmak için](#net_d) bu makalenin önceki kısımlarında bölümü.</span><span class="sxs-lookup"><span data-stu-id="87ec0-250">Instead, we recommend that you query the registry, as described in the [To find .NET Framework versions by querying the registry in code (.NET Framework 4.5 and later)](#net_d) section earlier in this article.</span></span>

     <span data-ttu-id="87ec0-251">İşte bir örnek sorgulama <xref:System.Environment.Version%2A?displayProperty=nameWithType> özelliği çalışma zamanı sürüm bilgileri için:</span><span class="sxs-lookup"><span data-stu-id="87ec0-251">Here's an example of querying the <xref:System.Environment.Version%2A?displayProperty=nameWithType> property for runtime version information:</span></span>

     [!code-csharp[ListVersions](../../../samples/snippets/csharp/framework/migration-guide/versions-installed2.cs)]
     [!code-vb[ListVersions](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed2.vb)]

     <span data-ttu-id="87ec0-252">Örnekte aşağıdakine benzer bir çıktı oluşturulur:</span><span class="sxs-lookup"><span data-stu-id="87ec0-252">The example produces output that's similar to the following:</span></span>

    ```
    Version: 4.0.30319.18010
    ```

## <a name="see-also"></a><span data-ttu-id="87ec0-253">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="87ec0-253">See also</span></span>

[<span data-ttu-id="87ec0-254">Nasıl yapılır: Hangi .NET Framework Güncelleştirmelerinin Yüklü Olduğunu Belirleme</span><span class="sxs-lookup"><span data-stu-id="87ec0-254">How to: Determine Which .NET Framework Updates Are Installed</span></span>](~/docs/framework/migration-guide/how-to-determine-which-net-framework-updates-are-installed.md)  
[<span data-ttu-id="87ec0-255">Geliştiriciler için .NET Framework'ü yükleme</span><span class="sxs-lookup"><span data-stu-id="87ec0-255">Install the .NET Framework for developers</span></span>](../../../docs/framework/install/guide-for-developers.md)  
[<span data-ttu-id="87ec0-256">Sürümler ve Bağımlılıklar</span><span class="sxs-lookup"><span data-stu-id="87ec0-256">Versions and Dependencies</span></span>](~/docs/framework/migration-guide/versions-and-dependencies.md)  
