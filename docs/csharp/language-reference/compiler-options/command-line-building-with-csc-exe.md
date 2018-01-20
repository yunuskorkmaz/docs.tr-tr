---
title: "Csc.exe ile komut satırı derleme"
ms.date: 04/19/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- builds [C#]
- command line [C#]
ms.assetid: 66e70056-dd20-453c-a9b3-507e0478b015
caps.latest.revision: "28"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 5fe7b735977b0cde0bed266815987b773be6bdbe
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="command-line-build-with-cscexe"></a><span data-ttu-id="e7a52-102">Csc.exe ile komut satırı derleme</span><span class="sxs-lookup"><span data-stu-id="e7a52-102">Command-line build with csc.exe</span></span>
<span data-ttu-id="e7a52-103">Yürütülebilir dosyanın adını yazarak C# Derleyici çağırabileceği (*csc.exe*) bir komut isteminde.</span><span class="sxs-lookup"><span data-stu-id="e7a52-103">You can invoke the C# compiler by typing the name of its executable file (*csc.exe*) at a command prompt.</span></span>

<span data-ttu-id="e7a52-104">Kullanırsanız **Visual Studio için geliştirici komut istemi** penceresinde, tüm gerekli ortam değişkenlerini sizin için ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="e7a52-104">If you use the **Developer Command Prompt for Visual Studio** window, all the necessary environment variables are set for you.</span></span> <span data-ttu-id="e7a52-105">Bu araç erişim hakkında daha fazla bilgi için bkz: [Visual Studio için geliştirici komut istemi](../../../framework/tools/developer-command-prompt-for-vs.md) konu.</span><span class="sxs-lookup"><span data-stu-id="e7a52-105">For information on how to access this tool, see the [Developer Command Prompt for Visual Studio](../../../framework/tools/developer-command-prompt-for-vs.md) topic.</span></span> 

<span data-ttu-id="e7a52-106">Standart bir komut istemi penceresi kullanırsanız, çağırabilirsiniz önce yolunuzu değiştirmelisiniz *csc.exe* bilgisayarınızdaki herhangi bir alt dizinden.</span><span class="sxs-lookup"><span data-stu-id="e7a52-106">If you use a standard Command Prompt window, you must adjust your path before you can invoke *csc.exe* from any subdirectory on your computer.</span></span> <span data-ttu-id="e7a52-107">Ayrıca çalıştırmalısınız *vsvars32.bat* komut satırı derlemeleri desteklemek için uygun ortam değişkenlerini ayarlamak için.</span><span class="sxs-lookup"><span data-stu-id="e7a52-107">You also must run *vsvars32.bat* to set the appropriate environment variables to support command-line builds.</span></span> <span data-ttu-id="e7a52-108">Hakkında daha fazla bilgi için *vsvars32.bat*, bulma ve görmek hakkında yönergeler de dahil olmak üzere [nasıl yapılır: ortam değişkenleri ayarlamak için Visual Studio komut satırı](../../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md).</span><span class="sxs-lookup"><span data-stu-id="e7a52-108">For more information about *vsvars32.bat*, including instructions for how to find and run it, see [How to: Set Environment Variables for the Visual Studio Command Line](../../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md).</span></span>

<span data-ttu-id="e7a52-109">Yalnızca sahip bir bilgisayarda çalışırken [!INCLUDE[winsdklong](~/includes/winsdklong-md.md)], C# Derleyici adresindeki kullanabilirsiniz **SDK Komut İstemi**, uyguladığınız **Microsoft .NET Framework SDK** menü seçeneği.</span><span class="sxs-lookup"><span data-stu-id="e7a52-109">If you're working on a computer that has only the [!INCLUDE[winsdklong](~/includes/winsdklong-md.md)], you can use the C# compiler at the **SDK Command Prompt**, which you open from the **Microsoft .NET Framework SDK** menu option.</span></span>

<span data-ttu-id="e7a52-110">Ayrıca C# programlarını program aracılığıyla oluşturmak için MSBuild'i kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e7a52-110">You can also use MSBuild to build C# programs programmatically.</span></span> <span data-ttu-id="e7a52-111">Daha fazla bilgi için bkz: [MSBuild](/visualstudio/msbuild/msbuild).</span><span class="sxs-lookup"><span data-stu-id="e7a52-111">For more information, see [MSBuild](/visualstudio/msbuild/msbuild).</span></span>

<span data-ttu-id="e7a52-112">*Csc.exe* yürütülebilir dosya genellikle bulunan Microsoft.NET\Framework\\*\<sürüm >* klasörü altında *Windows* Dizin.</span><span class="sxs-lookup"><span data-stu-id="e7a52-112">The *csc.exe* executable file usually is located in the Microsoft.NET\Framework\\*\<Version>* folder under the *Windows* directory.</span></span> <span data-ttu-id="e7a52-113">Bu dosyanın yeri, belirli bir bilgisayarın tam yapılandırmasına bağlı olarak değişebilir.</span><span class="sxs-lookup"><span data-stu-id="e7a52-113">Its location might vary depending on the exact configuration of a particular computer.</span></span> <span data-ttu-id="e7a52-114">Bilgisayarınızda .NET Framework'ün birden fazla sürümü yüklüyse, bu dosyanın birden fazla sürümünü bulacaksınız.</span><span class="sxs-lookup"><span data-stu-id="e7a52-114">If more than one version of the .NET Framework is installed on your computer, you'll find multiple versions of this file.</span></span> <span data-ttu-id="e7a52-115">Yüklemeler hakkında daha fazla bilgi için bkz: [nasıl yapılır: hangi .NET Framework sürümlerinin yüklü olduğunu belirleme](../../../framework/migration-guide/how-to-determine-which-versions-are-installed.md).</span><span class="sxs-lookup"><span data-stu-id="e7a52-115">For more information about such installations, see [How to: determine which versions of the .NET Framework are installed](../../../framework/migration-guide/how-to-determine-which-versions-are-installed.md).</span></span>

> [!TIP]
>  <span data-ttu-id="e7a52-116">Visual Studio IDE kullanarak bir projeyi derlerken görüntüleyebileceğiniz **csc** komut ve onun ilişkili derleyici seçenekleri **çıkış** penceresi.</span><span class="sxs-lookup"><span data-stu-id="e7a52-116">When you build a project by using the Visual Studio IDE, you can display the **csc** command and its associated compiler options in the **Output** window.</span></span> <span data-ttu-id="e7a52-117">Bu bilgileri görüntülemek için'ndaki yönergeleri izleyin [nasıl yapılır: görünümü, kaydetme ve yapı günlük dosyalarını Yapılandır](/visualstudio/ide/how-to-view-save-and-configure-build-log-files#to-change-the-amount-of-information-included-in-the-build-log) günlük verilerini ayrıntı düzeyini değiştirmek için **Normal** veya **ayrıntılı**.</span><span class="sxs-lookup"><span data-stu-id="e7a52-117">To display this information, follow the instructions in [How to: View, Save, and Configure Build Log Files](/visualstudio/ide/how-to-view-save-and-configure-build-log-files#to-change-the-amount-of-information-included-in-the-build-log) to change the verbosity level of the log data to **Normal** or **Detailed**.</span></span> <span data-ttu-id="e7a52-118">Projenizi yeniden oluşturduktan sonra arama **çıkış** penceresi **csc** C# Derleyici çağırma bulunamıyor.</span><span class="sxs-lookup"><span data-stu-id="e7a52-118">After you rebuild your project, search the **Output** window for **csc** to find the invocation of the C# compiler.</span></span>

 <span data-ttu-id="e7a52-119">**Bu konudaki**</span><span class="sxs-lookup"><span data-stu-id="e7a52-119">**In this topic**</span></span>

- [<span data-ttu-id="e7a52-120">Komut satırı sözdizimi için kurallar</span><span class="sxs-lookup"><span data-stu-id="e7a52-120">Rules for command-line syntax</span></span>](#-rules-for-command-line-syntax-for-the-c-compiler)

- [<span data-ttu-id="e7a52-121">Örnek komut satırları</span><span class="sxs-lookup"><span data-stu-id="e7a52-121">Sample command lines</span></span>](#sample-command-lines-for-the-c-compiler)

- [<span data-ttu-id="e7a52-122">C# Derleyici ve C++ Derleyici çıktısı arasındaki farklar</span><span class="sxs-lookup"><span data-stu-id="e7a52-122">Differences between C# compiler and C++ compiler output</span></span>](#differences-between-c-compiler-and-c-compiler-output)

## <a name="rules-for-command-line-syntax-for-the-c-compiler"></a><span data-ttu-id="e7a52-123">C# derleyici komut satırı sözdizimi için kurallar</span><span class="sxs-lookup"><span data-stu-id="e7a52-123">Rules for command-line syntax for the C# compiler</span></span>

<span data-ttu-id="e7a52-124">C# Derleyici işletim sistemi komut satırında belirtilen bağımsız değişkenler yorumlar aşağıdaki kuralları kullanır:</span><span class="sxs-lookup"><span data-stu-id="e7a52-124">The C# compiler uses the following rules when it interprets arguments given on the operating system command line:</span></span>

- <span data-ttu-id="e7a52-125">Bağımsız değişkenler, bir boşluk veya bir sekme olduğu boşluk tarafından sınırlandırılır.</span><span class="sxs-lookup"><span data-stu-id="e7a52-125">Arguments are delimited by white space, which is either a space or a tab.</span></span>

- <span data-ttu-id="e7a52-126">Şapka (^) karakteri kaçış karakteri veya sınırlayıcı tanınmıyor.</span><span class="sxs-lookup"><span data-stu-id="e7a52-126">The caret character (^) is not recognized as an escape character or delimiter.</span></span> <span data-ttu-id="e7a52-127">İçin geçmeden önce karakter işletim sisteminde komut satırı ayrıştırıcı tarafından işlenir `argv` program dizisinde.</span><span class="sxs-lookup"><span data-stu-id="e7a52-127">The character is handled by the command-line parser in the operating system before it's passed to the `argv` array in the program.</span></span>

- <span data-ttu-id="e7a52-128">Çift tırnak işaretleri ("dize") içine bir dize kapsamında yer alan boşluk bakılmaksızın tek bir bağımsız değişken olarak yorumlanır.</span><span class="sxs-lookup"><span data-stu-id="e7a52-128">A string enclosed in double quotation marks ("string") is interpreted as a single argument, regardless of white space that is contained within.</span></span> <span data-ttu-id="e7a52-129">Tırnak içine alınan bir dizeyi bir bağımsız değişken katıştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="e7a52-129">A quoted string can be embedded in an argument.</span></span>

- <span data-ttu-id="e7a52-130">Çift tırnak işareti eğik çizgi işaretinden (\\") değişmez değer çift tırnak işareti karakteri (") olarak yorumlanır.</span><span class="sxs-lookup"><span data-stu-id="e7a52-130">A double quotation mark preceded by a backslash (\\") is interpreted as a literal double quotation mark character (").</span></span>

- <span data-ttu-id="e7a52-131">Bunlar hemen çift tırnak işareti koyun sürece ters eğik çizgi tam anlamıyla, yorumlanır.</span><span class="sxs-lookup"><span data-stu-id="e7a52-131">Backslashes are interpreted literally, unless they immediately precede a double quotation mark.</span></span>

- <span data-ttu-id="e7a52-132">Ters eğik çizgi çift sayıda çift tırnak işareti izlediyseniz, bir ters eğik çizgi içine `argv` dizi her çift ters eğik çizgi ve çift tırnak işareti dize ayırıcı olarak yorumlanır.</span><span class="sxs-lookup"><span data-stu-id="e7a52-132">If an even number of backslashes is followed by a double quotation mark, one backslash is put in the `argv` array for every pair of backslashes, and the double quotation mark is interpreted as a string delimiter.</span></span>

- <span data-ttu-id="e7a52-133">Ters eğik çizgi tek sayıda çift tırnak işareti izlediyseniz, bir ters eğik çizgi içine `argv` dizi her çift ters eğik çizgi ve çift tırnak işareti "önce" kalan ters eğik çizgi tarafından.</span><span class="sxs-lookup"><span data-stu-id="e7a52-133">If an odd number of backslashes is followed by a double quotation mark, one backslash is put in the `argv` array for every pair of backslashes, and the double quotation mark is "escaped" by the remaining backslash.</span></span> <span data-ttu-id="e7a52-134">Bu sabit çift tırnak içinde eklenecek işareti (") neden olan `argv`.</span><span class="sxs-lookup"><span data-stu-id="e7a52-134">This causes a literal double quotation mark (") to be added in `argv`.</span></span>

## <a name="sample-command-lines-for-the-c-compiler"></a><span data-ttu-id="e7a52-135">C# derleyici için örnek komut satırları</span><span class="sxs-lookup"><span data-stu-id="e7a52-135">Sample command lines for the C# compiler</span></span>

- <span data-ttu-id="e7a52-136">Derlenen *File.cs* oluşturan *File.exe*:</span><span class="sxs-lookup"><span data-stu-id="e7a52-136">Compiles *File.cs* producing *File.exe*:</span></span>

```console
csc File.cs 
```

- <span data-ttu-id="e7a52-137">Derlenen *File.cs* oluşturan *File.dll*:</span><span class="sxs-lookup"><span data-stu-id="e7a52-137">Compiles *File.cs* producing *File.dll*:</span></span>

```console
csc -target:library File.cs
```

- <span data-ttu-id="e7a52-138">Derlenen *File.cs* ve oluşturur *My.exe*:</span><span class="sxs-lookup"><span data-stu-id="e7a52-138">Compiles *File.cs* and creates *My.exe*:</span></span>

```console
csc -out:My.exe File.cs
```

- <span data-ttu-id="e7a52-139">Tüm C# dosyalarını geçerli dizinde iyileştirmeler etkinleştirilerek derler ve hata ayıklama simgesi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e7a52-139">Compiles all the C# files in the current directory with optimizations enabled and defines the DEBUG symbol.</span></span> <span data-ttu-id="e7a52-140">Çıktı *File2.exe*:</span><span class="sxs-lookup"><span data-stu-id="e7a52-140">The output is *File2.exe*:</span></span>

```console
csc -define:DEBUG -optimize -out:File2.exe *.cs
```

- <span data-ttu-id="e7a52-141">Tüm C# geçerli dizindeki dosyaları bir hata ayıklama sürümü üreten derleyen *File2.dll*.</span><span class="sxs-lookup"><span data-stu-id="e7a52-141">Compiles all the C# files in the current directory producing a debug version of *File2.dll*.</span></span> <span data-ttu-id="e7a52-142">Logo ve uyarı görüntülenir:</span><span class="sxs-lookup"><span data-stu-id="e7a52-142">No logo and no warnings are displayed:</span></span>

```console
csc -target:library -out:File2.dll -warn:0 -nologo -debug *.cs
```

- <span data-ttu-id="e7a52-143">Tüm C# dosyalarını geçerli dizine derler *Something.xyz* (DLL):</span><span class="sxs-lookup"><span data-stu-id="e7a52-143">Compiles all the C# files in the current directory to *Something.xyz* (a DLL):</span></span>

```console
csc -target:library -out:Something.xyz *.cs
```

## <a name="differences-between-c-compiler-and-c-compiler-output"></a><span data-ttu-id="e7a52-144">C# Derleyici ve C++ Derleyici çıktısı arasındaki farklar</span><span class="sxs-lookup"><span data-stu-id="e7a52-144">Differences between C# compiler and C++ compiler output</span></span>
<span data-ttu-id="e7a52-145">Hiçbir nesne vardır (*.obj*) dosyaları oluşturan C# Derleyici çağrılması sonucunda; çıktı dosyaları doğrudan oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="e7a52-145">There are no object (*.obj*) files created as a result of invoking the C# compiler; output files are created directly.</span></span> <span data-ttu-id="e7a52-146">Bunun sonucunda, C# Derleyici bir bağlayıcı gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="e7a52-146">As a result of this, the C# compiler does not need a linker.</span></span>

## <a name="see-also"></a><span data-ttu-id="e7a52-147">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e7a52-147">See also</span></span>
 [<span data-ttu-id="e7a52-148">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="e7a52-148">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="e7a52-149">Alfabetik Listelenmiş C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="e7a52-149">C# Compiler Options Listed Alphabetically</span></span>](../../../csharp/language-reference/compiler-options/listed-alphabetically.md)  
 [<span data-ttu-id="e7a52-150">Kategorilere Göre Listelenen C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="e7a52-150">C# Compiler Options Listed by Category</span></span>](../../../csharp/language-reference/compiler-options/listed-by-category.md)  
 [<span data-ttu-id="e7a52-151">Ana() ve Komut Satırı Bağımsız Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="e7a52-151">Main() and Command-Line Arguments</span></span>](../../../csharp/programming-guide/main-and-command-args/index.md)  
 [<span data-ttu-id="e7a52-152">Komut Satırı Bağımsız Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="e7a52-152">Command-Line Arguments</span></span>](../../../csharp/programming-guide/main-and-command-args/command-line-arguments.md)  
 [<span data-ttu-id="e7a52-153">Nasıl yapılır: komut satırı bağımsız değişkenlerini görüntüleme</span><span class="sxs-lookup"><span data-stu-id="e7a52-153">How to: Display Command-Line Arguments</span></span>](../../../csharp/programming-guide/main-and-command-args/how-to-display-command-line-arguments.md)  
 [<span data-ttu-id="e7a52-154">Nasıl yapılır: foreach Kullanarak Komut Satırı Bağımsız Değişkenlerine Erişme</span><span class="sxs-lookup"><span data-stu-id="e7a52-154">How to: Access Command-Line Arguments Using foreach</span></span>](../../../csharp/programming-guide/main-and-command-args/how-to-access-command-line-arguments-using-foreach.md)  
 [<span data-ttu-id="e7a52-155">Ana() Dönüş Değerleri</span><span class="sxs-lookup"><span data-stu-id="e7a52-155">Main() Return Values</span></span>](../../../csharp/programming-guide/main-and-command-args/main-return-values.md)
