---
title: Visual Studio 'da .NET Core ile bir konsol uygulaması oluşturma
description: Visual Studio kullanarak C# veya Visual Basic .NET Core konsol uygulaması oluşturmayı öğrenin.
author: BillWagner
ms.author: wiwagn
ms.date: 05/20/2020
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: 7dcd7957a9a160b3caf2692e9888c70a838bffc5
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84005030"
---
# <a name="tutorial-create-a-net-core-console-application-in-visual-studio-2019"></a><span data-ttu-id="f79b5-103">Öğretici: Visual Studio 2019 'de .NET Core konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="f79b5-103">Tutorial: Create a .NET Core console application in Visual Studio 2019</span></span>

<span data-ttu-id="f79b5-104">Bu öğreticide, Visual Studio 2019 ' de .NET Core konsol uygulaması oluşturma ve çalıştırma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="f79b5-104">This tutorial shows how to create and run a .NET Core console application in Visual Studio 2019.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="f79b5-105">Ön koşullar</span><span class="sxs-lookup"><span data-stu-id="f79b5-105">Prerequisites</span></span>

- <span data-ttu-id="f79b5-106">**.NET Core platformlar arası geliştirme** iş yükünün yüklü olduğu [Visual Studio 2019 sürüm 16,6 veya sonraki bir sürüm](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) .</span><span class="sxs-lookup"><span data-stu-id="f79b5-106">[Visual Studio 2019 version 16.6 or a later version](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) with the **.NET Core cross-platform development** workload installed.</span></span> <span data-ttu-id="f79b5-107">.NET Core 3,1 SDK 'Sı, bu iş yükünü seçtiğinizde otomatik olarak yüklenir.</span><span class="sxs-lookup"><span data-stu-id="f79b5-107">The .NET Core 3.1 SDK is automatically installed when you select this workload.</span></span>

  <span data-ttu-id="f79b5-108">Daha fazla bilgi için, [.NET Core SDK](../install/sdk.md?pivots=os-windows) makalesine [Visual Studio ile install](../install/sdk.md?pivots=os-windows#install-with-visual-studio) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="f79b5-108">For more information, see the [Install with Visual Studio](../install/sdk.md?pivots=os-windows#install-with-visual-studio) section on the [Install the .NET Core SDK](../install/sdk.md?pivots=os-windows) article.</span></span>

## <a name="create-the-app"></a><span data-ttu-id="f79b5-109">Uygulama oluşturma</span><span class="sxs-lookup"><span data-stu-id="f79b5-109">Create the app</span></span>

<!-- markdownlint-disable MD025 -->

1. <span data-ttu-id="f79b5-110">Visual Studio 2019 ' i açın.</span><span class="sxs-lookup"><span data-stu-id="f79b5-110">Open Visual Studio 2019.</span></span>

1. <span data-ttu-id="f79b5-111">"HelloWorld" adlı yeni bir .NET Core konsol uygulaması projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="f79b5-111">Create a new .NET Core console app project named "HelloWorld".</span></span>

   1. <span data-ttu-id="f79b5-112">Başlangıç sayfasında **Yeni proje oluştur**' u seçin.</span><span class="sxs-lookup"><span data-stu-id="f79b5-112">On the start page, choose **Create a new project**.</span></span>

      ![Visual Studio başlangıç sayfasında yeni bir proje oluştur düğmesi seçili](./media/with-visual-studio/start-window.png)

   1. <span data-ttu-id="f79b5-114">**Yeni proje oluştur** sayfasında, arama kutusuna **konsol** girin.</span><span class="sxs-lookup"><span data-stu-id="f79b5-114">On the **Create a new project** page, enter **console** in the search box.</span></span> <span data-ttu-id="f79b5-115">Ardından, dil listesinden **C#** veya **Visual Basic** ' yi seçin ve ardından platform listesinden **tüm platformlar** ' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="f79b5-115">Next, choose **C#** or **Visual Basic** from the language list, and then choose **All platforms** from the platform list.</span></span> <span data-ttu-id="f79b5-116">**Konsol uygulaması (.NET Core)** şablonunu seçin ve ardından **İleri**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="f79b5-116">Choose the **Console App (.NET Core)** template, and then choose **Next**.</span></span>

      ![Filtreler seçiliyken yeni bir proje penceresi oluştur](./media/with-visual-studio/create-new-project.png)

      > [!TIP]
      > <span data-ttu-id="f79b5-118">.NET Core şablonlarını görmüyorsanız, muhtemelen gerekli iş yükünün eksik olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="f79b5-118">If you don't see the .NET Core templates, you're probably missing the required workload.</span></span> <span data-ttu-id="f79b5-119">**Aradığınızı bulmuyor musunuz?** iletisi altında, **daha fazla araç ve özellik yüklemeyi** seçin bağlantısına tıklayın.</span><span class="sxs-lookup"><span data-stu-id="f79b5-119">Under the **Not finding what you're looking for?** message, choose the **Install more tools and features** link.</span></span> <span data-ttu-id="f79b5-120">Visual Studio Yükleyicisi açılır.</span><span class="sxs-lookup"><span data-stu-id="f79b5-120">The Visual Studio Installer opens.</span></span> <span data-ttu-id="f79b5-121">**.NET Core platformlar arası geliştirme** iş yükünün yüklü olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="f79b5-121">Make sure you have the **.NET Core cross-platform development** workload installed.</span></span>

   1. <span data-ttu-id="f79b5-122">**Yeni projenizi yapılandırın** sayfasında, **Proje adı** kutusuna **HelloWorld** girin.</span><span class="sxs-lookup"><span data-stu-id="f79b5-122">On the **Configure your new project** page,  enter **HelloWorld** in the **Project name** box.</span></span> <span data-ttu-id="f79b5-123">Ardından **Oluştur**’u seçin.</span><span class="sxs-lookup"><span data-stu-id="f79b5-123">Then choose **Create**.</span></span>

      ![Yeni proje pencerenizi proje adı, konum ve çözüm adı alanlarıyla yapılandırın](./media/with-visual-studio/configure-new-project.png)

   <span data-ttu-id="f79b5-125">.NET Core konsol uygulaması şablonu, `Program` `Main` bağımsız değişken olarak bir dizi alan tek bir yöntemle bir sınıfını tanımlar <xref:System.String> .</span><span class="sxs-lookup"><span data-stu-id="f79b5-125">The Console Application template for .NET Core defines a class, `Program`, with a single method, `Main`, that takes a <xref:System.String> array as an argument.</span></span> <span data-ttu-id="f79b5-126">`Main`uygulama giriş noktası, uygulamayı başlattığında çalışma zamanı tarafından otomatik olarak çağrılan yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="f79b5-126">`Main` is the application entry point, the method that's called automatically by the runtime when it launches the application.</span></span> <span data-ttu-id="f79b5-127">Uygulama başlatıldığında sağlanan herhangi bir komut satırı bağımsız değişkeni, *args* dizisinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f79b5-127">Any command-line arguments supplied when the application is launched are available in the *args* array.</span></span>

   <span data-ttu-id="f79b5-128">Kullanmak istediğiniz dil gösterilmiyorsa sayfanın en üstündeki dil seçicisini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="f79b5-128">If the language you want to use is not shown, change the language selector at the top of the page.</span></span>

   ```csharp
   using System;

   namespace HelloWorld
   {
       class Program
       {
           static void Main(string[] args)
           {
               Console.WriteLine("Hello World!");
           }
       }
   }
   ```

   ```vb
   Imports System

   Module Program
       Sub Main(args As String())
           Console.WriteLine("Hello World!")
       End Sub
   End Module
   ```

   <span data-ttu-id="f79b5-129">Şablon basit bir "Merhaba Dünya" uygulaması oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f79b5-129">The template creates a simple "Hello World" application.</span></span> <span data-ttu-id="f79b5-130"><xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType>"Merhaba Dünya!" öğesini göstermek için yöntemini çağırır</span><span class="sxs-lookup"><span data-stu-id="f79b5-130">It calls the <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> method to display "Hello World!"</span></span> <span data-ttu-id="f79b5-131">Konsol penceresinde.</span><span class="sxs-lookup"><span data-stu-id="f79b5-131">in the console window.</span></span>

## <a name="run-the-app"></a><span data-ttu-id="f79b5-132">Uygulamayı çalıştırma</span><span class="sxs-lookup"><span data-stu-id="f79b5-132">Run the app</span></span>

1. <span data-ttu-id="f79b5-133">Programı çalıştırmak için araç çubuğunda **HelloWorld** ' ı seçin veya **F5**tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="f79b5-133">To run the program, choose **HelloWorld** on the toolbar, or press **F5**.</span></span>

   ![HelloWorld Run düğmesinin seçili olduğu Visual Studio araç çubuğu](./media/with-visual-studio/run-program.png)

   <span data-ttu-id="f79b5-135">Bir konsol penceresi "Merhaba Dünya!" metniyle açılıyor</span><span class="sxs-lookup"><span data-stu-id="f79b5-135">A console window opens with the text "Hello World!"</span></span> <span data-ttu-id="f79b5-136">ekranda ve bazı Visual Studio hata ayıklama bilgilerinde yazdırılır.</span><span class="sxs-lookup"><span data-stu-id="f79b5-136">printed on the screen and some Visual Studio debug information.</span></span>

   ![Merhaba Dünya devam etmek için herhangi bir tuşa basarak konsol penceresi](./media/with-visual-studio/hello-world-console.png)

1. <span data-ttu-id="f79b5-138">Konsol penceresini kapatmak için herhangi bir tuşa basın.</span><span class="sxs-lookup"><span data-stu-id="f79b5-138">Press any key to close the console window.</span></span>

## <a name="enhance-the-app"></a><span data-ttu-id="f79b5-139">Uygulamayı geliştirin</span><span class="sxs-lookup"><span data-stu-id="f79b5-139">Enhance the app</span></span>

<span data-ttu-id="f79b5-140">Kullanıcıya adını istemek ve Tarih ve saat ile birlikte göstermek için uygulamayı geliştirin.</span><span class="sxs-lookup"><span data-stu-id="f79b5-140">Enhance the application to prompt the user for their name and display it along with the date and time.</span></span> <span data-ttu-id="f79b5-141">Aşağıdaki yönergeler uygulamayı değiştirip yeniden çalıştırır:</span><span class="sxs-lookup"><span data-stu-id="f79b5-141">The following instructions modify the app and run it again:</span></span>

1. <span data-ttu-id="f79b5-142">`Main`Aşağıdaki kod ile Şu anda yalnızca çağıran satırı olan yönteminin içeriğini değiştirin `Console.WriteLine` :</span><span class="sxs-lookup"><span data-stu-id="f79b5-142">Replace the contents of the `Main` method, which is currently just the line that calls `Console.WriteLine`, with the following code:</span></span>

   [!code-csharp[GettingStarted#1](~/samples/snippets/csharp/getting_started/with_visual_studio/HelloWorld.cs#1)]

   [!code-vb[GettingStarted#1](~/samples/snippets/core/tutorials/vb-with-visual-studio/Program.vb#1)]

   <span data-ttu-id="f79b5-143">Bu kod "adınız nedir?" görüntüler</span><span class="sxs-lookup"><span data-stu-id="f79b5-143">This code displays "What is your name?"</span></span> <span data-ttu-id="f79b5-144">Konsol penceresinde ve ardından ENTER tuşuna basarak Kullanıcı bir dize girene kadar bekler.</span><span class="sxs-lookup"><span data-stu-id="f79b5-144">in the console window and waits until the user enters a string followed by the Enter key.</span></span> <span data-ttu-id="f79b5-145">Bu dizeyi adlı bir değişkende depolar `name` .</span><span class="sxs-lookup"><span data-stu-id="f79b5-145">It stores this string in a variable named `name`.</span></span> <span data-ttu-id="f79b5-146">Ayrıca <xref:System.DateTime.Now?displayProperty=nameWithType> , geçerli yerel saati içeren özelliğinin değerini alır ve bunu adlı bir değişkene `date` ( `currentDate` Visual Basic) atar.</span><span class="sxs-lookup"><span data-stu-id="f79b5-146">It also retrieves the value of the <xref:System.DateTime.Now?displayProperty=nameWithType> property, which contains the current local time, and assigns it to a variable named `date` (`currentDate` in Visual Basic).</span></span> <span data-ttu-id="f79b5-147">Son olarak, bu değerleri konsol penceresinde görüntüler.</span><span class="sxs-lookup"><span data-stu-id="f79b5-147">Finally, it displays these values in the console window.</span></span>

   <span data-ttu-id="f79b5-148">`\n`( `vbCrLf` Visual Basic), bir yeni satır karakterini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="f79b5-148">The `\n` (`vbCrLf` in Visual Basic) represents a newline character.</span></span>

   <span data-ttu-id="f79b5-149">`$`Bir dizenin önünde dolar işareti (), değişken adları gibi ifadeleri dizedeki küme ayraçları içine koymanıza imkan tanır.</span><span class="sxs-lookup"><span data-stu-id="f79b5-149">The dollar sign (`$`) in front of a string lets you put expressions such as variable names in curly braces in the string.</span></span> <span data-ttu-id="f79b5-150">İfade değeri, ifadenin yerine dizeye eklenir.</span><span class="sxs-lookup"><span data-stu-id="f79b5-150">The expression value is inserted into the string in place of the expression.</span></span> <span data-ttu-id="f79b5-151">Bu söz dizimi, [enterpolasyonlu dizeler](../../csharp/language-reference/tokens/interpolated.md)olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="f79b5-151">This syntax is referred to as [interpolated strings](../../csharp/language-reference/tokens/interpolated.md).</span></span>

1. <span data-ttu-id="f79b5-152">Programı çalıştırmak için araç çubuğunda **HelloWorld** ' ı seçin veya **F5**tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="f79b5-152">To run the program, choose **HelloWorld** on the toolbar, or press **F5**.</span></span>

1. <span data-ttu-id="f79b5-153">Bir ad girip **ENTER** tuşuna basarak istemi yanıtlayın.</span><span class="sxs-lookup"><span data-stu-id="f79b5-153">Respond to the prompt by entering a name and pressing the **Enter** key.</span></span>

   ![Değiştirilen program çıkışıyla konsol penceresi](./media/with-visual-studio/hello-world-update.png)

1. <span data-ttu-id="f79b5-155">Konsol penceresini kapatmak için herhangi bir tuşa basın.</span><span class="sxs-lookup"><span data-stu-id="f79b5-155">Press any key to close the console window.</span></span>

## <a name="next-steps"></a><span data-ttu-id="f79b5-156">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="f79b5-156">Next steps</span></span>

<span data-ttu-id="f79b5-157">Bu öğreticide, bir .NET Core uygulaması oluşturdunuz.</span><span class="sxs-lookup"><span data-stu-id="f79b5-157">In this tutorial, you created a .NET Core application.</span></span> <span data-ttu-id="f79b5-158">Sonraki öğreticide, uygulamada hata ayıklaması yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f79b5-158">In the next tutorial, you debug the app.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="f79b5-159">Visual Studio 'da bir .NET Core konsol uygulamasında hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="f79b5-159">Debug a .NET Core console application in Visual Studio</span></span>](debugging-with-visual-studio.md)
