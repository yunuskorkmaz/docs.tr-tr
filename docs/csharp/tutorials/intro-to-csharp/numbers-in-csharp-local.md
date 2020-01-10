---
title: C# C#
description: Sayısal C# türleri, özelliklerini ve yöntemlerini inceleyerek bilgi edinin.
ms.date: 10/31/2017
ms.custom: mvc
ms.openlocfilehash: 7537bb597665461021946a792e342149f29c0e95
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75694666"
---
# <a name="manipulate-integral-and-floating-point-numbers-in-c"></a><span data-ttu-id="1b48c-103">C\# integral ve kayan nokta numaralarını işleme</span><span class="sxs-lookup"><span data-stu-id="1b48c-103">Manipulate integral and floating point numbers in C\#</span></span>

<span data-ttu-id="1b48c-104">Bu öğretici, size etkileşimli olarak C# sayısal türler öğretir.</span><span class="sxs-lookup"><span data-stu-id="1b48c-104">This tutorial teaches you about the numeric types in C# interactively.</span></span> <span data-ttu-id="1b48c-105">Küçük miktarlarda kod yazacaksınız, daha sonra bu kodu derleyip çalıştıracaksınız.</span><span class="sxs-lookup"><span data-stu-id="1b48c-105">You'll write small amounts of code, then you'll compile and run that code.</span></span> <span data-ttu-id="1b48c-106">Öğreticide, içindeki C#sayıları ve matematik işlemlerini keşfettiği bir dizi ders bulunur.</span><span class="sxs-lookup"><span data-stu-id="1b48c-106">The tutorial contains a series of lessons that explore numbers and math operations in C#.</span></span> <span data-ttu-id="1b48c-107">Bu dersler size C# dilinin temel özelliklerini öğretir.</span><span class="sxs-lookup"><span data-stu-id="1b48c-107">These lessons teach you the fundamentals of the C# language.</span></span>

<span data-ttu-id="1b48c-108">Bu öğreticide, geliştirme için kullanabileceğiniz bir makineniz olması beklenir.</span><span class="sxs-lookup"><span data-stu-id="1b48c-108">This tutorial expects you to have a machine you can use for development.</span></span> <span data-ttu-id="1b48c-109">[10 dakika içinde Merhaba Dünya](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) .NET öğreticisi, Windows, Linux veya MacOS 'ta yerel geliştirme ortamınızı ayarlamaya yönelik yönergeler içerir.</span><span class="sxs-lookup"><span data-stu-id="1b48c-109">The .NET tutorial [Hello World in 10 minutes](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) has instructions for setting up your local development environment on Windows, Linux, or macOS.</span></span> <span data-ttu-id="1b48c-110">Kullanacağınız komutlara hızlı bir genel bakış, daha fazla ayrıntı için bağlantılarla birlikte [geliştirme araçları hakkında bilgi sahibi olmaya gelmiştir](local-environment.md) .</span><span class="sxs-lookup"><span data-stu-id="1b48c-110">A quick overview of the commands you'll use is in the [Become familiar with the development tools](local-environment.md) with links to more details.</span></span>

## <a name="explore-integer-math"></a><span data-ttu-id="1b48c-111">Tamsayı matematiğini inceleme</span><span class="sxs-lookup"><span data-stu-id="1b48c-111">Explore integer math</span></span>

<span data-ttu-id="1b48c-112">Sayı adlı bir dizin oluşturun *-hızlı başlangıç*.</span><span class="sxs-lookup"><span data-stu-id="1b48c-112">Create a directory named *numbers-quickstart*.</span></span> <span data-ttu-id="1b48c-113">Geçerli dizini yapın ve şu komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="1b48c-113">Make that the current directory and run the following command:</span></span>

```dotnetcli
dotnet new console -n NumbersInCSharp -o .
```

<span data-ttu-id="1b48c-114">En sevdiğiniz düzenleyicide *program.cs* açın ve satır `Console.WriteLine("Hello World!");` aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="1b48c-114">Open *Program.cs* in your favorite editor, and replace the line `Console.WriteLine("Hello World!");` with the following:</span></span>

```csharp
int a = 18;
int b = 6;
int c = a + b;
Console.WriteLine(c);
```

<span data-ttu-id="1b48c-115">Komut pencerenize `dotnet run` yazarak bu kodu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="1b48c-115">Run this code by typing `dotnet run` in your command window.</span></span>

<span data-ttu-id="1b48c-116">Az önce tamsayılarla gerçekleştirilen temel matematik işlemlerinden birini gördünüz.</span><span class="sxs-lookup"><span data-stu-id="1b48c-116">You've just seen one of the fundamental math operations with integers.</span></span> <span data-ttu-id="1b48c-117">`int` türü bir **tamsayıyı**, sıfır, pozitif veya negatif bir tam sayıyı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="1b48c-117">The `int` type represents an **integer**, a zero, positive, or negative whole number.</span></span> <span data-ttu-id="1b48c-118">Toplama için `+` sembolünü kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="1b48c-118">You use the `+` symbol for addition.</span></span> <span data-ttu-id="1b48c-119">Tamsayılar için sıklıkla kullanılan diğer matematiksel işlemler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="1b48c-119">Other common mathematical operations for integers include:</span></span>

- <span data-ttu-id="1b48c-120">çıkarma için `-`</span><span class="sxs-lookup"><span data-stu-id="1b48c-120">`-` for subtraction</span></span>
- <span data-ttu-id="1b48c-121">çarpma için `*`</span><span class="sxs-lookup"><span data-stu-id="1b48c-121">`*` for multiplication</span></span>
- <span data-ttu-id="1b48c-122">bölme için `/`</span><span class="sxs-lookup"><span data-stu-id="1b48c-122">`/` for division</span></span>

<span data-ttu-id="1b48c-123">Bu farklı işlemleri keşfederek başlayın.</span><span class="sxs-lookup"><span data-stu-id="1b48c-123">Start by exploring those different operations.</span></span> <span data-ttu-id="1b48c-124">`c`değerini yazan satırdan sonra bu satırları ekleyin:</span><span class="sxs-lookup"><span data-stu-id="1b48c-124">Add these lines after the line that writes the value of `c`:</span></span>

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

<span data-ttu-id="1b48c-125">Komut pencerenize `dotnet run` yazarak bu kodu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="1b48c-125">Run this code by typing `dotnet run` in your command window.</span></span>

<span data-ttu-id="1b48c-126">Ayrıca dilerseniz aynı satırda birden çok matematik işlemi gerçekleştirerek de deneme yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1b48c-126">You can also experiment by performing multiple mathematics operations in the same line, if you'd like.</span></span> <span data-ttu-id="1b48c-127">Örneğin `c = a + b - 12 * 17;` deneyin.</span><span class="sxs-lookup"><span data-stu-id="1b48c-127">Try `c = a + b - 12 * 17;` for example.</span></span> <span data-ttu-id="1b48c-128">Değişkenlerin ve sabit sayıların karıştırılmasına izin verilir.</span><span class="sxs-lookup"><span data-stu-id="1b48c-128">Mixing variables and constant numbers is allowed.</span></span>

> [!TIP]
> <span data-ttu-id="1b48c-129">C# dilini (veya herhangi bir programlama dilini) keşfederken, kod yazdığınızda hatalar yapacaksınız.</span><span class="sxs-lookup"><span data-stu-id="1b48c-129">As you explore C# (or any programming language), you'll make mistakes when you write code.</span></span> <span data-ttu-id="1b48c-130">**Derleyici** bu hataları bulup size bildirir.</span><span class="sxs-lookup"><span data-stu-id="1b48c-130">The **compiler** will find those errors and report them to you.</span></span> <span data-ttu-id="1b48c-131">Çıktı hata iletileri içerdiğinde, nelerin düzeltileceğini görmek için örnek koda ve penceredeki koda yakından bakın.</span><span class="sxs-lookup"><span data-stu-id="1b48c-131">When the output contains error messages, look closely at the example code and the code in your window to see what to fix.</span></span>
> <span data-ttu-id="1b48c-132">Bu alıştırma, C# kodunun yapısını öğrenmenize yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="1b48c-132">That exercise will help you learn the structure of C# code.</span></span>

<span data-ttu-id="1b48c-133">İlk adımı tamamladınız.</span><span class="sxs-lookup"><span data-stu-id="1b48c-133">You've finished the first step.</span></span> <span data-ttu-id="1b48c-134">Sonraki bölüme başlamadan önce geçerli kodu ayrı bir yönteme taşıyalim.</span><span class="sxs-lookup"><span data-stu-id="1b48c-134">Before you start the next section, let's move the current code into a separate method.</span></span> <span data-ttu-id="1b48c-135">Bu, yeni bir örnekle çalışmaya başlamasını kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="1b48c-135">That makes it easier to start working with a new example.</span></span> <span data-ttu-id="1b48c-136">`Main` yönteminizi `WorkingWithIntegers` olarak yeniden adlandırın ve `WorkingWithIntegers`çağıran yeni bir `Main` yöntemi yazın.</span><span class="sxs-lookup"><span data-stu-id="1b48c-136">Rename your `Main` method to `WorkingWithIntegers` and write a new `Main` method that calls `WorkingWithIntegers`.</span></span> <span data-ttu-id="1b48c-137">Bitirdiğinizde, kodunuzun şöyle görünmesi gerekir:</span><span class="sxs-lookup"><span data-stu-id="1b48c-137">When you finish, your code should look like this:</span></span>

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

## <a name="explore-order-of-operations"></a><span data-ttu-id="1b48c-138">İşlem sırasını inceleme</span><span class="sxs-lookup"><span data-stu-id="1b48c-138">Explore order of operations</span></span>

<span data-ttu-id="1b48c-139">`WorkingWithIntegers()`çağrısını açıklama.</span><span class="sxs-lookup"><span data-stu-id="1b48c-139">Comment out the call to `WorkingWithIntegers()`.</span></span> <span data-ttu-id="1b48c-140">Bu bölümde çalışırken çıktının daha az karışık hale gelir:</span><span class="sxs-lookup"><span data-stu-id="1b48c-140">It will make the output less cluttered as you work in this section:</span></span>

```csharp
//WorkingWithIntegers();
```

<span data-ttu-id="1b48c-141">`//` içinde C#bir **yorum** başlatır.</span><span class="sxs-lookup"><span data-stu-id="1b48c-141">The `//` starts a **comment** in C#.</span></span> <span data-ttu-id="1b48c-142">Açıklamalar, kaynak kodunuzda tutmak istediğiniz tüm metinlerdir, ancak kod olarak yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="1b48c-142">Comments are any text you want to keep in your source code but not execute as code.</span></span> <span data-ttu-id="1b48c-143">Derleyici açıklamalardan herhangi bir yürütülebilir kod oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="1b48c-143">The compiler does not generate any executable code from comments.</span></span>

<span data-ttu-id="1b48c-144">C# dili, farklı matematik işlemlerinin önceliğini matematikte öğrendiğiniz kurallarla tutarlı bir şekilde tanımlar.</span><span class="sxs-lookup"><span data-stu-id="1b48c-144">The C# language defines the precedence of different mathematics operations with rules consistent with the rules you learned in mathematics.</span></span>
<span data-ttu-id="1b48c-145">Çarpma ve bölme işlemleri, toplama ve çıkarma işlemlerinden önce gelir.</span><span class="sxs-lookup"><span data-stu-id="1b48c-145">Multiplication and division take precedence over addition and subtraction.</span></span>
<span data-ttu-id="1b48c-146">`Main` yöntemine aşağıdaki kodu ekleyerek ve `dotnet run`yürüterek bunu keşfedebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="1b48c-146">Explore that by adding the following code to your `Main` method, and executing `dotnet run`:</span></span>

```csharp
int a = 5;
int b = 4;
int c = 2;
int d = a + b * c;
Console.WriteLine(d);
 ```

<span data-ttu-id="1b48c-147">Çıkış, çarpma işleminin toplama işleminden önce gerçekleştiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="1b48c-147">The output demonstrates that the multiplication is performed before the addition.</span></span>

<span data-ttu-id="1b48c-148">Önce gerçekleştirilmesini istediğiniz işlemin veya işlemlerin çevresine parantez ekleyerek farklı bir işlem sırası zorlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1b48c-148">You can force a different order of operation by adding parentheses around the operation or operations you want performed first.</span></span> <span data-ttu-id="1b48c-149">Aşağıdaki satırları ekleyin ve yeniden çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="1b48c-149">Add the following lines and run again:</span></span>

```csharp
d = (a + b) * c;
Console.WriteLine(d);
```

<span data-ttu-id="1b48c-150">Birçok farklı işlemi birleştirerek daha fazlasını keşfedin.</span><span class="sxs-lookup"><span data-stu-id="1b48c-150">Explore more by combining many different operations.</span></span> <span data-ttu-id="1b48c-151">`Main` yönteminizin en altında aşağıdaki satırlara benzer bir şey ekleyin.</span><span class="sxs-lookup"><span data-stu-id="1b48c-151">Add something like the following lines at the bottom of your `Main` method.</span></span> <span data-ttu-id="1b48c-152">`dotnet run` komutunu yeniden deneyin.</span><span class="sxs-lookup"><span data-stu-id="1b48c-152">Try `dotnet run` again.</span></span>

```csharp
d = (a + b) - 6 * c + (12 * 4) / 3 + 12;
Console.WriteLine(d);
```

<span data-ttu-id="1b48c-153">Tamsayılar için farklı bir davranışla karşılaşmış olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1b48c-153">You may have noticed an interesting behavior for integers.</span></span> <span data-ttu-id="1b48c-154">Sonucun ondalık veya kesir bölümü içermesini bekliyor olsanız da tamsayı bölme işlemi her zaman tamsayı sonucu verir.</span><span class="sxs-lookup"><span data-stu-id="1b48c-154">Integer division always produces an integer result, even when you'd expect the result to include a decimal or fractional portion.</span></span>

<span data-ttu-id="1b48c-155">Bu davranışı görmediyseniz, `Main` yönteminizin sonunda aşağıdaki kodu deneyin:</span><span class="sxs-lookup"><span data-stu-id="1b48c-155">If you haven't seen this behavior, try the following code at the end of your `Main` method:</span></span>

```csharp
int e = 7;
int f = 4;
int g = 3;
int h = (e + f) / g;
Console.WriteLine(h);
```

<span data-ttu-id="1b48c-156">Sonuçları görmek için yeniden `dotnet run` yazın.</span><span class="sxs-lookup"><span data-stu-id="1b48c-156">Type `dotnet run` again to see the results.</span></span>

<span data-ttu-id="1b48c-157">' In üzerine geçmeden önce, bu bölümde yazdığınız tüm kodu alıp yeni bir yönteme koyabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1b48c-157">Before moving on, let's take all the code you've written in this section and put it in a new method.</span></span> <span data-ttu-id="1b48c-158">Yeni yöntemin `OrderPrecedence`çağırın.</span><span class="sxs-lookup"><span data-stu-id="1b48c-158">Call that new method `OrderPrecedence`.</span></span>
<span data-ttu-id="1b48c-159">Şöyle bir işlem yapmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="1b48c-159">You should end up with something like this:</span></span>

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

## <a name="explore-integer-precision-and-limits"></a><span data-ttu-id="1b48c-160">Tamsayı duyarlığını ve sınırlarını inceleme</span><span class="sxs-lookup"><span data-stu-id="1b48c-160">Explore integer precision and limits</span></span>

<span data-ttu-id="1b48c-161">Son örnek, tamsayı bölme işleminin sonucu kestiğini size göstermiştir.</span><span class="sxs-lookup"><span data-stu-id="1b48c-161">That last sample showed you that integer division truncates the result.</span></span>
<span data-ttu-id="1b48c-162">`%` karakteri olan **Modül** işlecini kullanarak **kalanı** alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1b48c-162">You can get the **remainder** by using the **modulo** operator, the `%` character.</span></span> <span data-ttu-id="1b48c-163">`Main` yönteminde aşağıdaki kodu deneyin:</span><span class="sxs-lookup"><span data-stu-id="1b48c-163">Try the following code in your `Main` method:</span></span>

```csharp
int a = 7;
int b = 4;
int c = 3;
int d = (a + b) / c;
int e = (a + b) % c;
Console.WriteLine($"quotient: {d}");
Console.WriteLine($"remainder: {e}");
```

<span data-ttu-id="1b48c-164">C# tamsayı türü diğer bir özelliğiyle matematiksel tamsayılardan farklıdır: `int` türünün alt ve üst sınırları vardır.</span><span class="sxs-lookup"><span data-stu-id="1b48c-164">The C# integer type differs from mathematical integers in one other way: the `int` type has minimum and maximum limits.</span></span> <span data-ttu-id="1b48c-165">Bu sınırları görmek için bu kodu `Main` yöntemine ekleyin:</span><span class="sxs-lookup"><span data-stu-id="1b48c-165">Add this code to your `Main` method to see those limits:</span></span>

```csharp
int max = int.MaxValue;
int min = int.MinValue;
Console.WriteLine($"The range of integers is {min} to {max}");
```

<span data-ttu-id="1b48c-166">Bir hesaplama, bu sınırları aşan bir değer veriyorsa bu, **aşağı taşma** veya **taşma** koşulunuzun olduğu anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="1b48c-166">If a calculation produces a value that exceeds those limits, you have an **underflow** or **overflow** condition.</span></span> <span data-ttu-id="1b48c-167">Yanıtın bir sınırdan diğerine kaydığı görülüyor.</span><span class="sxs-lookup"><span data-stu-id="1b48c-167">The answer appears to wrap from one limit to the other.</span></span> <span data-ttu-id="1b48c-168">Örnek görmek için bu iki satırı `Main` yöntemine ekleyin:</span><span class="sxs-lookup"><span data-stu-id="1b48c-168">Add these two lines to your `Main` method to see an example:</span></span>

```csharp
int what = max + 3;
Console.WriteLine($"An example of overflow: {what}");
```

<span data-ttu-id="1b48c-169">Yanıtın tam sayı alt sınırına (negatif) oldukça yakın olduğuna dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="1b48c-169">Notice that the answer is very close to the minimum (negative) integer.</span></span> <span data-ttu-id="1b48c-170">Bu, `min + 2` ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="1b48c-170">It's the same as `min + 2`.</span></span>
<span data-ttu-id="1b48c-171">Toplama işlemi, tamsayılar için izin verilen değerleri **aşmıştır**.</span><span class="sxs-lookup"><span data-stu-id="1b48c-171">The addition operation **overflowed** the allowed values for integers.</span></span>
<span data-ttu-id="1b48c-172">Taşma durumu en büyük olası tamsayı değerinden en küçük olana "kaydığından" yanıt oldukça büyük bir negatif sayıdır.</span><span class="sxs-lookup"><span data-stu-id="1b48c-172">The answer is a very large negative number because an overflow "wraps around" from the largest possible integer value to the smallest.</span></span>

<span data-ttu-id="1b48c-173">`int` türü, gereksinimlerinizi karşılamadığında kullanabileceğiniz farklı sınırlar ve duyarlık içeren başka sayısal türler de mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="1b48c-173">There are other numeric types with different limits and precision that you would use when the `int` type doesn't meet your needs.</span></span> <span data-ttu-id="1b48c-174">Bir sonraki adımda bunları inceleyelim.</span><span class="sxs-lookup"><span data-stu-id="1b48c-174">Let's explore those next.</span></span>

<span data-ttu-id="1b48c-175">Bir kez daha, bu bölümde yazdığınız kodu ayrı bir yönteme taşıyalim.</span><span class="sxs-lookup"><span data-stu-id="1b48c-175">Once again, let's move the code you wrote in this section into a separate method.</span></span> <span data-ttu-id="1b48c-176">Bunu, `TestLimits` olarak adlandırın.</span><span class="sxs-lookup"><span data-stu-id="1b48c-176">Name it `TestLimits`.</span></span>

## <a name="work-with-the-double-type"></a><span data-ttu-id="1b48c-177">Çift tür ile çalışma</span><span class="sxs-lookup"><span data-stu-id="1b48c-177">Work with the double type</span></span>

<span data-ttu-id="1b48c-178">`double` sayısal türü, çift duyarlıklı kayan noktalı bir sayıyı ifade eder.</span><span class="sxs-lookup"><span data-stu-id="1b48c-178">The `double` numeric type represents a double-precision floating point number.</span></span> <span data-ttu-id="1b48c-179">Bu terimler sizin için yeni olabilir.</span><span class="sxs-lookup"><span data-stu-id="1b48c-179">Those terms may be new to you.</span></span> <span data-ttu-id="1b48c-180">**Kayan noktalı** sayı, büyüklük açısından oldukça büyük veya küçük olabilen, tamsayı olmayan değerleri ifade etmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1b48c-180">A **floating point** number is useful to represent non-integral numbers that may be very large or small in magnitude.</span></span> <span data-ttu-id="1b48c-181">**Çift duyarlıklı**, bu sayıların **tek duyarlıktan** daha fazla duyarlık kullanılarak depolandığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="1b48c-181">**Double-precision** means that these numbers are stored using greater precision than **single-precision**.</span></span> <span data-ttu-id="1b48c-182">Modern bilgisayarlarda çift duyarlıklı sayı kullanımı, tek duyarlıklı sayılara göre daha yaygındır.</span><span class="sxs-lookup"><span data-stu-id="1b48c-182">On modern computers, it is more common to use double precision than single precision numbers.</span></span>
<span data-ttu-id="1b48c-183">İnceleyelim mi?</span><span class="sxs-lookup"><span data-stu-id="1b48c-183">Let's explore.</span></span> <span data-ttu-id="1b48c-184">Aşağıdaki kodu ekleyin ve sonucu görüntüleyin:</span><span class="sxs-lookup"><span data-stu-id="1b48c-184">Add the following code and see the result:</span></span>

```csharp
double a = 5;
double b = 4;
double c = 2;
double d = (a + b) / c;
Console.WriteLine(d);
```

<span data-ttu-id="1b48c-185">Yanıtın, bölümün ondalık kısmını içerdiğine dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="1b48c-185">Notice that the answer includes the decimal portion of the quotient.</span></span> <span data-ttu-id="1b48c-186">Çift değerlerle biraz daha karmaşık bir ifadeyi deneyin:</span><span class="sxs-lookup"><span data-stu-id="1b48c-186">Try a slightly more complicated expression with doubles:</span></span>

```csharp
double e = 19;
double f = 23;
double g = 8;
double h = (e + f) / g;
Console.WriteLine(h);
```

<span data-ttu-id="1b48c-187">Çift değerin aralığı, tamsayı değerlerinden çok daha büyüktür.</span><span class="sxs-lookup"><span data-stu-id="1b48c-187">The range of a double value is much greater than integer values.</span></span> <span data-ttu-id="1b48c-188">Şu ana kadar yazdıklarınız için aşağıdaki kodu deneyin:</span><span class="sxs-lookup"><span data-stu-id="1b48c-188">Try the following code below what you've written so far:</span></span>

```csharp
double max = double.MaxValue;
double min = double.MinValue;
Console.WriteLine($"The range of double is {min} to {max}");
```

<span data-ttu-id="1b48c-189">Bu değerler bilimsel gösterimde yazdırılır.</span><span class="sxs-lookup"><span data-stu-id="1b48c-189">These values are printed out in scientific notation.</span></span> <span data-ttu-id="1b48c-190">`E` değerinin sol tarafındaki sayı katsayıdır.</span><span class="sxs-lookup"><span data-stu-id="1b48c-190">The number to the left of the `E` is the significand.</span></span> <span data-ttu-id="1b48c-191">Sağ taraftaki sayı 10’un bir kuvveti olarak üstür.</span><span class="sxs-lookup"><span data-stu-id="1b48c-191">The number to the right is the exponent, as a power of 10.</span></span>

<span data-ttu-id="1b48c-192">Matematikteki ondalık sayılar gibi C# dilindeki çift değerlerde de yuvarlama hataları olabilir.</span><span class="sxs-lookup"><span data-stu-id="1b48c-192">Just like decimal numbers in math, doubles in C# can have rounding errors.</span></span> <span data-ttu-id="1b48c-193">Şu kodu deneyin:</span><span class="sxs-lookup"><span data-stu-id="1b48c-193">Try this code:</span></span>

```csharp
double third = 1.0 / 3.0;
Console.WriteLine(third);
```

<span data-ttu-id="1b48c-194">`0.3` yinelemesinin `1/3` ile tam olarak aynı olmadığını fark edersiniz.</span><span class="sxs-lookup"><span data-stu-id="1b48c-194">You know that `0.3` repeating is not exactly the same as `1/3`.</span></span>

<span data-ttu-id="1b48c-195">***Görev***</span><span class="sxs-lookup"><span data-stu-id="1b48c-195">***Challenge***</span></span>

<span data-ttu-id="1b48c-196">`double` türünü kullanarak büyük sayılar, küçük sayılar, çarpma işlemi ve bölme işlemi ile diğer hesaplamaları deneyin.</span><span class="sxs-lookup"><span data-stu-id="1b48c-196">Try other calculations with large numbers, small numbers, multiplication and division using the `double` type.</span></span> <span data-ttu-id="1b48c-197">Daha karmaşık hesaplamalar deneyin.</span><span class="sxs-lookup"><span data-stu-id="1b48c-197">Try more complicated calculations.</span></span>

<span data-ttu-id="1b48c-198">Zorluğa bir süre harcadıktan sonra yazdığınız kodu alın ve yeni bir yönteme yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="1b48c-198">After you've spent some time with the challenge, take the code you've written and place it in a new method.</span></span> <span data-ttu-id="1b48c-199">Yeni yöntemin `WorkWithDoubles`adı.</span><span class="sxs-lookup"><span data-stu-id="1b48c-199">Name that new method `WorkWithDoubles`.</span></span>

## <a name="work-with-fixed-point-types"></a><span data-ttu-id="1b48c-200">Sabit nokta türleriyle çalışma</span><span class="sxs-lookup"><span data-stu-id="1b48c-200">Work with fixed point types</span></span>

<span data-ttu-id="1b48c-201">C# dilinde temel sayısal türleri gördünüz: tamsayılar ve çiftler.</span><span class="sxs-lookup"><span data-stu-id="1b48c-201">You've seen the basic numeric types in C#: integers and doubles.</span></span>  <span data-ttu-id="1b48c-202">Öğrenmeniz gereken bir tür daha vardır: `decimal` türü.</span><span class="sxs-lookup"><span data-stu-id="1b48c-202">There is one other type to learn: the `decimal` type.</span></span> <span data-ttu-id="1b48c-203">`decimal` türü, `double` türünden daha küçük bir aralığa ancak daha fazla duyarlığa sahiptir.</span><span class="sxs-lookup"><span data-stu-id="1b48c-203">The `decimal` type has a smaller range but greater precision than `double`.</span></span> <span data-ttu-id="1b48c-204">**Sabit nokta** terimi, ondalık ayırıcının (veya ikili noktasının) hareket etmediği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="1b48c-204">The term **fixed point** means that the decimal point (or binary point) doesn't move.</span></span> <span data-ttu-id="1b48c-205">Bir göz atalım:</span><span class="sxs-lookup"><span data-stu-id="1b48c-205">Let's take a look:</span></span>

```csharp
decimal min = decimal.MinValue;
decimal max = decimal.MaxValue;
Console.WriteLine($"The range of the decimal type is {min} to {max}");
```

<span data-ttu-id="1b48c-206">Aralığın `double` türünden daha küçük olduğuna dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="1b48c-206">Notice that the range is smaller than the `double` type.</span></span> <span data-ttu-id="1b48c-207">Aşağıdaki kodu deneyerek ondalık türünde daha fazla duyarlık olduğunu görebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="1b48c-207">You can see the greater precision with the decimal type by trying the following code:</span></span>

```csharp
double a = 1.0;
double b = 3.0;
Console.WriteLine(a / b);

decimal c = 1.0M;
decimal d = 3.0M;
Console.WriteLine(c / d);
```

<span data-ttu-id="1b48c-208">Sayılardaki `M` sonekiyle, bir sabit sayının `decimal` türünü nasıl kullanması gerektiğini belirtirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1b48c-208">The `M` suffix on the numbers is how you indicate that a constant should use the `decimal` type.</span></span>

<span data-ttu-id="1b48c-209">Ondalık türünün kullanıldığı matematikte, ondalık ayırıcının sağ tarafında daha fazla basamak bulunduğunu görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1b48c-209">Notice that the math using the decimal type has more digits to the right of the decimal point.</span></span>

<span data-ttu-id="1b48c-210">***Görev***</span><span class="sxs-lookup"><span data-stu-id="1b48c-210">***Challenge***</span></span>

<span data-ttu-id="1b48c-211">Farklı sayısal türleri gördüğünüze göre yarı çapı 2,50 santimetre olan bir dairenin alanını hesaplayan kodu yazın.</span><span class="sxs-lookup"><span data-stu-id="1b48c-211">Now that you've seen the different numeric types, write code that calculates the area of a circle whose radius is 2.50 centimeters.</span></span> <span data-ttu-id="1b48c-212">Bir dairenin alanının, yarı çapın karesinin PI sayısı ile çarpımından elde edildiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="1b48c-212">Remember that the area of a circle is the radius squared multiplied by PI.</span></span> <span data-ttu-id="1b48c-213">İpucu: .NET, PI sayısı için kullanabileceğiniz <xref:System.Math.PI?displayProperty=nameWithType> sabit değerini içerir.</span><span class="sxs-lookup"><span data-stu-id="1b48c-213">One hint: .NET contains a constant for PI, <xref:System.Math.PI?displayProperty=nameWithType> that you can use for that value.</span></span>

<span data-ttu-id="1b48c-214">19 ile 20 arasında bir yanıt almanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="1b48c-214">You should get an answer between 19 and 20.</span></span>
<span data-ttu-id="1b48c-215">[GitHub 'daki tamamlanmış örnek koda bakarak](https://github.com/dotnet/samples/tree/master/csharp/numbers-quickstart/Program.cs#L104-L106)yanıtınızı kontrol edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1b48c-215">You can check your answer by [looking at the finished sample code on GitHub](https://github.com/dotnet/samples/tree/master/csharp/numbers-quickstart/Program.cs#L104-L106).</span></span>

<span data-ttu-id="1b48c-216">Dilerseniz diğer formüllerden de deneme yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1b48c-216">Try some other formulas if you'd like.</span></span>

<span data-ttu-id="1b48c-217">"Numaraları C#" hızlı başlangıç adımlarını tamamladınız.</span><span class="sxs-lookup"><span data-stu-id="1b48c-217">You've completed the "Numbers in C#" quickstart.</span></span> <span data-ttu-id="1b48c-218">Kendi geliştirme ortamınızda [dallar ve döngüler](branches-and-loops-local.md) hızlı başlangıç ile devam edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1b48c-218">You can continue with the [Branches and loops](branches-and-loops-local.md) quickstart in your own development environment.</span></span>

<span data-ttu-id="1b48c-219">Aşağıdaki konularda C# dilinde sayılar hakkında daha fazla bilgi edinebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="1b48c-219">You can learn more about numbers in C# in the following topics:</span></span>

- [<span data-ttu-id="1b48c-220">Integral sayısal türleri</span><span class="sxs-lookup"><span data-stu-id="1b48c-220">Integral numeric types</span></span>](../../language-reference/builtin-types/integral-numeric-types.md)
- [<span data-ttu-id="1b48c-221">Kayan nokta sayısal türleri</span><span class="sxs-lookup"><span data-stu-id="1b48c-221">Floating-point numeric types</span></span>](../../language-reference/builtin-types/floating-point-numeric-types.md)
- [<span data-ttu-id="1b48c-222">Yerleşik sayısal dönüşümler</span><span class="sxs-lookup"><span data-stu-id="1b48c-222">Built-in numeric conversions</span></span>](../../language-reference/builtin-types/numeric-conversions.md)
