---
title: "C# Öğreticisi - C# yerel quickstarts numaraları"
description: "C# sayısal türler, özellikleri ve yöntemleri keşfetme öğrenin."
author: billwagner
ms.author: wiwagn
ms.date: 10/31/2017
ms.topic: get-started-article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.custom: mvc
ms.openlocfilehash: 99c2f8e4807c4d18c0c798e3a737f4a88d6e62d6
ms.sourcegitcommit: 3a96c706e4dbb4667bf3bf37edac9e1666646f93
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/27/2018
---
# <a name="numbers-in-c-quickstart"></a><span data-ttu-id="78fe3-103">C# hızlı başlangıç numaraları</span><span class="sxs-lookup"><span data-stu-id="78fe3-103">Numbers in C# quickstart</span></span>

<span data-ttu-id="78fe3-104">Bu hızlı başlangıç C# sayı türleri hakkında etkileşimli olarak öğretilmektedir.</span><span class="sxs-lookup"><span data-stu-id="78fe3-104">This quickstart teaches you about the number types in C# interactively.</span></span> <span data-ttu-id="78fe3-105">Küçük miktarda kod yazacaksınız sonra derlemek ve bu kodu çalıştırmak.</span><span class="sxs-lookup"><span data-stu-id="78fe3-105">You'll write small amounts of code, then you'll compile and run that code.</span></span> <span data-ttu-id="78fe3-106">Hızlı bir dizi numaraları ve C# matematik işlemleri keşfedin dersleri içerir.</span><span class="sxs-lookup"><span data-stu-id="78fe3-106">The quickstart contains a series of lessons that explore numbers and math operations in C#.</span></span> <span data-ttu-id="78fe3-107">Bu derslerin C# dil temelleri öğretir.</span><span class="sxs-lookup"><span data-stu-id="78fe3-107">These lessons teach you the fundamentals of the C# language.</span></span>

<span data-ttu-id="78fe3-108">Bu hızlı başlangıç geliştirme için kullanabileceğiniz bir makine olmasını bekler.</span><span class="sxs-lookup"><span data-stu-id="78fe3-108">This quickstart expects you to have a machine you can use for development.</span></span> <span data-ttu-id="78fe3-109">.NET konu [Get Started 10 dakika içinde](https://www.microsoft.com/net/core) Mac, PC ya da Linux yerel geliştirme ortamınızı ayarlamak için yönergeler içerir.</span><span class="sxs-lookup"><span data-stu-id="78fe3-109">The .NET topic [Get Started in 10 minutes](https://www.microsoft.com/net/core) has instructions for setting up your local development environment on Mac, PC or Linux.</span></span> <span data-ttu-id="78fe3-110">Hızlı bir genel bakış kullandığınız komutların bulunduğu [yerel quickstarts giriş](local-environment.md) daha fazla bilgi için bağlantılar ile birlikte.</span><span class="sxs-lookup"><span data-stu-id="78fe3-110">A quick overview of the commands you'll use is in the [introduction to the local quickstarts](local-environment.md) with links to more details.</span></span>

## <a name="explore-integer-math"></a><span data-ttu-id="78fe3-111">Tamsayı matematik keşfedin</span><span class="sxs-lookup"><span data-stu-id="78fe3-111">Explore integer math</span></span>

<span data-ttu-id="78fe3-112">Adlı bir dizin oluşturun **numaraları Hızlı Başlangıç**.</span><span class="sxs-lookup"><span data-stu-id="78fe3-112">Create a directory named **numbers-quickstart**.</span></span> <span data-ttu-id="78fe3-113">Geçerli dizin çalıştırma yapıp `dotnet new console -n NumbersInCSharp -o .`.</span><span class="sxs-lookup"><span data-stu-id="78fe3-113">Make that the current directory and run `dotnet new console -n NumbersInCSharp -o .`.</span></span>

<span data-ttu-id="78fe3-114">Açık **Program.cs** sık kullanılan Düzenleyicisi ve Değiştir satır `Console.Writeline("Hello World!");` aşağıdaki:</span><span class="sxs-lookup"><span data-stu-id="78fe3-114">Open **Program.cs** in your favorite editor, and replace the line `Console.Writeline("Hello World!");` with the following:</span></span>

```csharp
int a = 18;
int b = 6;
int c = a + b;
Console.WriteLine(c);
```

<span data-ttu-id="78fe3-115">Bu kodu yazarak çalıştırmak `dotnet run` , komut penceresinde.</span><span class="sxs-lookup"><span data-stu-id="78fe3-115">Run this code by typing `dotnet run` in your command window.</span></span> 

<span data-ttu-id="78fe3-116">Temel matematik işlemlerden tamsayılı yalnızca gördünüz.</span><span class="sxs-lookup"><span data-stu-id="78fe3-116">You've just seen one of the fundamental math operations with integers.</span></span> <span data-ttu-id="78fe3-117">`int` Yazın gösteren bir **tamsayı**, pozitif veya negatif bir tam sayı.</span><span class="sxs-lookup"><span data-stu-id="78fe3-117">The `int` type represents an **integer**, a positive or negative whole number.</span></span> <span data-ttu-id="78fe3-118">Kullandığınız `+` toplama simgesi.</span><span class="sxs-lookup"><span data-stu-id="78fe3-118">You use the `+` symbol for addition.</span></span> <span data-ttu-id="78fe3-119">Diğer yaygın matematiksel işlemler tamsayılar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="78fe3-119">Other common mathematical operations for integers include:</span></span>

- <span data-ttu-id="78fe3-120">`-` için çıkarma</span><span class="sxs-lookup"><span data-stu-id="78fe3-120">`-` for subtraction</span></span>
- <span data-ttu-id="78fe3-121">`*` çarpma için</span><span class="sxs-lookup"><span data-stu-id="78fe3-121">`*` for multiplication</span></span>
- <span data-ttu-id="78fe3-122">`/` bölme için</span><span class="sxs-lookup"><span data-stu-id="78fe3-122">`/` for division</span></span>

<span data-ttu-id="78fe3-123">Bu farklı işlemler inceleyerek başlayın.</span><span class="sxs-lookup"><span data-stu-id="78fe3-123">Start by exploring those different operations.</span></span> <span data-ttu-id="78fe3-124">Bu satırlar değerini yazan satırı sonra ekleyin `c`:</span><span class="sxs-lookup"><span data-stu-id="78fe3-124">Add these lines after the line that writes the value of `c`:</span></span>

```csharp
c = a - b;
Console.WriteLine(c);
c = a * b;
Console.WriteLine(c);
c = a / b;
Console.WriteLine(c);
```

<span data-ttu-id="78fe3-125">Bu kodu yazarak çalıştırmak `dotnet run` , komut penceresinde.</span><span class="sxs-lookup"><span data-stu-id="78fe3-125">Run this code by typing `dotnet run` in your command window.</span></span> 
    
<span data-ttu-id="78fe3-126">İsterseniz aynı satırda, birden çok matematik işlemleri gerçekleştirerek de deneyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="78fe3-126">You can also experiment by performing multiple mathematics operations in the same line, if you'd like.</span></span> <span data-ttu-id="78fe3-127">Deneyin `c = a + b - 12 * 17;` örneğin.</span><span class="sxs-lookup"><span data-stu-id="78fe3-127">Try `c = a + b - 12 * 17;` for example.</span></span> <span data-ttu-id="78fe3-128">Değişkenleri ve sabit sayıları karıştırma izin verilir.</span><span class="sxs-lookup"><span data-stu-id="78fe3-128">Mixing variables and constant numbers is allowed.</span></span>

> [!TIP]
> <span data-ttu-id="78fe3-129">C# (veya herhangi bir programlama dili) keşfetmenizde kodu yazarken hataları hale getireceğiz.</span><span class="sxs-lookup"><span data-stu-id="78fe3-129">As you explore C# (or any programming language), you'll make mistakes when you write code.</span></span> <span data-ttu-id="78fe3-130">**Derleyici** bu hatalarını bulmak ve bunları sizin için rapor.</span><span class="sxs-lookup"><span data-stu-id="78fe3-130">The **compiler** will find those errors and report them to you.</span></span> <span data-ttu-id="78fe3-131">Çıktı, hata iletileri içerdiğinde, örnek kod ve düzeltmek görmek için pencerenizde kodu yakından bakın.</span><span class="sxs-lookup"><span data-stu-id="78fe3-131">When the output contains error messages, look closely at the example code and the code in your window to see what to fix.</span></span>
> <span data-ttu-id="78fe3-132">Bu alıştırmada, C# kod yapısını öğrenmenize yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="78fe3-132">That exercise will help you learn the structure of C# code.</span></span>     

<span data-ttu-id="78fe3-133">İlk adım tamamladınız.</span><span class="sxs-lookup"><span data-stu-id="78fe3-133">You've finished the first step.</span></span> <span data-ttu-id="78fe3-134">Şimdi, sonraki bölüme başlamadan önce geçerli kod ayrı bir yöntem taşıyın.</span><span class="sxs-lookup"><span data-stu-id="78fe3-134">Before you start the next section, let's move the current code into a separate method.</span></span> <span data-ttu-id="78fe3-135">Bu, yeni bir örnek ile çalışmaya başlamak kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="78fe3-135">That makes it easier to start working with a new example.</span></span> <span data-ttu-id="78fe3-136">Yeniden Adlandır, `Main` yönteme `WorkingWithIntegers` ve yeni bir yazma `Main` çağıran yöntemi `WorkingWithIntegers`.</span><span class="sxs-lookup"><span data-stu-id="78fe3-136">Rename your `Main` method to `WorkingWithIntegers` and write a new `Main` method that calls `WorkingWithIntegers`.</span></span> <span data-ttu-id="78fe3-137">İşiniz bittiğinde, kodunuzu aşağıdaki gibi görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="78fe3-137">When you have finished, your code should look like this:</span></span>

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

## <a name="explore-order-of-operations"></a><span data-ttu-id="78fe3-138">İşlem sırası keşfedin</span><span class="sxs-lookup"><span data-stu-id="78fe3-138">Explore order of operations</span></span>

<span data-ttu-id="78fe3-139">Açıklama çağrısı çıkışı `WorkingWithIntegers()`.</span><span class="sxs-lookup"><span data-stu-id="78fe3-139">Comment out the call to `WorkingWithIntegers()`.</span></span> <span data-ttu-id="78fe3-140">Bu bölümde çalışırken daha az kalabalık çıkış yapar:</span><span class="sxs-lookup"><span data-stu-id="78fe3-140">It will make the output less cluttered as you work in this section:</span></span>

```csharp
//WorkingWithIntegers();
```

<span data-ttu-id="78fe3-141">`//` Başlayan bir **açıklama** C#.</span><span class="sxs-lookup"><span data-stu-id="78fe3-141">The `//` starts a **comment** in C#.</span></span> <span data-ttu-id="78fe3-142">Kaynak kodunuz tutmak ancak kodu olarak yürütmeme istediğiniz herhangi bir metin açıklamalardır.</span><span class="sxs-lookup"><span data-stu-id="78fe3-142">Comments are any text you want to keep in your source code but not execute as code.</span></span> <span data-ttu-id="78fe3-143">Derleyici herhangi bir yürütülebilir kod açıklamalardan oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="78fe3-143">The compiler does not generate any executable code from comments.</span></span>

<span data-ttu-id="78fe3-144">C# dili kurallarla matematik içinde öğrenilen kurallarıyla tutarlı farklı matematik işlemlerinin önceliği tanımlar.</span><span class="sxs-lookup"><span data-stu-id="78fe3-144">The C# language defines the precedence of different mathematics operations with rules consistent with the rules you learned in mathematics.</span></span>
<span data-ttu-id="78fe3-145">Çarpma ve bölme toplama ve çıkarma daha önceliklidir.</span><span class="sxs-lookup"><span data-stu-id="78fe3-145">Multiplication and division take precedence over addition and subtraction.</span></span>
<span data-ttu-id="78fe3-146">Aşağıdaki kodu ekleyerek keşfetmek, `Main` yöntemi ve execuing `dotnet run`:</span><span class="sxs-lookup"><span data-stu-id="78fe3-146">Explore that by adding the following code to your `Main` method, and execuing `dotnet run`:</span></span>

```csharp
int a = 5;
int b = 4;
int c = 2;
int d = a + b * c;
Console.WriteLine(d);
 ```

<span data-ttu-id="78fe3-147">Çıktı çarpma toplamadan önce gerçekleştirildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="78fe3-147">The output demonstrates that the multiplication is performed before the addition.</span></span>

<span data-ttu-id="78fe3-148">İşlemi parantezler ekleyerek, farklı bir işlem sırasını zorlayabilirsiniz veya istediğiniz işlemler önce gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="78fe3-148">You can force a different order of operation by adding parentheses around the operation or operations you want performed first.</span></span> <span data-ttu-id="78fe3-149">Aşağıdaki satırları ekleyin ve yeniden çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="78fe3-149">Add the following lines and run again:</span></span>

```csharp
d = (a  + b) * c;
Console.WriteLine(d);
```

<span data-ttu-id="78fe3-150">Birden çok sayıda farklı işlemler birleştirerek keşfedin.</span><span class="sxs-lookup"><span data-stu-id="78fe3-150">Explore more by combining many different operations.</span></span> <span data-ttu-id="78fe3-151">Aşağıdaki satırları şöyle sonuna ekleyin, `Main` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="78fe3-151">Add something like the following lines at the bottom of your `Main` method.</span></span> <span data-ttu-id="78fe3-152">Deneyin `dotnet run` yeniden.</span><span class="sxs-lookup"><span data-stu-id="78fe3-152">Try `dotnet run` again.</span></span>

```csharp
d = (a + b) - 6 * c + (12 * 4) / 3 + 12;
Console.WriteLine(d);
```

<span data-ttu-id="78fe3-153">Tamsayıları için ilginç bir davranıştır fark etmiş olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="78fe3-153">You may have noticed an interesting behavior for integers.</span></span> <span data-ttu-id="78fe3-154">Bir ondalık veya kesir bölümünü eklemek için sonuç bile beklediğiniz zaman tamsayı bölme her zaman bir tamsayı sonuç üretir.</span><span class="sxs-lookup"><span data-stu-id="78fe3-154">Integer division always produces an integer result, even when you'd expect the result to include a decimal or fractional portion.</span></span>

<span data-ttu-id="78fe3-155">Bu davranış görmediyseniz, sonuna aşağıdaki kod deneyin, `Main` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="78fe3-155">If you haven't seen this behavior, try the following code at the end of your `Main` method:</span></span>

```csharp
int e = 7;
int f = 4;
int g = 3;
int h = (e  + f) / g;
Console.WriteLine(h);
```

<span data-ttu-id="78fe3-156">Tür `dotnet run` yeniden sonuçları görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="78fe3-156">Type `dotnet run` again to see the results.</span></span>

<span data-ttu-id="78fe3-157">Devam etmeden önce bu bölümde yazılmış ve yeni bir yöntemi put tüm kod atalım.</span><span class="sxs-lookup"><span data-stu-id="78fe3-157">Before moving on, let's take all the code you've written in this section and put it in a new method.</span></span> <span data-ttu-id="78fe3-158">Bu yeni yöntem çağrısı `OrderPrecedence`.</span><span class="sxs-lookup"><span data-stu-id="78fe3-158">Call that new method `OrderPrecedence`.</span></span>
<span data-ttu-id="78fe3-159">Aşağıdakine benzer şunun:</span><span class="sxs-lookup"><span data-stu-id="78fe3-159">You should end up with something like this:</span></span>

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

## <a name="explore-integer-precision-and-limits"></a><span data-ttu-id="78fe3-160">Tamsayı duyarlık ve sınırları keşfedin</span><span class="sxs-lookup"><span data-stu-id="78fe3-160">Explore integer precision and limits</span></span>
<span data-ttu-id="78fe3-161">Bu son örnekten tamsayı bölme sonucu kesen gösterdi.</span><span class="sxs-lookup"><span data-stu-id="78fe3-161">That last sample showed you that integer division truncates the result.</span></span>
<span data-ttu-id="78fe3-162">Alma **kalan** kullanarak **modulo** işleci, `%` karakter.</span><span class="sxs-lookup"><span data-stu-id="78fe3-162">You can get the **remainder** by using the **modulo** operator, the `%` character.</span></span> <span data-ttu-id="78fe3-163">Aşağıdaki kodda deneyin, `Main` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="78fe3-163">Try the following code in your `Main` method:</span></span>

```csharp
int a = 7;
int b = 4;
int c = 3;
int d = (a  + b) / c;
int e = (a + b) % c;
Console.WriteLine($"quotient: {d}");
Console.WriteLine($"remainder: {e}");
```

<span data-ttu-id="78fe3-164">C# tamsayı türü başka bir şekilde matematiksel tamsayılar farklıdır: `int` türüne sahip minimum ve maksimum sınırlar.</span><span class="sxs-lookup"><span data-stu-id="78fe3-164">The C# integer type differs from mathematical integers in one other way: the `int` type has minimum and maximum limits.</span></span> <span data-ttu-id="78fe3-165">Bu kodu ekleyin, `Main` yöntemi bu sınırları görmek için:</span><span class="sxs-lookup"><span data-stu-id="78fe3-165">Add this code to your `Main` method to see those limits:</span></span>
    
```csharp
int max = int.MaxValue;
int min = int.MinValue;
Console.WriteLine($"The range of integers is {min} to {max}");
```

<span data-ttu-id="78fe3-166">Bir hesaplama bu sınırlarını aşıyor bir değer oluşturursa, sahip olduğunuz bir **underflow** veya **taşma** koşulu.</span><span class="sxs-lookup"><span data-stu-id="78fe3-166">If a calculation produces a value that exceeds those limits, you have an **underflow** or **overflow** condition.</span></span> <span data-ttu-id="78fe3-167">Diğer bir sınırının sarmalamak için yanıt görünür.</span><span class="sxs-lookup"><span data-stu-id="78fe3-167">The answer appears to wrap from one limit to the other.</span></span> <span data-ttu-id="78fe3-168">Bu iki satır ekleyin, `Main` yöntemi bir örnek görmek için:</span><span class="sxs-lookup"><span data-stu-id="78fe3-168">Add these two lines to your `Main` method to see an example:</span></span>

```csharp
int what = max + 3;
Console.WriteLine($"An example of overflow: {what}");
```
    
<span data-ttu-id="78fe3-169">Yanıt çok düşük (negatif) tamsayı yakın olduğuna dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="78fe3-169">Notice that the answer is very close to the minimum (negative) integer.</span></span> <span data-ttu-id="78fe3-170">Aynı olan `min + 2`.</span><span class="sxs-lookup"><span data-stu-id="78fe3-170">It's the same as `min + 2`.</span></span> <span data-ttu-id="78fe3-171">Ek işlemi **taştı** tamsayı izin verilen değerleri.</span><span class="sxs-lookup"><span data-stu-id="78fe3-171">The addition operation **overflowed** the allowed values for integers.</span></span>
<span data-ttu-id="78fe3-172">Taşma "geçici en büyük olası tamsayı değerini küçüğe sarmalar" yanıt çok büyük negatif bir sayı nedeni.</span><span class="sxs-lookup"><span data-stu-id="78fe3-172">The answer is a very large negative number because an overflow "wraps around" from the largest possible integer value to the smallest.</span></span>

<span data-ttu-id="78fe3-173">Diğer sayısal türler farklı sınırlar ve ne zaman kullanacağınız duyarlık vardır `int` türü gereksinimlerinizi karşılayacak değil.</span><span class="sxs-lookup"><span data-stu-id="78fe3-173">There are other numeric types with different limits and precision that you would use when the `int` type doesn't meet your needs.</span></span> <span data-ttu-id="78fe3-174">Bu sonraki inceleyelim.</span><span class="sxs-lookup"><span data-stu-id="78fe3-174">Let's explore those next.</span></span>

<span data-ttu-id="78fe3-175">Bir kez daha, bu bölümde ayrı bir yöntem içine yazdığınız kodun şimdi taşıyın.</span><span class="sxs-lookup"><span data-stu-id="78fe3-175">Once again, let's move the code you wrote in this section into a separate method.</span></span> <span data-ttu-id="78fe3-176">Bu ad `TestLimits`.</span><span class="sxs-lookup"><span data-stu-id="78fe3-176">Name it `TestLimits`.</span></span> 

## <a name="work-with-the-double-type"></a><span data-ttu-id="78fe3-177">Çift tür ile çalışma</span><span class="sxs-lookup"><span data-stu-id="78fe3-177">Work with the double type</span></span>

<span data-ttu-id="78fe3-178">`double` Sayısal tür çift duyarlıklı kayan noktalı sayıyı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="78fe3-178">The `double` numeric type represents a double-precision floating point number.</span></span> <span data-ttu-id="78fe3-179">Bu koşullar, yeni olabilir.</span><span class="sxs-lookup"><span data-stu-id="78fe3-179">Those terms may be new to you.</span></span> <span data-ttu-id="78fe3-180">A **kayan nokta** sayıdır çok büyük veya küçük büyüklüğü integral olmayan sayılar temsil etmek kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="78fe3-180">A **floating point** number is useful to represent non-integral numbers that may be very large or small in magnitude.</span></span> <span data-ttu-id="78fe3-181">**Çift duyarlıklı** daha büyük duyarlık kullanılarak bu sayı depolanır anlamına gelir **tek duyarlıklı**.</span><span class="sxs-lookup"><span data-stu-id="78fe3-181">**Double-precision** means that these numbers are stored using greater precision than **single-precision**.</span></span> <span data-ttu-id="78fe3-182">Modern bilgisayarlarda tek duyarlıklı sayılar daha çift duyarlıklı kullanmak için daha yaygın bir durumdur.</span><span class="sxs-lookup"><span data-stu-id="78fe3-182">On modern computers, it is more common to use double precision than single precision numbers.</span></span>
<span data-ttu-id="78fe3-183">İnceleyelim.</span><span class="sxs-lookup"><span data-stu-id="78fe3-183">Let's explore.</span></span> <span data-ttu-id="78fe3-184">Aşağıdaki kodu ekleyin ve sonucu bakın:</span><span class="sxs-lookup"><span data-stu-id="78fe3-184">Add the following code and see the result:</span></span>

```csharp
double a = 5;
double b = 4;
double c = 2;
double d = (a  + b) / c;
Console.WriteLine(d);
```

<span data-ttu-id="78fe3-185">Yanıt sayının ondalık kısmı içerdiğine dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="78fe3-185">Notice that the answer includes the decimal portion of the quotient.</span></span> <span data-ttu-id="78fe3-186">Double biraz daha karmaşık bir ifadesiyle deneyin:</span><span class="sxs-lookup"><span data-stu-id="78fe3-186">Try a slightly more complicated expression with doubles:</span></span>

```csharp
double e = 19;
double f = 23;
double g = 8;
double h = (e  + f) / g;
Console.WriteLine(h);
```

<span data-ttu-id="78fe3-187">Bir çift değer aralığını tamsayı değerleri çok daha fazladır.</span><span class="sxs-lookup"><span data-stu-id="78fe3-187">The range of a double value is much greater than integer values.</span></span> <span data-ttu-id="78fe3-188">Şu ana kadar yazdıklarınızı altına aşağıdaki kodu deneyin:</span><span class="sxs-lookup"><span data-stu-id="78fe3-188">Try the following code below what you've written so far:</span></span>

```csharp
double max = double.MaxValue;
double min = double.MinValue;
Console.WriteLine($"The range of double is {min} to {max}");
```

<span data-ttu-id="78fe3-189">Bu değerleri bilimsel gösterimde yazdırılır.</span><span class="sxs-lookup"><span data-stu-id="78fe3-189">These values are printed out in scientific notation.</span></span> <span data-ttu-id="78fe3-190">Sol tarafındaki sayıya `E` significand değil.</span><span class="sxs-lookup"><span data-stu-id="78fe3-190">The number to the left of the `E` is the significand.</span></span> <span data-ttu-id="78fe3-191">Sağa üs 10 gücünü sayıdır.</span><span class="sxs-lookup"><span data-stu-id="78fe3-191">The number to the right is the exponent, as a power of 10.</span></span> 

<span data-ttu-id="78fe3-192">Yalnızca ondalık sayı gibi olarak matematik hataları yuvarlama çiftleri C# olabilir.</span><span class="sxs-lookup"><span data-stu-id="78fe3-192">Just like decimal numbers in math, doubles in C# can have rounding errors.</span></span> <span data-ttu-id="78fe3-193">Bu kod deneyin:</span><span class="sxs-lookup"><span data-stu-id="78fe3-193">Try this code:</span></span>

```csharp
double third = 1.0 / 3.0;
Console.WriteLine(third);
```

<span data-ttu-id="78fe3-194">Bunu biliyor `0.3` yinelenen tam olarak aynı olup `1/3`.</span><span class="sxs-lookup"><span data-stu-id="78fe3-194">You know that `0.3` repeating is not exactly the same as `1/3`.</span></span>

<span data-ttu-id="78fe3-195">***Challenge***</span><span class="sxs-lookup"><span data-stu-id="78fe3-195">***Challenge***</span></span>

<span data-ttu-id="78fe3-196">Büyük sayılar, küçük sayılar, çarpma ve bölme kullanarak diğer hesaplamalarla deneyin `double` türü.</span><span class="sxs-lookup"><span data-stu-id="78fe3-196">Try other calculations with large numbers, small numbers, multiplication and division using the `double` type.</span></span>  <span data-ttu-id="78fe3-197">Daha karmaşık hesaplamalar deneyin.</span><span class="sxs-lookup"><span data-stu-id="78fe3-197">Try more complicated calculations.</span></span>

<span data-ttu-id="78fe3-198">Sınama ile biraz zaman harcanan sonra yazdıktan ve yeni bir yöntemi yerleştirin kod alın.</span><span class="sxs-lookup"><span data-stu-id="78fe3-198">After you've spent some time with the challenge, take the code you've written and place it in a new method.</span></span> <span data-ttu-id="78fe3-199">Bu yeni yöntem adı `WorkWithDoubles`.</span><span class="sxs-lookup"><span data-stu-id="78fe3-199">Name that new method `WorkWithDoubles`.</span></span>

## <a name="work-with-fixed-point-types"></a><span data-ttu-id="78fe3-200">Sabit noktası türleri ile çalışma</span><span class="sxs-lookup"><span data-stu-id="78fe3-200">Work with fixed point types</span></span>

<span data-ttu-id="78fe3-201">C# temel sayısal türler gördünüz: tamsayılar ve iki katına çıkar.</span><span class="sxs-lookup"><span data-stu-id="78fe3-201">You've seen the basic numeric types in C#: integers and doubles.</span></span>  <span data-ttu-id="78fe3-202">Bilgi edinmek için bir tür: `decimal` türü.</span><span class="sxs-lookup"><span data-stu-id="78fe3-202">There is one other type to learn: the `decimal` type.</span></span> <span data-ttu-id="78fe3-203">`decimal` Türüne sahip daha küçük bir aralık daha iyi kesinlik ancak `double`.</span><span class="sxs-lookup"><span data-stu-id="78fe3-203">The `decimal` type has a smaller range but greater precision than `double`.</span></span> <span data-ttu-id="78fe3-204">Terim **sabit noktası** ondalık (veya ikili noktası) taşınmaz anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="78fe3-204">The term **fixed point** means that the decimal point (or binary point) doesn't move.</span></span> <span data-ttu-id="78fe3-205">Bir göz atalım:</span><span class="sxs-lookup"><span data-stu-id="78fe3-205">Let's take a look:</span></span>

```csharp
decimal min = decimal.MinValue;
decimal max = decimal.MaxValue;
Console.WriteLine($"The range of the decimal type is {min} to {max}");
```

<span data-ttu-id="78fe3-206">Aralık değerinden küçük olduğunu fark `double` türü.</span><span class="sxs-lookup"><span data-stu-id="78fe3-206">Notice that the range is smaller than the `double` type.</span></span> <span data-ttu-id="78fe3-207">Aşağıdaki kod deneyerek decimal türü ile daha iyi kesinlik görebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="78fe3-207">You can see the greater precision with the decimal type by trying the following code:</span></span>

```csharp
double a = 1.0;
double b = 3.0;
Console.WriteLine(a / b);

decimal c = 1.0M;
decimal d = 3.0M;
Console.WriteLine(c / d);
```

<span data-ttu-id="78fe3-208">`M` Numaraları sonekidir nasıl bir sabit kullanması gerektiğini belirtmek `decimal` türü.</span><span class="sxs-lookup"><span data-stu-id="78fe3-208">The `M` suffix on the numbers is how you indicate that a constant should use the `decimal` type.</span></span>

<span data-ttu-id="78fe3-209">Decimal türü kullanarak matematik ondalık konumun sağında daha fazla basamağa sahip olmadığına dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="78fe3-209">Notice that the math using the decimal type has more digits to the right of the decimal point.</span></span> 

<span data-ttu-id="78fe3-210">***Challenge***</span><span class="sxs-lookup"><span data-stu-id="78fe3-210">***Challenge***</span></span>

<span data-ttu-id="78fe3-211">Farklı sayısal türler gördüğünüze göre 2.50 santimetreden, RADIUS olduğu dairenin alanı hesaplar kod yazın.</span><span class="sxs-lookup"><span data-stu-id="78fe3-211">Now that you've seen the different numeric types, write code that calculates the area of a circle whose radius is 2.50 centimeters.</span></span> <span data-ttu-id="78fe3-212">Unutmayın PI ile çarpılmış dairenin alanı kare RADIUS olduğunu.</span><span class="sxs-lookup"><span data-stu-id="78fe3-212">Remember that the area of a circle is the radius squared multiplied by PI.</span></span> <span data-ttu-id="78fe3-213">Bir ipucu: .NET PI için bir sabit içeriyor <xref:System.Math.PI?displayProperty=nameWithType> , bu değer için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="78fe3-213">One hint: .NET contains a constant for PI, <xref:System.Math.PI?displayProperty=nameWithType> that you can use for that value.</span></span> 

<span data-ttu-id="78fe3-214">19 ve 20 arasında bir yanıt almanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="78fe3-214">You should get an answer between 19 and 20.</span></span>
<span data-ttu-id="78fe3-215">Yanıtınız tarafından kontrol edebilirsiniz [Github'da tamamlanmış örnek kodu incelemeden](https://github.com/dotnet/docs/tree/master/samples/csharp/numbers-quickstart/Program.cs#L104-L106)</span><span class="sxs-lookup"><span data-stu-id="78fe3-215">You can check your answer by [looking at the finished sample code on GitHub](https://github.com/dotnet/docs/tree/master/samples/csharp/numbers-quickstart/Program.cs#L104-L106)</span></span>

<span data-ttu-id="78fe3-216">İsterseniz başka bir formüller deneyin.</span><span class="sxs-lookup"><span data-stu-id="78fe3-216">Try some other formulas if you'd like.</span></span> 

<span data-ttu-id="78fe3-217">"Numaraları C# ' ta" Hızlı Başlangıç tamamladınız.</span><span class="sxs-lookup"><span data-stu-id="78fe3-217">You've completed the "Numbers in C#" quickstart.</span></span> <span data-ttu-id="78fe3-218">İle devam edebilirsiniz [dallar ve döngüler](branches-and-loops-local.md) kendi geliştirme ortamında hızlı başlangıç.</span><span class="sxs-lookup"><span data-stu-id="78fe3-218">You can continue with the [Branches and loops](branches-and-loops-local.md) quickstart in your own development environment.</span></span>

<span data-ttu-id="78fe3-219">Aşağıdaki konularda C# numaraları hakkında daha fazla bilgi edinebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="78fe3-219">You can learn more about numbers in C# in the following topics:</span></span>

<span data-ttu-id="78fe3-220">[Tam sayı türleri tablosu](../language-reference/keywords/integral-types-table.md) </span><span class="sxs-lookup"><span data-stu-id="78fe3-220">[Integral Types Table](../language-reference/keywords/integral-types-table.md) </span></span>  
<span data-ttu-id="78fe3-221">[Kayan nokta türleri tablosu](../language-reference/keywords/floating-point-types-table.md) </span><span class="sxs-lookup"><span data-stu-id="78fe3-221">[Floating-Point Types Table](../language-reference/keywords/floating-point-types-table.md) </span></span>  
<span data-ttu-id="78fe3-222">[Yerleşik türler tablosu](../language-reference/keywords/built-in-types-table.md) </span><span class="sxs-lookup"><span data-stu-id="78fe3-222">[Built-In Types Table](../language-reference/keywords/built-in-types-table.md) </span></span>  
<span data-ttu-id="78fe3-223">[Örtük sayısal dönüşümler tablosu](../language-reference/keywords/implicit-numeric-conversions-table.md) </span><span class="sxs-lookup"><span data-stu-id="78fe3-223">[Implicit Numeric Conversions Table](../language-reference/keywords/implicit-numeric-conversions-table.md) </span></span>  
[<span data-ttu-id="78fe3-224">Açık Sayısal Dönüştürmeler Tablosu</span><span class="sxs-lookup"><span data-stu-id="78fe3-224">Explicit Numeric Conversions Table</span></span>](../language-reference/keywords/explicit-numeric-conversions-table.md)

