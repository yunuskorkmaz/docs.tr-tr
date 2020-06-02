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
# <a name="using-dotnet-svcutilxmlserializer-on-net-core"></a>.NET Core 'da DotNet-Svcutil. XmlSerializer kullanma

`dotnet-svcutil.xmlserializer`NuGet paketi .NET Core projeleri için bir serileştirme derlemesini önceden oluşturabilir. WCF hizmet sözleşmesi tarafından kullanılan ve XmlSerializer tarafından seri hale getirileceden istemci uygulamasındaki türler için C# serileştirme kodu önceden oluşturulur. Bu, bu türlerin nesneleri serileştirilirken veya seri durumdan çıkarılırken XML serileştirmesinin başlangıç performansını geliştirir.

## <a name="prerequisites"></a>Önkoşullar

* [.NET Core 2,1 SDK](https://dotnet.microsoft.com/download) veya üzeri
* En sevdiğiniz kod düzenleyiciniz

`dotnet --info`.NET Core SDK ve çalışma zamanının hangi sürümlerinin yüklü olduğunu denetlemek için komutunu kullanabilirsiniz.

## <a name="getting-started"></a>Kullanmaya başlama

`dotnet-svcutil.xmlserializer`Bir .NET Core konsol uygulamasında kullanmak için:

1. .NET Framework ' de varsayılan ' WCF hizmet uygulaması ' şablonunu kullanarak ' MyWCFService ' adlı bir WCF hizmeti oluşturun. `[XmlSerializerFormat]`Aşağıdaki gibi hizmet yöntemine öznitelik ekleyin:

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

    Projenizin .NET Core 2,1 veya sonraki bir sürümü hedeflediğinden emin olmak için, `TargetFramework` proje dosyanızdaki XML öğesini inceleyin:

    ```xml
    <TargetFramework>netcoreapp2.1</TargetFramework>
    ```

3. Aşağıdaki komutu çalıştırarak öğesine bir paket başvurusu ekleyin `System.ServiceModel.Http` :

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

5. `dotnet-svcutil.xmlserializer`Aşağıdaki komutu çalıştırarak pakete bir başvuru ekleyin:
  
    ```dotnetcli
    dotnet add package dotnet-svcutil.xmlserializer
    ```

    Komutun çalıştırılması, proje dosyanıza şuna benzer bir girdi eklemeli:
  
    ```xml
    <ItemGroup>
      <DotNetCliToolReference Include="dotnet-svcutil.xmlserializer" Version="1.0.0" />
    </ItemGroup>
    ```

6. Çalıştırarak uygulamayı oluşturun `dotnet build` . Her şey başarılı olursa, çıkış klasöründe *Mywcfclient. Xmlserileştiriciler. dll* adlı bir derleme oluşturulur. Araç derlemeyi üretbir şekilde başarısız olursa, derleme çıkışında uyarılar görürsünüz.

7. WCF hizmetini, örneğin, tarayıcıda çalışan bir şekilde başlatın `http://localhost:2561/Service1.svc` . Ardından, istemci uygulamasını başlatın ve çalışma zamanında önceden oluşturulmuş serileştiricileri otomatik olarak yükler ve kullanır.
