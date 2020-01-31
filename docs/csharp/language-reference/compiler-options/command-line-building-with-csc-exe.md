---
title: Csc. exe ile komut satırı oluşturma
ms.date: 04/19/2017
helpviewer_keywords:
- builds [C#]
- command line [C#]
ms.assetid: 66e70056-dd20-453c-a9b3-507e0478b015
ms.openlocfilehash: f692e66672b1804a309c6ac04c158af948a1b1ab
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789866"
---
# <a name="command-line-build-with-cscexe"></a><span data-ttu-id="8e69f-102">Csc. exe ile komut satırı oluşturma</span><span class="sxs-lookup"><span data-stu-id="8e69f-102">Command-line build with csc.exe</span></span>

<span data-ttu-id="8e69f-103">Bir komut isteminde yürütülebilir C# dosyasının adını (*CSC. exe*) yazarak derleyiciyi çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8e69f-103">You can invoke the C# compiler by typing the name of its executable file (*csc.exe*) at a command prompt.</span></span>

<span data-ttu-id="8e69f-104">**Visual Studio için geliştirici komut istemi** kullanıyorsanız, tüm gerekli ortam değişkenleri sizin için ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="8e69f-104">If you use the **Developer Command Prompt for Visual Studio** window, all the necessary environment variables are set for you.</span></span> <span data-ttu-id="8e69f-105">Bu araca erişme hakkında daha fazla bilgi için bkz. [Visual Studio için geliştirici komut istemi](../../../framework/tools/developer-command-prompt-for-vs.md) konusu.</span><span class="sxs-lookup"><span data-stu-id="8e69f-105">For information on how to access this tool, see the [Developer Command Prompt for Visual Studio](../../../framework/tools/developer-command-prompt-for-vs.md) topic.</span></span>

<span data-ttu-id="8e69f-106">Standart bir komut Istemi penceresi kullanıyorsanız, bilgisayarınızdaki herhangi bir alt dizinden *CSC. exe* ' yi çağırabilmeniz için önce yolunu ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="8e69f-106">If you use a standard Command Prompt window, you must adjust your path before you can invoke *csc.exe* from any subdirectory on your computer.</span></span> <span data-ttu-id="8e69f-107">Ayrıca, komut satırı yapılarını desteklemek üzere uygun ortam değişkenlerini ayarlamak için *vsvars32. bat* dosyasını çalıştırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="8e69f-107">You also must run *vsvars32.bat* to set the appropriate environment variables to support command-line builds.</span></span> <span data-ttu-id="8e69f-108">*Vsvars32. bat*hakkında daha fazla bilgi için, bkz. [Visual Studio komut satırı için ortam değişkenlerini ayarlama](./how-to-set-environment-variables-for-the-visual-studio-command-line.md).</span><span class="sxs-lookup"><span data-stu-id="8e69f-108">For more information about *vsvars32.bat*, including instructions for how to find and run it, see [How to set environment variables for the Visual Studio Command Line](./how-to-set-environment-variables-for-the-visual-studio-command-line.md).</span></span>

<span data-ttu-id="8e69f-109">Yalnızca Windows yazılım geliştirme seti (SDK) olan bir bilgisayarda çalışıyorsanız, C# **Microsoft .NET Framework SDK** menü seçeneğinden açtığınız **SDK komut isteminde**derleyiciyi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8e69f-109">If you're working on a computer that has only the Windows Software Development Kit (SDK), you can use the C# compiler at the **SDK Command Prompt**, which you open from the **Microsoft .NET Framework SDK** menu option.</span></span>

<span data-ttu-id="8e69f-110">Ayrıca C# programlarını program aracılığıyla oluşturmak için MSBuild'i kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8e69f-110">You can also use MSBuild to build C# programs programmatically.</span></span> <span data-ttu-id="8e69f-111">Daha fazla bilgi için bkz. [MSBuild](/visualstudio/msbuild/msbuild).</span><span class="sxs-lookup"><span data-stu-id="8e69f-111">For more information, see [MSBuild](/visualstudio/msbuild/msbuild).</span></span>

<span data-ttu-id="8e69f-112">*CSC. exe* yürütülebilir dosyası genellikle *Windows* dizini altındaki Microsoft. NET\Framework\\ *\<sürüm >* klasöründedir.</span><span class="sxs-lookup"><span data-stu-id="8e69f-112">The *csc.exe* executable file usually is located in the Microsoft.NET\Framework\\*\<Version>* folder under the *Windows* directory.</span></span> <span data-ttu-id="8e69f-113">Bu dosyanın yeri, belirli bir bilgisayarın tam yapılandırmasına bağlı olarak değişebilir.</span><span class="sxs-lookup"><span data-stu-id="8e69f-113">Its location might vary depending on the exact configuration of a particular computer.</span></span> <span data-ttu-id="8e69f-114">Bilgisayarınızda .NET Framework'ün birden fazla sürümü yüklüyse, bu dosyanın birden fazla sürümünü bulacaksınız.</span><span class="sxs-lookup"><span data-stu-id="8e69f-114">If more than one version of the .NET Framework is installed on your computer, you'll find multiple versions of this file.</span></span> <span data-ttu-id="8e69f-115">Bu tür yüklemeler hakkında daha fazla bilgi için bkz. [nasıl yapılır: hangi .NET Framework sürümlerinin yüklendiğini belirleme](../../../framework/migration-guide/how-to-determine-which-versions-are-installed.md).</span><span class="sxs-lookup"><span data-stu-id="8e69f-115">For more information about such installations, see [How to: determine which versions of the .NET Framework are installed](../../../framework/migration-guide/how-to-determine-which-versions-are-installed.md).</span></span>

> [!TIP]
> <span data-ttu-id="8e69f-116">Visual Studio IDE kullanarak bir proje oluşturduğunuzda, **CSC** komutunu ve ilgili derleyici seçeneklerini **Çıkış** penceresinde görüntüleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8e69f-116">When you build a project by using the Visual Studio IDE, you can display the **csc** command and its associated compiler options in the **Output** window.</span></span> <span data-ttu-id="8e69f-117">Bu bilgileri görüntülemek için nasıl yapılır: günlük verilerinin ayrıntı düzeyini **normal** veya **ayrıntılı**olarak değiştirmek üzere [derleme günlüğü dosyalarını görüntüleme, kaydetme ve yapılandırma](/visualstudio/ide/how-to-view-save-and-configure-build-log-files#to-change-the-amount-of-information-included-in-the-build-log) konusundaki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="8e69f-117">To display this information, follow the instructions in [How to: View, Save, and Configure Build Log Files](/visualstudio/ide/how-to-view-save-and-configure-build-log-files#to-change-the-amount-of-information-included-in-the-build-log) to change the verbosity level of the log data to **Normal** or **Detailed**.</span></span> <span data-ttu-id="8e69f-118">Projenizi yeniden oluşturduktan sonra, C# derleyicinin çağrılmasını bulmak Için **CSC** **Çıkış** penceresinde arama yapın.</span><span class="sxs-lookup"><span data-stu-id="8e69f-118">After you rebuild your project, search the **Output** window for **csc** to find the invocation of the C# compiler.</span></span>

 <span data-ttu-id="8e69f-119">**Bu konudaki**</span><span class="sxs-lookup"><span data-stu-id="8e69f-119">**In this topic**</span></span>

- [<span data-ttu-id="8e69f-120">Komut satırı söz dizimi için kurallar</span><span class="sxs-lookup"><span data-stu-id="8e69f-120">Rules for command-line syntax</span></span>](#rules-for-command-line-syntax-for-the-c-compiler)

- [<span data-ttu-id="8e69f-121">Örnek komut satırları</span><span class="sxs-lookup"><span data-stu-id="8e69f-121">Sample command lines</span></span>](#sample-command-lines-for-the-c-compiler)

- [<span data-ttu-id="8e69f-122">Derleyici ve C# C++ derleyici çıkışı arasındaki farklılıklar</span><span class="sxs-lookup"><span data-stu-id="8e69f-122">Differences between C# compiler and C++ compiler output</span></span>](#differences-between-c-compiler-and-c-compiler-output)

## <a name="rules-for-command-line-syntax-for-the-c-compiler"></a><span data-ttu-id="8e69f-123">C# Derleyici komut satırı sözdizimi için kurallar</span><span class="sxs-lookup"><span data-stu-id="8e69f-123">Rules for command-line syntax for the C# compiler</span></span>

<span data-ttu-id="8e69f-124">C# Derleyici, işletim sistemi komut satırında verilen bağımsız değişkenleri yorumladığı zaman aşağıdaki kuralları kullanır:</span><span class="sxs-lookup"><span data-stu-id="8e69f-124">The C# compiler uses the following rules when it interprets arguments given on the operating system command line:</span></span>

- <span data-ttu-id="8e69f-125">Bağımsız değişkenler boşluk veya sekme olan boşluk ile sınırlandırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="8e69f-125">Arguments are delimited by white space, which is either a space or a tab.</span></span>

- <span data-ttu-id="8e69f-126">Giriş işareti karakteri (^) bir kaçış karakteri veya sınırlayıcı olarak tanınmıyor.</span><span class="sxs-lookup"><span data-stu-id="8e69f-126">The caret character (^) is not recognized as an escape character or delimiter.</span></span> <span data-ttu-id="8e69f-127">Karakter, programdaki `argv` dizisine geçirilmeden önce, işletim sistemindeki komut satırı ayrıştırıcısı tarafından işlenir.</span><span class="sxs-lookup"><span data-stu-id="8e69f-127">The character is handled by the command-line parser in the operating system before it's passed to the `argv` array in the program.</span></span>

- <span data-ttu-id="8e69f-128">Çift tırnak işaretleri ("String") içine alınmış bir dize, içinde yer alan boşluklardan bağımsız olarak tek bir bağımsız değişken olarak yorumlanır.</span><span class="sxs-lookup"><span data-stu-id="8e69f-128">A string enclosed in double quotation marks ("string") is interpreted as a single argument, regardless of white space that is contained within.</span></span> <span data-ttu-id="8e69f-129">Tırnak içine alınmış bir dize bir bağımsız değişkene gömülebilir.</span><span class="sxs-lookup"><span data-stu-id="8e69f-129">A quoted string can be embedded in an argument.</span></span>

- <span data-ttu-id="8e69f-130">Önünde ters eğik çizgi (\\") olan çift tırnak işareti, sabit değer çift tırnak işareti karakteri (") olarak yorumlanır.</span><span class="sxs-lookup"><span data-stu-id="8e69f-130">A double quotation mark preceded by a backslash (\\") is interpreted as a literal double quotation mark character (").</span></span>

- <span data-ttu-id="8e69f-131">Ters eğik çizgiler, bir çift tırnak işaretinden hemen önce gelmedikleri takdirde tam olarak yorumlanır.</span><span class="sxs-lookup"><span data-stu-id="8e69f-131">Backslashes are interpreted literally, unless they immediately precede a double quotation mark.</span></span>

- <span data-ttu-id="8e69f-132">İki ters eğik çizgi daha sonra çift tırnak işaretiyle, bir ters eğik çizgi, her ters eğik çizgi çifti için `argv` dizisine konur ve çift tırnak işareti bir dize sınırlayıcısı olarak yorumlanır.</span><span class="sxs-lookup"><span data-stu-id="8e69f-132">If an even number of backslashes is followed by a double quotation mark, one backslash is put in the `argv` array for every pair of backslashes, and the double quotation mark is interpreted as a string delimiter.</span></span>

- <span data-ttu-id="8e69f-133">Tek bir ters eğik çizgiden sonra çift tırnak işareti varsa, her ters eğik çizgi çiftinin `argv` dizisine bir ters eğik çizgi konur ve çift tırnak işareti geri kalan ters eğik çizgi ile "kaçışdır".</span><span class="sxs-lookup"><span data-stu-id="8e69f-133">If an odd number of backslashes is followed by a double quotation mark, one backslash is put in the `argv` array for every pair of backslashes, and the double quotation mark is "escaped" by the remaining backslash.</span></span> <span data-ttu-id="8e69f-134">Bu, `argv`bir sabit değer çift tırnak işareti (") eklenmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="8e69f-134">This causes a literal double quotation mark (") to be added in `argv`.</span></span>

## <a name="sample-command-lines-for-the-c-compiler"></a><span data-ttu-id="8e69f-135">C# Derleyici için örnek komut satırları</span><span class="sxs-lookup"><span data-stu-id="8e69f-135">Sample command lines for the C# compiler</span></span>

- <span data-ttu-id="8e69f-136">*File.cs* üreten *dosya. exe*' yi derler:</span><span class="sxs-lookup"><span data-stu-id="8e69f-136">Compiles *File.cs* producing *File.exe*:</span></span>

  ```console
  csc File.cs
  ```

- <span data-ttu-id="8e69f-137">*File.cs* üreten *dosyayı derler. dll*:</span><span class="sxs-lookup"><span data-stu-id="8e69f-137">Compiles *File.cs* producing *File.dll*:</span></span>

  ```console
  csc -target:library File.cs
  ```

- <span data-ttu-id="8e69f-138">*File.cs* derler ve *My. exe dosyasını*oluşturur:</span><span class="sxs-lookup"><span data-stu-id="8e69f-138">Compiles *File.cs* and creates *My.exe*:</span></span>

  ```console
  csc -out:My.exe File.cs
  ```

- <span data-ttu-id="8e69f-139">Geçerli dizindeki tüm C# dosyaları iyileştirmeler etkin olacak şekilde derler ve hata ayıklama sembolünü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="8e69f-139">Compiles all the C# files in the current directory with optimizations enabled and defines the DEBUG symbol.</span></span> <span data-ttu-id="8e69f-140">Çıktı, *dosya2. exe*' dir:</span><span class="sxs-lookup"><span data-stu-id="8e69f-140">The output is *File2.exe*:</span></span>

  ```console
  csc -define:DEBUG -optimize -out:File2.exe *.cs
  ```

- <span data-ttu-id="8e69f-141">Geçerli dizindeki tüm C# dosyaları, *dosya2. dll*' nin hata ayıklama sürümünü üreten şekilde derler.</span><span class="sxs-lookup"><span data-stu-id="8e69f-141">Compiles all the C# files in the current directory producing a debug version of *File2.dll*.</span></span> <span data-ttu-id="8e69f-142">Amblem yoktur ve hiçbir uyarı gösterilmez:</span><span class="sxs-lookup"><span data-stu-id="8e69f-142">No logo and no warnings are displayed:</span></span>

  ```console
  csc -target:library -out:File2.dll -warn:0 -nologo -debug *.cs
  ```

- <span data-ttu-id="8e69f-143">Geçerli dizindeki tüm C# dosyaları *bir. xyz* (bir dll) olarak derler:</span><span class="sxs-lookup"><span data-stu-id="8e69f-143">Compiles all the C# files in the current directory to *Something.xyz* (a DLL):</span></span>

  ```console
  csc -target:library -out:Something.xyz *.cs
  ```

## <a name="differences-between-c-compiler-and-c-compiler-output"></a><span data-ttu-id="8e69f-144">Derleyici ve C# C++ derleyici çıkışı arasındaki farklılıklar</span><span class="sxs-lookup"><span data-stu-id="8e69f-144">Differences between C# compiler and C++ compiler output</span></span>

<span data-ttu-id="8e69f-145">Derleyiciyi çağırma sonucu olarak oluşturulan nesne ( *. obj*) dosyaları yoktur; C# çıktı dosyaları doğrudan oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="8e69f-145">There are no object (*.obj*) files created as a result of invoking the C# compiler; output files are created directly.</span></span> <span data-ttu-id="8e69f-146">Bunun sonucunda, C# derleyicinin bir bağlayıcıya ihtiyacı yoktur.</span><span class="sxs-lookup"><span data-stu-id="8e69f-146">As a result of this, the C# compiler does not need a linker.</span></span>

## <a name="see-also"></a><span data-ttu-id="8e69f-147">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8e69f-147">See also</span></span>

- [<span data-ttu-id="8e69f-148">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="8e69f-148">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="8e69f-149">Alfabetik Listelenmiş C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="8e69f-149">C# Compiler Options Listed Alphabetically</span></span>](./listed-alphabetically.md)
- [<span data-ttu-id="8e69f-150">Kategorilere Göre Listelenen C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="8e69f-150">C# Compiler Options Listed by Category</span></span>](./listed-by-category.md)
- [<span data-ttu-id="8e69f-151">Ana() ve Komut Satırı Bağımsız Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="8e69f-151">Main() and Command-Line Arguments</span></span>](../../programming-guide/main-and-command-args/index.md)
- [<span data-ttu-id="8e69f-152">Komut Satırı Bağımsız Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="8e69f-152">Command-Line Arguments</span></span>](../../programming-guide/main-and-command-args/command-line-arguments.md)
- [<span data-ttu-id="8e69f-153">Komut satırı bağımsız değişkenlerini görüntüleme</span><span class="sxs-lookup"><span data-stu-id="8e69f-153">How to display command-line arguments</span></span>](../../programming-guide/main-and-command-args/how-to-display-command-line-arguments.md)
- [<span data-ttu-id="8e69f-154">Ana() Dönüş Değerleri</span><span class="sxs-lookup"><span data-stu-id="8e69f-154">Main() Return Values</span></span>](../../programming-guide/main-and-command-args/main-return-values.md)
