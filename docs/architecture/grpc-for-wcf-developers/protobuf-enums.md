---
title: Prototipsiz numaralandırmalar-WCF geliştiricileri için gRPC
description: Prototipte numaralandırmalar bildirme ve kullanma hakkında bilgi edinin.
ms.date: 09/09/2019
ms.openlocfilehash: 01cf4a4e5e0eda1e7ddff2a6780119fcb3120dad
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543150"
---
# <a name="protobuf-enumerations"></a><span data-ttu-id="69732-103">Protobuf sabit listeleri</span><span class="sxs-lookup"><span data-stu-id="69732-103">Protobuf enumerations</span></span>

<span data-ttu-id="69732-104">Prototip, numaralandırma türlerini destekler.</span><span class="sxs-lookup"><span data-stu-id="69732-104">Protobuf supports enumeration types.</span></span> <span data-ttu-id="69732-105">Bu desteği, bir `Oneof` alanının türünü belirlemekte bir sabit listesinin kullanıldığı önceki bölümde gördünüz.</span><span class="sxs-lookup"><span data-stu-id="69732-105">You saw this support in the previous section, where an enum was used to determine the type of a `Oneof` field.</span></span> <span data-ttu-id="69732-106">Kendi numaralandırma türlerinizi tanımlayabilir ve Protoda bunları sabit listesi türleri için C# derler.</span><span class="sxs-lookup"><span data-stu-id="69732-106">You can define your own enumeration types, and Protobuf will compile them to C# enum types.</span></span> 

<span data-ttu-id="69732-107">Prototip ' i çeşitli dillerle birlikte kullanabilmeniz için, numaralandırmalar için adlandırma kuralları C# kurallardan farklıdır.</span><span class="sxs-lookup"><span data-stu-id="69732-107">Because you can use Protobuf with various languages, the naming conventions for enumerations are different from the C# conventions.</span></span> <span data-ttu-id="69732-108">Ancak, kod Oluşturucu adları geleneksel C# harfe dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="69732-108">However, the code generator converts the names to the traditional C# case.</span></span> <span data-ttu-id="69732-109">Alan adının Pascal-case eşdeğerini, numaralandırma adıyla başlıyorsa, kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="69732-109">If the Pascal-case equivalent of the field name starts with the enumeration name, then it's removed.</span></span>

<span data-ttu-id="69732-110">Örneğin, aşağıdaki prototip numaralandırmasında, alanlar `ACCOUNT_STATUS`ön ekine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="69732-110">For example, in the following Protobuf enumeration, the fields are prefixed with `ACCOUNT_STATUS`.</span></span> <span data-ttu-id="69732-111">Bu ön ek, `AccountStatus`Pascal-case numaralandırma adına eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="69732-111">This prefix is equivalent to the Pascal-case enum name, `AccountStatus`.</span></span>

```protobuf
enum AccountStatus {
  ACCOUNT_STATUS_UNKNOWN = 0;
  ACCOUNT_STATUS_PENDING = 1;
  ACCOUNT_STATUS_ACTIVE = 2;
  ACCOUNT_STATUS_SUSPENDED = 3;
  ACCOUNT_STATUS_CLOSED = 4;
}
```

<span data-ttu-id="69732-112">Oluşturucu aşağıdaki koda denk C# bir sabit listesi oluşturur:</span><span class="sxs-lookup"><span data-stu-id="69732-112">The generator creates a C# enum equivalent to the following code:</span></span>

```csharp
public enum AccountStatus
{
    Unknown = 0,
    Pending = 1,
    Active = 2,
    Suspended = 3,
    Closed = 4
}
```

<span data-ttu-id="69732-113">Prototip numaralandırma tanımlarının ilk alanları olarak sıfır sabiti *olmalıdır* .</span><span class="sxs-lookup"><span data-stu-id="69732-113">Protobuf enumeration definitions *must* have a zero constant as their first field.</span></span> <span data-ttu-id="69732-114">İçinde C#olduğu gibi, aynı değere sahip birden fazla alan bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="69732-114">As in C#, you can declare multiple fields with the same value.</span></span> <span data-ttu-id="69732-115">Ancak, bu seçeneği numaralandırmasında `allow_alias` seçeneğini kullanarak açıkça etkinleştirmeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="69732-115">But you must explicitly enable this option by using the `allow_alias` option in the enum:</span></span>

```protobuf
enum AccountStatus {
  option allow_alias = true;
  ACCOUNT_STATUS_UNKNOWN = 0;
  ACCOUNT_STATUS_PENDING = 1;
  ACCOUNT_STATUS_ACTIVE = 2;
  ACCOUNT_STATUS_SUSPENDED = 3;
  ACCOUNT_STATUS_CLOSED = 4;
  ACCOUNT_STATUS_CANCELLED = 4;
}
```

<span data-ttu-id="69732-116">Numaralandırmalar `.proto` bir dosyanın en üst düzeyinde ya da bir ileti tanımı içinde iç içe bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="69732-116">You can declare enumerations at the top level in a `.proto` file, or nested within a message definition.</span></span> <span data-ttu-id="69732-117">İç içe geçmiş mesajlar gibi iç içe yerleştirilmiş numaralandırmalar, oluşturulan ileti sınıfındaki `.Types` statik sınıf içinde bildirilecektir.</span><span class="sxs-lookup"><span data-stu-id="69732-117">Nested enumerations—like nested messages—will be declared within the `.Types` static class in the generated message class.</span></span>

<span data-ttu-id="69732-118">[[Flags]](xref:System.FlagsAttribute) özniteliğini prototipsel olarak üretilen bir numaralandırmaya uygulamanın bir yolu yoktur ve protoarabellek, bit düzeyinde sabit listesi birleşimlerini anlamaz.</span><span class="sxs-lookup"><span data-stu-id="69732-118">There's no way to apply the [[Flags]](xref:System.FlagsAttribute) attribute to a Protobuf-generated enum, and Protobuf doesn't understand bitwise enum combinations.</span></span> <span data-ttu-id="69732-119">Aşağıdaki örneğe bakın:</span><span class="sxs-lookup"><span data-stu-id="69732-119">Look at the following example:</span></span>

```protobuf
enum Region {
  REGION_NONE = 0;
  REGION_NORTH_AMERICA = 1;
  REGION_SOUTH_AMERICA = 2;
  REGION_EMEA = 4;
  REGION_APAC = 8;
}

message Product {
  Region available_in = 1;
}
```

<span data-ttu-id="69732-120">`product.AvailableIn` `Region.NorthAmerica | Region.SouthAmerica`olarak ayarlarsanız, `3`tamsayı değer olarak serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="69732-120">If you set `product.AvailableIn` to `Region.NorthAmerica | Region.SouthAmerica`, it's serialized as the integer value `3`.</span></span> <span data-ttu-id="69732-121">Bir istemci veya sunucu değeri seri durumdan çıkarmaya çalıştığında, `3`için enum tanımında bir eşleşme bulamaz.</span><span class="sxs-lookup"><span data-stu-id="69732-121">When a client or server tries to deserialize the value, it won't find a match in the enum definition for `3`.</span></span> <span data-ttu-id="69732-122">Sonuç `Region.None`olacaktır.</span><span class="sxs-lookup"><span data-stu-id="69732-122">The result will be `Region.None`.</span></span>

<span data-ttu-id="69732-123">Prototipte birden çok Enum değeri ile çalışmanın en iyi yolu, sabit listesi türünde bir `repeated` alanı kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="69732-123">The best way to work with multiple enum values in Protobuf is to use a `repeated` field of the enum type.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="69732-124">[Önceki](protobuf-any-oneof.md)
>[İleri](protobuf-maps.md)</span><span class="sxs-lookup"><span data-stu-id="69732-124">[Previous](protobuf-any-oneof.md)
[Next](protobuf-maps.md)</span></span>
