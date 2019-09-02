---
title: .NET Core küresel aracı oluşturma
description: Genel bir aracın nasıl oluşturulacağını açıklar. Genel araç, .NET Core CLI aracılığıyla yüklenen bir konsol uygulamasıdır.
author: Thraka
ms.author: adegeo
ms.date: 08/22/2018
ms.openlocfilehash: f60e26d14e89b6b7c34b32bf9a114fe4ad691981
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70202769"
---
# <a name="create-a-net-core-global-tool-using-the-net-core-cli"></a><span data-ttu-id="1620a-104">.NET Core CLI kullanarak bir .NET Core genel aracı oluşturun</span><span class="sxs-lookup"><span data-stu-id="1620a-104">Create a .NET Core Global Tool using the .NET Core CLI</span></span>

<span data-ttu-id="1620a-105">Bu makalede bir .NET Core küresel aracı oluşturma ve paketleme hakkında öğretilir.</span><span class="sxs-lookup"><span data-stu-id="1620a-105">This article teaches you how to create and package a .NET Core Global Tool.</span></span> <span data-ttu-id="1620a-106">.NET Core CLI, bir konsol uygulamasını küresel bir araç olarak oluşturmanıza olanak tanır. Bu, başkalarının kolayca yükleyip çalıştırabilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="1620a-106">The .NET Core CLI allows you to create a console application as a Global Tool, which others can easily install and run.</span></span> <span data-ttu-id="1620a-107">.NET Core küresel araçları, .NET Core CLI yüklenen NuGet paketlerdir.</span><span class="sxs-lookup"><span data-stu-id="1620a-107">.NET Core Global Tools are NuGet packages that are installed from the .NET Core CLI.</span></span> <span data-ttu-id="1620a-108">Küresel araçlar hakkında daha fazla bilgi için bkz. [.NET Core genel araçlarına genel bakış](global-tools.md).</span><span class="sxs-lookup"><span data-stu-id="1620a-108">For more information about Global Tools, see [.NET Core Global Tools overview](global-tools.md).</span></span>

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

## <a name="create-a-project"></a><span data-ttu-id="1620a-109">Proje oluşturma</span><span class="sxs-lookup"><span data-stu-id="1620a-109">Create a project</span></span>

<span data-ttu-id="1620a-110">Bu makale bir proje oluşturmak ve yönetmek için .NET Core CLI kullanır.</span><span class="sxs-lookup"><span data-stu-id="1620a-110">This article uses the .NET Core CLI to create and manage a project.</span></span>

<span data-ttu-id="1620a-111">Örnek aracımız, bir ASCII bot üreten ve bir ileti yazdıran bir konsol uygulaması olacaktır.</span><span class="sxs-lookup"><span data-stu-id="1620a-111">Our example tool will be a console application that generates an ASCII bot and prints a message.</span></span> <span data-ttu-id="1620a-112">İlk olarak, yeni bir .NET Core konsol uygulaması oluşturun.</span><span class="sxs-lookup"><span data-stu-id="1620a-112">First, create a new .NET Core Console Application.</span></span>

```console
dotnet new console -o botsay
```

<span data-ttu-id="1620a-113">Önceki komutla oluşturulan dizine gidin. `botsay`</span><span class="sxs-lookup"><span data-stu-id="1620a-113">Navigate to the `botsay` directory created by the previous command.</span></span>

## <a name="add-the-code"></a><span data-ttu-id="1620a-114">Kodu ekleyin</span><span class="sxs-lookup"><span data-stu-id="1620a-114">Add the code</span></span>

<span data-ttu-id="1620a-115">Dosyayı, `vim` veya Visual Studio Code gibi sık kullanılan metin düzenleyicinizle açın. [](https://code.visualstudio.com/) `Program.cs`</span><span class="sxs-lookup"><span data-stu-id="1620a-115">Open the `Program.cs` file with your favorite text editor, such as `vim` or [Visual Studio Code](https://code.visualstudio.com/).</span></span>

<span data-ttu-id="1620a-116">Aşağıdaki `using` yönergeyi dosyanın en üstüne ekleyin; Bu, kodun, uygulamanın sürüm bilgilerini görüntülemesi için kod kısaltmanıza yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="1620a-116">Add the following `using` directive to the top of the file, this helps shorten the code to display the version information of the application.</span></span>

```csharp
using System.Reflection;
```

<span data-ttu-id="1620a-117">Sonra, `Main` yöntemine aşağı gidin.</span><span class="sxs-lookup"><span data-stu-id="1620a-117">Next, move down to the `Main` method.</span></span> <span data-ttu-id="1620a-118">Yöntemi, uygulamanız için komut satırı bağımsız değişkenlerini işlemek üzere aşağıdaki kodla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="1620a-118">Replace the method with the following code to process the command-line arguments for your application.</span></span> <span data-ttu-id="1620a-119">Bağımsız değişken geçirilmemişse, kısa bir yardım iletisi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="1620a-119">If no arguments were passed, a short help message is displayed.</span></span> <span data-ttu-id="1620a-120">Aksi takdirde, bu bağımsız değişkenlerin tümü bir dizeye dönüştürülür ve bot ile birlikte yazdırılır.</span><span class="sxs-lookup"><span data-stu-id="1620a-120">Otherwise, all of those arguments are transformed into a string and printed with the bot.</span></span>

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

### <a name="create-the-bot"></a><span data-ttu-id="1620a-121">Bot oluşturma</span><span class="sxs-lookup"><span data-stu-id="1620a-121">Create the bot</span></span>

<span data-ttu-id="1620a-122">Sonra, bir dize parametresi alan adlı `ShowBot` yeni bir yöntem ekleyin.</span><span class="sxs-lookup"><span data-stu-id="1620a-122">Next, add a new method named `ShowBot` that takes a string parameter.</span></span> <span data-ttu-id="1620a-123">Bu yöntem, iletiyi ve ASCII bot 'ı yazdırır.</span><span class="sxs-lookup"><span data-stu-id="1620a-123">This method prints out the message and the ASCII bot.</span></span> <span data-ttu-id="1620a-124">Bir dotnetbot kodu [dotnetbot](https://github.com/dotnet/core/blob/master/samples/dotnetsay/Program.cs) örneğinden alındı.</span><span class="sxs-lookup"><span data-stu-id="1620a-124">The ASCII bot code was taken from the [dotnetbot](https://github.com/dotnet/core/blob/master/samples/dotnetsay/Program.cs) sample.</span></span>

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

### <a name="test-the-tool"></a><span data-ttu-id="1620a-125">Aracı test etme</span><span class="sxs-lookup"><span data-stu-id="1620a-125">Test the tool</span></span>

<span data-ttu-id="1620a-126">Projeyi çalıştırın ve çıktıyı görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="1620a-126">Run the project and see the output.</span></span> <span data-ttu-id="1620a-127">Farklı sonuçları görmek için komut satırının bu çeşitlemelerini deneyin:</span><span class="sxs-lookup"><span data-stu-id="1620a-127">Try these variations of the command-line to see different results:</span></span>

```csharp
dotnet run
dotnet run -- "Hello from the bot"
dotnet run -- hello from the bot
```

<span data-ttu-id="1620a-128">`--` Sınırlayıcıdan sonraki tüm bağımsız değişkenler uygulamanıza geçirilir.</span><span class="sxs-lookup"><span data-stu-id="1620a-128">All arguments after the `--` delimiter are passed to your application.</span></span>

## <a name="setup-the-global-tool"></a><span data-ttu-id="1620a-129">Genel aracı kurma</span><span class="sxs-lookup"><span data-stu-id="1620a-129">Setup the global tool</span></span>

<span data-ttu-id="1620a-130">Uygulamayı küresel bir araç olarak paketleyebilir ve dağıtabilmeniz için önce proje dosyasını değiştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="1620a-130">Before you can pack and distribute the application as a Global Tool, you need to modify the project file.</span></span> <span data-ttu-id="1620a-131">Dosyayı açın ve `<Project><PropertyGroup>` düğüme üç yeni XML düğümü ekleyin: `botsay.csproj`</span><span class="sxs-lookup"><span data-stu-id="1620a-131">Open the `botsay.csproj` file and add three new XML nodes to the `<Project><PropertyGroup>` node:</span></span>

- `<PackAsTool>`\
<span data-ttu-id="1620a-132">ISTENIR Uygulamanın genel bir araç olarak yüklenmek üzere paketleneceğine bildirir.</span><span class="sxs-lookup"><span data-stu-id="1620a-132">[REQUIRED] Indicates that the application will be packaged for install as a Global Tool.</span></span>

- `<ToolCommandName>`\
<span data-ttu-id="1620a-133">SEÇIM Araç için alternatif bir ad, aksi takdirde araç için komut adı proje dosyasından sonra adlandıralınacaktır.</span><span class="sxs-lookup"><span data-stu-id="1620a-133">[OPTIONAL] An alternative name for the tool, otherwise the command name for the tool will be named after the project file.</span></span> <span data-ttu-id="1620a-134">Pakette birden fazla araca sahip olabilirsiniz, benzersiz ve kolay bir ad seçmek aynı paketteki diğer araçlardan ayırt edilmesine yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="1620a-134">You can have multiple tools in a package, choosing a unique and friendly name helps differentiate from other tools in the same package.</span></span>

- `<PackageOutputPath>`\
<span data-ttu-id="1620a-135">SEÇIM NuGet paketinin üretileceği yer.</span><span class="sxs-lookup"><span data-stu-id="1620a-135">[OPTIONAL] Where the NuGet package will be produced.</span></span> <span data-ttu-id="1620a-136">NuGet paketi, .NET Core CLI genel araçların aracınızı yüklemek için kullandığı şeydir.</span><span class="sxs-lookup"><span data-stu-id="1620a-136">The NuGet package is what the .NET Core CLI Global Tools uses to install your tool.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.1</TargetFramework>

    <PackAsTool>true</PackAsTool>
    <ToolCommandName>botsay</ToolCommandName>
    <PackageOutputPath>./nupkg</PackageOutputPath>

  </PropertyGroup>

</Project>
```

<span data-ttu-id="1620a-137">`<PackageOutputPath>` İsteğe bağlı olsa da, bu örnekte kullanın.</span><span class="sxs-lookup"><span data-stu-id="1620a-137">Even though `<PackageOutputPath>` is optional, use it in this example.</span></span> <span data-ttu-id="1620a-138">Ayarladığınızdan emin olun: `<PackageOutputPath>./nupkg</PackageOutputPath>`.</span><span class="sxs-lookup"><span data-stu-id="1620a-138">Make sure you set it: `<PackageOutputPath>./nupkg</PackageOutputPath>`.</span></span>

<span data-ttu-id="1620a-139">Ardından, uygulamanız için bir NuGet paketi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="1620a-139">Next, create a NuGet package for your application.</span></span>

```console
dotnet pack
```

<span data-ttu-id="1620a-140">Dosya, dosyadan `<PackageOutputPath>` xml değeri `botsay.csproj` tarafından tanımlanan klasörde oluşturulur, bu örnekte `./nupkg` klasörüdür. `botsay.1.0.0.nupkg`</span><span class="sxs-lookup"><span data-stu-id="1620a-140">The `botsay.1.0.0.nupkg` file is created in the folder identified by the `<PackageOutputPath>` XML value from the `botsay.csproj` file, which in this example is the `./nupkg` folder.</span></span> <span data-ttu-id="1620a-141">Bu, yüklemeyi ve test yapmayı kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="1620a-141">This makes it easy to install and test.</span></span> <span data-ttu-id="1620a-142">Bir aracı herkese açık bir şekilde yayınlamak istediğinizde, ' ye <https://www.nuget.org>yükleyin.</span><span class="sxs-lookup"><span data-stu-id="1620a-142">When you want to release a tool publicly, upload it to <https://www.nuget.org>.</span></span> <span data-ttu-id="1620a-143">Araç NuGet 'de kullanılabilir olduğunda, geliştiriciler `--global` [DotNet aracı yükleme](dotnet-tool-install.md) komutu seçeneğini kullanarak aracın Kullanıcı genelindeki bir yüklemesini gerçekleştirebilir.</span><span class="sxs-lookup"><span data-stu-id="1620a-143">Once the tool is available on NuGet, developers can perform a user-wide installation of the tool using the `--global` option of the [dotnet tool install](dotnet-tool-install.md) command.</span></span>

<span data-ttu-id="1620a-144">Artık bir paketiniz olduğuna göre, aracı bu paketten yükleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="1620a-144">Now that you have a package, install the tool from that package:</span></span>

```console
dotnet tool install --global --add-source ./nupkg botsay
```

<span data-ttu-id="1620a-145">Parametresi, .NET Core CLI NuGet paketleri için ek bir kaynak `./nupkg` akışı olarak klasörü `<PackageOutputPath>` (klasör) geçici olarak kullanmasını söyler. `--add-source`</span><span class="sxs-lookup"><span data-stu-id="1620a-145">The `--add-source` parameter tells the .NET Core CLI to temporarily use the `./nupkg` folder (our `<PackageOutputPath>` folder) as an additional source feed for NuGet packages.</span></span> <span data-ttu-id="1620a-146">Genel araçları yükleme hakkında daha fazla bilgi için bkz. [.NET Core genel araçlarına genel bakış](global-tools.md).</span><span class="sxs-lookup"><span data-stu-id="1620a-146">For more information about installing Global Tools, see [.NET Core Global Tools overview](global-tools.md).</span></span>

<span data-ttu-id="1620a-147">Yükleme başarılı olursa, aşağıdaki örneğe benzer şekilde, aracı ve yüklü sürümü çağırmak için kullanılan komutu gösteren bir ileti görüntülenir:</span><span class="sxs-lookup"><span data-stu-id="1620a-147">If installation is successful, a message is displayed showing the command used to call the tool and the version installed, similar to the following example:</span></span>

```output
You can invoke the tool using the following command: botsay
Tool 'botsay' (version '1.0.0') was successfully installed.
```

<span data-ttu-id="1620a-148">Artık araçtan bir yanıt yazabilir `botsay` ve yanıt alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1620a-148">You should now be able to type `botsay` and get a response from the tool.</span></span>

> [!NOTE]
> <span data-ttu-id="1620a-149">Yüklemenin başarılı olması, ancak `botsay` komutunu kullanmanızın ardından, yolu yenilemek için yeni bir Terminal açmanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="1620a-149">If the install was successful, but you cannot use the `botsay` command, you may need to open a new terminal to refresh the PATH.</span></span>

## <a name="remove-the-tool"></a><span data-ttu-id="1620a-150">Aracı kaldır</span><span class="sxs-lookup"><span data-stu-id="1620a-150">Remove the tool</span></span>

<span data-ttu-id="1620a-151">Araç ile deneme tamamladıktan sonra, aşağıdaki komutla kaldırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="1620a-151">Once you're done experimenting with the tool, you can remove it with the following command:</span></span>

```console
dotnet tool uninstall -g botsay
```
