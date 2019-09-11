---
title: .NET Core kullanarak REST istemcisi oluşturma
description: Bu öğretici, .NET Core ve bu C# dilin çeşitli özelliklerini öğretir.
ms.date: 03/06/2017
ms.assetid: 51033ce2-7a53-4cdd-966d-9da15c8204d2
ms.openlocfilehash: 001a9cbaae1cdb57b6451bc42ce326864f8dcf7b
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850981"
---
# <a name="rest-client"></a><span data-ttu-id="1fb2e-103">REST istemcisi</span><span class="sxs-lookup"><span data-stu-id="1fb2e-103">REST client</span></span>

## <a name="introduction"></a><span data-ttu-id="1fb2e-104">Giriş</span><span class="sxs-lookup"><span data-stu-id="1fb2e-104">Introduction</span></span>

<span data-ttu-id="1fb2e-105">Bu öğretici, .NET Core ve bu C# dilin çeşitli özelliklerini öğretir.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-105">This tutorial teaches you a number of features in .NET Core and the C# language.</span></span> <span data-ttu-id="1fb2e-106">Şunları öğreneceksiniz:</span><span class="sxs-lookup"><span data-stu-id="1fb2e-106">You’ll learn:</span></span>

* <span data-ttu-id="1fb2e-107">.NET Core komut satırı arabirimi (CLı) temelleri.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-107">The basics of the .NET Core Command Line Interface (CLI).</span></span>
* <span data-ttu-id="1fb2e-108">C# Dil özelliklerine genel bakış.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-108">An overview of C# Language features.</span></span>
* <span data-ttu-id="1fb2e-109">NuGet ile bağımlılıkları yönetme</span><span class="sxs-lookup"><span data-stu-id="1fb2e-109">Managing dependencies with NuGet</span></span>
* <span data-ttu-id="1fb2e-110">HTTP Iletişimleri</span><span class="sxs-lookup"><span data-stu-id="1fb2e-110">HTTP Communications</span></span>
* <span data-ttu-id="1fb2e-111">JSON bilgilerini işleme</span><span class="sxs-lookup"><span data-stu-id="1fb2e-111">Processing JSON information</span></span>
* <span data-ttu-id="1fb2e-112">Yapılandırmayı özniteliklerle yönetme.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-112">Managing configuration with Attributes.</span></span>

<span data-ttu-id="1fb2e-113">GitHub 'da REST hizmetine HTTP Istekleri veren bir uygulama oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-113">You’ll build an application that issues HTTP Requests to a REST service on GitHub.</span></span> <span data-ttu-id="1fb2e-114">JSON biçiminde bilgileri okuyacaksınız ve bu JSON paketini C# nesnelerine dönüştürürsünüz.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-114">You'll read information in JSON format, and convert that JSON packet into C# objects.</span></span> <span data-ttu-id="1fb2e-115">Son olarak, C# nesneleriyle nasıl çalışacaksınız görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-115">Finally, you'll see how to work with C# objects.</span></span>

<span data-ttu-id="1fb2e-116">Bu öğreticide birçok özellik vardır.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-116">There are a lot of features in this tutorial.</span></span> <span data-ttu-id="1fb2e-117">Bunları birer birer oluşturalım.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-117">Let’s build them one by one.</span></span>

<span data-ttu-id="1fb2e-118">Bu konuyla ilgili [son örnekle](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient) birlikte izlemeyi tercih ediyorsanız, indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-118">If you prefer to follow along with the [final sample](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient) for this topic, you can download it.</span></span> <span data-ttu-id="1fb2e-119">İndirme yönergeleri için bkz. [örnekler ve öğreticiler](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="1fb2e-119">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="1fb2e-120">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="1fb2e-120">Prerequisites</span></span>

<span data-ttu-id="1fb2e-121">Makinenizi .NET Core çalıştıracak şekilde ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-121">You’ll need to set up your machine to run .NET core.</span></span> <span data-ttu-id="1fb2e-122">Yükleme yönergelerini [.NET Core İndirmeleri](https://dotnet.microsoft.com/download) sayfasında bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-122">You can find the installation instructions on the [.NET Core Downloads](https://dotnet.microsoft.com/download) page.</span></span> <span data-ttu-id="1fb2e-123">Bu uygulamayı Windows, Linux, macOS veya bir Docker kapsayıcısında çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-123">You can run this application on Windows, Linux, macOS or in a Docker container.</span></span>
<span data-ttu-id="1fb2e-124">En sevdiğiniz kod düzenleyicinizi yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-124">You’ll need to install your favorite code editor.</span></span> <span data-ttu-id="1fb2e-125">Aşağıdaki açıklamalar açık kaynaklı, platformlar arası bir düzenleyici olan [Visual Studio Code](https://code.visualstudio.com/)kullanır.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-125">The descriptions below use [Visual Studio Code](https://code.visualstudio.com/), which is an open source, cross platform editor.</span></span> <span data-ttu-id="1fb2e-126">Bununla birlikte, rahat olan her türlü aracı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-126">However, you can use whatever tools you are comfortable with.</span></span>

## <a name="create-the-application"></a><span data-ttu-id="1fb2e-127">Uygulamayı oluşturma</span><span class="sxs-lookup"><span data-stu-id="1fb2e-127">Create the Application</span></span>

<span data-ttu-id="1fb2e-128">İlk adım yeni bir uygulama oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-128">The first step is to create a new application.</span></span> <span data-ttu-id="1fb2e-129">Bir komut istemi açın ve uygulamanız için yeni bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-129">Open a command prompt and create a new directory for your application.</span></span> <span data-ttu-id="1fb2e-130">Geçerli dizini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-130">Make that the current directory.</span></span> <span data-ttu-id="1fb2e-131">`dotnet new console` Komutu komut istemine yazın.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-131">Type the command `dotnet new console` at the command prompt.</span></span> <span data-ttu-id="1fb2e-132">Bu, temel bir "Merhaba Dünya" uygulaması için başlangıç dosyalarını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-132">This creates the starter files for a basic "Hello World" application.</span></span> <span data-ttu-id="1fb2e-133">Bu yeni bir proje olduğundan, bağımlılıklardan hiçbiri yerinde değildir, bu nedenle ilk çalıştırma .NET Core Framework 'ü indirir, bir geliştirme sertifikası yükler ve eksik bağımlılıkları geri yüklemek için NuGet Paket Yöneticisi 'ni çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-133">As this is a new project, none of the dependencies are in place, so the first run will download the .NET Core framework, install a development certificate and run the NuGet package manager to restore missing dependencies.</span></span>

<span data-ttu-id="1fb2e-134">Değişiklik yapmaya başlamadan önce, uygulamanızı çalıştırmak `dotnet run` için komut isteminde ([bkz. Note](#dotnet-restore-note)) yazın.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-134">Before you start making modifications, type `dotnet run` ([see note](#dotnet-restore-note)) at the command prompt to run your application.</span></span> <span data-ttu-id="1fb2e-135">`dotnet run`ortamınızda bağımlılıklar `dotnet restore` eksik olursa otomatik olarak gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-135">`dotnet run` automatically performs `dotnet restore` if your environment is missing dependencies.</span></span> <span data-ttu-id="1fb2e-136">Uygulamanızın yeniden oluşturulması `dotnet build` gerekiyorsa de çalışır.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-136">It also performs `dotnet build` if your application needs to be rebuilt.</span></span>
<span data-ttu-id="1fb2e-137">İlk kurulumdan sonra, yalnızca projeniz için anlamlı olduğunda veya `dotnet restore` `dotnet build` çalıştırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-137">After your initial setup, you will only need to run `dotnet restore` or `dotnet build` when it makes sense for your project.</span></span>

## <a name="adding-new-dependencies"></a><span data-ttu-id="1fb2e-138">Yeni bağımlılıklar ekleniyor</span><span class="sxs-lookup"><span data-stu-id="1fb2e-138">Adding New Dependencies</span></span>

<span data-ttu-id="1fb2e-139">.NET Core için önemli tasarım amaçlarından biri, .NET yüklemesinin boyutunu en aza indirmektir.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-139">One of the key design goals for .NET Core is to minimize the size of the .NET installation.</span></span> <span data-ttu-id="1fb2e-140">Bir uygulamanın bazı özellikleri için ek kitaplıklar gerekiyorsa, bu bağımlılıkları C# proje (\*. csproj) dosyanıza eklersiniz.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-140">If an application needs additional libraries for some of its features, you add those dependencies into your C# project (\*.csproj) file.</span></span> <span data-ttu-id="1fb2e-141">Örneğimiz için, uygulamanızın JSON yanıtlarını işleyebilmesi için `System.Runtime.Serialization.Json` paketini eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-141">For our example, you'll need to add the `System.Runtime.Serialization.Json` package so your application can process JSON responses.</span></span>

<span data-ttu-id="1fb2e-142">`csproj` Proje dosyanızı açın.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-142">Open your `csproj` project file.</span></span> <span data-ttu-id="1fb2e-143">Dosyanın ilk satırı şöyle görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="1fb2e-143">The first line of the file should appear as:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
```

<span data-ttu-id="1fb2e-144">Bu satırdan hemen sonra aşağıdakini ekleyin:</span><span class="sxs-lookup"><span data-stu-id="1fb2e-144">Add the following immediately after this line:</span></span>

```xml
   <ItemGroup>
      <PackageReference Include="System.Runtime.Serialization.Json" Version="4.3.0" />
   </ItemGroup>
```

<span data-ttu-id="1fb2e-145">Çoğu kod Düzenleyicisi, bu kitaplıkların farklı sürümleri için tamamlama sağlar.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-145">Most code editors will provide completion for different versions of these libraries.</span></span> <span data-ttu-id="1fb2e-146">Genellikle eklediğiniz herhangi bir paketin en son sürümünü kullanmak isteyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-146">You'll usually want to use the latest version of any package that you add.</span></span> <span data-ttu-id="1fb2e-147">Ancak, tüm paketlerin sürümlerinin eşleştiğinden ve ayrıca .NET Core uygulama çerçevesinin sürümüyle eşleştiğinden emin olmak önemlidir.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-147">However, it is important to make sure that the versions of all packages match, and that they also match the version of the .NET Core Application framework.</span></span>

<span data-ttu-id="1fb2e-148">Bu değişiklikleri yaptıktan sonra, paketin sisteminizde yüklü `dotnet restore` olması için yürütün ([bkz. Note](#dotnet-restore-note)).</span><span class="sxs-lookup"><span data-stu-id="1fb2e-148">After you've made these changes, execute `dotnet restore` ([see note](#dotnet-restore-note)) so that the package is installed on your system.</span></span>

## <a name="making-web-requests"></a><span data-ttu-id="1fb2e-149">Web Istekleri yapma</span><span class="sxs-lookup"><span data-stu-id="1fb2e-149">Making Web Requests</span></span>

<span data-ttu-id="1fb2e-150">Artık Web 'den veri almaya başlamaya hazırsınız.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-150">Now you're ready to start retrieving data from the web.</span></span> <span data-ttu-id="1fb2e-151">Bu uygulamada, [GITHUB API](https://developer.github.com/v3/)'sindeki bilgileri okuyacaksınız.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-151">In this application, you'll read information from the [GitHub API](https://developer.github.com/v3/).</span></span> <span data-ttu-id="1fb2e-152">[.Net Foundation](https://www.dotnetfoundation.org/) şemsiye kapsamındaki projelerle ilgili bilgileri okuyalim.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-152">Let's read information about the projects under the [.NET Foundation](https://www.dotnetfoundation.org/) umbrella.</span></span> <span data-ttu-id="1fb2e-153">Projeler hakkındaki bilgileri almak için GitHub API 'sine istek yaparak başlayacaksınız.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-153">You'll start by making the request to the GitHub API to retrieve information on the projects.</span></span> <span data-ttu-id="1fb2e-154">Kullanacağınız uç nokta: <https://api.github.com/orgs/dotnet/repos>.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-154">The endpoint you'll use is: <https://api.github.com/orgs/dotnet/repos>.</span></span> <span data-ttu-id="1fb2e-155">Bu projelerle ilgili tüm bilgileri almak istiyorsunuz, bu nedenle bir HTTP GET isteği kullanacaksınız.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-155">You want to retrieve all the information about these projects, so you'll use an HTTP GET request.</span></span>
<span data-ttu-id="1fb2e-156">Tarayıcınız ayrıca HTTP GET isteklerini kullanır; bu nedenle, hangi bilgileri almak ve işlemek istediğinizi görmek için bu URL 'YI tarayıcınıza yapıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-156">Your browser also uses HTTP GET requests, so you can paste that URL into your browser to see what information you'll be receiving and processing.</span></span>

<span data-ttu-id="1fb2e-157">Web istekleri yapmak <xref:System.Net.Http.HttpClient> için sınıfını kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-157">You use the <xref:System.Net.Http.HttpClient> class to make web requests.</span></span> <span data-ttu-id="1fb2e-158">Tüm modern .NET API 'lerinde olduğu <xref:System.Net.Http.HttpClient> gibi, uzun süre çalışan API 'ler için yalnızca zaman uyumsuz yöntemleri destekler.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-158">Like all modern .NET APIs, <xref:System.Net.Http.HttpClient> supports only async methods for its long-running APIs.</span></span>
<span data-ttu-id="1fb2e-159">Zaman uyumsuz bir yöntem yaparak başlayın.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-159">Start by making an async method.</span></span> <span data-ttu-id="1fb2e-160">Uygulamanın işlevlerini oluştururken uygulamayı doldurursunuz.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-160">You'll fill in the implementation as you build the functionality of the application.</span></span> <span data-ttu-id="1fb2e-161">`program.cs` Dosyayı proje dizininizde açıp `Program` sınıfına aşağıdaki yöntemi ekleyerek başlayın:</span><span class="sxs-lookup"><span data-stu-id="1fb2e-161">Start by opening the `program.cs` file in your project directory and adding the following method to the `Program` class:</span></span>

```csharp
private static async Task ProcessRepositories()
{
}
```

<span data-ttu-id="1fb2e-162">Derleyicinin türü tanıması `using` `Main` için yönteminizin en üstüne bir ifade eklemeniz gerekir: <xref:System.Threading.Tasks.Task> C#</span><span class="sxs-lookup"><span data-stu-id="1fb2e-162">You'll need to add a `using` statement at the top of your `Main` method so that the C# compiler recognizes the <xref:System.Threading.Tasks.Task> type:</span></span>

```csharp
using System.Threading.Tasks;
```

<span data-ttu-id="1fb2e-163">Bu noktada projenizi oluşturursanız, herhangi `await` bir işleç içermediğinden ve zaman uyumlu olarak çalışacağı için bu yöntem için bir uyarı alırsınız.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-163">If you build your project at this point, you'll get a warning generated for this method, because it does not contain any `await` operators and will run synchronously.</span></span> <span data-ttu-id="1fb2e-164">Şimdilik bunu yoksayın; yöntemi doldurduktan sonra `await` işleçleri ekleyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-164">Ignore that for now; you'll add `await` operators as you fill in the method.</span></span>

<span data-ttu-id="1fb2e-165">Sonra, `namespace` bildiriminde tanımlanan ad alanını öğesinin varsayılan değerini `ConsoleApp` olarak `WebAPIClient`yeniden adlandırın.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-165">Next, rename the namespace defined in the `namespace` statement from its default of `ConsoleApp` to `WebAPIClient`.</span></span> <span data-ttu-id="1fb2e-166">Daha sonra bu ad alanında `repo` bir sınıf tanımlayacağız.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-166">We'll later define a `repo` class in this namespace.</span></span>

<span data-ttu-id="1fb2e-167">Sonra, `Main` yöntemi bu yöntemi çağırmak için güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-167">Next, update the `Main` method to call this method.</span></span> <span data-ttu-id="1fb2e-168">`ProcessRepositories` Yöntemi bir görevi döndürür ve bu görev tamamlanmadan önce programdan çıkmamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-168">The `ProcessRepositories` method returns a Task, and you shouldn't exit the program before that task finishes.</span></span> <span data-ttu-id="1fb2e-169">Bu nedenle, görevi engellemek ve `Wait` görevin bitmesini beklemek için yöntemini kullanmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="1fb2e-169">Therefore, you must use the `Wait` method to block and wait for the task to finish:</span></span>

```csharp
static void Main(string[] args)
{
    ProcessRepositories().Wait();
}
```

<span data-ttu-id="1fb2e-170">Artık hiçbir şey yapmaz ancak zaman uyumsuz olarak bunu yapar.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-170">Now, you have a program that does nothing, but does it asynchronously.</span></span> <span data-ttu-id="1fb2e-171">Bunu geliştirelim.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-171">Let's improve it.</span></span>

<span data-ttu-id="1fb2e-172">Önce, Web 'den veri alan bir nesne gerekir; Bunu yapmak <xref:System.Net.Http.HttpClient> için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-172">First you need an object that is capable to retrieve data from the web; you can use a <xref:System.Net.Http.HttpClient> to do that.</span></span> <span data-ttu-id="1fb2e-173">Bu nesne, isteği ve yanıtları işler.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-173">This object handles the request and the responses.</span></span> <span data-ttu-id="1fb2e-174">Program.cs dosyasının içindeki `Program` sınıfta bu türün tek bir örneğini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-174">Instantiate a single instance of that type in the `Program` class inside the Program.cs file.</span></span>

```csharp
namespace WebAPIClient
{
    class Program
    {
        private static readonly HttpClient client = new HttpClient();

        static void Main(string[] args)
        {
            //...
        }
    }
}
```

<span data-ttu-id="1fb2e-175">`ProcessRepositories` Yönteme dönüp ilk bir sürümünü dolduralım:</span><span class="sxs-lookup"><span data-stu-id="1fb2e-175">Let's go back to the `ProcessRepositories` method and fill in a first version of it:</span></span>

```csharp
private static async Task ProcessRepositories()
{
    client.DefaultRequestHeaders.Accept.Clear();
    client.DefaultRequestHeaders.Accept.Add(
        new MediaTypeWithQualityHeaderValue("application/vnd.github.v3+json"));
    client.DefaultRequestHeaders.Add("User-Agent", ".NET Foundation Repository Reporter");

    var stringTask = client.GetStringAsync("https://api.github.com/orgs/dotnet/repos");

    var msg = await stringTask;
    Console.Write(msg);
}
```

<span data-ttu-id="1fb2e-176">Bunun derlenmesi için dosyanın en üstüne iki yeni using deyimi de eklemeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="1fb2e-176">You'll need to also add two new using statements at the top of the file for this to compile:</span></span>

```csharp
using System.Net.Http;
using System.Net.Http.Headers;
```

<span data-ttu-id="1fb2e-177">Bu ilk sürüm, DotNet Foundation kuruluşundaki tüm depoların listesini okumak için bir Web isteği oluşturur.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-177">This first version makes a web request to read the list of all repositories under the dotnet foundation organization.</span></span> <span data-ttu-id="1fb2e-178">(.NET Foundation için gitHub KIMLIĞI ' DotNet ').</span><span class="sxs-lookup"><span data-stu-id="1fb2e-178">(The gitHub ID for the .NET Foundation is 'dotnet').</span></span> <span data-ttu-id="1fb2e-179">İlk birkaç satır bu istek <xref:System.Net.Http.HttpClient> için ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-179">The first few lines set up the <xref:System.Net.Http.HttpClient> for this request.</span></span> <span data-ttu-id="1fb2e-180">İlk olarak, GitHub JSON yanıtlarını kabul edecek şekilde yapılandırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-180">First, it is configured to accept the GitHub JSON responses.</span></span>
<span data-ttu-id="1fb2e-181">Bu biçim yalnızca JSON 'dir.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-181">This format is simply JSON.</span></span> <span data-ttu-id="1fb2e-182">Sonraki satır, bu nesneden gelen tüm isteklere bir Kullanıcı Aracısı üst bilgisi ekler.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-182">The next line adds a User Agent header to all requests from this object.</span></span> <span data-ttu-id="1fb2e-183">Bu iki üst bilgi GitHub sunucusu kodu tarafından denetlenir ve GitHub 'dan bilgi almak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-183">These two headers are checked by the GitHub server code, and are necessary to retrieve information from GitHub.</span></span>

<span data-ttu-id="1fb2e-184">Yapılandırmasını <xref:System.Net.Http.HttpClient>yaptıktan sonra bir Web isteği yapar ve yanıtı alırsınız.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-184">After you've configured the <xref:System.Net.Http.HttpClient>, you make a web request and retrieve the response.</span></span> <span data-ttu-id="1fb2e-185">Bu ilk sürümde, <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)?displayProperty=nameWithType> kolaylık yöntemini kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-185">In this first version, you use the <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)?displayProperty=nameWithType> convenience method.</span></span> <span data-ttu-id="1fb2e-186">Bu kolaylık yöntemi, web isteğini yapan bir görevi başlatır ve ardından istek döndürüldüğünde yanıt akışını okur ve içeriği akıştan ayıklar.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-186">This convenience method starts a task that makes the web request, and then when the request returns, it reads the response stream and extracts the content from the stream.</span></span> <span data-ttu-id="1fb2e-187">Yanıtın gövdesi bir <xref:System.String>olarak döndürülür.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-187">The body of the response is returned as a <xref:System.String>.</span></span> <span data-ttu-id="1fb2e-188">Dize, görev tamamlandığında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-188">The string is available when the task completes.</span></span>

<span data-ttu-id="1fb2e-189">Bu yöntemin son iki satırı bu görevi bekler ve ardından yanıtı konsola yazdırır.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-189">The final two lines of this method await that task, and then print the response to the console.</span></span>
<span data-ttu-id="1fb2e-190">Uygulamayı derleyin ve çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-190">Build the app, and run it.</span></span> <span data-ttu-id="1fb2e-191">`ProcessRepositories` Şimdi bir`await` işleç içerdiğinden, derleme uyarısı şimdi çıktı.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-191">The build warning is gone now, because the `ProcessRepositories` now does contain an `await` operator.</span></span> <span data-ttu-id="1fb2e-192">JSON biçimli metnin uzun bir görüntüsünü görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-192">You'll see a long display of JSON formatted text.</span></span>

## <a name="processing-the-json-result"></a><span data-ttu-id="1fb2e-193">JSON sonucunu işleme</span><span class="sxs-lookup"><span data-stu-id="1fb2e-193">Processing the JSON Result</span></span>

<span data-ttu-id="1fb2e-194">Bu noktada, bir Web sunucusundan yanıt almak için kodu yazmış ve bu yanıtta bulunan metni görüntüdiniz.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-194">At this point, you've written the code to retrieve a response from a web server, and display the text that is contained in that response.</span></span> <span data-ttu-id="1fb2e-195">Sonra, bu JSON yanıtını C# nesnelere dönüştürelim.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-195">Next, let's convert that JSON response into C# objects.</span></span>

<span data-ttu-id="1fb2e-196">JSON seri hale getirici JSON verilerini C# nesnelerine dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-196">The JSON Serializer converts JSON data into C# Objects.</span></span> <span data-ttu-id="1fb2e-197">İlk göreviniz, bu yanıttan kullandığınız bilgileri C# içeren bir sınıf türü tanımlamaktır.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-197">Your first task is to define a C# class type to contain the information you use from this response.</span></span> <span data-ttu-id="1fb2e-198">Bunu yavaş oluşturalım, bu nedenle deponun adını içeren basit C# bir türle başlayın:</span><span class="sxs-lookup"><span data-stu-id="1fb2e-198">Let's build this slowly, so start with a simple C# type that contains the name of the repository:</span></span>

```csharp
using System;

namespace WebAPIClient
{
    public class repo
    {
        public string name;
    }
}
```

<span data-ttu-id="1fb2e-199">Yukarıdaki kodu ' repo. cs ' adlı yeni bir dosyaya yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-199">Put the above code in a new file called 'repo.cs'.</span></span> <span data-ttu-id="1fb2e-200">Sınıfının bu sürümü JSON verilerini işlemek için en basit yolu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-200">This version of the class represents the simplest path to process JSON data.</span></span> <span data-ttu-id="1fb2e-201">Sınıf adı ve üye adı, aşağıdaki C# kurallar yerine JSON paketinde kullanılan adlarla eşleşir.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-201">The class name and the member name match the names used in the JSON packet, instead of following C# conventions.</span></span> <span data-ttu-id="1fb2e-202">Daha sonra bazı yapılandırma öznitelikleri sağlayarak bunu düzeltireceksiniz.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-202">You'll fix that by providing some configuration attributes later.</span></span> <span data-ttu-id="1fb2e-203">Bu sınıf, JSON serileştirme ve seri durumundan çıkarma için başka bir önemli özelliği gösterir: JSON paketindeki tüm alanlar bu sınıfın bir parçası değil.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-203">This class demonstrates another important feature of JSON serialization and deserialization: Not all the fields in the JSON packet are part of this class.</span></span>
<span data-ttu-id="1fb2e-204">JSON seri hale getiricisi, kullanılmakta olan sınıf türünde bulunmayan bilgileri yoksayacaktır.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-204">The JSON serializer will ignore information that is not included in the class type being used.</span></span>
<span data-ttu-id="1fb2e-205">Bu özellik, JSON paketindeki alanların yalnızca bir alt kümesiyle çalışan türler oluşturmayı kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-205">This feature makes it easier to create types that work with only a subset of the fields in the JSON packet.</span></span>

<span data-ttu-id="1fb2e-206">Türü oluşturduğunuza göre, artık bunu serisini çıkaralım.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-206">Now that you've created the type, let's deserialize it.</span></span> <span data-ttu-id="1fb2e-207">Bir <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> nesnesi oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-207">You'll need to create a <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> object.</span></span> <span data-ttu-id="1fb2e-208">Bu nesne, aldığı JSON paketi için beklenen CLR türünü bilmelidir.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-208">This object must know the CLR type expected for the JSON packet it retrieves.</span></span> <span data-ttu-id="1fb2e-209">GitHub ' dan paket, bir `List<repo>` dizi depo içerir, bu nedenle, doğru türdür.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-209">The packet from GitHub contains a sequence of repositories, so a `List<repo>` is the correct type.</span></span> <span data-ttu-id="1fb2e-210">Aşağıdaki satırı `ProcessRepositories` yöntemine ekleyin:</span><span class="sxs-lookup"><span data-stu-id="1fb2e-210">Add the following line to your `ProcessRepositories` method:</span></span>

```csharp
var serializer = new DataContractJsonSerializer(typeof(List<repo>));
```

<span data-ttu-id="1fb2e-211">İki yeni ad alanı kullanıyorsunuz, bu nedenle bunları da eklemeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="1fb2e-211">You're using two new namespaces, so you'll need to add those as well:</span></span>

```csharp
using System.Collections.Generic;
using System.Runtime.Serialization.Json;
```

<span data-ttu-id="1fb2e-212">Ardından, JSON 'ı C# nesnelere dönüştürmek için seri hale getirici 'yi kullanacaksınız.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-212">Next, you'll use the serializer to convert JSON into C# objects.</span></span> <span data-ttu-id="1fb2e-213">Yöntemdeki`ProcessRepositories` çağrısını <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)> aşağıdaki iki satır ile değiştirin:</span><span class="sxs-lookup"><span data-stu-id="1fb2e-213">Replace the call to <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)> in your `ProcessRepositories` method with the following two lines:</span></span>

```csharp
var streamTask = client.GetStreamAsync("https://api.github.com/orgs/dotnet/repos");
var repositories = serializer.ReadObject(await streamTask) as List<repo>;
```

<span data-ttu-id="1fb2e-214"><xref:System.Net.Http.HttpClient.GetStreamAsync(System.String)> Artık<xref:System.Net.Http.HttpClient.GetStringAsync(System.String)>yerine kullandığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-214">Notice that you're now using <xref:System.Net.Http.HttpClient.GetStreamAsync(System.String)> instead of <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)>.</span></span> <span data-ttu-id="1fb2e-215">Serileştirici, kaynağı olarak bir dize yerine bir akış kullanır.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-215">The serializer uses a stream instead of a string as its source.</span></span> <span data-ttu-id="1fb2e-216">Yukarıdaki ikinci satırda kullanılmakta olan C# dilin birkaç özelliğini açıklayalim.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-216">Let's explain a couple features of the C# language that are being used in the second line above.</span></span> <span data-ttu-id="1fb2e-217">Bağımsız değişkeni <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject(System.IO.Stream)> bir `await` ifadedir.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-217">The argument to <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject(System.IO.Stream)> is an `await` expression.</span></span> <span data-ttu-id="1fb2e-218">Await ifadeleri kodunuzda neredeyse her yerde görünebilir, ancak şu anda yalnızca bir atama bildiriminin parçası olarak gördünüz.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-218">Await expressions can appear almost anywhere in your code, even though up to now, you've only seen them as part of an assignment statement.</span></span>

<span data-ttu-id="1fb2e-219">İkinci olarak, `as` işleç derleme zaman `object` türünden öğesine `List<repo>`dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-219">Secondly, the `as` operator converts from the compile time type of `object` to `List<repo>`.</span></span>
<span data-ttu-id="1fb2e-220">Bildirimi <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject(System.IO.Stream)> , türünde <xref:System.Object?displayProperty=nameWithType>bir nesne döndüren bildirir.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-220">The declaration of <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject(System.IO.Stream)> declares that it returns an object of type <xref:System.Object?displayProperty=nameWithType>.</span></span> <span data-ttu-id="1fb2e-221"><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject(System.IO.Stream)>, oluşturduğunuzda belirttiğiniz türü döndürür (`List<repo>` Bu öğreticide).</span><span class="sxs-lookup"><span data-stu-id="1fb2e-221"><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject(System.IO.Stream)> will return the type you specified when you constructed it (`List<repo>` in this tutorial).</span></span> <span data-ttu-id="1fb2e-222">Dönüştürme başarılı olmazsa, `as` bir özel durum oluşturmak yerine işleci olarak `null`değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-222">If the conversion does not succeed, the `as` operator evaluates to `null`, instead of throwing an exception.</span></span>

<span data-ttu-id="1fb2e-223">Bu bölümde neredeyse işiniz bitti.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-223">You're almost done with this section.</span></span> <span data-ttu-id="1fb2e-224">JSON 'ı C# nesnelere dönüştürdüğüne göre, her deponun adını görüntülim.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-224">Now that you've converted the JSON to C# objects, let's display the name of each repository.</span></span> <span data-ttu-id="1fb2e-225">Okunan satırları değiştirin:</span><span class="sxs-lookup"><span data-stu-id="1fb2e-225">Replace the lines that read:</span></span>

```csharp
var msg = await stringTask;   //**Deleted this
Console.Write(msg);
```

<span data-ttu-id="1fb2e-226">aşağıdakiler ile:</span><span class="sxs-lookup"><span data-stu-id="1fb2e-226">with the following:</span></span>

```csharp
foreach (var repo in repositories)
    Console.WriteLine(repo.name);
```

<span data-ttu-id="1fb2e-227">Uygulamayı derleyin ve çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-227">Compile and run the application.</span></span> <span data-ttu-id="1fb2e-228">.NET Foundation 'ın parçası olan Depoların adlarını yazdıracaktır.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-228">It will print out the names of the repositories that are part of the .NET Foundation.</span></span>

## <a name="controlling-serialization"></a><span data-ttu-id="1fb2e-229">Serileştirme denetleniyor</span><span class="sxs-lookup"><span data-stu-id="1fb2e-229">Controlling Serialization</span></span>

<span data-ttu-id="1fb2e-230">Daha fazla özellik eklemeden önce, `repo` türü ele alalım ve daha standart C# Kurallara uyalım.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-230">Before you add more features, let's address the `repo` type and make it follow more standard C# conventions.</span></span> <span data-ttu-id="1fb2e-231">Bunu, JSON seri hale getiricinin `repo` nasıl çalıştığını denetleyen *özniteliklerle* türe açıklama ekleyerek yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-231">You'll do this by annotating the `repo` type with *attributes* that control how the JSON Serializer works.</span></span> <span data-ttu-id="1fb2e-232">Bu durumda, JSON anahtar adları ve C# sınıf ile üye adları arasında bir eşleme tanımlamak için bu öznitelikleri kullanacaksınız.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-232">In your case, you'll use these attributes to define a mapping between the JSON key names and the C# class and member names.</span></span> <span data-ttu-id="1fb2e-233">Kullanılan iki öznitelik <xref:System.Runtime.Serialization.DataContractAttribute> ve <xref:System.Runtime.Serialization.DataMemberAttribute> öznitelikleridir.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-233">The two attributes used are the <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> attributes.</span></span> <span data-ttu-id="1fb2e-234">Kurala göre, tüm öznitelik sınıfları sonta `Attribute`sona erdir.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-234">By convention, all Attribute classes end in the suffix `Attribute`.</span></span> <span data-ttu-id="1fb2e-235">Ancak, bir özniteliği uyguladığınızda o soneki kullanmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-235">However, you do not need to use that suffix when you apply an attribute.</span></span>

<span data-ttu-id="1fb2e-236">Ve öznitelikleri farklı bir kitaplıkta olduğundan, bu kitaplığı C# proje dosyanıza bağımlılık olarak eklemeniz gerekir. <xref:System.Runtime.Serialization.DataMemberAttribute> <xref:System.Runtime.Serialization.DataContractAttribute></span><span class="sxs-lookup"><span data-stu-id="1fb2e-236">The <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> attributes are in a different library, so you'll need to add that library to your C# project file as a dependency.</span></span> <span data-ttu-id="1fb2e-237">Aşağıdaki satırı `<ItemGroup>` proje dosyanızın bölümüne ekleyin:</span><span class="sxs-lookup"><span data-stu-id="1fb2e-237">Add the following line to the `<ItemGroup>` section of your project file:</span></span>

```xml
<PackageReference Include="System.Runtime.Serialization.Primitives" Version="4.3.0" />
```

<span data-ttu-id="1fb2e-238">Dosyayı kaydettikten sonra, bu paketi almak `dotnet restore` için ([bkz. Note](#dotnet-restore-note)) öğesini çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-238">After you save the file, run `dotnet restore` ([see note](#dotnet-restore-note)) to retrieve this package.</span></span>

<span data-ttu-id="1fb2e-239">Sonra `repo.cs` dosyayı açın.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-239">Next, open the `repo.cs` file.</span></span> <span data-ttu-id="1fb2e-240">Bu adı, Pascal durumunu kullanacak şekilde değiştirelim ve adı `Repository`tamamen heceleyin.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-240">Let's change the name to use Pascal Case, and fully spell out the name `Repository`.</span></span> <span data-ttu-id="1fb2e-241">Hala bu tür JSON ' repo ' düğümlerini eşlemek istiyoruz, bu nedenle <xref:System.Runtime.Serialization.DataContractAttribute> özniteliği sınıf bildirimine eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-241">We still want to map JSON 'repo' nodes to this type, so you'll need to add the <xref:System.Runtime.Serialization.DataContractAttribute> attribute to the class declaration.</span></span> <span data-ttu-id="1fb2e-242">Özniteliğin `Name` özelliğini, bu türle eşlenen json düğümlerinin adına ayarlayacaksınız:</span><span class="sxs-lookup"><span data-stu-id="1fb2e-242">You'll set the `Name` property of the attribute to the name of the JSON nodes that map to this type:</span></span>

```csharp
[DataContract(Name="repo")]
public class Repository
```

<span data-ttu-id="1fb2e-243">, Ad alanının bir üyesidir `using` , bu yüzden dosyanın en üstüne uygun ifadeyi eklemeniz gerekir: <xref:System.Runtime.Serialization> <xref:System.Runtime.Serialization.DataContractAttribute></span><span class="sxs-lookup"><span data-stu-id="1fb2e-243">The <xref:System.Runtime.Serialization.DataContractAttribute> is a member of the <xref:System.Runtime.Serialization> namespace, so you'll need to add the appropriate `using` statement at the top of the file:</span></span>

```csharp
using System.Runtime.Serialization;
```

<span data-ttu-id="1fb2e-244">`repo` Sınıfının adını olarak `Repository`değiştirdiniz. bu nedenle, program.cs içinde aynı ad değişikliğini yapmanız gerekir (bazı düzenleyiciler, bu değişikliği otomatik olarak yapan bir yeniden adlandırma yeniden düzenlemesi destekleyebilir:)</span><span class="sxs-lookup"><span data-stu-id="1fb2e-244">You changed the name of the `repo` class to `Repository`, so you'll need to make the same name change in Program.cs (some editors may support a rename refactoring that will make this change automatically:)</span></span>

```csharp
var serializer = new DataContractJsonSerializer(typeof(List<Repository>));

// ...

var repositories = serializer.ReadObject(await streamTask) as List<Repository>;
```

<span data-ttu-id="1fb2e-245">Daha sonra, `name` <xref:System.Runtime.Serialization.DataMemberAttribute> sınıfını kullanarak aynı değişikliği alanla yapalim.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-245">Next, let's make the same change with the `name` field by using the <xref:System.Runtime.Serialization.DataMemberAttribute> class.</span></span> <span data-ttu-id="1fb2e-246">Repo.cs içindeki `name` alanın bildiriminde aşağıdaki değişiklikleri yapın:</span><span class="sxs-lookup"><span data-stu-id="1fb2e-246">Make the following changes to the declaration of the `name` field in repo.cs:</span></span>

```csharp
[DataMember(Name="name")]
public string Name;
```

<span data-ttu-id="1fb2e-247">Bu değişiklik, program.cs içindeki her deponun adını yazan kodu değiştirmeniz gereken anlamına gelir:</span><span class="sxs-lookup"><span data-stu-id="1fb2e-247">This change means you need to change the code that writes the name of each repository in program.cs:</span></span>

```csharp
Console.WriteLine(repo.Name);
```

<span data-ttu-id="1fb2e-248">Eşlemelerinizin doğru olduğundan emin `dotnet run` olmak için bir takipedin.`dotnet build`</span><span class="sxs-lookup"><span data-stu-id="1fb2e-248">Do a `dotnet build` followed by a `dotnet run` to make sure you've got the mappings correct.</span></span> <span data-ttu-id="1fb2e-249">Önceki ile aynı çıktıyı görmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-249">You should see the same output as before.</span></span> <span data-ttu-id="1fb2e-250">Web sunucusundan daha fazla özellik işleyebilmemiz için `Repository` , sınıfa daha fazla değişiklik yapalım.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-250">Before we process more properties from the web server, let's make one more change to the `Repository` class.</span></span> <span data-ttu-id="1fb2e-251">`Name` Üye, herkese açık bir alandır.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-251">The `Name` member is a publicly accessible field.</span></span> <span data-ttu-id="1fb2e-252">Bu iyi bir nesne odaklı uygulama değildir, bu nedenle bunu bir özellik olarak değiştirelim.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-252">That's not a good object-oriented practice, so let's change it to a property.</span></span> <span data-ttu-id="1fb2e-253">Özelliği alırken veya ayarlarken çalıştırmak için belirli bir kod gerekmez, ancak bir özelliği değiştirmek, bu değişiklikleri `Repository` sınıfını kullanan kodları bozmadan daha sonra eklemeyi kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-253">For our purposes, we don't need any specific code to run when getting or setting the property, but changing to a property makes it easier to add those changes later without breaking any code that uses the `Repository` class.</span></span>

<span data-ttu-id="1fb2e-254">Alan tanımını kaldırın ve [Otomatik uygulanan bir özellik](../programming-guide/classes-and-structs/auto-implemented-properties.md)ile değiştirin:</span><span class="sxs-lookup"><span data-stu-id="1fb2e-254">Remove the field definition, and replace it with an [auto-implemented property](../programming-guide/classes-and-structs/auto-implemented-properties.md):</span></span>

```csharp
public string Name { get; set; }
```

<span data-ttu-id="1fb2e-255">Derleyici, `get` ve erişimcilerinin gövdesini ve `set` adı depolamak için özel bir alanı üretir.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-255">The compiler generates the body of the `get` and `set` accessors, as well as a private field to store the name.</span></span> <span data-ttu-id="1fb2e-256">Bu, el ile yazabileceğiniz aşağıdaki koda benzer olacaktır:</span><span class="sxs-lookup"><span data-stu-id="1fb2e-256">It would be similar to the following code that you could type by hand:</span></span>

```csharp
public string Name
{
    get { return this._name; }
    set { this._name = value; }
}
private string _name;
```

<span data-ttu-id="1fb2e-257">Yeni özellikler eklemeden önce bir değişiklik yapalim.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-257">Let's make one more change before adding new features.</span></span> <span data-ttu-id="1fb2e-258">`ProcessRepositories` Yöntemi zaman uyumsuz çalışmayı yapabilir ve depoların bir koleksiyonunu döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-258">The `ProcessRepositories` method can do the async work and return a collection of the repositories.</span></span> <span data-ttu-id="1fb2e-259">Bu yöntemden ' ı `List<Repository>` dönelim ve bilgileri `Main` yöntemine yazan kodu taşıyalim.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-259">Let's return the `List<Repository>` from that method, and move the code that writes the information into the `Main` method.</span></span>

<span data-ttu-id="1fb2e-260">Sonucunu bir `Repository` nesne listesi `ProcessRepositories` olan bir görevi döndürmek için imzasını değiştirin:</span><span class="sxs-lookup"><span data-stu-id="1fb2e-260">Change the signature of `ProcessRepositories` to return a task whose result is a list of `Repository` objects:</span></span>

```csharp
private static async Task<List<Repository>> ProcessRepositories()
```

<span data-ttu-id="1fb2e-261">Ardından, JSON yanıtını işledikten sonra depoları geri döndürün:</span><span class="sxs-lookup"><span data-stu-id="1fb2e-261">Then, just return the repositories after processing the JSON response:</span></span>

```csharp
var repositories = serializer.ReadObject(await streamTask) as List<Repository>;
return repositories;
```

<span data-ttu-id="1fb2e-262">Bu yöntemi olarak `async`işaretlediğiniz `Task<T>` için derleyici, döndürme için nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-262">The compiler generates the `Task<T>` object for the return because you've marked this method as `async`.</span></span>
<span data-ttu-id="1fb2e-263">Ardından, `Main` yöntemi bu sonuçları yakalayıp, her depo adını konsola yazar şekilde değiştirelim.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-263">Then, let's modify the `Main` method so that it captures those results and writes each repository name to the console.</span></span> <span data-ttu-id="1fb2e-264">`Main` Yönteminiz şu şekilde görünür:</span><span class="sxs-lookup"><span data-stu-id="1fb2e-264">Your `Main` method now looks like this:</span></span>

```csharp
public static void Main(string[] args)
{
    var repositories = ProcessRepositories().Result;

    foreach (var repo in repositories)
        Console.WriteLine(repo.Name);
}
```

<span data-ttu-id="1fb2e-265">Görev tamamlanana kadar görev bloklarının özelliğineerişme.`Result`</span><span class="sxs-lookup"><span data-stu-id="1fb2e-265">Accessing the `Result` property of a Task blocks until the task has completed.</span></span> <span data-ttu-id="1fb2e-266">Normalde, `ProcessRepositories` yönteminde olduğu gibi, `await` ancak `Main` yönteminde izin verilmeyen görevi tamamlamayı tercih edersiniz.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-266">Normally, you would prefer to `await` the completion of the task, as in the `ProcessRepositories` method, but that isn't allowed in the `Main` method.</span></span>

## <a name="reading-more-information"></a><span data-ttu-id="1fb2e-267">Daha fazla bilgi okunuyor</span><span class="sxs-lookup"><span data-stu-id="1fb2e-267">Reading More Information</span></span>

<span data-ttu-id="1fb2e-268">Bu işlemi, GitHub API 'sinden gönderilen JSON paketindeki özelliklerden daha fazlasını işleyerek tamamlayalim.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-268">Let's finish this by processing a few more of the properties in the JSON packet that gets sent from the GitHub API.</span></span> <span data-ttu-id="1fb2e-269">Her şeyi almak istemezsiniz, ancak birkaç özelliği eklemek C# dilin birkaç özelliğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-269">You won't want to grab everything, but adding a few properties will demonstrate a few more features of the C# language.</span></span>

<span data-ttu-id="1fb2e-270">Daha fazla basit türü `Repository` sınıf tanımına ekleyerek başlayalım.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-270">Let's start by adding a few more simple types to the `Repository` class definition.</span></span> <span data-ttu-id="1fb2e-271">Bu özellikleri bu sınıfa ekleyin:</span><span class="sxs-lookup"><span data-stu-id="1fb2e-271">Add these properties to that class:</span></span>

```csharp
[DataMember(Name="description")]
public string Description { get; set; }

[DataMember(Name="html_url")]
public Uri GitHubHomeUrl { get; set; }

[DataMember(Name="homepage")]
public Uri Homepage { get; set; }

[DataMember(Name="watchers")]
public int Watchers { get; set; }
```

<span data-ttu-id="1fb2e-272">Bu özellikler dize türünden (JSON paketlerinin içerdiği), hedef türüne yerleşik Dönüştürmelere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-272">These properties have built-in conversions from the string type (which is what the JSON packets contain) to the target type.</span></span> <span data-ttu-id="1fb2e-273"><xref:System.Uri> Tür sizin için yeni olabilir.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-273">The <xref:System.Uri> type may be new to you.</span></span> <span data-ttu-id="1fb2e-274">Bir URI 'yi veya bu durumda bir URL 'yi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-274">It represents a URI, or in this case, a URL.</span></span> <span data-ttu-id="1fb2e-275">`Uri` Ve`int` türleri söz konusu olduğunda, JSON paketi hedef türüne Dönüştürülmeyen veriler içeriyorsa, serileştirme eylemi bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-275">In the case of the `Uri` and `int` types, if the JSON packet contains data that does not convert to the target type, the serialization action will throw an exception.</span></span>

<span data-ttu-id="1fb2e-276">Bunları ekledikten sonra, bu öğeleri göstermek için `Main` yöntemini güncelleştirin:</span><span class="sxs-lookup"><span data-stu-id="1fb2e-276">Once you've added these, update the `Main` method to display those elements:</span></span>

```csharp
foreach (var repo in repositories)
{
    Console.WriteLine(repo.Name);
    Console.WriteLine(repo.Description);
    Console.WriteLine(repo.GitHubHomeUrl);
    Console.WriteLine(repo.Homepage);
    Console.WriteLine(repo.Watchers);
    Console.WriteLine();
}
```

<span data-ttu-id="1fb2e-277">Son bir adım olarak, son gönderme işlemi için bilgileri ekleyelim.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-277">As a final step, let's add the information for the last push operation.</span></span> <span data-ttu-id="1fb2e-278">Bu bilgiler, JSON yanıtında bu biçimde biçimlendirilir:</span><span class="sxs-lookup"><span data-stu-id="1fb2e-278">This information is formatted in this fashion in the JSON response:</span></span>

```json
2016-02-08T21:27:00Z
```

<span data-ttu-id="1fb2e-279">Bu biçim standart .net <xref:System.DateTime> biçimlerinden hiçbirini izlemez.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-279">That format does not follow any of the standard .NET <xref:System.DateTime> formats.</span></span> <span data-ttu-id="1fb2e-280">Bu nedenle, özel bir dönüştürme yöntemi yazmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-280">Because of that, you'll need to write a custom conversion method.</span></span> <span data-ttu-id="1fb2e-281">Ham dizenin, `Repository` sınıfın kullanıcılarına gösterilmesini de istemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-281">You also probably don't want the raw string exposed to users of the `Repository` class.</span></span> <span data-ttu-id="1fb2e-282">Öznitelikleri, bu da denetim sağlanmasına yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-282">Attributes can help control that as well.</span></span> <span data-ttu-id="1fb2e-283">İlk olarak, sınıfınıza `private` `Repository` ait tarih saatinin dize gösterimini tutacak bir özellik tanımlayın:</span><span class="sxs-lookup"><span data-stu-id="1fb2e-283">First, define a `private` property that will hold the string representation of the date time in your `Repository` class:</span></span>

```csharp
[DataMember(Name="pushed_at")]
private string JsonDate { get; set; }
```

<span data-ttu-id="1fb2e-284"><xref:System.Runtime.Serialization.DataMemberAttribute> Özniteliği, seri hale getiricinin, ortak üye olmasa bile bu işleme yönelik olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-284">The <xref:System.Runtime.Serialization.DataMemberAttribute> attribute informs the serializer that this should be processed, even though it is not a public member.</span></span> <span data-ttu-id="1fb2e-285">Sonra, dizeyi geçerli <xref:System.DateTime> bir nesneye dönüştüren ortak bir salt okunurdur ve bu <xref:System.DateTime>özelliği yazmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="1fb2e-285">Next, you need to write a public read-only property that converts the string to a valid <xref:System.DateTime> object, and returns that <xref:System.DateTime>:</span></span>

```csharp
[IgnoreDataMember]
public DateTime LastPush
{
    get
    {
        return DateTime.ParseExact(JsonDate, "yyyy-MM-ddTHH:mm:ssZ", CultureInfo.InvariantCulture);
    }
}
```

<span data-ttu-id="1fb2e-286">Yukarıdaki yeni yapıları inceleyelim.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-286">Let's go over the new constructs above.</span></span> <span data-ttu-id="1fb2e-287">`IgnoreDataMember` Özniteliği, seri hale getirici bu türün herhangi bir JSON nesnesine okunmamalıdır veya yazılamaz olması gerektiğini söyler.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-287">The `IgnoreDataMember` attribute instructs the serializer that this type should not be read to or written from any JSON object.</span></span> <span data-ttu-id="1fb2e-288">Bu özellik yalnızca bir `get` erişimci içerir.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-288">This property contains only a `get` accessor.</span></span> <span data-ttu-id="1fb2e-289">`set` Erişimci yok.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-289">There is no `set` accessor.</span></span> <span data-ttu-id="1fb2e-290">İçinde C# *salt okunurdur* bir özelliği nasıl tanımlayacaksınız.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-290">That's how you define a *read-only* property in C#.</span></span> <span data-ttu-id="1fb2e-291">(Evet, öğesinde C# *salt yazılır* özellikler oluşturabilirsiniz, ancak değerleri sınırlıdır.) Yöntemi bir dizeyi ayrıştırır ve bir <xref:System.DateTime> nesne `DateTime` kullanarak `CultureInfo` bir nesne oluşturur. <xref:System.DateTime.ParseExact(System.String,System.String,System.IFormatProvider)></span><span class="sxs-lookup"><span data-stu-id="1fb2e-291">(Yes, you can create *write-only* properties in C#, but their value is limited.) The <xref:System.DateTime.ParseExact(System.String,System.String,System.IFormatProvider)> method parses a string and creates a <xref:System.DateTime> object using a provided date format, and adds additional metadata to the `DateTime` using a `CultureInfo` object.</span></span> <span data-ttu-id="1fb2e-292">Ayrıştırma işlemi başarısız olursa, özellik erişimcisi bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-292">If the parse operation fails, the property accessor throws an exception.</span></span>

<span data-ttu-id="1fb2e-293">Kullanmak <xref:System.Globalization.CultureInfo.InvariantCulture>için, <xref:System.Globalization> ad alanını `using` içindeki `repo.cs`deyimlere eklemeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="1fb2e-293">To use <xref:System.Globalization.CultureInfo.InvariantCulture>, you will need to add the <xref:System.Globalization> namespace to the `using` statements in `repo.cs`:</span></span>

```csharp
using System.Globalization;
```

<span data-ttu-id="1fb2e-294">Son olarak, konsolda bir çıkış bildirisi daha ekleyin ve bu uygulamayı yeniden oluşturup çalıştırmak için hazırsınız:</span><span class="sxs-lookup"><span data-stu-id="1fb2e-294">Finally, add one more output statement in the console, and you're ready to build and run this app again:</span></span>

```csharp
Console.WriteLine(repo.LastPush);
```

<span data-ttu-id="1fb2e-295">Sürümünüz artık [tamamlanmış örnekle](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient)eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-295">Your version should now match the [finished sample](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient).</span></span>

## <a name="conclusion"></a><span data-ttu-id="1fb2e-296">Sonuç</span><span class="sxs-lookup"><span data-stu-id="1fb2e-296">Conclusion</span></span>

<span data-ttu-id="1fb2e-297">Bu öğretici, Web istekleri oluşturma, sonucu ayrıştırma ve bu sonuçların özelliklerini görüntüleme konusunda sizi gösterdi.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-297">This tutorial showed you how to make web requests, parse the result, and display properties of those results.</span></span> <span data-ttu-id="1fb2e-298">Ayrıca, yeni paketleri projenize bağımlılıklar olarak eklediniz.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-298">You've also added new packages as dependencies in your project.</span></span> <span data-ttu-id="1fb2e-299">Nesne odaklı teknikleri destekleyen C# dilin bazı özelliklerini gördünüz.</span><span class="sxs-lookup"><span data-stu-id="1fb2e-299">You've seen some of the features of the C# language that support object-oriented techniques.</span></span>

<a name="dotnet-restore-note"></a>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
