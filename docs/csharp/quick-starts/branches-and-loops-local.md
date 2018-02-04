---
title: "Dal ve döngüler Öğreticisi - C# yerel quickstarts"
description: "Bu hızlı başlangıcı dallar ve döngüler hakkında koşullu dal ve art arda deyimlerini yürütmek için döngüler destekler dili sözdizimi keşfetmek için C# kod yazın."
author: billwagner
ms.author: wiwagn
ms.date: 10/31/2017
ms.topic: get-started-article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.custom: mvc
ms.openlocfilehash: 7d69b2b9bb02e2999bcd785da653bd4a13ed947c
ms.sourcegitcommit: d2da0142247ef42a219a5d2907f153e62dc6ea0d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/01/2018
---
# <a name="branches-and-loops"></a><span data-ttu-id="25e96-103">Dal ve döngüler</span><span class="sxs-lookup"><span data-stu-id="25e96-103">Branches and loops</span></span>

<span data-ttu-id="25e96-104">Bu hızlı başlangıç değişkenlerini inceler ve bu değişkenleri esas alarak yürütme yolu değiştirir kodunun nasıl yazılacağını öğretir.</span><span class="sxs-lookup"><span data-stu-id="25e96-104">This quickstart teaches you how to write code that examines variables and changes the execution path based on those variables.</span></span> <span data-ttu-id="25e96-105">C# kod yazma ve derleme ve onu çalıştırma sonuçları görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="25e96-105">You write C# code and see the results of compiling and running it.</span></span> <span data-ttu-id="25e96-106">Hızlı Başlangıç dallanma ve döngü yapıları C# keşfedin dersleri bir dizi içerir.</span><span class="sxs-lookup"><span data-stu-id="25e96-106">The quickstart contains a series of lessons that explore branching and looping constructs in C#.</span></span> <span data-ttu-id="25e96-107">Bu derslerin C# dil temelleri öğretir.</span><span class="sxs-lookup"><span data-stu-id="25e96-107">These lessons teach you the fundamentals of the C# language.</span></span>

<span data-ttu-id="25e96-108">Bu hızlı başlangıç geliştirme için kullanabileceğiniz bir makine olmasını bekler.</span><span class="sxs-lookup"><span data-stu-id="25e96-108">This quickstart expects you to have a machine you can use for development.</span></span> <span data-ttu-id="25e96-109">.NET konu [Get Started 10 dakika içinde](https://www.microsoft.com/net/core) Mac, PC ya da Linux yerel geliştirme ortamınızı ayarlamak için yönergeler içerir.</span><span class="sxs-lookup"><span data-stu-id="25e96-109">The .NET topic [Get Started in 10 minutes](https://www.microsoft.com/net/core) has instructions for setting up your local development environment on Mac, PC or Linux.</span></span> <span data-ttu-id="25e96-110">Hızlı bir genel bakış kullandığınız komutların bulunduğu [yerel quickstarts giriş](local-environment.md) daha fazla bilgi için bağlantılar ile birlikte.</span><span class="sxs-lookup"><span data-stu-id="25e96-110">A quick overview of the commands you'll use is in the [introduction to the local quickstarts](local-environment.md) with links to more details.</span></span>

## <a name="make-decisions-using-the-if-statement"></a><span data-ttu-id="25e96-111">Kullanarak kararlar `if` deyimi</span><span class="sxs-lookup"><span data-stu-id="25e96-111">Make decisions using the `if` statement</span></span>

<span data-ttu-id="25e96-112">Adlı bir dizin oluşturun **dalları Hızlı Başlangıç**.</span><span class="sxs-lookup"><span data-stu-id="25e96-112">Create a directory named **branches-quickstart**.</span></span> <span data-ttu-id="25e96-113">Geçerli dizin çalıştırma yapıp `dotnet new console -n BranchesAndLoops -o .`.</span><span class="sxs-lookup"><span data-stu-id="25e96-113">Make that the current directory and run `dotnet new console -n BranchesAndLoops -o .`.</span></span> <span data-ttu-id="25e96-114">Bu komut, geçerli dizinde yeni bir .NET Core konsol uygulaması oluşturur.</span><span class="sxs-lookup"><span data-stu-id="25e96-114">This command creates a new .NET Core console application in the current directory.</span></span>

<span data-ttu-id="25e96-115">Açık **Program.cs** sık kullanılan Düzenleyicisi ve Değiştir satır `Console.Writeline("Hello World!");` aşağıdaki kod ile:</span><span class="sxs-lookup"><span data-stu-id="25e96-115">Open **Program.cs** in your favorite editor, and replace the line `Console.Writeline("Hello World!");` with the following code:</span></span>

```csharp
int a = 5;
int b = 6;
if (a + b > 10)
    Console.WriteLine("The answer is greater than 10.");
```

<span data-ttu-id="25e96-116">Bu kod yazarak deneyin `dotnet run` içinde, konsol penceresi.</span><span class="sxs-lookup"><span data-stu-id="25e96-116">Try this code by typing `dotnet run` in the your console window.</span></span> <span data-ttu-id="25e96-117">"Yanıt 10'dan daha büyük." iletisini görmeniz gerekir</span><span class="sxs-lookup"><span data-stu-id="25e96-117">You should see the message "The answer is greater than 10."</span></span> <span data-ttu-id="25e96-118">konsolunuza yazdırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="25e96-118">printed to your console.</span></span>

<span data-ttu-id="25e96-119">Bildirimi değiştirme `b` toplam 10'dan az olmasını sağlayın:</span><span class="sxs-lookup"><span data-stu-id="25e96-119">Modify the declaration of `b` so that the sum is less than 10:</span></span> 

```csharp
int b = 3;
```

<span data-ttu-id="25e96-120">Tür `dotnet run` yeniden.</span><span class="sxs-lookup"><span data-stu-id="25e96-120">Type `dotnet run` again.</span></span> <span data-ttu-id="25e96-121">Yanıt 10'dan az olduğundan, hiçbir şey yazdırılır.</span><span class="sxs-lookup"><span data-stu-id="25e96-121">Because the answer is less than 10, nothing is printed.</span></span> <span data-ttu-id="25e96-122">**Koşulu** olduğunuz test değer false.</span><span class="sxs-lookup"><span data-stu-id="25e96-122">The **condition** you're testing is false.</span></span> <span data-ttu-id="25e96-123">Olası dallarını birini yalnızca yazdıktan çünkü yürütmek için herhangi bir kod olmayan bir `if` deyimi: true dal.</span><span class="sxs-lookup"><span data-stu-id="25e96-123">You don't have any code to execute because you've only written one of the possible branches for an `if` statement: the true branch.</span></span>

> [!TIP]
> <span data-ttu-id="25e96-124">C# (veya herhangi bir programlama dili) keşfetmenizde kodu yazarken hataları hale getireceğiz.</span><span class="sxs-lookup"><span data-stu-id="25e96-124">As you explore C# (or any programming language), you'll make mistakes when you write code.</span></span> <span data-ttu-id="25e96-125">Derleyici bulun ve hataları raporlar.</span><span class="sxs-lookup"><span data-stu-id="25e96-125">The compiler will find and report the errors.</span></span> <span data-ttu-id="25e96-126">Yakından hata çıkış ve hata oluşturulan kod bakın.</span><span class="sxs-lookup"><span data-stu-id="25e96-126">Look closely at the error output and the code that generated the error.</span></span> <span data-ttu-id="25e96-127">Compler hata genellikle sorun bulmanıza yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="25e96-127">The compler error can usually help you find the problem.</span></span>

<span data-ttu-id="25e96-128">Bu ilk örnek gücünü gösterir `if` ve Boolean türleri.</span><span class="sxs-lookup"><span data-stu-id="25e96-128">This first sample shows the power of `if` and Boolean types.</span></span> <span data-ttu-id="25e96-129">A *Boolean* iki değerlerden birine sahip bir değişken: `true` veya `false`.</span><span class="sxs-lookup"><span data-stu-id="25e96-129">A *Boolean* is a variable that can have one of two values: `true` or `false`.</span></span> <span data-ttu-id="25e96-130">C# özel türünü tanımlayan `bool` Boolean değişkenleri için.</span><span class="sxs-lookup"><span data-stu-id="25e96-130">C# defines a special type, `bool` for Boolean variables.</span></span> <span data-ttu-id="25e96-131">`if` Deyimi denetler değerini bir `bool`.</span><span class="sxs-lookup"><span data-stu-id="25e96-131">The `if` statement checks the value of a `bool`.</span></span> <span data-ttu-id="25e96-132">Değer olduğunda `true`, aşağıdaki deyim `if` yürütür.</span><span class="sxs-lookup"><span data-stu-id="25e96-132">When the value is `true`, the statement following the `if` executes.</span></span> <span data-ttu-id="25e96-133">Aksi takdirde atlanır.</span><span class="sxs-lookup"><span data-stu-id="25e96-133">Otherwise, it is skipped.</span></span>

<span data-ttu-id="25e96-134">Bu işlem koşullar denetleniyor ve bu koşullara göre deyimleri yürütme çok güçlü bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="25e96-134">This process of checking conditions and executing statements based on those conditions is very powerful.</span></span>

## <a name="make-if-and-else-work-together"></a><span data-ttu-id="25e96-135">Olun ve başka birlikte çalışma</span><span class="sxs-lookup"><span data-stu-id="25e96-135">Make if and else work together</span></span>

<span data-ttu-id="25e96-136">Her iki true ve false dallarda farklı kod yürütmek için oluşturduğunuz bir `else` koşul yanlış olduğunda, yürüten dal.</span><span class="sxs-lookup"><span data-stu-id="25e96-136">To execute different code in both the true and false branches, you create an `else` branch that executes when the condition is false.</span></span> <span data-ttu-id="25e96-137">Bu deneyin.</span><span class="sxs-lookup"><span data-stu-id="25e96-137">Try this.</span></span> <span data-ttu-id="25e96-138">Aşağıdaki kodda son iki satırı ekleyin, `Main` yöntemi (zaten sahip olmanız gereken ilk dört):</span><span class="sxs-lookup"><span data-stu-id="25e96-138">Add the last two lines in the code below to your `Main` method (you should already have the first four):</span></span>

```csharp
int a = 5;
int b = 3;
if (a + b > 10)
    Console.WriteLine("The answer is greater than 10");
else
    Console.WriteLine("The answer is not greater than 10");
```

<span data-ttu-id="25e96-139">Deyimi aşağıdaki `else` anahtar sözcüğü yürütür yalnızca sınanan koşul olduğunda `false`.</span><span class="sxs-lookup"><span data-stu-id="25e96-139">The statement following the `else` keyword executes only when the condition being tested is `false`.</span></span> <span data-ttu-id="25e96-140">Birleştirme `if` ve `else` Boolean ile koşullar sağlar hem işlemek için ihtiyacınız olan tüm güç bir `true` ve `false` koşulu.</span><span class="sxs-lookup"><span data-stu-id="25e96-140">Combining `if` and `else` with Boolean conditions provides all the power you need to handle both a `true` and a `false` condition.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="25e96-141">Girinti altında `if` ve `else` deyimleri İnsan okuyucular için değil.</span><span class="sxs-lookup"><span data-stu-id="25e96-141">The indentation under the `if` and `else` statements is for human readers.</span></span>
> <span data-ttu-id="25e96-142">C# dili girinti veya boşluk önemli olarak kabul etmez.</span><span class="sxs-lookup"><span data-stu-id="25e96-142">The C# language doesn't treat indentation or whitespace as significant.</span></span> <span data-ttu-id="25e96-143">Deyimi aşağıdaki `if` veya `else` anahtar sözcüğü koşula göre yürütülür.</span><span class="sxs-lookup"><span data-stu-id="25e96-143">The statement following the `if` or `else` keyword will be executed based on the condition.</span></span> <span data-ttu-id="25e96-144">Bu hızlı başlangıç tüm örneklerinde satırlarını deyimleri denetim akışı üzerinde göre Girintile yaygın bir uygulama izleyin.</span><span class="sxs-lookup"><span data-stu-id="25e96-144">All the samples in this quickstart follow a common practice to indent lines based on the control flow of statements.</span></span>

<span data-ttu-id="25e96-145">Girinti önemli olmadığı için kullanmanıza gerek `{` ve `}` koşullu yürütür blok parçası olarak birden fazla deyim istediğinizde belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="25e96-145">Because indentation is not significant, you need to use `{` and `}` to indicate when you want more than one statement to be part of the block that executes conditionally.</span></span> <span data-ttu-id="25e96-146">C# programcıları genellikle kullanın Bu küme ayraçları tüm `if` ve `else` yan tümceleri.</span><span class="sxs-lookup"><span data-stu-id="25e96-146">C# programmers typically use those braces on all `if` and `else` clauses.</span></span> <span data-ttu-id="25e96-147">Aşağıdaki örnek, yeni oluşturduğunuz bir ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="25e96-147">The following example is the same as the one you just created.</span></span> <span data-ttu-id="25e96-148">Aşağıdaki kod eşleştirmek için yukarıdaki kodunuzu değiştirin:</span><span class="sxs-lookup"><span data-stu-id="25e96-148">Modify your code above to match the following code:</span></span>

```csharp
int a = 5;
int b = 3;
if (a + b > 10)
{
    Console.WriteLine("The answer is greater than 10");
}
else
{
    Console.WriteLine("The answer is not greater than 10");
}
```

> [!TIP]
> <span data-ttu-id="25e96-149">Bu hızlı başlangıç kullanılmadıkları tüm kod örnekleri aşağıdaki küme ayraçları dahil kabul yöntemler.</span><span class="sxs-lookup"><span data-stu-id="25e96-149">Through the rest of this quickstart, the code samples all include the braces, following accepted practices.</span></span>

<span data-ttu-id="25e96-150">Daha karmaşık koşullar test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="25e96-150">You can test more complicated conditions.</span></span> <span data-ttu-id="25e96-151">Aşağıdaki kodu ekleyin, `Main` yöntemi, o ana kadarki yazılan koddan sonra:</span><span class="sxs-lookup"><span data-stu-id="25e96-151">Add the following code in your `Main` method after the code you've written so far:</span></span>

```csharp
    int c = 4;
    if ((a + b + c > 10) && (a > b))
{
    Console.WriteLine("The answer is greater than 10");
    Console.WriteLine("And the first number is greater than the second");
}
else
{
    Console.WriteLine("The answer is not greater than 10");
    Console.WriteLine("Or the first number is not greater than the second");
}
```

<span data-ttu-id="25e96-152">`&&` Temsil eder "ve".</span><span class="sxs-lookup"><span data-stu-id="25e96-152">The `&&` represents "and".</span></span> <span data-ttu-id="25e96-153">Bu koşulların her ikisi de true dalında deyimi yürütmek için doğru olması gerektiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="25e96-153">It means both conditions must be true to execute the statement in the true branch.</span></span>  <span data-ttu-id="25e96-154">Bunları içine sağlanan bu Ayrıca, her koşullu dal birden fazla deyime olabilir örnekler `{` ve `}`.</span><span class="sxs-lookup"><span data-stu-id="25e96-154">These examples also show that you can have multiple statements in each conditional branch, provided you enclose them in `{` and `}`.</span></span>

<span data-ttu-id="25e96-155">Aynı zamanda `||` temsil etmek için "veya".</span><span class="sxs-lookup"><span data-stu-id="25e96-155">You can also use  `||` to represent "or".</span></span> <span data-ttu-id="25e96-156">Şu ana kadar yazdıklarınızı sonra aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="25e96-156">Add the following code after what you've written so far:</span></span>

```csharp
if ((a + b + c > 10) || (a > b))
{
    Console.WriteLine("The answer is greater than 10");
    Console.WriteLine("Or the first number is greater than the second");
}
else
{
    Console.WriteLine("The answer is not greater than 10");
    Console.WriteLine("And the first number is not greater than the second");
}
```

<span data-ttu-id="25e96-157">İlk adım tamamladınız.</span><span class="sxs-lookup"><span data-stu-id="25e96-157">You've finished the first step.</span></span> <span data-ttu-id="25e96-158">Şimdi, sonraki bölüme başlamadan önce geçerli kod ayrı bir yöntem taşıyın.</span><span class="sxs-lookup"><span data-stu-id="25e96-158">Before you start the next section, let's move the current code into a separate method.</span></span> <span data-ttu-id="25e96-159">Bu, yeni bir örnek ile çalışmaya başlamak kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="25e96-159">That makes it easier to start working with a new example.</span></span> <span data-ttu-id="25e96-160">Yeniden Adlandır, `Main` yönteme `ExploreIf` ve yeni bir yazma `Main` çağıran yöntemi `ExploreIf`.</span><span class="sxs-lookup"><span data-stu-id="25e96-160">Rename your `Main` method to `ExploreIf` and write a new `Main` method that calls `ExploreIf`.</span></span> <span data-ttu-id="25e96-161">İşiniz bittiğinde, kodunuzu aşağıdaki gibi görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="25e96-161">When you have finished, your code should look like this:</span></span>

```csharp
using System;

namespace BranchesAndLoops
{
    class Program
    {
        static void ExploreIf()
        {
            int a = 5;
            int b = 3;
            if (a + b > 10)
            {
                Console.WriteLine("The answer is greater than 10");
            }
            else
            {
                Console.WriteLine("The answer is not greater than 10");
            }

            if ((a + b + c > 10) && (a > b))
            {
                Console.WriteLine("The answer is greater than 10");
                Console.WriteLine("And the first number is greater than the second");
            }
            else
            {
                Console.WriteLine("The answer is not greater than 10");
                Console.WriteLine("Or the first number is not greater than the second");
            }

            if ((a + b + c > 10) || (a > b))
            {
                Console.WriteLine("The answer is greater than 10");
                Console.WriteLine("Or the first number is greater than the second");
            }
            else
            {
                Console.WriteLine("The answer is not greater than 10");
                Console.WriteLine("And the first number is not greater than the second");
            }            
        }

        static void Main(string[] args)
        {
            ExploreIf();
        }
    }
}
```

<span data-ttu-id="25e96-162">Açıklama çağrısı çıkışı `ExploreIf()`.</span><span class="sxs-lookup"><span data-stu-id="25e96-162">Comment out the call to `ExploreIf()`.</span></span> <span data-ttu-id="25e96-163">Bu bölümde çalışırken daha az kalabalık çıkış yapar:</span><span class="sxs-lookup"><span data-stu-id="25e96-163">It will make the output less cluttered as you work in this section:</span></span>

```csharp
//ExploreIf();
```

<span data-ttu-id="25e96-164">`//` Başlayan bir **açıklama** C#.</span><span class="sxs-lookup"><span data-stu-id="25e96-164">The `//` starts a **comment** in C#.</span></span> <span data-ttu-id="25e96-165">Kaynak kodunuz tutmak ancak kodu olarak yürütmeme istediğiniz herhangi bir metin açıklamalardır.</span><span class="sxs-lookup"><span data-stu-id="25e96-165">Comments are any text you want to keep in your source code but not execute as code.</span></span> <span data-ttu-id="25e96-166">Derleyici herhangi bir yürütülebilir kod açıklamalardan oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="25e96-166">The compiler does not generate any executable code from comments.</span></span>

## <a name="use-loops-to-repeat-operations"></a><span data-ttu-id="25e96-167">Döngüler işlemleri yinelemek için kullanın</span><span class="sxs-lookup"><span data-stu-id="25e96-167">Use loops to repeat operations</span></span>

<span data-ttu-id="25e96-168">Bu bölümde kullandığınız **döngüler** deyimleri yinelenecek.</span><span class="sxs-lookup"><span data-stu-id="25e96-168">In this section you use **loops** to repeat statements.</span></span> <span data-ttu-id="25e96-169">Bu kodda deneyin, `Main` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="25e96-169">Try this code in your `Main` method:</span></span>

```csharp
int counter = 0;
while (counter < 10)
{
    Console.WriteLine($"Hello World! The counter is {counter}");
    counter++;
}
```

<span data-ttu-id="25e96-170">`while` İfadesi bir koşulu denetler ve ifadesi veya deyimi blok aşağıdaki yürütür `while`.</span><span class="sxs-lookup"><span data-stu-id="25e96-170">The `while` statement checks a condition and executes the statement or statement block following the `while`.</span></span> <span data-ttu-id="25e96-171">Art arda koşul ve koşul yanlış olana kadar bu deyimleri yürütme denetler.</span><span class="sxs-lookup"><span data-stu-id="25e96-171">It repeatedly checks the condition and executing those statements until the condition is false.</span></span>

<span data-ttu-id="25e96-172">Bu örnekte, diğer yeni bir işleç var.</span><span class="sxs-lookup"><span data-stu-id="25e96-172">There's one other new operator in this example.</span></span> <span data-ttu-id="25e96-173">`++` Sonra `counter` değişken **artırma** işleci.</span><span class="sxs-lookup"><span data-stu-id="25e96-173">The `++` after the `counter` variable is the **increment** operator.</span></span> <span data-ttu-id="25e96-174">1 değerine ekler `counter` ve bu değeri depolar `counter` değişkeni.</span><span class="sxs-lookup"><span data-stu-id="25e96-174">It adds 1 to the value of `counter` and stores that value in the `counter` variable.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="25e96-175">Olduğundan emin olun `while` kod yürütmek gibi Döngü koşulu değişiklikleri false.</span><span class="sxs-lookup"><span data-stu-id="25e96-175">Make sure that the `while` loop condition changes to false as you execute the code.</span></span> <span data-ttu-id="25e96-176">Aksi takdirde, oluşturduğunuz bir **sonsuz bir döngü** programınızı hiçbir zaman sona ereceği.</span><span class="sxs-lookup"><span data-stu-id="25e96-176">Otherwise, you create an **infinite loop** where your program never ends.</span></span> <span data-ttu-id="25e96-177">Değil gösterilmiştir Bu örnekte, kullanarak çıkmak için program zorlamak olduğundan **CTRL-C** veya diğer anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="25e96-177">That is not demonstrated in this sample, because you have to force your program to quit using **CTRL-C** or other means.</span></span>

<span data-ttu-id="25e96-178">`while` Döngü kod aşağıdaki yürütmeden önce koşulu sınar `while`.</span><span class="sxs-lookup"><span data-stu-id="25e96-178">The `while` loop tests the condition before executing the code following the `while`.</span></span> <span data-ttu-id="25e96-179">`do` ... `while` döngü kodu ilk yürütür ve koşul denetler.</span><span class="sxs-lookup"><span data-stu-id="25e96-179">The `do` ... `while` loop executes the code first, and then checks the condition.</span></span> <span data-ttu-id="25e96-180">Aşağıdaki kodda döngü gösterilmese yapın:</span><span class="sxs-lookup"><span data-stu-id="25e96-180">The do while loop is shown in the following code:</span></span>

```csharp
counter = 0;
do
{
    Console.WriteLine($"Hello World! The counter is {counter}");
    counter++;
} while (counter < 10);
```

<span data-ttu-id="25e96-181">Bu `do` döngü ve önceki `while` döngü, aynı çıktı üretir.</span><span class="sxs-lookup"><span data-stu-id="25e96-181">This `do` loop and the earlier `while` loop produce the same output.</span></span>

## <a name="work-with-the-for-loop"></a><span data-ttu-id="25e96-182">Çalışmak döngü için</span><span class="sxs-lookup"><span data-stu-id="25e96-182">Work with the for loop</span></span>

<span data-ttu-id="25e96-183">**İçin** döngü yaygın olarak kullanılan C# '.</span><span class="sxs-lookup"><span data-stu-id="25e96-183">The **for** loop is commonly used in C#.</span></span> <span data-ttu-id="25e96-184">Bu kod, Main() yönteminin deneyin:</span><span class="sxs-lookup"><span data-stu-id="25e96-184">Try this code in your Main() method:</span></span>

```csharp
for(int index = 0; index < 10; index++)
{
    Console.WriteLine($"Hello World! The index is {index}");
} 
```

<span data-ttu-id="25e96-185">Aynı iş olarak bunu yapar `while` döngü ve `do` zaten kullandığınız döngü.</span><span class="sxs-lookup"><span data-stu-id="25e96-185">This does the same work as the `while` loop and the `do` loop you've already used.</span></span> <span data-ttu-id="25e96-186">`for` Deyimi nasıl çalıştığını denetleyen üç bölümden sahiptir.</span><span class="sxs-lookup"><span data-stu-id="25e96-186">The `for` statement has three parts that control how it works.</span></span>

<span data-ttu-id="25e96-187">İlk bölümüdür **Başlatıcısı için**: `for index = 0;` bildiren `index` döngü değişkendir ve ilk değerini ayarlar `0`.</span><span class="sxs-lookup"><span data-stu-id="25e96-187">The first part is the **for initializer**: `for index = 0;` declares that `index` is the loop variable, and sets its initial value to `0`.</span></span>

<span data-ttu-id="25e96-188">Orta parçasıdır **koşul için**: `index < 10` bildirir bu `for` sayacın değeri 10'dan az olduğu sürece yürütme döngü devam eder.</span><span class="sxs-lookup"><span data-stu-id="25e96-188">The middle part is the **for condition**: `index < 10` declares that this `for` loop continues to execute as long as the value of counter is less than 10.</span></span>

<span data-ttu-id="25e96-189">Son bölümüdür **yineleyici için**: `index++` blok aşağıdaki yürüttükten sonra Döngü değişkeninin değiştirme belirtir `for` deyimi.</span><span class="sxs-lookup"><span data-stu-id="25e96-189">The final part is the **for iterator**: `index++` specifies how to modify the loop variable after executing the block following the `for` statement.</span></span> <span data-ttu-id="25e96-190">Burada, belirtir `index` bloğu yürütür her zaman 1 azaltılır.</span><span class="sxs-lookup"><span data-stu-id="25e96-190">Here, it specifies that `index` should be incremented by 1 each time the block executes.</span></span>

<span data-ttu-id="25e96-191">Bu kendinizle deneyin.</span><span class="sxs-lookup"><span data-stu-id="25e96-191">Experiment with these yourself.</span></span> <span data-ttu-id="25e96-192">Her birini deneyin:</span><span class="sxs-lookup"><span data-stu-id="25e96-192">Try each of the following:</span></span>

- <span data-ttu-id="25e96-193">Farklı bir değer başlatmak için Başlatıcı değiştirin.</span><span class="sxs-lookup"><span data-stu-id="25e96-193">Change the initializer to start at a different value.</span></span>
- <span data-ttu-id="25e96-194">Farklı bir değer durdurmak için koşulunu değiştirin.</span><span class="sxs-lookup"><span data-stu-id="25e96-194">Change the condition to stop at a different value.</span></span>

<span data-ttu-id="25e96-195">İşiniz bittiğinde, şimdi taşıma açın yazma bazı kendiniz ne öğrendiğinize kullanmak için kodu.</span><span class="sxs-lookup"><span data-stu-id="25e96-195">When you're done, let's move on to write some code yourself to use what you've learned.</span></span>

## <a name="combine-branches-and-loops"></a><span data-ttu-id="25e96-196">Dal ve döngüler birleştirin</span><span class="sxs-lookup"><span data-stu-id="25e96-196">Combine branches and loops</span></span>

<span data-ttu-id="25e96-197">Gördüğünüz göre `if` deyimi ve C# dil döngü yapıları bkz tüm tamsayılar 1 ila 3 ile tam bölünebilir 20 toplamını bulmak için C# kod yazın.</span><span class="sxs-lookup"><span data-stu-id="25e96-197">Now that you've seen the `if` statement and the looping constructs in the C# language, see if you can write C# code to find the sum of all integers 1 through 20 that are divisible by 3.</span></span>  <span data-ttu-id="25e96-198">Aşağıda, birkaç ipucu verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="25e96-198">Here are a few hints:</span></span>

- <span data-ttu-id="25e96-199">`%` İşleci, bir bölme işlemi geri kalanı verir.</span><span class="sxs-lookup"><span data-stu-id="25e96-199">The `%` operator gives you the remainder of a division operation.</span></span>
- <span data-ttu-id="25e96-200">`if` Deyimi, bir sayı toplamı parçası olup olmayacağını görmek için koşul verir.</span><span class="sxs-lookup"><span data-stu-id="25e96-200">The `if` statement gives you the condition to see if a number should be part of the sum.</span></span>
- <span data-ttu-id="25e96-201">`for` Döngü, 20'den sayılar 1 için bir dizi adımı yineleyin yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="25e96-201">The `for` loop can help you repeat a series of steps for all the numbers 1 through 20.</span></span>

<span data-ttu-id="25e96-202">Kendiniz deneyin.</span><span class="sxs-lookup"><span data-stu-id="25e96-202">Try it yourself.</span></span> <span data-ttu-id="25e96-203">Ardından nasıl yaptığınız denetleyin.</span><span class="sxs-lookup"><span data-stu-id="25e96-203">Then check how you did.</span></span> <span data-ttu-id="25e96-204">63 için bir yanıt almanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="25e96-204">You should get 63 for an answer.</span></span> <span data-ttu-id="25e96-205">Tarafından bir olası yanıt görebilirsiniz [tamamlanan kodu Github'da görüntüleme](https://github.com/dotnet/docs/tree/master/samples/csharp/branches-quickstart/Program.cs#L46-L54).</span><span class="sxs-lookup"><span data-stu-id="25e96-205">You can see one possible answer by [viewing the completed code on GitHub](https://github.com/dotnet/docs/tree/master/samples/csharp/branches-quickstart/Program.cs#L46-L54).</span></span>

<span data-ttu-id="25e96-206">"Dallar ve döngüler" Hızlı Başlangıç tamamladınız.</span><span class="sxs-lookup"><span data-stu-id="25e96-206">You've completed the "branches and loops" quickstart.</span></span>

<span data-ttu-id="25e96-207">İle devam edebilirsiniz [Ara değerli dizeler](interpolated-strings-local.md) kendi geliştirme ortamında hızlı başlangıç.</span><span class="sxs-lookup"><span data-stu-id="25e96-207">You can continue with the [Interpolated strings](interpolated-strings-local.md) quickstart in your own development environment.</span></span>

<span data-ttu-id="25e96-208">Bu konularda bu kavramlar hakkında daha fazla bilgi edinebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="25e96-208">You can learn more about these concepts in these topics:</span></span>

[<span data-ttu-id="25e96-209">Varsa ve else deyimi</span><span class="sxs-lookup"><span data-stu-id="25e96-209">If and else statement</span></span>](../language-reference/keywords/if-else.md)  
[<span data-ttu-id="25e96-210">While deyimi</span><span class="sxs-lookup"><span data-stu-id="25e96-210">While statement</span></span>](../language-reference/keywords/while.md)  
[<span data-ttu-id="25e96-211">Do deyimi</span><span class="sxs-lookup"><span data-stu-id="25e96-211">Do statement</span></span>](../language-reference/keywords/do.md)  
[<span data-ttu-id="25e96-212">For deyimi</span><span class="sxs-lookup"><span data-stu-id="25e96-212">For statement</span></span>](../language-reference/keywords/for.md)  
