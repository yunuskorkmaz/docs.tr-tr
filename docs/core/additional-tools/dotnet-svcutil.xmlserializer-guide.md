---
title: DotNet svcutil.xmlserializer üzerinde .NET Core kullanma
description: Nasıl kullanabileceğinizi öğrenin `dotnet-svcutil.xmlserializer` önceden .NET Core projeleri için bir serileştirme derlemesi oluşturmak için NuGet paketi.
author: huanwu
ms.date: 11/27/2018
ms.openlocfilehash: 375a5ad5660658431c0d327e55513024823a6eee
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65632194"
---
# <a name="using-dotnet-svcutilxmlserializer-on-net-core"></a>DotNet svcutil.xmlserializer üzerinde .NET Core kullanma

`dotnet-svcutil.xmlserializer` NuGet paketi önceden .NET Core projeleri için bir seri hale getirme derlemesi oluşturun. Önceden oluşturur C# WCF sözleşmesi tarafından kullanılır ve bu seri hale getirilemiyor XmlSerializer tarafından türleri istemci uygulamasındaki için serileştirme kodu. Bu seri hale getirme veya bu türden nesneler seri durumdan çıkarılırken zaman XML serileştirme başlangıç performansını artırır.

## <a name="prerequisites"></a>Önkoşullar

* [.NET core 2.1 SDK](https://www.microsoft.com/net/download) veya üzeri
* Sık kullandığınız kod düzenleyici

Komutunu kullanabilirsiniz `dotnet --info` .NET Core SDK ve çalışma zamanının hangi sürümlerinin zaten yüklemiş olduğunuz denetlemek için.

## <a name="getting-started"></a>Başlarken

Kullanılacak `dotnet-svcutil.xmlserializer` ' de .NET Core konsol uygulaması:

1. .NET Framework'teki varsayılan şablon 'WCF hizmet uygulaması' kullanılarak'MyWCFService ' adlı bir WCF hizmeti oluşturma. Ekleme `[XmlSerializerFormat]` özniteliği aşağıdaki gibi hizmet yöntemi:

   ```csharp
    [ServiceContract]
    public interface IService1
    {
        [XmlSerializerFormat]
        [OperationContract(Action = "http://tempuri.org/IService1/GetData", ReplyAction = "http://tempuri.org/IService1/GetDataResponse")]
        string GetData(int value);
    }
    ```

2. Bir .NET Core konsol uygulaması WCF istemci uygulaması olarak, .NET Core 2.1 veya üzeri sürümleri hedefleyen oluşturun. Örneğin, aşağıdaki komutla 'MyWCFClient' adlı bir uygulama oluşturun:

    ```console
    dotnet new console --name MyWCFClient
    ```

    Projeniz tarafından hedeflenen .NET Core 2.1 sağlayın ya da daha sonra incelemek üzere `TargetFramework` proje dosyanızda XML öğesi:

    ```xml
    <TargetFramework>netcoreapp2.1</TargetFramework>
    ```

3. Paket başvurusu ekleme `System.ServiceModel.Http` aşağıdaki komutu çalıştırarak:

    ```console
    dotnet add package System.ServiceModel.Http
    ```

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

5. Bir başvuru ekleyin `dotnet-svcutil.xmlserializer` aşağıdaki komutu çalıştırarak paketi:
  
    ```console
    dotnet add package dotnet-svcutil.xmlserializer
    ```

    Komutu çalıştırmadan proje dosyanız aşağıdakine benzer bir giriş ekleyin:
  
    ```xml
    <ItemGroup>
      <DotNetCliToolReference Include="dotnet-svcutil.xmlserializer" Version="1.0.0" />
    </ItemGroup>
    ```

6. Uygulamayı çalıştırarak oluşturmak `dotnet build`. Her şeyi başarılı olursa, adında bir derleme *MyWCFClient.XmlSerializers.dll* çıktı klasöründe oluşturulur. Araç derlemesi oluşturulamadı. derleme çıkışını uyarılar görürsünüz.

7. WCF hizmet tarafından Örneğin, çalıştırmaya başlayın `http://localhost:2561/Service1.svc` tarayıcıda. Ardından istemci uygulamasını başlatın ve bunu otomatik olarak yüklemek ve çalışma zamanında önceden oluşturulmuş seri hale getiricileri genişletme kullanın.
