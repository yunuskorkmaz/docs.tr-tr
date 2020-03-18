---
title: Dallar ve döngüler - C# eğitimine giriş
description: Dallar ve döngüler hakkında bu öğreticide, ifadeleri tekrar tekrar yürütmek için koşullu dalları ve döngüleri destekleyen dil sözdizimini keşfetmek için C# kodu yazarsınız.
ms.date: 10/31/2017
ms.custom: mvc
ms.openlocfilehash: 44b634e3c2120116ee7fd66770398a6b66c8ed8c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "73739131"
---
# <a name="learn-conditional-logic-with-branch-and-loop-statements"></a><span data-ttu-id="65a51-103">Dal ve döngü deyimleri ile koşullu mantığı öğrenin</span><span class="sxs-lookup"><span data-stu-id="65a51-103">Learn conditional logic with branch and loop statements</span></span>

<span data-ttu-id="65a51-104">Bu öğretici, değişkenleri inceleyen ve bu değişkenleri temel alan yürütme yolunu değiştiren kod yazmayı öğretir.</span><span class="sxs-lookup"><span data-stu-id="65a51-104">This tutorial teaches you how to write code that examines variables and changes the execution path based on those variables.</span></span> <span data-ttu-id="65a51-105">C# kodu yazar sınız ve derleme ve çalıştırma sonuçlarını görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="65a51-105">You write C# code and see the results of compiling and running it.</span></span> <span data-ttu-id="65a51-106">Öğretici C# dallanma ve döngü yapıları keşfetmek ders bir dizi içerir.</span><span class="sxs-lookup"><span data-stu-id="65a51-106">The tutorial contains a series of lessons that explore branching and looping constructs in C#.</span></span> <span data-ttu-id="65a51-107">Bu dersler size C# dilinin temel özelliklerini öğretir.</span><span class="sxs-lookup"><span data-stu-id="65a51-107">These lessons teach you the fundamentals of the C# language.</span></span>

<span data-ttu-id="65a51-108">Bu öğretici, geliştirme için kullanabileceğiniz bir makineye sahip olmak için bekliyor.</span><span class="sxs-lookup"><span data-stu-id="65a51-108">This tutorial expects you to have a machine you can use for development.</span></span> <span data-ttu-id="65a51-109">.NET öğretici [Hello World 10 dakika içinde](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) Windows, Linux veya macOS'ta yerel geliştirme ortamınızı ayarlama talimatları na sahiptir.</span><span class="sxs-lookup"><span data-stu-id="65a51-109">The .NET tutorial [Hello World in 10 minutes](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) has instructions for setting up your local development environment on Windows, Linux, or macOS.</span></span> <span data-ttu-id="65a51-110">Kullanacağınız komutların hızlı bir genel bakışı, daha fazla ayrıntıya bağlantılar içeren [geliştirme araçlarına aşina olun'da](local-environment.md) dır.</span><span class="sxs-lookup"><span data-stu-id="65a51-110">A quick overview of the commands you'll use is in the [Become familiar with the development tools](local-environment.md) with links to more details.</span></span>

## <a name="make-decisions-using-the-if-statement"></a><span data-ttu-id="65a51-111">İfadeyi kullanarak `if` kararlar verme</span><span class="sxs-lookup"><span data-stu-id="65a51-111">Make decisions using the `if` statement</span></span>

<span data-ttu-id="65a51-112">*Dallar-öğretici*adlı bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="65a51-112">Create a directory named *branches-tutorial*.</span></span> <span data-ttu-id="65a51-113">Geçerli dizinini yapın ve aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="65a51-113">Make that the current directory and run the following command:</span></span>

```dotnetcli
dotnet new console -n BranchesAndLoops -o .
```

<span data-ttu-id="65a51-114">Bu komut, geçerli dizinde yeni bir .NET Core konsol uygulaması oluşturur.</span><span class="sxs-lookup"><span data-stu-id="65a51-114">This command creates a new .NET Core console application in the current directory.</span></span>

<span data-ttu-id="65a51-115">En sevdiğiniz düzenleyicide *Program.cs* açın `Console.WriteLine("Hello World!");` ve satırı aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="65a51-115">Open *Program.cs* in your favorite editor, and replace the line `Console.WriteLine("Hello World!");` with the following code:</span></span>

```csharp
int a = 5;
int b = 6;
if (a + b > 10)
    Console.WriteLine("The answer is greater than 10.");
```

<span data-ttu-id="65a51-116">Konsol pencerenize `dotnet run` yazarak bu kodu deneyin.</span><span class="sxs-lookup"><span data-stu-id="65a51-116">Try this code by typing `dotnet run` in your console window.</span></span> <span data-ttu-id="65a51-117">"Yanıt 10'dan büyüktür" iletisini görmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="65a51-117">You should see the message "The answer is greater than 10."</span></span> <span data-ttu-id="65a51-118">konsolunuza yazdırılır.</span><span class="sxs-lookup"><span data-stu-id="65a51-118">printed to your console.</span></span>

<span data-ttu-id="65a51-119">`b` tanımlamasını toplamın 10’dan küçük olacağı şekilde değiştirin:</span><span class="sxs-lookup"><span data-stu-id="65a51-119">Modify the declaration of `b` so that the sum is less than 10:</span></span>

```csharp
int b = 3;
```

<span data-ttu-id="65a51-120">Tekrar `dotnet run` yazın.</span><span class="sxs-lookup"><span data-stu-id="65a51-120">Type `dotnet run` again.</span></span> <span data-ttu-id="65a51-121">Yanıt 10’dan küçük olduğundan herhangi bir şey yazdırılmaz.</span><span class="sxs-lookup"><span data-stu-id="65a51-121">Because the answer is less than 10, nothing is printed.</span></span> <span data-ttu-id="65a51-122">Test ettiğiniz **koşul** false değerindedir.</span><span class="sxs-lookup"><span data-stu-id="65a51-122">The **condition** you're testing is false.</span></span> <span data-ttu-id="65a51-123">Bir `if` deyimi için olası dallardan yalnızca birini (true dalı) yazdığınızdan, yürütülecek herhangi bir kodunuz yoktur.</span><span class="sxs-lookup"><span data-stu-id="65a51-123">You don't have any code to execute because you've only written one of the possible branches for an `if` statement: the true branch.</span></span>

> [!TIP]
> <span data-ttu-id="65a51-124">C# dilini (veya herhangi bir programlama dilini) keşfederken, kod yazdığınızda hatalar yapacaksınız.</span><span class="sxs-lookup"><span data-stu-id="65a51-124">As you explore C# (or any programming language), you'll make mistakes when you write code.</span></span> <span data-ttu-id="65a51-125">Derleyici hataları bulur ve bildirir.</span><span class="sxs-lookup"><span data-stu-id="65a51-125">The compiler will find and report the errors.</span></span> <span data-ttu-id="65a51-126">Hata çıktısını ve hatayı oluşturan kodu yakından incegörün.</span><span class="sxs-lookup"><span data-stu-id="65a51-126">Look closely at the error output and the code that generated the error.</span></span> <span data-ttu-id="65a51-127">Derleyici hatası genellikle sorunu bulmanıza yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="65a51-127">The compiler error can usually help you find the problem.</span></span>

<span data-ttu-id="65a51-128">Bu ilk örnek ve `if` Boolean türlerinin gücünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="65a51-128">This first sample shows the power of `if` and Boolean types.</span></span> <span data-ttu-id="65a51-129">*Boolean* iki değerden birine sahip olabilecek `true` bir `false`değişkendir: veya .</span><span class="sxs-lookup"><span data-stu-id="65a51-129">A *Boolean* is a variable that can have one of two values: `true` or `false`.</span></span> <span data-ttu-id="65a51-130">C# Boolean `bool` değişkenleri için özel bir tür tanımlar.</span><span class="sxs-lookup"><span data-stu-id="65a51-130">C# defines a special type, `bool` for Boolean variables.</span></span> <span data-ttu-id="65a51-131">`if` deyimi bir `bool` için değeri kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="65a51-131">The `if` statement checks the value of a `bool`.</span></span> <span data-ttu-id="65a51-132">Değer `true` olduğunda, `if` deyiminden sonra gelen deyim yürütülür.</span><span class="sxs-lookup"><span data-stu-id="65a51-132">When the value is `true`, the statement following the `if` executes.</span></span> <span data-ttu-id="65a51-133">Aksi halde atlanır.</span><span class="sxs-lookup"><span data-stu-id="65a51-133">Otherwise, it is skipped.</span></span>

<span data-ttu-id="65a51-134">Koşulları kontrol etmek ve bu koşullara göre deyimleri yürütmek için gerçekleştirilen bu işlem son derece etkilidir.</span><span class="sxs-lookup"><span data-stu-id="65a51-134">This process of checking conditions and executing statements based on those conditions is very powerful.</span></span>

## <a name="make-if-and-else-work-together"></a><span data-ttu-id="65a51-135">if ve else koşullarını birlikte çalıştırma</span><span class="sxs-lookup"><span data-stu-id="65a51-135">Make if and else work together</span></span>

<span data-ttu-id="65a51-136">Hem true hem de false dallarında farklı kod yürütmek için, koşul false olduğunda yürütülen bir `else` dalı oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="65a51-136">To execute different code in both the true and false branches, you create an `else` branch that executes when the condition is false.</span></span> <span data-ttu-id="65a51-137">Bunu dene.</span><span class="sxs-lookup"><span data-stu-id="65a51-137">Try this.</span></span> <span data-ttu-id="65a51-138">Aşağıdaki koddaki son iki satırı `Main` yönteminize ekleyin (ilk dördüne zaten sahip olmalısınız):</span><span class="sxs-lookup"><span data-stu-id="65a51-138">Add the last two lines in the code below to your `Main` method (you should already have the first four):</span></span>

```csharp
int a = 5;
int b = 3;
if (a + b > 10)
    Console.WriteLine("The answer is greater than 10");
else
    Console.WriteLine("The answer is not greater than 10");
```

<span data-ttu-id="65a51-139">`else` anahtar sözcüğünden sonraki deyim, yalnızca test edilen koşul `false` olduğunda yürütülür.</span><span class="sxs-lookup"><span data-stu-id="65a51-139">The statement following the `else` keyword executes only when the condition being tested is `false`.</span></span> <span data-ttu-id="65a51-140">Boolean `if` `else` koşullarını birleştirerek hem bir hem de bir `true` `false` durumu işlemek için ihtiyacınız olan tüm gücü sağlar.</span><span class="sxs-lookup"><span data-stu-id="65a51-140">Combining `if` and `else` with Boolean conditions provides all the power you need to handle both a `true` and a `false` condition.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="65a51-141">`if` ve `else` deyimlerinin altındaki girinti, insan okuyuculara yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="65a51-141">The indentation under the `if` and `else` statements is for human readers.</span></span>
> <span data-ttu-id="65a51-142">C# dili girinti veya beyaz boşluk önemli olarak tedavi etmez.</span><span class="sxs-lookup"><span data-stu-id="65a51-142">The C# language doesn't treat indentation or white space as significant.</span></span>
> <span data-ttu-id="65a51-143">`if` veya `else` anahtar sözcüğünden sonra gelen deyim, koşula bağlı olarak yürütülür.</span><span class="sxs-lookup"><span data-stu-id="65a51-143">The statement following the `if` or `else` keyword will be executed based on the condition.</span></span> <span data-ttu-id="65a51-144">Bu öğreticideki tüm örnekler, deyimlerin denetim akışına dayalı girintisi satırlara yönelik yaygın bir uygulamayı izler.</span><span class="sxs-lookup"><span data-stu-id="65a51-144">All the samples in this tutorial follow a common practice to indent lines based on the control flow of statements.</span></span>

<span data-ttu-id="65a51-145">Girinti dikkate alınmadığından, koşullu olarak yürütülen bloğun birden çok deyim içermesini istediğinizde bunu belirtmek için `{` ve `}` ayraçlarını kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="65a51-145">Because indentation is not significant, you need to use `{` and `}` to indicate when you want more than one statement to be part of the block that executes conditionally.</span></span> <span data-ttu-id="65a51-146">C# programcıları bu ayraçları genellikle tüm `if` and `else` tümcelerinde kullanır.</span><span class="sxs-lookup"><span data-stu-id="65a51-146">C# programmers typically use those braces on all `if` and `else` clauses.</span></span> <span data-ttu-id="65a51-147">Aşağıdaki örnek, az önce oluşturduğunuz örnekle aynıdır.</span><span class="sxs-lookup"><span data-stu-id="65a51-147">The following example is the same as the one you just created.</span></span> <span data-ttu-id="65a51-148">Yukarıdaki kodunuzu aşağıdaki kodla eşleşecek şekilde değiştirin:</span><span class="sxs-lookup"><span data-stu-id="65a51-148">Modify your code above to match the following code:</span></span>

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
> <span data-ttu-id="65a51-149">Bu öğreticinin geri kalanı boyunca, kod örneklerinin tümü, kabul edilen uygulamaları izleyerek parantezleri içerir.</span><span class="sxs-lookup"><span data-stu-id="65a51-149">Through the rest of this tutorial, the code samples all include the braces, following accepted practices.</span></span>

<span data-ttu-id="65a51-150">Daha karmaşık koşulları test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="65a51-150">You can test more complicated conditions.</span></span> <span data-ttu-id="65a51-151">Şimdiye kadar yazdığınız `Main` koddan sonra yönteminize aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="65a51-151">Add the following code in your `Main` method after the code you've written so far:</span></span>

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

<span data-ttu-id="65a51-152">Eşitlik `==` *için*sembol testleri.</span><span class="sxs-lookup"><span data-stu-id="65a51-152">The `==` symbol tests for *equality*.</span></span> <span data-ttu-id="65a51-153">Kullanmak, `==` eşitlik için testi atamadan ayırır, `a = 5`bunu ' da gördüğünüz.</span><span class="sxs-lookup"><span data-stu-id="65a51-153">Using `==` distinguishes the test for equality from assignment, which you saw in `a = 5`.</span></span>

<span data-ttu-id="65a51-154">`&&` "ve" sözcüğünü ifade eder.</span><span class="sxs-lookup"><span data-stu-id="65a51-154">The `&&` represents "and".</span></span> <span data-ttu-id="65a51-155">Bu, deyimi true dalında yürütmek için her iki koşulun da true olması gerektiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="65a51-155">It means both conditions must be true to execute the statement in the true branch.</span></span>  <span data-ttu-id="65a51-156">Bu örnekler aynı zamanda, `{` ve `}` ayraçları içine alınmaları koşuluyla her koşullu dalda birden çok deyime sahip olabileceğinizi de gösterir.</span><span class="sxs-lookup"><span data-stu-id="65a51-156">These examples also show that you can have multiple statements in each conditional branch, provided you enclose them in `{` and `}`.</span></span>

<span data-ttu-id="65a51-157">"veya" `||` temsil etmek için de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="65a51-157">You can also use  `||` to represent "or".</span></span> <span data-ttu-id="65a51-158">Şimdiye kadar yazdıkların ardından aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="65a51-158">Add the following code after what you've written so far:</span></span>

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

<span data-ttu-id="65a51-159">`a`, `b`ve `c` , ve arasında `&&` geçiş `||` ve keşfetmek için değerlerini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="65a51-159">Modify the values of `a`, `b`, and `c` and switch between `&&` and `||` to explore.</span></span> <span data-ttu-id="65a51-160">Operatörlerin ve `&&` `||` operatörlerin nasıl çalıştığını daha iyi anlayasınız.</span><span class="sxs-lookup"><span data-stu-id="65a51-160">You'll gain more understanding of how the `&&` and `||` operators work.</span></span>

<span data-ttu-id="65a51-161">İlk adımı bitirdin.</span><span class="sxs-lookup"><span data-stu-id="65a51-161">You've finished the first step.</span></span> <span data-ttu-id="65a51-162">Bir sonraki bölümü başlatmadan önce, geçerli kodu ayrı bir yönteme taşıyalım.</span><span class="sxs-lookup"><span data-stu-id="65a51-162">Before you start the next section, let's move the current code into a separate method.</span></span> <span data-ttu-id="65a51-163">Bu, yeni bir örnekle çalışmaya başlamayı kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="65a51-163">That makes it easier to start working with a new example.</span></span> <span data-ttu-id="65a51-164">Metodunuzu `ExploreIf` yeniden adlandırın `Main` `Main` ve `ExploreIf`çağıran yeni bir yöntem yazın.</span><span class="sxs-lookup"><span data-stu-id="65a51-164">Rename your `Main` method to `ExploreIf` and write a new `Main` method that calls `ExploreIf`.</span></span> <span data-ttu-id="65a51-165">Bitirdikten sonra, kodunuz şu şekilde görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="65a51-165">When you have finished, your code should look like this:</span></span>

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

<span data-ttu-id="65a51-166">Çağrıyı yorumla. `ExploreIf()`</span><span class="sxs-lookup"><span data-stu-id="65a51-166">Comment out the call to `ExploreIf()`.</span></span> <span data-ttu-id="65a51-167">Bu bölümde çalışırken çıktıdaha az darmadağın yapacaktır:</span><span class="sxs-lookup"><span data-stu-id="65a51-167">It will make the output less cluttered as you work in this section:</span></span>

```csharp
//ExploreIf();
```

<span data-ttu-id="65a51-168">C#'da `//` bir **yorum** başlar.</span><span class="sxs-lookup"><span data-stu-id="65a51-168">The `//` starts a **comment** in C#.</span></span> <span data-ttu-id="65a51-169">Yorumlar, kaynak kodunuzda tutmak istediğiniz ancak kod olarak yürütülmemek istemediğiniz herhangi bir metindir.</span><span class="sxs-lookup"><span data-stu-id="65a51-169">Comments are any text you want to keep in your source code but not execute as code.</span></span> <span data-ttu-id="65a51-170">Derleyici yorumlardan yürütülebilir bir kod oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="65a51-170">The compiler does not generate any executable code from comments.</span></span>

## <a name="use-loops-to-repeat-operations"></a><span data-ttu-id="65a51-171">İşlemleri yinelemek için döngüleri kullanma</span><span class="sxs-lookup"><span data-stu-id="65a51-171">Use loops to repeat operations</span></span>

<span data-ttu-id="65a51-172">Bu bölümde ifadeleri yinelemek için **döngüler** kullanın.</span><span class="sxs-lookup"><span data-stu-id="65a51-172">In this section you use **loops** to repeat statements.</span></span> <span data-ttu-id="65a51-173">Yönteminizde `Main` bu kodu deneyin:</span><span class="sxs-lookup"><span data-stu-id="65a51-173">Try this code in your `Main` method:</span></span>

```csharp
int counter = 0;
while (counter < 10)
{
    Console.WriteLine($"Hello World! The counter is {counter}");
    counter++;
}
```

<span data-ttu-id="65a51-174">İfade `while` bir koşulu denetler ve aşağıdaki ifade `while`veya deyim bloğunu yürütür.</span><span class="sxs-lookup"><span data-stu-id="65a51-174">The `while` statement checks a condition and executes the statement or statement block following the `while`.</span></span> <span data-ttu-id="65a51-175">Bu durum tekrar tekrar denetler ve koşul yanlış olana kadar bu ifadeleri yürütme.</span><span class="sxs-lookup"><span data-stu-id="65a51-175">It repeatedly checks the condition and executing those statements until the condition is false.</span></span>

<span data-ttu-id="65a51-176">Bu örnekte diğer bir yeni işleç mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="65a51-176">There's one other new operator in this example.</span></span> <span data-ttu-id="65a51-177">`counter` değişkeninden sonra gelen `++`, **artırma** işlecidir.</span><span class="sxs-lookup"><span data-stu-id="65a51-177">The `++` after the `counter` variable is the **increment** operator.</span></span> <span data-ttu-id="65a51-178">Bu değere 1 `counter` ekler ve `counter` değişkende bu değeri depolar.</span><span class="sxs-lookup"><span data-stu-id="65a51-178">It adds 1 to the value of `counter` and stores that value in the `counter` variable.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="65a51-179">Kodu çalıştırırken `while` döngü koşulunun false olarak değiştiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="65a51-179">Make sure that the `while` loop condition changes to false as you execute the code.</span></span> <span data-ttu-id="65a51-180">Aksi halde, programınızın hiç sona ermediği **sonsuz bir döngü** oluşturmuş olursunuz.</span><span class="sxs-lookup"><span data-stu-id="65a51-180">Otherwise, you create an **infinite loop** where your program never ends.</span></span> <span data-ttu-id="65a51-181">Bu örnekte gösterilmiş değildir, çünkü programınızı **CTRL-C** veya başka yolla kullanmayı bırakmaya zorlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="65a51-181">That is not demonstrated in this sample, because you have to force your program to quit using **CTRL-C** or other means.</span></span>

<span data-ttu-id="65a51-182">`while` döngüsü, `while` koşulundan sonraki kodu yürütmeden önce koşulu test eder.</span><span class="sxs-lookup"><span data-stu-id="65a51-182">The `while` loop tests the condition before executing the code following the `while`.</span></span> <span data-ttu-id="65a51-183">`do` ... `while` döngüsü önce kodu yürütür, sonra koşulu kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="65a51-183">The `do` ... `while` loop executes the code first, and then checks the condition.</span></span> <span data-ttu-id="65a51-184">Do while döngüsü aşağıdaki kodda gösterilir:</span><span class="sxs-lookup"><span data-stu-id="65a51-184">The do while loop is shown in the following code:</span></span>

```csharp
int counter = 0;
do
{
    Console.WriteLine($"Hello World! The counter is {counter}");
    counter++;
} while (counter < 10);
```

<span data-ttu-id="65a51-185">Bu `do` döngü ve `while` önceki döngü aynı çıktıyı üretir.</span><span class="sxs-lookup"><span data-stu-id="65a51-185">This `do` loop and the earlier `while` loop produce the same output.</span></span>

## <a name="work-with-the-for-loop"></a><span data-ttu-id="65a51-186">For döngüsü ile çalışma</span><span class="sxs-lookup"><span data-stu-id="65a51-186">Work with the for loop</span></span>

<span data-ttu-id="65a51-187">**For** döngüsü genellikle C#'da kullanılır.</span><span class="sxs-lookup"><span data-stu-id="65a51-187">The **for** loop is commonly used in C#.</span></span> <span data-ttu-id="65a51-188">Main() yönteminizde bu kodu deneyin:</span><span class="sxs-lookup"><span data-stu-id="65a51-188">Try this code in your Main() method:</span></span>

```csharp
for (int index = 0; index < 10; index++)
{
    Console.WriteLine($"Hello World! The index is {index}");
}
```

<span data-ttu-id="65a51-189">Bu, `while` döngüsü ve zaten kullandığınız `do` döngüsü ile aynı işlevi görür.</span><span class="sxs-lookup"><span data-stu-id="65a51-189">This does the same work as the `while` loop and the `do` loop you've already used.</span></span> <span data-ttu-id="65a51-190">`for` deyiminde, bunu nasıl çalıştığını denetleyen üç bölüm bulunur.</span><span class="sxs-lookup"><span data-stu-id="65a51-190">The `for` statement has three parts that control how it works.</span></span>

<span data-ttu-id="65a51-191">İlk bölüm **için başharf**: `int index = 0;` döngü `index` değişkeni olduğunu bildirir ve ilk `0`değerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="65a51-191">The first part is the **for initializer**: `int index = 0;` declares that `index` is the loop variable, and sets its initial value to `0`.</span></span>

<span data-ttu-id="65a51-192">Orta kısım **for koşuldur**: `index < 10` sayacın değeri 10'dan küçük olduğu sürece bu `for` döngünün yürütmeye devam ettiğini bildirir.</span><span class="sxs-lookup"><span data-stu-id="65a51-192">The middle part is the **for condition**: `index < 10` declares that this `for` loop continues to execute as long as the value of counter is less than 10.</span></span>

<span data-ttu-id="65a51-193">Son bölüm **iterator için** `index++` : `for` deyimi izleyen blok çalıştırdıktan sonra döngü değişkeninin nasıl değiştirilebildiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="65a51-193">The final part is the **for iterator**: `index++` specifies how to modify the loop variable after executing the block following the `for` statement.</span></span> <span data-ttu-id="65a51-194">Bu bölüm, bloğun her yürütme işleminde `index` değişkeninin 1 artırılması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="65a51-194">Here, it specifies that `index` should be incremented by 1 each time the block executes.</span></span>

<span data-ttu-id="65a51-195">Bunları kendiniz deneyin.</span><span class="sxs-lookup"><span data-stu-id="65a51-195">Experiment with these yourself.</span></span> <span data-ttu-id="65a51-196">Aşağıdakilerden her birini deneyin:</span><span class="sxs-lookup"><span data-stu-id="65a51-196">Try each of the following:</span></span>

- <span data-ttu-id="65a51-197">Farklı bir değerde başlamak için başlatıcıyı değiştirin.</span><span class="sxs-lookup"><span data-stu-id="65a51-197">Change the initializer to start at a different value.</span></span>
- <span data-ttu-id="65a51-198">Farklı bir değerde durmak için koşulu değiştirin.</span><span class="sxs-lookup"><span data-stu-id="65a51-198">Change the condition to stop at a different value.</span></span>

<span data-ttu-id="65a51-199">İşiniz bittiğinde öğrendiklerinizi kullanmak için kendi kendinize kod yazma adımına geçelim.</span><span class="sxs-lookup"><span data-stu-id="65a51-199">When you're done, let's move on to write some code yourself to use what you've learned.</span></span>

## <a name="combine-branches-and-loops"></a><span data-ttu-id="65a51-200">Dalları ve döngüleri birleştirme</span><span class="sxs-lookup"><span data-stu-id="65a51-200">Combine branches and loops</span></span>

<span data-ttu-id="65a51-201">C# dilinde `if` deyimini ve döngü yapılarını gördüğünüze göre şimdi 1 ile 20 arasında olup 3’e bölünebilen tüm tamsayıların toplamını bulmak için C# kodu yazmayı deneyin.</span><span class="sxs-lookup"><span data-stu-id="65a51-201">Now that you've seen the `if` statement and the looping constructs in the C# language, see if you can write C# code to find the sum of all integers 1 through 20 that are divisible by 3.</span></span>  <span data-ttu-id="65a51-202">Aşağıdaki ipuçlarından yararlanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="65a51-202">Here are a few hints:</span></span>

- <span data-ttu-id="65a51-203">`%` işleci size bölme işlemindeki kalanı verir.</span><span class="sxs-lookup"><span data-stu-id="65a51-203">The `%` operator gives you the remainder of a division operation.</span></span>
- <span data-ttu-id="65a51-204">`if` deyimi bir sayının toplama dahil edilip edilmemesi gerektiğini görmeniz için size koşulu verir.</span><span class="sxs-lookup"><span data-stu-id="65a51-204">The `if` statement gives you the condition to see if a number should be part of the sum.</span></span>
- <span data-ttu-id="65a51-205">`for` döngüsü 1 ile 20 arasındaki tüm sayılar için bir dizi adımı yinelemenize yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="65a51-205">The `for` loop can help you repeat a series of steps for all the numbers 1 through 20.</span></span>

<span data-ttu-id="65a51-206">Kendiniz deneyin.</span><span class="sxs-lookup"><span data-stu-id="65a51-206">Try it yourself.</span></span> <span data-ttu-id="65a51-207">Daha sonra başarılı olup olmadığınıza bakın.</span><span class="sxs-lookup"><span data-stu-id="65a51-207">Then check how you did.</span></span> <span data-ttu-id="65a51-208">Cevap için 63 almalısın.</span><span class="sxs-lookup"><span data-stu-id="65a51-208">You should get 63 for an answer.</span></span> <span data-ttu-id="65a51-209">[Tamamlanmış kodu GitHub'da görüntüleyerek](https://github.com/dotnet/samples/tree/master/csharp/branches-quickstart/Program.cs#L46-L54)olası bir yanıtı görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="65a51-209">You can see one possible answer by [viewing the completed code on GitHub](https://github.com/dotnet/samples/tree/master/csharp/branches-quickstart/Program.cs#L46-L54).</span></span>

<span data-ttu-id="65a51-210">"Dallar ve döngüler" eğitimini tamamladınız.</span><span class="sxs-lookup"><span data-stu-id="65a51-210">You've completed the "branches and loops" tutorial.</span></span>

<span data-ttu-id="65a51-211">Kendi geliştirme ortamınızda [diziler ve koleksiyonlar](arrays-and-collections.md) öğretici ile devam edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="65a51-211">You can continue with the [Arrays and collections](arrays-and-collections.md) tutorial in your own development environment.</span></span>

<span data-ttu-id="65a51-212">Aşağıdaki konulardan bu kavramlar hakkında daha fazla bilgi edinebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="65a51-212">You can learn more about these concepts in these topics:</span></span>

- [<span data-ttu-id="65a51-213">If ve else deyimi</span><span class="sxs-lookup"><span data-stu-id="65a51-213">If and else statement</span></span>](../../language-reference/keywords/if-else.md)
- [<span data-ttu-id="65a51-214">İfade iken</span><span class="sxs-lookup"><span data-stu-id="65a51-214">While statement</span></span>](../../language-reference/keywords/while.md)
- [<span data-ttu-id="65a51-215">Do deyimi</span><span class="sxs-lookup"><span data-stu-id="65a51-215">Do statement</span></span>](../../language-reference/keywords/do.md)
- [<span data-ttu-id="65a51-216">İfade için</span><span class="sxs-lookup"><span data-stu-id="65a51-216">For statement</span></span>](../../language-reference/keywords/for.md)
