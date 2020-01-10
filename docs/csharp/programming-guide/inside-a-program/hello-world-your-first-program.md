---
title: Merhaba Dünya--Windows veya Mac 'te Visual Studio 'Yu kullanan ilk programınız- C# Programlama Kılavuzu
ms.date: 09/12/2019
f1_keywords:
- cs.program
- vs.csharp.startpage.firstapplication
helpviewer_keywords:
- examples [C#], Hello World
- Hello World example [C#]
ms.assetid: 6493182a-b0b6-4539-a719-518a168cb730
ms.openlocfilehash: 910fa4af1b4e45ce627b589a06910dc168490047
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712149"
---
# <a name="hello-world----your-first-program"></a><span data-ttu-id="0208f-102">Merhaba Dünya--ilk programınız</span><span class="sxs-lookup"><span data-stu-id="0208f-102">Hello World -- Your first program</span></span>

<span data-ttu-id="0208f-103">Bu makalede, geleneksel "Merhaba Dünya!" öğesini oluşturmak için Visual Studio 'Yu kullanacaksınız</span><span class="sxs-lookup"><span data-stu-id="0208f-103">In this article, you'll use Visual Studio to create the traditional "Hello World!"</span></span> <span data-ttu-id="0208f-104">programda.</span><span class="sxs-lookup"><span data-stu-id="0208f-104">program.</span></span> <span data-ttu-id="0208f-105">Visual Studio, .NET geliştirmesi için tasarlanan çok sayıda özelliği olan profesyonel tümleşik bir geliştirme ortamıdır (IDE).</span><span class="sxs-lookup"><span data-stu-id="0208f-105">Visual Studio is a professional Integrated Development Environment (IDE) with many features designed for .NET development.</span></span> <span data-ttu-id="0208f-106">Bu programı oluşturmak için Visual Studio 'daki özelliklerden yalnızca birkaçını kullanacaksınız.</span><span class="sxs-lookup"><span data-stu-id="0208f-106">You'll use only a few of the features in Visual Studio to create this program.</span></span> <span data-ttu-id="0208f-107">Visual Studio hakkında daha fazla bilgi edinmek için bkz. [ C#Visual ile çalışmaya ](/visualstudio/ide/quickstart-csharp-console)başlama.</span><span class="sxs-lookup"><span data-stu-id="0208f-107">To learn more about Visual Studio, see [Getting Started with Visual C#](/visualstudio/ide/quickstart-csharp-console).</span></span>

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="create-a-new-application"></a><span data-ttu-id="0208f-108">Yeni uygulama oluşturma</span><span class="sxs-lookup"><span data-stu-id="0208f-108">Create a new application</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="windowstabwindows"></a>[<span data-ttu-id="0208f-109">Windows</span><span class="sxs-lookup"><span data-stu-id="0208f-109">Windows</span></span>](#tab/windows)

<span data-ttu-id="0208f-110">Visual Studio’yu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="0208f-110">Start Visual Studio.</span></span> <span data-ttu-id="0208f-111">Windows 'da aşağıdaki görüntüyü görürsünüz:</span><span class="sxs-lookup"><span data-stu-id="0208f-111">You'll see the following image on Windows:</span></span>

![Windows 'da Visual Studio hoş geldiniz ekranı](./media/hello-world-your-first-program/visual-studio-windows-start-screen.png)

<span data-ttu-id="0208f-113">Görüntünün sağ alt köşesinde **Yeni proje oluştur** ' u seçin.</span><span class="sxs-lookup"><span data-stu-id="0208f-113">Select **Create a new project** in the lower right corner of the image.</span></span> <span data-ttu-id="0208f-114">Visual Studio **Yeni proje** iletişim kutusunu görüntüler:</span><span class="sxs-lookup"><span data-stu-id="0208f-114">Visual Studio displays the **New Project** dialog:</span></span>

![Windows 'da Visual Studio yeni proje ekranı](./media/hello-world-your-first-program/visual-studio-windows-new-project.png)

> [!NOTE]
> <span data-ttu-id="0208f-116">Visual Studio 'Yu ilk kez başlattıysanız, **son kullanılan proje şablonları** listesi boştur.</span><span class="sxs-lookup"><span data-stu-id="0208f-116">If this is the first time you've started Visual Studio, the **Recent project templates** list is empty.</span></span>

<span data-ttu-id="0208f-117">Yeni proje iletişim kutusunda, "konsol uygulaması (.NET Core)" öğesini seçin ve ardından **İleri**' ye basın.</span><span class="sxs-lookup"><span data-stu-id="0208f-117">On the new project dialog, choose "Console App (.NET Core)" and then press **Next**.</span></span> <span data-ttu-id="0208f-118">Projenize "HelloWorld" gibi bir ad verin ve ardından **Oluştur**' a basın.</span><span class="sxs-lookup"><span data-stu-id="0208f-118">Give your project a name, such as "HelloWorld", then press **Create**.</span></span>

<span data-ttu-id="0208f-119">Visual Studio, projenizi açar.</span><span class="sxs-lookup"><span data-stu-id="0208f-119">Visual Studio opens your project.</span></span> <span data-ttu-id="0208f-120">Zaten temel bir "Merhaba Dünya!"</span><span class="sxs-lookup"><span data-stu-id="0208f-120">It's already a basic "Hello World!"</span></span> <span data-ttu-id="0208f-121">örneğinde.</span><span class="sxs-lookup"><span data-stu-id="0208f-121">example.</span></span> <span data-ttu-id="0208f-122">Projenizi çalıştırmak için `Ctrl` + `F5` tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="0208f-122">Press `Ctrl` + `F5` to run your project.</span></span> <span data-ttu-id="0208f-123">Visual Studio, projenizi oluşturup kaynak kodu yürütülebilir dosyaya dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="0208f-123">Visual Studio builds your project, converting the source code into an executable.</span></span> <span data-ttu-id="0208f-124">Ardından, yeni uygulamanızı çalıştıran bir komut penceresi başlatır.</span><span class="sxs-lookup"><span data-stu-id="0208f-124">Then, it launches a command window that runs your new application.</span></span> <span data-ttu-id="0208f-125">Pencerede aşağıdaki metni görmeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="0208f-125">You should see the following text in the window:</span></span>

```console
Hello World!

C:\Program Files\dotnet\dotnet.exe (process 11964) exited with code 0.
Press any key to close this window . . .
```

<span data-ttu-id="0208f-126">Pencereyi kapatmak için bir tuşa basın.</span><span class="sxs-lookup"><span data-stu-id="0208f-126">Press a key to close the window.</span></span>

# <a name="macostabmacos"></a>[<span data-ttu-id="0208f-127">macOS</span><span class="sxs-lookup"><span data-stu-id="0208f-127">macOS</span></span>](#tab/macos)

<span data-ttu-id="0208f-128">Mac için Visual Studio başlatın.</span><span class="sxs-lookup"><span data-stu-id="0208f-128">Start Visual Studio for Mac.</span></span> <span data-ttu-id="0208f-129">Mac üzerinde aşağıdaki görüntüyü görürsünüz:</span><span class="sxs-lookup"><span data-stu-id="0208f-129">You'll see the following image on Mac:</span></span>

![Mac üzerinde Visual Studio hoş geldiniz ekranı](./media/hello-world-your-first-program/visual-studio-mac-start-screen.png)

> [!NOTE]
> <span data-ttu-id="0208f-131">Mac için Visual Studio ilk kez başladıysanız, **son projeler** listesi boştur.</span><span class="sxs-lookup"><span data-stu-id="0208f-131">If this is the first time you've started Visual Studio for Mac, the **Recent projects** list is empty.</span></span>

<span data-ttu-id="0208f-132">Görüntünün sağ üst köşesindeki **Yeni** ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="0208f-132">Select **New** in the upper right corner of the image.</span></span> <span data-ttu-id="0208f-133">**Yeni proje** iletişim kutusunu Mac için Visual Studio görüntüler:</span><span class="sxs-lookup"><span data-stu-id="0208f-133">Visual Studio for Mac displays the **New Project** dialog:</span></span>

![Mac 'te Visual Studio yeni proje ekranı](./media/hello-world-your-first-program/visual-studio-mac-new-project.png)

<span data-ttu-id="0208f-135">Yeni proje iletişim kutusunda ".NET Core" ve "konsol uygulaması" ' nı seçin ve ardından **İleri**' ye basın.</span><span class="sxs-lookup"><span data-stu-id="0208f-135">On the new project dialog, choose ".NET Core", and "Console App" and then press **Next**.</span></span> <span data-ttu-id="0208f-136">Hedef Framework 'ü seçmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="0208f-136">You'll need to select the target framework.</span></span> <span data-ttu-id="0208f-137">Varsayılan değer iyidir, bu nedenle ileri ' ye basın.</span><span class="sxs-lookup"><span data-stu-id="0208f-137">The default is fine, so press next.</span></span> <span data-ttu-id="0208f-138">Projenize "HelloWorld" gibi bir ad verin ve ardından **Oluştur**' a basın.</span><span class="sxs-lookup"><span data-stu-id="0208f-138">Give your project a name, such as "HelloWorld", then press **Create**.</span></span> <span data-ttu-id="0208f-139">Varsayılan proje konumunu kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0208f-139">You can use the default project location.</span></span> <span data-ttu-id="0208f-140">Bu projeyi kaynak denetimine eklemeyin.</span><span class="sxs-lookup"><span data-stu-id="0208f-140">Don't add this project to source control.</span></span>

<span data-ttu-id="0208f-141">Mac için Visual Studio projenizi açar.</span><span class="sxs-lookup"><span data-stu-id="0208f-141">Visual Studio for Mac opens your project.</span></span> <span data-ttu-id="0208f-142">Zaten temel bir "Merhaba Dünya!"</span><span class="sxs-lookup"><span data-stu-id="0208f-142">It's already a basic "Hello World!"</span></span> <span data-ttu-id="0208f-143">örneğinde.</span><span class="sxs-lookup"><span data-stu-id="0208f-143">example.</span></span> <span data-ttu-id="0208f-144">Projenizi çalıştırmak için `Ctrl` + `Fn` + `F5` basın.</span><span class="sxs-lookup"><span data-stu-id="0208f-144">Press `Ctrl` + `Fn` + `F5` to run your project.</span></span> <span data-ttu-id="0208f-145">Mac için Visual Studio, projenizi derleme ve kaynak kodu çalıştırılabilir dosyaya dönüştürme.</span><span class="sxs-lookup"><span data-stu-id="0208f-145">Visual Studio for Mac builds your project, converting the source code into an executable.</span></span> <span data-ttu-id="0208f-146">Ardından, yeni uygulamanızı çalıştıran bir komut penceresi başlatır.</span><span class="sxs-lookup"><span data-stu-id="0208f-146">Then, it launches a command window that runs your new application.</span></span> <span data-ttu-id="0208f-147">Pencerede aşağıdaki metni görmeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="0208f-147">You should see the following text in the window:</span></span>

```console
Hello World!

Press any key to close this window . . .
```

<span data-ttu-id="0208f-148">Oturumu sonlandırmak için bir tuşa basın.</span><span class="sxs-lookup"><span data-stu-id="0208f-148">Press a key to end the session.</span></span>

---

## <a name="elements-of-a-c-program"></a><span data-ttu-id="0208f-149">Bir C# programın öğeleri</span><span class="sxs-lookup"><span data-stu-id="0208f-149">Elements of a C# program</span></span>

<span data-ttu-id="0208f-150">Bu programın önemli kısımlarını inceleyelim.</span><span class="sxs-lookup"><span data-stu-id="0208f-150">Let's examine the important parts of this program.</span></span> <span data-ttu-id="0208f-151">İlk satır bir açıklama içerir.</span><span class="sxs-lookup"><span data-stu-id="0208f-151">The first line contains a comment.</span></span> <span data-ttu-id="0208f-152">Karakterler `//` satırı geri kalanını açıklamaya dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="0208f-152">The characters `//` convert the rest of the line to a comment.</span></span>

[!code-csharp[csProgGuide#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#32)]

<span data-ttu-id="0208f-153">Ayrıca, bir metin bloğunu `/*` ve `*/` karakterleri arasına ekleyerek açıklama ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0208f-153">You can also comment out a block of text by enclosing it between the `/*` and `*/` characters.</span></span> <span data-ttu-id="0208f-154">Bu, aşağıdaki örnekte gösterilir.</span><span class="sxs-lookup"><span data-stu-id="0208f-154">This is shown in the following example.</span></span>

[!code-csharp[csProgGuide#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#33)]

<span data-ttu-id="0208f-155">C# Konsol uygulaması, denetimin başladığı ve bittiği `Main` bir yöntem içermelidir.</span><span class="sxs-lookup"><span data-stu-id="0208f-155">A C# console application must contain a `Main` method, in which control starts and ends.</span></span> <span data-ttu-id="0208f-156">`Main` yöntemi, nesneleri oluşturduğunuz ve diğer yöntemleri yürütebileceğiniz yerdir.</span><span class="sxs-lookup"><span data-stu-id="0208f-156">The `Main` method is where you create objects and execute other methods.</span></span>

<span data-ttu-id="0208f-157">`Main` yöntemi, bir sınıf veya yapı içinde bulunan [statik](../../language-reference/keywords/static.md) bir yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="0208f-157">The `Main` method is a [static](../../language-reference/keywords/static.md) method that resides inside a class or a struct.</span></span> <span data-ttu-id="0208f-158">Önceki "Merhaba Dünya!"</span><span class="sxs-lookup"><span data-stu-id="0208f-158">In the previous "Hello World!"</span></span> <span data-ttu-id="0208f-159">örnek, `Hello`adlı bir sınıfta bulunur.</span><span class="sxs-lookup"><span data-stu-id="0208f-159">example, it resides in a class named `Hello`.</span></span> <span data-ttu-id="0208f-160">`Main` yöntemini aşağıdaki yöntemlerden biriyle bildirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="0208f-160">You can declare the `Main` method in one of the following ways:</span></span>

- <span data-ttu-id="0208f-161">`void`döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="0208f-161">It can return `void`.</span></span> <span data-ttu-id="0208f-162">Bu, programınızın bir değer döndürmeyeceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="0208f-162">That means your program doesn't return a value.</span></span>

[!code-csharp[csProgGuideMain#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#12)]

- <span data-ttu-id="0208f-163">Ayrıca, bir tamsayı döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="0208f-163">It can also return an integer.</span></span> <span data-ttu-id="0208f-164">Tamsayı, uygulamanız için **Çıkış kodudur** .</span><span class="sxs-lookup"><span data-stu-id="0208f-164">The integer is the **exit code** for your application.</span></span>

[!code-csharp[csProgGuideMain#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#13)]

- <span data-ttu-id="0208f-165">Dönüş türlerinden biri ile bağımsız değişken alabilir.</span><span class="sxs-lookup"><span data-stu-id="0208f-165">With either of the return types, it can take arguments.</span></span>

[!code-csharp[csProgGuideMain#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#19)]

<span data-ttu-id="0208f-166">veya</span><span class="sxs-lookup"><span data-stu-id="0208f-166">-or-</span></span>

[!code-csharp[csProgGuideMain#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#18)]

<span data-ttu-id="0208f-167">`Main` yönteminin parametresi, `args`, programı çağırmak için kullanılan komut satırı bağımsız değişkenlerini içeren bir `string` dizidir.</span><span class="sxs-lookup"><span data-stu-id="0208f-167">The parameter of the `Main` method, `args`, is a `string` array that contains the command-line arguments used to invoke the program.</span></span>

<span data-ttu-id="0208f-168">Komut satırı bağımsız değişkenlerinin nasıl kullanılacağı hakkında daha fazla bilgi için, [ana () ve komut satırı bağımsız değişkenlerinde](../main-and-command-args/index.md)örneklere bakın.</span><span class="sxs-lookup"><span data-stu-id="0208f-168">For more information about how to use command-line arguments, see the examples in [Main() and Command-Line Arguments](../main-and-command-args/index.md).</span></span>

## <a name="input-and-output"></a><span data-ttu-id="0208f-169">Girdi ve çıktı</span><span class="sxs-lookup"><span data-stu-id="0208f-169">Input and output</span></span>

<span data-ttu-id="0208f-170">C#programlar genellikle .NET Framework çalışma zamanı kitaplığı tarafından sunulan giriş/çıkış hizmetlerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="0208f-170">C# programs generally use the input/output services provided by the run-time library of the .NET Framework.</span></span> <span data-ttu-id="0208f-171">Deyimin `System.Console.WriteLine("Hello World!");` <xref:System.Console.WriteLine%2A> yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="0208f-171">The statement `System.Console.WriteLine("Hello World!");` uses the <xref:System.Console.WriteLine%2A> method.</span></span> <span data-ttu-id="0208f-172">Bu, çalışma zamanı kitaplığındaki <xref:System.Console> sınıfının çıkış yöntemlerinden biridir.</span><span class="sxs-lookup"><span data-stu-id="0208f-172">This is one of the output methods of the <xref:System.Console> class in the run-time library.</span></span> <span data-ttu-id="0208f-173">Dize parametresini standart çıkış akışında ve ardından yeni bir satırla görüntüler.</span><span class="sxs-lookup"><span data-stu-id="0208f-173">It displays its string parameter on the standard output stream followed by a new line.</span></span> <span data-ttu-id="0208f-174">Diğer <xref:System.Console> Yöntemler farklı giriş ve çıkış işlemleri için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0208f-174">Other <xref:System.Console> methods are available for different input and output operations.</span></span> <span data-ttu-id="0208f-175">`using System;` yönergesini programın başına eklerseniz, <xref:System> sınıfları ve yöntemleri tamamen nitelemeden doğrudan kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0208f-175">If you include the `using System;` directive at the beginning of the program, you can directly use the <xref:System> classes and methods without fully qualifying them.</span></span> <span data-ttu-id="0208f-176">Örneğin, `System.Console.WriteLine`yerine `Console.WriteLine` çağırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="0208f-176">For example, you can call `Console.WriteLine` instead of `System.Console.WriteLine`:</span></span>

[!code-csharp[csProgGuide#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/using.cs#1)]

[!code-csharp[csProgGuide#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#23)]

<span data-ttu-id="0208f-177">Giriş/çıkış yöntemleri hakkında daha fazla bilgi için bkz. <xref:System.IO>.</span><span class="sxs-lookup"><span data-stu-id="0208f-177">For more information about input/output methods, see <xref:System.IO>.</span></span>

## <a name="see-also"></a><span data-ttu-id="0208f-178">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0208f-178">See also</span></span>

- [<span data-ttu-id="0208f-179">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="0208f-179">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="0208f-180">Örnekler ve öğreticiler</span><span class="sxs-lookup"><span data-stu-id="0208f-180">Samples and tutorials</span></span>](../../../samples-and-tutorials/index.md)
- [<span data-ttu-id="0208f-181">Ana() ve Komut Satırı Bağımsız Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="0208f-181">Main() and Command-Line Arguments</span></span>](../main-and-command-args/index.md)
- [<span data-ttu-id="0208f-182">Görsele BaşlarkenC#</span><span class="sxs-lookup"><span data-stu-id="0208f-182">Getting Started with Visual C#</span></span>](/visualstudio/ide/quickstart-csharp-console)
