---
title: dotnet-svcutil.xmlserializer kullanma
description: .NET Core projeleri `dotnet-svcutil.xmlserializer` için bir serileştirme derlemesi oluşturmak için NuGet paketini nasıl kullanabileceğinizi öğrenin.
author: huanwu
ms.date: 11/27/2018
ms.openlocfilehash: 4811647c294118cb160d25805e7d3ada97f071f9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75344894"
---
# <a name="using-dotnet-svcutilxmlserializer-on-net-core"></a><span data-ttu-id="28b75-103">Dotnet-svcutil.xmlserializer üzerinde .NET Core kullanma</span><span class="sxs-lookup"><span data-stu-id="28b75-103">Using dotnet-svcutil.xmlserializer on .NET Core</span></span>

<span data-ttu-id="28b75-104">`dotnet-svcutil.xmlserializer` NuGet paketi .NET Core projeleri için bir serileştirme derlemesi oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="28b75-104">The `dotnet-svcutil.xmlserializer` NuGet package can pre-generate a serialization assembly for .NET Core projects.</span></span> <span data-ttu-id="28b75-105">WCF Hizmet Sözleşmesi tarafından kullanılan ve XmlSerializer tarafından serihale getirilebilen istemci uygulamasındaki türler için C# serileştirme kodunu önceden oluşturur.</span><span class="sxs-lookup"><span data-stu-id="28b75-105">It pre-generates C# serialization code for the types in the client application that are used by the WCF Service Contract and that can be serialized by the XmlSerializer.</span></span> <span data-ttu-id="28b75-106">Bu, bu tür nesneleri serihale veya deserializing xml serileştirme başlangıç performansını artırır.</span><span class="sxs-lookup"><span data-stu-id="28b75-106">This improves the startup performance of XML serialization when serializing or deserializing objects of those types.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="28b75-107">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="28b75-107">Prerequisites</span></span>

* <span data-ttu-id="28b75-108">[.NET Core 2.1 SDK](https://dotnet.microsoft.com/download) veya sonrası</span><span class="sxs-lookup"><span data-stu-id="28b75-108">[.NET Core 2.1 SDK](https://dotnet.microsoft.com/download) or later</span></span>
* <span data-ttu-id="28b75-109">En sevdiğiniz kod düzenleyicisi</span><span class="sxs-lookup"><span data-stu-id="28b75-109">Your favorite code editor</span></span>

<span data-ttu-id="28b75-110">.NET Core `dotnet --info` SDK'nın hangi sürümlerini ve çalışma süresini zaten yüklediğinizi denetlemek için komutu kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="28b75-110">You can use the command `dotnet --info` to check which versions of .NET Core SDK and runtime you already have installed.</span></span>

## <a name="getting-started"></a><span data-ttu-id="28b75-111">Başlarken</span><span class="sxs-lookup"><span data-stu-id="28b75-111">Getting started</span></span>

<span data-ttu-id="28b75-112">.NET `dotnet-svcutil.xmlserializer` Core konsol uygulamasında kullanmak için:</span><span class="sxs-lookup"><span data-stu-id="28b75-112">To use `dotnet-svcutil.xmlserializer` in a .NET Core console application:</span></span>

1. <span data-ttu-id="28b75-113">.NET Framework'deki varsayılan 'WCF Hizmet Uygulaması' şablonundan'ı kullanarak 'MyWCFService' adlı bir WCF Hizmeti oluşturun.</span><span class="sxs-lookup"><span data-stu-id="28b75-113">Create a WCF Service named 'MyWCFService' using the default template 'WCF Service Application' in .NET Framework.</span></span> <span data-ttu-id="28b75-114">Hizmet `[XmlSerializerFormat]` yöntemine aşağıdaki gibi öznitelik ekleyin:</span><span class="sxs-lookup"><span data-stu-id="28b75-114">Add `[XmlSerializerFormat]` attribute on the service method like the following:</span></span>

   ```csharp
    [ServiceContract]
    public interface IService1
    {
        [XmlSerializerFormat]
        [OperationContract(Action = "http://tempuri.org/IService1/GetData", ReplyAction = "http://tempuri.org/IService1/GetDataResponse")]
        string GetData(int value);
    }
    ```

2. <span data-ttu-id="28b75-115">.NET Core 2.1 veya daha sonraki sürümleri hedefleyen WCF istemci uygulaması olarak bir .NET Core konsol uygulaması oluşturun.</span><span class="sxs-lookup"><span data-stu-id="28b75-115">Create a .NET Core console application as WCF client application that targets at .NET Core 2.1 or later versions.</span></span> <span data-ttu-id="28b75-116">Örneğin, aşağıdaki komutla 'MyWCFClient' adında bir uygulama oluşturun:</span><span class="sxs-lookup"><span data-stu-id="28b75-116">For example, create an app named 'MyWCFClient' with the following command:</span></span>

    ```dotnetcli
    dotnet new console --name MyWCFClient
    ```

    <span data-ttu-id="28b75-117">Projenizin .NET Core 2.1 veya sonraki leri `TargetFramework` hedeflediğinden emin olmak için proje dosyanızdaki XML öğesini inceleyin:</span><span class="sxs-lookup"><span data-stu-id="28b75-117">To ensure your project is targeting .NET Core 2.1 or later, inspect the `TargetFramework` XML element in your project file:</span></span>

    ```xml
    <TargetFramework>netcoreapp2.1</TargetFramework>
    ```

3. <span data-ttu-id="28b75-118">Aşağıdaki komutu `System.ServiceModel.Http` çalıştırarak bir paket başvurusu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="28b75-118">Add a package reference to `System.ServiceModel.Http` by running the following command:</span></span>

    ```dotnetcli
    dotnet add package System.ServiceModel.Http
    ```

4. <span data-ttu-id="28b75-119">WCF İstemci kodunu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="28b75-119">Add the WCF Client code:</span></span>

    ```csharp
    using System.ServiceModel;

        class Program
        {
            static void Main(string[] args)
            {
                var myBinding = new BasicHttpBinding();
                var myEndpoint = new EndpointAddress("http://localhost:2561/Service1.svc"); //Fill your service url here
                var myChannelFactory = new ChannelFactory<IService1>(myBinding, myEndpoint);
                IService1 client = myChannelFactory.CreateChannel();
                string s = client.GetData(1);
                ((ICommunicationObject)client).Close();
            }
        }

    [ServiceContract]
    public interface IService1
    {
        [XmlSerializerFormat]
        [OperationContract(Action = "http://tempuri.org/IService1/GetData", ReplyAction = "http://tempuri.org/IService1/GetDataResponse")]
        string GetData(int value);
    }
    ```

5. <span data-ttu-id="28b75-120">Aşağıdaki komutu `dotnet-svcutil.xmlserializer` çalıştırarak pakete bir başvuru ekleyin:</span><span class="sxs-lookup"><span data-stu-id="28b75-120">Add a reference to the `dotnet-svcutil.xmlserializer` package by running the following command:</span></span>
  
    ```dotnetcli
    dotnet add package dotnet-svcutil.xmlserializer
    ```

    <span data-ttu-id="28b75-121">Komutu çalıştırmak, proje dosyanıza buna benzer bir giriş eklemelidir:</span><span class="sxs-lookup"><span data-stu-id="28b75-121">Running the command should add an entry to your project file similar to this:</span></span>
  
    ```xml
    <ItemGroup>
      <DotNetCliToolReference Include="dotnet-svcutil.xmlserializer" Version="1.0.0" />
    </ItemGroup>
    ```

6. <span data-ttu-id="28b75-122">Çalıştırarak `dotnet build`uygulamayı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="28b75-122">Build the application by running `dotnet build`.</span></span> <span data-ttu-id="28b75-123">Her şey başarılı olursa, çıktı klasöründe *MyWCFClient.XmlSerializers.dll* adlı bir derleme oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="28b75-123">If everything succeeds, an assembly named *MyWCFClient.XmlSerializers.dll* is generated in the output folder.</span></span> <span data-ttu-id="28b75-124">Araç derlemeyi oluşturamazsa, yapı çıktısında uyarılar görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="28b75-124">If the tool failed to generate the assembly, you'll see warnings in the build output.</span></span>

7. <span data-ttu-id="28b75-125">WCF hizmetini, örneğin tarayıcıda `http://localhost:2561/Service1.svc` çalıştırarak başlatın.</span><span class="sxs-lookup"><span data-stu-id="28b75-125">Start the WCF service by, for example, running `http://localhost:2561/Service1.svc` in the browser.</span></span> <span data-ttu-id="28b75-126">Ardından istemci uygulamasını başlatın ve otomatik olarak yüklenir ve çalışma zamanında önceden oluşturulmuş serializers kullanır.</span><span class="sxs-lookup"><span data-stu-id="28b75-126">Then start the client application, and it will automatically load and use the pre-generated serializers at runtime.</span></span>
