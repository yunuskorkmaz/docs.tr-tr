---
title: Csc. exe ile komut satırı oluşturma
ms.date: 04/19/2017
helpviewer_keywords:
- builds [C#]
- command line [C#]
ms.assetid: 66e70056-dd20-453c-a9b3-507e0478b015
ms.openlocfilehash: 54306c79bc2856996925756ee4261fbe67692aea
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69606981"
---
# <a name="command-line-build-with-cscexe"></a><span data-ttu-id="05113-102">Csc. exe ile komut satırı oluşturma</span><span class="sxs-lookup"><span data-stu-id="05113-102">Command-line build with csc.exe</span></span>
<span data-ttu-id="05113-103">Bir komut isteminde yürütülebilir C# dosyasının adını (*CSC. exe*) yazarak derleyiciyi çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="05113-103">You can invoke the C# compiler by typing the name of its executable file (*csc.exe*) at a command prompt.</span></span>

<span data-ttu-id="05113-104">**Visual Studio için geliştirici komut istemi** kullanıyorsanız, tüm gerekli ortam değişkenleri sizin için ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="05113-104">If you use the **Developer Command Prompt for Visual Studio** window, all the necessary environment variables are set for you.</span></span> <span data-ttu-id="05113-105">Bu araca erişme hakkında daha fazla bilgi için bkz. [Visual Studio için geliştirici komut istemi](../../../framework/tools/developer-command-prompt-for-vs.md) konusu.</span><span class="sxs-lookup"><span data-stu-id="05113-105">For information on how to access this tool, see the [Developer Command Prompt for Visual Studio](../../../framework/tools/developer-command-prompt-for-vs.md) topic.</span></span> 

<span data-ttu-id="05113-106">Standart bir komut Istemi penceresi kullanıyorsanız, bilgisayarınızdaki herhangi bir alt dizinden *CSC. exe* ' yi çağırabilmeniz için önce yolunu ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="05113-106">If you use a standard Command Prompt window, you must adjust your path before you can invoke *csc.exe* from any subdirectory on your computer.</span></span> <span data-ttu-id="05113-107">Ayrıca, komut satırı yapılarını desteklemek üzere uygun ortam değişkenlerini ayarlamak için *vsvars32. bat* dosyasını çalıştırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="05113-107">You also must run *vsvars32.bat* to set the appropriate environment variables to support command-line builds.</span></span> <span data-ttu-id="05113-108">*Vsvars32. bat*hakkında daha fazla bilgi için, bkz [. nasıl yapılır: Visual Studio komut satırı](./how-to-set-environment-variables-for-the-visual-studio-command-line.md)için ortam değişkenlerini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="05113-108">For more information about *vsvars32.bat*, including instructions for how to find and run it, see [How to: Set Environment Variables for the Visual Studio Command Line](./how-to-set-environment-variables-for-the-visual-studio-command-line.md).</span></span>

<span data-ttu-id="05113-109">Yalnızca Windows yazılım geliştirme seti (SDK) olan bir bilgisayarda çalışıyorsanız, C# **Microsoft .NET Framework SDK** menü seçeneğinden açtığınız **SDK komut isteminde**derleyiciyi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="05113-109">If you're working on a computer that has only the Windows Software Development Kit (SDK), you can use the C# compiler at the **SDK Command Prompt**, which you open from the **Microsoft .NET Framework SDK** menu option.</span></span>

<span data-ttu-id="05113-110">Ayrıca C# programlarını program aracılığıyla oluşturmak için MSBuild'i kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="05113-110">You can also use MSBuild to build C# programs programmatically.</span></span> <span data-ttu-id="05113-111">Daha fazla bilgi için bkz. [MSBuild](/visualstudio/msbuild/msbuild).</span><span class="sxs-lookup"><span data-stu-id="05113-111">For more information, see [MSBuild](/visualstudio/msbuild/msbuild).</span></span>

<span data-ttu-id="05113-112">*CSC. exe* yürütülebilir dosyası genellikle\\ *Windows* dizini altındaki Microsoft. NET\Framework *\<Version >* klasöründe bulunur.</span><span class="sxs-lookup"><span data-stu-id="05113-112">The *csc.exe* executable file usually is located in the Microsoft.NET\Framework\\*\<Version>* folder under the *Windows* directory.</span></span> <span data-ttu-id="05113-113">Bu dosyanın yeri, belirli bir bilgisayarın tam yapılandırmasına bağlı olarak değişebilir.</span><span class="sxs-lookup"><span data-stu-id="05113-113">Its location might vary depending on the exact configuration of a particular computer.</span></span> <span data-ttu-id="05113-114">Bilgisayarınızda .NET Framework'ün birden fazla sürümü yüklüyse, bu dosyanın birden fazla sürümünü bulacaksınız.</span><span class="sxs-lookup"><span data-stu-id="05113-114">If more than one version of the .NET Framework is installed on your computer, you'll find multiple versions of this file.</span></span> <span data-ttu-id="05113-115">Bu tür yüklemeler hakkında daha fazla bilgi için bkz. [nasıl yapılır: hangi .NET Framework sürümlerinin yüklendiğini belirleme](../../../framework/migration-guide/how-to-determine-which-versions-are-installed.md).</span><span class="sxs-lookup"><span data-stu-id="05113-115">For more information about such installations, see [How to: determine which versions of the .NET Framework are installed](../../../framework/migration-guide/how-to-determine-which-versions-are-installed.md).</span></span>

> [!TIP]
>  <span data-ttu-id="05113-116">Visual Studio IDE kullanarak bir proje oluşturduğunuzda, **CSC** komutunu ve ilgili derleyici seçeneklerini **Çıkış** penceresinde görüntüleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="05113-116">When you build a project by using the Visual Studio IDE, you can display the **csc** command and its associated compiler options in the **Output** window.</span></span> <span data-ttu-id="05113-117">Bu bilgileri göstermek için aşağıdaki yönergeleri [izleyin: Günlük verilerinin ayrıntı düzeyini **normal** veya **ayrıntılı**olarak değiştirmek](/visualstudio/ide/how-to-view-save-and-configure-build-log-files#to-change-the-amount-of-information-included-in-the-build-log) için yapı günlüğü dosyalarını görüntüleyin, kaydedin ve yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="05113-117">To display this information, follow the instructions in [How to: View, Save, and Configure Build Log Files](/visualstudio/ide/how-to-view-save-and-configure-build-log-files#to-change-the-amount-of-information-included-in-the-build-log) to change the verbosity level of the log data to **Normal** or **Detailed**.</span></span> <span data-ttu-id="05113-118">Projenizi yeniden oluşturduktan sonra, C# derleyicinin çağrılmasını bulmak Için **CSC** **Çıkış** penceresinde arama yapın.</span><span class="sxs-lookup"><span data-stu-id="05113-118">After you rebuild your project, search the **Output** window for **csc** to find the invocation of the C# compiler.</span></span>

 <span data-ttu-id="05113-119">**Bu konudaki**</span><span class="sxs-lookup"><span data-stu-id="05113-119">**In this topic**</span></span>

- [<span data-ttu-id="05113-120">Komut satırı söz dizimi için kurallar</span><span class="sxs-lookup"><span data-stu-id="05113-120">Rules for command-line syntax</span></span>](#rules-for-command-line-syntax-for-the-c-compiler)

- [<span data-ttu-id="05113-121">Örnek komut satırları</span><span class="sxs-lookup"><span data-stu-id="05113-121">Sample command lines</span></span>](#sample-command-lines-for-the-c-compiler)

- [<span data-ttu-id="05113-122">Derleyici ve C# C++ derleyici çıkışı arasındaki farklılıklar</span><span class="sxs-lookup"><span data-stu-id="05113-122">Differences between C# compiler and C++ compiler output</span></span>](#differences-between-c-compiler-and-c-compiler-output)

## <a name="rules-for-command-line-syntax-for-the-c-compiler"></a><span data-ttu-id="05113-123">C# Derleyici komut satırı sözdizimi için kurallar</span><span class="sxs-lookup"><span data-stu-id="05113-123">Rules for command-line syntax for the C# compiler</span></span>

<span data-ttu-id="05113-124">C# Derleyici, işletim sistemi komut satırında verilen bağımsız değişkenleri yorumladığı zaman aşağıdaki kuralları kullanır:</span><span class="sxs-lookup"><span data-stu-id="05113-124">The C# compiler uses the following rules when it interprets arguments given on the operating system command line:</span></span>

- <span data-ttu-id="05113-125">Bağımsız değişkenler boşluk veya sekme olan boşluk ile sınırlandırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="05113-125">Arguments are delimited by white space, which is either a space or a tab.</span></span>

- <span data-ttu-id="05113-126">Giriş işareti karakteri (^) bir kaçış karakteri veya sınırlayıcı olarak tanınmıyor.</span><span class="sxs-lookup"><span data-stu-id="05113-126">The caret character (^) is not recognized as an escape character or delimiter.</span></span> <span data-ttu-id="05113-127">Karakter, programdaki `argv` diziye geçirilmeden önce işletim sistemindeki komut satırı ayrıştırıcısı tarafından işlenir.</span><span class="sxs-lookup"><span data-stu-id="05113-127">The character is handled by the command-line parser in the operating system before it's passed to the `argv` array in the program.</span></span>

- <span data-ttu-id="05113-128">Çift tırnak işaretleri ("String") içine alınmış bir dize, içinde yer alan boşluklardan bağımsız olarak tek bir bağımsız değişken olarak yorumlanır.</span><span class="sxs-lookup"><span data-stu-id="05113-128">A string enclosed in double quotation marks ("string") is interpreted as a single argument, regardless of white space that is contained within.</span></span> <span data-ttu-id="05113-129">Tırnak içine alınmış bir dize bir bağımsız değişkene gömülebilir.</span><span class="sxs-lookup"><span data-stu-id="05113-129">A quoted string can be embedded in an argument.</span></span>

- <span data-ttu-id="05113-130">Önünde ters eğik çizgi (\\") olan bir çift tırnak işareti, sabit değer çift tırnak işareti karakteri (") olarak yorumlanır.</span><span class="sxs-lookup"><span data-stu-id="05113-130">A double quotation mark preceded by a backslash (\\") is interpreted as a literal double quotation mark character (").</span></span>

- <span data-ttu-id="05113-131">Ters eğik çizgiler, bir çift tırnak işaretinden hemen önce gelmedikleri takdirde tam olarak yorumlanır.</span><span class="sxs-lookup"><span data-stu-id="05113-131">Backslashes are interpreted literally, unless they immediately precede a double quotation mark.</span></span>

- <span data-ttu-id="05113-132">İki ters eğik çizgi daha sonra çift tırnak işareti kullanıyorsa, bir ters eğik çizgi her çift eğik çizgi için `argv` diziye konur ve çift tırnak işareti dize sınırlayıcısı olarak yorumlanır.</span><span class="sxs-lookup"><span data-stu-id="05113-132">If an even number of backslashes is followed by a double quotation mark, one backslash is put in the `argv` array for every pair of backslashes, and the double quotation mark is interpreted as a string delimiter.</span></span>

- <span data-ttu-id="05113-133">Tek bir ters eğik çizgiden sonra çift tırnak işareti varsa, her ters eğik çizgi çifti için bir ters eğik `argv` çizgi konur ve çift tırnak işareti kalan ters eğik çizgi için "kaçışlı" olur.</span><span class="sxs-lookup"><span data-stu-id="05113-133">If an odd number of backslashes is followed by a double quotation mark, one backslash is put in the `argv` array for every pair of backslashes, and the double quotation mark is "escaped" by the remaining backslash.</span></span> <span data-ttu-id="05113-134">Bu, içinde `argv`bir sabit değer çift tırnak işareti (") eklenmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="05113-134">This causes a literal double quotation mark (") to be added in `argv`.</span></span>

## <a name="sample-command-lines-for-the-c-compiler"></a><span data-ttu-id="05113-135">C# Derleyici için örnek komut satırları</span><span class="sxs-lookup"><span data-stu-id="05113-135">Sample command lines for the C# compiler</span></span>

- <span data-ttu-id="05113-136">*File.cs* üreten *dosya. exe*' yi derler:</span><span class="sxs-lookup"><span data-stu-id="05113-136">Compiles *File.cs* producing *File.exe*:</span></span>

```console
csc File.cs 
```

- <span data-ttu-id="05113-137">*File.cs* üreten *dosyayı derler. dll*:</span><span class="sxs-lookup"><span data-stu-id="05113-137">Compiles *File.cs* producing *File.dll*:</span></span>

```console
csc -target:library File.cs
```

- <span data-ttu-id="05113-138">*File.cs* derler ve *My. exe dosyasını*oluşturur:</span><span class="sxs-lookup"><span data-stu-id="05113-138">Compiles *File.cs* and creates *My.exe*:</span></span>

```console
csc -out:My.exe File.cs
```

- <span data-ttu-id="05113-139">Geçerli dizindeki tüm C# dosyaları iyileştirmeler etkin olacak şekilde derler ve hata ayıklama sembolünü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="05113-139">Compiles all the C# files in the current directory with optimizations enabled and defines the DEBUG symbol.</span></span> <span data-ttu-id="05113-140">Çıktı, *dosya2. exe*' dir:</span><span class="sxs-lookup"><span data-stu-id="05113-140">The output is *File2.exe*:</span></span>

```console
csc -define:DEBUG -optimize -out:File2.exe *.cs
```

- <span data-ttu-id="05113-141">Geçerli dizindeki tüm C# dosyaları, *dosya2. dll*' nin hata ayıklama sürümünü üreten şekilde derler.</span><span class="sxs-lookup"><span data-stu-id="05113-141">Compiles all the C# files in the current directory producing a debug version of *File2.dll*.</span></span> <span data-ttu-id="05113-142">Amblem yoktur ve hiçbir uyarı gösterilmez:</span><span class="sxs-lookup"><span data-stu-id="05113-142">No logo and no warnings are displayed:</span></span>

```console
csc -target:library -out:File2.dll -warn:0 -nologo -debug *.cs
```

- <span data-ttu-id="05113-143">Geçerli dizindeki tüm C# dosyaları *bir. xyz* (bir dll) olarak derler:</span><span class="sxs-lookup"><span data-stu-id="05113-143">Compiles all the C# files in the current directory to *Something.xyz* (a DLL):</span></span>

```console
csc -target:library -out:Something.xyz *.cs
```

## <a name="differences-between-c-compiler-and-c-compiler-output"></a><span data-ttu-id="05113-144">Derleyici ve C# C++ derleyici çıkışı arasındaki farklılıklar</span><span class="sxs-lookup"><span data-stu-id="05113-144">Differences between C# compiler and C++ compiler output</span></span>
<span data-ttu-id="05113-145">Derleyiciyi çağırma sonucu olarak oluşturulan nesne ( *. obj*) dosyaları yoktur; C# çıktı dosyaları doğrudan oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="05113-145">There are no object (*.obj*) files created as a result of invoking the C# compiler; output files are created directly.</span></span> <span data-ttu-id="05113-146">Bunun sonucunda, C# derleyicinin bir bağlayıcıya ihtiyacı yoktur.</span><span class="sxs-lookup"><span data-stu-id="05113-146">As a result of this, the C# compiler does not need a linker.</span></span>

## <a name="see-also"></a><span data-ttu-id="05113-147">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="05113-147">See also</span></span>

- [<span data-ttu-id="05113-148">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="05113-148">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="05113-149">Alfabetik Listelenmiş C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="05113-149">C# Compiler Options Listed Alphabetically</span></span>](./listed-alphabetically.md)
- [<span data-ttu-id="05113-150">Kategorilere Göre Listelenen C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="05113-150">C# Compiler Options Listed by Category</span></span>](./listed-by-category.md)
- [<span data-ttu-id="05113-151">Ana() ve Komut Satırı Bağımsız Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="05113-151">Main() and Command-Line Arguments</span></span>](../../programming-guide/main-and-command-args/index.md)
- [<span data-ttu-id="05113-152">Komut Satırı Bağımsız Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="05113-152">Command-Line Arguments</span></span>](../../programming-guide/main-and-command-args/command-line-arguments.md)
- [<span data-ttu-id="05113-153">Nasıl yapılır: Komut satırı bağımsız değişkenlerini görüntüle</span><span class="sxs-lookup"><span data-stu-id="05113-153">How to: Display Command-Line Arguments</span></span>](../../programming-guide/main-and-command-args/how-to-display-command-line-arguments.md)
- [<span data-ttu-id="05113-154">Ana() Dönüş Değerleri</span><span class="sxs-lookup"><span data-stu-id="05113-154">Main() Return Values</span></span>](../../programming-guide/main-and-command-args/main-return-values.md)
