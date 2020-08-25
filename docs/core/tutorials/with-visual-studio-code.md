---
title: Visual Studio Code kullanarak bir .NET Core konsol uygulaması oluşturma
description: Visual Studio Code ve .NET Core CLI kullanarak .NET Core konsol uygulaması oluşturmayı öğrenin.
ms.date: 05/22/2020
ms.openlocfilehash: e936c23d8525e42a9d2781cc680067c9da2ce42f
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88811932"
---
# <a name="tutorial-create-a-net-core-console-application-using-visual-studio-code"></a><span data-ttu-id="931bb-103">Öğretici: Visual Studio Code kullanarak bir .NET Core konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="931bb-103">Tutorial: Create a .NET Core console application using Visual Studio Code</span></span>

<span data-ttu-id="931bb-104">Bu öğreticide, Visual Studio Code ve .NET Core CLI kullanılarak .NET Core konsol uygulaması oluşturma ve çalıştırma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="931bb-104">This tutorial shows how to create and run a .NET Core console application by using Visual Studio Code and the .NET Core CLI.</span></span> <span data-ttu-id="931bb-105">Proje oluşturma, derleme ve çalıştırma gibi proje görevleri, .NET Core CLI kullanılarak yapılır.</span><span class="sxs-lookup"><span data-stu-id="931bb-105">Project tasks, such as creating, compiling, and running a project are done by using the .NET Core CLI.</span></span> <span data-ttu-id="931bb-106">Bu öğreticiyi, farklı bir kod Düzenleyicisi ile izleyebilir ve tercih ediyorsanız komutları terminalde çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="931bb-106">You can follow this tutorial with a different code editor and run commands in a terminal if you prefer.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="931bb-107">Ön koşullar</span><span class="sxs-lookup"><span data-stu-id="931bb-107">Prerequisites</span></span>

1. <span data-ttu-id="931bb-108">[C# uzantısı](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp) yüklü [Visual Studio Code](https://code.visualstudio.com/) .</span><span class="sxs-lookup"><span data-stu-id="931bb-108">[Visual Studio Code](https://code.visualstudio.com/) with the [C# extension](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp) installed.</span></span> <span data-ttu-id="931bb-109">Visual Studio Code uzantıları nasıl yükleyeceğiniz hakkında daha fazla bilgi için bkz. [vs Code uzantısı marketi](https://code.visualstudio.com/docs/editor/extension-gallery).</span><span class="sxs-lookup"><span data-stu-id="931bb-109">For information about how to install extensions on Visual Studio Code, see [VS Code Extension Marketplace](https://code.visualstudio.com/docs/editor/extension-gallery).</span></span>
2. <span data-ttu-id="931bb-110">[.NET Core 3,1 SDK veya üzeri](https://dotnet.microsoft.com/download)</span><span class="sxs-lookup"><span data-stu-id="931bb-110">The [.NET Core 3.1 SDK or later](https://dotnet.microsoft.com/download)</span></span>

## <a name="create-the-app"></a><span data-ttu-id="931bb-111">Uygulama oluşturma</span><span class="sxs-lookup"><span data-stu-id="931bb-111">Create the app</span></span>

<span data-ttu-id="931bb-112">"HelloWorld" adlı bir .NET Core konsol uygulaması projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="931bb-112">Create a .NET Core console app project named "HelloWorld".</span></span>

1. <span data-ttu-id="931bb-113">Visual Studio Code’u başlatma.</span><span class="sxs-lookup"><span data-stu-id="931bb-113">Start Visual Studio Code.</span></span>

1. <span data-ttu-id="931bb-114">Ana menüden **Dosya**  >  **açma klasörünü** (**File**  >  MacOS üzerinde dosya**Aç...** ) seçin.</span><span class="sxs-lookup"><span data-stu-id="931bb-114">Select **File** > **Open Folder** (**File** > **Open...** on macOS) from the main menu.</span></span>

1. <span data-ttu-id="931bb-115">**Klasörü aç** iletişim kutusunda bir *HelloWorld* klasörü oluşturun ve **Klasör Seç** ' e tıklayın (MacOS üzerinde**açın** ).</span><span class="sxs-lookup"><span data-stu-id="931bb-115">In the **Open Folder** dialog, create a *HelloWorld* folder and click **Select Folder** (**Open** on macOS).</span></span>

   <span data-ttu-id="931bb-116">Klasör adı, varsayılan olarak proje adı ve ad alanı adı olur.</span><span class="sxs-lookup"><span data-stu-id="931bb-116">The folder name becomes the project name and the namespace name by default.</span></span> <span data-ttu-id="931bb-117">Daha sonra, proje ad alanının olduğunu varsayan öğreticide kod ekleyeceksiniz `HelloWorld` .</span><span class="sxs-lookup"><span data-stu-id="931bb-117">You'll add code later in the tutorial that assumes the project namespace is `HelloWorld`.</span></span>

1. <span data-ttu-id="931bb-118">Ana menüden **Terminal görünümü ' nu** seçerek **View**Visual Studio Code açın  >  **Terminal** .</span><span class="sxs-lookup"><span data-stu-id="931bb-118">Open the **Terminal** in Visual Studio Code by selecting **View** > **Terminal** from the main menu.</span></span>

   <span data-ttu-id="931bb-119">**Terminal** , *HelloWorld* klasöründe komut istemiyle açılır.</span><span class="sxs-lookup"><span data-stu-id="931bb-119">The **Terminal** opens with the command prompt in the *HelloWorld* folder.</span></span>

1. <span data-ttu-id="931bb-120">**Terminalde**aşağıdaki komutu girin:</span><span class="sxs-lookup"><span data-stu-id="931bb-120">In the **Terminal**, enter the following command:</span></span>

   ```dotnetcli
   dotnet new console
   ```

<span data-ttu-id="931bb-121">Şablon basit bir "Merhaba Dünya" uygulaması oluşturur.</span><span class="sxs-lookup"><span data-stu-id="931bb-121">The template creates a simple "Hello World" application.</span></span> <span data-ttu-id="931bb-122"><xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType>Konsol penceresinde "" görüntülenmesini sağlamak için yöntemini çağırır :::no-loc text="Hello World!"::: .</span><span class="sxs-lookup"><span data-stu-id="931bb-122">It calls the <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> method to display ":::no-loc text="Hello World!":::" in the console window.</span></span>

<span data-ttu-id="931bb-123">Şablon kodu, `Program` `Main` bağımsız değişken olarak bir diziyi alan tek bir yöntemi olan sınıfını tanımlar <xref:System.String> :</span><span class="sxs-lookup"><span data-stu-id="931bb-123">The template code defines a class, `Program`, with a single method, `Main`, that takes a <xref:System.String> array as an argument:</span></span>

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

<span data-ttu-id="931bb-124">`Main` uygulama giriş noktası, uygulamayı başlattığında çalışma zamanı tarafından otomatik olarak çağrılan yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="931bb-124">`Main` is the application entry point, the method that's called automatically by the runtime when it launches the application.</span></span> <span data-ttu-id="931bb-125">Uygulama başlatıldığında sağlanan herhangi bir komut satırı bağımsız değişkeni, *args* dizisinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="931bb-125">Any command-line arguments supplied when the application is launched are available in the *args* array.</span></span>

## <a name="run-the-app"></a><span data-ttu-id="931bb-126">Uygulamayı çalıştırma</span><span class="sxs-lookup"><span data-stu-id="931bb-126">Run the app</span></span>

<span data-ttu-id="931bb-127">**Terminalde**aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="931bb-127">Run the following command in the **Terminal**:</span></span>

```dotnetcli
dotnet run
```

<span data-ttu-id="931bb-128">Program "Merhaba Dünya!" görüntülüyor</span><span class="sxs-lookup"><span data-stu-id="931bb-128">The program displays "Hello World!"</span></span> <span data-ttu-id="931bb-129">ve bitiyor.</span><span class="sxs-lookup"><span data-stu-id="931bb-129">and ends.</span></span>

![DotNet Run komutu](media/with-visual-studio-code/dotnet-run-command.png)

## <a name="enhance-the-app"></a><span data-ttu-id="931bb-131">Uygulamayı geliştirin</span><span class="sxs-lookup"><span data-stu-id="931bb-131">Enhance the app</span></span>

<span data-ttu-id="931bb-132">Kullanıcıya adını istemek ve Tarih ve saat ile birlikte göstermek için uygulamayı geliştirin.</span><span class="sxs-lookup"><span data-stu-id="931bb-132">Enhance the application to prompt the user for their name and display it along with the date and time.</span></span>

1. <span data-ttu-id="931bb-133">Üzerine tıklayarak *program.cs* açın.</span><span class="sxs-lookup"><span data-stu-id="931bb-133">Open *Program.cs* by clicking on it.</span></span>

   <span data-ttu-id="931bb-134">Visual Studio Code bir C# dosyasını ilk açışınızda, [Omnisharp](https://www.omnisharp.net/) düzenleyicide yüklenir.</span><span class="sxs-lookup"><span data-stu-id="931bb-134">The first time you open a C# file in Visual Studio Code, [OmniSharp](https://www.omnisharp.net/) loads in the editor.</span></span>

   ![Program.cs dosyasını açın](media/with-visual-studio-code/open-program-cs.png)

1. <span data-ttu-id="931bb-136">Visual Studio Code, uygulamanızda derlemek ve hata ayıklamak için eksik varlıkları eklemenizi istediğinizde **Evet** ' i seçin.</span><span class="sxs-lookup"><span data-stu-id="931bb-136">Select **Yes** when Visual Studio Code prompts you to add the missing assets to build and debug your app.</span></span>

   ![Eksik varlıklar için istem](media/with-visual-studio-code/missing-assets.png)

1. <span data-ttu-id="931bb-138">`Main`Aşağıdaki kodla, çağıran satır olan *program.cs*içindeki yönteminin içeriğini değiştirin `Console.WriteLine` :</span><span class="sxs-lookup"><span data-stu-id="931bb-138">Replace the contents of the `Main` method in *Program.cs*, which is the line that calls `Console.WriteLine`, with the following code:</span></span>

   :::code language="csharp" source="./snippets/with-visual-studio/csharp/Program.cs" id="MainMethod":::

   <span data-ttu-id="931bb-139">Bu kod, konsol penceresinde bir istem görüntüler ve ardından <kbd>ENTER</kbd> tuşuna basarak Kullanıcı bir dize girene kadar bekler.</span><span class="sxs-lookup"><span data-stu-id="931bb-139">This code displays a prompt in the console window and waits until the user enters a string followed by the <kbd>Enter</kbd> key.</span></span> <span data-ttu-id="931bb-140">Bu dizeyi adlı bir değişkende depolar `name` .</span><span class="sxs-lookup"><span data-stu-id="931bb-140">It stores this string in a variable named `name`.</span></span> <span data-ttu-id="931bb-141">Ayrıca <xref:System.DateTime.Now?displayProperty=nameWithType> , geçerli yerel saati içeren özelliğinin değerini alır ve bunu adlı bir değişkene atar `date` .</span><span class="sxs-lookup"><span data-stu-id="931bb-141">It also retrieves the value of the <xref:System.DateTime.Now?displayProperty=nameWithType> property, which contains the current local time, and assigns it to a variable named `date`.</span></span> <span data-ttu-id="931bb-142">Bu değerleri konsol penceresinde görüntüler.</span><span class="sxs-lookup"><span data-stu-id="931bb-142">And it displays these values in the console window.</span></span> <span data-ttu-id="931bb-143">Son olarak, konsol penceresinde bir istem görüntüler ve <xref:System.Console.ReadKey(System.Boolean)?displayProperty=nameWithType> Kullanıcı girişini beklemek için yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="931bb-143">Finally, it displays a prompt in the console window and calls the <xref:System.Console.ReadKey(System.Boolean)?displayProperty=nameWithType> method to wait for user input.</span></span>

   <span data-ttu-id="931bb-144">`\n`Bir yeni satır karakterini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="931bb-144">The `\n` represents a newline character.</span></span>

   <span data-ttu-id="931bb-145">`$`Bir dizenin önünde dolar işareti (), değişken adları gibi ifadeleri dizedeki küme ayraçları içine koymanıza imkan tanır.</span><span class="sxs-lookup"><span data-stu-id="931bb-145">The dollar sign (`$`) in front of a string lets you put expressions such as variable names in curly braces in the string.</span></span> <span data-ttu-id="931bb-146">İfade değeri, ifadenin yerine dizeye eklenir.</span><span class="sxs-lookup"><span data-stu-id="931bb-146">The expression value is inserted into the string in place of the expression.</span></span> <span data-ttu-id="931bb-147">Bu söz dizimi, [enterpolasyonlu dizeler](../../csharp/language-reference/tokens/interpolated.md)olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="931bb-147">This syntax is referred to as [interpolated strings](../../csharp/language-reference/tokens/interpolated.md).</span></span>

1. <span data-ttu-id="931bb-148">Yaptığınız değişiklikleri kaydedin.</span><span class="sxs-lookup"><span data-stu-id="931bb-148">Save your changes.</span></span>

   > [!IMPORTANT]
   > <span data-ttu-id="931bb-149">Visual Studio Code, değişiklikleri açıkça kaydetmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="931bb-149">In Visual Studio Code, you have to explicitly save changes.</span></span> <span data-ttu-id="931bb-150">Visual Studio 'dan farklı olarak, bir uygulamayı derleyip çalıştırdığınızda dosya değişiklikleri otomatik olarak kaydedilmez.</span><span class="sxs-lookup"><span data-stu-id="931bb-150">Unlike Visual Studio, file changes are not automatically saved when you build and run an app.</span></span>

1. <span data-ttu-id="931bb-151">Programı yeniden çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="931bb-151">Run the program again:</span></span>

   ```dotnetcli
   dotnet run
   ```

1. <span data-ttu-id="931bb-152">Bir ad girip <kbd>ENTER</kbd> tuşuna basarak istemi yanıtlayın.</span><span class="sxs-lookup"><span data-stu-id="931bb-152">Respond to the prompt by entering a name and pressing the <kbd>Enter</kbd> key.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-code/run-modified-program.png" alt-text="Değiştirilen program çıkışındaki Terminal penceresi":::

1. <span data-ttu-id="931bb-154">Programdan çıkmak için herhangi bir tuşa basın.</span><span class="sxs-lookup"><span data-stu-id="931bb-154">Press any key to exit the program.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="931bb-155">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="931bb-155">Additional resources</span></span>

- [<span data-ttu-id="931bb-156">Visual Studio Code ayarlama</span><span class="sxs-lookup"><span data-stu-id="931bb-156">Setting up Visual Studio Code</span></span>](https://code.visualstudio.com/docs/setup/setup-overview)

## <a name="next-steps"></a><span data-ttu-id="931bb-157">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="931bb-157">Next steps</span></span>

<span data-ttu-id="931bb-158">Bu öğreticide, bir .NET Core konsol uygulaması oluşturdunuz.</span><span class="sxs-lookup"><span data-stu-id="931bb-158">In this tutorial, you created a .NET Core console application.</span></span> <span data-ttu-id="931bb-159">Sonraki öğreticide, uygulamada hata ayıklaması yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="931bb-159">In the next tutorial, you debug the app.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="931bb-160">Visual Studio Code kullanarak bir .NET Core konsol uygulamasında hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="931bb-160">Debug a .NET Core console application using Visual Studio Code</span></span>](debugging-with-visual-studio-code.md)
