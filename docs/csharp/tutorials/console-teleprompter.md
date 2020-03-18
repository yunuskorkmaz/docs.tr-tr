---
title: Konsol Uygulaması
description: Bu öğretici size .NET Core ve C# dillerinde bir dizi özellik öğretir.
ms.date: 03/06/2017
ms.technology: csharp-fundamentals
ms.assetid: 883cd93d-50ce-4144-b7c9-2df28d9c11a0
ms.openlocfilehash: 09ce36e7a61f576dc4449976ce676701dc57c9cd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76921130"
---
# <a name="console-app"></a><span data-ttu-id="947a4-103">Konsol uygulaması</span><span class="sxs-lookup"><span data-stu-id="947a4-103">Console app</span></span>

<span data-ttu-id="947a4-104">Bu öğretici size .NET Core ve C# dillerinde bir dizi özellik öğretir.</span><span class="sxs-lookup"><span data-stu-id="947a4-104">This tutorial teaches you a number of features in .NET Core and the C# language.</span></span> <span data-ttu-id="947a4-105">Şunları öğreneceksiniz:</span><span class="sxs-lookup"><span data-stu-id="947a4-105">You'll learn:</span></span>

- <span data-ttu-id="947a4-106">.NET Çekirdek CLI'nin temelleri</span><span class="sxs-lookup"><span data-stu-id="947a4-106">The basics of the .NET Core CLI</span></span>
- <span data-ttu-id="947a4-107">C# Console Uygulamasının yapısı</span><span class="sxs-lookup"><span data-stu-id="947a4-107">The structure of a C# Console Application</span></span>
- <span data-ttu-id="947a4-108">Konsol I/O</span><span class="sxs-lookup"><span data-stu-id="947a4-108">Console I/O</span></span>
- <span data-ttu-id="947a4-109">.NET'teki Dosya G/Ç API'lerinin temelleri</span><span class="sxs-lookup"><span data-stu-id="947a4-109">The basics of File I/O APIs in .NET</span></span>
- <span data-ttu-id="947a4-110">.NET'te Görev Tabanlı Eşzamanlı Programlamanın temelleri</span><span class="sxs-lookup"><span data-stu-id="947a4-110">The basics of the Task-based Asynchronous Programming in .NET</span></span>

<span data-ttu-id="947a4-111">Metin dosyasını okuyan ve bu metin dosyasının içeriğini konsola yansıtan bir uygulama oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="947a4-111">You'll build an application that reads a text file, and echoes the contents of that text file to the console.</span></span> <span data-ttu-id="947a4-112">Konsola çıkış yüksek sesle okuma maç için tempolu.</span><span class="sxs-lookup"><span data-stu-id="947a4-112">The output to the console is paced to match reading it aloud.</span></span> <span data-ttu-id="947a4-113">'<' (daha az) veya '>' (büyük) tuşlarına basarak hızı hızlandırabilir veya yavaşlatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="947a4-113">You can speed up or slow down the pace by pressing the '<' (less than) or '>' (greater than) keys.</span></span>

<span data-ttu-id="947a4-114">Bu öğretici özellikleri bir yeri vardır.</span><span class="sxs-lookup"><span data-stu-id="947a4-114">There are a lot of features in this tutorial.</span></span> <span data-ttu-id="947a4-115">Onları teker teker inşa edelim.</span><span class="sxs-lookup"><span data-stu-id="947a4-115">Let's build them one by one.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="947a4-116">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="947a4-116">Prerequisites</span></span>

- <span data-ttu-id="947a4-117">Makinenizi .NET Core'u çalıştıracak şekilde ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="947a4-117">Set up your machine to run .NET Core.</span></span> <span data-ttu-id="947a4-118">Yükleme yönergelerini [.NET Core indirme sayfasında](https://dotnet.microsoft.com/download) bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="947a4-118">You can find the installation instructions on the [.NET Core downloads](https://dotnet.microsoft.com/download) page.</span></span> <span data-ttu-id="947a4-119">Bu uygulamayı Windows, Linux, macOS veya Docker kapsayıcısında çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="947a4-119">You can run this application on Windows, Linux, macOS, or in a Docker container.</span></span>

- <span data-ttu-id="947a4-120">En sevdiğiniz kod düzenleyicisini yükleyin.</span><span class="sxs-lookup"><span data-stu-id="947a4-120">Install your favorite code editor.</span></span>

## <a name="create-the-app"></a><span data-ttu-id="947a4-121">Uygulama oluşturma</span><span class="sxs-lookup"><span data-stu-id="947a4-121">Create the app</span></span>

<span data-ttu-id="947a4-122">İlk adım yeni bir uygulama oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="947a4-122">The first step is to create a new application.</span></span> <span data-ttu-id="947a4-123">Bir komut istemi açın ve uygulamanız için yeni bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="947a4-123">Open a command prompt and create a new directory for your application.</span></span> <span data-ttu-id="947a4-124">Bunu geçerli dizini yapın.</span><span class="sxs-lookup"><span data-stu-id="947a4-124">Make that the current directory.</span></span> <span data-ttu-id="947a4-125">Komut istemine komut `dotnet new console` yazın.</span><span class="sxs-lookup"><span data-stu-id="947a4-125">Type the command `dotnet new console` at the command prompt.</span></span> <span data-ttu-id="947a4-126">Bu, temel bir "Hello World" uygulaması için başlangıç dosyalarını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="947a4-126">This creates the starter files for a basic "Hello World" application.</span></span>

<span data-ttu-id="947a4-127">Değişiklikler yapmaya başlamadan önce, basit Hello World uygulamasını çalıştırmak için gereken adımları gözden geçirelim.</span><span class="sxs-lookup"><span data-stu-id="947a4-127">Before you start making modifications, let's go through the steps to run the simple Hello World application.</span></span> <span data-ttu-id="947a4-128">Uygulamayı oluşturduktan sonra `dotnet restore` komut istemine yazın.</span><span class="sxs-lookup"><span data-stu-id="947a4-128">After creating the application, type `dotnet restore` at the command prompt.</span></span> <span data-ttu-id="947a4-129">Bu komut NuGet paket geri yükleme işlemini çalıştırAr.</span><span class="sxs-lookup"><span data-stu-id="947a4-129">This command runs the NuGet package restore process.</span></span> <span data-ttu-id="947a4-130">NuGet bir .NET paket yöneticisidir.</span><span class="sxs-lookup"><span data-stu-id="947a4-130">NuGet is a .NET package manager.</span></span> <span data-ttu-id="947a4-131">Bu komut, projeniz için eksik bağımlılıklardan herhangi birini karşıdan yükler.</span><span class="sxs-lookup"><span data-stu-id="947a4-131">This command downloads any of the missing dependencies for your project.</span></span> <span data-ttu-id="947a4-132">Bu yeni bir proje olduğundan, bağımlılıkların hiçbiri yerinde değildir, bu nedenle ilk çalıştırma .NET Core çerçevesini karşıdan yüklez.</span><span class="sxs-lookup"><span data-stu-id="947a4-132">As this is a new project, none of the dependencies are in place, so the first run will download the .NET Core framework.</span></span> <span data-ttu-id="947a4-133">Bu ilk adımdan sonra, yalnızca `dotnet restore` yeni bağımlı paketler eklediğinizde veya bağımlılıklarınızın sürümlerini güncelleştirdiğinizde çalışmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="947a4-133">After this initial step, you will only need to run `dotnet restore` when you add new dependent packages, or update the versions of any of your dependencies.</span></span>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="947a4-134">Paketleri geri aldıktan sonra, `dotnet build`çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="947a4-134">After restoring packages, you run `dotnet build`.</span></span> <span data-ttu-id="947a4-135">Bu, yapı altyapısını yürütür ve uygulamanızın çalıştırılabilir hale getirmesini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="947a4-135">This executes the build engine and creates your application executable.</span></span> <span data-ttu-id="947a4-136">Son olarak, `dotnet run` uygulamanızı çalıştırmak için çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="947a4-136">Finally, you execute `dotnet run` to run your application.</span></span>

<span data-ttu-id="947a4-137">Basit Hello World uygulama kodu tüm Program.cs.</span><span class="sxs-lookup"><span data-stu-id="947a4-137">The simple Hello World application code is all in Program.cs.</span></span> <span data-ttu-id="947a4-138">Bu dosyayı en sevdiğiniz metin düzenleyicisiyle açın.</span><span class="sxs-lookup"><span data-stu-id="947a4-138">Open that file with your favorite text editor.</span></span> <span data-ttu-id="947a4-139">İlk değişikliklerimizi yapmak üzereyiz.</span><span class="sxs-lookup"><span data-stu-id="947a4-139">We're about to make our first changes.</span></span> <span data-ttu-id="947a4-140">Dosyanın üst kısmında, aşağıdakileri kullanarak bir ifadeye bakın:</span><span class="sxs-lookup"><span data-stu-id="947a4-140">At the top of the file, see a using statement:</span></span>

```csharp
using System;
```

<span data-ttu-id="947a4-141">Bu deyim derleyiciye `System` ad alanından herhangi bir türün kapsam içinde olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="947a4-141">This statement tells the compiler that any types from the `System` namespace are in scope.</span></span> <span data-ttu-id="947a4-142">Kullanmış olabileceğiniz diğer Nesne Yönelimli diller gibi, C# türleri düzenlemek için ad alanlarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="947a4-142">Like other Object Oriented languages you may have used, C# uses namespaces to organize types.</span></span> <span data-ttu-id="947a4-143">Bu Hello World programı da farklı değil.</span><span class="sxs-lookup"><span data-stu-id="947a4-143">This Hello World program is no different.</span></span> <span data-ttu-id="947a4-144">Programın ad alanına, geçerli dizinin adını temel alan bir şekilde ekte olduğunu görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="947a4-144">You can see that the program is enclosed in the namespace with the name based on the name of the current directory.</span></span> <span data-ttu-id="947a4-145">Bu öğretici için, ad alanının adını şu `TeleprompterConsole`şekilde değiştirelim:</span><span class="sxs-lookup"><span data-stu-id="947a4-145">For this tutorial, let's change the name of the namespace to `TeleprompterConsole`:</span></span>

```csharp
namespace TeleprompterConsole
```

## <a name="reading-and-echoing-the-file"></a><span data-ttu-id="947a4-146">Dosyayı Okuma ve Yankılama</span><span class="sxs-lookup"><span data-stu-id="947a4-146">Reading and Echoing the File</span></span>

<span data-ttu-id="947a4-147">Eklemek için ilk özellik bir metin dosyası okumak ve konsola tüm bu metni görüntülemek için yeteneğidir.</span><span class="sxs-lookup"><span data-stu-id="947a4-147">The first feature to add is the ability to read a text file and display all that text to the console.</span></span> <span data-ttu-id="947a4-148">Önce bir metin dosyası ekleyelim.</span><span class="sxs-lookup"><span data-stu-id="947a4-148">First, let's add a text file.</span></span> <span data-ttu-id="947a4-149">Bu [örnek](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-teleprompter) için github deposundan [örnekQuotes.txt](https://github.com/dotnet/samples/raw/master/csharp/getting-started/console-teleprompter/sampleQuotes.txt) dosyasını proje dizininize kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="947a4-149">Copy the [sampleQuotes.txt](https://github.com/dotnet/samples/raw/master/csharp/getting-started/console-teleprompter/sampleQuotes.txt) file from the GitHub repository for this [sample](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-teleprompter) into your project directory.</span></span> <span data-ttu-id="947a4-150">Bu, uygulamanız için komut dosyası görevi göreceksiniz.</span><span class="sxs-lookup"><span data-stu-id="947a4-150">This will serve as the script for your application.</span></span> <span data-ttu-id="947a4-151">Bu konu yla ilgili örnek uygulamayı nasıl indireceğiniz hakkında bilgi almak istiyorsanız, [Örnekler ve Öğreticiler](../../samples-and-tutorials/index.md#viewing-and-downloading-samples) konusundaki talimatlara bakın.</span><span class="sxs-lookup"><span data-stu-id="947a4-151">If you would like information on how to download the sample app for this topic, see the instructions in the [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples) topic.</span></span>

<span data-ttu-id="947a4-152">Ardından, sınıfınızda `Program` aşağıdaki yöntemi ekleyin (yöntemin `Main` hemen altında):</span><span class="sxs-lookup"><span data-stu-id="947a4-152">Next, add the following method in your `Program` class (right below the `Main` method):</span></span>

```csharp
static IEnumerable<string> ReadFrom(string file)
{
    string line;
    using (var reader = File.OpenText(file))
    {
        while ((line = reader.ReadLine()) != null)
        {
            yield return line;
        }
    }
}
```

<span data-ttu-id="947a4-153">Bu yöntem, iki yeni ad alanı nın türlerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="947a4-153">This method uses types from two new namespaces.</span></span> <span data-ttu-id="947a4-154">Bunun derlemesi için dosyanın üst bölümüne aşağıdaki iki satırı eklemeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="947a4-154">For this to compile you'll need to add the following two lines to the top of the file:</span></span>

```csharp
using System.Collections.Generic;
using System.IO;
```

<span data-ttu-id="947a4-155">Arabirim <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Collections.Generic> ad alanında tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="947a4-155">The <xref:System.Collections.Generic.IEnumerable%601> interface is defined in the <xref:System.Collections.Generic> namespace.</span></span> <span data-ttu-id="947a4-156">Sınıf <xref:System.IO.File> <xref:System.IO> ad alanında tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="947a4-156">The <xref:System.IO.File> class is defined in the <xref:System.IO> namespace.</span></span>

<span data-ttu-id="947a4-157">Bu yöntem, *Bir Iterator yöntemi*olarak adlandırılan C# yönteminin özel bir türüdür.</span><span class="sxs-lookup"><span data-stu-id="947a4-157">This method is a special type of C# method called an *Iterator method*.</span></span> <span data-ttu-id="947a4-158">Enumerator yöntemleri tembel olarak değerlendirilen dizileri döndürer.</span><span class="sxs-lookup"><span data-stu-id="947a4-158">Enumerator methods return sequences that are evaluated lazily.</span></span> <span data-ttu-id="947a4-159">Bu, dizideki her öğenin, sırayı tüketen kod tarafından istendiği gibi oluşturulduğu anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="947a4-159">That means each item in the sequence is generated as it is requested by the code consuming the sequence.</span></span> <span data-ttu-id="947a4-160">Sayısallaştırıcı yöntemler, bir veya daha fazla [`yield return`](../language-reference/keywords/yield.md) ifade içeren yöntemlerdir.</span><span class="sxs-lookup"><span data-stu-id="947a4-160">Enumerator methods are methods that contain one or more [`yield return`](../language-reference/keywords/yield.md) statements.</span></span> <span data-ttu-id="947a4-161">`ReadFrom` Yöntem tarafından döndürülen nesne, dizideki her öğeyi oluşturmak için kodu içerir.</span><span class="sxs-lookup"><span data-stu-id="947a4-161">The object returned by the `ReadFrom` method contains the code to generate each item in the sequence.</span></span> <span data-ttu-id="947a4-162">Bu örnekte, kaynak dosyadan sonraki metin satırını okuma ve bu dizeyi döndürme içerir.</span><span class="sxs-lookup"><span data-stu-id="947a4-162">In this example, that involves reading the next line of text from the source file, and returning that string.</span></span> <span data-ttu-id="947a4-163">Arama kodu diziden bir sonraki öğeyi her istediğinde, kod dosyadaki bir sonraki metin satırını okur ve döndürür.</span><span class="sxs-lookup"><span data-stu-id="947a4-163">Each time the calling code requests the next item from the sequence, the code reads the next line of text from the file and returns it.</span></span> <span data-ttu-id="947a4-164">Dosya tamamen okunduğunda, sıra başka öğe olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="947a4-164">When the file is completely read, the sequence indicates that there are no more items.</span></span>

<span data-ttu-id="947a4-165">Sizin için yeni olabilecek iki C# sözdizimi öğesi daha vardır.</span><span class="sxs-lookup"><span data-stu-id="947a4-165">There are two other C# syntax elements that may be new to you.</span></span> <span data-ttu-id="947a4-166">Bu [`using`](../language-reference/keywords/using-statement.md) yöntemdeki deyim, kaynak temizlemeyi yönetir.</span><span class="sxs-lookup"><span data-stu-id="947a4-166">The [`using`](../language-reference/keywords/using-statement.md) statement in this method manages resource cleanup.</span></span> <span data-ttu-id="947a4-167">`using` İfadede`reader`(, bu örnekte) başlan değişken <xref:System.IDisposable> arabirimi uygulamalıdır.</span><span class="sxs-lookup"><span data-stu-id="947a4-167">The variable that is initialized in the `using` statement (`reader`, in this example) must implement the <xref:System.IDisposable> interface.</span></span> <span data-ttu-id="947a4-168">Bu arabirim, `Dispose`kaynağın serbest bırakılması gerektiğinde çağrılması gereken tek bir yöntem tanımlar.</span><span class="sxs-lookup"><span data-stu-id="947a4-168">That interface defines a single method, `Dispose`, that should be called when the resource should be released.</span></span> <span data-ttu-id="947a4-169">Derleyici, yürütme deyiminin kapanış ayracına `using` ulaştığında bu çağrıyı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="947a4-169">The compiler generates that call when execution reaches the closing brace of the `using` statement.</span></span> <span data-ttu-id="947a4-170">Derleyici tarafından oluşturulan kod, kullanarak ifade tarafından tanımlanan bloktaki koddan bir özel durum atılsa bile kaynağın serbest bırakılmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="947a4-170">The compiler-generated code ensures that the resource is released even if an exception is thrown from the code in the block defined by the using statement.</span></span>

<span data-ttu-id="947a4-171">Değişken `reader` `var` anahtar kelime kullanılarak tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="947a4-171">The `reader` variable is defined using the `var` keyword.</span></span> <span data-ttu-id="947a4-172">[`var`](../language-reference/keywords/var.md)*örtülü olarak yazılan yerel değişkeni*tanımlar.</span><span class="sxs-lookup"><span data-stu-id="947a4-172">[`var`](../language-reference/keywords/var.md) defines an *implicitly typed local variable*.</span></span> <span data-ttu-id="947a4-173">Bu, değişkenin türü değişkene atanan nesnenin derleme zamanı türüne göre belirlenir anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="947a4-173">That means the type of the variable is determined by the compile-time type of the object assigned to the variable.</span></span> <span data-ttu-id="947a4-174">Burada, bir <xref:System.IO.StreamReader> nesne olan <xref:System.IO.File.OpenText(System.String)> yöntemin iade değeridir.</span><span class="sxs-lookup"><span data-stu-id="947a4-174">Here, that is the return value from the <xref:System.IO.File.OpenText(System.String)> method, which is a <xref:System.IO.StreamReader> object.</span></span>

<span data-ttu-id="947a4-175">Şimdi, `Main` yöntemde dosyayı okumak için kodu dolduralım:</span><span class="sxs-lookup"><span data-stu-id="947a4-175">Now, let's fill in the code to read the file in the `Main` method:</span></span>

```csharp
var lines = ReadFrom("sampleQuotes.txt");
foreach (var line in lines)
{
    Console.WriteLine(line);
}
```

<span data-ttu-id="947a4-176">Programı çalıştırın `dotnet run`(kullanarak) ve konsola yazdırılan her satırı görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="947a4-176">Run the program (using `dotnet run`) and you can see every line printed out to the console.</span></span>

## <a name="adding-delays-and-formatting-output"></a><span data-ttu-id="947a4-177">Gecikmeler ekleme ve çıktıyı biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="947a4-177">Adding Delays and Formatting output</span></span>

<span data-ttu-id="947a4-178">Sahip olduğunuz şey yüksek sesle okunamayacak kadar hızlı görüntüleniyor.</span><span class="sxs-lookup"><span data-stu-id="947a4-178">What you have is being displayed far too fast to read aloud.</span></span> <span data-ttu-id="947a4-179">Şimdi çıkışgecikmeler eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="947a4-179">Now you need to add the delays in the output.</span></span> <span data-ttu-id="947a4-180">Başladığınızda, eşzamanlı işleme sağlayan bazı çekirdek kodu oluşturuyor olacaksınız.</span><span class="sxs-lookup"><span data-stu-id="947a4-180">As you start, you'll be building some of the core code that enables asynchronous processing.</span></span> <span data-ttu-id="947a4-181">Ancak, bu ilk adımlar birkaç anti-desenler ilerler.</span><span class="sxs-lookup"><span data-stu-id="947a4-181">However, these first steps will follow a few anti-patterns.</span></span> <span data-ttu-id="947a4-182">Kodu eklerken anti-desenler yorumlarda işaret edilir ve kod sonraki adımlarda güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="947a4-182">The anti-patterns are pointed out in comments as you add the code, and the code will be updated in later steps.</span></span>

<span data-ttu-id="947a4-183">Bu bölümün iki adımı vardır.</span><span class="sxs-lookup"><span data-stu-id="947a4-183">There are two steps to this section.</span></span> <span data-ttu-id="947a4-184">İlk olarak, tüm satırlarıyerine tek sözcük döndürmek için yineleyici yöntemini güncelleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="947a4-184">First, you'll update the iterator method to return single words instead of entire lines.</span></span> <span data-ttu-id="947a4-185">Bu modifikasyonlarla yapıldı.</span><span class="sxs-lookup"><span data-stu-id="947a4-185">That's done with these modifications.</span></span> <span data-ttu-id="947a4-186">İfadeyi `yield return line;` aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="947a4-186">Replace the `yield return line;` statement with the following code:</span></span>

```csharp
var words = line.Split(' ');
foreach (var word in words)
{
    yield return word + " ";
}
yield return Environment.NewLine;
```

<span data-ttu-id="947a4-187">Ardından, dosyanın satırlarını nasıl tükettiğinizi değiştirmeniz ve her sözcüğü yazdıktan sonra gecikme eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="947a4-187">Next, you need to modify how you consume the lines of the file, and add a delay after writing each word.</span></span> <span data-ttu-id="947a4-188">Yöntemdeki `Console.WriteLine(line)` `Main` deyimi aşağıdaki blokla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="947a4-188">Replace the `Console.WriteLine(line)` statement in the `Main` method with the following block:</span></span>

```csharp
Console.Write(line);
if (!string.IsNullOrWhiteSpace(line))
{
    var pause = Task.Delay(200);
    // Synchronously waiting on a task is an
    // anti-pattern. This will get fixed in later
    // steps.
    pause.Wait();
}
```

<span data-ttu-id="947a4-189">Sınıf <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks> ad alanındaolduğundan, bu `using` ifadeyi dosyanın en üstüne eklemeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="947a4-189">The <xref:System.Threading.Tasks.Task> class is in the <xref:System.Threading.Tasks> namespace, so you need to add that `using` statement at the top of file:</span></span>

```csharp
using System.Threading.Tasks;
```

<span data-ttu-id="947a4-190">Örneği çalıştırın ve çıktıyı kontrol edin.</span><span class="sxs-lookup"><span data-stu-id="947a4-190">Run the sample, and check the output.</span></span> <span data-ttu-id="947a4-191">Şimdi, her bir kelime yazdırılır, ardından 200 ms gecikme.</span><span class="sxs-lookup"><span data-stu-id="947a4-191">Now, each single word is printed, followed by a 200 ms delay.</span></span> <span data-ttu-id="947a4-192">Ancak, kaynak metin dosyasında satır sonu olmayan 80'den fazla karaktere sahip birkaç satır olduğundan, görüntülenen çıktı bazı sorunları gösterir.</span><span class="sxs-lookup"><span data-stu-id="947a4-192">However, the displayed output shows some issues because the source text file has several lines that have more than 80 characters without a line break.</span></span> <span data-ttu-id="947a4-193">Kaydırma yaparken bunu okumak zor olabilir.</span><span class="sxs-lookup"><span data-stu-id="947a4-193">That can be hard to read while it's scrolling by.</span></span> <span data-ttu-id="947a4-194">Bunu düzeltmek kolay.</span><span class="sxs-lookup"><span data-stu-id="947a4-194">That's easy to fix.</span></span> <span data-ttu-id="947a4-195">Yalnızca her satırın uzunluğunu izleyecek ve satır uzunluğu belirli bir eşiğe ulaştığında yeni bir satır oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="947a4-195">You'll just keep track of the length of each line, and generate a new line whenever the line length reaches a certain threshold.</span></span> <span data-ttu-id="947a4-196">Satır uzunluğunu tutan `words` `ReadFrom` yöntemde beyanı sonra yerel bir değişken bildirin:</span><span class="sxs-lookup"><span data-stu-id="947a4-196">Declare a local variable after the declaration of `words` in the `ReadFrom` method that holds the line length:</span></span>

```csharp
var lineLength = 0;
```

<span data-ttu-id="947a4-197">Ardından, deyimden `yield return word + " ";` sonra (kapanış ayracından önce) aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="947a4-197">Then, add the following code after the `yield return word + " ";` statement (before the closing brace):</span></span>

```csharp
lineLength += word.Length + 1;
if (lineLength > 70)
{
    yield return Environment.NewLine;
    lineLength = 0;
}
```

<span data-ttu-id="947a4-198">Örneği çalıştırın ve önceden yapılandırılmış hızında yüksek sesle okuyabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="947a4-198">Run the sample, and you'll be able to read aloud at its pre-configured pace.</span></span>

## <a name="async-tasks"></a><span data-ttu-id="947a4-199">Async Görevleri</span><span class="sxs-lookup"><span data-stu-id="947a4-199">Async Tasks</span></span>

<span data-ttu-id="947a4-200">Bu son adımda, çıktıyı eşit bir şekilde bir göreve yazmak için kodu eklersiniz, aynı zamanda metin ekranını hızlandırmak veya yavaşlatmak veya metin görüntülemeyi tamamen durdurmak istiyorlarsa kullanıcıdan gelen girişi okumak için başka bir görev çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="947a4-200">In this final step, you'll add the code to write the output asynchronously in one task, while also running another task to read input from the user if they want to speed up or slow down the text display, or stop the text display altogether.</span></span> <span data-ttu-id="947a4-201">Bu birkaç adım vardır ve sonunda, ihtiyacınız olan tüm güncelleştirmeleri olacak.</span><span class="sxs-lookup"><span data-stu-id="947a4-201">This has a few steps in it and by the end, you'll have all the updates that you need.</span></span> <span data-ttu-id="947a4-202">İlk adım, dosyayı okumak ve <xref:System.Threading.Tasks.Task> görüntülemek için şimdiye kadar oluşturduğunuz kodu temsil eden eşzamanlı bir döndürme yöntemi oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="947a4-202">The first step is to create an asynchronous <xref:System.Threading.Tasks.Task> returning method that represents the code you've created so far to read and display the file.</span></span>

<span data-ttu-id="947a4-203">Bu yöntemi sınıfınıza `Program` ekleyin (yönteminizin `Main` gövdesinden alınır):</span><span class="sxs-lookup"><span data-stu-id="947a4-203">Add this method to your `Program` class (it's taken from the body of your `Main` method):</span></span>

```csharp
private static async Task ShowTeleprompter()
{
    var words = ReadFrom("sampleQuotes.txt");
    foreach (var word in words)
    {
        Console.Write(word);
        if (!string.IsNullOrWhiteSpace(word))
        {
            await Task.Delay(200);
        }
    }
}
```

<span data-ttu-id="947a4-204">İki değişiklik fark edeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="947a4-204">You'll notice two changes.</span></span> <span data-ttu-id="947a4-205">İlk olarak, yöntemin gövdesinde, <xref:System.Threading.Tasks.Task.Wait> eşzamanlı olarak bir görevin tamamlanmasını beklemek için `await` arama yapmak yerine, bu sürüm anahtar sözcüğü kullanır.</span><span class="sxs-lookup"><span data-stu-id="947a4-205">First, in the body of the method, instead of calling <xref:System.Threading.Tasks.Task.Wait> to synchronously wait for a task to finish, this version uses the `await` keyword.</span></span> <span data-ttu-id="947a4-206">Bunu yapmak için, yöntem imzasına `async` değiştirici eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="947a4-206">In order to do that, you need to add the `async` modifier to the method signature.</span></span> <span data-ttu-id="947a4-207">Bu yöntem `Task`bir .</span><span class="sxs-lookup"><span data-stu-id="947a4-207">This method returns a `Task`.</span></span> <span data-ttu-id="947a4-208">Bir `Task` nesneyi döndüren iade ifadeleri olmadığına dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="947a4-208">Notice that there are no return statements that return a `Task` object.</span></span> <span data-ttu-id="947a4-209">Bunun yerine, bu `Task` `await` nesne, işleci kullandığınızda derleyicinin oluşturduğu kod la oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="947a4-209">Instead, that `Task` object is created by code the compiler generates when you use the `await` operator.</span></span> <span data-ttu-id="947a4-210">Bu yöntemin bir `await`.</span><span class="sxs-lookup"><span data-stu-id="947a4-210">You can imagine that this method returns when it reaches an `await`.</span></span> <span data-ttu-id="947a4-211">Döndürülen `Task` çalışma tamamlanmadı gösterir.</span><span class="sxs-lookup"><span data-stu-id="947a4-211">The returned `Task` indicates that the work has not completed.</span></span> <span data-ttu-id="947a4-212">Beklenen görev tamamlandığında yöntem devam eder.</span><span class="sxs-lookup"><span data-stu-id="947a4-212">The method resumes when the awaited task completes.</span></span> <span data-ttu-id="947a4-213">Tamamlanmak üzere yürütüldüğünde, `Task` döndürülen tamamlanmış olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="947a4-213">When it has executed to completion, the returned `Task` indicates that it is complete.</span></span>
<span data-ttu-id="947a4-214">Arama kodu, ne `Task` zaman tamamlandığını belirlemek için döndürülenleri izleyebilir.</span><span class="sxs-lookup"><span data-stu-id="947a4-214">Calling code can monitor that returned `Task` to determine when it has completed.</span></span>

<span data-ttu-id="947a4-215">Bu yeni yöntemi yönteminizde `Main` arayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="947a4-215">You can call this new method in your `Main` method:</span></span>

```csharp
ShowTeleprompter().Wait();
```

<span data-ttu-id="947a4-216">Burada, `Main`içinde , kod eşzamanlı olarak bekler.</span><span class="sxs-lookup"><span data-stu-id="947a4-216">Here, in `Main`, the code does synchronously wait.</span></span> <span data-ttu-id="947a4-217">Mümkün olduğunda `await` eşzamanlı olarak beklemek yerine işleci kullanmalısınız.</span><span class="sxs-lookup"><span data-stu-id="947a4-217">You should use the `await` operator instead of synchronously waiting whenever possible.</span></span> <span data-ttu-id="947a4-218">Ancak, bir konsol uygulamasının `Main` `await` yönteminde, işleci kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="947a4-218">But, in a console application's `Main` method, you cannot use the `await` operator.</span></span> <span data-ttu-id="947a4-219">Bu, tüm görevler tamamlanmadan uygulamanın çıkmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="947a4-219">That would result in the application exiting before all tasks have completed.</span></span>

> [!NOTE]
> <span data-ttu-id="947a4-220">C# 7.1 veya daha yeni kullanırsanız, [ `async` `Main` yöntemle](../whats-new/csharp-7-1.md#async-main)konsol uygulamaları oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="947a4-220">If you use C# 7.1 or later, you can create console applications with [`async` `Main` method](../whats-new/csharp-7-1.md#async-main).</span></span>

<span data-ttu-id="947a4-221">Daha sonra, Konsol'dan okumak ve '<' (daha az), '>' (büyüktür) ve 'X' veya 'x' tuşlarını izlemek için ikinci eşzamanlı yöntemi yazmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="947a4-221">Next, you need to write the second asynchronous method to read from the Console and watch for the '<' (less than), '>' (greater than) and 'X' or 'x' keys.</span></span> <span data-ttu-id="947a4-222">Bu görev için eklediğiniz yöntem şunlardır:</span><span class="sxs-lookup"><span data-stu-id="947a4-222">Here's the method you add for that task:</span></span>

```csharp
private static async Task GetInput()
{
    var delay = 200;
    Action work = () =>
    {
        do {
            var key = Console.ReadKey(true);
            if (key.KeyChar == '>')
            {
                delay -= 10;
            }
            else if (key.KeyChar == '<')
            {
                delay += 10;
            }
            else if (key.KeyChar == 'X' || key.KeyChar == 'x')
            {
                break;
            }
        } while (true);
    };
    await Task.Run(work);
}
```

<span data-ttu-id="947a4-223">Bu, Konsol'dan bir anahtarı <xref:System.Action> okuyan bir temsilciyi temsil eden bir lambda ifadesi oluşturur ve kullanıcı '<' (daha az) veya '>' (büyüktür) tuşlarına bastığında gecikmeyi temsil eden yerel bir değişkeni değiştirir.</span><span class="sxs-lookup"><span data-stu-id="947a4-223">This creates a lambda expression to represent an <xref:System.Action> delegate that reads a key from the Console and modifies a local variable representing the delay when the user presses the '<' (less than) or '>' (greater than) keys.</span></span> <span data-ttu-id="947a4-224">Temsilci yöntemi, kullanıcının metin ekranını istediği zaman durdurmasına olanak tanıyan 'X' veya 'x' tuşlarına bastığında sona eler.</span><span class="sxs-lookup"><span data-stu-id="947a4-224">The delegate method finishes when user presses the 'X' or 'x'  keys, which allow the user to stop the text display at any time.</span></span> <span data-ttu-id="947a4-225">Bu yöntem, kullanıcının bir tuşa basmasını engellemek ve beklemek için kullanır. <xref:System.Console.ReadKey></span><span class="sxs-lookup"><span data-stu-id="947a4-225">This method uses <xref:System.Console.ReadKey> to block and wait for the user to press a key.</span></span>

<span data-ttu-id="947a4-226">Bu özelliği tamamlamak için, bu `async Task` görevlerin her ikisini de başlatan`GetInput` `ShowTeleprompter`(ve) ve bu iki görev arasındaki paylaşılan verileri yöneten yeni bir dönen yöntem oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="947a4-226">To finish this feature, you need to create a new `async Task` returning method that starts both of these tasks (`GetInput` and `ShowTeleprompter`), and also manages the shared data between these two tasks.</span></span>

<span data-ttu-id="947a4-227">Bu iki görev arasında paylaşılan verileri işleyebilir bir sınıf oluşturma nın zamanı.</span><span class="sxs-lookup"><span data-stu-id="947a4-227">It's time to create a class that can handle the shared data between these two tasks.</span></span> <span data-ttu-id="947a4-228">Bu sınıf iki ortak özellik içerir: `Done` gecikme ve dosyanın tamamen okunduğunu gösteren bir bayrak:</span><span class="sxs-lookup"><span data-stu-id="947a4-228">This class contains two public properties: the delay, and a flag `Done` to indicate that the file has been completely read:</span></span>

```csharp
namespace TeleprompterConsole
{
    internal class TelePrompterConfig
    {
        public int DelayInMilliseconds { get; private set; } = 200;

        public void UpdateDelay(int increment) // negative to speed up
        {
            var newDelay = Min(DelayInMilliseconds + increment, 1000);
            newDelay = Max(newDelay, 20);
            DelayInMilliseconds = newDelay;
        }

        public bool Done { get; private set; }

        public void SetDone()
        {
            Done = true;
        }
    }
}
```

<span data-ttu-id="947a4-229">Bu sınıfı yeni bir dosyaya koyun ve `TeleprompterConsole` bu sınıfı yukarıda gösterildiği gibi ad alanına bürün.</span><span class="sxs-lookup"><span data-stu-id="947a4-229">Put that class in a new file, and enclose that class in the `TeleprompterConsole` namespace as shown above.</span></span> <span data-ttu-id="947a4-230">Ayrıca, ekleyen sınıf `using static` veya ad alanı adları `Min` `Max` olmadan ve yöntemlere başvuru yapabilmeniz için bir deyim eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="947a4-230">You'll also need to add a `using static` statement so that you can reference the `Min` and `Max` methods without the enclosing class or namespace names.</span></span> <span data-ttu-id="947a4-231">Bir [`using static`](../language-reference/keywords/using-static.md) deyim yöntemleri bir sınıftan içeri yedirer.</span><span class="sxs-lookup"><span data-stu-id="947a4-231">A [`using static`](../language-reference/keywords/using-static.md) statement imports the methods from one class.</span></span> <span data-ttu-id="947a4-232">Bu, bu noktaya `using` kadar kullanılan ve tüm sınıfları bir ad alanından alan ifadelerle zıttır.</span><span class="sxs-lookup"><span data-stu-id="947a4-232">This is in contrast with the `using` statements used up to this point that have imported all classes from a namespace.</span></span>

```csharp
using static System.Math;
```

<span data-ttu-id="947a4-233">Ardından, yeni `ShowTeleprompter` `config` nesneyi `GetInput` kullanmak için yöntemleri ve yöntemleri güncelleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="947a4-233">Next, you need to update the `ShowTeleprompter` and `GetInput` methods to use the new `config` object.</span></span> <span data-ttu-id="947a4-234">Her iki `Task` görevi `async` başlatmak ve ilk görev tamamlandığında çıkmak için son bir dönen yöntem yazın:</span><span class="sxs-lookup"><span data-stu-id="947a4-234">Write one final `Task` returning `async` method to start both tasks and exit when the first task finishes:</span></span>

```csharp
private static async Task RunTeleprompter()
{
    var config = new TelePrompterConfig();
    var displayTask = ShowTeleprompter(config);

    var speedTask = GetInput(config);
    await Task.WhenAny(displayTask, speedTask);
}
```

<span data-ttu-id="947a4-235">Burada yeni bir yöntem <xref:System.Threading.Tasks.Task.WhenAny(System.Threading.Tasks.Task[])> çağrıdır.</span><span class="sxs-lookup"><span data-stu-id="947a4-235">The one new method here is the <xref:System.Threading.Tasks.Task.WhenAny(System.Threading.Tasks.Task[])> call.</span></span> <span data-ttu-id="947a4-236">Bu, bağımsız `Task` değişken listesindeki görevlerden herhangi biri tamamlanır tamamlanmaz sona erdirilen bir sonuç oluşturur.</span><span class="sxs-lookup"><span data-stu-id="947a4-236">That creates a `Task` that finishes as soon as any of the tasks in its argument list completes.</span></span>

<span data-ttu-id="947a4-237">Ardından, gecikme için `ShowTeleprompter` `GetInput` `config` nesneyi kullanmak için hem yöntemleri hem de yöntemleri güncelleştirmeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="947a4-237">Next, you need to update both the `ShowTeleprompter` and `GetInput` methods to use the `config` object for the delay:</span></span>

```csharp
private static async Task ShowTeleprompter(TelePrompterConfig config)
{
    var words = ReadFrom("sampleQuotes.txt");
    foreach (var word in words)
    {
        Console.Write(word);
        if (!string.IsNullOrWhiteSpace(word))
        {
            await Task.Delay(config.DelayInMilliseconds);
        }
    }
    config.SetDone();
}

private static async Task GetInput(TelePrompterConfig config)
{
    Action work = () =>
    {
        do {
            var key = Console.ReadKey(true);
            if (key.KeyChar == '>')
                config.UpdateDelay(-10);
            else if (key.KeyChar == '<')
                config.UpdateDelay(10);
            else if (key.KeyChar == 'X' || key.KeyChar == 'x')
                config.SetDone();
        } while (!config.Done);
    };
    await Task.Run(work);
}
```

<span data-ttu-id="947a4-238">Bu yeni `ShowTeleprompter` sürüm `TeleprompterConfig` sınıfta yeni bir yöntem çağırır.</span><span class="sxs-lookup"><span data-stu-id="947a4-238">This new version of `ShowTeleprompter` calls a new method in the `TeleprompterConfig` class.</span></span> <span data-ttu-id="947a4-239">Şimdi, yerine aramak `Main` `RunTeleprompter` için güncelleştirmeniz `ShowTeleprompter`gerekir:</span><span class="sxs-lookup"><span data-stu-id="947a4-239">Now, you need to update `Main` to call `RunTeleprompter` instead of `ShowTeleprompter`:</span></span>

```csharp
RunTeleprompter().Wait();
```

## <a name="conclusion"></a><span data-ttu-id="947a4-240">Sonuç</span><span class="sxs-lookup"><span data-stu-id="947a4-240">Conclusion</span></span>

<span data-ttu-id="947a4-241">Bu öğretici, C# dili ve Konsol uygulamalarında çalışmakla ilgili .NET Core kitaplıkları ile ilgili bir dizi özelliği size göstermiştir.</span><span class="sxs-lookup"><span data-stu-id="947a4-241">This tutorial showed you a number of the features around the C# language and the .NET Core libraries related to working in Console applications.</span></span> <span data-ttu-id="947a4-242">Dil ve burada tanıtılan sınıflar hakkında daha fazla bilgi keşfetmek için bu bilgiyi üzerine inşa edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="947a4-242">You can build on this knowledge to explore more about the language, and the classes introduced here.</span></span> <span data-ttu-id="947a4-243">Dosya ve Console G/Ç'nin temellerini, Görev tabanlı eşzamanlı programlamanın kullanımını engellemeyi ve engellemeyenleri, C# dilini ve C# programlarının nasıl düzenlendiğini ve .NET Core CLI'yi gördünüz.</span><span class="sxs-lookup"><span data-stu-id="947a4-243">You've seen the basics of File and Console I/O, blocking and non-blocking use of the Task-based asynchronous programming, a tour of the C# language and how C# programs are organized, and the .NET Core CLI.</span></span>

<span data-ttu-id="947a4-244">Dosya G/Ç hakkında daha fazla bilgi için [Dosya ve Akış G/Ç](../../standard/io/index.md) konusuna bakın.</span><span class="sxs-lookup"><span data-stu-id="947a4-244">For more information about File I/O, see the [File and Stream I/O](../../standard/io/index.md) topic.</span></span> <span data-ttu-id="947a4-245">Bu eğitimde kullanılan eşzamanlı programlama modeli hakkında daha fazla bilgi için [Görev tabanlı Asynchronous Programming](../..//standard/parallel-programming/task-based-asynchronous-programming.md) konusuna ve [Asynchronous programlama](../async.md) konusuna bakın.</span><span class="sxs-lookup"><span data-stu-id="947a4-245">For more information about asynchronous programming model used in this tutorial, see the [Task-based Asynchronous Programming](../..//standard/parallel-programming/task-based-asynchronous-programming.md) topic and the [Asynchronous programming](../async.md) topic.</span></span>
