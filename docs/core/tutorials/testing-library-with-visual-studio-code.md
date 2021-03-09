---
title: Visual Studio Code kullanarak .NET sınıf kitaplığı test etme
description: .NET sınıf kitaplığı için bir birim testi projesi oluşturmak ve çalıştırmak üzere Visual Studio Code ve .NET CLı 'yi nasıl kullanacağınızı öğrenin.
ms.date: 11/17/2020
ms.openlocfilehash: bc8741e11504f94e54ccc45a5ad93408a3fe9309
ms.sourcegitcommit: 1d3af230ec30d8d061be7a887f6ba38a530c4ece
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2021
ms.locfileid: "102511820"
---
# <a name="tutorial-test-a-net-class-library-using-visual-studio-code"></a><span data-ttu-id="7c095-103">Öğretici: Visual Studio Code kullanarak .NET sınıf kitaplığı test etme</span><span class="sxs-lookup"><span data-stu-id="7c095-103">Tutorial: Test a .NET class library using Visual Studio Code</span></span>

<span data-ttu-id="7c095-104">Bu öğreticide, bir çözüme test projesi ekleyerek birim testinin nasıl otomatikleştirilmesi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="7c095-104">This tutorial shows how to automate unit testing by adding a test project to a solution.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="7c095-105">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="7c095-105">Prerequisites</span></span>

- <span data-ttu-id="7c095-106">Bu öğretici, [Visual Studio Code kullanarak bir .NET sınıf kitaplığı oluşturma](library-with-visual-studio-code.md)bölümünde oluşturduğunuz çözümle birlikte kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7c095-106">This tutorial works with the solution that you create in [Create a .NET class library using Visual Studio Code](library-with-visual-studio-code.md).</span></span>

## <a name="create-a-unit-test-project"></a><span data-ttu-id="7c095-107">Birim testi projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="7c095-107">Create a unit test project</span></span>

<span data-ttu-id="7c095-108">Birim testleri geliştirme ve yayımlama sırasında otomatik yazılım testi sağlar.</span><span class="sxs-lookup"><span data-stu-id="7c095-108">Unit tests provide automated software testing during your development and publishing.</span></span> <span data-ttu-id="7c095-109">Bu öğreticide kullandığınız test çerçevesi MSTest.</span><span class="sxs-lookup"><span data-stu-id="7c095-109">The testing framework that you use in this tutorial is MSTest.</span></span> <span data-ttu-id="7c095-110">[MSTest](https://github.com/Microsoft/testfx-docs) , aralarından seçim yapabileceğiniz üç test çerçevelerinden biridir.</span><span class="sxs-lookup"><span data-stu-id="7c095-110">[MSTest](https://github.com/Microsoft/testfx-docs) is one of three test frameworks you can choose from.</span></span> <span data-ttu-id="7c095-111">Diğerleri [xUnit](https://xunit.net/) ve [NUnit](https://nunit.org/)' dir.</span><span class="sxs-lookup"><span data-stu-id="7c095-111">The others are [xUnit](https://xunit.net/) and [nUnit](https://nunit.org/).</span></span>

1. <span data-ttu-id="7c095-112">Visual Studio Code’u başlatın.</span><span class="sxs-lookup"><span data-stu-id="7c095-112">Start Visual Studio Code.</span></span>

1. <span data-ttu-id="7c095-113">`ClassLibraryProjects` [Visual Studio Code kullanarak .NET sınıf kitaplığı oluşturma](library-with-visual-studio-code.md)bölümünde oluşturduğunuz çözümü açın.</span><span class="sxs-lookup"><span data-stu-id="7c095-113">Open the `ClassLibraryProjects` solution you created in [Create a .NET class library using Visual Studio Code](library-with-visual-studio-code.md).</span></span>

1. <span data-ttu-id="7c095-114">"StringLibraryTest" adlı bir birim testi projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="7c095-114">Create a unit test project named "StringLibraryTest".</span></span>

   ```dotnetcli
   dotnet new mstest -o StringLibraryTest
   ```

   <span data-ttu-id="7c095-115">Proje şablonu aşağıdaki kodla bir UnitTest1.cs dosyası oluşturur:</span><span class="sxs-lookup"><span data-stu-id="7c095-115">The project template creates a UnitTest1.cs file with the following code:</span></span>

   ```csharp
   using Microsoft.VisualStudio.TestTools.UnitTesting;

   namespace StringLibraryTest
   {
       [TestClass]
       public class UnitTest1
       {
           [TestMethod]
           public void TestMethod1()
           {
           }
       }
   }
   ```

   <span data-ttu-id="7c095-116">Birim testi şablonu tarafından oluşturulan kaynak kodu aşağıdakileri yapar:</span><span class="sxs-lookup"><span data-stu-id="7c095-116">The source code created by the unit test template does the following:</span></span>

   - <span data-ttu-id="7c095-117"><xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=nameWithType>Birim testi için kullanılan türleri içeren ad alanını içeri aktarır.</span><span class="sxs-lookup"><span data-stu-id="7c095-117">It imports the <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=nameWithType> namespace, which contains the types used for unit testing.</span></span>
   - <span data-ttu-id="7c095-118"><xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute>Özniteliği `UnitTest1` sınıfına uygular.</span><span class="sxs-lookup"><span data-stu-id="7c095-118">It applies the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> attribute to the `UnitTest1` class.</span></span>
   - <span data-ttu-id="7c095-119"><xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute>Tanımlamak için özniteliğini uygular `TestMethod1` .</span><span class="sxs-lookup"><span data-stu-id="7c095-119">It applies the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> attribute to define `TestMethod1`.</span></span>

   <span data-ttu-id="7c095-120">[ [TestClass]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute) ile etiketlenmiş bir test sınıfında [[TestMethod]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) etiketli her bir yöntem, birim testi çalıştırıldığında otomatik olarak yürütülür.</span><span class="sxs-lookup"><span data-stu-id="7c095-120">Each method tagged with [[TestMethod]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) in a test class tagged with [[TestClass]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute) is executed automatically when the unit test is run.</span></span>

1. <span data-ttu-id="7c095-121">Çözüme test projesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="7c095-121">Add the test project to the solution.</span></span>

   ```dotnetcli
   dotnet sln add StringLibraryTest/StringLibraryTest.csproj
   ```

## <a name="add-a-project-reference"></a><span data-ttu-id="7c095-122">Proje başvurusu Ekle</span><span class="sxs-lookup"><span data-stu-id="7c095-122">Add a project reference</span></span>

<span data-ttu-id="7c095-123">Test projesinin sınıfla çalışması için projeye `StringLibrary` bir başvuru ekleyin `StringLibraryTest` `StringLibrary` .</span><span class="sxs-lookup"><span data-stu-id="7c095-123">For the test project to work with the `StringLibrary` class, add a reference in the `StringLibraryTest` project to the `StringLibrary` project.</span></span>

1. <span data-ttu-id="7c095-124">Şu komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="7c095-124">Run the following command:</span></span>

   ```dotnetcli
   dotnet add StringLibraryTest/StringLibraryTest.csproj reference StringLibrary/StringLibrary.csproj
   ```

## <a name="add-and-run-unit-test-methods"></a><span data-ttu-id="7c095-125">Birim testi yöntemleri ekleme ve çalıştırma</span><span class="sxs-lookup"><span data-stu-id="7c095-125">Add and run unit test methods</span></span>

<span data-ttu-id="7c095-126">Visual Studio bir birim testi çalıştırdığında, özniteliğiyle <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> işaretlenmiş bir sınıfta özniteliğiyle işaretlenmiş her metodu yürütür  <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> .</span><span class="sxs-lookup"><span data-stu-id="7c095-126">When Visual Studio runs a unit test, it executes each method that is marked with the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> attribute in a class that is marked with the  <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> attribute.</span></span> <span data-ttu-id="7c095-127">İlk hata bulunduğunda veya yöntemde bulunan tüm testler başarılı olduğunda bir test yöntemi sonlanır.</span><span class="sxs-lookup"><span data-stu-id="7c095-127">A test method ends when the first failure is found or when all tests contained in the method have succeeded.</span></span>

<span data-ttu-id="7c095-128">En yaygın testler, sınıfının üyelerini çağırır <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> .</span><span class="sxs-lookup"><span data-stu-id="7c095-128">The most common tests call members of the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> class.</span></span> <span data-ttu-id="7c095-129">Birçok onaylama yöntemi, biri beklenen test sonucu ve diğeri de gerçek test sonucu olan en az iki parametre içerir.</span><span class="sxs-lookup"><span data-stu-id="7c095-129">Many assert methods include at least two parameters, one of which is the expected test result and the other of which is the actual test result.</span></span> <span data-ttu-id="7c095-130">`Assert`Sınıfın en sık çağrılan yöntemlerin bazıları aşağıdaki tabloda gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="7c095-130">Some of the `Assert` class's most frequently called methods are shown in the following table:</span></span>

| <span data-ttu-id="7c095-131">Onaylama yöntemleri</span><span class="sxs-lookup"><span data-stu-id="7c095-131">Assert methods</span></span>     | <span data-ttu-id="7c095-132">İşlev</span><span class="sxs-lookup"><span data-stu-id="7c095-132">Function</span></span> |
| ------------------ | -------- |
| `Assert.AreEqual`  | <span data-ttu-id="7c095-133">İki değerin veya nesnenin eşit olduğunu doğrular.</span><span class="sxs-lookup"><span data-stu-id="7c095-133">Verifies that two values or objects are equal.</span></span> <span data-ttu-id="7c095-134">Değerler veya nesneler eşitse onaylama başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="7c095-134">The assert fails if the values or objects aren't equal.</span></span> |
| `Assert.AreSame`   | <span data-ttu-id="7c095-135">İki nesne değişkeninin aynı nesneye başvurmasını doğrular.</span><span class="sxs-lookup"><span data-stu-id="7c095-135">Verifies that two object variables refer to the same object.</span></span> <span data-ttu-id="7c095-136">Değişkenler farklı nesnelere başvuru yaptığında onaylama başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="7c095-136">The assert fails if the variables refer to different objects.</span></span> |
| `Assert.IsFalse`   | <span data-ttu-id="7c095-137">Bir koşulun olduğunu doğrular `false` .</span><span class="sxs-lookup"><span data-stu-id="7c095-137">Verifies that a condition is `false`.</span></span> <span data-ttu-id="7c095-138">Koşul ise onaylama başarısız olur `true` .</span><span class="sxs-lookup"><span data-stu-id="7c095-138">The assert fails if the condition is `true`.</span></span> |
| `Assert.IsNotNull` | <span data-ttu-id="7c095-139">Bir nesnenin olmadığını doğrular `null` .</span><span class="sxs-lookup"><span data-stu-id="7c095-139">Verifies that an object isn't `null`.</span></span> <span data-ttu-id="7c095-140">Nesne ise onaylama başarısız olur `null` .</span><span class="sxs-lookup"><span data-stu-id="7c095-140">The assert fails if the object is `null`.</span></span> |

<span data-ttu-id="7c095-141"><xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A?displayProperty=nameWithType>Yöntemi bir test yönteminde, oluşturması beklenen özel durum türünü belirtmek için de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7c095-141">You can also use the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A?displayProperty=nameWithType> method in a test method to indicate the type of exception it's expected to throw.</span></span> <span data-ttu-id="7c095-142">Belirtilen özel durum atılmazsa, test başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="7c095-142">The test fails if the specified exception isn't thrown.</span></span>

<span data-ttu-id="7c095-143">Yöntemi test ederken `StringLibrary.StartsWithUpper` , büyük harf karakteriyle başlayan bir dizi dize sağlamak istersiniz.</span><span class="sxs-lookup"><span data-stu-id="7c095-143">In testing the `StringLibrary.StartsWithUpper` method, you want to provide a number of strings that begin with an uppercase character.</span></span> <span data-ttu-id="7c095-144">Yöntemi bu durumlarda Return olarak beklediğinizi ve `true` <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue%2A?displayProperty=nameWithType> yöntemi çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7c095-144">You expect the method to return `true` in these cases, so you can call the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="7c095-145">Benzer şekilde, büyük harfli bir karakter ile başlayan bir dizi dize sağlamak istersiniz.</span><span class="sxs-lookup"><span data-stu-id="7c095-145">Similarly, you want to provide a number of strings that begin with something other than an uppercase character.</span></span> <span data-ttu-id="7c095-146">Yöntemi bu durumlarda Return olarak beklediğinizi ve `false` <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse%2A?displayProperty=nameWithType> yöntemi çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7c095-146">You expect the method to return `false` in these cases, so you can call the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="7c095-147">Kitaplık yönteminiz dizeleri yaptığından, ayrıca [boş bir dizeyi ( `String.Empty` )](xref:System.String.Empty) ve bir dizeyi başarılı bir şekilde işleyeceğinden emin olmak istersiniz `null` .</span><span class="sxs-lookup"><span data-stu-id="7c095-147">Since your library method handles strings, you also want to make sure that it successfully handles an [empty string (`String.Empty`)](xref:System.String.Empty) and a `null` string.</span></span> <span data-ttu-id="7c095-148">Boş bir dize, karakteri olmayan ve 0 olan bir dizedir <xref:System.String.Length> .</span><span class="sxs-lookup"><span data-stu-id="7c095-148">An empty string is one that has no characters and whose <xref:System.String.Length> is 0.</span></span> <span data-ttu-id="7c095-149">Bir `null` dize başlatılmamış bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="7c095-149">A `null` string is one that hasn't been initialized.</span></span> <span data-ttu-id="7c095-150">`StartsWithUpper`Doğrudan statik bir yöntem olarak çağırabilir ve tek bir <xref:System.String> bağımsız değişken geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7c095-150">You can call `StartsWithUpper` directly as a static method and pass a single <xref:System.String> argument.</span></span> <span data-ttu-id="7c095-151">Ya da `StartsWithUpper` öğesine atanan bir değişkende bir genişletme yöntemi olarak çağırabilirsiniz `string` `null` .</span><span class="sxs-lookup"><span data-stu-id="7c095-151">Or you can call `StartsWithUpper` as an extension method on a `string` variable assigned to `null`.</span></span>

<span data-ttu-id="7c095-152">Her biri <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> bir dize dizisindeki her öğe için bir yöntem çağıran üç yöntem tanımlayacaksınız.</span><span class="sxs-lookup"><span data-stu-id="7c095-152">You'll define three methods, each of which calls an <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> method for each element in a string array.</span></span> <span data-ttu-id="7c095-153">Test hatası durumunda görüntülenecek bir hata iletisi belirtmenize imkan tanıyan bir yöntem aşırı yüklemesi çağıracaksınız.</span><span class="sxs-lookup"><span data-stu-id="7c095-153">You'll call a method overload that lets you specify an error message to be displayed in case of test failure.</span></span> <span data-ttu-id="7c095-154">İleti, hataya neden olan dizeyi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="7c095-154">The message identifies the string that caused the failure.</span></span>

<span data-ttu-id="7c095-155">Test yöntemleri oluşturmak için:</span><span class="sxs-lookup"><span data-stu-id="7c095-155">To create the test methods:</span></span>

1. <span data-ttu-id="7c095-156">*Stringlibrarytest/UnitTest1. cs* ' i açın ve tüm kodu aşağıdaki kodla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="7c095-156">Open *StringLibraryTest/UnitTest1.cs* and replace all of the code with the following code.</span></span>

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/StringLibraryTest/UnitTest1.cs":::

   <span data-ttu-id="7c095-157">Yöntemdeki büyük harfli karakterlerin testi, `TestStartsWithUpper` Yunanca Büyük Harf Alpha (u + 0391) ve Kiril Büyük harf em (u + 041C) içerir.</span><span class="sxs-lookup"><span data-stu-id="7c095-157">The test of uppercase characters in the `TestStartsWithUpper` method includes the Greek capital letter alpha (U+0391) and the Cyrillic capital letter EM (U+041C).</span></span> <span data-ttu-id="7c095-158">Yöntemdeki küçük harfli karakterlerin testi `TestDoesNotStartWithUpper` Yunanca Küçük Harf Alpha (u + 03B1) ve Kiril Küçük harf GHE (u + 0433) içerir.</span><span class="sxs-lookup"><span data-stu-id="7c095-158">The test of lowercase characters in the `TestDoesNotStartWithUpper` method includes the Greek small letter alpha (U+03B1) and the Cyrillic small letter Ghe (U+0433).</span></span>

1. <span data-ttu-id="7c095-159">Yaptığınız değişiklikleri kaydedin.</span><span class="sxs-lookup"><span data-stu-id="7c095-159">Save your changes.</span></span>

1. <span data-ttu-id="7c095-160">Testleri çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="7c095-160">Run the tests:</span></span>

   ```dotnetcli
   dotnet test StringLibraryTest/StringLibraryTest.csproj
   ```

   <span data-ttu-id="7c095-161">Terminal çıktısı tüm testlerin geçtiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="7c095-161">The terminal output shows that all tests passed.</span></span>

   ```output
   Starting test execution, please wait...
   A total of 1 test files matched the specified pattern.

   Passed!  - Failed:     0, Passed:     3, Skipped:     0, Total:     3, Duration: 3 ms - StringLibraryTest.dll (net5.0)
   ```

## <a name="handle-test-failures"></a><span data-ttu-id="7c095-162">Test başarısızlıklarını işle</span><span class="sxs-lookup"><span data-stu-id="7c095-162">Handle test failures</span></span>

<span data-ttu-id="7c095-163">Test odaklı geliştirme (TDD) yapıyorsanız, önce testleri yazarsınız ve ilk kez çalıştırdığınızda başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="7c095-163">If you're doing test-driven development (TDD), you write tests first and they fail the first time you run them.</span></span> <span data-ttu-id="7c095-164">Sonra, uygulamayı başarılı hale getiren uygulamaya kod eklersiniz.</span><span class="sxs-lookup"><span data-stu-id="7c095-164">Then you add code to the app that makes the test succeed.</span></span> <span data-ttu-id="7c095-165">Bu öğreticide, doğrulaması yaptığı uygulama kodunu yazdıktan sonra test başarısız olduğunu görmediyseniz testi oluşturdunuz.</span><span class="sxs-lookup"><span data-stu-id="7c095-165">For this tutorial, you created the test after writing the app code that it validates, so you haven't seen the test fail.</span></span> <span data-ttu-id="7c095-166">Başarısız olması beklendiğinde testin başarısız olduğunu doğrulamak için, test girişine geçersiz bir değer ekleyin.</span><span class="sxs-lookup"><span data-stu-id="7c095-166">To validate that a test fails when you expect it to fail, add an invalid value to the test input.</span></span>

1. <span data-ttu-id="7c095-167">`words`Yöntemdeki diziyi, `TestDoesNotStartWithUpper` "Error" dizesini içerecek şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="7c095-167">Modify the `words` array in the `TestDoesNotStartWithUpper` method to include the string "Error".</span></span>

   ```csharp
   string[] words = { "alphabet", "Error", "zebra", "abc", "αυτοκινητοβιομηχανία", "государство",
                      "1234", ".", ";", " " };
   ```

1. <span data-ttu-id="7c095-168">Testleri çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="7c095-168">Run the tests:</span></span>

   ```dotnetcli
   dotnet test StringLibraryTest/StringLibraryTest.csproj
   ```

   <span data-ttu-id="7c095-169">Terminal çıktısı bir testin başarısız olduğunu gösterir ve başarısız test için bir hata iletisi sağlar: "onaylama. IsFalse başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="7c095-169">The terminal output shows that one test fails, and it provides an error message for the failed test: "Assert.IsFalse failed.</span></span> <span data-ttu-id="7c095-170">' Error ' bekleniyor: false; gerçek: true ".</span><span class="sxs-lookup"><span data-stu-id="7c095-170">Expected for 'Error': false; actual: True".</span></span> <span data-ttu-id="7c095-171">Hata nedeniyle "hata" sonunda dizide hiçbir dize sınanmadı.</span><span class="sxs-lookup"><span data-stu-id="7c095-171">Because of the failure, no strings in the array after "Error" were tested.</span></span>

   ```output
   Starting test execution, please wait...
   A total of 1 test files matched the specified pattern.
     Failed TestDoesNotStartWithUpper [28 ms]
     Error Message:
      Assert.IsFalse failed. Expected for 'Error': false; Actual: True
     Stack Trace:
        at StringLibraryTest.UnitTest1.TestDoesNotStartWithUpper() in C:\ClassLibraryProjects\StringLibraryTest\UnitTest1.cs:line 33

   Failed!  - Failed:     1, Passed:     2, Skipped:     0, Total:     3, Duration: 31 ms - StringLibraryTest.dll (net5.0)
   ```

1. <span data-ttu-id="7c095-172">Adım 1 ' de eklediğiniz "Error" dizesini kaldırın.</span><span class="sxs-lookup"><span data-stu-id="7c095-172">Remove the string "Error" that you added in step 1.</span></span> <span data-ttu-id="7c095-173">Testi ve test geçişini yeniden çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="7c095-173">Rerun the test and the tests pass.</span></span>

## <a name="test-the-release-version-of-the-library"></a><span data-ttu-id="7c095-174">Kitaplığın yayın sürümünü test etme</span><span class="sxs-lookup"><span data-stu-id="7c095-174">Test the Release version of the library</span></span>

<span data-ttu-id="7c095-175">Artık, kitaplığın hata ayıklama derlemesini çalıştırırken testlerin başarılı olduğuna göre, bu testleri kitaplığın yayın derlemesi için ek bir zaman çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="7c095-175">Now that the tests have all passed when running the Debug build of the library, run the tests an additional time against the Release build of the library.</span></span> <span data-ttu-id="7c095-176">Derleyici iyileştirmeleri dahil olmak üzere bir dizi etken bazen hata ayıklama ve yayın yapıları arasında farklı davranışlar üretebilir.</span><span class="sxs-lookup"><span data-stu-id="7c095-176">A number of factors, including compiler optimizations, can sometimes produce different behavior between Debug and Release builds.</span></span>

1. <span data-ttu-id="7c095-177">Testleri yayın yapı yapılandırmasıyla çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="7c095-177">Run the tests with the Release build configuration:</span></span>

   ```dotnetcli
   dotnet test StringLibraryTest/StringLibraryTest.csproj --configuration Release
   ```

   <span data-ttu-id="7c095-178">Testler geçer.</span><span class="sxs-lookup"><span data-stu-id="7c095-178">The tests pass.</span></span>

## <a name="debug-tests"></a><span data-ttu-id="7c095-179">Hata ayıklama testleri</span><span class="sxs-lookup"><span data-stu-id="7c095-179">Debug tests</span></span>

<span data-ttu-id="7c095-180">IDE 'niz olarak Visual Studio Code kullanıyorsanız, birim testi projenizi kullanarak kodun hatalarını ayıklamak için [Visual Studio Code kullanarak bir .NET konsol uygulamasında hata ayıklama](debugging-with-visual-studio-code.md) sırasında gösterilen aynı işlemi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7c095-180">If you're using Visual Studio Code as your IDE, you can use the same process shown in [Debug a .NET console application using Visual Studio Code](debugging-with-visual-studio-code.md) to debug code using your unit test project.</span></span> <span data-ttu-id="7c095-181">*Gösterimi* uygulama projesini başlatmak yerine *stringlibrarytest/UnitTest1. cs* açın ve 7 ve 8 satırları arasında **Tüm Testleri Çalıştır** ' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="7c095-181">Instead of starting the *ShowCase* app project, open *StringLibraryTest/UnitTest1.cs*, and select **Run All Tests** between lines 7 and 8.</span></span> <span data-ttu-id="7c095-182">Bunu bulamıyorsanız, <kbd>CTRL</kbd> + <kbd>SHIFT</kbd> + <kbd>P</kbd> tuşlarına basarak komut paletini açın ve **yeniden yükle penceresini** girin.</span><span class="sxs-lookup"><span data-stu-id="7c095-182">If you're unable to find it, press <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> to open the command palette and enter **Reload Window**.</span></span>

<span data-ttu-id="7c095-183">Visual Studio Code, test projesini hata ayıklayıcı ekli olarak başlatır.</span><span class="sxs-lookup"><span data-stu-id="7c095-183">Visual Studio Code starts the test project with the debugger attached.</span></span> <span data-ttu-id="7c095-184">Yürütme, test projesine veya temeldeki kitaplık koduna eklediğiniz herhangi bir kesme noktasında durur.</span><span class="sxs-lookup"><span data-stu-id="7c095-184">Execution will stop at any breakpoint you've added to the test project or the underlying library code.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="7c095-185">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="7c095-185">Additional resources</span></span>

* [<span data-ttu-id="7c095-186">.NET 'te birim testi</span><span class="sxs-lookup"><span data-stu-id="7c095-186">Unit testing in .NET</span></span>](../testing/index.md)

## <a name="next-steps"></a><span data-ttu-id="7c095-187">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="7c095-187">Next steps</span></span>

<span data-ttu-id="7c095-188">Bu öğreticide, birim bir sınıf kitaplığı test edilmiştir.</span><span class="sxs-lookup"><span data-stu-id="7c095-188">In this tutorial, you unit tested a class library.</span></span> <span data-ttu-id="7c095-189">Bir paket olarak [NuGet](https://nuget.org) 'e yayımlayarak, kitaplığı başkaları için kullanılabilir hale getirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7c095-189">You can make the library available to others by publishing it to [NuGet](https://nuget.org) as a package.</span></span> <span data-ttu-id="7c095-190">Nasıl yapılacağını öğrenmek için bir NuGet öğreticisini izleyin:</span><span class="sxs-lookup"><span data-stu-id="7c095-190">To learn how, follow a NuGet tutorial:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="7c095-191">DotNet CLı kullanarak bir paket oluşturma ve yayımlama</span><span class="sxs-lookup"><span data-stu-id="7c095-191">Create and publish a package using the dotnet CLI</span></span>](/nuget/quickstart/create-and-publish-a-package-using-the-dotnet-cli)

<span data-ttu-id="7c095-192">Bir kitaplığı bir NuGet paketi olarak yayımlarsanız, diğerleri onu yükleyebilir ve kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="7c095-192">If you publish a library as a NuGet package, others can install and use it.</span></span> <span data-ttu-id="7c095-193">Nasıl yapılacağını öğrenmek için bir NuGet öğreticisini izleyin:</span><span class="sxs-lookup"><span data-stu-id="7c095-193">To learn how, follow a NuGet tutorial:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="7c095-194">DotNet CLı kullanarak bir paket yükleyip kullanma</span><span class="sxs-lookup"><span data-stu-id="7c095-194">Install and use a package using the dotnet CLI</span></span>](/nuget/quickstart/install-and-use-a-package-using-the-dotnet-cli)

<span data-ttu-id="7c095-195">Bir kitaplığın paket olarak dağıtılması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="7c095-195">A library doesn't have to be distributed as a package.</span></span> <span data-ttu-id="7c095-196">Onu kullanan bir konsol uygulamasıyla paketlenmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="7c095-196">It can be bundled with a console app that uses it.</span></span> <span data-ttu-id="7c095-197">Bir konsol uygulamasını yayımlamayı öğrenmek için bu serideki önceki öğreticiye bakın:</span><span class="sxs-lookup"><span data-stu-id="7c095-197">To learn how to publish a console app, see the earlier tutorial in this series:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="7c095-198">Visual Studio Code kullanarak bir .NET konsol uygulaması yayımlama</span><span class="sxs-lookup"><span data-stu-id="7c095-198">Publish a .NET console application using Visual Studio Code</span></span>](publishing-with-visual-studio-code.md)
