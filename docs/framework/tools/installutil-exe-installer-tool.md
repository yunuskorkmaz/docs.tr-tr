---
title: Installutil.exe (Yükleme Aracı)
ms.date: 03/30/2017
helpviewer_keywords:
- uninstalling server resources
- removing server resources
- status information for installation
- installation progress reports
- installing server resources
- Installer tool
- Installutil.exe
- files, Installer tool
- progress information for installation
- reporting installation progress
ms.assetid: 3f9d0533-f895-4897-b4ea-528284e0241d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8cd7826581a8750d0c5bc87b6223d51eb2b6cce2
ms.sourcegitcommit: a36cfc9dbbfc04bd88971f96e8a3f8e283c15d42
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/11/2019
ms.locfileid: "54221953"
---
# <a name="installutilexe-installer-tool"></a><span data-ttu-id="e712f-102">Installutil.exe (Yükleme Aracı)</span><span class="sxs-lookup"><span data-stu-id="e712f-102">Installutil.exe (Installer Tool)</span></span>
<span data-ttu-id="e712f-103">Yükleyici aracı, yükleyici bileşenlerini belirli derlemelerde yürüterek sunucu kaynaklarını yüklemenize ve kaldırmanıza olanak tanıyan bir komut satırı aracıdır.</span><span class="sxs-lookup"><span data-stu-id="e712f-103">The Installer tool is a command-line utility that allows you to install and uninstall server resources by executing the installer components in specified assemblies.</span></span> <span data-ttu-id="e712f-104">Bu araç, alanındaki sınıflarla birlikte çalışır. <xref:System.Configuration.Install> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="e712f-104">This tool works in conjunction with classes in the <xref:System.Configuration.Install> namespace.</span></span>  
  
 <span data-ttu-id="e712f-105">Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir.</span><span class="sxs-lookup"><span data-stu-id="e712f-105">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="e712f-106">Aracı çalıştırmak için Visual Studio (veya Windows 7'de Visual Studio komut istemi) için geliştirici Komut İstemi'ni kullanın.</span><span class="sxs-lookup"><span data-stu-id="e712f-106">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="e712f-107">Daha fazla bilgi için [komut istemleri](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="e712f-107">For more information, see [Command Prompts](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="e712f-108">Komut satırına şunu yazın:</span><span class="sxs-lookup"><span data-stu-id="e712f-108">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e712f-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e712f-109">Syntax</span></span>  
  
```  
installutil [/u[ninstall]] [options] assembly [[options] assembly] ...  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e712f-110">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e712f-110">Parameters</span></span>  
  
|<span data-ttu-id="e712f-111">Bağımsız Değişken</span><span class="sxs-lookup"><span data-stu-id="e712f-111">Argument</span></span>|<span data-ttu-id="e712f-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e712f-112">Description</span></span>|  
|--------------|-----------------|  
|`assembly`|<span data-ttu-id="e712f-113">Yükleyici bileşenlerinin yürütüleceği derlemenin dosya adı.</span><span class="sxs-lookup"><span data-stu-id="e712f-113">The file name of the assembly in which to execute the installer components.</span></span> <span data-ttu-id="e712f-114">Kullanarak derlemenin tanımlayıcı adını belirtmek istiyorsanız bu parametreyi atlarsanız `/AssemblyName` seçeneği.</span><span class="sxs-lookup"><span data-stu-id="e712f-114">Omit this parameter if you want to specify the assembly's strong name by using the `/AssemblyName` option.</span></span>|  
  
<a name="options"></a>   
## <a name="options"></a><span data-ttu-id="e712f-115">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="e712f-115">Options</span></span>  
  
|<span data-ttu-id="e712f-116">Seçenek</span><span class="sxs-lookup"><span data-stu-id="e712f-116">Option</span></span>|<span data-ttu-id="e712f-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e712f-117">Description</span></span>|  
|------------|-----------------|  
|`/h[elp]`<br /><br /> <span data-ttu-id="e712f-118">-veya-</span><span class="sxs-lookup"><span data-stu-id="e712f-118">-or-</span></span><br /><br /> `/?`|<span data-ttu-id="e712f-119">Araç için komut sözdizimini ve seçenekleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="e712f-119">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="e712f-120">`/help` *Derleme*</span><span class="sxs-lookup"><span data-stu-id="e712f-120">`/help` *assembly*</span></span><br /><br /> <span data-ttu-id="e712f-121">-veya-</span><span class="sxs-lookup"><span data-stu-id="e712f-121">-or-</span></span><br /><br /> <span data-ttu-id="e712f-122">`/?` *Derleme*</span><span class="sxs-lookup"><span data-stu-id="e712f-122">`/?` *assembly*</span></span>|<span data-ttu-id="e712f-123">InstallUtil.exe'ye ilişkin komut sözdizimi ve seçeneklerin yanı sıra, belirtilen derleme içinde tek tek yükleyiciler tarafından tanınan ek seçenekleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="e712f-123">Displays additional options recognized by individual installers within the specified assembly, along with command syntax and options for InstallUtil.exe.</span></span> <span data-ttu-id="e712f-124">Bu seçenek her yükleyici tarafından döndürülen metni ekler <xref:System.Configuration.Install.Installer.HelpText%2A?displayProperty=nameWithType> özelliğini InstallUtil.exe Yardım metni.</span><span class="sxs-lookup"><span data-stu-id="e712f-124">This option adds the text returned by each installer component's <xref:System.Configuration.Install.Installer.HelpText%2A?displayProperty=nameWithType> property to the help text of InstallUtil.exe.</span></span>|  
|<span data-ttu-id="e712f-125">`/AssemblyName` "*assemblyName*</span><span class="sxs-lookup"><span data-stu-id="e712f-125">`/AssemblyName` "*assemblyName*</span></span><br /><br /> <span data-ttu-id="e712f-126">, Sürüm =*major.minor.build.revision*</span><span class="sxs-lookup"><span data-stu-id="e712f-126">,Version=*major.minor.build.revision*</span></span><br /><br /> <span data-ttu-id="e712f-127">, Culture =*yerel ayar*</span><span class="sxs-lookup"><span data-stu-id="e712f-127">,Culture=*locale*</span></span><br /><br /> <span data-ttu-id="e712f-128">,PublicKeyToken=*publicKeyToken*"</span><span class="sxs-lookup"><span data-stu-id="e712f-128">,PublicKeyToken=*publicKeyToken*"</span></span>|<span data-ttu-id="e712f-129">Bir derlemenin, genel derleme önbelleğine kaydedilmesi gereken tanımlayıcı adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="e712f-129">Specifies the strong name of an assembly, which must be registered in the global assembly cache.</span></span> <span data-ttu-id="e712f-130">Derleme adı, derlemenin sürüm, kültür ve genel anahtar belirteciyle birlikte belirtilmelidir.</span><span class="sxs-lookup"><span data-stu-id="e712f-130">The assembly name must be fully qualified with the version, culture, and public key token of the assembly.</span></span> <span data-ttu-id="e712f-131">Tam olarak belirtilen ad, tırnak işareti içine alınmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e712f-131">The fully qualified name must be surrounded by quotes.</span></span><br /><br /> <span data-ttu-id="e712f-132">Örneğin, "myAssembly, Culture=neutral, PublicKeyToken=0038abc9deabfle5, Version=4.0.0.0" tam olaralk belirtilmiş bir derleme adıdır.</span><span class="sxs-lookup"><span data-stu-id="e712f-132">For example, "myAssembly, Culture=neutral, PublicKeyToken=0038abc9deabfle5, Version=4.0.0.0" is a fully qualified assembly name.</span></span>|  
|<span data-ttu-id="e712f-133">`/InstallStateDir=[` *DizinAdı* `]`</span><span class="sxs-lookup"><span data-stu-id="e712f-133">`/InstallStateDir=[` *directoryName* `]`</span></span>|<span data-ttu-id="e712f-134">Derlemeyi yüklemek için kullanılan verileri içeren .InstallState dosyasının dizinini içerir.</span><span class="sxs-lookup"><span data-stu-id="e712f-134">Specifies the directory of the .InstallState file that contains the data used to uninstall the assembly.</span></span> <span data-ttu-id="e712f-135">Varsayılan değer, derlemeyi içeren dizindir.</span><span class="sxs-lookup"><span data-stu-id="e712f-135">The default is the directory that contains the assembly.</span></span>|  
|<span data-ttu-id="e712f-136">`/LogFile=`[*filename*]</span><span class="sxs-lookup"><span data-stu-id="e712f-136">`/LogFile=`[*filename*]</span></span>|<span data-ttu-id="e712f-137">Yükleme ilerlemesinin kaydedildiği günlük dosyasının adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="e712f-137">Specifies the name of the log file where installation progress is recorded.</span></span> <span data-ttu-id="e712f-138">Varsayılan olarak, `/LogFile` seçeneği atlanırsa, adlı bir günlük dosyası *assemblyname*. InstallLog oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="e712f-138">By default, if the `/LogFile` option is omitted, a log file named *assemblyname*.InstallLog is created.</span></span> <span data-ttu-id="e712f-139">Varsa *filename* olan atlanırsa, günlük dosyası oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="e712f-139">If *filename* is omitted, no log file is generated.</span></span>|  
|<span data-ttu-id="e712f-140">`/LogToConsole`={`true`&#124;`false`}</span><span class="sxs-lookup"><span data-stu-id="e712f-140">`/LogToConsole`={`true`&#124;`false`}</span></span>|<span data-ttu-id="e712f-141">Varsa `true`, konsola çıkışı görüntüler.</span><span class="sxs-lookup"><span data-stu-id="e712f-141">If `true`, displays output to the console.</span></span> <span data-ttu-id="e712f-142">Varsa `false` (varsayılan), konsola çıkışı bastırır.</span><span class="sxs-lookup"><span data-stu-id="e712f-142">If `false` (the default), suppresses output to the console.</span></span>|  
|`/ShowCallStack`|<span data-ttu-id="e712f-143">Yükleme sırasında herhangi bir noktada bir özel durum oluşursa, çağrı yığınını günlük dosyana çıkış olarak aktarır.</span><span class="sxs-lookup"><span data-stu-id="e712f-143">Outputs the call stack to the log file if an exception occurs at any point during installation.</span></span>|  
|<span data-ttu-id="e712f-144">`/u`[`ninstall`]</span><span class="sxs-lookup"><span data-stu-id="e712f-144">`/u`[`ninstall`]</span></span>|<span data-ttu-id="e712f-145">Belirtilen derlemeleri kaldırır.</span><span class="sxs-lookup"><span data-stu-id="e712f-145">Uninstalls the specified assemblies.</span></span> <span data-ttu-id="e712f-146">Diğer seçeneklerin tersine `/u` seçeneğin komut satırında göründüğü bağımsız olarak tüm derlemelere uygulanır.</span><span class="sxs-lookup"><span data-stu-id="e712f-146">Unlike the other options, `/u` applies to all assemblies regardless of where the option appears on the command line.</span></span>|  
  
<a name="cmdline"></a>   
## <a name="additional-installer-options"></a><span data-ttu-id="e712f-147">Ek Yükleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="e712f-147">Additional Installer Options</span></span>  
 <span data-ttu-id="e712f-148">Bir derlemede kullanılan her bir yükleyici listelenenlere olarak seçenekleri tanıyabilir [seçenekleri](#options) bölümü.</span><span class="sxs-lookup"><span data-stu-id="e712f-148">Individual installers used within an assembly may recognize options in addition to those listed in the [Options](#options) section.</span></span> <span data-ttu-id="e712f-149">Bu seçenekler hakkında bilgi edinmek için InstallUtil.exe derlemelerin yollarıyla komut satırı ile birlikte çalışan `/?` veya `/help` seçeneği.</span><span class="sxs-lookup"><span data-stu-id="e712f-149">To learn about these options, run InstallUtil.exe with the paths of the assemblies on the command line along with the `/?` or `/help` option.</span></span> <span data-ttu-id="e712f-150">Bu seçenekleri belirtmek için, bunları, InstallUtil.exe tarafından tanınan seçeneklerin yanı sıra komut satırına ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e712f-150">To specify these options, you include them on the command line along with the options recognized by InstallUtil.exe.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e712f-151">Tarafından döndürülen tek tek yükleyici bileşenleri tarafından desteklenen seçeneklerle ilgili Yardım metni <xref:System.Configuration.Install.Installer.HelpText%2A?displayProperty=nameWithType> özelliği.</span><span class="sxs-lookup"><span data-stu-id="e712f-151">Help text on the options supported by individual installer components is returned by the <xref:System.Configuration.Install.Installer.HelpText%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="e712f-152">Komut satırına girilen ayrı ayrı seçenekler programlı olarak erişilebilir <xref:System.Configuration.Install.Installer.Context%2A?displayProperty=nameWithType> özelliği.</span><span class="sxs-lookup"><span data-stu-id="e712f-152">The individual options that have been entered on the command line are accessible programmatically from the <xref:System.Configuration.Install.Installer.Context%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="e712f-153">Tüm seçenekler ve komut satırı parametreleri yükleme günlük dosyasına yazılır.</span><span class="sxs-lookup"><span data-stu-id="e712f-153">All options and command-line parameters are written to the installation log file.</span></span> <span data-ttu-id="e712f-154">Ancak, kullanırsanız `/Password` bazı yükleyici bileşenleri tarafından tanınan parametre, parola bilgisi sekiz yıldız işaretiyle (\*) değiştirilir ve günlük dosyasında görünmez.</span><span class="sxs-lookup"><span data-stu-id="e712f-154">However, if you use the `/Password` parameter, which is recognized by some installer components, the password information will be replaced by eight asterisks (\*) and will not appear in the log file.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="e712f-155">Bazı durumlarda, yükleyiciye geçirilen ve varsayılan olarak düz bir metin günlüğü dosyasına yazılan, hassas veya kişisel olarak tanımlanabilir bilgiler içerebilir.</span><span class="sxs-lookup"><span data-stu-id="e712f-155">In some cases, parameters passed to the installer may include sensitive or personally identifiable information, which, by default, is written to a plain text log file.</span></span> <span data-ttu-id="e712f-156">Bu davranışı engellemek için günlük dosyasını belirterek gizleyebilirsiniz `/LogFile=` (olmadan *filename* bağımsız değişkeni) sonra komut satırında Installutil.exe.</span><span class="sxs-lookup"><span data-stu-id="e712f-156">To prevent this behavior, you can suppress the log file by specifying `/LogFile=` (with no *filename* argument) after Installutil.exe on the command line.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e712f-157">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e712f-157">Remarks</span></span>  
 <span data-ttu-id="e712f-158">.NET Framework uygulamaları, uygulama dağıtıldığında oluşturulması gereken ileti kuyrukları, olay günlükleri ve performans sayaçları gibi geleneksel program dosyalarından ve ilişkili kaynaklardan oluşur.</span><span class="sxs-lookup"><span data-stu-id="e712f-158">.NET Framework applications consist of traditional program files and associated resources, such as message queues, event logs, and performance counters that must be created when the application is deployed.</span></span> <span data-ttu-id="e712f-159">Uygulamanız yüklendiğinde bu kaynakları oluşturmak ve uygulamanız kaldırıldığında kaldırmak için, bir derlemenin yükleyici bileşenlerini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e712f-159">You can use an assembly's installer components to create these resources when your application is installed and to remove them when your application is uninstalled.</span></span> <span data-ttu-id="e712f-160">Installutil.exe, bu yükleyici bileşenlerini algılar ve çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="e712f-160">Installutil.exe detects and executes these installer components.</span></span>  
  
 <span data-ttu-id="e712f-161">Aynı komut satırında birden çok derleme belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e712f-161">You can specify multiple assemblies on the same command line.</span></span> <span data-ttu-id="e712f-162">Derleme adından önce gelen herhangi bir seçenek o derlemenin yüklemesine uygulanır.</span><span class="sxs-lookup"><span data-stu-id="e712f-162">Any option that occurs before an assembly name applies to that assembly's installation.</span></span> <span data-ttu-id="e712f-163">Dışında `/u` ve `/AssemblyName`, Seçenekler birikmelidir, ancak geçersiz kılınabilir.</span><span class="sxs-lookup"><span data-stu-id="e712f-163">Except for `/u` and `/AssemblyName`, options are cumulative but overridable.</span></span> <span data-ttu-id="e712f-164">Diğer bir deyişle, bir derleme için belirtilen seçenekler, seçenek yeni bir değerle belirtilmediği sürece sonraki tüm derlemelere uygulanır.</span><span class="sxs-lookup"><span data-stu-id="e712f-164">That is, options specified for one assembly apply to all subsequent assemblies unless the option is specified with a new value.</span></span>  
  
 <span data-ttu-id="e712f-165">Installutil.exe'yi herhangi bir seçenek belirtmeden bir derlemeye yönelik olarak çalıştırırsanız, aşağıdaki üç dosyayı derlemenin dizinine yerleştirir:</span><span class="sxs-lookup"><span data-stu-id="e712f-165">If you run Installutil.exe against an assembly without specifying any options, it places the following three files into the assembly's directory:</span></span>  
  
-   <span data-ttu-id="e712f-166">InstallUtil.InstallLog - Yükleme ilerlemesinin genel bir açıklamasını içerir.</span><span class="sxs-lookup"><span data-stu-id="e712f-166">InstallUtil.InstallLog - Contains a general description of the installation progress.</span></span>  
  
-   <span data-ttu-id="e712f-167">*AssemblyName*. InstallLog - yükleme işleminin kaydetme aşamasına özel bilgiler içerir.</span><span class="sxs-lookup"><span data-stu-id="e712f-167">*assemblyname*.InstallLog - Contains information specific to the commit phase of the installation process.</span></span> <span data-ttu-id="e712f-168">Kaydetme aşaması hakkında daha fazla bilgi için bkz. <xref:System.Configuration.Install.Installer.Commit%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="e712f-168">For more information about the commit phase, see the <xref:System.Configuration.Install.Installer.Commit%2A> method.</span></span>  
  
-   <span data-ttu-id="e712f-169">*AssemblyName*. InstallState - derlemeyi kaldırmak için kullanılan verileri içerir.</span><span class="sxs-lookup"><span data-stu-id="e712f-169">*assemblyname*.InstallState - Contains data used to uninstall the assembly.</span></span>  
  
 <span data-ttu-id="e712f-170">InstallUtil.exe belirtilen derlemeleri incelemek ve tüm bulmak için yansıtma kullanır <xref:System.Configuration.Install.Installer> sahip türleri <xref:System.ComponentModel.RunInstallerAttribute?displayProperty=nameWithType> özniteliğini `true`.</span><span class="sxs-lookup"><span data-stu-id="e712f-170">Installutil.exe uses reflection to inspect the specified assemblies and to find all <xref:System.Configuration.Install.Installer> types that have the <xref:System.ComponentModel.RunInstallerAttribute?displayProperty=nameWithType> attribute set to `true`.</span></span> <span data-ttu-id="e712f-171">Araç ardından yürütür <xref:System.Configuration.Install.Installer.Install%2A?displayProperty=nameWithType> veya <xref:System.Configuration.Install.Installer.Uninstall%2A?displayProperty=nameWithType> yöntemi her bir örneği üzerinde <xref:System.Configuration.Install.Installer> türü.</span><span class="sxs-lookup"><span data-stu-id="e712f-171">The tool then executes either the <xref:System.Configuration.Install.Installer.Install%2A?displayProperty=nameWithType> or the <xref:System.Configuration.Install.Installer.Uninstall%2A?displayProperty=nameWithType> method on each instance of the <xref:System.Configuration.Install.Installer> type.</span></span> <span data-ttu-id="e712f-172">Installutil.exe, yüklemeyi işlemsel bir şekilde gerçekleştirir; yani, derlemelerden birisi yüklenemezse, diğer tüm derlemelerin yüklemelerini geri alır.</span><span class="sxs-lookup"><span data-stu-id="e712f-172">Installutil.exe performs installation in a transactional manner; that is, if one of the assemblies fails to install, it rolls back the installations of all other assemblies.</span></span> <span data-ttu-id="e712f-173">Kaldırma, işlemsel değildir.</span><span class="sxs-lookup"><span data-stu-id="e712f-173">Uninstall is not transactional.</span></span>  
  
 <span data-ttu-id="e712f-174">Installutil.exe, gecikme imzalı derlemeleri yükleyemez veya kaldıramaz, fakat tanımlayıcı adlı derlemeleri yükleyebilir veya kaldırabilir.</span><span class="sxs-lookup"><span data-stu-id="e712f-174">Installutil.exe cannot install or uninstall delay-signed assemblies, but it can install or uninstall strong-named assemblies.</span></span>  
  
 <span data-ttu-id="e712f-175">.NET Framework sürüm 2.0 ile başlayarak, ortak dil çalışma zamanının (CLR) 32 bit sürümü Yükleyici aracının yalnızca 32 bit sürümüyle birlikte sevk edilir, fakat CLR'nin 64 bit sürümü Yükleyici aracının hem 32 bit hem de 64 bit sürümleriyle birlikte sevk edilir.</span><span class="sxs-lookup"><span data-stu-id="e712f-175">Starting with the .NET Framework version 2.0, the 32-bit version of the common language runtime (CLR) ships with only the 32-bit version of the Installer tool, but the 64-bit version of the CLR ships with both 32-bit and 64-bit versions of the Installer tool.</span></span> <span data-ttu-id="e712f-176">64 bit CLR kullanırken, 32 bit derlemeleri yüklemek için 32 bit Yükleyici aracını, 64 bit ve Microsoft ara dil (MSIL) derlemelerini yüklemek içinse 64 bit Yükleyici aracını kullanın.</span><span class="sxs-lookup"><span data-stu-id="e712f-176">When using the 64-bit CLR, use the 32-bit Installer tool to install 32-bit assemblies, and the 64-bit Installer tool to install 64-bit and Microsoft intermediate language (MSIL) assemblies.</span></span> <span data-ttu-id="e712f-177">Yükleyici aracının her iki sürümü de aynı şekilde davranır.</span><span class="sxs-lookup"><span data-stu-id="e712f-177">Both versions of the Installer tool behave the same.</span></span>  
  
 <span data-ttu-id="e712f-178">Installutil.exe C++ derleyicisi tarafından üretilen gömülü doğal kodu tanıyamayacağından, C++ kullanarak oluşturulan bir Windows hizmetini dağıtmak için Installutil.exe'yi kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="e712f-178">You cannot use Installutil.exe to deploy a Windows service that was created by using C++, because Installutil.exe cannot recognize the embedded native code that is produced by the C++ compiler.</span></span> <span data-ttu-id="e712f-179">Gibi bir C++ Windows hizmetini Installutil.exe, bir özel durum ile dağıtmayı denerseniz <xref:System.BadImageFormatException> oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="e712f-179">If you try to deploy a C++ Windows service with Installutil.exe, an exception such as <xref:System.BadImageFormatException> will be thrown.</span></span> <span data-ttu-id="e712f-180">Bu senaryoyla çalışmak için, hizmet kodunu bir C++ modülüne taşıyın ve sonra yükleyici nesnesini C# veya Visual Basic'te yazın.</span><span class="sxs-lookup"><span data-stu-id="e712f-180">To work with this scenario, move the service code to a C++ module, and then write the installer object in C# or Visual Basic.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="e712f-181">Örnekler</span><span class="sxs-lookup"><span data-stu-id="e712f-181">Examples</span></span>  
 <span data-ttu-id="e712f-182">Aşağıdaki komut, komut sözdiziminin bir açıklamasını ve InstallUtil.exe'ye ilişkin seçenekleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="e712f-182">The following command displays a description of the command syntax and options for InstallUtil.exe.</span></span>  
  
```  
installutil /?  
```  
  
 <span data-ttu-id="e712f-183">Aşağıdaki komut, komut sözdiziminin bir açıklamasını ve InstallUtil.exe'ye ilişkin seçenekleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="e712f-183">The following command displays a description of the command syntax and options for InstallUtil.exe.</span></span> <span data-ttu-id="e712f-184">Bir açıklama ve deki yükleyici bileşenleri tarafından desteklenen seçeneklerin bir listesini de görüntüler `myAssembly.exe` yükleyicinin Yardım metni atandıysa <xref:System.Configuration.Install.Installer.HelpText%2A?displayProperty=nameWithType> özelliği.</span><span class="sxs-lookup"><span data-stu-id="e712f-184">It also displays a description and list of options supported by the installer components in `myAssembly.exe` if help text has been assigned to the installer's <xref:System.Configuration.Install.Installer.HelpText%2A?displayProperty=nameWithType> property.</span></span>  
  
```  
installutil /? myAssembly.exe  
```  
  
 <span data-ttu-id="e712f-185">Aşağıdaki komutu derlemesindeki yükleyici bileşenlerini yürütür `myAssembly.exe`.</span><span class="sxs-lookup"><span data-stu-id="e712f-185">The following command executes the installer components in the assembly `myAssembly.exe`.</span></span>  
  
```  
installutil myAssembly.exe  
```  
  
 <span data-ttu-id="e712f-186">Aşağıdaki komut, kullanarak bir derlemede yükleyici bileşenlerini yürütür `/AssemblyName` anahtarı ve bir tam adı.</span><span class="sxs-lookup"><span data-stu-id="e712f-186">The following command executes the installer components in an assembly by using the `/AssemblyName` switch and a fully qualified name.</span></span>  
  
```  
installutil /AssemblyName "myAssembly, Culture=neutral, PublicKeyToken=0038abc9deabfle5, Version=4.0.0.0"  
```  
  
 <span data-ttu-id="e712f-187">Aşağıdaki komut, dosya adıyla belirtilen bir derlemede ve tanımlayıcı adla belirtilen bir derlemede yükleyici bileşenlerini yürütür.</span><span class="sxs-lookup"><span data-stu-id="e712f-187">The following command executes the installer components in an assembly specified by file name and in an assembly specified by strong name.</span></span> <span data-ttu-id="e712f-188">Dosya adıyla belirtilen tüm derlemelerin tanımlayıcı adla komut satırında belirtilen derlemeleri çünkü gelmelidir Not `/AssemblyName` seçeneği geçersiz.</span><span class="sxs-lookup"><span data-stu-id="e712f-188">Note that all assemblies specified by file name must precede assemblies specified by strong name on the command line, because the `/AssemblyName` option cannot be overridden.</span></span>  
  
```  
installutil myAssembly.exe /AssemblyName "myAssembly, Culture=neutral, PublicKeyToken=0038abc9deabfle5, Version=4.0.0.0"  
```  
  
 <span data-ttu-id="e712f-189">Aşağıdaki komut, derlemesindeki kaldırıcı bileşenlerini yürütür `myAssembly.exe`.</span><span class="sxs-lookup"><span data-stu-id="e712f-189">The following command executes the uninstaller components in the assembly `myAssembly.exe`.</span></span>  
  
```  
installutil /u myAssembly.exe   
```  
  
 <span data-ttu-id="e712f-190">Aşağıdaki komut, derlemelerde kaldırıcı bileşenlerini yürütür `myAssembly1.exe` ve `myAssembly2.exe`.</span><span class="sxs-lookup"><span data-stu-id="e712f-190">The following command executes the uninistaller components in the assemblies `myAssembly1.exe` and `myAssembly2.exe`.</span></span>  
  
```  
installutil myAssembly1.exe /u myAssembly2.exe  
```  
  
 <span data-ttu-id="e712f-191">Çünkü konumunu `/u` komut satırı seçeneği önemli değildir, bu aşağıdaki komuta denktir.</span><span class="sxs-lookup"><span data-stu-id="e712f-191">Because the position of the `/u` option on the command line is not important, this is equivalent to the following command.</span></span>  
  
```  
installutil /u myAssembly1.exe myAssembly2.exe  
```  
  
 <span data-ttu-id="e712f-192">Aşağıdaki komutu derlemesindeki yükleyicileri yürütür `myAssembly.exe` ve ilerleme bilgilerinin yazılacağı belirtir `myLog.InstallLog`.</span><span class="sxs-lookup"><span data-stu-id="e712f-192">The following command executes the installers in the assembly `myAssembly.exe` and specifies that progress information will be written to `myLog.InstallLog`.</span></span>  
  
```  
installutil /LogFile=myLog.InstallLog myAssembly.exe   
```  
  
 <span data-ttu-id="e712f-193">Aşağıdaki komutu derlemesindeki yükleyicileri yürütür `myAssembly.exe`, ilerleme durumu bilgileri için yazılması gerektiğini belirtir `myLog.InstallLog`ve özel kullanan `/reg` sisteme güncelleştirmeler yapılması gerektiğini belirtmek için seçeneği kayıt defteri.</span><span class="sxs-lookup"><span data-stu-id="e712f-193">The following command executes the installers in the assembly `myAssembly.exe`, specifies that progress information should be written to `myLog.InstallLog`, and uses the installers' custom `/reg` option to specify that updates should be made to the system registry.</span></span>  
  
```  
installutil /LogFile=myLog.InstallLog /reg=true myAssembly.exe  
```  
  
 <span data-ttu-id="e712f-194">Aşağıdaki komutu derlemesindeki yükleyicileri yürütür `myAssembly.exe`, kullandığı yükleyicinin özel `/email` kullanıcının e-posta adresini belirtmek için seçeneği ve günlük dosyasına çıkışı bastırır.</span><span class="sxs-lookup"><span data-stu-id="e712f-194">The following command executes the installers in the assembly `myAssembly.exe`, uses the installer's custom `/email` option to specify the user's email address, and suppresses output to the log file.</span></span>  
  
```  
installutil /LogFile= /email=admin@mycompany.com myAssembly.exe  
```  
  
 <span data-ttu-id="e712f-195">Yükleme ilerleme durumu için aşağıdaki komutu Yazar `myAssembly.exe` için `myLog.InstallLog` ve ilerleme durumunu yazan `myTestAssembly.exe` için `myTestLog.InstallLog`.</span><span class="sxs-lookup"><span data-stu-id="e712f-195">The following command writes the installation progress for `myAssembly.exe` to `myLog.InstallLog` and writes the progress for `myTestAssembly.exe` to `myTestLog.InstallLog`.</span></span>  
  
```  
installutil /LogFile=myLog.InstallLog myAssembly.exe /LogFile=myTestLog.InstallLog myTestAssembly.exe  
```  
  
## <a name="see-also"></a><span data-ttu-id="e712f-196">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e712f-196">See Also</span></span>  
 <xref:System.Configuration.Install>  
 [<span data-ttu-id="e712f-197">Araçlar</span><span class="sxs-lookup"><span data-stu-id="e712f-197">Tools</span></span>](../../../docs/framework/tools/index.md)  
 [<span data-ttu-id="e712f-198">Komut İstemleri</span><span class="sxs-lookup"><span data-stu-id="e712f-198">Command Prompts</span></span>](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
