---
title: "Installutil.exe (Yükleme Aracı)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "40"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: edda4e415f8ce0246ce6aa1a4d39f5bb6cec7728
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="installutilexe-installer-tool"></a><span data-ttu-id="6ce87-102">Installutil.exe (Yükleme Aracı)</span><span class="sxs-lookup"><span data-stu-id="6ce87-102">Installutil.exe (Installer Tool)</span></span>
<span data-ttu-id="6ce87-103">Yükleyici aracı, yükleyici bileşenlerini belirli derlemelerde yürüterek sunucu kaynaklarını yüklemenize ve kaldırmanıza olanak tanıyan bir komut satırı aracıdır.</span><span class="sxs-lookup"><span data-stu-id="6ce87-103">The Installer tool is a command-line utility that allows you to install and uninstall server resources by executing the installer components in specified assemblies.</span></span> <span data-ttu-id="6ce87-104">Bu araç, sınıflar ile birlikte çalışır. <xref:System.Configuration.Install> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="6ce87-104">This tool works in conjunction with classes in the <xref:System.Configuration.Install> namespace.</span></span>  
  
 <span data-ttu-id="6ce87-105">Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir.</span><span class="sxs-lookup"><span data-stu-id="6ce87-105">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="6ce87-106">Aracı çalıştırmak için, Geliştirici Komut İstemi (veya Windows 7'de Visual Studio Komut İstemi) kullanın.</span><span class="sxs-lookup"><span data-stu-id="6ce87-106">To run the tool, use the Developer Command Prompt (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="6ce87-107">Daha fazla bilgi için bkz: [komut istemlerini](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="6ce87-107">For more information, see [Command Prompts](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="6ce87-108">Komut satırına şunu yazın:</span><span class="sxs-lookup"><span data-stu-id="6ce87-108">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6ce87-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6ce87-109">Syntax</span></span>  
  
```  
installutil [/u[ninstall]] [options] assembly [[options] assembly] ...  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6ce87-110">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6ce87-110">Parameters</span></span>  
  
|<span data-ttu-id="6ce87-111">Bağımsız Değişken</span><span class="sxs-lookup"><span data-stu-id="6ce87-111">Argument</span></span>|<span data-ttu-id="6ce87-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6ce87-112">Description</span></span>|  
|--------------|-----------------|  
|`assembly`|<span data-ttu-id="6ce87-113">Yükleyici bileşenlerinin yürütüleceği derlemenin dosya adı.</span><span class="sxs-lookup"><span data-stu-id="6ce87-113">The file name of the assembly in which to execute the installer components.</span></span> <span data-ttu-id="6ce87-114">Derleme tanımlayıcı adı kullanarak belirtmek istiyorsanız bu parametreyi atlayın `/AssemblyName` seçeneği.</span><span class="sxs-lookup"><span data-stu-id="6ce87-114">Omit this parameter if you want to specify the assembly's strong name by using the `/AssemblyName` option.</span></span>|  
  
<a name="options"></a>   
## <a name="options"></a><span data-ttu-id="6ce87-115">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="6ce87-115">Options</span></span>  
  
|<span data-ttu-id="6ce87-116">Seçenek</span><span class="sxs-lookup"><span data-stu-id="6ce87-116">Option</span></span>|<span data-ttu-id="6ce87-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6ce87-117">Description</span></span>|  
|------------|-----------------|  
|`/h[elp]`<br /><br /> <span data-ttu-id="6ce87-118">veya</span><span class="sxs-lookup"><span data-stu-id="6ce87-118">-or-</span></span><br /><br /> `/?`|<span data-ttu-id="6ce87-119">Araç için komut sözdizimini ve seçenekleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="6ce87-119">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="6ce87-120">`/help`*derleme*</span><span class="sxs-lookup"><span data-stu-id="6ce87-120">`/help` *assembly*</span></span><br /><br /> <span data-ttu-id="6ce87-121">veya</span><span class="sxs-lookup"><span data-stu-id="6ce87-121">-or-</span></span><br /><br /> <span data-ttu-id="6ce87-122">`/?`*derleme*</span><span class="sxs-lookup"><span data-stu-id="6ce87-122">`/?` *assembly*</span></span>|<span data-ttu-id="6ce87-123">InstallUtil.exe'ye ilişkin komut sözdizimi ve seçeneklerin yanı sıra, belirtilen derleme içinde tek tek yükleyiciler tarafından tanınan ek seçenekleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="6ce87-123">Displays additional options recognized by individual installers within the specified assembly, along with command syntax and options for InstallUtil.exe.</span></span> <span data-ttu-id="6ce87-124">Bu seçenek her yükleyici bileşenin tarafından döndürülen metni ekler <xref:System.Configuration.Install.Installer.HelpText%2A?displayProperty=nameWithType> InstallUtil.exe Yardım metni özelliğine.</span><span class="sxs-lookup"><span data-stu-id="6ce87-124">This option adds the text returned by each installer component's <xref:System.Configuration.Install.Installer.HelpText%2A?displayProperty=nameWithType> property to the help text of InstallUtil.exe.</span></span>|  
|<span data-ttu-id="6ce87-125">`/AssemblyName`"*assemblyName*</span><span class="sxs-lookup"><span data-stu-id="6ce87-125">`/AssemblyName` "*assemblyName*</span></span><br /><br /> <span data-ttu-id="6ce87-126">, Sürüm =*major.minor.build.revision*</span><span class="sxs-lookup"><span data-stu-id="6ce87-126">,Version=*major.minor.build.revision*</span></span><br /><br /> <span data-ttu-id="6ce87-127">, Kültür =*yerel ayar*</span><span class="sxs-lookup"><span data-stu-id="6ce87-127">,Culture=*locale*</span></span><br /><br /> <span data-ttu-id="6ce87-128">PublicKeyToken =*publicKeyToken*"</span><span class="sxs-lookup"><span data-stu-id="6ce87-128">,PublicKeyToken=*publicKeyToken*"</span></span>|<span data-ttu-id="6ce87-129">Bir derlemenin, genel derleme önbelleğine kaydedilmesi gereken tanımlayıcı adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="6ce87-129">Specifies the strong name of an assembly, which must be registered in the global assembly cache.</span></span> <span data-ttu-id="6ce87-130">Derleme adı, derlemenin sürüm, kültür ve genel anahtar belirteciyle birlikte belirtilmelidir.</span><span class="sxs-lookup"><span data-stu-id="6ce87-130">The assembly name must be fully qualified with the version, culture, and public key token of the assembly.</span></span> <span data-ttu-id="6ce87-131">Tam olarak belirtilen ad, tırnak işareti içine alınmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6ce87-131">The fully qualified name must be surrounded by quotes.</span></span><br /><br /> <span data-ttu-id="6ce87-132">Örneğin, "myAssembly, Culture=neutral, PublicKeyToken=0038abc9deabfle5, Version=4.0.0.0" tam olaralk belirtilmiş bir derleme adıdır.</span><span class="sxs-lookup"><span data-stu-id="6ce87-132">For example, "myAssembly, Culture=neutral, PublicKeyToken=0038abc9deabfle5, Version=4.0.0.0" is a fully qualified assembly name.</span></span>|  
|<span data-ttu-id="6ce87-133">`/InstallStateDir=[`*directoryName*`]`</span><span class="sxs-lookup"><span data-stu-id="6ce87-133">`/InstallStateDir=[` *directoryName* `]`</span></span>|<span data-ttu-id="6ce87-134">Derlemeyi yüklemek için kullanılan verileri içeren .InstallState dosyasının dizinini içerir.</span><span class="sxs-lookup"><span data-stu-id="6ce87-134">Specifies the directory of the .InstallState file that contains the data used to uninstall the assembly.</span></span> <span data-ttu-id="6ce87-135">Varsayılan değer, derlemeyi içeren dizindir.</span><span class="sxs-lookup"><span data-stu-id="6ce87-135">The default is the directory that contains the assembly.</span></span>|  
|<span data-ttu-id="6ce87-136">`/LogFile=`[*filename*]</span><span class="sxs-lookup"><span data-stu-id="6ce87-136">`/LogFile=`[*filename*]</span></span>|<span data-ttu-id="6ce87-137">Yükleme ilerlemesinin kaydedildiği günlük dosyasının adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="6ce87-137">Specifies the name of the log file where installation progress is recorded.</span></span> <span data-ttu-id="6ce87-138">Varsayılan olarak, varsa `/LogFile` seçeneği atlanırsa, adlı bir günlük dosyası *assemblyname*. InstallLog oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="6ce87-138">By default, if the `/LogFile` option is omitted, a log file named *assemblyname*.InstallLog is created.</span></span> <span data-ttu-id="6ce87-139">Varsa *filename* olan atlanırsa, herhangi bir günlük dosyası oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="6ce87-139">If *filename* is omitted, no log file is generated.</span></span>|  
|<span data-ttu-id="6ce87-140">`/LogToConsole`={`true`&#124;`false`}</span><span class="sxs-lookup"><span data-stu-id="6ce87-140">`/LogToConsole`={`true`&#124;`false`}</span></span>|<span data-ttu-id="6ce87-141">Varsa `true`, konsola çıktı görüntüler.</span><span class="sxs-lookup"><span data-stu-id="6ce87-141">If `true`, displays output to the console.</span></span> <span data-ttu-id="6ce87-142">Varsa `false` (varsayılan), konsola çıktı gizler.</span><span class="sxs-lookup"><span data-stu-id="6ce87-142">If `false` (the default), suppresses output to the console.</span></span>|  
|`/ShowCallStack`|<span data-ttu-id="6ce87-143">Yükleme sırasında herhangi bir noktada bir özel durum oluşursa, çağrı yığınını günlük dosyana çıkış olarak aktarır.</span><span class="sxs-lookup"><span data-stu-id="6ce87-143">Outputs the call stack to the log file if an exception occurs at any point during installation.</span></span>|  
|<span data-ttu-id="6ce87-144">`/u`[`ninstall`]</span><span class="sxs-lookup"><span data-stu-id="6ce87-144">`/u`[`ninstall`]</span></span>|<span data-ttu-id="6ce87-145">Belirtilen derlemeleri kaldırır.</span><span class="sxs-lookup"><span data-stu-id="6ce87-145">Uninstalls the specified assemblies.</span></span> <span data-ttu-id="6ce87-146">Diğer Seçenekler aksine `/u` seçeneği komut satırında göründüğü bağımsız olarak tüm derlemeler için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="6ce87-146">Unlike the other options, `/u` applies to all assemblies regardless of where the option appears on the command line.</span></span>|  
  
<a name="cmdline"></a>   
## <a name="additional-installer-options"></a><span data-ttu-id="6ce87-147">Ek Yükleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="6ce87-147">Additional Installer Options</span></span>  
 <span data-ttu-id="6ce87-148">Bir derlemede kullanılan bağımsız yükleyiciler seçenekleri de listelenenlere tanıması [seçenekleri](#options) bölümü.</span><span class="sxs-lookup"><span data-stu-id="6ce87-148">Individual installers used within an assembly may recognize options in addition to those listed in the [Options](#options) section.</span></span> <span data-ttu-id="6ce87-149">Bu seçenekler hakkında bilgi edinmek için komut satırında ile birlikte derlemeler yollar ile InstallUtil.exe çalıştırmak `/?` veya `/help` seçeneği.</span><span class="sxs-lookup"><span data-stu-id="6ce87-149">To learn about these options, run InstallUtil.exe with the paths of the assemblies on the command line along with the `/?` or `/help` option.</span></span> <span data-ttu-id="6ce87-150">Bu seçenekleri belirtmek için, bunları, InstallUtil.exe tarafından tanınan seçeneklerin yanı sıra komut satırına ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6ce87-150">To specify these options, you include them on the command line along with the options recognized by InstallUtil.exe.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6ce87-151">Tek tek yükleyici bileşenler tarafından desteklenen seçenekler hakkında Yardım metni tarafından döndürülen <xref:System.Configuration.Install.Installer.HelpText%2A?displayProperty=nameWithType> özelliği.</span><span class="sxs-lookup"><span data-stu-id="6ce87-151">Help text on the options supported by individual installer components is returned by the <xref:System.Configuration.Install.Installer.HelpText%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="6ce87-152">Komut satırında girilen tek seçenekler erişilebilir program aracılığıyla <xref:System.Configuration.Install.Installer.Context%2A?displayProperty=nameWithType> özelliği.</span><span class="sxs-lookup"><span data-stu-id="6ce87-152">The individual options that have been entered on the command line are accessible programmatically from the <xref:System.Configuration.Install.Installer.Context%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="6ce87-153">Tüm seçenekler ve komut satırı parametreleri yükleme günlük dosyasına yazılır.</span><span class="sxs-lookup"><span data-stu-id="6ce87-153">All options and command-line parameters are written to the installation log file.</span></span> <span data-ttu-id="6ce87-154">Ancak, kullanırsanız `/Password` bazı yükleyici bileşenleri tarafından tanınan, parametre parola bilgilerini tarafından sekiz yıldız işareti (*) değiştirilecek ve günlük dosyasında görünmez.</span><span class="sxs-lookup"><span data-stu-id="6ce87-154">However, if you use the `/Password` parameter, which is recognized by some installer components, the password information will be replaced by eight asterisks (*) and will not appear in the log file.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="6ce87-155">Bazı durumlarda, yükleyiciye geçirilen ve varsayılan olarak düz bir metin günlüğü dosyasına yazılan, hassas veya kişisel olarak tanımlanabilir bilgiler içerebilir.</span><span class="sxs-lookup"><span data-stu-id="6ce87-155">In some cases, parameters passed to the installer may include sensitive or personally identifiable information, which, by default, is written to a plain text log file.</span></span> <span data-ttu-id="6ce87-156">Bu davranışı önlemek için günlük dosyası belirterek gizleyebilirsiniz `/LogFile=` (hiçbir *filename* bağımsız değişkeni) komut satırında Installutil.exe sonra.</span><span class="sxs-lookup"><span data-stu-id="6ce87-156">To prevent this behavior, you can suppress the log file by specifying `/LogFile=` (with no *filename* argument) after Installutil.exe on the command line.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6ce87-157">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6ce87-157">Remarks</span></span>  
 <span data-ttu-id="6ce87-158">.NET Framework uygulamaları, uygulama dağıtıldığında oluşturulması gereken ileti kuyrukları, olay günlükleri ve performans sayaçları gibi geleneksel program dosyalarından ve ilişkili kaynaklardan oluşur.</span><span class="sxs-lookup"><span data-stu-id="6ce87-158">.NET Framework applications consist of traditional program files and associated resources, such as message queues, event logs, and performance counters that must be created when the application is deployed.</span></span> <span data-ttu-id="6ce87-159">Uygulamanız yüklendiğinde bu kaynakları oluşturmak ve uygulamanız kaldırıldığında kaldırmak için, bir derlemenin yükleyici bileşenlerini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6ce87-159">You can use an assembly's installer components to create these resources when your application is installed and to remove them when your application is uninstalled.</span></span> <span data-ttu-id="6ce87-160">Installutil.exe, bu yükleyici bileşenlerini algılar ve çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="6ce87-160">Installutil.exe detects and executes these installer components.</span></span>  
  
 <span data-ttu-id="6ce87-161">Aynı komut satırında birden çok derleme belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6ce87-161">You can specify multiple assemblies on the same command line.</span></span> <span data-ttu-id="6ce87-162">Derleme adından önce gelen herhangi bir seçenek o derlemenin yüklemesine uygulanır.</span><span class="sxs-lookup"><span data-stu-id="6ce87-162">Any option that occurs before an assembly name applies to that assembly's installation.</span></span> <span data-ttu-id="6ce87-163">Dışında `/u` ve `/AssemblyName`, seçenekleri toplu ancak geçersiz kılınabilir.</span><span class="sxs-lookup"><span data-stu-id="6ce87-163">Except for `/u` and `/AssemblyName`, options are cumulative but overridable.</span></span> <span data-ttu-id="6ce87-164">Diğer bir deyişle, bir derleme için belirtilen seçenekler, seçenek yeni bir değerle belirtilmediği sürece sonraki tüm derlemelere uygulanır.</span><span class="sxs-lookup"><span data-stu-id="6ce87-164">That is, options specified for one assembly apply to all subsequent assemblies unless the option is specified with a new value.</span></span>  
  
 <span data-ttu-id="6ce87-165">Installutil.exe'yi herhangi bir seçenek belirtmeden bir derlemeye yönelik olarak çalıştırırsanız, aşağıdaki üç dosyayı derlemenin dizinine yerleştirir:</span><span class="sxs-lookup"><span data-stu-id="6ce87-165">If you run Installutil.exe against an assembly without specifying any options, it places the following three files into the assembly's directory:</span></span>  
  
-   <span data-ttu-id="6ce87-166">InstallUtil.InstallLog - Yükleme ilerlemesinin genel bir açıklamasını içerir.</span><span class="sxs-lookup"><span data-stu-id="6ce87-166">InstallUtil.InstallLog - Contains a general description of the installation progress.</span></span>  
  
-   <span data-ttu-id="6ce87-167">*AssemblyName*. InstallLog - yükleme işlemi yürütme aşamasında özgü bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="6ce87-167">*assemblyname*.InstallLog - Contains information specific to the commit phase of the installation process.</span></span> <span data-ttu-id="6ce87-168">Yürütme aşaması hakkında daha fazla bilgi için bkz: <xref:System.Configuration.Install.Installer.Commit%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="6ce87-168">For more information about the commit phase, see the <xref:System.Configuration.Install.Installer.Commit%2A> method.</span></span>  
  
-   <span data-ttu-id="6ce87-169">*AssemblyName*. InstallState - derlemesini kaldırmak için kullanılan verileri içerir.</span><span class="sxs-lookup"><span data-stu-id="6ce87-169">*assemblyname*.InstallState - Contains data used to uninstall the assembly.</span></span>  
  
 <span data-ttu-id="6ce87-170">Belirtilen derlemelere incelenecek ve tüm bulmak için Installutil.exe kullanır yansıma <xref:System.Configuration.Install.Installer> türleri <xref:System.ComponentModel.RunInstallerAttribute?displayProperty=nameWithType> özniteliği kümesine `true`.</span><span class="sxs-lookup"><span data-stu-id="6ce87-170">Installutil.exe uses reflection to inspect the specified assemblies and to find all <xref:System.Configuration.Install.Installer> types that have the <xref:System.ComponentModel.RunInstallerAttribute?displayProperty=nameWithType> attribute set to `true`.</span></span> <span data-ttu-id="6ce87-171">Araç ardından ya da yürütür <xref:System.Configuration.Install.Installer.Install%2A?displayProperty=nameWithType> veya <xref:System.Configuration.Install.Installer.Uninstall%2A?displayProperty=nameWithType> yöntemi her örneği üzerinde <xref:System.Configuration.Install.Installer> türü.</span><span class="sxs-lookup"><span data-stu-id="6ce87-171">The tool then executes either the <xref:System.Configuration.Install.Installer.Install%2A?displayProperty=nameWithType> or the <xref:System.Configuration.Install.Installer.Uninstall%2A?displayProperty=nameWithType> method on each instance of the <xref:System.Configuration.Install.Installer> type.</span></span> <span data-ttu-id="6ce87-172">Installutil.exe, yüklemeyi işlemsel bir şekilde gerçekleştirir; yani, derlemelerden birisi yüklenemezse, diğer tüm derlemelerin yüklemelerini geri alır.</span><span class="sxs-lookup"><span data-stu-id="6ce87-172">Installutil.exe performs installation in a transactional manner; that is, if one of the assemblies fails to install, it rolls back the installations of all other assemblies.</span></span> <span data-ttu-id="6ce87-173">Kaldırma, işlemsel değildir.</span><span class="sxs-lookup"><span data-stu-id="6ce87-173">Uninstall is not transactional.</span></span>  
  
 <span data-ttu-id="6ce87-174">Installutil.exe, gecikme imzalı derlemeleri yükleyemez veya kaldıramaz, fakat tanımlayıcı adlı derlemeleri yükleyebilir veya kaldırabilir.</span><span class="sxs-lookup"><span data-stu-id="6ce87-174">Installutil.exe cannot install or uninstall delay-signed assemblies, but it can install or uninstall strong-named assemblies.</span></span>  
  
 <span data-ttu-id="6ce87-175">.NET Framework sürüm 2.0 ile başlayarak, ortak dil çalışma zamanının (CLR) 32 bit sürümü Yükleyici aracının yalnızca 32 bit sürümüyle birlikte sevk edilir, fakat CLR'nin 64 bit sürümü Yükleyici aracının hem 32 bit hem de 64 bit sürümleriyle birlikte sevk edilir.</span><span class="sxs-lookup"><span data-stu-id="6ce87-175">Starting with the .NET Framework version 2.0, the 32-bit version of the common language runtime (CLR) ships with only the 32-bit version of the Installer tool, but the 64-bit version of the CLR ships with both 32-bit and 64-bit versions of the Installer tool.</span></span> <span data-ttu-id="6ce87-176">64 bit CLR kullanırken, 32 bit derlemeleri yüklemek için 32 bit Yükleyici aracını, 64 bit ve Microsoft ara dil (MSIL) derlemelerini yüklemek içinse 64 bit Yükleyici aracını kullanın.</span><span class="sxs-lookup"><span data-stu-id="6ce87-176">When using the 64-bit CLR, use the 32-bit Installer tool to install 32-bit assemblies, and the 64-bit Installer tool to install 64-bit and Microsoft intermediate language (MSIL) assemblies.</span></span> <span data-ttu-id="6ce87-177">Yükleyici aracının her iki sürümü de aynı şekilde davranır.</span><span class="sxs-lookup"><span data-stu-id="6ce87-177">Both versions of the Installer tool behave the same.</span></span>  
  
 <span data-ttu-id="6ce87-178">Installutil.exe C++ derleyicisi tarafından üretilen gömülü doğal kodu tanıyamayacağından, C++ kullanarak oluşturulan bir Windows hizmetini dağıtmak için Installutil.exe'yi kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="6ce87-178">You cannot use Installutil.exe to deploy a Windows service that was created by using C++, because Installutil.exe cannot recognize the embedded native code that is produced by the C++ compiler.</span></span> <span data-ttu-id="6ce87-179">C++ Windows hizmeti Installutil.exe, bir özel durum ile gibi dağıtmaya çalışırsanız <xref:System.BadImageFormatException> oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="6ce87-179">If you try to deploy a C++ Windows service with Installutil.exe, an exception such as <xref:System.BadImageFormatException> will be thrown.</span></span> <span data-ttu-id="6ce87-180">Bu senaryoyla çalışmak için, hizmet kodunu bir C++ modülüne taşıyın ve sonra yükleyici nesnesini C# veya Visual Basic'te yazın.</span><span class="sxs-lookup"><span data-stu-id="6ce87-180">To work with this scenario, move the service code to a C++ module, and then write the installer object in C# or Visual Basic.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="6ce87-181">Örnekler</span><span class="sxs-lookup"><span data-stu-id="6ce87-181">Examples</span></span>  
 <span data-ttu-id="6ce87-182">Aşağıdaki komut, komut sözdiziminin bir açıklamasını ve InstallUtil.exe'ye ilişkin seçenekleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="6ce87-182">The following command displays a description of the command syntax and options for InstallUtil.exe.</span></span>  
  
```  
installutil /?  
```  
  
 <span data-ttu-id="6ce87-183">Aşağıdaki komut, komut sözdiziminin bir açıklamasını ve InstallUtil.exe'ye ilişkin seçenekleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="6ce87-183">The following command displays a description of the command syntax and options for InstallUtil.exe.</span></span> <span data-ttu-id="6ce87-184">Yükleyici bileşenler tarafından desteklenen seçenekler listesinde ve açıklama ayrıca görüntüler `myAssembly.exe` Yardım metni yükleyicinin atanmışsa <xref:System.Configuration.Install.Installer.HelpText%2A?displayProperty=nameWithType> özelliği.</span><span class="sxs-lookup"><span data-stu-id="6ce87-184">It also displays a description and list of options supported by the installer components in `myAssembly.exe` if help text has been assigned to the installer's <xref:System.Configuration.Install.Installer.HelpText%2A?displayProperty=nameWithType> property.</span></span>  
  
```  
installutil /? myAssembly.exe  
```  
  
 <span data-ttu-id="6ce87-185">Aşağıdaki komutu yükleyici bileşenleri derlemede yürütür `myAssembly.exe`.</span><span class="sxs-lookup"><span data-stu-id="6ce87-185">The following command executes the installer components in the assembly `myAssembly.exe`.</span></span>  
  
```  
installutil myAssembly.exe  
```  
  
 <span data-ttu-id="6ce87-186">Aşağıdaki komutu kullanarak yükleyici bileşenleri bir derlemede yürütür `/AssemblyName` anahtarı ve bir tam ad.</span><span class="sxs-lookup"><span data-stu-id="6ce87-186">The following command executes the installer components in an assembly by using the `/AssemblyName` switch and a fully qualified name.</span></span>  
  
```  
installutil /AssemblyName "myAssembly, Culture=neutral, PublicKeyToken=0038abc9deabfle5, Version=4.0.0.0"  
```  
  
 <span data-ttu-id="6ce87-187">Aşağıdaki komut, dosya adıyla belirtilen bir derlemede ve tanımlayıcı adla belirtilen bir derlemede yükleyici bileşenlerini yürütür.</span><span class="sxs-lookup"><span data-stu-id="6ce87-187">The following command executes the installer components in an assembly specified by file name and in an assembly specified by strong name.</span></span> <span data-ttu-id="6ce87-188">Dosya adıyla belirtilen tüm derlemelerde olduğundan komut satırında güçlü adıyla belirtilen derlemeleri gelmelidir Not `/AssemblyName` seçeneği geçersiz kılınamaz.</span><span class="sxs-lookup"><span data-stu-id="6ce87-188">Note that all assemblies specified by file name must precede assemblies specified by strong name on the command line, because the `/AssemblyName` option cannot be overridden.</span></span>  
  
```  
installutil myAssembly.exe /AssemblyName "myAssembly, Culture=neutral, PublicKeyToken=0038abc9deabfle5, Version=4.0.0.0"  
```  
  
 <span data-ttu-id="6ce87-189">Aşağıdaki komutu kaldırıcı bileşenleri derlemede yürütür `myAssembly.exe`.</span><span class="sxs-lookup"><span data-stu-id="6ce87-189">The following command executes the uninstaller components in the assembly `myAssembly.exe`.</span></span>  
  
```  
installutil /u myAssembly.exe   
```  
  
 <span data-ttu-id="6ce87-190">Aşağıdaki komutu uninistaller bileşenleri derlemelerde yürütür `myAssembly1.exe` ve `myAssembly2.exe`.</span><span class="sxs-lookup"><span data-stu-id="6ce87-190">The following command executes the uninistaller components in the assemblies `myAssembly1.exe` and `myAssembly2.exe`.</span></span>  
  
```  
installutil myAssembly1.exe /u myAssembly2.exe  
```  
  
 <span data-ttu-id="6ce87-191">Çünkü konumunu `/u` komut satırı seçeneği önemli değildir, bu aşağıdaki komutu ile eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="6ce87-191">Because the position of the `/u` option on the command line is not important, this is equivalent to the following command.</span></span>  
  
```  
installutil /u myAssembly1.exe myAssembly2.exe  
```  
  
 <span data-ttu-id="6ce87-192">Aşağıdaki komutu yükleyicileri derlemede yürütür `myAssembly.exe` ve ilerleme durumu bilgileri yazılacağı belirtir `myLog.InstallLog`.</span><span class="sxs-lookup"><span data-stu-id="6ce87-192">The following command executes the installers in the assembly `myAssembly.exe` and specifies that progress information will be written to `myLog.InstallLog`.</span></span>  
  
```  
installutil /LogFile=myLog.InstallLog myAssembly.exe   
```  
  
 <span data-ttu-id="6ce87-193">Aşağıdaki komutu yükleyicileri derlemede yürütür `myAssembly.exe`, ilerleme durumu bilgileri için yazılması gerektiğini belirtir `myLog.InstallLog`ve yükleyicilerini özel kullanır `/reg` güncelleştirmeleri sisteme yapılması gerektiğini belirtmek için seçeneği kayıt defteri.</span><span class="sxs-lookup"><span data-stu-id="6ce87-193">The following command executes the installers in the assembly `myAssembly.exe`, specifies that progress information should be written to `myLog.InstallLog`, and uses the installers' custom `/reg` option to specify that updates should be made to the system registry.</span></span>  
  
```  
installutil /LogFile=myLog.InstallLog /reg=true myAssembly.exe  
```  
  
 <span data-ttu-id="6ce87-194">Aşağıdaki komutu yükleyicileri derlemede yürütür `myAssembly.exe`, kullandığı yükleyici özel `/email` kullanıcının e-posta adresini belirtmek için seçenek ve çıktı günlük dosyasına gizler.</span><span class="sxs-lookup"><span data-stu-id="6ce87-194">The following command executes the installers in the assembly `myAssembly.exe`, uses the installer's custom `/email` option to specify the user's e-mail address, and suppresses output to the log file.</span></span>  
  
```  
installutil /LogFile= /email=admin@mycompany.com myAssembly.exe  
```  
  
 <span data-ttu-id="6ce87-195">Yükleme ilerleme durumu için aşağıdaki komutu Yazar `myAssembly.exe` için `myLog.InstallLog` ve ilerleyişini Yazar `myTestAssembly.exe` için `myTestLog.InstallLog`.</span><span class="sxs-lookup"><span data-stu-id="6ce87-195">The following command writes the installation progress for `myAssembly.exe` to `myLog.InstallLog` and writes the progress for `myTestAssembly.exe` to `myTestLog.InstallLog`.</span></span>  
  
```  
installutil /LogFile=myLog.InstallLog myAssembly.exe /LogFile=myTestLog.InstallLog myTestAssembly.exe  
```  
  
## <a name="see-also"></a><span data-ttu-id="6ce87-196">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6ce87-196">See Also</span></span>  
 <xref:System.Configuration.Install>  
 [<span data-ttu-id="6ce87-197">Araçlar</span><span class="sxs-lookup"><span data-stu-id="6ce87-197">Tools</span></span>](../../../docs/framework/tools/index.md)  
 [<span data-ttu-id="6ce87-198">Komut İstemleri</span><span class="sxs-lookup"><span data-stu-id="6ce87-198">Command Prompts</span></span>](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
