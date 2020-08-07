---
title: F# Etkileşimli (fsi.exe) Başvurusu
description: 'F # kodunu konsolda etkileşimli olarak çalıştırmak veya F # betiklerini yürütmek için F# Etkileşimli (fsi.exe) nasıl kullanılacağını öğrenin.'
ms.date: 05/16/2016
f1_keywords:
- VS.ToolsOptionsPages.F#_Tools.F#_Interactive
ms.openlocfilehash: 8bb1563ad34e65101fb9f09d6e347278e4b0de78
ms.sourcegitcommit: c37e8d4642fef647ebab0e1c618ecc29ddfe2a0f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/06/2020
ms.locfileid: "87854951"
---
# <a name="interactive-programming-with-f"></a><span data-ttu-id="8f196-103">F ile etkileşimli programlama\#</span><span class="sxs-lookup"><span data-stu-id="8f196-103">Interactive programming with F\#</span></span>

> [!NOTE]
> <span data-ttu-id="8f196-104">Bu makalede şu anda yalnızca Windows deneyimi açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8f196-104">This article currently describes the experience for Windows only.</span></span>

<span data-ttu-id="8f196-105">F# Etkileşimli (fsi.exe), konsolda F # kodu etkileşimli olarak çalıştırmak veya F # betiklerini yürütmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8f196-105">F# Interactive (fsi.exe) is used to run F# code interactively at the console, or to execute F# scripts.</span></span> <span data-ttu-id="8f196-106">Diğer bir deyişle, F # Interactive F # dili için bir REPL (okuma, değerlendirme, yazdırma döngüsü) yürütür.</span><span class="sxs-lookup"><span data-stu-id="8f196-106">In other words, F# interactive executes a REPL (Read, Evaluate, Print Loop) for the F# language.</span></span>

<span data-ttu-id="8f196-107">Konsolundan F# Etkileşimli çalıştırmak için fsi.exe çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="8f196-107">To run F# Interactive from the console, run fsi.exe.</span></span> <span data-ttu-id="8f196-108">fsi.exe şu şekilde bulacaksınız:</span><span class="sxs-lookup"><span data-stu-id="8f196-108">You will find fsi.exe in:</span></span>

```console
C:\Program Files (x86)\Microsoft Visual Studio\2019\<sku>\Common7\IDE\CommonExtensions\Microsoft\FSharp
```

<span data-ttu-id="8f196-109">nerede `sku` `Community` , veya olur `Professional` `Enterprise` .</span><span class="sxs-lookup"><span data-stu-id="8f196-109">where `sku` is either `Community`, `Professional`, or `Enterprise`.</span></span>

<span data-ttu-id="8f196-110">Kullanılabilen komut satırı seçenekleri hakkında daha fazla bilgi için bkz. [F# etkileşimli seçenekleri](../../language-reference/fsharp-interactive-options.md).</span><span class="sxs-lookup"><span data-stu-id="8f196-110">For information about command line options available, see [F# Interactive Options](../../language-reference/fsharp-interactive-options.md).</span></span>

<span data-ttu-id="8f196-111">Visual Studio aracılığıyla F# Etkileşimli çalıştırmak için **F# Etkileşimli**etiketli uygun araç çubuğu düğmesine tıklayabilir veya **Ctrl + Alt + F**tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="8f196-111">To run F# Interactive through Visual Studio, you can click the appropriate toolbar button labeled **F# Interactive**, or use the keys **Ctrl+Alt+F**.</span></span> <span data-ttu-id="8f196-112">Bunu yapmak, F# Etkileşimli oturum çalıştıran bir araç penceresi olan etkileşimli pencereyi açar.</span><span class="sxs-lookup"><span data-stu-id="8f196-112">Doing this will open the interactive window, a tool window running an F# Interactive session.</span></span> <span data-ttu-id="8f196-113">Ayrıca etkileşimli pencerede çalıştırmak istediğiniz kod ve **Alt + Enter**tuş birleşimine basabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8f196-113">You can also select some code that you want to run in the interactive window and hit the key combination **Alt+Enter**.</span></span> <span data-ttu-id="8f196-114">F# Etkileşimli, **F# Etkileşimli**etiketli bir araç penceresinde başlatılır.</span><span class="sxs-lookup"><span data-stu-id="8f196-114">F# Interactive starts in a tool window labeled **F# Interactive**.</span></span> <span data-ttu-id="8f196-115">Bu tuş birleşimini kullandığınızda, düzenleyici penceresinin odağa sahip olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="8f196-115">When you use this key combination, make sure that the editor window has the focus.</span></span>

<span data-ttu-id="8f196-116">Konsolunu veya Visual Studio 'Yu kullanıp kullanmayacağınızı bir komut istemi belirir ve yorumlayıcı, girişinizi bekler.</span><span class="sxs-lookup"><span data-stu-id="8f196-116">Whether you are using the console or Visual Studio, a command prompt appears and the interpreter awaits your input.</span></span> <span data-ttu-id="8f196-117">Kodu, kod dosyasında olduğu gibi girebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8f196-117">You can enter code just as you would in a code file.</span></span> <span data-ttu-id="8f196-118">Kodu derlemek ve yürütmek için, bir satırı veya birkaç giriş satırını sonlandırmak üzere iki noktalı virgül (**;;**) girin.</span><span class="sxs-lookup"><span data-stu-id="8f196-118">To compile and execute the code, enter two semicolons (**;;**) to terminate a line or several lines of input.</span></span>

<span data-ttu-id="8f196-119">F# Etkileşimli kodu derlemeye çalışır ve başarılı olursa, kodu yürütür ve derlenen türlerin ve değerlerin imzasını yazdırır.</span><span class="sxs-lookup"><span data-stu-id="8f196-119">F# Interactive attempts to compile the code and, if successful, it executes the code and prints the signature of the types and values that it compiled.</span></span> <span data-ttu-id="8f196-120">Hata oluşursa yorumlayıcı hata iletilerini yazdırır.</span><span class="sxs-lookup"><span data-stu-id="8f196-120">If errors occur, the interpreter prints the error messages.</span></span>

<span data-ttu-id="8f196-121">Aynı oturumda girilen kod, daha önce girilmiş olan her türlü yapıya erişebilir, böylece programları oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8f196-121">Code entered in the same session has access to any constructs entered previously, so you can build up programs.</span></span> <span data-ttu-id="8f196-122">Araç penceresindeki kapsamlı bir arabellek, gerekirse kodu bir dosyaya kopyalamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="8f196-122">An extensive buffer in the tool window allows you to copy the code into a file if needed.</span></span>

<span data-ttu-id="8f196-123">Visual Studio 'da çalıştırıldığında F# Etkileşimli projenizden bağımsız olarak çalışır. bu nedenle, örneğin, işlev için kodu etkileşimli pencereye kopyalamadıkça, projenizde tanımlanan yapıları F# Etkileşimli kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="8f196-123">When run in Visual Studio, F# Interactive runs independently of your project, so, for example, you cannot use constructs defined in your project in F# Interactive unless you copy the code for the function into the interactive window.</span></span>

<span data-ttu-id="8f196-124">Bazı kitaplıklara başvuruda bulunan bir proje açıksa, bu F# Etkileşimli **Çözüm Gezgini**aracılığıyla bunlara başvurabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8f196-124">If you have a project open that references some libraries, you can reference these in F# Interactive through **Solution Explorer**.</span></span> <span data-ttu-id="8f196-125">F# Etkileşimli bir kitaplığa başvurmak için, **Başvurular** düğümünü genişletin, kitaplığın kısayol menüsünü açın ve **F# Etkileşimli gönder**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="8f196-125">To reference a library in F# Interactive, expand the **References** node, open the shortcut menu for the library, and choose **Send to F# Interactive**.</span></span>

<span data-ttu-id="8f196-126">Ayarları ayarlayarak F# Etkileşimli komut satırı bağımsız değişkenlerini (Seçenekler) kontrol edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8f196-126">You can control the F# Interactive command line arguments (options) by adjusting the settings.</span></span> <span data-ttu-id="8f196-127">**Araçlar** menüsünde **Seçenekler...**' i seçin ve ardından **F # araçları**' nı genişletin.</span><span class="sxs-lookup"><span data-stu-id="8f196-127">On the **Tools** menu, select **Options...**, and then expand **F# Tools**.</span></span> <span data-ttu-id="8f196-128">Değiştirebileceğiniz iki ayar F# Etkileşimli seçenekleridir ve **64 bit F# Etkileşimli** ayarıdır ve bu, yalnızca 64 bit makinede F# Etkileşimli çalıştırıyorsanız geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="8f196-128">The two settings that you can change are the F# Interactive options and the **64-bit F# Interactive** setting, which is relevant only if you are running F# Interactive on a 64-bit machine.</span></span> <span data-ttu-id="8f196-129">Bu ayar, 32 bit veya 64 bit işlem olarak çalıştırılıp çalıştırılmadığını belirleyen fsi.exe veya fsianycpu.exe adanmış 64 bitlik sürümünü çalıştırmak isteyip istemediğinizi belirler.</span><span class="sxs-lookup"><span data-stu-id="8f196-129">This setting determines whether you want to run the dedicated 64-bit version of fsi.exe or fsianycpu.exe, which uses the machine architecture to determine whether to run as a 32-bit or 64-bit process.</span></span>

## <a name="scripting-with-f"></a><span data-ttu-id="8f196-130">F ile betik oluşturma\#</span><span class="sxs-lookup"><span data-stu-id="8f196-130">Scripting with F\#</span></span>

<span data-ttu-id="8f196-131">Betikler **. FSX** veya **. fsscript**dosya uzantısını kullanır.</span><span class="sxs-lookup"><span data-stu-id="8f196-131">Scripts use the file extension **.fsx** or **.fsscript**.</span></span> <span data-ttu-id="8f196-132">Kaynak kodu derlemek ve daha sonra derlenen derlemeyi çalıştırmak yerine yalnızca **fsi.exe** çalıştırabilir ve f # Kaynak Kodu betiğinin dosya adını belirtebilir ve f # Interactive kodu okur ve gerçek zamanlı olarak yürütür.</span><span class="sxs-lookup"><span data-stu-id="8f196-132">Instead of compiling source code and then later running the compiled assembly, you can just run **fsi.exe** and specify the filename of the script of F# source code, and F# interactive reads the code and executes it in real time.</span></span>

## <a name="differences-between-the-interactive-scripting-and-compiled-environments"></a><span data-ttu-id="8f196-133">Etkileşimli, komut dosyası ve derlenmiş ortamlar arasındaki farklar</span><span class="sxs-lookup"><span data-stu-id="8f196-133">Differences between the interactive, scripting, and compiled environments</span></span>

<span data-ttu-id="8f196-134">Etkileşimli olarak çalıştırdığınız veya bir betiği çalıştıran F# Etkileşimli kod derlerken **etkileşimli** sembol tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="8f196-134">When you are compiling code in F# Interactive, whether you are running interactively or running a script, the symbol **INTERACTIVE** is defined.</span></span> <span data-ttu-id="8f196-135">Derleyicide kod derlerken, **derlenen** sembol tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="8f196-135">When you are compiling code in the compiler, the symbol **COMPILED** is defined.</span></span> <span data-ttu-id="8f196-136">Bu nedenle, kodun derlenmiş ve etkileşimli modlarda farklı olması gerekiyorsa, hangisinin kullanılacağını belirleyebilmek için koşullu derleme için önişlemci yönergelerini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8f196-136">Thus, if code needs to be different in compiled and interactive modes, you can use preprocessor directives for conditional compilation to determine which to use.</span></span>

<span data-ttu-id="8f196-137">Derleyici yürütürken kullanılamayan F# Etkileşimli betikler çalıştırırken bazı yönergeler kullanılabilir...</span><span class="sxs-lookup"><span data-stu-id="8f196-137">Some directives are available when you are executing scripts in F# Interactive that are not available when you are executing the compiler.</span></span> <span data-ttu-id="8f196-138">Aşağıdaki tabloda F# Etkileşimli kullanırken kullanılabilir olan yönergeler özetlenmektedir.</span><span class="sxs-lookup"><span data-stu-id="8f196-138">The following table summarizes directives that are available when you are using F# Interactive.</span></span>

|<span data-ttu-id="8f196-139">Deki</span><span class="sxs-lookup"><span data-stu-id="8f196-139">Directive</span></span>|<span data-ttu-id="8f196-140">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8f196-140">Description</span></span>|
|---------|-----------|
|<span data-ttu-id="8f196-141">**#help**</span><span class="sxs-lookup"><span data-stu-id="8f196-141">**#help**</span></span>|<span data-ttu-id="8f196-142">Kullanılabilir yönergeler hakkındaki bilgileri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="8f196-142">Displays information about available directives.</span></span>|
|<span data-ttu-id="8f196-143">**#I**</span><span class="sxs-lookup"><span data-stu-id="8f196-143">**#I**</span></span>|<span data-ttu-id="8f196-144">Bir derleme arama yolunu tırnak işaretleri halinde belirtir.</span><span class="sxs-lookup"><span data-stu-id="8f196-144">Specifies an assembly search path in quotation marks.</span></span>|
|<span data-ttu-id="8f196-145">**#load**</span><span class="sxs-lookup"><span data-stu-id="8f196-145">**#load**</span></span>|<span data-ttu-id="8f196-146">Bir kaynak dosyayı okur, derler ve çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="8f196-146">Reads a source file, compiles it, and runs it.</span></span>|
|<span data-ttu-id="8f196-147">**#quit**</span><span class="sxs-lookup"><span data-stu-id="8f196-147">**#quit**</span></span>|<span data-ttu-id="8f196-148">F# Etkileşimli oturumunu sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="8f196-148">Terminates an F# Interactive session.</span></span>|
|<span data-ttu-id="8f196-149">**#r**</span><span class="sxs-lookup"><span data-stu-id="8f196-149">**#r**</span></span>|<span data-ttu-id="8f196-150">Bir derlemeye başvurur.</span><span class="sxs-lookup"><span data-stu-id="8f196-150">References an assembly.</span></span>|
|<span data-ttu-id="8f196-151">**#time ["," &#124; "kapalı"]**</span><span class="sxs-lookup"><span data-stu-id="8f196-151">**#time ["on"&#124;"off"]**</span></span>|<span data-ttu-id="8f196-152">**#Time** , performans bilgilerinin görüntülenip görüntülenmeyeceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="8f196-152">By itself, **#time** toggles whether to display performance information.</span></span> <span data-ttu-id="8f196-153">Etkinleştirildiğinde, F# Etkileşimli yorumlanan ve yürütülen kodun her bölümü için gerçek zamanlı, CPU süresini ve çöp toplama bilgilerini ölçer.</span><span class="sxs-lookup"><span data-stu-id="8f196-153">When it is enabled, F# Interactive measures real time, CPU time, and garbage collection information for each section of code that is interpreted and executed.</span></span>|

<span data-ttu-id="8f196-154">F# Etkileşimli dosya veya yolları belirttiğinizde, bir dize sabit değeri beklenmektedir.</span><span class="sxs-lookup"><span data-stu-id="8f196-154">When you specify files or paths in F# Interactive, a string literal is expected.</span></span> <span data-ttu-id="8f196-155">Bu nedenle, dosyalar ve yollar tırnak işaretleri içinde olmalı ve normal kaçış karakterleri de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="8f196-155">Therefore, files and paths must be in quotation marks, and the usual escape characters apply.</span></span> <span data-ttu-id="8f196-156">Ayrıca, bir yolu içeren dizeyi tam bir dize olarak yorumlamasını F# Etkileşimli neden olması için @ karakterini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8f196-156">Also, you can use the @ character to cause F# Interactive to interpret a string that contains a path as a verbatim string.</span></span> <span data-ttu-id="8f196-157">Bu, F# Etkileşimli kaçış karakterlerini yoksaymasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="8f196-157">This causes F# Interactive to ignore any escape characters.</span></span>

<span data-ttu-id="8f196-158">Derlenmiş ve etkileşimli mod arasındaki farklardan biri, komut satırı bağımsız değişkenlerine erişme yöntemidir.</span><span class="sxs-lookup"><span data-stu-id="8f196-158">One of the differences between compiled and interactive mode is the way you access command line arguments.</span></span> <span data-ttu-id="8f196-159">Derlenmiş modda **System. Environment. Getcommandbir GS**kullanın.</span><span class="sxs-lookup"><span data-stu-id="8f196-159">In compiled mode, use **System.Environment.GetCommandLineArgs**.</span></span> <span data-ttu-id="8f196-160">Betikler ' de, **fsi. Commandbir g**kullanın.</span><span class="sxs-lookup"><span data-stu-id="8f196-160">In scripts, use **fsi.CommandLineArgs**.</span></span>

<span data-ttu-id="8f196-161">Aşağıdaki kod, bir betikteki komut satırı bağımsız değişkenlerini okuyan bir işlevin nasıl oluşturulduğunu ve ayrıca bir betikten başka bir derlemeye nasıl başvurulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="8f196-161">The following code illustrates how to create a function that reads the command line arguments in a script and also demonstrates how to reference another assembly from a script.</span></span> <span data-ttu-id="8f196-162">İlk kod dosyası **MyAssembly. FS**, başvurulmakta olan derlemenin kodudur.</span><span class="sxs-lookup"><span data-stu-id="8f196-162">The first code file, **MyAssembly.fs**, is the code for the assembly being referenced.</span></span> <span data-ttu-id="8f196-163">Bu dosyayı komut satırı ile derleyin: **FSC-a MyAssembly. FS** ve sonra ikinci dosyayı komut satırı ile komut dosyası olarak yürütün: **fsi--exec FILE1. FSX** test</span><span class="sxs-lookup"><span data-stu-id="8f196-163">Compile this file with the command line: **fsc -a MyAssembly.fs** and then execute the second file as a script with the command line: **fsi --exec file1.fsx** test</span></span>

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

<span data-ttu-id="8f196-164">Çıktı aşağıdaki şekilde olacaktır:</span><span class="sxs-lookup"><span data-stu-id="8f196-164">The output is as follows:</span></span>

```console
Command line arguments:
file1.fsx
test
90
```

## <a name="related-articles"></a><span data-ttu-id="8f196-165">İlgili makaleler:</span><span class="sxs-lookup"><span data-stu-id="8f196-165">Related articles</span></span>

|<span data-ttu-id="8f196-166">Başlık</span><span class="sxs-lookup"><span data-stu-id="8f196-166">Title</span></span>|<span data-ttu-id="8f196-167">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8f196-167">Description</span></span>|
|-----|-----------|
|[<span data-ttu-id="8f196-168">F# Etkileşimli Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="8f196-168">F# Interactive Options</span></span>](../../language-reference/fsharp-interactive-options.md)|<span data-ttu-id="8f196-169">F# Etkileşimli fsi.exe için komut satırı sözdizimini ve seçeneklerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="8f196-169">Describes command-line syntax and options for the F# Interactive, fsi.exe.</span></span>|
|[<span data-ttu-id="8f196-170">F# Etkileşimli kitaplığı başvurusu</span><span class="sxs-lookup"><span data-stu-id="8f196-170">F# Interactive Library Reference</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/fsharp-interactive-library-reference)|<span data-ttu-id="8f196-171">F # Interactive 'de kod yürütürken kullanılabilen kitaplık işlevlerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="8f196-171">Describes library functionality available when executing code in F# interactive.</span></span>|
