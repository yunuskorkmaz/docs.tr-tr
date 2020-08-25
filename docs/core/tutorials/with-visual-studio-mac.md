---
title: Mac için Visual Studio kullanarak bir .NET Core konsol uygulaması oluşturma
description: Mac için Visual Studio kullanarak bir .NET Core konsol uygulaması oluşturmayı öğrenin.
ms.date: 06/02/2020
ms.openlocfilehash: e0b18837bf8bef5be5f20b84341bde8526b9f7a2
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88811879"
---
# <a name="tutorial-create-a-net-core-console-application-using-visual-studio-for-mac"></a><span data-ttu-id="36b6c-103">Öğretici: Mac için Visual Studio kullanarak bir .NET Core konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="36b6c-103">Tutorial: Create a .NET Core console application using Visual Studio for Mac</span></span>

<span data-ttu-id="36b6c-104">Bu öğreticide Mac için Visual Studio kullanarak bir .NET Core konsol uygulamasının nasıl oluşturulacağı ve çalıştırılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="36b6c-104">This tutorial shows how to create and run a .NET Core console application using Visual Studio for Mac.</span></span>

> [!NOTE]
> <span data-ttu-id="36b6c-105">Geri bildiriminiz çok değerli.</span><span class="sxs-lookup"><span data-stu-id="36b6c-105">Your feedback is highly valued.</span></span> <span data-ttu-id="36b6c-106">Mac için Visual Studio üzerinde geliştirme ekibine geri bildirimde bulunmak için kullanabileceğiniz iki yol vardır:</span><span class="sxs-lookup"><span data-stu-id="36b6c-106">There are two ways you can provide feedback to the development team on Visual Studio for Mac:</span></span>
>
> * <span data-ttu-id="36b6c-107">Mac için Visual Studio, **Help**  >  menüden**sorun bildir** veya hoş geldiniz ekranından **sorun** bildir ' i seçerek bir hata raporu dosyalayarak bir pencere açar.</span><span class="sxs-lookup"><span data-stu-id="36b6c-107">In Visual Studio for Mac, select **Help** > **Report a Problem** from the menu or **Report a Problem** from the Welcome screen, which will open a window for filing a bug report.</span></span> <span data-ttu-id="36b6c-108">Geri bildiriminizi [Geliştirici Topluluğu](https://developercommunity.visualstudio.com/spaces/8/index.html) portalında izleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="36b6c-108">You can track your feedback in the [Developer Community](https://developercommunity.visualstudio.com/spaces/8/index.html) portal.</span></span>
> * <span data-ttu-id="36b6c-109">Öneride bulunmak için, **Help**  >  menüden**bir öneri sağlayın** veya hoş geldiniz ekranından bir öneri **Provide a Suggestion** sağlayın. Bu işlem sizi [Mac için Visual Studio Geliştirici topluluğu Web sayfasına](https://developercommunity.visualstudio.com/content/idea/post.html?space=41)götürür.</span><span class="sxs-lookup"><span data-stu-id="36b6c-109">To make a suggestion, select **Help** > **Provide a Suggestion** from the menu or **Provide a Suggestion** from the Welcome screen, which will take you to the [Visual Studio for Mac Developer Community webpage](https://developercommunity.visualstudio.com/content/idea/post.html?space=41).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="36b6c-110">Ön koşullar</span><span class="sxs-lookup"><span data-stu-id="36b6c-110">Prerequisites</span></span>

* <span data-ttu-id="36b6c-111">[Sürüm 8,6 veya üzeri Mac için Visual Studio](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link).</span><span class="sxs-lookup"><span data-stu-id="36b6c-111">[Visual Studio for Mac version 8.6 or later](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link).</span></span> <span data-ttu-id="36b6c-112">.NET Core ' u yüklemek için seçeneği belirleyin.</span><span class="sxs-lookup"><span data-stu-id="36b6c-112">Select the option to install .NET Core.</span></span> <span data-ttu-id="36b6c-113">.NET Core geliştirmesi için Xamarin 'in yüklenmesi isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="36b6c-113">Installing Xamarin is optional for .NET Core development.</span></span> <span data-ttu-id="36b6c-114">Daha fazla bilgi için aşağıdaki kaynaklara bakın:</span><span class="sxs-lookup"><span data-stu-id="36b6c-114">For more information, see the following resources:</span></span>

  * <span data-ttu-id="36b6c-115">[Öğretici: Mac için Visual Studio yüklemesi](/visualstudio/mac/installation).</span><span class="sxs-lookup"><span data-stu-id="36b6c-115">[Tutorial: Install Visual Studio for Mac](/visualstudio/mac/installation).</span></span>
  * <span data-ttu-id="36b6c-116">[Desteklenen macOS sürümleri](../install/dependencies.md?pivots=os-macos).</span><span class="sxs-lookup"><span data-stu-id="36b6c-116">[Supported macOS versions](../install/dependencies.md?pivots=os-macos).</span></span>
  * <span data-ttu-id="36b6c-117">[Mac için Visual Studio tarafından desteklenen .NET Core sürümleri](/visualstudio/mac/net-core-support).</span><span class="sxs-lookup"><span data-stu-id="36b6c-117">[.NET Core versions supported by Visual Studio for Mac](/visualstudio/mac/net-core-support).</span></span>

## <a name="create-the-app"></a><span data-ttu-id="36b6c-118">Uygulama oluşturma</span><span class="sxs-lookup"><span data-stu-id="36b6c-118">Create the app</span></span>

<span data-ttu-id="36b6c-119">"HelloWorld" adlı bir .NET Core konsol uygulaması projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="36b6c-119">Create a .NET Core console app project named "HelloWorld".</span></span>

1. <span data-ttu-id="36b6c-120">Mac için Visual Studio başlatın.</span><span class="sxs-lookup"><span data-stu-id="36b6c-120">Start Visual Studio for Mac.</span></span>

1. <span data-ttu-id="36b6c-121">Başlangıç penceresinde **Yeni** ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="36b6c-121">Select **New** in the start window.</span></span>

   :::image type="content" source="media/with-visual-studio-mac/visual-studio-mac-new-project.png" alt-text="Mac için Visual Studio başlangıç ekranında yeni düğme":::

1. <span data-ttu-id="36b6c-123">**Yeni proje** Iletişim kutusunda **Web ve konsol** düğümü altında **uygulama** ' yı seçin.</span><span class="sxs-lookup"><span data-stu-id="36b6c-123">In the **New Project** dialog, select **App** under the **Web and Console** node.</span></span> <span data-ttu-id="36b6c-124">**Konsol uygulaması** şablonunu seçin ve **İleri**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="36b6c-124">Select the **Console Application** template, and select **Next**.</span></span>

   :::image type="content" source="media/with-visual-studio-mac/visual-studio-mac-new-dialog.png" alt-text="Yeni proje şablonları listesi":::

1. <span data-ttu-id="36b6c-126">**Yeni konsol uygulamanızı yapılandırma** Iletişim kutusunun **hedef çerçeve** açılır penceresinde, **.NET Core 3,1**' ı seçin ve **İleri**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="36b6c-126">In the **Target Framework** drop-down of the **Configure your new Console Application** dialog, select **.NET Core 3.1**, and select **Next**.</span></span>

   :::image type="content" source="media/with-visual-studio-mac/target-framework.png" alt-text="Hedef Framework 'Ü seçin":::

1. <span data-ttu-id="36b6c-128">**Proje adı**Için "HelloWorld" yazın ve **Oluştur**' u seçin.</span><span class="sxs-lookup"><span data-stu-id="36b6c-128">Type "HelloWorld" for the **Project Name**, and select **Create**.</span></span>

   :::image type="content" source="media/with-visual-studio-mac/visual-studio-mac-new-options.png" alt-text="Yeni konsol uygulamanızı yapılandırma iletişim kutusu":::

<span data-ttu-id="36b6c-130">Şablon basit bir "Merhaba Dünya" uygulaması oluşturur.</span><span class="sxs-lookup"><span data-stu-id="36b6c-130">The template creates a simple "Hello World" application.</span></span> <span data-ttu-id="36b6c-131"><xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType>"Merhaba Dünya!" öğesini göstermek için yöntemini çağırır</span><span class="sxs-lookup"><span data-stu-id="36b6c-131">It calls the <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> method to display "Hello World!"</span></span> <span data-ttu-id="36b6c-132">, Terminal penceresinde.</span><span class="sxs-lookup"><span data-stu-id="36b6c-132">in the terminal window.</span></span>

<span data-ttu-id="36b6c-133">Şablon kodu, `Program` `Main` bağımsız değişken olarak bir diziyi alan tek bir yöntemi olan sınıfını tanımlar <xref:System.String> :</span><span class="sxs-lookup"><span data-stu-id="36b6c-133">The template code defines a class, `Program`, with a single method, `Main`, that takes a <xref:System.String> array as an argument:</span></span>

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

<span data-ttu-id="36b6c-134">`Main` uygulama giriş noktası, uygulamayı başlattığında çalışma zamanı tarafından otomatik olarak çağrılan yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="36b6c-134">`Main` is the application entry point, the method that's called automatically by the runtime when it launches the application.</span></span> <span data-ttu-id="36b6c-135">Uygulama başlatıldığında sağlanan tüm komut satırı bağımsız değişkenleri `args` dizide kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="36b6c-135">Any command-line arguments supplied when the application is launched are available in the `args` array.</span></span>

## <a name="run-the-app"></a><span data-ttu-id="36b6c-136">Uygulamayı çalıştırma</span><span class="sxs-lookup"><span data-stu-id="36b6c-136">Run the app</span></span>

1. <span data-ttu-id="36b6c-137"><kbd>⌥</kbd><kbd>⌘</kbd><kbd>↵</kbd> <kbd>option</kbd> + <kbd>command</kbd> + Uygulamayı hata ayıklamadan çalıştırmak için ⌥ ⌘ ↵ (Option komut<kbd>ENTER</kbd>) tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="36b6c-137">Press <kbd>⌥</kbd><kbd>⌘</kbd><kbd>↵</kbd> (<kbd>option</kbd>+<kbd>command</kbd>+<kbd>enter</kbd>) to run the app without debugging.</span></span>

   :::image type="content" source="media/with-visual-studio-mac/visual-studio-mac-output.png" alt-text="Terminal Merhaba Dünya gösterir!":::

1. <span data-ttu-id="36b6c-139">**Terminal** penceresini kapatın.</span><span class="sxs-lookup"><span data-stu-id="36b6c-139">Close the **Terminal** window.</span></span>

## <a name="enhance-the-app"></a><span data-ttu-id="36b6c-140">Uygulamayı geliştirin</span><span class="sxs-lookup"><span data-stu-id="36b6c-140">Enhance the app</span></span>

<span data-ttu-id="36b6c-141">Kullanıcıya adını istemek ve Tarih ve saat ile birlikte göstermek için uygulamayı geliştirin.</span><span class="sxs-lookup"><span data-stu-id="36b6c-141">Enhance the application to prompt the user for their name and display it along with the date and time.</span></span>

1. <span data-ttu-id="36b6c-142">*Program.cs*' de, `Main` aşağıdaki kodla birlikte çağıran satırı olan yönteminin içeriğini değiştirin `Console.WriteLine` :</span><span class="sxs-lookup"><span data-stu-id="36b6c-142">In *Program.cs*, replace the contents of the `Main` method, which is the line that calls `Console.WriteLine`, with the following code:</span></span>

   :::code language="csharp" source="./snippets/with-visual-studio/csharp/Program.cs" id="MainMethod":::

   <span data-ttu-id="36b6c-143">Bu kod, konsol penceresinde bir istem görüntüler ve ardından <kbd>ENTER</kbd> tuşuna basarak Kullanıcı bir dize girene kadar bekler.</span><span class="sxs-lookup"><span data-stu-id="36b6c-143">This code displays a prompt in the console window and waits until the user enters a string followed by the <kbd>enter</kbd> key.</span></span> <span data-ttu-id="36b6c-144">Bu dizeyi adlı bir değişkende depolar `name` .</span><span class="sxs-lookup"><span data-stu-id="36b6c-144">It stores this string in a variable named `name`.</span></span> <span data-ttu-id="36b6c-145">Ayrıca <xref:System.DateTime.Now?displayProperty=nameWithType> , geçerli yerel saati içeren özelliğinin değerini alır ve bunu adlı bir değişkene atar `date` .</span><span class="sxs-lookup"><span data-stu-id="36b6c-145">It also retrieves the value of the <xref:System.DateTime.Now?displayProperty=nameWithType> property, which contains the current local time, and assigns it to a variable named `date`.</span></span> <span data-ttu-id="36b6c-146">Bu değerleri konsol penceresinde görüntüler.</span><span class="sxs-lookup"><span data-stu-id="36b6c-146">And it displays these values in the console window.</span></span> <span data-ttu-id="36b6c-147">Son olarak, konsol penceresinde bir istem görüntüler ve <xref:System.Console.ReadKey(System.Boolean)?displayProperty=nameWithType> Kullanıcı girişini beklemek için yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="36b6c-147">Finally, it displays a prompt in the console window and calls the <xref:System.Console.ReadKey(System.Boolean)?displayProperty=nameWithType> method to wait for user input.</span></span>

   <span data-ttu-id="36b6c-148">`\n`Bir yeni satır karakterini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="36b6c-148">The `\n` represents a newline character.</span></span>

   <span data-ttu-id="36b6c-149">`$`Bir dizenin önünde dolar işareti (), değişken adları gibi ifadeleri dizedeki küme ayraçları içine koymanıza imkan tanır.</span><span class="sxs-lookup"><span data-stu-id="36b6c-149">The dollar sign (`$`) in front of a string lets you put expressions such as variable names in curly braces in the string.</span></span> <span data-ttu-id="36b6c-150">İfade değeri, ifadenin yerine dizeye eklenir.</span><span class="sxs-lookup"><span data-stu-id="36b6c-150">The expression value is inserted into the string in place of the expression.</span></span> <span data-ttu-id="36b6c-151">Bu söz dizimi, [enterpolasyonlu dizeler](../../csharp/language-reference/tokens/interpolated.md)olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="36b6c-151">This syntax is referred to as [interpolated strings](../../csharp/language-reference/tokens/interpolated.md).</span></span>

1. <span data-ttu-id="36b6c-152">Uygulamayı çalıştırmak için <kbd>⌥</kbd><kbd>⌘</kbd><kbd>↵</kbd> (<kbd>seçenek</kbd> + <kbd>komut</kbd> + <kbd>ENTER</kbd>) tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="36b6c-152">Press <kbd>⌥</kbd><kbd>⌘</kbd><kbd>↵</kbd> (<kbd>option</kbd>+<kbd>command</kbd>+<kbd>enter</kbd>) to run the app.</span></span>

1. <span data-ttu-id="36b6c-153">Bir ad girip <kbd>ENTER</kbd>tuşuna basarak istemi yanıtlayın.</span><span class="sxs-lookup"><span data-stu-id="36b6c-153">Respond to the prompt by entering a name and pressing <kbd>enter</kbd>.</span></span>

   :::image type="content" source="media/with-visual-studio-mac/hello-world-update.png" alt-text="Terminal değiştirilen program çıktısını gösterir":::

1. <span data-ttu-id="36b6c-155">Terminali kapatın.</span><span class="sxs-lookup"><span data-stu-id="36b6c-155">Close the terminal.</span></span>

## <a name="next-steps"></a><span data-ttu-id="36b6c-156">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="36b6c-156">Next steps</span></span>

<span data-ttu-id="36b6c-157">Bu öğreticide, bir .NET Core konsol uygulaması oluşturdunuz.</span><span class="sxs-lookup"><span data-stu-id="36b6c-157">In this tutorial, you created a .NET Core console application.</span></span> <span data-ttu-id="36b6c-158">Sonraki öğreticide, uygulamada hata ayıklaması yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="36b6c-158">In the next tutorial, you debug the app.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="36b6c-159">Visual Studio 'da bir .NET Core konsol uygulamasında hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="36b6c-159">Debug a .NET Core console application in Visual Studio</span></span>](debugging-with-visual-studio-mac.md)
