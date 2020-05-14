---
title: WCF Svcutil aracına genel bakış
description: .NET Framework projelerine yönelik WCF Svcutil aracına benzer şekilde .NET Core ve ASP.NET Core projelerine yönelik işlevler ekleyen Microsoft WCF DotNet-Svcutil aracına genel bakış.
author: mlacouture
ms.date: 02/22/2019
ms.openlocfilehash: fde42f7d040fba91f51ce6faa58282ed0206a853
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396216"
---
# <a name="wcf-dotnet-svcutil-tool-for-net-core"></a><span data-ttu-id="96191-103">.NET Core için WCF DotNet-Svcutil aracı</span><span class="sxs-lookup"><span data-stu-id="96191-103">WCF dotnet-svcutil tool for .NET Core</span></span>

<span data-ttu-id="96191-104">Windows Communication Foundation (WCF) **DotNet-Svcutil** Aracı, bir ağ konumundaki veya bir wsdl dosyasındaki bir Web hizmetinden meta verileri alan ve Web hizmeti işlemlerine erişen istemci proxy yöntemlerini IÇEREN bir WCF sınıfı oluşturan bir .net aracıdır.</span><span class="sxs-lookup"><span data-stu-id="96191-104">The Windows Communication Foundation (WCF) **dotnet-svcutil** tool is a .NET tool that retrieves metadata from a web service on a network location or from a WSDL file, and generates a WCF class containing client proxy methods that access the web service operations.</span></span>

<span data-ttu-id="96191-105">.NET Framework projelerine yönelik [**hizmet modeli meta verileri-Svcutil**](../../framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) aracına benzer şekilde **DotNet-Svcutil** , .NET Core ve .NET Standard projeleriyle uyumlu bir Web hizmeti başvurusu oluşturmaya yönelik bir komut satırı aracıdır.</span><span class="sxs-lookup"><span data-stu-id="96191-105">Similar to the [**Service Model Metadata - svcutil**](../../framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) tool for .NET Framework projects, the **dotnet-svcutil** is a command-line tool for generating a web service reference compatible with .NET Core and .NET Standard projects.</span></span>

<span data-ttu-id="96191-106">**DotNet-Svcutil** Aracı, Ilk olarak visual Studio 2017 sürüm 15,5 ile birlikte gelen [**WCF Web hizmeti başvurusu**](wcf-web-service-reference-guide.md) Visual Studio bağlı hizmet sağlayıcısına alternatif bir seçenektir.</span><span class="sxs-lookup"><span data-stu-id="96191-106">The **dotnet-svcutil** tool is an alternative option to the [**WCF Web Service Reference**](wcf-web-service-reference-guide.md) Visual Studio connected service provider that first shipped with Visual Studio 2017 version 15.5.</span></span> <span data-ttu-id="96191-107">.NET aracı olarak **DotNet-Svcutil** Aracı, Linux, MacOS ve Windows üzerinde platformlar arası kullanıma sunulmuştur.</span><span class="sxs-lookup"><span data-stu-id="96191-107">The **dotnet-svcutil** tool as a .NET tool, is available cross-platform on Linux, macOS, and Windows.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="96191-108">Yalnızca güvenilir bir kaynaktan hizmetlere başvurmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="96191-108">You should only reference services from a trusted source.</span></span> <span data-ttu-id="96191-109">Güvenilmeyen bir kaynaktan başvuruları eklemek güvenliği tehlikeye atabilir.</span><span class="sxs-lookup"><span data-stu-id="96191-109">Adding references from an untrusted source may compromise security.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="96191-110">Ön koşullar</span><span class="sxs-lookup"><span data-stu-id="96191-110">Prerequisites</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="dotnet-svcutil-2x"></a>[<span data-ttu-id="96191-111">DotNet-Svcutil 2. x</span><span class="sxs-lookup"><span data-stu-id="96191-111">dotnet-svcutil 2.x</span></span>](#tab/dotnetsvcutil2x)

- <span data-ttu-id="96191-112">[.NET Core 2,1 SDK](https://dotnet.microsoft.com/download) veya sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="96191-112">[.NET Core 2.1 SDK](https://dotnet.microsoft.com/download) or later versions</span></span>
- <span data-ttu-id="96191-113">En sevdiğiniz kod düzenleyiciniz</span><span class="sxs-lookup"><span data-stu-id="96191-113">Your favorite code editor</span></span>

# <a name="dotnet-svcutil-1x"></a>[<span data-ttu-id="96191-114">DotNet-Svcutil 1. x</span><span class="sxs-lookup"><span data-stu-id="96191-114">dotnet-svcutil 1.x</span></span>](#tab/dotnetsvcutil1x)

- <span data-ttu-id="96191-115">[.NET Core 1.0.4 SDK](https://dotnet.microsoft.com/download) veya sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="96191-115">[.NET Core 1.0.4 SDK](https://dotnet.microsoft.com/download) or later versions</span></span>
- <span data-ttu-id="96191-116">En sevdiğiniz kod düzenleyiciniz</span><span class="sxs-lookup"><span data-stu-id="96191-116">Your favorite code editor</span></span>

---

## <a name="getting-started"></a><span data-ttu-id="96191-117">Başlarken</span><span class="sxs-lookup"><span data-stu-id="96191-117">Getting started</span></span>

<span data-ttu-id="96191-118">Aşağıdaki örnek, bir .NET Core Web projesine Web hizmeti başvurusu eklemek ve hizmeti çağırmak için gereken adımlarda size yol gösterir.</span><span class="sxs-lookup"><span data-stu-id="96191-118">The following example walks you through the steps required to add a web service reference to a .NET Core web project and invoke the service.</span></span> <span data-ttu-id="96191-119">*Merhaba Svcutil* adlı bir .NET Core Web uygulaması oluşturacak ve aşağıdaki sözleşmeyi uygulayan bir Web hizmetine başvuru ekleyeceğiz:</span><span class="sxs-lookup"><span data-stu-id="96191-119">You'll create a .NET Core web application named *HelloSvcutil* and add a reference to a web service that implements the following contract:</span></span>

```csharp
[ServiceContract]
public interface ISayHello
{
    [OperationContract]
    string Hello(string name);
}
```

<span data-ttu-id="96191-120">Bu örnek için, Web hizmeti 'nin şu adreste barındırıldığını varsayalım:`http://contoso.com/SayHello.svc`</span><span class="sxs-lookup"><span data-stu-id="96191-120">For this example, let's assume the web service will be hosted at the following address: `http://contoso.com/SayHello.svc`</span></span>

<span data-ttu-id="96191-121">Bir Windows, macOS veya Linux komut penceresinde aşağıdaki adımları uygulayın:</span><span class="sxs-lookup"><span data-stu-id="96191-121">From a Windows, macOS, or Linux command window perform the following steps:</span></span>

1. <span data-ttu-id="96191-122">Projeniz için _Hellosvcutil_ adlı bir dizin oluşturun ve aşağıdaki örnekte olduğu gibi geçerli dizininiz yapın:</span><span class="sxs-lookup"><span data-stu-id="96191-122">Create a directory named _HelloSvcutil_ for your project and make it your current directory, as in the following example:</span></span>

    ```console
    mkdir HelloSvcutil
    cd HelloSvcutil
    ```

2. <span data-ttu-id="96191-123">Aşağıdaki gibi komutu kullanarak bu dizinde yeni bir C# Web projesi oluşturun [`dotnet new`](../tools/dotnet-new.md) :</span><span class="sxs-lookup"><span data-stu-id="96191-123">Create a new C# web project in that directory using the [`dotnet new`](../tools/dotnet-new.md) command as follows:</span></span>

    ```dotnetcli
    dotnet new web
    ```

3. <span data-ttu-id="96191-124">[ `dotnet-svcutil` NuGet PAKETINI](https://nuget.org/packages/dotnet-svcutil) bir CLI aracı olarak yükler: </span><span class="sxs-lookup"><span data-stu-id="96191-124">Install the [`dotnet-svcutil` NuGet package](https://nuget.org/packages/dotnet-svcutil) as a CLI tool:  </span></span><!-- markdownlint-disable MD023 -->
    # <a name="dotnet-svcutil-2x"></a>[<span data-ttu-id="96191-125">DotNet-Svcutil 2. x</span><span class="sxs-lookup"><span data-stu-id="96191-125">dotnet-svcutil 2.x</span></span>](#tab/dotnetsvcutil2x)

    ```dotnetcli
    dotnet tool install --global dotnet-svcutil
    ```

    # <a name="dotnet-svcutil-1x"></a>[<span data-ttu-id="96191-126">DotNet-Svcutil 1. x</span><span class="sxs-lookup"><span data-stu-id="96191-126">dotnet-svcutil 1.x</span></span>](#tab/dotnetsvcutil1x)
    <span data-ttu-id="96191-127">`HelloSvcutil.csproj`Düzenleyicinizde proje dosyasını açın, `Project` öğesini düzenleyin ve aşağıdaki kodu kullanarak [ `dotnet-svcutil` NuGet paketini](https://nuget.org/packages/dotnet-svcutil) bir CLI araç başvurusu olarak ekleyin:</span><span class="sxs-lookup"><span data-stu-id="96191-127">Open the `HelloSvcutil.csproj` project file in your editor, edit the `Project` element, and add the [`dotnet-svcutil` NuGet package](https://nuget.org/packages/dotnet-svcutil) as a CLI tool reference, using the following code:</span></span>

    ```xml
    <ItemGroup>
      <DotNetCliToolReference Include="dotnet-svcutil" Version="1.0.*" />
    </ItemGroup>
    ```

    <span data-ttu-id="96191-128">Ardından aşağıdaki komutu kullanarak _DotNet-Svcutil_ paketini [`dotnet restore`](../tools/dotnet-restore.md) Şu şekilde geri yükleyin:</span><span class="sxs-lookup"><span data-stu-id="96191-128">Then restore the _dotnet-svcutil_ package using the [`dotnet restore`](../tools/dotnet-restore.md) command as follows:</span></span>

    ```dotnetcli
    dotnet restore
    ```

    ---

4. <span data-ttu-id="96191-129">Web hizmeti başvuru dosyasını aşağıdaki gibi oluşturmak için _DotNet-Svcutil_ komutunu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="96191-129">Run the _dotnet-svcutil_ command to generate the web service reference file as follows:</span></span>

    # <a name="dotnet-svcutil-2x"></a>[<span data-ttu-id="96191-130">DotNet-Svcutil 2. x</span><span class="sxs-lookup"><span data-stu-id="96191-130">dotnet-svcutil 2.x</span></span>](#tab/dotnetsvcutil2x)

    ```dotnetcli
    dotnet-svcutil http://contoso.com/SayHello.svc
    ```

    # <a name="dotnet-svcutil-1x"></a>[<span data-ttu-id="96191-131">DotNet-Svcutil 1. x</span><span class="sxs-lookup"><span data-stu-id="96191-131">dotnet-svcutil 1.x</span></span>](#tab/dotnetsvcutil1x)

    ```dotnetcli
    dotnet svcutil http://contoso.com/SayHello.svc
    ```

    ---

<span data-ttu-id="96191-132">Oluşturulan dosya _Merhaba Svcutil/ServiceReference/Reference. cs_olarak kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="96191-132">The generated file is saved as _HelloSvcutil/ServiceReference/Reference.cs_.</span></span> <span data-ttu-id="96191-133">_DotNet-Svcutil_ aracı Ayrıca, proxy kodunun paket başvuruları olarak gerekli olan uygun WCF paketlerini projeye ekler.</span><span class="sxs-lookup"><span data-stu-id="96191-133">The _dotnet-svcutil_ tool also adds to the project the appropriate WCF packages required by the proxy code as package references.</span></span>

## <a name="using-the-service-reference"></a><span data-ttu-id="96191-134">Hizmet başvurusunu kullanma</span><span class="sxs-lookup"><span data-stu-id="96191-134">Using the Service Reference</span></span>

1. <span data-ttu-id="96191-135">Aşağıdaki gibi, komutunu kullanarak WCF paketlerini geri yükleyin [`dotnet restore`](../tools/dotnet-restore.md) :</span><span class="sxs-lookup"><span data-stu-id="96191-135">Restore the WCF packages using the [`dotnet restore`](../tools/dotnet-restore.md) command as follows:</span></span>

    ```dotnetcli
    dotnet restore
    ```

2. <span data-ttu-id="96191-136">Kullanmak istediğiniz istemci sınıfının ve işlemin adını bulun.</span><span class="sxs-lookup"><span data-stu-id="96191-136">Find the name of the client class and operation you want to use.</span></span> <span data-ttu-id="96191-137">`Reference.cs``System.ServiceModel.ClientBase`, hizmet üzerindeki işlemleri çağırmak için kullanılabilecek yöntemler ile öğesinden devralan bir sınıf içerir.</span><span class="sxs-lookup"><span data-stu-id="96191-137">`Reference.cs` will contain a class that inherits from `System.ServiceModel.ClientBase`, with methods that can be used to call operations on the service.</span></span> <span data-ttu-id="96191-138">Bu örnekte, _SayHello_ hizmetinin _Hello_ işlemini çağırmak istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="96191-138">In this example, you want to call the _SayHello_ service's _Hello_ operation.</span></span> <span data-ttu-id="96191-139">`ServiceReference.SayHelloClient`, istemci sınıfının adıdır ve `HelloAsync` işlemi çağırmak için kullanılabilecek bir yöntemi vardır.</span><span class="sxs-lookup"><span data-stu-id="96191-139">`ServiceReference.SayHelloClient` is the name of the client class, and has a method called `HelloAsync` that can be used to call the operation.</span></span>

3. <span data-ttu-id="96191-140">`Startup.cs`Dosyayı Düzenleyicinizde açın ve `using` en üstteki hizmet başvurusu ad alanı için bir yönerge ekleyin:</span><span class="sxs-lookup"><span data-stu-id="96191-140">Open the `Startup.cs` file in your editor, and add a `using` directive for the service reference namespace at the top:</span></span>

    ```csharp
    using ServiceReference;
    ```

4. <span data-ttu-id="96191-141">`Configure`Web hizmetini çağırmak için yöntemini düzenleyin.</span><span class="sxs-lookup"><span data-stu-id="96191-141">Edit the `Configure` method to invoke the web service.</span></span> <span data-ttu-id="96191-142">Bunu, `ClientBase` istemci nesnesindeki yönteminden devralan ve çağıran sınıfının bir örneğini oluşturarak yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="96191-142">You do this by creating an instance of the class that inherits from `ClientBase` and calling the method on the client object:</span></span>

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

5. <span data-ttu-id="96191-143">Komutunu kullanarak uygulamayı [`dotnet run`](../tools/dotnet-run.md) aşağıdaki gibi çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="96191-143">Run the application using the [`dotnet run`](../tools/dotnet-run.md) command as follows:</span></span>

    ```dotnetcli
    dotnet run
    ```

6. <span data-ttu-id="96191-144">Web tarayıcınızda konsolunda listelenen URL 'ye gidin (örneğin, `http://localhost:5000` ).</span><span class="sxs-lookup"><span data-stu-id="96191-144">Navigate to the URL listed in the console (for example, `http://localhost:5000`) in your web browser.</span></span>

<span data-ttu-id="96191-145">Şu çıktıyı görmeniz gerekir: "Hello DotNet-Svcutil!"</span><span class="sxs-lookup"><span data-stu-id="96191-145">You should see the following output: "Hello dotnet-svcutil!"</span></span>

<span data-ttu-id="96191-146">Araç parametrelerinin ayrıntılı bir açıklaması için `dotnet-svcutil` , yardım parametresini aşağıdaki gibi geçirerek aracı çağırın:</span><span class="sxs-lookup"><span data-stu-id="96191-146">For a detailed description of the `dotnet-svcutil` tool parameters, invoke the tool passing the help parameter as follows:</span></span>
# <a name="dotnet-svcutil-2x"></a>[<span data-ttu-id="96191-147">DotNet-Svcutil 2. x</span><span class="sxs-lookup"><span data-stu-id="96191-147">dotnet-svcutil 2.x</span></span>](#tab/dotnetsvcutil2x)

```dotnetcli
dotnet-svcutil --help
```

# <a name="dotnet-svcutil-1x"></a>[<span data-ttu-id="96191-148">DotNet-Svcutil 1. x</span><span class="sxs-lookup"><span data-stu-id="96191-148">dotnet-svcutil 1.x</span></span>](#tab/dotnetsvcutil1x)

```dotnetcli
dotnet svcutil --help
```

---

## <a name="feedback--questions"></a><span data-ttu-id="96191-149">Geri bildirim & soruları</span><span class="sxs-lookup"><span data-stu-id="96191-149">Feedback & questions</span></span>

<span data-ttu-id="96191-150">Sorularınız veya geri bildiriminiz varsa [GitHub ' da bir sorun açın](https://github.com/dotnet/wcf/issues/new).</span><span class="sxs-lookup"><span data-stu-id="96191-150">If you have any questions or feedback, [open an issue on GitHub](https://github.com/dotnet/wcf/issues/new).</span></span> <span data-ttu-id="96191-151">Ayrıca, [GitHub 'DAKI WCF](https://github.com/dotnet/wcf/issues?utf8=%E2%9C%93&q=is:issue%20label:tooling)deposundaki mevcut soruları veya sorunları da inceleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="96191-151">You can also review any existing questions or issues [at the WCF repo on GitHub](https://github.com/dotnet/wcf/issues?utf8=%E2%9C%93&q=is:issue%20label:tooling).</span></span>

## <a name="release-notes"></a><span data-ttu-id="96191-152">Sürüm notları</span><span class="sxs-lookup"><span data-stu-id="96191-152">Release notes</span></span>

- <span data-ttu-id="96191-153">Bilinen sorunlar da dahil olmak üzere, güncelleştirilmiş sürüm bilgileri için [sürüm notlarına](https://github.com/dotnet/wcf/blob/master/release-notes/dotnet-svcutil-notes.md) bakın.</span><span class="sxs-lookup"><span data-stu-id="96191-153">Refer to the [Release notes](https://github.com/dotnet/wcf/blob/master/release-notes/dotnet-svcutil-notes.md) for updated release information, including known issues.</span></span>

## <a name="information"></a><span data-ttu-id="96191-154">Bilgi</span><span class="sxs-lookup"><span data-stu-id="96191-154">Information</span></span>

- [<span data-ttu-id="96191-155">DotNet-Svcutil NuGet paketi</span><span class="sxs-lookup"><span data-stu-id="96191-155">dotnet-svcutil NuGet Package</span></span>](https://nuget.org/packages/dotnet-svcutil)
