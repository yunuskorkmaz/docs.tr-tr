---
title: Üst düzey deyimler-C# öğreticisi
description: Bu öğreticide, fikirlerinizi araştırırken en üst düzey deyimlerinizi deneyip kanıtlarken kavram kanıtlarını nasıl kullanabileceğiniz gösterilmektedir
ms.date: 10/28/2020
ms.openlocfilehash: c56a40e7a9715ff0265a897c494b457a32e52df2
ms.sourcegitcommit: 65af0f0ad316858882845391d60ef7e303b756e8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/05/2021
ms.locfileid: "99585630"
---
# <a name="tutorial-explore-ideas-using-top-level-statements-to-build-code-as-you-learn"></a><span data-ttu-id="0d5be-103">Öğretici: öğreniniz sırasında kod derlemek için en üst düzey deyimleri kullanarak fikirleri araştırma</span><span class="sxs-lookup"><span data-stu-id="0d5be-103">Tutorial: Explore ideas using top-level statements to build code as you learn</span></span>

<span data-ttu-id="0d5be-104">Bu öğreticide aşağıdakilerin nasıl yapılacağını öğreneceksiniz:</span><span class="sxs-lookup"><span data-stu-id="0d5be-104">In this tutorial, you'll learn how to:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="0d5be-105">En üst düzey deyimlerinizi kullanmanızı düzenleyen kuralları öğrenin.</span><span class="sxs-lookup"><span data-stu-id="0d5be-105">Learn the rules governing your use of top-level statements.</span></span>
> - <span data-ttu-id="0d5be-106">Algoritmaları araştırmak için en üst düzey deyimleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="0d5be-106">Use top-level statements to explore algorithms.</span></span>
> - <span data-ttu-id="0d5be-107">Araştırmaları yeniden kullanılabilir bileşenlerle yeniden düzenleyin.</span><span class="sxs-lookup"><span data-stu-id="0d5be-107">Refactor explorations into reusable components.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="0d5be-108">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="0d5be-108">Prerequisites</span></span>

<span data-ttu-id="0d5be-109">Makinenizde C# 9 derleyicisini içeren .NET 5 ' i çalıştıracak şekilde ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="0d5be-109">You'll need to set up your machine to run .NET 5, which includes the C# 9 compiler.</span></span> <span data-ttu-id="0d5be-110">C# 9 derleyicisi, [Visual Studio 2019 sürüm 16,9 Preview 1](https://visualstudio.microsoft.com/vs/preview/) veya [.NET 5,0 SDK](https://dot.net/get-dotnet5)ile başlayarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0d5be-110">The C# 9 compiler is available starting with [Visual Studio 2019 version 16.9 preview 1](https://visualstudio.microsoft.com/vs/preview/) or [.NET 5.0 SDK](https://dot.net/get-dotnet5).</span></span>

<span data-ttu-id="0d5be-111">Bu öğreticide, Visual Studio veya .NET Core CLI dahil olmak üzere C# ve .NET hakkında bilgi sahibi olduğunuz varsayılır.</span><span class="sxs-lookup"><span data-stu-id="0d5be-111">This tutorial assumes you're familiar with C# and .NET, including either Visual Studio or the .NET Core CLI.</span></span>

## <a name="start-exploring"></a><span data-ttu-id="0d5be-112">Keşfetmeye başlayın</span><span class="sxs-lookup"><span data-stu-id="0d5be-112">Start exploring</span></span>

<span data-ttu-id="0d5be-113">Üst düzey deyimler, programınızın giriş noktasını bir sınıftaki statik bir yönteme yerleştirerek gereken ek bir sertifika oluşmasını önlemenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="0d5be-113">Top-level statements enable you to avoid the extra ceremony required by placing your program's entry point in a static method in a class.</span></span> <span data-ttu-id="0d5be-114">Yeni bir konsol uygulaması için tipik başlangıç noktası aşağıdaki kod gibi görünür:</span><span class="sxs-lookup"><span data-stu-id="0d5be-114">The typical starting point for a new console application looks like the following code:</span></span>

```csharp
using System;

namespace Application
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Hello World!");
        }
    }
}
```

<span data-ttu-id="0d5be-115">Yukarıdaki kod, `dotnet new console` komutunu çalıştırmanın ve yeni bir konsol uygulaması oluşturmanın sonucudur.</span><span class="sxs-lookup"><span data-stu-id="0d5be-115">The preceding code is the result of running the `dotnet new console` command and creating a new console application.</span></span> <span data-ttu-id="0d5be-116">Bu 11 satır yalnızca bir adet yürütülebilir kod içerir.</span><span class="sxs-lookup"><span data-stu-id="0d5be-116">Those 11 lines contain only one line of executable code.</span></span> <span data-ttu-id="0d5be-117">Bu programı, yeni en üst düzey deyimler özelliğiyle basitleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0d5be-117">You can simplify that program with the new top-level statements feature.</span></span> <span data-ttu-id="0d5be-118">Bu, bu programdaki satırlardan yalnızca birini kaldırmanızı sağlar:</span><span class="sxs-lookup"><span data-stu-id="0d5be-118">That enables you to remove all but two of the lines in this program:</span></span>

```csharp
using System;

Console.WriteLine("Hello World!");
```

<span data-ttu-id="0d5be-119">Bu eylem, yeni fikirleri keşfetmeye başlamak için gerekenleri basitleştirir.</span><span class="sxs-lookup"><span data-stu-id="0d5be-119">This action simplifies what's needed to begin exploring new ideas.</span></span> <span data-ttu-id="0d5be-120">Komut dosyası senaryoları için en üst düzey deyimleri kullanabilir veya keşfedebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0d5be-120">You can use top-level statements for scripting scenarios, or to explore.</span></span> <span data-ttu-id="0d5be-121">Temel bilgileri aldıktan sonra kodu yeniden düzenlemeye başlayabilir ve derlediğiniz yeniden kullanılabilir bileşenler için yöntemler, sınıflar veya diğer derlemeler oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0d5be-121">Once you've got the basics working, you can start refactoring the code and create methods, classes, or other assemblies for reusable components you've built.</span></span> <span data-ttu-id="0d5be-122">Üst düzey deyimler hızlı deneme ve başlangıç öğreticilerini etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="0d5be-122">Top-level statements do enable quick experimentation and beginner tutorials.</span></span> <span data-ttu-id="0d5be-123">Ayrıca, deneme 'den tam programlara sorunsuz bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="0d5be-123">They also provide a smooth path from experimentation to full programs.</span></span>

<span data-ttu-id="0d5be-124">Üst düzey deyimler dosyada göründükleri sırada yürütülür.</span><span class="sxs-lookup"><span data-stu-id="0d5be-124">Top-level statements are executed in the order they appear in the file.</span></span> <span data-ttu-id="0d5be-125">En üst düzey deyimler yalnızca uygulamanızdaki tek bir kaynak dosyasında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0d5be-125">Top-level statements can only be used in one source file in your application.</span></span> <span data-ttu-id="0d5be-126">Birden çok dosyada kullandığınızda derleyici bir hata oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0d5be-126">The compiler generates an error if you use them in more than one file.</span></span>

## <a name="build-a-magic-net-answer-machine"></a><span data-ttu-id="0d5be-127">Sihirli .NET yanıt makinesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="0d5be-127">Build a magic .NET answer machine</span></span>

<span data-ttu-id="0d5be-128">Bu öğreticide, rastgele bir Yanıt ile "Evet" veya "Hayır" sorusunu yanıtlayan bir konsol uygulaması oluşturalım.</span><span class="sxs-lookup"><span data-stu-id="0d5be-128">For this tutorial, let's build a console application that answers a "yes" or "no" question with a random answer.</span></span> <span data-ttu-id="0d5be-129">Adım adım işlevselliği oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="0d5be-129">You'll build out the functionality step by step.</span></span> <span data-ttu-id="0d5be-130">Tipik bir programın yapısı için gereken sertifika yerine görevliliğe odaklanırsınız.</span><span class="sxs-lookup"><span data-stu-id="0d5be-130">You can focus on your task rather than ceremony needed for the structure of a typical program.</span></span> <span data-ttu-id="0d5be-131">Daha sonra, işlevsellikten memnun olduğunuzda uygulamayı uygun gördüğünüz şekilde yeniden düzenleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0d5be-131">Then, once you're happy with the functionality, you can refactor the application as you see fit.</span></span>

<span data-ttu-id="0d5be-132">İyi bir başlangıç noktası, soruyu konsola geri yazmaktır.</span><span class="sxs-lookup"><span data-stu-id="0d5be-132">A good starting point is to write the question back to the console.</span></span> <span data-ttu-id="0d5be-133">Aşağıdaki kodu yazarak başlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="0d5be-133">You can start by writing the following code:</span></span>

```csharp
using System;

Console.WriteLine(args);
```

<span data-ttu-id="0d5be-134">Bir değişken bildiremezsiniz `args` .</span><span class="sxs-lookup"><span data-stu-id="0d5be-134">You don't declare an `args` variable.</span></span> <span data-ttu-id="0d5be-135">En üst düzey deyimlerinizi içeren tek kaynak dosya için, derleyici `args` komut satırı bağımsız değişkenlerini anlamı olarak tanır.</span><span class="sxs-lookup"><span data-stu-id="0d5be-135">For the single source file that contains your top-level statements, the compiler recognizes `args` to mean the command-line arguments.</span></span> <span data-ttu-id="0d5be-136">Bağımsız değişkenlerin türü `string[]` , tüm C# programlarında olduğu gibi.</span><span class="sxs-lookup"><span data-stu-id="0d5be-136">The type of args is a `string[]`, as in all C# programs.</span></span>

<span data-ttu-id="0d5be-137">Aşağıdaki komutu çalıştırarak kodunuzu test edebilirsiniz `dotnet run` :</span><span class="sxs-lookup"><span data-stu-id="0d5be-137">You can test your code by running the following `dotnet run` command:</span></span>

```dotnetcli
dotnet run -- Should I use top level statements in all my programs?
```

<span data-ttu-id="0d5be-138">Komut satırındaki öğesinden sonraki bağımsız değişkenler `--` programa geçirilir.</span><span class="sxs-lookup"><span data-stu-id="0d5be-138">The arguments after the `--` on the command line are passed to the program.</span></span> <span data-ttu-id="0d5be-139">Nesnenin türünü görebilirsiniz `args` çünkü bu, konsola yazdırılmıştır:</span><span class="sxs-lookup"><span data-stu-id="0d5be-139">You can see the type of the `args` variable, because that's what's printed to the console:</span></span>

```console
System.String[]
```

<span data-ttu-id="0d5be-140">Soruyu konsola yazmak için, bağımsız değişkenleri numaralandırın ve bir boşluk ile ayırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="0d5be-140">To write the question to the console, you'll need to enumerate the arguments and separate them with a space.</span></span> <span data-ttu-id="0d5be-141">`WriteLine`Çağrıyı aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="0d5be-141">Replace the `WriteLine` call with the following code:</span></span>

:::code language="csharp" source="snippets/top-level-statements/ProgramSnippets.cs" ID="EchoInput":::

<span data-ttu-id="0d5be-142">Artık programı çalıştırdığınızda, soruyu bir bağımsız değişken dizesi olarak doğru şekilde görüntüler.</span><span class="sxs-lookup"><span data-stu-id="0d5be-142">Now, when you run the program, it will correctly display the question as a string of arguments.</span></span>

## <a name="respond-with-a-random-answer"></a><span data-ttu-id="0d5be-143">Rastgele bir Yanıtla yanıtla</span><span class="sxs-lookup"><span data-stu-id="0d5be-143">Respond with a random answer</span></span>

<span data-ttu-id="0d5be-144">Soruyu yankıladıktan sonra rastgele yanıtı oluşturmak için kodu ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0d5be-144">After echoing the question, you can add the code to generate the random answer.</span></span> <span data-ttu-id="0d5be-145">Olası bir yanıt dizisi ekleyerek başlayın:</span><span class="sxs-lookup"><span data-stu-id="0d5be-145">Start by adding an array of possible answers:</span></span>

:::code language="csharp" source="snippets/top-level-statements/ProgramSnippets.cs" ID="Answers":::

<span data-ttu-id="0d5be-146">Bu dizide, komite olmayan ve altı negatif olan 12 yanıt vardır.</span><span class="sxs-lookup"><span data-stu-id="0d5be-146">This array has 12 answers that are affirmative, six that are non-committal, and six that are negative.</span></span> <span data-ttu-id="0d5be-147">Sonra, diziden rastgele bir yanıt oluşturmak ve bu yanıtı göstermek için aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="0d5be-147">Next, add the following code to generate and display a random answer from the array:</span></span>

:::code language="csharp" source="snippets/top-level-statements/ProgramSnippets.cs" ID="GenerateAnswer":::

<span data-ttu-id="0d5be-148">Sonuçları görmek için uygulamayı yeniden çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0d5be-148">You can run the application again to see the results.</span></span> <span data-ttu-id="0d5be-149">Aşağıdaki çıktıya benzer bir şey görmeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="0d5be-149">You should see something like the following output:</span></span>

```dotnetcli
dotnet run -- Should I use top level statements in all my programs?

Should I use top level statements in all my programs?
Better not tell you now.
```

<span data-ttu-id="0d5be-150">Bu kod soruları yanıtlar, ancak bir özellik ekleyelim.</span><span class="sxs-lookup"><span data-stu-id="0d5be-150">This code answers the questions, but let's add one more feature.</span></span> <span data-ttu-id="0d5be-151">Soru uygulamanızı, yanıt hakkında düşünmeyi benzetmek istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="0d5be-151">You'd like your question app to simulate thinking about the answer.</span></span> <span data-ttu-id="0d5be-152">Bunu, ASCII animasyonunu bir bit ekleyerek ve çalışırken duraklatarak yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0d5be-152">You can do that by adding a bit of ASCII animation, and pausing while working.</span></span>  <span data-ttu-id="0d5be-153">Soruyu yankılayan satırdan sonra aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="0d5be-153">Add the following code after the line that echoes the question:</span></span>

:::code language="csharp" source="snippets/top-level-statements/UtilitiesPassOne.cs" ID="AnimationFirstPass":::

<span data-ttu-id="0d5be-154">Ayrıca, `using` kaynak dosyanın en üstüne bir ifade eklemeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="0d5be-154">You'll also need to add a `using` statement to the top of the source file:</span></span>

```csharp
using System.Threading.Tasks;
```

<span data-ttu-id="0d5be-155">`using`Deyimler, dosyadaki diğer deyimlerden önce olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0d5be-155">The `using` statements must be before any other statements in the file.</span></span> <span data-ttu-id="0d5be-156">Aksi halde derleyici hatası olur.</span><span class="sxs-lookup"><span data-stu-id="0d5be-156">Otherwise, it's a compiler error.</span></span> <span data-ttu-id="0d5be-157">Programı yeniden çalıştırabilir ve animasyonu görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0d5be-157">You can run the program again and see the animation.</span></span> <span data-ttu-id="0d5be-158">Bu, daha iyi bir deneyim sunar.</span><span class="sxs-lookup"><span data-stu-id="0d5be-158">That makes a better experience.</span></span> <span data-ttu-id="0d5be-159">Zevkinizi eşleştirmeye yönelik gecikmenin uzunluğu ile denemeler yapın.</span><span class="sxs-lookup"><span data-stu-id="0d5be-159">Experiment with the length of the delay to match your taste.</span></span>

<span data-ttu-id="0d5be-160">Yukarıdaki kod, boşlukla ayrılmış bir dönen çizgiler kümesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0d5be-160">The preceding code creates a set of spinning lines separated by a space.</span></span> <span data-ttu-id="0d5be-161">`await`Anahtar sözcüğü eklemek derleyiciye, değiştiriciye sahip bir yöntem olarak program giriş noktasını oluşturmasını söyler `async` ve bir döndürür <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="0d5be-161">Adding the `await` keyword instructs the compiler to generate the program entry point as a method that has the `async` modifier, and returns a <xref:System.Threading.Tasks.Task?displayProperty=nameWithType>.</span></span> <span data-ttu-id="0d5be-162">Bu program bir değer döndürmüyor, bu nedenle program giriş noktası bir döndürür `Task` .</span><span class="sxs-lookup"><span data-stu-id="0d5be-162">This program does not return a value, so the program entry point returns a `Task`.</span></span> <span data-ttu-id="0d5be-163">Programınız bir tamsayı değeri döndürürse, en üst düzey deyimlerinizin sonuna bir return deyimi eklersiniz.</span><span class="sxs-lookup"><span data-stu-id="0d5be-163">If your program returns an integer value, you would add a return statement to the end of your top-level statements.</span></span> <span data-ttu-id="0d5be-164">Bu return ifadesinde döndürülecek tamsayı değeri belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="0d5be-164">That return statement would specify the integer value to return.</span></span> <span data-ttu-id="0d5be-165">En üst düzey deyimlerinizin bir ifadesi varsa `await` , dönüş türü olur <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="0d5be-165">If your top-level statements include an `await` expression, the return type becomes <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType>.</span></span>

## <a name="refactoring-for-the-future"></a><span data-ttu-id="0d5be-166">Geleceğe yönelik yeniden düzenleme</span><span class="sxs-lookup"><span data-stu-id="0d5be-166">Refactoring for the future</span></span>

<span data-ttu-id="0d5be-167">Programınız aşağıdaki kod gibi görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="0d5be-167">Your program should look like the following code:</span></span>

```csharp
using System;
using System.Threading.Tasks;

Console.WriteLine();
foreach(var s in args)
{
    Console.Write(s);
    Console.Write(' ');
}
Console.WriteLine();

for (int i = 0; i < 20; i++)
{
    Console.Write("| -");
    await Task.Delay(50);
    Console.Write("\b\b\b");
    Console.Write("/ \\");
    await Task.Delay(50);
    Console.Write("\b\b\b");
    Console.Write("- |");
    await Task.Delay(50);
    Console.Write("\b\b\b");
    Console.Write("\\ /");
    await Task.Delay(50);
    Console.Write("\b\b\b");
}
Console.WriteLine();

string[] answers =
{
    "It is certain.",       "Reply hazy, try again.",     "Don’t count on it.",
    "It is decidedly so.",  "Ask again later.",           "My reply is no.",
    "Without a doubt.",     "Better not tell you now.",   "My sources say no.",
    "Yes – definitely.",    "Cannot predict now.",        "Outlook not so good.",
    "You may rely on it.",  "Concentrate and ask again.", "Very doubtful.",
    "As I see it, yes.",
    "Most likely.",
    "Outlook good.",
    "Yes.",
    "Signs point to yes.",
};

var index = new Random().Next(answers.Length - 1);
Console.WriteLine(answers[index]);
```

<span data-ttu-id="0d5be-168">Yukarıdaki kod mantıklı.</span><span class="sxs-lookup"><span data-stu-id="0d5be-168">The preceding code is reasonable.</span></span> <span data-ttu-id="0d5be-169">İşe yarar.</span><span class="sxs-lookup"><span data-stu-id="0d5be-169">It works.</span></span> <span data-ttu-id="0d5be-170">Ancak yeniden kullanılabilir değil.</span><span class="sxs-lookup"><span data-stu-id="0d5be-170">But it isn't reusable.</span></span> <span data-ttu-id="0d5be-171">Uygulamanın çalışır durumda olduğuna göre, yeniden kullanılabilir parçalar çekmeniz zaman alabilir.</span><span class="sxs-lookup"><span data-stu-id="0d5be-171">Now that you have the application working, it's time to pull out reusable parts.</span></span>

<span data-ttu-id="0d5be-172">Bir aday, bekleyen animasyonu görüntüleyen koddur.</span><span class="sxs-lookup"><span data-stu-id="0d5be-172">One candidate is the code that displays the waiting animation.</span></span> <span data-ttu-id="0d5be-173">Bu kod parçacığı bir yöntem haline gelebilir:</span><span class="sxs-lookup"><span data-stu-id="0d5be-173">That snippet can become a method:</span></span>

<span data-ttu-id="0d5be-174">Dosyanızda yerel bir işlev oluşturarak başlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0d5be-174">You can start by creating a local function in your file.</span></span> <span data-ttu-id="0d5be-175">Geçerli animasyonu şu kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="0d5be-175">Replace the current animation with the following code:</span></span>

```csharp
await ShowConsoleAnimation();

static async Task ShowConsoleAnimation()
{
    for (int i = 0; i < 20; i++)
    {
        Console.Write("| -");
        await Task.Delay(50);
        Console.Write("\b\b\b");
        Console.Write("/ \\");
        await Task.Delay(50);
        Console.Write("\b\b\b");
        Console.Write("- |");
        await Task.Delay(50);
        Console.Write("\b\b\b");
        Console.Write("\\ /");
        await Task.Delay(50);
        Console.Write("\b\b\b");
    }
    Console.WriteLine();
}
```

<span data-ttu-id="0d5be-176">Yukarıdaki kod, ana yönteminizin içinde yerel bir işlev oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0d5be-176">The preceding code creates a local function inside your main method.</span></span> <span data-ttu-id="0d5be-177">Yine de yeniden kullanılabilir değildir.</span><span class="sxs-lookup"><span data-stu-id="0d5be-177">That's still not reusable.</span></span> <span data-ttu-id="0d5be-178">Bu nedenle, kodu bir sınıfa ayıklayın.</span><span class="sxs-lookup"><span data-stu-id="0d5be-178">So, extract that code into a class.</span></span> <span data-ttu-id="0d5be-179">*Utilities.cs* adlı yeni bir dosya oluşturun ve aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="0d5be-179">Create a new file named *utilities.cs* and add the following code:</span></span>

:::code language="csharp" source="snippets/top-level-statements/UtilitiesPassOne.cs" ID="SnippetUtilities":::

<span data-ttu-id="0d5be-180">En üst düzey deyimler yalnızca bir dosya içinde olabilir ve bu dosya ad alanları veya türler içeremez.</span><span class="sxs-lookup"><span data-stu-id="0d5be-180">Top-level statements can only be in one file, and that file cannot contain namespaces or types.</span></span>

<span data-ttu-id="0d5be-181">Son olarak, bir yinelemeyi kaldırmak için animasyon kodunu temizleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="0d5be-181">Finally, you can clean the animation code to remove some duplication:</span></span>

:::code language="csharp" source="snippets/top-level-statements/Utilities.cs" ID="Animation":::

<span data-ttu-id="0d5be-182">Artık bir uygulamanız vardır ve daha sonra kullanmak üzere yeniden kullanılabilir parçalar yeniden düzenlenmiş.</span><span class="sxs-lookup"><span data-stu-id="0d5be-182">Now you have a complete application, and you've refactored the reusable parts for later use.</span></span> <span data-ttu-id="0d5be-183">Ana programın tamamlanmış sürümünde aşağıda gösterildiği gibi en üst düzey deyimlerden yeni yardımcı program yöntemini çağırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="0d5be-183">You can call the new utility method from your top-level statements, as shown below in the finished version of the main program:</span></span>

:::code language="csharp" source="snippets/top-level-statements/Program.cs":::

<span data-ttu-id="0d5be-184">Bu, çağrısını ekler `Utilities.ShowConsoleAnimation` ve ek bir `using` ifade ekler.</span><span class="sxs-lookup"><span data-stu-id="0d5be-184">This adds the call to `Utilities.ShowConsoleAnimation`, and adds an additional `using` statement.</span></span>

## <a name="summary"></a><span data-ttu-id="0d5be-185">Özet</span><span class="sxs-lookup"><span data-stu-id="0d5be-185">Summary</span></span>

<span data-ttu-id="0d5be-186">En üst düzey deyimler, yeni algoritmaları araştırmak için kullanılmak üzere basit programlar oluşturmayı kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="0d5be-186">Top-level statements make it easier to create simple programs for use to explore new algorithms.</span></span> <span data-ttu-id="0d5be-187">Farklı kod parçacıkları deneyerek algoritmalarla denemeler yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0d5be-187">You can experiment with algorithms by trying different snippets of code.</span></span> <span data-ttu-id="0d5be-188">Ne işe yarar olduğunu öğrendikten sonra kodu daha sürdürülebilir olacak şekilde yeniden düzenleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0d5be-188">Once you've learned what works, you can refactor the code to be more maintainable.</span></span>

<span data-ttu-id="0d5be-189">Üst düzey deyimler Konsol uygulamalarını temel alan programları basitleştirir.</span><span class="sxs-lookup"><span data-stu-id="0d5be-189">Top-level statements simplify programs that are based on console applications.</span></span> <span data-ttu-id="0d5be-190">Bunlar Azure işlevleri, GitHub eylemleri ve diğer küçük yardımcı programları içerir.</span><span class="sxs-lookup"><span data-stu-id="0d5be-190">These include Azure functions, GitHub actions, and other small utilities.</span></span>
