# <a name="using-dotnet-svcutilxmlserializer-on-net-core"></a><span data-ttu-id="94c8d-101">DotNet svcutil.xmlserializer üzerinde .NET Core kullanma</span><span class="sxs-lookup"><span data-stu-id="94c8d-101">Using dotnet-svcutil.xmlserializer on .NET Core</span></span>

## <a name="prerequisites"></a><span data-ttu-id="94c8d-102">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="94c8d-102">Prerequisites</span></span>

<span data-ttu-id="94c8d-103">Dotnet-çalışmaya svcutil.xmlserializer için aşağıdakiler gereklidir.</span><span class="sxs-lookup"><span data-stu-id="94c8d-103">The following is required for dotnet-svcutil.xmlserializer to work.</span></span> 

* [<span data-ttu-id="94c8d-104">.NET core 2.1 SDK veya üzeri</span><span class="sxs-lookup"><span data-stu-id="94c8d-104">.NET Core 2.1 SDK or later</span></span>](https://www.microsoft.com/net/download/dotnet-core/sdk-2.1.300)
* [<span data-ttu-id="94c8d-105">.NET core çalışma zamanı 2.1 veya üzeri</span><span class="sxs-lookup"><span data-stu-id="94c8d-105">.NET Core Runtime 2.1 or later</span></span>](https://www.microsoft.com/net/download/dotnet-core/runtime-2.1.0)

<span data-ttu-id="94c8d-106">Komutunu kullanabilirsiniz `dotnet --info` .NET Core SDK ve çalışma zamanının hangi sürümlerinin zaten yüklemiş olduğunuz denetlemek için.</span><span class="sxs-lookup"><span data-stu-id="94c8d-106">You can use the command `dotnet --info` to check which versions of .NET Core SDK and runtime you already have installed.</span></span>

<span data-ttu-id="94c8d-107">Bir .NET Core konsol uygulaması dotnet svcutil.xmlserializer kullanmak için:</span><span class="sxs-lookup"><span data-stu-id="94c8d-107">To use dotnet-svcutil.xmlserializer in a .NET Core console application:</span></span>

1. <span data-ttu-id="94c8d-108">.NET Framework'teki varsayılan şablon 'WCF hizmet uygulaması' kullanılarak'MyWCFService ' adlı bir WCF hizmeti oluşturma.</span><span class="sxs-lookup"><span data-stu-id="94c8d-108">Create a WCF Service named 'MyWCFService' using the default template 'WCF Service Application' in .NET Framework.</span></span>  <span data-ttu-id="94c8d-109">Ekleme ```[XmlSerializerFormat]``` özniteliği aşağıdaki gibi hizmet yöntemi</span><span class="sxs-lookup"><span data-stu-id="94c8d-109">Add ```[XmlSerializerFormat]``` attribute on the service method like the following</span></span>
    ```c#
    [ServiceContract]
    public interface IService1
    {
        [XmlSerializerFormat]
        [OperationContract(Action = "http://tempuri.org/IService1/GetData", ReplyAction = "http://tempuri.org/IService1/GetDataResponse")]
        string GetData(int value);
    }
    ```
2. <span data-ttu-id="94c8d-110">WCF istemci uygulaması hedefleri netcoreapp 2.1, örneğin oluşturduğunuz komutuyla 'MyWCFClient' adlı bir uygulama olarak bir .NET Core konsol uygulaması oluşturun</span><span class="sxs-lookup"><span data-stu-id="94c8d-110">Create a .NET Core console application as WCF client application that targets at netcoreapp 2.1, e.g. create an app named 'MyWCFClient' with the command,</span></span>
    ```
    dotnet new console --name MyWCFClient
    ```
    <span data-ttu-id="94c8d-111">Bir netcoreapp 2.1, csproj hedeflediğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="94c8d-111">Make sure your csproj targets a netcoreapp 2.1.</span></span> <span data-ttu-id="94c8d-112">Bu yapılır .csproj dosyanızda aşağıdaki XML öğesi kullanma</span><span class="sxs-lookup"><span data-stu-id="94c8d-112">This is done using the following XML element in your .csproj file</span></span>
    ```xml
    <TargetFramework>netcoreapp2.1</TargetFramework>
    ```
3. <span data-ttu-id="94c8d-113">Aşağıdaki komutu çalıştırarak System.ServiceModel.Http paket başvurusu ekleme:</span><span class="sxs-lookup"><span data-stu-id="94c8d-113">Add a package reference to System.ServiceModel.Http by running the following command:</span></span>
   
   ```dotnet add package System.ServiceModel.Http -v 4.5.0```

4. <span data-ttu-id="94c8d-114">WCF istemci kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="94c8d-114">Add the WCF Client code:</span></span>
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
5. <span data-ttu-id="94c8d-115">.Csproj dosyasını düzenleyin ve dotnet svcutil.xmlserializer paketine bir başvuru ekleyin.</span><span class="sxs-lookup"><span data-stu-id="94c8d-115">Edit the .csproj file and add a reference to the dotnet-svcutil.xmlserializer package.</span></span> <span data-ttu-id="94c8d-116">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="94c8d-116">For example:</span></span>

    <span data-ttu-id="94c8d-117">i.</span><span class="sxs-lookup"><span data-stu-id="94c8d-117">i.</span></span> <span data-ttu-id="94c8d-118">Komutu çalıştırın: `dotnet add package dotnet-svcutil.xmlserializer -v 1.0.0`</span><span class="sxs-lookup"><span data-stu-id="94c8d-118">Run command: `dotnet add package dotnet-svcutil.xmlserializer -v 1.0.0`</span></span>

    <span data-ttu-id="94c8d-119">ii.</span><span class="sxs-lookup"><span data-stu-id="94c8d-119">ii.</span></span> <span data-ttu-id="94c8d-120">İçinde MyWCFClient.csproj aşağıdaki satırları ekleyin,</span><span class="sxs-lookup"><span data-stu-id="94c8d-120">Add the following lines in MyWCFClient.csproj,</span></span>
    ```xml
    <ItemGroup>
      <DotNetCliToolReference Include="dotnet-svcutil.xmlserializer" Version="1.0.0" />
    </ItemGroup>
    ```

6. <span data-ttu-id="94c8d-121">Uygulamayı çalıştırarak oluşturmak `dotnet build`.</span><span class="sxs-lookup"><span data-stu-id="94c8d-121">Build the application by running `dotnet build`.</span></span> <span data-ttu-id="94c8d-122">Her şeyi başarılı olursa MyWCFClient.XmlSerializers.dll adlı bir derleme çıktı klasöründe oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="94c8d-122">If everything succeeds, an assembly named MyWCFClient.XmlSerializers.dll will be generated in the output folder.</span></span> <span data-ttu-id="94c8d-123">Araç derlemesi oluşturulamadı. derleme çıkışını uyarılar görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="94c8d-123">You will see warnings in the build output if the tool failed to generate the assembly.</span></span>

7. <span data-ttu-id="94c8d-124">WCF hizmeti, örneğin çalıştırarak başlatın http://localhost:2561/Service1.svc tarayıcıda.</span><span class="sxs-lookup"><span data-stu-id="94c8d-124">Start the WCF service e.g. by running http://localhost:2561/Service1.svc in the browser.</span></span> <span data-ttu-id="94c8d-125">Ardından istemci uygulamasını başlatın ve bunu otomatik olarak yüklemek ve çalışma zamanında önceden oluşturulmuş seri hale getiricileri genişletme kullanın.</span><span class="sxs-lookup"><span data-stu-id="94c8d-125">Then start the client application, and it will automatically load and use the pre-generated serializers at runtime.</span></span>
