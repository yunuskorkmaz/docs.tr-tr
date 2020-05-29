---
title: Visual Studio Code kullanarak .NET Core ile bir konsol uygulaması oluşturma
description: Visual Studio Code ve .NET Core CLI kullanarak .NET Core konsol uygulaması oluşturmayı öğrenin.
ms.date: 05/22/2020
ms.openlocfilehash: 673c4a639a2cab26261b7cdafd5d8e20acfafb94
ms.sourcegitcommit: 71b8f5a2108a0f1a4ef1d8d75c5b3e129ec5ca1e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/29/2020
ms.locfileid: "84201702"
---
# <a name="tutorial-create-a-console-application-with-net-core-using-visual-studio-code"></a><span data-ttu-id="8f94a-103">Öğretici: Visual Studio Code kullanarak .NET Core ile bir konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="8f94a-103">Tutorial: Create a console application with .NET Core using Visual Studio Code</span></span>

<span data-ttu-id="8f94a-104">Bu öğreticide, Visual Studio Code ve .NET Core CLI kullanılarak .NET Core konsol uygulaması oluşturma ve çalıştırma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="8f94a-104">This tutorial shows how to create and run a .NET Core console application by using Visual Studio Code and the .NET Core CLI.</span></span> <span data-ttu-id="8f94a-105">Proje oluşturma, derleme ve çalıştırma gibi proje görevleri CLı kullanılarak yapılır, bu nedenle bu öğreticiyi bir kod Düzenleyicisi ile izleyebilir ve tercih ediyorsanız komutları terminalde çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8f94a-105">Project tasks, such as creating, compiling, and running a project are done by using the CLI, so you can follow this tutorial with a different code editor and run commands in a terminal if you prefer.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="8f94a-106">Ön koşullar</span><span class="sxs-lookup"><span data-stu-id="8f94a-106">Prerequisites</span></span>

1. <span data-ttu-id="8f94a-107">[C# uzantısı](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp) yüklü [Visual Studio Code](https://code.visualstudio.com/) .</span><span class="sxs-lookup"><span data-stu-id="8f94a-107">[Visual Studio Code](https://code.visualstudio.com/) with the [C# extension](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp) installed.</span></span> <span data-ttu-id="8f94a-108">Visual Studio Code uzantıları nasıl yükleyeceğiniz hakkında daha fazla bilgi için bkz. [vs Code uzantısı marketi](https://code.visualstudio.com/docs/editor/extension-gallery).</span><span class="sxs-lookup"><span data-stu-id="8f94a-108">For information about how to install extensions on Visual Studio Code, see [VS Code Extension Marketplace](https://code.visualstudio.com/docs/editor/extension-gallery).</span></span>
2. <span data-ttu-id="8f94a-109">[.NET Core 3,1 SDK veya üzeri](https://dotnet.microsoft.com/download)</span><span class="sxs-lookup"><span data-stu-id="8f94a-109">The [.NET Core 3.1 SDK or later](https://dotnet.microsoft.com/download)</span></span>

## <a name="create-the-app"></a><span data-ttu-id="8f94a-110">Uygulama oluşturma</span><span class="sxs-lookup"><span data-stu-id="8f94a-110">Create the app</span></span>

1. <span data-ttu-id="8f94a-111">Visual Studio Code'u açın.</span><span class="sxs-lookup"><span data-stu-id="8f94a-111">Open Visual Studio Code.</span></span>

1. <span data-ttu-id="8f94a-112">Bir proje oluşturun.</span><span class="sxs-lookup"><span data-stu-id="8f94a-112">Create a project.</span></span>

   1. <span data-ttu-id="8f94a-113">**Dosya**  >  **Aç klasör**aç... ' ı seçin, / **Open...** ana menüden bir *HelloWorld* klasörü oluşturun ve klasör aç **Seç**' e tıklayın / **Open**.</span><span class="sxs-lookup"><span data-stu-id="8f94a-113">Select **File** > **Open Folder**/**Open...** from the main menu, create a *HelloWorld* folder, and click **Select Folder**/**Open**.</span></span>

      <span data-ttu-id="8f94a-114">Klasör adı, varsayılan olarak proje adı ve ad alanı adı olur.</span><span class="sxs-lookup"><span data-stu-id="8f94a-114">The folder name becomes the project name and the namespace name by default.</span></span> <span data-ttu-id="8f94a-115">Daha sonra, proje ad alanının olduğunu varsayan öğreticide kod ekleyeceksiniz `HelloWorld` .</span><span class="sxs-lookup"><span data-stu-id="8f94a-115">You'll add code later in the tutorial that assumes the project namespace is `HelloWorld`.</span></span>

   1. <span data-ttu-id="8f94a-116">Ana menüden **Terminal görünümü ' nu** seçerek **View**Visual Studio Code açın  >  **Terminal** .</span><span class="sxs-lookup"><span data-stu-id="8f94a-116">Open the **Terminal** in Visual Studio Code by selecting **View** > **Terminal** from the main menu.</span></span>

      <span data-ttu-id="8f94a-117">**Terminal** , *HelloWorld* klasöründe komut istemiyle açılır.</span><span class="sxs-lookup"><span data-stu-id="8f94a-117">The **Terminal** opens with the command prompt in the *HelloWorld* folder.</span></span>

   1. <span data-ttu-id="8f94a-118">**Terminalde**aşağıdaki komutu girin:</span><span class="sxs-lookup"><span data-stu-id="8f94a-118">In the **Terminal**, enter the following command:</span></span>

      ```dotnetcli
      dotnet new console
      ```

<span data-ttu-id="8f94a-119">.NET Core konsol uygulaması şablonu, `Program` `Main` bağımsız değişken olarak bir dizi alan tek bir yöntemle bir sınıfını tanımlar <xref:System.String> .</span><span class="sxs-lookup"><span data-stu-id="8f94a-119">The Console Application template for .NET Core defines a class, `Program`, with a single method, `Main`, that takes a <xref:System.String> array as an argument.</span></span> <span data-ttu-id="8f94a-120">*Program.cs* dosyası aşağıdaki koda sahiptir:</span><span class="sxs-lookup"><span data-stu-id="8f94a-120">The *Program.cs* file has the following code:</span></span>

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

<span data-ttu-id="8f94a-121">`Main`uygulama giriş noktası, uygulamayı başlattığında çalışma zamanı tarafından otomatik olarak çağrılan yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="8f94a-121">`Main` is the application entry point, the method that's called automatically by the runtime when it launches the application.</span></span> <span data-ttu-id="8f94a-122">Uygulama başlatıldığında sağlanan herhangi bir komut satırı bağımsız değişkeni, *args* dizisinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="8f94a-122">Any command-line arguments supplied when the application is launched are available in the *args* array.</span></span>

<span data-ttu-id="8f94a-123">Şablon, <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> "Merhaba Dünya!" öğesini göstermek için yöntemi çağıran basit bir uygulama oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8f94a-123">The template creates a simple application that calls the <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> method to display "Hello World!"</span></span> <span data-ttu-id="8f94a-124">Konsol penceresinde.</span><span class="sxs-lookup"><span data-stu-id="8f94a-124">in the console window.</span></span>

## <a name="run-the-app"></a><span data-ttu-id="8f94a-125">Uygulamayı çalıştırma</span><span class="sxs-lookup"><span data-stu-id="8f94a-125">Run the app</span></span>

<span data-ttu-id="8f94a-126">**Terminalde**aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="8f94a-126">Run the following command in the **Terminal**:</span></span>

```dotnetcli
dotnet run
```

<span data-ttu-id="8f94a-127">Program "Merhaba Dünya!" görüntülüyor</span><span class="sxs-lookup"><span data-stu-id="8f94a-127">The program displays "Hello World!"</span></span> <span data-ttu-id="8f94a-128">ve bitiyor.</span><span class="sxs-lookup"><span data-stu-id="8f94a-128">and ends.</span></span>

![DotNet Run komutu](media/with-visual-studio-code/dotnet-run-command.png)

## <a name="enhance-the-app"></a><span data-ttu-id="8f94a-130">Uygulamayı geliştirin</span><span class="sxs-lookup"><span data-stu-id="8f94a-130">Enhance the app</span></span>

<span data-ttu-id="8f94a-131">Kullanıcıya adını istemek ve Tarih ve saat ile birlikte göstermek için uygulamayı geliştirin.</span><span class="sxs-lookup"><span data-stu-id="8f94a-131">Enhance the application to prompt the user for their name and display it along with the date and time.</span></span>

1. <span data-ttu-id="8f94a-132">Üzerine tıklayarak *program.cs* açın.</span><span class="sxs-lookup"><span data-stu-id="8f94a-132">Open *Program.cs* by clicking on it.</span></span>

   <span data-ttu-id="8f94a-133">Visual Studio Code bir C# dosyasını ilk açışınızda, [Omnisharp](https://www.omnisharp.net/) düzenleyicide yüklenir.</span><span class="sxs-lookup"><span data-stu-id="8f94a-133">The first time you open a C# file in Visual Studio Code, [OmniSharp](https://www.omnisharp.net/) loads in the editor.</span></span>

   ![Program.cs dosyasını açın](media/with-visual-studio-code/open-program-cs.png)

1. <span data-ttu-id="8f94a-135">Visual Studio Code, uygulamanızda derlemek ve hata ayıklamak için eksik varlıkları eklemenizi istediğinizde **Evet** ' i seçin.</span><span class="sxs-lookup"><span data-stu-id="8f94a-135">Select **Yes** when Visual Studio Code prompts you to add the missing assets to build and debug your app.</span></span>

   ![Eksik varlıklar için istem](media/with-visual-studio-code/missing-assets.png)

1. <span data-ttu-id="8f94a-137">`Main`Aşağıdaki kodla, şu anda yalnızca çağıran satırı olan *program.cs*içindeki yönteminin içeriğini değiştirin `Console.WriteLine` :</span><span class="sxs-lookup"><span data-stu-id="8f94a-137">Replace the contents of the `Main` method in *Program.cs*, which is currently just the line that calls `Console.WriteLine`, with the following code:</span></span>

   :::code language="csharp" source="./snippets/with-visual-studio/csharp/Program.cs" id="Snippet1":::

   <span data-ttu-id="8f94a-138">Bu kod "adınız nedir?" görüntüler</span><span class="sxs-lookup"><span data-stu-id="8f94a-138">This code displays "What is your name?"</span></span> <span data-ttu-id="8f94a-139">Konsol penceresinde ve ardından **ENTER** tuşuna basarak Kullanıcı bir dize girene kadar bekler.</span><span class="sxs-lookup"><span data-stu-id="8f94a-139">in the console window and waits until the user enters a string followed by the **Enter** key.</span></span> <span data-ttu-id="8f94a-140">Bu dizeyi adlı bir değişkende depolar `name` .</span><span class="sxs-lookup"><span data-stu-id="8f94a-140">It stores this string in a variable named `name`.</span></span> <span data-ttu-id="8f94a-141">Ayrıca <xref:System.DateTime.Now?displayProperty=nameWithType> , geçerli yerel saati içeren özelliğinin değerini alır ve bunu adlı bir değişkene atar `date` .</span><span class="sxs-lookup"><span data-stu-id="8f94a-141">It also retrieves the value of the <xref:System.DateTime.Now?displayProperty=nameWithType> property, which contains the current local time, and assigns it to a variable named `date`.</span></span> <span data-ttu-id="8f94a-142">Son olarak, bu değerleri konsol penceresinde görüntüler.</span><span class="sxs-lookup"><span data-stu-id="8f94a-142">Finally, it displays these values in the console window.</span></span>

   <span data-ttu-id="8f94a-143">`\n`Bir yeni satır karakterini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="8f94a-143">The `\n` represents a newline character.</span></span>

   <span data-ttu-id="8f94a-144">`$`Bir dizenin önünde dolar işareti (), değişken adları gibi ifadeleri dizedeki küme ayraçları içine koymanıza imkan tanır.</span><span class="sxs-lookup"><span data-stu-id="8f94a-144">The dollar sign (`$`) in front of a string lets you put expressions such as variable names in curly braces in the string.</span></span> <span data-ttu-id="8f94a-145">İfade değeri, ifadenin yerine dizeye eklenir.</span><span class="sxs-lookup"><span data-stu-id="8f94a-145">The expression value is inserted into the string in place of the expression.</span></span> <span data-ttu-id="8f94a-146">Bu söz dizimi, [enterpolasyonlu dizeler](../../csharp/language-reference/tokens/interpolated.md)olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="8f94a-146">This syntax is referred to as [interpolated strings](../../csharp/language-reference/tokens/interpolated.md).</span></span>

1. <span data-ttu-id="8f94a-147">Yaptığınız değişiklikleri kaydedin.</span><span class="sxs-lookup"><span data-stu-id="8f94a-147">Save your changes.</span></span>

   > [!IMPORTANT]
   > <span data-ttu-id="8f94a-148">Visual Studio Code, değişiklikleri açıkça kaydetmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="8f94a-148">In Visual Studio Code, you have to explicitly save changes.</span></span> <span data-ttu-id="8f94a-149">Visual Studio 'dan farklı olarak, bir uygulamayı derleyip çalıştırdığınızda dosya değişiklikleri otomatik olarak kaydedilmez.</span><span class="sxs-lookup"><span data-stu-id="8f94a-149">Unlike Visual Studio, file changes are not automatically saved when you build and run an app.</span></span>

1. <span data-ttu-id="8f94a-150">Programı yeniden çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="8f94a-150">Run the program again:</span></span>

   ```dotnetcli
   dotnet run
   ```

1. <span data-ttu-id="8f94a-151">Bir ad girip **ENTER** tuşuna basarak istemi yanıtlayın.</span><span class="sxs-lookup"><span data-stu-id="8f94a-151">Respond to the prompt by entering a name and pressing the **Enter** key.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-code/run-modified-program.png" alt-text="Değiştirilen program çıkışındaki Terminal penceresi":::

1. <span data-ttu-id="8f94a-153">Programdan çıkmak için herhangi bir tuşa basın.</span><span class="sxs-lookup"><span data-stu-id="8f94a-153">Press any key to exit the program.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="8f94a-154">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="8f94a-154">Additional resources</span></span>

- [<span data-ttu-id="8f94a-155">Visual Studio Code ayarlama</span><span class="sxs-lookup"><span data-stu-id="8f94a-155">Setting up Visual Studio Code</span></span>](https://code.visualstudio.com/docs/setup/setup-overview)

## <a name="next-steps"></a><span data-ttu-id="8f94a-156">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="8f94a-156">Next steps</span></span>

<span data-ttu-id="8f94a-157">Bu öğreticide, bir .NET Core uygulaması oluşturdunuz.</span><span class="sxs-lookup"><span data-stu-id="8f94a-157">In this tutorial, you created a .NET Core application.</span></span> <span data-ttu-id="8f94a-158">Sonraki öğreticide, uygulamada hata ayıklaması yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8f94a-158">In the next tutorial, you debug the app.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="8f94a-159">Visual Studio Code kullanarak bir .NET Core konsol uygulamasında hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="8f94a-159">Debug a .NET Core console application using Visual Studio Code</span></span>](debugging-with-visual-studio-code.md)
