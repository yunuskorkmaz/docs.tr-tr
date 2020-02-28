---
title: Visual Studio 'da .NET Core ile .NET Standard sınıf kitaplığı test etme
description: .NET Core sınıf kitaplığınız için bir birim testi projesi oluşturun. .NET Core sınıf kitaplığınızın birim testlerle düzgün çalıştığını doğrulayın.
ms.date: 12/24/2019
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet, seodoc18
ms.openlocfilehash: 307261088f5c7c69c0e69fbd6b99940c04842eec
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78156627"
---
# <a name="test-a-net-standard-library-with-net-core-in-visual-studio"></a><span data-ttu-id="d05e2-104">Visual Studio 'da .NET Core ile .NET Standard kitaplığı test etme</span><span class="sxs-lookup"><span data-stu-id="d05e2-104">Test a .NET Standard library with .NET Core in Visual Studio</span></span>

<span data-ttu-id="d05e2-105">[Visual Studio 'da .NET Standard kitaplığı oluşturma](library-with-visual-studio.md)bölümünde, <xref:System.String> sınıfına bir genişletme yöntemi ekleyen basit bir sınıf kitaplığı oluşturdunuz.</span><span class="sxs-lookup"><span data-stu-id="d05e2-105">In [Build a .NET Standard library in Visual Studio](library-with-visual-studio.md), you created a simple class library that adds an extension method to the <xref:System.String> class.</span></span> <span data-ttu-id="d05e2-106">Şimdi, beklendiği gibi çalıştığından emin olmak için bir birim testi oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="d05e2-106">Now, you'll create a unit test to make sure that it works as expected.</span></span> <span data-ttu-id="d05e2-107">Birim testi projenizi önceki makalede oluşturduğunuz çözüme ekleyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="d05e2-107">You'll add your unit test project to the solution you created in the previous article.</span></span>

## <a name="create-a-unit-test-project"></a><span data-ttu-id="d05e2-108">Birim testi projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="d05e2-108">Create a unit test project</span></span>

<span data-ttu-id="d05e2-109">Birim testi projesi oluşturmak için aşağıdakileri yapın:</span><span class="sxs-lookup"><span data-stu-id="d05e2-109">To create the unit test project, do the following:</span></span>

1. <span data-ttu-id="d05e2-110">[Visual Studio 'da bir .NET Standard kitaplığı oluşturun](library-with-visual-studio.md) makalesindeki oluşturduğunuz `ClassLibraryProjects` çözümünü açın.</span><span class="sxs-lookup"><span data-stu-id="d05e2-110">Open the `ClassLibraryProjects` solution you created in the [Build a .NET Standard library in Visual Studio](library-with-visual-studio.md) article.</span></span>

1. <span data-ttu-id="d05e2-111">Çözüme "StringLibraryTest" adlı yeni bir birim test projesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="d05e2-111">Add a new unit test project named "StringLibraryTest" to the solution.</span></span>

   1. <span data-ttu-id="d05e2-112">**Çözüm Gezgini** çözüme sağ tıklayın ve > **Yeni proje** **Ekle** ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="d05e2-112">Right-click on the solution in **Solution Explorer** and select **Add** > **New project**.</span></span>

   1. <span data-ttu-id="d05e2-113">**Yeni Proje Ekle** sayfasında, arama kutusuna **MSTest** yazın.</span><span class="sxs-lookup"><span data-stu-id="d05e2-113">On the **Add a new project** page, enter **mstest** in the search box.</span></span> <span data-ttu-id="d05e2-114">Dil **C#** listesinden seçin veya **Visual Basic** ve ardından platform listesinden **tüm platformlar** ' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="d05e2-114">Choose **C#** or **Visual Basic** from the Language list, and then choose **All platforms** from the Platform list.</span></span> <span data-ttu-id="d05e2-115">**MSTest test projesi (.NET Core)** şablonunu seçin ve ardından **İleri**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="d05e2-115">Choose the **MsTest Test Project (.NET Core)** template, and then choose **Next**.</span></span>

   1. <span data-ttu-id="d05e2-116">**Yeni projenizi yapılandırın** sayfasında, **Proje adı** kutusuna **stringlibrarytest** girin.</span><span class="sxs-lookup"><span data-stu-id="d05e2-116">On the **Configure your new project** page, enter **StringLibraryTest** in the **Project name** box.</span></span> <span data-ttu-id="d05e2-117">Ardından **Oluştur**’u seçin.</span><span class="sxs-lookup"><span data-stu-id="d05e2-117">Then choose **Create**.</span></span>

   > [!NOTE]
   > <span data-ttu-id="d05e2-118">Bir MSTest 'e ek olarak, Visual Studio 'da .NET Core için xUnit ve nUnit test projeleri de oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d05e2-118">In addition to an MSTest, you can also create xUnit and nUnit test projects for .NET Core in Visual Studio.</span></span>

1. <span data-ttu-id="d05e2-119">Visual Studio projeyi oluşturur ve kod penceresinde sınıf dosyasını aşağıdaki kodla açar:</span><span class="sxs-lookup"><span data-stu-id="d05e2-119">Visual Studio creates the project and opens the class file in the code window with the following code:</span></span>

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

   <span data-ttu-id="d05e2-120">Birim testi şablonu tarafından oluşturulan kaynak kodu aşağıdakileri yapar:</span><span class="sxs-lookup"><span data-stu-id="d05e2-120">The source code created by the unit test template does the following:</span></span>

   - <span data-ttu-id="d05e2-121">Birim testi için kullanılan türleri içeren <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=nameWithType> ad alanını içeri aktarır.</span><span class="sxs-lookup"><span data-stu-id="d05e2-121">It imports the <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=nameWithType> namespace, which contains the types used for unit testing.</span></span>

   - <span data-ttu-id="d05e2-122">`UnitTest1` sınıfına [TestClass](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute) özniteliğini uygular.</span><span class="sxs-lookup"><span data-stu-id="d05e2-122">It applies the [TestClass](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute) attribute to the `UnitTest1` class.</span></span> <span data-ttu-id="d05e2-123">[TestMethod](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) özniteliğiyle etiketlenmiş bir test sınıfındaki her test yöntemi, birim testi çalıştırıldığında otomatik olarak yürütülür.</span><span class="sxs-lookup"><span data-stu-id="d05e2-123">Each test method in a test class tagged with the [TestMethod](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) attribute is executed automatically when the unit test is run.</span></span>

   - <span data-ttu-id="d05e2-124">Birim testi çalıştırıldığında otomatik yürütmeye yönelik bir test yöntemi olarak C# Visual Basic içinde `TestMethod1` veya `TestSub` tanımlamak Için [TestMethod](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) özniteliğini uygular.</span><span class="sxs-lookup"><span data-stu-id="d05e2-124">It applies the [TestMethod](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) attribute to define `TestMethod1` in C# or `TestSub` in Visual Basic as a test method for automatic execution when the unit test is run.</span></span>

1. <span data-ttu-id="d05e2-125">**Çözüm Gezgini**, **stringlibrarytest** projesinin **Bağımlılıklar** düğümüne sağ tıklayın ve bağlam menüsünden **Başvuru Ekle** ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="d05e2-125">In **Solution Explorer**, right-click the **Dependencies** node of the **StringLibraryTest** project and select **Add Reference** from the context menu.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="d05e2-126">StringLibraryTest bağımlılıklarının bağlam menüsünü ![](./media/testing-library-with-visual-studio/add-reference-context-menu.png)</span><span class="sxs-lookup"><span data-stu-id="d05e2-126">![Context menu of StringLibraryTest dependencies](./media/testing-library-with-visual-studio/add-reference-context-menu.png)</span></span>

1. <span data-ttu-id="d05e2-127">**Başvuru Yöneticisi** iletişim kutusunda, **Projeler** düğümünü genişletin ve **StringLibrary**' ın yanındaki kutuyu işaretleyin.</span><span class="sxs-lookup"><span data-stu-id="d05e2-127">In the **Reference Manager** dialog, expand the **Projects** node and check the box next to **StringLibrary**.</span></span> <span data-ttu-id="d05e2-128">`StringLibrary` derlemesine bir başvuru eklemek derleyicinin **StringLibrary** yöntemlerini bulmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="d05e2-128">Adding a reference to the `StringLibrary` assembly allows the compiler to find **StringLibrary** methods.</span></span> <span data-ttu-id="d05e2-129">**Tamam** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="d05e2-129">Select the **OK** button.</span></span> <span data-ttu-id="d05e2-130">`StringLibrary`sınıf kitaplığı projenize bir başvuru eklenir.</span><span class="sxs-lookup"><span data-stu-id="d05e2-130">A reference is added to your class library project, `StringLibrary`.</span></span>

   ![Visual Studio 'da başvuru Yöneticisi iletişim kutusu](./media/testing-library-with-visual-studio/project-reference-manager.png)

## <a name="add-and-run-unit-test-methods"></a><span data-ttu-id="d05e2-132">Birim testi yöntemleri ekleme ve çalıştırma</span><span class="sxs-lookup"><span data-stu-id="d05e2-132">Add and run unit test methods</span></span>

<span data-ttu-id="d05e2-133">Visual Studio bir birim testi çalıştırdığında, bir birim testi sınıfında <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> özniteliğiyle işaretlenmiş her bir yöntemi yürütür, bu sınıf, <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> özniteliği uygulandı.</span><span class="sxs-lookup"><span data-stu-id="d05e2-133">When Visual Studio runs a unit test, it executes each method that is marked with the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> attribute in a unit test class, the class to which the  <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> attribute is applied.</span></span> <span data-ttu-id="d05e2-134">İlk hata bulunduğunda veya yöntemde bulunan tüm testler başarılı olduğunda bir test yöntemi sonlanır.</span><span class="sxs-lookup"><span data-stu-id="d05e2-134">A test method ends when the first failure is found or when all tests contained in the method have succeeded.</span></span>

<span data-ttu-id="d05e2-135">En yaygın testler <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> sınıfının üyelerini çağırır.</span><span class="sxs-lookup"><span data-stu-id="d05e2-135">The most common tests call members of the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> class.</span></span> <span data-ttu-id="d05e2-136">Birçok onaylama yöntemi, biri beklenen test sonucu ve diğeri de gerçek test sonucu olan en az iki parametre içerir.</span><span class="sxs-lookup"><span data-stu-id="d05e2-136">Many assert methods include at least two parameters, one of which is the expected test result and the other of which is the actual test result.</span></span> <span data-ttu-id="d05e2-137">`Assert` sınıfının en sık çağrılan yöntemlerin bazıları aşağıdaki tabloda gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="d05e2-137">Some of the `Assert` class's most frequently called methods are shown in the following table:</span></span>

| <span data-ttu-id="d05e2-138">Onaylama yöntemleri</span><span class="sxs-lookup"><span data-stu-id="d05e2-138">Assert methods</span></span>     | <span data-ttu-id="d05e2-139">İşlev</span><span class="sxs-lookup"><span data-stu-id="d05e2-139">Function</span></span> |
| ------------------ | -------- |
| `Assert.AreEqual`  | <span data-ttu-id="d05e2-140">İki değerin veya nesnenin eşit olduğunu doğrular.</span><span class="sxs-lookup"><span data-stu-id="d05e2-140">Verifies that two values or objects are equal.</span></span> <span data-ttu-id="d05e2-141">Değerler veya nesneler eşitse onaylama başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="d05e2-141">The assert fails if the values or objects aren't equal.</span></span> |
| `Assert.AreSame`   | <span data-ttu-id="d05e2-142">İki nesne değişkeninin aynı nesneye başvurmasını doğrular.</span><span class="sxs-lookup"><span data-stu-id="d05e2-142">Verifies that two object variables refer to the same object.</span></span> <span data-ttu-id="d05e2-143">Değişkenler farklı nesnelere başvuru yaptığında onaylama başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="d05e2-143">The assert fails if the variables refer to different objects.</span></span> |
| `Assert.IsFalse`   | <span data-ttu-id="d05e2-144">Bir koşulun `false`olduğunu doğrular.</span><span class="sxs-lookup"><span data-stu-id="d05e2-144">Verifies that a condition is `false`.</span></span> <span data-ttu-id="d05e2-145">Koşul `true`, onaylama başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="d05e2-145">The assert fails if the condition is `true`.</span></span> |
| `Assert.IsNotNull` | <span data-ttu-id="d05e2-146">Bir nesnenin `null`olmadığını doğrular.</span><span class="sxs-lookup"><span data-stu-id="d05e2-146">Verifies that an object isn't `null`.</span></span> <span data-ttu-id="d05e2-147">Nesne `null`, onaylama başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="d05e2-147">The assert fails if the object is `null`.</span></span> |

<span data-ttu-id="d05e2-148">Ayrıca, oluşturması beklenen özel durum türünü belirtmek için bir test yönteminde <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A> yöntemini de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d05e2-148">You can also use the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A> method in a test method to indicate the type of exception it's expected to throw.</span></span> <span data-ttu-id="d05e2-149">Belirtilen özel durum atılmazsa, test başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="d05e2-149">The test fails if the specified exception isn't thrown.</span></span>

<span data-ttu-id="d05e2-150">`StringLibrary.StartsWithUpper` yöntemini test ederken, büyük harfli bir karakterle başlayan bir dizi dize sağlamak istersiniz.</span><span class="sxs-lookup"><span data-stu-id="d05e2-150">In testing the `StringLibrary.StartsWithUpper` method, you want to provide a number of strings that begin with an uppercase character.</span></span> <span data-ttu-id="d05e2-151">Yöntemi bu durumlarda `true` döndürecek şekilde beklediğinizi, <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue%2A> yöntemini çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d05e2-151">You expect the method to return `true` in these cases, so you can call the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue%2A> method.</span></span> <span data-ttu-id="d05e2-152">Benzer şekilde, büyük harfli bir karakter ile başlayan bir dizi dize sağlamak istersiniz.</span><span class="sxs-lookup"><span data-stu-id="d05e2-152">Similarly, you want to provide a number of strings that begin with something other than an uppercase character.</span></span> <span data-ttu-id="d05e2-153">Yöntemi bu durumlarda `false` döndürecek şekilde beklediğinizi, <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse%2A> yöntemini çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d05e2-153">You expect the method to return `false` in these cases, so you can call the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse%2A> method.</span></span>

<span data-ttu-id="d05e2-154">Kitaplık yönteminiz dizeleri yaptığından, ayrıca [boş bir dizeyi (`String.Empty`) başarılı bir şekilde ()](xref:System.String.Empty), hiçbir karakteri olmayan geçerli bir dizeyi ve <xref:System.String.Length> 0 olan `null` bir dizeyi başarıyla işlemesini sağlamak isteyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="d05e2-154">Since your library method handles strings, you also want to make sure that it successfully handles an [empty string (`String.Empty`)](xref:System.String.Empty), a valid string that has no characters and whose <xref:System.String.Length> is 0, and a `null` string that hasn't been initialized.</span></span> <span data-ttu-id="d05e2-155">`StartsWithUpper` bir <xref:System.String> örneğinde uzantı yöntemi olarak çağrılırsa, `null` bir dize geçirilebilir.</span><span class="sxs-lookup"><span data-stu-id="d05e2-155">If `StartsWithUpper` is called as an extension method on a <xref:System.String> instance, it can't be passed a `null` string.</span></span> <span data-ttu-id="d05e2-156">Ancak, bunu doğrudan statik bir yöntem olarak çağırabilir ve tek bir <xref:System.String> bağımsız değişkeni geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d05e2-156">However, you can also call it directly as a static method and pass a single <xref:System.String> argument.</span></span>

<span data-ttu-id="d05e2-157">Her biri bir dize dizisindeki her öğe için sürekli olarak <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> yöntemi çağıran üç yöntem tanımlayacaksınız.</span><span class="sxs-lookup"><span data-stu-id="d05e2-157">You'll define three methods, each of which calls an <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> method repeatedly for each element in a string array.</span></span> <span data-ttu-id="d05e2-158">İlk hatayı bulduğunda test yöntemi başarısız olduğundan, yöntem çağrısında kullanılan dize değerini gösteren bir dize geçirmenize izin veren bir yöntem aşırı yüklemesi çağıracaksınız.</span><span class="sxs-lookup"><span data-stu-id="d05e2-158">Because the test method fails as soon as it finds the first failure, you'll call a method overload that allows you to pass a string that indicates the string value used in the method call.</span></span>

<span data-ttu-id="d05e2-159">Test yöntemleri oluşturmak için:</span><span class="sxs-lookup"><span data-stu-id="d05e2-159">To create the test methods:</span></span>

1. <span data-ttu-id="d05e2-160">*UnitTest1.cs* veya *UnitTest1. vb* kodu penceresinde, kodu aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="d05e2-160">In the *UnitTest1.cs* or *UnitTest1.vb* code window, replace the code with the following code:</span></span>

   [!code-csharp[Test#1](~/samples/snippets/csharp/getting_started/with_visual_studio_2017/testlib1.cs)]
   [!code-vb[Test#1](~/samples/snippets/core/tutorials/vb-library-with-visual-studio/testlib.vb)]

   <span data-ttu-id="d05e2-161">`TestStartsWithUpper` yönteminde büyük harfli karakterlerin testi, Yunanca Büyük Harf Alpha (U + 0391) ve Kiril Büyük harf EM (U + 041C) içerir.</span><span class="sxs-lookup"><span data-stu-id="d05e2-161">The test of uppercase characters in the `TestStartsWithUpper` method includes the Greek capital letter alpha (U+0391) and the Cyrillic capital letter EM (U+041C).</span></span> <span data-ttu-id="d05e2-162">`TestDoesNotStartWithUpper` yönteminde küçük harfli karakterlerin testi, Yunanca Küçük Harf Alpha (U + 03B1) ve Kiril Küçük harf GHE (U + 0433) içerir.</span><span class="sxs-lookup"><span data-stu-id="d05e2-162">The test of lowercase characters in the `TestDoesNotStartWithUpper` method includes the Greek small letter alpha (U+03B1) and the Cyrillic small letter Ghe (U+0433).</span></span>

1. <span data-ttu-id="d05e2-163">Menü çubuğunda **Dosya** ' yı seçin > **UnitTest1.cs as** veya **Dosya** kaydet > **UnitTest1. vb dosyasını kaydedin**.</span><span class="sxs-lookup"><span data-stu-id="d05e2-163">On the menu bar, select **File** > **Save UnitTest1.cs As** or **File** > **Save UnitTest1.vb As**.</span></span> <span data-ttu-id="d05e2-164">**Dosyayı farklı kaydet** Iletişim kutusunda **Kaydet** düğmesinin yanındaki oku seçin ve **kodlamayla kaydet**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="d05e2-164">In the **Save File As** dialog, select the arrow beside the **Save** button, and select **Save with Encoding**.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="d05e2-165">Visual Studio dosyayı farklı Kaydet iletişim kutusunu ![](./media/testing-library-with-visual-studio/save-file-as-dialog.png)</span><span class="sxs-lookup"><span data-stu-id="d05e2-165">![Visual Studio Save File As dialog](./media/testing-library-with-visual-studio/save-file-as-dialog.png)</span></span>

1. <span data-ttu-id="d05e2-166">**Farklı kaydet** iletişim kutusunda, dosyayı kaydetmek için **Evet** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="d05e2-166">In the **Confirm Save As** dialog, select the **Yes** button to save the file.</span></span>

1. <span data-ttu-id="d05e2-167">**Gelişmiş kaydetme seçenekleri** iletişim kutusunda, **kodlama** açılan LISTESINDEN **Unicode (imzayla UTF-8)-kod sayfası 65001** ' i seçin ve **Tamam**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="d05e2-167">In the **Advanced Save Options** dialog, select **Unicode (UTF-8 with signature) - Codepage 65001** from the **Encoding** drop-down list and select **OK**.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="d05e2-168">Visual Studio Gelişmiş kaydetme seçenekleri iletişim ![](./media/testing-library-with-visual-studio/advanced-save-options.png)</span><span class="sxs-lookup"><span data-stu-id="d05e2-168">![Visual Studio Advanced Save Options dialog](./media/testing-library-with-visual-studio/advanced-save-options.png)</span></span>

   <span data-ttu-id="d05e2-169">Kaynak kodunuzu UTF8 kodlu bir dosya olarak kaydedemeyebilirsiniz, Visual Studio bunu bir ASCII dosyası olarak kaydedebilir.</span><span class="sxs-lookup"><span data-stu-id="d05e2-169">If you fail to save your source code as a UTF8-encoded file, Visual Studio may save it as an ASCII file.</span></span> <span data-ttu-id="d05e2-170">Söz konusu olduğunda, çalışma zamanı, ASCII aralığının dışında UTF8 karakterlerinin kodunu doğru şekilde çözmez ve test sonuçları doğru olmayacaktır.</span><span class="sxs-lookup"><span data-stu-id="d05e2-170">When that happens, the runtime doesn't accurately decode the UTF8 characters outside of the ASCII range, and the test results won't be correct.</span></span>

1. <span data-ttu-id="d05e2-171">Menü çubuğunda **Test** > **Tüm testler** > **Çalıştır** ' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="d05e2-171">On the menu bar, select **Test** > **Run** > **All Tests**.</span></span> <span data-ttu-id="d05e2-172">**Test Gezgini** penceresi açılır ve testlerin başarıyla çalıştığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d05e2-172">The **Test Explorer** window opens and shows that the tests ran successfully.</span></span> <span data-ttu-id="d05e2-173">**Geçen testler** bölümünde üç test listelenir ve **Özet** bölümü Test çalıştırmasının sonucunu raporlar.</span><span class="sxs-lookup"><span data-stu-id="d05e2-173">The three tests are listed in the **Passed Tests** section, and the **Summary** section reports the result of the test run.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="d05e2-174">testleri geçirerek test Gezgini penceresini ![](./media/testing-library-with-visual-studio/test-explorer-window.png)</span><span class="sxs-lookup"><span data-stu-id="d05e2-174">![Test Explorer window with passing tests](./media/testing-library-with-visual-studio/test-explorer-window.png)</span></span>

## <a name="handle-test-failures"></a><span data-ttu-id="d05e2-175">Test başarısızlıklarını işle</span><span class="sxs-lookup"><span data-stu-id="d05e2-175">Handle test failures</span></span>

<span data-ttu-id="d05e2-176">Test çalıştırmasında hata yoktu, ancak test yöntemlerinden birinin başarısız olması için biraz değiştirin:</span><span class="sxs-lookup"><span data-stu-id="d05e2-176">Your test run had no failures, but change it slightly so that one of the test methods fails:</span></span>

1. <span data-ttu-id="d05e2-177">`TestDoesNotStartWithUpper` yönteminde `words` diziyi, "Error" dizesini içerecek şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="d05e2-177">Modify the `words` array in the `TestDoesNotStartWithUpper` method to include the string "Error".</span></span> <span data-ttu-id="d05e2-178">Testleri çalıştırmak için bir çözüm oluşturulduğunda Visual Studio açık dosyaları otomatik olarak kaydettiği için dosyayı kaydetmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="d05e2-178">You don't need to save the file because Visual Studio automatically saves open files when a solution is built to run tests.</span></span>

   ```csharp
   string[] words = { "alphabet", "Error", "zebra", "abc", "αυτοκινητοβιομηχανία", "государство",
                      "1234", ".", ";", " " };
   ```

   ```vb
   Dim words() As String = { "alphabet", "Error", "zebra", "abc", "αυτοκινητοβιομηχανία", "государство",
                      "1234", ".", ";", " " }

   ```

1. <span data-ttu-id="d05e2-179">**Test > menü** çubuğundan **tüm testleri** > **Çalıştır** öğesini seçerek testi çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="d05e2-179">Run the test by selecting **Test** > **Run** > **All Tests** from the menu bar.</span></span> <span data-ttu-id="d05e2-180">**Test Gezgini** penceresi, iki testin başarılı olduğunu ve bir başarısız olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="d05e2-180">The **Test Explorer** window indicates that two tests succeeded and one failed.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="d05e2-181">Test Gezgini penceresini başarısız testlerle ![](./media/testing-library-with-visual-studio/failed-test-window.png)</span><span class="sxs-lookup"><span data-stu-id="d05e2-181">![Test Explorer window with failing tests](./media/testing-library-with-visual-studio/failed-test-window.png)</span></span>

1. <span data-ttu-id="d05e2-182">Başarısız testi seçin, `TestDoesNotStartWith`.</span><span class="sxs-lookup"><span data-stu-id="d05e2-182">Select the failed test, `TestDoesNotStartWith`.</span></span> <span data-ttu-id="d05e2-183">**Test Gezgini** penceresi onay tarafından oluşturulan iletiyi görüntüler: "onaylama. IsFalse başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="d05e2-183">The **Test Explorer** window displays the message produced by the assert: "Assert.IsFalse failed.</span></span> <span data-ttu-id="d05e2-184">' Error ' bekleniyor: false; gerçek: true ".</span><span class="sxs-lookup"><span data-stu-id="d05e2-184">Expected for 'Error': false; actual: True".</span></span> <span data-ttu-id="d05e2-185">Hata nedeniyle "hata" sonunda dizideki tüm dizeler sınanmadı.</span><span class="sxs-lookup"><span data-stu-id="d05e2-185">Because of the failure, all strings in the array after "Error" weren't tested.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="d05e2-186">IsFalse onaylama başarısızlığını gösteren test Gezgini penceresi ![](./media/testing-library-with-visual-studio/failed-test-detail.png)</span><span class="sxs-lookup"><span data-stu-id="d05e2-186">![Test Explorer window showing the IsFalse assertion failure](./media/testing-library-with-visual-studio/failed-test-detail.png)</span></span>

1. <span data-ttu-id="d05e2-187">Adım 1 ' de yaptığınız değişikliği geri alın ve "hata" dizesini kaldırın.</span><span class="sxs-lookup"><span data-stu-id="d05e2-187">Undo the modification you did in step 1 and remove the string "Error".</span></span> <span data-ttu-id="d05e2-188">Testi yeniden çalıştırın ve testler geçer.</span><span class="sxs-lookup"><span data-stu-id="d05e2-188">Rerun the test and the tests will pass.</span></span>

## <a name="test-the-release-version-of-the-library"></a><span data-ttu-id="d05e2-189">Kitaplığın yayın sürümünü test etme</span><span class="sxs-lookup"><span data-stu-id="d05e2-189">Test the Release version of the library</span></span>

<span data-ttu-id="d05e2-190">Testlerinizi kitaplığın hata ayıklama sürümüne karşı çalıştırıyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="d05e2-190">You've been running your tests against the Debug version of the library.</span></span> <span data-ttu-id="d05e2-191">Artık testleriniz başarılı olduğuna ve kitaplığınızı yeterince test edinceye kadar, bu testleri kitaplığın yayın derlemesi için ek bir zaman çalıştırmalısınız.</span><span class="sxs-lookup"><span data-stu-id="d05e2-191">Now that your tests have all passed and you've adequately tested your library, you should run the tests an additional time against the Release build of the library.</span></span> <span data-ttu-id="d05e2-192">Derleyici iyileştirmeleri dahil olmak üzere bir dizi etken bazen hata ayıklama ve yayın yapıları arasında farklı davranışlar üretebilir.</span><span class="sxs-lookup"><span data-stu-id="d05e2-192">A number of factors, including compiler optimizations, can sometimes produce different behavior between Debug and Release builds.</span></span>

<span data-ttu-id="d05e2-193">Yayın derlemesini test etmek için:</span><span class="sxs-lookup"><span data-stu-id="d05e2-193">To test the Release build:</span></span>

1. <span data-ttu-id="d05e2-194">Visual Studio araç çubuğunda, derleme yapılandırmasını **Debug** iken **Release**olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="d05e2-194">In the Visual Studio toolbar, change the build configuration from **Debug** to **Release**.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="d05e2-195">Yayın derlemesi vurgulanan Visual Studio araç çubuğunu ![](./media/testing-library-with-visual-studio/visual-studio-toolbar-release.png)</span><span class="sxs-lookup"><span data-stu-id="d05e2-195">![Visual Studio toolbar with release build highlighted](./media/testing-library-with-visual-studio/visual-studio-toolbar-release.png)</span></span>

1. <span data-ttu-id="d05e2-196">**Çözüm Gezgini**, **StringLibrary** projesine sağ tıklayın ve kitaplığı yeniden derlemek için bağlam menüsünden **Oluştur** ' u seçin.</span><span class="sxs-lookup"><span data-stu-id="d05e2-196">In **Solution Explorer**, right-click the **StringLibrary** project and select **Build** from the context menu to recompile the library.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="d05e2-197">Build komutuyla ![StringLibrary bağlam menüsü](./media/testing-library-with-visual-studio/build-library-context-menu.png)</span><span class="sxs-lookup"><span data-stu-id="d05e2-197">![StringLibrary context menu with build command](./media/testing-library-with-visual-studio/build-library-context-menu.png)</span></span>

1. <span data-ttu-id="d05e2-198">**Test** > menü çubuğundan **tüm testleri** > **Çalıştır** öğesini seçerek birim testlerini çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="d05e2-198">Run the unit tests by choosing **Test** > **Run** > **All Tests** from the menu bar.</span></span> <span data-ttu-id="d05e2-199">Testler geçer.</span><span class="sxs-lookup"><span data-stu-id="d05e2-199">The tests pass.</span></span>

<span data-ttu-id="d05e2-200">Artık kitaplığınızı test etmeyi tamamladığınıza göre, bir sonraki adım çağıranlar tarafından kullanılabilir hale gelir.</span><span class="sxs-lookup"><span data-stu-id="d05e2-200">Now that you've finished testing your library, the next step is to make it available to callers.</span></span> <span data-ttu-id="d05e2-201">Bunu bir veya daha fazla uygulamayla paketleyebilir veya bir NuGet paketi olarak dağıtabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d05e2-201">You can bundle it with one or more applications, or you can distribute it as a NuGet package.</span></span> <span data-ttu-id="d05e2-202">Daha fazla bilgi için bkz. [.NET Standard sınıf kitaplığı](consuming-library-with-visual-studio.md)kullanma.</span><span class="sxs-lookup"><span data-stu-id="d05e2-202">For more information, see [Consuming a .NET Standard Class Library](consuming-library-with-visual-studio.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d05e2-203">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d05e2-203">See also</span></span>

- [<span data-ttu-id="d05e2-204">Birim testi temelleri-Visual Studio</span><span class="sxs-lookup"><span data-stu-id="d05e2-204">Unit test basics - Visual Studio</span></span>](/visualstudio/test/unit-test-basics)
