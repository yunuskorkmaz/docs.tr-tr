---
title: Visual Studio kullanarak bir .NET konsol uygulaması oluşturma
description: Visual Studio kullanarak C# veya Visual Basic .NET konsol uygulaması oluşturmayı öğrenin.
ms.date: 03/26/2021
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet,contperf-fy21q3
ms.openlocfilehash: e55927080ab30e7a24c54656b7f11a94a023bd65
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/27/2021
ms.locfileid: "105636811"
---
# <a name="tutorial-create-a-net-console-application-using-visual-studio"></a><span data-ttu-id="04356-103">Öğretici: Visual Studio kullanarak bir .NET konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="04356-103">Tutorial: Create a .NET console application using Visual Studio</span></span>

<span data-ttu-id="04356-104">Bu öğreticide, Visual Studio 2019 ' de bir .NET konsol uygulamasının nasıl oluşturulacağı ve çalıştırılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="04356-104">This tutorial shows how to create and run a .NET console application in Visual Studio 2019.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="04356-105">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="04356-105">Prerequisites</span></span>

- <span data-ttu-id="04356-106">**.NET Core platformlar arası geliştirme** iş yükünün yüklü olduğu [Visual Studio 2019 sürüm 16.9.2 veya sonraki bir sürümü](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) .</span><span class="sxs-lookup"><span data-stu-id="04356-106">[Visual Studio 2019 version 16.9.2 or a later version](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) with the **.NET Core cross-platform development** workload installed.</span></span> <span data-ttu-id="04356-107">.NET 5,0 SDK, bu iş yükünü seçtiğinizde otomatik olarak yüklenir.</span><span class="sxs-lookup"><span data-stu-id="04356-107">The .NET 5.0 SDK is automatically installed when you select this workload.</span></span>

  <span data-ttu-id="04356-108">Daha fazla bilgi için bkz. [Visual Studio ile .NET SDK 'Yı yükler](../install/windows.md#install-with-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="04356-108">For more information, see [Install the .NET SDK with Visual Studio](../install/windows.md#install-with-visual-studio).</span></span>

## <a name="create-the-app"></a><span data-ttu-id="04356-109">Uygulama oluşturma</span><span class="sxs-lookup"><span data-stu-id="04356-109">Create the app</span></span>

<span data-ttu-id="04356-110">"HelloWorld" adlı bir .NET konsol uygulaması projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="04356-110">Create a .NET console app project named "HelloWorld".</span></span>

1. <span data-ttu-id="04356-111">Visual Studio 2019’u başlatın.</span><span class="sxs-lookup"><span data-stu-id="04356-111">Start Visual Studio 2019.</span></span>

1. <span data-ttu-id="04356-112">Başlangıç sayfasında **Yeni proje oluştur**' u seçin.</span><span class="sxs-lookup"><span data-stu-id="04356-112">On the start page, choose **Create a new project**.</span></span>

   :::image type="content" source="./media/with-visual-studio/start-window.png" alt-text="Visual Studio başlangıç sayfasında yeni bir proje oluştur düğmesi seçili":::

1. <span data-ttu-id="04356-114">**Yeni proje oluştur** sayfasında, arama kutusuna **konsol** girin.</span><span class="sxs-lookup"><span data-stu-id="04356-114">On the **Create a new project** page, enter **console** in the search box.</span></span> <span data-ttu-id="04356-115">Ardından, dil listesinden **C#** veya **Visual Basic** ' yi seçin ve ardından platform listesinden **tüm platformlar** ' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="04356-115">Next, choose **C#** or **Visual Basic** from the language list, and then choose **All platforms** from the platform list.</span></span> <span data-ttu-id="04356-116">**Konsol uygulaması** şablonunu seçin ve ardından **İleri**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="04356-116">Choose the **Console Application** template, and then choose **Next**.</span></span>

   :::image type="content" source="./media/with-visual-studio/create-new-project.png" alt-text="Filtreler seçiliyken yeni bir proje penceresi oluştur":::

   > [!TIP]
   > <span data-ttu-id="04356-118">.NET şablonlarını görmüyorsanız, muhtemelen gerekli iş yükü eksik olabilir.</span><span class="sxs-lookup"><span data-stu-id="04356-118">If you don't see the .NET templates, you're probably missing the required workload.</span></span> <span data-ttu-id="04356-119">**Aradığınızı bulmuyor musunuz?** iletisi altında, **daha fazla araç ve özellik yüklemeyi** seçin bağlantısına tıklayın.</span><span class="sxs-lookup"><span data-stu-id="04356-119">Under the **Not finding what you're looking for?** message, choose the **Install more tools and features** link.</span></span> <span data-ttu-id="04356-120">Visual Studio Yükleyicisi açılır.</span><span class="sxs-lookup"><span data-stu-id="04356-120">The Visual Studio Installer opens.</span></span> <span data-ttu-id="04356-121">**.NET Core platformlar arası geliştirme** iş yükünün yüklü olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="04356-121">Make sure you have the **.NET Core cross-platform development** workload installed.</span></span>

1. <span data-ttu-id="04356-122">**Yeni projenizi yapılandırın** iletişim kutusunda, **Proje adı** kutusuna **HelloWorld** yazın.</span><span class="sxs-lookup"><span data-stu-id="04356-122">In the **Configure your new project** dialog,  enter **HelloWorld** in the **Project name** box.</span></span> <span data-ttu-id="04356-123">Ardından **İleri**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="04356-123">Then choose **Next**.</span></span>

   :::image type="content" source="./media/with-visual-studio/configure-new-project.png" alt-text="Yeni proje pencerenizi proje adı, konum ve çözüm adı alanlarıyla yapılandırın":::

1. <span data-ttu-id="04356-125">**Ek bilgi** iletişim kutusunda **.NET 5,0 (geçerli)** öğesini seçin ve ardından **Oluştur**' u seçin.</span><span class="sxs-lookup"><span data-stu-id="04356-125">In the **Additional information** dialog, select **.NET 5.0 (Current)**, and then select **Create**.</span></span>

   :::image type="content" source="media/with-visual-studio/additional-info.png" alt-text="Ek bilgi iletişim kutusu":::

<span data-ttu-id="04356-127">Şablon basit bir "Merhaba Dünya" uygulaması oluşturur.</span><span class="sxs-lookup"><span data-stu-id="04356-127">The template creates a simple "Hello World" application.</span></span> <span data-ttu-id="04356-128"><xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType>"Merhaba Dünya!" öğesini göstermek için yöntemini çağırır</span><span class="sxs-lookup"><span data-stu-id="04356-128">It calls the <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> method to display "Hello World!"</span></span> <span data-ttu-id="04356-129">Konsol penceresinde.</span><span class="sxs-lookup"><span data-stu-id="04356-129">in the console window.</span></span>

<span data-ttu-id="04356-130">Şablon kodu, `Program` `Main` bağımsız değişken olarak bir diziyi alan tek bir yöntemi olan sınıfını tanımlar <xref:System.String> :</span><span class="sxs-lookup"><span data-stu-id="04356-130">The template code defines a class, `Program`, with a single method, `Main`, that takes a <xref:System.String> array as an argument:</span></span>

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

<span data-ttu-id="04356-131">`Main` uygulama giriş noktası, uygulamayı başlattığında çalışma zamanı tarafından otomatik olarak çağrılan yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="04356-131">`Main` is the application entry point, the method that's called automatically by the runtime when it launches the application.</span></span> <span data-ttu-id="04356-132">Uygulama başlatıldığında sağlanan herhangi bir komut satırı bağımsız değişkeni, *args* dizisinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="04356-132">Any command-line arguments supplied when the application is launched are available in the *args* array.</span></span>

<span data-ttu-id="04356-133">Kullanmak istediğiniz dil gösterilmiyorsa sayfanın en üstündeki dil seçicisini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="04356-133">If the language you want to use is not shown, change the language selector at the top of the page.</span></span>

## <a name="run-the-app"></a><span data-ttu-id="04356-134">Uygulamayı çalıştırma</span><span class="sxs-lookup"><span data-stu-id="04356-134">Run the app</span></span>

1. <span data-ttu-id="04356-135"><kbd></kbd> + Programı hata ayıklamadan çalıştırmak için CTRL<kbd>F5</kbd> tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="04356-135">Press <kbd>Ctrl</kbd>+<kbd>F5</kbd> to run the program without debugging.</span></span>

   <span data-ttu-id="04356-136">Bir konsol penceresi "Merhaba Dünya!" metniyle açılıyor</span><span class="sxs-lookup"><span data-stu-id="04356-136">A console window opens with the text "Hello World!"</span></span> <span data-ttu-id="04356-137">ekranda yazdırılır.</span><span class="sxs-lookup"><span data-stu-id="04356-137">printed on the screen.</span></span>

   :::image type="content" source="./media/with-visual-studio/hello-world-console.png" alt-text="Merhaba Dünya devam etmek için herhangi bir tuşa basarak konsol penceresi":::

1. <span data-ttu-id="04356-139">Konsol penceresini kapatmak için herhangi bir tuşa basın.</span><span class="sxs-lookup"><span data-stu-id="04356-139">Press any key to close the console window.</span></span>

## <a name="enhance-the-app"></a><span data-ttu-id="04356-140">Uygulamayı geliştirin</span><span class="sxs-lookup"><span data-stu-id="04356-140">Enhance the app</span></span>

<span data-ttu-id="04356-141">Kullanıcıya adını istemek ve Tarih ve saat ile birlikte göstermek için uygulamayı geliştirin.</span><span class="sxs-lookup"><span data-stu-id="04356-141">Enhance the application to prompt the user for their name and display it along with the date and time.</span></span>

1. <span data-ttu-id="04356-142">*Program. cs* veya *program. vb*' de, yönteminin içeriğini, `Main` çağıran satırı, `Console.WriteLine` aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="04356-142">In *Program.cs* or *Program.vb*, replace the contents of the `Main` method, which is the line that calls `Console.WriteLine`, with the following code:</span></span>

   :::code language="csharp" source="./snippets/with-visual-studio/csharp/Program.cs" id="MainMethod":::
   :::code language="vb" source="./snippets/with-visual-studio/vb/Program.vb" id="MainMethod":::

   <span data-ttu-id="04356-143">Bu kod, konsol penceresinde bir istem görüntüler ve ardından <kbd>ENTER</kbd> tuşuna basarak Kullanıcı bir dize girene kadar bekler.</span><span class="sxs-lookup"><span data-stu-id="04356-143">This code displays a prompt in the console window and waits until the user enters a string followed by the <kbd>Enter</kbd> key.</span></span> <span data-ttu-id="04356-144">Bu dizeyi adlı bir değişkende depolar `name` .</span><span class="sxs-lookup"><span data-stu-id="04356-144">It stores this string in a variable named `name`.</span></span> <span data-ttu-id="04356-145">Ayrıca <xref:System.DateTime.Now?displayProperty=nameWithType> , geçerli yerel saati içeren özelliğinin değerini alır ve bunu adlı bir değişkene atar `currentDate` .</span><span class="sxs-lookup"><span data-stu-id="04356-145">It also retrieves the value of the <xref:System.DateTime.Now?displayProperty=nameWithType> property, which contains the current local time, and assigns it to a variable named `currentDate`.</span></span> <span data-ttu-id="04356-146">Bu değerleri konsol penceresinde görüntüler.</span><span class="sxs-lookup"><span data-stu-id="04356-146">And it displays these values in the console window.</span></span> <span data-ttu-id="04356-147">Son olarak, konsol penceresinde bir istem görüntüler ve <xref:System.Console.ReadKey(System.Boolean)?displayProperty=nameWithType> Kullanıcı girişini beklemek için yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="04356-147">Finally, it displays a prompt in the console window and calls the <xref:System.Console.ReadKey(System.Boolean)?displayProperty=nameWithType> method to wait for user input.</span></span>

   <span data-ttu-id="04356-148"><xref:System.Environment.NewLine> , bir satır kesmeyi göstermek için platformdan bağımsız ve dilden bağımsız bir yoldur.</span><span class="sxs-lookup"><span data-stu-id="04356-148"><xref:System.Environment.NewLine> is a platform-independent and language-independent way to represent a line break.</span></span> <span data-ttu-id="04356-149">Alternatifler `\n` C# ve `vbCrLf` Visual Basic ' de bulunur.</span><span class="sxs-lookup"><span data-stu-id="04356-149">Alternatives are `\n` in C# and `vbCrLf` in Visual Basic.</span></span>

   <span data-ttu-id="04356-150">`$`Bir dizenin önünde dolar işareti (), değişken adları gibi ifadeleri dizedeki küme ayraçları içine koymanıza imkan tanır.</span><span class="sxs-lookup"><span data-stu-id="04356-150">The dollar sign (`$`) in front of a string lets you put expressions such as variable names in curly braces in the string.</span></span> <span data-ttu-id="04356-151">İfade değeri, ifadenin yerine dizeye eklenir.</span><span class="sxs-lookup"><span data-stu-id="04356-151">The expression value is inserted into the string in place of the expression.</span></span> <span data-ttu-id="04356-152">Bu söz dizimi, [enterpolasyonlu dizeler](../../csharp/language-reference/tokens/interpolated.md)olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="04356-152">This syntax is referred to as [interpolated strings](../../csharp/language-reference/tokens/interpolated.md).</span></span>

1. <span data-ttu-id="04356-153"><kbd></kbd> + Programı hata ayıklamadan çalıştırmak için CTRL<kbd>F5</kbd> tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="04356-153">Press <kbd>Ctrl</kbd>+<kbd>F5</kbd> to run the program without debugging.</span></span>

1. <span data-ttu-id="04356-154">Bir ad girip <kbd>ENTER</kbd> tuşuna basarak istemi yanıtlayın.</span><span class="sxs-lookup"><span data-stu-id="04356-154">Respond to the prompt by entering a name and pressing the <kbd>Enter</kbd> key.</span></span>

   :::image type="content" source="./media/with-visual-studio/hello-world-update.png" alt-text="Değiştirilen program çıkışıyla konsol penceresi":::

1. <span data-ttu-id="04356-156">Konsol penceresini kapatmak için herhangi bir tuşa basın.</span><span class="sxs-lookup"><span data-stu-id="04356-156">Press any key to close the console window.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="04356-157">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="04356-157">Additional resources</span></span>

- [<span data-ttu-id="04356-158">Geçerli yayınlar ve uzun süreli destek yayınları</span><span class="sxs-lookup"><span data-stu-id="04356-158">Current releases and long-term support releases</span></span>](../releases-and-support.md#net-core-and-net-5-version-lifecycles)

## <a name="next-steps"></a><span data-ttu-id="04356-159">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="04356-159">Next steps</span></span>

<span data-ttu-id="04356-160">Bu öğreticide, bir .NET konsol uygulaması oluşturdunuz.</span><span class="sxs-lookup"><span data-stu-id="04356-160">In this tutorial, you created a .NET console application.</span></span> <span data-ttu-id="04356-161">Sonraki öğreticide, uygulamada hata ayıklaması yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="04356-161">In the next tutorial, you debug the app.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="04356-162">Visual Studio kullanarak bir .NET konsol uygulamasında hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="04356-162">Debug a .NET console application using Visual Studio</span></span>](debugging-with-visual-studio.md)
