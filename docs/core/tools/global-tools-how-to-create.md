---
title: .NET Core genel aracı oluşturma
description: Genel bir aracı oluşturmayı açıklar. Genel aracı ile .NET Core CLI'yı yüklediğiniz bir konsol uygulamasıdır.
author: Thraka
ms.author: adegeo
ms.date: 08/22/2018
ms.openlocfilehash: 3d0a64d0473f51d73892cd40633e2982c1130469
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61647950"
---
# <a name="create-a-net-core-global-tool-using-the-net-core-cli"></a><span data-ttu-id="76c69-104">Bir .NET Core genel .NET Core CLI'yı kullanarak aracı oluşturma</span><span class="sxs-lookup"><span data-stu-id="76c69-104">Create a .NET Core Global Tool using the .NET Core CLI</span></span>

<span data-ttu-id="76c69-105">Bu makalede nasıl oluşturulacağı ve bir .NET Core genel aracı paketlemeyi öğretir.</span><span class="sxs-lookup"><span data-stu-id="76c69-105">This article teaches you how to create and package a .NET Core Global Tool.</span></span> <span data-ttu-id="76c69-106">.NET Core CLI bir konsol uygulaması olarak bir genel diğer kolayca yükleyip çalıştırabileceği Aracı'nı oluşturmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="76c69-106">The .NET Core CLI allows you to create a console application as a Global Tool, which others can easily install and run.</span></span> <span data-ttu-id="76c69-107">.NET core genel araçları, .NET Core CLI üzerinden yüklü olan NuGet paketlerdir.</span><span class="sxs-lookup"><span data-stu-id="76c69-107">.NET Core Global Tools are NuGet packages that are installed from the .NET Core CLI.</span></span> <span data-ttu-id="76c69-108">Genel araçları hakkında daha fazla bilgi için bkz. [.NET Core Araçları Genel genel bakış](global-tools.md).</span><span class="sxs-lookup"><span data-stu-id="76c69-108">For more information about Global Tools, see [.NET Core Global Tools overview](global-tools.md).</span></span>

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

## <a name="create-a-project"></a><span data-ttu-id="76c69-109">Proje oluşturma</span><span class="sxs-lookup"><span data-stu-id="76c69-109">Create a project</span></span>

<span data-ttu-id="76c69-110">Bu makalede .NET Core CLI oluşturmak ve bir proje yönetmek üzere kullanılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="76c69-110">This article uses the .NET Core CLI to create and manage a project.</span></span>

<span data-ttu-id="76c69-111">Örnek aracımızı ASCII bot oluşturur ve bir ileti yazdıran bir konsol uygulaması olacaktır.</span><span class="sxs-lookup"><span data-stu-id="76c69-111">Our example tool will be a console application that generates an ASCII bot and prints a message.</span></span> <span data-ttu-id="76c69-112">İlk olarak, yeni bir .NET Core konsol uygulaması oluşturun.</span><span class="sxs-lookup"><span data-stu-id="76c69-112">First, create a new .NET Core Console Application.</span></span>

```console
dotnet new console -o botsay
```

<span data-ttu-id="76c69-113">Gidin `botsay` önceki komutu tarafından oluşturulan dizin.</span><span class="sxs-lookup"><span data-stu-id="76c69-113">Navigate to the `botsay` directory created by the previous command.</span></span>

## <a name="add-the-code"></a><span data-ttu-id="76c69-114">Kod ekleme</span><span class="sxs-lookup"><span data-stu-id="76c69-114">Add the code</span></span>

<span data-ttu-id="76c69-115">Açık `Program.cs` gibi sevdiğiniz bir metin düzenleyici ile dosya `vim` veya [Visual Studio Code](https://code.visualstudio.com/).</span><span class="sxs-lookup"><span data-stu-id="76c69-115">Open the `Program.cs` file with your favorite text editor, such as `vim` or [Visual Studio Code](https://code.visualstudio.com/).</span></span>

<span data-ttu-id="76c69-116">Aşağıdaki `using` dosyanın en üstüne yönergesi, bu uygulamanın sürüm bilgilerini görüntülemek için kod kısaltın yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="76c69-116">Add the following `using` directive to the top of the file, this helps shorten the code to display the version information of the application.</span></span>

```csharp
using System.Reflection;
```

<span data-ttu-id="76c69-117">Ardından, Aşağı Taşı `Main` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="76c69-117">Next, move down to the `Main` method.</span></span> <span data-ttu-id="76c69-118">Yöntemi, uygulamanız için komut satırı bağımsız değişkenleri işlemek için aşağıdaki kod ile değiştirin.</span><span class="sxs-lookup"><span data-stu-id="76c69-118">Replace the method with the following code to process the command-line arguments for your application.</span></span> <span data-ttu-id="76c69-119">Hiçbir bağımsız değişken geçirildi, bir kısa Yardım iletisi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="76c69-119">If no arguments were passed, a short help message is displayed.</span></span> <span data-ttu-id="76c69-120">Aksi takdirde, tüm bu bağımsız değişken bir dizeye dönüştürülür ve ile bot yazdırılır.</span><span class="sxs-lookup"><span data-stu-id="76c69-120">Otherwise, all of those arguments are transformed into a string and printed with the bot.</span></span>

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

### <a name="create-the-bot"></a><span data-ttu-id="76c69-121">Bot oluşturma</span><span class="sxs-lookup"><span data-stu-id="76c69-121">Create the bot</span></span>

<span data-ttu-id="76c69-122">Ardından, adlı yeni bir yöntem ekleyin `ShowBot` , bir dize parametresi alan.</span><span class="sxs-lookup"><span data-stu-id="76c69-122">Next, add a new method named `ShowBot` that takes a string parameter.</span></span> <span data-ttu-id="76c69-123">Bu yöntem, ileti ve ASCII bot out yazdırır.</span><span class="sxs-lookup"><span data-stu-id="76c69-123">This method prints out the message and the ASCII bot.</span></span> <span data-ttu-id="76c69-124">ASCII bot kodu alındığı [dotnetbot](https://github.com/dotnet/core/blob/master/samples/dotnetsay/Program.cs) örnek.</span><span class="sxs-lookup"><span data-stu-id="76c69-124">The ASCII bot code was taken from the [dotnetbot](https://github.com/dotnet/core/blob/master/samples/dotnetsay/Program.cs) sample.</span></span>

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

### <a name="test-the-tool"></a><span data-ttu-id="76c69-125">Aracı'nı test edin</span><span class="sxs-lookup"><span data-stu-id="76c69-125">Test the tool</span></span>

<span data-ttu-id="76c69-126">Projeyi çalıştırın ve çıktıyı görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="76c69-126">Run the project and see the output.</span></span> <span data-ttu-id="76c69-127">Bu farklı sonuçlar görmek için komut satırı çeşitleri deneyin:</span><span class="sxs-lookup"><span data-stu-id="76c69-127">Try these variations of the command-line to see different results:</span></span>

```csharp
dotnet run
dotnet run -- "Hello from the bot"
dotnet run -- hello from the bot
```

<span data-ttu-id="76c69-128">Tüm bağımsız değişkenlerden sonra `--` sınırlayıcı uygulamanıza geçirilir.</span><span class="sxs-lookup"><span data-stu-id="76c69-128">All arguments after the `--` delimiter are passed to your application.</span></span>

## <a name="setup-the-global-tool"></a><span data-ttu-id="76c69-129">Genel aracı Kurulumu</span><span class="sxs-lookup"><span data-stu-id="76c69-129">Setup the global tool</span></span>

<span data-ttu-id="76c69-130">Paketi ve uygulamanızı genel bir aracı olarak dağıtmak için önce proje dosyasını değiştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="76c69-130">Before you can pack and distribute the application as a Global Tool, you need to modify the project file.</span></span> <span data-ttu-id="76c69-131">Açık `botsay.csproj` dosya ve üç yeni XML düğüm ekleme `<Project><PropertyGroup>` düğüm:</span><span class="sxs-lookup"><span data-stu-id="76c69-131">Open the `botsay.csproj` file and add three new XML nodes to the `<Project><PropertyGroup>` node:</span></span>

- `<PackAsTool>`\
<span data-ttu-id="76c69-132">[GEREKLİ] Uygulama genel bir aracı olarak yüklenmesi için paketlendi olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="76c69-132">[REQUIRED] Indicates that the application will be packaged for install as a Global Tool.</span></span>

- `<ToolCommandName>`\
<span data-ttu-id="76c69-133">[İSTEĞE BAĞLI] Aracı için bir diğer ad, aksi takdirde sonra proje dosyası aracı için komut adı adlandırılacaktır.</span><span class="sxs-lookup"><span data-stu-id="76c69-133">[OPTIONAL] An alternative name for the tool, otherwise the command name for the tool will be named after the project file.</span></span> <span data-ttu-id="76c69-134">Benzersiz ve kolay bir ad yardımcı olan diğer araçlar aynı pakette ayırt seçerek bir pakette birden çok aracı olabilir.</span><span class="sxs-lookup"><span data-stu-id="76c69-134">You can have multiple tools in a package, choosing a unique and friendly name helps differentiate from other tools in the same package.</span></span>

- `<PackageOutputPath>`\
<span data-ttu-id="76c69-135">[İSTEĞE BAĞLI] NuGet paketini burada oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="76c69-135">[OPTIONAL] Where the NuGet package will be produced.</span></span> <span data-ttu-id="76c69-136">NuGet paketini, .NET Core CLI genel araçları, aracı yüklemek için kullandığı ' dir.</span><span class="sxs-lookup"><span data-stu-id="76c69-136">The NuGet package is what the .NET Core CLI Global Tools uses to install your tool.</span></span>

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

<span data-ttu-id="76c69-137">Olsa da `<PackageOutputPath>` isteğe bağlıdır, bu örnekte kullanın.</span><span class="sxs-lookup"><span data-stu-id="76c69-137">Even though `<PackageOutputPath>` is optional, use it in this example.</span></span> <span data-ttu-id="76c69-138">Bunu ayarladığınızdan emin olun: `<PackageOutputPath>./nupkg</PackageOutputPath>`.</span><span class="sxs-lookup"><span data-stu-id="76c69-138">Make sure you set it: `<PackageOutputPath>./nupkg</PackageOutputPath>`.</span></span>

<span data-ttu-id="76c69-139">Ardından, uygulamanız için bir NuGet paketi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="76c69-139">Next, create a NuGet package for your application.</span></span>

```console
dotnet pack
```

<span data-ttu-id="76c69-140">`botsay.1.0.0.nupkg` Dosyası tarafından tanımlanan klasöründe oluşturulur `<PackageOutputPath>` XML değerinden `botsay.csproj` olan bu örnekte dosyası `./nupkg` klasör.</span><span class="sxs-lookup"><span data-stu-id="76c69-140">The `botsay.1.0.0.nupkg` file is created in the folder identified by the `<PackageOutputPath>` XML value from the `botsay.csproj` file, which in this example is the `./nupkg` folder.</span></span> <span data-ttu-id="76c69-141">Bu, yükleme ve test etmek kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="76c69-141">This makes it easy to install and test.</span></span> <span data-ttu-id="76c69-142">Bir aracı genel olarak yayınlamak istediğinizde, karşıya <https://www.nuget.org>.</span><span class="sxs-lookup"><span data-stu-id="76c69-142">When you want to release a tool publicly, upload it to <https://www.nuget.org>.</span></span> <span data-ttu-id="76c69-143">Aracı üzerinde NuGet kullanılabilir olduğunda, geliştiricilerin aracını kullanarak bir kullanıcı genelinde yükleme gerçekleştirebilirsiniz `--global` seçeneği [dotnet aracı yükleme](dotnet-tool-install.md) komutu.</span><span class="sxs-lookup"><span data-stu-id="76c69-143">Once the tool is available on NuGet, developers can perform a user-wide installation of the tool using the `--global` option of the [dotnet tool install](dotnet-tool-install.md) command.</span></span>

<span data-ttu-id="76c69-144">Bir paket olduğuna göre bu paketten aracını yükleyin:</span><span class="sxs-lookup"><span data-stu-id="76c69-144">Now that you have a package, install the tool from that package:</span></span>

```console
dotnet tool install --global --add-source ./nupkg botsay
```

<span data-ttu-id="76c69-145">`--add-source` Parametresi, geçici olarak kullanmak için .NET Core CLI bildirir `./nupkg` klasörü (bizim `<PackageOutputPath>` klasör) ek bir kaynak için NuGet paketlerini akış.</span><span class="sxs-lookup"><span data-stu-id="76c69-145">The `--add-source` parameter tells the .NET Core CLI to temporarily use the `./nupkg` folder (our `<PackageOutputPath>` folder) as an additional source feed for NuGet packages.</span></span> <span data-ttu-id="76c69-146">Genel araçlarını yükleme hakkında daha fazla bilgi için bkz. [.NET Core Araçları Genel genel bakış](global-tools.md).</span><span class="sxs-lookup"><span data-stu-id="76c69-146">For more information about installing Global Tools, see [.NET Core Global Tools overview](global-tools.md).</span></span>

<span data-ttu-id="76c69-147">Yükleme başarılı olursa, aracı ve yüklü sürümü çağırmak için kullanılan komut aşağıdaki örneğe benzer gösteren bir ileti görüntülenir:</span><span class="sxs-lookup"><span data-stu-id="76c69-147">If installation is successful, a message is displayed showing the command used to call the tool and the version installed, similar to the following example:</span></span>

```
You can invoke the tool using the following command: botsay
Tool 'botsay' (version '1.0.0') was successfully installed.
```

<span data-ttu-id="76c69-148">Artık türüne erişebileceğinizi `botsay` ve aracından bir yanıt alın.</span><span class="sxs-lookup"><span data-stu-id="76c69-148">You should now be able to type `botsay` and get a response from the tool.</span></span>

> [!NOTE]
> <span data-ttu-id="76c69-149">Yükleme başarılı oldu ancak kullanamazsınız `botsay` komutunu yolu yenilemek için yeni bir terminal açmanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="76c69-149">If the install was successful, but you cannot use the `botsay` command, you may need to open a new terminal to refresh the PATH.</span></span>

## <a name="remove-the-tool"></a><span data-ttu-id="76c69-150">Aracı kaldırma</span><span class="sxs-lookup"><span data-stu-id="76c69-150">Remove the tool</span></span>

<span data-ttu-id="76c69-151">İşiniz bittiğinde aracı ile denemeler, aşağıdaki komutla kaldırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="76c69-151">Once you're done experimenting with the tool, you can remove it with the following command:</span></span>

```console
dotnet tool uninstall -g botsay
```
