---
title: İçindeki numaralandırır C# -giriş C# Öğreticisi
description: Bilgi C# sayısal türler, özellikler ve yöntemler keşfetmeye tarafından.
ms.date: 10/31/2017
ms.custom: mvc
ms.openlocfilehash: 65b31c29fa9662619f92efb7977577f12d23fb30
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/28/2019
ms.locfileid: "67423419"
---
# <a name="manipulate-integral-and-floating-point-numbers-in-c"></a><span data-ttu-id="3fa8c-103">İntegral ve kayan nokta numaralarını c ile düzenleme\#</span><span class="sxs-lookup"><span data-stu-id="3fa8c-103">Manipulate integral and floating point numbers in C\#</span></span>

<span data-ttu-id="3fa8c-104">Bu öğretici sayısal türlerle ilgili öğretir C# etkileşimli olarak.</span><span class="sxs-lookup"><span data-stu-id="3fa8c-104">This tutorial teaches you about the numeric types in C# interactively.</span></span> <span data-ttu-id="3fa8c-105">Az miktarda kod yazacaksınız ve ardından derleyin ve kod çalıştırması.</span><span class="sxs-lookup"><span data-stu-id="3fa8c-105">You'll write small amounts of code, then you'll compile and run that code.</span></span> <span data-ttu-id="3fa8c-106">Öğreticiyi dersler ve içinde matematik işlemlerini inceleyen bir dizi içeren C#.</span><span class="sxs-lookup"><span data-stu-id="3fa8c-106">The tutorial contains a series of lessons that explore numbers and math operations in C#.</span></span> <span data-ttu-id="3fa8c-107">Bu dersler size C# dilinin temellerini öğretin.</span><span class="sxs-lookup"><span data-stu-id="3fa8c-107">These lessons teach you the fundamentals of the C# language.</span></span>

<span data-ttu-id="3fa8c-108">Bu öğretici geliştirme için kullanabileceğiniz bir makine olmasını bekliyor.</span><span class="sxs-lookup"><span data-stu-id="3fa8c-108">This tutorial expects you to have a machine you can use for development.</span></span> <span data-ttu-id="3fa8c-109">.NET konu [10 dakika içinde kullanmaya başla](https://www.microsoft.com/net/core) Mac, PC veya Linux üzerinde yerel geliştirme ortamınızı ayarlamaya yönelik yönergeler içerir.</span><span class="sxs-lookup"><span data-stu-id="3fa8c-109">The .NET topic [Get Started in 10 minutes](https://www.microsoft.com/net/core) has instructions for setting up your local development environment on Mac, PC or Linux.</span></span> <span data-ttu-id="3fa8c-110">Kullandığınız hesap komutları hızlı bir genel bakış yer [geliştirme araçları ile aşina](local-environment.md) daha ayrıntılı bilgi için bağlantılarla birlikte.</span><span class="sxs-lookup"><span data-stu-id="3fa8c-110">A quick overview of the commands you'll use is in the [Become familiar with the development tools](local-environment.md) with links to more details.</span></span>

## <a name="explore-integer-math"></a><span data-ttu-id="3fa8c-111">Tamsayı matematiğini İnceleme</span><span class="sxs-lookup"><span data-stu-id="3fa8c-111">Explore integer math</span></span>

<span data-ttu-id="3fa8c-112">Adlı bir dizin oluşturmak **numaraları-quickstart**.</span><span class="sxs-lookup"><span data-stu-id="3fa8c-112">Create a directory named **numbers-quickstart**.</span></span> <span data-ttu-id="3fa8c-113">Geçerli dizin ve çalışma olun `dotnet new console -n NumbersInCSharp -o .`.</span><span class="sxs-lookup"><span data-stu-id="3fa8c-113">Make that the current directory and run `dotnet new console -n NumbersInCSharp -o .`.</span></span>

<span data-ttu-id="3fa8c-114">Açık **Program.cs** satırı değiştirin ve tercih ettiğiniz düzenleyiciyi `Console.WriteLine("Hello World!");` aşağıdaki:</span><span class="sxs-lookup"><span data-stu-id="3fa8c-114">Open **Program.cs** in your favorite editor, and replace the line `Console.WriteLine("Hello World!");` with the following:</span></span>

```csharp
int a = 18;
int b = 6;
int c = a + b;
Console.WriteLine(c);
```

<span data-ttu-id="3fa8c-115">Bu kod yazarak çalıştırın `dotnet run` komut pencerenizde.</span><span class="sxs-lookup"><span data-stu-id="3fa8c-115">Run this code by typing `dotnet run` in your command window.</span></span>

<span data-ttu-id="3fa8c-116">Az önce tamsayılarla gerçekleştirilen temel matematik işlemlerinden birini gördünüz.</span><span class="sxs-lookup"><span data-stu-id="3fa8c-116">You've just seen one of the fundamental math operations with integers.</span></span> <span data-ttu-id="3fa8c-117">`int` Türü temsil eder bir **tamsayı**, bir pozitif veya negatif tamsayı.</span><span class="sxs-lookup"><span data-stu-id="3fa8c-117">The `int` type represents an **integer**, a positive or negative whole number.</span></span> <span data-ttu-id="3fa8c-118">Kullandığınız `+` sembol ekleme.</span><span class="sxs-lookup"><span data-stu-id="3fa8c-118">You use the `+` symbol for addition.</span></span> <span data-ttu-id="3fa8c-119">Tamsayılar için kullanılan diğer matematiksel işlemler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="3fa8c-119">Other common mathematical operations for integers include:</span></span>

- <span data-ttu-id="3fa8c-120">`-` çıkarma için</span><span class="sxs-lookup"><span data-stu-id="3fa8c-120">`-` for subtraction</span></span>
- <span data-ttu-id="3fa8c-121">`*` çarpma için</span><span class="sxs-lookup"><span data-stu-id="3fa8c-121">`*` for multiplication</span></span>
- <span data-ttu-id="3fa8c-122">`/` bölme için</span><span class="sxs-lookup"><span data-stu-id="3fa8c-122">`/` for division</span></span>

<span data-ttu-id="3fa8c-123">Bu farklı işlemleri keşfederek başlayın.</span><span class="sxs-lookup"><span data-stu-id="3fa8c-123">Start by exploring those different operations.</span></span> <span data-ttu-id="3fa8c-124">Değerini yazan bir satırın sonunda şu satırı ekleyin `c`:</span><span class="sxs-lookup"><span data-stu-id="3fa8c-124">Add these lines after the line that writes the value of `c`:</span></span>

```csharp
c = a - b;
Console.WriteLine(c);
c = a * b;
Console.WriteLine(c);
c = a / b;
Console.WriteLine(c);
```

<span data-ttu-id="3fa8c-125">Bu kod yazarak çalıştırın `dotnet run` komut pencerenizde.</span><span class="sxs-lookup"><span data-stu-id="3fa8c-125">Run this code by typing `dotnet run` in your command window.</span></span>

<span data-ttu-id="3fa8c-126">Dilerseniz aynı satırda birden çok matematik işlemi gerçekleştirerek de deneyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3fa8c-126">You can also experiment by performing multiple mathematics operations in the same line, if you'd like.</span></span> <span data-ttu-id="3fa8c-127">Deneyin `c = a + b - 12 * 17;` örneğin.</span><span class="sxs-lookup"><span data-stu-id="3fa8c-127">Try `c = a + b - 12 * 17;` for example.</span></span> <span data-ttu-id="3fa8c-128">Değişkenleri ve sabit sayıları karıştırılmasına izin.</span><span class="sxs-lookup"><span data-stu-id="3fa8c-128">Mixing variables and constant numbers is allowed.</span></span>

> [!TIP]
> <span data-ttu-id="3fa8c-129">C# (veya herhangi bir programlama dilini) keşfederken, kod yazdığınızda hatalar yapacaksınız.</span><span class="sxs-lookup"><span data-stu-id="3fa8c-129">As you explore C# (or any programming language), you'll make mistakes when you write code.</span></span> <span data-ttu-id="3fa8c-130">**Derleyici** bu hataları bulup size bildirir.</span><span class="sxs-lookup"><span data-stu-id="3fa8c-130">The **compiler** will find those errors and report them to you.</span></span> <span data-ttu-id="3fa8c-131">Çıktı, hata iletileri içerdiğinde, örnek kod ve kodda neyin düzeltilmesi gerektiğini görmek için pencerenizi yakından bakın.</span><span class="sxs-lookup"><span data-stu-id="3fa8c-131">When the output contains error messages, look closely at the example code and the code in your window to see what to fix.</span></span>
> <span data-ttu-id="3fa8c-132">Bu alıştırma, C# kodunun yapısını öğrenmenize yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="3fa8c-132">That exercise will help you learn the structure of C# code.</span></span>

<span data-ttu-id="3fa8c-133">İlk adımı tamamladınız.</span><span class="sxs-lookup"><span data-stu-id="3fa8c-133">You've finished the first step.</span></span> <span data-ttu-id="3fa8c-134">Sonraki bölümde başlamadan önce geçerli kodu ayrı bir yöntem geçelim.</span><span class="sxs-lookup"><span data-stu-id="3fa8c-134">Before you start the next section, let's move the current code into a separate method.</span></span> <span data-ttu-id="3fa8c-135">Bu, yeni bir örnek ile çalışmaya başlamak kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="3fa8c-135">That makes it easier to start working with a new example.</span></span> <span data-ttu-id="3fa8c-136">Yeniden adlandırma, `Main` yönteme `WorkingWithIntegers` ve yeni bir yazma `Main` metoduna çağrı yapan `WorkingWithIntegers`.</span><span class="sxs-lookup"><span data-stu-id="3fa8c-136">Rename your `Main` method to `WorkingWithIntegers` and write a new `Main` method that calls `WorkingWithIntegers`.</span></span> <span data-ttu-id="3fa8c-137">İşiniz bittiğinde, kodunuzun şu şekilde görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="3fa8c-137">When you have finished, your code should look like this:</span></span>

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
            int c = a + b;
            Console.WriteLine(c);
            c = a - b;
            Console.WriteLine(c);
            c = a * b;
            Console.WriteLine(c);
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

## <a name="explore-order-of-operations"></a><span data-ttu-id="3fa8c-138">İşlem sırasını İnceleme</span><span class="sxs-lookup"><span data-stu-id="3fa8c-138">Explore order of operations</span></span>

<span data-ttu-id="3fa8c-139">Çağrı yorum `WorkingWithIntegers()`.</span><span class="sxs-lookup"><span data-stu-id="3fa8c-139">Comment out the call to `WorkingWithIntegers()`.</span></span> <span data-ttu-id="3fa8c-140">Bu, bu bölümde çalışırken daha az dağınıktır çıkış yapar:</span><span class="sxs-lookup"><span data-stu-id="3fa8c-140">It will make the output less cluttered as you work in this section:</span></span>

```csharp
//WorkingWithIntegers();
```

<span data-ttu-id="3fa8c-141">`//` Başlatan bir **yorum** içinde C#.</span><span class="sxs-lookup"><span data-stu-id="3fa8c-141">The `//` starts a **comment** in C#.</span></span> <span data-ttu-id="3fa8c-142">Kaynak kodunuzu korumakla birlikte kod olarak yürütmeme istediğiniz herhangi bir metin açıklamaları bulunmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3fa8c-142">Comments are any text you want to keep in your source code but not execute as code.</span></span> <span data-ttu-id="3fa8c-143">Derleyicinin açıklamaları herhangi bir yürütülebilir kod oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="3fa8c-143">The compiler does not generate any executable code from comments.</span></span>

<span data-ttu-id="3fa8c-144">C# dil kuralları Matematikte öğrendiğiniz kurallarla tutarlı farklı matematik işlemlerinin önceliğini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3fa8c-144">The C# language defines the precedence of different mathematics operations with rules consistent with the rules you learned in mathematics.</span></span>
<span data-ttu-id="3fa8c-145">Çarpma ve bölme, toplama ve çıkarma öncelik kazanır.</span><span class="sxs-lookup"><span data-stu-id="3fa8c-145">Multiplication and division take precedence over addition and subtraction.</span></span>
<span data-ttu-id="3fa8c-146">Aşağıdaki kodu ekleyerek keşfedin, `Main` yöntemi ve yürütme `dotnet run`:</span><span class="sxs-lookup"><span data-stu-id="3fa8c-146">Explore that by adding the following code to your `Main` method, and executing `dotnet run`:</span></span>

```csharp
int a = 5;
int b = 4;
int c = 2;
int d = a + b * c;
Console.WriteLine(d);
 ```

<span data-ttu-id="3fa8c-147">Çıkış, çarpma işleminin toplama işleminden önce gerçekleştiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="3fa8c-147">The output demonstrates that the multiplication is performed before the addition.</span></span>

<span data-ttu-id="3fa8c-148">İşlemi parantez içine ekleyerek farklı bir işlem sırasını zorlayabilirsiniz veya istediğiniz operations ilk kez gerçekleştirildi.</span><span class="sxs-lookup"><span data-stu-id="3fa8c-148">You can force a different order of operation by adding parentheses around the operation or operations you want performed first.</span></span> <span data-ttu-id="3fa8c-149">Aşağıdaki satırları ekleyin ve yeniden çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="3fa8c-149">Add the following lines and run again:</span></span>

```csharp
d = (a  + b) * c;
Console.WriteLine(d);
```

<span data-ttu-id="3fa8c-150">Birçok farklı işlemi birleştirerek daha fazlasını keşfedin.</span><span class="sxs-lookup"><span data-stu-id="3fa8c-150">Explore more by combining many different operations.</span></span> <span data-ttu-id="3fa8c-151">Aşağıdaki satırları benzer bir şey alt kısmında ekleyin, `Main` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="3fa8c-151">Add something like the following lines at the bottom of your `Main` method.</span></span> <span data-ttu-id="3fa8c-152">Deneyin `dotnet run` yeniden.</span><span class="sxs-lookup"><span data-stu-id="3fa8c-152">Try `dotnet run` again.</span></span>

```csharp
d = (a + b) - 6 * c + (12 * 4) / 3 + 12;
Console.WriteLine(d);
```

<span data-ttu-id="3fa8c-153">Tamsayılar için ilgi çekici bir davranışı fark etmiş olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3fa8c-153">You may have noticed an interesting behavior for integers.</span></span> <span data-ttu-id="3fa8c-154">Sonucun ondalık veya kesir bölümü içermesini bile beklediğiniz, Tamsayı bölme her zaman tamsayı sonucu üretir.</span><span class="sxs-lookup"><span data-stu-id="3fa8c-154">Integer division always produces an integer result, even when you'd expect the result to include a decimal or fractional portion.</span></span>

<span data-ttu-id="3fa8c-155">Bu davranışı görmediyseniz sonuna aşağıdaki kodu deneyin, `Main` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="3fa8c-155">If you haven't seen this behavior, try the following code at the end of your `Main` method:</span></span>

```csharp
int e = 7;
int f = 4;
int g = 3;
int h = (e  + f) / g;
Console.WriteLine(h);
```

<span data-ttu-id="3fa8c-156">Tür `dotnet run` yeniden sonuçları görmek için.</span><span class="sxs-lookup"><span data-stu-id="3fa8c-156">Type `dotnet run` again to see the results.</span></span>

<span data-ttu-id="3fa8c-157">Devam etmeden önce bu bölümde yazılan ve yeni bir yöntemde put tüm kod ele alalım.</span><span class="sxs-lookup"><span data-stu-id="3fa8c-157">Before moving on, let's take all the code you've written in this section and put it in a new method.</span></span> <span data-ttu-id="3fa8c-158">Bu yeni bir yöntem çağrısı `OrderPrecedence`.</span><span class="sxs-lookup"><span data-stu-id="3fa8c-158">Call that new method `OrderPrecedence`.</span></span>
<span data-ttu-id="3fa8c-159">Bu gibi bir şeyle görmeniz:</span><span class="sxs-lookup"><span data-stu-id="3fa8c-159">You should end up with something like this:</span></span>

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
            int c = a + b;
            Console.WriteLine(c);
            c = a - b;
            Console.WriteLine(c);
            c = a * b;
            Console.WriteLine(c);
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

            d = (a  + b) * c;
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

## <a name="explore-integer-precision-and-limits"></a><span data-ttu-id="3fa8c-160">Tamsayı duyarlığını ve sınırlarını İnceleme</span><span class="sxs-lookup"><span data-stu-id="3fa8c-160">Explore integer precision and limits</span></span>

<span data-ttu-id="3fa8c-161">Son örnek, Tamsayı bölme sonucu kestiğini size göstermiştir.</span><span class="sxs-lookup"><span data-stu-id="3fa8c-161">That last sample showed you that integer division truncates the result.</span></span>
<span data-ttu-id="3fa8c-162">Alabileceğiniz **kalan** kullanarak **modül** işleci `%` karakter.</span><span class="sxs-lookup"><span data-stu-id="3fa8c-162">You can get the **remainder** by using the **modulo** operator, the `%` character.</span></span> <span data-ttu-id="3fa8c-163">Aşağıdaki kodu deneyin, `Main` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="3fa8c-163">Try the following code in your `Main` method:</span></span>

```csharp
int a = 7;
int b = 4;
int c = 3;
int d = (a  + b) / c;
int e = (a + b) % c;
Console.WriteLine($"quotient: {d}");
Console.WriteLine($"remainder: {e}");
```

<span data-ttu-id="3fa8c-164">C# tamsayı türü diğer bir özelliğiyle matematiksel tamsayılardan farklıdır: `int` türünün alt ve üst sınırları vardır.</span><span class="sxs-lookup"><span data-stu-id="3fa8c-164">The C# integer type differs from mathematical integers in one other way: the `int` type has minimum and maximum limits.</span></span> <span data-ttu-id="3fa8c-165">Bu kodu ekleyin, `Main` yöntemi bu sınırları görmek için:</span><span class="sxs-lookup"><span data-stu-id="3fa8c-165">Add this code to your `Main` method to see those limits:</span></span>

```csharp
int max = int.MaxValue;
int min = int.MinValue;
Console.WriteLine($"The range of integers is {min} to {max}");
```

<span data-ttu-id="3fa8c-166">Bir hesaplama, bu sınırları aşan bir değer veriyorsa, sahip olduğunuz bir **underflow** veya **taşma** koşul.</span><span class="sxs-lookup"><span data-stu-id="3fa8c-166">If a calculation produces a value that exceeds those limits, you have an **underflow** or **overflow** condition.</span></span> <span data-ttu-id="3fa8c-167">Yanıtın bir sınırdan diğerine kaydığı görünür.</span><span class="sxs-lookup"><span data-stu-id="3fa8c-167">The answer appears to wrap from one limit to the other.</span></span> <span data-ttu-id="3fa8c-168">Bu iki satırları ekleyin, `Main` yöntemi bir örnek görmek için:</span><span class="sxs-lookup"><span data-stu-id="3fa8c-168">Add these two lines to your `Main` method to see an example:</span></span>

```csharp
int what = max + 3;
Console.WriteLine($"An example of overflow: {what}");
```

<span data-ttu-id="3fa8c-169">Yanıt çok az (negatif) tamsayı yakın olduğuna dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="3fa8c-169">Notice that the answer is very close to the minimum (negative) integer.</span></span> <span data-ttu-id="3fa8c-170">Aynı olan `min + 2`.</span><span class="sxs-lookup"><span data-stu-id="3fa8c-170">It's the same as `min + 2`.</span></span>
<span data-ttu-id="3fa8c-171">Toplama işlemi **taştı** tamsayılar için izin verilen değerler.</span><span class="sxs-lookup"><span data-stu-id="3fa8c-171">The addition operation **overflowed** the allowed values for integers.</span></span>
<span data-ttu-id="3fa8c-172">Taşma "etrafında en büyük olası tamsayı değerinden en küçük kaydırıldığı" yanıt oldukça büyük negatif bir sayı olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="3fa8c-172">The answer is a very large negative number because an overflow "wraps around" from the largest possible integer value to the smallest.</span></span>

<span data-ttu-id="3fa8c-173">Farklı sınırlar ve ne zaman kullanacağınız duyarlık içeren başka sayısal türler vardır `int` türü, gereksinimlerinizi karşılamadığında.</span><span class="sxs-lookup"><span data-stu-id="3fa8c-173">There are other numeric types with different limits and precision that you would use when the `int` type doesn't meet your needs.</span></span> <span data-ttu-id="3fa8c-174">Bir sonraki adımda bunları inceleyelim.</span><span class="sxs-lookup"><span data-stu-id="3fa8c-174">Let's explore those next.</span></span>

<span data-ttu-id="3fa8c-175">Bir kez daha, bu bölümde ayrı bir yöntem içinde yazdığınız kodun geçelim.</span><span class="sxs-lookup"><span data-stu-id="3fa8c-175">Once again, let's move the code you wrote in this section into a separate method.</span></span> <span data-ttu-id="3fa8c-176">Adlandırın `TestLimits`.</span><span class="sxs-lookup"><span data-stu-id="3fa8c-176">Name it `TestLimits`.</span></span>

## <a name="work-with-the-double-type"></a><span data-ttu-id="3fa8c-177">Çift tür ile çalışma</span><span class="sxs-lookup"><span data-stu-id="3fa8c-177">Work with the double type</span></span>

<span data-ttu-id="3fa8c-178">`double` Sayısal türü temsil eder, çift duyarlıklı kayan nokta sayısı.</span><span class="sxs-lookup"><span data-stu-id="3fa8c-178">The `double` numeric type represents a double-precision floating point number.</span></span> <span data-ttu-id="3fa8c-179">Bu terimler sizin için yeni olabilir.</span><span class="sxs-lookup"><span data-stu-id="3fa8c-179">Those terms may be new to you.</span></span> <span data-ttu-id="3fa8c-180">A **kayan nokta** numarası, çok büyük ya da büyüklük açısından küçük olabilen, tamsayı olmayan değerleri temsil etmek kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="3fa8c-180">A **floating point** number is useful to represent non-integral numbers that may be very large or small in magnitude.</span></span> <span data-ttu-id="3fa8c-181">**Çift duyarlıklı** bu numaraları daha fazla duyarlık kullanılarak depolandığı anlamına gelir **tek duyarlıklı**.</span><span class="sxs-lookup"><span data-stu-id="3fa8c-181">**Double-precision** means that these numbers are stored using greater precision than **single-precision**.</span></span> <span data-ttu-id="3fa8c-182">Modern bilgisayarlarda çift duyarlıklı tek duyarlıklı sayılara kullanmak daha yaygındır.</span><span class="sxs-lookup"><span data-stu-id="3fa8c-182">On modern computers, it is more common to use double precision than single precision numbers.</span></span>
<span data-ttu-id="3fa8c-183">Haydi keşfedelim.</span><span class="sxs-lookup"><span data-stu-id="3fa8c-183">Let's explore.</span></span> <span data-ttu-id="3fa8c-184">Aşağıdaki kodu ekleyin ve sonuca bakın:</span><span class="sxs-lookup"><span data-stu-id="3fa8c-184">Add the following code and see the result:</span></span>

```csharp
double a = 5;
double b = 4;
double c = 2;
double d = (a  + b) / c;
Console.WriteLine(d);
```

<span data-ttu-id="3fa8c-185">Yanıt sayının ondalık kısmını içerdiğine dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="3fa8c-185">Notice that the answer includes the decimal portion of the quotient.</span></span> <span data-ttu-id="3fa8c-186">Çift değerlerle biraz daha karmaşık bir ifadeyi deneyin:</span><span class="sxs-lookup"><span data-stu-id="3fa8c-186">Try a slightly more complicated expression with doubles:</span></span>

```csharp
double e = 19;
double f = 23;
double g = 8;
double h = (e  + f) / g;
Console.WriteLine(h);
```

<span data-ttu-id="3fa8c-187">Çift değerin aralığı, tamsayı değerlerinden çok büyük.</span><span class="sxs-lookup"><span data-stu-id="3fa8c-187">The range of a double value is much greater than integer values.</span></span> <span data-ttu-id="3fa8c-188">Şu ana kadar yazdıklarınızı altına aşağıdaki kodu deneyin:</span><span class="sxs-lookup"><span data-stu-id="3fa8c-188">Try the following code below what you've written so far:</span></span>

```csharp
double max = double.MaxValue;
double min = double.MinValue;
Console.WriteLine($"The range of double is {min} to {max}");
```

<span data-ttu-id="3fa8c-189">Bu değerler bilimsel gösterimde yazdırılır.</span><span class="sxs-lookup"><span data-stu-id="3fa8c-189">These values are printed out in scientific notation.</span></span> <span data-ttu-id="3fa8c-190">Sol tarafındaki sayı `E` katsayıdır.</span><span class="sxs-lookup"><span data-stu-id="3fa8c-190">The number to the left of the `E` is the significand.</span></span> <span data-ttu-id="3fa8c-191">Sağ taraftaki sayı, 10 'un bir kuvveti üstür.</span><span class="sxs-lookup"><span data-stu-id="3fa8c-191">The number to the right is the exponent, as a power of 10.</span></span>

<span data-ttu-id="3fa8c-192">Yalnızca ondalık sayılar gibi C# double yuvarlama hataları olabilir.</span><span class="sxs-lookup"><span data-stu-id="3fa8c-192">Just like decimal numbers in math, doubles in C# can have rounding errors.</span></span> <span data-ttu-id="3fa8c-193">Bu kodu deneyin:</span><span class="sxs-lookup"><span data-stu-id="3fa8c-193">Try this code:</span></span>

```csharp
double third = 1.0 / 3.0;
Console.WriteLine(third);
```

<span data-ttu-id="3fa8c-194">Bildiğiniz `0.3` yinelenen tam olarak aynı olup `1/3`.</span><span class="sxs-lookup"><span data-stu-id="3fa8c-194">You know that `0.3` repeating is not exactly the same as `1/3`.</span></span>

<span data-ttu-id="3fa8c-195">***Sınama***</span><span class="sxs-lookup"><span data-stu-id="3fa8c-195">***Challenge***</span></span>

<span data-ttu-id="3fa8c-196">Büyük sayılar, küçük sayılar, çarpma ve bölme kullanarak ile diğer hesaplamaları deneyin `double` türü.</span><span class="sxs-lookup"><span data-stu-id="3fa8c-196">Try other calculations with large numbers, small numbers, multiplication and division using the `double` type.</span></span>  <span data-ttu-id="3fa8c-197">Daha karmaşık hesaplamalar deneyin.</span><span class="sxs-lookup"><span data-stu-id="3fa8c-197">Try more complicated calculations.</span></span>

<span data-ttu-id="3fa8c-198">Çok süre çalışmış olduğunuz sonra kodu yazdıktan ve yeni bir yöntemde yerleştirin yararlanın.</span><span class="sxs-lookup"><span data-stu-id="3fa8c-198">After you've spent some time with the challenge, take the code you've written and place it in a new method.</span></span> <span data-ttu-id="3fa8c-199">Bu yeni bir yöntem adı `WorkWithDoubles`.</span><span class="sxs-lookup"><span data-stu-id="3fa8c-199">Name that new method `WorkWithDoubles`.</span></span>

## <a name="work-with-fixed-point-types"></a><span data-ttu-id="3fa8c-200">Sabit nokta türleriyle çalışma</span><span class="sxs-lookup"><span data-stu-id="3fa8c-200">Work with fixed point types</span></span>

<span data-ttu-id="3fa8c-201">C# dilinde temel sayısal türleri gördünüz: tamsayılar ve çiftler.</span><span class="sxs-lookup"><span data-stu-id="3fa8c-201">You've seen the basic numeric types in C#: integers and doubles.</span></span>  <span data-ttu-id="3fa8c-202">Bilgi edinmek için bir türü vardır: `decimal` türü.</span><span class="sxs-lookup"><span data-stu-id="3fa8c-202">There is one other type to learn: the `decimal` type.</span></span> <span data-ttu-id="3fa8c-203">`decimal` Türünde daha küçük bir aralığa ancak daha fazla duyarlığa `double`.</span><span class="sxs-lookup"><span data-stu-id="3fa8c-203">The `decimal` type has a smaller range but greater precision than `double`.</span></span> <span data-ttu-id="3fa8c-204">Terim **sabit nokta** Ondalık ayırıcının (veya ikili noktasının) hareket etmediği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="3fa8c-204">The term **fixed point** means that the decimal point (or binary point) doesn't move.</span></span> <span data-ttu-id="3fa8c-205">Bir göz atalım:</span><span class="sxs-lookup"><span data-stu-id="3fa8c-205">Let's take a look:</span></span>

```csharp
decimal min = decimal.MinValue;
decimal max = decimal.MaxValue;
Console.WriteLine($"The range of the decimal type is {min} to {max}");
```

<span data-ttu-id="3fa8c-206">Aralık değerinden küçük olduğunu fark `double` türü.</span><span class="sxs-lookup"><span data-stu-id="3fa8c-206">Notice that the range is smaller than the `double` type.</span></span> <span data-ttu-id="3fa8c-207">Aşağıdaki kodu deneyerek ondalık türünde daha fazla duyarlık görebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="3fa8c-207">You can see the greater precision with the decimal type by trying the following code:</span></span>

```csharp
double a = 1.0;
double b = 3.0;
Console.WriteLine(a / b);

decimal c = 1.0M;
decimal d = 3.0M;
Console.WriteLine(c / d);
```

<span data-ttu-id="3fa8c-208">`M` Numaralarda sonekidir nasıl bir sabit kullanması gerektiğini belirten `decimal` türü.</span><span class="sxs-lookup"><span data-stu-id="3fa8c-208">The `M` suffix on the numbers is how you indicate that a constant should use the `decimal` type.</span></span>

<span data-ttu-id="3fa8c-209">Ondalık türünün kullanıldığı Matematikte, ondalık noktanın sağındaki daha fazla rakam olduğuna dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="3fa8c-209">Notice that the math using the decimal type has more digits to the right of the decimal point.</span></span>

<span data-ttu-id="3fa8c-210">***Sınama***</span><span class="sxs-lookup"><span data-stu-id="3fa8c-210">***Challenge***</span></span>

<span data-ttu-id="3fa8c-211">Farklı sayısal türleri gördüğünüze göre çapı 2,50 santimetre olan bir dairenin alanını hesaplayan kodu yazın.</span><span class="sxs-lookup"><span data-stu-id="3fa8c-211">Now that you've seen the different numeric types, write code that calculates the area of a circle whose radius is 2.50 centimeters.</span></span> <span data-ttu-id="3fa8c-212">Unutmayın PI sayısı ile çarpılan bir dairenin alanının kare RADIUS olduğunu.</span><span class="sxs-lookup"><span data-stu-id="3fa8c-212">Remember that the area of a circle is the radius squared multiplied by PI.</span></span> <span data-ttu-id="3fa8c-213">İpucu: .NET, PI sayısı için bir sabit içeriyor <xref:System.Math.PI?displayProperty=nameWithType> , bu değer için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3fa8c-213">One hint: .NET contains a constant for PI, <xref:System.Math.PI?displayProperty=nameWithType> that you can use for that value.</span></span>

<span data-ttu-id="3fa8c-214">19 ile 20 arasında bir yanıt almanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="3fa8c-214">You should get an answer between 19 and 20.</span></span>
<span data-ttu-id="3fa8c-215">Yanıtınız tarafından denetleyebilirsiniz [tamamlanan örnek koda Github'da bakmak](https://github.com/dotnet/samples/tree/master/csharp/numbers-quickstart/Program.cs#L104-L106)</span><span class="sxs-lookup"><span data-stu-id="3fa8c-215">You can check your answer by [looking at the finished sample code on GitHub](https://github.com/dotnet/samples/tree/master/csharp/numbers-quickstart/Program.cs#L104-L106)</span></span>

<span data-ttu-id="3fa8c-216">Dilerseniz diğer formüllerden deneyin.</span><span class="sxs-lookup"><span data-stu-id="3fa8c-216">Try some other formulas if you'd like.</span></span>

<span data-ttu-id="3fa8c-217">Tamamladınız "içindeki numaralandırır C#" Hızlı Başlangıç.</span><span class="sxs-lookup"><span data-stu-id="3fa8c-217">You've completed the "Numbers in C#" quickstart.</span></span> <span data-ttu-id="3fa8c-218">İle devam edebilir [dallar ve döngüler](branches-and-loops-local.md) kendi geliştirme ortamında hızlı başlangıç.</span><span class="sxs-lookup"><span data-stu-id="3fa8c-218">You can continue with the [Branches and loops](branches-and-loops-local.md) quickstart in your own development environment.</span></span>

<span data-ttu-id="3fa8c-219">Aşağıdaki konularda C# dilinde sayılar hakkında daha fazla bilgi edinebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="3fa8c-219">You can learn more about numbers in C# in the following topics:</span></span>

- [<span data-ttu-id="3fa8c-220">Tam sayı türleri</span><span class="sxs-lookup"><span data-stu-id="3fa8c-220">Integral types</span></span>](../../language-reference/builtin-types/integral-numeric-types.md)
- [<span data-ttu-id="3fa8c-221">Kayan Nokta Türleri Tablosu</span><span class="sxs-lookup"><span data-stu-id="3fa8c-221">Floating-Point Types Table</span></span>](../../language-reference/keywords/floating-point-types-table.md)
- [<span data-ttu-id="3fa8c-222">Yerleşik Türler Tablosu</span><span class="sxs-lookup"><span data-stu-id="3fa8c-222">Built-In Types Table</span></span>](../../language-reference/keywords/built-in-types-table.md)
- [<span data-ttu-id="3fa8c-223">Örtük Sayısal Dönüştürmeler Tablosu</span><span class="sxs-lookup"><span data-stu-id="3fa8c-223">Implicit Numeric Conversions Table</span></span>](../../language-reference/keywords/implicit-numeric-conversions-table.md)
- [<span data-ttu-id="3fa8c-224">Açık Sayısal Dönüştürmeler Tablosu</span><span class="sxs-lookup"><span data-stu-id="3fa8c-224">Explicit Numeric Conversions Table</span></span>](../../language-reference/keywords/explicit-numeric-conversions-table.md)
