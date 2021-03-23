---
title: .NET Core kullanarak REST istemcisi oluşturma
description: Bu öğreticide, .NET Core ve C# dilinde bazı özellikler öğretilir.
ms.date: 01/09/2020
ms.assetid: 51033ce2-7a53-4cdd-966d-9da15c8204d2
ms.openlocfilehash: 4d36cdafd232de9bbd0fac12e894f905b4808419
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/23/2021
ms.locfileid: "104876155"
---
# <a name="rest-client"></a><span data-ttu-id="fc1c5-103">REST istemcisi</span><span class="sxs-lookup"><span data-stu-id="fc1c5-103">REST client</span></span>

<span data-ttu-id="fc1c5-104">Bu öğretici, .NET Core ve C# dilinde birçok özellik öğretir.</span><span class="sxs-lookup"><span data-stu-id="fc1c5-104">This tutorial teaches you a number of features in .NET Core and the C# language.</span></span> <span data-ttu-id="fc1c5-105">Şunları öğreneceksiniz:</span><span class="sxs-lookup"><span data-stu-id="fc1c5-105">You'll learn:</span></span>

* <span data-ttu-id="fc1c5-106">.NET Core CLI temel kavramları.</span><span class="sxs-lookup"><span data-stu-id="fc1c5-106">The basics of the .NET Core CLI.</span></span>
* <span data-ttu-id="fc1c5-107">C# dil özelliklerine genel bakış.</span><span class="sxs-lookup"><span data-stu-id="fc1c5-107">An overview of C# Language features.</span></span>
* <span data-ttu-id="fc1c5-108">NuGet ile bağımlılıkları yönetme</span><span class="sxs-lookup"><span data-stu-id="fc1c5-108">Managing dependencies with NuGet</span></span>
* <span data-ttu-id="fc1c5-109">HTTP Iletişimleri</span><span class="sxs-lookup"><span data-stu-id="fc1c5-109">HTTP Communications</span></span>
* <span data-ttu-id="fc1c5-110">JSON bilgilerini işleme</span><span class="sxs-lookup"><span data-stu-id="fc1c5-110">Processing JSON information</span></span>
* <span data-ttu-id="fc1c5-111">Yapılandırmayı özniteliklerle yönetme.</span><span class="sxs-lookup"><span data-stu-id="fc1c5-111">Managing configuration with Attributes.</span></span>

<span data-ttu-id="fc1c5-112">GitHub 'da REST hizmetine HTTP Istekleri veren bir uygulama oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="fc1c5-112">You'll build an application that issues HTTP Requests to a REST service on GitHub.</span></span> <span data-ttu-id="fc1c5-113">JSON biçiminde bilgileri okur ve bu JSON paketini C# nesnelerine dönüştürürsünüz.</span><span class="sxs-lookup"><span data-stu-id="fc1c5-113">You'll read information in JSON format, and convert that JSON packet into C# objects.</span></span> <span data-ttu-id="fc1c5-114">Son olarak C# nesneleriyle nasıl çalışacaksınız görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="fc1c5-114">Finally, you'll see how to work with C# objects.</span></span>

<span data-ttu-id="fc1c5-115">Bu öğreticide birçok özellik vardır.</span><span class="sxs-lookup"><span data-stu-id="fc1c5-115">There are many features in this tutorial.</span></span> <span data-ttu-id="fc1c5-116">Bunları birer birer oluşturalım.</span><span class="sxs-lookup"><span data-stu-id="fc1c5-116">Let's build them one by one.</span></span>

<span data-ttu-id="fc1c5-117">Bu makaleye yönelik [son örnekle](https://github.com/dotnet/samples/tree/main/csharp/getting-started/console-webapiclient) birlikte izlemeyi tercih ediyorsanız, indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fc1c5-117">If you prefer to follow along with the [final sample](https://github.com/dotnet/samples/tree/main/csharp/getting-started/console-webapiclient) for this article, you can download it.</span></span> <span data-ttu-id="fc1c5-118">İndirme yönergeleri için bkz. [örnekler ve öğreticiler](../../samples-and-tutorials/index.md#view-and-download-samples).</span><span class="sxs-lookup"><span data-stu-id="fc1c5-118">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#view-and-download-samples).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="fc1c5-119">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="fc1c5-119">Prerequisites</span></span>

<span data-ttu-id="fc1c5-120">Makinenizi .NET Core çalıştıracak şekilde ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="fc1c5-120">You'll need to set up your machine to run .NET core.</span></span> <span data-ttu-id="fc1c5-121">Yükleme yönergelerini [.NET Core İndirmeleri](https://dotnet.microsoft.com/download) sayfasında bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fc1c5-121">You can find the installation instructions on the [.NET Core Downloads](https://dotnet.microsoft.com/download) page.</span></span> <span data-ttu-id="fc1c5-122">Bu uygulamayı Windows, Linux veya macOS üzerinde veya bir Docker kapsayıcısında çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fc1c5-122">You can run this application on Windows, Linux, or macOS, or in a Docker container.</span></span>
<span data-ttu-id="fc1c5-123">En sevdiğiniz kod düzenleyicinizi yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="fc1c5-123">You'll need to install your favorite code editor.</span></span> <span data-ttu-id="fc1c5-124">Aşağıdaki açıklamalar açık kaynaklı, platformlar arası bir düzenleyici olan [Visual Studio Code](https://code.visualstudio.com/)kullanır.</span><span class="sxs-lookup"><span data-stu-id="fc1c5-124">The descriptions below use [Visual Studio Code](https://code.visualstudio.com/), which is an open source, cross platform editor.</span></span> <span data-ttu-id="fc1c5-125">Bununla birlikte, rahat olan her türlü aracı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fc1c5-125">However, you can use whatever tools you are comfortable with.</span></span>

## <a name="create-the-application"></a><span data-ttu-id="fc1c5-126">Uygulamayı oluşturma</span><span class="sxs-lookup"><span data-stu-id="fc1c5-126">Create the Application</span></span>

<span data-ttu-id="fc1c5-127">İlk adım yeni bir uygulama oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="fc1c5-127">The first step is to create a new application.</span></span> <span data-ttu-id="fc1c5-128">Bir komut istemi açın ve uygulamanız için yeni bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="fc1c5-128">Open a command prompt and create a new directory for your application.</span></span> <span data-ttu-id="fc1c5-129">Geçerli dizini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="fc1c5-129">Make that the current directory.</span></span> <span data-ttu-id="fc1c5-130">Konsol penceresine aşağıdaki komutu girin:</span><span class="sxs-lookup"><span data-stu-id="fc1c5-130">Enter the following command in a console window:</span></span>

```dotnetcli
dotnet new console --name WebAPIClient
```

<span data-ttu-id="fc1c5-131">Bu, temel bir "Merhaba Dünya" uygulaması için başlangıç dosyalarını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="fc1c5-131">This creates the starter files for a basic "Hello World" application.</span></span> <span data-ttu-id="fc1c5-132">Proje adı "WebAPIClient" dir.</span><span class="sxs-lookup"><span data-stu-id="fc1c5-132">The project name is "WebAPIClient".</span></span> <span data-ttu-id="fc1c5-133">Bu yeni bir proje olduğundan, bağımlılıklardan hiçbiri yerinde değildir.</span><span class="sxs-lookup"><span data-stu-id="fc1c5-133">As this is a new project, none of the dependencies are in place.</span></span> <span data-ttu-id="fc1c5-134">İlk çalıştırma .NET Core Framework 'ü indirir, bir geliştirme sertifikası yükler ve eksik bağımlılıkları geri yüklemek için NuGet Paket Yöneticisi 'ni çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="fc1c5-134">The first run will download the .NET Core framework, install a development certificate, and run the NuGet package manager to restore missing dependencies.</span></span>

<span data-ttu-id="fc1c5-135">`cd`Uygulamanızı çalıştırmak için komut isteminde "WebAPIClient" dizinine ve yazın `dotnet run` ([bkz. Note](#dotnet-restore-note)).</span><span class="sxs-lookup"><span data-stu-id="fc1c5-135">Before you start making modifications, `cd` into the "WebAPIClient" directory and type `dotnet run` ([see note](#dotnet-restore-note)) at the command prompt to run your application.</span></span> <span data-ttu-id="fc1c5-136">`dotnet run``dotnet restore`ortamınızda bağımlılıklar eksik olursa otomatik olarak gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="fc1c5-136">`dotnet run` automatically performs `dotnet restore` if your environment is missing dependencies.</span></span> <span data-ttu-id="fc1c5-137">Uygulamanızın yeniden oluşturulması gerekiyorsa de çalışır `dotnet build` .</span><span class="sxs-lookup"><span data-stu-id="fc1c5-137">It also performs `dotnet build` if your application needs to be rebuilt.</span></span>
<span data-ttu-id="fc1c5-138">İlk kurulumdan sonra, yalnızca `dotnet restore` `dotnet build` projeniz için anlamlı olduğunda veya çalıştırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="fc1c5-138">After your initial setup, you will only need to run `dotnet restore` or `dotnet build` when it makes sense for your project.</span></span>

## <a name="adding-new-dependencies"></a><span data-ttu-id="fc1c5-139">Yeni bağımlılıklar ekleniyor</span><span class="sxs-lookup"><span data-stu-id="fc1c5-139">Adding New Dependencies</span></span>

<span data-ttu-id="fc1c5-140">.NET Core için önemli tasarım amaçlarından biri, .NET yüklemesinin boyutunu en aza indirmektir.</span><span class="sxs-lookup"><span data-stu-id="fc1c5-140">One of the key design goals for .NET Core is to minimize the size of the .NET installation.</span></span> <span data-ttu-id="fc1c5-141">Bir uygulamanın bazı özellikleri için ek kitaplıklar gerekiyorsa, bu bağımlılıkları C# projeniz ( \* . csproj) dosyanıza eklersiniz.</span><span class="sxs-lookup"><span data-stu-id="fc1c5-141">If an application needs additional libraries for some of its features, you add those dependencies into your C# project (\*.csproj) file.</span></span> <span data-ttu-id="fc1c5-142">Örneğimiz için, `System.Runtime.Serialization.Json` UYGULAMANıZıN JSON yanıtlarını işleyebilmesi için paketini eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="fc1c5-142">For our example, you'll need to add the `System.Runtime.Serialization.Json` package, so your application can process JSON responses.</span></span>

<span data-ttu-id="fc1c5-143">`System.Runtime.Serialization.Json`Bu uygulama için pakete ihtiyacınız olacak.</span><span class="sxs-lookup"><span data-stu-id="fc1c5-143">You'll need the `System.Runtime.Serialization.Json` package for this application.</span></span> <span data-ttu-id="fc1c5-144">Aşağıdaki [.net CLI](../../core/tools/dotnet-add-package.md) komutunu çalıştırarak projenize ekleyin:</span><span class="sxs-lookup"><span data-stu-id="fc1c5-144">Add it to your project by running the following [.NET CLI](../../core/tools/dotnet-add-package.md) command:</span></span>

```dotnetcli
dotnet add package System.Text.Json
```

## <a name="making-web-requests"></a><span data-ttu-id="fc1c5-145">Web Istekleri yapma</span><span class="sxs-lookup"><span data-stu-id="fc1c5-145">Making Web Requests</span></span>

<span data-ttu-id="fc1c5-146">Artık Web 'den veri almaya başlamaya hazırsınız.</span><span class="sxs-lookup"><span data-stu-id="fc1c5-146">Now you're ready to start retrieving data from the web.</span></span> <span data-ttu-id="fc1c5-147">Bu uygulamada, [GITHUB API](https://developer.github.com/v3/)'sindeki bilgileri okuyacaksınız.</span><span class="sxs-lookup"><span data-stu-id="fc1c5-147">In this application, you'll read information from the [GitHub API](https://developer.github.com/v3/).</span></span> <span data-ttu-id="fc1c5-148">[.Net Foundation](https://www.dotnetfoundation.org/) şemsiye kapsamındaki projelerle ilgili bilgileri okuyalim.</span><span class="sxs-lookup"><span data-stu-id="fc1c5-148">Let's read information about the projects under the [.NET Foundation](https://www.dotnetfoundation.org/) umbrella.</span></span> <span data-ttu-id="fc1c5-149">Projeler hakkındaki bilgileri almak için GitHub API 'sine istek yaparak başlayacaksınız.</span><span class="sxs-lookup"><span data-stu-id="fc1c5-149">You'll start by making the request to the GitHub API to retrieve information on the projects.</span></span> <span data-ttu-id="fc1c5-150">Kullanacağınız uç nokta: <https://api.github.com/orgs/dotnet/repos> .</span><span class="sxs-lookup"><span data-stu-id="fc1c5-150">The endpoint you'll use is: <https://api.github.com/orgs/dotnet/repos>.</span></span> <span data-ttu-id="fc1c5-151">Bu projelerle ilgili tüm bilgileri almak istiyorsunuz, bu nedenle bir HTTP GET isteği kullanacaksınız.</span><span class="sxs-lookup"><span data-stu-id="fc1c5-151">You want to retrieve all the information about these projects, so you'll use an HTTP GET request.</span></span>
<span data-ttu-id="fc1c5-152">Tarayıcınız ayrıca HTTP GET isteklerini kullanır; bu nedenle, hangi bilgileri almak ve işlemek istediğinizi görmek için bu URL 'YI tarayıcınıza yapıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fc1c5-152">Your browser also uses HTTP GET requests, so you can paste that URL into your browser to see what information you'll be receiving and processing.</span></span>

<span data-ttu-id="fc1c5-153"><xref:System.Net.Http.HttpClient>Web istekleri yapmak için sınıfını kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="fc1c5-153">You use the <xref:System.Net.Http.HttpClient> class to make web requests.</span></span> <span data-ttu-id="fc1c5-154">Tüm modern .NET API 'Lerinde olduğu gibi, <xref:System.Net.Http.HttpClient> uzun süre çalışan API 'ler için yalnızca zaman uyumsuz yöntemleri destekler.</span><span class="sxs-lookup"><span data-stu-id="fc1c5-154">Like all modern .NET APIs, <xref:System.Net.Http.HttpClient> supports only async methods for its long-running APIs.</span></span>
<span data-ttu-id="fc1c5-155">Zaman uyumsuz bir yöntem yaparak başlayın.</span><span class="sxs-lookup"><span data-stu-id="fc1c5-155">Start by making an async method.</span></span> <span data-ttu-id="fc1c5-156">Uygulamanın işlevlerini oluştururken uygulamayı doldurursunuz.</span><span class="sxs-lookup"><span data-stu-id="fc1c5-156">You'll fill in the implementation as you build the functionality of the application.</span></span> <span data-ttu-id="fc1c5-157">`program.cs`Dosyayı proje dizininizde açıp sınıfına aşağıdaki yöntemi ekleyerek başlayın `Program` :</span><span class="sxs-lookup"><span data-stu-id="fc1c5-157">Start by opening the `program.cs` file in your project directory and adding the following method to the `Program` class:</span></span>

```csharp
private static async Task ProcessRepositories()
{
}
```

<span data-ttu-id="fc1c5-158">`using` `Main` C# derleyicisinin türü tanıması için yönteminizin en üstüne bir yönerge eklemeniz gerekir <xref:System.Threading.Tasks.Task> :</span><span class="sxs-lookup"><span data-stu-id="fc1c5-158">You'll need to add a `using` directive at the top of your `Main` method so that the C# compiler recognizes the <xref:System.Threading.Tasks.Task> type:</span></span>

```csharp
using System.Threading.Tasks;
```

<span data-ttu-id="fc1c5-159">Bu noktada projenizi oluşturursanız, herhangi bir `await` işleç içermediğinden ve zaman uyumlu olarak çalışacağı için bu yöntem için bir uyarı alırsınız.</span><span class="sxs-lookup"><span data-stu-id="fc1c5-159">If you build your project at this point, you'll get a warning generated for this method, because it does not contain any `await` operators and will run synchronously.</span></span> <span data-ttu-id="fc1c5-160">Şimdilik bunu yoksayın; yöntemi doldurduktan sonra `await` işleçleri ekleyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="fc1c5-160">Ignore that for now; you'll add `await` operators as you fill in the method.</span></span>

<span data-ttu-id="fc1c5-161">Sonra, yöntemini `Main` çağırmak için yöntemini güncelleştirin `ProcessRepositories` .</span><span class="sxs-lookup"><span data-stu-id="fc1c5-161">Next, update the `Main` method to call the `ProcessRepositories` method.</span></span> <span data-ttu-id="fc1c5-162">`ProcessRepositories`Yöntemi bir görevi döndürür ve bu görev tamamlanmadan önce programdan çıkmamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="fc1c5-162">The `ProcessRepositories` method returns a task, and you shouldn't exit the program before that task finishes.</span></span> <span data-ttu-id="fc1c5-163">Bu nedenle, imzasını değiştirmeniz gerekir `Main` .</span><span class="sxs-lookup"><span data-stu-id="fc1c5-163">Therefore, you must change the signature of `Main`.</span></span> <span data-ttu-id="fc1c5-164">Değiştiricisini ekleyin `async` ve dönüş türünü olarak değiştirin `Task` .</span><span class="sxs-lookup"><span data-stu-id="fc1c5-164">Add the `async` modifier, and change the return type to `Task`.</span></span> <span data-ttu-id="fc1c5-165">Ardından, yönteminin gövdesinde öğesine bir çağrı ekleyin `ProcessRepositories` .</span><span class="sxs-lookup"><span data-stu-id="fc1c5-165">Then, in the body of the method, add a call to `ProcessRepositories`.</span></span> <span data-ttu-id="fc1c5-166">`await`Anahtar sözcüğünü bu yöntem çağrısına ekleyin:</span><span class="sxs-lookup"><span data-stu-id="fc1c5-166">Add the `await` keyword to that method call:</span></span>

```csharp
static async Task Main(string[] args)
{
    await ProcessRepositories();
}
```

<span data-ttu-id="fc1c5-167">Artık hiçbir şey yapmaz ancak zaman uyumsuz olarak bunu yapar.</span><span class="sxs-lookup"><span data-stu-id="fc1c5-167">Now, you have a program that does nothing, but does it asynchronously.</span></span> <span data-ttu-id="fc1c5-168">Bunu geliştirelim.</span><span class="sxs-lookup"><span data-stu-id="fc1c5-168">Let's improve it.</span></span>

<span data-ttu-id="fc1c5-169">Önce, Web 'den veri alan bir nesne gerekir; <xref:System.Net.Http.HttpClient> bunu yapmak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fc1c5-169">First you need an object that is capable to retrieve data from the web; you can use a <xref:System.Net.Http.HttpClient> to do that.</span></span> <span data-ttu-id="fc1c5-170">Bu nesne, isteği ve yanıtları işler.</span><span class="sxs-lookup"><span data-stu-id="fc1c5-170">This object handles the request and the responses.</span></span> <span data-ttu-id="fc1c5-171">`Program` *Program. cs* dosyasının içindeki sınıfta bu türün tek bir örneğini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="fc1c5-171">Instantiate a single instance of that type in the `Program` class inside the *Program.cs* file.</span></span>

```csharp
namespace WebAPIClient
{
    class Program
    {
        private static readonly HttpClient client = new HttpClient();

        static async Task Main(string[] args)
        {
            //...
        }
    }
}
```

<span data-ttu-id="fc1c5-172">`ProcessRepositories`Yönteme dönüp ilk bir sürümünü dolduralım:</span><span class="sxs-lookup"><span data-stu-id="fc1c5-172">Let's go back to the `ProcessRepositories` method and fill in a first version of it:</span></span>

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

<span data-ttu-id="fc1c5-173">`using`Bunun derlenmesi için dosyanın en üstüne iki yeni yönergeler de eklemeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="fc1c5-173">You'll need to also add two new `using` directives at the top of the file for this to compile:</span></span>

```csharp
using System.Net.Http;
using System.Net.Http.Headers;
```

<span data-ttu-id="fc1c5-174">Bu ilk sürüm, DotNet Foundation kuruluşundaki tüm depoların listesini okumak için bir Web isteği oluşturur.</span><span class="sxs-lookup"><span data-stu-id="fc1c5-174">This first version makes a web request to read the list of all repositories under the dotnet foundation organization.</span></span> <span data-ttu-id="fc1c5-175">(.NET Foundation için GitHub KIMLIĞI `dotnet` .) İlk birkaç satır <xref:System.Net.Http.HttpClient> Bu istek için ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="fc1c5-175">(The GitHub ID for the .NET Foundation is `dotnet`.) The first few lines set up the <xref:System.Net.Http.HttpClient> for this request.</span></span> <span data-ttu-id="fc1c5-176">İlk olarak, GitHub JSON yanıtlarını kabul edecek şekilde yapılandırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="fc1c5-176">First, it is configured to accept the GitHub JSON responses.</span></span>
<span data-ttu-id="fc1c5-177">Bu biçim yalnızca JSON 'dir.</span><span class="sxs-lookup"><span data-stu-id="fc1c5-177">This format is simply JSON.</span></span> <span data-ttu-id="fc1c5-178">Sonraki satır, bu nesneden gelen tüm isteklere bir Kullanıcı Aracısı üst bilgisi ekler.</span><span class="sxs-lookup"><span data-stu-id="fc1c5-178">The next line adds a User Agent header to all requests from this object.</span></span> <span data-ttu-id="fc1c5-179">Bu iki üst bilgi GitHub sunucusu kodu tarafından denetlenir ve GitHub 'dan bilgi almak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="fc1c5-179">These two headers are checked by the GitHub server code, and are necessary to retrieve information from GitHub.</span></span>

<span data-ttu-id="fc1c5-180">Yapılandırmasını yaptıktan sonra <xref:System.Net.Http.HttpClient> bir Web isteği yapar ve yanıtı alırsınız.</span><span class="sxs-lookup"><span data-stu-id="fc1c5-180">After you've configured the <xref:System.Net.Http.HttpClient>, you make a web request and retrieve the response.</span></span> <span data-ttu-id="fc1c5-181">Bu ilk sürümde, <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)?displayProperty=nameWithType> kolaylık yöntemini kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="fc1c5-181">In this first version, you use the <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)?displayProperty=nameWithType> convenience method.</span></span> <span data-ttu-id="fc1c5-182">Bu kolaylık yöntemi, web isteğini yapan bir görevi başlatır ve ardından istek döndürüldüğünde yanıt akışını okur ve içeriği akıştan ayıklar.</span><span class="sxs-lookup"><span data-stu-id="fc1c5-182">This convenience method starts a task that makes the web request, and then when the request returns, it reads the response stream and extracts the content from the stream.</span></span> <span data-ttu-id="fc1c5-183">Yanıtın gövdesi bir olarak döndürülür <xref:System.String> .</span><span class="sxs-lookup"><span data-stu-id="fc1c5-183">The body of the response is returned as a <xref:System.String>.</span></span> <span data-ttu-id="fc1c5-184">Dize, görev tamamlandığında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="fc1c5-184">The string is available when the task completes.</span></span>

<span data-ttu-id="fc1c5-185">Bu yöntemin son iki satırı bu görevi bekler ve ardından yanıtı konsola yazdırır.</span><span class="sxs-lookup"><span data-stu-id="fc1c5-185">The final two lines of this method await that task, and then print the response to the console.</span></span>
<span data-ttu-id="fc1c5-186">Uygulamayı derleyin ve çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="fc1c5-186">Build the app, and run it.</span></span> <span data-ttu-id="fc1c5-187">`ProcessRepositories`Şimdi bir işleç içerdiğinden, derleme uyarısı şimdi çıktı `await` .</span><span class="sxs-lookup"><span data-stu-id="fc1c5-187">The build warning is gone now, because the `ProcessRepositories` now does contain an `await` operator.</span></span> <span data-ttu-id="fc1c5-188">JSON biçimli metnin uzun bir görüntüsünü görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="fc1c5-188">You'll see a long display of JSON formatted text.</span></span>

## <a name="processing-the-json-result"></a><span data-ttu-id="fc1c5-189">JSON sonucunu işleme</span><span class="sxs-lookup"><span data-stu-id="fc1c5-189">Processing the JSON Result</span></span>

<span data-ttu-id="fc1c5-190">Bu noktada, bir Web sunucusundan yanıt almak için kodu yazmış ve bu yanıtta bulunan metni görüntüdiniz.</span><span class="sxs-lookup"><span data-stu-id="fc1c5-190">At this point, you've written the code to retrieve a response from a web server, and display the text that is contained in that response.</span></span> <span data-ttu-id="fc1c5-191">Ardından, bu JSON yanıtını C# nesnelerine dönüştürelim.</span><span class="sxs-lookup"><span data-stu-id="fc1c5-191">Next, let's convert that JSON response into C# objects.</span></span>

<span data-ttu-id="fc1c5-192"><xref:System.Text.Json.JsonSerializer?displayProperty=nameWithType>Sınıfı, NESNELERI JSON 'a seri hale getirir ve JSON 'ı nesnelere yeniden ayırır.</span><span class="sxs-lookup"><span data-stu-id="fc1c5-192">The <xref:System.Text.Json.JsonSerializer?displayProperty=nameWithType> class serializes objects to JSON and deserializes JSON into objects.</span></span> <span data-ttu-id="fc1c5-193">`repo`GITHUB API 'sinden döndürülen JSON nesnesini temsil eden bir sınıf tanımlayarak başlayın:</span><span class="sxs-lookup"><span data-stu-id="fc1c5-193">Start by defining a class to represent the `repo` JSON object returned from the GitHub API:</span></span>

```csharp
using System;

namespace WebAPIClient
{
    public class Repository
    {
        public string name { get; set; }
    }
}
```

<span data-ttu-id="fc1c5-194">Yukarıdaki kodu ' repo. cs ' adlı yeni bir dosyaya yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="fc1c5-194">Put the above code in a new file called 'repo.cs'.</span></span> <span data-ttu-id="fc1c5-195">Sınıfının bu sürümü JSON verilerini işlemek için en basit yolu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="fc1c5-195">This version of the class represents the simplest path to process JSON data.</span></span> <span data-ttu-id="fc1c5-196">Sınıf adı ve üye adı, aşağıdaki C# kuralları yerine JSON paketinde kullanılan adlarla eşleşir.</span><span class="sxs-lookup"><span data-stu-id="fc1c5-196">The class name and the member name match the names used in the JSON packet, instead of following C# conventions.</span></span> <span data-ttu-id="fc1c5-197">Daha sonra bazı yapılandırma öznitelikleri sağlayarak bunu düzeltireceksiniz.</span><span class="sxs-lookup"><span data-stu-id="fc1c5-197">You'll fix that by providing some configuration attributes later.</span></span> <span data-ttu-id="fc1c5-198">Bu sınıf, JSON serileştirme ve seri durumdan çıkarma için başka bir önemli özellik gösterir: JSON paketindeki tüm alanlar bu sınıfın bir parçası değil.</span><span class="sxs-lookup"><span data-stu-id="fc1c5-198">This class demonstrates another important feature of JSON serialization and deserialization: Not all the fields in the JSON packet are part of this class.</span></span>
<span data-ttu-id="fc1c5-199">JSON seri hale getiricisi, kullanılmakta olan sınıf türünde bulunmayan bilgileri yoksayacaktır.</span><span class="sxs-lookup"><span data-stu-id="fc1c5-199">The JSON serializer will ignore information that is not included in the class type being used.</span></span>
<span data-ttu-id="fc1c5-200">Bu özellik, JSON paketindeki alanların yalnızca bir alt kümesiyle çalışan türler oluşturmayı kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="fc1c5-200">This feature makes it easier to create types that work with only a subset of the fields in the JSON packet.</span></span>

<span data-ttu-id="fc1c5-201">Türü oluşturduğunuza göre, artık bunu serisini çıkaralım.</span><span class="sxs-lookup"><span data-stu-id="fc1c5-201">Now that you've created the type, let's deserialize it.</span></span>

<span data-ttu-id="fc1c5-202">Ardından, seri hale getirici kullanarak JSON 'u C# nesnelerine dönüştürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fc1c5-202">Next, you'll use the serializer to convert JSON into C# objects.</span></span> <span data-ttu-id="fc1c5-203"><xref:System.Net.Http.HttpClient.GetStringAsync(System.String)> `ProcessRepositories` Yöntemdeki çağrısını aşağıdaki satırlarla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="fc1c5-203">Replace the call to <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)> in your `ProcessRepositories` method with the following lines:</span></span>

```csharp
var streamTask = client.GetStreamAsync("https://api.github.com/orgs/dotnet/repos");
var repositories = await JsonSerializer.DeserializeAsync<List<Repository>>(await streamTask);
```

<span data-ttu-id="fc1c5-204">Yeni ad alanları kullanıyorsunuz, bu yüzden dosyanın en üstüne de eklemeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="fc1c5-204">You're using new namespaces, so you'll need to add it at the top of the file as well:</span></span>

```csharp
using System.Collections.Generic;
using System.Text.Json;
```

<span data-ttu-id="fc1c5-205">Artık yerine kullandığınızdan emin olun <xref:System.Net.Http.HttpClient.GetStreamAsync(System.String)> <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)> .</span><span class="sxs-lookup"><span data-stu-id="fc1c5-205">Notice that you're now using <xref:System.Net.Http.HttpClient.GetStreamAsync(System.String)> instead of <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)>.</span></span> <span data-ttu-id="fc1c5-206">Serileştirici, kaynağı olarak bir dize yerine bir akış kullanır.</span><span class="sxs-lookup"><span data-stu-id="fc1c5-206">The serializer uses a stream instead of a string as its source.</span></span> <span data-ttu-id="fc1c5-207">Önceki kod parçacığının ikinci satırında kullanılmakta olan C# dilinin birkaç özelliği açıklanalım.</span><span class="sxs-lookup"><span data-stu-id="fc1c5-207">Let's explain a couple features of the C# language that are being used in the second line of the preceding code snippet.</span></span> <span data-ttu-id="fc1c5-208">İçin ilk bağımsız değişken <xref:System.Text.Json.JsonSerializer.DeserializeAsync%60%601(System.IO.Stream,System.Text.Json.JsonSerializerOptions,System.Threading.CancellationToken)?displayProperty=nameWithType> bir `await` ifadedir.</span><span class="sxs-lookup"><span data-stu-id="fc1c5-208">The first argument to <xref:System.Text.Json.JsonSerializer.DeserializeAsync%60%601(System.IO.Stream,System.Text.Json.JsonSerializerOptions,System.Threading.CancellationToken)?displayProperty=nameWithType> is an `await` expression.</span></span> <span data-ttu-id="fc1c5-209">(Diğer iki parametre isteğe bağlıdır ve kod parçacığında atlanır.) Await ifadeleri kodunuzda neredeyse her yerde görünebilir, ancak şu anda yalnızca bir atama bildiriminin parçası olarak gördünüz.</span><span class="sxs-lookup"><span data-stu-id="fc1c5-209">(The other two parameters are optional and are omitted in the code snippet.) Await expressions can appear almost anywhere in your code, even though up to now, you've only seen them as part of an assignment statement.</span></span> <span data-ttu-id="fc1c5-210">`Deserialize`Yöntemi *geneldir*, yani JSON metninde ne tür nesneler oluşturulması gerektiği için tür bağımsız değişkenleri sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="fc1c5-210">The `Deserialize` method is *generic*, which means you must supply type arguments for what kind of objects should be created from the JSON text.</span></span> <span data-ttu-id="fc1c5-211">Bu örnekte, `List<Repository>` başka bir genel nesne olan olan ' a bir tane olarak serisini halyorsunuz <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="fc1c5-211">In this example, you're deserializing to a `List<Repository>`, which is another generic object, the <xref:System.Collections.Generic.List%601?displayProperty=nameWithType>.</span></span> <span data-ttu-id="fc1c5-212">`List<>`Sınıfı bir nesne koleksiyonunu depolar.</span><span class="sxs-lookup"><span data-stu-id="fc1c5-212">The `List<>` class stores a collection of objects.</span></span> <span data-ttu-id="fc1c5-213">Tür bağımsız değişkeni içinde depolanan nesne türlerini bildirir `List<>` .</span><span class="sxs-lookup"><span data-stu-id="fc1c5-213">The type argument declares the type of objects stored in the `List<>`.</span></span> <span data-ttu-id="fc1c5-214">JSON metni, bir depo nesnesi koleksiyonunu temsil eder, bu nedenle tür bağımsız değişkeni olur `Repository` .</span><span class="sxs-lookup"><span data-stu-id="fc1c5-214">The JSON text represents a collection of repo objects, so the type argument is `Repository`.</span></span>

<span data-ttu-id="fc1c5-215">Bu bölümde neredeyse işiniz bitti.</span><span class="sxs-lookup"><span data-stu-id="fc1c5-215">You're almost done with this section.</span></span> <span data-ttu-id="fc1c5-216">JSON 'u C# nesnelerine dönüştürdüğüne göre, her deponun adını görüntülim.</span><span class="sxs-lookup"><span data-stu-id="fc1c5-216">Now that you've converted the JSON to C# objects, let's display the name of each repository.</span></span> <span data-ttu-id="fc1c5-217">Okunan satırları değiştirin:</span><span class="sxs-lookup"><span data-stu-id="fc1c5-217">Replace the lines that read:</span></span>

```csharp
var msg = await stringTask;   //**Deleted this
Console.Write(msg);
```

<span data-ttu-id="fc1c5-218">aşağıdakiler ile:</span><span class="sxs-lookup"><span data-stu-id="fc1c5-218">with the following:</span></span>

```csharp
foreach (var repo in repositories)
    Console.WriteLine(repo.name);
```

<span data-ttu-id="fc1c5-219">Uygulamayı derleyin ve çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="fc1c5-219">Compile and run the application.</span></span> <span data-ttu-id="fc1c5-220">.NET Foundation 'ın parçası olan Depoların adlarını yazdıracaktır.</span><span class="sxs-lookup"><span data-stu-id="fc1c5-220">It will print the names of the repositories that are part of the .NET Foundation.</span></span>

## <a name="controlling-serialization"></a><span data-ttu-id="fc1c5-221">Serileştirme denetleniyor</span><span class="sxs-lookup"><span data-stu-id="fc1c5-221">Controlling Serialization</span></span>

<span data-ttu-id="fc1c5-222">Daha fazla özellik eklemeden önce `name` özniteliğini kullanarak özelliği ele alalım `[JsonPropertyName]` .</span><span class="sxs-lookup"><span data-stu-id="fc1c5-222">Before you add more features, let's address the `name` property by using the `[JsonPropertyName]` attribute.</span></span> <span data-ttu-id="fc1c5-223">`name`Depo. cs içindeki alanın bildiriminde aşağıdaki değişiklikleri yapın:</span><span class="sxs-lookup"><span data-stu-id="fc1c5-223">Make the following changes to the declaration of the `name` field in repo.cs:</span></span>

```csharp
[JsonPropertyName("name")]
public string Name { get; set; }
```

<span data-ttu-id="fc1c5-224">Özniteliğini kullanmak için `[JsonPropertyName]` , bu <xref:System.Text.Json.Serialization> ad alanını yönergelere eklemeniz gerekir `using` :</span><span class="sxs-lookup"><span data-stu-id="fc1c5-224">To use `[JsonPropertyName]` attribute, you will need to add the <xref:System.Text.Json.Serialization> namespace to the `using` directives:</span></span>

```csharp
using System.Text.Json.Serialization;
```

<span data-ttu-id="fc1c5-225">Bu değişiklik, program. cs dosyasındaki her deponun adını yazan kodu değiştirmeniz gereken anlamına gelir:</span><span class="sxs-lookup"><span data-stu-id="fc1c5-225">This change means you need to change the code that writes the name of each repository in program.cs:</span></span>

```csharp
Console.WriteLine(repo.Name);
```

<span data-ttu-id="fc1c5-226">`dotnet run`Eşlemeleri doğru olduğundan emin olmak için yürütün.</span><span class="sxs-lookup"><span data-stu-id="fc1c5-226">Execute `dotnet run` to make sure you've got the mappings correct.</span></span> <span data-ttu-id="fc1c5-227">Önceki ile aynı çıktıyı görmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="fc1c5-227">You should see the same output as before.</span></span>

<span data-ttu-id="fc1c5-228">Yeni özellikler eklemeden önce bir değişiklik yapalim.</span><span class="sxs-lookup"><span data-stu-id="fc1c5-228">Let's make one more change before adding new features.</span></span> <span data-ttu-id="fc1c5-229">`ProcessRepositories`Yöntemi zaman uyumsuz çalışmayı yapabilir ve depoların bir koleksiyonunu döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="fc1c5-229">The `ProcessRepositories` method can do the async work and return a collection of the repositories.</span></span> <span data-ttu-id="fc1c5-230">`List<Repository>`Bu yöntemden ' ı dönelim ve bilgileri yöntemine yazan kodu taşıyalim `Main` .</span><span class="sxs-lookup"><span data-stu-id="fc1c5-230">Let's return the `List<Repository>` from that method, and move the code that writes the information into the `Main` method.</span></span>

<span data-ttu-id="fc1c5-231">`ProcessRepositories`Sonucunu bir nesne listesi olan bir görevi döndürmek için imzasını değiştirin `Repository` :</span><span class="sxs-lookup"><span data-stu-id="fc1c5-231">Change the signature of `ProcessRepositories` to return a task whose result is a list of `Repository` objects:</span></span>

```csharp
private static async Task<List<Repository>> ProcessRepositories()
```

<span data-ttu-id="fc1c5-232">Ardından, JSON yanıtını işledikten sonra depoları geri döndürün:</span><span class="sxs-lookup"><span data-stu-id="fc1c5-232">Then, just return the repositories after processing the JSON response:</span></span>

```csharp
var streamTask = client.GetStreamAsync("https://api.github.com/orgs/dotnet/repos");
var repositories = await JsonSerializer.DeserializeAsync<List<Repository>>(await streamTask);
return repositories;
```

<span data-ttu-id="fc1c5-233">`Task<T>`Bu yöntemi olarak işaretlediğiniz için derleyici, döndürme için nesnesi oluşturur `async` .</span><span class="sxs-lookup"><span data-stu-id="fc1c5-233">The compiler generates the `Task<T>` object for the return because you've marked this method as `async`.</span></span>
<span data-ttu-id="fc1c5-234">Ardından, `Main` yöntemi bu sonuçları yakalayıp, her depo adını konsola yazar şekilde değiştirelim.</span><span class="sxs-lookup"><span data-stu-id="fc1c5-234">Then, let's modify the `Main` method so that it captures those results and writes each repository name to the console.</span></span> <span data-ttu-id="fc1c5-235">`Main`Yönteminiz şu şekilde görünür:</span><span class="sxs-lookup"><span data-stu-id="fc1c5-235">Your `Main` method now looks like this:</span></span>

```csharp
public static async Task Main(string[] args)
{
    var repositories = await ProcessRepositories();

    foreach (var repo in repositories)
        Console.WriteLine(repo.Name);
}
```

## <a name="reading-more-information"></a><span data-ttu-id="fc1c5-236">Daha fazla bilgi okunuyor</span><span class="sxs-lookup"><span data-stu-id="fc1c5-236">Reading More Information</span></span>

<span data-ttu-id="fc1c5-237">Bu işlemi, GitHub API 'sinden gönderilen JSON paketindeki özelliklerden daha fazlasını işleyerek tamamlayalim.</span><span class="sxs-lookup"><span data-stu-id="fc1c5-237">Let's finish this by processing a few more of the properties in the JSON packet that gets sent from the GitHub API.</span></span> <span data-ttu-id="fc1c5-238">Her şeyi almak istemezsiniz, ancak birkaç özelliği eklemek C# dilinin daha fazla özelliği gösterir.</span><span class="sxs-lookup"><span data-stu-id="fc1c5-238">You won't want to grab everything, but adding a few properties will demonstrate a few more features of the C# language.</span></span>

<span data-ttu-id="fc1c5-239">Daha fazla basit türü `Repository` sınıf tanımına ekleyerek başlayalım.</span><span class="sxs-lookup"><span data-stu-id="fc1c5-239">Let's start by adding a few more simple types to the `Repository` class definition.</span></span> <span data-ttu-id="fc1c5-240">Bu özellikleri bu sınıfa ekleyin:</span><span class="sxs-lookup"><span data-stu-id="fc1c5-240">Add these properties to that class:</span></span>

```csharp
[JsonPropertyName("description")]
public string Description { get; set; }

[JsonPropertyName("html_url")]
public Uri GitHubHomeUrl { get; set; }

[JsonPropertyName("homepage")]
public Uri Homepage { get; set; }

[JsonPropertyName("watchers")]
public int Watchers { get; set; }
```

<span data-ttu-id="fc1c5-241">Bu özellikler dize türünden (JSON paketlerinin içerdiği), hedef türüne yerleşik Dönüştürmelere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="fc1c5-241">These properties have built-in conversions from the string type (which is what the JSON packets contain) to the target type.</span></span> <span data-ttu-id="fc1c5-242"><xref:System.Uri>Tür sizin için yeni olabilir.</span><span class="sxs-lookup"><span data-stu-id="fc1c5-242">The <xref:System.Uri> type may be new to you.</span></span> <span data-ttu-id="fc1c5-243">Bir URI 'yi veya bu durumda bir URL 'yi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="fc1c5-243">It represents a URI, or in this case, a URL.</span></span> <span data-ttu-id="fc1c5-244">Ve türleri söz konusu olduğunda `Uri` `int` , JSON paketi hedef türüne Dönüştürülmeyen veriler içeriyorsa, serileştirme eylemi bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="fc1c5-244">In the case of the `Uri` and `int` types, if the JSON packet contains data that does not convert to the target type, the serialization action will throw an exception.</span></span>

<span data-ttu-id="fc1c5-245">Bunları ekledikten sonra, `Main` Bu öğeleri göstermek için yöntemini güncelleştirin:</span><span class="sxs-lookup"><span data-stu-id="fc1c5-245">Once you've added these, update the `Main` method to display those elements:</span></span>

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

<span data-ttu-id="fc1c5-246">Son bir adım olarak, son gönderme işlemi için bilgileri ekleyelim.</span><span class="sxs-lookup"><span data-stu-id="fc1c5-246">As a final step, let's add the information for the last push operation.</span></span> <span data-ttu-id="fc1c5-247">Bu bilgiler, JSON yanıtında bu biçimde biçimlendirilir:</span><span class="sxs-lookup"><span data-stu-id="fc1c5-247">This information is formatted in this fashion in the JSON response:</span></span>

```json
2016-02-08T21:27:00Z
```

<span data-ttu-id="fc1c5-248">Bu biçim Eşgüdümlü Evrensel Saat (UTC) biçiminde olduğundan, özelliği olan bir <xref:System.DateTime> değer alırsınız <xref:System.DateTime.Kind%2A> <xref:System.DateTimeKind.Utc> .</span><span class="sxs-lookup"><span data-stu-id="fc1c5-248">That format is in Coordinated Universal Time (UTC) so you'll get a <xref:System.DateTime> value whose <xref:System.DateTime.Kind%2A> property is <xref:System.DateTimeKind.Utc>.</span></span> <span data-ttu-id="fc1c5-249">Saat diliminizde temsil edilen bir tarihi tercih ediyorsanız, özel bir dönüştürme yöntemi yazmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="fc1c5-249">If you prefer a date represented in your time zone, you'll need to write a custom conversion method.</span></span> <span data-ttu-id="fc1c5-250">İlk olarak, `public` sınıfınızın tarih ve SAATININ UTC gösterimini `Repository` ve `LastPush` `readonly` yerel saate Dönüştürülecek tarihi döndüren bir özelliği tanımlar:</span><span class="sxs-lookup"><span data-stu-id="fc1c5-250">First, define a `public` property that will hold the UTC representation of the date and time in your `Repository` class and a `LastPush` `readonly` property that returns the date converted to local time:</span></span>

```csharp
[JsonPropertyName("pushed_at")]
public DateTime LastPushUtc { get; set; }

public DateTime LastPush => LastPushUtc.ToLocalTime();
```

<span data-ttu-id="fc1c5-251">Şimdi tanımladığımız yeni yapıları inceleyelim.</span><span class="sxs-lookup"><span data-stu-id="fc1c5-251">Let's go over the new constructs we just defined.</span></span> <span data-ttu-id="fc1c5-252">`LastPush`Özelliği, erişimci için *ifade-Bodied üyesi* kullanılarak tanımlanır `get` .</span><span class="sxs-lookup"><span data-stu-id="fc1c5-252">The `LastPush` property is defined using an *expression-bodied member* for the `get` accessor.</span></span> <span data-ttu-id="fc1c5-253">`set`Erişimci yok.</span><span class="sxs-lookup"><span data-stu-id="fc1c5-253">There is no `set` accessor.</span></span> <span data-ttu-id="fc1c5-254">`set`Erişimcinin atlanması, C# ' de *salt okunurdur* bir özelliği nasıl tanımlayacağınızı belirler.</span><span class="sxs-lookup"><span data-stu-id="fc1c5-254">Omitting the `set` accessor is how you define a *read-only* property in C#.</span></span> <span data-ttu-id="fc1c5-255">(Evet, C# dilinde *salt yazılır* özellikler oluşturabilirsiniz, ancak bunların değeri sınırlı olur.)</span><span class="sxs-lookup"><span data-stu-id="fc1c5-255">(Yes, you can create *write-only* properties in C#, but their value is limited.)</span></span>

<span data-ttu-id="fc1c5-256">Son olarak, konsolda bir çıkış bildirisi daha ekleyin ve bu uygulamayı yeniden oluşturup çalıştırmak için hazırsınız:</span><span class="sxs-lookup"><span data-stu-id="fc1c5-256">Finally, add one more output statement in the console, and you're ready to build and run this app again:</span></span>

```csharp
Console.WriteLine(repo.LastPush);
```

<span data-ttu-id="fc1c5-257">Sürümünüz artık [tamamlanmış örnekle](https://github.com/dotnet/samples/tree/main/csharp/getting-started/console-webapiclient)eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="fc1c5-257">Your version should now match the [finished sample](https://github.com/dotnet/samples/tree/main/csharp/getting-started/console-webapiclient).</span></span>

## <a name="conclusion"></a><span data-ttu-id="fc1c5-258">Sonuç</span><span class="sxs-lookup"><span data-stu-id="fc1c5-258">Conclusion</span></span>

<span data-ttu-id="fc1c5-259">Bu öğretici, Web istekleri oluşturma, sonucu ayrıştırma ve bu sonuçların özelliklerini görüntüleme konusunda sizi gösterdi.</span><span class="sxs-lookup"><span data-stu-id="fc1c5-259">This tutorial showed you how to make web requests, parse the result, and display properties of those results.</span></span> <span data-ttu-id="fc1c5-260">Ayrıca, yeni paketleri projenize bağımlılıklar olarak eklediniz.</span><span class="sxs-lookup"><span data-stu-id="fc1c5-260">You've also added new packages as dependencies in your project.</span></span> <span data-ttu-id="fc1c5-261">Nesne odaklı teknikleri destekleyen C# dilinin bazı özelliklerini gördünüz.</span><span class="sxs-lookup"><span data-stu-id="fc1c5-261">You've seen some of the features of the C# language that support object-oriented techniques.</span></span>

<a name="dotnet-restore-note"></a>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
