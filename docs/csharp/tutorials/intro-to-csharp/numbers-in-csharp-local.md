---
title: C# dilinde sayılar-C# öğreticisine giriş
description: Sayısal türleri, kullanımları, özellikleri ve yöntemleri inceleyerek C# hakkında bilgi edinin.
ms.date: 02/02/2021
ms.custom: mvc
ms.openlocfilehash: 253ecbc089722961013d058aff900bdde23fd366
ms.sourcegitcommit: 65af0f0ad316858882845391d60ef7e303b756e8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/05/2021
ms.locfileid: "99585643"
---
# <a name="manipulate-integral-and-floating-point-numbers-in-c"></a><span data-ttu-id="6627a-103">C 'de integral ve kayan nokta numaralarını işleme\#</span><span class="sxs-lookup"><span data-stu-id="6627a-103">Manipulate integral and floating point numbers in C\#</span></span>

<span data-ttu-id="6627a-104">Bu öğretici, C# ' deki sayısal türleri etkileşimli olarak size öğretir.</span><span class="sxs-lookup"><span data-stu-id="6627a-104">This tutorial teaches you about the numeric types in C# interactively.</span></span> <span data-ttu-id="6627a-105">Küçük miktarlarda kod yazacaksınız, daha sonra bu kodu derleyip çalıştıracaksınız.</span><span class="sxs-lookup"><span data-stu-id="6627a-105">You'll write small amounts of code, then you'll compile and run that code.</span></span> <span data-ttu-id="6627a-106">Öğretici, C# ' de sayıları ve matematik işlemlerini keşfetmenizi sağlayan bir dizi ders içerir.</span><span class="sxs-lookup"><span data-stu-id="6627a-106">The tutorial contains a series of lessons that explore numbers and math operations in C#.</span></span> <span data-ttu-id="6627a-107">Bu dersler size C# dilinin temel özelliklerini öğretir.</span><span class="sxs-lookup"><span data-stu-id="6627a-107">These lessons teach you the fundamentals of the C# language.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="6627a-108">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="6627a-108">Prerequisites</span></span>

<span data-ttu-id="6627a-109">Öğretici, yerel geliştirme için ayarlanmış bir makineniz olmasını bekler.</span><span class="sxs-lookup"><span data-stu-id="6627a-109">The tutorial expects that you have a machine set up for local development.</span></span> <span data-ttu-id="6627a-110">Windows, Linux veya macOS 'ta, uygulamaları oluşturmak, derlemek ve çalıştırmak için .NET CLı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6627a-110">On Windows, Linux, or macOS, you can use the .NET CLI to create, build, and run applications.</span></span> <span data-ttu-id="6627a-111">Windows 'ta, Visual Studio 2019 ' i kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6627a-111">On Windows, you can use Visual Studio 2019.</span></span> <span data-ttu-id="6627a-112">Kurulum yönergeleri için bkz. [Yerel ortamınızı ayarlama](local-environment.md).</span><span class="sxs-lookup"><span data-stu-id="6627a-112">For setup instructions, see [Set up your local environment](local-environment.md).</span></span>

## <a name="explore-integer-math"></a><span data-ttu-id="6627a-113">Tamsayı matematiğini inceleme</span><span class="sxs-lookup"><span data-stu-id="6627a-113">Explore integer math</span></span>

<span data-ttu-id="6627a-114">Sayı adlı bir dizin oluşturun *-hızlı başlangıç*.</span><span class="sxs-lookup"><span data-stu-id="6627a-114">Create a directory named *numbers-quickstart*.</span></span> <span data-ttu-id="6627a-115">Geçerli dizini yapın ve şu komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="6627a-115">Make that the current directory and run the following command:</span></span>

```dotnetcli
dotnet new console -n NumbersInCSharp -o .
```

<span data-ttu-id="6627a-116">En sevdiğiniz düzenleyicide *program.cs* açın ve satırı `Console.WriteLine("Hello World!");` aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="6627a-116">Open *Program.cs* in your favorite editor, and replace the line `Console.WriteLine("Hello World!");` with the following code:</span></span>

```csharp
int a = 18;
int b = 6;
int c = a + b;
Console.WriteLine(c);
```

<span data-ttu-id="6627a-117">Komut pencerenizi yazarak bu kodu çalıştırın `dotnet run` .</span><span class="sxs-lookup"><span data-stu-id="6627a-117">Run this code by typing `dotnet run` in your command window.</span></span>

<span data-ttu-id="6627a-118">Tamsayılarla temel matematik işlemlerinden birini gördünüz.</span><span class="sxs-lookup"><span data-stu-id="6627a-118">You've seen one of the fundamental math operations with integers.</span></span> <span data-ttu-id="6627a-119">`int`Tür bir **tamsayıyı**, sıfır, pozitif veya negatif bir tam sayıyı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="6627a-119">The `int` type represents an **integer**, a zero, positive, or negative whole number.</span></span> <span data-ttu-id="6627a-120">Toplama için `+` sembolünü kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="6627a-120">You use the `+` symbol for addition.</span></span> <span data-ttu-id="6627a-121">Tamsayılar için sıklıkla kullanılan diğer matematiksel işlemler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="6627a-121">Other common mathematical operations for integers include:</span></span>

- <span data-ttu-id="6627a-122">çıkarma için `-`</span><span class="sxs-lookup"><span data-stu-id="6627a-122">`-` for subtraction</span></span>
- <span data-ttu-id="6627a-123">çarpma için `*`</span><span class="sxs-lookup"><span data-stu-id="6627a-123">`*` for multiplication</span></span>
- <span data-ttu-id="6627a-124">bölme için `/`</span><span class="sxs-lookup"><span data-stu-id="6627a-124">`/` for division</span></span>

<span data-ttu-id="6627a-125">Bu farklı işlemleri keşfederek başlayın.</span><span class="sxs-lookup"><span data-stu-id="6627a-125">Start by exploring those different operations.</span></span> <span data-ttu-id="6627a-126">Değerini yazan satırdan sonra bu satırları ekleyin `c` :</span><span class="sxs-lookup"><span data-stu-id="6627a-126">Add these lines after the line that writes the value of `c`:</span></span>

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

<span data-ttu-id="6627a-127">Komut pencerenizi yazarak bu kodu çalıştırın `dotnet run` .</span><span class="sxs-lookup"><span data-stu-id="6627a-127">Run this code by typing `dotnet run` in your command window.</span></span>

<span data-ttu-id="6627a-128">Ayrıca, isterseniz aynı satırda birden çok matematik işlemi yazarak da deneyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6627a-128">You can also experiment by writing multiple mathematics operations in the same line, if you'd like.</span></span> <span data-ttu-id="6627a-129">Örneğin, deneyin `c = a + b - 12 * 17;` .</span><span class="sxs-lookup"><span data-stu-id="6627a-129">Try `c = a + b - 12 * 17;` for example.</span></span> <span data-ttu-id="6627a-130">Değişkenlerin ve sabit sayıların karıştırılmasına izin verilir.</span><span class="sxs-lookup"><span data-stu-id="6627a-130">Mixing variables and constant numbers is allowed.</span></span>

> [!TIP]
> <span data-ttu-id="6627a-131">C# dilini (veya herhangi bir programlama dilini) keşfederken, kod yazdığınızda hatalar yapacaksınız.</span><span class="sxs-lookup"><span data-stu-id="6627a-131">As you explore C# (or any programming language), you'll make mistakes when you write code.</span></span> <span data-ttu-id="6627a-132">**Derleyici** bu hataları bulup size bildirir.</span><span class="sxs-lookup"><span data-stu-id="6627a-132">The **compiler** will find those errors and report them to you.</span></span> <span data-ttu-id="6627a-133">Çıktı hata iletileri içerdiğinde, nelerin düzeltileceğini görmek için örnek koda ve penceredeki koda yakından bakın.</span><span class="sxs-lookup"><span data-stu-id="6627a-133">When the output contains error messages, look closely at the example code and the code in your window to see what to fix.</span></span>
> <span data-ttu-id="6627a-134">Bu alıştırma, C# kodunun yapısını öğrenmenize yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="6627a-134">That exercise will help you learn the structure of C# code.</span></span>

<span data-ttu-id="6627a-135">İlk adımı tamamladınız.</span><span class="sxs-lookup"><span data-stu-id="6627a-135">You've finished the first step.</span></span> <span data-ttu-id="6627a-136">Sonraki bölüme başlamadan önce geçerli kodu ayrı bir yönteme taşıyalim.</span><span class="sxs-lookup"><span data-stu-id="6627a-136">Before you start the next section, let's move the current code into a separate method.</span></span> <span data-ttu-id="6627a-137">Bu, yeni bir örnekle çalışmaya başlamasını kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="6627a-137">That makes it easier to start working with a new example.</span></span> <span data-ttu-id="6627a-138">`Main`Yönteminizi olarak yeniden adlandırın `WorkingWithIntegers` ve çağıran yeni bir `Main` Yöntem yazın `WorkingWithIntegers` .</span><span class="sxs-lookup"><span data-stu-id="6627a-138">Rename your `Main` method to `WorkingWithIntegers` and write a new `Main` method that calls `WorkingWithIntegers`.</span></span> <span data-ttu-id="6627a-139">Bitirdiğinizde, kodunuzun şöyle görünmesi gerekir:</span><span class="sxs-lookup"><span data-stu-id="6627a-139">When you finish, your code should look like this:</span></span>

```csharp
using System;

namespace NumbersInCSharp
{
    class Program
    {
        static void WorkingWithIntegers()
        {
            int a = 18;
            int b = 6;

            // addition
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

        static void Main(string[] args)
        {
            WorkingWithIntegers();
        }
    }
}
```

## <a name="explore-order-of-operations"></a><span data-ttu-id="6627a-140">İşlem sırasını inceleme</span><span class="sxs-lookup"><span data-stu-id="6627a-140">Explore order of operations</span></span>

<span data-ttu-id="6627a-141">Çağrısını not edin `WorkingWithIntegers()` .</span><span class="sxs-lookup"><span data-stu-id="6627a-141">Comment out the call to `WorkingWithIntegers()`.</span></span> <span data-ttu-id="6627a-142">Bu bölümde çalışırken çıktının daha az karışık hale gelir:</span><span class="sxs-lookup"><span data-stu-id="6627a-142">It will make the output less cluttered as you work in this section:</span></span>

```csharp
//WorkingWithIntegers();
```

<span data-ttu-id="6627a-143">`//`C# dilinde bir **Açıklama** başlatır.</span><span class="sxs-lookup"><span data-stu-id="6627a-143">The `//` starts a **comment** in C#.</span></span> <span data-ttu-id="6627a-144">Açıklamalar, kaynak kodunuzda tutmak istediğiniz tüm metinlerdir, ancak kod olarak yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="6627a-144">Comments are any text you want to keep in your source code but not execute as code.</span></span> <span data-ttu-id="6627a-145">Derleyici açıklamalardan herhangi bir yürütülebilir kod oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="6627a-145">The compiler doesn't generate any executable code from comments.</span></span>

<span data-ttu-id="6627a-146">C# dili, farklı matematik işlemlerinin önceliğini matematikte öğrendiğiniz kurallarla tutarlı bir şekilde tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6627a-146">The C# language defines the precedence of different mathematics operations with rules consistent with the rules you learned in mathematics.</span></span>
<span data-ttu-id="6627a-147">Çarpma ve bölme işlemleri, toplama ve çıkarma işlemlerinden önce gelir.</span><span class="sxs-lookup"><span data-stu-id="6627a-147">Multiplication and division take precedence over addition and subtraction.</span></span>
<span data-ttu-id="6627a-148">Yöntemine aşağıdaki kodu ekleyerek `Main` ve yürüterek şunu araştırın `dotnet run` :</span><span class="sxs-lookup"><span data-stu-id="6627a-148">Explore that by adding the following code to your `Main` method, and executing `dotnet run`:</span></span>

```csharp
int a = 5;
int b = 4;
int c = 2;
int d = a + b * c;
Console.WriteLine(d);
 ```

<span data-ttu-id="6627a-149">Çıkış, çarpma işleminin toplama işleminden önce gerçekleştiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="6627a-149">The output demonstrates that the multiplication is performed before the addition.</span></span>

<span data-ttu-id="6627a-150">Önce gerçekleştirilmesini istediğiniz işlemin veya işlemlerin çevresine parantez ekleyerek farklı bir işlem sırası zorlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6627a-150">You can force a different order of operation by adding parentheses around the operation or operations you want performed first.</span></span> <span data-ttu-id="6627a-151">Aşağıdaki satırları ekleyin ve yeniden çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="6627a-151">Add the following lines and run again:</span></span>

```csharp
d = (a + b) * c;
Console.WriteLine(d);
```

<span data-ttu-id="6627a-152">Birçok farklı işlemi birleştirerek daha fazlasını keşfedin.</span><span class="sxs-lookup"><span data-stu-id="6627a-152">Explore more by combining many different operations.</span></span> <span data-ttu-id="6627a-153">Yönteminizin en altında aşağıdaki satırlara benzer bir şey ekleyin `Main` .</span><span class="sxs-lookup"><span data-stu-id="6627a-153">Add something like the following lines at the bottom of your `Main` method.</span></span> <span data-ttu-id="6627a-154">`dotnet run` komutunu yeniden deneyin.</span><span class="sxs-lookup"><span data-stu-id="6627a-154">Try `dotnet run` again.</span></span>

```csharp
d = (a + b) - 6 * c + (12 * 4) / 3 + 12;
Console.WriteLine(d);
```

<span data-ttu-id="6627a-155">Tamsayılar için farklı bir davranışla karşılaşmış olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6627a-155">You may have noticed an interesting behavior for integers.</span></span> <span data-ttu-id="6627a-156">Sonucun ondalık veya kesir bölümü içermesini bekliyor olsanız da tamsayı bölme işlemi her zaman tamsayı sonucu verir.</span><span class="sxs-lookup"><span data-stu-id="6627a-156">Integer division always produces an integer result, even when you'd expect the result to include a decimal or fractional portion.</span></span>

<span data-ttu-id="6627a-157">Bu davranışı görmediyseniz, yönteminizin sonunda aşağıdaki kodu deneyin `Main` :</span><span class="sxs-lookup"><span data-stu-id="6627a-157">If you haven't seen this behavior, try the following code at the end of your `Main` method:</span></span>

```csharp
int e = 7;
int f = 4;
int g = 3;
int h = (e + f) / g;
Console.WriteLine(h);
```

<span data-ttu-id="6627a-158">`dotnet run`Sonuçları görmek için yeniden yazın.</span><span class="sxs-lookup"><span data-stu-id="6627a-158">Type `dotnet run` again to see the results.</span></span>

<span data-ttu-id="6627a-159">' In üzerine geçmeden önce, bu bölümde yazdığınız tüm kodu alıp yeni bir yönteme koyabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6627a-159">Before moving on, let's take all the code you've written in this section and put it in a new method.</span></span> <span data-ttu-id="6627a-160">Bu yeni yöntemi çağırın `OrderPrecedence` .</span><span class="sxs-lookup"><span data-stu-id="6627a-160">Call that new method `OrderPrecedence`.</span></span>
<span data-ttu-id="6627a-161">Şöyle bir değer yazmalısınız:</span><span class="sxs-lookup"><span data-stu-id="6627a-161">You should write something like this:</span></span>

```csharp
using System;

namespace NumbersInCSharp
{
    class Program
    {
        static void WorkingWithIntegers()
        {
            int a = 18;
            int b = 6;

            // addition
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

        static void OrderPrecedence()
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
            int h = (e  + f) / g;
            Console.WriteLine(h);
        }

        static void Main(string[] args)
        {
            WorkingWithIntegers();

            OrderPrecedence();

        }
    }
}
```

## <a name="explore-integer-precision-and-limits"></a><span data-ttu-id="6627a-162">Tamsayı duyarlığını ve sınırlarını inceleme</span><span class="sxs-lookup"><span data-stu-id="6627a-162">Explore integer precision and limits</span></span>

<span data-ttu-id="6627a-163">Son örnek, tamsayı bölme işleminin sonucu kestiğini size göstermiştir.</span><span class="sxs-lookup"><span data-stu-id="6627a-163">That last sample showed you that integer division truncates the result.</span></span>
<span data-ttu-id="6627a-164">**Geri kalanını** , **mod** işleci, karakterini kullanarak edinebilirsiniz `%` .</span><span class="sxs-lookup"><span data-stu-id="6627a-164">You can get the **remainder** by using the **modulo** operator, the `%` character.</span></span> <span data-ttu-id="6627a-165">Yönteyinizdeki aşağıdaki kodu deneyin `Main` :</span><span class="sxs-lookup"><span data-stu-id="6627a-165">Try the following code in your `Main` method:</span></span>

```csharp
int a = 7;
int b = 4;
int c = 3;
int d = (a + b) / c;
int e = (a + b) % c;
Console.WriteLine($"quotient: {d}");
Console.WriteLine($"remainder: {e}");
```

<span data-ttu-id="6627a-166">C# tamsayı türü diğer bir özelliğiyle matematiksel tamsayılardan farklıdır: `int` türünün alt ve üst sınırları vardır.</span><span class="sxs-lookup"><span data-stu-id="6627a-166">The C# integer type differs from mathematical integers in one other way: the `int` type has minimum and maximum limits.</span></span> <span data-ttu-id="6627a-167">Bu `Main` sınırları görmek için bu kodu yönteminizin içine ekleyin:</span><span class="sxs-lookup"><span data-stu-id="6627a-167">Add this code to your `Main` method to see those limits:</span></span>

```csharp
int max = int.MaxValue;
int min = int.MinValue;
Console.WriteLine($"The range of integers is {min} to {max}");
```

<span data-ttu-id="6627a-168">Bir hesaplama, bu sınırları aşan bir değer veriyorsa bu, **aşağı taşma** veya **taşma** koşulunuzun olduğu anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="6627a-168">If a calculation produces a value that exceeds those limits, you have an **underflow** or **overflow** condition.</span></span> <span data-ttu-id="6627a-169">Yanıtın bir sınırdan diğerine kaydığı görülüyor.</span><span class="sxs-lookup"><span data-stu-id="6627a-169">The answer appears to wrap from one limit to the other.</span></span> <span data-ttu-id="6627a-170">`Main`Bir örnek görmek için bu iki satırı yönteminizin içine ekleyin:</span><span class="sxs-lookup"><span data-stu-id="6627a-170">Add these two lines to your `Main` method to see an example:</span></span>

```csharp
int what = max + 3;
Console.WriteLine($"An example of overflow: {what}");
```

<span data-ttu-id="6627a-171">Yanıtın tam sayı alt sınırına (negatif) oldukça yakın olduğuna dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="6627a-171">Notice that the answer is very close to the minimum (negative) integer.</span></span> <span data-ttu-id="6627a-172">Bu, `min + 2` ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="6627a-172">It's the same as `min + 2`.</span></span>
<span data-ttu-id="6627a-173">Toplama işlemi, tamsayılar için izin verilen değerleri **aşmıştır**.</span><span class="sxs-lookup"><span data-stu-id="6627a-173">The addition operation **overflowed** the allowed values for integers.</span></span>
<span data-ttu-id="6627a-174">Taşma durumu en büyük olası tamsayı değerinden en küçük olana "kaydığından" yanıt oldukça büyük bir negatif sayıdır.</span><span class="sxs-lookup"><span data-stu-id="6627a-174">The answer is a very large negative number because an overflow "wraps around" from the largest possible integer value to the smallest.</span></span>

<span data-ttu-id="6627a-175">`int` türü, gereksinimlerinizi karşılamadığında kullanabileceğiniz farklı sınırlar ve duyarlık içeren başka sayısal türler de mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="6627a-175">There are other numeric types with different limits and precision that you would use when the `int` type doesn't meet your needs.</span></span> <span data-ttu-id="6627a-176">Daha sonra bu diğer türleri keşfedelim.</span><span class="sxs-lookup"><span data-stu-id="6627a-176">Let's explore those other types next.</span></span>

<span data-ttu-id="6627a-177">Bir kez daha, bu bölümde yazdığınız kodu ayrı bir yönteme taşıyalim.</span><span class="sxs-lookup"><span data-stu-id="6627a-177">Once again, let's move the code you wrote in this section into a separate method.</span></span> <span data-ttu-id="6627a-178">Bunu, `TestLimits` olarak adlandırın.</span><span class="sxs-lookup"><span data-stu-id="6627a-178">Name it `TestLimits`.</span></span>

## <a name="work-with-the-double-type"></a><span data-ttu-id="6627a-179">Çift tür ile çalışma</span><span class="sxs-lookup"><span data-stu-id="6627a-179">Work with the double type</span></span>

<span data-ttu-id="6627a-180">`double` sayısal türü, çift duyarlıklı kayan noktalı bir sayıyı ifade eder.</span><span class="sxs-lookup"><span data-stu-id="6627a-180">The `double` numeric type represents a double-precision floating point number.</span></span> <span data-ttu-id="6627a-181">Bu terimler sizin için yeni olabilir.</span><span class="sxs-lookup"><span data-stu-id="6627a-181">Those terms may be new to you.</span></span> <span data-ttu-id="6627a-182">**Kayan noktalı** sayı, büyüklük açısından oldukça büyük veya küçük olabilen, tamsayı olmayan değerleri ifade etmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6627a-182">A **floating point** number is useful to represent non-integral numbers that may be very large or small in magnitude.</span></span> <span data-ttu-id="6627a-183">**Çift duyarlık** , değeri depolamak için kullanılan ikili basamak sayısını açıklayan göreli bir terimdir.</span><span class="sxs-lookup"><span data-stu-id="6627a-183">**Double-precision** is a relative term that describes the number of binary digits used to store the value.</span></span> <span data-ttu-id="6627a-184">**Çift duyarlık** sayıları, ikili basamakların sayısının **tek duyarlıklı** olarak iki katına sahiptir.</span><span class="sxs-lookup"><span data-stu-id="6627a-184">**Double precision** numbers have twice the number of binary digits as **single-precision**.</span></span> <span data-ttu-id="6627a-185">Modern bilgisayarlarda, tek duyarlık sayılarıyla çift duyarlık kullanmak daha yaygındır.</span><span class="sxs-lookup"><span data-stu-id="6627a-185">On modern computers, it's more common to use double precision than single precision numbers.</span></span> <span data-ttu-id="6627a-186">**Tek duyarlık** numaraları anahtar sözcüğü kullanılarak belirtilir `float` .</span><span class="sxs-lookup"><span data-stu-id="6627a-186">**Single precision** numbers are declared using the `float` keyword.</span></span>
<span data-ttu-id="6627a-187">İnceleyelim mi?</span><span class="sxs-lookup"><span data-stu-id="6627a-187">Let's explore.</span></span> <span data-ttu-id="6627a-188">Aşağıdaki kodu ekleyin ve sonucu görüntüleyin:</span><span class="sxs-lookup"><span data-stu-id="6627a-188">Add the following code and see the result:</span></span>

```csharp
double a = 5;
double b = 4;
double c = 2;
double d = (a + b) / c;
Console.WriteLine(d);
```

<span data-ttu-id="6627a-189">Yanıtın, bölümün ondalık kısmını içerdiğine dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="6627a-189">Notice that the answer includes the decimal portion of the quotient.</span></span> <span data-ttu-id="6627a-190">Çift değerlerle biraz daha karmaşık bir ifadeyi deneyin:</span><span class="sxs-lookup"><span data-stu-id="6627a-190">Try a slightly more complicated expression with doubles:</span></span>

```csharp
double e = 19;
double f = 23;
double g = 8;
double h = (e + f) / g;
Console.WriteLine(h);
```

<span data-ttu-id="6627a-191">Çift değerin aralığı, tamsayı değerlerinden çok daha büyüktür.</span><span class="sxs-lookup"><span data-stu-id="6627a-191">The range of a double value is much greater than integer values.</span></span> <span data-ttu-id="6627a-192">Şu ana kadar yazdıklarınız için aşağıdaki kodu deneyin:</span><span class="sxs-lookup"><span data-stu-id="6627a-192">Try the following code below what you've written so far:</span></span>

```csharp
double max = double.MaxValue;
double min = double.MinValue;
Console.WriteLine($"The range of double is {min} to {max}");
```

<span data-ttu-id="6627a-193">Bu değerler bilimsel gösterimde yazdırılır.</span><span class="sxs-lookup"><span data-stu-id="6627a-193">These values are printed out in scientific notation.</span></span> <span data-ttu-id="6627a-194">`E` değerinin sol tarafındaki sayı katsayıdır.</span><span class="sxs-lookup"><span data-stu-id="6627a-194">The number to the left of the `E` is the significand.</span></span> <span data-ttu-id="6627a-195">Sağ taraftaki sayı 10’un bir kuvveti olarak üstür.</span><span class="sxs-lookup"><span data-stu-id="6627a-195">The number to the right is the exponent, as a power of 10.</span></span>

<span data-ttu-id="6627a-196">Matematikteki ondalık sayılar gibi C# dilindeki çift değerlerde de yuvarlama hataları olabilir.</span><span class="sxs-lookup"><span data-stu-id="6627a-196">Just like decimal numbers in math, doubles in C# can have rounding errors.</span></span> <span data-ttu-id="6627a-197">Şu kodu deneyin:</span><span class="sxs-lookup"><span data-stu-id="6627a-197">Try this code:</span></span>

```csharp
double third = 1.0 / 3.0;
Console.WriteLine(third);
```

<span data-ttu-id="6627a-198">`0.3`Yinelenen tam olarak aynı olmadığını bilirsiniz `1/3` .</span><span class="sxs-lookup"><span data-stu-id="6627a-198">You know that `0.3` repeating isn't exactly the same as `1/3`.</span></span>

<span data-ttu-id="6627a-199">***Sınama***</span><span class="sxs-lookup"><span data-stu-id="6627a-199">***Challenge***</span></span>

<span data-ttu-id="6627a-200">Türü kullanarak büyük sayılar, küçük sayılar, çarpma ve bölme ile diğer hesaplamaları deneyin `double` .</span><span class="sxs-lookup"><span data-stu-id="6627a-200">Try other calculations with large numbers, small numbers, multiplication, and division using the `double` type.</span></span> <span data-ttu-id="6627a-201">Daha karmaşık hesaplamalar deneyin.</span><span class="sxs-lookup"><span data-stu-id="6627a-201">Try more complicated calculations.</span></span>

<span data-ttu-id="6627a-202">Zorluğa bir süre harcadıktan sonra yazdığınız kodu alın ve yeni bir yönteme yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="6627a-202">After you've spent some time with the challenge, take the code you've written and place it in a new method.</span></span> <span data-ttu-id="6627a-203">Yeni yönteme adlandırın `WorkWithDoubles` .</span><span class="sxs-lookup"><span data-stu-id="6627a-203">Name that new method `WorkWithDoubles`.</span></span>

## <a name="work-with-decimal-types"></a><span data-ttu-id="6627a-204">Ondalık türlerle çalışma</span><span class="sxs-lookup"><span data-stu-id="6627a-204">Work with decimal types</span></span>

<span data-ttu-id="6627a-205">C# dilinde temel sayısal türleri gördünüz: tamsayılar ve çiftler.</span><span class="sxs-lookup"><span data-stu-id="6627a-205">You've seen the basic numeric types in C#: integers and doubles.</span></span>  <span data-ttu-id="6627a-206">Öğreneceğinizi öğrenmek için başka bir tür vardır: `decimal` türü.</span><span class="sxs-lookup"><span data-stu-id="6627a-206">There's one other type to learn: the `decimal` type.</span></span> <span data-ttu-id="6627a-207">`decimal` türü, `double` türünden daha küçük bir aralığa ancak daha fazla duyarlığa sahiptir.</span><span class="sxs-lookup"><span data-stu-id="6627a-207">The `decimal` type has a smaller range but greater precision than `double`.</span></span> <span data-ttu-id="6627a-208">Şimdi buna bir göz atalım:</span><span class="sxs-lookup"><span data-stu-id="6627a-208">Let's take a look:</span></span>

```csharp
decimal min = decimal.MinValue;
decimal max = decimal.MaxValue;
Console.WriteLine($"The range of the decimal type is {min} to {max}");
```

<span data-ttu-id="6627a-209">Aralığın `double` türünden daha küçük olduğuna dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="6627a-209">Notice that the range is smaller than the `double` type.</span></span> <span data-ttu-id="6627a-210">Aşağıdaki kodu deneyerek ondalık türünde daha fazla duyarlık olduğunu görebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="6627a-210">You can see the greater precision with the decimal type by trying the following code:</span></span>

```csharp
double a = 1.0;
double b = 3.0;
Console.WriteLine(a / b);

decimal c = 1.0M;
decimal d = 3.0M;
Console.WriteLine(c / d);
```

<span data-ttu-id="6627a-211">Sayılardaki `M` sonekiyle, bir sabit sayının `decimal` türünü nasıl kullanması gerektiğini belirtirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6627a-211">The `M` suffix on the numbers is how you indicate that a constant should use the `decimal` type.</span></span> <span data-ttu-id="6627a-212">Aksi takdirde, derleyici türü varsayar `double` .</span><span class="sxs-lookup"><span data-stu-id="6627a-212">Otherwise, the compiler assumes the `double` type.</span></span>

> [!NOTE]
> <span data-ttu-id="6627a-213">Harf, `M` `double` ve anahtar kelimeleri arasında en görsel olarak ayrı bir harf olarak seçilmiştir `decimal` .</span><span class="sxs-lookup"><span data-stu-id="6627a-213">The letter `M` was chosen as the most visually distinct letter between the `double` and `decimal` keywords.</span></span>

<span data-ttu-id="6627a-214">Ondalık türünün kullanıldığı matematikte, ondalık ayırıcının sağ tarafında daha fazla basamak bulunduğunu görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6627a-214">Notice that the math using the decimal type has more digits to the right of the decimal point.</span></span>

<span data-ttu-id="6627a-215">***Sınama***</span><span class="sxs-lookup"><span data-stu-id="6627a-215">***Challenge***</span></span>

<span data-ttu-id="6627a-216">Farklı sayısal türleri gördüğünüze göre yarı çapı 2,50 santimetre olan bir dairenin alanını hesaplayan kodu yazın.</span><span class="sxs-lookup"><span data-stu-id="6627a-216">Now that you've seen the different numeric types, write code that calculates the area of a circle whose radius is 2.50 centimeters.</span></span> <span data-ttu-id="6627a-217">Bir dairenin alanının, yarı çapın karesinin PI sayısı ile çarpımından elde edildiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="6627a-217">Remember that the area of a circle is the radius squared multiplied by PI.</span></span> <span data-ttu-id="6627a-218">İpucu: .NET, PI sayısı için kullanabileceğiniz <xref:System.Math.PI?displayProperty=nameWithType> sabit değerini içerir.</span><span class="sxs-lookup"><span data-stu-id="6627a-218">One hint: .NET contains a constant for PI, <xref:System.Math.PI?displayProperty=nameWithType> that you can use for that value.</span></span> <span data-ttu-id="6627a-219"><xref:System.Math.PI?displayProperty=nameWithType>, ad alanında belirtilen tüm sabitler gibi `System.Math` bir `double` değerdir.</span><span class="sxs-lookup"><span data-stu-id="6627a-219"><xref:System.Math.PI?displayProperty=nameWithType>, like all constants declared in the `System.Math` namespace, is a `double` value.</span></span> <span data-ttu-id="6627a-220">Bu nedenle, `double` `decimal` Bu zorluk için değer yerine kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="6627a-220">For that reason, you should use `double` instead of `decimal` values for this challenge.</span></span>

<span data-ttu-id="6627a-221">19 ile 20 arasında bir yanıt almanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="6627a-221">You should get an answer between 19 and 20.</span></span>
<span data-ttu-id="6627a-222">[GitHub 'daki tamamlanmış örnek koda bakarak](https://github.com/dotnet/samples/tree/master/csharp/numbers-quickstart/Program.cs#L104-L106)yanıtınızı kontrol edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6627a-222">You can check your answer by [looking at the finished sample code on GitHub](https://github.com/dotnet/samples/tree/master/csharp/numbers-quickstart/Program.cs#L104-L106).</span></span>

<span data-ttu-id="6627a-223">Dilerseniz diğer formüllerden de deneme yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6627a-223">Try some other formulas if you'd like.</span></span>

<span data-ttu-id="6627a-224">"C# dilinde sayılar" hızlı başlangıç adımlarını tamamladınız.</span><span class="sxs-lookup"><span data-stu-id="6627a-224">You've completed the "Numbers in C#" quickstart.</span></span> <span data-ttu-id="6627a-225">Kendi geliştirme ortamınızda [dallar ve döngüler](branches-and-loops-local.md) hızlı başlangıç ile devam edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6627a-225">You can continue with the [Branches and loops](branches-and-loops-local.md) quickstart in your own development environment.</span></span>

<span data-ttu-id="6627a-226">Aşağıdaki makalelerde C# dilinde sayılar hakkında daha fazla bilgi edinebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="6627a-226">You can learn more about numbers in C# in the following articles:</span></span>

- [<span data-ttu-id="6627a-227">Tamsayı sayısal türler</span><span class="sxs-lookup"><span data-stu-id="6627a-227">Integral numeric types</span></span>](../../language-reference/builtin-types/integral-numeric-types.md)
- [<span data-ttu-id="6627a-228">Kayan nokta sayısal türleri</span><span class="sxs-lookup"><span data-stu-id="6627a-228">Floating-point numeric types</span></span>](../../language-reference/builtin-types/floating-point-numeric-types.md)
- [<span data-ttu-id="6627a-229">Yerleşik sayısal dönüşümler</span><span class="sxs-lookup"><span data-stu-id="6627a-229">Built-in numeric conversions</span></span>](../../language-reference/builtin-types/numeric-conversions.md)
