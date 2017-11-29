---
title: "Hello World -- İlk Programınız (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: get-started-article
f1_keywords:
- cs.program
- vs.csharp.startpage.firstapplication
helpviewer_keywords:
- examples [C#], Hello World
- Hello World example [C#]
ms.assetid: 6493182a-b0b6-4539-a719-518a168cb730
caps.latest.revision: "39"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c17dcce921f3a6ff1a9c547c5ff5d34c3dbbf28d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="hello-world----your-first-program-c-programming-guide"></a><span data-ttu-id="e4a96-102">Hello World -- İlk Programınız (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="e4a96-102">Hello World -- Your First Program (C# Programming Guide)</span></span>
<span data-ttu-id="e4a96-103">Aşağıdaki yordam bir C# sürümünü geleneksel "Hello World!" oluşturur</span><span class="sxs-lookup"><span data-stu-id="e4a96-103">The following procedure creates a C# version of the traditional "Hello World!"</span></span> <span data-ttu-id="e4a96-104">Program.</span><span class="sxs-lookup"><span data-stu-id="e4a96-104">program.</span></span> <span data-ttu-id="e4a96-105">Program dize görüntüler`Hello World!`</span><span class="sxs-lookup"><span data-stu-id="e4a96-105">The program displays the string `Hello World!`</span></span>  
  
 <span data-ttu-id="e4a96-106">Giriş kavramları daha fazla örnekleri için bkz: [Visual C# ve Visual Basic ile çalışmaya başlama](/visualstudio/ide/getting-started-with-visual-csharp-and-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="e4a96-106">For more examples of introductory concepts, see [Getting Started with Visual C# and Visual Basic](/visualstudio/ide/getting-started-with-visual-csharp-and-visual-basic).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-and-run-a-console-application"></a><span data-ttu-id="e4a96-107">Bir konsol uygulaması oluşturmak ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="e4a96-107">To create and run a console application</span></span>  
  
1.  <span data-ttu-id="e4a96-108">Visual Studio'yu başlatın.</span><span class="sxs-lookup"><span data-stu-id="e4a96-108">Start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="e4a96-109">Menü çubuğunda seçin **dosya**, **yeni**, **proje**.</span><span class="sxs-lookup"><span data-stu-id="e4a96-109">On the menu bar, choose **File**, **New**, **Project**.</span></span>  
  
     <span data-ttu-id="e4a96-110">**Yeni proje** iletişim kutusu açılır.</span><span class="sxs-lookup"><span data-stu-id="e4a96-110">The **New Project** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="e4a96-111">Genişletme **yüklü**, genişletin **şablonları**, genişletin **Visual C#**ve ardından **konsol uygulaması**.</span><span class="sxs-lookup"><span data-stu-id="e4a96-111">Expand **Installed**, expand **Templates**, expand **Visual C#**, and then choose **Console Application**.</span></span>  
  
4.  <span data-ttu-id="e4a96-112">İçinde **adı** kutusunda projeniz için bir ad belirtin ve ardından **Tamam** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="e4a96-112">In the **Name** box, specify a name for your project, and then choose the **OK** button.</span></span>  
  
     <span data-ttu-id="e4a96-113">Yeni Proje görünür **Çözüm Gezgini**.</span><span class="sxs-lookup"><span data-stu-id="e4a96-113">The new project appears in **Solution Explorer**.</span></span>  
  
5.  <span data-ttu-id="e4a96-114">Program.cs içinde açık değilse **Kod düzenleyicisinde**, kısayol menüsünü açın **Program.cs** içinde **Çözüm Gezgini**ve ardından **görünümü kodu**.</span><span class="sxs-lookup"><span data-stu-id="e4a96-114">If Program.cs isn't open in the **Code Editor**, open the shortcut menu for **Program.cs** in **Solution Explorer**, and then choose **View Code**.</span></span>  
  
6.  <span data-ttu-id="e4a96-115">Program.cs içeriğini aşağıdaki kodla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="e4a96-115">Replace the contents of Program.cs with the following code.</span></span>  
  
     [!code-csharp[csProgGuide#21](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_1.cs)]  
  
7.  <span data-ttu-id="e4a96-116">Projeyi çalıştırmak için F5 tuşuna seçin.</span><span class="sxs-lookup"><span data-stu-id="e4a96-116">Choose the F5 key to run the project.</span></span> <span data-ttu-id="e4a96-117">Bir çizgi içeren bir komut istemi penceresi görüntülenir`Hello World!`</span><span class="sxs-lookup"><span data-stu-id="e4a96-117">A Command Prompt window appears that contains the line `Hello World!`</span></span>  
  
 <span data-ttu-id="e4a96-118">Ardından, bu program önemli kısımlarını incelenir.</span><span class="sxs-lookup"><span data-stu-id="e4a96-118">Next, the important parts of this program are examined.</span></span>  
  
## <a name="comments"></a><span data-ttu-id="e4a96-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e4a96-119">Comments</span></span>  
 <span data-ttu-id="e4a96-120">İlk satır yorum içerir.</span><span class="sxs-lookup"><span data-stu-id="e4a96-120">The first line contains a comment.</span></span> <span data-ttu-id="e4a96-121">Karakterleri `//` açıklama satırı kalan Dönüştür.</span><span class="sxs-lookup"><span data-stu-id="e4a96-121">The characters `//` convert the rest of the line to a comment.</span></span>  
  
 [!code-csharp[csProgGuide#32](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_2.cs)]  
  
 <span data-ttu-id="e4a96-122">Bir metin bloğunu arasında kapsayan tarafından da yorum yapabileceği `/*` ve `*/` karakter.</span><span class="sxs-lookup"><span data-stu-id="e4a96-122">You can also comment out a block of text by enclosing it between the `/*` and `*/` characters.</span></span> <span data-ttu-id="e4a96-123">Bu, aşağıdaki örnekte gösterilir.</span><span class="sxs-lookup"><span data-stu-id="e4a96-123">This is shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuide#33](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_3.cs)]  
  
## <a name="main-method"></a><span data-ttu-id="e4a96-124">Ana Yöntem</span><span class="sxs-lookup"><span data-stu-id="e4a96-124">Main Method</span></span>  
 <span data-ttu-id="e4a96-125">Bir C# konsol uygulaması içermesi gereken bir `Main` denetim başlar ve biter yöntemi.</span><span class="sxs-lookup"><span data-stu-id="e4a96-125">A C# console application must contain a `Main` method, in which control starts and ends.</span></span> <span data-ttu-id="e4a96-126">`Main` Yöntemdir burada nesneleri oluşturmak ve diğer bir yöntem yürütülemez.</span><span class="sxs-lookup"><span data-stu-id="e4a96-126">The `Main` method is where you create objects and execute other methods.</span></span>  
  
 <span data-ttu-id="e4a96-127">`Main` Yöntemi bir [statik](../../../csharp/language-reference/keywords/static.md) bir sınıf veya yapı içinde bulunduğu yöntemi.</span><span class="sxs-lookup"><span data-stu-id="e4a96-127">The `Main` method is a [static](../../../csharp/language-reference/keywords/static.md) method that resides inside a class or a struct.</span></span> <span data-ttu-id="e4a96-128">Önceki "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="e4a96-128">In the previous "Hello World!"</span></span> <span data-ttu-id="e4a96-129">Örneğin, adlı bir sınıf içinde bulunduğu `Hello`.</span><span class="sxs-lookup"><span data-stu-id="e4a96-129">example, it resides in a class named `Hello`.</span></span> <span data-ttu-id="e4a96-130">Bildirebilirsiniz `Main` aşağıdaki yollardan biriyle yöntemi:</span><span class="sxs-lookup"><span data-stu-id="e4a96-130">You can declare the `Main` method in one of the following ways:</span></span>  
  
-   <span data-ttu-id="e4a96-131">Geri dönebilirsiniz `void`.</span><span class="sxs-lookup"><span data-stu-id="e4a96-131">It can return `void`.</span></span>  
  
     [!code-csharp[csProgGuideMain#12](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_4.cs)]  
  
-   <span data-ttu-id="e4a96-132">Ayrıca bir tamsayı geri dönebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e4a96-132">It can also return an integer.</span></span>  
  
     [!code-csharp[csProgGuideMain#13](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_5.cs)]  
  
-   <span data-ttu-id="e4a96-133">Dönüş türleri birini kullanarak, bağımsız değişkenleri alabilir.</span><span class="sxs-lookup"><span data-stu-id="e4a96-133">With either of the return types, it can take arguments.</span></span>  
  
     [!code-csharp[csProgGuideMain#19](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_6.cs)]  
  
     <span data-ttu-id="e4a96-134">veya</span><span class="sxs-lookup"><span data-stu-id="e4a96-134">-or-</span></span>  
  
     [!code-csharp[csProgGuideMain#18](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_7.cs)]  
  
 <span data-ttu-id="e4a96-135">Parametresi, `Main` yöntemi, `args`, olan bir `string` program çağırmak için kullanılan komut satırı bağımsız değişkenleri içeren bir dizi.</span><span class="sxs-lookup"><span data-stu-id="e4a96-135">The parameter of the `Main` method, `args`, is a `string` array that contains the command-line arguments used to invoke the program.</span></span> <span data-ttu-id="e4a96-136">Aksine C++'da, dizi yürütülebilir (exe) dosyasının adı içermez.</span><span class="sxs-lookup"><span data-stu-id="e4a96-136">Unlike in C++, the array does not include the name of the executable (exe) file.</span></span>  
  
 <span data-ttu-id="e4a96-137">Örneklerde komut satırı bağımsız değişkenleri kullanma hakkında daha fazla bilgi için bkz: [ana() ve komut satırı bağımsız değişkenleri](../../../csharp/programming-guide/main-and-command-args/index.md) ve [nasıl yapılır: oluşturma ve kullanma derlemeler kullanma komut satırı](http://msdn.microsoft.com/library/70f65026-3687-4e9c-ab79-c18b97dd8be4).</span><span class="sxs-lookup"><span data-stu-id="e4a96-137">For more information about how to use command-line arguments, see the examples in [Main() and Command-Line Arguments](../../../csharp/programming-guide/main-and-command-args/index.md) and [How to: Create and Use Assemblies Using the Command Line](http://msdn.microsoft.com/library/70f65026-3687-4e9c-ab79-c18b97dd8be4).</span></span>  
  
 <span data-ttu-id="e4a96-138">Çağrı <xref:System.Console.ReadKey%2A> sonunda `Main` yöntemi, F5 tuşuna basarak programınızı hata ayıklama modunda çalıştırdığınızda, çıktı okuma fırsatına sahip önce kapatma konsol penceresi önler.</span><span class="sxs-lookup"><span data-stu-id="e4a96-138">The call to <xref:System.Console.ReadKey%2A> at the end of the `Main` method prevents the console window from closing before you have a chance to read the output when you run your program in debug mode, by pressing F5.</span></span>  
  
## <a name="input-and-output"></a><span data-ttu-id="e4a96-139">Girdi ve Çıktı</span><span class="sxs-lookup"><span data-stu-id="e4a96-139">Input and Output</span></span>  
 <span data-ttu-id="e4a96-140">C# programları genellikle .NET Framework çalışma zamanı kitaplığı tarafından sağlanan giriş/çıkış Hizmetleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="e4a96-140">C# programs generally use the input/output services provided by the run-time library of the .NET Framework.</span></span> <span data-ttu-id="e4a96-141">Deyim `System.Console.WriteLine("Hello World!");` kullanan <xref:System.Console.WriteLine%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="e4a96-141">The statement `System.Console.WriteLine("Hello World!");` uses the <xref:System.Console.WriteLine%2A> method.</span></span> <span data-ttu-id="e4a96-142">Çıktı yöntemlerinden birini budur <xref:System.Console> Çalışma Zamanı Kitaplığı'nda sınıfı.</span><span class="sxs-lookup"><span data-stu-id="e4a96-142">This is one of the output methods of the <xref:System.Console> class in the run-time library.</span></span> <span data-ttu-id="e4a96-143">Yeni bir satırla tarafından izlenen standart çıktı akışı, dize parametresinin görüntüler.</span><span class="sxs-lookup"><span data-stu-id="e4a96-143">It displays its string parameter on the standard output stream followed by a new line.</span></span> <span data-ttu-id="e4a96-144">Diğer <xref:System.Console> yöntemleri farklı bir giriş ve çıkış işlemleri için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e4a96-144">Other <xref:System.Console> methods are available for different input and output operations.</span></span> <span data-ttu-id="e4a96-145">Dahil ederseniz `using System;` yönerge program başında doğrudan kullanabileceğiniz <xref:System> sınıflar ve yöntemler tam olarak niteleme olmadan.</span><span class="sxs-lookup"><span data-stu-id="e4a96-145">If you include the `using System;` directive at the beginning of the program, you can directly use the <xref:System> classes and methods without fully qualifying them.</span></span> <span data-ttu-id="e4a96-146">Örneğin, çağırabilirsiniz `Console.WriteLine` yerine `System.Console.WriteLine`:</span><span class="sxs-lookup"><span data-stu-id="e4a96-146">For example, you can call `Console.WriteLine` instead of `System.Console.WriteLine`:</span></span>  
  
 [!code-csharp[csProgGuide#1](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_8.cs)]  
  
 [!code-csharp[csProgGuide#23](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_9.cs)]  
  
 <span data-ttu-id="e4a96-147">Giriş/Çıkış yöntemleri hakkında daha fazla bilgi için bkz: <xref:System.IO>.</span><span class="sxs-lookup"><span data-stu-id="e4a96-147">For more information about input/output methods, see <xref:System.IO>.</span></span>  
  
## <a name="command-line-compilation-and-execution"></a><span data-ttu-id="e4a96-148">Komut Satırı Derlemesi ve Yürütme</span><span class="sxs-lookup"><span data-stu-id="e4a96-148">Command-Line Compilation and Execution</span></span>  
 <span data-ttu-id="e4a96-149">"Hello World!" derleme</span><span class="sxs-lookup"><span data-stu-id="e4a96-149">You can compile the "Hello World!"</span></span> <span data-ttu-id="e4a96-150">Visual Studio tümleşik geliştirme ortamı (IDE yerine) komut satırını kullanarak programı.</span><span class="sxs-lookup"><span data-stu-id="e4a96-150">program by using the command line instead of the Visual Studio Integrated Development Environment (IDE).</span></span>  
  
#### <a name="to-compile-and-run-from-a-command-prompt"></a><span data-ttu-id="e4a96-151">Derlemek ve bir komut satırından çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="e4a96-151">To compile and run from a command prompt</span></span>  
  
1.  <span data-ttu-id="e4a96-152">Yukarıdaki yordamı koddan bir metin düzenleyicisine yapıştırın ve dosyayı bir metin dosyası olarak kaydedin.</span><span class="sxs-lookup"><span data-stu-id="e4a96-152">Paste the code from the preceding procedure into any text editor, and then save the file as a text file.</span></span> <span data-ttu-id="e4a96-153">Dosya adı `Hello.cs`.</span><span class="sxs-lookup"><span data-stu-id="e4a96-153">Name the file `Hello.cs`.</span></span> <span data-ttu-id="e4a96-154">C# kaynak kodu dosyaları kullanmak uzantısı `.cs`.</span><span class="sxs-lookup"><span data-stu-id="e4a96-154">C# source code files use the extension `.cs`.</span></span>  
  
2.  <span data-ttu-id="e4a96-155">Bir komut istemi penceresi açmak için aşağıdaki adımlardan birini gerçekleştirin:</span><span class="sxs-lookup"><span data-stu-id="e4a96-155">Perform one of the following steps to open a command-prompt window:</span></span>  
  
    -   <span data-ttu-id="e4a96-156">Windows 10 ' daki üzerinde **Başlat** menüsü, arama `Developer Command Prompt`ve ardından dokunun veya seçin **VS 2017 için geliştirici komut istemi**.</span><span class="sxs-lookup"><span data-stu-id="e4a96-156">In Windows 10, on the **Start** menu, search for `Developer Command Prompt`, and then tap or choose **Developer Command Prompt for VS 2017**.</span></span>  
  
         <span data-ttu-id="e4a96-157">Bir geliştirici komut istemi penceresi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="e4a96-157">A Developer Command Prompt window appears.</span></span>  
  
    -   <span data-ttu-id="e4a96-158">Windows 7'de açmak **Başlat** menüsü, Visual Studio'nun geçerli sürümü için klasörü genişletin, kısayol menüsünü açın **Visual Studio Araçları**ve ardından **Geliştirici komut istemi VS 2017 için**.</span><span class="sxs-lookup"><span data-stu-id="e4a96-158">In Windows 7, open the **Start** menu, expand the folder for the current version of Visual Studio, open the shortcut menu for **Visual Studio Tools**, and then choose **Developer Command Prompt for VS 2017**.</span></span>  
  
         <span data-ttu-id="e4a96-159">Bir geliştirici komut istemi penceresi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="e4a96-159">A Developer Command Prompt window appears.</span></span>  
  
    -   <span data-ttu-id="e4a96-160">Standart bir komut istemi penceresinden komut satırı derlemeleri etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="e4a96-160">Enable command-line builds from a standard Command Prompt window.</span></span>  
  
         <span data-ttu-id="e4a96-161">Bkz: [nasıl yapılır: Visual Studio komut satırı için ortam değişkenlerini ayarlama](../../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md).</span><span class="sxs-lookup"><span data-stu-id="e4a96-161">See [How to: Set Environment Variables for the Visual Studio Command Line](../../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md).</span></span>  
  
3.  <span data-ttu-id="e4a96-162">Komut İstemi penceresinde içeren klasöre gidin, `Hello.cs` dosya.</span><span class="sxs-lookup"><span data-stu-id="e4a96-162">In the command-prompt window, navigate to the folder that contains your `Hello.cs` file.</span></span>  
  
4.  <span data-ttu-id="e4a96-163">Derlemek için aşağıdaki komutu girin `Hello.cs`.</span><span class="sxs-lookup"><span data-stu-id="e4a96-163">Enter the following command to compile `Hello.cs`.</span></span>  
  
     `csc Hello.cs`  
  
     <span data-ttu-id="e4a96-164">Programınızı adlı bir yürütülebilir dosya hiç derleme hatası olup olmadığını `Hello.exe` oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="e4a96-164">If your program has no compilation errors, an executable file that is named `Hello.exe` is created.</span></span>  
  
5.  <span data-ttu-id="e4a96-165">Komut İstemi penceresinde programı çalıştırmak için aşağıdaki komutu girin:</span><span class="sxs-lookup"><span data-stu-id="e4a96-165">In the command-prompt window, enter the following command to run the program:</span></span>  
  
     `Hello`  
  
 <span data-ttu-id="e4a96-166">C# Derleyici ve seçenekleri hakkında daha fazla bilgi için bkz: [C# Derleyici Seçenekleri](../../../csharp/language-reference/compiler-options/index.md).</span><span class="sxs-lookup"><span data-stu-id="e4a96-166">For more information about the C# compiler and its options, see [C# Compiler Options](../../../csharp/language-reference/compiler-options/index.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="e4a96-167">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e4a96-167">See Also</span></span>  
 [<span data-ttu-id="e4a96-168">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="e4a96-168">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="e4a96-169">Bir C# programı içinde</span><span class="sxs-lookup"><span data-stu-id="e4a96-169">Inside a C# Program</span></span>](../../../csharp/programming-guide/inside-a-program/index.md)  
 [<span data-ttu-id="e4a96-170">Dizeleri</span><span class="sxs-lookup"><span data-stu-id="e4a96-170">Strings</span></span>](../../../csharp/programming-guide/strings/index.md)  
 [<span data-ttu-id="e4a96-171">\<paveover > C# örnek uygulamaları</span><span class="sxs-lookup"><span data-stu-id="e4a96-171">\<paveover>C# Sample Applications</span></span>](http://msdn.microsoft.com/en-us/9a9d7aaa-51d3-4224-b564-95409b0f3e15)  
 [<span data-ttu-id="e4a96-172">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="e4a96-172">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="e4a96-173">Ana() ve komut satırı bağımsız değişkenleri</span><span class="sxs-lookup"><span data-stu-id="e4a96-173">Main() and Command-Line Arguments</span></span>](../../../csharp/programming-guide/main-and-command-args/index.md)  
 [<span data-ttu-id="e4a96-174">Visual C# ve Visual Basic'e Başlarken</span><span class="sxs-lookup"><span data-stu-id="e4a96-174">Getting Started with Visual C# and Visual Basic</span></span>](/visualstudio/ide/getting-started-with-visual-csharp-and-visual-basic)
