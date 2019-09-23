---
title: WCF geliştiricileri için bir WCF isteği-yanıt hizmetini gRPC-gRPC 'ye geçirme
description: WCF 'den gRPC 'ye basit bir istek-yanıt hizmeti geçirmeyi öğrenin.
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: ac9eecf66a7ac37a1df9714e6383f7eaebae4781
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184311"
---
# <a name="migrate-a-wcf-request-reply-service-to-a-grpc-unary-rpc"></a>WCF isteği yanıt verme hizmetini gRPC birli RPC 'ye geçirme

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Bu bölümde, WCF 'de temel bir istek-yanıt hizmetinin ASP.NET Core gRPC 'deki birli RPC hizmetine geçirilmesi ele alınmaktadır. Bu hizmetler hem Windows Communication Foundation (WCF) hem de gRPC içindeki en basit hizmet türleridir. bu nedenle başlamak için mükemmel bir yerdir. Hizmeti geçirdikten sonra, bir .NET istemci uygulamasından hizmeti kullanmak için aynı `.proto` dosyadan bir istemci kitaplığı oluşturmayı öğreneceksiniz.

## <a name="the-wcf-solution"></a>WCF çözümü

[PortfoliosSample çözümü](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/PortfoliosSample/wcf/TraderSys) , tek bir portföy veya belirli bir eğitime için tüm portföylerin indirileceği basit bir Istek-yanıt portföyü hizmeti içerir. Hizmet, arabiriminde `IPortfolioService` bir `ServiceContract` özniteliği ile tanımlanmıştır:

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

Model, `PortfolioItem` bir nesne listesi C# dahil olmak üzere [DataContract](xref:System.Runtime.Serialization.DataContractAttribute)ile işaretlenmiş basit bir sınıftır. `Portfolio` Bu modeller `TraderSys.PortfolioData` projede, veri erişimi soyutlamasını temsil eden bir depo sınıfıyla birlikte tanımlanmıştır.

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

Uygulama `ServiceContract` , `DataContract` türlerin örneklerini döndüren bağımlılık ekleme yoluyla sağlanmış bir depo sınıfı kullanır.

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

Önceki bölümde yer alan yönergeleri izlediyseniz, aşağıdakine benzer bir `portfolios.proto` dosya içeren bir GRPC projeniz olmalıdır.

```protobuf
syntax = "proto3";

option csharp_namespace = "TraderSys.Portfolios.Protos";

package PortfolioServer;

service Portfolios {
  // RPCs will go here
}
```

İlk adım, `DataContract` sınıfları prototip eşdeğerlerine geçirmeyecektir.

## <a name="convert-the-datacontracts-to-grpc-messages"></a>Veri Sözleşmelerini gRPC iletilerine Dönüştür

Sınıf, kendisine bağımlı olduğu için önce `Portfolio` bir prototipme iletisine dönüştürülür. `PortfolioItem` Sınıfı çok basittir ve özelliklerin üçü doğrudan gRPC veri türlerine eşlenir. Satın alma sırasında yapılan paylaşımlar için ödenen fiyatı temsil eden `decimal` `float`özelliğibir alandır ve `double` GRPC yalnızca para birimi için uygun olmayan gerçek sayıları destekler. `Cost` Paylaşma fiyatları, en az bir San 'a göre farklılık gösterdiğinden, maliyet, her bir `int32` ilal olarak ifade edilebilir.

> [!NOTE]
> Dosyanızdaki alan adları `camelCase` C# `PascalCase` için kullanmayı unutmayın; kod Oluşturucu bunları sizin için dönüştürecek ve diğer dillerin kullanıcıları farklı kodlama standartlarını daha da tahmin ettiğiniz için teşekkür ederiz. `.proto`

```protobuf
message PortfolioItem {
    int32 id = 1;
    int32 shareId = 2;
    int32 holding = 3;
    int32 costCents = 4;
}
```

`Portfolio` Sınıf biraz daha karmaşıktır. WCF kodunda, Geliştirici `Guid` `TraderId` özelliği için bir kullanır ve bir `List<PortfolioItem>`içerir. Birinci sınıf `UUID` türüne sahip olmayan prototipte, `traderId` alanı için bir `string` kullanmalı ve kendi kodunuzda ayrıştırmalısınız. Öğelerin listesi için alandaki `repeated` anahtar sözcüğünü kullanın.

```protobuf
message Portfolio {
    int32 id = 1;
    string traderId = 2;
    repeated PortfolioItem items = 3;
}
```

Artık veri iletilerimiz var, hizmet RPC uç noktalarını bildirebiliriz.

## <a name="convert-the-servicecontract-to-a-grpc-service"></a>ServiceContract 'i gRPC hizmetine Dönüştür

WCF `Get` yöntemi iki parametre alır: `Guid traderId` ve `int portfolioId`. gRPC hizmeti yöntemleri yalnızca tek bir parametre alabilir, bu nedenle iki değeri tutmak için bir ileti oluşturulmalıdır. Bu istek nesnelerini, yöntemiyle ve sonekiyle `Request`aynı ada sahip olacak şekilde adlandırmak yaygın bir uygulamadır. Bunun yerine, alanı`traderId` için kullanılıyor. `Guid` `string`

Hizmet yalnızca bir `Portfolio` iletiyi doğrudan döndürebilir, ancak bu, ileride geriye dönük uyumluluğu etkileyebilir. Bir hizmette bulunan her yöntem için `Request` ayrı ve `Response` iletileri tanımlamak iyi bir uygulamadır, bu nedenle, çoğu bu kadar çok aynı olsa da, tek `Portfolio` bir alan içeren bir `GetResponse` ileti bildirin.

Aşağıdaki örnek, şu `GetRequest` iletiyi kullanarak GRPC hizmeti yönteminin bildirimini gösterir:

```protobuf
message GetRequest {
    string traderId = 1;
    int32 portfolioId = 2;
}

message GetResponse {
    Portfolio portfolio = 1;
}

service Portfolios {
    rpc Get(GetRequest) returns (GetResponse);
}
```

WCF `GetAll` yöntemi yalnızca tek bir `traderId`parametre alır, bu nedenle parametre türü olarak bir belirtebilir `string` , ancak GRPC tanımlı bir ileti türü gerektirir. Bu gereksinim, ileri doğru uyumluluk için tüm girişler ve çıkışlar için özel iletiler kullanma uygulamasını zorlamaya yardımcı olur.

WCF yöntemi bir `List<Portfolio>`de döndürür, ancak basit parametre türlerine izin vermediğinden aynı nedenden dolayı GRPC, dönüş türü olarak izin vermez `repeated Portfolio` . Bunun yerine, listeyi `GetAllResponse` kaydırmak için bir tür oluşturun.

> [!WARNING]
> Bir ileti oluşturmayı veya benzer bir `PortfolioList` şekilde birden çok hizmet yöntemi arasında kullanmayı düşünebilirsiniz, ancak bu geçici yeniden ölçeklendirmelisiniz. Bir hizmette çeşitli yöntemlerin gelecekte nasıl gelişeceğimizi bilmek imkansız olabilir. bu nedenle, iletilerini belirli ve düzgün bir şekilde ayrılmış olarak tutun.

```protobuf
message GetAllRequest {
    string traderId = 1;
}

message PortfolioList {
    repeated Portfolio portfolios = 1;
}

service Portfolios {
    rpc Get(GetRequest) returns (Portfolio);
    rpc GetAll(GetAllRequest) returns (GetAllResponse);
}
```

Projenizi bu değişikliklerle kaydederseniz, gRPC derleme hedefi arka planda çalışır ve tüm Prototipsiz ileti türlerini ve hizmeti uygulamak için kalıtımla oluşturabileceğiniz bir temel sınıfı oluşturur.

`Services/GreeterService.cs` Sınıfı açın ve örnek kodu silin. Artık portföy hizmeti uygulamasını ekleyebilirsiniz. Oluşturulan temel sınıf `Protos` ad alanında olur ve iç içe yerleştirilmiş bir sınıf olarak oluşturulur. GRPC, `.proto` dosyadaki hizmetle aynı ada sahip bir statik sınıf ve ardından bu statik sınıfın içindeki sonekine `Base` sahip bir temel sınıf oluşturur. bu nedenle, temel tür için tam tanımlayıcı olur `TraderSys.Portfolios.Protos.Portfolios.PortfoliosBase`.

```csharp
namespace TraderSys.Portfolios.Services
{
    public class PortfolioService : Protos.Portfolios.PortfoliosBase
    {
    }
}
```

Temel sınıf, hizmetini `virtual` uygulamak için `Get` geçersiz `GetAll` kılınabilen ve için yöntemleri bildirir. Yöntemler `virtual` `Unimplemented` `NotImplementedException` C# yerine, bunları uygulamadıysanız, bu, normal bir kodda bir oluşturma gibi açık bir GRPC durum kodu döndürebilir. `abstract`

ASP.NET Core içindeki tüm gRPC birli hizmet yöntemleri için imza tutarlıdır. İki parametre vardır: ilki `.proto` dosyada bildirildiği ileti türüdür ve ikincisi `ServerCallContext` , `HttpContext` from ASP.NET Core benzer şekilde çalışır. Aslında, temel aldığı `GetHttpContext` `HttpContext`için kullanabileceğiniz bir genişletme yöntemi `ServerCallContext` vardır, ancak bunu sık kullanmanıza gerek kalmaz. Bu bölümde `ServerCallContext` daha sonra ve ayrıca kimlik doğrulamasını ele alan bölümde bir göz atalım.

Yöntemin dönüş türü `Task<T>` `T` , yanıt iletisi türüdür. Tüm gRPC hizmet yöntemleri zaman uyumsuzdur.

## <a name="migrate-the-portfoliodata-library-to-net-core"></a>PortfolioData kitaplığını .NET Core 'a geçirme

Bu noktada projenin, WCF çözümünde `TraderSys.PortfolioData` sınıf kitaplığında bulunan portföy deposuna ve modellerine ihtiyacı vardır. Bunu yapmanın en kolay yolu, *sınıf kitaplığı (.NET Standard)* şablonuyla Visual Studio **Yeni proje** iletişim kutusunu kullanarak veya komut .NET Core CLI satırından aşağıdaki komutları çalıştırarak yeni bir sınıf kitaplığı oluşturmaktır `TraderSys.sln` dosyasını içeren dizinden.

```dotnetcli
dotnet new classlib -o src/TraderSys.PortfolioData
dotnet sln add src/TraderSys.PortfolioData
```

Kitaplık oluşturulup çözüme eklendikten sonra, oluşturulan `Class1.cs` dosyayı silin ve dosyaları WCF çözümünün kitaplığından yeni sınıf kitaplığının klasörüne kopyalayın ve klasör yapısını saklayın.

```
Models
  Portfolio.cs
  PortfolioItem.cs
IPortfolioRepository.cs
PortfolioRepository.cs
```

Modern .NET proje dosyaları, kendi dizinine `.cs` veya bu dizinin altına herhangi bir dosyayı otomatik olarak ekler. bu nedenle, bunları projeye açıkça eklemeniz gerekmez. Kalan tek adım, `DataContract` ve `PortfolioItem` sınıflarının, ve sınıflarının `DataMember` düz eski C# sınıflar `Portfolio` olması için, özniteliklerini kaldırmasıdır.

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

Artık GRPC uygulama projesine bu kitaplığa bir başvuru ekleyebilir ve `PortfolioRepository` GRPC hizmeti uygulamasına bağımlılık ekleme kullanarak sınıfı kullanabilirsiniz. WCF uygulamasında, bağımlılık ekleme Autofac IoC kapsayıcısı tarafından sağlandı. ASP.NET Core içinde bağımlılık ekleme Depo, `ConfigureServices` `Startup` sınıfındaki yöntemine kaydedilebilir.

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

Uygulama artık `PortfolioService` sınıfında bir oluşturucu parametresi olarak belirtilebilir, şöyle olabilir: `IPortfolioRepository`

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

Artık iletilerinizi ve hizmetinizi `portfolios.proto` dosyada bildirdiğine göre, hizmet yöntemlerini `PortfolioService` GRPC tarafından oluşturulan `Portfolios.PortfoliosBase` sınıftan devralan sınıfta uygulamanız gerekir. Yöntemler, temel sınıfta olduğu `virtual` gibi bildirilmiştir. Bunları geçersiz kılamazsanız, varsayılan olarak bir gRPC "uygulanmamış" durum kodu döndürür.

`Get` Yöntemini uygulayarak başlatın. Varsayılan geçersiz kılma aşağıdaki örnekteki gibi görünür:

```csharp
public override Task<GetResponse> Get(GetRequest request, ServerCallContext context)
{
    return base.Get(request, context);
}
```

İlk sorun `request.TraderId` bir dizedir ve hizmet için `Guid`gerekir. Dize için beklenen biçim bir `UUID`olsa da, kod çağıranın geçersiz bir değer gönderdiği ve uygun şekilde yanıt verdiği olasılığa karşı uğraşmak zorunda olur. Hizmet bir `RpcException`oluşturarak hatalarla yanıt verebilir ve sorunu ifade etmek için standart `InvalidArgument` durum kodunu kullanabilir.

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

`Guid` İçin`traderId`uygun bir değer olduğunda depo, portföyü almak ve istemciye döndürmek için kullanılabilir.

```csharp
    var response = new GetResponse
    {
        Portfolio = await _repository.GetAsync(request.TraderId, request.PortfolioId)
    };
```

### <a name="map-internal-models-to-grpc-messages"></a>İç modelleri gRPC iletilerine eşleme

Önceki kod aslında çalışmıyor çünkü depo kendi poco modelini `Portfolio`döndürüyor, ancak GRPC 'nin kendi prototipli *mesajına* `Portfolio`ihtiyacı vardır. Entity Framework türlerini veri aktarım türlerine eşleme gibi, en iyi çözüm ise iki arasında dönüştürme sağlamaktır. Bu kodu, genişletilebilecek bir `partial` sınıf olarak bildirildiği prototip oluşturulan sınıfta yerleştirmek için iyi bir yerdir.

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
> Ya da `string` / [gibi alt düzey tür](https://automapper.org/) dönüştürmeleriyapılandırdığınızsürece,içmodelsınıflarındanbudönüştürmeyiprototiptürlerineişlemekiçinautomabergibibirkitaplıkkullanabilirsiniz.`decimal` `Guid` /velisteeşlemesi. `double`

Dönüştürme kodu yerine, `Get` Yöntem uygulama tamamlanabilir.

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

`GetAll` Yöntemin uygulanması benzerdir. Prototipsiz `repeated` iletilerdeki alanların `RepeatedField<T>`türünün özellikleri olarak `readonly` oluşturulduğunu, bu nedenle aşağıdaki örnekte gösterildiği gibi, `AddRange` yöntemini kullanarak bunlara öğe eklemeniz gerektiğini unutmayın:

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

WCF istek-yanıt verme hizmetini başarıyla GRPC 'ye geçirdiyseniz, bu `.proto` dosya için bir istemci oluşturmaya göz atalım.

## <a name="generate-client-code"></a>İstemci kodu oluştur

İstemcisini içermesi için aynı çözümde bir .NET Standard sınıf kitaplığı oluşturun. Bu, temelde istemci kodu oluşturma örneğidir, ancak bu tür bir kitaplığı NuGet kullanarak paketleyebilir ve diğer .NET ekiplerinin tüketmesi için bir iç depoya dağıtabilirsiniz. Devam edin ve çözüme adlı `TraderSys.Portfolios.Client` yeni bir .NET Standard sınıfı kitaplığı ekleyin ve `Class1.cs` dosyayı silin.

> [!CAUTION]
> [GRPC .net. Client](https://www.nuget.org/packages/Grpc.Net.Client) NuGet paketi .net Core 3,0 (veya başka bir .NET Standard 2,1 uyumlu çalışma zamanı) gerektirir. .NET Framework ve .NET Core 'un önceki sürümleri [GRPC. Core](https://www.nuget.org/packages/Grpc.Core) NuGet paketi tarafından desteklenir.

Visual Studio 2019 ' de, gRPC hizmetlerine benzer şekilde, Visual Studio 'nun önceki sürümlerindeki WCF projelerine hizmet başvuruları ekleme yöntemine benzer başvurular ekleyebilirsiniz. Hizmet başvuruları ve bağlı hizmetler artık aynı kullanıcı arabirimi altında yönetilir ve bu, Çözüm Gezgini `TraderSys.Portfolios.Client` projedeki **Bağımlılıklar** düğümüne sağ tıklayıp **bağlı hizmet ekle**' yi seçerek erişebilirsiniz. Görüntülenen araç penceresinde, **hizmet başvuruları** bölümünü seçin ve **Yeni GRPC hizmet başvurusu Ekle**' ye tıklayın.

![Visual Studio 2019 'de bağlı hizmetler kullanıcı arabirimi](media/migrate-request-reply/add-connected-service.png)

Projedeki dosyaya gidin, istemci olarak oluşturulacak sınıf türünü bırakın ve Tamam ' a tıklayın. `portfolios.proto` `TraderSys.Portfolios`

![Visual Studio 2019 ' de yeni gRPC hizmet başvurusu Ekle iletişim kutusu](media/migrate-request-reply/add-new-grpc-service-reference.png)

> [!TIP]
> Bu iletişim kutusunun Ayrıca bir URL alanı sağladığını unutmayın. Kuruluşunuz, Web 'de erişilebilir bir `.proto` dosya dizini tutuyorsa, bu URL adresini ayarlayarak istemcileri oluşturabilirsiniz.

Visual Studio **bağlı hizmet ekle** özelliği kullanılırken, `portfolios.proto` dosya, sınıf kitaplığı projesine kopyalanmaktansa *bağlantılı bir dosya*olarak eklenir, bu nedenle hizmet projesindeki dosyada yapılan değişiklikler otomatik olarak şu şekilde uygulanır. İstemci projesi. `csproj` Dosyadaki `<Protobuf>` öğesi şöyle görünür:

```xml
<Protobuf Include="..\TraderSys.Portfolios\Protos\portfolios.proto" GrpcServices="Client">
  <Link>Protos\portfolios.proto</Link>
</Protobuf>
```

### <a name="use-the-portfolios-service-from-a-client-application"></a>Bir istemci uygulamasından portföyde hizmetini kullanma

Aşağıdaki kod, bir konsol uygulamasında oluşturulan istemciyi kullanmayla ilgili kısa bir örnektir. GRPC istemci kodunun daha ayrıntılı bir araştırması, bu bölümün sonunda bulunur.

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

Artık temel bir WCF uygulamasını ASP.NET Core gRPC hizmetine geçirdiniz ve hizmeti bir .NET uygulamasından tüketmek üzere bir istemci oluşturdunuz. Sonraki bölümde ilgili "çift yönlü" hizmetler ele alınacaktır.

>[!div class="step-by-step"]
>[Önceki](create-project.md)
>[İleri](migrate-duplex-services.md)
