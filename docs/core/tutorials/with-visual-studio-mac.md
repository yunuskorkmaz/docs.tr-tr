---
title: Mac için Visual Studio kullanarak bir .NET konsol uygulaması oluşturma
description: Mac için Visual Studio kullanarak bir .NET konsol uygulaması oluşturmayı öğrenin.
ms.date: 11/30/2020
ms.openlocfilehash: 4add8309338b8618265a66b9e71dab2df38ca8d0
ms.sourcegitcommit: 1d3af230ec30d8d061be7a887f6ba38a530c4ece
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2021
ms.locfileid: "102511833"
---
# <a name="tutorial-create-a-net-console-application-using-visual-studio-for-mac"></a><span data-ttu-id="4c4a6-103">Öğretici: Mac için Visual Studio kullanarak bir .NET konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="4c4a6-103">Tutorial: Create a .NET console application using Visual Studio for Mac</span></span>

<span data-ttu-id="4c4a6-104">Bu öğreticide, Mac için Visual Studio kullanarak bir .NET konsol uygulamasının nasıl oluşturulacağı ve çalıştırılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="4c4a6-104">This tutorial shows how to create and run a .NET console application using Visual Studio for Mac.</span></span>

> [!NOTE]
> <span data-ttu-id="4c4a6-105">Geri bildiriminiz çok değerli.</span><span class="sxs-lookup"><span data-stu-id="4c4a6-105">Your feedback is highly valued.</span></span> <span data-ttu-id="4c4a6-106">Mac için Visual Studio üzerinde geliştirme ekibine geri bildirimde bulunmak için kullanabileceğiniz iki yol vardır:</span><span class="sxs-lookup"><span data-stu-id="4c4a6-106">There are two ways you can provide feedback to the development team on Visual Studio for Mac:</span></span>
>
> * <span data-ttu-id="4c4a6-107">Mac için Visual Studio,   >  menüden **sorun bildir** veya hoş geldiniz ekranından **sorun** bildir ' i seçerek bir hata raporu dosyalayarak bir pencere açar.</span><span class="sxs-lookup"><span data-stu-id="4c4a6-107">In Visual Studio for Mac, select **Help** > **Report a Problem** from the menu or **Report a Problem** from the Welcome screen, which will open a window for filing a bug report.</span></span> <span data-ttu-id="4c4a6-108">Geri bildiriminizi [Geliştirici Topluluğu](https://aka.ms/feedback/report?space=41) portalında izleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4c4a6-108">You can track your feedback in the [Developer Community](https://aka.ms/feedback/report?space=41) portal.</span></span>
> * <span data-ttu-id="4c4a6-109">Öneride bulunmak için,   >  menüden **bir öneri sağlayın** veya hoş geldiniz ekranından bir öneri  sağlayın. Bu işlem sizi [Mac için Visual Studio Geliştirici topluluğu Web sayfasına](https://aka.ms/feedback/suggest?space=41)götürür.</span><span class="sxs-lookup"><span data-stu-id="4c4a6-109">To make a suggestion, select **Help** > **Provide a Suggestion** from the menu or **Provide a Suggestion** from the Welcome screen, which will take you to the [Visual Studio for Mac Developer Community webpage](https://aka.ms/feedback/suggest?space=41).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="4c4a6-110">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="4c4a6-110">Prerequisites</span></span>

* <span data-ttu-id="4c4a6-111">[Sürüm 8,8 veya üzeri Mac için Visual Studio](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link).</span><span class="sxs-lookup"><span data-stu-id="4c4a6-111">[Visual Studio for Mac version 8.8 or later](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link).</span></span> <span data-ttu-id="4c4a6-112">.NET Core ' u yüklemek için seçeneği belirleyin.</span><span class="sxs-lookup"><span data-stu-id="4c4a6-112">Select the option to install .NET Core.</span></span> <span data-ttu-id="4c4a6-113">Xamarin 'in yüklenmesi .NET geliştirme için isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="4c4a6-113">Installing Xamarin is optional for .NET development.</span></span> <span data-ttu-id="4c4a6-114">Daha fazla bilgi için aşağıdaki kaynaklara bakın:</span><span class="sxs-lookup"><span data-stu-id="4c4a6-114">For more information, see the following resources:</span></span>

  * <span data-ttu-id="4c4a6-115">[Öğretici: Mac için Visual Studio yüklemesi](/visualstudio/mac/installation).</span><span class="sxs-lookup"><span data-stu-id="4c4a6-115">[Tutorial: Install Visual Studio for Mac](/visualstudio/mac/installation).</span></span>
  * <span data-ttu-id="4c4a6-116">[Desteklenen macOS sürümleri](../install/windows.md).</span><span class="sxs-lookup"><span data-stu-id="4c4a6-116">[Supported macOS versions](../install/windows.md).</span></span>
  * <span data-ttu-id="4c4a6-117">[Mac için Visual Studio tarafından desteklenen .NET sürümleri](/visualstudio/mac/net-core-support).</span><span class="sxs-lookup"><span data-stu-id="4c4a6-117">[.NET versions supported by Visual Studio for Mac](/visualstudio/mac/net-core-support).</span></span>

## <a name="create-the-app"></a><span data-ttu-id="4c4a6-118">Uygulama oluşturma</span><span class="sxs-lookup"><span data-stu-id="4c4a6-118">Create the app</span></span>

1. <span data-ttu-id="4c4a6-119">Mac için Visual Studio başlatın.</span><span class="sxs-lookup"><span data-stu-id="4c4a6-119">Start Visual Studio for Mac.</span></span>

1. <span data-ttu-id="4c4a6-120">Başlangıç penceresinde **Yeni** ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="4c4a6-120">Select **New** in the start window.</span></span>

   :::image type="content" source="media/with-visual-studio-mac/visual-studio-mac-new-project.png" alt-text="Mac için Visual Studio başlangıç ekranında yeni düğme":::

1. <span data-ttu-id="4c4a6-122">**Yeni proje** Iletişim kutusunda **Web ve konsol** düğümü altında **uygulama** ' yı seçin.</span><span class="sxs-lookup"><span data-stu-id="4c4a6-122">In the **New Project** dialog, select **App** under the **Web and Console** node.</span></span> <span data-ttu-id="4c4a6-123">**Konsol uygulaması** şablonunu seçin ve **İleri**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="4c4a6-123">Select the **Console Application** template, and select **Next**.</span></span>

   :::image type="content" source="media/with-visual-studio-mac/visual-studio-mac-new-dialog.png" alt-text="Yeni proje şablonları listesi":::

1. <span data-ttu-id="4c4a6-125">**Yeni konsol uygulamanızı yapılandırma** Iletişim kutusunun **hedef çerçeve** açılır penceresinde, **.NET 5,0**' i seçin ve **İleri**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="4c4a6-125">In the **Target Framework** drop-down of the **Configure your new Console Application** dialog, select **.NET 5.0**, and select **Next**.</span></span>

1. <span data-ttu-id="4c4a6-126">**Proje adı** Için "HelloWorld" yazın ve **Oluştur**' u seçin.</span><span class="sxs-lookup"><span data-stu-id="4c4a6-126">Type "HelloWorld" for the **Project Name**, and select **Create**.</span></span>

   :::image type="content" source="media/with-visual-studio-mac/visual-studio-mac-new-options.png" alt-text="Yeni konsol uygulamanızı yapılandırma iletişim kutusu":::

<span data-ttu-id="4c4a6-128">Şablon basit bir "Merhaba Dünya" uygulaması oluşturur.</span><span class="sxs-lookup"><span data-stu-id="4c4a6-128">The template creates a simple "Hello World" application.</span></span> <span data-ttu-id="4c4a6-129"><xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType>"Merhaba Dünya!" öğesini göstermek için yöntemini çağırır</span><span class="sxs-lookup"><span data-stu-id="4c4a6-129">It calls the <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> method to display "Hello World!"</span></span> <span data-ttu-id="4c4a6-130">, Terminal penceresinde.</span><span class="sxs-lookup"><span data-stu-id="4c4a6-130">in the terminal window.</span></span>

<span data-ttu-id="4c4a6-131">Şablon kodu, `Program` `Main` bağımsız değişken olarak bir diziyi alan tek bir yöntemi olan sınıfını tanımlar <xref:System.String> :</span><span class="sxs-lookup"><span data-stu-id="4c4a6-131">The template code defines a class, `Program`, with a single method, `Main`, that takes a <xref:System.String> array as an argument:</span></span>

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

<span data-ttu-id="4c4a6-132">`Main` uygulama giriş noktası, uygulamayı başlattığında çalışma zamanı tarafından otomatik olarak çağrılan yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="4c4a6-132">`Main` is the application entry point, the method that's called automatically by the runtime when it launches the application.</span></span> <span data-ttu-id="4c4a6-133">Uygulama başlatıldığında sağlanan tüm komut satırı bağımsız değişkenleri `args` dizide kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="4c4a6-133">Any command-line arguments supplied when the application is launched are available in the `args` array.</span></span>

## <a name="run-the-app"></a><span data-ttu-id="4c4a6-134">Uygulamayı çalıştırma</span><span class="sxs-lookup"><span data-stu-id="4c4a6-134">Run the app</span></span>

1. <span data-ttu-id="4c4a6-135"><kbd></kbd><kbd></kbd><kbd></kbd> <kbd></kbd> + <kbd></kbd> + Uygulamayı hata ayıklamadan çalıştırmak için ⌥ ⌘ ↵ (Option komut<kbd>ENTER</kbd>) tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="4c4a6-135">Press <kbd>⌥</kbd><kbd>⌘</kbd><kbd>↵</kbd> (<kbd>option</kbd>+<kbd>command</kbd>+<kbd>enter</kbd>) to run the app without debugging.</span></span>

   :::image type="content" source="media/with-visual-studio-mac/visual-studio-mac-output.png" alt-text="Terminal Merhaba Dünya gösterir!":::

1. <span data-ttu-id="4c4a6-137">**Terminal** penceresini kapatın.</span><span class="sxs-lookup"><span data-stu-id="4c4a6-137">Close the **Terminal** window.</span></span>

## <a name="enhance-the-app"></a><span data-ttu-id="4c4a6-138">Uygulamayı geliştirin</span><span class="sxs-lookup"><span data-stu-id="4c4a6-138">Enhance the app</span></span>

<span data-ttu-id="4c4a6-139">Kullanıcıya adını istemek ve Tarih ve saat ile birlikte göstermek için uygulamayı geliştirin.</span><span class="sxs-lookup"><span data-stu-id="4c4a6-139">Enhance the application to prompt the user for their name and display it along with the date and time.</span></span>

1. <span data-ttu-id="4c4a6-140">*Program.cs*' de, `Main` aşağıdaki kodla birlikte çağıran satırı olan yönteminin içeriğini değiştirin `Console.WriteLine` :</span><span class="sxs-lookup"><span data-stu-id="4c4a6-140">In *Program.cs*, replace the contents of the `Main` method, which is the line that calls `Console.WriteLine`, with the following code:</span></span>

   :::code language="csharp" source="./snippets/with-visual-studio/csharp/Program.cs" id="MainMethod":::

   <span data-ttu-id="4c4a6-141">Bu kod, konsol penceresinde bir istem görüntüler ve ardından <kbd>ENTER</kbd> tuşuna basarak Kullanıcı bir dize girene kadar bekler.</span><span class="sxs-lookup"><span data-stu-id="4c4a6-141">This code displays a prompt in the console window and waits until the user enters a string followed by the <kbd>enter</kbd> key.</span></span> <span data-ttu-id="4c4a6-142">Bu dizeyi adlı bir değişkende depolar `name` .</span><span class="sxs-lookup"><span data-stu-id="4c4a6-142">It stores this string in a variable named `name`.</span></span> <span data-ttu-id="4c4a6-143">Ayrıca <xref:System.DateTime.Now?displayProperty=nameWithType> , geçerli yerel saati içeren özelliğinin değerini alır ve bunu adlı bir değişkene atar `date` .</span><span class="sxs-lookup"><span data-stu-id="4c4a6-143">It also retrieves the value of the <xref:System.DateTime.Now?displayProperty=nameWithType> property, which contains the current local time, and assigns it to a variable named `date`.</span></span> <span data-ttu-id="4c4a6-144">Bu değerleri konsol penceresinde görüntüler.</span><span class="sxs-lookup"><span data-stu-id="4c4a6-144">And it displays these values in the console window.</span></span> <span data-ttu-id="4c4a6-145">Son olarak, konsol penceresinde bir istem görüntüler ve <xref:System.Console.ReadKey(System.Boolean)?displayProperty=nameWithType> Kullanıcı girişini beklemek için yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="4c4a6-145">Finally, it displays a prompt in the console window and calls the <xref:System.Console.ReadKey(System.Boolean)?displayProperty=nameWithType> method to wait for user input.</span></span>

   <span data-ttu-id="4c4a6-146"><xref:System.Environment.NewLine> , bir satır kesmeyi göstermek için platformdan bağımsız ve dilden bağımsız bir yoldur.</span><span class="sxs-lookup"><span data-stu-id="4c4a6-146"><xref:System.Environment.NewLine> is a platform-independent and language-independent way to represent a line break.</span></span> <span data-ttu-id="4c4a6-147">Alternatifler `\n` C# ve `vbCrLf` Visual Basic ' de bulunur.</span><span class="sxs-lookup"><span data-stu-id="4c4a6-147">Alternatives are `\n` in C# and `vbCrLf` in Visual Basic.</span></span>

   <span data-ttu-id="4c4a6-148">`$`Bir dizenin önünde dolar işareti (), değişken adları gibi ifadeleri dizedeki küme ayraçları içine koymanıza imkan tanır.</span><span class="sxs-lookup"><span data-stu-id="4c4a6-148">The dollar sign (`$`) in front of a string lets you put expressions such as variable names in curly braces in the string.</span></span> <span data-ttu-id="4c4a6-149">İfade değeri, ifadenin yerine dizeye eklenir.</span><span class="sxs-lookup"><span data-stu-id="4c4a6-149">The expression value is inserted into the string in place of the expression.</span></span> <span data-ttu-id="4c4a6-150">Bu söz dizimi, [enterpolasyonlu dizeler](../../csharp/language-reference/tokens/interpolated.md)olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="4c4a6-150">This syntax is referred to as [interpolated strings](../../csharp/language-reference/tokens/interpolated.md).</span></span>

1. <span data-ttu-id="4c4a6-151">Uygulamayı çalıştırmak için <kbd>⌥</kbd><kbd>⌘</kbd><kbd>↵</kbd> (<kbd>seçenek</kbd> + <kbd>komut</kbd> + <kbd>ENTER</kbd>) tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="4c4a6-151">Press <kbd>⌥</kbd><kbd>⌘</kbd><kbd>↵</kbd> (<kbd>option</kbd>+<kbd>command</kbd>+<kbd>enter</kbd>) to run the app.</span></span>

1. <span data-ttu-id="4c4a6-152">Bir ad girip <kbd>ENTER</kbd>tuşuna basarak istemi yanıtlayın.</span><span class="sxs-lookup"><span data-stu-id="4c4a6-152">Respond to the prompt by entering a name and pressing <kbd>enter</kbd>.</span></span>

   :::image type="content" source="media/with-visual-studio-mac/hello-world-update.png" alt-text="Terminal değiştirilen program çıktısını gösterir":::

1. <span data-ttu-id="4c4a6-154">Terminali kapatın.</span><span class="sxs-lookup"><span data-stu-id="4c4a6-154">Close the terminal.</span></span>

## <a name="next-steps"></a><span data-ttu-id="4c4a6-155">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="4c4a6-155">Next steps</span></span>

<span data-ttu-id="4c4a6-156">Bu öğreticide, bir .NET konsol uygulaması oluşturdunuz.</span><span class="sxs-lookup"><span data-stu-id="4c4a6-156">In this tutorial, you created a .NET console application.</span></span> <span data-ttu-id="4c4a6-157">Sonraki öğreticide, uygulamada hata ayıklaması yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4c4a6-157">In the next tutorial, you debug the app.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="4c4a6-158">Mac için Visual Studio kullanarak bir .NET konsol uygulamasında hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="4c4a6-158">Debug a .NET console application using Visual Studio for Mac</span></span>](debugging-with-visual-studio-mac.md)
