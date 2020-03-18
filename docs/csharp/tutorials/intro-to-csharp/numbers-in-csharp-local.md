---
title: C# sayılar - C# eğitimine giriş
description: Sayısal türleri, özelliklerini ve yöntemlerini inceleyerek C# öğrenin.
ms.date: 10/31/2017
ms.custom: mvc
ms.openlocfilehash: 7e9af4b3b859f74d7e92ff10b3964ddd59d2473b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79156551"
---
# <a name="manipulate-integral-and-floating-point-numbers-in-c"></a><span data-ttu-id="78d22-103">C'deki integral ve kayan nokta sayılarını işleme\#</span><span class="sxs-lookup"><span data-stu-id="78d22-103">Manipulate integral and floating point numbers in C\#</span></span>

<span data-ttu-id="78d22-104">Bu öğretici c # interaktif sayısal türleri hakkında öğretir.</span><span class="sxs-lookup"><span data-stu-id="78d22-104">This tutorial teaches you about the numeric types in C# interactively.</span></span> <span data-ttu-id="78d22-105">Küçük miktarlarda kod yazacaksın, sonra bu kodu derleyip çalıştıracaksın.</span><span class="sxs-lookup"><span data-stu-id="78d22-105">You'll write small amounts of code, then you'll compile and run that code.</span></span> <span data-ttu-id="78d22-106">Öğretici C# numaraları ve matematik işlemleri keşfetmek dersler bir dizi içerir.</span><span class="sxs-lookup"><span data-stu-id="78d22-106">The tutorial contains a series of lessons that explore numbers and math operations in C#.</span></span> <span data-ttu-id="78d22-107">Bu dersler size C# dilinin temel özelliklerini öğretir.</span><span class="sxs-lookup"><span data-stu-id="78d22-107">These lessons teach you the fundamentals of the C# language.</span></span>

<span data-ttu-id="78d22-108">Bu öğretici, geliştirme için kullanabileceğiniz bir makineye sahip olmak için bekliyor.</span><span class="sxs-lookup"><span data-stu-id="78d22-108">This tutorial expects you to have a machine you can use for development.</span></span> <span data-ttu-id="78d22-109">.NET öğretici [Hello World 10 dakika içinde](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) Windows, Linux veya macOS'ta yerel geliştirme ortamınızı ayarlama talimatları na sahiptir.</span><span class="sxs-lookup"><span data-stu-id="78d22-109">The .NET tutorial [Hello World in 10 minutes](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) has instructions for setting up your local development environment on Windows, Linux, or macOS.</span></span> <span data-ttu-id="78d22-110">Kullanacağınız komutların hızlı bir genel bakışı, daha fazla ayrıntıya bağlantılar içeren [geliştirme araçlarına aşina olun'da](local-environment.md) dır.</span><span class="sxs-lookup"><span data-stu-id="78d22-110">A quick overview of the commands you'll use is in the [Become familiar with the development tools](local-environment.md) with links to more details.</span></span>

## <a name="explore-integer-math"></a><span data-ttu-id="78d22-111">Tamsayı matematiğini inceleme</span><span class="sxs-lookup"><span data-stu-id="78d22-111">Explore integer math</span></span>

<span data-ttu-id="78d22-112">*Numbers-quickstart*adlı bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="78d22-112">Create a directory named *numbers-quickstart*.</span></span> <span data-ttu-id="78d22-113">Geçerli dizinini yapın ve aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="78d22-113">Make that the current directory and run the following command:</span></span>

```dotnetcli
dotnet new console -n NumbersInCSharp -o .
```

<span data-ttu-id="78d22-114">En sevdiğiniz düzenleyicide *Program.cs* açın `Console.WriteLine("Hello World!");` ve satırı aşağıdakilerle değiştirin:</span><span class="sxs-lookup"><span data-stu-id="78d22-114">Open *Program.cs* in your favorite editor, and replace the line `Console.WriteLine("Hello World!");` with the following:</span></span>

```csharp
int a = 18;
int b = 6;
int c = a + b;
Console.WriteLine(c);
```

<span data-ttu-id="78d22-115">Komut pencerenize `dotnet run` yazarak bu kodu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="78d22-115">Run this code by typing `dotnet run` in your command window.</span></span>

<span data-ttu-id="78d22-116">Az önce tamsayılarla gerçekleştirilen temel matematik işlemlerinden birini gördünüz.</span><span class="sxs-lookup"><span data-stu-id="78d22-116">You've just seen one of the fundamental math operations with integers.</span></span> <span data-ttu-id="78d22-117">Tür, `int` sıfır, pozitif veya negatif tam sayı olan bir **tamsayıyı**temsil eder.</span><span class="sxs-lookup"><span data-stu-id="78d22-117">The `int` type represents an **integer**, a zero, positive, or negative whole number.</span></span> <span data-ttu-id="78d22-118">Toplama için `+` sembolünü kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="78d22-118">You use the `+` symbol for addition.</span></span> <span data-ttu-id="78d22-119">Tamsayılar için sıklıkla kullanılan diğer matematiksel işlemler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="78d22-119">Other common mathematical operations for integers include:</span></span>

- <span data-ttu-id="78d22-120">çıkarma için `-`</span><span class="sxs-lookup"><span data-stu-id="78d22-120">`-` for subtraction</span></span>
- <span data-ttu-id="78d22-121">çarpma için `*`</span><span class="sxs-lookup"><span data-stu-id="78d22-121">`*` for multiplication</span></span>
- <span data-ttu-id="78d22-122">bölme için `/`</span><span class="sxs-lookup"><span data-stu-id="78d22-122">`/` for division</span></span>

<span data-ttu-id="78d22-123">Bu farklı işlemleri keşfederek başlayın.</span><span class="sxs-lookup"><span data-stu-id="78d22-123">Start by exploring those different operations.</span></span> <span data-ttu-id="78d22-124">Değerini yazan satırdan sonra bu `c`satırları ekleyin:</span><span class="sxs-lookup"><span data-stu-id="78d22-124">Add these lines after the line that writes the value of `c`:</span></span>

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

<span data-ttu-id="78d22-125">Komut pencerenize `dotnet run` yazarak bu kodu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="78d22-125">Run this code by typing `dotnet run` in your command window.</span></span>

<span data-ttu-id="78d22-126">Ayrıca dilerseniz aynı satırda birden çok matematik işlemi gerçekleştirerek de deneme yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="78d22-126">You can also experiment by performing multiple mathematics operations in the same line, if you'd like.</span></span> <span data-ttu-id="78d22-127">Örneğin `c = a + b - 12 * 17;` deneyin.</span><span class="sxs-lookup"><span data-stu-id="78d22-127">Try `c = a + b - 12 * 17;` for example.</span></span> <span data-ttu-id="78d22-128">Değişkenleri ve sabit sayıları karıştırmaya izin verilir.</span><span class="sxs-lookup"><span data-stu-id="78d22-128">Mixing variables and constant numbers is allowed.</span></span>

> [!TIP]
> <span data-ttu-id="78d22-129">C# dilini (veya herhangi bir programlama dilini) keşfederken, kod yazdığınızda hatalar yapacaksınız.</span><span class="sxs-lookup"><span data-stu-id="78d22-129">As you explore C# (or any programming language), you'll make mistakes when you write code.</span></span> <span data-ttu-id="78d22-130">**Derleyici** bu hataları bulup size bildirir.</span><span class="sxs-lookup"><span data-stu-id="78d22-130">The **compiler** will find those errors and report them to you.</span></span> <span data-ttu-id="78d22-131">Çıktı hata iletileri içeriyorsa, neyi düzelteceğimize bakmak için örnek koduna ve pencerenizdeki koda yakından bakın.</span><span class="sxs-lookup"><span data-stu-id="78d22-131">When the output contains error messages, look closely at the example code and the code in your window to see what to fix.</span></span>
> <span data-ttu-id="78d22-132">Bu alıştırma, C# kodunun yapısını öğrenmenize yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="78d22-132">That exercise will help you learn the structure of C# code.</span></span>

<span data-ttu-id="78d22-133">İlk adımı bitirdin.</span><span class="sxs-lookup"><span data-stu-id="78d22-133">You've finished the first step.</span></span> <span data-ttu-id="78d22-134">Bir sonraki bölümü başlatmadan önce, geçerli kodu ayrı bir yönteme taşıyalım.</span><span class="sxs-lookup"><span data-stu-id="78d22-134">Before you start the next section, let's move the current code into a separate method.</span></span> <span data-ttu-id="78d22-135">Bu, yeni bir örnekle çalışmaya başlamayı kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="78d22-135">That makes it easier to start working with a new example.</span></span> <span data-ttu-id="78d22-136">Metodunuzu `WorkingWithIntegers` yeniden adlandırın `Main` `Main` ve `WorkingWithIntegers`çağıran yeni bir yöntem yazın.</span><span class="sxs-lookup"><span data-stu-id="78d22-136">Rename your `Main` method to `WorkingWithIntegers` and write a new `Main` method that calls `WorkingWithIntegers`.</span></span> <span data-ttu-id="78d22-137">Bitirdiğinizde, kodunuz şu şekilde görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="78d22-137">When you finish, your code should look like this:</span></span>

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

## <a name="explore-order-of-operations"></a><span data-ttu-id="78d22-138">İşlem sırasını inceleme</span><span class="sxs-lookup"><span data-stu-id="78d22-138">Explore order of operations</span></span>

<span data-ttu-id="78d22-139">Çağrıyı yorumla. `WorkingWithIntegers()`</span><span class="sxs-lookup"><span data-stu-id="78d22-139">Comment out the call to `WorkingWithIntegers()`.</span></span> <span data-ttu-id="78d22-140">Bu bölümde çalışırken çıktıdaha az darmadağın yapacaktır:</span><span class="sxs-lookup"><span data-stu-id="78d22-140">It will make the output less cluttered as you work in this section:</span></span>

```csharp
//WorkingWithIntegers();
```

<span data-ttu-id="78d22-141">C#'da `//` bir **yorum** başlar.</span><span class="sxs-lookup"><span data-stu-id="78d22-141">The `//` starts a **comment** in C#.</span></span> <span data-ttu-id="78d22-142">Yorumlar, kaynak kodunuzda tutmak istediğiniz ancak kod olarak yürütülmemek istemediğiniz herhangi bir metindir.</span><span class="sxs-lookup"><span data-stu-id="78d22-142">Comments are any text you want to keep in your source code but not execute as code.</span></span> <span data-ttu-id="78d22-143">Derleyici yorumlardan yürütülebilir bir kod oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="78d22-143">The compiler does not generate any executable code from comments.</span></span>

<span data-ttu-id="78d22-144">C# dili, farklı matematik işlemlerinin önceliğini matematikte öğrendiğiniz kurallarla tutarlı bir şekilde tanımlar.</span><span class="sxs-lookup"><span data-stu-id="78d22-144">The C# language defines the precedence of different mathematics operations with rules consistent with the rules you learned in mathematics.</span></span>
<span data-ttu-id="78d22-145">Çarpma ve bölme işlemleri, toplama ve çıkarma işlemlerinden önce gelir.</span><span class="sxs-lookup"><span data-stu-id="78d22-145">Multiplication and division take precedence over addition and subtraction.</span></span>
<span data-ttu-id="78d22-146">Yönteminize `Main` aşağıdaki kodu ekleyerek ve aşağıdakileri `dotnet run`gerçekleştirerek bunu keşfedin:</span><span class="sxs-lookup"><span data-stu-id="78d22-146">Explore that by adding the following code to your `Main` method, and executing `dotnet run`:</span></span>

```csharp
int a = 5;
int b = 4;
int c = 2;
int d = a + b * c;
Console.WriteLine(d);
 ```

<span data-ttu-id="78d22-147">Çıkış, çarpma işleminin toplama işleminden önce gerçekleştiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="78d22-147">The output demonstrates that the multiplication is performed before the addition.</span></span>

<span data-ttu-id="78d22-148">Önce yapılmasını istediğiniz işlem veya işlemlerin etrafına parantez ekleyerek farklı bir işlem sırası zorlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="78d22-148">You can force a different order of operation by adding parentheses around the operation or operations you want performed first.</span></span> <span data-ttu-id="78d22-149">Aşağıdaki satırları ekleyin ve yeniden çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="78d22-149">Add the following lines and run again:</span></span>

```csharp
d = (a + b) * c;
Console.WriteLine(d);
```

<span data-ttu-id="78d22-150">Birçok farklı işlemi birleştirerek daha fazlasını keşfedin.</span><span class="sxs-lookup"><span data-stu-id="78d22-150">Explore more by combining many different operations.</span></span> <span data-ttu-id="78d22-151">Yönteminizin `Main` altındaki aşağıdaki satırları gibi bir şey ekleyin.</span><span class="sxs-lookup"><span data-stu-id="78d22-151">Add something like the following lines at the bottom of your `Main` method.</span></span> <span data-ttu-id="78d22-152">`dotnet run` komutunu yeniden deneyin.</span><span class="sxs-lookup"><span data-stu-id="78d22-152">Try `dotnet run` again.</span></span>

```csharp
d = (a + b) - 6 * c + (12 * 4) / 3 + 12;
Console.WriteLine(d);
```

<span data-ttu-id="78d22-153">Tamsayılar için farklı bir davranışla karşılaşmış olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="78d22-153">You may have noticed an interesting behavior for integers.</span></span> <span data-ttu-id="78d22-154">Sonucun ondalık veya kesir bölümü içermesini bekliyor olsanız da tamsayı bölme işlemi her zaman tamsayı sonucu verir.</span><span class="sxs-lookup"><span data-stu-id="78d22-154">Integer division always produces an integer result, even when you'd expect the result to include a decimal or fractional portion.</span></span>

<span data-ttu-id="78d22-155">Bu davranışı görmediyseniz, yönteminizin `Main` sonunda aşağıdaki kodu deneyin:</span><span class="sxs-lookup"><span data-stu-id="78d22-155">If you haven't seen this behavior, try the following code at the end of your `Main` method:</span></span>

```csharp
int e = 7;
int f = 4;
int g = 3;
int h = (e + f) / g;
Console.WriteLine(h);
```

<span data-ttu-id="78d22-156">Sonuçları `dotnet run` görmek için yeniden yazın.</span><span class="sxs-lookup"><span data-stu-id="78d22-156">Type `dotnet run` again to see the results.</span></span>

<span data-ttu-id="78d22-157">Devam etmeden önce, bu bölümde yazdığınız tüm kodları alıp yeni bir yönteme koyalım.</span><span class="sxs-lookup"><span data-stu-id="78d22-157">Before moving on, let's take all the code you've written in this section and put it in a new method.</span></span> <span data-ttu-id="78d22-158">Buna yeni `OrderPrecedence`bir yöntem deyin.</span><span class="sxs-lookup"><span data-stu-id="78d22-158">Call that new method `OrderPrecedence`.</span></span>
<span data-ttu-id="78d22-159">Böyle bir şeyle bitirmelisin:</span><span class="sxs-lookup"><span data-stu-id="78d22-159">You should end up with something like this:</span></span>

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

## <a name="explore-integer-precision-and-limits"></a><span data-ttu-id="78d22-160">Tamsayı duyarlığını ve sınırlarını inceleme</span><span class="sxs-lookup"><span data-stu-id="78d22-160">Explore integer precision and limits</span></span>

<span data-ttu-id="78d22-161">Son örnek, tamsayı bölme işleminin sonucu kestiğini size göstermiştir.</span><span class="sxs-lookup"><span data-stu-id="78d22-161">That last sample showed you that integer division truncates the result.</span></span>
<span data-ttu-id="78d22-162">Geri **kalanını** **modulo** işleci, `%` karakter kullanarak alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="78d22-162">You can get the **remainder** by using the **modulo** operator, the `%` character.</span></span> <span data-ttu-id="78d22-163">Yönteminizde `Main` aşağıdaki kodu deneyin:</span><span class="sxs-lookup"><span data-stu-id="78d22-163">Try the following code in your `Main` method:</span></span>

```csharp
int a = 7;
int b = 4;
int c = 3;
int d = (a + b) / c;
int e = (a + b) % c;
Console.WriteLine($"quotient: {d}");
Console.WriteLine($"remainder: {e}");
```

<span data-ttu-id="78d22-164">C# tamsayı türü diğer bir özelliğiyle matematiksel tamsayılardan farklıdır: `int` türünün alt ve üst sınırları vardır.</span><span class="sxs-lookup"><span data-stu-id="78d22-164">The C# integer type differs from mathematical integers in one other way: the `int` type has minimum and maximum limits.</span></span> <span data-ttu-id="78d22-165">Bu sınırları görmek `Main` için bu kodu yönteminize ekleyin:</span><span class="sxs-lookup"><span data-stu-id="78d22-165">Add this code to your `Main` method to see those limits:</span></span>

```csharp
int max = int.MaxValue;
int min = int.MinValue;
Console.WriteLine($"The range of integers is {min} to {max}");
```

<span data-ttu-id="78d22-166">Bir hesaplama, bu sınırları aşan bir değer veriyorsa bu, **aşağı taşma** veya **taşma** koşulunuzun olduğu anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="78d22-166">If a calculation produces a value that exceeds those limits, you have an **underflow** or **overflow** condition.</span></span> <span data-ttu-id="78d22-167">Yanıtın bir sınırdan diğerine kaydığı görülüyor.</span><span class="sxs-lookup"><span data-stu-id="78d22-167">The answer appears to wrap from one limit to the other.</span></span> <span data-ttu-id="78d22-168">Bir örnek görmek `Main` için yönteminize bu iki satırı ekleyin:</span><span class="sxs-lookup"><span data-stu-id="78d22-168">Add these two lines to your `Main` method to see an example:</span></span>

```csharp
int what = max + 3;
Console.WriteLine($"An example of overflow: {what}");
```

<span data-ttu-id="78d22-169">Yanıtın tam sayı alt sınırına (negatif) oldukça yakın olduğuna dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="78d22-169">Notice that the answer is very close to the minimum (negative) integer.</span></span> <span data-ttu-id="78d22-170">Bu, `min + 2` ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="78d22-170">It's the same as `min + 2`.</span></span>
<span data-ttu-id="78d22-171">Toplama işlemi, tamsayılar için izin verilen değerleri **aşmıştır**.</span><span class="sxs-lookup"><span data-stu-id="78d22-171">The addition operation **overflowed** the allowed values for integers.</span></span>
<span data-ttu-id="78d22-172">Taşma durumu en büyük olası tamsayı değerinden en küçük olana "kaydığından" yanıt oldukça büyük bir negatif sayıdır.</span><span class="sxs-lookup"><span data-stu-id="78d22-172">The answer is a very large negative number because an overflow "wraps around" from the largest possible integer value to the smallest.</span></span>

<span data-ttu-id="78d22-173">`int` türü, gereksinimlerinizi karşılamadığında kullanabileceğiniz farklı sınırlar ve duyarlık içeren başka sayısal türler de mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="78d22-173">There are other numeric types with different limits and precision that you would use when the `int` type doesn't meet your needs.</span></span> <span data-ttu-id="78d22-174">Bir sonraki adımda bunları inceleyelim.</span><span class="sxs-lookup"><span data-stu-id="78d22-174">Let's explore those next.</span></span>

<span data-ttu-id="78d22-175">Bir kez daha, bu bölümde yazdığınız kodu ayrı bir yönteme taşıyalım.</span><span class="sxs-lookup"><span data-stu-id="78d22-175">Once again, let's move the code you wrote in this section into a separate method.</span></span> <span data-ttu-id="78d22-176">Bunu, `TestLimits` olarak adlandırın.</span><span class="sxs-lookup"><span data-stu-id="78d22-176">Name it `TestLimits`.</span></span>

## <a name="work-with-the-double-type"></a><span data-ttu-id="78d22-177">Çift tür ile çalışma</span><span class="sxs-lookup"><span data-stu-id="78d22-177">Work with the double type</span></span>

<span data-ttu-id="78d22-178">`double` sayısal türü, çift duyarlıklı kayan noktalı bir sayıyı ifade eder.</span><span class="sxs-lookup"><span data-stu-id="78d22-178">The `double` numeric type represents a double-precision floating point number.</span></span> <span data-ttu-id="78d22-179">Bu terimler sizin için yeni olabilir.</span><span class="sxs-lookup"><span data-stu-id="78d22-179">Those terms may be new to you.</span></span> <span data-ttu-id="78d22-180">**Kayan noktalı** sayı, büyüklük açısından oldukça büyük veya küçük olabilen, tamsayı olmayan değerleri ifade etmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="78d22-180">A **floating point** number is useful to represent non-integral numbers that may be very large or small in magnitude.</span></span> <span data-ttu-id="78d22-181">**Çift duyarlıklı**, bu sayıların **tek duyarlıktan** daha fazla duyarlık kullanılarak depolandığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="78d22-181">**Double-precision** means that these numbers are stored using greater precision than **single-precision**.</span></span> <span data-ttu-id="78d22-182">Modern bilgisayarlarda çift duyarlıklı sayı kullanımı, tek duyarlıklı sayılara göre daha yaygındır.</span><span class="sxs-lookup"><span data-stu-id="78d22-182">On modern computers, it is more common to use double precision than single precision numbers.</span></span>
<span data-ttu-id="78d22-183">İnceleyelim mi?</span><span class="sxs-lookup"><span data-stu-id="78d22-183">Let's explore.</span></span> <span data-ttu-id="78d22-184">Aşağıdaki kodu ekleyin ve sonucu görün:</span><span class="sxs-lookup"><span data-stu-id="78d22-184">Add the following code and see the result:</span></span>

```csharp
double a = 5;
double b = 4;
double c = 2;
double d = (a + b) / c;
Console.WriteLine(d);
```

<span data-ttu-id="78d22-185">Yanıtın, bölümün ondalık kısmını içerdiğine dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="78d22-185">Notice that the answer includes the decimal portion of the quotient.</span></span> <span data-ttu-id="78d22-186">Çift değerlerle biraz daha karmaşık bir ifadeyi deneyin:</span><span class="sxs-lookup"><span data-stu-id="78d22-186">Try a slightly more complicated expression with doubles:</span></span>

```csharp
double e = 19;
double f = 23;
double g = 8;
double h = (e + f) / g;
Console.WriteLine(h);
```

<span data-ttu-id="78d22-187">Çift değerin aralığı, tamsayı değerlerinden çok daha büyüktür.</span><span class="sxs-lookup"><span data-stu-id="78d22-187">The range of a double value is much greater than integer values.</span></span> <span data-ttu-id="78d22-188">Şimdiye kadar yazdıkların aşağıdaki kodu deneyin:</span><span class="sxs-lookup"><span data-stu-id="78d22-188">Try the following code below what you've written so far:</span></span>

```csharp
double max = double.MaxValue;
double min = double.MinValue;
Console.WriteLine($"The range of double is {min} to {max}");
```

<span data-ttu-id="78d22-189">Bu değerler bilimsel gösterimde yazdırılır.</span><span class="sxs-lookup"><span data-stu-id="78d22-189">These values are printed out in scientific notation.</span></span> <span data-ttu-id="78d22-190">`E` değerinin sol tarafındaki sayı katsayıdır.</span><span class="sxs-lookup"><span data-stu-id="78d22-190">The number to the left of the `E` is the significand.</span></span> <span data-ttu-id="78d22-191">Sağ taraftaki sayı 10’un bir kuvveti olarak üstür.</span><span class="sxs-lookup"><span data-stu-id="78d22-191">The number to the right is the exponent, as a power of 10.</span></span>

<span data-ttu-id="78d22-192">Matematikteki ondalık sayılar gibi C# dilindeki çift değerlerde de yuvarlama hataları olabilir.</span><span class="sxs-lookup"><span data-stu-id="78d22-192">Just like decimal numbers in math, doubles in C# can have rounding errors.</span></span> <span data-ttu-id="78d22-193">Şu kodu deneyin:</span><span class="sxs-lookup"><span data-stu-id="78d22-193">Try this code:</span></span>

```csharp
double third = 1.0 / 3.0;
Console.WriteLine(third);
```

<span data-ttu-id="78d22-194">`0.3` yinelemesinin `1/3` ile tam olarak aynı olmadığını fark edersiniz.</span><span class="sxs-lookup"><span data-stu-id="78d22-194">You know that `0.3` repeating is not exactly the same as `1/3`.</span></span>

<span data-ttu-id="78d22-195">***Sınama***</span><span class="sxs-lookup"><span data-stu-id="78d22-195">***Challenge***</span></span>

<span data-ttu-id="78d22-196">`double` türünü kullanarak büyük sayılar, küçük sayılar, çarpma işlemi ve bölme işlemi ile diğer hesaplamaları deneyin.</span><span class="sxs-lookup"><span data-stu-id="78d22-196">Try other calculations with large numbers, small numbers, multiplication and division using the `double` type.</span></span> <span data-ttu-id="78d22-197">Daha karmaşık hesaplamalar deneyin.</span><span class="sxs-lookup"><span data-stu-id="78d22-197">Try more complicated calculations.</span></span>

<span data-ttu-id="78d22-198">Meydan okumayla biraz zaman geçirdikten sonra, yazdığınız kodu alın ve yeni bir yönteme yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="78d22-198">After you've spent some time with the challenge, take the code you've written and place it in a new method.</span></span> <span data-ttu-id="78d22-199">Bu yeni `WorkWithDoubles`yöntemi adlandırın.</span><span class="sxs-lookup"><span data-stu-id="78d22-199">Name that new method `WorkWithDoubles`.</span></span>

## <a name="work-with-fixed-point-types"></a><span data-ttu-id="78d22-200">Sabit nokta türleriyle çalışma</span><span class="sxs-lookup"><span data-stu-id="78d22-200">Work with fixed point types</span></span>

<span data-ttu-id="78d22-201">C# dilinde temel sayısal türleri gördünüz: tamsayılar ve çiftler.</span><span class="sxs-lookup"><span data-stu-id="78d22-201">You've seen the basic numeric types in C#: integers and doubles.</span></span>  <span data-ttu-id="78d22-202">Öğrenmeniz gereken bir tür daha vardır: `decimal` türü.</span><span class="sxs-lookup"><span data-stu-id="78d22-202">There is one other type to learn: the `decimal` type.</span></span> <span data-ttu-id="78d22-203">`decimal` türü, `double` türünden daha küçük bir aralığa ancak daha fazla duyarlığa sahiptir.</span><span class="sxs-lookup"><span data-stu-id="78d22-203">The `decimal` type has a smaller range but greater precision than `double`.</span></span> <span data-ttu-id="78d22-204">**Sabit nokta** terimi, ondalık ayırıcının (veya ikili noktasının) hareket etmediği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="78d22-204">The term **fixed point** means that the decimal point (or binary point) doesn't move.</span></span> <span data-ttu-id="78d22-205">Şimdi buna bir göz atalım:</span><span class="sxs-lookup"><span data-stu-id="78d22-205">Let's take a look:</span></span>

```csharp
decimal min = decimal.MinValue;
decimal max = decimal.MaxValue;
Console.WriteLine($"The range of the decimal type is {min} to {max}");
```

<span data-ttu-id="78d22-206">Aralığın `double` türünden daha küçük olduğuna dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="78d22-206">Notice that the range is smaller than the `double` type.</span></span> <span data-ttu-id="78d22-207">Aşağıdaki kodu deneyerek ondalık türünde daha fazla duyarlık olduğunu görebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="78d22-207">You can see the greater precision with the decimal type by trying the following code:</span></span>

```csharp
double a = 1.0;
double b = 3.0;
Console.WriteLine(a / b);

decimal c = 1.0M;
decimal d = 3.0M;
Console.WriteLine(c / d);
```

<span data-ttu-id="78d22-208">Sayılardaki `M` sonekiyle, bir sabit sayının `decimal` türünü nasıl kullanması gerektiğini belirtirsiniz.</span><span class="sxs-lookup"><span data-stu-id="78d22-208">The `M` suffix on the numbers is how you indicate that a constant should use the `decimal` type.</span></span>

<span data-ttu-id="78d22-209">Ondalık türünün kullanıldığı matematikte, ondalık ayırıcının sağ tarafında daha fazla basamak bulunduğunu görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="78d22-209">Notice that the math using the decimal type has more digits to the right of the decimal point.</span></span>

<span data-ttu-id="78d22-210">***Sınama***</span><span class="sxs-lookup"><span data-stu-id="78d22-210">***Challenge***</span></span>

<span data-ttu-id="78d22-211">Farklı sayısal türleri gördüğünüze göre yarı çapı 2,50 santimetre olan bir dairenin alanını hesaplayan kodu yazın.</span><span class="sxs-lookup"><span data-stu-id="78d22-211">Now that you've seen the different numeric types, write code that calculates the area of a circle whose radius is 2.50 centimeters.</span></span> <span data-ttu-id="78d22-212">Bir dairenin alanının, yarı çapın karesinin PI sayısı ile çarpımından elde edildiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="78d22-212">Remember that the area of a circle is the radius squared multiplied by PI.</span></span> <span data-ttu-id="78d22-213">İpucu: .NET, PI sayısı için kullanabileceğiniz <xref:System.Math.PI?displayProperty=nameWithType> sabit değerini içerir.</span><span class="sxs-lookup"><span data-stu-id="78d22-213">One hint: .NET contains a constant for PI, <xref:System.Math.PI?displayProperty=nameWithType> that you can use for that value.</span></span>

<span data-ttu-id="78d22-214">19 ile 20 arasında bir yanıt almanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="78d22-214">You should get an answer between 19 and 20.</span></span>
<span data-ttu-id="78d22-215">[GitHub'daki bitmiş örnek koda bakarak](https://github.com/dotnet/samples/tree/master/csharp/numbers-quickstart/Program.cs#L104-L106)yanıtınızı kontrol edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="78d22-215">You can check your answer by [looking at the finished sample code on GitHub](https://github.com/dotnet/samples/tree/master/csharp/numbers-quickstart/Program.cs#L104-L106).</span></span>

<span data-ttu-id="78d22-216">Dilerseniz diğer formüllerden de deneme yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="78d22-216">Try some other formulas if you'd like.</span></span>

<span data-ttu-id="78d22-217">"C#'daki sayılar" hızlı başlangıcını tamamladınız.</span><span class="sxs-lookup"><span data-stu-id="78d22-217">You've completed the "Numbers in C#" quickstart.</span></span> <span data-ttu-id="78d22-218">Kendi geliştirme ortamınızda [Şubeler ve döngüler](branches-and-loops-local.md) ile hızlı bir şekilde başlatAbilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="78d22-218">You can continue with the [Branches and loops](branches-and-loops-local.md) quickstart in your own development environment.</span></span>

<span data-ttu-id="78d22-219">Aşağıdaki konularda C# dilinde sayılar hakkında daha fazla bilgi edinebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="78d22-219">You can learn more about numbers in C# in the following topics:</span></span>

- [<span data-ttu-id="78d22-220">Tamsayı sayısal türler</span><span class="sxs-lookup"><span data-stu-id="78d22-220">Integral numeric types</span></span>](../../language-reference/builtin-types/integral-numeric-types.md)
- [<span data-ttu-id="78d22-221">Kayan nokta sayısal türleri</span><span class="sxs-lookup"><span data-stu-id="78d22-221">Floating-point numeric types</span></span>](../../language-reference/builtin-types/floating-point-numeric-types.md)
- [<span data-ttu-id="78d22-222">Yerleşik sayısal dönüşümler</span><span class="sxs-lookup"><span data-stu-id="78d22-222">Built-in numeric conversions</span></span>](../../language-reference/builtin-types/numeric-conversions.md)
