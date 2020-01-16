---
title: .NET Core kullanarak REST istemcisi oluşturma
description: Bu öğretici, .NET Core ve bu C# dilin çeşitli özelliklerini öğretir.
ms.date: 01/09/2020
ms.assetid: 51033ce2-7a53-4cdd-966d-9da15c8204d2
ms.openlocfilehash: 9478966598a9aaa1e9f592b72afce8f878a38abf
ms.sourcegitcommit: c01c18755bb7b0f82c7232314ccf7955ea7834db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/15/2020
ms.locfileid: "75964416"
---
# <a name="rest-client"></a><span data-ttu-id="8f077-103">REST istemcisi</span><span class="sxs-lookup"><span data-stu-id="8f077-103">REST client</span></span>

## <a name="introduction"></a><span data-ttu-id="8f077-104">Giriş</span><span class="sxs-lookup"><span data-stu-id="8f077-104">Introduction</span></span>

<span data-ttu-id="8f077-105">Bu öğretici, .NET Core ve bu C# dilin çeşitli özelliklerini öğretir.</span><span class="sxs-lookup"><span data-stu-id="8f077-105">This tutorial teaches you a number of features in .NET Core and the C# language.</span></span> <span data-ttu-id="8f077-106">Şunları öğrenirsiniz:</span><span class="sxs-lookup"><span data-stu-id="8f077-106">You’ll learn:</span></span>

* <span data-ttu-id="8f077-107">.NET Core komut satırı arabirimi (CLı) temelleri.</span><span class="sxs-lookup"><span data-stu-id="8f077-107">The basics of the .NET Core Command Line Interface (CLI).</span></span>
* <span data-ttu-id="8f077-108">C# Dil özelliklerine genel bakış.</span><span class="sxs-lookup"><span data-stu-id="8f077-108">An overview of C# Language features.</span></span>
* <span data-ttu-id="8f077-109">NuGet ile bağımlılıkları yönetme</span><span class="sxs-lookup"><span data-stu-id="8f077-109">Managing dependencies with NuGet</span></span>
* <span data-ttu-id="8f077-110">HTTP Iletişimleri</span><span class="sxs-lookup"><span data-stu-id="8f077-110">HTTP Communications</span></span>
* <span data-ttu-id="8f077-111">JSON bilgilerini işleme</span><span class="sxs-lookup"><span data-stu-id="8f077-111">Processing JSON information</span></span>
* <span data-ttu-id="8f077-112">Yapılandırmayı özniteliklerle yönetme.</span><span class="sxs-lookup"><span data-stu-id="8f077-112">Managing configuration with Attributes.</span></span>

<span data-ttu-id="8f077-113">GitHub 'da REST hizmetine HTTP Istekleri veren bir uygulama oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="8f077-113">You’ll build an application that issues HTTP Requests to a REST service on GitHub.</span></span> <span data-ttu-id="8f077-114">JSON biçiminde bilgileri okuyacaksınız ve bu JSON paketini C# nesnelerine dönüştürürsünüz.</span><span class="sxs-lookup"><span data-stu-id="8f077-114">You'll read information in JSON format, and convert that JSON packet into C# objects.</span></span> <span data-ttu-id="8f077-115">Son olarak, C# nesneleriyle nasıl çalışacaksınız görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="8f077-115">Finally, you'll see how to work with C# objects.</span></span>

<span data-ttu-id="8f077-116">Bu öğreticide birçok özellik vardır.</span><span class="sxs-lookup"><span data-stu-id="8f077-116">There are a lot of features in this tutorial.</span></span> <span data-ttu-id="8f077-117">Bunları birer birer oluşturalım.</span><span class="sxs-lookup"><span data-stu-id="8f077-117">Let’s build them one by one.</span></span>

<span data-ttu-id="8f077-118">Bu konuyla ilgili [son örnekle](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient) birlikte izlemeyi tercih ediyorsanız, indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8f077-118">If you prefer to follow along with the [final sample](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient) for this topic, you can download it.</span></span> <span data-ttu-id="8f077-119">İndirme yönergeleri için bkz. [örnekler ve öğreticiler](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="8f077-119">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="8f077-120">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="8f077-120">Prerequisites</span></span>

<span data-ttu-id="8f077-121">Makinenizi .NET Core çalıştıracak şekilde ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="8f077-121">You’ll need to set up your machine to run .NET core.</span></span> <span data-ttu-id="8f077-122">Yükleme yönergelerini [.NET Core İndirmeleri](https://dotnet.microsoft.com/download) sayfasında bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8f077-122">You can find the installation instructions on the [.NET Core Downloads](https://dotnet.microsoft.com/download) page.</span></span> <span data-ttu-id="8f077-123">Bu uygulamayı Windows, Linux, macOS veya bir Docker kapsayıcısında çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8f077-123">You can run this application on Windows, Linux, macOS or in a Docker container.</span></span>
<span data-ttu-id="8f077-124">En sevdiğiniz kod düzenleyicinizi yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="8f077-124">You’ll need to install your favorite code editor.</span></span> <span data-ttu-id="8f077-125">Aşağıdaki açıklamalar açık kaynaklı, platformlar arası bir düzenleyici olan [Visual Studio Code](https://code.visualstudio.com/)kullanır.</span><span class="sxs-lookup"><span data-stu-id="8f077-125">The descriptions below use [Visual Studio Code](https://code.visualstudio.com/), which is an open source, cross platform editor.</span></span> <span data-ttu-id="8f077-126">Bununla birlikte, rahat olan her türlü aracı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8f077-126">However, you can use whatever tools you are comfortable with.</span></span>

## <a name="create-the-application"></a><span data-ttu-id="8f077-127">Uygulamayı oluşturma</span><span class="sxs-lookup"><span data-stu-id="8f077-127">Create the Application</span></span>

<span data-ttu-id="8f077-128">İlk adım yeni bir uygulama oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="8f077-128">The first step is to create a new application.</span></span> <span data-ttu-id="8f077-129">Bir komut istemi açın ve uygulamanız için yeni bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="8f077-129">Open a command prompt and create a new directory for your application.</span></span> <span data-ttu-id="8f077-130">Geçerli dizini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="8f077-130">Make that the current directory.</span></span> <span data-ttu-id="8f077-131">Konsol penceresine aşağıdaki komutu girin:</span><span class="sxs-lookup"><span data-stu-id="8f077-131">Enter the following command in a console window:</span></span>

```dotnetcli
dotnet new console --name WebApiClient
```

<span data-ttu-id="8f077-132">Bu, temel bir "Merhaba Dünya" uygulaması için başlangıç dosyalarını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8f077-132">This creates the starter files for a basic "Hello World" application.</span></span> <span data-ttu-id="8f077-133">Proje adı "WebApiClient" dir.</span><span class="sxs-lookup"><span data-stu-id="8f077-133">The project name is "WebApiClient".</span></span> <span data-ttu-id="8f077-134">Bu yeni bir proje olduğundan, bağımlılıklardan hiçbiri yerinde değildir, bu nedenle ilk çalıştırma .NET Core Framework 'ü indirir, bir geliştirme sertifikası yükler ve eksik bağımlılıkları geri yüklemek için NuGet Paket Yöneticisi 'ni çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="8f077-134">As this is a new project, none of the dependencies are in place, so the first run will download the .NET Core framework, install a development certificate and run the NuGet package manager to restore missing dependencies.</span></span>

<span data-ttu-id="8f077-135">Değişiklik yapmaya başlamadan önce, uygulamanızı çalıştırmak için komut isteminde `dotnet run` ([bkz. Note](#dotnet-restore-note)) yazın.</span><span class="sxs-lookup"><span data-stu-id="8f077-135">Before you start making modifications, type `dotnet run` ([see note](#dotnet-restore-note)) at the command prompt to run your application.</span></span> <span data-ttu-id="8f077-136">`dotnet run`, ortamınızda bağımlılıklar eksik ise `dotnet restore` otomatik olarak gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="8f077-136">`dotnet run` automatically performs `dotnet restore` if your environment is missing dependencies.</span></span> <span data-ttu-id="8f077-137">Uygulamanızın yeniden oluşturulması gerekiyorsa `dotnet build` de gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="8f077-137">It also performs `dotnet build` if your application needs to be rebuilt.</span></span>
<span data-ttu-id="8f077-138">İlk kurulumdan sonra, yalnızca projeniz için anlamlı olduğunda `dotnet restore` veya `dotnet build` çalıştırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="8f077-138">After your initial setup, you will only need to run `dotnet restore` or `dotnet build` when it makes sense for your project.</span></span>

## <a name="adding-new-dependencies"></a><span data-ttu-id="8f077-139">Yeni bağımlılıklar ekleniyor</span><span class="sxs-lookup"><span data-stu-id="8f077-139">Adding New Dependencies</span></span>

<span data-ttu-id="8f077-140">.NET Core için önemli tasarım amaçlarından biri, .NET yüklemesinin boyutunu en aza indirmektir.</span><span class="sxs-lookup"><span data-stu-id="8f077-140">One of the key design goals for .NET Core is to minimize the size of the .NET installation.</span></span> <span data-ttu-id="8f077-141">Bir uygulamanın bazı özellikleri için ek kitaplıklar gerekiyorsa, bu bağımlılıkları C# proje (\*. csproj) dosyanıza eklersiniz.</span><span class="sxs-lookup"><span data-stu-id="8f077-141">If an application needs additional libraries for some of its features, you add those dependencies into your C# project (\*.csproj) file.</span></span> <span data-ttu-id="8f077-142">Örneğimizde, uygulamanızın JSON yanıtlarını işleyebilmesi için `System.Runtime.Serialization.Json` paketini eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="8f077-142">For our example, you'll need to add the `System.Runtime.Serialization.Json` package, so your application can process JSON responses.</span></span>

<span data-ttu-id="8f077-143">Bu uygulama için `System.Runtime.Serialization.Json` pakete ihtiyacınız olacak.</span><span class="sxs-lookup"><span data-stu-id="8f077-143">You'll need the `System.Runtime.Serialization.Json` package for this application.</span></span> <span data-ttu-id="8f077-144">Aşağıdaki [.net CLI](../../core/tools/dotnet-add-package.md) komutunu çalıştırarak projenize ekleyin:</span><span class="sxs-lookup"><span data-stu-id="8f077-144">Add it to your project by running the following [.NET CLI](../../core/tools/dotnet-add-package.md) command:</span></span>

```console
dotnet add package System.Text.Json
```

## <a name="making-web-requests"></a><span data-ttu-id="8f077-145">Web Istekleri yapma</span><span class="sxs-lookup"><span data-stu-id="8f077-145">Making Web Requests</span></span>

<span data-ttu-id="8f077-146">Artık Web 'den veri almaya başlamaya hazırsınız.</span><span class="sxs-lookup"><span data-stu-id="8f077-146">Now you're ready to start retrieving data from the web.</span></span> <span data-ttu-id="8f077-147">Bu uygulamada, [GITHUB API](https://developer.github.com/v3/)'sindeki bilgileri okuyacaksınız.</span><span class="sxs-lookup"><span data-stu-id="8f077-147">In this application, you'll read information from the [GitHub API](https://developer.github.com/v3/).</span></span> <span data-ttu-id="8f077-148">[.Net Foundation](https://www.dotnetfoundation.org/) şemsiye kapsamındaki projelerle ilgili bilgileri okuyalim.</span><span class="sxs-lookup"><span data-stu-id="8f077-148">Let's read information about the projects under the [.NET Foundation](https://www.dotnetfoundation.org/) umbrella.</span></span> <span data-ttu-id="8f077-149">Projeler hakkındaki bilgileri almak için GitHub API 'sine istek yaparak başlayacaksınız.</span><span class="sxs-lookup"><span data-stu-id="8f077-149">You'll start by making the request to the GitHub API to retrieve information on the projects.</span></span> <span data-ttu-id="8f077-150">Kullanacağınız uç nokta: <https://api.github.com/orgs/dotnet/repos>.</span><span class="sxs-lookup"><span data-stu-id="8f077-150">The endpoint you'll use is: <https://api.github.com/orgs/dotnet/repos>.</span></span> <span data-ttu-id="8f077-151">Bu projelerle ilgili tüm bilgileri almak istiyorsunuz, bu nedenle bir HTTP GET isteği kullanacaksınız.</span><span class="sxs-lookup"><span data-stu-id="8f077-151">You want to retrieve all the information about these projects, so you'll use an HTTP GET request.</span></span>
<span data-ttu-id="8f077-152">Tarayıcınız ayrıca HTTP GET isteklerini kullanır; bu nedenle, hangi bilgileri almak ve işlemek istediğinizi görmek için bu URL 'YI tarayıcınıza yapıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8f077-152">Your browser also uses HTTP GET requests, so you can paste that URL into your browser to see what information you'll be receiving and processing.</span></span>

<span data-ttu-id="8f077-153">Web istekleri yapmak için <xref:System.Net.Http.HttpClient> sınıfını kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="8f077-153">You use the <xref:System.Net.Http.HttpClient> class to make web requests.</span></span> <span data-ttu-id="8f077-154">Tüm modern .NET API 'Leri gibi <xref:System.Net.Http.HttpClient>, uzun süre çalışan API 'Ler için yalnızca zaman uyumsuz yöntemleri destekler.</span><span class="sxs-lookup"><span data-stu-id="8f077-154">Like all modern .NET APIs, <xref:System.Net.Http.HttpClient> supports only async methods for its long-running APIs.</span></span>
<span data-ttu-id="8f077-155">Zaman uyumsuz bir yöntem yaparak başlayın.</span><span class="sxs-lookup"><span data-stu-id="8f077-155">Start by making an async method.</span></span> <span data-ttu-id="8f077-156">Uygulamanın işlevlerini oluştururken uygulamayı doldurursunuz.</span><span class="sxs-lookup"><span data-stu-id="8f077-156">You'll fill in the implementation as you build the functionality of the application.</span></span> <span data-ttu-id="8f077-157">`program.cs` dosyasını proje dizininizde açıp `Program` sınıfına aşağıdaki yöntemi ekleyerek başlayın:</span><span class="sxs-lookup"><span data-stu-id="8f077-157">Start by opening the `program.cs` file in your project directory and adding the following method to the `Program` class:</span></span>

```csharp
private static async Task ProcessRepositories()
{
}
```

<span data-ttu-id="8f077-158">C# Derleyicinin <xref:System.Threading.Tasks.Task> türünü tanıması için `Main` yönteminizin en üstüne `using` bir ifade eklemeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="8f077-158">You'll need to add a `using` statement at the top of your `Main` method so that the C# compiler recognizes the <xref:System.Threading.Tasks.Task> type:</span></span>

```csharp
using System.Threading.Tasks;
```

<span data-ttu-id="8f077-159">Projenizi bu noktada oluşturursanız, hiçbir `await` işleci içermediğinden ve zaman uyumlu olarak çalışacağı için bu yöntem için bir uyarı alırsınız.</span><span class="sxs-lookup"><span data-stu-id="8f077-159">If you build your project at this point, you'll get a warning generated for this method, because it does not contain any `await` operators and will run synchronously.</span></span> <span data-ttu-id="8f077-160">Şimdilik bunu yoksayın; yöntemi doldurduktan sonra `await` işleçleri ekleyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="8f077-160">Ignore that for now; you'll add `await` operators as you fill in the method.</span></span>

<span data-ttu-id="8f077-161">Sonra, `namespace` deyiminizde tanımlanan ad alanını `ConsoleApp` varsayılan olan `WebAPIClient`olarak yeniden adlandırın.</span><span class="sxs-lookup"><span data-stu-id="8f077-161">Next, rename the namespace defined in the `namespace` statement from its default of `ConsoleApp` to `WebAPIClient`.</span></span> <span data-ttu-id="8f077-162">Daha sonra bu ad alanında bir `repo` sınıfı tanımlayacağız.</span><span class="sxs-lookup"><span data-stu-id="8f077-162">We'll later define a `repo` class in this namespace.</span></span>

<span data-ttu-id="8f077-163">Sonra, bu yöntemi çağırmak için `Main` yöntemini güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="8f077-163">Next, update the `Main` method to call this method.</span></span> <span data-ttu-id="8f077-164">`ProcessRepositories` yöntemi bir görevi döndürür ve bu görev tamamlanmadan önce programdan çıkmamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="8f077-164">The `ProcessRepositories` method returns a Task, and you shouldn't exit the program before that task finishes.</span></span> <span data-ttu-id="8f077-165">Bu nedenle, `Main`imzasını değiştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="8f077-165">Therefore, you must change the signature of `Main`.</span></span> <span data-ttu-id="8f077-166">`async` değiştiricisini ekleyin ve dönüş türünü `Task`olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="8f077-166">Add the `async` modifier, and change the return type to `Task`.</span></span> <span data-ttu-id="8f077-167">Ardından, yönteminin gövdesinde `ProcessRepositories`bir çağrı ekleyin.</span><span class="sxs-lookup"><span data-stu-id="8f077-167">Then, in the body of the method, add a call to `ProcessRepositories`.</span></span> <span data-ttu-id="8f077-168">Bu yöntem çağrısında `await` anahtar sözcüğünü ekleyin:</span><span class="sxs-lookup"><span data-stu-id="8f077-168">Add the `await` keyword when to that method call:</span></span>

```csharp
static Task Main(string[] args)
{
    await ProcessRepositories();
}
```

<span data-ttu-id="8f077-169">Artık hiçbir şey yapmaz ancak zaman uyumsuz olarak bunu yapar.</span><span class="sxs-lookup"><span data-stu-id="8f077-169">Now, you have a program that does nothing, but does it asynchronously.</span></span> <span data-ttu-id="8f077-170">Bunu geliştirelim.</span><span class="sxs-lookup"><span data-stu-id="8f077-170">Let's improve it.</span></span>

<span data-ttu-id="8f077-171">Önce, Web 'den veri alan bir nesne gerekir; Bunu yapmak için bir <xref:System.Net.Http.HttpClient> kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8f077-171">First you need an object that is capable to retrieve data from the web; you can use a <xref:System.Net.Http.HttpClient> to do that.</span></span> <span data-ttu-id="8f077-172">Bu nesne, isteği ve yanıtları işler.</span><span class="sxs-lookup"><span data-stu-id="8f077-172">This object handles the request and the responses.</span></span> <span data-ttu-id="8f077-173">Program.cs dosyasının içindeki `Program` sınıfında bu türün tek bir örneğini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="8f077-173">Instantiate a single instance of that type in the `Program` class inside the Program.cs file.</span></span>

```csharp
namespace WebAPIClient
{
    class Program
    {
        private static readonly HttpClient client = new HttpClient();

        static Task Main(string[] args)
        {
            //...
        }
    }
}
```

<span data-ttu-id="8f077-174">`ProcessRepositories` yöntemine geri dönüp bir ilk sürümü dolduralım:</span><span class="sxs-lookup"><span data-stu-id="8f077-174">Let's go back to the `ProcessRepositories` method and fill in a first version of it:</span></span>

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

<span data-ttu-id="8f077-175">Bunun derlenmesi için dosyanın en üstüne iki yeni using deyimi de eklemeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="8f077-175">You'll need to also add two new using statements at the top of the file for this to compile:</span></span>

```csharp
using System.Net.Http;
using System.Net.Http.Headers;
```

<span data-ttu-id="8f077-176">Bu ilk sürüm, DotNet Foundation kuruluşundaki tüm depoların listesini okumak için bir Web isteği oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8f077-176">This first version makes a web request to read the list of all repositories under the dotnet foundation organization.</span></span> <span data-ttu-id="8f077-177">(.NET Foundation için gitHub KIMLIĞI ' DotNet ').</span><span class="sxs-lookup"><span data-stu-id="8f077-177">(The gitHub ID for the .NET Foundation is 'dotnet').</span></span> <span data-ttu-id="8f077-178">İlk birkaç satır bu istek için <xref:System.Net.Http.HttpClient> ayarlar.</span><span class="sxs-lookup"><span data-stu-id="8f077-178">The first few lines set up the <xref:System.Net.Http.HttpClient> for this request.</span></span> <span data-ttu-id="8f077-179">İlk olarak, GitHub JSON yanıtlarını kabul edecek şekilde yapılandırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="8f077-179">First, it is configured to accept the GitHub JSON responses.</span></span>
<span data-ttu-id="8f077-180">Bu biçim yalnızca JSON 'dir.</span><span class="sxs-lookup"><span data-stu-id="8f077-180">This format is simply JSON.</span></span> <span data-ttu-id="8f077-181">Sonraki satır, bu nesneden gelen tüm isteklere bir Kullanıcı Aracısı üst bilgisi ekler.</span><span class="sxs-lookup"><span data-stu-id="8f077-181">The next line adds a User Agent header to all requests from this object.</span></span> <span data-ttu-id="8f077-182">Bu iki üst bilgi GitHub sunucusu kodu tarafından denetlenir ve GitHub 'dan bilgi almak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="8f077-182">These two headers are checked by the GitHub server code, and are necessary to retrieve information from GitHub.</span></span>

<span data-ttu-id="8f077-183"><xref:System.Net.Http.HttpClient>yapılandırdıktan sonra, bir Web isteği yapar ve yanıtı alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8f077-183">After you've configured the <xref:System.Net.Http.HttpClient>, you make a web request and retrieve the response.</span></span> <span data-ttu-id="8f077-184">Bu ilk sürümde <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)?displayProperty=nameWithType> kullanışlı yöntemini kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="8f077-184">In this first version, you use the <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)?displayProperty=nameWithType> convenience method.</span></span> <span data-ttu-id="8f077-185">Bu kolaylık yöntemi, web isteğini yapan bir görevi başlatır ve ardından istek döndürüldüğünde yanıt akışını okur ve içeriği akıştan ayıklar.</span><span class="sxs-lookup"><span data-stu-id="8f077-185">This convenience method starts a task that makes the web request, and then when the request returns, it reads the response stream and extracts the content from the stream.</span></span> <span data-ttu-id="8f077-186">Yanıtın gövdesi bir <xref:System.String>olarak döndürülür.</span><span class="sxs-lookup"><span data-stu-id="8f077-186">The body of the response is returned as a <xref:System.String>.</span></span> <span data-ttu-id="8f077-187">Dize, görev tamamlandığında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="8f077-187">The string is available when the task completes.</span></span>

<span data-ttu-id="8f077-188">Bu yöntemin son iki satırı bu görevi bekler ve ardından yanıtı konsola yazdırır.</span><span class="sxs-lookup"><span data-stu-id="8f077-188">The final two lines of this method await that task, and then print the response to the console.</span></span>
<span data-ttu-id="8f077-189">Uygulamayı derleyin ve çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="8f077-189">Build the app, and run it.</span></span> <span data-ttu-id="8f077-190">Artık `ProcessRepositories` bir `await` işleci içerdiğinden, derleme uyarısı şimdi çıktı.</span><span class="sxs-lookup"><span data-stu-id="8f077-190">The build warning is gone now, because the `ProcessRepositories` now does contain an `await` operator.</span></span> <span data-ttu-id="8f077-191">JSON biçimli metnin uzun bir görüntüsünü görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="8f077-191">You'll see a long display of JSON formatted text.</span></span>

## <a name="processing-the-json-result"></a><span data-ttu-id="8f077-192">JSON sonucunu işleme</span><span class="sxs-lookup"><span data-stu-id="8f077-192">Processing the JSON Result</span></span>

<span data-ttu-id="8f077-193">Bu noktada, bir Web sunucusundan yanıt almak için kodu yazmış ve bu yanıtta bulunan metni görüntüdiniz.</span><span class="sxs-lookup"><span data-stu-id="8f077-193">At this point, you've written the code to retrieve a response from a web server, and display the text that is contained in that response.</span></span> <span data-ttu-id="8f077-194">Sonra, bu JSON yanıtını C# nesnelere dönüştürelim.</span><span class="sxs-lookup"><span data-stu-id="8f077-194">Next, let's convert that JSON response into C# objects.</span></span>

<span data-ttu-id="8f077-195"><xref:System.Text.Json.JsonSerializer?displayProperty=nameWithType> sınıfı, nesneleri JSON 'a seri hale getirir ve JSON nesnelerini nesnelere yeniden ayırır.</span><span class="sxs-lookup"><span data-stu-id="8f077-195">The <xref:System.Text.Json.JsonSerializer?displayProperty=nameWithType> class serializes objects to JSON and deserializes JSON into objects.</span></span> <span data-ttu-id="8f077-196">GitHub API 'sinden döndürülen `repo` JSON nesnesini temsil eden bir sınıf tanımlayarak başlayın:</span><span class="sxs-lookup"><span data-stu-id="8f077-196">Start by defining a class to represent the `repo` JSON object returned from the GitHub API:</span></span>

```csharp
using System;

namespace WebAPIClient
{
    public class Repository
    {
        public string name { get; set; };
    }
}
```

<span data-ttu-id="8f077-197">Yukarıdaki kodu ' repo. cs ' adlı yeni bir dosyaya yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="8f077-197">Put the above code in a new file called 'repo.cs'.</span></span> <span data-ttu-id="8f077-198">Sınıfının bu sürümü JSON verilerini işlemek için en basit yolu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="8f077-198">This version of the class represents the simplest path to process JSON data.</span></span> <span data-ttu-id="8f077-199">Sınıf adı ve üye adı, aşağıdaki C# kurallar yerine JSON paketinde kullanılan adlarla eşleşir.</span><span class="sxs-lookup"><span data-stu-id="8f077-199">The class name and the member name match the names used in the JSON packet, instead of following C# conventions.</span></span> <span data-ttu-id="8f077-200">Daha sonra bazı yapılandırma öznitelikleri sağlayarak bunu düzeltireceksiniz.</span><span class="sxs-lookup"><span data-stu-id="8f077-200">You'll fix that by providing some configuration attributes later.</span></span> <span data-ttu-id="8f077-201">Bu sınıf, JSON serileştirme ve seri durumdan çıkarma için başka bir önemli özellik gösterir: JSON paketindeki tüm alanlar bu sınıfın bir parçası değil.</span><span class="sxs-lookup"><span data-stu-id="8f077-201">This class demonstrates another important feature of JSON serialization and deserialization: Not all the fields in the JSON packet are part of this class.</span></span>
<span data-ttu-id="8f077-202">JSON seri hale getiricisi, kullanılmakta olan sınıf türünde bulunmayan bilgileri yoksayacaktır.</span><span class="sxs-lookup"><span data-stu-id="8f077-202">The JSON serializer will ignore information that is not included in the class type being used.</span></span>
<span data-ttu-id="8f077-203">Bu özellik, JSON paketindeki alanların yalnızca bir alt kümesiyle çalışan türler oluşturmayı kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="8f077-203">This feature makes it easier to create types that work with only a subset of the fields in the JSON packet.</span></span>

<span data-ttu-id="8f077-204">Türü oluşturduğunuza göre, artık bunu serisini çıkaralım.</span><span class="sxs-lookup"><span data-stu-id="8f077-204">Now that you've created the type, let's deserialize it.</span></span> 

<span data-ttu-id="8f077-205">Ardından, JSON 'ı C# nesnelere dönüştürmek için seri hale getirici 'yi kullanacaksınız.</span><span class="sxs-lookup"><span data-stu-id="8f077-205">Next, you'll use the serializer to convert JSON into C# objects.</span></span> <span data-ttu-id="8f077-206">`ProcessRepositories` yönteminizin <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)> çağrısını aşağıdaki üç satır ile değiştirin:</span><span class="sxs-lookup"><span data-stu-id="8f077-206">Replace the call to <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)> in your `ProcessRepositories` method with the following three lines:</span></span>

```csharp
var streamTask = client.GetStreamAsync("https://api.github.com/orgs/dotnet/repos");
var repositories = await JsonSerializer.DeserializeAsync<List<Repository>>(await streamTask);
return repositories;
```

<span data-ttu-id="8f077-207">Yeni bir ad alanı kullanıyorsunuz, bu yüzden dosyanın en üstüne de eklemeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="8f077-207">You're using a new namespace, so you'll need to add it at the top of the file as well:</span></span>

```csharp
using System.Text.Json;
```

<span data-ttu-id="8f077-208">Artık <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)>yerine <xref:System.Net.Http.HttpClient.GetStreamAsync(System.String)> kullandığınızı fark edersiniz.</span><span class="sxs-lookup"><span data-stu-id="8f077-208">Notice that you're now using <xref:System.Net.Http.HttpClient.GetStreamAsync(System.String)> instead of <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)>.</span></span> <span data-ttu-id="8f077-209">Serileştirici, kaynağı olarak bir dize yerine bir akış kullanır.</span><span class="sxs-lookup"><span data-stu-id="8f077-209">The serializer uses a stream instead of a string as its source.</span></span> <span data-ttu-id="8f077-210">Önceki kod parçacığının ikinci satırında kullanılmakta olan C# dilin birkaç özelliğini açıklayalim.</span><span class="sxs-lookup"><span data-stu-id="8f077-210">Let's explain a couple features of the C# language that are being used in the second line of the preceding code snippet.</span></span> <span data-ttu-id="8f077-211"><xref:System.Text.Json.JsonSerializer.DeserializeAsync%60%601(System.IO.Stream,System.Text.Json.JsonSerializerOptions,System.Threading.CancellationToken)?displayProperty=nameWithType> ilk bağımsız değişkeni `await` bir ifadedir.</span><span class="sxs-lookup"><span data-stu-id="8f077-211">The first argument to <xref:System.Text.Json.JsonSerializer.DeserializeAsync%60%601(System.IO.Stream,System.Text.Json.JsonSerializerOptions,System.Threading.CancellationToken)?displayProperty=nameWithType> is an `await` expression.</span></span> <span data-ttu-id="8f077-212">(Diğer iki parametre isteğe bağlıdır ve kod parçacığında atlanır.) Await ifadeleri kodunuzda neredeyse her yerde görünebilir, ancak şu anda yalnızca bir atama bildiriminin parçası olarak gördünüz.</span><span class="sxs-lookup"><span data-stu-id="8f077-212">(The other two parameters are optional and are omitted in the code snippet.) Await expressions can appear almost anywhere in your code, even though up to now, you've only seen them as part of an assignment statement.</span></span> <span data-ttu-id="8f077-213">`Deserialize` yöntemi *geneldir*, yani JSON metninde ne tür nesneler oluşturulması gerektiği için tür bağımsız değişkenleri sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="8f077-213">The `Deserialize` method is *generic*, which means you must supply type arguments for what kind of objects should be created from the JSON text.</span></span> <span data-ttu-id="8f077-214">Bu örnekte, <xref:System.Collections.Generic.List%601?displayProperty=nameWithType>başka bir genel nesne olan `List<Repository>`serisini kaldırma işlemi yaptığınız anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="8f077-214">In this example, you're deserializing to a `List<Repository>`, which is another generic object, the <xref:System.Collections.Generic.List%601?displayProperty=nameWithType>.</span></span> <span data-ttu-id="8f077-215">`List<>` sınıfı bir nesne koleksiyonunu depolar.</span><span class="sxs-lookup"><span data-stu-id="8f077-215">The `List<>` class stores a collection of objects.</span></span> <span data-ttu-id="8f077-216">Tür bağımsız değişkeni, `List<>`depolanan nesne türlerini bildirir.</span><span class="sxs-lookup"><span data-stu-id="8f077-216">The type argument declares the type of objects stored in the `List<>`.</span></span> <span data-ttu-id="8f077-217">JSON metni, depo nesnelerinin bir koleksiyonunu temsil eder, bu nedenle tür bağımsız değişkeni `Repository`.</span><span class="sxs-lookup"><span data-stu-id="8f077-217">The JSON text represents a collection of repo objects, so the type argument is `Repository`.</span></span>

<span data-ttu-id="8f077-218">Bu bölümde neredeyse işiniz bitti.</span><span class="sxs-lookup"><span data-stu-id="8f077-218">You're almost done with this section.</span></span> <span data-ttu-id="8f077-219">JSON 'ı C# nesnelere dönüştürdüğüne göre, her deponun adını görüntülim.</span><span class="sxs-lookup"><span data-stu-id="8f077-219">Now that you've converted the JSON to C# objects, let's display the name of each repository.</span></span> <span data-ttu-id="8f077-220">Okunan satırları değiştirin:</span><span class="sxs-lookup"><span data-stu-id="8f077-220">Replace the lines that read:</span></span>

```csharp
var msg = await stringTask;   //**Deleted this
Console.Write(msg);
```

<span data-ttu-id="8f077-221">aşağıdakiler ile:</span><span class="sxs-lookup"><span data-stu-id="8f077-221">with the following:</span></span>

```csharp
foreach (var repo in repositories)
    Console.WriteLine(repo.name);
```

<span data-ttu-id="8f077-222">Uygulamayı derleyin ve çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="8f077-222">Compile and run the application.</span></span> <span data-ttu-id="8f077-223">.NET Foundation 'ın parçası olan Depoların adlarını yazdıracaktır.</span><span class="sxs-lookup"><span data-stu-id="8f077-223">It will print out the names of the repositories that are part of the .NET Foundation.</span></span>

## <a name="controlling-serialization"></a><span data-ttu-id="8f077-224">Serileştirme denetleniyor</span><span class="sxs-lookup"><span data-stu-id="8f077-224">Controlling Serialization</span></span>

<span data-ttu-id="8f077-225">Daha fazla özellik eklemeden önce `[JsonPropertyName]` özniteliğini kullanarak `name` özelliğini ele alalım.</span><span class="sxs-lookup"><span data-stu-id="8f077-225">Before you add more features, let's address the `name` property by using the `[JsonPropertyName]` attribute.</span></span> <span data-ttu-id="8f077-226">Repo.cs içinde `name` alanının bildiriminde aşağıdaki değişiklikleri yapın:</span><span class="sxs-lookup"><span data-stu-id="8f077-226">Make the following changes to the declaration of the `name` field in repo.cs:</span></span>

```csharp
[JsonPropertyName("name")]
public string Name { get; set; }
```

<span data-ttu-id="8f077-227">Bu değişiklik, program.cs içindeki her deponun adını yazan kodu değiştirmeniz gereken anlamına gelir:</span><span class="sxs-lookup"><span data-stu-id="8f077-227">This change means you need to change the code that writes the name of each repository in program.cs:</span></span>

```csharp
Console.WriteLine(repo.Name);
```

<span data-ttu-id="8f077-228">Eşlemelerinizin doğru olduğundan emin olmak için `dotnet run` yürütün.</span><span class="sxs-lookup"><span data-stu-id="8f077-228">Execute `dotnet run` to make sure you've got the mappings correct.</span></span> <span data-ttu-id="8f077-229">Önceki ile aynı çıktıyı görmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="8f077-229">You should see the same output as before.</span></span>

<span data-ttu-id="8f077-230">Yeni özellikler eklemeden önce bir değişiklik yapalim.</span><span class="sxs-lookup"><span data-stu-id="8f077-230">Let's make one more change before adding new features.</span></span> <span data-ttu-id="8f077-231">`ProcessRepositories` yöntemi zaman uyumsuz çalışmayı yapabilir ve depoların bir koleksiyonunu döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="8f077-231">The `ProcessRepositories` method can do the async work and return a collection of the repositories.</span></span> <span data-ttu-id="8f077-232">Bu yöntemden `List<Repository>` dönelim ve bilgileri yazan kodu `Main` yöntemine taşıyalim.</span><span class="sxs-lookup"><span data-stu-id="8f077-232">Let's return the `List<Repository>` from that method, and move the code that writes the information into the `Main` method.</span></span>

<span data-ttu-id="8f077-233">`ProcessRepositories` imzasını, sonucu bir `Repository` nesneleri listesi olan bir görevi döndürecek şekilde değiştirin:</span><span class="sxs-lookup"><span data-stu-id="8f077-233">Change the signature of `ProcessRepositories` to return a task whose result is a list of `Repository` objects:</span></span>

```csharp
private static async Task<List<Repository>> ProcessRepositories()
```

<span data-ttu-id="8f077-234">Ardından, JSON yanıtını işledikten sonra depoları geri döndürün:</span><span class="sxs-lookup"><span data-stu-id="8f077-234">Then, just return the repositories after processing the JSON response:</span></span>

```csharp
var repositories = serializer.ReadObject(await streamTask) as List<Repository>;
return repositories;
```

<span data-ttu-id="8f077-235">Bu yöntemi `async`olarak işaretlediğiniz için derleyici, return için `Task<T>` nesnesini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8f077-235">The compiler generates the `Task<T>` object for the return because you've marked this method as `async`.</span></span>
<span data-ttu-id="8f077-236">Sonra, `Main` yöntemini bu sonuçları yakalayıp, her depo adını konsola yazar şekilde değiştirelim.</span><span class="sxs-lookup"><span data-stu-id="8f077-236">Then, let's modify the `Main` method so that it captures those results and writes each repository name to the console.</span></span> <span data-ttu-id="8f077-237">`Main` yönteminiz şu şekilde görünür:</span><span class="sxs-lookup"><span data-stu-id="8f077-237">Your `Main` method now looks like this:</span></span>

```csharp
public static Task Main(string[] args)
{
    var repositories = await ProcessRepositories();

    foreach (var repo in repositories)
        Console.WriteLine(repo.Name);
}
```

## <a name="reading-more-information"></a><span data-ttu-id="8f077-238">Daha fazla bilgi okunuyor</span><span class="sxs-lookup"><span data-stu-id="8f077-238">Reading More Information</span></span>

<span data-ttu-id="8f077-239">Bu işlemi, GitHub API 'sinden gönderilen JSON paketindeki özelliklerden daha fazlasını işleyerek tamamlayalim.</span><span class="sxs-lookup"><span data-stu-id="8f077-239">Let's finish this by processing a few more of the properties in the JSON packet that gets sent from the GitHub API.</span></span> <span data-ttu-id="8f077-240">Her şeyi almak istemezsiniz, ancak birkaç özelliği eklemek C# dilin birkaç özelliğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="8f077-240">You won't want to grab everything, but adding a few properties will demonstrate a few more features of the C# language.</span></span>

<span data-ttu-id="8f077-241">`Repository` sınıf tanımına birkaç basit tür ekleyerek başlayalım.</span><span class="sxs-lookup"><span data-stu-id="8f077-241">Let's start by adding a few more simple types to the `Repository` class definition.</span></span> <span data-ttu-id="8f077-242">Bu özellikleri bu sınıfa ekleyin:</span><span class="sxs-lookup"><span data-stu-id="8f077-242">Add these properties to that class:</span></span>

```csharp
[JsonPropertyName(Name="description")]
public string Description { get; set; }

[JsonPropertyName(Name="html_url")]
public Uri GitHubHomeUrl { get; set; }

[JsonPropertyName(Name="homepage")]
public Uri Homepage { get; set; }

[JsonPropertyName(Name="watchers")]
public int Watchers { get; set; }
```

<span data-ttu-id="8f077-243">Bu özellikler dize türünden (JSON paketlerinin içerdiği), hedef türüne yerleşik Dönüştürmelere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="8f077-243">These properties have built-in conversions from the string type (which is what the JSON packets contain) to the target type.</span></span> <span data-ttu-id="8f077-244"><xref:System.Uri> türü sizin için yeni olabilir.</span><span class="sxs-lookup"><span data-stu-id="8f077-244">The <xref:System.Uri> type may be new to you.</span></span> <span data-ttu-id="8f077-245">Bir URI 'yi veya bu durumda bir URL 'yi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="8f077-245">It represents a URI, or in this case, a URL.</span></span> <span data-ttu-id="8f077-246">`Uri` ve `int` türlerinde, JSON paketi hedef türüne Dönüştürülmeyen veriler içeriyorsa, serileştirme eylemi bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8f077-246">In the case of the `Uri` and `int` types, if the JSON packet contains data that does not convert to the target type, the serialization action will throw an exception.</span></span>

<span data-ttu-id="8f077-247">Bunları ekledikten sonra, bu öğeleri göstermek için `Main` yöntemini güncelleştirin:</span><span class="sxs-lookup"><span data-stu-id="8f077-247">Once you've added these, update the `Main` method to display those elements:</span></span>

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

<span data-ttu-id="8f077-248">Son bir adım olarak, son gönderme işlemi için bilgileri ekleyelim.</span><span class="sxs-lookup"><span data-stu-id="8f077-248">As a final step, let's add the information for the last push operation.</span></span> <span data-ttu-id="8f077-249">Bu bilgiler, JSON yanıtında bu biçimde biçimlendirilir:</span><span class="sxs-lookup"><span data-stu-id="8f077-249">This information is formatted in this fashion in the JSON response:</span></span>

```json
2016-02-08T21:27:00Z
```

<span data-ttu-id="8f077-250">Bu biçim standart .NET <xref:System.DateTime> biçimlerinden hiçbirini izlemez.</span><span class="sxs-lookup"><span data-stu-id="8f077-250">That format does not follow any of the standard .NET <xref:System.DateTime> formats.</span></span> <span data-ttu-id="8f077-251">Bu nedenle, özel bir dönüştürme yöntemi yazmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="8f077-251">Because of that, you'll need to write a custom conversion method.</span></span> <span data-ttu-id="8f077-252">Ham dizenin `Repository` sınıfının kullanıcılarına sunulamayada istemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="8f077-252">You also probably don't want the raw string exposed to users of the `Repository` class.</span></span> <span data-ttu-id="8f077-253">Öznitelikleri, bu da denetim sağlanmasına yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="8f077-253">Attributes can help control that as well.</span></span> <span data-ttu-id="8f077-254">İlk olarak, `Repository` sınıfınıza tarih ve saatin dize gösterimini ve döndürülen tarihi temsil eden biçimli bir dize döndüren bir `LastPush` `readonly` özelliğini tutan bir `public` özelliği tanımlayın:</span><span class="sxs-lookup"><span data-stu-id="8f077-254">First, define a `public` property that will hold the string representation of the date and time in your `Repository` class and a `LastPush` `readonly` property that returns a formatted string that represents the returned date:</span></span>

```csharp
[JsonPropertyName(Name="pushed_at")]
public string JsonDate { get; set; }

public DateTime LastPush =>
    DateTime.ParseExact(JsonDate, "yyyy-MM-ddTHH:mm:ssZ", CultureInfo.InvariantCulture);
```

<span data-ttu-id="8f077-255">Şimdi tanımladığımız yeni yapıları inceleyelim.</span><span class="sxs-lookup"><span data-stu-id="8f077-255">Let's go over the new constructs we just defined.</span></span> <span data-ttu-id="8f077-256">`LastPush` özelliği, `get` erişimcisi için *ifade-Bodied üyesi* kullanılarak tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="8f077-256">The `LastPush` property is defined using an *expression-bodied member* for the `get` accessor.</span></span> <span data-ttu-id="8f077-257">`set` erişimcisi yok.</span><span class="sxs-lookup"><span data-stu-id="8f077-257">There is no `set` accessor.</span></span> <span data-ttu-id="8f077-258">`set` erişimcinin atlanması, içinde C# *salt okunurdur* bir özelliği nasıl tanımlayacağınızı belirler.</span><span class="sxs-lookup"><span data-stu-id="8f077-258">Omitting the `set` accessor is how you define a *read-only* property in C#.</span></span> <span data-ttu-id="8f077-259">(Evet, öğesinde C# *salt yazılır* özellikler oluşturabilirsiniz, ancak değerleri sınırlıdır.) <xref:System.DateTime.ParseExact(System.String,System.String,System.IFormatProvider)> yöntemi bir dizeyi ayrıştırır ve sağlanmış bir tarih biçimi kullanarak bir <xref:System.DateTime> nesnesi oluşturur ve bir `CultureInfo` nesnesi kullanarak `DateTime` ek meta veri ekler.</span><span class="sxs-lookup"><span data-stu-id="8f077-259">(Yes, you can create *write-only* properties in C#, but their value is limited.) The <xref:System.DateTime.ParseExact(System.String,System.String,System.IFormatProvider)> method parses a string and creates a <xref:System.DateTime> object using a provided date format, and adds additional metadata to the `DateTime` using a `CultureInfo` object.</span></span> <span data-ttu-id="8f077-260">Ayrıştırma işlemi başarısız olursa, özellik erişimcisi bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8f077-260">If the parse operation fails, the property accessor throws an exception.</span></span>

<span data-ttu-id="8f077-261"><xref:System.Globalization.CultureInfo.InvariantCulture>kullanmak için, `repo.cs`içindeki `using` deyimlerine <xref:System.Globalization> ad alanı eklemeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="8f077-261">To use <xref:System.Globalization.CultureInfo.InvariantCulture>, you will need to add the <xref:System.Globalization> namespace to the `using` statements in `repo.cs`:</span></span>

```csharp
using System.Globalization;
```

<span data-ttu-id="8f077-262">Son olarak, konsolda bir çıkış bildirisi daha ekleyin ve bu uygulamayı yeniden oluşturup çalıştırmak için hazırsınız:</span><span class="sxs-lookup"><span data-stu-id="8f077-262">Finally, add one more output statement in the console, and you're ready to build and run this app again:</span></span>

```csharp
Console.WriteLine(repo.LastPush);
```

<span data-ttu-id="8f077-263">Sürümünüz artık [tamamlanmış örnekle](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient)eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="8f077-263">Your version should now match the [finished sample](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient).</span></span>

## <a name="conclusion"></a><span data-ttu-id="8f077-264">Sonuç</span><span class="sxs-lookup"><span data-stu-id="8f077-264">Conclusion</span></span>

<span data-ttu-id="8f077-265">Bu öğretici, Web istekleri oluşturma, sonucu ayrıştırma ve bu sonuçların özelliklerini görüntüleme konusunda sizi gösterdi.</span><span class="sxs-lookup"><span data-stu-id="8f077-265">This tutorial showed you how to make web requests, parse the result, and display properties of those results.</span></span> <span data-ttu-id="8f077-266">Ayrıca, yeni paketleri projenize bağımlılıklar olarak eklediniz.</span><span class="sxs-lookup"><span data-stu-id="8f077-266">You've also added new packages as dependencies in your project.</span></span> <span data-ttu-id="8f077-267">Nesne odaklı teknikleri destekleyen C# dilin bazı özelliklerini gördünüz.</span><span class="sxs-lookup"><span data-stu-id="8f077-267">You've seen some of the features of the C# language that support object-oriented techniques.</span></span>

<a name="dotnet-restore-note"></a>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
