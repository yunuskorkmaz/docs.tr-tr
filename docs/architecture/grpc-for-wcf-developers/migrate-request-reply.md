---
title: WCF geliştiricileri için bir WCF isteği-yanıt hizmetini gRPC-gRPC 'ye geçirme
description: WCF 'den gRPC 'ye basit bir istek-yanıt hizmeti geçirmeyi öğrenin.
ms.date: 09/02/2019
ms.openlocfilehash: 29a7bc77bc3a4becd767fc7a50adff5b746f54bc
ms.sourcegitcommit: d0990c1c1ab2f81908360f47eafa8db9aa165137
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97512703"
---
# <a name="migrate-a-wcf-request-reply-service-to-a-grpc-unary-rpc"></a>WCF isteği yanıt verme hizmetini gRPC birli RPC 'ye geçirme

Bu bölümde, WCF 'de temel bir istek-yanıt hizmetinin ASP.NET Core gRPC 'deki birli RPC hizmetine geçirilmesi ele alınmaktadır. Bu hizmetler hem Windows Communication Foundation (WCF) hem de gRPC içindeki en basit hizmet türleridir. bu nedenle başlamak için mükemmel bir yerdir. Hizmeti geçirdikten sonra, `.proto` bir .NET istemci uygulamasından hizmeti kullanmak için aynı dosyadan bir istemci kitaplığı oluşturmayı öğreneceksiniz.

## <a name="the-wcf-solution"></a>WCF çözümü

[PortfoliosSample çözümü](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/PortfoliosSample/wcf/TraderSys) , belirli bir eğitime için tek bir portföy ya da tüm portföyleri indirmek üzere basit bir istek-yanıt portföyü hizmeti içerir. Hizmet, arabiriminde `IPortfolioService` bir özniteliği ile tanımlanmıştır `ServiceContract` :

```csharp
[ServiceContract]
public interface IPortfolioService
{
    [OperationContract]
    Task<Portfolio> Get(Guid traderId, int portfolioId);

    [OperationContract]
    Task<List<Portfolio>> GetAll(Guid traderId);
}
```

`Portfolio`Model, [DataContract](xref:System.Runtime.Serialization.DataContractAttribute) ile işaretlenmiş ve nesne listesi dahil olmak üzere basit bir C# sınıfıdır `PortfolioItem` . Bu modeller `TraderSys.PortfolioData` projede, bir veri erişimi soyutlamasını temsil eden bir depo sınıfıyla birlikte tanımlanmıştır.

```csharp
[DataContract]
public class Portfolio
{
    [DataMember]
    public int Id { get; set; }

    [DataMember]
    public Guid TraderId { get; set; }

    [DataMember]
    public List<PortfolioItem> Items { get; set; }
}

[DataContract]
public class PortfolioItem
{
    [DataMember]
    public int Id { get; set; }

    [DataMember]
    public int ShareId { get; set; }

    [DataMember]
    public int Holding { get; set; }

    [DataMember]
    public decimal Cost { get; set; }
}
```

`ServiceContract`Uygulama, türlerin örneklerini döndüren bağımlılık ekleme yoluyla sağlanmış bir depo sınıfı kullanır `DataContract` :

```csharp
public class PortfolioService : IPortfolioService
{
    private readonly IPortfolioRepository _repository;

    public PortfolioService(IPortfolioRepository repository)
    {
        _repository = repository;
    }

    public async Task<Portfolio> Get(Guid traderId, int portfolioId)
    {
        return await _repository.GetAsync(traderId, portfolioId);
    }

    public async Task<List<Portfolio>> GetAll(Guid traderId)
    {
        return await _repository.GetAllAsync(traderId);
    }
}
```

## <a name="the-portfoliosproto-file"></a>Portföyler. proto dosyası

Önceki bölümde yer alan yönergeleri izlediyseniz şuna benzer bir dosya içeren bir gRPC projeniz olmalıdır `portfolios.proto` :

```protobuf
syntax = "proto3";

option csharp_namespace = "TraderSys.Portfolios.Protos";

package PortfolioServer;

service Portfolios {
  // RPCs will go here
}
```

İlk adım, `DataContract` sınıfları prototip eşdeğerlerine geçirmeyecektir.

## <a name="convert-the-datacontract-classes-to-grpc-messages"></a>DataContract sınıflarını gRPC iletilerine Dönüştür

Sınıfı, `PortfolioItem` `Portfolio` sınıf kendisine bağlı olduğundan, önce bir prototipme iletisine dönüştürülür. Sınıfı basittir ve özelliklerden üçü doğrudan gRPC veri türlerine eşlenir. Satın alımlardaki `Cost` paylaşımlar için ödenen fiyatı temsil eden özelliği bir `decimal` alandır. gRPC yalnızca `float` `double` , para birimi için uygun olmayan gerçek sayıları destekler. Paylaşma fiyatları, en az bir sent 'a göre farklılık gösterdiğinden, maliyet, bir ilal olarak ifade edilebilir `int32` .

> [!NOTE]
> `snake_case`Dosyanızdaki alan adları için kullanmayı unutmayın `.proto` . C# kod Oluşturucu bunları `PascalCase` sizin için dönüştürür ve diğer dillerin kullanıcıları farklı kodlama standartlarını daha da tahmin etmek için teşekkür ederiz.

```protobuf
message PortfolioItem {
    int32 id = 1;
    int32 share_id = 2;
    int32 holding = 3;
    int32 cost_cents = 4;
}
```

`Portfolio`Sınıf biraz daha karmaşıktır. WCF kodunda, Geliştirici `Guid` özelliği için bir kullanır `TraderId` ve bir içerir `List<PortfolioItem>` . Birinci sınıf türüne sahip olmayan prototipte, `UUID` `string` alanı için bir kullanmalı `traderId` ve kendi kodunuzda ayrıştırmalısınız. Öğelerin listesi için `repeated` alandaki anahtar sözcüğünü kullanın.

```protobuf
message Portfolio {
    int32 id = 1;
    string trader_id = 2;
    repeated PortfolioItem items = 3;
}
```

Artık veri iletilerine sahip olduğunuza göre, hizmet RPC uç noktalarını bildirebilirsiniz.

## <a name="convert-servicecontract-to-a-grpc-service"></a>ServiceContract 'i gRPC hizmetine dönüştürme

WCF `Get` yöntemi iki parametre alır: `Guid traderId` ve `int portfolioId` . gRPC hizmeti yöntemleri yalnızca tek bir parametre alabilir, bu nedenle iki değeri tutacak bir ileti oluşturmanız gerekir. Bu istek nesnelerini, ve ardından sonek tarafından aynı ada sahip olacak şekilde adlandırmak yaygın bir uygulamadır `Request` . `string` `traderId` Bunun yerine, alanı için kullanılıyor `Guid` .

Hizmet yalnızca bir `Portfolio` iletiyi doğrudan döndürebilir, ancak bu, gelecekte geriye dönük uyumluluğu etkileyebilir. `Request` `Response` Çoğu bir hizmette aynı anda aynı olsa bile, her bir yöntemde ayrı ve iletileri tanımlamak iyi bir uygulamadır. Bu nedenle `GetResponse` , tek bir alan içeren bir ileti bildirin `Portfolio` .

Bu örnekte, gRPC hizmeti yönteminin bildirimi şu `GetRequest` iletiyle gösterilmektedir:

```protobuf
message GetRequest {
    string trader_id = 1;
    int32 portfolio_id = 2;
}

message GetResponse {
    Portfolio portfolio = 1;
}

service Portfolios {
    rpc Get(GetRequest) returns (GetResponse);
}
```

WCF `GetAll` yöntemi yalnızca tek bir parametre alır, bu `traderId` yüzden `string` parametre türü olarak belirtebileceğiniz görünebilir. Ancak gRPC tanımlı bir ileti türü gerektirir. Bu gereksinim, ileri doğru uyumluluk için tüm girişler ve çıkışlar için özel iletiler kullanma uygulamasını zorlamaya yardımcı olur.

WCF Yöntemi de döndürür `List<Portfolio>` , ancak basit parametre türlerine izin vermediğinden aynı nedenden dolayı gRPC, `repeated Portfolio` dönüş türü olarak izin vermez. Bunun yerine, `GetAllResponse` Listeyi kaydırmak için bir tür oluşturun.

> [!WARNING]
> Bir `PortfolioList` ileti veya benzer bir ileti oluşturabilir ve bunu birden çok hizmet yöntemi genelinde kullanabilirsiniz, ancak bu geçici yeniden ölçeklendirmelisiniz. Bir hizmette çeşitli yöntemlerin nasıl gelişeceğimizi bilmek olanaksızdır, bu sayede iletilerini özel ve düzgün bir şekilde ayrılmış olarak tutun.

```protobuf
message GetAllRequest {
    string trader_id = 1;
}

message PortfolioList {
    repeated Portfolio portfolios = 1;
}

service Portfolios {
    rpc Get(GetRequest) returns (Portfolio);
    rpc GetAll(GetAllRequest) returns (GetAllResponse);
}
```

Projenizi bu değişikliklerle kaydederseniz, gRPC derleme hedefi arka planda çalışır ve tüm prototip ileti türlerini ve hizmeti uygulamak için kalıtımla oluşturabileceğiniz bir temel sınıfı oluşturur.

Sınıfını açın `Services/GreeterService.cs` ve örnek kodu silin. Artık portföy hizmeti uygulamasını ekleyebilirsiniz. Oluşturulan temel sınıf `Protos` ad alanında olur ve iç içe yerleştirilmiş bir sınıf olarak oluşturulur. gRPC, dosyadaki hizmetle aynı ada sahip bir statik sınıf `.proto` ve bu statik sınıfın içindeki sonekine sahip bir temel sınıf oluşturur `Base` . bu nedenle, temel tür için tam tanımlayıcı olur `TraderSys.Portfolios.Protos.Portfolios.PortfoliosBase` .

```csharp
namespace TraderSys.Portfolios.Services
{
    public class PortfolioService : Protos.Portfolios.PortfoliosBase
    {
    }
}
```

Temel sınıf, `virtual` `Get` `GetAll` hizmetini uygulamak için geçersiz kılınabilen ve için yöntemleri bildirir. Yöntemler yerine, `virtual` `abstract` bunları uygulamadıysanız `Unimplemented` bir, normal C# kodunda bir oluşturma gibi açık bir GRPC durum kodu döndürebilir `NotImplementedException` .

ASP.NET Core içindeki tüm gRPC birli hizmet yöntemleri için imza tutarlıdır. İki parametre vardır: ilki dosyada bildirildiği ileti türüdür `.proto` ve ikincisi, `ServerCallContext` from ASP.NET Core benzer şekilde çalışır `HttpContext` . Aslında, temel aldığı için kullanabileceğiniz bir genişletme yöntemi vardır `GetHttpContext` `ServerCallContext` `HttpContext` , ancak bunu sık kullanmanıza gerek kalmaz. `ServerCallContext`Bu bölümde daha sonra ve ayrıca kimlik doğrulamasını ele alan bölümde bir göz atalım.

Yöntemin dönüş türü bir `Task<T>` , burada `T` yanıt iletisi türüdür. Tüm gRPC hizmet yöntemleri zaman uyumsuzdur.

## <a name="migrate-the-portfoliodata-library-to-net-core"></a>PortfolioData kitaplığını .NET Core 'a geçirme

Bu noktada projenin, `TraderSys.PortfolioData` WCF çözümünde sınıf kitaplığında bulunan portföy deposuna ve modellerine ihtiyacı vardır. Bunu yapmanın en kolay yolu, sınıf kitaplığı (.NET Standard) şablonuyla Visual Studio **Yeni proje** iletişim kutusunu kullanarak ya da .NET Core CLI kullanarak komut satırından, dosyayı içeren dizinden bu komutları çalıştırarak yeni bir sınıf kitaplığı oluşturmaktır `TraderSys.sln` :

```dotnetcli
dotnet new classlib -o src/TraderSys.PortfolioData
dotnet sln add src/TraderSys.PortfolioData
```

Kitaplığı oluşturup çözüme ekledikten sonra, oluşturulan `Class1.cs` dosyayı silin ve dosyaları WCF çözümünün kitaplığından yeni sınıf kitaplığının klasörüne kopyalayın ve klasör yapısını saklayın:

```
Models
  Portfolio.cs
  PortfolioItem.cs
IPortfolioRepository.cs
PortfolioRepository.cs
```

SDK stili .NET projeleri otomatik olarak `.cs` kendi dizinine veya altına tüm dosyaları dahil eder, bu nedenle bunları projeye açıkça eklemeniz gerekmez. Kalan tek adım, ve `DataContract` sınıflarının ve özniteliklerinin, `DataMember` `Portfolio` `PortfolioItem` düz eski C# sınıfları olacak şekilde kaldırılması:

```csharp
public class Portfolio
{
    public int Id { get; set; }
    public Guid TraderId { get; set; }
    public List<PortfolioItem> Items { get; set; }
}

public class PortfolioItem
{
    public int Id { get; set; }
    public int ShareId { get; set; }
    public int Holding { get; set; }
    public decimal Cost { get; set; }
}
```

## <a name="use-aspnet-core-dependency-injection"></a>ASP.NET Core bağımlılığı ekleme kullanma

Artık gRPC uygulama projesine bu kitaplığa bir başvuru ekleyebilir ve `PortfolioRepository` GRPC hizmeti uygulamasında bağımlılık ekleme 'yi kullanarak sınıfı kullanabilirsiniz. WCF uygulamasında, bağımlılık ekleme Autofac IoC kapsayıcısı tarafından sağlandı. ASP.NET Core içinde bağımlılık ekleme ' ye sahiptir. Depoyu `ConfigureServices` sınıfındaki metoduna kaydedebilirsiniz `Startup` :

```csharp
public class Startup
{
    public void ConfigureServices(IServiceCollection services)
    {
        // Register the repository class as a scoped service (instance per request)
        services.AddScoped<IPortfolioRepository, PortfolioRepository>();

        services.AddGrpc();
    }

    // ...
}
```

`IPortfolioRepository`Uygulama artık sınıfında bir oluşturucu parametresi olarak belirtilebilir `PortfolioService` , şöyle olabilir:

```csharp
public class PortfolioService : Protos.Portfolios.PortfoliosBase
{
    private readonly IPortfolioRepository _repository;

    public PortfolioService(IPortfolioRepository repository)
    {
        _repository = repository;
    }
}
```

## <a name="implement-the-grpc-service"></a>GRPC hizmetini uygulama

Artık iletilerinizi ve hizmetinizi dosyada bildirdiğine göre `portfolios.proto` , hizmet yöntemlerini `PortfolioService` GRPC tarafından oluşturulan sınıftan devralan sınıfta uygulamanız gerekir `Portfolios.PortfoliosBase` . Yöntemler, temel sınıfta olduğu gibi bildirilmiştir `virtual` . Bunları geçersiz kılamazsanız, varsayılan olarak bir gRPC "uygulanmamış" durum kodu döndürür.

Yöntemini uygulayarak başlatın `Get` . Varsayılan geçersiz kılma Şu örneğe benzer şekilde görünür:

```csharp
public override Task<GetResponse> Get(GetRequest request, ServerCallContext context)
{
    return base.Get(request, context);
}
```

İlk sorun `request.TraderId` bir dizedir ve hizmet için gerekir `Guid` . Dize için beklenen biçim olsa da `UUID` , kod çağıranın geçersiz bir değer gönderdiği ve uygun şekilde yanıt verdiği olasılığa karşı uğraşmak zorunda olur. Hizmet, `RpcException` sorunu ifade etmek için bir oluşturarak ve standart durum kodunu kullanarak hatalarla yanıt verebilir `InvalidArgument` :

```csharp
public override Task<GetResponse> Get(GetRequest request, ServerCallContext context)
{
    if (!Guid.TryParse(request.TraderId, out var traderId))
    {
        throw new RpcException(new Status(StatusCode.InvalidArgument, "traderId must be a UUID"));
    }

    return base.Get(request, context);
}
```

İçin uygun bir değer olduktan sonra `Guid` `traderId` , portföyü almak ve istemciye döndürmek için depoyu kullanabilirsiniz:

```csharp
    var response = new GetResponse
    {
        Portfolio = await _repository.GetAsync(request.TraderId, request.PortfolioId)
    };
```

### <a name="map-internal-models-to-grpc-messages"></a>İç modelleri gRPC iletilerine eşleme

Önceki kod aslında çalışmıyor çünkü depo kendi POCO modelini döndürüyor `Portfolio` , ancak gRPC 'nin kendi prototipli mesajına ihtiyacı vardır `Portfolio` . Entity Framework türlerini veri aktarım türleriyle eşleştirdiğinizde, en iyi çözüm iki arasında dönüştürme sağlamaktır. Bu dönüştürmeye yönelik kodu yerleştirmek için iyi bir yer vardır. Bu, genişletilebilecek bir sınıf olarak bildirildiği Protoarabelleğe oluşturulmuş sınıfta `partial` :

```csharp
namespace TraderSys.Portfolios.Protos
{
    public partial class PortfolioItem
    {
        public static PortfolioItem FromRepositoryModel(PortfolioData.Models.PortfolioItem source)
        {
            if (source is null) return null;

            return new PortfolioItem
            {
                Id = source.Id,
                ShareId = source.ShareId,
                Holding = source.Holding,
                CostCents = (int)(source.Cost * 100)
            };
        }
    }

    public partial class Portfolio
    {
        public static Portfolio FromRepositoryModel(PortfolioData.Models.Portfolio source)
        {
            if (source is null) return null;

            var target = new Portfolio
            {
                Id = source.Id,
                TraderId = source.TraderId.ToString(),
            };

            target.Items.AddRange(source.Items.Select(PortfolioItem.FromRepositoryModel));

            return target;
        }
    }
}
```

> [!NOTE]
> [](https://automapper.org/) `string` / `Guid` Ya da `decimal` / `double` ve liste eşlemesi gibi alt düzey tür dönüştürmeleri yapılandırdığınız sürece, iç model sınıflarından bu dönüştürmeyi prototip türlerine işlemek için automaber gibi bir kitaplık kullanabilirsiniz.

Artık dönüştürme koduna sahip olduğunuza göre, `Get` Yöntem uygulamasını tamamlayabilirsiniz:

```csharp
public override async Task<GetResponse> Get(GetRequest request, ServerCallContext context)
{
    if (!Guid.TryParse(request.TraderId, out var traderId))
    {
        throw new RpcException(new Status(StatusCode.InvalidArgument, "traderId must be a UUID"));
    }

    var portfolio = await _repository.GetAsync(traderId, request.PortfolioId);

    return new GetResponse
    {
        Portfolio = Portfolio.FromRepositoryModel(portfolio)
    };
}

```

`GetAll`Yöntemin uygulanması benzerdir. `repeated`Prototipsiz iletilerde bulunan alanların `readonly` türünün özellikleri olarak oluşturulduğunu `RepeatedField<T>` , `AddRange` Bu nedenle bu örnekte olduğu gibi yöntemini kullanarak öğeleri eklemeniz gerekir:

```csharp
public override async Task<GetAllResponse> GetAll(GetAllRequest request, ServerCallContext context)
{
    if (!Guid.TryParse(request.TraderId, out var traderId))
    {
        throw new RpcException(new Status(StatusCode.InvalidArgument, "traderId must be a UUID"));
    }

    var portfolios = await _repository.GetAllAsync(traderId);

    var response = new GetAllResponse();
    response.Portfolios.AddRange(portfolios.Select(Portfolio.FromRepositoryModel));

    return response;
}
```

WCF istek-yanıt verme hizmetini başarıyla gRPC 'ye geçirdiyseniz, bu dosya için bir istemci oluşturmaya göz atalım `.proto` .

## <a name="generate-client-code"></a>İstemci kodu oluştur

İstemcisini içermesi için aynı çözümde bir .NET Standard sınıf kitaplığı oluşturun. Bu öncelikle istemci kodu oluşturma örneğidir, ancak bu tür bir kitaplığı NuGet kullanarak paketleyebilir ve diğer .NET ekibinin kullanması için bir iç depoya dağıtabilirsiniz. Devam edin ve çözüme adlı yeni bir .NET Standard sınıfı kitaplığı ekleyin `TraderSys.Portfolios.Client` ve `Class1.cs` dosyayı silin.

> [!CAUTION]
> [GRPC .net. Client](https://www.nuget.org/packages/Grpc.Net.Client) NuGet paketi .net Core 3,0 (veya başka bir .NET Standard 2,1 uyumlu çalışma zamanı) gerektirir. .NET Framework ve .NET Core 'un önceki sürümleri [GRPC. Core](https://www.nuget.org/packages/Grpc.Core) NuGet paketi tarafından desteklenir.

Visual Studio 2019 ' de, Visual Studio 'nun önceki sürümlerindeki WCF projelerine hizmet başvuruları ekleme yöntemine benzer bir şekilde gRPC hizmetlerine başvurular ekleyebilirsiniz. Hizmet başvuruları ve bağlı hizmetler artık aynı kullanıcı arabirimi altında yönetilir. Çözüm Gezgini ' de projedeki **Bağımlılıklar** düğümüne sağ tıklayıp `TraderSys.Portfolios.Client` **bağlı hizmet ekle**' yi seçerek kullanıcı arabirimine erişebilirsiniz. Görüntülenen araç penceresinde, **hizmet başvuruları** bölümünü seçin ve ardından **Yeni GRPC hizmet başvurusu Ekle**' yi seçin:

![Visual Studio 2019 'de bağlı hizmetler kullanıcı arabirimi](media/migrate-request-reply/add-connected-service.png)

`portfolios.proto`Projedeki dosyaya gidin `TraderSys.Portfolios` , çalıştırılacak **sınıf türünü seçin** altında **istemciden** bırakın ve **Tamam**' ı seçin:

![Visual Studio 2019 ' de yeni gRPC hizmet başvurusu Ekle iletişim kutusu](media/migrate-request-reply/add-new-grpc-service-reference.png)

> [!TIP]
> Bu iletişim kutusunun Ayrıca bir URL alanı sağladığını unutmayın. Kuruluşunuz, Web 'de erişilebilir bir dosya dizini tutuyorsa `.proto` , bu URL adresini ayarlayarak istemcileri oluşturabilirsiniz.

Visual Studio **bağlı hizmet ekle** özelliğini kullandığınızda, `portfolios.proto` Dosya, sınıf kitaplığı projesine kopyalamak yerine *bağlantılı bir dosya* olarak eklenir, bu nedenle hizmet projesindeki dosyada yapılan değişiklikler istemci projesinde otomatik olarak uygulanır. `<Protobuf>`Dosyadaki öğesi şöyle `csproj` görünür:

```xml
<Protobuf Include="..\TraderSys.Portfolios\Protos\portfolios.proto" GrpcServices="Client">
  <Link>Protos\portfolios.proto</Link>
</Protobuf>
```

> [!TIP]
> Visual Studio kullanmıyorsanız veya komut satırından çalışmayı tercih ediyorsanız, `dotnet-grpc` bir .net gRPC projesindeki prototipsel başvuruları yönetmek için genel aracı kullanabilirsiniz. Daha fazla bilgi için [ `dotnet-grpc` belgelerine](/aspnet/core/grpc/dotnet-grpc)bakın.

### <a name="use-the-portfolios-service-from-a-client-application"></a>Bir istemci uygulamasından portföyde hizmetini kullanma

Aşağıdaki kod, bir konsol uygulamasında oluşturulan istemciyi nasıl kullanacağınızı gösteren kısa bir örnektir. GRPC istemci kodunun daha ayrıntılı bir araştırması, bu bölümün sonunda bulunur.

```csharp
public class Program
{
    public async Task Main(string[] args)
    {
        GetResponse response;

        using (var channel = GrpcChannel.ForAddress("https://localhost:5001"))
        {
            var client = new Protos.Portfolios.PortfoliosClient(channel);

            response = await client.GetAsync(new GetRequest
            {
                TraderId = args[0],
                PortfolioId = int.Parse(args[1])
            });
        }

        foreach (var item in response.Portfolio.Items)
        {
            Console.WriteLine($"Holding {item.Holding} of Share ID {item.ShareId}.");
        }
    }
}
```

Artık temel bir WCF uygulamasını ASP.NET Core gRPC hizmetine geçirdiniz ve hizmeti bir .NET uygulamasından tüketmek için bir istemci oluşturdunuz. Sonraki bölümde, ilgili çift yönlü hizmetler ele alınacaktır.

>[!div class="step-by-step"]
>[Önceki](create-project.md) 
> [Sonraki](migrate-duplex-services.md)
