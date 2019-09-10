---
title: .NET Core 'da DotNet-Svcutil. XmlSerializer kullanma
description: .NET Core projeleri için bir serileştirme `dotnet-svcutil.xmlserializer` derlemesini önceden oluşturmak üzere NuGet paketini nasıl kullanabileceğinizi öğrenin.
author: huanwu
ms.date: 11/27/2018
ms.openlocfilehash: a98f8d30f2e37b722a3bf1f93be8fe9df540a468
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70848973"
---
# <a name="using-dotnet-svcutilxmlserializer-on-net-core"></a>.NET Core 'da DotNet-Svcutil. XmlSerializer kullanma

`dotnet-svcutil.xmlserializer` NuGet paketi .NET Core projeleri için bir serileştirme derlemesini önceden oluşturabilir. WCF hizmet sözleşmesi tarafından C# kullanılan ve XmlSerializer tarafından seri hale getirilebilen istemci uygulamasındaki türler için serileştirme kodu önceden oluşturulur. Bu, bu türlerin nesneleri serileştirilirken veya seri durumdan çıkarılırken XML serileştirmesinin başlangıç performansını geliştirir.

## <a name="prerequisites"></a>Önkoşullar

* [.NET Core 2,1 SDK](https://dotnet.microsoft.com/download) veya üzeri
* En sevdiğiniz kod düzenleyiciniz

.NET Core SDK ve çalışma zamanının hangi `dotnet --info` sürümlerinin yüklü olduğunu denetlemek için komutunu kullanabilirsiniz.

## <a name="getting-started"></a>Başlarken

Bir .net `dotnet-svcutil.xmlserializer` Core konsol uygulamasında kullanmak için:

1. .NET Framework ' de varsayılan ' WCF hizmet uygulaması ' şablonunu kullanarak ' MyWCFService ' adlı bir WCF hizmeti oluşturun. Aşağıdaki `[XmlSerializerFormat]` gibi hizmet yöntemine öznitelik ekleyin:

   ```csharp
    [ServiceContract]
    public interface IService1
    {
        [XmlSerializerFormat]
        [OperationContract(Action = "http://tempuri.org/IService1/GetData", ReplyAction = "http://tempuri.org/IService1/GetDataResponse")]
        string GetData(int value);
    }
    ```

2. .NET Core 2,1 veya sonraki sürümlerini hedefleyen WCF istemci uygulaması olarak bir .NET Core konsol uygulaması oluşturun. Örneğin, aşağıdaki komutla ' MyWCFClient ' adlı bir uygulama oluşturun:

    ```console
    dotnet new console --name MyWCFClient
    ```

    Projenizin .NET Core 2,1 veya sonraki bir sürümü hedeflediğinden emin olmak için, `TargetFramework` proje dosyanızdaki XML öğesini inceleyin:

    ```xml
    <TargetFramework>netcoreapp2.1</TargetFramework>
    ```

3. Aşağıdaki komutu çalıştırarak öğesine `System.ServiceModel.Http` bir paket başvurusu ekleyin:

    ```console
    dotnet add package System.ServiceModel.Http
    ```

4. WCF Istemci kodunu ekleyin:

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

5. Aşağıdaki komutu çalıştırarak `dotnet-svcutil.xmlserializer` pakete bir başvuru ekleyin:
  
    ```console
    dotnet add package dotnet-svcutil.xmlserializer
    ```

    Komutun çalıştırılması, proje dosyanıza şuna benzer bir girdi eklemeli:
  
    ```xml
    <ItemGroup>
      <DotNetCliToolReference Include="dotnet-svcutil.xmlserializer" Version="1.0.0" />
    </ItemGroup>
    ```

6. Çalıştırarak `dotnet build`uygulamayı oluşturun. Her şey başarılı olursa, çıkış klasöründe *Mywcfclient. Xmlserileştiriciler. dll* adlı bir derleme oluşturulur. Araç derlemeyi üretbir şekilde başarısız olursa, derleme çıkışında uyarılar görürsünüz.

7. WCF hizmetini, örneğin, tarayıcıda çalışan `http://localhost:2561/Service1.svc` bir şekilde başlatın. Ardından istemci uygulamasını başlatın ve çalışma zamanında önceden oluşturulmuş serileştiriciler ' ı otomatik olarak yükler ve kullanır.
