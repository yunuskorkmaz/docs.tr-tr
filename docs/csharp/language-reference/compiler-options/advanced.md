---
description: Gelişmiş C# derleyici seçenekleri. Bu seçenekler Gelişmiş senaryolarda kullanılır.
title: C# derleyici seçenekleri-Gelişmiş senaryolar
ms.date: 03/12/2021
f1_keywords:
- cs.build.options
helpviewer_keywords:
- BaseAddress compiler option [C#]
- ChecksumAlgorithm compiler option [C#]
- CodePage compiler option [C#]
- Utf8Output compiler option [C#]
- MainEntryPoint compiler option [C#]
- GenerateFullPaths compiler option [C#]
- FileAlignment compiler option [C#]
- PathMap compiler option [C#]
- PdbFile compiler option [C#]
- ErrorEndLocation compiler option [C#]
- NoStandardLib compiler option [C#]
- PreferredUILang compiler option [C#]
- SubsystemVersion compiler option [C#]
- AdditionalLibPaths compiler option [C#]
- ErrorReport compiler option [C#]
- ApplicationConfiguration compiler option [C#]
- ModuleAssemblyName compiler option [C#]
ms.openlocfilehash: fd65cea6a5524425de5061a2d930181fcd081090
ms.sourcegitcommit: 0bb8074d524e0dcf165430b744bb143461f17026
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2021
ms.locfileid: "103482957"
---
# <a name="advanced-c-compiler-options"></a><span data-ttu-id="e4a57-104">Gelişmiş C# derleyici seçenekleri</span><span class="sxs-lookup"><span data-stu-id="e4a57-104">Advanced C# compiler options</span></span>

<span data-ttu-id="e4a57-105">Aşağıdaki seçenekler gelişmiş senaryoları destekler.</span><span class="sxs-lookup"><span data-stu-id="e4a57-105">The following options support advanced scenarios.</span></span> <span data-ttu-id="e4a57-106">Yeni MSBuild sözdizimi **kalın** olarak gösterilir.</span><span class="sxs-lookup"><span data-stu-id="e4a57-106">The new MSBuild syntax is shown in **Bold**.</span></span> <span data-ttu-id="e4a57-107">Eski `csc.exe` sözdizimi içinde gösterilir `code style` .</span><span class="sxs-lookup"><span data-stu-id="e4a57-107">The older `csc.exe` syntax is shown in `code style`.</span></span>

- <span data-ttu-id="e4a57-108">**MainEntryPoint**, **StartupObject**  /  `-main` : giriş noktasını içeren türü belirtin.</span><span class="sxs-lookup"><span data-stu-id="e4a57-108">**MainEntryPoint**, **StartupObject** / `-main`: Specify the type that contains the entry point.</span></span>
- <span data-ttu-id="e4a57-109">**Pdbdosya**  /  `-pdb` : hata ayıklama bilgi dosyası adını belirtin.</span><span class="sxs-lookup"><span data-stu-id="e4a57-109">**PdbFile** / `-pdb`: Specify debug information file name.</span></span>
- <span data-ttu-id="e4a57-110">**Pathmap**  /  `-pathmap` : derleyici tarafından çıkış kaynak yolu adları için bir eşleme belirtin.</span><span class="sxs-lookup"><span data-stu-id="e4a57-110">**PathMap** / `-pathmap`: Specify a mapping for source path names output by the compiler.</span></span>
- <span data-ttu-id="e4a57-111">**Errorreport**  /  `-errorreport` : iç derleyici hatalarının nasıl işleneceğini belirtin.</span><span class="sxs-lookup"><span data-stu-id="e4a57-111">**ErrorReport** / `-errorreport`: Specify how to handle internal compiler errors.</span></span>
- <span data-ttu-id="e4a57-112">**ApplicationConfiguration**  /  `-appconfig` : derleme bağlama ayarlarını içeren bir uygulama yapılandırma dosyası belirtin.</span><span class="sxs-lookup"><span data-stu-id="e4a57-112">**ApplicationConfiguration** / `-appconfig`: Specify an application configuration file containing assembly binding settings.</span></span>
- <span data-ttu-id="e4a57-113">**Adtionalyobpaths**  /  `-lib` : başvuruların içinde aranacağı ek dizinleri belirtin.</span><span class="sxs-lookup"><span data-stu-id="e4a57-113">**AdditionalLibPaths** / `-lib`: Specify additional directories to search in for references.</span></span>
- <span data-ttu-id="e4a57-114">**GenerateFullPaths**  /  `-fullpath` : Derleyici tam nitelikli yollar oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e4a57-114">**GenerateFullPaths** / `-fullpath`: Compiler generates fully qualified paths.</span></span>
- <span data-ttu-id="e4a57-115">**PreferredUILang**  /  `-preferreduilang` : tercih edilen çıkış dili adını belirtin.</span><span class="sxs-lookup"><span data-stu-id="e4a57-115">**PreferredUILang** / `-preferreduilang`: Specify the preferred output language name.</span></span>
- <span data-ttu-id="e4a57-116">**BaseAddress**  /  `-baseaddress` : oluşturulacak kitaplığın temel adresini belirtin.</span><span class="sxs-lookup"><span data-stu-id="e4a57-116">**BaseAddress** / `-baseaddress`: Specify the base address for the library to be built.</span></span>
- <span data-ttu-id="e4a57-117">**Checksumalgorithm**  /  `-checksumalgorithm` : PDB 'de depolanan kaynak dosyası sağlama toplamını hesaplamak için algoritmayı belirtin.</span><span class="sxs-lookup"><span data-stu-id="e4a57-117">**ChecksumAlgorithm** / `-checksumalgorithm` : Specify algorithm for calculating source file checksum stored in PDB.</span></span>
- <span data-ttu-id="e4a57-118">**Kod sayfası**  /  `-codepage` : kaynak dosyalar açılırken kullanılacak kod sayfasını belirtin.</span><span class="sxs-lookup"><span data-stu-id="e4a57-118">**CodePage** / `-codepage`: Specify the codepage to use when opening source files.</span></span>
- <span data-ttu-id="e4a57-119">**Utf8output**  /  `-utf8output` : Derleyici iletilerini UTF-8 kodlamasında çıktı.</span><span class="sxs-lookup"><span data-stu-id="e4a57-119">**Utf8Output** / `-utf8output`: Output compiler messages in UTF-8 encoding.</span></span>
- <span data-ttu-id="e4a57-120">Dosya **hizalaması**  /  `-filealign` : çıkış dosyası bölümleri için kullanılan hizalamayı belirtin.</span><span class="sxs-lookup"><span data-stu-id="e4a57-120">**FileAlignment** / `-filealign`: Specify the alignment used for output file sections.</span></span>
- <span data-ttu-id="e4a57-121">**Errorendlocation**  /  `-errorendlocation` : her hatanın bitiş konumunun çıkış satırı ve sütunu.</span><span class="sxs-lookup"><span data-stu-id="e4a57-121">**ErrorEndLocation** / `-errorendlocation`: Output line and column of the end location of each error.</span></span>
- <span data-ttu-id="e4a57-122">**NoStandardLib**  /  `-nostdlib` : standart kitaplık *mscorlib.dll* başvurulmayın.</span><span class="sxs-lookup"><span data-stu-id="e4a57-122">**NoStandardLib** / `-nostdlib`: Don't reference standard library *mscorlib.dll*.</span></span>
- <span data-ttu-id="e4a57-123">**Subsystemversion**  /  `-subsystemversion` : Bu derlemenin alt sistem sürümünü belirtin.</span><span class="sxs-lookup"><span data-stu-id="e4a57-123">**SubsystemVersion** / `-subsystemversion`: Specify subsystem version of this assembly.</span></span>
- <span data-ttu-id="e4a57-124">**Moduleassemblyname**  /  `-moduleassemblyname` : Bu modülün bir parçası olacağı derlemenin adı.</span><span class="sxs-lookup"><span data-stu-id="e4a57-124">**ModuleAssemblyName** / `-moduleassemblyname`: Name of the assembly that this module will be a part of.</span></span>

## <a name="mainentrypoint-or-startupobject"></a><span data-ttu-id="e4a57-125">MainEntryPoint veya StartupObject</span><span class="sxs-lookup"><span data-stu-id="e4a57-125">MainEntryPoint or StartupObject</span></span>

<span data-ttu-id="e4a57-126">Bu seçenek, birden fazla sınıf bir yöntemi içeriyorsa programa giriş noktasını içeren sınıfı belirtir `Main` .</span><span class="sxs-lookup"><span data-stu-id="e4a57-126">This option specifies the class that contains the entry point to the program, if more than one class contains a `Main` method.</span></span>

```xml
<StartupObject>MyNamespace.Program</StartupObject>
```

<span data-ttu-id="e4a57-127">veya</span><span class="sxs-lookup"><span data-stu-id="e4a57-127">or</span></span>

```xml
<MainEntryPoint>MyNamespace.Program</MainEntryPoint>
```

<span data-ttu-id="e4a57-128">, `Program` Yöntemini içeren türdür `Main` .</span><span class="sxs-lookup"><span data-stu-id="e4a57-128">Where `Program` is the type that contains the `Main` method.</span></span> <span data-ttu-id="e4a57-129">Belirtilen sınıf adı tam olarak nitelenmiş olmalıdır; sınıfını içeren tam ad alanını ve ardından sınıf adını içermelidir.</span><span class="sxs-lookup"><span data-stu-id="e4a57-129">The provided class name must be fully qualified; it must include the full namespace containing the class, followed by the class name.</span></span> <span data-ttu-id="e4a57-130">Örneğin, `Main` yöntemi `Program` `MyApplication.Core` ad alanındaki sınıfının içindeyse, derleyici seçeneğinin olması gerekir `-main:MyApplication.Core.Program` .</span><span class="sxs-lookup"><span data-stu-id="e4a57-130">For example, when the `Main` method is located inside the `Program` class in the `MyApplication.Core` namespace, the compiler option has to be `-main:MyApplication.Core.Program`.</span></span> <span data-ttu-id="e4a57-131">Derlemeniz bir yöntemi olan birden çok tür içeriyorsa [`Main`](../../programming-guide/main-and-command-args/index.md) , hangi türün yöntemi içerdiğini belirtebilirsiniz `Main` .</span><span class="sxs-lookup"><span data-stu-id="e4a57-131">If your compilation includes more than one type with a [`Main`](../../programming-guide/main-and-command-args/index.md) method, you can specify which type contains the `Main` method.</span></span>

> [!NOTE]
> <span data-ttu-id="e4a57-132">Bu seçenek, bu proje bir veya daha fazla yöntem içerse bile, [en üst düzey deyimler](../../programming-guide/main-and-command-args/top-level-statements.md)içeren bir proje için kullanılamaz `Main` .</span><span class="sxs-lookup"><span data-stu-id="e4a57-132">This option can't be used for a project that includes [top-level statements](../../programming-guide/main-and-command-args/top-level-statements.md), even if that project contains one or more `Main` methods.</span></span>

## <a name="pdbfile"></a><span data-ttu-id="e4a57-133">Pdbdosya</span><span class="sxs-lookup"><span data-stu-id="e4a57-133">PdbFile</span></span>

<span data-ttu-id="e4a57-134">**Pdbdosya** derleyici seçeneği, hata ayıklama sembolleri dosyasının adını ve konumunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="e4a57-134">The **PdbFile** compiler option specifies the name and location of the debug symbols file.</span></span>  <span data-ttu-id="e4a57-135">`filename`Değer, hata ayıklama sembolleri dosyasının adını ve konumunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="e4a57-135">The `filename` value specifies the name and location of the debug symbols file.</span></span>  

```xml
<PdbFile>filename</PdbFile>
```

<span data-ttu-id="e4a57-136">[**DEBUGTYPE**](code-generation.md#debugtype)belirttiğinizde, derleyici aynı dizinde bir *. pdb* dosyası oluşturur ve bu dosya derleyicinin çıkış dosyasını (. exe veya. dll) oluşturacaktır.</span><span class="sxs-lookup"><span data-stu-id="e4a57-136">When you specify [**DebugType**](code-generation.md#debugtype), the compiler will create a *.pdb* file in the same directory where the compiler will create the output file (.exe or .dll).</span></span> <span data-ttu-id="e4a57-137">*. Pdb* dosyası, çıkış dosyasının adı ile aynı temel dosya adına sahiptir.</span><span class="sxs-lookup"><span data-stu-id="e4a57-137">The *.pdb* file has the same base file name as the name of the output file.</span></span> <span data-ttu-id="e4a57-138">**Pdbdosya** ,. pdb dosyası için varsayılan olmayan bir dosya adı ve konum belirtmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="e4a57-138">**PdbFile** allows you to specify a non-default file name and location for the .pdb file.</span></span> <span data-ttu-id="e4a57-139">Bu derleyici seçeneği Visual Studio geliştirme ortamında ayarlanamaz veya program aracılığıyla değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="e4a57-139">This compiler option cannot be set in the Visual Studio development environment, nor can it be changed programmatically.</span></span>  

## <a name="pathmap"></a><span data-ttu-id="e4a57-140">PathMap</span><span class="sxs-lookup"><span data-stu-id="e4a57-140">PathMap</span></span>

<span data-ttu-id="e4a57-141">**Pathmap** derleyici seçeneği, fiziksel yolların derleyicinin çıkış kaynak yol adlarına nasıl eşlendiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="e4a57-141">The **PathMap** compiler option specifies how to map physical paths to source path names output by the compiler.</span></span> <span data-ttu-id="e4a57-142">Bu seçenek, derleyicinin çalıştığı makinedeki her fiziksel yolu, çıktı dosyalarında yazılması gereken karşılık gelen bir yola eşler.</span><span class="sxs-lookup"><span data-stu-id="e4a57-142">This option maps each physical path on the machine where the compiler runs to a corresponding path that should be written in the output files.</span></span> <span data-ttu-id="e4a57-143">Aşağıdaki örnekte, `path1` geçerli ortamdaki kaynak dosyalarının tam yoludur ve `sourcePath1` `path1` herhangi bir çıkış dosyasında yerine kaynak yol kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e4a57-143">In the following example, `path1` is the full path to the source files in the current environment, and `sourcePath1` is the source path substituted for `path1` in any output files.</span></span> <span data-ttu-id="e4a57-144">Birden çok eşlenmiş kaynak yolunu belirtmek için, her biri noktalı virgülle ayırın.</span><span class="sxs-lookup"><span data-stu-id="e4a57-144">To specify multiple mapped source paths, separate each with a semicolon.</span></span>

```xml
<PathMap>path1=sourcePath1;path2=sourcePath2</PathMap>
```

<span data-ttu-id="e4a57-145">Derleyici, kaynak yolunu aşağıdaki nedenlerden dolayı çıktısına yazar:</span><span class="sxs-lookup"><span data-stu-id="e4a57-145">The compiler writes the source path into its output for the following reasons:</span></span>

1. <span data-ttu-id="e4a57-146">İsteğe bağlı bir parametreye uygulandığında kaynak yolu bir bağımsız değişken için değiştirilir <xref:System.Runtime.CompilerServices.CallerFilePathAttribute> .</span><span class="sxs-lookup"><span data-stu-id="e4a57-146">The source path is substituted for an argument when the <xref:System.Runtime.CompilerServices.CallerFilePathAttribute> is applied to an optional parameter.</span></span>
1. <span data-ttu-id="e4a57-147">Kaynak yolu bir PDB dosyasına katıştırılır.</span><span class="sxs-lookup"><span data-stu-id="e4a57-147">The source path is embedded in a PDB file.</span></span>
1. <span data-ttu-id="e4a57-148">PDB dosyasının yolu bir PE (taşınabilir yürütülebilir) dosyasına katıştırılır.</span><span class="sxs-lookup"><span data-stu-id="e4a57-148">The path of the PDB file is embedded into a PE (portable executable) file.</span></span>

## <a name="errorreport"></a><span data-ttu-id="e4a57-149">ErrorReport</span><span class="sxs-lookup"><span data-stu-id="e4a57-149">ErrorReport</span></span>

<span data-ttu-id="e4a57-150">Bu seçenek, C# iç derleyici hatasını Microsoft 'a bildirmenin kolay bir yolunu sağlar.</span><span class="sxs-lookup"><span data-stu-id="e4a57-150">This option provides a convenient way to report a C# internal compiler error to Microsoft.</span></span>

> [!NOTE]
> <span data-ttu-id="e4a57-151">Windows Vista ve Windows Server 2008 ' de, Visual Studio için yaptığınız hata raporlama ayarları Windows Hata Bildirimi (WER) ile yapılan ayarları geçersiz kılmaz.</span><span class="sxs-lookup"><span data-stu-id="e4a57-151">On Windows Vista and Windows Server 2008, the error reporting settings that you make for Visual Studio do not override the settings made through Windows Error Reporting (WER).</span></span> <span data-ttu-id="e4a57-152">WER ayarları her zaman Visual Studio hata raporlama ayarlarından önceliklidir.</span><span class="sxs-lookup"><span data-stu-id="e4a57-152">WER settings always take precedence over Visual Studio error reporting settings.</span></span>

```xml
<ErrorReport>setting</ErrorReport>
```

<span data-ttu-id="e4a57-153">Bağımsız değişkeni şunlardan biri olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="e4a57-153">The argument must be one of:</span></span>

- <span data-ttu-id="e4a57-154">**hiçbiri**: iç derleyici hataları hakkında raporlar toplanmayacak veya Microsoft 'a gönderilmez.</span><span class="sxs-lookup"><span data-stu-id="e4a57-154">**none**: Reports about internal compiler errors won't be collected or sent to Microsoft.</span></span>
- <span data-ttu-id="e4a57-155">**istem**: iç derleyici hatası aldığınızda rapor göndermenizi ister.</span><span class="sxs-lookup"><span data-stu-id="e4a57-155">**prompt**: Prompts you to send a report when you receive an internal compiler error.</span></span> <span data-ttu-id="e4a57-156">geliştirme ortamında bir uygulama derlerken varsayılan değer, **istem** varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="e4a57-156">**prompt** is the default when you compile an application in the development environment.</span></span>
- <span data-ttu-id="e4a57-157">**kuyruk**: hata raporunu sıralar.</span><span class="sxs-lookup"><span data-stu-id="e4a57-157">**queue**: Queues the error report.</span></span> <span data-ttu-id="e4a57-158">Yönetici kimlik bilgileriyle oturum açtığınızda, son oturum açtığınız zamandan bu yana tüm sorunları bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e4a57-158">When you sign in with administrative credentials, you can report any failures since the last time that you were logged on.</span></span> <span data-ttu-id="e4a57-159">Her üç günde birden çok kez rapor göndermeniz istenmez.</span><span class="sxs-lookup"><span data-stu-id="e4a57-159">You won't be prompted to send reports for failures more than once every three days.</span></span> <span data-ttu-id="e4a57-160">komut satırında bir uygulama derlerken varsayılan **kuyruk** varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="e4a57-160">**queue** is the default when you compile an application at the command line.</span></span>
- <span data-ttu-id="e4a57-161">**Send**: iç derleyici hatalarının raporlarını otomatik olarak Microsoft 'a gönderir.</span><span class="sxs-lookup"><span data-stu-id="e4a57-161">**send**: Automatically sends reports of internal compiler errors to Microsoft.</span></span> <span data-ttu-id="e4a57-162">Bu seçeneği etkinleştirmek için öncelikle Microsoft veri toplama ilkesini kabul etmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="e4a57-162">To enable this option, you must first agree to the Microsoft data collection policy.</span></span> <span data-ttu-id="e4a57-163">Bir bilgisayarda ilk kez belirttiğinizde `<ErrorReport>send</ErrorReport>` , bir derleyici iletisi sizi Microsoft veri toplama ilkesini içeren bir Web sitesine başvuracaktır.</span><span class="sxs-lookup"><span data-stu-id="e4a57-163">The first time that you specify `<ErrorReport>send</ErrorReport>` on a computer, a compiler message will refer you to a Web site that contains the Microsoft data collection policy.</span></span>

<span data-ttu-id="e4a57-164">Derleyici bir kaynak kodu dosyasını işleyeişce bir iç derleyici hatası (ıCE) oluşur.</span><span class="sxs-lookup"><span data-stu-id="e4a57-164">An internal compiler error (ICE) results when the compiler can't process a source code file.</span></span> <span data-ttu-id="e4a57-165">Bir buz gerçekleştiğinde, derleyici bir çıkış dosyası ya da kodunuzu onarmak için kullanabileceğiniz yararlı bir tanılama üretmez.</span><span class="sxs-lookup"><span data-stu-id="e4a57-165">When an ICE occurs, the compiler doesn't produce an output file or any useful diagnostic that you can use to fix your code.</span></span>

<span data-ttu-id="e4a57-166">**Errorreport**'U kullanarak C# EKIBINE Ice bilgileri sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e4a57-166">By using **ErrorReport**, you can provide ICE information to the C# team.</span></span> <span data-ttu-id="e4a57-167">Hata raporlarınız, gelecekteki derleyici sürümlerinin artırılmasına yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="e4a57-167">Your error reports can help improve future compiler releases.</span></span> <span data-ttu-id="e4a57-168">Kullanıcının raporları gönderebilme özelliği bilgisayar ve Kullanıcı ilkesi izinlerine bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="e4a57-168">A user's ability to send reports depends on computer and user policy permissions.</span></span>

## <a name="applicationconfiguration"></a><span data-ttu-id="e4a57-169">ApplicationConfiguration</span><span class="sxs-lookup"><span data-stu-id="e4a57-169">ApplicationConfiguration</span></span>

<span data-ttu-id="e4a57-170">**ApplicationConfiguration** derleyici seçeneği, bir C# uygulamasının derleme bağlama süresinde ortak dil çalışma zamanına (CLR) bir derlemenin uygulama yapılandırma (app.config) dosyasının konumunu belirtmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="e4a57-170">The **ApplicationConfiguration** compiler option enables a C# application to specify the location of an assembly's application configuration (app.config) file to the common language runtime (CLR) at assembly binding time.</span></span>

```xml
<ApplicationConfiguration>file</ApplicationConfiguration>
```

<span data-ttu-id="e4a57-171">`file`, Derleme bağlama ayarlarını içeren uygulama yapılandırma dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="e4a57-171">Where `file` is the application configuration file that contains assembly binding settings.</span></span> <span data-ttu-id="e4a57-172">**ApplicationConfiguration** 'ın bir kullanımı, bir derlemenin hem .NET Framework sürümüne hem de aynı anda belirli bir başvuru derlemesinin Silverlight sürümüne .NET Framework başvurması gereken gelişmiş senaryolardır.</span><span class="sxs-lookup"><span data-stu-id="e4a57-172">One use of **ApplicationConfiguration** is advanced scenarios in which an assembly has to reference both the .NET Framework version and the .NET Framework for Silverlight version of a particular reference assembly at the same time.</span></span> <span data-ttu-id="e4a57-173">Örneğin, Windows Presentation Foundation (WPF) içinde yazılmış bir XAML tasarımcısının, tasarımcı 'nın Kullanıcı arabirimi için hem WPF masaüstüne hem de Silverlight 'ın içerdiği WPF 'nin alt kümesine başvurması gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="e4a57-173">For example, a XAML designer written in Windows Presentation Foundation (WPF) might have to reference both the WPF Desktop, for the designer's user interface, and the subset of WPF that is included with Silverlight.</span></span> <span data-ttu-id="e4a57-174">Aynı tasarımcı derlemesinin her iki derlemeye de erişimi vardır.</span><span class="sxs-lookup"><span data-stu-id="e4a57-174">The same designer assembly has to access both assemblies.</span></span> <span data-ttu-id="e4a57-175">Varsayılan olarak, derleme bağlaması iki derlemeyi eşdeğer olarak gördüğü için ayrı başvurular bir derleyici hatasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="e4a57-175">By default, the separate references cause a compiler error, because assembly binding sees the two assemblies as equivalent.</span></span> <span data-ttu-id="e4a57-176">**ApplicationConfiguration** derleyici seçeneği `<supportPortability>` , aşağıdaki örnekte gösterildiği gibi bir etiketi kullanarak varsayılan davranışı devre dışı bırakan bir app.config dosyasının konumunu belirtmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="e4a57-176">The **ApplicationConfiguration** compiler option enables you to specify the location of an app.config file that disables the default behavior by using a `<supportPortability>` tag, as shown in the following example.</span></span>

```xml
<supportPortability PKT="7cec85d7bea7798e" enable="false"/>
```

<span data-ttu-id="e4a57-177">Derleyici, dosyanın konumunu CLR 'nin derleme bağlama mantığına geçirir.</span><span class="sxs-lookup"><span data-stu-id="e4a57-177">The compiler passes the location of the file to the CLR's assembly-binding logic.</span></span>

> [!NOTE]
> <span data-ttu-id="e4a57-178">Projede zaten ayarlanmış olan app.config dosyasını kullanmak için, `<UseAppConfigForCompiler>` *. csproj* dosyasına özellik etiketi ekleyin ve değerini olarak ayarlayın `true` .</span><span class="sxs-lookup"><span data-stu-id="e4a57-178">To use the app.config file that is already set in the project, add property tag `<UseAppConfigForCompiler>` to the *.csproj* file and set its value to `true`.</span></span> <span data-ttu-id="e4a57-179">Farklı bir app.config dosyası belirtmek için, özellik etiketi ekleyin `<AppConfigForCompiler>` ve değerini dosyanın konumuna ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="e4a57-179">To specify a different app.config file, add property tag `<AppConfigForCompiler>` and set its value to the location of the file.</span></span>

<span data-ttu-id="e4a57-180">Aşağıdaki örnek, bir uygulamanın hem .NET Framework .NET Framework uygulamasına hem de her iki uygulamada bulunan herhangi bir .NET Framework derlemesinin Silverlight uygulamasına yönelik başvurularına sahip olmasını sağlayan bir app.config dosyası gösterir.</span><span class="sxs-lookup"><span data-stu-id="e4a57-180">The following example shows an app.config file that enables an application to have references to both the .NET Framework implementation and the .NET Framework for Silverlight implementation of any .NET Framework assembly that exists in both implementations.</span></span> <span data-ttu-id="e4a57-181">**ApplicationConfiguration** derleyici seçeneği bu app.config dosyasının konumunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="e4a57-181">The **ApplicationConfiguration** compiler option specifies the location of this app.config file.</span></span>

```xml
<configuration>
  <runtime>
    <assemblyBinding>
      <supportPortability PKT="7cec85d7bea7798e" enable="false"/>
      <supportPortability PKT="31bf3856ad364e35" enable="false"/>
    </assemblyBinding>
  </runtime>
</configuration>
```

## <a name="additionallibpaths"></a><span data-ttu-id="e4a57-182">Adtiontalbpaths</span><span class="sxs-lookup"><span data-stu-id="e4a57-182">AdditionalLibPaths</span></span>

<span data-ttu-id="e4a57-183">**Additionalbıpaths** seçeneği, [**Başvurular**](inputs.md#references) seçeneğiyle başvurulan derlemelerin konumunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="e4a57-183">The **AdditionalLibPaths** option specifies the location of assemblies referenced with the [**References**](inputs.md#references) option.</span></span>

```xml
<AdditionalLibPaths>dir1[,dir2]</AdditionalLibPaths>
```

<span data-ttu-id="e4a57-184">, `dir1` Başvurulan bir derlemenin geçerli çalışma dizininde (derleyicisini çağırmakta olduğunuz dizin) veya ortak dil çalışma zamanının sistem dizininde bulunamaması durumunda, derleyicinin bakacağı bir dizindir.</span><span class="sxs-lookup"><span data-stu-id="e4a57-184">Where `dir1` is a directory for the compiler to look in if a referenced assembly isn't found in the current working directory (the directory from which you're invoking the compiler) or in the common language runtime's system directory.</span></span> <span data-ttu-id="e4a57-185">`dir2` , derleme başvuruları için içinde arama yapılacak bir veya daha fazla dizin.</span><span class="sxs-lookup"><span data-stu-id="e4a57-185">`dir2` is one or more additional directories to search in for assembly references.</span></span> <span data-ttu-id="e4a57-186">Dizin adlarını virgülle ve aralarında boşluk olmadan ayırın.</span><span class="sxs-lookup"><span data-stu-id="e4a57-186">Separate directory names with a comma, and without white space between them.</span></span> <span data-ttu-id="e4a57-187">Derleyici, aşağıdaki sırayla tam olmayan derleme başvurularını arar:</span><span class="sxs-lookup"><span data-stu-id="e4a57-187">The compiler searches for assembly references that aren't fully qualified in the following order:</span></span>  

1. <span data-ttu-id="e4a57-188">Geçerli çalışma dizini.</span><span class="sxs-lookup"><span data-stu-id="e4a57-188">Current working directory.</span></span>
1. <span data-ttu-id="e4a57-189">Ortak dil çalışma zamanı sistem dizini.</span><span class="sxs-lookup"><span data-stu-id="e4a57-189">The common language runtime system directory.</span></span>
1. <span data-ttu-id="e4a57-190">**Additionalbpaths** tarafından belirtilen dizinler.</span><span class="sxs-lookup"><span data-stu-id="e4a57-190">Directories specified by **AdditionalLibPaths**.</span></span>
1. <span data-ttu-id="e4a57-191">LıB ortam değişkeni tarafından belirtilen dizinler.</span><span class="sxs-lookup"><span data-stu-id="e4a57-191">Directories specified by the LIB environment variable.</span></span>

<span data-ttu-id="e4a57-192">Derleme başvurusunu belirtmek için **başvuruyu** kullanın.</span><span class="sxs-lookup"><span data-stu-id="e4a57-192">Use **Reference** to specify an assembly reference.</span></span> <span data-ttu-id="e4a57-193">**Adtiontalbpaths** eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="e4a57-193">**AdditionalLibPaths** is additive.</span></span> <span data-ttu-id="e4a57-194">Bir defadan fazla belirtmek önceki değerlere ekler.</span><span class="sxs-lookup"><span data-stu-id="e4a57-194">Specifying it more than once appends to any prior values.</span></span> <span data-ttu-id="e4a57-195">Bağımlı derlemenin yolu derleme bildiriminde belirtilmediğinden, uygulama derlemeyi genel derleme önbelleğinde bulur ve kullanır.</span><span class="sxs-lookup"><span data-stu-id="e4a57-195">Since the path to the dependent assembly isn't specified in the assembly manifest, the application will find and use the assembly in the global assembly cache.</span></span> <span data-ttu-id="e4a57-196">Derlemeye başvuran derleyici, ortak dil çalışma zamanının derlemeyi çalışma zamanında bulabileceği ve yükleyemediğini göstermez.</span><span class="sxs-lookup"><span data-stu-id="e4a57-196">The compiler referencing the assembly doesn't imply the common language runtime can find and load the assembly at runtime.</span></span> <span data-ttu-id="e4a57-197">Çalışma zamanının başvurulmuş derlemeleri nasıl arayacağını görmek için bkz. [çalışma zamanının derlemeleri nasıl konumlandırır](../../../framework/deployment/how-the-runtime-locates-assemblies.md) .</span><span class="sxs-lookup"><span data-stu-id="e4a57-197">See [How the Runtime Locates Assemblies](../../../framework/deployment/how-the-runtime-locates-assemblies.md) for details on how the runtime searches for referenced assemblies.</span></span>  

## <a name="generatefullpaths"></a><span data-ttu-id="e4a57-198">GenerateFullPaths</span><span class="sxs-lookup"><span data-stu-id="e4a57-198">GenerateFullPaths</span></span>

<span data-ttu-id="e4a57-199">**GenerateFullPaths** seçeneği derleyicinin derleme hatalarını ve uyarılarını listelerken dosyanın tam yolunu belirtmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="e4a57-199">The **GenerateFullPaths** option causes the compiler to specify the full path to the file when listing compilation errors and warnings.</span></span>
  
```Xml
<GenerateFullPaths>true</GenerateFullPaths>
```

<span data-ttu-id="e4a57-200">Varsayılan olarak, derlemeden kaynaklanan hatalar ve uyarılar, bir hatanın bulunduğu dosyanın adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="e4a57-200">By default, errors and warnings that result from compilation specify the name of the file in which an error was found.</span></span> <span data-ttu-id="e4a57-201">**GenerateFullPaths** seçeneği derleyicinin dosyanın tam yolunu belirtmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="e4a57-201">The **GenerateFullPaths** option causes the compiler to specify the full path to the file.</span></span> <span data-ttu-id="e4a57-202">Bu derleyici seçeneği Visual Studio 'da kullanılamaz ve program aracılığıyla değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="e4a57-202">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>

## <a name="preferreduilang"></a><span data-ttu-id="e4a57-203">PreferredUILang</span><span class="sxs-lookup"><span data-stu-id="e4a57-203">PreferredUILang</span></span>

<span data-ttu-id="e4a57-204">**PreferredUILang** derleyici seçeneğini kullanarak, C# derleyicisinin hata iletileri gibi çıktıyı görüntülediği dili belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e4a57-204">By using the **PreferredUILang** compiler option, you can specify the language in which the C# compiler displays output, such as error messages.</span></span>

```xml
<PreferredUILang>language</PreferredUILang>
```

<span data-ttu-id="e4a57-205">Burada `language` , Derleyici çıktısı için kullanılacak dilin [dil adıdır](/windows/desktop/Intl/language-names) .</span><span class="sxs-lookup"><span data-stu-id="e4a57-205">Where `language` is the [language name](/windows/desktop/Intl/language-names) of the language to use for compiler output.</span></span> <span data-ttu-id="e4a57-206">C# derleyicisinin hata iletileri ve diğer komut satırı çıktıları için kullanmasını istediğiniz dili belirtmek için **PreferredUILang** derleyici seçeneğini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e4a57-206">You can use the **PreferredUILang** compiler option to specify the language that you want the C# compiler to use for error messages and other command-line output.</span></span> <span data-ttu-id="e4a57-207">Dile ait dil paketi yüklü değilse, bunun yerine işletim sisteminin dil ayarı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e4a57-207">If the language pack for the language isn't installed, the language setting of the operating system is used instead.</span></span>

## <a name="baseaddress"></a><span data-ttu-id="e4a57-208">BaseAddress</span><span class="sxs-lookup"><span data-stu-id="e4a57-208">BaseAddress</span></span>

<span data-ttu-id="e4a57-209">**BaseAddress** SEÇENEĞI, dll 'nin yükleneceği tercih edilen temel adresi belirtmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="e4a57-209">The **BaseAddress** option lets you specify the preferred base address at which to load a DLL.</span></span> <span data-ttu-id="e4a57-210">Bu seçeneğin ne zaman ve neden kullanıldığı hakkında daha fazla bilgi için bkz. [Larry Osterman 'ın Web günlüğü](/archive/blogs/larryosterman/why-should-i-even-bother-to-use-dlls-in-my-system).</span><span class="sxs-lookup"><span data-stu-id="e4a57-210">For more information about when and why to use this option, see [Larry Osterman's WebLog](/archive/blogs/larryosterman/why-should-i-even-bother-to-use-dlls-in-my-system).</span></span>

```xml
<BaseAddress>address</BaseAddress>
```

<span data-ttu-id="e4a57-211">`address`, Dll 'nin temel adresidir.</span><span class="sxs-lookup"><span data-stu-id="e4a57-211">Where `address` is the base address for the DLL.</span></span> <span data-ttu-id="e4a57-212">Bu adres ondalık, onaltılık veya sekizlik sayı olarak belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="e4a57-212">This address can be specified as a decimal, hexadecimal, or octal number.</span></span> <span data-ttu-id="e4a57-213">Bir DLL için varsayılan temel adres, .NET ortak dil çalışma zamanı tarafından ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="e4a57-213">The default base address for a DLL is set by the .NET common language runtime.</span></span> <span data-ttu-id="e4a57-214">Bu adresteki alt sıralama sözcüğü yuvarlanır.</span><span class="sxs-lookup"><span data-stu-id="e4a57-214">The lower-order word in this address will be rounded.</span></span> <span data-ttu-id="e4a57-215">Örneğin, öğesini belirtirseniz `0x11110001` , ' ye yuvarlanacaktır `0x11110000` .</span><span class="sxs-lookup"><span data-stu-id="e4a57-215">For example, if you specify `0x11110001`, it will be rounded to `0x11110000`.</span></span> <span data-ttu-id="e4a57-216">DLL imzalama işlemini gerçekleştirmek için,-R seçeneğiyle SN.EXE kullanın.</span><span class="sxs-lookup"><span data-stu-id="e4a57-216">To complete the signing process for a DLL, use SN.EXE with the -R option.</span></span>

## <a name="checksumalgorithm"></a><span data-ttu-id="e4a57-217">ChecksumAlgorithm</span><span class="sxs-lookup"><span data-stu-id="e4a57-217">ChecksumAlgorithm</span></span>

<span data-ttu-id="e4a57-218">Bu seçenek, PDB 'deki kaynak dosyalarını kodlamak için kullandığımız sağlama toplamı algoritmasını denetler.</span><span class="sxs-lookup"><span data-stu-id="e4a57-218">This option controls the checksum algorithm we use to encode source files in the PDB.</span></span>

```xml
<ChecksumAlgorithm>algorithm</ChecksumAlgorithm>
```

<span data-ttu-id="e4a57-219">`algorithm` `SHA1` (Varsayılan) ya da olmalıdır `SHA256` .</span><span class="sxs-lookup"><span data-stu-id="e4a57-219">The `algorithm` must be either `SHA1` (default) or `SHA256`.</span></span>

## <a name="codepage"></a><span data-ttu-id="e4a57-220">Sayfasının</span><span class="sxs-lookup"><span data-stu-id="e4a57-220">CodePage</span></span>

<span data-ttu-id="e4a57-221">Bu seçenek, gerekli sayfa sistem için geçerli varsayılan kod sayfası değilse, derleme sırasında kullanılacak kod sayfasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="e4a57-221">This option specifies which codepage to use during compilation if the required page isn't the current default codepage for the system.</span></span>
  
```xml
<CodePage>id</CodePage>
```

<span data-ttu-id="e4a57-222">, `id` Derlemedeki tüm kaynak kodu dosyaları için kullanılacak kod sayfasının kimliğidir.</span><span class="sxs-lookup"><span data-stu-id="e4a57-222">Where `id` is the id of the code page to use for all source code files in the compilation.</span></span> <span data-ttu-id="e4a57-223">Derleyici önce tüm kaynak dosyalarını UTF-8 olarak yorumlamaya çalışacaktır.</span><span class="sxs-lookup"><span data-stu-id="e4a57-223">The compiler will first attempt to interpret all source files as UTF-8.</span></span> <span data-ttu-id="e4a57-224">Kaynak kodu dosyalarınız UTF-8 dışındaki bir kodlamadeyse ve 7 bit ASCII karakterlerden farklı karakterler kullanıyorsa, hangi kod sayfasının kullanılacağını belirtmek için **kod** sayfası seçeneğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="e4a57-224">If your source code files are in an encoding other than UTF-8 and use characters other than 7-bit ASCII characters, use the **CodePage** option to specify which code page should be used.</span></span> <span data-ttu-id="e4a57-225">**Kod sayfası** , derinizdeki tüm kaynak kodu dosyaları için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="e4a57-225">**CodePage** applies to all source code files in your compilation.</span></span> <span data-ttu-id="e4a57-226">Sisteminizde hangi kod sayfalarının desteklendiğini bulma hakkında bilgi için bkz. [Getcpınfo](/windows/desktop/api/winnls/nf-winnls-getcpinfo) .</span><span class="sxs-lookup"><span data-stu-id="e4a57-226">See [GetCPInfo](/windows/desktop/api/winnls/nf-winnls-getcpinfo) for information on how to find which code pages are supported on your system.</span></span>

## <a name="utf8output"></a><span data-ttu-id="e4a57-227">Utf8Output</span><span class="sxs-lookup"><span data-stu-id="e4a57-227">Utf8Output</span></span>

<span data-ttu-id="e4a57-228">**Utf8output** seçeneği, DERLEYICI çıkışını utf-8 kodlaması kullanarak görüntüler.</span><span class="sxs-lookup"><span data-stu-id="e4a57-228">The **Utf8Output** option displays compiler output using UTF-8 encoding.</span></span>

```xml
<Utf8Output>true</Utf8Output>
```

<span data-ttu-id="e4a57-229">Bazı uluslararası yapılandırmalarda, Derleyici çıktısı konsolunda doğru şekilde görüntülenemez.</span><span class="sxs-lookup"><span data-stu-id="e4a57-229">In some international configurations, compiler output cannot correctly be displayed in the console.</span></span> <span data-ttu-id="e4a57-230">**Utf8output** kullanın ve derleyici çıkışını bir dosyaya yeniden yönlendirin.</span><span class="sxs-lookup"><span data-stu-id="e4a57-230">Use **Utf8Output** and redirect compiler output to a file.</span></span>

## <a name="filealignment"></a><span data-ttu-id="e4a57-231">Dosya hizalaması</span><span class="sxs-lookup"><span data-stu-id="e4a57-231">FileAlignment</span></span>

<span data-ttu-id="e4a57-232">**Filehizalaması** seçeneği, çıkış dosyanızdaki bölümlerin boyutunu belirtmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="e4a57-232">The **FileAlignment** option lets you specify the size of sections in your output file.</span></span> <span data-ttu-id="e4a57-233">Geçerli değerler 512, 1024, 2048, 4096 ve 8192.</span><span class="sxs-lookup"><span data-stu-id="e4a57-233">Valid values are 512, 1024, 2048, 4096, and 8192.</span></span> <span data-ttu-id="e4a57-234">Bu değerler baytlardır.</span><span class="sxs-lookup"><span data-stu-id="e4a57-234">These values are in bytes.</span></span>

```xml
<FileAlignment>number</FileAlignment>
```

<span data-ttu-id="e4a57-235">Visual Studio 'da projeniz için **derleme** özelliklerinin **Gelişmiş** sayfasından **filehizalaması** seçeneğini ayarlarsınız.</span><span class="sxs-lookup"><span data-stu-id="e4a57-235">You set the **FileAlignment** option from the **Advanced** page of the **Build** properties for your project in Visual Studio.</span></span> <span data-ttu-id="e4a57-236">Her bölüm, **Filehizalaması** değerinin katı olan bir sınıra göre hizalanacaktır.</span><span class="sxs-lookup"><span data-stu-id="e4a57-236">Each section will be aligned on a boundary that is a multiple of the **FileAlignment** value.</span></span> <span data-ttu-id="e4a57-237">Sabit bir varsayılan yoktur.</span><span class="sxs-lookup"><span data-stu-id="e4a57-237">There's no fixed default.</span></span> <span data-ttu-id="e4a57-238">**Dosya hizalama** belirtilmezse, ortak dil çalışma zamanı derleme zamanında bir varsayılan değer seçer.</span><span class="sxs-lookup"><span data-stu-id="e4a57-238">If **FileAlignment** isn't specified, the common language runtime picks a default at compile time.</span></span> <span data-ttu-id="e4a57-239">Bölüm boyutunu belirterek, çıkış dosyasının boyutunu etkilersiniz.</span><span class="sxs-lookup"><span data-stu-id="e4a57-239">By specifying the section size, you affect the size of the output file.</span></span> <span data-ttu-id="e4a57-240">Bölüm boyutunu değiştirmek, daha küçük cihazlarda çalıştırılacak programlar için yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="e4a57-240">Modifying section size may be useful for programs that will run on smaller devices.</span></span> <span data-ttu-id="e4a57-241">Çıkış dosyanızdaki bölümler hakkındaki bilgileri görmek için [dumpbin](/cpp/build/reference/dumpbin-options) ' i kullanın.</span><span class="sxs-lookup"><span data-stu-id="e4a57-241">Use [DUMPBIN](/cpp/build/reference/dumpbin-options) to see information about sections in your output file.</span></span>

## <a name="errorendlocation"></a><span data-ttu-id="e4a57-242">ErrorEndLocation</span><span class="sxs-lookup"><span data-stu-id="e4a57-242">ErrorEndLocation</span></span>

<span data-ttu-id="e4a57-243">Derleyiciye her hatanın bitiş konumunun satırını ve sütununu çıktı olarak bildirir.</span><span class="sxs-lookup"><span data-stu-id="e4a57-243">Instructs the compiler to output line and column of the end location of each error.</span></span>

```xml
<ErrorEndLocation>filename</ErrorEndLocation>
```

<span data-ttu-id="e4a57-244">Varsayılan olarak, derleyici tüm hatalar ve uyarılar için kaynaktaki başlangıç konumunu yazar.</span><span class="sxs-lookup"><span data-stu-id="e4a57-244">By default, the compiler writes the starting location in source for all errors and warnings.</span></span> <span data-ttu-id="e4a57-245">Bu seçenek true olarak ayarlandığında, derleyici her bir hata ve uyarı için hem başlangıç hem de bitiş konumunu yazar.</span><span class="sxs-lookup"><span data-stu-id="e4a57-245">When this option is set to true, the compiler writes both the starting and end location for each error and warning.</span></span>

## <a name="nostandardlib"></a><span data-ttu-id="e4a57-246">NoStandardLib</span><span class="sxs-lookup"><span data-stu-id="e4a57-246">NoStandardLib</span></span>

<span data-ttu-id="e4a57-247">**NoStandardLib** , tüm sistem ad alanını tanımlayan mscorlib.dll içeri aktarmayı engeller.</span><span class="sxs-lookup"><span data-stu-id="e4a57-247">**NoStandardLib** prevents the import of mscorlib.dll, which defines the entire System namespace.</span></span>

```xml
<NoStandardLib>true</NoStandardLib>
```

<span data-ttu-id="e4a57-248">Kendi sistem ad alanınızı ve nesnelerinizi tanımlamak veya oluşturmak istiyorsanız bu seçeneği kullanın.</span><span class="sxs-lookup"><span data-stu-id="e4a57-248">Use this option if you want to define or create your own System namespace and objects.</span></span> <span data-ttu-id="e4a57-249">**NoStandardLib** belirtmezseniz, mscorlib.dll programınıza içeri aktarılır (belirtirken aynı `<NoStandardLib>false</NoStandardLib>` ).</span><span class="sxs-lookup"><span data-stu-id="e4a57-249">If you don't specify **NoStandardLib**, mscorlib.dll is imported into your program (same as specifying `<NoStandardLib>false</NoStandardLib>`).</span></span>

## <a name="subsystemversion"></a><span data-ttu-id="e4a57-250">SubsystemVersion</span><span class="sxs-lookup"><span data-stu-id="e4a57-250">SubsystemVersion</span></span>

<span data-ttu-id="e4a57-251">Yürütülebilir dosyanın çalıştığı alt sistemin en düşük sürümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="e4a57-251">Specifies the minimum version of the subsystem on which the executable file runs.</span></span> <span data-ttu-id="e4a57-252">En yaygın olarak, bu seçenek yürütülebilir dosyanın eski Windows sürümleriyle kullanılamayan güvenlik özelliklerini kullanmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="e4a57-252">Most commonly, this option ensures that the executable file can use security features that aren’t available with older versions of Windows.</span></span>

> [!NOTE]
> <span data-ttu-id="e4a57-253">Alt sistemi belirtmek için, [**TargetType**](./output.md#targettype) derleyici seçeneğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="e4a57-253">To specify the subsystem itself, use the [**TargetType**](./output.md#targettype) compiler option.</span></span>

```xml
<SubsystemVersion>major.minor</SubsystemVersion>
```

<span data-ttu-id="e4a57-254">`major.minor`Alt sistemin gerekli en düşük sürümünü, birincil ve ikincil sürümlerin nokta gösteriminde gösterildiği gibi belirtin.</span><span class="sxs-lookup"><span data-stu-id="e4a57-254">The `major.minor` specify the minimum required version of the subsystem, as expressed in a dot notation for major and minor versions.</span></span> <span data-ttu-id="e4a57-255">Örneğin, bir uygulamanın Windows 7 ' den eski bir işletim sisteminde çalışacağını belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e4a57-255">For example, you can specify that an application can't run on an operating system that's older than Windows 7.</span></span> <span data-ttu-id="e4a57-256">Bu seçeneğin değerini, bu makalede daha sonra açıklanan tabloda açıklanan şekilde 6,01 olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="e4a57-256">Set the value of this option to 6.01, as the table later in this article describes.</span></span> <span data-ttu-id="e4a57-257">`major`Ve değerlerini `minor` tamsayılar olarak belirtirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e4a57-257">You specify the values for `major` and `minor` as integers.</span></span> <span data-ttu-id="e4a57-258">Sürümdeki öndeki sıfırlar `minor` sürümü değiştirmez, ancak sonunda sıfır yapılır.</span><span class="sxs-lookup"><span data-stu-id="e4a57-258">Leading zeroes in the `minor` version don't change the version, but trailing zeroes do.</span></span> <span data-ttu-id="e4a57-259">Örneğin, 6,1 ve 6,01 aynı sürüme başvurun, ancak 6,10 farklı bir sürüme başvurur.</span><span class="sxs-lookup"><span data-stu-id="e4a57-259">For example, 6.1 and 6.01 refer to the same version, but 6.10 refers to a different version.</span></span> <span data-ttu-id="e4a57-260">Karışıklığın önüne geçmek için küçük sürümü iki basamakla ifade etmenizi öneririz.</span><span class="sxs-lookup"><span data-stu-id="e4a57-260">We recommend expressing the minor version as two digits to avoid confusion.</span></span>

<span data-ttu-id="e4a57-261">Aşağıdaki tabloda, Windows 'un ortak alt sistem sürümleri listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="e4a57-261">The following table lists common subsystem versions of Windows.</span></span>

|<span data-ttu-id="e4a57-262">Windows sürümü</span><span class="sxs-lookup"><span data-stu-id="e4a57-262">Windows version</span></span>|<span data-ttu-id="e4a57-263">Alt sistem sürümü</span><span class="sxs-lookup"><span data-stu-id="e4a57-263">Subsystem version</span></span>|
|---------------------|-----------------------|
|<span data-ttu-id="e4a57-264">Windows 2000</span><span class="sxs-lookup"><span data-stu-id="e4a57-264">Windows 2000</span></span>|<span data-ttu-id="e4a57-265">5.00</span><span class="sxs-lookup"><span data-stu-id="e4a57-265">5.00</span></span>|
|<span data-ttu-id="e4a57-266">Windows XP</span><span class="sxs-lookup"><span data-stu-id="e4a57-266">Windows XP</span></span>|<span data-ttu-id="e4a57-267">5,01</span><span class="sxs-lookup"><span data-stu-id="e4a57-267">5.01</span></span>|
|<span data-ttu-id="e4a57-268">Windows Server 2003</span><span class="sxs-lookup"><span data-stu-id="e4a57-268">Windows Server 2003</span></span>|<span data-ttu-id="e4a57-269">5,02</span><span class="sxs-lookup"><span data-stu-id="e4a57-269">5.02</span></span>|
|<span data-ttu-id="e4a57-270">Windows Vista</span><span class="sxs-lookup"><span data-stu-id="e4a57-270">Windows Vista</span></span>|<span data-ttu-id="e4a57-271">6,00</span><span class="sxs-lookup"><span data-stu-id="e4a57-271">6.00</span></span>|
|<span data-ttu-id="e4a57-272">Windows 7</span><span class="sxs-lookup"><span data-stu-id="e4a57-272">Windows 7</span></span>|<span data-ttu-id="e4a57-273">6,01</span><span class="sxs-lookup"><span data-stu-id="e4a57-273">6.01</span></span>|
|<span data-ttu-id="e4a57-274">Windows Server 2008</span><span class="sxs-lookup"><span data-stu-id="e4a57-274">Windows Server 2008</span></span>|<span data-ttu-id="e4a57-275">6,01</span><span class="sxs-lookup"><span data-stu-id="e4a57-275">6.01</span></span>|
|<span data-ttu-id="e4a57-276">Windows 8</span><span class="sxs-lookup"><span data-stu-id="e4a57-276">Windows 8</span></span>|<span data-ttu-id="e4a57-277">6,02</span><span class="sxs-lookup"><span data-stu-id="e4a57-277">6.02</span></span>|

<span data-ttu-id="e4a57-278">**Alt Systemversion** derleyici seçeneğinin varsayılan değeri aşağıdaki listede yer alan koşullara bağlıdır:</span><span class="sxs-lookup"><span data-stu-id="e4a57-278">The default value of the **SubsystemVersion** compiler option depends on the conditions in the following list:</span></span>

- <span data-ttu-id="e4a57-279">Aşağıdaki listede herhangi bir derleyici seçeneğinin ayarlanmış olması halinde varsayılan değer 6,02 ' dir:</span><span class="sxs-lookup"><span data-stu-id="e4a57-279">The default value is 6.02 if any compiler option in the following list is set:</span></span>
  - [<span data-ttu-id="e4a57-280">-target:appcontainerexe</span><span class="sxs-lookup"><span data-stu-id="e4a57-280">-target:appcontainerexe</span></span>](./target-appcontainerexe-compiler-option.md)
  - [<span data-ttu-id="e4a57-281">-target:winmdobj</span><span class="sxs-lookup"><span data-stu-id="e4a57-281">-target:winmdobj</span></span>](./target-winmdobj-compiler-option.md)
  - [<span data-ttu-id="e4a57-282">-Platform: ARM</span><span class="sxs-lookup"><span data-stu-id="e4a57-282">-platform:arm</span></span>](./platform-compiler-option.md)
- <span data-ttu-id="e4a57-283">MSBuild kullanıyorsanız varsayılan değer 6,00 ' dir. .NET Framework 4,5 ' i hedefliyorsanız ve bu listede daha önce belirtilen derleyici seçeneklerinden hiçbirini belirlemediniz.</span><span class="sxs-lookup"><span data-stu-id="e4a57-283">The default value is 6.00 if you're using MSBuild, you're targeting .NET Framework 4.5, and you haven't set any of the compiler options that were specified earlier in this list.</span></span>
- <span data-ttu-id="e4a57-284">Önceki koşullardan hiçbiri doğru değilse varsayılan değer 4,00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="e4a57-284">The default value is 4.00 if none of the previous conditions are true.</span></span>

## <a name="moduleassemblyname"></a><span data-ttu-id="e4a57-285">ModuleAssemblyName</span><span class="sxs-lookup"><span data-stu-id="e4a57-285">ModuleAssemblyName</span></span>

<span data-ttu-id="e4a57-286">Genel olmayan türleri *. netmodule* 'nin erişebileceği bir derlemenin adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="e4a57-286">Specifies the name of an assembly whose non-public types a *.netmodule* can access.</span></span>

```xml
<ModuleAssemblyName>assembly_name</ModuleAssemblyName>
```

<span data-ttu-id="e4a57-287">**Moduleassemblyname** bir *. netmodule* oluştururken ve aşağıdaki koşulların doğru olduğu durumlarda kullanılmalıdır:</span><span class="sxs-lookup"><span data-stu-id="e4a57-287">**ModuleAssemblyName** should be used when building a *.netmodule*, and where the following conditions are true:</span></span>

- <span data-ttu-id="e4a57-288">*. Netmodule* , mevcut bir derlemede ortak olmayan türlere erişim gerektirir.</span><span class="sxs-lookup"><span data-stu-id="e4a57-288">The *.netmodule* needs access to non-public types in an existing assembly.</span></span>
- <span data-ttu-id="e4a57-289">. Netmodule 'nin derolacağı derlemenin adını bilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e4a57-289">You know the name of the assembly into which the .netmodule will be built.</span></span>
- <span data-ttu-id="e4a57-290">Mevcut bütünleştirilmiş kod, öğesine arkadaş bütünleştirilmiş kodu erişimi verdi. *netmodule* oluşturulacak.</span><span class="sxs-lookup"><span data-stu-id="e4a57-290">The existing assembly has granted friend assembly access to the assembly into which the .*netmodule* will be built.</span></span>

<span data-ttu-id="e4a57-291">. Netmodule oluşturma hakkında daha fazla bilgi için, bkz. **modülün** [**TargetType**](output.md#targettype) seçeneği.</span><span class="sxs-lookup"><span data-stu-id="e4a57-291">For more information on building a .netmodule, see [**TargetType**](output.md#targettype) option of **module**.</span></span> <span data-ttu-id="e4a57-292">Friend derlemeleri hakkında daha fazla bilgi için bkz. [arkadaş derlemeler](../../../standard/assembly/friend.md).</span><span class="sxs-lookup"><span data-stu-id="e4a57-292">For more information on friend assemblies, see [Friend Assemblies](../../../standard/assembly/friend.md).</span></span>
