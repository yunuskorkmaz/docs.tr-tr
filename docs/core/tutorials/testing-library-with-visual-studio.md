---
title: Visual Studio 2017 ' de .NET Core ile .NET Standard sınıf kitaplığı test etme
description: .NET Core sınıf kitaplığınız için bir birim testi projesi oluşturun. .NET Core sınıf kitaplığınızın birim testlerle düzgün çalıştığını doğrulayın.
author: BillWagner
ms.author: wiwagn
ms.date: 08/07/2017
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet, seodoc18
ms.openlocfilehash: 242234d93bc1b8f9b88749f2e3bcfb37c2bde86d
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73037973"
---
# <a name="test-a-net-standard-library-with-net-core-in-visual-studio-2017"></a><span data-ttu-id="dbf88-104">Visual Studio 2017’de NET Core ile bir .NET Standard kitaplığını test etme</span><span class="sxs-lookup"><span data-stu-id="dbf88-104">Test a .NET Standard library with .NET Core in Visual Studio 2017</span></span>

<span data-ttu-id="dbf88-105">[Visual studio 2017 ' de ve C# .net Core Ile .NET Standard kitaplığı oluşturun](library-with-visual-studio.md) veya [visual Studio 2017 ' de Visual Basic ve .NET Core ile bir .NET Standard kitaplığı oluşturun](vb-library-with-visual-studio.md)@no__t_ bir genişletme yöntemi ekleyen basit bir sınıf kitaplığı oluşturdunuz 3_ sınıfı.</span><span class="sxs-lookup"><span data-stu-id="dbf88-105">In [Build a .NET Standard library with C# and .NET Core in Visual Studio 2017](library-with-visual-studio.md) or [Build a .NET Standard library with Visual Basic and .NET Core in Visual Studio 2017](vb-library-with-visual-studio.md), you created a simple class library that adds an extension method to the <xref:System.String> class.</span></span> <span data-ttu-id="dbf88-106">Şimdi, beklendiği gibi çalıştığından emin olmak için bir birim testi oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="dbf88-106">Now, you'll create a unit test to make sure that it works as expected.</span></span> <span data-ttu-id="dbf88-107">Birim testi projenizi önceki makalede oluşturduğunuz çözüme ekleyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="dbf88-107">You'll add your unit test project to the solution you created in the previous article.</span></span>

## <a name="creating-a-unit-test-project"></a><span data-ttu-id="dbf88-108">Birim testi projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="dbf88-108">Creating a unit test project</span></span>

<span data-ttu-id="dbf88-109">Birim testi projesi oluşturmak için aşağıdakileri yapın:</span><span class="sxs-lookup"><span data-stu-id="dbf88-109">To create the unit test project, do the following:</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="ctabcsharp"></a>[<span data-ttu-id="dbf88-110">C#</span><span class="sxs-lookup"><span data-stu-id="dbf88-110">C#</span></span>](#tab/csharp)

1. <span data-ttu-id="dbf88-111">**Çözüm Gezgini**, **classlibraryprojects** çözüm düğümünün bağlam menüsünü açın ve > **Yeni proje** **Ekle** ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="dbf88-111">In **Solution Explorer**, open the context menu for the **ClassLibraryProjects** solution node and select **Add** > **New Project**.</span></span>

1. <span data-ttu-id="dbf88-112">**Yeni Proje Ekle** iletişim kutusunda  **C# görsel** düğümünü seçin.</span><span class="sxs-lookup"><span data-stu-id="dbf88-112">In the **Add New Project** dialog, select the **Visual C#** node.</span></span> <span data-ttu-id="dbf88-113">Ardından, **.NET Core** düğümünü ve ardından **MSTest test projesi (.NET Core)** proje şablonunu seçin.</span><span class="sxs-lookup"><span data-stu-id="dbf88-113">Then select the **.NET Core** node followed by the **MSTest Test Project (.NET Core)** project template.</span></span> <span data-ttu-id="dbf88-114">**Ad** metin kutusuna projenin adı olarak "StringLibraryTest" yazın.</span><span class="sxs-lookup"><span data-stu-id="dbf88-114">In the **Name** text box, enter "StringLibraryTest" as the name of the project.</span></span> <span data-ttu-id="dbf88-115">Birim testi projesini oluşturmak için **Tamam ' ı** seçin.</span><span class="sxs-lookup"><span data-stu-id="dbf88-115">Select **OK** to create the unit test project.</span></span>

   ![Birim testi projesi görüntülenirken yeni proje iletişim kutusu Ekle-C#](./media/testing-library-with-visual-studio/create-new-test-project.png)

   > [!NOTE]  
   > <span data-ttu-id="dbf88-117">Bir MSTest test projesine ek olarak, .NET Core için bir xUnit test projesi oluşturmak üzere Visual Studio 'Yu da kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dbf88-117">In addition to an MSTest Test project, you can also use Visual Studio to create an xUnit test project for .NET Core.</span></span>

1. <span data-ttu-id="dbf88-118">Visual Studio projeyi oluşturur ve kod penceresinde *UnitTest1.cs* dosyasını açar.</span><span class="sxs-lookup"><span data-stu-id="dbf88-118">Visual Studio creates the project and opens the *UnitTest1.cs* file in the code window.</span></span>

   ![Birim testi proje sınıfı ve yöntemi için Visual Studio Code penceresi-C#](./media/testing-library-with-visual-studio/unit-test-editor-window.png)

   <span data-ttu-id="dbf88-120">Birim testi şablonu tarafından oluşturulan kaynak kodu aşağıdakileri yapar:</span><span class="sxs-lookup"><span data-stu-id="dbf88-120">The source code created by the unit test template does the following:</span></span>

   - <span data-ttu-id="dbf88-121">Birim testi için kullanılan türleri içeren <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=nameWithType> ad alanını içeri aktarır.</span><span class="sxs-lookup"><span data-stu-id="dbf88-121">It imports the <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=nameWithType> namespace, which contains the types used for unit testing.</span></span>

   - <span data-ttu-id="dbf88-122">`UnitTest1` sınıfına <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> özniteliğini uygular.</span><span class="sxs-lookup"><span data-stu-id="dbf88-122">It applies the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> attribute to the `UnitTest1` class.</span></span> <span data-ttu-id="dbf88-123">\[TestMethod\] özniteliğiyle etiketlenmiş bir test sınıfındaki her test yöntemi, birim testi çalıştırıldığında otomatik olarak yürütülür.</span><span class="sxs-lookup"><span data-stu-id="dbf88-123">Each test method in a test class tagged with the \[TestMethod\] attribute is executed automatically when the unit test is run.</span></span>

   - <span data-ttu-id="dbf88-124">Birim testi çalıştırıldığında otomatik yürütmeye yönelik bir test yöntemi olarak `TestMethod1` tanımlamak için <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> özniteliğini uygular.</span><span class="sxs-lookup"><span data-stu-id="dbf88-124">It applies the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> attribute to define `TestMethod1` as a test method for automatic execution when the unit test is run.</span></span>

1. <span data-ttu-id="dbf88-125">**Çözüm Gezgini**, **stringlibrarytest** projesinin **Bağımlılıklar** düğümüne sağ tıklayın ve bağlam menüsünden **Başvuru Ekle** ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="dbf88-125">In **Solution Explorer**, right-click the **Dependencies** node of the **StringLibraryTest** project and select **Add Reference** from the context menu.</span></span>

   ![StringLibraryTest bağımlılıklarının bağlam menüsü-C#](./media/testing-library-with-visual-studio/add-reference-context-menu.png)

1. <span data-ttu-id="dbf88-127">**Başvuru Yöneticisi** iletişim kutusunda, **Projeler** düğümünü genişletin ve **StringLibrary**' ın yanındaki kutuyu işaretleyin.</span><span class="sxs-lookup"><span data-stu-id="dbf88-127">In the **Reference Manager** dialog, expand the **Projects** node and check the box next to **StringLibrary**.</span></span> <span data-ttu-id="dbf88-128">`StringLibrary` derlemesine bir başvuru eklemek derleyicinin **StringLibrary** yöntemlerini bulmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="dbf88-128">Adding a reference to the `StringLibrary` assembly allows the compiler to find **StringLibrary** methods.</span></span> <span data-ttu-id="dbf88-129">**Tamam** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="dbf88-129">Select the **OK** button.</span></span> <span data-ttu-id="dbf88-130">Bu, `StringLibrary`sınıf kitaplığı projenize bir başvuru ekler.</span><span class="sxs-lookup"><span data-stu-id="dbf88-130">This adds a reference to your class library project, `StringLibrary`.</span></span>

   ![Visual Studio proje başvurusu ekleme iletişim kutusu](./media/testing-library-with-visual-studio/project-reference-manager.png)

# <a name="visual-basictabvb"></a>[<span data-ttu-id="dbf88-132">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="dbf88-132">Visual Basic</span></span>](#tab/vb)

1. <span data-ttu-id="dbf88-133">**Çözüm Gezgini**, **classlibraryprojects** çözüm düğümünün bağlam menüsünü açın ve > **Yeni proje** **Ekle** ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="dbf88-133">In **Solution Explorer**, open the context menu for the **ClassLibraryProjects** solution node and select **Add** > **New Project**.</span></span>

1. <span data-ttu-id="dbf88-134">**Yeni Proje Ekle** iletişim kutusunda **Visual Basic** düğümünü seçin.</span><span class="sxs-lookup"><span data-stu-id="dbf88-134">In the **Add New Project** dialog, select the **Visual Basic** node.</span></span> <span data-ttu-id="dbf88-135">Ardından, **.NET Core** düğümünü ve ardından **MSTest test projesi (.NET Core)** proje şablonunu seçin.</span><span class="sxs-lookup"><span data-stu-id="dbf88-135">Then select the **.NET Core** node followed by the **MSTest Test Project (.NET Core)** project template.</span></span> <span data-ttu-id="dbf88-136">**Ad** metin kutusuna projenin adı olarak "StringLibraryTest" yazın.</span><span class="sxs-lookup"><span data-stu-id="dbf88-136">In the **Name** text box, enter "StringLibraryTest" as the name of the project.</span></span> <span data-ttu-id="dbf88-137">Birim testi projesini oluşturmak için **Tamam ' ı** seçin.</span><span class="sxs-lookup"><span data-stu-id="dbf88-137">Select **OK** to create the unit test project.</span></span>

   ![Birim testi projesi görüntülenirken yeni proje iletişim kutusu Ekle-Visual Basic](./media/testing-library-with-visual-studio/vb-create-new-test-project.png)

   > [!NOTE]  
   > <span data-ttu-id="dbf88-139">Bir MSTest test projesine ek olarak, .NET Core için bir xUnit test projesi oluşturmak üzere Visual Studio 'Yu da kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dbf88-139">In addition to an MSTest Test project, you can also use Visual Studio to create an xUnit test project for .NET Core.</span></span>

1. <span data-ttu-id="dbf88-140">Visual Studio projeyi oluşturur ve kod penceresinde *UnitTest1. vb* dosyasını açar.</span><span class="sxs-lookup"><span data-stu-id="dbf88-140">Visual Studio creates the project and opens the *UnitTest1.vb* file in the code window.</span></span>

   ![Birim testi proje sınıfı ve yöntemi için Visual Studio Code penceresi-Visual Basic](./media/testing-library-with-visual-studio/vb-unit-test-editor-window.png)

   <span data-ttu-id="dbf88-142">Birim testi şablonu tarafından oluşturulan kaynak kodu aşağıdakileri yapar:</span><span class="sxs-lookup"><span data-stu-id="dbf88-142">The source code created by the unit test template does the following:</span></span>

   - <span data-ttu-id="dbf88-143">Birim testi için kullanılan türleri içeren <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=nameWithType> ad alanını içeri aktarır.</span><span class="sxs-lookup"><span data-stu-id="dbf88-143">It imports the <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=nameWithType> namespace, which contains the types used for unit testing.</span></span>

   - <span data-ttu-id="dbf88-144">`UnitTest1` sınıfına <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> özniteliğini uygular.</span><span class="sxs-lookup"><span data-stu-id="dbf88-144">It applies the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> attribute to the `UnitTest1` class.</span></span> <span data-ttu-id="dbf88-145"><xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> özniteliğiyle etiketlenmiş bir test sınıfındaki her test yöntemi, birim testi çalıştırıldığında otomatik olarak yürütülür.</span><span class="sxs-lookup"><span data-stu-id="dbf88-145">Each test method in a test class tagged with the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> attribute is executed automatically when the unit test is run.</span></span>

   - <span data-ttu-id="dbf88-146">Birim testi çalıştırıldığında otomatik yürütmeye yönelik bir test yöntemi olarak `TestMethod1` tanımlamak için <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> özniteliğini uygular.</span><span class="sxs-lookup"><span data-stu-id="dbf88-146">It applies the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> attribute to define `TestMethod1` as a test method for automatic execution when the unit test is run.</span></span>

1. <span data-ttu-id="dbf88-147">**Çözüm Gezgini**, **stringlibrarytest** projesinin **Bağımlılıklar** düğümüne sağ tıklayın ve bağlam menüsünden **Başvuru Ekle** ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="dbf88-147">In **Solution Explorer**, right-click the **Dependencies** node of the **StringLibraryTest** project and select **Add Reference** from the context menu.</span></span>

   ![StringLibraryTest bağımlılıklarının bağlam menüsü](./media/testing-library-with-visual-studio/add-reference-context-menu.png)

1. <span data-ttu-id="dbf88-149">**Başvuru Yöneticisi** iletişim kutusunda, **Projeler** düğümünü genişletin ve **StringLibrary**' ın yanındaki kutuyu işaretleyin.</span><span class="sxs-lookup"><span data-stu-id="dbf88-149">In the **Reference Manager** dialog, expand the **Projects** node and check the box next to **StringLibrary**.</span></span> <span data-ttu-id="dbf88-150">`StringLibrary` derlemesine bir başvuru eklemek derleyicinin **StringLibrary** yöntemlerini bulmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="dbf88-150">Adding a reference to the `StringLibrary` assembly allows the compiler to find **StringLibrary** methods.</span></span> <span data-ttu-id="dbf88-151">**Tamam** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="dbf88-151">Select the **OK** button.</span></span> <span data-ttu-id="dbf88-152">Bu, `StringLibrary`sınıf kitaplığı projenize bir başvuru ekler.</span><span class="sxs-lookup"><span data-stu-id="dbf88-152">This adds a reference to your class library project, `StringLibrary`.</span></span>

   ![Visual Studio proje başvurusu ekleme iletişim kutusu-Visual Basic](./media/testing-library-with-visual-studio/project-reference-manager.png)

---

## <a name="adding-and-running-unit-test-methods"></a><span data-ttu-id="dbf88-154">Birim testi yöntemleri ekleme ve çalıştırma</span><span class="sxs-lookup"><span data-stu-id="dbf88-154">Adding and running unit test methods</span></span>

<span data-ttu-id="dbf88-155">Visual Studio bir birim testi çalıştırdığında, bir birim testi sınıfında <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> özniteliğiyle işaretlenmiş her bir yöntemi yürütür, bu sınıf <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> özniteliği uygulandı.</span><span class="sxs-lookup"><span data-stu-id="dbf88-155">When Visual Studio runs a unit test, it executes each method marked with the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> attribute in a unit test class, the class to which the  <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> attribute is applied.</span></span> <span data-ttu-id="dbf88-156">Bir test yöntemi, ilk hata ile karşılaşıldığında veya yöntemde bulunan tüm testler başarılı olduğunda sona erer.</span><span class="sxs-lookup"><span data-stu-id="dbf88-156">A test method ends when the first failure is encountered or when all tests contained in the method have succeeded.</span></span>

<span data-ttu-id="dbf88-157">En yaygın testler <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> sınıfının üyelerini çağırır.</span><span class="sxs-lookup"><span data-stu-id="dbf88-157">The most common tests call members of the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> class.</span></span> <span data-ttu-id="dbf88-158">Birçok onaylama yöntemi, biri beklenen test sonucu ve diğeri de gerçek test sonucu olan en az iki parametre içerir.</span><span class="sxs-lookup"><span data-stu-id="dbf88-158">Many assert methods include at least two parameters, one of which is the expected test result and the other of which is the actual test result.</span></span> <span data-ttu-id="dbf88-159">En sık çağrılan yöntemlerin bazıları aşağıdaki tabloda gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="dbf88-159">Some of its most frequently called methods are shown in the following table:</span></span>

<span data-ttu-id="dbf88-160">Onaylama yöntemleri</span><span class="sxs-lookup"><span data-stu-id="dbf88-160">Assert methods</span></span> | <span data-ttu-id="dbf88-161">İşlev</span><span class="sxs-lookup"><span data-stu-id="dbf88-161">Function</span></span>
--- | ---
`Assert.AreEqual` | <span data-ttu-id="dbf88-162">İki değerin veya nesnenin eşit olduğunu doğrular.</span><span class="sxs-lookup"><span data-stu-id="dbf88-162">Verifies that two values or objects are equal.</span></span> <span data-ttu-id="dbf88-163">Değerler veya nesneler eşit değilse onaylama başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="dbf88-163">The assert fails if the values or objects are not equal.</span></span>
`Assert.AreSame` | <span data-ttu-id="dbf88-164">İki nesne değişkeninin aynı nesneye başvurmasını doğrular.</span><span class="sxs-lookup"><span data-stu-id="dbf88-164">Verifies that two object variables refer to the same object.</span></span> <span data-ttu-id="dbf88-165">Değişkenler farklı nesnelere başvuru yaptığında onaylama başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="dbf88-165">The assert fails if the variables refer to different objects.</span></span>
`Assert.IsFalse` | <span data-ttu-id="dbf88-166">Bir koşulun `false`olduğunu doğrular.</span><span class="sxs-lookup"><span data-stu-id="dbf88-166">Verifies that a condition is `false`.</span></span> <span data-ttu-id="dbf88-167">Koşul `true`, onaylama başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="dbf88-167">The assert fails if the condition is `true`.</span></span>
`Assert.IsNotNull` | <span data-ttu-id="dbf88-168">Bir nesnenin `null`olmadığını doğrular.</span><span class="sxs-lookup"><span data-stu-id="dbf88-168">Verifies that an object is not `null`.</span></span> <span data-ttu-id="dbf88-169">Nesne `null`, onaylama başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="dbf88-169">The assert fails if the object is `null`.</span></span>

<span data-ttu-id="dbf88-170"><xref:Microsoft.VisualStudio.TestTools.UnitTesting.ExpectedExceptionAttribute> özniteliğini bir test yöntemine de uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dbf88-170">You can also apply the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.ExpectedExceptionAttribute> attribute to a test method.</span></span> <span data-ttu-id="dbf88-171">Bir test yönteminin oluşturması beklenen özel durum türünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="dbf88-171">It indicates the type of exception a test method is expected to throw.</span></span> <span data-ttu-id="dbf88-172">Belirtilen özel durum atılmazsa, test başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="dbf88-172">The test fails if the specified exception is not thrown.</span></span>

<span data-ttu-id="dbf88-173">`StringLibrary.StartsWithUpper` yöntemini test ederken, büyük harfli bir karakterle başlayan bir dizi dize sağlamak istersiniz.</span><span class="sxs-lookup"><span data-stu-id="dbf88-173">In testing the `StringLibrary.StartsWithUpper` method, you want to provide a number of strings that begin with an uppercase character.</span></span> <span data-ttu-id="dbf88-174">Yöntemi bu durumlarda `true` döndürecek şekilde beklediğinizi, <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue%2A> yöntemini çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dbf88-174">You expect the method to return `true` in these cases, so you can call the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue%2A> method.</span></span> <span data-ttu-id="dbf88-175">Benzer şekilde, büyük harfli bir karakter ile başlayan bir dizi dize sağlamak istersiniz.</span><span class="sxs-lookup"><span data-stu-id="dbf88-175">Similarly, you want to provide a number of strings that begin with something other than an uppercase character.</span></span> <span data-ttu-id="dbf88-176">Yöntemi bu durumlarda `false` döndürecek şekilde beklediğinizi, <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse%2A> yöntemini çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dbf88-176">You expect the method to return `false` in these cases, so you can call the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse%2A> method.</span></span>

<span data-ttu-id="dbf88-177">Kitaplık yönteminiz dizeleri yaptığından, ayrıca [boş bir dizeyi (`String.Empty`) başarılı bir şekilde ()](xref:System.String.Empty), hiçbir karakteri olmayan ve <xref:System.String.Length> 0 olan ve başlatılmamış bir `null` dizesinin başarıyla çalıştığından emin olmak istersiniz.</span><span class="sxs-lookup"><span data-stu-id="dbf88-177">Since your library method handles strings, you also want to make sure that it successfully handles an [empty string (`String.Empty`)](xref:System.String.Empty), a valid string that has no characters and whose <xref:System.String.Length> is 0, and a `null` string that has not been initialized.</span></span> <span data-ttu-id="dbf88-178">`StartsWithUpper` bir <xref:System.String> örneğinde uzantı yöntemi olarak çağrılırsa, `null` bir dize geçirilemez.</span><span class="sxs-lookup"><span data-stu-id="dbf88-178">If `StartsWithUpper` is called as an extension method on a <xref:System.String> instance, it cannot be passed a `null` string.</span></span> <span data-ttu-id="dbf88-179">Ancak, bunu doğrudan statik bir yöntem olarak çağırabilir ve tek bir <xref:System.String> bağımsız değişkeni geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dbf88-179">However, you can also call it directly as a static method and pass a single <xref:System.String> argument.</span></span>

<span data-ttu-id="dbf88-180">Her biri bir dize dizisindeki her öğe için <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> yöntemini her bir kez çağıran üç yöntem tanımlayacaksınız.</span><span class="sxs-lookup"><span data-stu-id="dbf88-180">You'll define three methods, each of which calls its <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> method repeatedly for each element in a string array.</span></span> <span data-ttu-id="dbf88-181">İlk başarısızlığından sonra test yöntemi başarısız olduğundan, yöntem çağrısında kullanılan dize değerini gösteren bir dize geçirmenize izin veren bir yöntem aşırı yüklemesi çağıracaksınız.</span><span class="sxs-lookup"><span data-stu-id="dbf88-181">Because the test method fails as soon as it encounters the first failure, you'll call a method overload that allows you to pass a string that indicates the string value used in the method call.</span></span>

<span data-ttu-id="dbf88-182">Test yöntemleri oluşturmak için:</span><span class="sxs-lookup"><span data-stu-id="dbf88-182">To create the test methods:</span></span>

# <a name="ctabcsharp"></a>[<span data-ttu-id="dbf88-183">C#</span><span class="sxs-lookup"><span data-stu-id="dbf88-183">C#</span></span>](#tab/csharp)

1. <span data-ttu-id="dbf88-184">*UnitTest1.cs* Code penceresinde, kodu şu kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="dbf88-184">In the *UnitTest1.cs* code window, replace the code with the following code:</span></span>

   [!code-csharp[Test#1](~/samples/snippets/csharp/getting_started/with_visual_studio_2017/testlib1.cs)]

   <span data-ttu-id="dbf88-185">`TestStartsWithUpper` yönteminde büyük harfli karakter testinizin Yunanca Büyük Harf Alpha (U + 0391) ve Kiril Büyük harf EM (U + 041C) ve `TestDoesNotStartWithUpper` yönteminde küçük harfli karakterlerin testi, Yunanca Küçük Harf Alpha ' ı (U +) içerir. 03B1) ve Kiril Küçük harf GHE (U + 0433).</span><span class="sxs-lookup"><span data-stu-id="dbf88-185">Note that your test of uppercase characters in the `TestStartsWithUpper` method includes the Greek capital letter alpha (U+0391) and the Cyrillic capital letter EM (U+041C), and the test of lowercase characters in the `TestDoesNotStartWithUpper` method includes the Greek small letter alpha (U+03B1) and the Cyrillic small letter Ghe (U+0433).</span></span>

1. <span data-ttu-id="dbf88-186">Menü çubuğunda **dosya > dosyayı** **farklı kaydet**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="dbf88-186">On the menu bar, select **File** > **Save UnitTest1.cs As**.</span></span> <span data-ttu-id="dbf88-187">**Dosyayı farklı kaydet** Iletişim kutusunda **Kaydet** düğmesinin yanındaki oku seçin ve **kodlamayla kaydet**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="dbf88-187">In the **Save File As** dialog, select the arrow beside the **Save** button, and select **Save with Encoding**.</span></span>

   ![Visual Studio dosyayı farklı Kaydet iletişim kutusu-C#](./media/testing-library-with-visual-studio/save-file-as-dialog.png)

# <a name="visual-basictabvb"></a>[<span data-ttu-id="dbf88-189">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="dbf88-189">Visual Basic</span></span>](#tab/vb)

1. <span data-ttu-id="dbf88-190">*UnitTest1. vb* Code penceresinde, kodu aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="dbf88-190">In the *UnitTest1.vb* code window, replace the code with the following code:</span></span>

    [!code-vb[Test#1](~/samples/snippets/core/tutorials/vb-library-with-visual-studio/testlib.vb)]

   <span data-ttu-id="dbf88-191">`TestStartsWithUpper` yönteminde büyük harfli karakter testinizin Yunanca Büyük Harf Alpha (U + 0391) ve Kiril Büyük harf EM (U + 041C) ve `TestDoesNotStartWithUpper` yönteminde küçük harfli karakterlerin testi, Yunanca Küçük Harf Alpha ' ı (U +) içerir. 03B1) ve Kiril Küçük harf GHE (U + 0433).</span><span class="sxs-lookup"><span data-stu-id="dbf88-191">Note that your test of uppercase characters in the `TestStartsWithUpper` method includes the Greek capital letter alpha (U+0391) and the Cyrillic capital letter EM (U+041C), and the test of lowercase characters in the `TestDoesNotStartWithUpper` method includes the Greek small letter alpha (U+03B1) and the Cyrillic small letter Ghe (U+0433).</span></span>

1. <span data-ttu-id="dbf88-192">Menü çubuğunda **Dosya** ' yı seçin > **UnitTest1. vb dosyasını farklı kaydedin**.</span><span class="sxs-lookup"><span data-stu-id="dbf88-192">On the menu bar, select **File** > **Save UnitTest1.vb As**.</span></span> <span data-ttu-id="dbf88-193">**Dosyayı farklı kaydet** Iletişim kutusunda **Kaydet** düğmesinin yanındaki oku seçin ve **kodlamayla kaydet**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="dbf88-193">In the **Save File As** dialog, select the arrow beside the **Save** button, and select **Save with Encoding**.</span></span>

   ![Visual Studio dosyayı farklı Kaydet iletişim kutusu Visual Basic](./media/testing-library-with-visual-studio/save-file-as-dialog.png)

---

1. <span data-ttu-id="dbf88-195">**Farklı kaydet** iletişim kutusunda, dosyayı kaydetmek için **Evet** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="dbf88-195">In the **Confirm Save As** dialog, select the **Yes** button to save the file.</span></span>

1. <span data-ttu-id="dbf88-196">**Gelişmiş kaydetme seçenekleri** iletişim kutusunda, **kodlama** açılan LISTESINDEN **Unicode (imzayla UTF-8)-kod sayfası 65001** ' i seçin ve **Tamam**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="dbf88-196">In the **Advanced Save Options** dialog, select **Unicode (UTF-8 with signature) - Codepage 65001** from the **Encoding** drop-down list and select **OK**.</span></span>

   ![Visual Studio Gelişmiş kaydetme seçenekleri iletişim kutusu](./media/testing-library-with-visual-studio/advanced-save-options.png)

   <span data-ttu-id="dbf88-198">Kaynak kodunuzu UTF8 kodlu bir dosya olarak kaydedemeyebilirsiniz, Visual Studio bunu bir ASCII dosyası olarak kaydedebilir.</span><span class="sxs-lookup"><span data-stu-id="dbf88-198">If you fail to save your source code as a UTF8-encoded file, Visual Studio may save it as an ASCII file.</span></span> <span data-ttu-id="dbf88-199">Söz konusu olduğunda, çalışma zamanı, ASCII aralığının dışında UTF8 karakterlerinin kodunu doğru şekilde çözmez ve test sonuçları doğru olmayacaktır.</span><span class="sxs-lookup"><span data-stu-id="dbf88-199">When that happens, the runtime doesn't accurately decode the UTF8 characters outside of the ASCII range, and the test results won't be accurate.</span></span>

1. <span data-ttu-id="dbf88-200">Menü çubuğunda **Test** > **Tüm testler** > **Çalıştır** ' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="dbf88-200">On the menu bar, select **Test** > **Run** > **All Tests**.</span></span> <span data-ttu-id="dbf88-201">**Test Gezgini** penceresi açılır ve testlerin başarıyla çalıştığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="dbf88-201">The **Test Explorer** window opens and shows that the tests ran successfully.</span></span> <span data-ttu-id="dbf88-202">**Geçen testler** bölümünde üç test listelenir ve **Özet** bölümü Test çalıştırmasının sonucunu raporlar.</span><span class="sxs-lookup"><span data-stu-id="dbf88-202">The three tests are listed in the **Passed Tests** section, and the **Summary** section reports the result of the test run.</span></span>

   ![Testleri geçirerek test Gezgini penceresi](./media/testing-library-with-visual-studio/test-explorer-window.png)

## <a name="handling-test-failures"></a><span data-ttu-id="dbf88-204">Test başarısızlıklarını işleme</span><span class="sxs-lookup"><span data-stu-id="dbf88-204">Handling test failures</span></span>

<span data-ttu-id="dbf88-205">Test çalıştırmasında hata yoktu, ancak test yöntemlerinden birinin başarısız olması için biraz değiştirin:</span><span class="sxs-lookup"><span data-stu-id="dbf88-205">Your test run had no failures, but change it slightly so that one of the test methods fails:</span></span>

1. <span data-ttu-id="dbf88-206">`TestDoesNotStartWithUpper` yönteminde `words` diziyi, "Error" dizesini içerecek şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="dbf88-206">Modify the `words` array in the `TestDoesNotStartWithUpper` method to include the string "Error".</span></span> <span data-ttu-id="dbf88-207">Testleri çalıştırmak için bir çözüm oluşturulduğunda Visual Studio açık dosyaları otomatik olarak kaydettiği için dosyayı kaydetmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="dbf88-207">You don't need to save the file because Visual Studio automatically saves open files when a solution is built to run tests.</span></span>

   ```csharp
   string[] words = { "alphabet", "Error", "zebra", "abc", "αυτοκινητοβιομηχανία", "государство",
                      "1234", ".", ";", " " };
   ```

   ```vb
   Dim words() As String = { "alphabet", "Error", "zebra", "abc", "αυτοκινητοβιομηχανία", "государство",
                      "1234", ".", ";", " " }

   ```

1. <span data-ttu-id="dbf88-208">**Test > menü** çubuğundan **tüm testleri** > **Çalıştır** öğesini seçerek testi çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="dbf88-208">Run the test by selecting **Test** > **Run** > **All Tests** from the menu bar.</span></span> <span data-ttu-id="dbf88-209">**Test Gezgini** penceresi, iki testin başarılı olduğunu ve bir başarısız olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="dbf88-209">The **Test Explorer** window indicates that two tests succeeded and one failed.</span></span>

   ![Başarısız testlerle test Gezgini penceresi](./media/testing-library-with-visual-studio/failed-test-window.png)

1. <span data-ttu-id="dbf88-211">**Başarısız testler** bölümünde başarısız test ' i seçin `TestDoesNotStartWith`.</span><span class="sxs-lookup"><span data-stu-id="dbf88-211">In the **Failed Tests** section, select the failed test, `TestDoesNotStartWith`.</span></span> <span data-ttu-id="dbf88-212">**Test Gezgini** penceresi onay tarafından oluşturulan iletiyi görüntüler: "onaylama. IsFalse başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="dbf88-212">The **Test Explorer** window displays the message produced by the assert: "Assert.IsFalse failed.</span></span> <span data-ttu-id="dbf88-213">' Error ' bekleniyor: false; gerçek: true ".</span><span class="sxs-lookup"><span data-stu-id="dbf88-213">Expected for 'Error': false; actual: True".</span></span> <span data-ttu-id="dbf88-214">Hata nedeniyle "hata" sonunda dizideki tüm dizeler sınanmadı.</span><span class="sxs-lookup"><span data-stu-id="dbf88-214">Because of the failure, all strings in the array after "Error" were not tested.</span></span>

   ![False onaylama hatası olduğunu gösteren test Gezgini penceresi](./media/testing-library-with-visual-studio/failed-test-detail.png)

1. <span data-ttu-id="dbf88-216">Adım 1 ' de yaptığınız değişikliği geri alın ve "hata" dizesini kaldırın.</span><span class="sxs-lookup"><span data-stu-id="dbf88-216">Undo the modification you did in step 1 and remove the string "Error".</span></span> <span data-ttu-id="dbf88-217">Testi yeniden çalıştırın ve testler geçer.</span><span class="sxs-lookup"><span data-stu-id="dbf88-217">Rerun the test and the tests will pass.</span></span>

## <a name="testing-the-release-version-of-the-library"></a><span data-ttu-id="dbf88-218">Kitaplığın yayın sürümünü test etme</span><span class="sxs-lookup"><span data-stu-id="dbf88-218">Testing the Release version of the library</span></span>

<span data-ttu-id="dbf88-219">Testlerinizi kitaplığın hata ayıklama sürümüne karşı çalıştırıyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="dbf88-219">You've been running your tests against the Debug version of the library.</span></span> <span data-ttu-id="dbf88-220">Artık testleriniz başarılı olduğuna ve kitaplığınızı yeterince test edinceye kadar, bu testleri kitaplığın yayın derlemesi için ek bir zaman çalıştırmalısınız.</span><span class="sxs-lookup"><span data-stu-id="dbf88-220">Now that your tests have all passed and you've adequately tested your library, you should run the tests an additional time against the Release build of the library.</span></span> <span data-ttu-id="dbf88-221">Derleyici iyileştirmeleri dahil olmak üzere bir dizi etken bazen hata ayıklama ve yayın yapıları arasında farklı davranışlar üretebilir.</span><span class="sxs-lookup"><span data-stu-id="dbf88-221">A number of factors, including compiler optimizations, can sometimes produce different behavior between Debug and Release builds.</span></span>

<span data-ttu-id="dbf88-222">Yayın derlemesini test etmek için:</span><span class="sxs-lookup"><span data-stu-id="dbf88-222">To test the Release build:</span></span>

1. <span data-ttu-id="dbf88-223">Visual Studio araç çubuğunda, derleme yapılandırmasını **Debug** iken **Release**olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="dbf88-223">In the Visual Studio toolbar, change the build configuration from **Debug** to **Release**.</span></span>

   ![Yayın derlemesi vurgulanmış Visual Studio araç çubuğu](./media/testing-library-with-visual-studio/visual-studio-toolbar-release.png)

1. <span data-ttu-id="dbf88-225">**Çözüm Gezgini**, **StringLibrary** projesine sağ tıklayın ve kitaplığı yeniden derlemek için bağlam menüsünden **Oluştur** ' u seçin.</span><span class="sxs-lookup"><span data-stu-id="dbf88-225">In **Solution Explorer**, right-click the **StringLibrary** project and select **Build** from the context menu to recompile the library.</span></span>

   ![Build komutuyla StringLibrary bağlam menüsü](./media/testing-library-with-visual-studio/build-library-context-menu.png)

1. <span data-ttu-id="dbf88-227">**Test** > menü çubuğundan **tüm testleri** > **Çalıştır** öğesini seçerek birim testlerini çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="dbf88-227">Run the unit tests by choosing **Test** > **Run** > **All Tests** from the menu bar.</span></span> <span data-ttu-id="dbf88-228">Testler geçer.</span><span class="sxs-lookup"><span data-stu-id="dbf88-228">The tests pass.</span></span>

<span data-ttu-id="dbf88-229">Artık kitaplığınızı test etmeyi tamamladığınıza göre, bir sonraki adım çağıranlar tarafından kullanılabilir hale gelir.</span><span class="sxs-lookup"><span data-stu-id="dbf88-229">Now that you've finished testing your library, the next step is to make it available to callers.</span></span> <span data-ttu-id="dbf88-230">Bunu bir veya daha fazla uygulamayla paketleyebilir veya bir NuGet paketi olarak dağıtabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dbf88-230">You can bundle it with one or more applications, or you can distribute it as a NuGet package.</span></span> <span data-ttu-id="dbf88-231">Daha fazla bilgi için bkz. [.NET Standard sınıf kitaplığı](./consuming-library-with-visual-studio.md)kullanma.</span><span class="sxs-lookup"><span data-stu-id="dbf88-231">For more information, see [Consuming a .NET Standard Class Library](./consuming-library-with-visual-studio.md).</span></span>
