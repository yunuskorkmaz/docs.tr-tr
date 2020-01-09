---
title: DotNet-Svcutil. XmlSerializer kullanma
description: .NET Core projeleri için bir serileştirme derlemesini önceden oluşturmak üzere `dotnet-svcutil.xmlserializer` NuGet paketini nasıl kullanabileceğinizi öğrenin.
author: huanwu
ms.date: 11/27/2018
ms.openlocfilehash: 4811647c294118cb160d25805e7d3ada97f071f9
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75344894"
---
# <a name="using-dotnet-svcutilxmlserializer-on-net-core"></a>.NET Core 'da DotNet-Svcutil. XmlSerializer kullanma

`dotnet-svcutil.xmlserializer` NuGet paketi .NET Core projeleri için bir serileştirme derlemesini önceden oluşturabilir. WCF hizmet sözleşmesi tarafından C# kullanılan ve XmlSerializer tarafından seri hale getirilebilen istemci uygulamasındaki türler için serileştirme kodu önceden oluşturulur. Bu, bu türlerin nesneleri serileştirilirken veya seri durumdan çıkarılırken XML serileştirmesinin başlangıç performansını geliştirir.

## <a name="prerequisites"></a>Prerequisites

* [.NET Core 2,1 SDK](https://dotnet.microsoft.com/download) veya üzeri
* En sevdiğiniz kod düzenleyiciniz

`dotnet --info` .NET Core SDK ve çalışma zamanının hangi sürümlerinin yüklü olduğunu denetlemek için komutunu kullanabilirsiniz.

## <a name="getting-started"></a>Başlarken

Bir .NET Core konsol uygulamasında `dotnet-svcutil.xmlserializer` kullanmak için:

1. .NET Framework ' de varsayılan ' WCF hizmet uygulaması ' şablonunu kullanarak ' MyWCFService ' adlı bir WCF hizmeti oluşturun. Hizmet yöntemine aşağıdakiler gibi `[XmlSerializerFormat]` özniteliği ekleyin:

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

    ```dotnetcli
    dotnet new console --name MyWCFClient
    ```

    Projenizin .NET Core 2,1 veya sonraki bir sürümünü hedeflediğinden emin olmak için, proje dosyanızdaki `TargetFramework` XML öğesini inceleyin:

    ```xml
    <TargetFramework>netcoreapp2.1</TargetFramework>
    ```

3. Aşağıdaki komutu çalıştırarak `System.ServiceModel.Http` bir paket başvurusu ekleyin:

    ```dotnetcli
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

5. Aşağıdaki komutu çalıştırarak `dotnet-svcutil.xmlserializer` paketine bir başvuru ekleyin:
  
    ```dotnetcli
    dotnet add package dotnet-svcutil.xmlserializer
    ```

    Komutun çalıştırılması, proje dosyanıza şuna benzer bir girdi eklemeli:
  
    ```xml
    <ItemGroup>
      <DotNetCliToolReference Include="dotnet-svcutil.xmlserializer" Version="1.0.0" />
    </ItemGroup>
    ```

6. `dotnet build`çalıştırarak uygulamayı derleyin. Her şey başarılı olursa, çıkış klasöründe *Mywcfclient. Xmlserileştiriciler. dll* adlı bir derleme oluşturulur. Araç derlemeyi üretbir şekilde başarısız olursa, derleme çıkışında uyarılar görürsünüz.

7. WCF hizmetini, örneğin, tarayıcıda `http://localhost:2561/Service1.svc` çalıştırarak başlatın. Ardından istemci uygulamasını başlatın ve çalışma zamanında önceden oluşturulmuş serileştiriciler ' ı otomatik olarak yükler ve kullanır.
