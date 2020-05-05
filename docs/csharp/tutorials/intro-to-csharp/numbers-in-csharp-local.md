---
title: C# dilinde sayılar-C# öğreticisine giriş
description: Sayısal türleri, kullanımları, özellikleri ve yöntemleri inceleyerek C# hakkında bilgi edinin.
ms.date: 10/31/2017
ms.custom: mvc
ms.openlocfilehash: 3dc2a5afc6321da45351525a632f586cb84bf7fe
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82794620"
---
# <a name="manipulate-integral-and-floating-point-numbers-in-c"></a><span data-ttu-id="87377-103">C 'de integral ve kayan nokta numaralarını işleme\#</span><span class="sxs-lookup"><span data-stu-id="87377-103">Manipulate integral and floating point numbers in C\#</span></span>

<span data-ttu-id="87377-104">Bu öğretici, C# ' deki sayısal türleri etkileşimli olarak size öğretir.</span><span class="sxs-lookup"><span data-stu-id="87377-104">This tutorial teaches you about the numeric types in C# interactively.</span></span> <span data-ttu-id="87377-105">Küçük miktarlarda kod yazacaksınız, daha sonra bu kodu derleyip çalıştıracaksınız.</span><span class="sxs-lookup"><span data-stu-id="87377-105">You'll write small amounts of code, then you'll compile and run that code.</span></span> <span data-ttu-id="87377-106">Öğretici, C# ' de sayıları ve matematik işlemlerini keşfetmenizi sağlayan bir dizi ders içerir.</span><span class="sxs-lookup"><span data-stu-id="87377-106">The tutorial contains a series of lessons that explore numbers and math operations in C#.</span></span> <span data-ttu-id="87377-107">Bu dersler size C# dilinin temel özelliklerini öğretir.</span><span class="sxs-lookup"><span data-stu-id="87377-107">These lessons teach you the fundamentals of the C# language.</span></span>

<span data-ttu-id="87377-108">Bu öğreticide, geliştirme için kullanabileceğiniz bir makineniz olması beklenir.</span><span class="sxs-lookup"><span data-stu-id="87377-108">This tutorial expects you to have a machine you can use for development.</span></span> <span data-ttu-id="87377-109">[10 dakika içinde Merhaba Dünya](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) .NET öğreticisi, Windows, Linux veya MacOS 'ta yerel geliştirme ortamınızı ayarlamaya yönelik yönergeler içerir.</span><span class="sxs-lookup"><span data-stu-id="87377-109">The .NET tutorial [Hello World in 10 minutes](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) has instructions for setting up your local development environment on Windows, Linux, or macOS.</span></span> <span data-ttu-id="87377-110">Kullanacağınız komutlara hızlı bir genel bakış, daha fazla ayrıntı için bağlantılarla birlikte [geliştirme araçları hakkında bilgi sahibi olmaya gelmiştir](local-environment.md) .</span><span class="sxs-lookup"><span data-stu-id="87377-110">A quick overview of the commands you'll use is in the [Become familiar with the development tools](local-environment.md) with links to more details.</span></span>

## <a name="explore-integer-math"></a><span data-ttu-id="87377-111">Tamsayı matematiğini inceleme</span><span class="sxs-lookup"><span data-stu-id="87377-111">Explore integer math</span></span>

<span data-ttu-id="87377-112">Sayı adlı bir dizin oluşturun *-hızlı başlangıç*.</span><span class="sxs-lookup"><span data-stu-id="87377-112">Create a directory named *numbers-quickstart*.</span></span> <span data-ttu-id="87377-113">Geçerli dizini yapın ve şu komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="87377-113">Make that the current directory and run the following command:</span></span>

```dotnetcli
dotnet new console -n NumbersInCSharp -o .
```

<span data-ttu-id="87377-114">En sevdiğiniz düzenleyicide *program.cs* açın ve satırı `Console.WriteLine("Hello World!");` aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="87377-114">Open *Program.cs* in your favorite editor, and replace the line `Console.WriteLine("Hello World!");` with the following code:</span></span>

```csharp
int a = 18;
int b = 6;
int c = a + b;
Console.WriteLine(c);
```

<span data-ttu-id="87377-115">Komut pencerenizi yazarak `dotnet run` bu kodu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="87377-115">Run this code by typing `dotnet run` in your command window.</span></span>

<span data-ttu-id="87377-116">Tamsayılarla temel matematik işlemlerinden birini gördünüz.</span><span class="sxs-lookup"><span data-stu-id="87377-116">You've seen one of the fundamental math operations with integers.</span></span> <span data-ttu-id="87377-117">`int` Tür bir **tamsayıyı**, sıfır, pozitif veya negatif bir tam sayıyı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="87377-117">The `int` type represents an **integer**, a zero, positive, or negative whole number.</span></span> <span data-ttu-id="87377-118">Toplama için `+` sembolünü kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="87377-118">You use the `+` symbol for addition.</span></span> <span data-ttu-id="87377-119">Tamsayılar için sıklıkla kullanılan diğer matematiksel işlemler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="87377-119">Other common mathematical operations for integers include:</span></span>

- <span data-ttu-id="87377-120">çıkarma için `-`</span><span class="sxs-lookup"><span data-stu-id="87377-120">`-` for subtraction</span></span>
- <span data-ttu-id="87377-121">çarpma için `*`</span><span class="sxs-lookup"><span data-stu-id="87377-121">`*` for multiplication</span></span>
- <span data-ttu-id="87377-122">bölme için `/`</span><span class="sxs-lookup"><span data-stu-id="87377-122">`/` for division</span></span>

<span data-ttu-id="87377-123">Bu farklı işlemleri keşfederek başlayın.</span><span class="sxs-lookup"><span data-stu-id="87377-123">Start by exploring those different operations.</span></span> <span data-ttu-id="87377-124">Değerini yazan satırdan sonra bu satırları ekleyin `c`:</span><span class="sxs-lookup"><span data-stu-id="87377-124">Add these lines after the line that writes the value of `c`:</span></span>

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

<span data-ttu-id="87377-125">Komut pencerenizi yazarak `dotnet run` bu kodu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="87377-125">Run this code by typing `dotnet run` in your command window.</span></span>

<span data-ttu-id="87377-126">Ayrıca, isterseniz aynı satırda birden çok matematik işlemi yazarak da deneyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="87377-126">You can also experiment by writing multiple mathematics operations in the same line, if you'd like.</span></span> <span data-ttu-id="87377-127">Örneğin `c = a + b - 12 * 17;` , deneyin.</span><span class="sxs-lookup"><span data-stu-id="87377-127">Try `c = a + b - 12 * 17;` for example.</span></span> <span data-ttu-id="87377-128">Değişkenlerin ve sabit sayıların karıştırılmasına izin verilir.</span><span class="sxs-lookup"><span data-stu-id="87377-128">Mixing variables and constant numbers is allowed.</span></span>

> [!TIP]
> <span data-ttu-id="87377-129">C# dilini (veya herhangi bir programlama dilini) keşfederken, kod yazdığınızda hatalar yapacaksınız.</span><span class="sxs-lookup"><span data-stu-id="87377-129">As you explore C# (or any programming language), you'll make mistakes when you write code.</span></span> <span data-ttu-id="87377-130">**Derleyici** bu hataları bulup size bildirir.</span><span class="sxs-lookup"><span data-stu-id="87377-130">The **compiler** will find those errors and report them to you.</span></span> <span data-ttu-id="87377-131">Çıktı hata iletileri içerdiğinde, nelerin düzeltileceğini görmek için örnek koda ve penceredeki koda yakından bakın.</span><span class="sxs-lookup"><span data-stu-id="87377-131">When the output contains error messages, look closely at the example code and the code in your window to see what to fix.</span></span>
> <span data-ttu-id="87377-132">Bu alıştırma, C# kodunun yapısını öğrenmenize yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="87377-132">That exercise will help you learn the structure of C# code.</span></span>

<span data-ttu-id="87377-133">İlk adımı tamamladınız.</span><span class="sxs-lookup"><span data-stu-id="87377-133">You've finished the first step.</span></span> <span data-ttu-id="87377-134">Sonraki bölüme başlamadan önce geçerli kodu ayrı bir yönteme taşıyalim.</span><span class="sxs-lookup"><span data-stu-id="87377-134">Before you start the next section, let's move the current code into a separate method.</span></span> <span data-ttu-id="87377-135">Bu, yeni bir örnekle çalışmaya başlamasını kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="87377-135">That makes it easier to start working with a new example.</span></span> <span data-ttu-id="87377-136">`Main` Yönteminizi `WorkingWithIntegers` olarak yeniden adlandırın ve çağıran `Main` `WorkingWithIntegers`yeni bir yöntem yazın.</span><span class="sxs-lookup"><span data-stu-id="87377-136">Rename your `Main` method to `WorkingWithIntegers` and write a new `Main` method that calls `WorkingWithIntegers`.</span></span> <span data-ttu-id="87377-137">Bitirdiğinizde, kodunuzun şöyle görünmesi gerekir:</span><span class="sxs-lookup"><span data-stu-id="87377-137">When you finish, your code should look like this:</span></span>

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

## <a name="explore-order-of-operations"></a><span data-ttu-id="87377-138">İşlem sırasını inceleme</span><span class="sxs-lookup"><span data-stu-id="87377-138">Explore order of operations</span></span>

<span data-ttu-id="87377-139">Çağrısını not edin `WorkingWithIntegers()`.</span><span class="sxs-lookup"><span data-stu-id="87377-139">Comment out the call to `WorkingWithIntegers()`.</span></span> <span data-ttu-id="87377-140">Bu bölümde çalışırken çıktının daha az karışık hale gelir:</span><span class="sxs-lookup"><span data-stu-id="87377-140">It will make the output less cluttered as you work in this section:</span></span>

```csharp
//WorkingWithIntegers();
```

<span data-ttu-id="87377-141">C# `//` dilinde bir **Açıklama** başlatır.</span><span class="sxs-lookup"><span data-stu-id="87377-141">The `//` starts a **comment** in C#.</span></span> <span data-ttu-id="87377-142">Açıklamalar, kaynak kodunuzda tutmak istediğiniz tüm metinlerdir, ancak kod olarak yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="87377-142">Comments are any text you want to keep in your source code but not execute as code.</span></span> <span data-ttu-id="87377-143">Derleyici açıklamalardan herhangi bir yürütülebilir kod oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="87377-143">The compiler doesn't generate any executable code from comments.</span></span>

<span data-ttu-id="87377-144">C# dili, farklı matematik işlemlerinin önceliğini matematikte öğrendiğiniz kurallarla tutarlı bir şekilde tanımlar.</span><span class="sxs-lookup"><span data-stu-id="87377-144">The C# language defines the precedence of different mathematics operations with rules consistent with the rules you learned in mathematics.</span></span>
<span data-ttu-id="87377-145">Çarpma ve bölme işlemleri, toplama ve çıkarma işlemlerinden önce gelir.</span><span class="sxs-lookup"><span data-stu-id="87377-145">Multiplication and division take precedence over addition and subtraction.</span></span>
<span data-ttu-id="87377-146">`Main` Yöntemine aşağıdaki kodu ekleyerek ve yürüterek `dotnet run`şunu araştırın:</span><span class="sxs-lookup"><span data-stu-id="87377-146">Explore that by adding the following code to your `Main` method, and executing `dotnet run`:</span></span>

```csharp
int a = 5;
int b = 4;
int c = 2;
int d = a + b * c;
Console.WriteLine(d);
 ```

<span data-ttu-id="87377-147">Çıkış, çarpma işleminin toplama işleminden önce gerçekleştiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="87377-147">The output demonstrates that the multiplication is performed before the addition.</span></span>

<span data-ttu-id="87377-148">Önce gerçekleştirilmesini istediğiniz işlemin veya işlemlerin çevresine parantez ekleyerek farklı bir işlem sırası zorlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="87377-148">You can force a different order of operation by adding parentheses around the operation or operations you want performed first.</span></span> <span data-ttu-id="87377-149">Aşağıdaki satırları ekleyin ve yeniden çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="87377-149">Add the following lines and run again:</span></span>

```csharp
d = (a + b) * c;
Console.WriteLine(d);
```

<span data-ttu-id="87377-150">Birçok farklı işlemi birleştirerek daha fazlasını keşfedin.</span><span class="sxs-lookup"><span data-stu-id="87377-150">Explore more by combining many different operations.</span></span> <span data-ttu-id="87377-151">`Main` Yönteminizin en altında aşağıdaki satırlara benzer bir şey ekleyin.</span><span class="sxs-lookup"><span data-stu-id="87377-151">Add something like the following lines at the bottom of your `Main` method.</span></span> <span data-ttu-id="87377-152">`dotnet run` komutunu yeniden deneyin.</span><span class="sxs-lookup"><span data-stu-id="87377-152">Try `dotnet run` again.</span></span>

```csharp
d = (a + b) - 6 * c + (12 * 4) / 3 + 12;
Console.WriteLine(d);
```

<span data-ttu-id="87377-153">Tamsayılar için farklı bir davranışla karşılaşmış olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="87377-153">You may have noticed an interesting behavior for integers.</span></span> <span data-ttu-id="87377-154">Sonucun ondalık veya kesir bölümü içermesini bekliyor olsanız da tamsayı bölme işlemi her zaman tamsayı sonucu verir.</span><span class="sxs-lookup"><span data-stu-id="87377-154">Integer division always produces an integer result, even when you'd expect the result to include a decimal or fractional portion.</span></span>

<span data-ttu-id="87377-155">Bu davranışı görmediyseniz, `Main` yönteminizin sonunda aşağıdaki kodu deneyin:</span><span class="sxs-lookup"><span data-stu-id="87377-155">If you haven't seen this behavior, try the following code at the end of your `Main` method:</span></span>

```csharp
int e = 7;
int f = 4;
int g = 3;
int h = (e + f) / g;
Console.WriteLine(h);
```

<span data-ttu-id="87377-156">Sonuçları `dotnet run` görmek için yeniden yazın.</span><span class="sxs-lookup"><span data-stu-id="87377-156">Type `dotnet run` again to see the results.</span></span>

<span data-ttu-id="87377-157">' In üzerine geçmeden önce, bu bölümde yazdığınız tüm kodu alıp yeni bir yönteme koyabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="87377-157">Before moving on, let's take all the code you've written in this section and put it in a new method.</span></span> <span data-ttu-id="87377-158">Bu yeni yöntemi `OrderPrecedence`çağırın.</span><span class="sxs-lookup"><span data-stu-id="87377-158">Call that new method `OrderPrecedence`.</span></span>
<span data-ttu-id="87377-159">Şöyle bir değer yazmalısınız:</span><span class="sxs-lookup"><span data-stu-id="87377-159">You should write something like this:</span></span>

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

## <a name="explore-integer-precision-and-limits"></a><span data-ttu-id="87377-160">Tamsayı duyarlığını ve sınırlarını inceleme</span><span class="sxs-lookup"><span data-stu-id="87377-160">Explore integer precision and limits</span></span>

<span data-ttu-id="87377-161">Son örnek, tamsayı bölme işleminin sonucu kestiğini size göstermiştir.</span><span class="sxs-lookup"><span data-stu-id="87377-161">That last sample showed you that integer division truncates the result.</span></span>
<span data-ttu-id="87377-162">**Geri kalanını** , **mod** işleci, `%` karakterini kullanarak edinebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="87377-162">You can get the **remainder** by using the **modulo** operator, the `%` character.</span></span> <span data-ttu-id="87377-163">Yönteyinizdeki `Main` aşağıdaki kodu deneyin:</span><span class="sxs-lookup"><span data-stu-id="87377-163">Try the following code in your `Main` method:</span></span>

```csharp
int a = 7;
int b = 4;
int c = 3;
int d = (a + b) / c;
int e = (a + b) % c;
Console.WriteLine($"quotient: {d}");
Console.WriteLine($"remainder: {e}");
```

<span data-ttu-id="87377-164">C# tamsayı türü diğer bir özelliğiyle matematiksel tamsayılardan farklıdır: `int` türünün alt ve üst sınırları vardır.</span><span class="sxs-lookup"><span data-stu-id="87377-164">The C# integer type differs from mathematical integers in one other way: the `int` type has minimum and maximum limits.</span></span> <span data-ttu-id="87377-165">Bu sınırları görmek için bu `Main` kodu yönteminizin içine ekleyin:</span><span class="sxs-lookup"><span data-stu-id="87377-165">Add this code to your `Main` method to see those limits:</span></span>

```csharp
int max = int.MaxValue;
int min = int.MinValue;
Console.WriteLine($"The range of integers is {min} to {max}");
```

<span data-ttu-id="87377-166">Bir hesaplama, bu sınırları aşan bir değer veriyorsa bu, **aşağı taşma** veya **taşma** koşulunuzun olduğu anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="87377-166">If a calculation produces a value that exceeds those limits, you have an **underflow** or **overflow** condition.</span></span> <span data-ttu-id="87377-167">Yanıtın bir sınırdan diğerine kaydığı görülüyor.</span><span class="sxs-lookup"><span data-stu-id="87377-167">The answer appears to wrap from one limit to the other.</span></span> <span data-ttu-id="87377-168">Bir örnek görmek için bu iki `Main` satırı yönteminizin içine ekleyin:</span><span class="sxs-lookup"><span data-stu-id="87377-168">Add these two lines to your `Main` method to see an example:</span></span>

```csharp
int what = max + 3;
Console.WriteLine($"An example of overflow: {what}");
```

<span data-ttu-id="87377-169">Yanıtın tam sayı alt sınırına (negatif) oldukça yakın olduğuna dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="87377-169">Notice that the answer is very close to the minimum (negative) integer.</span></span> <span data-ttu-id="87377-170">Bu, `min + 2` ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="87377-170">It's the same as `min + 2`.</span></span>
<span data-ttu-id="87377-171">Toplama işlemi, tamsayılar için izin verilen değerleri **aşmıştır**.</span><span class="sxs-lookup"><span data-stu-id="87377-171">The addition operation **overflowed** the allowed values for integers.</span></span>
<span data-ttu-id="87377-172">Taşma durumu en büyük olası tamsayı değerinden en küçük olana "kaydığından" yanıt oldukça büyük bir negatif sayıdır.</span><span class="sxs-lookup"><span data-stu-id="87377-172">The answer is a very large negative number because an overflow "wraps around" from the largest possible integer value to the smallest.</span></span>

<span data-ttu-id="87377-173">`int` türü, gereksinimlerinizi karşılamadığında kullanabileceğiniz farklı sınırlar ve duyarlık içeren başka sayısal türler de mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="87377-173">There are other numeric types with different limits and precision that you would use when the `int` type doesn't meet your needs.</span></span> <span data-ttu-id="87377-174">Daha sonra bu diğer türleri keşfedelim.</span><span class="sxs-lookup"><span data-stu-id="87377-174">Let's explore those other types next.</span></span>

<span data-ttu-id="87377-175">Bir kez daha, bu bölümde yazdığınız kodu ayrı bir yönteme taşıyalim.</span><span class="sxs-lookup"><span data-stu-id="87377-175">Once again, let's move the code you wrote in this section into a separate method.</span></span> <span data-ttu-id="87377-176">Bunu, `TestLimits` olarak adlandırın.</span><span class="sxs-lookup"><span data-stu-id="87377-176">Name it `TestLimits`.</span></span>

## <a name="work-with-the-double-type"></a><span data-ttu-id="87377-177">Çift tür ile çalışma</span><span class="sxs-lookup"><span data-stu-id="87377-177">Work with the double type</span></span>

<span data-ttu-id="87377-178">`double` sayısal türü, çift duyarlıklı kayan noktalı bir sayıyı ifade eder.</span><span class="sxs-lookup"><span data-stu-id="87377-178">The `double` numeric type represents a double-precision floating point number.</span></span> <span data-ttu-id="87377-179">Bu terimler sizin için yeni olabilir.</span><span class="sxs-lookup"><span data-stu-id="87377-179">Those terms may be new to you.</span></span> <span data-ttu-id="87377-180">**Kayan noktalı** sayı, büyüklük açısından oldukça büyük veya küçük olabilen, tamsayı olmayan değerleri ifade etmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="87377-180">A **floating point** number is useful to represent non-integral numbers that may be very large or small in magnitude.</span></span> <span data-ttu-id="87377-181">**Çift duyarlık** , değeri depolamak için kullanılan ikili basamak sayısını açıklayan göreli bir terimdir.</span><span class="sxs-lookup"><span data-stu-id="87377-181">**Double-precision** is a relative term that describes the number of binary digits used to store the value.</span></span> <span data-ttu-id="87377-182">**Çift duyarlık** sayıları, ikili basamakların sayısının **tek duyarlıklı**olarak iki katına sahiptir.</span><span class="sxs-lookup"><span data-stu-id="87377-182">**Double precision** numbers have twice the number of binary digits as **single-precision**.</span></span> <span data-ttu-id="87377-183">Modern bilgisayarlarda, tek duyarlık sayılarıyla çift duyarlık kullanmak daha yaygındır.</span><span class="sxs-lookup"><span data-stu-id="87377-183">On modern computers, it's more common to use double precision than single precision numbers.</span></span> <span data-ttu-id="87377-184">**Tek duyarlık** numaraları `float` anahtar sözcüğü kullanılarak belirtilir.</span><span class="sxs-lookup"><span data-stu-id="87377-184">**Single precision** numbers are declared using the `float` keyword.</span></span>
<span data-ttu-id="87377-185">İnceleyelim mi?</span><span class="sxs-lookup"><span data-stu-id="87377-185">Let's explore.</span></span> <span data-ttu-id="87377-186">Aşağıdaki kodu ekleyin ve sonucu görüntüleyin:</span><span class="sxs-lookup"><span data-stu-id="87377-186">Add the following code and see the result:</span></span>

```csharp
double a = 5;
double b = 4;
double c = 2;
double d = (a + b) / c;
Console.WriteLine(d);
```

<span data-ttu-id="87377-187">Yanıtın, bölümün ondalık kısmını içerdiğine dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="87377-187">Notice that the answer includes the decimal portion of the quotient.</span></span> <span data-ttu-id="87377-188">Çift değerlerle biraz daha karmaşık bir ifadeyi deneyin:</span><span class="sxs-lookup"><span data-stu-id="87377-188">Try a slightly more complicated expression with doubles:</span></span>

```csharp
double e = 19;
double f = 23;
double g = 8;
double h = (e + f) / g;
Console.WriteLine(h);
```

<span data-ttu-id="87377-189">Çift değerin aralığı, tamsayı değerlerinden çok daha büyüktür.</span><span class="sxs-lookup"><span data-stu-id="87377-189">The range of a double value is much greater than integer values.</span></span> <span data-ttu-id="87377-190">Şu ana kadar yazdıklarınız için aşağıdaki kodu deneyin:</span><span class="sxs-lookup"><span data-stu-id="87377-190">Try the following code below what you've written so far:</span></span>

```csharp
double max = double.MaxValue;
double min = double.MinValue;
Console.WriteLine($"The range of double is {min} to {max}");
```

<span data-ttu-id="87377-191">Bu değerler bilimsel gösterimde yazdırılır.</span><span class="sxs-lookup"><span data-stu-id="87377-191">These values are printed out in scientific notation.</span></span> <span data-ttu-id="87377-192">`E` değerinin sol tarafındaki sayı katsayıdır.</span><span class="sxs-lookup"><span data-stu-id="87377-192">The number to the left of the `E` is the significand.</span></span> <span data-ttu-id="87377-193">Sağ taraftaki sayı 10’un bir kuvveti olarak üstür.</span><span class="sxs-lookup"><span data-stu-id="87377-193">The number to the right is the exponent, as a power of 10.</span></span>

<span data-ttu-id="87377-194">Matematikteki ondalık sayılar gibi C# dilindeki çift değerlerde de yuvarlama hataları olabilir.</span><span class="sxs-lookup"><span data-stu-id="87377-194">Just like decimal numbers in math, doubles in C# can have rounding errors.</span></span> <span data-ttu-id="87377-195">Şu kodu deneyin:</span><span class="sxs-lookup"><span data-stu-id="87377-195">Try this code:</span></span>

```csharp
double third = 1.0 / 3.0;
Console.WriteLine(third);
```

<span data-ttu-id="87377-196">Yinelenen tam olarak `0.3` `1/3`aynı olmadığını bilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="87377-196">You know that `0.3` repeating isn't exactly the same as `1/3`.</span></span>

<span data-ttu-id="87377-197">***Sınama***</span><span class="sxs-lookup"><span data-stu-id="87377-197">***Challenge***</span></span>

<span data-ttu-id="87377-198">`double` Türü kullanarak büyük sayılar, küçük sayılar, çarpma ve bölme ile diğer hesaplamaları deneyin.</span><span class="sxs-lookup"><span data-stu-id="87377-198">Try other calculations with large numbers, small numbers, multiplication, and division using the `double` type.</span></span> <span data-ttu-id="87377-199">Daha karmaşık hesaplamalar deneyin.</span><span class="sxs-lookup"><span data-stu-id="87377-199">Try more complicated calculations.</span></span>

<span data-ttu-id="87377-200">Zorluğa bir süre harcadıktan sonra yazdığınız kodu alın ve yeni bir yönteme yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="87377-200">After you've spent some time with the challenge, take the code you've written and place it in a new method.</span></span> <span data-ttu-id="87377-201">Yeni yönteme `WorkWithDoubles`adlandırın.</span><span class="sxs-lookup"><span data-stu-id="87377-201">Name that new method `WorkWithDoubles`.</span></span>

## <a name="work-with-decimal-types"></a><span data-ttu-id="87377-202">Ondalık türlerle çalışma</span><span class="sxs-lookup"><span data-stu-id="87377-202">Work with decimal types</span></span>

<span data-ttu-id="87377-203">C# dilinde temel sayısal türleri gördünüz: tamsayılar ve çiftler.</span><span class="sxs-lookup"><span data-stu-id="87377-203">You've seen the basic numeric types in C#: integers and doubles.</span></span>  <span data-ttu-id="87377-204">Öğreneceğinizi öğrenmek için başka bir tür vardır: `decimal` türü.</span><span class="sxs-lookup"><span data-stu-id="87377-204">There's one other type to learn: the `decimal` type.</span></span> <span data-ttu-id="87377-205">`decimal` türü, `double` türünden daha küçük bir aralığa ancak daha fazla duyarlığa sahiptir.</span><span class="sxs-lookup"><span data-stu-id="87377-205">The `decimal` type has a smaller range but greater precision than `double`.</span></span> <span data-ttu-id="87377-206">Şimdi buna bir göz atalım:</span><span class="sxs-lookup"><span data-stu-id="87377-206">Let's take a look:</span></span>

```csharp
decimal min = decimal.MinValue;
decimal max = decimal.MaxValue;
Console.WriteLine($"The range of the decimal type is {min} to {max}");
```

<span data-ttu-id="87377-207">Aralığın `double` türünden daha küçük olduğuna dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="87377-207">Notice that the range is smaller than the `double` type.</span></span> <span data-ttu-id="87377-208">Aşağıdaki kodu deneyerek ondalık türünde daha fazla duyarlık olduğunu görebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="87377-208">You can see the greater precision with the decimal type by trying the following code:</span></span>

```csharp
double a = 1.0;
double b = 3.0;
Console.WriteLine(a / b);

decimal c = 1.0M;
decimal d = 3.0M;
Console.WriteLine(c / d);
```

<span data-ttu-id="87377-209">Sayılardaki `M` sonekiyle, bir sabit sayının `decimal` türünü nasıl kullanması gerektiğini belirtirsiniz.</span><span class="sxs-lookup"><span data-stu-id="87377-209">The `M` suffix on the numbers is how you indicate that a constant should use the `decimal` type.</span></span> <span data-ttu-id="87377-210">Aksi takdirde, derleyici `double` türü varsayar.</span><span class="sxs-lookup"><span data-stu-id="87377-210">Otherwise, the compiler assumes the `double` type.</span></span>

> [!NOTE]
> <span data-ttu-id="87377-211">Harf `M` , `double` ve `decimal` anahtar kelimeleri arasında en görsel olarak ayrı bir harf olarak seçilmiştir.</span><span class="sxs-lookup"><span data-stu-id="87377-211">The letter `M` was chosen as the most visually distinct letter between the `double` and `decimal` keywords.</span></span>

<span data-ttu-id="87377-212">Ondalık türünün kullanıldığı matematikte, ondalık ayırıcının sağ tarafında daha fazla basamak bulunduğunu görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="87377-212">Notice that the math using the decimal type has more digits to the right of the decimal point.</span></span>

<span data-ttu-id="87377-213">***Sınama***</span><span class="sxs-lookup"><span data-stu-id="87377-213">***Challenge***</span></span>

<span data-ttu-id="87377-214">Farklı sayısal türleri gördüğünüze göre yarı çapı 2,50 santimetre olan bir dairenin alanını hesaplayan kodu yazın.</span><span class="sxs-lookup"><span data-stu-id="87377-214">Now that you've seen the different numeric types, write code that calculates the area of a circle whose radius is 2.50 centimeters.</span></span> <span data-ttu-id="87377-215">Bir dairenin alanının, yarı çapın karesinin PI sayısı ile çarpımından elde edildiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="87377-215">Remember that the area of a circle is the radius squared multiplied by PI.</span></span> <span data-ttu-id="87377-216">İpucu: .NET, PI sayısı için kullanabileceğiniz <xref:System.Math.PI?displayProperty=nameWithType> sabit değerini içerir.</span><span class="sxs-lookup"><span data-stu-id="87377-216">One hint: .NET contains a constant for PI, <xref:System.Math.PI?displayProperty=nameWithType> that you can use for that value.</span></span> <span data-ttu-id="87377-217"><xref:System.Math.PI?displayProperty=nameWithType>, `System.Math` ad alanında belirtilen tüm sabitler gibi bir `double` değerdir.</span><span class="sxs-lookup"><span data-stu-id="87377-217"><xref:System.Math.PI?displayProperty=nameWithType>, like all constants declared in the `System.Math` namespace, is a `double` value.</span></span> <span data-ttu-id="87377-218">Bu nedenle, bu zorluk için `double` `decimal` değer yerine kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="87377-218">For that reason, you should use `double` instead of `decimal` values for this challenge.</span></span>

<span data-ttu-id="87377-219">19 ile 20 arasında bir yanıt almanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="87377-219">You should get an answer between 19 and 20.</span></span>
<span data-ttu-id="87377-220">[GitHub 'daki tamamlanmış örnek koda bakarak](https://github.com/dotnet/samples/tree/master/csharp/numbers-quickstart/Program.cs#L104-L106)yanıtınızı kontrol edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="87377-220">You can check your answer by [looking at the finished sample code on GitHub](https://github.com/dotnet/samples/tree/master/csharp/numbers-quickstart/Program.cs#L104-L106).</span></span>

<span data-ttu-id="87377-221">Dilerseniz diğer formüllerden de deneme yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="87377-221">Try some other formulas if you'd like.</span></span>

<span data-ttu-id="87377-222">"C# dilinde sayılar" hızlı başlangıç adımlarını tamamladınız.</span><span class="sxs-lookup"><span data-stu-id="87377-222">You've completed the "Numbers in C#" quickstart.</span></span> <span data-ttu-id="87377-223">Kendi geliştirme ortamınızda [dallar ve döngüler](branches-and-loops-local.md) hızlı başlangıç ile devam edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="87377-223">You can continue with the [Branches and loops](branches-and-loops-local.md) quickstart in your own development environment.</span></span>

<span data-ttu-id="87377-224">Aşağıdaki makalelerde C# dilinde sayılar hakkında daha fazla bilgi edinebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="87377-224">You can learn more about numbers in C# in the following articles:</span></span>

- [<span data-ttu-id="87377-225">Tamsayı sayısal türler</span><span class="sxs-lookup"><span data-stu-id="87377-225">Integral numeric types</span></span>](../../language-reference/builtin-types/integral-numeric-types.md)
- [<span data-ttu-id="87377-226">Kayan nokta sayısal türleri</span><span class="sxs-lookup"><span data-stu-id="87377-226">Floating-point numeric types</span></span>](../../language-reference/builtin-types/floating-point-numeric-types.md)
- [<span data-ttu-id="87377-227">Yerleşik sayısal dönüşümler</span><span class="sxs-lookup"><span data-stu-id="87377-227">Built-in numeric conversions</span></span>](../../language-reference/builtin-types/numeric-conversions.md)
