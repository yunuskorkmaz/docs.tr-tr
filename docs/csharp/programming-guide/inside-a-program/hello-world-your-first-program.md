---
title: Merhaba Dünya--ilk program C# programlama kılavuzunuz
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- cs.program
- vs.csharp.startpage.firstapplication
helpviewer_keywords:
- examples [C#], Hello World
- Hello World example [C#]
ms.assetid: 6493182a-b0b6-4539-a719-518a168cb730
ms.openlocfilehash: 9a50de0bb583a1dfccfa609be1cca732868505ba
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69589380"
---
# <a name="hello-world----your-first-program-c-programming-guide"></a><span data-ttu-id="9f314-102">Merhaba Dünya--ilk programınız (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="9f314-102">Hello World -- Your first program (C# Programming Guide)</span></span>

<span data-ttu-id="9f314-103">Aşağıdaki yordam geleneksel bir C# "Merhaba Dünya!" sürümü oluşturuyor</span><span class="sxs-lookup"><span data-stu-id="9f314-103">The following procedure creates a C# version of the traditional "Hello World!"</span></span> <span data-ttu-id="9f314-104">programda.</span><span class="sxs-lookup"><span data-stu-id="9f314-104">program.</span></span> <span data-ttu-id="9f314-105">Program dizeyi görüntüler`Hello World!`</span><span class="sxs-lookup"><span data-stu-id="9f314-105">The program displays the string `Hello World!`</span></span>

<span data-ttu-id="9f314-106">Tanıtım kavramlarıyla ilgili daha fazla örnek için bkz. [Visual C# ve Visual Basic kullanmaya](/visualstudio/ide/getting-started-with-visual-csharp-and-visual-basic)başlama.</span><span class="sxs-lookup"><span data-stu-id="9f314-106">For more examples of introductory concepts, see [Getting Started with Visual C# and Visual Basic](/visualstudio/ide/getting-started-with-visual-csharp-and-visual-basic).</span></span>

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-create-and-run-a-console-application"></a><span data-ttu-id="9f314-107">Bir konsol uygulaması oluşturmak ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="9f314-107">To create and run a console application</span></span>

1. <span data-ttu-id="9f314-108">Visual Studio’yu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="9f314-108">Start Visual Studio.</span></span>

2. <span data-ttu-id="9f314-109">Menü çubuğunda, **dosya**, **yeni**, **proje**.</span><span class="sxs-lookup"><span data-stu-id="9f314-109">On the menu bar, choose **File**, **New**, **Project**.</span></span>

     <span data-ttu-id="9f314-110">**Yeni proje** iletişim kutusu açılır.</span><span class="sxs-lookup"><span data-stu-id="9f314-110">The **New Project** dialog box opens.</span></span>

3. <span data-ttu-id="9f314-111">**Yüklü**' i genişletin, **Şablonlar**' ı genişletin, **C#görsel**' i genişletin ve **konsol uygulaması**' nı</span><span class="sxs-lookup"><span data-stu-id="9f314-111">Expand **Installed**, expand **Templates**, expand **Visual C#**, and then choose **Console Application**.</span></span>

4. <span data-ttu-id="9f314-112">**Ad** kutusunda, projeniz için bir ad belirtin ve sonra **Tamam** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="9f314-112">In the **Name** box, specify a name for your project, and then choose the **OK** button.</span></span>

     <span data-ttu-id="9f314-113">Yeni proje **Çözüm Gezgini**görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="9f314-113">The new project appears in **Solution Explorer**.</span></span>

5. <span data-ttu-id="9f314-114">**Kod Düzenleyicisi**'nde program.cs açık değilse, **Çözüm Gezgini**için kısayol menüsünü açın ve sonra **kodu görüntüle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="9f314-114">If Program.cs isn't open in the **Code Editor**, open the shortcut menu for **Program.cs** in **Solution Explorer**, and then choose **View Code**.</span></span>

6. <span data-ttu-id="9f314-115">Program.cs içeriğini aşağıdaki kodla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="9f314-115">Replace the contents of Program.cs with the following code.</span></span>

     [!code-csharp[csProgGuide#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#21)]

7. <span data-ttu-id="9f314-116">Projeyi çalıştırmak için F5 tuşunu seçin.</span><span class="sxs-lookup"><span data-stu-id="9f314-116">Choose the F5 key to run the project.</span></span> <span data-ttu-id="9f314-117">Satırı içeren bir komut Istemi penceresi görünür`Hello World!`</span><span class="sxs-lookup"><span data-stu-id="9f314-117">A Command Prompt window appears that contains the line `Hello World!`</span></span>

<span data-ttu-id="9f314-118">Daha sonra, bu programın önemli bölümleri incelenir.</span><span class="sxs-lookup"><span data-stu-id="9f314-118">Next, the important parts of this program are examined.</span></span>

## <a name="comments"></a><span data-ttu-id="9f314-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9f314-119">Comments</span></span>

<span data-ttu-id="9f314-120">İlk satır bir açıklama içerir.</span><span class="sxs-lookup"><span data-stu-id="9f314-120">The first line contains a comment.</span></span> <span data-ttu-id="9f314-121">Karakterler `//` satırın geri kalanını açıklamaya dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="9f314-121">The characters `//` convert the rest of the line to a comment.</span></span>

 [!code-csharp[csProgGuide#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#32)]

<span data-ttu-id="9f314-122">Ayrıca, bir metin bloğunu, `/*` ve `*/` karakterleri arasına ekleyerek açıklama ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9f314-122">You can also comment out a block of text by enclosing it between the `/*` and `*/` characters.</span></span> <span data-ttu-id="9f314-123">Bu, aşağıdaki örnekte gösterilir.</span><span class="sxs-lookup"><span data-stu-id="9f314-123">This is shown in the following example.</span></span>

 [!code-csharp[csProgGuide#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#33)]

## <a name="main-method"></a><span data-ttu-id="9f314-124">Main yöntemi</span><span class="sxs-lookup"><span data-stu-id="9f314-124">Main method</span></span>

<span data-ttu-id="9f314-125">C# Konsol uygulaması, denetimin başladığı ve `Main` bittiği bir yöntemi içermelidir.</span><span class="sxs-lookup"><span data-stu-id="9f314-125">A C# console application must contain a `Main` method, in which control starts and ends.</span></span> <span data-ttu-id="9f314-126">`Main` Yöntemi nesne oluşturduğunuz ve diğer yöntemleri yürütebileceğiniz yerdir.</span><span class="sxs-lookup"><span data-stu-id="9f314-126">The `Main` method is where you create objects and execute other methods.</span></span>

<span data-ttu-id="9f314-127">Yöntemi, bir sınıf veya yapı içinde bulunan statik bir yöntemdir. [](../../language-reference/keywords/static.md) `Main`</span><span class="sxs-lookup"><span data-stu-id="9f314-127">The `Main` method is a [static](../../language-reference/keywords/static.md) method that resides inside a class or a struct.</span></span> <span data-ttu-id="9f314-128">Önceki "Merhaba Dünya!"</span><span class="sxs-lookup"><span data-stu-id="9f314-128">In the previous "Hello World!"</span></span> <span data-ttu-id="9f314-129">örnek, adlı `Hello`bir sınıfta bulunur.</span><span class="sxs-lookup"><span data-stu-id="9f314-129">example, it resides in a class named `Hello`.</span></span> <span data-ttu-id="9f314-130">`Main` Yöntemi aşağıdaki yöntemlerden biriyle bildirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="9f314-130">You can declare the `Main` method in one of the following ways:</span></span>

- <span data-ttu-id="9f314-131">Bu, döndürebilir `void`.</span><span class="sxs-lookup"><span data-stu-id="9f314-131">It can return `void`.</span></span>

     [!code-csharp[csProgGuideMain#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#12)]

- <span data-ttu-id="9f314-132">Ayrıca, bir tamsayı döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="9f314-132">It can also return an integer.</span></span>

     [!code-csharp[csProgGuideMain#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#13)]

- <span data-ttu-id="9f314-133">Dönüş türlerinden biri ile bağımsız değişken alabilir.</span><span class="sxs-lookup"><span data-stu-id="9f314-133">With either of the return types, it can take arguments.</span></span>

     [!code-csharp[csProgGuideMain#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#19)]

     <span data-ttu-id="9f314-134">-veya-</span><span class="sxs-lookup"><span data-stu-id="9f314-134">-or-</span></span>

     [!code-csharp[csProgGuideMain#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#18)]

<span data-ttu-id="9f314-135">Yönteminin parametresi, programı çağırmak için kullanılan komut satırı `string` bağımsız değişkenlerini içeren bir dizidir. `args` `Main`</span><span class="sxs-lookup"><span data-stu-id="9f314-135">The parameter of the `Main` method, `args`, is a `string` array that contains the command-line arguments used to invoke the program.</span></span> <span data-ttu-id="9f314-136">Öğesinden farklı C++olarak, dizi yürütülebilir (exe) dosyanın adını içermez.</span><span class="sxs-lookup"><span data-stu-id="9f314-136">Unlike in C++, the array does not include the name of the executable (exe) file.</span></span>

<span data-ttu-id="9f314-137">Komut satırı bağımsız değişkenlerinin nasıl kullanılacağı hakkında daha fazla bilgi için, [ana () ve komut satırı bağımsız değişkenlerinde](../main-and-command-args/index.md) örneklere ve [nasıl yapılacağını görün: Komut satırını](../concepts/assemblies-gac/how-to-create-and-use-assemblies-using-the-command-line.md)kullanarak derlemeleri oluşturun ve kullanın.</span><span class="sxs-lookup"><span data-stu-id="9f314-137">For more information about how to use command-line arguments, see the examples in [Main() and Command-Line Arguments](../main-and-command-args/index.md) and [How to: Create and Use Assemblies Using the Command Line](../concepts/assemblies-gac/how-to-create-and-use-assemblies-using-the-command-line.md).</span></span>

<span data-ttu-id="9f314-138">`Main` Yönteminin sonunda öğesine yapılan <xref:System.Console.ReadKey%2A> çağrı, F5 tuşuna basarak, programınızı hata ayıklama modunda çalıştırdığınızda çıktıyı okuma şansınız olmadan önce konsol penceresinin bitmesini önler.</span><span class="sxs-lookup"><span data-stu-id="9f314-138">The call to <xref:System.Console.ReadKey%2A> at the end of the `Main` method prevents the console window from closing before you have a chance to read the output when you run your program in debug mode, by pressing F5.</span></span>

## <a name="input-and-output"></a><span data-ttu-id="9f314-139">Girdi ve çıktı</span><span class="sxs-lookup"><span data-stu-id="9f314-139">Input and output</span></span>

<span data-ttu-id="9f314-140">C#programlar genellikle .NET Framework çalışma zamanı kitaplığı tarafından sunulan giriş/çıkış hizmetlerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="9f314-140">C# programs generally use the input/output services provided by the run-time library of the .NET Framework.</span></span> <span data-ttu-id="9f314-141">İfade `System.Console.WriteLine("Hello World!");` yöntemini<xref:System.Console.WriteLine%2A> kullanır.</span><span class="sxs-lookup"><span data-stu-id="9f314-141">The statement `System.Console.WriteLine("Hello World!");` uses the <xref:System.Console.WriteLine%2A> method.</span></span> <span data-ttu-id="9f314-142">Bu, çalışma zamanı kitaplığındaki <xref:System.Console> sınıfının çıkış yöntemlerinden biridir.</span><span class="sxs-lookup"><span data-stu-id="9f314-142">This is one of the output methods of the <xref:System.Console> class in the run-time library.</span></span> <span data-ttu-id="9f314-143">Dize parametresini standart çıkış akışında ve ardından yeni bir satırla görüntüler.</span><span class="sxs-lookup"><span data-stu-id="9f314-143">It displays its string parameter on the standard output stream followed by a new line.</span></span> <span data-ttu-id="9f314-144">Farklı <xref:System.Console> giriş ve çıkış işlemleri için diğer yöntemler kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="9f314-144">Other <xref:System.Console> methods are available for different input and output operations.</span></span> <span data-ttu-id="9f314-145">Programın başına `using System;` yönergesini eklerseniz, <xref:System> sınıfları ve yöntemleri tamamen nitelemeden doğrudan kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9f314-145">If you include the `using System;` directive at the beginning of the program, you can directly use the <xref:System> classes and methods without fully qualifying them.</span></span> <span data-ttu-id="9f314-146">Örneğin, `Console.WriteLine` `System.Console.WriteLine`yerine şunu çağırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="9f314-146">For example, you can call `Console.WriteLine` instead of `System.Console.WriteLine`:</span></span>

 [!code-csharp[csProgGuide#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/using.cs#1)]

 [!code-csharp[csProgGuide#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#23)]

<span data-ttu-id="9f314-147">Giriş/çıkış yöntemleri hakkında daha fazla bilgi için bkz <xref:System.IO>.</span><span class="sxs-lookup"><span data-stu-id="9f314-147">For more information about input/output methods, see <xref:System.IO>.</span></span>

## <a name="command-line-compilation-and-execution"></a><span data-ttu-id="9f314-148">Komut satırı derleme ve yürütme</span><span class="sxs-lookup"><span data-stu-id="9f314-148">Command-line compilation and execution</span></span>

<span data-ttu-id="9f314-149">"Merhaba Dünya!" öğesini derleyebilirsiniz</span><span class="sxs-lookup"><span data-stu-id="9f314-149">You can compile the "Hello World!"</span></span> <span data-ttu-id="9f314-150">Visual Studio tümleşik geliştirme ortamı (IDE) yerine komut satırını kullanarak program.</span><span class="sxs-lookup"><span data-stu-id="9f314-150">program by using the command line instead of the Visual Studio Integrated Development Environment (IDE).</span></span>

### <a name="to-compile-and-run-from-a-command-prompt"></a><span data-ttu-id="9f314-151">Derlemek ve bir komut satırından çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="9f314-151">To compile and run from a command prompt</span></span>

1. <span data-ttu-id="9f314-152">Önceki yordamdan kodu herhangi bir metin düzenleyicisine yapıştırın ve sonra dosyayı bir metin dosyası olarak kaydedin.</span><span class="sxs-lookup"><span data-stu-id="9f314-152">Paste the code from the preceding procedure into any text editor, and then save the file as a text file.</span></span> <span data-ttu-id="9f314-153">Dosyayı `Hello.cs` olarak adlandırın.</span><span class="sxs-lookup"><span data-stu-id="9f314-153">Name the file `Hello.cs`.</span></span> <span data-ttu-id="9f314-154">C#kaynak kodu dosyaları uzantısını `.cs`kullanır.</span><span class="sxs-lookup"><span data-stu-id="9f314-154">C# source code files use the extension `.cs`.</span></span>

2. <span data-ttu-id="9f314-155">Bir komut istemi penceresi açmak için aşağıdaki adımlardan birini gerçekleştirin:</span><span class="sxs-lookup"><span data-stu-id="9f314-155">Perform one of the following steps to open a command-prompt window:</span></span>

    - <span data-ttu-id="9f314-156">Windows 10 ' da, **Başlat** menüsünde, için `Developer Command Prompt`arama yapın ve sonra **vs 2017 için geliştirici komut istemi**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="9f314-156">In Windows 10, on the **Start** menu, search for `Developer Command Prompt`, and then tap or choose **Developer Command Prompt for VS 2017**.</span></span>

         <span data-ttu-id="9f314-157">Geliştirici Komut İstemi bir pencere görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="9f314-157">A Developer Command Prompt window appears.</span></span>

    - <span data-ttu-id="9f314-158">Windows 7 ' de, **Başlat** menüsünü açın, Visual Studio 'nun geçerli sürümüne ait klasörü genişletin, **Visual Studio Araçları**için KıSAYOL menüsünü açın ve **vs 2017 için geliştirici komut istemi**öğesini seçin.</span><span class="sxs-lookup"><span data-stu-id="9f314-158">In Windows 7, open the **Start** menu, expand the folder for the current version of Visual Studio, open the shortcut menu for **Visual Studio Tools**, and then choose **Developer Command Prompt for VS 2017**.</span></span>

         <span data-ttu-id="9f314-159">Geliştirici Komut İstemi bir pencere görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="9f314-159">A Developer Command Prompt window appears.</span></span>

    - <span data-ttu-id="9f314-160">Komut satırı derlemelerini standart bir komut Istemi penceresinden etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="9f314-160">Enable command-line builds from a standard Command Prompt window.</span></span>

         <span data-ttu-id="9f314-161">Bkz [. nasıl yapılır: Visual Studio komut satırı](../../language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md)için ortam değişkenlerini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="9f314-161">See [How to: Set Environment Variables for the Visual Studio Command Line](../../language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md).</span></span>

3. <span data-ttu-id="9f314-162">Komut istemi penceresinde, `Hello.cs` dosyanızı içeren klasöre gidin.</span><span class="sxs-lookup"><span data-stu-id="9f314-162">In the command-prompt window, navigate to the folder that contains your `Hello.cs` file.</span></span>

4. <span data-ttu-id="9f314-163">Derlemek `Hello.cs`için aşağıdaki komutu girin.</span><span class="sxs-lookup"><span data-stu-id="9f314-163">Enter the following command to compile `Hello.cs`.</span></span>

     `csc Hello.cs`

     <span data-ttu-id="9f314-164">Programınızın derleme hatası yoksa, adında `Hello.exe` bir yürütülebilir dosya oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="9f314-164">If your program has no compilation errors, an executable file that is named `Hello.exe` is created.</span></span>

5. <span data-ttu-id="9f314-165">Komut istemi penceresinde, programı çalıştırmak için aşağıdaki komutu girin:</span><span class="sxs-lookup"><span data-stu-id="9f314-165">In the command-prompt window, enter the following command to run the program:</span></span>

     `Hello`

 <span data-ttu-id="9f314-166">C# Derleyici ve seçenekleri hakkında daha fazla bilgi için bkz [ C# . derleyici seçenekleri](../../language-reference/compiler-options/index.md).</span><span class="sxs-lookup"><span data-stu-id="9f314-166">For more information about the C# compiler and its options, see [C# Compiler Options](../../language-reference/compiler-options/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="9f314-167">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9f314-167">See also</span></span>

- [<span data-ttu-id="9f314-168">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="9f314-168">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="9f314-169">C# Programı İçinde</span><span class="sxs-lookup"><span data-stu-id="9f314-169">Inside a C# Program</span></span>](./index.md)
- [<span data-ttu-id="9f314-170">Dizeler</span><span class="sxs-lookup"><span data-stu-id="9f314-170">Strings</span></span>](../strings/index.md)
- [<span data-ttu-id="9f314-171">Örnekler ve öğreticiler</span><span class="sxs-lookup"><span data-stu-id="9f314-171">Samples and tutorials</span></span>](../../../samples-and-tutorials/index.md)
- [<span data-ttu-id="9f314-172">C#Başvurunun</span><span class="sxs-lookup"><span data-stu-id="9f314-172">C# Reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="9f314-173">Ana() ve Komut Satırı Bağımsız Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="9f314-173">Main() and Command-Line Arguments</span></span>](../main-and-command-args/index.md)
- [<span data-ttu-id="9f314-174">Visual C# ve Visual Basic'e Başlarken</span><span class="sxs-lookup"><span data-stu-id="9f314-174">Getting Started with Visual C# and Visual Basic</span></span>](/visualstudio/ide/getting-started-with-visual-csharp-and-visual-basic)
