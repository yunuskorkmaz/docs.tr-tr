---
title: 'Öğretici: Bir .NET Core aracı oluşturma'
description: Bir .NET Core aracını nasıl oluşturabilirsiniz öğrenin. Bir araç .NET Core CLI kullanılarak yüklenen bir konsol uygulamasıdır.
ms.date: 02/12/2020
ms.openlocfilehash: 88cc3be7b149834ace0c5f3ba8ac8c039199908f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78156731"
---
# <a name="tutorial-create-a-net-core-tool-using-the-net-core-cli"></a><span data-ttu-id="54373-104">Öğretici: .NET Core CLI'yi kullanarak bir .NET Core aracı oluşturun</span><span class="sxs-lookup"><span data-stu-id="54373-104">Tutorial: Create a .NET Core tool using the .NET Core CLI</span></span>

<span data-ttu-id="54373-105">**Bu makale şu şekilde dir:** ✔️ .NET Core 2.1 SDK ve sonraki sürümler</span><span class="sxs-lookup"><span data-stu-id="54373-105">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

<span data-ttu-id="54373-106">Bu öğretici, bir .NET Core aracını nasıl oluşturup paketlediğinizi öğretir.</span><span class="sxs-lookup"><span data-stu-id="54373-106">This tutorial teaches you how to create and package a .NET Core tool.</span></span> <span data-ttu-id="54373-107">.NET Core CLI, başkalarının yükleyip çalıştırabileceği bir araç olarak bir konsol uygulaması oluşturmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="54373-107">The .NET Core CLI lets you create a console application as a tool, which others can install and run.</span></span> <span data-ttu-id="54373-108">.NET Core araçları, .NET Core CLI'den yüklenen NuGet paketleridir.</span><span class="sxs-lookup"><span data-stu-id="54373-108">.NET Core tools are NuGet packages that are installed from the .NET Core CLI.</span></span> <span data-ttu-id="54373-109">Araçlar hakkında daha fazla bilgi için [.NET Core araçlarına genel bakış](global-tools.md)ala.</span><span class="sxs-lookup"><span data-stu-id="54373-109">For more information about tools, see [.NET Core tools overview](global-tools.md).</span></span>

<span data-ttu-id="54373-110">Oluşturacağınız araç, bir iletiyi girdi olarak alan ve iletiyi bir robot görüntüsünü oluşturan metin çizgileri ile birlikte görüntüleyen bir konsol uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="54373-110">The tool that you'll create is a console application that takes a message as input and displays the message along with lines of text that create the image of a robot.</span></span>

<span data-ttu-id="54373-111">Bu üç öğreticiler bir dizi ilkidir.</span><span class="sxs-lookup"><span data-stu-id="54373-111">This is the first in a series of three tutorials.</span></span> <span data-ttu-id="54373-112">Bu öğreticide, bir araç oluşturur ve paketlersiniz.</span><span class="sxs-lookup"><span data-stu-id="54373-112">In this tutorial, you create and package a tool.</span></span> <span data-ttu-id="54373-113">Sonraki iki öğreticide [aracı genel bir araç olarak kullanırsınız](global-tools-how-to-use.md) ve [aracı yerel bir araç olarak kullanırsınız.](local-tools-how-to-use.md)</span><span class="sxs-lookup"><span data-stu-id="54373-113">In the next two tutorials you [use the tool as a global tool](global-tools-how-to-use.md) and [use the tool as a local tool](local-tools-how-to-use.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="54373-114">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="54373-114">Prerequisites</span></span>

- <span data-ttu-id="54373-115">[.NET Core SDK 3.1](https://dotnet.microsoft.com/download) veya daha sonraki bir sürüm.</span><span class="sxs-lookup"><span data-stu-id="54373-115">[.NET Core SDK 3.1](https://dotnet.microsoft.com/download) or a later version.</span></span>

  <span data-ttu-id="54373-116">Bu öğretici ve [genel araçlar için](global-tools-how-to-use.md) aşağıdaki öğretici .NET Core SDK 2.1 ve sonraki sürümlere uygulanır, çünkü bu sürümden başlayarak genel araçlar mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="54373-116">This tutorial and the following [tutorial for global tools](global-tools-how-to-use.md) apply to .NET Core SDK 2.1 and later versions because global tools are available starting in that version.</span></span> <span data-ttu-id="54373-117">Ama bu öğretici [yerel araçlar öğretici](local-tools-how-to-use.md)devam seçeneği ne var böylece 3.1 veya daha sonra yüklü varsayar.</span><span class="sxs-lookup"><span data-stu-id="54373-117">But this tutorial assumes you have installed 3.1 or later so that you have the option of continuing on to the [local tools tutorial](local-tools-how-to-use.md).</span></span> <span data-ttu-id="54373-118">Yerel araçlar .NET Core SDK 3.0'dan başlayarak mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="54373-118">Local tools are available starting in .NET Core SDK 3.0.</span></span> <span data-ttu-id="54373-119">Bir araç oluşturma yordamları, ister genel bir araç olarak ister yerel bir araç olarak kullanın aynıdır.</span><span class="sxs-lookup"><span data-stu-id="54373-119">The procedures for creating a tool are the same whether you use it as a global tool or as a local tool.</span></span>
  
- <span data-ttu-id="54373-120">Tercih ettiğiniz bir metin veya kod düzenleyicisi.</span><span class="sxs-lookup"><span data-stu-id="54373-120">A text editor or code editor of your choice.</span></span>

## <a name="create-a-project"></a><span data-ttu-id="54373-121">Proje oluşturma</span><span class="sxs-lookup"><span data-stu-id="54373-121">Create a project</span></span>

1. <span data-ttu-id="54373-122">Komut istemini açın ve *depo*adlı bir klasör oluşturun.</span><span class="sxs-lookup"><span data-stu-id="54373-122">Open a command prompt and create a folder named *repository*.</span></span>

1. <span data-ttu-id="54373-123">*Depo* klasörüne gidin ve aşağıdaki komutu girin:</span><span class="sxs-lookup"><span data-stu-id="54373-123">Navigate to the *repository* folder and enter the following command:</span></span>

   ```dotnetcli
   dotnet new console -n microsoft.botsay
   ```

   <span data-ttu-id="54373-124">Komut, *depo* klasörü altında *microsoft.botsay* adlı yeni bir klasör oluşturur.</span><span class="sxs-lookup"><span data-stu-id="54373-124">The command creates a new folder named *microsoft.botsay* under the *repository* folder.</span></span>

1. <span data-ttu-id="54373-125">*microsoft.botsay* klasörüne gidin.</span><span class="sxs-lookup"><span data-stu-id="54373-125">Navigate to the *microsoft.botsay* folder.</span></span>

   ```console
   cd microsoft.botsay
   ```

## <a name="add-the-code"></a><span data-ttu-id="54373-126">Kod ekleme</span><span class="sxs-lookup"><span data-stu-id="54373-126">Add the code</span></span>

1. <span data-ttu-id="54373-127">Kodu `Program.cs` düzenleyicinizle dosyayı açın.</span><span class="sxs-lookup"><span data-stu-id="54373-127">Open the `Program.cs` file with your code editor.</span></span>

1. <span data-ttu-id="54373-128">Dosyanın `using` üst bölümüne aşağıdaki yönergeyi ekleyin:</span><span class="sxs-lookup"><span data-stu-id="54373-128">Add the following `using` directive to the top of the file:</span></span>

   ```csharp
   using System.Reflection;
   ```

1. <span data-ttu-id="54373-129">Uygulama `Main` için komut satırı bağımsız değişkenlerini işlemek için yöntemi aşağıdaki kodla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="54373-129">Replace the `Main` method with the following code to process the command-line arguments for the application.</span></span>

   ```csharp
   static void Main(string[] args)
   {
       if (args.Length == 0)
       {
           var versionString = Assembly.GetEntryAssembly()
                                   .GetCustomAttribute<AssemblyInformationalVersionAttribute>()
                                   .InformationalVersion
                                   .ToString();

           Console.WriteLine($"botsay v{versionString}");
           Console.WriteLine("-------------");
           Console.WriteLine("\nUsage:");
           Console.WriteLine("  botsay <message>");
           return;
       }

       ShowBot(string.Join(' ', args));
   }
   ```

   <span data-ttu-id="54373-130">Bağımsız değişken geçirilmezse, kısa bir yardım iletisi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="54373-130">If no arguments are passed, a short help message is displayed.</span></span> <span data-ttu-id="54373-131">Aksi takdirde, tüm bağımsız değişkenler tek bir dize içine sıkıştırılır ve bir sonraki adımda oluşturduğunuz `ShowBot` yöntem çağırArak yazdırılır.</span><span class="sxs-lookup"><span data-stu-id="54373-131">Otherwise, all of the arguments are concatenated into a single string and printed by calling the `ShowBot` method that you create in the next step.</span></span>

1. <span data-ttu-id="54373-132">Dize parametresi alan yeni bir yöntem ekleyin. `ShowBot`</span><span class="sxs-lookup"><span data-stu-id="54373-132">Add a new method named `ShowBot` that takes a string parameter.</span></span> <span data-ttu-id="54373-133">Yöntem, metin satırlarını kullanarak bir robotun iletisini ve görüntüsünü yazdırır.</span><span class="sxs-lookup"><span data-stu-id="54373-133">The method prints out the message and an image of a robot using lines of text.</span></span>

   ```csharp
   static void ShowBot(string message)
   {
       string bot = $"\n        {message}";
       bot += @"
       __________________
                         \
                          \
                             ....
                             ....'
                              ....
                           ..........
                       .............'..'..
                    ................'..'.....
                  .......'..........'..'..'....
                 ........'..........'..'..'.....
                .'....'..'..........'..'.......'.
                .'..................'...   ......
                .  ......'.........         .....
                .    _            __        ......
               ..    #            ##        ......
              ....       .                 .......
              ......  .......          ............
               ................  ......................
               ........................'................
              ......................'..'......    .......
           .........................'..'.....       .......
        ........    ..'.............'..'....      ..........
      ..'..'...      ...............'.......      ..........
     ...'......     ...... ..........  ......         .......
    ...........   .......              ........        ......
   .......        '...'.'.              '.'.'.'         ....
   .......       .....'..               ..'.....
      ..       ..........               ..'........
             ............               ..............
            .............               '..............
           ...........'..              .'.'............
          ...............              .'.'.............
         .............'..               ..'..'...........
         ...............                 .'..............
          .........                        ..............
           .....
   ";
       Console.WriteLine(bot);
   }
   ```

1. <span data-ttu-id="54373-134">Yaptığınız değişiklikleri kaydedin.</span><span class="sxs-lookup"><span data-stu-id="54373-134">Save your changes.</span></span>

## <a name="test-the-application"></a><span data-ttu-id="54373-135">Uygulamayı test etme</span><span class="sxs-lookup"><span data-stu-id="54373-135">Test the application</span></span>

<span data-ttu-id="54373-136">Projeyi çalıştırın ve çıktıyı görün.</span><span class="sxs-lookup"><span data-stu-id="54373-136">Run the project and see the output.</span></span> <span data-ttu-id="54373-137">Farklı sonuçlar görmek için komut satırında bu varyasyonları deneyin:</span><span class="sxs-lookup"><span data-stu-id="54373-137">Try these variations at the command line to see different results:</span></span>

```dotnetcli
dotnet run
dotnet run -- "Hello from the bot"
dotnet run -- Hello from the bot
```

<span data-ttu-id="54373-138">`--` Delimiter sonra tüm bağımsız değişkenler uygulamanıza geçirilir.</span><span class="sxs-lookup"><span data-stu-id="54373-138">All arguments after the `--` delimiter are passed to your application.</span></span>

## <a name="package-the-tool"></a><span data-ttu-id="54373-139">Aracı paketle</span><span class="sxs-lookup"><span data-stu-id="54373-139">Package the tool</span></span>

<span data-ttu-id="54373-140">Uygulamayı bir araç olarak paketleyip dağıtabilmeniz için proje dosyasını değiştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="54373-140">Before you can pack and distribute the application as a tool, you need to modify the project file.</span></span>

1. <span data-ttu-id="54373-141">*microsoft.botsay.csproj* dosyasını açın ve `<PropertyGroup>` düğümün sonuna üç yeni XML düğümü ekleyin:</span><span class="sxs-lookup"><span data-stu-id="54373-141">Open the *microsoft.botsay.csproj* file and add three new XML nodes to the end of the `<PropertyGroup>` node:</span></span>

   ```xml
   <PackAsTool>true</PackAsTool>
   <ToolCommandName>botsay</ToolCommandName>
   <PackageOutputPath>./nupkg</PackageOutputPath>
   ```

   <span data-ttu-id="54373-142">`<ToolCommandName>`yüklendikten sonra aracı çağıracak komutu belirten isteğe bağlı bir öğedir.</span><span class="sxs-lookup"><span data-stu-id="54373-142">`<ToolCommandName>` is an optional element that specifies the command that will invoke the tool after it's installed.</span></span> <span data-ttu-id="54373-143">Bu öğe sağlanmadıysa, aracın komut adı *.csproj* uzantısı olmayan proje dosya adıdır.</span><span class="sxs-lookup"><span data-stu-id="54373-143">If this element isn't provided, the command name for the tool is the project file name without the *.csproj* extension.</span></span>

   <span data-ttu-id="54373-144">`<PackageOutputPath>`NuGet paketinin nerede üretileceğini belirleyen isteğe bağlı bir öğedir.</span><span class="sxs-lookup"><span data-stu-id="54373-144">`<PackageOutputPath>` is an optional element that determines where the NuGet package will be produced.</span></span> <span data-ttu-id="54373-145">NuGet paketi .NET Core CLI'nin aracınızı yüklemek için kullandığı pakettir.</span><span class="sxs-lookup"><span data-stu-id="54373-145">The NuGet package is what the .NET Core CLI uses to install your tool.</span></span>

   <span data-ttu-id="54373-146">Proje dosyası şimdi aşağıdaki örnek gibi görünüyor:</span><span class="sxs-lookup"><span data-stu-id="54373-146">The project file now looks like the following example:</span></span>

   ```xml
   <Project Sdk="Microsoft.NET.Sdk">
  
     <PropertyGroup>

       <OutputType>Exe</OutputType>
       <TargetFramework>netcoreapp3.1</TargetFramework>
  
       <PackAsTool>true</PackAsTool>
       <ToolCommandName>botsay</ToolCommandName>
       <PackageOutputPath>./nupkg</PackageOutputPath>
  
     </PropertyGroup>

   </Project>
   ```

1. <span data-ttu-id="54373-147">[dotnet paketi](dotnet-pack.md) komutunu çalıştırarak bir NuGet paketi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="54373-147">Create a NuGet package by running the [dotnet pack](dotnet-pack.md) command:</span></span>

   ```dotnetcli
   dotnet pack
   ```

   <span data-ttu-id="54373-148">*microsoft.botsay.1.0.0.nupkg* dosyası, `<PackageOutputPath>` *microsoft.botsay.csproj* dosyasından alınan değerle tanımlanan klasörde oluşturulur ve bu örnekte *./nupkg* klasörü bulunur.</span><span class="sxs-lookup"><span data-stu-id="54373-148">The *microsoft.botsay.1.0.0.nupkg* file is created in the folder identified by the `<PackageOutputPath>` value from the *microsoft.botsay.csproj* file, which in this example is the *./nupkg* folder.</span></span>
  
   <span data-ttu-id="54373-149">Bir aracı herkese açık olarak serbest bırakmak istediğinizde, aracı ' ya `https://www.nuget.org`yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="54373-149">When you want to release a tool publicly, you can upload it to `https://www.nuget.org`.</span></span> <span data-ttu-id="54373-150">Araç NuGet'de kullanılabilir hale getirinince, geliştiriciler [dotnet aracı yükleme](dotnet-tool-install.md) komutunu kullanarak aracı yükleyebilir.</span><span class="sxs-lookup"><span data-stu-id="54373-150">Once the tool is available on NuGet, developers can install the tool by using the [dotnet tool install](dotnet-tool-install.md) command.</span></span> <span data-ttu-id="54373-151">Bu öğretici için paketi doğrudan yerel *nupkg* klasöründen yüklersiniz, böylece paketi NuGet'e yüklemenize gerek yoktur.</span><span class="sxs-lookup"><span data-stu-id="54373-151">For this tutorial you install the package directly from the local *nupkg* folder, so there's no need to upload the package to NuGet.</span></span>

## <a name="troubleshoot"></a><span data-ttu-id="54373-152">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="54373-152">Troubleshoot</span></span>

<span data-ttu-id="54373-153">Öğreticiyi izlerken bir hata iletisi alırsanız, [Sorun Giderme .NET Core araç kullanım sorunlarına](troubleshoot-usage-issues.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="54373-153">If you get an error message while following the tutorial, see [Troubleshoot .NET Core tool usage issues](troubleshoot-usage-issues.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="54373-154">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="54373-154">Next steps</span></span>

<span data-ttu-id="54373-155">Bu eğitimde, bir konsol uygulaması oluşturdunuz ve bir araç olarak paketlediniz.</span><span class="sxs-lookup"><span data-stu-id="54373-155">In this tutorial, you created a console application and packaged it as a tool.</span></span> <span data-ttu-id="54373-156">Aracı genel bir araç olarak nasıl kullanacağınızı öğrenmek için bir sonraki öğreticiye ilerleyin.</span><span class="sxs-lookup"><span data-stu-id="54373-156">To learn how to use the tool as a global tool, advance to the next tutorial.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="54373-157">Genel araç yükleyip kullanma</span><span class="sxs-lookup"><span data-stu-id="54373-157">Install and use a global tool</span></span>](global-tools-how-to-use.md)

<span data-ttu-id="54373-158">İsterseniz, genel araçlar öğretici atlayabilir ve doğrudan yerel araçlar öğretici gidin.</span><span class="sxs-lookup"><span data-stu-id="54373-158">If you prefer, you can skip the global tools tutorial and go directly to the local tools tutorial.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="54373-159">Yerel araç yükleyip kullanma</span><span class="sxs-lookup"><span data-stu-id="54373-159">Install and use a local tool</span></span>](local-tools-how-to-use.md)
