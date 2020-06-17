---
title: Visual Studio kullanarak bir .NET Core konsol uygulaması oluşturma
description: Visual Studio kullanarak C# veya Visual Basic .NET Core konsol uygulaması oluşturmayı öğrenin.
ms.date: 06/08/2020
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: 3c8fc7c4702b786c05e14397dc36d994c77e114d
ms.sourcegitcommit: 1eae045421d9ea2bfc82aaccfa5b1ff1b8c9e0e4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/16/2020
ms.locfileid: "84811648"
---
# <a name="tutorial-create-a-net-core-console-application-using-visual-studio"></a><span data-ttu-id="f9746-103">Öğretici: Visual Studio kullanarak .NET Core konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="f9746-103">Tutorial: Create a .NET Core console application using Visual Studio</span></span>

<span data-ttu-id="f9746-104">Bu öğreticide, Visual Studio 2019 ' de .NET Core konsol uygulaması oluşturma ve çalıştırma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="f9746-104">This tutorial shows how to create and run a .NET Core console application in Visual Studio 2019.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="f9746-105">Ön koşullar</span><span class="sxs-lookup"><span data-stu-id="f9746-105">Prerequisites</span></span>

- <span data-ttu-id="f9746-106">**.NET Core platformlar arası geliştirme** iş yükünün yüklü olduğu [Visual Studio 2019 sürüm 16,6 veya sonraki bir sürüm](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) .</span><span class="sxs-lookup"><span data-stu-id="f9746-106">[Visual Studio 2019 version 16.6 or a later version](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) with the **.NET Core cross-platform development** workload installed.</span></span> <span data-ttu-id="f9746-107">.NET Core 3,1 SDK 'Sı, bu iş yükünü seçtiğinizde otomatik olarak yüklenir.</span><span class="sxs-lookup"><span data-stu-id="f9746-107">The .NET Core 3.1 SDK is automatically installed when you select this workload.</span></span>

  <span data-ttu-id="f9746-108">Daha fazla bilgi için bkz. [Visual Studio ile .NET Core SDK yüklemesi](../install/sdk.md?pivots=os-windows#install-with-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="f9746-108">For more information, see [Install the .NET Core SDK with Visual Studio](../install/sdk.md?pivots=os-windows#install-with-visual-studio).</span></span>

## <a name="create-the-app"></a><span data-ttu-id="f9746-109">Uygulama oluşturma</span><span class="sxs-lookup"><span data-stu-id="f9746-109">Create the app</span></span>

<span data-ttu-id="f9746-110">"HelloWorld" adlı bir .NET Core konsol uygulaması projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="f9746-110">Create a .NET Core console app project named "HelloWorld".</span></span>

1. <span data-ttu-id="f9746-111">Visual Studio 2019 ' i başlatın.</span><span class="sxs-lookup"><span data-stu-id="f9746-111">Start Visual Studio 2019.</span></span>

1. <span data-ttu-id="f9746-112">Başlangıç sayfasında **Yeni proje oluştur**' u seçin.</span><span class="sxs-lookup"><span data-stu-id="f9746-112">On the start page, choose **Create a new project**.</span></span>

   ![Visual Studio başlangıç sayfasında yeni bir proje oluştur düğmesi seçili](./media/with-visual-studio/start-window.png)

1. <span data-ttu-id="f9746-114">**Yeni proje oluştur** sayfasında, arama kutusuna **konsol** girin.</span><span class="sxs-lookup"><span data-stu-id="f9746-114">On the **Create a new project** page, enter **console** in the search box.</span></span> <span data-ttu-id="f9746-115">Ardından, dil listesinden **C#** veya **Visual Basic** ' yi seçin ve ardından platform listesinden **tüm platformlar** ' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="f9746-115">Next, choose **C#** or **Visual Basic** from the language list, and then choose **All platforms** from the platform list.</span></span> <span data-ttu-id="f9746-116">**Konsol uygulaması (.NET Core)** şablonunu seçin ve ardından **İleri**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="f9746-116">Choose the **Console App (.NET Core)** template, and then choose **Next**.</span></span>

   ![Filtreler seçiliyken yeni bir proje penceresi oluştur](./media/with-visual-studio/create-new-project.png)

   > [!TIP]
   > <span data-ttu-id="f9746-118">.NET Core şablonlarını görmüyorsanız, muhtemelen gerekli iş yükünün eksik olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="f9746-118">If you don't see the .NET Core templates, you're probably missing the required workload.</span></span> <span data-ttu-id="f9746-119">**Aradığınızı bulmuyor musunuz?** iletisi altında, **daha fazla araç ve özellik yüklemeyi** seçin bağlantısına tıklayın.</span><span class="sxs-lookup"><span data-stu-id="f9746-119">Under the **Not finding what you're looking for?** message, choose the **Install more tools and features** link.</span></span> <span data-ttu-id="f9746-120">Visual Studio Yükleyicisi açılır.</span><span class="sxs-lookup"><span data-stu-id="f9746-120">The Visual Studio Installer opens.</span></span> <span data-ttu-id="f9746-121">**.NET Core platformlar arası geliştirme** iş yükünün yüklü olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="f9746-121">Make sure you have the **.NET Core cross-platform development** workload installed.</span></span>

1. <span data-ttu-id="f9746-122">**Yeni projenizi yapılandırın** iletişim kutusunda, **Proje adı** kutusuna **HelloWorld** yazın.</span><span class="sxs-lookup"><span data-stu-id="f9746-122">In the **Configure your new project** dialog,  enter **HelloWorld** in the **Project name** box.</span></span> <span data-ttu-id="f9746-123">Ardından **Oluştur**’u seçin.</span><span class="sxs-lookup"><span data-stu-id="f9746-123">Then choose **Create**.</span></span>

   ![Yeni proje pencerenizi proje adı, konum ve çözüm adı alanlarıyla yapılandırın](./media/with-visual-studio/configure-new-project.png)

<span data-ttu-id="f9746-125">Şablon basit bir "Merhaba Dünya" uygulaması oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f9746-125">The template creates a simple "Hello World" application.</span></span> <span data-ttu-id="f9746-126"><xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType>"Merhaba Dünya!" öğesini göstermek için yöntemini çağırır</span><span class="sxs-lookup"><span data-stu-id="f9746-126">It calls the <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> method to display "Hello World!"</span></span> <span data-ttu-id="f9746-127">Konsol penceresinde.</span><span class="sxs-lookup"><span data-stu-id="f9746-127">in the console window.</span></span>

<span data-ttu-id="f9746-128">Şablon kodu, `Program` `Main` bağımsız değişken olarak bir diziyi alan tek bir yöntemi olan sınıfını tanımlar <xref:System.String> :</span><span class="sxs-lookup"><span data-stu-id="f9746-128">The template code defines a class, `Program`, with a single method, `Main`, that takes a <xref:System.String> array as an argument:</span></span>

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

<span data-ttu-id="f9746-129">`Main`uygulama giriş noktası, uygulamayı başlattığında çalışma zamanı tarafından otomatik olarak çağrılan yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="f9746-129">`Main` is the application entry point, the method that's called automatically by the runtime when it launches the application.</span></span> <span data-ttu-id="f9746-130">Uygulama başlatıldığında sağlanan herhangi bir komut satırı bağımsız değişkeni, *args* dizisinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f9746-130">Any command-line arguments supplied when the application is launched are available in the *args* array.</span></span>

<span data-ttu-id="f9746-131">Kullanmak istediğiniz dil gösterilmiyorsa sayfanın en üstündeki dil seçicisini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="f9746-131">If the language you want to use is not shown, change the language selector at the top of the page.</span></span>

## <a name="run-the-app"></a><span data-ttu-id="f9746-132">Uygulamayı çalıştırma</span><span class="sxs-lookup"><span data-stu-id="f9746-132">Run the app</span></span>

1. <span data-ttu-id="f9746-133"><kbd>Shift</kbd> + Programı hata ayıklamadan çalıştırmak için SHIFT<kbd>F5</kbd> tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="f9746-133">Press <kbd>Shift</kbd>+<kbd>F5</kbd> to run the program without debugging.</span></span>

   <span data-ttu-id="f9746-134">Bir konsol penceresi "Merhaba Dünya!" metniyle açılıyor</span><span class="sxs-lookup"><span data-stu-id="f9746-134">A console window opens with the text "Hello World!"</span></span> <span data-ttu-id="f9746-135">ekranda ve bazı Visual Studio hata ayıklama bilgilerinde yazdırılır.</span><span class="sxs-lookup"><span data-stu-id="f9746-135">printed on the screen and some Visual Studio debug information.</span></span>

   ![Merhaba Dünya devam etmek için herhangi bir tuşa basarak konsol penceresi](./media/with-visual-studio/hello-world-console.png)

1. <span data-ttu-id="f9746-137">Konsol penceresini kapatmak için herhangi bir tuşa basın.</span><span class="sxs-lookup"><span data-stu-id="f9746-137">Press any key to close the console window.</span></span>

## <a name="enhance-the-app"></a><span data-ttu-id="f9746-138">Uygulamayı geliştirin</span><span class="sxs-lookup"><span data-stu-id="f9746-138">Enhance the app</span></span>

<span data-ttu-id="f9746-139">Kullanıcıya adını istemek ve Tarih ve saat ile birlikte göstermek için uygulamayı geliştirin.</span><span class="sxs-lookup"><span data-stu-id="f9746-139">Enhance the application to prompt the user for their name and display it along with the date and time.</span></span>

1. <span data-ttu-id="f9746-140">*Program.cs* veya *program. vb*' de, yönteminin içeriğini, `Main` çağıran satırı, `Console.WriteLine` aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="f9746-140">In *Program.cs* or *Program.vb*, replace the contents of the `Main` method, which is the line that calls `Console.WriteLine`, with the following code:</span></span>

   :::code language="csharp" source="./snippets/with-visual-studio/csharp/Program.cs" id="MainMethod":::
   :::code language="vb" source="./snippets/with-visual-studio/vb/Program.vb" id="MainMethod":::

   <span data-ttu-id="f9746-141">Bu kod "adınız nedir?" görüntüler</span><span class="sxs-lookup"><span data-stu-id="f9746-141">This code displays "What is your name?"</span></span> <span data-ttu-id="f9746-142">Konsol penceresinde ve ardından <kbd>ENTER</kbd> tuşuna basarak Kullanıcı bir dize girene kadar bekler.</span><span class="sxs-lookup"><span data-stu-id="f9746-142">in the console window and waits until the user enters a string followed by the <kbd>Enter</kbd> key.</span></span> <span data-ttu-id="f9746-143">Bu dizeyi adlı bir değişkende depolar `name` .</span><span class="sxs-lookup"><span data-stu-id="f9746-143">It stores this string in a variable named `name`.</span></span> <span data-ttu-id="f9746-144">Ayrıca <xref:System.DateTime.Now?displayProperty=nameWithType> , geçerli yerel saati içeren özelliğinin değerini alır ve bunu adlı bir değişkene `date` ( `currentDate` Visual Basic) atar.</span><span class="sxs-lookup"><span data-stu-id="f9746-144">It also retrieves the value of the <xref:System.DateTime.Now?displayProperty=nameWithType> property, which contains the current local time, and assigns it to a variable named `date` (`currentDate` in Visual Basic).</span></span> <span data-ttu-id="f9746-145">Son olarak, bu değerleri konsol penceresinde görüntüler.</span><span class="sxs-lookup"><span data-stu-id="f9746-145">Finally, it displays these values in the console window.</span></span>

   <span data-ttu-id="f9746-146">`\n`( `vbCrLf` Visual Basic), bir yeni satır karakterini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="f9746-146">The `\n` (`vbCrLf` in Visual Basic) represents a newline character.</span></span>

   <span data-ttu-id="f9746-147">`$`Bir dizenin önünde dolar işareti (), değişken adları gibi ifadeleri dizedeki küme ayraçları içine koymanıza imkan tanır.</span><span class="sxs-lookup"><span data-stu-id="f9746-147">The dollar sign (`$`) in front of a string lets you put expressions such as variable names in curly braces in the string.</span></span> <span data-ttu-id="f9746-148">İfade değeri, ifadenin yerine dizeye eklenir.</span><span class="sxs-lookup"><span data-stu-id="f9746-148">The expression value is inserted into the string in place of the expression.</span></span> <span data-ttu-id="f9746-149">Bu söz dizimi, [enterpolasyonlu dizeler](../../csharp/language-reference/tokens/interpolated.md)olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="f9746-149">This syntax is referred to as [interpolated strings](../../csharp/language-reference/tokens/interpolated.md).</span></span>

1. <span data-ttu-id="f9746-150"><kbd>Shift</kbd> + Programı hata ayıklamadan çalıştırmak için SHIFT<kbd>F5</kbd> tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="f9746-150">Press <kbd>Shift</kbd>+<kbd>F5</kbd> to run the program without debugging.</span></span>

1. <span data-ttu-id="f9746-151">Bir ad girip <kbd>ENTER</kbd> tuşuna basarak istemi yanıtlayın.</span><span class="sxs-lookup"><span data-stu-id="f9746-151">Respond to the prompt by entering a name and pressing the <kbd>Enter</kbd> key.</span></span>

   ![Değiştirilen program çıkışıyla konsol penceresi](./media/with-visual-studio/hello-world-update.png)

1. <span data-ttu-id="f9746-153">Konsol penceresini kapatmak için herhangi bir tuşa basın.</span><span class="sxs-lookup"><span data-stu-id="f9746-153">Press any key to close the console window.</span></span>

## <a name="next-steps"></a><span data-ttu-id="f9746-154">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="f9746-154">Next steps</span></span>

<span data-ttu-id="f9746-155">Bu öğreticide, bir .NET Core konsol uygulaması oluşturdunuz.</span><span class="sxs-lookup"><span data-stu-id="f9746-155">In this tutorial, you created a .NET Core console application.</span></span> <span data-ttu-id="f9746-156">Sonraki öğreticide, uygulamada hata ayıklaması yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f9746-156">In the next tutorial, you debug the app.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="f9746-157">Visual Studio 'da bir .NET Core konsol uygulamasında hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="f9746-157">Debug a .NET Core console application in Visual Studio</span></span>](debugging-with-visual-studio.md)
