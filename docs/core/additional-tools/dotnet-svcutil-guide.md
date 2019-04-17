---
title: WCF svcutil aracına genel bakış
description: .NET Core ve ASP.NET Core projeleri için .NET Framework projeleri için WCF svcutil aracına benzer işlevsellik ekleyen Microsoft WCF svcutil dotnet araç genel bakış.
author: mlacouture
ms.date: 02/22/2019
ms.custom: seodec18
ms.openlocfilehash: b5dfb84f19c3748daa303c828cbe881f1582eb76
ms.sourcegitcommit: 438919211260bb415fc8f96ca3eabc33cf2d681d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2019
ms.locfileid: "59612829"
---
# <a name="wcf-dotnet-svcutil-tool-for-net-core"></a><span data-ttu-id="877fd-103">.NET Core için WCF dotnet svcutil aracı</span><span class="sxs-lookup"><span data-stu-id="877fd-103">WCF dotnet-svcutil tool for .NET Core</span></span>

<span data-ttu-id="877fd-104">Windows Communication Foundation (WCF) **dotnet svcutil** araçtır bir ağ konumu üzerinde bir web hizmetinden veya bir WSDL dosyasından meta verilerini alır ve istemci proxy yöntemleri içeren bir WCF sınıfı oluşturur bir .NET Core CLI aracı, web hizmet işlemleri erişim.</span><span class="sxs-lookup"><span data-stu-id="877fd-104">The Windows Communication Foundation (WCF) **dotnet-svcutil** tool is a .NET Core CLI tool that retrieves metadata from a web service on a network location or from a WSDL file, and generates a WCF class containing client proxy methods that access the web service operations.</span></span>

<span data-ttu-id="877fd-105">Benzer şekilde [ **Service Model meta verilerini - svcutil** ](../../framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) .NET Framework projeleri için araç **dotnet svcutil** bir web hizmeti başvurusu oluşturmak için bir komut satırı aracı .NET Core ve .NET Standard projelerine uyumludur.</span><span class="sxs-lookup"><span data-stu-id="877fd-105">Similar to the [**Service Model Metadata - svcutil**](../../framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) tool for .NET Framework projects, the **dotnet-svcutil** is a command-line tool for generating a web service reference compatible with .NET Core and .NET Standard projects.</span></span>

<span data-ttu-id="877fd-106">**Dotnet svcutil** araçtır için alternatif bir seçenek [ **WCF Web Service Reference** ](wcf-web-service-reference-guide.md) Visual Studio, Visual Studio ile ilk sevk edilen hizmet sağlayıcısı bağlı 2017 v15.5.</span><span class="sxs-lookup"><span data-stu-id="877fd-106">The **dotnet-svcutil** tool is an alternative option to the [**WCF Web Service Reference**](wcf-web-service-reference-guide.md) Visual Studio connected service provider that first shipped with Visual Studio 2017 v15.5.</span></span> <span data-ttu-id="877fd-107">**Dotnet svcutil** aracı bir .NET Core CLI aracı, Linux, macOS ve Windows üzerinde kullanılabilir çapraz platform.</span><span class="sxs-lookup"><span data-stu-id="877fd-107">The **dotnet-svcutil** tool as a .NET Core CLI tool, is available cross-platform on Linux, macOS, and Windows.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="877fd-108">Yalnızca güvenilir bir kaynaktan Hizmetleri başvuruda bulunmalıdır.</span><span class="sxs-lookup"><span data-stu-id="877fd-108">You should only reference services from a trusted source.</span></span> <span data-ttu-id="877fd-109">Güvenilmeyen bir kaynaktan başvurularının eklenmesi, güvenliği tehlikeye atabilir.</span><span class="sxs-lookup"><span data-stu-id="877fd-109">Adding references from an untrusted source may compromise security.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="877fd-110">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="877fd-110">Prerequisites</span></span>

# <a name="dotnet-svcutil-2xtabdotnetsvcutil2x"></a>[<span data-ttu-id="877fd-111">dotnet-svcutil 2.x</span><span class="sxs-lookup"><span data-stu-id="877fd-111">dotnet-svcutil 2.x</span></span>](#tab/dotnetsvcutil2x)
* <span data-ttu-id="877fd-112">[.NET core 2.1 SDK](https://dotnet.microsoft.com/download) veya sonraki sürümler</span><span class="sxs-lookup"><span data-stu-id="877fd-112">[.NET Core 2.1 SDK](https://dotnet.microsoft.com/download) or later versions</span></span>
* <span data-ttu-id="877fd-113">Sık kullandığınız kod düzenleyici</span><span class="sxs-lookup"><span data-stu-id="877fd-113">Your favorite code editor</span></span>

# <a name="dotnet-svcutil-1xtabdotnetsvcutil1x"></a>[<span data-ttu-id="877fd-114">dotnet-svcutil 1.x</span><span class="sxs-lookup"><span data-stu-id="877fd-114">dotnet-svcutil 1.x</span></span>](#tab/dotnetsvcutil1x)
* <span data-ttu-id="877fd-115">[.NET core 1.0.4 SDK](https://dotnet.microsoft.com/download) veya sonraki sürümler</span><span class="sxs-lookup"><span data-stu-id="877fd-115">[.NET Core 1.0.4 SDK](https://dotnet.microsoft.com/download) or later versions</span></span>
* <span data-ttu-id="877fd-116">Sık kullandığınız kod düzenleyici</span><span class="sxs-lookup"><span data-stu-id="877fd-116">Your favorite code editor</span></span>

---

## <a name="getting-started"></a><span data-ttu-id="877fd-117">Başlarken</span><span class="sxs-lookup"><span data-stu-id="877fd-117">Getting started</span></span>

<span data-ttu-id="877fd-118">Aşağıdaki örnek bir .NET Core web projesi için bir web hizmeti başvurusu eklemek ve hizmeti çağırmak için gereken adımlarda size yol gösterir.</span><span class="sxs-lookup"><span data-stu-id="877fd-118">The following example walks you through the steps required to add a web service reference to a .NET Core web project and invoke the service.</span></span> <span data-ttu-id="877fd-119">Adlı bir .NET Core web uygulaması oluşturacaksınız _HelloSvcutil_ aşağıdaki sözleşme uygulayan bir web hizmeti için bir başvuru ekleyin:</span><span class="sxs-lookup"><span data-stu-id="877fd-119">You'll create a .NET Core web application named _HelloSvcutil_ and add a reference to a web service that implements the following contract:</span></span>

```csharp
[ServiceContract]
public interface ISayHello
{
    [OperationContract]
    string Hello(string name);
}
```

<span data-ttu-id="877fd-120">Bu örnekte, web hizmeti şu adresten barındırılacak varsayalım: `http://contoso.com/SayHello.svc`</span><span class="sxs-lookup"><span data-stu-id="877fd-120">For this example, let's assume the web service will be hosted at the following address: `http://contoso.com/SayHello.svc`</span></span>

<span data-ttu-id="877fd-121">Bir Windows, macOS veya Linux komut penceresinde aşağıdaki adımları gerçekleştirin:</span><span class="sxs-lookup"><span data-stu-id="877fd-121">From a Windows, macOS, or Linux command window perform the following steps:</span></span>

1. <span data-ttu-id="877fd-122">Adlı bir dizin oluşturmak _HelloSvcutil_ projeniz için ve aşağıdaki örnekte olduğu gibi geçerli dizin yapın:</span><span class="sxs-lookup"><span data-stu-id="877fd-122">Create a directory named _HelloSvcutil_ for your project and make it your current directory, as in the following example:</span></span>

```console
mkdir HelloSvcutil
cd HelloSvcutil
```

2. <span data-ttu-id="877fd-123">Yeni bir C# directory kullanarak web projesi [ `dotnet new` ](../tools/dotnet-new.md) komutuyla şu şekilde:</span><span class="sxs-lookup"><span data-stu-id="877fd-123">Create a new C# web project in that directory using the [`dotnet new`](../tools/dotnet-new.md) command as follows:</span></span>

```console
dotnet new web
```

3. <span data-ttu-id="877fd-124">Yükleme [ `dotnet-svcutil` NuGet paketini](https://nuget.org/packages/dotnet-svcutil) CLI aracı olarak:</span><span class="sxs-lookup"><span data-stu-id="877fd-124">Install the [`dotnet-svcutil` NuGet package](https://nuget.org/packages/dotnet-svcutil) as a CLI tool:</span></span>
# <a name="dotnet-svcutil-2xtabdotnetsvcutil2x"></a>[<span data-ttu-id="877fd-125">dotnet-svcutil 2.x</span><span class="sxs-lookup"><span data-stu-id="877fd-125">dotnet-svcutil 2.x</span></span>](#tab/dotnetsvcutil2x)

```console
dotnet tool install --global dotnet-svcutil
```

# <a name="dotnet-svcutil-1xtabdotnetsvcutil1x"></a>[<span data-ttu-id="877fd-126">dotnet-svcutil 1.x</span><span class="sxs-lookup"><span data-stu-id="877fd-126">dotnet-svcutil 1.x</span></span>](#tab/dotnetsvcutil1x)
<span data-ttu-id="877fd-127">Açık `HelloSvcutil.csproj` proje dosyası düzenleyicinizde, düzenleme `Project` öğesi ve ekleme [ `dotnet-svcutil` NuGet paketini](https://nuget.org/packages/dotnet-svcutil) CLI aracı başvuru olarak, aşağıdaki kodu kullanarak:</span><span class="sxs-lookup"><span data-stu-id="877fd-127">Open the `HelloSvcutil.csproj` project file in your editor, edit the `Project` element, and add the [`dotnet-svcutil` NuGet package](https://nuget.org/packages/dotnet-svcutil) as a CLI tool reference, using the following code:</span></span>

```xml
<ItemGroup>
  <DotNetCliToolReference Include="dotnet-svcutil" Version="1.0.*" />
</ItemGroup>
```

<span data-ttu-id="877fd-128">Daha sonra geri _dotnet svcutil_ kullanarak paket [ `dotnet restore` ](../tools/dotnet-restore.md) komutuyla şu şekilde:</span><span class="sxs-lookup"><span data-stu-id="877fd-128">Then restore the _dotnet-svcutil_ package using the [`dotnet restore`](../tools/dotnet-restore.md) command as follows:</span></span>

```console
dotnet restore
```

---

4. <span data-ttu-id="877fd-129">Çalıştırma _dotnet svcutil_ gibi web hizmeti başvurusu dosyası oluşturmak için komutu:</span><span class="sxs-lookup"><span data-stu-id="877fd-129">Run the _dotnet-svcutil_ command to generate the web service reference file as follows:</span></span>
# <a name="dotnet-svcutil-2xtabdotnetsvcutil2x"></a>[<span data-ttu-id="877fd-130">dotnet-svcutil 2.x</span><span class="sxs-lookup"><span data-stu-id="877fd-130">dotnet-svcutil 2.x</span></span>](#tab/dotnetsvcutil2x)

```console
dotnet-svcutil http://contoso.com/SayHello.svc
```

# <a name="dotnet-svcutil-1xtabdotnetsvcutil1x"></a>[<span data-ttu-id="877fd-131">dotnet-svcutil 1.x</span><span class="sxs-lookup"><span data-stu-id="877fd-131">dotnet-svcutil 1.x</span></span>](#tab/dotnetsvcutil1x)

```console
dotnet svcutil http://contoso.com/SayHello.svc
```

---

<span data-ttu-id="877fd-132">Oluşturulan dosyası olarak kaydedilen _HelloSvcutil/ServiceReference/Reference.cs_.</span><span class="sxs-lookup"><span data-stu-id="877fd-132">The generated file is saved as _HelloSvcutil/ServiceReference/Reference.cs_.</span></span> <span data-ttu-id="877fd-133">_Dotnet svcutil_ aracı gerekli proxy kodu tarafından uygun WCF paketleri paket başvuruları projeye de ekler.</span><span class="sxs-lookup"><span data-stu-id="877fd-133">The _dotnet-svcutil_ tool also adds to the project the appropriate WCF packages required by the proxy code as package references.</span></span>

## <a name="using-the-service-reference"></a><span data-ttu-id="877fd-134">Hizmet başvurusunu kullanma</span><span class="sxs-lookup"><span data-stu-id="877fd-134">Using the Service Reference</span></span>

1. <span data-ttu-id="877fd-135">Kullanarak WCF paketleri geri [ `dotnet restore` ](../tools/dotnet-restore.md) komutuyla şu şekilde:</span><span class="sxs-lookup"><span data-stu-id="877fd-135">Restore the WCF packages using the [`dotnet restore`](../tools/dotnet-restore.md) command as follows:</span></span>

```console
dotnet restore
```

2. <span data-ttu-id="877fd-136">İstemci adı, sınıf ve kullanmak istediğiniz işlemi bulun.</span><span class="sxs-lookup"><span data-stu-id="877fd-136">Find the name of the client class and operation you want to use.</span></span> <span data-ttu-id="877fd-137">`Reference.cs` devralan bir sınıfın içereceği `System.ServiceModel.ClientBase`, hizmetteki işlemleri çağırmak için kullanılan yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="877fd-137">`Reference.cs` will contain a class that inherits from `System.ServiceModel.ClientBase`, with methods that can be used to call operations on the service.</span></span> <span data-ttu-id="877fd-138">Bu örnekte, aramak istediğiniz _SayHello_ hizmetin _Hello_ işlemi.</span><span class="sxs-lookup"><span data-stu-id="877fd-138">In this example, you want to call the _SayHello_ service's _Hello_ operation.</span></span> <span data-ttu-id="877fd-139">`ServiceReference.SayHelloClient` İstemci sınıf adıdır ve sahip bir yöntemi çağıran `HelloAsync` işlemi çağırmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="877fd-139">`ServiceReference.SayHelloClient` is the name of the client class, and has a method called `HelloAsync` that can be used to call the operation.</span></span>

3. <span data-ttu-id="877fd-140">Açık `Startup.cs` Düzenleyicisi'nde dosya ve kullanarak bir ekleme üst hizmet başvurusu isim uzayı için:</span><span class="sxs-lookup"><span data-stu-id="877fd-140">Open the `Startup.cs` file in your editor, and add a using statement for the service reference namespace at the top:</span></span>

```csharp
using ServiceReference;
```

 4. <span data-ttu-id="877fd-141">Düzen `Configure` web hizmetini çağırmak için yöntem.</span><span class="sxs-lookup"><span data-stu-id="877fd-141">Edit the `Configure` method to invoke the web service.</span></span> <span data-ttu-id="877fd-142">Devralınan sınıfının bir örneğini oluşturarak bunu `ClientBase` ve istemci nesneye yöntemi çağırma:</span><span class="sxs-lookup"><span data-stu-id="877fd-142">You do this by creating an instance of the class that inherits from `ClientBase` and calling the method on the client object:</span></span>

```csharp
public void Configure(IApplicationBuilder app, IHostingEnvironment env)
{
    if (env.IsDevelopment())
    {
        app.UseDeveloperExceptionPage();
    }

    app.Run(async (context) =>
    {
        var client = new SayHelloClient();
        var response = await client.HelloAsync();
        await context.Response.WriteAsync(response);
    });
}

```

5. <span data-ttu-id="877fd-143">Kullanarak uygulama çalıştırma [ `dotnet run` ](../tools/dotnet-run.md) komutuyla şu şekilde:</span><span class="sxs-lookup"><span data-stu-id="877fd-143">Run the application using the [`dotnet run`](../tools/dotnet-run.md) command as follows:</span></span>

```console
dotnet run
```

6. <span data-ttu-id="877fd-144">Konsolda listelenen URL'ye gidin (örneğin, `http://localhost:5000`) web tarayıcınızda.</span><span class="sxs-lookup"><span data-stu-id="877fd-144">Navigate to the URL listed in the console (for example, `http://localhost:5000`) in your web browser.</span></span>

<span data-ttu-id="877fd-145">Aşağıdaki çıktıyı görmeniz gerekir: "Hello dotnet-svcutil!"</span><span class="sxs-lookup"><span data-stu-id="877fd-145">You should see the following output: "Hello dotnet-svcutil!"</span></span>

<span data-ttu-id="877fd-146">Ayrıntılı bir açıklaması için `dotnet-svcutil` aracı parametreleri, help parametresini aşağıdaki şekilde geçirme aracı Çağır:</span><span class="sxs-lookup"><span data-stu-id="877fd-146">For a detailed description of the `dotnet-svcutil` tool parameters, invoke the tool passing the help parameter as follows:</span></span>
# <a name="dotnet-svcutil-2xtabdotnetsvcutil2x"></a>[<span data-ttu-id="877fd-147">dotnet-svcutil 2.x</span><span class="sxs-lookup"><span data-stu-id="877fd-147">dotnet-svcutil 2.x</span></span>](#tab/dotnetsvcutil2x)

```console
dotnet-svcutil --help
```

# <a name="dotnet-svcutil-1xtabdotnetsvcutil1x"></a>[<span data-ttu-id="877fd-148">dotnet-svcutil 1.x</span><span class="sxs-lookup"><span data-stu-id="877fd-148">dotnet-svcutil 1.x</span></span>](#tab/dotnetsvcutil1x)

```console
dotnet svcutil --help
```

---

## <a name="feedback--questions"></a><span data-ttu-id="877fd-149">Geri bildirim ve sorular</span><span class="sxs-lookup"><span data-stu-id="877fd-149">Feedback & questions</span></span>

<span data-ttu-id="877fd-150">Sorularınız veya geri bildirim, varsa [github'da bir sorun açın](https://github.com/dotnet/wcf/issues/new).</span><span class="sxs-lookup"><span data-stu-id="877fd-150">If you have any questions or feedback, [open an issue on GitHub](https://github.com/dotnet/wcf/issues/new).</span></span> <span data-ttu-id="877fd-151">Mevcut bir soru veya sorunlarla gözden geçirebilirsiniz [WCF deponun GitHub üzerinde en](https://github.com/dotnet/wcf/issues?utf8=%E2%9C%93&q=is:issue%20label:tooling).</span><span class="sxs-lookup"><span data-stu-id="877fd-151">You can also review any existing questions or issues [at the WCF repo on GitHub](https://github.com/dotnet/wcf/issues?utf8=%E2%9C%93&q=is:issue%20label:tooling).</span></span>

## <a name="release-notes"></a><span data-ttu-id="877fd-152">Sürüm notları</span><span class="sxs-lookup"><span data-stu-id="877fd-152">Release notes</span></span>

* <span data-ttu-id="877fd-153">Başvurmak [sürüm notları](https://github.com/dotnet/wcf/blob/master/release-notes/dotnet-svcutil-notes.md) güncelleştirilmiş sürüm bilgileri için bilinen sorunlar da dahil olmak üzere.</span><span class="sxs-lookup"><span data-stu-id="877fd-153">Refer to the [Release notes](https://github.com/dotnet/wcf/blob/master/release-notes/dotnet-svcutil-notes.md) for updated release information, including known issues.</span></span>

## <a name="information"></a><span data-ttu-id="877fd-154">Bilgiler</span><span class="sxs-lookup"><span data-stu-id="877fd-154">Information</span></span>

* [<span data-ttu-id="877fd-155">DotNet svcutil NuGet paketi</span><span class="sxs-lookup"><span data-stu-id="877fd-155">dotnet-svcutil NuGet Package</span></span>](https://nuget.org/packages/dotnet-svcutil)
