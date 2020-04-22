---
title: WCF svcutil aracına genel bakış
description: .NET Framework projeleri için WCF svcutil aracına benzer şekilde .NET Core ve ASP.NET Core projeleri için işlevsellik ekleyen Microsoft WCF dotnet-svcutil aracına genel bakış.
author: mlacouture
ms.date: 02/22/2019
ms.openlocfilehash: 1f500c9355112183a135c2b639807c7cd62fbbfc
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021259"
---
# <a name="wcf-dotnet-svcutil-tool-for-net-core"></a><span data-ttu-id="6cfb2-103">.NET Core için WCF dotnet-svcutil aracı</span><span class="sxs-lookup"><span data-stu-id="6cfb2-103">WCF dotnet-svcutil tool for .NET Core</span></span>

<span data-ttu-id="6cfb2-104">Windows Communication Foundation (WCF) **dotnet-svcutil** aracı, ağ konumundaki bir web hizmetinden veya WSDL dosyasındaki meta verileri alan ve web hizmeti işlemlerine erişen istemci proxy yöntemleri içeren bir WCF sınıfı oluşturan bir .NET aracıdır.</span><span class="sxs-lookup"><span data-stu-id="6cfb2-104">The Windows Communication Foundation (WCF) **dotnet-svcutil** tool is a .NET tool that retrieves metadata from a web service on a network location or from a WSDL file, and generates a WCF class containing client proxy methods that access the web service operations.</span></span>

<span data-ttu-id="6cfb2-105">.NET Framework projeleri için [**svcutil**](../../framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) aracı olan Service Model Metadata'ya benzer şekilde, **dotnet-svcutil** ,NET Core ve .NET Standard projeleri ile uyumlu bir web hizmeti başvurusu oluşturmak için bir komut satırı aracıdır.</span><span class="sxs-lookup"><span data-stu-id="6cfb2-105">Similar to the [**Service Model Metadata - svcutil**](../../framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) tool for .NET Framework projects, the **dotnet-svcutil** is a command-line tool for generating a web service reference compatible with .NET Core and .NET Standard projects.</span></span>

<span data-ttu-id="6cfb2-106">**Dotnet-svcutil** aracı, Visual Studio 2017 sürüm 15.5 ile ilk olarak gönderilen [**WCF Web Service Reference**](wcf-web-service-reference-guide.md) Visual Studio bağlantılı servis sağlayıcısına alternatif bir seçenektir.</span><span class="sxs-lookup"><span data-stu-id="6cfb2-106">The **dotnet-svcutil** tool is an alternative option to the [**WCF Web Service Reference**](wcf-web-service-reference-guide.md) Visual Studio connected service provider that first shipped with Visual Studio 2017 version 15.5.</span></span> <span data-ttu-id="6cfb2-107">**Dotnet-svcutil** aracı bir .NET aracı olarak, Linux, macOS ve Windows'da çapraz platform da kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="6cfb2-107">The **dotnet-svcutil** tool as a .NET tool, is available cross-platform on Linux, macOS, and Windows.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6cfb2-108">Yalnızca güvenilir bir kaynaktan gelen hizmetlere başvurmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="6cfb2-108">You should only reference services from a trusted source.</span></span> <span data-ttu-id="6cfb2-109">Güvenilmeyen bir kaynaktan referans eklemek güvenliği tehlikeye atabilir.</span><span class="sxs-lookup"><span data-stu-id="6cfb2-109">Adding references from an untrusted source may compromise security.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="6cfb2-110">Ön koşullar</span><span class="sxs-lookup"><span data-stu-id="6cfb2-110">Prerequisites</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="dotnet-svcutil-2x"></a>[<span data-ttu-id="6cfb2-111">dotnet-svcutil 2.x</span><span class="sxs-lookup"><span data-stu-id="6cfb2-111">dotnet-svcutil 2.x</span></span>](#tab/dotnetsvcutil2x)

- <span data-ttu-id="6cfb2-112">[.NET Core 2.1 SDK](https://dotnet.microsoft.com/download) veya sonraki sürümler</span><span class="sxs-lookup"><span data-stu-id="6cfb2-112">[.NET Core 2.1 SDK](https://dotnet.microsoft.com/download) or later versions</span></span>
- <span data-ttu-id="6cfb2-113">En sevdiğiniz kod düzenleyicisi</span><span class="sxs-lookup"><span data-stu-id="6cfb2-113">Your favorite code editor</span></span>

# <a name="dotnet-svcutil-1x"></a>[<span data-ttu-id="6cfb2-114">dotnet-svcutil 1.x</span><span class="sxs-lookup"><span data-stu-id="6cfb2-114">dotnet-svcutil 1.x</span></span>](#tab/dotnetsvcutil1x)

- <span data-ttu-id="6cfb2-115">[.NET Core 1.0.4 SDK](https://dotnet.microsoft.com/download) veya sonraki sürümler</span><span class="sxs-lookup"><span data-stu-id="6cfb2-115">[.NET Core 1.0.4 SDK](https://dotnet.microsoft.com/download) or later versions</span></span>
- <span data-ttu-id="6cfb2-116">En sevdiğiniz kod düzenleyicisi</span><span class="sxs-lookup"><span data-stu-id="6cfb2-116">Your favorite code editor</span></span>

---

## <a name="getting-started"></a><span data-ttu-id="6cfb2-117">Başlarken</span><span class="sxs-lookup"><span data-stu-id="6cfb2-117">Getting started</span></span>

<span data-ttu-id="6cfb2-118">Aşağıdaki örnek, bir .NET Core web projesine bir web hizmeti başvurusu eklemek ve hizmeti çağırmak için gereken adımları size iletir.</span><span class="sxs-lookup"><span data-stu-id="6cfb2-118">The following example walks you through the steps required to add a web service reference to a .NET Core web project and invoke the service.</span></span> <span data-ttu-id="6cfb2-119">*HelloSvcutil* adında bir .NET Core web uygulaması oluşturacak ve aşağıdaki sözleşmeyi uygulayan bir web hizmetine başvuru ekleyeceğiz:</span><span class="sxs-lookup"><span data-stu-id="6cfb2-119">You'll create a .NET Core web application named *HelloSvcutil* and add a reference to a web service that implements the following contract:</span></span>

```csharp
[ServiceContract]
public interface ISayHello
{
    [OperationContract]
    string Hello(string name);
}
```

<span data-ttu-id="6cfb2-120">Bu örnekiçin, web hizmetinin aşağıdaki adreste barındırılan olacağını varsayalım:`http://contoso.com/SayHello.svc`</span><span class="sxs-lookup"><span data-stu-id="6cfb2-120">For this example, let's assume the web service will be hosted at the following address: `http://contoso.com/SayHello.svc`</span></span>

<span data-ttu-id="6cfb2-121">Windows, macOS veya Linux komut penceresinden aşağıdaki adımları gerçekleştirin:</span><span class="sxs-lookup"><span data-stu-id="6cfb2-121">From a Windows, macOS, or Linux command window perform the following steps:</span></span>

1. <span data-ttu-id="6cfb2-122">Projeniz için _HelloSvcutil_ adında bir dizin oluşturun ve aşağıdaki örnekte olduğu gibi geçerli dizininiz olsun:</span><span class="sxs-lookup"><span data-stu-id="6cfb2-122">Create a directory named _HelloSvcutil_ for your project and make it your current directory, as in the following example:</span></span>

    ```console
    mkdir HelloSvcutil
    cd HelloSvcutil
    ```

2. <span data-ttu-id="6cfb2-123">Aşağıdaki komutu [`dotnet new`](../tools/dotnet-new.md) kullanarak bu dizinde yeni bir C# web projesi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="6cfb2-123">Create a new C# web project in that directory using the [`dotnet new`](../tools/dotnet-new.md) command as follows:</span></span>

    ```dotnetcli
    dotnet new web
    ```

3. <span data-ttu-id="6cfb2-124">[ `dotnet-svcutil` NuGet paketini](https://nuget.org/packages/dotnet-svcutil) CLI aracı olarak yükleyin: </span><span class="sxs-lookup"><span data-stu-id="6cfb2-124">Install the [`dotnet-svcutil` NuGet package](https://nuget.org/packages/dotnet-svcutil) as a CLI tool:  </span></span><!-- markdownlint-disable MD023 -->
    # <a name="dotnet-svcutil-2x"></a>[<span data-ttu-id="6cfb2-125">dotnet-svcutil 2.x</span><span class="sxs-lookup"><span data-stu-id="6cfb2-125">dotnet-svcutil 2.x</span></span>](#tab/dotnetsvcutil2x)

    ```dotnetcli
    dotnet tool install --global dotnet-svcutil
    ```

    # <a name="dotnet-svcutil-1x"></a>[<span data-ttu-id="6cfb2-126">dotnet-svcutil 1.x</span><span class="sxs-lookup"><span data-stu-id="6cfb2-126">dotnet-svcutil 1.x</span></span>](#tab/dotnetsvcutil1x)
    <span data-ttu-id="6cfb2-127">Proje `HelloSvcutil.csproj` dosyasını düzenleyicinizde açın, `Project` öğeyi düzenlemeyi ve [ `dotnet-svcutil` NuGet paketini](https://nuget.org/packages/dotnet-svcutil) aşağıdaki kodu kullanarak CLI araç başvurusu olarak ekleyin:</span><span class="sxs-lookup"><span data-stu-id="6cfb2-127">Open the `HelloSvcutil.csproj` project file in your editor, edit the `Project` element, and add the [`dotnet-svcutil` NuGet package](https://nuget.org/packages/dotnet-svcutil) as a CLI tool reference, using the following code:</span></span>

    ```xml
    <ItemGroup>
      <DotNetCliToolReference Include="dotnet-svcutil" Version="1.0.*" />
    </ItemGroup>
    ```

    <span data-ttu-id="6cfb2-128">Sonra aşağıdaki komutu kullanarak _dotnet-svcutil_ paketini geri yükleyin: [`dotnet restore`](../tools/dotnet-restore.md)</span><span class="sxs-lookup"><span data-stu-id="6cfb2-128">Then restore the _dotnet-svcutil_ package using the [`dotnet restore`](../tools/dotnet-restore.md) command as follows:</span></span>

    ```dotnetcli
    dotnet restore
    ```

    ---

4. <span data-ttu-id="6cfb2-129">Web hizmeti başvuru dosyasını oluşturmak için _dotnet-svcutil_ komutunu aşağıdaki gibi çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="6cfb2-129">Run the _dotnet-svcutil_ command to generate the web service reference file as follows:</span></span>

    # <a name="dotnet-svcutil-2x"></a>[<span data-ttu-id="6cfb2-130">dotnet-svcutil 2.x</span><span class="sxs-lookup"><span data-stu-id="6cfb2-130">dotnet-svcutil 2.x</span></span>](#tab/dotnetsvcutil2x)

    ```dotnetcli
    dotnet-svcutil http://contoso.com/SayHello.svc
    ```

    # <a name="dotnet-svcutil-1x"></a>[<span data-ttu-id="6cfb2-131">dotnet-svcutil 1.x</span><span class="sxs-lookup"><span data-stu-id="6cfb2-131">dotnet-svcutil 1.x</span></span>](#tab/dotnetsvcutil1x)

    ```dotnetcli
    dotnet svcutil http://contoso.com/SayHello.svc
    ```

    ---

<span data-ttu-id="6cfb2-132">Oluşturulan dosya _HelloSvcutil/ServiceReference/Reference.cs_olarak kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="6cfb2-132">The generated file is saved as _HelloSvcutil/ServiceReference/Reference.cs_.</span></span> <span data-ttu-id="6cfb2-133">_Dotnet-svcutil_ aracı, proxy kodunun gerektirdiği uygun WCF paketlerini de paket referansolarak projeye ekler.</span><span class="sxs-lookup"><span data-stu-id="6cfb2-133">The _dotnet-svcutil_ tool also adds to the project the appropriate WCF packages required by the proxy code as package references.</span></span>

## <a name="using-the-service-reference"></a><span data-ttu-id="6cfb2-134">Hizmet Başvuruyu Kullanma</span><span class="sxs-lookup"><span data-stu-id="6cfb2-134">Using the Service Reference</span></span>

1. <span data-ttu-id="6cfb2-135">Aşağıdaki komutu kullanarak [`dotnet restore`](../tools/dotnet-restore.md) WCF paketlerini geri yükleyin:</span><span class="sxs-lookup"><span data-stu-id="6cfb2-135">Restore the WCF packages using the [`dotnet restore`](../tools/dotnet-restore.md) command as follows:</span></span>

    ```dotnetcli
    dotnet restore
    ```

2. <span data-ttu-id="6cfb2-136">Kullanmak istediğiniz istemci sınıfının ve işlemin adını bulun.</span><span class="sxs-lookup"><span data-stu-id="6cfb2-136">Find the name of the client class and operation you want to use.</span></span> <span data-ttu-id="6cfb2-137">`Reference.cs`hizmetteki işlemleri çağırmak için `System.ServiceModel.ClientBase`kullanılabilecek yöntemlerle devralan bir sınıf içerir.</span><span class="sxs-lookup"><span data-stu-id="6cfb2-137">`Reference.cs` will contain a class that inherits from `System.ServiceModel.ClientBase`, with methods that can be used to call operations on the service.</span></span> <span data-ttu-id="6cfb2-138">Bu örnekte, _SayHello_ hizmetinin _Merhaba_ işlemini aramak istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="6cfb2-138">In this example, you want to call the _SayHello_ service's _Hello_ operation.</span></span> <span data-ttu-id="6cfb2-139">`ServiceReference.SayHelloClient`istemci sınıfın adıdır ve işlemi çağırmak `HelloAsync` için kullanılabilecek bir yöntem vardır.</span><span class="sxs-lookup"><span data-stu-id="6cfb2-139">`ServiceReference.SayHelloClient` is the name of the client class, and has a method called `HelloAsync` that can be used to call the operation.</span></span>

3. <span data-ttu-id="6cfb2-140">Düzenleyicinizdeki `Startup.cs` dosyayı açın ve en üstteki hizmet başvuru ad alanı için bir kullanım deyimi ekleyin:</span><span class="sxs-lookup"><span data-stu-id="6cfb2-140">Open the `Startup.cs` file in your editor, and add a using statement for the service reference namespace at the top:</span></span>

    ```csharp
    using ServiceReference;
    ```

4. <span data-ttu-id="6cfb2-141">Web hizmetini `Configure` çağırmak için yöntemi edin.</span><span class="sxs-lookup"><span data-stu-id="6cfb2-141">Edit the `Configure` method to invoke the web service.</span></span> <span data-ttu-id="6cfb2-142">Bunu, istemci nesnesinden devralan sınıfın bir `ClientBase` örneğini oluşturarak ve yöntemi istemci nesnesi üzerinde çağırarak yaparsınız:</span><span class="sxs-lookup"><span data-stu-id="6cfb2-142">You do this by creating an instance of the class that inherits from `ClientBase` and calling the method on the client object:</span></span>

    ```csharp
    public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
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

5. <span data-ttu-id="6cfb2-143">Aşağıdaki komutu [`dotnet run`](../tools/dotnet-run.md) kullanarak uygulamayı çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="6cfb2-143">Run the application using the [`dotnet run`](../tools/dotnet-run.md) command as follows:</span></span>

    ```dotnetcli
    dotnet run
    ```

6. <span data-ttu-id="6cfb2-144">Konsolda listelenen URL'ye (örneğin, `http://localhost:5000`web tarayıcınızda) gidin.</span><span class="sxs-lookup"><span data-stu-id="6cfb2-144">Navigate to the URL listed in the console (for example, `http://localhost:5000`) in your web browser.</span></span>

<span data-ttu-id="6cfb2-145">Aşağıdaki çıktıyı görmelisiniz: "Merhaba dotnet-svcutil!"</span><span class="sxs-lookup"><span data-stu-id="6cfb2-145">You should see the following output: "Hello dotnet-svcutil!"</span></span>

<span data-ttu-id="6cfb2-146">`dotnet-svcutil` Takım parametrelerinin ayrıntılı bir açıklaması için, yardım parametresini aşağıdaki gibi geçen aracı çağırın:</span><span class="sxs-lookup"><span data-stu-id="6cfb2-146">For a detailed description of the `dotnet-svcutil` tool parameters, invoke the tool passing the help parameter as follows:</span></span>
# <a name="dotnet-svcutil-2x"></a>[<span data-ttu-id="6cfb2-147">dotnet-svcutil 2.x</span><span class="sxs-lookup"><span data-stu-id="6cfb2-147">dotnet-svcutil 2.x</span></span>](#tab/dotnetsvcutil2x)

```dotnetcli
dotnet-svcutil --help
```

# <a name="dotnet-svcutil-1x"></a>[<span data-ttu-id="6cfb2-148">dotnet-svcutil 1.x</span><span class="sxs-lookup"><span data-stu-id="6cfb2-148">dotnet-svcutil 1.x</span></span>](#tab/dotnetsvcutil1x)

```dotnetcli
dotnet svcutil --help
```

---

## <a name="feedback--questions"></a><span data-ttu-id="6cfb2-149">Geri bildirim & sorular</span><span class="sxs-lookup"><span data-stu-id="6cfb2-149">Feedback & questions</span></span>

<span data-ttu-id="6cfb2-150">Herhangi bir sorunuz veya geri bildiriminiz varsa, [GitHub'da bir sorun açın.](https://github.com/dotnet/wcf/issues/new)</span><span class="sxs-lookup"><span data-stu-id="6cfb2-150">If you have any questions or feedback, [open an issue on GitHub](https://github.com/dotnet/wcf/issues/new).</span></span> <span data-ttu-id="6cfb2-151">Ayrıca [GitHub'daki WCF repo'sunda](https://github.com/dotnet/wcf/issues?utf8=%E2%9C%93&q=is:issue%20label:tooling)varolan tüm soruları veya sorunları inceleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6cfb2-151">You can also review any existing questions or issues [at the WCF repo on GitHub](https://github.com/dotnet/wcf/issues?utf8=%E2%9C%93&q=is:issue%20label:tooling).</span></span>

## <a name="release-notes"></a><span data-ttu-id="6cfb2-152">Sürüm notları</span><span class="sxs-lookup"><span data-stu-id="6cfb2-152">Release notes</span></span>

- <span data-ttu-id="6cfb2-153">Bilinen sorunlar da dahil olmak üzere güncelleştirilmiş sürüm bilgileri için [Yayın notlarına](https://github.com/dotnet/wcf/blob/master/release-notes/dotnet-svcutil-notes.md) bakın.</span><span class="sxs-lookup"><span data-stu-id="6cfb2-153">Refer to the [Release notes](https://github.com/dotnet/wcf/blob/master/release-notes/dotnet-svcutil-notes.md) for updated release information, including known issues.</span></span>

## <a name="information"></a><span data-ttu-id="6cfb2-154">Bilgi</span><span class="sxs-lookup"><span data-stu-id="6cfb2-154">Information</span></span>

- [<span data-ttu-id="6cfb2-155">dotnet-svcutil NuGet Paketi</span><span class="sxs-lookup"><span data-stu-id="6cfb2-155">dotnet-svcutil NuGet Package</span></span>](https://nuget.org/packages/dotnet-svcutil)
