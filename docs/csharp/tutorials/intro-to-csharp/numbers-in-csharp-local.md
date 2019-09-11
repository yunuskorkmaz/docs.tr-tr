---
title: C# C#
description: Sayısal C# türleri, özelliklerini ve yöntemlerini inceleyerek bilgi edinin.
ms.date: 10/31/2017
ms.custom: mvc
ms.openlocfilehash: 436e8db10f973b468458987150e1312a16103b91
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850685"
---
# <a name="manipulate-integral-and-floating-point-numbers-in-c"></a><span data-ttu-id="6be6c-103">C 'de integral ve kayan nokta numaralarını işleme\#</span><span class="sxs-lookup"><span data-stu-id="6be6c-103">Manipulate integral and floating point numbers in C\#</span></span>

<span data-ttu-id="6be6c-104">Bu öğretici, size etkileşimli olarak C# sayısal türler öğretir.</span><span class="sxs-lookup"><span data-stu-id="6be6c-104">This tutorial teaches you about the numeric types in C# interactively.</span></span> <span data-ttu-id="6be6c-105">Küçük miktarlarda kod yazacaksınız, daha sonra bu kodu derleyip çalıştıracaksınız.</span><span class="sxs-lookup"><span data-stu-id="6be6c-105">You'll write small amounts of code, then you'll compile and run that code.</span></span> <span data-ttu-id="6be6c-106">Öğreticide, içindeki C#sayıları ve matematik işlemlerini keşfettiği bir dizi ders bulunur.</span><span class="sxs-lookup"><span data-stu-id="6be6c-106">The tutorial contains a series of lessons that explore numbers and math operations in C#.</span></span> <span data-ttu-id="6be6c-107">Bu dersler, C# dilin temellerini öğretir.</span><span class="sxs-lookup"><span data-stu-id="6be6c-107">These lessons teach you the fundamentals of the C# language.</span></span>

<span data-ttu-id="6be6c-108">Bu öğreticide, geliştirme için kullanabileceğiniz bir makineniz olması beklenir.</span><span class="sxs-lookup"><span data-stu-id="6be6c-108">This tutorial expects you to have a machine you can use for development.</span></span> <span data-ttu-id="6be6c-109">[10 dakika içinde Merhaba Dünya](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) .NET öğreticisi, yerel geliştirme ortamınızı Mac, PC veya Linux üzerinde ayarlamaya yönelik yönergeler içerir.</span><span class="sxs-lookup"><span data-stu-id="6be6c-109">The .NET tutorial [Hello World in 10 minutes](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) has instructions for setting up your local development environment on Mac, PC or Linux.</span></span> <span data-ttu-id="6be6c-110">Kullanacağınız komutlara hızlı bir genel bakış, daha fazla ayrıntı için bağlantılarla birlikte [geliştirme araçları hakkında bilgi sahibi olmaya gelmiştir](local-environment.md) .</span><span class="sxs-lookup"><span data-stu-id="6be6c-110">A quick overview of the commands you'll use is in the [Become familiar with the development tools](local-environment.md) with links to more details.</span></span>

## <a name="explore-integer-math"></a><span data-ttu-id="6be6c-111">Tamsayı matematiğini keşfet</span><span class="sxs-lookup"><span data-stu-id="6be6c-111">Explore integer math</span></span>

<span data-ttu-id="6be6c-112">Sayı adlı bir dizin oluşturun **-hızlı başlangıç**.</span><span class="sxs-lookup"><span data-stu-id="6be6c-112">Create a directory named **numbers-quickstart**.</span></span> <span data-ttu-id="6be6c-113">Geçerli dizini oluşturun ve çalıştırın `dotnet new console -n NumbersInCSharp -o .`.</span><span class="sxs-lookup"><span data-stu-id="6be6c-113">Make that the current directory and run `dotnet new console -n NumbersInCSharp -o .`.</span></span>

<span data-ttu-id="6be6c-114">En sevdiğiniz düzenleyicide **program.cs** açın ve satırı `Console.WriteLine("Hello World!");` aşağıdaki ile değiştirin:</span><span class="sxs-lookup"><span data-stu-id="6be6c-114">Open **Program.cs** in your favorite editor, and replace the line `Console.WriteLine("Hello World!");` with the following:</span></span>

```csharp
int a = 18;
int b = 6;
int c = a + b;
Console.WriteLine(c);
```

<span data-ttu-id="6be6c-115">Komut pencerenizi yazarak `dotnet run` bu kodu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="6be6c-115">Run this code by typing `dotnet run` in your command window.</span></span>

<span data-ttu-id="6be6c-116">Yalnızca tamsayılarla temel matematik işlemlerinden birini gördünüz.</span><span class="sxs-lookup"><span data-stu-id="6be6c-116">You've just seen one of the fundamental math operations with integers.</span></span> <span data-ttu-id="6be6c-117">Tür bir tamsayıyı, pozitif veya negatif bir tam sayıyı temsil eder. `int`</span><span class="sxs-lookup"><span data-stu-id="6be6c-117">The `int` type represents an **integer**, a positive or negative whole number.</span></span> <span data-ttu-id="6be6c-118">Eklemek için `+` simgesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="6be6c-118">You use the `+` symbol for addition.</span></span> <span data-ttu-id="6be6c-119">Tamsayılar için diğer yaygın matematik işlemleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="6be6c-119">Other common mathematical operations for integers include:</span></span>

- <span data-ttu-id="6be6c-120">`-`çıkarma için</span><span class="sxs-lookup"><span data-stu-id="6be6c-120">`-` for subtraction</span></span>
- <span data-ttu-id="6be6c-121">`*`Çarpma için</span><span class="sxs-lookup"><span data-stu-id="6be6c-121">`*` for multiplication</span></span>
- <span data-ttu-id="6be6c-122">`/`Bölüm için</span><span class="sxs-lookup"><span data-stu-id="6be6c-122">`/` for division</span></span>

<span data-ttu-id="6be6c-123">Bu farklı işlemleri inceleyerek başlayın.</span><span class="sxs-lookup"><span data-stu-id="6be6c-123">Start by exploring those different operations.</span></span> <span data-ttu-id="6be6c-124">Değerini yazan satırdan sonra bu satırları ekleyin `c`:</span><span class="sxs-lookup"><span data-stu-id="6be6c-124">Add these lines after the line that writes the value of `c`:</span></span>

```csharp
c = a - b;
Console.WriteLine(c);
c = a * b;
Console.WriteLine(c);
c = a / b;
Console.WriteLine(c);
```

<span data-ttu-id="6be6c-125">Komut pencerenizi yazarak `dotnet run` bu kodu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="6be6c-125">Run this code by typing `dotnet run` in your command window.</span></span>

<span data-ttu-id="6be6c-126">İsterseniz aynı satırda birden çok matematik işlemi gerçekleştirerek da deneyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6be6c-126">You can also experiment by performing multiple mathematics operations in the same line, if you'd like.</span></span> <span data-ttu-id="6be6c-127">Örneğin `c = a + b - 12 * 17;` , deneyin.</span><span class="sxs-lookup"><span data-stu-id="6be6c-127">Try `c = a + b - 12 * 17;` for example.</span></span> <span data-ttu-id="6be6c-128">Değişkenlerin ve sabit sayıların karıştırılmasına izin verilir.</span><span class="sxs-lookup"><span data-stu-id="6be6c-128">Mixing variables and constant numbers is allowed.</span></span>

> [!TIP]
> <span data-ttu-id="6be6c-129">Keşfederken C# (veya herhangi bir programlama dilini), kod yazarken hata oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="6be6c-129">As you explore C# (or any programming language), you'll make mistakes when you write code.</span></span> <span data-ttu-id="6be6c-130">**Derleyici** bu hataları bulacak ve size rapor eder.</span><span class="sxs-lookup"><span data-stu-id="6be6c-130">The **compiler** will find those errors and report them to you.</span></span> <span data-ttu-id="6be6c-131">Çıktı hata iletileri içerdiğinde, nelerin düzeltileceğini görmek için örnek koda ve penceredeki koda yakından bakın.</span><span class="sxs-lookup"><span data-stu-id="6be6c-131">When the output contains error messages, look closely at the example code and the code in your window to see what to fix.</span></span>
> <span data-ttu-id="6be6c-132">Bu alıştırma, C# kod yapısını öğrenmenize yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="6be6c-132">That exercise will help you learn the structure of C# code.</span></span>

<span data-ttu-id="6be6c-133">İlk adımı tamamladınız.</span><span class="sxs-lookup"><span data-stu-id="6be6c-133">You've finished the first step.</span></span> <span data-ttu-id="6be6c-134">Sonraki bölüme başlamadan önce geçerli kodu ayrı bir yönteme taşıyalim.</span><span class="sxs-lookup"><span data-stu-id="6be6c-134">Before you start the next section, let's move the current code into a separate method.</span></span> <span data-ttu-id="6be6c-135">Bu, yeni bir örnekle çalışmaya başlamasını kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="6be6c-135">That makes it easier to start working with a new example.</span></span> <span data-ttu-id="6be6c-136">Yönteminizi olarak `WorkingWithIntegers` yeniden adlandırın ve çağıran `Main` `WorkingWithIntegers`yeni bir yöntem yazın. `Main`</span><span class="sxs-lookup"><span data-stu-id="6be6c-136">Rename your `Main` method to `WorkingWithIntegers` and write a new `Main` method that calls `WorkingWithIntegers`.</span></span> <span data-ttu-id="6be6c-137">İşiniz bittiğinde kodunuzun şöyle görünmesi gerekir:</span><span class="sxs-lookup"><span data-stu-id="6be6c-137">When you have finished, your code should look like this:</span></span>

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

## <a name="explore-order-of-operations"></a><span data-ttu-id="6be6c-138">İşlem sırasını keşfet</span><span class="sxs-lookup"><span data-stu-id="6be6c-138">Explore order of operations</span></span>

<span data-ttu-id="6be6c-139">Çağrısını not edin `WorkingWithIntegers()`.</span><span class="sxs-lookup"><span data-stu-id="6be6c-139">Comment out the call to `WorkingWithIntegers()`.</span></span> <span data-ttu-id="6be6c-140">Bu bölümde çalışırken çıktının daha az karışık hale gelir:</span><span class="sxs-lookup"><span data-stu-id="6be6c-140">It will make the output less cluttered as you work in this section:</span></span>

```csharp
//WorkingWithIntegers();
```

<span data-ttu-id="6be6c-141">, `//` İçinde C#bir **yorum** başlatır.</span><span class="sxs-lookup"><span data-stu-id="6be6c-141">The `//` starts a **comment** in C#.</span></span> <span data-ttu-id="6be6c-142">Açıklamalar, kaynak kodunuzda tutmak istediğiniz tüm metinlerdir, ancak kod olarak yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="6be6c-142">Comments are any text you want to keep in your source code but not execute as code.</span></span> <span data-ttu-id="6be6c-143">Derleyici açıklamalardan herhangi bir yürütülebilir kod oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="6be6c-143">The compiler does not generate any executable code from comments.</span></span>

<span data-ttu-id="6be6c-144">C# Dil, matematiksel olarak öğrendiğiniz kurallarla tutarlı kurallara sahip farklı matematik işlemlerinin önceliğini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6be6c-144">The C# language defines the precedence of different mathematics operations with rules consistent with the rules you learned in mathematics.</span></span>
<span data-ttu-id="6be6c-145">Çarpma ve bölme, toplama ve çıkarma konusunda önceliklidir.</span><span class="sxs-lookup"><span data-stu-id="6be6c-145">Multiplication and division take precedence over addition and subtraction.</span></span>
<span data-ttu-id="6be6c-146">`Main` Yöntemine aşağıdaki kodu ekleyerek ve yürüterek `dotnet run`şunu araştırın:</span><span class="sxs-lookup"><span data-stu-id="6be6c-146">Explore that by adding the following code to your `Main` method, and executing `dotnet run`:</span></span>

```csharp
int a = 5;
int b = 4;
int c = 2;
int d = a + b * c;
Console.WriteLine(d);
 ```

<span data-ttu-id="6be6c-147">Çıktı, çarpma 'nın ekleme işleminden önce gerçekleştirildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="6be6c-147">The output demonstrates that the multiplication is performed before the addition.</span></span>

<span data-ttu-id="6be6c-148">Önce gerçekleştirilmesini istediğiniz işlemin veya işlemlerin çevresine parantez ekleyerek farklı bir işlem sırası zorlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6be6c-148">You can force a different order of operation by adding parentheses around the operation or operations you want performed first.</span></span> <span data-ttu-id="6be6c-149">Aşağıdaki satırları ekleyin ve yeniden çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="6be6c-149">Add the following lines and run again:</span></span>

```csharp
d = (a  + b) * c;
Console.WriteLine(d);
```

<span data-ttu-id="6be6c-150">Birçok farklı işlemi birleştirerek daha fazlasını keşfedebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6be6c-150">Explore more by combining many different operations.</span></span> <span data-ttu-id="6be6c-151">`Main` Yönteminizin en altında aşağıdaki satırlara benzer bir şey ekleyin.</span><span class="sxs-lookup"><span data-stu-id="6be6c-151">Add something like the following lines at the bottom of your `Main` method.</span></span> <span data-ttu-id="6be6c-152">Yeniden `dotnet run` deneyin.</span><span class="sxs-lookup"><span data-stu-id="6be6c-152">Try `dotnet run` again.</span></span>

```csharp
d = (a + b) - 6 * c + (12 * 4) / 3 + 12;
Console.WriteLine(d);
```

<span data-ttu-id="6be6c-153">Tamsayılar için ilginç bir davranış fark etmiş olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6be6c-153">You may have noticed an interesting behavior for integers.</span></span> <span data-ttu-id="6be6c-154">Sonucun ondalık veya kesir kısmını içermesini bekleseniz bile, tam sayı bölümü her zaman bir tamsayı sonucu üretir.</span><span class="sxs-lookup"><span data-stu-id="6be6c-154">Integer division always produces an integer result, even when you'd expect the result to include a decimal or fractional portion.</span></span>

<span data-ttu-id="6be6c-155">Bu davranışı görmediyseniz, `Main` yönteminizin sonunda aşağıdaki kodu deneyin:</span><span class="sxs-lookup"><span data-stu-id="6be6c-155">If you haven't seen this behavior, try the following code at the end of your `Main` method:</span></span>

```csharp
int e = 7;
int f = 4;
int g = 3;
int h = (e  + f) / g;
Console.WriteLine(h);
```

<span data-ttu-id="6be6c-156">Sonuçları `dotnet run` görmek için yeniden yazın.</span><span class="sxs-lookup"><span data-stu-id="6be6c-156">Type `dotnet run` again to see the results.</span></span>

<span data-ttu-id="6be6c-157">' In üzerine geçmeden önce, bu bölümde yazdığınız tüm kodu alıp yeni bir yönteme koyabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6be6c-157">Before moving on, let's take all the code you've written in this section and put it in a new method.</span></span> <span data-ttu-id="6be6c-158">Bu yeni yöntemi `OrderPrecedence`çağırın.</span><span class="sxs-lookup"><span data-stu-id="6be6c-158">Call that new method `OrderPrecedence`.</span></span>
<span data-ttu-id="6be6c-159">Şöyle bir işlem yapmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="6be6c-159">You should end up with something like this:</span></span>

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

## <a name="explore-integer-precision-and-limits"></a><span data-ttu-id="6be6c-160">Tamsayı hassasiyetini ve limitleri keşfet</span><span class="sxs-lookup"><span data-stu-id="6be6c-160">Explore integer precision and limits</span></span>

<span data-ttu-id="6be6c-161">Bu son örnek, bu tamsayı bölümünün sonucu ne olduğunu gösterdi.</span><span class="sxs-lookup"><span data-stu-id="6be6c-161">That last sample showed you that integer division truncates the result.</span></span>
<span data-ttu-id="6be6c-162">**Geri kalanını** , **mod** `%` işleci, karakterini kullanarak edinebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6be6c-162">You can get the **remainder** by using the **modulo** operator, the `%` character.</span></span> <span data-ttu-id="6be6c-163">Yönteyinizdeki `Main` aşağıdaki kodu deneyin:</span><span class="sxs-lookup"><span data-stu-id="6be6c-163">Try the following code in your `Main` method:</span></span>

```csharp
int a = 7;
int b = 4;
int c = 3;
int d = (a  + b) / c;
int e = (a + b) % c;
Console.WriteLine($"quotient: {d}");
Console.WriteLine($"remainder: {e}");
```

<span data-ttu-id="6be6c-164">C# Tamsayı türü matematik tamlarından farklı bir şekilde farklılık gösterir: `int` türün en az ve en fazla sınırı vardır.</span><span class="sxs-lookup"><span data-stu-id="6be6c-164">The C# integer type differs from mathematical integers in one other way: the `int` type has minimum and maximum limits.</span></span> <span data-ttu-id="6be6c-165">Bu sınırları görmek için bu `Main` kodu yönteminizin içine ekleyin:</span><span class="sxs-lookup"><span data-stu-id="6be6c-165">Add this code to your `Main` method to see those limits:</span></span>

```csharp
int max = int.MaxValue;
int min = int.MinValue;
Console.WriteLine($"The range of integers is {min} to {max}");
```

<span data-ttu-id="6be6c-166">Hesaplama bu sınırları aşan bir değer üretirse, bir **yetersiz** yer veya **taşma** koşulunuz vardır.</span><span class="sxs-lookup"><span data-stu-id="6be6c-166">If a calculation produces a value that exceeds those limits, you have an **underflow** or **overflow** condition.</span></span> <span data-ttu-id="6be6c-167">Yanıt bir sınırdan diğerine kaydırılır.</span><span class="sxs-lookup"><span data-stu-id="6be6c-167">The answer appears to wrap from one limit to the other.</span></span> <span data-ttu-id="6be6c-168">Bir örnek görmek için bu iki `Main` satırı yönteminizin içine ekleyin:</span><span class="sxs-lookup"><span data-stu-id="6be6c-168">Add these two lines to your `Main` method to see an example:</span></span>

```csharp
int what = max + 3;
Console.WriteLine($"An example of overflow: {what}");
```

<span data-ttu-id="6be6c-169">Yanıtın en düşük (negatif) tamsayıya çok yakın olduğuna dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="6be6c-169">Notice that the answer is very close to the minimum (negative) integer.</span></span> <span data-ttu-id="6be6c-170">Bu, ile `min + 2`aynıdır.</span><span class="sxs-lookup"><span data-stu-id="6be6c-170">It's the same as `min + 2`.</span></span>
<span data-ttu-id="6be6c-171">Toplama işlemi, tamsayılar için izin verilen değerleri **taşırdı** .</span><span class="sxs-lookup"><span data-stu-id="6be6c-171">The addition operation **overflowed** the allowed values for integers.</span></span>
<span data-ttu-id="6be6c-172">Bir taşma, olası en büyük tamsayı değerinden en küçüğe "kaydırdığı için, yanıt çok büyük negatif bir sayıdır.</span><span class="sxs-lookup"><span data-stu-id="6be6c-172">The answer is a very large negative number because an overflow "wraps around" from the largest possible integer value to the smallest.</span></span>

<span data-ttu-id="6be6c-173">`int` Türü gereksinimlerinizi karşılamıyorsa, farklı sınırlara ve duyarlığa sahip başka sayısal türler vardır.</span><span class="sxs-lookup"><span data-stu-id="6be6c-173">There are other numeric types with different limits and precision that you would use when the `int` type doesn't meet your needs.</span></span> <span data-ttu-id="6be6c-174">Bundan sonra bu ileri keşfedelim.</span><span class="sxs-lookup"><span data-stu-id="6be6c-174">Let's explore those next.</span></span>

<span data-ttu-id="6be6c-175">Bir kez daha, bu bölümde yazdığınız kodu ayrı bir yönteme taşıyalim.</span><span class="sxs-lookup"><span data-stu-id="6be6c-175">Once again, let's move the code you wrote in this section into a separate method.</span></span> <span data-ttu-id="6be6c-176">`TestLimits`Adlandırın.</span><span class="sxs-lookup"><span data-stu-id="6be6c-176">Name it `TestLimits`.</span></span>

## <a name="work-with-the-double-type"></a><span data-ttu-id="6be6c-177">Double türüyle çalışma</span><span class="sxs-lookup"><span data-stu-id="6be6c-177">Work with the double type</span></span>

<span data-ttu-id="6be6c-178">`double` Sayısal tür bir çift duyarlıklı kayan noktalı sayıyı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="6be6c-178">The `double` numeric type represents a double-precision floating point number.</span></span> <span data-ttu-id="6be6c-179">Bu terimler sizin için yeni olabilir.</span><span class="sxs-lookup"><span data-stu-id="6be6c-179">Those terms may be new to you.</span></span> <span data-ttu-id="6be6c-180">**Kayan noktalı** sayı, çok büyük veya küçük olabilecek tamsayı olmayan sayıları temsil etmek için kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="6be6c-180">A **floating point** number is useful to represent non-integral numbers that may be very large or small in magnitude.</span></span> <span data-ttu-id="6be6c-181">**Çift duyarlıklı** , bu sayıların **tek duyarlığa**göre daha fazla duyarlık kullanılarak depolandığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="6be6c-181">**Double-precision** means that these numbers are stored using greater precision than **single-precision**.</span></span> <span data-ttu-id="6be6c-182">Modern bilgisayarlarda, tek duyarlık sayılarıyla çift duyarlık kullanmak daha yaygındır.</span><span class="sxs-lookup"><span data-stu-id="6be6c-182">On modern computers, it is more common to use double precision than single precision numbers.</span></span>
<span data-ttu-id="6be6c-183">Keşfedelim.</span><span class="sxs-lookup"><span data-stu-id="6be6c-183">Let's explore.</span></span> <span data-ttu-id="6be6c-184">Aşağıdaki kodu ekleyin ve sonucu görüntüleyin:</span><span class="sxs-lookup"><span data-stu-id="6be6c-184">Add the following code and see the result:</span></span>

```csharp
double a = 5;
double b = 4;
double c = 2;
double d = (a  + b) / c;
Console.WriteLine(d);
```

<span data-ttu-id="6be6c-185">Yanıtın, bölümün ondalık kısmını içerdiğine dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="6be6c-185">Notice that the answer includes the decimal portion of the quotient.</span></span> <span data-ttu-id="6be6c-186">Double değerleri ile biraz daha karmaşık bir ifade deneyin:</span><span class="sxs-lookup"><span data-stu-id="6be6c-186">Try a slightly more complicated expression with doubles:</span></span>

```csharp
double e = 19;
double f = 23;
double g = 8;
double h = (e  + f) / g;
Console.WriteLine(h);
```

<span data-ttu-id="6be6c-187">Double değerinin aralığı tamsayı değerlerinden çok daha büyüktür.</span><span class="sxs-lookup"><span data-stu-id="6be6c-187">The range of a double value is much greater than integer values.</span></span> <span data-ttu-id="6be6c-188">Şu ana kadar yazdıklarınız için aşağıdaki kodu deneyin:</span><span class="sxs-lookup"><span data-stu-id="6be6c-188">Try the following code below what you've written so far:</span></span>

```csharp
double max = double.MaxValue;
double min = double.MinValue;
Console.WriteLine($"The range of double is {min} to {max}");
```

<span data-ttu-id="6be6c-189">Bu değerler bilimsel gösterimde yazdırılır.</span><span class="sxs-lookup"><span data-stu-id="6be6c-189">These values are printed out in scientific notation.</span></span> <span data-ttu-id="6be6c-190">Öğesinin solundaki sayı mantisinin ' `E` dir.</span><span class="sxs-lookup"><span data-stu-id="6be6c-190">The number to the left of the `E` is the significand.</span></span> <span data-ttu-id="6be6c-191">Sağdaki sayı, 10 ' un üssü olarak üs değeri olan sayıdır.</span><span class="sxs-lookup"><span data-stu-id="6be6c-191">The number to the right is the exponent, as a power of 10.</span></span>

<span data-ttu-id="6be6c-192">Matematiği gibi ondalık sayılar gibi, içindeki Double C# değerleri de yuvarlama hataları içerebilir.</span><span class="sxs-lookup"><span data-stu-id="6be6c-192">Just like decimal numbers in math, doubles in C# can have rounding errors.</span></span> <span data-ttu-id="6be6c-193">Şu kodu deneyin:</span><span class="sxs-lookup"><span data-stu-id="6be6c-193">Try this code:</span></span>

```csharp
double third = 1.0 / 3.0;
Console.WriteLine(third);
```

<span data-ttu-id="6be6c-194">`0.3` Tekrarda tam olarak `1/3`aynı olmadığını bilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6be6c-194">You know that `0.3` repeating is not exactly the same as `1/3`.</span></span>

<span data-ttu-id="6be6c-195">***Sına***</span><span class="sxs-lookup"><span data-stu-id="6be6c-195">***Challenge***</span></span>

<span data-ttu-id="6be6c-196">`double` Türü kullanarak büyük sayılar, küçük sayılar, çarpma ve bölme ile diğer hesaplamaları deneyin.</span><span class="sxs-lookup"><span data-stu-id="6be6c-196">Try other calculations with large numbers, small numbers, multiplication and division using the `double` type.</span></span>  <span data-ttu-id="6be6c-197">Daha karmaşık hesaplamalar deneyin.</span><span class="sxs-lookup"><span data-stu-id="6be6c-197">Try more complicated calculations.</span></span>

<span data-ttu-id="6be6c-198">Zorluğa bir süre harcadıktan sonra yazdığınız kodu alın ve yeni bir yönteme yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="6be6c-198">After you've spent some time with the challenge, take the code you've written and place it in a new method.</span></span> <span data-ttu-id="6be6c-199">Yeni yönteme `WorkWithDoubles`adlandırın.</span><span class="sxs-lookup"><span data-stu-id="6be6c-199">Name that new method `WorkWithDoubles`.</span></span>

## <a name="work-with-fixed-point-types"></a><span data-ttu-id="6be6c-200">Sabit nokta türleriyle çalışma</span><span class="sxs-lookup"><span data-stu-id="6be6c-200">Work with fixed point types</span></span>

<span data-ttu-id="6be6c-201">Temel sayısal türleri C#: tamsayılar ve Double değerleri ile gördünüz.</span><span class="sxs-lookup"><span data-stu-id="6be6c-201">You've seen the basic numeric types in C#: integers and doubles.</span></span>  <span data-ttu-id="6be6c-202">Öğreneceğinizi bir başka tür vardır: `decimal` türü.</span><span class="sxs-lookup"><span data-stu-id="6be6c-202">There is one other type to learn: the `decimal` type.</span></span> <span data-ttu-id="6be6c-203">Türün daha küçük bir aralığı, ancak daha fazla `double`duyarlık vardır. `decimal`</span><span class="sxs-lookup"><span data-stu-id="6be6c-203">The `decimal` type has a smaller range but greater precision than `double`.</span></span> <span data-ttu-id="6be6c-204">**Sabit nokta** terimi, ondalık noktanın (veya ikili noktanın) taşınmayacağı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="6be6c-204">The term **fixed point** means that the decimal point (or binary point) doesn't move.</span></span> <span data-ttu-id="6be6c-205">Bir göz atalım:</span><span class="sxs-lookup"><span data-stu-id="6be6c-205">Let's take a look:</span></span>

```csharp
decimal min = decimal.MinValue;
decimal max = decimal.MaxValue;
Console.WriteLine($"The range of the decimal type is {min} to {max}");
```

<span data-ttu-id="6be6c-206">Aralığın `double` türden küçük olduğuna dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="6be6c-206">Notice that the range is smaller than the `double` type.</span></span> <span data-ttu-id="6be6c-207">Aşağıdaki kodu deneyerek ondalık türüyle daha büyük duyarlık görebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="6be6c-207">You can see the greater precision with the decimal type by trying the following code:</span></span>

```csharp
double a = 1.0;
double b = 3.0;
Console.WriteLine(a / b);

decimal c = 1.0M;
decimal d = 3.0M;
Console.WriteLine(c / d);
```

<span data-ttu-id="6be6c-208">Sayıların son eki, bir sabitin `decimal` türü kullanması gerektiğini gösterir. `M`</span><span class="sxs-lookup"><span data-stu-id="6be6c-208">The `M` suffix on the numbers is how you indicate that a constant should use the `decimal` type.</span></span>

<span data-ttu-id="6be6c-209">Ondalık türü kullanan matematik, ondalık noktanın sağında daha fazla basamağa sahip olduğuna dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="6be6c-209">Notice that the math using the decimal type has more digits to the right of the decimal point.</span></span>

<span data-ttu-id="6be6c-210">***Sına***</span><span class="sxs-lookup"><span data-stu-id="6be6c-210">***Challenge***</span></span>

<span data-ttu-id="6be6c-211">Farklı sayısal türleri gördüğünüze göre, yarıçapı 2,50 santimetre olan bir dairenin alanını hesaplayan bir kod yazın.</span><span class="sxs-lookup"><span data-stu-id="6be6c-211">Now that you've seen the different numeric types, write code that calculates the area of a circle whose radius is 2.50 centimeters.</span></span> <span data-ttu-id="6be6c-212">Bir daire alanının, Radius ile çarpıldığı bir daire olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="6be6c-212">Remember that the area of a circle is the radius squared multiplied by PI.</span></span> <span data-ttu-id="6be6c-213">Bir ipucu: .net, <xref:System.Math.PI?displayProperty=nameWithType> bu değer için kullanabileceğiniz PI için bir sabit içerir.</span><span class="sxs-lookup"><span data-stu-id="6be6c-213">One hint: .NET contains a constant for PI, <xref:System.Math.PI?displayProperty=nameWithType> that you can use for that value.</span></span>

<span data-ttu-id="6be6c-214">19 ila 20 arasında bir yanıt almanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="6be6c-214">You should get an answer between 19 and 20.</span></span>
<span data-ttu-id="6be6c-215">[GitHub 'daki tamamlanmış örnek koda bakarak](https://github.com/dotnet/samples/tree/master/csharp/numbers-quickstart/Program.cs#L104-L106) yanıtınızı kontrol edebilirsiniz</span><span class="sxs-lookup"><span data-stu-id="6be6c-215">You can check your answer by [looking at the finished sample code on GitHub](https://github.com/dotnet/samples/tree/master/csharp/numbers-quickstart/Program.cs#L104-L106)</span></span>

<span data-ttu-id="6be6c-216">İsterseniz başka formüller de deneyin.</span><span class="sxs-lookup"><span data-stu-id="6be6c-216">Try some other formulas if you'd like.</span></span>

<span data-ttu-id="6be6c-217">"Numaraları C#" hızlı başlangıç adımlarını tamamladınız.</span><span class="sxs-lookup"><span data-stu-id="6be6c-217">You've completed the "Numbers in C#" quickstart.</span></span> <span data-ttu-id="6be6c-218">Kendi geliştirme ortamınızda [dallar ve döngüler](branches-and-loops-local.md) hızlı başlangıç ile devam edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6be6c-218">You can continue with the [Branches and loops](branches-and-loops-local.md) quickstart in your own development environment.</span></span>

<span data-ttu-id="6be6c-219">Aşağıdaki konularda, içindeki C# numaralar hakkında daha fazla bilgi edinebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="6be6c-219">You can learn more about numbers in C# in the following topics:</span></span>

- [<span data-ttu-id="6be6c-220">Integral türleri</span><span class="sxs-lookup"><span data-stu-id="6be6c-220">Integral types</span></span>](../../language-reference/builtin-types/integral-numeric-types.md)
- [<span data-ttu-id="6be6c-221">Kayan Nokta Türleri Tablosu</span><span class="sxs-lookup"><span data-stu-id="6be6c-221">Floating-Point Types Table</span></span>](../../language-reference/builtin-types/floating-point-numeric-types.md)
- [<span data-ttu-id="6be6c-222">Yerleşik Türler Tablosu</span><span class="sxs-lookup"><span data-stu-id="6be6c-222">Built-In Types Table</span></span>](../../language-reference/keywords/built-in-types-table.md)
- [<span data-ttu-id="6be6c-223">Örtük Sayısal Dönüştürmeler Tablosu</span><span class="sxs-lookup"><span data-stu-id="6be6c-223">Implicit Numeric Conversions Table</span></span>](../../language-reference/keywords/implicit-numeric-conversions-table.md)
- [<span data-ttu-id="6be6c-224">Açık Sayısal Dönüştürmeler Tablosu</span><span class="sxs-lookup"><span data-stu-id="6be6c-224">Explicit Numeric Conversions Table</span></span>](../../language-reference/keywords/explicit-numeric-conversions-table.md)
