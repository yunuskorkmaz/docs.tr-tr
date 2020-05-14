---
title: Dallar ve döngüler-C# öğreticisine giriş
description: Dallar ve döngüler hakkında bu öğreticide, ifadeleri sürekli olarak yürütmek için koşullu dalları ve döngüleri destekleyen dil sözdizimini araştırmak üzere C# kodu yazarsınız.
ms.date: 10/31/2017
ms.custom: mvc
ms.openlocfilehash: d67cfe359634783bb542e9ac34df52a095b45c20
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396875"
---
# <a name="learn-conditional-logic-with-branch-and-loop-statements"></a><span data-ttu-id="3fb6f-103">Dal ve döngü deyimleri ile koşullu mantık öğrenin</span><span class="sxs-lookup"><span data-stu-id="3fb6f-103">Learn conditional logic with branch and loop statements</span></span>

<span data-ttu-id="3fb6f-104">Bu öğretici, değişkenleri inceleyen ve bu değişkenlere göre yürütme yolunu değiştiren bir kod yazmayı öğretir.</span><span class="sxs-lookup"><span data-stu-id="3fb6f-104">This tutorial teaches you how to write code that examines variables and changes the execution path based on those variables.</span></span> <span data-ttu-id="3fb6f-105">C# kodu yazar ve bunu derleyip çalıştırmanın sonuçlarını görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="3fb6f-105">You write C# code and see the results of compiling and running it.</span></span> <span data-ttu-id="3fb6f-106">Öğretici, C# ' de dallanma ve döngü yapılarını keşfetmenizi sağlayan bir dizi ders içerir.</span><span class="sxs-lookup"><span data-stu-id="3fb6f-106">The tutorial contains a series of lessons that explore branching and looping constructs in C#.</span></span> <span data-ttu-id="3fb6f-107">Bu dersler size C# dilinin temel özelliklerini öğretir.</span><span class="sxs-lookup"><span data-stu-id="3fb6f-107">These lessons teach you the fundamentals of the C# language.</span></span>

<span data-ttu-id="3fb6f-108">Bu öğreticide, geliştirme için kullanabileceğiniz bir makineniz olması beklenir.</span><span class="sxs-lookup"><span data-stu-id="3fb6f-108">This tutorial expects you to have a machine you can use for development.</span></span> <span data-ttu-id="3fb6f-109">[10 dakika içinde Merhaba Dünya](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) .NET öğreticisi, Windows, Linux veya MacOS 'ta yerel geliştirme ortamınızı ayarlamaya yönelik yönergeler içerir.</span><span class="sxs-lookup"><span data-stu-id="3fb6f-109">The .NET tutorial [Hello World in 10 minutes](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) has instructions for setting up your local development environment on Windows, Linux, or macOS.</span></span> <span data-ttu-id="3fb6f-110">Kullanacağınız komutlara hızlı bir genel bakış, daha fazla ayrıntı için bağlantılarla birlikte [geliştirme araçları hakkında bilgi sahibi olmaya gelmiştir](local-environment.md) .</span><span class="sxs-lookup"><span data-stu-id="3fb6f-110">A quick overview of the commands you'll use is in the [Become familiar with the development tools](local-environment.md) with links to more details.</span></span>

## <a name="make-decisions-using-the-if-statement"></a><span data-ttu-id="3fb6f-111">İfadesini kullanarak kararlar alın `if`</span><span class="sxs-lookup"><span data-stu-id="3fb6f-111">Make decisions using the `if` statement</span></span>

<span data-ttu-id="3fb6f-112">Dallar adlı bir dizin oluşturun *-öğretici*.</span><span class="sxs-lookup"><span data-stu-id="3fb6f-112">Create a directory named *branches-tutorial*.</span></span> <span data-ttu-id="3fb6f-113">Geçerli dizini yapın ve şu komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="3fb6f-113">Make that the current directory and run the following command:</span></span>

```dotnetcli
dotnet new console -n BranchesAndLoops -o .
```

<span data-ttu-id="3fb6f-114">Bu komut geçerli dizinde yeni bir .NET Core konsol uygulaması oluşturur.</span><span class="sxs-lookup"><span data-stu-id="3fb6f-114">This command creates a new .NET Core console application in the current directory.</span></span>

<span data-ttu-id="3fb6f-115">En sevdiğiniz düzenleyicide *program.cs* açın ve satırı `Console.WriteLine("Hello World!");` aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="3fb6f-115">Open *Program.cs* in your favorite editor, and replace the line `Console.WriteLine("Hello World!");` with the following code:</span></span>

```csharp
int a = 5;
int b = 6;
if (a + b > 10)
    Console.WriteLine("The answer is greater than 10.");
```

<span data-ttu-id="3fb6f-116">Konsol pencerenizi yazarak bu kodu deneyin `dotnet run` .</span><span class="sxs-lookup"><span data-stu-id="3fb6f-116">Try this code by typing `dotnet run` in your console window.</span></span> <span data-ttu-id="3fb6f-117">"Yanıt 10 ' dan büyük" iletisini görmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="3fb6f-117">You should see the message "The answer is greater than 10."</span></span> <span data-ttu-id="3fb6f-118">konsolunuza yazdırılır.</span><span class="sxs-lookup"><span data-stu-id="3fb6f-118">printed to your console.</span></span>

<span data-ttu-id="3fb6f-119">`b` tanımlamasını toplamın 10’dan küçük olacağı şekilde değiştirin:</span><span class="sxs-lookup"><span data-stu-id="3fb6f-119">Modify the declaration of `b` so that the sum is less than 10:</span></span>

```csharp
int b = 3;
```

<span data-ttu-id="3fb6f-120">`dotnet run`Yeniden yazın.</span><span class="sxs-lookup"><span data-stu-id="3fb6f-120">Type `dotnet run` again.</span></span> <span data-ttu-id="3fb6f-121">Yanıt 10’dan küçük olduğundan herhangi bir şey yazdırılmaz.</span><span class="sxs-lookup"><span data-stu-id="3fb6f-121">Because the answer is less than 10, nothing is printed.</span></span> <span data-ttu-id="3fb6f-122">Test ettiğiniz **koşul** false değerindedir.</span><span class="sxs-lookup"><span data-stu-id="3fb6f-122">The **condition** you're testing is false.</span></span> <span data-ttu-id="3fb6f-123">Bir `if` deyimi için olası dallardan yalnızca birini (true dalı) yazdığınızdan, yürütülecek herhangi bir kodunuz yoktur.</span><span class="sxs-lookup"><span data-stu-id="3fb6f-123">You don't have any code to execute because you've only written one of the possible branches for an `if` statement: the true branch.</span></span>

> [!TIP]
> <span data-ttu-id="3fb6f-124">C# dilini (veya herhangi bir programlama dilini) keşfederken, kod yazdığınızda hatalar yapacaksınız.</span><span class="sxs-lookup"><span data-stu-id="3fb6f-124">As you explore C# (or any programming language), you'll make mistakes when you write code.</span></span> <span data-ttu-id="3fb6f-125">Derleyici hataları bulacak ve rapor eder.</span><span class="sxs-lookup"><span data-stu-id="3fb6f-125">The compiler will find and report the errors.</span></span> <span data-ttu-id="3fb6f-126">Hata çıktısına ve hatayı oluşturan koda yakından bakın.</span><span class="sxs-lookup"><span data-stu-id="3fb6f-126">Look closely at the error output and the code that generated the error.</span></span> <span data-ttu-id="3fb6f-127">Derleyici hatası genellikle sorunu bulmanıza yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="3fb6f-127">The compiler error can usually help you find the problem.</span></span>

<span data-ttu-id="3fb6f-128">Bu ilk örnek, `if` ve Boolean türlerin gücünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="3fb6f-128">This first sample shows the power of `if` and Boolean types.</span></span> <span data-ttu-id="3fb6f-129">*Boolean* , iki değerden birine sahip olabilir bir değişkendir: `true` veya `false` .</span><span class="sxs-lookup"><span data-stu-id="3fb6f-129">A *Boolean* is a variable that can have one of two values: `true` or `false`.</span></span> <span data-ttu-id="3fb6f-130">C#, Boole değişkenleri için özel bir tür tanımlar `bool` .</span><span class="sxs-lookup"><span data-stu-id="3fb6f-130">C# defines a special type, `bool` for Boolean variables.</span></span> <span data-ttu-id="3fb6f-131">`if` deyimi bir `bool` için değeri kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="3fb6f-131">The `if` statement checks the value of a `bool`.</span></span> <span data-ttu-id="3fb6f-132">Değer `true` olduğunda, `if` deyiminden sonra gelen deyim yürütülür.</span><span class="sxs-lookup"><span data-stu-id="3fb6f-132">When the value is `true`, the statement following the `if` executes.</span></span> <span data-ttu-id="3fb6f-133">Aksi takdirde, atlanır.</span><span class="sxs-lookup"><span data-stu-id="3fb6f-133">Otherwise, it's skipped.</span></span>

<span data-ttu-id="3fb6f-134">Bu koşullara göre koşulları denetleme ve deyimleri yürütme işlemi güçlü bir işlemdir.</span><span class="sxs-lookup"><span data-stu-id="3fb6f-134">This process of checking conditions and executing statements based on those conditions is powerful.</span></span>

## <a name="make-if-and-else-work-together"></a><span data-ttu-id="3fb6f-135">if ve else koşullarını birlikte çalıştırma</span><span class="sxs-lookup"><span data-stu-id="3fb6f-135">Make if and else work together</span></span>

<span data-ttu-id="3fb6f-136">Hem true hem de false dallarında farklı kod yürütmek için, koşul false olduğunda yürütülen bir `else` dalı oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="3fb6f-136">To execute different code in both the true and false branches, you create an `else` branch that executes when the condition is false.</span></span> <span data-ttu-id="3fb6f-137">Bunu deneyin.</span><span class="sxs-lookup"><span data-stu-id="3fb6f-137">Try this.</span></span> <span data-ttu-id="3fb6f-138">Aşağıdaki kodda bulunan son iki satırı `Main` yöntemine ekleyin (ilk dördü zaten var olmalıdır):</span><span class="sxs-lookup"><span data-stu-id="3fb6f-138">Add the last two lines in the code below to your `Main` method (you should already have the first four):</span></span>

```csharp
int a = 5;
int b = 3;
if (a + b > 10)
    Console.WriteLine("The answer is greater than 10");
else
    Console.WriteLine("The answer is not greater than 10");
```

<span data-ttu-id="3fb6f-139">`else` anahtar sözcüğünden sonraki deyim, yalnızca test edilen koşul `false` olduğunda yürütülür.</span><span class="sxs-lookup"><span data-stu-id="3fb6f-139">The statement following the `else` keyword executes only when the condition being tested is `false`.</span></span> <span data-ttu-id="3fb6f-140">`if`Ve `else` Boolean koşulları ile birleştirmek, hem hem de bir koşulu işlemek için ihtiyacınız olan tüm gücü sağlar `true` `false` .</span><span class="sxs-lookup"><span data-stu-id="3fb6f-140">Combining `if` and `else` with Boolean conditions provides all the power you need to handle both a `true` and a `false` condition.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3fb6f-141">`if` ve `else` deyimlerinin altındaki girinti, insan okuyuculara yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="3fb6f-141">The indentation under the `if` and `else` statements is for human readers.</span></span>
> <span data-ttu-id="3fb6f-142">C# dili, girintileme veya boşluk olarak kabul etmez.</span><span class="sxs-lookup"><span data-stu-id="3fb6f-142">The C# language doesn't treat indentation or white space as significant.</span></span>
> <span data-ttu-id="3fb6f-143">`if` veya `else` anahtar sözcüğünden sonra gelen deyim, koşula bağlı olarak yürütülür.</span><span class="sxs-lookup"><span data-stu-id="3fb6f-143">The statement following the `if` or `else` keyword will be executed based on the condition.</span></span> <span data-ttu-id="3fb6f-144">Bu öğreticideki tüm örnekler, ifadelerin denetim akışına göre satırları girintilemek için ortak bir uygulama izler.</span><span class="sxs-lookup"><span data-stu-id="3fb6f-144">All the samples in this tutorial follow a common practice to indent lines based on the control flow of statements.</span></span>

<span data-ttu-id="3fb6f-145">Girintileme önemli olmadığından, `{` `}` çok sayıda deyimin koşullu olarak yürütülen bloğun bir parçası olmasını istediğiniz zaman göstermek için ve kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="3fb6f-145">Because indentation isn't significant, you need to use `{` and `}` to indicate when you want more than one statement to be part of the block that executes conditionally.</span></span> <span data-ttu-id="3fb6f-146">C# programcıları bu ayraçları genellikle tüm `if` and `else` tümcelerinde kullanır.</span><span class="sxs-lookup"><span data-stu-id="3fb6f-146">C# programmers typically use those braces on all `if` and `else` clauses.</span></span> <span data-ttu-id="3fb6f-147">Aşağıdaki örnek, oluşturduğunuz bir ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="3fb6f-147">The following example is the same as the one you created.</span></span> <span data-ttu-id="3fb6f-148">Yukarıdaki kodu aşağıdaki kodla eşleşecek şekilde değiştirin:</span><span class="sxs-lookup"><span data-stu-id="3fb6f-148">Modify your code above to match the following code:</span></span>

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
> <span data-ttu-id="3fb6f-149">Bu öğreticinin geri kalanında, kod örnekleri, kabul edilen uygulamaları takip eden ayraçları içerir.</span><span class="sxs-lookup"><span data-stu-id="3fb6f-149">Through the rest of this tutorial, the code samples all include the braces, following accepted practices.</span></span>

<span data-ttu-id="3fb6f-150">Daha karmaşık koşulları test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3fb6f-150">You can test more complicated conditions.</span></span> <span data-ttu-id="3fb6f-151">Şu `Main` ana kadar yazdığınız koddan sonra aşağıdaki kodu yöntemine ekleyin:</span><span class="sxs-lookup"><span data-stu-id="3fb6f-151">Add the following code in your `Main` method after the code you've written so far:</span></span>

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

<span data-ttu-id="3fb6f-152">`==` *Eşitlik*için simge testi.</span><span class="sxs-lookup"><span data-stu-id="3fb6f-152">The `==` symbol tests for *equality*.</span></span> <span data-ttu-id="3fb6f-153">`==`' Yi kullanarak, ' de gördüğünüz şekilde testi, atamanın eşitliğine ayırır `a = 5` .</span><span class="sxs-lookup"><span data-stu-id="3fb6f-153">Using `==` distinguishes the test for equality from assignment, which you saw in `a = 5`.</span></span>

<span data-ttu-id="3fb6f-154">`&&` "ve" sözcüğünü ifade eder.</span><span class="sxs-lookup"><span data-stu-id="3fb6f-154">The `&&` represents "and".</span></span> <span data-ttu-id="3fb6f-155">Bu, deyimi true dalında yürütmek için her iki koşulun da true olması gerektiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="3fb6f-155">It means both conditions must be true to execute the statement in the true branch.</span></span>  <span data-ttu-id="3fb6f-156">Bu örnekler aynı zamanda, `{` ve `}` ayraçları içine alınmaları koşuluyla her koşullu dalda birden çok deyime sahip olabileceğinizi de gösterir.</span><span class="sxs-lookup"><span data-stu-id="3fb6f-156">These examples also show that you can have multiple statements in each conditional branch, provided you enclose them in `{` and `}`.</span></span>

<span data-ttu-id="3fb6f-157">`||`"Veya" öğesini göstermek için de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3fb6f-157">You can also use  `||` to represent "or".</span></span> <span data-ttu-id="3fb6f-158">Şu ana kadar yazıldıktan sonra aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="3fb6f-158">Add the following code after what you've written so far:</span></span>

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

<span data-ttu-id="3fb6f-159">, Ve değerlerini değiştirin `a` ve `b` `c` arasında geçiş yapın `&&` `||` .</span><span class="sxs-lookup"><span data-stu-id="3fb6f-159">Modify the values of `a`, `b`, and `c` and switch between `&&` and `||` to explore.</span></span> <span data-ttu-id="3fb6f-160">Ve işleçlerinin nasıl çalıştığını daha fazla anlayacaksınız `&&` `||` .</span><span class="sxs-lookup"><span data-stu-id="3fb6f-160">You'll gain more understanding of how the `&&` and `||` operators work.</span></span>

<span data-ttu-id="3fb6f-161">İlk adımı tamamladınız.</span><span class="sxs-lookup"><span data-stu-id="3fb6f-161">You've finished the first step.</span></span> <span data-ttu-id="3fb6f-162">Sonraki bölüme başlamadan önce geçerli kodu ayrı bir yönteme taşıyalim.</span><span class="sxs-lookup"><span data-stu-id="3fb6f-162">Before you start the next section, let's move the current code into a separate method.</span></span> <span data-ttu-id="3fb6f-163">Bu, yeni bir örnekle çalışmaya başlamasını kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="3fb6f-163">That makes it easier to start working with a new example.</span></span> <span data-ttu-id="3fb6f-164">`Main`Yönteminizi olarak yeniden adlandırın `ExploreIf` ve çağıran yeni bir `Main` Yöntem yazın `ExploreIf` .</span><span class="sxs-lookup"><span data-stu-id="3fb6f-164">Rename your `Main` method to `ExploreIf` and write a new `Main` method that calls `ExploreIf`.</span></span> <span data-ttu-id="3fb6f-165">İşiniz bittiğinde kodunuzun şöyle görünmesi gerekir:</span><span class="sxs-lookup"><span data-stu-id="3fb6f-165">When you've finished, your code should look like this:</span></span>

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

<span data-ttu-id="3fb6f-166">Çağrısını not edin `ExploreIf()` .</span><span class="sxs-lookup"><span data-stu-id="3fb6f-166">Comment out the call to `ExploreIf()`.</span></span> <span data-ttu-id="3fb6f-167">Bu bölümde çalışırken çıktının daha az karışık hale gelir:</span><span class="sxs-lookup"><span data-stu-id="3fb6f-167">It will make the output less cluttered as you work in this section:</span></span>

```csharp
//ExploreIf();
```

<span data-ttu-id="3fb6f-168">`//`C# dilinde bir **Açıklama** başlatır.</span><span class="sxs-lookup"><span data-stu-id="3fb6f-168">The `//` starts a **comment** in C#.</span></span> <span data-ttu-id="3fb6f-169">Açıklamalar, kaynak kodunuzda tutmak istediğiniz tüm metinlerdir, ancak kod olarak yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="3fb6f-169">Comments are any text you want to keep in your source code but not execute as code.</span></span> <span data-ttu-id="3fb6f-170">Derleyici açıklamalardan herhangi bir yürütülebilir kod oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="3fb6f-170">The compiler doesn't generate any executable code from comments.</span></span>

## <a name="use-loops-to-repeat-operations"></a><span data-ttu-id="3fb6f-171">İşlemleri yinelemek için döngüleri kullanma</span><span class="sxs-lookup"><span data-stu-id="3fb6f-171">Use loops to repeat operations</span></span>

<span data-ttu-id="3fb6f-172">Bu bölümde, deyimlerini yinelemek için **döngüleri** kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="3fb6f-172">In this section, you use **loops** to repeat statements.</span></span> <span data-ttu-id="3fb6f-173">Bu kodu yönteminizin içinde deneyin `Main` :</span><span class="sxs-lookup"><span data-stu-id="3fb6f-173">Try this code in your `Main` method:</span></span>

```csharp
int counter = 0;
while (counter < 10)
{
    Console.WriteLine($"Hello World! The counter is {counter}");
    counter++;
}
```

<span data-ttu-id="3fb6f-174">`while`İfade bir koşulu denetler ve öğesinden sonra deyimin veya bildiri bloğunu yürütür `while` .</span><span class="sxs-lookup"><span data-stu-id="3fb6f-174">The `while` statement checks a condition and executes the statement or statement block following the `while`.</span></span> <span data-ttu-id="3fb6f-175">Koşul false olana kadar durumu sürekli olarak denetler ve bu deyimleri gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="3fb6f-175">It repeatedly checks the condition and executing those statements until the condition is false.</span></span>

<span data-ttu-id="3fb6f-176">Bu örnekte diğer bir yeni işleç mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="3fb6f-176">There's one other new operator in this example.</span></span> <span data-ttu-id="3fb6f-177">`counter` değişkeninden sonra gelen `++`, **artırma** işlecidir.</span><span class="sxs-lookup"><span data-stu-id="3fb6f-177">The `++` after the `counter` variable is the **increment** operator.</span></span> <span data-ttu-id="3fb6f-178">Değerine 1 ekler `counter` ve bu değeri `counter` değişkende depolar.</span><span class="sxs-lookup"><span data-stu-id="3fb6f-178">It adds 1 to the value of `counter` and stores that value in the `counter` variable.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3fb6f-179">`while`Kodu yürüttüğünüzde döngü koşulunun yanlış olarak değiştiği emin olun.</span><span class="sxs-lookup"><span data-stu-id="3fb6f-179">Make sure that the `while` loop condition changes to false as you execute the code.</span></span> <span data-ttu-id="3fb6f-180">Aksi halde, programınızın hiç sona ermediği **sonsuz bir döngü** oluşturmuş olursunuz.</span><span class="sxs-lookup"><span data-stu-id="3fb6f-180">Otherwise, you create an **infinite loop** where your program never ends.</span></span> <span data-ttu-id="3fb6f-181">Bu örnekte gösterilmediği için, programınızı **CTRL-C** veya başka yollarla çıkmaya zorlamaya zorlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="3fb6f-181">That is not demonstrated in this sample, because you have to force your program to quit using **CTRL-C** or other means.</span></span>

<span data-ttu-id="3fb6f-182">`while` döngüsü, `while` koşulundan sonraki kodu yürütmeden önce koşulu test eder.</span><span class="sxs-lookup"><span data-stu-id="3fb6f-182">The `while` loop tests the condition before executing the code following the `while`.</span></span> <span data-ttu-id="3fb6f-183">`do` ... `while` döngüsü önce kodu yürütür, sonra koşulu kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="3fb6f-183">The `do` ... `while` loop executes the code first, and then checks the condition.</span></span> <span data-ttu-id="3fb6f-184">*Do while* döngüsü aşağıdaki kodda gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="3fb6f-184">The *do while* loop is shown in the following code:</span></span>

```csharp
int counter = 0;
do
{
    Console.WriteLine($"Hello World! The counter is {counter}");
    counter++;
} while (counter < 10);
```

<span data-ttu-id="3fb6f-185">Bu `do` döngü ve önceki `while` döngü aynı çıktıyı üretir.</span><span class="sxs-lookup"><span data-stu-id="3fb6f-185">This `do` loop and the earlier `while` loop produce the same output.</span></span>

## <a name="work-with-the-for-loop"></a><span data-ttu-id="3fb6f-186">For döngüsü ile çalışma</span><span class="sxs-lookup"><span data-stu-id="3fb6f-186">Work with the for loop</span></span>

<span data-ttu-id="3fb6f-187">**For** döngüsü genellikle C# dilinde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3fb6f-187">The **for** loop is commonly used in C#.</span></span> <span data-ttu-id="3fb6f-188">Main () yönteminde bu kodu deneyin:</span><span class="sxs-lookup"><span data-stu-id="3fb6f-188">Try this code in your Main() method:</span></span>

```csharp
for (int index = 0; index < 10; index++)
{
    Console.WriteLine($"Hello World! The index is {index}");
}
```

<span data-ttu-id="3fb6f-189">Önceki kod, `while` döngüyle aynı çalışmayı ve `do` zaten kullandığınız döngüyü yapar.</span><span class="sxs-lookup"><span data-stu-id="3fb6f-189">The previous code does the same work as the `while` loop and the `do` loop you've already used.</span></span> <span data-ttu-id="3fb6f-190">`for` deyiminde, bunu nasıl çalıştığını denetleyen üç bölüm bulunur.</span><span class="sxs-lookup"><span data-stu-id="3fb6f-190">The `for` statement has three parts that control how it works.</span></span>

<span data-ttu-id="3fb6f-191">İlk bölüm **for başlatıcıdır**: `int index = 0;` Loop değişkeni olduğunu bildirir `index` ve başlangıç değerini olarak ayarlar `0` .</span><span class="sxs-lookup"><span data-stu-id="3fb6f-191">The first part is the **for initializer**: `int index = 0;` declares that `index` is the loop variable, and sets its initial value to `0`.</span></span>

<span data-ttu-id="3fb6f-192">Orta kısım **for koşuludur**: `index < 10` `for` sayacın değeri 10 ' dan az olduğu sürece bu döngünün yürütülmeye devam ettiğini bildirir.</span><span class="sxs-lookup"><span data-stu-id="3fb6f-192">The middle part is the **for condition**: `index < 10` declares that this `for` loop continues to execute as long as the value of counter is less than 10.</span></span>

<span data-ttu-id="3fb6f-193">Son bölüm, **Yineleyici için**: `index++` deyimden sonra blok yürütüldükten sonra döngü değişkeninin nasıl değiştirileceğini belirtir `for` .</span><span class="sxs-lookup"><span data-stu-id="3fb6f-193">The final part is the **for iterator**: `index++` specifies how to modify the loop variable after executing the block following the `for` statement.</span></span> <span data-ttu-id="3fb6f-194">Bu bölüm, bloğun her yürütme işleminde `index` değişkeninin 1 artırılması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="3fb6f-194">Here, it specifies that `index` should be incremented by 1 each time the block executes.</span></span>

<span data-ttu-id="3fb6f-195">Kendiniz deneyin.</span><span class="sxs-lookup"><span data-stu-id="3fb6f-195">Experiment yourself.</span></span> <span data-ttu-id="3fb6f-196">Aşağıdaki çeşitlemelerin her birini deneyin:</span><span class="sxs-lookup"><span data-stu-id="3fb6f-196">Try each of the following variations:</span></span>

- <span data-ttu-id="3fb6f-197">Farklı bir değerde başlamak için başlatıcıyı değiştirin.</span><span class="sxs-lookup"><span data-stu-id="3fb6f-197">Change the initializer to start at a different value.</span></span>
- <span data-ttu-id="3fb6f-198">Farklı bir değerde durmak için koşulu değiştirin.</span><span class="sxs-lookup"><span data-stu-id="3fb6f-198">Change the condition to stop at a different value.</span></span>

<span data-ttu-id="3fb6f-199">İşiniz bittiğinde öğrendiklerinizi kullanmak için kendi kendinize kod yazma adımına geçelim.</span><span class="sxs-lookup"><span data-stu-id="3fb6f-199">When you're done, let's move on to write some code yourself to use what you've learned.</span></span>

<span data-ttu-id="3fb6f-200">Bu öğreticide kapsanmayan başka bir döngü bildirisi vardır: `foreach` ifade.</span><span class="sxs-lookup"><span data-stu-id="3fb6f-200">There's one other looping statement that isn't covered in this tutorial: the `foreach` statement.</span></span> <span data-ttu-id="3fb6f-201">`foreach`İfade, öğe dizisindeki her öğe için kendi ifadesini yineler.</span><span class="sxs-lookup"><span data-stu-id="3fb6f-201">The `foreach` statement repeats its statement for every item in a sequence of items.</span></span> <span data-ttu-id="3fb6f-202">En sık *koleksiyonlarla*birlikte kullanılır, bu nedenle sonraki öğreticide ele alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="3fb6f-202">It's most often used with *collections*, so it's covered in the next tutorial.</span></span>

## <a name="created-nested-loops"></a><span data-ttu-id="3fb6f-203">İç içe geçmiş döngüler oluşturuldu</span><span class="sxs-lookup"><span data-stu-id="3fb6f-203">Created nested loops</span></span>

<span data-ttu-id="3fb6f-204">Bir `while` , `do` veya `for` döngüsü, iç döngüde her öğe ile dış döngüdeki her bir öğenin birleşimini kullanarak bir matris oluşturmak için başka bir döngünün içinde iç içe olabilir.</span><span class="sxs-lookup"><span data-stu-id="3fb6f-204">A `while`, `do`, or `for` loop can be nested inside another loop to create a matrix using the combination of each item in the outer loop with each item in the inner loop.</span></span> <span data-ttu-id="3fb6f-205">Satırları ve sütunları temsil etmek için alfasayısal çiftler kümesi oluşturmayı görelim.</span><span class="sxs-lookup"><span data-stu-id="3fb6f-205">Let's do that to build a set of alphanumeric pairs to represent rows and columns.</span></span>

<span data-ttu-id="3fb6f-206">Bir `for` döngü satırları oluşturabilir:</span><span class="sxs-lookup"><span data-stu-id="3fb6f-206">One `for` loop can generate the rows:</span></span>

```csharp
for (int row = 1; row < 11; row++)
{
    Console.WriteLine($"The row is {row}");
}
```

<span data-ttu-id="3fb6f-207">Şu sütunları başka bir döngü oluşturabilir:</span><span class="sxs-lookup"><span data-stu-id="3fb6f-207">Another loop can generate the columns:</span></span>

```csharp
for (char column = 'a'; column < 'k'; column++)
{
    Console.WriteLine($"The column is {column}");
}
```

<span data-ttu-id="3fb6f-208">Bir döngüyü diğerinin içine, çiftler halinde iç içe geçirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="3fb6f-208">You can nest one loop inside the other to form pairs:</span></span>

```csharp
for (int row = 1; row < 11; row++)
{
    for (char column = 'a'; column < 'k'; column++)
    {
        Console.WriteLine($"The cell is ({row}, {column})");
    }
}
```

<span data-ttu-id="3fb6f-209">İç döngünün her tam çalışması için dış döngünün bir kez artıyor olduğunu görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3fb6f-209">You can see that the outer loop increments once for each full run of the inner loop.</span></span> <span data-ttu-id="3fb6f-210">Satır ve sütun iç içe geçirmeyi tersine çevirin ve yaptığınız değişiklikleri kendiniz görün.</span><span class="sxs-lookup"><span data-stu-id="3fb6f-210">Reverse the row and column nesting, and see the changes for yourself.</span></span>

## <a name="combine-branches-and-loops"></a><span data-ttu-id="3fb6f-211">Dalları ve döngüleri birleştirme</span><span class="sxs-lookup"><span data-stu-id="3fb6f-211">Combine branches and loops</span></span>

<span data-ttu-id="3fb6f-212">C# dilinde `if` deyimini ve döngü yapılarını gördüğünüze göre şimdi 1 ile 20 arasında olup 3’e bölünebilen tüm tamsayıların toplamını bulmak için C# kodu yazmayı deneyin.</span><span class="sxs-lookup"><span data-stu-id="3fb6f-212">Now that you've seen the `if` statement and the looping constructs in the C# language, see if you can write C# code to find the sum of all integers 1 through 20 that are divisible by 3.</span></span>  <span data-ttu-id="3fb6f-213">Aşağıdaki ipuçlarından yararlanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="3fb6f-213">Here are a few hints:</span></span>

- <span data-ttu-id="3fb6f-214">`%` işleci size bölme işlemindeki kalanı verir.</span><span class="sxs-lookup"><span data-stu-id="3fb6f-214">The `%` operator gives you the remainder of a division operation.</span></span>
- <span data-ttu-id="3fb6f-215">`if` deyimi bir sayının toplama dahil edilip edilmemesi gerektiğini görmeniz için size koşulu verir.</span><span class="sxs-lookup"><span data-stu-id="3fb6f-215">The `if` statement gives you the condition to see if a number should be part of the sum.</span></span>
- <span data-ttu-id="3fb6f-216">`for` döngüsü 1 ile 20 arasındaki tüm sayılar için bir dizi adımı yinelemenize yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="3fb6f-216">The `for` loop can help you repeat a series of steps for all the numbers 1 through 20.</span></span>

<span data-ttu-id="3fb6f-217">Kendiniz deneyin.</span><span class="sxs-lookup"><span data-stu-id="3fb6f-217">Try it yourself.</span></span> <span data-ttu-id="3fb6f-218">Daha sonra başarılı olup olmadığınıza bakın.</span><span class="sxs-lookup"><span data-stu-id="3fb6f-218">Then check how you did.</span></span> <span data-ttu-id="3fb6f-219">Yanıt için 63 almalısınız.</span><span class="sxs-lookup"><span data-stu-id="3fb6f-219">You should get 63 for an answer.</span></span> <span data-ttu-id="3fb6f-220">[GitHub 'da tamamlanan kodu görüntüleyerek](https://github.com/dotnet/samples/tree/master/csharp/branches-quickstart/Program.cs#L46-L54)olası bir yanıt görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3fb6f-220">You can see one possible answer by [viewing the completed code on GitHub](https://github.com/dotnet/samples/tree/master/csharp/branches-quickstart/Program.cs#L46-L54).</span></span>

<span data-ttu-id="3fb6f-221">"Dallar ve döngüler" öğreticisini tamamladınız.</span><span class="sxs-lookup"><span data-stu-id="3fb6f-221">You've completed the "branches and loops" tutorial.</span></span>

<span data-ttu-id="3fb6f-222">Kendi geliştirme ortamınızda [diziler ve koleksiyonlar](arrays-and-collections.md) öğreticisiyle devam edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3fb6f-222">You can continue with the [Arrays and collections](arrays-and-collections.md) tutorial in your own development environment.</span></span>

<span data-ttu-id="3fb6f-223">Aşağıdaki makalelerde bu kavramlar hakkında daha fazla bilgi edinebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="3fb6f-223">You can learn more about these concepts in these articles:</span></span>

- [<span data-ttu-id="3fb6f-224">If ve else deyimi</span><span class="sxs-lookup"><span data-stu-id="3fb6f-224">If and else statement</span></span>](../../language-reference/keywords/if-else.md)
- [<span data-ttu-id="3fb6f-225">While ekstresi</span><span class="sxs-lookup"><span data-stu-id="3fb6f-225">While statement</span></span>](../../language-reference/keywords/while.md)
- [<span data-ttu-id="3fb6f-226">Do deyimi</span><span class="sxs-lookup"><span data-stu-id="3fb6f-226">Do statement</span></span>](../../language-reference/keywords/do.md)
- [<span data-ttu-id="3fb6f-227">For deyimleri</span><span class="sxs-lookup"><span data-stu-id="3fb6f-227">For statement</span></span>](../../language-reference/keywords/for.md)
