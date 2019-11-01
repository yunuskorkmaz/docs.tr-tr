---
title: Merhaba Dünya--Windows veya Mac 'te Visual Studio 'Yu kullanan ilk programınız- C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 09/12/2019
f1_keywords:
- cs.program
- vs.csharp.startpage.firstapplication
helpviewer_keywords:
- examples [C#], Hello World
- Hello World example [C#]
ms.assetid: 6493182a-b0b6-4539-a719-518a168cb730
ms.openlocfilehash: edab64bf02a2b60cce21af536d2da98193dea9a1
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73196220"
---
# <a name="hello-world----your-first-program"></a><span data-ttu-id="90ce9-102">Merhaba Dünya--ilk programınız</span><span class="sxs-lookup"><span data-stu-id="90ce9-102">Hello World -- Your first program</span></span>

<span data-ttu-id="90ce9-103">Bu makalede, geleneksel "Merhaba Dünya!" öğesini oluşturmak için Visual Studio 'Yu kullanacaksınız</span><span class="sxs-lookup"><span data-stu-id="90ce9-103">In this article, you'll use Visual Studio to create the traditional "Hello World!"</span></span> <span data-ttu-id="90ce9-104">programda.</span><span class="sxs-lookup"><span data-stu-id="90ce9-104">program.</span></span> <span data-ttu-id="90ce9-105">Visual Studio, .NET geliştirmesi için tasarlanan çok sayıda özelliği olan profesyonel tümleşik bir geliştirme ortamıdır (IDE).</span><span class="sxs-lookup"><span data-stu-id="90ce9-105">Visual Studio is a professional Integrated Development Environment (IDE) with many features designed for .NET development.</span></span> <span data-ttu-id="90ce9-106">Bu programı oluşturmak için Visual Studio 'daki özelliklerden yalnızca birkaçını kullanacaksınız.</span><span class="sxs-lookup"><span data-stu-id="90ce9-106">You'll use only a few of the features in Visual Studio to create this program.</span></span> <span data-ttu-id="90ce9-107">Visual Studio hakkında daha fazla bilgi edinmek için bkz. [ C#Visual ile çalışmaya ](/visualstudio/ide/quickstart-csharp-console)başlama.</span><span class="sxs-lookup"><span data-stu-id="90ce9-107">To learn more about Visual Studio, see [Getting Started with Visual C#](/visualstudio/ide/quickstart-csharp-console).</span></span>

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="create-a-new-application"></a><span data-ttu-id="90ce9-108">Yeni bir uygulama oluşturun</span><span class="sxs-lookup"><span data-stu-id="90ce9-108">Create a new application</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="windowstabwindows"></a>[<span data-ttu-id="90ce9-109">Windows</span><span class="sxs-lookup"><span data-stu-id="90ce9-109">Windows</span></span>](#tab/windows)

<span data-ttu-id="90ce9-110">Visual Studio 'Yu başlatın.</span><span class="sxs-lookup"><span data-stu-id="90ce9-110">Start Visual Studio.</span></span> <span data-ttu-id="90ce9-111">Windows 'da aşağıdaki görüntüyü görürsünüz:</span><span class="sxs-lookup"><span data-stu-id="90ce9-111">You'll see the following image on Windows:</span></span>

![Windows 'da Visual Studio hoş geldiniz ekranı](./media/hello-world-your-first-program/visual-studio-windows-start-screen.png)

<span data-ttu-id="90ce9-113">Görüntünün sağ alt köşesinde **Yeni proje oluştur** ' u seçin.</span><span class="sxs-lookup"><span data-stu-id="90ce9-113">Select **Create a new project** in the lower right corner of the image.</span></span> <span data-ttu-id="90ce9-114">Visual Studio **Yeni proje** iletişim kutusunu görüntüler:</span><span class="sxs-lookup"><span data-stu-id="90ce9-114">Visual Studio displays the **New Project** dialog:</span></span>

![Windows 'da Visual Studio yeni proje ekranı](./media/hello-world-your-first-program/visual-studio-windows-new-project.png)

> [!NOTE]
> <span data-ttu-id="90ce9-116">Visual Studio 'Yu ilk kez başlattıysanız, **son kullanılan proje şablonları** listesi boştur.</span><span class="sxs-lookup"><span data-stu-id="90ce9-116">If this is the first time you've started Visual Studio, the **Recent project templates** list is empty.</span></span>

<span data-ttu-id="90ce9-117">Yeni proje iletişim kutusunda, "konsol uygulaması (.NET Core)" öğesini seçin ve ardından **İleri**' ye basın.</span><span class="sxs-lookup"><span data-stu-id="90ce9-117">On the new project dialog, choose "Console App (.NET Core)" and then press **Next**.</span></span> <span data-ttu-id="90ce9-118">Projenize "HelloWorld" gibi bir ad verin ve ardından **Oluştur**' a basın.</span><span class="sxs-lookup"><span data-stu-id="90ce9-118">Give your project a name, such as "HelloWorld", then press **Create**.</span></span>

<span data-ttu-id="90ce9-119">Visual Studio, projenizi açar.</span><span class="sxs-lookup"><span data-stu-id="90ce9-119">Visual Studio opens your project.</span></span> <span data-ttu-id="90ce9-120">Zaten temel bir "Merhaba Dünya!"</span><span class="sxs-lookup"><span data-stu-id="90ce9-120">It's already a basic "Hello World!"</span></span> <span data-ttu-id="90ce9-121">örneğinde.</span><span class="sxs-lookup"><span data-stu-id="90ce9-121">example.</span></span> <span data-ttu-id="90ce9-122">Projenizi çalıştırmak için `Ctrl` + `F5` tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="90ce9-122">Press `Ctrl` + `F5` to run your project.</span></span> <span data-ttu-id="90ce9-123">Visual Studio, projenizi oluşturup kaynak kodu yürütülebilir dosyaya dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="90ce9-123">Visual Studio builds your project, converting the source code into an executable.</span></span> <span data-ttu-id="90ce9-124">Ardından, yeni uygulamanızı çalıştıran bir komut penceresi başlatır.</span><span class="sxs-lookup"><span data-stu-id="90ce9-124">Then, it launches a command window that runs your new application.</span></span> <span data-ttu-id="90ce9-125">Pencerede aşağıdaki metni görmeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="90ce9-125">You should see the following text in the window:</span></span>

```console
Hello World!

C:\Program Files\dotnet\dotnet.exe (process 11964) exited with code 0.
Press any key to close this window . . .
```

<span data-ttu-id="90ce9-126">Pencereyi kapatmak için bir tuşa basın.</span><span class="sxs-lookup"><span data-stu-id="90ce9-126">Press a key to close the window.</span></span>

# <a name="macostabmacos"></a>[<span data-ttu-id="90ce9-127">macOS</span><span class="sxs-lookup"><span data-stu-id="90ce9-127">macOS</span></span>](#tab/macos)

<span data-ttu-id="90ce9-128">Mac için Visual Studio başlatın.</span><span class="sxs-lookup"><span data-stu-id="90ce9-128">Start Visual Studio for Mac.</span></span> <span data-ttu-id="90ce9-129">Mac üzerinde aşağıdaki görüntüyü görürsünüz:</span><span class="sxs-lookup"><span data-stu-id="90ce9-129">You'll see the following image on Mac:</span></span>

![Mac üzerinde Visual Studio hoş geldiniz ekranı](./media/hello-world-your-first-program/visual-studio-mac-start-screen.png)

> [!NOTE]
> <span data-ttu-id="90ce9-131">Mac için Visual Studio ilk kez başladıysanız, **son projeler** listesi boştur.</span><span class="sxs-lookup"><span data-stu-id="90ce9-131">If this is the first time you've started Visual Studio for Mac, the **Recent projects** list is empty.</span></span>

<span data-ttu-id="90ce9-132">Görüntünün sağ üst köşesindeki **Yeni** ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="90ce9-132">Select **New** in the upper right corner of the image.</span></span> <span data-ttu-id="90ce9-133">**Yeni proje** iletişim kutusunu Mac için Visual Studio görüntüler:</span><span class="sxs-lookup"><span data-stu-id="90ce9-133">Visual Studio for Mac displays the **New Project** dialog:</span></span>

![Mac 'te Visual Studio yeni proje ekranı](./media/hello-world-your-first-program/visual-studio-mac-new-project.png)

<span data-ttu-id="90ce9-135">Yeni proje iletişim kutusunda ".NET Core" ve "konsol uygulaması" ' nı seçin ve ardından **İleri**' ye basın.</span><span class="sxs-lookup"><span data-stu-id="90ce9-135">On the new project dialog, choose ".NET Core", and "Console App" and then press **Next**.</span></span> <span data-ttu-id="90ce9-136">Hedef Framework 'ü seçmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="90ce9-136">You'll need to select the target framework.</span></span> <span data-ttu-id="90ce9-137">Varsayılan değer iyidir, bu nedenle ileri ' ye basın.</span><span class="sxs-lookup"><span data-stu-id="90ce9-137">The default is fine, so press next.</span></span> <span data-ttu-id="90ce9-138">Projenize "HelloWorld" gibi bir ad verin ve ardından **Oluştur**' a basın.</span><span class="sxs-lookup"><span data-stu-id="90ce9-138">Give your project a name, such as "HelloWorld", then press **Create**.</span></span> <span data-ttu-id="90ce9-139">Varsayılan proje konumunu kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="90ce9-139">You can use the default project location.</span></span> <span data-ttu-id="90ce9-140">Bu projeyi kaynak denetimine eklemeyin.</span><span class="sxs-lookup"><span data-stu-id="90ce9-140">Don't add this project to source control.</span></span>

<span data-ttu-id="90ce9-141">Mac için Visual Studio projenizi açar.</span><span class="sxs-lookup"><span data-stu-id="90ce9-141">Visual Studio for Mac opens your project.</span></span> <span data-ttu-id="90ce9-142">Zaten temel bir "Merhaba Dünya!"</span><span class="sxs-lookup"><span data-stu-id="90ce9-142">It's already a basic "Hello World!"</span></span> <span data-ttu-id="90ce9-143">örneğinde.</span><span class="sxs-lookup"><span data-stu-id="90ce9-143">example.</span></span> <span data-ttu-id="90ce9-144">Projenizi çalıştırmak için `Ctrl` + `Fn` + `F5` basın.</span><span class="sxs-lookup"><span data-stu-id="90ce9-144">Press `Ctrl` + `Fn` + `F5` to run your project.</span></span> <span data-ttu-id="90ce9-145">Mac için Visual Studio, projenizi derleme ve kaynak kodu çalıştırılabilir dosyaya dönüştürme.</span><span class="sxs-lookup"><span data-stu-id="90ce9-145">Visual Studio for Mac builds your project, converting the source code into an executable.</span></span> <span data-ttu-id="90ce9-146">Ardından, yeni uygulamanızı çalıştıran bir komut penceresi başlatır.</span><span class="sxs-lookup"><span data-stu-id="90ce9-146">Then, it launches a command window that runs your new application.</span></span> <span data-ttu-id="90ce9-147">Pencerede aşağıdaki metni görmeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="90ce9-147">You should see the following text in the window:</span></span>

```console
Hello World!

Press any key to close this window . . .
```

<span data-ttu-id="90ce9-148">Oturumu sonlandırmak için bir tuşa basın.</span><span class="sxs-lookup"><span data-stu-id="90ce9-148">Press a key to end the session.</span></span>

---

## <a name="elements-of-a-c-program"></a><span data-ttu-id="90ce9-149">Bir C# programın öğeleri</span><span class="sxs-lookup"><span data-stu-id="90ce9-149">Elements of a C# program</span></span>

<span data-ttu-id="90ce9-150">Bu programın önemli kısımlarını inceleyelim.</span><span class="sxs-lookup"><span data-stu-id="90ce9-150">Let's examine the important parts of this program.</span></span> <span data-ttu-id="90ce9-151">İlk satır bir açıklama içerir.</span><span class="sxs-lookup"><span data-stu-id="90ce9-151">The first line contains a comment.</span></span> <span data-ttu-id="90ce9-152">Karakterler `//` satırı geri kalanını açıklamaya dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="90ce9-152">The characters `//` convert the rest of the line to a comment.</span></span>

[!code-csharp[csProgGuide#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#32)]

<span data-ttu-id="90ce9-153">Ayrıca, bir metin bloğunu `/*` ve `*/` karakterleri arasına ekleyerek açıklama ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="90ce9-153">You can also comment out a block of text by enclosing it between the `/*` and `*/` characters.</span></span> <span data-ttu-id="90ce9-154">Bu, aşağıdaki örnekte gösterilir.</span><span class="sxs-lookup"><span data-stu-id="90ce9-154">This is shown in the following example.</span></span>

[!code-csharp[csProgGuide#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#33)]

<span data-ttu-id="90ce9-155">C# Konsol uygulaması, denetimin başladığı ve bittiği `Main` bir yöntem içermelidir.</span><span class="sxs-lookup"><span data-stu-id="90ce9-155">A C# console application must contain a `Main` method, in which control starts and ends.</span></span> <span data-ttu-id="90ce9-156">`Main` yöntemi, nesneleri oluşturduğunuz ve diğer yöntemleri yürütebileceğiniz yerdir.</span><span class="sxs-lookup"><span data-stu-id="90ce9-156">The `Main` method is where you create objects and execute other methods.</span></span>

<span data-ttu-id="90ce9-157">`Main` yöntemi, bir sınıf veya yapı içinde bulunan [statik](../../language-reference/keywords/static.md) bir yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="90ce9-157">The `Main` method is a [static](../../language-reference/keywords/static.md) method that resides inside a class or a struct.</span></span> <span data-ttu-id="90ce9-158">Önceki "Merhaba Dünya!"</span><span class="sxs-lookup"><span data-stu-id="90ce9-158">In the previous "Hello World!"</span></span> <span data-ttu-id="90ce9-159">örnek, `Hello`adlı bir sınıfta bulunur.</span><span class="sxs-lookup"><span data-stu-id="90ce9-159">example, it resides in a class named `Hello`.</span></span> <span data-ttu-id="90ce9-160">`Main` yöntemini aşağıdaki yöntemlerden biriyle bildirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="90ce9-160">You can declare the `Main` method in one of the following ways:</span></span>

- <span data-ttu-id="90ce9-161">`void`döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="90ce9-161">It can return `void`.</span></span> <span data-ttu-id="90ce9-162">Bu, programınızın bir değer döndürmeyeceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="90ce9-162">That means your program doesn't return a value.</span></span>

[!code-csharp[csProgGuideMain#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#12)]

- <span data-ttu-id="90ce9-163">Ayrıca, bir tamsayı döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="90ce9-163">It can also return an integer.</span></span> <span data-ttu-id="90ce9-164">Tamsayı, uygulamanız için **Çıkış kodudur** .</span><span class="sxs-lookup"><span data-stu-id="90ce9-164">The integer is the **exit code** for your application.</span></span>

[!code-csharp[csProgGuideMain#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#13)]

- <span data-ttu-id="90ce9-165">Dönüş türlerinden biri ile bağımsız değişken alabilir.</span><span class="sxs-lookup"><span data-stu-id="90ce9-165">With either of the return types, it can take arguments.</span></span>

[!code-csharp[csProgGuideMain#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#19)]

<span data-ttu-id="90ce9-166">veya</span><span class="sxs-lookup"><span data-stu-id="90ce9-166">-or-</span></span>

[!code-csharp[csProgGuideMain#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#18)]

<span data-ttu-id="90ce9-167">`Main` yönteminin parametresi, `args`, programı çağırmak için kullanılan komut satırı bağımsız değişkenlerini içeren bir `string` dizidir.</span><span class="sxs-lookup"><span data-stu-id="90ce9-167">The parameter of the `Main` method, `args`, is a `string` array that contains the command-line arguments used to invoke the program.</span></span>

<span data-ttu-id="90ce9-168">Komut satırı bağımsız değişkenlerinin nasıl kullanılacağı hakkında daha fazla bilgi için, [ana () ve komut satırı bağımsız değişkenlerinde](../main-and-command-args/index.md)örneklere bakın.</span><span class="sxs-lookup"><span data-stu-id="90ce9-168">For more information about how to use command-line arguments, see the examples in [Main() and Command-Line Arguments](../main-and-command-args/index.md).</span></span>

## <a name="input-and-output"></a><span data-ttu-id="90ce9-169">Girdi ve çıktı</span><span class="sxs-lookup"><span data-stu-id="90ce9-169">Input and output</span></span>

<span data-ttu-id="90ce9-170">C#programlar genellikle .NET Framework çalışma zamanı kitaplığı tarafından sunulan giriş/çıkış hizmetlerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="90ce9-170">C# programs generally use the input/output services provided by the run-time library of the .NET Framework.</span></span> <span data-ttu-id="90ce9-171">Deyimin `System.Console.WriteLine("Hello World!");` <xref:System.Console.WriteLine%2A> yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="90ce9-171">The statement `System.Console.WriteLine("Hello World!");` uses the <xref:System.Console.WriteLine%2A> method.</span></span> <span data-ttu-id="90ce9-172">Bu, çalışma zamanı kitaplığındaki <xref:System.Console> sınıfının çıkış yöntemlerinden biridir.</span><span class="sxs-lookup"><span data-stu-id="90ce9-172">This is one of the output methods of the <xref:System.Console> class in the run-time library.</span></span> <span data-ttu-id="90ce9-173">Dize parametresini standart çıkış akışında ve ardından yeni bir satırla görüntüler.</span><span class="sxs-lookup"><span data-stu-id="90ce9-173">It displays its string parameter on the standard output stream followed by a new line.</span></span> <span data-ttu-id="90ce9-174">Diğer <xref:System.Console> Yöntemler farklı giriş ve çıkış işlemleri için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="90ce9-174">Other <xref:System.Console> methods are available for different input and output operations.</span></span> <span data-ttu-id="90ce9-175">`using System;` yönergesini programın başına eklerseniz, <xref:System> sınıfları ve yöntemleri tamamen nitelemeden doğrudan kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="90ce9-175">If you include the `using System;` directive at the beginning of the program, you can directly use the <xref:System> classes and methods without fully qualifying them.</span></span> <span data-ttu-id="90ce9-176">Örneğin, `System.Console.WriteLine`yerine `Console.WriteLine` çağırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="90ce9-176">For example, you can call `Console.WriteLine` instead of `System.Console.WriteLine`:</span></span>

[!code-csharp[csProgGuide#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/using.cs#1)]

[!code-csharp[csProgGuide#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#23)]

<span data-ttu-id="90ce9-177">Giriş/çıkış yöntemleri hakkında daha fazla bilgi için bkz. <xref:System.IO>.</span><span class="sxs-lookup"><span data-stu-id="90ce9-177">For more information about input/output methods, see <xref:System.IO>.</span></span>

## <a name="see-also"></a><span data-ttu-id="90ce9-178">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="90ce9-178">See also</span></span>

- [<span data-ttu-id="90ce9-179">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="90ce9-179">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="90ce9-180">Örnekler ve öğreticiler</span><span class="sxs-lookup"><span data-stu-id="90ce9-180">Samples and tutorials</span></span>](../../../samples-and-tutorials/index.md)
- [<span data-ttu-id="90ce9-181">Ana() ve Komut Satırı Bağımsız Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="90ce9-181">Main() and Command-Line Arguments</span></span>](../main-and-command-args/index.md)
- [<span data-ttu-id="90ce9-182">Görsele BaşlarkenC#</span><span class="sxs-lookup"><span data-stu-id="90ce9-182">Getting Started with Visual C#</span></span>](/visualstudio/ide/quickstart-csharp-console)
