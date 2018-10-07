---
title: Visual Studio 2017'yi kullanarak, Windows üzerinde eksiksiz bir .NET Core çözümü derleme
description: Windows üzerinde Visual Studio 2017'de eksiksiz bir .NET Core çözümü oluşturmayı öğrenin.
author: bleroy
ms.author: mairaw
ms.date: 11/16/2016
ms.custom: vs-dotnet
ms.openlocfilehash: c21c257b55c4389ea4a60fca55eb83cff60ff3b5
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2018
ms.locfileid: "48840946"
---
# <a name="building-a-complete-net-core-solution-on-windows-using-visual-studio-2017"></a><span data-ttu-id="c526e-103">Visual Studio 2017'yi kullanarak, Windows üzerinde eksiksiz bir .NET Core çözümü derleme</span><span class="sxs-lookup"><span data-stu-id="c526e-103">Building a complete .NET Core solution on Windows, using Visual Studio 2017</span></span>

<span data-ttu-id="c526e-104">Visual Studio 2017, .NET Core uygulamaları geliştirmek için bir tam özellikli bir geliştirme ortamı sağlar.</span><span class="sxs-lookup"><span data-stu-id="c526e-104">Visual Studio 2017 provides a full-featured development environment for developing .NET Core applications.</span></span> <span data-ttu-id="c526e-105">Bu belgedeki yordamları, test ve üçüncü taraf kitaplıklar kullanılarak yeniden kullanılabilir kitaplıklar içeren tipik bir .NET Core çözümü oluşturmak gereken adımları açıklar.</span><span class="sxs-lookup"><span data-stu-id="c526e-105">The procedures in this document describe the steps necessary to build a typical .NET Core solution that includes reusable libraries, testing, and using third-party libraries.</span></span> 

## <a name="prerequisites"></a><span data-ttu-id="c526e-106">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="c526e-106">Prerequisites</span></span>

<span data-ttu-id="c526e-107">Yönergeleri takip edin [önkoşulları sayfamızı](../windows-prerequisites.md) ortamınızı güncelleştirilecek.</span><span class="sxs-lookup"><span data-stu-id="c526e-107">Follow the instructions on [our prerequisites page](../windows-prerequisites.md) to update your environment.</span></span>

## <a name="a-solution-using-only-net-core-projects"></a><span data-ttu-id="c526e-108">Yalnızca .NET Core projeleri kullanarak çözümü</span><span class="sxs-lookup"><span data-stu-id="c526e-108">A solution using only .NET Core projects</span></span>

### <a name="writing-the-library"></a><span data-ttu-id="c526e-109">Kitaplığı yazma</span><span class="sxs-lookup"><span data-stu-id="c526e-109">Writing the library</span></span>

1. <span data-ttu-id="c526e-110">Visual Studio'da **dosya**, **yeni**, **proje**.</span><span class="sxs-lookup"><span data-stu-id="c526e-110">In Visual Studio, choose **File**, **New**, **Project**.</span></span> <span data-ttu-id="c526e-111">İçinde **yeni proje** iletişim kutusunda genişletin **Visual C#** düğüm ve **.NET Standard** düğümünü ve ardından **sınıf kitaplığı (.NET Standard)**.</span><span class="sxs-lookup"><span data-stu-id="c526e-111">In the **New Project** dialog, expand the **Visual C#** node and choose the **.NET Standard** node, and then choose **Class Library (.NET Standard)**.</span></span> <span data-ttu-id="c526e-112">Bu .NET Core hedefleyen bir .NET Standard kitaplığı 2.0 sürümünü destekleyen her bir .NET uygulaması oluşturur [.Net standart](https://docs.microsoft.com/en-us/dotnet/standard/net-standard)</span><span class="sxs-lookup"><span data-stu-id="c526e-112">This creates a .NET Standard library that targets .NET Core as well as any other .NET implementation that supports version 2.0 of the [.Net Standard](https://docs.microsoft.com/en-us/dotnet/standard/net-standard)</span></span>

2. <span data-ttu-id="c526e-113">Adı ' % s'projesi "Library" ve "Altın" Çözüm.</span><span class="sxs-lookup"><span data-stu-id="c526e-113">Name the project "Library" and the solution "Golden".</span></span> <span data-ttu-id="c526e-114">Bırakın **çözüm için dizin oluştur** işaretli.</span><span class="sxs-lookup"><span data-stu-id="c526e-114">Leave **Create directory for solution** checked.</span></span> <span data-ttu-id="c526e-115">**Tamam**'ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="c526e-115">Click **OK**.</span></span>

3. <span data-ttu-id="c526e-116">Çözüm Gezgini'nde, bağlam menüsünü açın **bağımlılıkları** düğümünü seçip **NuGet paketlerini Yönet**.</span><span class="sxs-lookup"><span data-stu-id="c526e-116">In Solution Explorer, open the context menu for the **Dependencies** node and choose **Manage NuGet Packages**.</span></span>

4. <span data-ttu-id="c526e-117">"Nuget.org" olarak seçin **paket kaynağı**ve **Gözat** sekmesi. Göz atın **Newtonsoft.Json**.</span><span class="sxs-lookup"><span data-stu-id="c526e-117">Choose "nuget.org" as the **Package source**, and choose the **Browse** tab. Browse for **Newtonsoft.Json**.</span></span> <span data-ttu-id="c526e-118">Tıklayın **yükleme**, lisans sözleşmesini kabul edin.</span><span class="sxs-lookup"><span data-stu-id="c526e-118">Click **Install**, and accept the license agreement.</span></span> <span data-ttu-id="c526e-119">Paket artık altında görünmelidir **bağımlılıkları/NuGet** ve otomatik olarak geri yüklenir.</span><span class="sxs-lookup"><span data-stu-id="c526e-119">The package should now appear under **Dependencies/NuGet** and be automatically restored.</span></span>

5. <span data-ttu-id="c526e-120">Yeniden adlandırma `Class1.cs` dosyasını `Thing.cs`.</span><span class="sxs-lookup"><span data-stu-id="c526e-120">Rename the `Class1.cs` file to `Thing.cs`.</span></span> <span data-ttu-id="c526e-121">Sınıfı yeniden adlandırılması kabul edin.</span><span class="sxs-lookup"><span data-stu-id="c526e-121">Accept the rename of the class.</span></span> <span data-ttu-id="c526e-122">Bir yöntem ekleyin: `public int Get(int number) => Newtonsoft.Json.JsonConvert.DeserializeObject<int>($"{number}");`</span><span class="sxs-lookup"><span data-stu-id="c526e-122">Add a method: `public int Get(int number) => Newtonsoft.Json.JsonConvert.DeserializeObject<int>($"{number}");`</span></span>

7. <span data-ttu-id="c526e-123">Üzerinde **derleme** menüsünde seçin **Çözümü Derle**.</span><span class="sxs-lookup"><span data-stu-id="c526e-123">On the **Build** menu, choose **Build Solution**.</span></span>

   <span data-ttu-id="c526e-124">Çözüm, hatasız oluşturması gerekir.</span><span class="sxs-lookup"><span data-stu-id="c526e-124">The solution should build without error.</span></span>

### <a name="writing-the-test-project"></a><span data-ttu-id="c526e-125">Test projesi yazma</span><span class="sxs-lookup"><span data-stu-id="c526e-125">Writing the test project</span></span>

1. <span data-ttu-id="c526e-126">Çözüm Gezgini'nde, bağlam menüsünü açın **çözüm** düğümünü seçip **Ekle**, **yeni proje**.</span><span class="sxs-lookup"><span data-stu-id="c526e-126">In Solution Explorer, open the context menu for the **Solution** node and choose **Add**, **New Project**.</span></span> <span data-ttu-id="c526e-127">İçinde **yeni proje** iletişim altında **Visual C# / .NET Core**, seçin **birim testi projesi (.NET Core)**.</span><span class="sxs-lookup"><span data-stu-id="c526e-127">In the **New Project** dialog, under **Visual C# / .NET Core**, choose **Unit Test Project (.NET Core)**.</span></span> <span data-ttu-id="c526e-128">"TestLibrary" olarak adlandırın ve Tamam'a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="c526e-128">Name it "TestLibrary" and click OK.</span></span> 

2. <span data-ttu-id="c526e-129">İçinde **TestLibrary** için bağlam menüsünü açın, proje **bağımlılıkları** düğüm ve **Başvuru Ekle**.</span><span class="sxs-lookup"><span data-stu-id="c526e-129">In the **TestLibrary** project, open the context menu for the **Dependencies** node and choose **Add Reference**.</span></span> <span data-ttu-id="c526e-130">Tıklayın **projeleri**, sonra kitaplık projesi işaretleyin ve Tamam'a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="c526e-130">Click **Projects**, then check the Library project and click OK.</span></span> <span data-ttu-id="c526e-131">Bu test projesinden, kitaplığına bir başvuru ekler.</span><span class="sxs-lookup"><span data-stu-id="c526e-131">This adds a reference to your library from the test project.</span></span>

3. <span data-ttu-id="c526e-132">Yeniden adlandırma `UnitTest1.cs` dosyasını `LibraryTests.cs` sınıfı yeniden adlandır kabul edin.</span><span class="sxs-lookup"><span data-stu-id="c526e-132">Rename the `UnitTest1.cs` file to `LibraryTests.cs` and accept the class rename.</span></span> <span data-ttu-id="c526e-133">Ekleme `using Library;` dosyasını ve değiştirme en üstüne `TestMethod1` yöntemini aşağıdaki kod ile:</span><span class="sxs-lookup"><span data-stu-id="c526e-133">Add `using Library;` to the top of the file, and replace the `TestMethod1` method with the following code:</span></span>
    ```csharp
    [TestMethod]
    public void ThingGetsObjectValFromNumber()
    {
        Assert.AreEqual(42, new Thing().Get(42));
    }
    ```

   <span data-ttu-id="c526e-134">Şimdi çözüm oluşturulabiliyor olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="c526e-134">You should now be able to build the solution.</span></span> 
   
4. <span data-ttu-id="c526e-135">Üzerinde **Test** menüsünde seçin **Windows**, **Test Gezgini** test Gezgini penceresi çalışma alanınıza almak için.</span><span class="sxs-lookup"><span data-stu-id="c526e-135">On the **Test** menu, choose **Windows**, **Test Explorer** in order to get the test explorer window into your workspace.</span></span> <span data-ttu-id="c526e-136">Birkaç saniye sonra `ThingGetsObjectValFromNumber` test, test Gezgini'nde görüntülenmelidir.</span><span class="sxs-lookup"><span data-stu-id="c526e-136">After a few seconds, the `ThingGetsObjectValFromNumber` test should appear in the test explorer.</span></span> <span data-ttu-id="c526e-137">Seçin **çalıştırması**.</span><span class="sxs-lookup"><span data-stu-id="c526e-137">Choose **Run All**.</span></span>
   
   <span data-ttu-id="c526e-138">Test geçişi yapılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c526e-138">The test should pass.</span></span>

### <a name="writing-the-console-app"></a><span data-ttu-id="c526e-139">Konsol uygulaması yazma</span><span class="sxs-lookup"><span data-stu-id="c526e-139">Writing the console app</span></span>

1. <span data-ttu-id="c526e-140">Çözüm Gezgini'nde, çözümü için bağlam menüsünü açın ve yeni bir **konsol uygulaması (.NET Core)** proje.</span><span class="sxs-lookup"><span data-stu-id="c526e-140">In Solution Explorer, open the context menu for the solution, and add a new **Console App (.NET Core)** project.</span></span> <span data-ttu-id="c526e-141">"Uygulama" olarak adlandırın.</span><span class="sxs-lookup"><span data-stu-id="c526e-141">Name it "App".</span></span>

2. <span data-ttu-id="c526e-142">İçinde **uygulama** için bağlam menüsünü açın, proje **bağımlılıkları** düğüm ve **Ekle**, **başvuru**.</span><span class="sxs-lookup"><span data-stu-id="c526e-142">In the **App** project, open the context menu for the **Dependencies** node and choose **Add**,  **Reference**.</span></span> 

3. <span data-ttu-id="c526e-143">İçinde **başvuru Yöneticisi** iletişim kutusunda, onay **Kitaplığı** altında **projeleri**, **çözüm** düğümünü ve ardından **Tamam**</span><span class="sxs-lookup"><span data-stu-id="c526e-143">In the **Reference Manager** dialog, check **Library** under the **Projects**, **Solution** node, and then click **OK**</span></span>

6. <span data-ttu-id="c526e-144">Bağlam menüsünü **uygulama** düğüm ve **başlangıç projesi olarak ayarla**.</span><span class="sxs-lookup"><span data-stu-id="c526e-144">Open the context menu for the **App** node and choose **Set as StartUp Project**.</span></span> <span data-ttu-id="c526e-145">Bu, F5 veya CTRL + F5 tuşlarına basarak konsol uygulamasını Başlat sağlar.</span><span class="sxs-lookup"><span data-stu-id="c526e-145">This ensures that hitting F5 or CTRL+F5 will start the console app.</span></span>

7. <span data-ttu-id="c526e-146">Açık `Program.cs` ekleyin bir `using Library;` dosyanın en üstüne yönerge ve ardından eklemek `Console.WriteLine($"The answer is {new Thing().Get(42)}.");` için `Main` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="c526e-146">Open the `Program.cs` file, add a `using Library;` directive to the top of the file, and then add `Console.WriteLine($"The answer is {new Thing().Get(42)}.");` to the `Main` method.</span></span>

8. <span data-ttu-id="c526e-147">Az önce eklediğiniz bir satırın sonunda bir kesme noktası ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="c526e-147">Set a breakpoint after the line that you just added.</span></span>

9. <span data-ttu-id="c526e-148">Uygulamayı çalıştırmak için F5 tuşuna basın...</span><span class="sxs-lookup"><span data-stu-id="c526e-148">Press F5 to run the application..</span></span>

   <span data-ttu-id="c526e-149">Uygulama hatasız oluşturması gerekir ve kesme noktasına isabet.</span><span class="sxs-lookup"><span data-stu-id="c526e-149">The application should build without error, and should hit the breakpoint.</span></span> <span data-ttu-id="c526e-150">Aynı zamanda "yanıt 42 sağlıyor." uygulama çıkış denetleme olanağına olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c526e-150">You should also be able to check that the application output "The answer is 42.".</span></span>
