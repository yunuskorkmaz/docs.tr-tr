---
title: .NET Standart sınıf kitaplığını Visual Studio'da .NET Core ile test edin
description: .NET Core sınıf kitaplığınız için bir birim test projesi oluşturun. .NET Core sınıf kitaplığınızın birim testleriyle doğru çalıştığını doğrulayın.
ms.date: 12/24/2019
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet, seodoc18
ms.openlocfilehash: 307261088f5c7c69c0e69fbd6b99940c04842eec
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78156627"
---
# <a name="test-a-net-standard-library-with-net-core-in-visual-studio"></a><span data-ttu-id="628cc-104">.NET Standart kitaplığını .NET Core ile Visual Studio'da test edin</span><span class="sxs-lookup"><span data-stu-id="628cc-104">Test a .NET Standard library with .NET Core in Visual Studio</span></span>

<span data-ttu-id="628cc-105">[Visual Studio'da bir .NET Standart kitaplık oluşturun'da,](library-with-visual-studio.md) <xref:System.String> sınıfa uzantı yöntemi ekleyen basit bir sınıf kitaplığı oluşturdunuz.</span><span class="sxs-lookup"><span data-stu-id="628cc-105">In [Build a .NET Standard library in Visual Studio](library-with-visual-studio.md), you created a simple class library that adds an extension method to the <xref:System.String> class.</span></span> <span data-ttu-id="628cc-106">Şimdi, beklendiği gibi çalıştığından emin olmak için bir birim testi oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="628cc-106">Now, you'll create a unit test to make sure that it works as expected.</span></span> <span data-ttu-id="628cc-107">Birim test projenizi önceki makalede oluşturduğunuz çözüme eklersiniz.</span><span class="sxs-lookup"><span data-stu-id="628cc-107">You'll add your unit test project to the solution you created in the previous article.</span></span>

## <a name="create-a-unit-test-project"></a><span data-ttu-id="628cc-108">Birim testi projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="628cc-108">Create a unit test project</span></span>

<span data-ttu-id="628cc-109">Birim test projesini oluşturmak için aşağıdakileri yapın:</span><span class="sxs-lookup"><span data-stu-id="628cc-109">To create the unit test project, do the following:</span></span>

1. <span data-ttu-id="628cc-110">Visual `ClassLibraryProjects` Studio makalesinde [Bir .NET Standart kitaplığı oluştur'da](library-with-visual-studio.md) oluşturduğunuz çözümü açın.</span><span class="sxs-lookup"><span data-stu-id="628cc-110">Open the `ClassLibraryProjects` solution you created in the [Build a .NET Standard library in Visual Studio](library-with-visual-studio.md) article.</span></span>

1. <span data-ttu-id="628cc-111">Çözüme "StringLibraryTest" adlı yeni bir birim test projesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="628cc-111">Add a new unit test project named "StringLibraryTest" to the solution.</span></span>

   1. <span data-ttu-id="628cc-112">**Solution Explorer'da** çözüme sağ tıklayın ve**Yeni proje** **Ekle'yi** > seçin.</span><span class="sxs-lookup"><span data-stu-id="628cc-112">Right-click on the solution in **Solution Explorer** and select **Add** > **New project**.</span></span>

   1. <span data-ttu-id="628cc-113">Yeni **bir proje ekle** sayfasında, arama kutusuna **mstest** girin.</span><span class="sxs-lookup"><span data-stu-id="628cc-113">On the **Add a new project** page, enter **mstest** in the search box.</span></span> <span data-ttu-id="628cc-114">Dil listesinden **C#** veya **Visual Basic'i** seçin ve ardından Platform listesindeki **tüm platformları** seçin.</span><span class="sxs-lookup"><span data-stu-id="628cc-114">Choose **C#** or **Visual Basic** from the Language list, and then choose **All platforms** from the Platform list.</span></span> <span data-ttu-id="628cc-115">**MsTest Test Project (.NET Core)** şablonunu seçin ve ardından **İleri'yi**seçin.</span><span class="sxs-lookup"><span data-stu-id="628cc-115">Choose the **MsTest Test Project (.NET Core)** template, and then choose **Next**.</span></span>

   1. <span data-ttu-id="628cc-116">Yeni **proje sayfanızı Yapılandır'da,** Project **ad** kutusuna **StringLibraryTest'i** girin.</span><span class="sxs-lookup"><span data-stu-id="628cc-116">On the **Configure your new project** page, enter **StringLibraryTest** in the **Project name** box.</span></span> <span data-ttu-id="628cc-117">Ardından **Oluştur**’u seçin.</span><span class="sxs-lookup"><span data-stu-id="628cc-117">Then choose **Create**.</span></span>

   > [!NOTE]
   > <span data-ttu-id="628cc-118">MSTest'e ek olarak Visual Studio'da .NET Core için xUnit ve nUnit test projeleri de oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="628cc-118">In addition to an MSTest, you can also create xUnit and nUnit test projects for .NET Core in Visual Studio.</span></span>

1. <span data-ttu-id="628cc-119">Visual Studio projeyi oluşturur ve kod penceresindeki sınıf dosyasını aşağıdaki kodla açar:</span><span class="sxs-lookup"><span data-stu-id="628cc-119">Visual Studio creates the project and opens the class file in the code window with the following code:</span></span>

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

   <span data-ttu-id="628cc-120">Birim test şablonu tarafından oluşturulan kaynak kodu aşağıdakileri yapar:</span><span class="sxs-lookup"><span data-stu-id="628cc-120">The source code created by the unit test template does the following:</span></span>

   - <span data-ttu-id="628cc-121">Birim sınama <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=nameWithType> için kullanılan türleri içeren ad alanını içeri iter.</span><span class="sxs-lookup"><span data-stu-id="628cc-121">It imports the <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=nameWithType> namespace, which contains the types used for unit testing.</span></span>

   - <span data-ttu-id="628cc-122">[TestClass](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute) özniteliğini `UnitTest1` sınıfa uygular.</span><span class="sxs-lookup"><span data-stu-id="628cc-122">It applies the [TestClass](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute) attribute to the `UnitTest1` class.</span></span> <span data-ttu-id="628cc-123">[Test Yöntemi](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) özniteliği ile etiketlenmiş bir test sınıfındaki her test yöntemi, birim testi çalıştırıldığında otomatik olarak çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="628cc-123">Each test method in a test class tagged with the [TestMethod](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) attribute is executed automatically when the unit test is run.</span></span>

   - <span data-ttu-id="628cc-124">Birim testi çalıştırıldığında otomatik yürütme `TestMethod1` için bir `TestSub` test yöntemi olarak C# veya Visual Basic'te tanımlamak için [TestYöntemi](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) özniteliğiuygular.</span><span class="sxs-lookup"><span data-stu-id="628cc-124">It applies the [TestMethod](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) attribute to define `TestMethod1` in C# or `TestSub` in Visual Basic as a test method for automatic execution when the unit test is run.</span></span>

1. <span data-ttu-id="628cc-125">**Çözüm Gezgini'nde** **StringLibraryTest** projesinin **Bağımlılıklar** düğümüne sağ tıklayın ve bağlam menüsünden **Başvuru Ekle'yi** seçin.</span><span class="sxs-lookup"><span data-stu-id="628cc-125">In **Solution Explorer**, right-click the **Dependencies** node of the **StringLibraryTest** project and select **Add Reference** from the context menu.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="628cc-126">![StringLibraryTest bağımlılıkları bağlam menüsü](./media/testing-library-with-visual-studio/add-reference-context-menu.png)</span><span class="sxs-lookup"><span data-stu-id="628cc-126">![Context menu of StringLibraryTest dependencies](./media/testing-library-with-visual-studio/add-reference-context-menu.png)</span></span>

1. <span data-ttu-id="628cc-127">Başvuru **Yöneticisi** iletişim kutusunda, **Projeler** düğüm'üne genişletin ve **StringLibrary'nin**yanındaki kutuyu işaretleyin.</span><span class="sxs-lookup"><span data-stu-id="628cc-127">In the **Reference Manager** dialog, expand the **Projects** node and check the box next to **StringLibrary**.</span></span> <span data-ttu-id="628cc-128">`StringLibrary` Derlemeye bir başvuru eklemek, derleyicinin **StringLibrary** yöntemlerini bulmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="628cc-128">Adding a reference to the `StringLibrary` assembly allows the compiler to find **StringLibrary** methods.</span></span> <span data-ttu-id="628cc-129">**Tamam** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="628cc-129">Select the **OK** button.</span></span> <span data-ttu-id="628cc-130">Sınıf kitaplığı projenize bir `StringLibrary`başvuru eklenir.</span><span class="sxs-lookup"><span data-stu-id="628cc-130">A reference is added to your class library project, `StringLibrary`.</span></span>

   ![Visual Studio'da referans yöneticisi iletişim kutusu](./media/testing-library-with-visual-studio/project-reference-manager.png)

## <a name="add-and-run-unit-test-methods"></a><span data-ttu-id="628cc-132">Birim test yöntemleri ekleme ve çalıştırma</span><span class="sxs-lookup"><span data-stu-id="628cc-132">Add and run unit test methods</span></span>

<span data-ttu-id="628cc-133">Visual Studio bir birim testi çalıştırdığında, özniteliğin <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> uygulandığı sınıf <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> olan birim test sınıfında öznitelik ile işaretlenmiş her yöntemi yürütür.</span><span class="sxs-lookup"><span data-stu-id="628cc-133">When Visual Studio runs a unit test, it executes each method that is marked with the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> attribute in a unit test class, the class to which the  <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> attribute is applied.</span></span> <span data-ttu-id="628cc-134">İlk hata bulunduğunda veya yöntemde bulunan tüm testler başarılı olduğunda bir test yöntemi sona erer.</span><span class="sxs-lookup"><span data-stu-id="628cc-134">A test method ends when the first failure is found or when all tests contained in the method have succeeded.</span></span>

<span data-ttu-id="628cc-135">En yaygın testler <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> sınıfın üyelerini çağırır.</span><span class="sxs-lookup"><span data-stu-id="628cc-135">The most common tests call members of the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> class.</span></span> <span data-ttu-id="628cc-136">Birçok ileri alma yöntemi, biri beklenen test sonucu, diğeri gerçek test sonucu olmak üzere en az iki parametre içerir.</span><span class="sxs-lookup"><span data-stu-id="628cc-136">Many assert methods include at least two parameters, one of which is the expected test result and the other of which is the actual test result.</span></span> <span data-ttu-id="628cc-137">`Assert` Sınıfın en sık çağrılan yöntemlerinden bazıları aşağıdaki tabloda gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="628cc-137">Some of the `Assert` class's most frequently called methods are shown in the following table:</span></span>

| <span data-ttu-id="628cc-138">Öne koyma yöntemleri</span><span class="sxs-lookup"><span data-stu-id="628cc-138">Assert methods</span></span>     | <span data-ttu-id="628cc-139">İşlev</span><span class="sxs-lookup"><span data-stu-id="628cc-139">Function</span></span> |
| ------------------ | -------- |
| `Assert.AreEqual`  | <span data-ttu-id="628cc-140">İki değerin veya nesnenin eşit olduğunu doğrular.</span><span class="sxs-lookup"><span data-stu-id="628cc-140">Verifies that two values or objects are equal.</span></span> <span data-ttu-id="628cc-141">Değerler veya nesneler eşit değilse, ileri deyiş başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="628cc-141">The assert fails if the values or objects aren't equal.</span></span> |
| `Assert.AreSame`   | <span data-ttu-id="628cc-142">İki nesne değişkeninin aynı nesneye atıfta bulunduğunu doğrular.</span><span class="sxs-lookup"><span data-stu-id="628cc-142">Verifies that two object variables refer to the same object.</span></span> <span data-ttu-id="628cc-143">Değişkenler farklı nesnelere başvuruyorsa, assert başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="628cc-143">The assert fails if the variables refer to different objects.</span></span> |
| `Assert.IsFalse`   | <span data-ttu-id="628cc-144">Bir koşulun `false`.</span><span class="sxs-lookup"><span data-stu-id="628cc-144">Verifies that a condition is `false`.</span></span> <span data-ttu-id="628cc-145">Koşul `true`.</span><span class="sxs-lookup"><span data-stu-id="628cc-145">The assert fails if the condition is `true`.</span></span> |
| `Assert.IsNotNull` | <span data-ttu-id="628cc-146">Nesnenin olmadığını `null`doğrular.</span><span class="sxs-lookup"><span data-stu-id="628cc-146">Verifies that an object isn't `null`.</span></span> <span data-ttu-id="628cc-147">Nesne `null`.</span><span class="sxs-lookup"><span data-stu-id="628cc-147">The assert fails if the object is `null`.</span></span> |

<span data-ttu-id="628cc-148">Atması beklenen özel <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A> durum türünü belirtmek için yöntemi bir test yönteminde de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="628cc-148">You can also use the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A> method in a test method to indicate the type of exception it's expected to throw.</span></span> <span data-ttu-id="628cc-149">Belirtilen özel durum atılmıyorsa test başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="628cc-149">The test fails if the specified exception isn't thrown.</span></span>

<span data-ttu-id="628cc-150">`StringLibrary.StartsWithUpper` Yöntemi sınamak için, büyük harf karakteriyle başlayan bir dizi dize sağlamak istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="628cc-150">In testing the `StringLibrary.StartsWithUpper` method, you want to provide a number of strings that begin with an uppercase character.</span></span> <span data-ttu-id="628cc-151">Bu gibi durumlarda `true` yöntemin dönmesini beklersiniz, <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue%2A> böylece yöntemi arayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="628cc-151">You expect the method to return `true` in these cases, so you can call the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue%2A> method.</span></span> <span data-ttu-id="628cc-152">Benzer şekilde, büyük harf karakteri dışında bir şeyle başlayan dizeleri bir dizi sağlamak istiyorum.</span><span class="sxs-lookup"><span data-stu-id="628cc-152">Similarly, you want to provide a number of strings that begin with something other than an uppercase character.</span></span> <span data-ttu-id="628cc-153">Bu gibi durumlarda `false` yöntemin dönmesini beklersiniz, <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse%2A> böylece yöntemi arayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="628cc-153">You expect the method to return `false` in these cases, so you can call the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse%2A> method.</span></span>

<span data-ttu-id="628cc-154">Kitaplık yönteminiz dizeleri işlediğiiçin, boş bir [dizeyi ( )`String.Empty`,](xref:System.String.Empty)karakteri olmayan ve <xref:System.String.Length> 0 olan geçerli bir `null` dize ve baş harfe çevrilmiş bir dize yi başarıyla işlediğinden de emin olmak istersiniz.</span><span class="sxs-lookup"><span data-stu-id="628cc-154">Since your library method handles strings, you also want to make sure that it successfully handles an [empty string (`String.Empty`)](xref:System.String.Empty), a valid string that has no characters and whose <xref:System.String.Length> is 0, and a `null` string that hasn't been initialized.</span></span> <span data-ttu-id="628cc-155">`StartsWithUpper` Bir <xref:System.String> örnekte uzantı yöntemi olarak adlandırılırsa, bir `null` dize geçirilemeyecek.</span><span class="sxs-lookup"><span data-stu-id="628cc-155">If `StartsWithUpper` is called as an extension method on a <xref:System.String> instance, it can't be passed a `null` string.</span></span> <span data-ttu-id="628cc-156">Ancak, doğrudan statik bir yöntem olarak çağırabilir <xref:System.String> ve tek bir bağımsız değişken geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="628cc-156">However, you can also call it directly as a static method and pass a single <xref:System.String> argument.</span></span>

<span data-ttu-id="628cc-157">Dize dizisindeki her öğe için <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> tekrar tekrar bir yöntem çağıran üç yöntem tanımlarsınız.</span><span class="sxs-lookup"><span data-stu-id="628cc-157">You'll define three methods, each of which calls an <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> method repeatedly for each element in a string array.</span></span> <span data-ttu-id="628cc-158">Test yöntemi ilk hatayı bulur bulmaz başarısız olduğundan, yöntem çağrısında kullanılan dize değerini gösteren bir dize yi geçmenizi sağlayan bir yöntem aşırı yüklemesi çağırırsınız.</span><span class="sxs-lookup"><span data-stu-id="628cc-158">Because the test method fails as soon as it finds the first failure, you'll call a method overload that allows you to pass a string that indicates the string value used in the method call.</span></span>

<span data-ttu-id="628cc-159">Test yöntemlerini oluşturmak için:</span><span class="sxs-lookup"><span data-stu-id="628cc-159">To create the test methods:</span></span>

1. <span data-ttu-id="628cc-160">*UnitTest1.cs* veya *UnitTest1.vb* kod penceresinde, kodu aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="628cc-160">In the *UnitTest1.cs* or *UnitTest1.vb* code window, replace the code with the following code:</span></span>

   [!code-csharp[Test#1](~/samples/snippets/csharp/getting_started/with_visual_studio_2017/testlib1.cs)]
   [!code-vb[Test#1](~/samples/snippets/core/tutorials/vb-library-with-visual-studio/testlib.vb)]

   <span data-ttu-id="628cc-161">`TestStartsWithUpper` Yöntemdeki büyük harflerin testi, Yunan büyük harfi alfa (U+0391) ve Kiril büyük harfi EM 'yi (U+041C) içerir.</span><span class="sxs-lookup"><span data-stu-id="628cc-161">The test of uppercase characters in the `TestStartsWithUpper` method includes the Greek capital letter alpha (U+0391) and the Cyrillic capital letter EM (U+041C).</span></span> <span data-ttu-id="628cc-162">`TestDoesNotStartWithUpper` Yöntemde küçük harflerin testi Yunanca küçük alfa harfi (U+03B1) ve Kiril küçük harf Ghe (U+0433) içerir.</span><span class="sxs-lookup"><span data-stu-id="628cc-162">The test of lowercase characters in the `TestDoesNotStartWithUpper` method includes the Greek small letter alpha (U+03B1) and the Cyrillic small letter Ghe (U+0433).</span></span>

1. <span data-ttu-id="628cc-163">Menü çubuğunda **Dosya** > **Kaydet UnitTest1.cs** veya **Dosya** > Yı**Kaydet BirimiTest1.vb As'ı**seçin.</span><span class="sxs-lookup"><span data-stu-id="628cc-163">On the menu bar, select **File** > **Save UnitTest1.cs As** or **File** > **Save UnitTest1.vb As**.</span></span> <span data-ttu-id="628cc-164">**Dosyayı Kaydet** iletişim kutusunda, **Kaydet** düğmesinin yanındaki oku seçin ve **Kodlama ile Kaydet'i**seçin.</span><span class="sxs-lookup"><span data-stu-id="628cc-164">In the **Save File As** dialog, select the arrow beside the **Save** button, and select **Save with Encoding**.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="628cc-165">![Visual Studio Dosyayı İletişim Olarak Kaydet](./media/testing-library-with-visual-studio/save-file-as-dialog.png)</span><span class="sxs-lookup"><span data-stu-id="628cc-165">![Visual Studio Save File As dialog](./media/testing-library-with-visual-studio/save-file-as-dialog.png)</span></span>

1. <span data-ttu-id="628cc-166">**Kaydet'i Doğrula** iletişim kutusunda, dosyayı kaydetmek için **Evet** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="628cc-166">In the **Confirm Save As** dialog, select the **Yes** button to save the file.</span></span>

1. <span data-ttu-id="628cc-167">Gelişmiş **Kaydet Seçenekleri** iletişim kutusunda, **Unicode'u (imzalı UTF-8) seçin -** **Kodlama** açılır listesinden Codepage 65001'i seçin ve **Tamam'ı**seçin.</span><span class="sxs-lookup"><span data-stu-id="628cc-167">In the **Advanced Save Options** dialog, select **Unicode (UTF-8 with signature) - Codepage 65001** from the **Encoding** drop-down list and select **OK**.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="628cc-168">![Visual Studio Gelişmiş Kaydet Seçenekleri iletişim kutusu](./media/testing-library-with-visual-studio/advanced-save-options.png)</span><span class="sxs-lookup"><span data-stu-id="628cc-168">![Visual Studio Advanced Save Options dialog](./media/testing-library-with-visual-studio/advanced-save-options.png)</span></span>

   <span data-ttu-id="628cc-169">Kaynak kodunuzu UTF8 kodlanmış bir dosya olarak kaydetmezseniz, Visual Studio dosyayı ASCII dosyası olarak kaydedebilir.</span><span class="sxs-lookup"><span data-stu-id="628cc-169">If you fail to save your source code as a UTF8-encoded file, Visual Studio may save it as an ASCII file.</span></span> <span data-ttu-id="628cc-170">Bu durumda, çalışma süresi ASCII aralığının dışındaki UTF8 karakterlerinin kodunu tam olarak çözmez ve test sonuçları doğru olmaz.</span><span class="sxs-lookup"><span data-stu-id="628cc-170">When that happens, the runtime doesn't accurately decode the UTF8 characters outside of the ASCII range, and the test results won't be correct.</span></span>

1. <span data-ttu-id="628cc-171">Menü çubuğunda,**Tüm Testleri** **Test** > **Edin'i** > seçin.</span><span class="sxs-lookup"><span data-stu-id="628cc-171">On the menu bar, select **Test** > **Run** > **All Tests**.</span></span> <span data-ttu-id="628cc-172">**Test Gezgini** penceresi açılır ve testlerin başarılı bir şekilde çalıştırıldığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="628cc-172">The **Test Explorer** window opens and shows that the tests ran successfully.</span></span> <span data-ttu-id="628cc-173">Üç test **Geçti Testleri** bölümünde listelenir ve **Özet** bölümü test çalışmasının sonucunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="628cc-173">The three tests are listed in the **Passed Tests** section, and the **Summary** section reports the result of the test run.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="628cc-174">![Geçen testler ile Explorer'ı test edin penceresi](./media/testing-library-with-visual-studio/test-explorer-window.png)</span><span class="sxs-lookup"><span data-stu-id="628cc-174">![Test Explorer window with passing tests](./media/testing-library-with-visual-studio/test-explorer-window.png)</span></span>

## <a name="handle-test-failures"></a><span data-ttu-id="628cc-175">Test hatalarını işleme</span><span class="sxs-lookup"><span data-stu-id="628cc-175">Handle test failures</span></span>

<span data-ttu-id="628cc-176">Test çalışmanızda hiçbir hata yoktu, ancak test yöntemlerinden birinin başarısız olması için biraz değiştirin:</span><span class="sxs-lookup"><span data-stu-id="628cc-176">Your test run had no failures, but change it slightly so that one of the test methods fails:</span></span>

1. <span data-ttu-id="628cc-177">"Hata" dizesini `words` `TestDoesNotStartWithUpper` içerecek şekilde yöntemdeki diziyi değiştirin.</span><span class="sxs-lookup"><span data-stu-id="628cc-177">Modify the `words` array in the `TestDoesNotStartWithUpper` method to include the string "Error".</span></span> <span data-ttu-id="628cc-178">Visual Studio testleri çalıştırmak için bir çözüm oluşturulunca açık dosyaları otomatik olarak kaydettiğinden dosyayı kaydetmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="628cc-178">You don't need to save the file because Visual Studio automatically saves open files when a solution is built to run tests.</span></span>

   ```csharp
   string[] words = { "alphabet", "Error", "zebra", "abc", "αυτοκινητοβιομηχανία", "государство",
                      "1234", ".", ";", " " };
   ```

   ```vb
   Dim words() As String = { "alphabet", "Error", "zebra", "abc", "αυτοκινητοβιομηχανία", "государство",
                      "1234", ".", ";", " " }

   ```

1. <span data-ttu-id="628cc-179">Menü çubuğundan**Tüm Testleri** **Test** > **Edin'i** > seçerek testi çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="628cc-179">Run the test by selecting **Test** > **Run** > **All Tests** from the menu bar.</span></span> <span data-ttu-id="628cc-180">**Test Gezgini** penceresi, iki testin başarılı olduğunu ve birinin başarısız olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="628cc-180">The **Test Explorer** window indicates that two tests succeeded and one failed.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="628cc-181">![Başarısız testler ile Explorer penceresi test](./media/testing-library-with-visual-studio/failed-test-window.png)</span><span class="sxs-lookup"><span data-stu-id="628cc-181">![Test Explorer window with failing tests](./media/testing-library-with-visual-studio/failed-test-window.png)</span></span>

1. <span data-ttu-id="628cc-182">Başarısız testi `TestDoesNotStartWith`seçin.</span><span class="sxs-lookup"><span data-stu-id="628cc-182">Select the failed test, `TestDoesNotStartWith`.</span></span> <span data-ttu-id="628cc-183">**Test Gezgini** penceresi assert tarafından üretilen iletiyi görüntüler: "Assert.IsFalse başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="628cc-183">The **Test Explorer** window displays the message produced by the assert: "Assert.IsFalse failed.</span></span> <span data-ttu-id="628cc-184">'Hata' için beklenen: yanlış; gerçek: True".</span><span class="sxs-lookup"><span data-stu-id="628cc-184">Expected for 'Error': false; actual: True".</span></span> <span data-ttu-id="628cc-185">Hata nedeniyle, "Hata" sonra dizideki tüm dizeleri sınanmadı.</span><span class="sxs-lookup"><span data-stu-id="628cc-185">Because of the failure, all strings in the array after "Error" weren't tested.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="628cc-186">![IsFalse savması hatasını gösteren Sınayış penceresi](./media/testing-library-with-visual-studio/failed-test-detail.png)</span><span class="sxs-lookup"><span data-stu-id="628cc-186">![Test Explorer window showing the IsFalse assertion failure](./media/testing-library-with-visual-studio/failed-test-detail.png)</span></span>

1. <span data-ttu-id="628cc-187">Adım 1'de yaptığınız değişikliği geri alave ve "Hata" dizesini kaldırın.</span><span class="sxs-lookup"><span data-stu-id="628cc-187">Undo the modification you did in step 1 and remove the string "Error".</span></span> <span data-ttu-id="628cc-188">Testi yeniden çalıştırın ve testler geçsin.</span><span class="sxs-lookup"><span data-stu-id="628cc-188">Rerun the test and the tests will pass.</span></span>

## <a name="test-the-release-version-of-the-library"></a><span data-ttu-id="628cc-189">Kitaplığın Sürüm sürümünü sına</span><span class="sxs-lookup"><span data-stu-id="628cc-189">Test the Release version of the library</span></span>

<span data-ttu-id="628cc-190">Testlerinizi kitaplığın Hata Ayıklama sürümüne karşı çalıştırDınız.</span><span class="sxs-lookup"><span data-stu-id="628cc-190">You've been running your tests against the Debug version of the library.</span></span> <span data-ttu-id="628cc-191">Artık tüm testlerinizin tümü geçtiğine ve kitaplığınızı yeterince test ettiğinize göre, testleri kitaplığın Sürüm yapısına karşı ek bir süre çalıştırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="628cc-191">Now that your tests have all passed and you've adequately tested your library, you should run the tests an additional time against the Release build of the library.</span></span> <span data-ttu-id="628cc-192">Derleyici optimizasyonları da dahil olmak üzere bir dizi etken bazen Hata Ayıklama ve Sürüm oluşturmaları arasında farklı davranışlar oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="628cc-192">A number of factors, including compiler optimizations, can sometimes produce different behavior between Debug and Release builds.</span></span>

<span data-ttu-id="628cc-193">Sürüm oluşturmatest etmek için:</span><span class="sxs-lookup"><span data-stu-id="628cc-193">To test the Release build:</span></span>

1. <span data-ttu-id="628cc-194">Visual Studio araç çubuğunda, yapı yapılandırmasını **Hata Ayıklama'dan** **Sürüm'e**değiştirin.</span><span class="sxs-lookup"><span data-stu-id="628cc-194">In the Visual Studio toolbar, change the build configuration from **Debug** to **Release**.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="628cc-195">![Sürüm yapısı vurgulanmış Visual Studio araç çubuğu](./media/testing-library-with-visual-studio/visual-studio-toolbar-release.png)</span><span class="sxs-lookup"><span data-stu-id="628cc-195">![Visual Studio toolbar with release build highlighted](./media/testing-library-with-visual-studio/visual-studio-toolbar-release.png)</span></span>

1. <span data-ttu-id="628cc-196">**Çözüm Gezgini'nde** **StringLibrary** projesini sağ tıklatın ve kitaplığı yeniden derlemek için bağlam menüsünden **Oluştur'u** seçin.</span><span class="sxs-lookup"><span data-stu-id="628cc-196">In **Solution Explorer**, right-click the **StringLibrary** project and select **Build** from the context menu to recompile the library.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="628cc-197">![Yapı komutu ile StringLibrary bağlam menüsü](./media/testing-library-with-visual-studio/build-library-context-menu.png)</span><span class="sxs-lookup"><span data-stu-id="628cc-197">![StringLibrary context menu with build command](./media/testing-library-with-visual-studio/build-library-context-menu.png)</span></span>

1. <span data-ttu-id="628cc-198">Menü çubuğundan**Tüm Testleri** **Test** > **Çalıştır'ı** > seçerek birim testlerini çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="628cc-198">Run the unit tests by choosing **Test** > **Run** > **All Tests** from the menu bar.</span></span> <span data-ttu-id="628cc-199">Testler geçiyor.</span><span class="sxs-lookup"><span data-stu-id="628cc-199">The tests pass.</span></span>

<span data-ttu-id="628cc-200">Kitaplığınızı test etmeyi tamamladığınızda, bir sonraki adım, kitaplığı arayanların kullanımına açmaktır.</span><span class="sxs-lookup"><span data-stu-id="628cc-200">Now that you've finished testing your library, the next step is to make it available to callers.</span></span> <span data-ttu-id="628cc-201">Bir veya daha fazla uygulamayla paketleyebilir veya NuGet paketi olarak dağıtabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="628cc-201">You can bundle it with one or more applications, or you can distribute it as a NuGet package.</span></span> <span data-ttu-id="628cc-202">Daha fazla bilgi için [bkz.](consuming-library-with-visual-studio.md)</span><span class="sxs-lookup"><span data-stu-id="628cc-202">For more information, see [Consuming a .NET Standard Class Library](consuming-library-with-visual-studio.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="628cc-203">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="628cc-203">See also</span></span>

- [<span data-ttu-id="628cc-204">Ünite test temelleri - Visual Studio</span><span class="sxs-lookup"><span data-stu-id="628cc-204">Unit test basics - Visual Studio</span></span>](/visualstudio/test/unit-test-basics)
