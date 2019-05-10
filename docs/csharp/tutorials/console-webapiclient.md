---
title: .NET Core kullanarak bir REST istemcisi oluşturma
description: Bu öğretici, .NET Core ve C# dili özellikleri sayısı öğretir.
ms.date: 03/06/2017
ms.assetid: 51033ce2-7a53-4cdd-966d-9da15c8204d2
ms.openlocfilehash: f6e3371a72810b30f804169be4025360aa10c477
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/06/2019
ms.locfileid: "65063878"
---
# <a name="rest-client"></a><span data-ttu-id="b96a5-103">REST istemcisi</span><span class="sxs-lookup"><span data-stu-id="b96a5-103">REST client</span></span>

## <a name="introduction"></a><span data-ttu-id="b96a5-104">Giriş</span><span class="sxs-lookup"><span data-stu-id="b96a5-104">Introduction</span></span>

<span data-ttu-id="b96a5-105">Bu öğretici, .NET Core ve C# dili özellikleri sayısı öğretir.</span><span class="sxs-lookup"><span data-stu-id="b96a5-105">This tutorial teaches you a number of features in .NET Core and the C# language.</span></span> <span data-ttu-id="b96a5-106">Şunları öğreneceksiniz:</span><span class="sxs-lookup"><span data-stu-id="b96a5-106">You’ll learn:</span></span>

* <span data-ttu-id="b96a5-107">Temel .NET Core komut satırı arabirimi (CLI).</span><span class="sxs-lookup"><span data-stu-id="b96a5-107">The basics of the .NET Core Command Line Interface (CLI).</span></span>
* <span data-ttu-id="b96a5-108">C# dili özellikleri genel bakış.</span><span class="sxs-lookup"><span data-stu-id="b96a5-108">An overview of C# Language features.</span></span>
* <span data-ttu-id="b96a5-109">NuGet ile bağımlılık Yönetimi</span><span class="sxs-lookup"><span data-stu-id="b96a5-109">Managing dependencies with NuGet</span></span>
* <span data-ttu-id="b96a5-110">HTTP iletişimleri</span><span class="sxs-lookup"><span data-stu-id="b96a5-110">HTTP Communications</span></span>
* <span data-ttu-id="b96a5-111">JSON bilgilerini işleme</span><span class="sxs-lookup"><span data-stu-id="b96a5-111">Processing JSON information</span></span>
* <span data-ttu-id="b96a5-112">Öznitelikleri yapılandırmasıyla yönetme.</span><span class="sxs-lookup"><span data-stu-id="b96a5-112">Managing configuration with Attributes.</span></span>

<span data-ttu-id="b96a5-113">GitHub üzerinde bir REST hizmeti için HTTP isteklerini veren bir uygulama oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="b96a5-113">You’ll build an application that issues HTTP Requests to a REST service on GitHub.</span></span> <span data-ttu-id="b96a5-114">JSON biçiminde bilgileri okuyun ve C# nesneler bu JSON paket dönüştürme.</span><span class="sxs-lookup"><span data-stu-id="b96a5-114">You'll read information in JSON format, and convert that JSON packet into C# objects.</span></span> <span data-ttu-id="b96a5-115">Son olarak, C# nesneleriyle çalışma konusunda görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="b96a5-115">Finally, you'll see how to work with C# objects.</span></span>

<span data-ttu-id="b96a5-116">Bu öğreticide birçok özellik vardır.</span><span class="sxs-lookup"><span data-stu-id="b96a5-116">There are a lot of features in this tutorial.</span></span> <span data-ttu-id="b96a5-117">Bunları tek tek oluşturalım.</span><span class="sxs-lookup"><span data-stu-id="b96a5-117">Let’s build them one by one.</span></span>

<span data-ttu-id="b96a5-118">İle birlikte izlemek isterseniz [son örnek](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient) yönelik bu konuda, indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b96a5-118">If you prefer to follow along with the [final sample](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient) for this topic, you can download it.</span></span> <span data-ttu-id="b96a5-119">Yükleme yönergeleri için bkz: [örnekler ve öğreticiler](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="b96a5-119">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="b96a5-120">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="b96a5-120">Prerequisites</span></span>

<span data-ttu-id="b96a5-121">.NET core çalıştırmak için makinenizi ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="b96a5-121">You’ll need to set up your machine to run .NET core.</span></span> <span data-ttu-id="b96a5-122">Yükleme yönergelerini bulabilirsiniz [.NET Core](https://www.microsoft.com/net/core) sayfası.</span><span class="sxs-lookup"><span data-stu-id="b96a5-122">You can find the installation instructions on the [.NET Core](https://www.microsoft.com/net/core) page.</span></span> <span data-ttu-id="b96a5-123">Bu uygulama, Windows, Linux, macOS veya Docker kapsayıcısı çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b96a5-123">You can run this application on Windows, Linux, macOS or in a Docker container.</span></span>
<span data-ttu-id="b96a5-124">Sık kullandığınız Kod Düzenleyicisi'ni yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="b96a5-124">You’ll need to install your favorite code editor.</span></span> <span data-ttu-id="b96a5-125">Aşağıdaki tanımlamalar [Visual Studio Code](https://code.visualstudio.com/), açık kaynaklı, çapraz platform Düzenleyicisi olduğu.</span><span class="sxs-lookup"><span data-stu-id="b96a5-125">The descriptions below use [Visual Studio Code](https://code.visualstudio.com/), which is an open source, cross platform editor.</span></span> <span data-ttu-id="b96a5-126">Ancak, rahat sevdiğiniz araçları kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b96a5-126">However, you can use whatever tools you are comfortable with.</span></span>

## <a name="create-the-application"></a><span data-ttu-id="b96a5-127">Uygulama oluşturma</span><span class="sxs-lookup"><span data-stu-id="b96a5-127">Create the Application</span></span>

<span data-ttu-id="b96a5-128">İlk adım, yeni bir uygulama oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="b96a5-128">The first step is to create a new application.</span></span> <span data-ttu-id="b96a5-129">Bir komut istemi açın ve uygulamanız için yeni bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="b96a5-129">Open a command prompt and create a new directory for your application.</span></span> <span data-ttu-id="b96a5-130">Bu, geçerli bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="b96a5-130">Make that the current directory.</span></span> <span data-ttu-id="b96a5-131">Komut türü `dotnet new console` komut isteminde.</span><span class="sxs-lookup"><span data-stu-id="b96a5-131">Type the command `dotnet new console` at the command prompt.</span></span> <span data-ttu-id="b96a5-132">Bu, temel bir "Hello World" uygulaması için başlangıç dosyaları oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b96a5-132">This creates the starter files for a basic "Hello World" application.</span></span> <span data-ttu-id="b96a5-133">Bu yeni bir proje olduğundan, ilk çalıştırma .NET Core Framework'ün indirin, geliştirme sertifikası yüklenir ve eksik bağımlılıklar geri yüklemek için NuGet paket yöneticisini çalıştırın böylece bağımlılıkları hiçbiri yerde değil.</span><span class="sxs-lookup"><span data-stu-id="b96a5-133">As this is a new project, none of the dependencies are in place, so the first run will download the .NET Core framework, install a development certificate and run the NuGet package manager to restore missing dependencies.</span></span>

<span data-ttu-id="b96a5-134">Bir değişiklik yapmadan başlamadan önce yazın `dotnet run` ([bkz. Not](#dotnet-restore-note)) uygulamanızı çalıştırmak için komut isteminde.</span><span class="sxs-lookup"><span data-stu-id="b96a5-134">Before you start making modifications, type `dotnet run` ([see note](#dotnet-restore-note)) at the command prompt to run your application.</span></span> <span data-ttu-id="b96a5-135">`dotnet run` otomatik olarak gerçekleştirir `dotnet restore` ortamınızı bağımlılıkları eksikse.</span><span class="sxs-lookup"><span data-stu-id="b96a5-135">`dotnet run` automatically performs `dotnet restore` if your environment is missing dependencies.</span></span> <span data-ttu-id="b96a5-136">Ayrıca gerçekleştirir `dotnet build` uygulamanız yeniden oluşturulması gerekiyorsa.</span><span class="sxs-lookup"><span data-stu-id="b96a5-136">It also performs `dotnet build` if your application needs to be rebuilt.</span></span>
<span data-ttu-id="b96a5-137">İlk Kurulumdan sonra yalnızca çalıştırmanız gerekir `dotnet restore` veya `dotnet build` projeniz için anlamlı olduğunda kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="b96a5-137">After your initial setup, you will only need to run `dotnet restore` or `dotnet build` when it makes sense for your project.</span></span>

## <a name="adding-new-dependencies"></a><span data-ttu-id="b96a5-138">Yeni bağımlılıkları ekleme</span><span class="sxs-lookup"><span data-stu-id="b96a5-138">Adding New Dependencies</span></span>

<span data-ttu-id="b96a5-139">.NET Core için önemli tasarım amaçlarından .NET yükleme boyutu en aza indirmektir.</span><span class="sxs-lookup"><span data-stu-id="b96a5-139">One of the key design goals for .NET Core is to minimize the size of the .NET installation.</span></span> <span data-ttu-id="b96a5-140">Bir uygulamanın bazı özelliklerin ek kitaplıklar gerekiyorsa bu bağımlılıkların C# projenize ekleyin (\*.csproj) dosyası.</span><span class="sxs-lookup"><span data-stu-id="b96a5-140">If an application needs additional libraries for some of its features, you add those dependencies into your C# project (\*.csproj) file.</span></span> <span data-ttu-id="b96a5-141">Bizim örneğimizde, eklemeniz gerekecektir `System.Runtime.Serialization.Json` uygulamanızın JSON yanıtları işleyebilmek için paket.</span><span class="sxs-lookup"><span data-stu-id="b96a5-141">For our example, you'll need to add the `System.Runtime.Serialization.Json` package so your application can process JSON responses.</span></span>

<span data-ttu-id="b96a5-142">Açık, `csproj` proje dosyası.</span><span class="sxs-lookup"><span data-stu-id="b96a5-142">Open your `csproj` project file.</span></span> <span data-ttu-id="b96a5-143">Dosyanın ilk satırı olarak görünmesi gerekir:</span><span class="sxs-lookup"><span data-stu-id="b96a5-143">The first line of the file should appear as:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
```

<span data-ttu-id="b96a5-144">Bu satırın hemen sonra aşağıdakileri ekleyin:</span><span class="sxs-lookup"><span data-stu-id="b96a5-144">Add the following immediately after this line:</span></span>

```xml
   <ItemGroup>
      <PackageReference Include="System.Runtime.Serialization.Json" Version="4.3.0" />
   </ItemGroup>
```

<span data-ttu-id="b96a5-145">Çoğu kod düzenleyicilerinden, bu kitaplıkların farklı sürümleri için tamamlama sağlayacaktır.</span><span class="sxs-lookup"><span data-stu-id="b96a5-145">Most code editors will provide completion for different versions of these libraries.</span></span> <span data-ttu-id="b96a5-146">Genellikle, eklediğiniz herhangi bir paket en son sürümünü kullanmak isteyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="b96a5-146">You'll usually want to use the latest version of any package that you add.</span></span> <span data-ttu-id="b96a5-147">Ancak, tüm paketlerin sürümlerinin eşleştiğinden ve .NET Core uygulaması framework sürümü de eşleştiğinden emin olmak önemlidir.</span><span class="sxs-lookup"><span data-stu-id="b96a5-147">However, it is important to make sure that the versions of all packages match, and that they also match the version of the .NET Core Application framework.</span></span>

<span data-ttu-id="b96a5-148">Bu değişiklikleri yaptıktan sonra yürütme `dotnet restore` ([bkz. Not](#dotnet-restore-note)) paketi sisteminizde yüklü olduğunu.</span><span class="sxs-lookup"><span data-stu-id="b96a5-148">After you've made these changes, execute `dotnet restore` ([see note](#dotnet-restore-note)) so that the package is installed on your system.</span></span>

## <a name="making-web-requests"></a><span data-ttu-id="b96a5-149">Web istekleri yapma</span><span class="sxs-lookup"><span data-stu-id="b96a5-149">Making Web Requests</span></span>

<span data-ttu-id="b96a5-150">Artık Web'den veri almaya başlamak hazırsınız.</span><span class="sxs-lookup"><span data-stu-id="b96a5-150">Now you're ready to start retrieving data from the web.</span></span> <span data-ttu-id="b96a5-151">Bilgileri okuyun bu uygulamada [GitHub API](https://developer.github.com/v3/).</span><span class="sxs-lookup"><span data-stu-id="b96a5-151">In this application, you'll read information from the [GitHub API](https://developer.github.com/v3/).</span></span> <span data-ttu-id="b96a5-152">Projeleri hakkında bilgi okuyalım [.NET Foundation](https://www.dotnetfoundation.org/) terimdir.</span><span class="sxs-lookup"><span data-stu-id="b96a5-152">Let's read information about the projects under the [.NET Foundation](https://www.dotnetfoundation.org/) umbrella.</span></span> <span data-ttu-id="b96a5-153">Projeler hakkında bilgi almak için GitHub API isteği yapan başlayacağız.</span><span class="sxs-lookup"><span data-stu-id="b96a5-153">You'll start by making the request to the GitHub API to retrieve information on the projects.</span></span> <span data-ttu-id="b96a5-154">Kullandığınız hesap uç noktadır: <https://api.github.com/orgs/dotnet/repos>.</span><span class="sxs-lookup"><span data-stu-id="b96a5-154">The endpoint you'll use is: <https://api.github.com/orgs/dotnet/repos>.</span></span> <span data-ttu-id="b96a5-155">Bir HTTP GET isteği kullanacaksınız böylece bu projeleri hakkındaki tüm bilgileri almak istediğiniz.</span><span class="sxs-lookup"><span data-stu-id="b96a5-155">You want to retrieve all the information about these projects, so you'll use an HTTP GET request.</span></span>
<span data-ttu-id="b96a5-156">Tarayıcınız, ayrıca hangi bilgileri görmek için URL'yi tarayıcınıza aldığınız, yapıştırabilirsiniz HTTP GET istekleri ve işleme kullanır.</span><span class="sxs-lookup"><span data-stu-id="b96a5-156">Your browser also uses HTTP GET requests, so you can paste that URL into your browser to see what information you'll be receiving and processing.</span></span>

<span data-ttu-id="b96a5-157">Kullandığınız <xref:System.Net.Http.HttpClient> web isteklerinde bulunmak için sınıf.</span><span class="sxs-lookup"><span data-stu-id="b96a5-157">You use the <xref:System.Net.Http.HttpClient> class to make web requests.</span></span> <span data-ttu-id="b96a5-158">İster modern tüm .NET API'lerini <xref:System.Net.Http.HttpClient> yalnızca zaman uyumsuz yöntemler için uzun süre çalışan API'ler destekler.</span><span class="sxs-lookup"><span data-stu-id="b96a5-158">Like all modern .NET APIs, <xref:System.Net.Http.HttpClient> supports only async methods for its long-running APIs.</span></span>
<span data-ttu-id="b96a5-159">Zaman uyumsuz bir yöntem sağlayarak başlatın.</span><span class="sxs-lookup"><span data-stu-id="b96a5-159">Start by making an async method.</span></span> <span data-ttu-id="b96a5-160">Uygulamanın işlevselliğini oluşturdukça uygulamasında doldururlar.</span><span class="sxs-lookup"><span data-stu-id="b96a5-160">You'll fill in the implementation as you build the functionality of the application.</span></span> <span data-ttu-id="b96a5-161">Başlangıç açarak `program.cs` dosya proje dizininde ve aşağıdaki yöntemi ekleyerek `Program` sınıfı:</span><span class="sxs-lookup"><span data-stu-id="b96a5-161">Start by opening the `program.cs` file in your project directory and adding the following method to the `Program` class:</span></span>

```csharp
private static async Task ProcessRepositories()
{
}
```

<span data-ttu-id="b96a5-162">Eklemeniz gerekecektir bir `using` en üstündeki deyimi, `Main` yöntemi C# derleyicisi tanımasını <xref:System.Threading.Tasks.Task> türü:</span><span class="sxs-lookup"><span data-stu-id="b96a5-162">You'll need to add a `using` statement at the top of your `Main` method so that the C# compiler recognizes the <xref:System.Threading.Tasks.Task> type:</span></span>

```csharp
using System.Threading.Tasks;
```

<span data-ttu-id="b96a5-163">Bu noktada, projenizi derleme yaparsanız herhangi içermez çünkü bu yöntem için oluşturulan bir uyarı alırsınız `await` işleçler ve zaman uyumlu olarak çalışır.</span><span class="sxs-lookup"><span data-stu-id="b96a5-163">If you build your project at this point, you'll get a warning generated for this method, because it does not contain any `await` operators and will run synchronously.</span></span> <span data-ttu-id="b96a5-164">Şimdilik yoksayın; ekleyeceğiniz `await` yazarken işleçleri yöntemi doldurun.</span><span class="sxs-lookup"><span data-stu-id="b96a5-164">Ignore that for now; you'll add `await` operators as you fill in the method.</span></span>

<span data-ttu-id="b96a5-165">Ardından, içinde tanımlanan ad alanı yeniden adlandırma `namespace` varsayılan deyimden `ConsoleApp` için `WebAPIClient`.</span><span class="sxs-lookup"><span data-stu-id="b96a5-165">Next, rename the namespace defined in the `namespace` statement from its default of `ConsoleApp` to `WebAPIClient`.</span></span> <span data-ttu-id="b96a5-166">Daha sonra tanımlarız bir `repo` bu ad alanındaki sınıfı.</span><span class="sxs-lookup"><span data-stu-id="b96a5-166">We'll later define a `repo` class in this namespace.</span></span>

<span data-ttu-id="b96a5-167">Ardından, güncelleştirme `Main` bu yöntemi çağırmak için yöntem.</span><span class="sxs-lookup"><span data-stu-id="b96a5-167">Next, update the `Main` method to call this method.</span></span> <span data-ttu-id="b96a5-168">`ProcessRepositories` Yöntemi bir görev döndürür ve bu görev tamamlanmadan önce programdan çıkmak olmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="b96a5-168">The `ProcessRepositories` method returns a Task, and you shouldn't exit the program before that task finishes.</span></span> <span data-ttu-id="b96a5-169">Bu nedenle, kullanmalısınız `Wait` engelleyin ve görevin tamamlanmasını bekle yöntemi:</span><span class="sxs-lookup"><span data-stu-id="b96a5-169">Therefore, you must use the `Wait` method to block and wait for the task to finish:</span></span>

```csharp
static void Main(string[] args)
{
    ProcessRepositories().Wait();
}
```

<span data-ttu-id="b96a5-170">Artık, hiçbir şey yapılmaz, ancak zaman uyumsuz olarak mevcut bir program var.</span><span class="sxs-lookup"><span data-stu-id="b96a5-170">Now, you have a program that does nothing, but does it asynchronously.</span></span> <span data-ttu-id="b96a5-171">Şimdi geliştirebilir.</span><span class="sxs-lookup"><span data-stu-id="b96a5-171">Let's improve it.</span></span>

<span data-ttu-id="b96a5-172">İlk veri Web'den yeteneğine sahip bir nesne gerekir; kullanabileceğiniz bir <xref:System.Net.Http.HttpClient> Bunu yapmak için.</span><span class="sxs-lookup"><span data-stu-id="b96a5-172">First you need an object that is capable to retrieve data from the web; you can use a <xref:System.Net.Http.HttpClient> to do that.</span></span> <span data-ttu-id="b96a5-173">Bu nesne, istek ve yanıtları işler.</span><span class="sxs-lookup"><span data-stu-id="b96a5-173">This object handles the request and the responses.</span></span> <span data-ttu-id="b96a5-174">Bu türde tek bir örneğini `Program` sınıf Program.cs dosyasının içinde.</span><span class="sxs-lookup"><span data-stu-id="b96a5-174">Instantiate a single instance of that type in the `Program` class inside the Program.cs file.</span></span>

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

<span data-ttu-id="b96a5-175">Geri dönelim `ProcessRepositories` yöntemi ve ilk sürümü doldurun:</span><span class="sxs-lookup"><span data-stu-id="b96a5-175">Let's go back to the `ProcessRepositories` method and fill in a first version of it:</span></span>

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

<span data-ttu-id="b96a5-176">Ayrıca iki eklemeniz gerekecektir yeni deyimleri için bu dosyanın üst derlemeye kullanarak:</span><span class="sxs-lookup"><span data-stu-id="b96a5-176">You'll need to also add two new using statements at the top of the file for this to compile:</span></span>

```csharp
using System.Net.Http;
using System.Net.Http.Headers;
```

<span data-ttu-id="b96a5-177">Bu ilk sürümü dotnet foundation kuruluş altındaki tüm depo listesi okumak için bir web isteği yapar.</span><span class="sxs-lookup"><span data-stu-id="b96a5-177">This first version makes a web request to read the list of all repositories under the dotnet foundation organization.</span></span> <span data-ttu-id="b96a5-178">(GitHub .NET Foundation 'dotnet' kimliğidir).</span><span class="sxs-lookup"><span data-stu-id="b96a5-178">(The gitHub ID for the .NET Foundation is 'dotnet').</span></span> <span data-ttu-id="b96a5-179">İlk birkaç satırı ayarlanan <xref:System.Net.Http.HttpClient> bu istek için.</span><span class="sxs-lookup"><span data-stu-id="b96a5-179">The first few lines set up the <xref:System.Net.Http.HttpClient> for this request.</span></span> <span data-ttu-id="b96a5-180">İlk olarak, bunu GitHub JSON yanıtları kabul edecek şekilde yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="b96a5-180">First, it is configured to accept the GitHub JSON responses.</span></span>
<span data-ttu-id="b96a5-181">Yalnızca JSON biçimidir.</span><span class="sxs-lookup"><span data-stu-id="b96a5-181">This format is simply JSON.</span></span> <span data-ttu-id="b96a5-182">Sonraki satır, bu nesneden tüm istekler için bir kullanıcı aracısı üstbilgisi ekler.</span><span class="sxs-lookup"><span data-stu-id="b96a5-182">The next line adds a User Agent header to all requests from this object.</span></span> <span data-ttu-id="b96a5-183">Bu iki üstbilgi GitHub sunucu kodu tarafından denetlenir ve Github'dan bilgileri almak gereklidir.</span><span class="sxs-lookup"><span data-stu-id="b96a5-183">These two headers are checked by the GitHub server code, and are necessary to retrieve information from GitHub.</span></span>

<span data-ttu-id="b96a5-184">Yapılandırmayı tamamladığınızda <xref:System.Net.Http.HttpClient>, bir web isteği ve yanıtı almak olun.</span><span class="sxs-lookup"><span data-stu-id="b96a5-184">After you've configured the <xref:System.Net.Http.HttpClient>, you make a web request and retrieve the response.</span></span> <span data-ttu-id="b96a5-185">Bu ilk sürümde kullandığınız <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)?displayProperty=nameWithType> kolaylık yöntemi.</span><span class="sxs-lookup"><span data-stu-id="b96a5-185">In this first version, you use the <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)?displayProperty=nameWithType> convenience method.</span></span> <span data-ttu-id="b96a5-186">Bu kolaylık yöntemi web isteği yapan bir görev başlatır ve ardından istek geri döndüğünde, yanıt akışına okur ve içeriği akıştan ayıklar.</span><span class="sxs-lookup"><span data-stu-id="b96a5-186">This convenience method starts a task that makes the web request, and then when the request returns, it reads the response stream and extracts the content from the stream.</span></span> <span data-ttu-id="b96a5-187">Yanıt gövdesi olarak döndürülen bir <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="b96a5-187">The body of the response is returned as a <xref:System.String>.</span></span> <span data-ttu-id="b96a5-188">Görev tamamlandığında kullanılabilir bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="b96a5-188">The string is available when the task completes.</span></span>

<span data-ttu-id="b96a5-189">Bu yöntem son iki satırı, o görev await ve konsola yanıt yazdırın.</span><span class="sxs-lookup"><span data-stu-id="b96a5-189">The final two lines of this method await that task, and then print the response to the console.</span></span>
<span data-ttu-id="b96a5-190">Uygulamayı oluşturun ve çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="b96a5-190">Build the app, and run it.</span></span> <span data-ttu-id="b96a5-191">Derleme uyarısı artık, çünkü kalktığını `ProcessRepositories` artık içeren bir `await` işleci.</span><span class="sxs-lookup"><span data-stu-id="b96a5-191">The build warning is gone now, because the `ProcessRepositories` now does contain an `await` operator.</span></span> <span data-ttu-id="b96a5-192">Biçimlendirilmiş metin JSON uzun bir görünümünü görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="b96a5-192">You'll see a long display of JSON formatted text.</span></span>

## <a name="processing-the-json-result"></a><span data-ttu-id="b96a5-193">JSON sonuç işleme</span><span class="sxs-lookup"><span data-stu-id="b96a5-193">Processing the JSON Result</span></span>

<span data-ttu-id="b96a5-194">Bu noktada, bir web sunucusundan bir yanıt almak ve bu yanıt olarak yer alan metni görüntülemek için kod yazdığınız.</span><span class="sxs-lookup"><span data-stu-id="b96a5-194">At this point, you've written the code to retrieve a response from a web server, and display the text that is contained in that response.</span></span> <span data-ttu-id="b96a5-195">Ardından, bu JSON yanıtı C# nesnelerini şimdi Dönüştür.</span><span class="sxs-lookup"><span data-stu-id="b96a5-195">Next, let's convert that JSON response into C# objects.</span></span>

<span data-ttu-id="b96a5-196">JSON serileştirici JSON verilerini C# nesnelerine dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="b96a5-196">The JSON Serializer converts JSON data into C# Objects.</span></span> <span data-ttu-id="b96a5-197">İlk göreviniz bu yanıttan kullandığınız bilgilerini içeren bir C# sınıf türü tanımlamaktır.</span><span class="sxs-lookup"><span data-stu-id="b96a5-197">Your first task is to define a C# class type to contain the information you use from this response.</span></span> <span data-ttu-id="b96a5-198">Bu hiçbiriyse bunu başlangıç depo adını içeren bir basit C# türü ile oluşturalım:</span><span class="sxs-lookup"><span data-stu-id="b96a5-198">Let's build this slowly, so start with a simple C# type that contains the name of the repository:</span></span>

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

<span data-ttu-id="b96a5-199">Yukarıdaki kod, 'repo.cs' adlı yeni bir dosya içinde yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="b96a5-199">Put the above code in a new file called 'repo.cs'.</span></span> <span data-ttu-id="b96a5-200">Bu sürüm sınıfının, JSON verilerini işlemek için en basit yolu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="b96a5-200">This version of the class represents the simplest path to process JSON data.</span></span> <span data-ttu-id="b96a5-201">Sınıf adı ve üye adı yerine aşağıdaki C# kuralları JSON Pakette kullanılan adları aynı.</span><span class="sxs-lookup"><span data-stu-id="b96a5-201">The class name and the member name match the names used in the JSON packet, instead of following C# conventions.</span></span> <span data-ttu-id="b96a5-202">Bazı configuration öznitelikleri daha sonra sağlayarak çözeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="b96a5-202">You'll fix that by providing some configuration attributes later.</span></span> <span data-ttu-id="b96a5-203">Bu sınıf, JSON seri hale getirme ve seri durumundan çıkarma başka bir önemli özelliği gösterilmektedir: JSON paketteki tüm alanlar, bu sınıfın bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="b96a5-203">This class demonstrates another important feature of JSON serialization and deserialization: Not all the fields in the JSON packet are part of this class.</span></span>
<span data-ttu-id="b96a5-204">JSON serileştirici kullanılan sınıf türü içinde yer almayan bilgi yoksayar.</span><span class="sxs-lookup"><span data-stu-id="b96a5-204">The JSON serializer will ignore information that is not included in the class type being used.</span></span>
<span data-ttu-id="b96a5-205">Bu özellik, yalnızca bir alt kümesi ile JSON paket alanlarda çalışan türleri oluşturmak kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="b96a5-205">This feature makes it easier to create types that work with only a subset of the fields in the JSON packet.</span></span>

<span data-ttu-id="b96a5-206">Türü oluşturduğunuza göre şimdi bu seri durumdan.</span><span class="sxs-lookup"><span data-stu-id="b96a5-206">Now that you've created the type, let's deserialize it.</span></span> <span data-ttu-id="b96a5-207">Oluşturmak ihtiyacınız olacak bir <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> nesne.</span><span class="sxs-lookup"><span data-stu-id="b96a5-207">You'll need to create a <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> object.</span></span> <span data-ttu-id="b96a5-208">Bu nesne, CLR türü beklenen JSON paket için bunu bilmeniz gerekir alır.</span><span class="sxs-lookup"><span data-stu-id="b96a5-208">This object must know the CLR type expected for the JSON packet it retrieves.</span></span> <span data-ttu-id="b96a5-209">Github depoları, bir dizi şekilde pakette bir `List<repo>` doğru türde.</span><span class="sxs-lookup"><span data-stu-id="b96a5-209">The packet from GitHub contains a sequence of repositories, so a `List<repo>` is the correct type.</span></span> <span data-ttu-id="b96a5-210">Aşağıdaki satırı ekleyin, `ProcessRepositories` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="b96a5-210">Add the following line to your `ProcessRepositories` method:</span></span>

```csharp
var serializer = new DataContractJsonSerializer(typeof(List<repo>));
```

<span data-ttu-id="b96a5-211">Bu da eklemeniz gerekir, böylece iki yeni ad alanları, kullanmakta olduğunuz:</span><span class="sxs-lookup"><span data-stu-id="b96a5-211">You're using two new namespaces, so you'll need to add those as well:</span></span>

```csharp
using System.Collections.Generic;
using System.Runtime.Serialization.Json;
```

<span data-ttu-id="b96a5-212">Ardından, JSON C# nesnelerine dönüştürmek için seri hale getirici kullanacaksınız.</span><span class="sxs-lookup"><span data-stu-id="b96a5-212">Next, you'll use the serializer to convert JSON into C# objects.</span></span> <span data-ttu-id="b96a5-213">Çağrısını <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)> içinde `ProcessRepositories` aşağıdaki iki satır ile yöntemi:</span><span class="sxs-lookup"><span data-stu-id="b96a5-213">Replace the call to <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)> in your `ProcessRepositories` method with the following two lines:</span></span>

```csharp
var streamTask = client.GetStreamAsync("https://api.github.com/orgs/dotnet/repos");
var repositories = serializer.ReadObject(await streamTask) as List<repo>;
```

<span data-ttu-id="b96a5-214">Kullanmakta olduğunuz bildirimi <xref:System.Net.Http.HttpClient.GetStreamAsync(System.String)> yerine <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)>.</span><span class="sxs-lookup"><span data-stu-id="b96a5-214">Notice that you're now using <xref:System.Net.Http.HttpClient.GetStreamAsync(System.String)> instead of <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)>.</span></span> <span data-ttu-id="b96a5-215">Seri hale getirici bir akış, bir dize yerine, kaynağı olarak kullanır.</span><span class="sxs-lookup"><span data-stu-id="b96a5-215">The serializer uses a stream instead of a string as its source.</span></span> <span data-ttu-id="b96a5-216">Şimdi ikinci satırında yukarıdaki kullanılan birkaç C# dili özellikleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b96a5-216">Let's explain a couple features of the C# language that are being used in the second line above.</span></span> <span data-ttu-id="b96a5-217">Bağımsız değişkeni <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject(System.IO.Stream)> olduğu bir `await` ifade.</span><span class="sxs-lookup"><span data-stu-id="b96a5-217">The argument to <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject(System.IO.Stream)> is an `await` expression.</span></span> <span data-ttu-id="b96a5-218">Await ifadeleri neredeyse herhangi bir yerinde görünebilir kodunuzda şimdiye kadar yalnızca bunları Atama ifadesinin bir parçası olarak gördüğünüz olsa bile.</span><span class="sxs-lookup"><span data-stu-id="b96a5-218">Await expressions can appear almost anywhere in your code, even though up to now, you've only seen them as part of an assignment statement.</span></span>

<span data-ttu-id="b96a5-219">İkincisi, `as` işleci dönüştürür derleme zamanı türünden `object` için `List<repo>`.</span><span class="sxs-lookup"><span data-stu-id="b96a5-219">Secondly, the `as` operator converts from the compile time type of `object` to `List<repo>`.</span></span>
<span data-ttu-id="b96a5-220">Bildirimi <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject(System.IO.Stream)> türünde bir nesne döndürür bildirir <xref:System.Object?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b96a5-220">The declaration of <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject(System.IO.Stream)> declares that it returns an object of type <xref:System.Object?displayProperty=nameWithType>.</span></span> <span data-ttu-id="b96a5-221"><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject(System.IO.Stream)> oluşturduğu zaman belirttiğiniz türü döndürür (`List<repo>` bu öğreticideki).</span><span class="sxs-lookup"><span data-stu-id="b96a5-221"><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject(System.IO.Stream)> will return the type you specified when you constructed it (`List<repo>` in this tutorial).</span></span> <span data-ttu-id="b96a5-222">Dönüştürme başarısız olursa `as` işleci değerlendirilen `null`, bir özel durum oluşturmaktansa.</span><span class="sxs-lookup"><span data-stu-id="b96a5-222">If the conversion does not succeed, the `as` operator evaluates to `null`, instead of throwing an exception.</span></span>

<span data-ttu-id="b96a5-223">Bu bölümde ile neredeyse hazırsınız.</span><span class="sxs-lookup"><span data-stu-id="b96a5-223">You're almost done with this section.</span></span> <span data-ttu-id="b96a5-224">C# nesnelerini JSON dönüştürdükten sonra şimdi her depo adını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="b96a5-224">Now that you've converted the JSON to C# objects, let's display the name of each repository.</span></span> <span data-ttu-id="b96a5-225">Okuma satırları değiştirin:</span><span class="sxs-lookup"><span data-stu-id="b96a5-225">Replace the lines that read:</span></span>

```csharp
var msg = await stringTask;   //**Deleted this
Console.Write(msg);
```

<span data-ttu-id="b96a5-226">şunlarla birlikte:</span><span class="sxs-lookup"><span data-stu-id="b96a5-226">with the following:</span></span>

```csharp
foreach (var repo in repositories)
    Console.WriteLine(repo.name);
```

<span data-ttu-id="b96a5-227">Derleme ve uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="b96a5-227">Compile and run the application.</span></span> <span data-ttu-id="b96a5-228">.NET Foundation'ın yer depolar adlarını yazdırılacağı.</span><span class="sxs-lookup"><span data-stu-id="b96a5-228">It will print out the names of the repositories that are part of the .NET Foundation.</span></span>

## <a name="controlling-serialization"></a><span data-ttu-id="b96a5-229">Serileştirme denetleme</span><span class="sxs-lookup"><span data-stu-id="b96a5-229">Controlling Serialization</span></span>

<span data-ttu-id="b96a5-230">Daha fazla özellik eklemeden önce şimdi adres `repo` yazın ve daha fazla standart C# kurallarına uygun hale getirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b96a5-230">Before you add more features, let's address the `repo` type and make it follow more standard C# conventions.</span></span> <span data-ttu-id="b96a5-231">Bu açıklama ekleyerek yaparsınız `repo` tür *öznitelikleri* JSON serileştirici nasıl çalıştığını denetleyen.</span><span class="sxs-lookup"><span data-stu-id="b96a5-231">You'll do this by annotating the `repo` type with *attributes* that control how the JSON Serializer works.</span></span> <span data-ttu-id="b96a5-232">Sizin durumunuzda, bu öznitelikler JSON anahtar adlarını ve C# sınıf ve üye adları arasında bir eşleme tanımlamak için kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="b96a5-232">In your case, you'll use these attributes to define a mapping between the JSON key names and the C# class and member names.</span></span> <span data-ttu-id="b96a5-233">Kullanılan iki öznitelikleri <xref:System.Runtime.Serialization.DataContractAttribute> ve <xref:System.Runtime.Serialization.DataMemberAttribute> öznitelikleri.</span><span class="sxs-lookup"><span data-stu-id="b96a5-233">The two attributes used are the <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> attributes.</span></span> <span data-ttu-id="b96a5-234">Kural gereği, tüm öznitelik sınıfları soneki bitiş `Attribute`.</span><span class="sxs-lookup"><span data-stu-id="b96a5-234">By convention, all Attribute classes end in the suffix `Attribute`.</span></span> <span data-ttu-id="b96a5-235">Ancak, bir öznitelik uygulamak soneki kullanın gerekmez.</span><span class="sxs-lookup"><span data-stu-id="b96a5-235">However, you do not need to use that suffix when you apply an attribute.</span></span>

<span data-ttu-id="b96a5-236"><xref:System.Runtime.Serialization.DataContractAttribute> Ve <xref:System.Runtime.Serialization.DataMemberAttribute> öznitelikleri olan farklı bir kitaplıkta, bu nedenle bu kitaplığı, bağımlılık olarak C# proje dosyası eklemek gerekir.</span><span class="sxs-lookup"><span data-stu-id="b96a5-236">The <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> attributes are in a different library, so you'll need to add that library to your C# project file as a dependency.</span></span> <span data-ttu-id="b96a5-237">Aşağıdaki satırı ekleyin `<ItemGroup>` proje dosyanızın bölümü:</span><span class="sxs-lookup"><span data-stu-id="b96a5-237">Add the following line to the `<ItemGroup>` section of your project file:</span></span>

```xml
<PackageReference Include="System.Runtime.Serialization.Primitives" Version="4.3.0" />
```

<span data-ttu-id="b96a5-238">Dosyayı kaydettikten sonra çalıştırın `dotnet restore` ([bkz. Not](#dotnet-restore-note)) bu paketi alınamadı.</span><span class="sxs-lookup"><span data-stu-id="b96a5-238">After you save the file, run `dotnet restore` ([see note](#dotnet-restore-note)) to retrieve this package.</span></span>

<span data-ttu-id="b96a5-239">Ardından, açık `repo.cs` dosya.</span><span class="sxs-lookup"><span data-stu-id="b96a5-239">Next, open the `repo.cs` file.</span></span> <span data-ttu-id="b96a5-240">Baş harfleri büyük kullanmanız ve tam adı yazım adı değiştirelim `Repository`.</span><span class="sxs-lookup"><span data-stu-id="b96a5-240">Let's change the name to use Pascal Case, and fully spell out the name `Repository`.</span></span> <span data-ttu-id="b96a5-241">Biz yine de eklemeniz gerekecektir. Bu nedenle bu tür için JSON 'repo' düğümleri eşlemek istediğiniz <xref:System.Runtime.Serialization.DataContractAttribute> sınıf bildirimine özniteliği.</span><span class="sxs-lookup"><span data-stu-id="b96a5-241">We still want to map JSON 'repo' nodes to this type, so you'll need to add the <xref:System.Runtime.Serialization.DataContractAttribute> attribute to the class declaration.</span></span> <span data-ttu-id="b96a5-242">Siz ayarlarsınız `Name` bu türüyle JSON düğüm adı özniteliğinin özelliği:</span><span class="sxs-lookup"><span data-stu-id="b96a5-242">You'll set the `Name` property of the attribute to the name of the JSON nodes that map to this type:</span></span>

```csharp
[DataContract(Name="repo")]
public class Repository
```

<span data-ttu-id="b96a5-243"><xref:System.Runtime.Serialization.DataContractAttribute> Üyesi <xref:System.Runtime.Serialization> ad alanı, bu nedenle uygun eklemeniz gerekir `using` deyimini dosyanın üst:</span><span class="sxs-lookup"><span data-stu-id="b96a5-243">The <xref:System.Runtime.Serialization.DataContractAttribute> is a member of the <xref:System.Runtime.Serialization> namespace, so you'll need to add the appropriate `using` statement at the top of the file:</span></span>

```csharp
using System.Runtime.Serialization;
```

<span data-ttu-id="b96a5-244">Adını değiştirdiğinizi `repo` sınıfının `Repository`, bu nedenle aynı ad Program.cs içinde değişikliğini yapmanız gerekir (bazı düzenleyiciler otomatik olarak bu değişikliği yapmadan bir yeniden adlandırma düzenlemesi destekleyebilir:)</span><span class="sxs-lookup"><span data-stu-id="b96a5-244">You changed the name of the `repo` class to `Repository`, so you'll need to make the same name change in Program.cs (some editors may support a rename refactoring that will make this change automatically:)</span></span>

```csharp
var serializer = new DataContractJsonSerializer(typeof(List<Repository>));

// ...

var repositories = serializer.ReadObject(await streamTask) as List<Repository>;
```

<span data-ttu-id="b96a5-245">Ardından, aynı değişikliği olalım `name` kullanarak alan <xref:System.Runtime.Serialization.DataMemberAttribute> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="b96a5-245">Next, let's make the same change with the `name` field by using the <xref:System.Runtime.Serialization.DataMemberAttribute> class.</span></span> <span data-ttu-id="b96a5-246">Bildirimi için aşağıdaki değişiklikleri yapın `name` repo.cs alanındaki:</span><span class="sxs-lookup"><span data-stu-id="b96a5-246">Make the following changes to the declaration of the `name` field in repo.cs:</span></span>

```csharp
[DataMember(Name="name")]
public string Name;
```

<span data-ttu-id="b96a5-247">Bu değişiklik, program.cs içinde her deponun adını yazar kodu değiştirmek ihtiyacınız olduğu anlamına gelir:</span><span class="sxs-lookup"><span data-stu-id="b96a5-247">This change means you need to change the code that writes the name of each repository in program.cs:</span></span>

```csharp
Console.WriteLine(repo.Name);
```

<span data-ttu-id="b96a5-248">Yapmak bir `dotnet build` arkasından bir `dotnet run` gördüğümüz eşlemeleri doğru emin olmak için.</span><span class="sxs-lookup"><span data-stu-id="b96a5-248">Do a `dotnet build` followed by a `dotnet run` to make sure you've got the mappings correct.</span></span> <span data-ttu-id="b96a5-249">Önce aynı çıktıyı görmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="b96a5-249">You should see the same output as before.</span></span> <span data-ttu-id="b96a5-250">Daha fazla değişiklik için size daha fazla özellik web sunucusundan işlemeden önce olalım `Repository` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="b96a5-250">Before we process more properties from the web server, let's make one more change to the `Repository` class.</span></span> <span data-ttu-id="b96a5-251">`Name` Üye ortak olarak erişilebilen bir alandır.</span><span class="sxs-lookup"><span data-stu-id="b96a5-251">The `Name` member is a publicly accessible field.</span></span> <span data-ttu-id="b96a5-252">Nesne yönelimli iyi değil, şimdi bunu bir özelliğini değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b96a5-252">That's not a good object-oriented practice, so let's change it to a property.</span></span> <span data-ttu-id="b96a5-253">Amaçlarımız doğrultusunda alma veya özellik ayarlama, çalıştırmak için özel kod gerekmez, ancak bir özelliğe değiştirme kolaylaştırır kullanan herhangi bir kod bozup olmadan bu değişiklikleri daha sonra eklenecek `Repository` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="b96a5-253">For our purposes, we don't need any specific code to run when getting or setting the property, but changing to a property makes it easier to add those changes later without breaking any code that uses the `Repository` class.</span></span>

<span data-ttu-id="b96a5-254">Alan tanımını kaldırın ve değiştirin bir [otomatik uygulanan özellik](../programming-guide/classes-and-structs/auto-implemented-properties.md):</span><span class="sxs-lookup"><span data-stu-id="b96a5-254">Remove the field definition, and replace it with an [auto-implemented property](../programming-guide/classes-and-structs/auto-implemented-properties.md):</span></span>

```csharp
public string Name { get; set; }
```

<span data-ttu-id="b96a5-255">Derleyici gövdesinin oluşturur `get` ve `set` erişimcileri, aynı zamanda özel bir alan adı depolamak için.</span><span class="sxs-lookup"><span data-stu-id="b96a5-255">The compiler generates the body of the `get` and `set` accessors, as well as a private field to store the name.</span></span> <span data-ttu-id="b96a5-256">El ile yazabilirsiniz aşağıdaki koda benzer olacaktır:</span><span class="sxs-lookup"><span data-stu-id="b96a5-256">It would be similar to the following code that you could type by hand:</span></span>

```csharp
public string Name
{
    get { return this._name; }
    set { this._name = value; }
}
private string _name;
```

<span data-ttu-id="b96a5-257">Şimdi yeni özellikler eklemeden önce bir daha fazla değişiklik yapın.</span><span class="sxs-lookup"><span data-stu-id="b96a5-257">Let's make one more change before adding new features.</span></span> <span data-ttu-id="b96a5-258">`ProcessRepositories` Yöntemi zaman uyumsuz çalışma yapmak ve depoları koleksiyonunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="b96a5-258">The `ProcessRepositories` method can do the async work and return a collection of the repositories.</span></span> <span data-ttu-id="b96a5-259">Şimdi iade `List<Repository>` o yöntemi ve taşıma bilgilerini yazar kodu `Main` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="b96a5-259">Let's return the `List<Repository>` from that method, and move the code that writes the information into the `Main` method.</span></span>

<span data-ttu-id="b96a5-260">İmzasını Değiştir `ProcessRepositories` bir görevin sonucu bir listedir döndürmek için `Repository` nesneler:</span><span class="sxs-lookup"><span data-stu-id="b96a5-260">Change the signature of `ProcessRepositories` to return a task whose result is a list of `Repository` objects:</span></span>

```csharp
private static async Task<List<Repository>> ProcessRepositories()
```

<span data-ttu-id="b96a5-261">Ardından, yalnızca depolar JSON yanıtı işledikten sonra dönüş:</span><span class="sxs-lookup"><span data-stu-id="b96a5-261">Then, just return the repositories after processing the JSON response:</span></span>

```csharp
var repositories = serializer.ReadObject(await streamTask) as List<Repository>;
return repositories;
```

<span data-ttu-id="b96a5-262">Derleyicinin oluşturduğu `Task<T>` çünkü bu yöntem olarak işaretlediğiniz için döndürülecek nesne `async`.</span><span class="sxs-lookup"><span data-stu-id="b96a5-262">The compiler generates the `Task<T>` object for the return because you've marked this method as `async`.</span></span>
<span data-ttu-id="b96a5-263">Ardından, değişiklik bakalım `Main` BT'nin bunlar yakalar, böylece yöntemi sonuçlarını ve her bir depo adı konsola yazar.</span><span class="sxs-lookup"><span data-stu-id="b96a5-263">Then, let's modify the `Main` method so that it captures those results and writes each repository name to the console.</span></span> <span data-ttu-id="b96a5-264">`Main` Metodu artık şuna benzer:</span><span class="sxs-lookup"><span data-stu-id="b96a5-264">Your `Main` method now looks like this:</span></span>

```csharp
public static void Main(string[] args)
{
    var repositories = ProcessRepositories().Result;

    foreach (var repo in repositories)
        Console.WriteLine(repo.Name);
}
```

<span data-ttu-id="b96a5-265">Erişim `Result` bir görevin özelliği, görev tamamlanıncaya kadar engeller.</span><span class="sxs-lookup"><span data-stu-id="b96a5-265">Accessing the `Result` property of a Task blocks until the task has completed.</span></span> <span data-ttu-id="b96a5-266">Normalde, tercih `await` görüldüğü görevi tamamlanırken `ProcessRepositories` yöntemi ancak içinde kullanılamaz `Main` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="b96a5-266">Normally, you would prefer to `await` the completion of the task, as in the `ProcessRepositories` method, but that isn't allowed in the `Main` method.</span></span>

## <a name="reading-more-information"></a><span data-ttu-id="b96a5-267">Daha fazla bilgi okuma</span><span class="sxs-lookup"><span data-stu-id="b96a5-267">Reading More Information</span></span>

<span data-ttu-id="b96a5-268">Şimdi bu GitHub API'den gidiyor JSON paket özelliklerinde, birkaç daha işleyerek tamamlayın.</span><span class="sxs-lookup"><span data-stu-id="b96a5-268">Let's finish this by processing a few more of the properties in the JSON packet that gets sent from the GitHub API.</span></span> <span data-ttu-id="b96a5-269">Her şeyi edinin istemezsiniz, ancak bazı özellikler ekleme, C# dilinin birkaç daha fazla özellik gösterilecektir.</span><span class="sxs-lookup"><span data-stu-id="b96a5-269">You won't want to grab everything, but adding a few properties will demonstrate a few more features of the C# language.</span></span>

<span data-ttu-id="b96a5-270">Daha fazla birkaç basit türler için ekleyerek başlayalım `Repository` sınıf tanımını.</span><span class="sxs-lookup"><span data-stu-id="b96a5-270">Let's start by adding a few more simple types to the `Repository` class definition.</span></span> <span data-ttu-id="b96a5-271">Bu özellikler, o sınıfa ekleyin:</span><span class="sxs-lookup"><span data-stu-id="b96a5-271">Add these properties to that class:</span></span>

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

<span data-ttu-id="b96a5-272">Bu özellikler hedef türe (olan JSON paketlerinin ne içermesi) dize türünden yerleşik dönüştürmeleri vardır.</span><span class="sxs-lookup"><span data-stu-id="b96a5-272">These properties have built-in conversions from the string type (which is what the JSON packets contain) to the target type.</span></span> <span data-ttu-id="b96a5-273"><xref:System.Uri> Türü için yeni olabilir.</span><span class="sxs-lookup"><span data-stu-id="b96a5-273">The <xref:System.Uri> type may be new to you.</span></span> <span data-ttu-id="b96a5-274">Bir URI'yı temsil veya bu durumda, bir URL.</span><span class="sxs-lookup"><span data-stu-id="b96a5-274">It represents a URI, or in this case, a URL.</span></span> <span data-ttu-id="b96a5-275">Durumunda, `Uri` ve `int` türleri, JSON paket hedef türe dönüştürülmeyecekse veri içeriyorsa, serileştirme eylemi bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b96a5-275">In the case of the `Uri` and `int` types, if the JSON packet contains data that does not convert to the target type, the serialization action will throw an exception.</span></span>

<span data-ttu-id="b96a5-276">Bunlar ekledikten sonra güncelleştirme `Main` yöntemi bu öğeleri görüntülemek için:</span><span class="sxs-lookup"><span data-stu-id="b96a5-276">Once you've added these, update the `Main` method to display those elements:</span></span>

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

<span data-ttu-id="b96a5-277">Son adım olarak, son zorlama işlemi için bilgi ekleyelim.</span><span class="sxs-lookup"><span data-stu-id="b96a5-277">As a final step, let's add the information for the last push operation.</span></span> <span data-ttu-id="b96a5-278">Bu bilgiler, JSON yanıtındaki bu şekilde biçimlendirilir:</span><span class="sxs-lookup"><span data-stu-id="b96a5-278">This information is formatted in this fashion in the JSON response:</span></span>

```json
2016-02-08T21:27:00Z
```

<span data-ttu-id="b96a5-279">Bu biçim standart .NET hiçbirini izlemez <xref:System.DateTime> biçimleri.</span><span class="sxs-lookup"><span data-stu-id="b96a5-279">That format does not follow any of the standard .NET <xref:System.DateTime> formats.</span></span> <span data-ttu-id="b96a5-280">Bu nedenle özel dönüştürme yöntemi yazma gerekecektir.</span><span class="sxs-lookup"><span data-stu-id="b96a5-280">Because of that, you'll need to write a custom conversion method.</span></span> <span data-ttu-id="b96a5-281">Ayrıca bunu büyük olasılıkla kullanıcıları için kullanıma sunulan ham dize istemediğiniz `Repository` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="b96a5-281">You also probably don't want the raw string exposed to users of the `Repository` class.</span></span> <span data-ttu-id="b96a5-282">Öznitelikleri de bu denetim yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="b96a5-282">Attributes can help control that as well.</span></span> <span data-ttu-id="b96a5-283">İlk olarak tanımlayan bir `private` tarih saat dize gösterimini tutacak özelliği, `Repository` sınıfı:</span><span class="sxs-lookup"><span data-stu-id="b96a5-283">First, define a `private` property that will hold the string representation of the date time in your `Repository` class:</span></span>

```csharp
[DataMember(Name="pushed_at")]
private string JsonDate { get; set; }
```

<span data-ttu-id="b96a5-284"><xref:System.Runtime.Serialization.DataMemberAttribute> Öznitelik bildirir seri hale getirici bu işlenmesi gerektiğini, bir ortak üye olmasa bile.</span><span class="sxs-lookup"><span data-stu-id="b96a5-284">The <xref:System.Runtime.Serialization.DataMemberAttribute> attribute informs the serializer that this should be processed, even though it is not a public member.</span></span> <span data-ttu-id="b96a5-285">Ardından, geçerli bir dize dönüştürür genel bir salt okunur özelliği yazmanız gereken <xref:System.DateTime> nesne ve döndüren <xref:System.DateTime>:</span><span class="sxs-lookup"><span data-stu-id="b96a5-285">Next, you need to write a public read-only property that converts the string to a valid <xref:System.DateTime> object, and returns that <xref:System.DateTime>:</span></span>

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

<span data-ttu-id="b96a5-286">Şimdi yeni yapıları üzerinden geçelim.</span><span class="sxs-lookup"><span data-stu-id="b96a5-286">Let's go over the new constructs above.</span></span> <span data-ttu-id="b96a5-287">`IgnoreDataMember` Özniteliği, bu tür okuma veya herhangi bir JSON nesnesinden yazılmış, seri hale getirici bildirir.</span><span class="sxs-lookup"><span data-stu-id="b96a5-287">The `IgnoreDataMember` attribute instructs the serializer that this type should not be read to or written from any JSON object.</span></span> <span data-ttu-id="b96a5-288">Bu özellik yalnızca içeren bir `get` erişimcisi.</span><span class="sxs-lookup"><span data-stu-id="b96a5-288">This property contains only a `get` accessor.</span></span> <span data-ttu-id="b96a5-289">Var olan hiçbir `set` erişimcisi.</span><span class="sxs-lookup"><span data-stu-id="b96a5-289">There is no `set` accessor.</span></span> <span data-ttu-id="b96a5-290">Nasıl tanımladığınızı olan bir *salt okunur* C# özelliği.</span><span class="sxs-lookup"><span data-stu-id="b96a5-290">That's how you define a *read-only* property in C#.</span></span> <span data-ttu-id="b96a5-291">(Evet, oluşturabileceğiniz *salt yazılır* C# ancak değerlerine özellikleri sınırlıdır.) <xref:System.DateTime.ParseExact(System.String,System.String,System.IFormatProvider)> Yöntemi bir dizeyi ayrıştırır ve oluşturan bir <xref:System.DateTime> sağlanan tarih biçimini kullanarak nesne ve ek meta veri için ekler `DateTime` kullanarak bir `CultureInfo` nesne.</span><span class="sxs-lookup"><span data-stu-id="b96a5-291">(Yes, you can create *write-only* properties in C#, but their value is limited.) The <xref:System.DateTime.ParseExact(System.String,System.String,System.IFormatProvider)> method parses a string and creates a <xref:System.DateTime> object using a provided date format, and adds additional metadata to the `DateTime` using a `CultureInfo` object.</span></span> <span data-ttu-id="b96a5-292">Ayrıştırma işlemi başarısız olursa, özellik erişimcisi özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b96a5-292">If the parse operation fails, the property accessor throws an exception.</span></span>

<span data-ttu-id="b96a5-293">Kullanılacak <xref:System.Globalization.CultureInfo.InvariantCulture>, eklemeniz gerekecektir <xref:System.Globalization> ad alanına `using` deyimlerinde `repo.cs`:</span><span class="sxs-lookup"><span data-stu-id="b96a5-293">To use <xref:System.Globalization.CultureInfo.InvariantCulture>, you will need to add the <xref:System.Globalization> namespace to the `using` statements in `repo.cs`:</span></span>

```csharp
using System.Globalization;
```

<span data-ttu-id="b96a5-294">Son olarak, bir deyim konsolunda daha çıkış ve oluşturup bu uygulamayı yeniden çalıştırmak hazır ekleyin:</span><span class="sxs-lookup"><span data-stu-id="b96a5-294">Finally, add one more output statement in the console, and you're ready to build and run this app again:</span></span>

```csharp
Console.WriteLine(repo.LastPush);
```

<span data-ttu-id="b96a5-295">Sürümünüz artık eşleşmelidir [tamamlanan örnek](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient).</span><span class="sxs-lookup"><span data-stu-id="b96a5-295">Your version should now match the [finished sample](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient).</span></span>

## <a name="conclusion"></a><span data-ttu-id="b96a5-296">Sonuç</span><span class="sxs-lookup"><span data-stu-id="b96a5-296">Conclusion</span></span>

<span data-ttu-id="b96a5-297">Bu öğreticide, web isteklerinde bulunmak, istemcinin sonucu ayrıştırması ve sonuçları özelliklerini görüntülemek nasıl gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="b96a5-297">This tutorial showed you how to make web requests, parse the result, and display properties of those results.</span></span> <span data-ttu-id="b96a5-298">Projenizde bağımlılıklar olarak yeni paketler de ekledik.</span><span class="sxs-lookup"><span data-stu-id="b96a5-298">You've also added new packages as dependencies in your project.</span></span> <span data-ttu-id="b96a5-299">C# dilinin nesne yönelimli teknikleri destekleyen özelliklerden bazıları gördünüz.</span><span class="sxs-lookup"><span data-stu-id="b96a5-299">You've seen some of the features of the C# language that support object-oriented techniques.</span></span>

<a name="dotnet-restore-note"></a>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
