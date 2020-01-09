---
title: .NET Core küresel aracı oluşturma
description: Genel bir aracın nasıl oluşturulacağını açıklar. Genel araç, .NET Core CLI aracılığıyla yüklenen bir konsol uygulamasıdır.
author: Thraka
ms.author: adegeo
ms.date: 08/22/2018
ms.openlocfilehash: 1daecf7234f02a5fe0dcf25cf7edbb0af327b8c1
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75343518"
---
# <a name="create-a-net-core-global-tool-using-the-net-core-cli"></a><span data-ttu-id="5c8e0-104">.NET Core CLI kullanarak bir .NET Core genel aracı oluşturun</span><span class="sxs-lookup"><span data-stu-id="5c8e0-104">Create a .NET Core Global Tool using the .NET Core CLI</span></span>

<span data-ttu-id="5c8e0-105">Bu makalede bir .NET Core küresel aracı oluşturma ve paketleme hakkında öğretilir.</span><span class="sxs-lookup"><span data-stu-id="5c8e0-105">This article teaches you how to create and package a .NET Core Global Tool.</span></span> <span data-ttu-id="5c8e0-106">.NET Core CLI, bir konsol uygulamasını küresel bir araç olarak oluşturmanıza olanak tanır. Bu, başkalarının kolayca yükleyip çalıştırabilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="5c8e0-106">The .NET Core CLI allows you to create a console application as a Global Tool, which others can easily install and run.</span></span> <span data-ttu-id="5c8e0-107">.NET Core küresel araçları, .NET Core CLI yüklenen NuGet paketlerdir.</span><span class="sxs-lookup"><span data-stu-id="5c8e0-107">.NET Core Global Tools are NuGet packages that are installed from the .NET Core CLI.</span></span> <span data-ttu-id="5c8e0-108">Küresel araçlar hakkında daha fazla bilgi için bkz. [.NET Core genel araçlarına genel bakış](global-tools.md).</span><span class="sxs-lookup"><span data-stu-id="5c8e0-108">For more information about Global Tools, see [.NET Core Global Tools overview](global-tools.md).</span></span>

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

## <a name="create-a-project"></a><span data-ttu-id="5c8e0-109">Proje oluştur</span><span class="sxs-lookup"><span data-stu-id="5c8e0-109">Create a project</span></span>

<span data-ttu-id="5c8e0-110">Bu makale bir proje oluşturmak ve yönetmek için .NET Core CLI kullanır.</span><span class="sxs-lookup"><span data-stu-id="5c8e0-110">This article uses the .NET Core CLI to create and manage a project.</span></span>

<span data-ttu-id="5c8e0-111">Örnek aracımız, bir ASCII bot üreten ve bir ileti yazdıran bir konsol uygulaması olacaktır.</span><span class="sxs-lookup"><span data-stu-id="5c8e0-111">Our example tool will be a console application that generates an ASCII bot and prints a message.</span></span> <span data-ttu-id="5c8e0-112">İlk olarak, yeni bir .NET Core konsol uygulaması oluşturun.</span><span class="sxs-lookup"><span data-stu-id="5c8e0-112">First, create a new .NET Core Console Application.</span></span>

```dotnetcli
dotnet new console -o botsay
```

<span data-ttu-id="5c8e0-113">Önceki komut tarafından oluşturulan `botsay` dizinine gidin.</span><span class="sxs-lookup"><span data-stu-id="5c8e0-113">Navigate to the `botsay` directory created by the previous command.</span></span>

## <a name="add-the-code"></a><span data-ttu-id="5c8e0-114">Kod ekleme</span><span class="sxs-lookup"><span data-stu-id="5c8e0-114">Add the code</span></span>

<span data-ttu-id="5c8e0-115">`Program.cs` dosyasını `vim` veya [Visual Studio Code](https://code.visualstudio.com/)gibi en sevdiğiniz metin düzenleyicinizle açın.</span><span class="sxs-lookup"><span data-stu-id="5c8e0-115">Open the `Program.cs` file with your favorite text editor, such as `vim` or [Visual Studio Code](https://code.visualstudio.com/).</span></span>

<span data-ttu-id="5c8e0-116">Aşağıdaki `using` yönergesini dosyanın en üstüne ekleyin, bu, uygulamanın sürüm bilgilerini göstermek için kodu kısaltmanıza yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="5c8e0-116">Add the following `using` directive to the top of the file, this helps shorten the code to display the version information of the application.</span></span>

```csharp
using System.Reflection;
```

<span data-ttu-id="5c8e0-117">Sonra `Main` yöntemine gidin.</span><span class="sxs-lookup"><span data-stu-id="5c8e0-117">Next, move down to the `Main` method.</span></span> <span data-ttu-id="5c8e0-118">Yöntemi, uygulamanız için komut satırı bağımsız değişkenlerini işlemek üzere aşağıdaki kodla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="5c8e0-118">Replace the method with the following code to process the command-line arguments for your application.</span></span> <span data-ttu-id="5c8e0-119">Bağımsız değişken geçirilmemişse, kısa bir yardım iletisi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="5c8e0-119">If no arguments were passed, a short help message is displayed.</span></span> <span data-ttu-id="5c8e0-120">Aksi takdirde, bu bağımsız değişkenlerin tümü bir dizeye dönüştürülür ve bot ile birlikte yazdırılır.</span><span class="sxs-lookup"><span data-stu-id="5c8e0-120">Otherwise, all of those arguments are transformed into a string and printed with the bot.</span></span>

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

### <a name="create-the-bot"></a><span data-ttu-id="5c8e0-121">Bot oluşturma</span><span class="sxs-lookup"><span data-stu-id="5c8e0-121">Create the bot</span></span>

<span data-ttu-id="5c8e0-122">Sonra, bir dize parametresi alan `ShowBot` adlı yeni bir yöntem ekleyin.</span><span class="sxs-lookup"><span data-stu-id="5c8e0-122">Next, add a new method named `ShowBot` that takes a string parameter.</span></span> <span data-ttu-id="5c8e0-123">Bu yöntem, iletiyi ve ASCII bot 'ı yazdırır.</span><span class="sxs-lookup"><span data-stu-id="5c8e0-123">This method prints out the message and the ASCII bot.</span></span> <span data-ttu-id="5c8e0-124">Bir [dotnetbot kodu dotnetbot](https://github.com/dotnet/core/blob/master/samples/dotnetsay/Program.cs) örneğinden alındı.</span><span class="sxs-lookup"><span data-stu-id="5c8e0-124">The ASCII bot code was taken from the [dotnetbot](https://github.com/dotnet/core/blob/master/samples/dotnetsay/Program.cs) sample.</span></span>

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

### <a name="test-the-tool"></a><span data-ttu-id="5c8e0-125">Aracı test etme</span><span class="sxs-lookup"><span data-stu-id="5c8e0-125">Test the tool</span></span>

<span data-ttu-id="5c8e0-126">Projeyi çalıştırın ve çıktıyı görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="5c8e0-126">Run the project and see the output.</span></span> <span data-ttu-id="5c8e0-127">Farklı sonuçları görmek için komut satırında bu çeşitlemeleri deneyin:</span><span class="sxs-lookup"><span data-stu-id="5c8e0-127">Try these variations at the command line to see different results:</span></span>

```dotnetcli
dotnet run
dotnet run -- "Hello from the bot"
dotnet run -- hello from the bot
```

<span data-ttu-id="5c8e0-128">`--` sınırlayıcısından sonraki tüm bağımsız değişkenler uygulamanıza geçirilir.</span><span class="sxs-lookup"><span data-stu-id="5c8e0-128">All arguments after the `--` delimiter are passed to your application.</span></span>

## <a name="set-up-the-global-tool"></a><span data-ttu-id="5c8e0-129">Genel aracı ayarlama</span><span class="sxs-lookup"><span data-stu-id="5c8e0-129">Set up the global tool</span></span>

<span data-ttu-id="5c8e0-130">Uygulamayı küresel bir araç olarak paketleyebilir ve dağıtabilmeniz için önce proje dosyasını değiştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="5c8e0-130">Before you can pack and distribute the application as a Global Tool, you need to modify the project file.</span></span> <span data-ttu-id="5c8e0-131">`botsay.csproj` dosyasını açın ve `<Project><PropertyGroup>` düğümüne üç yeni XML düğümü ekleyin:</span><span class="sxs-lookup"><span data-stu-id="5c8e0-131">Open the `botsay.csproj` file and add three new XML nodes to the `<Project><PropertyGroup>` node:</span></span>

- `<PackAsTool>`\
<span data-ttu-id="5c8e0-132">ISTENIR Uygulamanın genel bir araç olarak yüklenmek üzere paketleneceğine bildirir.</span><span class="sxs-lookup"><span data-stu-id="5c8e0-132">[REQUIRED] Indicates that the application will be packaged for install as a Global Tool.</span></span>

- `<ToolCommandName>`\
<span data-ttu-id="5c8e0-133">SEÇIM Araç için alternatif bir ad, aksi takdirde araç için komut adı proje dosyasından sonra adlandıralınacaktır.</span><span class="sxs-lookup"><span data-stu-id="5c8e0-133">[OPTIONAL] An alternative name for the tool, otherwise the command name for the tool will be named after the project file.</span></span> <span data-ttu-id="5c8e0-134">Pakette birden fazla araca sahip olabilirsiniz, benzersiz ve kolay bir ad seçmek aynı paketteki diğer araçlardan ayırt edilmesine yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="5c8e0-134">You can have multiple tools in a package, choosing a unique and friendly name helps differentiate from other tools in the same package.</span></span>

- `<PackageOutputPath>`\
<span data-ttu-id="5c8e0-135">SEÇIM NuGet paketinin üretileceği yer.</span><span class="sxs-lookup"><span data-stu-id="5c8e0-135">[OPTIONAL] Where the NuGet package will be produced.</span></span> <span data-ttu-id="5c8e0-136">NuGet paketi, .NET Core CLI genel araçların aracınızı yüklemek için kullandığı şeydir.</span><span class="sxs-lookup"><span data-stu-id="5c8e0-136">The NuGet package is what the .NET Core CLI Global Tools uses to install your tool.</span></span>

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

<span data-ttu-id="5c8e0-137">`<PackageOutputPath>`, isteğe bağlı olsa da, bu örnekte kullanın.</span><span class="sxs-lookup"><span data-stu-id="5c8e0-137">Even though `<PackageOutputPath>` is optional, use it in this example.</span></span> <span data-ttu-id="5c8e0-138">Ayarladığınızdan emin olun: `<PackageOutputPath>./nupkg</PackageOutputPath>`.</span><span class="sxs-lookup"><span data-stu-id="5c8e0-138">Make sure you set it: `<PackageOutputPath>./nupkg</PackageOutputPath>`.</span></span>

<span data-ttu-id="5c8e0-139">Ardından, uygulamanız için bir NuGet paketi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="5c8e0-139">Next, create a NuGet package for your application.</span></span>

```dotnetcli
dotnet pack
```

<span data-ttu-id="5c8e0-140">`botsay.1.0.0.nupkg` dosyası, bu örnekte `./nupkg` klasörü olan `botsay.csproj` dosyasından `<PackageOutputPath>` XML değeri tarafından tanımlanan klasörde oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="5c8e0-140">The `botsay.1.0.0.nupkg` file is created in the folder identified by the `<PackageOutputPath>` XML value from the `botsay.csproj` file, which in this example is the `./nupkg` folder.</span></span> <span data-ttu-id="5c8e0-141">Bu, yüklemeyi ve test yapmayı kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="5c8e0-141">This makes it easy to install and test.</span></span> <span data-ttu-id="5c8e0-142">Bir aracı herkese açık bir şekilde yayınlamak istediğinizde, <https://www.nuget.org>' ye yükleyin.</span><span class="sxs-lookup"><span data-stu-id="5c8e0-142">When you want to release a tool publicly, upload it to <https://www.nuget.org>.</span></span> <span data-ttu-id="5c8e0-143">Araç NuGet 'de kullanılabilir olduğunda, geliştiriciler [DotNet aracı install](dotnet-tool-install.md) komutunun `--global` seçeneğini kullanarak aracın Kullanıcı genelindeki bir yüklemesini gerçekleştirebilir.</span><span class="sxs-lookup"><span data-stu-id="5c8e0-143">Once the tool is available on NuGet, developers can perform a user-wide installation of the tool using the `--global` option of the [dotnet tool install](dotnet-tool-install.md) command.</span></span>

<span data-ttu-id="5c8e0-144">Artık bir paketiniz olduğuna göre, aracı bu paketten yükleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="5c8e0-144">Now that you have a package, install the tool from that package:</span></span>

```dotnetcli
dotnet tool install --global --add-source ./nupkg botsay
```

<span data-ttu-id="5c8e0-145">`--add-source` parametresi, .NET Core CLI, NuGet paketleri için ek bir kaynak akışı olarak `./nupkg` klasörünü (`<PackageOutputPath>` klasörü) geçici olarak kullanmasını söyler.</span><span class="sxs-lookup"><span data-stu-id="5c8e0-145">The `--add-source` parameter tells the .NET Core CLI to temporarily use the `./nupkg` folder (our `<PackageOutputPath>` folder) as an additional source feed for NuGet packages.</span></span> <span data-ttu-id="5c8e0-146">Genel araçları yükleme hakkında daha fazla bilgi için bkz. [.NET Core genel araçlarına genel bakış](global-tools.md).</span><span class="sxs-lookup"><span data-stu-id="5c8e0-146">For more information about installing Global Tools, see [.NET Core Global Tools overview](global-tools.md).</span></span>

<span data-ttu-id="5c8e0-147">Yükleme başarılı olursa, aşağıdaki örneğe benzer şekilde, aracı ve yüklü sürümü çağırmak için kullanılan komutu gösteren bir ileti görüntülenir:</span><span class="sxs-lookup"><span data-stu-id="5c8e0-147">If installation is successful, a message is displayed showing the command used to call the tool and the version installed, similar to the following example:</span></span>

```output
You can invoke the tool using the following command: botsay
Tool 'botsay' (version '1.0.0') was successfully installed.
```

<span data-ttu-id="5c8e0-148">Artık `botsay` yazabilir ve araçtan bir yanıt alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5c8e0-148">You should now be able to type `botsay` and get a response from the tool.</span></span>

> [!NOTE]
> <span data-ttu-id="5c8e0-149">Yüklemesi başarılı olduysa, ancak `botsay` komutunu kullanamazsınız, yolu yenilemek için yeni bir Terminal açmanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="5c8e0-149">If the install was successful, but you cannot use the `botsay` command, you may need to open a new terminal to refresh the PATH.</span></span>

## <a name="remove-the-tool"></a><span data-ttu-id="5c8e0-150">Aracı kaldır</span><span class="sxs-lookup"><span data-stu-id="5c8e0-150">Remove the tool</span></span>

<span data-ttu-id="5c8e0-151">Araç ile deneme tamamladıktan sonra, aşağıdaki komutla kaldırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="5c8e0-151">Once you're done experimenting with the tool, you can remove it with the following command:</span></span>

```dotnetcli
dotnet tool uninstall -g botsay
```
