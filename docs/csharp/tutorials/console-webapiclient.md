---
title: ".NET Core kullanarak bir REST istemcisi oluşturma"
description: "Bu öğretici bir dizi özellik .NET Core ve C# dili öğretir."
keywords: .NET, .NET Core
author: BillWagner
ms.author: wiwagn
ms.date: 03/06/2017
ms.topic: article
ms.prod: .net-core
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 51033ce2-7a53-4cdd-966d-9da15c8204d2
ms.openlocfilehash: 6b0f3acc3a6dbed4f44497d92d3c518ee5a5d2a7
ms.sourcegitcommit: dd6ea7f0e581ac84e0a90d9b23c463fcf1ec3ce7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2018
---
# <a name="rest-client"></a><span data-ttu-id="b206e-104">REST istemcisi</span><span class="sxs-lookup"><span data-stu-id="b206e-104">REST client</span></span>

## <a name="introduction"></a><span data-ttu-id="b206e-105">Giriş</span><span class="sxs-lookup"><span data-stu-id="b206e-105">Introduction</span></span>
<span data-ttu-id="b206e-106">Bu öğretici bir dizi özellik .NET Core ve C# dili öğretir.</span><span class="sxs-lookup"><span data-stu-id="b206e-106">This tutorial teaches you a number of features in .NET Core and the C# language.</span></span> <span data-ttu-id="b206e-107">Şunları öğreneceksiniz:</span><span class="sxs-lookup"><span data-stu-id="b206e-107">You’ll learn:</span></span>
*   <span data-ttu-id="b206e-108">Temel .NET Core komut satırı arabirimi (CLI).</span><span class="sxs-lookup"><span data-stu-id="b206e-108">The basics of the .NET Core Command Line Interface (CLI).</span></span>
*   <span data-ttu-id="b206e-109">C# dili özelliklerine genel bakış.</span><span class="sxs-lookup"><span data-stu-id="b206e-109">An overview of C# Language features.</span></span>
*   <span data-ttu-id="b206e-110">Bağımlılıkları NuGet ile yönetme</span><span class="sxs-lookup"><span data-stu-id="b206e-110">Managing dependencies with NuGet</span></span>
*   <span data-ttu-id="b206e-111">HTTP iletişimleri</span><span class="sxs-lookup"><span data-stu-id="b206e-111">HTTP Communications</span></span>
*   <span data-ttu-id="b206e-112">JSON bilgilerini işleme</span><span class="sxs-lookup"><span data-stu-id="b206e-112">Processing JSON information</span></span>
*   <span data-ttu-id="b206e-113">Öznitelikleri yapılandırmayla yönetme.</span><span class="sxs-lookup"><span data-stu-id="b206e-113">Managing configuration with Attributes.</span></span> 

<span data-ttu-id="b206e-114">HTTP istekleri sorunlarını GitHub üzerinde bir REST hizmeti için bir uygulama oluşturmak.</span><span class="sxs-lookup"><span data-stu-id="b206e-114">You’ll build an application that issues HTTP Requests to a REST service on GitHub.</span></span> <span data-ttu-id="b206e-115">JSON biçiminde bilgileri okuyun ve C# nesnelerini bu JSON paket dönüştürme.</span><span class="sxs-lookup"><span data-stu-id="b206e-115">You'll read information in JSON format, and convert that JSON packet into C# objects.</span></span> <span data-ttu-id="b206e-116">Son olarak, C# nesneleriyle çalışmak nasıl görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="b206e-116">Finally, you'll see how to work with C# objects.</span></span>

<span data-ttu-id="b206e-117">Bu öğreticide birçok özellik vardır.</span><span class="sxs-lookup"><span data-stu-id="b206e-117">There are a lot of features in this tutorial.</span></span> <span data-ttu-id="b206e-118">Şimdi bunları tek tek oluşturun.</span><span class="sxs-lookup"><span data-stu-id="b206e-118">Let’s build them one by one.</span></span>

<span data-ttu-id="b206e-119">İle birlikte izlemek tercih ederseniz [son örnek](https://github.com/dotnet/docs/tree/master/samples/csharp/getting-started/console-webapiclient) yönelik bu konu, yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b206e-119">If you prefer to follow along with the [final sample](https://github.com/dotnet/docs/tree/master/samples/csharp/getting-started/console-webapiclient) for this topic, you can download it.</span></span> <span data-ttu-id="b206e-120">Yükleme yönergeleri için bkz: [örnekler ve öğreticiler](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="b206e-120">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="b206e-121">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="b206e-121">Prerequisites</span></span>
<span data-ttu-id="b206e-122">.NET core çalışmasına, makine ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="b206e-122">You’ll need to set up your machine to run .NET core.</span></span> <span data-ttu-id="b206e-123">Yükleme yönergelerini bulabilirsiniz [.NET Core](https://www.microsoft.com/net/core) sayfası.</span><span class="sxs-lookup"><span data-stu-id="b206e-123">You can find the installation instructions on the [.NET Core](https://www.microsoft.com/net/core) page.</span></span> <span data-ttu-id="b206e-124">Bu uygulama, Windows, Linux, macOS veya Docker kapsayıcısı çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b206e-124">You can run this application on Windows, Linux, macOS or in a Docker container.</span></span> <span data-ttu-id="b206e-125">Sık kullanılan Kod Düzenleyicisi'ni yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="b206e-125">You’ll need to install your favorite code editor.</span></span> <span data-ttu-id="b206e-126">Kullanım aşağıda açıklamaları [Visual Studio Code](https://code.visualstudio.com/), platform Düzenleyicisi arası bir açık kaynak olduğu.</span><span class="sxs-lookup"><span data-stu-id="b206e-126">The descriptions below use [Visual Studio Code](https://code.visualstudio.com/), which is an open source, cross platform editor.</span></span> <span data-ttu-id="b206e-127">Ancak, tanımanız ne olursa olsun araçları kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b206e-127">However, you can use whatever tools you are comfortable with.</span></span>
## <a name="create-the-application"></a><span data-ttu-id="b206e-128">Uygulama oluşturma</span><span class="sxs-lookup"><span data-stu-id="b206e-128">Create the Application</span></span>
<span data-ttu-id="b206e-129">İlk adım, yeni bir uygulama oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="b206e-129">The first step is to create a new application.</span></span> <span data-ttu-id="b206e-130">Bir komut istemi açın ve uygulamanız için yeni bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="b206e-130">Open a command prompt and create a new directory for your application.</span></span> <span data-ttu-id="b206e-131">Geçerli dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="b206e-131">Make that the current directory.</span></span> <span data-ttu-id="b206e-132">Komut türü `dotnet new console` komut isteminde.</span><span class="sxs-lookup"><span data-stu-id="b206e-132">Type the command `dotnet new console` at the command prompt.</span></span> <span data-ttu-id="b206e-133">Bu, temel bir "Hello World" uygulaması için başlangıç dosyaları oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b206e-133">This creates the starter files for a basic "Hello World" application.</span></span>

<span data-ttu-id="b206e-134">Değişiklik yapmaya başlamadan önce basit Hello World uygulamasını çalıştırmak için adımlara edelim.</span><span class="sxs-lookup"><span data-stu-id="b206e-134">Before you start making modifications, let’s go through the steps to run the simple Hello World application.</span></span> <span data-ttu-id="b206e-135">Uygulamayı oluşturduktan sonra yazın `dotnet restore` ([bkz. Not](#dotnet-restore-note)) komut isteminde.</span><span class="sxs-lookup"><span data-stu-id="b206e-135">After creating the application, type `dotnet restore` ([see note](#dotnet-restore-note)) at the command prompt.</span></span> <span data-ttu-id="b206e-136">Bu komut, NuGet paket geri yükleme işlemi çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="b206e-136">This command runs the NuGet package restore process.</span></span> <span data-ttu-id="b206e-137">NuGet, bir .NET paketi yöneticisidir.</span><span class="sxs-lookup"><span data-stu-id="b206e-137">NuGet is a .NET package manager.</span></span> <span data-ttu-id="b206e-138">Bu komut, projeniz için eksik bağımlılıklar hiçbirini indirir.</span><span class="sxs-lookup"><span data-stu-id="b206e-138">This command downloads any of the missing dependencies for your project.</span></span> <span data-ttu-id="b206e-139">Yeni bir proje olarak ilk çalıştırmada .NET Core framework yükleyecek şekilde bağımlılıkları yerinde yok.</span><span class="sxs-lookup"><span data-stu-id="b206e-139">As this is a new project, none of the dependencies are in place, so the first run will download the .NET Core framework.</span></span> <span data-ttu-id="b206e-140">Bu ilk adımı tamamlandıktan sonra yalnızca çalıştırmanız gerekir `dotnet restore` ([bkz. Not](#dotnet-restore-note)) yeni bağımlı paketler eklediğinizde, veya bağımlılıklarınızı hiçbirini sürümlerini güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="b206e-140">After this initial step, you will only need to run `dotnet restore` ([see note](#dotnet-restore-note)) when you add new dependent packages, or update the versions of any of your dependencies.</span></span>  

<span data-ttu-id="b206e-141">Paketler geri yükledikten sonra çalıştırmanız `dotnet build`.</span><span class="sxs-lookup"><span data-stu-id="b206e-141">After restoring packages, you run `dotnet build`.</span></span> <span data-ttu-id="b206e-142">Bu yapı altyapısı yürütür ve uygulamanızı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b206e-142">This executes the build engine and creates your application.</span></span> <span data-ttu-id="b206e-143">Son olarak, yürütme `dotnet run` uygulamanızı çalıştırmak için.</span><span class="sxs-lookup"><span data-stu-id="b206e-143">Finally, you execute `dotnet run` to run your application.</span></span>

## <a name="adding-new-dependencies"></a><span data-ttu-id="b206e-144">Yeni bağımlılıkları ekleme</span><span class="sxs-lookup"><span data-stu-id="b206e-144">Adding New Dependencies</span></span>
<span data-ttu-id="b206e-145">.NET Core için temel tasarım hedefleri .NET framework yükleme boyutu en aza indirmek için biridir.</span><span class="sxs-lookup"><span data-stu-id="b206e-145">One of the key design goals for .NET Core is to minimize the size of the .NET framework installation.</span></span> <span data-ttu-id="b206e-146">.NET Core uygulama çerçevesi yalnızca tam .NET framework'ün en yaygın öğeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="b206e-146">The .NET Core Application framework contains only the most common elements of the .NET full framework.</span></span> <span data-ttu-id="b206e-147">Bir uygulama ek kitaplıklara özelliklerinden bazıları için gerekirse, C# projenize bu bağımlılıkları ekleyin (\*.csproj) dosyası.</span><span class="sxs-lookup"><span data-stu-id="b206e-147">If an application needs additional libraries for some of its features, you add those dependencies into your C# project (\*.csproj) file.</span></span> <span data-ttu-id="b206e-148">Bizim örneğimizde, eklemeniz gerekir `System.Runtime.Serialization.Json` uygulamanızın JSON yanıtları işleyebilmek için paket.</span><span class="sxs-lookup"><span data-stu-id="b206e-148">For our example, you'll need to add the `System.Runtime.Serialization.Json` package so your application can process JSON responses.</span></span>

<span data-ttu-id="b206e-149">Açık, `csproj` proje dosyası.</span><span class="sxs-lookup"><span data-stu-id="b206e-149">Open your `csproj` project file.</span></span> <span data-ttu-id="b206e-150">Dosyanın ilk satırı olarak görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="b206e-150">The first line of the file should appear as:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
```

<span data-ttu-id="b206e-151">Bu satırı hemen sonra aşağıdakini ekleyin:</span><span class="sxs-lookup"><span data-stu-id="b206e-151">Add the following immediately after this line:</span></span> 

```xml
   <ItemGroup>
      <PackageReference Include="System.Runtime.Serialization.Json" Version="4.3.0" />
   </ItemGroup> 
```
<span data-ttu-id="b206e-152">Çoğu Kod Düzenleyicisi Bu kitaplıklar farklı sürümlerini tamamlanmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="b206e-152">Most code editors will provide completion for different versions of these libraries.</span></span> <span data-ttu-id="b206e-153">Genellikle eklediğiniz herhangi bir paket en yeni sürümünü kullanmak istersiniz.</span><span class="sxs-lookup"><span data-stu-id="b206e-153">You'll usually want to use the latest version of any package that you add.</span></span> <span data-ttu-id="b206e-154">Bununla birlikte, tüm paketler sürümleri eşleşip eşleşmediğini ve .NET Core uygulama framework'ün sürümünü de eşleştiğinden emin emin olmak önemlidir.</span><span class="sxs-lookup"><span data-stu-id="b206e-154">However, it is important to make sure that the versions of all packages match, and that they also match the version of the .NET Core Application framework.</span></span>

<span data-ttu-id="b206e-155">Bu değişiklikleri yaptıktan sonra çalışması gerektiğini `dotnet restore` ([bkz. Not](#dotnet-restore-note)) yeniden böylece paket sisteminizde yüklenir.</span><span class="sxs-lookup"><span data-stu-id="b206e-155">After you've made these changes, you should run `dotnet restore` ([see note](#dotnet-restore-note)) again so that the package is installed on your system.</span></span>

## <a name="making-web-requests"></a><span data-ttu-id="b206e-156">Yapma Web istekleri</span><span class="sxs-lookup"><span data-stu-id="b206e-156">Making Web Requests</span></span>
<span data-ttu-id="b206e-157">Artık web sunucusundan veri alma başlatmaya hazırsınız.</span><span class="sxs-lookup"><span data-stu-id="b206e-157">Now you're ready to start retrieving data from the web.</span></span> <span data-ttu-id="b206e-158">Bilgileri okuyun bu uygulamada [GitHub API](https://developer.github.com/v3/).</span><span class="sxs-lookup"><span data-stu-id="b206e-158">In this application, you'll read information from the [GitHub API](https://developer.github.com/v3/).</span></span> <span data-ttu-id="b206e-159">Şimdi projeler altında hakkındaki bilgileri okumak [.NET Foundation](http://www.dotnetfoundation.org/) şemsiyesi.</span><span class="sxs-lookup"><span data-stu-id="b206e-159">Let's read information about the projects under the [.NET Foundation](http://www.dotnetfoundation.org/) umbrella.</span></span> <span data-ttu-id="b206e-160">Projeler hakkında bilgi almak için GitHub API isteği yaparak başlayacağız.</span><span class="sxs-lookup"><span data-stu-id="b206e-160">You'll start by making the request to the GitHub API to retrieve information on the projects.</span></span> <span data-ttu-id="b206e-161">Uç noktası kullanmanız: [https://api.github.com/orgs/dotnet/repos](https://api.github.com/orgs/dotnet/repos).</span><span class="sxs-lookup"><span data-stu-id="b206e-161">The endpoint you'll use is: [https://api.github.com/orgs/dotnet/repos](https://api.github.com/orgs/dotnet/repos).</span></span> <span data-ttu-id="b206e-162">Bir HTTP GET isteği kullanacağınız için bu projeler, ilgili tüm bilgileri almak istiyor.</span><span class="sxs-lookup"><span data-stu-id="b206e-162">You want to retrieve all the information about these projects, so you'll use an HTTP GET request.</span></span>
<span data-ttu-id="b206e-163">Tarayıcınız Ayrıca hangi bilgilerin görmek için URL'yi tarayıcınıza aldığınız, yapıştırabilirsiniz HTTP GET istekleri ve işleme kullanır.</span><span class="sxs-lookup"><span data-stu-id="b206e-163">Your browser also uses HTTP GET requests, so you can paste that URL into your browser to see what information you'll be receiving and processing.</span></span>

<span data-ttu-id="b206e-164">Kullandığınız <xref:System.Net.Http.HttpClient> web isteği yapmak için sınıf.</span><span class="sxs-lookup"><span data-stu-id="b206e-164">You use the <xref:System.Net.Http.HttpClient> class to make web requests.</span></span> <span data-ttu-id="b206e-165">Gibi tüm modern .NET API'leri, <xref:System.Net.Http.HttpClient> , uzun süre çalışan API'ler yalnızca zaman uyumsuz yöntemleri destekler.</span><span class="sxs-lookup"><span data-stu-id="b206e-165">Like all modern .NET APIs, <xref:System.Net.Http.HttpClient> supports only async methods for its long-running APIs.</span></span>
<span data-ttu-id="b206e-166">Zaman uyumsuz yöntem yaparak başlatın.</span><span class="sxs-lookup"><span data-stu-id="b206e-166">Start by making an async method.</span></span> <span data-ttu-id="b206e-167">Uygulamanın işlevselliğini yapı olarak uygulamasında doldurmanız.</span><span class="sxs-lookup"><span data-stu-id="b206e-167">You'll fill in the implementation as you build the functionality of the application.</span></span> <span data-ttu-id="b206e-168">Başlangıç açarak `program.cs` dosya proje dizininde ve aşağıdaki yöntemi ekleme `Program` sınıfı:</span><span class="sxs-lookup"><span data-stu-id="b206e-168">Start by opening the `program.cs` file in your project directory and adding the following method to the `Program` class:</span></span>

```csharp
private static async Task ProcessRepositories()
{
    
}
```

<span data-ttu-id="b206e-169">Eklemeniz gerekir bir `using` en üstündeki deyimi, `Main` yöntemi C# Derleyici tanımasını <xref:System.Threading.Tasks.Task> türü:</span><span class="sxs-lookup"><span data-stu-id="b206e-169">You'll need to add a `using` statement at the top of your `Main` method so that the C# compiler recognizes the <xref:System.Threading.Tasks.Task> type:</span></span>

```csharp
using System.Threading.Tasks;
```

<span data-ttu-id="b206e-170">Projenizi bu noktada yapılandırdıysanız, herhangi bir içermediği için bu yöntem için oluşturulan bir uyarı alırsınız `await` işleçler ve zaman uyumlu olarak çalışır.</span><span class="sxs-lookup"><span data-stu-id="b206e-170">If you build your project at this point, you'll get a warning generated for this method, because it does not contain any `await` operators and will run synchronously.</span></span> <span data-ttu-id="b206e-171">Şimdilik yoksay; ekleyeceksiniz `await` işleçleri yazarken yönteminde doldurun.</span><span class="sxs-lookup"><span data-stu-id="b206e-171">Ignore that for now; you'll add `await` operators as you fill in the method.</span></span>

<span data-ttu-id="b206e-172">Ardından, tanımlanan ad alanı yeniden adlandırma `namespace` varsayılan from deyimi `ConsoleApp` için `WebAPIClient`.</span><span class="sxs-lookup"><span data-stu-id="b206e-172">Next, rename the namespace defined in the `namespace` statement from its default of `ConsoleApp` to `WebAPIClient`.</span></span> <span data-ttu-id="b206e-173">Daha sonra tanımlarız bir `repo` bu ad alanındaki sınıfı.</span><span class="sxs-lookup"><span data-stu-id="b206e-173">We'll later define a `repo` class in this namespace.</span></span>

<span data-ttu-id="b206e-174">Ardından, güncelleştirme `Main` yöntemi bu yöntemi çağırın.</span><span class="sxs-lookup"><span data-stu-id="b206e-174">Next, update the `Main` method to call this method.</span></span> <span data-ttu-id="b206e-175">`ProcessRepositories` Yöntemi bir görev döndürür ve bu görev tamamlanmadan önce programdan çıkmak döndürmemelidir.</span><span class="sxs-lookup"><span data-stu-id="b206e-175">The `ProcessRepositories` method returns a Task, and you shouldn't exit the program before that task finishes.</span></span> <span data-ttu-id="b206e-176">Bu nedenle, kullanmalısınız `Wait` engellemek ve görevin tamamlanmasını beklemek için yöntemi:</span><span class="sxs-lookup"><span data-stu-id="b206e-176">Therefore, you must use the `Wait` method to block and wait for the task to finish:</span></span>

```csharp
public static void Main(string[] args)
{
    ProcessRepositories().Wait();
}
```

<span data-ttu-id="b206e-177">Artık, hiçbir şey yapmaz ancak zaman uyumsuz olarak mevcut bir program var.</span><span class="sxs-lookup"><span data-stu-id="b206e-177">Now, you have a program that does nothing, but does it asynchronously.</span></span> <span data-ttu-id="b206e-178">Şimdi geliştirin.</span><span class="sxs-lookup"><span data-stu-id="b206e-178">Let's improve it.</span></span>

<span data-ttu-id="b206e-179">İlk web üzerinden veri almak yeteneğine sahip bir nesne gerekir; kullanabileceğiniz bir <xref:System.Net.Http.HttpClient> Bunu yapmak için.</span><span class="sxs-lookup"><span data-stu-id="b206e-179">First you need an object that is capable to retrieve data from the web; you can use a <xref:System.Net.Http.HttpClient> to do that.</span></span> <span data-ttu-id="b206e-180">Bu nesne, istek ve yanıt işler.</span><span class="sxs-lookup"><span data-stu-id="b206e-180">This object handles the request and the responses.</span></span> <span data-ttu-id="b206e-181">Bu türde tek bir örneğini `Program` sınıf Program.cs dosyasının içinde.</span><span class="sxs-lookup"><span data-stu-id="b206e-181">Instantiate a single instance of that type in the `Program` class inside the Program.cs file.</span></span>

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

 <span data-ttu-id="b206e-182">Geri dönelim `ProcessRepositories` yöntemi ve ilk sürümü doldurun:</span><span class="sxs-lookup"><span data-stu-id="b206e-182">Let's go back to the `ProcessRepositories` method and fill in a first version of it:</span></span>

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

<span data-ttu-id="b206e-183">Ayrıca iki eklemeniz gerekecektir yeni bu dosyayı üst derlemek için using deyimleri:</span><span class="sxs-lookup"><span data-stu-id="b206e-183">You'll need to also add two new using statements at the top of the file for this to compile:</span></span>

```csharp
using System.Net.Http;
using System.Net.Http.Headers;
```

<span data-ttu-id="b206e-184">Bu ilk sürüm dotnet foundation kuruluş altındaki tüm depoları listesi okumak için web isteği yapar.</span><span class="sxs-lookup"><span data-stu-id="b206e-184">This first version makes a web request to read the list of all repositories under the dotnet foundation organization.</span></span> <span data-ttu-id="b206e-185">(GitHub .NET Foundation için 'dotnet' kimliğidir).</span><span class="sxs-lookup"><span data-stu-id="b206e-185">(The gitHub ID for the .NET Foundation is 'dotnet').</span></span> <span data-ttu-id="b206e-186">İlk birkaç satırı ayarlamak <xref:System.Net.Http.HttpClient> bu istek için.</span><span class="sxs-lookup"><span data-stu-id="b206e-186">The first few lines set up the <xref:System.Net.Http.HttpClient> for this request.</span></span> <span data-ttu-id="b206e-187">İlk olarak, GitHub JSON yanıtları kabul edecek şekilde yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="b206e-187">First, it is configured to accept the GitHub JSON responses.</span></span>
<span data-ttu-id="b206e-188">Yalnızca JSON biçimidir.</span><span class="sxs-lookup"><span data-stu-id="b206e-188">This format is simply JSON.</span></span> <span data-ttu-id="b206e-189">Sonraki satıra bir kullanıcı aracısı üstbilgisi tüm istekler bu nesneden ekler.</span><span class="sxs-lookup"><span data-stu-id="b206e-189">The next line adds a User Agent header to all requests from this object.</span></span> <span data-ttu-id="b206e-190">Bu iki üstbilgileri GitHub sunucu kodu tarafından denetlenir ve Github'dan bilgileri almak gereklidir.</span><span class="sxs-lookup"><span data-stu-id="b206e-190">These two headers are checked by the GitHub server code, and are necessary to retrieve information from GitHub.</span></span>

<span data-ttu-id="b206e-191">Sonra yapılandırdığınız <xref:System.Net.Http.HttpClient>, istek ve yanıt almak web olun.</span><span class="sxs-lookup"><span data-stu-id="b206e-191">After you've configured the <xref:System.Net.Http.HttpClient>, you make a web request and retrieve the response.</span></span> <span data-ttu-id="b206e-192">Bu ilk sürümünde kullandığınız <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)?displayProperty=nameWithType> kolaylık yöntemi.</span><span class="sxs-lookup"><span data-stu-id="b206e-192">In this first version, you use the <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)?displayProperty=nameWithType> convenience method.</span></span> <span data-ttu-id="b206e-193">Bu kolaylık metodunun web istekte bir görev başlatır ve ardından istek geri döndüğünde, yanıt akışına okur ve akış içeriği ayıklar.</span><span class="sxs-lookup"><span data-stu-id="b206e-193">This convenience method starts a task that makes the web request, and then when the request returns, it reads the response stream and extracts the content from the stream.</span></span> <span data-ttu-id="b206e-194">Yanıt gövdesi olarak döndürülür bir <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="b206e-194">The body of the response is returned as a <xref:System.String>.</span></span> <span data-ttu-id="b206e-195">Görev tamamlandığında kullanılabilir bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="b206e-195">The string is available when the task completes.</span></span> 

<span data-ttu-id="b206e-196">Bu yöntem son iki satırı görev bekler ve sonra konsol yanıtı yazdırın.</span><span class="sxs-lookup"><span data-stu-id="b206e-196">The final two lines of this method await that task, and then print the response to the console.</span></span>
<span data-ttu-id="b206e-197">Uygulama oluşturun ve çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="b206e-197">Build the app, and run it.</span></span> <span data-ttu-id="b206e-198">Yapı uyarı artık, çünkü kayboluyor `ProcessRepositories` şimdi içeren bir `await` işleci.</span><span class="sxs-lookup"><span data-stu-id="b206e-198">The build warning is gone now, because the `ProcessRepositories` now does contain an `await` operator.</span></span> <span data-ttu-id="b206e-199">Biçimlendirilmiş metin JSON uzun görünümünü görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="b206e-199">You'll see a long display of JSON formatted text.</span></span>   

## <a name="processing-the-json-result"></a><span data-ttu-id="b206e-200">JSON sonuç işleme</span><span class="sxs-lookup"><span data-stu-id="b206e-200">Processing the JSON Result</span></span>

<span data-ttu-id="b206e-201">Bu noktada, bir web sunucusundan bir yanıt almak ve bu yanıtta bulunan metni görüntülemek için kodu yazdıktan.</span><span class="sxs-lookup"><span data-stu-id="b206e-201">At this point, you've written the code to retrieve a response from a web server, and display the text that is contained in that response.</span></span> <span data-ttu-id="b206e-202">Ardından, şimdi bu JSON yanıtını C# nesnelerini dönüştürün.</span><span class="sxs-lookup"><span data-stu-id="b206e-202">Next, let's convert that JSON response into C# objects.</span></span>

<span data-ttu-id="b206e-203">JSON serileştirici JSON verilerini C# nesnelerine dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="b206e-203">The JSON Serializer converts JSON data into C# Objects.</span></span> <span data-ttu-id="b206e-204">İlk göreviniz bu yanıttan kullandığınız bilgileri içeren bir C# sınıf türü tanımlamaktır.</span><span class="sxs-lookup"><span data-stu-id="b206e-204">Your first task is to define a C# class type to contain the information you use from this response.</span></span> <span data-ttu-id="b206e-205">Şimdi bu yavaş depo adını içeren basit bir C# tür ile bunu başlangıç oluşturun:</span><span class="sxs-lookup"><span data-stu-id="b206e-205">Let's build this slowly, so start with a simple C# type that contains the name of the repository:</span></span>

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

<span data-ttu-id="b206e-206">Yukarıdaki kod 'repo.cs' adlı yeni bir dosyada yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="b206e-206">Put the above code in a new file called 'repo.cs'.</span></span> <span data-ttu-id="b206e-207">Bu sınıfın sürümü JSON veri işlemek için en basit yolu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="b206e-207">This version of the class represents the simplest path to process JSON data.</span></span> <span data-ttu-id="b206e-208">Sınıf adı ve üye adı aşağıdaki C# kuralları yerine JSON paketteki kullanılan adları eşleşir.</span><span class="sxs-lookup"><span data-stu-id="b206e-208">The class name and the member name match the names used in the JSON packet, instead of following C# conventions.</span></span> <span data-ttu-id="b206e-209">Bazı configuration öznitelikleri daha sonra sağlayarak, düzeltme.</span><span class="sxs-lookup"><span data-stu-id="b206e-209">You'll fix that by providing some configuration attributes later.</span></span> <span data-ttu-id="b206e-210">Bu sınıf, JSON seri hale getirme ve seri durumdan çıkarma başka bir önemli özelliği gösterilmektedir: JSON paketteki tüm alanlar bu sınıf, bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="b206e-210">This class demonstrates another important feature of JSON serialization and deserialization: Not all the fields in the JSON packet are part of this class.</span></span>
<span data-ttu-id="b206e-211">JSON serileştirici kullanılan sınıf türünde bulunmayan bilgileri göz ardı eder.</span><span class="sxs-lookup"><span data-stu-id="b206e-211">The JSON serializer will ignore information that is not included in the class type being used.</span></span>
<span data-ttu-id="b206e-212">Bu özellik yalnızca bir alt kümesini JSON paket alanları çalışmak türleri oluşturmak kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="b206e-212">This feature makes it easier to create types that work with only a subset of the fields in the JSON packet.</span></span>

<span data-ttu-id="b206e-213">Türü oluşturduğunuza göre şimdi onu seri durumdan çıkarır.</span><span class="sxs-lookup"><span data-stu-id="b206e-213">Now that you've created the type, let's deserialize it.</span></span> <span data-ttu-id="b206e-214">Oluşturmanız gerekecek bir <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="b206e-214">You'll need to create a <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> object.</span></span> <span data-ttu-id="b206e-215">Bu nesne CLR türü beklenen JSON paket için bunu bilmelisiniz alır.</span><span class="sxs-lookup"><span data-stu-id="b206e-215">This object must know the CLR type expected for the JSON packet it retrieves.</span></span> <span data-ttu-id="b206e-216">Github'dan bir dizi depoları, böylece pakette bir `List<repo>` doğru türüdür.</span><span class="sxs-lookup"><span data-stu-id="b206e-216">The packet from GitHub contains a sequence of repositories, so a `List<repo>` is the correct type.</span></span> <span data-ttu-id="b206e-217">Aşağıdaki satırı ekleyin, `ProcessRepositories` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="b206e-217">Add the following line to your `ProcessRepositories` method:</span></span>

```csharp
var serializer = new DataContractJsonSerializer(typeof(List<repo>));
```

<span data-ttu-id="b206e-218">Bu de eklemeniz gerekir böylece iki yeni ad alanı kullanıyorsanız:</span><span class="sxs-lookup"><span data-stu-id="b206e-218">You're using two new namespaces, so you'll need to add those as well:</span></span>

```csharp
using System.Collections.Generic;
using System.Runtime.Serialization.Json;
```

<span data-ttu-id="b206e-219">Ardından, C# nesnelerini JSON dönüştürmek için seri hale getirici kullanacaksınız.</span><span class="sxs-lookup"><span data-stu-id="b206e-219">Next, you'll use the serializer to convert JSON into C# objects.</span></span> <span data-ttu-id="b206e-220">Çağrı Değiştir <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)> içinde `ProcessRepositories` aşağıdaki iki satırı yöntemiyle:</span><span class="sxs-lookup"><span data-stu-id="b206e-220">Replace the call to <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)> in your `ProcessRepositories` method with the following two lines:</span></span>

```csharp
var streamTask = client.GetStreamAsync("https://api.github.com/orgs/dotnet/repos");
var repositories = serializer.ReadObject(await streamTask) as List<repo>;
```

<span data-ttu-id="b206e-221">Kullanmakta olduğunuz bildirim <xref:System.Net.Http.HttpClient.GetStreamAsync(System.String)> yerine <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)>.</span><span class="sxs-lookup"><span data-stu-id="b206e-221">Notice that you're now using <xref:System.Net.Http.HttpClient.GetStreamAsync(System.String)> instead of <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)>.</span></span> <span data-ttu-id="b206e-222">Seri hale getirici bir akış yerine bir dize, kaynağı olarak kullanır.</span><span class="sxs-lookup"><span data-stu-id="b206e-222">The serializer uses a stream instead of a string as its source.</span></span> <span data-ttu-id="b206e-223">Şimdi, yukarıdaki ikinci satırda kullanılmakta olan birkaç C# dil özellikleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b206e-223">Let's explain a couple features of the C# language that are being used in the second line above.</span></span> <span data-ttu-id="b206e-224">Bağımsız değişkeni <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject(System.IO.Stream)> olan bir `await` ifade.</span><span class="sxs-lookup"><span data-stu-id="b206e-224">The argument to <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject(System.IO.Stream)> is an `await` expression.</span></span> <span data-ttu-id="b206e-225">Await ifadeleri görünebilir neredeyse her yerden, kodunuzda şimdi kadar yalnızca bunları Atama ifadesinin bir parçası olarak gördüğünüz olsa bile.</span><span class="sxs-lookup"><span data-stu-id="b206e-225">Await expressions can appear almost anywhere in your code, even though up to now, you've only seen them as part of an assignment statement.</span></span>

<span data-ttu-id="b206e-226">İkincisi, `as` işleci dönüştürür derleme zamanı türünden `object` için `List<repo>`.</span><span class="sxs-lookup"><span data-stu-id="b206e-226">Secondly, the `as` operator converts from the compile time type of `object` to `List<repo>`.</span></span> <span data-ttu-id="b206e-227">Bildirimi <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject(System.IO.Stream)> türünde bir nesne döndürür bildirir <xref:System.Object?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b206e-227">The declaration of <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject(System.IO.Stream)> declares that it returns an object of type <xref:System.Object?displayProperty=nameWithType>.</span></span> <span data-ttu-id="b206e-228"><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject(System.IO.Stream)>Bu oluşturulan, belirttiğiniz türü döndürür (`List<repo>` bu öğreticideki).</span><span class="sxs-lookup"><span data-stu-id="b206e-228"><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject(System.IO.Stream)> will return the type you specified when you constructed it (`List<repo>` in this tutorial).</span></span> <span data-ttu-id="b206e-229">Dönüştürme başarılı olmazsa, `as` işleci hesaplar için `null`, bir özel durum atma yerine.</span><span class="sxs-lookup"><span data-stu-id="b206e-229">If the conversion does not succeed, the `as` operator evaluates to `null`, instead of throwing an exception.</span></span>

<span data-ttu-id="b206e-230">Bu bölümde ile bitmek üzere.</span><span class="sxs-lookup"><span data-stu-id="b206e-230">You're almost done with this section.</span></span> <span data-ttu-id="b206e-231">C# nesnelerini JSON dönüştürdükten, şimdi her depo adını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="b206e-231">Now that you've converted the JSON to C# objects, let's display the name of each repository.</span></span> <span data-ttu-id="b206e-232">Okuma satırları değiştirin:</span><span class="sxs-lookup"><span data-stu-id="b206e-232">Replace the lines that read:</span></span>

```csharp
var msg = await stringTask;   //**Deleted this
Console.Write(msg);
```

<span data-ttu-id="b206e-233">Aşağıdaki ile:</span><span class="sxs-lookup"><span data-stu-id="b206e-233">with the following:</span></span>

```csharp
foreach (var repo in repositories)
    Console.WriteLine(repo.name);
```

<span data-ttu-id="b206e-234">Derleme ve uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="b206e-234">Compile and run the application.</span></span> <span data-ttu-id="b206e-235">.NET Foundation parçası olan depoları adları yazdırır.</span><span class="sxs-lookup"><span data-stu-id="b206e-235">It will print out the names of the repositories that are part of the .NET Foundation.</span></span>

## <a name="controlling-serialization"></a><span data-ttu-id="b206e-236">Seri hale getirme denetleme</span><span class="sxs-lookup"><span data-stu-id="b206e-236">Controlling Serialization</span></span>

<span data-ttu-id="b206e-237">Daha fazla özellik eklemeden önce şimdi adres `repo` yazın ve daha fazla standart C# kurallarına uygun kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="b206e-237">Before you add more features, let's address the `repo` type and make it follow more standard C# conventions.</span></span> <span data-ttu-id="b206e-238">Bu açıklama ekleyerek gerçekleştirirsiniz `repo` ile yazın *öznitelikleri* kontrol eden JSON seri hale getirici nasıl çalışır.</span><span class="sxs-lookup"><span data-stu-id="b206e-238">You'll do this by annotating the `repo` type with *attributes* that control how the JSON Serializer works.</span></span> <span data-ttu-id="b206e-239">Sizin durumunuzda, JSON anahtar adları ve C# sınıfı ve üye adları arasında bir eşleme tanımlamak için bu öznitelikler kullanacaksınız.</span><span class="sxs-lookup"><span data-stu-id="b206e-239">In your case, you'll use these attributes to define a mapping between the JSON key names and the C# class and member names.</span></span> <span data-ttu-id="b206e-240">Kullanılan iki öznitelikleri `DataContract` özniteliği ve `DataMember` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="b206e-240">The two attributes used are the `DataContract` attribute and the `DataMember` attribute.</span></span> <span data-ttu-id="b206e-241">Kurala göre tüm öznitelik sınıfları soneki sona `Attribute`.</span><span class="sxs-lookup"><span data-stu-id="b206e-241">By convention, all Attribute classes end in the suffix `Attribute`.</span></span> <span data-ttu-id="b206e-242">Ancak, bir öznitelik uyguladığınızda, o soneki kullanan gerekmez.</span><span class="sxs-lookup"><span data-stu-id="b206e-242">However, you do not need to use that suffix when you apply an attribute.</span></span> 

<span data-ttu-id="b206e-243">`DataContract` Ve `DataMember` öznitelikleridir farklı bir kitaplık için bu kitaplığı, C# projesi dosyanızı bağımlılık olarak eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="b206e-243">The `DataContract` and `DataMember` attributes are in a different library, so you'll need to add that library to your C# project file as a dependency.</span></span> <span data-ttu-id="b206e-244">Aşağıdaki satırı ekleyin `<ItemGroup>` proje dosyanızı bölümünü:</span><span class="sxs-lookup"><span data-stu-id="b206e-244">Add the following line to the `<ItemGroup>` section of your project file:</span></span>

```xml
<PackageReference Include="System.Runtime.Serialization.Primitives" Version="4.3.0" />
```

<span data-ttu-id="b206e-245">Dosyayı kaydettikten sonra çalıştırmak `dotnet restore` ([bkz. Not](#dotnet-restore-note)) bu paketi alınamadı.</span><span class="sxs-lookup"><span data-stu-id="b206e-245">After you save the file, run `dotnet restore` ([see note](#dotnet-restore-note)) to retrieve this package.</span></span>

<span data-ttu-id="b206e-246">Ardından, açık `repo.cs` dosya.</span><span class="sxs-lookup"><span data-stu-id="b206e-246">Next, open the `repo.cs` file.</span></span> <span data-ttu-id="b206e-247">Pascal kullanım ve tam adı yazım ad değiştirelim `Repository`.</span><span class="sxs-lookup"><span data-stu-id="b206e-247">Let's change the name to use Pascal Case, and fully spell out the name `Repository`.</span></span> <span data-ttu-id="b206e-248">Biz yine eklemeniz gerekir böylece bu türe, JSON 'depodaki' düğümleri eşlemek istediğiniz `DataContract` özniteliği sınıf bildirimi.</span><span class="sxs-lookup"><span data-stu-id="b206e-248">We still want to map JSON 'repo' nodes to this type, so you'll need to add the `DataContract` attribute to the class declaration.</span></span> <span data-ttu-id="b206e-249">Ayarlarız `Name` bu türüyle eşleştirmek JSON düğümlerin adı özniteliğine özelliği:</span><span class="sxs-lookup"><span data-stu-id="b206e-249">You'll set the `Name` property of the attribute to the name of the JSON nodes that map to this type:</span></span>

```csharp
[DataContract(Name="repo")]
public class Repository
```

<span data-ttu-id="b206e-250"><xref:System.Runtime.Serialization.DataContractAttribute> Üyesi <xref:System.Runtime.Serialization> uygun eklemeniz gerekir böylece ad alanı, `using` deyimini dosyanın üst:</span><span class="sxs-lookup"><span data-stu-id="b206e-250">The <xref:System.Runtime.Serialization.DataContractAttribute> is a member of the <xref:System.Runtime.Serialization> namespace, so you'll need to add the appropriate `using` statement at the top of the file:</span></span>

```csharp
using System.Runtime.Serialization;
```

<span data-ttu-id="b206e-251">Adının değişip `repo` sınıfının `Repository`, aynı ad Program.cs içinde değişikliğini yapmanız gerekir (bazı düzenleyicileri otomatik olarak bu değişikliği yapmadan bir yeniden adlandırma düzenlemesi destekleyebilir:)</span><span class="sxs-lookup"><span data-stu-id="b206e-251">You changed the name of the `repo` class to `Repository`, so you'll need to make the same name change in Program.cs (some editors may support a rename refactoring that will make this change automatically:)</span></span>

```csharp
var serializer = new DataContractJsonSerializer(typeof(List<Repository>));

// ...

var repositories = serializer.ReadObject(await streamTask) as List<Repository>;
```

<span data-ttu-id="b206e-252">Ardından, aynı değişiklikle olalım `name` kullanarak alan <xref:System.Runtime.Serialization.DataMemberAttribute> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="b206e-252">Next, let's make the same change with the `name` field by using the <xref:System.Runtime.Serialization.DataMemberAttribute> class.</span></span> <span data-ttu-id="b206e-253">Aşağıdaki değişiklik bildirimi için `name` repo.cs alanındaki:</span><span class="sxs-lookup"><span data-stu-id="b206e-253">Make the following changes to the declaration of the `name` field in repo.cs:</span></span>

```csharp
[DataMember(Name="name")]
public string Name;
```

<span data-ttu-id="b206e-254">Bu değişiklik program.cs içinde her depo adını yazar kodunu değiştirmek ihtiyaç duyacağınız anlamına gelir:</span><span class="sxs-lookup"><span data-stu-id="b206e-254">This change means you need to change the code that writes the name of each repository in program.cs:</span></span>

```csharp
Console.WriteLine(repo.Name);
```

<span data-ttu-id="b206e-255">Yapmak bir `dotnet build` arkasından bir `dotnet run` aldığınız eşlemeleri doğru olduğundan emin olmak.</span><span class="sxs-lookup"><span data-stu-id="b206e-255">Do a `dotnet build` followed by a `dotnet run` to make sure you've got the mappings correct.</span></span> <span data-ttu-id="b206e-256">Önce aynı çıkışı görmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="b206e-256">You should see the same output as before.</span></span> <span data-ttu-id="b206e-257">Biz web sunucusundan daha fazla özellik işlemeden önce bir daha fazla değişiklik yapılmasını olalım `Repository` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="b206e-257">Before we process more properties from the web server, let's make one more change to the `Repository` class.</span></span> <span data-ttu-id="b206e-258">`Name` Üye genel olarak erişilebilir bir alandır.</span><span class="sxs-lookup"><span data-stu-id="b206e-258">The `Name` member is a publicly accessible field.</span></span> <span data-ttu-id="b206e-259">İyi bir nesne yönelimli uygulama değil, bu nedenle, bir özelliğe değiştirelim.</span><span class="sxs-lookup"><span data-stu-id="b206e-259">That's not a good object-oriented practice, so let's change it to a property.</span></span> <span data-ttu-id="b206e-260">Bizim amaçlarla özelliği alırken veya ayarlarken çalıştırmak için özel kod gerekmez, ancak bir özellik için değiştirme kolaylaştırır kullanan herhangi bir kod masraf yapmadan daha sonra bu değişiklikleri eklemek `Repository` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="b206e-260">For our purposes, we don't need any specific code to run when getting or setting the property, but changing to a property makes it easier to add those changes later without breaking any code that uses the `Repository` class.</span></span>

<span data-ttu-id="b206e-261">Alan tanımı kaldırın ve bunların yerine bir [otomatik uygulanan özelliği](../programming-guide/classes-and-structs/auto-implemented-properties.md):</span><span class="sxs-lookup"><span data-stu-id="b206e-261">Remove the field definition, and replace it with an [auto-implemented property](../programming-guide/classes-and-structs/auto-implemented-properties.md):</span></span>

```csharp
public string Name { get; set; }
```

<span data-ttu-id="b206e-262">Derleyici gövdesini oluşturur `get` ve `set` erişimciler, hem de bir özel alan adı depolamak için.</span><span class="sxs-lookup"><span data-stu-id="b206e-262">The compiler generates the body of the `get` and `set` accessors, as well as a private field to store the name.</span></span> <span data-ttu-id="b206e-263">El ile yazabilirsiniz aşağıdaki kodu benzer olacaktır:</span><span class="sxs-lookup"><span data-stu-id="b206e-263">It would be similar to the following code that you could type by hand:</span></span>

```csharp
public string Name 
{ 
    get { return this._name; }
    set { this._name = value; }
}
private string _name;
```

<span data-ttu-id="b206e-264">Yeni özellikler eklemeden önce bir daha fazla değişiklik olalım.</span><span class="sxs-lookup"><span data-stu-id="b206e-264">Let's make one more change before adding new features.</span></span> <span data-ttu-id="b206e-265">`ProcessRepositories` Yöntemi zaman uyumsuz iş yapın ve depoları koleksiyonunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="b206e-265">The `ProcessRepositories` method can do the async work and return a collection of the repositories.</span></span> <span data-ttu-id="b206e-266">Şimdi iade `List<Repository>` , yöntemi ve taşıma içine bilgi yazar kod `Main` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="b206e-266">Let's return the `List<Repository>` from that method, and move the code that writes the information into the `Main` method.</span></span>

<span data-ttu-id="b206e-267">İmzasını değiştirmek `ProcessRepositories` sonucu olan bir liste görev dönmek için `Repository` nesneler:</span><span class="sxs-lookup"><span data-stu-id="b206e-267">Change the signature of `ProcessRepositories` to return a task whose result is a list of `Repository` objects:</span></span>

```csharp
private static async Task<List<Repository>> ProcessRepositories()
```

<span data-ttu-id="b206e-268">Sonra yalnızca JSON yanıt işledikten sonra depoları döndürün:</span><span class="sxs-lookup"><span data-stu-id="b206e-268">Then, just return the repositories after processing the JSON response:</span></span>

```csharp
var repositories = serializer.ReadObject(await streamTask) as List<Repository>;
return repositories;
```

<span data-ttu-id="b206e-269">Derleyici oluşturur `Task<T>` bu yöntemi olarak işaretlendiğinden için dönüş nesne `async`.</span><span class="sxs-lookup"><span data-stu-id="b206e-269">The compiler generates the `Task<T>` object for the return because you've marked this method as `async`.</span></span>
<span data-ttu-id="b206e-270">Ardından, değiştirelim `Main` , BT'nin bunlar yakalar şekilde yöntemi sonuçlanır ve her bir havuz adı konsola yazar.</span><span class="sxs-lookup"><span data-stu-id="b206e-270">Then, let's modify the `Main` method so that it captures those results and writes each repository name to the console.</span></span> <span data-ttu-id="b206e-271">`Main` Yöntemi şimdi aşağıdaki gibi görünür:</span><span class="sxs-lookup"><span data-stu-id="b206e-271">Your `Main` method now looks like this:</span></span>

```csharp
public static void Main(string[] args)
{
    var repositories = ProcessRepositories().Result;

    foreach (var repo in repositories)
        Console.WriteLine(repo.Name);
}
```

<span data-ttu-id="b206e-272">Erişme `Result` özelliği bir görevin görevin tamamlanmasını engeller.</span><span class="sxs-lookup"><span data-stu-id="b206e-272">Accessing the `Result` property of a Task blocks until the task has completed.</span></span> <span data-ttu-id="b206e-273">Normalde, tercih `await` giriş olarak görev tamamlandığında `ProcessRepositories` yöntemi, ancak kullanılamaz olarak `Main` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="b206e-273">Normally, you would prefer to `await` the completion of the task, as in the `ProcessRepositories` method, but that isn't allowed in the `Main` method.</span></span>

## <a name="reading-more-information"></a><span data-ttu-id="b206e-274">Daha fazla bilgi okuma</span><span class="sxs-lookup"><span data-stu-id="b206e-274">Reading More Information</span></span>

<span data-ttu-id="b206e-275">Şimdi bu GitHub API'SİNDEN gönderilir JSON paket özelliklerinde, birkaç daha işleyerek tamamlayın.</span><span class="sxs-lookup"><span data-stu-id="b206e-275">Let's finish this by processing a few more of the properties in the JSON packet that gets sent from the GitHub API.</span></span> <span data-ttu-id="b206e-276">Her şeyi yakalayın istemezsiniz, ancak bazı özellikler ekleme C# dilinin birkaç daha fazla özelliği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="b206e-276">You won't want to grab everything, but adding a few properties will demonstrate a few more features of the C# language.</span></span>

<span data-ttu-id="b206e-277">Daha fazla birkaç basit türler için ekleyerek başlayalım `Repository` sınıf tanımının.</span><span class="sxs-lookup"><span data-stu-id="b206e-277">Let's start by adding a few more simple types to the `Repository` class definition.</span></span> <span data-ttu-id="b206e-278">Bu özellikler, sınıfına ekleyin:</span><span class="sxs-lookup"><span data-stu-id="b206e-278">Add these properties to that class:</span></span>

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

<span data-ttu-id="b206e-279">Bu özellikler hedef türe (olan ne JSON paketleri içeren) dize türünden yerleşik dönüştürmeleri vardır.</span><span class="sxs-lookup"><span data-stu-id="b206e-279">These properties have built-in conversions from the string type (which is what the JSON packets contain) to the target type.</span></span> <span data-ttu-id="b206e-280"><xref:System.Uri> Türü için yeni olabilir.</span><span class="sxs-lookup"><span data-stu-id="b206e-280">The <xref:System.Uri> type may be new to you.</span></span> <span data-ttu-id="b206e-281">Bir URI temsil eder ya da bu durumda, bir URL.</span><span class="sxs-lookup"><span data-stu-id="b206e-281">It represents a URI, or in this case, a URL.</span></span> <span data-ttu-id="b206e-282">Durumunda `Uri` ve `int` türleri, JSON paketi hedef türü dönüştürmez veri içeriyorsa, serileştirme eylem throw bir özel durum.</span><span class="sxs-lookup"><span data-stu-id="b206e-282">In the case of the `Uri` and `int` types, if the JSON packet contains data that does not convert to the target type, the serialization action will throw an exception.</span></span>

<span data-ttu-id="b206e-283">Bunlar ekledikten sonra güncelleştirme `Main` yöntemi bu öğeleri görüntülemek için:</span><span class="sxs-lookup"><span data-stu-id="b206e-283">Once you've added these, update the `Main` method to display those elements:</span></span>

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
<span data-ttu-id="b206e-284">Son adım olarak, son gönderme işlemi için bilgi ekleyelim.</span><span class="sxs-lookup"><span data-stu-id="b206e-284">As a final step, let's add the information for the last push operation.</span></span> <span data-ttu-id="b206e-285">Bu bilgiler, JSON yanıt bu şekilde biçimlendirilmiş:</span><span class="sxs-lookup"><span data-stu-id="b206e-285">This information is formatted in this fashion in the JSON response:</span></span>

```json
2016-02-08T21:27:00Z
```

<span data-ttu-id="b206e-286">Bu biçim herhangi bir standart .NET izlemez <xref:System.DateTime> biçimleri.</span><span class="sxs-lookup"><span data-stu-id="b206e-286">That format does not follow any of the standard .NET <xref:System.DateTime> formats.</span></span> <span data-ttu-id="b206e-287">Bu nedenle özel dönüştürme yöntemi yazma gerekecektir.</span><span class="sxs-lookup"><span data-stu-id="b206e-287">Because of that, you'll need to write a custom conversion method.</span></span> <span data-ttu-id="b206e-288">Kullanıcılara gösterilen ham dizesini de büyük olasılıkla istemediğiniz `Repository` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="b206e-288">You also probably don't want the raw string exposed to users of the `Repository` class.</span></span> <span data-ttu-id="b206e-289">Öznitelikler de bu denetim yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="b206e-289">Attributes can help control that as well.</span></span> <span data-ttu-id="b206e-290">İlk olarak tanımlayan bir `private` tarih saat dize gösterimini tutacak özelliği, `Repository` sınıfı:</span><span class="sxs-lookup"><span data-stu-id="b206e-290">First, define a `private` property that will hold the string representation of the date time in your `Repository` class:</span></span>

```csharp
[DataMember(Name="pushed_at")]
private string JsonDate { get; set; }
```

<span data-ttu-id="b206e-291">`DataMember` Özniteliği bildirir seri hale getirici bu işlenmesi gerektiğini, ortak üyesi olmasa bile.</span><span class="sxs-lookup"><span data-stu-id="b206e-291">The `DataMember` attribute informs the serializer that this should be processed, even though it is not a public member.</span></span> <span data-ttu-id="b206e-292">Ardından, geçerli bir dize dönüştürür genel bir salt okunur özelliği yazılamıyor ihtiyacınız <xref:System.DateTime> nesne ve döndüren <xref:System.DateTime>:</span><span class="sxs-lookup"><span data-stu-id="b206e-292">Next, you need to write a public read-only property that converts the string to a valid <xref:System.DateTime> object, and returns that <xref:System.DateTime>:</span></span>

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

<span data-ttu-id="b206e-293">Yeni yapıları üzerinden edelim.</span><span class="sxs-lookup"><span data-stu-id="b206e-293">Let's go over the new constructs above.</span></span> <span data-ttu-id="b206e-294">`IgnoreDataMember` Özniteliği, bu tür için okuma veya herhangi bir JSON nesneden yazılmış, seri hale getirici bildirir.</span><span class="sxs-lookup"><span data-stu-id="b206e-294">The `IgnoreDataMember` attribute instructs the serializer that this type should not be read to or written from any JSON object.</span></span> <span data-ttu-id="b206e-295">Bu özellik yalnızca içeren bir `get` erişimcisi.</span><span class="sxs-lookup"><span data-stu-id="b206e-295">This property contains only a `get` accessor.</span></span> <span data-ttu-id="b206e-296">Var olan hiçbir `set` erişimcisi.</span><span class="sxs-lookup"><span data-stu-id="b206e-296">There is no `set` accessor.</span></span> <span data-ttu-id="b206e-297">Tanımladığınız nasıl olan bir *salt okunur* C# özelliği.</span><span class="sxs-lookup"><span data-stu-id="b206e-297">That's how you define a *read-only* property in C#.</span></span> <span data-ttu-id="b206e-298">(Evet, oluşturabileceğiniz *salt yazılır* C# ancak değerlerine özelliklerinde sınırlıdır.) <xref:System.DateTime.ParseExact(System.String,System.String,System.IFormatProvider)> Yöntemi bir dize ayrıştırır ve oluşturur bir <xref:System.DateTime> sağlanan tarih biçimini kullanarak nesne ve ek meta veri ekler `DateTime` kullanarak bir `CultureInfo` nesnesi.</span><span class="sxs-lookup"><span data-stu-id="b206e-298">(Yes, you can create *write-only* properties in C#, but their value is limited.) The <xref:System.DateTime.ParseExact(System.String,System.String,System.IFormatProvider)> method parses a string and creates a <xref:System.DateTime> object using a provided date format, and adds additional metadata to the `DateTime` using a `CultureInfo` object.</span></span> <span data-ttu-id="b206e-299">Özellik erişimcisi ayrıştırma işlemi başarısız olursa, bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b206e-299">If the parse operation fails, the property accessor throws an exception.</span></span>

<span data-ttu-id="b206e-300">Kullanılacak <xref:System.Globalization.CultureInfo.InvariantCulture>, eklemeniz gerekir <xref:System.Globalization> ad alanına `using` deyimlerinde `repo.cs`:</span><span class="sxs-lookup"><span data-stu-id="b206e-300">To use <xref:System.Globalization.CultureInfo.InvariantCulture>, you will need to add the <xref:System.Globalization> namespace to the `using` statements in `repo.cs`:</span></span>

```csharp
using System.Globalization;
```

<span data-ttu-id="b206e-301">Son olarak, bir konsol deyiminde daha çıkış ve oluşturmak ve bu uygulamayı tekrar çalıştırmak hazır ekleyin:</span><span class="sxs-lookup"><span data-stu-id="b206e-301">Finally, add one more output statement in the console, and you're ready to build and run this app again:</span></span>

```csharp
Console.WriteLine(repo.LastPush);
```

<span data-ttu-id="b206e-302">Sürümünüz artık eşleşmelidir [tamamlanmış örnek](https://github.com/dotnet/docs/tree/master/samples/csharp/getting-started/console-webapiclient).</span><span class="sxs-lookup"><span data-stu-id="b206e-302">Your version should now match the [finished sample](https://github.com/dotnet/docs/tree/master/samples/csharp/getting-started/console-webapiclient).</span></span>
 
## <a name="conclusion"></a><span data-ttu-id="b206e-303">Sonuç</span><span class="sxs-lookup"><span data-stu-id="b206e-303">Conclusion</span></span>

<span data-ttu-id="b206e-304">Bu öğreticide web istekleri yapabilir, sonuç ayrıştırma ve bu sonuçlar özelliklerini görüntülemek nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="b206e-304">This tutorial showed you how to make web requests, parse the result, and display properties of those results.</span></span> <span data-ttu-id="b206e-305">Ayrıca, yeni paketler bağımlılıklar olarak projenizde ekledik.</span><span class="sxs-lookup"><span data-stu-id="b206e-305">You've also added new packages as dependencies in your project.</span></span> <span data-ttu-id="b206e-306">Bazı nesne yönelimli teknikleri destekleyen C# dilinin özelliklerini gördünüz.</span><span class="sxs-lookup"><span data-stu-id="b206e-306">You've seen some of the features of the C# language that support object-oriented techniques.</span></span>

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
