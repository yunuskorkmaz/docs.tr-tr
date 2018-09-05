---
title: Csc.exe ile komut satırı derleme
ms.date: 04/19/2017
helpviewer_keywords:
- builds [C#]
- command line [C#]
ms.assetid: 66e70056-dd20-453c-a9b3-507e0478b015
ms.openlocfilehash: 4b6dfdbce131371553fc729206de29794266bfbe
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43553233"
---
# <a name="command-line-build-with-cscexe"></a><span data-ttu-id="cbb44-102">Csc.exe ile komut satırı derleme</span><span class="sxs-lookup"><span data-stu-id="cbb44-102">Command-line build with csc.exe</span></span>
<span data-ttu-id="cbb44-103">Yürütülebilir dosyanın adını yazarak C# derleyicisini çağırabilirsiniz (*csc.exe*) bir komut isteminde.</span><span class="sxs-lookup"><span data-stu-id="cbb44-103">You can invoke the C# compiler by typing the name of its executable file (*csc.exe*) at a command prompt.</span></span>

<span data-ttu-id="cbb44-104">Kullanırsanız **Visual Studio için geliştirici komut istemi** penceresinde tüm gerekli ortam değişkenleri sizin için ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="cbb44-104">If you use the **Developer Command Prompt for Visual Studio** window, all the necessary environment variables are set for you.</span></span> <span data-ttu-id="cbb44-105">Bu araç erişim hakkında daha fazla bilgi için bkz: [Visual Studio için geliştirici komut istemi](../../../framework/tools/developer-command-prompt-for-vs.md) konu.</span><span class="sxs-lookup"><span data-stu-id="cbb44-105">For information on how to access this tool, see the [Developer Command Prompt for Visual Studio](../../../framework/tools/developer-command-prompt-for-vs.md) topic.</span></span> 

<span data-ttu-id="cbb44-106">Standart bir komut istemi penceresi kullanıyorsanız çağırabilirsiniz önce yolunuzu ayarlamanız gerekir *csc.exe* bilgisayarınızdaki herhangi bir alt dizinden.</span><span class="sxs-lookup"><span data-stu-id="cbb44-106">If you use a standard Command Prompt window, you must adjust your path before you can invoke *csc.exe* from any subdirectory on your computer.</span></span> <span data-ttu-id="cbb44-107">Ayrıca çalıştırmalısınız *vsvars32.bat* komut satırı yapılarını desteklemek üzere uygun ortam değişkenlerini ayarlamak için.</span><span class="sxs-lookup"><span data-stu-id="cbb44-107">You also must run *vsvars32.bat* to set the appropriate environment variables to support command-line builds.</span></span> <span data-ttu-id="cbb44-108">Hakkında daha fazla bilgi için *vsvars32.bat*, bulmak ve çalıştırmak için bkz: hakkında yönergeler dahil olmak üzere [nasıl yapılır: ortam değişkenlerini ayarlamak için Visual Studio komut satırı](../../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md).</span><span class="sxs-lookup"><span data-stu-id="cbb44-108">For more information about *vsvars32.bat*, including instructions for how to find and run it, see [How to: Set Environment Variables for the Visual Studio Command Line](../../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md).</span></span>

<span data-ttu-id="cbb44-109">Yalnızca bir bilgisayarda çalışıyorsanız [!INCLUDE[winsdklong](~/includes/winsdklong-md.md)], C# derleyicisi, kullanabileceğiniz **SDK Komut İstemi**, açtığınız **Microsoft .NET Framework SDK'sı** menü seçeneği.</span><span class="sxs-lookup"><span data-stu-id="cbb44-109">If you're working on a computer that has only the [!INCLUDE[winsdklong](~/includes/winsdklong-md.md)], you can use the C# compiler at the **SDK Command Prompt**, which you open from the **Microsoft .NET Framework SDK** menu option.</span></span>

<span data-ttu-id="cbb44-110">Ayrıca C# programlarını program aracılığıyla oluşturmak için MSBuild'i kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cbb44-110">You can also use MSBuild to build C# programs programmatically.</span></span> <span data-ttu-id="cbb44-111">Daha fazla bilgi için [MSBuild](/visualstudio/msbuild/msbuild).</span><span class="sxs-lookup"><span data-stu-id="cbb44-111">For more information, see [MSBuild](/visualstudio/msbuild/msbuild).</span></span>

<span data-ttu-id="cbb44-112">*Csc.exe* yürütülebilir dosyası genellikle bulunan Microsoft.NET\Framework\\*\<sürüm >* klasörü altında *Windows* Dizin.</span><span class="sxs-lookup"><span data-stu-id="cbb44-112">The *csc.exe* executable file usually is located in the Microsoft.NET\Framework\\*\<Version>* folder under the *Windows* directory.</span></span> <span data-ttu-id="cbb44-113">Bu dosyanın yeri, belirli bir bilgisayarın tam yapılandırmasına bağlı olarak değişebilir.</span><span class="sxs-lookup"><span data-stu-id="cbb44-113">Its location might vary depending on the exact configuration of a particular computer.</span></span> <span data-ttu-id="cbb44-114">Bilgisayarınızda .NET Framework'ün birden fazla sürümü yüklüyse, bu dosyanın birden fazla sürümünü bulacaksınız.</span><span class="sxs-lookup"><span data-stu-id="cbb44-114">If more than one version of the .NET Framework is installed on your computer, you'll find multiple versions of this file.</span></span> <span data-ttu-id="cbb44-115">Bu tür yüklemeler hakkında daha fazla bilgi için bkz. [nasıl yapılır: hangi .NET Framework sürümlerinin yüklü olduğunu belirleme](../../../framework/migration-guide/how-to-determine-which-versions-are-installed.md).</span><span class="sxs-lookup"><span data-stu-id="cbb44-115">For more information about such installations, see [How to: determine which versions of the .NET Framework are installed](../../../framework/migration-guide/how-to-determine-which-versions-are-installed.md).</span></span>

> [!TIP]
>  <span data-ttu-id="cbb44-116">Visual Studio IDE kullanarak bir proje oluşturduğunuzda, görüntüleyebileceğiniz **csc** komut ve ilgili derleme seçeneklerini de **çıkış** penceresi.</span><span class="sxs-lookup"><span data-stu-id="cbb44-116">When you build a project by using the Visual Studio IDE, you can display the **csc** command and its associated compiler options in the **Output** window.</span></span> <span data-ttu-id="cbb44-117">Bu bilgileri görüntülemek için yönergeleri izleyin. [nasıl yapılır: görünüm, kaydetme ve yapılandırma derleme günlük dosyalarını](/visualstudio/ide/how-to-view-save-and-configure-build-log-files#to-change-the-amount-of-information-included-in-the-build-log) günlük verilerinin ayrıntı düzeyini değiştirmek için **Normal** veya **ayrıntılı**.</span><span class="sxs-lookup"><span data-stu-id="cbb44-117">To display this information, follow the instructions in [How to: View, Save, and Configure Build Log Files](/visualstudio/ide/how-to-view-save-and-configure-build-log-files#to-change-the-amount-of-information-included-in-the-build-log) to change the verbosity level of the log data to **Normal** or **Detailed**.</span></span> <span data-ttu-id="cbb44-118">Projenizi yeniden oluşturduktan sonra arama **çıkış** penceresi **csc** C# derleyicisinin çağrısını bulmak için.</span><span class="sxs-lookup"><span data-stu-id="cbb44-118">After you rebuild your project, search the **Output** window for **csc** to find the invocation of the C# compiler.</span></span>

 <span data-ttu-id="cbb44-119">**Bu konudaki**</span><span class="sxs-lookup"><span data-stu-id="cbb44-119">**In this topic**</span></span>

- [<span data-ttu-id="cbb44-120">Komut satırı sözdizimi için kurallar</span><span class="sxs-lookup"><span data-stu-id="cbb44-120">Rules for command-line syntax</span></span>](#-rules-for-command-line-syntax-for-the-c-compiler)

- [<span data-ttu-id="cbb44-121">Örnek komut satırları</span><span class="sxs-lookup"><span data-stu-id="cbb44-121">Sample command lines</span></span>](#sample-command-lines-for-the-c-compiler)

- [<span data-ttu-id="cbb44-122">C# Derleyici ve C++ Derleyici çıkışını arasındaki farklar</span><span class="sxs-lookup"><span data-stu-id="cbb44-122">Differences between C# compiler and C++ compiler output</span></span>](#differences-between-c-compiler-and-c-compiler-output)

## <a name="rules-for-command-line-syntax-for-the-c-compiler"></a><span data-ttu-id="cbb44-123">Komut satırı sözdizimi C# derleyicisi için kurallar</span><span class="sxs-lookup"><span data-stu-id="cbb44-123">Rules for command-line syntax for the C# compiler</span></span>

<span data-ttu-id="cbb44-124">İşletim sistemi komut satırında belirtilen bağımsız değişkenler yorumlarken C# derleyici aşağıdaki kuralları kullanır:</span><span class="sxs-lookup"><span data-stu-id="cbb44-124">The C# compiler uses the following rules when it interprets arguments given on the operating system command line:</span></span>

- <span data-ttu-id="cbb44-125">Bağımsız değişkenler bir boşluk veya sekme olduğu boşluk tarafından ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="cbb44-125">Arguments are delimited by white space, which is either a space or a tab.</span></span>

- <span data-ttu-id="cbb44-126">İnceltme işareti (^) bir kaçış karakteri veya sınırlayıcı olarak tanınmıyor.</span><span class="sxs-lookup"><span data-stu-id="cbb44-126">The caret character (^) is not recognized as an escape character or delimiter.</span></span> <span data-ttu-id="cbb44-127">İşletim sistemindeki komut satırı ayrıştırıcı tarafından karakter için geçirilmeden önce işlenir `argv` programı dizisi.</span><span class="sxs-lookup"><span data-stu-id="cbb44-127">The character is handled by the command-line parser in the operating system before it's passed to the `argv` array in the program.</span></span>

- <span data-ttu-id="cbb44-128">Çift tırnak işaretleri ("dize") arasına bir dize içinde bulunan boşluk bağımsız olarak tek bir bağımsız değişken olarak yorumlanır.</span><span class="sxs-lookup"><span data-stu-id="cbb44-128">A string enclosed in double quotation marks ("string") is interpreted as a single argument, regardless of white space that is contained within.</span></span> <span data-ttu-id="cbb44-129">Tırnak işaretli dize bağımsız değişkeni eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="cbb44-129">A quoted string can be embedded in an argument.</span></span>

- <span data-ttu-id="cbb44-130">Çift tırnak işareti öncesinde bir ters eğik çizgi (\\") bir değişmez değer çift tırnak işareti karakteri (") yorumlanır.</span><span class="sxs-lookup"><span data-stu-id="cbb44-130">A double quotation mark preceded by a backslash (\\") is interpreted as a literal double quotation mark character (").</span></span>

- <span data-ttu-id="cbb44-131">Ters eğik çizgi, başka bir deyişle, bunlar hemen çift tırnak işareti koyun sürece yorumlanır.</span><span class="sxs-lookup"><span data-stu-id="cbb44-131">Backslashes are interpreted literally, unless they immediately precede a double quotation mark.</span></span>

- <span data-ttu-id="cbb44-132">Çift tırnak işareti ters eğik çizgi sayıda izlediyseniz, bir ters eğik çizgi yerleştirecek `argv` dizisi için her çift ters eğik çizgi ve çift tırnak işareti, dize ayırıcı olarak yorumlanır.</span><span class="sxs-lookup"><span data-stu-id="cbb44-132">If an even number of backslashes is followed by a double quotation mark, one backslash is put in the `argv` array for every pair of backslashes, and the double quotation mark is interpreted as a string delimiter.</span></span>

- <span data-ttu-id="cbb44-133">Çift tırnak işareti ters eğik çizgi tek sayıda izlediyseniz, bir ters eğik çizgi yerleştirecek `argv` dizisi için her çift ters eğik çizgi ve çift tırnak işareti "kaçış" kalan ters eğik çizgi.</span><span class="sxs-lookup"><span data-stu-id="cbb44-133">If an odd number of backslashes is followed by a double quotation mark, one backslash is put in the `argv` array for every pair of backslashes, and the double quotation mark is "escaped" by the remaining backslash.</span></span> <span data-ttu-id="cbb44-134">Bu sabit değeri çift tırnak içinde eklenecek işareti (") neden `argv`.</span><span class="sxs-lookup"><span data-stu-id="cbb44-134">This causes a literal double quotation mark (") to be added in `argv`.</span></span>

## <a name="sample-command-lines-for-the-c-compiler"></a><span data-ttu-id="cbb44-135">C# derleyicisi için örnek komut satırları</span><span class="sxs-lookup"><span data-stu-id="cbb44-135">Sample command lines for the C# compiler</span></span>

- <span data-ttu-id="cbb44-136">Derleme *File.cs* üretme *File.exe*:</span><span class="sxs-lookup"><span data-stu-id="cbb44-136">Compiles *File.cs* producing *File.exe*:</span></span>

```console
csc File.cs 
```

- <span data-ttu-id="cbb44-137">Derleme *File.cs* üretme *File.dll*:</span><span class="sxs-lookup"><span data-stu-id="cbb44-137">Compiles *File.cs* producing *File.dll*:</span></span>

```console
csc -target:library File.cs
```

- <span data-ttu-id="cbb44-138">Derleme *File.cs* ve oluşturan *My.exe*:</span><span class="sxs-lookup"><span data-stu-id="cbb44-138">Compiles *File.cs* and creates *My.exe*:</span></span>

```console
csc -out:My.exe File.cs
```

- <span data-ttu-id="cbb44-139">Tüm C# dosyaları geçerli dizine iyileştirmeler derler ve hata ayıklama sembolünü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="cbb44-139">Compiles all the C# files in the current directory with optimizations enabled and defines the DEBUG symbol.</span></span> <span data-ttu-id="cbb44-140">Çıktı *File2.exe*:</span><span class="sxs-lookup"><span data-stu-id="cbb44-140">The output is *File2.exe*:</span></span>

```console
csc -define:DEBUG -optimize -out:File2.exe *.cs
```

- <span data-ttu-id="cbb44-141">Tüm C# dosyalarında hata ayıklama sürümü geçerli dizindeki derler *File2.dll*.</span><span class="sxs-lookup"><span data-stu-id="cbb44-141">Compiles all the C# files in the current directory producing a debug version of *File2.dll*.</span></span> <span data-ttu-id="cbb44-142">Logo ve uyarı görüntülenir:</span><span class="sxs-lookup"><span data-stu-id="cbb44-142">No logo and no warnings are displayed:</span></span>

```console
csc -target:library -out:File2.dll -warn:0 -nologo -debug *.cs
```

- <span data-ttu-id="cbb44-143">Tüm C# dosyaları geçerli dizine derler *Something.xyz* (DLL):</span><span class="sxs-lookup"><span data-stu-id="cbb44-143">Compiles all the C# files in the current directory to *Something.xyz* (a DLL):</span></span>

```console
csc -target:library -out:Something.xyz *.cs
```

## <a name="differences-between-c-compiler-and-c-compiler-output"></a><span data-ttu-id="cbb44-144">C# Derleyici ve C++ Derleyici çıkışını arasındaki farklar</span><span class="sxs-lookup"><span data-stu-id="cbb44-144">Differences between C# compiler and C++ compiler output</span></span>
<span data-ttu-id="cbb44-145">Hiçbir nesne vardır (*.obj*) dosyaları oluşturan C# derleyicisini çağırma işleminin sonucu olarak; çıktı dosyaları doğrudan oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="cbb44-145">There are no object (*.obj*) files created as a result of invoking the C# compiler; output files are created directly.</span></span> <span data-ttu-id="cbb44-146">Bunun bir sonucu olarak C# derleyicisinin bir bağlayıcı gerekmez.</span><span class="sxs-lookup"><span data-stu-id="cbb44-146">As a result of this, the C# compiler does not need a linker.</span></span>

## <a name="see-also"></a><span data-ttu-id="cbb44-147">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cbb44-147">See also</span></span>

- [<span data-ttu-id="cbb44-148">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="cbb44-148">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
- [<span data-ttu-id="cbb44-149">Alfabetik Listelenmiş C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="cbb44-149">C# Compiler Options Listed Alphabetically</span></span>](../../../csharp/language-reference/compiler-options/listed-alphabetically.md)  
- [<span data-ttu-id="cbb44-150">Kategorilere Göre Listelenen C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="cbb44-150">C# Compiler Options Listed by Category</span></span>](../../../csharp/language-reference/compiler-options/listed-by-category.md)  
- [<span data-ttu-id="cbb44-151">Ana() ve Komut Satırı Bağımsız Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="cbb44-151">Main() and Command-Line Arguments</span></span>](../../../csharp/programming-guide/main-and-command-args/index.md)  
- [<span data-ttu-id="cbb44-152">Komut Satırı Bağımsız Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="cbb44-152">Command-Line Arguments</span></span>](../../../csharp/programming-guide/main-and-command-args/command-line-arguments.md)  
- [<span data-ttu-id="cbb44-153">Nasıl yapılır: komut satırı bağımsız değişkenlerini görüntüleme</span><span class="sxs-lookup"><span data-stu-id="cbb44-153">How to: Display Command-Line Arguments</span></span>](../../../csharp/programming-guide/main-and-command-args/how-to-display-command-line-arguments.md)  
- [<span data-ttu-id="cbb44-154">Nasıl yapılır: foreach Kullanarak Komut Satırı Bağımsız Değişkenlerine Erişme</span><span class="sxs-lookup"><span data-stu-id="cbb44-154">How to: Access Command-Line Arguments Using foreach</span></span>](../../../csharp/programming-guide/main-and-command-args/how-to-access-command-line-arguments-using-foreach.md)  
- [<span data-ttu-id="cbb44-155">Ana() Dönüş Değerleri</span><span class="sxs-lookup"><span data-stu-id="cbb44-155">Main() Return Values</span></span>](../../../csharp/programming-guide/main-and-command-args/main-return-values.md)
