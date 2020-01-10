---
title: Visual Studio 'da .NET Standard sınıf kitaplığı oluşturma
description: Visual Studio kullanarak C# veya Visual Basic yazılmış .NET Standard sınıf kitaplığı oluşturmayı öğrenin
ms.date: 12/09/2019
ms.custom: vs-dotnet
ms.openlocfilehash: 748a1499e0c3a4a41613a69b715dbcfbd585bfe3
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75714015"
---
# <a name="build-a-net-standard-library-in-visual-studio"></a><span data-ttu-id="0a83b-103">Visual Studio 'da .NET Standard kitaplığı oluşturma</span><span class="sxs-lookup"><span data-stu-id="0a83b-103">Build a .NET Standard library in Visual Studio</span></span>

<span data-ttu-id="0a83b-104">Bir *sınıf kitaplığı* , bir uygulama tarafından çağrılan türleri ve yöntemleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="0a83b-104">A *class library* defines types and methods that are called by an application.</span></span> <span data-ttu-id="0a83b-105">.NET Standard 2,0 ' i hedefleyen bir sınıf kitaplığı, kitaplığınızın bu .NET Standard sürümünü destekleyen herhangi bir .NET uygulamasının çağrılmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="0a83b-105">A class library that targets .NET Standard 2.0 allows your library to be called by any .NET implementation that supports that version of .NET Standard.</span></span> <span data-ttu-id="0a83b-106">Sınıf kitaplığınızı bitirdiğinizde, bunu üçüncü taraf bir bileşen olarak dağıtmak mı yoksa bir veya daha fazla uygulamayla paketlenmiş bir bileşen olarak eklemek mi istediğinize karar verebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0a83b-106">When you finish your class library, you can decide whether you want to distribute it as a third-party component or whether you want to include it as a bundled component with one or more applications.</span></span>

> [!NOTE]
> <span data-ttu-id="0a83b-107">.NET Standard sürümlerinin ve destekledikleri platformların listesi için bkz. [.NET Standard](../../standard/net-standard.md).</span><span class="sxs-lookup"><span data-stu-id="0a83b-107">For a list of .NET Standard versions and the platforms they support, see [.NET Standard](../../standard/net-standard.md).</span></span>

<span data-ttu-id="0a83b-108">Bu konu başlığında, tek bir dize işleme yöntemi içeren basit bir yardımcı program kitaplığı oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="0a83b-108">In this topic, you'll create a simple utility library that contains a single string-handling method.</span></span> <span data-ttu-id="0a83b-109">Bunu, <xref:System.String> sınıfının bir üyesi gibi çağırabilmeniz için bir [genişletme yöntemi](../../csharp/programming-guide/classes-and-structs/extension-methods.md) olarak uygulayacaksınız.</span><span class="sxs-lookup"><span data-stu-id="0a83b-109">You'll implement it as an [extension method](../../csharp/programming-guide/classes-and-structs/extension-methods.md) so that you can call it as if it were a member of the <xref:System.String> class.</span></span>

## <a name="create-a-visual-studio-solution"></a><span data-ttu-id="0a83b-110">Visual Studio çözümü oluşturma</span><span class="sxs-lookup"><span data-stu-id="0a83b-110">Create a Visual Studio solution</span></span>

<span data-ttu-id="0a83b-111">' De Sınıf Kitaplığı projesini yerleştirmek için boş bir çözüm oluşturarak başlayın.</span><span class="sxs-lookup"><span data-stu-id="0a83b-111">Start by creating a blank solution to put the class library project in.</span></span> <span data-ttu-id="0a83b-112">Visual Studio çözümü bir veya daha fazla proje için kapsayıcı görevi görür.</span><span class="sxs-lookup"><span data-stu-id="0a83b-112">A Visual Studio solution serves as a container for one or more projects.</span></span> <span data-ttu-id="0a83b-113">Öğretici serisiyle devam ederseniz, aynı çözüme ek ve ilgili projeler ekleyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="0a83b-113">You'll add additional, related projects to the same solution if you continue on with the tutorial series.</span></span>

<span data-ttu-id="0a83b-114">Boş çözümü oluşturmak için:</span><span class="sxs-lookup"><span data-stu-id="0a83b-114">To create the blank solution:</span></span>

1. <span data-ttu-id="0a83b-115">Visual Studio'yu açın.</span><span class="sxs-lookup"><span data-stu-id="0a83b-115">Open Visual Studio.</span></span>

2. <span data-ttu-id="0a83b-116">Başlangıç penceresinde **Yeni proje oluştur**' u seçin.</span><span class="sxs-lookup"><span data-stu-id="0a83b-116">On the start window, choose **Create a new project**.</span></span>

3. <span data-ttu-id="0a83b-117">**Yeni proje oluştur** sayfasında, arama kutusuna **çözüm** girin.</span><span class="sxs-lookup"><span data-stu-id="0a83b-117">On the **Create a new project** page, enter **solution** in the search box.</span></span> <span data-ttu-id="0a83b-118">**Boş çözüm** şablonunu seçin ve ardından **İleri**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="0a83b-118">Choose the **Blank Solution** template, and then choose **Next**.</span></span>

   ![Visual Studio'da boş çözüm şablonu](media/library-with-visual-studio/blank-solution.png)

4. <span data-ttu-id="0a83b-120">**Yeni projenizi yapılandırın** sayfasında, **Proje adı** kutusuna **classlibraryprojects** ' i girin.</span><span class="sxs-lookup"><span data-stu-id="0a83b-120">On the **Configure your new project** page, enter **ClassLibraryProjects** in the **Project name** box.</span></span> <span data-ttu-id="0a83b-121">Ardından **Oluştur**' u seçin.</span><span class="sxs-lookup"><span data-stu-id="0a83b-121">Then, choose **Create**.</span></span>

> [!TIP]
> <span data-ttu-id="0a83b-122">Ayrıca, bu adımı atlayabilir ve bir sonraki adımda projeyi oluştururken Visual Studio 'nun sizin için çözümü oluşturmasına izin verebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0a83b-122">You can also skip this step and let Visual Studio create the solution for you when you create the project in the next step.</span></span> <span data-ttu-id="0a83b-123">**Yeni projenizde yapılandırma** sayfasında çözüm seçeneklerini bulun.</span><span class="sxs-lookup"><span data-stu-id="0a83b-123">Look for the solution options on the **Configure your new project** page.</span></span>

## <a name="create-a-class-library-project"></a><span data-ttu-id="0a83b-124">Sınıf kitaplığı projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="0a83b-124">Create a class library project</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="ctabcsharp"></a>[<span data-ttu-id="0a83b-125">C#</span><span class="sxs-lookup"><span data-stu-id="0a83b-125">C#</span></span>](#tab/csharp)

1. <span data-ttu-id="0a83b-126">Çözüme "StringLibrary" adlı yeni C# bir .NET Standard sınıf kitaplığı projesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="0a83b-126">Add a new C# .NET Standard class library project named "StringLibrary" to the solution.</span></span>

   1. <span data-ttu-id="0a83b-127">**Çözüm Gezgini** çözüme sağ tıklayın ve > **Yeni proje** **Ekle** ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="0a83b-127">Right-click on the solution in **Solution Explorer** and select **Add** > **New project**.</span></span>

   1. <span data-ttu-id="0a83b-128">**Yeni Proje Ekle** sayfasında, arama kutusuna **kitaplık** yazın.</span><span class="sxs-lookup"><span data-stu-id="0a83b-128">On the **Add a new project** page, enter **library** in the search box.</span></span> <span data-ttu-id="0a83b-129">Dil **C#** listesinden seçim yapın ve ardından platform listesinden **tüm platformlar** ' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="0a83b-129">Choose **C#** from the Language list, and then choose **All platforms** from the Platform list.</span></span> <span data-ttu-id="0a83b-130">**Sınıf kitaplığı (.NET Standard)** şablonunu seçin ve ardından **İleri**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="0a83b-130">Choose the **Class Library (.NET Standard)** template, and then choose **Next**.</span></span>

   1. <span data-ttu-id="0a83b-131">**Yeni projenizi yapılandırın** sayfasında, **Proje adı** kutusuna **StringLibrary** yazın.</span><span class="sxs-lookup"><span data-stu-id="0a83b-131">On the **Configure your new project** page, enter **StringLibrary** in the **Project name** box.</span></span> <span data-ttu-id="0a83b-132">Ardından **Oluştur**' u seçin.</span><span class="sxs-lookup"><span data-stu-id="0a83b-132">Then, choose **Create**.</span></span>

1. <span data-ttu-id="0a83b-133">Kitaplığın doğru .NET Standard sürümünü hedeflediğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="0a83b-133">Check to make sure that the library targets the correct version of .NET Standard.</span></span> <span data-ttu-id="0a83b-134">**Çözüm Gezgini**kitaplık projesine sağ tıklayın ve ardından **Özellikler**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="0a83b-134">Right-click on the library project in **Solution Explorer**, and then select **Properties**.</span></span> <span data-ttu-id="0a83b-135">**Hedef Framework** metin kutusu, projenin .NET Standard 2,0 ' i hedeflediğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="0a83b-135">The **Target Framework** text box shows that the project targets .NET Standard 2.0.</span></span>

   ![Sınıf kitaplığı için proje özellikleri](./media/library-with-visual-studio/library-project-properties.png)

1. <span data-ttu-id="0a83b-137">Kod penceresindeki kodu aşağıdaki kodla değiştirin ve dosyayı kaydedin:</span><span class="sxs-lookup"><span data-stu-id="0a83b-137">Replace the code in the code window with the following code and save the file:</span></span>

   [!CODE-csharp[ClassLib#1](../../../samples/snippets/csharp/getting_started/with_visual_studio_2017/classlib.cs)]

   <span data-ttu-id="0a83b-138">`UtilityLibraries.StringLibrary`sınıf kitaplığı, `StartsWithUpper`adlı bir yöntemi içerir.</span><span class="sxs-lookup"><span data-stu-id="0a83b-138">The class library, `UtilityLibraries.StringLibrary`, contains a method named `StartsWithUpper`.</span></span> <span data-ttu-id="0a83b-139">Bu yöntem, geçerli dize örneğinin büyük harfli bir karakterle başlayıp başlamadığını belirten bir <xref:System.Boolean> değeri döndürür.</span><span class="sxs-lookup"><span data-stu-id="0a83b-139">This method returns a <xref:System.Boolean> value that indicates whether the current string instance begins with an uppercase character.</span></span> <span data-ttu-id="0a83b-140">Unicode standart, büyük harfli karakterleri küçük harfli karakterlerden ayırır.</span><span class="sxs-lookup"><span data-stu-id="0a83b-140">The Unicode standard distinguishes uppercase characters from lowercase characters.</span></span> <span data-ttu-id="0a83b-141"><xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> yöntemi, bir karakter büyük harfle `true` döndürür.</span><span class="sxs-lookup"><span data-stu-id="0a83b-141">The <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> method returns `true` if a character is uppercase.</span></span>

1. <span data-ttu-id="0a83b-142">Menü çubuğunda **derleme** > **Build Solution**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="0a83b-142">On the menu bar, select **Build** > **Build Solution**.</span></span>

# <a name="visual-basictabvb"></a>[<span data-ttu-id="0a83b-143">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0a83b-143">Visual Basic</span></span>](#tab/vb)

1. <span data-ttu-id="0a83b-144">Çözüme "StringLibrary" adlı yeni bir Visual Basic .NET Standard sınıf kitaplığı projesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="0a83b-144">Add a new Visual Basic .NET Standard class library project named "StringLibrary" to the solution.</span></span>

   1. <span data-ttu-id="0a83b-145">**Çözüm Gezgini** çözüme sağ tıklayın ve > **Yeni proje** **Ekle** ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="0a83b-145">Right-click on the solution in **Solution Explorer** and select **Add** > **New project**.</span></span>

   1. <span data-ttu-id="0a83b-146">**Yeni Proje Ekle** sayfasında, arama kutusuna **kitaplık** yazın.</span><span class="sxs-lookup"><span data-stu-id="0a83b-146">On the **Add a new project** page, enter **library** in the search box.</span></span> <span data-ttu-id="0a83b-147">Dil listesinden **Visual Basic** ' yi seçin ve ardından platform listesinden **tüm platformlar** ' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="0a83b-147">Choose **Visual Basic** from the Language list, and then choose **All platforms** from the Platform list.</span></span> <span data-ttu-id="0a83b-148">**Sınıf kitaplığı (.NET Standard)** şablonunu seçin ve ardından **İleri**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="0a83b-148">Choose the **Class Library (.NET Standard)** template, and then choose **Next**.</span></span>

   1. <span data-ttu-id="0a83b-149">**Yeni projenizi yapılandırın** sayfasında, **Proje adı** kutusuna **StringLibrary** yazın.</span><span class="sxs-lookup"><span data-stu-id="0a83b-149">On the **Configure your new project** page, enter **StringLibrary** in the **Project name** box.</span></span> <span data-ttu-id="0a83b-150">Ardından **Oluştur**' u seçin.</span><span class="sxs-lookup"><span data-stu-id="0a83b-150">Then, choose **Create**.</span></span>

1. <span data-ttu-id="0a83b-151">Kitaplığın doğru .NET Standard sürümünü hedeflediğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="0a83b-151">Check to make sure that the library targets the correct version of .NET Standard.</span></span> <span data-ttu-id="0a83b-152">**Çözüm Gezgini**kitaplık projesine sağ tıklayın ve ardından **Özellikler**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="0a83b-152">Right-click on the library project in **Solution Explorer**, and then select **Properties**.</span></span> <span data-ttu-id="0a83b-153">**Hedef Framework** metin kutusu, projenin .NET Standard 2,0 ' i hedeflediğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="0a83b-153">The **Target Framework** text box shows that the project targets .NET Standard 2.0.</span></span>

   ![Sınıf kitaplığı için proje özellikleri](./media/library-with-visual-studio/vb/library-project-properties.png)

1. <span data-ttu-id="0a83b-155">**Özellikler** iletişim kutusunda, **kök ad alanı** metin kutusundaki metni temizleyin.</span><span class="sxs-lookup"><span data-stu-id="0a83b-155">In the **Properties** dialog, clear the text in the **Root namespace** text box.</span></span> <span data-ttu-id="0a83b-156">Her proje için, Visual Basic otomatik olarak proje adına karşılık gelen bir ad alanı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0a83b-156">For each project, Visual Basic automatically creates a namespace that corresponds to the project name.</span></span> <span data-ttu-id="0a83b-157">Bu öğreticide, kod dosyasında [`namespace`](../../visual-basic/language-reference/statements/namespace-statement.md) anahtar sözcüğünü kullanarak en üst düzey bir ad alanı tanımlarsınız.</span><span class="sxs-lookup"><span data-stu-id="0a83b-157">In this tutorial, you define a top-level namespace by using the [`namespace`](../../visual-basic/language-reference/statements/namespace-statement.md) keyword in the code file.</span></span>

1. <span data-ttu-id="0a83b-158">Kod penceresindeki kodu aşağıdaki kodla değiştirin ve dosyayı kaydedin:</span><span class="sxs-lookup"><span data-stu-id="0a83b-158">Replace the code in the code window with the following code and save the file:</span></span>

   [!CODE-vb[ClassLib#1](../../../samples/snippets/core/tutorials/vb-library-with-visual-studio/stringlibrary.vb)]

   <span data-ttu-id="0a83b-159">`UtilityLibraries.StringLibrary`sınıf kitaplığı, `StartsWithUpper`adlı bir yöntemi içerir.</span><span class="sxs-lookup"><span data-stu-id="0a83b-159">The class library, `UtilityLibraries.StringLibrary`, contains a method named `StartsWithUpper`.</span></span> <span data-ttu-id="0a83b-160">Bu yöntem, geçerli dize örneğinin büyük harfli bir karakterle başlayıp başlamadığını belirten bir <xref:System.Boolean> değeri döndürür.</span><span class="sxs-lookup"><span data-stu-id="0a83b-160">This method returns a <xref:System.Boolean> value that indicates whether the current string instance begins with an uppercase character.</span></span> <span data-ttu-id="0a83b-161">Unicode standart, büyük harfli karakterleri küçük harfli karakterlerden ayırır.</span><span class="sxs-lookup"><span data-stu-id="0a83b-161">The Unicode standard distinguishes uppercase characters from lowercase characters.</span></span> <span data-ttu-id="0a83b-162"><xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> yöntemi, bir karakter büyük harfle `true` döndürür.</span><span class="sxs-lookup"><span data-stu-id="0a83b-162">The <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> method returns `true` if a character is uppercase.</span></span>

1. <span data-ttu-id="0a83b-163">Menü çubuğunda **derleme** > **Build Solution**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="0a83b-163">On the menu bar, select **Build** > **Build Solution**.</span></span>

---

   <span data-ttu-id="0a83b-164">Projenin hatasız derlenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="0a83b-164">The project should compile without error.</span></span>

## <a name="next-steps"></a><span data-ttu-id="0a83b-165">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="0a83b-165">Next steps</span></span>

<span data-ttu-id="0a83b-166">Kitaplığı başarıyla derlediniz.</span><span class="sxs-lookup"><span data-stu-id="0a83b-166">You've successfully built the library.</span></span> <span data-ttu-id="0a83b-167">Yöntemlerinden herhangi birini çağırmadığınız için, beklendiği gibi çalışıp çalışmadığını bilemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="0a83b-167">Because you haven't called any of its methods, you don't know whether it works as expected.</span></span> <span data-ttu-id="0a83b-168">Kitaplığınızı geliştirmedeki bir sonraki adım, test etmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0a83b-168">The next step in developing your library is to test it.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="0a83b-169">Birim testi projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="0a83b-169">Create a unit test project</span></span>](testing-library-with-visual-studio.md)
