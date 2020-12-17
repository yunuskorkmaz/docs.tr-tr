---
title: 'Öğretici: .NET aracı oluşturma'
description: .NET aracı oluşturmayı öğrenin. Araç, .NET CLı kullanılarak yüklenen bir konsol uygulamasıdır.
ms.topic: tutorial
ms.date: 12/14/2020
ms.openlocfilehash: dc5cf014336848ff1a3035647a386419653a083b
ms.sourcegitcommit: 635a0ff775d2447a81ef7233a599b8f88b162e5d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/17/2020
ms.locfileid: "97633903"
---
# <a name="tutorial-create-a-net-tool-using-the-net-cli"></a><span data-ttu-id="d72d8-104">Öğretici: .NET CLı kullanarak .NET aracı oluşturma</span><span class="sxs-lookup"><span data-stu-id="d72d8-104">Tutorial: Create a .NET tool using the .NET CLI</span></span>

<span data-ttu-id="d72d8-105">**Bu makale şu şekilde geçerlidir:** ✔️ .net Core 2,1 SDK ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="d72d8-105">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

<span data-ttu-id="d72d8-106">Bu öğreticide bir .NET aracı oluşturma ve paketleme hakkında öğretilir.</span><span class="sxs-lookup"><span data-stu-id="d72d8-106">This tutorial teaches you how to create and package a .NET tool.</span></span> <span data-ttu-id="d72d8-107">.NET CLı, diğer kullanıcıların yükleyebileceği ve çalıştırabileceği bir araç olarak konsol uygulaması oluşturmanıza imkan tanır.</span><span class="sxs-lookup"><span data-stu-id="d72d8-107">The .NET CLI lets you create a console application as a tool, which others can install and run.</span></span> <span data-ttu-id="d72d8-108">.NET araçları, .NET CLı 'den yüklenen NuGet paketlerdir.</span><span class="sxs-lookup"><span data-stu-id="d72d8-108">.NET tools are NuGet packages that are installed from the .NET CLI.</span></span> <span data-ttu-id="d72d8-109">Araçlar hakkında daha fazla bilgi için bkz. [.net araçlarına genel bakış](global-tools.md).</span><span class="sxs-lookup"><span data-stu-id="d72d8-109">For more information about tools, see [.NET tools overview](global-tools.md).</span></span>

<span data-ttu-id="d72d8-110">Oluşturacağınız araç, girdi olarak bir ileti alıp iletiyi bir robot görüntüsünü oluşturan metin satırlarıyla birlikte görüntüleyen bir konsol uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="d72d8-110">The tool that you'll create is a console application that takes a message as input and displays the message along with lines of text that create the image of a robot.</span></span>

<span data-ttu-id="d72d8-111">Bu, bir dizi üç öğreticiden ilkdir.</span><span class="sxs-lookup"><span data-stu-id="d72d8-111">This is the first in a series of three tutorials.</span></span> <span data-ttu-id="d72d8-112">Bu öğreticide bir araç oluşturur ve paketleyin.</span><span class="sxs-lookup"><span data-stu-id="d72d8-112">In this tutorial, you create and package a tool.</span></span> <span data-ttu-id="d72d8-113">Sonraki iki öğreticilerde [, aracı genel araç olarak kullanır](global-tools-how-to-use.md) ve [Aracı yerel bir araç olarak kullanabilirsiniz](local-tools-how-to-use.md).</span><span class="sxs-lookup"><span data-stu-id="d72d8-113">In the next two tutorials you [use the tool as a global tool](global-tools-how-to-use.md) and [use the tool as a local tool](local-tools-how-to-use.md).</span></span> <span data-ttu-id="d72d8-114">Bir araç oluşturma yordamları, bunu küresel bir araç olarak veya yerel bir araç olarak kullanıp kullanmayacağınızı de aynıdır.</span><span class="sxs-lookup"><span data-stu-id="d72d8-114">The procedures for creating a tool are the same whether you use it as a global tool or as a local tool.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="d72d8-115">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="d72d8-115">Prerequisites</span></span>

- <span data-ttu-id="d72d8-116">[.NET SDK 5.0.100](https://dotnet.microsoft.com/download) veya sonraki bir sürümü.</span><span class="sxs-lookup"><span data-stu-id="d72d8-116">[.NET SDK 5.0.100](https://dotnet.microsoft.com/download) or a later version.</span></span>

  <span data-ttu-id="d72d8-117">Bu öğretici .NET SDK 5,0 kullanır, ancak küresel araçlar .NET Core SDK 2,1 ' den itibaren kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d72d8-117">This tutorial uses .NET SDK 5.0, but global tools are available starting in .NET Core SDK 2.1.</span></span> <span data-ttu-id="d72d8-118">Yerel araçlar .NET Core SDK 3,0 ' den başlayarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d72d8-118">Local tools are available starting in .NET Core SDK 3.0.</span></span>

- <span data-ttu-id="d72d8-119">Tercih ettiğiniz bir metin veya kod düzenleyicisi.</span><span class="sxs-lookup"><span data-stu-id="d72d8-119">A text editor or code editor of your choice.</span></span>

## <a name="create-a-project"></a><span data-ttu-id="d72d8-120">Proje oluşturma</span><span class="sxs-lookup"><span data-stu-id="d72d8-120">Create a project</span></span>

1. <span data-ttu-id="d72d8-121">Bir komut istemi açın ve *Depo* adlı bir klasör oluşturun.</span><span class="sxs-lookup"><span data-stu-id="d72d8-121">Open a command prompt and create a folder named *repository*.</span></span>

1. <span data-ttu-id="d72d8-122">*Depo* klasörüne gidin ve şu komutu girin:</span><span class="sxs-lookup"><span data-stu-id="d72d8-122">Navigate to the *repository* folder and enter the following command:</span></span>

   ```dotnetcli
   dotnet new console -n microsoft.botsay -f net5.0
   ```

   <span data-ttu-id="d72d8-123">Komut, *Depo* klasörü altında *Microsoft. botdeyin* adlı yeni bir klasör oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d72d8-123">The command creates a new folder named *microsoft.botsay* under the *repository* folder.</span></span>

   > [!NOTE]
   > <span data-ttu-id="d72d8-124">Bu öğreticide, .NET 5,0 ' i hedefleyen bir araç oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="d72d8-124">For this tutorial you create a tool that targets .NET 5.0.</span></span> <span data-ttu-id="d72d8-125">Farklı bir çerçeveyi hedeflemek için `-f|--framework` seçeneğini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="d72d8-125">To target a different framework, change the `-f|--framework` option.</span></span> <span data-ttu-id="d72d8-126">Birden çok çerçeveyi hedeflemek için, `TargetFramework` `TargetFrameworks` Aşağıdaki örnekte gösterildiği gibi, öğesini proje dosyasındaki bir öğeyle değiştirin:</span><span class="sxs-lookup"><span data-stu-id="d72d8-126">To target multiple frameworks, change the `TargetFramework` element to a `TargetFrameworks` element in the project file, as shown in the following example:</span></span>
   >
   > ```xml
   > <Project Sdk="Microsoft.NET.Sdk">
   >   <PropertyGroup>
   >     <OutputType>Exe</OutputType>
   >     <TargetFrameworks>netcoreapp3.1;net5.0</TargetFrameworks>
   >   </PropertyGroup>
   > </Project>
   > ```

1. <span data-ttu-id="d72d8-127">*Microsoft. botsay* klasörüne gidin.</span><span class="sxs-lookup"><span data-stu-id="d72d8-127">Navigate to the *microsoft.botsay* folder.</span></span>

   ```console
   cd microsoft.botsay
   ```

## <a name="add-the-code"></a><span data-ttu-id="d72d8-128">Kod ekleme</span><span class="sxs-lookup"><span data-stu-id="d72d8-128">Add the code</span></span>

1. <span data-ttu-id="d72d8-129">`Program.cs`Dosyayı kod düzenleyicinizle açın.</span><span class="sxs-lookup"><span data-stu-id="d72d8-129">Open the `Program.cs` file with your code editor.</span></span>

1. <span data-ttu-id="d72d8-130">Aşağıdaki `using` yönergeyi dosyanın en üstüne ekleyin:</span><span class="sxs-lookup"><span data-stu-id="d72d8-130">Add the following `using` directive to the top of the file:</span></span>

   ```csharp
   using System.Reflection;
   ```

1. <span data-ttu-id="d72d8-131">Yöntemi, `Main` uygulamanın komut satırı bağımsız değişkenlerini işlemek için aşağıdaki kodla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="d72d8-131">Replace the `Main` method with the following code to process the command-line arguments for the application.</span></span>

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

   <span data-ttu-id="d72d8-132">Hiçbir bağımsız değişken geçirilmezse, kısa bir yardım iletisi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="d72d8-132">If no arguments are passed, a short help message is displayed.</span></span> <span data-ttu-id="d72d8-133">Aksi takdirde, tüm bağımsız değişkenler tek bir dizeye birleştirilir ve bir `ShowBot` sonraki adımda oluşturduğunuz yöntemi çağırarak yazdırılır.</span><span class="sxs-lookup"><span data-stu-id="d72d8-133">Otherwise, all of the arguments are concatenated into a single string and printed by calling the `ShowBot` method that you create in the next step.</span></span>

1. <span data-ttu-id="d72d8-134">Dize parametresi alan adlı yeni bir yöntem ekleyin `ShowBot` .</span><span class="sxs-lookup"><span data-stu-id="d72d8-134">Add a new method named `ShowBot` that takes a string parameter.</span></span> <span data-ttu-id="d72d8-135">Yöntemi, metin satırlarını kullanarak iletiyi ve bir robot görüntüsünü yazdırır.</span><span class="sxs-lookup"><span data-stu-id="d72d8-135">The method prints out the message and an image of a robot using lines of text.</span></span>

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

1. <span data-ttu-id="d72d8-136">Yaptığınız değişiklikleri kaydedin.</span><span class="sxs-lookup"><span data-stu-id="d72d8-136">Save your changes.</span></span>

## <a name="test-the-application"></a><span data-ttu-id="d72d8-137">Uygulamayı test etme</span><span class="sxs-lookup"><span data-stu-id="d72d8-137">Test the application</span></span>

<span data-ttu-id="d72d8-138">Projeyi çalıştırın ve çıktıyı görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="d72d8-138">Run the project and see the output.</span></span> <span data-ttu-id="d72d8-139">Farklı sonuçları görmek için komut satırında bu çeşitlemeleri deneyin:</span><span class="sxs-lookup"><span data-stu-id="d72d8-139">Try these variations at the command line to see different results:</span></span>

```dotnetcli
dotnet run
dotnet run -- "Hello from the bot"
dotnet run -- Hello from the bot
```

<span data-ttu-id="d72d8-140">Sınırlayıcıdan sonraki tüm bağımsız değişkenler `--` uygulamanıza geçirilir.</span><span class="sxs-lookup"><span data-stu-id="d72d8-140">All arguments after the `--` delimiter are passed to your application.</span></span>

## <a name="package-the-tool"></a><span data-ttu-id="d72d8-141">Aracı paketleyin</span><span class="sxs-lookup"><span data-stu-id="d72d8-141">Package the tool</span></span>

<span data-ttu-id="d72d8-142">Uygulamayı bir araç olarak paketleyebilir ve dağıtabilmeniz için önce proje dosyasını değiştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="d72d8-142">Before you can pack and distribute the application as a tool, you need to modify the project file.</span></span>

1. <span data-ttu-id="d72d8-143">*Microsoft. botsöyleyin. csproj* dosyasını açın ve düğümün sonuna üç yeni XML düğümü ekleyin `<PropertyGroup>` :</span><span class="sxs-lookup"><span data-stu-id="d72d8-143">Open the *microsoft.botsay.csproj* file and add three new XML nodes to the end of the `<PropertyGroup>` node:</span></span>

   ```xml
   <PackAsTool>true</PackAsTool>
   <ToolCommandName>botsay</ToolCommandName>
   <PackageOutputPath>./nupkg</PackageOutputPath>
   ```

   <span data-ttu-id="d72d8-144">`<ToolCommandName>` , yüklendikten sonra aracı çağıracağı komutu belirten isteğe bağlı bir öğedir.</span><span class="sxs-lookup"><span data-stu-id="d72d8-144">`<ToolCommandName>` is an optional element that specifies the command that will invoke the tool after it's installed.</span></span> <span data-ttu-id="d72d8-145">Bu öğe sağlanmazsa, araç için komut adı *. csproj* uzantısı olmayan proje dosyası adıdır.</span><span class="sxs-lookup"><span data-stu-id="d72d8-145">If this element isn't provided, the command name for the tool is the project file name without the *.csproj* extension.</span></span>

   <span data-ttu-id="d72d8-146">`<PackageOutputPath>` , NuGet paketinin nerede üretileceği belirleyen isteğe bağlı bir öğedir.</span><span class="sxs-lookup"><span data-stu-id="d72d8-146">`<PackageOutputPath>` is an optional element that determines where the NuGet package will be produced.</span></span> <span data-ttu-id="d72d8-147">NuGet paketi, .NET CLı 'nin aracınızı yüklemek için kullandığı şeydir.</span><span class="sxs-lookup"><span data-stu-id="d72d8-147">The NuGet package is what the .NET CLI uses to install your tool.</span></span>

   <span data-ttu-id="d72d8-148">Proje dosyası artık aşağıdaki örneğe benzer şekilde görünür:</span><span class="sxs-lookup"><span data-stu-id="d72d8-148">The project file now looks like the following example:</span></span>

   ```xml
   <Project Sdk="Microsoft.NET.Sdk">

     <PropertyGroup>

       <OutputType>Exe</OutputType>
       <TargetFramework>net5.0</TargetFramework>

       <PackAsTool>true</PackAsTool>
       <ToolCommandName>botsay</ToolCommandName>
       <PackageOutputPath>./nupkg</PackageOutputPath>

     </PropertyGroup>

   </Project>
   ```

1. <span data-ttu-id="d72d8-149">[DotNet Pack](dotnet-pack.md) komutunu çalıştırarak bir NuGet paketi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="d72d8-149">Create a NuGet package by running the [dotnet pack](dotnet-pack.md) command:</span></span>

   ```dotnetcli
   dotnet pack
   ```

   <span data-ttu-id="d72d8-150">*Microsoft. botı. 1.0.0. nupkg* dosyası, `<PackageOutputPath>` *Microsoft. botsöyleyin. csproj* dosyasındaki değeri tarafından tanımlanan klasörde oluşturulur. Bu örnekte *./nupkg* klasörüdür.</span><span class="sxs-lookup"><span data-stu-id="d72d8-150">The *microsoft.botsay.1.0.0.nupkg* file is created in the folder identified by the `<PackageOutputPath>` value from the *microsoft.botsay.csproj* file, which in this example is the *./nupkg* folder.</span></span>

   <span data-ttu-id="d72d8-151">Bir aracı herkese açık bir şekilde yayınlamak istediğinizde, ' a yükleyebilirsiniz `https://www.nuget.org` .</span><span class="sxs-lookup"><span data-stu-id="d72d8-151">When you want to release a tool publicly, you can upload it to `https://www.nuget.org`.</span></span> <span data-ttu-id="d72d8-152">Araç NuGet 'de kullanılabilir olduğunda, geliştiriciler [DotNet aracı install](dotnet-tool-install.md) komutunu kullanarak aracı yükleyebilir.</span><span class="sxs-lookup"><span data-stu-id="d72d8-152">Once the tool is available on NuGet, developers can install the tool by using the [dotnet tool install](dotnet-tool-install.md) command.</span></span> <span data-ttu-id="d72d8-153">Bu öğreticide, paketini doğrudan yerel *nupkg* klasöründen yüklersiniz, bu nedenle paketi NuGet 'e yüklemeye gerek yoktur.</span><span class="sxs-lookup"><span data-stu-id="d72d8-153">For this tutorial you install the package directly from the local *nupkg* folder, so there's no need to upload the package to NuGet.</span></span>

## <a name="troubleshoot"></a><span data-ttu-id="d72d8-154">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="d72d8-154">Troubleshoot</span></span>

<span data-ttu-id="d72d8-155">Öğreticiyi takip ederken bir hata mesajı alırsanız bkz. [.NET araç kullanım sorunlarını giderme](troubleshoot-usage-issues.md).</span><span class="sxs-lookup"><span data-stu-id="d72d8-155">If you get an error message while following the tutorial, see [Troubleshoot .NET tool usage issues](troubleshoot-usage-issues.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="d72d8-156">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="d72d8-156">Next steps</span></span>

<span data-ttu-id="d72d8-157">Bu öğreticide, bir konsol uygulaması oluşturdunuz ve bunu bir araç olarak paketlediyseniz.</span><span class="sxs-lookup"><span data-stu-id="d72d8-157">In this tutorial, you created a console application and packaged it as a tool.</span></span> <span data-ttu-id="d72d8-158">Aracın genel bir araç olarak nasıl kullanılacağını öğrenmek için bir sonraki öğreticiye ilerleyin.</span><span class="sxs-lookup"><span data-stu-id="d72d8-158">To learn how to use the tool as a global tool, advance to the next tutorial.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="d72d8-159">Genel araç yükleyip kullanma</span><span class="sxs-lookup"><span data-stu-id="d72d8-159">Install and use a global tool</span></span>](global-tools-how-to-use.md)

<span data-ttu-id="d72d8-160">İsterseniz küresel araçlar öğreticisini atlayabilir ve doğrudan yerel araçlar öğreticisine gidebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d72d8-160">If you prefer, you can skip the global tools tutorial and go directly to the local tools tutorial.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="d72d8-161">Yerel araç yükleyip kullanma</span><span class="sxs-lookup"><span data-stu-id="d72d8-161">Install and use a local tool</span></span>](local-tools-how-to-use.md)
