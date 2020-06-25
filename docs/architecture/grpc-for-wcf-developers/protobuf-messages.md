---
title: Prototipsiz iletiler-WCF geliştiricileri için gRPC
description: Prototipme iletilerinin IDL 'de nasıl tanımlandığını ve C# dilinde oluşturulduğunu öğrenin.
ms.date: 09/09/2019
ms.openlocfilehash: 6fc7b9c34810abaa8d674af56d1517a5cf87521b
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325043"
---
# <a name="protobuf-messages"></a><span data-ttu-id="898c6-103">Protobuf iletileri</span><span class="sxs-lookup"><span data-stu-id="898c6-103">Protobuf messages</span></span>

<span data-ttu-id="898c6-104">Bu bölümde, dosyalardaki protokol arabelleği (Protoarabelleği) iletilerinin nasıl bildirildiği ele alınmaktadır `.proto` .</span><span class="sxs-lookup"><span data-stu-id="898c6-104">This section covers how to declare Protocol Buffer (Protobuf) messages in `.proto` files.</span></span> <span data-ttu-id="898c6-105">Alan numaralarının ve türlerinin temel kavramlarını açıklar ve derleyicinin oluşturduğu C# koduna bakar `protoc` .</span><span class="sxs-lookup"><span data-stu-id="898c6-105">It explains the fundamental concepts of field numbers and types, and it looks at the C# code that the `protoc` compiler generates.</span></span>

<span data-ttu-id="898c6-106">Bölümün geri kalanı, farklı veri türlerinin prototipte nasıl temsil edildiği konusunda daha ayrıntılı bilgi sağlayacaktır.</span><span class="sxs-lookup"><span data-stu-id="898c6-106">The rest of the chapter will look in more detail at how different types of data are represented in Protobuf.</span></span>

## <a name="declaring-a-message"></a><span data-ttu-id="898c6-107">İleti bildirme</span><span class="sxs-lookup"><span data-stu-id="898c6-107">Declaring a message</span></span>

<span data-ttu-id="898c6-108">Windows Communication Foundation (WCF) ' de, `Stock` hisse senedi Market Ticari uygulaması için bir sınıf aşağıdaki örnekte olduğu gibi tanımlanabilir:</span><span class="sxs-lookup"><span data-stu-id="898c6-108">In Windows Communication Foundation (WCF), a `Stock` class for a stock market trading application might be defined like the following example:</span></span>

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

<span data-ttu-id="898c6-109">Protoarabelleğe denk sınıfı uygulamak için, `.proto` dosyayı dosyada bildirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="898c6-109">To implement the equivalent class in Protobuf, you must declare it in the `.proto` file.</span></span> <span data-ttu-id="898c6-110">`protoc`Derleyici daha sonra yapı sürecinin bir parçası olarak .NET sınıfını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="898c6-110">The `protoc` compiler will then generate the .NET class as part of the build process.</span></span>

```protobuf
syntax = "proto3";

option csharp_namespace = "TraderSys";

message Stock {

    int32 id = 1;
    string symbol = 2;
    string display_name = 3;
    int32 market_id = 4;

}  
```

<span data-ttu-id="898c6-111">İlk satır, kullanılmakta olan sözdizimi sürümünü bildirir.</span><span class="sxs-lookup"><span data-stu-id="898c6-111">The first line declares the syntax version being used.</span></span> <span data-ttu-id="898c6-112">Dilin sürüm 3 2016 ' de yayımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="898c6-112">Version 3 of the language was released in 2016.</span></span> <span data-ttu-id="898c6-113">Bu, gRPC Hizmetleri için önerdiğimiz sürümdür.</span><span class="sxs-lookup"><span data-stu-id="898c6-113">It's the version that we recommend for gRPC services.</span></span>

<span data-ttu-id="898c6-114">`option csharp_namespace`Satır, oluşturulan C# türleri için kullanılacak ad alanını belirtir.</span><span class="sxs-lookup"><span data-stu-id="898c6-114">The `option csharp_namespace` line specifies the namespace to be used for the generated C# types.</span></span> <span data-ttu-id="898c6-115">Bu seçenek, `.proto` dosya diğer diller için derlendiğinde yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="898c6-115">This option will be ignored when the `.proto` file is compiled for other languages.</span></span> <span data-ttu-id="898c6-116">Prototip dosyaları genellikle birkaç dil için dile özgü seçenekler içerir.</span><span class="sxs-lookup"><span data-stu-id="898c6-116">Protobuf files often contain language-specific options for several languages.</span></span>

<span data-ttu-id="898c6-117">`Stock`İleti tanımı dört alanı belirtir.</span><span class="sxs-lookup"><span data-stu-id="898c6-117">The `Stock` message definition specifies four fields.</span></span> <span data-ttu-id="898c6-118">Her birinin bir türü, adı ve alan numarası vardır.</span><span class="sxs-lookup"><span data-stu-id="898c6-118">Each has a type, a name, and a field number.</span></span>

## <a name="field-numbers"></a><span data-ttu-id="898c6-119">Alan numaraları</span><span class="sxs-lookup"><span data-stu-id="898c6-119">Field numbers</span></span>

<span data-ttu-id="898c6-120">Alan numaraları, prototipin önemli bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="898c6-120">Field numbers are an important part of Protobuf.</span></span> <span data-ttu-id="898c6-121">Bunlar, ikili kodlu verilerdeki alanları tanımlamak için kullanılır. Bu, sürümden hizmetinizin sürümüne değiştiremeyeceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="898c6-121">They're used to identify fields in the binary encoded data, which means they can't change from version to version of your service.</span></span> <span data-ttu-id="898c6-122">Bunun avantajı, geriye dönük uyumluluk ve ileriye doğru uyumluluk olanaklarından yararlanabilmektir.</span><span class="sxs-lookup"><span data-stu-id="898c6-122">The advantage is that backward compatibility and forward compatibility are possible.</span></span> <span data-ttu-id="898c6-123">Eksik değer olasılığı işlendiği sürece, istemciler ve hizmetler, hakkında bilgi sahibi olmadıkları alan numaralarını yok sayacaktır.</span><span class="sxs-lookup"><span data-stu-id="898c6-123">Clients and services will simply ignore field numbers that they don't know about, as long as the possibility of missing values is handled.</span></span>

<span data-ttu-id="898c6-124">İkili biçimde, alan numarası bir tür tanımlayıcısıyla birleştirilir.</span><span class="sxs-lookup"><span data-stu-id="898c6-124">In the binary format, the field number is combined with a type identifier.</span></span> <span data-ttu-id="898c6-125">1 ile 15 arasında alan numaraları, tek bir bayt olarak türlerine göre kodlanabilir.</span><span class="sxs-lookup"><span data-stu-id="898c6-125">Field numbers from 1 to 15 can be encoded with their type as a single byte.</span></span> <span data-ttu-id="898c6-126">16 ile 2.047 arasında sayılar 2 bayt sürer.</span><span class="sxs-lookup"><span data-stu-id="898c6-126">Numbers from 16 to 2,047 take 2 bytes.</span></span> <span data-ttu-id="898c6-127">Herhangi bir nedenden dolayı bir ileti üzerinde 2.047 ' den fazla alana ihtiyacınız varsa daha yüksek bir değere geçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="898c6-127">You can go higher if you need more than 2,047 fields on a message for any reason.</span></span> <span data-ttu-id="898c6-128">1 ile 15 arasındaki alan numaralarının tek baytlık tanımlayıcıları daha iyi performans sağlar, bu nedenle bunları en temel, sık kullanılan alanlar için kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="898c6-128">The single byte identifiers for field numbers 1 to 15 offer better performance, so you should use them for the most basic, frequently used fields.</span></span>

## <a name="types"></a><span data-ttu-id="898c6-129">Türler</span><span class="sxs-lookup"><span data-stu-id="898c6-129">Types</span></span>

<span data-ttu-id="898c6-130">Tür bildirimleri, [sonraki bölümde](protobuf-data-types.md)daha ayrıntılı bir şekilde ele alınan Prototiparabelleği yerel skaler veri türlerini kullanıyor.</span><span class="sxs-lookup"><span data-stu-id="898c6-130">The type declarations are using Protobuf's native scalar data types, which are discussed in more detail in [the next section](protobuf-data-types.md).</span></span> <span data-ttu-id="898c6-131">Bu bölümün geri kalanı, prototipin yerleşik türlerini kapsayacak ve bunların ortak .NET türleriyle ilişkisini göstermeyecektir.</span><span class="sxs-lookup"><span data-stu-id="898c6-131">The rest of this chapter will cover Protobuf's built-in types and show how they relate to common .NET types.</span></span>

> [!NOTE]
> <span data-ttu-id="898c6-132">Prototip `decimal` , bir türü yerel olarak desteklemez, `double` bunun yerine kullanılır.</span><span class="sxs-lookup"><span data-stu-id="898c6-132">Protobuf doesn't natively support a `decimal` type, so `double` is used instead.</span></span> <span data-ttu-id="898c6-133">Tam ondalık duyarlık gerektiren uygulamalar için, bu bölümün sonraki bölümünde yer [alan Ondalıklar bölümüne](protobuf-data-types.md#decimals) bakın.</span><span class="sxs-lookup"><span data-stu-id="898c6-133">For applications that require full decimal precision, refer to the [section on decimals](protobuf-data-types.md#decimals) in the next part of this chapter.</span></span>

## <a name="the-generated-code"></a><span data-ttu-id="898c6-134">Oluşturulan kod</span><span class="sxs-lookup"><span data-stu-id="898c6-134">The generated code</span></span>

<span data-ttu-id="898c6-135">Uygulamanızı yapılandırdığınızda, Prototipsiz iletilerinizin her biri için sınıflar oluşturur ve yerel türlerini C# türlerine eşleyerek.</span><span class="sxs-lookup"><span data-stu-id="898c6-135">When you build your application, Protobuf creates classes for each of your messages, mapping its native types to C# types.</span></span> <span data-ttu-id="898c6-136">Oluşturulan `Stock` tür aşağıdaki imzaya sahip olacaktır:</span><span class="sxs-lookup"><span data-stu-id="898c6-136">The generated `Stock` type would have the following signature:</span></span>

```csharp
public class Stock
{
    public int Id { get; set; }
    public string Symbol { get; set; }
    public string DisplayName { get; set; }
    public int MarketId { get; set; }
}
```

<span data-ttu-id="898c6-137">Oluşturulan gerçek kod bundan çok daha karmaşıktır.</span><span class="sxs-lookup"><span data-stu-id="898c6-137">The actual code that's generated is far more complicated than this.</span></span> <span data-ttu-id="898c6-138">Bunun nedeni, her bir sınıfın kendisini seri hale getirmek için gereken tüm kodu ve ikili tel biçiminde seri durumdan çıkarmak için gerekli olduğunu içerir.</span><span class="sxs-lookup"><span data-stu-id="898c6-138">The reason is that each class contains all the code necessary to serialize and deserialize itself to the binary wire format.</span></span>

### <a name="property-names"></a><span data-ttu-id="898c6-139">Özellik adları</span><span class="sxs-lookup"><span data-stu-id="898c6-139">Property names</span></span>

<span data-ttu-id="898c6-140">Prototip derleyicisinin, `PascalCase` dosyasında olmasına rağmen özellik adlarına uygulandığını unutmayın `snake_case` `.proto` .</span><span class="sxs-lookup"><span data-stu-id="898c6-140">Note that the Protobuf compiler applied `PascalCase` to the property names, although they were `snake_case` in the `.proto` file.</span></span> <span data-ttu-id="898c6-141">[Prototipli Stil Kılavuzu](https://developers.google.com/protocol-buffers/docs/style) , `snake_case` diğer platformlar için kod oluşturmanın, kuralları için beklenen durumu üretmeleri için ileti tanımlarınızda kullanılmasını önerir.</span><span class="sxs-lookup"><span data-stu-id="898c6-141">The [Protobuf style guide](https://developers.google.com/protocol-buffers/docs/style) recommends using `snake_case` in your message definitions so that the code generation for other platforms produces the expected case for their conventions.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="898c6-142">[Önceki](protocol-buffers.md) 
> [Sonraki](protobuf-data-types.md)</span><span class="sxs-lookup"><span data-stu-id="898c6-142">[Previous](protocol-buffers.md)
[Next](protobuf-data-types.md)</span></span>
