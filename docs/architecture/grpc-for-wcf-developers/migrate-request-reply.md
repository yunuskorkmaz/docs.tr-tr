---
title: WCF geliştiricileri için bir WCF isteği-yanıt hizmetini gRPC-gRPC 'ye geçirme
description: WCF 'den gRPC 'ye basit bir istek-yanıt hizmeti geçirmeyi öğrenin.
ms.date: 09/02/2019
ms.openlocfilehash: 018aa94a15cdcb1e0f559afb7b3a88cd4f915398
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628559"
---
# <a name="migrate-a-wcf-request-reply-service-to-a-grpc-unary-rpc"></a><span data-ttu-id="82875-103">WCF isteği yanıt verme hizmetini gRPC birli RPC 'ye geçirme</span><span class="sxs-lookup"><span data-stu-id="82875-103">Migrate a WCF request-reply service to a gRPC unary RPC</span></span>

<span data-ttu-id="82875-104">Bu bölümde, WCF 'de temel bir istek-yanıt hizmetinin ASP.NET Core gRPC 'deki birli RPC hizmetine geçirilmesi ele alınmaktadır.</span><span class="sxs-lookup"><span data-stu-id="82875-104">This section covers how to migrate a basic request-reply service in WCF to a unary RPC service in ASP.NET Core gRPC.</span></span> <span data-ttu-id="82875-105">Bu hizmetler hem Windows Communication Foundation (WCF) hem de gRPC içindeki en basit hizmet türleridir. bu nedenle başlamak için mükemmel bir yerdir.</span><span class="sxs-lookup"><span data-stu-id="82875-105">These services are the simplest service types in both Windows Communication Foundation (WCF) and gRPC, so it's an excellent place to start.</span></span> <span data-ttu-id="82875-106">Hizmeti geçirdikten sonra, bir .NET istemci uygulamasından hizmeti kullanmak için aynı `.proto` dosyasından bir istemci kitaplığı oluşturmayı öğreneceksiniz.</span><span class="sxs-lookup"><span data-stu-id="82875-106">After migrating the service, you'll learn how to generate a client library from the same `.proto` file to consume the service from a .NET client application.</span></span>

## <a name="the-wcf-solution"></a><span data-ttu-id="82875-107">WCF çözümü</span><span class="sxs-lookup"><span data-stu-id="82875-107">The WCF solution</span></span>

<span data-ttu-id="82875-108">[PortfoliosSample çözümü](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/PortfoliosSample/wcf/TraderSys) , belirli bir eğitime için tek bir portföy ya da tüm portföyleri indirmek üzere basit bir istek-yanıt portföyü hizmeti içerir.</span><span class="sxs-lookup"><span data-stu-id="82875-108">The [PortfoliosSample solution](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/PortfoliosSample/wcf/TraderSys) includes a simple request-reply Portfolio service to download either a single portfolio or all portfolios for a given trader.</span></span> <span data-ttu-id="82875-109">Hizmet, arabirim `IPortfolioService` `ServiceContract` özniteliğiyle tanımlanmıştır:</span><span class="sxs-lookup"><span data-stu-id="82875-109">The service is defined in the interface `IPortfolioService` with a `ServiceContract` attribute:</span></span>

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

<span data-ttu-id="82875-110">`Portfolio` modeli, [DataContract](xref:System.Runtime.Serialization.DataContractAttribute) ile işaretlenmiş C# ve `PortfolioItem` nesnelerinin bir listesini içeren basit bir sınıftır.</span><span class="sxs-lookup"><span data-stu-id="82875-110">The `Portfolio` model is a simple C# class marked with [DataContract](xref:System.Runtime.Serialization.DataContractAttribute) and including a list of `PortfolioItem` objects.</span></span> <span data-ttu-id="82875-111">Bu modeller `TraderSys.PortfolioData` projesinde, bir veri erişimi soyutlamasını temsil eden bir depo sınıfıyla birlikte tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="82875-111">These models are defined in the `TraderSys.PortfolioData` project along with a repository class that represents a data access abstraction.</span></span>

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

<span data-ttu-id="82875-112">`ServiceContract` uygulama, `DataContract` türlerinin örneklerini döndüren bağımlılık ekleme yoluyla sağlanmış bir depo sınıfı kullanır:</span><span class="sxs-lookup"><span data-stu-id="82875-112">The `ServiceContract` implementation uses a repository class provided via dependency injection that returns instances of the `DataContract` types:</span></span>

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

## <a name="the-portfoliosproto-file"></a><span data-ttu-id="82875-113">Portföyler. proto dosyası</span><span class="sxs-lookup"><span data-stu-id="82875-113">The portfolios.proto file</span></span>

<span data-ttu-id="82875-114">Önceki bölümde yer alan yönergeleri izlediyseniz, şuna benzer bir `portfolios.proto` dosyası içeren bir gRPC projeniz olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="82875-114">If you followed the instructions in the previous section, you should have a gRPC project with a `portfolios.proto` file that looks like this:</span></span>

```protobuf
syntax = "proto3";

option csharp_namespace = "TraderSys.Portfolios.Protos";

package PortfolioServer;

service Portfolios {
  // RPCs will go here
}
```

<span data-ttu-id="82875-115">İlk adım `DataContract` sınıflarını prototip eşdeğerlerine geçirmeyecektir.</span><span class="sxs-lookup"><span data-stu-id="82875-115">The first step is to migrate the `DataContract` classes to their Protobuf equivalents.</span></span>

## <a name="convert-the-datacontract-classes-to-grpc-messages"></a><span data-ttu-id="82875-116">DataContract sınıflarını gRPC iletilerine Dönüştür</span><span class="sxs-lookup"><span data-stu-id="82875-116">Convert the DataContract classes to gRPC messages</span></span>

<span data-ttu-id="82875-117">`PortfolioItem` sınıfı ilk olarak bir Prototipme iletisine dönüştürülür, çünkü `Portfolio` sınıfı buna bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="82875-117">The `PortfolioItem` class will be converted to a Protobuf message first, because the `Portfolio` class depends on it.</span></span> <span data-ttu-id="82875-118">Sınıfı basittir ve özelliklerden üçü doğrudan gRPC veri türlerine eşlenir.</span><span class="sxs-lookup"><span data-stu-id="82875-118">The class is simple, and three of the properties map directly to gRPC data types.</span></span> <span data-ttu-id="82875-119">Satın alımlardaki paylaşımlar için ödenen fiyatı temsil eden `Cost` özelliği bir `decimal` alanıdır.</span><span class="sxs-lookup"><span data-stu-id="82875-119">The `Cost` property, which represents the price paid for the shares at purchase, is a `decimal` field.</span></span> <span data-ttu-id="82875-120">gRPC yalnızca `float` veya `double`, para birimi için uygun olmayan gerçek numaralar için destekler.</span><span class="sxs-lookup"><span data-stu-id="82875-120">gRPC supports only `float` or `double` for real numbers, which aren't suitable for currency.</span></span> <span data-ttu-id="82875-121">Paylaşma fiyatları en az bir sent 'a göre farklılık gösterdiğinden, maliyet, ilal `int32` olarak ifade edilebilir.</span><span class="sxs-lookup"><span data-stu-id="82875-121">Because share prices vary by a minimum of one cent, the cost can be expressed as an `int32` of cents.</span></span>

> [!NOTE]
> <span data-ttu-id="82875-122">`.proto` dosyanızdaki alan adları için camelCase kullanmayı unutmayın.</span><span class="sxs-lookup"><span data-stu-id="82875-122">Remember to use camelCase for field names in your `.proto` file.</span></span> <span data-ttu-id="82875-123">C# Kod Oluşturucu, sizin Için PascalCase 'e dönüştürecek ve diğer dillerin kullanıcıları farklı kodlama standartlarını daha iyi bir şekilde tahmin ettiğiniz için teşekkür eder.</span><span class="sxs-lookup"><span data-stu-id="82875-123">The C# code generator will convert them to PascalCase for you, and users of other languages will thank you for respecting their different coding standards.</span></span>

```protobuf
message PortfolioItem {
    int32 id = 1;
    int32 share_id = 2;
    int32 holding = 3;
    int32 cost_cents = 4;
}
```

<span data-ttu-id="82875-124">`Portfolio` sınıfı biraz daha karmaşıktır.</span><span class="sxs-lookup"><span data-stu-id="82875-124">The `Portfolio` class is a little more complicated.</span></span> <span data-ttu-id="82875-125">WCF kodunda, geliştirici `TraderId` özelliği için bir `Guid` kullanıyordu ve bir `List<PortfolioItem>`içerir.</span><span class="sxs-lookup"><span data-stu-id="82875-125">In the WCF code, the developer used a `Guid` for the `TraderId` property, and contains a `List<PortfolioItem>`.</span></span> <span data-ttu-id="82875-126">Birinci sınıf `UUID` türüne sahip olmayan prototipte, `traderId` alanı için bir `string` kullanmalı ve kendi kodunuzda ayrıştırmalısınız.</span><span class="sxs-lookup"><span data-stu-id="82875-126">In Protobuf, which doesn't have a first-class `UUID` type, you should use a `string` for the `traderId` field and parse it in your own code.</span></span> <span data-ttu-id="82875-127">Öğelerin listesi için alanındaki `repeated` anahtar sözcüğünü kullanın.</span><span class="sxs-lookup"><span data-stu-id="82875-127">For the list of items, use the `repeated` keyword on the field.</span></span>

```protobuf
message Portfolio {
    int32 id = 1;
    string trader_id = 2;
    repeated PortfolioItem items = 3;
}
```

<span data-ttu-id="82875-128">Artık veri iletilerine sahip olduğunuza göre, hizmet RPC uç noktalarını bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="82875-128">Now that you have the data messages, you can declare the service RPC endpoints.</span></span>

## <a name="convert-servicecontract-to-a-grpc-service"></a><span data-ttu-id="82875-129">ServiceContract 'i gRPC hizmetine dönüştürme</span><span class="sxs-lookup"><span data-stu-id="82875-129">Convert ServiceContract to a gRPC service</span></span>

<span data-ttu-id="82875-130">WCF `Get` yöntemi iki parametre alır: `Guid traderId` ve `int portfolioId`.</span><span class="sxs-lookup"><span data-stu-id="82875-130">The WCF `Get` method takes two parameters: `Guid traderId` and `int portfolioId`.</span></span> <span data-ttu-id="82875-131">gRPC hizmeti yöntemleri yalnızca tek bir parametre alabilir, bu nedenle iki değeri tutacak bir ileti oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="82875-131">gRPC service methods can take only a single parameter, so you need to create a message to hold the two values.</span></span> <span data-ttu-id="82875-132">Bu istek nesnelerini, ardından sonek `Request`ile aynı ada sahip olacak şekilde adlandırmak yaygın bir uygulamadır.</span><span class="sxs-lookup"><span data-stu-id="82875-132">It's common practice to name these request objects with the same name as the method followed by the suffix `Request`.</span></span> <span data-ttu-id="82875-133">`string`, `traderId` alanı için `Guid`yerine kullanılıyor.</span><span class="sxs-lookup"><span data-stu-id="82875-133">Again, `string` is being used for the `traderId` field instead of `Guid`.</span></span>

<span data-ttu-id="82875-134">Hizmet yalnızca `Portfolio` bir ileti döndürebilir, ancak bu, gelecekte geriye dönük uyumluluğu etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="82875-134">The service could just return a `Portfolio` message directly, but again, this could affect backward compatibility in the future.</span></span> <span data-ttu-id="82875-135">Bir hizmette bulunan her yöntem için ayrı `Request` ve `Response` iletileri tanımlamak iyi bir uygulamadır. Bu, çoğu durumda aynı anda aynı olsa bile.</span><span class="sxs-lookup"><span data-stu-id="82875-135">It's a good practice to define separate `Request` and `Response` messages for every method in a service, even if many of them are the same right now.</span></span> <span data-ttu-id="82875-136">Bu nedenle, tek bir `Portfolio` alanla `GetResponse` bir ileti bildirin.</span><span class="sxs-lookup"><span data-stu-id="82875-136">So declare a `GetResponse` message with a single `Portfolio` field.</span></span>

<span data-ttu-id="82875-137">Bu örnek, `GetRequest` iletisiyle gRPC hizmeti yönteminin bildirimini gösterir:</span><span class="sxs-lookup"><span data-stu-id="82875-137">This example shows the declaration of the gRPC service method with the `GetRequest` message:</span></span>

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

<span data-ttu-id="82875-138">WCF `GetAll` yöntemi, `traderId`yalnızca tek bir parametre alır, bu yüzden parametre türü olarak `string` belirtebileceğiniz görünebilir.</span><span class="sxs-lookup"><span data-stu-id="82875-138">The WCF `GetAll` method takes only a single parameter, `traderId`, so it might seem that you could specify `string` as the parameter type.</span></span> <span data-ttu-id="82875-139">Ancak gRPC tanımlı bir ileti türü gerektirir.</span><span class="sxs-lookup"><span data-stu-id="82875-139">But gRPC requires a defined message type.</span></span> <span data-ttu-id="82875-140">Bu gereksinim, ileri doğru uyumluluk için tüm girişler ve çıkışlar için özel iletiler kullanma uygulamasını zorlamaya yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="82875-140">This requirement helps to enforce the practice of using custom messages for all inputs and outputs, for future backward compatibility.</span></span>

<span data-ttu-id="82875-141">WCF Yöntemi ayrıca bir `List<Portfolio>`döndürür, ancak basit parametre türlerine izin vermediği için gRPC, dönüş türü olarak `repeated Portfolio` izin vermez.</span><span class="sxs-lookup"><span data-stu-id="82875-141">The WCF method also returns a `List<Portfolio>`, but for the same reason it doesn't allow simple parameter types, gRPC won't allow `repeated Portfolio` as a return type.</span></span> <span data-ttu-id="82875-142">Bunun yerine, listeyi kaydırmak için bir `GetAllResponse` türü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="82875-142">Instead, create a `GetAllResponse` type to wrap the list.</span></span>

> [!WARNING]
> <span data-ttu-id="82875-143">`PortfolioList` bir ileti veya benzer bir durum oluşturabilir ve bunu birden çok hizmet yöntemi genelinde kullanabilirsiniz, ancak bu geçici yeniden ölçeklendirmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="82875-143">You might be tempted to create a `PortfolioList` message or something similar and use it across multiple service methods, but you should resist this temptation.</span></span> <span data-ttu-id="82875-144">Bir hizmette çeşitli yöntemlerin nasıl gelişeceğimizi bilmek olanaksızdır, bu sayede iletilerini özel ve düzgün bir şekilde ayrılmış olarak tutun.</span><span class="sxs-lookup"><span data-stu-id="82875-144">It's impossible to know how the various methods on a service will evolve, so keep their messages specific and cleanly separated.</span></span>

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

<span data-ttu-id="82875-145">Projenizi bu değişikliklerle kaydederseniz, gRPC derleme hedefi arka planda çalışır ve tüm prototip ileti türlerini ve hizmeti uygulamak için kalıtımla oluşturabileceğiniz bir temel sınıfı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="82875-145">If you save your project with these changes, the gRPC build target will run in the background and generate all the Protobuf message types and a base class that you can inherit to implement the service.</span></span>

<span data-ttu-id="82875-146">`Services/GreeterService.cs` sınıfını açın ve örnek kodu silin.</span><span class="sxs-lookup"><span data-stu-id="82875-146">Open the `Services/GreeterService.cs` class and delete the example code.</span></span> <span data-ttu-id="82875-147">Artık portföy hizmeti uygulamasını ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="82875-147">Now you can add the Portfolio service implementation.</span></span> <span data-ttu-id="82875-148">Oluşturulan temel sınıf `Protos` ad alanında olur ve iç içe geçmiş bir sınıf olarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="82875-148">The generated base class will be in the `Protos` namespace and is generated as a nested class.</span></span> <span data-ttu-id="82875-149">gRPC, `.proto` dosyasında hizmetle aynı ada sahip bir statik sınıf ve bu statik sınıfın içinde `Base` sonekine sahip bir temel sınıf oluşturur. bu nedenle, temel tür için tam tanımlayıcı `TraderSys.Portfolios.Protos.Portfolios.PortfoliosBase`olur.</span><span class="sxs-lookup"><span data-stu-id="82875-149">gRPC creates a static class with the same name as the service in the `.proto` file and a base class with the suffix `Base` inside that static class, so the full identifier for the base type is `TraderSys.Portfolios.Protos.Portfolios.PortfoliosBase`.</span></span>

```csharp
namespace TraderSys.Portfolios.Services
{
    public class PortfolioService : Protos.Portfolios.PortfoliosBase
    {
    }
}
```

<span data-ttu-id="82875-150">Temel sınıf, hizmeti uygulamak için geçersiz kılınabilen `Get` ve `GetAll` için `virtual` Yöntemler bildirir.</span><span class="sxs-lookup"><span data-stu-id="82875-150">The base class declares `virtual` methods for `Get` and `GetAll` that can be overridden to implement the service.</span></span> <span data-ttu-id="82875-151">Yöntemler, `abstract` yerine `virtual`. bu sayede, hizmet, normal C# kodda bir `NotImplementedException` oluşturabilmeniz gibi açık bir grpc `Unimplemented` durum kodu döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="82875-151">The methods are `virtual` rather than `abstract` so that if you don't implement them, the service can return an explicit gRPC `Unimplemented` status code, much like you might throw a `NotImplementedException` in regular C# code.</span></span>

<span data-ttu-id="82875-152">ASP.NET Core içindeki tüm gRPC birli hizmet yöntemleri için imza tutarlıdır.</span><span class="sxs-lookup"><span data-stu-id="82875-152">The signature for all gRPC unary service methods in ASP.NET Core is consistent.</span></span> <span data-ttu-id="82875-153">İki parametre vardır: ilki `.proto` dosyasında bildirildiği ileti türüdür ve ikincisi ASP.NET Core `HttpContext` benzer şekilde çalışır `ServerCallContext`.</span><span class="sxs-lookup"><span data-stu-id="82875-153">There are two parameters: the first is the message type declared in the `.proto` file, and the second is a `ServerCallContext` that works similarly to the `HttpContext` from ASP.NET Core.</span></span> <span data-ttu-id="82875-154">Aslında, temel `HttpContext`almak için kullanabileceğiniz `ServerCallContext` sınıfında `GetHttpContext` adlı bir genişletme yöntemi vardır, ancak bunu sık kullanmanıza gerek kalmaz.</span><span class="sxs-lookup"><span data-stu-id="82875-154">In fact, there's an extension method called `GetHttpContext` on the `ServerCallContext` class that you can use to get the underlying `HttpContext`, although you shouldn't need to use it often.</span></span> <span data-ttu-id="82875-155">Bu bölümde daha sonra `ServerCallContext` ve ayrıca, kimlik doğrulamasını ele alan bölümde de bir göz atalım.</span><span class="sxs-lookup"><span data-stu-id="82875-155">We'll take a look at `ServerCallContext` later in this chapter, and also in the chapter that discusses authentication.</span></span>

<span data-ttu-id="82875-156">Yöntemin dönüş türü bir `Task<T>`, burada `T` yanıt iletisi türüdür.</span><span class="sxs-lookup"><span data-stu-id="82875-156">The method's return type is a `Task<T>`, where `T` is the response message type.</span></span> <span data-ttu-id="82875-157">Tüm gRPC hizmet yöntemleri zaman uyumsuzdur.</span><span class="sxs-lookup"><span data-stu-id="82875-157">All gRPC service methods are asynchronous.</span></span>

## <a name="migrate-the-portfoliodata-library-to-net-core"></a><span data-ttu-id="82875-158">PortfolioData kitaplığını .NET Core 'a geçirme</span><span class="sxs-lookup"><span data-stu-id="82875-158">Migrate the PortfolioData library to .NET Core</span></span>

<span data-ttu-id="82875-159">Bu noktada, projenin, WCF çözümünde `TraderSys.PortfolioData` sınıf kitaplığında bulunan portföy deposuna ve modellerine ihtiyacı vardır.</span><span class="sxs-lookup"><span data-stu-id="82875-159">At this point, the project needs the Portfolio repository and models contained in the `TraderSys.PortfolioData` class library in the WCF solution.</span></span> <span data-ttu-id="82875-160">Bunu yapmanın en kolay yolu, sınıf kitaplığı (.NET Standard) şablonuyla Visual Studio **Yeni proje** iletişim kutusunu kullanarak ya da .NET Core CLI kullanarak komut satırından, `TraderSys.sln` dosyasını içeren dizinden bu komutları çalıştırarak yeni bir sınıf kitaplığı oluşturmaktır:</span><span class="sxs-lookup"><span data-stu-id="82875-160">The easiest way to bring them across is to create a new class library by using either the Visual Studio **New project** dialog box with the Class Library (.NET Standard) template, or from the command line by using the .NET Core CLI, running these commands from the directory that contains the `TraderSys.sln` file:</span></span>

```dotnetcli
dotnet new classlib -o src/TraderSys.PortfolioData
dotnet sln add src/TraderSys.PortfolioData
```

<span data-ttu-id="82875-161">Kitaplığı oluşturup çözüme ekledikten sonra, oluşturulan `Class1.cs` dosyasını silin ve dosyaları WCF çözümünün kitaplığından yeni sınıf kitaplığının klasörüne kopyalayın ve klasör yapısını saklayın:</span><span class="sxs-lookup"><span data-stu-id="82875-161">After you've created the library and added it to the solution, delete the generated `Class1.cs` file and copy the files from the WCF solution's library into the new class library's folder, keeping the folder structure:</span></span>

```
Models
  Portfolio.cs
  PortfolioItem.cs
IPortfolioRepository.cs
PortfolioRepository.cs
```

<span data-ttu-id="82875-162">SDK stili .NET projeleri otomatik olarak kendi dizinine veya altına `.cs` dosyaları dahil eder, bu nedenle bunları projeye açıkça eklemeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="82875-162">SDK-style .NET projects automatically include any `.cs` files in or under their own directory, so you don't need to explicitly add them to the project.</span></span> <span data-ttu-id="82875-163">Kalan tek adım, `DataContract` ve `DataMember` özniteliklerinin `Portfolio` ve `PortfolioItem` sınıflarının salt eski C# sınıflar olması için kaldırmasıdır:</span><span class="sxs-lookup"><span data-stu-id="82875-163">The only step remaining is to remove the `DataContract` and `DataMember` attributes from the `Portfolio` and `PortfolioItem` classes so they're plain old C# classes:</span></span>

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

## <a name="use-aspnet-core-dependency-injection"></a><span data-ttu-id="82875-164">ASP.NET Core bağımlılığı ekleme kullanma</span><span class="sxs-lookup"><span data-stu-id="82875-164">Use ASP.NET Core dependency injection</span></span>

<span data-ttu-id="82875-165">Artık gRPC uygulama projesine bu kitaplığa bir başvuru ekleyebilir ve gRPC hizmeti uygulamasına bağımlılık ekleme işlemini kullanarak `PortfolioRepository` sınıfını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="82875-165">Now you can add a reference to this library to the gRPC application project and consume the `PortfolioRepository` class by using dependency injection in the gRPC service implementation.</span></span> <span data-ttu-id="82875-166">WCF uygulamasında, bağımlılık ekleme Autofac IoC kapsayıcısı tarafından sağlandı.</span><span class="sxs-lookup"><span data-stu-id="82875-166">In the WCF application, dependency injection was provided by the Autofac IoC container.</span></span> <span data-ttu-id="82875-167">ASP.NET Core içinde bağımlılık ekleme ' ye sahiptir.</span><span class="sxs-lookup"><span data-stu-id="82875-167">ASP.NET Core has dependency injection baked in.</span></span> <span data-ttu-id="82875-168">Depoyu `Startup` sınıfındaki `ConfigureServices` yöntemine kaydedebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="82875-168">You can register the repository in the `ConfigureServices` method in the `Startup` class:</span></span>

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

<span data-ttu-id="82875-169">`IPortfolioRepository` uygulama artık aşağıdaki gibi `PortfolioService` sınıfında bir oluşturucu parametresi olarak belirtilebilir:</span><span class="sxs-lookup"><span data-stu-id="82875-169">The `IPortfolioRepository` implementation can now be specified as a constructor parameter in the `PortfolioService` class, as follows:</span></span>

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

## <a name="implement-the-grpc-service"></a><span data-ttu-id="82875-170">GRPC hizmetini uygulama</span><span class="sxs-lookup"><span data-stu-id="82875-170">Implement the gRPC service</span></span>

<span data-ttu-id="82875-171">İletilerinizi ve hizmetinizi `portfolios.proto` dosyasında bildirdiğine göre, hizmet yöntemlerini gRPC tarafından oluşturulan `Portfolios.PortfoliosBase` sınıfından devralan `PortfolioService` sınıfında uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="82875-171">Now that you've declared your messages and your service in the `portfolios.proto` file, you have to implement the service methods in the `PortfolioService` class that inherits from the gRPC-generated `Portfolios.PortfoliosBase` class.</span></span> <span data-ttu-id="82875-172">Yöntemler, temel sınıfta `virtual` olarak bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="82875-172">The methods are declared as `virtual` in the base class.</span></span> <span data-ttu-id="82875-173">Bunları geçersiz kılamazsanız, varsayılan olarak bir gRPC "uygulanmamış" durum kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="82875-173">If you don't override them, they'll return a gRPC "Not Implemented" status code by default.</span></span>

<span data-ttu-id="82875-174">`Get` yöntemi uygulayarak başlayın.</span><span class="sxs-lookup"><span data-stu-id="82875-174">Start by implementing the `Get` method.</span></span> <span data-ttu-id="82875-175">Varsayılan geçersiz kılma Şu örneğe benzer şekilde görünür:</span><span class="sxs-lookup"><span data-stu-id="82875-175">The default override looks like this example:</span></span>

```csharp
public override Task<GetResponse> Get(GetRequest request, ServerCallContext context)
{
    return base.Get(request, context);
}
```

<span data-ttu-id="82875-176">İlk sorun `request.TraderId` bir dizedir ve hizmet bir `Guid`gerektirir.</span><span class="sxs-lookup"><span data-stu-id="82875-176">The first problem is that `request.TraderId` is a string, and the service requires a `Guid`.</span></span> <span data-ttu-id="82875-177">Dize için beklenen biçim `UUID`olsa da, kod çağıranın geçersiz bir değer gönderdiği ve uygun şekilde yanıt verdiği olasılığa karşı uğraşmak zorunda olur.</span><span class="sxs-lookup"><span data-stu-id="82875-177">Even though the expected format for the string is `UUID`, the code has to deal with the possibility that a caller has sent an invalid value and respond appropriately.</span></span> <span data-ttu-id="82875-178">Hizmet, `RpcException` oluşturarak ve sorunu ifade etmek için standart `InvalidArgument` durum kodunu kullanarak hatalarla yanıt verebilir:</span><span class="sxs-lookup"><span data-stu-id="82875-178">The service can respond with errors by throwing an `RpcException` and use the standard `InvalidArgument` status code to express the problem:</span></span>

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

<span data-ttu-id="82875-179">`traderId`için uygun bir `Guid` değeri olduktan sonra, portföyü almak ve istemciye döndürmek için depoyu kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="82875-179">After there's a proper `Guid` value for `traderId`, you can use the repository to retrieve the Portfolio and return it to the client:</span></span>

```csharp
    var response = new GetResponse
    {
        Portfolio = await _repository.GetAsync(request.TraderId, request.PortfolioId)
    };
```

### <a name="map-internal-models-to-grpc-messages"></a><span data-ttu-id="82875-180">İç modelleri gRPC iletilerine eşleme</span><span class="sxs-lookup"><span data-stu-id="82875-180">Map internal models to gRPC messages</span></span>

<span data-ttu-id="82875-181">Depo kendi POCO model `Portfolio`döndürürken, ancak gRPC 'nin kendi prototipli ileti `Portfolio`ihtiyacı olduğundan, önceki kod aslında çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="82875-181">The previous code doesn't actually work because the repository is returning its own POCO model `Portfolio`, but gRPC needs its own Protobuf message `Portfolio`.</span></span> <span data-ttu-id="82875-182">Entity Framework türlerini veri aktarım türleriyle eşleştirdiğinizde, en iyi çözüm iki arasında dönüştürme sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="82875-182">As when you map Entity Framework types to data transfer types, the best solution is to provide a conversion between the two.</span></span> <span data-ttu-id="82875-183">Bu dönüştürme için kodu yerleştirmek için iyi bir yer, `partial` sınıf olarak belirtilen Prototipsiz oluşturulan sınıfta yer alabilir ve bu nedenle Genişletilebilir:</span><span class="sxs-lookup"><span data-stu-id="82875-183">A good place to put the code for this conversion is in the Protobuf-generated class, which is declared as a `partial` class so it can be extended:</span></span>

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
> <span data-ttu-id="82875-184">`string`/`Guid` veya `decimal`/`double` ve liste eşlemesi gibi alt düzey tür dönüştürmelerini yapılandırdığınız sürece, iç model sınıflarından bu dönüştürmeyi prototip türlerine işlemek için [Automaber](https://automapper.org/) gibi bir kitaplık kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="82875-184">You could use a library like [AutoMapper](https://automapper.org/) to handle this conversion from internal model classes to Protobuf types, as long as you configure the lower-level type conversions like `string`/`Guid` or `decimal`/`double` and the list mapping.</span></span>

<span data-ttu-id="82875-185">Artık dönüştürme koduna sahip olduğunuza göre `Get` yöntemi uygulamasını tamamlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="82875-185">Now that you have the conversion code in place, you can complete the `Get` method implementation:</span></span>

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

<span data-ttu-id="82875-186">`GetAll` yönteminin uygulanması benzerdir.</span><span class="sxs-lookup"><span data-stu-id="82875-186">The implementation of the `GetAll` method is similar.</span></span> <span data-ttu-id="82875-187">Prototipteki iletilerde `repeated` alanlarının `RepeatedField<T>`türünde `readonly` özellikler olarak oluşturulduğunu unutmayın, bu nedenle, bu örnekte olduğu gibi `AddRange` yöntemini kullanarak bunlara öğe eklemeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="82875-187">Note that the `repeated` fields on Protobuf messages are generated as `readonly` properties of type `RepeatedField<T>`, so you have to add items to them by using the `AddRange` method, like in this example:</span></span>

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

<span data-ttu-id="82875-188">WCF istek-yanıt hizmetini başarıyla gRPC 'ye geçirdiyseniz, `.proto` dosyasından bir istemci oluşturmaya bakalım.</span><span class="sxs-lookup"><span data-stu-id="82875-188">Having successfully migrated the WCF request-reply service to gRPC, let's look at creating a client for it from the `.proto` file.</span></span>

## <a name="generate-client-code"></a><span data-ttu-id="82875-189">İstemci kodu oluştur</span><span class="sxs-lookup"><span data-stu-id="82875-189">Generate client code</span></span>

<span data-ttu-id="82875-190">İstemcisini içermesi için aynı çözümde bir .NET Standard sınıf kitaplığı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="82875-190">Create a .NET Standard class library in the same solution to contain the client.</span></span> <span data-ttu-id="82875-191">Bu öncelikle istemci kodu oluşturma örneğidir, ancak bu tür bir kitaplığı NuGet kullanarak paketleyebilir ve diğer .NET ekibinin kullanması için bir iç depoya dağıtabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="82875-191">This is primarily an example of creating client code, but you could package such a library by using NuGet and distribute it on an internal repository for other .NET teams to consume.</span></span> <span data-ttu-id="82875-192">Devam edin ve çözüme `TraderSys.Portfolios.Client` adlı yeni bir .NET Standard sınıf kitaplığı ekleyin ve `Class1.cs` dosyasını silin.</span><span class="sxs-lookup"><span data-stu-id="82875-192">Go ahead and add a new .NET Standard class library called `TraderSys.Portfolios.Client` to the solution and delete the `Class1.cs` file.</span></span>

> [!CAUTION]
> <span data-ttu-id="82875-193">[GRPC .net. Client](https://www.nuget.org/packages/Grpc.Net.Client) NuGet paketi .net Core 3,0 (veya başka bir .NET Standard 2,1 uyumlu çalışma zamanı) gerektirir.</span><span class="sxs-lookup"><span data-stu-id="82875-193">The [Grpc.Net.Client](https://www.nuget.org/packages/Grpc.Net.Client) NuGet package requires .NET Core 3.0 (or another .NET Standard 2.1-compliant runtime).</span></span> <span data-ttu-id="82875-194">.NET Framework ve .NET Core 'un önceki sürümleri [GRPC. Core](https://www.nuget.org/packages/Grpc.Core) NuGet paketi tarafından desteklenir.</span><span class="sxs-lookup"><span data-stu-id="82875-194">Earlier versions of .NET Framework and .NET Core are supported by the [Grpc.Core](https://www.nuget.org/packages/Grpc.Core) NuGet package.</span></span>

<span data-ttu-id="82875-195">Visual Studio 2019 ' de, Visual Studio 'nun önceki sürümlerindeki WCF projelerine hizmet başvuruları ekleme yöntemine benzer bir şekilde gRPC hizmetlerine başvurular ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="82875-195">In Visual Studio 2019, you can add references to gRPC services in a way that's similar to how you'd add service references to WCF projects in earlier versions of Visual Studio.</span></span> <span data-ttu-id="82875-196">Hizmet başvuruları ve bağlı hizmetler artık aynı kullanıcı arabirimi altında yönetilir.</span><span class="sxs-lookup"><span data-stu-id="82875-196">Service references and connected services are all managed under the same UI now.</span></span> <span data-ttu-id="82875-197">Çözüm Gezgini ' de `TraderSys.Portfolios.Client` projesindeki **Bağımlılıklar** düğümüne sağ tıklayıp **bağlı hizmet ekle**' yi seçerek kullanıcı arabirimine erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="82875-197">You can access the UI by right-clicking the **Dependencies** node in the `TraderSys.Portfolios.Client` project in Solution Explorer and selecting **Add Connected Service**.</span></span> <span data-ttu-id="82875-198">Görüntülenen araç penceresinde, **hizmet başvuruları** bölümünü seçin ve ardından **Yeni GRPC hizmet başvurusu Ekle**' yi seçin:</span><span class="sxs-lookup"><span data-stu-id="82875-198">In the tool window that appears, select the **Service References** section and then select **Add new gRPC service reference**:</span></span>

![Visual Studio 2019 'de bağlı hizmetler kullanıcı arabirimi](media/migrate-request-reply/add-connected-service.png)

<span data-ttu-id="82875-200">`TraderSys.Portfolios` projesindeki `portfolios.proto` dosyasına gidin, **istemciye** , **oluşturulacak sınıf türünü seçin**altında bırakın ve **Tamam**' ı seçin:</span><span class="sxs-lookup"><span data-stu-id="82875-200">Browse to the `portfolios.proto` file in the `TraderSys.Portfolios` project, leave **Client** under **Select the type of class to be generated**, and then select **OK**:</span></span>

![Visual Studio 2019 ' de yeni gRPC hizmet başvurusu Ekle iletişim kutusu](media/migrate-request-reply/add-new-grpc-service-reference.png)

> [!TIP]
> <span data-ttu-id="82875-202">Bu iletişim kutusunun Ayrıca bir URL alanı sağladığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="82875-202">Notice that this dialog box also provides a URL field.</span></span> <span data-ttu-id="82875-203">Kuruluşunuz, `.proto` dosyaları için Web erişimli bir dizin koruyorsa, bu URL adresini ayarlayarak istemcileri oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="82875-203">If your organization maintains a web-accessible directory of `.proto` files, you can create clients just by setting this URL address.</span></span>

<span data-ttu-id="82875-204">Visual Studio **bağlı hizmet ekle** özelliğini kullandığınızda `portfolios.proto` dosyası, kopyalamak yerine *bağlantılı bir dosya* olarak sınıf kitaplığı projesine eklenir, bu nedenle hizmet projesindeki dosyada yapılan değişiklikler istemci projesinde otomatik olarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="82875-204">When you use the Visual Studio **Add Connected Service** feature, the `portfolios.proto` file is added to the class library project as a *linked file* rather than copied, so changes to the file in the service project will automatically be applied in the client project.</span></span> <span data-ttu-id="82875-205">`csproj` dosyasındaki `<Protobuf>` öğesi şöyle görünür:</span><span class="sxs-lookup"><span data-stu-id="82875-205">The `<Protobuf>` element in the `csproj` file looks like this:</span></span>

```xml
<Protobuf Include="..\TraderSys.Portfolios\Protos\portfolios.proto" GrpcServices="Client">
  <Link>Protos\portfolios.proto</Link>
</Protobuf>
```

> [!TIP]
> <span data-ttu-id="82875-206">Visual Studio 'Yu kullanmıyorsanız veya komut satırından çalışmayı tercih ediyorsanız, bir .NET gRPC projesindeki prototipsel başvuruları yönetmek için `dotnet-grpc` genel aracını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="82875-206">If you're not using Visual Studio or prefer to work from the command line, you can use the `dotnet-grpc` global tool to manage Protobuf references in a .NET gRPC project.</span></span> <span data-ttu-id="82875-207">Daha fazla bilgi için [`dotnet-grpc` belgelerine](/aspnet/core/grpc/dotnet-grpc)bakın.</span><span class="sxs-lookup"><span data-stu-id="82875-207">For more information, see the [`dotnet-grpc` documentation](/aspnet/core/grpc/dotnet-grpc).</span></span>

### <a name="use-the-portfolios-service-from-a-client-application"></a><span data-ttu-id="82875-208">Bir istemci uygulamasından portföyde hizmetini kullanma</span><span class="sxs-lookup"><span data-stu-id="82875-208">Use the Portfolios service from a client application</span></span>

<span data-ttu-id="82875-209">Aşağıdaki kod, bir konsol uygulamasında oluşturulan istemciyi nasıl kullanacağınızı gösteren kısa bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="82875-209">The following code is a brief example of how to use the generated client in a console application.</span></span> <span data-ttu-id="82875-210">GRPC istemci kodunun daha ayrıntılı bir araştırması, bu bölümün sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="82875-210">A more detailed exploration of the gRPC client code is at the end of this chapter.</span></span>

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

<span data-ttu-id="82875-211">Artık temel bir WCF uygulamasını ASP.NET Core gRPC hizmetine geçirdiniz ve hizmeti bir .NET uygulamasından tüketmek için bir istemci oluşturdunuz.</span><span class="sxs-lookup"><span data-stu-id="82875-211">You've now migrated a basic WCF application to an ASP.NET Core gRPC service and created a client to consume the service from a .NET application.</span></span> <span data-ttu-id="82875-212">Sonraki bölümde, ilgili çift yönlü hizmetler ele alınacaktır.</span><span class="sxs-lookup"><span data-stu-id="82875-212">The next section will cover the more involved duplex services.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="82875-213">[Önceki](create-project.md)
>[İleri](migrate-duplex-services.md)</span><span class="sxs-lookup"><span data-stu-id="82875-213">[Previous](create-project.md)
[Next](migrate-duplex-services.md)</span></span>
