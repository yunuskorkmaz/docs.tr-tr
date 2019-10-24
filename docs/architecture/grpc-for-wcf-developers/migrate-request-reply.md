---
title: WCF geliştiricileri için bir WCF isteği-yanıt hizmetini gRPC-gRPC 'ye geçirme
description: WCF 'den gRPC 'ye basit bir istek-yanıt hizmeti geçirmeyi öğrenin.
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 183e3b0ab1ce5c63714ced064f0d0901f59819c7
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72770400"
---
# <a name="migrate-a-wcf-request-reply-service-to-a-grpc-unary-rpc"></a><span data-ttu-id="d8bc6-103">WCF isteği yanıt verme hizmetini gRPC birli RPC 'ye geçirme</span><span class="sxs-lookup"><span data-stu-id="d8bc6-103">Migrate a WCF request-reply service to a gRPC unary RPC</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="d8bc6-104">Bu bölümde, WCF 'de temel bir istek-yanıt hizmetinin ASP.NET Core gRPC 'deki birli RPC hizmetine geçirilmesi ele alınmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d8bc6-104">This section covers how to migrate a basic request-reply service in WCF to a unary RPC service in ASP.NET Core gRPC.</span></span> <span data-ttu-id="d8bc6-105">Bu hizmetler hem Windows Communication Foundation (WCF) hem de gRPC içindeki en basit hizmet türleridir. bu nedenle başlamak için mükemmel bir yerdir.</span><span class="sxs-lookup"><span data-stu-id="d8bc6-105">These services are the simplest service types in both Windows Communication Foundation (WCF) and gRPC, so it's an excellent place to start.</span></span> <span data-ttu-id="d8bc6-106">Hizmeti geçirdikten sonra, bir .NET istemci uygulamasından hizmeti kullanmak için aynı `.proto` dosyasından bir istemci kitaplığı oluşturmayı öğreneceksiniz.</span><span class="sxs-lookup"><span data-stu-id="d8bc6-106">After migrating the service, you'll learn how to generate a client library from the same `.proto` file to consume the service from a .NET client application.</span></span>

## <a name="the-wcf-solution"></a><span data-ttu-id="d8bc6-107">WCF çözümü</span><span class="sxs-lookup"><span data-stu-id="d8bc6-107">The WCF solution</span></span>

<span data-ttu-id="d8bc6-108">[PortfoliosSample çözümü](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/PortfoliosSample/wcf/TraderSys) , tek bir portföy veya belirli bir eğitime için tüm portföylerin indirileceği basit bir Istek-yanıt portföyü hizmeti içerir.</span><span class="sxs-lookup"><span data-stu-id="d8bc6-108">The [PortfoliosSample solution](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/PortfoliosSample/wcf/TraderSys) includes a simple Request-Reply Portfolio service to download a single portfolio, or all portfolios for a given Trader.</span></span> <span data-ttu-id="d8bc6-109">Hizmet, arabirim `IPortfolioService` `ServiceContract` özniteliğiyle tanımlanmıştır:</span><span class="sxs-lookup"><span data-stu-id="d8bc6-109">The service is defined in the interface `IPortfolioService` with a `ServiceContract` attribute:</span></span>

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

<span data-ttu-id="d8bc6-110">@No__t_0 modeli, `PortfolioItem` nesnelerin listesi C# dahil olmak üzere [DataContract](xref:System.Runtime.Serialization.DataContractAttribute)ile işaretlenmiş basit bir sınıftır.</span><span class="sxs-lookup"><span data-stu-id="d8bc6-110">The `Portfolio` model is a simple C# class marked with [DataContract](xref:System.Runtime.Serialization.DataContractAttribute), including a list of `PortfolioItem` objects.</span></span> <span data-ttu-id="d8bc6-111">Bu modeller `TraderSys.PortfolioData` projesinde, veri erişimi soyutlamasını temsil eden bir depo sınıfıyla birlikte tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="d8bc6-111">These models are defined in the `TraderSys.PortfolioData` project, along with a repository class representing a data access abstraction.</span></span>

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

<span data-ttu-id="d8bc6-112">@No__t_0 uygulama, `DataContract` türlerinin örneklerini döndüren bağımlılık ekleme yoluyla sağlanmış bir depo sınıfı kullanır.</span><span class="sxs-lookup"><span data-stu-id="d8bc6-112">The `ServiceContract` implementation uses a repository class provided via dependency injection that returns instances of the `DataContract` types.</span></span>

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

## <a name="the-portfoliosproto-file"></a><span data-ttu-id="d8bc6-113">Portföyler. proto dosyası</span><span class="sxs-lookup"><span data-stu-id="d8bc6-113">The portfolios.proto file</span></span>

<span data-ttu-id="d8bc6-114">Önceki bölümde yer alan yönergeleri izlediyseniz, şuna benzer bir `portfolios.proto` dosyası içeren bir gRPC projeniz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d8bc6-114">If you followed the instructions in the previous section, you should have a gRPC project with a `portfolios.proto` file that looks like this.</span></span>

```protobuf
syntax = "proto3";

option csharp_namespace = "TraderSys.Portfolios.Protos";

package PortfolioServer;

service Portfolios {
  // RPCs will go here
}
```

<span data-ttu-id="d8bc6-115">İlk adım `DataContract` sınıflarını prototip eşdeğerlerine geçirmeyecektir.</span><span class="sxs-lookup"><span data-stu-id="d8bc6-115">The first step is to migrate the `DataContract` classes to their Protobuf equivalents.</span></span>

## <a name="convert-the-datacontracts-to-grpc-messages"></a><span data-ttu-id="d8bc6-116">Veri Sözleşmelerini gRPC iletilerine Dönüştür</span><span class="sxs-lookup"><span data-stu-id="d8bc6-116">Convert the DataContracts to gRPC messages</span></span>

<span data-ttu-id="d8bc6-117">@No__t_0 sınıfı, önce bir Prototipme iletisine dönüştürülür, `Portfolio` sınıfı buna bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="d8bc6-117">The `PortfolioItem` class will be converted to a Protobuf message first, as the `Portfolio` class depends on it.</span></span> <span data-ttu-id="d8bc6-118">Sınıfı çok basittir ve özelliklerin üçü doğrudan gRPC veri türlerine eşlenir.</span><span class="sxs-lookup"><span data-stu-id="d8bc6-118">The class is very simple, and three of the properties map directly to gRPC data types.</span></span> <span data-ttu-id="d8bc6-119">Satın alma sırasında yapılan paylaşımlar için ödenen fiyatı temsil eden `Cost` özelliği, bir `decimal` alanıdır ve gRPC yalnızca gerçek sayılar için `float` veya `double` destekler, bu da para birimi için uygun değildir.</span><span class="sxs-lookup"><span data-stu-id="d8bc6-119">The `Cost` property, representing the price paid for the shares at purchase, is a `decimal` field, and gRPC only supports `float` or `double` for real numbers, which aren't suitable for currency.</span></span> <span data-ttu-id="d8bc6-120">Paylaşma fiyatları en az bir sent 'a göre farklılık gösterdiğinden, maliyet, ilal `int32` olarak ifade edilebilir.</span><span class="sxs-lookup"><span data-stu-id="d8bc6-120">Since share prices vary by a minimum of one cent, the cost can be expressed as an `int32` of cents.</span></span>

> [!NOTE]
> <span data-ttu-id="d8bc6-121">@No__t_1 dosyanızdaki alan adları için `camelCase` kullanmayı unutmayın; C# kod Oluşturucu bu dosyaları sizin için `PascalCase` dönüştürür ve diğer dillerin kullanıcıları farklı kodlama standartlarını daha da tahmin etmek için teşekkür ederiz.</span><span class="sxs-lookup"><span data-stu-id="d8bc6-121">Remember to use `camelCase` for field names in your `.proto` file; the C# code generator will convert them to `PascalCase` for you, and users of other languages will thank you for respecting their different coding standards.</span></span>

```protobuf
message PortfolioItem {
    int32 id = 1;
    int32 share_id = 2;
    int32 holding = 3;
    int32 cost_cents = 4;
}
```

<span data-ttu-id="d8bc6-122">@No__t_0 sınıfı biraz daha karmaşıktır.</span><span class="sxs-lookup"><span data-stu-id="d8bc6-122">The `Portfolio` class is a little more complicated.</span></span> <span data-ttu-id="d8bc6-123">WCF kodunda, geliştirici `TraderId` özelliği için bir `Guid` kullanıyordu ve bir `List<PortfolioItem>` içerir.</span><span class="sxs-lookup"><span data-stu-id="d8bc6-123">In the WCF code, the developer used a `Guid` for the `TraderId` property, and contains a `List<PortfolioItem>`.</span></span> <span data-ttu-id="d8bc6-124">Birinci sınıf `UUID` türüne sahip olmayan prototipte, `traderId` alanı için bir `string` kullanmalı ve kendi kodunuzda ayrıştırmalısınız.</span><span class="sxs-lookup"><span data-stu-id="d8bc6-124">In Protobuf, which doesn't have a first-class `UUID` type, you should use a `string` for the `traderId` field and parse it in your own code.</span></span> <span data-ttu-id="d8bc6-125">Öğelerin listesi için alanındaki `repeated` anahtar sözcüğünü kullanın.</span><span class="sxs-lookup"><span data-stu-id="d8bc6-125">For the list of items, use the `repeated` keyword on the field.</span></span>

```protobuf
message Portfolio {
    int32 id = 1;
    string trader_id = 2;
    repeated PortfolioItem items = 3;
}
```

<span data-ttu-id="d8bc6-126">Artık veri iletilerimiz var, hizmet RPC uç noktalarını bildirebiliriz.</span><span class="sxs-lookup"><span data-stu-id="d8bc6-126">Now we have our data messages, we can declare the service RPC endpoints.</span></span>

## <a name="convert-the-servicecontract-to-a-grpc-service"></a><span data-ttu-id="d8bc6-127">ServiceContract 'i gRPC hizmetine Dönüştür</span><span class="sxs-lookup"><span data-stu-id="d8bc6-127">Convert the ServiceContract to a gRPC service</span></span>

<span data-ttu-id="d8bc6-128">WCF `Get` yöntemi iki parametre alır: `Guid traderId` ve `int portfolioId`.</span><span class="sxs-lookup"><span data-stu-id="d8bc6-128">The WCF `Get` method takes two parameters: `Guid traderId` and `int portfolioId`.</span></span> <span data-ttu-id="d8bc6-129">gRPC hizmeti yöntemleri yalnızca tek bir parametre alabilir, bu nedenle iki değeri tutmak için bir ileti oluşturulmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d8bc6-129">gRPC service methods can only take a single parameter, so a message must be created to hold the two values.</span></span> <span data-ttu-id="d8bc6-130">Bu istek nesnelerini yöntemiyle aynı ada ve sonek `Request` adlandırmak yaygın bir uygulamadır.</span><span class="sxs-lookup"><span data-stu-id="d8bc6-130">It's common practice to name these request objects with the same name as the method and the suffix `Request`.</span></span> <span data-ttu-id="d8bc6-131">@No__t_0, `traderId` alanı için `Guid` yerine kullanılıyor.</span><span class="sxs-lookup"><span data-stu-id="d8bc6-131">Again, `string` is being used for the `traderId` field instead of `Guid`.</span></span>

<span data-ttu-id="d8bc6-132">Hizmet yalnızca `Portfolio` bir ileti döndürebilir, ancak bu, ileride geriye dönük uyumluluğu etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="d8bc6-132">The service could just return a `Portfolio` message directly, but again, this could impact backward compatibility in the future.</span></span> <span data-ttu-id="d8bc6-133">Bir hizmette bulunan her yöntem için ayrı `Request` ve `Response` iletileri tanımlamak iyi bir uygulamadır, bu nedenle tek bir `Portfolio` alanı olan `GetResponse` bir ileti bildirin.</span><span class="sxs-lookup"><span data-stu-id="d8bc6-133">It's a good practice to define separate `Request` and `Response` messages for every method in a service, even if many of them are the same right now, so declare a `GetResponse` message with a single `Portfolio` field.</span></span>

<span data-ttu-id="d8bc6-134">Aşağıdaki örnek, `GetRequest` iletisini kullanarak gRPC hizmeti yönteminin bildirimini gösterir:</span><span class="sxs-lookup"><span data-stu-id="d8bc6-134">The following example shows the declaration of the gRPC service method using the `GetRequest` message:</span></span>

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

<span data-ttu-id="d8bc6-135">WCF `GetAll` yöntemi, `traderId` yalnızca tek bir parametre alır, bu nedenle parametre türü olarak `string` belirtebilir, ancak gRPC tanımlı bir ileti türü gerektirir.</span><span class="sxs-lookup"><span data-stu-id="d8bc6-135">The WCF `GetAll` method only takes a single parameter, `traderId`, so it might seem that one could specify `string` as the parameter type, but gRPC requires a defined message type.</span></span> <span data-ttu-id="d8bc6-136">Bu gereksinim, ileri doğru uyumluluk için tüm girişler ve çıkışlar için özel iletiler kullanma uygulamasını zorlamaya yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="d8bc6-136">This requirement helps to enforce the practice of using custom messages for all inputs and outputs, for future backward compatibility.</span></span>

<span data-ttu-id="d8bc6-137">WCF Yöntemi ayrıca bir `List<Portfolio>` döndürür, ancak basit parametre türlerine izin vermediği için gRPC, dönüş türü olarak `repeated Portfolio` izin vermez.</span><span class="sxs-lookup"><span data-stu-id="d8bc6-137">The WCF method also returned a `List<Portfolio>`, but for the same reason it doesn't allow simple parameter types, gRPC won't allow `repeated Portfolio` as a return type.</span></span> <span data-ttu-id="d8bc6-138">Bunun yerine, listeyi kaydırmak için bir `GetAllResponse` türü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="d8bc6-138">Instead, create a `GetAllResponse` type to wrap the list.</span></span>

> [!WARNING]
> <span data-ttu-id="d8bc6-139">@No__t_0 bir ileti oluşturabilir veya benzer bir şekilde birden çok hizmet yöntemi genelinde kullanabilirsiniz, ancak bu geçici yeniden ölçeklendirmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="d8bc6-139">You may be tempted to create a `PortfolioList` message or similar and use it across multiple service methods, but you should resist this temptation.</span></span> <span data-ttu-id="d8bc6-140">Bir hizmette çeşitli yöntemlerin gelecekte nasıl gelişeceğimizi bilmek imkansız olabilir. bu nedenle, iletilerini belirli ve düzgün bir şekilde ayrılmış olarak tutun.</span><span class="sxs-lookup"><span data-stu-id="d8bc6-140">It's impossible to know how the various methods on a service may evolve in the future, so keep their messages specific and cleanly separated.</span></span>

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

<span data-ttu-id="d8bc6-141">Projenizi bu değişikliklerle kaydederseniz, gRPC derleme hedefi arka planda çalışır ve tüm Prototipsiz ileti türlerini ve hizmeti uygulamak için kalıtımla oluşturabileceğiniz bir temel sınıfı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d8bc6-141">If you save your project with these changes, the gRPC build target will run in the background and generate all the Protobuf message types and a base class you can inherit to implement the service.</span></span>

<span data-ttu-id="d8bc6-142">@No__t_0 sınıfını açın ve örnek kodu silin.</span><span class="sxs-lookup"><span data-stu-id="d8bc6-142">Open up the `Services/GreeterService.cs` class and delete the example code.</span></span> <span data-ttu-id="d8bc6-143">Artık portföy hizmeti uygulamasını ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d8bc6-143">Now you can add the Portfolio service implementation.</span></span> <span data-ttu-id="d8bc6-144">Oluşturulan temel sınıf `Protos` ad alanında olur ve iç içe geçmiş bir sınıf olarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="d8bc6-144">The generated base class will be in the `Protos` namespace and is generated as a nested class.</span></span> <span data-ttu-id="d8bc6-145">gRPC, `.proto` dosyasında hizmetle aynı ada sahip bir statik sınıf oluşturur ve ardından bu statik sınıfın içindeki bir temel sınıf `Base` ve bu nedenle temel tür için tam tanımlayıcı `TraderSys.Portfolios.Protos.Portfolios.PortfoliosBase` olur.</span><span class="sxs-lookup"><span data-stu-id="d8bc6-145">gRPC creates a static class with the same name as the service in the `.proto` file, and then a base class with the suffix `Base` inside that static class, so the full identifier for the base type is `TraderSys.Portfolios.Protos.Portfolios.PortfoliosBase`.</span></span>

```csharp
namespace TraderSys.Portfolios.Services
{
    public class PortfolioService : Protos.Portfolios.PortfoliosBase
    {
    }
}
```

<span data-ttu-id="d8bc6-146">Temel sınıf, hizmeti uygulamak için geçersiz kılınabilen `Get` ve `GetAll` için `virtual` Yöntemler bildirir.</span><span class="sxs-lookup"><span data-stu-id="d8bc6-146">The base class declares `virtual` methods for `Get` and `GetAll` that can be overridden to implement the service.</span></span> <span data-ttu-id="d8bc6-147">Yöntemler, `abstract` yerine `virtual`. bu sayede, hizmet, normal C# kodda bir `NotImplementedException` oluşturabilmeniz gibi açık bir grpc `Unimplemented` durum kodu döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="d8bc6-147">The methods are `virtual` rather than `abstract` so that if you don't implement them, the service can return an explicit gRPC `Unimplemented` status code, much like you might throw a `NotImplementedException` in regular C# code.</span></span>

<span data-ttu-id="d8bc6-148">ASP.NET Core içindeki tüm gRPC birli hizmet yöntemleri için imza tutarlıdır.</span><span class="sxs-lookup"><span data-stu-id="d8bc6-148">The signature for all gRPC unary service methods in ASP.NET Core is consistent.</span></span> <span data-ttu-id="d8bc6-149">İki parametre vardır: ilki `.proto` dosyasında bildirildiği ileti türüdür ve ikincisi ASP.NET Core `HttpContext` benzer şekilde çalışır `ServerCallContext`.</span><span class="sxs-lookup"><span data-stu-id="d8bc6-149">There are two parameters: the first is the message type declared in the `.proto` file, and the second is a `ServerCallContext` that works similarly to the `HttpContext` from ASP.NET Core.</span></span> <span data-ttu-id="d8bc6-150">Aslında, temel `HttpContext` almak için kullanabileceğiniz `ServerCallContext` sınıfında `GetHttpContext` adlı bir genişletme yöntemi vardır, ancak bunu sık kullanmanıza gerek kalmaz.</span><span class="sxs-lookup"><span data-stu-id="d8bc6-150">In fact, there's an extension method called `GetHttpContext` on the `ServerCallContext` class that you can use to get the underlying `HttpContext`, although you shouldn't need to use it often.</span></span> <span data-ttu-id="d8bc6-151">Bu bölümde daha sonra `ServerCallContext` ve ayrıca, kimlik doğrulamasını ele alan bölümde de bir göz atalım.</span><span class="sxs-lookup"><span data-stu-id="d8bc6-151">We'll take a look at `ServerCallContext` later in this chapter, and also in the chapter that discusses authentication.</span></span>

<span data-ttu-id="d8bc6-152">Yöntemin dönüş türü, `T` yanıt iletisi türü olan bir `Task<T>`.</span><span class="sxs-lookup"><span data-stu-id="d8bc6-152">The method's return type is a `Task<T>` where `T` is the response message type.</span></span> <span data-ttu-id="d8bc6-153">Tüm gRPC hizmet yöntemleri zaman uyumsuzdur.</span><span class="sxs-lookup"><span data-stu-id="d8bc6-153">All gRPC service methods are asynchronous.</span></span>

## <a name="migrate-the-portfoliodata-library-to-net-core"></a><span data-ttu-id="d8bc6-154">PortfolioData kitaplığını .NET Core 'a geçirme</span><span class="sxs-lookup"><span data-stu-id="d8bc6-154">Migrate the PortfolioData library to .NET Core</span></span>

<span data-ttu-id="d8bc6-155">Bu noktada, projenin, WCF çözümünde `TraderSys.PortfolioData` sınıf kitaplığında bulunan portföy deposuna ve modellerine ihtiyacı vardır.</span><span class="sxs-lookup"><span data-stu-id="d8bc6-155">At this point, the project needs the Portfolio repository and models contained in the `TraderSys.PortfolioData` class library in the WCF solution.</span></span> <span data-ttu-id="d8bc6-156">Bunu yapmanın en kolay yolu, *sınıf kitaplığı (.NET Standard)* şablonuyla Visual Studio **Yeni proje** iletişim kutusunu kullanarak veya komut .NET Core CLI satırından aşağıdaki komutları çalıştırarak yeni bir sınıf kitaplığı oluşturmaktır `TraderSys.sln` dosyasını içeren dizinden.</span><span class="sxs-lookup"><span data-stu-id="d8bc6-156">The easiest way to bring them across is to create a new class library using either the Visual Studio **New project** dialog with the *Class Library (.NET Standard)* template, or from the command line using the .NET Core CLI, running the following commands from the directory containing the `TraderSys.sln` file.</span></span>

```dotnetcli
dotnet new classlib -o src/TraderSys.PortfolioData
dotnet sln add src/TraderSys.PortfolioData
```

<span data-ttu-id="d8bc6-157">Kitaplık oluşturulup çözüme eklendikten sonra, oluşturulan `Class1.cs` dosyasını silin ve dosyaları WCF çözümünün kitaplığından yeni sınıf kitaplığının klasörüne kopyalayın ve klasör yapısını saklayın.</span><span class="sxs-lookup"><span data-stu-id="d8bc6-157">Once the library has been created and added to the solution, delete the generated `Class1.cs` file and copy the files from the WCF solution's library into the new class library's folder, keeping the folder structure.</span></span>

```
Models
  Portfolio.cs
  PortfolioItem.cs
IPortfolioRepository.cs
PortfolioRepository.cs
```

<span data-ttu-id="d8bc6-158">SDK stili .NET projeleri otomatik olarak kendi dizinine veya altına `.cs` dosyaları dahil eder, bu nedenle bunları projeye açıkça eklemeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="d8bc6-158">SDK-style .NET projects automatically include any `.cs` files in or under their own directory, so there's no need to explicitly add them to the project.</span></span> <span data-ttu-id="d8bc6-159">Kalan tek adım, `DataContract` ve `DataMember` özniteliklerinin `Portfolio` ve `PortfolioItem` sınıflarının salt eski C# sınıflar olması için kaldırmasıdır.</span><span class="sxs-lookup"><span data-stu-id="d8bc6-159">The only step remaining is to remove the `DataContract` and `DataMember` attributes from the `Portfolio` and `PortfolioItem` classes so they're plain old C# classes.</span></span>

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

## <a name="use-aspnet-core-dependency-injection"></a><span data-ttu-id="d8bc6-160">ASP.NET Core bağımlılığı ekleme kullanma</span><span class="sxs-lookup"><span data-stu-id="d8bc6-160">Use ASP.NET Core dependency injection</span></span>

<span data-ttu-id="d8bc6-161">Artık gRPC uygulama projesine bu kitaplığa bir başvuru ekleyebilir ve gRPC hizmeti uygulamasına bağımlılık ekleme işlemini kullanarak `PortfolioRepository` sınıfını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d8bc6-161">Now you can add a reference to this library to the gRPC application project and consume the `PortfolioRepository` class using dependency injection in the gRPC service implementation.</span></span> <span data-ttu-id="d8bc6-162">WCF uygulamasında, bağımlılık ekleme Autofac IoC kapsayıcısı tarafından sağlandı.</span><span class="sxs-lookup"><span data-stu-id="d8bc6-162">In the WCF application, dependency injection was provided by the Autofac IoC container.</span></span> <span data-ttu-id="d8bc6-163">ASP.NET Core içinde bağımlılık ekleme Depo, `Startup` sınıfındaki `ConfigureServices` yöntemine kaydedilebilir.</span><span class="sxs-lookup"><span data-stu-id="d8bc6-163">ASP.NET Core has dependency injection baked in; the repository can be registered in the `ConfigureServices` method in the `Startup` class.</span></span>

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

<span data-ttu-id="d8bc6-164">@No__t_0 uygulama artık aşağıdaki gibi `PortfolioService` sınıfında bir oluşturucu parametresi olarak belirtilebilir:</span><span class="sxs-lookup"><span data-stu-id="d8bc6-164">The `IPortfolioRepository` implementation can now be specified as a constructor parameter in the `PortfolioService` class, as follows:</span></span>

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

## <a name="implement-the-grpc-service"></a><span data-ttu-id="d8bc6-165">GRPC hizmetini uygulama</span><span class="sxs-lookup"><span data-stu-id="d8bc6-165">Implement the gRPC service</span></span>

<span data-ttu-id="d8bc6-166">İletilerinizi ve hizmetinizi `portfolios.proto` dosyasında bildirdiğine göre, hizmet yöntemlerini gRPC tarafından oluşturulan `Portfolios.PortfoliosBase` sınıfından devralan `PortfolioService` sınıfında uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="d8bc6-166">Now that you've declared your messages and your service in the `portfolios.proto` file, you have to implement the service methods in the `PortfolioService` class that inherits from the gRPC-generated `Portfolios.PortfoliosBase` class.</span></span> <span data-ttu-id="d8bc6-167">Yöntemler, temel sınıfta `virtual` olarak bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="d8bc6-167">The methods are declared as `virtual` in the base class.</span></span> <span data-ttu-id="d8bc6-168">Bunları geçersiz kılamazsanız, varsayılan olarak bir gRPC "uygulanmamış" durum kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="d8bc6-168">If you don't override them, they'll return a gRPC "Not Implemented" status code by default.</span></span>

<span data-ttu-id="d8bc6-169">@No__t_0 yöntemi uygulayarak başlayın.</span><span class="sxs-lookup"><span data-stu-id="d8bc6-169">Start by implementing the `Get` method.</span></span> <span data-ttu-id="d8bc6-170">Varsayılan geçersiz kılma aşağıdaki örnekteki gibi görünür:</span><span class="sxs-lookup"><span data-stu-id="d8bc6-170">The default override looks like the following example:</span></span>

```csharp
public override Task<GetResponse> Get(GetRequest request, ServerCallContext context)
{
    return base.Get(request, context);
}
```

<span data-ttu-id="d8bc6-171">İlk sorun `request.TraderId` bir dizedir ve hizmet bir `Guid` gerektirir.</span><span class="sxs-lookup"><span data-stu-id="d8bc6-171">The first issue is that `request.TraderId` is a string, and the service requires a `Guid`.</span></span> <span data-ttu-id="d8bc6-172">Dize için beklenen biçim bir `UUID` olsa da, kod çağıranın geçersiz bir değer gönderdiği ve uygun şekilde yanıt verdiği olasılığa karşı uğraşmak zorunda olur.</span><span class="sxs-lookup"><span data-stu-id="d8bc6-172">Even though the expected format for the string is a `UUID`, the code has to deal with the possibility that a caller has sent an invalid value and respond appropriately.</span></span> <span data-ttu-id="d8bc6-173">Hizmet bir `RpcException` vererek hatalarla yanıt verebilir ve sorunu ifade etmek için standart `InvalidArgument` durum kodunu kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="d8bc6-173">The service can respond with errors by throwing an `RpcException`, and use the standard `InvalidArgument` status code to express the problem.</span></span>

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

<span data-ttu-id="d8bc6-174">@No__t_1 için uygun bir `Guid` değeri olduktan sonra, depo, portföyü almak ve istemciye döndürmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d8bc6-174">Once there's a proper `Guid` value for `traderId`, the repository can be used to retrieve the Portfolio and return it to the client.</span></span>

```csharp
    var response = new GetResponse
    {
        Portfolio = await _repository.GetAsync(request.TraderId, request.PortfolioId)
    };
```

### <a name="map-internal-models-to-grpc-messages"></a><span data-ttu-id="d8bc6-175">İç modelleri gRPC iletilerine eşleme</span><span class="sxs-lookup"><span data-stu-id="d8bc6-175">Map internal models to gRPC messages</span></span>

<span data-ttu-id="d8bc6-176">Depo kendi POCO model `Portfolio` döndürürken, ancak gRPC 'nin kendi prototipli ileti *`Portfolio` ihtiyacı olduğundan* , önceki kod aslında çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="d8bc6-176">The previous code doesn't actually work because the repository is returning its own POCO model `Portfolio`, but gRPC needs *its* own Protobuf message `Portfolio`.</span></span> <span data-ttu-id="d8bc6-177">Entity Framework türlerini veri aktarım türlerine eşleme gibi, en iyi çözüm ise iki arasında dönüştürme sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="d8bc6-177">Much like mapping Entity Framework types to data transfer types, the best solution is to provide conversion between the two.</span></span> <span data-ttu-id="d8bc6-178">Bu kodu, genişletilebilecek bir `partial` sınıfı olarak belirtilen Prototipsiz oluşturulan sınıfta yerleştirmek için iyi bir yerdir.</span><span class="sxs-lookup"><span data-stu-id="d8bc6-178">A good place to put the code for this is in the Protobuf-generated class, which is declared as a `partial` class so it can be extended.</span></span>

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
> <span data-ttu-id="d8bc6-179">@No__t_1 / `Guid` veya `decimal` / `double` ve liste eşlemesi gibi alt düzey tür dönüştürmelerini yapılandırdığınız sürece, iç model sınıflarından bu dönüştürmeyi prototip türlerine işlemek için [Automaber](https://automapper.org/) gibi bir kitaplık kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d8bc6-179">You could use a library like [AutoMapper](https://automapper.org/) to handle this conversion from internal model classes to Protobuf types, as long as you configure the lower-level type conversions like `string`/`Guid` or `decimal`/`double` and the list mapping.</span></span>

<span data-ttu-id="d8bc6-180">Dönüştürme kodu yerine, `Get` yöntemi uygulama tamamlanabilir.</span><span class="sxs-lookup"><span data-stu-id="d8bc6-180">With the conversion code in place, the `Get` method implementation can be completed.</span></span>

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

<span data-ttu-id="d8bc6-181">@No__t_0 yönteminin uygulanması benzerdir.</span><span class="sxs-lookup"><span data-stu-id="d8bc6-181">The implementation of the `GetAll` method is similar.</span></span> <span data-ttu-id="d8bc6-182">Prototipteki iletilerde `repeated` alanları `RepeatedField<T>` türünde `readonly` özellikler olarak oluşturulduğunu ve bu nedenle, aşağıdaki örnekte olduğu gibi `AddRange` yöntemini kullanarak bunlara öğe eklemeniz gerektiğini unutmayın:</span><span class="sxs-lookup"><span data-stu-id="d8bc6-182">Note that the `repeated` fields on Protobuf messages are generated as `readonly` properties of type `RepeatedField<T>`, so you have to add items to them using the `AddRange` method, like in the following example:</span></span>

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

<span data-ttu-id="d8bc6-183">WCF istek-yanıt hizmetini başarıyla gRPC 'ye geçirdiyseniz, `.proto` dosyasından bir istemci oluşturmaya bakalım.</span><span class="sxs-lookup"><span data-stu-id="d8bc6-183">Having successfully migrated the WCF request-reply service to gRPC, let's look at creating a client for it from the `.proto` file.</span></span>

## <a name="generate-client-code"></a><span data-ttu-id="d8bc6-184">İstemci kodu oluştur</span><span class="sxs-lookup"><span data-stu-id="d8bc6-184">Generate client code</span></span>

<span data-ttu-id="d8bc6-185">İstemcisini içermesi için aynı çözümde bir .NET Standard sınıf kitaplığı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="d8bc6-185">Create a .NET Standard class library in the same solution to contain the client.</span></span> <span data-ttu-id="d8bc6-186">Bu, temelde istemci kodu oluşturma örneğidir, ancak bu tür bir kitaplığı NuGet kullanarak paketleyebilir ve diğer .NET ekiplerinin tüketmesi için bir iç depoya dağıtabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d8bc6-186">This is primarily an example of creating client code, but you could package such a library using NuGet and distribute it on an internal repository for other .NET teams to consume.</span></span> <span data-ttu-id="d8bc6-187">Devam edin ve çözüme `TraderSys.Portfolios.Client` adlı yeni bir .NET Standard sınıf kitaplığı ekleyin ve `Class1.cs` dosyasını silin.</span><span class="sxs-lookup"><span data-stu-id="d8bc6-187">Go ahead and add a new .NET Standard Class Library called `TraderSys.Portfolios.Client` to the solution and delete the `Class1.cs` file.</span></span>

> [!CAUTION]
> <span data-ttu-id="d8bc6-188">[GRPC .net. Client](https://www.nuget.org/packages/Grpc.Net.Client) NuGet paketi .net Core 3,0 (veya başka bir .NET Standard 2,1 uyumlu çalışma zamanı) gerektirir.</span><span class="sxs-lookup"><span data-stu-id="d8bc6-188">The [Grpc.Net.Client](https://www.nuget.org/packages/Grpc.Net.Client) NuGet package requires .NET Core 3.0 (or another .NET Standard 2.1-compliant runtime).</span></span> <span data-ttu-id="d8bc6-189">.NET Framework ve .NET Core 'un önceki sürümleri [GRPC. Core](https://www.nuget.org/packages/Grpc.Core) NuGet paketi tarafından desteklenir.</span><span class="sxs-lookup"><span data-stu-id="d8bc6-189">Earlier versions of .NET Framework and .NET Core are supported by the [Grpc.Core](https://www.nuget.org/packages/Grpc.Core) NuGet package.</span></span>

<span data-ttu-id="d8bc6-190">Visual Studio 2019 ' de, gRPC hizmetlerine benzer şekilde, Visual Studio 'nun önceki sürümlerindeki WCF projelerine hizmet başvuruları ekleme yöntemine benzer başvurular ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d8bc6-190">In Visual Studio 2019, you can add references to gRPC services similar to the way you'd add Service References to WCF projects in earlier versions of Visual Studio.</span></span> <span data-ttu-id="d8bc6-191">Hizmet başvuruları ve bağlı hizmetler artık aynı kullanıcı arabirimi altında yönetilir ve bu, Çözüm Gezgini `TraderSys.Portfolios.Client` projesindeki **Bağımlılıklar** düğümüne sağ tıklayıp **bağlı hizmet ekle**' yi seçerek erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d8bc6-191">Service References and Connected Services are all managed under the same UI now, which you can access by right-clicking the **Dependencies** node in the `TraderSys.Portfolios.Client` project in Solution Explorer and selecting **Add Connected Service**.</span></span> <span data-ttu-id="d8bc6-192">Görüntülenen araç penceresinde, **hizmet başvuruları** bölümünü seçin ve **Yeni GRPC hizmet başvurusu Ekle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d8bc6-192">In the tool window that appears, select the **Service References** section and click **Add new gRPC service reference**.</span></span>

![Visual Studio 2019 'de bağlı hizmetler kullanıcı arabirimi](media/migrate-request-reply/add-connected-service.png)

<span data-ttu-id="d8bc6-194">@No__t_1 projesindeki `portfolios.proto` dosyasına gidin, **istemci**olarak **oluşturulacak sınıf türünü** bırakın ve **Tamam**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d8bc6-194">Browse to the `portfolios.proto` file in the `TraderSys.Portfolios` project, leave the **type of class to be generated** as **Client**, and click **OK**.</span></span>

![Visual Studio 2019 ' de yeni gRPC hizmet başvurusu Ekle iletişim kutusu](media/migrate-request-reply/add-new-grpc-service-reference.png)

> [!TIP]
> <span data-ttu-id="d8bc6-196">Bu iletişim kutusunun Ayrıca bir URL alanı sağladığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="d8bc6-196">Notice that this dialog also provides a URL field.</span></span> <span data-ttu-id="d8bc6-197">Kuruluşunuz, `.proto` dosyaları için Web erişimli bir dizin koruyorsa, bu URL adresini ayarlayarak istemcileri oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d8bc6-197">If your organization maintains a web-accessible directory of `.proto` files, you can create clients just by setting this URL address.</span></span>

<span data-ttu-id="d8bc6-198">Visual Studio **bağlı hizmet ekle** özelliği kullanılırken, `portfolios.proto` dosyası, kopyalamak yerine *bağlantılı bir dosya*olarak sınıf kitaplığı projesine eklenir, bu nedenle hizmet projesindeki dosyada yapılan değişiklikler istemciye otomatik olarak uygulanır. Proje.</span><span class="sxs-lookup"><span data-stu-id="d8bc6-198">When using the Visual Studio **Add Connected Service** feature, the `portfolios.proto` file is added to the Class Library project as a *linked file*, rather than copied, so changes to the file in the service project will automatically be applied in the client project.</span></span> <span data-ttu-id="d8bc6-199">@No__t_1 dosyasındaki `<Protobuf>` öğesi şöyle görünür:</span><span class="sxs-lookup"><span data-stu-id="d8bc6-199">The `<Protobuf>` element in the `csproj` file looks like this:</span></span>

```xml
<Protobuf Include="..\TraderSys.Portfolios\Protos\portfolios.proto" GrpcServices="Client">
  <Link>Protos\portfolios.proto</Link>
</Protobuf>
```

> [!TIP]
> <span data-ttu-id="d8bc6-200">Visual Studio kullanmıyorsanız veya komut satırından çalışmayı tercih ediyorsanız, bir .NET gRPC projesi içindeki prototipsel başvuruları yönetmek için **DotNet-GRPC** genel aracını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d8bc6-200">If you are not using Visual Studio or prefer to work from the command line, you can use the **dotnet-grpc** global tool to manage Protobuf references within a .NET gRPC project.</span></span> <span data-ttu-id="d8bc6-201">[Daha fazla bilgi için **DotNet-GRPC** belgelerine bakın](https://docs.microsoft.com/aspnet/core/grpc/dotnet-grpc).</span><span class="sxs-lookup"><span data-stu-id="d8bc6-201">[Refer to the **dotnet-grpc** documentation for more information](https://docs.microsoft.com/aspnet/core/grpc/dotnet-grpc).</span></span>

### <a name="use-the-portfolios-service-from-a-client-application"></a><span data-ttu-id="d8bc6-202">Bir istemci uygulamasından portföyde hizmetini kullanma</span><span class="sxs-lookup"><span data-stu-id="d8bc6-202">Use the Portfolios service from a client application</span></span>

<span data-ttu-id="d8bc6-203">Aşağıdaki kod, bir konsol uygulamasında oluşturulan istemciyi kullanmayla ilgili kısa bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="d8bc6-203">The following code is a brief example of using the generated client in a console application.</span></span> <span data-ttu-id="d8bc6-204">GRPC istemci kodunun daha ayrıntılı bir araştırması, bu bölümün sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="d8bc6-204">A more detailed exploration of the gRPC client code is at the end of this chapter.</span></span>

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

<span data-ttu-id="d8bc6-205">Artık temel bir WCF uygulamasını ASP.NET Core gRPC hizmetine geçirdiniz ve hizmeti bir .NET uygulamasından tüketmek üzere bir istemci oluşturdunuz.</span><span class="sxs-lookup"><span data-stu-id="d8bc6-205">Now, you've migrated a basic WCF application to an ASP.NET Core gRPC service and created a client to consume the service from a .NET application.</span></span> <span data-ttu-id="d8bc6-206">Sonraki bölümde ilgili "çift yönlü" hizmetler ele alınacaktır.</span><span class="sxs-lookup"><span data-stu-id="d8bc6-206">The next section will cover the more involved "duplex" services.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="d8bc6-207">[Önceki](create-project.md)
>[İleri](migrate-duplex-services.md)</span><span class="sxs-lookup"><span data-stu-id="d8bc6-207">[Previous](create-project.md)
[Next](migrate-duplex-services.md)</span></span>
