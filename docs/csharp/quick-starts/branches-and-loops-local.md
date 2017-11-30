---
title: "Hızlı Başlat - dalları ve lops - C# Kılavuzu"
description: "Bu hızlı başlangıç bölümünde dallar ve döngüler hakkında koşullu dal ve art arda deyimlerini yürütmek için döngüler destekler dili sözdizimi keşfetmek için C# kod yazın."
author: billwagner
ms.author: wiwagn
ms.date: 10/31/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.custom: mvc
ms.openlocfilehash: 4b077a29cf42072a93b054f50a13a4580ad54304
ms.sourcegitcommit: 43c656811dd38a66a6672084c65d10c0cbbf2015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2017
---
# <a name="branches-and-loops"></a><span data-ttu-id="6631b-103">Dal ve döngüler</span><span class="sxs-lookup"><span data-stu-id="6631b-103">Branches and loops</span></span>

<span data-ttu-id="6631b-104">Bu hızlı başlangıç değişkenlerini inceler ve bu değişkenleri esas alarak yürütme yolu değiştirir kodunun nasıl yazılacağını öğretir.</span><span class="sxs-lookup"><span data-stu-id="6631b-104">This quick start teaches you how to write code that examines variables and changes the execution path based on those variables.</span></span> <span data-ttu-id="6631b-105">C# kod yazma ve derleme ve onu çalıştırma sonuçları görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="6631b-105">You write C# code and see the results of compiling and running it.</span></span> <span data-ttu-id="6631b-106">Hızlı Başlangıç dallanma ve döngü yapıları C# keşfedin dersleri bir dizi içerir.</span><span class="sxs-lookup"><span data-stu-id="6631b-106">The quick start contains a series of lessons that explore branching and looping constructs in C#.</span></span> <span data-ttu-id="6631b-107">Bu derslerin C# dil temelleri öğretir.</span><span class="sxs-lookup"><span data-stu-id="6631b-107">These lessons teach you the fundamentals of the C# language.</span></span>

<span data-ttu-id="6631b-108">Bu hızlı başlangıç geliştirme için kullanabileceğiniz bir makine olmasını bekler.</span><span class="sxs-lookup"><span data-stu-id="6631b-108">This quick start expects you to have a machine you can use for development.</span></span> <span data-ttu-id="6631b-109">.NET konu [Get Started 10 dakika içinde](https://www.microsoft.com/net/core) Mac, PC ya da Linux yerel geliştirme ortamınızı ayarlamak için yönergeler içerir.</span><span class="sxs-lookup"><span data-stu-id="6631b-109">The .NET topic [Get Started in 10 minutes](https://www.microsoft.com/net/core) has instructions for setting up your local development environment on Mac, PC or Linux.</span></span>

## <a name="make-decisions-using-the-if-statement"></a><span data-ttu-id="6631b-110">Kullanarak kararlar `if` deyimi</span><span class="sxs-lookup"><span data-stu-id="6631b-110">Make decisions using the `if` statement</span></span>

<span data-ttu-id="6631b-111">Adlı bir dizin oluşturun **dalları Hızlı Başlangıç**.</span><span class="sxs-lookup"><span data-stu-id="6631b-111">Create a directory named **branches-quickstart**.</span></span> <span data-ttu-id="6631b-112">Geçerli dizin çalıştırma yapıp `dotnet new console -n BranchesAndLoops -o .`.</span><span class="sxs-lookup"><span data-stu-id="6631b-112">Make that the current directory and run `dotnet new console -n BranchesAndLoops -o .`.</span></span> <span data-ttu-id="6631b-113">Bu komut, geçerli dizinde yeni bir .NET Core konsol uygulaması oluşturur.</span><span class="sxs-lookup"><span data-stu-id="6631b-113">This command creates a new .NET Core console application in the current directory.</span></span> 

<span data-ttu-id="6631b-114">Açık **Program.cs** sık kullanılan Düzenleyicisi ve Değiştir satır `Console.Writeline("Hello World!");` aşağıdaki kod ile:</span><span class="sxs-lookup"><span data-stu-id="6631b-114">Open **Program.cs** in your favorite editor, and replace the line `Console.Writeline("Hello World!");` with the following code:</span></span>

```csharp
int a = 5;
int b = 6;
if (a + b > 10)
    Console.WriteLine("The answer is greater than 10.");
```

<span data-ttu-id="6631b-115">Bu kod yazarak deneyin `dotnet run` içinde, konsol penceresi.</span><span class="sxs-lookup"><span data-stu-id="6631b-115">Try this code by typing `dotnet run` in the your console window.</span></span> <span data-ttu-id="6631b-116">"Yanıt 10'dan daha büyük." iletisini görmeniz gerekir</span><span class="sxs-lookup"><span data-stu-id="6631b-116">You should see the message "The answer is greater than 10."</span></span> <span data-ttu-id="6631b-117">konsolunuza yazdırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="6631b-117">printed to your console.</span></span>

<span data-ttu-id="6631b-118">Bildirimi değiştirme `b` toplam 10'dan az olmasını sağlayın:</span><span class="sxs-lookup"><span data-stu-id="6631b-118">Modify the declaration of `b` so that the sum is less than 10:</span></span> 

```csharp
int b = 3;
```

<span data-ttu-id="6631b-119">Tür `dotnet run` yeniden.</span><span class="sxs-lookup"><span data-stu-id="6631b-119">Type `dotnet run` again.</span></span> <span data-ttu-id="6631b-120">Yanıt 10'dan az olduğundan, hiçbir şey yazdırılır.</span><span class="sxs-lookup"><span data-stu-id="6631b-120">Because the answer is less than 10, nothing is printed.</span></span> <span data-ttu-id="6631b-121">**Koşulu** olduğunuz test değer false.</span><span class="sxs-lookup"><span data-stu-id="6631b-121">The **condition** you're testing is false.</span></span> <span data-ttu-id="6631b-122">Olası dallarını birini yalnızca yazdıktan çünkü yürütmek için herhangi bir kod olmayan bir `if` deyimi: true dal.</span><span class="sxs-lookup"><span data-stu-id="6631b-122">You don't have any code to execute because you've only written one of the possible branches for an `if` statement: the true branch.</span></span>

> [!TIP]
> <span data-ttu-id="6631b-123">C# (veya herhangi bir programlama dili) keşfetmenizde kodu yazarken hataları hale getireceğiz.</span><span class="sxs-lookup"><span data-stu-id="6631b-123">As you explore C# (or any programming language), you'll make mistakes when you write code.</span></span> <span data-ttu-id="6631b-124">Derleyici bulun ve hataları raporlar.</span><span class="sxs-lookup"><span data-stu-id="6631b-124">The compiler will find and report the errors.</span></span> <span data-ttu-id="6631b-125">Arayın yakından hata çıkış ve hata kodu.</span><span class="sxs-lookup"><span data-stu-id="6631b-125">Look closely the the error output and the code that generated the error.</span></span> <span data-ttu-id="6631b-126">Compler hata genellikle sorun bulmanıza yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="6631b-126">The compler error can usually help you find the problem.</span></span> 

<span data-ttu-id="6631b-127">Bu ilk örnek gücünü gösterir `if` ve Boolean türleri.</span><span class="sxs-lookup"><span data-stu-id="6631b-127">This first sample shows the power of `if` and Boolean types.</span></span> <span data-ttu-id="6631b-128">A *Boolean* iki değerlerden birine sahip bir değişken: `true` veya `false`.</span><span class="sxs-lookup"><span data-stu-id="6631b-128">A *Boolean* is a variable that can have one of two values: `true` or `false`.</span></span> <span data-ttu-id="6631b-129">C# özel türünü tanımlayan `bool` Boolean değişkenleri için.</span><span class="sxs-lookup"><span data-stu-id="6631b-129">C# defines a special type, `bool` for Boolean variables.</span></span> <span data-ttu-id="6631b-130">`if` Deyimi denetler değerini bir `bool`.</span><span class="sxs-lookup"><span data-stu-id="6631b-130">The `if` statement checks the value of a `bool`.</span></span> <span data-ttu-id="6631b-131">Değer olduğunda `true`, aşağıdaki deyim `if` yürütür.</span><span class="sxs-lookup"><span data-stu-id="6631b-131">When the value is `true`, the statement following the `if` executes.</span></span> <span data-ttu-id="6631b-132">Aksi takdirde atlanır.</span><span class="sxs-lookup"><span data-stu-id="6631b-132">Otherwise, it is skipped.</span></span> 

<span data-ttu-id="6631b-133">Bu işlem koşullar denetleniyor ve bu koşullara göre deyimleri yürütme çok güçlü bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="6631b-133">This process of checking conditions and executing statements based on those conditions is very powerful.</span></span>


## <a name="make-if-and-else-work-together"></a><span data-ttu-id="6631b-134">Olun ve başka birlikte çalışma</span><span class="sxs-lookup"><span data-stu-id="6631b-134">Make if and else work together</span></span>

<span data-ttu-id="6631b-135">Her iki true ve false dallarda farklı kod yürütmek için oluşturduğunuz bir `else` koşul yanlış olduğunda, yürüten dal.</span><span class="sxs-lookup"><span data-stu-id="6631b-135">To execute different code in both the true and false branches, you create an `else` branch that executes when the condition is false.</span></span> <span data-ttu-id="6631b-136">Bu deneyin.</span><span class="sxs-lookup"><span data-stu-id="6631b-136">Try this.</span></span> <span data-ttu-id="6631b-137">Aşağıdaki kodda son iki satırı ekleyin, `Main` yöntemi (zaten sahip olmanız gereken ilk dört):</span><span class="sxs-lookup"><span data-stu-id="6631b-137">Add the last two lines in the code below to your `Main` method (you should already have the first four):</span></span>

```csharp
int a = 5;
int b = 3;
if (a + b > 10)
    Console.WriteLine("The answer is greater than 10");
else
    Console.WriteLine("The answer is not greater than 10");
```

<span data-ttu-id="6631b-138">Deyimi aşağıdaki `else` anahtar sözcüğü yürütür yalnızca sınanan koşul olduğunda `false`.</span><span class="sxs-lookup"><span data-stu-id="6631b-138">The statement following the `else` keyword executes only when the condition being tested is `false`.</span></span> <span data-ttu-id="6631b-139">Birleştirme `if` ve `else` Boolean ile koşullar sağlar hem işlemek için ihtiyacınız olan tüm güç bir `true` ve `false` koşulu.</span><span class="sxs-lookup"><span data-stu-id="6631b-139">Combining `if` and `else` with Boolean conditions provides all the power you need to handle both a `true` and a `false` condition.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6631b-140">Girinti altında `if` ve `else` deyimleri İnsan okuyucular için değil.</span><span class="sxs-lookup"><span data-stu-id="6631b-140">The indentation under the `if` and `else` statements is for human readers.</span></span>
> <span data-ttu-id="6631b-141">C# dili girinti veya boşluk önemli olarak kabul etmez.</span><span class="sxs-lookup"><span data-stu-id="6631b-141">The C# language doesn't treat indentation or whitespace as significant.</span></span> <span data-ttu-id="6631b-142">Deyimi aşağıdaki `if` veya `else` anahtar sözcüğü koşula göre yürütülür.</span><span class="sxs-lookup"><span data-stu-id="6631b-142">The statement following the `if` or `else` keyword will be executed based on the condition.</span></span> <span data-ttu-id="6631b-143">Bu hızlı başlangıç tüm örneklerinde satırlarını deyimleri denetim akışı üzerinde göre Girintile yaygın bir uygulama izleyin.</span><span class="sxs-lookup"><span data-stu-id="6631b-143">All the samples in this quick start follow a common practice to indent lines based on the control flow of statements.</span></span>

<span data-ttu-id="6631b-144">Girinti önemli olmadığı için kullanmanıza gerek `{` ve `}` koşullu yürütür blok parçası olarak birden fazla deyim istediğinizde belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="6631b-144">Because indentation is not significant, you need to use `{` and `}` to indicate when you want more than one statement to be part of the block that executes conditionally.</span></span> <span data-ttu-id="6631b-145">C# programcıları genellikle kullanın Bu küme ayraçları tüm `if` ve `else` yan tümceleri.</span><span class="sxs-lookup"><span data-stu-id="6631b-145">C# programmers typically use those braces on all `if` and `else` clauses.</span></span> <span data-ttu-id="6631b-146">Aşağıdaki örnek, yeni oluşturduğunuz bir ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="6631b-146">The following example is the same as the one you just created.</span></span> <span data-ttu-id="6631b-147">Aşağıdaki kod eşleştirmek için yukarıdaki kodunuzu değiştirin:</span><span class="sxs-lookup"><span data-stu-id="6631b-147">Modify your code above to match the following code:</span></span>

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
> <span data-ttu-id="6631b-148">Bu hızlı başlangıç kullanılmadıkları tüm kod örnekleri aşağıdaki küme ayraçları dahil kabul yöntemler.</span><span class="sxs-lookup"><span data-stu-id="6631b-148">Through the rest of this quick start, the code samples all include the braces, following accepted practices.</span></span>

<span data-ttu-id="6631b-149">Daha karmaşık koşullar test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6631b-149">You can test more complicated conditions.</span></span> <span data-ttu-id="6631b-150">Aşağıdaki kodu ekleyin, `Main` yöntemi, o ana kadarki yazılan koddan sonra:</span><span class="sxs-lookup"><span data-stu-id="6631b-150">Add the following code in your `Main` method after the code you've written so far:</span></span>

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

<span data-ttu-id="6631b-151">`&&` Temsil eder "ve".</span><span class="sxs-lookup"><span data-stu-id="6631b-151">The `&&` represents "and".</span></span> <span data-ttu-id="6631b-152">Bu koşulların her ikisi de true dalında deyimi yürütmek için doğru olması gerektiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="6631b-152">It means both conditions must be true to execute the statement in the true branch.</span></span>  <span data-ttu-id="6631b-153">Bunları içine sağlanan bu Ayrıca, her koşullu dal birden fazla deyime olabilir örnekler `{` ve `}`.</span><span class="sxs-lookup"><span data-stu-id="6631b-153">These examples also show that you can have multiple statements in each conditional branch, provided you enclose them in `{` and `}`.</span></span>

<span data-ttu-id="6631b-154">Aynı zamanda `||` temsil etmek için "veya".</span><span class="sxs-lookup"><span data-stu-id="6631b-154">You can also use  `||` to represent "or".</span></span> <span data-ttu-id="6631b-155">Şu ana kadar yazdıklarınızı sonra aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="6631b-155">Add the following code after what you've written so far:</span></span>

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

<span data-ttu-id="6631b-156">İlk adım tamamladınız.</span><span class="sxs-lookup"><span data-stu-id="6631b-156">You've finished the first step.</span></span> <span data-ttu-id="6631b-157">Şimdi, sonraki bölüme başlamadan önce geçerli kod ayrı bir yöntem taşıyın.</span><span class="sxs-lookup"><span data-stu-id="6631b-157">Before you start the next section, let's move the current code into a separate method.</span></span> <span data-ttu-id="6631b-158">Bu, yeni bir örnek ile çalışmaya başlamak kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="6631b-158">That makes it easier to start working with a new example.</span></span> <span data-ttu-id="6631b-159">Yeniden Adlandır, `Main` yönteme `ExploreIf` ve yeni bir yazma `Main` çağıran yöntemi `ExploreIf`.</span><span class="sxs-lookup"><span data-stu-id="6631b-159">Rename your `Main` method to `ExploreIf` and write a new `Main` method that calls `ExploreIf`.</span></span> <span data-ttu-id="6631b-160">İşiniz bittiğinde, kodunuzu aşağıdaki gibi görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="6631b-160">When you have finished, your code should look like this:</span></span>

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

<span data-ttu-id="6631b-161">Açıklama çağrısı çıkışı `ExploreIf()`.</span><span class="sxs-lookup"><span data-stu-id="6631b-161">Comment out the call to `ExploreIf()`.</span></span> <span data-ttu-id="6631b-162">Bu bölümde çalışırken daha az kalabalık çıkış yapar:</span><span class="sxs-lookup"><span data-stu-id="6631b-162">It will make the output less cluttered as you work in this section:</span></span>

```csharp
//ExploreIf();
```

<span data-ttu-id="6631b-163">`//` Başlayan bir **açıklama** C#.</span><span class="sxs-lookup"><span data-stu-id="6631b-163">The `//` starts a **comment** in C#.</span></span> <span data-ttu-id="6631b-164">Kaynak kodunuz tutmak ancak kodu olarak yürütmeme istediğiniz herhangi bir metin açıklamalardır.</span><span class="sxs-lookup"><span data-stu-id="6631b-164">Comments are any text you want to keep in your source code but not execute as code.</span></span> <span data-ttu-id="6631b-165">Derleyici herhangi bir yürütülebilir kod açıklamalardan oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="6631b-165">The compiler does not generate any executable code from comments.</span></span>

## <a name="use-loops-to-repeat-operations"></a><span data-ttu-id="6631b-166">Döngüler işlemleri yinelemek için kullanın</span><span class="sxs-lookup"><span data-stu-id="6631b-166">Use loops to repeat operations</span></span>

<span data-ttu-id="6631b-167">Bu bölümde kullandığınız **döngüler** deyimleri yinelenecek.</span><span class="sxs-lookup"><span data-stu-id="6631b-167">In this section you use **loops** to repeat statements.</span></span> <span data-ttu-id="6631b-168">Bu kodda deneyin, `Main` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="6631b-168">Try this code in your `Main` method:</span></span>

```csharp
int counter = 0;
while (counter < 10)
{
    Console.WriteLine($"Hello World! The counter is {counter}");
    counter++;
}
```

<span data-ttu-id="6631b-169">`while` İfadesi bir koşulu denetler ve ifadesi veya deyimi blok aşağıdaki yürütür `while`.</span><span class="sxs-lookup"><span data-stu-id="6631b-169">The `while` statement checks a condition and executes the statement or statement block following the `while`.</span></span> <span data-ttu-id="6631b-170">Art arda koşul ve koşul yanlış olana kadar bu deyimleri yürütme denetler.</span><span class="sxs-lookup"><span data-stu-id="6631b-170">It repeatedly checks the condition and executing those statements until the condition is false.</span></span>

<span data-ttu-id="6631b-171">Bu örnekte, diğer yeni bir işleç var.</span><span class="sxs-lookup"><span data-stu-id="6631b-171">There's one other new operator in this example.</span></span> <span data-ttu-id="6631b-172">`++` Sonra `counter` değişken **artırma** işleci.</span><span class="sxs-lookup"><span data-stu-id="6631b-172">The `++` after the `counter` variable is the **increment** operator.</span></span> <span data-ttu-id="6631b-173">1 değerine ekler `counter` ve bu değeri depolar `counter` değişkeni.</span><span class="sxs-lookup"><span data-stu-id="6631b-173">It adds 1 to the value of `counter` and stores that value in the `counter` variable.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6631b-174">Olduğundan emin olun `while` kod yürütmek gibi Döngü koşulu değişiklikleri false.</span><span class="sxs-lookup"><span data-stu-id="6631b-174">Make sure that the `while` loop condition changes to false as you execute the code.</span></span> <span data-ttu-id="6631b-175">Aksi takdirde, oluşturduğunuz bir **sonsuz bir döngü** programınızı hiçbir zaman sona ereceği.</span><span class="sxs-lookup"><span data-stu-id="6631b-175">Otherwise, you create an **infinite loop** where your program never ends.</span></span> <span data-ttu-id="6631b-176">Değil gösterilmiştir Bu örnekte, kullanarak çıkmak için program zorlamak olduğundan **CTRL-C** veya diğer anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="6631b-176">That is not demonstrated in this sample, because you have to force your program to quit using **CTRL-C** or other means.</span></span>

<span data-ttu-id="6631b-177">`while` Döngü kod aşağıdaki yürütmeden önce koşulu sınar `while`.</span><span class="sxs-lookup"><span data-stu-id="6631b-177">The `while` loop tests the condition before executing the code following the `while`.</span></span> <span data-ttu-id="6631b-178">`do` ... `while` döngü kodu ilk yürütür ve koşul denetler.</span><span class="sxs-lookup"><span data-stu-id="6631b-178">The `do` ... `while` loop executes the code first, and then checks the condition.</span></span> <span data-ttu-id="6631b-179">Aşağıdaki kodda döngü gösterilmese yapın:</span><span class="sxs-lookup"><span data-stu-id="6631b-179">The do while loop is shown in the following code:</span></span>

```csharp
counter = 0;
do
{
    Console.WriteLine($"Hello World! The counter is {counter}");
    counter++;
} while (counter < 10);
```

<span data-ttu-id="6631b-180">Bu `do` döngü ve önceki `while` döngü, aynı çıktı üretir.</span><span class="sxs-lookup"><span data-stu-id="6631b-180">This `do` loop and the earlier `while` loop produce the same output.</span></span>

## <a name="work-with-the-for-loop"></a><span data-ttu-id="6631b-181">Çalışmak döngü için</span><span class="sxs-lookup"><span data-stu-id="6631b-181">Work with the for loop</span></span>

<span data-ttu-id="6631b-182">**İçin** döngü yaygın olarak kullanılan C# '.</span><span class="sxs-lookup"><span data-stu-id="6631b-182">The **for** loop is commonly used in C#.</span></span> <span data-ttu-id="6631b-183">Bu kod, Main() yönteminin deneyin:</span><span class="sxs-lookup"><span data-stu-id="6631b-183">Try this code in your Main() method:</span></span>

```csharp
for(int index = 0; index < 10; index++)
{
    Console.WriteLine($"Hello World! The index is {index}");
} 
```

<span data-ttu-id="6631b-184">Aynı iş olarak bunu yapar `while` döngü ve `do` zaten kullandığınız döngü.</span><span class="sxs-lookup"><span data-stu-id="6631b-184">This does the same work as the `while` loop and the `do` loop you've already used.</span></span> <span data-ttu-id="6631b-185">`for` Deyimi nasıl çalıştığını denetleyen üç bölümden sahiptir.</span><span class="sxs-lookup"><span data-stu-id="6631b-185">The `for` statement has three parts that control how it works.</span></span> 

<span data-ttu-id="6631b-186">İlk bölümüdür **Başlatıcısı için**: `for index = 0;` bildiren `index` döngü değişkendir ve ilk değerini ayarlar `0`.</span><span class="sxs-lookup"><span data-stu-id="6631b-186">The first part is the **for initializer**: `for index = 0;` declares that `index` is the loop variable, and sets its initial value to `0`.</span></span>

<span data-ttu-id="6631b-187">Orta parçasıdır **koşul için**: `index < 10` bildirir bu `for` sayacın değeri 10'dan az olduğu sürece yürütme döngü devam eder.</span><span class="sxs-lookup"><span data-stu-id="6631b-187">The middle part is the **for condition**: `index < 10` declares that this `for` loop continues to execute as long as the value of counter is less than 10.</span></span>

<span data-ttu-id="6631b-188">Son bölümüdür **yineleyici için**: `index++` blok aşağıdaki yürüttükten sonra Döngü değişkeninin değiştirme belirtir `for` deyimi.</span><span class="sxs-lookup"><span data-stu-id="6631b-188">The final part is the **for iterator**: `index++` specifies how to modify the loop variable after executing the block following the `for` statement.</span></span> <span data-ttu-id="6631b-189">Burada, belirtir `index` bloğu yürütür her zaman 1 azaltılır.</span><span class="sxs-lookup"><span data-stu-id="6631b-189">Here, it specifies that `index` should be incremented by 1 each time the block executes.</span></span>

<span data-ttu-id="6631b-190">Bu kendinizle deneyin.</span><span class="sxs-lookup"><span data-stu-id="6631b-190">Experiment with these yourself.</span></span> <span data-ttu-id="6631b-191">Her birini deneyin:</span><span class="sxs-lookup"><span data-stu-id="6631b-191">Try each of the following:</span></span>

- <span data-ttu-id="6631b-192">Farklı bir değer başlatmak için Başlatıcı değiştirin.</span><span class="sxs-lookup"><span data-stu-id="6631b-192">Change the initializer to start at a different value.</span></span>
- <span data-ttu-id="6631b-193">Farklı bir değer durdurmak için koşulunu değiştirin.</span><span class="sxs-lookup"><span data-stu-id="6631b-193">Change the condition to stop at a different value.</span></span>

<span data-ttu-id="6631b-194">İşiniz bittiğinde, şimdi taşıma açın yazma bazı kendiniz ne öğrendiğinize kullanmak için kodu.</span><span class="sxs-lookup"><span data-stu-id="6631b-194">When you're done, let's move on to write some code yourself to use what you've learned.</span></span>

## <a name="combine-branches-and-loops"></a><span data-ttu-id="6631b-195">Dal ve döngüler birleştirin</span><span class="sxs-lookup"><span data-stu-id="6631b-195">Combine branches and loops</span></span>

<span data-ttu-id="6631b-196">Gördüğünüz göre `if` deyimi ve C# dil döngü yapıları bkz tüm tamsayılar 1 ila 3 ile tam bölünebilir 20 toplamını bulmak için C# kod yazın.</span><span class="sxs-lookup"><span data-stu-id="6631b-196">Now that you've seen the `if` statement and the looping constructs in the C# language, see if you can write C# code to find the sum of all integers 1 through 20 that are divisible by 3.</span></span>  <span data-ttu-id="6631b-197">Aşağıda, birkaç ipucu verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="6631b-197">Here are a few hints:</span></span>

- <span data-ttu-id="6631b-198">`%` İşleci, bir bölme işlemi geri kalanı verir.</span><span class="sxs-lookup"><span data-stu-id="6631b-198">The `%` operator gives you the remainder of a division operation.</span></span>
- <span data-ttu-id="6631b-199">`if` Deyimi, bir sayı toplamı parçası olup olmayacağını görmek için koşul verir.</span><span class="sxs-lookup"><span data-stu-id="6631b-199">The `if` statement gives you the condition to see if a number should be part of the sum.</span></span>
- <span data-ttu-id="6631b-200">`for` Döngü, 20'den sayılar 1 için bir dizi adımı yineleyin yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="6631b-200">The `for` loop can help you repeat a series of steps for all the numbers 1 through 20.</span></span>

<span data-ttu-id="6631b-201">Kendiniz deneyin.</span><span class="sxs-lookup"><span data-stu-id="6631b-201">Try it yourself.</span></span> <span data-ttu-id="6631b-202">Ardından nasıl yaptığınız denetleyin.</span><span class="sxs-lookup"><span data-stu-id="6631b-202">Then check how you did.</span></span> <span data-ttu-id="6631b-203">Tarafından bir olası yanıt görebilirsiniz [tamamlanan kodu Github'da görüntüleme](https://github.com/dotnet/docs/tree/master/samples/csharp/branches-quickstart/Program.cs#L46-L54).</span><span class="sxs-lookup"><span data-stu-id="6631b-203">You can see one possible answer by [viewing the completed code on GitHub](https://github.com/dotnet/docs/tree/master/samples/csharp/branches-quickstart/Program.cs#L46-L54).</span></span>

<span data-ttu-id="6631b-204">"Dallandırır ve döngü" Hızlı Başlangıç tamamladınız.</span><span class="sxs-lookup"><span data-stu-id="6631b-204">You've completed the "branches and loops" quick start.</span></span>

<span data-ttu-id="6631b-205">İle devam edebilirsiniz [dizileri ve koleksiyonları](arrays-and-collections.md) kendi geliştirme ortamında hızlı başlangıç.</span><span class="sxs-lookup"><span data-stu-id="6631b-205">You can continue with the [Arrays and collections](arrays-and-collections.md) quick start in your own development environment.</span></span>

<span data-ttu-id="6631b-206">Bu konularda bu kavramlar hakkında daha fazla bilgi edinebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="6631b-206">You can learn more about these concepts in these topics:</span></span>

<span data-ttu-id="6631b-207">[Varsa ve else deyimi](../language-reference/keywords/if-else.md) </span><span class="sxs-lookup"><span data-stu-id="6631b-207">[If and else statement](../language-reference/keywords/if-else.md) </span></span>  
<span data-ttu-id="6631b-208">[While deyimi](../language-reference/keywords/while.md) </span><span class="sxs-lookup"><span data-stu-id="6631b-208">[While statement](../language-reference/keywords/while.md) </span></span>  
<span data-ttu-id="6631b-209">[Do deyimi](../language-reference/keywords/do.md) </span><span class="sxs-lookup"><span data-stu-id="6631b-209">[Do statement](../language-reference/keywords/do.md) </span></span>  
[<span data-ttu-id="6631b-210">For deyimi</span><span class="sxs-lookup"><span data-stu-id="6631b-210">For statement</span></span>](../language-reference/keywords/for.md)   
