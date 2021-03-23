---
title: C# dilinde sayılar-C# öğreticisine giriş
description: Sayısal türleri, kullanımları, özellikleri ve yöntemleri inceleyerek C# hakkında bilgi edinin.
ms.date: 02/05/2021
ms.openlocfilehash: d6546fc8ac2609066a4f9b829749a4091fce7ce6
ms.sourcegitcommit: 5ce37699c2a51ed173171813be68ef7577b1aba5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/23/2021
ms.locfileid: "104881113"
---
# <a name="manipulate-integral-and-floating-point-numbers-in-c"></a><span data-ttu-id="c7687-103">C 'de integral ve kayan nokta numaralarını işleme\#</span><span class="sxs-lookup"><span data-stu-id="c7687-103">Manipulate integral and floating point numbers in C\#</span></span>

<span data-ttu-id="c7687-104">Bu öğretici, C# ' deki sayısal türleri etkileşimli olarak size öğretir.</span><span class="sxs-lookup"><span data-stu-id="c7687-104">This tutorial teaches you about the numeric types in C# interactively.</span></span> <span data-ttu-id="c7687-105">Küçük miktarlarda kod yazacaksınız, daha sonra bu kodu derleyip çalıştıracaksınız.</span><span class="sxs-lookup"><span data-stu-id="c7687-105">You'll write small amounts of code, then you'll compile and run that code.</span></span> <span data-ttu-id="c7687-106">Öğretici, C# ' de sayıları ve matematik işlemlerini keşfetmenizi sağlayan bir dizi ders içerir.</span><span class="sxs-lookup"><span data-stu-id="c7687-106">The tutorial contains a series of lessons that explore numbers and math operations in C#.</span></span> <span data-ttu-id="c7687-107">Bu dersler size C# dilinin temel özelliklerini öğretir.</span><span class="sxs-lookup"><span data-stu-id="c7687-107">These lessons teach you the fundamentals of the C# language.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="c7687-108">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="c7687-108">Prerequisites</span></span>

<span data-ttu-id="c7687-109">Öğretici, yerel geliştirme için ayarlanmış bir makineniz olmasını bekler.</span><span class="sxs-lookup"><span data-stu-id="c7687-109">The tutorial expects that you have a machine set up for local development.</span></span> <span data-ttu-id="c7687-110">Windows, Linux veya macOS 'ta, uygulamaları oluşturmak, derlemek ve çalıştırmak için .NET CLı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c7687-110">On Windows, Linux, or macOS, you can use the .NET CLI to create, build, and run applications.</span></span> <span data-ttu-id="c7687-111">Mac veya Windows üzerinde Visual Studio 2019 ' i kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c7687-111">On Mac or Windows, you can use Visual Studio 2019.</span></span> <span data-ttu-id="c7687-112">Kurulum yönergeleri için bkz. [Yerel ortamınızı ayarlama](local-environment.md).</span><span class="sxs-lookup"><span data-stu-id="c7687-112">For setup instructions, see [Set up your local environment](local-environment.md).</span></span>

## <a name="explore-integer-math"></a><span data-ttu-id="c7687-113">Tamsayı matematiğini inceleme</span><span class="sxs-lookup"><span data-stu-id="c7687-113">Explore integer math</span></span>

<span data-ttu-id="c7687-114">Sayı adlı bir dizin oluşturun *-hızlı başlangıç*.</span><span class="sxs-lookup"><span data-stu-id="c7687-114">Create a directory named *numbers-quickstart*.</span></span> <span data-ttu-id="c7687-115">Geçerli dizin yapın ve şu komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="c7687-115">Make it the current directory and run the following command:</span></span>

```dotnetcli
dotnet new console -n NumbersInCSharp -o .
```

<span data-ttu-id="c7687-116">En sevdiğiniz düzenleyicide *program. cs* dosyasını açın ve dosyanın içeriğini aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="c7687-116">Open *Program.cs* in your favorite editor, and replace the contents of the file with the following code:</span></span>

```csharp
using System;

int a = 18;
int b = 6;
int c = a + b;
Console.WriteLine(c);
```

<span data-ttu-id="c7687-117">Komut pencerenizi yazarak bu kodu çalıştırın `dotnet run` .</span><span class="sxs-lookup"><span data-stu-id="c7687-117">Run this code by typing `dotnet run` in your command window.</span></span>

<span data-ttu-id="c7687-118">Tamsayılarla temel matematik işlemlerinden birini gördünüz.</span><span class="sxs-lookup"><span data-stu-id="c7687-118">You've seen one of the fundamental math operations with integers.</span></span> <span data-ttu-id="c7687-119">`int`Tür bir **tamsayıyı**, sıfır, pozitif veya negatif bir tam sayıyı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="c7687-119">The `int` type represents an **integer**, a zero, positive, or negative whole number.</span></span> <span data-ttu-id="c7687-120">Toplama için `+` sembolünü kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="c7687-120">You use the `+` symbol for addition.</span></span> <span data-ttu-id="c7687-121">Tamsayılar için sıklıkla kullanılan diğer matematiksel işlemler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="c7687-121">Other common mathematical operations for integers include:</span></span>

- <span data-ttu-id="c7687-122">çıkarma için `-`</span><span class="sxs-lookup"><span data-stu-id="c7687-122">`-` for subtraction</span></span>
- <span data-ttu-id="c7687-123">çarpma için `*`</span><span class="sxs-lookup"><span data-stu-id="c7687-123">`*` for multiplication</span></span>
- <span data-ttu-id="c7687-124">bölme için `/`</span><span class="sxs-lookup"><span data-stu-id="c7687-124">`/` for division</span></span>

<span data-ttu-id="c7687-125">Bu farklı işlemleri keşfederek başlayın.</span><span class="sxs-lookup"><span data-stu-id="c7687-125">Start by exploring those different operations.</span></span> <span data-ttu-id="c7687-126">Değerini yazan satırdan sonra bu satırları ekleyin `c` :</span><span class="sxs-lookup"><span data-stu-id="c7687-126">Add these lines after the line that writes the value of `c`:</span></span>

```csharp
// subtraction
c = a - b;
Console.WriteLine(c);

// multiplication
c = a * b;
Console.WriteLine(c);

// division
c = a / b;
Console.WriteLine(c);
```

<span data-ttu-id="c7687-127">Komut pencerenizi yazarak bu kodu çalıştırın `dotnet run` .</span><span class="sxs-lookup"><span data-stu-id="c7687-127">Run this code by typing `dotnet run` in your command window.</span></span>

<span data-ttu-id="c7687-128">Ayrıca, isterseniz aynı satırda birden çok matematik işlemi yazarak da deneyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c7687-128">You can also experiment by writing multiple mathematics operations in the same line, if you'd like.</span></span> <span data-ttu-id="c7687-129">Örneğin, deneyin `c = a + b - 12 * 17;` .</span><span class="sxs-lookup"><span data-stu-id="c7687-129">Try `c = a + b - 12 * 17;` for example.</span></span> <span data-ttu-id="c7687-130">Değişkenlerin ve sabit sayıların karıştırılmasına izin verilir.</span><span class="sxs-lookup"><span data-stu-id="c7687-130">Mixing variables and constant numbers is allowed.</span></span>

> [!TIP]
> <span data-ttu-id="c7687-131">C# dilini (veya herhangi bir programlama dilini) keşfederken, kod yazdığınızda hatalar yapacaksınız.</span><span class="sxs-lookup"><span data-stu-id="c7687-131">As you explore C# (or any programming language), you'll make mistakes when you write code.</span></span> <span data-ttu-id="c7687-132">**Derleyici** bu hataları bulup size bildirir.</span><span class="sxs-lookup"><span data-stu-id="c7687-132">The **compiler** will find those errors and report them to you.</span></span> <span data-ttu-id="c7687-133">Hata mesajları içerdiğinde, nelerin düzeltileceğini görmek için örnek koda ve penceredeki koda yakından bakın.</span><span class="sxs-lookup"><span data-stu-id="c7687-133">When the contains error messages, look closely at the example code and the code in your window to see what to fix.</span></span> <span data-ttu-id="c7687-134">Bu alıştırma, C# kodunun yapısını öğrenmenize yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="c7687-134">That exercise will help you learn the structure of C# code.</span></span>

<span data-ttu-id="c7687-135">İlk adımı tamamladınız.</span><span class="sxs-lookup"><span data-stu-id="c7687-135">You've finished the first step.</span></span> <span data-ttu-id="c7687-136">Sonraki bölüme başlamadan önce geçerli kodu ayrı bir *yönteme* taşıyalim.</span><span class="sxs-lookup"><span data-stu-id="c7687-136">Before you start the next section, let's move the current code into a separate *method*.</span></span> <span data-ttu-id="c7687-137">Bir yöntem, birlikte gruplanmış ve bir ad verilen deyimler dizisidir.</span><span class="sxs-lookup"><span data-stu-id="c7687-137">A method is a series of statements grouped together and given a name.</span></span> <span data-ttu-id="c7687-138">Yöntemi, ardından yönteminin adını yazarak çağırabilirsiniz `()` .</span><span class="sxs-lookup"><span data-stu-id="c7687-138">You call a method by writing the method's name followed by `()`.</span></span> <span data-ttu-id="c7687-139">Kodunuzun yöntemlere düzenlenmesi, yeni bir örnekle çalışmaya başlamasını kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="c7687-139">Organizing your code into methods makes it easier to start working with a new example.</span></span> <span data-ttu-id="c7687-140">Bitirdiğinizde, kodunuzun şöyle görünmesi gerekir:</span><span class="sxs-lookup"><span data-stu-id="c7687-140">When you finish, your code should look like this:</span></span>

```csharp
using System;

WorkWithIntegers();

void WorkWithIntegers()
{
    int a = 18;
    int b = 6;
    int c = a + b;
    Console.WriteLine(c);


    // subtraction
    c = a - b;
    Console.WriteLine(c);

    // multiplication
    c = a * b;
    Console.WriteLine(c);

    // division
    c = a / b;
    Console.WriteLine(c);
}
```

<span data-ttu-id="c7687-141">Satırı `WorkWithIntegers();` yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="c7687-141">The line `WorkWithIntegers();` invokes the method.</span></span> <span data-ttu-id="c7687-142">Aşağıdaki kod yöntemini bildirir ve tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c7687-142">The following code declares the method and defines it.</span></span>

## <a name="explore-order-of-operations"></a><span data-ttu-id="c7687-143">İşlem sırasını inceleme</span><span class="sxs-lookup"><span data-stu-id="c7687-143">Explore order of operations</span></span>

<span data-ttu-id="c7687-144">Çağrısını not edin `WorkingWithIntegers()` .</span><span class="sxs-lookup"><span data-stu-id="c7687-144">Comment out the call to `WorkingWithIntegers()`.</span></span> <span data-ttu-id="c7687-145">Bu bölümde çalışırken çıktının daha az karışık hale gelir:</span><span class="sxs-lookup"><span data-stu-id="c7687-145">It will make the output less cluttered as you work in this section:</span></span>

```csharp
//WorkWithIntegers();
```

<span data-ttu-id="c7687-146">`//`C# dilinde bir **Açıklama** başlatır.</span><span class="sxs-lookup"><span data-stu-id="c7687-146">The `//` starts a **comment** in C#.</span></span> <span data-ttu-id="c7687-147">Açıklamalar, kaynak kodunuzda tutmak istediğiniz tüm metinlerdir, ancak kod olarak yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="c7687-147">Comments are any text you want to keep in your source code but not execute as code.</span></span> <span data-ttu-id="c7687-148">Derleyici açıklamalardan herhangi bir yürütülebilir kod oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="c7687-148">The compiler doesn't generate any executable code from comments.</span></span> <span data-ttu-id="c7687-149">`WorkWithIntegers()`Bir yöntem olduğundan, yalnızca bir satır için açıklama yazmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="c7687-149">Because `WorkWithIntegers()` is a method, you need to only comment out one line.</span></span>

<span data-ttu-id="c7687-150">C# dili, farklı matematik işlemlerinin önceliğini matematikte öğrendiğiniz kurallarla tutarlı bir şekilde tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c7687-150">The C# language defines the precedence of different mathematics operations with rules consistent with the rules you learned in mathematics.</span></span> <span data-ttu-id="c7687-151">Çarpma ve bölme işlemleri, toplama ve çıkarma işlemlerinden önce gelir.</span><span class="sxs-lookup"><span data-stu-id="c7687-151">Multiplication and division take precedence over addition and subtraction.</span></span> <span data-ttu-id="c7687-152">' I çağırarak ve yürüttükten sonra aşağıdaki kodu ekleyerek bunu keşfedebilirsiniz `WorkWithIntegers()` `dotnet run` :</span><span class="sxs-lookup"><span data-stu-id="c7687-152">Explore that by adding the following code after the call to `WorkWithIntegers()`, and executing `dotnet run`:</span></span>

```csharp
int a = 5;
int b = 4;
int c = 2;
int d = a + b * c;
Console.WriteLine(d);
 ```

<span data-ttu-id="c7687-153">Çıkış, çarpma işleminin toplama işleminden önce gerçekleştiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="c7687-153">The output demonstrates that the multiplication is performed before the addition.</span></span>

<span data-ttu-id="c7687-154">Önce gerçekleştirilmesini istediğiniz işlemin veya işlemlerin çevresine parantez ekleyerek farklı bir işlem sırası zorlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c7687-154">You can force a different order of operation by adding parentheses around the operation or operations you want performed first.</span></span> <span data-ttu-id="c7687-155">Aşağıdaki satırları ekleyin ve yeniden çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="c7687-155">Add the following lines and run again:</span></span>

```csharp
d = (a + b) * c;
Console.WriteLine(d);
```

<span data-ttu-id="c7687-156">Birçok farklı işlemi birleştirerek daha fazlasını keşfedin.</span><span class="sxs-lookup"><span data-stu-id="c7687-156">Explore more by combining many different operations.</span></span> <span data-ttu-id="c7687-157">Aşağıdaki satırlara benzer bir şey ekleyin.</span><span class="sxs-lookup"><span data-stu-id="c7687-157">Add something like the following lines.</span></span> <span data-ttu-id="c7687-158">`dotnet run` komutunu yeniden deneyin.</span><span class="sxs-lookup"><span data-stu-id="c7687-158">Try `dotnet run` again.</span></span>

```csharp
d = (a + b) - 6 * c + (12 * 4) / 3 + 12;
Console.WriteLine(d);
```

<span data-ttu-id="c7687-159">Tamsayılar için farklı bir davranışla karşılaşmış olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c7687-159">You may have noticed an interesting behavior for integers.</span></span> <span data-ttu-id="c7687-160">Sonucun ondalık veya kesir bölümü içermesini bekliyor olsanız da tamsayı bölme işlemi her zaman tamsayı sonucu verir.</span><span class="sxs-lookup"><span data-stu-id="c7687-160">Integer division always produces an integer result, even when you'd expect the result to include a decimal or fractional portion.</span></span>

<span data-ttu-id="c7687-161">Bu davranışı görmediyseniz, aşağıdaki kodu deneyin:</span><span class="sxs-lookup"><span data-stu-id="c7687-161">If you haven't seen this behavior, try the following code:</span></span>

```csharp
int e = 7;
int f = 4;
int g = 3;
int h = (e + f) / g;
Console.WriteLine(h);
```

<span data-ttu-id="c7687-162">`dotnet run`Sonuçları görmek için yeniden yazın.</span><span class="sxs-lookup"><span data-stu-id="c7687-162">Type `dotnet run` again to see the results.</span></span>

<span data-ttu-id="c7687-163">' In üzerine geçmeden önce, bu bölümde yazdığınız tüm kodu alıp yeni bir yönteme koyabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c7687-163">Before moving on, let's take all the code you've written in this section and put it in a new method.</span></span> <span data-ttu-id="c7687-164">Bu yeni yöntemi çağırın `OrderPrecedence` .</span><span class="sxs-lookup"><span data-stu-id="c7687-164">Call that new method `OrderPrecedence`.</span></span> <span data-ttu-id="c7687-165">Kodunuz şuna benzemelidir:</span><span class="sxs-lookup"><span data-stu-id="c7687-165">Your code should look something like this:</span></span>

```csharp
using System;

// WorkWithIntegers();
OrderPrecedence();

void WorkWithIntegers()
{
    int a = 18;
    int b = 6;
    int c = a + b;
    Console.WriteLine(c);


    // subtraction
    c = a - b;
    Console.WriteLine(c);

    // multiplication
    c = a * b;
    Console.WriteLine(c);

    // division
    c = a / b;
    Console.WriteLine(c);
}

void OrderPrecedence()
{
    int a = 5;
    int b = 4;
    int c = 2;
    int d = a + b * c;
    Console.WriteLine(d);

    d = (a + b) * c;
    Console.WriteLine(d);

    d = (a + b) - 6 * c + (12 * 4) / 3 + 12;
    Console.WriteLine(d);

    int e = 7;
    int f = 4;
    int g = 3;
    int h = (e + f) / g;
    Console.WriteLine(h);
}
```

## <a name="explore-integer-precision-and-limits"></a><span data-ttu-id="c7687-166">Tamsayı duyarlığını ve sınırlarını inceleme</span><span class="sxs-lookup"><span data-stu-id="c7687-166">Explore integer precision and limits</span></span>

<span data-ttu-id="c7687-167">Son örnek, tamsayı bölme işleminin sonucu kestiğini size göstermiştir.</span><span class="sxs-lookup"><span data-stu-id="c7687-167">That last sample showed you that integer division truncates the result.</span></span> <span data-ttu-id="c7687-168">**Geri kalanını** , **mod** işleci, karakterini kullanarak edinebilirsiniz `%` .</span><span class="sxs-lookup"><span data-stu-id="c7687-168">You can get the **remainder** by using the **modulo** operator, the `%` character.</span></span> <span data-ttu-id="c7687-169">Yöntem çağrısından sonra aşağıdaki kodu deneyin `OrderPrecedence()` :</span><span class="sxs-lookup"><span data-stu-id="c7687-169">Try the following code after the method call to `OrderPrecedence()`:</span></span>

```csharp
int a = 7;
int b = 4;
int c = 3;
int d = (a + b) / c;
int e = (a + b) % c;
Console.WriteLine($"quotient: {d}");
Console.WriteLine($"remainder: {e}");
```

<span data-ttu-id="c7687-170">C# tamsayı türü diğer bir özelliğiyle matematiksel tamsayılardan farklıdır: `int` türünün alt ve üst sınırları vardır.</span><span class="sxs-lookup"><span data-stu-id="c7687-170">The C# integer type differs from mathematical integers in one other way: the `int` type has minimum and maximum limits.</span></span> <span data-ttu-id="c7687-171">Bu sınırları görmek için bu kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="c7687-171">Add this code to see those limits:</span></span>

```csharp
int max = int.MaxValue;
int min = int.MinValue;
Console.WriteLine($"The range of integers is {min} to {max}");
```

<span data-ttu-id="c7687-172">Bir hesaplama, bu sınırları aşan bir değer veriyorsa bu, **aşağı taşma** veya **taşma** koşulunuzun olduğu anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="c7687-172">If a calculation produces a value that exceeds those limits, you have an **underflow** or **overflow** condition.</span></span> <span data-ttu-id="c7687-173">Yanıtın bir sınırdan diğerine kaydığı görülüyor.</span><span class="sxs-lookup"><span data-stu-id="c7687-173">The answer appears to wrap from one limit to the other.</span></span> <span data-ttu-id="c7687-174">Örnek görmek için bu iki satırı ekleyin:</span><span class="sxs-lookup"><span data-stu-id="c7687-174">Add these two lines to see an example:</span></span>

```csharp
int what = max + 3;
Console.WriteLine($"An example of overflow: {what}");
```

<span data-ttu-id="c7687-175">Yanıtın tam sayı alt sınırına (negatif) oldukça yakın olduğuna dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="c7687-175">Notice that the answer is very close to the minimum (negative) integer.</span></span> <span data-ttu-id="c7687-176">Bu, `min + 2` ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="c7687-176">It's the same as `min + 2`.</span></span> <span data-ttu-id="c7687-177">Toplama işlemi, tamsayılar için izin verilen değerleri **aşmıştır**.</span><span class="sxs-lookup"><span data-stu-id="c7687-177">The addition operation **overflowed** the allowed values for integers.</span></span> <span data-ttu-id="c7687-178">Taşma durumu en büyük olası tamsayı değerinden en küçük olana "kaydığından" yanıt oldukça büyük bir negatif sayıdır.</span><span class="sxs-lookup"><span data-stu-id="c7687-178">The answer is a very large negative number because an overflow "wraps around" from the largest possible integer value to the smallest.</span></span>

<span data-ttu-id="c7687-179">`int` türü, gereksinimlerinizi karşılamadığında kullanabileceğiniz farklı sınırlar ve duyarlık içeren başka sayısal türler de mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="c7687-179">There are other numeric types with different limits and precision that you would use when the `int` type doesn't meet your needs.</span></span> <span data-ttu-id="c7687-180">Daha sonra bu diğer türleri keşfedelim.</span><span class="sxs-lookup"><span data-stu-id="c7687-180">Let's explore those other types next.</span></span> <span data-ttu-id="c7687-181">Sonraki bölüme başlamadan önce, bu bölümde yazdığınız kodu ayrı bir yönteme taşıyın.</span><span class="sxs-lookup"><span data-stu-id="c7687-181">Before you start the next section, move the code you wrote in this section into a separate method.</span></span> <span data-ttu-id="c7687-182">Bunu, `TestLimits` olarak adlandırın.</span><span class="sxs-lookup"><span data-stu-id="c7687-182">Name it `TestLimits`.</span></span>

## <a name="work-with-the-double-type"></a><span data-ttu-id="c7687-183">Çift tür ile çalışma</span><span class="sxs-lookup"><span data-stu-id="c7687-183">Work with the double type</span></span>

<span data-ttu-id="c7687-184">`double` sayısal türü, çift duyarlıklı kayan noktalı bir sayıyı ifade eder.</span><span class="sxs-lookup"><span data-stu-id="c7687-184">The `double` numeric type represents a double-precision floating point number.</span></span> <span data-ttu-id="c7687-185">Bu terimler sizin için yeni olabilir.</span><span class="sxs-lookup"><span data-stu-id="c7687-185">Those terms may be new to you.</span></span> <span data-ttu-id="c7687-186">**Kayan noktalı** sayı, büyüklük açısından oldukça büyük veya küçük olabilen, tamsayı olmayan değerleri ifade etmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c7687-186">A **floating point** number is useful to represent non-integral numbers that may be very large or small in magnitude.</span></span> <span data-ttu-id="c7687-187">**Çift duyarlık** , değeri depolamak için kullanılan ikili basamak sayısını açıklayan göreli bir terimdir.</span><span class="sxs-lookup"><span data-stu-id="c7687-187">**Double-precision** is a relative term that describes the number of binary digits used to store the value.</span></span> <span data-ttu-id="c7687-188">**Çift duyarlık** sayıları, ikili basamakların sayısının **tek duyarlıklı** olarak iki katına sahiptir.</span><span class="sxs-lookup"><span data-stu-id="c7687-188">**Double precision** numbers have twice the number of binary digits as **single-precision**.</span></span> <span data-ttu-id="c7687-189">Modern bilgisayarlarda, tek duyarlık sayılarıyla çift duyarlık kullanmak daha yaygındır.</span><span class="sxs-lookup"><span data-stu-id="c7687-189">On modern computers, it's more common to use double precision than single precision numbers.</span></span> <span data-ttu-id="c7687-190">**Tek duyarlık** numaraları anahtar sözcüğü kullanılarak belirtilir `float` .</span><span class="sxs-lookup"><span data-stu-id="c7687-190">**Single precision** numbers are declared using the `float` keyword.</span></span> <span data-ttu-id="c7687-191">İnceleyelim mi?</span><span class="sxs-lookup"><span data-stu-id="c7687-191">Let's explore.</span></span> <span data-ttu-id="c7687-192">Aşağıdaki kodu ekleyin ve sonucu görüntüleyin:</span><span class="sxs-lookup"><span data-stu-id="c7687-192">Add the following code and see the result:</span></span>

```csharp
double a = 5;
double b = 4;
double c = 2;
double d = (a + b) / c;
Console.WriteLine(d);
```

<span data-ttu-id="c7687-193">Yanıtın, bölümün ondalık kısmını içerdiğine dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="c7687-193">Notice that the answer includes the decimal portion of the quotient.</span></span> <span data-ttu-id="c7687-194">Çift değerlerle biraz daha karmaşık bir ifadeyi deneyin:</span><span class="sxs-lookup"><span data-stu-id="c7687-194">Try a slightly more complicated expression with doubles:</span></span>

```csharp
double e = 19;
double f = 23;
double g = 8;
double h = (e + f) / g;
Console.WriteLine(h);
```

<span data-ttu-id="c7687-195">Çift değerin aralığı, tamsayı değerlerinden çok daha büyüktür.</span><span class="sxs-lookup"><span data-stu-id="c7687-195">The range of a double value is much greater than integer values.</span></span> <span data-ttu-id="c7687-196">Şu ana kadar yazdıklarınız için aşağıdaki kodu deneyin:</span><span class="sxs-lookup"><span data-stu-id="c7687-196">Try the following code below what you've written so far:</span></span>

```csharp
double max = double.MaxValue;
double min = double.MinValue;
Console.WriteLine($"The range of double is {min} to {max}");
```

<span data-ttu-id="c7687-197">Bu değerler bilimsel gösterimde yazdırılır.</span><span class="sxs-lookup"><span data-stu-id="c7687-197">These values are printed in scientific notation.</span></span> <span data-ttu-id="c7687-198">`E` değerinin sol tarafındaki sayı katsayıdır.</span><span class="sxs-lookup"><span data-stu-id="c7687-198">The number to the left of the `E` is the significand.</span></span> <span data-ttu-id="c7687-199">Sağ taraftaki sayı 10’un bir kuvveti olarak üstür.</span><span class="sxs-lookup"><span data-stu-id="c7687-199">The number to the right is the exponent, as a power of 10.</span></span> <span data-ttu-id="c7687-200">Matematikteki ondalık sayılar gibi C# dilindeki çift değerlerde de yuvarlama hataları olabilir.</span><span class="sxs-lookup"><span data-stu-id="c7687-200">Just like decimal numbers in math, doubles in C# can have rounding errors.</span></span> <span data-ttu-id="c7687-201">Şu kodu deneyin:</span><span class="sxs-lookup"><span data-stu-id="c7687-201">Try this code:</span></span>

```csharp
double third = 1.0 / 3.0;
Console.WriteLine(third);
```

<span data-ttu-id="c7687-202">`0.3`Yinelenen tam olarak aynı olmadığını bilirsiniz `1/3` .</span><span class="sxs-lookup"><span data-stu-id="c7687-202">You know that `0.3` repeating isn't exactly the same as `1/3`.</span></span>

<span data-ttu-id="c7687-203">***Sınama***</span><span class="sxs-lookup"><span data-stu-id="c7687-203">***Challenge***</span></span>

<span data-ttu-id="c7687-204">Türü kullanarak büyük sayılar, küçük sayılar, çarpma ve bölme ile diğer hesaplamaları deneyin `double` .</span><span class="sxs-lookup"><span data-stu-id="c7687-204">Try other calculations with large numbers, small numbers, multiplication, and division using the `double` type.</span></span> <span data-ttu-id="c7687-205">Daha karmaşık hesaplamalar deneyin.</span><span class="sxs-lookup"><span data-stu-id="c7687-205">Try more complicated calculations.</span></span> <span data-ttu-id="c7687-206">Zorluğa bir süre harcadıktan sonra yazdığınız kodu alın ve yeni bir yönteme yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="c7687-206">After you've spent some time with the challenge, take the code you've written and place it in a new method.</span></span> <span data-ttu-id="c7687-207">Yeni yönteme adlandırın `WorkWithDoubles` .</span><span class="sxs-lookup"><span data-stu-id="c7687-207">Name that new method `WorkWithDoubles`.</span></span>

## <a name="work-with-decimal-types"></a><span data-ttu-id="c7687-208">Ondalık türlerle çalışma</span><span class="sxs-lookup"><span data-stu-id="c7687-208">Work with decimal types</span></span>

<span data-ttu-id="c7687-209">C# dilinde temel sayısal türleri gördünüz: tamsayılar ve çiftler.</span><span class="sxs-lookup"><span data-stu-id="c7687-209">You've seen the basic numeric types in C#: integers and doubles.</span></span> <span data-ttu-id="c7687-210">Öğreneceğinizi öğrenmek için başka bir tür vardır: `decimal` türü.</span><span class="sxs-lookup"><span data-stu-id="c7687-210">There's one other type to learn: the `decimal` type.</span></span> <span data-ttu-id="c7687-211">`decimal` türü, `double` türünden daha küçük bir aralığa ancak daha fazla duyarlığa sahiptir.</span><span class="sxs-lookup"><span data-stu-id="c7687-211">The `decimal` type has a smaller range but greater precision than `double`.</span></span> <span data-ttu-id="c7687-212">Şimdi buna bir göz atalım:</span><span class="sxs-lookup"><span data-stu-id="c7687-212">Let's take a look:</span></span>

```csharp
decimal min = decimal.MinValue;
decimal max = decimal.MaxValue;
Console.WriteLine($"The range of the decimal type is {min} to {max}");
```

<span data-ttu-id="c7687-213">Aralığın `double` türünden daha küçük olduğuna dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="c7687-213">Notice that the range is smaller than the `double` type.</span></span> <span data-ttu-id="c7687-214">Aşağıdaki kodu deneyerek ondalık türünde daha fazla duyarlık olduğunu görebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="c7687-214">You can see the greater precision with the decimal type by trying the following code:</span></span>

```csharp
double a = 1.0;
double b = 3.0;
Console.WriteLine(a / b);

decimal c = 1.0M;
decimal d = 3.0M;
Console.WriteLine(c / d);
```

<span data-ttu-id="c7687-215">Sayılardaki `M` sonekiyle, bir sabit sayının `decimal` türünü nasıl kullanması gerektiğini belirtirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c7687-215">The `M` suffix on the numbers is how you indicate that a constant should use the `decimal` type.</span></span> <span data-ttu-id="c7687-216">Aksi takdirde, derleyici türü varsayar `double` .</span><span class="sxs-lookup"><span data-stu-id="c7687-216">Otherwise, the compiler assumes the `double` type.</span></span>

> [!NOTE]
> <span data-ttu-id="c7687-217">Harf, `M` `double` ve anahtar kelimeleri arasında en görsel olarak ayrı bir harf olarak seçilmiştir `decimal` .</span><span class="sxs-lookup"><span data-stu-id="c7687-217">The letter `M` was chosen as the most visually distinct letter between the `double` and `decimal` keywords.</span></span>

<span data-ttu-id="c7687-218">Ondalık türünün kullanıldığı matematikte, ondalık ayırıcının sağ tarafında daha fazla basamak bulunduğunu görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c7687-218">Notice that the math using the decimal type has more digits to the right of the decimal point.</span></span>

<span data-ttu-id="c7687-219">***Sınama***</span><span class="sxs-lookup"><span data-stu-id="c7687-219">***Challenge***</span></span>

<span data-ttu-id="c7687-220">Farklı sayısal türleri gördüğünüze göre yarı çapı 2,50 santimetre olan bir dairenin alanını hesaplayan kodu yazın.</span><span class="sxs-lookup"><span data-stu-id="c7687-220">Now that you've seen the different numeric types, write code that calculates the area of a circle whose radius is 2.50 centimeters.</span></span> <span data-ttu-id="c7687-221">Bir dairenin alanının, yarı çapın karesinin PI sayısı ile çarpımından elde edildiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="c7687-221">Remember that the area of a circle is the radius squared multiplied by PI.</span></span> <span data-ttu-id="c7687-222">İpucu: .NET, PI sayısı için kullanabileceğiniz <xref:System.Math.PI?displayProperty=nameWithType> sabit değerini içerir.</span><span class="sxs-lookup"><span data-stu-id="c7687-222">One hint: .NET contains a constant for PI, <xref:System.Math.PI?displayProperty=nameWithType> that you can use for that value.</span></span> <span data-ttu-id="c7687-223"><xref:System.Math.PI?displayProperty=nameWithType>, ad alanında belirtilen tüm sabitler gibi `System.Math` bir `double` değerdir.</span><span class="sxs-lookup"><span data-stu-id="c7687-223"><xref:System.Math.PI?displayProperty=nameWithType>, like all constants declared in the `System.Math` namespace, is a `double` value.</span></span> <span data-ttu-id="c7687-224">Bu nedenle, `double` `decimal` Bu zorluk için değer yerine kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="c7687-224">For that reason, you should use `double` instead of `decimal` values for this challenge.</span></span>

<span data-ttu-id="c7687-225">19 ile 20 arasında bir yanıt almanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="c7687-225">You should get an answer between 19 and 20.</span></span> <span data-ttu-id="c7687-226">[GitHub 'daki tamamlanmış örnek koda bakarak](https://github.com/dotnet/samples/tree/main/csharp/numbers-quickstart/Program.cs#L9-L11)yanıtınızı kontrol edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c7687-226">You can check your answer by [looking at the finished sample code on GitHub](https://github.com/dotnet/samples/tree/main/csharp/numbers-quickstart/Program.cs#L9-L11).</span></span>

<span data-ttu-id="c7687-227">Dilerseniz diğer formüllerden de deneme yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c7687-227">Try some other formulas if you'd like.</span></span>

<span data-ttu-id="c7687-228">"C# dilinde sayılar" hızlı başlangıç adımlarını tamamladınız.</span><span class="sxs-lookup"><span data-stu-id="c7687-228">You've completed the "Numbers in C#" quickstart.</span></span> <span data-ttu-id="c7687-229">Kendi geliştirme ortamınızda [dallar ve döngüler](branches-and-loops-local.md) hızlı başlangıç ile devam edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c7687-229">You can continue with the [Branches and loops](branches-and-loops-local.md) quickstart in your own development environment.</span></span>

<span data-ttu-id="c7687-230">Aşağıdaki makalelerde C# dilinde sayılar hakkında daha fazla bilgi edinebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="c7687-230">You can learn more about numbers in C# in the following articles:</span></span>

- [<span data-ttu-id="c7687-231">Tamsayı sayısal türler</span><span class="sxs-lookup"><span data-stu-id="c7687-231">Integral numeric types</span></span>](../../language-reference/builtin-types/integral-numeric-types.md)
- [<span data-ttu-id="c7687-232">Kayan nokta sayısal türleri</span><span class="sxs-lookup"><span data-stu-id="c7687-232">Floating-point numeric types</span></span>](../../language-reference/builtin-types/floating-point-numeric-types.md)
- [<span data-ttu-id="c7687-233">Yerleşik sayısal dönüşümler</span><span class="sxs-lookup"><span data-stu-id="c7687-233">Built-in numeric conversions</span></span>](../../language-reference/builtin-types/numeric-conversions.md)
