---
title: DotNet svcutil.xmlserializer üzerinde .NET Core kullanma
description: Nasıl kullanabileceğinizi öğrenin `dotnet-svcutil.xmlserializer` önceden .NET Core projeleri için bir serileştirme derlemesi oluşturmak için NuGet paketi.
author: huanwu
ms.date: 11/27/2018
ms.openlocfilehash: f5ffed47079a3ee122c7784d0c61c4d40461ba26
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61638989"
---
# <a name="using-dotnet-svcutilxmlserializer-on-net-core"></a><span data-ttu-id="510d3-103">DotNet svcutil.xmlserializer üzerinde .NET Core kullanma</span><span class="sxs-lookup"><span data-stu-id="510d3-103">Using dotnet-svcutil.xmlserializer on .NET Core</span></span>

<span data-ttu-id="510d3-104">`dotnet-svcutil.xmlserializer` NuGet paketi önceden .NET Core projeleri için bir seri hale getirme derlemesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="510d3-104">The `dotnet-svcutil.xmlserializer` NuGet package can pre-generate a serialization assembly for .NET Core projects.</span></span> <span data-ttu-id="510d3-105">Önceden oluşturur C# WCF sözleşmesi tarafından kullanılır ve bu seri hale getirilemiyor XmlSerializer tarafından türleri istemci uygulamasındaki için serileştirme kodu.</span><span class="sxs-lookup"><span data-stu-id="510d3-105">It pre-generates C# serialization code for the types in the client application that are used by the WCF Service Contract and that can be serialized by the XmlSerializer.</span></span> <span data-ttu-id="510d3-106">Bu seri hale getirme veya bu türden nesneler seri durumdan çıkarılırken zaman XML serileştirme başlangıç performansını artırır.</span><span class="sxs-lookup"><span data-stu-id="510d3-106">This improves the startup performance of XML serialization when serializing or deserializing objects of those types.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="510d3-107">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="510d3-107">Prerequisites</span></span>

* <span data-ttu-id="510d3-108">[.NET core 2.1 SDK](https://www.microsoft.com/net/download) veya üzeri</span><span class="sxs-lookup"><span data-stu-id="510d3-108">[.NET Core 2.1 SDK](https://www.microsoft.com/net/download) or later</span></span>
* <span data-ttu-id="510d3-109">Sık kullandığınız kod düzenleyici</span><span class="sxs-lookup"><span data-stu-id="510d3-109">Your favorite code editor</span></span>

<span data-ttu-id="510d3-110">Komutunu kullanabilirsiniz `dotnet --info` .NET Core SDK ve çalışma zamanının hangi sürümlerinin zaten yüklemiş olduğunuz denetlemek için.</span><span class="sxs-lookup"><span data-stu-id="510d3-110">You can use the command `dotnet --info` to check which versions of .NET Core SDK and runtime you already have installed.</span></span>

## <a name="getting-started"></a><span data-ttu-id="510d3-111">Başlarken</span><span class="sxs-lookup"><span data-stu-id="510d3-111">Getting started</span></span>

<span data-ttu-id="510d3-112">Kullanılacak `dotnet-svcutil.xmlserializer` ' de .NET Core konsol uygulaması:</span><span class="sxs-lookup"><span data-stu-id="510d3-112">To use `dotnet-svcutil.xmlserializer` in a .NET Core console application:</span></span>

1. <span data-ttu-id="510d3-113">.NET Framework'teki varsayılan şablon 'WCF hizmet uygulaması' kullanılarak'MyWCFService ' adlı bir WCF hizmeti oluşturma.</span><span class="sxs-lookup"><span data-stu-id="510d3-113">Create a WCF Service named 'MyWCFService' using the default template 'WCF Service Application' in .NET Framework.</span></span> <span data-ttu-id="510d3-114">Ekleme `[XmlSerializerFormat]` özniteliği aşağıdaki gibi hizmet yöntemi:</span><span class="sxs-lookup"><span data-stu-id="510d3-114">Add `[XmlSerializerFormat]` attribute on the service method like the following:</span></span>

   ```csharp
    [ServiceContract]
    public interface IService1
    {
        [XmlSerializerFormat]
        [OperationContract(Action = "http://tempuri.org/IService1/GetData", ReplyAction = "http://tempuri.org/IService1/GetDataResponse")]
        string GetData(int value);
    }
    ```

2. <span data-ttu-id="510d3-115">Bir .NET Core konsol uygulaması WCF istemci uygulaması olarak, .NET Core 2.1 veya üzeri sürümleri hedefleyen oluşturun.</span><span class="sxs-lookup"><span data-stu-id="510d3-115">Create a .NET Core console application as WCF client application that targets at .NET Core 2.1 or later versions.</span></span> <span data-ttu-id="510d3-116">Örneğin, aşağıdaki komutla 'MyWCFClient' adlı bir uygulama oluşturun:</span><span class="sxs-lookup"><span data-stu-id="510d3-116">For example, create an app named 'MyWCFClient' with the following command:</span></span>

    ```console
    dotnet new console --name MyWCFClient
    ```

    <span data-ttu-id="510d3-117">Projeniz tarafından hedeflenen .NET Core 2.1 sağlayın ya da daha sonra incelemek üzere `TargetFramework` proje dosyanızda XML öğesi:</span><span class="sxs-lookup"><span data-stu-id="510d3-117">To ensure your project is targeting .NET Core 2.1 or later, inspect the `TargetFramework` XML element in your project file:</span></span>

    ```xml
    <TargetFramework>netcoreapp2.1</TargetFramework>
    ```

3. <span data-ttu-id="510d3-118">Paket başvurusu ekleme `System.ServiceModel.Http` aşağıdaki komutu çalıştırarak:</span><span class="sxs-lookup"><span data-stu-id="510d3-118">Add a package reference to `System.ServiceModel.Http` by running the following command:</span></span>

    ```console
    dotnet add package System.ServiceModel.Http
    ```

4. <span data-ttu-id="510d3-119">WCF istemci kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="510d3-119">Add the WCF Client code:</span></span>

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

5. <span data-ttu-id="510d3-120">Bir başvuru ekleyin `dotnet-svcutil.xmlserializer` aşağıdaki komutu çalıştırarak paketi:</span><span class="sxs-lookup"><span data-stu-id="510d3-120">Add a reference to the `dotnet-svcutil.xmlserializer` package by running the following command:</span></span>
  
    ```console
    dotnet add package dotnet-svcutil.xmlserializer
    ```

    <span data-ttu-id="510d3-121">Komutu çalıştırmadan proje dosyanız aşağıdakine benzer bir giriş ekleyin:</span><span class="sxs-lookup"><span data-stu-id="510d3-121">Running the command should add an entry to your project file similar to this:</span></span>
  
    ```xml
    <ItemGroup>
      <DotNetCliToolReference Include="dotnet-svcutil.xmlserializer" Version="1.0.0" />
    </ItemGroup>
    ```

6. <span data-ttu-id="510d3-122">Uygulamayı çalıştırarak oluşturmak `dotnet build`.</span><span class="sxs-lookup"><span data-stu-id="510d3-122">Build the application by running `dotnet build`.</span></span> <span data-ttu-id="510d3-123">Her şeyi başarılı olursa, adında bir derleme *MyWCFClient.XmlSerializers.dll* çıktı klasöründe oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="510d3-123">If everything succeeds, an assembly named *MyWCFClient.XmlSerializers.dll* is generated in the output folder.</span></span> <span data-ttu-id="510d3-124">Araç derlemesi oluşturulamadı. derleme çıkışını uyarılar görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="510d3-124">If the tool failed to generate the assembly, you'll see warnings in the build output.</span></span>

7. <span data-ttu-id="510d3-125">WCF hizmet tarafından Örneğin, çalıştırmaya başlayın `http://localhost:2561/Service1.svc` tarayıcıda.</span><span class="sxs-lookup"><span data-stu-id="510d3-125">Start the WCF service by, for example, running `http://localhost:2561/Service1.svc` in the browser.</span></span> <span data-ttu-id="510d3-126">Ardından istemci uygulamasını başlatın ve bunu otomatik olarak yüklemek ve çalışma zamanında önceden oluşturulmuş seri hale getiricileri genişletme kullanın.</span><span class="sxs-lookup"><span data-stu-id="510d3-126">Then start the client application, and it will automatically load and use the pre-generated serializers at runtime.</span></span>