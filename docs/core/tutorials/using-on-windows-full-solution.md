---
title: Visual Studio 2017 kullanarak Windows'da eksiksiz bir .NET Core çözümü oluşturma
description: Visual Studio 2017 Windows üzerinde tam bir .NET Core çözümde oluşturmayı öğrenin.
author: bleroy
ms.author: mairaw
ms.date: 11/16/2016
ms.topic: conceptual
ms.prod: dotnet-core
ms.devlang: dotnet
ms.workload:
- dotnetcore
ms.openlocfilehash: 8e37eb578f9c4ac63fbc120e6227098ea69d169d
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="building-a-complete-net-core-solution-on-windows-using-visual-studio-2017"></a><span data-ttu-id="516b4-103">Visual Studio 2017 kullanarak Windows'da eksiksiz bir .NET Core çözümü oluşturma</span><span class="sxs-lookup"><span data-stu-id="516b4-103">Building a complete .NET Core solution on Windows, using Visual Studio 2017</span></span>

<span data-ttu-id="516b4-104">Visual Studio 2017 .NET Core uygulamaları geliştirmek için bir tam özellikli bir geliştirme ortamı sağlar.</span><span class="sxs-lookup"><span data-stu-id="516b4-104">Visual Studio 2017 provides a full-featured development environment for developing .NET Core applications.</span></span> <span data-ttu-id="516b4-105">Bu belgedeki yordamlar, test ve üçüncü taraf kitaplıklar kullanılarak yeniden kullanılabilir kitaplıklarını içerir tipik bir .NET Core çözümü oluşturmak için gereken adımları açıklar.</span><span class="sxs-lookup"><span data-stu-id="516b4-105">The procedures in this document describe the steps necessary to build a typical .NET Core solution that includes reusable libraries, testing, and using third-party libraries.</span></span> 

## <a name="prerequisites"></a><span data-ttu-id="516b4-106">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="516b4-106">Prerequisites</span></span>

<span data-ttu-id="516b4-107">Yönergeleri izleyerek [Önkoşullar sayfamızı](../windows-prerequisites.md) ortamınızı güncelleştirmek için.</span><span class="sxs-lookup"><span data-stu-id="516b4-107">Follow the instructions on [our prerequisites page](../windows-prerequisites.md) to update your environment.</span></span>

## <a name="a-solution-using-only-net-core-projects"></a><span data-ttu-id="516b4-108">Yalnızca .NET çekirdeği projeleri kullanarak bir çözüm</span><span class="sxs-lookup"><span data-stu-id="516b4-108">A solution using only .NET Core projects</span></span>

### <a name="writing-the-library"></a><span data-ttu-id="516b4-109">Kitaplık yazma</span><span class="sxs-lookup"><span data-stu-id="516b4-109">Writing the library</span></span>

1. <span data-ttu-id="516b4-110">Visual Studio'da, **dosya**, **yeni**, **proje**.</span><span class="sxs-lookup"><span data-stu-id="516b4-110">In Visual Studio, choose **File**, **New**, **Project**.</span></span> <span data-ttu-id="516b4-111">İçinde **yeni proje** iletişim kutusunda, genişletin **Visual C#** düğümü ve seçin **.NET standart** düğümünü ve ardından **(.NET standart)sınıfkitaplığı**.</span><span class="sxs-lookup"><span data-stu-id="516b4-111">In the **New Project** dialog, expand the **Visual C#** node and choose the **.NET Standard** node, and then choose **Class Library (.NET Standard)**.</span></span> 

2. <span data-ttu-id="516b4-112">Adı "Kitaplığı" proje ve Çözüm "Altın".</span><span class="sxs-lookup"><span data-stu-id="516b4-112">Name the project "Library" and the solution "Golden".</span></span> <span data-ttu-id="516b4-113">Bırakın **çözüm için dizin oluştur** işaretli.</span><span class="sxs-lookup"><span data-stu-id="516b4-113">Leave **Create directory for solution** checked.</span></span> <span data-ttu-id="516b4-114">**Tamam**'ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="516b4-114">Click **OK**.</span></span>

3. <span data-ttu-id="516b4-115">Çözüm Gezgini'nde bağlam menüsünü açın **bağımlılıkları** düğümü seçin **NuGet paketlerini Yönet**.</span><span class="sxs-lookup"><span data-stu-id="516b4-115">In Solution Explorer, open the context menu for the **Dependencies** node and choose **Manage NuGet Packages**.</span></span>

4. <span data-ttu-id="516b4-116">"Nuget.org" olarak seçin **paket kaynağı**ve seçin **Gözat** sekmesi. Göz **Newtonsoft.Json**.</span><span class="sxs-lookup"><span data-stu-id="516b4-116">Choose "nuget.org" as the **Package source**, and choose the **Browse** tab. Browse for **Newtonsoft.Json**.</span></span> <span data-ttu-id="516b4-117">Tıklatın **yükleme**ve Lisans Sözleşmesi'ni kabul edin.</span><span class="sxs-lookup"><span data-stu-id="516b4-117">Click **Install**, and accept the license agreement.</span></span> <span data-ttu-id="516b4-118">Paket artık altında görünmelidir **bağımlılıkları/NuGet** ve otomatik olarak geri yüklenir.</span><span class="sxs-lookup"><span data-stu-id="516b4-118">The package should now appear under **Dependencies/NuGet** and be automatically restored.</span></span>

5. <span data-ttu-id="516b4-119">Yeniden Adlandır `Class1.cs` dosyasını `Thing.cs`.</span><span class="sxs-lookup"><span data-stu-id="516b4-119">Rename the `Class1.cs` file to `Thing.cs`.</span></span> <span data-ttu-id="516b4-120">Yeniden Adlandır sınıfının kabul edin.</span><span class="sxs-lookup"><span data-stu-id="516b4-120">Accept the rename of the class.</span></span> <span data-ttu-id="516b4-121">Bir yöntem ekleyin: `public int Get(int number) => Newtonsoft.Json.JsonConvert.DeserializeObject<int>($"{number}");`</span><span class="sxs-lookup"><span data-stu-id="516b4-121">Add a method: `public int Get(int number) => Newtonsoft.Json.JsonConvert.DeserializeObject<int>($"{number}");`</span></span>

7. <span data-ttu-id="516b4-122">Üzerinde **yapı** menüsünde seçin **yapı çözümü**.</span><span class="sxs-lookup"><span data-stu-id="516b4-122">On the **Build** menu, choose **Build Solution**.</span></span>

   <span data-ttu-id="516b4-123">Çözüm hatasız oluşturması gerekir.</span><span class="sxs-lookup"><span data-stu-id="516b4-123">The solution should build without error.</span></span>

### <a name="writing-the-test-project"></a><span data-ttu-id="516b4-124">Oluşturduğunuz test projesinin yazma</span><span class="sxs-lookup"><span data-stu-id="516b4-124">Writing the test project</span></span>

1. <span data-ttu-id="516b4-125">Çözüm Gezgini'nde bağlam menüsünü açın **çözüm** düğümü seçin **Ekle**, **yeni proje**.</span><span class="sxs-lookup"><span data-stu-id="516b4-125">In Solution Explorer, open the context menu for the **Solution** node and choose **Add**, **New Project**.</span></span> <span data-ttu-id="516b4-126">İçinde **yeni proje** iletişim altında **Visual C# / .NET Core**, seçin **birim testi projesi (.NET Core)**.</span><span class="sxs-lookup"><span data-stu-id="516b4-126">In the **New Project** dialog, under **Visual C# / .NET Core**, choose **Unit Test Project (.NET Core)**.</span></span> <span data-ttu-id="516b4-127">"TestLibrary" olarak adlandırın ve Tamam'ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="516b4-127">Name it "TestLibrary" and click OK.</span></span> 

2. <span data-ttu-id="516b4-128">İçinde **TestLibrary** proje, bağlam menüsünü açın **bağımlılıkları** düğümü seçin **Başvuru Ekle**.</span><span class="sxs-lookup"><span data-stu-id="516b4-128">In the **TestLibrary** project, open the context menu for the **Dependencies** node and choose **Add Reference**.</span></span> <span data-ttu-id="516b4-129">Tıklatın **projeleri**, ardından kitaplığı projesi kontrol edin ve Tamam'ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="516b4-129">Click **Projects**, then check the Library project and click OK.</span></span> <span data-ttu-id="516b4-130">Bu test projesinin kitaplığınıza bir başvuru ekler.</span><span class="sxs-lookup"><span data-stu-id="516b4-130">This adds a reference to your library from the test project.</span></span>

3. <span data-ttu-id="516b4-131">Yeniden Adlandır `UnitTest1.cs` dosya `LibraryTests.cs` ve sınıf rename kabul edin.</span><span class="sxs-lookup"><span data-stu-id="516b4-131">Rename the `UnitTest1.cs` file to `LibraryTests.cs` and accept the class rename.</span></span> <span data-ttu-id="516b4-132">Ekleme `using Library;` dosyasını ve Değiştir üstüne `TestMethod1` aşağıdaki kod ile yöntemi:</span><span class="sxs-lookup"><span data-stu-id="516b4-132">Add `using Library;` to the top of the file, and replace the `TestMethod1` method with the following code:</span></span>
    ```csharp
    [TestMethod]
    public void ThingGetsObjectValFromNumber()
    {
        Assert.AreEqual(42, new Thing().Get(42));
    }
    ```

   <span data-ttu-id="516b4-133">Artık çözümü oluşturabiliyor olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="516b4-133">You should now be able to build the solution.</span></span> 
   
4. <span data-ttu-id="516b4-134">Üzerinde **Test** menüsünde seçin **Windows**, **Test Gezgini** test Gezgini penceresi çalışma alanınıza alabilmek için.</span><span class="sxs-lookup"><span data-stu-id="516b4-134">On the **Test** menu, choose **Windows**, **Test Explorer** in order to get the test explorer window into your workspace.</span></span> <span data-ttu-id="516b4-135">Birkaç saniye sonra `ThingGetsObjectValFromNumber` test test Explorer'da görünmelidir.</span><span class="sxs-lookup"><span data-stu-id="516b4-135">After a few seconds, the `ThingGetsObjectValFromNumber` test should appear in the test explorer.</span></span> <span data-ttu-id="516b4-136">Seçin **çalıştırması**.</span><span class="sxs-lookup"><span data-stu-id="516b4-136">Choose **Run All**.</span></span>
   
   <span data-ttu-id="516b4-137">Test geçirmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="516b4-137">The test should pass.</span></span>

### <a name="writing-the-console-app"></a><span data-ttu-id="516b4-138">Konsol uygulaması yazma</span><span class="sxs-lookup"><span data-stu-id="516b4-138">Writing the console app</span></span>

1. <span data-ttu-id="516b4-139">Çözüm Gezgini'nde, çözüm bağlam menüsünü açın ve yeni bir ekleyin **konsol uygulaması (.NET Core)** projesi.</span><span class="sxs-lookup"><span data-stu-id="516b4-139">In Solution Explorer, open the context menu for the solution, and add a new **Console App (.NET Core)** project.</span></span> <span data-ttu-id="516b4-140">"Uygulama" adı.</span><span class="sxs-lookup"><span data-stu-id="516b4-140">Name it "App".</span></span>

2. <span data-ttu-id="516b4-141">İçinde **uygulama** proje, bağlam menüsünü açın **bağımlılıkları** düğümü seçin **Ekle**, **başvuru**.</span><span class="sxs-lookup"><span data-stu-id="516b4-141">In the **App** project, open the context menu for the **Dependencies** node and choose **Add**,  **Reference**.</span></span> 

3. <span data-ttu-id="516b4-142">İçinde **başvuru Yöneticisi** iletişim kutusunda, onay **Kitaplığı** altında **projeleri**, **çözüm** düğümünü ve ardından **Tamam**</span><span class="sxs-lookup"><span data-stu-id="516b4-142">In the **Reference Manager** dialog, check **Library** under the **Projects**, **Solution** node, and then click **OK**</span></span>

6. <span data-ttu-id="516b4-143">Bağlam menüsünü açın **uygulama** düğümü seçin **başlangıç projesi olarak ayarla**.</span><span class="sxs-lookup"><span data-stu-id="516b4-143">Open the context menu for the **App** node and choose **Set as StartUp Project**.</span></span> <span data-ttu-id="516b4-144">Bu, F5 veya CTRL + F5 tuşuna konsol uygulaması başlangıç sağlar.</span><span class="sxs-lookup"><span data-stu-id="516b4-144">This ensures that hitting F5 or CTRL+F5 will start the console app.</span></span>

7. <span data-ttu-id="516b4-145">Açık `Program.cs` dosya, ekleme bir `using Library;` dosyanın en üstüne yönerge ve ardından ekleyin `Console.WriteLine($"The answer is {new Thing().Get(42)}.");` için `Main` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="516b4-145">Open the `Program.cs` file, add a `using Library;` directive to the top of the file, and then add `Console.WriteLine($"The answer is {new Thing().Get(42)}.");` to the `Main` method.</span></span>

8. <span data-ttu-id="516b4-146">Yeni eklediğiniz satırından sonra bir kesme noktası ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="516b4-146">Set a breakpoint after the line that you just added.</span></span>

9. <span data-ttu-id="516b4-147">Uygulamayı çalıştırmak için F5'e basın...</span><span class="sxs-lookup"><span data-stu-id="516b4-147">Press F5 to run the application..</span></span>

   <span data-ttu-id="516b4-148">Uygulama hatasız oluşturmalısınız ve kesme noktası isabet.</span><span class="sxs-lookup"><span data-stu-id="516b4-148">The application should build without error, and should hit the breakpoint.</span></span> <span data-ttu-id="516b4-149">Uygulama "yanıt 42 var." çıktı denetleyebilmek olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="516b4-149">You should also be able to check that the application output "The answer is 42.".</span></span>
