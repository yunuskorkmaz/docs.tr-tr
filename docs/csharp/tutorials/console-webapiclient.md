---
title: .NET Core'u kullanarak BIR REST istemcisi oluşturma
description: Bu öğretici size .NET Core ve C# dillerinde bir dizi özellik öğretir.
ms.date: 01/09/2020
ms.assetid: 51033ce2-7a53-4cdd-966d-9da15c8204d2
ms.openlocfilehash: 5796df2d2fd8c4d9aaca783d720448c90858c067
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79156863"
---
# <a name="rest-client"></a><span data-ttu-id="88c75-103">REST istemcisi</span><span class="sxs-lookup"><span data-stu-id="88c75-103">REST client</span></span>

<span data-ttu-id="88c75-104">Bu öğretici size .NET Core ve C# dillerinde bir dizi özellik öğretir.</span><span class="sxs-lookup"><span data-stu-id="88c75-104">This tutorial teaches you a number of features in .NET Core and the C# language.</span></span> <span data-ttu-id="88c75-105">Öğreneceksin:</span><span class="sxs-lookup"><span data-stu-id="88c75-105">You’ll learn:</span></span>

* <span data-ttu-id="88c75-106">.NET Core CLI'nin temelleri.</span><span class="sxs-lookup"><span data-stu-id="88c75-106">The basics of the .NET Core CLI.</span></span>
* <span data-ttu-id="88c75-107">C# Language özelliklerine genel bakış.</span><span class="sxs-lookup"><span data-stu-id="88c75-107">An overview of C# Language features.</span></span>
* <span data-ttu-id="88c75-108">NuGet ile bağımlılıkları yönetme</span><span class="sxs-lookup"><span data-stu-id="88c75-108">Managing dependencies with NuGet</span></span>
* <span data-ttu-id="88c75-109">HTTP İletişim</span><span class="sxs-lookup"><span data-stu-id="88c75-109">HTTP Communications</span></span>
* <span data-ttu-id="88c75-110">JSON bilgilerinin işlenmesi</span><span class="sxs-lookup"><span data-stu-id="88c75-110">Processing JSON information</span></span>
* <span data-ttu-id="88c75-111">Yapılandırmayı Özniteliklerle yönetme.</span><span class="sxs-lookup"><span data-stu-id="88c75-111">Managing configuration with Attributes.</span></span>

<span data-ttu-id="88c75-112">GitHub'daki bir REST hizmetine HTTP İstekleri veren bir uygulama oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="88c75-112">You’ll build an application that issues HTTP Requests to a REST service on GitHub.</span></span> <span data-ttu-id="88c75-113">Bilgileri JSON formatında okuyacak ve bu JSON paketini C# nesnelerine dönüştüreceksiniz.</span><span class="sxs-lookup"><span data-stu-id="88c75-113">You'll read information in JSON format, and convert that JSON packet into C# objects.</span></span> <span data-ttu-id="88c75-114">Son olarak, C# nesneleri ile nasıl çalışacağınızı görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="88c75-114">Finally, you'll see how to work with C# objects.</span></span>

<span data-ttu-id="88c75-115">Bu öğretici birçok özelliği vardır.</span><span class="sxs-lookup"><span data-stu-id="88c75-115">There are many features in this tutorial.</span></span> <span data-ttu-id="88c75-116">Onları teker teker inşa edelim.</span><span class="sxs-lookup"><span data-stu-id="88c75-116">Let’s build them one by one.</span></span>

<span data-ttu-id="88c75-117">Bu konu için son [örnekle](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient) birlikte takip etmeyi tercih ederseniz, indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="88c75-117">If you prefer to follow along with the [final sample](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient) for this topic, you can download it.</span></span> <span data-ttu-id="88c75-118">İndirme talimatları için [Örnekler ve Öğreticiler'e](../../samples-and-tutorials/index.md#viewing-and-downloading-samples)bakın.</span><span class="sxs-lookup"><span data-stu-id="88c75-118">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="88c75-119">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="88c75-119">Prerequisites</span></span>

<span data-ttu-id="88c75-120">.NET çekirdeğini çalıştırmak için makinenizi ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="88c75-120">You’ll need to set up your machine to run .NET core.</span></span> <span data-ttu-id="88c75-121">Yükleme yönergelerini [.NET Çekirdek İndirmeler](https://dotnet.microsoft.com/download) sayfasında bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="88c75-121">You can find the installation instructions on the [.NET Core Downloads](https://dotnet.microsoft.com/download) page.</span></span> <span data-ttu-id="88c75-122">Bu uygulamayı Windows, Linux, macOS veya Docker kapsayıcısında çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="88c75-122">You can run this application on Windows, Linux, macOS or in a Docker container.</span></span>
<span data-ttu-id="88c75-123">En sevdiğiniz kod düzenleyicisini yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="88c75-123">You’ll need to install your favorite code editor.</span></span> <span data-ttu-id="88c75-124">Aşağıdaki açıklamalar, açık kaynak kodlu, çapraz platform düzenleyicisi olan [Visual Studio Code'u](https://code.visualstudio.com/)kullanabilmiştir.</span><span class="sxs-lookup"><span data-stu-id="88c75-124">The descriptions below use [Visual Studio Code](https://code.visualstudio.com/), which is an open source, cross platform editor.</span></span> <span data-ttu-id="88c75-125">Ancak, hangi araçları ile rahat kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="88c75-125">However, you can use whatever tools you are comfortable with.</span></span>

## <a name="create-the-application"></a><span data-ttu-id="88c75-126">Uygulamayı Oluştur</span><span class="sxs-lookup"><span data-stu-id="88c75-126">Create the Application</span></span>

<span data-ttu-id="88c75-127">İlk adım yeni bir uygulama oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="88c75-127">The first step is to create a new application.</span></span> <span data-ttu-id="88c75-128">Bir komut istemi açın ve uygulamanız için yeni bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="88c75-128">Open a command prompt and create a new directory for your application.</span></span> <span data-ttu-id="88c75-129">Bunu geçerli dizini yapın.</span><span class="sxs-lookup"><span data-stu-id="88c75-129">Make that the current directory.</span></span> <span data-ttu-id="88c75-130">Konsol penceresine aşağıdaki komutu girin:</span><span class="sxs-lookup"><span data-stu-id="88c75-130">Enter the following command in a console window:</span></span>

```dotnetcli
dotnet new console --name WebApiClient
```

<span data-ttu-id="88c75-131">Bu, temel bir "Hello World" uygulaması için başlangıç dosyalarını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="88c75-131">This creates the starter files for a basic "Hello World" application.</span></span> <span data-ttu-id="88c75-132">Proje adı "WebApiClient"dır.</span><span class="sxs-lookup"><span data-stu-id="88c75-132">The project name is "WebApiClient".</span></span> <span data-ttu-id="88c75-133">Bu yeni bir proje olduğu için, bağımlılıkların hiçbiri yerinde değildir.</span><span class="sxs-lookup"><span data-stu-id="88c75-133">As this is a new project, none of the dependencies are in place.</span></span> <span data-ttu-id="88c75-134">İlk çalıştırma .NET Core çerçevesini karşıdan yükler, geliştirme sertifikası yükler ve eksik bağımlılıkları geri yüklemek için NuGet paket yöneticisini çalıştıracaktır.</span><span class="sxs-lookup"><span data-stu-id="88c75-134">The first run will download the .NET Core framework, install a development certificate, and run the NuGet package manager to restore missing dependencies.</span></span>

<span data-ttu-id="88c75-135">Değişiklik yapmaya başlamadan önce, `dotnet run` uygulamanızı çalıştırmak için komut istemine[(nota bakınız)](#dotnet-restore-note)yazın.</span><span class="sxs-lookup"><span data-stu-id="88c75-135">Before you start making modifications, type `dotnet run` ([see note](#dotnet-restore-note)) at the command prompt to run your application.</span></span> <span data-ttu-id="88c75-136">`dotnet run`ortamınız `dotnet restore` bağımlılıkları eksikse otomatik olarak gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="88c75-136">`dotnet run` automatically performs `dotnet restore` if your environment is missing dependencies.</span></span> <span data-ttu-id="88c75-137">Uygulamanızın `dotnet build` yeniden oluşturulması gerekiyorsa da gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="88c75-137">It also performs `dotnet build` if your application needs to be rebuilt.</span></span>
<span data-ttu-id="88c75-138">İlk kurulumunuzdan sonra, yalnızca `dotnet restore` çalıştırmanız veya projeniz için anlamlı `dotnet build` olduğunda yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="88c75-138">After your initial setup, you will only need to run `dotnet restore` or `dotnet build` when it makes sense for your project.</span></span>

## <a name="adding-new-dependencies"></a><span data-ttu-id="88c75-139">Yeni Bağımlılıklar Ekleme</span><span class="sxs-lookup"><span data-stu-id="88c75-139">Adding New Dependencies</span></span>

<span data-ttu-id="88c75-140">.NET Core'un temel tasarım hedeflerinden biri .NET yüklemesinin boyutunu en aza indirmektir.</span><span class="sxs-lookup"><span data-stu-id="88c75-140">One of the key design goals for .NET Core is to minimize the size of the .NET installation.</span></span> <span data-ttu-id="88c75-141">Bir uygulamanın bazı özellikleri için ek kitaplıklara ihtiyacı varsa, bu\*bağımlılıkları C# projenize (.csproj) dosyanıza eklersiniz.</span><span class="sxs-lookup"><span data-stu-id="88c75-141">If an application needs additional libraries for some of its features, you add those dependencies into your C# project (\*.csproj) file.</span></span> <span data-ttu-id="88c75-142">Örneğin, uygulamanızın JSON yanıtlarını `System.Runtime.Serialization.Json` işleme sayılabilmesi için paketi eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="88c75-142">For our example, you'll need to add the `System.Runtime.Serialization.Json` package, so your application can process JSON responses.</span></span>

<span data-ttu-id="88c75-143">Bu uygulama için `System.Runtime.Serialization.Json` pakete ihtiyacınız olacak.</span><span class="sxs-lookup"><span data-stu-id="88c75-143">You'll need the `System.Runtime.Serialization.Json` package for this application.</span></span> <span data-ttu-id="88c75-144">Aşağıdaki [.NET CLI](../../core/tools/dotnet-add-package.md) komutunu çalıştırarak projenize ekleyin:</span><span class="sxs-lookup"><span data-stu-id="88c75-144">Add it to your project by running the following [.NET CLI](../../core/tools/dotnet-add-package.md) command:</span></span>

```dotnetcli
dotnet add package System.Text.Json
```

## <a name="making-web-requests"></a><span data-ttu-id="88c75-145">Web İstekleri Yapma</span><span class="sxs-lookup"><span data-stu-id="88c75-145">Making Web Requests</span></span>

<span data-ttu-id="88c75-146">Artık web'den veri almaya başlamaya hazırsınız.</span><span class="sxs-lookup"><span data-stu-id="88c75-146">Now you're ready to start retrieving data from the web.</span></span> <span data-ttu-id="88c75-147">Bu uygulamada, [GitHub API'sinden](https://developer.github.com/v3/)gelen bilgileri okuyacaksınız.</span><span class="sxs-lookup"><span data-stu-id="88c75-147">In this application, you'll read information from the [GitHub API](https://developer.github.com/v3/).</span></span> <span data-ttu-id="88c75-148">[.NET Foundation](https://www.dotnetfoundation.org/) şemsiyesi altındaki projelerle ilgili bilgileri okuyalım.</span><span class="sxs-lookup"><span data-stu-id="88c75-148">Let's read information about the projects under the [.NET Foundation](https://www.dotnetfoundation.org/) umbrella.</span></span> <span data-ttu-id="88c75-149">Projeler hakkında bilgi almak için GitHub API'sine istekte bulunarak işe başlarsınız.</span><span class="sxs-lookup"><span data-stu-id="88c75-149">You'll start by making the request to the GitHub API to retrieve information on the projects.</span></span> <span data-ttu-id="88c75-150">Kullanacağınız bitiş noktası: <https://api.github.com/orgs/dotnet/repos>.</span><span class="sxs-lookup"><span data-stu-id="88c75-150">The endpoint you'll use is: <https://api.github.com/orgs/dotnet/repos>.</span></span> <span data-ttu-id="88c75-151">Bu projelerle ilgili tüm bilgileri almak istediğinizden, http get isteği kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="88c75-151">You want to retrieve all the information about these projects, so you'll use an HTTP GET request.</span></span>
<span data-ttu-id="88c75-152">Tarayıcınız http get isteklerini de kullanır, böylece hangi bilgileri alacağınızı ve işlediğinizi görmek için bu URL'yi tarayıcınıza yapıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="88c75-152">Your browser also uses HTTP GET requests, so you can paste that URL into your browser to see what information you'll be receiving and processing.</span></span>

<span data-ttu-id="88c75-153"><xref:System.Net.Http.HttpClient> Web istekleri yapmak için sınıfı kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="88c75-153">You use the <xref:System.Net.Http.HttpClient> class to make web requests.</span></span> <span data-ttu-id="88c75-154">Tüm modern .NET API'leri gibi, <xref:System.Net.Http.HttpClient> uzun süredir devam eden API'leri için yalnızca uyumlu yöntemleri destekler.</span><span class="sxs-lookup"><span data-stu-id="88c75-154">Like all modern .NET APIs, <xref:System.Net.Http.HttpClient> supports only async methods for its long-running APIs.</span></span>
<span data-ttu-id="88c75-155">Bir async yöntemi yaparak başlayın.</span><span class="sxs-lookup"><span data-stu-id="88c75-155">Start by making an async method.</span></span> <span data-ttu-id="88c75-156">Uygulamanın işlevselliğini oluştururken uygulamayı doldurursunuz.</span><span class="sxs-lookup"><span data-stu-id="88c75-156">You'll fill in the implementation as you build the functionality of the application.</span></span> <span data-ttu-id="88c75-157">Proje dizininizdeki dosyayı `program.cs` açarak ve `Program` sınıfa aşağıdaki yöntemi ekleyerek başlayın:</span><span class="sxs-lookup"><span data-stu-id="88c75-157">Start by opening the `program.cs` file in your project directory and adding the following method to the `Program` class:</span></span>

```csharp
private static async Task ProcessRepositories()
{
}
```

<span data-ttu-id="88c75-158">C# derleyicisinin `using` <xref:System.Threading.Tasks.Task> türünü tanıması için `Main` yönteminizin en üstüne bir yönerge eklemeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="88c75-158">You'll need to add a `using` directive at the top of your `Main` method so that the C# compiler recognizes the <xref:System.Threading.Tasks.Task> type:</span></span>

```csharp
using System.Threading.Tasks;
```

<span data-ttu-id="88c75-159">Bu noktada projenizi oluşturursanız, herhangi `await` bir işleç içermediğinden ve eşzamanlı olarak çalışacağından, bu yöntem için oluşturulan bir uyarı alırsınız.</span><span class="sxs-lookup"><span data-stu-id="88c75-159">If you build your project at this point, you'll get a warning generated for this method, because it does not contain any `await` operators and will run synchronously.</span></span> <span data-ttu-id="88c75-160">Bunu şimdilik görmezden gelin; yöntemi doldururken `await` işleçler eklersiniz.</span><span class="sxs-lookup"><span data-stu-id="88c75-160">Ignore that for now; you'll add `await` operators as you fill in the method.</span></span>

<span data-ttu-id="88c75-161">Ardından, `namespace` ifadede tanımlanan ad alanını varsayılanından `ConsoleApp` ' `WebAPIClient`' a yeniden adlandırın</span><span class="sxs-lookup"><span data-stu-id="88c75-161">Next, rename the namespace defined in the `namespace` statement from its default of `ConsoleApp` to `WebAPIClient`.</span></span> <span data-ttu-id="88c75-162">Daha sonra bu `repo` ad alanında bir sınıf tanımlayacağız.</span><span class="sxs-lookup"><span data-stu-id="88c75-162">We'll later define a `repo` class in this namespace.</span></span>

<span data-ttu-id="88c75-163">Ardından, bu `Main` yöntemi çağırmak için yöntemi güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="88c75-163">Next, update the `Main` method to call this method.</span></span> <span data-ttu-id="88c75-164">Yöntem `ProcessRepositories` bir görevi döndürür ve bu görev bitmeden programdan çıkmamalısınız.</span><span class="sxs-lookup"><span data-stu-id="88c75-164">The `ProcessRepositories` method returns a task, and you shouldn't exit the program before that task finishes.</span></span> <span data-ttu-id="88c75-165">Bu nedenle, imzayı `Main`değiştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="88c75-165">Therefore, you must change the signature of `Main`.</span></span> <span data-ttu-id="88c75-166">`async` Değiştiriciyi ekleyin ve dönüş türünü `Task`' le değiştirin</span><span class="sxs-lookup"><span data-stu-id="88c75-166">Add the `async` modifier, and change the return type to `Task`.</span></span> <span data-ttu-id="88c75-167">Daha sonra, yöntemin gövdesinde, bir `ProcessRepositories`çağrı ekleyin.</span><span class="sxs-lookup"><span data-stu-id="88c75-167">Then, in the body of the method, add a call to `ProcessRepositories`.</span></span> <span data-ttu-id="88c75-168">Bu `await` yöntem çağrısına anahtar kelime ekleyin:</span><span class="sxs-lookup"><span data-stu-id="88c75-168">Add the `await` keyword to that method call:</span></span>

```csharp
static async Task Main(string[] args)
{
    await ProcessRepositories();
}
```

<span data-ttu-id="88c75-169">Şimdi, hiçbir şey yapmaz bir program var, ama eşzamanlı yok.</span><span class="sxs-lookup"><span data-stu-id="88c75-169">Now, you have a program that does nothing, but does it asynchronously.</span></span> <span data-ttu-id="88c75-170">Hadi geliştirelim.</span><span class="sxs-lookup"><span data-stu-id="88c75-170">Let's improve it.</span></span>

<span data-ttu-id="88c75-171">İlk olarak web'den veri alabilen bir nesneye ihtiyacınız vardır; bunu yapmak <xref:System.Net.Http.HttpClient> için a kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="88c75-171">First you need an object that is capable to retrieve data from the web; you can use a <xref:System.Net.Http.HttpClient> to do that.</span></span> <span data-ttu-id="88c75-172">Bu nesne isteği ve yanıtları işler.</span><span class="sxs-lookup"><span data-stu-id="88c75-172">This object handles the request and the responses.</span></span> <span data-ttu-id="88c75-173">`Program` *Program.cs* dosyasının içindeki sınıfta bu tür tek bir örneği anında seçin.</span><span class="sxs-lookup"><span data-stu-id="88c75-173">Instantiate a single instance of that type in the `Program` class inside the *Program.cs* file.</span></span>

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

<span data-ttu-id="88c75-174">Yönteme `ProcessRepositories` geri dönelim ve ilk sürümünü dolduralım:</span><span class="sxs-lookup"><span data-stu-id="88c75-174">Let's go back to the `ProcessRepositories` method and fill in a first version of it:</span></span>

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

<span data-ttu-id="88c75-175">Bunun derlemesi için dosyanın en üstüne iki yeni `using` yönerge eklemeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="88c75-175">You'll need to also add two new `using` directives at the top of the file for this to compile:</span></span>

```csharp
using System.Net.Http;
using System.Net.Http.Headers;
```

<span data-ttu-id="88c75-176">Bu ilk sürüm, dotnet vakıf kuruluşu altındaki tüm depoların listesini okumak için bir web isteği yapar.</span><span class="sxs-lookup"><span data-stu-id="88c75-176">This first version makes a web request to read the list of all repositories under the dotnet foundation organization.</span></span> <span data-ttu-id="88c75-177">(.NET Foundation için gitHub kimliği 'dotnet'tir).</span><span class="sxs-lookup"><span data-stu-id="88c75-177">(The gitHub ID for the .NET Foundation is 'dotnet').</span></span> <span data-ttu-id="88c75-178">İlk birkaç satır bu <xref:System.Net.Http.HttpClient> istek için ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="88c75-178">The first few lines set up the <xref:System.Net.Http.HttpClient> for this request.</span></span> <span data-ttu-id="88c75-179">İlk olarak, GitHub JSON yanıtlarını kabul etmek üzere yapılandırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="88c75-179">First, it is configured to accept the GitHub JSON responses.</span></span>
<span data-ttu-id="88c75-180">Bu biçim sadece JSON olduğunu.</span><span class="sxs-lookup"><span data-stu-id="88c75-180">This format is simply JSON.</span></span> <span data-ttu-id="88c75-181">Sonraki satır, bu nesneden gelen tüm isteklere bir Kullanıcı Aracısı üstbilgisi ekler.</span><span class="sxs-lookup"><span data-stu-id="88c75-181">The next line adds a User Agent header to all requests from this object.</span></span> <span data-ttu-id="88c75-182">Bu iki üstbilgi GitHub sunucu kodu tarafından denetlenir ve GitHub'dan bilgi almak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="88c75-182">These two headers are checked by the GitHub server code, and are necessary to retrieve information from GitHub.</span></span>

<span data-ttu-id="88c75-183">Yapılandırıldıktan <xref:System.Net.Http.HttpClient>sonra bir web isteği yapar ve yanıtı alırsınız.</span><span class="sxs-lookup"><span data-stu-id="88c75-183">After you've configured the <xref:System.Net.Http.HttpClient>, you make a web request and retrieve the response.</span></span> <span data-ttu-id="88c75-184">Bu ilk sürümde, <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)?displayProperty=nameWithType> kolaylık yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="88c75-184">In this first version, you use the <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)?displayProperty=nameWithType> convenience method.</span></span> <span data-ttu-id="88c75-185">Bu kolaylık yöntemi, web isteği yapan bir görev başlatır ve istek döndüğünde yanıt akışını okur ve içeriği akıştan ayıklar.</span><span class="sxs-lookup"><span data-stu-id="88c75-185">This convenience method starts a task that makes the web request, and then when the request returns, it reads the response stream and extracts the content from the stream.</span></span> <span data-ttu-id="88c75-186">Yanıtın gövdesi bir <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="88c75-186">The body of the response is returned as a <xref:System.String>.</span></span> <span data-ttu-id="88c75-187">Görev tamamlandığında dize kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="88c75-187">The string is available when the task completes.</span></span>

<span data-ttu-id="88c75-188">Bu yöntemin son iki satırı bu görevi bekliyor ve ardından yanıtı konsola yazdırın.</span><span class="sxs-lookup"><span data-stu-id="88c75-188">The final two lines of this method await that task, and then print the response to the console.</span></span>
<span data-ttu-id="88c75-189">Uygulamayı oluşturun ve çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="88c75-189">Build the app, and run it.</span></span> <span data-ttu-id="88c75-190">Şimdi bir `ProcessRepositories` `await` işleç içerdiğinden, yapı uyarısı artık gitti.</span><span class="sxs-lookup"><span data-stu-id="88c75-190">The build warning is gone now, because the `ProcessRepositories` now does contain an `await` operator.</span></span> <span data-ttu-id="88c75-191">JSON biçimlendirilmiş metnin uzun bir ekranını görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="88c75-191">You'll see a long display of JSON formatted text.</span></span>

## <a name="processing-the-json-result"></a><span data-ttu-id="88c75-192">JSON Sonucunun İşlenmesi</span><span class="sxs-lookup"><span data-stu-id="88c75-192">Processing the JSON Result</span></span>

<span data-ttu-id="88c75-193">Bu noktada, bir web sunucusundan yanıt almak ve bu yanıtta bulunan metni görüntülemek için kodu yazdınız.</span><span class="sxs-lookup"><span data-stu-id="88c75-193">At this point, you've written the code to retrieve a response from a web server, and display the text that is contained in that response.</span></span> <span data-ttu-id="88c75-194">Sonra, bu JSON yanıtını C# nesnelerine dönüştürelim.</span><span class="sxs-lookup"><span data-stu-id="88c75-194">Next, let's convert that JSON response into C# objects.</span></span>

<span data-ttu-id="88c75-195">Sınıf <xref:System.Text.Json.JsonSerializer?displayProperty=nameWithType> nesneleri JSON'a serileştirir ve JSON'u nesnelere ayırıyor.</span><span class="sxs-lookup"><span data-stu-id="88c75-195">The <xref:System.Text.Json.JsonSerializer?displayProperty=nameWithType> class serializes objects to JSON and deserializes JSON into objects.</span></span> <span data-ttu-id="88c75-196">GitHub API'sinden döndürülen JSON nesnesini `repo` temsil edecek bir sınıf tanımlayarak başlayın:</span><span class="sxs-lookup"><span data-stu-id="88c75-196">Start by defining a class to represent the `repo` JSON object returned from the GitHub API:</span></span>

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

<span data-ttu-id="88c75-197">Yukarıdaki kodu 'repo.cs' adlı yeni bir dosyaya koyun.</span><span class="sxs-lookup"><span data-stu-id="88c75-197">Put the above code in a new file called 'repo.cs'.</span></span> <span data-ttu-id="88c75-198">Sınıfın bu sürümü JSON verilerini işlemek için en basit yolu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="88c75-198">This version of the class represents the simplest path to process JSON data.</span></span> <span data-ttu-id="88c75-199">Sınıf adı ve üye adı, C# kurallarını takip etmek yerine JSON paketinde kullanılan adlarla eşleşir.</span><span class="sxs-lookup"><span data-stu-id="88c75-199">The class name and the member name match the names used in the JSON packet, instead of following C# conventions.</span></span> <span data-ttu-id="88c75-200">Bunu daha sonra bazı yapılandırma öznitelikleri sağlayarak düzelteceksiniz.</span><span class="sxs-lookup"><span data-stu-id="88c75-200">You'll fix that by providing some configuration attributes later.</span></span> <span data-ttu-id="88c75-201">Bu sınıf JSON serileştirme ve deserialization başka önemli bir özelliği gösterir: JSON paketindeki tüm alanlar bu sınıfın bir parçası değildir.</span><span class="sxs-lookup"><span data-stu-id="88c75-201">This class demonstrates another important feature of JSON serialization and deserialization: Not all the fields in the JSON packet are part of this class.</span></span>
<span data-ttu-id="88c75-202">JSON serileştiricisi, kullanılan sınıf türüne dahil olmayan bilgileri yoksayacaktır.</span><span class="sxs-lookup"><span data-stu-id="88c75-202">The JSON serializer will ignore information that is not included in the class type being used.</span></span>
<span data-ttu-id="88c75-203">Bu özellik, JSON paketindeki alanların yalnızca bir alt kümesiyle çalışan türler oluşturmayı kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="88c75-203">This feature makes it easier to create types that work with only a subset of the fields in the JSON packet.</span></span>

<span data-ttu-id="88c75-204">Şimdi türü oluşturduğunuza göre, onu deserialize edelim.</span><span class="sxs-lookup"><span data-stu-id="88c75-204">Now that you've created the type, let's deserialize it.</span></span>

<span data-ttu-id="88c75-205">Daha sonra, JSON'u C# nesnelerine dönüştürmek için serileştiriciyi kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="88c75-205">Next, you'll use the serializer to convert JSON into C# objects.</span></span> <span data-ttu-id="88c75-206">Aramayı <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)> yönteminizde `ProcessRepositories` aşağıdaki üç satırla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="88c75-206">Replace the call to <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)> in your `ProcessRepositories` method with the following three lines:</span></span>

```csharp
var streamTask = client.GetStreamAsync("https://api.github.com/orgs/dotnet/repos");
var repositories = await JsonSerializer.DeserializeAsync<List<Repository>>(await streamTask);
```

<span data-ttu-id="88c75-207">Yeni bir ad alanı kullanıyorsanız, bu nedenle dosyanın en üstüne de eklemeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="88c75-207">You're using a new namespace, so you'll need to add it at the top of the file as well:</span></span>

```csharp
using System.Text.Json;
```

<span data-ttu-id="88c75-208">Şimdi yerine kullandığınıza <xref:System.Net.Http.HttpClient.GetStreamAsync(System.String)> dikkat <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)>edin.</span><span class="sxs-lookup"><span data-stu-id="88c75-208">Notice that you're now using <xref:System.Net.Http.HttpClient.GetStreamAsync(System.String)> instead of <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)>.</span></span> <span data-ttu-id="88c75-209">Serializer kaynağı olarak bir dize yerine bir akış kullanır.</span><span class="sxs-lookup"><span data-stu-id="88c75-209">The serializer uses a stream instead of a string as its source.</span></span> <span data-ttu-id="88c75-210">Önceki kod snippet'in ikinci satırında kullanılan C# dilinin birkaç özelliğini açıklayalım.</span><span class="sxs-lookup"><span data-stu-id="88c75-210">Let's explain a couple features of the C# language that are being used in the second line of the preceding code snippet.</span></span> <span data-ttu-id="88c75-211">İlk bağımsız <xref:System.Text.Json.JsonSerializer.DeserializeAsync%60%601(System.IO.Stream,System.Text.Json.JsonSerializerOptions,System.Threading.CancellationToken)?displayProperty=nameWithType> değişken `await` bir ifadedir.</span><span class="sxs-lookup"><span data-stu-id="88c75-211">The first argument to <xref:System.Text.Json.JsonSerializer.DeserializeAsync%60%601(System.IO.Stream,System.Text.Json.JsonSerializerOptions,System.Threading.CancellationToken)?displayProperty=nameWithType> is an `await` expression.</span></span> <span data-ttu-id="88c75-212">(Diğer iki parametre isteğe bağlıdır ve kod snippet atlanır.) Bekleyen ifadeler, şimdiye kadar bunları yalnızca atama deyiminin bir parçası olarak görmüş olsanız bile, kodunuzda hemen hemen her yerde görünebilir.</span><span class="sxs-lookup"><span data-stu-id="88c75-212">(The other two parameters are optional and are omitted in the code snippet.) Await expressions can appear almost anywhere in your code, even though up to now, you've only seen them as part of an assignment statement.</span></span> <span data-ttu-id="88c75-213">Yöntem `Deserialize` *geneldir,* bu da JSON metninden ne tür nesnelerin oluşturulması gerektiğine yönelik tür bağımsız değişkenleri sağlamanız gerektiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="88c75-213">The `Deserialize` method is *generic*, which means you must supply type arguments for what kind of objects should be created from the JSON text.</span></span> <span data-ttu-id="88c75-214">Bu örnekte, başka bir genel `List<Repository>`nesne olan bir , <xref:System.Collections.Generic.List%601?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="88c75-214">In this example, you're deserializing to a `List<Repository>`, which is another generic object, the <xref:System.Collections.Generic.List%601?displayProperty=nameWithType>.</span></span> <span data-ttu-id="88c75-215">Sınıf `List<>` nesnelerin bir koleksiyon depolar.</span><span class="sxs-lookup"><span data-stu-id="88c75-215">The `List<>` class stores a collection of objects.</span></span> <span data-ttu-id="88c75-216">Tür bağımsız `List<>`değişkeni, .</span><span class="sxs-lookup"><span data-stu-id="88c75-216">The type argument declares the type of objects stored in the `List<>`.</span></span> <span data-ttu-id="88c75-217">JSON metni repo nesnelerinin bir koleksiyonunu temsil eder, bu nedenle tür bağımsız değişkeni `Repository`.</span><span class="sxs-lookup"><span data-stu-id="88c75-217">The JSON text represents a collection of repo objects, so the type argument is `Repository`.</span></span>

<span data-ttu-id="88c75-218">Bu bölümü neredeyse bitirdin.</span><span class="sxs-lookup"><span data-stu-id="88c75-218">You're almost done with this section.</span></span> <span data-ttu-id="88c75-219">Artık JSON'u C# nesnelerine dönüştürdüğünüze göre, her deponun adını gösterelim.</span><span class="sxs-lookup"><span data-stu-id="88c75-219">Now that you've converted the JSON to C# objects, let's display the name of each repository.</span></span> <span data-ttu-id="88c75-220">Aşağıdaki satırları değiştirin:</span><span class="sxs-lookup"><span data-stu-id="88c75-220">Replace the lines that read:</span></span>

```csharp
var msg = await stringTask;   //**Deleted this
Console.Write(msg);
```

<span data-ttu-id="88c75-221">aşağıdakilerle birlikte:</span><span class="sxs-lookup"><span data-stu-id="88c75-221">with the following:</span></span>

```csharp
foreach (var repo in repositories)
    Console.WriteLine(repo.name);
```

<span data-ttu-id="88c75-222">Uygulamayı derle ve çalıştır.</span><span class="sxs-lookup"><span data-stu-id="88c75-222">Compile and run the application.</span></span> <span data-ttu-id="88c75-223">.NET Foundation'ın bir parçası olan depoların adlarını yazdırır.</span><span class="sxs-lookup"><span data-stu-id="88c75-223">It will print out the names of the repositories that are part of the .NET Foundation.</span></span>

## <a name="controlling-serialization"></a><span data-ttu-id="88c75-224">Serileştirmeyi Denetleme</span><span class="sxs-lookup"><span data-stu-id="88c75-224">Controlling Serialization</span></span>

<span data-ttu-id="88c75-225">Daha fazla özellik eklemeden önce, `name` özniteliği `[JsonPropertyName]` kullanarak özelliği ele alalım.</span><span class="sxs-lookup"><span data-stu-id="88c75-225">Before you add more features, let's address the `name` property by using the `[JsonPropertyName]` attribute.</span></span> <span data-ttu-id="88c75-226">repo.cs alan bildiriminde `name` aşağıdaki değişiklikleri yapın:</span><span class="sxs-lookup"><span data-stu-id="88c75-226">Make the following changes to the declaration of the `name` field in repo.cs:</span></span>

```csharp
[JsonPropertyName("name")]
public string Name { get; set; }
```

<span data-ttu-id="88c75-227">Öznitelik `[JsonPropertyName]` kullanmak `using` için, yönergelere <xref:System.Text.Json.Serialization> ad alanı eklemeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="88c75-227">To use `[JsonPropertyName]` attribute, you will need to add the <xref:System.Text.Json.Serialization> namespace to the `using` directives:</span></span>

```csharp
using System.Text.Json.Serialization;
```

<span data-ttu-id="88c75-228">Bu değişiklik, program.cs her deponun adını yazan kodu değiştirmeniz gerektiği anlamına gelir:</span><span class="sxs-lookup"><span data-stu-id="88c75-228">This change means you need to change the code that writes the name of each repository in program.cs:</span></span>

```csharp
Console.WriteLine(repo.Name);
```

<span data-ttu-id="88c75-229">Eşlemeleri doğru yaptığınızdan emin olmak için uygulayın. `dotnet run`</span><span class="sxs-lookup"><span data-stu-id="88c75-229">Execute `dotnet run` to make sure you've got the mappings correct.</span></span> <span data-ttu-id="88c75-230">Önceki yle aynı çıktıyı görmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="88c75-230">You should see the same output as before.</span></span>

<span data-ttu-id="88c75-231">Yeni özellikler eklemeden önce bir değişiklik daha yapalım.</span><span class="sxs-lookup"><span data-stu-id="88c75-231">Let's make one more change before adding new features.</span></span> <span data-ttu-id="88c75-232">Yöntem `ProcessRepositories` async iş yapabilir ve depoların bir koleksiyon döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="88c75-232">The `ProcessRepositories` method can do the async work and return a collection of the repositories.</span></span> <span data-ttu-id="88c75-233">Bu yöntemden `List<Repository>` döndürelim ve bilgileri yazan kodu `Main` yönteme taşıyalım.</span><span class="sxs-lookup"><span data-stu-id="88c75-233">Let's return the `List<Repository>` from that method, and move the code that writes the information into the `Main` method.</span></span>

<span data-ttu-id="88c75-234">Sonucu nesnelerin `ProcessRepositories` listesi olan bir görevi döndürmek `Repository` için imzayı değiştirin:</span><span class="sxs-lookup"><span data-stu-id="88c75-234">Change the signature of `ProcessRepositories` to return a task whose result is a list of `Repository` objects:</span></span>

```csharp
private static async Task<List<Repository>> ProcessRepositories()
```

<span data-ttu-id="88c75-235">Sonra, sadece JSON yanıtı işledikten sonra depoları döndürün:</span><span class="sxs-lookup"><span data-stu-id="88c75-235">Then, just return the repositories after processing the JSON response:</span></span>

```csharp
var streamTask = client.GetStreamAsync("https://api.github.com/orgs/dotnet/repos");
var repositories = await JsonSerializer.DeserializeAsync<List<Repository>>(await streamTask);
return repositories;
```

<span data-ttu-id="88c75-236">Derleyici, bu `Task<T>` yöntemi ' olarak `async`işaretlediğiniz için geri dönüş için nesne oluşturur</span><span class="sxs-lookup"><span data-stu-id="88c75-236">The compiler generates the `Task<T>` object for the return because you've marked this method as `async`.</span></span>
<span data-ttu-id="88c75-237">Daha sonra, `Main` bu sonuçları yakalar ve konsola her depo adı yazar şekilde yöntemi değiştirelim.</span><span class="sxs-lookup"><span data-stu-id="88c75-237">Then, let's modify the `Main` method so that it captures those results and writes each repository name to the console.</span></span> <span data-ttu-id="88c75-238">Yönteminiz `Main` şimdi şuna benziyor:</span><span class="sxs-lookup"><span data-stu-id="88c75-238">Your `Main` method now looks like this:</span></span>

```csharp
public static async Task Main(string[] args)
{
    var repositories = await ProcessRepositories();

    foreach (var repo in repositories)
        Console.WriteLine(repo.Name);
}
```

## <a name="reading-more-information"></a><span data-ttu-id="88c75-239">Daha Fazla Bilgi Okuma</span><span class="sxs-lookup"><span data-stu-id="88c75-239">Reading More Information</span></span>

<span data-ttu-id="88c75-240">Bunu, GitHub API'sinden gönderilen JSON paketindeki birkaç özelliği daha işleyerek bitirelim.</span><span class="sxs-lookup"><span data-stu-id="88c75-240">Let's finish this by processing a few more of the properties in the JSON packet that gets sent from the GitHub API.</span></span> <span data-ttu-id="88c75-241">Her şeyi kapmak istemeyeceksiniz, ancak birkaç özellik eklemek C# dilinin birkaç özelliğini daha gösterir.</span><span class="sxs-lookup"><span data-stu-id="88c75-241">You won't want to grab everything, but adding a few properties will demonstrate a few more features of the C# language.</span></span>

<span data-ttu-id="88c75-242">`Repository` Sınıf tanımına birkaç basit tür daha ekleyerek başlayalım.</span><span class="sxs-lookup"><span data-stu-id="88c75-242">Let's start by adding a few more simple types to the `Repository` class definition.</span></span> <span data-ttu-id="88c75-243">Bu özellikleri bu sınıfa ekleyin:</span><span class="sxs-lookup"><span data-stu-id="88c75-243">Add these properties to that class:</span></span>

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

<span data-ttu-id="88c75-244">Bu özellikler, dize türünden (JSON paketlerinin içerdiği) hedef türe yerleşik dönüşümlere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="88c75-244">These properties have built-in conversions from the string type (which is what the JSON packets contain) to the target type.</span></span> <span data-ttu-id="88c75-245">Türü <xref:System.Uri> sizin için yeni olabilir.</span><span class="sxs-lookup"><span data-stu-id="88c75-245">The <xref:System.Uri> type may be new to you.</span></span> <span data-ttu-id="88c75-246">Bir URI'yi veya bu durumda bir URL'yi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="88c75-246">It represents a URI, or in this case, a URL.</span></span> <span data-ttu-id="88c75-247">`Uri` JSON paketi hedef türüne dönüştürmeyen veriler içeriyorsa, serileştirme eylemi bir özel durum `int` oluşturur.</span><span class="sxs-lookup"><span data-stu-id="88c75-247">In the case of the `Uri` and `int` types, if the JSON packet contains data that does not convert to the target type, the serialization action will throw an exception.</span></span>

<span data-ttu-id="88c75-248">Bunları ekledikten sonra, bu `Main` öğeleri görüntülemek için yöntemi güncelleştirin:</span><span class="sxs-lookup"><span data-stu-id="88c75-248">Once you've added these, update the `Main` method to display those elements:</span></span>

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

<span data-ttu-id="88c75-249">Son adım olarak, son itme işlemi için bilgileri ekleyelim.</span><span class="sxs-lookup"><span data-stu-id="88c75-249">As a final step, let's add the information for the last push operation.</span></span> <span data-ttu-id="88c75-250">Bu bilgiler JSON yanıtında bu şekilde biçimlendirilir:</span><span class="sxs-lookup"><span data-stu-id="88c75-250">This information is formatted in this fashion in the JSON response:</span></span>

```json
2016-02-08T21:27:00Z
```

<span data-ttu-id="88c75-251">Bu biçim, standart .NET <xref:System.DateTime> biçimlerinin hiçbirini izlemez.</span><span class="sxs-lookup"><span data-stu-id="88c75-251">That format does not follow any of the standard .NET <xref:System.DateTime> formats.</span></span> <span data-ttu-id="88c75-252">Bu nedenle, özel bir dönüştürme yöntemi yazmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="88c75-252">Because of that, you'll need to write a custom conversion method.</span></span> <span data-ttu-id="88c75-253">Ayrıca büyük olasılıkla ham dize `Repository` sınıfın kullanıcılarına maruz istemiyorum.</span><span class="sxs-lookup"><span data-stu-id="88c75-253">You also probably don't want the raw string exposed to users of the `Repository` class.</span></span> <span data-ttu-id="88c75-254">Öznitelikler de bunu denetlemeye yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="88c75-254">Attributes can help control that as well.</span></span> <span data-ttu-id="88c75-255">İlk olarak, `public` `Repository` sınıfınızdaki tarih ve saatin dize temsilini `LastPush` `readonly` ve döndürülen tarihi temsil eden biçimlendirilmiş bir dize döndüren bir özelliği tanımla:</span><span class="sxs-lookup"><span data-stu-id="88c75-255">First, define a `public` property that will hold the string representation of the date and time in your `Repository` class and a `LastPush` `readonly` property that returns a formatted string that represents the returned date:</span></span>

```csharp
[JsonPropertyName("pushed_at")]
public string JsonDate { get; set; }

public DateTime LastPush =>
    DateTime.ParseExact(JsonDate, "yyyy-MM-ddTHH:mm:ssZ", CultureInfo.InvariantCulture);
```

<span data-ttu-id="88c75-256">Az önce tanımladığımız yeni yapılara bakalım.</span><span class="sxs-lookup"><span data-stu-id="88c75-256">Let's go over the new constructs we just defined.</span></span> <span data-ttu-id="88c75-257">Özellik, `LastPush` `get` erişimci için *ifade gövdeli* bir üye kullanılarak tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="88c75-257">The `LastPush` property is defined using an *expression-bodied member* for the `get` accessor.</span></span> <span data-ttu-id="88c75-258">Erişimci `set` yok.</span><span class="sxs-lookup"><span data-stu-id="88c75-258">There is no `set` accessor.</span></span> <span data-ttu-id="88c75-259">Erişime erişim amacını atlayarak C#'da salt okunur özelliği nasıl tanımladığınızdır. *read-only* `set`</span><span class="sxs-lookup"><span data-stu-id="88c75-259">Omitting the `set` accessor is how you define a *read-only* property in C#.</span></span> <span data-ttu-id="88c75-260">(Evet, C#'da *yalnızca yazma* özellikleri oluşturabilirsiniz, ancak değerleri sınırlıdır.) Yöntem, <xref:System.DateTime.ParseExact(System.String,System.String,System.IFormatProvider)> bir dizeyi ayrıştırır ve sağlanan tarih biçimini kullanarak bir <xref:System.DateTime> nesne oluşturur ve `DateTime` kullanan `CultureInfo` nesneye ek meta veriler ekler.</span><span class="sxs-lookup"><span data-stu-id="88c75-260">(Yes, you can create *write-only* properties in C#, but their value is limited.) The <xref:System.DateTime.ParseExact(System.String,System.String,System.IFormatProvider)> method parses a string and creates a <xref:System.DateTime> object using a provided date format, and adds additional metadata to the `DateTime` using a `CultureInfo` object.</span></span> <span data-ttu-id="88c75-261">Ayrışdırıcı işlemi başarısız olursa, özellik erişimcisi bir özel durum atar.</span><span class="sxs-lookup"><span data-stu-id="88c75-261">If the parse operation fails, the property accessor throws an exception.</span></span>

<span data-ttu-id="88c75-262">Kullanmak <xref:System.Globalization.CultureInfo.InvariantCulture>için, <xref:System.Globalization> `using` aşağıdaki yönergelere ad alanını eklemeniz `repo.cs`gerekir:</span><span class="sxs-lookup"><span data-stu-id="88c75-262">To use <xref:System.Globalization.CultureInfo.InvariantCulture>, you will need to add the <xref:System.Globalization> namespace to the `using` directives in `repo.cs`:</span></span>

```csharp
using System.Globalization;
```

<span data-ttu-id="88c75-263">Son olarak, konsola bir çıkış deyimi daha ekleyin ve bu uygulamayı yeniden oluşturmaya ve çalıştırmaya hazır sınız:</span><span class="sxs-lookup"><span data-stu-id="88c75-263">Finally, add one more output statement in the console, and you're ready to build and run this app again:</span></span>

```csharp
Console.WriteLine(repo.LastPush);
```

<span data-ttu-id="88c75-264">Sürümünüz artık [bitmiş örnekle](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient)eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="88c75-264">Your version should now match the [finished sample](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient).</span></span>

## <a name="conclusion"></a><span data-ttu-id="88c75-265">Sonuç</span><span class="sxs-lookup"><span data-stu-id="88c75-265">Conclusion</span></span>

<span data-ttu-id="88c75-266">Bu öğretici, web isteklerini nasıl yapacağınızı, sonucu ayrıştırmayı ve bu sonuçların özelliklerini nasıl görüntülediğinizi göstermiştir.</span><span class="sxs-lookup"><span data-stu-id="88c75-266">This tutorial showed you how to make web requests, parse the result, and display properties of those results.</span></span> <span data-ttu-id="88c75-267">Ayrıca projenize bağımlılık olarak yeni paketler eklediniz.</span><span class="sxs-lookup"><span data-stu-id="88c75-267">You've also added new packages as dependencies in your project.</span></span> <span data-ttu-id="88c75-268">C# dilinin nesne yönelimli teknikleri destekleyen bazı özelliklerini gördünüz.</span><span class="sxs-lookup"><span data-stu-id="88c75-268">You've seen some of the features of the C# language that support object-oriented techniques.</span></span>

<a name="dotnet-restore-note"></a>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
