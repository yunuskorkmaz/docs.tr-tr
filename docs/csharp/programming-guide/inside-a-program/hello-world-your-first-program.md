---
title: Hello World -- Windows veya Mac'te Visual Studio'yu kullanan ilk programınız - C# Programlama Kılavuzu
ms.date: 09/12/2019
f1_keywords:
- cs.program
- vs.csharp.startpage.firstapplication
helpviewer_keywords:
- examples [C#], Hello World
- Hello World example [C#]
ms.assetid: 6493182a-b0b6-4539-a719-518a168cb730
ms.openlocfilehash: 910fa4af1b4e45ce627b589a06910dc168490047
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712149"
---
# <a name="hello-world----your-first-program"></a><span data-ttu-id="68734-102">Hello World -- İlk programınız</span><span class="sxs-lookup"><span data-stu-id="68734-102">Hello World -- Your first program</span></span>

<span data-ttu-id="68734-103">Bu makalede, geleneksel "Hello World!" oluşturmak için Visual Studio'yu kullanacaksınız.</span><span class="sxs-lookup"><span data-stu-id="68734-103">In this article, you'll use Visual Studio to create the traditional "Hello World!"</span></span> <span data-ttu-id="68734-104">Program.</span><span class="sxs-lookup"><span data-stu-id="68734-104">program.</span></span> <span data-ttu-id="68734-105">Visual Studio, .NET geliştirme için tasarlanmış birçok özelliğe sahip profesyonel bir Entegre Geliştirme Ortamıdır (IDE).</span><span class="sxs-lookup"><span data-stu-id="68734-105">Visual Studio is a professional Integrated Development Environment (IDE) with many features designed for .NET development.</span></span> <span data-ttu-id="68734-106">Bu programı oluşturmak için Visual Studio'daki özelliklerden yalnızca birkaçını kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="68734-106">You'll use only a few of the features in Visual Studio to create this program.</span></span> <span data-ttu-id="68734-107">Visual Studio hakkında daha fazla bilgi edinmek için Visual [C# ile Başlarken'e](/visualstudio/ide/quickstart-csharp-console)bakın.</span><span class="sxs-lookup"><span data-stu-id="68734-107">To learn more about Visual Studio, see [Getting Started with Visual C#](/visualstudio/ide/quickstart-csharp-console).</span></span>

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="create-a-new-application"></a><span data-ttu-id="68734-108">Yeni uygulama oluşturma</span><span class="sxs-lookup"><span data-stu-id="68734-108">Create a new application</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="windows"></a>[<span data-ttu-id="68734-109">Windows</span><span class="sxs-lookup"><span data-stu-id="68734-109">Windows</span></span>](#tab/windows)

<span data-ttu-id="68734-110">Visual Studio’yu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="68734-110">Start Visual Studio.</span></span> <span data-ttu-id="68734-111">Windows'da aşağıdaki resmi görürsünüz:</span><span class="sxs-lookup"><span data-stu-id="68734-111">You'll see the following image on Windows:</span></span>

![Windows'da Visual Studio karşılama ekranı](./media/hello-world-your-first-program/visual-studio-windows-start-screen.png)

<span data-ttu-id="68734-113">Görüntünün sağ alt köşesinde **yeni bir proje oluştur'u** seçin.</span><span class="sxs-lookup"><span data-stu-id="68734-113">Select **Create a new project** in the lower right corner of the image.</span></span> <span data-ttu-id="68734-114">Visual Studio **Yeni Proje** iletişim kutusunu görüntüler:</span><span class="sxs-lookup"><span data-stu-id="68734-114">Visual Studio displays the **New Project** dialog:</span></span>

![Windows'da Visual Studio yeni proje ekranı](./media/hello-world-your-first-program/visual-studio-windows-new-project.png)

> [!NOTE]
> <span data-ttu-id="68734-116">Visual Studio'yu ilk kez başlattıysanız, **Son proje şablonları** listesi boştur.</span><span class="sxs-lookup"><span data-stu-id="68734-116">If this is the first time you've started Visual Studio, the **Recent project templates** list is empty.</span></span>

<span data-ttu-id="68734-117">Yeni proje iletişim kutusunda "Console App (.NET Core)" seçeneğini belirleyin ve **ardından İleri**tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="68734-117">On the new project dialog, choose "Console App (.NET Core)" and then press **Next**.</span></span> <span data-ttu-id="68734-118">Projenize "HelloWorld" gibi bir ad verin ve **Oluştur'a**basın.</span><span class="sxs-lookup"><span data-stu-id="68734-118">Give your project a name, such as "HelloWorld", then press **Create**.</span></span>

<span data-ttu-id="68734-119">Visual Studio projenizi açar.</span><span class="sxs-lookup"><span data-stu-id="68734-119">Visual Studio opens your project.</span></span> <span data-ttu-id="68734-120">Zaten temel bir "Merhaba Dünya!"</span><span class="sxs-lookup"><span data-stu-id="68734-120">It's already a basic "Hello World!"</span></span> <span data-ttu-id="68734-121">Örnek.</span><span class="sxs-lookup"><span data-stu-id="68734-121">example.</span></span> <span data-ttu-id="68734-122">Projenizi çalıştırmak için basın. `Ctrl`  +  `F5`</span><span class="sxs-lookup"><span data-stu-id="68734-122">Press `Ctrl` + `F5` to run your project.</span></span> <span data-ttu-id="68734-123">Visual Studio, kaynak kodu çalıştırılabilir e dönüştürerek projenizi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="68734-123">Visual Studio builds your project, converting the source code into an executable.</span></span> <span data-ttu-id="68734-124">Daha sonra, yeni uygulamanızı çalıştıran bir komut penceresi başlatıyor.</span><span class="sxs-lookup"><span data-stu-id="68734-124">Then, it launches a command window that runs your new application.</span></span> <span data-ttu-id="68734-125">Pencerede aşağıdaki metni görmeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="68734-125">You should see the following text in the window:</span></span>

```console
Hello World!

C:\Program Files\dotnet\dotnet.exe (process 11964) exited with code 0.
Press any key to close this window . . .
```

<span data-ttu-id="68734-126">Pencereyi kapatmak için bir tuşa basın.</span><span class="sxs-lookup"><span data-stu-id="68734-126">Press a key to close the window.</span></span>

# <a name="macos"></a>[<span data-ttu-id="68734-127">Macos</span><span class="sxs-lookup"><span data-stu-id="68734-127">macOS</span></span>](#tab/macos)

<span data-ttu-id="68734-128">Mac için Visual Studio'u başlatın.</span><span class="sxs-lookup"><span data-stu-id="68734-128">Start Visual Studio for Mac.</span></span> <span data-ttu-id="68734-129">Mac'te aşağıdaki resmi görürsünüz:</span><span class="sxs-lookup"><span data-stu-id="68734-129">You'll see the following image on Mac:</span></span>

![Mac'te Visual Studio karşılama ekranı](./media/hello-world-your-first-program/visual-studio-mac-start-screen.png)

> [!NOTE]
> <span data-ttu-id="68734-131">Mac için Visual Studio'yu ilk kez başlattıysanız, **Son projeler** listesi boştur.</span><span class="sxs-lookup"><span data-stu-id="68734-131">If this is the first time you've started Visual Studio for Mac, the **Recent projects** list is empty.</span></span>

<span data-ttu-id="68734-132">Görüntünün sağ üst köşesinde **Yeni'yi** seçin.</span><span class="sxs-lookup"><span data-stu-id="68734-132">Select **New** in the upper right corner of the image.</span></span> <span data-ttu-id="68734-133">Mac için Visual **Studio, Yeni Proje** iletişim kutusunu görüntüler:</span><span class="sxs-lookup"><span data-stu-id="68734-133">Visual Studio for Mac displays the **New Project** dialog:</span></span>

![Mac Visual Studio yeni proje ekranı](./media/hello-world-your-first-program/visual-studio-mac-new-project.png)

<span data-ttu-id="68734-135">Yeni proje iletişim kutusunda ".NET Core" ve "Console App" seçeneğini belirleyin ve **Ardından İleri**tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="68734-135">On the new project dialog, choose ".NET Core", and "Console App" and then press **Next**.</span></span> <span data-ttu-id="68734-136">Hedef çerçeveyi seçmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="68734-136">You'll need to select the target framework.</span></span> <span data-ttu-id="68734-137">Varsayılan değer gayet iyi, bu yüzden bir sonrakine basın.</span><span class="sxs-lookup"><span data-stu-id="68734-137">The default is fine, so press next.</span></span> <span data-ttu-id="68734-138">Projenize "HelloWorld" gibi bir ad verin ve **Oluştur'a**basın.</span><span class="sxs-lookup"><span data-stu-id="68734-138">Give your project a name, such as "HelloWorld", then press **Create**.</span></span> <span data-ttu-id="68734-139">Varsayılan proje konumunu kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="68734-139">You can use the default project location.</span></span> <span data-ttu-id="68734-140">Bu projeyi kaynak denetimine eklemeyin.</span><span class="sxs-lookup"><span data-stu-id="68734-140">Don't add this project to source control.</span></span>

<span data-ttu-id="68734-141">Mac için Visual Studio projenizi açar.</span><span class="sxs-lookup"><span data-stu-id="68734-141">Visual Studio for Mac opens your project.</span></span> <span data-ttu-id="68734-142">Zaten temel bir "Merhaba Dünya!"</span><span class="sxs-lookup"><span data-stu-id="68734-142">It's already a basic "Hello World!"</span></span> <span data-ttu-id="68734-143">Örnek.</span><span class="sxs-lookup"><span data-stu-id="68734-143">example.</span></span> <span data-ttu-id="68734-144">Projenizi çalıştırmak için basın. `Ctrl`  +  `Fn`  +  `F5`</span><span class="sxs-lookup"><span data-stu-id="68734-144">Press `Ctrl` + `Fn` + `F5` to run your project.</span></span> <span data-ttu-id="68734-145">Mac için Visual Studio, kaynak kodu çalıştırılabilire dönüştürerek projenizi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="68734-145">Visual Studio for Mac builds your project, converting the source code into an executable.</span></span> <span data-ttu-id="68734-146">Daha sonra, yeni uygulamanızı çalıştıran bir komut penceresi başlatıyor.</span><span class="sxs-lookup"><span data-stu-id="68734-146">Then, it launches a command window that runs your new application.</span></span> <span data-ttu-id="68734-147">Pencerede aşağıdaki metni görmeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="68734-147">You should see the following text in the window:</span></span>

```console
Hello World!

Press any key to close this window . . .
```

<span data-ttu-id="68734-148">Oturumu sonlamak için bir tuşa basın.</span><span class="sxs-lookup"><span data-stu-id="68734-148">Press a key to end the session.</span></span>

---

## <a name="elements-of-a-c-program"></a><span data-ttu-id="68734-149">C# programının öğeleri</span><span class="sxs-lookup"><span data-stu-id="68734-149">Elements of a C# program</span></span>

<span data-ttu-id="68734-150">Bu programın önemli bölümlerini inceleyelim.</span><span class="sxs-lookup"><span data-stu-id="68734-150">Let's examine the important parts of this program.</span></span> <span data-ttu-id="68734-151">İlk satır bir yorum içerir.</span><span class="sxs-lookup"><span data-stu-id="68734-151">The first line contains a comment.</span></span> <span data-ttu-id="68734-152">Karakterler satırın geri kalanını yoruma `//` dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="68734-152">The characters `//` convert the rest of the line to a comment.</span></span>

[!code-csharp[csProgGuide#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#32)]

<span data-ttu-id="68734-153">Ayrıca, bir metin bloğunu `/*` karakterlerle `*/` karakterler arasına ekleyerek yorum yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="68734-153">You can also comment out a block of text by enclosing it between the `/*` and `*/` characters.</span></span> <span data-ttu-id="68734-154">Bu, aşağıdaki örnekte gösterilir.</span><span class="sxs-lookup"><span data-stu-id="68734-154">This is shown in the following example.</span></span>

[!code-csharp[csProgGuide#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#33)]

<span data-ttu-id="68734-155">C# konsol uygulaması, `Main` denetimin başlayıp sona erdiği bir yöntem içermelidir.</span><span class="sxs-lookup"><span data-stu-id="68734-155">A C# console application must contain a `Main` method, in which control starts and ends.</span></span> <span data-ttu-id="68734-156">Yöntem, `Main` nesneleri oluşturduğunuz ve diğer yöntemleri yürüttüğüğün yerdir.</span><span class="sxs-lookup"><span data-stu-id="68734-156">The `Main` method is where you create objects and execute other methods.</span></span>

<span data-ttu-id="68734-157">Yöntem, `Main` bir sınıf veya bir yapı içinde bulunan [statik](../../language-reference/keywords/static.md) bir yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="68734-157">The `Main` method is a [static](../../language-reference/keywords/static.md) method that resides inside a class or a struct.</span></span> <span data-ttu-id="68734-158">Önceki "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="68734-158">In the previous "Hello World!"</span></span> <span data-ttu-id="68734-159">örneğin, adlı `Hello`bir sınıfta bulunur.</span><span class="sxs-lookup"><span data-stu-id="68734-159">example, it resides in a class named `Hello`.</span></span> <span data-ttu-id="68734-160">`Main` Yöntemi aşağıdaki yollardan biriyle bildirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="68734-160">You can declare the `Main` method in one of the following ways:</span></span>

- <span data-ttu-id="68734-161">Geri dönebilir. `void`</span><span class="sxs-lookup"><span data-stu-id="68734-161">It can return `void`.</span></span> <span data-ttu-id="68734-162">Bu, programınızın bir değer döndürmediği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="68734-162">That means your program doesn't return a value.</span></span>

[!code-csharp[csProgGuideMain#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#12)]

- <span data-ttu-id="68734-163">Ayrıca bir sonda döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="68734-163">It can also return an integer.</span></span> <span data-ttu-id="68734-164">Sonda, uygulamanızın **çıkış kodudur.**</span><span class="sxs-lookup"><span data-stu-id="68734-164">The integer is the **exit code** for your application.</span></span>

[!code-csharp[csProgGuideMain#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#13)]

- <span data-ttu-id="68734-165">İade türlerinden herhangi biriyle, bağımsız değişkenler alabilir.</span><span class="sxs-lookup"><span data-stu-id="68734-165">With either of the return types, it can take arguments.</span></span>

[!code-csharp[csProgGuideMain#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#19)]

<span data-ttu-id="68734-166">-veya-</span><span class="sxs-lookup"><span data-stu-id="68734-166">-or-</span></span>

[!code-csharp[csProgGuideMain#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#18)]

<span data-ttu-id="68734-167">`Main` Yöntemin parametresi, `args`programı `string` çağırmak için kullanılan komut satırı bağımsız değişkenlerini içeren bir dizidir.</span><span class="sxs-lookup"><span data-stu-id="68734-167">The parameter of the `Main` method, `args`, is a `string` array that contains the command-line arguments used to invoke the program.</span></span>

<span data-ttu-id="68734-168">Komut satırı bağımsız değişkenleri nasıl kullanılacağı hakkında daha fazla bilgi için [Main() ve Command-Line Bağımsız](../main-and-command-args/index.md)Değişkenleri'ndeki örneklere bakın.</span><span class="sxs-lookup"><span data-stu-id="68734-168">For more information about how to use command-line arguments, see the examples in [Main() and Command-Line Arguments](../main-and-command-args/index.md).</span></span>

## <a name="input-and-output"></a><span data-ttu-id="68734-169">Girdi ve çıktı</span><span class="sxs-lookup"><span data-stu-id="68734-169">Input and output</span></span>

<span data-ttu-id="68734-170">C# programları genellikle .NET Framework'ün çalışma zamanı kitaplığı tarafından sağlanan giriş/çıktı hizmetlerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="68734-170">C# programs generally use the input/output services provided by the run-time library of the .NET Framework.</span></span> <span data-ttu-id="68734-171">İfade `System.Console.WriteLine("Hello World!");` yöntemini <xref:System.Console.WriteLine%2A> kullanır.</span><span class="sxs-lookup"><span data-stu-id="68734-171">The statement `System.Console.WriteLine("Hello World!");` uses the <xref:System.Console.WriteLine%2A> method.</span></span> <span data-ttu-id="68734-172">Bu, çalışma zamanı kitaplığında <xref:System.Console> sınıfın çıktı yöntemlerinden biridir.</span><span class="sxs-lookup"><span data-stu-id="68734-172">This is one of the output methods of the <xref:System.Console> class in the run-time library.</span></span> <span data-ttu-id="68734-173">Dize parametresini standart çıktı akışında yeni bir çizgi yle görüntüler.</span><span class="sxs-lookup"><span data-stu-id="68734-173">It displays its string parameter on the standard output stream followed by a new line.</span></span> <span data-ttu-id="68734-174">Farklı <xref:System.Console> giriş ve çıkış işlemleri için başka yöntemler de mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="68734-174">Other <xref:System.Console> methods are available for different input and output operations.</span></span> <span data-ttu-id="68734-175">Yönergeyi `using System;` programın başına eklerseniz, <xref:System> sınıfları ve yöntemleri tam olarak nitelemeden doğrudan kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="68734-175">If you include the `using System;` directive at the beginning of the program, you can directly use the <xref:System> classes and methods without fully qualifying them.</span></span> <span data-ttu-id="68734-176">Örneğin, bunun yerine `Console.WriteLine` `System.Console.WriteLine`arayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="68734-176">For example, you can call `Console.WriteLine` instead of `System.Console.WriteLine`:</span></span>

[!code-csharp[csProgGuide#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/using.cs#1)]

[!code-csharp[csProgGuide#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#23)]

<span data-ttu-id="68734-177">Giriş/çıkış yöntemleri hakkında daha fazla <xref:System.IO>bilgi için bkz.</span><span class="sxs-lookup"><span data-stu-id="68734-177">For more information about input/output methods, see <xref:System.IO>.</span></span>

## <a name="see-also"></a><span data-ttu-id="68734-178">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="68734-178">See also</span></span>

- [<span data-ttu-id="68734-179">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="68734-179">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="68734-180">Örnekler ve öğreticiler</span><span class="sxs-lookup"><span data-stu-id="68734-180">Samples and tutorials</span></span>](../../../samples-and-tutorials/index.md)
- [<span data-ttu-id="68734-181">Ana() ve Komut Satırı Bağımsız Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="68734-181">Main() and Command-Line Arguments</span></span>](../main-and-command-args/index.md)
- [<span data-ttu-id="68734-182">Görsel C ile Başlarken #</span><span class="sxs-lookup"><span data-stu-id="68734-182">Getting Started with Visual C#</span></span>](/visualstudio/ide/quickstart-csharp-console)
