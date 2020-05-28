---
title: .NET Core kullanarak REST istemcisi oluşturma
description: Bu öğretici, .NET Core ve C# dilinde birçok özellik öğretir.
ms.date: 01/09/2020
ms.assetid: 51033ce2-7a53-4cdd-966d-9da15c8204d2
ms.openlocfilehash: 1d1d1bec8c6602e4fe34fa3ce243423290412736
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84004861"
---
# <a name="rest-client"></a><span data-ttu-id="eb7b7-103">REST istemcisi</span><span class="sxs-lookup"><span data-stu-id="eb7b7-103">REST client</span></span>

<span data-ttu-id="eb7b7-104">Bu öğretici, .NET Core ve C# dilinde birçok özellik öğretir.</span><span class="sxs-lookup"><span data-stu-id="eb7b7-104">This tutorial teaches you a number of features in .NET Core and the C# language.</span></span> <span data-ttu-id="eb7b7-105">Şunları öğreneceksiniz:</span><span class="sxs-lookup"><span data-stu-id="eb7b7-105">You’ll learn:</span></span>

* <span data-ttu-id="eb7b7-106">.NET Core CLI temel kavramları.</span><span class="sxs-lookup"><span data-stu-id="eb7b7-106">The basics of the .NET Core CLI.</span></span>
* <span data-ttu-id="eb7b7-107">C# dil özelliklerine genel bakış.</span><span class="sxs-lookup"><span data-stu-id="eb7b7-107">An overview of C# Language features.</span></span>
* <span data-ttu-id="eb7b7-108">NuGet ile bağımlılıkları yönetme</span><span class="sxs-lookup"><span data-stu-id="eb7b7-108">Managing dependencies with NuGet</span></span>
* <span data-ttu-id="eb7b7-109">HTTP Iletişimleri</span><span class="sxs-lookup"><span data-stu-id="eb7b7-109">HTTP Communications</span></span>
* <span data-ttu-id="eb7b7-110">JSON bilgilerini işleme</span><span class="sxs-lookup"><span data-stu-id="eb7b7-110">Processing JSON information</span></span>
* <span data-ttu-id="eb7b7-111">Yapılandırmayı özniteliklerle yönetme.</span><span class="sxs-lookup"><span data-stu-id="eb7b7-111">Managing configuration with Attributes.</span></span>

<span data-ttu-id="eb7b7-112">GitHub 'da REST hizmetine HTTP Istekleri veren bir uygulama oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="eb7b7-112">You’ll build an application that issues HTTP Requests to a REST service on GitHub.</span></span> <span data-ttu-id="eb7b7-113">JSON biçiminde bilgileri okur ve bu JSON paketini C# nesnelerine dönüştürürsünüz.</span><span class="sxs-lookup"><span data-stu-id="eb7b7-113">You'll read information in JSON format, and convert that JSON packet into C# objects.</span></span> <span data-ttu-id="eb7b7-114">Son olarak C# nesneleriyle nasıl çalışacaksınız görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="eb7b7-114">Finally, you'll see how to work with C# objects.</span></span>

<span data-ttu-id="eb7b7-115">Bu öğreticide birçok özellik vardır.</span><span class="sxs-lookup"><span data-stu-id="eb7b7-115">There are many features in this tutorial.</span></span> <span data-ttu-id="eb7b7-116">Bunları birer birer oluşturalım.</span><span class="sxs-lookup"><span data-stu-id="eb7b7-116">Let’s build them one by one.</span></span>

<span data-ttu-id="eb7b7-117">Bu konuyla ilgili [son örnekle](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient) birlikte izlemeyi tercih ediyorsanız, indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="eb7b7-117">If you prefer to follow along with the [final sample](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient) for this topic, you can download it.</span></span> <span data-ttu-id="eb7b7-118">İndirme yönergeleri için bkz. [örnekler ve öğreticiler](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="eb7b7-118">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="eb7b7-119">Ön koşullar</span><span class="sxs-lookup"><span data-stu-id="eb7b7-119">Prerequisites</span></span>

<span data-ttu-id="eb7b7-120">Makinenizi .NET Core çalıştıracak şekilde ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="eb7b7-120">You’ll need to set up your machine to run .NET core.</span></span> <span data-ttu-id="eb7b7-121">Yükleme yönergelerini [.NET Core İndirmeleri](https://dotnet.microsoft.com/download) sayfasında bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="eb7b7-121">You can find the installation instructions on the [.NET Core Downloads](https://dotnet.microsoft.com/download) page.</span></span> <span data-ttu-id="eb7b7-122">Bu uygulamayı Windows, Linux, macOS veya bir Docker kapsayıcısında çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="eb7b7-122">You can run this application on Windows, Linux, macOS or in a Docker container.</span></span>
<span data-ttu-id="eb7b7-123">En sevdiğiniz kod düzenleyicinizi yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="eb7b7-123">You’ll need to install your favorite code editor.</span></span> <span data-ttu-id="eb7b7-124">Aşağıdaki açıklamalar açık kaynaklı, platformlar arası bir düzenleyici olan [Visual Studio Code](https://code.visualstudio.com/)kullanır.</span><span class="sxs-lookup"><span data-stu-id="eb7b7-124">The descriptions below use [Visual Studio Code](https://code.visualstudio.com/), which is an open source, cross platform editor.</span></span> <span data-ttu-id="eb7b7-125">Bununla birlikte, rahat olan her türlü aracı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="eb7b7-125">However, you can use whatever tools you are comfortable with.</span></span>

## <a name="create-the-application"></a><span data-ttu-id="eb7b7-126">Uygulamayı oluşturma</span><span class="sxs-lookup"><span data-stu-id="eb7b7-126">Create the Application</span></span>

<span data-ttu-id="eb7b7-127">İlk adım yeni bir uygulama oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="eb7b7-127">The first step is to create a new application.</span></span> <span data-ttu-id="eb7b7-128">Bir komut istemi açın ve uygulamanız için yeni bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="eb7b7-128">Open a command prompt and create a new directory for your application.</span></span> <span data-ttu-id="eb7b7-129">Geçerli dizini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="eb7b7-129">Make that the current directory.</span></span> <span data-ttu-id="eb7b7-130">Konsol penceresine aşağıdaki komutu girin:</span><span class="sxs-lookup"><span data-stu-id="eb7b7-130">Enter the following command in a console window:</span></span>

```dotnetcli
dotnet new console --name WebAPIClient
```

<span data-ttu-id="eb7b7-131">Bu, temel bir "Merhaba Dünya" uygulaması için başlangıç dosyalarını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="eb7b7-131">This creates the starter files for a basic "Hello World" application.</span></span> <span data-ttu-id="eb7b7-132">Proje adı "WebAPIClient" dir.</span><span class="sxs-lookup"><span data-stu-id="eb7b7-132">The project name is "WebAPIClient".</span></span> <span data-ttu-id="eb7b7-133">Bu yeni bir proje olduğundan, bağımlılıklardan hiçbiri yerinde değildir.</span><span class="sxs-lookup"><span data-stu-id="eb7b7-133">As this is a new project, none of the dependencies are in place.</span></span> <span data-ttu-id="eb7b7-134">İlk çalıştırma .NET Core Framework 'ü indirir, bir geliştirme sertifikası yükler ve eksik bağımlılıkları geri yüklemek için NuGet Paket Yöneticisi 'ni çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="eb7b7-134">The first run will download the .NET Core framework, install a development certificate, and run the NuGet package manager to restore missing dependencies.</span></span>

<span data-ttu-id="eb7b7-135">Değişiklik yapmaya başlamadan önce, `dotnet run` uygulamanızı çalıştırmak için komut isteminde ([bkz. Note](#dotnet-restore-note)) yazın.</span><span class="sxs-lookup"><span data-stu-id="eb7b7-135">Before you start making modifications, type `dotnet run` ([see note](#dotnet-restore-note)) at the command prompt to run your application.</span></span> <span data-ttu-id="eb7b7-136">`dotnet run``dotnet restore`ortamınızda bağımlılıklar eksik olursa otomatik olarak gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="eb7b7-136">`dotnet run` automatically performs `dotnet restore` if your environment is missing dependencies.</span></span> <span data-ttu-id="eb7b7-137">Uygulamanızın yeniden oluşturulması gerekiyorsa de çalışır `dotnet build` .</span><span class="sxs-lookup"><span data-stu-id="eb7b7-137">It also performs `dotnet build` if your application needs to be rebuilt.</span></span>
<span data-ttu-id="eb7b7-138">İlk kurulumdan sonra, yalnızca `dotnet restore` `dotnet build` projeniz için anlamlı olduğunda veya çalıştırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="eb7b7-138">After your initial setup, you will only need to run `dotnet restore` or `dotnet build` when it makes sense for your project.</span></span>

## <a name="adding-new-dependencies"></a><span data-ttu-id="eb7b7-139">Yeni bağımlılıklar ekleniyor</span><span class="sxs-lookup"><span data-stu-id="eb7b7-139">Adding New Dependencies</span></span>

<span data-ttu-id="eb7b7-140">.NET Core için önemli tasarım amaçlarından biri, .NET yüklemesinin boyutunu en aza indirmektir.</span><span class="sxs-lookup"><span data-stu-id="eb7b7-140">One of the key design goals for .NET Core is to minimize the size of the .NET installation.</span></span> <span data-ttu-id="eb7b7-141">Bir uygulamanın bazı özellikleri için ek kitaplıklar gerekiyorsa, bu bağımlılıkları C# projeniz ( \* . csproj) dosyanıza eklersiniz.</span><span class="sxs-lookup"><span data-stu-id="eb7b7-141">If an application needs additional libraries for some of its features, you add those dependencies into your C# project (\*.csproj) file.</span></span> <span data-ttu-id="eb7b7-142">Örneğimiz için, `System.Runtime.Serialization.Json` UYGULAMANıZıN JSON yanıtlarını işleyebilmesi için paketini eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="eb7b7-142">For our example, you'll need to add the `System.Runtime.Serialization.Json` package, so your application can process JSON responses.</span></span>

<span data-ttu-id="eb7b7-143">`System.Runtime.Serialization.Json`Bu uygulama için pakete ihtiyacınız olacak.</span><span class="sxs-lookup"><span data-stu-id="eb7b7-143">You'll need the `System.Runtime.Serialization.Json` package for this application.</span></span> <span data-ttu-id="eb7b7-144">Aşağıdaki [.net CLI](../../core/tools/dotnet-add-package.md) komutunu çalıştırarak projenize ekleyin:</span><span class="sxs-lookup"><span data-stu-id="eb7b7-144">Add it to your project by running the following [.NET CLI](../../core/tools/dotnet-add-package.md) command:</span></span>

```dotnetcli
dotnet add package System.Text.Json
```

## <a name="making-web-requests"></a><span data-ttu-id="eb7b7-145">Web Istekleri yapma</span><span class="sxs-lookup"><span data-stu-id="eb7b7-145">Making Web Requests</span></span>

<span data-ttu-id="eb7b7-146">Artık Web 'den veri almaya başlamaya hazırsınız.</span><span class="sxs-lookup"><span data-stu-id="eb7b7-146">Now you're ready to start retrieving data from the web.</span></span> <span data-ttu-id="eb7b7-147">Bu uygulamada, [GITHUB API](https://developer.github.com/v3/)'sindeki bilgileri okuyacaksınız.</span><span class="sxs-lookup"><span data-stu-id="eb7b7-147">In this application, you'll read information from the [GitHub API](https://developer.github.com/v3/).</span></span> <span data-ttu-id="eb7b7-148">[.Net Foundation](https://www.dotnetfoundation.org/) şemsiye kapsamındaki projelerle ilgili bilgileri okuyalim.</span><span class="sxs-lookup"><span data-stu-id="eb7b7-148">Let's read information about the projects under the [.NET Foundation](https://www.dotnetfoundation.org/) umbrella.</span></span> <span data-ttu-id="eb7b7-149">Projeler hakkındaki bilgileri almak için GitHub API 'sine istek yaparak başlayacaksınız.</span><span class="sxs-lookup"><span data-stu-id="eb7b7-149">You'll start by making the request to the GitHub API to retrieve information on the projects.</span></span> <span data-ttu-id="eb7b7-150">Kullanacağınız uç nokta: <https://api.github.com/orgs/dotnet/repos> .</span><span class="sxs-lookup"><span data-stu-id="eb7b7-150">The endpoint you'll use is: <https://api.github.com/orgs/dotnet/repos>.</span></span> <span data-ttu-id="eb7b7-151">Bu projelerle ilgili tüm bilgileri almak istiyorsunuz, bu nedenle bir HTTP GET isteği kullanacaksınız.</span><span class="sxs-lookup"><span data-stu-id="eb7b7-151">You want to retrieve all the information about these projects, so you'll use an HTTP GET request.</span></span>
<span data-ttu-id="eb7b7-152">Tarayıcınız ayrıca HTTP GET isteklerini kullanır; bu nedenle, hangi bilgileri almak ve işlemek istediğinizi görmek için bu URL 'YI tarayıcınıza yapıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="eb7b7-152">Your browser also uses HTTP GET requests, so you can paste that URL into your browser to see what information you'll be receiving and processing.</span></span>

<span data-ttu-id="eb7b7-153"><xref:System.Net.Http.HttpClient>Web istekleri yapmak için sınıfını kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="eb7b7-153">You use the <xref:System.Net.Http.HttpClient> class to make web requests.</span></span> <span data-ttu-id="eb7b7-154">Tüm modern .NET API 'Lerinde olduğu gibi, <xref:System.Net.Http.HttpClient> uzun süre çalışan API 'ler için yalnızca zaman uyumsuz yöntemleri destekler.</span><span class="sxs-lookup"><span data-stu-id="eb7b7-154">Like all modern .NET APIs, <xref:System.Net.Http.HttpClient> supports only async methods for its long-running APIs.</span></span>
<span data-ttu-id="eb7b7-155">Zaman uyumsuz bir yöntem yaparak başlayın.</span><span class="sxs-lookup"><span data-stu-id="eb7b7-155">Start by making an async method.</span></span> <span data-ttu-id="eb7b7-156">Uygulamanın işlevlerini oluştururken uygulamayı doldurursunuz.</span><span class="sxs-lookup"><span data-stu-id="eb7b7-156">You'll fill in the implementation as you build the functionality of the application.</span></span> <span data-ttu-id="eb7b7-157">`program.cs`Dosyayı proje dizininizde açıp sınıfına aşağıdaki yöntemi ekleyerek başlayın `Program` :</span><span class="sxs-lookup"><span data-stu-id="eb7b7-157">Start by opening the `program.cs` file in your project directory and adding the following method to the `Program` class:</span></span>

```csharp
private static async Task ProcessRepositories()
{
}
```

<span data-ttu-id="eb7b7-158">`using` `Main` C# derleyicisinin türü tanıması için yönteminizin en üstüne bir yönerge eklemeniz gerekir <xref:System.Threading.Tasks.Task> :</span><span class="sxs-lookup"><span data-stu-id="eb7b7-158">You'll need to add a `using` directive at the top of your `Main` method so that the C# compiler recognizes the <xref:System.Threading.Tasks.Task> type:</span></span>

```csharp
using System.Threading.Tasks;
```

<span data-ttu-id="eb7b7-159">Bu noktada projenizi oluşturursanız, herhangi bir `await` işleç içermediğinden ve zaman uyumlu olarak çalışacağı için bu yöntem için bir uyarı alırsınız.</span><span class="sxs-lookup"><span data-stu-id="eb7b7-159">If you build your project at this point, you'll get a warning generated for this method, because it does not contain any `await` operators and will run synchronously.</span></span> <span data-ttu-id="eb7b7-160">Şimdilik bunu yoksayın; yöntemi doldurduktan sonra `await` işleçleri ekleyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="eb7b7-160">Ignore that for now; you'll add `await` operators as you fill in the method.</span></span>

<span data-ttu-id="eb7b7-161">Sonra, yöntemini `Main` çağırmak için yöntemini güncelleştirin `ProcessRepositories` .</span><span class="sxs-lookup"><span data-stu-id="eb7b7-161">Next, update the `Main` method to call the `ProcessRepositories` method.</span></span> <span data-ttu-id="eb7b7-162">`ProcessRepositories`Yöntemi bir görevi döndürür ve bu görev tamamlanmadan önce programdan çıkmamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="eb7b7-162">The `ProcessRepositories` method returns a task, and you shouldn't exit the program before that task finishes.</span></span> <span data-ttu-id="eb7b7-163">Bu nedenle, imzasını değiştirmeniz gerekir `Main` .</span><span class="sxs-lookup"><span data-stu-id="eb7b7-163">Therefore, you must change the signature of `Main`.</span></span> <span data-ttu-id="eb7b7-164">Değiştiricisini ekleyin `async` ve dönüş türünü olarak değiştirin `Task` .</span><span class="sxs-lookup"><span data-stu-id="eb7b7-164">Add the `async` modifier, and change the return type to `Task`.</span></span> <span data-ttu-id="eb7b7-165">Ardından, yönteminin gövdesinde öğesine bir çağrı ekleyin `ProcessRepositories` .</span><span class="sxs-lookup"><span data-stu-id="eb7b7-165">Then, in the body of the method, add a call to `ProcessRepositories`.</span></span> <span data-ttu-id="eb7b7-166">`await`Anahtar sözcüğünü bu yöntem çağrısına ekleyin:</span><span class="sxs-lookup"><span data-stu-id="eb7b7-166">Add the `await` keyword to that method call:</span></span>

```csharp
static async Task Main(string[] args)
{
    await ProcessRepositories();
}
```

<span data-ttu-id="eb7b7-167">Artık hiçbir şey yapmaz ancak zaman uyumsuz olarak bunu yapar.</span><span class="sxs-lookup"><span data-stu-id="eb7b7-167">Now, you have a program that does nothing, but does it asynchronously.</span></span> <span data-ttu-id="eb7b7-168">Bunu geliştirelim.</span><span class="sxs-lookup"><span data-stu-id="eb7b7-168">Let's improve it.</span></span>

<span data-ttu-id="eb7b7-169">Önce, Web 'den veri alan bir nesne gerekir; <xref:System.Net.Http.HttpClient>bunu yapmak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="eb7b7-169">First you need an object that is capable to retrieve data from the web; you can use a <xref:System.Net.Http.HttpClient> to do that.</span></span> <span data-ttu-id="eb7b7-170">Bu nesne, isteği ve yanıtları işler.</span><span class="sxs-lookup"><span data-stu-id="eb7b7-170">This object handles the request and the responses.</span></span> <span data-ttu-id="eb7b7-171">`Program` *Program.cs* dosyasının içindeki sınıfta bu türün tek bir örneğini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="eb7b7-171">Instantiate a single instance of that type in the `Program` class inside the *Program.cs* file.</span></span>

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

<span data-ttu-id="eb7b7-172">`ProcessRepositories`Yönteme dönüp ilk bir sürümünü dolduralım:</span><span class="sxs-lookup"><span data-stu-id="eb7b7-172">Let's go back to the `ProcessRepositories` method and fill in a first version of it:</span></span>

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

<span data-ttu-id="eb7b7-173">`using`Bunun derlenmesi için dosyanın en üstüne iki yeni yönergeler de eklemeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="eb7b7-173">You'll need to also add two new `using` directives at the top of the file for this to compile:</span></span>

```csharp
using System.Net.Http;
using System.Net.Http.Headers;
```

<span data-ttu-id="eb7b7-174">Bu ilk sürüm, DotNet Foundation kuruluşundaki tüm depoların listesini okumak için bir Web isteği oluşturur.</span><span class="sxs-lookup"><span data-stu-id="eb7b7-174">This first version makes a web request to read the list of all repositories under the dotnet foundation organization.</span></span> <span data-ttu-id="eb7b7-175">(.NET Foundation için gitHub KIMLIĞI ' DotNet ').</span><span class="sxs-lookup"><span data-stu-id="eb7b7-175">(The gitHub ID for the .NET Foundation is 'dotnet').</span></span> <span data-ttu-id="eb7b7-176">İlk birkaç satır <xref:System.Net.Http.HttpClient> Bu istek için ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="eb7b7-176">The first few lines set up the <xref:System.Net.Http.HttpClient> for this request.</span></span> <span data-ttu-id="eb7b7-177">İlk olarak, GitHub JSON yanıtlarını kabul edecek şekilde yapılandırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="eb7b7-177">First, it is configured to accept the GitHub JSON responses.</span></span>
<span data-ttu-id="eb7b7-178">Bu biçim yalnızca JSON 'dir.</span><span class="sxs-lookup"><span data-stu-id="eb7b7-178">This format is simply JSON.</span></span> <span data-ttu-id="eb7b7-179">Sonraki satır, bu nesneden gelen tüm isteklere bir Kullanıcı Aracısı üst bilgisi ekler.</span><span class="sxs-lookup"><span data-stu-id="eb7b7-179">The next line adds a User Agent header to all requests from this object.</span></span> <span data-ttu-id="eb7b7-180">Bu iki üst bilgi GitHub sunucusu kodu tarafından denetlenir ve GitHub 'dan bilgi almak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="eb7b7-180">These two headers are checked by the GitHub server code, and are necessary to retrieve information from GitHub.</span></span>

<span data-ttu-id="eb7b7-181">Yapılandırmasını yaptıktan sonra <xref:System.Net.Http.HttpClient> bir Web isteği yapar ve yanıtı alırsınız.</span><span class="sxs-lookup"><span data-stu-id="eb7b7-181">After you've configured the <xref:System.Net.Http.HttpClient>, you make a web request and retrieve the response.</span></span> <span data-ttu-id="eb7b7-182">Bu ilk sürümde, <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)?displayProperty=nameWithType> kolaylık yöntemini kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="eb7b7-182">In this first version, you use the <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)?displayProperty=nameWithType> convenience method.</span></span> <span data-ttu-id="eb7b7-183">Bu kolaylık yöntemi, web isteğini yapan bir görevi başlatır ve ardından istek döndürüldüğünde yanıt akışını okur ve içeriği akıştan ayıklar.</span><span class="sxs-lookup"><span data-stu-id="eb7b7-183">This convenience method starts a task that makes the web request, and then when the request returns, it reads the response stream and extracts the content from the stream.</span></span> <span data-ttu-id="eb7b7-184">Yanıtın gövdesi bir olarak döndürülür <xref:System.String> .</span><span class="sxs-lookup"><span data-stu-id="eb7b7-184">The body of the response is returned as a <xref:System.String>.</span></span> <span data-ttu-id="eb7b7-185">Dize, görev tamamlandığında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="eb7b7-185">The string is available when the task completes.</span></span>

<span data-ttu-id="eb7b7-186">Bu yöntemin son iki satırı bu görevi bekler ve ardından yanıtı konsola yazdırır.</span><span class="sxs-lookup"><span data-stu-id="eb7b7-186">The final two lines of this method await that task, and then print the response to the console.</span></span>
<span data-ttu-id="eb7b7-187">Uygulamayı derleyin ve çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="eb7b7-187">Build the app, and run it.</span></span> <span data-ttu-id="eb7b7-188">`ProcessRepositories`Şimdi bir işleç içerdiğinden, derleme uyarısı şimdi çıktı `await` .</span><span class="sxs-lookup"><span data-stu-id="eb7b7-188">The build warning is gone now, because the `ProcessRepositories` now does contain an `await` operator.</span></span> <span data-ttu-id="eb7b7-189">JSON biçimli metnin uzun bir görüntüsünü görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="eb7b7-189">You'll see a long display of JSON formatted text.</span></span>

## <a name="processing-the-json-result"></a><span data-ttu-id="eb7b7-190">JSON sonucunu işleme</span><span class="sxs-lookup"><span data-stu-id="eb7b7-190">Processing the JSON Result</span></span>

<span data-ttu-id="eb7b7-191">Bu noktada, bir Web sunucusundan yanıt almak için kodu yazmış ve bu yanıtta bulunan metni görüntüdiniz.</span><span class="sxs-lookup"><span data-stu-id="eb7b7-191">At this point, you've written the code to retrieve a response from a web server, and display the text that is contained in that response.</span></span> <span data-ttu-id="eb7b7-192">Ardından, bu JSON yanıtını C# nesnelerine dönüştürelim.</span><span class="sxs-lookup"><span data-stu-id="eb7b7-192">Next, let's convert that JSON response into C# objects.</span></span>

<span data-ttu-id="eb7b7-193"><xref:System.Text.Json.JsonSerializer?displayProperty=nameWithType>Sınıfı, NESNELERI JSON 'a seri hale getirir ve JSON 'ı nesnelere yeniden ayırır.</span><span class="sxs-lookup"><span data-stu-id="eb7b7-193">The <xref:System.Text.Json.JsonSerializer?displayProperty=nameWithType> class serializes objects to JSON and deserializes JSON into objects.</span></span> <span data-ttu-id="eb7b7-194">`repo`GITHUB API 'sinden döndürülen JSON nesnesini temsil eden bir sınıf tanımlayarak başlayın:</span><span class="sxs-lookup"><span data-stu-id="eb7b7-194">Start by defining a class to represent the `repo` JSON object returned from the GitHub API:</span></span>

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

<span data-ttu-id="eb7b7-195">Yukarıdaki kodu ' repo. cs ' adlı yeni bir dosyaya yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="eb7b7-195">Put the above code in a new file called 'repo.cs'.</span></span> <span data-ttu-id="eb7b7-196">Sınıfının bu sürümü JSON verilerini işlemek için en basit yolu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="eb7b7-196">This version of the class represents the simplest path to process JSON data.</span></span> <span data-ttu-id="eb7b7-197">Sınıf adı ve üye adı, aşağıdaki C# kuralları yerine JSON paketinde kullanılan adlarla eşleşir.</span><span class="sxs-lookup"><span data-stu-id="eb7b7-197">The class name and the member name match the names used in the JSON packet, instead of following C# conventions.</span></span> <span data-ttu-id="eb7b7-198">Daha sonra bazı yapılandırma öznitelikleri sağlayarak bunu düzeltireceksiniz.</span><span class="sxs-lookup"><span data-stu-id="eb7b7-198">You'll fix that by providing some configuration attributes later.</span></span> <span data-ttu-id="eb7b7-199">Bu sınıf, JSON serileştirme ve seri durumdan çıkarma için başka bir önemli özellik gösterir: JSON paketindeki tüm alanlar bu sınıfın bir parçası değil.</span><span class="sxs-lookup"><span data-stu-id="eb7b7-199">This class demonstrates another important feature of JSON serialization and deserialization: Not all the fields in the JSON packet are part of this class.</span></span>
<span data-ttu-id="eb7b7-200">JSON seri hale getiricisi, kullanılmakta olan sınıf türünde bulunmayan bilgileri yoksayacaktır.</span><span class="sxs-lookup"><span data-stu-id="eb7b7-200">The JSON serializer will ignore information that is not included in the class type being used.</span></span>
<span data-ttu-id="eb7b7-201">Bu özellik, JSON paketindeki alanların yalnızca bir alt kümesiyle çalışan türler oluşturmayı kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="eb7b7-201">This feature makes it easier to create types that work with only a subset of the fields in the JSON packet.</span></span>

<span data-ttu-id="eb7b7-202">Türü oluşturduğunuza göre, artık bunu serisini çıkaralım.</span><span class="sxs-lookup"><span data-stu-id="eb7b7-202">Now that you've created the type, let's deserialize it.</span></span>

<span data-ttu-id="eb7b7-203">Ardından, seri hale getirici kullanarak JSON 'u C# nesnelerine dönüştürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="eb7b7-203">Next, you'll use the serializer to convert JSON into C# objects.</span></span> <span data-ttu-id="eb7b7-204"><xref:System.Net.Http.HttpClient.GetStringAsync(System.String)> `ProcessRepositories` Yöntemdeki çağrısını aşağıdaki satırlarla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="eb7b7-204">Replace the call to <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)> in your `ProcessRepositories` method with the following lines:</span></span>

```csharp
var streamTask = client.GetStreamAsync("https://api.github.com/orgs/dotnet/repos");
var repositories = await JsonSerializer.DeserializeAsync<List<Repository>>(await streamTask);
```

<span data-ttu-id="eb7b7-205">Yeni ad alanları kullanıyorsunuz, bu yüzden dosyanın en üstüne de eklemeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="eb7b7-205">You're using new namespaces, so you'll need to add it at the top of the file as well:</span></span>

```csharp
using System.Collections.Generic;
using System.Text.Json;
```

<span data-ttu-id="eb7b7-206">Artık yerine kullandığınızdan emin olun <xref:System.Net.Http.HttpClient.GetStreamAsync(System.String)> <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)> .</span><span class="sxs-lookup"><span data-stu-id="eb7b7-206">Notice that you're now using <xref:System.Net.Http.HttpClient.GetStreamAsync(System.String)> instead of <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)>.</span></span> <span data-ttu-id="eb7b7-207">Serileştirici, kaynağı olarak bir dize yerine bir akış kullanır.</span><span class="sxs-lookup"><span data-stu-id="eb7b7-207">The serializer uses a stream instead of a string as its source.</span></span> <span data-ttu-id="eb7b7-208">Önceki kod parçacığının ikinci satırında kullanılmakta olan C# dilinin birkaç özelliği açıklanalım.</span><span class="sxs-lookup"><span data-stu-id="eb7b7-208">Let's explain a couple features of the C# language that are being used in the second line of the preceding code snippet.</span></span> <span data-ttu-id="eb7b7-209">İçin ilk bağımsız değişken <xref:System.Text.Json.JsonSerializer.DeserializeAsync%60%601(System.IO.Stream,System.Text.Json.JsonSerializerOptions,System.Threading.CancellationToken)?displayProperty=nameWithType> bir `await` ifadedir.</span><span class="sxs-lookup"><span data-stu-id="eb7b7-209">The first argument to <xref:System.Text.Json.JsonSerializer.DeserializeAsync%60%601(System.IO.Stream,System.Text.Json.JsonSerializerOptions,System.Threading.CancellationToken)?displayProperty=nameWithType> is an `await` expression.</span></span> <span data-ttu-id="eb7b7-210">(Diğer iki parametre isteğe bağlıdır ve kod parçacığında atlanır.) Await ifadeleri kodunuzda neredeyse her yerde görünebilir, ancak şu anda yalnızca bir atama bildiriminin parçası olarak gördünüz.</span><span class="sxs-lookup"><span data-stu-id="eb7b7-210">(The other two parameters are optional and are omitted in the code snippet.) Await expressions can appear almost anywhere in your code, even though up to now, you've only seen them as part of an assignment statement.</span></span> <span data-ttu-id="eb7b7-211">`Deserialize`Yöntemi *geneldir*, yani JSON metninde ne tür nesneler oluşturulması gerektiği için tür bağımsız değişkenleri sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="eb7b7-211">The `Deserialize` method is *generic*, which means you must supply type arguments for what kind of objects should be created from the JSON text.</span></span> <span data-ttu-id="eb7b7-212">Bu örnekte, `List<Repository>` başka bir genel nesne olan olan ' a bir tane olarak serisini halyorsunuz <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="eb7b7-212">In this example, you're deserializing to a `List<Repository>`, which is another generic object, the <xref:System.Collections.Generic.List%601?displayProperty=nameWithType>.</span></span> <span data-ttu-id="eb7b7-213">`List<>`Sınıfı bir nesne koleksiyonunu depolar.</span><span class="sxs-lookup"><span data-stu-id="eb7b7-213">The `List<>` class stores a collection of objects.</span></span> <span data-ttu-id="eb7b7-214">Tür bağımsız değişkeni içinde depolanan nesne türlerini bildirir `List<>` .</span><span class="sxs-lookup"><span data-stu-id="eb7b7-214">The type argument declares the type of objects stored in the `List<>`.</span></span> <span data-ttu-id="eb7b7-215">JSON metni, bir depo nesnesi koleksiyonunu temsil eder, bu nedenle tür bağımsız değişkeni olur `Repository` .</span><span class="sxs-lookup"><span data-stu-id="eb7b7-215">The JSON text represents a collection of repo objects, so the type argument is `Repository`.</span></span>

<span data-ttu-id="eb7b7-216">Bu bölümde neredeyse işiniz bitti.</span><span class="sxs-lookup"><span data-stu-id="eb7b7-216">You're almost done with this section.</span></span> <span data-ttu-id="eb7b7-217">JSON 'u C# nesnelerine dönüştürdüğüne göre, her deponun adını görüntülim.</span><span class="sxs-lookup"><span data-stu-id="eb7b7-217">Now that you've converted the JSON to C# objects, let's display the name of each repository.</span></span> <span data-ttu-id="eb7b7-218">Okunan satırları değiştirin:</span><span class="sxs-lookup"><span data-stu-id="eb7b7-218">Replace the lines that read:</span></span>

```csharp
var msg = await stringTask;   //**Deleted this
Console.Write(msg);
```

<span data-ttu-id="eb7b7-219">aşağıdakiler ile:</span><span class="sxs-lookup"><span data-stu-id="eb7b7-219">with the following:</span></span>

```csharp
foreach (var repo in repositories)
    Console.WriteLine(repo.name);
```

<span data-ttu-id="eb7b7-220">Uygulamayı derleyin ve çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="eb7b7-220">Compile and run the application.</span></span> <span data-ttu-id="eb7b7-221">.NET Foundation 'ın parçası olan Depoların adlarını yazdıracaktır.</span><span class="sxs-lookup"><span data-stu-id="eb7b7-221">It will print out the names of the repositories that are part of the .NET Foundation.</span></span>

## <a name="controlling-serialization"></a><span data-ttu-id="eb7b7-222">Serileştirme denetleniyor</span><span class="sxs-lookup"><span data-stu-id="eb7b7-222">Controlling Serialization</span></span>

<span data-ttu-id="eb7b7-223">Daha fazla özellik eklemeden önce `name` özniteliğini kullanarak özelliği ele alalım `[JsonPropertyName]` .</span><span class="sxs-lookup"><span data-stu-id="eb7b7-223">Before you add more features, let's address the `name` property by using the `[JsonPropertyName]` attribute.</span></span> <span data-ttu-id="eb7b7-224">Repo.cs içindeki alanın bildiriminde aşağıdaki değişiklikleri yapın `name` :</span><span class="sxs-lookup"><span data-stu-id="eb7b7-224">Make the following changes to the declaration of the `name` field in repo.cs:</span></span>

```csharp
[JsonPropertyName("name")]
public string Name { get; set; }
```

<span data-ttu-id="eb7b7-225">Özniteliğini kullanmak için `[JsonPropertyName]` , bu <xref:System.Text.Json.Serialization> ad alanını yönergelere eklemeniz gerekir `using` :</span><span class="sxs-lookup"><span data-stu-id="eb7b7-225">To use `[JsonPropertyName]` attribute, you will need to add the <xref:System.Text.Json.Serialization> namespace to the `using` directives:</span></span>

```csharp
using System.Text.Json.Serialization;
```

<span data-ttu-id="eb7b7-226">Bu değişiklik, program.cs içindeki her deponun adını yazan kodu değiştirmeniz gereken anlamına gelir:</span><span class="sxs-lookup"><span data-stu-id="eb7b7-226">This change means you need to change the code that writes the name of each repository in program.cs:</span></span>

```csharp
Console.WriteLine(repo.Name);
```

<span data-ttu-id="eb7b7-227">`dotnet run`Eşlemeleri doğru olduğundan emin olmak için yürütün.</span><span class="sxs-lookup"><span data-stu-id="eb7b7-227">Execute `dotnet run` to make sure you've got the mappings correct.</span></span> <span data-ttu-id="eb7b7-228">Önceki ile aynı çıktıyı görmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="eb7b7-228">You should see the same output as before.</span></span>

<span data-ttu-id="eb7b7-229">Yeni özellikler eklemeden önce bir değişiklik yapalim.</span><span class="sxs-lookup"><span data-stu-id="eb7b7-229">Let's make one more change before adding new features.</span></span> <span data-ttu-id="eb7b7-230">`ProcessRepositories`Yöntemi zaman uyumsuz çalışmayı yapabilir ve depoların bir koleksiyonunu döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="eb7b7-230">The `ProcessRepositories` method can do the async work and return a collection of the repositories.</span></span> <span data-ttu-id="eb7b7-231">`List<Repository>`Bu yöntemden ' ı dönelim ve bilgileri yöntemine yazan kodu taşıyalim `Main` .</span><span class="sxs-lookup"><span data-stu-id="eb7b7-231">Let's return the `List<Repository>` from that method, and move the code that writes the information into the `Main` method.</span></span>

<span data-ttu-id="eb7b7-232">`ProcessRepositories`Sonucunu bir nesne listesi olan bir görevi döndürmek için imzasını değiştirin `Repository` :</span><span class="sxs-lookup"><span data-stu-id="eb7b7-232">Change the signature of `ProcessRepositories` to return a task whose result is a list of `Repository` objects:</span></span>

```csharp
private static async Task<List<Repository>> ProcessRepositories()
```

<span data-ttu-id="eb7b7-233">Ardından, JSON yanıtını işledikten sonra depoları geri döndürün:</span><span class="sxs-lookup"><span data-stu-id="eb7b7-233">Then, just return the repositories after processing the JSON response:</span></span>

```csharp
var streamTask = client.GetStreamAsync("https://api.github.com/orgs/dotnet/repos");
var repositories = await JsonSerializer.DeserializeAsync<List<Repository>>(await streamTask);
return repositories;
```

<span data-ttu-id="eb7b7-234">`Task<T>`Bu yöntemi olarak işaretlediğiniz için derleyici, döndürme için nesnesi oluşturur `async` .</span><span class="sxs-lookup"><span data-stu-id="eb7b7-234">The compiler generates the `Task<T>` object for the return because you've marked this method as `async`.</span></span>
<span data-ttu-id="eb7b7-235">Ardından, `Main` yöntemi bu sonuçları yakalayıp, her depo adını konsola yazar şekilde değiştirelim.</span><span class="sxs-lookup"><span data-stu-id="eb7b7-235">Then, let's modify the `Main` method so that it captures those results and writes each repository name to the console.</span></span> <span data-ttu-id="eb7b7-236">`Main`Yönteminiz şu şekilde görünür:</span><span class="sxs-lookup"><span data-stu-id="eb7b7-236">Your `Main` method now looks like this:</span></span>

```csharp
public static async Task Main(string[] args)
{
    var repositories = await ProcessRepositories();

    foreach (var repo in repositories)
        Console.WriteLine(repo.Name);
}
```

## <a name="reading-more-information"></a><span data-ttu-id="eb7b7-237">Daha fazla bilgi okunuyor</span><span class="sxs-lookup"><span data-stu-id="eb7b7-237">Reading More Information</span></span>

<span data-ttu-id="eb7b7-238">Bu işlemi, GitHub API 'sinden gönderilen JSON paketindeki özelliklerden daha fazlasını işleyerek tamamlayalim.</span><span class="sxs-lookup"><span data-stu-id="eb7b7-238">Let's finish this by processing a few more of the properties in the JSON packet that gets sent from the GitHub API.</span></span> <span data-ttu-id="eb7b7-239">Her şeyi almak istemezsiniz, ancak birkaç özelliği eklemek C# dilinin daha fazla özelliği gösterir.</span><span class="sxs-lookup"><span data-stu-id="eb7b7-239">You won't want to grab everything, but adding a few properties will demonstrate a few more features of the C# language.</span></span>

<span data-ttu-id="eb7b7-240">Daha fazla basit türü `Repository` sınıf tanımına ekleyerek başlayalım.</span><span class="sxs-lookup"><span data-stu-id="eb7b7-240">Let's start by adding a few more simple types to the `Repository` class definition.</span></span> <span data-ttu-id="eb7b7-241">Bu özellikleri bu sınıfa ekleyin:</span><span class="sxs-lookup"><span data-stu-id="eb7b7-241">Add these properties to that class:</span></span>

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

<span data-ttu-id="eb7b7-242">Bu özellikler dize türünden (JSON paketlerinin içerdiği), hedef türüne yerleşik Dönüştürmelere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="eb7b7-242">These properties have built-in conversions from the string type (which is what the JSON packets contain) to the target type.</span></span> <span data-ttu-id="eb7b7-243"><xref:System.Uri>Tür sizin için yeni olabilir.</span><span class="sxs-lookup"><span data-stu-id="eb7b7-243">The <xref:System.Uri> type may be new to you.</span></span> <span data-ttu-id="eb7b7-244">Bir URI 'yi veya bu durumda bir URL 'yi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="eb7b7-244">It represents a URI, or in this case, a URL.</span></span> <span data-ttu-id="eb7b7-245">Ve türleri söz konusu olduğunda `Uri` `int` , JSON paketi hedef türüne Dönüştürülmeyen veriler içeriyorsa, serileştirme eylemi bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="eb7b7-245">In the case of the `Uri` and `int` types, if the JSON packet contains data that does not convert to the target type, the serialization action will throw an exception.</span></span>

<span data-ttu-id="eb7b7-246">Bunları ekledikten sonra, `Main` Bu öğeleri göstermek için yöntemini güncelleştirin:</span><span class="sxs-lookup"><span data-stu-id="eb7b7-246">Once you've added these, update the `Main` method to display those elements:</span></span>

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

<span data-ttu-id="eb7b7-247">Son bir adım olarak, son gönderme işlemi için bilgileri ekleyelim.</span><span class="sxs-lookup"><span data-stu-id="eb7b7-247">As a final step, let's add the information for the last push operation.</span></span> <span data-ttu-id="eb7b7-248">Bu bilgiler, JSON yanıtında bu biçimde biçimlendirilir:</span><span class="sxs-lookup"><span data-stu-id="eb7b7-248">This information is formatted in this fashion in the JSON response:</span></span>

```json
2016-02-08T21:27:00Z
```

<span data-ttu-id="eb7b7-249">Bu biçim Eşgüdümlü Evrensel Saat (UTC) biçiminde olduğundan, özelliği olan bir <xref:System.DateTime> değer alırsınız <xref:System.DateTime.Kind%2A> <xref:System.DateTimeKind.Utc> .</span><span class="sxs-lookup"><span data-stu-id="eb7b7-249">That format is in Coordinated Universal Time (UTC) so you'll get a <xref:System.DateTime> value whose <xref:System.DateTime.Kind%2A> property is <xref:System.DateTimeKind.Utc>.</span></span> <span data-ttu-id="eb7b7-250">Saat diliminizde temsil edilen bir tarihi tercih ediyorsanız, özel bir dönüştürme yöntemi yazmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="eb7b7-250">If you prefer a date represented in your time zone, you'll need to write a custom conversion method.</span></span> <span data-ttu-id="eb7b7-251">İlk olarak, `public` sınıfınızın tarih ve SAATININ UTC gösterimini `Repository` ve `LastPush` `readonly` yerel saate Dönüştürülecek tarihi döndüren bir özelliği tanımlar:</span><span class="sxs-lookup"><span data-stu-id="eb7b7-251">First, define a `public` property that will hold the UTC representation of the date and time in your `Repository` class and a `LastPush` `readonly` property that returns the date converted to local time:</span></span>

```csharp
[JsonPropertyName("pushed_at")]
public DateTime LastPushUtc { get; set; }

public DateTime LastPush => LastPushUtc.ToLocalTime();
```

<span data-ttu-id="eb7b7-252">Şimdi tanımladığımız yeni yapıları inceleyelim.</span><span class="sxs-lookup"><span data-stu-id="eb7b7-252">Let's go over the new constructs we just defined.</span></span> <span data-ttu-id="eb7b7-253">`LastPush`Özelliği, erişimci için *ifade-Bodied üyesi* kullanılarak tanımlanır `get` .</span><span class="sxs-lookup"><span data-stu-id="eb7b7-253">The `LastPush` property is defined using an *expression-bodied member* for the `get` accessor.</span></span> <span data-ttu-id="eb7b7-254">`set`Erişimci yok.</span><span class="sxs-lookup"><span data-stu-id="eb7b7-254">There is no `set` accessor.</span></span> <span data-ttu-id="eb7b7-255">`set`Erişimcinin atlanması, C# ' de *salt okunurdur* bir özelliği nasıl tanımlayacağınızı belirler.</span><span class="sxs-lookup"><span data-stu-id="eb7b7-255">Omitting the `set` accessor is how you define a *read-only* property in C#.</span></span> <span data-ttu-id="eb7b7-256">(Evet, C# dilinde *salt yazılır* özellikler oluşturabilirsiniz, ancak bunların değeri sınırlı olur.)</span><span class="sxs-lookup"><span data-stu-id="eb7b7-256">(Yes, you can create *write-only* properties in C#, but their value is limited.)</span></span>

<span data-ttu-id="eb7b7-257">Son olarak, konsolda bir çıkış bildirisi daha ekleyin ve bu uygulamayı yeniden oluşturup çalıştırmak için hazırsınız:</span><span class="sxs-lookup"><span data-stu-id="eb7b7-257">Finally, add one more output statement in the console, and you're ready to build and run this app again:</span></span>

```csharp
Console.WriteLine(repo.LastPush);
```

<span data-ttu-id="eb7b7-258">Sürümünüz artık [tamamlanmış örnekle](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient)eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="eb7b7-258">Your version should now match the [finished sample](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient).</span></span>

## <a name="conclusion"></a><span data-ttu-id="eb7b7-259">Sonuç</span><span class="sxs-lookup"><span data-stu-id="eb7b7-259">Conclusion</span></span>

<span data-ttu-id="eb7b7-260">Bu öğretici, Web istekleri oluşturma, sonucu ayrıştırma ve bu sonuçların özelliklerini görüntüleme konusunda sizi gösterdi.</span><span class="sxs-lookup"><span data-stu-id="eb7b7-260">This tutorial showed you how to make web requests, parse the result, and display properties of those results.</span></span> <span data-ttu-id="eb7b7-261">Ayrıca, yeni paketleri projenize bağımlılıklar olarak eklediniz.</span><span class="sxs-lookup"><span data-stu-id="eb7b7-261">You've also added new packages as dependencies in your project.</span></span> <span data-ttu-id="eb7b7-262">Nesne odaklı teknikleri destekleyen C# dilinin bazı özelliklerini gördünüz.</span><span class="sxs-lookup"><span data-stu-id="eb7b7-262">You've seen some of the features of the C# language that support object-oriented techniques.</span></span>

<a name="dotnet-restore-note"></a>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
