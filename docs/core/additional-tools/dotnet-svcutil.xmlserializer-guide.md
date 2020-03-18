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
# <a name="using-dotnet-svcutilxmlserializer-on-net-core"></a>Dotnet-svcutil.xmlserializer üzerinde .NET Core kullanma

`dotnet-svcutil.xmlserializer` NuGet paketi .NET Core projeleri için bir serileştirme derlemesi oluşturabilir. WCF Hizmet Sözleşmesi tarafından kullanılan ve XmlSerializer tarafından serihale getirilebilen istemci uygulamasındaki türler için C# serileştirme kodunu önceden oluşturur. Bu, bu tür nesneleri serihale veya deserializing xml serileştirme başlangıç performansını artırır.

## <a name="prerequisites"></a>Önkoşullar

* [.NET Core 2.1 SDK](https://dotnet.microsoft.com/download) veya sonrası
* En sevdiğiniz kod düzenleyicisi

.NET Core `dotnet --info` SDK'nın hangi sürümlerini ve çalışma süresini zaten yüklediğinizi denetlemek için komutu kullanabilirsiniz.

## <a name="getting-started"></a>Başlarken

.NET `dotnet-svcutil.xmlserializer` Core konsol uygulamasında kullanmak için:

1. .NET Framework'deki varsayılan 'WCF Hizmet Uygulaması' şablonundan'ı kullanarak 'MyWCFService' adlı bir WCF Hizmeti oluşturun. Hizmet `[XmlSerializerFormat]` yöntemine aşağıdaki gibi öznitelik ekleyin:

   ```csharp
    [ServiceContract]
    public interface IService1
    {
        [XmlSerializerFormat]
        [OperationContract(Action = "http://tempuri.org/IService1/GetData", ReplyAction = "http://tempuri.org/IService1/GetDataResponse")]
        string GetData(int value);
    }
    ```

2. .NET Core 2.1 veya daha sonraki sürümleri hedefleyen WCF istemci uygulaması olarak bir .NET Core konsol uygulaması oluşturun. Örneğin, aşağıdaki komutla 'MyWCFClient' adında bir uygulama oluşturun:

    ```dotnetcli
    dotnet new console --name MyWCFClient
    ```

    Projenizin .NET Core 2.1 veya sonraki leri `TargetFramework` hedeflediğinden emin olmak için proje dosyanızdaki XML öğesini inceleyin:

    ```xml
    <TargetFramework>netcoreapp2.1</TargetFramework>
    ```

3. Aşağıdaki komutu `System.ServiceModel.Http` çalıştırarak bir paket başvurusu ekleyin:

    ```dotnetcli
    dotnet add package System.ServiceModel.Http
    ```

4. WCF İstemci kodunu ekleyin:

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

5. Aşağıdaki komutu `dotnet-svcutil.xmlserializer` çalıştırarak pakete bir başvuru ekleyin:
  
    ```dotnetcli
    dotnet add package dotnet-svcutil.xmlserializer
    ```

    Komutu çalıştırmak, proje dosyanıza buna benzer bir giriş eklemelidir:
  
    ```xml
    <ItemGroup>
      <DotNetCliToolReference Include="dotnet-svcutil.xmlserializer" Version="1.0.0" />
    </ItemGroup>
    ```

6. Çalıştırarak `dotnet build`uygulamayı oluşturun. Her şey başarılı olursa, çıktı klasöründe *MyWCFClient.XmlSerializers.dll* adlı bir derleme oluşturulur. Araç derlemeyi oluşturamazsa, yapı çıktısında uyarılar görürsünüz.

7. WCF hizmetini, örneğin tarayıcıda `http://localhost:2561/Service1.svc` çalıştırarak başlatın. Ardından istemci uygulamasını başlatın ve otomatik olarak yüklenir ve çalışma zamanında önceden oluşturulmuş serializers kullanır.
