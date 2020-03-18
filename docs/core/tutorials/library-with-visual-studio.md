---
title: Visual Studio'da .NET Standart sınıf kitaplığı oluşturma
description: Visual Studio'u kullanarak C# veya Visual Basic ile yazılmış bir .NET Standart sınıf kitaplığı oluşturmayı öğrenin
ms.date: 12/09/2019
ms.custom: vs-dotnet
ms.openlocfilehash: 748a1499e0c3a4a41613a69b715dbcfbd585bfe3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75714015"
---
# <a name="build-a-net-standard-library-in-visual-studio"></a><span data-ttu-id="e55fa-103">Visual Studio'da bir .NET Standart kitaplığı oluşturun</span><span class="sxs-lookup"><span data-stu-id="e55fa-103">Build a .NET Standard library in Visual Studio</span></span>

<span data-ttu-id="e55fa-104">*Sınıf kitaplığı,* uygulama tarafından çağrılan türleri ve yöntemleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e55fa-104">A *class library* defines types and methods that are called by an application.</span></span> <span data-ttu-id="e55fa-105">.NET Standart 2.0'ı hedefleyen bir sınıf kitaplığı, kitaplığınızın .NET Standard'ın bu sürümünü destekleyen herhangi bir .NET uygulaması tarafından çağrılmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="e55fa-105">A class library that targets .NET Standard 2.0 allows your library to be called by any .NET implementation that supports that version of .NET Standard.</span></span> <span data-ttu-id="e55fa-106">Sınıf kitaplığınızı bitirdiğinizde, onu üçüncü taraf bileşeni olarak mı yoksa bir veya daha fazla uygulamaiçeren paketlenmiş bir bileşen olarak mı eklemek istediğinize karar verebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e55fa-106">When you finish your class library, you can decide whether you want to distribute it as a third-party component or whether you want to include it as a bundled component with one or more applications.</span></span>

> [!NOTE]
> <span data-ttu-id="e55fa-107">.NET Standart sürümlerinin ve destekledikleri platformların listesi [için](../../standard/net-standard.md)bkz.</span><span class="sxs-lookup"><span data-stu-id="e55fa-107">For a list of .NET Standard versions and the platforms they support, see [.NET Standard](../../standard/net-standard.md).</span></span>

<span data-ttu-id="e55fa-108">Bu konuda, tek bir dize işleme yöntemi içeren basit bir yardımcı program kitaplığı oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="e55fa-108">In this topic, you'll create a simple utility library that contains a single string-handling method.</span></span> <span data-ttu-id="e55fa-109">Sınıfın bir üyesiysek <xref:System.String> diye adlandırabilmeniz için bunu bir [uzantı yöntemi](../../csharp/programming-guide/classes-and-structs/extension-methods.md) olarak uygularsınız.</span><span class="sxs-lookup"><span data-stu-id="e55fa-109">You'll implement it as an [extension method](../../csharp/programming-guide/classes-and-structs/extension-methods.md) so that you can call it as if it were a member of the <xref:System.String> class.</span></span>

## <a name="create-a-visual-studio-solution"></a><span data-ttu-id="e55fa-110">Visual Studio çözümü oluşturun</span><span class="sxs-lookup"><span data-stu-id="e55fa-110">Create a Visual Studio solution</span></span>

<span data-ttu-id="e55fa-111">Sınıf kitaplığı projesini koymak için boş bir çözüm oluşturarak başlayın.</span><span class="sxs-lookup"><span data-stu-id="e55fa-111">Start by creating a blank solution to put the class library project in.</span></span> <span data-ttu-id="e55fa-112">Visual Studio çözümü, bir veya daha fazla proje için bir kapsayıcı görevi görehizmet eder.</span><span class="sxs-lookup"><span data-stu-id="e55fa-112">A Visual Studio solution serves as a container for one or more projects.</span></span> <span data-ttu-id="e55fa-113">Öğretici seriye devam ederseniz, aynı çözüme ek, ilgili projeler eklersiniz.</span><span class="sxs-lookup"><span data-stu-id="e55fa-113">You'll add additional, related projects to the same solution if you continue on with the tutorial series.</span></span>

<span data-ttu-id="e55fa-114">Boş çözümü oluşturmak için:</span><span class="sxs-lookup"><span data-stu-id="e55fa-114">To create the blank solution:</span></span>

1. <span data-ttu-id="e55fa-115">Visual Studio'yu açın.</span><span class="sxs-lookup"><span data-stu-id="e55fa-115">Open Visual Studio.</span></span>

2. <span data-ttu-id="e55fa-116">Başlangıç penceresinde yeni **bir proje oluştur'u**seçin.</span><span class="sxs-lookup"><span data-stu-id="e55fa-116">On the start window, choose **Create a new project**.</span></span>

3. <span data-ttu-id="e55fa-117">Yeni **bir proje oluştur** sayfasında, **çözüm** arama kutusuna girin.</span><span class="sxs-lookup"><span data-stu-id="e55fa-117">On the **Create a new project** page, enter **solution** in the search box.</span></span> <span data-ttu-id="e55fa-118">Boş **Çözüm** şablonu'nu seçin ve sonra **İleri'yi**seçin.</span><span class="sxs-lookup"><span data-stu-id="e55fa-118">Choose the **Blank Solution** template, and then choose **Next**.</span></span>

   ![Visual Studio'da boş çözüm şablonu](media/library-with-visual-studio/blank-solution.png)

4. <span data-ttu-id="e55fa-120">Yeni **proje sayfanızı Yapılandır'da,** Proje **adı** kutusuna **ClassLibraryProjects'i** girin.</span><span class="sxs-lookup"><span data-stu-id="e55fa-120">On the **Configure your new project** page, enter **ClassLibraryProjects** in the **Project name** box.</span></span> <span data-ttu-id="e55fa-121">Ardından **Oluştur'u**seçin.</span><span class="sxs-lookup"><span data-stu-id="e55fa-121">Then, choose **Create**.</span></span>

> [!TIP]
> <span data-ttu-id="e55fa-122">Ayrıca bu adımı atlayabilir ve bir sonraki adımda projeyi oluştururken Visual Studio'nun sizin için çözüm oluşturmasına izin verebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e55fa-122">You can also skip this step and let Visual Studio create the solution for you when you create the project in the next step.</span></span> <span data-ttu-id="e55fa-123">**Yeni proje sayfanızda Yapılandır'daki** çözüm seçeneklerini arayın.</span><span class="sxs-lookup"><span data-stu-id="e55fa-123">Look for the solution options on the **Configure your new project** page.</span></span>

## <a name="create-a-class-library-project"></a><span data-ttu-id="e55fa-124">Sınıf kitaplığı projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="e55fa-124">Create a class library project</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="c"></a>[<span data-ttu-id="e55fa-125">C #</span><span class="sxs-lookup"><span data-stu-id="e55fa-125">C#</span></span>](#tab/csharp)

1. <span data-ttu-id="e55fa-126">Çözüme "StringLibrary" adlı yeni bir C# .NET Standart sınıf kitaplık projesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="e55fa-126">Add a new C# .NET Standard class library project named "StringLibrary" to the solution.</span></span>

   1. <span data-ttu-id="e55fa-127">**Solution Explorer'da** çözüme sağ tıklayın ve**Yeni proje** **Ekle'yi** > seçin.</span><span class="sxs-lookup"><span data-stu-id="e55fa-127">Right-click on the solution in **Solution Explorer** and select **Add** > **New project**.</span></span>

   1. <span data-ttu-id="e55fa-128">Yeni **bir proje ekle** sayfasında, arama kutusuna **kitaplığı** girin.</span><span class="sxs-lookup"><span data-stu-id="e55fa-128">On the **Add a new project** page, enter **library** in the search box.</span></span> <span data-ttu-id="e55fa-129">Dil listesinden **C#** seçeneğini seçin ve ardından Platform listesinden **Tüm platformları** seçin.</span><span class="sxs-lookup"><span data-stu-id="e55fa-129">Choose **C#** from the Language list, and then choose **All platforms** from the Platform list.</span></span> <span data-ttu-id="e55fa-130">Sınıf **Kitaplığı (.NET Standart)** şablonu seçin ve sonra **İleri'yi**seçin.</span><span class="sxs-lookup"><span data-stu-id="e55fa-130">Choose the **Class Library (.NET Standard)** template, and then choose **Next**.</span></span>

   1. <span data-ttu-id="e55fa-131">Yeni **proje sayfanızı Yapılandır'da,** **Proje adı** kutusuna **StringLibrary'yi** girin.</span><span class="sxs-lookup"><span data-stu-id="e55fa-131">On the **Configure your new project** page, enter **StringLibrary** in the **Project name** box.</span></span> <span data-ttu-id="e55fa-132">Ardından **Oluştur'u**seçin.</span><span class="sxs-lookup"><span data-stu-id="e55fa-132">Then, choose **Create**.</span></span>

1. <span data-ttu-id="e55fa-133">Kitaplığın .NET Standard'ın doğru sürümünü hedefaldığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="e55fa-133">Check to make sure that the library targets the correct version of .NET Standard.</span></span> <span data-ttu-id="e55fa-134">**Çözüm Gezgini'ndeki**kitaplık projesine sağ tıklayın ve ardından **Özellikler'i**seçin.</span><span class="sxs-lookup"><span data-stu-id="e55fa-134">Right-click on the library project in **Solution Explorer**, and then select **Properties**.</span></span> <span data-ttu-id="e55fa-135">**Hedef Çerçeve** metin kutusu, projenin .NET Standard 2.0'ı hedefaldığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e55fa-135">The **Target Framework** text box shows that the project targets .NET Standard 2.0.</span></span>

   ![Sınıf kitaplığı için proje özellikleri](./media/library-with-visual-studio/library-project-properties.png)

1. <span data-ttu-id="e55fa-137">Kod penceresindeki kodu aşağıdaki kodla değiştirin ve dosyayı kaydedin:</span><span class="sxs-lookup"><span data-stu-id="e55fa-137">Replace the code in the code window with the following code and save the file:</span></span>

   [!CODE-csharp[ClassLib#1](../../../samples/snippets/csharp/getting_started/with_visual_studio_2017/classlib.cs)]

   <span data-ttu-id="e55fa-138">Sınıf kitaplığı, `UtilityLibraries.StringLibrary`adlı `StartsWithUpper`bir yöntem içerir.</span><span class="sxs-lookup"><span data-stu-id="e55fa-138">The class library, `UtilityLibraries.StringLibrary`, contains a method named `StartsWithUpper`.</span></span> <span data-ttu-id="e55fa-139">Bu yöntem, <xref:System.Boolean> geçerli dize örneğinin büyük harfli bir karakterle başlayıp başlamadığını gösteren bir değer döndürür.</span><span class="sxs-lookup"><span data-stu-id="e55fa-139">This method returns a <xref:System.Boolean> value that indicates whether the current string instance begins with an uppercase character.</span></span> <span data-ttu-id="e55fa-140">Unicode standardı büyük harflerkarakterleri küçük karakterlerden ayırır.</span><span class="sxs-lookup"><span data-stu-id="e55fa-140">The Unicode standard distinguishes uppercase characters from lowercase characters.</span></span> <span data-ttu-id="e55fa-141">Bir <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> karakter `true` büyük harfse yöntem döndürür.</span><span class="sxs-lookup"><span data-stu-id="e55fa-141">The <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> method returns `true` if a character is uppercase.</span></span>

1. <span data-ttu-id="e55fa-142">Menü çubuğunda **Yapı** > **Çözümünü**seçin.</span><span class="sxs-lookup"><span data-stu-id="e55fa-142">On the menu bar, select **Build** > **Build Solution**.</span></span>

# <a name="visual-basic"></a>[<span data-ttu-id="e55fa-143">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e55fa-143">Visual Basic</span></span>](#tab/vb)

1. <span data-ttu-id="e55fa-144">Çözüme "StringLibrary" adlı yeni bir Visual Basic .NET Standart sınıf kitaplık projesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="e55fa-144">Add a new Visual Basic .NET Standard class library project named "StringLibrary" to the solution.</span></span>

   1. <span data-ttu-id="e55fa-145">**Solution Explorer'da** çözüme sağ tıklayın ve**Yeni proje** **Ekle'yi** > seçin.</span><span class="sxs-lookup"><span data-stu-id="e55fa-145">Right-click on the solution in **Solution Explorer** and select **Add** > **New project**.</span></span>

   1. <span data-ttu-id="e55fa-146">Yeni **bir proje ekle** sayfasında, arama kutusuna **kitaplığı** girin.</span><span class="sxs-lookup"><span data-stu-id="e55fa-146">On the **Add a new project** page, enter **library** in the search box.</span></span> <span data-ttu-id="e55fa-147">Dil listesinden **Visual Basic'i** seçin ve ardından Platform listesindeki **Tüm platformları** seçin.</span><span class="sxs-lookup"><span data-stu-id="e55fa-147">Choose **Visual Basic** from the Language list, and then choose **All platforms** from the Platform list.</span></span> <span data-ttu-id="e55fa-148">Sınıf **Kitaplığı (.NET Standart)** şablonu seçin ve sonra **İleri'yi**seçin.</span><span class="sxs-lookup"><span data-stu-id="e55fa-148">Choose the **Class Library (.NET Standard)** template, and then choose **Next**.</span></span>

   1. <span data-ttu-id="e55fa-149">Yeni **proje sayfanızı Yapılandır'da,** **Proje adı** kutusuna **StringLibrary'yi** girin.</span><span class="sxs-lookup"><span data-stu-id="e55fa-149">On the **Configure your new project** page, enter **StringLibrary** in the **Project name** box.</span></span> <span data-ttu-id="e55fa-150">Ardından **Oluştur'u**seçin.</span><span class="sxs-lookup"><span data-stu-id="e55fa-150">Then, choose **Create**.</span></span>

1. <span data-ttu-id="e55fa-151">Kitaplığın .NET Standard'ın doğru sürümünü hedefaldığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="e55fa-151">Check to make sure that the library targets the correct version of .NET Standard.</span></span> <span data-ttu-id="e55fa-152">**Çözüm Gezgini'ndeki**kitaplık projesine sağ tıklayın ve ardından **Özellikler'i**seçin.</span><span class="sxs-lookup"><span data-stu-id="e55fa-152">Right-click on the library project in **Solution Explorer**, and then select **Properties**.</span></span> <span data-ttu-id="e55fa-153">**Hedef Çerçeve** metin kutusu, projenin .NET Standard 2.0'ı hedefaldığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e55fa-153">The **Target Framework** text box shows that the project targets .NET Standard 2.0.</span></span>

   ![Sınıf kitaplığı için proje özellikleri](./media/library-with-visual-studio/vb/library-project-properties.png)

1. <span data-ttu-id="e55fa-155">**Özellikler** iletişim kutusunda, Kök ad **alanı** metin kutusundaki metni temizleyin.</span><span class="sxs-lookup"><span data-stu-id="e55fa-155">In the **Properties** dialog, clear the text in the **Root namespace** text box.</span></span> <span data-ttu-id="e55fa-156">Her proje için Visual Basic otomatik olarak proje adına karşılık gelen bir ad alanı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e55fa-156">For each project, Visual Basic automatically creates a namespace that corresponds to the project name.</span></span> <span data-ttu-id="e55fa-157">Bu öğreticide, kod dosyasındaki anahtar kelimeyi [`namespace`](../../visual-basic/language-reference/statements/namespace-statement.md) kullanarak üst düzey bir ad alanı tanımlarsınız.</span><span class="sxs-lookup"><span data-stu-id="e55fa-157">In this tutorial, you define a top-level namespace by using the [`namespace`](../../visual-basic/language-reference/statements/namespace-statement.md) keyword in the code file.</span></span>

1. <span data-ttu-id="e55fa-158">Kod penceresindeki kodu aşağıdaki kodla değiştirin ve dosyayı kaydedin:</span><span class="sxs-lookup"><span data-stu-id="e55fa-158">Replace the code in the code window with the following code and save the file:</span></span>

   [!CODE-vb[ClassLib#1](../../../samples/snippets/core/tutorials/vb-library-with-visual-studio/stringlibrary.vb)]

   <span data-ttu-id="e55fa-159">Sınıf kitaplığı, `UtilityLibraries.StringLibrary`adlı `StartsWithUpper`bir yöntem içerir.</span><span class="sxs-lookup"><span data-stu-id="e55fa-159">The class library, `UtilityLibraries.StringLibrary`, contains a method named `StartsWithUpper`.</span></span> <span data-ttu-id="e55fa-160">Bu yöntem, <xref:System.Boolean> geçerli dize örneğinin büyük harfli bir karakterle başlayıp başlamadığını gösteren bir değer döndürür.</span><span class="sxs-lookup"><span data-stu-id="e55fa-160">This method returns a <xref:System.Boolean> value that indicates whether the current string instance begins with an uppercase character.</span></span> <span data-ttu-id="e55fa-161">Unicode standardı büyük harflerkarakterleri küçük karakterlerden ayırır.</span><span class="sxs-lookup"><span data-stu-id="e55fa-161">The Unicode standard distinguishes uppercase characters from lowercase characters.</span></span> <span data-ttu-id="e55fa-162">Bir <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> karakter `true` büyük harfse yöntem döndürür.</span><span class="sxs-lookup"><span data-stu-id="e55fa-162">The <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> method returns `true` if a character is uppercase.</span></span>

1. <span data-ttu-id="e55fa-163">Menü çubuğunda **Yapı** > **Çözümünü**seçin.</span><span class="sxs-lookup"><span data-stu-id="e55fa-163">On the menu bar, select **Build** > **Build Solution**.</span></span>

---

   <span data-ttu-id="e55fa-164">Proje hatasız derlemelidir.</span><span class="sxs-lookup"><span data-stu-id="e55fa-164">The project should compile without error.</span></span>

## <a name="next-steps"></a><span data-ttu-id="e55fa-165">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="e55fa-165">Next steps</span></span>

<span data-ttu-id="e55fa-166">Kütüphaneyi başarıyla inşa ettin.</span><span class="sxs-lookup"><span data-stu-id="e55fa-166">You've successfully built the library.</span></span> <span data-ttu-id="e55fa-167">Yöntemlerinin hiçbirini aramadığınız için beklendiği gibi çalışıp çalışmadığını bilmiyorsun.</span><span class="sxs-lookup"><span data-stu-id="e55fa-167">Because you haven't called any of its methods, you don't know whether it works as expected.</span></span> <span data-ttu-id="e55fa-168">Kitaplığınızı geliştirmenin bir sonraki adımı bunu test etmektir.</span><span class="sxs-lookup"><span data-stu-id="e55fa-168">The next step in developing your library is to test it.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="e55fa-169">Birim testi projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="e55fa-169">Create a unit test project</span></span>](testing-library-with-visual-studio.md)
