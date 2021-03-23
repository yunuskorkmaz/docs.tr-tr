---
title: Dallar ve döngüler-C# öğreticisine giriş
description: Dallar ve döngüler hakkında bu öğreticide, ifadeleri sürekli olarak yürütmek için koşullu dalları ve döngüleri destekleyen dil sözdizimini araştırmak üzere C# kodu yazarsınız.
ms.date: 02/05/2021
ms.openlocfilehash: cc1c5457738ca0f7d4756811adec4a7bd57cb009
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/23/2021
ms.locfileid: "104872502"
---
# <a name="learn-conditional-logic-with-branch-and-loop-statements"></a><span data-ttu-id="c7fe3-103">Dal ve döngü deyimleri ile koşullu mantık öğrenin</span><span class="sxs-lookup"><span data-stu-id="c7fe3-103">Learn conditional logic with branch and loop statements</span></span>

<span data-ttu-id="c7fe3-104">Bu öğretici, değişkenleri inceleyen ve bu değişkenlere göre yürütme yolunu değiştiren bir kod yazmayı öğretir.</span><span class="sxs-lookup"><span data-stu-id="c7fe3-104">This tutorial teaches you how to write code that examines variables and changes the execution path based on those variables.</span></span> <span data-ttu-id="c7fe3-105">C# kodu yazar ve bunu derleyip çalıştırmanın sonuçlarını görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="c7fe3-105">You write C# code and see the results of compiling and running it.</span></span> <span data-ttu-id="c7fe3-106">Öğretici, C# ' de dallanma ve döngü yapılarını keşfetmenizi sağlayan bir dizi ders içerir.</span><span class="sxs-lookup"><span data-stu-id="c7fe3-106">The tutorial contains a series of lessons that explore branching and looping constructs in C#.</span></span> <span data-ttu-id="c7fe3-107">Bu dersler size C# dilinin temel özelliklerini öğretir.</span><span class="sxs-lookup"><span data-stu-id="c7fe3-107">These lessons teach you the fundamentals of the C# language.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="c7fe3-108">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="c7fe3-108">Prerequisites</span></span>

<span data-ttu-id="c7fe3-109">Öğretici, yerel geliştirme için ayarlanmış bir makineniz olmasını bekler.</span><span class="sxs-lookup"><span data-stu-id="c7fe3-109">The tutorial expects that you have a machine set up for local development.</span></span> <span data-ttu-id="c7fe3-110">Windows, Linux veya macOS 'ta, uygulamaları oluşturmak, derlemek ve çalıştırmak için .NET CLı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c7fe3-110">On Windows, Linux, or macOS, you can use the .NET CLI to create, build, and run applications.</span></span> <span data-ttu-id="c7fe3-111">Mac ve Windows 'da, Visual Studio 2019 ' i kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c7fe3-111">On Mac and Windows, you can use Visual Studio 2019.</span></span> <span data-ttu-id="c7fe3-112">Kurulum yönergeleri için bkz. [Yerel ortamınızı ayarlama](local-environment.md).</span><span class="sxs-lookup"><span data-stu-id="c7fe3-112">For setup instructions, see [Set up your local environment](local-environment.md).</span></span>

## <a name="make-decisions-using-the-if-statement"></a><span data-ttu-id="c7fe3-113">İfadesini kullanarak kararlar alın `if`</span><span class="sxs-lookup"><span data-stu-id="c7fe3-113">Make decisions using the `if` statement</span></span>

<span data-ttu-id="c7fe3-114">Dallar adlı bir dizin oluşturun *-öğretici*.</span><span class="sxs-lookup"><span data-stu-id="c7fe3-114">Create a directory named *branches-tutorial*.</span></span> <span data-ttu-id="c7fe3-115">Geçerli dizini yapın ve şu komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="c7fe3-115">Make that the current directory and run the following command:</span></span>

```dotnetcli
dotnet new console -n BranchesAndLoops -o .
```

<span data-ttu-id="c7fe3-116">Bu komut geçerli dizinde yeni bir .NET konsol uygulaması oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c7fe3-116">This command creates a new .NET console application in the current directory.</span></span> <span data-ttu-id="c7fe3-117">*Program. cs* ' yi en sevdiğiniz düzenleyicide açın ve içeriği şu kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="c7fe3-117">Open *Program.cs* in your favorite editor, and replace the contents with the following code:</span></span>

```csharp
using System;

int a = 5;
int b = 6;
if (a + b > 10)
    Console.WriteLine("The answer is greater than 10.");
```

<span data-ttu-id="c7fe3-118">Konsol pencerenizi yazarak bu kodu deneyin `dotnet run` .</span><span class="sxs-lookup"><span data-stu-id="c7fe3-118">Try this code by typing `dotnet run` in your console window.</span></span> <span data-ttu-id="c7fe3-119">"Yanıt 10 ' dan büyük" iletisini görmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="c7fe3-119">You should see the message "The answer is greater than 10."</span></span> <span data-ttu-id="c7fe3-120">konsolunuza yazdırılır.</span><span class="sxs-lookup"><span data-stu-id="c7fe3-120">printed to your console.</span></span> <span data-ttu-id="c7fe3-121">`b` tanımlamasını toplamın 10’dan küçük olacağı şekilde değiştirin:</span><span class="sxs-lookup"><span data-stu-id="c7fe3-121">Modify the declaration of `b` so that the sum is less than 10:</span></span>

```csharp
int b = 3;
```

<span data-ttu-id="c7fe3-122">`dotnet run`Yeniden yazın.</span><span class="sxs-lookup"><span data-stu-id="c7fe3-122">Type `dotnet run` again.</span></span> <span data-ttu-id="c7fe3-123">Yanıt 10’dan küçük olduğundan herhangi bir şey yazdırılmaz.</span><span class="sxs-lookup"><span data-stu-id="c7fe3-123">Because the answer is less than 10, nothing is printed.</span></span> <span data-ttu-id="c7fe3-124">Test ettiğiniz **koşul** false değerindedir.</span><span class="sxs-lookup"><span data-stu-id="c7fe3-124">The **condition** you're testing is false.</span></span> <span data-ttu-id="c7fe3-125">Bir `if` deyimi için olası dallardan yalnızca birini (true dalı) yazdığınızdan, yürütülecek herhangi bir kodunuz yoktur.</span><span class="sxs-lookup"><span data-stu-id="c7fe3-125">You don't have any code to execute because you've only written one of the possible branches for an `if` statement: the true branch.</span></span>

> [!TIP]
> <span data-ttu-id="c7fe3-126">C# dilini (veya herhangi bir programlama dilini) keşfederken, kod yazdığınızda hatalar yapacaksınız.</span><span class="sxs-lookup"><span data-stu-id="c7fe3-126">As you explore C# (or any programming language), you'll make mistakes when you write code.</span></span> <span data-ttu-id="c7fe3-127">Derleyici hataları bulacak ve rapor eder.</span><span class="sxs-lookup"><span data-stu-id="c7fe3-127">The compiler will find and report the errors.</span></span> <span data-ttu-id="c7fe3-128">Hata çıktısına ve hatayı oluşturan koda yakından bakın.</span><span class="sxs-lookup"><span data-stu-id="c7fe3-128">Look closely at the error output and the code that generated the error.</span></span> <span data-ttu-id="c7fe3-129">Derleyici hatası genellikle sorunu bulmanıza yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="c7fe3-129">The compiler error can usually help you find the problem.</span></span>

<span data-ttu-id="c7fe3-130">Bu ilk örnek, `if` ve Boolean türlerin gücünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="c7fe3-130">This first sample shows the power of `if` and Boolean types.</span></span> <span data-ttu-id="c7fe3-131">*Boolean* , iki değerden birine sahip olabilir bir değişkendir: `true` veya `false` .</span><span class="sxs-lookup"><span data-stu-id="c7fe3-131">A *Boolean* is a variable that can have one of two values: `true` or `false`.</span></span> <span data-ttu-id="c7fe3-132">C#, Boole değişkenleri için özel bir tür tanımlar `bool` .</span><span class="sxs-lookup"><span data-stu-id="c7fe3-132">C# defines a special type, `bool` for Boolean variables.</span></span> <span data-ttu-id="c7fe3-133">`if` deyimi bir `bool` için değeri kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="c7fe3-133">The `if` statement checks the value of a `bool`.</span></span> <span data-ttu-id="c7fe3-134">Değer `true` olduğunda, `if` deyiminden sonra gelen deyim yürütülür.</span><span class="sxs-lookup"><span data-stu-id="c7fe3-134">When the value is `true`, the statement following the `if` executes.</span></span> <span data-ttu-id="c7fe3-135">Aksi takdirde, atlanır.</span><span class="sxs-lookup"><span data-stu-id="c7fe3-135">Otherwise, it's skipped.</span></span> <span data-ttu-id="c7fe3-136">Bu koşullara göre koşulları denetleme ve deyimleri yürütme işlemi güçlü bir işlemdir.</span><span class="sxs-lookup"><span data-stu-id="c7fe3-136">This process of checking conditions and executing statements based on those conditions is powerful.</span></span>

## <a name="make-if-and-else-work-together"></a><span data-ttu-id="c7fe3-137">if ve else koşullarını birlikte çalıştırma</span><span class="sxs-lookup"><span data-stu-id="c7fe3-137">Make if and else work together</span></span>

<span data-ttu-id="c7fe3-138">Hem true hem de false dallarında farklı kod yürütmek için, koşul false olduğunda yürütülen bir `else` dalı oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="c7fe3-138">To execute different code in both the true and false branches, you create an `else` branch that executes when the condition is false.</span></span> <span data-ttu-id="c7fe3-139">Bir `else` dal deneyin.</span><span class="sxs-lookup"><span data-stu-id="c7fe3-139">Try an `else` branch.</span></span> <span data-ttu-id="c7fe3-140">Aşağıdaki koda son iki satırı ekleyin (ilk dördü zaten olmalıdır):</span><span class="sxs-lookup"><span data-stu-id="c7fe3-140">Add the last two lines in the code below (you should already have the first four):</span></span>

```csharp
int a = 5;
int b = 3;
if (a + b > 10)
    Console.WriteLine("The answer is greater than 10");
else
    Console.WriteLine("The answer is not greater than 10");
```

<span data-ttu-id="c7fe3-141">`else` anahtar sözcüğünden sonraki deyim, yalnızca test edilen koşul `false` olduğunda yürütülür.</span><span class="sxs-lookup"><span data-stu-id="c7fe3-141">The statement following the `else` keyword executes only when the condition being tested is `false`.</span></span> <span data-ttu-id="c7fe3-142">`if`Ve `else` Boolean koşulları ile birleştirmek, hem hem de bir koşulu işlemek için ihtiyacınız olan tüm gücü sağlar `true` `false` .</span><span class="sxs-lookup"><span data-stu-id="c7fe3-142">Combining `if` and `else` with Boolean conditions provides all the power you need to handle both a `true` and a `false` condition.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c7fe3-143">`if` ve `else` deyimlerinin altındaki girinti, insan okuyuculara yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="c7fe3-143">The indentation under the `if` and `else` statements is for human readers.</span></span> <span data-ttu-id="c7fe3-144">C# dili, girintileme veya boşluk olarak kabul etmez.</span><span class="sxs-lookup"><span data-stu-id="c7fe3-144">The C# language doesn't treat indentation or white space as significant.</span></span> <span data-ttu-id="c7fe3-145">`if` veya `else` anahtar sözcüğünden sonra gelen deyim, koşula bağlı olarak yürütülür.</span><span class="sxs-lookup"><span data-stu-id="c7fe3-145">The statement following the `if` or `else` keyword will be executed based on the condition.</span></span> <span data-ttu-id="c7fe3-146">Bu öğreticideki tüm örnekler, ifadelerin denetim akışına göre satırları girintilemek için ortak bir uygulama izler.</span><span class="sxs-lookup"><span data-stu-id="c7fe3-146">All the samples in this tutorial follow a common practice to indent lines based on the control flow of statements.</span></span>

<span data-ttu-id="c7fe3-147">Girintileme önemli olmadığından, `{` `}` çok sayıda deyimin koşullu olarak yürütülen bloğun bir parçası olmasını istediğiniz zaman göstermek için ve kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="c7fe3-147">Because indentation isn't significant, you need to use `{` and `}` to indicate when you want more than one statement to be part of the block that executes conditionally.</span></span> <span data-ttu-id="c7fe3-148">C# programcıları bu ayraçları genellikle tüm `if` and `else` tümcelerinde kullanır.</span><span class="sxs-lookup"><span data-stu-id="c7fe3-148">C# programmers typically use those braces on all `if` and `else` clauses.</span></span> <span data-ttu-id="c7fe3-149">Aşağıdaki örnek, oluşturduğunuz bir ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="c7fe3-149">The following example is the same as the one you created.</span></span> <span data-ttu-id="c7fe3-150">Yukarıdaki kodu aşağıdaki kodla eşleşecek şekilde değiştirin:</span><span class="sxs-lookup"><span data-stu-id="c7fe3-150">Modify your code above to match the following code:</span></span>

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
> <span data-ttu-id="c7fe3-151">Bu öğreticinin geri kalanında, kod örnekleri, kabul edilen uygulamaları takip eden ayraçları içerir.</span><span class="sxs-lookup"><span data-stu-id="c7fe3-151">Through the rest of this tutorial, the code samples all include the braces, following accepted practices.</span></span>

<span data-ttu-id="c7fe3-152">Daha karmaşık koşulları test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c7fe3-152">You can test more complicated conditions.</span></span> <span data-ttu-id="c7fe3-153">Şu ana kadar yazdığınız koddan sonra aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="c7fe3-153">Add the following code after the code you've written so far:</span></span>

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

<span data-ttu-id="c7fe3-154">`==` *Eşitlik* için simge testi.</span><span class="sxs-lookup"><span data-stu-id="c7fe3-154">The `==` symbol tests for *equality*.</span></span> <span data-ttu-id="c7fe3-155">`==`' Yi kullanarak, ' de gördüğünüz şekilde testi, atamanın eşitliğine ayırır `a = 5` .</span><span class="sxs-lookup"><span data-stu-id="c7fe3-155">Using `==` distinguishes the test for equality from assignment, which you saw in `a = 5`.</span></span>

<span data-ttu-id="c7fe3-156">`&&` "ve" sözcüğünü ifade eder.</span><span class="sxs-lookup"><span data-stu-id="c7fe3-156">The `&&` represents "and".</span></span> <span data-ttu-id="c7fe3-157">Bu, deyimi true dalında yürütmek için her iki koşulun da true olması gerektiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="c7fe3-157">It means both conditions must be true to execute the statement in the true branch.</span></span>  <span data-ttu-id="c7fe3-158">Bu örnekler aynı zamanda, `{` ve `}` ayraçları içine alınmaları koşuluyla her koşullu dalda birden çok deyime sahip olabileceğinizi de gösterir.</span><span class="sxs-lookup"><span data-stu-id="c7fe3-158">These examples also show that you can have multiple statements in each conditional branch, provided you enclose them in `{` and `}`.</span></span> <span data-ttu-id="c7fe3-159">`||`"Veya" öğesini göstermek için de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c7fe3-159">You can also use  `||` to represent "or".</span></span> <span data-ttu-id="c7fe3-160">Şu ana kadar yazıldıktan sonra aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="c7fe3-160">Add the following code after what you've written so far:</span></span>

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

<span data-ttu-id="c7fe3-161">, Ve değerlerini değiştirin `a` ve `b` `c` arasında geçiş yapın `&&` `||` .</span><span class="sxs-lookup"><span data-stu-id="c7fe3-161">Modify the values of `a`, `b`, and `c` and switch between `&&` and `||` to explore.</span></span> <span data-ttu-id="c7fe3-162">Ve işleçlerinin nasıl çalıştığını daha fazla anlayacaksınız `&&` `||` .</span><span class="sxs-lookup"><span data-stu-id="c7fe3-162">You'll gain more understanding of how the `&&` and `||` operators work.</span></span>

<span data-ttu-id="c7fe3-163">İlk adımı tamamladınız.</span><span class="sxs-lookup"><span data-stu-id="c7fe3-163">You've finished the first step.</span></span> <span data-ttu-id="c7fe3-164">Sonraki bölüme başlamadan önce geçerli kodu ayrı bir yönteme taşıyalim.</span><span class="sxs-lookup"><span data-stu-id="c7fe3-164">Before you start the next section, let's move the current code into a separate method.</span></span> <span data-ttu-id="c7fe3-165">Bu, yeni bir örnekle çalışmaya başlamasını kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="c7fe3-165">That makes it easier to start working with a new example.</span></span> <span data-ttu-id="c7fe3-166">Var olan kodu adlı bir metoda koyun `ExploreIf()` .</span><span class="sxs-lookup"><span data-stu-id="c7fe3-166">Put the existing code in a method called `ExploreIf()`.</span></span> <span data-ttu-id="c7fe3-167">Programınızın en üstünden bunu çağırın.</span><span class="sxs-lookup"><span data-stu-id="c7fe3-167">Call it from the top of your program.</span></span> <span data-ttu-id="c7fe3-168">Bu değişiklikleri tamamladığınızda kodunuzun aşağıdaki gibi görünmesi gerekir:</span><span class="sxs-lookup"><span data-stu-id="c7fe3-168">When you finished those changes, your code should look like the following:</span></span>

```csharp
using System;

ExploreIf();

void ExploreIf()
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
```

<span data-ttu-id="c7fe3-169">Çağrısını not edin `ExploreIf()` .</span><span class="sxs-lookup"><span data-stu-id="c7fe3-169">Comment out the call to `ExploreIf()`.</span></span> <span data-ttu-id="c7fe3-170">Bu bölümde çalışırken çıktının daha az karışık hale gelir:</span><span class="sxs-lookup"><span data-stu-id="c7fe3-170">It will make the output less cluttered as you work in this section:</span></span>

```csharp
//ExploreIf();
```

<span data-ttu-id="c7fe3-171">`//`C# dilinde bir **Açıklama** başlatır.</span><span class="sxs-lookup"><span data-stu-id="c7fe3-171">The `//` starts a **comment** in C#.</span></span> <span data-ttu-id="c7fe3-172">Açıklamalar, kaynak kodunuzda tutmak istediğiniz tüm metinlerdir, ancak kod olarak yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="c7fe3-172">Comments are any text you want to keep in your source code but not execute as code.</span></span> <span data-ttu-id="c7fe3-173">Derleyici açıklamalardan herhangi bir yürütülebilir kod oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="c7fe3-173">The compiler doesn't generate any executable code from comments.</span></span>

## <a name="use-loops-to-repeat-operations"></a><span data-ttu-id="c7fe3-174">İşlemleri yinelemek için döngüleri kullanma</span><span class="sxs-lookup"><span data-stu-id="c7fe3-174">Use loops to repeat operations</span></span>

<span data-ttu-id="c7fe3-175">Bu bölümde, deyimlerini yinelemek için **döngüleri** kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="c7fe3-175">In this section, you use **loops** to repeat statements.</span></span> <span data-ttu-id="c7fe3-176">Çağrısından sonra bu kodu ekleyin `ExploreIf` :</span><span class="sxs-lookup"><span data-stu-id="c7fe3-176">Add this code after the call to `ExploreIf`:</span></span>

```csharp
int counter = 0;
while (counter < 10)
{
    Console.WriteLine($"Hello World! The counter is {counter}");
    counter++;
}
```

<span data-ttu-id="c7fe3-177">`while`İfade bir koşulu denetler ve öğesinden sonra deyimin veya bildiri bloğunu yürütür `while` .</span><span class="sxs-lookup"><span data-stu-id="c7fe3-177">The `while` statement checks a condition and executes the statement or statement block following the `while`.</span></span> <span data-ttu-id="c7fe3-178">Koşul false olana kadar durumu sürekli olarak denetler ve bu deyimleri gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="c7fe3-178">It repeatedly checks the condition and executing those statements until the condition is false.</span></span>

<span data-ttu-id="c7fe3-179">Bu örnekte diğer bir yeni işleç mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="c7fe3-179">There's one other new operator in this example.</span></span> <span data-ttu-id="c7fe3-180">`counter` değişkeninden sonra gelen `++`, **artırma** işlecidir.</span><span class="sxs-lookup"><span data-stu-id="c7fe3-180">The `++` after the `counter` variable is the **increment** operator.</span></span> <span data-ttu-id="c7fe3-181">Değerine 1 ekler `counter` ve bu değeri `counter` değişkende depolar.</span><span class="sxs-lookup"><span data-stu-id="c7fe3-181">It adds 1 to the value of `counter` and stores that value in the `counter` variable.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c7fe3-182">`while`Kodu yürüttüğünüzde döngü koşulunun yanlış olarak değiştiği emin olun.</span><span class="sxs-lookup"><span data-stu-id="c7fe3-182">Make sure that the `while` loop condition changes to false as you execute the code.</span></span> <span data-ttu-id="c7fe3-183">Aksi halde, programınızın hiç sona ermediği **sonsuz bir döngü** oluşturmuş olursunuz.</span><span class="sxs-lookup"><span data-stu-id="c7fe3-183">Otherwise, you create an **infinite loop** where your program never ends.</span></span> <span data-ttu-id="c7fe3-184">Bu örnekte gösterilmediği için, programınızı **CTRL-C** veya başka yollarla çıkmaya zorlamaya zorlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="c7fe3-184">That is not demonstrated in this sample, because you have to force your program to quit using **CTRL-C** or other means.</span></span>

<span data-ttu-id="c7fe3-185">`while` döngüsü, `while` koşulundan sonraki kodu yürütmeden önce koşulu test eder.</span><span class="sxs-lookup"><span data-stu-id="c7fe3-185">The `while` loop tests the condition before executing the code following the `while`.</span></span> <span data-ttu-id="c7fe3-186">`do` ... `while` döngüsü önce kodu yürütür, sonra koşulu kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="c7fe3-186">The `do` ... `while` loop executes the code first, and then checks the condition.</span></span> <span data-ttu-id="c7fe3-187">*Do while* döngüsü aşağıdaki kodda gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="c7fe3-187">The *do while* loop is shown in the following code:</span></span>

```csharp
int counter = 0;
do
{
    Console.WriteLine($"Hello World! The counter is {counter}");
    counter++;
} while (counter < 10);
```

<span data-ttu-id="c7fe3-188">Bu `do` döngü ve önceki `while` döngü aynı çıktıyı üretir.</span><span class="sxs-lookup"><span data-stu-id="c7fe3-188">This `do` loop and the earlier `while` loop produce the same output.</span></span>

## <a name="work-with-the-for-loop"></a><span data-ttu-id="c7fe3-189">For döngüsü ile çalışma</span><span class="sxs-lookup"><span data-stu-id="c7fe3-189">Work with the for loop</span></span>

<span data-ttu-id="c7fe3-190">**For** döngüsü genellikle C# dilinde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c7fe3-190">The **for** loop is commonly used in C#.</span></span> <span data-ttu-id="c7fe3-191">Şu kodu deneyin:</span><span class="sxs-lookup"><span data-stu-id="c7fe3-191">Try this code:</span></span>

```csharp
for (int index = 0; index < 10; index++)
{
    Console.WriteLine($"Hello World! The index is {index}");
}
```

<span data-ttu-id="c7fe3-192">Önceki kod, `while` döngüyle aynı çalışmayı ve `do` zaten kullandığınız döngüyü yapar.</span><span class="sxs-lookup"><span data-stu-id="c7fe3-192">The previous code does the same work as the `while` loop and the `do` loop you've already used.</span></span> <span data-ttu-id="c7fe3-193">`for` deyiminde, bunu nasıl çalıştığını denetleyen üç bölüm bulunur.</span><span class="sxs-lookup"><span data-stu-id="c7fe3-193">The `for` statement has three parts that control how it works.</span></span>

<span data-ttu-id="c7fe3-194">İlk bölüm **for başlatıcıdır**: `int index = 0;` Loop değişkeni olduğunu bildirir `index` ve başlangıç değerini olarak ayarlar `0` .</span><span class="sxs-lookup"><span data-stu-id="c7fe3-194">The first part is the **for initializer**: `int index = 0;` declares that `index` is the loop variable, and sets its initial value to `0`.</span></span>

<span data-ttu-id="c7fe3-195">Orta kısım **for koşuludur**: `index < 10` `for` sayacın değeri 10 ' dan az olduğu sürece bu döngünün yürütülmeye devam ettiğini bildirir.</span><span class="sxs-lookup"><span data-stu-id="c7fe3-195">The middle part is the **for condition**: `index < 10` declares that this `for` loop continues to execute as long as the value of counter is less than 10.</span></span>

<span data-ttu-id="c7fe3-196">Son bölüm, **Yineleyici için**: `index++` deyimden sonra blok yürütüldükten sonra döngü değişkeninin nasıl değiştirileceğini belirtir `for` .</span><span class="sxs-lookup"><span data-stu-id="c7fe3-196">The final part is the **for iterator**: `index++` specifies how to modify the loop variable after executing the block following the `for` statement.</span></span> <span data-ttu-id="c7fe3-197">Bu bölüm, bloğun her yürütme işleminde `index` değişkeninin 1 artırılması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="c7fe3-197">Here, it specifies that `index` should be incremented by 1 each time the block executes.</span></span>

<span data-ttu-id="c7fe3-198">Kendiniz deneyin.</span><span class="sxs-lookup"><span data-stu-id="c7fe3-198">Experiment yourself.</span></span> <span data-ttu-id="c7fe3-199">Aşağıdaki çeşitlemelerin her birini deneyin:</span><span class="sxs-lookup"><span data-stu-id="c7fe3-199">Try each of the following variations:</span></span>

- <span data-ttu-id="c7fe3-200">Farklı bir değerde başlamak için başlatıcıyı değiştirin.</span><span class="sxs-lookup"><span data-stu-id="c7fe3-200">Change the initializer to start at a different value.</span></span>
- <span data-ttu-id="c7fe3-201">Farklı bir değerde durmak için koşulu değiştirin.</span><span class="sxs-lookup"><span data-stu-id="c7fe3-201">Change the condition to stop at a different value.</span></span>

<span data-ttu-id="c7fe3-202">İşiniz bittiğinde öğrendiklerinizi kullanmak için kendi kendinize kod yazma adımına geçelim.</span><span class="sxs-lookup"><span data-stu-id="c7fe3-202">When you're done, let's move on to write some code yourself to use what you've learned.</span></span>

<span data-ttu-id="c7fe3-203">Bu öğreticide kapsanmayan başka bir döngü bildirisi vardır: `foreach` ifade.</span><span class="sxs-lookup"><span data-stu-id="c7fe3-203">There's one other looping statement that isn't covered in this tutorial: the `foreach` statement.</span></span> <span data-ttu-id="c7fe3-204">`foreach`İfade, öğe dizisindeki her öğe için kendi ifadesini yineler.</span><span class="sxs-lookup"><span data-stu-id="c7fe3-204">The `foreach` statement repeats its statement for every item in a sequence of items.</span></span> <span data-ttu-id="c7fe3-205">En sık *koleksiyonlarla* birlikte kullanılır, bu nedenle sonraki öğreticide ele alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="c7fe3-205">It's most often used with *collections*, so it's covered in the next tutorial.</span></span>

## <a name="created-nested-loops"></a><span data-ttu-id="c7fe3-206">İç içe geçmiş döngüler oluşturuldu</span><span class="sxs-lookup"><span data-stu-id="c7fe3-206">Created nested loops</span></span>

<span data-ttu-id="c7fe3-207">Bir `while` , `do` veya `for` döngüsü, iç döngüde her öğe ile dış döngüdeki her bir öğenin birleşimini kullanarak bir matris oluşturmak için başka bir döngünün içinde iç içe olabilir.</span><span class="sxs-lookup"><span data-stu-id="c7fe3-207">A `while`, `do`, or `for` loop can be nested inside another loop to create a matrix using the combination of each item in the outer loop with each item in the inner loop.</span></span> <span data-ttu-id="c7fe3-208">Satırları ve sütunları temsil etmek için alfasayısal çiftler kümesi oluşturmayı görelim.</span><span class="sxs-lookup"><span data-stu-id="c7fe3-208">Let's do that to build a set of alphanumeric pairs to represent rows and columns.</span></span>

<span data-ttu-id="c7fe3-209">Bir `for` döngü satırları oluşturabilir:</span><span class="sxs-lookup"><span data-stu-id="c7fe3-209">One `for` loop can generate the rows:</span></span>

```csharp
for (int row = 1; row < 11; row++)
{
    Console.WriteLine($"The row is {row}");
}
```

<span data-ttu-id="c7fe3-210">Şu sütunları başka bir döngü oluşturabilir:</span><span class="sxs-lookup"><span data-stu-id="c7fe3-210">Another loop can generate the columns:</span></span>

```csharp
for (char column = 'a'; column < 'k'; column++)
{
    Console.WriteLine($"The column is {column}");
}
```

<span data-ttu-id="c7fe3-211">Bir döngüyü diğerinin içine, çiftler halinde iç içe geçirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="c7fe3-211">You can nest one loop inside the other to form pairs:</span></span>

```csharp
for (int row = 1; row < 11; row++)
{
    for (char column = 'a'; column < 'k'; column++)
    {
        Console.WriteLine($"The cell is ({row}, {column})");
    }
}
```

<span data-ttu-id="c7fe3-212">İç döngünün her tam çalışması için dış döngünün bir kez artıyor olduğunu görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c7fe3-212">You can see that the outer loop increments once for each full run of the inner loop.</span></span> <span data-ttu-id="c7fe3-213">Satır ve sütun iç içe geçirmeyi tersine çevirin ve yaptığınız değişiklikleri kendiniz görün.</span><span class="sxs-lookup"><span data-stu-id="c7fe3-213">Reverse the row and column nesting, and see the changes for yourself.</span></span> <span data-ttu-id="c7fe3-214">İşiniz bittiğinde, kodu bu bölümden adlı bir yönteme koyun `ExploreLoops()` .</span><span class="sxs-lookup"><span data-stu-id="c7fe3-214">When you're done, place the code from this section in a method called `ExploreLoops()`.</span></span>

## <a name="combine-branches-and-loops"></a><span data-ttu-id="c7fe3-215">Dalları ve döngüleri birleştirme</span><span class="sxs-lookup"><span data-stu-id="c7fe3-215">Combine branches and loops</span></span>

<span data-ttu-id="c7fe3-216">C# dilinde `if` deyimini ve döngü yapılarını gördüğünüze göre şimdi 1 ile 20 arasında olup 3’e bölünebilen tüm tamsayıların toplamını bulmak için C# kodu yazmayı deneyin.</span><span class="sxs-lookup"><span data-stu-id="c7fe3-216">Now that you've seen the `if` statement and the looping constructs in the C# language, see if you can write C# code to find the sum of all integers 1 through 20 that are divisible by 3.</span></span>  <span data-ttu-id="c7fe3-217">Aşağıdaki ipuçlarından yararlanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="c7fe3-217">Here are a few hints:</span></span>

- <span data-ttu-id="c7fe3-218">`%` işleci size bölme işlemindeki kalanı verir.</span><span class="sxs-lookup"><span data-stu-id="c7fe3-218">The `%` operator gives you the remainder of a division operation.</span></span>
- <span data-ttu-id="c7fe3-219">`if` deyimi bir sayının toplama dahil edilip edilmemesi gerektiğini görmeniz için size koşulu verir.</span><span class="sxs-lookup"><span data-stu-id="c7fe3-219">The `if` statement gives you the condition to see if a number should be part of the sum.</span></span>
- <span data-ttu-id="c7fe3-220">`for` döngüsü 1 ile 20 arasındaki tüm sayılar için bir dizi adımı yinelemenize yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="c7fe3-220">The `for` loop can help you repeat a series of steps for all the numbers 1 through 20.</span></span>

<span data-ttu-id="c7fe3-221">Kendiniz deneyin.</span><span class="sxs-lookup"><span data-stu-id="c7fe3-221">Try it yourself.</span></span> <span data-ttu-id="c7fe3-222">Daha sonra başarılı olup olmadığınıza bakın.</span><span class="sxs-lookup"><span data-stu-id="c7fe3-222">Then check how you did.</span></span> <span data-ttu-id="c7fe3-223">Yanıt için 63 almalısınız.</span><span class="sxs-lookup"><span data-stu-id="c7fe3-223">You should get 63 for an answer.</span></span> <span data-ttu-id="c7fe3-224">[GitHub 'da tamamlanan kodu görüntüleyerek](https://github.com/dotnet/samples/tree/main/csharp/branches-quickstart/Program.cs#L46-L54)olası bir yanıt görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c7fe3-224">You can see one possible answer by [viewing the completed code on GitHub](https://github.com/dotnet/samples/tree/main/csharp/branches-quickstart/Program.cs#L46-L54).</span></span>

<span data-ttu-id="c7fe3-225">"Dallar ve döngüler" öğreticisini tamamladınız.</span><span class="sxs-lookup"><span data-stu-id="c7fe3-225">You've completed the "branches and loops" tutorial.</span></span>

<span data-ttu-id="c7fe3-226">Kendi geliştirme ortamınızda [diziler ve koleksiyonlar](arrays-and-collections.md) öğreticisiyle devam edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c7fe3-226">You can continue with the [Arrays and collections](arrays-and-collections.md) tutorial in your own development environment.</span></span>

<span data-ttu-id="c7fe3-227">Aşağıdaki makalelerde bu kavramlar hakkında daha fazla bilgi edinebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="c7fe3-227">You can learn more about these concepts in these articles:</span></span>

- [<span data-ttu-id="c7fe3-228">If ve else deyimi</span><span class="sxs-lookup"><span data-stu-id="c7fe3-228">If and else statement</span></span>](../../language-reference/keywords/if-else.md)
- [<span data-ttu-id="c7fe3-229">While ekstresi</span><span class="sxs-lookup"><span data-stu-id="c7fe3-229">While statement</span></span>](../../language-reference/keywords/while.md)
- [<span data-ttu-id="c7fe3-230">Do deyimi</span><span class="sxs-lookup"><span data-stu-id="c7fe3-230">Do statement</span></span>](../../language-reference/keywords/do.md)
- [<span data-ttu-id="c7fe3-231">For deyimleri</span><span class="sxs-lookup"><span data-stu-id="c7fe3-231">For statement</span></span>](../../language-reference/keywords/for.md)
