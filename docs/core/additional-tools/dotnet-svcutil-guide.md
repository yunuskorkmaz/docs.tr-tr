---
title: Microsoft WCF dotnet svcutil aracı
description: .NET Core ve ASP.NET Core projeleri için .NET Framework projeleri için WCF svcutil aracına benzer işlevsellik ekleyen Microsoft WCF svcutil dotnet araç genel bakış.
author: mlacouture
ms.author: jralexander
ms.date: 08/20/2018
ms.openlocfilehash: bb4d8e5f3997318b720535b0f1e07fc33d13338a
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43511892"
---
# <a name="microsoft-wcf-dotnet-svcutil-tool"></a><span data-ttu-id="73331-103">Microsoft WCF dotnet svcutil aracı</span><span class="sxs-lookup"><span data-stu-id="73331-103">Microsoft WCF dotnet-svcutil tool</span></span>

<span data-ttu-id="73331-104">Windows Communication Foundation (WCF) **dotnet svcutil** araçtır bir ağ konumu üzerinde bir web hizmetinden veya bir WSDL dosyasından meta verilerini alır ve istemci proxy yöntemleri içeren bir WCF sınıfı oluşturur bir .NET Core CLI aracı, web hizmet işlemleri erişim.</span><span class="sxs-lookup"><span data-stu-id="73331-104">The Windows Communication Foundation (WCF) **dotnet-svcutil** tool is a .NET Core CLI tool that retrieves metadata from a web service on a network location or from a WSDL file, and generates a WCF class containing client proxy methods that access the web service operations.</span></span>

<span data-ttu-id="73331-105">Benzer şekilde [ **Service Model meta verilerini - svcutil** ](../../framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) .NET Framework projeleri için araç **dotnet svcutil** bir web hizmeti başvurusu oluşturmak için bir komut satırı aracı .NET Core ve .NET Standard projelerine uyumludur.</span><span class="sxs-lookup"><span data-stu-id="73331-105">Similar to the [**Service Model Metadata - svcutil**](../../framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) tool for .NET Framework projects, the **dotnet-svcutil** is a command-line tool for generating a web service reference compatible with .NET Core and .NET Standard projects.</span></span>

<span data-ttu-id="73331-106">**Dotnet svcutil** araçtır için alternatif bir seçenek [ **WCF Web Service Reference** ](wcf-web-service-reference-guide.md) Visual Studio, Visual Studio ile ilk sevk edilen hizmet sağlayıcısı bağlı 2017 v15.5.</span><span class="sxs-lookup"><span data-stu-id="73331-106">The **dotnet-svcutil** tool is an alternative option to the [**WCF Web Service Reference**](wcf-web-service-reference-guide.md) Visual Studio connected service provider that first shipped with Visual Studio 2017 v15.5.</span></span> <span data-ttu-id="73331-107">**Dotnet svcutil** aracı bir .NET Core CLI aracı, Linux, macOS ve Windows üzerinde kullanılabilir çapraz platform.</span><span class="sxs-lookup"><span data-stu-id="73331-107">The **dotnet-svcutil** tool as a .NET Core CLI tool, is available cross-platform on Linux, macOS, and Windows.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="73331-108">Yalnızca güvenilir bir kaynaktan Hizmetleri başvuruda bulunmalıdır.</span><span class="sxs-lookup"><span data-stu-id="73331-108">You should only reference services from a trusted source.</span></span> <span data-ttu-id="73331-109">Güvenilmeyen bir kaynaktan başvurularının eklenmesi, güvenliği tehlikeye atabilir.</span><span class="sxs-lookup"><span data-stu-id="73331-109">Adding references from an untrusted source may compromise security.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="73331-110">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="73331-110">Prerequisites</span></span>

* <span data-ttu-id="73331-111">[.NET core SDK'sı](https://www.microsoft.com/net/download) v1.0.4 veya sonraki sürümler</span><span class="sxs-lookup"><span data-stu-id="73331-111">[.NET Core SDK](https://www.microsoft.com/net/download) v1.0.4 or later versions</span></span>
* <span data-ttu-id="73331-112">Sık kullandığınız kod düzenleyici</span><span class="sxs-lookup"><span data-stu-id="73331-112">Your favorite code editor</span></span>

## <a name="getting-started"></a><span data-ttu-id="73331-113">Başlarken</span><span class="sxs-lookup"><span data-stu-id="73331-113">Getting started</span></span>

<span data-ttu-id="73331-114">Aşağıdaki örnek bir .NET Core konsol projesi için bir web hizmeti başvurusu eklemek ve hizmeti çağırmak için gereken adımlarda size yol gösterir.</span><span class="sxs-lookup"><span data-stu-id="73331-114">The following example walks you through the steps required to add a web service reference to a .NET Core console project and invoke the service.</span></span> <span data-ttu-id="73331-115">Adlı bir .NET Core konsol uygulaması oluşturacaksınız _HelloSvcutil_ ve aşağıdaki sözleşme uygulayan bir web hizmeti için bir başvuru ekler:</span><span class="sxs-lookup"><span data-stu-id="73331-115">You will create a .NET Core console application named _HelloSvcutil_ and will add a reference to a web service that implements the following contract:</span></span>

```csharp
[ServiceContract]
public interface ISayHello
{
    [OperationContract]
    string Hello(string name);
}
```

<span data-ttu-id="73331-116">Bu örnekte, web hizmeti, şu adresten barındırılması varsayılacak: `http://contoso.com/SayHello.svc`</span><span class="sxs-lookup"><span data-stu-id="73331-116">For this example, the web service will be assumed to be hosted at the following address: `http://contoso.com/SayHello.svc`</span></span>

<span data-ttu-id="73331-117">Bir Windows, macOS veya Linux komut penceresinde aşağıdaki adımları gerçekleştirin:</span><span class="sxs-lookup"><span data-stu-id="73331-117">From a Windows, macOS, or Linux command window perform the following steps:</span></span>

1. <span data-ttu-id="73331-118">Adlı bir dizin oluşturmak _HelloSvcutil_ projeniz için ve aşağıdaki örnekte olduğu gibi geçerli dizin yapın:</span><span class="sxs-lookup"><span data-stu-id="73331-118">Create a directory named _HelloSvcutil_ for your project and make it your current directory, as in the following example:</span></span>

```console
mkdir HelloSvcutil
cd HelloSvcutil
```

2. <span data-ttu-id="73331-119">Bu dizin kullanarak azure'da yeni bir C# konsol projesi oluşturma [ `dotnet new` ](../tools/dotnet-new.md) komutuyla şu şekilde:</span><span class="sxs-lookup"><span data-stu-id="73331-119">Create a new C# console project in that directory using the [`dotnet new`](../tools/dotnet-new.md) command as follows:</span></span>

```console
dotnet new console
```

3. <span data-ttu-id="73331-120">Açık `HelloSvcutil.csproj` proje dosyası düzenleyicinizde, düzenleme `Project` öğesi ve ekleme [ `dotnet-svcutil` NuGet paketini](https://nuget.org/packages/dotnet-svcutil) CLI aracı başvuru olarak, aşağıdaki kodu kullanarak:</span><span class="sxs-lookup"><span data-stu-id="73331-120">Open the `HelloSvcutil.csproj` project file in your editor, edit the `Project` element, and add the [`dotnet-svcutil` NuGet package](https://nuget.org/packages/dotnet-svcutil) as a CLI tool reference, using the following code:</span></span>

```xml
<ItemGroup>
  <DotNetCliToolReference Include="dotnet-svcutil" Version="1.0.*" />
</ItemGroup>
```

4. <span data-ttu-id="73331-121">Geri yükleme _dotnet svcutil_ kullanarak paket [ `dotnet restore` ](../tools/dotnet-restore.md) komutuyla şu şekilde:</span><span class="sxs-lookup"><span data-stu-id="73331-121">Restore the _dotnet-svcutil_ package using the [`dotnet restore`](../tools/dotnet-restore.md) command as follows:</span></span>

```console
dotnet restore
```

5. <span data-ttu-id="73331-122">Çalıştırma _dotnet_ ile _svcutil_ gibi web hizmeti başvurusu dosyası oluşturmak için komutu:</span><span class="sxs-lookup"><span data-stu-id="73331-122">Run _dotnet_ with the _svcutil_ command to generate the web service reference file as follows:</span></span>

```console
dotnet svcutil http://contoso.com/SayHello.svc
```
<span data-ttu-id="73331-123">Oluşturulan dosyası olarak kaydedilen _HelloSvcutil/ServiceReference1/Reference.cs_.</span><span class="sxs-lookup"><span data-stu-id="73331-123">The generated file is saved as _HelloSvcutil/ServiceReference1/Reference.cs_.</span></span> <span data-ttu-id="73331-124">_Dotnet_svcutil_ aracı gerekli proxy kodu tarafından uygun WCF paketleri paket başvuruları projeye de ekler.</span><span class="sxs-lookup"><span data-stu-id="73331-124">The _dotnet_svcutil_ tool also adds to the project the appropriate WCF packages required by the proxy code as package references.</span></span>

6. <span data-ttu-id="73331-125">Kullanarak WCF paketleri geri [ `dotnet restore` ](../tools/dotnet-restore.md) komutuyla şu şekilde:</span><span class="sxs-lookup"><span data-stu-id="73331-125">Restore the WCF packages using the [`dotnet restore`](../tools/dotnet-restore.md) command as follows:</span></span>

```console
dotnet restore
```

7. <span data-ttu-id="73331-126">Açık `Program.cs` dosya Düzenleyicisi'nde, Düzen `Main()` yöntemi ve web hizmetini çağırmak için aşağıdaki kodla değiştirin otomatik olarak oluşturulan kodu:</span><span class="sxs-lookup"><span data-stu-id="73331-126">Open the `Program.cs` file in your editor, edit the `Main()` method, and replace the auto-generated code with the following code to invoke the web service:</span></span>

```csharp
static void Main(string[] args)
{
    var client = new SayHelloClient();
    Console.WriteLine(client.HelloAsync("dotnet-svcutil").Result);
}
```

8. <span data-ttu-id="73331-127">Kullanarak uygulama çalıştırma [ `dotnet run` ](../tools/dotnet-run.md) komutuyla şu şekilde:</span><span class="sxs-lookup"><span data-stu-id="73331-127">Run the application using the [`dotnet run`](../tools/dotnet-run.md) command as follows:</span></span>

```console
dotnet run
```
<span data-ttu-id="73331-128">Aşağıdaki çıktıyı görmeniz gerekir: "Dotnet svcutil Merhaba!"</span><span class="sxs-lookup"><span data-stu-id="73331-128">You should see the following output: "Hello dotnet-svcutil!"</span></span>

<span data-ttu-id="73331-129">Ayrıntılı bir açıklaması için `dotnet-svcutil` aracı parametreleri, help parametresini aşağıdaki şekilde geçirme aracı Çağır:</span><span class="sxs-lookup"><span data-stu-id="73331-129">For a detailed description of the `dotnet-svcutil` tool parameters, invoke the tool passing the help parameter as follows:</span></span>

```console
dotnet svcutil --help
```

## <a name="next-steps"></a><span data-ttu-id="73331-130">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="73331-130">Next steps</span></span>

### <a name="feedback--questions"></a><span data-ttu-id="73331-131">Geri bildirim ve sorular</span><span class="sxs-lookup"><span data-stu-id="73331-131">Feedback & questions</span></span>

<span data-ttu-id="73331-132">Sorularınız veya geri bildirim, varsa [github'da bir sorun açın](https://github.com/dotnet/wcf/issues/new).</span><span class="sxs-lookup"><span data-stu-id="73331-132">If you have any questions or feedback, [open an issue on GitHub](https://github.com/dotnet/wcf/issues/new).</span></span> <span data-ttu-id="73331-133">Mevcut bir soru veya sorunlarla gözden geçirebilirsiniz [WCF deponun GitHub üzerinde en](https://github.com/dotnet/wcf/issues?utf8=%E2%9C%93&q=is:issue%20label:tooling).</span><span class="sxs-lookup"><span data-stu-id="73331-133">You can also review any existing questions or issues [at the WCF repo on GitHub](https://github.com/dotnet/wcf/issues?utf8=%E2%9C%93&q=is:issue%20label:tooling).</span></span>

### <a name="release-notes"></a><span data-ttu-id="73331-134">Sürüm notları</span><span class="sxs-lookup"><span data-stu-id="73331-134">Release notes</span></span>

* <span data-ttu-id="73331-135">Başvurmak [sürüm notları](https://github.com/dotnet/wcf/blob/master/release-notes/dotnet-svcutil-notes.md) güncelleştirilmiş sürüm bilgileri için bilinen sorunlar da dahil olmak üzere.</span><span class="sxs-lookup"><span data-stu-id="73331-135">Refer to the [Release notes](https://github.com/dotnet/wcf/blob/master/release-notes/dotnet-svcutil-notes.md) for updated release information, including known issues.</span></span>

### <a name="information"></a><span data-ttu-id="73331-136">Bilgiler</span><span class="sxs-lookup"><span data-stu-id="73331-136">Information</span></span>

* [<span data-ttu-id="73331-137">DotNet svcutil NuGet paketi</span><span class="sxs-lookup"><span data-stu-id="73331-137">dotnet-svcutil NuGet Package</span></span>](https://nuget.org/packages/dotnet-svcutil)
