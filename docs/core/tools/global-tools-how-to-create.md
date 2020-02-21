---
title: 'Öğretici: .NET Core aracı oluşturma'
description: .NET Core aracı oluşturmayı öğrenin. Araç, .NET Core CLI kullanılarak yüklenen bir konsol uygulamasıdır.
ms.date: 02/12/2020
ms.openlocfilehash: 558bf9e37efc8de68a61f1384fababe342ab7d66
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543410"
---
# <a name="tutorial-create-a-net-core-tool-using-the-net-core-cli"></a><span data-ttu-id="c6bab-104">Öğretici: .NET Core CLI kullanarak bir .NET Core aracı oluşturma</span><span class="sxs-lookup"><span data-stu-id="c6bab-104">Tutorial: Create a .NET Core tool using the .NET Core CLI</span></span>

<span data-ttu-id="c6bab-105">**Bu makale şu şekilde geçerlidir:** ✔️ .net Core 2,1 SDK ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="c6bab-105">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

<span data-ttu-id="c6bab-106">Bu öğreticide bir .NET Core aracı oluşturma ve paketleme öğretilir.</span><span class="sxs-lookup"><span data-stu-id="c6bab-106">This tutorial teaches you how to create and package a .NET Core tool.</span></span> <span data-ttu-id="c6bab-107">.NET Core CLI, diğer kullanıcıların yükleyebileceği ve çalıştırabileceği bir araç olarak konsol uygulaması oluşturmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="c6bab-107">The .NET Core CLI lets you create a console application as a tool, which others can install and run.</span></span> <span data-ttu-id="c6bab-108">.NET Core araçları, .NET Core CLI yüklenen NuGet paketlerdir.</span><span class="sxs-lookup"><span data-stu-id="c6bab-108">.NET Core tools are NuGet packages that are installed from the .NET Core CLI.</span></span> <span data-ttu-id="c6bab-109">Araçlar hakkında daha fazla bilgi için bkz. [.NET Core araçlarına genel bakış](global-tools.md).</span><span class="sxs-lookup"><span data-stu-id="c6bab-109">For more information about tools, see [.NET Core tools overview](global-tools.md).</span></span>

<span data-ttu-id="c6bab-110">Oluşturacağınız araç, girdi olarak bir ileti alıp iletiyi bir robot görüntüsünü oluşturan metin satırlarıyla birlikte görüntüleyen bir konsol uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="c6bab-110">The tool that you'll create is a console application that takes a message as input and displays the message along with lines of text that create the image of a robot.</span></span>

<span data-ttu-id="c6bab-111">Bu, bir dizi üç öğreticiden ilkdir.</span><span class="sxs-lookup"><span data-stu-id="c6bab-111">This is the first in a series of three tutorials.</span></span> <span data-ttu-id="c6bab-112">Bu öğreticide bir araç oluşturur ve paketleyin.</span><span class="sxs-lookup"><span data-stu-id="c6bab-112">In this tutorial, you create and package a tool.</span></span> <span data-ttu-id="c6bab-113">Sonraki iki öğreticilerde [, aracı genel araç olarak kullanır](global-tools-how-to-use.md) ve [Aracı yerel bir araç olarak kullanabilirsiniz](local-tools-how-to-use.md).</span><span class="sxs-lookup"><span data-stu-id="c6bab-113">In the next two tutorials you [use the tool as a global tool](global-tools-how-to-use.md) and [use the tool as a local tool](local-tools-how-to-use.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="c6bab-114">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="c6bab-114">Prerequisites</span></span>

- <span data-ttu-id="c6bab-115">[.NET Core SDK 3,1](https://dotnet.microsoft.com/download) veya sonraki bir sürümü.</span><span class="sxs-lookup"><span data-stu-id="c6bab-115">[.NET Core SDK 3.1](https://dotnet.microsoft.com/download) or a later version.</span></span>

  <span data-ttu-id="c6bab-116">Bu öğreticide, genel [araçlar .NET Core SDK](global-tools-how-to-use.md) 2,1 ve üzeri sürümler için bu öğretici ve bu sürümden itibaren küresel araçlar geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="c6bab-116">This tutorial and the following [tutorial for global tools](global-tools-how-to-use.md) apply to .NET Core SDK 2.1 and later versions because global tools are available starting in that version.</span></span> <span data-ttu-id="c6bab-117">Ancak bu öğreticide, [Yerel araçlar öğreticisine](local-tools-how-to-use.md)devam etme seçeneğine sahip olmanız için 3,1 veya sonraki bir sürümü yüklemiş olduğunuz varsayılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c6bab-117">But this tutorial assumes you have installed 3.1 or later so that you have the option of continuing on to the [local tools tutorial](local-tools-how-to-use.md).</span></span> <span data-ttu-id="c6bab-118">Yerel araçlar .NET Core SDK 3,0 ' den başlayarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c6bab-118">Local tools are available starting in .NET Core SDK 3.0.</span></span> <span data-ttu-id="c6bab-119">Bir araç oluşturma yordamları, bunu küresel bir araç olarak veya yerel bir araç olarak kullanıp kullanmayacağınızı de aynıdır.</span><span class="sxs-lookup"><span data-stu-id="c6bab-119">The procedures for creating a tool are the same whether you use it as a global tool or as a local tool.</span></span>
  
- <span data-ttu-id="c6bab-120">Tercih ettiğiniz bir metin veya kod düzenleyicisi.</span><span class="sxs-lookup"><span data-stu-id="c6bab-120">A text editor or code editor of your choice.</span></span>

## <a name="create-a-project"></a><span data-ttu-id="c6bab-121">Proje oluştur</span><span class="sxs-lookup"><span data-stu-id="c6bab-121">Create a project</span></span>

1. <span data-ttu-id="c6bab-122">Bir komut istemi açın ve *Depo*adlı bir klasör oluşturun.</span><span class="sxs-lookup"><span data-stu-id="c6bab-122">Open a command prompt and create a folder named *repository*.</span></span>

1. <span data-ttu-id="c6bab-123">*Depo* klasörüne gidin ve aşağıdaki komutu girin ve proje adının benzersiz olması için `<name>` benzersiz bir değerle değiştirin.</span><span class="sxs-lookup"><span data-stu-id="c6bab-123">Navigate to the *repository* folder and enter the following command, replacing `<name>` with a unique value to make the project name unique.</span></span> 

   ```dotnetcli
   dotnet new console -n botsay-<name>
   ```

   <span data-ttu-id="c6bab-124">Örneğin, aşağıdaki komutu çalıştırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="c6bab-124">For example, you could run the following command:</span></span>

   ```dotnetcli
   dotnet new console -n botsay-nancydavolio
   ```

   <span data-ttu-id="c6bab-125">Komut, *Depo* klasörü altında *botdeyin-\<name >* adlı yeni bir klasör oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c6bab-125">The command creates a new folder named *botsay-\<name>* under the *repository* folder.</span></span>

1. <span data-ttu-id="c6bab-126">*Botdeyin-\<adı >* klasörüne gidin.</span><span class="sxs-lookup"><span data-stu-id="c6bab-126">Navigate to the *botsay-\<name>* folder.</span></span>

   ```console
   cd botsay-<name>
   ```

## <a name="add-the-code"></a><span data-ttu-id="c6bab-127">Kod ekleme</span><span class="sxs-lookup"><span data-stu-id="c6bab-127">Add the code</span></span>

1. <span data-ttu-id="c6bab-128">`Program.cs` dosyasını kod düzenleyicinizle açın.</span><span class="sxs-lookup"><span data-stu-id="c6bab-128">Open the `Program.cs` file with your code editor.</span></span>

1. <span data-ttu-id="c6bab-129">Aşağıdaki `using` yönergesini dosyanın en üstüne ekleyin:</span><span class="sxs-lookup"><span data-stu-id="c6bab-129">Add the following `using` directive to the top of the file:</span></span>

   ```csharp
   using System.Reflection;
   ```

1. <span data-ttu-id="c6bab-130">Uygulama için komut satırı bağımsız değişkenlerini işlemek üzere `Main` yöntemini aşağıdaki kodla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="c6bab-130">Replace the `Main` method with the following code to process the command-line arguments for the application.</span></span>

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

   <span data-ttu-id="c6bab-131">Hiçbir bağımsız değişken geçirilmezse, kısa bir yardım iletisi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="c6bab-131">If no arguments are passed, a short help message is displayed.</span></span> <span data-ttu-id="c6bab-132">Aksi takdirde, tüm bağımsız değişkenler tek bir dizeye birleştirilir ve bir sonraki adımda oluşturduğunuz `ShowBot` yöntemi çağırarak yazdırılır.</span><span class="sxs-lookup"><span data-stu-id="c6bab-132">Otherwise, all of the arguments are concatenated into a single string and printed by calling the `ShowBot` method that you create in the next step.</span></span>

1. <span data-ttu-id="c6bab-133">Dize parametresi alan `ShowBot` adlı yeni bir yöntem ekleyin.</span><span class="sxs-lookup"><span data-stu-id="c6bab-133">Add a new method named `ShowBot` that takes a string parameter.</span></span> <span data-ttu-id="c6bab-134">Yöntemi, metin satırlarını kullanarak iletiyi ve bir robot görüntüsünü yazdırır.</span><span class="sxs-lookup"><span data-stu-id="c6bab-134">The method prints out the message and an image of a robot using lines of text.</span></span>

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

1. <span data-ttu-id="c6bab-135">Yaptığınız değişiklikleri kaydedin.</span><span class="sxs-lookup"><span data-stu-id="c6bab-135">Save your changes.</span></span>

## <a name="test-the-application"></a><span data-ttu-id="c6bab-136">Uygulamayı test etme</span><span class="sxs-lookup"><span data-stu-id="c6bab-136">Test the application</span></span>

<span data-ttu-id="c6bab-137">Projeyi çalıştırın ve çıktıyı görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="c6bab-137">Run the project and see the output.</span></span> <span data-ttu-id="c6bab-138">Farklı sonuçları görmek için komut satırında bu çeşitlemeleri deneyin:</span><span class="sxs-lookup"><span data-stu-id="c6bab-138">Try these variations at the command line to see different results:</span></span>

```dotnetcli
dotnet run
dotnet run -- "Hello from the bot"
dotnet run -- Hello from the bot
```

<span data-ttu-id="c6bab-139">`--` sınırlayıcısından sonraki tüm bağımsız değişkenler uygulamanıza geçirilir.</span><span class="sxs-lookup"><span data-stu-id="c6bab-139">All arguments after the `--` delimiter are passed to your application.</span></span>

## <a name="package-the-tool"></a><span data-ttu-id="c6bab-140">Aracı paketleyin</span><span class="sxs-lookup"><span data-stu-id="c6bab-140">Package the tool</span></span>

<span data-ttu-id="c6bab-141">Uygulamayı bir araç olarak paketleyebilir ve dağıtabilmeniz için önce proje dosyasını değiştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="c6bab-141">Before you can pack and distribute the application as a tool, you need to modify the project file.</span></span> 

1. <span data-ttu-id="c6bab-142">*Botdeyin-\<adı >. csproj* dosyasını açın ve `<PropertyGroup>` düğümünün sonuna üç yeni XML düğümü ekleyin:</span><span class="sxs-lookup"><span data-stu-id="c6bab-142">Open the *botsay-\<name>.csproj* file and add three new XML nodes to the end of the `<PropertyGroup>` node:</span></span>

   ```xml
   <PackAsTool>true</PackAsTool>
   <ToolCommandName>botsay</ToolCommandName>
   <PackageOutputPath>./nupkg</PackageOutputPath>
   ```

   <span data-ttu-id="c6bab-143">`<ToolCommandName>`, yüklendikten sonra aracı çağıracağı komutu belirten isteğe bağlı bir öğedir.</span><span class="sxs-lookup"><span data-stu-id="c6bab-143">`<ToolCommandName>` is an optional element that specifies the command that will invoke the tool after it's installed.</span></span> <span data-ttu-id="c6bab-144">Bu öğe sağlanmazsa, araç için komut adı *. csproj* uzantısı olmayan proje dosyası adıdır.</span><span class="sxs-lookup"><span data-stu-id="c6bab-144">If this element isn't provided, the command name for the tool is the project file name without the *.csproj* extension.</span></span>

   <span data-ttu-id="c6bab-145">`<PackageOutputPath>`, NuGet paketinin nerede üretileceği belirleyen isteğe bağlı bir öğedir.</span><span class="sxs-lookup"><span data-stu-id="c6bab-145">`<PackageOutputPath>` is an optional element that determines where the NuGet package will be produced.</span></span> <span data-ttu-id="c6bab-146">NuGet paketi, .NET Core CLI aracınızı yüklemek için kullandığı şeydir.</span><span class="sxs-lookup"><span data-stu-id="c6bab-146">The NuGet package is what the .NET Core CLI uses to install your tool.</span></span>

   <span data-ttu-id="c6bab-147">Proje dosyası artık aşağıdaki örneğe benzer şekilde görünür:</span><span class="sxs-lookup"><span data-stu-id="c6bab-147">The project file now looks like the following example:</span></span>

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

1. <span data-ttu-id="c6bab-148">[DotNet Pack](dotnet-pack.md) komutunu çalıştırarak bir NuGet paketi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="c6bab-148">Create a NuGet package by running the [dotnet pack](dotnet-pack.md) command:</span></span>

   ```dotnetcli
   dotnet pack
   ```

   <span data-ttu-id="c6bab-149">*Botdeyin-\<name >. 1.0.0. nupkg* dosyası, bu örnekte *./nupkg klasörüdür./n/nDosya* olan *botsöyleyin-\<name >. csproj* dosyasındaki `<PackageOutputPath>` değeri tarafından tanımlanan klasörde oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="c6bab-149">The *botsay-\<name>.1.0.0.nupkg* file is created in the folder identified by the `<PackageOutputPath>` value from the *botsay-\<name>.csproj* file, which in this example is the *./nupkg* folder.</span></span>
  
   <span data-ttu-id="c6bab-150">Bir aracı herkese açık bir şekilde yayınlamak istediğinizde, `https://www.nuget.org`yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c6bab-150">When you want to release a tool publicly, you can upload it to `https://www.nuget.org`.</span></span> <span data-ttu-id="c6bab-151">Araç NuGet 'de kullanılabilir olduğunda, geliştiriciler [DotNet aracı install](dotnet-tool-install.md) komutunu kullanarak aracı yükleyebilir.</span><span class="sxs-lookup"><span data-stu-id="c6bab-151">Once the tool is available on NuGet, developers can install the tool by using the [dotnet tool install](dotnet-tool-install.md) command.</span></span> <span data-ttu-id="c6bab-152">Bu öğreticide, paketini doğrudan yerel *nupkg* klasöründen yüklersiniz, bu nedenle paketi NuGet 'e yüklemeye gerek yoktur.</span><span class="sxs-lookup"><span data-stu-id="c6bab-152">For this tutorial you install the package directly from the local *nupkg* folder, so there's no need to upload the package to NuGet.</span></span>

## <a name="troubleshoot"></a><span data-ttu-id="c6bab-153">Sorunları Gider</span><span class="sxs-lookup"><span data-stu-id="c6bab-153">Troubleshoot</span></span>

<span data-ttu-id="c6bab-154">Öğreticiyi takip ederken bir hata mesajı alırsanız bkz. [.NET Core araç kullanımı sorunlarını giderme](troubleshoot-usage-issues.md).</span><span class="sxs-lookup"><span data-stu-id="c6bab-154">If you get an error message while following the tutorial, see [Troubleshoot .NET Core tool usage issues](troubleshoot-usage-issues.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="c6bab-155">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="c6bab-155">Next steps</span></span>

<span data-ttu-id="c6bab-156">Bu öğreticide, bir konsol uygulaması oluşturdunuz ve bunu bir araç olarak paketlediyseniz.</span><span class="sxs-lookup"><span data-stu-id="c6bab-156">In this tutorial, you created a console application and packaged it as a tool.</span></span> <span data-ttu-id="c6bab-157">Aracın genel bir araç olarak nasıl kullanılacağını öğrenmek için bir sonraki öğreticiye ilerleyin.</span><span class="sxs-lookup"><span data-stu-id="c6bab-157">To learn how to use the tool as a global tool, advance to the next tutorial.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="c6bab-158">Küresel bir araç yükleyip kullanma</span><span class="sxs-lookup"><span data-stu-id="c6bab-158">Install and use a global tool</span></span>](global-tools-how-to-use.md)

<span data-ttu-id="c6bab-159">İsterseniz küresel araçlar öğreticisini atlayabilir ve doğrudan yerel araçlar öğreticisine gidebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c6bab-159">If you prefer, you can skip the global tools tutorial and go directly to the local tools tutorial.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="c6bab-160">Yerel bir araç yükleyip kullanma</span><span class="sxs-lookup"><span data-stu-id="c6bab-160">Install and use a local tool</span></span>](local-tools-how-to-use.md)
