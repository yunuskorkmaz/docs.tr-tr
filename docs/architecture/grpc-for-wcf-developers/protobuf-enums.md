---
title: Prototipsiz numaralandırmalar-WCF geliştiricileri için gRPC
description: Prototipte numaralandırmalar bildirme ve kullanma hakkında bilgi edinin.
author: markrendle
ms.date: 09/09/2019
ms.openlocfilehash: d93319b713588129a19246976a82bb03a90ce680
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184241"
---
# <a name="protobuf-enumerations"></a><span data-ttu-id="49163-103">Prototip listeleme</span><span class="sxs-lookup"><span data-stu-id="49163-103">Protobuf enumerations</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="49163-104">Prototip, bir `oneof` alanın türünü belirlemekte bir sabit listesinin kullanıldığı önceki bölümde görüldüğü gibi numaralandırma türlerini destekler.</span><span class="sxs-lookup"><span data-stu-id="49163-104">Protobuf supports enumeration types, as seen in the previous section where an enum was used to determine the type of a `oneof` field.</span></span> <span data-ttu-id="49163-105">Kendi numaralandırma türlerinizi tanımlayabilir ve Protoda bunları sabit listesi türleri için C# derler.</span><span class="sxs-lookup"><span data-stu-id="49163-105">You can define your own enumeration types and Protobuf will compile them to C# enum types.</span></span> <span data-ttu-id="49163-106">Prototip farklı dillerde kullanılabilir olduğundan, numaralandırmalar için adlandırma kuralları C# kurallardan farklıdır.</span><span class="sxs-lookup"><span data-stu-id="49163-106">Since Protobuf can be used with different languages, the naming conventions for enumerations are different from the C# conventions.</span></span> <span data-ttu-id="49163-107">Ancak, kod üreticisi zekice ' dir ve adları geleneksel C# harfe dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="49163-107">However, the code generator is clever and converts the names to the traditional C# case.</span></span> <span data-ttu-id="49163-108">Alan adının Pascal-case eşdeğerini, numaralandırma adıyla başlıyorsa, kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="49163-108">If the Pascal-case equivalent of the field name starts with the enumeration name, then it's removed.</span></span>

<span data-ttu-id="49163-109">Örneğin, bu prototiplik numaralandırmasında alanlar `ACCOUNT_STATUS`, Pascal case numaralandırma adına eşdeğer olan ön ekine sahiptir:. `AccountStatus`</span><span class="sxs-lookup"><span data-stu-id="49163-109">For example, in this Protobuf enumeration the fields are prefixed with `ACCOUNT_STATUS`, which is equivalent to the Pascal case enum name: `AccountStatus`.</span></span>

```protobuf
enum AccountStatus {
  ACCOUNT_STATUS_UNKNOWN = 0;
  ACCOUNT_STATUS_PENDING = 1;
  ACCOUNT_STATUS_ACTIVE = 2;
  ACCOUNT_STATUS_SUSPENDED = 3;
  ACCOUNT_STATUS_CLOSED = 4;
}
```

<span data-ttu-id="49163-110">Bu nedenle, Oluşturucu aşağıdaki koda C# denk bir sabit listesi oluşturur:</span><span class="sxs-lookup"><span data-stu-id="49163-110">So, the generator creates a C# enum equivalent to the following code:</span></span>

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

<span data-ttu-id="49163-111">Prototip numaralandırma tanımlarının ilk alanları olarak sıfır sabiti **olmalıdır** .</span><span class="sxs-lookup"><span data-stu-id="49163-111">Protobuf enumeration definitions **must** have a zero constant as their first field.</span></span> <span data-ttu-id="49163-112">' De C#olduğu gibi, aynı değere sahip birden fazla alan bildirebilirsiniz, ancak bu seçeneği, Numaralandırmadaki `allow_alias` seçeneğini kullanarak açıkça etkinleştirmelisiniz:</span><span class="sxs-lookup"><span data-stu-id="49163-112">As in C#, you can declare multiple fields with the same value, but you must explicitly enable this option using the `allow_alias` option in the enum:</span></span>

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

<span data-ttu-id="49163-113">Numaralandırmalar bir `.proto` dosyanın en üst düzeyinde veya bir ileti tanımı içinde iç içe bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="49163-113">You can declare enumerations at the top level in a `.proto` file, or nested within a message definition.</span></span> <span data-ttu-id="49163-114">İç içe geçmiş (iç içe geçmiş iletiler gibi) numaralandırmalar `.Types` oluşturulan ileti sınıfındaki statik sınıf içinde bildirilecektir.</span><span class="sxs-lookup"><span data-stu-id="49163-114">Nested enumerations—like nested messages—will be declared within the `.Types` static class in the generated message class.</span></span>

<span data-ttu-id="49163-115">[[Flags]](xref:System.FlagsAttribute) özniteliğini prototipsel olarak üretilen bir numaralandırmaya uygulamanın bir yolu yoktur ve protoarabellek, bit düzeyinde sabit listesi birleşimlerini anlamaz.</span><span class="sxs-lookup"><span data-stu-id="49163-115">There's no way to apply the [[Flags]](xref:System.FlagsAttribute) attribute to a Protobuf-generated enum, and Protobuf doesn't understand bitwise enum combinations.</span></span> <span data-ttu-id="49163-116">Aşağıdaki örneğe göz atın:</span><span class="sxs-lookup"><span data-stu-id="49163-116">Take a look at the following example:</span></span>

```protobuf
enum Region {
  REGION_NONE = 0;
  REGION_NORTH_AMERICA = 1;
  REGION_SOUTH_AMERICA = 2;
  REGION_EMEA = 4;
  REGION_APAC = 8;
}

message Product {
  Region availableIn = 1;
}
```

<span data-ttu-id="49163-117">' A ayarlarsanız `product.AvailableIn` , tamsayı değeri `3`olarak serileştirilir. `Region.NorthAmerica | Region.SouthAmerica`</span><span class="sxs-lookup"><span data-stu-id="49163-117">If you set `product.AvailableIn` to `Region.NorthAmerica | Region.SouthAmerica`, it's serialized as the integer value `3`.</span></span> <span data-ttu-id="49163-118">Bir istemci veya sunucu değeri seri durumdan çıkarmaya çalıştığında, için `3` enum tanımında bir eşleşme bulamaz ve sonuç `Region.None`olur.</span><span class="sxs-lookup"><span data-stu-id="49163-118">When a client or server tries to deserialize the value, it won't find a match in the enum definition for `3` and the result will be `Region.None`.</span></span>

<span data-ttu-id="49163-119">Prototipte birden çok Enum değeri ile çalışmanın en iyi yolu, sabit listesi türünün `repeated` bir alanını kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="49163-119">The best way to work with multiple enum values in Protobuf is to use a `repeated` field of the enum type.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="49163-120">[Önceki](protobuf-any-oneof.md)
>[İleri](protobuf-maps.md)</span><span class="sxs-lookup"><span data-stu-id="49163-120">[Previous](protobuf-any-oneof.md)
[Next](protobuf-maps.md)</span></span>
