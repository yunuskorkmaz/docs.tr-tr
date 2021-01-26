---
title: Visual Studio kullanarak bir .NET konsol uygulaması oluşturma
description: Visual Studio kullanarak C# veya Visual Basic .NET konsol uygulaması oluşturmayı öğrenin.
ms.date: 06/08/2020
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: a3a27c1baaab135108ef475d77c35d607c45fa82
ms.sourcegitcommit: 4d5e25a46aa7cd0d29b4b9227b92987354d444c4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/26/2021
ms.locfileid: "98794798"
---
# <a name="tutorial-create-a-net-console-application-using-visual-studio"></a><span data-ttu-id="2f7d4-103">Öğretici: Visual Studio kullanarak bir .NET konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="2f7d4-103">Tutorial: Create a .NET console application using Visual Studio</span></span>

<span data-ttu-id="2f7d4-104">Bu öğreticide, Visual Studio 2019 ' de bir .NET konsol uygulamasının nasıl oluşturulacağı ve çalıştırılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="2f7d4-104">This tutorial shows how to create and run a .NET console application in Visual Studio 2019.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="2f7d4-105">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="2f7d4-105">Prerequisites</span></span>

- <span data-ttu-id="2f7d4-106">**.NET Core platformlar arası geliştirme** iş yükünün yüklü olduğu [Visual Studio 2019 sürüm 16,8 veya sonraki bir sürüm](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) .</span><span class="sxs-lookup"><span data-stu-id="2f7d4-106">[Visual Studio 2019 version 16.8 or a later version](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) with the **.NET Core cross-platform development** workload installed.</span></span> <span data-ttu-id="2f7d4-107">.NET 5,0 SDK, bu iş yükünü seçtiğinizde otomatik olarak yüklenir.</span><span class="sxs-lookup"><span data-stu-id="2f7d4-107">The .NET 5.0 SDK is automatically installed when you select this workload.</span></span>

  <span data-ttu-id="2f7d4-108">Daha fazla bilgi için bkz. [Visual Studio ile .NET SDK 'Yı yükler](../install/windows.md#install-with-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="2f7d4-108">For more information, see [Install the .NET SDK with Visual Studio](../install/windows.md#install-with-visual-studio).</span></span>

## <a name="create-the-app"></a><span data-ttu-id="2f7d4-109">Uygulama oluşturma</span><span class="sxs-lookup"><span data-stu-id="2f7d4-109">Create the app</span></span>

<span data-ttu-id="2f7d4-110">"HelloWorld" adlı bir .NET konsol uygulaması projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="2f7d4-110">Create a .NET console app project named "HelloWorld".</span></span>

1. <span data-ttu-id="2f7d4-111">Visual Studio 2019’u başlatın.</span><span class="sxs-lookup"><span data-stu-id="2f7d4-111">Start Visual Studio 2019.</span></span>

1. <span data-ttu-id="2f7d4-112">**Araçlar**  >  **Seçenekler**  >  **ortam**  >  **Önizleme özellikleri**' ni seçin ve ardından **Yeni projede tüm .NET Core şablonlarını göster ' i seçin (yeniden başlatma gerektirir)**.</span><span class="sxs-lookup"><span data-stu-id="2f7d4-112">Select **Tools** > **Options** > **Environment** > **Preview features**, and then select **Show all .NET Core templates in the New project (requires restart)**.</span></span>

   :::image type="content" source="media/with-visual-studio/dotnet-options.png" alt-text="Tüm .NET şablonları seçeneğini göster":::

1. <span data-ttu-id="2f7d4-114">Visual Studio 'Yu kapatın ve yeniden açın.</span><span class="sxs-lookup"><span data-stu-id="2f7d4-114">Close and reopen Visual Studio.</span></span>

1. <span data-ttu-id="2f7d4-115">Başlangıç sayfasında **Yeni proje oluştur**' u seçin.</span><span class="sxs-lookup"><span data-stu-id="2f7d4-115">On the start page, choose **Create a new project**.</span></span>

   :::image type="content" source="./media/with-visual-studio/start-window.png" alt-text="Visual Studio başlangıç sayfasında yeni bir proje oluştur düğmesi seçili":::

1. <span data-ttu-id="2f7d4-117">**Yeni proje oluştur** sayfasında, arama kutusuna **konsol** girin.</span><span class="sxs-lookup"><span data-stu-id="2f7d4-117">On the **Create a new project** page, enter **console** in the search box.</span></span> <span data-ttu-id="2f7d4-118">Ardından, dil listesinden **C#** veya **Visual Basic** ' yi seçin ve ardından platform listesinden **tüm platformlar** ' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="2f7d4-118">Next, choose **C#** or **Visual Basic** from the language list, and then choose **All platforms** from the platform list.</span></span> <span data-ttu-id="2f7d4-119">**Konsol uygulaması** şablonunu seçin ve ardından **İleri**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="2f7d4-119">Choose the **Console Application** template, and then choose **Next**.</span></span>

   :::image type="content" source="./media/with-visual-studio/create-new-project.png" alt-text="Filtreler seçiliyken yeni bir proje penceresi oluştur":::

   > [!TIP]
   > <span data-ttu-id="2f7d4-121">.NET şablonlarını görmüyorsanız, muhtemelen gerekli iş yükü eksik olabilir.</span><span class="sxs-lookup"><span data-stu-id="2f7d4-121">If you don't see the .NET templates, you're probably missing the required workload.</span></span> <span data-ttu-id="2f7d4-122">**Aradığınızı bulmuyor musunuz?** iletisi altında, **daha fazla araç ve özellik yüklemeyi** seçin bağlantısına tıklayın.</span><span class="sxs-lookup"><span data-stu-id="2f7d4-122">Under the **Not finding what you're looking for?** message, choose the **Install more tools and features** link.</span></span> <span data-ttu-id="2f7d4-123">Visual Studio Yükleyicisi açılır.</span><span class="sxs-lookup"><span data-stu-id="2f7d4-123">The Visual Studio Installer opens.</span></span> <span data-ttu-id="2f7d4-124">**.NET Core platformlar arası geliştirme** iş yükünün yüklü olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="2f7d4-124">Make sure you have the **.NET Core cross-platform development** workload installed.</span></span>

1. <span data-ttu-id="2f7d4-125">**Yeni projenizi yapılandırın** iletişim kutusunda, **Proje adı** kutusuna **HelloWorld** yazın.</span><span class="sxs-lookup"><span data-stu-id="2f7d4-125">In the **Configure your new project** dialog,  enter **HelloWorld** in the **Project name** box.</span></span> <span data-ttu-id="2f7d4-126">Ardından **Oluştur**’u seçin.</span><span class="sxs-lookup"><span data-stu-id="2f7d4-126">Then choose **Create**.</span></span>

   :::image type="content" source="./media/with-visual-studio/configure-new-project.png" alt-text="Yeni proje pencerenizi proje adı, konum ve çözüm adı alanlarıyla yapılandırın":::

1. <span data-ttu-id="2f7d4-128">**Ek bilgi** iletişim kutusunda **.NET 5,0 (geçerli)** öğesini seçin ve ardından **Oluştur**' u seçin.</span><span class="sxs-lookup"><span data-stu-id="2f7d4-128">In the **Additional information** dialog, select **.NET 5.0 (Current)**, and then select **Create**.</span></span>

   :::image type="content" source="media/with-visual-studio/additional-info.png" alt-text="Ek bilgi iletişim kutusu":::

<span data-ttu-id="2f7d4-130">Şablon basit bir "Merhaba Dünya" uygulaması oluşturur.</span><span class="sxs-lookup"><span data-stu-id="2f7d4-130">The template creates a simple "Hello World" application.</span></span> <span data-ttu-id="2f7d4-131"><xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType>"Merhaba Dünya!" öğesini göstermek için yöntemini çağırır</span><span class="sxs-lookup"><span data-stu-id="2f7d4-131">It calls the <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> method to display "Hello World!"</span></span> <span data-ttu-id="2f7d4-132">Konsol penceresinde.</span><span class="sxs-lookup"><span data-stu-id="2f7d4-132">in the console window.</span></span>

<span data-ttu-id="2f7d4-133">Şablon kodu, `Program` `Main` bağımsız değişken olarak bir diziyi alan tek bir yöntemi olan sınıfını tanımlar <xref:System.String> :</span><span class="sxs-lookup"><span data-stu-id="2f7d4-133">The template code defines a class, `Program`, with a single method, `Main`, that takes a <xref:System.String> array as an argument:</span></span>

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

<span data-ttu-id="2f7d4-134">`Main` uygulama giriş noktası, uygulamayı başlattığında çalışma zamanı tarafından otomatik olarak çağrılan yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="2f7d4-134">`Main` is the application entry point, the method that's called automatically by the runtime when it launches the application.</span></span> <span data-ttu-id="2f7d4-135">Uygulama başlatıldığında sağlanan herhangi bir komut satırı bağımsız değişkeni, *args* dizisinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="2f7d4-135">Any command-line arguments supplied when the application is launched are available in the *args* array.</span></span>

<span data-ttu-id="2f7d4-136">Kullanmak istediğiniz dil gösterilmiyorsa sayfanın en üstündeki dil seçicisini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="2f7d4-136">If the language you want to use is not shown, change the language selector at the top of the page.</span></span>

## <a name="run-the-app"></a><span data-ttu-id="2f7d4-137">Uygulamayı çalıştırma</span><span class="sxs-lookup"><span data-stu-id="2f7d4-137">Run the app</span></span>

1. <span data-ttu-id="2f7d4-138"><kbd></kbd> + Programı hata ayıklamadan çalıştırmak için CTRL<kbd>F5</kbd> tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="2f7d4-138">Press <kbd>Ctrl</kbd>+<kbd>F5</kbd> to run the program without debugging.</span></span>

   <span data-ttu-id="2f7d4-139">Bir konsol penceresi "Merhaba Dünya!" metniyle açılıyor</span><span class="sxs-lookup"><span data-stu-id="2f7d4-139">A console window opens with the text "Hello World!"</span></span> <span data-ttu-id="2f7d4-140">ekranda yazdırılır.</span><span class="sxs-lookup"><span data-stu-id="2f7d4-140">printed on the screen.</span></span>

   :::image type="content" source="./media/with-visual-studio/hello-world-console.png" alt-text="Merhaba Dünya devam etmek için herhangi bir tuşa basarak konsol penceresi":::

1. <span data-ttu-id="2f7d4-142">Konsol penceresini kapatmak için herhangi bir tuşa basın.</span><span class="sxs-lookup"><span data-stu-id="2f7d4-142">Press any key to close the console window.</span></span>

## <a name="enhance-the-app"></a><span data-ttu-id="2f7d4-143">Uygulamayı geliştirin</span><span class="sxs-lookup"><span data-stu-id="2f7d4-143">Enhance the app</span></span>

<span data-ttu-id="2f7d4-144">Kullanıcıya adını istemek ve Tarih ve saat ile birlikte göstermek için uygulamayı geliştirin.</span><span class="sxs-lookup"><span data-stu-id="2f7d4-144">Enhance the application to prompt the user for their name and display it along with the date and time.</span></span>

1. <span data-ttu-id="2f7d4-145">*Program.cs* veya *program. vb*' de, yönteminin içeriğini, `Main` çağıran satırı, `Console.WriteLine` aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="2f7d4-145">In *Program.cs* or *Program.vb*, replace the contents of the `Main` method, which is the line that calls `Console.WriteLine`, with the following code:</span></span>

   :::code language="csharp" source="./snippets/with-visual-studio/csharp/Program.cs" id="MainMethod":::
   :::code language="vb" source="./snippets/with-visual-studio/vb/Program.vb" id="MainMethod":::

   <span data-ttu-id="2f7d4-146">Bu kod, konsol penceresinde bir istem görüntüler ve ardından <kbd>ENTER</kbd> tuşuna basarak Kullanıcı bir dize girene kadar bekler.</span><span class="sxs-lookup"><span data-stu-id="2f7d4-146">This code displays a prompt in the console window and waits until the user enters a string followed by the <kbd>Enter</kbd> key.</span></span> <span data-ttu-id="2f7d4-147">Bu dizeyi adlı bir değişkende depolar `name` .</span><span class="sxs-lookup"><span data-stu-id="2f7d4-147">It stores this string in a variable named `name`.</span></span> <span data-ttu-id="2f7d4-148">Ayrıca <xref:System.DateTime.Now?displayProperty=nameWithType> , geçerli yerel saati içeren özelliğinin değerini alır ve bunu adlı bir değişkene `date` ( `currentDate` Visual Basic) atar.</span><span class="sxs-lookup"><span data-stu-id="2f7d4-148">It also retrieves the value of the <xref:System.DateTime.Now?displayProperty=nameWithType> property, which contains the current local time, and assigns it to a variable named `date` (`currentDate` in Visual Basic).</span></span> <span data-ttu-id="2f7d4-149">Bu değerleri konsol penceresinde görüntüler.</span><span class="sxs-lookup"><span data-stu-id="2f7d4-149">And it displays these values in the console window.</span></span> <span data-ttu-id="2f7d4-150">Son olarak, konsol penceresinde bir istem görüntüler ve <xref:System.Console.ReadKey(System.Boolean)?displayProperty=nameWithType> Kullanıcı girişini beklemek için yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="2f7d4-150">Finally, it displays a prompt in the console window and calls the <xref:System.Console.ReadKey(System.Boolean)?displayProperty=nameWithType> method to wait for user input.</span></span>

   <span data-ttu-id="2f7d4-151">`\n`(Veya `vbCrLf` Visual Basic kodundaki) bir yeni satır karakterini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="2f7d4-151">The `\n` (or `vbCrLf` in the Visual Basic code) represents a newline character.</span></span>

   <span data-ttu-id="2f7d4-152">`$`Bir dizenin önünde dolar işareti (), değişken adları gibi ifadeleri dizedeki küme ayraçları içine koymanıza imkan tanır.</span><span class="sxs-lookup"><span data-stu-id="2f7d4-152">The dollar sign (`$`) in front of a string lets you put expressions such as variable names in curly braces in the string.</span></span> <span data-ttu-id="2f7d4-153">İfade değeri, ifadenin yerine dizeye eklenir.</span><span class="sxs-lookup"><span data-stu-id="2f7d4-153">The expression value is inserted into the string in place of the expression.</span></span> <span data-ttu-id="2f7d4-154">Bu söz dizimi, [enterpolasyonlu dizeler](../../csharp/language-reference/tokens/interpolated.md)olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="2f7d4-154">This syntax is referred to as [interpolated strings](../../csharp/language-reference/tokens/interpolated.md).</span></span>

1. <span data-ttu-id="2f7d4-155"><kbd></kbd> + Programı hata ayıklamadan çalıştırmak için CTRL<kbd>F5</kbd> tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="2f7d4-155">Press <kbd>Ctrl</kbd>+<kbd>F5</kbd> to run the program without debugging.</span></span>

1. <span data-ttu-id="2f7d4-156">Bir ad girip <kbd>ENTER</kbd> tuşuna basarak istemi yanıtlayın.</span><span class="sxs-lookup"><span data-stu-id="2f7d4-156">Respond to the prompt by entering a name and pressing the <kbd>Enter</kbd> key.</span></span>

   :::image type="content" source="./media/with-visual-studio/hello-world-update.png" alt-text="Değiştirilen program çıkışıyla konsol penceresi":::

1. <span data-ttu-id="2f7d4-158">Konsol penceresini kapatmak için herhangi bir tuşa basın.</span><span class="sxs-lookup"><span data-stu-id="2f7d4-158">Press any key to close the console window.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="2f7d4-159">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="2f7d4-159">Additional resources</span></span>

- [<span data-ttu-id="2f7d4-160">Geçerli yayınlar ve uzun süreli destek yayınları</span><span class="sxs-lookup"><span data-stu-id="2f7d4-160">Current releases and long-term support releases</span></span>](../releases-and-support.md#net-core-and-net-5-version-lifecycles)

## <a name="next-steps"></a><span data-ttu-id="2f7d4-161">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="2f7d4-161">Next steps</span></span>

<span data-ttu-id="2f7d4-162">Bu öğreticide, bir .NET konsol uygulaması oluşturdunuz.</span><span class="sxs-lookup"><span data-stu-id="2f7d4-162">In this tutorial, you created a .NET console application.</span></span> <span data-ttu-id="2f7d4-163">Sonraki öğreticide, uygulamada hata ayıklaması yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2f7d4-163">In the next tutorial, you debug the app.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="2f7d4-164">Visual Studio kullanarak bir .NET konsol uygulamasında hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="2f7d4-164">Debug a .NET console application using Visual Studio</span></span>](debugging-with-visual-studio.md)
