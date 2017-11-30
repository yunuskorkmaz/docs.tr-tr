---
title: "Hızlı Başlangıç - C# numaraları - C# Kılavuzu"
description: "C# sayısal türler, özellikleri ve yöntemleri keşfetme öğrenin."
author: billwagner
ms.author: wiwagn
ms.date: 10/31/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.custom: mvc
ms.openlocfilehash: 821cca4ea6d6148410e9b179f05d5b74c4844628
ms.sourcegitcommit: 43c656811dd38a66a6672084c65d10c0cbbf2015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2017
---
# <a name="numbers-in-c-quick-start"></a><span data-ttu-id="3b471-103">C# hızlı başlangıç numaraları</span><span class="sxs-lookup"><span data-stu-id="3b471-103">Numbers in C# quick start</span></span> #

<span data-ttu-id="3b471-104">Bu hızlı başlangıç C# sayı türleri hakkında etkileşimli olarak öğretilmektedir.</span><span class="sxs-lookup"><span data-stu-id="3b471-104">This quick start teaches you about the number types in C# interactively.</span></span> <span data-ttu-id="3b471-105">Küçük miktarda kod yazacaksınız sonra derlemek ve bu kodu çalıştırmak.</span><span class="sxs-lookup"><span data-stu-id="3b471-105">You'll write small amounts of code, then you'll compile and run that code.</span></span> <span data-ttu-id="3b471-106">Hızlı Başlangıç bir dizi numaraları ve C# matematik işlemleri keşfedin dersleri içerir.</span><span class="sxs-lookup"><span data-stu-id="3b471-106">The quick start contains a series of lessons that explore numbers and math operations in C#.</span></span> <span data-ttu-id="3b471-107">Bu derslerin C# dil temelleri öğretir.</span><span class="sxs-lookup"><span data-stu-id="3b471-107">These lessons teach you the fundamentals of the C# language.</span></span>

<span data-ttu-id="3b471-108">Bu hızlı başlangıç geliştirme için kullanabileceğiniz bir makine olmasını bekler.</span><span class="sxs-lookup"><span data-stu-id="3b471-108">This quick start expects you to have a machine you can use for development.</span></span> <span data-ttu-id="3b471-109">.NET konu [Get Started 10 dakika içinde](https://www.microsoft.com/net/core) Mac, PC ya da Linux yerel geliştirme ortamınızı ayarlamak için yönergeler içerir.</span><span class="sxs-lookup"><span data-stu-id="3b471-109">The .NET topic [Get Started in 10 minutes](https://www.microsoft.com/net/core) has instructions for setting up your local development environment on Mac, PC or Linux.</span></span>

## <a name="explore-integer-math"></a><span data-ttu-id="3b471-110">Tamsayı matematik keşfedin</span><span class="sxs-lookup"><span data-stu-id="3b471-110">Explore integer math</span></span>

<span data-ttu-id="3b471-111">Adlı bir dizin oluşturun **numaraları Hızlı Başlangıç**.</span><span class="sxs-lookup"><span data-stu-id="3b471-111">Create a directory named **numbers-quickstart**.</span></span> <span data-ttu-id="3b471-112">Geçerli dizin çalıştırma yapıp `dotnet new console -n NumbersInCSharp -o .`.</span><span class="sxs-lookup"><span data-stu-id="3b471-112">Make that the current directory and run `dotnet new console -n NumbersInCSharp -o .`.</span></span>

<span data-ttu-id="3b471-113">Açık **Program.cs** sık kullanılan Düzenleyicisi ve Değiştir satır `Console.Writeline("Hello World!");` aşağıdaki:</span><span class="sxs-lookup"><span data-stu-id="3b471-113">Open **Program.cs** in your favorite editor, and replace the line `Console.Writeline("Hello World!");` with the following:</span></span>

```csharp
int a = 18;
int b = 6;
int c = a + b;
Console.WriteLine(c);
```

<span data-ttu-id="3b471-114">Bu kodu yazarak çalıştırmak `dotnet run` , komut penceresinde.</span><span class="sxs-lookup"><span data-stu-id="3b471-114">Run this code by typing `dotnet run` in your command window.</span></span> 

<span data-ttu-id="3b471-115">Temel matematik işlemlerden tamsayılı yalnızca gördünüz.</span><span class="sxs-lookup"><span data-stu-id="3b471-115">You've just seen one of the fundamental math operations with integers.</span></span> <span data-ttu-id="3b471-116">`int` Yazın gösteren bir **tamsayı**, pozitif veya negatif bir tam sayı.</span><span class="sxs-lookup"><span data-stu-id="3b471-116">The `int` type represents an **integer**, a positive or negative whole number.</span></span> <span data-ttu-id="3b471-117">Kullandığınız `+` toplama simgesi.</span><span class="sxs-lookup"><span data-stu-id="3b471-117">You use the `+` symbol for addition.</span></span> <span data-ttu-id="3b471-118">Diğer yaygın matematiksel işlemler tamsayılar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="3b471-118">Other common mathematical operations for integers include:</span></span>

- <span data-ttu-id="3b471-119">`-`için çıkarma</span><span class="sxs-lookup"><span data-stu-id="3b471-119">`-` for subtraction</span></span>
- <span data-ttu-id="3b471-120">`*`çarpma için</span><span class="sxs-lookup"><span data-stu-id="3b471-120">`*` for multiplication</span></span>
- <span data-ttu-id="3b471-121">`/`bölme için</span><span class="sxs-lookup"><span data-stu-id="3b471-121">`/` for division</span></span>

<span data-ttu-id="3b471-122">Bu farklı işlemler inceleyerek başlayın.</span><span class="sxs-lookup"><span data-stu-id="3b471-122">Start by exploring those different operations.</span></span> <span data-ttu-id="3b471-123">Bu satırlar değerini yazan satırı sonra ekleyin `c`:</span><span class="sxs-lookup"><span data-stu-id="3b471-123">Add these lines after the line that writes the value of `c`:</span></span>

```csharp
c = a - b;
Console.WriteLine(c);
c = a * b;
Console.WriteLine(c);
c = a / b;
Console.WriteLine(c);
```

<span data-ttu-id="3b471-124">Bu kodu yazarak çalıştırmak `dotnet run` , komut penceresinde.</span><span class="sxs-lookup"><span data-stu-id="3b471-124">Run this code by typing `dotnet run` in your command window.</span></span> 
    
<span data-ttu-id="3b471-125">İsterseniz aynı satırda, birden çok matematik işlemleri gerçekleştirerek de deneyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3b471-125">You can also experiment by performing multiple mathematics operations in the same line, if you'd like.</span></span> <span data-ttu-id="3b471-126">Deneyin `c = a + b - 12 * 17;` örneğin.</span><span class="sxs-lookup"><span data-stu-id="3b471-126">Try `c = a + b - 12 * 17;` for example.</span></span> <span data-ttu-id="3b471-127">Değişkenleri ve sabit sayıları karıştırma izin verilir.</span><span class="sxs-lookup"><span data-stu-id="3b471-127">Mixing variables and constant numbers is allowed.</span></span>

> [!TIP]
> <span data-ttu-id="3b471-128">C# (veya herhangi bir programlama dili) keşfetmenizde kodu yazarken hataları hale getireceğiz.</span><span class="sxs-lookup"><span data-stu-id="3b471-128">As you explore C# (or any programming language), you'll make mistakes when you write code.</span></span> <span data-ttu-id="3b471-129">**Derleyici** bu hatalarını bulmak ve bunları sizin için rapor.</span><span class="sxs-lookup"><span data-stu-id="3b471-129">The **compiler** will find those errors and report them to you.</span></span> <span data-ttu-id="3b471-130">Çıktı, hata iletileri içerdiğinde, örnek kod ve düzeltmek görmek için pencerenizde kodu yakından bakın.</span><span class="sxs-lookup"><span data-stu-id="3b471-130">When the output contains error messages, look closely at the example code and the code in your window to see what to fix.</span></span>
> <span data-ttu-id="3b471-131">Bu alıştırmada, C# kod yapısını öğrenmenize yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="3b471-131">That exercise will help you learn the structure of C# code.</span></span>     

<span data-ttu-id="3b471-132">İlk adım tamamladınız.</span><span class="sxs-lookup"><span data-stu-id="3b471-132">You've finished the first step.</span></span> <span data-ttu-id="3b471-133">Şimdi, sonraki bölüme başlamadan önce geçerli kod ayrı bir yöntem taşıyın.</span><span class="sxs-lookup"><span data-stu-id="3b471-133">Before you start the next section, let's move the current code into a separate method.</span></span> <span data-ttu-id="3b471-134">Bu, yeni bir örnek ile çalışmaya başlamak kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="3b471-134">That makes it easier to start working with a new example.</span></span> <span data-ttu-id="3b471-135">Yeniden Adlandır, `Main` yönteme `WorkingWithIntegers` ve yeni bir yazma `Main` çağıran yöntemi `WorkingWithIntegers`.</span><span class="sxs-lookup"><span data-stu-id="3b471-135">Rename your `Main` method to `WorkingWithIntegers` and write a new `Main` method that calls `WorkingWithIntegers`.</span></span> <span data-ttu-id="3b471-136">İşiniz bittiğinde, kodunuzu aşağıdaki gibi görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="3b471-136">When you have finished, your code should look like this:</span></span>

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

## <a name="explore-order-of-operations"></a><span data-ttu-id="3b471-137">İşlem sırası keşfedin</span><span class="sxs-lookup"><span data-stu-id="3b471-137">Explore order of operations</span></span>

<span data-ttu-id="3b471-138">Açıklama çağrısı çıkışı `WorkingWithIntegers()`.</span><span class="sxs-lookup"><span data-stu-id="3b471-138">Comment out the call to `WorkingWithIntegers()`.</span></span> <span data-ttu-id="3b471-139">Bu bölümde çalışırken daha az kalabalık çıkış yapar:</span><span class="sxs-lookup"><span data-stu-id="3b471-139">It will make the output less cluttered as you work in this section:</span></span>

```csharp
//WorkingWithIntegers();
```

<span data-ttu-id="3b471-140">`//` Başlayan bir **açıklama** C#.</span><span class="sxs-lookup"><span data-stu-id="3b471-140">The `//` starts a **comment** in C#.</span></span> <span data-ttu-id="3b471-141">Kaynak kodunuz tutmak ancak kodu olarak yürütmeme istediğiniz herhangi bir metin açıklamalardır.</span><span class="sxs-lookup"><span data-stu-id="3b471-141">Comments are any text you want to keep in your source code but not execute as code.</span></span> <span data-ttu-id="3b471-142">Derleyici herhangi bir yürütülebilir kod açıklamalardan oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="3b471-142">The compiler does not generate any executable code from comments.</span></span>

<span data-ttu-id="3b471-143">C# dili kurallarla matematik içinde öğrenilen kurallarıyla tutarlı farklı matematik işlemlerinin önceliği tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3b471-143">The C# language defines the precedence of different mathematics operations with rules consistent with the rules you learned in mathematics.</span></span>
<span data-ttu-id="3b471-144">Çarpma ve bölme toplama ve çıkarma daha önceliklidir.</span><span class="sxs-lookup"><span data-stu-id="3b471-144">Multiplication and division take precedence over addition and subtraction.</span></span>
<span data-ttu-id="3b471-145">Aşağıdaki kodu ekleyerek keşfetmek, `Main` yöntemi ve execuing `dotnet run`:</span><span class="sxs-lookup"><span data-stu-id="3b471-145">Explore that by adding the following code to your `Main` method, and execuing `dotnet run`:</span></span>

```csharp
int a = 5;
int b = 4;
int c = 2;
int d = a + b * c;
Console.WriteLine(d);
 ```

<span data-ttu-id="3b471-146">Çıktı çarpma toplamadan önce gerçekleştirildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="3b471-146">The output demonstrates that the multiplication is performed before the addition.</span></span>

<span data-ttu-id="3b471-147">İşlemi parantezler ekleyerek, farklı bir işlem sırasını zorlayabilirsiniz veya istediğiniz işlemler önce gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="3b471-147">You can force a different order of operation by adding parentheses around the operation or operations you want performed first.</span></span> <span data-ttu-id="3b471-148">Aşağıdaki satırları ekleyin ve yeniden çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="3b471-148">Add the following lines and run again:</span></span>

```csharp
d = (a  + b) * c;
Console.WriteLine(d);
```

<span data-ttu-id="3b471-149">Birden çok sayıda farklı işlemler birleştirerek keşfedin.</span><span class="sxs-lookup"><span data-stu-id="3b471-149">Explore more by combining many different operations.</span></span> <span data-ttu-id="3b471-150">Aşağıdaki satırları şöyle sonuna ekleyin, `Main` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="3b471-150">Add something like the following lines at the bottom of your `Main` method.</span></span> <span data-ttu-id="3b471-151">Deneyin `dotnet run` yeniden.</span><span class="sxs-lookup"><span data-stu-id="3b471-151">Try `dotnet run` again.</span></span>

```csharp
d = (a + b) - 6 * c + (12 * 4) / 3 + 12;
Console.WriteLine(d);
```

<span data-ttu-id="3b471-152">Tamsayıları için ilginç bir davranıştır fark etmiş olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3b471-152">You may have noticed an interesting behavior for integers.</span></span> <span data-ttu-id="3b471-153">Bir ondalık veya kesir bölümünü eklemek için sonuç bile beklediğiniz zaman tamsayı bölme her zaman bir tamsayı sonuç üretir.</span><span class="sxs-lookup"><span data-stu-id="3b471-153">Integer division always produces an integer result, even when you'd expect the result to include a decimal or fractional portion.</span></span>

<span data-ttu-id="3b471-154">Bu davranış görmediyseniz, sonuna aşağıdaki kod deneyin, `Main` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="3b471-154">If you haven't seen this behavior, try the following code at the end of your `Main` method:</span></span>

```csharp
int e = 7;
int f = 4;
int g = 3;
int h = (e  + f) / g;
Console.WriteLine(h);
```

<span data-ttu-id="3b471-155">Tür `dotnet run` yeniden sonuçları görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="3b471-155">Type `dotnet run` again to see the results.</span></span>

<span data-ttu-id="3b471-156">Devam etmeden önce bu bölümde yazılmış ve yeni bir yöntemi put tüm kod atalım.</span><span class="sxs-lookup"><span data-stu-id="3b471-156">Before moving on, let's take all the code you've written in this section and put it in a new method.</span></span> <span data-ttu-id="3b471-157">Bu yeni yöntem çağrısı `OrderPrecedence`.</span><span class="sxs-lookup"><span data-stu-id="3b471-157">Call that new method `OrderPrecedence`.</span></span>
<span data-ttu-id="3b471-158">Aşağıdakine benzer şunun:</span><span class="sxs-lookup"><span data-stu-id="3b471-158">You should end up with something like this:</span></span>

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

## <a name="explore-integer-precision-and-limits"></a><span data-ttu-id="3b471-159">Tamsayı duyarlık ve sınırları keşfedin</span><span class="sxs-lookup"><span data-stu-id="3b471-159">Explore integer precision and limits</span></span>
<span data-ttu-id="3b471-160">Bu son örnekten tamsayı bölme sonucu kesen gösterdi.</span><span class="sxs-lookup"><span data-stu-id="3b471-160">That last sample showed you that integer division truncates the result.</span></span>
<span data-ttu-id="3b471-161">Alma **kalan** kullanarak **modulo** işleci, `%` karakter.</span><span class="sxs-lookup"><span data-stu-id="3b471-161">You can get the **remainder** by using the **modulo** operator, the `%` character.</span></span> <span data-ttu-id="3b471-162">Aşağıdaki kodda deneyin, `Main` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="3b471-162">Try the following code in your `Main` method:</span></span>

```csharp
int a = 7;
int b = 4;
int c = 3;
int d = (a  + b) / c;
int e = (a + b) % c;
Console.WriteLine($"quotient: {d}");
Console.WriteLine($"remainder: {e}");
```

<span data-ttu-id="3b471-163">C# tamsayı türü başka bir şekilde matematiksel tamsayılar farklıdır: `int` türüne sahip minimum ve maksimum sınırlar.</span><span class="sxs-lookup"><span data-stu-id="3b471-163">The C# integer type differs from mathematical integers in one other way: the `int` type has minimum and maximum limits.</span></span> <span data-ttu-id="3b471-164">Bu kodu ekleyin, `Main` yöntemi bu sınırları görmek için:</span><span class="sxs-lookup"><span data-stu-id="3b471-164">Add this code to your `Main` method to see those limits:</span></span>
    
```csharp
int max = int.MaxValue;
int min = int.MinValue;
Console.WriteLine($"The range of integers is {min} to {max}");
```

<span data-ttu-id="3b471-165">Bir hesaplama bu sınırlarını aşıyor bir değer oluşturursa, sahip olduğunuz bir **underflow** veya **taşma** koşulu.</span><span class="sxs-lookup"><span data-stu-id="3b471-165">If a calculation produces a value that exceeds those limits, you have an **underflow** or **overflow** condition.</span></span> <span data-ttu-id="3b471-166">Diğer bir sınırının sarmalamak için yanıt görünür.</span><span class="sxs-lookup"><span data-stu-id="3b471-166">The answer appears to wrap from one limit to the other.</span></span> <span data-ttu-id="3b471-167">Bu iki satır ekleyin, `Main` yöntemi bir örnek görmek için:</span><span class="sxs-lookup"><span data-stu-id="3b471-167">Add these two lines to your `Main` method to see an example:</span></span>

```csharp
int what = max + 3;
Console.WriteLine($"An example of overflow: {what}");
```
    
<span data-ttu-id="3b471-168">Yanıt çok düşük (negatif) tamsayı yakın olduğuna dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="3b471-168">Notice that the answer is very close to the minimum (negative) integer.</span></span> <span data-ttu-id="3b471-169">Aynı olan `min + 2`.</span><span class="sxs-lookup"><span data-stu-id="3b471-169">It's the same as `min + 2`.</span></span> <span data-ttu-id="3b471-170">Ek işlemi **taştı** tamsayı izin verilen değerleri.</span><span class="sxs-lookup"><span data-stu-id="3b471-170">The addition operation **overflowed** the allowed values for integers.</span></span>
<span data-ttu-id="3b471-171">Taşma "geçici en büyük olası tamsayı değerini küçüğe sarmalar" yanıt çok büyük negatif bir sayı nedeni.</span><span class="sxs-lookup"><span data-stu-id="3b471-171">The answer is a very large negative number because an overflow "wraps around" from the largest possible integer value to the smallest.</span></span>

<span data-ttu-id="3b471-172">Diğer sayısal türler farklı sınırlar ve ne zaman kullanacağınız duyarlık vardır `int` türü gereksinimlerinizi karşılayacak değil.</span><span class="sxs-lookup"><span data-stu-id="3b471-172">There are other numeric types with different limits and precision that you would use when the `int` type doesn't meet your needs.</span></span> <span data-ttu-id="3b471-173">Bu sonraki inceleyelim.</span><span class="sxs-lookup"><span data-stu-id="3b471-173">Let's explore those next.</span></span>

<span data-ttu-id="3b471-174">Bir kez daha, bu bölümde ayrı bir yöntem içine yazdığınız kodun şimdi taşıyın.</span><span class="sxs-lookup"><span data-stu-id="3b471-174">Once again, let's move the code you wrote in this section into a separate method.</span></span> <span data-ttu-id="3b471-175">Bu ad `TestLimits`.</span><span class="sxs-lookup"><span data-stu-id="3b471-175">Name it `TestLimits`.</span></span> 

## <a name="work-with-the-double-type"></a><span data-ttu-id="3b471-176">Çift tür ile çalışma</span><span class="sxs-lookup"><span data-stu-id="3b471-176">Work with the double type</span></span>

<span data-ttu-id="3b471-177">`double` Sayısal tür çift duyarlıklı kayan noktalı sayıyı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="3b471-177">The `double` numeric type represents a double-precision floating point number.</span></span> <span data-ttu-id="3b471-178">Bu koşullar, yeni olabilir.</span><span class="sxs-lookup"><span data-stu-id="3b471-178">Those terms may be new to you.</span></span> <span data-ttu-id="3b471-179">A **kayan nokta** sayıdır çok büyük veya küçük büyüklüğü integral olmayan sayılar temsil etmek kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="3b471-179">A **floating point** number is useful to represent non-integral numbers that may be very large or small in magnitude.</span></span> <span data-ttu-id="3b471-180">**Çift duyarlıklı** daha büyük duyarlık kullanılarak bu sayı depolanır anlamına gelir **tek duyarlıklı**.</span><span class="sxs-lookup"><span data-stu-id="3b471-180">**Double-precision** means that these numbers are stored using greater precision than **single-precision**.</span></span> <span data-ttu-id="3b471-181">Modern bilgisayarlarda tek duyarlıklı sayılar daha çift duyarlıklı kullanmak için daha yaygın bir durumdur.</span><span class="sxs-lookup"><span data-stu-id="3b471-181">On modern computers, it is more common to use double precision than single precision numbers.</span></span>
<span data-ttu-id="3b471-182">İnceleyelim.</span><span class="sxs-lookup"><span data-stu-id="3b471-182">Let's explore.</span></span> <span data-ttu-id="3b471-183">Aşağıdaki kodu ekleyin ve sonucu bakın:</span><span class="sxs-lookup"><span data-stu-id="3b471-183">Add the following code and see the result:</span></span>

```csharp
double a = 5;
double b = 4;
double c = 2;
double d = (a  + b) / c;
Console.WriteLine(d);
```

<span data-ttu-id="3b471-184">Yanıt sayının ondalık kısmı içerdiğine dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="3b471-184">Notice that the answer includes the decimal portion of the quotient.</span></span> <span data-ttu-id="3b471-185">Double biraz daha karmaşık bir ifadesiyle deneyin:</span><span class="sxs-lookup"><span data-stu-id="3b471-185">Try a slightly more complicated expression with doubles:</span></span>

```csharp
double e = 19;
double f = 23;
double g = 8;
double h = (e  + f) / g;
Console.WriteLine(h);
```

<span data-ttu-id="3b471-186">Bir çift değer aralığını tamsayı değerleri çok daha fazladır.</span><span class="sxs-lookup"><span data-stu-id="3b471-186">The range of a double value is much greater than integer values.</span></span> <span data-ttu-id="3b471-187">Şu ana kadar yazdıklarınızı altına aşağıdaki kodu deneyin:</span><span class="sxs-lookup"><span data-stu-id="3b471-187">Try the following code below what you've written so far:</span></span>

```csharp
double max = double.MaxValue;
double min = double.MinValue;
Console.WriteLine($"The range of double is {min} to {max}");
```

<span data-ttu-id="3b471-188">Bu değerleri bilimsel gösterimde yazdırılır.</span><span class="sxs-lookup"><span data-stu-id="3b471-188">These values are printed out in scientific notation.</span></span> <span data-ttu-id="3b471-189">Sol tarafındaki sayıya `E` significand değil.</span><span class="sxs-lookup"><span data-stu-id="3b471-189">The number to the left of the `E` is the significand.</span></span> <span data-ttu-id="3b471-190">Sağa üs 10 gücünü sayıdır.</span><span class="sxs-lookup"><span data-stu-id="3b471-190">The number to the right is the exponent, as a power of 10.</span></span> 

<span data-ttu-id="3b471-191">Yalnızca ondalık sayı gibi olarak matematik hataları yuvarlama çiftleri C# olabilir.</span><span class="sxs-lookup"><span data-stu-id="3b471-191">Just like decimal numbers in math, doubles in C# can have rounding errors.</span></span> <span data-ttu-id="3b471-192">Bu kod deneyin:</span><span class="sxs-lookup"><span data-stu-id="3b471-192">Try this code:</span></span>

```csharp
double third = 1.0 / 3.0;
Console.WriteLine(third);
```

<span data-ttu-id="3b471-193">Bunu biliyor `0.3` yinelenen tam olarak aynı olup `1/3`.</span><span class="sxs-lookup"><span data-stu-id="3b471-193">You know that `0.3` repeating is not exactly the same as `1/3`.</span></span>

<span data-ttu-id="3b471-194">***Sınama***</span><span class="sxs-lookup"><span data-stu-id="3b471-194">***Challenge***</span></span>

<span data-ttu-id="3b471-195">Büyük sayılar, küçük sayılar, çarpma ve bölme kullanarak diğer hesaplamalarla deneyin `double` türü.</span><span class="sxs-lookup"><span data-stu-id="3b471-195">Try other calculations with large numbers, small numbers, multiplication and division using the `double` type.</span></span>  <span data-ttu-id="3b471-196">Daha karmaşık hesaplamalar deneyin.</span><span class="sxs-lookup"><span data-stu-id="3b471-196">Try more complicated calculations.</span></span>

<span data-ttu-id="3b471-197">Sınama ile biraz zaman harcanan sonra yazdıktan ve yeni bir yöntemi yerleştirin kod alın.</span><span class="sxs-lookup"><span data-stu-id="3b471-197">After you've spent some time with the challenge, take the code you've written and place it in a new method.</span></span> <span data-ttu-id="3b471-198">Bu yeni yöntem adı `WorkWithDoubles`.</span><span class="sxs-lookup"><span data-stu-id="3b471-198">Name that new method `WorkWithDoubles`.</span></span>

## <a name="work-with-fixed-point-types"></a><span data-ttu-id="3b471-199">Sabit noktası türleri ile çalışma</span><span class="sxs-lookup"><span data-stu-id="3b471-199">Work with fixed point types</span></span>

<span data-ttu-id="3b471-200">C# temel sayısal türler gördünüz: tamsayılar ve iki katına çıkar.</span><span class="sxs-lookup"><span data-stu-id="3b471-200">You've seen the basic numeric types in C#: integers and doubles.</span></span>  <span data-ttu-id="3b471-201">Bilgi edinmek için bir tür: `decimal` türü.</span><span class="sxs-lookup"><span data-stu-id="3b471-201">There is one other type to learn: the `decimal` type.</span></span> <span data-ttu-id="3b471-202">`decimal` Türüne sahip daha küçük bir aralık daha iyi kesinlik ancak `double`.</span><span class="sxs-lookup"><span data-stu-id="3b471-202">The `decimal` type has a smaller range but greater precision than `double`.</span></span> <span data-ttu-id="3b471-203">Terim **sabit noktası** ondalık (veya ikili noktası) taşınmaz anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="3b471-203">The term **fixed point** means that the decimal point (or binary point) doesn't move.</span></span> <span data-ttu-id="3b471-204">Bir göz atalım:</span><span class="sxs-lookup"><span data-stu-id="3b471-204">Let's take a look:</span></span>

```csharp
decimal min = decimal.MinValue;
decimal max = decimal.MaxValue;
Console.WriteLine($"The range of the decimal type is {min} to {max}");
```

<span data-ttu-id="3b471-205">Aralık değerinden küçük olduğunu fark `double` türü.</span><span class="sxs-lookup"><span data-stu-id="3b471-205">Notice that the range is smaller than the `double` type.</span></span> <span data-ttu-id="3b471-206">Aşağıdaki kod deneyerek decimal türü ile daha iyi kesinlik görebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="3b471-206">You can see the greater precision with the decimal type by trying the following code:</span></span>

```csharp
double a = 1.0;
double b = 3.0;
Console.WriteLine(a / b);

decimal c = 1.0M;
decimal d = 3.0M;
Console.WriteLine(c / d);
```

<span data-ttu-id="3b471-207">`M` Numaraları sonekidir nasıl bir sabit kullanması gerektiğini belirtmek `decimal` türü.</span><span class="sxs-lookup"><span data-stu-id="3b471-207">The `M` suffix on the numbers is how you indicate that a constant should use the `decimal` type.</span></span>

<span data-ttu-id="3b471-208">Decimal türü kullanarak matematik ondalık konumun sağında daha fazla basamağa sahip olmadığına dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="3b471-208">Notice that the math using the decimal type has more digits to the right of the decimal point.</span></span> 

<span data-ttu-id="3b471-209">***Sınama***</span><span class="sxs-lookup"><span data-stu-id="3b471-209">***Challenge***</span></span>

<span data-ttu-id="3b471-210">Farklı sayısal türler gördüğünüze göre 2.50 inç, RADIUS olduğu dairenin alanı hesaplar kod yazın.</span><span class="sxs-lookup"><span data-stu-id="3b471-210">Now that you've seen the different numeric types, write code that calculates the area of a circle whose radius is 2.50 inches.</span></span> <span data-ttu-id="3b471-211">Unutmayın PI ile çarpılmış dairenin alanı kare RADIUS olduğunu.</span><span class="sxs-lookup"><span data-stu-id="3b471-211">Remember that the area of a circle is the radius squared multiplied by PI.</span></span> <span data-ttu-id="3b471-212">Bir ipucu: C# PI için bir sabit içeriyor <xref:System.Math.PI?displayProperty=nameWithType> , bu değer için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3b471-212">One hint: C# contains a constant for PI, <xref:System.Math.PI?displayProperty=nameWithType> that you can use for that value.</span></span> 

<span data-ttu-id="3b471-213">Yanıtınız tarafından kontrol edebilirsiniz [Github'da tamamlanmış örnek kodu incelemeden](https://github.com/dotnet/docs/tree/master/samples/csharp/numbers-quickstart/Program.cs#L104-L106)</span><span class="sxs-lookup"><span data-stu-id="3b471-213">You can check your answer by [looking at the finished sample code on GitHub](https://github.com/dotnet/docs/tree/master/samples/csharp/numbers-quickstart/Program.cs#L104-L106)</span></span>

<span data-ttu-id="3b471-214">İsterseniz başka bir formüller deneyin.</span><span class="sxs-lookup"><span data-stu-id="3b471-214">Try some other formulas if you'd like.</span></span> 

<span data-ttu-id="3b471-215">"Numaraları C# ' ta" Hızlı Başlangıç tamamladınız.</span><span class="sxs-lookup"><span data-stu-id="3b471-215">You've completed the "Numbers in C#" quick start.</span></span> <span data-ttu-id="3b471-216">İle devam edebilirsiniz [dallar ve döngüler](branches-and-loops-local.md) kendi geliştirme ortamında hızlı başlangıç.</span><span class="sxs-lookup"><span data-stu-id="3b471-216">You can continue with the [Branches and loops](branches-and-loops-local.md) quick start in your own development environment.</span></span>

<span data-ttu-id="3b471-217">Aşağıdaki konularda C# numaraları hakkında daha fazla bilgi edinebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="3b471-217">You can learn more about numbers in C# in the following topics:</span></span>

<span data-ttu-id="3b471-218">[Tam sayı türleri tablosu](../language-reference/keywords/integral-types-table.md) </span><span class="sxs-lookup"><span data-stu-id="3b471-218">[Integral Types Table](../language-reference/keywords/integral-types-table.md) </span></span>  
<span data-ttu-id="3b471-219">[Kayan nokta türleri tablosu](../language-reference/keywords/floating-point-types-table.md) </span><span class="sxs-lookup"><span data-stu-id="3b471-219">[Floating-Point Types Table](../language-reference/keywords/floating-point-types-table.md) </span></span>  
<span data-ttu-id="3b471-220">[Yerleşik türler tablosu](../language-reference/keywords/built-in-types-table.md) </span><span class="sxs-lookup"><span data-stu-id="3b471-220">[Built-In Types Table](../language-reference/keywords/built-in-types-table.md) </span></span>  
<span data-ttu-id="3b471-221">[Örtük sayısal dönüşümler tablosu](../language-reference/keywords/implicit-numeric-conversions-table.md) </span><span class="sxs-lookup"><span data-stu-id="3b471-221">[Implicit Numeric Conversions Table](../language-reference/keywords/implicit-numeric-conversions-table.md) </span></span>  
[<span data-ttu-id="3b471-222">Açık sayısal dönüşümler tablosu</span><span class="sxs-lookup"><span data-stu-id="3b471-222">Explicit Numeric Conversions Table</span></span>](../language-reference/keywords/explicit-numeric-conversions-table.md)

