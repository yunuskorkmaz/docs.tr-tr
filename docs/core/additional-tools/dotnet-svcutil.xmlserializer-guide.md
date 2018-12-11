# <a name="using-dotnet-svcutilxmlserializer-on-net-core"></a>DotNet svcutil.xmlserializer üzerinde .NET Core kullanma

## <a name="prerequisites"></a>Önkoşullar

Dotnet-çalışmaya svcutil.xmlserializer için aşağıdakiler gereklidir. 

* [.NET core 2.1 SDK veya üzeri](https://www.microsoft.com/net/download/dotnet-core/sdk-2.1.300)
* [.NET core çalışma zamanı 2.1 veya üzeri](https://www.microsoft.com/net/download/dotnet-core/runtime-2.1.0)

Komutunu kullanabilirsiniz `dotnet --info` .NET Core SDK ve çalışma zamanının hangi sürümlerinin zaten yüklemiş olduğunuz denetlemek için.

Bir .NET Core konsol uygulaması dotnet svcutil.xmlserializer kullanmak için:

1. .NET Framework'teki varsayılan şablon 'WCF hizmet uygulaması' kullanılarak'MyWCFService ' adlı bir WCF hizmeti oluşturma.  Ekleme ```[XmlSerializerFormat]``` özniteliği aşağıdaki gibi hizmet yöntemi
    ```c#
    [ServiceContract]
    public interface IService1
    {
        [XmlSerializerFormat]
        [OperationContract(Action = "http://tempuri.org/IService1/GetData", ReplyAction = "http://tempuri.org/IService1/GetDataResponse")]
        string GetData(int value);
    }
    ```
2. WCF istemci uygulaması hedefleri netcoreapp 2.1, örneğin oluşturduğunuz komutuyla 'MyWCFClient' adlı bir uygulama olarak bir .NET Core konsol uygulaması oluşturun
    ```
    dotnet new console --name MyWCFClient
    ```
    Bir netcoreapp 2.1, csproj hedeflediğinden emin olun. Bu yapılır .csproj dosyanızda aşağıdaki XML öğesi kullanma
    ```xml
    <TargetFramework>netcoreapp2.1</TargetFramework>
    ```
3. Aşağıdaki komutu çalıştırarak System.ServiceModel.Http paket başvurusu ekleme:
   
   ```dotnet add package System.ServiceModel.Http -v 4.5.0```

4. WCF istemci kodu ekleyin:
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
5. .Csproj dosyasını düzenleyin ve dotnet svcutil.xmlserializer paketine bir başvuru ekleyin. Örneğin:

    i. Komutu çalıştırın: `dotnet add package dotnet-svcutil.xmlserializer -v 1.0.0`

    ii. İçinde MyWCFClient.csproj aşağıdaki satırları ekleyin,
    ```xml
    <ItemGroup>
      <DotNetCliToolReference Include="dotnet-svcutil.xmlserializer" Version="1.0.0" />
    </ItemGroup>
    ```

6. Uygulamayı çalıştırarak oluşturmak `dotnet build`. Her şeyi başarılı olursa MyWCFClient.XmlSerializers.dll adlı bir derleme çıktı klasöründe oluşturulur. Araç derlemesi oluşturulamadı. derleme çıkışını uyarılar görürsünüz.

7. WCF hizmeti, örneğin çalıştırarak başlatın http://localhost:2561/Service1.svc tarayıcıda. Ardından istemci uygulamasını başlatın ve bunu otomatik olarak yüklemek ve çalışma zamanında önceden oluşturulmuş seri hale getiricileri genişletme kullanın.
