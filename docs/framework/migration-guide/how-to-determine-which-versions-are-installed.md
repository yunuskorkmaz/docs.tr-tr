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
ms.openlocfilehash: 3677ff7cc27847d56802206c793a574d61b1464c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33391644"
---
# <a name="how-to-determine-which-net-framework-versions-are-installed"></a><span data-ttu-id="08ded-102">Nasıl yapılır: hangi .NET Framework sürümlerinin yüklü olduğunu belirleme</span><span class="sxs-lookup"><span data-stu-id="08ded-102">How to: Determine which .NET Framework versions are installed</span></span>

<span data-ttu-id="08ded-103">Kullanıcılar, yükleyin ve bilgisayarlarında birden çok .NET Framework sürümünü çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="08ded-103">Users can install and run multiple versions of the .NET Framework on their computers.</span></span> <span data-ttu-id="08ded-104">Geliştirme ya da uygulamanızı dağıtma kullanıcının bilgisayarda hangi .NET Framework sürümlerinin yüklü olduğunu bilmeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="08ded-104">When you develop or deploy your app, you might need to know which .NET Framework versions are installed on the user’s computer.</span></span> <span data-ttu-id="08ded-105">.NET Framework sürümü tutulan ayrı ayrı olan iki ana bileşen içerdiğini unutmayın:</span><span class="sxs-lookup"><span data-stu-id="08ded-105">Note that the .NET Framework consists of two main components, which are versioned separately:</span></span>  
  
-   <span data-ttu-id="08ded-106">Koleksiyon türleri ve uygulamalarınız için işlevselliği sağlayan kaynakları derlemeleri kümesi.</span><span class="sxs-lookup"><span data-stu-id="08ded-106">A set of assemblies, which are collections of types and resources that provide the functionality for your apps.</span></span> <span data-ttu-id="08ded-107">.NET Framework ve derlemeleri aynı sürüm numarasına paylaşır.</span><span class="sxs-lookup"><span data-stu-id="08ded-107">The .NET Framework and assemblies share the same version number.</span></span>  
  
-   <span data-ttu-id="08ded-108">Yöneten ve uygulamanızın kodu yürütür ortak dil çalışma zamanı (CLR).</span><span class="sxs-lookup"><span data-stu-id="08ded-108">The common language runtime (CLR), which manages and executes your app's code.</span></span> <span data-ttu-id="08ded-109">CLR kendi sürüm numarasına göre tanımlanır (bkz [sürümleri ve bağımlılıkları](~/docs/framework/migration-guide/versions-and-dependencies.md)).</span><span class="sxs-lookup"><span data-stu-id="08ded-109">The CLR is identified by its own version number (see [Versions and Dependencies](~/docs/framework/migration-guide/versions-and-dependencies.md)).</span></span>  
  
 <span data-ttu-id="08ded-110">Bir bilgisayarda yüklü .NET Framework sürümleri doğru bir listesini almak için kayıt defterini görüntüleyebilir veya kod kayıt defterini sorgulayın:</span><span class="sxs-lookup"><span data-stu-id="08ded-110">To get an accurate list of the .NET Framework versions installed on a computer, you can view the registry or query the registry in code:</span></span>  
  
 [<span data-ttu-id="08ded-111">Kayıt defteri (sürümler 1-4) görüntüleme</span><span class="sxs-lookup"><span data-stu-id="08ded-111">Viewing the registry (versions 1-4)</span></span>](#net_a)  
 [<span data-ttu-id="08ded-112">Kayıt defteri (sürüm 4.5 ve üstü) görüntüleme</span><span class="sxs-lookup"><span data-stu-id="08ded-112">Viewing the registry (version 4.5 and later)</span></span>](#net_b)  
 [<span data-ttu-id="08ded-113">Kayıt defteri (sürümler 1-4) sorgulamak için kod kullanarak</span><span class="sxs-lookup"><span data-stu-id="08ded-113">Using code to query the registry (versions 1-4)</span></span>](#net_c)  
 [<span data-ttu-id="08ded-114">Kayıt defteri (sürüm 4.5 ve üstü) sorgulamak için kod kullanarak</span><span class="sxs-lookup"><span data-stu-id="08ded-114">Using code to query the registry (version 4.5 and later)</span></span>](#net_d)  
 [<span data-ttu-id="08ded-115">Kayıt defteri (sürüm 4.5 ve üstü) sorgulamak için PowerShell kullanma</span><span class="sxs-lookup"><span data-stu-id="08ded-115">Using PowerShell to query the registry (version 4.5 and later)</span></span>](#ps_a)  
  
 <span data-ttu-id="08ded-116">CLR sürümünü bulmak için bir araç veya kodu kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="08ded-116">To find the CLR version, you can use a tool or code:</span></span>  
  
 [<span data-ttu-id="08ded-117">Clrver Aracı'nı kullanma</span><span class="sxs-lookup"><span data-stu-id="08ded-117">Using the Clrver tool</span></span>](#clr_a)  
 [<span data-ttu-id="08ded-118">System.Environment sınıfı sorgulamak için kod kullanarak</span><span class="sxs-lookup"><span data-stu-id="08ded-118">Using code to query the System.Environment class</span></span>](#clr_b)  
  
 <span data-ttu-id="08ded-119">.NET Framework'ün her sürüm için yüklü güncelleştirmeler algılama hakkında daha fazla bilgi için bkz: [nasıl yapılır: belirlemek, .NET Framework güncelleştirmeler yüklenir](~/docs/framework/migration-guide/how-to-determine-which-net-framework-updates-are-installed.md).</span><span class="sxs-lookup"><span data-stu-id="08ded-119">For information about detecting the installed updates for each version of the .NET Framework, see [How to: Determine Which .NET Framework Updates Are Installed](~/docs/framework/migration-guide/how-to-determine-which-net-framework-updates-are-installed.md).</span></span> <span data-ttu-id="08ded-120">.NET Framework yükleme hakkında daha fazla bilgi için bkz: [geliştiriciler için .NET Framework'ü yüklemek](../../../docs/framework/install/guide-for-developers.md).</span><span class="sxs-lookup"><span data-stu-id="08ded-120">For information about installing the .NET Framework, see [Install the .NET Framework for developers](../../../docs/framework/install/guide-for-developers.md).</span></span>  
  
<a name="net_a"></a>   
## <a name="to-find-net-framework-versions-by-viewing-the-registry-net-framework-1-4"></a><span data-ttu-id="08ded-121">.NET Framework sürümleri (.NET Framework 1-4) kayıt defteri görüntüleyerek bulmak için</span><span class="sxs-lookup"><span data-stu-id="08ded-121">To find .NET Framework versions by viewing the registry (.NET Framework 1-4)</span></span>  
  
1.  <span data-ttu-id="08ded-122">Üzerinde **Başlat** menüsünde seçin **çalıştırmak**.</span><span class="sxs-lookup"><span data-stu-id="08ded-122">On the **Start** menu, choose **Run**.</span></span>  
  
2.  <span data-ttu-id="08ded-123">İçinde **açık** kutusuna **regedit.exe**.</span><span class="sxs-lookup"><span data-stu-id="08ded-123">In the **Open** box, enter **regedit.exe**.</span></span>  
  
     <span data-ttu-id="08ded-124">regedit.exe'yi çalıştırmak için yönetici kimlik bilgileriniz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="08ded-124">You must have administrative credentials to run regedit.exe.</span></span>  
  
3.  <span data-ttu-id="08ded-125">Kayıt Defteri Düzenleyicisi'nde, aşağıdaki alt anahtarı açın:</span><span class="sxs-lookup"><span data-stu-id="08ded-125">In the Registry Editor, open the following subkey:</span></span>  
  
     `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP`  
  
     <span data-ttu-id="08ded-126">Yüklenen sürümler NDP alt anahtarı altında listelenir.</span><span class="sxs-lookup"><span data-stu-id="08ded-126">The installed versions are listed under the NDP subkey.</span></span> <span data-ttu-id="08ded-127">Sürüm numarasını depolanan **sürüm** girişi.</span><span class="sxs-lookup"><span data-stu-id="08ded-127">The version number is stored in the **Version** entry.</span></span> <span data-ttu-id="08ded-128">İçin [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] **sürüm** giriştir istemci veya (altında NDP'nin), tam alt anahtarı altında veya her iki alt altında.</span><span class="sxs-lookup"><span data-stu-id="08ded-128">For the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] the **Version** entry is under the Client or Full subkey (under NDP), or under both subkeys.</span></span>  
  

    > [!NOTE]
    > <span data-ttu-id="08ded-129">Kayıt defterindeki "NET Framework Kurulum" klasörü, nokta karakteri ile başlamaz.</span><span class="sxs-lookup"><span data-stu-id="08ded-129">The "NET Framework Setup" folder in the registry does not begin with a period.</span></span>

<a name="net_b"></a> 
## <a name="to-find-net-framework-versions-by-viewing-the-registry-net-framework-45-and-later"></a><span data-ttu-id="08ded-130">.NET Framework sürümleri (.NET Framework 4.5 ve üzeri) kayıt defteri görüntüleyerek bulmak için</span><span class="sxs-lookup"><span data-stu-id="08ded-130">To find .NET Framework versions by viewing the registry (.NET Framework 4.5 and later)</span></span>

1. <span data-ttu-id="08ded-131">Üzerinde **Başlat** menüsünde seçin **çalıştırmak**.</span><span class="sxs-lookup"><span data-stu-id="08ded-131">On the **Start** menu, choose **Run**.</span></span>

2. <span data-ttu-id="08ded-132">İçinde **açık** kutusuna **regedit.exe**.</span><span class="sxs-lookup"><span data-stu-id="08ded-132">In the **Open** box, enter **regedit.exe**.</span></span>

     <span data-ttu-id="08ded-133">regedit.exe'yi çalıştırmak için yönetici kimlik bilgileriniz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="08ded-133">You must have administrative credentials to run regedit.exe.</span></span>

3. <span data-ttu-id="08ded-134">Kayıt Defteri Düzenleyicisi'nde, aşağıdaki alt anahtarı açın:</span><span class="sxs-lookup"><span data-stu-id="08ded-134">In the Registry Editor, open the following subkey:</span></span>

     `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full`

     <span data-ttu-id="08ded-135">Unutmayın yoluna `Full` alt anahtarını içeren alt `Net Framework` yerine `.NET Framework`.</span><span class="sxs-lookup"><span data-stu-id="08ded-135">Note that the path to the `Full` subkey includes the subkey `Net Framework` rather than `.NET Framework`.</span></span>

    > [!NOTE]
    > <span data-ttu-id="08ded-136">Varsa `Full` alt mevcut değil, ardından .NET Framework 4.5 yok veya sonraki bir sürümü yüklü.</span><span class="sxs-lookup"><span data-stu-id="08ded-136">If the `Full` subkey is not present, then you do not have the .NET Framework 4.5 or later installed.</span></span>

     <span data-ttu-id="08ded-137">Adlı bir DWORD değeri için denetleyin. `Release`.</span><span class="sxs-lookup"><span data-stu-id="08ded-137">Check for a DWORD value named `Release`.</span></span> <span data-ttu-id="08ded-138">Varlığını `Release` DWORD gösterir [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] ya da daha yeni bu bilgisayara yüklendi.</span><span class="sxs-lookup"><span data-stu-id="08ded-138">The existence of the `Release` DWORD indicates that the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] or newer has been installed on that computer.</span></span>

     <span data-ttu-id="08ded-139">![.NET Framework 4.5 için kayıt defteri girişi. ] (../../../docs/framework/migration-guide/media/clr-installdir.png "CLR_InstallDir")</span><span class="sxs-lookup"><span data-stu-id="08ded-139">![The registry entry for the .NET Framework 4.5.](../../../docs/framework/migration-guide/media/clr-installdir.png "CLR_InstallDir")</span></span>

     <span data-ttu-id="08ded-140">Değeri `Release` DWORD gösterir .NET Framework'ün hangi sürümünün yüklü.</span><span class="sxs-lookup"><span data-stu-id="08ded-140">The value of the `Release` DWORD indicates which version of the .NET Framework is installed.</span></span>

    [!INCLUDE[Release key values note](~/includes/version-keys-note.md)]

    |<span data-ttu-id="08ded-141">Yayın DWORD değeri</span><span class="sxs-lookup"><span data-stu-id="08ded-141">Value of the Release DWORD</span></span>|<span data-ttu-id="08ded-142">Sürüm</span><span class="sxs-lookup"><span data-stu-id="08ded-142">Version</span></span>|
    |--------------------------------|-------------|
    |<span data-ttu-id="08ded-143">378389</span><span class="sxs-lookup"><span data-stu-id="08ded-143">378389</span></span>|<span data-ttu-id="08ded-144">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="08ded-144">.NET Framework 4.5</span></span>|
    |<span data-ttu-id="08ded-145">378675</span><span class="sxs-lookup"><span data-stu-id="08ded-145">378675</span></span>|<span data-ttu-id="08ded-146">.NET framework 4.5.1 Windows 8.1 veya Windows Server 2012 R2 ile yüklenen</span><span class="sxs-lookup"><span data-stu-id="08ded-146">.NET Framework 4.5.1 installed with Windows 8.1 or Windows Server 2012 R2</span></span>|
    |<span data-ttu-id="08ded-147">378758</span><span class="sxs-lookup"><span data-stu-id="08ded-147">378758</span></span>|<span data-ttu-id="08ded-148">.NET framework 4.5.1 Windows 8, Windows 7 SP1 veya Windows Vista SP2 yüklü</span><span class="sxs-lookup"><span data-stu-id="08ded-148">.NET Framework 4.5.1 installed on Windows 8, Windows 7 SP1, or Windows Vista SP2</span></span>|
    |<span data-ttu-id="08ded-149">379893</span><span class="sxs-lookup"><span data-stu-id="08ded-149">379893</span></span>|<span data-ttu-id="08ded-150">.NET Framework 4.5.2</span><span class="sxs-lookup"><span data-stu-id="08ded-150">.NET Framework 4.5.2</span></span>|
    |<span data-ttu-id="08ded-151">Yalnızca Windows 10 sistemlerde: 393295</span><span class="sxs-lookup"><span data-stu-id="08ded-151">On Windows 10 systems only: 393295</span></span><br /><br /> <span data-ttu-id="08ded-152">Diğer tüm işletim sistemi sürümlerinde: 393297</span><span class="sxs-lookup"><span data-stu-id="08ded-152">On all other OS versions: 393297</span></span>|[!INCLUDE[net_v46](../../../includes/net-v46-md.md)]|
    |<span data-ttu-id="08ded-153">Yalnızca Windows 10 Kasım güncelleştirme sistemlerde: 394254</span><span class="sxs-lookup"><span data-stu-id="08ded-153">On Windows 10 November Update systems only: 394254</span></span><br /><br /> <span data-ttu-id="08ded-154">Diğer tüm işletim sistemi sürümlerinde: 394271</span><span class="sxs-lookup"><span data-stu-id="08ded-154">On all other OS versions: 394271</span></span>|[!INCLUDE[net_v461](../../../includes/net-v461-md.md)]|
    |<span data-ttu-id="08ded-155">Windows 10 Anniversary üzerinde güncelleştirme yalnızca: 394802</span><span class="sxs-lookup"><span data-stu-id="08ded-155">On Windows 10 Anniversary Update only: 394802</span></span><br /><br /> <span data-ttu-id="08ded-156">Diğer tüm işletim sistemi sürümlerinde: 394806</span><span class="sxs-lookup"><span data-stu-id="08ded-156">On all other OS versions: 394806</span></span>|[!INCLUDE[net_v462](../../../includes/net-v462-md.md)]| 
    |<span data-ttu-id="08ded-157">Windows 10 oluşturucuları üzerinde güncelleştirme yalnızca: 460798</span><span class="sxs-lookup"><span data-stu-id="08ded-157">On Windows 10 Creators Update only: 460798</span></span><br/><br/> <span data-ttu-id="08ded-158">Diğer tüm işletim sistemi sürümlerinde: 460805</span><span class="sxs-lookup"><span data-stu-id="08ded-158">On all other OS versions: 460805</span></span> | <span data-ttu-id="08ded-159">.NET framework 4.7</span><span class="sxs-lookup"><span data-stu-id="08ded-159">.NET Framework 4.7</span></span> |
    |<span data-ttu-id="08ded-160">Windows 10 sonbaharda oluşturucuları güncelleştirmesi yalnızca: 461308</span><span class="sxs-lookup"><span data-stu-id="08ded-160">On Windows 10 Fall Creators Update only: 461308</span></span><br/><br/> <span data-ttu-id="08ded-161">Diğer tüm işletim sistemi sürümlerinde: 461310</span><span class="sxs-lookup"><span data-stu-id="08ded-161">On all other OS versions: 461310</span></span> | <span data-ttu-id="08ded-162">.NET framework 4.7.1</span><span class="sxs-lookup"><span data-stu-id="08ded-162">.NET Framework 4.7.1</span></span> |
    |<span data-ttu-id="08ded-163">Yalnızca Windows 10 Nisan 2018 Update: 461808</span><span class="sxs-lookup"><span data-stu-id="08ded-163">On Windows 10 April 2018 Update only: 461808</span></span><br/><br/> <span data-ttu-id="08ded-164">Diğer tüm işletim sistemi sürümlerinde: 461814</span><span class="sxs-lookup"><span data-stu-id="08ded-164">On all other OS versions: 461814</span></span>| <span data-ttu-id="08ded-165">.NET framework 4.7.2</span><span class="sxs-lookup"><span data-stu-id="08ded-165">.NET Framework 4.7.2</span></span> |
    
<a name="net_c"></a> 
## <a name="to-find-net-framework-versions-by-querying-the-registry-in-code-net-framework-1-4"></a><span data-ttu-id="08ded-166">.NET Framework sürümleri kod (.NET Framework 1-4) kayıt defterinde sorgulayarak bulmak için</span><span class="sxs-lookup"><span data-stu-id="08ded-166">To find .NET Framework versions by querying the registry in code (.NET Framework 1-4)</span></span>

- <span data-ttu-id="08ded-167">Kullanım <xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType> Windows kayıt defterinde HKEY_LOCAL_MACHINE altında Software\Microsoft\NET Framework Setup\NDP\ alt erişmek için sınıf.</span><span class="sxs-lookup"><span data-stu-id="08ded-167">Use the <xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType> class to access the Software\Microsoft\NET Framework Setup\NDP\ subkey under HKEY_LOCAL_MACHINE in the Windows registry.</span></span>

     <span data-ttu-id="08ded-168">Aşağıdaki kod, bu sorgunun bir örneğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="08ded-168">The following code shows an example of this query.</span></span>

    > [!NOTE]
    > <span data-ttu-id="08ded-169">Bu kodu nasıl algılanacağını göstermez [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] veya sonraki bir sürümü.</span><span class="sxs-lookup"><span data-stu-id="08ded-169">This code does not show how to detect the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] or later.</span></span> <span data-ttu-id="08ded-170">Denetleme `Release` önceki bölümde açıklandığı gibi bu sürümler algılamaya DWORD.</span><span class="sxs-lookup"><span data-stu-id="08ded-170">Check the `Release` DWORD to detect those versions, as described in the previous section.</span></span> <span data-ttu-id="08ded-171">Algılamıyor kodu için [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] veya sonraki sürümleri, bu makalenin sonraki bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="08ded-171">For code that does detect the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] or later versions, see the next section in this article.</span></span>

     [!code-csharp[ListVersions](../../../samples/snippets/csharp/framework/migration-guide/versions-installed1.cs)]
     [!code-vb[ListVersions](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed1.vb)]

     <span data-ttu-id="08ded-172">Örnekte aşağıdakine benzer bir çıktı oluşturulur:</span><span class="sxs-lookup"><span data-stu-id="08ded-172">The example produces output that's similar to the following:</span></span>

    ```
    v2.0.50727  2.0.50727.4016  SP2
    v3.0  3.0.30729.4037  SP2
    v3.5  3.5.30729.01  SP1
    v4
      Client  4.0.30319
      Full  4.0.30319
    ```

<a name="net_d"></a> 
## <a name="to-find-net-framework-versions-by-querying-the-registry-in-code-net-framework-45-and-later"></a><span data-ttu-id="08ded-173">.NET Framework sürümleri kod (.NET Framework 4.5 ve üzeri) kayıt defterinde sorgulayarak bulmak için</span><span class="sxs-lookup"><span data-stu-id="08ded-173">To find .NET Framework versions by querying the registry in code (.NET Framework 4.5 and later)</span></span>

1. <span data-ttu-id="08ded-174">Varlığını `Release` DWORD .NET Framework 4.5 veya sonraki bir bilgisayarda yüklü olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="08ded-174">The existence of the `Release` DWORD indicates that the .NET Framework 4.5 or later has been installed on a computer.</span></span> <span data-ttu-id="08ded-175">Anahtar değeri yüklü olan sürümü gösterir.</span><span class="sxs-lookup"><span data-stu-id="08ded-175">The value of the keyword indicates the installed version.</span></span> <span data-ttu-id="08ded-176">Bu anahtar sözcük denetlemek için kullanın <xref:Microsoft.Win32.RegistryKey.OpenBaseKey%2A> ve <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A> yöntemlerinin <xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType> Windows kayıt defterinde HKEY_LOCAL_MACHINE altında Software\Microsoft\NET Framework Setup\NDP\v4\Full alt erişmek için sınıf.</span><span class="sxs-lookup"><span data-stu-id="08ded-176">To check this keyword, use the <xref:Microsoft.Win32.RegistryKey.OpenBaseKey%2A> and <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A> methods of the <xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType> class to access the Software\Microsoft\NET Framework Setup\NDP\v4\Full subkey under HKEY_LOCAL_MACHINE in the Windows registry.</span></span>

2. <span data-ttu-id="08ded-177">Değerini denetleyin `Release` yüklü olan sürümü belirlemek için anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="08ded-177">Check the value of the `Release` keyword to determine the installed version.</span></span> <span data-ttu-id="08ded-178">İleri uyumlu olması için tabloda listelenen değerleri eşit veya daha büyük bir değere denetleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="08ded-178">To be forward-compatible, you can check for a value greater than or equal to the values listed in the table.</span></span> <span data-ttu-id="08ded-179">.NET Framework sürümleri şunlardır ve ilişkili `Release` anahtar sözcükler.</span><span class="sxs-lookup"><span data-stu-id="08ded-179">Here are the .NET Framework versions and associated `Release` keywords.</span></span>

    [!INCLUDE[Release key values note](~/includes/version-keys-note.md)]

    |<span data-ttu-id="08ded-180">Sürüm</span><span class="sxs-lookup"><span data-stu-id="08ded-180">Version</span></span>|<span data-ttu-id="08ded-181">Yayın DWORD değeri</span><span class="sxs-lookup"><span data-stu-id="08ded-181">Value of the Release DWORD</span></span>|
    |-------------|--------------------------------|
    |<span data-ttu-id="08ded-182">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="08ded-182">.NET Framework 4.5</span></span>|<span data-ttu-id="08ded-183">378389</span><span class="sxs-lookup"><span data-stu-id="08ded-183">378389</span></span>|
    |<span data-ttu-id="08ded-184">.NET framework 4.5.1 Windows 8.1 ile yüklü</span><span class="sxs-lookup"><span data-stu-id="08ded-184">.NET Framework 4.5.1 installed with Windows 8.1</span></span>|<span data-ttu-id="08ded-185">378675</span><span class="sxs-lookup"><span data-stu-id="08ded-185">378675</span></span>|
    |<span data-ttu-id="08ded-186">.NET framework 4.5.1 Windows 8, Windows 7 SP1 veya Windows Vista SP2 yüklü</span><span class="sxs-lookup"><span data-stu-id="08ded-186">.NET Framework 4.5.1 installed on Windows 8, Windows 7 SP1, or Windows Vista SP2</span></span>|<span data-ttu-id="08ded-187">378758</span><span class="sxs-lookup"><span data-stu-id="08ded-187">378758</span></span>|
    |<span data-ttu-id="08ded-188">.NET Framework 4.5.2</span><span class="sxs-lookup"><span data-stu-id="08ded-188">.NET Framework 4.5.2</span></span>|<span data-ttu-id="08ded-189">379893</span><span class="sxs-lookup"><span data-stu-id="08ded-189">379893</span></span>|
    |<span data-ttu-id="08ded-190">Windows 10 ile yüklü .NET framework 4.6</span><span class="sxs-lookup"><span data-stu-id="08ded-190">.NET Framework 4.6 installed with Windows 10</span></span>|<span data-ttu-id="08ded-191">393295</span><span class="sxs-lookup"><span data-stu-id="08ded-191">393295</span></span>|
    |<span data-ttu-id="08ded-192">.NET framework 4.6 diğer tüm Windows işletim sistemi sürümlerinde yüklü</span><span class="sxs-lookup"><span data-stu-id="08ded-192">.NET Framework 4.6 installed on all other Windows OS versions</span></span>|<span data-ttu-id="08ded-193">393297</span><span class="sxs-lookup"><span data-stu-id="08ded-193">393297</span></span>|
    |<span data-ttu-id="08ded-194">.NET framework 4.6.1 üzerinde Windows 10 yüklü</span><span class="sxs-lookup"><span data-stu-id="08ded-194">.NET Framework 4.6.1 installed on Windows 10</span></span>|<span data-ttu-id="08ded-195">394254</span><span class="sxs-lookup"><span data-stu-id="08ded-195">394254</span></span>|
    |<span data-ttu-id="08ded-196">.NET framework 4.6.1 diğer tüm Windows işletim sistemi sürümlerinde yüklü</span><span class="sxs-lookup"><span data-stu-id="08ded-196">.NET Framework 4.6.1 installed on all other Windows OS versions</span></span>|<span data-ttu-id="08ded-197">394271</span><span class="sxs-lookup"><span data-stu-id="08ded-197">394271</span></span>|
    |<span data-ttu-id="08ded-198">.NET framework 4.6.2 Windows 10 Anniversary Update'te yüklü</span><span class="sxs-lookup"><span data-stu-id="08ded-198">.NET Framework 4.6.2 installed on Windows 10 Anniversary Update</span></span>|<span data-ttu-id="08ded-199">394802</span><span class="sxs-lookup"><span data-stu-id="08ded-199">394802</span></span>|
    |<span data-ttu-id="08ded-200">.NET framework 4.6.2 diğer tüm Windows işletim sistemi sürümlerinde yüklü</span><span class="sxs-lookup"><span data-stu-id="08ded-200">.NET Framework 4.6.2 installed on all other Windows OS versions</span></span>|<span data-ttu-id="08ded-201">394806</span><span class="sxs-lookup"><span data-stu-id="08ded-201">394806</span></span>|
    |<span data-ttu-id="08ded-202">.NET framework Windows 10 oluşturucuları Update'te yüklü 4.7</span><span class="sxs-lookup"><span data-stu-id="08ded-202">.NET Framework 4.7 installed on Windows 10 Creators Update</span></span>|<span data-ttu-id="08ded-203">460798</span><span class="sxs-lookup"><span data-stu-id="08ded-203">460798</span></span>|
    |<span data-ttu-id="08ded-204">.NET framework tüm diğer Windows işletim sistemi sürümleri yüklü 4.7</span><span class="sxs-lookup"><span data-stu-id="08ded-204">.NET Framework 4.7 installed on all other Windows OS versions</span></span>|<span data-ttu-id="08ded-205">460805</span><span class="sxs-lookup"><span data-stu-id="08ded-205">460805</span></span>|
    |<span data-ttu-id="08ded-206">.NET framework Windows 10 sonbaharda oluşturucuları Update'te yüklü 4.7.1</span><span class="sxs-lookup"><span data-stu-id="08ded-206">.NET Framework 4.7.1 installed on Windows 10 Fall Creators Update</span></span>|<span data-ttu-id="08ded-207">461308</span><span class="sxs-lookup"><span data-stu-id="08ded-207">461308</span></span>|
    |<span data-ttu-id="08ded-208">.NET framework tüm diğer Windows işletim sistemi sürümleri yüklü 4.7.1</span><span class="sxs-lookup"><span data-stu-id="08ded-208">.NET Framework 4.7.1 installed on all other Windows OS versions</span></span>|<span data-ttu-id="08ded-209">461310</span><span class="sxs-lookup"><span data-stu-id="08ded-209">461310</span></span>|
    |<span data-ttu-id="08ded-210">.NET framework Windows yüklenen 4.7.2 10 Nisan 2018 güncelleştir</span><span class="sxs-lookup"><span data-stu-id="08ded-210">.NET Framework 4.7.2 installed on Windows 10 April 2018 Update</span></span>|<span data-ttu-id="08ded-211">461808</span><span class="sxs-lookup"><span data-stu-id="08ded-211">461808</span></span>|
    |<span data-ttu-id="08ded-212">.NET framework tüm diğer Windows işletim sistemi sürümleri yüklü 4.7.2</span><span class="sxs-lookup"><span data-stu-id="08ded-212">.NET Framework 4.7.2 installed on all other Windows OS versions</span></span>|<span data-ttu-id="08ded-213">461814</span><span class="sxs-lookup"><span data-stu-id="08ded-213">461814</span></span>|
    
     <span data-ttu-id="08ded-214">Aşağıdaki örnek denetimleri `Release` belirlemek için kayıt defteri değerinde olup olmadığını [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] veya .NET Framework'ün daha yeni bir sürümü yüklü.</span><span class="sxs-lookup"><span data-stu-id="08ded-214">The following example checks the `Release` value in the registry to determine whether the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] or a later version of the .NET Framework is installed.</span></span>

     [!code-csharp[ListVersions#5](../../../samples/snippets/csharp/framework/migration-guide/versions-installed3.cs)]
     [!code-vb[ListVersions#5](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed3.vb)]

     <span data-ttu-id="08ded-215">Bu örnek, sürüm denetimi için önerilen yöntem aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="08ded-215">This example follows the recommended practice for version checking:</span></span>

    - <span data-ttu-id="08ded-216">Denetlediği olup olmadığını değerini `Release` girişi *değerinden büyük veya eşit* bilinen yayın anahtarlarının değerini.</span><span class="sxs-lookup"><span data-stu-id="08ded-216">It checks whether the value of the `Release` entry is *greater than or equal to* the value of the known release keys.</span></span>

    - <span data-ttu-id="08ded-217">Eski sürümü için en son sürümüne sırayla denetler.</span><span class="sxs-lookup"><span data-stu-id="08ded-217">It checks in order from most recent version to earliest version.</span></span>

<a name="ps_a"></a> 
## <a name="to-check-for-a-minimum-required-net-framework-version-by-querying-the-registry-in-powershell-net-framework-45-and-later"></a><span data-ttu-id="08ded-218">PowerShell (.NET Framework 4.5 ve üzeri) kayıt defterinde sorgulayarak için gereken en düşük .NET Framework sürümü denetlemek için</span><span class="sxs-lookup"><span data-stu-id="08ded-218">To check for a minimum-required .NET Framework version by querying the registry in PowerShell (.NET Framework 4.5 and later)</span></span>

- <span data-ttu-id="08ded-219">Aşağıdaki örnek değeri kontrol `Release` belirlemek için anahtar sözcüğü olup olmadığını .NET Framework 4.6.2 veya üstü yüklü, ne olursa olsun, Windows işletim sistemi sürümü (döndürme `True` etkinleştirilmişse ve `False` Aksi durumda).</span><span class="sxs-lookup"><span data-stu-id="08ded-219">The following example checks the value of the `Release` keyword to determine whether .NET Framework 4.6.2 or higher is installed, regardless of Windows OS version (returning `True` if it is and `False` otherwise).</span></span>

    ```PowerShell
    Get-ChildItem "HKLM:SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full\" | Get-ItemPropertyValue -Name Release | ForEach-Object { $_ -ge 394802 } 
    ```

    <span data-ttu-id="08ded-220">Değiştirebileceğiniz `394802` için farklı bir gereken en düşük .NET Framework sürüm denetlemek için aşağıdaki tabloda önceki örnekte başka bir değere sahip.</span><span class="sxs-lookup"><span data-stu-id="08ded-220">You can replace `394802` in the previous example with another value from the following table to check for a different minimum-required .NET Framework version.</span></span>
  
    |<span data-ttu-id="08ded-221">Sürüm</span><span class="sxs-lookup"><span data-stu-id="08ded-221">Version</span></span>|<span data-ttu-id="08ded-222">En düşük sürüm DWORD değeri</span><span class="sxs-lookup"><span data-stu-id="08ded-222">Minimum value of the Release DWORD</span></span>|
    |-------------|--------------------------------|
    |<span data-ttu-id="08ded-223">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="08ded-223">.NET Framework 4.5</span></span>|<span data-ttu-id="08ded-224">378389</span><span class="sxs-lookup"><span data-stu-id="08ded-224">378389</span></span>|
    |<span data-ttu-id="08ded-225">.NET Framework 4.5.1</span><span class="sxs-lookup"><span data-stu-id="08ded-225">.NET Framework 4.5.1</span></span>|<span data-ttu-id="08ded-226">378675</span><span class="sxs-lookup"><span data-stu-id="08ded-226">378675</span></span>|
    |<span data-ttu-id="08ded-227">.NET Framework 4.5.2</span><span class="sxs-lookup"><span data-stu-id="08ded-227">.NET Framework 4.5.2</span></span>|<span data-ttu-id="08ded-228">379893</span><span class="sxs-lookup"><span data-stu-id="08ded-228">379893</span></span>|
    |[!INCLUDE[net_v46](../../../includes/net-v46-md.md)]|<span data-ttu-id="08ded-229">393295</span><span class="sxs-lookup"><span data-stu-id="08ded-229">393295</span></span>|
    |[!INCLUDE[net_v461](../../../includes/net-v461-md.md)]|<span data-ttu-id="08ded-230">394254</span><span class="sxs-lookup"><span data-stu-id="08ded-230">394254</span></span>|
    |[!INCLUDE[net_v462](../../../includes/net-v462-md.md)]|<span data-ttu-id="08ded-231">394802</span><span class="sxs-lookup"><span data-stu-id="08ded-231">394802</span></span>|
    |<span data-ttu-id="08ded-232">.NET framework 4.7</span><span class="sxs-lookup"><span data-stu-id="08ded-232">.NET Framework 4.7</span></span>|<span data-ttu-id="08ded-233">460798</span><span class="sxs-lookup"><span data-stu-id="08ded-233">460798</span></span>|
    |<span data-ttu-id="08ded-234">.NET framework 4.7.1</span><span class="sxs-lookup"><span data-stu-id="08ded-234">.NET Framework 4.7.1</span></span>|<span data-ttu-id="08ded-235">461308</span><span class="sxs-lookup"><span data-stu-id="08ded-235">461308</span></span>|
    |<span data-ttu-id="08ded-236">.NET framework 4.7.2</span><span class="sxs-lookup"><span data-stu-id="08ded-236">.NET Framework 4.7.2</span></span>|<span data-ttu-id="08ded-237">461808</span><span class="sxs-lookup"><span data-stu-id="08ded-237">461808</span></span>|

<a name="clr_a"></a> 
## <a name="to-find-the-current-runtime-version-by-using-the-clrver-tool"></a><span data-ttu-id="08ded-238">Geçerli çalışma zamanı sürümü Clrver Aracı'nı kullanarak bulma</span><span class="sxs-lookup"><span data-stu-id="08ded-238">To find the current runtime version by using the Clrver tool</span></span>

- <span data-ttu-id="08ded-239">Bilgisayarda ortak dil çalışma zamanının hangi sürümlerinin yüklü olduğunu saptamak için CLR Sürüm Aracı'nı (Clrver.exe) kullanın.</span><span class="sxs-lookup"><span data-stu-id="08ded-239">Use the CLR Version Tool (Clrver.exe) to determine which versions of the common language runtime are installed on a computer.</span></span>

     <span data-ttu-id="08ded-240">Visual Studio komut isteminden, girin `clrver`.</span><span class="sxs-lookup"><span data-stu-id="08ded-240">From a Visual Studio Command Prompt, enter `clrver`.</span></span> <span data-ttu-id="08ded-241">Bu komut aşağıdakine benzer bir çıktı oluşturur:</span><span class="sxs-lookup"><span data-stu-id="08ded-241">This command produces output similar to the following:</span></span>

    ```
    Versions installed on the machine:
    v2.0.50727
    v4.0.30319
    ```

     <span data-ttu-id="08ded-242">Bu aracı kullanmayla ilgili daha fazla bilgi için bkz: [Clrver.exe (CLR sürüm aracı)](~/docs/framework/tools/clrver-exe-clr-version-tool.md).</span><span class="sxs-lookup"><span data-stu-id="08ded-242">For more information about using this tool, see [Clrver.exe (CLR Version Tool)](~/docs/framework/tools/clrver-exe-clr-version-tool.md).</span></span>

<a name="clr_b"></a> 
## <a name="to-find-the-current-runtime-version-by-querying-the-environment-class-in-code"></a><span data-ttu-id="08ded-243">Kod içinde Ortam sınıfını sorgulayarak geçerli çalışma zamanı sürümünü bulmak için</span><span class="sxs-lookup"><span data-stu-id="08ded-243">To find the current runtime version by querying the Environment class in code</span></span>

- <span data-ttu-id="08ded-244">Sorgu <xref:System.Environment.Version%2A?displayProperty=nameWithType> almak için özelliğini bir <xref:System.Version> kod şu anda yürütülmekte çalışma zamanı sürümü tanımlayan nesne.</span><span class="sxs-lookup"><span data-stu-id="08ded-244">Query the <xref:System.Environment.Version%2A?displayProperty=nameWithType> property to retrieve a <xref:System.Version> object that identifies the version of the runtime that is currently executing the code.</span></span> <span data-ttu-id="08ded-245">Kullanabileceğiniz <xref:System.Version.Major%2A?displayProperty=nameWithType> özelliği (örneğin, "4" sürüm 4.0 için), ana sürüm tanıtıcısını alın <xref:System.Version.Minor%2A?displayProperty=nameWithType> özelliği (örneğin, "0" sürüm 4.0 için), alt sürüm tanıtıcısını alın veya <xref:System.Object.ToString%2A?displayProperty=nameWithType> tüm sürümü almak için yöntemi dize ("aşağıdaki kodda gösterildiği gibi 4.0.30319.18010",).</span><span class="sxs-lookup"><span data-stu-id="08ded-245">You can use the <xref:System.Version.Major%2A?displayProperty=nameWithType> property to get the major release identifier (for example, "4" for version 4.0), the <xref:System.Version.Minor%2A?displayProperty=nameWithType> property to get the minor release identifier (for example, "0" for version 4.0), or the <xref:System.Object.ToString%2A?displayProperty=nameWithType> method to get the entire version string (for example, "4.0.30319.18010", as shown in the following code).</span></span> <span data-ttu-id="08ded-246">Bu özellik, kodu şu anda yürüten çalışma zamanı sürümünü gösteren tek bir değer döndürür; diğer sürümleri bilgisayarda yüklü çalışma zamanı derleme sürümleri döndürmez.</span><span class="sxs-lookup"><span data-stu-id="08ded-246">This property returns a single value that reflects the version of the runtime that is currently executing the code; it does not return assembly versions or other versions of the runtime that may have been installed on the computer.</span></span>

     <span data-ttu-id="08ded-247">.NET Framework sürüm 4, 4.5, 4.5.1 ve 4.5.2 <xref:System.Environment.Version%2A?displayProperty=nameWithType> özelliği döndürür bir <xref:System.Version> , dize gösterimi yok formun nesne `4.0.30319.xxxxx`.</span><span class="sxs-lookup"><span data-stu-id="08ded-247">For the .NET Framework Versions 4, 4.5, 4.5.1, and 4.5.2, the <xref:System.Environment.Version%2A?displayProperty=nameWithType> property returns a <xref:System.Version> object whose string representation has the form `4.0.30319.xxxxx`.</span></span> <span data-ttu-id="08ded-248">.NET Framework 4.6 ve daha sonra formun sahip `4.0.30319.42000`.</span><span class="sxs-lookup"><span data-stu-id="08ded-248">For the .NET Framework 4.6 and later, it has the form `4.0.30319.42000`.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="08ded-249">İçin [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] ve kullanarak daha sonra önermiyoruz <xref:System.Environment.Version%2A?displayProperty=nameWithType> çalışma zamanı sürümü algılamak için özellik.</span><span class="sxs-lookup"><span data-stu-id="08ded-249">For the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] and later, we do not recommend using the  <xref:System.Environment.Version%2A?displayProperty=nameWithType> property to detect the version of the runtime.</span></span> <span data-ttu-id="08ded-250">Bunun yerine, kayıt defterini sorgulayın açıklandığı şekilde öneririz [kod (.NET Framework 4.5 ve üzeri) kayıt defterinde sorgulayarak .NET Framework sürümlerini bulmak için](#net_d) bu makalenin önceki bölümünde.</span><span class="sxs-lookup"><span data-stu-id="08ded-250">Instead, we recommend that you query the registry, as described in the [To find .NET Framework versions by querying the registry in code (.NET Framework 4.5 and later)](#net_d) section earlier in this article.</span></span>

     <span data-ttu-id="08ded-251">Sorgulama örneği <xref:System.Environment.Version%2A?displayProperty=nameWithType> özelliği çalışma zamanı sürüm bilgileri için:</span><span class="sxs-lookup"><span data-stu-id="08ded-251">Here's an example of querying the <xref:System.Environment.Version%2A?displayProperty=nameWithType> property for runtime version information:</span></span>

     [!code-csharp[ListVersions](../../../samples/snippets/csharp/framework/migration-guide/versions-installed2.cs)]
     [!code-vb[ListVersions](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed2.vb)]

     <span data-ttu-id="08ded-252">Örnekte aşağıdakine benzer bir çıktı oluşturulur:</span><span class="sxs-lookup"><span data-stu-id="08ded-252">The example produces output that's similar to the following:</span></span>

    ```
    Version: 4.0.30319.18010
    ```

## <a name="see-also"></a><span data-ttu-id="08ded-253">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="08ded-253">See also</span></span>

[<span data-ttu-id="08ded-254">Nasıl yapılır: Hangi .NET Framework Güncelleştirmelerinin Yüklü Olduğunu Belirleme</span><span class="sxs-lookup"><span data-stu-id="08ded-254">How to: Determine Which .NET Framework Updates Are Installed</span></span>](~/docs/framework/migration-guide/how-to-determine-which-net-framework-updates-are-installed.md)  
[<span data-ttu-id="08ded-255">Geliştiriciler için .NET Framework'ü yükleme</span><span class="sxs-lookup"><span data-stu-id="08ded-255">Install the .NET Framework for developers</span></span>](../../../docs/framework/install/guide-for-developers.md)  
[<span data-ttu-id="08ded-256">Sürümler ve Bağımlılıklar</span><span class="sxs-lookup"><span data-stu-id="08ded-256">Versions and Dependencies</span></span>](~/docs/framework/migration-guide/versions-and-dependencies.md)  
