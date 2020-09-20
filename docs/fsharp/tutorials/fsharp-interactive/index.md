---
title: F# Etkileşimli (DotNet) başvurusu
description: 'F # kodunu konsolda etkileşimli olarak çalıştırmak veya F # betiklerini yürütmek için F# Etkileşimli (DotNet fsi) nasıl kullanılacağını öğrenin.'
ms.date: 08/20/2020
f1_keywords:
- VS.ToolsOptionsPages.F#_Tools.F#_Interactive
ms.openlocfilehash: ae8d68140ddec8e18ee23e9a43b548907e1ab5c4
ms.sourcegitcommit: fe8877e564deb68d77fa4b79f55584ac8d7e8997
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2020
ms.locfileid: "90720328"
---
# <a name="interactive-programming-with-f"></a><span data-ttu-id="a4b9b-103">F ile etkileşimli programlama\#</span><span class="sxs-lookup"><span data-stu-id="a4b9b-103">Interactive programming with F\#</span></span>

<span data-ttu-id="a4b9b-104">F# Etkileşimli (DotNet fsi), konsolda F # kodunu etkileşimli olarak çalıştırmak veya F # betiklerini yürütmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a4b9b-104">F# Interactive (dotnet fsi) is used to run F# code interactively at the console, or to execute F# scripts.</span></span> <span data-ttu-id="a4b9b-105">Diğer bir deyişle, F # Interactive F # dili için bir REPL (okuma, değerlendirme, yazdırma döngüsü) yürütür.</span><span class="sxs-lookup"><span data-stu-id="a4b9b-105">In other words, F# interactive executes a REPL (Read, Evaluate, Print Loop) for the F# language.</span></span>

<span data-ttu-id="a4b9b-106">Konsolundan F# Etkileşimli çalıştırmak için, öğesini çalıştırın `dotnet fsi` .</span><span class="sxs-lookup"><span data-stu-id="a4b9b-106">To run F# Interactive from the console, run `dotnet fsi`.</span></span> <span data-ttu-id="a4b9b-107">`dotnet fsi`Herhangi bir .NET SDK 'sında bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a4b9b-107">You will find `dotnet fsi` in any .NET SDK.</span></span>

<span data-ttu-id="a4b9b-108">Kullanılabilen komut satırı seçenekleri hakkında daha fazla bilgi için bkz. [F# etkileşimli seçenekleri](../../language-reference/fsharp-interactive-options.md).</span><span class="sxs-lookup"><span data-stu-id="a4b9b-108">For information about command line options available, see [F# Interactive Options](../../language-reference/fsharp-interactive-options.md).</span></span>

<span data-ttu-id="a4b9b-109">Visual Studio aracılığıyla F# Etkileşimli çalıştırmak için **F# Etkileşimli**etiketli uygun araç çubuğu düğmesine tıklayabilir veya **Ctrl + Alt + F**tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="a4b9b-109">To run F# Interactive through Visual Studio, you can click the appropriate toolbar button labeled **F# Interactive**, or use the keys **Ctrl+Alt+F**.</span></span> <span data-ttu-id="a4b9b-110">Bunu yapmak, F# Etkileşimli oturum çalıştıran bir araç penceresi olan etkileşimli pencereyi açar.</span><span class="sxs-lookup"><span data-stu-id="a4b9b-110">Doing this will open the interactive window, a tool window running an F# Interactive session.</span></span> <span data-ttu-id="a4b9b-111">Ayrıca etkileşimli pencerede çalıştırmak istediğiniz kod ve **Alt + Enter**tuş birleşimine basabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a4b9b-111">You can also select some code that you want to run in the interactive window and hit the key combination **Alt+Enter**.</span></span> <span data-ttu-id="a4b9b-112">F# Etkileşimli, **F# Etkileşimli**etiketli bir araç penceresinde başlatılır.</span><span class="sxs-lookup"><span data-stu-id="a4b9b-112">F# Interactive starts in a tool window labeled **F# Interactive**.</span></span> <span data-ttu-id="a4b9b-113">Bu tuş birleşimini kullandığınızda, düzenleyici penceresinin odağa sahip olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="a4b9b-113">When you use this key combination, make sure that the editor window has the focus.</span></span>

<span data-ttu-id="a4b9b-114">Konsolunu veya Visual Studio 'Yu kullanıp kullanmayacağınızı bir komut istemi belirir ve yorumlayıcı, girişinizi bekler.</span><span class="sxs-lookup"><span data-stu-id="a4b9b-114">Whether you are using the console or Visual Studio, a command prompt appears and the interpreter awaits your input.</span></span> <span data-ttu-id="a4b9b-115">Kodu, kod dosyasında olduğu gibi girebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a4b9b-115">You can enter code just as you would in a code file.</span></span> <span data-ttu-id="a4b9b-116">Kodu derlemek ve yürütmek için, bir satırı veya birkaç giriş satırını sonlandırmak üzere iki noktalı virgül (**;;**) girin.</span><span class="sxs-lookup"><span data-stu-id="a4b9b-116">To compile and execute the code, enter two semicolons (**;;**) to terminate a line or several lines of input.</span></span>

<span data-ttu-id="a4b9b-117">F# Etkileşimli kodu derlemeye çalışır ve başarılı olursa, kodu yürütür ve derlenen türlerin ve değerlerin imzasını yazdırır.</span><span class="sxs-lookup"><span data-stu-id="a4b9b-117">F# Interactive attempts to compile the code and, if successful, it executes the code and prints the signature of the types and values that it compiled.</span></span> <span data-ttu-id="a4b9b-118">Hata oluşursa yorumlayıcı hata iletilerini yazdırır.</span><span class="sxs-lookup"><span data-stu-id="a4b9b-118">If errors occur, the interpreter prints the error messages.</span></span>

<span data-ttu-id="a4b9b-119">Aynı oturumda girilen kod, daha önce girilmiş olan her türlü yapıya erişebilir, böylece programları oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a4b9b-119">Code entered in the same session has access to any constructs entered previously, so you can build up programs.</span></span> <span data-ttu-id="a4b9b-120">Araç penceresindeki kapsamlı bir arabellek, gerekirse kodu bir dosyaya kopyalamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="a4b9b-120">An extensive buffer in the tool window allows you to copy the code into a file if needed.</span></span>

<span data-ttu-id="a4b9b-121">Visual Studio 'da çalıştırıldığında F# Etkileşimli projenizden bağımsız olarak çalışır. bu nedenle, örneğin, işlev için kodu etkileşimli pencereye kopyalamadıkça, projenizde tanımlanan yapıları F# Etkileşimli kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="a4b9b-121">When run in Visual Studio, F# Interactive runs independently of your project, so, for example, you cannot use constructs defined in your project in F# Interactive unless you copy the code for the function into the interactive window.</span></span>

<span data-ttu-id="a4b9b-122">Bazı kitaplıklara başvuruda bulunan bir proje açıksa, bu F# Etkileşimli **Çözüm Gezgini**aracılığıyla bunlara başvurabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a4b9b-122">If you have a project open that references some libraries, you can reference these in F# Interactive through **Solution Explorer**.</span></span> <span data-ttu-id="a4b9b-123">F# Etkileşimli bir kitaplığa başvurmak için, **Başvurular** düğümünü genişletin, kitaplığın kısayol menüsünü açın ve **F# Etkileşimli gönder**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="a4b9b-123">To reference a library in F# Interactive, expand the **References** node, open the shortcut menu for the library, and choose **Send to F# Interactive**.</span></span>

<span data-ttu-id="a4b9b-124">Ayarları ayarlayarak F# Etkileşimli komut satırı bağımsız değişkenlerini (Seçenekler) kontrol edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a4b9b-124">You can control the F# Interactive command line arguments (options) by adjusting the settings.</span></span> <span data-ttu-id="a4b9b-125">**Araçlar** menüsünde **Seçenekler...**' i seçin ve ardından **F # araçları**' nı genişletin.</span><span class="sxs-lookup"><span data-stu-id="a4b9b-125">On the **Tools** menu, select **Options...**, and then expand **F# Tools**.</span></span> <span data-ttu-id="a4b9b-126">Değiştirebileceğiniz iki ayar F# Etkileşimli seçenekleridir ve **64 bit F# Etkileşimli** ayarıdır ve bu, yalnızca 64 bit makinede F# Etkileşimli çalıştırıyorsanız geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="a4b9b-126">The two settings that you can change are the F# Interactive options and the **64-bit F# Interactive** setting, which is relevant only if you are running F# Interactive on a 64-bit machine.</span></span> <span data-ttu-id="a4b9b-127">Bu ayar, 32 bit veya 64 bit işlem olarak çalıştırılıp çalıştırılmadığını belirleyen fsi.exe veya fsianycpu.exe adanmış 64 bitlik sürümünü çalıştırmak isteyip istemediğinizi belirler.</span><span class="sxs-lookup"><span data-stu-id="a4b9b-127">This setting determines whether you want to run the dedicated 64-bit version of fsi.exe or fsianycpu.exe, which uses the machine architecture to determine whether to run as a 32-bit or 64-bit process.</span></span>

## <a name="scripting-with-f"></a><span data-ttu-id="a4b9b-128">F ile betik oluşturma\#</span><span class="sxs-lookup"><span data-stu-id="a4b9b-128">Scripting with F\#</span></span>

<span data-ttu-id="a4b9b-129">Betikler **. FSX** veya **. fsscript**dosya uzantısını kullanır.</span><span class="sxs-lookup"><span data-stu-id="a4b9b-129">Scripts use the file extension **.fsx** or **.fsscript**.</span></span> <span data-ttu-id="a4b9b-130">Kaynak kodu derlemek ve daha sonra derlenen derlemeyi çalıştırmak yerine **DotNet fsi** 'yi çalıştırabilir ve f # Kaynak Kodu betiğinin dosya adını belirtebilir ve f # Interactive kodu okur ve gerçek zamanlı olarak yürütür.</span><span class="sxs-lookup"><span data-stu-id="a4b9b-130">Instead of compiling source code and then later running the compiled assembly, you can just run **dotnet fsi** and specify the filename of the script of F# source code, and F# interactive reads the code and executes it in real time.</span></span>

## <a name="differences-between-the-interactive-scripting-and-compiled-environments"></a><span data-ttu-id="a4b9b-131">Etkileşimli, komut dosyası ve derlenmiş ortamlar arasındaki farklar</span><span class="sxs-lookup"><span data-stu-id="a4b9b-131">Differences between the interactive, scripting, and compiled environments</span></span>

<span data-ttu-id="a4b9b-132">Etkileşimli olarak çalıştırdığınız veya bir betiği çalıştıran F# Etkileşimli kod derlerken **etkileşimli** sembol tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="a4b9b-132">When you are compiling code in F# Interactive, whether you are running interactively or running a script, the symbol **INTERACTIVE** is defined.</span></span> <span data-ttu-id="a4b9b-133">Derleyicide kod derlerken, **derlenen** sembol tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="a4b9b-133">When you are compiling code in the compiler, the symbol **COMPILED** is defined.</span></span> <span data-ttu-id="a4b9b-134">Bu nedenle, kodun derlenmiş ve etkileşimli modlarda farklı olması gerekiyorsa, hangisinin kullanılacağını belirleyebilmek için koşullu derleme için önişlemci yönergelerini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a4b9b-134">Thus, if code needs to be different in compiled and interactive modes, you can use preprocessor directives for conditional compilation to determine which to use.</span></span>

<span data-ttu-id="a4b9b-135">Derleyici yürütürken kullanılamayan F# Etkileşimli betikler çalıştırırken bazı yönergeler kullanılabilir...</span><span class="sxs-lookup"><span data-stu-id="a4b9b-135">Some directives are available when you are executing scripts in F# Interactive that are not available when you are executing the compiler.</span></span> <span data-ttu-id="a4b9b-136">Aşağıdaki tabloda F# Etkileşimli kullanırken kullanılabilir olan yönergeler özetlenmektedir.</span><span class="sxs-lookup"><span data-stu-id="a4b9b-136">The following table summarizes directives that are available when you are using F# Interactive.</span></span>

|<span data-ttu-id="a4b9b-137">Deki</span><span class="sxs-lookup"><span data-stu-id="a4b9b-137">Directive</span></span>|<span data-ttu-id="a4b9b-138">Description</span><span class="sxs-lookup"><span data-stu-id="a4b9b-138">Description</span></span>|
|---------|-----------|
|<span data-ttu-id="a4b9b-139">**#help**</span><span class="sxs-lookup"><span data-stu-id="a4b9b-139">**#help**</span></span>|<span data-ttu-id="a4b9b-140">Kullanılabilir yönergeler hakkındaki bilgileri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="a4b9b-140">Displays information about available directives.</span></span>|
|<span data-ttu-id="a4b9b-141">**#I**</span><span class="sxs-lookup"><span data-stu-id="a4b9b-141">**#I**</span></span>|<span data-ttu-id="a4b9b-142">Bir derleme arama yolunu tırnak işaretleri halinde belirtir.</span><span class="sxs-lookup"><span data-stu-id="a4b9b-142">Specifies an assembly search path in quotation marks.</span></span>|
|<span data-ttu-id="a4b9b-143">**#load**</span><span class="sxs-lookup"><span data-stu-id="a4b9b-143">**#load**</span></span>|<span data-ttu-id="a4b9b-144">Bir kaynak dosyayı okur, derler ve çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="a4b9b-144">Reads a source file, compiles it, and runs it.</span></span>|
|<span data-ttu-id="a4b9b-145">**#quit**</span><span class="sxs-lookup"><span data-stu-id="a4b9b-145">**#quit**</span></span>|<span data-ttu-id="a4b9b-146">F# Etkileşimli oturumunu sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="a4b9b-146">Terminates an F# Interactive session.</span></span>|
|<span data-ttu-id="a4b9b-147">**#r**</span><span class="sxs-lookup"><span data-stu-id="a4b9b-147">**#r**</span></span>|<span data-ttu-id="a4b9b-148">Bir derlemeye başvurur.</span><span class="sxs-lookup"><span data-stu-id="a4b9b-148">References an assembly.</span></span>|
|<span data-ttu-id="a4b9b-149">**#time ["," &#124; "kapalı"]**</span><span class="sxs-lookup"><span data-stu-id="a4b9b-149">**#time ["on"&#124;"off"]**</span></span>|<span data-ttu-id="a4b9b-150">**#Time** , performans bilgilerinin görüntülenip görüntülenmeyeceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="a4b9b-150">By itself, **#time** toggles whether to display performance information.</span></span> <span data-ttu-id="a4b9b-151">Etkinleştirildiğinde, F# Etkileşimli yorumlanan ve yürütülen kodun her bölümü için gerçek zamanlı, CPU süresini ve çöp toplama bilgilerini ölçer.</span><span class="sxs-lookup"><span data-stu-id="a4b9b-151">When it is enabled, F# Interactive measures real time, CPU time, and garbage collection information for each section of code that is interpreted and executed.</span></span>|

<span data-ttu-id="a4b9b-152">F# Etkileşimli dosya veya yolları belirttiğinizde, bir dize sabit değeri beklenmektedir.</span><span class="sxs-lookup"><span data-stu-id="a4b9b-152">When you specify files or paths in F# Interactive, a string literal is expected.</span></span> <span data-ttu-id="a4b9b-153">Bu nedenle, dosyalar ve yollar tırnak işaretleri içinde olmalı ve normal kaçış karakterleri de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="a4b9b-153">Therefore, files and paths must be in quotation marks, and the usual escape characters apply.</span></span> <span data-ttu-id="a4b9b-154">Ayrıca, bir yolu içeren dizeyi tam bir dize olarak yorumlamasını F# Etkileşimli neden olması için @ karakterini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a4b9b-154">Also, you can use the @ character to cause F# Interactive to interpret a string that contains a path as a verbatim string.</span></span> <span data-ttu-id="a4b9b-155">Bu, F# Etkileşimli kaçış karakterlerini yoksaymasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="a4b9b-155">This causes F# Interactive to ignore any escape characters.</span></span>

<span data-ttu-id="a4b9b-156">Derlenmiş ve etkileşimli mod arasındaki farklardan biri, komut satırı bağımsız değişkenlerine erişme yöntemidir.</span><span class="sxs-lookup"><span data-stu-id="a4b9b-156">One of the differences between compiled and interactive mode is the way you access command line arguments.</span></span> <span data-ttu-id="a4b9b-157">Derlenmiş modda **System. Environment. Getcommandbir GS**kullanın.</span><span class="sxs-lookup"><span data-stu-id="a4b9b-157">In compiled mode, use **System.Environment.GetCommandLineArgs**.</span></span> <span data-ttu-id="a4b9b-158">Betikler ' de, **fsi. Commandbir g**kullanın.</span><span class="sxs-lookup"><span data-stu-id="a4b9b-158">In scripts, use **fsi.CommandLineArgs**.</span></span>

<span data-ttu-id="a4b9b-159">Aşağıdaki kod, bir betikteki komut satırı bağımsız değişkenlerini okuyan bir işlevin nasıl oluşturulduğunu ve ayrıca bir betikten başka bir derlemeye nasıl başvurulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="a4b9b-159">The following code illustrates how to create a function that reads the command line arguments in a script and also demonstrates how to reference another assembly from a script.</span></span> <span data-ttu-id="a4b9b-160">İlk kod dosyası **MyAssembly. FS**, başvurulmakta olan derlemenin kodudur.</span><span class="sxs-lookup"><span data-stu-id="a4b9b-160">The first code file, **MyAssembly.fs**, is the code for the assembly being referenced.</span></span> <span data-ttu-id="a4b9b-161">Bu dosyayı komut satırı ile derleyin: **FSC-a MyAssembly. FS** ve sonra ikinci dosyayı komut satırı ile komut dosyası olarak yürütün: **fsi--exec FILE1. FSX** test</span><span class="sxs-lookup"><span data-stu-id="a4b9b-161">Compile this file with the command line: **fsc -a MyAssembly.fs** and then execute the second file as a script with the command line: **fsi --exec file1.fsx** test</span></span>

```fsharp
// MyAssembly.fs
module MyAssembly
let myFunction x y = x + 2 * y
```

```fsharp
// file1.fsx
#r "MyAssembly.dll"

printfn "Command line arguments: "

for arg in fsi.CommandLineArgs do
    printfn "%s" arg

printfn "%A" (MyAssembly.myFunction 10 40)
```

<span data-ttu-id="a4b9b-162">Çıktı aşağıdaki şekilde olacaktır:</span><span class="sxs-lookup"><span data-stu-id="a4b9b-162">The output is as follows:</span></span>

```console
Command line arguments:
file1.fsx
test
90
```

## <a name="package-management-in-f-interactive"></a><span data-ttu-id="a4b9b-163">F# Etkileşimli Paket Yönetimi</span><span class="sxs-lookup"><span data-stu-id="a4b9b-163">Package Management in F# Interactive</span></span>

[!NOTE] <span data-ttu-id="a4b9b-164">Paket Yönetimi, .NET SDK 'nın `dotnet fsi` `3.1.300` ve sonraki sürümlerinde ve .NET SDK 'sının tüm sürümlerinde sevk edilen sürümlerinde bir önizleme özelliği olarak kullanılabilir `5.*` .</span><span class="sxs-lookup"><span data-stu-id="a4b9b-164">Package management is available as a preview feature in versions of `dotnet fsi` shipped in the `3.1.300` and greater versions of the .NET SDK, as well as all `5.*` versions of the .NET SDK.</span></span> <span data-ttu-id="a4b9b-165">Bu önizleme sürümünde etkinleştirmek için `dotnet fsi` `--langversion:preview` bağımsız değişkenle çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="a4b9b-165">To enable it in this preview release, run `dotnet fsi` with the `--langversion:preview` argument.</span></span>

<span data-ttu-id="a4b9b-166">`#r`Aşağıdaki sözdizimi aracılığıyla bir NuGet paketine başvurmak için F# Etkileşimli içindeki BIR DLL 'ye başvurmak üzere sözdizimi de kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="a4b9b-166">The `#r` syntax for referencing a DLL in F# Interactive can also be used to reference a nuget package via the following syntax:</span></span>

```fsharp
#r "nuget: <package name>
```

<span data-ttu-id="a4b9b-167">Örneğin, pakete başvurmak için `FSharp.Data` aşağıdaki `#r` başvuruyu kullanın:</span><span class="sxs-lookup"><span data-stu-id="a4b9b-167">For example, to reference the `FSharp.Data` package, use the following `#r` reference:</span></span>

```fsharp
#r "nuget: FSharp.Data"
```

<span data-ttu-id="a4b9b-168">Bu satırı yürüttükten sonra, paketin en son sürümü `FSharp.Data` NuGet önbelleğinize indirilir ve geçerli F# Etkileşimli oturumunda başvurulacaktır.</span><span class="sxs-lookup"><span data-stu-id="a4b9b-168">After executing this line, the latest version of the `FSharp.Data` package will be downloaded to your nuget cache and referenced in the current F# Interactive session.</span></span>

<span data-ttu-id="a4b9b-169">Paket adına ek olarak, bir paketin belirli sürümlerine kısa bir sözdizimi aracılığıyla başvurulabilir:</span><span class="sxs-lookup"><span data-stu-id="a4b9b-169">In addition to the package name, specific versions of a package can be referenced via a short syntax:</span></span>

```fsharp
#r "nuget: FSharp.Data, 3.3.2"
```

<span data-ttu-id="a4b9b-170">daha açık bir biçimde:</span><span class="sxs-lookup"><span data-stu-id="a4b9b-170">or in a more explicit fashion:</span></span>

```fsharp
#r "nuget: FSharp.Data, Version=3.3.2"
```

## <a name="related-articles"></a><span data-ttu-id="a4b9b-171">İlgili makaleler:</span><span class="sxs-lookup"><span data-stu-id="a4b9b-171">Related articles</span></span>

|<span data-ttu-id="a4b9b-172">Başlık</span><span class="sxs-lookup"><span data-stu-id="a4b9b-172">Title</span></span>|<span data-ttu-id="a4b9b-173">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a4b9b-173">Description</span></span>|
|-----|-----------|
|[<span data-ttu-id="a4b9b-174">F# Etkileşimli Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="a4b9b-174">F# Interactive Options</span></span>](../../language-reference/fsharp-interactive-options.md)|<span data-ttu-id="a4b9b-175">F# Etkileşimli fsi.exe için komut satırı sözdizimini ve seçeneklerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="a4b9b-175">Describes command-line syntax and options for the F# Interactive, fsi.exe.</span></span>|
