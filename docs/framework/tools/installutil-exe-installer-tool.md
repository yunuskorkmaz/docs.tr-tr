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
ms.openlocfilehash: 5ad0497bd5303dc4113dbb7b8078c70cb044cc95
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71044536"
---
# <a name="installutilexe-installer-tool"></a><span data-ttu-id="a9f07-102">Installutil.exe (Yükleme Aracı)</span><span class="sxs-lookup"><span data-stu-id="a9f07-102">Installutil.exe (Installer Tool)</span></span>

<span data-ttu-id="a9f07-103">Yükleyici aracı, yükleyici bileşenlerini belirli derlemelerde yürüterek sunucu kaynaklarını yüklemenize ve kaldırmanıza olanak tanıyan bir komut satırı aracıdır.</span><span class="sxs-lookup"><span data-stu-id="a9f07-103">The Installer tool is a command-line utility that allows you to install and uninstall server resources by executing the installer components in specified assemblies.</span></span> <span data-ttu-id="a9f07-104">Bu araç, <xref:System.Configuration.Install> ad alanındaki sınıflarla birlikte çalışmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a9f07-104">This tool works in conjunction with classes in the <xref:System.Configuration.Install> namespace.</span></span>

<span data-ttu-id="a9f07-105">Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir.</span><span class="sxs-lookup"><span data-stu-id="a9f07-105">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="a9f07-106">Aracı çalıştırmak için, Visual Studio için Geliştirici Komut İstemi (veya Windows 7 ' de Visual Studio komut Istemi) kullanın.</span><span class="sxs-lookup"><span data-stu-id="a9f07-106">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="a9f07-107">Daha fazla bilgi için bkz. [komut istemleri](developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="a9f07-107">For more information, see [Command Prompts](developer-command-prompt-for-vs.md).</span></span>

<span data-ttu-id="a9f07-108">Komut satırına şunu yazın:</span><span class="sxs-lookup"><span data-stu-id="a9f07-108">At the command prompt, type the following:</span></span>

## <a name="syntax"></a><span data-ttu-id="a9f07-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a9f07-109">Syntax</span></span>

```console
installutil [/u[ninstall]] [options] assembly [[options] assembly] ...
```

## <a name="parameters"></a><span data-ttu-id="a9f07-110">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a9f07-110">Parameters</span></span>

|<span data-ttu-id="a9f07-111">Bağımsız Değişken</span><span class="sxs-lookup"><span data-stu-id="a9f07-111">Argument</span></span>|<span data-ttu-id="a9f07-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a9f07-112">Description</span></span>|
|--------------|-----------------|
|`assembly`|<span data-ttu-id="a9f07-113">Yükleyici bileşenlerinin yürütüleceği derlemenin dosya adı.</span><span class="sxs-lookup"><span data-stu-id="a9f07-113">The file name of the assembly in which to execute the installer components.</span></span> <span data-ttu-id="a9f07-114">`/AssemblyName` Seçeneğini kullanarak derlemenin tanımlayıcı adını belirtmek istiyorsanız bu parametreyi atlayın.</span><span class="sxs-lookup"><span data-stu-id="a9f07-114">Omit this parameter if you want to specify the assembly's strong name by using the `/AssemblyName` option.</span></span>|

<a name="options"></a>

## <a name="options"></a><span data-ttu-id="a9f07-115">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="a9f07-115">Options</span></span>

|<span data-ttu-id="a9f07-116">Seçenek</span><span class="sxs-lookup"><span data-stu-id="a9f07-116">Option</span></span>|<span data-ttu-id="a9f07-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a9f07-117">Description</span></span>|
|------------|-----------------|
|`/h[elp]`<br /><br /> <span data-ttu-id="a9f07-118">-veya-</span><span class="sxs-lookup"><span data-stu-id="a9f07-118">-or-</span></span><br /><br /> `/?`|<span data-ttu-id="a9f07-119">Araç için komut sözdizimini ve seçenekleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="a9f07-119">Displays command syntax and options for the tool.</span></span>|
|<span data-ttu-id="a9f07-120">`/help`*derleme*</span><span class="sxs-lookup"><span data-stu-id="a9f07-120">`/help` *assembly*</span></span><br /><br /> <span data-ttu-id="a9f07-121">-veya-</span><span class="sxs-lookup"><span data-stu-id="a9f07-121">-or-</span></span><br /><br /> <span data-ttu-id="a9f07-122">`/?`*derleme*</span><span class="sxs-lookup"><span data-stu-id="a9f07-122">`/?` *assembly*</span></span>|<span data-ttu-id="a9f07-123">InstallUtil.exe'ye ilişkin komut sözdizimi ve seçeneklerin yanı sıra, belirtilen derleme içinde tek tek yükleyiciler tarafından tanınan ek seçenekleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="a9f07-123">Displays additional options recognized by individual installers within the specified assembly, along with command syntax and options for InstallUtil.exe.</span></span> <span data-ttu-id="a9f07-124">Bu seçenek, her bir yükleyici bileşeninin <xref:System.Configuration.Install.Installer.HelpText%2A?displayProperty=nameWithType> özelliği tarafından döndürülen metni InstallUtil. exe ' nin yardım metnine ekler.</span><span class="sxs-lookup"><span data-stu-id="a9f07-124">This option adds the text returned by each installer component's <xref:System.Configuration.Install.Installer.HelpText%2A?displayProperty=nameWithType> property to the help text of InstallUtil.exe.</span></span>|
|<span data-ttu-id="a9f07-125">`/AssemblyName`"*AssemblyName*</span><span class="sxs-lookup"><span data-stu-id="a9f07-125">`/AssemblyName` "*assemblyName*</span></span><br /><br /> <span data-ttu-id="a9f07-126">, Sürüm =*ana. ikincil. derleme. düzeltme*</span><span class="sxs-lookup"><span data-stu-id="a9f07-126">,Version=*major.minor.build.revision*</span></span><br /><br /> <span data-ttu-id="a9f07-127">, Kültür =*yerel ayar*</span><span class="sxs-lookup"><span data-stu-id="a9f07-127">,Culture=*locale*</span></span><br /><br /> <span data-ttu-id="a9f07-128">,PublicKeyToken=*publicKeyToken*"</span><span class="sxs-lookup"><span data-stu-id="a9f07-128">,PublicKeyToken=*publicKeyToken*"</span></span>|<span data-ttu-id="a9f07-129">Bir derlemenin, genel derleme önbelleğine kaydedilmesi gereken tanımlayıcı adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="a9f07-129">Specifies the strong name of an assembly, which must be registered in the global assembly cache.</span></span> <span data-ttu-id="a9f07-130">Derleme adı, derlemenin sürüm, kültür ve genel anahtar belirteciyle birlikte belirtilmelidir.</span><span class="sxs-lookup"><span data-stu-id="a9f07-130">The assembly name must be fully qualified with the version, culture, and public key token of the assembly.</span></span> <span data-ttu-id="a9f07-131">Tam olarak belirtilen ad, tırnak işareti içine alınmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a9f07-131">The fully qualified name must be surrounded by quotes.</span></span><br /><br /> <span data-ttu-id="a9f07-132">Örneğin, "myAssembly, Culture=neutral, PublicKeyToken=0038abc9deabfle5, Version=4.0.0.0" tam olaralk belirtilmiş bir derleme adıdır.</span><span class="sxs-lookup"><span data-stu-id="a9f07-132">For example, "myAssembly, Culture=neutral, PublicKeyToken=0038abc9deabfle5, Version=4.0.0.0" is a fully qualified assembly name.</span></span>|
|<span data-ttu-id="a9f07-133">`/InstallStateDir=[`*DirectoryName*`]`</span><span class="sxs-lookup"><span data-stu-id="a9f07-133">`/InstallStateDir=[` *directoryName* `]`</span></span>|<span data-ttu-id="a9f07-134">Derlemeyi yüklemek için kullanılan verileri içeren .InstallState dosyasının dizinini içerir.</span><span class="sxs-lookup"><span data-stu-id="a9f07-134">Specifies the directory of the .InstallState file that contains the data used to uninstall the assembly.</span></span> <span data-ttu-id="a9f07-135">Varsayılan değer, derlemeyi içeren dizindir.</span><span class="sxs-lookup"><span data-stu-id="a9f07-135">The default is the directory that contains the assembly.</span></span>|
|<span data-ttu-id="a9f07-136">`/LogFile=`[*dosya adı*]</span><span class="sxs-lookup"><span data-stu-id="a9f07-136">`/LogFile=`[*filename*]</span></span>|<span data-ttu-id="a9f07-137">Yükleme ilerlemesinin kaydedildiği günlük dosyasının adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="a9f07-137">Specifies the name of the log file where installation progress is recorded.</span></span> <span data-ttu-id="a9f07-138">Varsayılan `/LogFile` olarak, seçeneği atlanırsa *AssemblyName*adlı bir günlük dosyası. InstallLog oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="a9f07-138">By default, if the `/LogFile` option is omitted, a log file named *assemblyname*.InstallLog is created.</span></span> <span data-ttu-id="a9f07-139">*Dosya adı* atlanırsa, günlük dosyası oluşturulmaz.</span><span class="sxs-lookup"><span data-stu-id="a9f07-139">If *filename* is omitted, no log file is generated.</span></span>|
|<span data-ttu-id="a9f07-140">`/LogToConsole`={`true`&#124;`false`}</span><span class="sxs-lookup"><span data-stu-id="a9f07-140">`/LogToConsole`={`true`&#124;`false`}</span></span>|<span data-ttu-id="a9f07-141">`true`, Çıktıyı konsola görüntüler.</span><span class="sxs-lookup"><span data-stu-id="a9f07-141">If `true`, displays output to the console.</span></span> <span data-ttu-id="a9f07-142">`false` (Varsayılan), çıktıyı konsola bastırır.</span><span class="sxs-lookup"><span data-stu-id="a9f07-142">If `false` (the default), suppresses output to the console.</span></span>|
|`/ShowCallStack`|<span data-ttu-id="a9f07-143">Yükleme sırasında herhangi bir noktada bir özel durum oluşursa, çağrı yığınını günlük dosyana çıkış olarak aktarır.</span><span class="sxs-lookup"><span data-stu-id="a9f07-143">Outputs the call stack to the log file if an exception occurs at any point during installation.</span></span>|
|<span data-ttu-id="a9f07-144">`/u`[`ninstall`]</span><span class="sxs-lookup"><span data-stu-id="a9f07-144">`/u`[`ninstall`]</span></span>|<span data-ttu-id="a9f07-145">Belirtilen derlemeleri kaldırır.</span><span class="sxs-lookup"><span data-stu-id="a9f07-145">Uninstalls the specified assemblies.</span></span> <span data-ttu-id="a9f07-146">Diğer seçeneklerin aksine, `/u` seçeneğin komut satırında göründüğü yere bakılmaksızın tüm derlemeler için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="a9f07-146">Unlike the other options, `/u` applies to all assemblies regardless of where the option appears on the command line.</span></span>|

<a name="cmdline"></a>

## <a name="additional-installer-options"></a><span data-ttu-id="a9f07-147">Ek Yükleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="a9f07-147">Additional Installer Options</span></span>

<span data-ttu-id="a9f07-148">Bir derlemede kullanılan bireysel yükleyiciler [Seçenekler](#options) bölümünde listelenenlere ek olarak seçenekleri tanıyabilir.</span><span class="sxs-lookup"><span data-stu-id="a9f07-148">Individual installers used within an assembly may recognize options in addition to those listed in the [Options](#options) section.</span></span> <span data-ttu-id="a9f07-149">Bu seçenekler hakkında bilgi edinmek için, komut satırındaki derlemelerin yollarıyla birlikte `/?` InstallUtil. exe ' yi veya `/help` seçeneğini çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="a9f07-149">To learn about these options, run InstallUtil.exe with the paths of the assemblies on the command line along with the `/?` or `/help` option.</span></span> <span data-ttu-id="a9f07-150">Bu seçenekleri belirtmek için, bunları, InstallUtil.exe tarafından tanınan seçeneklerin yanı sıra komut satırına ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a9f07-150">To specify these options, you include them on the command line along with the options recognized by InstallUtil.exe.</span></span>

> [!NOTE]
> <span data-ttu-id="a9f07-151">Ayrı yükleyici bileşenleri tarafından desteklenen seçeneklerde yardım metni, <xref:System.Configuration.Install.Installer.HelpText%2A?displayProperty=nameWithType> özelliği tarafından döndürülür.</span><span class="sxs-lookup"><span data-stu-id="a9f07-151">Help text on the options supported by individual installer components is returned by the <xref:System.Configuration.Install.Installer.HelpText%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="a9f07-152">Komut satırına girilen tek tek seçeneklere <xref:System.Configuration.Install.Installer.Context%2A?displayProperty=nameWithType> özelliğinden programlı olarak erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="a9f07-152">The individual options that have been entered on the command line are accessible programmatically from the <xref:System.Configuration.Install.Installer.Context%2A?displayProperty=nameWithType> property.</span></span>

<span data-ttu-id="a9f07-153">Tüm seçenekler ve komut satırı parametreleri yükleme günlük dosyasına yazılır.</span><span class="sxs-lookup"><span data-stu-id="a9f07-153">All options and command-line parameters are written to the installation log file.</span></span> <span data-ttu-id="a9f07-154">Ancak, bazı yükleyici bileşenleri tarafından `/Password` tanınan parametresini kullanırsanız, parola bilgileri sekiz yıldız işaretiyle (\*) değişir ve günlük dosyasında görünmez.</span><span class="sxs-lookup"><span data-stu-id="a9f07-154">However, if you use the `/Password` parameter, which is recognized by some installer components, the password information will be replaced by eight asterisks (\*) and will not appear in the log file.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a9f07-155">Bazı durumlarda, yükleyiciye geçirilen ve varsayılan olarak düz bir metin günlüğü dosyasına yazılan, hassas veya kişisel olarak tanımlanabilir bilgiler içerebilir.</span><span class="sxs-lookup"><span data-stu-id="a9f07-155">In some cases, parameters passed to the installer may include sensitive or personally identifiable information, which, by default, is written to a plain text log file.</span></span> <span data-ttu-id="a9f07-156">Bu davranışı önlemek için, komut satırında InstallUtil. exe ' den `/LogFile=` sonra ( *dosya adı* olmadan) öğesini belirterek günlük dosyasını bastırın.</span><span class="sxs-lookup"><span data-stu-id="a9f07-156">To prevent this behavior, you can suppress the log file by specifying `/LogFile=` (with no *filename* argument) after Installutil.exe on the command line.</span></span>

## <a name="remarks"></a><span data-ttu-id="a9f07-157">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a9f07-157">Remarks</span></span>

<span data-ttu-id="a9f07-158">.NET Framework uygulamaları, uygulama dağıtıldığında oluşturulması gereken ileti kuyrukları, olay günlükleri ve performans sayaçları gibi geleneksel program dosyalarından ve ilişkili kaynaklardan oluşur.</span><span class="sxs-lookup"><span data-stu-id="a9f07-158">.NET Framework applications consist of traditional program files and associated resources, such as message queues, event logs, and performance counters that must be created when the application is deployed.</span></span> <span data-ttu-id="a9f07-159">Uygulamanız yüklendiğinde bu kaynakları oluşturmak ve uygulamanız kaldırıldığında kaldırmak için, bir derlemenin yükleyici bileşenlerini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a9f07-159">You can use an assembly's installer components to create these resources when your application is installed and to remove them when your application is uninstalled.</span></span> <span data-ttu-id="a9f07-160">Installutil.exe, bu yükleyici bileşenlerini algılar ve çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="a9f07-160">Installutil.exe detects and executes these installer components.</span></span>

<span data-ttu-id="a9f07-161">Aynı komut satırında birden çok derleme belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a9f07-161">You can specify multiple assemblies on the same command line.</span></span> <span data-ttu-id="a9f07-162">Derleme adından önce gelen herhangi bir seçenek o derlemenin yüklemesine uygulanır.</span><span class="sxs-lookup"><span data-stu-id="a9f07-162">Any option that occurs before an assembly name applies to that assembly's installation.</span></span> <span data-ttu-id="a9f07-163">`/u` Ve`/AssemblyName`dışında, Seçenekler birikimli ancak geçersiz kılınabilir.</span><span class="sxs-lookup"><span data-stu-id="a9f07-163">Except for `/u` and `/AssemblyName`, options are cumulative but overridable.</span></span> <span data-ttu-id="a9f07-164">Diğer bir deyişle, bir derleme için belirtilen seçenekler, seçenek yeni bir değerle belirtilmediği sürece sonraki tüm derlemelere uygulanır.</span><span class="sxs-lookup"><span data-stu-id="a9f07-164">That is, options specified for one assembly apply to all subsequent assemblies unless the option is specified with a new value.</span></span>

<span data-ttu-id="a9f07-165">Installutil.exe'yi herhangi bir seçenek belirtmeden bir derlemeye yönelik olarak çalıştırırsanız, aşağıdaki üç dosyayı derlemenin dizinine yerleştirir:</span><span class="sxs-lookup"><span data-stu-id="a9f07-165">If you run Installutil.exe against an assembly without specifying any options, it places the following three files into the assembly's directory:</span></span>

- <span data-ttu-id="a9f07-166">InstallUtil.InstallLog - Yükleme ilerlemesinin genel bir açıklamasını içerir.</span><span class="sxs-lookup"><span data-stu-id="a9f07-166">InstallUtil.InstallLog - Contains a general description of the installation progress.</span></span>

- <span data-ttu-id="a9f07-167">*AssemblyName*. InstallLog-yükleme işleminin kaydetme aşamasına özgü bilgileri Içerir.</span><span class="sxs-lookup"><span data-stu-id="a9f07-167">*assemblyname*.InstallLog - Contains information specific to the commit phase of the installation process.</span></span> <span data-ttu-id="a9f07-168">Tamamlama aşaması hakkında daha fazla bilgi için, bkz <xref:System.Configuration.Install.Installer.Commit%2A> . yöntemi.</span><span class="sxs-lookup"><span data-stu-id="a9f07-168">For more information about the commit phase, see the <xref:System.Configuration.Install.Installer.Commit%2A> method.</span></span>

- <span data-ttu-id="a9f07-169">*AssemblyName*. InstallState-derlemeyi kaldırmak için kullanılan verileri Içerir.</span><span class="sxs-lookup"><span data-stu-id="a9f07-169">*assemblyname*.InstallState - Contains data used to uninstall the assembly.</span></span>

<span data-ttu-id="a9f07-170">InstallUtil. exe, <xref:System.Configuration.Install.Installer> <xref:System.ComponentModel.RunInstallerAttribute?displayProperty=nameWithType> belirtilen derlemeleri incelemek ve özniteliği olarak `true`ayarlanmış tüm türleri bulmak için yansıma kullanır.</span><span class="sxs-lookup"><span data-stu-id="a9f07-170">Installutil.exe uses reflection to inspect the specified assemblies and to find all <xref:System.Configuration.Install.Installer> types that have the <xref:System.ComponentModel.RunInstallerAttribute?displayProperty=nameWithType> attribute set to `true`.</span></span> <span data-ttu-id="a9f07-171">Araç daha sonra <xref:System.Configuration.Install.Installer.Install%2A?displayProperty=nameWithType> <xref:System.Configuration.Install.Installer> türü her örneği üzerinde <xref:System.Configuration.Install.Installer.Uninstall%2A?displayProperty=nameWithType> ya da yöntemini yürütür.</span><span class="sxs-lookup"><span data-stu-id="a9f07-171">The tool then executes either the <xref:System.Configuration.Install.Installer.Install%2A?displayProperty=nameWithType> or the <xref:System.Configuration.Install.Installer.Uninstall%2A?displayProperty=nameWithType> method on each instance of the <xref:System.Configuration.Install.Installer> type.</span></span> <span data-ttu-id="a9f07-172">Installutil.exe, yüklemeyi işlemsel bir şekilde gerçekleştirir; yani, derlemelerden birisi yüklenemezse, diğer tüm derlemelerin yüklemelerini geri alır.</span><span class="sxs-lookup"><span data-stu-id="a9f07-172">Installutil.exe performs installation in a transactional manner; that is, if one of the assemblies fails to install, it rolls back the installations of all other assemblies.</span></span> <span data-ttu-id="a9f07-173">Kaldırma, işlemsel değildir.</span><span class="sxs-lookup"><span data-stu-id="a9f07-173">Uninstall is not transactional.</span></span>

<span data-ttu-id="a9f07-174">Installutil.exe, gecikme imzalı derlemeleri yükleyemez veya kaldıramaz, fakat tanımlayıcı adlı derlemeleri yükleyebilir veya kaldırabilir.</span><span class="sxs-lookup"><span data-stu-id="a9f07-174">Installutil.exe cannot install or uninstall delay-signed assemblies, but it can install or uninstall strong-named assemblies.</span></span>

<span data-ttu-id="a9f07-175">.NET Framework sürüm 2.0 ile başlayarak, ortak dil çalışma zamanının (CLR) 32 bit sürümü Yükleyici aracının yalnızca 32 bit sürümüyle birlikte sevk edilir, fakat CLR'nin 64 bit sürümü Yükleyici aracının hem 32 bit hem de 64 bit sürümleriyle birlikte sevk edilir.</span><span class="sxs-lookup"><span data-stu-id="a9f07-175">Starting with the .NET Framework version 2.0, the 32-bit version of the common language runtime (CLR) ships with only the 32-bit version of the Installer tool, but the 64-bit version of the CLR ships with both 32-bit and 64-bit versions of the Installer tool.</span></span> <span data-ttu-id="a9f07-176">64 bit CLR kullanırken, 32 bit derlemeleri yüklemek için 32 bit Yükleyici aracını, 64 bit ve Microsoft ara dil (MSIL) derlemelerini yüklemek içinse 64 bit Yükleyici aracını kullanın.</span><span class="sxs-lookup"><span data-stu-id="a9f07-176">When using the 64-bit CLR, use the 32-bit Installer tool to install 32-bit assemblies, and the 64-bit Installer tool to install 64-bit and Microsoft intermediate language (MSIL) assemblies.</span></span> <span data-ttu-id="a9f07-177">Yükleyici aracının her iki sürümü de aynı şekilde davranır.</span><span class="sxs-lookup"><span data-stu-id="a9f07-177">Both versions of the Installer tool behave the same.</span></span>

<span data-ttu-id="a9f07-178">Installutil.exe C++ derleyicisi tarafından üretilen gömülü doğal kodu tanıyamayacağından, C++ kullanarak oluşturulan bir Windows hizmetini dağıtmak için Installutil.exe'yi kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="a9f07-178">You cannot use Installutil.exe to deploy a Windows service that was created by using C++, because Installutil.exe cannot recognize the embedded native code that is produced by the C++ compiler.</span></span> <span data-ttu-id="a9f07-179">InstallUtil. exe ile bir C++ Windows hizmeti dağıtmaya çalışırsanız, gibi bir özel durum <xref:System.BadImageFormatException> oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="a9f07-179">If you try to deploy a C++ Windows service with Installutil.exe, an exception such as <xref:System.BadImageFormatException> will be thrown.</span></span> <span data-ttu-id="a9f07-180">Bu senaryoyla çalışmak için, hizmet kodunu bir C++ modülüne taşıyın ve sonra yükleyici nesnesini C# veya Visual Basic'te yazın.</span><span class="sxs-lookup"><span data-stu-id="a9f07-180">To work with this scenario, move the service code to a C++ module, and then write the installer object in C# or Visual Basic.</span></span>

## <a name="examples"></a><span data-ttu-id="a9f07-181">Örnekler</span><span class="sxs-lookup"><span data-stu-id="a9f07-181">Examples</span></span>

<span data-ttu-id="a9f07-182">Aşağıdaki komut, komut sözdiziminin bir açıklamasını ve InstallUtil.exe'ye ilişkin seçenekleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="a9f07-182">The following command displays a description of the command syntax and options for InstallUtil.exe.</span></span>

```console
installutil /?
```

<span data-ttu-id="a9f07-183">Aşağıdaki komut, komut sözdiziminin bir açıklamasını ve InstallUtil.exe'ye ilişkin seçenekleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="a9f07-183">The following command displays a description of the command syntax and options for InstallUtil.exe.</span></span> <span data-ttu-id="a9f07-184">Ayrıca, `myAssembly.exe` <xref:System.Configuration.Install.Installer.HelpText%2A?displayProperty=nameWithType> yükleyicinin özelliğine yardım metni atanmışsa, içindeki yükleyici bileşenleri tarafından desteklenen seçeneklerin bir açıklamasını ve listesini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="a9f07-184">It also displays a description and list of options supported by the installer components in `myAssembly.exe` if help text has been assigned to the installer's <xref:System.Configuration.Install.Installer.HelpText%2A?displayProperty=nameWithType> property.</span></span>

```console
installutil /? myAssembly.exe
```

<span data-ttu-id="a9f07-185">Aşağıdaki komut, derlemede `myAssembly.exe`yükleyici bileşenlerini yürütür.</span><span class="sxs-lookup"><span data-stu-id="a9f07-185">The following command executes the installer components in the assembly `myAssembly.exe`.</span></span>

```console
installutil myAssembly.exe
```

<span data-ttu-id="a9f07-186">Aşağıdaki komut, `/AssemblyName` anahtarı ve tam nitelikli adı kullanarak bir derlemede yükleyici bileşenlerini yürütür.</span><span class="sxs-lookup"><span data-stu-id="a9f07-186">The following command executes the installer components in an assembly by using the `/AssemblyName` switch and a fully qualified name.</span></span>

```console
installutil /AssemblyName "myAssembly, Culture=neutral, PublicKeyToken=0038abc9deabfle5, Version=4.0.0.0"
```

<span data-ttu-id="a9f07-187">Aşağıdaki komut, dosya adıyla belirtilen bir derlemede ve tanımlayıcı adla belirtilen bir derlemede yükleyici bileşenlerini yürütür.</span><span class="sxs-lookup"><span data-stu-id="a9f07-187">The following command executes the installer components in an assembly specified by file name and in an assembly specified by strong name.</span></span> <span data-ttu-id="a9f07-188">`/AssemblyName` Seçenek geçersiz kılınamadığından, dosya adı tarafından belirtilen tüm derlemelerin komut satırında tanımlayıcı ad tarafından belirtilen derlemelerden önce gelmelidir olduğuna unutmayın.</span><span class="sxs-lookup"><span data-stu-id="a9f07-188">Note that all assemblies specified by file name must precede assemblies specified by strong name on the command line, because the `/AssemblyName` option cannot be overridden.</span></span>

```console
installutil myAssembly.exe /AssemblyName "myAssembly, Culture=neutral, PublicKeyToken=0038abc9deabfle5, Version=4.0.0.0"
```

<span data-ttu-id="a9f07-189">Aşağıdaki komut derlemedeki `myAssembly.exe`Uninstaller bileşenlerini yürütür.</span><span class="sxs-lookup"><span data-stu-id="a9f07-189">The following command executes the uninstaller components in the assembly `myAssembly.exe`.</span></span>

```console
installutil /u myAssembly.exe
```

<span data-ttu-id="a9f07-190">Aşağıdaki komut, derlemelerdeki `myAssembly1.exe` ve `myAssembly2.exe`yükleyicideki Uninstaller bileşenlerini yürütür.</span><span class="sxs-lookup"><span data-stu-id="a9f07-190">The following command executes the uninstaller components in the assemblies `myAssembly1.exe` and `myAssembly2.exe`.</span></span>

```console
installutil myAssembly1.exe /u myAssembly2.exe
```

<span data-ttu-id="a9f07-191">`/u` Seçeneğinin komut satırındaki konumu önemli olmadığından, bu, aşağıdaki komuta eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="a9f07-191">Because the position of the `/u` option on the command line is not important, this is equivalent to the following command.</span></span>

```console
installutil /u myAssembly1.exe myAssembly2.exe
```

<span data-ttu-id="a9f07-192">Aşağıdaki komut, derlemede `myAssembly.exe` yükleyicileri yürütür ve ilerleme bilgilerinin `myLog.InstallLog`yazıldığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="a9f07-192">The following command executes the installers in the assembly `myAssembly.exe` and specifies that progress information will be written to `myLog.InstallLog`.</span></span>

```console
installutil /LogFile=myLog.InstallLog myAssembly.exe
```

<span data-ttu-id="a9f07-193">Aşağıdaki komut derlemede `myAssembly.exe`yükleyicileri yürütür, ilerleme bilgilerinin üzerine `myLog.InstallLog`yazılması gerektiğini belirtir ve güncelleştirmelerin sisteme yapılması gerektiğini belirtmek için yükleyicilerin özel `/reg` seçeneğini kullanır defteri.</span><span class="sxs-lookup"><span data-stu-id="a9f07-193">The following command executes the installers in the assembly `myAssembly.exe`, specifies that progress information should be written to `myLog.InstallLog`, and uses the installers' custom `/reg` option to specify that updates should be made to the system registry.</span></span>

```console
installutil /LogFile=myLog.InstallLog /reg=true myAssembly.exe
```

<span data-ttu-id="a9f07-194">Aşağıdaki komut derlemede `myAssembly.exe`yükleyicileri yürütür, kullanıcının e-posta adresini belirtmek için yükleyicinin özel `/email` seçeneğini kullanır ve günlük dosyasına çıktıyı bastırır.</span><span class="sxs-lookup"><span data-stu-id="a9f07-194">The following command executes the installers in the assembly `myAssembly.exe`, uses the installer's custom `/email` option to specify the user's email address, and suppresses output to the log file.</span></span>

```console
installutil /LogFile= /email=admin@mycompany.com myAssembly.exe
```

<span data-ttu-id="a9f07-195">Aşağıdaki komut, `myAssembly.exe` için yükleme ilerleme durumunu `myLog.InstallLog` yazar `myTestAssembly.exe` ve için ilerleme durumunu `myTestLog.InstallLog`yazar.</span><span class="sxs-lookup"><span data-stu-id="a9f07-195">The following command writes the installation progress for `myAssembly.exe` to `myLog.InstallLog` and writes the progress for `myTestAssembly.exe` to `myTestLog.InstallLog`.</span></span>

```console
installutil /LogFile=myLog.InstallLog myAssembly.exe /LogFile=myTestLog.InstallLog myTestAssembly.exe
```

## <a name="see-also"></a><span data-ttu-id="a9f07-196">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a9f07-196">See also</span></span>

- <xref:System.Configuration.Install>
- [<span data-ttu-id="a9f07-197">Araçlar</span><span class="sxs-lookup"><span data-stu-id="a9f07-197">Tools</span></span>](index.md)
- [<span data-ttu-id="a9f07-198">Komut İstemleri</span><span class="sxs-lookup"><span data-stu-id="a9f07-198">Command Prompts</span></span>](developer-command-prompt-for-vs.md)
