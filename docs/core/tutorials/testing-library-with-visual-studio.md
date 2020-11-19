---
title: Visual Studio kullanarak .NET sınıf kitaplığı test etme
description: Visual Studio 'Yu kullanarak bir .NET sınıf kitaplığı için bir birim testi projesi oluşturma ve çalıştırma hakkında bilgi edinin.
ms.date: 11/18/2020
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: 3d56627b937fa0ad5f8002f396ce617e09ce9d2c
ms.sourcegitcommit: 5114e7847e0ff8ddb8c266802d47af78567949cf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/19/2020
ms.locfileid: "94916133"
---
# <a name="tutorial-test-a-net-class-library-with-net-using-visual-studio"></a><span data-ttu-id="0e756-103">Öğretici: Visual Studio kullanarak .NET sınıf kitaplığını .NET ile test etme</span><span class="sxs-lookup"><span data-stu-id="0e756-103">Tutorial: Test a .NET class library with .NET using Visual Studio</span></span>

<span data-ttu-id="0e756-104">Bu öğreticide, bir çözüme test projesi ekleyerek birim testinin nasıl otomatikleştirilmesi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="0e756-104">This tutorial shows how to automate unit testing by adding a test project to a solution.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="0e756-105">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="0e756-105">Prerequisites</span></span>

- <span data-ttu-id="0e756-106">Bu öğretici, [Visual Studio kullanarak bir .NET sınıf kitaplığı oluşturma](library-with-visual-studio.md)bölümünde oluşturduğunuz çözümle birlikte kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0e756-106">This tutorial works with the solution that you create in [Create a .NET class library using Visual Studio](library-with-visual-studio.md).</span></span>

## <a name="create-a-unit-test-project"></a><span data-ttu-id="0e756-107">Birim testi projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="0e756-107">Create a unit test project</span></span>

<span data-ttu-id="0e756-108">Birim testleri geliştirme ve yayımlama sırasında otomatik yazılım testi sağlar.</span><span class="sxs-lookup"><span data-stu-id="0e756-108">Unit tests provide automated software testing during your development and publishing.</span></span> <span data-ttu-id="0e756-109">[MSTest](https://github.com/Microsoft/testfx-docs) , aralarından seçim yapabileceğiniz üç test çerçevelerinden biridir.</span><span class="sxs-lookup"><span data-stu-id="0e756-109">[MSTest](https://github.com/Microsoft/testfx-docs) is one of three test frameworks you can choose from.</span></span> <span data-ttu-id="0e756-110">Diğerleri [xUnit](https://xunit.net/) ve [NUnit](https://nunit.org/)' dir.</span><span class="sxs-lookup"><span data-stu-id="0e756-110">The others are [xUnit](https://xunit.net/) and [nUnit](https://nunit.org/).</span></span>

1. <span data-ttu-id="0e756-111">Visual Studio’yu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="0e756-111">Start Visual Studio.</span></span>

1. <span data-ttu-id="0e756-112">`ClassLibraryProjects` [Visual Studio 'yu kullanarak .NET sınıf kitaplığı oluşturma](library-with-visual-studio.md)bölümünde oluşturduğunuz çözümü açın.</span><span class="sxs-lookup"><span data-stu-id="0e756-112">Open the `ClassLibraryProjects` solution you created in [Create a .NET class library using Visual Studio](library-with-visual-studio.md).</span></span>

1. <span data-ttu-id="0e756-113">Çözüme "StringLibraryTest" adlı yeni bir birim test projesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="0e756-113">Add a new unit test project named "StringLibraryTest" to the solution.</span></span>

   1. <span data-ttu-id="0e756-114">**Çözüm Gezgini** çözüme sağ tıklayın ve **Add**  >  **Yeni proje** Ekle ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="0e756-114">Right-click on the solution in **Solution Explorer** and select **Add** > **New project**.</span></span>

   1. <span data-ttu-id="0e756-115">**Yeni Proje Ekle** sayfasında, arama kutusuna **MSTest** yazın.</span><span class="sxs-lookup"><span data-stu-id="0e756-115">On the **Add a new project** page, enter **mstest** in the search box.</span></span> <span data-ttu-id="0e756-116">Dil listesinden **C#** veya **Visual Basic** seçin ve ardından platform listesinden **tüm platformlar** ' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="0e756-116">Choose **C#** or **Visual Basic** from the Language list, and then choose **All platforms** from the Platform list.</span></span>

   1. <span data-ttu-id="0e756-117">**Birim testi proje** şablonunu seçin ve ardından **İleri**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="0e756-117">Choose the **Unit Test Project** template, and then choose **Next**.</span></span>

   1. <span data-ttu-id="0e756-118">**Yeni projenizi yapılandırın** sayfasında, **Proje adı** kutusuna **stringlibrarytest** girin.</span><span class="sxs-lookup"><span data-stu-id="0e756-118">On the **Configure your new project** page, enter **StringLibraryTest** in the **Project name** box.</span></span> <span data-ttu-id="0e756-119">Ardından **İleri**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="0e756-119">Then choose **Next**.</span></span>

   1. <span data-ttu-id="0e756-120">**Ek bilgiler** sayfasında, **hedef çerçeve** kutusunda **.NET 5,0 (geçerli)** seçeneğini belirleyin.</span><span class="sxs-lookup"><span data-stu-id="0e756-120">On the **Additional information** page, select **.NET 5.0 (Current)** in the **Target Framework** box.</span></span> <span data-ttu-id="0e756-121">Ardından **Oluştur**’u seçin.</span><span class="sxs-lookup"><span data-stu-id="0e756-121">Then choose **Create**.</span></span>

1. <span data-ttu-id="0e756-122">Visual Studio projeyi oluşturur ve kod penceresinde aşağıdaki kodla sınıf dosyasını açar.</span><span class="sxs-lookup"><span data-stu-id="0e756-122">Visual Studio creates the project and opens the class file in the code window with the following code.</span></span> <span data-ttu-id="0e756-123">Kullanmak istediğiniz dil gösterilmiyorsa sayfanın en üstündeki dil seçicisini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="0e756-123">If the language you want to use is not shown, change the language selector at the top of the page.</span></span>

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

   ```vb
   Imports Microsoft.VisualStudio.TestTools.UnitTesting

   Namespace StringLibraryTest
       <TestClass>
       Public Class UnitTest1
           <TestMethod>
           Sub TestSub()

           End Sub
       End Class
   End Namespace
   ```

   <span data-ttu-id="0e756-124">Birim testi şablonu tarafından oluşturulan kaynak kodu aşağıdakileri yapar:</span><span class="sxs-lookup"><span data-stu-id="0e756-124">The source code created by the unit test template does the following:</span></span>

   - <span data-ttu-id="0e756-125"><xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=nameWithType>Birim testi için kullanılan türleri içeren ad alanını içeri aktarır.</span><span class="sxs-lookup"><span data-stu-id="0e756-125">It imports the <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=nameWithType> namespace, which contains the types used for unit testing.</span></span>
   - <span data-ttu-id="0e756-126"><xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute>Özniteliği `UnitTest1` sınıfına uygular.</span><span class="sxs-lookup"><span data-stu-id="0e756-126">It applies the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> attribute to the `UnitTest1` class.</span></span>
   - <span data-ttu-id="0e756-127"><xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> `TestMethod1` C# veya Visual Basic içinde tanımlamak için özniteliğini uygular `TestSub` .</span><span class="sxs-lookup"><span data-stu-id="0e756-127">It applies the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> attribute to define `TestMethod1` in C# or `TestSub` in Visual Basic.</span></span>

   <span data-ttu-id="0e756-128">[ [TestClass]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute) ile etiketlenmiş bir test sınıfında [[TestMethod]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) etiketli her bir yöntem, birim testi çalıştırıldığında otomatik olarak yürütülür.</span><span class="sxs-lookup"><span data-stu-id="0e756-128">Each method tagged with [[TestMethod]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) in a test class tagged with [[TestClass]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute) is executed automatically when the unit test is run.</span></span>

## <a name="add-a-project-reference"></a><span data-ttu-id="0e756-129">Proje başvurusu Ekle</span><span class="sxs-lookup"><span data-stu-id="0e756-129">Add a project reference</span></span>

<span data-ttu-id="0e756-130">Test projesinin sınıfla çalışması için `StringLibrary` , **Stringlibrarytest** projesinde projeye bir başvuru ekleyin `StringLibrary` .</span><span class="sxs-lookup"><span data-stu-id="0e756-130">For the test project to work with the `StringLibrary` class, add a reference in the **StringLibraryTest** project to the `StringLibrary` project.</span></span>

1. <span data-ttu-id="0e756-131">**Çözüm Gezgini**, **stringlibrarytest** projesinin **Bağımlılıklar** düğümüne sağ tıklayın ve bağlam menüsünden **proje başvurusu Ekle** ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="0e756-131">In **Solution Explorer**, right-click the **Dependencies** node of the **StringLibraryTest** project and select **Add Project Reference** from the context menu.</span></span>

1. <span data-ttu-id="0e756-132">**Başvuru Yöneticisi** iletişim kutusunda, **Projeler** düğümünü genişletin ve **StringLibrary**' ın yanındaki kutuyu seçin.</span><span class="sxs-lookup"><span data-stu-id="0e756-132">In the **Reference Manager** dialog, expand the **Projects** node, and select the box next to **StringLibrary**.</span></span> <span data-ttu-id="0e756-133">Derlemeye başvuru eklemek `StringLibrary` derleyicinin **Stringlibrarytest** projesini derlerken **StringLibrary** yöntemlerini bulmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="0e756-133">Adding a reference to the `StringLibrary` assembly allows the compiler to find **StringLibrary** methods while compiling the **StringLibraryTest** project.</span></span>

1. <span data-ttu-id="0e756-134">**Tamam**’ı seçin.</span><span class="sxs-lookup"><span data-stu-id="0e756-134">Select **OK**.</span></span>

## <a name="add-and-run-unit-test-methods"></a><span data-ttu-id="0e756-135">Birim testi yöntemleri ekleme ve çalıştırma</span><span class="sxs-lookup"><span data-stu-id="0e756-135">Add and run unit test methods</span></span>

<span data-ttu-id="0e756-136">Visual Studio bir birim testi çalıştırdığında, özniteliğiyle <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> işaretlenmiş bir sınıfta özniteliğiyle işaretlenmiş her metodu yürütür  <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> .</span><span class="sxs-lookup"><span data-stu-id="0e756-136">When Visual Studio runs a unit test, it executes each method that is marked with the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> attribute in a class that is marked with the  <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> attribute.</span></span> <span data-ttu-id="0e756-137">İlk hata bulunduğunda veya yöntemde bulunan tüm testler başarılı olduğunda bir test yöntemi sonlanır.</span><span class="sxs-lookup"><span data-stu-id="0e756-137">A test method ends when the first failure is found or when all tests contained in the method have succeeded.</span></span>

<span data-ttu-id="0e756-138">En yaygın testler, sınıfının üyelerini çağırır <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> .</span><span class="sxs-lookup"><span data-stu-id="0e756-138">The most common tests call members of the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> class.</span></span> <span data-ttu-id="0e756-139">Birçok onaylama yöntemi, biri beklenen test sonucu ve diğeri de gerçek test sonucu olan en az iki parametre içerir.</span><span class="sxs-lookup"><span data-stu-id="0e756-139">Many assert methods include at least two parameters, one of which is the expected test result and the other of which is the actual test result.</span></span> <span data-ttu-id="0e756-140">`Assert`Sınıfın en sık çağrılan yöntemlerin bazıları aşağıdaki tabloda gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="0e756-140">Some of the `Assert` class's most frequently called methods are shown in the following table:</span></span>

| <span data-ttu-id="0e756-141">Onaylama yöntemleri</span><span class="sxs-lookup"><span data-stu-id="0e756-141">Assert methods</span></span>     | <span data-ttu-id="0e756-142">İşlev</span><span class="sxs-lookup"><span data-stu-id="0e756-142">Function</span></span> |
| ------------------ | -------- |
| `Assert.AreEqual`  | <span data-ttu-id="0e756-143">İki değerin veya nesnenin eşit olduğunu doğrular.</span><span class="sxs-lookup"><span data-stu-id="0e756-143">Verifies that two values or objects are equal.</span></span> <span data-ttu-id="0e756-144">Değerler veya nesneler eşitse onaylama başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="0e756-144">The assert fails if the values or objects aren't equal.</span></span> |
| `Assert.AreSame`   | <span data-ttu-id="0e756-145">İki nesne değişkeninin aynı nesneye başvurmasını doğrular.</span><span class="sxs-lookup"><span data-stu-id="0e756-145">Verifies that two object variables refer to the same object.</span></span> <span data-ttu-id="0e756-146">Değişkenler farklı nesnelere başvuru yaptığında onaylama başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="0e756-146">The assert fails if the variables refer to different objects.</span></span> |
| `Assert.IsFalse`   | <span data-ttu-id="0e756-147">Bir koşulun olduğunu doğrular `false` .</span><span class="sxs-lookup"><span data-stu-id="0e756-147">Verifies that a condition is `false`.</span></span> <span data-ttu-id="0e756-148">Koşul ise onaylama başarısız olur `true` .</span><span class="sxs-lookup"><span data-stu-id="0e756-148">The assert fails if the condition is `true`.</span></span> |
| `Assert.IsNotNull` | <span data-ttu-id="0e756-149">Bir nesnenin olmadığını doğrular `null` .</span><span class="sxs-lookup"><span data-stu-id="0e756-149">Verifies that an object isn't `null`.</span></span> <span data-ttu-id="0e756-150">Nesne ise onaylama başarısız olur `null` .</span><span class="sxs-lookup"><span data-stu-id="0e756-150">The assert fails if the object is `null`.</span></span> |

<span data-ttu-id="0e756-151"><xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A?displayProperty=nameWithType>Yöntemi bir test yönteminde, oluşturması beklenen özel durum türünü belirtmek için de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0e756-151">You can also use the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A?displayProperty=nameWithType> method in a test method to indicate the type of exception it's expected to throw.</span></span> <span data-ttu-id="0e756-152">Belirtilen özel durum atılmazsa, test başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="0e756-152">The test fails if the specified exception isn't thrown.</span></span>

<span data-ttu-id="0e756-153">Yöntemi test ederken `StringLibrary.StartsWithUpper` , büyük harf karakteriyle başlayan bir dizi dize sağlamak istersiniz.</span><span class="sxs-lookup"><span data-stu-id="0e756-153">In testing the `StringLibrary.StartsWithUpper` method, you want to provide a number of strings that begin with an uppercase character.</span></span> <span data-ttu-id="0e756-154">Yöntemi bu durumlarda Return olarak beklediğinizi ve `true` <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue%2A?displayProperty=nameWithType> yöntemi çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0e756-154">You expect the method to return `true` in these cases, so you can call the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="0e756-155">Benzer şekilde, büyük harfli bir karakter ile başlayan bir dizi dize sağlamak istersiniz.</span><span class="sxs-lookup"><span data-stu-id="0e756-155">Similarly, you want to provide a number of strings that begin with something other than an uppercase character.</span></span> <span data-ttu-id="0e756-156">Yöntemi bu durumlarda Return olarak beklediğinizi ve `false` <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse%2A?displayProperty=nameWithType> yöntemi çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0e756-156">You expect the method to return `false` in these cases, so you can call the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="0e756-157">Kitaplık yönteminiz dizeleri yaptığından, ayrıca [boş bir dizeyi ( `String.Empty` )](xref:System.String.Empty)başarılı bir şekilde (), karakteri olmayan ve 0 olan geçerli bir dize <xref:System.String.Length> ve başlatılmamış bir dize de işlemesini sağlamak istersiniz `null` .</span><span class="sxs-lookup"><span data-stu-id="0e756-157">Since your library method handles strings, you also want to make sure that it successfully handles an [empty string (`String.Empty`)](xref:System.String.Empty), a valid string that has no characters and whose <xref:System.String.Length> is 0, and a `null` string that hasn't been initialized.</span></span> <span data-ttu-id="0e756-158">`StartsWithUpper`Doğrudan statik bir yöntem olarak çağırabilir ve tek bir <xref:System.String> bağımsız değişken geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0e756-158">You can call `StartsWithUpper` directly as a static method and pass a single <xref:System.String> argument.</span></span> <span data-ttu-id="0e756-159">Ya da `StartsWithUpper` öğesine atanan bir değişkende bir genişletme yöntemi olarak çağırabilirsiniz `string` `null` .</span><span class="sxs-lookup"><span data-stu-id="0e756-159">Or you can call `StartsWithUpper` as an extension method on a `string` variable assigned to `null`.</span></span>

<span data-ttu-id="0e756-160">Her biri <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> bir dize dizisindeki her öğe için bir yöntem çağıran üç yöntem tanımlayacaksınız.</span><span class="sxs-lookup"><span data-stu-id="0e756-160">You'll define three methods, each of which calls an <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> method for each element in a string array.</span></span> <span data-ttu-id="0e756-161">Test hatası durumunda görüntülenecek bir hata iletisi belirtmenize imkan tanıyan bir yöntem aşırı yüklemesi çağıracaksınız.</span><span class="sxs-lookup"><span data-stu-id="0e756-161">You'll call a method overload that lets you specify an error message to be displayed in case of test failure.</span></span> <span data-ttu-id="0e756-162">İleti, hataya neden olan dizeyi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="0e756-162">The message identifies the string that caused the failure.</span></span>

<span data-ttu-id="0e756-163">Test yöntemleri oluşturmak için:</span><span class="sxs-lookup"><span data-stu-id="0e756-163">To create the test methods:</span></span>

1. <span data-ttu-id="0e756-164">*UnitTest1.cs* veya *UnitTest1. vb* kodu penceresinde, kodu aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="0e756-164">In the *UnitTest1.cs* or *UnitTest1.vb* code window, replace the code with the following code:</span></span>

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/StringLibraryTest/UnitTest1.cs":::
   :::code language="vb" source="./snippets/library-with-visual-studio/vb/StringLibraryTest/UnitTest1.vb":::

   <span data-ttu-id="0e756-165">Yöntemdeki büyük harfli karakterlerin testi, `TestStartsWithUpper` Yunanca Büyük Harf Alpha (u + 0391) ve Kiril Büyük harf em (u + 041C) içerir.</span><span class="sxs-lookup"><span data-stu-id="0e756-165">The test of uppercase characters in the `TestStartsWithUpper` method includes the Greek capital letter alpha (U+0391) and the Cyrillic capital letter EM (U+041C).</span></span> <span data-ttu-id="0e756-166">Yöntemdeki küçük harfli karakterlerin testi `TestDoesNotStartWithUpper` Yunanca Küçük Harf Alpha (u + 03B1) ve Kiril Küçük harf GHE (u + 0433) içerir.</span><span class="sxs-lookup"><span data-stu-id="0e756-166">The test of lowercase characters in the `TestDoesNotStartWithUpper` method includes the Greek small letter alpha (U+03B1) and the Cyrillic small letter Ghe (U+0433).</span></span>

1. <span data-ttu-id="0e756-167">Menü çubuğunda **Dosya**  >  **Kaydet UnitTest1.cs as** veya **Dosya**  >  **Kaydet UnitTest1. vb**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="0e756-167">On the menu bar, select **File** > **Save UnitTest1.cs As** or **File** > **Save UnitTest1.vb As**.</span></span> <span data-ttu-id="0e756-168">**Dosyayı farklı kaydet** Iletişim kutusunda **Kaydet** düğmesinin yanındaki oku seçin ve **kodlamayla kaydet**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="0e756-168">In the **Save File As** dialog, select the arrow beside the **Save** button, and select **Save with Encoding**.</span></span>

   > [!div class="mx-imgBorder"]
   > :::image type="content" source="./media/testing-library-with-visual-studio/save-file-as-dialog.png" alt-text="Visual Studio dosyayı farklı Kaydet iletişim kutusu":::

1. <span data-ttu-id="0e756-170">**Farklı kaydet** iletişim kutusunda, dosyayı kaydetmek için **Evet** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="0e756-170">In the **Confirm Save As** dialog, select the **Yes** button to save the file.</span></span>

1. <span data-ttu-id="0e756-171">**Gelişmiş kaydetme seçenekleri** iletişim kutusunda, **kodlama** açılan LISTESINDEN **Unicode (imzayla UTF-8)-kod sayfası 65001** ' i seçin ve **Tamam**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="0e756-171">In the **Advanced Save Options** dialog, select **Unicode (UTF-8 with signature) - Codepage 65001** from the **Encoding** drop-down list and select **OK**.</span></span>

   > [!div class="mx-imgBorder"]
   > :::image type="content" source="./media/testing-library-with-visual-studio/advanced-save-options.png" alt-text="Visual Studio Gelişmiş kaydetme seçenekleri iletişim kutusu":::

   <span data-ttu-id="0e756-173">Kaynak kodunuzu UTF8 kodlu bir dosya olarak kaydedemeyebilirsiniz, Visual Studio bunu bir ASCII dosyası olarak kaydedebilir.</span><span class="sxs-lookup"><span data-stu-id="0e756-173">If you fail to save your source code as a UTF8-encoded file, Visual Studio may save it as an ASCII file.</span></span> <span data-ttu-id="0e756-174">Söz konusu olduğunda, çalışma zamanı, ASCII aralığının dışında UTF8 karakterlerinin kodunu doğru şekilde çözmez ve test sonuçları doğru olmayacaktır.</span><span class="sxs-lookup"><span data-stu-id="0e756-174">When that happens, the runtime doesn't accurately decode the UTF8 characters outside of the ASCII range, and the test results won't be correct.</span></span>

1. <span data-ttu-id="0e756-175">Menü çubuğunda, **Test**  >  **Çalıştır tüm testler**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="0e756-175">On the menu bar, select **Test** > **Run All Tests**.</span></span> <span data-ttu-id="0e756-176">**Test Gezgini** penceresi açılmazsa **Test**  >  **Test Gezgini**' ni seçerek açın.</span><span class="sxs-lookup"><span data-stu-id="0e756-176">If the **Test Explorer** window doesn't open, open it by choosing **Test** > **Test Explorer**.</span></span> <span data-ttu-id="0e756-177">**Geçen testler** bölümünde üç test listelenir ve **Özet** bölümü Test çalıştırmasının sonucunu raporlar.</span><span class="sxs-lookup"><span data-stu-id="0e756-177">The three tests are listed in the **Passed Tests** section, and the **Summary** section reports the result of the test run.</span></span>

   > [!div class="mx-imgBorder"]
   > :::image type="content" source="./media/testing-library-with-visual-studio/test-explorer-window.png" alt-text="Testleri geçirerek test Gezgini penceresi":::

## <a name="handle-test-failures"></a><span data-ttu-id="0e756-179">Test başarısızlıklarını işle</span><span class="sxs-lookup"><span data-stu-id="0e756-179">Handle test failures</span></span>

<span data-ttu-id="0e756-180">Test odaklı geliştirme (TDD) yapıyorsanız, önce testleri yazarsınız ve ilk kez çalıştırdığınızda başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="0e756-180">If you're doing test-driven development (TDD), you write tests first and they fail the first time you run them.</span></span> <span data-ttu-id="0e756-181">Sonra, uygulamayı başarılı hale getiren uygulamaya kod eklersiniz.</span><span class="sxs-lookup"><span data-stu-id="0e756-181">Then you add code to the app that makes the test succeed.</span></span> <span data-ttu-id="0e756-182">Bu öğreticide, doğrulaması yaptığı uygulama kodunu yazdıktan sonra test başarısız olduğunu görmediyseniz testi oluşturdunuz.</span><span class="sxs-lookup"><span data-stu-id="0e756-182">For this tutorial, you created the test after writing the app code that it validates, so you haven't seen the test fail.</span></span> <span data-ttu-id="0e756-183">Başarısız olması beklendiğinde testin başarısız olduğunu doğrulamak için, test girişine geçersiz bir değer ekleyin.</span><span class="sxs-lookup"><span data-stu-id="0e756-183">To validate that a test fails when you expect it to fail, add an invalid value to the test input.</span></span>

1. <span data-ttu-id="0e756-184">`words`Yöntemdeki diziyi, `TestDoesNotStartWithUpper` "Error" dizesini içerecek şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="0e756-184">Modify the `words` array in the `TestDoesNotStartWithUpper` method to include the string "Error".</span></span> <span data-ttu-id="0e756-185">Testleri çalıştırmak için bir çözüm oluşturulduğunda Visual Studio açık dosyaları otomatik olarak kaydettiği için dosyayı kaydetmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="0e756-185">You don't need to save the file because Visual Studio automatically saves open files when a solution is built to run tests.</span></span>

   ```csharp
   string[] words = { "alphabet", "Error", "zebra", "abc", "αυτοκινητοβιομηχανία", "государство",
                      "1234", ".", ";", " " };
   ```

   ```vb
   Dim words() As String = { "alphabet", "Error", "zebra", "abc", "αυτοκινητοβιομηχανία", "государство",
                      "1234", ".", ";", " " }

   ```

1. <span data-ttu-id="0e756-186">Test Çalıştır **Test**  >  **tüm testleri** menü çubuğundan Çalıştır öğesini seçerek testi çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="0e756-186">Run the test by selecting **Test** > **Run All Tests** from the menu bar.</span></span> <span data-ttu-id="0e756-187">**Test Gezgini** penceresi, iki testin başarılı olduğunu ve bir başarısız olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="0e756-187">The **Test Explorer** window indicates that two tests succeeded and one failed.</span></span>

   > [!div class="mx-imgBorder"]
   > :::image type="content" source="./media/testing-library-with-visual-studio/failed-test-window.png" alt-text="Başarısız testlerle test Gezgini penceresi":::

1. <span data-ttu-id="0e756-189">Başarısız testi seçin `TestDoesNotStartWith` .</span><span class="sxs-lookup"><span data-stu-id="0e756-189">Select the failed test, `TestDoesNotStartWith`.</span></span>

   <span data-ttu-id="0e756-190">**Test Gezgini** penceresi onay tarafından oluşturulan iletiyi görüntüler: "onaylama. IsFalse başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="0e756-190">The **Test Explorer** window displays the message produced by the assert: "Assert.IsFalse failed.</span></span> <span data-ttu-id="0e756-191">' Error ' bekleniyor: false; gerçek: true ".</span><span class="sxs-lookup"><span data-stu-id="0e756-191">Expected for 'Error': false; actual: True".</span></span> <span data-ttu-id="0e756-192">Hata nedeniyle "hata" sonunda dizide hiçbir dize sınanmadı.</span><span class="sxs-lookup"><span data-stu-id="0e756-192">Because of the failure, no strings in the array after "Error" were tested.</span></span>

   > [!div class="mx-imgBorder"]
   > :::image type="content" source="./media/testing-library-with-visual-studio/failed-test-detail.png" alt-text="IsFalse onaylama hatasını gösteren test Gezgini penceresi":::

1. <span data-ttu-id="0e756-194">Adım 1 ' de eklediğiniz "Error" dizesini kaldırın.</span><span class="sxs-lookup"><span data-stu-id="0e756-194">Remove the string "Error" that you added in step 1.</span></span> <span data-ttu-id="0e756-195">Testi ve test geçişini yeniden çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="0e756-195">Rerun the test and the tests pass.</span></span>

## <a name="test-the-release-version-of-the-library"></a><span data-ttu-id="0e756-196">Kitaplığın yayın sürümünü test etme</span><span class="sxs-lookup"><span data-stu-id="0e756-196">Test the Release version of the library</span></span>

<span data-ttu-id="0e756-197">Artık, kitaplığın hata ayıklama derlemesini çalıştırırken testlerin başarılı olduğuna göre, bu testleri kitaplığın yayın derlemesi için ek bir zaman çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="0e756-197">Now that the tests have all passed when running the Debug build of the library, run the tests an additional time against the Release build of the library.</span></span> <span data-ttu-id="0e756-198">Derleyici iyileştirmeleri dahil olmak üzere bir dizi etken bazen hata ayıklama ve yayın yapıları arasında farklı davranışlar üretebilir.</span><span class="sxs-lookup"><span data-stu-id="0e756-198">A number of factors, including compiler optimizations, can sometimes produce different behavior between Debug and Release builds.</span></span>

<span data-ttu-id="0e756-199">Yayın derlemesini test etmek için:</span><span class="sxs-lookup"><span data-stu-id="0e756-199">To test the Release build:</span></span>

1. <span data-ttu-id="0e756-200">Visual Studio araç çubuğunda, derleme yapılandırmasını **Debug** iken **Release** olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="0e756-200">In the Visual Studio toolbar, change the build configuration from **Debug** to **Release**.</span></span>

   > [!div class="mx-imgBorder"]
   > :::image type="content" source="./media/testing-library-with-visual-studio/visual-studio-toolbar-release.png" alt-text="Yayın derlemesi vurgulanmış Visual Studio araç çubuğu":::

1. <span data-ttu-id="0e756-202">**Çözüm Gezgini**, **StringLibrary** projesine sağ tıklayın ve kitaplığı yeniden derlemek için bağlam menüsünden **Oluştur** ' u seçin.</span><span class="sxs-lookup"><span data-stu-id="0e756-202">In **Solution Explorer**, right-click the **StringLibrary** project and select **Build** from the context menu to recompile the library.</span></span>

   > [!div class="mx-imgBorder"]
   > :::image type="content" source="./media/testing-library-with-visual-studio/build-library-context-menu.png" alt-text="Build komutuyla StringLibrary bağlam menüsü":::

1. <span data-ttu-id="0e756-204">**Test Run**  >  Menü çubuğundan **tüm testleri** Çalıştır test ' i seçerek birim testlerini çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="0e756-204">Run the unit tests by choosing **Test Run** > **All Tests** from the menu bar.</span></span> <span data-ttu-id="0e756-205">Testler geçer.</span><span class="sxs-lookup"><span data-stu-id="0e756-205">The tests pass.</span></span>

## <a name="debug-tests"></a><span data-ttu-id="0e756-206">Hata ayıklama testleri</span><span class="sxs-lookup"><span data-stu-id="0e756-206">Debug tests</span></span>

<span data-ttu-id="0e756-207">IDE 'niz olarak Visual Studio kullanıyorsanız, öğretici: birim test projenizi kullanarak kodda hata ayıklamak için [Visual Studio 'yu kullanarak bir .NET konsol uygulamasında hata ayıklama](debugging-with-visual-studio.md) için gösterilen aynı süreci kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0e756-207">If you're using Visual Studio as your IDE, you can use the same process shown in [Tutorial: Debug a .NET console application using Visual Studio](debugging-with-visual-studio.md) to debug code using your unit test project.</span></span> <span data-ttu-id="0e756-208">*Gösterimi* uygulama projesini başlatmak yerine **stringlibrarytests** projesine sağ tıklayın ve bağlam menüsünden **testlerin hatalarını ayıkla** ' yı seçin.</span><span class="sxs-lookup"><span data-stu-id="0e756-208">Instead of starting the *ShowCase* app project, right-click the **StringLibraryTests** project, and select **Debug Tests** from the context menu.</span></span>

<span data-ttu-id="0e756-209">Visual Studio, hata ayıklayıcı ekli olarak test projesi başlatır.</span><span class="sxs-lookup"><span data-stu-id="0e756-209">Visual Studio starts the test project with the debugger attached.</span></span> <span data-ttu-id="0e756-210">Yürütme, test projesine veya temeldeki kitaplık koduna eklediğiniz herhangi bir kesme noktasında durur.</span><span class="sxs-lookup"><span data-stu-id="0e756-210">Execution will stop at any breakpoint you've added to the test project or the underlying library code.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="0e756-211">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="0e756-211">Additional resources</span></span>

* [<span data-ttu-id="0e756-212">Birim testi temelleri-Visual Studio</span><span class="sxs-lookup"><span data-stu-id="0e756-212">Unit test basics - Visual Studio</span></span>](/visualstudio/test/unit-test-basics)
* [<span data-ttu-id="0e756-213">.NET 'te birim testi</span><span class="sxs-lookup"><span data-stu-id="0e756-213">Unit testing in .NET</span></span>](../testing/index.md)

## <a name="next-steps"></a><span data-ttu-id="0e756-214">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="0e756-214">Next steps</span></span>

<span data-ttu-id="0e756-215">Bu öğreticide, birim bir sınıf kitaplığı test edilmiştir.</span><span class="sxs-lookup"><span data-stu-id="0e756-215">In this tutorial, you unit tested a class library.</span></span> <span data-ttu-id="0e756-216">Bir paket olarak [NuGet](https://nuget.org) 'e yayımlayarak, kitaplığı başkaları için kullanılabilir hale getirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0e756-216">You can make the library available to others by publishing it to [NuGet](https://nuget.org) as a package.</span></span> <span data-ttu-id="0e756-217">Nasıl yapılacağını öğrenmek için bir NuGet öğreticisini izleyin:</span><span class="sxs-lookup"><span data-stu-id="0e756-217">To learn how, follow a NuGet tutorial:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="0e756-218">Visual Studio kullanarak bir NuGet paketi oluşturma ve yayımlama</span><span class="sxs-lookup"><span data-stu-id="0e756-218">Create and publish a NuGet package using Visual Studio</span></span>](/nuget/quickstart/create-and-publish-a-package-using-visual-studio?tabs=netcore-cli)

<span data-ttu-id="0e756-219">Bir kitaplığı bir NuGet paketi olarak yayımlarsanız, diğerleri onu yükleyebilir ve kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="0e756-219">If you publish a library as a NuGet package, others can install and use it.</span></span> <span data-ttu-id="0e756-220">Nasıl yapılacağını öğrenmek için bir NuGet öğreticisini izleyin:</span><span class="sxs-lookup"><span data-stu-id="0e756-220">To learn how, follow a NuGet tutorial:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="0e756-221">Visual Studio 'da paket yükleyip kullanma</span><span class="sxs-lookup"><span data-stu-id="0e756-221">Install and use a package in Visual Studio</span></span>](/nuget/quickstart/install-and-use-a-package-in-visual-studio)

<span data-ttu-id="0e756-222">Bir kitaplığın paket olarak dağıtılması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="0e756-222">A library doesn't have to be distributed as a package.</span></span> <span data-ttu-id="0e756-223">Onu kullanan bir konsol uygulamasıyla paketlenmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="0e756-223">It can be bundled with a console app that uses it.</span></span> <span data-ttu-id="0e756-224">Bir konsol uygulamasını yayımlamayı öğrenmek için bu serideki önceki öğreticiye bakın:</span><span class="sxs-lookup"><span data-stu-id="0e756-224">To learn how to publish a console app, see the earlier tutorial in this series:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="0e756-225">Visual Studio kullanarak bir .NET konsol uygulaması yayımlama</span><span class="sxs-lookup"><span data-stu-id="0e756-225">Publish a .NET console application using Visual Studio</span></span>](publishing-with-visual-studio.md)
