---
title: Konsol Uygulaması
description: Bu öğretici, .NET Core ve C# dili özellikleri sayısı öğretir.
ms.date: 03/06/2017
ms.assetid: 883cd93d-50ce-4144-b7c9-2df28d9c11a0
ms.openlocfilehash: da3f8f913d452b5c3c9dcda6079067c879a678dd
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/20/2018
ms.locfileid: "46478623"
---
# <a name="console-application"></a><span data-ttu-id="1ccb0-103">Konsol Uygulaması</span><span class="sxs-lookup"><span data-stu-id="1ccb0-103">Console Application</span></span>

<span data-ttu-id="1ccb0-104">Bu öğretici, .NET Core ve C# dili özellikleri sayısı öğretir.</span><span class="sxs-lookup"><span data-stu-id="1ccb0-104">This tutorial teaches you a number of features in .NET Core and the C# language.</span></span> <span data-ttu-id="1ccb0-105">Şunları öğreneceksiniz:</span><span class="sxs-lookup"><span data-stu-id="1ccb0-105">You’ll learn:</span></span>

- <span data-ttu-id="1ccb0-106">Temel .NET Core komut satırı arabirimi (CLI)</span><span class="sxs-lookup"><span data-stu-id="1ccb0-106">The basics of the .NET Core Command Line Interface (CLI)</span></span>
- <span data-ttu-id="1ccb0-107">Bir C# konsol uygulaması yapısı</span><span class="sxs-lookup"><span data-stu-id="1ccb0-107">The structure of a C# Console Application</span></span>
- <span data-ttu-id="1ccb0-108">Konsol g/ç</span><span class="sxs-lookup"><span data-stu-id="1ccb0-108">Console I/O</span></span>
- <span data-ttu-id="1ccb0-109">.NET içindeki dosya g/ç API'leri temelleri</span><span class="sxs-lookup"><span data-stu-id="1ccb0-109">The basics of File I/O APIs in .NET</span></span>
- <span data-ttu-id="1ccb0-110">Görev tabanlı zaman uyumsuz programlama .NET temelleri</span><span class="sxs-lookup"><span data-stu-id="1ccb0-110">The basics of the Task-based Asynchronous Programming in .NET</span></span>

<span data-ttu-id="1ccb0-111">Bir metin dosyasını okur ve konsola, metin dosyasının içeriğini yankılayan bir uygulama oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="1ccb0-111">You’ll build an application that reads a text file, and echoes the contents of that text file to the console.</span></span> <span data-ttu-id="1ccb0-112">Konsola çıktı yüksek sesle okumak eşleştirmek için adım adım.</span><span class="sxs-lookup"><span data-stu-id="1ccb0-112">The output to the console is paced to match reading it aloud.</span></span> <span data-ttu-id="1ccb0-113">Hız performansındaki veya uygun bir hızda tuşlarına basarak yavaş ' <' (küçüktür) veya ' >' (büyüktür) anahtarları.</span><span class="sxs-lookup"><span data-stu-id="1ccb0-113">You can speed up or slow down the pace by pressing the ‘<’ (less than) or ‘>’ (greater than) keys.</span></span>

<span data-ttu-id="1ccb0-114">Bu öğreticide birçok özellik vardır.</span><span class="sxs-lookup"><span data-stu-id="1ccb0-114">There are a lot of features in this tutorial.</span></span> <span data-ttu-id="1ccb0-115">Bunları tek tek oluşturalım.</span><span class="sxs-lookup"><span data-stu-id="1ccb0-115">Let’s build them one by one.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="1ccb0-116">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="1ccb0-116">Prerequisites</span></span>

<span data-ttu-id="1ccb0-117">.NET Core çalıştırmak için makinenizi ayarlamak gerekir.</span><span class="sxs-lookup"><span data-stu-id="1ccb0-117">You’ll need to setup your machine to run .NET Core.</span></span> <span data-ttu-id="1ccb0-118">Yükleme yönergelerini bulabilirsiniz [.NET Core](https://www.microsoft.com/net/core) sayfası.</span><span class="sxs-lookup"><span data-stu-id="1ccb0-118">You can find the installation instructions on the [.NET Core](https://www.microsoft.com/net/core) page.</span></span> <span data-ttu-id="1ccb0-119">Bu uygulama, Windows, Linux, macOS veya Docker kapsayıcısı çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1ccb0-119">You can run this application on Windows, Linux, macOS or in a Docker container.</span></span>
<span data-ttu-id="1ccb0-120">Sık kullandığınız Kod Düzenleyicisi'ni yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="1ccb0-120">You’ll need to install your favorite code editor.</span></span>

## <a name="create-the-application"></a><span data-ttu-id="1ccb0-121">Uygulama oluşturma</span><span class="sxs-lookup"><span data-stu-id="1ccb0-121">Create the Application</span></span>

<span data-ttu-id="1ccb0-122">İlk adım, yeni bir uygulama oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="1ccb0-122">The first step is to create a new application.</span></span> <span data-ttu-id="1ccb0-123">Bir komut istemi açın ve uygulamanız için yeni bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="1ccb0-123">Open a command prompt and create a new directory for your application.</span></span> <span data-ttu-id="1ccb0-124">Bu, geçerli bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="1ccb0-124">Make that the current directory.</span></span> <span data-ttu-id="1ccb0-125">Komut türü `dotnet new console` komut isteminde.</span><span class="sxs-lookup"><span data-stu-id="1ccb0-125">Type the command `dotnet new console` at the command prompt.</span></span> <span data-ttu-id="1ccb0-126">Bu, temel bir "Hello World" uygulaması için başlangıç dosyaları oluşturur.</span><span class="sxs-lookup"><span data-stu-id="1ccb0-126">This creates the starter files for a basic "Hello World" application.</span></span>

<span data-ttu-id="1ccb0-127">Bir değişiklik yapmadan başlamadan önce basit bir Hello World uygulamasını çalıştırmak için adımlara Bahsedelim.</span><span class="sxs-lookup"><span data-stu-id="1ccb0-127">Before you start making modifications, let’s go through the steps to run the simple Hello World application.</span></span> <span data-ttu-id="1ccb0-128">Uygulamayı oluşturduktan sonra yazın `dotnet restore` komut isteminde.</span><span class="sxs-lookup"><span data-stu-id="1ccb0-128">After creating the application, type `dotnet restore` at the command prompt.</span></span> <span data-ttu-id="1ccb0-129">Bu komut, NuGet paket geri yükleme işlemi çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="1ccb0-129">This command runs the NuGet package restore process.</span></span> <span data-ttu-id="1ccb0-130">NuGet, .NET paket yöneticisidir.</span><span class="sxs-lookup"><span data-stu-id="1ccb0-130">NuGet is a .NET package manager.</span></span> <span data-ttu-id="1ccb0-131">Bu komut tüm projeniz için eksik bağımlılıkların indirir.</span><span class="sxs-lookup"><span data-stu-id="1ccb0-131">This command downloads any of the missing dependencies for your project.</span></span> <span data-ttu-id="1ccb0-132">Bu yeni bir proje olduğundan, ilk çalıştırma .NET Core framework yükleyecek şekilde bağımlılıkları hiçbiri yerde değil.</span><span class="sxs-lookup"><span data-stu-id="1ccb0-132">As this is a new project, none of the dependencies are in place, so the first run will download the .NET Core framework.</span></span> <span data-ttu-id="1ccb0-133">Bu ilk adımdan sonra yalnızca çalıştırmanız gerekir `dotnet restore` yeni bağımlı paketler eklediğinizde, veya herhangi birini bağımlılıklarınızı sürümlerini güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="1ccb0-133">After this initial step, you will only need to run `dotnet restore` when you add new dependent packages, or update the versions of any of your dependencies.</span></span>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="1ccb0-134">Paketleri geri yükledikten sonra çalıştırmanız `dotnet build`.</span><span class="sxs-lookup"><span data-stu-id="1ccb0-134">After restoring packages, you run `dotnet build`.</span></span> <span data-ttu-id="1ccb0-135">Bu yapı altyapısının yürütür ve uygulamanızın yürütülebilir oluşturur.</span><span class="sxs-lookup"><span data-stu-id="1ccb0-135">This executes the build engine and creates your application executable.</span></span> <span data-ttu-id="1ccb0-136">Son olarak, yürüttüğünüz `dotnet run` uygulamanızı çalıştırmak için.</span><span class="sxs-lookup"><span data-stu-id="1ccb0-136">Finally, you execute `dotnet run` to run your application.</span></span>

<span data-ttu-id="1ccb0-137">Basit bir Hello World uygulama kodu, Program.cs içinde tüm ' dir.</span><span class="sxs-lookup"><span data-stu-id="1ccb0-137">The simple Hello World application code is all in Program.cs.</span></span> <span data-ttu-id="1ccb0-138">Bu dosyayı sevdiğiniz bir metin düzenleyici ile açın.</span><span class="sxs-lookup"><span data-stu-id="1ccb0-138">Open that file with your favorite text editor.</span></span> <span data-ttu-id="1ccb0-139">İlk değişiklikler yapmak üzere çalışıyoruz.</span><span class="sxs-lookup"><span data-stu-id="1ccb0-139">We’re about to make our first changes.</span></span>
<span data-ttu-id="1ccb0-140">Kullanarak bir dosyanın üst kısmında görmek deyimi:</span><span class="sxs-lookup"><span data-stu-id="1ccb0-140">At the top of the file, see a using statement:</span></span>

```csharp
using System;
```

<span data-ttu-id="1ccb0-141">Bu ifade herhangi türlerini, derleyiciye `System` ad alanı kapsamında olan.</span><span class="sxs-lookup"><span data-stu-id="1ccb0-141">This statement tells the compiler that any types from the `System` namespace are in scope.</span></span> <span data-ttu-id="1ccb0-142">Kullanmış diğer nesne yönelimli diller gibi C# ad alanlarında türleri düzenlemek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="1ccb0-142">Like other Object Oriented languages you may have used, C# uses namespaces to organize types.</span></span> <span data-ttu-id="1ccb0-143">Bu Hello World programı farklı değildir.</span><span class="sxs-lookup"><span data-stu-id="1ccb0-143">This Hello World program is no different.</span></span> <span data-ttu-id="1ccb0-144">Program ad alanında geçerli dizin adını temel alarak adı alınmış görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1ccb0-144">You can see that the program is enclosed in the namespace with the name based on the name of the current directory.</span></span> <span data-ttu-id="1ccb0-145">Bu öğreticide, ad alanına adı değiştirelim `TeleprompterConsole`:</span><span class="sxs-lookup"><span data-stu-id="1ccb0-145">For this tutorial, let's change the name of the namespace to `TeleprompterConsole`:</span></span>

```csharp
namespace TeleprompterConsole
```

## <a name="reading-and-echoing-the-file"></a><span data-ttu-id="1ccb0-146">Okuma ve dosyaya Yankı</span><span class="sxs-lookup"><span data-stu-id="1ccb0-146">Reading and Echoing the File</span></span>

<span data-ttu-id="1ccb0-147">Metin dosyası okuma ve bu metin konsoluna görüntüleme olanağı eklemek için ilk özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="1ccb0-147">The first feature to add is the ability to read a text file and display all that text to the console.</span></span> <span data-ttu-id="1ccb0-148">İlk olarak, bir metin dosyasına ekleyelim.</span><span class="sxs-lookup"><span data-stu-id="1ccb0-148">First, let’s add a text file.</span></span> <span data-ttu-id="1ccb0-149">Kopyalama [sampleQuotes.txt](https://github.com/dotnet/samples/raw/master/csharp/getting-started/console-teleprompter/sampleQuotes.txt) bu GitHub deposundan dosya [örnek](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-teleprompter) , proje dizinine.</span><span class="sxs-lookup"><span data-stu-id="1ccb0-149">Copy the [sampleQuotes.txt](https://github.com/dotnet/samples/raw/master/csharp/getting-started/console-teleprompter/sampleQuotes.txt) file from the GitHub repository for this [sample](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-teleprompter) into your project directory.</span></span> <span data-ttu-id="1ccb0-150">Bu, uygulamanız için betik olarak hizmet verecektir.</span><span class="sxs-lookup"><span data-stu-id="1ccb0-150">This will serve as the script for your application.</span></span> <span data-ttu-id="1ccb0-151">Bu konu için örnek uygulamasını indirme hakkında bilgi isterseniz, yönergelere bakın [örnekler ve öğreticiler](../../samples-and-tutorials/index.md#viewing-and-downloading-samples) konu.</span><span class="sxs-lookup"><span data-stu-id="1ccb0-151">If you would like information on how to download the sample app for this topic, see the instructions in the [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples) topic.</span></span>

<span data-ttu-id="1ccb0-152">Ardından, aşağıdaki yöntemi ekleyin, `Program` sınıfı (hemen altına `Main` yöntemi):</span><span class="sxs-lookup"><span data-stu-id="1ccb0-152">Next, add the following method in your `Program` class (right below the `Main` method):</span></span>

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

<span data-ttu-id="1ccb0-153">Bu yöntem, iki yeni ad alanı türlerinden kullanır.</span><span class="sxs-lookup"><span data-stu-id="1ccb0-153">This method uses types from two new namespaces.</span></span> <span data-ttu-id="1ccb0-154">Bu derleme aşağıdaki iki satırı dosyasının en üstüne eklemeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="1ccb0-154">For this to compile you’ll need to add the following two lines to the top of the file:</span></span>

```csharp
using System.Collections.Generic;
using System.IO;
```

<span data-ttu-id="1ccb0-155"><xref:System.Collections.Generic.IEnumerable%601> Arabirimi içinde tanımlanan <xref:System.Collections.Generic> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="1ccb0-155">The <xref:System.Collections.Generic.IEnumerable%601> interface is defined in the <xref:System.Collections.Generic> namespace.</span></span> <span data-ttu-id="1ccb0-156"><xref:System.IO.File> Sınıfı içinde tanımlanan <xref:System.IO> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="1ccb0-156">The <xref:System.IO.File> class is defined in the <xref:System.IO> namespace.</span></span>

<span data-ttu-id="1ccb0-157">Bu yöntem çağrılır C# yöntemi özel türüdür bir *yineleyici yöntem*.</span><span class="sxs-lookup"><span data-stu-id="1ccb0-157">This method is a special type of C# method called an *Iterator method*.</span></span> <span data-ttu-id="1ccb0-158">Numaralandırıcı yöntemleri gevşek değerlendirilir dizilerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="1ccb0-158">Enumerator methods return sequences that are evaluated lazily.</span></span> <span data-ttu-id="1ccb0-159">Dizideki her öğe dizisi kullanan kod tarafından istendiği oluşturulan anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="1ccb0-159">That means each item in the sequence is generated as it is requested by the code consuming the sequence.</span></span> <span data-ttu-id="1ccb0-160">Numaralandırıcı yöntemlerden birini veya daha fazlasını içeren yöntemlerdir [ `yield return` ](../language-reference/keywords/yield.md) deyimleri.</span><span class="sxs-lookup"><span data-stu-id="1ccb0-160">Enumerator methods are methods that contain one or more [`yield return`](../language-reference/keywords/yield.md) statements.</span></span> <span data-ttu-id="1ccb0-161">Tarafından döndürülen nesne `ReadFrom` yöntem dizideki her öğe oluşturmak için kod içeriyor.</span><span class="sxs-lookup"><span data-stu-id="1ccb0-161">The object returned by the `ReadFrom` method contains the code to generate each item in the sequence.</span></span> <span data-ttu-id="1ccb0-162">Bu örnekte, metnin bir sonraki satırı kaynak dosyadan okuma ve o dizeyi döndüren içerir.</span><span class="sxs-lookup"><span data-stu-id="1ccb0-162">In this example, that involves reading the next line of text from the source file, and returning that string.</span></span> <span data-ttu-id="1ccb0-163">Çağıran kod dizisinden bir sonraki öğeye istekleri her zaman kod sonraki satıra bir metin dosyasından verileri okur ve döndürür.</span><span class="sxs-lookup"><span data-stu-id="1ccb0-163">Each time the calling code requests the next item from the sequence, the code reads the next line of text from the file and returns it.</span></span> <span data-ttu-id="1ccb0-164">Dosya tamamen okunduğunda, daha fazla öğe yok dizisini gösterir.</span><span class="sxs-lookup"><span data-stu-id="1ccb0-164">When the file is completely read, the sequence indicates that there are no more items.</span></span>

<span data-ttu-id="1ccb0-165">Sizin için yeni olabilecek diğer iki C# sözdizimi öğe vardır.</span><span class="sxs-lookup"><span data-stu-id="1ccb0-165">There are two other C# syntax elements that may be new to you.</span></span> <span data-ttu-id="1ccb0-166">[ `using` ](../language-reference/keywords/using-statement.md) Bu yöntem deyiminde kaynak temizleme yönetir.</span><span class="sxs-lookup"><span data-stu-id="1ccb0-166">The [`using`](../language-reference/keywords/using-statement.md) statement in this method manages resource cleanup.</span></span> <span data-ttu-id="1ccb0-167">İçinde başlatılan değişkeni `using` deyimi (`reader`, bu örnekte) uygulamalıdır <xref:System.IDisposable> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="1ccb0-167">The variable that is initialized in the `using` statement (`reader`, in this example) must implement the <xref:System.IDisposable> interface.</span></span> <span data-ttu-id="1ccb0-168">Bu arabirim, tek bir yöntemi tanımlar `Dispose`, çağrılabilir kaynak yayınlandığı zaman.</span><span class="sxs-lookup"><span data-stu-id="1ccb0-168">That interface defines a single method, `Dispose`, that should be called when the resource should be released.</span></span> <span data-ttu-id="1ccb0-169">Yürütme kapanış ayracı ulaştığında, derleyici bu çağrı oluşturur `using` deyimi.</span><span class="sxs-lookup"><span data-stu-id="1ccb0-169">The compiler generates that call when execution reaches the closing brace of the `using` statement.</span></span> <span data-ttu-id="1ccb0-170">Derleyicinin ürettiği kodu kullanılarak tanımlanmış bloğundaki kodun bir özel durum olsa bile kaynak serbest bırakılmasını sağlar. deyimi.</span><span class="sxs-lookup"><span data-stu-id="1ccb0-170">The compiler-generated code ensures that the resource is released even if an exception is thrown from the code in the block defined by the using statement.</span></span>

<span data-ttu-id="1ccb0-171">`reader` Değişkeni kullanılarak tanımlanmış `var` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="1ccb0-171">The `reader` variable is defined using the `var` keyword.</span></span> <span data-ttu-id="1ccb0-172">[`var`](../language-reference/keywords/var.md) tanımlayan bir *türü örtük olarak belirlenmiş yerel değişken*.</span><span class="sxs-lookup"><span data-stu-id="1ccb0-172">[`var`](../language-reference/keywords/var.md) defines an *implicitly typed local variable*.</span></span> <span data-ttu-id="1ccb0-173">Değişkeninin türü değişkenine atanan nesnenin derleme zamanı türü tarafından belirlenir anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="1ccb0-173">That means the type of the variable is determined by the compile-time type of the object assigned to the variable.</span></span> <span data-ttu-id="1ccb0-174">Dönüş değeri olan burada <xref:System.IO.File.OpenText(System.String)> olan yöntemini bir <xref:System.IO.StreamReader> nesne.</span><span class="sxs-lookup"><span data-stu-id="1ccb0-174">Here, that is the return value from the <xref:System.IO.File.OpenText(System.String)> method, which is a <xref:System.IO.StreamReader> object.</span></span>

<span data-ttu-id="1ccb0-175">Şimdi, dosyayı okumayı kod şimdi doldurun `Main` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="1ccb0-175">Now, let’s fill in the code to read the file in the `Main` method:</span></span>

```csharp
var lines = ReadFrom("sampleQuotes.txt");
foreach (var line in lines)
{
    Console.WriteLine(line);
}
```

<span data-ttu-id="1ccb0-176">Programı çalıştırın (kullanarak `dotnet run`) konsola yazdırılabilir her satırı görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1ccb0-176">Run the program (using `dotnet run`) and you can see every line printed out to the console.</span></span>

## <a name="adding-delays-and-formatting-output"></a><span data-ttu-id="1ccb0-177">Gecikme ekleme ve çıkışı biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="1ccb0-177">Adding Delays and Formatting output</span></span>

<span data-ttu-id="1ccb0-178">Sahip olduğunuz çok hızlı yüksek sesle okumak için görüntülenmektedir.</span><span class="sxs-lookup"><span data-stu-id="1ccb0-178">What you have is being displayed far too fast to read aloud.</span></span> <span data-ttu-id="1ccb0-179">Şimdi gecikmeleri çıktısında eklemek gerekir.</span><span class="sxs-lookup"><span data-stu-id="1ccb0-179">Now you need to add the delays in the output.</span></span> <span data-ttu-id="1ccb0-180">Başladığınızda, siz bazı zaman uyumsuz işleme etkinleştirir çekirdek kodu oluşturuyor olacaksınız.</span><span class="sxs-lookup"><span data-stu-id="1ccb0-180">As you start, you’ll be building some of the core code that enables asynchronous processing.</span></span> <span data-ttu-id="1ccb0-181">Ancak, ilk adımları bazı ters desenler izler.</span><span class="sxs-lookup"><span data-stu-id="1ccb0-181">However, these first steps will follow a few anti-patterns.</span></span> <span data-ttu-id="1ccb0-182">Ters desenler açıklamalar kodu ekleyin ve daha sonraki adımlarda kod güncelleştirilecek belirtildiği.</span><span class="sxs-lookup"><span data-stu-id="1ccb0-182">The anti-patterns are pointed out in comments as you add the code, and the code will be updated in later steps.</span></span>

<span data-ttu-id="1ccb0-183">Bu bölüm için iki adım vardır.</span><span class="sxs-lookup"><span data-stu-id="1ccb0-183">There are two steps to this section.</span></span> <span data-ttu-id="1ccb0-184">İlk olarak, tüm satırlar yerine tek sözcük döndürülecek yineleyici yöntem güncelleştireceksiniz.</span><span class="sxs-lookup"><span data-stu-id="1ccb0-184">First, you’ll update the iterator method to return single words instead of entire lines.</span></span> <span data-ttu-id="1ccb0-185">Bu değişiklikler ile gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="1ccb0-185">That’s done with these modifications.</span></span> <span data-ttu-id="1ccb0-186">Değiştirin `yield return line;` deyimi aşağıdaki kod ile:</span><span class="sxs-lookup"><span data-stu-id="1ccb0-186">Replace the `yield return line;` statement with the following code:</span></span>

```csharp
var words = line.Split(' ');
foreach (var word in words)
{
    yield return word + " ";
}
yield return Environment.NewLine;
```

<span data-ttu-id="1ccb0-187">Ardından, dosyayı satırlarını kullanma ve nasıl her sözcüğün yazıldıktan sonra gecikme ekleme değiştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="1ccb0-187">Next, you need to modify how you consume the lines of the file, and add a delay after writing each word.</span></span> <span data-ttu-id="1ccb0-188">Değiştirin `Console.WriteLine(line)` deyiminde `Main` aşağıdaki bloğu ile yöntemi:</span><span class="sxs-lookup"><span data-stu-id="1ccb0-188">Replace the `Console.WriteLine(line)` statement in the `Main` method with the following block:</span></span>

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

<span data-ttu-id="1ccb0-189"><xref:System.Threading.Tasks.Task> Sınıfı <xref:System.Threading.Tasks> ad alanı, eklemek istediğiniz şekilde `using` deyimini dosyanın üst:</span><span class="sxs-lookup"><span data-stu-id="1ccb0-189">The <xref:System.Threading.Tasks.Task> class is in the <xref:System.Threading.Tasks> namespace, so you need to add that `using` statement at the top of file:</span></span>

```csharp
using System.Threading.Tasks;
```

<span data-ttu-id="1ccb0-190">Örneği çalıştırın ve çıktıyı denetleyin.</span><span class="sxs-lookup"><span data-stu-id="1ccb0-190">Run the sample, and check the output.</span></span> <span data-ttu-id="1ccb0-191">Artık, bir 200 ms gecikmeyle tarafından izlenen her bir sözcüğe yazdırılır.</span><span class="sxs-lookup"><span data-stu-id="1ccb0-191">Now, each single word is printed, followed by a 200 ms delay.</span></span> <span data-ttu-id="1ccb0-192">Ancak, kaynak metin dosyası 80 karakterden uzun olmayan bir satır sonu sahip birden çok satıra sahip olduğundan görüntülenen çıktının bazı sorunları gösterir.</span><span class="sxs-lookup"><span data-stu-id="1ccb0-192">However, the displayed output shows some issues because the source text file has several lines that have more than 80 characters without a line break.</span></span> <span data-ttu-id="1ccb0-193">Tarafından kaydırma sırasında okunması zor olabilir.</span><span class="sxs-lookup"><span data-stu-id="1ccb0-193">That can be hard to read while it's scrolling by.</span></span> <span data-ttu-id="1ccb0-194">Bu düzeltmek kolay bir işlemdir.</span><span class="sxs-lookup"><span data-stu-id="1ccb0-194">That’s easy to fix.</span></span> <span data-ttu-id="1ccb0-195">Yalnızca her satır uzunluğu izlemek ve yeni bir satır satır uzunluğu belirli bir eşiği eriştiğinde oluşturmak.</span><span class="sxs-lookup"><span data-stu-id="1ccb0-195">You’ll just keep track of the length of each line, and generate a new line whenever the line length reaches a certain threshold.</span></span> <span data-ttu-id="1ccb0-196">Bir yerel değişken bildirimi sonra bildirip `words` içinde `ReadFrom` satır uzunluğu tutan yöntemi:</span><span class="sxs-lookup"><span data-stu-id="1ccb0-196">Declare a local variable after the declaration of `words` in the `ReadFrom` method that holds the line length:</span></span>

```csharp
var lineLength = 0;
```

<span data-ttu-id="1ccb0-197">Ardından, sonra aşağıdaki kodu ekleyin `yield return word + " ";` deyimi (önce kapanış ayracı):</span><span class="sxs-lookup"><span data-stu-id="1ccb0-197">Then, add the following code after the `yield return word + " ";` statement (before the closing brace):</span></span>

```csharp
lineLength += word.Length + 1;
if (lineLength > 70)
{
    yield return Environment.NewLine;
    lineLength = 0;
}
```

<span data-ttu-id="1ccb0-198">Örneği çalıştırmak ve sesli okunabilir önceden yapılandırılmış tutulacak uygun bir hızda.</span><span class="sxs-lookup"><span data-stu-id="1ccb0-198">Run the sample, and you’ll be able to read aloud at its pre-configured pace.</span></span>

## <a name="async-tasks"></a><span data-ttu-id="1ccb0-199">Zaman uyumsuz görevleri</span><span class="sxs-lookup"><span data-stu-id="1ccb0-199">Async Tasks</span></span>

<span data-ttu-id="1ccb0-200">Bu son adımda, zaman uyumsuz olarak çıkış hızını artırın ya da metin görüntülenmesini yavaşlatan isterseniz de okumak için başka bir görev giriş kullanıcıdan çalıştırılırken bir görevde yazan kodu ekleyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="1ccb0-200">In this final step, you’ll add the code to write the output asynchronously in one task, while also running another task to read input from the user if they want to speed up or slow down the text display.</span></span> <span data-ttu-id="1ccb0-201">Bu da ve sonuna birkaç adım vardır, ihtiyacınız olan tüm güncelleştirmeleri gerekir.</span><span class="sxs-lookup"><span data-stu-id="1ccb0-201">This has a few steps in it and by the end, you’ll have all the updates that you need.</span></span>
<span data-ttu-id="1ccb0-202">Zaman uyumsuz oluşturmak için ilk adımıdır <xref:System.Threading.Tasks.Task> okumak ve dosyayı görüntülemek için oluşturduğunuz şimdiye kodunu temsil eden yöntemi döndürüyor.</span><span class="sxs-lookup"><span data-stu-id="1ccb0-202">The first step is to create an asynchronous <xref:System.Threading.Tasks.Task> returning method that represents the code you’ve created so far to read and display the file.</span></span>

<span data-ttu-id="1ccb0-203">Bu yöntemi ekleyin, `Program` sınıfı (gövdesinden alınır, `Main` yöntemi):</span><span class="sxs-lookup"><span data-stu-id="1ccb0-203">Add this method to your `Program` class (it’s taken from the body of your `Main` method):</span></span>

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

<span data-ttu-id="1ccb0-204">İki değişiklikler fark edeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="1ccb0-204">You’ll notice two changes.</span></span> <span data-ttu-id="1ccb0-205">İlk çağırmak yerine yöntemin gövdesinde <xref:System.Threading.Tasks.Task.Wait> zaman uyumlu olarak bir görevin bitmesini beklemek için bu sürümü kullanan `await` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="1ccb0-205">First, in the body of the method, instead of calling <xref:System.Threading.Tasks.Task.Wait> to synchronously wait for a task to finish, this version uses the `await` keyword.</span></span> <span data-ttu-id="1ccb0-206">Bunu yapabilmek için eklemeniz gerekir `async` değiştiricisi metodu imzası.</span><span class="sxs-lookup"><span data-stu-id="1ccb0-206">In order to do that, you need to add the `async` modifier to the method signature.</span></span> <span data-ttu-id="1ccb0-207">Bu yöntem döndürür bir `Task`.</span><span class="sxs-lookup"><span data-stu-id="1ccb0-207">This method returns a `Task`.</span></span> <span data-ttu-id="1ccb0-208">Geri dönüş deyim olduğuna dikkat edin bir `Task` nesne.</span><span class="sxs-lookup"><span data-stu-id="1ccb0-208">Notice that there are no return statements that return a `Task` object.</span></span> <span data-ttu-id="1ccb0-209">Bunun yerine, `Task` nesne kullandığınızda derleyici üretir kod tarafından oluşturulan `await` işleci.</span><span class="sxs-lookup"><span data-stu-id="1ccb0-209">Instead, that `Task` object is created by code the compiler generates when you use the `await` operator.</span></span> <span data-ttu-id="1ccb0-210">Bu yöntem ulaştığında döndürür hayal edebileceğiniz bir `await`.</span><span class="sxs-lookup"><span data-stu-id="1ccb0-210">You can imagine that this method returns when it reaches an `await`.</span></span> <span data-ttu-id="1ccb0-211">Döndürülen `Task` iş değil tamamlandığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="1ccb0-211">The returned `Task` indicates that the work has not completed.</span></span>
<span data-ttu-id="1ccb0-212">Yöntemi, beklenen görev tamamlandığında sürdürür.</span><span class="sxs-lookup"><span data-stu-id="1ccb0-212">The method resumes when the awaited task completes.</span></span> <span data-ttu-id="1ccb0-213">Ne zaman yürütülen tamamlanana kadar döndürülen `Task` tam olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="1ccb0-213">When it has executed to completion, the returned `Task` indicates that it is complete.</span></span>
<span data-ttu-id="1ccb0-214">Kodu çağırma izlemek için kullanabileceğiniz döndürülen `Task` zaman tamamlandı belirlemek için.</span><span class="sxs-lookup"><span data-stu-id="1ccb0-214">Calling code can monitor that returned `Task` to determine when it has completed.</span></span>

<span data-ttu-id="1ccb0-215">Bu yeni yöntemini çağırabilirsiniz, `Main` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="1ccb0-215">You can call this new method in your `Main` method:</span></span>

```csharp
ShowTeleprompter().Wait();
```

<span data-ttu-id="1ccb0-216">Burada, `Main`, kod zaman uyumlu olarak bekleyin.</span><span class="sxs-lookup"><span data-stu-id="1ccb0-216">Here, in `Main`, the code does synchronously wait.</span></span> <span data-ttu-id="1ccb0-217">Kullanmanız gereken `await` mümkün olduğunda eşzamanlı olarak beklemek yerine işleci.</span><span class="sxs-lookup"><span data-stu-id="1ccb0-217">You should use the `await` operator instead of synchronously waiting whenever possible.</span></span> <span data-ttu-id="1ccb0-218">Ancak, bir konsol uygulamasının `Main` yöntemi kullanamaz `await` işleci.</span><span class="sxs-lookup"><span data-stu-id="1ccb0-218">But, in a console application’s `Main` method, you cannot use the `await` operator.</span></span> <span data-ttu-id="1ccb0-219">Bu, tüm görevleri tamamlanmadan uygulamadan çıkmak içinde neden olur.</span><span class="sxs-lookup"><span data-stu-id="1ccb0-219">That would result in the application exiting before all tasks have completed.</span></span>

> [!NOTE]
> <span data-ttu-id="1ccb0-220">C# 7.1 kullandığınız ya da daha sonra konsol uygulamaları ile oluşturabileceğiniz [ `async` `Main` yöntemi](../whats-new/csharp-7-1.md#async-main).</span><span class="sxs-lookup"><span data-stu-id="1ccb0-220">If you use C# 7.1 or later, you can create console applications with [`async` `Main` method](../whats-new/csharp-7-1.md#async-main).</span></span>

<span data-ttu-id="1ccb0-221">Konsoldan okunan ve izlemek için ikinci zaman uyumsuz yöntem yazmanıza gerek ardından, ' <' (küçüktür) ve ' >' (büyüktür) anahtarları.</span><span class="sxs-lookup"><span data-stu-id="1ccb0-221">Next, you need to write the second asynchronous method to read from the Console and watch for the ‘<’ (less than) and ‘>’ (greater than) keys.</span></span> <span data-ttu-id="1ccb0-222">Bu görev için eklediğiniz yöntemi aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="1ccb0-222">Here’s the method you add for that task:</span></span>

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
        } while (true);
    };
    await Task.Run(work);
}
```

<span data-ttu-id="1ccb0-223">Bu bir lambda ifadesini göstermek için oluşturur bir <xref:System.Action> konsoldan bir anahtar okuyan ve kullanıcının bastığında gecikmesini temsil eden yerel bir değişken değiştirir temsilci ' <' (küçüktür) veya ' >' (büyüktür) anahtarları.</span><span class="sxs-lookup"><span data-stu-id="1ccb0-223">This creates a lambda expression to represent an <xref:System.Action> delegate that reads a key from the Console and modifies a local variable representing the delay when the user presses the ‘<’ (less than) or ‘>’ (greater than) keys.</span></span> <span data-ttu-id="1ccb0-224">Bu yöntemde <xref:System.Console.ReadKey> engelleyin ve kullanıcıyı bir tuşa basın.</span><span class="sxs-lookup"><span data-stu-id="1ccb0-224">This method uses <xref:System.Console.ReadKey> to block and wait for the user to press a key.</span></span>

<span data-ttu-id="1ccb0-225">Bu özellik tamamlamak için yeni bir gereksinim `async Task` bu görevlerin her ikisi de başlatan yöntem döndüren (`GetInput` ve `ShowTeleprompter`) ve bu iki görevler arasında paylaşılan veri da yönetir.</span><span class="sxs-lookup"><span data-stu-id="1ccb0-225">To finish this feature, you need to create a new `async Task` returning method that starts both of these tasks (`GetInput` and `ShowTeleprompter`), and also manages the shared data between these two tasks.</span></span>

<span data-ttu-id="1ccb0-226">Bu iki görevler arasında paylaşılan veri işleyen bir sınıf oluşturmak için zaman var.</span><span class="sxs-lookup"><span data-stu-id="1ccb0-226">It’s time to create a class that can handle the shared data between these two tasks.</span></span> <span data-ttu-id="1ccb0-227">Bu sınıfı iki genel özellikleri içerir: gecikme ve bayrak `Done` dosya tamamen Okunmuş olduğunu belirtmek için:</span><span class="sxs-lookup"><span data-stu-id="1ccb0-227">This class contains two public properties: the delay, and a flag `Done` to indicate that the file has been completely read:</span></span>

```csharp
namespace TeleprompterConsole
{
    internal class TelePrompterConfig
    {
        private object lockHandle = new object();
        public int DelayInMilliseconds { get; private set; } = 200;

        public void UpdateDelay(int increment) // negative to speed up
        {
            var newDelay = Min(DelayInMilliseconds + increment, 1000);
            newDelay = Max(newDelay, 20);
            lock (lockHandle)
            {
                DelayInMilliseconds = newDelay;
            }
        }

        public bool Done { get; private set; }

        public void SetDone()
        {
            Done = true;
        }
    }
}
```

<span data-ttu-id="1ccb0-228">Bu sınıfın yeni bir dosya yerleştirin ve bu sınıfta içine `TeleprompterConsole` yukarıda da gösterildiği gibi bir ad alanı.</span><span class="sxs-lookup"><span data-stu-id="1ccb0-228">Put that class in a new file, and enclose that class in the `TeleprompterConsole` namespace as shown above.</span></span> <span data-ttu-id="1ccb0-229">Eklemeniz gerekecektir bir `using static` deyimi, başvuru `Min` ve `Max` kapsayan sınıf veya ad alanı adları olmadan yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="1ccb0-229">You’ll also need to add a `using static` statement so that you can reference the `Min` and `Max` methods without the enclosing class or namespace names.</span></span> <span data-ttu-id="1ccb0-230">A [ `using static` ](../language-reference/keywords/using-static.md) deyimi bir sınıftan yöntemleri alır.</span><span class="sxs-lookup"><span data-stu-id="1ccb0-230">A [`using static`](../language-reference/keywords/using-static.md) statement imports the methods from one class.</span></span> <span data-ttu-id="1ccb0-231">Tersine ile budur `using` bu noktaya kadar kullanılan deyimleri, bir ad alanındaki tüm sınıfları aldınız.</span><span class="sxs-lookup"><span data-stu-id="1ccb0-231">This is in contrast with the `using` statements used up to this point that have imported all classes from a namespace.</span></span>

```csharp
using static System.Math;
```

<span data-ttu-id="1ccb0-232">Yeni bir dil özelliği [ `lock` ](../language-reference/keywords/lock-statement.md) deyimi.</span><span class="sxs-lookup"><span data-stu-id="1ccb0-232">The other language feature that’s new is the [`lock`](../language-reference/keywords/lock-statement.md) statement.</span></span> <span data-ttu-id="1ccb0-233">Bu bildirimi, yalnızca tek bir iş parçacığı kodda herhangi bir zamanda olabilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="1ccb0-233">This statement ensures that only a single thread can be in that code at any given time.</span></span> <span data-ttu-id="1ccb0-234">Bir iş parçacığı kilitli bölümde ise, diğer iş parçacıkları bu bölümü çıkmak ilk iş parçacığı için beklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="1ccb0-234">If one thread is in the locked section, other threads must wait for the first thread to exit that section.</span></span> <span data-ttu-id="1ccb0-235">`lock` Deyim bölümü kilitle korur bir nesne kullanır.</span><span class="sxs-lookup"><span data-stu-id="1ccb0-235">The `lock` statement uses an object that guards the lock section.</span></span> <span data-ttu-id="1ccb0-236">Bu sınıf, özel bir nesne sınıfında kilitlemek için standart bir deyim izler.</span><span class="sxs-lookup"><span data-stu-id="1ccb0-236">This class follows a standard idiom to lock a private object in the class.</span></span>

<span data-ttu-id="1ccb0-237">Ardından, güncelleştirmeye gerek duyduğunuz `ShowTeleprompter` ve `GetInput` yeni yöntemleri `config` nesne.</span><span class="sxs-lookup"><span data-stu-id="1ccb0-237">Next, you need to update the `ShowTeleprompter` and `GetInput` methods to use the new `config` object.</span></span> <span data-ttu-id="1ccb0-238">Bir son yazma `Task` döndüren `async` her iki görevi başlatmak ve ilk görev tamamlandığında çıkmak için yöntemi:</span><span class="sxs-lookup"><span data-stu-id="1ccb0-238">Write one final `Task` returning `async` method to start both tasks and exit when the first task finishes:</span></span>

```csharp
private static async Task RunTeleprompter()
{
    var config = new TelePrompterConfig();
    var displayTask = ShowTeleprompter(config);

    var speedTask = GetInput(config);
    await Task.WhenAny(displayTask, speedTask);
}
```

<span data-ttu-id="1ccb0-239">Burada bir yeni yöntem <xref:System.Threading.Tasks.Task.WhenAny(System.Threading.Tasks.Task[])> çağırın.</span><span class="sxs-lookup"><span data-stu-id="1ccb0-239">The one new method here is the <xref:System.Threading.Tasks.Task.WhenAny(System.Threading.Tasks.Task[])> call.</span></span> <span data-ttu-id="1ccb0-240">Oluşturan bir `Task` kendi bağımsız değişken listesindeki görevleri tamamladıktan hemen sonra tamamlanır.</span><span class="sxs-lookup"><span data-stu-id="1ccb0-240">That creates a `Task` that finishes as soon as any of the tasks in its argument list completes.</span></span>

<span data-ttu-id="1ccb0-241">Ardından, her ikisi de güncelleştirmeye gerek duyduğunuz `ShowTeleprompter` ve `GetInput` kullanılacak yöntemleri `config` nesne gecikme için:</span><span class="sxs-lookup"><span data-stu-id="1ccb0-241">Next, you need to update both the `ShowTeleprompter` and `GetInput` methods to use the `config` object for the delay:</span></span>

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
        } while (!config.Done);
    };
    await Task.Run(work);
}
```

<span data-ttu-id="1ccb0-242">Bu yeni sürümü `ShowTeleprompter` yeni bir yöntem çağrıları `TeleprompterConfig` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="1ccb0-242">This new version of `ShowTeleprompter` calls a new method in the `TeleprompterConfig` class.</span></span> <span data-ttu-id="1ccb0-243">Şimdi, güncelleştirmeye gerek duyduğunuz `Main` çağrılacak `RunTeleprompter` yerine `ShowTeleprompter`:</span><span class="sxs-lookup"><span data-stu-id="1ccb0-243">Now, you need to update `Main` to call `RunTeleprompter` instead of `ShowTeleprompter`:</span></span>

```csharp
RunTeleprompter().Wait();
```

## <a name="conclusion"></a><span data-ttu-id="1ccb0-244">Sonuç</span><span class="sxs-lookup"><span data-stu-id="1ccb0-244">Conclusion</span></span>

<span data-ttu-id="1ccb0-245">Bu öğreticide, bir dizi özellik C# dili ve .NET Core kitaplıkları'ta konsol uygulamaları çalışmayla ilgili gösterdi.</span><span class="sxs-lookup"><span data-stu-id="1ccb0-245">This tutorial showed you a number of the features around the C# language and the .NET Core libraries related to working in Console applications.</span></span>
<span data-ttu-id="1ccb0-246">Dil ve burada sunulan sınıfları hakkında daha fazla araştırmak için bu bilgilerine oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1ccb0-246">You can build on this knowledge to explore more about the language, and the classes introduced here.</span></span> <span data-ttu-id="1ccb0-247">Dosya ve konsol g/ç, görev tabanlı zaman uyumsuz programlama, gezdiriyor C# dili ve C# programları nasıl düzenlendiği ve .NET Core komut satırı arabirimi ve araçları engelleyici ve engelleyici olmayan kullanımı hakkındaki temel bilgileri öğrendiniz.</span><span class="sxs-lookup"><span data-stu-id="1ccb0-247">You’ve seen the basics of File and Console I/O, blocking and non-blocking use of the Task-based asynchronous programming, a tour of the C# language and how C# programs are organized and the .NET Core Command Line Interface and tools.</span></span>

<span data-ttu-id="1ccb0-248">Dosya g/ç hakkında daha fazla bilgi için bkz: [dosya ve Stream g/ç](../../standard/io/index.md) konu.</span><span class="sxs-lookup"><span data-stu-id="1ccb0-248">For more information about File I/O, see the [File and Stream I/O](../../standard/io/index.md) topic.</span></span> <span data-ttu-id="1ccb0-249">Bu öğreticide kullanılan zaman uyumsuz programlama modeli hakkında daha fazla bilgi için bkz. [görev tabanlı zaman uyumsuz programlama](../..//standard/parallel-programming/task-based-asynchronous-programming.md) konu ve [zaman uyumsuz programlama](../async.md) konu.</span><span class="sxs-lookup"><span data-stu-id="1ccb0-249">For more information about asynchronous programming model used in this tutorial, see the [Task-based Asynchronous Programming](../..//standard/parallel-programming/task-based-asynchronous-programming.md) topic and the [Asynchronous programming](../async.md) topic.</span></span>
