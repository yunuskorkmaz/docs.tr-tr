---
title: Protobuf mesajları - WCF geliştiricileri için gRPC
description: Protobuf iletilerinin IDL'de nasıl tanımlandığını ve C#'da nasıl oluşturulduğunu öğrenin.
ms.date: 09/09/2019
ms.openlocfilehash: 5b3d4383de39a3785ef804fec21939a740f54669
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79147990"
---
# <a name="protobuf-messages"></a><span data-ttu-id="c8c25-103">Protobuf iletileri</span><span class="sxs-lookup"><span data-stu-id="c8c25-103">Protobuf messages</span></span>

<span data-ttu-id="c8c25-104">Bu bölümde, dosyalarda `.proto` Protokol Arabelleği (Protobuf) iletilerinin nasıl beyan edilebildiğini kapsar.</span><span class="sxs-lookup"><span data-stu-id="c8c25-104">This section covers how to declare Protocol Buffer (Protobuf) messages in `.proto` files.</span></span> <span data-ttu-id="c8c25-105">Alan sayıları ve türlerinin temel kavramlarını açıklar ve `protoc` derleyicinin oluşturduğu C# koduna bakar.</span><span class="sxs-lookup"><span data-stu-id="c8c25-105">It explains the fundamental concepts of field numbers and types, and it looks at the C# code that the `protoc` compiler generates.</span></span>

<span data-ttu-id="c8c25-106">Bölümün geri kalanı, Farklı veri türlerinin Protobuf'ta nasıl temsil edildiğine daha ayrıntılı olarak bakacaktır.</span><span class="sxs-lookup"><span data-stu-id="c8c25-106">The rest of the chapter will look in more detail at how different types of data are represented in Protobuf.</span></span>

## <a name="declaring-a-message"></a><span data-ttu-id="c8c25-107">İleti bildirme</span><span class="sxs-lookup"><span data-stu-id="c8c25-107">Declaring a message</span></span>

<span data-ttu-id="c8c25-108">Windows Communication Foundation'da (WCF) bir borsa işlem uygulaması `Stock` sınıfı aşağıdaki örnek gibi tanımlanabilir:</span><span class="sxs-lookup"><span data-stu-id="c8c25-108">In Windows Communication Foundation (WCF), a `Stock` class for a stock market trading application might be defined like the following example:</span></span>

```csharp
namespace TraderSys
{
    [DataContract]
    public class Stock
    {
        [DataMember]
        public int Id { get; set;}
        [DataMember]
        public string Symbol { get; set;}
        [DataMember]
        public string DisplayName { get; set;}
        [DataMember]
        public int MarketId { get; set; }
    }
}
```

<span data-ttu-id="c8c25-109">Protobuf'ta eşdeğer sınıfı uygulamak için dosyada `.proto` beyan etmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="c8c25-109">To implement the equivalent class in Protobuf, you must declare it in the `.proto` file.</span></span> <span data-ttu-id="c8c25-110">Derleyici `protoc` daha sonra yapı işleminin bir parçası olarak .NET sınıfını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c8c25-110">The `protoc` compiler will then generate the .NET class as part of the build process.</span></span>

```protobuf
syntax "proto3";

option csharp_namespace = "TraderSys";

message Stock {

    int32 id = 1;
    string symbol = 2;
    string display_name = 3;
    int32 market_id = 4;

}  
```

<span data-ttu-id="c8c25-111">İlk satır, kullanılan sözdizimi sürümünü bildirir.</span><span class="sxs-lookup"><span data-stu-id="c8c25-111">The first line declares the syntax version being used.</span></span> <span data-ttu-id="c8c25-112">Dilin 3 sürümü 2016 yılında piyasaya sürüldü.</span><span class="sxs-lookup"><span data-stu-id="c8c25-112">Version 3 of the language was released in 2016.</span></span> <span data-ttu-id="c8c25-113">GRPC hizmetleri için önerdiğimiz sürümdür.</span><span class="sxs-lookup"><span data-stu-id="c8c25-113">It's the version that we recommend for gRPC services.</span></span>

<span data-ttu-id="c8c25-114">Satır, `option csharp_namespace` oluşturulan C# türleri için kullanılacak ad alanını belirtir.</span><span class="sxs-lookup"><span data-stu-id="c8c25-114">The `option csharp_namespace` line specifies the namespace to be used for the generated C# types.</span></span> <span data-ttu-id="c8c25-115">`.proto` Dosya diğer diller için derlendiğinde bu seçenek yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="c8c25-115">This option will be ignored when the `.proto` file is compiled for other languages.</span></span> <span data-ttu-id="c8c25-116">Protobuf dosyaları genellikle birkaç dil için dile özgü seçenekler içerir.</span><span class="sxs-lookup"><span data-stu-id="c8c25-116">Protobuf files often contain language-specific options for several languages.</span></span>

<span data-ttu-id="c8c25-117">İleti `Stock` tanımı dört alan belirtir.</span><span class="sxs-lookup"><span data-stu-id="c8c25-117">The `Stock` message definition specifies four fields.</span></span> <span data-ttu-id="c8c25-118">Her birinin bir türü, adı ve bir alan numarası vardır.</span><span class="sxs-lookup"><span data-stu-id="c8c25-118">Each has a type, a name, and a field number.</span></span>

## <a name="field-numbers"></a><span data-ttu-id="c8c25-119">Alan numaraları</span><span class="sxs-lookup"><span data-stu-id="c8c25-119">Field numbers</span></span>

<span data-ttu-id="c8c25-120">Alan numaraları Protobuf önemli bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="c8c25-120">Field numbers are an important part of Protobuf.</span></span> <span data-ttu-id="c8c25-121">İkili kodlanmış verilerdeki alanları tanımlamak için kullanılırlar, bu da hizmetin sürümünden sürümüne değiştirilemeyecekleri anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="c8c25-121">They're used to identify fields in the binary encoded data, which means they can't change from version to version of your service.</span></span> <span data-ttu-id="c8c25-122">Avantajı geriye dönük uyumluluk ve ileri uyumluluk mümkün olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="c8c25-122">The advantage is that backward compatibility and forward compatibility are possible.</span></span> <span data-ttu-id="c8c25-123">İstemciler ve hizmetler, eksik değerler olasılığı işlendiği sürece, bilmedikleri alan numaralarını yok sayacaktır.</span><span class="sxs-lookup"><span data-stu-id="c8c25-123">Clients and services will simply ignore field numbers that they don't know about, as long as the possibility of missing values is handled.</span></span>

<span data-ttu-id="c8c25-124">İkili biçimde, alan numarası bir tür tanımlayıcısı ile birleştirilir.</span><span class="sxs-lookup"><span data-stu-id="c8c25-124">In the binary format, the field number is combined with a type identifier.</span></span> <span data-ttu-id="c8c25-125">1'den 15'e kadar alan numaraları, tek bir bayt olarak kendi türüyle kodlanabilir.</span><span class="sxs-lookup"><span data-stu-id="c8c25-125">Field numbers from 1 to 15 can be encoded with their type as a single byte.</span></span> <span data-ttu-id="c8c25-126">16 ile 2,047 arası sayılar 2 bayt alır.</span><span class="sxs-lookup"><span data-stu-id="c8c25-126">Numbers from 16 to 2,047 take 2 bytes.</span></span> <span data-ttu-id="c8c25-127">Herhangi bir nedenle bir iletide 2.047'den fazla alana ihtiyacınız varsa daha yükseğe çıkabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c8c25-127">You can go higher if you need more than 2,047 fields on a message for any reason.</span></span> <span data-ttu-id="c8c25-128">1 ile 15 arasında alan numaraları için tek bayt tanımlayıcıları daha iyi performans sunar, bu nedenle bunları en temel, en sık kullanılan alanlar için kullanmalısınız.</span><span class="sxs-lookup"><span data-stu-id="c8c25-128">The single byte identifiers for field numbers 1 to 15 offer better performance, so you should use them for the most basic, frequently used fields.</span></span>

## <a name="types"></a><span data-ttu-id="c8c25-129">Türler</span><span class="sxs-lookup"><span data-stu-id="c8c25-129">Types</span></span>

<span data-ttu-id="c8c25-130">Tür bildirimleri, [bir sonraki bölümde](protobuf-data-types.md)daha ayrıntılı olarak tartışılan Protobuf'un yerel skaler veri türlerini kullanıyor.</span><span class="sxs-lookup"><span data-stu-id="c8c25-130">The type declarations are using Protobuf's native scalar data types, which are discussed in more detail in [the next section](protobuf-data-types.md).</span></span> <span data-ttu-id="c8c25-131">Bu bölümün geri kalanı Protobuf'un yerleşik türlerini kapsayacak ve bunların ortak .NET türleri ile nasıl ilişkili olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="c8c25-131">The rest of this chapter will cover Protobuf's built-in types and show how they relate to common .NET types.</span></span>

> [!NOTE]
> <span data-ttu-id="c8c25-132">Protobuf yerel olarak bir `decimal` türü desteklemez, bu nedenle `double` bunun yerine kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c8c25-132">Protobuf doesn't natively support a `decimal` type, so `double` is used instead.</span></span> <span data-ttu-id="c8c25-133">Tam ondalık kesinlik gerektiren uygulamalar için, bu bölümün bir sonraki bölümünde [ondalık sayılar bölümüne](protobuf-data-types.md#decimals) bakın.</span><span class="sxs-lookup"><span data-stu-id="c8c25-133">For applications that require full decimal precision, refer to the [section on decimals](protobuf-data-types.md#decimals) in the next part of this chapter.</span></span>

## <a name="the-generated-code"></a><span data-ttu-id="c8c25-134">Oluşturulan kod</span><span class="sxs-lookup"><span data-stu-id="c8c25-134">The generated code</span></span>

<span data-ttu-id="c8c25-135">Uygulamanızı oluşturduğunuzda, Protobuf iletilerinizin her biri için sınıflar oluşturur ve yerel türlerini C# türleri ile eşler.</span><span class="sxs-lookup"><span data-stu-id="c8c25-135">When you build your application, Protobuf creates classes for each of your messages, mapping its native types to C# types.</span></span> <span data-ttu-id="c8c25-136">Oluşturulan `Stock` tür aşağıdaki imzaya sahip olacaktır:</span><span class="sxs-lookup"><span data-stu-id="c8c25-136">The generated `Stock` type would have the following signature:</span></span>

```csharp
public class Stock
{
    public int Id { get; set; }
    public string Symbol { get; set; }
    public string DisplayName { get; set; }
    public int MarketId { get; set; }
}
```

<span data-ttu-id="c8c25-137">Oluşturulan gerçek kod bundan çok daha karmaşıktır.</span><span class="sxs-lookup"><span data-stu-id="c8c25-137">The actual code that's generated is far more complicated than this.</span></span> <span data-ttu-id="c8c25-138">Bunun nedeni, her sınıfın kendisini ikili tel biçimine seri hale getirmek ve deserialize etmek için gereken tüm kodu içermesidir.</span><span class="sxs-lookup"><span data-stu-id="c8c25-138">The reason is that each class contains all the code necessary to serialize and deserialize itself to the binary wire format.</span></span>

### <a name="property-names"></a><span data-ttu-id="c8c25-139">Özellik adları</span><span class="sxs-lookup"><span data-stu-id="c8c25-139">Property names</span></span>

<span data-ttu-id="c8c25-140">Protobuf derleyicisinin dosyada olmalarına `PascalCase` `snake_case` rağmen özellik adlarına uygulandığını `.proto` unutmayın.</span><span class="sxs-lookup"><span data-stu-id="c8c25-140">Note that the Protobuf compiler applied `PascalCase` to the property names, although they were `snake_case` in the `.proto` file.</span></span> <span data-ttu-id="c8c25-141">[Protobuf stil kılavuzu,](https://developers.google.com/protocol-buffers/docs/style) `snake_case` diğer platformlar için kod oluşturmanın kendi kuralları için beklenen örneği üretecek şekilde ileti tanımlarınızda kullanılmasını önerir.</span><span class="sxs-lookup"><span data-stu-id="c8c25-141">The [Protobuf style guide](https://developers.google.com/protocol-buffers/docs/style) recommends using `snake_case` in your message definitions so that the code generation for other platforms produces the expected case for their conventions.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="c8c25-142">[Önceki](protocol-buffers.md)
>[Sonraki](protobuf-data-types.md)</span><span class="sxs-lookup"><span data-stu-id="c8c25-142">[Previous](protocol-buffers.md)
[Next](protobuf-data-types.md)</span></span>
