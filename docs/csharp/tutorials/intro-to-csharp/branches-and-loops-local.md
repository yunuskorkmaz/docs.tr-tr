---
title: Dallar ve döngüler - Giriş C# Öğreticisi
description: Dallar ve döngüler hakkındaki Bu öğreticide, yazdığınız C# koşullu dallar ve döngüler deyimleri tekrar tekrar yürütmenin destekleyen dili sözdizimi keşfetmek için kod.
ms.date: 10/31/2017
ms.custom: mvc
ms.openlocfilehash: c9e2ede3ee8632304a86efdf25bb2a8db5354a13
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2019
ms.locfileid: "57677792"
---
# <a name="learn-conditional-logic-with-branch-and-loop-statements"></a><span data-ttu-id="f4017-103">Dal ve döngü deyimleriyle koşullu mantık öğrenin</span><span class="sxs-lookup"><span data-stu-id="f4017-103">Learn conditional logic with branch and loop statements</span></span>

<span data-ttu-id="f4017-104">Bu öğretici size değişkenleri araştıran ve yürütme yolunu Bu değişkenlere göre değiştiren bir kodun nasıl yazılacağını öğretir.</span><span class="sxs-lookup"><span data-stu-id="f4017-104">This tutorial teaches you how to write code that examines variables and changes the execution path based on those variables.</span></span> <span data-ttu-id="f4017-105">C# kodu yazacak ve derleyerek ve çalıştırarak bunu sonuçlarını göreceksiniz.</span><span class="sxs-lookup"><span data-stu-id="f4017-105">You write C# code and see the results of compiling and running it.</span></span> <span data-ttu-id="f4017-106">Öğreticiyi içeren bir dizi, dallanma ve döngü yapıları içindeki keşfedin Ders C#.</span><span class="sxs-lookup"><span data-stu-id="f4017-106">The tutorial contains a series of lessons that explore branching and looping constructs in C#.</span></span> <span data-ttu-id="f4017-107">Bu dersler size C# dilinin temellerini öğretin.</span><span class="sxs-lookup"><span data-stu-id="f4017-107">These lessons teach you the fundamentals of the C# language.</span></span>

<span data-ttu-id="f4017-108">Bu öğretici geliştirme için kullanabileceğiniz bir makine olmasını bekliyor.</span><span class="sxs-lookup"><span data-stu-id="f4017-108">This tutorial expects you to have a machine you can use for development.</span></span> <span data-ttu-id="f4017-109">.NET konu [10 dakika içinde kullanmaya başla](https://www.microsoft.com/net/core) Mac, PC veya Linux üzerinde yerel geliştirme ortamınızı ayarlamaya yönelik yönergeler içerir.</span><span class="sxs-lookup"><span data-stu-id="f4017-109">The .NET topic [Get Started in 10 minutes](https://www.microsoft.com/net/core) has instructions for setting up your local development environment on Mac, PC or Linux.</span></span> <span data-ttu-id="f4017-110">Kullandığınız hesap komutları hızlı bir genel bakış yer [geliştirme araçları ile aşina](local-environment.md) daha ayrıntılı bilgi için bağlantılarla birlikte.</span><span class="sxs-lookup"><span data-stu-id="f4017-110">A quick overview of the commands you'll use is in the [Become familiar with the development tools](local-environment.md) with links to more details.</span></span>

## <a name="make-decisions-using-the-if-statement"></a><span data-ttu-id="f4017-111">Kullanarak kararlar `if` deyimi</span><span class="sxs-lookup"><span data-stu-id="f4017-111">Make decisions using the `if` statement</span></span>

<span data-ttu-id="f4017-112">Adlı bir dizin oluşturmak **dalları-tutorial**.</span><span class="sxs-lookup"><span data-stu-id="f4017-112">Create a directory named **branches-tutorial**.</span></span> <span data-ttu-id="f4017-113">Geçerli dizin ve çalışma olun `dotnet new console -n BranchesAndLoops -o .`.</span><span class="sxs-lookup"><span data-stu-id="f4017-113">Make that the current directory and run `dotnet new console -n BranchesAndLoops -o .`.</span></span> <span data-ttu-id="f4017-114">Bu komut geçerli dizinde yeni bir .NET Core konsol uygulaması oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f4017-114">This command creates a new .NET Core console application in the current directory.</span></span>

<span data-ttu-id="f4017-115">Açık **Program.cs** satırı değiştirin ve tercih ettiğiniz düzenleyiciyi `Console.WriteLine("Hello World!");` aşağıdaki kod ile:</span><span class="sxs-lookup"><span data-stu-id="f4017-115">Open **Program.cs** in your favorite editor, and replace the line `Console.WriteLine("Hello World!");` with the following code:</span></span>

```csharp
int a = 5;
int b = 6;
if (a + b > 10)
    Console.WriteLine("The answer is greater than 10.");
```

<span data-ttu-id="f4017-116">Bu kod yazarak deneme `dotnet run` konsol pencerenizde.</span><span class="sxs-lookup"><span data-stu-id="f4017-116">Try this code by typing `dotnet run` in your console window.</span></span> <span data-ttu-id="f4017-117">"Yanıt 10'dan büyük sağlıyor." iletisini görmeniz gerekir</span><span class="sxs-lookup"><span data-stu-id="f4017-117">You should see the message "The answer is greater than 10."</span></span> <span data-ttu-id="f4017-118">konsolunuza yazdırılmasını.</span><span class="sxs-lookup"><span data-stu-id="f4017-118">printed to your console.</span></span>

<span data-ttu-id="f4017-119">Değiştirin `b` böylece toplam 10'dan küçük:</span><span class="sxs-lookup"><span data-stu-id="f4017-119">Modify the declaration of `b` so that the sum is less than 10:</span></span>

```csharp
int b = 3;
```

<span data-ttu-id="f4017-120">Tür `dotnet run` yeniden.</span><span class="sxs-lookup"><span data-stu-id="f4017-120">Type `dotnet run` again.</span></span> <span data-ttu-id="f4017-121">Yanıt 10'dan küçük olduğundan herhangi bir şey yazdırılmaz.</span><span class="sxs-lookup"><span data-stu-id="f4017-121">Because the answer is less than 10, nothing is printed.</span></span> <span data-ttu-id="f4017-122">**Koşul** olduğunuz test değer false.</span><span class="sxs-lookup"><span data-stu-id="f4017-122">The **condition** you're testing is false.</span></span> <span data-ttu-id="f4017-123">İçin olası dallardan birine yalnızca yazdığınız yürütülecek herhangi bir kodu olmayan bir `if` deyimi: true dalı.</span><span class="sxs-lookup"><span data-stu-id="f4017-123">You don't have any code to execute because you've only written one of the possible branches for an `if` statement: the true branch.</span></span>

> [!TIP]
> <span data-ttu-id="f4017-124">C# (veya herhangi bir programlama dilini) keşfederken, kod yazdığınızda hatalar yapacaksınız.</span><span class="sxs-lookup"><span data-stu-id="f4017-124">As you explore C# (or any programming language), you'll make mistakes when you write code.</span></span> <span data-ttu-id="f4017-125">Derleyici, bulun ve hataları bildirin.</span><span class="sxs-lookup"><span data-stu-id="f4017-125">The compiler will find and report the errors.</span></span> <span data-ttu-id="f4017-126">Hata çıkış ve hatayı oluşturan kodu yakından bakın.</span><span class="sxs-lookup"><span data-stu-id="f4017-126">Look closely at the error output and the code that generated the error.</span></span> <span data-ttu-id="f4017-127">Derleyici Hatası genellikle sorun bulmanıza yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="f4017-127">The compiler error can usually help you find the problem.</span></span>

<span data-ttu-id="f4017-128">İlk örnek gücünü gösterir `if` ve Boole türlerini.</span><span class="sxs-lookup"><span data-stu-id="f4017-128">This first sample shows the power of `if` and Boolean types.</span></span> <span data-ttu-id="f4017-129">A *Boole* iki değerden birine sahip olabilen bir değişkendir: `true` veya `false`.</span><span class="sxs-lookup"><span data-stu-id="f4017-129">A *Boolean* is a variable that can have one of two values: `true` or `false`.</span></span> <span data-ttu-id="f4017-130">C#özel bir tür tanımlar `bool` Boole değişkenleri için.</span><span class="sxs-lookup"><span data-stu-id="f4017-130">C# defines a special type, `bool` for Boolean variables.</span></span> <span data-ttu-id="f4017-131">`if` Deyimi değerini denetler bir `bool`.</span><span class="sxs-lookup"><span data-stu-id="f4017-131">The `if` statement checks the value of a `bool`.</span></span> <span data-ttu-id="f4017-132">Değer olduğunda `true`, sonrasındaki deyime `if` yürütür.</span><span class="sxs-lookup"><span data-stu-id="f4017-132">When the value is `true`, the statement following the `if` executes.</span></span> <span data-ttu-id="f4017-133">Aksi halde atlanır.</span><span class="sxs-lookup"><span data-stu-id="f4017-133">Otherwise, it is skipped.</span></span>

<span data-ttu-id="f4017-134">Koşulları kontrol etmek ve bu koşullara göre deyimleri yürütmek için gerçekleştirilen bu işlem son derece etkilidir.</span><span class="sxs-lookup"><span data-stu-id="f4017-134">This process of checking conditions and executing statements based on those conditions is very powerful.</span></span>

## <a name="make-if-and-else-work-together"></a><span data-ttu-id="f4017-135">İf ve else koşullarını birlikte</span><span class="sxs-lookup"><span data-stu-id="f4017-135">Make if and else work together</span></span>

<span data-ttu-id="f4017-136">Hem true hem de false dallarında farklı kod yürütmek için oluşturduğunuz bir `else` dalı, koşul false olduğunda yürütür.</span><span class="sxs-lookup"><span data-stu-id="f4017-136">To execute different code in both the true and false branches, you create an `else` branch that executes when the condition is false.</span></span> <span data-ttu-id="f4017-137">Bu deneyin.</span><span class="sxs-lookup"><span data-stu-id="f4017-137">Try this.</span></span> <span data-ttu-id="f4017-138">Aşağıdaki kodda için son iki satırı ekleyin, `Main` yöntemi (zaten ilk dört):</span><span class="sxs-lookup"><span data-stu-id="f4017-138">Add the last two lines in the code below to your `Main` method (you should already have the first four):</span></span>

```csharp
int a = 5;
int b = 3;
if (a + b > 10)
    Console.WriteLine("The answer is greater than 10");
else
    Console.WriteLine("The answer is not greater than 10");
```

<span data-ttu-id="f4017-139">Deyim `else` anahtar sözcüğü, yalnızca test edilen koşul olduğunda yürütür `false`.</span><span class="sxs-lookup"><span data-stu-id="f4017-139">The statement following the `else` keyword executes only when the condition being tested is `false`.</span></span> <span data-ttu-id="f4017-140">Birleştirme `if` ve `else` Boole koşullarıyla koşullar sağlar hem de işlemek için ihtiyacınız olan tüm etkiyi bir `true` ve `false` koşul.</span><span class="sxs-lookup"><span data-stu-id="f4017-140">Combining `if` and `else` with Boolean conditions provides all the power you need to handle both a `true` and a `false` condition.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f4017-141">Altındaki girinti `if` ve `else` deyimleri, İnsan okuyuculara yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="f4017-141">The indentation under the `if` and `else` statements is for human readers.</span></span>
> <span data-ttu-id="f4017-142">C# dili girintileri veya boşlukları olarak önemli kabul etmez.</span><span class="sxs-lookup"><span data-stu-id="f4017-142">The C# language doesn't treat indentation or white space as significant.</span></span>
> <span data-ttu-id="f4017-143">Deyim `if` veya `else` anahtar sözcüğü, bir koşula göre yürütülecek.</span><span class="sxs-lookup"><span data-stu-id="f4017-143">The statement following the `if` or `else` keyword will be executed based on the condition.</span></span> <span data-ttu-id="f4017-144">Bu öğreticideki tüm örnekler üzerinde deyimlerin denetim akışına bağlı olarak satır girintilemenin sık kullanılan bir yöntemini uygulayın.</span><span class="sxs-lookup"><span data-stu-id="f4017-144">All the samples in this tutorial follow a common practice to indent lines based on the control flow of statements.</span></span>

<span data-ttu-id="f4017-145">Girinti önemli olmadığı için kullanmanız gerekir `{` ve `}` koşullu olarak yürütülen bloğun parçası olarak birden fazla deyim istediğinizde belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="f4017-145">Because indentation is not significant, you need to use `{` and `}` to indicate when you want more than one statement to be part of the block that executes conditionally.</span></span> <span data-ttu-id="f4017-146">C# programcıları genellikle kullanır Bu ayraçları tüm `if` ve `else` yan tümceleri.</span><span class="sxs-lookup"><span data-stu-id="f4017-146">C# programmers typically use those braces on all `if` and `else` clauses.</span></span> <span data-ttu-id="f4017-147">Aşağıdaki örnek, oluşturduğunuz bir ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="f4017-147">The following example is the same as the one you just created.</span></span> <span data-ttu-id="f4017-148">Aşağıdaki kod eşleştirmek için yukarıdaki kodunuzu değiştirin:</span><span class="sxs-lookup"><span data-stu-id="f4017-148">Modify your code above to match the following code:</span></span>

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
> <span data-ttu-id="f4017-149">Bu öğreticinin geri kalanını, sonraki küme ayraçlarını, tüm kod örnekleri dahil kabul edilen yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="f4017-149">Through the rest of this tutorial, the code samples all include the braces, following accepted practices.</span></span>

<span data-ttu-id="f4017-150">Daha karmaşık koşulları test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f4017-150">You can test more complicated conditions.</span></span> <span data-ttu-id="f4017-151">Aşağıdaki kodu ekleyin, `Main` yöntemi, şimdiye yazılan koddan sonra:</span><span class="sxs-lookup"><span data-stu-id="f4017-151">Add the following code in your `Main` method after the code you've written so far:</span></span>

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

<span data-ttu-id="f4017-152">`&&` Temsil eder "ve".</span><span class="sxs-lookup"><span data-stu-id="f4017-152">The `&&` represents "and".</span></span> <span data-ttu-id="f4017-153">Bu koşulların her ikisi de deyimi true dalında yürütmek için true anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="f4017-153">It means both conditions must be true to execute the statement in the true branch.</span></span>  <span data-ttu-id="f4017-154">İçine alınmaları koşuluyla her koşullu dalda birden çok deyime sahip bu örnek ayrıca Göster `{` ve `}`.</span><span class="sxs-lookup"><span data-stu-id="f4017-154">These examples also show that you can have multiple statements in each conditional branch, provided you enclose them in `{` and `}`.</span></span>

<span data-ttu-id="f4017-155">Ayrıca `||` temsil etmek için "veya".</span><span class="sxs-lookup"><span data-stu-id="f4017-155">You can also use  `||` to represent "or".</span></span> <span data-ttu-id="f4017-156">Şu ana kadar yazdıklarınızı sonra aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="f4017-156">Add the following code after what you've written so far:</span></span>

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

<span data-ttu-id="f4017-157">İlk adımı tamamladınız.</span><span class="sxs-lookup"><span data-stu-id="f4017-157">You've finished the first step.</span></span> <span data-ttu-id="f4017-158">Sonraki bölümde başlamadan önce geçerli kodu ayrı bir yöntem geçelim.</span><span class="sxs-lookup"><span data-stu-id="f4017-158">Before you start the next section, let's move the current code into a separate method.</span></span> <span data-ttu-id="f4017-159">Bu, yeni bir örnek ile çalışmaya başlamak kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="f4017-159">That makes it easier to start working with a new example.</span></span> <span data-ttu-id="f4017-160">Yeniden adlandırma, `Main` yönteme `ExploreIf` ve yeni bir yazma `Main` metoduna çağrı yapan `ExploreIf`.</span><span class="sxs-lookup"><span data-stu-id="f4017-160">Rename your `Main` method to `ExploreIf` and write a new `Main` method that calls `ExploreIf`.</span></span> <span data-ttu-id="f4017-161">İşiniz bittiğinde, kodunuzun şu şekilde görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="f4017-161">When you have finished, your code should look like this:</span></span>

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

<span data-ttu-id="f4017-162">Çağrı yorum `ExploreIf()`.</span><span class="sxs-lookup"><span data-stu-id="f4017-162">Comment out the call to `ExploreIf()`.</span></span> <span data-ttu-id="f4017-163">Bu, bu bölümde çalışırken daha az dağınıktır çıkış yapar:</span><span class="sxs-lookup"><span data-stu-id="f4017-163">It will make the output less cluttered as you work in this section:</span></span>

```csharp
//ExploreIf();
```

<span data-ttu-id="f4017-164">`//` Başlatan bir **yorum** içinde C#.</span><span class="sxs-lookup"><span data-stu-id="f4017-164">The `//` starts a **comment** in C#.</span></span> <span data-ttu-id="f4017-165">Kaynak kodunuzu korumakla birlikte kod olarak yürütmeme istediğiniz herhangi bir metin açıklamaları bulunmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f4017-165">Comments are any text you want to keep in your source code but not execute as code.</span></span> <span data-ttu-id="f4017-166">Derleyicinin açıklamaları herhangi bir yürütülebilir kod oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="f4017-166">The compiler does not generate any executable code from comments.</span></span>

## <a name="use-loops-to-repeat-operations"></a><span data-ttu-id="f4017-167">İşlemleri yinelemek için döngüleri kullanma</span><span class="sxs-lookup"><span data-stu-id="f4017-167">Use loops to repeat operations</span></span>

<span data-ttu-id="f4017-168">Bu bölümde kullandığınız **döngüler** deyimleri yinelemek için.</span><span class="sxs-lookup"><span data-stu-id="f4017-168">In this section you use **loops** to repeat statements.</span></span> <span data-ttu-id="f4017-169">Bu kodu deneyin, `Main` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="f4017-169">Try this code in your `Main` method:</span></span>

```csharp
int counter = 0;
while (counter < 10)
{
    Console.WriteLine($"Hello World! The counter is {counter}");
    counter++;
}
```

<span data-ttu-id="f4017-170">`while` Deyimi bir koşulu kontrol eder ve deyimi veya deyim bloğunu izleyen yürütür `while`.</span><span class="sxs-lookup"><span data-stu-id="f4017-170">The `while` statement checks a condition and executes the statement or statement block following the `while`.</span></span> <span data-ttu-id="f4017-171">Art arda koşulu ve koşul false olana kadar bu deyimleri yürütmeyi denetler.</span><span class="sxs-lookup"><span data-stu-id="f4017-171">It repeatedly checks the condition and executing those statements until the condition is false.</span></span>

<span data-ttu-id="f4017-172">Bu örnekte diğer bir yeni işleç yoktur.</span><span class="sxs-lookup"><span data-stu-id="f4017-172">There's one other new operator in this example.</span></span> <span data-ttu-id="f4017-173">`++` Sonra `counter` değişkendir **artışı** işleci.</span><span class="sxs-lookup"><span data-stu-id="f4017-173">The `++` after the `counter` variable is the **increment** operator.</span></span> <span data-ttu-id="f4017-174">Değerine 1 ekler `counter` ve değeri depolar `counter` değişkeni.</span><span class="sxs-lookup"><span data-stu-id="f4017-174">It adds 1 to the value of `counter` and stores that value in the `counter` variable.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f4017-175">Emin olun `while` siz kodu yürütürken gibi Döngü koşulu değişiklikleri false.</span><span class="sxs-lookup"><span data-stu-id="f4017-175">Make sure that the `while` loop condition changes to false as you execute the code.</span></span> <span data-ttu-id="f4017-176">Aksi halde, oluşturduğunuz bir **sonsuz döngü** programınızı hiçbir zaman sona ereceği.</span><span class="sxs-lookup"><span data-stu-id="f4017-176">Otherwise, you create an **infinite loop** where your program never ends.</span></span> <span data-ttu-id="f4017-177">Bu değil gösterilmiştir Bu örnekte, programınızı kullanarak çıkmak için zorlamak sahip olduğunuz için **CTRL-C** veya diğer anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="f4017-177">That is not demonstrated in this sample, because you have to force your program to quit using **CTRL-C** or other means.</span></span>

<span data-ttu-id="f4017-178">`while` Döngü, sonraki kodu yürütmeden önce koşulu test eder `while`.</span><span class="sxs-lookup"><span data-stu-id="f4017-178">The `while` loop tests the condition before executing the code following the `while`.</span></span> <span data-ttu-id="f4017-179">`do` ... `while` döngüsü önce kodu yürütür ve sonra koşulu kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="f4017-179">The `do` ... `while` loop executes the code first, and then checks the condition.</span></span> <span data-ttu-id="f4017-180">Döngü, aşağıdaki kodda gösterilen sırada yapın:</span><span class="sxs-lookup"><span data-stu-id="f4017-180">The do while loop is shown in the following code:</span></span>

```csharp
counter = 0;
do
{
    Console.WriteLine($"Hello World! The counter is {counter}");
    counter++;
} while (counter < 10);
```

<span data-ttu-id="f4017-181">Bu `do` döngüsü ve önceki `while` döngü, aynı çıktı üretir.</span><span class="sxs-lookup"><span data-stu-id="f4017-181">This `do` loop and the earlier `while` loop produce the same output.</span></span>

## <a name="work-with-the-for-loop"></a><span data-ttu-id="f4017-182">Çalışmak for döngüsü</span><span class="sxs-lookup"><span data-stu-id="f4017-182">Work with the for loop</span></span>

<span data-ttu-id="f4017-183">**İçin** döngü kullanılan yaygın olarak C#.</span><span class="sxs-lookup"><span data-stu-id="f4017-183">The **for** loop is commonly used in C#.</span></span> <span data-ttu-id="f4017-184">Bu kodu Main() yönteminizde deneyin:</span><span class="sxs-lookup"><span data-stu-id="f4017-184">Try this code in your Main() method:</span></span>

```csharp
for(int index = 0; index < 10; index++)
{
    Console.WriteLine($"Hello World! The index is {index}");
}
```

<span data-ttu-id="f4017-185">Bu aynı işlevi görür `while` döngü ve `do` zaten kullandığınız döngü.</span><span class="sxs-lookup"><span data-stu-id="f4017-185">This does the same work as the `while` loop and the `do` loop you've already used.</span></span> <span data-ttu-id="f4017-186">`for` Deyimi nasıl çalıştığını denetleyen üç bölümü vardır.</span><span class="sxs-lookup"><span data-stu-id="f4017-186">The `for` statement has three parts that control how it works.</span></span>

<span data-ttu-id="f4017-187">İlk bölüm **for başlatıcısıdır**: `int index = 0;` bildiren `index` Döngü değişkeninin ve bunun başlangıçtaki değerini ayarlar `0`.</span><span class="sxs-lookup"><span data-stu-id="f4017-187">The first part is the **for initializer**: `int index = 0;` declares that `index` is the loop variable, and sets its initial value to `0`.</span></span>

<span data-ttu-id="f4017-188">Ortadaki bölüm **koşulu**: `index < 10` bildirir bu `for` döngü sayacının değerini 10'dan az olduğu sürece yürütülmeye devam eder.</span><span class="sxs-lookup"><span data-stu-id="f4017-188">The middle part is the **for condition**: `index < 10` declares that this `for` loop continues to execute as long as the value of counter is less than 10.</span></span>

<span data-ttu-id="f4017-189">Son bölüm ise **yineleyici için**: `index++` nasıl blok yürütüldükten sonra Döngü değişkeninin değiştirileceğini belirtir `for` deyimi.</span><span class="sxs-lookup"><span data-stu-id="f4017-189">The final part is the **for iterator**: `index++` specifies how to modify the loop variable after executing the block following the `for` statement.</span></span> <span data-ttu-id="f4017-190">Burada, belirtir `index` bloğun her zaman 1 tarafından arttırılarak.</span><span class="sxs-lookup"><span data-stu-id="f4017-190">Here, it specifies that `index` should be incremented by 1 each time the block executes.</span></span>

<span data-ttu-id="f4017-191">Bunları kendiniz deneyin.</span><span class="sxs-lookup"><span data-stu-id="f4017-191">Experiment with these yourself.</span></span> <span data-ttu-id="f4017-192">Her birini deneyin:</span><span class="sxs-lookup"><span data-stu-id="f4017-192">Try each of the following:</span></span>

- <span data-ttu-id="f4017-193">Farklı bir değerde başlamak için başlatıcıyı değiştirin.</span><span class="sxs-lookup"><span data-stu-id="f4017-193">Change the initializer to start at a different value.</span></span>
- <span data-ttu-id="f4017-194">Farklı bir değerde durmak için koşulu değiştirin.</span><span class="sxs-lookup"><span data-stu-id="f4017-194">Change the condition to stop at a different value.</span></span>

<span data-ttu-id="f4017-195">İşiniz bittiğinde yazma adımına geçelim bazı öğrendikleriniz kullanılacak kodunu kendiniz.</span><span class="sxs-lookup"><span data-stu-id="f4017-195">When you're done, let's move on to write some code yourself to use what you've learned.</span></span>

## <a name="combine-branches-and-loops"></a><span data-ttu-id="f4017-196">Dalları ve döngüleri birleştirme</span><span class="sxs-lookup"><span data-stu-id="f4017-196">Combine branches and loops</span></span>

<span data-ttu-id="f4017-197">Gördüğünüze göre `if` deyimini ve döngü yapılarını C# dil bkz 1 ile 3 ile bölünebilen 20 tüm tamsayıların toplamını bulmak için C# kodu yazacak.</span><span class="sxs-lookup"><span data-stu-id="f4017-197">Now that you've seen the `if` statement and the looping constructs in the C# language, see if you can write C# code to find the sum of all integers 1 through 20 that are divisible by 3.</span></span>  <span data-ttu-id="f4017-198">Bazı ipuçları şunlardır:</span><span class="sxs-lookup"><span data-stu-id="f4017-198">Here are a few hints:</span></span>

- <span data-ttu-id="f4017-199">`%` İşleci size bölme işlemindeki kalanı verir.</span><span class="sxs-lookup"><span data-stu-id="f4017-199">The `%` operator gives you the remainder of a division operation.</span></span>
- <span data-ttu-id="f4017-200">`if` Deyimi bir sayı toplamı parçası olup olmayacağını görmek için koşul sağlar.</span><span class="sxs-lookup"><span data-stu-id="f4017-200">The `if` statement gives you the condition to see if a number should be part of the sum.</span></span>
- <span data-ttu-id="f4017-201">`for` Yinelemenize yardımcı olur, 20'den sayılar 1 için bir dizi adımı yineleyin.</span><span class="sxs-lookup"><span data-stu-id="f4017-201">The `for` loop can help you repeat a series of steps for all the numbers 1 through 20.</span></span>

<span data-ttu-id="f4017-202">Kendiniz deneyin.</span><span class="sxs-lookup"><span data-stu-id="f4017-202">Try it yourself.</span></span> <span data-ttu-id="f4017-203">Ardından olup olmadığınıza bakın.</span><span class="sxs-lookup"><span data-stu-id="f4017-203">Then check how you did.</span></span> <span data-ttu-id="f4017-204">63 için bir yanıt almanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="f4017-204">You should get 63 for an answer.</span></span> <span data-ttu-id="f4017-205">Olası bir yanıt olarak gördüğünüz [tamamlanan kodu Github'da görüntüleme](https://github.com/dotnet/samples/tree/master/csharp/branches-quickstart/Program.cs#L46-L54).</span><span class="sxs-lookup"><span data-stu-id="f4017-205">You can see one possible answer by [viewing the completed code on GitHub](https://github.com/dotnet/samples/tree/master/csharp/branches-quickstart/Program.cs#L46-L54).</span></span>

<span data-ttu-id="f4017-206">"Dallar ve döngüler" öğreticisini tamamladınız.</span><span class="sxs-lookup"><span data-stu-id="f4017-206">You've completed the "branches and loops" tutorial.</span></span>

<span data-ttu-id="f4017-207">İle devam edebilir [dize ilişkilendirme](interpolated-strings-local.md) kendi geliştirme ortamınızda öğretici.</span><span class="sxs-lookup"><span data-stu-id="f4017-207">You can continue with the [String interpolation](interpolated-strings-local.md) tutorial in your own development environment.</span></span>

<span data-ttu-id="f4017-208">Aşağıdaki konulardan Bu kavramlar hakkında daha fazla bilgi edinebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="f4017-208">You can learn more about these concepts in these topics:</span></span>

- [<span data-ttu-id="f4017-209">Varsa ve else deyimi</span><span class="sxs-lookup"><span data-stu-id="f4017-209">If and else statement</span></span>](../../language-reference/keywords/if-else.md)
- [<span data-ttu-id="f4017-210">while deyimi</span><span class="sxs-lookup"><span data-stu-id="f4017-210">While statement</span></span>](../../language-reference/keywords/while.md)
- [<span data-ttu-id="f4017-211">do deyimi</span><span class="sxs-lookup"><span data-stu-id="f4017-211">Do statement</span></span>](../../language-reference/keywords/do.md)
- [<span data-ttu-id="f4017-212">For deyimi</span><span class="sxs-lookup"><span data-stu-id="f4017-212">For statement</span></span>](../../language-reference/keywords/for.md)
