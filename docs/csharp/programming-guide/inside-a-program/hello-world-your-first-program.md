---
title: Hello World--İlk programınız - C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- cs.program
- vs.csharp.startpage.firstapplication
helpviewer_keywords:
- examples [C#], Hello World
- Hello World example [C#]
ms.assetid: 6493182a-b0b6-4539-a719-518a168cb730
ms.openlocfilehash: 7ff65867f9f81118cad30852c439f8b3491bf1aa
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56969732"
---
# <a name="hello-world----your-first-program-c-programming-guide"></a><span data-ttu-id="76bca-102">Hello World--İlk programınız (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="76bca-102">Hello World -- Your first program (C# Programming Guide)</span></span>

<span data-ttu-id="76bca-103">Aşağıdaki yordam geleneksel "Hello World!"'ın bir C# sürümünü oluşturur.</span><span class="sxs-lookup"><span data-stu-id="76bca-103">The following procedure creates a C# version of the traditional "Hello World!"</span></span> <span data-ttu-id="76bca-104">Program.</span><span class="sxs-lookup"><span data-stu-id="76bca-104">program.</span></span> <span data-ttu-id="76bca-105">Program dizesini görüntüler. `Hello World!`</span><span class="sxs-lookup"><span data-stu-id="76bca-105">The program displays the string `Hello World!`</span></span>

<span data-ttu-id="76bca-106">Tanıtım kavramlarına daha fazla örnek için bkz: [Visual C# ve Visual Basic ile çalışmaya başlama](/visualstudio/ide/getting-started-with-visual-csharp-and-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="76bca-106">For more examples of introductory concepts, see [Getting Started with Visual C# and Visual Basic](/visualstudio/ide/getting-started-with-visual-csharp-and-visual-basic).</span></span>

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-create-and-run-a-console-application"></a><span data-ttu-id="76bca-107">Bir konsol uygulaması oluşturmak ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="76bca-107">To create and run a console application</span></span>

1. <span data-ttu-id="76bca-108">Visual Studio’yu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="76bca-108">Start Visual Studio.</span></span>

2. <span data-ttu-id="76bca-109">Menü çubuğunda, **dosya**, **yeni**, **proje**.</span><span class="sxs-lookup"><span data-stu-id="76bca-109">On the menu bar, choose **File**, **New**, **Project**.</span></span>

     <span data-ttu-id="76bca-110">**Yeni proje** iletişim kutusu açılır.</span><span class="sxs-lookup"><span data-stu-id="76bca-110">The **New Project** dialog box opens.</span></span>

3. <span data-ttu-id="76bca-111">Genişletin **yüklü**, genişletme **şablonları**, genişletme **Visual C#** ve ardından **konsol uygulaması**.</span><span class="sxs-lookup"><span data-stu-id="76bca-111">Expand **Installed**, expand **Templates**, expand **Visual C#**, and then choose **Console Application**.</span></span>

4. <span data-ttu-id="76bca-112">İçinde **adı** kutusuna projeniz için bir ad belirtin ve ardından **Tamam** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="76bca-112">In the **Name** box, specify a name for your project, and then choose the **OK** button.</span></span>

     <span data-ttu-id="76bca-113">Yeni Proje görünür **Çözüm Gezgini**.</span><span class="sxs-lookup"><span data-stu-id="76bca-113">The new project appears in **Solution Explorer**.</span></span>

5. <span data-ttu-id="76bca-114">Program.cs içinde açık değilse **Kod Düzenleyicisi**, kısayol menüsünü açın **Program.cs** içinde **Çözüm Gezgini**ve ardından **Kodu Görüntüle**.</span><span class="sxs-lookup"><span data-stu-id="76bca-114">If Program.cs isn't open in the **Code Editor**, open the shortcut menu for **Program.cs** in **Solution Explorer**, and then choose **View Code**.</span></span>

6. <span data-ttu-id="76bca-115">Program.cs içeriğini aşağıdaki kodla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="76bca-115">Replace the contents of Program.cs with the following code.</span></span>

     [!code-csharp[csProgGuide#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#21)]

7. <span data-ttu-id="76bca-116">Projeyi çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="76bca-116">Choose the F5 key to run the project.</span></span> <span data-ttu-id="76bca-117">Bir çizgi içeren bir komut istemi penceresi görünür `Hello World!`</span><span class="sxs-lookup"><span data-stu-id="76bca-117">A Command Prompt window appears that contains the line `Hello World!`</span></span>

<span data-ttu-id="76bca-118">Ardından, bu programın önemli bölümleri incelenir.</span><span class="sxs-lookup"><span data-stu-id="76bca-118">Next, the important parts of this program are examined.</span></span>

## <a name="comments"></a><span data-ttu-id="76bca-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="76bca-119">Comments</span></span>

<span data-ttu-id="76bca-120">İlk satır bir açıklama içerir.</span><span class="sxs-lookup"><span data-stu-id="76bca-120">The first line contains a comment.</span></span> <span data-ttu-id="76bca-121">Karakterleri `//` satırın geri kalanını açıklamaya Dönüştür.</span><span class="sxs-lookup"><span data-stu-id="76bca-121">The characters `//` convert the rest of the line to a comment.</span></span>

 [!code-csharp[csProgGuide#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#32)]

<span data-ttu-id="76bca-122">Metin bloğu arasında kapsayan tarafından da yorum yapabilecek `/*` ve `*/` karakter.</span><span class="sxs-lookup"><span data-stu-id="76bca-122">You can also comment out a block of text by enclosing it between the `/*` and `*/` characters.</span></span> <span data-ttu-id="76bca-123">Bu, aşağıdaki örnekte gösterilir.</span><span class="sxs-lookup"><span data-stu-id="76bca-123">This is shown in the following example.</span></span>

 [!code-csharp[csProgGuide#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#33)]

## <a name="main-method"></a><span data-ttu-id="76bca-124">Main yöntemi</span><span class="sxs-lookup"><span data-stu-id="76bca-124">Main method</span></span>

<span data-ttu-id="76bca-125">Bir C# konsol uygulaması içermelidir bir `Main` yöntemi, Denetim'ın başlar ve biter.</span><span class="sxs-lookup"><span data-stu-id="76bca-125">A C# console application must contain a `Main` method, in which control starts and ends.</span></span> <span data-ttu-id="76bca-126">`Main` Yöntemdir nesneleri oluşturduğunuz ve diğer bir yöntem yürütülemez.</span><span class="sxs-lookup"><span data-stu-id="76bca-126">The `Main` method is where you create objects and execute other methods.</span></span>

<span data-ttu-id="76bca-127">`Main` Yöntemi bir [statik](../../../csharp/language-reference/keywords/static.md) bir sınıf ya da yapının içinde bulunan yöntemi.</span><span class="sxs-lookup"><span data-stu-id="76bca-127">The `Main` method is a [static](../../../csharp/language-reference/keywords/static.md) method that resides inside a class or a struct.</span></span> <span data-ttu-id="76bca-128">Önceki "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="76bca-128">In the previous "Hello World!"</span></span> <span data-ttu-id="76bca-129">Örneğin, adında bir sınıf içinde bulunduğu `Hello`.</span><span class="sxs-lookup"><span data-stu-id="76bca-129">example, it resides in a class named `Hello`.</span></span> <span data-ttu-id="76bca-130">Bildirebilirsiniz `Main` aşağıdaki yollardan biriyle yöntemi:</span><span class="sxs-lookup"><span data-stu-id="76bca-130">You can declare the `Main` method in one of the following ways:</span></span>

- <span data-ttu-id="76bca-131">Geri dönebilirsiniz `void`.</span><span class="sxs-lookup"><span data-stu-id="76bca-131">It can return `void`.</span></span>

     [!code-csharp[csProgGuideMain#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#12)]

- <span data-ttu-id="76bca-132">Bu, ayrıca bir tamsayı döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="76bca-132">It can also return an integer.</span></span>

     [!code-csharp[csProgGuideMain#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#13)]

- <span data-ttu-id="76bca-133">Dönüş türleri her ikisiyle bağımsız değişken alabilir.</span><span class="sxs-lookup"><span data-stu-id="76bca-133">With either of the return types, it can take arguments.</span></span>

     [!code-csharp[csProgGuideMain#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#19)]

     <span data-ttu-id="76bca-134">-veya-</span><span class="sxs-lookup"><span data-stu-id="76bca-134">-or-</span></span>

     [!code-csharp[csProgGuideMain#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#18)]

<span data-ttu-id="76bca-135">Parametresi `Main` yöntemi `args`, olan bir `string` program başlatmak için kullanılan komut satırı bağımsız değişkenleri içeren bir dizi.</span><span class="sxs-lookup"><span data-stu-id="76bca-135">The parameter of the `Main` method, `args`, is a `string` array that contains the command-line arguments used to invoke the program.</span></span> <span data-ttu-id="76bca-136">Farklı C++'da dizi yürütülebilir (exe) dosyanın adını içermez.</span><span class="sxs-lookup"><span data-stu-id="76bca-136">Unlike in C++, the array does not include the name of the executable (exe) file.</span></span>

<span data-ttu-id="76bca-137">Komut satırı bağımsız değişkenlerinin nasıl kullanılacağı hakkında daha fazla bilgi için bkz: örneklerde [ana() ve komut satırı bağımsız değişkenleri](../../../csharp/programming-guide/main-and-command-args/index.md) ve [nasıl yapılır: Komut satırını kullanarak derlemeler oluşturma ve kullanma](../../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-and-use-assemblies-using-the-command-line.md).</span><span class="sxs-lookup"><span data-stu-id="76bca-137">For more information about how to use command-line arguments, see the examples in [Main() and Command-Line Arguments](../../../csharp/programming-guide/main-and-command-args/index.md) and [How to: Create and Use Assemblies Using the Command Line](../../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-and-use-assemblies-using-the-command-line.md).</span></span>

<span data-ttu-id="76bca-138">Çağrı <xref:System.Console.ReadKey%2A> sonunda `Main` yöntemi kapatılmasını programınızı F5 tuşuna basarak hata ayıklama modunda çalıştırdığınızda, çıktıyı okuma şansı bulamadan konsol penceresinde engeller.</span><span class="sxs-lookup"><span data-stu-id="76bca-138">The call to <xref:System.Console.ReadKey%2A> at the end of the `Main` method prevents the console window from closing before you have a chance to read the output when you run your program in debug mode, by pressing F5.</span></span>

## <a name="input-and-output"></a><span data-ttu-id="76bca-139">Giriş ve çıkış</span><span class="sxs-lookup"><span data-stu-id="76bca-139">Input and output</span></span>

<span data-ttu-id="76bca-140">C# programları genellikle .NET Framework'ün çalışma zamanı kitaplığı tarafından sağlanan giriş/çıkış hizmetlerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="76bca-140">C# programs generally use the input/output services provided by the run-time library of the .NET Framework.</span></span> <span data-ttu-id="76bca-141">Deyim `System.Console.WriteLine("Hello World!");` kullanan <xref:System.Console.WriteLine%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="76bca-141">The statement `System.Console.WriteLine("Hello World!");` uses the <xref:System.Console.WriteLine%2A> method.</span></span> <span data-ttu-id="76bca-142">Bu çıkış yöntemlerinden biridir <xref:System.Console> Çalışma Zamanı Kitaplığı'nda sınıfı.</span><span class="sxs-lookup"><span data-stu-id="76bca-142">This is one of the output methods of the <xref:System.Console> class in the run-time library.</span></span> <span data-ttu-id="76bca-143">Yeni bir satır tarafından izlenen standart çıktı akışında kendi dize parametresini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="76bca-143">It displays its string parameter on the standard output stream followed by a new line.</span></span> <span data-ttu-id="76bca-144">Diğer <xref:System.Console> yöntemleri farklı giriş ve çıkış işlemleri için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="76bca-144">Other <xref:System.Console> methods are available for different input and output operations.</span></span> <span data-ttu-id="76bca-145">Eklerseniz `using System;` yönerge programın başında, doğrudan kullanabilirsiniz <xref:System> sınıflarını ve yöntemlerini tamamen nitelendirmeden.</span><span class="sxs-lookup"><span data-stu-id="76bca-145">If you include the `using System;` directive at the beginning of the program, you can directly use the <xref:System> classes and methods without fully qualifying them.</span></span> <span data-ttu-id="76bca-146">Örneğin, çağırabilirsiniz `Console.WriteLine` yerine `System.Console.WriteLine`:</span><span class="sxs-lookup"><span data-stu-id="76bca-146">For example, you can call `Console.WriteLine` instead of `System.Console.WriteLine`:</span></span>

 [!code-csharp[csProgGuide#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/using.cs#1)]

 [!code-csharp[csProgGuide#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#23)]

<span data-ttu-id="76bca-147">Giriş/Çıkış yöntemleri hakkında daha fazla bilgi için bkz. <xref:System.IO>.</span><span class="sxs-lookup"><span data-stu-id="76bca-147">For more information about input/output methods, see <xref:System.IO>.</span></span>

## <a name="command-line-compilation-and-execution"></a><span data-ttu-id="76bca-148">Komut satırı derlemesi ve yürütme</span><span class="sxs-lookup"><span data-stu-id="76bca-148">Command-line compilation and execution</span></span>

<span data-ttu-id="76bca-149">"Hello World!" derlemesi</span><span class="sxs-lookup"><span data-stu-id="76bca-149">You can compile the "Hello World!"</span></span> <span data-ttu-id="76bca-150">Visual Studio tümleşik geliştirme ortamı (IDE yerine) komut satırını kullanarak program'ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="76bca-150">program by using the command line instead of the Visual Studio Integrated Development Environment (IDE).</span></span>

### <a name="to-compile-and-run-from-a-command-prompt"></a><span data-ttu-id="76bca-151">Derlemek ve bir komut satırından çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="76bca-151">To compile and run from a command prompt</span></span>

1. <span data-ttu-id="76bca-152">Önceki yordamdaki kodu herhangi bir metin düzenleyiciye yapıştırın ve dosyayı bir metin dosyası olarak kaydedin.</span><span class="sxs-lookup"><span data-stu-id="76bca-152">Paste the code from the preceding procedure into any text editor, and then save the file as a text file.</span></span> <span data-ttu-id="76bca-153">Dosyayı `Hello.cs` olarak adlandırın.</span><span class="sxs-lookup"><span data-stu-id="76bca-153">Name the file `Hello.cs`.</span></span> <span data-ttu-id="76bca-154">C# kaynak kodu dosyaları uzantısını kullanır `.cs`.</span><span class="sxs-lookup"><span data-stu-id="76bca-154">C# source code files use the extension `.cs`.</span></span>

2. <span data-ttu-id="76bca-155">Bir komut istemi penceresi açmak için aşağıdaki adımlardan birini gerçekleştirin:</span><span class="sxs-lookup"><span data-stu-id="76bca-155">Perform one of the following steps to open a command-prompt window:</span></span>

    - <span data-ttu-id="76bca-156">Windows 10 üzerinde **Başlat** menüsünde `Developer Command Prompt`, seçin ve ardından dokunun **VS 2017 için geliştirici komut istemi**.</span><span class="sxs-lookup"><span data-stu-id="76bca-156">In Windows 10, on the **Start** menu, search for `Developer Command Prompt`, and then tap or choose **Developer Command Prompt for VS 2017**.</span></span>

         <span data-ttu-id="76bca-157">Bir geliştirici komut istemi penceresi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="76bca-157">A Developer Command Prompt window appears.</span></span>

    - <span data-ttu-id="76bca-158">Windows 7'de açın **Başlat** menüsünde, geçerli Visual Studio sürümü için klasörünü genişletin, kısayol menüsünü açın **Visual Studio Araçları**ve ardından **Geliştirici komut istemi VS 2017 için**.</span><span class="sxs-lookup"><span data-stu-id="76bca-158">In Windows 7, open the **Start** menu, expand the folder for the current version of Visual Studio, open the shortcut menu for **Visual Studio Tools**, and then choose **Developer Command Prompt for VS 2017**.</span></span>

         <span data-ttu-id="76bca-159">Bir geliştirici komut istemi penceresi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="76bca-159">A Developer Command Prompt window appears.</span></span>

    - <span data-ttu-id="76bca-160">Standart bir komut istemi penceresinden komut satırı yapılarını etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="76bca-160">Enable command-line builds from a standard Command Prompt window.</span></span>

         <span data-ttu-id="76bca-161">Bkz: [nasıl yapılır: Visual Studio komut satırı için ortam değişkenlerini ayarlama](../../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md).</span><span class="sxs-lookup"><span data-stu-id="76bca-161">See [How to: Set Environment Variables for the Visual Studio Command Line](../../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md).</span></span>

3. <span data-ttu-id="76bca-162">Komut İstemi penceresinde içeren klasöre gidin, `Hello.cs` dosya.</span><span class="sxs-lookup"><span data-stu-id="76bca-162">In the command-prompt window, navigate to the folder that contains your `Hello.cs` file.</span></span>

4. <span data-ttu-id="76bca-163">Derlemek için aşağıdaki komutu girin `Hello.cs`.</span><span class="sxs-lookup"><span data-stu-id="76bca-163">Enter the following command to compile `Hello.cs`.</span></span>

     `csc Hello.cs`

     <span data-ttu-id="76bca-164">Programınızı adında bir yürütülebilir dosya hiç derleme hatası varsa `Hello.exe` oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="76bca-164">If your program has no compilation errors, an executable file that is named `Hello.exe` is created.</span></span>

5. <span data-ttu-id="76bca-165">Komut İstemi penceresinde, programı çalıştırmak için aşağıdaki komutu girin:</span><span class="sxs-lookup"><span data-stu-id="76bca-165">In the command-prompt window, enter the following command to run the program:</span></span>

     `Hello`

 <span data-ttu-id="76bca-166">C# derleyicisi ve seçenekleri hakkında daha fazla bilgi için bkz: [C# Derleyici Seçenekleri](../../../csharp/language-reference/compiler-options/index.md).</span><span class="sxs-lookup"><span data-stu-id="76bca-166">For more information about the C# compiler and its options, see [C# Compiler Options](../../../csharp/language-reference/compiler-options/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="76bca-167">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="76bca-167">See also</span></span>

- [<span data-ttu-id="76bca-168">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="76bca-168">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="76bca-169">C# Programı İçinde</span><span class="sxs-lookup"><span data-stu-id="76bca-169">Inside a C# Program</span></span>](../../../csharp/programming-guide/inside-a-program/index.md)
- [<span data-ttu-id="76bca-170">Dizeler</span><span class="sxs-lookup"><span data-stu-id="76bca-170">Strings</span></span>](../../../csharp/programming-guide/strings/index.md)
- [<span data-ttu-id="76bca-171">Örnekler ve öğreticiler</span><span class="sxs-lookup"><span data-stu-id="76bca-171">Samples and tutorials</span></span>](../../../samples-and-tutorials/index.md)
- [<span data-ttu-id="76bca-172">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="76bca-172">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="76bca-173">Ana() ve Komut Satırı Bağımsız Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="76bca-173">Main() and Command-Line Arguments</span></span>](../../../csharp/programming-guide/main-and-command-args/index.md)
- [<span data-ttu-id="76bca-174">Visual C# ve Visual Basic'e Başlarken</span><span class="sxs-lookup"><span data-stu-id="76bca-174">Getting Started with Visual C# and Visual Basic</span></span>](/visualstudio/ide/getting-started-with-visual-csharp-and-visual-basic)