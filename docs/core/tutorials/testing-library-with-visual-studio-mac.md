---
title: Mac için Visual Studio kullanarak .NET Core ile .NET Standard sınıf kitaplığı test etme
description: .NET Core sınıf kitaplığı için bir birim test projesi oluşturun. .NET Core sınıf kitaplığının birim testleriyle düzgün çalıştığını doğrulayın.
ms.date: 06/08/2020
ms.openlocfilehash: d3c8a5e01d16047949e977f3af6a429970d996d0
ms.sourcegitcommit: ae2e8a61a93c5cf3f0035c59e6b064fa2f812d14
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "89359226"
---
# <a name="test-a-net-standard-class-library-with-net-core-using-visual-studio"></a><span data-ttu-id="eee08-104">Visual Studio kullanarak .NET Core ile .NET Standard sınıf kitaplığı test etme</span><span class="sxs-lookup"><span data-stu-id="eee08-104">Test a .NET Standard class library with .NET Core using Visual Studio</span></span>

<span data-ttu-id="eee08-105">Bu öğreticide, bir çözüme test projesi ekleyerek birim testinin nasıl otomatikleştirilmesi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="eee08-105">This tutorial shows how to automate unit testing by adding a test project to a solution.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="eee08-106">Ön koşullar</span><span class="sxs-lookup"><span data-stu-id="eee08-106">Prerequisites</span></span>

- <span data-ttu-id="eee08-107">Bu öğretici, [Mac için Visual Studio kullanarak .NET Standard kitaplığı oluşturma](library-with-visual-studio-mac.md)bölümünde oluşturduğunuz çözümle birlikte kullanılır.</span><span class="sxs-lookup"><span data-stu-id="eee08-107">This tutorial works with the solution that you create in [Create a .NET Standard library using Visual Studio for Mac](library-with-visual-studio-mac.md).</span></span>

## <a name="create-a-unit-test-project"></a><span data-ttu-id="eee08-108">Birim testi projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="eee08-108">Create a unit test project</span></span>

<span data-ttu-id="eee08-109">Birim testleri geliştirme ve yayımlama sırasında otomatik yazılım testi sağlar.</span><span class="sxs-lookup"><span data-stu-id="eee08-109">Unit tests provide automated software testing during your development and publishing.</span></span> <span data-ttu-id="eee08-110">[MSTest](https://github.com/Microsoft/testfx-docs) , aralarından seçim yapabileceğiniz üç test çerçevelerinden biridir.</span><span class="sxs-lookup"><span data-stu-id="eee08-110">[MSTest](https://github.com/Microsoft/testfx-docs) is one of three test frameworks you can choose from.</span></span> <span data-ttu-id="eee08-111">Diğerleri [xUnit](https://xunit.net/) ve [NUnit](https://nunit.org/)' dir.</span><span class="sxs-lookup"><span data-stu-id="eee08-111">The others are [xUnit](https://xunit.net/) and [nUnit](https://nunit.org/).</span></span>

1. <span data-ttu-id="eee08-112">Mac için Visual Studio başlatın.</span><span class="sxs-lookup"><span data-stu-id="eee08-112">Start Visual Studio for Mac.</span></span>

1. <span data-ttu-id="eee08-113">`ClassLibraryProjects` [Mac için Visual Studio kullanarak .NET Standard kitaplığı oluşturma](library-with-visual-studio-mac.md)bölümünde oluşturduğunuz çözümü açın.</span><span class="sxs-lookup"><span data-stu-id="eee08-113">Open the `ClassLibraryProjects` solution you created in [Create a .NET Standard library using Visual Studio for Mac](library-with-visual-studio-mac.md).</span></span>

1. <span data-ttu-id="eee08-114">**Çözüm** panelinde, çözüme <kbd>CTRL</kbd>-tıklayın `ClassLibraryProjects` ve **Add**  >  **Yeni proje**Ekle ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="eee08-114">In the **Solution** pad, <kbd>ctrl</kbd>-click the `ClassLibraryProjects` solution and select **Add** > **New Project**.</span></span>

1. <span data-ttu-id="eee08-115">**Yeni proje** iletişim kutusunda, **Web ve konsol** düğümünden **testler** ' i seçin.</span><span class="sxs-lookup"><span data-stu-id="eee08-115">In the **New Project** dialog, select **Tests** from the **Web and Console** node.</span></span> <span data-ttu-id="eee08-116">**MSTest projesini** ve ardından Ileri ' **yi**seçin.</span><span class="sxs-lookup"><span data-stu-id="eee08-116">Select the **MSTest Project** followed by **Next**.</span></span>

   :::image type="content" source="media/testing-library-with-visual-studio-mac/visual-studio-mac-unit-test-project.png" alt-text="Visual Studio Mac yeni proje iletişim kutusu test projesi oluşturma":::

1. <span data-ttu-id="eee08-118">**.NET Core 3,1**' u seçin.</span><span class="sxs-lookup"><span data-stu-id="eee08-118">Select **.NET Core 3.1**.</span></span> <span data-ttu-id="eee08-119">"StringLibraryTest" adlı yeni projeyi adlandırın ve **Oluştur**' u seçin.</span><span class="sxs-lookup"><span data-stu-id="eee08-119">Name the new project "StringLibraryTest" and select **Create**.</span></span>

   :::image type="content" source="media/testing-library-with-visual-studio-mac/visual-studio-mac-new-project-name.png" alt-text="Proje adı sağlayan Visual Studio Mac yeni proje iletişim kutusu":::

   <span data-ttu-id="eee08-121">Visual Studio aşağıdaki kodla bir sınıf dosyası oluşturur:</span><span class="sxs-lookup"><span data-stu-id="eee08-121">Visual Studio creates a class file with the following code:</span></span>

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

   <span data-ttu-id="eee08-122">Birim testi şablonu tarafından oluşturulan kaynak kodu aşağıdakileri yapar:</span><span class="sxs-lookup"><span data-stu-id="eee08-122">The source code created by the unit test template does the following:</span></span>

   - <span data-ttu-id="eee08-123"><xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=nameWithType>Birim testi için kullanılan türleri içeren ad alanını içeri aktarır.</span><span class="sxs-lookup"><span data-stu-id="eee08-123">It imports the <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=nameWithType> namespace, which contains the types used for unit testing.</span></span>
   - <span data-ttu-id="eee08-124"><xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute>Özniteliği `UnitTest1` sınıfına uygular.</span><span class="sxs-lookup"><span data-stu-id="eee08-124">It applies the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> attribute to the `UnitTest1` class.</span></span>
   - <span data-ttu-id="eee08-125"><xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute>Özniteliğini öğesine uygular `TestMethod1` .</span><span class="sxs-lookup"><span data-stu-id="eee08-125">It applies the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> attribute to `TestMethod1`.</span></span>

   <span data-ttu-id="eee08-126">[ [TestClass]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute) ile etiketlenmiş bir test sınıfında [[TestMethod]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) etiketli her bir yöntem, birim testi çalıştırıldığında otomatik olarak yürütülür.</span><span class="sxs-lookup"><span data-stu-id="eee08-126">Each method tagged with [[TestMethod]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) in a test class tagged with [[TestClass]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute) is executed automatically when the unit test is run.</span></span>

## <a name="add-a-project-reference"></a><span data-ttu-id="eee08-127">Proje başvurusu Ekle</span><span class="sxs-lookup"><span data-stu-id="eee08-127">Add a project reference</span></span>

<span data-ttu-id="eee08-128">Test projesinin sınıfla çalışması için `StringLibrary` projeye bir başvuru ekleyin `StringLibrary` .</span><span class="sxs-lookup"><span data-stu-id="eee08-128">For the test project to work with the `StringLibrary` class, add a reference to the `StringLibrary` project.</span></span>

1. <span data-ttu-id="eee08-129">**Çözüm** panelinde, **stringlibrarytest**altındaki **Bağımlılıklar** ' a <kbd>CTRL tuşuna</kbd>tıklayın.</span><span class="sxs-lookup"><span data-stu-id="eee08-129">In the **Solution** pad, <kbd>ctrl</kbd>-click **Dependencies** under **StringLibraryTest**.</span></span> <span data-ttu-id="eee08-130">Bağlam menüsünden **Başvuru Ekle** ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="eee08-130">Select **Add Reference** from the context menu.</span></span>

1. <span data-ttu-id="eee08-131">**Başvurular** Iletişim kutusunda **StringLibrary** projesini seçin.</span><span class="sxs-lookup"><span data-stu-id="eee08-131">In the **References** dialog, select the **StringLibrary** project.</span></span> <span data-ttu-id="eee08-132">**Tamam**’ı seçin.</span><span class="sxs-lookup"><span data-stu-id="eee08-132">Select **OK**.</span></span>

      :::image type="content" source="media/testing-library-with-visual-studio-mac/visual-studio-mac-edit-references.png" alt-text="Visual Studio Mac başvuruları Düzenle iletişim kutusu":::

## <a name="add-and-run-unit-test-methods"></a><span data-ttu-id="eee08-134">Birim testi yöntemleri ekleme ve çalıştırma</span><span class="sxs-lookup"><span data-stu-id="eee08-134">Add and run unit test methods</span></span>

<span data-ttu-id="eee08-135">Visual Studio bir birim testi çalıştırdığında, özniteliğiyle <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> işaretlenmiş bir sınıfta özniteliğiyle işaretlenmiş her metodu yürütür  <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> .</span><span class="sxs-lookup"><span data-stu-id="eee08-135">When Visual Studio runs a unit test, it executes each method that is marked with the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> attribute in a class that is marked with the  <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> attribute.</span></span> <span data-ttu-id="eee08-136">İlk hata bulunduğunda veya yöntemde bulunan tüm testler başarılı olduğunda bir test yöntemi sonlanır.</span><span class="sxs-lookup"><span data-stu-id="eee08-136">A test method ends when the first failure is found or when all tests contained in the method have succeeded.</span></span>

<span data-ttu-id="eee08-137">En yaygın testler, sınıfının üyelerini çağırır <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> .</span><span class="sxs-lookup"><span data-stu-id="eee08-137">The most common tests call members of the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> class.</span></span> <span data-ttu-id="eee08-138">Birçok onaylama yöntemi, biri beklenen test sonucu ve diğeri de gerçek test sonucu olan en az iki parametre içerir.</span><span class="sxs-lookup"><span data-stu-id="eee08-138">Many assert methods include at least two parameters, one of which is the expected test result and the other of which is the actual test result.</span></span> <span data-ttu-id="eee08-139">`Assert`Sınıfın en sık çağrılan yöntemlerin bazıları aşağıdaki tabloda gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="eee08-139">Some of the `Assert` class's most frequently called methods are shown in the following table:</span></span>

| <span data-ttu-id="eee08-140">Onaylama yöntemleri</span><span class="sxs-lookup"><span data-stu-id="eee08-140">Assert methods</span></span>     | <span data-ttu-id="eee08-141">İşlev</span><span class="sxs-lookup"><span data-stu-id="eee08-141">Function</span></span> |
| ------------------ | -------- |
| `Assert.AreEqual`  | <span data-ttu-id="eee08-142">İki değerin veya nesnenin eşit olduğunu doğrular.</span><span class="sxs-lookup"><span data-stu-id="eee08-142">Verifies that two values or objects are equal.</span></span> <span data-ttu-id="eee08-143">Değerler veya nesneler eşitse onaylama başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="eee08-143">The assert fails if the values or objects aren't equal.</span></span> |
| `Assert.AreSame`   | <span data-ttu-id="eee08-144">İki nesne değişkeninin aynı nesneye başvurmasını doğrular.</span><span class="sxs-lookup"><span data-stu-id="eee08-144">Verifies that two object variables refer to the same object.</span></span> <span data-ttu-id="eee08-145">Değişkenler farklı nesnelere başvuru yaptığında onaylama başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="eee08-145">The assert fails if the variables refer to different objects.</span></span> |
| `Assert.IsFalse`   | <span data-ttu-id="eee08-146">Bir koşulun olduğunu doğrular `false` .</span><span class="sxs-lookup"><span data-stu-id="eee08-146">Verifies that a condition is `false`.</span></span> <span data-ttu-id="eee08-147">Koşul ise onaylama başarısız olur `true` .</span><span class="sxs-lookup"><span data-stu-id="eee08-147">The assert fails if the condition is `true`.</span></span> |
| `Assert.IsNotNull` | <span data-ttu-id="eee08-148">Bir nesnenin olmadığını doğrular `null` .</span><span class="sxs-lookup"><span data-stu-id="eee08-148">Verifies that an object isn't `null`.</span></span> <span data-ttu-id="eee08-149">Nesne ise onaylama başarısız olur `null` .</span><span class="sxs-lookup"><span data-stu-id="eee08-149">The assert fails if the object is `null`.</span></span> |

<span data-ttu-id="eee08-150"><xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A?displayProperty=nameWithType>Yöntemi bir test yönteminde, oluşturması beklenen özel durum türünü belirtmek için de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="eee08-150">You can also use the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A?displayProperty=nameWithType> method in a test method to indicate the type of exception it's expected to throw.</span></span> <span data-ttu-id="eee08-151">Belirtilen özel durum atılmazsa, test başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="eee08-151">The test fails if the specified exception isn't thrown.</span></span>

<span data-ttu-id="eee08-152">Yöntemi test ederken `StringLibrary.StartsWithUpper` , büyük harf karakteriyle başlayan bir dizi dize sağlamak istersiniz.</span><span class="sxs-lookup"><span data-stu-id="eee08-152">In testing the `StringLibrary.StartsWithUpper` method, you want to provide a number of strings that begin with an uppercase character.</span></span> <span data-ttu-id="eee08-153">Yöntemi bu durumlarda Return olarak beklediğinizi ve `true` <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue%2A?displayProperty=nameWithType> yöntemi çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="eee08-153">You expect the method to return `true` in these cases, so you can call the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="eee08-154">Benzer şekilde, büyük harfli bir karakter ile başlayan bir dizi dize sağlamak istersiniz.</span><span class="sxs-lookup"><span data-stu-id="eee08-154">Similarly, you want to provide a number of strings that begin with something other than an uppercase character.</span></span> <span data-ttu-id="eee08-155">Yöntemi bu durumlarda Return olarak beklediğinizi ve `false` <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse%2A?displayProperty=nameWithType> yöntemi çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="eee08-155">You expect the method to return `false` in these cases, so you can call the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="eee08-156">Kitaplık yönteminiz dizeleri yaptığından, ayrıca [boş bir dizeyi ( `String.Empty` )](xref:System.String.Empty)başarılı bir şekilde (), karakteri olmayan ve 0 olan geçerli bir dize <xref:System.String.Length> ve başlatılmamış bir dize de işlemesini sağlamak istersiniz `null` .</span><span class="sxs-lookup"><span data-stu-id="eee08-156">Since your library method handles strings, you also want to make sure that it successfully handles an [empty string (`String.Empty`)](xref:System.String.Empty), a valid string that has no characters and whose <xref:System.String.Length> is 0, and a `null` string that hasn't been initialized.</span></span> <span data-ttu-id="eee08-157">`StartsWithUpper`Doğrudan statik bir yöntem olarak çağırabilir ve tek bir <xref:System.String> bağımsız değişken geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="eee08-157">You can call `StartsWithUpper` directly as a static method and pass a single <xref:System.String> argument.</span></span> <span data-ttu-id="eee08-158">Ya da `StartsWithUpper` öğesine atanan bir değişkende bir genişletme yöntemi olarak çağırabilirsiniz `string` `null` .</span><span class="sxs-lookup"><span data-stu-id="eee08-158">Or you can call `StartsWithUpper` as an extension method on a `string` variable assigned to `null`.</span></span>

<span data-ttu-id="eee08-159">Her biri <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> bir dize dizisindeki her öğe için bir yöntem çağıran üç yöntem tanımlayacaksınız.</span><span class="sxs-lookup"><span data-stu-id="eee08-159">You'll define three methods, each of which calls an <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> method for each element in a string array.</span></span> <span data-ttu-id="eee08-160">Test hatası durumunda görüntülenecek bir hata iletisi belirtmenize imkan tanıyan bir yöntem aşırı yüklemesi çağıracaksınız.</span><span class="sxs-lookup"><span data-stu-id="eee08-160">You'll call a method overload that lets you specify an error message to be displayed in case of test failure.</span></span> <span data-ttu-id="eee08-161">İleti, hataya neden olan dizeyi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="eee08-161">The message identifies the string that caused the failure.</span></span>

<span data-ttu-id="eee08-162">Test yöntemleri oluşturmak için:</span><span class="sxs-lookup"><span data-stu-id="eee08-162">To create the test methods:</span></span>

1. <span data-ttu-id="eee08-163">*UnitTest1.cs* dosyasını açın ve kodu şu kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="eee08-163">Open the *UnitTest1.cs* file and replace the code with the following code:</span></span>

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/StringLibraryTest/UnitTest1.cs":::

   <span data-ttu-id="eee08-164">Yöntemdeki büyük harfli karakterlerin testi, `TestStartsWithUpper` Yunanca Büyük Harf Alpha (u + 0391) ve Kiril Büyük harf em (u + 041C) içerir.</span><span class="sxs-lookup"><span data-stu-id="eee08-164">The test of uppercase characters in the `TestStartsWithUpper` method includes the Greek capital letter alpha (U+0391) and the Cyrillic capital letter EM (U+041C).</span></span> <span data-ttu-id="eee08-165">Yöntemdeki küçük harfli karakterlerin testi `TestDoesNotStartWithUpper` Yunanca Küçük Harf Alpha (u + 03B1) ve Kiril Küçük harf GHE (u + 0433) içerir.</span><span class="sxs-lookup"><span data-stu-id="eee08-165">The test of lowercase characters in the `TestDoesNotStartWithUpper` method includes the Greek small letter alpha (U+03B1) and the Cyrillic small letter Ghe (U+0433).</span></span>

1. <span data-ttu-id="eee08-166">Menü çubuğunda **Dosya**  >  **farklı kaydet**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="eee08-166">On the menu bar, select **File** > **Save As**.</span></span> <span data-ttu-id="eee08-167">İletişim kutusunda, **kodlamanın** **UNICODE (UTF-8)** olarak ayarlandığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="eee08-167">In the dialog, make sure that **Encoding** is set to **Unicode (UTF-8)**.</span></span>

   :::image type="content" source="media/testing-library-with-visual-studio-mac/save-file-as-dialog.png" alt-text="Visual Studio dosyayı farklı Kaydet iletişim kutusu":::

1. <span data-ttu-id="eee08-169">Var olan dosyayı değiştirmek isteyip istemediğiniz sorulduğunda **Değiştir**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="eee08-169">When you're asked if you want to replace the existing file, select **Replace**.</span></span>

   <span data-ttu-id="eee08-170">Kaynak kodunuzu UTF8 kodlu bir dosya olarak kaydedemeyebilirsiniz, Visual Studio bunu bir ASCII dosyası olarak kaydedebilir.</span><span class="sxs-lookup"><span data-stu-id="eee08-170">If you fail to save your source code as a UTF8-encoded file, Visual Studio may save it as an ASCII file.</span></span> <span data-ttu-id="eee08-171">Söz konusu olduğunda, çalışma zamanı, ASCII aralığının dışında UTF8 karakterlerinin kodunu doğru şekilde çözmez ve test sonuçları doğru olmayacaktır.</span><span class="sxs-lookup"><span data-stu-id="eee08-171">When that happens, the runtime doesn't accurately decode the UTF8 characters outside of the ASCII range, and the test results won't be correct.</span></span>

1. <span data-ttu-id="eee08-172">Ekranın sağ tarafındaki **birim testleri** panelini açın.</span><span class="sxs-lookup"><span data-stu-id="eee08-172">Open the **Unit Tests** panel on the right side of the screen.</span></span> <span data-ttu-id="eee08-173">Menüden **View**  >  **Testleri** görüntüle ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="eee08-173">Select **View** > **Tests** from the menu.</span></span>

1. <span data-ttu-id="eee08-174">Paneli açık tutmak için **Yerleştir** simgesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="eee08-174">Click the **Dock** icon to keep the panel open.</span></span>

   :::image type="content" source="media/testing-library-with-visual-studio-mac/visual-studio-mac-unit-test-dock-icon.png" alt-text="Mac için Visual Studio birim testleri bölmesi yerleştirme simgesi":::

1. <span data-ttu-id="eee08-176">**Tümünü Çalıştır** düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="eee08-176">Click the **Run All** button.</span></span>

   <span data-ttu-id="eee08-177">Tüm testler geçer.</span><span class="sxs-lookup"><span data-stu-id="eee08-177">All tests pass.</span></span>

   :::image type="content" source="media/testing-library-with-visual-studio-mac/visual-studio-mac-unit-test-pass.png" alt-text="Beklenen test geçişleri Mac için Visual Studio":::

## <a name="handle-test-failures"></a><span data-ttu-id="eee08-179">Test başarısızlıklarını işle</span><span class="sxs-lookup"><span data-stu-id="eee08-179">Handle test failures</span></span>

<span data-ttu-id="eee08-180">Test odaklı geliştirme (TDD) yapıyorsanız, önce testleri yazarsınız ve ilk kez çalıştırdığınızda başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="eee08-180">If you're doing test-driven development (TDD), you write tests first and they fail the first time you run them.</span></span> <span data-ttu-id="eee08-181">Sonra, uygulamayı başarılı hale getiren uygulamaya kod eklersiniz.</span><span class="sxs-lookup"><span data-stu-id="eee08-181">Then you add code to the app that makes the test succeed.</span></span> <span data-ttu-id="eee08-182">Bu öğreticide, doğrulaması yaptığı uygulama kodunu yazdıktan sonra test başarısız olduğunu görmediyseniz testi oluşturdunuz.</span><span class="sxs-lookup"><span data-stu-id="eee08-182">For this tutorial, you created the test after writing the app code that it validates, so you haven't seen the test fail.</span></span> <span data-ttu-id="eee08-183">Başarısız olması beklendiğinde testin başarısız olduğunu doğrulamak için, test girişine geçersiz bir değer ekleyin.</span><span class="sxs-lookup"><span data-stu-id="eee08-183">To validate that a test fails when you expect it to fail, add an invalid value to the test input.</span></span>

1. <span data-ttu-id="eee08-184">`words`Yöntemdeki diziyi, `TestDoesNotStartWithUpper` "Error" dizesini içerecek şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="eee08-184">Modify the `words` array in the `TestDoesNotStartWithUpper` method to include the string "Error".</span></span> <span data-ttu-id="eee08-185">Testleri çalıştırmak için bir çözüm oluşturulduğunda Visual Studio açık dosyaları otomatik olarak kaydettiği için dosyayı kaydetmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="eee08-185">You don't need to save the file because Visual Studio automatically saves open files when a solution is built to run tests.</span></span>

   ```csharp
   string[] words = { "alphabet", "Error", "zebra", "abc", "αυτοκινητοβιομηχανία", "государство",
                      "1234", ".", ";", " " };
   ```

1. <span data-ttu-id="eee08-186">Testleri yeniden çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="eee08-186">Run the tests again.</span></span>

   <span data-ttu-id="eee08-187">Bu kez, **Test Gezgini** penceresi iki testin başarılı olduğunu ve bir başarısız olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="eee08-187">This time, the **Test Explorer** window indicates that two tests succeeded and one failed.</span></span>

   :::image type="content" source="media/testing-library-with-visual-studio-mac/failed-test-window.png" alt-text="Başarısız testlerle test Gezgini penceresi":::

1. <span data-ttu-id="eee08-189"><kbd>CTRL tuşuna</kbd>basıp başarısız teste tıklayın `TestDoesNotStartWithUpper` ve bağlam menüsünden **sonuçlar panelini göster** ' i seçin.</span><span class="sxs-lookup"><span data-stu-id="eee08-189"><kbd>ctrl</kbd>-click the failed test, `TestDoesNotStartWithUpper`, and select **Show Results Pad** from the context menu.</span></span>

   <span data-ttu-id="eee08-190">**Sonuç** panelinde, "onay. IsFalse başarısız oldu" onay tarafından oluşturulan ileti görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="eee08-190">The **Results** pad displays the message produced by the assert: "Assert.IsFalse failed.</span></span> <span data-ttu-id="eee08-191">' Error ' bekleniyor: false; gerçek: true ".</span><span class="sxs-lookup"><span data-stu-id="eee08-191">Expected for 'Error': false; actual: True".</span></span> <span data-ttu-id="eee08-192">Hata nedeniyle "hata" sonunda dizide hiçbir dize sınanmadı.</span><span class="sxs-lookup"><span data-stu-id="eee08-192">Because of the failure, no strings in the array after "Error" were tested.</span></span>

   :::image type="content" source="media/testing-library-with-visual-studio-mac/visual-studio-mac-unit-test-failure.png" alt-text="IsFalse onaylama hatasını gösteren test Gezgini penceresi":::

1. <span data-ttu-id="eee08-194">Adım 1 ' de eklediğiniz "Error" dizesini kaldırın.</span><span class="sxs-lookup"><span data-stu-id="eee08-194">Remove the string "Error" that you added in step 1.</span></span> <span data-ttu-id="eee08-195">Testi ve test geçişini yeniden çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="eee08-195">Rerun the test and the tests pass.</span></span>

## <a name="test-the-release-version-of-the-library"></a><span data-ttu-id="eee08-196">Kitaplığın yayın sürümünü test etme</span><span class="sxs-lookup"><span data-stu-id="eee08-196">Test the Release version of the library</span></span>

<span data-ttu-id="eee08-197">Artık, kitaplığın hata ayıklama derlemesini çalıştırırken testlerin başarılı olduğuna göre, bu testleri kitaplığın yayın derlemesi için ek bir zaman çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="eee08-197">Now that the tests have all passed when running the Debug build of the library, run the tests an additional time against the Release build of the library.</span></span> <span data-ttu-id="eee08-198">Derleyici iyileştirmeleri dahil olmak üzere bir dizi etken bazen hata ayıklama ve yayın yapıları arasında farklı davranışlar üretebilir.</span><span class="sxs-lookup"><span data-stu-id="eee08-198">A number of factors, including compiler optimizations, can sometimes produce different behavior between Debug and Release builds.</span></span>

<span data-ttu-id="eee08-199">Yayın derlemesini test etmek için:</span><span class="sxs-lookup"><span data-stu-id="eee08-199">To test the Release build:</span></span>

1. <span data-ttu-id="eee08-200">Visual Studio araç çubuğunda, derleme yapılandırmasını **Debug** iken **Release**olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="eee08-200">In the Visual Studio toolbar, change the build configuration from **Debug** to **Release**.</span></span>

   :::image type="content" source="media/testing-library-with-visual-studio-mac/visual-studio-toolbar-release.png" alt-text="Yayın derlemesi vurgulanmış Visual Studio araç çubuğu":::

1. <span data-ttu-id="eee08-202">**Çözüm** panelinde, **StringLibrary** projesine <kbd>CTRL</kbd>-tıklayın ve bağlam menüsünden **Oluştur** ' u seçerek kitaplığı yeniden derleyin.</span><span class="sxs-lookup"><span data-stu-id="eee08-202">In the **Solution** pad, <kbd>ctrl</kbd>-click the **StringLibrary** project and select **Build** from the context menu to recompile the library.</span></span>

   :::image type="content" source="media/testing-library-with-visual-studio-mac/build-library-context-menu.png" alt-text="Build komutuyla StringLibrary bağlam menüsü":::

1. <span data-ttu-id="eee08-204">Birim testlerini yeniden çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="eee08-204">Run the unit tests again.</span></span>

   <span data-ttu-id="eee08-205">Testler geçer.</span><span class="sxs-lookup"><span data-stu-id="eee08-205">The tests pass.</span></span>

## <a name="debug-tests"></a><span data-ttu-id="eee08-206">Hata ayıklama testleri</span><span class="sxs-lookup"><span data-stu-id="eee08-206">Debug tests</span></span>

<span data-ttu-id="eee08-207">Öğreticide gösterilen aynı süreci kullanabilirsiniz: birim test projenizi kullanarak kodun hatalarını ayıklamak için [Mac için Visual Studio kullanarak bir .NET Core konsol uygulamasında hata ayıklayın](debugging-with-visual-studio-mac.md) .</span><span class="sxs-lookup"><span data-stu-id="eee08-207">You can use the same process shown in [Tutorial: Debug a .NET Core console application using Visual Studio for Mac](debugging-with-visual-studio-mac.md) to debug code using your unit test project.</span></span> <span data-ttu-id="eee08-208">Gösterimi uygulama projesini başlatmak yerine **Stringlibrarytests** projesine <kbd>CTRL tuşunu basılı</kbd>ve bağlam menüsünde **proje hata ayıklamayı Başlat** ' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="eee08-208">Instead of starting the ShowCase app project, <kbd>ctrl</kbd>-click the **StringLibraryTests** project, and select **Start Debugging Project** from the context menu.</span></span> <span data-ttu-id="eee08-209">Visual Studio, hata ayıklayıcı ekli olarak test projesi başlatır.</span><span class="sxs-lookup"><span data-stu-id="eee08-209">Visual Studio starts the test project with the debugger attached.</span></span> <span data-ttu-id="eee08-210">Yürütme, test projesine veya temeldeki kitaplık koduna eklediğiniz herhangi bir kesme noktasında durur.</span><span class="sxs-lookup"><span data-stu-id="eee08-210">Execution will stop at any breakpoint you've added to the test project or the underlying library code.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="eee08-211">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="eee08-211">Additional resources</span></span>

* [<span data-ttu-id="eee08-212">.NET Core ve .NET Standard birim testi</span><span class="sxs-lookup"><span data-stu-id="eee08-212">Unit testing in .NET Core and .NET Standard</span></span>](../testing/index.md)

## <a name="next-steps"></a><span data-ttu-id="eee08-213">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="eee08-213">Next steps</span></span>

<span data-ttu-id="eee08-214">Bu öğreticide, birim bir sınıf kitaplığı test edilmiştir.</span><span class="sxs-lookup"><span data-stu-id="eee08-214">In this tutorial, you unit tested a class library.</span></span> <span data-ttu-id="eee08-215">Bir paket olarak [NuGet](https://nuget.org) 'e yayımlayarak, kitaplığı başkaları için kullanılabilir hale getirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="eee08-215">You can make the library available to others by publishing it to [NuGet](https://nuget.org) as a package.</span></span> <span data-ttu-id="eee08-216">Nasıl yapılacağını öğrenmek için bir NuGet öğreticisini izleyin:</span><span class="sxs-lookup"><span data-stu-id="eee08-216">To learn how, follow a NuGet tutorial:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="eee08-217">Paket (dotnet CLI) oluşturma ve yayımlama</span><span class="sxs-lookup"><span data-stu-id="eee08-217">Create and publish a package (dotnet CLI)</span></span>](/nuget/quickstart/create-and-publish-a-package-using-the-dotnet-cli)

<span data-ttu-id="eee08-218">Bir kitaplığı bir NuGet paketi olarak yayımlarsanız, diğerleri onu yükleyebilir ve kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="eee08-218">If you publish a library as a NuGet package, others can install and use it.</span></span> <span data-ttu-id="eee08-219">Nasıl yapılacağını öğrenmek için bir NuGet öğreticisini izleyin:</span><span class="sxs-lookup"><span data-stu-id="eee08-219">To learn how, follow a NuGet tutorial:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="eee08-220">Mac için Visual Studio bir paketi yükleyip kullanma</span><span class="sxs-lookup"><span data-stu-id="eee08-220">Install and use a package in Visual Studio for Mac</span></span>](/nuget/quickstart/install-and-use-a-package-in-visual-studio-mac)

<span data-ttu-id="eee08-221">Bir kitaplığın paket olarak dağıtılması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="eee08-221">A library doesn't have to be distributed as a package.</span></span> <span data-ttu-id="eee08-222">Onu kullanan bir konsol uygulamasıyla paketlenmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="eee08-222">It can be bundled with a console app that uses it.</span></span> <span data-ttu-id="eee08-223">Bir konsol uygulamasını yayımlamayı öğrenmek için bu serideki önceki öğreticiye bakın:</span><span class="sxs-lookup"><span data-stu-id="eee08-223">To learn how to publish a console app, see the earlier tutorial in this series:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="eee08-224">Mac için Visual Studio kullanarak bir .NET Core konsol uygulaması yayımlama</span><span class="sxs-lookup"><span data-stu-id="eee08-224">Publish a .NET Core console application using Visual Studio for Mac</span></span>](publishing-with-visual-studio-mac.md)
