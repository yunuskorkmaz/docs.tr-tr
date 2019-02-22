---
title: 'Nasıl yapılır: Hangi .NET Framework sürümlerinin yüklü olduğunu belirleme'
ms.date: 02/20/2019
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
ms.openlocfilehash: d7661b3ebaa8f29d6d3b2adbc56c405c8f0945f3
ms.sourcegitcommit: 07c4368273b446555cb2c85397ea266b39d5fe50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56584180"
---
# <a name="how-to-determine-which-net-framework-versions-are-installed"></a><span data-ttu-id="a48ea-102">Nasıl yapılır: Hangi .NET Framework sürümlerinin yüklü olduğunu belirleme</span><span class="sxs-lookup"><span data-stu-id="a48ea-102">How to: Determine which .NET Framework versions are installed</span></span>

<span data-ttu-id="a48ea-103">Kullanıcılar yükleyebilir ve kendi bilgisayarlarına .NET Framework'ün birden çok sürümünü çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="a48ea-103">Users can install and run multiple versions of the .NET Framework on their computers.</span></span> <span data-ttu-id="a48ea-104">Geliştirme veya uygulamanızı dağıtma, hangi .NET Framework sürümlerinin kullanıcının bilgisayarında yüklü olduğunu bilmeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="a48ea-104">When you develop or deploy your app, you might need to know which .NET Framework versions are installed on the user’s computer.</span></span> <span data-ttu-id="a48ea-105">Not: .NET Framework, ayrı ayrı uyarlandı iki ana bileşenden, oluşur</span><span class="sxs-lookup"><span data-stu-id="a48ea-105">Note that the .NET Framework consists of two main components, which are versioned separately:</span></span>  
  
- <span data-ttu-id="a48ea-106">Koleksiyonları türlerin ve uygulamalarınız için işlevsellik sağlayan kaynaklar derlemelere kümesi.</span><span class="sxs-lookup"><span data-stu-id="a48ea-106">A set of assemblies, which are collections of types and resources that provide the functionality for your apps.</span></span> <span data-ttu-id="a48ea-107">.NET Framework ve derlemeleri, aynı sürüm numarasını paylaşır.</span><span class="sxs-lookup"><span data-stu-id="a48ea-107">The .NET Framework and assemblies share the same version number.</span></span>  
  
- <span data-ttu-id="a48ea-108">Yönetir ve uygulamanızın kod yürüten ortak dil çalışma zamanı (CLR).</span><span class="sxs-lookup"><span data-stu-id="a48ea-108">The common language runtime (CLR), which manages and executes your app's code.</span></span> <span data-ttu-id="a48ea-109">CLR kendi sürüm numarasıyla tanımlanır (bkz [sürümler ve bağımlılıklar](~/docs/framework/migration-guide/versions-and-dependencies.md)).</span><span class="sxs-lookup"><span data-stu-id="a48ea-109">The CLR is identified by its own version number (see [Versions and Dependencies](~/docs/framework/migration-guide/versions-and-dependencies.md)).</span></span>  
  
<span data-ttu-id="a48ea-110">Bir bilgisayarda yüklü .NET Framework sürümünü doğru bir listesini almak için kayıt defteri görüntüleyebilir veya kod içinde kayıt defterini sorgulayın:</span><span class="sxs-lookup"><span data-stu-id="a48ea-110">To get an accurate list of the .NET Framework versions installed on a computer, you can view the registry or query the registry in code:</span></span>  
  
 [<span data-ttu-id="a48ea-111">.NET Framework sürüm 1-4 kayıt defterinde bulunamadı.</span><span class="sxs-lookup"><span data-stu-id="a48ea-111">Find .NET Framework versions 1-4 in the registry</span></span>](#net_a)  
 [<span data-ttu-id="a48ea-112">.NET Framework sürüm 4.5 ve sonraki kayıt defterinde Bul)</span><span class="sxs-lookup"><span data-stu-id="a48ea-112">Find .NET Framework versions 4.5 and later in the registry)</span></span>](#net_b)  
 [<span data-ttu-id="a48ea-113">Kayıt defteri (sürüm 1-4) sorgulamak için kod kullanma</span><span class="sxs-lookup"><span data-stu-id="a48ea-113">Using code to query the registry (versions 1-4)</span></span>](#net_c)  
 [<span data-ttu-id="a48ea-114">Kayıt defteri (sürüm 4.5 ve üstü) sorgulamak için kod kullanma</span><span class="sxs-lookup"><span data-stu-id="a48ea-114">Using code to query the registry (version 4.5 and later)</span></span>](#net_d)  
 [<span data-ttu-id="a48ea-115">Kayıt defteri (sürüm 4.5 ve üstü) sorgulamak için PowerShell'i kullanma</span><span class="sxs-lookup"><span data-stu-id="a48ea-115">Using PowerShell to query the registry (version 4.5 and later)</span></span>](#ps_a)  

 <span data-ttu-id="a48ea-116">CLR sürümü bulmak için bir aracı veya kodu kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="a48ea-116">To find the CLR version, you can use a tool or code:</span></span>  
  
 [<span data-ttu-id="a48ea-117">Clrver Aracı'nı kullanma</span><span class="sxs-lookup"><span data-stu-id="a48ea-117">Using the Clrver tool</span></span>](#clr_a)  
 [<span data-ttu-id="a48ea-118">System.Environment sınıfı sorgulamak için kod kullanma</span><span class="sxs-lookup"><span data-stu-id="a48ea-118">Using code to query the System.Environment class</span></span>](#clr_b)  

> [!NOTE]
> <span data-ttu-id="a48ea-119">.NET Framework sürümünü ve ortak dil çalışma zamanı (CLR) sürümünü arasında bir fark yoktur.</span><span class="sxs-lookup"><span data-stu-id="a48ea-119">There is a difference between the .NET Framework version and the common language runtime (CLR) version.</span></span> <span data-ttu-id="a48ea-120">.NET Framework sınıf kitaplığı oluşturan derlemeleri kümesine göre .NET Framework sürümü.</span><span class="sxs-lookup"><span data-stu-id="a48ea-120">The .NET Framework is versioned based on the set of assemblies that form the .NET Framework Class Library.</span></span> <span data-ttu-id="a48ea-121">Örneğin, .NET Framework sürüm 4.5, 4.6.1 ve 4.7.2 içerir.</span><span class="sxs-lookup"><span data-stu-id="a48ea-121">For example, .NET Framework versions include 4.5, 4.6.1, and 4.7.2.</span></span> <span data-ttu-id="a48ea-122">.NET Framework uygulamalarını yürütmek çalışma zamanına göre CLR sürümü tutulan ve tek bir CLR sürümü genellikle birden çok .NET Framework sürümlerini destekler.</span><span class="sxs-lookup"><span data-stu-id="a48ea-122">The CLR is versioned based on the runtime on which .NET Framework applications execute, and a single CLR version typically supports multiple .NET Framework versions.</span></span> <span data-ttu-id="a48ea-123">CLR sürümü 4.30319. *xxxxx* .NET Framework sürüm 4.5.2; aracılığıyla 4 destekler CLR sürümü 4.30319.42000 .NET Framework 4. 6'ile başlayan .NET Framework sürümlerini destekler.</span><span class="sxs-lookup"><span data-stu-id="a48ea-123">CLR version 4.30319.*xxxxx* supports .NET Framework versions 4 through 4.5.2; CLR version 4.30319.42000 supports .NET Framework versions starting with .NET Framework 4.6.</span></span> <span data-ttu-id="a48ea-124">Daha fazla bilgi için <xref:System.Environment.Version?displayProperty=nameWithType> özelliği.</span><span class="sxs-lookup"><span data-stu-id="a48ea-124">For more information, see the <xref:System.Environment.Version?displayProperty=nameWithType> property.</span></span>

 <span data-ttu-id="a48ea-125">.NET Framework'ün her sürümü için yüklü güncelleştirmeleri algılama hakkında daha fazla bilgi için bkz: [nasıl yapılır: Hangi .NET Framework güncelleştirmelerinin yüklü olduğunu belirleme](~/docs/framework/migration-guide/how-to-determine-which-net-framework-updates-are-installed.md).</span><span class="sxs-lookup"><span data-stu-id="a48ea-125">For information about detecting the installed updates for each version of the .NET Framework, see [How to: Determine Which .NET Framework Updates Are Installed](~/docs/framework/migration-guide/how-to-determine-which-net-framework-updates-are-installed.md).</span></span> <span data-ttu-id="a48ea-126">.NET Framework'ü yükleme hakkında daha fazla bilgi için bkz: [geliştiriciler için .NET Framework yükleme](../../../docs/framework/install/guide-for-developers.md).</span><span class="sxs-lookup"><span data-stu-id="a48ea-126">For information about installing the .NET Framework, see [Install the .NET Framework for developers](../../../docs/framework/install/guide-for-developers.md).</span></span>  
  
<a name="net_a"></a>   
## <a name="find-net-framework-versions-1-4-in-the-registry"></a><span data-ttu-id="a48ea-127">.NET Framework sürüm 1-4 kayıt defterinde bulunamadı.</span><span class="sxs-lookup"><span data-stu-id="a48ea-127">Find .NET Framework versions 1-4 in the registry</span></span> 
  
1.  <span data-ttu-id="a48ea-128">Üzerinde **Başlat** menüsünde seçin **çalıştırma**.</span><span class="sxs-lookup"><span data-stu-id="a48ea-128">On the **Start** menu, choose **Run**.</span></span>  
  
2.  <span data-ttu-id="a48ea-129">İçinde **açık** kutusuna **regedit.exe**.</span><span class="sxs-lookup"><span data-stu-id="a48ea-129">In the **Open** box, enter **regedit.exe**.</span></span>  
  
     <span data-ttu-id="a48ea-130">regedit.exe'yi çalıştırmak için yönetici kimlik bilgileriniz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a48ea-130">You must have administrative credentials to run regedit.exe.</span></span>  
  
3.  <span data-ttu-id="a48ea-131">Kayıt Defteri Düzenleyicisi'nde, aşağıdaki alt anahtarı açın:</span><span class="sxs-lookup"><span data-stu-id="a48ea-131">In the Registry Editor, open the following subkey:</span></span>  
  
     `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP`  
  
     <span data-ttu-id="a48ea-132">.NET Framework sürüm 1.1-3.5 yüklü sürümlerini anahtarlarında olarak listelenen `NDP` alt.</span><span class="sxs-lookup"><span data-stu-id="a48ea-132">For .NET Framework versions 1.1 through 3.5, the installed versions are listed as subkeys under the `NDP` subkey.</span></span> <span data-ttu-id="a48ea-133">Sürüm numarası sürüm alt anahtarında 's depolanan **sürüm** girişi.</span><span class="sxs-lookup"><span data-stu-id="a48ea-133">The version number is stored in the version subkey's **Version** entry.</span></span> 
     
     <span data-ttu-id="a48ea-134">.NET Framework 4 için **sürüm** girdidir altında `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4.0\Client` alt anahtarı `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4.0\Full` alt anahtar, veya her iki alt altında.</span><span class="sxs-lookup"><span data-stu-id="a48ea-134">For .NET Framework 4, the **Version** entry is under the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4.0\Client` subkey, the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4.0\Full` subkey, or under both subkeys.</span></span>

    > [!NOTE]
    > <span data-ttu-id="a48ea-135">Kayıt defterindeki "NET Framework Kurulum" klasörü, nokta karakteri ile başlamaz.</span><span class="sxs-lookup"><span data-stu-id="a48ea-135">The "NET Framework Setup" folder in the registry does not begin with a period.</span></span>

    <span data-ttu-id="a48ea-136">Aşağıdaki şekilde ile birlikte .NET Framework 3.5 için alt gösterir, **sürüm** girişi.</span><span class="sxs-lookup"><span data-stu-id="a48ea-136">The following figure shows that the subkey for the .NET Framework 3.5 along with its **Version** entry.</span></span>

     <span data-ttu-id="a48ea-137">![.NET Framework 3.5 için kayıt defteri girişi. ](../../../docs/framework/migration-guide/media/net-4-and-earlier.png ".NET framework 4 ve önceki sürümleri")</span><span class="sxs-lookup"><span data-stu-id="a48ea-137">![The registry entry for the .NET Framework 3.5.](../../../docs/framework/migration-guide/media/net-4-and-earlier.png ".NET Framework 4 and earlier versions")</span></span>

<a name="net_b"></a> 
## <a name="find-net-framework-versions-45-and-later-in-the-registry"></a><span data-ttu-id="a48ea-138">.NET Framework sürüm 4.5 ve sonraki kayıt defterinde bulun</span><span class="sxs-lookup"><span data-stu-id="a48ea-138">Find .NET Framework versions 4.5 and later in the registry</span></span>

1. <span data-ttu-id="a48ea-139">Üzerinde **Başlat** menüsünde seçin **çalıştırma**.</span><span class="sxs-lookup"><span data-stu-id="a48ea-139">On the **Start** menu, choose **Run**.</span></span>

2. <span data-ttu-id="a48ea-140">İçinde **açık** kutusuna **regedit.exe**.</span><span class="sxs-lookup"><span data-stu-id="a48ea-140">In the **Open** box, enter **regedit.exe**.</span></span>

     <span data-ttu-id="a48ea-141">regedit.exe'yi çalıştırmak için yönetici kimlik bilgileriniz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a48ea-141">You must have administrative credentials to run regedit.exe.</span></span>

3. <span data-ttu-id="a48ea-142">Kayıt Defteri Düzenleyicisi'nde, aşağıdaki alt anahtarı açın:</span><span class="sxs-lookup"><span data-stu-id="a48ea-142">In the Registry Editor, open the following subkey:</span></span>

     `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full`

     <span data-ttu-id="a48ea-143">Unutmayın yoluna `Full` alt anahtar alt anahtar içerir `Net Framework` yerine `.NET Framework`.</span><span class="sxs-lookup"><span data-stu-id="a48ea-143">Note that the path to the `Full` subkey includes the subkey `Net Framework` rather than `.NET Framework`.</span></span>

    > [!NOTE]
    > <span data-ttu-id="a48ea-144">Varsa `Full` alt mevcut değil, ardından .NET Framework 4.5 yok veya sonraki bir sürümü yüklü.</span><span class="sxs-lookup"><span data-stu-id="a48ea-144">If the `Full` subkey is not present, then you do not have the .NET Framework 4.5 or later installed.</span></span>

     <span data-ttu-id="a48ea-145">Adlı bir DWORD değerini denetleyin `Release`.</span><span class="sxs-lookup"><span data-stu-id="a48ea-145">Check for a DWORD value named `Release`.</span></span> <span data-ttu-id="a48ea-146">Varlığını `Release` DWORD .NET Framework 4.5 veya sonrası o bilgisayarda yüklü olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="a48ea-146">The existence of the `Release` DWORD indicates that .NET Framework 4.5 or later has been installed on that computer.</span></span> <span data-ttu-id="a48ea-147">Değerini belirli bir .NET Framework sürümü için karşılık gelen bir yayın anahtardır.</span><span class="sxs-lookup"><span data-stu-id="a48ea-147">Its value is a release key that corresponds to a particular version of .NET Framework.</span></span> <span data-ttu-id="a48ea-148">Aşağıdaki şekilde, örneğin değerini `Release` DWORD 378389, .NET Framework 4.5 için yayın anahtar olduğu değeridir.</span><span class="sxs-lookup"><span data-stu-id="a48ea-148">In the following figure, for example, the value of the `Release` DWORD is 378389, which is the release key for .NET Framework 4.5.</span></span> 

     <span data-ttu-id="a48ea-149">![.NET Framework 4.5 için kayıt defteri girişi. ](../../../docs/framework/migration-guide/media/clr-installdir.png "CLR_InstallDir")</span><span class="sxs-lookup"><span data-stu-id="a48ea-149">![The registry entry for the .NET Framework 4.5.](../../../docs/framework/migration-guide/media/clr-installdir.png "CLR_InstallDir")</span></span>

<span data-ttu-id="a48ea-150">Aşağıdaki tabloda en küçük değerini `Release` DWORD her .NET Framework sürümü için.</span><span class="sxs-lookup"><span data-stu-id="a48ea-150">The following table lists the minimum value of the `Release` DWORD for each .NET Framework version.</span></span> <span data-ttu-id="a48ea-151">Bu değerleri şu şekilde kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="a48ea-151">You can use these values as follows:</span></span>

- <span data-ttu-id="a48ea-152">Bir en düşük .NET Framework sürümü mevcut olup olmadığını belirlemek için test olmadığını `Release` DWORD değeri kayıt defterinde bulundu *büyüktür veya eşittir* değeri tabloda listelenen.</span><span class="sxs-lookup"><span data-stu-id="a48ea-152">To determine whether a minimum .NET Framework version is present, test whether the `Release` DWORD value found in the registry is *greater than or equal to* the value listed in the table.</span></span> <span data-ttu-id="a48ea-153">Örneğin, uygulamanızın gerektirdiği .NET Framework 4.7 ya da daha sonra en düşük sürüm anahtar değeri 460798 için test edersiniz.</span><span class="sxs-lookup"><span data-stu-id="a48ea-153">For example, if your application requires .NET Framework 4.7 or later, you would test for a minimum release key value of 460798.</span></span>

- <span data-ttu-id="a48ea-154">Birden çok sürümü için test etmek için en son .NET Framework sürümü ile başlayın ve ardından her art arda gelen önceki sürümü için test.</span><span class="sxs-lookup"><span data-stu-id="a48ea-154">To test for multiple versions, begin with the latest .NET Framework version, and then test for each successive earlier version.</span></span>

[!INCLUDE[Release key values note](~/includes/version-keys-note.md)]

|<span data-ttu-id="a48ea-155">.NET Framework Sürümü</span><span class="sxs-lookup"><span data-stu-id="a48ea-155">.NET Framework Version</span></span>|<span data-ttu-id="a48ea-156">Yayın DWORD değeri</span><span class="sxs-lookup"><span data-stu-id="a48ea-156">Value of the Release DWORD</span></span>|
|--------------------------------|-------------|
|<span data-ttu-id="a48ea-157">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="a48ea-157">.NET Framework 4.5</span></span>|<span data-ttu-id="a48ea-158">378389</span><span class="sxs-lookup"><span data-stu-id="a48ea-158">378389</span></span>|
|<span data-ttu-id="a48ea-159">.NET Framework 4.5.1</span><span class="sxs-lookup"><span data-stu-id="a48ea-159">.NET Framework 4.5.1</span></span>|<span data-ttu-id="a48ea-160">378675</span><span class="sxs-lookup"><span data-stu-id="a48ea-160">378675</span></span>|
|<span data-ttu-id="a48ea-161">.NET Framework 4.5.2</span><span class="sxs-lookup"><span data-stu-id="a48ea-161">.NET Framework 4.5.2</span></span>|<span data-ttu-id="a48ea-162">379893</span><span class="sxs-lookup"><span data-stu-id="a48ea-162">379893</span></span>|
|<span data-ttu-id="a48ea-163">.NET Framework 4.6</span><span class="sxs-lookup"><span data-stu-id="a48ea-163">.NET Framework 4.6</span></span>|<span data-ttu-id="a48ea-164">393295</span><span class="sxs-lookup"><span data-stu-id="a48ea-164">393295</span></span>|
|<span data-ttu-id="a48ea-165">.NET Framework 4.6.1</span><span class="sxs-lookup"><span data-stu-id="a48ea-165">.NET Framework 4.6.1</span></span>|<span data-ttu-id="a48ea-166">394254</span><span class="sxs-lookup"><span data-stu-id="a48ea-166">394254</span></span>|
|<span data-ttu-id="a48ea-167">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="a48ea-167">.NET Framework 4.6.2</span></span>|<span data-ttu-id="a48ea-168">394802</span><span class="sxs-lookup"><span data-stu-id="a48ea-168">394802</span></span>|
|<span data-ttu-id="a48ea-169">.NET framework 4.7</span><span class="sxs-lookup"><span data-stu-id="a48ea-169">.NET Framework 4.7</span></span>|<span data-ttu-id="a48ea-170">460798</span><span class="sxs-lookup"><span data-stu-id="a48ea-170">460798</span></span>|
|<span data-ttu-id="a48ea-171">.NET framework 4.7.1</span><span class="sxs-lookup"><span data-stu-id="a48ea-171">.NET Framework 4.7.1</span></span>|<span data-ttu-id="a48ea-172">461308</span><span class="sxs-lookup"><span data-stu-id="a48ea-172">461308</span></span>|
|<span data-ttu-id="a48ea-173">.NET Framework 4.7.2</span><span class="sxs-lookup"><span data-stu-id="a48ea-173">.NET Framework 4.7.2</span></span>|<span data-ttu-id="a48ea-174">461808</span><span class="sxs-lookup"><span data-stu-id="a48ea-174">461808</span></span>|

<span data-ttu-id="a48ea-175">.NET Framework belirli Windows işletim sistemi sürümleri için yayın anahtar tam bir tablo için bkz. [.NET Framework sürüm anahtarları ve Windows işletim sistemi sürümleri](release-keys-and-os-versions.md).</span><span class="sxs-lookup"><span data-stu-id="a48ea-175">For a complete table of release keys for the .NET Framework for specific Windows operating system versions, see [.NET Framework release keys and Windows operating system versions](release-keys-and-os-versions.md).</span></span>

<a name="net_c"></a> 
## <a name="find-net-framework-versions-1-4-with-code"></a><span data-ttu-id="a48ea-176">.NET Framework sürüm 1-4 ile kod bulma</span><span class="sxs-lookup"><span data-stu-id="a48ea-176">Find .NET Framework versions 1-4 with code</span></span>

- <span data-ttu-id="a48ea-177">Kullanım <xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType> sınıfı erişimi `Software\Microsoft\NET Framework Setup\NDP\` alt anahtarı altında `HKEY_LOCAL_MACHINE` Windows kayıt defterinde dal.</span><span class="sxs-lookup"><span data-stu-id="a48ea-177">Use the <xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType> class to access the `Software\Microsoft\NET Framework Setup\NDP\` subkey under `HKEY_LOCAL_MACHINE` branch in the Windows registry.</span></span>

     <span data-ttu-id="a48ea-178">Aşağıdaki kod, bu sorgunun bir örneğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="a48ea-178">The following code shows an example of this query.</span></span>

    > [!NOTE]
    > <span data-ttu-id="a48ea-179">Bu kod, .NET Framework 4.5 veya üzeri algılamak nasıl algılanacağını göstermez.</span><span class="sxs-lookup"><span data-stu-id="a48ea-179">This code does not show how to detect .NET Framework 4.5 or later.</span></span> <span data-ttu-id="a48ea-180">Denetleme `Release` önceki bölümde açıklandığı gibi bu sürümleri algılamak için DWORD.</span><span class="sxs-lookup"><span data-stu-id="a48ea-180">Check the `Release` DWORD to detect those versions, as described in the previous section.</span></span> <span data-ttu-id="a48ea-181">.NET Framework 4.5 veya sonraki sürümler algılayan kod için bu makalenin sonraki bölüme bakın.</span><span class="sxs-lookup"><span data-stu-id="a48ea-181">For code that detects .NET Framework 4.5 or later versions, see the next section in this article.</span></span>

     [!code-csharp[ListVersions](../../../samples/snippets/csharp/framework/migration-guide/versions-installed1.cs)]
     [!code-vb[ListVersions](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed1.vb)]

<a name="net_d"></a> 
## <a name="find-net-framework-versions-45-and-later-with-code"></a><span data-ttu-id="a48ea-182">.NET Framework sürüm 4.5 ve sonraki kodu bulun</span><span class="sxs-lookup"><span data-stu-id="a48ea-182">Find .NET Framework versions 4.5 and later with code</span></span>

1. <span data-ttu-id="a48ea-183">Varlığını `Release` DWORD `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` anahtar, .NET Framework 4.5 veya sonraki bir bilgisayara yüklendiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="a48ea-183">The existence of the `Release` DWORD in the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` key indicates that the .NET Framework 4.5 or later is installed on a computer.</span></span> <span data-ttu-id="a48ea-184">Anahtar sözcüğü değerini yüklü olan sürümü gösterir.</span><span class="sxs-lookup"><span data-stu-id="a48ea-184">The value of the keyword indicates the installed version.</span></span> <span data-ttu-id="a48ea-185">Bu anahtar sözcük denetlemek için kullanmak <xref:Microsoft.Win32.RegistryKey.OpenBaseKey%2A?displayProperty=nameWithType> ve <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A?displayProperty=nameWithType> Windows kayıt defteri alt anahtarına erişmek için yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="a48ea-185">To check this keyword, use the <xref:Microsoft.Win32.RegistryKey.OpenBaseKey%2A?displayProperty=nameWithType> and <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A?displayProperty=nameWithType> methods to access the subkey in the Windows registry.</span></span>

2. <span data-ttu-id="a48ea-186">Değerini kontrol edin `Release` yüklenen sürümü belirlemek için anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="a48ea-186">Check the value of the `Release` keyword to determine the installed version.</span></span> <span data-ttu-id="a48ea-187">İleri uyumlu olması için tabloda listelenen değerine eşit veya büyük bir değer denetleyebilirsiniz [kayıt defteri bulma .NET Framework sürüm 4.5 ve sonrası](#net_b) bölümü.</span><span class="sxs-lookup"><span data-stu-id="a48ea-187">To be forward-compatible, you can check for a value greater than or equal to the value listed in the table in the [Find .NET Framework versions 4.5 and later in the registry](#net_b) section.</span></span>

<span data-ttu-id="a48ea-188">Aşağıdaki örnek denetimlerini `Release` .NET Framework 4.5 veya sonraki bir sürümü yüklü olup olmadığını belirlemek için kayıt defteri değeri.</span><span class="sxs-lookup"><span data-stu-id="a48ea-188">The following example checks the `Release` value in the registry to determine whether .NET Framework 4.5 or a later version is installed.</span></span>

[!code-csharp[ListVersions#5](../../../samples/snippets/csharp/framework/migration-guide/versions-installed3.cs)]
[!code-vb[ListVersions#5](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed3.vb)]

<span data-ttu-id="a48ea-189">Bu örnek, sürüm denetimi için önerilen yöntem aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="a48ea-189">This example follows the recommended practice for version checking:</span></span>

- <span data-ttu-id="a48ea-190">Denetlediği olup olmadığını değerini `Release` giriş *büyüktür veya eşittir* bilinen yayın anahtarları değeri.</span><span class="sxs-lookup"><span data-stu-id="a48ea-190">It checks whether the value of the `Release` entry is *greater than or equal to* the value of the known release keys.</span></span>

- <span data-ttu-id="a48ea-191">Eski sürümü için en son sürüm sırayla denetler.</span><span class="sxs-lookup"><span data-stu-id="a48ea-191">It checks in order from most recent version to earliest version.</span></span>

<a name="ps_a"></a> 
## <a name="check-for-a-minimum-required-net-framework-version-45-and-later-with-powershell"></a><span data-ttu-id="a48ea-192">Bir en düşük gerekli .NET Framework sürüm (4.5 ve üzeri) PowerShell ile denetle</span><span class="sxs-lookup"><span data-stu-id="a48ea-192">Check for a minimum required .NET Framework version (4.5 and later) with PowerShell</span></span>

<span data-ttu-id="a48ea-193">Aşağıdaki örnek değerini denetler `Release` belirlemek için anahtar sözcüğü olup olmadığını .NET Framework 4.6.2 veya üzeri yüklü (döndüren `True` etkinleştirilmişse ve `False` yoksa).</span><span class="sxs-lookup"><span data-stu-id="a48ea-193">The following example checks the value of the `Release` keyword to determine whether .NET Framework 4.6.2 or higher is installed (returning `True` if it is and `False` otherwise).</span></span>

    ```PowerShell
    # PowerShell 5
    Get-ChildItem 'HKLM:\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full\' | Get-ItemPropertyValue -Name Release | Foreach-Object { $_ -ge 394802 } 
    ```

    ```PowerShell
    # PowerShell 4
    (Get-ItemProperty "HKLM:SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full").Release -gt 394802
    ```

    You can replace `394802` in the previous example with another value from the following table in the [Find .NET Framework versions 4.5 and later in the registry](#net_b) section to check for a different minimum required .NET Framework version.
  
<a name="clr_a"></a> 
## <a name="find-the-current-clr-version-with-clrverexe"></a><span data-ttu-id="a48ea-194">Clrver.exe geçerli CLR sürümüyle Bul</span><span class="sxs-lookup"><span data-stu-id="a48ea-194">Find the current CLR version with Clrver.exe</span></span>

<span data-ttu-id="a48ea-195">Bilgisayarda ortak dil çalışma zamanının hangi sürümlerinin yüklü olduğunu saptamak için CLR Sürüm Aracı'nı (Clrver.exe) kullanın.</span><span class="sxs-lookup"><span data-stu-id="a48ea-195">Use the CLR Version Tool (Clrver.exe) to determine which versions of the common language runtime are installed on a computer.</span></span>

<span data-ttu-id="a48ea-196">Visual Studio için geliştirici komut isteminden, girin `clrver`.</span><span class="sxs-lookup"><span data-stu-id="a48ea-196">From a Developer Command Prompt for Visual Studio, enter `clrver`.</span></span> <span data-ttu-id="a48ea-197">Bu komut aşağıdakine benzer bir çıktı oluşturur:</span><span class="sxs-lookup"><span data-stu-id="a48ea-197">This command produces output similar to the following:</span></span>

```console
Versions installed on the machine:
v2.0.50727
v4.0.30319
```

<span data-ttu-id="a48ea-198">Bu aracı kullanma hakkında daha fazla bilgi için bkz. [Clrver.exe (CLR sürüm aracı)](~/docs/framework/tools/clrver-exe-clr-version-tool.md).</span><span class="sxs-lookup"><span data-stu-id="a48ea-198">For more information about using this tool, see [Clrver.exe (CLR Version Tool)](~/docs/framework/tools/clrver-exe-clr-version-tool.md).</span></span>

<a name="clr_b"></a> 
## <a name="find-the-current-clr-version-with-the-environment-class"></a><span data-ttu-id="a48ea-199">Geçerli ortam sınıfını CLR sürümüyle Bul</span><span class="sxs-lookup"><span data-stu-id="a48ea-199">Find the current CLR version with the Environment class</span></span>

<span data-ttu-id="a48ea-200">Değerini alabilir <xref:System.Environment.Version?displayProperty=nameWithType> almak için özellik bir <xref:System.Version> şu anda kodu yürüten çalışma zamanının sürümünü tanımlayan nesne.</span><span class="sxs-lookup"><span data-stu-id="a48ea-200">You can retrieve the value of the <xref:System.Environment.Version?displayProperty=nameWithType> property to retrieve a <xref:System.Version> object that identifies the version of the runtime that is currently executing the code.</span></span> <span data-ttu-id="a48ea-201">Bu özellik şu anda kodu yürüten çalışma zamanının sürümünü gösteren tek bir değer döndürür; derleme sürümlerini ya da diğer sürümleri bilgisayarda yüklü çalışma zamanı döndürmez. Kullanabileceğiniz <xref:System.Version.Major%2A?displayProperty=nameWithType> (örneğin, "4" sürüm 4.0 için), ana sürüm tanıtıcısını almak için özellik <xref:System.Version.Minor%2A?displayProperty=nameWithType> (örneğin, "0" sürüm 4.0 için), alt sürüm tanıtıcısını almak için özellik veya <xref:System.Version.ToString%2A?displayProperty=nameWithType> tüm sürümü almak için yöntemi dize ("aşağıdaki kodda gösterildiği gibi 4.0.30319.18010").</span><span class="sxs-lookup"><span data-stu-id="a48ea-201">This property returns a single value that reflects the version of the runtime that is currently executing the code; it does not return assembly versions or other versions of the runtime that may have been installed on the computer.You can use the <xref:System.Version.Major%2A?displayProperty=nameWithType> property to get the major release identifier (for example, "4" for version 4.0), the <xref:System.Version.Minor%2A?displayProperty=nameWithType> property to get the minor release identifier (for example, "0" for version 4.0), or the <xref:System.Version.ToString%2A?displayProperty=nameWithType> method to get the entire version string (for example, "4.0.30319.18010", as shown in the following code).</span></span> 

<span data-ttu-id="a48ea-202">4, 4.5, 4.5.1 ve 4.5.2'yi, .NET Framework sürümleri için <xref:System.Environment.Version%2A?displayProperty=nameWithType> özelliği döndürür bir <xref:System.Version> nesnenin dize temsili olan form `4.0.30319.xxxxx`.</span><span class="sxs-lookup"><span data-stu-id="a48ea-202">For the .NET Framework Versions 4, 4.5, 4.5.1, and 4.5.2, the <xref:System.Environment.Version%2A?displayProperty=nameWithType> property returns a <xref:System.Version> object whose string representation has the form `4.0.30319.xxxxx`.</span></span> <span data-ttu-id="a48ea-203">.NET Framework 4.6 ve daha sonra bu biçimde `4.0.30319.42000`.</span><span class="sxs-lookup"><span data-stu-id="a48ea-203">For the .NET Framework 4.6 and later, it has the form `4.0.30319.42000`.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a48ea-204">.NET Framework 4.5 ve sonrası kullanılması önerilmez <xref:System.Environment.Version%2A?displayProperty=nameWithType> özelliği çalışma zamanı sürümünü algılayamaz.</span><span class="sxs-lookup"><span data-stu-id="a48ea-204">For the .NET Framework 4.5 and later, we do not recommend using the  <xref:System.Environment.Version%2A?displayProperty=nameWithType> property to detect the version of the runtime.</span></span> <span data-ttu-id="a48ea-205">Bunun yerine, kayıt defteri sorgu açıklandığı öneririz [(.NET Framework 4.5 ve üstü) kod içinde kayıt defterini sorgulayarak .NET Framework sürümlerini bulmak için](#net_d) bu makalenin önceki kısımlarında bölümü.</span><span class="sxs-lookup"><span data-stu-id="a48ea-205">Instead, we recommend that you query the registry, as described in the [To find .NET Framework versions by querying the registry in code (.NET Framework 4.5 and later)](#net_d) section earlier in this article.</span></span>

<span data-ttu-id="a48ea-206">Aşağıdaki örnekte kullanılan <xref:System.Environment.Version%2A?displayProperty=nameWithType> çalışma zamanı sürüm bilgileri almak için özellik:</span><span class="sxs-lookup"><span data-stu-id="a48ea-206">The following example used the <xref:System.Environment.Version%2A?displayProperty=nameWithType> property to retrieve runtime version information:</span></span>

[!code-csharp[ListVersions](../../../samples/snippets/csharp/framework/migration-guide/versions-installed2.cs)]
[!code-vb[ListVersions](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed2.vb)]

## <a name="see-also"></a><span data-ttu-id="a48ea-207">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a48ea-207">See also</span></span>

- [<span data-ttu-id="a48ea-208">Nasıl yapılır: Hangi .NET Framework güncelleştirmelerinin yüklü olduğunu belirleme</span><span class="sxs-lookup"><span data-stu-id="a48ea-208">How to: Determine Which .NET Framework Updates Are Installed</span></span>](~/docs/framework/migration-guide/how-to-determine-which-net-framework-updates-are-installed.md)
- [<span data-ttu-id="a48ea-209">Geliştiriciler için .NET Framework'ü yükleme</span><span class="sxs-lookup"><span data-stu-id="a48ea-209">Install the .NET Framework for developers</span></span>](../../../docs/framework/install/guide-for-developers.md)
- [<span data-ttu-id="a48ea-210">Sürümler ve Bağımlılıklar</span><span class="sxs-lookup"><span data-stu-id="a48ea-210">Versions and Dependencies</span></span>](~/docs/framework/migration-guide/versions-and-dependencies.md)
