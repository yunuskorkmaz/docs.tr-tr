---
title: WCF Svcutil aracına genel bakış
description: .NET Framework projelerine yönelik WCF Svcutil aracına benzer şekilde .NET Core ve ASP.NET Core projelerine yönelik işlevler ekleyen Microsoft WCF DotNet-Svcutil aracına genel bakış.
author: mlacouture
ms.date: 02/22/2019
ms.custom: seodec18
ms.openlocfilehash: 89fe72c8116498ff60d439ce17ef2e857edf621e
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72771977"
---
# <a name="wcf-dotnet-svcutil-tool-for-net-core"></a><span data-ttu-id="6d30b-103">.NET Core için WCF DotNet-Svcutil aracı</span><span class="sxs-lookup"><span data-stu-id="6d30b-103">WCF dotnet-svcutil tool for .NET Core</span></span>

<span data-ttu-id="6d30b-104">Windows Communication Foundation (WCF) **DotNet-Svcutil** Aracı, bir ağ konumundaki veya bir wsdl dosyasındaki bir Web hizmetinden meta verileri alan ve Web hizmetine erişen istemci proxy yöntemleri IÇEREN bir WCF sınıfı oluşturan bir .NET Core CLI aracıdır operasyonları.</span><span class="sxs-lookup"><span data-stu-id="6d30b-104">The Windows Communication Foundation (WCF) **dotnet-svcutil** tool is a .NET Core CLI tool that retrieves metadata from a web service on a network location or from a WSDL file, and generates a WCF class containing client proxy methods that access the web service operations.</span></span>

<span data-ttu-id="6d30b-105">.NET Framework projelerine yönelik [**hizmet modeli meta verileri-Svcutil**](../../framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) aracına benzer şekilde **DotNet-Svcutil** , .NET Core ve .NET Standard projeleriyle uyumlu bir Web hizmeti başvurusu oluşturmaya yönelik bir komut satırı aracıdır.</span><span class="sxs-lookup"><span data-stu-id="6d30b-105">Similar to the [**Service Model Metadata - svcutil**](../../framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) tool for .NET Framework projects, the **dotnet-svcutil** is a command-line tool for generating a web service reference compatible with .NET Core and .NET Standard projects.</span></span>

<span data-ttu-id="6d30b-106">**DotNet-Svcutil** Aracı, Ilk olarak visual Studio 2017 sürüm 15,5 ile birlikte gelen [**WCF Web hizmeti başvurusu**](wcf-web-service-reference-guide.md) Visual Studio bağlı hizmet sağlayıcısına alternatif bir seçenektir.</span><span class="sxs-lookup"><span data-stu-id="6d30b-106">The **dotnet-svcutil** tool is an alternative option to the [**WCF Web Service Reference**](wcf-web-service-reference-guide.md) Visual Studio connected service provider that first shipped with Visual Studio 2017 version 15.5.</span></span> <span data-ttu-id="6d30b-107">.NET Core CLI aracı olarak **DotNet-Svcutil** Aracı, Linux, MacOS ve Windows üzerinde platformlar arası kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="6d30b-107">The **dotnet-svcutil** tool as a .NET Core CLI tool, is available cross-platform on Linux, macOS, and Windows.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6d30b-108">Yalnızca güvenilir bir kaynaktan hizmetlere başvurmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="6d30b-108">You should only reference services from a trusted source.</span></span> <span data-ttu-id="6d30b-109">Güvenilmeyen bir kaynaktan başvuruları eklemek güvenliği tehlikeye atabilir.</span><span class="sxs-lookup"><span data-stu-id="6d30b-109">Adding references from an untrusted source may compromise security.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="6d30b-110">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="6d30b-110">Prerequisites</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="dotnet-svcutil-2xtabdotnetsvcutil2x"></a>[<span data-ttu-id="6d30b-111">DotNet-Svcutil 2. x</span><span class="sxs-lookup"><span data-stu-id="6d30b-111">dotnet-svcutil 2.x</span></span>](#tab/dotnetsvcutil2x)

- <span data-ttu-id="6d30b-112">[.NET Core 2,1 SDK](https://dotnet.microsoft.com/download) veya sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="6d30b-112">[.NET Core 2.1 SDK](https://dotnet.microsoft.com/download) or later versions</span></span>
- <span data-ttu-id="6d30b-113">En sevdiğiniz kod düzenleyiciniz</span><span class="sxs-lookup"><span data-stu-id="6d30b-113">Your favorite code editor</span></span>

# <a name="dotnet-svcutil-1xtabdotnetsvcutil1x"></a>[<span data-ttu-id="6d30b-114">DotNet-Svcutil 1. x</span><span class="sxs-lookup"><span data-stu-id="6d30b-114">dotnet-svcutil 1.x</span></span>](#tab/dotnetsvcutil1x)

- <span data-ttu-id="6d30b-115">[.NET Core 1.0.4 SDK](https://dotnet.microsoft.com/download) veya sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="6d30b-115">[.NET Core 1.0.4 SDK](https://dotnet.microsoft.com/download) or later versions</span></span>
- <span data-ttu-id="6d30b-116">En sevdiğiniz kod düzenleyiciniz</span><span class="sxs-lookup"><span data-stu-id="6d30b-116">Your favorite code editor</span></span>

---

## <a name="getting-started"></a><span data-ttu-id="6d30b-117">Başlarken</span><span class="sxs-lookup"><span data-stu-id="6d30b-117">Getting started</span></span>

<span data-ttu-id="6d30b-118">Aşağıdaki örnek, bir .NET Core Web projesine Web hizmeti başvurusu eklemek ve hizmeti çağırmak için gereken adımlarda size yol gösterir.</span><span class="sxs-lookup"><span data-stu-id="6d30b-118">The following example walks you through the steps required to add a web service reference to a .NET Core web project and invoke the service.</span></span> <span data-ttu-id="6d30b-119">*Merhaba Svcutil* adlı bir .NET Core Web uygulaması oluşturacak ve aşağıdaki sözleşmeyi uygulayan bir Web hizmetine başvuru ekleyeceğiz:</span><span class="sxs-lookup"><span data-stu-id="6d30b-119">You'll create a .NET Core web application named *HelloSvcutil* and add a reference to a web service that implements the following contract:</span></span>

```csharp
[ServiceContract]
public interface ISayHello
{
    [OperationContract]
    string Hello(string name);
}
```

<span data-ttu-id="6d30b-120">Bu örnekte, Web hizmetinin şu adreste barındırıldığını varsayalım: `http://contoso.com/SayHello.svc`</span><span class="sxs-lookup"><span data-stu-id="6d30b-120">For this example, let's assume the web service will be hosted at the following address: `http://contoso.com/SayHello.svc`</span></span>

<span data-ttu-id="6d30b-121">Bir Windows, macOS veya Linux komut penceresinde aşağıdaki adımları uygulayın:</span><span class="sxs-lookup"><span data-stu-id="6d30b-121">From a Windows, macOS, or Linux command window perform the following steps:</span></span>

1. <span data-ttu-id="6d30b-122">Projeniz için _Hellosvcutil_ adlı bir dizin oluşturun ve aşağıdaki örnekte olduğu gibi geçerli dizininiz yapın:</span><span class="sxs-lookup"><span data-stu-id="6d30b-122">Create a directory named _HelloSvcutil_ for your project and make it your current directory, as in the following example:</span></span>

    ```console
    mkdir HelloSvcutil
    cd HelloSvcutil
    ```

2. <span data-ttu-id="6d30b-123">Aşağıdaki şekilde C# [`dotnet new`](../tools/dotnet-new.md) komutunu kullanarak bu dizinde yeni bir Web projesi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="6d30b-123">Create a new C# web project in that directory using the [`dotnet new`](../tools/dotnet-new.md) command as follows:</span></span>

    ```dotnetcli
    dotnet new web
    ```

3. <span data-ttu-id="6d30b-124">[@No__t_1 NuGet PAKETINI](https://nuget.org/packages/dotnet-svcutil) CLI aracı olarak yükler:  </span><span class="sxs-lookup"><span data-stu-id="6d30b-124">Install the [`dotnet-svcutil` NuGet package](https://nuget.org/packages/dotnet-svcutil) as a CLI tool:  </span></span><!-- markdownlint-disable MD023 -->
    # <a name="dotnet-svcutil-2xtabdotnetsvcutil2x"></a>[<span data-ttu-id="6d30b-125">DotNet-Svcutil 2. x</span><span class="sxs-lookup"><span data-stu-id="6d30b-125">dotnet-svcutil 2.x</span></span>](#tab/dotnetsvcutil2x)

    ```dotnetcli
    dotnet tool install --global dotnet-svcutil
    ```

    # <a name="dotnet-svcutil-1xtabdotnetsvcutil1x"></a>[<span data-ttu-id="6d30b-126">DotNet-Svcutil 1. x</span><span class="sxs-lookup"><span data-stu-id="6d30b-126">dotnet-svcutil 1.x</span></span>](#tab/dotnetsvcutil1x)
    <span data-ttu-id="6d30b-127">@No__t_0 proje dosyasını Düzenleyicinizde açın, `Project` öğesini düzenleyin ve aşağıdaki kodu kullanarak bir CLı araç başvurusu olarak [`dotnet-svcutil` NuGet paketini](https://nuget.org/packages/dotnet-svcutil) ekleyin:</span><span class="sxs-lookup"><span data-stu-id="6d30b-127">Open the `HelloSvcutil.csproj` project file in your editor, edit the `Project` element, and add the [`dotnet-svcutil` NuGet package](https://nuget.org/packages/dotnet-svcutil) as a CLI tool reference, using the following code:</span></span>

    ```xml
    <ItemGroup>
      <DotNetCliToolReference Include="dotnet-svcutil" Version="1.0.*" />
    </ItemGroup>
    ```

    <span data-ttu-id="6d30b-128">Daha sonra [`dotnet restore`](../tools/dotnet-restore.md) komutunu kullanarak _DotNet-Svcutil_ paketini aşağıdaki gibi geri yükleyin:</span><span class="sxs-lookup"><span data-stu-id="6d30b-128">Then restore the _dotnet-svcutil_ package using the [`dotnet restore`](../tools/dotnet-restore.md) command as follows:</span></span>

    ```dotnetcli
    dotnet restore
    ```

    ---

4. <span data-ttu-id="6d30b-129">Web hizmeti başvuru dosyasını aşağıdaki gibi oluşturmak için _DotNet-Svcutil_ komutunu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="6d30b-129">Run the _dotnet-svcutil_ command to generate the web service reference file as follows:</span></span>

    # <a name="dotnet-svcutil-2xtabdotnetsvcutil2x"></a>[<span data-ttu-id="6d30b-130">DotNet-Svcutil 2. x</span><span class="sxs-lookup"><span data-stu-id="6d30b-130">dotnet-svcutil 2.x</span></span>](#tab/dotnetsvcutil2x)

    ```dotnetcli
    dotnet-svcutil http://contoso.com/SayHello.svc
    ```

    # <a name="dotnet-svcutil-1xtabdotnetsvcutil1x"></a>[<span data-ttu-id="6d30b-131">DotNet-Svcutil 1. x</span><span class="sxs-lookup"><span data-stu-id="6d30b-131">dotnet-svcutil 1.x</span></span>](#tab/dotnetsvcutil1x)

    ```dotnetcli
    dotnet svcutil http://contoso.com/SayHello.svc
    ```

    ---

<span data-ttu-id="6d30b-132">Oluşturulan dosya _Merhaba Svcutil/ServiceReference/Reference. cs_olarak kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="6d30b-132">The generated file is saved as _HelloSvcutil/ServiceReference/Reference.cs_.</span></span> <span data-ttu-id="6d30b-133">_DotNet-Svcutil_ aracı Ayrıca, proxy kodunun paket başvuruları olarak gerekli olan uygun WCF paketlerini projeye ekler.</span><span class="sxs-lookup"><span data-stu-id="6d30b-133">The _dotnet-svcutil_ tool also adds to the project the appropriate WCF packages required by the proxy code as package references.</span></span>

## <a name="using-the-service-reference"></a><span data-ttu-id="6d30b-134">Hizmet başvurusunu kullanma</span><span class="sxs-lookup"><span data-stu-id="6d30b-134">Using the Service Reference</span></span>

1. <span data-ttu-id="6d30b-135">[@No__t_1](../tools/dotnet-restore.md) komutunu kullanarak WCF paketlerini aşağıdaki şekilde geri yükleyin:</span><span class="sxs-lookup"><span data-stu-id="6d30b-135">Restore the WCF packages using the [`dotnet restore`](../tools/dotnet-restore.md) command as follows:</span></span>

    ```dotnetcli
    dotnet restore
    ```

2. <span data-ttu-id="6d30b-136">Kullanmak istediğiniz istemci sınıfının ve işlemin adını bulun.</span><span class="sxs-lookup"><span data-stu-id="6d30b-136">Find the name of the client class and operation you want to use.</span></span> <span data-ttu-id="6d30b-137">`Reference.cs`, hizmet üzerindeki işlemleri çağırmak için kullanılabilecek yöntemler ile `System.ServiceModel.ClientBase` devralan bir sınıf içerir.</span><span class="sxs-lookup"><span data-stu-id="6d30b-137">`Reference.cs` will contain a class that inherits from `System.ServiceModel.ClientBase`, with methods that can be used to call operations on the service.</span></span> <span data-ttu-id="6d30b-138">Bu örnekte, _SayHello_ hizmetinin _Hello_ işlemini çağırmak istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="6d30b-138">In this example, you want to call the _SayHello_ service's _Hello_ operation.</span></span> <span data-ttu-id="6d30b-139">`ServiceReference.SayHelloClient`, istemci sınıfının adıdır ve işlemi çağırmak için kullanılabilecek `HelloAsync` adlı bir yöntemi vardır.</span><span class="sxs-lookup"><span data-stu-id="6d30b-139">`ServiceReference.SayHelloClient` is the name of the client class, and has a method called `HelloAsync` that can be used to call the operation.</span></span>

3. <span data-ttu-id="6d30b-140">@No__t_0 dosyasını Düzenleyicinizde açın ve en üstteki hizmet başvurusu ad alanı için bir using ifadesini ekleyin:</span><span class="sxs-lookup"><span data-stu-id="6d30b-140">Open the `Startup.cs` file in your editor, and add a using statement for the service reference namespace at the top:</span></span>

    ```csharp
    using ServiceReference;
    ```

4. <span data-ttu-id="6d30b-141">Web hizmetini çağırmak için `Configure` yöntemini düzenleyin.</span><span class="sxs-lookup"><span data-stu-id="6d30b-141">Edit the `Configure` method to invoke the web service.</span></span> <span data-ttu-id="6d30b-142">Bunu, `ClientBase` devralan ve istemci nesnesinde yöntemi çağıran sınıfının bir örneğini oluşturarak yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="6d30b-142">You do this by creating an instance of the class that inherits from `ClientBase` and calling the method on the client object:</span></span>

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

5. <span data-ttu-id="6d30b-143">[@No__t_1](../tools/dotnet-run.md) komutunu kullanarak uygulamayı aşağıdaki şekilde çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="6d30b-143">Run the application using the [`dotnet run`](../tools/dotnet-run.md) command as follows:</span></span>

    ```dotnetcli
    dotnet run
    ```

6. <span data-ttu-id="6d30b-144">Web tarayıcınızda konsolunda listelenen URL 'ye gidin (örneğin, `http://localhost:5000`).</span><span class="sxs-lookup"><span data-stu-id="6d30b-144">Navigate to the URL listed in the console (for example, `http://localhost:5000`) in your web browser.</span></span>

<span data-ttu-id="6d30b-145">Şu çıktıyı görmeniz gerekir: "Hello DotNet-Svcutil!"</span><span class="sxs-lookup"><span data-stu-id="6d30b-145">You should see the following output: "Hello dotnet-svcutil!"</span></span>

<span data-ttu-id="6d30b-146">@No__t_0 aracı parametrelerinin ayrıntılı bir açıklaması için, yardım parametresini aşağıdaki gibi geçirerek aracı çağırın:</span><span class="sxs-lookup"><span data-stu-id="6d30b-146">For a detailed description of the `dotnet-svcutil` tool parameters, invoke the tool passing the help parameter as follows:</span></span>
# <a name="dotnet-svcutil-2xtabdotnetsvcutil2x"></a>[<span data-ttu-id="6d30b-147">DotNet-Svcutil 2. x</span><span class="sxs-lookup"><span data-stu-id="6d30b-147">dotnet-svcutil 2.x</span></span>](#tab/dotnetsvcutil2x)

```dotnetcli
dotnet-svcutil --help
```

# <a name="dotnet-svcutil-1xtabdotnetsvcutil1x"></a>[<span data-ttu-id="6d30b-148">DotNet-Svcutil 1. x</span><span class="sxs-lookup"><span data-stu-id="6d30b-148">dotnet-svcutil 1.x</span></span>](#tab/dotnetsvcutil1x)

```dotnetcli
dotnet svcutil --help
```

---

## <a name="feedback--questions"></a><span data-ttu-id="6d30b-149">Geri bildirim & soruları</span><span class="sxs-lookup"><span data-stu-id="6d30b-149">Feedback & questions</span></span>

<span data-ttu-id="6d30b-150">Sorularınız veya geri bildiriminiz varsa [GitHub ' da bir sorun açın](https://github.com/dotnet/wcf/issues/new).</span><span class="sxs-lookup"><span data-stu-id="6d30b-150">If you have any questions or feedback, [open an issue on GitHub](https://github.com/dotnet/wcf/issues/new).</span></span> <span data-ttu-id="6d30b-151">Ayrıca, [GitHub 'DAKI WCF](https://github.com/dotnet/wcf/issues?utf8=%E2%9C%93&q=is:issue%20label:tooling)deposundaki mevcut soruları veya sorunları da inceleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6d30b-151">You can also review any existing questions or issues [at the WCF repo on GitHub](https://github.com/dotnet/wcf/issues?utf8=%E2%9C%93&q=is:issue%20label:tooling).</span></span>

## <a name="release-notes"></a><span data-ttu-id="6d30b-152">Sürüm notları</span><span class="sxs-lookup"><span data-stu-id="6d30b-152">Release notes</span></span>

- <span data-ttu-id="6d30b-153">Bilinen sorunlar da dahil olmak üzere, güncelleştirilmiş sürüm bilgileri için [sürüm notlarına](https://github.com/dotnet/wcf/blob/master/release-notes/dotnet-svcutil-notes.md) bakın.</span><span class="sxs-lookup"><span data-stu-id="6d30b-153">Refer to the [Release notes](https://github.com/dotnet/wcf/blob/master/release-notes/dotnet-svcutil-notes.md) for updated release information, including known issues.</span></span>

## <a name="information"></a><span data-ttu-id="6d30b-154">Bilgiler</span><span class="sxs-lookup"><span data-stu-id="6d30b-154">Information</span></span>

- [<span data-ttu-id="6d30b-155">DotNet-Svcutil NuGet paketi</span><span class="sxs-lookup"><span data-stu-id="6d30b-155">dotnet-svcutil NuGet Package</span></span>](https://nuget.org/packages/dotnet-svcutil)
