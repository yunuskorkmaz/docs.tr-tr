---
title: 'Öğretici: .NET aracı oluşturma'
description: .NET aracı oluşturmayı öğrenin. Araç, .NET CLı kullanılarak yüklenen bir konsol uygulamasıdır.
ms.topic: tutorial
ms.date: 02/12/2020
ms.openlocfilehash: 93d0567f3d73707f828f84fad6128804debf6579
ms.sourcegitcommit: b201d177e01480a139622f3bf8facd367657a472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/15/2020
ms.locfileid: "94633784"
---
# <a name="tutorial-create-a-net-tool-using-the-net-cli"></a><span data-ttu-id="2df29-104">Öğretici: .NET CLı kullanarak .NET aracı oluşturma</span><span class="sxs-lookup"><span data-stu-id="2df29-104">Tutorial: Create a .NET tool using the .NET CLI</span></span>

<span data-ttu-id="2df29-105">**Bu makale şu şekilde geçerlidir:** ✔️ .net Core 2,1 SDK ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="2df29-105">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

<span data-ttu-id="2df29-106">Bu öğreticide bir .NET aracı oluşturma ve paketleme hakkında öğretilir.</span><span class="sxs-lookup"><span data-stu-id="2df29-106">This tutorial teaches you how to create and package a .NET tool.</span></span> <span data-ttu-id="2df29-107">.NET CLı, diğer kullanıcıların yükleyebileceği ve çalıştırabileceği bir araç olarak konsol uygulaması oluşturmanıza imkan tanır.</span><span class="sxs-lookup"><span data-stu-id="2df29-107">The .NET CLI lets you create a console application as a tool, which others can install and run.</span></span> <span data-ttu-id="2df29-108">.NET araçları, .NET CLı 'den yüklenen NuGet paketlerdir.</span><span class="sxs-lookup"><span data-stu-id="2df29-108">.NET tools are NuGet packages that are installed from the .NET CLI.</span></span> <span data-ttu-id="2df29-109">Araçlar hakkında daha fazla bilgi için bkz. [.net araçlarına genel bakış](global-tools.md).</span><span class="sxs-lookup"><span data-stu-id="2df29-109">For more information about tools, see [.NET tools overview](global-tools.md).</span></span>

<span data-ttu-id="2df29-110">Oluşturacağınız araç, girdi olarak bir ileti alıp iletiyi bir robot görüntüsünü oluşturan metin satırlarıyla birlikte görüntüleyen bir konsol uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="2df29-110">The tool that you'll create is a console application that takes a message as input and displays the message along with lines of text that create the image of a robot.</span></span>

<span data-ttu-id="2df29-111">Bu, bir dizi üç öğreticiden ilkdir.</span><span class="sxs-lookup"><span data-stu-id="2df29-111">This is the first in a series of three tutorials.</span></span> <span data-ttu-id="2df29-112">Bu öğreticide bir araç oluşturur ve paketleyin.</span><span class="sxs-lookup"><span data-stu-id="2df29-112">In this tutorial, you create and package a tool.</span></span> <span data-ttu-id="2df29-113">Sonraki iki öğreticilerde [, aracı genel araç olarak kullanır](global-tools-how-to-use.md) ve [Aracı yerel bir araç olarak kullanabilirsiniz](local-tools-how-to-use.md).</span><span class="sxs-lookup"><span data-stu-id="2df29-113">In the next two tutorials you [use the tool as a global tool](global-tools-how-to-use.md) and [use the tool as a local tool](local-tools-how-to-use.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="2df29-114">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="2df29-114">Prerequisites</span></span>

- <span data-ttu-id="2df29-115">[.NET Core SDK 3,1](https://dotnet.microsoft.com/download) veya sonraki bir sürümü.</span><span class="sxs-lookup"><span data-stu-id="2df29-115">[.NET Core SDK 3.1](https://dotnet.microsoft.com/download) or a later version.</span></span>

  <span data-ttu-id="2df29-116">Bu öğreticide, genel [araçlar .NET Core SDK](global-tools-how-to-use.md) 2,1 ve üzeri sürümler için bu öğretici ve bu sürümden itibaren küresel araçlar geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="2df29-116">This tutorial and the following [tutorial for global tools](global-tools-how-to-use.md) apply to .NET Core SDK 2.1 and later versions because global tools are available starting in that version.</span></span> <span data-ttu-id="2df29-117">Ancak bu öğreticide, [Yerel araçlar öğreticisine](local-tools-how-to-use.md)devam etme seçeneğine sahip olmanız için 3,1 veya sonraki bir sürümü yüklemiş olduğunuz varsayılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="2df29-117">But this tutorial assumes you have installed 3.1 or later so that you have the option of continuing on to the [local tools tutorial](local-tools-how-to-use.md).</span></span> <span data-ttu-id="2df29-118">Yerel araçlar .NET Core SDK 3,0 ' den başlayarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="2df29-118">Local tools are available starting in .NET Core SDK 3.0.</span></span> <span data-ttu-id="2df29-119">Bir araç oluşturma yordamları, bunu küresel bir araç olarak veya yerel bir araç olarak kullanıp kullanmayacağınızı de aynıdır.</span><span class="sxs-lookup"><span data-stu-id="2df29-119">The procedures for creating a tool are the same whether you use it as a global tool or as a local tool.</span></span>
  
- <span data-ttu-id="2df29-120">Tercih ettiğiniz bir metin veya kod düzenleyicisi.</span><span class="sxs-lookup"><span data-stu-id="2df29-120">A text editor or code editor of your choice.</span></span>

## <a name="create-a-project"></a><span data-ttu-id="2df29-121">Proje oluşturma</span><span class="sxs-lookup"><span data-stu-id="2df29-121">Create a project</span></span>

1. <span data-ttu-id="2df29-122">Bir komut istemi açın ve *Depo* adlı bir klasör oluşturun.</span><span class="sxs-lookup"><span data-stu-id="2df29-122">Open a command prompt and create a folder named *repository*.</span></span>

1. <span data-ttu-id="2df29-123">*Depo* klasörüne gidin ve şu komutu girin:</span><span class="sxs-lookup"><span data-stu-id="2df29-123">Navigate to the *repository* folder and enter the following command:</span></span>

   ```dotnetcli
   dotnet new console -n microsoft.botsay
   ```

   <span data-ttu-id="2df29-124">Komut, *Depo* klasörü altında *Microsoft. botdeyin* adlı yeni bir klasör oluşturur.</span><span class="sxs-lookup"><span data-stu-id="2df29-124">The command creates a new folder named *microsoft.botsay* under the *repository* folder.</span></span>

1. <span data-ttu-id="2df29-125">*Microsoft. botsay* klasörüne gidin.</span><span class="sxs-lookup"><span data-stu-id="2df29-125">Navigate to the *microsoft.botsay* folder.</span></span>

   ```console
   cd microsoft.botsay
   ```

## <a name="add-the-code"></a><span data-ttu-id="2df29-126">Kod ekleme</span><span class="sxs-lookup"><span data-stu-id="2df29-126">Add the code</span></span>

1. <span data-ttu-id="2df29-127">`Program.cs`Dosyayı kod düzenleyicinizle açın.</span><span class="sxs-lookup"><span data-stu-id="2df29-127">Open the `Program.cs` file with your code editor.</span></span>

1. <span data-ttu-id="2df29-128">Aşağıdaki `using` yönergeyi dosyanın en üstüne ekleyin:</span><span class="sxs-lookup"><span data-stu-id="2df29-128">Add the following `using` directive to the top of the file:</span></span>

   ```csharp
   using System.Reflection;
   ```

1. <span data-ttu-id="2df29-129">Yöntemi, `Main` uygulamanın komut satırı bağımsız değişkenlerini işlemek için aşağıdaki kodla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="2df29-129">Replace the `Main` method with the following code to process the command-line arguments for the application.</span></span>

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

   <span data-ttu-id="2df29-130">Hiçbir bağımsız değişken geçirilmezse, kısa bir yardım iletisi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="2df29-130">If no arguments are passed, a short help message is displayed.</span></span> <span data-ttu-id="2df29-131">Aksi takdirde, tüm bağımsız değişkenler tek bir dizeye birleştirilir ve bir `ShowBot` sonraki adımda oluşturduğunuz yöntemi çağırarak yazdırılır.</span><span class="sxs-lookup"><span data-stu-id="2df29-131">Otherwise, all of the arguments are concatenated into a single string and printed by calling the `ShowBot` method that you create in the next step.</span></span>

1. <span data-ttu-id="2df29-132">Dize parametresi alan adlı yeni bir yöntem ekleyin `ShowBot` .</span><span class="sxs-lookup"><span data-stu-id="2df29-132">Add a new method named `ShowBot` that takes a string parameter.</span></span> <span data-ttu-id="2df29-133">Yöntemi, metin satırlarını kullanarak iletiyi ve bir robot görüntüsünü yazdırır.</span><span class="sxs-lookup"><span data-stu-id="2df29-133">The method prints out the message and an image of a robot using lines of text.</span></span>

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

1. <span data-ttu-id="2df29-134">Yaptığınız değişiklikleri kaydedin.</span><span class="sxs-lookup"><span data-stu-id="2df29-134">Save your changes.</span></span>

## <a name="test-the-application"></a><span data-ttu-id="2df29-135">Uygulamayı test edin</span><span class="sxs-lookup"><span data-stu-id="2df29-135">Test the application</span></span>

<span data-ttu-id="2df29-136">Projeyi çalıştırın ve çıktıyı görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="2df29-136">Run the project and see the output.</span></span> <span data-ttu-id="2df29-137">Farklı sonuçları görmek için komut satırında bu çeşitlemeleri deneyin:</span><span class="sxs-lookup"><span data-stu-id="2df29-137">Try these variations at the command line to see different results:</span></span>

```dotnetcli
dotnet run
dotnet run -- "Hello from the bot"
dotnet run -- Hello from the bot
```

<span data-ttu-id="2df29-138">Sınırlayıcıdan sonraki tüm bağımsız değişkenler `--` uygulamanıza geçirilir.</span><span class="sxs-lookup"><span data-stu-id="2df29-138">All arguments after the `--` delimiter are passed to your application.</span></span>

## <a name="package-the-tool"></a><span data-ttu-id="2df29-139">Aracı paketleyin</span><span class="sxs-lookup"><span data-stu-id="2df29-139">Package the tool</span></span>

<span data-ttu-id="2df29-140">Uygulamayı bir araç olarak paketleyebilir ve dağıtabilmeniz için önce proje dosyasını değiştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="2df29-140">Before you can pack and distribute the application as a tool, you need to modify the project file.</span></span>

1. <span data-ttu-id="2df29-141">*Microsoft. botsöyleyin. csproj* dosyasını açın ve düğümün sonuna üç yeni XML düğümü ekleyin `<PropertyGroup>` :</span><span class="sxs-lookup"><span data-stu-id="2df29-141">Open the *microsoft.botsay.csproj* file and add three new XML nodes to the end of the `<PropertyGroup>` node:</span></span>

   ```xml
   <PackAsTool>true</PackAsTool>
   <ToolCommandName>botsay</ToolCommandName>
   <PackageOutputPath>./nupkg</PackageOutputPath>
   ```

   <span data-ttu-id="2df29-142">`<ToolCommandName>` , yüklendikten sonra aracı çağıracağı komutu belirten isteğe bağlı bir öğedir.</span><span class="sxs-lookup"><span data-stu-id="2df29-142">`<ToolCommandName>` is an optional element that specifies the command that will invoke the tool after it's installed.</span></span> <span data-ttu-id="2df29-143">Bu öğe sağlanmazsa, araç için komut adı *. csproj* uzantısı olmayan proje dosyası adıdır.</span><span class="sxs-lookup"><span data-stu-id="2df29-143">If this element isn't provided, the command name for the tool is the project file name without the *.csproj* extension.</span></span>

   <span data-ttu-id="2df29-144">`<PackageOutputPath>` , NuGet paketinin nerede üretileceği belirleyen isteğe bağlı bir öğedir.</span><span class="sxs-lookup"><span data-stu-id="2df29-144">`<PackageOutputPath>` is an optional element that determines where the NuGet package will be produced.</span></span> <span data-ttu-id="2df29-145">NuGet paketi, .NET Core CLI aracınızı yüklemek için kullandığı şeydir.</span><span class="sxs-lookup"><span data-stu-id="2df29-145">The NuGet package is what the .NET Core CLI uses to install your tool.</span></span>

   <span data-ttu-id="2df29-146">Proje dosyası artık aşağıdaki örneğe benzer şekilde görünür:</span><span class="sxs-lookup"><span data-stu-id="2df29-146">The project file now looks like the following example:</span></span>

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

1. <span data-ttu-id="2df29-147">[DotNet Pack](dotnet-pack.md) komutunu çalıştırarak bir NuGet paketi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="2df29-147">Create a NuGet package by running the [dotnet pack](dotnet-pack.md) command:</span></span>

   ```dotnetcli
   dotnet pack
   ```

   <span data-ttu-id="2df29-148">*Microsoft. botı. 1.0.0. nupkg* dosyası, `<PackageOutputPath>` *Microsoft. botsöyleyin. csproj* dosyasındaki değeri tarafından tanımlanan klasörde oluşturulur. Bu örnekte *./nupkg* klasörüdür.</span><span class="sxs-lookup"><span data-stu-id="2df29-148">The *microsoft.botsay.1.0.0.nupkg* file is created in the folder identified by the `<PackageOutputPath>` value from the *microsoft.botsay.csproj* file, which in this example is the *./nupkg* folder.</span></span>
  
   <span data-ttu-id="2df29-149">Bir aracı herkese açık bir şekilde yayınlamak istediğinizde, ' a yükleyebilirsiniz `https://www.nuget.org` .</span><span class="sxs-lookup"><span data-stu-id="2df29-149">When you want to release a tool publicly, you can upload it to `https://www.nuget.org`.</span></span> <span data-ttu-id="2df29-150">Araç NuGet 'de kullanılabilir olduğunda, geliştiriciler [DotNet aracı install](dotnet-tool-install.md) komutunu kullanarak aracı yükleyebilir.</span><span class="sxs-lookup"><span data-stu-id="2df29-150">Once the tool is available on NuGet, developers can install the tool by using the [dotnet tool install](dotnet-tool-install.md) command.</span></span> <span data-ttu-id="2df29-151">Bu öğreticide, paketini doğrudan yerel *nupkg* klasöründen yüklersiniz, bu nedenle paketi NuGet 'e yüklemeye gerek yoktur.</span><span class="sxs-lookup"><span data-stu-id="2df29-151">For this tutorial you install the package directly from the local *nupkg* folder, so there's no need to upload the package to NuGet.</span></span>

## <a name="troubleshoot"></a><span data-ttu-id="2df29-152">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="2df29-152">Troubleshoot</span></span>

<span data-ttu-id="2df29-153">Öğreticiyi takip ederken bir hata mesajı alırsanız bkz. [.NET araç kullanım sorunlarını giderme](troubleshoot-usage-issues.md).</span><span class="sxs-lookup"><span data-stu-id="2df29-153">If you get an error message while following the tutorial, see [Troubleshoot .NET tool usage issues](troubleshoot-usage-issues.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="2df29-154">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="2df29-154">Next steps</span></span>

<span data-ttu-id="2df29-155">Bu öğreticide, bir konsol uygulaması oluşturdunuz ve bunu bir araç olarak paketlediyseniz.</span><span class="sxs-lookup"><span data-stu-id="2df29-155">In this tutorial, you created a console application and packaged it as a tool.</span></span> <span data-ttu-id="2df29-156">Aracın genel bir araç olarak nasıl kullanılacağını öğrenmek için bir sonraki öğreticiye ilerleyin.</span><span class="sxs-lookup"><span data-stu-id="2df29-156">To learn how to use the tool as a global tool, advance to the next tutorial.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="2df29-157">Genel araç yükleyip kullanma</span><span class="sxs-lookup"><span data-stu-id="2df29-157">Install and use a global tool</span></span>](global-tools-how-to-use.md)

<span data-ttu-id="2df29-158">İsterseniz küresel araçlar öğreticisini atlayabilir ve doğrudan yerel araçlar öğreticisine gidebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2df29-158">If you prefer, you can skip the global tools tutorial and go directly to the local tools tutorial.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="2df29-159">Yerel araç yükleyip kullanma</span><span class="sxs-lookup"><span data-stu-id="2df29-159">Install and use a local tool</span></span>](local-tools-how-to-use.md)
