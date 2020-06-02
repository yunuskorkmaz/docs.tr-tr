---
title: DotNet-Svcutil. XmlSerializer kullanma
description: '`dotnet-svcutil.xmlserializer`.NET Core projeleri için bir serileştirme derlemesini önceden oluşturmak üzere NuGet paketini nasıl kullanabileceğinizi öğrenin.'
author: huanwu
ms.date: 11/27/2018
ms.openlocfilehash: 14bb2e8a85ec35f08b0a83b9734a64d751074f1b
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84284331"
---
# <a name="using-dotnet-svcutilxmlserializer-on-net-core"></a><span data-ttu-id="b0495-103">.NET Core 'da DotNet-Svcutil. XmlSerializer kullanma</span><span class="sxs-lookup"><span data-stu-id="b0495-103">Using dotnet-svcutil.xmlserializer on .NET Core</span></span>

<span data-ttu-id="b0495-104">`dotnet-svcutil.xmlserializer`NuGet paketi .NET Core projeleri için bir serileştirme derlemesini önceden oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="b0495-104">The `dotnet-svcutil.xmlserializer` NuGet package can pre-generate a serialization assembly for .NET Core projects.</span></span> <span data-ttu-id="b0495-105">WCF hizmet sözleşmesi tarafından kullanılan ve XmlSerializer tarafından seri hale getirileceden istemci uygulamasındaki türler için C# serileştirme kodu önceden oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="b0495-105">It pre-generates C# serialization code for the types in the client application that are used by the WCF Service Contract and that can be serialized by the XmlSerializer.</span></span> <span data-ttu-id="b0495-106">Bu, bu türlerin nesneleri serileştirilirken veya seri durumdan çıkarılırken XML serileştirmesinin başlangıç performansını geliştirir.</span><span class="sxs-lookup"><span data-stu-id="b0495-106">This improves the startup performance of XML serialization when serializing or deserializing objects of those types.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="b0495-107">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="b0495-107">Prerequisites</span></span>

* <span data-ttu-id="b0495-108">[.NET Core 2,1 SDK](https://dotnet.microsoft.com/download) veya üzeri</span><span class="sxs-lookup"><span data-stu-id="b0495-108">[.NET Core 2.1 SDK](https://dotnet.microsoft.com/download) or later</span></span>
* <span data-ttu-id="b0495-109">En sevdiğiniz kod düzenleyiciniz</span><span class="sxs-lookup"><span data-stu-id="b0495-109">Your favorite code editor</span></span>

<span data-ttu-id="b0495-110">`dotnet --info`.NET Core SDK ve çalışma zamanının hangi sürümlerinin yüklü olduğunu denetlemek için komutunu kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b0495-110">You can use the command `dotnet --info` to check which versions of .NET Core SDK and runtime you already have installed.</span></span>

## <a name="getting-started"></a><span data-ttu-id="b0495-111">Kullanmaya başlama</span><span class="sxs-lookup"><span data-stu-id="b0495-111">Getting started</span></span>

<span data-ttu-id="b0495-112">`dotnet-svcutil.xmlserializer`Bir .NET Core konsol uygulamasında kullanmak için:</span><span class="sxs-lookup"><span data-stu-id="b0495-112">To use `dotnet-svcutil.xmlserializer` in a .NET Core console application:</span></span>

1. <span data-ttu-id="b0495-113">.NET Framework ' de varsayılan ' WCF hizmet uygulaması ' şablonunu kullanarak ' MyWCFService ' adlı bir WCF hizmeti oluşturun.</span><span class="sxs-lookup"><span data-stu-id="b0495-113">Create a WCF Service named 'MyWCFService' using the default template 'WCF Service Application' in .NET Framework.</span></span> <span data-ttu-id="b0495-114">`[XmlSerializerFormat]`Aşağıdaki gibi hizmet yöntemine öznitelik ekleyin:</span><span class="sxs-lookup"><span data-stu-id="b0495-114">Add `[XmlSerializerFormat]` attribute on the service method like the following:</span></span>

   ```csharp
    [ServiceContract]
    public interface IService1
    {
        [XmlSerializerFormat]
        [OperationContract(Action = "http://tempuri.org/IService1/GetData", ReplyAction = "http://tempuri.org/IService1/GetDataResponse")]
        string GetData(int value);
    }
    ```

2. <span data-ttu-id="b0495-115">.NET Core 2,1 veya sonraki sürümlerini hedefleyen WCF istemci uygulaması olarak bir .NET Core konsol uygulaması oluşturun.</span><span class="sxs-lookup"><span data-stu-id="b0495-115">Create a .NET Core console application as WCF client application that targets at .NET Core 2.1 or later versions.</span></span> <span data-ttu-id="b0495-116">Örneğin, aşağıdaki komutla ' MyWCFClient ' adlı bir uygulama oluşturun:</span><span class="sxs-lookup"><span data-stu-id="b0495-116">For example, create an app named 'MyWCFClient' with the following command:</span></span>

    ```dotnetcli
    dotnet new console --name MyWCFClient
    ```

    <span data-ttu-id="b0495-117">Projenizin .NET Core 2,1 veya sonraki bir sürümü hedeflediğinden emin olmak için, `TargetFramework` proje dosyanızdaki XML öğesini inceleyin:</span><span class="sxs-lookup"><span data-stu-id="b0495-117">To ensure your project is targeting .NET Core 2.1 or later, inspect the `TargetFramework` XML element in your project file:</span></span>

    ```xml
    <TargetFramework>netcoreapp2.1</TargetFramework>
    ```

3. <span data-ttu-id="b0495-118">Aşağıdaki komutu çalıştırarak öğesine bir paket başvurusu ekleyin `System.ServiceModel.Http` :</span><span class="sxs-lookup"><span data-stu-id="b0495-118">Add a package reference to `System.ServiceModel.Http` by running the following command:</span></span>

    ```dotnetcli
    dotnet add package System.ServiceModel.Http
    ```

4. <span data-ttu-id="b0495-119">WCF Istemci kodunu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="b0495-119">Add the WCF Client code:</span></span>

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

5. <span data-ttu-id="b0495-120">`dotnet-svcutil.xmlserializer`Aşağıdaki komutu çalıştırarak pakete bir başvuru ekleyin:</span><span class="sxs-lookup"><span data-stu-id="b0495-120">Add a reference to the `dotnet-svcutil.xmlserializer` package by running the following command:</span></span>
  
    ```dotnetcli
    dotnet add package dotnet-svcutil.xmlserializer
    ```

    <span data-ttu-id="b0495-121">Komutun çalıştırılması, proje dosyanıza şuna benzer bir girdi eklemeli:</span><span class="sxs-lookup"><span data-stu-id="b0495-121">Running the command should add an entry to your project file similar to this:</span></span>
  
    ```xml
    <ItemGroup>
      <DotNetCliToolReference Include="dotnet-svcutil.xmlserializer" Version="1.0.0" />
    </ItemGroup>
    ```

6. <span data-ttu-id="b0495-122">Çalıştırarak uygulamayı oluşturun `dotnet build` .</span><span class="sxs-lookup"><span data-stu-id="b0495-122">Build the application by running `dotnet build`.</span></span> <span data-ttu-id="b0495-123">Her şey başarılı olursa, çıkış klasöründe *Mywcfclient. Xmlserileştiriciler. dll* adlı bir derleme oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="b0495-123">If everything succeeds, an assembly named *MyWCFClient.XmlSerializers.dll* is generated in the output folder.</span></span> <span data-ttu-id="b0495-124">Araç derlemeyi üretbir şekilde başarısız olursa, derleme çıkışında uyarılar görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="b0495-124">If the tool failed to generate the assembly, you'll see warnings in the build output.</span></span>

7. <span data-ttu-id="b0495-125">WCF hizmetini, örneğin, tarayıcıda çalışan bir şekilde başlatın `http://localhost:2561/Service1.svc` .</span><span class="sxs-lookup"><span data-stu-id="b0495-125">Start the WCF service by, for example, running `http://localhost:2561/Service1.svc` in the browser.</span></span> <span data-ttu-id="b0495-126">Ardından, istemci uygulamasını başlatın ve çalışma zamanında önceden oluşturulmuş serileştiricileri otomatik olarak yükler ve kullanır.</span><span class="sxs-lookup"><span data-stu-id="b0495-126">Then start the client application, and it will automatically load and use the pre-generated serializers at run time.</span></span>
