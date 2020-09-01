---
description: csc.exe ile komut satırı oluşturma
title: csc.exe ile komut satırı oluşturma
ms.date: 04/19/2017
helpviewer_keywords:
- builds [C#]
- command line [C#]
ms.assetid: 66e70056-dd20-453c-a9b3-507e0478b015
ms.openlocfilehash: 9ffd164602862fce7f5e4f0982d3eda7cb403e60
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89125936"
---
# <a name="command-line-build-with-cscexe"></a><span data-ttu-id="8363f-103">csc.exe ile komut satırı oluşturma</span><span class="sxs-lookup"><span data-stu-id="8363f-103">Command-line build with csc.exe</span></span>

<span data-ttu-id="8363f-104">Komut istemine yürütülebilir dosyasının adını (*csc.exe*) yazarak C# derleyicisini çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8363f-104">You can invoke the C# compiler by typing the name of its executable file (*csc.exe*) at a command prompt.</span></span>

<span data-ttu-id="8363f-105">**Visual Studio için geliştirici komut istemi** kullanıyorsanız, tüm gerekli ortam değişkenleri sizin için ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="8363f-105">If you use the **Developer Command Prompt for Visual Studio** window, all the necessary environment variables are set for you.</span></span> <span data-ttu-id="8363f-106">Bu araca erişme hakkında daha fazla bilgi için bkz. [Visual Studio için geliştirici komut istemi](../../../framework/tools/developer-command-prompt-for-vs.md) konusu.</span><span class="sxs-lookup"><span data-stu-id="8363f-106">For information on how to access this tool, see the [Developer Command Prompt for Visual Studio](../../../framework/tools/developer-command-prompt-for-vs.md) topic.</span></span>

<span data-ttu-id="8363f-107">Standart bir komut Istemi penceresi kullanıyorsanız, bilgisayarınızdaki herhangi bir alt dizinden *csc.exe* çağırabilmeniz için önce yolunu ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="8363f-107">If you use a standard Command Prompt window, you must adjust your path before you can invoke *csc.exe* from any subdirectory on your computer.</span></span> <span data-ttu-id="8363f-108">Ayrıca, komut satırı yapılarını desteklemek için uygun ortam değişkenlerini ayarlamak üzere *VsDevCmd.bat* çalıştırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="8363f-108">You also must run *VsDevCmd.bat* to set the appropriate environment variables to support command-line builds.</span></span> <span data-ttu-id="8363f-109">*VsDevCmd.bat*hakkında daha fazla bilgi edinmek için, bkz. [Visual Studio komut satırı için ortam değişkenlerini ayarlama](./how-to-set-environment-variables-for-the-visual-studio-command-line.md).</span><span class="sxs-lookup"><span data-stu-id="8363f-109">For more information about *VsDevCmd.bat*, including instructions for how to find and run it, see [How to set environment variables for the Visual Studio Command Line](./how-to-set-environment-variables-for-the-visual-studio-command-line.md).</span></span>

<span data-ttu-id="8363f-110">Yalnızca Windows yazılım geliştirme seti (SDK) olan bir bilgisayarda çalışıyorsanız, C# derleyicisini **Microsoft .NET Framework SDK** menü seçeneğinden açtığınız **SDK komut istemi**' nde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8363f-110">If you're working on a computer that has only the Windows Software Development Kit (SDK), you can use the C# compiler at the **SDK Command Prompt**, which you open from the **Microsoft .NET Framework SDK** menu option.</span></span>

<span data-ttu-id="8363f-111">Ayrıca C# programlarını program aracılığıyla oluşturmak için MSBuild'i kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8363f-111">You can also use MSBuild to build C# programs programmatically.</span></span> <span data-ttu-id="8363f-112">Daha fazla bilgi için bkz. [MSBuild](/visualstudio/msbuild/msbuild).</span><span class="sxs-lookup"><span data-stu-id="8363f-112">For more information, see [MSBuild](/visualstudio/msbuild/msbuild).</span></span>

<span data-ttu-id="8363f-113">*csc.exe* çalıştırılabilir dosya genellikle \\ *\<Version>* *Windows* dizini altındaki Microsoft. NET\Framework klasöründe bulunur.</span><span class="sxs-lookup"><span data-stu-id="8363f-113">The *csc.exe* executable file usually is located in the Microsoft.NET\Framework\\*\<Version>* folder under the *Windows* directory.</span></span> <span data-ttu-id="8363f-114">Bu dosyanın yeri, belirli bir bilgisayarın tam yapılandırmasına bağlı olarak değişebilir.</span><span class="sxs-lookup"><span data-stu-id="8363f-114">Its location might vary depending on the exact configuration of a particular computer.</span></span> <span data-ttu-id="8363f-115">Bilgisayarınızda .NET Framework'ün birden fazla sürümü yüklüyse, bu dosyanın birden fazla sürümünü bulacaksınız.</span><span class="sxs-lookup"><span data-stu-id="8363f-115">If more than one version of the .NET Framework is installed on your computer, you'll find multiple versions of this file.</span></span> <span data-ttu-id="8363f-116">Bu tür yüklemeler hakkında daha fazla bilgi için bkz. [nasıl yapılır: hangi .NET Framework sürümlerinin yüklendiğini belirleme](../../../framework/migration-guide/how-to-determine-which-versions-are-installed.md).</span><span class="sxs-lookup"><span data-stu-id="8363f-116">For more information about such installations, see [How to: determine which versions of the .NET Framework are installed](../../../framework/migration-guide/how-to-determine-which-versions-are-installed.md).</span></span>

> [!TIP]
> <span data-ttu-id="8363f-117">Visual Studio IDE kullanarak bir proje oluşturduğunuzda, **CSC** komutunu ve ilgili derleyici seçeneklerini **Çıkış** penceresinde görüntüleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8363f-117">When you build a project by using the Visual Studio IDE, you can display the **csc** command and its associated compiler options in the **Output** window.</span></span> <span data-ttu-id="8363f-118">Bu bilgileri görüntülemek için nasıl yapılır: günlük verilerinin ayrıntı düzeyini **normal** veya **ayrıntılı**olarak değiştirmek üzere [derleme günlüğü dosyalarını görüntüleme, kaydetme ve yapılandırma](/visualstudio/ide/how-to-view-save-and-configure-build-log-files#to-change-the-amount-of-information-included-in-the-build-log) konusundaki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="8363f-118">To display this information, follow the instructions in [How to: View, Save, and Configure Build Log Files](/visualstudio/ide/how-to-view-save-and-configure-build-log-files#to-change-the-amount-of-information-included-in-the-build-log) to change the verbosity level of the log data to **Normal** or **Detailed**.</span></span> <span data-ttu-id="8363f-119">Projenizi yeniden oluşturduktan sonra, C# derleyicisinin çağrılmasını bulmak için **CSC** **Çıkış** penceresinde arama yapın.</span><span class="sxs-lookup"><span data-stu-id="8363f-119">After you rebuild your project, search the **Output** window for **csc** to find the invocation of the C# compiler.</span></span>

 <span data-ttu-id="8363f-120">**Bu konuda**</span><span class="sxs-lookup"><span data-stu-id="8363f-120">**In this topic**</span></span>

- [<span data-ttu-id="8363f-121">Komut satırı söz dizimi için kurallar</span><span class="sxs-lookup"><span data-stu-id="8363f-121">Rules for command-line syntax</span></span>](#rules-for-command-line-syntax-for-the-c-compiler)

- [<span data-ttu-id="8363f-122">Örnek komut satırları</span><span class="sxs-lookup"><span data-stu-id="8363f-122">Sample command lines</span></span>](#sample-command-lines-for-the-c-compiler)

- [<span data-ttu-id="8363f-123">C# derleyicisi ve C++ derleyici çıkışı arasındaki farklılıklar</span><span class="sxs-lookup"><span data-stu-id="8363f-123">Differences between C# compiler and C++ compiler output</span></span>](#differences-between-c-compiler-and-c-compiler-output)

## <a name="rules-for-command-line-syntax-for-the-c-compiler"></a><span data-ttu-id="8363f-124">C# derleyicisi için komut satırı söz dizimi kuralları</span><span class="sxs-lookup"><span data-stu-id="8363f-124">Rules for command-line syntax for the C# compiler</span></span>

<span data-ttu-id="8363f-125">C# derleyicisi, işletim sistemi komut satırında verilen bağımsız değişkenleri yorumladığı zaman aşağıdaki kuralları kullanır:</span><span class="sxs-lookup"><span data-stu-id="8363f-125">The C# compiler uses the following rules when it interprets arguments given on the operating system command line:</span></span>

- <span data-ttu-id="8363f-126">Bağımsız değişkenler boşluk veya sekme olan boşluk ile sınırlandırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="8363f-126">Arguments are delimited by white space, which is either a space or a tab.</span></span>

- <span data-ttu-id="8363f-127">Giriş işareti karakteri (^) bir kaçış karakteri veya sınırlayıcı olarak tanınmıyor.</span><span class="sxs-lookup"><span data-stu-id="8363f-127">The caret character (^) is not recognized as an escape character or delimiter.</span></span> <span data-ttu-id="8363f-128">Karakter, programdaki diziye geçirilmeden önce işletim sistemindeki komut satırı ayrıştırıcısı tarafından işlenir `argv` .</span><span class="sxs-lookup"><span data-stu-id="8363f-128">The character is handled by the command-line parser in the operating system before it's passed to the `argv` array in the program.</span></span>

- <span data-ttu-id="8363f-129">Çift tırnak işaretleri ("String") içine alınmış bir dize, içinde yer alan boşluklardan bağımsız olarak tek bir bağımsız değişken olarak yorumlanır.</span><span class="sxs-lookup"><span data-stu-id="8363f-129">A string enclosed in double quotation marks ("string") is interpreted as a single argument, regardless of white space that is contained within.</span></span> <span data-ttu-id="8363f-130">Tırnak içine alınmış bir dize bir bağımsız değişkene gömülebilir.</span><span class="sxs-lookup"><span data-stu-id="8363f-130">A quoted string can be embedded in an argument.</span></span>

- <span data-ttu-id="8363f-131">Önünde ters eğik çizgi (") olan bir çift tırnak işareti \\ , sabit değer çift tırnak işareti karakteri (") olarak yorumlanır.</span><span class="sxs-lookup"><span data-stu-id="8363f-131">A double quotation mark preceded by a backslash (\\") is interpreted as a literal double quotation mark character (").</span></span>

- <span data-ttu-id="8363f-132">Ters eğik çizgiler, bir çift tırnak işaretinden hemen önce gelmedikleri takdirde tam olarak yorumlanır.</span><span class="sxs-lookup"><span data-stu-id="8363f-132">Backslashes are interpreted literally, unless they immediately precede a double quotation mark.</span></span>

- <span data-ttu-id="8363f-133">İki ters eğik çizgi daha sonra çift tırnak işareti kullanıyorsa, bir ters eğik çizgi `argv` her çift eğik çizgi için diziye konur ve çift tırnak işareti dize sınırlayıcısı olarak yorumlanır.</span><span class="sxs-lookup"><span data-stu-id="8363f-133">If an even number of backslashes is followed by a double quotation mark, one backslash is put in the `argv` array for every pair of backslashes, and the double quotation mark is interpreted as a string delimiter.</span></span>

- <span data-ttu-id="8363f-134">Tek bir ters eğik çizgiden sonra çift tırnak işareti varsa, her ters eğik çizgi çifti için bir ters eğik çizgi konur `argv` ve çift tırnak işareti kalan ters eğik çizgi için "kaçışlı" olur.</span><span class="sxs-lookup"><span data-stu-id="8363f-134">If an odd number of backslashes is followed by a double quotation mark, one backslash is put in the `argv` array for every pair of backslashes, and the double quotation mark is "escaped" by the remaining backslash.</span></span> <span data-ttu-id="8363f-135">Bu, içinde bir sabit değer çift tırnak işareti (") eklenmesine neden olur `argv` .</span><span class="sxs-lookup"><span data-stu-id="8363f-135">This causes a literal double quotation mark (") to be added in `argv`.</span></span>

## <a name="sample-command-lines-for-the-c-compiler"></a><span data-ttu-id="8363f-136">C# derleyicisi için örnek komut satırları</span><span class="sxs-lookup"><span data-stu-id="8363f-136">Sample command lines for the C# compiler</span></span>

- <span data-ttu-id="8363f-137">*File.cs* üreten *File.exe*derler:</span><span class="sxs-lookup"><span data-stu-id="8363f-137">Compiles *File.cs* producing *File.exe*:</span></span>

  ```console
  csc File.cs
  ```

- <span data-ttu-id="8363f-138">*File.cs* üreten *File.dll*derler:</span><span class="sxs-lookup"><span data-stu-id="8363f-138">Compiles *File.cs* producing *File.dll*:</span></span>

  ```console
  csc -target:library File.cs
  ```

- <span data-ttu-id="8363f-139">*File.cs* derler ve *My.exe*oluşturur:</span><span class="sxs-lookup"><span data-stu-id="8363f-139">Compiles *File.cs* and creates *My.exe*:</span></span>

  ```console
  csc -out:My.exe File.cs
  ```

- <span data-ttu-id="8363f-140">Geçerli dizindeki tüm C# dosyalarını iyileştirmeler etkin olacak şekilde derler ve hata ayıklama sembolünü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="8363f-140">Compiles all the C# files in the current directory with optimizations enabled and defines the DEBUG symbol.</span></span> <span data-ttu-id="8363f-141">Çıktı *File2.exe*:</span><span class="sxs-lookup"><span data-stu-id="8363f-141">The output is *File2.exe*:</span></span>

  ```console
  csc -define:DEBUG -optimize -out:File2.exe *.cs
  ```

- <span data-ttu-id="8363f-142">Geçerli dizindeki tüm C# dosyalarını, *File2.dll*hata ayıklama sürümü üreten şekilde derler.</span><span class="sxs-lookup"><span data-stu-id="8363f-142">Compiles all the C# files in the current directory producing a debug version of *File2.dll*.</span></span> <span data-ttu-id="8363f-143">Amblem yoktur ve hiçbir uyarı gösterilmez:</span><span class="sxs-lookup"><span data-stu-id="8363f-143">No logo and no warnings are displayed:</span></span>

  ```console
  csc -target:library -out:File2.dll -warn:0 -nologo -debug *.cs
  ```

- <span data-ttu-id="8363f-144">Geçerli dizindeki tüm C# dosyalarını bir *. xyz* (bir dll) olarak derler:</span><span class="sxs-lookup"><span data-stu-id="8363f-144">Compiles all the C# files in the current directory to *Something.xyz* (a DLL):</span></span>

  ```console
  csc -target:library -out:Something.xyz *.cs
  ```

## <a name="differences-between-c-compiler-and-c-compiler-output"></a><span data-ttu-id="8363f-145">C# derleyicisi ve C++ derleyici çıkışı arasındaki farklılıklar</span><span class="sxs-lookup"><span data-stu-id="8363f-145">Differences between C# compiler and C++ compiler output</span></span>

<span data-ttu-id="8363f-146">C# derleyicisini çağırma sonucu olarak oluşturulan herhangi bir nesne (*. obj*) dosyası yoktur; çıktı dosyaları doğrudan oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="8363f-146">There are no object (*.obj*) files created as a result of invoking the C# compiler; output files are created directly.</span></span> <span data-ttu-id="8363f-147">Bunun sonucunda, C# derleyicisinin bir bağlayıcıya ihtiyacı yoktur.</span><span class="sxs-lookup"><span data-stu-id="8363f-147">As a result of this, the C# compiler does not need a linker.</span></span>

## <a name="see-also"></a><span data-ttu-id="8363f-148">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8363f-148">See also</span></span>

- [<span data-ttu-id="8363f-149">C# derleyici seçenekleri</span><span class="sxs-lookup"><span data-stu-id="8363f-149">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="8363f-150">Alfabetik Listelenmiş C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="8363f-150">C# Compiler Options Listed Alphabetically</span></span>](./listed-alphabetically.md)
- [<span data-ttu-id="8363f-151">Kategorilere Göre Listelenen C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="8363f-151">C# Compiler Options Listed by Category</span></span>](./listed-by-category.md)
- [<span data-ttu-id="8363f-152">Main () ve komut satırı bağımsız değişkenleri</span><span class="sxs-lookup"><span data-stu-id="8363f-152">Main() and Command-Line Arguments</span></span>](../../programming-guide/main-and-command-args/index.md)
- [<span data-ttu-id="8363f-153">Komut Satırı Bağımsız Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="8363f-153">Command-Line Arguments</span></span>](../../programming-guide/main-and-command-args/command-line-arguments.md)
- [<span data-ttu-id="8363f-154">Komut satırı bağımsız değişkenlerini görüntüleme</span><span class="sxs-lookup"><span data-stu-id="8363f-154">How to display command-line arguments</span></span>](../../programming-guide/main-and-command-args/how-to-display-command-line-arguments.md)
- [<span data-ttu-id="8363f-155">Ana() Dönüş Değerleri</span><span class="sxs-lookup"><span data-stu-id="8363f-155">Main() Return Values</span></span>](../../programming-guide/main-and-command-args/main-return-values.md)
