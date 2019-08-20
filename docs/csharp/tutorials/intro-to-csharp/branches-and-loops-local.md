---
title: Dallar ve döngüler- C# öğreticiye giriş
description: Dallar ve döngüler hakkında bu öğreticide, ifadeleri sürekli C# olarak yürütmek için koşullu dalları ve döngüleri destekleyen dil sözdizimini araştırmak üzere kod yazarsınız.
ms.date: 10/31/2017
ms.custom: mvc
ms.openlocfilehash: 0da446a71f5d7a7183a8323c470087c8726bc02f
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69587219"
---
# <a name="learn-conditional-logic-with-branch-and-loop-statements"></a><span data-ttu-id="dc08c-103">Dal ve döngü deyimleri ile koşullu mantık öğrenin</span><span class="sxs-lookup"><span data-stu-id="dc08c-103">Learn conditional logic with branch and loop statements</span></span>

<span data-ttu-id="dc08c-104">Bu öğretici, değişkenleri inceleyen ve bu değişkenlere göre yürütme yolunu değiştiren bir kod yazmayı öğretir.</span><span class="sxs-lookup"><span data-stu-id="dc08c-104">This tutorial teaches you how to write code that examines variables and changes the execution path based on those variables.</span></span> <span data-ttu-id="dc08c-105">Kod yazar C# ve bunları derleyip çalıştırmaya ilişkin sonuçları görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="dc08c-105">You write C# code and see the results of compiling and running it.</span></span> <span data-ttu-id="dc08c-106">Öğreticide, ' de C#dallanma ve döngü yapılarını keşfeden oluşan bir dizi ders bulunur.</span><span class="sxs-lookup"><span data-stu-id="dc08c-106">The tutorial contains a series of lessons that explore branching and looping constructs in C#.</span></span> <span data-ttu-id="dc08c-107">Bu dersler, C# dilin temellerini öğretir.</span><span class="sxs-lookup"><span data-stu-id="dc08c-107">These lessons teach you the fundamentals of the C# language.</span></span>

<span data-ttu-id="dc08c-108">Bu öğreticide, geliştirme için kullanabileceğiniz bir makineniz olması beklenir.</span><span class="sxs-lookup"><span data-stu-id="dc08c-108">This tutorial expects you to have a machine you can use for development.</span></span> <span data-ttu-id="dc08c-109">[10 dakika Içinde başlayan](https://www.microsoft.com/net/core) .net konusunun yerel geliştirme ortamınızı Mac, PC veya Linux üzerinde ayarlamaya yönelik yönergeler vardır.</span><span class="sxs-lookup"><span data-stu-id="dc08c-109">The .NET topic [Get Started in 10 minutes](https://www.microsoft.com/net/core) has instructions for setting up your local development environment on Mac, PC or Linux.</span></span> <span data-ttu-id="dc08c-110">Kullanacağınız komutlara hızlı bir genel bakış, daha fazla ayrıntı için bağlantılarla birlikte [geliştirme araçları hakkında bilgi sahibi olmaya gelmiştir](local-environment.md) .</span><span class="sxs-lookup"><span data-stu-id="dc08c-110">A quick overview of the commands you'll use is in the [Become familiar with the development tools](local-environment.md) with links to more details.</span></span>

## <a name="make-decisions-using-the-if-statement"></a><span data-ttu-id="dc08c-111">`if` İfadesini kullanarak kararlar alın</span><span class="sxs-lookup"><span data-stu-id="dc08c-111">Make decisions using the `if` statement</span></span>

<span data-ttu-id="dc08c-112">Dallar adlı bir dizin oluşturun **-öğretici**.</span><span class="sxs-lookup"><span data-stu-id="dc08c-112">Create a directory named **branches-tutorial**.</span></span> <span data-ttu-id="dc08c-113">Geçerli dizini oluşturun ve çalıştırın `dotnet new console -n BranchesAndLoops -o .`.</span><span class="sxs-lookup"><span data-stu-id="dc08c-113">Make that the current directory and run `dotnet new console -n BranchesAndLoops -o .`.</span></span> <span data-ttu-id="dc08c-114">Bu komut geçerli dizinde yeni bir .NET Core konsol uygulaması oluşturur.</span><span class="sxs-lookup"><span data-stu-id="dc08c-114">This command creates a new .NET Core console application in the current directory.</span></span>

<span data-ttu-id="dc08c-115">En sevdiğiniz düzenleyicide **program.cs** açın ve satırı `Console.WriteLine("Hello World!");` aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="dc08c-115">Open **Program.cs** in your favorite editor, and replace the line `Console.WriteLine("Hello World!");` with the following code:</span></span>

```csharp
int a = 5;
int b = 6;
if (a + b > 10)
    Console.WriteLine("The answer is greater than 10.");
```

<span data-ttu-id="dc08c-116">Konsol pencerenizi yazarak `dotnet run` bu kodu deneyin.</span><span class="sxs-lookup"><span data-stu-id="dc08c-116">Try this code by typing `dotnet run` in your console window.</span></span> <span data-ttu-id="dc08c-117">"Yanıt 10 ' dan büyük" iletisini görmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="dc08c-117">You should see the message "The answer is greater than 10."</span></span> <span data-ttu-id="dc08c-118">konsolunuza yazdırılır.</span><span class="sxs-lookup"><span data-stu-id="dc08c-118">printed to your console.</span></span>

<span data-ttu-id="dc08c-119">Bildirimi, toplamın 10 `b` ' dan küçük olacak şekilde değiştirin:</span><span class="sxs-lookup"><span data-stu-id="dc08c-119">Modify the declaration of `b` so that the sum is less than 10:</span></span>

```csharp
int b = 3;
```

<span data-ttu-id="dc08c-120">Yeniden `dotnet run` yazın.</span><span class="sxs-lookup"><span data-stu-id="dc08c-120">Type `dotnet run` again.</span></span> <span data-ttu-id="dc08c-121">Yanıt 10 ' dan az olduğu için hiçbir şey yazdırılmaz.</span><span class="sxs-lookup"><span data-stu-id="dc08c-121">Because the answer is less than 10, nothing is printed.</span></span> <span data-ttu-id="dc08c-122">Test ettiğiniz **koşul** false 'tur.</span><span class="sxs-lookup"><span data-stu-id="dc08c-122">The **condition** you're testing is false.</span></span> <span data-ttu-id="dc08c-123">Yalnızca bir `if` deyimin olası dallarından birini yazdığınız için yürütülecek bir kodunuz yok: doğru dal.</span><span class="sxs-lookup"><span data-stu-id="dc08c-123">You don't have any code to execute because you've only written one of the possible branches for an `if` statement: the true branch.</span></span>

> [!TIP]
> <span data-ttu-id="dc08c-124">Keşfederken C# (veya herhangi bir programlama dilini), kod yazarken hata oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="dc08c-124">As you explore C# (or any programming language), you'll make mistakes when you write code.</span></span> <span data-ttu-id="dc08c-125">Derleyici hataları bulacak ve rapor eder.</span><span class="sxs-lookup"><span data-stu-id="dc08c-125">The compiler will find and report the errors.</span></span> <span data-ttu-id="dc08c-126">Hata çıktısına ve hatayı oluşturan koda yakından bakın.</span><span class="sxs-lookup"><span data-stu-id="dc08c-126">Look closely at the error output and the code that generated the error.</span></span> <span data-ttu-id="dc08c-127">Derleyici hatası genellikle sorunu bulmanıza yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="dc08c-127">The compiler error can usually help you find the problem.</span></span>

<span data-ttu-id="dc08c-128">Bu ilk örnek, `if` ve Boolean türlerin gücünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="dc08c-128">This first sample shows the power of `if` and Boolean types.</span></span> <span data-ttu-id="dc08c-129">*Boolean* , iki değerden birine sahip olabilir bir değişkendir: `true` veya. `false`</span><span class="sxs-lookup"><span data-stu-id="dc08c-129">A *Boolean* is a variable that can have one of two values: `true` or `false`.</span></span> <span data-ttu-id="dc08c-130">C#Boole değişkenleri `bool` için özel bir tür tanımlar.</span><span class="sxs-lookup"><span data-stu-id="dc08c-130">C# defines a special type, `bool` for Boolean variables.</span></span> <span data-ttu-id="dc08c-131">`if` İfade a`bool`değerini denetler.</span><span class="sxs-lookup"><span data-stu-id="dc08c-131">The `if` statement checks the value of a `bool`.</span></span> <span data-ttu-id="dc08c-132">Değer `true`olduğunda, `if` yürütülür ' i izleyen ifade.</span><span class="sxs-lookup"><span data-stu-id="dc08c-132">When the value is `true`, the statement following the `if` executes.</span></span> <span data-ttu-id="dc08c-133">Aksi takdirde, atlanır.</span><span class="sxs-lookup"><span data-stu-id="dc08c-133">Otherwise, it is skipped.</span></span>

<span data-ttu-id="dc08c-134">Bu koşullara göre koşulları denetleme ve deyimleri yürütme işlemi çok güçlüdür.</span><span class="sxs-lookup"><span data-stu-id="dc08c-134">This process of checking conditions and executing statements based on those conditions is very powerful.</span></span>

## <a name="make-if-and-else-work-together"></a><span data-ttu-id="dc08c-135">Eğer ve başka bir birlikte çalışır yap</span><span class="sxs-lookup"><span data-stu-id="dc08c-135">Make if and else work together</span></span>

<span data-ttu-id="dc08c-136">Doğru ve yanlış dallarda farklı kodu yürütmek için, koşul yanlış olduğunda yürütülen bir `else` dal oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="dc08c-136">To execute different code in both the true and false branches, you create an `else` branch that executes when the condition is false.</span></span> <span data-ttu-id="dc08c-137">Bunu deneyin.</span><span class="sxs-lookup"><span data-stu-id="dc08c-137">Try this.</span></span> <span data-ttu-id="dc08c-138">Aşağıdaki kodda bulunan son iki satırı `Main` yöntemine ekleyin (ilk dördü zaten var olmalıdır):</span><span class="sxs-lookup"><span data-stu-id="dc08c-138">Add the last two lines in the code below to your `Main` method (you should already have the first four):</span></span>

```csharp
int a = 5;
int b = 3;
if (a + b > 10)
    Console.WriteLine("The answer is greater than 10");
else
    Console.WriteLine("The answer is not greater than 10");
```

<span data-ttu-id="dc08c-139">`else` Anahtar sözcüğünü izleyen ifade yalnızca `false`test edilen koşul olduğunda yürütülür.</span><span class="sxs-lookup"><span data-stu-id="dc08c-139">The statement following the `else` keyword executes only when the condition being tested is `false`.</span></span> <span data-ttu-id="dc08c-140">Ve `if` `true` `false` Boolean koşulları ile birleştirmek, hem hem de bir koşulu işlemek için ihtiyacınız olan tüm gücü sağlar. `else`</span><span class="sxs-lookup"><span data-stu-id="dc08c-140">Combining `if` and `else` with Boolean conditions provides all the power you need to handle both a `true` and a `false` condition.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="dc08c-141">`if` Ve`else` deyimlerinin altındaki girintileme insan okuyucular içindir.</span><span class="sxs-lookup"><span data-stu-id="dc08c-141">The indentation under the `if` and `else` statements is for human readers.</span></span>
> <span data-ttu-id="dc08c-142">Dil C# , girintileme veya boşluk olarak kabul etmez.</span><span class="sxs-lookup"><span data-stu-id="dc08c-142">The C# language doesn't treat indentation or white space as significant.</span></span>
> <span data-ttu-id="dc08c-143">`if` Or`else` anahtar sözcüğünü izleyen ifade, koşula göre yürütülür.</span><span class="sxs-lookup"><span data-stu-id="dc08c-143">The statement following the `if` or `else` keyword will be executed based on the condition.</span></span> <span data-ttu-id="dc08c-144">Bu öğreticideki tüm örnekler, ifadelerin denetim akışına göre satırları girintilemek için ortak bir uygulama izler.</span><span class="sxs-lookup"><span data-stu-id="dc08c-144">All the samples in this tutorial follow a common practice to indent lines based on the control flow of statements.</span></span>

<span data-ttu-id="dc08c-145">Girintileme önemli olmadığından, birden fazla deyimin koşullu olarak yürütülen `{` bloğun `}` bir parçası olmasını istediğiniz zaman göstermek için ve kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="dc08c-145">Because indentation is not significant, you need to use `{` and `}` to indicate when you want more than one statement to be part of the block that executes conditionally.</span></span> <span data-ttu-id="dc08c-146">C#programcılar genellikle bu ayraçları tüm `if` ve `else` yan tümcelerde kullanır.</span><span class="sxs-lookup"><span data-stu-id="dc08c-146">C# programmers typically use those braces on all `if` and `else` clauses.</span></span> <span data-ttu-id="dc08c-147">Aşağıdaki örnek, az önce oluşturduğunuz ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="dc08c-147">The following example is the same as the one you just created.</span></span> <span data-ttu-id="dc08c-148">Yukarıdaki kodu aşağıdaki kodla eşleşecek şekilde değiştirin:</span><span class="sxs-lookup"><span data-stu-id="dc08c-148">Modify your code above to match the following code:</span></span>

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
> <span data-ttu-id="dc08c-149">Bu öğreticinin geri kalanında, kod örnekleri, kabul edilen uygulamaları takip eden ayraçları içerir.</span><span class="sxs-lookup"><span data-stu-id="dc08c-149">Through the rest of this tutorial, the code samples all include the braces, following accepted practices.</span></span>

<span data-ttu-id="dc08c-150">Daha karmaşık koşulları test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dc08c-150">You can test more complicated conditions.</span></span> <span data-ttu-id="dc08c-151">Şu ana kadar yazdığınız koddan sonra `Main` aşağıdaki kodu yöntemine ekleyin:</span><span class="sxs-lookup"><span data-stu-id="dc08c-151">Add the following code in your `Main` method after the code you've written so far:</span></span>

```csharp
int c = 4;
if ((a + b + c > 10) && (a == b))
{
    Console.WriteLine("The answer is greater than 10");
    Console.WriteLine("And the first number is equal to the second");
}
else
{
    Console.WriteLine("The answer is not greater than 10");
    Console.WriteLine("Or the first number is not equal to the second");
}
```

<span data-ttu-id="dc08c-152">`==` *Eşitlik*için simge testi.</span><span class="sxs-lookup"><span data-stu-id="dc08c-152">The `==` symbol tests for *equality*.</span></span> <span data-ttu-id="dc08c-153">' `==` Yi kullanarak, ' de gördüğünüz şekilde `a = 5`testi, atamanın eşitliğine ayırır.</span><span class="sxs-lookup"><span data-stu-id="dc08c-153">Using `==` distinguishes the test for equality from assignment, which you saw in `a = 5`.</span></span>

<span data-ttu-id="dc08c-154">"Ve" temsil eder. `&&`</span><span class="sxs-lookup"><span data-stu-id="dc08c-154">The `&&` represents "and".</span></span> <span data-ttu-id="dc08c-155">Doğru dalda deyimin yürütülmesi için her iki koşulun de true olması gerektiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="dc08c-155">It means both conditions must be true to execute the statement in the true branch.</span></span>  <span data-ttu-id="dc08c-156">Bu örnekler Ayrıca, ve `{` `}`içinde yer alan her bir koşullu dalda birden çok deyim olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="dc08c-156">These examples also show that you can have multiple statements in each conditional branch, provided you enclose them in `{` and `}`.</span></span>

<span data-ttu-id="dc08c-157">"Veya" öğesini `||` göstermek için de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dc08c-157">You can also use  `||` to represent "or".</span></span> <span data-ttu-id="dc08c-158">Şu ana kadar yazıldıktan sonra aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="dc08c-158">Add the following code after what you've written so far:</span></span>

```csharp
if ((a + b + c > 10) || (a == b))
{
    Console.WriteLine("The answer is greater than 10");
    Console.WriteLine("Or the first number is equal to the second");
}
else
{
    Console.WriteLine("The answer is not greater than 10");
    Console.WriteLine("And the first number is not equal to the second");
}
```

<span data-ttu-id="dc08c-159">`a`, Ve`b`değerlerini değiştirin ve arasında`&&` geçiş yapın.`||` `c`</span><span class="sxs-lookup"><span data-stu-id="dc08c-159">Modify the values of `a`, `b`, and `c` and switch between `&&` and `||` to explore.</span></span> <span data-ttu-id="dc08c-160">`&&` Ve`||` işleçlerinin nasıl çalıştığını daha fazla anlayacaksınız.</span><span class="sxs-lookup"><span data-stu-id="dc08c-160">You'll gain more understanding of how the `&&` and `||` operators work.</span></span>

<span data-ttu-id="dc08c-161">İlk adımı tamamladınız.</span><span class="sxs-lookup"><span data-stu-id="dc08c-161">You've finished the first step.</span></span> <span data-ttu-id="dc08c-162">Sonraki bölüme başlamadan önce geçerli kodu ayrı bir yönteme taşıyalim.</span><span class="sxs-lookup"><span data-stu-id="dc08c-162">Before you start the next section, let's move the current code into a separate method.</span></span> <span data-ttu-id="dc08c-163">Bu, yeni bir örnekle çalışmaya başlamasını kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="dc08c-163">That makes it easier to start working with a new example.</span></span> <span data-ttu-id="dc08c-164">Yönteminizi olarak `ExploreIf` yeniden adlandırın ve çağıran `Main` `ExploreIf`yeni bir yöntem yazın. `Main`</span><span class="sxs-lookup"><span data-stu-id="dc08c-164">Rename your `Main` method to `ExploreIf` and write a new `Main` method that calls `ExploreIf`.</span></span> <span data-ttu-id="dc08c-165">İşiniz bittiğinde kodunuzun şöyle görünmesi gerekir:</span><span class="sxs-lookup"><span data-stu-id="dc08c-165">When you have finished, your code should look like this:</span></span>

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

<span data-ttu-id="dc08c-166">Çağrısını not edin `ExploreIf()`.</span><span class="sxs-lookup"><span data-stu-id="dc08c-166">Comment out the call to `ExploreIf()`.</span></span> <span data-ttu-id="dc08c-167">Bu bölümde çalışırken çıktının daha az karışık hale gelir:</span><span class="sxs-lookup"><span data-stu-id="dc08c-167">It will make the output less cluttered as you work in this section:</span></span>

```csharp
//ExploreIf();
```

<span data-ttu-id="dc08c-168">, `//` İçinde C#bir **yorum** başlatır.</span><span class="sxs-lookup"><span data-stu-id="dc08c-168">The `//` starts a **comment** in C#.</span></span> <span data-ttu-id="dc08c-169">Açıklamalar, kaynak kodunuzda tutmak istediğiniz tüm metinlerdir, ancak kod olarak yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="dc08c-169">Comments are any text you want to keep in your source code but not execute as code.</span></span> <span data-ttu-id="dc08c-170">Derleyici açıklamalardan herhangi bir yürütülebilir kod oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="dc08c-170">The compiler does not generate any executable code from comments.</span></span>

## <a name="use-loops-to-repeat-operations"></a><span data-ttu-id="dc08c-171">İşlemleri yinelemek için döngüleri kullanma</span><span class="sxs-lookup"><span data-stu-id="dc08c-171">Use loops to repeat operations</span></span>

<span data-ttu-id="dc08c-172">Bu bölümde deyimlerini yinelemek için **döngüleri** kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="dc08c-172">In this section you use **loops** to repeat statements.</span></span> <span data-ttu-id="dc08c-173">Bu kodu `Main` yönteminizin içinde deneyin:</span><span class="sxs-lookup"><span data-stu-id="dc08c-173">Try this code in your `Main` method:</span></span>

```csharp
int counter = 0;
while (counter < 10)
{
    Console.WriteLine($"Hello World! The counter is {counter}");
    counter++;
}
```

<span data-ttu-id="dc08c-174">İfade bir koşulu denetler ve öğesinden sonra deyimin veya bildiri bloğunu `while`yürütür. `while`</span><span class="sxs-lookup"><span data-stu-id="dc08c-174">The `while` statement checks a condition and executes the statement or statement block following the `while`.</span></span> <span data-ttu-id="dc08c-175">Koşul false olana kadar durumu sürekli olarak denetler ve bu deyimleri gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="dc08c-175">It repeatedly checks the condition and executing those statements until the condition is false.</span></span>

<span data-ttu-id="dc08c-176">Bu örnekte başka bir yeni işleç vardır.</span><span class="sxs-lookup"><span data-stu-id="dc08c-176">There's one other new operator in this example.</span></span> <span data-ttu-id="dc08c-177">Değişken, **artırma** işlecinden `++`sonra. `counter`</span><span class="sxs-lookup"><span data-stu-id="dc08c-177">The `++` after the `counter` variable is the **increment** operator.</span></span> <span data-ttu-id="dc08c-178">Değerine `counter` 1 ekler ve bu değeri `counter` değişkende depolar.</span><span class="sxs-lookup"><span data-stu-id="dc08c-178">It adds 1 to the value of `counter` and stores that value in the `counter` variable.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="dc08c-179">Kodu yürüttüğünüzde `while` döngü koşulunun yanlış olarak değiştiği emin olun.</span><span class="sxs-lookup"><span data-stu-id="dc08c-179">Make sure that the `while` loop condition changes to false as you execute the code.</span></span> <span data-ttu-id="dc08c-180">Aksi takdirde, programınızın hiç bitmediğini **sonsuz bir döngü** oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="dc08c-180">Otherwise, you create an **infinite loop** where your program never ends.</span></span> <span data-ttu-id="dc08c-181">Bu örnekte gösterilmediği için, programınızı **CTRL-C** veya başka yollarla çıkmaya zorlamaya zorlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="dc08c-181">That is not demonstrated in this sample, because you have to force your program to quit using **CTRL-C** or other means.</span></span>

<span data-ttu-id="dc08c-182">`while` Döngü ,`while`sonrasında kodu yürütmeden önce koşulu sınar.</span><span class="sxs-lookup"><span data-stu-id="dc08c-182">The `while` loop tests the condition before executing the code following the `while`.</span></span> <span data-ttu-id="dc08c-183">`do` ... `while` döngü önce kodu yürütür ve sonra koşulu denetler.</span><span class="sxs-lookup"><span data-stu-id="dc08c-183">The `do` ... `while` loop executes the code first, and then checks the condition.</span></span> <span data-ttu-id="dc08c-184">Do while döngüsü aşağıdaki kodda gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="dc08c-184">The do while loop is shown in the following code:</span></span>

```csharp
int counter = 0;
do
{
    Console.WriteLine($"Hello World! The counter is {counter}");
    counter++;
} while (counter < 10);
```

<span data-ttu-id="dc08c-185">Bu `do` döngü ve önceki `while` döngü aynı çıktıyı üretir.</span><span class="sxs-lookup"><span data-stu-id="dc08c-185">This `do` loop and the earlier `while` loop produce the same output.</span></span>

## <a name="work-with-the-for-loop"></a><span data-ttu-id="dc08c-186">For döngüsü ile çalışma</span><span class="sxs-lookup"><span data-stu-id="dc08c-186">Work with the for loop</span></span>

<span data-ttu-id="dc08c-187">**For** döngüsü genellikle ' de C#kullanılır.</span><span class="sxs-lookup"><span data-stu-id="dc08c-187">The **for** loop is commonly used in C#.</span></span> <span data-ttu-id="dc08c-188">Main () yönteminde bu kodu deneyin:</span><span class="sxs-lookup"><span data-stu-id="dc08c-188">Try this code in your Main() method:</span></span>

```csharp
for (int index = 0; index < 10; index++)
{
    Console.WriteLine($"Hello World! The index is {index}");
}
```

<span data-ttu-id="dc08c-189">Bu, `while` döngüyle aynı çalışmayı `do` ve zaten kullandığınız döngüyü yapar.</span><span class="sxs-lookup"><span data-stu-id="dc08c-189">This does the same work as the `while` loop and the `do` loop you've already used.</span></span> <span data-ttu-id="dc08c-190">`for` İfadesinin nasıl çalıştığını denetleyen üç bölümü vardır.</span><span class="sxs-lookup"><span data-stu-id="dc08c-190">The `for` statement has three parts that control how it works.</span></span>

<span data-ttu-id="dc08c-191">İlk bölüm **for başlatıcıdır**: `int index = 0;` Loop değişkeni olduğunu bildirir `index` ve başlangıç değerini olarak `0`ayarlar.</span><span class="sxs-lookup"><span data-stu-id="dc08c-191">The first part is the **for initializer**: `int index = 0;` declares that `index` is the loop variable, and sets its initial value to `0`.</span></span>

<span data-ttu-id="dc08c-192">Orta kısım **for koşuludur**: `index < 10` sayacın değeri 10 ' dan `for` az olduğu sürece bu döngünün yürütülmeye devam ettiğini bildirir.</span><span class="sxs-lookup"><span data-stu-id="dc08c-192">The middle part is the **for condition**: `index < 10` declares that this `for` loop continues to execute as long as the value of counter is less than 10.</span></span>

<span data-ttu-id="dc08c-193">Son bölüm, **Yineleyici için**: `index++` `for` deyimden sonra blok yürütüldükten sonra döngü değişkeninin nasıl değiştirileceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="dc08c-193">The final part is the **for iterator**: `index++` specifies how to modify the loop variable after executing the block following the `for` statement.</span></span> <span data-ttu-id="dc08c-194">Burada, blok her yürütüldüğünde `index` 1 ' in artırılabilmelidir.</span><span class="sxs-lookup"><span data-stu-id="dc08c-194">Here, it specifies that `index` should be incremented by 1 each time the block executes.</span></span>

<span data-ttu-id="dc08c-195">Bunlarla deneyin.</span><span class="sxs-lookup"><span data-stu-id="dc08c-195">Experiment with these yourself.</span></span> <span data-ttu-id="dc08c-196">Aşağıdakilerin her birini deneyin:</span><span class="sxs-lookup"><span data-stu-id="dc08c-196">Try each of the following:</span></span>

- <span data-ttu-id="dc08c-197">Başlatıcıyı farklı bir değerle başlayacak şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="dc08c-197">Change the initializer to start at a different value.</span></span>
- <span data-ttu-id="dc08c-198">Koşulu, farklı bir değerde durdurulacak şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="dc08c-198">Change the condition to stop at a different value.</span></span>

<span data-ttu-id="dc08c-199">İşiniz bittiğinde, öğrendiklerinizi kullanmak için kendinize bir kod yazmak üzere ilerlim.</span><span class="sxs-lookup"><span data-stu-id="dc08c-199">When you're done, let's move on to write some code yourself to use what you've learned.</span></span>

## <a name="combine-branches-and-loops"></a><span data-ttu-id="dc08c-200">Dalları ve döngüleri birleştirme</span><span class="sxs-lookup"><span data-stu-id="dc08c-200">Combine branches and loops</span></span>

<span data-ttu-id="dc08c-201">Artık, ve içindeki `if` C# döngü yapılarını gördüğünüze göre, 3 ' e bölünebilen 1 ile 20 arasındaki C# tüm tamsayıların toplamını bulmak için kod yazıp yazbileceğinizi görün.</span><span class="sxs-lookup"><span data-stu-id="dc08c-201">Now that you've seen the `if` statement and the looping constructs in the C# language, see if you can write C# code to find the sum of all integers 1 through 20 that are divisible by 3.</span></span>  <span data-ttu-id="dc08c-202">İşte birkaç ipucu:</span><span class="sxs-lookup"><span data-stu-id="dc08c-202">Here are a few hints:</span></span>

- <span data-ttu-id="dc08c-203">`%` İşleci, bir bölme işleminin kalanını verir.</span><span class="sxs-lookup"><span data-stu-id="dc08c-203">The `%` operator gives you the remainder of a division operation.</span></span>
- <span data-ttu-id="dc08c-204">`if` İfade, bir sayının toplamın bir parçası olup olmadığını görmek için koşul sağlar.</span><span class="sxs-lookup"><span data-stu-id="dc08c-204">The `if` statement gives you the condition to see if a number should be part of the sum.</span></span>
- <span data-ttu-id="dc08c-205">`for` Döngü, 1 ile 20 arasındaki tüm sayılar için bir dizi adımı yinelemenize yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="dc08c-205">The `for` loop can help you repeat a series of steps for all the numbers 1 through 20.</span></span>

<span data-ttu-id="dc08c-206">Kendiniz deneyin.</span><span class="sxs-lookup"><span data-stu-id="dc08c-206">Try it yourself.</span></span> <span data-ttu-id="dc08c-207">Sonra nasıl yapıldığını kontrol edin.</span><span class="sxs-lookup"><span data-stu-id="dc08c-207">Then check how you did.</span></span> <span data-ttu-id="dc08c-208">Yanıt için 63 almalısınız.</span><span class="sxs-lookup"><span data-stu-id="dc08c-208">You should get 63 for an answer.</span></span> <span data-ttu-id="dc08c-209">[GitHub 'da tamamlanan kodu görüntüleyerek](https://github.com/dotnet/samples/tree/master/csharp/branches-quickstart/Program.cs#L46-L54)olası bir yanıt görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dc08c-209">You can see one possible answer by [viewing the completed code on GitHub](https://github.com/dotnet/samples/tree/master/csharp/branches-quickstart/Program.cs#L46-L54).</span></span>

<span data-ttu-id="dc08c-210">"Dallar ve döngüler" öğreticisini tamamladınız.</span><span class="sxs-lookup"><span data-stu-id="dc08c-210">You've completed the "branches and loops" tutorial.</span></span>

<span data-ttu-id="dc08c-211">Kendi geliştirme ortamınızda [diziler ve koleksiyonlar](arrays-and-collections.md) öğreticisiyle devam edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dc08c-211">You can continue with the [Arrays and collections](arrays-and-collections.md) tutorial in your own development environment.</span></span>

<span data-ttu-id="dc08c-212">Bu kavramlar hakkında daha fazla bilgi için aşağıdaki konulara bakın:</span><span class="sxs-lookup"><span data-stu-id="dc08c-212">You can learn more about these concepts in these topics:</span></span>

- [<span data-ttu-id="dc08c-213">If ve Else deyimleri</span><span class="sxs-lookup"><span data-stu-id="dc08c-213">If and else statement</span></span>](../../language-reference/keywords/if-else.md)
- [<span data-ttu-id="dc08c-214">While ekstresi</span><span class="sxs-lookup"><span data-stu-id="dc08c-214">While statement</span></span>](../../language-reference/keywords/while.md)
- [<span data-ttu-id="dc08c-215">Do ekstresi</span><span class="sxs-lookup"><span data-stu-id="dc08c-215">Do statement</span></span>](../../language-reference/keywords/do.md)
- [<span data-ttu-id="dc08c-216">For deyimleri</span><span class="sxs-lookup"><span data-stu-id="dc08c-216">For statement</span></span>](../../language-reference/keywords/for.md)
