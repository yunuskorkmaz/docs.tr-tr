---
title: Konsol Uygulaması
description: Bu öğretici bir dizi özellik .NET Core ve C# dili öğretir.
ms.date: 03/06/2017
ms.assetid: 883cd93d-50ce-4144-b7c9-2df28d9c11a0
ms.openlocfilehash: bae03c9ae02f2888b1b70617ca712ef7927e9dce
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33355492"
---
# <a name="console-application"></a><span data-ttu-id="89aa1-103">Konsol Uygulaması</span><span class="sxs-lookup"><span data-stu-id="89aa1-103">Console Application</span></span>

<span data-ttu-id="89aa1-104">Bu öğretici bir dizi özellik .NET Core ve C# dili öğretir.</span><span class="sxs-lookup"><span data-stu-id="89aa1-104">This tutorial teaches you a number of features in .NET Core and the C# language.</span></span> <span data-ttu-id="89aa1-105">Şunları öğreneceksiniz:</span><span class="sxs-lookup"><span data-stu-id="89aa1-105">You’ll learn:</span></span>

- <span data-ttu-id="89aa1-106">.NET Core komut satırı arabirimi (CLI) Temelleri</span><span class="sxs-lookup"><span data-stu-id="89aa1-106">The basics of the .NET Core Command Line Interface (CLI)</span></span>
- <span data-ttu-id="89aa1-107">Bir C# konsol uygulaması yapısı</span><span class="sxs-lookup"><span data-stu-id="89aa1-107">The structure of a C# Console Application</span></span>
- <span data-ttu-id="89aa1-108">Konsol g/ç</span><span class="sxs-lookup"><span data-stu-id="89aa1-108">Console I/O</span></span>
- <span data-ttu-id="89aa1-109">Dosya g/ç API'leri .NET temelleri</span><span class="sxs-lookup"><span data-stu-id="89aa1-109">The basics of File I/O APIs in .NET</span></span>
- <span data-ttu-id="89aa1-110">Görev tabanlı zaman uyumsuz programlama .NET temelleri</span><span class="sxs-lookup"><span data-stu-id="89aa1-110">The basics of the Task-based Asynchronous Programming in .NET</span></span>

<span data-ttu-id="89aa1-111">Bir metin dosyasını okur ve konsola, metin dosyasının içeriğini görüntülemektedir bir uygulama oluşturmak.</span><span class="sxs-lookup"><span data-stu-id="89aa1-111">You’ll build an application that reads a text file, and echoes the contents of that text file to the console.</span></span> <span data-ttu-id="89aa1-112">Konsola çıktı sesli okuma eşleşecek şekilde hızını belirleyebileceği.</span><span class="sxs-lookup"><span data-stu-id="89aa1-112">The output to the console is paced to match reading it aloud.</span></span> <span data-ttu-id="89aa1-113">Hızlandırma ya da hızınıza tuşlarına basarak yavaş ' <' veya ' >' anahtarları.</span><span class="sxs-lookup"><span data-stu-id="89aa1-113">You can speed up or slow down the pace by pressing the ‘<’ or ‘>’ keys.</span></span>

<span data-ttu-id="89aa1-114">Bu öğreticide birçok özellik vardır.</span><span class="sxs-lookup"><span data-stu-id="89aa1-114">There are a lot of features in this tutorial.</span></span> <span data-ttu-id="89aa1-115">Şimdi bunları tek tek oluşturun.</span><span class="sxs-lookup"><span data-stu-id="89aa1-115">Let’s build them one by one.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="89aa1-116">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="89aa1-116">Prerequisites</span></span>

<span data-ttu-id="89aa1-117">.NET Core çalışmasına, makine Kurulum gerekir.</span><span class="sxs-lookup"><span data-stu-id="89aa1-117">You’ll need to setup your machine to run .NET Core.</span></span> <span data-ttu-id="89aa1-118">Yükleme yönergelerini bulabilirsiniz [.NET Core](https://www.microsoft.com/net/core) sayfası.</span><span class="sxs-lookup"><span data-stu-id="89aa1-118">You can find the installation instructions on the [.NET Core](https://www.microsoft.com/net/core) page.</span></span> <span data-ttu-id="89aa1-119">Bu uygulama, Windows, Linux, macOS veya Docker kapsayıcısı çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="89aa1-119">You can run this application on Windows, Linux, macOS or in a Docker container.</span></span>
<span data-ttu-id="89aa1-120">Sık kullanılan Kod Düzenleyicisi'ni yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="89aa1-120">You’ll need to install your favorite code editor.</span></span>

## <a name="create-the-application"></a><span data-ttu-id="89aa1-121">Uygulama oluşturma</span><span class="sxs-lookup"><span data-stu-id="89aa1-121">Create the Application</span></span>

<span data-ttu-id="89aa1-122">İlk adım, yeni bir uygulama oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="89aa1-122">The first step is to create a new application.</span></span> <span data-ttu-id="89aa1-123">Bir komut istemi açın ve uygulamanız için yeni bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="89aa1-123">Open a command prompt and create a new directory for your application.</span></span> <span data-ttu-id="89aa1-124">Geçerli dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="89aa1-124">Make that the current directory.</span></span> <span data-ttu-id="89aa1-125">Komut türü `dotnet new console` komut isteminde.</span><span class="sxs-lookup"><span data-stu-id="89aa1-125">Type the command `dotnet new console` at the command prompt.</span></span> <span data-ttu-id="89aa1-126">Bu, temel bir "Hello World" uygulaması için başlangıç dosyaları oluşturur.</span><span class="sxs-lookup"><span data-stu-id="89aa1-126">This creates the starter files for a basic "Hello World" application.</span></span>

<span data-ttu-id="89aa1-127">Değişiklik yapmaya başlamadan önce basit Hello World uygulamasını çalıştırmak için adımlara edelim.</span><span class="sxs-lookup"><span data-stu-id="89aa1-127">Before you start making modifications, let’s go through the steps to run the simple Hello World application.</span></span> <span data-ttu-id="89aa1-128">Uygulamayı oluşturduktan sonra yazın `dotnet restore` komut isteminde.</span><span class="sxs-lookup"><span data-stu-id="89aa1-128">After creating the application, type `dotnet restore` at the command prompt.</span></span> <span data-ttu-id="89aa1-129">Bu komut, NuGet paket geri yükleme işlemi çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="89aa1-129">This command runs the NuGet package restore process.</span></span> <span data-ttu-id="89aa1-130">NuGet, bir .NET paketi yöneticisidir.</span><span class="sxs-lookup"><span data-stu-id="89aa1-130">NuGet is a .NET package manager.</span></span> <span data-ttu-id="89aa1-131">Bu komut, projeniz için eksik bağımlılıklar hiçbirini indirir.</span><span class="sxs-lookup"><span data-stu-id="89aa1-131">This command downloads any of the missing dependencies for your project.</span></span> <span data-ttu-id="89aa1-132">Yeni bir proje olarak ilk çalıştırmada .NET Core framework yükleyecek şekilde bağımlılıkları yerinde yok.</span><span class="sxs-lookup"><span data-stu-id="89aa1-132">As this is a new project, none of the dependencies are in place, so the first run will download the .NET Core framework.</span></span> <span data-ttu-id="89aa1-133">Bu ilk adımı tamamlandıktan sonra yalnızca çalıştırmanız gerekir `dotnet restore` yeni bağımlı paketler eklediğinizde, veya bağımlılıklarınızı hiçbirini sürümlerini güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="89aa1-133">After this initial step, you will only need to run `dotnet restore` when you add new dependent packages, or update the versions of any of your dependencies.</span></span>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="89aa1-134">Paketler geri yükledikten sonra çalıştırmanız `dotnet build`.</span><span class="sxs-lookup"><span data-stu-id="89aa1-134">After restoring packages, you run `dotnet build`.</span></span> <span data-ttu-id="89aa1-135">Bu yapı altyapısı yürütür ve uygulamanızın yürütülebilir oluşturur.</span><span class="sxs-lookup"><span data-stu-id="89aa1-135">This executes the build engine and creates your application executable.</span></span> <span data-ttu-id="89aa1-136">Son olarak, yürütme `dotnet run` uygulamanızı çalıştırmak için.</span><span class="sxs-lookup"><span data-stu-id="89aa1-136">Finally, you execute `dotnet run` to run your application.</span></span>

<span data-ttu-id="89aa1-137">Basit Hello World uygulama tüm Program.cs içinde kodudur.</span><span class="sxs-lookup"><span data-stu-id="89aa1-137">The simple Hello World application code is all in Program.cs.</span></span> <span data-ttu-id="89aa1-138">Bu dosya, sık kullandığınız metin düzenleyicisiyle açın.</span><span class="sxs-lookup"><span data-stu-id="89aa1-138">Open that file with your favorite text editor.</span></span> <span data-ttu-id="89aa1-139">İlk değişikliklerimizi yapmak üzere çalışıyoruz.</span><span class="sxs-lookup"><span data-stu-id="89aa1-139">We’re about to make our first changes.</span></span>
<span data-ttu-id="89aa1-140">Kullanarak bir dosyanın üst kısmında, bkz: deyimi:</span><span class="sxs-lookup"><span data-stu-id="89aa1-140">At the top of the file, see a using statement:</span></span>

```csharp
using System;
```

<span data-ttu-id="89aa1-141">Bu deyim herhangi yazdığı gelen derleyici söyler `System` ad alanı olan kapsam içinde.</span><span class="sxs-lookup"><span data-stu-id="89aa1-141">This statement tells the compiler that any types from the `System` namespace are in scope.</span></span> <span data-ttu-id="89aa1-142">Kullanmış diğer nesne yönelimli diller gibi C# ad alanları türleri düzenlemek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="89aa1-142">Like other Object Oriented languages you may have used, C# uses namespaces to organize types.</span></span> <span data-ttu-id="89aa1-143">Bu Hello World programı farklı değildir.</span><span class="sxs-lookup"><span data-stu-id="89aa1-143">This Hello World program is no different.</span></span> <span data-ttu-id="89aa1-144">Geçerli dizin adını temel alarak adlı ad alanında programın içine görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="89aa1-144">You can see that the program is enclosed in the namespace with the name based on the name of the current directory.</span></span> <span data-ttu-id="89aa1-145">Bu öğretici için ad alanı değiştirelim `TeleprompterConsole`:</span><span class="sxs-lookup"><span data-stu-id="89aa1-145">For this tutorial, let's change the name of the namespace to `TeleprompterConsole`:</span></span>

```csharp
namespace TeleprompterConsole
```

## <a name="reading-and-echoing-the-file"></a><span data-ttu-id="89aa1-146">Okuma ve dosyayı Yankı</span><span class="sxs-lookup"><span data-stu-id="89aa1-146">Reading and Echoing the File</span></span>

<span data-ttu-id="89aa1-147">Metin dosyası okuma ve tüm metni konsola görüntüleme olanağı eklemek için ilk özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="89aa1-147">The first feature to add is the ability to read a text file and display all that text to the console.</span></span> <span data-ttu-id="89aa1-148">İlk olarak, bir metin dosyası ekleyelim.</span><span class="sxs-lookup"><span data-stu-id="89aa1-148">First, let’s add a text file.</span></span> <span data-ttu-id="89aa1-149">Kopya [sampleQuotes.txt](https://github.com/dotnet/samples/raw/master/csharp/getting-started/console-teleprompter/sampleQuotes.txt) GitHub deposuna bir dosyadan bu [örnek](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-teleprompter) proje dizinine.</span><span class="sxs-lookup"><span data-stu-id="89aa1-149">Copy the [sampleQuotes.txt](https://github.com/dotnet/samples/raw/master/csharp/getting-started/console-teleprompter/sampleQuotes.txt) file from the GitHub repository for this [sample](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-teleprompter) into your project directory.</span></span> <span data-ttu-id="89aa1-150">Bu, uygulamanız için komut dosyası olarak hizmet verecektir.</span><span class="sxs-lookup"><span data-stu-id="89aa1-150">This will serve as the script for your application.</span></span> <span data-ttu-id="89aa1-151">Bu konu için örnek uygulama indirme hakkında bilgi edinmek istiyorsanız deki yönergelere bakın [örnekler ve öğreticiler](../../samples-and-tutorials/index.md#viewing-and-downloading-samples) konu.</span><span class="sxs-lookup"><span data-stu-id="89aa1-151">If you would like information on how to download the sample app for this topic, see the instructions in the [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples) topic.</span></span>

<span data-ttu-id="89aa1-152">Sonra aşağıdaki yöntemi ekleyin, `Program` sınıfı (hemen altında `Main` yöntemi):</span><span class="sxs-lookup"><span data-stu-id="89aa1-152">Next, add the following method in your `Program` class (right below the `Main` method):</span></span>

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

<span data-ttu-id="89aa1-153">Bu yöntem, iki yeni ad alanı türlerinden kullanır.</span><span class="sxs-lookup"><span data-stu-id="89aa1-153">This method uses types from two new namespaces.</span></span> <span data-ttu-id="89aa1-154">Bu, derlemek aşağıdaki iki satırı dosyanın en üstüne ekleyin yapmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="89aa1-154">For this to compile you’ll need to add the following two lines to the top of the file:</span></span>

```csharp
using System.Collections.Generic;
using System.IO;
```

<span data-ttu-id="89aa1-155"><xref:System.Collections.Generic.IEnumerable%601> Arabirimi tanımlanmış <xref:System.Collections.Generic> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="89aa1-155">The <xref:System.Collections.Generic.IEnumerable%601> interface is defined in the <xref:System.Collections.Generic> namespace.</span></span> <span data-ttu-id="89aa1-156"><xref:System.IO.File> Sınıfı tanımlanmış <xref:System.IO> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="89aa1-156">The <xref:System.IO.File> class is defined in the <xref:System.IO> namespace.</span></span>

<span data-ttu-id="89aa1-157">Bu yöntem çağrılır C# yöntemi özel türünde bir *yineleyici yöntemi*.</span><span class="sxs-lookup"><span data-stu-id="89aa1-157">This method is a special type of C# method called an *Iterator method*.</span></span> <span data-ttu-id="89aa1-158">Numaralandırıcı yöntemleri gevşek değerlendirilir dizilerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="89aa1-158">Enumerator methods return sequences that are evaluated lazily.</span></span> <span data-ttu-id="89aa1-159">Dizideki her öğe dizisi kullanan kodu tarafından istenen şekilde oluşturulan anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="89aa1-159">That means each item in the sequence is generated as it is requested by the code consuming the sequence.</span></span> <span data-ttu-id="89aa1-160">Numaralandırıcı yöntemlerden birini veya daha fazlasını içeren yöntemlerdir [ `yield return` ](../language-reference/keywords/yield.md) deyimleri.</span><span class="sxs-lookup"><span data-stu-id="89aa1-160">Enumerator methods are methods that contain one or more [`yield return`](../language-reference/keywords/yield.md) statements.</span></span> <span data-ttu-id="89aa1-161">Tarafından döndürülen nesne `ReadFrom` yöntemi dizideki her öğe oluşturmak için kodunu içerir.</span><span class="sxs-lookup"><span data-stu-id="89aa1-161">The object returned by the `ReadFrom` method contains the code to generate each item in the sequence.</span></span> <span data-ttu-id="89aa1-162">Bu örnekte, metnin sonraki satırı kaynak dosyadan okunuyor ve bu dizeyi döndürme içerir.</span><span class="sxs-lookup"><span data-stu-id="89aa1-162">In this example, that involves reading the next line of text from the source file, and returning that string.</span></span> <span data-ttu-id="89aa1-163">Çağıran kodun sonraki öğe dizisinden istekleri her zaman kodu metnin sonraki satırı dosyadan okur ve döndürür.</span><span class="sxs-lookup"><span data-stu-id="89aa1-163">Each time the calling code requests the next item from the sequence, the code reads the next line of text from the file and returns it.</span></span> <span data-ttu-id="89aa1-164">Dosya tamamen okunduğunda daha fazla öğe yok dizisini gösterir.</span><span class="sxs-lookup"><span data-stu-id="89aa1-164">When the file is completely read, the sequence indicates that there are no more items.</span></span>

<span data-ttu-id="89aa1-165">Size yeni olabilecek iki C# sözdizimi öğe vardır.</span><span class="sxs-lookup"><span data-stu-id="89aa1-165">There are two other C# syntax elements that may be new to you.</span></span> <span data-ttu-id="89aa1-166">[ `using` ](../language-reference/keywords/using-statement.md) Bu yöntem deyiminde kaynak temizleme yönetir.</span><span class="sxs-lookup"><span data-stu-id="89aa1-166">The [`using`](../language-reference/keywords/using-statement.md) statement in this method manages resource cleanup.</span></span> <span data-ttu-id="89aa1-167">İçinde başlatılan değişkeni `using` deyimi (`reader`, bu örnekte) uygulamalıdır <xref:System.IDisposable> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="89aa1-167">The variable that is initialized in the `using` statement (`reader`, in this example) must implement the <xref:System.IDisposable> interface.</span></span> <span data-ttu-id="89aa1-168">Bu arabirim tek bir yöntemi tanımlayan `Dispose`, çağrılabilir kaynak yayımlandığı zaman.</span><span class="sxs-lookup"><span data-stu-id="89aa1-168">That interface defines a single method, `Dispose`, that should be called when the resource should be released.</span></span> <span data-ttu-id="89aa1-169">Yürütme kapanış ayracı ulaştığında derleyici bu çağrı üretir `using` deyimi.</span><span class="sxs-lookup"><span data-stu-id="89aa1-169">The compiler generates that call when execution reaches the closing brace of the `using` statement.</span></span> <span data-ttu-id="89aa1-170">Derleyici tarafından üretilen kod kullanılarak tanımlanmış bloğundaki koddan bir özel durum olsa bile, kaynak yayımlanan sağlar deyimi.</span><span class="sxs-lookup"><span data-stu-id="89aa1-170">The compiler-generated code ensures that the resource is released even if an exception is thrown from the code in the block defined by the using statement.</span></span>

<span data-ttu-id="89aa1-171">`reader` Değişkeni kullanılarak tanımlanmış `var` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="89aa1-171">The `reader` variable is defined using the `var` keyword.</span></span> <span data-ttu-id="89aa1-172">[`var`](../language-reference/keywords/var.md) tanımlayan bir *türü örtük olarak belirlenmiş yerel değişken*.</span><span class="sxs-lookup"><span data-stu-id="89aa1-172">[`var`](../language-reference/keywords/var.md) defines an *implicitly typed local variable*.</span></span> <span data-ttu-id="89aa1-173">Değişken türü değişkenine atanan nesne derleme zamanı türüne göre belirlenir anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="89aa1-173">That means the type of the variable is determined by the compile-time type of the object assigned to the variable.</span></span> <span data-ttu-id="89aa1-174">Dönüş değeri Buraya, <xref:System.IO.File.OpenText(System.String)> olan yöntemini bir <xref:System.IO.StreamReader> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="89aa1-174">Here, that is the return value from the <xref:System.IO.File.OpenText(System.String)> method, which is a <xref:System.IO.StreamReader> object.</span></span>

<span data-ttu-id="89aa1-175">Şimdi, şimdi dosyayı okumak için kod doldurun `Main` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="89aa1-175">Now, let’s fill in the code to read the file in the `Main` method:</span></span>

```csharp
var lines = ReadFrom("sampleQuotes.txt");
foreach (var line in lines)
{
    Console.WriteLine(line);
}
```

<span data-ttu-id="89aa1-176">Program çalıştır (kullanarak `dotnet run`) ve konsola yazdırılır her satırı görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="89aa1-176">Run the program (using `dotnet run`) and you can see every line printed out to the console.</span></span>

## <a name="adding-delays-and-formatting-output"></a><span data-ttu-id="89aa1-177">Gecikme ekleme ve çıktı biçimlendirmesi</span><span class="sxs-lookup"><span data-stu-id="89aa1-177">Adding Delays and Formatting output</span></span>

<span data-ttu-id="89aa1-178">Sahip olduğunuz ne kadar çok hızlı sesli okumak için görüntülenmektedir.</span><span class="sxs-lookup"><span data-stu-id="89aa1-178">What you have is being displayed far too fast to read aloud.</span></span> <span data-ttu-id="89aa1-179">Şimdi çıktıda gecikmeleri eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="89aa1-179">Now you need to add the delays in the output.</span></span> <span data-ttu-id="89aa1-180">Başladığınızda, zaman uyumsuz işleme sağlayan çekirdek kodu bazılarını oluşturmakta.</span><span class="sxs-lookup"><span data-stu-id="89aa1-180">As you start, you’ll be building some of the core code that enables asynchronous processing.</span></span> <span data-ttu-id="89aa1-181">Ancak, ilk adımları birkaç koruma desenlerini izleyin.</span><span class="sxs-lookup"><span data-stu-id="89aa1-181">However, these first steps will follow a few anti-patterns.</span></span> <span data-ttu-id="89aa1-182">Koruma desenleri açıklamaları kodu ekleyin ve daha sonraki adımlarda kod güncelleştirilecek işaret.</span><span class="sxs-lookup"><span data-stu-id="89aa1-182">The anti-patterns are pointed out in comments as you add the code, and the code will be updated in later steps.</span></span>

<span data-ttu-id="89aa1-183">Bu bölüm için iki adım vardır.</span><span class="sxs-lookup"><span data-stu-id="89aa1-183">There are two steps to this section.</span></span> <span data-ttu-id="89aa1-184">İlk olarak, tüm satırlar yerine tek tek sözcükleri döndürmek için yineleyici yöntemini güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="89aa1-184">First, you’ll update the iterator method to return single words instead of entire lines.</span></span> <span data-ttu-id="89aa1-185">Bu değişiklikler ile gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="89aa1-185">That’s done with these modifications.</span></span> <span data-ttu-id="89aa1-186">Değiştir `yield return line;` deyimi aşağıdaki kod ile:</span><span class="sxs-lookup"><span data-stu-id="89aa1-186">Replace the `yield return line;` statement with the following code:</span></span>

```csharp
var words = line.Split(' ');
foreach (var word in words)
{
    yield return word + " ";
}
yield return Environment.NewLine;
```

<span data-ttu-id="89aa1-187">Ardından, nasıl satırlık bir dosyayı kullanmak ve her sözcüğün yazdıktan sonra bir gecikme ekleme değiştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="89aa1-187">Next, you need to modify how you consume the lines of the file, and add a delay after writing each word.</span></span> <span data-ttu-id="89aa1-188">Değiştir `Console.WriteLine(line)` deyiminde `Main` yöntemi aşağıdaki bloğu ile:</span><span class="sxs-lookup"><span data-stu-id="89aa1-188">Replace the `Console.WriteLine(line)` statement in the `Main` method with the following block:</span></span>

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

<span data-ttu-id="89aa1-189"><xref:System.Threading.Tasks.Task> Sınıfı olan <xref:System.Threading.Tasks> eklemek gereken şekilde ad alanı, `using` deyimini dosyanın üst kısmındaki:</span><span class="sxs-lookup"><span data-stu-id="89aa1-189">The <xref:System.Threading.Tasks.Task> class is in the <xref:System.Threading.Tasks> namespace, so you need to add that `using` statement at the top of file:</span></span>

```csharp
using System.Threading.Tasks;
```

<span data-ttu-id="89aa1-190">Örneği çalıştırmak ve çıktısını denetleyin.</span><span class="sxs-lookup"><span data-stu-id="89aa1-190">Run the sample, and check the output.</span></span> <span data-ttu-id="89aa1-191">Şimdi, her tek sözcüklük bir 200 ms gecikmeyle tarafından izlenen yazdırılır.</span><span class="sxs-lookup"><span data-stu-id="89aa1-191">Now, each single word is printed, followed by a 200 ms delay.</span></span> <span data-ttu-id="89aa1-192">Ancak, kaynak metin dosyası 80 karakterden fazla satır sonu olmadan sahip birden fazla satır içerdiğinden görüntülenen çıktının bazı sorunları gösterir.</span><span class="sxs-lookup"><span data-stu-id="89aa1-192">However, the displayed output shows some issues because the source text file has several lines that have more than 80 characters without a line break.</span></span> <span data-ttu-id="89aa1-193">Tarafından kaydırma sırasında okunması zor olabilir.</span><span class="sxs-lookup"><span data-stu-id="89aa1-193">That can be hard to read while it's scrolling by.</span></span> <span data-ttu-id="89aa1-194">Düzeltmek kolay olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="89aa1-194">That’s easy to fix.</span></span> <span data-ttu-id="89aa1-195">Yalnızca her bir satır uzunluğu izlemek ve satır uzunluğu belirli bir eşiği eriştiğinde yeni bir satır oluşturmak.</span><span class="sxs-lookup"><span data-stu-id="89aa1-195">You’ll just keep track of the length of each line, and generate a new line whenever the line length reaches a certain threshold.</span></span> <span data-ttu-id="89aa1-196">Bir yerel değişken bildirimi sonra bildirip `words` içinde `ReadFrom` satır uzunluğu tutan yöntemi:</span><span class="sxs-lookup"><span data-stu-id="89aa1-196">Declare a local variable after the declaration of `words` in the `ReadFrom` method that holds the line length:</span></span>

```csharp
var lineLength = 0;
```

<span data-ttu-id="89aa1-197">Ardından, sonra aşağıdaki kodu ekleyin `yield return word + " ";` deyimi (önce kapanış ayracı):</span><span class="sxs-lookup"><span data-stu-id="89aa1-197">Then, add the following code after the `yield return word + " ";` statement (before the closing brace):</span></span>

```csharp
lineLength += word.Length + 1;
if (lineLength > 70)
{
    yield return Environment.NewLine;
    lineLength = 0;
}
```

<span data-ttu-id="89aa1-198">Örneği çalıştırmak ve sesli önceden yapılandırılmış sırasında okuma kullanabileceksiniz hızınıza.</span><span class="sxs-lookup"><span data-stu-id="89aa1-198">Run the sample, and you’ll be able to read aloud at its pre-configured pace.</span></span>

## <a name="async-tasks"></a><span data-ttu-id="89aa1-199">Zaman uyumsuz görevleri</span><span class="sxs-lookup"><span data-stu-id="89aa1-199">Async Tasks</span></span>

<span data-ttu-id="89aa1-200">Bu son adımda, zaman uyumsuz olarak çıkışını hızlandırmak veya metin görüntüle aşağı yavaş istiyorsanız aynı zamanda okumak için başka bir görev giriş kullanıcıdan çalıştırılırken bir görevde yazmak için kod ekleyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="89aa1-200">In this final step, you’ll add the code to write the output asynchronously in one task, while also running another task to read input from the user if they want to speed up or slow down the text display.</span></span> <span data-ttu-id="89aa1-201">Bu da ve son birkaç adım sahip, gerek duyduğunuz tüm güncelleştirmeleri gerekir.</span><span class="sxs-lookup"><span data-stu-id="89aa1-201">This has a few steps in it and by the end, you’ll have all the updates that you need.</span></span>
<span data-ttu-id="89aa1-202">Zaman uyumsuz bir oluşturmak için ilk adımdır <xref:System.Threading.Tasks.Task> okumak ve dosyayı görüntülemek için oluşturduğunuz kadarki kodunu temsil eder yöntemi döndürüyor.</span><span class="sxs-lookup"><span data-stu-id="89aa1-202">The first step is to create an asynchronous <xref:System.Threading.Tasks.Task> returning method that represents the code you’ve created so far to read and display the file.</span></span>

<span data-ttu-id="89aa1-203">Bu yöntemine ekleyin, `Program` sınıfı (gövdesinden alınır, `Main` yöntemi):</span><span class="sxs-lookup"><span data-stu-id="89aa1-203">Add this method to your `Program` class (it’s taken from the body of your `Main` method):</span></span>

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

<span data-ttu-id="89aa1-204">İki değişiklikler fark edeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="89aa1-204">You’ll notice two changes.</span></span> <span data-ttu-id="89aa1-205">İlk çağırmak yerine yöntemin gövdesine <xref:System.Threading.Tasks.Task.Wait> eşzamanlı olarak bir görevi tamamlamak için beklemek için bu sürümü kullanan `await` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="89aa1-205">First, in the body of the method, instead of calling <xref:System.Threading.Tasks.Task.Wait> to synchronously wait for a task to finish, this version uses the `await` keyword.</span></span> <span data-ttu-id="89aa1-206">Bunu yapmak için eklemeniz gerekir `async` değiştirici yöntem imzası.</span><span class="sxs-lookup"><span data-stu-id="89aa1-206">In order to do that, you need to add the `async` modifier to the method signature.</span></span> <span data-ttu-id="89aa1-207">Bu yöntem bir `Task`.</span><span class="sxs-lookup"><span data-stu-id="89aa1-207">This method returns a `Task`.</span></span> <span data-ttu-id="89aa1-208">Dönüş hiçbir return deyimlerinde olduğunu fark bir `Task` nesnesi.</span><span class="sxs-lookup"><span data-stu-id="89aa1-208">Notice that there are no return statements that return a `Task` object.</span></span> <span data-ttu-id="89aa1-209">Bunun yerine, `Task` nesne derleyici oluşturur kullandığınızda kodla oluşturulur `await` işleci.</span><span class="sxs-lookup"><span data-stu-id="89aa1-209">Instead, that `Task` object is created by code the compiler generates when you use the `await` operator.</span></span> <span data-ttu-id="89aa1-210">Bu yöntem ulaştığında döndürür düşünün bir `await`.</span><span class="sxs-lookup"><span data-stu-id="89aa1-210">You can imagine that this method returns when it reaches an `await`.</span></span> <span data-ttu-id="89aa1-211">Döndürülen `Task` iş tamamlanmadı gösterir.</span><span class="sxs-lookup"><span data-stu-id="89aa1-211">The returned `Task` indicates that the work has not completed.</span></span>
<span data-ttu-id="89aa1-212">Awaited görev tamamlandığında yöntemi sürdürür.</span><span class="sxs-lookup"><span data-stu-id="89aa1-212">The method resumes when the awaited task completes.</span></span> <span data-ttu-id="89aa1-213">Ne zaman çalıştırılmadan tamamlanıncaya kadar döndürülen `Task` tam olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="89aa1-213">When it has executed to completion, the returned `Task` indicates that it is complete.</span></span>
<span data-ttu-id="89aa1-214">Kodu çağırma izleyebilirsiniz döndürülen `Task` zaman tamamlandı belirlemek için.</span><span class="sxs-lookup"><span data-stu-id="89aa1-214">Calling code can monitor that returned `Task` to determine when it has completed.</span></span>

<span data-ttu-id="89aa1-215">Bu yeni yöntemi çağırabilirsiniz, `Main` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="89aa1-215">You can call this new method in your `Main` method:</span></span>

```csharp
ShowTeleprompter().Wait();
```

<span data-ttu-id="89aa1-216">Burada, `Main`, kod zaman uyumlu olarak bekleyin.</span><span class="sxs-lookup"><span data-stu-id="89aa1-216">Here, in `Main`, the code does synchronously wait.</span></span> <span data-ttu-id="89aa1-217">Kullanmanız gereken `await` zaman uyumlu olarak mümkün olduğunca beklemek yerine işleci.</span><span class="sxs-lookup"><span data-stu-id="89aa1-217">You should use the `await` operator instead of synchronously waiting whenever possible.</span></span> <span data-ttu-id="89aa1-218">Ancak, bir konsol uygulamasının `Main` yöntemini kullanamaz `await` işleci.</span><span class="sxs-lookup"><span data-stu-id="89aa1-218">But, in a console application’s `Main` method, you cannot use the `await` operator.</span></span> <span data-ttu-id="89aa1-219">Bu, tüm görevler tamamlandığında önce uygulama çıkma içinde neden olur.</span><span class="sxs-lookup"><span data-stu-id="89aa1-219">That would result in the application exiting before all tasks have completed.</span></span>

> [!NOTE]
> <span data-ttu-id="89aa1-220">C# 7.1 kullanın ya da daha sonra konsol uygulamaları ile oluşturabileceğiniz [ `async` `Main` yöntemi](../whats-new/csharp-7-1.md#async-main).</span><span class="sxs-lookup"><span data-stu-id="89aa1-220">If you use C# 7.1 or later, you can create console applications with [`async` `Main` method](../whats-new/csharp-7-1.md#async-main).</span></span>

<span data-ttu-id="89aa1-221">Ardından, konsoldan okunan ve izlemesi için ikinci zaman uyumsuz yöntem yazmanız gerekir ' <' ve ' >' anahtarları.</span><span class="sxs-lookup"><span data-stu-id="89aa1-221">Next, you need to write the second asynchronous method to read from the Console and watch for the ‘<’ and ‘>’ keys.</span></span> <span data-ttu-id="89aa1-222">Bu görev için eklediğiniz yöntemi şöyledir:</span><span class="sxs-lookup"><span data-stu-id="89aa1-222">Here’s the method you add for that task:</span></span>

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

<span data-ttu-id="89aa1-223">Bu temsil eden bir lambda ifadesi oluşturur bir <xref:System.Action> bir anahtar konsoldan okuyan ve kullanıcı bastığında gecikmesini temsil eden bir yerel değişken değiştirir temsilci ' <' veya ' >' anahtarları.</span><span class="sxs-lookup"><span data-stu-id="89aa1-223">This creates a lambda expression to represent an <xref:System.Action> delegate that reads a key from the Console and modifies a local variable representing the delay when the user presses the ‘<’ or ‘>’ keys.</span></span> <span data-ttu-id="89aa1-224">Bu yöntem <xref:System.Console.ReadKey> engellemek ve kullanıcının herhangi bir tuşa basın için bekleyin.</span><span class="sxs-lookup"><span data-stu-id="89aa1-224">This method uses <xref:System.Console.ReadKey> to block and wait for the user to press a key.</span></span>

<span data-ttu-id="89aa1-225">Bu özellik tamamlamak için yeni bir oluşturmanız gerekir `async Task` hem de bu görevleri başlatır yöntemi döndürme (`GetInput` ve `ShowTeleprompter`) ve ayrıca bu iki görevler arasında paylaşılan veri yönetir.</span><span class="sxs-lookup"><span data-stu-id="89aa1-225">To finish this feature, you need to create a new `async Task` returning method that starts both of these tasks (`GetInput` and `ShowTeleprompter`), and also manages the shared data between these two tasks.</span></span>

<span data-ttu-id="89aa1-226">Bu iki görevler arasında paylaşılan veri işleyebilir bir sınıf oluşturmak için zaman yapılır.</span><span class="sxs-lookup"><span data-stu-id="89aa1-226">It’s time to create a class that can handle the shared data between these two tasks.</span></span> <span data-ttu-id="89aa1-227">Bu sınıf, iki genel özellikleri içerir: gecikme ve bir bayrak `Done` dosyası tamamen okundu belirtmek için:</span><span class="sxs-lookup"><span data-stu-id="89aa1-227">This class contains two public properties: the delay, and a flag `Done` to indicate that the file has been completely read:</span></span>

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

<span data-ttu-id="89aa1-228">Bu sınıfın yeni bir dosyaya yerleştirin ve bu sınıfta içine `TeleprompterConsole` yukarıda gösterildiği gibi ad alanı.</span><span class="sxs-lookup"><span data-stu-id="89aa1-228">Put that class in a new file, and enclose that class in the `TeleprompterConsole` namespace as shown above.</span></span> <span data-ttu-id="89aa1-229">Ayrıca eklemeniz gerekir bir `using static` deyimi, başvurabilmek `Min` ve `Max` kapsayan sınıfı veya ad alanı adları olmadan yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="89aa1-229">You’ll also need to add a `using static` statement so that you can reference the `Min` and `Max` methods without the enclosing class or namespace names.</span></span> <span data-ttu-id="89aa1-230">A [ `using static` ](../language-reference/keywords/using-static.md) deyimi bir sınıftan yöntemleri alır.</span><span class="sxs-lookup"><span data-stu-id="89aa1-230">A [`using static`](../language-reference/keywords/using-static.md) statement imports the methods from one class.</span></span> <span data-ttu-id="89aa1-231">Tersine ile budur `using` bu noktaya kadar kullanılan ifadeleri, bir ad alanındaki tüm sınıfları aldınız.</span><span class="sxs-lookup"><span data-stu-id="89aa1-231">This is in contrast with the `using` statements used up to this point that have imported all classes from a namespace.</span></span>

```csharp
using static System.Math;
```

<span data-ttu-id="89aa1-232">Yeni bir dil özelliği [ `lock` ](../language-reference/keywords/lock-statement.md) deyimi.</span><span class="sxs-lookup"><span data-stu-id="89aa1-232">The other language feature that’s new is the [`lock`](../language-reference/keywords/lock-statement.md) statement.</span></span> <span data-ttu-id="89aa1-233">Bu deyim yalnızca tek bir iş parçacığı herhangi bir zamanda bu kodu olabilir sağlar.</span><span class="sxs-lookup"><span data-stu-id="89aa1-233">This statement ensures that only a single thread can be in that code at any given time.</span></span> <span data-ttu-id="89aa1-234">Bir iş parçacığı kilitli bölümünde ise başka bir iş parçacığı bu bölümün çıkmak ilk iş parçacığı için beklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="89aa1-234">If one thread is in the locked section, other threads must wait for the first thread to exit that section.</span></span> <span data-ttu-id="89aa1-235">`lock` Deyimini kullanan bölümü kilitle korur bir nesne.</span><span class="sxs-lookup"><span data-stu-id="89aa1-235">The `lock` statement uses an object that guards the lock section.</span></span> <span data-ttu-id="89aa1-236">Bu sınıf, özel bir nesne sınıfında kilitlemek için standart bir deyim izler.</span><span class="sxs-lookup"><span data-stu-id="89aa1-236">This class follows a standard idiom to lock a private object in the class.</span></span>

<span data-ttu-id="89aa1-237">Ardından, güncelleştirmeniz gerekir `ShowTeleprompter` ve `GetInput` yeni kullanılacak yöntemleri `config` nesnesi.</span><span class="sxs-lookup"><span data-stu-id="89aa1-237">Next, you need to update the `ShowTeleprompter` and `GetInput` methods to use the new `config` object.</span></span> <span data-ttu-id="89aa1-238">Bir son yazma `Task` döndüren `async` hem görevlerini başlatmak ve ilk görev tamamlandığında çıkmak için yöntem:</span><span class="sxs-lookup"><span data-stu-id="89aa1-238">Write one final `Task` returning `async` method to start both tasks and exit when the first task finishes:</span></span>

```csharp
private static async Task RunTeleprompter()
{
    var config = new TelePrompterConfig();
    var displayTask = ShowTeleprompter(config);

    var speedTask = GetInput(config);
    await Task.WhenAny(displayTask, speedTask);
}
```

<span data-ttu-id="89aa1-239">Yeni yöntemi burada <xref:System.Threading.Tasks.Task.WhenAny(System.Threading.Tasks.Task[])> çağırın.</span><span class="sxs-lookup"><span data-stu-id="89aa1-239">The one new method here is the <xref:System.Threading.Tasks.Task.WhenAny(System.Threading.Tasks.Task[])> call.</span></span> <span data-ttu-id="89aa1-240">Oluşturan bir `Task` kendi bağımsız değişken listesinde görevlerden herhangi birini tamamlandıktan hemen sonra tamamlanır.</span><span class="sxs-lookup"><span data-stu-id="89aa1-240">That creates a `Task` that finishes as soon as any of the tasks in its argument list completes.</span></span>

<span data-ttu-id="89aa1-241">Ardından, her ikisi de güncelleştirmeniz gerekir `ShowTeleprompter` ve `GetInput` kullanılacak yöntemleri `config` nesne gecikme için:</span><span class="sxs-lookup"><span data-stu-id="89aa1-241">Next, you need to update both the `ShowTeleprompter` and `GetInput` methods to use the `config` object for the delay:</span></span>

```csharp
private static async Task ShowTeleprompter(TelePrompterConfig config)
{
    var words = ReadFrom("sampleQuotes.txt");
    foreach (var line in words)
    {
        Console.Write(line);
        if (!string.IsNullOrWhiteSpace(line))
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

<span data-ttu-id="89aa1-242">Bu yeni sürümü `ShowTeleprompter` yeni bir yöntem çağrıları `TeleprompterConfig` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="89aa1-242">This new version of `ShowTeleprompter` calls a new method in the `TeleprompterConfig` class.</span></span> <span data-ttu-id="89aa1-243">Şimdi güncelleştirmeniz gerekir `Main` çağırmak için `RunTeleprompter` yerine `ShowTeleprompter`:</span><span class="sxs-lookup"><span data-stu-id="89aa1-243">Now, you need to update `Main` to call `RunTeleprompter` instead of `ShowTeleprompter`:</span></span>

```csharp
RunTeleprompter().Wait();
```

## <a name="conclusion"></a><span data-ttu-id="89aa1-244">Sonuç</span><span class="sxs-lookup"><span data-stu-id="89aa1-244">Conclusion</span></span>

<span data-ttu-id="89aa1-245">Bu öğretici, bir dizi özellik C# dili ve .NET Core kitaplıkları geçici konsol uygulamaları çalışmayla ilgili gösterdi.</span><span class="sxs-lookup"><span data-stu-id="89aa1-245">This tutorial showed you a number of the features around the C# language and the .NET Core libraries related to working in Console applications.</span></span>
<span data-ttu-id="89aa1-246">Dili ve burada sunulan sınıfları hakkında daha fazla araştırmak için bu bilgilerine oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="89aa1-246">You can build on this knowledge to explore more about the language, and the classes introduced here.</span></span> <span data-ttu-id="89aa1-247">Dosya ve konsol g/ç, engelleme ve engelleyici olmayan kullanımını görev tabanlı zaman uyumsuz programlama, C# dili ve C# programları nasıl düzenlendiği turu ve .NET Core komut satırı arabirimi ve araçları temelleri gördünüz.</span><span class="sxs-lookup"><span data-stu-id="89aa1-247">You’ve seen the basics of File and Console I/O, blocking and non-blocking use of the Task-based asynchronous programming, a tour of the C# language and how C# programs are organized and the .NET Core Command Line Interface and tools.</span></span>

<span data-ttu-id="89aa1-248">Dosya g/ç hakkında daha fazla bilgi için bkz: [dosya ve akış g/ç](../../standard/io/index.md) konu.</span><span class="sxs-lookup"><span data-stu-id="89aa1-248">For more information about File I/O, see the [File and Stream I/O](../../standard/io/index.md) topic.</span></span> <span data-ttu-id="89aa1-249">Bu öğreticide kullanılan zaman uyumsuz programlama modeli hakkında daha fazla bilgi için bkz: [görev tabanlı zaman uyumsuz programlama](../..//standard/parallel-programming/task-based-asynchronous-programming.md) konu ve [zaman uyumsuz programlama](../async.md) konu.</span><span class="sxs-lookup"><span data-stu-id="89aa1-249">For more information about asynchronous programming model used in this tutorial, see the [Task-based Asynchronous Programming](../..//standard/parallel-programming/task-based-asynchronous-programming.md) topic and the [Asynchronous programming](../async.md) topic.</span></span>
